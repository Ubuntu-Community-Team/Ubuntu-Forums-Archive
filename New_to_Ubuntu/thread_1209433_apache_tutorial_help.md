---
title: "apache tutorial help"
date: 2009-07-10
forum: New to Ubuntu
---

### Post by benh13 on 2009-07-10
I have successfully managed to install apache2, however, does anybody know of any online tutorials or help sites that could help me understand and learn to use apache?
thanks

---

### Post by DGortze380 on 2009-07-10
> **benh13 said:**
> I have successfully managed to install apache2, however, does anybody know of any online tutorials or help sites that could help me understand and learn to use apache?
thanks

The default configuration will work. It's always a good idea to learn about it and security it a little, but just go ahead put your HTML files in 

/var/www

check with a web browser with either your internal IP or localhost

---

### Post by Majorix on 2009-07-10
You don't need Apache at all if you are going to learn HTML only. Apache is only worth the trouble if you are going to do server-side scripting, like PHP or Rails.

---

### Post by benh13 on 2009-07-10
i plan to use the whole LAMP thing, using php and all. i have downloaded mysql and php5, i just need to learn how to use them together, i am learning how to write in php.

---

### Post by Celauran on 2009-07-10
There isn't really much to using Apache. The only recommendation I'd make is to set up [virtual hosts](http://httpd.apache.org/docs/2.2/vhosts/) with DocumentRoot in your home directory. The Apache site itself has a tremendous wealth of information. Ubuntu Community Documentation also has a good article on [LAMP](https://help.ubuntu.com/community/ApacheMySQLPHP).

---

### Post by Cheesemill on 2009-07-10
> **benh13 said:**
> i plan to use the whole LAMP thing, using php and all. i have downloaded mysql and php5, i just need to learn how to use them together, i am learning how to write in php.

I really hope you didn't download MySQL and PHP from their websites. This is not the way to do things in Ubuntu.

To install the entire LAMP stack you just need to do a:
```
sudo apt-get install lamp-server^
```

---

### Post by Celauran on 2009-07-10
> **Cheesemill said:**
> 
To install the entire LAMP stack you just need to do a:
```
sudo tasksel install lamp-server
```
Fixed that for you.

---

### Post by snek on 2009-07-10
I just replied this to another thread, but you will find these links very useful I think, they taught me most that I know now :)

> 
Don't have much time to go into this problem, but I'm pretty much sure you can find your answer on how to configure Apache/PHP/MySQL in these articles:

[http://articles.slicehost.com/2008/4/25/ubuntu-hardy-installing-apache-and-php5](http://articles.slicehost.com/2008/4/25/ubuntu-hardy-installing-apache-and-php5)
[http://articles.slicehost.com/2008/4/28/ubuntu-hardy-apache-config-layout](http://articles.slicehost.com/2008/4/28/ubuntu-hardy-apache-config-layout)
[http://articles.slicehost.com/2008/4/28/ubuntu-hardy-apache-configuration-1](http://articles.slicehost.com/2008/4/28/ubuntu-hardy-apache-configuration-1)
[http://articles.slicehost.com/2008/4/28/ubuntu-hardy-apache-configuration-2](http://articles.slicehost.com/2008/4/28/ubuntu-hardy-apache-configuration-2)

There's many, many more excellent articles on [http://articles.slicehost.com]("http://articles.slicehost.com/") if you want to dive a bit deeper into setting up a webserver!

Example for VHOSTS setup (hosting multiple domains on one webserver):
[http://articles.slicehost.com/2008/4/29/ubuntu-hardy-apache-virtual-hosts-1](http://articles.slicehost.com/2008/4/29/ubuntu-hardy-apache-virtual-hosts-1)
[http://articles.slicehost.com/2008/4/29/ubuntu-hardy-apache-virtual-hosts-2](http://articles.slicehost.com/2008/4/29/ubuntu-hardy-apache-virtual-hosts-2)

Personally I use Zend Server CE a modded PHP5 version which is many, many times faster than the standard one that comes with Ubuntu repositories..
It's really simple to setup as well!!
[http://files.zend.com/help/Zend-Server-Community-Edition/zend-server-community-edition.htm#deb_installation.htm](http://files.zend.com/help/Zend-Server-Community-Edition/zend-server-community-edition.htm#deb_installation.htm)
If you do go with Zend Server CE be sure to also install **[B]php5-extra-extensions-zend-**[/B]**[B]ce**[/B]


---

### Post by Cheesemill on 2009-07-10
> **Celauran said:**
> Fixed that for you.

Mine wasn't broken !!

---

### Post by Celauran on 2009-07-10
> **Cheesemill said:**
> Mine wasn't broken !!

```
Couldn't find any package whose name or description matched "lamp-server"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

It is on my system.

---

### Post by Cheesemill on 2009-07-10
> **Celauran said:**
> ```
Couldn't find any package whose name or description matched "lamp-server"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```It is on my system.

You missed the caret, its lamp-server^

---

### Post by Celauran on 2009-07-10
Tried both, actually. Same result. Anyways, if yours works for you, maybe it works for the OP as well. Different versions, I guess. If it doesn't work for OP, then he can try mine.

---

### Post by Cheesemill on 2009-07-10
```
rob@robuntu:~$ sudo apt-get install lamp-server^
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libwrap0 is already the newest version.
libmysqlclient15off is already the newest version.
tcpd is already the newest version.
ssl-cert is already the newest version.
mysql-common is already the newest version.
libwrap0 is already the newest version.
libmysqlclient15off is already the newest version.
tcpd is already the newest version.
ssl-cert is already the newest version.
mysql-common is already the newest version.
The following extra packages will be installed:
  apache2 apache2-mpm-prefork apache2-utils apache2.2-common libapache2-mod-php5 libapr1 libaprutil1 libdbd-mysql-perl libdbi-perl libhtml-template-perl libnet-daemon-perl
  libplrpc-perl libpq5 mysql-client-5.0 mysql-server mysql-server-5.0 mysql-server-core-5.0 php5-common php5-mysql
Suggested packages:
  apache2-doc apache2-suexec apache2-suexec-custom php-pear dbishell libipc-sharedcache-perl mysql-doc-5.0 tinyca mailx
The following NEW packages will be installed
  apache2 apache2-mpm-prefork apache2-utils apache2.2-common libapache2-mod-php5 libapr1 libaprutil1 libdbd-mysql-perl libdbi-perl libhtml-template-perl libnet-daemon-perl
  libplrpc-perl libpq5 mysql-client-5.0 mysql-server mysql-server-5.0 mysql-server-core-5.0 php5-common php5-mysql
0 upgraded, 19 newly installed, 0 to remove and 2 not upgraded.
Need to get 41.8MB of archives.
After this operation, 128MB of additional disk space will be used.
Do you want to continue [Y/n]? 
```The lamp-server^ package will only work with apt-get, not aptitude (ever since Hardy anyway).

---

### Post by Celauran on 2009-07-10
Ahh. That explains it. I never use apt-get, always aptitude.

---

### Post by Cheesemill on 2009-07-10
> **Celauran said:**
> Ahh. That explains it. I never use apt-get, always aptitude.

I only ever use apt-get for the above command, usually I always use aptitude as well.

---

### Post by ashishkum on 2009-07-13
hi i am also looking to install LAMP on my Ubuntu...

i gave the following command


abc@abc-laptop:~$ sudo apt-get install lamp-server
[sudo] password for abc:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package lamp-server

do you know the solution for this??

i am running Ubuntu desktop version 7.10

thanks

---

### Post by Celauran on 2009-07-13
As Cheesemill mentioned above, you've omitted the caret.

```
sudo apt-get install lamp-server^
```

If that doesn't work, you can always use

```
sudo apt-get install apache2 php5 mysql
```

---

### Post by Mornedhel on 2009-07-13
> **Celauran said:**
> As Cheesemill mentioned above, you've omitted the caret.

Somewhat offtopic : I haven't found any documentation on the caret in the apt-get man page and googling for apt-get caret obviously returns a lot of unrelated results. Can you enlighten me ? I always used the caret in the regexp anchor sense, it's weird seeing it at the end of a line...

---

### Post by Celauran on 2009-07-13
It's a new one on me, also. Whatever it is, it's apt-get specific and doesn't work with aptitude. Seems to emulate tasksel behaviour.

---

### Post by ashishkum on 2009-07-13
> **Celauran said:**
> As Cheesemill mentioned above, you've omitted the caret.

```
sudo apt-get install lamp-server^
```

i have used the above command

```

abc@abc-laptop:~$ sudo apt-get install lamp-server^
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
E: Couldn't find task lamp-server

```

> **Celauran said:**
> 
If that doesn't work, you can always use

```
sudo apt-get install apache2 php5 mysql
``` 

i tried this too...here is the output
```
abc@abc-laptop:~$ sudo apt-get install apache2 php5 mysql
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package apache2

```

---

### Post by Celauran on 2009-07-13
Maybe the lamp-server^ thing was introduced with Hardy.

```
sudo aptitude search apache
```

What does that give?

---

### Post by ashishkum on 2009-07-13
> **Celauran said:**
> Maybe the lamp-server^ thing was introduced with Hardy.

```
sudo aptitude search apache
```

What does that give?


when i run this command i get nothing

```

abc@abc-laptop:/$ sudo aptitude search apache
abc@abc-laptop:/$ 

```

---

### Post by Celauran on 2009-07-13
Are you still running 7.10 as suggested by your profile? Support for Gutsy ended in April.

---

### Post by ashishkum on 2009-07-13
> **Celauran said:**
> Are you still running 7.10 as suggested by your profile? Support for Gutsy ended in April.

yeah am running gusty...i think you are right the problem is in the support...do you have any solution in your mind??

---

### Post by benh13 on 2009-07-14
i just intstalled lamp using sudo apt get install for apache, php, and mysql individually

---

### Post by benh13 on 2009-07-14
putting files onto var/www seems to work

---

### Post by ashishkum on 2009-07-14
> **benh13 said:**
> putting files onto var/www seems to work

hi can you please explain in detail

---

### Post by benh13 on 2009-07-15
putting files you want to run onto your server into the var folder in the file system, then the www folder. then to view the files, just type [http://localhost/(file](http://localhost/(file) you want). you might need to use sudo commands to gain permission to move the files into var/www in file system.

---

