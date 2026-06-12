---
title: "can't connect with an ethernet cable"
date: 2009-07-25
forum: New to Ubuntu
---

### Post by malaikaangel on 2009-07-25
Hello,
i'm very new to ubuntu... My ethernet connection worked fine until a couple of days ago when I couldn't connect via an ethernet cable anymore. I have to plug the ethernet cable into a USB adaptor which I then connect to my laptop. Wireless connection works fine.
I guess it's something to do with my network card?
Here are 
**sudo dhclient eth0**
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/eth0/00:1b:38:ca:9f:cb
Sending on   LPF/eth0/00:1b:38:ca:9f:cb
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
No DHCPOFFERS received.
No working leases in persistent database - sleeping

**and lspci**
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
05:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)
06:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
07:00.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
07:00.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
07:00.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
07:00.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
07:00.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)

**and lsusb**
Bus 007 Device 002: ID 0a5c:2101 Broadcom Corp. A-Link BlueUsbA2 Bluetooth
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 005: ID 2001:1a00 D-Link Corp. [hex] 10/100 Ethernet
Bus 002 Device 002: ID 064e:a101 Suyin Corp. Acer CrystalEye Webcam
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 15ca:00c3 Textech International Ltd. Mini Optical Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

**and ifconfig**
eth0      Link encap:Ethernet  HWaddr 00:1b:38:ca:9f:cb  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Packets reçus:0 erreurs:0 :0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:0 (0.0 B) Octets transmis:0 (0.0 B)
          Interruption:18 

eth1      Link encap:Ethernet  HWaddr 00:80:c8:37:c3:6d  
          inet adr:192.168.0.142  Bcast:192.168.0.255  Masque:255.255.255.0
          adr inet6: fe80::280:c8ff:fe37:c36d/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:119453 erreurs:0 :0 overruns:0 frame:0
          TX packets:82650 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:175359568 (175.3 MB) Octets transmis:6427177 (6.4 MB)

eth0:avahi Link encap:Ethernet  HWaddr 00:1b:38:ca:9f:cb  
          inet adr:169.254.9.93  Bcast:169.254.255.255  Masque:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interruption:18 

lo        Link encap:Boucle locale  
          inet adr:127.0.0.1  Masque:255.0.0.0
          adr inet6: ::1/128 Scope:Hôte
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          Packets reçus:124 erreurs:0 :0 overruns:0 frame:0
          TX packets:124 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0 
          Octets reçus:13888 (13.8 KB) Octets transmis:13888 (13.8 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1f:3a:34:3b:54  
          inet adr:192.168.1.74  Bcast:192.168.1.255  Masque:255.255.255.0
          adr inet6: fe80::21f:3aff:fe34:3b54/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:38004 erreurs:0 :0 overruns:0 frame:0
          TX packets:2340 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:1601991 (1.6 MB) Octets transmis:145071 (145.0 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1F-3A-34-3B-54-62-35-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:0 erreurs:0 :0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:0 (0.0 B) Octets transmis:0 (0.0 B)

I hope this makes some sense to anyone willing to help me...
Thanks a lot

---

### Post by kansasnoob on 2009-07-25
I'm really clueless, but you might look at "**Known Jaunty Wireless/Ethernet workarounds**" here:

[http://ubuntuforums.org/forumdisplay.php?f=336](http://ubuntuforums.org/forumdisplay.php?f=336)

You may even want to repost this question there. (Or click on "report post" and request that one of the moderators move it.

Sorry I can't be of any real help, at least you can consider this a free bump:)

---

### Post by LookTJ on 2009-07-25
If you are trying get a lease through DHCP, try this [workaround]("http://ubuntuforums.org/showpost.php?p=7276275&postcount=8").

:)

---

### Post by malaikaangel on 2009-07-26
> **kansasnoob said:**
> I'm really clueless, but you might look at "**Known Jaunty Wireless/Ethernet workarounds**" here:

[http://ubuntuforums.org/forumdisplay.php?f=336](http://ubuntuforums.org/forumdisplay.php?f=336)

You may even want to repost this question there. (Or click on "report post" and request that one of the moderators move it.

Sorry I can't be of any real help, at least you can consider this a free bump:)

Thanks!:D that link was helpful, I found another[ link]("http://www.prash-babu.com/2009/05/how-to-fix-ubuntu-network-manager-error.html") which helped me, the problem was with Network Manager apparently.

---

