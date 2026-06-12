---
title: "php not working with apache2"
date: 2007-03-06
forum: Networking &amp; Wireless
---

### Post by sarwatj on 2007-03-06
hi

I am a newbie with opensource i need 2 get the lamp architecture up and running in a weeks time and PHP is not working with apache2 on my ubuntu-desktop dapper machine 

The error i get is that the browser starts downloading the php page 

and if i add the following code in httpd.conf 

> include etc/apache2/mods-enabled/php.load
include etc/apache2/mods-enabled/php.conf

i get the following error

> prj-cusp@mcusp-platform:~/Desktop/apache2/bin$ ./httpd
httpd: Syntax error on line 445 of /home/prj-cusp/Desktop/apache2/conf/httpd.conf: Syntax error on line 1 of /etc/apache2/mods-enabled/php5.load: API module structure `php5_module' in file /usr/lib/apache2/modules/libphp5.so is garbled - perhaps this is not an Apache module DSO?

I have libapache2-mod-php5 and i have also used a2enmod php5 which runs successfully
and restarted my server after that as well but results do not change

---

### Post by Mr. C. on 2007-03-06
It looks like you've built these yourself ?

Show the lines from the error messages, line 445 and line 1, as the two errors indicate.

MrC

---

### Post by sarwatj on 2007-03-06
these are lines 445 and 446 from httpd.conf 

> Include /etc/apache2/mods-enabled/php5.load
Include /etc/apache2/mods-enabled/php5.conf

and this is php5.load line 1 

> LoadModule php5_module /usr/lib/apache2/modules/libphp5.so

---

### Post by Mr. C. on 2007-03-06
You did not answer my other question.  Did you build this yourself, or find these modules precompiled somewhere?

Please describe as much as you can about how you installed or built apache, php, etc.

Did your system already have an apache or php installed as well?

This is a build problem, or compatibility problem due to using a binary that was not built for your environment.

MrC

---

### Post by sarwatj on 2007-03-06
I used apache-2.2.4 from the official apache site and the rest of the packages (mysql and php ) from packages.ubuntu 

i have apache installed on the desktop using --prefix and the rest of the components are installed in default locations

no other options are enabled with apache at configure time

---

### Post by sarwatj on 2007-03-06
should i try the apache2 package available at packages.ubuntu

---

### Post by Heliix on 2007-03-06
there is an easy-to install and easy-to-setup package xampp, that offers Apache, MySQL, PHP & PEAR, Perl, ProFTPD, phpMyAdmin, OpenSSL and other things:
[http://www.apachefriends.org/en/xampp.html](http://www.apachefriends.org/en/xampp.html)

you should try this, i'm quite happy with it :) . if you aren't satisfied, it is also easy to remove

---

### Post by Mr. C. on 2007-03-06
There's your problem.  You cannot mix and match pre-built and home spun components in general.

Either build all of them yourself, or install all from packages.

MrC

---

### Post by sarwatj on 2007-03-07
oh so thats the problem i installed the apache2 packages but by then i had messed my system enough to have nothing working anyways did a reinstall of ubuntu and tried out xampp.Its a nice precompiled all in one life saving package 

thanks for the help

---

