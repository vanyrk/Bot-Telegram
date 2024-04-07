# Bot-Telegram

# Импорт библиотек и установка токена бота:

python
Copy code
import telebot
import random

bot = telebot.TeleBot('YOUR_TELEGRAM_BOT_TOKEN')
Этот блок кода импортирует необходимые библиотеки (telebot для работы с Telegram API и random для генерации случайных чисел) и создает объект bot с использованием вашего токена Telegram бота.

Список слов:

python
Copy code
word_list = ["яблоко", "банан", ... ]
В этом списке содержатся слова, из которых будет случайным образом выбираться одно для угадывания.

# Настройки игры:

python
Copy code
MAX_ATTEMPTS = 6
MAX_HINTS = 3
hints_used = 0
attempts_left = MAX_ATTEMPTS
secret_word = ""
guessed_word = ""
Здесь задаются настройки игры: максимальное количество попыток (MAX_ATTEMPTS), максимальное количество подсказок (MAX_HINTS), а также переменные для отслеживания использованных подсказок, оставшихся попыток, загаданного слова и угаданного слова.

# Обработчик команды /start:

python
Copy code
@bot.message_handler(commands=['start'])
def start_message(message):
    global attempts_left
    global hints_used
    global secret_word
    global guessed_word
    ...
Эта функция вызывается, когда пользователь отправляет команду /start. Она сбрасывает значения переменных, инициализирует загаданное слово и угаданное слово, а затем отправляет приветственное сообщение и инструкцию о том, как играть.

# Обработчик команды /hint:

python
Copy code
@bot.message_handler(commands=['hint'])
def send_hint(message):
    global secret_word
    global guessed_word
    global hints_used
    ...
Эта функция вызывается, когда пользователь отправляет команду /hint. Она проверяет количество использованных подсказок и отправляет подсказку (если есть неугаданные буквы в слове).

# Обработчик текстовых сообщений:

python
Copy code
@bot.message_handler(content_types=['text'])
def check_letter(message):
    global guessed_word
    global secret_word
    global attempts_left
    ...
Эта функция вызывается, когда пользователь отправляет текстовое сообщение. Она проверяет содержимое сообщения (должна быть одна буква) и проверяет, есть ли эта буква в загаданном слове. Затем она обновляет угаданное слово и отправляет результат пользователю.

# Запуск бота:

python
Copy code
bot.polling()
Этот метод начинает прослушивание сообщений от Telegram и вызывает соответствующие обработчики для обработки команд и сообщений пользователей.



