def text_num(text):
    symbols = {
        'ноль': 0, 'один': 1, 'два': 2, 'три': 3, 'четыре': 4,
        'пять': 5, 'шесть': 6, 'семь': 7, 'восемь': 8,
        'девять': 9, 'десять': 10, 'одиннадцать': 11, 'двенадцать': 12,
        'тринадцать': 13, 'четырнадцать': 14, 'пятнадцать': 15,
        'шестнадцать': 16, 'семнадцать': 17, 'восемнадцать': 18,
        'девятнадцать': 19, 'двадцать': 20, 'тридцать': 30,
        'сорок': 40, 'пятьдесят': 50, 'шестьдесят': 60,
        'семьдесят': 70, 'восемьдесят': 80, 'девяносто': 90,
        'сто': 100, 'двести': 200, 'триста': 300, 'четыреста': 400,
        'пятьсот': 500, 'шестьсот': 600, 'семьсот': 700, 'восемьсот': 800,
        'девятьсот': 900, 'плюс': '+', 'минус': '-', 'умножить': '*', 'на': ''
    }

    words = text.split()
    total = []
    ignore = {'на'}

    i = 0
    while i < len(words):
        word = words[i]
        if word in ignore:
            i += 1
            continue

        #Отрицательные числа
        if word == 'минус' and (i == 0 or words[i-1] in {'плюс', 'минус', '*', 'на'}):
            if i + 1 < len(words) and words[i+1] in symbols:
                total.append(-symbols[words[i+1]])
                i += 2
                continue
            else:
                return f"Ошибка: После 'минус' должно быть число"
        if word in symbols:
            total.append(symbols[word])
        else:
            return f"Неизвестное слово: {word}"
        i += 1
    return total

def calculate(total):
    # Сначала умножение
    while '*' in total:
        index = total.index('*')
        result = total[index - 1] * total[index + 1]
        total = total[:index - 1] + [result] + total[index + 2:]

    # сложение и вычитание
    while '+' in total or '-' in total:
        if '+' in total:
            index = total.index('+')
            result = total[index - 1] + total[index + 1]
            total = total[:index - 1] + [result] + total[index + 2:]
        elif '-' in total:
            index = total.index('-')
            result = total[index - 1] - total[index + 1]
            total = total[:index - 1] + [result] + total[index + 2:]

    return total[0]

def calc(vvodik):
    total = text_num(vvodik)
    if isinstance(total, str):
        return total
    result = calculate(total)
    return result
def num_to_words(num):
    num_words = {0: 'ноль', 1: 'один', 2: 'два', 3: 'три', 4: 'четыре',
        5: 'пять', 6: 'шесть', 7: 'семь', 8: 'восемь', 9: 'девять',
        10: 'десять', 11: 'одиннадцать', 12: 'двенадцать', 13: 'тринадцать',
        14: 'четырнадцать', 15: 'пятнадцать', 16: 'шестнадцать', 17: 'семнадцать',
        18: 'восемнадцать', 19: 'девятнадцать', 20: 'двадцать', 30: 'тридцать',
        40: 'сорок', 50: 'пятьдесят', 60: 'шестьдесят', 70: 'семьдесят',
        80: 'восемьдесят', 90: 'девяносто', 100: 'сто', 200: 'двести',
        300: 'триста', 400: 'четыреста', 500: 'пятьсот', 600: 'шестьсот',
        700: 'семьсот', 800: 'восемьсот', 900: 'девятьсот'}
    if num == 0:
        return 'ноль'
    temp = []
    if num >= 100:
        hundreds = num // 100 * 100
        temp.append(num_words[hundreds])
        num %= 100
    if num >= 20:
        tens = num // 10 * 10
        temp.append(num_words[tens])
        num %= 10
    if num > 0:
        temp.append(num_words[num])

    return ' '.join(temp)

print("Добро пожаловать в текстовый калькулятор. Введите выражение, а я посчитаю и дам вам ответ в виде текста!(Результат в текстовом виде выводится для результатов до 1000. Результаты больше 1000 будут выводиться в численном виде)")
while True:
    vvod = input("Введите выражение: ")
    result = calc(vvod)
    if isinstance(result, int) and result <= 1000:
        result = num_to_words(result)
    print(f"Результат: {result}")
