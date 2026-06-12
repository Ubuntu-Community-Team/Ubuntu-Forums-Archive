---
title: "[SOLVED] WIRELESS PROBLEM IN HARDY (not the usual either)"
date: 2008-05-19
forum: Networking &amp; Wireless
---

### Post by k33bz on 2008-05-19
I know there is tons of threads on this. But none seem to match the problem I am having now.

I cant get my wireless to show anything. my chipset is AR5007EG. I know because I have it fixed in Fiesty. Which is what i am using at the moment. I can not connect to the internet by any means except by wireless. I had gotten Fiesty working with wireless only because I had hijacked the LAN form work, which i no longer work there.

I am currently tryin to get this all to work with my Hardy Installation, which really aint installed, just using the live cd till I can figure out how to get wireless on there. So please, a step by step guide for me to get wireless on Hardy, after installed, WITH OUT A INTERNET CONNECTION. I need to know what i need to download now with FIesty, to get Hardy installed and working with wireless. As soon as I install Hardy I wont have no wireless what so ever, or a way to connect to the internet unless I have wireless working.

So a big help to knwo what to download now, and hte commands to install it step by step will be very appreciated.


lspci
```
keebler@K33bz-mobile:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller (rev 14)
03:00.0 Ethernet controller: Atheros Communications, Inc. Unknown device 001c (rev 01)
0a:09.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
0a:09.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
keebler@K33bz-mobile:~$ 

```

sudo lshw -C network
```
keebler@K33bz-mobile:~$ sudo lshw -C network
Password:
  *-network               
       description: Ethernet interface
       product: 88E8038 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@02:00.0
       logical name: eth0
       version: 14
       serial: 00:1b:24:26:5b:e1
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.13 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: iomemory:34000000-34003fff ioport:2000-20ff irq:16
  *-network
       description: Wireless interface
       product: Atheros Communications, Inc.
       vendor: Atheros Communications, Inc.
       physical id: 0
       bus info: pci@03:00.0
       logical name: wlan0
       version: 01
       serial: 00:19:7e:4d:5b:1b
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper driverversion=1.38 firmware=,11/15/2006,5.1.1.9 ip=192.168.1.139 latency=0 link=yes multicast=yes wireless=IEEE 802.11g
       resources: iomemory:34100000-3410ffff irq:17
keebler@K33bz-mobile:~$ 

```

---

