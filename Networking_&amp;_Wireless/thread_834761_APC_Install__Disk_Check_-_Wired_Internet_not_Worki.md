---
title: "APC Install / Disk Check - Wired Internet not Working"
date: 2008-06-19
forum: Networking &amp; Wireless
---

### Post by drivehappy on 2008-06-19
I installed the latest updates on 6/18/08, turned it off for the night. Turn it on today, skip the disk check and do a quick svn checkin this morning (so network was working). Bought an APC ES 350 today and plugged the USB data cable into my computer as well. Booted it up and left it to disk check. After that the network would not get the IP information from my router (all other machines retrieve the IP info correctly still, wired/wireless).

```
eth0      Link encap:Ethernet  HWaddr 00:1a:92:83:5f:95  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:216 

eth1      Link encap:Ethernet  HWaddr 00:1a:92:83:68:2c  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:138 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:179 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:16459 (16.0 KB)  TX bytes:0 (0.0 B)
          Interrupt:217 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:622 errors:0 dropped:0 overruns:0 frame:0
          TX packets:622 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:39611 (38.6 KB)  TX bytes:39611 (38.6 KB)

wlan0     Link encap:Ethernet  HWaddr 00:18:4d:c6:50:01  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14020 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13335 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7091696 (6.7 MB)  TX bytes:1800918 (1.7 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-18-4D-C6-50-01-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

lspci:
```

00:00.0 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP55 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP55 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP55 USB Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation MCP55 USB Controller (rev a2)
00:04.0 IDE interface: nVidia Corporation MCP55 IDE (rev a1)
00:05.0 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:05.1 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:05.2 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:06.0 PCI bridge: nVidia Corporation MCP55 PCI bridge (rev a2)
00:06.1 Audio device: nVidia Corporation MCP55 High Definition Audio (rev a2)
00:08.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)
00:09.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)
00:0a.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:0d.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:0e.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:0f.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:0b.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
06:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 03)
06:00.1 IDE interface: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 03)
07:00.0 VGA compatible controller: nVidia Corporation GeForce 8600 GT (rev a1)

```

I was finally able to connect via a USB wireless adapter (as seen above). I tried both eth0 and eth1 jacks, in addition to turning off roaming mode and trying dhcp as well as Static IP with the correct info and it still doesn't work.

The nm-applet reports the driver used is "forcedeth". Thanks.

---

### Post by chili555 on 2008-06-19
Perhaps post #13 here will be useful: [http://ubuntuforums.org/showthread.php?t=830723&page=2&highlight=forcedeth](http://ubuntuforums.org/showthread.php?t=830723&page=2&highlight=forcedeth)

---

### Post by drivehappy on 2008-06-19
It seems this is nearly the exact same problem:

As post #13 summarizes:
```

00:08.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)
00:09.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)

```

However, a small difference (v 0.60 vs 0.61):
```

[   23.260691] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.

```

I tried the temporary solution as well as the proposed permanent one and the wired connection still doesn't work.

Edit: Looking deeper I came across [this]("https://bugs.launchpad.net/ubuntu/intrepid/+source/linux/+bug/136836") as well.

My output from sudo lspci -v:

```

00:0f.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=07, subordinate=07, sec-latency=0
	I/O behind bridge: 00007000-00007fff
	Memory behind bridge: f8000000-fbffffff
	Prefetchable memory behind bridge: 00000000e0000000-00000000efffffff
	Capabilities: [40] Subsystem: nVidia Corporation Unknown device 0000
	Capabilities: [48] Power Management version 2
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable+
	Capabilities: [60] HyperTransport: MSI Mapping
	Capabilities: [80] Express Root Port (Slot+) IRQ 0

```

More specifically I think it still shows MSI still enabled, even after the proposed solutions.

---

### Post by chili555 on 2008-06-19
> Edit: Looking deeper I came across this as well.That's where the fix came from; please see jad's post, about 40% down the page. What happens when you do:```
sudo dhclient eth1
```Thanks.

---

### Post by drivehappy on 2008-06-19
```

$ sudo dhclient eth1
There is already a pid file /var/run/dhclient.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/eth1/00:1a:92:83:68:2c
Sending on   LPF/eth1/00:1a:92:83:68:2c
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 1

```

I killed it at the end.

---

