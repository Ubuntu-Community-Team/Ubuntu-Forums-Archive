---
title: "(Solved) Help with offline b43 install"
date: 2016-11-07
forum: Networking &amp; Wireless
---

### Post by kazakore on 2016-11-07
I have read the guide above but I have no ethernet connection so I tried downloading b43-fwcutter and firmware-43-installer from the repos to my phone, transferring to laptop and manually installing. Unfortunately, add I expected, the driver files are downloaded by the installer program and obviously I have no net connection so it failed. Can somebody help me getting this installed without a net connection? 

According to lspci my card is the bcm4311 rev1. Anything else you need to know? 

Also from what I read elsewhere you can usually just run Install Additional Diver from the Settings menu if you have an ethernet connection and it will do it all for you. Not worth mentioning this in the guide??

---

### Post by wildmanne39 on 2016-11-08
Follow the directions in the link below for installing the driver without an internet connection.
[https://askubuntu.com/questions/470153/no-wireless-when-install-14-04-on-macbook-pro/470347#470347](https://askubuntu.com/questions/470153/no-wireless-when-install-14-04-on-macbook-pro/470347#470347)

---

### Post by kazakore on 2016-11-15
Sorry only just had a chance to try bit that worked so many thanks &#9786;

---

### Post by wildmanne39 on 2016-11-15
Glad it worked!
Enjoy!

---

### Post by kazakore on 2016-11-15
Well it worked until I tried to upgrade the system, including selecting the driver in the Additional Drivers bit in settings to make sure it would get updated which I suspect is what did the damage, and now it doesn't work again. If I try and run through the offline steps again I get no output when I run "sudo modprobe -rv b43" and it freezes on the first line when running "sudo modprobe -v b43" which says "insmod /lib/modules/4.4.0-47-lowlatency/kernel/drivers/ssb/ssb.ko" If I leave it a few minutes I then can even cancel the command with ctrl+c and the driver has disappeared from the Additional Drivers page when I could always see it before but not install without a net connection. 

Any idea how to fix what I have now broken?

---

### Post by kazakore on 2016-11-15
Nevermind this worked


[http://askubuntu.com/questions/340265/sudo-modprobe-b43-not-working-in-ubuntu-13-04](http://askubuntu.com/questions/340265/sudo-modprobe-b43-not-working-in-ubuntu-13-04)

---

### Post by wildmanne39 on 2016-11-15
I knew what happened when you said you tried the additional driver.
Glad it is working again.

---

