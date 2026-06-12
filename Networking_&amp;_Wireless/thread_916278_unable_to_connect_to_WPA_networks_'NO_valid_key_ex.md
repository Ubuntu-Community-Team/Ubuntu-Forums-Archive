---
title: "unable to connect to WPA networks: 'NO valid key exists'"
date: 2008-09-10
forum: Networking &amp; Wireless
---

### Post by Fenderson on 2008-09-10
i am able to connect to unsecured networks as well as WEP secured networks, but not WPA (have only tried PSK type)

here is the syslog of the connection attempt:

```
Sep 10 19:05:34 avi-eee NetworkManager: <debug> [1221087934.664993] nm_device_802_11_wireless_get_activation_ap(): Forcing AP 'EMILY' 
Sep 10 19:05:34 avi-eee NetworkManager: <info>  User Switch: /org/freedesktop/NetworkManager/Devices/ra0 / EMILY 
Sep 10 19:05:34 avi-eee NetworkManager: <info>  Deactivating device ra0. 
Sep 10 19:05:34 avi-eee dhclient: There is already a pid file /var/run/dhclient.ra0.pid with pid 7091
Sep 10 19:05:34 avi-eee dhclient: killed old client process, removed PID file
Sep 10 19:05:35 avi-eee dhclient: DHCPRELEASE on ra0 to 192.168.0.1 port 67
Sep 10 19:05:35 avi-eee avahi-daemon[5054]: Withdrawing address record for 192.168.0.108 on ra0.
Sep 10 19:05:35 avi-eee avahi-daemon[5054]: Leaving mDNS multicast group on interface ra0.IPv4 with address 192.168.0.108.
Sep 10 19:05:35 avi-eee avahi-daemon[5054]: Interface ra0.IPv4 no longer relevant for mDNS.
Sep 10 19:05:35 avi-eee avahi-daemon[5054]: Withdrawing address record for fe80::215:afff:febc:c0c5 on ra0.
Sep 10 19:05:35 avi-eee NetworkManager: <info>  Device ra0 activation scheduled... 
Sep 10 19:05:35 avi-eee NetworkManager: <info>  Activation (ra0) started... 
Sep 10 19:05:35 avi-eee NetworkManager: <info>  Activation (ra0) Stage 1 of 5 (Device Prepare) scheduled... 
Sep 10 19:05:35 avi-eee NetworkManager: <info>  Activation (ra0) Stage 1 of 5 (Device Prepare) started... 
Sep 10 19:05:35 avi-eee NetworkManager: <info>  Activation (ra0) Stage 2 of 5 (Device Configure) scheduled... 
Sep 10 19:05:35 avi-eee NetworkManager: <info>  Activation (ra0) Stage 1 of 5 (Device Prepare) complete. 
Sep 10 19:05:35 avi-eee NetworkManager: <info>  Activation (ra0) Stage 2 of 5 (Device Configure) starting... 
Sep 10 19:05:35 avi-eee NetworkManager: <info>  Activation (ra0/wireless): access point 'EMILY' is encrypted, but NO valid key exists.  New key needed. 
Sep 10 19:05:35 avi-eee NetworkManager: <info>  Activation (ra0) New wireless user key requested for network 'EMILY'. 
Sep 10 19:05:35 avi-eee NetworkManager: <info>  Activation (ra0) Stage 2 of 5 (Device Configure) complete. 
```


seems like the problem is that it cant find the network key... not sure what to do from here.

the same wireless router with WPA encryption works fine on my windows machine.

thanks!

---

### Post by pytheas22 on 2008-09-10
First, try using [wicd]("http://wicd.sourceforge.net") instead of Network Manager; you might have better luck.

If not, please post the output of these commands so that we can figure out which chipset and driver you have; there's probably a better one (if you're using Ralink, which I think you are, you can install drivers that are more stable than the ones that Ubuntu ships with):
```

lshw -C Network
lspci -nn
lsusb
```

---

### Post by Fenderson on 2008-09-10
results with wicd were even worse... was not able to connect to any wireless network.

i have an Asus eeePC 1000, if that makes any difference.

here is the output from lshw -C Network

```
Framebuffer devices       [A
  *-network        
       description: Ethernet interface
       product: Attansic Technology Corp.
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: b0
       serial: 00:22:15:49:9d:d6
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=ATL1e driverversion=1.0.0.4 duplex=full firmware=L1e latency=0 link=yes module=atl1e multicast=yes port=twisted pair speed=100MB/s
  *-network
       description: Wireless interface
       product: RaLink
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: ra0
       version: 00
       serial: 00:15:af:bc:c0:c5
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2860 ip=192.168.0.108 latency=0 module=rt2860sta multicast=yes wireless=RT2860 Wireless
avi@avi-eee:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: Attansic Technology Corp.
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: b0
       serial: 00:22:15:49:9d:d6
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=ATL1e driverversion=1.0.0.4 firmware=L1e latency=0 module=atl1e multicast=yes
  *-network
       description: Wireless interface
       product: RaLink
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: ra0
       version: 00
       serial: 00:15:af:bc:c0:c5
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2860 ip=192.168.0.108 latency=0 module=rt2860sta multicast=yes wireless=RT2860 Wireless

```





and lspci -nn

```
00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GME Express Memory Controller Hub [8086:27ac] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GME Express Integrated Graphics Controller [8086:27ae] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller [8086:27d8] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 [8086:27d0] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 [8086:27d2] (rev 02)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 [8086:27d4] (rev 02)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 [8086:27d6] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 [8086:27c8] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 [8086:27c9] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 [8086:27ca] (rev 02)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 [8086:27cb] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller [8086:27cc] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 02)
00:1f.2 IDE interface [0101]: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller [8086:27c4] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801G (ICH7 Family) SMBus Controller [8086:27da] (rev 02)
01:00.0 Network controller [0280]: RaLink Unknown device [1814:0781]
03:00.0 Ethernet controller [0200]: Attansic Technology Corp. Unknown device [1969:1026] (rev b0)

```


and lsusb


```
Bus 005 Device 004: ID 04f2:b071 Chicony Electronics Co., Ltd 
Bus 005 Device 002: ID 058f:6335 Alcor Micro Corp. 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 0b05:b700 ASUSTek Computer, Inc. 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

```

---

### Post by pytheas22 on 2008-09-11
Sorry that wicd didn't help.  You can reinstall NM with:
```

sudo apt-get install network-manager-gnome
```

Unfortunately, I don't think that the legacy drivers from serialmonkey will support this card, as some googling suggests that it's very new (did you just buy this computer?).  Also, you seem to currently be using a driver named 'rt2860,' but I don't think that it's included in Ubuntu by default.  Did you install this driver yourself from somewhere?  Ralink has drivers [on its site]("http://www.ralinktech.com/ralink/Home/Support/Linux.html") that might work well, although I suspect that they're the ones you already have installed.  ndiswrapper might also work for this card, but again, since it's a very new device I couldn't find any affirmation by other users that ndiswrapper supports this card well.

Please let me know where you got the current driver from etc. and we can google around some more to see if there are any alternatives that you could try.

---

### Post by Fenderson on 2008-09-11
thanks for the help. i re-installed network manager and that fixed it.  not sure what the problem was but it is working now.

---

