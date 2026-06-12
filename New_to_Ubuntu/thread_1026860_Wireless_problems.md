---
title: "Wireless problems"
date: 2008-12-31
forum: New to Ubuntu
---

### Post by HolySpagetty on 2008-12-31
I just got my Ubuntu back up and running when all of a sudden a symtom appears, I have no wireless connection.

This is odd since it never did this before but once and all I had to do was take out the wireless and put it back in.

It works in WinXP x64 so it is not faulty hardware.

Can someone please help me with this catastrophe? :confused:

---

### Post by 67GTA on 2008-12-31
Post the output of ```
lspci -kvv
``` from a terminal.

---

### Post by HolySpagetty on 2008-12-31
```
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
	Subsystem: Advanced Micro Devices [AMD] RS780 Host Bridge
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ >SERR- <PERR- INTx-
	Latency: 32
	Region 3: Memory at <ignored> (64-bit, non-prefetchable)
	Capabilities: <access denied>

00:02.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (ext gfx port 0)
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 4 bytes
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: f8000000-fbffffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA- VGA+ MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:0a.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 5)
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 4 bytes
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: fdc00000-fdcfffff
	Prefetchable memory behind bridge: 00000000fdf00000-00000000fdffffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode] (prog-if 01)
	Subsystem: Giga-byte Technology Device b002
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 32
	Interrupt: pin A routed to IRQ 2300
	Region 0: I/O ports at ff00 [size=8]
	Region 1: I/O ports at fe00 [size=4]
	Region 2: I/O ports at fd00 [size=8]
	Region 3: I/O ports at fc00 [size=4]
	Region 4: I/O ports at fb00 [size=16]
	Region 5: Memory at fe02f000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ahci
	Kernel modules: ahci

00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller (prog-if 10)
	Subsystem: Giga-byte Technology Device 5004
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 32, Cache Line Size: 4 bytes
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at fe02e000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd
	Kernel modules: ohci-hcd

00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller (prog-if 10)
	Subsystem: Giga-byte Technology Device 5004
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 32, Cache Line Size: 4 bytes
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at fe02d000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd
	Kernel modules: ohci-hcd

00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller (prog-if 20)
	Subsystem: Giga-byte Technology Device 5004
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 32, Cache Line Size: 64 bytes
	Interrupt: pin B routed to IRQ 17
	Region 0: Memory at fe02c000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd
	Kernel modules: ehci-hcd

00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller (prog-if 10)
	Subsystem: Giga-byte Technology Device 5004
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 32, Cache Line Size: 4 bytes
	Interrupt: pin A routed to IRQ 18
	Region 0: Memory at fe02b000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd
	Kernel modules: ohci-hcd

00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller (prog-if 10)
	Subsystem: Giga-byte Technology Device 5004
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 32, Cache Line Size: 4 bytes
	Interrupt: pin A routed to IRQ 18
	Region 0: Memory at fe02a000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd
	Kernel modules: ohci-hcd

00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller (prog-if 20)
	Subsystem: Giga-byte Technology Device 5004
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 32, Cache Line Size: 64 bytes
	Interrupt: pin B routed to IRQ 19
	Region 0: Memory at fe029000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd
	Kernel modules: ehci-hcd

00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
	Subsystem: Giga-byte Technology Device 4385
	Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort+ <MAbort- >SERR+ <PERR+ INTx-
	Capabilities: <access denied>
	Kernel driver in use: piix4_smbus
	Kernel modules: i2c-piix4

00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller (prog-if 8a [Master SecP PriP])
	Subsystem: Giga-byte Technology Device 5002
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 32
	Interrupt: pin A routed to IRQ 16
	Region 0: I/O ports at 01f0 [size=8]
	Region 1: I/O ports at 03f4 [size=1]
	Region 2: I/O ports at 0170 [size=8]
	Region 3: I/O ports at 0374 [size=1]
	Region 4: I/O ports at fa00 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: pata_atiixp
	Kernel modules: pata_atiixp, pata_acpi, ata_generic

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
	Subsystem: Giga-byte Technology Device a022
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=slow >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 32, Cache Line Size: 4 bytes
	Interrupt: pin ? routed to IRQ 16
	Region 0: Memory at fe024000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
	Subsystem: ATI Technologies Inc Device 4383
	Control: I/O+ Mem+ BusMaster+ SpecCycle+ MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0

00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (prog-if 01)
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop+ ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=64
	I/O behind bridge: 0000c000-0000cfff
	Memory behind bridge: fde00000-fdefffff
	Prefetchable memory behind bridge: fdd00000-fddfffff
	Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-

00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller (prog-if 10)
	Subsystem: Giga-byte Technology Device 5004
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 32, Cache Line Size: 4 bytes
	Interrupt: pin C routed to IRQ 18
	Region 0: Memory at fe028000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd
	Kernel modules: ohci-hcd

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Capabilities: <access denied>
	Kernel driver in use: k8temp
	Kernel modules: k8temp

01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600 GT (rev a1)
	Subsystem: XFX Pine Group Inc. Device 4016
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 18
	Region 0: Memory at fa000000 (32-bit, non-prefetchable) [size=16M]
	Region 1: Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Region 3: Memory at f8000000 (64-bit, non-prefetchable) [size=32M]
	Region 5: I/O ports at ef00 [size=128]
	[virtual] Expansion ROM at fb000000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: nvidia
	Kernel modules: nvidiafb, nvidia

02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
	Subsystem: Giga-byte Technology Device e000
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 2301
	Region 0: I/O ports at de00 [size=256]
	Region 2: Memory at fdfff000 (64-bit, prefetchable) [size=4K]
	Region 4: Memory at fdfe0000 (64-bit, prefetchable) [size=64K]
	[virtual] Expansion ROM at fdf00000 [disabled] [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: r8169
	Kernel modules: r8169

03:0e.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link) (prog-if 10)
	Subsystem: Giga-byte Technology Device 1000
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 32 (500ns min, 1000ns max), Cache Line Size: 4 bytes
	Interrupt: pin A routed to IRQ 22
	Region 0: Memory at fdeff000 (32-bit, non-prefetchable) [size=2K]
	Region 1: Memory at fdef8000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: ohci1394
	Kernel modules: ohci1394


```

Sorry, don't think it kept it's original format.

But, there ya go. 

I have no idea what any of it means but it may mean something to you guys..

---

### Post by 67GTA on 2008-12-31
That command shows your PCI devices. It doesn't show any wireless devices. What kind of wireless card do you have?

---

### Post by HolySpagetty on 2008-12-31
It is not a card, it is a USB wireless, sorry, forgot to mention that.

---

### Post by 67GTA on 2008-12-31
Then try ```
lsusb
```

---

### Post by HolySpagetty on 2008-12-31
Nothing comes up, it doesn't say it is an invalid command, it it just blank, sat there for like a minute waiting but nothing.

Thanks for your quick reply's BTW. :)

Note: Since it is New Year's and all, I am going to go eat a little right now. And once again, thanks a lot. You guys answered a lot of my questions and are making my Ubuntu experience great. :D

---

### Post by melojo on 2008-12-31
make sure you typed it correctly  

lsusb

the first letter is a small L not a 1(one)

---

### Post by HolySpagetty on 2008-12-31
I did, nothing happens...

I have no idea, because I also have a USB mouse that works.. :confused:

---

### Post by 67GTA on 2008-12-31
Something isn't right then. Open a terminal and run ```
dmesg > /home/yourusername/Desktop/dmesg
``` Post the file that it creates.

---

### Post by HolySpagetty on 2008-12-31
Sorry, New Years, will do as soon as possible.. :D

Thanks once again, again. :)

---

### Post by HolySpagetty on 2008-12-31
Here it is:

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.27-9-generic (buildd@yellow) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Thu Nov 20 22:15:32 UTC 2008 (Ubuntu 2.6.27-9.19-generic)
[    0.000000] Command line: root=UUID=126aacd9-472e-4bdc-9608-a1707d41f5f3 ro quiet splash vga=791
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000cfee0000 (usable)
[    0.000000]  BIOS-e820: 00000000cfee0000 - 00000000cfee3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000cfee3000 - 00000000cfef0000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000cfef0000 - 00000000cff00000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000130000000 (usable)
[    0.000000] last_pfn = 0x130000 max_arch_pfn = 0x3ffffffff
[    0.000000] last_pfn = 0xcfee0 max_arch_pfn = 0x3ffffffff
[    0.000000] init_memory_mapping
[    0.000000]  0000000000 - 00cfe00000 page 2M
[    0.000000]  00cfe00000 - 00cfee0000 page 4k
[    0.000000] kernel direct mapping tables up to cfee0000 @ 8000-e000
[    0.000000] last_map_addr: cfee0000 end: cfee0000
[    0.000000] init_memory_mapping
[    0.000000]  0100000000 - 0130000000 page 2M
[    0.000000] kernel direct mapping tables up to 130000000 @ c000-12000
[    0.000000] last_map_addr: 130000000 end: 130000000
[    0.000000] RAMDISK: 37054000 - 37fefbc4
[    0.000000] DMI 2.4 present.
[    0.000000] ACPI: RSDP 000F70C0, 0014 (r0 GBT   )
[    0.000000] ACPI: RSDT CFEE3000, 0038 (r1 GBT    GBTUACPI 42302E31 GBTU  1010101)
[    0.000000] ACPI: FACP CFEE3040, 0074 (r1 GBT    GBTUACPI 42302E31 GBTU  1010101)
[    0.000000] ACPI: DSDT CFEE30C0, 6550 (r1 GBT    GBTUACPI     1000 MSFT  3000000)
[    0.000000] ACPI: FACS CFEE0000, 0040
[    0.000000] ACPI: SSDT CFEE9700, 030E (r1 PTLTD  POWERNOW        1  LTP        1)
[    0.000000] ACPI: HPET CFEE9A40, 0038 (r1 GBT    GBTUACPI 42302E31 GBTU       98)
[    0.000000] ACPI: MCFG CFEE9A80, 003C (r1 GBT    GBTUACPI 42302E31 GBTU  1010101)
[    0.000000] ACPI: APIC CFEE9640, 0084 (r1 GBT    GBTUACPI 42302E31 GBTU  1010101)
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-0000000130000000
[    0.000000] Bootmem setup node 0 0000000000000000-0000000130000000
[    0.000000]   NODE_DATA [0000000000001000 - 0000000000005fff]
[    0.000000]   bootmap [000000000000d000 -  0000000000032fff] pages 26
[    0.000000] (7 early reservations) ==> bootmem [0000000000 - 0130000000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
[    0.000000]   #2 [0000200000 - 00008b8f9c]    TEXT DATA BSS ==> [0000200000 - 00008b8f9c]
[    0.000000]   #3 [0037054000 - 0037fefbc4]          RAMDISK ==> [0037054000 - 0037fefbc4]
[    0.000000]   #4 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000]
[    0.000000]   #5 [0000008000 - 000000c000]          PGTABLE ==> [0000008000 - 000000c000]
[    0.000000]   #6 [000000c000 - 000000d000]          PGTABLE ==> [000000c000 - 000000d000]
[    0.000000] found SMP MP-table at [ffff8800000f5770] 000f5770
[    0.000000]  [ffffe20000000000-ffffe20004bfffff] PMD -> [ffff880028200000-ffff88002c1fffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00130000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x000cfee0
[    0.000000]     0: 0x00100000 -> 0x00130000
[    0.000000] On node 0 totalpages: 1048191
[    0.000000]   DMA zone: 2109 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 831264 pages, LIFO batch:31
[    0.000000]   Normal zone: 193536 pages, LIFO batch:31
[    0.000000] Detected use of extended apic ids on hypertransport bus
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] dfl dfl lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 0, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Setting APIC routing to flat
[    0.000000] ACPI: HPET id: 0x10b9a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000cfee0000 - 00000000cfee3000
[    0.000000] PM: Registered nosave memory: 00000000cfee3000 - 00000000cfef0000
[    0.000000] PM: Registered nosave memory: 00000000cfef0000 - 00000000cff00000
[    0.000000] PM: Registered nosave memory: 00000000cff00000 - 00000000e0000000
[    0.000000] PM: Registered nosave memory: 00000000e0000000 - 00000000f0000000
[    0.000000] PM: Registered nosave memory: 00000000f0000000 - 00000000fec00000
[    0.000000] PM: Registered nosave memory: 00000000fec00000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at d0000000 (gap: cff00000:10100000)
[    0.000000] PERCPU: Allocating 64928 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 4, nr_node_ids 1
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1026909
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: root=UUID=126aacd9-472e-4bdc-9608-a1707d41f5f3 ro quiet splash vga=791
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] TSC: PIT calibration confirmed by PMTIMER.
[    0.000000] TSC: using PIT calibration value
[    0.000000] Detected 2906.179 MHz processor.
[    0.004000] Console: colour dummy device 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Checking aperture...
[    0.004000] No AGP bridge found
[    0.004000] Node 0: aperture @ 20000000 size 32 MB
[    0.004000] Aperture pointing to e820 RAM. Ignoring.
[    0.004000] Your BIOS doesn't leave a aperture memory hole
[    0.004000] Please enable the IOMMU option in the BIOS setup
[    0.004000] This costs you 64 MB of RAM
[    0.004000] Mapping aperture over 65536 KB of RAM @ 20000000
[    0.004000] PM: Registered nosave memory: 0000000020000000 - 0000000024000000
[    0.004000] Memory: 4038308k/4980736k available (3112k kernel code, 154456k reserved, 1575k data, 536k init)
[    0.004000] CPA: page pool initialized 1 of 1 pages preallocated
[    0.004000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.004000] hpet clockevent registered
[    0.004007] Calibrating delay loop (skipped), value calculated using timer frequency.. 5812.35 BogoMIPS (lpj=11624716)
[    0.004027] Security Framework initialized
[    0.004033] SELinux:  Disabled at boot.
[    0.004043] AppArmor: AppArmor initialized
[    0.004356] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.006560] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.007445] Mount-cache hash table entries: 256
[    0.007597] Initializing cgroup subsys ns
[    0.007600] Initializing cgroup subsys cpuacct
[    0.007602] Initializing cgroup subsys memory
[    0.007614] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.007615] CPU: L2 Cache: 512K (64 bytes/line)
[    0.007617] CPU 0/0 -> Node 0
[    0.007618] tseg: 00cff00000
[    0.007620] CPU: Physical Processor ID: 0
[    0.007621] CPU: Processor Core ID: 0
[    0.007628] using C1E aware idle routine
[    0.008018] ACPI: Core revision 20080609
[    0.009724] ACPI: Checking initramfs for custom DSDT
[    0.364642] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.407387] CPU0: AMD Athlon(tm) 64 X2 Dual Core Processor 5600+ stepping 02
[    0.407390] Using local APIC timer interrupts.
[    0.408026] APIC timer calibration result 12526665
[    0.408028] Detected 12.526 MHz APIC timer.
[    0.408150] Booting processor 1/1 ip 6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 5812.42 BogoMIPS (lpj=11624848)
[    0.004000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.004000] CPU 1/1 -> Node 0
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.496192] CPU1: AMD Athlon(tm) 64 X2 Dual Core Processor 5600+ stepping 02
[    0.496203] Brought up 2 CPUs
[    0.496205] Total of 2 processors activated (11624.78 BogoMIPS).
[    0.496295] CPU0 attaching sched-domain:
[    0.496297]  domain 0: span 0-1 level CPU
[    0.496299]   groups: 0 1
[    0.496302]   domain 1: span 0-1 level NODE
[    0.496303]    groups: 0-1
[    0.496307] CPU1 attaching sched-domain:
[    0.496308]  domain 0: span 0-1 level CPU
[    0.496310]   groups: 1 0
[    0.496313]   domain 1: span 0-1 level NODE
[    0.496314]    groups: 0-1
[    0.496378] net_namespace: 1552 bytes
[    0.496378] Booting paravirtualized kernel on bare hardware
[    0.496378] Time:  2:50:41  Date: 01/01/09
[    0.496378] NET: Registered protocol family 16
[    0.496378] node 0 link 0: io port [c000, ffff]
[    0.496378] TOM: 00000000d0000000 aka 3328M
[    0.496378] node 0 link 0: mmio [a0000, bffff]
[    0.496378] node 0 link 0: mmio [d0000000, fe02ffff]
[    0.496378] node 0 link 0: mmio [e0000000, efffffff]
[    0.496378] TOM2: 0000000130000000 aka 4864M
[    0.496378] bus: [00,03] on node 0 link 0
[    0.496378] bus: 00 index 0 io port: [0, ffff]
[    0.496378] bus: 00 index 1 mmio: [a0000, bffff]
[    0.496378] bus: 00 index 2 mmio: [d0000000, ffffffff]
[    0.496378] bus: 00 index 3 mmio: [130000000, fcffffffff]
[    0.496378] ACPI: bus type pci registered
[    0.496378] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.496378] PCI: MCFG area at e0000000 reserved in E820
[    0.506304] PCI: Using MMCONFIG at e0000000 - efffffff
[    0.506306] PCI: Using configuration type 1 for base access
[    0.506334] ACPI: EC: Look up EC in DSDT
[    0.515436] ACPI: Interpreter enabled
[    0.515440] ACPI: (supports S0 S1 S4 S5)
[    0.515455] ACPI: Using IOAPIC for interrupt routing
[    0.520417] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.520417] PCI: 0000:00:00.0 reg 1c 64bit mmio: [e0000000, ffffffff]
[    0.520417] pci 0000:00:02.0: PME# supported from D0 D3hot D3cold
[    0.520417] pci 0000:00:02.0: PME# disabled
[    0.520417] pci 0000:00:0a.0: PME# supported from D0 D3hot D3cold
[    0.520417] pci 0000:00:0a.0: PME# disabled
[    0.520417] PCI: 0000:00:11.0 reg 10 io port: [ff00, ff07]
[    0.520417] PCI: 0000:00:11.0 reg 14 io port: [fe00, fe03]
[    0.520417] PCI: 0000:00:11.0 reg 18 io port: [fd00, fd07]
[    0.520417] PCI: 0000:00:11.0 reg 1c io port: [fc00, fc03]
[    0.520417] PCI: 0000:00:11.0 reg 20 io port: [fb00, fb0f]
[    0.520417] PCI: 0000:00:11.0 reg 24 32bit mmio: [fe02f000, fe02f3ff]
[    0.520417] pci 0000:00:11.0: set SATA to AHCI mode
[    0.520417] PCI: 0000:00:12.0 reg 10 32bit mmio: [fe02e000, fe02efff]
[    0.520417] PCI: 0000:00:12.1 reg 10 32bit mmio: [fe02d000, fe02dfff]
[    0.520417] PCI: 0000:00:12.2 reg 10 32bit mmio: [fe02c000, fe02c0ff]
[    0.520454] pci 0000:00:12.2: supports D1
[    0.520456] pci 0000:00:12.2: supports D2
[    0.520457] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
[    0.520461] pci 0000:00:12.2: PME# disabled
[    0.520484] PCI: 0000:00:13.0 reg 10 32bit mmio: [fe02b000, fe02bfff]
[    0.520541] PCI: 0000:00:13.1 reg 10 32bit mmio: [fe02a000, fe02afff]
[    0.520612] PCI: 0000:00:13.2 reg 10 32bit mmio: [fe029000, fe0290ff]
[    0.520659] pci 0000:00:13.2: supports D1
[    0.520660] pci 0000:00:13.2: supports D2
[    0.520661] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
[    0.520665] pci 0000:00:13.2: PME# disabled
[    0.520765] PCI: 0000:00:14.1 reg 10 io port: [0, 7]
[    0.520772] PCI: 0000:00:14.1 reg 14 io port: [0, 3]
[    0.520779] PCI: 0000:00:14.1 reg 18 io port: [0, 7]
[    0.520785] PCI: 0000:00:14.1 reg 1c io port: [0, 3]
[    0.520791] PCI: 0000:00:14.1 reg 20 io port: [fa00, fa0f]
[    0.520848] PCI: 0000:00:14.2 reg 10 64bit mmio: [fe024000, fe027fff]
[    0.520888] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
[    0.520892] pci 0000:00:14.2: PME# disabled
[    0.520987] PCI: 0000:00:14.5 reg 10 32bit mmio: [fe028000, fe028fff]
[    0.521110] PCI: 0000:01:00.0 reg 10 32bit mmio: [fa000000, faffffff]
[    0.521115] PCI: 0000:01:00.0 reg 14 32bit mmio: [d0000000, dfffffff]
[    0.521127] PCI: 0000:01:00.0 reg 1c 64bit mmio: [f8000000, f9ffffff]
[    0.521132] PCI: 0000:01:00.0 reg 24 io port: [ef00, ef7f]
[    0.521137] PCI: 0000:01:00.0 reg 30 32bit mmio: [0, 1ffff]
[    0.521192] PCI: bridge 0000:00:02.0 io port: [e000, efff]
[    0.521194] PCI: bridge 0000:00:02.0 32bit mmio: [f8000000, fbffffff]
[    0.521198] PCI: bridge 0000:00:02.0 64bit mmio pref: [d0000000, dfffffff]
[    0.521233] PCI: 0000:02:00.0 reg 10 io port: [de00, deff]
[    0.521244] PCI: 0000:02:00.0 reg 18 32bit mmio: [fdfff000, fdffffff]
[    0.521255] PCI: 0000:02:00.0 reg 20 32bit mmio: [fdfe0000, fdfeffff]
[    0.521265] PCI: 0000:02:00.0 reg 30 32bit mmio: [0, ffff]
[    0.521287] pci 0000:02:00.0: supports D1
[    0.521288] pci 0000:02:00.0: supports D2
[    0.521289] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.521293] pci 0000:02:00.0: PME# disabled
[    0.521335] PCI: bridge 0000:00:0a.0 io port: [d000, dfff]
[    0.521337] PCI: bridge 0000:00:0a.0 32bit mmio: [fdc00000, fdcfffff]
[    0.521341] PCI: bridge 0000:00:0a.0 64bit mmio pref: [fdf00000, fdffffff]
[    0.521407] PCI: 0000:03:0e.0 reg 10 32bit mmio: [fdeff000, fdeff7ff]
[    0.521415] PCI: 0000:03:0e.0 reg 14 32bit mmio: [fdef8000, fdefbfff]
[    0.521468] pci 0000:03:0e.0: supports D1
[    0.521469] pci 0000:03:0e.0: supports D2
[    0.521470] pci 0000:03:0e.0: PME# supported from D0 D1 D2 D3hot
[    0.521475] pci 0000:03:0e.0: PME# disabled
[    0.521504] pci 0000:00:14.4: transparent bridge
[    0.521508] PCI: bridge 0000:00:14.4 io port: [c000, cfff]
[    0.521512] PCI: bridge 0000:00:14.4 32bit mmio: [fde00000, fdefffff]
[    0.521516] PCI: bridge 0000:00:14.4 32bit mmio pref: [fdd00000, fddfffff]
[    0.521533] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.521927] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[    0.522064] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE2._PRT]
[    0.522164] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCEA._PRT]
[    0.541019] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.541019] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.541019] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.544046] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.544186] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.544325] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.544463] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.544601] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.544665] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.544665] pnp: PnP ACPI init
[    0.544665] ACPI: bus type pnp registered
[    0.548132] pnp 00:0c: mem resource (0xe0000000-0xefffffff) overlaps 0000:00:00.0 BAR 3 (0xe0000000-0xffffffff), disabling
[    0.548282] pnp 00:0d: mem resource (0xffff0000-0xffffffff) overlaps 0000:00:00.0 BAR 3 (0xe0000000-0xffffffff), disabling
[    0.548284] pnp 00:0d: mem resource (0xfec00000-0xfec00fff) overlaps 0000:00:00.0 BAR 3 (0xe0000000-0xffffffff), disabling
[    0.548287] pnp 00:0d: mem resource (0xfee00000-0xfee00fff) overlaps 0000:00:00.0 BAR 3 (0xe0000000-0xffffffff), disabling
[    0.548289] pnp 00:0d: mem resource (0xfff80000-0xfffeffff) overlaps 0000:00:00.0 BAR 3 (0xe0000000-0xffffffff), disabling
[    0.548337] pnp: PnP ACPI: found 14 devices
[    0.548337] ACPI: ACPI bus type pnp unregistered
[    0.548337] PCI: Using ACPI for IRQ routing
[    0.548337] pci 0000:00:00.0: BAR 3: can't allocate resource
[    0.568038] NET: Registered protocol family 8
[    0.568039] NET: Registered protocol family 20
[    0.568064] NetLabel: Initializing
[    0.568065] NetLabel:  domain hash size = 128
[    0.568066] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.568078] NetLabel:  unlabeled traffic allowed by default
[    0.568153] PCI-DMA: Disabling AGP.
[    0.568248] PCI-DMA: aperture base @ 20000000 size 65536 KB
[    0.568248] PCI-DMA: using GART IOMMU.
[    0.568248] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture
[    0.568495] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.568500] hpet0: 4 32-bit timers, 14318180 Hz
[    0.571395] tracer: 1286 pages allocated for 65536 entries of 80 bytes
[    0.571397]    actual entries 65586
[    0.571493] AppArmor: AppArmor Filesystem Enabled
[    0.571515] ACPI: RTC can wake from S4
[    0.572048] Switched to high resolution mode on CPU 0
[    0.572169] Switched to high resolution mode on CPU 1
[    0.584046] system 00:01: ioport range 0x4d0-0x4d1 has been reserved
[    0.584049] system 00:01: ioport range 0x220-0x225 has been reserved
[    0.584051] system 00:01: ioport range 0x290-0x294 has been reserved
[    0.584056] system 00:02: ioport range 0x4100-0x411f has been reserved
[    0.584058] system 00:02: ioport range 0x228-0x22f has been reserved
[    0.584060] system 00:02: ioport range 0x238-0x23f has been reserved
[    0.584062] system 00:02: ioport range 0x40b-0x40b has been reserved
[    0.584064] system 00:02: ioport range 0x4d6-0x4d6 has been reserved
[    0.584066] system 00:02: ioport range 0xc00-0xc01 has been reserved
[    0.584068] system 00:02: ioport range 0xc14-0xc14 has been reserved
[    0.584069] system 00:02: ioport range 0xc50-0xc52 has been reserved
[    0.584071] system 00:02: ioport range 0xc6c-0xc6d has been reserved
[    0.584073] system 00:02: ioport range 0xc6f-0xc6f has been reserved
[    0.584075] system 00:02: ioport range 0xcd0-0xcd1 has been reserved
[    0.584077] system 00:02: ioport range 0xcd2-0xcd3 has been reserved
[    0.584079] system 00:02: ioport range 0xcd4-0xcdf has been reserved
[    0.584081] system 00:02: ioport range 0x4000-0x40fe has been reserved
[    0.584083] system 00:02: ioport range 0x4210-0x4217 has been reserved
[    0.584085] system 00:02: ioport range 0xb00-0xb0f has been reserved
[    0.584087] system 00:02: ioport range 0xb10-0xb1f has been reserved
[    0.584089] system 00:02: ioport range 0xb20-0xb3f has been reserved
[    0.584102] system 00:0d: iomem range 0xcd000-0xcffff has been reserved
[    0.584104] system 00:0d: iomem range 0xf0000-0xf7fff could not be reserved
[    0.584106] system 00:0d: iomem range 0xf8000-0xfbfff could not be reserved
[    0.584108] system 00:0d: iomem range 0xfc000-0xfffff could not be reserved
[    0.584110] system 00:0d: iomem range 0xcfee0000-0xcfefffff could not be reserved
[    0.584112] system 00:0d: iomem range 0x0-0x9ffff could not be reserved
[    0.584114] system 00:0d: iomem range 0x100000-0xcfedffff could not be reserved
[    0.589428] pci 0000:00:02.0: PCI bridge, secondary bus 0000:01
[    0.589431] pci 0000:00:02.0:   IO window: 0xe000-0xefff
[    0.589434] pci 0000:00:02.0:   MEM window: 0xf8000000-0xfbffffff
[    0.589436] pci 0000:00:02.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
[    0.589440] pci 0000:00:0a.0: PCI bridge, secondary bus 0000:02
[    0.589442] pci 0000:00:0a.0:   IO window: 0xd000-0xdfff
[    0.589445] pci 0000:00:0a.0:   MEM window: 0xfdc00000-0xfdcfffff
[    0.589447] pci 0000:00:0a.0:   PREFETCH window: 0x000000fdf00000-0x000000fdffffff
[    0.589451] pci 0000:00:14.4: PCI bridge, secondary bus 0000:03
[    0.589453] pci 0000:00:14.4:   IO window: 0xc000-0xcfff
[    0.589458] pci 0000:00:14.4:   MEM window: 0xfde00000-0xfdefffff
[    0.589462] pci 0000:00:14.4:   PREFETCH window: 0x000000fdd00000-0x000000fddfffff
[    0.589482] pci 0000:00:02.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.589485] pci 0000:00:02.0: setting latency timer to 64
[    0.589490] pci 0000:00:0a.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.589492] pci 0000:00:0a.0: setting latency timer to 64
[    0.589499] bus: 00 index 0 io port: [0, ffff]
[    0.589500] bus: 00 index 1 mmio: [0, ffffffffffffffff]
[    0.589502] bus: 01 index 0 io port: [e000, efff]
[    0.589503] bus: 01 index 1 mmio: [f8000000, fbffffff]
[    0.589505] bus: 01 index 2 mmio: [d0000000, dfffffff]
[    0.589506] bus: 01 index 3 mmio: [0, 0]
[    0.589507] bus: 02 index 0 io port: [d000, dfff]
[    0.589509] bus: 02 index 1 mmio: [fdc00000, fdcfffff]
[    0.589510] bus: 02 index 2 mmio: [fdf00000, fdffffff]
[    0.589511] bus: 02 index 3 mmio: [0, 0]
[    0.589513] bus: 03 index 0 io port: [c000, cfff]
[    0.589514] bus: 03 index 1 mmio: [fde00000, fdefffff]
[    0.589515] bus: 03 index 2 mmio: [fdd00000, fddfffff]
[    0.589517] bus: 03 index 3 io port: [0, ffff]
[    0.589518] bus: 03 index 4 mmio: [0, ffffffffffffffff]
[    0.589528] NET: Registered protocol family 2
[    0.628130] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.629303] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.632552] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.632973] TCP: Hash tables configured (established 524288 bind 65536)
[    0.632975] TCP reno registered
[    0.644103] NET: Registered protocol family 1
[    0.644189] checking if image is initramfs... it is
[    1.361422] Freeing initrd memory: 15982k freed
[    1.369703] audit: initializing netlink socket (disabled)
[    1.369714] type=2000 audit(1230778241.368:1): initialized
[    1.373949] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.376426] VFS: Disk quotas dquot_6.5.1
[    1.376501] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.376593] msgmni has been set to 7918
[    1.376696] io scheduler noop registered
[    1.376697] io scheduler anticipatory registered
[    1.376699] io scheduler deadline registered
[    1.376809] io scheduler cfq registered (default)
[    2.232016] pci 0000:00:13.0: OHCI: BIOS handoff failed (BIOS bug?) 00000184
[    2.288051] pci 0000:01:00.0: Boot video device
[    2.288191] pcieport-driver 0000:00:02.0: setting latency timer to 64
[    2.288212] pcieport-driver 0000:00:02.0: found MSI capability
[    2.288235] pci_express 0000:00:02.0:pcie00: allocate port service
[    2.288321] pcieport-driver 0000:00:0a.0: setting latency timer to 64
[    2.288341] pcieport-driver 0000:00:0a.0: found MSI capability
[    2.288360] pci_express 0000:00:0a.0:pcie00: allocate port service
[    2.324542] hpet_resources: 0xfed00000 is busy
[    2.324613] Linux agpgart interface v0.103
[    2.324617] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    2.324772] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    2.325409] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    2.327171] brd: module loaded
[    2.327238] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    2.327348] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    2.327349] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    2.327484] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.340327] mice: PS/2 mouse device common for all mice
[    2.340474] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    2.340511] rtc0: alarms up to one month, hpet irqs
[    2.340562] cpuidle: using governor ladder
[    2.340564] cpuidle: using governor menu
[    2.340844] TCP cubic registered
[    2.341082] registered taskstats version 1
[    2.341190]   Magic number: 9:39:813
[    2.341253] tty ptys7: hash matches
[    2.341259] tty ptypa: hash matches
[    2.341317] rtc_cmos 00:05: setting system clock to 2009-01-01 02:50:43 UTC (1230778243)
[    2.341319] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.341320] EDD information not available.
[    2.341354] Freeing unused kernel memory: 536k freed
[    2.341564] Write protecting the kernel read-only data: 4348k
[    2.361339] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    2.392793] vesafb: framebuffer at 0xf9000000, mapped to 0xffffc20011100000, using 3072k, total 14336k
[    2.392797] vesafb: mode is 1024x768x16, linelength=2048, pages=1
[    2.392798] vesafb: scrolling: redraw
[    2.392800] vesafb: Truecolor: size=0:5:6:5, shift=0:11:5:0
[    2.392979] Console: switching to colour frame buffer device 128x48
[    2.401013] fb0: VESA VGA frame buffer device
[    2.474947] fuse init (API version 7.9)
[    2.489077] processor ACPI0007:00: registered as cooling_device0
[    2.489146] processor ACPI0007:01: registered as cooling_device1
[    2.686559] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    2.686581] r8169 0000:02:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    2.686597] r8169 0000:02:00.0: setting latency timer to 64
[    2.686866] eth0: RTL8168c/8111c at 0xffffc20000630000, 00:1f:d0:86:08:df, XID 3c4000c0 IRQ 2301
[    2.692120] No dock devices found.
[    2.710644] SCSI subsystem initialized
[    2.739529] libata version 3.00 loaded.
[    2.745399] usbcore: registered new interface driver usbfs
[    2.745420] usbcore: registered new interface driver hub
[    2.745485] usbcore: registered new device driver usb
[    2.746643] pata_atiixp 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.749276] scsi0 : pata_atiixp
[    2.749408] scsi1 : pata_atiixp
[    2.750358] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xfa00 irq 14
[    2.750360] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xfa08 irq 15
[    2.752233] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.928554] ata1.00: ATAPI: ATAPI   DVD W  DH16W1P, LG12, max UDMA/66
[    2.960495] ata1.00: configured for UDMA/66
[    3.148368] ata2.00: HPA unlocked: 234439535 -> 234441648, native 234441648
[    3.148374] ata2.00: ATA-7: WDC WD1200JS-00NCB1, 10.02E02, max UDMA/133
[    3.148376] ata2.00: 234441648 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    3.156554] ata2.00: configured for UDMA/100
[    3.157638] scsi 0:0:0:0: CD-ROM            ATAPI    DVD W  DH16W1P   LG12 PQ: 0 ANSI: 5
[    3.157768] scsi 1:0:0:0: Direct-Access     ATA      WDC WD1200JS-00N 10.0 PQ: 0 ANSI: 5
[    3.157872] ahci 0000:00:11.0: version 3.0
[    3.157894] ahci 0000:00:11.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    3.158025] ahci 0000:00:11.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[    3.158028] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part 
[    3.158309] scsi2 : ahci
[    3.158391] scsi3 : ahci
[    3.158454] scsi4 : ahci
[    3.158512] scsi5 : ahci
[    3.158601] ata3: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f100 irq 2300
[    3.158604] ata4: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f180 irq 2300
[    3.158607] ata5: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f200 irq 2300
[    3.158610] ata6: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f280 irq 2300
[    3.476034] ata3: SATA link down (SStatus 0 SControl 300)
[    3.812035] ata4: SATA link down (SStatus 0 SControl 300)
[    4.148034] ata5: SATA link down (SStatus 0 SControl 300)
[    4.484033] ata6: SATA link down (SStatus 0 SControl 300)
[    4.500068] ohci_hcd 0000:00:12.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    4.500082] ohci_hcd 0000:00:12.0: OHCI Host Controller
[    4.500131] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 1
[    4.500165] ohci_hcd 0000:00:12.0: irq 16, io mem 0xfe02e000
[    4.560534] usb usb1: configuration #1 chosen from 1 choice
[    4.560938] hub 1-0:1.0: USB hub found
[    4.560949] hub 1-0:1.0: 3 ports detected
[    4.664782] ohci_hcd 0000:00:12.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    4.664797] ohci_hcd 0000:00:12.1: OHCI Host Controller
[    4.664819] ohci_hcd 0000:00:12.1: new USB bus registered, assigned bus number 2
[    4.664836] ohci_hcd 0000:00:12.1: irq 16, io mem 0xfe02d000
[    4.724602] usb usb2: configuration #1 chosen from 1 choice
[    4.725022] hub 2-0:1.0: USB hub found
[    4.725033] hub 2-0:1.0: 3 ports detected
[    4.932246] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    4.932261] ehci_hcd 0000:00:12.2: EHCI Host Controller
[    4.932283] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 3
[    4.932318] ehci_hcd 0000:00:12.2: debug port 1
[    4.932344] ehci_hcd 0000:00:12.2: irq 17, io mem 0xfe02c000
[    4.944016] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    4.944109] usb usb3: configuration #1 chosen from 1 choice
[    4.944131] hub 3-0:1.0: USB hub found
[    4.944138] hub 3-0:1.0: 6 ports detected
[    5.152218] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    5.152232] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    5.152253] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 4
[    5.152284] ohci_hcd 0000:00:13.0: irq 18, io mem 0xfe02b000
[    5.212651] usb usb4: configuration #1 chosen from 1 choice
[    5.212684] hub 4-0:1.0: USB hub found
[    5.212694] hub 4-0:1.0: 3 ports detected
[    5.317811] ohci_hcd 0000:00:13.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    5.317829] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    5.317864] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 5
[    5.317881] ohci_hcd 0000:00:13.1: irq 18, io mem 0xfe02a000
[    5.376129] usb usb5: configuration #1 chosen from 1 choice
[    5.376158] hub 5-0:1.0: USB hub found
[    5.376168] hub 5-0:1.0: 3 ports detected
[    5.584253] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    5.584267] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    5.584289] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 6
[    5.584324] ehci_hcd 0000:00:13.2: debug port 1
[    5.584350] ehci_hcd 0000:00:13.2: irq 19, io mem 0xfe029000
[    5.624021] usb 2-1: new low speed USB device using ohci_hcd and address 2
[    5.636019] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    5.636148] usb usb6: configuration #1 chosen from 1 choice
[    5.636172] hub 6-0:1.0: USB hub found
[    5.636180] hub 6-0:1.0: 6 ports detected
[    5.803804] usb 2-1: configuration #1 chosen from 1 choice
[    5.844350] ohci_hcd 0000:00:14.5: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    5.844364] ohci_hcd 0000:00:14.5: OHCI Host Controller
[    5.844384] ohci_hcd 0000:00:14.5: new USB bus registered, assigned bus number 7
[    5.844402] ohci_hcd 0000:00:14.5: irq 18, io mem 0xfe028000
[    5.908698] usb usb7: configuration #1 chosen from 1 choice
[    5.909275] hub 7-0:1.0: USB hub found
[    5.909287] hub 7-0:1.0: 2 ports detected
[    6.012938] ohci1394 0000:03:0e.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    6.044527] usb 6-6: new high speed USB device using ehci_hcd and address 2
[    6.062696] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[22]  MMIO=[fdeff000-fdeff7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    6.067535] scsi 0:0:0:0: Attached scsi generic sg0 type 5
[    6.067567] scsi 1:0:0:0: Attached scsi generic sg1 type 0
[    6.122357] Driver 'sr' needs updating - please use bus_type methods
[    6.125294] Driver 'sd' needs updating - please use bus_type methods
[    6.127136] sr0: scsi3-mmc drive: 94x/94x writer cd/rw xa/form2 cdda tray
[    6.127139] Uniform CD-ROM driver Revision: 3.20
[    6.127215] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    6.127312] sd 1:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[    6.127331] sd 1:0:0:0: [sda] Write Protect is off
[    6.127333] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    6.127364] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.127427] sd 1:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[    6.127443] sd 1:0:0:0: [sda] Write Protect is off
[    6.127444] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    6.127474] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.127477]  sda: sda1 sda2 sda3 < sda5 >
[    6.164485] sd 1:0:0:0: [sda] Attached SCSI disk
[    6.180981] usb 6-6: configuration #1 chosen from 1 choice
[    6.182049] usbcore: registered new interface driver hiddev
[    6.186385] input: Logitech Optical USB Mouse as /devices/pci0000:00/0000:00:12.1/usb2/2-1/2-1:1.0/input/input2
[    6.208159] input,hidraw0: USB HID v1.10 Mouse [Logitech Optical USB Mouse] on usb-0000:00:12.1-1
[    6.208182] usbcore: registered new interface driver usbhid
[    6.208185] usbhid: v2.6:USB HID core driver
[    6.397507] PM: Starting manual resume from disk
[    6.397510] PM: Resume from partition 8:5
[    6.397511] PM: Checking hibernation image.
[    6.397682] PM: Resume from disk failed.
[    6.445772] kjournald starting.  Commit interval 5 seconds
[    6.445786] EXT3-fs: mounted filesystem with ordered data mode.
[    7.332721] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[007538c800001fd0]
[   10.937708] udevd version 124 started
[   11.269599] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   11.299945] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   11.325246] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[   11.344550] ACPI: Power Button (FF) [PWRF]
[   11.344631] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input4
[   11.378393] ACPI: Power Button (CM) [PWRB]
[   11.394075] ACPI: WMI: Mapper loaded
[   11.447818] parport_pc 00:0a: reported by Plug and Play ACPI
[   11.447874] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   11.455676] ACPI: I/O resource piix4_smbus [0xb00-0xb07] conflicts with ACPI region SOR1 [0xb00-0xb0f]
[   11.455679] ACPI: Device needs an ACPI driver
[   11.455686] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0xb00, revision 0
[   11.778443] nvidia: module license 'NVIDIA' taints kernel.
[   12.048315] nvidia 0000:01:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   12.048322] nvidia 0000:01:00.0: setting latency timer to 64
[   12.049480] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  177.80  Wed Oct  1 14:43:46 PDT 2008
[   12.115281] input: PC Speaker as /devices/platform/pcspkr/input/input5
[   12.147781] usbcore: registered new interface driver cdc_ether
[   12.188616] usbcore: registered new interface driver rndis_host
[   12.229215] rndis_wlan 6-6:1.0: rndis media disconnect
[   12.229226] ------------[ cut here ]------------
[   12.229228] kernel BUG at /build/buildd/linux-2.6.27/kernel/workqueue.c:188!
[   12.229230] invalid opcode: 0000 [1] SMP 
[   12.229233] CPU 1 
[   12.229234] Modules linked in: rndis_wlan(+) soundcore rndis_host snd_page_alloc cdc_ether usbnet pcspkr(+) k8temp mii evdev nvidia(P) i2c_piix4 parport_pc parport wmi i2c_core button shpchp pci_hotplug ext3 jbd mbcache sd_mod sr_mod crc_t10dif cdrom usbhid hid sg ata_generic pata_acpi ohci1394 ehci_hcd ohci_hcd ahci pata_atiixp ieee1394 usbcore libata scsi_mod dock r8169 thermal processor fan fuse vesafb fbcon tileblit font bitblit softcursor
[   12.229262] Pid: 2701, comm: modprobe Tainted: P          2.6.27-9-generic #1
[   12.229264] RIP: 0010:[<ffffffff80263276>]  [<ffffffff80263276>] queue_work_on+0x56/0x60
[   12.229271] RSP: 0000:ffff8801295c1ad8  EFLAGS: 00010213
[   12.229273] RAX: ffff88012d1520a8 RBX: ffff88012d152800 RCX: ffff88012d1520a0
[   12.229275] RDX: 0000000000000000 RSI: 0000000000000000 RDI: 0000000000000001
[   12.229277] RBP: ffff8801295c1ad8 R08: 0000000000000000 R09: 0000000000000006
[   12.229279] R10: ffff8801295c1898 R11: ffff8801a95c19a7 R12: ffff88012a5c1000
[   12.229280] R13: ffff88012a560780 R14: 0000000080000002 R15: 0000000000000001
[   12.229282] FS:  00007fb0517216e0(0000) GS:ffff88012fc02980(0000) knlGS:0000000000000000
[   12.229284] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
[   12.229286] CR2: 00007fadd9d0c000 CR3: 000000012b909000 CR4: 00000000000006e0
[   12.229288] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
[   12.229290] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
[   12.229292] Process modprobe (pid: 2701, threadinfo ffff8801295c0000, task ffff88012a428000)
[   12.229293] Stack:  ffff8801295c1ae8 ffffffff8026339f ffff8801295c1af8 ffffffffa09d2176
[   12.229297]  ffff8801295c1b78 ffffffffa09c6442 ffff88012d152800 ffffffff00000401
[   12.229301]  ffff880100001388 000004012a560780 ffffffffa09c6cfc ffff88012a560900
[   12.229303] Call Trace:
[   12.229307]  [<ffffffff8026339f>] queue_work+0x1f/0x30
[   12.229312]  [<ffffffffa09d2176>] rndis_wext_link_change+0x36/0x40 [rndis_wlan]
[   12.229315]  [<ffffffffa09c6442>] rndis_command+0x1e2/0x2f0 [rndis_host]
[   12.229319]  [<ffffffffa09c68aa>] generic_rndis_bind+0x19a/0x4b0 [rndis_host]
[   12.229323]  [<ffffffff80467651>] ? alloc_netdev_mq+0x71/0x190
[   12.229326]  [<ffffffff802e1ecb>] ? kmem_cache_alloc+0x8b/0xd0
[   12.229330]  [<ffffffffa09d5605>] rndis_wext_bind+0xa5/0x268 [rndis_wlan]
[   12.229335]  [<ffffffffa09b43de>] usbnet_probe+0x27e/0x520 [usbnet]
[   12.229339]  [<ffffffff8034a2c9>] ? __sysfs_add_one+0x39/0xb0
[   12.229353]  [<ffffffffa00d27dd>] ? usb_match_one_id+0x3d/0xd0 [usbcore]
[   12.229357]  [<ffffffff80501139>] ? mutex_unlock+0x9/0x20
[   12.229366]  [<ffffffffa00d2f60>] ? usb_autopm_do_device+0xc0/0x110 [usbcore]
[   12.229375]  [<ffffffffa00d36fc>] usb_probe_interface+0xcc/0x180 [usbcore]
[   12.229379]  [<ffffffff80430542>] really_probe+0x72/0x1a0
[   12.229383]  [<ffffffff804306c0>] driver_probe_device+0x50/0x60
[   12.229385]  [<ffffffff8043075b>] __driver_attach+0x8b/0x90
[   12.229387]  [<ffffffff804306d0>] ? __driver_attach+0x0/0x90
[   12.229390]  [<ffffffff8042fccb>] bus_for_each_dev+0x6b/0xa0
[   12.229392]  [<ffffffff802e1ecb>] ? kmem_cache_alloc+0x8b/0xd0
[   12.229395]  [<ffffffff804303a1>] driver_attach+0x21/0x30
[   12.229397]  [<ffffffff8042f538>] bus_add_driver+0x1f8/0x270
[   12.229400]  [<ffffffff80430955>] driver_register+0x75/0x170
[   12.229409]  [<ffffffffa00d3a69>] usb_register_driver+0xa9/0x120 [usbcore]
[   12.229413]  [<ffffffffa00c5000>] ? rndis_wlan_init+0x0/0x25 [rndis_wlan]
[   12.229416]  [<ffffffffa00c5023>] rndis_wlan_init+0x23/0x25 [rndis_wlan]
[   12.229419]  [<ffffffff8020a041>] do_one_initcall+0x41/0x170
[   12.229422]  [<ffffffff8026c261>] ? __blocking_notifier_call_chain+0x21/0x90
[   12.229426]  [<ffffffff8027d085>] sys_init_module+0xb5/0x1f0
[   12.229429]  [<ffffffff8021285a>] system_call_fastpath+0x16/0x1b
[   12.229430] 
[   12.229431] 
[   12.229432] Code: 8b 5e 20 48 8b 06 48 89 ce 45 85 db 0f 45 3d ea c7 48 00 48 f7 d0 48 63 d7 48 8b 3c d0 e8 13 ff ff ff ba 01 00 00 00 c9 89 d0 c3 <0f> 0b eb fe 66 0f 1f 44 00 00 55 48 89 e5 e8 f7 f3 fa ff 48 89 
[   12.229456] RIP  [<ffffffff80263276>] queue_work_on+0x56/0x60
[   12.229459]  RSP <ffff8801295c1ad8>
[   12.229462] ---[ end trace 055dd2934ee64fa9 ]---
[   12.783369] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   12.814459] hda_codec: Unknown model for ALC882, trying auto-probe from BIOS...
[   14.941014] lp0: using parport0 (interrupt-driven).
[   15.096618] Adding 4803392k swap on /dev/sda5.  Priority:-1 extents:1 across:4803392k
[   15.645284] EXT3 FS on sda1, internal journal
[   16.569773] type=1505 audit(1230778257.738:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4124
[   16.690950] type=1505 audit(1230778257.858:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4129
[   16.691120] type=1505 audit(1230778257.858:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4129
[   16.828109] ip_tables: (C) 2000-2006 Netfilter Core Team
[   17.518149] powernow-k8: Found 1 AMD Athlon(tm) 64 X2 Dual Core Processor 5600+ processors (2 cpu cores) (version 2.20.00)
[   17.518219] powernow-k8:    0 : fid 0x15 (2900 MHz), vid 0x8
[   17.518222] powernow-k8:    1 : fid 0x14 (2800 MHz), vid 0x9
[   17.518223] powernow-k8:    2 : fid 0x12 (2600 MHz), vid 0xb
[   17.518225] powernow-k8:    3 : fid 0x10 (2400 MHz), vid 0xd
[   17.518226] powernow-k8:    4 : fid 0xe (2200 MHz), vid 0xf
[   17.518228] powernow-k8:    5 : fid 0xc (2000 MHz), vid 0x11
[   17.518229] powernow-k8:    6 : fid 0xa (1800 MHz), vid 0x11
[   17.518230] powernow-k8:    7 : fid 0x2 (1000 MHz), vid 0x12
[   18.188854] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   18.433322] ppdev: user-space parallel port driver
[   21.000520] Clocksource tsc unstable (delta = -92621195 ns)
[   25.345521] r8169: eth0: link down
[   29.693886] hda-intel: Invalid position buffer, using LPIB read method instead.
[   58.532516] UDF-fs: Partition marked readonly; forcing readonly mount
[   58.565729] UDF-fs INFO UDF: Mounting volume 'COD4MW', timestamp 2007/10/04 03:35 (1ed4)
[   73.251286] NET: Registered protocol family 10
[   73.264906] lo: Disabled Privacy Extensions
[   73.267052] ADDRCONF(NETDEV_UP): eth0: link is not ready

```

Hope it helps.

I would skim through it, but it is was too long for me. :D

---

### Post by unutbu on 2009-01-01
What is the make and model of your USB wireless device?

It appears from the output above that you are using the r8169 driver. 

Do I understand correctly that your USB wireless adapter was working, then something happened, and now it doesn't? 

Please post the output of 

```
ifconfig
iwconfig
iwlist scan
cat /etc/network/interfaces
```

Finally, what happens when you type
```
sudo /etc/init.d/networking restart
```
Do you get a connection?

---

### Post by HolySpagetty on 2009-01-01
I have a Buffalo WLI-U2-KG125S Keychain adapter.

And yes, something happened to make it not work, but I don't know what. I just turned it on and it didn't find a connection.

I will do those as soon as I can, thanks for your reply.

---

### Post by HolySpagetty on 2009-01-01
Here is the output of your first request:

```

sam@sam-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1f:d0:86:08:df  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:1516707008 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:253 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:376 (376.0 B)  TX bytes:376 (376.0 B)

sam@sam-desktop:~$ 
sam@sam-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sam@sam-desktop:~$ 
sam@sam-desktop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

sam@sam-desktop:~$ 
sam@sam-desktop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

```

From what I can see in that, it doesn't even detect my USB wireless's existence.
What can make it detect my USB?

And for the second command, did it twice, no luck.

---

### Post by unutbu on 2009-01-01
Unfortunately, I don't know for sure how to solve your problem.

Here are two possibilities:
[list]
[*]Perhaps a package update broke Linux's ability to recognize USB devices.
Oddly, I didn't see anything in your dmesg output which said Linux was having any problems with USB, but perhaps I don't understand dmesg output well enough.

It might be interesting to look at the output of this command:
```

lsmod | grep usb

```
You should see something like this:
```
usb_storage            81728  6 
usbhid                 35840  0 
hid                    50560  1 usbhid
libusual               27156  1 usb_storage
scsi_mod              155212  5 sr_mod,sd_mod,sg,usb_storage,libata
usbcore               148848  7 ndiswrapper,usb_storage,usbhid,libusual,ehci_hcd,uhci_hcd

```

These are the kernel modules in charge of handling USB devices. I don't know what each one does, but if you are missing something here, that might explain why the "lsusb" command was not returning any output, and why the wireless adapter is not getting recognized.

[*]Another possibility is that maybe, somehow your BIOS settings have gotten altered.
In this case, reboot and go to the BIOS menu. There are many different BIOSes, so you are going to have to poke around.

Look for any configuration option having to do with USB. If/when you find an option, write down what it currently is set to, and then try changing it. Reboot, and see if it helps.

Change only one option at a time. This is the only way to discover what solves the problem.

Take good notes so you can revert to your current settings (in case this is just a dead end). 
[/list]

---

### Post by HolySpagetty on 2009-01-01
I don't think it is BIOS because if it was, that would mean that my WinXP wireless wouldn't work right? Since I am using it on the same computer, different OS.

I will try that command though and look at the output, and try *lsusb* again.

---

### Post by HolySpagetty on 2009-01-01
```
lsusb
```
Did nothing again.

And here is the output of the other command:

```
sam@sam-desktop:~$ lsmod | grep usb
usbnet                 27272  3 rndis_wlan,rndis_host,cdc_ether
mii                    14592  1 usbnet
usbhid                 39776  0 
hid                    59072  1 usbhid
usbcore               175376  8 rndis_wlan,rndis_host,cdc_ether,usbnet,usbhid,ohci_hcd,ehci_hcd
```

---

### Post by HolySpagetty on 2009-01-01
Sorry for triple post, but, I looked back at:

```
sam@sam-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1f:d0:86:08:df  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:1516707008 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:253 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:376 (376.0 B)  TX bytes:376 (376.0 B)

sam@sam-desktop:~$ 
sam@sam-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sam@sam-desktop:~$ 
sam@sam-desktop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

sam@sam-desktop:~$ 
sam@sam-desktop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback
```

And thought that there should have been something else, to report a wireless connection.

It is only my network card (not wireless) and a local loop back.

Something is not right here!! :confused:

---

### Post by unutbu on 2009-01-01
Please post the output:

```

ls -l /var/log/messages*
cat /var/log/messages|grep usb|tail -n 25
```

---

### Post by HolySpagetty on 2009-01-01
Here ya go:

```
sam@sam-desktop:~$ ls -l /var/log/messages*
-rw-r----- 1 syslog adm 3261930 2009-01-01 18:53 /var/log/messages
-rw-r----- 1 syslog adm   52502 2008-12-27 19:38 /var/log/messages.0
sam@sam-desktop:~$ 
sam@sam-desktop:~$ cat /var/log/messages|grep usb|tail -n 25
Jan  1 18:52:33 sam-desktop kernel: [    5.092022] usb 4-3: new full speed USB device using ohci_hcd and address 2
Jan  1 18:52:33 sam-desktop kernel: [    5.104146] usb usb5: configuration #1 chosen from 1 choice
Jan  1 18:52:33 sam-desktop kernel: [    5.263069] usb 4-3: not running at top speed; connect to a high speed hub
Jan  1 18:52:33 sam-desktop kernel: [    5.275688] usb 4-3: configuration #1 chosen from 1 choice
Jan  1 18:52:33 sam-desktop kernel: [    5.280024] usb 2-1: USB disconnect, address 2
Jan  1 18:52:33 sam-desktop kernel: [    5.324117] usb usb6: configuration #1 chosen from 1 choice
Jan  1 18:52:33 sam-desktop kernel: [    5.464040] usb 4-3: USB disconnect, address 2
Jan  1 18:52:33 sam-desktop kernel: [    5.592771] usb usb7: configuration #1 chosen from 1 choice
Jan  1 18:52:33 sam-desktop kernel: [    5.704517] usb 6-6: new high speed USB device using ehci_hcd and address 2
Jan  1 18:52:33 sam-desktop kernel: [    5.839557] usb 6-6: configuration #1 chosen from 1 choice
Jan  1 18:52:33 sam-desktop kernel: [    6.100540] usb 2-1: new low speed USB device using ohci_hcd and address 3
Jan  1 18:52:33 sam-desktop kernel: [    6.274714] usb 2-1: configuration #1 chosen from 1 choice
Jan  1 18:52:33 sam-desktop kernel: [    6.277467] usbcore: registered new interface driver hiddev
Jan  1 18:52:33 sam-desktop kernel: [    6.281445] input: Logitech Optical USB Mouse as /devices/pci0000:00/0000:00:12.1/usb2/2-1/2-1:1.0/input/input2
Jan  1 18:52:33 sam-desktop kernel: [    6.308625] input,hidraw0: USB HID v1.10 Mouse [Logitech Optical USB Mouse] on usb-0000:00:12.1-1
Jan  1 18:52:33 sam-desktop kernel: [    6.308644] usbcore: registered new interface driver usbhid
Jan  1 18:52:33 sam-desktop kernel: [    6.308647] usbhid: v2.6:USB HID core driver
Jan  1 18:52:33 sam-desktop kernel: [   12.737900] usbcore: registered new interface driver cdc_ether
Jan  1 18:52:33 sam-desktop kernel: [   12.751821] usbcore: registered new interface driver rndis_host
Jan  1 18:52:33 sam-desktop kernel: [   12.813771] Modules linked in: rndis_wlan(+) snd_pcm rndis_host cdc_ether usbnet snd_seq_dummy k8temp pcspkr(+) mii snd_seq_oss evdev nvidia(P) snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device parport_pc parport wmi snd button i2c_piix4 i2c_core shpchp pci_hotplug soundcore snd_page_alloc ext3 jbd mbcache sr_mod cdrom sd_mod crc_t10dif usbhid hid ata_generic sg pata_acpi ohci1394 ieee1394 pata_atiixp ahci libata ehci_hcd ohci_hcd scsi_mod usbcore r8169 dock thermal processor fan fuse vesafb fbcon tileblit font bitblit softcursor
Jan  1 18:52:33 sam-desktop kernel: [   12.813868]  [<ffffffffa0a1b3de>] usbnet_probe+0x27e/0x520 [usbnet]
Jan  1 18:52:33 sam-desktop kernel: [   12.813888]  [<ffffffffa00717dd>] ? usb_match_one_id+0x3d/0xd0 [usbcore]
Jan  1 18:52:33 sam-desktop kernel: [   12.813901]  [<ffffffffa0071f60>] ? usb_autopm_do_device+0xc0/0x110 [usbcore]
Jan  1 18:52:33 sam-desktop kernel: [   12.813911]  [<ffffffffa00726fc>] usb_probe_interface+0xcc/0x180 [usbcore]
Jan  1 18:52:33 sam-desktop kernel: [   12.813945]  [<ffffffffa0072a69>] usb_register_driver+0xa9/0x120 [usbcore
```

Once again, I have no idea..

EDIT: Looking at this for the first time (after I posted this), I am thinking that maybe I should try putting the wireless adapter in the back ports? I don't know, it is just an idea..

---

### Post by unutbu on 2009-01-01
You know HolySpagetty, part of me would love to know how to fix this problem the "elegant" way. However, I just don't know the answer, and since you had a working wireless adapter before, it might be easier to backup your data and reinstall the operating system.

---

### Post by HolySpagetty on 2009-01-01
Okay, well uhh, will that keep all me cool themes and whatnot that I don't think I can live without?

---

### Post by HolySpagetty on 2009-01-01
SOLVED!!! :KS

Pluged it in the back USB and it worked...

Follow your first instinct everyone, the answer may be the simplest thing!

Don't know what is wrong with my front USB and Ubuntu, but there's some kind of conflict there.

Thank you for all your time unutbu. :)

---

### Post by unutbu on 2009-01-01
Congratulations, HolySpagetty! I'm so glad you solved it! :D

---

### Post by HolySpagetty on 2009-01-01
Wait, one problem though, it is super slow.

I am guessing since it is in the back, it gets a bad reception.

I don't know, but it is horribly slow.

And Ubuntu is what I use to surf the web and do random things that windows can't do as well. Other than play games, that's all I want to do on WinXP.

It kind of defeats the purpose since I'd rather go to WinXP to get a faster connection than to come here for eyecandy and get a slow connection..

Anyway to fix a SLOW connection?! :D

Or maybe a way to get Ubuntu to recognise my front USB ports?

---

