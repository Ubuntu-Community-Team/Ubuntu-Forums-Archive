---
title: "Xubuntu 14.04 eee pc 1001 ha LAN atheros AR8132 problem"
date: 2014-10-11
forum: Networking &amp; Wireless
---

### Post by erotavlas on 2014-10-11
Hi,

I installed xubuntu 14.04.1 32 bit version on eee pc 1001 ha. All works well except the LAN connection. It seems that the driver are correctly installed, but the network is not recognized. Any suggestions? 

Thank you

```

cat /etc/network/interfaces
 # interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

```
```

dmesg | grep -e eth0 -e bcm
[   15.700329] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   27.062443] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   27.076365] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready

```
```

 sudo lshw -C Network
  *-network               
       description: Wireless interface
       product: RT3090 Wireless 802.11n 1T/1R PCIe
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 00
       serial: 00:25:d3:98:de:90
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical 
wireless
       configuration: broadcast=yes driver=rt2800pci driverversion=3.13.0-37-
generic firmware=0.34 ip=192.168.0.6 latency=0 link=yes multicast=yes 
wireless=IEEE 802.11bgn
       resources: irq:17 memory:fbff0000-fbffffff
  *-network
       description: Ethernet interface
       product: AR8132 Fast Ethernet
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: c0
       serial: e0:cb:4e:86:c0:26
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet 
physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c 
driverversion=1.0.1.1-NAPI latency=0 link=no multicast=yes port=twisted pair
       resources: irq:45 memory:f7fc0000-f7ffffff ioport:ec00(size=128)

```
```

  lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GSE Express Memory 
Controller Hub [8086:27ac] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GSE 
Express Integrated Graphics Controller [8086:27ae] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/GME, 
943/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation NM10/ICH7 Family High 
Definition Audio Controller [8086:27d8] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation NM10/ICH7 Family PCI Express Port 
1 [8086:27d0] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation NM10/ICH7 Family PCI Express Port 
2 [8086:27d2] (rev 02)
00:1c.3 PCI bridge [0604]: Intel Corporation NM10/ICH7 Family PCI Express Port 
4 [8086:27d6] (rev 02)
00:1d.0 USB controller [0c03]: Intel Corporation NM10/ICH7 Family USB UHCI 
Controller #1 [8086:27c8] (rev 02)
00:1d.1 USB controller [0c03]: Intel Corporation NM10/ICH7 Family USB UHCI 
Controller #2 [8086:27c9] (rev 02)
00:1d.2 USB controller [0c03]: Intel Corporation NM10/ICH7 Family USB UHCI 
Controller #3 [8086:27ca] (rev 02)
00:1d.3 USB controller [0c03]: Intel Corporation NM10/ICH7 Family USB UHCI 
Controller #4 [8086:27cb] (rev 02)
00:1d.7 USB controller [0c03]: Intel Corporation NM10/ICH7 Family USB2 EHCI 
Controller [8086:27cc] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:
2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface 
Bridge [8086:27b9] (rev 02)
00:1f.2 SATA controller [0106]: Intel Corporation 82801GBM/GHM (ICH7-M Family) 
SATA Controller [AHCI mode] [8086:27c5] (rev 02)
01:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8132 Fast Ethernet 
[1969:1062] (rev c0)
02:00.0 Network controller [0280]: Ralink corp. RT3090 Wireless 802.11n 1T/1R 
PCIe [1814:3090]




```

---

### Post by TheFu on 2014-10-11
Wired?
/etc/network/interfaces is used on servers, not most desktops. Use network manager to setup desktop network connections. Oh - and either use wifi OR wired, not both at the same time.

There's a wifi info script somewhere around here. If you are trying to get wifi working, running that and posting the output should help those experts.

Wish I could help more - haven't booted my Eee 1008H since Feb. after getting a new netbook.

---

### Post by erotavlas on 2014-10-12
Yes I'm talking about wired connection. Normally, if I connect ethernet cable the system automatically recognizes the LAN. In this case this does not happen. I cannot figure out if it is a problem of driver or some weird setting. Wifi is working perfectly...

---

### Post by TheFu on 2014-10-12
disable the wifi. Having 2 different network devices enabled is complicated. rfkill is the command to "soft lock" it. Or just use the Fn-key.

Output from 
* ifconfig
* route

Also - try a different cable and port on the router/switch.

---

### Post by erotavlas on 2014-10-12
I solved by downloading all the updates from the repository. Thank you

---

