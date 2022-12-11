import telebot
from telebot import types
import qrcode
import os
from PIL import Image

bot = telebot.TeleBot('Token bot')

@bot.message_handler(commands=['start'])
def start(message):
    markup = types.ReplyKeyboardMarkup(resize_keyboard=True)
    btn1 = types.KeyboardButton("Адреса")
    btn2 = types.KeyboardButton("Получить скидку")
    btn3 = types.KeyboardButton("Наше меню")
    markup.add(btn1, btn2, btn3)
    bot.send_message(message.chat.id, text=f"Привет, {message.from_user.first_name}! Жми на кнопки, чтобы получить всю информацию ", reply_markup=markup)

@bot.message_handler(content_types=['text'])
def func(message):
    if message.text == "Получить скидку":
        img = qrcode.make('Скидка 10%')
        type(img)
        img.save("some_file.png")
        bot.send_photo(message.chat.id, photo=open(os.path.join("some_file.png"), "rb"), caption="Ваша скидка")

    elif message.text == "Наше меню":
        bot.send_message(message.chat.id, text="Посмотреть меню и заказать доставку:\nhttps://eda.yandex.ru/spb/r/chicken_star")
        markup = types.ReplyKeyboardMarkup(resize_keyboard=True)
        back = types.KeyboardButton("Вернуться в главное меню")
        markup.add(back)

    elif message.text == "Адреса":
        markup = types.ReplyKeyboardMarkup(resize_keyboard=True)
        btn1 = types.KeyboardButton("Мурино")
        btn2 = types.KeyboardButton("Парнас")
        btn3 = types.KeyboardButton("Ладожская")
        back = types.KeyboardButton("Вернуться в главное меню")
        markup.add(btn1, btn2, btn3, back)
        bot.send_message(message.chat.id, text=f"Выбери адрес: ", reply_markup=markup)

    elif message.text == "Мурино":
        bot.send_message(message.chat.id, text="Как добраться:\nhttps://go.2gis.com/7htgy1")

    elif message.text == "Парнас":
        bot.send_message(message.chat.id, text="Как добраться:\nhttps://go.2gis.com/azvl1")

    elif message.text == "Ладожская":
        bot.send_message(message.chat.id, text="Как добраться:\nhttps://go.2gis.com/3dz75")

    elif message.text == "Вернуться в главное меню":
        markup = types.ReplyKeyboardMarkup(resize_keyboard=True)
        btn1 = types.KeyboardButton("Адреса")
        btn2 = types.KeyboardButton("Получить скидку")
        btn3 = types.KeyboardButton("Наше меню")
        markup.add(btn1, btn2, btn3)
        bot.send_message(message.chat.id, text=f"Привет, {message.from_user.first_name}! Жми на кнопки, чтобы получить всю информацию ",
                         reply_markup=markup)
    else:
        bot.send_message(message.chat.id, text="Жми на кнопки!")

bot.polling(none_stop=True)
