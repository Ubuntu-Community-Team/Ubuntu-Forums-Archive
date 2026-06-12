---
title: "Atheros/G45 lockup conflict"
date: 2008-11-23
forum: Networking &amp; Wireless
---

### Post by Mikka_au on 2008-11-23
I've just upgraded the motherboard in my htpc to one with a G45/ICH10R chipset ([Gigabyte GA-EG45M-DS2H]("http://www.gigabyte.com.tw/Products/Motherboard/Products_Spec.aspx?ClassValue=Motherboard&ProductID=2877&ProductName=GA-EG45M-DS2H")) and now the system locks up when the wireless modules are loaded. It was previously working using ndiswrapper on my old nforce4 system.

I've managed to get the system bootable by removing the card (a Netgear WG311v1) and blacklisting the modules (ath_hal, ath_pci, ath5k, ndiswrapper), then plugging the card back in, but obviously there is no network. If I attempt to modprobe any of the possible modules for the card (ath_pci, ath5k or ndiswrapper), the system hangs, with nothing logged anywhere I can find.

Does anyone have any suggestions for fixing the issue, or should I just grab a new card with a different chipset (eg, a Linksys WMP-54G)?

lspci -vvv
```
00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
	Subsystem: Giga-byte Technology Device 5000
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ >SERR- <PERR- INTx-
	Latency: 0
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
	Subsystem: Giga-byte Technology Device d000
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 3
	Region 0: Memory at e1000000 (64-bit, non-prefetchable) [size=4M]
	Region 2: Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Region 4: I/O ports at e200 [size=8]
	Capabilities: <access denied>

00:02.1 Display controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
	Subsystem: Giga-byte Technology Device d000
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Region 0: Memory at e1400000 (64-bit, non-prefetchable) [size=1M]
	Capabilities: <access denied>

00:1a.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4
	Subsystem: Giga-byte Technology Device 5004
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 16
	Region 4: I/O ports at e600 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1a.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5
	Subsystem: Giga-byte Technology Device 5004
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin B routed to IRQ 21
	Region 4: I/O ports at e000 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1a.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6
	Subsystem: Giga-byte Technology Device 5004
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin C routed to IRQ 18
	Region 4: I/O ports at e100 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1a.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2 (prog-if 20)
	Subsystem: Giga-byte Technology Device 5006
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin C routed to IRQ 18
	Region 0: Memory at e1705000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd
	Kernel modules: ehci-hcd

00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
	Subsystem: Giga-byte Technology Device a102
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 22
	Region 0: Memory at e1700000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 1
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 32 bytes
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 0000f000-00000fff
	Memory behind bridge: fff00000-000fffff
	Prefetchable memory behind bridge: 00000000fff00000-00000000000fffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.5 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 6
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 32 bytes
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 0000c000-0000cfff
	Memory behind bridge: e0000000-e0ffffff
	Prefetchable memory behind bridge: 00000000e1500000-00000000e15fffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1
	Subsystem: Giga-byte Technology Device 5004
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 23
	Region 4: I/O ports at e300 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2
	Subsystem: Giga-byte Technology Device 5004
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin B routed to IRQ 19
	Region 4: I/O ports at e400 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3
	Subsystem: Giga-byte Technology Device 5004
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin C routed to IRQ 18
	Region 4: I/O ports at e500 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1 (prog-if 20)
	Subsystem: Giga-byte Technology Device 5006
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 23
	Region 0: Memory at e1704000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd
	Kernel modules: ehci-hcd

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90) (prog-if 01)
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=32
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: e1600000-e16fffff
	Prefetchable memory behind bridge: 00000000fff00000-00000000000fffff
	Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801JIR (ICH10R) LPC Interface Controller
	Subsystem: Giga-byte Technology Device 5001
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Capabilities: <access denied>

00:1f.2 IDE interface: Intel Corporation 82801JI (ICH10 Family) 4 port SATA IDE Controller (prog-if 8a [Master SecP PriP])
	Subsystem: Giga-byte Technology Device b002
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin B routed to IRQ 19
	Region 0: I/O ports at 01f0 [size=8]
	Region 1: I/O ports at 03f4 [size=1]
	Region 2: I/O ports at 0170 [size=8]
	Region 3: I/O ports at 0374 [size=1]
	Region 4: I/O ports at f000 [size=16]
	Region 5: I/O ports at f100 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: ata_piix
	Kernel modules: ata_generic, ata_piix, pata_acpi

00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller
	Subsystem: Giga-byte Technology Device 5001
	Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Interrupt: pin C routed to IRQ 11
	Region 0: Memory at e1706000 (64-bit, non-prefetchable) [size=256]
	Region 4: I/O ports at 0500 [size=32]
	Kernel modules: i2c-i801

00:1f.5 IDE interface: Intel Corporation 82801JI (ICH10 Family) 2 port SATA IDE Controller (prog-if 85 [Master SecO PriO])
	Subsystem: Giga-byte Technology Device b002
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin B routed to IRQ 19
	Region 0: I/O ports at e800 [size=8]
	Region 1: I/O ports at e900 [size=4]
	Region 2: I/O ports at ea00 [size=8]
	Region 3: I/O ports at eb00 [size=4]
	Region 4: I/O ports at ec00 [size=16]
	Region 5: I/O ports at ed00 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: ata_piix
	Kernel modules: ata_generic, ata_piix, pata_acpi

02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
	Subsystem: Giga-byte Technology Device e000
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 2301
	Region 0: I/O ports at c000 [size=256]
	Region 2: Memory at e1510000 (64-bit, prefetchable) [size=4K]
	Region 4: Memory at e1500000 (64-bit, prefetchable) [size=64K]
	[virtual] Expansion ROM at e1520000 [disabled] [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: r8169
	Kernel modules: r8169

03:00.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 62)
	Subsystem: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 32, Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 20
	Region 4: I/O ports at d000 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

03:00.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 62)
	Subsystem: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 32, Cache Line Size: 32 bytes
	Interrupt: pin B routed to IRQ 19
	Region 4: I/O ports at d100 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

03:00.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 65) (prog-if 20)
	Subsystem: VIA Technologies, Inc. USB 2.0
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 32, Cache Line Size: 32 bytes
	Interrupt: pin C routed to IRQ 18
	Region 0: Memory at e1615000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd
	Kernel modules: ehci-hcd

03:01.0 Ethernet controller: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01)
	Subsystem: Netgear Device 4900
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64 (2500ns min, 7000ns max), Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 11
	Region 0: Memory at e1600000 (32-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel modules: ath_pci, ath5k

03:05.0 IDE interface: Integrated Technology Express, Inc. IT8213 IDE Controller (prog-if 85 [Master SecO PriO])
	Subsystem: Giga-byte Technology Device b000
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64 (2000ns min, 2000ns max)
	Interrupt: pin A routed to IRQ 21
	Region 0: I/O ports at d200 [size=8]
	Region 1: I/O ports at d300 [size=4]
	Region 2: I/O ports at d400 [size=8]
	Region 3: I/O ports at d500 [size=4]
	Region 4: I/O ports at d600 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: pata_it8213
	Kernel modules: ata_generic, pata_acpi, pata_it8213

03:07.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link) (prog-if 10)
	Subsystem: Giga-byte Technology Device 1000
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 32 (500ns min, 1000ns max), Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 23
	Region 0: Memory at e1614000 (32-bit, non-prefetchable) [size=2K]
	Region 1: Memory at e1610000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: ohci1394
	Kernel modules: ohci1394


```

dmesg:
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.27-7-generic (buildd@crested) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Tue Nov 4 19:33:06 UTC 2008 (Ubuntu 2.6.27-7.16-generic)
[    0.000000] Command line: root=UUID=09cceaf5-9537-40db-a972-f6e251f2686e ro quiet splash 
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007bcb0000 (usable)
[    0.000000]  BIOS-e820: 000000007bcb0000 - 000000007bce3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007bce3000 - 000000007bcf0000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007bcf0000 - 000000007bd00000 (reserved)
[    0.000000]  BIOS-e820: 00000000c0000000 - 00000000d0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] last_pfn = 0x7bcb0 max_arch_pfn = 0x3ffffffff
[    0.000000] init_memory_mapping
[    0.000000]  0000000000 - 007bc00000 page 2M
[    0.000000]  007bc00000 - 007bcb0000 page 4k
[    0.000000] kernel direct mapping tables up to 7bcb0000 @ 8000-c000
[    0.000000] last_map_addr: 7bcb0000 end: 7bcb0000
[    0.000000] RAMDISK: 3772a000 - 37fefc5d
[    0.000000] DMI 2.4 present.
[    0.000000] ACPI: RSDP 000F75E0, 0014 (r0 GBT   )
[    0.000000] ACPI: RSDT 7BCE3040, 0048 (r1 GBT    GBTUACPI 42302E31 GBTU  1010101)
[    0.000000] ACPI: FACP 7BCE30C0, 0074 (r1 GBT    GBTUACPI 42302E31 GBTU  1010101)
[    0.000000] ACPI: DSDT 7BCE3180, 49ED (r1 GBT    GBTUACPI     1000 MSFT  100000C)
[    0.000000] ACPI: FACS 7BCB0000, 0040
[    0.000000] ACPI: HPET 7BCE7CC0, 0038 (r1 GBT    GBTUACPI 42302E31 GBTU       98)
[    0.000000] ACPI: MCFG 7BCE7D40, 003C (r1 GBT    GBTUACPI 42302E31 GBTU  1010101)
[    0.000000] ACPI: APIC 7BCE7BC0, 0084 (r1 GBT    GBTUACPI 42302E31 GBTU  1010101)
[    0.000000] ACPI: SSDT 7BCE8460, 018A (r1  PmRef  Cpu0Cst     3001 INTL 20040311)
[    0.000000] ACPI: SSDT 7BCE85F0, 018A (r1  PmRef  Cpu1Cst     3001 INTL 20040311)
[    0.000000] ACPI: SSDT 7BCE8780, 018A (r1  PmRef  Cpu2Cst     3001 INTL 20040311)
[    0.000000] ACPI: SSDT 7BCE8910, 018A (r1  PmRef  Cpu3Cst     3001 INTL 20040311)
[    0.000000] ACPI: SSDT 7BCE8AA0, 03AB (r1  PmRef    CpuPm     3000 INTL 20040311)
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-000000007bcb0000
[    0.000000] Bootmem setup node 0 0000000000000000-000000007bcb0000
[    0.000000]   NODE_DATA [0000000000001000 - 0000000000005fff]
[    0.000000]   bootmap [000000000000a000 -  0000000000019797] pages 10
[    0.000000] (6 early reservations) ==> bootmem [0000000000 - 007bcb0000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
[    0.000000]   #2 [0000200000 - 00008b8f9c]    TEXT DATA BSS ==> [0000200000 - 00008b8f9c]
[    0.000000]   #3 [003772a000 - 0037fefc5d]          RAMDISK ==> [003772a000 - 0037fefc5d]
[    0.000000]   #4 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000]
[    0.000000]   #5 [0000008000 - 000000a000]          PGTABLE ==> [0000008000 - 000000a000]
[    0.000000] found SMP MP-table at [ffff8800000f57b0] 000f57b0
[    0.000000]  [ffffe20000000000-ffffe20001ffffff] PMD -> [ffff880001200000-ffff8800031fffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00100000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0007bcb0
[    0.000000] On node 0 totalpages: 506959
[    0.000000]   DMA zone: 2112 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 495101 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x408
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
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Setting APIC routing to flat
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 7bd00000:44300000)
[    0.000000] PERCPU: Allocating 64928 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 4, nr_node_ids 1
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 497213
[    0.000000] Policy zone: DMA32
[    0.000000] Kernel command line: root=UUID=09cceaf5-9537-40db-a972-f6e251f2686e ro quiet splash 
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] TSC: PIT calibration confirmed by PMTIMER.
[    0.000000] TSC: using PMTIMER calibration value
[    0.000000] Detected 2999.657 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Checking aperture...
[    0.004000] No AGP bridge found
[    0.004000] Calgary: detecting Calgary via BIOS EBDA area
[    0.004000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.004000] Memory: 1978772k/2028224k available (3112k kernel code, 49064k reserved, 1575k data, 536k init)
[    0.004000] CPA: page pool initialized 1 of 1 pages preallocated
[    0.004000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.004000] hpet clockevent registered
[    0.004000] Calibrating delay loop (skipped), value calculated using timer frequency.. 5999.31 BogoMIPS (lpj=11998628)
[    0.004000] Security Framework initialized
[    0.004000] SELinux:  Disabled at boot.
[    0.004000] AppArmor: AppArmor initialized
[    0.004000] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.004000] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.004000] Mount-cache hash table entries: 256
[    0.004000] Initializing cgroup subsys ns
[    0.004000] Initializing cgroup subsys cpuacct
[    0.004000] Initializing cgroup subsys memory
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 6144K
[    0.004000] CPU 0/0 -> Node 0
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 0
[    0.004000] CPU0: Thermal monitoring enabled (TM2)
[    0.004000] using mwait in idle threads.
[    0.004000] ACPI: Core revision 20080609
[    0.004980] ACPI: Checking initramfs for custom DSDT
[    0.274171] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.313866] CPU0: Intel(R) Core(TM)2 Duo CPU     E8400  @ 3.00GHz stepping 0a
[    0.313868] Using local APIC timer interrupts.
[    0.316020] APIC timer calibration result 20831018
[    0.316021] Detected 20.831 MHz APIC timer.
[    0.316116] Booting processor 1/1 ip 6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 5999.38 BogoMIPS (lpj=11998767)
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 6144K
[    0.004000] CPU 1/1 -> Node 0
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.004000] CPU1: Thermal monitoring enabled (TM2)
[    0.404748] CPU1: Intel(R) Core(TM)2 Duo CPU     E8400  @ 3.00GHz stepping 0a
[    0.404763] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.408057] Brought up 2 CPUs
[    0.408059] Total of 2 processors activated (11998.69 BogoMIPS).
[    0.408099] CPU0 attaching sched-domain:
[    0.408101]  domain 0: span 0-1 level MC
[    0.408102]   groups: 0 1
[    0.408104]   domain 1: span 0-1 level NODE
[    0.408106]    groups: 0-1
[    0.408110] CPU1 attaching sched-domain:
[    0.408111]  domain 0: span 0-1 level MC
[    0.408112]   groups: 1 0
[    0.408113]   domain 1: span 0-1 level NODE
[    0.408115]    groups: 0-1
[    0.408182] net_namespace: 1552 bytes
[    0.408182] Booting paravirtualized kernel on bare hardware
[    0.408216] Time: 13:05:38  Date: 11/23/08
[    0.408240] NET: Registered protocol family 16
[    0.408252] ACPI: bus type pci registered
[    0.408252] PCI: MCFG configuration 0: base c0000000 segment 0 buses 0 - 255
[    0.408252] PCI: MCFG area at c0000000 reserved in E820
[    0.414994] PCI: Using MMCONFIG at c0000000 - cfffffff
[    0.414995] PCI: Using configuration type 1 for base access
[    0.415005] ACPI: EC: Look up EC in DSDT
[    0.420389] ACPI: Interpreter enabled
[    0.420392] ACPI: (supports S0 S3 S4 S5)
[    0.420404] ACPI: Using IOAPIC for interrupt routing
[    0.424112] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.424112] PCI: 0000:00:02.0 reg 10 64bit mmio: [e1000000, e13fffff]
[    0.424112] PCI: 0000:00:02.0 reg 18 32bit mmio: [d0000000, dfffffff]
[    0.424112] PCI: 0000:00:02.0 reg 20 io port: [e200, e207]
[    0.424112] PCI: 0000:00:02.1 reg 10 64bit mmio: [e1400000, e14fffff]
[    0.424155] PCI: 0000:00:1a.0 reg 20 io port: [e600, e61f]
[    0.424202] PCI: 0000:00:1a.1 reg 20 io port: [e000, e01f]
[    0.424250] PCI: 0000:00:1a.2 reg 20 io port: [e100, e11f]
[    0.424289] PCI: 0000:00:1a.7 reg 10 32bit mmio: [e1705000, e17053ff]
[    0.424344] PCI: 0000:00:1b.0 reg 10 64bit mmio: [e1700000, e1703fff]
[    0.424371] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.424374] pci 0000:00:1b.0: PME# disabled
[    0.424408] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.424411] pci 0000:00:1c.0: PME# disabled
[    0.424447] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    0.424450] pci 0000:00:1c.5: PME# disabled
[    0.424483] PCI: 0000:00:1d.0 reg 20 io port: [e300, e31f]
[    0.424530] PCI: 0000:00:1d.1 reg 20 io port: [e400, e41f]
[    0.424576] PCI: 0000:00:1d.2 reg 20 io port: [e500, e51f]
[    0.424615] PCI: 0000:00:1d.7 reg 10 32bit mmio: [e1704000, e17043ff]
[    0.424754] PCI: 0000:00:1f.2 reg 10 io port: [0, 7]
[    0.424758] PCI: 0000:00:1f.2 reg 14 io port: [0, 3]
[    0.424762] PCI: 0000:00:1f.2 reg 18 io port: [0, 7]
[    0.424766] PCI: 0000:00:1f.2 reg 1c io port: [0, 3]
[    0.424770] PCI: 0000:00:1f.2 reg 20 io port: [f000, f00f]
[    0.424773] PCI: 0000:00:1f.2 reg 24 io port: [f100, f10f]
[    0.424799] PCI: 0000:00:1f.3 reg 10 64bit mmio: [e1706000, e17060ff]
[    0.424809] PCI: 0000:00:1f.3 reg 20 io port: [500, 51f]
[    0.424839] PCI: 0000:00:1f.5 reg 10 io port: [e800, e807]
[    0.424843] PCI: 0000:00:1f.5 reg 14 io port: [e900, e903]
[    0.424847] PCI: 0000:00:1f.5 reg 18 io port: [ea00, ea07]
[    0.424851] PCI: 0000:00:1f.5 reg 1c io port: [eb00, eb03]
[    0.424855] PCI: 0000:00:1f.5 reg 20 io port: [ec00, ec0f]
[    0.424859] PCI: 0000:00:1f.5 reg 24 io port: [ed00, ed0f]
[    0.424941] PCI: 0000:02:00.0 reg 10 io port: [c000, c0ff]
[    0.424953] PCI: 0000:02:00.0 reg 18 32bit mmio: [e1510000, e1510fff]
[    0.424964] PCI: 0000:02:00.0 reg 20 32bit mmio: [e1500000, e150ffff]
[    0.424976] PCI: 0000:02:00.0 reg 30 32bit mmio: [0, ffff]
[    0.424999] pci 0000:02:00.0: supports D1
[    0.425000] pci 0000:02:00.0: supports D2
[    0.425001] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.425004] pci 0000:02:00.0: PME# disabled
[    0.425028] PCI: bridge 0000:00:1c.5 io port: [c000, cfff]
[    0.425031] PCI: bridge 0000:00:1c.5 32bit mmio: [e0000000, e0ffffff]
[    0.425035] PCI: bridge 0000:00:1c.5 64bit mmio pref: [e1500000, e15fffff]
[    0.425076] PCI: 0000:03:00.0 reg 20 io port: [d000, d01f]
[    0.425094] pci 0000:03:00.0: supports D1
[    0.425095] pci 0000:03:00.0: supports D2
[    0.425096] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot
[    0.425099] pci 0000:03:00.0: PME# disabled
[    0.425137] PCI: 0000:03:00.1 reg 20 io port: [d100, d11f]
[    0.425155] pci 0000:03:00.1: supports D1
[    0.425156] pci 0000:03:00.1: supports D2
[    0.425157] pci 0000:03:00.1: PME# supported from D0 D1 D2 D3hot
[    0.425160] pci 0000:03:00.1: PME# disabled
[    0.425181] PCI: 0000:03:00.2 reg 10 32bit mmio: [e1615000, e16150ff]
[    0.425215] pci 0000:03:00.2: supports D1
[    0.425216] pci 0000:03:00.2: supports D2
[    0.425217] pci 0000:03:00.2: PME# supported from D0 D1 D2 D3hot
[    0.425220] pci 0000:03:00.2: PME# disabled
[    0.425247] PCI: 0000:03:01.0 reg 10 32bit mmio: [e1600000, e160ffff]
[    0.425306] PCI: 0000:03:05.0 reg 10 io port: [d200, d207]
[    0.425310] PCI: 0000:03:05.0 reg 14 io port: [d300, d303]
[    0.425315] PCI: 0000:03:05.0 reg 18 io port: [d400, d407]
[    0.425320] PCI: 0000:03:05.0 reg 1c io port: [d500, d503]
[    0.425325] PCI: 0000:03:05.0 reg 20 io port: [d600, d60f]
[    0.425366] PCI: 0000:03:07.0 reg 10 32bit mmio: [e1614000, e16147ff]
[    0.425371] PCI: 0000:03:07.0 reg 14 32bit mmio: [e1610000, e1613fff]
[    0.425403] pci 0000:03:07.0: supports D1
[    0.425404] pci 0000:03:07.0: supports D2
[    0.425405] pci 0000:03:07.0: PME# supported from D0 D1 D2 D3hot
[    0.425408] pci 0000:03:07.0: PME# disabled
[    0.425433] pci 0000:00:1e.0: transparent bridge
[    0.425436] PCI: bridge 0000:00:1e.0 io port: [d000, dfff]
[    0.425438] PCI: bridge 0000:00:1e.0 32bit mmio: [e1600000, e16fffff]
[    0.425455] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.425661] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]
[    0.425737] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX5._PRT]
[    0.425808] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[    0.440103] ACPI: PCI Interrupt Link [LNKA] (IRQs *3 4 5 6 7 9 10 11 12 14 15)
[    0.440192] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[    0.440277] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[    0.440363] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[    0.440448] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[    0.440533] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[    0.440618] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[    0.440703] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 *6 7 9 10 11 12 14 15)
[    0.440743] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.440743] pnp: PnP ACPI init
[    0.440743] ACPI: bus type pnp registered
[    0.440743] pnp: PnP ACPI: found 13 devices
[    0.440743] ACPI: ACPI bus type pnp unregistered
[    0.440743] PCI: Using ACPI for IRQ routing
[    0.460036] NET: Registered protocol family 8
[    0.460038] NET: Registered protocol family 20
[    0.460051] NetLabel: Initializing
[    0.460051] NetLabel:  domain hash size = 128
[    0.460051] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.460061] NetLabel:  unlabeled traffic allowed by default
[    0.460081] PCI-GART: No AMD northbridge found.
[    0.460085] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.460089] hpet0: 4 64-bit timers, 14318180 Hz
[    0.462673] tracer: 1286 pages allocated for 65536 entries of 80 bytes
[    0.462674]    actual entries 65586
[    0.462733] AppArmor: AppArmor Filesystem Enabled
[    0.462748] ACPI: RTC can wake from S4
[    0.476017] system 00:01: ioport range 0x4d0-0x4d1 has been reserved
[    0.476020] system 00:01: ioport range 0x290-0x29f has been reserved
[    0.476022] system 00:01: ioport range 0x800-0x805 has been reserved
[    0.476024] system 00:01: ioport range 0x290-0x294 has been reserved
[    0.476027] system 00:01: ioport range 0x880-0x88f has been reserved
[    0.476029] system 00:01: ioport range 0x4c0-0x4ff could not be reserved
[    0.476037] system 00:09: ioport range 0x400-0x4bf has been reserved
[    0.476045] system 00:0a: iomem range 0xc0000000-0xcfffffff could not be reserved
[    0.476050] system 00:0b: iomem range 0xcc600-0xcffff has been reserved
[    0.476052] system 00:0b: iomem range 0xf0000-0xf7fff could not be reserved
[    0.476054] system 00:0b: iomem range 0xf8000-0xfbfff could not be reserved
[    0.476057] system 00:0b: iomem range 0xfc000-0xfffff could not be reserved
[    0.476059] system 00:0b: iomem range 0x7bcb0000-0x7bcfffff could not be reserved
[    0.476061] system 00:0b: iomem range 0x0-0x9ffff could not be reserved
[    0.476063] system 00:0b: iomem range 0x100000-0x7bcaffff could not be reserved
[    0.476066] system 00:0b: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.476068] system 00:0b: iomem range 0xfed10000-0xfed1dfff could not be reserved
[    0.476071] system 00:0b: iomem range 0xfed20000-0xfed8ffff could not be reserved
[    0.476073] system 00:0b: iomem range 0xfee00000-0xfee00fff could not be reserved
[    0.476075] system 00:0b: iomem range 0xffb00000-0xffb7ffff could not be reserved
[    0.476078] system 00:0b: iomem range 0xfff00000-0xffffffff could not be reserved
[    0.476080] system 00:0b: iomem range 0xe0000-0xeffff has been reserved
[    0.480929] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:01
[    0.480931] pci 0000:00:1c.0:   IO window: disabled
[    0.480934] pci 0000:00:1c.0:   MEM window: disabled
[    0.480936] pci 0000:00:1c.0:   PREFETCH window: disabled
[    0.480942] pci 0000:00:1c.5: PCI bridge, secondary bus 0000:02
[    0.480944] pci 0000:00:1c.5:   IO window: 0xc000-0xcfff
[    0.480947] pci 0000:00:1c.5:   MEM window: 0xe0000000-0xe0ffffff
[    0.480949] pci 0000:00:1c.5:   PREFETCH window: 0x000000e1500000-0x000000e15fffff
[    0.480954] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:03
[    0.480956] pci 0000:00:1e.0:   IO window: 0xd000-0xdfff
[    0.480959] pci 0000:00:1e.0:   MEM window: 0xe1600000-0xe16fffff
[    0.480962] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.480972] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.480975] pci 0000:00:1c.0: setting latency timer to 64
[    0.480981] pci 0000:00:1c.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.480984] pci 0000:00:1c.5: setting latency timer to 64
[    0.480988] pci 0000:00:1e.0: setting latency timer to 64
[    0.480990] bus: 00 index 0 io port: [0, ffff]
[    0.480991] bus: 00 index 1 mmio: [0, ffffffffffffffff]
[    0.480992] bus: 01 index 0 mmio: [0, 0]
[    0.480993] bus: 01 index 1 mmio: [0, 0]
[    0.480994] bus: 01 index 2 mmio: [0, 0]
[    0.480995] bus: 01 index 3 mmio: [0, 0]
[    0.480996] bus: 02 index 0 io port: [c000, cfff]
[    0.480997] bus: 02 index 1 mmio: [e0000000, e0ffffff]
[    0.480998] bus: 02 index 2 mmio: [e1500000, e15fffff]
[    0.480999] bus: 02 index 3 mmio: [0, 0]
[    0.481000] bus: 03 index 0 io port: [d000, dfff]
[    0.481001] bus: 03 index 1 mmio: [e1600000, e16fffff]
[    0.481002] bus: 03 index 2 mmio: [0, 0]
[    0.481003] bus: 03 index 3 io port: [0, ffff]
[    0.481004] bus: 03 index 4 mmio: [0, ffffffffffffffff]
[    0.481011] NET: Registered protocol family 2
[    0.500718] Switched to high resolution mode on CPU 1
[    0.503950] Switched to high resolution mode on CPU 0
[    0.520099] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
[    0.520563] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
[    0.521646] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.522004] TCP: Hash tables configured (established 262144 bind 65536)
[    0.522005] TCP reno registered
[    0.532085] NET: Registered protocol family 1
[    0.532183] checking if image is initramfs... it is
[    1.076433] Freeing initrd memory: 8983k freed
[    1.079862] audit: initializing netlink socket (disabled)
[    1.079887] type=2000 audit(1227445538.076:1): initialized
[    1.083905] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.085493] VFS: Disk quotas dquot_6.5.1
[    1.085545] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.085614] msgmni has been set to 3882
[    1.085690] io scheduler noop registered
[    1.085692] io scheduler anticipatory registered
[    1.085693] io scheduler deadline registered
[    1.085769] io scheduler cfq registered (default)
[    1.085780] pci 0000:00:02.0: Boot video device
[    1.085992] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    1.086017] pcieport-driver 0000:00:1c.0: found MSI capability
[    1.086043] pci_express 0000:00:1c.0:pcie00: allocate port service
[    1.086070] pci_express 0000:00:1c.0:pcie02: allocate port service
[    1.086095] pci_express 0000:00:1c.0:pcie03: allocate port service
[    1.086154] pcieport-driver 0000:00:1c.5: setting latency timer to 64
[    1.086178] pcieport-driver 0000:00:1c.5: found MSI capability
[    1.086201] pci_express 0000:00:1c.5:pcie00: allocate port service
[    1.086226] pci_express 0000:00:1c.5:pcie02: allocate port service
[    1.086250] pci_express 0000:00:1c.5:pcie03: allocate port service
[    1.106115] hpet_resources: 0xfed00000 is busy
[    1.106171] Linux agpgart interface v0.103
[    1.106196] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.106317] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.106744] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.107883] brd: module loaded
[    1.107933] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    1.108115] PNP: No PS/2 controller found. Probing ports directly.
[    1.108427] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.108433] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.120225] mice: PS/2 mouse device common for all mice
[    1.120301] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    1.120322] rtc0: alarms up to one month, hpet irqs
[    1.120345] cpuidle: using governor ladder
[    1.120347] cpuidle: using governor menu
[    1.120595] TCP cubic registered
[    1.120717] registered taskstats version 1
[    1.120816]   Magic number: 0:650:79
[    1.120897] rtc_cmos 00:04: setting system clock to 2008-11-23 13:05:38 UTC (1227445538)
[    1.120899] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.120900] EDD information not available.
[    1.120923] Freeing unused kernel memory: 536k freed
[    1.121113] Write protecting the kernel read-only data: 4348k
[    1.199110] fuse init (API version 7.9)
[    1.270707] ACPI: SSDT 7BCE7E40, 022A (r1  PmRef  Cpu0Ist     3000 INTL 20040311)
[    1.271013] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    1.271054] processor ACPI0007:00: registered as cooling_device0
[    1.271057] ACPI: Processor [CPU0] (supports 8 throttling states)
[    1.271195] ACPI: SSDT 7BCE8300, 0152 (r1  PmRef  Cpu1Ist     3000 INTL 20040311)
[    1.271416] ACPI Error (psparse-0530): Method parse/execution failed [\_PR_.CPU1._PDC] (Node ffff88007bb36f60), AE_ALREADY_EXISTS
[    1.271421] ACPI: Marking method _PDC as Serialized because of AE_ALREADY_EXISTS error
[    1.271525] Marking TSC unstable due to TSC halts in idle
[    1.271650] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    1.271682] processor ACPI0007:01: registered as cooling_device1
[    1.271684] ACPI: Processor [CPU1] (supports 8 throttling states)
[    1.280961] device-mapper: uevent: version 1.0.3
[    1.281095] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
[    1.459758] usbcore: registered new interface driver usbfs
[    1.459773] usbcore: registered new interface driver hub
[    1.459804] usbcore: registered new device driver usb
[    1.460851] USB Universal Host Controller Interface driver v3.0
[    1.460886] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.460893] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    1.460895] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    1.460921] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    1.460949] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000e600
[    1.461049] usb usb1: configuration #1 chosen from 1 choice
[    1.461064] hub 1-0:1.0: USB hub found
[    1.461067] hub 1-0:1.0: 2 ports detected
[    1.508879] No dock devices found.
[    1.520667] SCSI subsystem initialized
[    1.541304] libata version 3.00 loaded.
[    1.672949] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    1.672957] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    1.672960] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    1.672984] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
[    1.673011] uhci_hcd 0000:00:1a.1: irq 21, io base 0x0000e000
[    1.673068] usb usb2: configuration #1 chosen from 1 choice
[    1.673084] hub 2-0:1.0: USB hub found
[    1.673088] hub 2-0:1.0: 2 ports detected
[    1.776839] uhci_hcd 0000:00:1a.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.776846] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[    1.776849] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    1.776865] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 3
[    1.776892] uhci_hcd 0000:00:1a.2: irq 18, io base 0x0000e100
[    1.776950] usb usb3: configuration #1 chosen from 1 choice
[    1.776965] hub 3-0:1.0: USB hub found
[    1.776969] hub 3-0:1.0: 2 ports detected
[    1.788018] usb 1-1: new low speed USB device using uhci_hcd and address 2
[    1.880749] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.880761] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    1.880764] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    1.880784] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 4
[    1.884670] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    1.884674] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xe1705000
[    1.916020] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    1.916086] usb usb4: configuration #1 chosen from 1 choice
[    1.916111] hub 4-0:1.0: USB hub found
[    1.916117] hub 4-0:1.0: 6 ports detected
[    2.124163] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    2.124169] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    2.124177] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    2.124196] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    2.124221] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000e300
[    2.124272] usb usb5: configuration #1 chosen from 1 choice
[    2.124287] hub 5-0:1.0: USB hub found
[    2.124291] hub 5-0:1.0: 2 ports detected
[    2.228167] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    2.228177] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    2.228179] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    2.228193] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    2.228216] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000e400
[    2.228269] usb usb6: configuration #1 chosen from 1 choice
[    2.228283] hub 6-0:1.0: USB hub found
[    2.228287] hub 6-0:1.0: 2 ports detected
[    2.316035] usb 1-1: device not accepting address 2, error -71
[    2.332777] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    2.332781] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    2.332783] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    2.332800] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    2.332819] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000e500
[    2.332870] usb usb7: configuration #1 chosen from 1 choice
[    2.332886] hub 7-0:1.0: USB hub found
[    2.332889] hub 7-0:1.0: 2 ports detected
[    2.372046] hub 1-0:1.0: unable to enumerate USB device on port 1
[    2.437425] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    2.437430] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    2.437432] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    2.437781] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 8
[    2.441675] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    2.441678] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xe1704000
[    2.456020] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    2.456455] usb usb8: configuration #1 chosen from 1 choice
[    2.456816] hub 8-0:1.0: USB hub found
[    2.456820] hub 8-0:1.0: 6 ports detected
[    2.560911] uhci_hcd 0000:03:00.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    2.560916] uhci_hcd 0000:03:00.0: UHCI Host Controller
[    2.560932] uhci_hcd 0000:03:00.0: new USB bus registered, assigned bus number 9
[    2.560955] uhci_hcd 0000:03:00.0: irq 20, io base 0x0000d000
[    2.561006] usb usb9: configuration #1 chosen from 1 choice
[    2.561021] hub 9-0:1.0: USB hub found
[    2.561024] hub 9-0:1.0: 2 ports detected
[    2.562034] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    2.562045] r8169 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    2.562055] r8169 0000:02:00.0: setting latency timer to 64
[    2.562270] eth0: RTL8168c/8111c at 0xffffc20000336000, 00:1f:d0:a5:29:77, XID 3c4000c0 IRQ 2301
[    2.768897] uhci_hcd 0000:03:00.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    2.768901] uhci_hcd 0000:03:00.1: UHCI Host Controller
[    2.768918] uhci_hcd 0000:03:00.1: new USB bus registered, assigned bus number 10
[    2.768936] uhci_hcd 0000:03:00.1: irq 19, io base 0x0000d100
[    2.768987] usb usb10: configuration #1 chosen from 1 choice
[    2.769002] hub 10-0:1.0: USB hub found
[    2.769006] hub 10-0:1.0: 2 ports detected
[    2.852024] usb 1-1: new low speed USB device using uhci_hcd and address 4
[    2.976957] ehci_hcd 0000:03:00.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    2.976963] ehci_hcd 0000:03:00.2: EHCI Host Controller
[    2.976981] ehci_hcd 0000:03:00.2: new USB bus registered, assigned bus number 11
[    2.977005] ehci_hcd 0000:03:00.2: irq 18, io mem 0xe1615000
[    2.992028] ehci_hcd 0000:03:00.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    2.992531] usb usb11: configuration #1 chosen from 1 choice
[    2.992962] hub 11-0:1.0: USB hub found
[    2.992967] hub 11-0:1.0: 4 ports detected
[    3.036503] usb 1-1: configuration #1 chosen from 1 choice
[    3.201176] ohci1394 0000:03:07.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    3.250865] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[23]  MMIO=[e1614000-e16147ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    3.254484] ata_piix 0000:00:1f.2: version 2.12
[    3.254495] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    3.254497] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    3.254528] ata_piix 0000:00:1f.2: setting latency timer to 64
[    3.255371] scsi0 : ata_piix
[    3.255461] scsi1 : ata_piix
[    3.255942] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[    3.255946] ata2: SATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[    3.280029] usb 1-2: new low speed USB device using uhci_hcd and address 5
[    3.457087] usb 1-2: configuration #1 chosen from 1 choice
[    3.460144] usbcore: registered new interface driver hiddev
[    3.606229] input: Logitech Logitech USB Keyboard as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1:1.0/input/input1
[    3.616062] input,hidraw0: USB HID v1.10 Keyboard [Logitech Logitech USB Keyboard] on usb-0000:00:1a.0-1
[    3.654051] input: Logitech Logitech USB Keyboard as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1:1.1/input/input2
[    3.676569] input,hidraw1: USB HID v1.10 Mouse [Logitech Logitech USB Keyboard] on usb-0000:00:1a.0-1
[    3.704024] usb 11-1: new high speed USB device using ehci_hcd and address 2
[    3.728098] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    3.744212] ata1.00: HPA unlocked: 1250261615 -> 1250263728, native 1250263728
[    3.744215] ata1.00: ATA-8: WDC WD6400AAKS-75A7B0, 01.03B01, max UDMA/133
[    3.744216] ata1.00: 1250263728 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    3.761336] ata1.00: configured for UDMA/133
[    3.833290] usb 11-1: configuration #1 chosen from 1 choice
[    3.849207] input: B16_b_02 USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1a.0/usb1/1-2/1-2:1.0/input/input3
[    3.876075] input,hidraw2: USB HID v1.10 Mouse [B16_b_02 USB-PS/2 Optical Mouse] on usb-0000:00:1a.0-2
[    3.876091] usbcore: registered new interface driver usbhid
[    3.876093] usbhid: v2.6:USB HID core driver
[    4.090621] ata2: SATA link down (SStatus 0 SControl 300)
[    4.090658] isa bounce pool size: 16 pages
[    4.090720] scsi 0:0:0:0: Direct-Access     ATA      WDC WD6400AAKS-7 01.0 PQ: 0 ANSI: 5
[    4.090796] ata_piix 0000:00:1f.5: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    4.090799] ata_piix 0000:00:1f.5: MAP [ P0 -- P1 -- ]
[    4.090828] ata_piix 0000:00:1f.5: setting latency timer to 64
[    4.090871] scsi2 : ata_piix
[    4.090918] scsi3 : ata_piix
[    4.091325] ata3: SATA max UDMA/133 cmd 0xe800 ctl 0xe900 bmdma 0xec00 irq 19
[    4.091328] ata4: SATA max UDMA/133 cmd 0xea00 ctl 0xeb00 bmdma 0xec08 irq 19
[    4.418573] ata3: SATA link down (SStatus 0 SControl 300)
[    4.525122] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00aa238f00001fd0]
[    4.746585] ata4: SATA link down (SStatus 0 SControl 300)
[    4.746627] pata_acpi 0000:03:05.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    4.746643] pata_acpi 0000:03:05.0: setting latency timer to 64
[    4.746652] pata_acpi 0000:03:05.0: PCI INT A disabled
[    4.748685] pata_it8213 0000:03:05.0: version 0.0.3
[    4.748690] pata_it8213 0000:03:05.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    4.749333] scsi4 : pata_it8213
[    4.749388] scsi5 : pata_it8213
[    4.749411] ata5: PATA max UDMA/66 cmd 0xd200 ctl 0xd300 bmdma 0xd600 irq 21
[    4.749412] ata6: DUMMY
[    4.754352] scsi 0:0:0:0: Attached scsi generic sg0 type 0
[    4.761183] Driver 'sd' needs updating - please use bus_type methods
[    4.761245] sd 0:0:0:0: [sda] 1250263728 512-byte hardware sectors (640135 MB)
[    4.761257] sd 0:0:0:0: [sda] Write Protect is off
[    4.761258] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.761277] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.761322] sd 0:0:0:0: [sda] 1250263728 512-byte hardware sectors (640135 MB)
[    4.761333] sd 0:0:0:0: [sda] Write Protect is off
[    4.761334] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.761353] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.761355]  sda: sda1 sda2 sda3 sda4
[    4.783834] sd 0:0:0:0: [sda] Attached SCSI disk
[    4.912480] ata5.00: ATAPI: PIONEER DVD-RW  DVR-108, 1.18, max UDMA/66
[    4.928344] ata5.00: configured for UDMA/66
[    4.934048] scsi 4:0:0:0: CD-ROM            PIONEER  DVD-RW  DVR-108  1.18 PQ: 0 ANSI: 5
[    4.934146] scsi 4:0:0:0: Attached scsi generic sg1 type 5
[    4.946345] Driver 'sr' needs updating - please use bus_type methods
[    4.964469] sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[    4.964472] Uniform CD-ROM driver Revision: 3.20
[    4.964602] sr 4:0:0:0: Attached scsi CD-ROM sr0
[    5.259846] PM: Starting manual resume from disk
[    5.259848] PM: Resume from partition 8:2
[    5.259849] PM: Checking hibernation image.
[    5.260003] PM: Resume from disk failed.
[    5.275462] kjournald starting.  Commit interval 5 seconds
[    5.275477] EXT3-fs: mounted filesystem with ordered data mode.
[    7.668504] udevd version 124 started
[    8.021147] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    8.069614] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    8.169868] input: PC Speaker as /devices/platform/pcspkr/input/input4
[    8.202211] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input5
[    8.204148] agpgart-intel 0000:00:00.0: Intel G45/G43 Chipset
[    8.205335] agpgart-intel 0000:00:00.0: detected 65532K stolen memory
[    8.215926] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[    8.344590] ACPI: Power Button (FF) [PWRF]
[    8.344629] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input6
[    8.412572] ACPI: Power Button (CM) [PWRB]
[    8.529918] parport_pc 00:08: reported by Plug and Play ACPI
[    8.529964] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[    8.576053] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    8.576078] HDA Intel 0000:00:1b.0: setting latency timer to 64
[    8.610382] hda_codec: Unknown model for ALC882, trying auto-probe from BIOS...
[    8.678219] udev: renamed network interface eth0 to eth2
[    8.922456] dib0700: loaded with support for 7 different device-types
[    8.923381] dvb-usb: found a 'Hauppauge Nova-T 500 Dual DVB-T' in warm state.
[    8.923420] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[    8.923588] DVB: registering new adapter (Hauppauge Nova-T 500 Dual DVB-T)
[    9.039050] DVB: registering frontend 0 (DiBcom 3000MC/P)...
[    9.077299] MT2060: successfully identified (IF1 = 1220)
[    9.571273] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[    9.571437] DVB: registering new adapter (Hauppauge Nova-T 500 Dual DVB-T)
[    9.578520] DVB: registering frontend 1 (DiBcom 3000MC/P)...
[    9.583275] MT2060: successfully identified (IF1 = 1220)
[   10.145477] input: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:1e.0/0000:03:00.2/usb11/11-1/input/input7
[   10.188615] dvb-usb: schedule remote query interval to 150 msecs.
[   10.188618] dvb-usb: Hauppauge Nova-T 500 Dual DVB-T successfully initialized and connected.
[   10.188880] usbcore: registered new interface driver dvb_usb_dib0700
[   10.389249] lp0: using parport0 (interrupt-driven).
[   10.438763] it87: Found IT8718F chip at 0x290, revision 5
[   10.438770] it87: in3 is VCC (+5V)
[   10.673701] Adding 996020k swap on /dev/sda2.  Priority:-1 extents:1 across:996020k
[   11.449937] EXT3 FS on sda3, internal journal
[   12.189568] kjournald starting.  Commit interval 5 seconds
[   12.189782] EXT3 FS on sda1, internal journal
[   12.189787] EXT3-fs: mounted filesystem with ordered data mode.
[   12.212359] SGI XFS with ACLs, security attributes, realtime, large block/inode numbers, no debug enabled
[   12.215167] SGI XFS Quota Management subsystem
[   12.222809] Filesystem "dm-0": Disabling barriers, trial barrier write failed
[   12.248995] XFS mounting filesystem dm-0
[   12.348106] Ending clean XFS mount for filesystem: dm-0
[   12.851210] type=1505 audit(1227445550.569:2): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4394
[   12.851335] type=1505 audit(1227445550.569:3): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4394
[   12.879555] type=1505 audit(1227445550.597:4): operation="profile_load" name="/usr/sbin/mysqld" name2="default" pid=4398
[   13.033147] ip_tables: (C) 2000-2006 Netfilter Core Team
[   14.293934] ACPI: WMI: Mapper loaded
[   15.404854] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   15.757842] NET: Registered protocol family 10
[   15.758700] lo: Disabled Privacy Extensions
[   16.650323] ppdev: user-space parallel port driver
[   23.357066] Bluetooth: Core ver 2.13
[   23.357128] NET: Registered protocol family 31
[   23.357129] Bluetooth: HCI device and connection manager initialized
[   23.357132] Bluetooth: HCI socket layer initialized
[   23.386812] Bluetooth: L2CAP ver 2.11
[   23.386817] Bluetooth: L2CAP socket layer initialized
[   23.401750] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   23.401755] Bluetooth: BNEP filters: protocol multicast
[   23.418224] Bridge firewalling registered
[   23.418955] pan0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature.
[   23.454746] Bluetooth: SCO (Voice Link) ver 0.6
[   23.454751] Bluetooth: SCO socket layer initialized
[   23.767955] Bluetooth: RFCOMM socket layer initialized
[   23.768624] Bluetooth: RFCOMM TTY layer initialized
[   23.768629] Bluetooth: RFCOMM ver 1.10
[   27.924397] r8169: eth2: link up
[   27.924406] r8169: eth2: link up
[   28.322322] NET: Registered protocol family 17
[   29.022570] lirc_dev: IR Remote Control driver registered, major 61 
[   29.031476] 
[   29.031479] lirc_mceusb2: Philips eHome USB IR Transceiver and Microsoft MCE 2005 Remote Control driver for LIRC $Revision: 1.44 $
[   29.031482] lirc_mceusb2: Daniel Melander <lirc@rajidae.se>, Martin Blatter <martin_a_blatter@yahoo.com>
[   29.033084] usbcore: registered new interface driver lirc_mceusb2
[   38.698636] eth2: no IPv6 routers present
[   44.631342] r8169: eth2: link down
[  867.073640] mythfilldatabas[7140]: segfault at 24b3c70 ip 00000000024b3c70 sp 00000000417b5dd8 error 15
[  878.972626] r8169: eth2: link up
[ 1947.681569] usbhid: event field not found
[ 1947.729573] usbhid: event field not found
[ 1948.081555] usbhid: event field not found
[ 1948.297555] usbhid: event field not found
[ 1948.385551] usbhid: event field not found
[ 1948.417546] usbhid: event field not found
[ 1948.481548] usbhid: event field not found
[ 1948.497549] usbhid: event field not found
[ 1948.585547] usbhid: event field not found
[ 1948.593545] usbhid: event field not found

```

---

