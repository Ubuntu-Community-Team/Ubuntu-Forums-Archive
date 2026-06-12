---
title: "XAMPP installation in ubuntu 9.10 help wanted"
date: 2009-11-22
forum: New to Ubuntu
---

### Post by chaotic_clone01 on 2009-11-22
Hi,
I am  trying to install  XAMPP 1.7[latestversion] in ubuntu 9.10 but the problem is the MySql is  not working in it. and  when i  do this command[i dont know y people use this]

 sudo ps aux | grep mysql
The output is  :

root      4295  0.0  0.0   1748   540 pts/0    S    18:58   0:00 /bin/sh /usr/bin/[COLOR=Red]mysqld[/COLOR]_safe
[COLOR=Red]mysql[/COLOR]     4403  0.0  1.7 128908 18020 pts/0    Sl   18:58   0:06 /usr/sbin/mysqld --basedir=/usr --datadir=/var/lib/mysql --user=[COLOR=Red]mysq[/COLOR]l --pid-file=/var/run/mysqld/mysqld.pid --socket=/var/run/mysqld/mysqld.sock --port=3306
root      4404  0.0  0.0   2932   688 pts/0    S    18:58   0:00 logger -t m[COLOR=Red]ysqld -[/COLOR]p daemon.error
ravi      4673  0.2  2.1  56372 22136 ?        S    19:01   0:14 /usr/bin/[COLOR=Red]mysql[/COLOR]-query-browser
ravi      5339  0.0  0.0   3036   804 pts/0    S+   20:50   0:00 grep --color=auto mysql


I dont  know  what  to do. Can anyone help .Thanks in advance

---

### Post by headlessspider on 2009-11-22
from the output it seems that mysql *is running*. its the same output i have with my setup (more or less)

---

### Post by chaotic_clone01 on 2009-11-23
but when i do [http://localhost](http://localhost) then the  status of the mysql is  DEACTIVATED   .Do u know  how to  enable it?

---

### Post by louieb on 2009-11-23
Its been a few years since I used xampp, so not much help with your current problem. 

In the future you might consider using tasksel  to set up your lamp server. Works great.  

```
sudo tasksel install lamp-server
```

or to see a list of the different things it can install
```
tasksel --list-tasks | less
```

---

### Post by headlessspider on 2009-11-24
you can try

```
sudo /opt/lampp/lampp startmysql
```

---

### Post by bilalakhtar on 2009-11-24
> **louieb said:**
> Its been a few years since I used xampp, so not much help with your current problem. 

In the future you might consider using tasksel  to set up your lamp server. Works great.  

```
sudo tasksel install lamp-server
```

or to see a list of the different things it can install
```
tasksel --list-tasks | less
```

Tasksel worked great for installing LAMP in my case till Ubuntu 9.04 Jaunty, but in Karmic (9.10) the same thing can be done by the following command:-
```
sudo apt-get install lamp-server^
```
This is a better way to do things, as it directly uses APT.

---

