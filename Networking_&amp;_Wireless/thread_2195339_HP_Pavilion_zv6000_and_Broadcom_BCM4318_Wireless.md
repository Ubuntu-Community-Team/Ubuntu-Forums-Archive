---
title: "HP Pavilion zv6000 and Broadcom BCM4318 Wireless"
date: 2013-12-23
forum: Networking &amp; Wireless
---

### Post by wewantutopia on 2013-12-23
Hello, searching the web for this problem show that this horse has been beaten long dead.  However, I can't find the solution to the issue I'm having now.

I just installed 12.04 on this old laptop (was previously a dual boot 9.10 and Windows XP and worked fine after previous tinkering) and of course the wireless card wasn't working.

lspci -vnn -d 144: shows  
```
BCM4318 [AirForce One 54g] [14e4:4318] (rev 2)

```

I ran:  sudo apt-get remove --purge bcmwl-kernel-source
then: sudo apt-get install linux-firmware-nonfree

rebooted

then: sudo modprobe -r b43
then: sudo modprobe b43

Now the wireless card is recognized.  Network manager now shows a check next to enable wireless.  

But,

Wireless Network is greyed out and underneath shows a greyed out disconnected.

The are tons of wifi networks that should be visible to this laptop.

Any ideas whats going on now?

---

### Post by wewantutopia on 2013-12-23
Ok, weird.  

Just for the heck of it I tried connect to hidden network, entered name and password.  Then it connected to my network and displayed the names of the other networks in the area.

Any ideas what that was all about?

I wonder if I leave my house if it will be able to see networks elsewhere without manually entering the credentials...

---

### Post by wewantutopia on 2013-12-23
Ha sorry, one more thing..

I just restarted and it was again displaying no networks.  I reconnected to the now saved hidden network and they are all now displayed.

How can I make it search for networks on it's own??  Never seen this with any of our other laptops.  I guess it's an odd Broadcom thing...

---

