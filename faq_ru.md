# FAQ

### 1. Что это за торговый бот? Чем он отличается от других?
Gbot Trader является серверным торговым ботом. Это значит что его можно запускать на хостинге и дистанционно управлять им.<br> 
Так же бот может совершать более быстрые операции с ордерами. При хорошей связи с сервером API биржи бот может за секунду устанавливать более 30 ордеров. <br>
Нет ограничения на число торговых пар и апи ключей. Вы можете запускать несколько копий бота одновременно на одной или нескольких биржах (главное чтобы ключи не пересикались).<br>
Гибкая и в тоже время простая система настроек под разные ситуации на рынке. Не нужно самому писать торговые комбинации. <br>
 
### 2. Какие системные требования?
* Версия [Node.js](https://nodejs.org/en/download/current) 8 или выше.
* Версия Npm 5 или выше.
* Процессор i3 2.3Ghz или выше
* Оперативная память 100mb
* Место на диске 50mb
* Доступ в интернет

### 3. Какие платформы поддерживает Gbot Trader?
Gbot Trader поддерживает все современные платформы Windows, Mac, *unix.

Его можно устанавливаеть на любые PAAS-платформы и VDS/VPS. Например [heroku](https://signup.heroku.com/login), [pivotal](https://account.run.pivotal.io/z/uaa/sign-up), [UltraVDS](https://ultravds.com).

### 4. Нужны ли какие-то знания о трейдинге чтобы пользоваться им?
Любой бот это просто инструмент в руках трейдера. Как и любой инструмент, он облегчает и автоматизирует какие-либо действия трейдера. Т.е пользователь должен иметь хотя бы минимальные представления о трейдинге и понимать рынок, только в этом случае можно гарантировать заработок и минимизировать риски.
 
### 5. Какие минимальные знания нужны чтобы использовать бота?
Помимо знаний о торговле и рынке, желательно умение использовать git и начальные знания работы в консоле.
 
### 6. Как управлять этим ботом?
Бот может работать полностью автономно без вмешательства пользователя длинный промежуток времени. Но ботом можно и управлять используя мессенджер Telegram.
 
### 7. Что можно делать через Telegram?
- получить информацию об открытых ордерах
- информация о котировки рынка
- информация о последних сделках
- изменять тип торговли (полуручная торговля)
- переключатся между торговыми парами
- включать и выключать различные торговые параметры
- переключать торговые стратегии
- модифировать конфигурацию бота во время его работы
- получать уведомления о скачках курса
- получать уведомления об активных торговых парах
- … и многое другое.
 
### 8. Как установить бота?
Бота можно устанавливать как на локальный компьютер, так и на хостинг.<br />
Подробная инструкция об установке описана в [Readme](readme_ru.md)
 
### 9. Какие минимальные параметры нужно задать чтобы бот включился?
Для успешного старта бота необходимо задать Секретные ключи API биржи и Telegram.<br />
Если использовать Telegram не нужно, например у вас десятки торговых ботов, то можно его отключить указав параметр `TELEGRAM_OFF=true` или просто не указывать токен и id Telegram.
 
### 10. Можно ли использовать бота с настройками по умолчанию?
Можно, но толку от этого никакого.<br />
Для каждого рынка необходимо задавать свои настройки, т.к волатильность рынка везде разная, а значит и результат на одних и тех же настройках будет всегда разный. Для оптимального результата настройки нужно подбирать. Именно поэтому для использования любого торгового бота нужно иметь минимальные знания о рынке.
 
### 11. Какой набор минимальных параметров нужно задать чтобы понять как пользоваться ботом?
Самая безопасная стратегия, это стратегия “Усреднения”. <br />
Суть стратегии в том, что во время движения цены вниз, бот набирает позицию, а во время отскока цены вверх бот продает 1 ордером весь накопленный объем. <br />
Используя параметр Мартинейл `SIZE_ORDERS_MARTINGALE` каждый следующий ордер будет больше предыдущего, тем самым снижая цену продажи в зависимости от купленного объема.<br />
Для использования этой стратегии необходимо задать следующие параметры, на примере бирже Btc-e и торговой паре ltc/usd: <br />
```
TELEGRAM_OFF=true
KEY=ваш ключ
SECRET=ваш секрет
EXCHANGE=btc-e
NAME_COIN=ltc
NAME_COIN_TWO=usd
COUNT_ORDERS=20
SIZE_ORDERS_MARTINGALE=50
RANGE_OFFSET=10
ONE_ORDERS_SELL=true
ONE_ORDERS_SELL_PERCENT=1
ONE_ORDERS_SELL_OFFSET=1.5
```
Эти параметры не являются универсальными, и составлены они во время написания данного FAQ, так что в ваше время, они могут быть уже не сильно актуальны, но их достаточно чтобы понять как работает данная стратегия.
 
### 12. Как добиться максимальной прибыльности сделки?
Нужно подобрать оптимальную комбинацию параметров именно под используемую торговую пару.
 
### 13. Как уменьшить риски при работе с ботом в полностью автоматическом режиме?
Чем больше ордеров указано, тем лучше (больши запас прочности депозита).<br />
Уменьшите размер используемого депозита, указав разрешенный предел его использования.<br />
Увеличьте отступы между ордерами. Идеально, когда 70% всех ордеров будут исполняться при очень крупных обвалах цены, при этом в запасе остается 30% на непредвиденные сквизы.<br />
Но учтите чем больше запасы прочности, тем меньше прибыльность сделок. И наоборот, чем больше прибыльность сделки, тем больше рисков не продать купленный объем и стать инвестором.
 
### 14. Чем отличаются разные стратегии друг от друга?
**Стратегия “Скальпер”**. Данная стратегия используется когда на рынке стоит в основном флет и цена ходит в известном диапазоне. Скальпер разбрасывает сетку ордеров на покупку и продажу, и при исполнении ордера сразу же ставить противоположный.
 
**Стратегия “Линии Боллинджера”**. Это трендовая стратегия. Суть ее работы в том что когда рынок идет вверх, в какой то момент создается перекупленность рынка, и в этот момент по показаниям индикаторов будет производится продажа. Когда рынок начинает идти вниз, создается перепроданность рынка, и бот начинает делать покупки. Стратегия сложная, и требует соответствующих навыков ее использования и умения понимать торговые индикаторы.
 
**Стратегия “Усреднения”, она же “One Sell a lot Buy”**. Данная стратегия построена на логике покупки при движении цены вниз, накопления объема и продажи всего объема одним ордером при откате цены наверх. Является самой простой и наиболее безопасной стратегией.
 
### 15. Можно ли торговать ботом в ручную?
Да, боту можно давать команды чтобы бот только покупал или только продавал по требованию пользователя. Тем самым вы сами решаете когда необходимо делать покупки и продажи. Никаких самостоятельных решений бот принимать не будет, только установка ордеров и их отмена.
Для этого нужно перевести бота в стратегию “Скальпер” и в Telegram в типе торговли указать соответствующие действие.
 
### 16. Может ли бот помочь узнать на какой паре лучше работать?
Это сложная задача которая требует от пользователя понимания рынка. <br />
Бот может подсказать только на каких парах в данный момент происходит более менее заметное движение рынка. <br />
Анализируе эти данные вы можете принять решения входить в данную пару или нет.
 
### 17. Я не сижу за компьютером постоянно, как мне узнать что на рынке начался “пиздец”?
Бот может постоянно мониторить рынок на предмет резких изменений цен и прислать соответствующие уведомления.<br /> 
Все уведомления можно включить через Telegram в разделе “Нотис”. <br />
Для уведомлений необходимо задать через конфиг какие пары нужно мониторить и на какое отклонение от нормального спреда стоить реагировать.
 
### 18. Чем отличается параметры OFFSET_ORDERS_PERCENT и RANGE_OFFSET?
Параметром **OFFSET_ORDERS_PERCENT** вы указываете расстояние между ордерами, в процентах от цены.<br />
Параметром **RANGE_OFFSET** указывается размер всей необходимой сетки ордеров (разница между первым и последним ордеров. Другими словами сколько процентов изменения цены вы хотите поймать всей сеткой ордеров). Отступы между ордерами будут рассчитаны автоматически.
 
### 19. Как ограничить размер используемого депозита?
Для этого есть два параметра на выбор:

- **DEPOSIT_LIMIT_PERCENT** - указывается сколько процентов необходимо использовать.
- **DEPOSIT_LIMIT_CURRENCY** - указывается сколько конкретно валюты необходимо использовать (тип валюты определяется в параметром **NAME_COIN_TWO**).
 
### 20. Что такое шаг безубытка? Зачем нужен параметр STEP_BREAKEVEN_PERCENT?
Безубыток (breakeven) — это такой уровень цены, относительно открытой сделки, на котором нет ни прибыли, ни убытка.

**STEP_BREAKEVEN_PERCENT** используется только в стратегии “Скальпер”. И отвечает за то, когда начинать работать торговому боту. <br />
Если уровень спреда меньше этого параметра, тогда покупка и продажа будет производится в минус, чтобы этого избежать и введено данное ограничение. <br />
Чем больше указанный параметр, тем шире необходимо быть спреду чтобы бот начал работать.<br />
Параметр указывает насколько процентов должен быть выше спред уровня безубытка.
 
### 21. Что делается в автонастройках, для чего нужен параметр TIME_UPDATE_AUTO_SETTINGS?
В автонастройках рассчитываются все необходимые торговые параметры относительно указанных настроек пользователя через конфиг и текущих цен рынка.<br />
Параметр **TIME_UPDATE_AUTO_SETTINGS** отвечает с какой частотой будут пересчитываться эти торговые параметры.<br />
Слишком частое обновление это пустая трата вычислительных ресурсов. Слишком редкое обновление это пропуск различных ситуаций на рынке.
 
### 22. Что делает параметр QUANTITY_ORDERS_IN_BLOCKS. Чем он отличается от COUNT_ORDERS?
Параметр **COUNT_ORDERS** отвечает за общее количество ордеров.

Параметр **QUANTITY_ORDERS_IN_BLOCKS** контролирует сколько ордеров будет установлено за 1 раз, и при уменьшении этого числа добавлять новые ордера до указанного значения. 

Параметр **QUANTITY_ORDERS_IN_BLOCKS** не может быть больше **COUNT_ORDERS**, иначе в нем нет никакого смысла.
 
### 23. За что отвечает параметр INTEGRITY_CONTROL_ORDERS?
Данный параметр отвечает за целостность ордеров.

Иногда бывает что биржа по какой-либо причине не возвращает правильный объем купленных ордеров, или же просто теряет ордера. В такой ситуации неверно выставленный объем и цена SELL ордера приведет к убыточной сделке.
Чтобы как-то следить за этой ситуацией и используется как раз данный параметр.

В режиме **_hard_** ордер на продажу поставляется только в том случае, когда объем купленных позиций будет в точности совпадать с кешем бота. Это означает что все прошло гладко и ни 1 ордер не потерялся и не изменил свой объем.

В режиме **_soft_** (по умолчанию) ордер на продажу ставится в любом случае, даже если объем купленных позиций будет отличаться от данных которые возвращает биржа.

_В основном проблемы с потерей ордеров встречаются на бирже Poloniex._
 
### 24. Я запустил бота но он не ставит ордера.
Скорей всего это происходит по двум причинам:
 
 1. У вас недостаточно денег на счете, чтобы хватило на установку даже 1 ордера. Это бывает когда вы заходите маленьким депозитом в дорогие пары. Либо вы установили лимит на использование депозитов очень большой, и средств не хватило.
 
 2. У вас включена стратегия “Скальпер” и спред в текущей момент меньше чем уровень безубытка. (см п. 20)
 
### 25. Я нажимаю на кнопки в Telegram но бот не реагирует
Telegram это сторонний сервис со своим оборудованием. Так что могут случаться какие-либо сбои, и сообщения просто не отправляются или не доходят до торгового бота. Соответственно если бот не получает ни каких команд, он и не будет производить ответных действий.
Если вы сталкнулись с этой проблемой при первом запуске бота во время его установки, возможно вы не верно указали токен Telegram.
 
### 26. У меня много ботов, мне для каждого нужно создавать бота в Telegram?
Если вы хотите управлять и мониторить за ботом через Telegram и получать разные уведомления, то да.
Если же вы отстроили работу бота и никаких нареканий нет, то можно указать параметр `TELEGRAM_OFF=true` и бот не будет взаимодействовать с сервисом Telegram.
 
### 27. Как мне получать уведомления об ошибках если Telegram не работает?
Вы можете настроить уведомления об ошибках на вашу электронную почту.
Для этого необходимо указать следующие параметры:
```
EMAIL_REPORT_ADDRESS 
HOST_SMTP
EMAIL_AUTH_USER
EMAIL_AUTH_PASS
```
 
### 28. Я получаю непонятную ошибку error_code: 409, description: 'Conflict: terminated by other long poll or webhook'. Что это?
Это ошибка сервера Telegram, она говорит о том что вы используете 2 клиента с одним и тем же токеном. Этого делать нельзя. Проверьте, возможно у вас уже запущен бот с таким токеном или же какое-либо другое приложение.
 
### 29. Я хочу использовать несколько ботов одновременно, что для этого необходимо?
Необходимо для каждой копии бота создать собственные уникальные ключи и секреты от  API биржи, и при необходимости токены Telegram.

**Запрещено** использовать **на разных ботах одинаковые ключи**, это вызывает конфликты в работе между ботами.

Также следите чтобы на 1 аккаунте биржи не пересекались несколько ботов, иначе они могут не поделить общий депозит. 
 
### 30. Я запускаю бота на Windows, на локальном компьютере, мне необходимо постоянно вводить в консоль все параметры?
Да, если вы закрыли консоль, то все параметры будут потеряны.
Но вы можете написать bat файл, и в него прописать все необходимые параметры, а затем просто запускать этот файл.
Пример простого **start_bot_files.bat** выглядит так:
```
echo on
cd C:
cd директория_с_ботом

SET ПАРАМЕТР1=ЗНАЧЕНИЕ1
SET ПАРАМЕТР2=ЗНАЧЕНИЕ2
npm start
pause
```

Про SET и переменные окружения можно прочитать [здесь](http://ab57.ru/cmdlist/set.html) или [здесь](http://rus-linux.net/nlib.php?name=/MyLDP/BOOKS/Linux-tools/05/ltfwp-05-01.html).


### 31. Я торгую на бирже Poloniex и у меня начинается сыпаться куча ошибок.
Биржа Poloniex не очень любит торговых ботов. Поэтому использует очень жесткие ограничения, такие как ограничение на число запросов с одного IP адреса, частота запросов и др.
Вы можете установить параметры ограничения на запросы к API биржи:

**DELAY_REQUEST_API** - время в миллисекундах между запросами.

**RESTART_TRADER_TIME** - время в секундах через сколько пытаться повторить запрос после ошибки.

### 32. Биржа изменила комиссию на сделки, как ее поменять в настройках бота?

Для биржи Btc-e комиссия берется с сервера биржи, по этому в ручном изменении нет необходимости.

Для остальных бирж комиссию необходимо указать в ручную.
За это отвечает параметр **EXCHANGE_FEE**. По умолчанию комиссия на сделки составляет 0.25%. Комиссия указывается за сделку в одну сторону.

### 33. Я хочу знать что делает бот, какие расчеты ведет.
Вы можете установить параметры:

`LOG=true` - отображает общие расчеты торговли.

`LOG_DEBUG=true` - отображает более подробные расчеты при работе с ордерами.

Также вы можете указать тип лога через параметр **LOG_TRANSPORTS**.
И указать путь куда сохранять лог (параметр **LOG_PATH**), если выбрали вариант сохранения лога в файл. Если путь не указан, директория `logs` будет создана в корневой директории бота.

Эта информация вам может понадобиться для общения с разработчиками, если будут какие-то серьезные ошибки.
 
### 34. Как задавать параметры Вкл/Выкл в консоле?
Чтобы включить какой либо логический параметр необходимо присвоить ему значение true или 1.

Чтобы выключить параметр, нужно присвоить значение false или 0. Либо просто удалить данный параметр из настроек.
 
### 35. Я хочу изменить параметры при работе бота не выключая его, возможно ли это?
Да, это возможно. Некоторые параметры можно менять через Telegram.

Список параметров доступны по команде **/params** в Telegram.

Изменить параметр можно отправив в Telegram команду с указанием значения параметра. 
Например `OFFSET_ORDERS_PERCENT=1` изменит отступ между ордеров на 1%.

Все вновь введенные изменения будут применены когда произойдет новый перерасчет автопараметров. <br>
**Важно!** Если вы остановите бота, то новые параметры будут удалены. При запуске бота возьмутся параметры из конфига.

### 36. Я остановил бота до того как он продал ордер Sell в стратегии “One Sell a lot Buy”, а после запуска бот не видит купленные ордера.
При запуске стратегии "One Sell a lot Buy" начальное состояние баланса основной валюты в паре игнорируется.

Но бот может посмотреть историю последних сделок и выставить недавно купленные ордера, но только до первого Sell ордера.

Для этого используйте параметр `FIRST_LOADING_HISTORY=true`.

Если вы хотите чтобы при старте бот попытался продолжить сетку ордеров от последнего значения используйте параметр `CONTINUE_MARTINGALE_GRID=true`.


### 37. Почему иногда автоматически изменяется размер отступов ордеров и не работает тот который указал пользователь?
Включена опция `DYNAMIC_OFFSET_ORDERS`. Это **автостраховка** если ваши параметры расчета сетки ордеров не подошли под условия рынка.

Если вы используете отступы в пунктах (опция `OFFSET_ORDERS_POINTS`) тогда бот автоматически изменит размер отступов если будет увеличено нормальное значение спреда выше критических значений (300%, 380% или 450% от нормы).

Если вы используете отступы в процентах (опция `OFFSET_ORDERS_PERCENT` или `RANGE_OFFSET`) тогда проверяется разница цены за интервал времени (1 час) и если значение превышает указанный пользовательский размер, бот будет использовать данные этой разницы.

Например, вы указали значение `RANGE_OFFSET=10`, текущая цена $9, пол часа назад было $7 тогда дельта цены будет 22%, и отступы пересчитаются уже при значении `RANGE_OFFSET=22`.
 
Так же меняется параметр `ONE_ORDERS_SELL_PERCENT`. Он ставится равный RANGE_OFFSET / 10, но не меньше юзерского значения.

Имейте ввиду, что расчет происходит не мгновенно при изменении цены, а с интервалом указанном в `TIME_UPDATE_AUTO_SETTINGS` (см. п.21). 

Так же отступы не будут пересчитаны на уже установленных ордерах. Чтобы не устанавливать все ордера сразу используйте опцию `QUANTITY_ORDERS_IN_BLOCKS` (см. п.22). 
 
### 38. Я хочу изменить часовой пояс. Как это сделать?
Используйте параметр **TIME_ZONE**. Список всех временных зон можно посмотреть тут [Database Time Zones](https://en.wikipedia.org/wiki/List_of_tz_database_time_zones) в колонке TZ.

Например для Москвы значение будет `TIME_ZONE=Europe/Moscow`

### 39. Анализ торговли за сессию, как его читать?

Анализ отображается когда сработает функция "**Авто выход из пары**" или "**Закрыть все ордера**".

Анализ считается сравнением начального баланса с текущим балансом аккаунта. 

При использовании параметра `FIRST_LOADING_HISTORY` из первой валюты будет вычтен размер кэша. При этом во вторую валюту будет добавлено значение профита/убытка от совершенной сделки. Дальше все данные будут считаться как есть.

Если параметр `FIRST_LOADING_HISTORY` **не использовался**, данные будут считаться как есть.

**Total** - показывает абсолютное значение депозита, т.е сумму двух валют на момент анализа по последней цене рынка. Это значение может меняться как в большую так и в меньшию сторону, так как привязано к текущей цене на момент анализа.

**Установлено ордеров** - сколько всего ордеров было установлено за время работы бота с момента его включения.

**Исполнено ордеров** - сколько ордеров было исполнено.

**Перезапусков** - Сколько раз бот перезапрашивал данные при ошибках в ответе api биржи.

```
Анализ торговли за сессию:
0 PPC  | 0%
0.47512 $ | 0.9%
Total: 0.47512 $ | 0.9%  по цене: 2.458
Установлено ордеров: 31
Исполнено ордеров: 13
Перезапусков: 0
```

**Важно!**
 
* Данные являются не точными, так как расчитываются на основании рынка и не учитывают разные погрешности цен и округления. Не стоит воспринимать как точную статистику. Реальные данные баланса вы можете узнать только в ЛК биржи.
* Если на одном аккаунте запущено несколько ботов в расчет могут попадать профиты/убытки от другого бота. 
* Если в стратегии "One Sell a lot Buy" включен `FIRST_LOADING_HISTORY`, то до тех пор весь кэш не будет распродан, значение профита второй валюты будет отрицательным.


### 40. Типичные ошибки в консоле бота
Иногда в консоле могу появлятся сообщения об ошибках, например:

* `ESOCKETTIMEDOUT` или `ETIMEDOUT`  - это сетевые ошибки, вызванные отсутствием ответа от биржи или отсутствием соединением с интернетом.
* `INSUFFICIENT_FUNDS` - недостаточно средств для установки ордера. (Встречается на бирже Bittrex. Уменьшите размер использования депозита, чтобы на балансе оставался небольшой резерв).

Эти не критические ошибки и бот с ними успешно справится. Они выводятся только для уведомления пользователя. Вмешательства пользователя не требуется.

##### Ошибки связанные с настройками бота.

* `There is no KEY or SECRET api exchange`  - Не указан API KEY или SECRET KEY.
* `Not valid pair` - Не правильно указана торговая пара. (Попробуйте инвертировать название пары. Проверьте правильность указанной биржи).
* `There is no token Telegram` - Не указан токен Telegram. (Если вы не хотите использовать Telegram используйте `TELEGRAM_OFF=true`).

##### Ошибки связанные с настройками биржи.
* `APIKEY_INVALID`  - не правельно указан API KEY или SECRET KEY (Укажите верные ключи, проверьте на наличие лишних пробелов).
* `INVALID_PERMISSION` - на Bittrex, означает что вы не прошли верификацию для торговли.


### 41. Модули автоконфигурации. Как они работают?
Модули автоконфигурации вносят коррективы в заданные настройки пользователя при незапланированных ситуациях на рынке.

**DANGER_PRICE_STOP** - параметр поставит бота на паузу если за короткий период цена изменилась больше чем на 9%, например резкий сквиз. Так же пользователю будет выслано уведомление в Telegram. Будут закрыты Buy ордера если скачек был вверх.

**DYNAMIC_SETTINGS_TIME** - параметр включает автоматическую регулировку скорости обновления автонастроек.
Если за определенный период (50 циклов) разница между high и low price будет больше 2% тогда скорость обновления автонастроек будет увеличена.

**DYNAMIC_OFFSET_ORDERS** - Параметр **автоматически изменит размер отступов** и уровень безубытка если на рынке образуются шпили (см п. 37).

**TREND_DEFINITION - Параметр включает попытку определение направления тренда. Только для стратегии "Скальпер"**.<br>

**Зачем это нужно?**<br>
Идея в том что если начался памп, то чуток по позже продать, а при дампе - купить.

**Условия срабатывания:**<br>
Если текущая цена bid и ask выше чем прошлое значение этих цен, а так же текущий уровень безубытка стал выше 200% (появилась свеча) и скорость бота в режиме _normal_ то тренд восходящий.
Если текущие цены ниже чем прошлые цены... , то тренд нисходящий.

**Что происходит:**<br>
Если все условия выполнены, то сетка ордеров по тренду растягивается, а сетка ордеров с противоположной стороны стакана сжимается до минимальных отступов рассчитанных системой.<br>
Если выключен ручной тип торговли и работает auto (ALL) тогда ордера по направлению тренда будут закрыты, до следующего перерасчета цикла.


**ABRUPT_CHANGE_TREND - Является доп. опцией параметра `TREND_DEFINITION`. Только для стратегии "Скальпер"**.<br>

**Зачем это нужно?**<br>
Если начался резкий памп или дамп с огромной свечой, то лучше сразу закупится по максимуму по текущей цене или распродать соответственно.

**Условия срабатывания:**<br>
Все условия из параметра `TREND_DEFINITION`, только размер возникшего уровня безубытка больше 400% от нормы.

**Что происходит:**<br>
Происходит выставление ордеров выше/ниже текущей цены bid или ask (смотря какой ордер) тем самым совершается покупка/продажа по рынку.<br>
Размер ордера рассчитывается как N / 2, т.е каждый следующий ордер будет в 2 раза меньше предыдущего (чтобы самим не создать сквиз).<br>
После этого сразу же запускается новый цикл перерасчета автопараметров.


**OFF_MODULES_AUTO_SETTINGS** - включает или выключает сразу все выше указанные параметры.


### 42. Я установил на Windows node.js но получаю в консоле сообщение "node не является внутренней или внешней командой" (npm not found)

1. Удалите установленную node.js.
2. Установите node.js в директорию windows. В пункте выбора директории установки измените program files на windows.

### 43. Что такое Мартингейл. Для чего он используется?
Мартингейл - это система управления ставками. Суть ее заключается в том, что каждая следующая ставка должна перекрывать убыток предыдущей.

Для управления Мартингейл используются параметры:

* **SIZE_ORDERS_MARTINGALE** - насколько увеличить ордер от стандартного. Каждый следующий ордер будет больше предыдущего на этот размер.
* **MARTINGALE_TYPE** - какой тип увеличения ордера использовать.
* **CONTINUE_MARTINGALE_GRID** - продолжать ли сетку ордеров с использованием Мартингейл при перезапуске бота. Если выключена, сетка начнется с 0. Если включено, будет найдена сумма ордеров с одинаковой ценой последней в стеке и от нее продолжена сетка.

### 44. Для чего нужны TIME_CLOSE_ORDERS и TIME_CLOSE_ORDERS_INACTIVITY?

**TIME_CLOSE_ORDERS** - Если во время работы бота какие-то ордера не будут исполнены в течении указанного времени, они будут закрыты и сетка пересчитается заново.
<br> Это нужно для того чтобы держать ровную сетку. Т.к во время работы скальпера ордера могут 'откусывать рынком' по чуть-чуть и собираться в кучу на одной цене.
<br> Так же это позволяет сдвигать ордера если рынок движется.

**TIME_CLOSE_ORDERS_INACTIVITY** - Если рынок стоит и ни одной сделки не совершается, а так же спред упал ниже уровня безубытка, то этот параметр закроет ордера.

По умолчанию `TIME_CLOSE_ORDERS_INACTIVITY = 3 * TIME_CLOSE_ORDERS`

### Как использовать этого бота на других биржах?
Вы можете использовать бота на любой крипто бирже, для этого вам нужно написать api к бирже или промежуточное програмное обеспечение которое сконвертирует данные из api биржи в api бота.

Как это сделать написано здесь: [middleware exchange api](middleware_exchange_api.md). 
 