---
title: "Help With Broadcom Device/Drivers please?"
date: 2007-04-14
forum: Networking &amp; Wireless
---

### Post by shalashazka on 2007-04-14
I'm on an HP Pavilion dv6000z (laptop). I went and formatted my Windows XP Media Center Edition 2006 because it was giving me performance issues.
Now I can't get the Broadcom device to work. Usually I can /only/ connect to wireless, but I went to my friend's to use his wired stuff.

Can someone please supply me with the correct with the correct drivers for 64-bit ndiswrapper? 

Also, might it be that my device could be compatible with only 32-bit systems? I really don't know what the problem is, or what drivers I need for that matter...I have to wait until my friend finishes screwing around with my partitions and booting Feisty to check my device's name and this, so I'll post that when I get it.

---

### Post by Wofl on 2007-04-14
just type lspci into the terminal

it usually shows that way...

then check the listin gon ndiswrappers site to see what file to get and from where

---

### Post by shalashazka on 2007-04-15
Bump...

---

### Post by Floppyjoe on 2007-04-15
You need to specify what type of Broadcom card you are using otherwise people will not be able to help you.
enter:
```
lspci
``` 
into the terminal to find out your chipset under network controller.


You can open a terminal by clicking on Applications/Accessories/Terminal.

---

### Post by shalashazka on 2007-04-15
Heheheh, thanks, you guys are really on the ball when helping people ^_~

03:00.0 Network controller: Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card (rev 01)

---

### Post by dbott67 on 2007-04-15
Using that output, check this list:

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#B](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#B)

I searched for '1390' and found this:

> 40.  Card:Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card rev 01 [LIST]
[*]PCIID: 03:00.0 0280 14e:4311 rev 01
[*]PC: HP pavilion dv6000 series 'DV6105US'
[*]OS: Slackware 11.0
[*]Driver Used:  Win32 Driver from HP
[*][HP Driver]("http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?softwareitem=ob-45290-1&lc=en&cc=sg&dlc=en&product=3245619&os=228&lang=en")
[*]Other: Kernel version 2.6.19 Slackware 11.0 Ndis 1.33 newest windows driver, absolutely no issues![/LIST]and then follow these instructions:

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation)

---

