# Предсказание оттока клиентов в телеком компании
Учебный проект.  

## Данные
Есть доступ к sql базе с 4 таблицами, в которых находится информация:
* о договоре
* персональных данных
* информация об интернет-услугах
* информация о услугах телефонии

Данные за период от 2018-04-17 по 2020-02-01.

## Задачи
1. Загрузить данные из sql базы
2. Объединить таблицы в один датафрейм
3. Исследовать данные
4. Сравнить модели 
5. Подобрать гиперпараметры к лучшей
6. Проанализировать важность признаков

## Детали
Нужно проверить и подготовить данные, создав описание клиента по этим данным. Один клиент - один вектор.
Были исправлены небольшие погрешности в данных.

Провести EDA, в результате которого были обнаружены корреляции между признаками и между таргетом и признаками. 
Также определенные ограничения по использованию данных для предсказания отдельных подгрупп.

Для сравнения моделей была использована метрика `ROC AUC`.

Были обучены модели:
* логистическая регрессия и подбор `C` с помощью learning curve и кросс валидацией
* дерево решений cv
* catboost cv
* нейронная сеть (в качестве эксперимента)

Дальше с помощью optuna были оптимизированы гиперпараметры catboost, т.к. эта модель показала наилучший результат и наименьшее стандартное отклонение на 10 фолдах.  

Исследование важности фичей было произведено с помощью `SHAP`.

Итоговый `ROC AUC`: 0.85

