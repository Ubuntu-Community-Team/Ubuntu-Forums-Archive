---
title: "Toshiba NB200-10Z wireless card working"
date: 2011-02-26
forum: New to Ubuntu
---

### Post by acbrown on 2011-02-26
My toshiba NB200-10Z laptop shows no wireless card in the device manager and won't connect to my wireless router. Any suggestions om whats wrong or how i could fix it? It connects to the router via the ethernet cable. :/ it is on windows xp.

---

### Post by davidmohammed on 2011-02-26
please post the results of the following commands in a terminal

sudo lshw -class network

lspci

lsusb

remember to paste the output within [CODE] tags.

...

its not clear if you are using ubuntu or windows xp - if the latter - suggest use a windows forum for help.

---

### Post by 3177 on 2011-02-26
gonna need some more info than that.
Whats your wireless card?

---

### Post by Matt__ on 2011-02-26
isnt the wireless on the 10Z atheros?

should work out of the box with ubuntu 10.10 using the ath9k driver.

---

### Post by metrics on 2011-09-20
> **Matt__ said:**
> isnt the wireless on the 10Z atheros?

should work out of the box with ubuntu 10.10 using the ath9k driver.

the card is an Atheros AR9285 and doesn't seem to work on ubuntu 11.04

the card in my laptop is  hard blocked = greyed out. ( rfkill unblock all didn't work)

thank you in advance for the help
```
 lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
03:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)


```

```
lsusb
Bus 005 Device 002: ID 054c:01f8 Sony Corp. 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 04f2:b128 Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


```

```
  sudo lshw -class network
*-network DISABLED      
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: 00:24:d2:a9:ba:90
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=2.6.38-10-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:f0100000-f010ffff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 02
       serial: 00:23:5a:f8:57:15
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:44 ioport:2000(size=256) memory:f0510000-f0510fff memory:f0500000-f050ffff memory:f0520000-f053ffff


```

---

