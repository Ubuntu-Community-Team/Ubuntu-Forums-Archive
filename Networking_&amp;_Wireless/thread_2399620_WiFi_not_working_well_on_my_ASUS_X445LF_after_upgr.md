---
title: "WiFi not working well on my ASUS X445LF after upgrading from 16.04 to 18.04"
date: 2018-08-27
forum: Networking &amp; Wireless
---

### Post by MJae on 2018-08-27
I finally said yes to the upgrade prompt and now wireless not working all that well. Sometimes, it can connect (like now), but sometimes it can't (like yesterday). I'm not sure how to work through this. I'm not sure if these will help:

```

*-network                 
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: enp2s0
       version: 10
       serial: 9c:5c:8e:3f:a7:10
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168g-3_0.0.1 04/23/13 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:18 ioport:e000(size=256) memory:f7904000-f7904fff memory:f7900000-f7903fff
  *-network
       description: Wireless interface
       product: QCA9565 / AR9565 Wireless Network Adapter
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlp3s0
       version: 01
       serial: 80:a5:89:8b:53:1d
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=4.15.0-33-generic firmware=N/A ip=192.168.1.100 latency=0 link=yes multicast=yes wireless=IEEE 802.11
       resources: irq:19 memory:f7800000-f787ffff memory:f7880000-f788ffff

```

```

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

```

Here's the output from the wireless info script: [https://pastebin.com/QKyVpt3V](https://pastebin.com/QKyVpt3V)

---

