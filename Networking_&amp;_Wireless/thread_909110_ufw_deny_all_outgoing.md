---
title: "ufw deny all outgoing"
date: 2008-09-03
forum: Networking &amp; Wireless
---

### Post by lilpaul on 2008-09-03
Im pretty new to linux and ubuntu and so far im lovin it.  

Im just in the process of securing my installation with ufw

I have so far issued the following commands:-

sudo ufw enable
sudo ufw default deny
sudo ufw logging on


I believe the default deny blocks all incoming connections only, is it possiable to block all outgoing connections with one command, be it a ufw command or a iptables command (I have not used iptables before)

I will then add rules for the ports i want to open on a needs basis.

Bit overkill but im a paranoid android!!

---

### Post by lilpaul on 2008-09-06
Can anyone help me with this query?

---

### Post by g0nzal01 on 2008-12-04
try looking through the man page 
man ufw
Remember that outgoing ports are always going to open when you surf the web. you can restrict where you can go but that may be a little overkill.

---

### Post by Iowan on 2008-12-05
The Beginning Ubuntu Administration book I've been reading *suggests* **iptables** can be set up that way.  It suggested **ufw** is good for simple applications, but complex rules need **iptables**.  I'll check when I get home (if my internet starts working...).

---

### Post by MarblePanther on 2008-12-05
A good gui for ufw is  gufw

It's in the repos

[http://gufw.tuxfamily.org/index.html](http://gufw.tuxfamily.org/index.html)

---

