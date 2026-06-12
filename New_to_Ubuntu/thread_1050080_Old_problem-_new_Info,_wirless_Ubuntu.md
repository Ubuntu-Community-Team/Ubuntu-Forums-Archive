---
title: "Old problem- new Info, wirless Ubuntu"
date: 2009-01-25
forum: New to Ubuntu
---

### Post by Yed Ied on 2009-01-25
Gateway laptop MX6436, command prompt-lshw -c network-
*-network
description: ethernet interface
product: 88E8036 PCI-E fast Ethernet Controller
vendor: Marvell Tech. Group Ltd.
physical id: 0
bus info: pci@oooo:03:00.0
logical name: eth0
version 10
serial: 00:e0:b8:8f:6b:6a
capacity: 100MB/s
width 64 bits
clock: 33MHz
capabilities: pm vpd msi pciexpress bus_master cap_list ethernet
phisical tp 10bt-fd 100bt 100bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.22 firmware=N/A latency=0 module=sky2 multicast=yes port=twisted pair
*-network
description: Network controller
product: BCM4318 [Air Force One 54g] 802.11g Wireless LAN Controller
vendor: Broadcom Corp
physical id: 2
bus info: pci@0000:05:02.0
version:02 
width: 32 bits
clock: 33MHz 
capabilities: bus_master
configuration: driver=b43-pci-bridge latency=64 module=ssb
*-network:1 DISABLED
description: Ethernet Interface
physical id: 2
logical name: pan0
serial: ba:70:fd:f6:86:b3
capabilities ethernet physical
configuration: broadcast=yes driver=bridge driverversion=2.3
firmware=N/A link=yes multicast=yes
*-network:0 DISABLED
description: Wireless interface
physical id: 1
logical name: wlan0
serial: 00:14:a5:87:f2:3d
capabilities: ethernet physical wireless
configuration: broadcast+yes multicast=yes wireless=IEEE 802.11g
Hope this is what you need.

---

### Post by Yed Ied on 2009-01-25
command prompt- sudo lspci | grep -i net
03:00.0 Ethernet controller: Marvell Technology Froup Ltd.
88E8036 PCI-E Fast Ethernet Controller (rev 10)
05:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev o2)

Hope this is of some help. Thanks

---

### Post by Yed Ied on 2009-01-25
I know this may seem an amaturish suggestion, but I've already lost any sense of ego, I once may have had, but could I just ENABLE the two network descriptions that are DISABLED?

---

### Post by sp0nge on 2009-01-25
I had a similar issue where there was the smallest button that needed to be pushed to enable the wireless card. Does your machine have such a button? Look at the light for the wireless signal (mine are all on the front of the laptop), there should be a painted or engraved icon on the light. Look around the machine for a switch or button with this icon and see if that makes a difference. 

With my particular POS, once I enabled the WiFi, I had to restart the machine (although restarting the network may work, I didn't actually think to do so until now). 

Anyway, the next thing I would try would be System>Administration>Hardware Drivers and see what's there and ensure your driver is installed and working.

---

### Post by Yed Ied on 2009-01-25
I am very new to laptops.  You are right about the lights, just in front of the left right click buttons are a row of 5 lit icons.  Left to right is a ((.)), a padlock with an "A" in the middle, then another padlock with a "1", then what looks like a cup with a rectangle standing on end in it, with a up & down arrow in that, and finally what looks like a soup can, that seems to be the indicator for the hard drive, by that I mean as work is being done it blinks.  The first icon, double ((.)) is lit all the time. the three middle icons never, or I've never noticed them even blink.  I would never have thought of considering them as part of the problem, thanks for the input.

---

