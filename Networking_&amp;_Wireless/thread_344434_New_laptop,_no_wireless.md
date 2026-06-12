---
title: "New laptop, no wireless"
date: 2007-01-22
forum: Networking &amp; Wireless
---

### Post by jgb2185 on 2007-01-22
I have just purchased a Lenovo 3000 C200 laptop and am trying to verify its usability with Ubuntu. It will boot from the Edgy Live CD, but I am unable to get the wifi connection working. According to lspci, the card is a 'Broadcomm Corporation Unknown device 4311'. lshw shows 'network DISABLED', and the driver is bcm43xx. 

I suspect that the interface is disabled to save power. Is it possible to activate it under the live CD, or do I need to do an install first?

I'm not a Linux newbie, but I am where laptops and wireless are concerned. Any help gratefully accepted.

JGB

---

### Post by scrooge_74 on 2007-01-23
Check this thread in may give you some light into the problem

[http://www.ubuntuforums.org/showthread.php?t=185174](http://www.ubuntuforums.org/showthread.php?t=185174)

---

### Post by discord on 2007-01-25
look here got it working and with network manager!

[https://launchpad.net/ubuntu/+source/ndiswrapper/+bug/59983](https://launchpad.net/ubuntu/+source/ndiswrapper/+bug/59983)

---

### Post by jgb2185 on 2007-01-27
Thanks, scrooge & discord. After more research, it seems that I won't be able to get this card working under the live CD. I'm preparing to install Edgy and see if I can get the card working afterward.

---

### Post by scrooge_74 on 2007-01-27
Let us know how you  fare with it

---

