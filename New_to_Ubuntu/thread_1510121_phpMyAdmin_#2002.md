---
title: "phpMyAdmin #2002"
date: 2010-06-15
forum: New to Ubuntu
---

### Post by thorbs on 2010-06-15
Hi after the last update I have had trouble.

For some reason the install goes wrong. The updater still wants to install it. 

I have fixed broken packages in the package manager.

I have tried to read threads about this error on the forum (and other forums) and have tried many of the suggested solutions without luck. 


This is my work this morning:

thorbs@Thorbs:~$ ps aux | grep mysql
thorbs    3020  0.0  0.0   3324   812 pts/0    S+   09:11   0:00 grep --color=auto mysql
thorbs@Thorbs:~$ mysqld_safe &
[1] 3162
thorbs@Thorbs:~$ 100615 09:12:59 mysqld_safe Logging to syslog.
100615 09:12:59 mysqld_safe Starting mysqld daemon with databases from /var/lib/mysql
100615 09:13:01 mysqld_safe mysqld from pid file /var/lib/mysql/Thorbs.pid ended
thorbs@Thorbs:~$ mysql -u root -p
Enter password: 
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
[1]+  Done                    mysqld_safe
thorbs@Thorbs:~$ dpkg -l mysql* | grep ii | awk '{ print $2 }'
mysql-client-5.1
mysql-client-core-5.1
mysql-common
mysql-server
mysql-server-5.1
mysql-server-core-5.1
thorbs@Thorbs:~$ 



As far as I understand 5.1 is installed (the update that keeps going wrong and that the update manager still wants to install) and the server is started.

Do you have any sugestions as how I could fix this?

I maybe should add, that I had it up and running before the update. I am not sure if I remember the password, but my password manager, fills it out automatically, when I go into phpMyAdmin, but with the #2002 as a result.

---

### Post by thorbs on 2010-06-15
Maybe I should clarify that it is the update of MySQL to 5.1. It is as far as I can see installed and running. 

But I get the Error #2002 when I try to lock into phpMyAdmin. 

I have succesfully repaired the broken packages.

Some how it was not running and I turned it on using the safemode. 


But I still gets the #2002 at the phpMyAdmin.

I have tried the different sollutions that I have been able to see on the forum, but I am not able to fix it.

---

### Post by thorbs on 2010-06-15
Anybody able to help with this?

---

### Post by thorbs on 2010-06-15
Ok, I succesfully purged mysql and re-installed it succesfully, but I still get the same erro. 

I really dont know what to do. 

I feel I am in way over my head, trying solutions I can find in the forum, but having a feeling that I might just make it all worse. 

If I cant make this work, I will have to leave Ubunu. It will be a major defeat for myself, but also I am having a hard time to see how ubuntu should be a mainstream program. It really seems that I apparently really dont have the skills or the knowledge to be part of this community. If nobody can help I will have to leave it at that....

---

### Post by bodhi.zazen on 2010-06-15
I do not know your problem , but you should probably file a bug report on launchpad.

[http://ubuntuforums.org/showthread.php?p=9458255](http://ubuntuforums.org/showthread.php?p=9458255)

---

### Post by thorbs on 2010-06-15
ok bodhi, I will do that. But what about my system. I am at school learning php, so I really need the mysql. But I just dont know how to get anywhere with this. Should I reinstall the 10.04? Should I go back to an earlier version of ubuntu, another linux version, windblows?

---

### Post by indytim on 2010-06-15
I don't have a specific remedy either.  My suggestion at this point would be to do a fresh install of phpMyAdmin directly from phpMyAdmin.  Pay particular attention to the password blowfish instructions.

[ttp://www.phpmyadmin.net/home_page/index.php]("ttp://www.phpmyadmin.net/home_page/index.php")

IndyTim / DataMan

---

### Post by bodhi.zazen on 2010-06-15
> **thorbs said:**
> ok bodhi, I will do that. But what about my system. I am at school learning php, so I really need the mysql. But I just dont know how to get anywhere with this. Should I reinstall the 10.04? Should I go back to an earlier version of ubuntu, another linux version, windblows?

Assuming you updated 9.10 -> 10.04 , the only solution I know is to re-install, wither 9.10 and do not upgrade or go with 10.04.

---

