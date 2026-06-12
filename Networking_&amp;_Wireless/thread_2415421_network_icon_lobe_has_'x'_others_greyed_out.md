---
title: "network icon lobe has 'x' others greyed out"
date: 2019-03-25
forum: Networking &amp; Wireless
---

### Post by jgw on 2019-03-25
This is odd.  I am running with a powerline av2 2000 gigabit starter kit for wireless.  I have run speedtest-cli.  Last night I had 10mbits.  This morning .20 to .78  Switched to wireless and got 1.78   Sometimes my network just seems to go away.  I have turned my network on and off, restarted it, etc. several times.  Some info:
 sudo lshw -C network
  *-network                 
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: enp1s0
       version: 06
       serial: 40:8d:5c:4d:8d:8e
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168e-3_0.0.4 03/27/12 ip=192.168.0.29 latency=0 link=yes multicast=yes port=MII speed=1Gbit/s
       resources: irq:36 ioport:e000(size=256) memory:fea00000-fea00fff memory:d0800000-d0803fff
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       bus info: usb@1:3
       logical name: wlx008736326fa1
       serial: 00:87:36:32:6f:a1
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=mt7601u driverversion=4.15.0-46-generic firmware=N/A link=no multicast=yes wireless=IEEE 802.11

I am thinking about reinstalling the network.  If I should how?

Thank you.....................

---

### Post by jgw on 2019-03-30
apparently this is a mysterious and unsolvable problem so I will mark it solved.

---

