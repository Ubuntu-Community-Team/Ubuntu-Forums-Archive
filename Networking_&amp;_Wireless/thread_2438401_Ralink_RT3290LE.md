---
title: "Ralink RT3290LE"
date: 2020-03-11
forum: Networking &amp; Wireless
---

### Post by jigsaff on 2020-03-11
Ubuntu 19.10, HP Pavilion g6, clean install. Wi-fi connection constantly disappears.
```
02:00.0 Network controller [0280]: Ralink corp. RT3290 Wireless 802.11n 1T/1R PCIe [1814:3290]
    DeviceName: Ralink RT3290LE 802.11bgn 1x1 Wi-Fi Adapter
    Subsystem: Hewlett-Packard Company Ralink RT3290LE 802.11bgn 1x1 Wi-Fi and Bluetooth 4.0 Combo Adapter [103c:18ec]
```

```
inxi -SN
```
```
System:
  Host: jigsaw Kernel: 5.3.0-40-generic x86_64 bits: 64 
  Desktop: Gnome 3.34.1 Distro: Ubuntu 19.10 (Eoan Ermine) 
Network:
  Device-1: Ralink RT3290 Wireless 802.11n 1T/1R PCIe driver: rt2800pci 
  Device-2: Realtek RTL810xE PCI Express Fast Ethernet driver: r8169
```

```
ip link
``` when wi-fi is down:
```
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN mode DEFAULT group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
2: eno1: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc fq_codel state DOWN mode DEFAULT group default qlen 1000
    link/ether a4:5d:36:77:22:4e brd ff:ff:ff:ff:ff:ff
3: wlo1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP mode DORMANT group default qlen 1000
    link/ether 0c:84:dc:67:c5:17 brd ff:ff:ff:ff:ff:ff
```

How to solve this problem?

---

