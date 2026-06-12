---
title: "zabbix from repositorie don't allow postgresql!"
date: 2007-11-21
forum: Networking &amp; Wireless
---

### Post by derbouka on 2007-11-21
Hello!

There is bug on the version from zabbix in the repositorie that don't allow to install zabbix using Postgresql...

Basically I've installed:
[LIST]
[*]zabbix-agent
[*]zabbix-frontend-php
[*]zabbix-server-pgsql
[/LIST]
Here I didn't had any troubles, but when I went to [http://localhost/zabbix](http://localhost/zabbix) and start to configure it, I've received the following error's:
```
2. Licence Agreement
Missing licence file. See GPL licence.
```
```
3. Check of pre-requisites
PHP max execution time:	30 sec	Fail
PHP Timezone:	n/a	Fail

```
Had to manually edit the file "/etc/php5/apache2/php.ini" and correct the "date.timezone"([http://us3.php.net/manual/en/timezones.php](http://us3.php.net/manual/en/timezones.php)) and "max_execution_time" and restart the apache.

```

4. Configure DB connection

    * mysql_pconnect() [function.mysql-pconnect]: Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)[/usr/share/zabbix/include/db.inc.php:46]
    * Cannot modify header information - headers already sent by (output started at /usr/share/zabbix/include/config.inc.php:21)[/usr/share/zabbix/include/page_header.php:58]
    * Cannot modify header information - headers already sent by (output started at /usr/share/zabbix/include/config.inc.php:21)[/usr/share/zabbix/include/config.inc.php:1859]

```Put my configurations from postgresql, even thought I've received an "OK" in "Test connection"
So... Basically I had to remove zabbix_server_pgsql and install zabbix-server-mysql... 
And zabbix-server-mysql don't have an mysql dependence, which I had to manually install mysql-server and only then I could install the zabbix-server-mysql, 

Ok, I hope that someone can fix this in future versions!

Best regards

---

### Post by Blutack on 2007-11-21
You need to report it as a bug.

---

### Post by derbouka on 2007-11-24
By the way, can you point me in the right direction, to be able to create .deb files?

---

