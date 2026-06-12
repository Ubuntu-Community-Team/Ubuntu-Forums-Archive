---
title: "wierd internet setup"
date: 2007-08-03
forum: Networking &amp; Wireless
---

### Post by theplasticpoet on 2007-08-03
hi, i'm running ubuntu 7.04 on my desktop pc at home. i've got one other desktop in my parent's room and a laptop in my sister's room. all three PCs use the same internet connection, which is configured as follows:


|===========================| >>USB>>Ubuntu PC>>LAN>>Parent's PC
|US Robotics 9112 ADSL modem |
|===========================|>>LAN>>laptop

now i've got a bit of a strange problem here.
i run counterstrike via cedega, and i can join games but can't host them. this is annoying. what does happen is that the half life dedicated server applet gives me a local loopback address (127.0.0.1) both on LAN and Internet. I'm not sure whether this is a wine problem or something wrong with my ifconfig/masquerade.

another problem is one that has to do with port forwarding. i live in the middle east, and my ISP likes to babysit my internet connection. websites like flickr, last.fm etc. are blocked. as a workaround, i forward port 1080 on my PC to a friend's computer running ubuntu in ireland. this is the command i use:

ssh -D 1080 -l pirzada isythica.net

then i set my browser's proxy to localhost:1080 and browse through the other computer's internet connection. how do i use this for other programs and services, like apache2 or wget etc.?

---

