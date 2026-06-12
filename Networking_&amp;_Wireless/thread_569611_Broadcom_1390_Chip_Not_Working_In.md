---
title: "Broadcom 1390 Chip Not Working In"
date: 2007-10-07
forum: Networking &amp; Wireless
---

### Post by BlueFusionX on 2007-10-07
Hello there!

My Broadcom chip can return a list of networks but it will not connect.  in Gnome's network connection task icon it shows the blue swirl and then says not connected.  In Wifi radar it says it's connected, but it's really not.  Nothing works.  Prior to this I installed ndiswrapper and my driver.  Lspci tells me it's a 1390 card, but I'm beginning to doubt it.  After all it says it's for Dell but I'm on an HP Pavillion. . .

Bluefusionx

---

### Post by kevdog on 2007-10-07
Post the following to give some background info (Dell truemobile network card is a brand of wireless networking cards often found in many computers other than Dell!!)

lspci -nn
lshw -C network
iwlist scan  <==== Which network is yours???
ndiswrapper -v
ndiswrapper -l
modinfo ndiswrapper
lsmod | grep ndiswrapper

---

### Post by BlueFusionX on 2007-10-07
```
bfusionx@ubuntu:~/ies4linux-2.0.5$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub [8086:27a0] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller [8086:27a2] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller [8086:27d8] (rev 01)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 [8086:27d0] (rev 01)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 [8086:27d2] (rev 01)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 [8086:27d4] (rev 01)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 [8086:27c8] (rev 01)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 [8086:27c9] (rev 01)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 [8086:27ca] (rev 01)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 [8086:27cb] (rev 01)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller [8086:27cc] (rev 01)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e1)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 01)
00:1f.1 IDE interface [0101]: Intel Corporation 82801G (ICH7 Family) IDE Controller [8086:27df] (rev 01)
00:1f.2 SATA controller [0106]: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller AHCI [8086:27c5] (rev 01)
00:1f.3 SMBus [0c05]: Intel Corporation 82801G (ICH7 Family) SMBus Controller [8086:27da] (rev 01)
06:00.0 Network controller [0280]: Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card [14e4:4311] (rev 01)
08:08.0 Ethernet controller [0200]: Intel Corporation PRO/100 VE Network Connection [8086:1092] (rev 01)

```

```
bfusionx@ubuntu:~/ies4linux-2.0.5$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: Dell Wireless 1390 WLAN Mini-PCI Card
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@06:00.0
       logical name: eth1
       version: 01
       serial: 00:14:a5:ab:3d:1c
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper driverversion=1.42 firmware=Broadcom,10/12/2006, 4.100.15.5 latency=0 multicast=yes wireless=IEEE 802.11b
       resources: iomemory:20000000-20003fff irq:18
  *-network
       description: Ethernet interface
       product: PRO/100 VE Network Connection
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@08:08.0
       logical name: eth0
       version: 01
       serial: 00:16:d4:0b:a5:61
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.17-k2-NAPI firmware=N/A ip=192.168.0.114 latency=66 maxlatency=56 mingnt=8 multicast=yes
       resources: iomemory:d0100000-d0100fff ioport:2000-203f irq:21

```

```
bfusionx@ubuntu:~/ies4linux-2.0.5$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

**eth1 **     Scan completed :
          Cell 01 - Address: 00:0D:88:2C:40:7F
                    [B]ESSID:"default"
                    Protocol:IEEE 802.11[/B]b
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:92/100  Signal level:-37 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

```

```
bfusionx@ubuntu:~/ies4linux-2.0.5$ ndiswrapper -v
utils version: 1.9
driver version:        1.42
vermagic:       2.6.20-15-generic SMP mod_unload 586 
```

```
bfusionx@ubuntu:~/ies4linux-2.0.5$ ndiswrapper -l
bcmwl5 : driver installed
        device (14E4:4311) present (alternate driver: bcm43xx)

```

```
bfusionx@ubuntu:~/ies4linux-2.0.5$ modinfo ndiswrapper
filename:       /lib/modules/2.6.20-15-generic/misc/ndiswrapper.ko
license:        GPL
version:        1.42
description:    NDIS wrapper driver
author:         ndiswrapper team <ndiswrapper-general@lists.sourceforge.net>
srcversion:     348477D4AA1FCEC6D749644
depends:        usbcore
vermagic:       2.6.20-15-generic SMP mod_unload 586 
parm:           if_name:Network interface name or template (default: wlan%d) (charp)
parm:           proc_uid:The uid of the files created in /proc (default: 0). (int)
parm:           proc_gid:The gid of the files created in /proc (default: 0). (int)
parm:           debug:debug level (int)
parm:           hangcheck_interval:The interval, in seconds, for checking if driver is hung. (default: 0) (int)

```

```
bfusionx@ubuntu:~/ies4linux-2.0.5$ lsmod | grep ndiswrapper
ndiswrapper           194228  0 
usbcore               134280  7 ndiswrapper,usb_storage,libusual,ohci_hcd,uhci_hcd,ehci_hcd

```

---

### Post by kevdog on 2007-10-07
Never seen version 1.42 of ndiswrapper installed before -- its a nice change.  Anyway looks like you did a stellar job on setting up your ndiswrapper.  If something doesnt work however Im going to recommend updating to version 1.48, but that is later. 

Can you post 
/etc/iftab

Also try this at command line:
```
sudo ifdown eth1
sudo ifup eth1
sudo iwconfig eth1 essid default
sudo iwconfig eth1 mode Managed
sudo dhclient eth1
```

---

### Post by BlueFusionX on 2007-10-07
Those commands made it work!  Should I add them all to startup?  Here's what it outputted:

```

root@ubuntu:/etc# /etc/iftab
/etc/iftab: line 4: eth0: command not found
/etc/iftab: line 5: eth1: command not found
root@ubuntu:/etc# su bfusionx
bfusionx@ubuntu:/etc$ sudo ifdown eth1
sudo ifupifdown: interface eth1 not configured
bfusionx@ubuntu:/etc$ sudo ifup eth1
Ignoring unknown interface eth1=eth1.
bfusionx@ubuntu:/etc$ sudo iwconfig eth1 essid default
bfusionx@ubuntu:/etc$ sudo iwconfig mode Managed
Error : unrecognised wireless request "Managed"
bfusionx@ubuntu:/etc$ sudo dhclient eth1
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:14:a5:ab:3d:1c
Sending on   LPF/eth1/00:14:a5:ab:3d:1c
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPOFFER from 192.168.0.1
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPACK from 192.168.0.1
bound to 192.168.0.113 -- renewal in 285326 seconds.
bfusionx@ubuntu:/etc$ 



```

---

### Post by kevdog on 2007-10-07
I dont know why network manager doesnt connect!!! We simply did a manual connection at the command line so I would think network manager would do something similar.  You've got a bunch of choices at this point -- keep trying network manager, add those commands to a startup script, install version 1.34 of WICD, wifi radar.  Im not sure how to advise you to go.

---

### Post by BlueFusionX on 2007-10-07
From my experiments of each command, I found that it was the last one dealing with DCHP.  I might just uninstall NetworkManager.  Why would it not do the DCHP you think?

---

### Post by kevdog on 2007-10-07
It does do dhcp, however it just doesnt receive any offers.  You will find this at the command line also, it just seems in my experience to happen a lot less often

---

### Post by BlueFusionX on 2007-10-08
Well I suppose that solves my problem.  It's not very hard managing networks with command line and I'll do that from now on.  Thanks a bunch for your help!

---

