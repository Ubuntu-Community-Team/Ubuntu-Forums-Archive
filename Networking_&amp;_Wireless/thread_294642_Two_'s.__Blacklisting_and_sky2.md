---
title: "Two ?'s.  Blacklisting and sky2"
date: 2006-11-06
forum: Networking &amp; Wireless
---

### Post by digger4ubuntu on 2006-11-06
I have installed Ubuntu 6.06 Server on a Dual Xeon box.  The box has a Marvell Yukon II chipset.  I am running 2.6.15-27-server and by default it used sky2 for this chipset.

Whenever I pass a lot of traffic (100-200Mb/s) the interfaces lock up and I have to rmmod/modprobe to start them back up.  I have found (Google) that several other people have experienced the same issue with the sky2 module in several different kernel versions from 2.6.14 - 2.6.18.  Supposedly I have read that these issues are fixed on some the bleeding edge kernels late in the 2.6.18 and early 2.6.19 releases.  Being that this is a production server I can not put bleeding edge in place.

My two questions are:

I am trying the sk98lin driver from Marvell.  Anyone had any luck with this being stable under such a load?

How can I blacklist the sky2 module?  I have tried adding it to /etc/modprobe.d/blacklist as well as creating /etc/modprobe.d/blacklist-sky2 both of which contain the line "blacklist sky2" but the module keeps loading at boot.  For now I have moved _sky2.ko to _sky2.ko.bak under /lib/modules/2.6.15-27-server/kernel/drivers/net but this is very crude and I would like to find a solution that will work even after upgrades.

---

### Post by digger4ubuntu on 2006-11-07
*bump*

FWIW - approaching 12 hours uptime on the sk98lin driver where I could barely get 3-4 hours on the sky2 driver.

---

