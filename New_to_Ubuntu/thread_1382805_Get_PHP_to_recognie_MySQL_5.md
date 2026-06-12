---
title: "Get PHP to recognie MySQL 5"
date: 2010-01-16
forum: New to Ubuntu
---

### Post by TorMike on 2010-01-16
Help!

I followed the LAMP installation procedure from 'www.howtoforge.com/ubuntu_lamp_for_newbies' and got everything installed and running except when I called phpinfo() I noticed that MySQL was not listed.

I think it's because I never ran the:

sudo apt-get install libapache2-mod-auth-mysql php5-mysql phpmyadmin

because I didn't want to install phpmyadmin (it sucks).

My question is:

Is this the missing command? And can I; stop the apache server, run the install without the phpmyadmin and restart the apache to 'link' mySQL to PHP so that when I run phpinfo() I'll see MySQL listed?

Thanks from a Ubuntu newbie that loves it.

---

### Post by Cheesemill on 2010-01-16
Yes you can, just run:
```
sudo apt-get install libapache2-mod-auth-mysql php5-mysql
```
to finish the installation.



For future reference you could have just done:
```
sudo apt-get install lamp-server^
```
to do Apache, MySQL, and PHP all in one go.

---

### Post by TorMike on 2010-01-16
Great!  Thank-you.  Worked like a charm.

This next question is just for my own information:

I've installed Apache2/PHP/MySQL on other platforms and always had to configure apache via the httdp.conf file.  Yet is appears as though that file on Ubuntu is either not used or ignored.  I went looking for found it /etc/apache2/httdp.conf but it was empty.  I issued a UNIX find command and found the file under host directory (dual boot XP sector).  

So why no configuration file required for apache?

---

### Post by Cheesemill on 2010-01-16
In Ubuntu the httpd.conf file has been depreciated in favour of individual configuration files for each site. The defaults are in /etc/apache2/sites-available/default. If you copy this file and make any changes you want and save it /etc/apache2/sites/available/mysite you can then use:
```
sudo a2ensite mysite
```to enable mysite and:
```
sudo a2dissite mysite
```to disable it.

This method is used so you can disable, make changes to, and enable individual sites without having to restart apache in it's entirety. It also makes troubleshooting easier than having one large global configuration file.

httpd.conf can still be used for global settings if you wish.

---

### Post by halitech on 2010-01-16
I think some Debian based distros have moved from using /etc/apache2/httpd.conf to using /etc/apache2/apache2.conf. Not sure on all distros but Debian and Ubuntu for sure.

---

### Post by TorMike on 2010-01-16
Unbelievable! 

I've only been using this O/S for a couple of days and I'm blown away at just how great it is.  

Sure, there is a learning curve, but most of the problems I've run into very cause by... ME.

I've been using UNIX forever and us fossils just can't give up setting configuration files and file/folder permission that easily.  It's always been, download files, untar, /install, modify Apache2/PHP/MySQL configuration files, restart apache.

Sometimes you just have to pull the finger out of your bum.

Amazing!

I just install mysql query browser via the ubuntu database.  Where do I find of list of all the available apps?  I'm like a kid in a candy store.  More More MORE!!

One more thing, This community as got to be the most responsive I've ever been involve with.  I post a inquiry and longest I've ever waited was a few hours for a response.

Who ever and where ever you guys are, pat yourselves on the back for a job well done.

Amazing!  Just said that again didn't I.

---

