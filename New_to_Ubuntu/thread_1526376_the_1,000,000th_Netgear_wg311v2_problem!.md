---
title: "the 1,000,000th Netgear wg311v2 problem!"
date: 2010-07-07
forum: New to Ubuntu
---

### Post by Gman279 on 2010-07-07
I've seen Netgear wg311v2 stuff all over but i cant seem to get mine to work no matter what i try from all different suggestions, I'm using Ubuntu 10.04 freshly installed, literally a few hours ago Ive done a little work to help you guys out...

First i did the lshw -C network thing, then iwconfig, what do I need to do!!!

sudo lshw -C network

  *-network:0             
       description: Ethernet interface
       product: RTL8139 Ethernet
       vendor: D-Link System Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 10
       serial: 00:40:05:0f:90:e0
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s
       resources: irq:21 ioport:de00(size=256) memory:feadcf00-feadcfff
  *-network:1 UNCLAIMED
       description: Network controller
       product: ACX 111 54Mbps Wireless Interface
       vendor: Texas Instruments
       physical id: 1
       bus info: pci@0000:01:01.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=64
       resources: memory:feade000-feadffff memory:feae0000-feafffff
  *-network:2
       description: Ethernet interface
       product: 82562EZ 10/100 Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:01:08.0
       logical name: eth1
       version: 02
       serial: 00:0c:f1:89:ec:d0
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=half firmware=N/A latency=64 link=no maxlatency=56 mingnt=8 multicast=yes port=MII speed=10MB/s
       resources: irq:20 memory:feadd000-feaddfff ioport:ddc0(size=64)
garrett@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.



P.S. this is my first time using Linux, so I'm a big noob!

---

### Post by bkratz on 2010-07-08
Perhaps this thread may be of some help--

[http://ubuntuforums.org/showthread.php?t=1404097&highlight=acx](http://ubuntuforums.org/showthread.php?t=1404097&highlight=acx)

Especially read Chili555's comment in post #3.

---

