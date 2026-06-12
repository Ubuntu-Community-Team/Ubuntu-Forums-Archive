---
title: "How can i enable wi-fi and bluetooth?"
date: 2008-10-13
forum: Networking &amp; Wireless
---

### Post by Fabolous_Boy on 2008-10-13
OK, i got alot of problems, first, I CANNOT ENABLE WI-FI. second, I CANNOT  ENABLE BLUETOOTH. third, I CANNOT SUCCESFULLY ENABLE STUFF LIKE THE COMPIZ FUSION IN TERMINAL (but this is kinda off-topic so lets just stick to the 2 problems)

Can someone please properly explain how to enable WI-FI without having to buy another Wi-FI card??

and also please include how to enable bluetooth

im using an MSI Wind by the way...(which has BUILT IN WI-FI which i dont know how to enable in Ubuntu)

---

### Post by superprash2003 on 2008-10-13
in your terminal type lshw -C network and post output.. also post output of iwconfig

---

### Post by dogeatery on 2008-10-13
Hi, I am having a similar problem in that my notebook has integrated Bluetooth but I can't seem to make it work ....

```
dogeatery@dogeatery-laptop ~ $ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:12:3f:f9:0a:cc
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 latency=32 module=ssb multicast=yes
  *-network:1
       description: Wireless interface
       product: PRO/Wireless 2200BG Network Connection
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       logical name: eth1
       version: 05
       serial: 00:13:ce:0f:44:41
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) ip=192.168.1.102 latency=32 maxlatency=24 mingnt=3 module=ipw2200 multicast=yes wireless=IEEE 802.11g

```

---

