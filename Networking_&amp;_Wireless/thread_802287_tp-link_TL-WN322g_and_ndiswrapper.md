---
title: "tp-link TL-WN322g and ndiswrapper"
date: 2008-05-21
forum: Networking &amp; Wireless
---

### Post by wiredrick on 2008-05-21
Hi I am trying to setup my Tp-Link TL-wn322g USB wireless adapter on my Toshiba L20. I have Ubuntu 8.04 and have installed the vista drivers using ndiswrapper.

user@toshiba-L20:~$ ndiswrapper -l
netathrusb : driver installed
	device (0ACE:1215) present (alternate driver: zd1211rw)
user@toshiba-L20:~$ 

but lshw -C network only list my wired driver

user@toshiba-L20:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 2
       bus info: pci@0000:09:02.0
       logical name: eth0
       version: 10
       serial: 00:c0:9f:e0:b4:f7
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.0.2 latency=64 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
user@toshiba-L20:~$

I have added the following to /etc/network/interfaces 

auto wlan0
iface wlan0 inet dhcp 

any help is greatly appreciated

Have now solved problem

---

### Post by kralj299 on 2013-03-20
how did u solve problem.. i have same adapter but on 10.04 can you tell me?

---

