---
title: "Making ubunutu desktop as server"
date: 2014-10-13
forum: Networking &amp; Wireless
---

### Post by Emamul_Andalib_Ayo on 2014-10-13
I want to make my ubuntu desktop as web server. I have some websites. I don't want to use another hosting or VPS. I want to make my own pc for web hosting or server. Please help me to make this happen. Thank you.

---

### Post by TheFu on 2014-10-13
[http://blog.jdpfu.com/2009/08/18/internet-hosting-setup](http://blog.jdpfu.com/2009/08/18/internet-hosting-setup)

Desktop tools/programs (even the base GUI) adds bloat to a system and increases the attack vector for attackers, not recommended.

However .... there are lots of how-to guides out "there" - google "ubuntu perfect server" to see how many other people setup a box. Depending on your skill level, this will be fairly easy or very hard. Regardless, you'll learn a bunch.

Pick a webserver. A smaller, easier to use webserver might be a better choice over the i-can-do-anything apache. Apache has a huge surface for attacks. It is also fairly secure, when configured properly.  Where I work, we stopped using apache around 2007, but it just depends on your needs from a web/app server. There are many choices. Do a little research.

Oh ... and be prepared for the machine to be attacked. That is just the way of the world these days. This can risk your internal network too. Have fun.

---

### Post by davit2 on 2014-10-13
1. you should install apache web server. 

$ sudo apt-get install apache2

2.After installation web server will be ready for use. Open browser, write "localhost" in link bar, and default web page will be opened.

3.Your web page files are in /var/www/  folder, (default page fail is index.html).

4.Your server(apache) configuration files are in /etc/apache2/ folder.

---

