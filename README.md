Ansible Role: Astra Atestat ALD
=========

Эта роль выполнит настройку нескольких АРМ на базе ОС Astra Linux SE версий 1.5, 1.6, 1.7, подключенных к локальной сети, в соответствии с требованиями безопасности для обработки конфеденциальной информации (аттестационные мероприятия). С помощью роли можно установить и настроить систему управления службой ALD (контроллер домена и клиенты), создать общий сетевой репозиторий (main и update) на контроллере домена, установить оперативные обновления операционной системы с общий сетевой репозитория, создать пользователей в системе ALD и настроить директории для хранения конфеденциальной информации с различным уровнем мандатного доступа, а также предоставить сетевой доступ клиентам ALD в эту директорию. Предполагается что ISO-образы основного диска и диска с обновлениями расположены на контроллере домена в домашней директории пользователя в директории astra, параметр `astra_at_ald_iso_path: /home/user/astra`.

Requirements
------------

Для хоста, на котором запускается эта роль необходимы следующие требования:
```
sshpass
rsync
pexpect >= 3.3
```

Role Variables
--------------

Доступные переменные перечислены вместе со значениями по умолчанию в файле **defaults/main.yml**.
Переменные отвечающие установку оперативных обновлений и обновление загрузчика grub (по умолчанию `false`):
```
astra_at_ald_os_update: false
astra_at_ald_grub_edit: false
```
Выбор способа установки обновления (штатный способ `dist_upgrade` или через утилиту `astra_update`, рекомендуемую разработчиками Astra):
```
astra_at_ald_os_update_tool: astra_update
```
Переменная для создания пользователей ALD для работы под мандатным уровнем доступа (имя пользователей и общий пароль):
```
astra_at_ald_domain_users: 
  - user1
  - user2
astra_at_ald_domain_users_password: 1qaz!QAZ
```

Dependencies
------------

None.

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - astra_at_ald

License
-------

BSD

Author Information
------------------

Chubik Sergey.