---
title: "webmin https wrong ip"
date: 2008-07-08
forum: Networking &amp; Wireless
---

### Post by mitjab on 2008-07-08
When i am connecting to [http://82.149.25.222:10000](http://82.149.25.222:10000) i get

Error - Bad Request

This web server is running in SSL mode. Try the URL 
[https://192.168.123.171:10000/](https://192.168.123.171:10000/) instead.


how to make that adress will be [https://82.149.25.222:10000](https://82.149.25.222:10000) and not local IP

regards

---

### Post by yamato08 on 2008-07-08
Try [https://82.149.25.222:10000/](https://82.149.25.222:10000/)
It works perfectly fine, I just saw your login screen. You have to add exception for certificate in firefox though.

---

### Post by mitjab on 2008-07-08
yes i know that works.

But i want to make that it will write correct ip adress.

I want this message to display

Error - Bad Request

This web server is running in SSL mode. Try the URL
[https://82.149.25.222:10000/](https://82.149.25.222:10000/) instead.

hope understand me

---

### Post by superprash2003 on 2008-07-08
that error normally comes only when you try to connect via LAN.. it wouldnt come when connecting from the internet

---

### Post by samuel.stringham on 2011-04-04
Late reply is better than nothing.

Try adding:

musthost=[URL="https://82.149.25.222:10000/"]82.149.25.222
[/URL]
Into the miniserv.conf .  Webmin just guesses at your hostname/IP via get_socket_name(), that musthost config option allows you to specify.

---

