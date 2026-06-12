---
title: "Wireless troubles (Atheros w/less adapter)"
date: 2008-08-15
forum: Networking &amp; Wireless
---

### Post by hackapelite on 2008-08-15
I can't get my wireless adapter to work on Ubuntu (8.04.01) on my Lappy (Compaq Presario C700 [C731TU]). It says that proprietary drivers for"Atheros Hardware Access Layer (HAL)" and "Support for Atheros 802.11 wireless LAN cards" are being used, but no wireless appears in network manager and the wireless indicator light stays off. Naturally, I've tried pressing the button on my lappy a thousand times, but it's never done a thing - it seems that it's being detected, but stays off for some reason.

Here's some output on my terminal mockaround:

====================
markus@PRESARIO:~$ sudo lshw -C network
  *-network UNCLAIMED     
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 10
       serial: 00:1b:38:bd:bd:cb
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=10.1.1.4 latency=64 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
markus@PRESARIO:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

markus@PRESARIO:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1b:38:bd:bd:cb  
          inet addr:10.1.1.4  Bcast:10.1.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:38ff:febd:bdcb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:22018 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19206 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:24323595 (23.1 MB)  TX bytes:3395427 (3.2 MB)
          Interrupt:21 Base address:0x1000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1334 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1334 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:66700 (65.1 KB)  TX bytes:66700 (65.1 KB)

markus@PRESARIO:~$ sudo ifup lo
ifup: interface lo already configured
=====================

I tried ifdown and then ifup, but that didn't help. 

If I have to resort to using ndiswrapper, should I get the drivers for Vista, XP or 2000? Currently I have a DSL modem hooked up via an ethernet cable, if that helps any...?

---

### Post by hackapelite on 2008-08-16
Okay, now it appears that the drivers for my w/less adapter are only available for Vista, and I hear that ndiswrapper only supports XP drivers (&older?). Can anyone confirm this? If this is true, I assume ndiswrapper is no option for me, correct?

Anyone know what else to try? Why aren't the Linux drivers working...? Does anyone know if this is distro-specific and would possibly work on another distro (I'm a noob so excuse my stupid questions)?

---

