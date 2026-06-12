---
title: "Broadcom 4318 with Ubuntu edgy, again"
date: 2007-03-30
forum: Networking &amp; Wireless
---

### Post by xabierurra on 2007-03-30
I still haven't been able to make my wireless card work after three weeks, its an Asus wl-138g v2 with the famous broadcom 4318 chipset. I got a very slow and transient conexion using bcm43xx-fwcutter but it was useless. I have also tried with ndiswrapper 1.23, and it seems that it is going to work but finally it doesn't. This is the message I get after *dhclient eth1*:

[COLOR="Red"]root@xabierurra-desktop:~# dhclient eth1
There is already a pid file /var/run/dhclient.pid with pid 5938
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:18:f3:e4:51:4a
Sending on   LPF/eth1/00:18:f3:e4:51:4a
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
No DHCPOFFERS received.
No working leases in persistent database - sleeping.[/COLOR]

Any idea of what this means? And any idea of why I don't get my card working?

Thank you

---

### Post by Drate on 2007-03-30
Do this:

[http://www.ubuntuforums.org/showthread.php?p=2378480#post2378480](http://www.ubuntuforums.org/showthread.php?p=2378480#post2378480)

I don't know how adept you are with Linux, so if you need me to I can break down each step into "beginner style" instruction... otherwise, this will work.

BTW:  I don't know what all you've done with your computer thus far, fwcutter, etc, so you may need to undo, uninstall, etc, anything you've added to it thus far, start these steps clean and I'm justabout positve they will work for you.

---

### Post by xabierurra on 2007-03-30
Drate:[http://ubuntuforums.org/images/smilies/icon_smile.gif](http://ubuntuforums.org/images/smilies/icon_smile.gif)

THANK YOU VERY MUCH: you made it work! I'm not sure what the key point is, but it works now and I was already quite skeptic about it...

You should post this somewhere else, because I think there are many people with the same problem. I will definitely do so in spanish and basque language forums. 

Thank you again.

---

### Post by xabierurra on 2007-03-31
Just one point: the driver I finally installed and worked is the bcmwl5a.inf

Xabi

---

### Post by Drate on 2007-03-31
Hmm... well, ndiswrapper website, where they list all the cards that work with it, specified the one without the "a" at the end.... but hey, whatever works.

---

### Post by xabierurra on 2007-03-31
Well, I've done it twice with the bcmwl5a driver, and it worked. When I tried again with the bcmwl5 it didn't.  Don't know why, and don't mind. The only problem is that it is quite tricky to get wireless working on linux, I think this has been the biggest problem I've found in my short experience. Hope it will be easier in the near future...

---

### Post by Drate on 2007-03-31
Understood, I would like to learn how to write a script or program to automate the process, I spose I should learn Python ey?

---

