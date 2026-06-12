---
title: "strange network problem"
date: 2008-03-24
forum: Networking &amp; Wireless
---

### Post by sasgross on 2008-03-24
I installed ubuntu 7.10 on my laptop (Acer Apire 1600) and I'm having this strange network problem. I call it strange, because it only occurs if I start ubuntu from the hard disk. If I start ubuntu from the live CD the problem does not occur. The problem simply is: I have [COLOR="Red"]no wired internet connection[/COLOR].

In the live CD mode i checked the network settings, and applied them to the installed version. I checked the network tools, everything looks fine, but pinging my DSL modem does not work (192.168.1.1). :confused:

Can anybody help me with this? Thanks a lot in advance...

Sascha

---

### Post by farahbod on 2008-03-24
let us have the result of these commands:

ifconfig eth0

route

---

### Post by erginemr on 2008-03-24
How are you connected to the Internet? Modem via USB or ethernet?

What is the outcome of the following commands from the terminal?
```
ifconfig
```
```
lshw -C network
```
```
cat /etc/network/interfaces
```

---

### Post by sasgross on 2008-03-30
Hi folks,

sorry for the inconvenience and taking your time. I solved the problem by installing ubuntu 8.04.

Thanks anyway

---

### Post by erginemr on 2008-03-30
Okey dokey...

Take good care! :D

---

### Post by Chappy7777 on 2008-03-30
> **sasgross said:**
> Hi folks,

sorry for the inconvenience and taking your time. I solved the problem by installing ubuntu 8.04.

Thanks anyway

Sorry, do you mean 7.04? I see no mention of 8.10 or any other version of Ubuntu 8. If you do mean 8.04, what is the URL? I went to "Get Ubuntu" and all the are giving out is 7.10, which they say there, is the latest.

---

### Post by erginemr on 2008-03-31
> **Chappy7777 said:**
> Sorry, do you mean 7.04? I see no mention of 8.10 or any other version of Ubuntu 8. If you do mean 8.04, what is the URL? I went to "Get Ubuntu" and all the are giving out is 7.10, which they say there, is the latest.

Version 8.04 is code named Hardy Heron and is at Beta stage. You can download and try it from Live CD by visiting:
[http://www.ubuntu.com/](http://www.ubuntu.com/)

but I'd suggest you to wait till late April and upgrade your system then, when Hardy will be released officially.

---

