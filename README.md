import pandas as pd
import random

# Создаем исходный DataFrame
lst = ['robot'] * 10 + ['human'] * 10
random.shuffle(lst)
data = pd.DataFrame({'whoAmI': lst})

# Преобразуем 'whoAmI' в one hot вид
one_hot_encoded = pd.concat([
    data['whoAmI'].apply(lambda x: pd.Series(1 if x == category else 0 for category in data['whoAmI'].unique()))
], axis=1)

# Даем названия новым столбцам
one_hot_encoded.columns = data['whoAmI'].unique()

# Выводим результат
print(one_hot_encoded.head())
