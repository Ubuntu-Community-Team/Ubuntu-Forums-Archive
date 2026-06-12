---
title: "No wireless after re boot"
date: 2008-04-14
forum: Networking &amp; Wireless
---

### Post by uniuk2000 on 2008-04-14
Ok, brand new to Linux so please be kind.

I'm running 8.04 but I had the same problem with 7.10. I set up to my wpa encrypted network and all's well until I reboot / switch back on. I have to go back into network manager and re input wpa key and resave everything before my connection works again. Using a Dell Latitude 110L. This is the info from ishw -c network if it helps. How can I get it to boot and enable wireless?

dave@dave-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Wireless interface
       product: PRO/Wireless 2200BG Network Connection
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       logical name: eth1
       version: 05
       serial: 00:13:ce:0e:79:47
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) ip=192.168.15.3 latency=64 maxlatency=24 mingnt=3 module=ipw2200 multicast=yes wireless=IEEE 802.11g
  *-network:1
       description: Ethernet interface
       product: 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 03
       serial: 00:12:3f:16:b3:2b
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI firmware=N/A latency=64 maxlatency=56 mingnt=8 module=e100 multicast=yes

---

