---
title: "Ubuntu wireless woes."
date: 2007-05-08
forum: Networking &amp; Wireless
---

### Post by rules on 2007-05-08
Hi all

I have been trying for a while now to get away from Windows, atleast on my personal machines. Unfortuanitly majority of the software I use is Windows based. 
I got real excited when a family member told me about Ubuntu and how they are using it at work and getting it to run Windows appz. Next step was for me to wipe Suse 10.2, which I have been running for a while without any major problems, to load Fiesty Fawn. 
From the get go I loved it. The way it looks, the ease of use, everything is only a couple of clicks away. 
My dilema is this though, what good is this software if it can't even run something as simple, yet important, thing as a wireless card. Fair enough, even with Suse I had to do the Ndiswrapper trick but its quick and easy. With Ubuntu its a whole mission with downloading all kinds of software and all kinds of funny tricks only to end up days later with a wireless card that still does not work.

Sorry for the long post, just need to vent a little.

Cheers

---

### Post by mthakur2006 on 2007-05-08
what wireless card have you got? if you tell us then, we might be able to help. Also, could you post us the result of ```
 lspci -vv 
``` and ```
 iwconfig 
```
thanks

---

### Post by rules on 2007-05-09
Hi

I will have to check those setting later, but I have one of those ipn2220 built-in goodies.

Thanks.

---

### Post by rules on 2007-05-09
_**lspci -vv**_


 lspci -vv
00:00.0 Host bridge: ATI Technologies Inc Radeon 9100 IGP Host Bridge (rev 02)
        Subsystem: Acer Incorporated [ALI] Unknown device 0065
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64
        Region 0: Memory at ea000000 (32-bit, prefetchable) [size=32M]
        Region 1: Memory at e8000000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [a0] AGP version 3.0
                Status: RQ=32 Iso- ArqSz=0 Cal=0 SBA+ ITACoh- GART64- HTrans- 64bit- FW+ AGP3+ Rate=x4,x8
                Command: RQ=1 ArqSz=0 Cal=0 SBA+ AGP+ GART64- 64bit- FW- Rate=x4

00:01.0 PCI bridge: ATI Technologies Inc Radeon 9100 IGP AGP Bridge (prog-if 00 [Normal decode])
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 99
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=68
        I/O behind bridge: 00009000-00009fff
        Memory behind bridge: e8100000-e81fffff
        Prefetchable memory behind bridge: f0000000-f7ffffff
        Secondary status: 66MHz+ FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
        BridgeCtl: Parity- SERR- NoISA+ VGA+ MAbort- >Reset- FastB2B-

00:13.0 USB Controller: ATI Technologies Inc OHCI USB Controller #1 (rev 01) (prog-if 10 [OHCI])
        Subsystem: Acer Incorporated [ALI] Unknown device 0065
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64, Cache Line Size: 128 bytes
        Interrupt: pin A routed to IRQ 18
        Region 0: Memory at e8001000 (32-bit, non-prefetchable) [size=4K]

00:13.1 USB Controller: ATI Technologies Inc OHCI USB Controller #2 (rev 01) (prog-if 10 [OHCI])
        Subsystem: Acer Incorporated [ALI] Unknown device 0065
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64, Cache Line Size: 128 bytes
        Interrupt: pin A routed to IRQ 18
        Region 0: Memory at e8002000 (32-bit, non-prefetchable) [size=4K]

00:13.2 USB Controller: ATI Technologies Inc EHCI USB Controller (rev 01) (prog-if 20 [EHCI])
        Subsystem: Acer Incorporated [ALI] Unknown device 0065
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64, Cache Line Size: 128 bytes
        Interrupt: pin A routed to IRQ 18
        Region 0: Memory at e8003000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [dc] Power Management version 2
                Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-
                Bridge: PM- B3+

00:14.0 SMBus: ATI Technologies Inc ATI SMBus (rev 1a)
        Subsystem: Acer Incorporated [ALI] Unknown device 0065
        Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Region 0: I/O ports at 8060 [size=16]
        Region 1: Memory at e8004000 (32-bit, non-prefetchable) [size=1K]

00:14.1 IDE interface: ATI Technologies Inc ATI Dual Channel Bus Master PCI IDE Controller (prog-if 8a [Master SecP PriP])
        Subsystem: Acer Incorporated [ALI] Unknown device 0065
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort+ <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64
        Interrupt: pin A routed to IRQ 16
        Region 0: I/O ports at 01f0 [size=8]
        Region 1: I/O ports at 03f4 [size=1]
        Region 2: I/O ports at 0170 [size=8]
        Region 3: I/O ports at 0374 [size=1]
        Region 4: I/O ports at 8070 [size=16]

00:14.3 ISA bridge: ATI Technologies Inc Unknown device 434c
        Subsystem: Acer Incorporated [ALI] Unknown device 0065
        Control: I/O+ Mem+ BusMaster+ SpecCycle+ MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0

00:14.4 PCI bridge: ATI Technologies Inc Unknown device 4342 (prog-if 01 [Subtractive decode])
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64
        Bus: primary=00, secondary=02, subordinate=04, sec-latency=68
        I/O behind bridge: 0000a000-0000afff
        Memory behind bridge: e8200000-e82fffff
        Prefetchable memory behind bridge: 40000000-43ffffff
        Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
        BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-

00:14.5 Multimedia audio controller: ATI Technologies Inc IXP150 AC'97 Audio Controller (rev 01)
        Subsystem: Acer Incorporated [ALI] Unknown device 0065
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=slow >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64 (500ns min), Cache Line Size: 32 bytes
        Interrupt: pin B routed to IRQ 17
        Region 0: Memory at e8004400 (32-bit, non-prefetchable) [size=256]

00:14.6 Modem: ATI Technologies Inc IXP AC'97 Modem (rev 01) (prog-if 00 [Generic])
        Subsystem: Acer Incorporated [ALI] Unknown device 0065
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=slow >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64 (500ns min), Cache Line Size: 32 bytes
        Interrupt: pin B routed to IRQ 17
        Region 0: Memory at e8004800 (32-bit, non-prefetchable) [size=256]

01:05.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10] (prog-if 00 [VGA])
        Subsystem: Acer Incorporated [ALI] Unknown device 0065
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B+
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 66 (2000ns min), Cache Line Size: 32 bytes
        Interrupt: pin A routed to IRQ 16
        Region 0: Memory at f0000000 (32-bit, prefetchable) [size=128M]
        Region 1: I/O ports at 9000 [size=256]
        Region 2: Memory at e8100000 (32-bit, non-prefetchable) [size=64K]
        [virtual] Expansion ROM at e8120000 [disabled] [size=128K]
        Capabilities: [58] AGP version 3.0
                Status: RQ=256 Iso- ArqSz=0 Cal=0 SBA+ ITACoh- GART64- HTrans- 64bit- FW+ AGP3+ Rate=x4,x8
                Command: RQ=32 ArqSz=0 Cal=0 SBA+ AGP+ GART64- 64bit- FW- Rate=x4
        Capabilities: [50] Power Management version 2
                Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-

02:00.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80) (prog-if 10 [OHCI])
        Subsystem: Acer Incorporated [ALI] Unknown device 0065
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64 (8000ns max), Cache Line Size: 32 bytes
        Interrupt: pin A routed to IRQ 16
        Region 0: Memory at e8200000 (32-bit, non-prefetchable) [size=2K]
        Region 1: I/O ports at a400 [size=128]
        Capabilities: [50] Power Management version 2
                Flags: PMEClk- DSI- D1- D2+ AuxCurrent=0mA PME(D0-,D1-,D2+,D3hot+,D3cold+)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-

02:02.0 Ethernet controller: Linksys, A Division of Cisco Systems [AirConn] INPROCOMM IPN 2220 Wireless LAN Adapter (rev 01)
        Subsystem: AMBIT Microsystem Corp. Unknown device 0305
        Control: I/O+ Mem+ BusMaster+ SpecCycle+ MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64 (8000ns min, 8000ns max)
        Interrupt: pin A routed to IRQ 11
        Region 0: I/O ports at a480 [size=32]
        Region 1: Memory at e8201000 (32-bit, non-prefetchable) [size=32]
        Region 2: Memory at e8200800 (32-bit, non-prefetchable) [size=2K]
        Capabilities: [40] Power Management version 2
                Flags: PMEClk- DSI+ D1- D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-

02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
        Subsystem: Acer Incorporated [ALI] Unknown device 0036
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR+
        Latency: 128 (8000ns min, 16000ns max)
        Interrupt: pin A routed to IRQ 18
        Region 0: I/O ports at a000 [size=256]
        Region 1: Memory at e8201400 (32-bit, non-prefetchable) [size=256]
        Capabilities: [50] Power Management version 2
                Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=375mA PME(D0-,D1+,D2+,D3hot+,D3cold+)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-

02:04.0 CardBus bridge: ENE Technology Inc CB-710/2/4 Cardbus Controller
        Subsystem: Acer Incorporated [ALI] Unknown device 0065
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 168, Cache Line Size: 128 bytes
        Interrupt: pin A routed to IRQ 16
        Region 0: Memory at e8203000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=02, secondary=03, subordinate=03, sec-latency=176
        Memory window 0: 40000000-43fff000 (prefetchable)
        Memory window 1: 44000000-47fff000
        I/O window 0: 0000a800-0000a8ff
        I/O window 1: 0000ac00-0000acff
        BridgeCtl: Parity- SERR- ISA- VGA- MAbort- >Reset+ 16bInt+ PostWrite+
        16-bit legacy interface ports at 0001

02:04.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller
        Subsystem: Acer Incorporated [ALI] Unknown device 0065
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64 (250ns min, 1000ns max), Cache Line Size: 32 bytes
        Interrupt: pin B routed to IRQ 11
        Region 0: Memory at e8201800 (32-bit, non-prefetchable) [size=128]
        Capabilities: [80] Power Management version 2
                Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-

02:04.2 Generic system peripheral [0805]: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (prog-if 01)
        Subsystem: Acer Incorporated [ALI] Unknown device 0065
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64 (8000ns min, 18000ns max), Cache Line Size: 32 bytes
        Interrupt: pin B routed to IRQ 17
        Region 0: Memory at e8201c00 (32-bit, non-prefetchable) [size=256]
        Capabilities: [80] Power Management version 2
                Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-

02:04.3 FLASH memory: ENE Technology Inc FLASH memory: ENE Technology Inc:
        Subsystem: Acer Incorporated [ALI] Unknown device 0065
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64 (250ns min, 1000ns max), Cache Line Size: 32 bytes
        Interrupt: pin B routed to IRQ 11
        Region 0: Memory at e8202000 (32-bit, non-prefetchable) [size=128]
        Capabilities: [80] Power Management version 2
                Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-

---

### Post by rules on 2007-05-09
Well, I don't know what to say ... I'm connected through my wireless connection.
This morning after reading your replies, I wanted to check those settings you guys asked about. Before doing so I realized that I had uninstall ed the card again so thought I would reinstall it before trying to check the settings and for some reason unknown to me, I did exactly as I have done before and hey presto, it started working. The only problem now is that I manually have to go through these steps every time I restart Ubuntu. Is there a way of getting around this?

These are the steps I follow:

ndiswrapper -i /home/rafiq/Desktop/80211bg/Winxp/neti2220.inf
sudo depmod -a
sudo ndiswrapper -m
sudo modprobe ndiswrapper

Thanks. :)

---

### Post by rules on 2007-05-10
Everytime I reboot I have to enter the steps and set up a connection otherwise it doesn't work.

Any ideas welcoms :)

---

### Post by mthakur2006 on 2007-05-10
do u have to repeat every single step or the modprobe bit? If just the modprobe bit,
do this:

```
 sudo gedit /etc/modules 
```
and add
```
 ndiswrapper 
```
at the end of it and save it.
otherwise, u might want to write a script that does these steps, set it as an executable and add it to startup programs. I am no programmer myself, so I am sorry I can't help you there.
thanks, mthakur

---

