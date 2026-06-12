---
title: "Problems with Cisco Aironet Wireless 802.11b on Ubuntu 8.04"
date: 2008-08-04
forum: Networking &amp; Wireless
---

### Post by gabrieldiaz.semfid on 2008-08-04
Good Day

In my office my boss recently buy 6 IBM Thinkpad T40, and i install the ubuntu 8.04 on each, the problem is that the wireless card is not working.

i try to use the ndiswrapper, but i cannot find the drivers for the wireless card.

Pentium M 1.3Ghz, 1Gb Ram, 40Gb HDD and the wireless card is a Cisco Aironet Wireless 802.11b

i run the command " sudo lshw -C network " and it show me this

*-network:0
description: Network controller
product: Cisco Aironet Wireless 802.11b
vendor: AIRONET Wireless Communications
physical id: 2
bus info: pci@0000:02:02.0
version: 00
width: 32 bits
clock: 33MHz
capabilities: pm vpd bus_master cap_list
configuration: driver=airo latency=64 maxlatency=4 mingnt=4
*-network:1
description: Ethernet interface
product: 82801DB PRO/100 VE (MOB) Ethernet Controller
vendor: Intel Corporation
physical id: 8
bus info: pci@0000:02:08.0
logical name: eth0
version: 81
serial: 00:0d:60:2e:5e:06
size: 100MB/s
capacity: 100MB/s
width: 32 bits
clock: 33MHz
capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI duplex=full firmware=N/A ip=192.168.1.102 latency=66 link=yes maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=100MB/s

---

### Post by chili555 on 2008-08-04
First, Network Manager, which is installed by default, will not allow a wireless connection if you have a working ethernet connection, which you do:> driver=e100 driverversion=3.5.23-k4-NAPI duplex=full firmware=N/A ip=192.168.1.102Please detach the wire before you configure your wireless.

See post #2 here: [http://ubuntuforums.org/showthread.php?t=826233&highlight=aironet](http://ubuntuforums.org/showthread.php?t=826233&highlight=aironet)

---

### Post by gabrieldiaz.semfid on 2008-08-04
I read the post [http://ubuntuforums.org/showthread.p...hlight=aironet](http://ubuntuforums.org/showthread.p...hlight=aironet)

but do not solve my problem, because i know how to config the connection but i don't know how the make that the Ubuntu detect the wireless card.

And i cannot say that it works before, because the laptops was buy the last week.

i just detach the wire connection, and run the " sudo lshw -C network " and show me this now.

  *-network:0             
       description: Network controller
       product: Cisco Aironet Wireless 802.11b
       vendor: AIRONET Wireless Communications
       physical id: 2
       bus info: pci@0000:02:02.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm vpd bus_master cap_list
       configuration: driver=airo latency=64 maxlatency=4 mingnt=4
  *-network:1
       description: Ethernet interface
       product: 82801DB PRO/100 VE (MOB) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 81
       serial: 00:0d:60:7f:de:de
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI duplex=half firmware=N/A latency=66 link=no maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=10MB/s


:(
I am new on Ubuntu, and i try to show my boss that Ubuntu is better that Wintendo =) but this problem with the wireless is making me look bad. =(

Please help, i am from venezuela, but in Ubuntu-ve nobody answer me about this (they do help me about other questions) and ubuntu-es almost never work. =(

---

### Post by chili555 on 2008-08-04
Please confirm that you added the lines to your *blacklist* file, rebooted and there is no change to your *lshw*; that is, that your Aironet did not get a logical name like *eth1*, for example.

---

### Post by gabrieldiaz.semfid on 2008-08-11
well thanks for the help...

i still cannot make work the wireless in Ubuntu 8.04.1.

But it`s work in Ubuntu 8.10 Alfa 3 and work`s to in OpenSuse  11:):(

---

### Post by seren6ipity on 2008-11-06
Thank you Chili555 for your input. It rocked!!! :)
Thanks gabrieldiaz for starting this thread. 

I was able to fix the problem by blacklisting and restarting. Following which I went to Xubuntu system>network>unlock> Choose SSID

> **chili555 said:**
> Please confirm that you added the lines to your *blacklist* file, rebooted and there is no change to your *lshw*; that is, that your Aironet did not get a logical name like *eth1*, for example.

---

