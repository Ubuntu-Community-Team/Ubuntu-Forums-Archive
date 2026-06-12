---
title: "Qualcomm Atheros AR938x Wireless Network Adapter Not Found"
date: 2019-08-12
forum: Networking &amp; Wireless
---

### Post by merlot160 on 2019-08-12
Ubuntu 18.04 cannot find my Qualcomm Atheros AR938x Adaptor. It is switched on and working properly and I get "No WiFi Adaptor Found" when I select Wi-Fi. I have tried several commands in the terminal to try and find it to no avail.

Any help would be most appreciated.

---

### Post by &amp;wP*!) on 2019-08-14
Can you copy and paste here the output of **lspci -nnvv** ? You can use [http://pastebin.com](http://pastebin.com) for this.

---

### Post by merlot160 on 2019-08-16
```
00:00.0 Host bridge [0600]: Intel Corporation 440FX - 82441FX PMC [Natoma] [8086:1237] (rev 02)
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-


00:01.0 ISA bridge [0601]: Intel Corporation 82371SB PIIX3 ISA [Natoma/Triton II] [8086:7000]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0


00:01.1 IDE interface [0101]: Intel Corporation 82371AB/EB/MB PIIX4 IDE [8086:7111] (rev 01) (prog-if 8a [ISA Compatibility mode controller, supports both channels switched to PCI native mode, supports bus mastering])
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64
    Region 0: [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [size=8]
    Region 1: [virtual] Memory at 000003f0 (type 3, non-prefetchable)
    Region 2: [virtual] Memory at 00000170 (32-bit, non-prefetchable) [size=8]
    Region 3: [virtual] Memory at 00000370 (type 3, non-prefetchable)
    Region 4: I/O ports at d000 [size=16]
    Kernel driver in use: ata_piix
    Kernel modules: pata_acpi


00:02.0 VGA compatible controller [0300]: VMware SVGA II Adapter [15ad:0405] (prog-if 00 [VGA controller])
    Subsystem: VMware SVGA II Adapter [15ad:0405]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64
    Interrupt: pin A routed to IRQ 18
    Region 0: I/O ports at d010 [size=16]
    Region 1: Memory at f0000000 (32-bit, non-prefetchable) [size=128M]
    Region 2: Memory at f8000000 (32-bit, non-prefetchable) [size=2M]
    [virtual] Expansion ROM at 000c0000 [disabled] [size=128K]
    Kernel driver in use: vmwgfx
    Kernel modules: vmwgfx


00:03.0 Ethernet controller [0200]: Intel Corporation 82540EM Gigabit Ethernet Controller [8086:100e] (rev 02)
    Subsystem: Intel Corporation PRO/1000 MT Desktop Adapter [8086:001e]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64 (63750ns min)
    Interrupt: pin A routed to IRQ 19
    Region 0: Memory at f8200000 (32-bit, non-prefetchable) [size=128K]
    Region 2: I/O ports at d020 [size=8]
    Capabilities: <access denied>
    Kernel driver in use: e1000
    Kernel modules: e1000


00:04.0 System peripheral [0880]: InnoTek Systemberatung GmbH VirtualBox Guest Service [80ee:cafe]
    Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Interrupt: pin A routed to IRQ 20
    Region 0: I/O ports at d040 [size=32]
    Region 1: Memory at f8400000 (32-bit, non-prefetchable) [size=4M]
    Region 2: Memory at f8800000 (32-bit, prefetchable) [size=16K]
    Kernel driver in use: vboxguest
    Kernel modules: vboxguest


00:05.0 Multimedia audio controller [0401]: Intel Corporation 82801AA AC'97 Audio Controller [8086:2415] (rev 01)
    Subsystem: Dell 82801AA AC'97 Audio Controller [1028:0177]
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64
    Interrupt: pin A routed to IRQ 21
    Region 0: I/O ports at d100 [size=256]
    Region 1: I/O ports at d200 [size=64]
    Kernel driver in use: snd_intel8x0
    Kernel modules: snd_intel8x0


00:07.0 Bridge [0680]: Intel Corporation 82371AB/EB/MB PIIX4 ACPI [8086:7113] (rev 08)
    Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Interrupt: pin A routed to IRQ 9
    Kernel driver in use: piix4_smbus
    Kernel modules: i2c_piix4


00:0c.0 USB controller [0c03]: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller [8086:1e31] (prog-if 30 [XHCI])
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 20
    Region 0: Memory at f8810000 (32-bit, non-prefetchable) [size=64K]
    Kernel driver in use: xhci_hcd


00:0d.0 SATA controller [0106]: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) SATA Controller [AHCI mode] [8086:2829] (rev 02) (prog-if 01 [AHCI 1.0])
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64
    Interrupt: pin A routed to IRQ 21
    Region 0: I/O ports at d240 [size=8]
    Region 1: I/O ports at d248 [size=4]
    Region 2: I/O ports at d250 [size=8]
    Region 3: I/O ports at d258 [size=4]
    Region 4: I/O ports at d260 [size=16]
    Region 5: Memory at f8820000 (32-bit, non-prefetchable) [size=8K]
    Capabilities: <access denied>
    Kernel driver in use: ahci
    Kernel modules: ahci
```

---

### Post by chili555 on 2019-08-16
It appears that this is a virtual machine. Please see: [https://ubuntuforums.org/showthread.php?t=2424713](https://ubuntuforums.org/showthread.php?t=2424713)

---

