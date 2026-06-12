---
title: "BCM43142 wifi disconnecting problem"
date: 2017-11-10
forum: Networking &amp; Wireless
---

### Post by aliba777 on 2017-11-10
Hello! I have a problem with wifi since I started to use ubuntu 14.04. The problem is that it keeps disconnecting every 3-5 minutes from the network, which makes uncomfortable to use. I looked at every solution in the forum, but they did not work. 

Laptop model is HP 15p-165nr.

[COLOR=#000000][I]sudo lshw -C network

  *-network                 
       description: Wireless interface
       product: BCM43142 802.11b/g/n
       vendor: Broadcom Limited
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: wlo1
       version: 01
       serial: 74:29:af:e5:8f:1d
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=6.30.223.271 (r587334) ip=143.248.228.73 latency=0 multicast=yes wireless=IEEE 802.11
       resources: irq:18 memory:b5500000-b5507fff
  *-network
       description: Ethernet interface
       product: RTL8101/2/6E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eno1
       version: 08
       serial: d0:bf:9c:93:bc:55
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8106e-2_0.0.1 04/23/13 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:41 ioport:4000(size=256) memory:b5404000-b5404fff memory:b5400000-b5403fff




[/I][/COLOR]

Thank you in advance!

---

### Post by jeremy31 on 2017-11-11
Likely power management causing some of the issues
```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```
```
systemctl restart network-manager.service
```

---

