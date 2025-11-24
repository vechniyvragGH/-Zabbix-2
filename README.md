   # Домашнее задание к занятию «Система мониторинга Zabbix. Часть 2»

## Дорожкин Артем Сергеевич


#### В практике есть 4 основных и 5 дополнительных (со звездочкой) заданий. Основные задания нужно выполнять обязательно, со звездочкой - по желанию и его решение никак не повлияет на получение вами зачета по этому домашнему заданию, при этом вы сможете глубже и/или шире разобраться в материале.

Пожалуйста, присылайте на проверку все задачи сразу. Любые вопросы по решению задавайте в чате учебной группы.

#### <ins>Цели задания</ins>

1. Научиться создавать свои шаблоны в Zabbix, добавлять в Zabbix хосты и связывать шаблон с хостами

2. Научиться составлять кастомный дашборд

3. Научиться создавать UserParameter на Bash

4. Научиться создавать Python-скрип, добавляться в него UserParameter и прикреплять к шаблону

5. Научиться создавать Vagrant-скрипты для Zabbix Agent

#### <ins>Чеклист готовности к домашнему заданию</ins>

Просмотрите в личном кабинете занятие "Система мониторинга Zabbix. Часть 2"

#### <ins>Инструкция по выполнению домашнего задания</ins>

1. Сделайте fork репозитория c шаблоном решения к себе в Github и переименуйте его по названию или номеру занятия, например, https://github.com/имя-вашего-репозитория/gitlab-hw или https://github.com/имя-вашего-репозитория/8-03-hw).

2. Выполните клонирование этого репозитория к себе на ПК с помощью команды git clone.

3. Выполните домашнее задание и заполните у себя локально этот файл README.md:

   - впишите вверху название занятия и ваши фамилию и имя;
   
   - в каждом задании добавьте решение в требуемом виде: текст/код/скриншоты/ссылка;
   
   - для корректного добавления скриншотов воспользуйтесь инструкцией «Как вставить скриншот в шаблон с решением»;
   
   - при оформлении используйте возможности языка разметки md. Коротко об этом можно посмотреть в инструкции по MarkDown.

4. После завершения работы над домашним заданием сделайте коммит (git commit -m "comment") и отправьте его на Github (git push origin).

5. Для проверки домашнего задания преподавателем в личном кабинете прикрепите и отправьте ссылку на решение в виде md-файла в вашем Github.

6. Любые вопросы задавайте в чате учебной группы и/или в разделе «Вопросы по заданию» в личном кабинете.


## Задание 1
 Создайте свой шаблон, в котором будут элементы данных, мониторящие загрузку CPU и RAM хоста.

#### <ins>Процесс выполнения</ins>

1. Выполняя ДЗ сверяйтесь с процессом, отражённым в записи лекции
   
3. В веб-интерфейсе Zabbix Server`a в разделе Templates создайте новый шаблон
   
5. Создайте Item который будет собирать информацию об загрузке CPU в процентах
   
7. Создайте Item который будет собирать информацию об загрузке RAM в процентах
   
#### <ins>Требования к результату</ins>

 1. Прикрепите в файл README.md скриншот страницы шаблона с названием «Задание 1»
    
---
<ins>Шаг 1: Создание шаблона Templates</ins>

   Configuration - Templates:

      - Create template

      - Template - CPU_RAM_Monitoring

      - Save
---------


<ins>Шаг 2: Создание Items</ins>

   Добавление элемента данных для мониторинга загрузки CPU:

      - Items

      - Create item

      - Заполнить поля:

            Name: CPU Usage (%)

            Type: Zabbix agent

            Key: system.cpu.load[percpu,avg1]

            Type of information: Numeric (float)

            Units: %

   Добавление элемента данных для мониторинга загрузки RAM:

      - Item

      - Create item

      - Заполнить поля:

            Name: RAM Usage (%)

            Type: Zabbix agent

            Key: vm.memory.size[pused]

            Type of information: Numeric (float)

            Units: %

<ins>Шаг 3: Применение шаблона к хостам</ins>

   Применить шаблон к хостам:

      - Configuration > Hosts.

      - Выбрать хост и нажать Templates.

      - Select и найти свой шаблон Template CPU_RAM_Monitoring.

      - Выбрать нужный шаблон и нажать Add, затем Update или Save.

<ins>Шаг 4: Проверка работы шаблона</ins>

   Перейти в раздел Monitoring > Latest data.

   Выбрать хост, к которому применили шаблон, и проверить, что новые элементы с данными по CPU и RAM отображаются корректно.

<img width="1680" height="595" alt="image" src="https://github.com/user-attachments/assets/4020232d-9f05-4bfe-a96a-9ceb92cfa723" />

<img width="1670" height="700" alt="image" src="https://github.com/user-attachments/assets/0a46cfc1-eaf1-4dd3-abae-ea156d0b8f7e" />

<img width="1711" height="762" alt="image" src="https://github.com/user-attachments/assets/0f2af62d-bb37-47ea-921a-b88f6c9cbf97" />

<img width="1701" height="721" alt="image" src="https://github.com/user-attachments/assets/9072cd89-0a95-4560-9cec-02387b4c0451" />

<img width="1542" height="822" alt="image" src="https://github.com/user-attachments/assets/c251ab65-fd7a-4592-abc1-67d4173550ef" />

<img width="1338" height="816" alt="image" src="https://github.com/user-attachments/assets/933f6dea-16a9-42e2-988c-d018742060d6" />








<img width="1442" height="298" alt="image" src="https://github.com/user-attachments/assets/13b98063-9f44-4d6b-b85f-6b54b075ea24" />


<img width="1777" height="345" alt="image" src="https://github.com/user-attachments/assets/20484a08-0e02-4ffa-a856-bafa15c8f52e" />


 
<img width="1230" height="808" alt="Снимок экрана 2025-11-19 005252" src="https://github.com/user-attachments/assets/87a1c012-2366-4e97-ab13-fa539c2dfc0b" />

<img width="990" height="748" alt="Снимок экрана 2025-11-19 010114" src="https://github.com/user-attachments/assets/43182f07-fc96-4267-8893-9888f1d76223" />

<img width="1602" height="436" alt="image" src="https://github.com/user-attachments/assets/6c1477a5-3cd3-4396-825d-b904e8abddb5" />




---

## Задание 2
 Добавьте в Zabbix два хоста и задайте им имена <фамилия и инициалы-1> и <фамилия и инициалы-2>. Например: ivanovii-1 и ivanovii-2.

### <ins>Процесс выполнения</ins>

1. Выполняя ДЗ сверяйтесь с процессом отражённым в записи лекции

2. Установите Zabbix Agent на 2 виртмашины, одной из них может быть ваш Zabbix Server

3. Добавьте Zabbix Server в список разрешенных серверов ваших Zabbix Agentов

4. Добавьте Zabbix Agentов в раздел Configuration > Hosts вашего Zabbix Servera

5. Прикрепите за каждым хостом шаблон Linux by Zabbix Agent

6. Проверьте что в разделе Latest Data начали появляться данные с добавленных агентов
   
#### <ins>Требования к результату</ins>

 1. Результат данного задания сдавайте вместе с заданием 3

---

## Задание 3
 Привяжите созданный шаблон к двум хостам. Также привяжите к обоим хостам шаблон Linux by Zabbix Agent.

#### <ins>Процесс выполнения</ins>

1. Выполняя ДЗ сверяйтесь с процессом отражённым в записи лекции

2. Зайдите в настройки каждого хоста и в разделе Templates прикрепите к этому хосту ваш шаблон

3. Так же к каждому хосту привяжите шаблон Linux by Zabbix Agent

4. Проверьте что в раздел Latest Data начали поступать необходимые данные из вашего шаблона
   
#### <ins>Требования к результату</ins>

 1. Прикрепите в файл README.md скриншот страницы хостов, где будут видны привязки шаблонов с названиями «Задание 2-3». Хосты должны иметь зелёный статус подключения

---

<ins>Шаг 1: Добавление хостов в Zabbix Server</ins>

     - Перейти в раздел Configuration → Hosts
     
     - Нажать на кнопку Create host
     
     - Для каждого хоста:
     
          Имя: DorozhkinAS-1 для первой машины и DorozhkinAS-2 для второй
          
          DNS Name или IP Address: Добавить IP-адрес
          
          Groups: Присоединиться одной из существующих групп или создайте новую
          

<ins>Шаг 2: Добавить Zabbix Agent в список разрешённых серверов</ins>

      - /etc/zabbix/zabbix_agentd.conf на каждой виртуальной машине добавлены IP-адреса Zabbix сервера в настройки Server=

<ins>Шаг 3: Сохранить все изменения</ins>

<ins>Шаг 4: Привязка шаблонов</ins>

      - Templates
      
      - Select, чтобы выбрать шаблоны
      
      - Найти Template Linux by Zabbix Agent и прикрепить его к каждому хосту

<ins>Шаг 5: Проверка данных</ins>

      - Monitoring → Latest data
      
      - Выбрать хосты и убедитесь, что данные собираются корректно


<img width="1731" height="543" alt="image" src="https://github.com/user-attachments/assets/a25f82c4-65a6-4887-8f07-01d1da254f50" />


<img width="1602" height="436" alt="image" src="https://github.com/user-attachments/assets/6bd7f44f-bc56-4994-bee5-a615dc015772" />

<img width="1883" height="812" alt="image" src="https://github.com/user-attachments/assets/35288f3b-660b-4412-85f0-c3e73d02316f" />


<img width="1717" height="817" alt="image" src="https://github.com/user-attachments/assets/5f0bcc4b-376b-4021-9426-979a86ff10cb" />


---



      ## Задание 4
 Создайте свой кастомный дашборд.

#### <ins>Процесс выполнения</ins>

1. Выполняя ДЗ сверяйтесь с процессом отражённым в записи лекции

2. В разделе Dashboards создайте новый дашборд

3. Разместите на нём несколько графиков на ваше усмотрение
   
#### <ins>Требования к результату</ins>

 1. Прикрепите в файл README.md скриншот дашборда с названием «Задание 4»

---

<img width="1637" height="812" alt="image" src="https://github.com/user-attachments/assets/072727ad-edcb-4be1-b6ac-8712a98f59d4" />

