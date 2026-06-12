---
title: "Ubuntu Linux 7.04 (`Feisty Fawn Herd`) vs. bcm43xx"
date: 2007-03-21
forum: Networking &amp; Wireless
---

### Post by bepe79 on 2007-03-21
Hi `ya! I have a very important question. Does the new Feisty Fawn Herd Beta 5 support the bcm43xx chipset without any config and when will it just work? I have heard about the new Ubuntu 7.04 `s zer0conf feature and I `m just wonderin` how does it work with my bcm4318 wifi / wlan card. Thank You for Your help!

Bepe

---

### Post by Belyel on 2007-03-21
Two things: Feisty is actually still alpha software.  It can and will break.  If you are planning to run this on your daily use machine, ie something that has important data or programs or information on it, just don't do it.  Trust me.  
Second thing: I don't know if the bcm43xx chipset "just works" in feisty, but in feisty there are many more chipsets supported.  The version of ndiswrapper in feisty is also newer, so it supports more chipsets if yours isn't natively supported.  My suggestion would be to download the herd5 live CD and give it a shot.  Then you'll be helping the devel team with testing the liveCD and you'll be testing your system.

---

### Post by spd106 on 2007-03-21
At the moment it doesn't work out of the box, as you still need to download (or extract) the firmware. This cannot be distributed without Broadcom's approval due to copyright restrictions. Having said that as long as you already have a net connection the bcm43xx-fwcutter will fetch the firmware for you, (as it does with Edgy, iirc).

This situation is unlikely to change in the near future. If you want to know more have a look at the linuxwireless site [http://linuxwireless.org/en/users/Drivers/bcm43xx](http://linuxwireless.org/en/users/Drivers/bcm43xx)

I haven't done extensive testing, but in my opinion the bcm43xx driver is much improved over Edgy's version. It's far more stable, though it is still slower than ndiswrapper.

---

