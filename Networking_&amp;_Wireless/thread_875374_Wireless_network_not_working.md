---
title: "Wireless network not working"
date: 2008-07-30
forum: Networking &amp; Wireless
---

### Post by cluu908 on 2008-07-30
Hello everyone. First off, I just want to warn you that I'm completely new to Linux/Ubuntu so I'm pretty much clueless regarding how this OS works. Anyway, it seems that my computer isn't receiving any signal from my router, but it worked fine when it used XP before. I was following [this guide]("http://ubuntuforums.org/showthread.php?t=571188"), and it seems that I don't have the driver installed or something. The lshw command returns:

  *-network:1 UNCLAIMED               
       description: Network controller
       product: PRO/Wireless 2915ABG Network Connection
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@000:02:03.0
       version: 05
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=32 maxlatency=24 mingnt=3

So after this, I'm pretty much stuck, since I'm not sure how to install the driver on a linux system. Please help?

---

### Post by sandeepy on 2008-07-30
use kevdog's guide to install ndiswrapper

[http://ubuntuforums.org/showthread.php?t=574501&highlight=Kevdog](http://ubuntuforums.org/showthread.php?t=574501&highlight=Kevdog)

btw ... wht's ur chipset ? i guess bcm43xx ?

---

### Post by thomas576 on 2008-07-30
do a search for 43 legacy drivers, the howto solved my problems i didn't even have to think

---

