---
title: "Trying to adapt Trendnet TEW-643PI to Linux"
date: 2011-07-01
forum: New to Ubuntu
---

### Post by Flinxon on 2011-07-01
Hello,
I recently installed Ubuntu along with Windows 7 on my computer and it worked perfectly.

Except one thing, my network card/adapter wouldnt work. I am currently using my old and horrible usb network adapter from Zyxel.

Now I searched solutions for this problem and tried ndiswrapper.

I downloaded the correct driver but ndiswrapper said: "Error, invalid driver"

So that is my problem....

Does anyone recognize this problem or has a similar problem?


Best Regards,
Flinxon

---

### Post by TeoBigusGeekus on 2011-07-01
Can you post us the output of
```
lshw -C network
```
?

---

### Post by Flinxon on 2011-07-02
WARNING: you should run this program as super-user.
  *-network:0 UNCLAIMED   
       description: Network controller
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 2
       bus info: pci@0000:02:02.0
       version: 00WARNING: you should run this program as super-user.
  *-network:0 UNCLAIMED   
       description: Network controller
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 2
       bus info: pci@0000:02:02.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=32 maxlatency=64 mingnt=32
       resources: ioport:de00(size=256) memory:fddff000-fddfffff
  *-network:1
       description: Ethernet interface
       product: RTL-8110SC/8169SC Gigabit Ethernet
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 5
       bus info: pci@0000:02:05.0
       logical name: eth0
       version: 10
       serial: 6c:f0:49:2c:09:03
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=64 maxlatency=64 mingnt=32 multicast=yes port=MII speed=10Mbit/s
       resources: irq:21 ioport:dc00(size=256) memory:fddfe000-fddfe0ff memory:cff00000-cff1ffff
  *-network:0
       description: Ethernet interface
       physical id: 1
       bus info: usb@1:4
       logical name: eth1
       serial: 06:0c:ce:5e:72:17
       capabilities: ethernet physical
       configuration: broadcast=yes driver=ipheth multicast=yes
  *-network:1
       description: Wireless interface
       physical id: 2
       bus info: usb@1:3
       logical name: wlan0
       serial: 00:23:f8:2b:91:dd
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=zd1211rw driverversion=2.6.38-8-generic firmware=4725 ip=192.168.1.145 multicast=yes wireless=IEEE 802.11bg
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.

       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=32 maxlatency=64 mingnt=32
       resources: ioport:de00(size=256) memory:fddff000-fddfffff
  *-network:1
       description: Ethernet interface
       product: RTL-8110SC/8169SC Gigabit Ethernet
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 5
       bus info: pci@0000:02:05.0
       logical name: eth0
       version: 10
       serial: 6c:f0:49:2c:09:03
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=64 maxlatency=64 mingnt=32 multicast=yes port=MII speed=10Mbit/s
       resources: irq:21 ioport:dc00(size=256) memory:fddfe000-fddfe0ff memory:cff00000-cff1ffff
  *-network:0
       description: Ethernet interface
       physical id: 1
       bus info: usb@1:4
       logical name: eth1
       serial: 06:0c:ce:5e:72:17
       capabilities: ethernet physical
       configuration: broadcast=yes driver=ipheth multicast=yes
  *-network:1
       description: Wireless interface
       physical id: 2
       bus info: usb@1:3
       logical name: wlan0
       serial: 00:23:f8:2b:91:dd
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=zd1211rw driverversion=2.6.38-8-generic firmware=4725 ip=192.168.1.145 multicast=yes wireless=IEEE 802.11bg
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.

Super-user?
Sorry, I am new at this and learning.

---

### Post by Flinxon on 2011-07-03
> **TeoBigusGeekus said:**
> Can you post us the output of
```
lshw -C network
```?


WARNING: you should run this program as super-user.
  *-network:0 UNCLAIMED   
       description: Network controller
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 2
       bus info: pci@0000:02:02.0
       version: 00WARNING: you should run this program as super-user.
  *-network:0 UNCLAIMED   
       description: Network controller
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 2
       bus info: pci@0000:02:02.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=32 maxlatency=64 mingnt=32
       resources: ioport:de00(size=256) memory:fddff000-fddfffff
  *-network:1
       description: Ethernet interface
       product: RTL-8110SC/8169SC Gigabit Ethernet
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 5
       bus info: pci@0000:02:05.0
       logical name: eth0
       version: 10
       serial: 6c:f0:49:2c:09:03
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list rom ethernet physical tp mii  10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169  driverversion=2.3LK-NAPI duplex=half latency=64 maxlatency=64 mingnt=32  multicast=yes port=MII speed=10Mbit/s
       resources: irq:21 ioport:dc00(size=256) memory:fddfe000-fddfe0ff memory:cff00000-cff1ffff
  *-network:0
       description: Ethernet interface
       physical id: 1
       bus info: usb@1:4
       logical name: eth1
       serial: 06:0c:ce:5e:72:17
       capabilities: ethernet physical
       configuration: broadcast=yes driver=ipheth multicast=yes
  *-network:1
       description: Wireless interface
       physical id: 2
       bus info: usb@1:3
       logical name: wlan0
       serial: 00:23:f8:2b:91:dd
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=zd1211rw  driverversion=2.6.38-8-generic firmware=4725 ip=192.168.1.145  multicast=yes wireless=IEEE 802.11bg
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.

       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=32 maxlatency=64 mingnt=32
       resources: ioport:de00(size=256) memory:fddff000-fddfffff
  *-network:1
       description: Ethernet interface
       product: RTL-8110SC/8169SC Gigabit Ethernet
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 5
       bus info: pci@0000:02:05.0
       logical name: eth0
       version: 10
       serial: 6c:f0:49:2c:09:03
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list rom ethernet physical tp mii  10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169  driverversion=2.3LK-NAPI duplex=half latency=64 maxlatency=64 mingnt=32  multicast=yes port=MII speed=10Mbit/s
       resources: irq:21 ioport:dc00(size=256) memory:fddfe000-fddfe0ff memory:cff00000-cff1ffff
  *-network:0
       description: Ethernet interface
       physical id: 1
       bus info: usb@1:4
       logical name: eth1
       serial: 06:0c:ce:5e:72:17
       capabilities: ethernet physical
       configuration: broadcast=yes driver=ipheth multicast=yes
  *-network:1
       description: Wireless interface
       physical id: 2
       bus info: usb@1:3
       logical name: wlan0
       serial: 00:23:f8:2b:91:dd
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=zd1211rw  driverversion=2.6.38-8-generic firmware=4725 ip=192.168.1.145  multicast=yes wireless=IEEE 802.11bg
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.

Super-user?
Sorry, I am new at this and learning.

---

