---
title: "Wifi not showing up but wireless hotspot does"
date: 2018-08-28
forum: Networking &amp; Wireless
---

### Post by kseyese9 on 2018-08-28
Hello all... I have a problem that I can't seem to find an answer to online, I recently started using ubuntu 18.04 and everything is fine except for the fact that I can't connect to my wifi network, I know it's there as it shows up on windows 10, but when I switch back to ubuntu, it's not displaying whenever I look at the available wireless networks , and when I tried to see if my hotspot would work, it apparently does. I can't seem to find any answer elsewhere online for it.. I would appreciate if someone here could help. Here is my wifi card:

 *-network                 
       description: Wireless interface
       product: RTL8723BE PCIe Wireless Network Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlo1
       version: 00
       serial: 3c:a0:67:ba:47:c1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8723be driverversion=4.15.0-29-generic firmware=N/A ip=192.168.43.106 latency=0 link=yes multicast=yes wireless=IEEE 802.11
       resources: irq:40 ioport:3000(size=256) memory:f0c00000-f0c03fff
  *-network
       description: Ethernet interface
       product: RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: enp3s0
       version: 07
       serial: 3c:52:82:89:df:fa
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8106e-1_0.0.1 06/29/12 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:31 ioport:2000(size=256) memory:f0b00000-f0b00fff memory:f0800000-f0803fff

---

