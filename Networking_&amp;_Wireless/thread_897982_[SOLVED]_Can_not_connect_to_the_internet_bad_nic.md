---
title: "[SOLVED] Can not connect to the internet bad nic?"
date: 2008-08-22
forum: Networking &amp; Wireless
---

### Post by ooolongT on 2008-08-22
I can not connect to the internet. I think there is something wrong with my nic but I am not sure. The facts:
[LIST=1]
[*]Brand new (as of yesterday) install of Ubuntu Hardy 8.04.1.  Had to replace it due to other problems, this one does seem to be working better, but this networking problem has persisted.
[*]Dual boots with MS XP and has a strong connection.
[*]Nic says Network Everywhere nc100N on it.
[*]I have done a reasonable amount of research, and nothing seems to help (including replacing the Network Everywhere card with a Realtek 8169 card).
[*]I tried using the old acpi=off pci=noacpi trick, and that has not helped.
[*]It worked yesterday just fine after the new install.  
[*]I am frustrated.

[/LIST]

Info:
```
############# ifconfig -a 


eth1      Link encap:Ethernet  HWaddr 00:11:5b:2b:76:22  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:23 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2230 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2230 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:111500 (108.8 KB)  TX bytes:111500 (108.8 KB)



############# lspci -vvnn

00:00.0 Host bridge [0600]: VIA Technologies, Inc. CN400/PM880 Host Bridge [1106:0259]
	Subsystem: Elitegroup Computer Systems Unknown device [1019:1899]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ >SERR- <PERR+
	Latency: 8
	Region 0: Memory at d0000000 (32-bit, prefetchable) [size=128M]
	Capabilities: [80] AGP version 3.5
		Status: RQ=32 Iso- ArqSz=0 Cal=0 SBA+ ITACoh- GART64- HTrans- 64bit- FW+ AGP3- Rate=x1,x2,x4
		Command: RQ=1 ArqSz=0 Cal=0 SBA+ AGP+ GART64- 64bit- FW- Rate=x4
	Capabilities: [50] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-

00:00.1 Host bridge [0600]: VIA Technologies, Inc. CN400/PM880 Host Bridge [1106:1259]
	Subsystem: Elitegroup Computer Systems Unknown device [1019:1899]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0

00:00.2 Host bridge [0600]: VIA Technologies, Inc. CN400/PM880 Host Bridge [1106:2259]
	Subsystem: Elitegroup Computer Systems Unknown device [1019:1899]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0

00:00.3 Host bridge [0600]: VIA Technologies, Inc. CN400/PM880 Host Bridge [1106:3259]
	Subsystem: Elitegroup Computer Systems Unknown device [1019:1899]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0

00:00.4 Host bridge [0600]: VIA Technologies, Inc. CN400/PM880 Host Bridge [1106:4259]
	Subsystem: Elitegroup Computer Systems Unknown device [1019:1899]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0

00:00.7 Host bridge [0600]: VIA Technologies, Inc. CN400/PM880 Host Bridge [1106:7259]
	Subsystem: Elitegroup Computer Systems Unknown device [1019:1899]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0

00:01.0 PCI bridge [0604]: VIA Technologies, Inc. VT8237 PCI Bridge [1106:b198] (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	Memory behind bridge: dc000000-ddffffff
	Prefetchable memory behind bridge: d8000000-dbffffff
	Secondary status: 66MHz+ FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR+ <PERR+
	BridgeCtl: Parity- SERR+ NoISA+ VGA+ MAbort- >Reset- FastB2B-
	Capabilities: [70] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-

00:09.0 FireWire (IEEE 1394) [0c00]: Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link) [104c:8024] (prog-if 10 [OHCI])
	Subsystem: Ads Technologies Inc Unknown device [1421:0001]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 32 (500ns min, 1000ns max), Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 17
	Region 0: Memory at df005000 (32-bit, non-prefetchable) [size=2K]
	Region 1: Memory at df000000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: [44] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME+

00:0a.0 Ethernet controller [0200]: Datacube, Inc Unknown device [1117:0985] (rev 11) (prog-if 02)
	Subsystem: ADMtek Unknown device [1317:0570]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B+
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR+
	Latency: 34 (16000ns min, 32000ns max), Cache Line Size: 32 bytes
	Interrupt: pin C routed to IRQ 18
	Region 0: I/O ports at 9000 [size=256]
	Region 1: Memory at df004000 (32-bit, non-prefetchable) [size=1K]
	Region 2: Memory at <ignored> (32-bit, non-prefetchable)
	Region 3: Memory at <ignored> (32-bit, non-prefetchable)
	Region 4: Memory at <ignored> (32-bit, non-prefetchable)
	Region 5: Memory at <ignored> (32-bit, non-prefetchable)
	[virtual] Expansion ROM at 20000000 [disabled] [size=128K]
	Capabilities: [c0] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=100mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
		Status: D0 PME-Enable+ DSel=0 DScale=0 PME-

00:0f.0 RAID bus controller [0104]: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller [1106:3149] (rev 80)
	Subsystem: Elitegroup Computer Systems Unknown device [1019:1899]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 32
	Interrupt: pin B routed to IRQ 20
	Region 0: I/O ports at 9400 [size=8]
	Region 1: I/O ports at 9800 [size=4]
	Region 2: I/O ports at 9c00 [size=8]
	Region 3: I/O ports at a000 [size=4]
	Region 4: I/O ports at a400 [size=16]
	Region 5: I/O ports at a800 [size=256]
	Capabilities: [c0] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-

00:0f.1 IDE interface [0101]: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE [1106:0571] (rev 06) (prog-if 8a [Master SecP PriP])
	Subsystem: Elitegroup Computer Systems Unknown device [1019:1899]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 32
	Interrupt: pin A routed to IRQ 20
	Region 0: [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [size=8]
	Region 1: [virtual] Memory at 000003f0 (type 3, non-prefetchable) [size=1]
	Region 2: [virtual] Memory at 00000170 (32-bit, non-prefetchable) [size=8]
	Region 3: [virtual] Memory at 00000370 (type 3, non-prefetchable) [size=1]
	Region 4: I/O ports at ac00 [size=16]
	Capabilities: [c0] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-

00:10.0 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 81) (prog-if 00 [UHCI])
	Subsystem: Elitegroup Computer Systems Unknown device [1019:1899]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 32, Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 21
	Region 4: I/O ports at b000 [size=32]
	Capabilities: [80] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=375mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-

00:10.1 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 81) (prog-if 00 [UHCI])
	Subsystem: Elitegroup Computer Systems Unknown device [1019:1899]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 32, Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 21
	Region 4: I/O ports at b400 [size=32]
	Capabilities: [80] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=375mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-

00:10.2 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 81) (prog-if 00 [UHCI])
	Subsystem: Elitegroup Computer Systems Unknown device [1019:1899]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 32, Cache Line Size: 32 bytes
	Interrupt: pin B routed to IRQ 21
	Region 4: I/O ports at b800 [size=32]
	Capabilities: [80] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=375mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-

00:10.3 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 81) (prog-if 00 [UHCI])
	Subsystem: Elitegroup Computer Systems Unknown device [1019:1899]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 32, Cache Line Size: 32 bytes
	Interrupt: pin B routed to IRQ 21
	Region 4: I/O ports at bc00 [size=32]
	Capabilities: [80] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=375mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-

00:10.4 USB Controller [0c03]: VIA Technologies, Inc. USB 2.0 [1106:3104] (rev 86) (prog-if 20 [EHCI])
	Subsystem: Elitegroup Computer Systems Unknown device [1019:1899]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 32, Cache Line Size: 128 bytes
	Interrupt: pin C routed to IRQ 21
	Region 0: Memory at df006000 (32-bit, non-prefetchable) [size=256]
	Capabilities: [80] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=375mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-

00:11.0 ISA bridge [0601]: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South] [1106:3227]
	Subsystem: Elitegroup Computer Systems Unknown device [1019:1899]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping+ SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0
	Capabilities: [c0] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-

00:11.5 Multimedia audio controller [0401]: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller [1106:3059] (rev 60)
	Subsystem: Elitegroup Computer Systems Unknown device [1019:1899]
	Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Interrupt: pin C routed to IRQ 22
	Region 0: I/O ports at c000 [size=256]
	Capabilities: [c0] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-

00:12.0 Ethernet controller [0200]: VIA Technologies, Inc. VT6102 [Rhine-II] [1106:3065] (rev 78)
	Subsystem: VIA Technologies, Inc. VT6102 [Rhine II] Embeded Ethernet Controller on VT8235 [1106:0102]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 32 (750ns min, 2000ns max), Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 23
	Region 0: I/O ports at c800 [size=256]
	Region 1: Memory at df007000 (32-bit, non-prefetchable) [size=256]
	Capabilities: [40] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-

01:00.0 VGA compatible controller [0300]: VIA Technologies, Inc. S3 Unichrome Pro VGA Adapter [1106:3118] (rev 02) (prog-if 00 [VGA controller])
	Subsystem: VIA Technologies, Inc. S3 Unichrome Pro VGA Adapter [1106:3118]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 32 (500ns min)
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at d8000000 (32-bit, prefetchable) [size=64M]
	Region 1: Memory at dc000000 (32-bit, non-prefetchable) [size=16M]
	[virtual] Expansion ROM at dd000000 [disabled] [size=64K]
	Capabilities: [60] Power Management version 2
		Flags: PMEClk- DSI+ D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [70] AGP version 2.0
		Status: RQ=32 Iso- ArqSz=0 Cal=0 SBA+ ITACoh- GART64- HTrans- 64bit- FW- AGP3- Rate=x1,x2,x4
		Command: RQ=32 ArqSz=0 Cal=0 SBA+ AGP+ GART64- 64bit- FW- Rate=x4


############## dmesg | eth1

[   53.305450] udev: renamed network interface eth0 to eth1
[   65.495645] eth1: link down
[  108.683018] ADDRCONF(NETDEV_UP): eth1: link is not ready


############### route

dmesg | grep eth1
[   53.305450] udev: renamed network interface eth0 to eth1
[   65.495645] eth1: link down
[  108.683018] ADDRCONF(NETDEV_UP): eth1: link is not ready


############### ethtool -i eth1

driver: via-rhine
version: 1.4.3
firmware-version: 
bus-info: 0000:00:12.0


############### /etc/network/interfaces

auto lo
iface lo inet loopback

iface eth0 inet dhcp

auto eth0
```

If there is anyhting else you need, please let me know. 

Thanks in advance for your help!  I know there are a lot of posts out there regarding this issue, but I could not find one matching this issue.

---

### Post by pytheas22 on 2008-08-22
Please try running these commands:
```

sudo rmmod via-rhine
sudo modprobe via-rhine
sudo ifconfig eth0 up
sudo ifconfig eth1 up
sudo dhclient eth0
sudo dhclient eth1
```

Does that get you an IP address?

There are also some weird issues with some cards resulting from the way that Windows powers them down.  Are you on a dual-boot machine?  If so, try shutting down Windows completely (shutdown, not restart, not hibernate).  Then boot to Ubuntu and see if it works.  You might also want to try shutting down the machine, unplugging the power (and battery if it's a laptop) for a few minutes, then try.  Finally, try restarting your router/modem to see if it makes a difference.  In some cases these things help.

If none of the above is useful, please post the output of:
```

lshw -C Network
ifconfig
dmesg | grep -e via -e eth0 -e eth1
```

so that we can look into other things.

---

### Post by ooolongT on 2008-08-23
> **pytheas22 said:**
> Please try running these commands:
```

sudo rmmod via-rhine
sudo modprobe via-rhine
sudo ifconfig eth0 up
sudo ifconfig eth1 up
sudo dhclient eth0
sudo dhclient eth1
```

Does that get you an IP address?


Looks like that did the trick to get me an IP address:
```

tj@tj-desktop:~$ ifconfig -a
eth1      Link encap:Ethernet  HWaddr 00:11:5b:2b:76:22  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:23 Base address:0x2000 

eth1:avahi Link encap:Ethernet  HWaddr 00:11:5b:2b:76:22  
          inet addr:169.254.3.203  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:23 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2270 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2270 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:113500 (110.8 KB)  TX bytes:113500 (110.8 KB)

```
But no internet access.


I am on a dual-boot machine, so I tried this:
> 
Are you on a dual-boot machine?  If so, try shutting down Windows completely (shutdown, not restart, not hibernate).  Then boot to Ubuntu and see if it works.  

No luck. 
 

So then I did this:
> 
You might also want to try shutting down the machine, unplugging the power (and battery if it's a laptop) for a few minutes, then try.  

Still no luck.


I persisted:
> 
Finally, try restarting your router/modem to see if it makes a difference.  In some cases these things help.

That didnt work either.


So, here is the oupput of: lshw -C Network, ifconfig, and dmesg | grep -e via -e eth0 -e eth1
```

##########lshw -C Network

WARNING: you should run this program as super-user.
  *-network:0 UNCLAIMED   
       description: Ethernet controller
       product: Datacube, Inc
       vendor: Datacube, Inc
       physical id: a
       bus info: pci@0000:00:0a.0
       version: 11
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=32 maxlatency=128 mingnt=64
  *-network:1
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth1
       version: 78
       serial: 00:11:5b:2b:76:22
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=via-rhine driverversion=1.4.3 latency=32 maxlatency=8 mingnt=3 module=via_rhine multicast=yes

##########ifconfig -a -v

eth1      Link encap:Ethernet  HWaddr 00:11:5b:2b:76:22  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:23 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2166 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2166 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:108300 (105.7 KB)  TX bytes:108300 (105.7 KB)

########## dmesg | grep -e via -e eth0 -e eth01

[   34.813581] via-rhine.c:v1.10-LK1.4.3 2007-03-06 Written by Donald Becker
[   34.813591] via-rhine: Broken BIOS detected, avoid_D3 enabled.
[   35.385365] sata_via 0000:00:0f.0: version 2.3
[   35.385433] sata_via 0000:00:0f.0: routed to hard irq line 11
[   35.386912] scsi0 : sata_via
[   35.388116] scsi1 : sata_via
[   35.814492] pata_via 0000:00:0f.1: version 0.3.3
[   35.816418] scsi2 : pata_via
[   35.816929] scsi3 : pata_via
[   36.917384] eth0: VIA Rhine II at 0xdf007000, 00:11:5b:2b:76:22, IRQ 23.
[   36.918099] eth0: MII PHY found at address 1, status 0x7849 advertising 05e1 Link 0000.
[   55.460196] udev: renamed network interface eth0 to eth1
[   70.767426] [drm] Initialized via 2.11.1 20070202 on minor 0

```

Interstingly, the first set of commands you gave me seemed to have worked - I got the IP, but after restarting the machine, the IP went away. 

Thanks for all the help!

---

### Post by pytheas22 on 2008-08-24
Thanks for all the information.

Unfortunately, even though you got an IP using that first set of commands, I don't think they're really helping.  The IP that you got, [169.254.X.X]("http://ask-leo.com/why_cant_i_connect_with_a_169254xx_ip_address.html"), is a bogus address that won't really get you online.

I'm still not positive what's going on, but I found this [bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/48263") that I think may be related to your issue, as it deals with the same driver (via-rhine).  The posters there suggest that adding "irqpoll" to your kernel options at boot resolves the issue.  To try doing that, open up your grub menu:
```

sudo gedit /boot/grub/menu.lst
```

Scroll down towards the bottom and look for a section similar to:
```

title          Ubuntu 8.04.1, kernel 2.6.24-19-generic
root           (hd0,5)
kernel         /boot/vmlinuz-2.6.24-16-generic root=UUID=8k4o3ilj-3fff-dfae-943j-4332lkj52kl43 ro quiet splash
initrd         /boot/initrd.img-2.6.24-16-generic
```

Edit that section so that it looks like this (see "irqpoll" in bold):

```
title          Ubuntu 8.04.1, kernel 2.6.24-19-generic
root           (hd0,5)
kernel         /boot/vmlinuz-2.6.24-16-generic root=UUID=8k4o3ilj-3fff-dfae-943j-4332lkj52kl43 ro quiet splash **irqpoll**
initrd         /boot/initrd.img-2.6.24-16-generic
```

There may be multiple sections in your grub menu file that look like that, each one for a different kernel.  If there's more than one, make sure to add the "irqpoll" option to the entry that you actually use to boot (probably the top one), or just add it to all of them.

Be sure to save the grub file, then reboot.  Please let me know if it makes a difference.

---

### Post by ooolongT on 2008-08-25
Ok, I tried **irqpoll** to menu.lst and that did not work either. 

I am going to take a closer look at that bug report to see if there is anything I can glean from it.  I did figure out what my motherboard is, and have looked on its website [here.]("http://www.ecs.com.tw/ECSWebSite/Downloads/ProductsDetail_Download.aspx?detailid=453&DetailName=Driver&DetailDesc=PM800-M2(V1.0)&CategoryID=1&MenuID=74&LanID=8") 
and found nothing but Windows drivers.  Troubling.  However, I know that I can use the internet on this computer under Ubuntu because it was working when it first booted after the install.  It worked all day.  I didn't do anyhting to the install other than adding a theme and moving some of the panel icons around.  Very strange.

That bug indicates there is a mobo blacklist somewhere, does anyone know where can I find that?  

If you have any more suggestions, I am willing to try whatever it takes, I did try using a Realtek 8169 NIC but that did not seem to work either (I know Ubuntu has had problems with Realtek cards in the past, but I thought those had all been resolved).  I can go into Windows and try to upgrade the BIOS if that would help, any ideas?

---

### Post by pytheas22 on 2008-08-25
Sorry that irqpoll didn't help.

I did do a bit more googling and have a few more suggestions.  Take a look at [this thread]("http://ubuntuforums.org/showthread.php?t=522260") and [this thread]("http://ubuntuforums.org/showthread.php?t=142606")--they also deal with the same ethernet chipset as yours and describe what appears to be the same problem--the card is recognized by the system, but won't get an IP.

The first thread says that adding the **acpi=noirq** option to your kernel line solves the problem.  You would do that in the same way that you added the irqpoll option--open up your /boot/grub/menu.list file and add **acpi=noirq** to the "kernel" line for each boot entry.

The second thread says that switching to 10FD instead of 100FD fixes the issue.  Unfortunately the poster didn't say how he or she switched, but I'd imagine that you can do it through BIOS, or possibly from Windows--look for an option to configure the speed at which your ethernet card operates.

Finally, you may want to change your /etc/network/interfaces file so that it contains only:

```
auto lo
iface lo inet loopback

```

The other lines shouldn't be necessary and could potentially be interfering with something.

There is some strange stuff going on with your system--it's weird that your ethernet interface gets renamed to eth1; usually it would be eth0.  Also, do you have two ethernet interfaces in this machine?  Because lshw mentions one unclaimed card made by Datacube (I googled and couldn't find anything about it).

The r8169 chipset should have worked, as well.  There are still a few issues that affect a handful of Realtek 8169 cards (one of the most ubiquitous models), but most should "just work."  Mine certainly does.  If you really can't get the onboard LAN working and you want to troubleshoot your Realtek card (I assume it's PCI), plug it in and post the output of:
```

lshw -C Network
ifconfig
ifconfig -a
lspci -nn | grep -i realtek
```

But hopefully you'll get the onboard card working.

---

### Post by ooolongT on 2008-08-25
I tried adding the **acpi=noirq** option to the kernel lines but that did not work.  

I will see if i can dig up some more info about the 10FD/100FD switching and let you know what I learn.

I also tried changing /etc/network/interfaces file so that it contains only:

```
auto lo
iface lo inet loopback

```

and that did not work either, but I have left it with the reduced information. 

Here is some more info:

1. I have unplugged the Network Everywhere card which was what was giving me the "Datacube" entry in the lshw list.

2. I tried assigning static IPs that should (and do) work on Windows, that didn't work, so I have set it back to Roaming

3. I added the network monitor to the top panel, and it has given me this message: "Could not find information on interface 'eth1:avahi' in proc/net/dev".  I went into network tools and looked at what is there and there is no eth0 there, there is a eth1, and now a "eth1:avhi"

4. I will reset everything and fool around with the Realtek card to see if I can get that working

5. I ran dmesg | grep -e via -e eth0 -e eth1 again, and it has changed, so I am including that info below, weirdness in bold:
```

[   24.676390] via-rhine.c:v1.10-LK1.4.3 2007-03-06 Written by Donald Becker
**[   24.676460] via-rhine: Broken BIOS detected, avoid_D3 enabled.**
[   25.255700] sata_via 0000:00:0f.0: version 2.3
[   25.256338] sata_via 0000:00:0f.0: routed to hard irq line 11
[   25.257641] scsi0 : sata_via
[   25.258914] scsi1 : sata_via
[   25.681691] pata_via 0000:00:0f.1: version 0.3.3
[   25.683793] scsi2 : pata_via
[   25.683953] scsi3 : pata_via
[   26.804459] eth0: VIA Rhine II at 0xde006000, 00:11:5b:2b:76:22, IRQ 19.
[   26.805234] eth0: MII PHY found at address 1, status 0x786d advertising 05e1 Link 41e1.
**[   45.679694] udev: renamed network interface eth0 to eth1**
[  109.059677] eth1: link up, 100Mbps, full-duplex, lpa 0x41E1
[  112.318710] [drm] Initialized via 2.11.1 20070202 on minor 0
**[  139.682642] eth1: no IPv6 routers present**

```

Thanks again for all your help with this!

---

### Post by ooolongT on 2008-08-25
I tried changing the BIOS, but could not find a pace to change FD10 to FD100.

I don't want to muddy the waters here, but I tried the Realtek card, and I am getting similar messages, and it is still renaming things from eth0 to ethx.

Here is the output you requested:
```

##########sudo lshw -C Network
  *-network:0             
       description: Ethernet interface
       product: RTL-8169 Gigabit Ethernet
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 8
       bus info: pci@0000:00:08.0
       logical name: eth2
       version: 10
       serial: 00:40:f4:cf:06:58
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=full latency=64 link=yes maxlatency=64 mingnt=32 module=r8169 multicast=yes port=twisted pair speed=100MB/s
  *-network:1
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth1
       version: 78
       serial: 00:11:5b:2b:76:22
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=half latency=32 link=no maxlatency=8 mingnt=3 module=via_rhine multicast=yes port=MII speed=10MB/s


##########ifconfig
eth1      Link encap:Ethernet  HWaddr 00:11:5b:2b:76:22  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:39 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:5283 (5.1 KB)
          Interrupt:20 

eth2      Link encap:Ethernet  HWaddr 00:40:f4:cf:06:58  
          inet6 addr: fe80::240:f4ff:fecf:658/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:650 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:54745 (53.4 KB)
          Interrupt:16 Base address:0xa000 

eth1:avahi Link encap:Ethernet  HWaddr 00:11:5b:2b:76:22  
          inet addr:169.254.3.203  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:20 

eth2:avahi Link encap:Ethernet  HWaddr 00:40:f4:cf:06:58  
          inet addr:169.254.6.102  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:16 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3549 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3549 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:194482 (189.9 KB)  TX bytes:194482 (189.9 KB)


##########ifconfig -a
eth1      Link encap:Ethernet  HWaddr 00:11:5b:2b:76:22  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:39 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:5283 (5.1 KB)
          Interrupt:20 

eth2      Link encap:Ethernet  HWaddr 00:40:f4:cf:06:58  
          inet6 addr: fe80::240:f4ff:fecf:658/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:653 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:55771 (54.4 KB)
          Interrupt:16 Base address:0xa000 

eth1:avahi Link encap:Ethernet  HWaddr 00:11:5b:2b:76:22  
          inet addr:169.254.3.203  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:20 

eth2:avahi Link encap:Ethernet  HWaddr 00:40:f4:cf:06:58  
          inet addr:169.254.6.102  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:16 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3549 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3549 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:194482 (189.9 KB)  TX bytes:194482 (189.9 KB)


##########lspci -nn | grep -i realtek
00:08.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet [10ec:8169] (rev 10)


##########dmesg | grep -e Realtek -e realtek -e eth0 -e eth1 -e eth2
[   26.230405] eth0: RTL8110s at 0xdc83a000, 00:40:f4:cf:06:58, XID 04000000 IRQ 16
[   28.605153] eth1: VIA Rhine II at 0xdf007000, 00:11:5b:2b:76:22, IRQ 20.
[   28.605877] eth1: MII PHY found at address 1, status 0x786d advertising 01e1 Link 41e1.
[   44.954192] udev: renamed network interface eth0 to eth2
[   57.617413] eth1: link up, 100Mbps, full-duplex, lpa 0x41E1
[   57.645886] r8169: eth2: link down
[   77.516258] ADDRCONF(NETDEV_UP): eth2: link is not ready
[   88.128365] eth1: no IPv6 routers present
[  113.376352] eth1: link down
[  119.402329] r8169: eth2: link up
[  119.402551] ADDRCONF(NETDEV_CHANGE): eth2: link becomes ready
[  130.083146] eth2: no IPv6 routers present

```

---

### Post by pytheas22 on 2008-08-25
The Realtek card seems to be doing some screwy stuff as well, so I'm wondering if the problem may not lie with the interfaces themselves as much as with the system networking installation.  The fact that static IP fails as well supports that conclusion.

I don't know how much you already have invested in your Ubuntu installation, but if it's not too much, you may want to try just doing a fresh install of the whole system.  Make sure both the VIA and Realtek cards are plugged in and activated during the installation, and keep the DataCube thing unplugged.  That may do the trick.  If you don't get an IP after a fresh install, please post again:
```

dmesg | grep -e r8169 -e via-rhine -e eth1 -e eth2 -e eth0
lshw -C Network
sudo dhclient eth0
sudo dhclient eth1
sudo dhclient eth2
```

If you do have a lot invested in your existing Ubuntu system and don't want to reinstall, that's alright; there are still other things we can try.  But at this point I'm thinking that it would make the most sense to spend an hour reinstalling the system to try to get back to a clean slate, because there a number of strange things going on with your networking.

---

### Post by ooolongT on 2008-08-26
Ok.  Another new install.  But this time, I decided to do some cross referencing with Windows, using all three ethernet  adapters: The Via-Rhine, Network Everywhere, Realtek8169/ 8110.  So I reinstalled ubuntu, and tried out all three methods of connecting.  None worked.  

I switched to windows, and only one worked - the Network Everywhere card.  So I plugged all three in and looked at the settings for each one.  The only thing substantially different was the 10BaseTX Full Duplex setting on that card, as opposed to the 100Base settings on the other two. 

This is that dang FD10/ FD100 setting you mentioned in your earlier post Pytheas!  So I changed it in Windows for the Via-Rhine controller, and the Realtek card, in Windows, then booted into Ubuntu, and viola!  

Whew.  

Here it is not working on ubuntu:
```

########## sudo lshw -C Network
[sudo] password for tj: 
  *-network               
       description: Ethernet interface
       product: ***VT6102 [Rhine-II]***
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth1
       version: 78
       serial: 00:11:5b:2b:76:22
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd ***autonegotiation***
       configuration: ***autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=full latency=32 link=yes maxlatency=8 mingnt=3 module=via_rhine multicast=yes port=MII speed=100MB/s***

########## ifconfig
eth1      Link encap:Ethernet  HWaddr 00:11:5b:2b:76:22  
          inet6 addr: fe80::211:5bff:fe2b:7622/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:42 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:6145 (6.0 KB)
          Interrupt:19 Base address:0xe000 

eth1:avahi Link encap:Ethernet  HWaddr 00:11:5b:2b:76:22  
          inet addr:169.254.3.203  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:19 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2494 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2494 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:126596 (123.6 KB)  TX bytes:126596 (123.6 KB)

########## ifconfig -a
eth1      Link encap:Ethernet  HWaddr 00:11:5b:2b:76:22  
          inet6 addr: fe80::211:5bff:fe2b:7622/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:42 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:6145 (6.0 KB)
          Interrupt:19 Base address:0xe000 

eth1:avahi Link encap:Ethernet  HWaddr 00:11:5b:2b:76:22  
          inet addr:169.254.3.203  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:19 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2494 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2494 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:126596 (123.6 KB)  TX bytes:126596 (123.6 KB)

########## lspci -nn | grep -i via
00:00.0 Host bridge [0600]: VIA Technologies, Inc. CN400/PM880 Host Bridge [1106:0259]
00:00.1 Host bridge [0600]: VIA Technologies, Inc. CN400/PM880 Host Bridge [1106:1259]
00:00.2 Host bridge [0600]: VIA Technologies, Inc. CN400/PM880 Host Bridge [1106:2259]
00:00.3 Host bridge [0600]: VIA Technologies, Inc. CN400/PM880 Host Bridge [1106:3259]
00:00.4 Host bridge [0600]: VIA Technologies, Inc. CN400/PM880 Host Bridge [1106:4259]
00:00.7 Host bridge [0600]: VIA Technologies, Inc. CN400/PM880 Host Bridge [1106:7259]
00:01.0 PCI bridge [0604]: VIA Technologies, Inc. VT8237 PCI Bridge [1106:b198]
00:0f.0 RAID bus controller [0104]: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller [1106:3149] (rev 80)
00:0f.1 IDE interface [0101]: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE [1106:0571] (rev 06)
00:10.0 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 81)
00:10.1 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 81)
00:10.2 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 81)
00:10.3 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 81)
00:10.4 USB Controller [0c03]: VIA Technologies, Inc. USB 2.0 [1106:3104] (rev 86)
00:11.0 ISA bridge [0601]: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South] [1106:3227]
00:11.5 Multimedia audio controller [0401]: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller [1106:3059] (rev 60)
00:12.0 Ethernet controller [0200]: VIA Technologies, Inc. VT6102 [Rhine-II] [1106:3065] (rev 78)
01:00.0 VGA compatible controller [0300]: VIA Technologies, Inc. S3 Unichrome Pro VGA Adapter [1106:3118] (rev 02)

########### dmesg | grep -e via-rhine -e eth0 -e eth1
[   30.033319] via-rhine.c:v1.10-LK1.4.3 2007-03-06 Written by Donald Becker
[   30.033328] via-rhine: Broken BIOS detected, avoid_D3 enabled.
[   32.159926] eth0: VIA Rhine II at 0xde006000, 00:11:5b:2b:76:22, IRQ 19.
[   32.160640] eth0: MII PHY found at address 1, status 0x7869 advertising 01e1 Link 41e1.
[   48.793078] udev: renamed network interface eth0 to eth1
[   58.099283] ***eth1: link up, 100Mbps, full-duplex, lpa 0x41E1***
[  115.751111] eth1: no IPv6 routers present

```


And here it is working:
```

########## sudo lshw -C Network
  *-network:0             
       description: Ethernet interface
       product: NC100 Network Everywhere Fast Ethernet 10/100
       vendor: ADMtek
       physical id: 8
       bus info: pci@0000:00:08.0
       logical name: eth0
       version: 11
       serial: 00:04:5a:8a:f4:55
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tulip driverversion=1.1.15 latency=32 maxlatency=128 mingnt=64 module=tulip multicast=yes
  *-network:1
       description: Ethernet interface
       product: ***VT6102 [Rhine-II]***
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth1
       version: 78
       serial: 00:11:5b:2b:76:22
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: ***autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=half ip=192.168.123.103 latency=32 link=yes maxlatency=8 mingnt=3 module=via_rhine multicast=yes port=MII speed=10MB/s***

########## ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:04:5a:8a:f4:55  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 Base address:0x9000 

eth1      Link encap:Ethernet  HWaddr 00:11:5b:2b:76:22  
          inet addr:192.168.123.103  Bcast:192.168.123.255  Mask:255.255.255.0
          inet6 addr: fe80::211:5bff:fe2b:7622/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:24577 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16459 errors:16 dropped:0 overruns:0 carrier:16
          collisions:6669 txqueuelen:1000 
          RX bytes:26891721 (25.6 MB)  TX bytes:2069193 (1.9 MB)
          Interrupt:20 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1100 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1100 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:55000 (53.7 KB)  TX bytes:55000 (53.7 KB)

########### lspci -nn | grep -i via
00:00.0 Host bridge [0600]: VIA Technologies, Inc. CN400/PM880 Host Bridge [1106:0259]
00:00.1 Host bridge [0600]: VIA Technologies, Inc. CN400/PM880 Host Bridge [1106:1259]
00:00.2 Host bridge [0600]: VIA Technologies, Inc. CN400/PM880 Host Bridge [1106:2259]
00:00.3 Host bridge [0600]: VIA Technologies, Inc. CN400/PM880 Host Bridge [1106:3259]
00:00.4 Host bridge [0600]: VIA Technologies, Inc. CN400/PM880 Host Bridge [1106:4259]
00:00.7 Host bridge [0600]: VIA Technologies, Inc. CN400/PM880 Host Bridge [1106:7259]
00:01.0 PCI bridge [0604]: VIA Technologies, Inc. VT8237 PCI Bridge [1106:b198]
00:0f.0 RAID bus controller [0104]: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller [1106:3149] (rev 80)
00:0f.1 IDE interface [0101]: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE [1106:0571] (rev 06)
00:10.0 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 81)
00:10.1 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 81)
00:10.2 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 81)
00:10.3 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 81)
00:10.4 USB Controller [0c03]: VIA Technologies, Inc. USB 2.0 [1106:3104] (rev 86)
00:11.0 ISA bridge [0601]: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South] [1106:3227]
00:11.5 Multimedia audio controller [0401]: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller [1106:3059] (rev 60)
00:11.6 Communication controller [0780]: VIA Technologies, Inc. AC'97 Modem Controller [1106:3068] (rev 80)
00:12.0 Ethernet controller [0200]: VIA Technologies, Inc. VT6102 [Rhine-II] [1106:3065] (rev 78)
01:00.0 VGA compatible controller [0300]: VIA Technologies, Inc. S3 Unichrome Pro VGA Adapter [1106:3118] (rev 02)

########## dmesg | grep -e via-rhine -e eth0 -e eth1
[   20.750396] eth0: ADMtek Comet rev 17 at Port 0x9000, 00:04:5a:8a:f4:55, IRQ 16.
[   21.007368] via-rhine.c:v1.10-LK1.4.3 2007-03-06 Written by Donald Becker
[   21.007438] via-rhine: Broken BIOS detected, avoid_D3 enabled.
[   23.149766] eth1: VIA Rhine II at 0xdf007000, 00:11:5b:2b:76:22, IRQ 20.
[   23.150536] eth1: MII PHY found at address 1, status 0x786d advertising 0021 Link 41e1.
[ 2120.642532] ***eth1: link up, 10Mbps, half-duplex, lpa 0x41E1***
[ 2125.600848] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 2136.010652] eth1: no IPv6 routers present

```

So, the trick is to make sure I am at 10Mbps, half-duplex!

I have not tried to do this yet, but there are threads that discuss doing exactly this [here]("http://ubuntuforums.org/showthread.php?t=143982") and [here]("http://ubuntuforums.org/showthread.php?t=858137&highlight=half-duplex").

---

### Post by mcarlson on 2008-10-19
For those like me who found themselves asking the same question "so how do you change to half duplex and 10mp/sec???"  Here is what I found:

[http://www.cyberciti.biz/faq/howto-setup-linux-lan-card-find-out-full-duplex-half-speed-or-mode/]("http://www.cyberciti.biz/faq/howto-setup-linux-lan-card-find-out-full-duplex-half-speed-or-mode/")

```
mii-tool -F 10baseT-HD
```

Hope that helps

M@

---

