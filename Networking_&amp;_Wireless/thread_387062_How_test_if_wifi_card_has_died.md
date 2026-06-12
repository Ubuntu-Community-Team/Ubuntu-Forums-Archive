---
title: "How test if wifi card has died"
date: 2007-03-17
forum: Networking &amp; Wireless
---

### Post by jlhughes on 2007-03-17
UPDATE: My wireless card disappeared, and I was unable to figure out why. I originally thought it had been caused by a botched software install stepping on something. I figured out a solution worth recommending:

Press and hold the "wireless" button to re-enable the card.

Too easy to believe, I realize, but true.

During the course of troubleshooting I had considered reinstalling the operating system. I downloaded a copy of Ubuntu 6.10 (Edgy), created a CD, tested the CD and then tried to reinstall.

During the boot sequence from the CD, the laptop reported "IPW 3945 Radio Frequency Kill Switch Set To On" I had no idea what that meant and my email to [email]support@system76.com[/email] went unanswered.

I was unable to get Edgy to work on the laptop, but I was able to get Dapper to work. It was when I was running on the CD and saw that the network STILL didn't recognize the wireless card that I realized that it wasn't a software issue.

Of course, I didn't try the wireless switch right away. First, I pulled the card out, examined it and reinstalled it. I then reinstalled the Network Manager Applet.

It was after doing all of this that I remembered that the laptop has a "wireless" button.

Pressing and holding the button worked. The card awoke and a connection was quickly established to my wireless network.

Another hint that there was nothing wrong with the card was provided by the command $sudo lspci -vv

03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
        Subsystem: Intel Corporation Unknown device 1000
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0, Cache Line Size: 64 bytes
        Interrupt: pin A routed to IRQ 169
        Region 0: Memory at d8000000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [c8] Power Management version 2
                Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-
        Capabilities: [d0] Message Signalled Interrupts: 64bit+ Queue=0/0 Enable-
                Address: 0000000000000000  Data: 0000
        Capabilities: [e0] Express Legacy Endpoint IRQ 0
                Device: Supported: MaxPayload 128 bytes, PhantFunc 0, ExtTag-
                Device: Latency L0s <512ns, L1 unlimited
                Device: AtnBtn- AtnInd- PwrInd-
                Device: Errors: Correctable- Non-Fatal- Fatal- Unsupported-
                Device: RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop+
                Device: MaxPayload 128 bytes, MaxReadReq 128 bytes
                Link: Supported Speed 2.5Gb/s, Width x1, ASPM L0s L1, Port 0
                Link: Latency L0s <128ns, L1 <64us
                Link: ASPM L0s L1 Enabled RCB 64 bytes CommClk+ ExtSynch-
                Link: Speed 2.5Gb/s, Width x1
        Capabilities: [100] Advanced Error Reporting
        Capabilities: [140] Device Serial Number 8a-89-01-ff-ff-02-13-00

05:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8055 PCI-E Gigabit Ethernet Controller (rev 11)
        Subsystem: QUANTA Computer Inc Unknown device 0754
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0, Cache Line Size: 64 bytes
        Interrupt: pin A routed to IRQ 50
        Region 0: Memory at da000000 (64-bit, non-prefetchable) [size=16K]
        Region 2: I/O ports at 4000 [size=256]
        [virtual] Expansion ROM at d4000000 [disabled] [size=128K]
        Capabilities: [48] Power Management version 3
                Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
                Status: D0 PME-Enable- DSel=0 DScale=1 PME-
        Capabilities: [50] Vital Product Data
        Capabilities: [5c] Message Signalled Interrupts: 64bit+ Queue=0/0 Enable+
                Address: 00000000fee00000  Data: 4032
        Capabilities: [e0] Express Legacy Endpoint IRQ 0
                Device: Supported: MaxPayload 128 bytes, PhantFunc 0, ExtTag-
                Device: Latency L0s unlimited, L1 unlimited
                Device: AtnBtn- AtnInd- PwrInd-
                Device: Errors: Correctable- Non-Fatal- Fatal- Unsupported-
                Device: RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
                Device: MaxPayload 128 bytes, MaxReadReq 512 bytes
                Link: Supported Speed 2.5Gb/s, Width x1, ASPM L0s L1, Port 0
                Link: Latency L0s <256ns, L1 unlimited
                Link: ASPM Disabled RCB 128 bytes CommClk+ ExtSynch-
                Link: Speed 2.5Gb/s, Width x1
        Capabilities: [100] Advanced Error Reporting

---

