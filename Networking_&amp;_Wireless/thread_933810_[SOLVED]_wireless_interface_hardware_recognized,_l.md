---
title: "[SOLVED] wireless interface: hardware recognized, logical name gone"
date: 2008-09-29
forum: Networking &amp; Wireless
---

### Post by spotsworth on 2008-09-29
hi all,
i've been running 7.10 for a while and had no problem getting my wireless to work initially.  a few days ago it stopped, and when i investigated the logical name of my wireless interface (eth1) got the respse 'device not found'.  below is the output for a few things that may tell someone else more than it told me.




gweather@mango:/$ sudo lshw -C network
[sudo] password for gweather:
  *-network               
       description: Network controller
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=ipw3945 latency=0 module=ipw3945
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:15:c5:04:49:8c
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=1.01 duplex=full ip=128.59.171.167 latency=64 link=yes module=b44 multicast=yes port=twisted pair speed=100MB/s


gweather@mango:/$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

answer found:#7
[http://ubuntuforums.org/showthread.php?t=571188&highlight=radio+frequency+kill+switch](http://ubuntuforums.org/showthread.php?t=571188&highlight=radio+frequency+kill+switch)

---

### Post by nixscripter on 2008-09-30
Good. Please mark this thread as solved (under the Thread Tools menu).

---

