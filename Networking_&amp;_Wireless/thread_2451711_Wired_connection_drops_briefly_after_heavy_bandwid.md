---
title: "Wired connection drops briefly after heavy bandwidth use"
date: 2020-10-09
forum: Networking &amp; Wireless
---

### Post by jordandunstall on 2020-10-09
Hello all,

Basically I have a wired connection, connected via powerlan adapters and the internet is slightly unstable. It will drop connection after around 15 minutes of multiplayer gaming as an example, as a result I'll have to disable then re-enable my networking for it to come back.

It does not seem to drop with light internet usage (browsing, watching videos).

Probably should note this doesn't happen on Windows.

Any ideas what this could be?

```
lshw -c network
```:

```
  *-network DISABLED        
       description: Wireless interface
       product: Wireless-AC 9260
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlp3s0
       version: 29
       serial: 3c:58:c2:c5:ab:fc
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=5.4.0-48-generic firmware=46.6bf1df06.0 latency=0 link=no multicast=yes wireless=IEEE 802.11
       resources: irq:24 memory:fc700000-fc703fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: enp4s0
       version: 26
       serial: 24:4b:fe:04:50:92
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 duplex=full firmware=rtl8168h-2_0.0.2 02/26/15 ip=192.168.1.97 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:35 ioport:f000(size=256) memory:fc604000-fc604fff memory:fc600000-fc603fff
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.



```

---

