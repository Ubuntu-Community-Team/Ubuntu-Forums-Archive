---
title: "Marvell Yukon NIC problem"
date: 2007-02-19
forum: Networking &amp; Wireless
---

### Post by dontjee on 2007-02-19
Hi everyone. I installed Ubuntu 6.10 today, and my ethernet connection cuts out when I try to download a file or if I am online for about 5 minutes. The only thing I can do to make it come back is to reboot or to disable and enable the network adapter. I know the problem isn't the network because I am dual booting, and XP has no problems and I can also use the wireless adapter without problems. I installed Open SUSE 10.2 before Ubuntu and the network card worked fine on SUSE. I like Ubuntu better, and I would like to get my card working. The card is a Marvell Yukon 88E8036 PCI-E Fast Ethernet Controller. I did some searching around on the forum and I found this thread: [http://ubuntuforums.org/showthread.p...=marvell+yukon](http://ubuntuforums.org/showthread.p...=marvell+yukon) which talks about a backported driver for the Marvell Yukon NIC. I would like to try this, but I'm unsure of where to start. Is it as simple as updating ubuntu or do I need to recompile the kernel. Thanks for the help.

---

### Post by chili555 on 2007-02-19
This is from one of the topics regading Yukon:
> Enable your backports repo. For example:

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

You should be able to locate the driver in synaptic after a sudo apt-get update.

Recompiling the kernel is fun, but maybe not today.

---

### Post by dontjee on 2007-02-19
I tried doing that, but I'm not sure where the new driver will be in synaptic. I tried looking for a sky2 or a sk98lin package, but couldn't find one. Sorry for the bad link above, I think this is a working link to the post I was referring to. [http://ubuntuforums.org/showthread.php?t=316545](http://ubuntuforums.org/showthread.php?t=316545) .

---

### Post by chili555 on 2007-02-19
After doing a LOT of research on this, I believe we do not see them in synaptic, is because they are already in your system. Try locate sky2 and locate sk98lin. I think the problem is sk98lin is buggy.

The only post I saw that said, "Fixed, no problem" was this: [http://www.ubuntuforums.org/showthread.php?t=326343](http://www.ubuntuforums.org/showthread.php?t=326343)

Daunting but do-able. Let me know if I can help.

---

### Post by dontjee on 2007-02-19
Ok just a couple of questions before I start. Will this work on a laptop without a dual core processor and to install it do I just download and run the deb files. Thanks for all your help!

---

### Post by chili555 on 2007-02-19
Nope!

I thoght sure, from the problems posted here, and your identical problem, you were a Core 2 Duo on a P965 motherboard guy. Tell us what you DO have, and let us see the output of sudo lspci -vv.

I think a 2.6.19 kernel will fix you up, but it's a scary, but do-able job.

---

### Post by dontjee on 2007-02-19
Hi chili555, I have a pentium M 740 processor, but I'm not sure what motherboard I have. Here is the output of lspci -vv: 
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ >SERR- <PERR-
        Latency: 0
        Capabilities: [e0] Vendor Specific Information

00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03) (prog-if 00 [VGA])
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin A routed to IRQ 11
        Region 0: Memory at d0000000 (32-bit, non-prefetchable) [size=512K]
        Region 1: I/O ports at e000 [size=8]
        Region 2: Memory at a0000000 (32-bit, prefetchable) [size=256M]
        Region 3: Memory at d0080000 (32-bit, non-prefetchable) [size=256K]
        Capabilities: [d0] Power Management version 2
                Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-

00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Region 0: Memory at d0100000 (32-bit, non-prefetchable) [size=512K]
        Capabilities: [d0] Power Management version 2
                Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-

00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04) (prog-if 00 [Normal decode])
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0, Cache Line Size: 16 bytes
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 0000c000-0000dfff
        Memory behind bridge: cc000000-cfffffff
        Prefetchable memory behind bridge: 000000009c000000-000000009ff00000
        Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
        BridgeCtl: Parity- SERR+ NoISA- VGA- MAbort- >Reset- FastB2B-
        Capabilities: [40] Express Root Port (Slot+) IRQ 0
                Device: Supported: MaxPayload 128 bytes, PhantFunc 0, ExtTag+
                Device: Latency L0s unlimited, L1 unlimited
                Device: Errors: Correctable- Non-Fatal- Fatal- Unsupported-
                Device: RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
                Device: MaxPayload 128 bytes, MaxReadReq 128 bytes
                Link: Supported Speed 2.5Gb/s, Width x1, ASPM L0s L1, Port 1
                Link: Latency L0s <1us, L1 <4us
                Link: ASPM Disabled RCB 64 bytes CommClk- ExtSynch-
                Link: Speed 2.5Gb/s, Width x1
                Slot: AtnBtn- PwrCtrl- MRL- AtnInd- PwrInd- HotPlug+ Surpise+
                Slot: Number 2, PowerLimit 6.500000
                Slot: Enabled AtnBtn- PwrFlt- MRL- PresDet+ CmdCplt- HPIrq-
                Slot: AttnInd Unknown, PwrInd Unknown, Power-
                Root: Correctable- Non-Fatal- Fatal- PME-
        Capabilities: [80] Message Signalled Interrupts: 64bit- Queue=0/0 Enable+
                Address: fee00000  Data: 4041
        Capabilities: [90] #0d [0000]
        Capabilities: [a0] Power Management version 2
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-

00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 04) (prog-if 00 [Normal decode])
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0, Cache Line Size: 16 bytes
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        I/O behind bridge: 0000a000-0000bfff
        Memory behind bridge: c8000000-cbffffff
        Prefetchable memory behind bridge: 0000000098000000-000000009bf00000
        Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
        BridgeCtl: Parity- SERR+ NoISA- VGA- MAbort- >Reset- FastB2B-
        Capabilities: [40] Express Root Port (Slot+) IRQ 0
                Device: Supported: MaxPayload 128 bytes, PhantFunc 0, ExtTag+
                Device: Latency L0s unlimited, L1 unlimited
                Device: Errors: Correctable- Non-Fatal- Fatal- Unsupported-
                Device: RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
                Device: MaxPayload 128 bytes, MaxReadReq 128 bytes
                Link: Supported Speed 2.5Gb/s, Width x1, ASPM L0s L1, Port 2
                Link: Latency L0s <1us, L1 <4us
                Link: ASPM Disabled RCB 64 bytes CommClk- ExtSynch-
                Link: Speed 2.5Gb/s, Width x1
                Slot: AtnBtn- PwrCtrl- MRL- AtnInd- PwrInd- HotPlug+ Surpise+
                Slot: Number 3, PowerLimit 6.500000
                Slot: Enabled AtnBtn- PwrFlt- MRL- PresDet+ CmdCplt- HPIrq-
                Slot: AttnInd Unknown, PwrInd Unknown, Power-
                Root: Correctable- Non-Fatal- Fatal- PME-
        Capabilities: [80] Message Signalled Interrupts: 64bit- Queue=0/0 Enable+
                Address: fee00000  Data: 4049
        Capabilities: [90] #0d [0000]
        Capabilities: [a0] Power Management version 2
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-

00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04) (prog-if 00 [UHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin A routed to IRQ 10
        Region 4: I/O ports at 1200 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04) (prog-if 00 [UHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin B routed to IRQ 11
        Region 4: I/O ports at 1220 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04) (prog-if 00 [UHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin C routed to IRQ 11
        Region 4: I/O ports at 1240 [size=32]

00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04) (prog-if 00 [UHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin D routed to IRQ 11
        Region 4: I/O ports at 1260 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04) (prog-if 20 [EHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin A routed to IRQ 10
        Region 0: Memory at f4000000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: [50] Power Management version 2
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=375mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-
        Capabilities: [58] Debug port

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4) (prog-if 01 [Subtractive decode])
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Bus: primary=00, secondary=05, subordinate=09, sec-latency=32
        I/O behind bridge: 00008000-00009fff
        Memory behind bridge: b8000000-c7ffffff
        Prefetchable memory behind bridge: 0000000088000000-0000000097f00000
        Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
        BridgeCtl: Parity- SERR+ NoISA+ VGA- MAbort- >Reset- FastB2B-
        Capabilities: [50] #0d [0000]

00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 04)
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin A routed to IRQ 10
        Region 0: I/O ports at e100 [size=256]
        Region 1: I/O ports at e200 [size=64]
        Region 2: Memory at d0180000 (32-bit, non-prefetchable) [size=512]
        Region 3: Memory at d0180200 (32-bit, non-prefetchable) [size=256]
        Capabilities: [50] Power Management version 2
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=375mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-

00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 04) (prog-if 00 [Generic])
        Subsystem: Toshiba America Info Systems Unknown device 0001
        Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Interrupt: pin B routed to IRQ 5
        Region 0: I/O ports at e300 [size=256]
        Region 1: I/O ports at e400 [size=128]
        Capabilities: [50] Power Management version 2
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=375mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-

00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0

00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 04) (prog-if 80 [Master])
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin B routed to IRQ 11
        Region 0: I/O ports at <unassigned>
        Region 1: I/O ports at <unassigned>
        Region 2: I/O ports at <unassigned>
        Region 3: I/O ports at <unassigned>
        Region 4: I/O ports at 1100 [size=16]
        Capabilities: [70] Power Management version 2
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot+,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-

01:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8036 PCI-E Fast Ethernet Controller (rev 10)
        Subsystem: Toshiba America Info Systems Marvell 88E8036 Fast Ethernet Controller (Inventec)
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0, Cache Line Size: 16 bytes
        Interrupt: pin A routed to IRQ 11
        Region 0: Memory at cc000000 (64-bit, non-prefetchable) [size=16K]
        Region 2: I/O ports at c000 [size=256]
        Capabilities: [48] Power Management version 2
                Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
                Status: D0 PME-Enable- DSel=0 DScale=1 PME-
        Capabilities: [50] Vital Product Data
        Capabilities: [5c] Message Signalled Interrupts: 64bit+ Queue=0/1 Enable-
                Address: 00000000fee00000  Data: 4051
        Capabilities: [e0] Express Legacy Endpoint IRQ 0
                Device: Supported: MaxPayload 128 bytes, PhantFunc 0, ExtTag-
                Device: Latency L0s unlimited, L1 unlimited
                Device: AtnBtn- AtnInd- PwrInd-
                Device: Errors: Correctable- Non-Fatal- Fatal- Unsupported-
                Device: RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
                Device: MaxPayload 128 bytes, MaxReadReq 512 bytes
                Link: Supported Speed 2.5Gb/s, Width x1, ASPM L0s, Port 0
                Link: Latency L0s <256ns, L1 unlimited
                Link: ASPM Disabled RCB 128 bytes CommClk- ExtSynch-
                Link: Speed 2.5Gb/s, Width x1

05:04.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)
        Subsystem: Intel Corporation Unknown device 2741
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 128 (750ns min, 6000ns max)
        Interrupt: pin A routed to IRQ 11
        Region 0: Memory at b800b000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [dc] Power Management version 2
                Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
                Status: D0 PME-Enable- DSel=0 DScale=1 PME-

05:06.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 168, Cache Line Size: 128 bytes
        Interrupt: pin A routed to IRQ 11
        Region 0: Memory at b8001000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=05, secondary=06, subordinate=09, sec-latency=176
        Memory window 0: 88000000-89fff000 (prefetchable)
        Memory window 1: ba000000-bbfff000
        I/O window 0: 00008000-000080ff
        I/O window 1: 00008400-000084ff
        BridgeCtl: Parity- SERR- ISA- VGA- MAbort- >Reset+ 16bInt+ PostWrite+
        16-bit legacy interface ports at 0001

05:06.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller (prog-if 10 [OHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 128 (500ns min, 1000ns max), Cache Line Size: 16 bytes
        Interrupt: pin C routed to IRQ 11
        Region 0: Memory at b8000000 (32-bit, non-prefetchable) [size=2K]
        Region 1: Memory at b8004000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: [44] Power Management version 2
                Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME+

05:06.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64 (1750ns min, 1000ns max)
        Interrupt: pin D routed to IRQ 5
        Region 0: Memory at b8008000 (32-bit, non-prefetchable) [size=8K]
        Capabilities: [44] Power Management version 2
                Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-

05:06.4 Class 0805: Texas Instruments PCI6411, PCI6421, PCI6611, PCI6621, PCI7411, PCI7421, PCI7611, PCI7621 Secure Digital (SD) Controller
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64 (1750ns min, 1000ns max)
        Interrupt: pin A routed to IRQ 11
        Region 0: Memory at b800a000 (32-bit, non-prefetchable) [size=256]
        Region 1: Memory at b800a100 (32-bit, non-prefetchable) [size=256]
        Region 2: Memory at b800a200 (32-bit, non-prefetchable) [size=256]
        Capabilities: [80] Power Management version 2
                Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-
Thanks for all the help.

---

### Post by chili555 on 2007-02-20
I have continued to do a lot of research on Marvell Yukon and it's buggy driver sky2. I have read a number of comments that seem to involve editing the wording of the driver itself, compiling a new driver from a tarball, and amending *that* driver along the way and all of these seem a bit troubling. 

I am encouraged by this: [https://launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/68338](https://launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/68338) , especially here: > No need to touch that sources.list file.
'linux-image-2.6.17-50-386_2.6.17.1-50.50_i386.deb' or as appropriate
can be downloaded directly from:

[http://gb.archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.17/](http://gb.archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.17/)

Then, just use 'dpkg -i <file>' and enjoy!

This involves installing a second kernel on your machine that has, apparently, fixed sky2. The advantage here is that grub will show two kernels to boot from. If 2.6.17.1-50.50 doesn't fix it, you can boot into 2.6.17-11-generic and delete 50.50. 

Take a look.

I also read evidence that this is fixed in Feisty, which uses the 2.6.20 kernel. Here is a post about using the Feisty kernel: [http://ubuntuforums.org/showthread.php?t=333808](http://ubuntuforums.org/showthread.php?t=333808)  Again, if it doesn't work, you can boot back into 2.6.17-11-generic and delete 2.6.20.

I'll be glad to help you any way I can.

---

### Post by chili555 on 2007-02-20
Just to check, and because I'm just a bit compulsive, I followed this: 
> 1. backup /etc/apt/sources.list
2. replace temporary (!) all edgy with feisty in sources.list
3. apt-get update
4. apt-get install linux-headers-2.6.20-5 linux-headers-2.6.20-5-generic linux-image-2.6.20-5-generic
5. check /boot/grub/menu.lst, mine was set to hd(0,6) and /dev/sda7 and were wrong. It must be hd(0,1) and /dev/sda2
6. restore your /etc/apt/sources.list from step 1
7. reboot

I am writing to you from a 2.6.20 kernel on my old laptop! According to the counter on my CD player, it took 13 minutes! 

I am not sure about the part here: > check /boot/grub/menu.lst, mine was set to hd(0,6) and /dev/sda7 and were wrong. It must be hd(0,1) and /dev/sda2 I think you just need to duplicate what the settings are for your 2.6.17.x kernels are. Post back if you need help here.

Of course, my old lappy doesn't have the Marvell chipset, so I don't know if the new sky2 will solve your problem, but, since the 2.6.17 et al kernels are still here, and I can boot into one any time, this seems like a painless way to try it.

Two hitches: first, the default timeout in /boot/grub/menu.lst for you to hit ESC to see the boot menu is 3 seconds: a bit speedy for me. You might sudo gedit the file and change it to 10 or 15 seconds. Second, my wireless connection wanted a little coaxing to remember how to proceed.

Good luck and post back if you need help.

---

### Post by dontjee on 2007-02-20
Awesome thank you very much. I tried the  linux-image-2.6.17-50-386_2.6.17.1-50.50_i386.deb and that didn't seem to fix it. I'll try the 2.6.20-5 and get back to you. Thanks for writing out the instructions.

---

### Post by dontjee on 2007-02-22
The new kernel fixed it!!! I can download files without the internet stalling anymore. Thank you so much chili.

---

### Post by chili555 on 2007-02-22
Fabulous! First, please be sure you have restored your original /etc/apt/sources.list so you don't download anything else from Feisty aside from the kernel. Second, there are a few posts on this forum referencing Marvell Yukon stalling and some of them look like the poster gave up because he or she could never find the fix.

*You have the fix!!!*

Would you please go back to your first post and edit the subject to add SOLVED so others can gain from your painful journey? Thanks and have fun! Good luck.

---

