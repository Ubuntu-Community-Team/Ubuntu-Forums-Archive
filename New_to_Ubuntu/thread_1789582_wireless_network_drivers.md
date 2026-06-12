---
title: "wireless network drivers"
date: 2011-06-24
forum: New to Ubuntu
---

### Post by kivilaakso on 2011-06-24
Hi, I recently installed Ubuntu 11.04 on my desktop and everything is running perfect, except for the internet, in this desktop I only use my wireless connection an ubuntu is not detecting the wireless networks, I searched and I tried to install the drivers but in the System>Applications>Hardware menu there were no drivers at all.

---

### Post by garvinrick4 on 2011-06-24
Open a terminal and run this so users can see your network card and driver:
```
sudo lshw -C network
```Post in your thread:

---

### Post by Bucky Ball on 2011-06-24
Have you/can you plug in an ethernet cable, get updates, then check Hardware Drivers again? This could save a lot of screwing around. ;)

---

### Post by kivilaakso on 2011-06-24
Here is what i got: 

 *-network               
       description: Ethernet interface
       product: AR8132 Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: c0
       serial: 70:71:bc:d2:96:f3
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:44 memory:feac0000-feafffff ioport:ec00(size=128)
  *-network DISABLED
       description: Wireless interface
       product: RT3090 Wireless 802.11n 1T/1R PCIe
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 00
       serial: 1c:65:9d:9d:b4:c3
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2800pci driverversion=2.6.38-8-generic firmware=0.11 latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:febf0000-febfffff

---

### Post by kivilaakso on 2011-06-24
> **Bucky Ball said:**
> Have you/can you plug in an ethernet cable, get updates, then check Hardware Drivers again? This could save a lot of screwing around. ;)

Actually I can't because the modem and the router are in the other side of my house.

---

### Post by Bucky Ball on 2011-06-24
Pity, cos that card will probably work 'out of the box'. Carry on ... ;)

---

### Post by kivilaakso on 2011-06-24
What should I do next people?

---

### Post by gandaran on 2011-06-24
> **kivilaakso said:**
> What should I do next people?
```
description: Wireless interface
product: RT3090 Wireless 802.11n 1T/1R PCIe
```
I don't know if the RT3090 chip works out of the box but if it doesn't I'm sure theres an easy fix, use the forum search for RT3090 wireless or post for help with this chip on the ubuntu networking and wireless forum section

---

### Post by hearthand on 2011-07-28
Ok-I had this problem too this is what just fixed it.

1, attach directly to the internet with the cable.
2, open the search and find the update package installer
3, run this and install all the updates, reboot
4, when the system reboots, click the idle wireless network icon on the top navigation bar, uncheck enable wireless then recheck it.
 my system downloaded new drivers and installed them, then the internet worked fine.:)

---

### Post by Paqman on 2011-07-28
> **kivilaakso said:**
> Actually I can't because the modem and the router are in the other side of my house.

You have our permission to carry your PC across the house if you want.

---

### Post by grahammechanical on 2011-07-28
For the record. There is a driver installed. It is

> driver=rt2800pci driverversion=2.6.38-8-generic

Regards.

---

