---
title: "Pulseaudio and ALSA help Please"
date: 2010-05-15
forum: New to Ubuntu
---

### Post by vipin.balakrishnan on 2010-05-15
Hi All,

 Sorry for the lengthy post. I was facing sound problem in Ubuntu 8.04 LTS and kernal 2.6.24-27-generic. My pulseaudio crashes very frequently.

when I tried to debug the pulseaudio with pulseaudio -vvvv. and  look into the log file generated.I'm not understanding the few lines in it. please any Ubuntu expert and sound expert help me.

1)  As soon as when I play any song it will put into the log file

```

May 15 22:52:40  pulseaudio[6305]: module-alsa-sink.c: Starting playback.
May 15 22:52:40  pulseaudio[6305]: module-alsa-sink.c: EAGAIN
May 15 22:52:40  pulseaudio[6305]: module-suspend-on-idle.c: Sink alsa_output.pci_1102_7_sound_card_0_alsa_playback_0 becomes idle.
May 15 22:52:40  pulseaudio[6305]: module-suspend-on-idle.c: Sink alsa_output.pci_1102_7_sound_card_0_alsa_playback_0 becomes busy.
May 15 22:52:40  pulseaudio[6305]: resampler.c: Channel matrix:
May 15 22:52:40  pulseaudio[6305]: resampler.c:        I00   I01
May 15 22:52:40  pulseaudio[6305]: resampler.c:     +------------
May 15 22:52:40  pulseaudio[6305]: resampler.c: O00 | 1.000 0.000
May 15 22:52:40  pulseaudio[6305]: resampler.c: O01 | 0.000 1.000
May 15 22:52:40  pulseaudio[6305]: resampler.c: O02 | 1.000 0.000
May 15 22:52:40  pulseaudio[6305]: resampler.c: O03 | 0.000 1.000
May 15 22:52:40  pulseaudio[6305]: resampler.c: Using resampler 'speex-float-3'
May 15 22:52:40  pulseaudio[6305]: resampler.c: Using float32le as working format.
May 15 22:52:40  pulseaudio[6305]: resampler.c: Choosing speex quality setting 3.
May 15 22:52:40  pulseaudio[6305]: sink-input.c: Created input 2 "Playback Stream" on alsa_output.pci_1102_7_sound_card_0_alsa_playback_0 with sample spec float32le 2ch 44100Hz and channel map front-left,front-right
[COLOR=Red][B]May 15 22:52:40  pulseaudio[6305]: memblock.c: Memory block too large for pool: 17640 > 16376
May 15 22:52:40  pulseaudio[6305]: memblockq.c: memblockq requested: maxlength=141120, tlength=70560, base=8, prebuf=67032, minreq=3528
May 15 22:52:40  pulseaudio[6305]: memblockq.c: memblockq sanitized: maxlength=141120, tlength=70560, base=8, prebuf=67032, minreq=3528[/B][/COLOR]

```

In this red colour line look to be little bit strange for me. Can anyone help me to translate these lines. Is there any problem with buffer size???

2) Second thing I noticed is I'm getting continues below message

```

May 15 22:53:40 pulseaudio[6305]: module-alsa-sink.c: EAGAIN

```

After a long play back my audio player will hang and it will through an  error something like this. This time pulseaudio daeomon will not be running and player memory utilization will start increasing.

```

May 15 19:46:49  pulseaudio[7076]: module-alsa-sink.c: Buffer underrun!
May 15 19:46:49  pulseaudio[7076]: module-alsa-sink.c: EAGAIN
May 15 19:46:49  pulseaudio[7076]: module-alsa-sink.c: Buffer underrun!
May 15 19:46:49  pulseaudio[7076]: module-alsa-sink.c: EAGAIN
May 15 19:46:49  pulseaudio[7076]: module-alsa-sink.c: Buffer underrun!
May 15 19:46:49  pulseaudio[7076]: module-alsa-sink.c: EAGAIN
May 15 19:46:49  pulseaudio[7076]: module-alsa-sink.c: Buffer underrun!
May 15 19:46:49  pulseaudio[7076]: module-alsa-sink.c: EAGAIN
May 15 19:46:49  pulseaudio[7076]: module-alsa-sink.c: Buffer underrun!
May 15 19:46:49  pulseaudio[7076]: module-alsa-sink.c: EAGAIN
May 15 19:46:49  pulseaudio[7076]: module-alsa-sink.c: Buffer underrun!
May 15 19:46:49  pulseaudio[7076]: module-alsa-sink.c: EAGAIN
May 15 19:46:49  pulseaudio[7076]: module-alsa-sink.c: Buffer underrun!
May 15 19:46:49  pulseaudio[7076]: module-alsa-sink.c: EAGAIN
May 15 19:46:49  pulseaudio[7076]: module-alsa-sink.c: Buffer underrun!

```

I have gone through one of the link below
[http://www.suse.de/~mana/alsa090_howto.html](http://www.suse.de/~mana/alsa090_howto.html)

In this link they disscribed  some of the program discribed like, if there no correct buffer size setup  "<<<<<<<<<<<<<<< Buffer Overrun >>>>>>>>>>>>>>>" message will be send back. Is this can releate to my problem???

Please I'm expecting a reply for this.

---

### Post by vipin.balakrishnan on 2010-05-15
Hi ALL

My hardware config i'm appending here
[HTML]
sudo lspci -vvv
[/HTML]

```

00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge Alternate
    Subsystem: ASUSTeK Computer Inc. Unknown device 83a2
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
    Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ >SERR- <PERR-
    Latency: 0
    Capabilities: [c4] HyperTransport: Slave or Primary Interface
        Command: BaseUnitID=0 UnitCnt=12 MastHost- DefDir- DUL-
        Link Control 0: CFlE- CST- CFE- <LkFail- Init+ EOC- TXO- <CRCErr=0 IsocEn+ LSEn- ExtCTL- 64b-
        Link Config 0: MLWI=16bit DwFcIn- MLWO=16bit DwFcOut- LWI=16bit DwFcInEn- LWO=16bit DwFcOutEn-
        Link Control 1: CFlE- CST- CFE- <LkFail+ Init- EOC+ TXO+ <CRCErr=0 IsocEn- LSEn- ExtCTL- 64b-
        Link Config 1: MLWI=8bit DwFcIn- MLWO=8bit DwFcOut- LWI=8bit DwFcInEn- LWO=8bit DwFcOutEn-
        Revision ID: 3.00
        Link Frequency 0: [b]
        Link Error 0: <Prot- <Ovfl- <EOC- CTLTm-
        Link Frequency Capability 0: 200MHz+ 300MHz- 400MHz+ 500MHz- 600MHz+ 800MHz+ 1.0GHz+ 1.2GHz- 1.4GHz- 1.6GHz- Vend-
        Feature Capability: IsocFC- LDTSTOP+ CRCTM- ECTLT- 64bA- UIDRD-
        Link Frequency 1: 200MHz
        Link Error 1: <Prot- <Ovfl- <EOC- CTLTm-
        Link Frequency Capability 1: 200MHz- 300MHz- 400MHz- 500MHz- 600MHz- 800MHz- 1.0GHz- 1.2GHz- 1.4GHz- 1.6GHz- Vend-
        Error Handling: PFlE- OFlE- PFE- OFE- EOCFE- RFE- CRCFE- SERRFE- CF- RE- PNFE- ONFE- EOCNFE- RNFE- CRCNFE- SERRNFE-
        Prefetchable memory behind bridge Upper: 00-00
        Bus Number: 00
    Capabilities: [54] HyperTransport: UnitID Clumping
    Capabilities: [40] HyperTransport: Retry Mode
    Capabilities: [9c] HyperTransport: #1a
    Capabilities: [f8] HyperTransport: #1c

00:02.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (ext gfx port 0) (prog-if 00 [Normal decode])
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
    Latency: 0, Cache Line Size: 64 bytes
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 0000c000-0000cfff
    Memory behind bridge: fa000000-fe9fffff
    Prefetchable memory behind bridge: 00000000c0000000-00000000dfffffff
    Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
    BridgeCtl: Parity+ SERR+ NoISA- VGA+ MAbort- >Reset- FastB2B-
    Capabilities: [50] Power Management version 3
        Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
        Status: D0 PME-Enable- DSel=0 DScale=0 PME-
    Capabilities: [58] Express Root Port (Slot+) IRQ 0
        Device: Supported: MaxPayload 128 bytes, PhantFunc 0, ExtTag+
        Device: Latency L0s <64ns, L1 <1us
        Device: Errors: Correctable+ Non-Fatal+ Fatal+ Unsupported+
        Device: RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop+
        Device: MaxPayload 128 bytes, MaxReadReq 128 bytes
        Link: Supported Speed unknown, Width x16, ASPM L0s L1, Port 0
        Link: Latency L0s <64ns, L1 <1us
        Link: ASPM Disabled RCB 64 bytes CommClk+ ExtSynch-
        Link: Speed 2.5Gb/s, Width x16
        Slot: AtnBtn- PwrCtrl- MRL- AtnInd- PwrInd- HotPlug- Surpise-
        Slot: Number 2, PowerLimit 75.000000
        Slot: Enabled AtnBtn- PwrFlt- MRL- PresDet- CmdCplt- HPIrq-
        Slot: AttnInd Unknown, PwrInd Unknown, Power-
        Root: Correctable- Non-Fatal- Fatal- PME-
    Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
        Address: fee0f00c  Data: 41b1
    Capabilities: [b0] Subsystem: ASUSTeK Computer Inc. Unknown device 83a2
    Capabilities: [b8] HyperTransport: MSI Mapping

00:0a.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 5) (prog-if 00 [Normal decode])
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
    Latency: 0, Cache Line Size: 64 bytes
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: fea00000-feafffff
    Prefetchable memory behind bridge: 00000000f8f00000-00000000f8ffffff
    Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
    BridgeCtl: Parity+ SERR+ NoISA+ VGA- MAbort- >Reset- FastB2B-
    Capabilities: [50] Power Management version 3
        Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
        Status: D0 PME-Enable- DSel=0 DScale=0 PME-
    Capabilities: [58] Express Root Port (Slot+) IRQ 0
        Device: Supported: MaxPayload 128 bytes, PhantFunc 0, ExtTag+
        Device: Latency L0s <64ns, L1 <1us
        Device: Errors: Correctable+ Non-Fatal+ Fatal+ Unsupported+
        Device: RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop+
        Device: MaxPayload 128 bytes, MaxReadReq 128 bytes
        Link: Supported Speed unknown, Width x1, ASPM L0s L1, Port 1
        Link: Latency L0s <64ns, L1 <1us
        Link: ASPM Disabled RCB 64 bytes CommClk+ ExtSynch-
        Link: Speed 2.5Gb/s, Width x1
        Slot: AtnBtn- PwrCtrl- MRL- AtnInd- PwrInd- HotPlug- Surpise-
        Slot: Number 10, PowerLimit 25.000000
        Slot: Enabled AtnBtn- PwrFlt- MRL- PresDet- CmdCplt- HPIrq-
        Slot: AttnInd Unknown, PwrInd Unknown, Power-
        Root: Correctable- Non-Fatal- Fatal- PME-
    Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
        Address: fee0f00c  Data: 41b9
    Capabilities: [b0] Subsystem: ASUSTeK Computer Inc. Unknown device 83a2
    Capabilities: [b8] HyperTransport: MSI Mapping

00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode] (prog-if 01 [AHCI 1.0])
    Subsystem: ASUSTeK Computer Inc. Unknown device 8389
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
    Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
    Latency: 64, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 20
    Region 0: I/O ports at b000 [size=8]
    Region 1: I/O ports at a000 [size=4]
    Region 2: I/O ports at 9000 [size=8]
    Region 3: I/O ports at 8000 [size=4]
    Region 4: I/O ports at 7000 [size=16]
    Region 5: Memory at f9fffc00 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [60] Power Management version 2
        Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
        Status: D0 PME-Enable- DSel=0 DScale=0 PME-
    Capabilities: [70] #12 [0010]

00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller (prog-if 10 [OHCI])
    Subsystem: ASUSTeK Computer Inc. Unknown device 8389
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
    Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
    Latency: 64, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 17
    Region 0: Memory at f9ffe000 (32-bit, non-prefetchable) [size=4K]

00:12.1 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI1 Controller (prog-if 10 [OHCI])
    Subsystem: ASUSTeK Computer Inc. Unknown device 8389
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B-
    Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
    Latency: 64, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 17
    Region 0: Memory at f9ffd000 (32-bit, non-prefetchable) [size=4K]

00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller (prog-if 20 [EHCI])
    Subsystem: ASUSTeK Computer Inc. Unknown device 8389
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B-
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
    Latency: 64, Cache Line Size: 64 bytes
    Interrupt: pin B routed to IRQ 18
    Region 0: Memory at f9fff800 (32-bit, non-prefetchable) [size=256]
    Capabilities: [c0] Power Management version 2
        Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold-)
        Status: D0 PME-Enable- DSel=0 DScale=0 PME-
        Bridge: PM- B3+
    Capabilities: [e4] Debug port

00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller (prog-if 10 [OHCI])
    Subsystem: ASUSTeK Computer Inc. Unknown device 8389
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
    Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
    Latency: 64, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 16
    Region 0: Memory at f9ffc000 (32-bit, non-prefetchable) [size=4K]

00:13.1 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI1 Controller (prog-if 10 [OHCI])
    Subsystem: ASUSTeK Computer Inc. Unknown device 8389
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B-
    Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
    Latency: 64, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 16
    Region 0: Memory at f9ffb000 (32-bit, non-prefetchable) [size=4K]

00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller (prog-if 20 [EHCI])
    Subsystem: ASUSTeK Computer Inc. Unknown device 8389
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B-
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
    Latency: 64, Cache Line Size: 64 bytes
    Interrupt: pin B routed to IRQ 19
    Region 0: Memory at f9fff400 (32-bit, non-prefetchable) [size=256]
    Capabilities: [c0] Power Management version 2
        Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold-)
        Status: D0 PME-Enable- DSel=0 DScale=0 PME-
        Bridge: PM- B3+
    Capabilities: [e4] Debug port

00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3c)
    Subsystem: ASUSTeK Computer Inc. Unknown device 8389
    Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
    Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort+ <MAbort- >SERR+ <PERR+
    Capabilities: [b0] HyperTransport: MSI Mapping

00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller (prog-if 8a [Master SecP PriP])
    Subsystem: ASUSTeK Computer Inc. Unknown device 8389
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
    Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
    Latency: 0
    Interrupt: pin A routed to IRQ 17
    Region 0: I/O ports at 01f0 [size=8]
    Region 1: I/O ports at 03f4 [size=1]
    Region 2: I/O ports at 0170 [size=8]
    Region 3: I/O ports at 0374 [size=1]
    Region 4: I/O ports at ff00 [size=16]
    Capabilities: [70] Message Signalled Interrupts: Mask- 64bit- Queue=0/1 Enable-
        Address: 00000000  Data: 0000

00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
    Subsystem: ASUSTeK Computer Inc. Unknown device 8389
    Control: I/O+ Mem+ BusMaster+ SpecCycle+ MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
    Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
    Latency: 0

00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (prog-if 01 [Subtractive decode])
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
    Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
    Latency: 64
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=64
    I/O behind bridge: 0000e000-0000efff
    Memory behind bridge: feb00000-febfffff
    Prefetchable memory behind bridge: fff00000-000fffff
    Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
    BridgeCtl: Parity+ SERR+ NoISA+ VGA- MAbort- >Reset- FastB2B-

00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller (prog-if 10 [OHCI])
    Subsystem: ASUSTeK Computer Inc. Unknown device 8389
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
    Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
    Latency: 64, Cache Line Size: 64 bytes
    Interrupt: pin C routed to IRQ 16
    Region 0: Memory at f9ffa000 (32-bit, non-prefetchable) [size=4K]

00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] HyperTransport Configuration
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
    Capabilities: [80] HyperTransport: Host or Secondary Interface
        Command: WarmRst+ DblEnd- DevNum=0 ChainSide- HostHide+ Slave- <EOCErr- DUL-
        Link Control: CFlE- CST- CFE- <LkFail- Init+ EOC- TXO- <CRCErr=0 IsocEn+ LSEn+ ExtCTL- 64b-
        Link Config: MLWI=16bit DwFcIn- MLWO=16bit DwFcOut- LWI=16bit DwFcInEn- LWO=16bit DwFcOutEn-
        Revision ID: 3.00
        Link Frequency: [b]
        Link Error: <Prot- <Ovfl- <EOC- CTLTm-
        Link Frequency Capability: 200MHz+ 300MHz- 400MHz+ 500MHz- 600MHz+ 800MHz+ 1.0GHz+ 1.2GHz+ 1.4GHz- 1.6GHz- Vend-
        Feature Capability: IsocFC+ LDTSTOP+ CRCTM- ECTLT- 64bA+ UIDRD- ExtRS- UCnfE-

00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Address Map
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
    Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-

00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] DRAM Controller
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
    Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-

00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Miscellaneous Control
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
    Capabilities: [f0] #0f [0010]

00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Link Control
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
    Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-

01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600 GT (rev a1) (prog-if 00 [VGA controller])
    Subsystem: XFX Pine Group Inc. Unknown device 2286
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
    Latency: 0
    Interrupt: pin A routed to IRQ 16
    Region 0: Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
    Region 1: Memory at c0000000 (64-bit, prefetchable) [size=512M]
    Region 3: Memory at fa000000 (64-bit, non-prefetchable) [size=32M]
    Region 5: I/O ports at cc00 [size=128]
    [virtual] Expansion ROM at fe9e0000 [disabled] [size=128K]
    Capabilities: [60] Power Management version 2
        Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
        Status: D0 PME-Enable- DSel=0 DScale=0 PME-
    Capabilities: [68] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Address: 0000000000000000  Data: 0000
    Capabilities: [78] Express Endpoint IRQ 0
        Device: Supported: MaxPayload 128 bytes, PhantFunc 0, ExtTag+
        Device: Latency L0s <512ns, L1 <4us
        Device: AtnBtn- AtnInd- PwrInd-
        Device: Errors: Correctable- Non-Fatal- Fatal- Unsupported-
        Device: RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop+
        Device: MaxPayload 128 bytes, MaxReadReq 512 bytes
        Link: Supported Speed 2.5Gb/s, Width x16, ASPM L0s L1, Port 0
        Link: Latency L0s <512ns, L1 <4us
        Link: ASPM Disabled RCB 128 bytes CommClk+ ExtSynch-
        Link: Speed 2.5Gb/s, Width x16

02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
    Subsystem: ASUSTeK Computer Inc. Unknown device 83a3
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
    Latency: 0, Cache Line Size: 32 bytes
    Interrupt: pin A routed to IRQ 221
    Region 0: I/O ports at d800 [size=256]
    Region 2: Memory at f8fff000 (64-bit, prefetchable) [size=4K]
    Region 4: Memory at f8ff8000 (64-bit, prefetchable) [size=16K]
    Expansion ROM at feaf0000 [disabled] [size=64K]
    Capabilities: [40] Power Management version 3
        Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=375mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
        Status: D0 PME-Enable- DSel=0 DScale=0 PME-
    Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
        Address: 00000000fee0f00c  Data: 41e1
    Capabilities: [70] Express Endpoint IRQ 1
        Device: Supported: MaxPayload 256 bytes, PhantFunc 0, ExtTag-
        Device: Latency L0s <512ns, L1 <64us
        Device: AtnBtn- AtnInd- PwrInd-
        Device: Errors: Correctable- Non-Fatal- Fatal- Unsupported-
        Device: RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
        Device: MaxPayload 128 bytes, MaxReadReq 4096 bytes
        Link: Supported Speed 2.5Gb/s, Width x1, ASPM L0s L1, Port 0
        Link: Latency L0s <512ns, L1 <64us
        Link: ASPM Disabled RCB 64 bytes CommClk+ ExtSynch-
        Link: Speed 2.5Gb/s, Width x1
    Capabilities: [ac] MSI-X: Enable- Mask- TabSize=4
        Vector table: BAR=4 offset=00000000
        PBA: BAR=4 offset=00000800
    Capabilities: [cc] Vital Product Data

03:07.0 Multimedia audio controller: Creative Labs SB Audigy LS
    Subsystem: Creative Labs Unknown device 100a
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
    Latency: 64 (500ns min, 5000ns max)
    Interrupt: pin A routed to IRQ 20
    Region 0: I/O ports at ec00 [size=32]
    Capabilities: [dc] Power Management version 2
        Flags: PMEClk- DSI+ D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
        Status: D0 PME-Enable- DSel=0 DScale=0 PME-

03:08.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev c0) (prog-if 10 [OHCI])
    Subsystem: ASUSTeK Computer Inc. Unknown device 81fe
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
    Latency: 64 (8000ns max), Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 21
    Region 0: Memory at febff800 (32-bit, non-prefetchable) [size=2K]
    Region 1: I/O ports at e880 [size=128]
    Capabilities: [50] Power Management version 2
        Flags: PMEClk- DSI- D1- D2+ AuxCurrent=0mA PME(D0-,D1-,D2+,D3hot+,D3cold+)
        Status: D0 PME-Enable- DSel=0 DScale=0 PME-


```

[HTML]
/home/vipinb/.pulse/daemon.conf
[/HTML]

```

# $Id: daemon.conf.in 2175 2008-03-27 23:39:10Z lennart $
#
# This file is part of PulseAudio.
#
# PulseAudio is free software; you can redistribute it and/or modify
# it under the terms of the GNU Lesser General Public License as published by
# the Free Software Foundation; either version 2 of the License, or
# (at your option) any later version.
#
# PulseAudio is distributed in the hope that it will be useful, but
# WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU
# General Public License for more details.
#
# You should have received a copy of the GNU Lesser General Public License
# along with PulseAudio; if not, write to the Free Software
# Foundation, Inc., 59 Temple Place, Suite 330, Boston, MA 02111-1307
# USA.

## Configuration file for the PulseAudio daemon. See pulse-daemon.conf(5) for
## more information. Default values a commented out.  Use either ; or # for
## commenting.

; daemonize = no
; fail = yes
; disallow-module-loading = no
; use-pid-file = yes
; system-instance = no
; disable-shm = no

; high-priority = yes
; nice-level = -11

; realtime-scheduling = no
; realtime-priority = 5

; exit-idle-time = -1
; module-idle-time = 20
; scache-idle-time = 20

; dl-search-path = (depends on architecture)

; default-script-file = 

; log-target = auto
; log-level = notice

; resample-method = speex-float-3
; disable-remixing = no

; no-cpu-limit = no

; rlimit-as = -1
; rlimit-core = -1
; rlimit-data = -1
; rlimit-fsize = -1
; rlimit-nofile = 256
; rlimit-stack = -1
; rlimit-nproc = -1
; rlimit-memlock = -1
; rlimit-nice = 31
; rlimit-rtprio = 9

; default-sample-format = s16le
  default-sample-rate = 48000
  default-sample-channels =4 

; default-fragments = 4
; default-fragment-size-msec = 25

```

---

### Post by jkxx on 2010-05-15
A quick google returned this page: [http://ubuntuforums.org/archive/index.php/t-982985.html]("http://ubuntuforums.org/archive/index.php/t-982985.html") which lets you try a couple modifications to the Pulse config file.

Disclaimer: I could not get Pulse to work properly on my system and had to uninstall it (10.04). I hope you have better luck with it.

---

### Post by BandD on 2010-05-15
can you post the results of?

```
aplay -l
```

---

### Post by vipin.balakrishnan on 2010-05-15
Hi ALL 

Please find the out put of 

[HTML]
$ aplay -l
[/HTML]```

**** List of PLAYBACK Hardware Devices ****
card 0: CA0106 [CA0106], device 0: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 1: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 2: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 3: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0



```

[HTML]
lsmod |grep snd 
[/HTML]

```

snd_ca0106             36192  2 
snd_ac97_codec        101028  1 snd_ca0106
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78724  3 snd_ca0106,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4868  0 
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
snd_rawmidi            25760  2 snd_ca0106,snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    56996  15 snd_ca0106,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
ac97_bus                3072  1 snd_ac97_codec
snd_page_alloc         11400  2 snd_ca0106,snd_pcm


```

---

### Post by vipin.balakrishnan on 2010-05-16
Hi ALL

Please anyone help me...

Expecting an answer

---

### Post by BandD on 2010-05-16
I'm not very familiar with the SoundBlaster cards.  Google didn't seem to help much.  I think in 8.04 you can go to System --> Preferences --> Sound.  Try switching everything to ALSA instead of Default or Pulse.  

You could also try updating to 10.04 LTS.  Pulse has come a long way in two years.  You might find that it works much better for you in 10.04.  

Also, if it was working fine for you with a different kernel, just select the last known working kernel on boot. 

Sorry I can't be of more help.

---

