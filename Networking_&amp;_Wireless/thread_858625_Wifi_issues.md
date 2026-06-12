---
title: "Wifi issues"
date: 2008-07-13
forum: Networking &amp; Wireless
---

### Post by Fuzzykins on 2008-07-13
I am running Ubuntu 8.04 on a newly purchased Gateway notebook computer to decide if I want to convert over to it.  Initial installation went fine and so I tried to attain wifi capability by loading NDISwrapper from the distribution CD.  Upon loading the INF via the NDISwrapper, the GUI tells me that it has found the hardware and displays the INF name.  However, when I go to Network Configuration, the wifi card entry is not displayed.  The Gateway is the Costco M-6337 configuration natively running Vista Home Premium with a Ralink 802.11n wireless LAN card listed under Network Adaptor.

I would welcome any advice on troubleshooting and the general suitability of the Gateway configuration for Ubuntu.

---

### Post by adldesigner on 2008-07-14
Open up a terminal (Applications > Accessories > Terminal) and try the following commands:

(Lists all your PCI devices)
```
lspci
```
(Lists all your USB devices)
```
lsusb
```
(Lists your hardware and extracts Network entries)
```
sudo lshw -C -network
```
(Lists any wireless network available in your area)
```
iwlist scan
```

Post the output of each one of those commands enclosed by CODE tags (for better code readability).
This should help us start to diagnose your issue.

---

### Post by beldon on 2008-08-19
NOTE:  I have updated these to refelect results with the wifi switch actually turned on (d'oh!).

I have the same laptop and the same issue.  Here are the results of the commands:

lspci

```
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 04)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 04)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 04)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 04)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f4)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 04)
02:00.0 Network controller: RaLink Unknown device 0781
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)

```


lsusb

```
Bus 007 Device 001: ID 0000:0000
Bus 006 Device 001: ID 0000:0000
Bus 005 Device 002: ID 0461:4d03 Primax Electronics, Ltd Kensington Mouse-in-a-box
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 003: ID 0bda:0158 Realtek Semiconductor Corp.
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 002: ID 04f2:b027 Chicony Electronics Co., Ltd
Bus 001 Device 001: ID 0000:0000

```

sudo lshw -C network

```

  *-network UNCLAIMED
       description: Network controller
       product: RaLink
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: RTL8101E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 01
       serial: 00:e0:b8:fb:33:87
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=full ip=192.168.0.105 latency=0 link=yes module=r8169 multicast=yes port=twisted pair speed=100MB/s
```


iwlist scan

```

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.
```

Much appreciated!

     -=Beldon

---

