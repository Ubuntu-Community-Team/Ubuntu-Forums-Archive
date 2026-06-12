---
title: "Having problems with wired network on laptop"
date: 2007-12-11
forum: Networking &amp; Wireless
---

### Post by kaizah on 2007-12-11
My acer laptop consist out of a 2.6 ghz proc/ 512 mb ram with a realtec RTL8139 onboard lan card. I've been trying to fix this for a few days now.. looking for solutions, none have worked untill now.. PING doesn't even work to my router..

below are some results.. please can anyone help a desperate ex-windows user. :P

etc/network/interfaces
iface lo inet loopback

iface eth0 inet dhcp

auto eth0

king@king-ubuntu:~$ lspci -nn
00:00.0 Host bridge [0600]: Silicon Integrated Systems [SiS] SiS645DX Host & Memory & AGP Controller [1039:0646] (rev 01)
00:01.0 PCI bridge [0604]: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP) [1039:0001]
00:02.0 ISA bridge [0601]: Silicon Integrated Systems [SiS] SiS962 [MuTIOL Media IO] [1039:0962] (rev 14)
00:02.1 SMBus [0c05]: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller [1039:0016]
00:02.3 FireWire (IEEE 1394) [0c00]: Silicon Integrated Systems [SiS] FireWire Controller [1039:7007]
00:02.5 IDE interface [0101]: Silicon Integrated Systems [SiS] 5513 [IDE] [1039:5513]
00:02.6 Modem [0703]: Silicon Integrated Systems [SiS] AC'97 Modem Controller [1039:7013] (rev a0)
00:02.7 Multimedia audio controller [0401]: Silicon Integrated Systems [SiS] AC'97 Sound Controller [1039:7012] (rev a0)
00:03.0 USB Controller [0c03]: Silicon Integrated Systems [SiS] USB 1.0 Controller [1039:7001] (rev 0f)
00:03.1 USB Controller [0c03]: Silicon Integrated Systems [SiS] USB 1.0 Controller [1039:7001] (rev 0f)
00:03.2 USB Controller [0c03]: Silicon Integrated Systems [SiS] USB 1.0 Controller [1039:7001] (rev 0f)
00:03.3 USB Controller [0c03]: Silicon Integrated Systems [SiS] USB 2.0 Controller [1039:7002]
00:07.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
00:09.0 CardBus bridge [0607]: Texas Instruments PCI1520 PC card Cardbus Controller [104c:ac55] (rev 01)
00:09.1 CardBus bridge [0607]: Texas Instruments PCI1520 PC card Cardbus Controller [104c:ac55] (rev 01)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon RV250 [Mobility FireGL 9000] [1002:4c66] (rev 01)


king@king-ubuntu:~$ lspci -vvnn
00:00.0 Host bridge [0600]: Silicon Integrated Systems [SiS] SiS645DX Host & Mem
ory & AGP Controller [1039:0646] (rev 01)
        Subsystem: Wistron Corp. Unknown device [17c0:4000]
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Step
ping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort
- <MAbort+ >SERR- <PERR-
        Latency: 64
        Region 0: Memory at e8000000 (32-bit, non-prefetchable) [size=64M]
        Capabilities: <access denied>

00:01.0 PCI bridge [0604]: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI b
ridge (AGP) [1039:0001] (prog-if 00 [Normal decode])
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Step
ping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort-
<MAbort- >SERR- <PERR-
        Latency: 99
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=68
        I/O behind bridge: 0000a000-0000afff
        Memory behind bridge: ec100000-ec1fffff
        Prefetchable memory behind bridge: f0000000-f7ffffff
        Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort-
<MAbort+ <SERR- <PERR-
        BridgeCtl: Parity- SERR- NoISA+ VGA+ MAbort- >Reset- FastB2B-

00:02.0 ISA bridge [0601]: Silicon Integrated Systems [SiS] SiS962 [MuTIOL Media
 IO] [1039:0962] (rev 14)
        Control: I/O+ Mem+ BusMaster+ SpecCycle+ MemWINV- VGASnoop- ParErr- Step
ping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort
- <MAbort- >SERR- <PERR-
        Latency: 0

00:02.1 SMBus [0c05]: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
 [1039:0016]
        Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Step
ping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort
- <MAbort- >SERR- <PERR-
        Interrupt: pin B routed to IRQ 0
        Region 4: I/O ports at 9000 [size=32]

00:02.3 FireWire (IEEE 1394) [0c00]: Silicon Integrated Systems [SiS] FireWire C
ontroller [1039:7007] (prog-if 10 [OHCI])
        Subsystem: Wistron Corp. Unknown device [17c0:1054]
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Step
ping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort
- <MAbort- >SERR- <PERR-
        Latency: 64 (1000ns min, 3000ns max)
        Interrupt: pin B routed to IRQ 17
        Region 0: Memory at ec000000 (32-bit, non-prefetchable) [size=4K]
        [virtual] Expansion ROM at 40000000 [disabled] [size=128K]
        Capabilities: <access denied>

00:02.5 IDE interface [0101]: Silicon Integrated Systems [SiS] 5513 [IDE] [1039:
5513] (prog-if 80 [Master])
        Subsystem: Wistron Corp. Unknown device [17c0:1056]
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Step
ping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort
- <MAbort- >SERR- <PERR-
        Latency: 128
        Interrupt: pin ? routed to IRQ 16
        Region 0: [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disab
led] [size=8]
        Region 1: [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disab
led] [size=1]
        Region 2: [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disab
led] [size=8]
        Region 3: [virtual] Memory at 00000370 (type 3, non-prefetchable) [disab
led] [size=1]
        Region 4: I/O ports at 2000 [size=16]

00:02.6 Modem [0703]: Silicon Integrated Systems [SiS] AC'97 Modem Controller [1
039:7013] (rev a0) (prog-if 00 [Generic])
        Subsystem: Wistron Corp. Unknown device [17c0:1059]
        Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Step
ping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort
- <MAbort- >SERR- <PERR-
        Interrupt: pin C routed to IRQ 18
        Region 0: I/O ports at 1000 [size=256]
        Region 1: I/O ports at 1c00 [size=128]
        Capabilities: <access denied>

00:02.7 Multimedia audio controller [0401]: Silicon Integrated Systems [SiS] AC'
97 Sound Controller [1039:7012] (rev a0)
        Subsystem: Wistron Corp. Unknown device [17c0:200a]
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Step
ping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort
- <MAbort- >SERR- <PERR-
        Latency: 173 (13000ns min, 2750ns max)
        Interrupt: pin C routed to IRQ 18
        Region 0: I/O ports at 1400 [size=256]
        Region 1: I/O ports at 1c80 [size=128]
        Capabilities: <access denied>

00:03.0 USB Controller [0c03]: Silicon Integrated Systems [SiS] USB 1.0 Controll
er [1039:7001] (rev 0f) (prog-if 10 [OHCI])
        Subsystem: Wistron Corp. Unknown device [17c0:1056]
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Step
ping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort
- <MAbort- >SERR- <PERR-
        Latency: 64 (20000ns max)
        Interrupt: pin A routed to IRQ 19
        Region 0: Memory at ec001000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:03.1 USB Controller [0c03]: Silicon Integrated Systems [SiS] USB 1.0 Controll
er [1039:7001] (rev 0f) (prog-if 10 [OHCI])
        Subsystem: Wistron Corp. Unknown device [17c0:1056]
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Step
ping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort
- <MAbort- >SERR- <PERR-
        Latency: 64 (20000ns max)
        Interrupt: pin B routed to IRQ 20
        Region 0: Memory at ec002000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:03.2 USB Controller [0c03]: Silicon Integrated Systems [SiS] USB 1.0 Controll
er [1039:7001] (rev 0f) (prog-if 10 [OHCI])
        Subsystem: Wistron Corp. Unknown device [17c0:1056]
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Step
ping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort
- <MAbort- >SERR- <PERR-
        Latency: 64 (20000ns max)
        Interrupt: pin C routed to IRQ 21
        Region 0: Memory at ec003000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:03.3 USB Controller [0c03]: Silicon Integrated Systems [SiS] USB 2.0 Controll
er [1039:7002] (prog-if 20 [EHCI])
        Subsystem: Wistron Corp. Unknown device [17c0:1056]
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Step
ping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort
- <MAbort- >SERR- <PERR-
        Latency: 64 (20000ns max)
        Interrupt: pin D routed to IRQ 23
        Region 0: Memory at ec004000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:07.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/813
9C/8139C+ [10ec:8139] (rev 10)
        Subsystem: Wistron Corp. Unknown device [17c0:1053]
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Step
ping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort
- <MAbort- >SERR- <PERR-
        Latency: 64 (8000ns min, 16000ns max)
        Interrupt: pin A routed to IRQ 22
        Region 0: I/O ports at 1800 [size=256]
        Region 1: Memory at ec005000 (32-bit, non-prefetchable) [size=256]
        [virtual] Expansion ROM at 40020000 [disabled] [size=64K]
        Capabilities: <access denied>

00:09.0 CardBus bridge [0607]: Texas Instruments PCI1520 PC card Cardbus Control
ler [104c:ac55] (rev 01)
        Subsystem: Wistron Corp. Unknown device [17c0:3202]
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Step
ping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort
- <MAbort- >SERR- <PERR-
        Latency: 168, Cache Line Size: 128 bytes
        Interrupt: pin A routed to IRQ 16
        Region 0: Memory at 40030000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=00, secondary=02, subordinate=05, sec-latency=176
        Memory window 0: 30000000-33fff000 (prefetchable)
        Memory window 1: 34000000-37fff000
        I/O window 0: 00002400-000024ff
        I/O window 1: 00002800-000028ff
        BridgeCtl: Parity- SERR- ISA- VGA- MAbort- >Reset+ 16bInt+ PostWrite+
        16-bit legacy interface ports at 0001

00:09.1 CardBus bridge [0607]: Texas Instruments PCI1520 PC card Cardbus Control
ler [104c:ac55] (rev 01)
        Subsystem: Wistron Corp. Unknown device [17c0:3202]
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Step
ping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort
- <MAbort- >SERR- <PERR-
        Latency: 168, Cache Line Size: 128 bytes
        Interrupt: pin B routed to IRQ 17
        Region 0: Memory at 40031000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=00, secondary=06, subordinate=09, sec-latency=176
        Memory window 0: 38000000-3bfff000 (prefetchable)
        Memory window 1: 3c000000-3ffff000
        I/O window 0: 00002c00-00002cff
        I/O window 1: 00003000-000030ff
        BridgeCtl: Parity- SERR- ISA- VGA- MAbort- >Reset+ 16bInt+ PostWrite+
        16-bit legacy interface ports at 0001

01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon RV250 [Mob                                                              ility FireGL 9000] [1002:4c66] (rev 01) (prog-if 00 [VGA])
        Subsystem: Wistron Corp. Unknown device [17c0:2058]
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Step                                                              ping+ SERR- FastB2B+
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort                                                              - <MAbort- >SERR- <PERR-
        Latency: 66 (2000ns min), Cache Line Size: 16 bytes
        Interrupt: pin A routed to IRQ 16
        Region 0: Memory at f0000000 (32-bit, prefetchable) [size=128M]
        Region 1: I/O ports at a000 [size=256]
        Region 2: Memory at ec100000 (32-bit, non-prefetchable) [size=64K]
        [virtual] Expansion ROM at ec120000 [disabled] [size=128K]
        Capabilities: <access denied>

sudo dhclient eth0
king@king-ubuntu:~$ sudo dhclient eth0
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:0a:e4:43:2b:2d
Sending on   LPF/eth0/00:0a:e4:43:2b:2d
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

sudo lspci | grep -i eth
00:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

sudo lshw -C network
king@king-ubuntu:~$ sudo lshw -C network
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@0000:00:07.0
       logical name: eth0
       version: 10
       serial: 00:0a:e4:43:2b:2d
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full latency=64 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s

sudo ifconfig -a
king@king-ubuntu:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:0A:E4:43:2B:2D
          inet6 addr: fe80::20a:e4ff:fe43:2b2d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2077 (2.0 KB)  TX bytes:2940 (2.8 KB)
          Interrupt:23 Base address:0xe000

eth0:avah Link encap:Ethernet  HWaddr 00:0A:E4:43:2B:2D
          inet addr:169.254.4.41  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:23 Base address:0xe000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:32 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:2984 (2.9 KB)  TX bytes:2984 (2.9 KB)

sudo lsmod | grep 8139
king@king-ubuntu:~$ sudo lsmod | grep 8139
8139cp                 25088  0
8139too                27776  0
mii                     6528  2 8139cp,8139too

---

### Post by Original Brownster on 2007-12-12
Hi,
That's a strange problem you got there, everything looks right from your end. Some routers don't play nicely with ipv6 which can cause issues, since 7.10 uses this by default I would try disabling it. [this thread]("http://ubuntuforums.org/archive/index.php/t-87798.html") describes how to do it.

If this doesn't do it maybe it's the chipset being incorrectly recognised. 
Do you know if it works under windows ok?

---

### Post by phillips247n on 2007-12-12
Hi, 
I notice that the dhcp says it is not getting anything from the router, have you tried setting the ip address manually?

---

### Post by Sagadon on 2007-12-12
This is the same problem I'm having.  I notice your IP address is getting assigned similar to mine: 169.254.4.41.  I'm willing to bet an XP box on this connection works fine with DHCP.

Setting the static IP for me only meant there was no visible problems - just that nothing worked (including nslookup or ping to the router). 

I vaguely considered the situation where all traffic was being blocked and not being sent, or traffic was not being received for some reason.  My network card worked before I did any updates, and then stopped working (7.04).

Was yours working at one point, and then failed after doing updates?

---

