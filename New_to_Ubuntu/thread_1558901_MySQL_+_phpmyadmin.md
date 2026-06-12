---
title: "MySQL + phpmyadmin"
date: 2010-08-22
forum: New to Ubuntu
---

### Post by kendel on 2010-08-22
I been going off old outdate guides and informaion around the internet and nothing is working

I have 2 Servers
Server A running apache, php, phpmyadmin
Sever B running MySQL

Server A has IP of 192.168.1.110
Server B has IP of 192.168.1.120

I edited /etc/phpmyadmin/config.inc.php

to have these:
$cfg['Servers'][$i]['host'] = 'MySQL IP Address'; // MySQL hostname
$cfg['Servers'][$i]['port'] = 'port number'; // MySQL port 
$cfg['Servers'][$i]['extension'] = 'mysql';
$cfg['Servers'][$i]['connect_type']= 'tcp';
$cfg['Servers'][$i]['compress'] = false;
$cfg['Servers'][$i]['auth_type'] = 'config';
$cfg['Servers'][$i]['user'] = 'username'; // MySQL user
$cfg['Servers'][$i]['password'] = 'password'; // MySQL password 


(This par was confusing to I just re-added the line above instead of searching for it all).

Then I set the MySQL vi /etc/mysql/my.cnf to comment out #bind-address = 127.0.0.1
There is another line that most of the guides asked me to comment out but I cannot find that like: # skip-networking

The Next closest match to that is: skip-external-locking

I will assume that is not it and leave it alone....

I keep getting errors for example: "Cannot start session without errors, please check errors given in your PHP and/or webserver log file and configure your PHP installation properly"

Another error was it canno connect because it is not accepting connections from the IP Address of my webserver...

Can anyone help?

---

### Post by sandyd on 2010-08-22
> **kendel said:**
> I been going off old outdate guides and informaion around the internet and nothing is working

I have 2 Servers
Server A running apache, php, phpmyadmin
Sever B running MySQL

Server A has IP of 192.168.1.110
Server B has IP of 192.168.1.120

I edited /etc/phpmyadmin/config.inc.php

to have these:
$cfg['Servers'][$i]['host'] = 'MySQL IP Address'; // MySQL hostname
$cfg['Servers'][$i]['port'] = 'port number'; // MySQL port 
$cfg['Servers'][$i]['extension'] = 'mysql';
$cfg['Servers'][$i]['connect_type']= 'tcp';
$cfg['Servers'][$i]['compress'] = false;
$cfg['Servers'][$i]['auth_type'] = 'config';
$cfg['Servers'][$i]['user'] = 'username'; // MySQL user
$cfg['Servers'][$i]['password'] = 'password'; // MySQL password 


(This par was confusing to I just re-added the line above instead of searching for it all).

[B]Then I set the MySQL vi /etc/mysql/my.cnf to comment out #bind-address = 127.0.0.1
There is another line that most of the guides asked me to comment out but I cannot find that like: # skip-networking[/B]

The Next closest match to that is: skip-external-locking

I will assume that is not it and leave it alone....

I keep getting errors for example: "Cannot start session without errors, please check errors given in your PHP and/or webserver log file and configure your PHP installation properly"

Another error was it canno connect because it is not accepting connections from the IP Address of my webserver...

Can anyone help?
try changing changing bind-address to your server's LAN address instead of commenting it out

---

### Post by kendel on 2010-08-22
Ok now I get this when I try to set it up:
 
Access Denied Error 1045 (28000) for user @ domain (using password YES) etc...

---

### Post by sandyd on 2010-08-23
> **kendel said:**
> Ok now I get this when I try to set it up:
 
Access Denied Error 1045 (28000) for user @ domain (using password YES) etc...

your typing the passwd wrong

---

### Post by kendel on 2010-08-23
OMG i got it....thank you...its working now:lolflag:

---

### Post by kendel on 2010-08-23
back to square one... what might have changed to cause #2002 Cannot log in to the MySQL server??

---

