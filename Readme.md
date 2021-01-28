## ユーザー管理サーバではFluentd不要

## ファイル構成

```
.
├── Readme.md
├── group_vars
│   └── all.yml
├── playbook.yml
└── roles
    ├── apache
    │   ├── files
    │   │   ├── 00-proxy.conf
    │   │   ├── 10-proxy_h2.conf
    │   │   ├── autoindex.conf
    │   │   ├── httpd.conf
    │   │   ├── userdir.conf
    │   │   ├── vhost.conf
    │   │   └── welcome.conf
    │   ├── handlers
    │   │   └── main.yml
    │   └── tasks
    │       └── main.yml
    ├── codedeploy
    │   └── tasks
    │       └── main.yml
    ├── common
    │   ├── tasks
    │   │   ├── change_root_password.yml
    │   │   ├── cloud_cfg.yml
    │   │   ├── disabled_ec2-user.yml
    │   │   ├── locale.yml
    │   │   ├── logrotate.yml
    │   │   ├── main.yml
    │   │   ├── pkg_install.yml
    │   │   ├── selinux.yml
    │   │   ├── sudoers.yml
    │   │   ├── timezone.yml
    │   │   └── user_group.yml
    │   ├── templates
    │   │   └── logrotate.conf
    │   └── vars
    │       └── main.yml
    ├── efs
    │   ├── tasks
    │   │   └── main.yml
    │   └── vars
    │       └── main.yml
    ├── fluentd
    │   ├── files
    │   │   ├── td-agent.conf
    │   │   └── td.repo
    │   ├── handlers
    │   │   └── main.yml
    │   └── tasks
    │       └── main.yml
    ├── mysql
    │   └── tasks
    │       └── main.yml
    ├── php
    │   └── tasks
    │       ├── files
    │       │   └── php.ini
    │       └── main.yml
    ├── postfix
    │   ├── files
    │   │   └── sasl_passwd
    │   ├── handlers
    │   │   └── main.yml
    │   └── tasks
    │       └── main.yml
    ├── tripwire
    │   ├── defaults
    │   │   └── main.yml
    │   ├── files
    │   │   ├── ch-hostname.service
    │   │   ├── ch-hostname.sh
    │   │   ├── tripwire-check.sh
    │   │   ├── tripwire-set.sh
    │   │   └── twpolmake.pl
    │   ├── handlers
    │   │   └── main.yml
    │   ├── meta
    │   │   └── main.yml
    │   ├── tasks
    │   │   └── main.yml
    │   └── templates
    │       └── etc
    │           └── tripwire
    │               ├── tripwire-check.sh.j2
    │               ├── twcfg.txt.j2
    │               └── twpol.txt.j2
    └── wordpress
        ├── handlers
        │   └── main.yml
        └── tasks
            └── main.yml
```

## 手動で変更が必要な部分

```
role
- vault_pass.sh
```

```
role
- common
  - tasks
    - change_root_password.yml
```

```
role
- efs
  - vars
    - main.yml
```

```
role
- postfix
  - files
    - sasl_passwd
```

```
role
- fluentd
  - files
    - td-agent.conf
```

```
role
- tripwire
  - files
    - tripwire-check.sh
    - tripwire-set.sh
```