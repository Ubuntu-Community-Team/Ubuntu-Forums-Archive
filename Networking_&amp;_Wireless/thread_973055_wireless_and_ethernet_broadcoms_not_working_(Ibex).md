---
title: "wireless and ethernet broadcoms not working (Ibex)"
date: 2008-11-06
forum: Networking &amp; Wireless
---

### Post by gumbel2gumbel on 2008-11-06
I recently upgraded my laptop with an ibex/hardy dual boot.  My wireless never,ever worked in Hardy despite anything i did with b43fwcutter, ndiswrapper, or anything command line.  my problem is that now my ethernet won't even work, and half the solutions to try and fix my wireless card in ibex require accessing the depositories which is impossible at the moment.

Ibex:  Release day version
Ethernet: BCM4401-B0
Wireless: BCM4318 Rev 02
Router: Netgear Rangemax Wireless

---

### Post by Ayuthia on 2008-11-06
> **gumbel2gumbel said:**
> I recently upgraded my laptop with an ibex/hardy dual boot.  My wireless never,ever worked in Hardy despite anything i did with b43fwcutter, ndiswrapper, or anything command line.  my problem is that now my ethernet won't even work, and half the solutions to try and fix my wireless card in ibex require accessing the depositories which is impossible at the moment.

Ibex:  Release day version
Ethernet: BCM4401-B0
Wireless: BCM4318 Rev 02
Router: Netgear Rangemax Wireless

You might try to get you wired connection up and running by trying the following:
```
sudo modprobe -r b43 b44 ssb ndiswrapper wl
sudo modprobe b44
sudo ifconfig eth0 up
sudo dhclient eth0
ping -c1 www.google.com
```

---

### Post by superprash2003 on 2008-11-06
try this [http://prash-babu.blogspot.com/2008/11/how-to-configure-broadcom-wireless-in.html](http://prash-babu.blogspot.com/2008/11/how-to-configure-broadcom-wireless-in.html)

---

### Post by gumbel2gumbel on 2008-11-06
well, now my wired connection won't work on my hardy partition.  this has been something of a nightmare.  ayuthia, i tried that link, and in the driver manager all it says is "No proprietary drivers are in use on this system" and no option to enable or install any.  the list is blank.

---

