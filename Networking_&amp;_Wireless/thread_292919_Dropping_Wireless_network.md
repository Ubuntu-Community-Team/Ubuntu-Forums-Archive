---
title: "Dropping Wireless network"
date: 2006-11-04
forum: Networking &amp; Wireless
---

### Post by ribena on 2006-11-04
Hello all,

I'm running Xubuntu edgy eft and have a rt2500 wireless card - connects fine when I boot into my PC. However occasionally the connection drops (cheapo router and card). In windows it repairs itself automagically. In xubuntu I have to open the network gui and then disable and re-enable the interface. Any ideas how can I get it to do this automatically?

Cheers

Rob

---

### Post by Propwash on 2006-11-04
Hi Rob;
I have the same thing happening to me.  I use a 3Com card 3CRWE52092B and a DLINK DI 714P+ router.  5.10 worked great, 6.06 had intermittent dropouts and 6.10 seems to act the same way.  To fix it I reset the wireless card by pushing in the antenna thereby dropping the connection and then extending it again.  I have not found any software fix yet.
Jim

---

### Post by gtrtoolman on 2006-11-12
I had the same issue with a WUSB54GV4 adapter in Dapper and Edgy until I went into /etc/network and remarked # iface eth0 in the interfaces file so it would not look for it. Has not dropped out since. Hope this helps.

gtrtoolman

---

### Post by ribena on 2006-11-14
Unfortunately that isn't as I don't have eth0 specified. I guess I'll have to look into how wireless tools work. Isn't there a newer package that does WPA to?

Cheers

Rob

---

