---
title: "DELL insnpiron 1704 driver not working in 18.04"
date: 2018-06-20
forum: Networking &amp; Wireless
---

### Post by jackpinto on 2018-06-20
Hi there
Need help not able to connect to Wireless ..
sudo lshw -class network
  *-network UNCLAIMED       
       description: Network controller
       product: BCM43142 802.11b/g/n
       vendor: Broadcom Limited
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: memory:aa100000-aa107fff
  *-network
       description: Ethernet interface
       product: RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: enp7s0
       version: 07
       serial: 20:47:47:2b:19:5b
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8106e-1_0.0.1 06/29/12 ip=192.168.1.128 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:48 ioport:3000(size=256) memory:aa000000-aa000fff memory:c0000000-c0003fff

---

### Post by chili555 on 2018-06-20
What is your kernel version? From the terminal:```
uname -r
```

---

