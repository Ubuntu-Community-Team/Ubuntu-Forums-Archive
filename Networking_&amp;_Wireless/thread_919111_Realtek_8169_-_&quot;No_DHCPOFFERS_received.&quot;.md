---
title: "Realtek 8169 - &quot;No DHCPOFFERS received.&quot;"
date: 2008-09-13
forum: Networking &amp; Wireless
---

### Post by geodanny on 2008-09-13
I am having difficulty connecting through my wired network. I've spent quite a bit of time looking through the forums and checking to see if I don't have the same issues as someone else but haven't gotten anything to work. Do you have any suggestions? 

The first thing I looked at was whether is is affected by the ["wake on lan after shutdown" issue]("http://www.linuxquestions.org/questions/linux-networking-3/realtek-813981688169-on-2.6.21.3-or-newer-593495/"). It does dual boot with windows but that issue doesn't appear to affect my computer. The wake setting is enabled and the issue continued after leaving the computer unplugged for a few minutes. 

Some info (perhaps, too much) to help you understand my setup.
**ethtool -i eth0**
```
driver: r8169
version: 2.2LK
firmware-version: 
bus-info: 0000:00:0b.0
```


**more /etc/network/interfaces**
```
auto lo
iface lo inet loopback


iface eth0 inet dhcp



auto eth0
```


**lscpi -vvnn:**
```
00:00.0 Host bridge [0600]: VIA Technologies, Inc. VT8385 [K8T800 AGP] Host Bridge [1106:3188] (rev 01)
	Subsystem: VIA Technologies, Inc. VT8385 [K8T800 AGP] Host Bridge [1106:3188]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ >SERR- <PERR+
	Latency: 8
	Region 0: Memory at <ignored> (32-bit, prefetchable)
	Capabilities: <access denied>

00:01.0 PCI bridge [0604]: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South] [1106:b188] (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 00009000-00009fff
	Memory behind bridge: cfe00000-cfefffff
	Prefetchable memory behind bridge: 8fd00000-cfcfffff
	Secondary status: 66MHz+ FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
	BridgeCtl: Parity- SERR+ NoISA+ VGA+ MAbort- >Reset- FastB2B-
	Capabilities: <access denied>

00:07.0 Ethernet controller [0200]: Atheros Communications Inc. AR2413 802.11bg NIC [168c:001a] (rev 01)
	Subsystem: D-Link System Inc D-Link AirPlus G DWL-G510 Wireless PCI Adapter(rev.B) [1186:3a16]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 168 (2500ns min, 7000ns max), Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 18
	Region 0: Memory at cffe0000 (32-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>

00:0b.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet [10ec:8169] (rev 10)
	Subsystem: Micro-Star International Co., Ltd. K8T NEO 2 motherboard [1462:702c]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 64 (8000ns min, 16000ns max), Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 16
	Region 0: I/O ports at e000 [size=256]
	Region 1: Memory at cfffef00 (32-bit, non-prefetchable) [size=256]
	Expansion ROM at cffa0000 [disabled] [size=128K]
	Capabilities: <access denied>

00:0d.0 RAID bus controller [0104]: Promise Technology, Inc. PDC20378 (FastTrak 378/SATA 378) [105a:3373] (rev 02)
	Subsystem: Micro-Star International Co., Ltd. K8T NEO FIS2R motherboard [1462:702e]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 96 (1000ns min, 4500ns max), Cache Line Size: 580 bytes
	Interrupt: pin A routed to IRQ 17
	Region 0: I/O ports at ec00 [size=64]
	Region 1: I/O ports at e800 [size=16]
	Region 2: I/O ports at e400 [size=128]
	Region 3: Memory at cffff000 (32-bit, non-prefetchable) [size=4K]
	Region 4: Memory at cffc0000 (32-bit, non-prefetchable) [size=128K]
	Capabilities: <access denied>

00:0e.0 FireWire (IEEE 1394) [0c00]: VIA Technologies, Inc. IEEE 1394 Host Controller [1106:3044] (rev 80) (prog-if 10 [OHCI])
	Subsystem: Micro-Star International Co., Ltd. K8T NEO 2 motherboard [1462:702d]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 32 (8000ns max), Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 19
	Region 0: Memory at cfffe000 (32-bit, non-prefetchable) [size=2K]
	Region 1: I/O ports at dc00 [size=128]
	Capabilities: <access denied>

00:0f.0 RAID bus controller [0104]: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller [1106:3149] (rev 80)
	Subsystem: Micro-Star International Co., Ltd. K8T Neo 2 Motherboard [1462:7020]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 32
	Interrupt: pin B routed to IRQ 20
	Region 0: I/O ports at d800 [size=8]
	Region 1: I/O ports at d400 [size=4]
	Region 2: I/O ports at d000 [size=8]
	Region 3: I/O ports at cc00 [size=4]
	Region 4: I/O ports at c800 [size=16]
	Region 5: I/O ports at c400 [size=256]
	Capabilities: <access denied>

00:0f.1 IDE interface [0101]: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE [1106:0571] (rev 06) (prog-if 8a [Master SecP PriP])
	Subsystem: Micro-Star International Co., Ltd. K8T NEO 2 motherboard [1462:7020]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 32
	Interrupt: pin A routed to IRQ 20
	Region 0: [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [size=8]
	Region 1: [virtual] Memory at 000003f0 (type 3, non-prefetchable) [size=1]
	Region 2: [virtual] Memory at 00000170 (32-bit, non-prefetchable) [size=8]
	Region 3: [virtual] Memory at 00000370 (type 3, non-prefetchable) [size=1]
	Region 4: I/O ports at fc00 [size=16]
	Capabilities: <access denied>

00:10.0 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 81) (prog-if 00 [UHCI])
	Subsystem: Micro-Star International Co., Ltd. K8T NEO 2 motherboard [1462:7020]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 32, Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 21
	Region 4: I/O ports at b400 [size=32]
	Capabilities: <access denied>

00:10.1 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 81) (prog-if 00 [UHCI])
	Subsystem: Micro-Star International Co., Ltd. K8T NEO 2 motherboard [1462:7020]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 32, Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 21
	Region 4: I/O ports at b800 [size=32]
	Capabilities: <access denied>

00:10.2 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 81) (prog-if 00 [UHCI])
	Subsystem: Micro-Star International Co., Ltd. K8T NEO 2 motherboard [1462:7020]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 32, Cache Line Size: 32 bytes
	Interrupt: pin B routed to IRQ 21
	Region 4: I/O ports at bc00 [size=32]
	Capabilities: <access denied>

00:10.3 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 81) (prog-if 00 [UHCI])
	Subsystem: Micro-Star International Co., Ltd. K8T NEO 2 motherboard [1462:7020]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 32, Cache Line Size: 32 bytes
	Interrupt: pin B routed to IRQ 21
	Region 4: I/O ports at c000 [size=32]
	Capabilities: <access denied>

00:10.4 USB Controller [0c03]: VIA Technologies, Inc. USB 2.0 [1106:3104] (rev 86) (prog-if 20 [EHCI])
	Subsystem: Micro-Star International Co., Ltd. K8T NEO 2 motherboard [1462:7020]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 32, Cache Line Size: 64 bytes
	Interrupt: pin C routed to IRQ 21
	Region 0: Memory at cfffed00 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

00:11.0 ISA bridge [0601]: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South] [1106:3227]
	Subsystem: VIA Technologies, Inc. DFI KT600-AL / Soltek SL-B9D-FGR Motherboard [1106:3227]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping+ SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Capabilities: <access denied>

00:11.5 Multimedia audio controller [0401]: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller [1106:3059] (rev 60)
	Subsystem: Micro-Star International Co., Ltd. K8T NEO 2 motherboard [1462:0080]
	Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Interrupt: pin C routed to IRQ 22
	Region 0: I/O ports at b000 [size=256]
	Capabilities: <access denied>

00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Capabilities: <access denied>

00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-

00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-

00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-

01:00.0 VGA compatible controller [0300]: ATI Technologies Inc RV350 AP [Radeon 9600] [1002:4150] (prog-if 00 [VGA controller])
	Subsystem: ABIT Computer Corp. Unknown device [147b:6193]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 32 (2000ns min), Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at b0000000 (32-bit, prefetchable) [size=256M]
	Region 1: I/O ports at 9800 [size=256]
	Region 2: Memory at cfef0000 (32-bit, non-prefetchable) [size=64K]
	Expansion ROM at cfec0000 [disabled] [size=128K]
	Capabilities: <access denied>

01:00.1 Display controller [0380]: ATI Technologies Inc RV350 AP [Radeon 9600] (Secondary) [1002:4170]
	Subsystem: ABIT Computer Corp. Unknown device [147b:6192]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 32 (2000ns min), Cache Line Size: 32 bytes
	Region 0: Memory at a0000000 (32-bit, prefetchable) [size=256M]
	Region 1: Memory at cfee0000 (32-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
```


**sudo ifup eth0:**
```
There is already a pid file /var/run/dhclient.eth0.pid with pid 0
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/eth0/00:0c:76:e2:a8:5b
Sending on   LPF/eth0/00:0c:76:e2:a8:5b
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

**sudo lshw:** 
```
id:	
network:1
description: 	Ethernet interface
product: 	RTL-8169 Gigabit Ethernet
vendor: 	Realtek Semiconductor Co., Ltd.
physical id: 	
b
bus info: 	
pci@0000:00:0b.0
logical name: 	
eth0
version: 	10
serial: 	00:0c:76:e2:a8:5b
size: 	100MB/s
capacity: 	1GB/s
width: 	32 bits
clock: 	66MHz
capabilities: 	pm bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
configuration:	
autonegotiation	=	on
broadcast	=	yes
driver	=	r8169
driverversion	=	2.2LK
duplex	=	full
latency	=	64
link	=	yes
maxlatency	=	64
mingnt	=	32
module	=	r8169
multicast	=	yes
port	=	twisted pair
speed	=	100MB/s
```


** dmesg | grep eth0**
```
[   44.937969] eth0: RTL8110s at 0xffffc20000324f00, 00:0c:76:e2:a8:5b, XID 04000000 IRQ 16
[   59.229358] r8169: eth0: link up
[  103.675899] eth0: no IPv6 routers present
[ 1695.323154] r8169: eth0: link up
[ 1705.635817] eth0: no IPv6 routers present
[ 2028.197763] eth0: RTL8110s at 0xffffc20000324f00, 00:0c:76:e2:a8:5b, XID 04000000 IRQ 16
[ 2028.213462] r8169: eth0: link down
[ 2028.214661] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 2030.292964] r8169: eth0: link up
[ 2030.294083] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 2040.570003] eth0: no IPv6 routers present
[ 2346.699251] r8169: eth0: link up
[ 2357.662278] eth0: no IPv6 routers present
```

Other commands I ran, based on suggestions on the boards: 

**sudo rmmod r8169**

**sudo modprobe r8169**

**sudo ifconfig eth0 up**

**sudo dhclient eth0**
```
There is already a pid file /var/run/dhclient.pid with pid 8874
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/eth0/00:0c:76:e2:a8:5b
Sending on   LPF/eth0/00:0c:76:e2:a8:5b
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```


**sudo ifconfig**
```
eth0      Link encap:Ethernet  HWaddr 00:0c:76:e2:a8:5b  
          inet6 addr: fe80::20c:76ff:fee2:a85b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:36 errors:0 dropped:0 overruns:0 frame:0
          TX packets:255 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2571 (2.5 KB)  TX bytes:33694 (32.9 KB)
          Interrupt:16 Base address:0x4f00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1854 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1854 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:92924 (90.7 KB)  TX bytes:92924 (90.7 KB)
```

---

### Post by cariboo on 2008-09-13
Thanks for all the info, but you forgot to tell us how you connect to the internet, is it directly to a modem, or through a router? If through a modem, do you need ppoe?

From all the info you posted it looks like the hardware is working ok, so the problem has to be elsewhwere. If you have another ethernet cable try that first.

Jim

---

### Post by geodanny on 2008-09-14
duh!

My Internet connection is DSL, connected by a D-Link DSL modem (DSL-2320B) that stores the PPPOE information (no need for the router to do so). 

I have a NetGear switch (fs605) that connects to the DSL modem and that my computers connect into for network access.  

I cannot connect to either the DSL modem or switch using the computer. I've switched ports and switched cables. I can connect through windows on the same computer so I know the Realtek 8169 NIC is not bad. 

I use the same network setup for my other computers, one of which uses the same version of Ubuntu (8.04). 

Any ideas? Perhaps I need to reinstall Ubuntu. The NIC has worked in the past, although not with this particular switch. Or perhaps I need to try with a different switch/router.

---

### Post by ab1301 on 2008-09-28
Did you ever solve this?  I am having similar problem with 8169. similar results with all those commands as well.  I am connecting through a dlink switch, which connects to a dlink wireless printserver/access point, which connects to a dlink wireless router, then cable modem.  The setup works just fine with other windows and linux computers.  I actually just unplugged the ethernet cable from a working linux box and plugged it into this one, and it still doesn't work.

---

### Post by geodanny on 2008-09-28
No, I still have problems but I'm closer to tracking down the origin. 

I found that this happens more after my computer hibernates than any other time (it does happen w/o hibernation). It generally does not happen when the computer turns on while the ethernet cable is attached to both the computer and router. If I plug the ethernet cable in after the computer is on, this problem occurs. I found this out last week after I needed to unplug the router to clean up around it. 

Once this problem raises its ugly head, I have more luck when I shutdown and then turn the computer back on. When I do, I need to run sudo dhclient. 

I have more luck plugged into a Linksys router than my D-Link DSL modem or the NetGear switch I had been using. 

In the end, it still happens but not as frequently.

---

### Post by lisati on 2008-09-28
I too sometimes have trouble connecting - thankfully not often - and use a Netgear router/switch (different model) and a D-link ADSL router/modem (provided by my ISP, also a different model). One of the first things I include in my troubleshooting repertoire is to restart both, wait for the Netgear router/switch to recognise that the D-link device is ready (the colour of the display indicators changes), and then try again. This usually works.

---

### Post by pzakielarz on 2008-10-04
I'm wondering if anyone got anywhere with this issue.  I'm having the same problem.

Something I can add is that I checked out the network traffic using another machine on the LAN.  I can see the DHCPDISCOVER request going out and a reply coming from my router, but for somereason dhclient exits reporting "No DHCPOFFERS received"

On another forum I've read that some people have had success with swapping out the NIC for another.

I'm hesitant because I know it works, and also the only spare I have is the same model.

---

### Post by kellyhardinguk on 2008-10-10
I've got the same issue. I found putting pci=noacpi at the end of the kernel line in the grub config file sorted it enough for me to get online.

Seems to be a bug in the 2.6.19-generic kernel with 8.0.4.1, as it didn't happen with 8.04 before upgrading.

Kelly

---

### Post by togo59 on 2008-10-15
I had the same issue exactly on my new Toshiba laptop with Realtex R8169

I could see the network VERY occasionally (about twice in 50 attempts).

[[COLOR="Blue"]But this worked for me [/COLOR]]("http://ubuntuforums.org/showpost.php?p=5580701&postcount=2")

:biggrin:

---

### Post by alfordej on 2008-12-23
Hello World!

I am a newb to Ubuntu, but not to forums\computing. I've been in the (WINDOWS)IT world for a while, just never touched linux\unix.

I am having the exact problem that the original poster described. After viewing my lspci results, I believe it might be a problem with my NIC sharing the same IRQ as other devices (sometimes my GPU, sometimes my USB controller), however I don't know how to effectively troubleshoot that in Linux.

I've tried a bunch of crazy GRUB start up commands: 
```


kernel	/boot/vmlinuz-2.6.12-10-k7 root=/dev/hdb1 ro quiet splash noapic nolapic

noapic acpi=noirq

noapic acpi=off

noapictimer

noapictimer irqpoll

noapic acpi=off

noapic acpi=noirq nolapic

clock=pmtmr notsc

notsc

```

None of those work.

I think I turned off IPv6 functionality with 
```


/etc/modprobe.d/aliases, change the line

alias net-pf-10 ipv6

to

alias net-pf-10 off


```

That didn't work either. So I commented it out. That didnt work.

I can post the basic diagnostic stuff if you want, just gotta find a thumb drive. Everything seems good though, I've been reading posts for the past two days, following everyone's troubleshooting steps to no avail.

Here is my setup:

Desktop Computer (MSI K8n Neo2 Platinum, AMD 3500+)
Onboard NIC (RealTek RTL-8169)
Wired Connection to Home Router
Home Router provides DHCP
Router connects to Cable Modem

Five other machines in this room work, including my previous setup (On the same hardware) running Windows.

Like I said, I've been in the IT world for a while, and really hate being stumped by a seemingly easy problem, so it took a lot for me to make an account and post here. Any help would be greatly appreciated!

Thanks,
Eric

EDIT:

Heres my uname -a
```

Linux ubuntubox 2.6.24-22-generic #1 SMP Mon Nov 24 18:32:42 UTC 2008 i686 GNU/Linux

```

---

### Post by alfordej on 2008-12-23
Update:  I don't have the capture of it, but I did a "dhclient eth1" and received an IP from my router. However, after it was received, dhclient kept looking for an IP. I did an 'ifconfig' and the IP didn't take.

My question is: Is it normal for dhclient to keep requesting IPs after the DHCP server issues one? If not, I could further deduce that this is more of an issue with my NIC driver or IRQ assignment.

---

### Post by The_Noise on 2009-01-06
Maybe the problem is related to this:

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/274593](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/274593)

---

