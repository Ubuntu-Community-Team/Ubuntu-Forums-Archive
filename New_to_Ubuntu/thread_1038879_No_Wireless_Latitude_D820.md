---
title: "No Wireless Latitude D820"
date: 2009-01-14
forum: New to Ubuntu
---

### Post by Jion_Wansu on 2009-01-14
I cannot get any wireless connections to work on my Latitude laptop. Ubuntu 8.10 does not recognize my wireless card on my laptop for some reason. I tried all the suggestions and walk-thoughs but without success. I spent about 10 hours total on this thing trying to figure it out. Am I just out of luck?

[img]http://img238.imageshack.us/img238/8219/cantconnect1sc5.png[/img]


[img]http://img48.imageshack.us/img48/7044/cantconnect2xg1.png[/img]


home@Home:~$ sudo ndiswrapper -l
sudo: unable to resolve host Home
[sudo] password for Home: 
bcmwl5 : driver installed
home@Home:~$

home@Home:~$ sudo iwlist scan
sudo: unable to resolve host Home
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

pan0      Interface doesn't support scanning.

home@Home:~$

---

