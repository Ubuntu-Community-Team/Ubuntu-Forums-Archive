---
title: "Switching between eth1 and eth2"
date: 2006-07-21
forum: Networking &amp; Wireless
---

### Post by Minilek on 2006-07-21
I set up my wireless card (a broadcom 4306) in dapper by using the guide found at [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper#head-d0946e95811e2999580f6073e165fa66c3709f01](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper#head-d0946e95811e2999580f6073e165fa66c3709f01) (I used bcm43xx-fwcutter).  Now when I start my machine, half the time the wireless card is seen as eth1 and half the time it's eth2.  It's not too big of an issue because I just put both eth1 and eth2 in my /etc/network/interfaces, though it is kind of annoying since it affects the gnome icon in the upper right corner of the screen that shows connectivity.  Does anyone know how to get the device to consistently show up under one name?

EDIT: All solved.  Modifying /etc/iftab worked.

---

