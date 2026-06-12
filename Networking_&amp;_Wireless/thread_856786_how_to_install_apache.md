---
title: "how to install apache?"
date: 2008-07-11
forum: Networking &amp; Wireless
---

### Post by revenge2 on 2008-07-11
hey guys, how do i install apache using the terminal?
-thanks.

---

### Post by tamoneya on 2008-07-11
I installed a LAMP server using this guide: [http://ubuntuguide.org/wiki/Ubuntu:Hardy#Install_a_LAMP_server_on_a_Desktop](http://ubuntuguide.org/wiki/Ubuntu:Hardy#Install_a_LAMP_server_on_a_Desktop)

This will install apache, mysql and PHP.

---

### Post by rogier.de.groot on 2008-07-11
"sudo apt-get install apache2" should do the trick...

---

### Post by revenge2 on 2008-07-11
hello, i just installed but i cant seem to find where it is.

---

### Post by tamoneya on 2008-07-11
there isnt a menu item for apache.  To test it go into firefox and go to [http://localhost/](http://localhost/).  You should say something along the line of "It works".  If you got that then you can just place your website or whatever you want online in /var/www/

---

### Post by rogier.de.groot on 2008-07-11
What do you mean by "where it is" ? The config files are in /etc/apache2 and the default website files in /var/www

---

### Post by revenge2 on 2008-07-12
Hey guys are there any such tutorials/guides like this for linux. [http://lifehacker.com/software/feature/how-to-set-up-a-personal-home-web-server-124212.php]("http://lifehacker.com/software/feature/how-to-set-up-a-personal-home-web-server-124212.php") (this guide on lifehacker)

-thanks

---

### Post by NikoC on 2008-07-12
[http://www.ubuntugeek.com/ubuntu-804-hardy-heron-lamp-server-setup.html]("http://www.ubuntugeek.com/ubuntu-804-hardy-heron-lamp-server-setup.html")
[http://www.howtoforge.com/perfect-server-ubuntu8.04-lts]("http://www.howtoforge.com/perfect-server-ubuntu8.04-lts")
[http://www.corey-m.com/blog/?p=291]("http://www.corey-m.com/blog/?p=291")

Cheers.

---

### Post by pjcvdpol on 2008-07-12
the configuration of apache is done with the files/scripts in /etc/apache2/  most scripts are pretty well documented, so go ahead and experiment! Do make sure you backup before making any changes and remember to do /etc/init.d/apache2 reload to activate your changes. 

(obviously /etc/init.d/apache2 stop  followed by /etc/init.d/apache2 start also does the trick :-) )

Also: make sure you read/learn about (web)server security before going live on the internet....

---

