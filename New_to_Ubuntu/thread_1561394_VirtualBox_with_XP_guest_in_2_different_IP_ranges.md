---
title: "VirtualBox with XP guest in 2 different IP ranges"
date: 2010-08-26
forum: New to Ubuntu
---

### Post by oliver_m on 2010-08-26
Hi,

i am running VirtualBox 3.1.8 on an Ubuntu 10.04 with an XP guest system in VB.
My physical machine runs on IP 192.168.0.4 (assigned by my wirelss router), and on the virtual XP machine i have an application running on 10.0.0.109 (i cant change that).

Now my question is, how do i need to configure the VB network that i can access the virtualbox-app from my physical machine via a webbrowser ?



Thanks in advance
Oliver

---

### Post by Calash on 2010-08-26
Was the 10.0.0.109 assigned by Virtualbox or is that necessary for your webapp to function?

The simplest way would be to change the virtual network adapter on your guest OS to bridged.  This will allow it to get a real IP from your network and allow you direct network access as if it was a real system.

---

### Post by oliver_m on 2010-08-28
Its required by the app, and i ve assigned it as fixed IP.

i solved it by assigning 10.x.x.x ranges to my router (sometimes things are sooo simple :-))

---

