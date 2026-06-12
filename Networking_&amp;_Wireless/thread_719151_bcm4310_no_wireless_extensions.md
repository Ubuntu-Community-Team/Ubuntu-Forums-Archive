---
title: "bcm4310 no wireless extensions"
date: 2008-03-08
forum: Networking &amp; Wireless
---

### Post by Papa-san on 2008-03-08
Been through just about every how to on the internet for this thing...
tried this one:
[http://linux.dell.com/wiki/index.php/Tech/Wireless/Truemobile_ndiswrapper](http://linux.dell.com/wiki/index.php/Tech/Wireless/Truemobile_ndiswrapper)

Supposedly it works, but in actuality, it doesn't...


Evidently, bcmwl5.inf isn't the one I need. bcmwl6.inf gives me the screenshot below:
look where it says the driver is not at...

I guess one of the problems I run into frequently is not knowing which one of '/tmp' I am supposed to use nor do I know how to navigate to it properly...

EDIT:
Called Dell. Learned that my wireless card is a '1395 wlan mini 80211gi'
The driver is supposed to be: Dell_multi-device_A17_R174292.exe
This is the one I used that got me the bcmwl6 driver.

I have that .exe on my desktop and have run all the commands I can find anywhere to remove any traces of ndiswrapper from the system.

Now, I need to know what to do from here... I have three identical laptops to do this to, so good advice will be used a lot! I'll even make sure that my wife and kids all thank you! lol

RE-EDIT: I have re-installed Ubuntu 7.10 because I kept trying to work on it... Wasn't sure I'd ever clean it up, so I just re-installed it... Waiting for replies...

---

### Post by Papa-san on 2008-03-13
Bump

---

### Post by Astura on 2008-03-18
I also  have the bcm4310 (in an hp) and have tried many ndiswrapper/non-ndiswrapper guides to get the driver, and I too have no wireless extensions

> 
astral@velio:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.



Wish I had something useful to add

---

### Post by lsutiger on 2008-03-19
[Try this]("http://www.ubuntu1501.com/2007/10/wireless-in-ubuntu-710-gutsy-gibbon.html")

Worked for me!

---

