---
title: "Can't Connect To Internet After Installing Firestarter"
date: 2006-12-10
forum: Networking &amp; Wireless
---

### Post by FoodForDog on 2006-12-10
Hi-

I just installed Ubuntu 6.10, had no problems.  I was able to use firefox and gaim.  I then installed firestarter, and I can no longer access the web or aim.

Any suggestions would be greatly appreciated.

Thanks in advance!

edit:  I have tried uninstalling firestarter, and still no success.  Also, perhaps of interest: I am connecting to the Internet through a router.  Thanks again.

---

### Post by goodfella on 2006-12-11
goto a termian and type route and post the information to the forum.

---

### Post by FoodForDog on 2006-12-11
After typing route:


Destination  Gateway       Genmask  Flags   Metric Ref Use Iface

192.168.0.0  *      255.255.255.0   U   0   0   0  eth0
192.168.0.0  *      255.255.255.0   U   0   0   0  eth1
default  192.168.0.1   0.0.0.0   UG     0   0   0  eth1
default  192.168.0.1   0.0.0.0   UG     0   0   0  eth0



Thanks!

---

### Post by gReEnT3a on 2006-12-14
> **FoodForDog said:**
> Hi-

I just installed Ubuntu 6.10, had no problems.  I was able to use firefox and gaim.  I then installed firestarter, and I can no longer access the web or aim.

Any suggestions would be greatly appreciated.

Thanks in advance!

edit:  I have tried uninstalling firestarter, and still no success.  Also, perhaps of interest: I am connecting to the Internet through a router.  Thanks again.

I got a similar problem, but only when I "activate" firestarter...
I think you might have uninstalled firestarter without stopping it, which means the iptable is till running~

Anyway, I am still interested in running Firestarter and would like some help to solve this problem also ](*,)

---

### Post by Ethos on 2006-12-14
Ip tables are always running, Firestarter is merely a way to control them more efficiently...

---

