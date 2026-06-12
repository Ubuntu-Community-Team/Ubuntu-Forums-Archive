---
title: "Ubuntu 8.10 BCM4318 and Aircrack-ng"
date: 2008-10-08
forum: Networking &amp; Wireless
---

### Post by sxfx on 2008-10-08
Hey guys I installed 8.10 today and to my surprise my BCM4318 card started working right out of the box with out using ndiswrapper in that instant I got very excited and went see if I can aircrack-ng to work.

Well that didn't go so well, so I proceeded to check my lshw -C network and I got this.

> 
 *-network:0             
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:06:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb


I right away noticed that its using the ssb module.  

I guess I'm just wondering if its possible to finally use my BCM4318 chipset with aircrak-ng with out a problem?

Any input would be greatly appreciated as Iv always wanted to play around with it.

Thanks.

---

### Post by PinkFloyd102489 on 2008-10-08
Try installing the restricted modules and then doing this.

```

sudo rmmod ssb
sudo rmmod wl
sudo modprobe wl
sudo modprobe ssb

```

---

### Post by snakep on 2008-10-08
That is the same output I get from "lshw -C network".  I am running 8.04, though.  I have trouble removing and reloading ndiswrapper.  Every time I do so the machine locks up.  Any idea what might cause this?

---

### Post by iwallet on 2008-12-01
were you able to get it to work?!?! i got super exited too as soon as i saw that it worked right away!!! :D

---

### Post by Ayuthia on 2008-12-01
Have you tried to see if you can get the b43 driver to work in 8.10?  It looks like some of the 4318 cards are now working with it.

---

