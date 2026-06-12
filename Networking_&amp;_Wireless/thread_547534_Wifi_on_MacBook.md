---
title: "Wifi on MacBook"
date: 2007-09-10
forum: Networking &amp; Wireless
---

### Post by mactiger on 2007-09-10
Wifi is not recognised on a MacBook. I did after clean install Ubuntu 7.04:

aptitude update
aptitude install build-essential
aptitude install module-assistant
m-a prepare

svn checkout [http://svn.madwifi.org/trunk](http://svn.madwifi.org/trunk) madwifi   <<<< did not work, so I downloaded manually<<<
cd madwifi
make clean
make
sudo make install
sudo modprobe ath_pci

no errors, but also no wifi

macbook@macbook-laptop:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 88E8053 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@01:00.0
       logical name: eth0
       version: 22
       serial: 00:19:e3:45:f9:b8
       size: 1GB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.13 duplex=full firmware=N/A ip=192.168.1.121 latency=0 link=yes multicast=yes port=twisted pair speed=1GB/s
       resources: iomemory:50200000-50203fff ioport:1000-10ff irq:17
  *-network UNCLAIMED
       description: Network controller
       product: Atheros Communications, Inc.
       vendor: Atheros Communications, Inc.
       physical id: 0
       bus info: pci@02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: iomemory:50100000-5010ffff irq:11

macbook@macbook-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

Thanks, Wim

---

### Post by RelativelyQuantum on 2007-12-29
Sorry, but, would someone mind clarifying a little?

---

