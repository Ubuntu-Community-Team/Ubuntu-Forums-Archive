---
title: "Wireless internet"
date: 2008-01-21
forum: Networking &amp; Wireless
---

### Post by bluetwinkle on 2008-01-21
I have recently installed Ubuntu 7.10 on an Acer laptop, and I now realize that it can't connect to wireless. I tried to follow the troubleshooting steps in the Ubuntu help documentation, but couldn't understand what I was supposed to do.

typing in sudo lshw gives me this for wireless:
*-network DISABLED
description: Wireless interface
product: BCM94311MCG wlan mini-PCI
vendor: Broadcom Corporation
physical id: 0
bus info: pci@0000:03:00.0
logical name: eth1
version: 01
serial: 00:19:7e:90:42:71
width: 32 bits
clock: 33MHz
capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver=bcm43xx driverversion=2.6.22-14-generic latency=0 link=no module=bcm43xx multicast=yes wireless=IEEE 802.11b/g

sudo pccardctl ident gives me this:
Socket 0:
no product info available

And I have no idea what to do from there. I dual boot with Vista, and the wireless works fine there, but Ubuntu can't seem to be able to find the wireless hardware...

---

### Post by ACmilan on 2008-01-21
I recently had this same problem. This is what I was instructed to do by Kure-ji, so it's his work and not mine. This is my post with the link, [http://ubuntuforums.org/showthread.php?t=668460](http://ubuntuforums.org/showthread.php?t=668460), and the instructions are on that, it's the first from the bottom with all the terminal sections. Hope this works for you too.

---

### Post by rosegarden78 on 2008-01-21
a) Install the BCM43xx package from the repos

b) Type 
sudo modprobe bcm43xx 
from a terminal

c) Type 
nm-applet 
from a terminal

Note: if nm-applet is missing check the repos

---

