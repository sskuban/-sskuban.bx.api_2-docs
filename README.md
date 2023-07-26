# API

**Входная точка** `https://bx.sskuban.ru/api_2/`

Все запросы формируются с параметром `api_key`  
Пример `https://bx.sskuban.ru/api_2/?api_key=test`

Данные возвращаются в формате `json` в кодировке `utf-8`

### Получить список статей

`GET` `articles/`

#### Возвращаемые данные

| Параметры | Тип              | Описание      |
|-----------|------------------|---------------|
| `status`  | `responseStatus` | Статус ответа |
| `data`    | `array(article)` | Список статей |

### Получить список новостей

`GET` `news/`

#### Возвращаемые данные

| Параметры | Тип              | Описание      |
|-----------|------------------|---------------|
| `status`  | `responseStatus` | Статус ответа |
| `data`    | `array(article)` | Список статей |

### Получить список акций

`GET` `promos/`

#### Возвращаемые данные

| Параметры | Тип              | Описание      |
|-----------|------------------|---------------|
| `status`  | `responseStatus` | Статус ответа |
| `data`    | `array(article)` | Список статей |

### Получить список видео

`GET` `videos/`

#### Возвращаемые данные

| Параметры | Тип              | Описание      |
|-----------|------------------|---------------|
| `status`  | `responseStatus` | Статус ответа |
| `data`    | `array(video)`   | Список видео  |

### Получить список социальных проектов

`GET` `projects/`

#### Возвращаемые данные

| Параметры         | Тип                    | Описание               |
|-------------------|------------------------|------------------------|
| `status`          | `responseStatus`       | Статус ответа          |
| `data`            | `array(project)`       | Список проектов        |
| `lists`           | `array`                | Вспомогательные списки |
| `lists[statuses]` | `array(projectStatus)` | Статусы проектов       |

### Получить список документов

`GET` `docs/`

#### Возвращаемые данные

| Параметры | Тип              | Описание          |
|-----------|------------------|-------------------|
| `status`  | `responseStatus` | Статус ответа     |
| `data`    | `array(doc)`     | Список документов |

### Получить список пользователей

`GET` `users/`

#### Параметры запроса

| Параметры                | Тип       | Описание            |
|--------------------------|-----------|---------------------|
| `search`                 | `array=`  | Поисковые параметры |
| `search[cityId]`         | `int=`    | ID города           |
| `search[cityName]`       | `string=` | Название города     |
| `search[departmentName]` | `string=` | Название отдела     |

#### Возвращаемые данные

| Параметры              | Тип              | Описание               |
|------------------------|------------------|------------------------|
| `status`               | `responseStatus` | Статус ответа          |
| `data`                 | `array(user)`    | Список пользователей   |
| `lists`                | `array`          | Вспомогательные списки |
| `lists[cities]`        | `array(city)`    | Города                 |
| `lists[workPositions]` | `array(string)`  | Должности              |

### Получить список ЖК и связанных площадей

`GET` `complexes/`

#### Возвращаемые данные

| Параметры               | Тип              | Описание      |
|-------------------------|------------------|---------------|
| `status`                | `responseStatus` | Статус ответа |
| `residential_complexes` | `array(complex)` | Список ЖК     |

## Типы

### article

Статья

| Параметры             | Тип        | Описание                                   |
|-----------------------|------------|--------------------------------------------|
| `createdAt`           | `datetime` | Дата и время создания                      |
| `title`               | `string`   | Заголовок                                  |
| `announce`            | `string`   | Анонс                                      |
| `detailText`          | `string`   | Подробное описание                         |
| `seoMetaDescription`  | `string`   | СЕО описание                               |
| `previewImageUrl`     | `string`   | Путь к превью                              |
| `slideImageUrl`       | `string`   | Путь к изображению для слайдера            |
| `slideMobileImageUrl` | `string`   | Путь к мобильному изображению для слайдера |
| `detailTextImageUrl`  | `string`   | Путь к изображению для подробного описания |
| `tagName`             | `string`   | Тег                                        |
| `siteId`              | `number`   | ID сайта                                   |
| `isSlider`            | `bool`     | Отображать в слайдере                      |
| `isPublished`         | `bool`     | Отображать на сайте                        |
| `isNotShowInMainPage` | `bool`     | Скрыть с титульной страницы                |

### video

Видео

| Параметры         | Тип      | Описание         |
|-------------------|----------|------------------|
| `title`           | `string` | Заголовок        |
| `youtubeVideoId`  | `string` | ID видео YouTube |
| `previewImageUrl` | `string` | Путь к превью    |

### project

Проект

| Параметры            | Тип      | Описание           |
|----------------------|----------|--------------------|
| `title`              | `string` | Заголовок          |
| `announce`           | `string` | Анонс              |
| `detailText`         | `string` | Подробное описание |
| `type`               | `string` | Тип                |
| `statusId`           | `number` | Статус             |
| `isNational`         | `bool`   | Национальный       |
| `seoMetaDescription` | `string` | СЕО описание       |
| `previewImageUrl`    | `string` | Путь к превью      |
| `youtubeVideoId`     | `string` | ID видео YouTube   |

### doc

Документ

| Параметры   | Тип      | Описание     |
|-------------|----------|--------------|
| `title`     | `string` | Заголовок    |
| `fileUrl`   | `string` | Путь к файлу |
| `complexId` | `string` | ID комплекса |

### projectStatus

Статус проекта

| Параметры | Тип      | Описание  |
|-----------|----------|-----------|
| `id`      | `string` | ID        |
| `title`   | `string` | Заголовок |

### user

Пользователь

| Параметры        | Тип      | Описание          |
|------------------|----------|-------------------|
| `name`           | `string` | Имя               |
| `lastName`       | `string` | Фамилия           |
| `secondName`     | `string` | Отчество          |
| `workPosition`   | `string` | Должность         |
| `photo`          | `string` | Путь к фотографии |
| `departmentName` | `string` | Отдел             |
| `cityId`         | `number` | ID города         |
| `cityName`       | `string` | Город             |

### city

Город

| Параметры | Тип      | Описание |
|-----------|----------|----------|
| `id`      | `string` | ID       |
| `name`    | `string` | Название |

### responseStatus

Статус ответа

| Параметры       | Тип      | Описание        |
|-----------------|----------|-----------------|
| `code`          | `number` | Код ошибки      |
| `error_message` | `string` | Описание ошибки |

### complex

Жилой комплекс

| Параметры | Тип            | Описание               |
|-----------|----------------|------------------------|
| `crm_id`  | `number`       | ID в системе Битрикс24 |
| `name`    | `string`       | Название               |
| `address` | `string`       | Адрес                  |
| `liters`  | `array(build)` | Список строений        |

### build

Строение

| Параметры           | Тип              | Описание                             |
|---------------------|------------------|--------------------------------------|
| `name`              | `string`         | Название                             |
| `liter_num`         | `number`         | Номер литера                         |
| `start_date`        | `date`           | Дата начала строительства            |
| `end_date`          | `date`           | Дата завершения строительства        |
| `key_date`          | `date`           | Дата выдачи ключей                   |
| `escrou`            | `number`         | Участвует в Эскроу                   |
| `project_financing` | `bool`           | Участвует в проектном финансировании |
| `queue`             | `number`         | Очередь строительства                |
| `floors`            | `string`         | Этажность                            |
| `status`            | `string`         | Статус                               |
| `apartments`        | `array(product)` | Список продуктов                     |

### product

Продукт

| Параметры             | Тип      | Описание                                |
|-----------------------|----------|-----------------------------------------|
| `published`           | `bool`   | Опубликован                             |
| `crm_id`              | `number` | ID в системе Битрикс24                  |
| `name`                | `string` | Название                                |
| `cardinal_directions` | `string` | Сторона света                           |
| `price`               | `number` | Цена                                    |
| `price_action`        | `number` | Акционная цена                          |
| `end_date_action`     | `date`   | Дата завершения акции                   |
| `have_repair`         | `bool`   | Можно включить ремонт                   |
| `count_balcony`       | `number` | Количество балконов                     |
| `count_loggia`        | `number` | КОличество лоджий                       |
| `count_terrace`       | `number` | Количество террас                       |
| `area_dressing_room`  | `float`  | Площадь гардиробной                     |
| `count_joint_su`      | `number` | Количество совмещенных с/у              |
| `count_separate_su`   | `number` | Количество раздельных с/у               |
| `euro_type`           | `bool`   | Еврапланировка                          |
| `section`             | `number` | Секция                                  |
| `floor`               | `number` | Этаж                                    |
| `cunt_rooms`          | `number` | Количество комнат                       |
| `status`              | `string` | Статус                                  |
| `price_m2`            | `number` | Цена м2                                 |
| `type`                | `string` | Тип                                     |
| `entrance`            | `number` | Подъезд                                 |
| `apartment_number`    | `number` | Номер                                   |
| `area_total`          | `float`  | Общая площадь                           |
| `area_living`         | `float`  | Площадь гостинной                       |
| `area_kitchen`        | `float`  | Плозадь кухни                           |
| `area_su`             | `float`  | Площадь с/у                             |
| `area_hollway`        | `float`  | Площадь коридора                        |
| `area_wothout_bl_log` | `float`  | Площадь без балконов/лоджий             |
| `area_k1`             | `float`  | Площадь 1 компнаты                      |
| `area_k2`             | `float`  | Площадь 2 компнаты                      |
| `area_k3`             | `float`  | Площадь 3 компнаты                      |
| `area_k4`             | `float`  | Площадь 4 компнаты                      |
| `area_k5`             | `float`  | Площадь 5 компнаты                      |
| `glazing_type`        | `string` | Тип остеклкния                          |
| `windows_overlook`    | `string` | Вид из окна                             |
| `img_room`            | `string` | Путь к изображению планировки           |
| `img_floor`           | `string` | Путь к изображению планировки этажа     |
| `img_furniture`       | `string` | Путь к изображению планировки с мебелью |
| `apartment_type`      | `string` | Тип                                     |
