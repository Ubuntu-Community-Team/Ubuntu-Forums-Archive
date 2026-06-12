---
title: "installing ethernet card - not in ifconfig -a"
date: 2008-09-26
forum: Networking &amp; Wireless
---

### Post by ibaniski on 2008-09-26
Hey all,

I have a Intel® PRO/1000 PT Quad Port Bypass Server Adapter that I need to get on an Ubuntu server machine. I installed the driver listed on Intel's page (e1000e) without any problems.

The problem is that the card is not listed when doing *ifconfig -a*. The only things listed are the local loopback and the onboard ethernet adapter.

When executing *lsmod*, the module/driver is listed.

*lspci* returns the following:
```

Adapter (rev 06)
06:00.1 Ethernet controller: Intel Corporation 82571EB PRO/1000 AT Quad port Bypass Adapter (rev 06)
07:00.0 Ethernet controller: Intel Corporation 82571EB PRO/1000 AT Quad port Bypass Adapter (rev 06)
07:00.1 Ethernet controller: Intel Corporation 82571EB PRO/1000 AT Quad port Bypass Adapter (rev 06)

```

When I run *lshw -C network*, I get the following relevant information:
```

*-network:0 UNCLAIMED
    description: Ethernet controller
    product: 82571EB PRO/1000 AT Quad Port Bypass Adapter
    vendor: Intel Corporation
    physical id: 0
    bus info: pci@0000:06:00.0
    version 06
    width: 32 bits
    clock: 33MHz
    capabilities: pm msi pciexpress bus_master cap_list
    configuration: latency=0
*-network:1 UNCLAIMED
    description: Ethernet controller
    product: 82571EB PRO/1000 AT Quad Port Bypass Adapter
    vendor: Intel Corporation
    physical id: 0.1
    bus info: pci@0000:06:00.1
    version 06
    width: 32 bits
    clock: 33MHz
    capabilities: pm msi pciexpress bus_master cap_list
    configuration: latency=0
*-network:0 UNCLAIMED
    description: Ethernet controller
    product: 82571EB PRO/1000 AT Quad Port Bypass Adapter
    vendor: Intel Corporation
    physical id: 0
    bus info: pci@0000:07:00.0
    version 06
    width: 32 bits
    clock: 33MHz
    capabilities: pm msi pciexpress bus_master cap_list
    configuration: latency=0
*-network:1 UNCLAIMED
    description: Ethernet controller
    product: 82571EB PRO/1000 AT Quad Port Bypass Adapter
    vendor: Intel Corporation
    physical id: 0.1
    bus info: pci@0000:07:00.1
    version 06
    width: 32 bits
    clock: 33MHz
    capabilities: pm msi pciexpress bus_master cap_list
    configuration: latency=0
*-network
    description: Ethernet interface
    product: L1 Gigabit Ethernet Adapter
    ... more about the onboard adapter ...

```

Would anyone have an idea of how to enable this interface so I can then configure it? Any input is appreciated.

Oh, and by the way the card works fine on the same setup on OpenBSD.

Thanks,
i.b.

---

### Post by shanix on 2008-09-26
can I have the pci id for the card using

lspci -vvnn

and the kernel version?

uname -r

---

### Post by ibaniski on 2008-09-26
Here are the relevant devices obtained by *lspci -vvnn*
```

01:00.0 Ethernet controller [0200]: Attansic Technology Corp. L1 Gigabit Ethernet Adapter [1969:1048] (rev b0)
	Subsystem: ASUSTeK Computer Inc. Unknown device [1043:8226]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0, Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 216
	Region 0: Memory at fe6c0000 (64-bit, non-prefetchable) [size=256K]
	Expansion ROM at fe6a0000 [disabled] [size=128K]
	Capabilities: [40] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [48] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
		Address: 00000000fee0f00c  Data: 415a
	Capabilities: [58] Express Endpoint IRQ 0
		Device: Supported: MaxPayload 128 bytes, PhantFunc 0, ExtTag-
		Device: Latency L0s <4us, L1 unlimited
		Device: AtnBtn+ AtnInd+ PwrInd+
		Device: Errors: Correctable- Non-Fatal- Fatal- Unsupported-
		Device: RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
		Device: MaxPayload 128 bytes, MaxReadReq 512 bytes
		Link: Supported Speed 2.5Gb/s, Width x1, ASPM L0s, Port 0
		Link: Latency L0s unlimited, L1 unlimited
		Link: ASPM Disabled RCB 64 bytes CommClk+ ExtSynch-
		Link: Speed 2.5Gb/s, Width x1


06:00.0 Ethernet controller [0200]: Intel Corporation 82571EB PRO/1000 AT Quad Port Bypass Adapter [8086:10a0] (rev 06)
	Subsystem: Intel Corporation 82571EB PRO/1000 AT Quad Port Bypass Adapter [8086:10a0]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0, Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 15
	Region 0: Memory at fe980000 (32-bit, non-prefetchable) [size=128K]
	Region 1: Memory at fe960000 (32-bit, non-prefetchable) [size=128K]
	Region 2: I/O ports at c880 [size=32]
	Expansion ROM at fe940000 [disabled] [size=128K]
	Capabilities: [c8] Power Management version 2
		Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=1 PME-
	Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
		Address: 0000000000000000  Data: 0000
	Capabilities: [e0] Express Endpoint IRQ 0
		Device: Supported: MaxPayload 256 bytes, PhantFunc 0, ExtTag-
		Device: Latency L0s <512ns, L1 <64us
		Device: AtnBtn- AtnInd- PwrInd-
		Device: Errors: Correctable- Non-Fatal- Fatal- Unsupported-
		Device: RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop+
		Device: MaxPayload 128 bytes, MaxReadReq 512 bytes
		Link: Supported Speed 2.5Gb/s, Width x4, ASPM L0s, Port 2
		Link: Latency L0s <4us, L1 <64us
		Link: ASPM Disabled RCB 64 bytes CommClk- ExtSynch-
		Link: Speed 2.5Gb/s, Width x4

06:00.1 Ethernet controller [0200]: Intel Corporation 82571EB PRO/1000 AT Quad Port Bypass Adapter [8086:10a0] (rev 06)
	Subsystem: Intel Corporation 82571EB PRO/1000 AT Quad Port Bypass Adapter [8086:10a0]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0, Cache Line Size: 32 bytes
	Interrupt: pin B routed to IRQ 5
	Region 0: Memory at fe9e0000 (32-bit, non-prefetchable) [size=128K]
	Region 1: Memory at fe9c0000 (32-bit, non-prefetchable) [size=128K]
	Region 2: I/O ports at cc00 [size=32]
	Expansion ROM at fe9a0000 [disabled] [size=128K]
	Capabilities: [c8] Power Management version 2
		Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=1 PME-
	Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
		Address: 0000000000000000  Data: 0000
	Capabilities: [e0] Express Endpoint IRQ 0
		Device: Supported: MaxPayload 256 bytes, PhantFunc 0, ExtTag-
		Device: Latency L0s <512ns, L1 <64us
		Device: AtnBtn- AtnInd- PwrInd-
		Device: Errors: Correctable- Non-Fatal- Fatal- Unsupported-
		Device: RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop+
		Device: MaxPayload 128 bytes, MaxReadReq 512 bytes
		Link: Supported Speed 2.5Gb/s, Width x4, ASPM L0s, Port 2
		Link: Latency L0s <4us, L1 <64us
		Link: ASPM Disabled RCB 64 bytes CommClk- ExtSynch-
		Link: Speed 2.5Gb/s, Width x4

07:00.0 Ethernet controller [0200]: Intel Corporation 82571EB PRO/1000 AT Quad Port Bypass Adapter [8086:10a0] (rev 06)
	Subsystem: Intel Corporation 82571EB PRO/1000 AT Quad Port Bypass Adapter [8086:10a0]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0, Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 5
	Region 0: Memory at fea80000 (32-bit, non-prefetchable) [size=128K]
	Region 1: Memory at fea60000 (32-bit, non-prefetchable) [size=128K]
	Region 2: I/O ports at d880 [size=32]
	Expansion ROM at fea40000 [disabled] [size=128K]
	Capabilities: [c8] Power Management version 2
		Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=1 PME-
	Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
		Address: 0000000000000000  Data: 0000
	Capabilities: [e0] Express Endpoint IRQ 0
		Device: Supported: MaxPayload 256 bytes, PhantFunc 0, ExtTag-
		Device: Latency L0s <512ns, L1 <64us
		Device: AtnBtn- AtnInd- PwrInd-
		Device: Errors: Correctable- Non-Fatal- Fatal- Unsupported-
		Device: RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop+
		Device: MaxPayload 128 bytes, MaxReadReq 512 bytes
		Link: Supported Speed 2.5Gb/s, Width x4, ASPM L0s, Port 3
		Link: Latency L0s <4us, L1 <64us
		Link: ASPM Disabled RCB 64 bytes CommClk- ExtSynch-
		Link: Speed 2.5Gb/s, Width x4

07:00.1 Ethernet controller [0200]: Intel Corporation 82571EB PRO/1000 AT Quad Port Bypass Adapter [8086:10a0] (rev 06)
	Subsystem: Intel Corporation 82571EB PRO/1000 AT Quad Port Bypass Adapter [8086:10a0]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0, Cache Line Size: 32 bytes
	Interrupt: pin B routed to IRQ 11
	Region 0: Memory at feae0000 (32-bit, non-prefetchable) [size=128K]
	Region 1: Memory at feac0000 (32-bit, non-prefetchable) [size=128K]
	Region 2: I/O ports at dc00 [size=32]
	Expansion ROM at feaa0000 [disabled] [size=128K]
	Capabilities: [c8] Power Management version 2
		Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=1 PME-
	Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
		Address: 0000000000000000  Data: 0000
	Capabilities: [e0] Express Endpoint IRQ 0
		Device: Supported: MaxPayload 256 bytes, PhantFunc 0, ExtTag-
		Device: Latency L0s <512ns, L1 <64us
		Device: AtnBtn- AtnInd- PwrInd-
		Device: Errors: Correctable- Non-Fatal- Fatal- Unsupported-
		Device: RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop+
		Device: MaxPayload 128 bytes, MaxReadReq 512 bytes
		Link: Supported Speed 2.5Gb/s, Width x4, ASPM L0s, Port 3
		Link: Latency L0s <4us, L1 <64us
		Link: ASPM Disabled RCB 64 bytes CommClk- ExtSynch-
		Link: Speed 2.5Gb/s, Width x4

```

The kernel version is **2.6.24-16-server**.

Thanks.

---

### Post by jonobr on 2008-09-26
Could you check or post the relevant content of dmesg? Seeing any messages in there?

---

### Post by shanix on 2008-09-26
How about:

sudo mii-tool
ethtool -i eth0

and syslog, dmesg, message file to pastebin.

---

### Post by ibaniski on 2008-09-26
The following useful info regarding the card is in dmesg:
```

[   113.649950] e1000e: Intel(R) PRO/1000 Network Driver - 0.4.1.7-NAPI
[   113.649954] e1000e: Copyright (c) 1999-2008 Intel Corporation.

```

sudo mii-tool returns **eht0: no link**, but that's because at this point eth0 is the onboard card, and not my PCIx card. The cable is now plugged in the PCIx card, hence the "no link".

Thanks for the responses.

---

### Post by shanix on 2008-09-26
Can we take a look at the ifconfig and ifconfig -a reuslt? Also, if you replace the eth0 from the command to whatever your PCIx card is, what does it show?

---

### Post by ibaniski on 2008-09-26
Thanks for the responses.

The problem was that even though this is the correct driver for the card, the actual driver did not have the device registered. I just had to add my device to the driver and recompile it.

Just in case someone stumbles on this, the changes were made in the e1000_hw.h and netdev.c files

To see the actual id that should be added in e1000_hw.h look up the device in /usr/share/misc/pci.ids

Cheers.

--- edit ---

You really should contact Intel... they should provide you with a patch for an existing driver that will properly work with your card.

---

