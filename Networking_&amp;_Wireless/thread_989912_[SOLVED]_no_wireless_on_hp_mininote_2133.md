---
title: "[SOLVED] no wireless on hp mininote 2133"
date: 2008-11-22
forum: Networking &amp; Wireless
---

### Post by elliah on 2008-11-22
I have tried every wiki solution and forum tip I found relevant to my problem but still no wireless. My hp mininote is the one with the 4gb ssd and I followed the instructions on this wiki [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)
I used step 1, 2e and 3. But it didnt work. So I applied the Hardy fix, which also didnt work.
lspci -nn showed 
 Network controller [0280]: Broadcom Corporation BCM4310 USB Controller [14e4:4315] (rev 01)

the network manager doesn't pick up any wireless signals at all. Anyone with a similar problem managed to get this fixed?

---

### Post by Ayuthia on 2008-11-22
> **elliah said:**
> I have tried every wiki solution and forum tip I found relevant to my problem but still no wireless. My hp mininote is the one with the 4gb ssd and I followed the instructions on this wiki [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)
I used step 1, 2e and 3. But it didnt work. So I applied the Hardy fix, which also didnt work.
lspci -nn showed 
 Network controller [0280]: Broadcom Corporation BCM4310 USB Controller [14e4:4315] (rev 01)

the network manager doesn't pick up any wireless signals at all. Anyone with a similar problem managed to get this fixed?

You might try installing Intrepid where it should work after you activate the driver in System->Administration->Hardware Drivers.

However, if you have a wired connection, you can get your system updated to the most recent updates and then you could activate the driver by going to System->Administration->Hardware Drivers.

The other option is to install it yourself if you don't have a working connection in Ubuntu:
[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

---

### Post by Olivier2371 on 2008-11-22
I there,

When you say that your wireless adapter doesn't work, do you base it on whether the led on your laptop is lit or not, or the fact that you do not have a connection at all.

---

### Post by elliah on 2008-11-30
after more googling and forum trolling...i kind of managed to get it to work with the wireless at my place...but i have yet to try it out elsewhere...
the problem turned out to be that ndiswrapper wasn't being loaded and the wl drivers were still being used everytime i rebooted...so i disabled the wl driver...and now it works...so far...	:-D

---

