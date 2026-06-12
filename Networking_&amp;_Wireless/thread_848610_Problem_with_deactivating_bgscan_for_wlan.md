---
title: "Problem with deactivating bgscan for wlan"
date: 2008-07-03
forum: Networking &amp; Wireless
---

### Post by Headsick on 2008-07-03
Good evening...
I've a problem with my WLAN-Connection. My wlan performs a reconnect every 3-5 minutes. I've searched the internet to deactivate this scan and found this:
```
iwpriv eth0 bgscan 0
```
The problem is this:
```
root@Linux:/home/samuel# iwpriv eth0 bgscan 0
Invalid command : bgscan

```
My wlan-network adapter is eth0, zydas-chip and usb.

Is there and reason to deactivate this scan? Is there a file to do this manually? I've no idea...

If you need more informations - say it. ;)


Lg Headsick

---

### Post by Headsick on 2008-07-03
Some information for you...

ifconfig -a```
eth0      Link encap:Ethernet  Hardware Adresse 00:11:e2:01:41:c9  
          inet Adresse:192.168.100.56  Bcast:192.168.100.255  Maske:255.255.255.0
          inet6-Adresse: fe80::211:e2ff:fe01:41c9/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metrik:1
          RX packets:40737 errors:4453 dropped:1286 overruns:0 frame:4431
          TX packets:38404 errors:4572 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX bytes:26202528 (24.9 MB)  TX bytes:7023944 (6.6 MB)

eth1      Link encap:Ethernet  Hardware Adresse 00:13:8f:dd:d5:80  
          UP BROADCAST MULTICAST  MTU:1500  Metrik:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 Basisadresse:0x2000 

lo        Link encap:Lokale Schleife  
          inet Adresse:127.0.0.1  Maske:255.0.0.0
          inet6-Adresse: ::1/128 Gültigkeitsbereich:Maschine
          UP LOOPBACK RUNNING  MTU:16436  Metrik:1
          RX packets:4735 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4735 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:0 
          RX bytes:230650 (225.2 KB)  TX bytes:230650 (225.2 KB)

```
route -n```

Kernel-IP-Routentabelle
Ziel            Router          Genmask         Flags Metric Ref    Use Iface
192.168.100.0   0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.100.1   0.0.0.0         UG    0      0        0 eth0
```
iwconfig
```
lo        no wireless extensions.

eth1      no wireless extensions.

eth0      IEEE 802.11b/g  ESSID:"Homenet"  Nickname:"zd1211"
          Mode:Managed  Frequency:2.412 GHz  Access Point: **:**:**:**:**:**   
          Bit Rate=24 Mb/s   
          Encryption key:****-****-****-****-****-****-****-****-****-****-****-****-****-****-****-****-****   Security mode:open
          Link Quality=68/100  Signal level=20/100  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```
lspci
```
00:00.0 Host bridge: nVidia Corporation nForce3 250Gb Host Bridge (rev a1)
00:01.0 ISA bridge: nVidia Corporation nForce3 250Gb LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation nForce 250Gb PCI System Management (rev a1)
00:02.0 USB Controller: nVidia Corporation CK8S USB Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation CK8S USB Controller (rev a1)
00:02.2 USB Controller: nVidia Corporation nForce3 EHCI USB 2.0 Controller (rev a2)
00:05.0 Bridge: nVidia Corporation CK8S Ethernet Controller (rev a2)
00:08.0 IDE interface: nVidia Corporation CK8S Parallel ATA Controller (v2.5) (rev a2)
00:0a.0 IDE interface: nVidia Corporation CK8S Serial ATA Controller (v2.5) (rev a2)
00:0b.0 PCI bridge: nVidia Corporation nForce3 250Gb AGP Host to PCI Bridge (rev a2)
00:0e.0 PCI bridge: nVidia Corporation nForce3 250Gb PCI-to-PCI Bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation GeForce 7600 GT (rev a2)
02:07.0 Network controller: Techsan Electronics Co Ltd B2C2 FlexCopII DVB chip / Technisat SkyStar2 DVB card (rev 02)
02:08.0 Multimedia audio controller: Creative Labs SB0400 Audigy2 Value
root@Linux:/home/samuel# lspci
00:00.0 Host bridge: nVidia Corporation nForce3 250Gb Host Bridge (rev a1)
00:01.0 ISA bridge: nVidia Corporation nForce3 250Gb LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation nForce 250Gb PCI System Management (rev a1)
00:02.0 USB Controller: nVidia Corporation CK8S USB Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation CK8S USB Controller (rev a1)
00:02.2 USB Controller: nVidia Corporation nForce3 EHCI USB 2.0 Controller (rev a2)
00:05.0 Bridge: nVidia Corporation CK8S Ethernet Controller (rev a2)
00:08.0 IDE interface: nVidia Corporation CK8S Parallel ATA Controller (v2.5) (rev a2)
00:0a.0 IDE interface: nVidia Corporation CK8S Serial ATA Controller (v2.5) (rev a2)
00:0b.0 PCI bridge: nVidia Corporation nForce3 250Gb AGP Host to PCI Bridge (rev a2)
00:0e.0 PCI bridge: nVidia Corporation nForce3 250Gb PCI-to-PCI Bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation GeForce 7600 GT (rev a2)
02:07.0 Network controller: Techsan Electronics Co Ltd B2C2 FlexCopII DVB chip / Technisat SkyStar2 DVB card (rev 02)
02:08.0 Multimedia audio controller: Creative Labs SB0400 Audigy2 Value

```
lsusb
```
Bus 003 Device 004: ID 0ace:1211 ZyDAS 802.11b/g USB2 WiFi
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 046d:08da Logitech, Inc. QuickCam Messanger
Bus 001 Device 003: ID 03f0:7304 Hewlett-Packard DeskJet 35xx
Bus 001 Device 001: ID 0000:0000  

```

---

### Post by Headsick on 2008-07-05
*Push* - Hope, someone can help me...

---

