---
title: "[SOLVED] Lost Internet after installing dvd drive"
date: 2007-12-02
forum: Networking &amp; Wireless
---

### Post by drs305 on 2007-12-02
More correctly, I lost my network. Last night after installing a dvd drive I found I couldn't connect to the (wired)  internet nor to my other home computers. I don't know if the two are related but usually things like this are.
Homebuilt, linux only - Gutsy 64, M2N-SLI deluxe, internet via router.

I've done the following:
Rechecked connections. I may have originally had the rj45 connected to the #1 ethernet port but that one doesn't seem to work. The ethernet 2 port lights up when the connection is plugged in but no internet or network connection.The connection lights on the hub are all illuminated.  If I remove the cable and plug it into a laptop the connection is almost instantaneous. Doesn't work via hub or directly to router but the same cable to a laptop works normally.

Tried restoring a /home backup image, then a root backup image. Didn't work.

Ping 192.168.0.XXX  Destination Host Unreachable
Ping 192.168.0.XXX (server) Destination Host Unreachable

I suspect some kind of hardware issue but don't know if I could have messed it up within the software settings.

Here are some outputs that might help id the problem:
The network interfaces seems odd to me. Also, running "sudo lshw -C network" produced no results. Is having eth1 and eth1 avahi normal? In system, admin, network tools, devices, eth1 has nothing listed - everything is "not available". Has my DHCP crapped out?

```


sudo ethtool eth0

Settings for eth0:
	Supported ports: [ MII ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Advertised auto-negotiation: Yes
	Speed: Unknown! (65535)
	Duplex: Unknown! (255)
	Port: MII
	PHYAD: 1
	Transceiver: external
	Auto-negotiation: on
	Supports Wake-on: g
	Wake-on: d
	Link detected: no


***

sudo ethtool eth1

Settings for eth1:
	Supported ports: [ MII ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Advertised auto-negotiation: Yes
	Speed: 100Mb/s
	Duplex: Half
	Port: MII
	PHYAD: 1
	Transceiver: external
	Auto-negotiation: on
	Supports Wake-on: g
	Wake-on: d
	Link detected: yes

***

lspci -nn

00:00.0 RAM memory [0500]: nVidia Corporation MCP55 Memory Controller [10de:0369] (rev a1)
00:01.0 ISA bridge [0601]: nVidia Corporation MCP55 LPC Bridge [10de:0360] (rev a2)
00:01.1 SMBus [0c05]: nVidia Corporation MCP55 SMBus [10de:0368] (rev a2)
00:01.2 RAM memory [0500]: nVidia Corporation MCP55 Memory Controller [10de:036a] (rev a2)
00:02.0 USB Controller [0c03]: nVidia Corporation MCP55 USB Controller [10de:036c] (rev a1)
00:02.1 USB Controller [0c03]: nVidia Corporation MCP55 USB Controller [10de:036d] (rev a2)
00:04.0 IDE interface [0101]: nVidia Corporation MCP55 IDE [10de:036e] (rev a1)
00:05.0 IDE interface [0101]: nVidia Corporation MCP55 SATA Controller [10de:037f] (rev a2)
00:05.1 IDE interface [0101]: nVidia Corporation MCP55 SATA Controller [10de:037f] (rev a2)
00:05.2 IDE interface [0101]: nVidia Corporation MCP55 SATA Controller [10de:037f] (rev a2)
00:06.0 PCI bridge [0604]: nVidia Corporation MCP55 PCI bridge [10de:0370] (rev a2)
00:06.1 Audio device [0403]: nVidia Corporation MCP55 High Definition Audio [10de:0371] (rev a2)
00:08.0 Bridge [0680]: nVidia Corporation MCP55 Ethernet [10de:0373] (rev a2)
00:09.0 Bridge [0680]: nVidia Corporation MCP55 Ethernet [10de:0373] (rev a2)
00:0e.0 PCI bridge [0604]: nVidia Corporation MCP55 PCI Express bridge [10de:0375] (rev a2)
00:0f.0 PCI bridge [0604]: nVidia Corporation MCP55 PCI Express bridge [10de:0377] (rev a2)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
01:0b.0 FireWire (IEEE 1394) [0c00]: Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link) [104c:8023]
02:00.0 SATA controller [0106]: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller [197b:2363] (rev 02)
02:00.1 IDE interface [0101]: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller [197b:2363] (rev 02)
03:00.0 VGA compatible controller [0300]: nVidia Corporation G70 [GeForce 7600 GS] [10de:0392] (rev a1)


***

ifconfig

eth0      Link encap:Ethernet  HWaddr 00:18:F3:B1:28:A7  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:22 Base address:0x2000 

eth1      Link encap:Ethernet  HWaddr 00:18:F3:B1:44:0A  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:45 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:255 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4424 (4.3 KB)  TX bytes:0 (0.0 b)
          Interrupt:21 Base address:0x4000 

eth1:avah Link encap:Ethernet  HWaddr 00:18:F3:B1:44:0A  
          inet addr:169.254.5.84  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:21 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:131 errors:0 dropped:0 overruns:0 frame:0
          TX packets:131 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:11830 (11.5 KB)  TX bytes:11830 (11.5 KB)


***

/etc/network/interfaces

auto lo
iface lo inet loopback


***

etc/hosts

127.0.0.1	localhost
127.0.1.XXX	hb1

192.168.0.XXX	hb1

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts


```

This is really frustrating, especially since I really don't know where to start.

Thanks.

---

### Post by drs305 on 2007-12-02
After about the fifth unsuccessful reboot, I turned off the computer, unplugged the ups, and let it sit for ten minutes. When I rebooted, the network was restored. Even the #1 ethernet connector now worked normally (as did #2). 

I have read that some people have had wake-on-lan issues. Perhaps it's related, or just gremlins running around my machine. In any case, the network is back on line ... for now.

I'll mark this solved if the network continues to work for the rest of the day.

---

