---
title: "LAMP stack - Apache error message in line 222"
date: 2016-01-05
forum: Networking &amp; Wireless
---

### Post by rene16 on 2016-01-05
Hello fellow linuxers:


  I would like to link my laptop to my Android phone and Android  tablet, which hasn't been possible via bluetooth or directly through USB  / mini-USB ports.


  A friend on another linux forum advised me to install a LAMP server  and using instructions from around the 'net I got the Apache server  working ... for a while.


  I got to the point where I could get Firefox to display the apache  test page, but since attempting to install the remaining components of  the LAMP stack (MySql and PHP), the apache bit I had going has stopped  working.


  I am troubleshooting apache2, because I get the following error message when I try to run apache from the Terminal :


  **Restarting web server apache2 [fail]**[INDENT][B]The apache2 configtest failed. 

The output of config test was:

 apache2: Syntax error on line 222 of /etc/apache2/apache2.conf: Could  not open configuration file /etc/phpadmin/apache.conf: No such file or  directory Action 'configtest' failed.[/B]
[/INDENT]
 
Now I am confused, because as well as not really understanding the  concept of a LAMP stack to begin with, I think I took too many different  bits of advice on how to install it.

 
I don't know how to fix line 222, but I think the problem is because I  altered some of the apache files, following advice in the article [URL="http://ubuntuserverguide.com/2014/06/how-to-install-lamp-in-ubuntu-server-14-04-lts.html"]http://ubuntuserverguide.com/2014/06/how-to-install-lamp-in-ubuntu-server-14-04-lts.html

[/URL]

  I was also taking tips from [URL="https://www.digitalocean.com/commun...x-apache-mysql-php-lamp-stack-on-ubuntu-14-04"]https://www.digitalocean.com/commun...x-apache-mysql-php-lamp-stack-on-ubuntu-14-04

[/URL]Please can anyone tell me how I get apache working again, or whether I need to reinstall it?

 
I will be grateful enough to offer praise and prayers to Jesus for  your health and well-being, even if you are just reading this.


  :-D

---

### Post by ajgreeny on 2016-01-05
For the USB connection have you followed all the info in the thread at [http://ubuntuforums.org/showthread.php?t=2226702](http://ubuntuforums.org/showthread.php?t=2226702)

I have managed to get all our Android machines (2 phones and two tablets) to connect with no problem to Trusty by doing all that is shown there.

I can't help with a lamp server stack as I've never used any of the server systems available.

---

