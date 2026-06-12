---
title: "bcm wireless card not recognized in Gutsy"
date: 2007-11-09
forum: Networking &amp; Wireless
---

### Post by xjgnsdof on 2007-11-09
I have the bcm4318 wireless card on a Presario V2000. I installed the restricted drivers that came with Gutsy, and the wireless connection worked great at home. At school, I could never connect, so I removed the firmware and installed it again. Now, my wireless button won't light up, and I don't even have the option to enable wireless in the network manager.

I tried reinstalling the firmware while on an ethernet connection (so that I can download the firmware, which is what I have always done), and the wireless card connects just fine, but it's disabled again after I restart my computer. What's wrong? I'll keep my laptop from restarting til I get a solution.

---

### Post by kevdog on 2007-11-09
When its not working can you post the following:

lshw -C network

---

### Post by xjgnsdof on 2007-11-09
WARNING: you should run this program as super-user.
*-network:0
*[lists my ethernet card info]*

*-network:1 UNCLAIMED
description: Network controller
product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
vendor: Broadcom Corporation
physical id: 2
bus info: pci@0000:05:02.0
version: 02
width: 32 bits
clock: 33MHz
capabilities bus_master
configuration: latency=64

---

### Post by kevdog on 2007-11-09
Unclaimed means the driver is not installed or is not loaded.  

Lets see if you have the driver installed in the first place.  Do you get anything when you type:

modinfo bcm43xx

If something shows then if you do the following:
sudo modprobe bcm43xx

then recheck with lshw -C network, is the device still unclaimed??

Is the bcm43xx module blacklisted in the /etc/modprobe.d/blacklist file??

---

### Post by xjgnsdof on 2007-11-09
When I typed in ```
modinfo bcm43xx
```, followed by ```
sudo modprobe bcm43xx
```, I was able to turn on my wireless card and detect the wireless network in my apartment. And yes, I have bcm43xx blacklisted in /etc/modprobe.d/blacklist. How do I make this accessibility permanent?

---

### Post by kevdog on 2007-11-09
Simply comment out (#) or remove the blacklist line for the bcm43xx.  

The blacklist bcm43xx specifically tells the kernel not to load the driver module during boot.  If you remove this statement, then I think the module should be loaded automatically.  If it is not, to force custom kernel modules to load during boot (which bcm43xx is technically not), you would add simply bcm43xx on one new line in the /etc/modules file.

---

### Post by xjgnsdof on 2007-11-09
Thanks a lot kevdog. That fixed everything. I'll definitely write this down for my own records.

---

