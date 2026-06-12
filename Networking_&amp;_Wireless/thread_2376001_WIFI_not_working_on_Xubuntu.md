---
title: "WIFI not working on Xubuntu"
date: 2017-10-29
forum: Networking &amp; Wireless
---

### Post by shooteger on 2017-10-29
Hello guys,

please help me I search now for hours on the internet for my problem. I have no WIFI but Ethernet is perfectly working. I have all the newest updates.

-the command iwconfig says:

lo        no wireless extensions.

enp2s0f1  no wireless extensions.

-thean the command lsusb say:

Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 248a:8366  
Bus 001 Device 003: ID 04f2:b59e Chicony Electronics Co., Ltd 
Bus 001 Device 002: ID 8087:0a2b Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

-last command I used is sudo lshw -C network  and output here:

  *-network               
       Beschreibung: Ethernet interface
       Produkt: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       Hersteller: Realtek Semiconductor Co., Ltd.
       Physische ID: 0.1
       Bus-Informationen: pci@0000:02:00.1
       Logischer Name: enp2s0f1
       Version: 12
       Seriennummer: 80:fa:5b:42:0a:1f
       Größe: 1Gbit/s
       Kapazität: 1Gbit/s
       Breite: 64 bits
       Takt: 33MHz
       Fähigkeiten: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       Konfiguration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8411-2_0.0.1 07/08/13 ip=192.168.0.18 latency=0 link=yes multicast=yes port=MII speed=1Gbit/s
       Ressourcen: irq:130 ioport:e000(Größe=256) memory:df114000-df114fff memory:df110000-df113fff
  *-network UNGEFORDERT
       Beschreibung: Network controller
       Produkt: Intel Corporation
       Hersteller: Intel Corporation
       Physische ID: 0
       Bus-Informationen: pci@0000:03:00.0
       Version: 78
       Breite: 64 bits
       Takt: 33MHz
       Fähigkeiten: pm msi pciexpress cap_list
       Konfiguration: latency=0
       Ressourcen: memory:df000000-df001fff


So why can't my WLAN card find any Wlan here? Please help me

---

### Post by ajgreeny on 2017-10-29
See **Wireless-info** in my signature, download it and run the script, then report back the output here or using [http://pastebin.ubuntu.com/](http://pastebin.ubuntu.com/) if the output is too large to add direct.

The forum wifi gurus will probably be able to help you more with the extra info contained in your output.

---

