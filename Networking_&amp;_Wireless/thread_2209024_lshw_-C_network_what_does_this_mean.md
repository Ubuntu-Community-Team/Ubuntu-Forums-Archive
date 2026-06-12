---
title: "lshw -C network: what does this mean?"
date: 2014-03-03
forum: Networking &amp; Wireless
---

### Post by dcunn2002 on 2014-03-03
Just got a brand new laptop and installed Ubuntu 13.1.
No wi fi so did lshw-C netwok and got this - can anyone advise what this means as I can see no obvious reference to any wireless card:
Thanks
 *-network UNCLAIMED     
       description: Network controller
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: ioport:e000(size=256) memory:f7d00000-f7d03fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0.1
       bus info: pci@0000:03:00.1
       logical name: eth0
       version: 12
       serial: 00:90:f5:f0:8c:31
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8411-2_0.0.1 07/08/13 ip=192.168.1.74 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:47 ioport:d000(size=256) memory:f7c14000-f7c14fff memory:f7c10000-f7c13fff

---

### Post by chili555 on 2014-03-03
This is probably your wireless card:> *-network UNCLAIMED
description: Network controller
product: Realtek Semiconductor Co., Ltd.
vendor: Realtek Semiconductor Co., Ltd.
physical id: 0
bus info: pci@0000:02:00.0
version: 00
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress cap_list
configuration: latency=0
resources: ioport:e000(size=256) memory:f7d00000-f7d03fffUnclaimed suggests that there is no driver to claim and drive your wireless card. Let's further identify your card and find a driver. Please run and post:```
lspci -nn | grep 0280
```Thanks.

---

### Post by dcunn2002 on 2014-03-03
Thanks:

02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:b723]

---

### Post by chili555 on 2014-03-03
Perfect!

Hook up that ethernet and follow the steps in post #9 here: [http://ubuntuforums.org/showthread.php?t=2205497&p=12931188#post12931188](http://ubuntuforums.org/showthread.php?t=2205497&p=12931188#post12931188)

You may safely just copy and paste each command. Post back if you get stuck.

---

### Post by dcunn2002 on 2014-03-03
many, many thanks.

Replying via wi fi!

David

---

### Post by chili555 on 2014-03-03
Great news! When Update Manager installs a later kernel version, also known as linux-image, after reboot, recompile the driver:```
cd ~/rtl8723be
make clean
make
sudo make install
sudo modprobe rtl8723be
```Please retain the file and these instructions for that time.

---

### Post by dcunn2002 on 2014-03-03
Thanks again.  Really appreciated.

David

---

