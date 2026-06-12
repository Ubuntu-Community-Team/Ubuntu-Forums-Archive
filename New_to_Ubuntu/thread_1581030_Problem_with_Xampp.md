---
title: "Problem with Xampp"
date: 2010-09-24
forum: New to Ubuntu
---

### Post by aaricia on 2010-09-24
Hello Ubuntu-ers,

I have checked about this problem in other Linux fora but the solution given is not working for me, that is why I am asking here.

I have installed xampp as I thought that it would be easier than having to set up a virtual host every time that I need to set up a development site.

Before running xampp, I stop the previous apache and mysql demons by doing:

sudo /etc/init.d/apache2 stop
sudo /etc/init.d/mysql stop

then I launch xampp (from terminal):

cd /opt/lampp
sudo ./lampp start


Then, when I try to call Mysql from the console I get the following error message:

ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

I have tried to link the mysqld.sock file with the xampp one (as adviced) but nothing.

In the solution I have seen, no one seems to be using xampp.

The thing is: I have downloaded the database from our production drupal site, and it is so big (230 MB) that the only way I can import it in phpmyadmin is by mysql commands. 

I thought that xampp could make easier to handle multiple development sites (like wamp)) but I wasn't expected this problems. 

Any suggestion would be very much appreciated.

Thank you.

---

### Post by okplayer02 on 2010-09-24
a simple search of google about this error shows that mysql is not running

and as you stated in your situation you stopped mysql then try to run XAMPP

[http://ubuntuforums.org/showthread.php?t=804021](http://ubuntuforums.org/showthread.php?t=804021)

take a look at this thread its an old one but still relevant to you

---

