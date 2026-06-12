---
title: "AR9485 Wireless Network Adapter"
date: 2015-02-23
forum: Networking &amp; Wireless
---

### Post by senti2 on 2015-02-23
Hallo Ubunutforums Community,
I have since I installed ubuntu in dualboot with winows8 a unstable internet connections (often high ping)
So here is my output from lshw -C nework:

```
senti@senti-Inspiron-ubuntu:~$ lshw -C network
WARNUNG: Sie sollten dieses Programm mit Systemverwalterrechten (root) ausführen.
  *-network               
       Beschreibung: Ethernet interface
       Produkt: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       Hersteller: Realtek Semiconductor Co., Ltd.
       Physische ID: 0
       Bus-Informationen: pci@0000:01:00.0
       Logischer Name: eth0
       Version: 05
       Seriennummer: b8:ca:3a:c5:6e:23
       Größe: 10Mbit/s
       Kapazität: 100Mbit/s
       Breite: 64 bits
       Takt: 33MHz
       Fähigkeiten: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       Konfiguration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8105e-1.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       Ressourcen: irq:44 ioport:2000(Größe=256) memory:c0404000-c0404fff memory:c0400000-c0403fff
  *-network
       Beschreibung: Kabellose Verbindung
       Produkt: AR9485 Wireless Network Adapter
       Hersteller: Qualcomm Atheros
       Physische ID: 0
       Bus-Informationen: pci@0000:02:00.0
       Logischer Name: wlan0
       Version: 01
       Seriennummer: f4:b7:e2:59:9e:1f
       Breite: 64 bits
       Takt: 33MHz
       Fähigkeiten: bus_master cap_list rom ethernet physical wireless
       Konfiguration: broadcast=yes driver=ath9k driverversion=3.13.0-45-generic firmware=N/A ip=192.168.0.160 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       Ressourcen: irq:17 memory:c0500000-c057ffff memory:afb00000-afb0ffff


```

Thanks for your help!:)
Kind regards
Senti

---

