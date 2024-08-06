Ansible роль Docker
=========

Роль для установки и настройки Docker.

Требования
------------

Роль предназначена для использования в операционных системах:

- Astra Linux 1.7
- Rocky Linux 8.7

Параметры роли
--------------

| Название                         | Значение по умолчанию   |  Описание                               |
|----------------------------------|-------------------------|-----------------------------------------|
| niitp_docker_user                | tasp                    | Пользователь для запуска конетейнеров   |
| niitp_docker_group               | opertasp                | Группа для запуска конетейнеров         |
| niitp_docker_maclabel            | 0                       | Мандатная метка запущенных контейнеров  |
| niitp_docker_log_max_size        | 10m                     | Максимальный размер лог-файла           |
| niitp_docker_log_max_file        | 10                      | Максимальное количество лог-файлов      |
| niitp_docker_data_root           | *1                      | Путь размещения данных Docker           |
| niitp_docker_unsecure_registries | []                      | Добавление разрешения на работу с небезопасным репозиторием |

> Примечание 1:
>
> В Rocky Linux: /var/lib/docker
>
> В Astra Linux: /var/lib/rootlessdocker/{{ niitp_docker_user }}/l{{ niitp_docker_maclabel }}i0c0x0t0x0/.local/share/docker

Зависимости
------------

Для ОС Astra Linux:

- niitp.maclabel

Пример использования
----------------

В репозитории содержатся параметры для установки и настройки Docker для ПК ТА
в директории [environments/tasp](./environments/tasp)

    - hosts: all
      roles:
         - niitp.docker

```sh
ansible-playbook site.yml
```
