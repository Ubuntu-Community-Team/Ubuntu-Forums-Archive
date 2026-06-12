---
title: "setting up apache2 server on ubuntu 606 to execute python sripts"
date: 2008-04-18
forum: Networking &amp; Wireless
---

### Post by syed mehdi on 2008-04-18
Hi Guys,
I am using ubuntu 606, i want to do some server side scripting in python for one of my applications. So after installing apache2, python lib for apache2 (libapache2....) on my machine, and doing some changes in default file in /etc/apache2/sites-available i was able to execute python scripts in /var/www/ directory from client side.
but i want to place all of my python scripts in some other directory like /home/username/myserver, so what changes i have to make in configuration files at /etc/apache2/apache2.conf or some other place (like /etc/apache2/sites-available/default), so that my server side scripts placed in this folder (/home/username/myserver) gets executed from client side using some url like [http://machine-ip/home/username/myserver/abc.py](http://machine-ip/home/username/myserver/abc.py).

Thanks & Regards
Syed

---

