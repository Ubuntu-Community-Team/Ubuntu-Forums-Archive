---
title: "Need help on strange incomming connections!"
date: 2008-11-30
forum: Networking &amp; Wireless
---

### Post by jvasque7 on 2008-11-30
Hello to all.

I recently installed Ubuntu 8.10, and I was told to add firestarter. It has all worked correctly but in the past few days I have seen that this firewall has blocked incomming connections (marked as serious) from an address 192.168.2.3, using as service Microsoft DS (port 445) and Samba (port 139).

On top of that, my Ip adress, which is supposed to be dynamic, hasn't changed for the last 11 days. A friend of mine has recently told me that a hacker locked her address so it wouldn't change, with the supposed objective of cloning it, is this really possible?

Can this mean that I am under some sort of threat or attack attemp? 

I use a router and there are two other computer connected using Windows XP.    

It someone can help i'd really appreciate it!

---

### Post by philetus on 2008-11-30
192.168.1.2  is part of the private block you have for your networking.
[http://www.comptechdoc.org/os/linux/usersguide/linux_ugrouting.html](http://www.comptechdoc.org/os/linux/usersguide/linux_ugrouting.html)

what kind of router do you have?
Is it password protected?

You can access your router by typiing 192.168.1.1 into a browser  address window.

---

### Post by philetus on 2008-11-30
or possibly 192.168.1.2

---

### Post by gpsmikey on 2008-11-30
Actually, if you are seeing stuff from 192.168.2.3, then your router should be at 192.168.2.1 (I think SMC uses .2.x for their routers - I have my Linksys there, but I have moved stuff around so I don't remember for sure on that).  You should also have changed the password on your router from the default (especially if there is wireless involved).

mikey

---

