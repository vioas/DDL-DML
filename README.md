## Домашнее задание к занятию «Работа с данными (DDL/DML)»
### Инструкция по выполнению домашнего задания
1.Сделайте fork репозитория c шаблоном решения к себе в Github и переименуйте его по названию или номеру занятия, например, https://github.com/имя-вашего-репозитория/gitlab-hw или https://github.com/имя-вашего-репозитория/8-03-hw).
2. Выполните клонирование этого репозитория к себе на ПК с помощью команды git clone.
3. Выполните домашнее задание и заполните у себя локально этот файл README.md:
 - впишите вверху название занятия и ваши фамилию и имя;
 - в каждом задании добавьте решение в требуемом виде: текст/код/скриншоты/ссылка;
 - для корректного добавления скриншотов воспользуйтесь инструкцией «Как вставить скриншот в шаблон с решением»;
 - при оформлении используйте возможности языка разметки md. Коротко об этом можно посмотреть в инструкции по MarkDown.
4. После завершения работы над домашним заданием сделайте коммит (git commit -m "comment") и отправьте его на Github (git push origin).
5. Для проверки домашнего задания преподавателем в личном кабинете прикрепите и отправьте ссылку на решение в виде md-файла в вашем Github.
6. Любые вопросы задавайте в чате учебной группы и/или в разделе «Вопросы по заданию» в личном кабинете.

Желаем успехов в выполнении домашнего задания.

Задание можно выполнить как в любом IDE, так и в командной строке.

### Задание 1
1.1. Поднимите чистый инстанс MySQL версии 8.0+. Можно использовать локальный сервер или контейнер Docker.

Предварительно нужно установить пакет gnupg. Если не устанавливали, то:

apt-get install gnupg

Установим MySQL APT репозиторий, переходим на страничку:

https://dev.mysql.com/downloads/

Последний пакет называется mysql-apt-config_0.8.25-1_all.deb, копируем ссылку на него. Загрузим пакет:

cd /tmp

wget -c https://dev.mysql.com/get/mysql-apt-config_0.8.25-1_all.deb

ls -fla | grep mysql

Установим пакет:

dpkg -i mysql-apt-config_0.8.25-1_all.deb

После установки пакета в /etc/apt/source.list.d/ добавится mysql.list.

Обновляем репозиторий:

apt-get update

Установим MySQL сервер.

apt-get install mysql-server

В процессе установки нас просят установить пароль пользователя root для MySQL. Выбираем плагин аутентификации по умолчанию. Рекомендуется Strong Password Encryption. Ok. Установка завершена.

![image](https://github.com/vioas/DDL-DML/assets/142601752/d532f866-dee2-4c1e-b45f-c597509e515e)


1.2. Создайте учётную запись sys_temp.
Вход в консоль MySQL: mysql -u root -p

CREATE USER 'sys_temp'@'localhost' IDENTIFIED BY 'password';

####1.3. Выполните запрос на получение списка пользователей в базе данных. (скриншот)

mysql> SELECT user FROM mysql.user

alt text

1.4. Дайте все права для пользователя sys_temp.
mysql> GRANT ALL PRIVILEGES ON . TO 'sys_temp'@'localhost';

1.5. Выполните запрос на получение списка прав для пользователя sys_temp. (скриншот)

mysql> SHOW GRANTS FOR 'sys_temp'@'localhost';
alt text

1.6. Переподключитесь к базе данных от имени sys_temp. Для смены типа аутентификации с sha2 используйте запрос:

ALTER USER 'sys_temp'@'localhost' IDENTIFIED WITH mysql_native_password BY 'password';

1.6. По ссылке https://downloads.mysql.com/docs/sakila-db.zip скачайте дамп базы данных.

1.7. Восстановите дамп в базу данных.

alt text

1.8. При работе в IDE сформируйте ER-диаграмму получившейся базы данных. При работе в командной строке используйте команду для получения всех таблиц базы данных. (скриншот)

alt text alt text alt text Результатом работы должны быть скриншоты обозначенных заданий, а также простыня со всеми запросами.

### Задание 2 
Составьте таблицу, используя любой текстовый редактор или Excel, в которой должно быть два столбца: в первом должны быть названия таблиц восстановленной базы, во втором названия первичных ключей этих таблиц. Пример: (скриншот/текст)

Название таблицы | Название первичного ключа customer | customer_id

alt text


### Дополнительные задания (со звёздочкой*)
Эти задания дополнительные, то есть не обязательные к выполнению, и никак не повлияют на получение вами зачёта по этому домашнему заданию. Вы можете их выполнить, если хотите глубже шире разобраться в материале.

### Задание 3*
3.1. Уберите у пользователя sys_temp права на внесение, изменение и удаление данных из базы sakila.

3.2. Выполните запрос на получение списка прав для пользователя sys_temp. (скриншот)

Результатом работы должны быть скриншоты обозначенных заданий, а также простыня со всеми запросами.
