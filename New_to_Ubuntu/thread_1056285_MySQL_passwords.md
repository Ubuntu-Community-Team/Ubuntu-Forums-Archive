---
title: "MySQL passwords"
date: 2009-01-31
forum: New to Ubuntu
---

### Post by danpantry on 2009-01-31
OK, So I´ve installed mysql-server, mysql-server-5.0, mysql-client. I´ve been trying to get into the database, but it says
```

ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)

```
when I use $mysql -u root, and 
```

ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)

```
when I use $mysql -u root -p. I have no idea of my mySQL password, and this is what I am trying to get. I am using it over SSH, so there is no GUI, and I don´t know how I can make a password when I install it. When I try to install mysql-client, mysql-server, and libmysql, I get this
```

VQA001:/home/danpantry# apt-get install mysql-server mysql-client libmysqlclient15-dev
Reading package lists... Done
Building dependency tree... Done
mysql-client is already the newest version.
libmysqlclient15-dev is already the newest version.
The following extra packages will be installed:
  mysql-server-5.0
Suggested packages:
  tinyca
The following NEW packages will be installed:
  mysql-server mysql-server-5.0
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/25.3MB of archives.
After unpacking 67.8MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
Selecting previously deselected package mysql-server-5.0.
(Reading database ... 25090 files and directories currently installed.)
Unpacking mysql-server-5.0 (from .../mysql-server-5.0_5.0.32-7etch8_i386.deb) ...
Unpacking mysql-server (from .../mysql-server_5.0.32-7etch8_all.deb) ...
Stopping MySQL database server: mysqld.
Setting up mysql-server-5.0 (5.0.32-7etch8) ...
Stopping MySQL database server: mysqld.
Starting MySQL database server: mysqld . . . . . . . . . . . . . . failed!
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.0 (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.0; however:
  Package mysql-server-5.0 is not configured yet.
dpkg: error processing mysql-server (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 mysql-server-5.0
 mysql-server
E: Sub-process /usr/bin/dpkg returned an error code (1)
VQA001:/home/danpantry#

```
Anyone got any idea? 

Thanks in advance

---

### Post by schwascore on 2009-01-31
The password must be set during installation. There is a prompt that you must have skipped over somehow that requires you to set the root mysql password.

Try a re-install and this time make sure to watch for this prompt.


EDIT:

After reading more of the output you posted, make sure you actually remove mysql-server and then install it again.
```

sudo apt-get remove mysql-server
sudo apt-get autoclean
sudo apt-get install mysql-server

```

---

### Post by danpantry on 2009-01-31
Nope, I get no password prompt. Here is the log I got when I used your commands:
```
VQA001:/etc/init.d# sudo apt-get remove mysql-server-5.0
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  mysql-server-5.0
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 67.7MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 26631 files and directories currently installed.)
Removing mysql-server-5.0 ...
Stopping MySQL database server: mysqld.
VQA001:/etc/init.d# sudo apt-get autoclean
Reading package lists... Done
Building dependency tree... Done
VQA001:/etc/init.d# sudo apt-get install mysql-server
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  mysql-server-5.0
Suggested packages:
  tinyca
The following NEW packages will be installed:
  mysql-server mysql-server-5.0
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/25.3MB of archives.
After unpacking 67.8MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
Selecting previously deselected package mysql-server-5.0.
(Reading database ... 25090 files and directories currently installed.)
Unpacking mysql-server-5.0 (from .../mysql-server-5.0_5.0.32-7etch8_i386.deb) ...
Selecting previously deselected package mysql-server.
Unpacking mysql-server (from .../mysql-server_5.0.32-7etch8_all.deb) ...
Stopping MySQL database server: mysqld.
Setting up mysql-server-5.0 (5.0.32-7etch8) ...
Stopping MySQL database server: mysqld.
Starting MySQL database server: mysqld . . . . . . . . . . . . . . failed!
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.0 (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.0; however:
  Package mysql-server-5.0 is not configured yet.
dpkg: error processing mysql-server (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 mysql-server-5.0
 mysql-server
E: Sub-process /usr/bin/dpkg returned an error code (1)
VQA001:/etc/init.d# 

```

EDIT: 

It seems like Mysqld does NOT want to start. I killalled, did it again and it said none killed, then I try reinstalling and nothing, it´s always failing on the starting mysqld bit >.<

---

