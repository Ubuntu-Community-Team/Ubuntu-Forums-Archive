---
title: "Realtek 8139 and Ubuntu 8.04=no wireless"
date: 2008-08-16
forum: Networking &amp; Wireless
---

### Post by Grimesville89 on 2008-08-16
First I am completely new to Ubuntu/Linux so most of the terms are like jibberish to me.  Please bear with me.  I have been searching around the forums trying to understand what I need to do.  I want to get away from windows but if I can not get my wireless up an running then I am forced to go back to Vista.

This is what I have---Installed Hardy last night tried to connect to my network and I can't even see it.  The light on my laptop that usually shows I am connected is red instead of blue.  I am on a Compaq Presario C751NR laptop.  When I go to edit wireless networks nothing shows up.

iwconfig says:

lo        no wireless extensions.

eth0      no wireless extensions.


lshw -C network says:


 description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 10
       serial: 00:1b:38:c3:4b:08
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.1.3 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes

what do i need to do???

--GV89

---

### Post by scream_sayonara on 2008-12-02
me too...

---

