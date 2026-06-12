---
title: "Wireless Card Errors after install"
date: 2007-07-12
forum: Networking &amp; Wireless
---

### Post by tyler_warren on 2007-07-12
using fiesty fawn release of Ubuntu and tried installing wireless card on ZV5000t laptop, HP, and installed fine until I went to run ifconfig/iwconfig and nothing came up for my wireless card. I also ran sudo ifup wlan0. I got the following messages when i ran the later. 

 ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.
 
can someone please explain that to me. I am new to  linux and trying set up wireless cards on it. Please help!!! If you need anymore information just let me know and I will get you what I can. there is also a bcmwl5a.inf.  Will that change anything. This driver should work without a problem. Like i said. Everything is good until that one point. Sorry this is lengthy. Just wanted to get all info i had in.

---

### Post by jimrz on 2007-07-12
> **tyler_warren said:**
> using fiesty fawn release of Ubuntu and tried installing wireless card on ZV5000t laptop, HP, and installed fine until I went to run ifconfig/iwconfig and nothing came up for my wireless card. I also ran sudo ifup wlan0. I got the following messages when i ran the later. 

 ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.
 
can someone please explain that to me. I am new to  linux and trying set up wireless cards on it. Please help!!! If you need anymore information just let me know and I will get you what I can. there is also a bcmwl5a.inf.  Will that change anything. This driver should work without a problem. Like i said. Everything is good until that one point. Sorry this is lengthy. Just wanted to get all info i had in.

Welcome

it woould appear you card is not recognised "out of the box', but most can still be made to work with a bit of tinkerin. please post your wifi card info - make/model/chipset. pretty hard to help out if we do not know what equipment is being dealt with

---

### Post by tyler_warren on 2007-07-13
This is what comes up when i run lspci

Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03), hope that is what your looking for. I tried finding more info but was unable to anywhere. 

I have  bcmwl5.inf  installed and it shows up as installed. but my card isn't recognized.

---

### Post by kevdog on 2007-07-13
Can you post:
lshw -C network

along with 
/etc/network/interfaces

---

### Post by tyler_warren on 2007-07-13
here is lshw output

  *-network:0             
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@02:02.0
       logical name: eth1
       version: 03
       serial: 00:90:4b:a3:1c:97
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.47+Broadcom,04/21/2005, 3.100. latency=64 link=no multicast=yes wireless=IEEE 802.11g
       resources: iomemory:d0204000-d0205fff irq:19
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 3
       bus info: pci@02:03.0
       logical name: eth0
       version: 10
       serial: 00:0f:b0:47:ae:71
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.2.202 latency=128 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: ioport:a000-a0ff iomemory:d0208800-d02088ff irq:1

and here is /etc/network/interfaces

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

---

### Post by tyler_warren on 2007-07-15
got wireless card working somehow to where is shows networks. It has connected once or twice now. However when I run iw(f)config it doesn't show a wlan it only shows eth1 even when I am connected to my network. Is that normal or is there something still not set right?

---

### Post by fredj on 2007-07-16
Wireless cards are often detected as eth0 rather than wlan0 that doesn't matter and has nothing to do with your
connection difficulties.

---

