---
title: "patch for bcm43xx driver for 4311 support"
date: 2006-11-08
forum: Networking &amp; Wireless
---

### Post by ninaprem on 2006-11-08
I am a newbie. Installed kernel 2.6.17.10-generic on my laptop hp compaq nx 7400. The problem is the wireless network is not working. I have tried different methods found on this forum but without success.:( 
Tried the ndiswrapper method and bcm43xx method. In both cases modules get loaded. 
But iwconfig gives 

lo        no wireless extensions.

sit0      no wireless extensions.

eth0      no wireless extensions.
 
The chip is bcm4311. lspci gives
10:00.0 Network controller: Broadcom Corporation Unknown device 4311 (rev 01)

which is not currently supported by the bcm43xx driver.
during the search I came accross a patch which gives the bcm43xx driver the 4311 support.
([http://www.mail-archive.com/bcm43xx-dev@lists.berlios.de/msg01814.html](http://www.mail-archive.com/bcm43xx-dev@lists.berlios.de/msg01814.html))
can someone guide assist me how to apply this patch which I feel might work. thanks in advance.

---

### Post by ninaprem on 2006-11-10
> **ninaprem said:**
> I***_[I][B]***_[/I][/B] am a newbie. Installed kernel 2.6.17.10-generic on my laptop hp compaq nx 7400. The problem is the wireless network is not working. I have tried different methods found on this forum but without success.:( 
Tried the ndiswrapper method and bcm43xx method. In both cases modules get loaded. 
But iwconfig gives 

lo        no wireless extensions.

sit0      no wireless extensions.

eth0      no wireless extensions.
 
The chip is bcm4311. lspci gives
10:00.0 Network controller: Broadcom Corporation Unknown device 4311 (rev 01)

which is not currently supported by the bcm43xx driver.
during the search I came accross a patch which gives the bcm43xx driver the 4311 support.
([http://www.mail-archive.com/bcm43xx-dev@lists.berlios.de/msg01814.html](http://www.mail-archive.com/bcm43xx-dev@lists.berlios.de/msg01814.html))
can someone guide assist me how to apply this patch which I feel might work. thanks in advance.

Installed kernel 2.6.18.2 but networking still not working.

**[B][B][B]**[/B][/B][/B]

---

### Post by snpz on 2006-11-15
AFAIK this is not tested yet, so not implemented in kernel. I tryed kernel wireless-dev tree. Compiled it and tryed to run. Card becomes active, but i could not connect to any of AP. Right now some new instructions, how to test all this better.
If u have interest in testing - PM. 

> **ninaprem said:**
> Installed kernel 2.6.18.2 but networking still not working.


---

