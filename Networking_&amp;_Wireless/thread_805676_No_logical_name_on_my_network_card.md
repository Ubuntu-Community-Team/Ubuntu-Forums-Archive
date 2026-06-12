---
title: "No logical name on my network card"
date: 2008-05-24
forum: Networking &amp; Wireless
---

### Post by dvyjones on 2008-05-24
When I tried to get my network card working a couple of days ago, the network card "lost" it's logical name (wlan0). How do I get a logical name for it again?

The code has been shortened, so only the network card is showing.
```

henrik@henrik-desktop:~$ sudo lshw -C network
  *-network
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 9
       bus info: pci@0000:05:09.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=32 modules=ssb

henrik@henrik-desktop:~$ lspci
05:09.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

henrik@henrik-desktop:~$ lspci -ns 05:09.0
05:09.0 0280: 14e4:4320 (rev 03)

```

---

### Post by dvyjones on 2008-05-25
Sorry for bumping, but I really need help with this, no net on my computer until its fixed. Tell me if you need more info (and preferably what info...)

---

### Post by paapu on 2009-02-24
Same problem with me (Acer Aspire 3022WLMi, Ubuntu 8.10). wlan0 was there but I got no wireless network. Googled some instructions and managed to loose the non-functional wlan0. Tried ndiswrapper with no luck. 
Wireless is working fine on the windows side of this laptop.
My data at the moment:

mka-laptop:~>lshw -C network
  *-network:0             
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 5
       bus info: pci@0000:06:05.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb

mka-laptop:~>lspci
06:05.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

mka-laptop:~> lspci -ns 06:05.0
06:05.0 0280: 14e4:4318 (rev 02)

mka-laptop:~>  ndiswrapper -l
bcmwl5 : driver installed
	device (14E4:4318) present (alternate driver: bcm43xx)

terveisin Markus :oops:

---

### Post by Iowan on 2009-02-24
The assignment should be in */etc/udev/rules.d/70-persistent-net.rules*.  File sez you can add your own, but it'd be easier to let the system build it - if it would.

---

### Post by paapu on 2009-05-06
Hei,
I upgraded to ubuntu 9.04.
Now wlan works fine without any hassle:)
Don't know what has been done but result is great!
(My system: Acer Aspire 3022WLMi)
terveisin, Markus

---

### Post by Iowan on 2009-05-06
> **paapu said:**
> I upgraded to ubuntu 9.04.
Now wlan works fine without any hassleMaybe it's just what gets posted, or what I notice... but it seems like "upgrade fixed my problems" are more rare than "major problems after upgrade".

Congrats! \\:D/

---

