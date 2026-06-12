---
title: "VIA Rhine II Chipset (VT1602) In 8.04 no connectivity"
date: 2008-05-15
forum: Networking &amp; Wireless
---

### Post by k5dreadlord on 2008-05-15
Hi all, I've been surfing the internet (using google) for the past 7 hours or so (It's 4 am here) and cannot find a single working solution to the lack of internets on my computer.

Quick facts: 
-It worked on 7.10
-A lot of people seem to get this problem
-I started this thread so we can gather as much info as possible in One thread instead of 2423531 billion threads.

Things I've noticed:
-I have an Eth0 ethernet connection that doesn't even have an IP address and isn't receiving or sending anything. Cannot be configured. (Network Tools)
-I have an eth0:avahi connection that can be pinged, has an IP but cannot be configured because the device doesn't exist. (Network Tools) 
-ethtool DEVNAME shows only "cannot get"s and "no such devices".
-modprobe.conf contains only: alias eth0 via-rhine.
-lspci recognizes my card.
-I tried installing rhinefet.tgz but wherever I download it from there ALWAYS is/are file(s) missing.
-dmesg | grep eth0 tells me eth0 exists, MII PHY has an address but eth0's link is down...
-I am quite mad.

If anyone out there has a suggestion that can solve my problem, it is welcome.

Looking forward to writing 'thx' as a reply to your post,
FX

---

### Post by Draku on 2008-05-15
I think we have the same issue [http://ubuntuforums.org/showthread.php?t=792640](http://ubuntuforums.org/showthread.php?t=792640)
Sadly no solution...

---

### Post by chili555 on 2008-05-15
eth0:avahi assigns a 169.254.x.x placeholder when it cannot obtain a valid IP address from the router/access point/etc. Please let us see:```
lsmod | grep mii
lsmod | grep via
sudo dhclient eth0
```Thanks.

---

