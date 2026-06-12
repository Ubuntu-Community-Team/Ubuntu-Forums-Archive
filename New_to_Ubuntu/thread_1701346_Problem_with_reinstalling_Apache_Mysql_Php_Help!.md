---
title: "Problem with reinstalling Apache Mysql Php Help!"
date: 2011-03-06
forum: New to Ubuntu
---

### Post by imrairai on 2011-03-06
Hi, just what to ask about my problem in reinstalling Apache, Mysql and php. I really dont know what to do next, whole day i've been trying to solve this problem.

FIrst, I installed mysql server, mysql administrator and mysql query browser. It works just fine. But later I installed xampp. Problem is the xampp i installed has a bundle ( with mysql, apache and php5 already) so i got some errors after installing it because I made a mistake of having 2 mysql installed (one i installed earlier and the one from xampp) and 2 apache. I got this errors:

another mysql daemon is running

and 

another web server daemon is running

What i did was stop mysql and apache

i enter this command to the terminal:

sudo /etc/init.d/apache2 stop

and

sudo /etc/init.d/mysql stop

After doing this xamp finally works but i now i can't access mysql. this error shows:

[FONT=Arial][SIZE=1][COLOR=Black]**Can't connect to local MySQL server through socket  '/var/run/mysqld/mysqld.sock' (2)**[/COLOR][/SIZE][/FONT]

after everything i decided to start from scratch again so i uninstall mysql and xampp, i cant with apache2 because it says that the package is damaged.

After all of this, now i cant reinstall them because of this

imrairai@imrairai-laptop:~$ sudo apt-get install apache2
[sudo] password for imrairai: 
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

T_T

---

