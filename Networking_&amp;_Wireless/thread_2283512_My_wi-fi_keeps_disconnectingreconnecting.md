---
title: "My wi-fi keeps disconnecting/reconnecting"
date: 2015-06-22
forum: Networking &amp; Wireless
---

### Post by mikael-janek on 2015-06-22
I tried several reinstallations from 14.04 - 15.04. versions,  currently on 15.04. It seems until regular automatic updates take place  it does not happen but after them, my wifi-connection (not just home but  anywhere) keeps disconnecting and reconnecting which is extremely  irritating.
  I have gone through several topics on forum but could not fix it  (sometime did not really understand what am i supposed to do since I am  beginner in Ubuntu). Now I am almost positive it has to do something with the wi-fi drivers  but since I am newbie in Ubuntu I am unable to come with the solution  (what to check in terminal etc.)
  Any insight on this matter is extremely appreciated.
  I managed to follow something though which is:

  
```
sudo apt-get install linux-firmware-nonfree
  
sudo lshw -C network
  
*-network               
       description: Wireless interface
       product: BCM43142 802.11b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 48:d2:24:fa:05:dd
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=6.30.223.248 (r487574) ip=192.168.1.3 latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:17 memory:f0500000-f0507fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 07
       serial: 3c:97:0e:ca:91:42
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168e-3_0.0.4 03/27/12 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:25 ioport:2000(size=256) memory:f0404000-f0404fff memory:f0400000-f0403fff
```


  It may have something with switched wl0 or wlan0 but honestly I may be completely wrong.... Modinfo on both does not show anything...

---

### Post by PaulW2U on 2015-06-22
Moved to Networking & Wireless

---

### Post by mikael-janek on 2015-06-22
oh, I am sorry. saw similar thread in that section so thought it can be there...

---

### Post by PaulW2U on 2015-06-22
No problem, "that" section was for the development release - what will become Ubuntu 15.10.

Mods and admin staff will quite happily move posts to the correct sub-forum if need be.

---

