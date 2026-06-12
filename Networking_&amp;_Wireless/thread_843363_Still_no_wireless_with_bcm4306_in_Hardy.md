---
title: "Still no wireless with bcm4306 in Hardy"
date: 2008-06-28
forum: Networking &amp; Wireless
---

### Post by captgadget on 2008-06-28
I have removed fwcutter, installed ndiswrapper and wicd and still can not connect to the wireless bcm4306. Nothing finds the ip address. When I run iwconfig wlan0 it comes back with no essid.

If one didn't love playing with Linux this is exactly why people choose Mac or Windoze!!

---

### Post by ScaredNoob on 2008-06-28
I have similar issues with bcm4306 in Hardy.  I went with the restricted driver manager, (ie fwcutter) and now my wireless connection is only 1 mb/s.  In everything up till Hardy, I got 11 mb/s (b).  However, 1 mb/s is usable, and I do have wireless internet.  If you want to go this route, reinstall Hardy and go to system > administration > hardware drivers and check to enable its usage, including the box to extract and fetch firmware when the time comes.  At least you will have wifi.

---

### Post by daemonfly on 2008-06-30
I have the BCM4306 in my Dell. I installed bc-fwcutter, then put "b43" into /etc/modules. This worked a LOT better than the bcm43xx module thats usually suggested.

I use Xubuntu, and still have a few issues with NetworkManager (known to have problems with many Broadcom cards). Once I get home from work, I'm going to replace NetworkManager with Wicd [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/) as it's mentioned to work a lot better with BCM stuff.

The driver worked fine, NetworkManager just could never consistantly remember what wireless network I was running on.

---

### Post by untermensch on 2008-06-30
Either go back to fwcutter ( I never had a problem with slow internet with it) or do what daemonfly. that seems like a pretty good idea.

---

