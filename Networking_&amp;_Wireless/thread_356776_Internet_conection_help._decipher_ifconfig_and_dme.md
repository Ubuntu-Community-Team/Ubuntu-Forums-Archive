---
title: "Internet conection help. decipher ifconfig and dmesg outputs"
date: 2007-02-08
forum: Networking &amp; Wireless
---

### Post by n0ll on 2007-02-08
[COLOR="Blue"]**Trying to get internet up on new install of kubuntu-amd64 edgy, I have Comcast cable using ethernet cable and a Motorola external modem.**[/COLOR]

[COLOR="Blue"]**Don’t know how to decipher the following outputs. Please advise as I am out of my realm here. Internet is not pnp? Conection works fine on my Win-xp com.**[/COLOR]

My Machine: ASUS M2N32-SLI-D, AMD64 +3800 Dual Core, CORSAIR XMS2 240-Pin DDR2 800, NVIDIA GeForce 7300 GT, HDD WD 150G Raptor

Thanks,


start outputs:

```
sudo pppoeconf
```

returns error: 
Access Concentractor of your provider did not respond


```
sudo ifconfig
```

returns: 

**eth0 **   Link encap:Ethernet  HWaddr 00:17:31: D C:4B:FE  
          inet6 addr: fe80::217:31ff:fedc:4bfe/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6718 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:411172 (401.5 KiB)  TX bytes:636 (636.0 b)
          Interrupt:225 Base address:0xa000 

**eth1**    Link encap:Ethernet  HWaddr 00:17:31: D C:59:78  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:233 Base address:0xc000 

**lo **       Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:416 errors:0 dropped:0 overruns:0 frame:0
          TX packets:416 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:31232 (30.5 KiB)  TX bytes:31232 (30.5 KiB)

**wlan0**     Link encap:Ethernet  HWaddr 00:15:AF:03:CF:C6  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:2 errors:0 dropped:2 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:184 (184.0 b)  TX bytes:0 (0.0 b)

```
dpkg -s pppoeconf
```
returns: 

Package: pppoeconf
Status: install ok installed
Priority: optional
Section: net
Installed-Size: 308
Maintainer: Ubuntu Core Developers <ubuntu-devel@lists.ubuntu.com>
Architecture: all
Version: 1.10ubuntu3
Recommends: locales
Suggests: xdialog
Description: configures PPPoE/ADSL connections
 User-friendly tool for initial configuration of a DSL (PPPoE) connection.
Original-Maintainer: Debian QA Group [email]packages@qa.debian.org[/email]

```
sudo lspci
```

returns:

00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:08.0 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a1)
00:09.0 ISA bridge: nVidia Corporation MCP55 LPC Bridge (rev a2)
00:09.1 SMBus: nVidia Corporation MCP55 SMBus (rev a2)
00:09.2 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a2)
00:0a.0 USB Controller: nVidia Corporation MCP55 USB Controller (rev a1)
00:0a.1 USB Controller: nVidia Corporation MCP55 USB Controller (rev a2)
00:0c.0 IDE interface: nVidia Corporation MCP55 IDE (rev a1)
00:0d.0 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:0d.1 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:0d.2 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:0e.0 PCI bridge: nVidia Corporation Unknown device 0370 (rev a2)
00:0e.1 Audio device: nVidia Corporation MCP55 High Definition Audio (rev a2)
00:10.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)
00:11.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)
00:12.0 PCI bridge: nVidia Corporation Unknown device 0376 (rev a2)
00:14.0 PCI bridge: nVidia Corporation Unknown device 0374 (rev a2)
00:16.0 PCI bridge: nVidia Corporation Unknown device 0375 (rev a2)
00:17.0 PCI bridge: nVidia Corporation Unknown device 0377 (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
02:00.0 VGA compatible controller: nVidia Corporation Unknown device 0393 (rev a1)
03:0b.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
06:00.0 Mass storage controller: Silicon Image, Inc. SiI 3132 Serial ATA Raid II Controller (rev 01)



```
sudo dmesg
```
returns:
attached dmesg.out file    
(too big, email me if you want the dmesg.out  file [email]andrewhadams@gmail.com[/email])

---

