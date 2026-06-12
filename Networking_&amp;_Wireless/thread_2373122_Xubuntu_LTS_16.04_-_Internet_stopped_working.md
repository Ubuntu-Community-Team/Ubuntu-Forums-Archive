---
title: "Xubuntu LTS 16.04 - Internet stopped working"
date: 2017-10-03
forum: Networking &amp; Wireless
---

### Post by r102 on 2017-10-03
I have a PPPOE connection, through router. I tried wireless and with cable also, but it doesn't work. This happened all of a sudden. It is exactly like it is disabled from somewhere, it doesn't show any available networks. I ran some commands through terminal, I will post here the outcomes, maybe it will help.

ifconfig

enp0s25   Link encap:Ethernet  HWaddr b0:5a:da:b4:d0:2e
UP BROADCAST MULTICAST  MTU:1500  Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B )   TX bytes:0 (0.0 B )
Interrupt:20 Memory:d0700000-d0720000

lo

inet addr:127.0.0.1  Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING  MTU:65536  Metric:1
RX packets:2308 errors:0 dropped:0 overruns:0 frame:0
TX packets:2308 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:185728 (185.7 KB)  TX bytes:185728 (185.7 KB)

lspci -k

00:19.0 Ethernet controller: Intel Corporation Ethernet Connection I217-V (rev 04)
Subsystem: Hewlett-Packard Company Ethernet Connection I217-V
Kernel driver in use: e1000e
Kernel modules: e1000e
02:00.0 Network controller: Broadcom Corporation BCM43228 802.11a/b/g/n
DeviceName: WLAN
Subsystem: Broadcom Corporation BCM43228 802.11a/b/g/n
Kernel driver in use: bcma-pci-bridge
Kernel modules: bcma

ping 192.168.0.1
connect: Network is unreachable

ping [www.google.ro]("http://www.google.ro")
ping: unknown host [www.google.ro]("http://www.google.ro")


iwconfig
lo        no wireless extensions.
enp0s25   no wireless extensions.
sudo lshw -C network
*-network              
description: Ethernet interface
product: Ethernet Connection I217-V
vendor: Intel Corporation
physical id: 19
bus info: pci@0000:00:19.0
logical name: enp0s25
version: 04
serial: b0:5a:da:b4:d0:2e
capacity: 1Gbit/s
width: 32 bits
clock: 33MHz
capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=e1000e  driverversion=3.2.6-k firmware=0.12-3 latency=0 link=no multicast=yes  port=twisted pair
resources: irq:29 memory:d0700000-d071ffff memory:d073f000-d073ffff ioport:3080(size=32)
*-network
description: Network controller
product: BCM43228 802.11a/b/g/n
vendor: Broadcom Corporation
physical id: 0
bus info: pci@0000:02:00.0
version: 00
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress bus_master cap_list
configuration: driver=bcma-pci-bridge latency=0
resources: irq:18 memory:d0500000-d0503fff

My laptop's config is: 
Intel i5 4210M
8 GB RAM
SSD INTEL 2500 series
Nvidia HD4600

---

### Post by r102 on 2017-10-03
It was fixed using: sudo apt-get install --reinstall linux-headers-generic
and after that: sudo apt-get install bcmwl-kernel-source

---

### Post by r102 on 2017-10-03
But now when I try to run software updater, I receive the message from the picture

LE: Sorry for the double post

---

