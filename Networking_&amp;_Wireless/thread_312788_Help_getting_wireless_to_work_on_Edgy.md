---
title: "Help getting wireless to work on Edgy"
date: 2006-12-04
forum: Networking &amp; Wireless
---

### Post by beastjangles on 2006-12-04
I have a Toshiba A105-2141 with an integrated Atheros AR5211 wireless chip.  When I installed Edgy for the first time, my wireless ethernet didn't appear in the network manager.

I've tried ndiswrapper(1.29) with the windows driver and I still couldn't configure my wireless.  

I've installed the latest linux-restricted modules(2.6.17), and that's still a no go.   

Here are my outputs:

lspci:
```

00:00.0 Host bridge: ATI Technologies Inc Unknown device 5a31 (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:04.0 PCI bridge: ATI Technologies Inc Unknown device 5a36
00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:07.0 PCI bridge: ATI Technologies Inc Unknown device 5a39
00:12.0 IDE interface: ATI Technologies Inc ATI 4379 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 82)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI (rev 80)
00:14.2 Audio device: ATI Technologies Inc Unknown device 437b (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]
02:00.0 Ethernet controller: Atheros Communications, Inc. Unknown device 001c (rev 01)
0b:06.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
0b:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)


```

dmesg:
```
[17179569.184000] Linux version 2.6.17-10-generic (root@vernadsky) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Fri Oct 13 18:45:35 UTC 2006 (Ubuntu 2.6.17-10.33-generic)
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009dc00 (usable)
[17179569.184000]  BIOS-e820: 000000000009dc00 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000dc000 - 00000000000e0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000001be80000 (usable)
[17179569.184000]  BIOS-e820: 000000001be80000 - 000000001be93000 (ACPI data)
[17179569.184000]  BIOS-e820: 000000001be93000 - 000000001bf00000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 000000001bf00000 - 000000001c000000 (reserved)
[17179569.184000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 446MB LOWMEM available.
[17179569.184000] found SMP MP-table at 000f7e30
[17179569.184000] On node 0 totalpages: 114304
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   Normal zone: 110208 pages, LIFO batch:31
[17179569.184000] DMI present.
[17179569.184000] ACPI: RSDP (v000 TOSINV                                ) @ 0x000f7d80
[17179569.184000] ACPI: RSDT (v001 TOSINV   RSDT   0x06040000  LTP 0x00000000) @ 0x1be8d820
[17179569.184000] ACPI: FADT (v001 TOSINV Bonefish 0x06040000 ATI  0x000f4240) @ 0x1be92f00
[17179569.184000] ACPI: MADT (v001 TOSINV        APIC   0x06040000  LTP 0x00000000) @ 0x1be92f74
[17179569.184000] ACPI: MCFG (v001 TOSINV   MCFG   0x06040000  LTP 0x00000000) @ 0x1be92fc4
[17179569.184000] ACPI: SSDT (v001  PmRef  Cpu0Cst 0x00003001 INTL 0x20050228) @ 0x1be8dd8d
[17179569.184000] ACPI: SSDT (v001  PmRef    CpuPm 0x00003000 INTL 0x20050228) @ 0x1be8d858
[17179569.184000] ACPI: DSDT (v001 TOSINV    SB450 0x06040000 MSFT 0x0100000e) @ 0x00000000
[17179569.184000] ATI board detected. Disabling timer routing over 8254.
[17179569.184000] ACPI: PM-Timer IO Port: 0x8008
[17179569.184000] ACPI: Local APIC address 0xfee00000
[17179569.184000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[17179569.184000] Processor #0 6:14 APIC version 20
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[17179569.184000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[17179569.184000] IOAPIC[0]: apic_id 1, version 33, address 0xfec00000, GSI 0-23
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 21 low level)
[17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[17179569.184000] Using ACPI (MADT) for SMP configuration information
[17179569.184000] Allocating PCI resources starting at 20000000 (gap: 1c000000:c4000000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/sda3 ro quiet splash
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
[17179569.184000] Enabling fast FPU save and restore... done.
[17179569.184000] Enabling unmasked SIMD FPU exception support... done.
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[17179569.184000] Detected 1463.267 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179571.840000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179571.840000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179571.852000] Memory: 443360k/457216k available (1910k kernel code, 13324k reserved, 1070k data, 308k init, 0k highmem)
[17179571.852000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179571.932000] Calibrating delay using timer specific routine.. 2931.31 BogoMIPS (lpj=5862633)
[17179571.932000] Security Framework v1.0.0 initialized
[17179571.932000] SELinux:  Disabled at boot.
[17179571.932000] Mount-cache hash table entries: 512
[17179571.932000] CPU: After generic identify, caps: afe9fbff 00000000 00000000 00000000 0000c109 00000000 00000000
[17179571.932000] CPU: After vendor identify, caps: afe9fbff 00000000 00000000 00000000 0000c109 00000000 00000000
[17179571.932000] monitor/mwait feature present.
[17179571.932000] using mwait in idle threads.
[17179571.932000] CPU: L1 I cache: 32K, L1 D cache: 32K
[17179571.932000] CPU: L2 cache: 1024K
[17179571.932000] CPU: After all inits, caps: afe9fbff 00000000 00000000 00000140 0000c109 00000000 00000000
[17179571.932000] Checking 'hlt' instruction... OK.
[17179571.948000] SMP alternatives: switching to UP code
[17179571.948000] Freeing SMP alternatives: 16k freed
[17179571.948000] checking if image is initramfs... it is
[17179572.600000] Freeing initrd memory: 5563k freed
[17179572.600000] ACPI: Core revision 20060707
[17179572.620000] ACPI: Looking for DSDT ... not found!
[17179573.268000] CPU0: Intel(R) Celeron(R) M CPU        410  @ 1.46GHz stepping 08
[17179573.268000] Total of 1 processors activated (2931.31 BogoMIPS).
[17179573.268000] ENABLING IO-APIC IRQs
[17179573.268000] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
[17179573.412000] Brought up 1 CPUs
[17179573.412000] migration_cost=0
[17179573.412000] NET: Registered protocol family 16
[17179573.412000] EISA bus registered
[17179573.412000] ACPI: bus type pci registered
[17179573.412000] PCI: Using MMCONFIG
[17179573.412000] Setting up standard PCI resources
[17179573.432000] ACPI: Interpreter enabled
[17179573.432000] ACPI: Using IOAPIC for interrupt routing
[17179573.436000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179573.436000] PCI: Probing PCI hardware (bus 00)
[17179573.468000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:14.1
[17179573.468000] Boot video device is 0000:01:05.0
[17179573.468000] PCI: Transparent bridge - 0000:00:14.4
[17179573.468000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179573.472000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB4_._PRT]
[17179573.472000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB6_._PRT]
[17179573.472000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB7_._PRT]
[17179573.472000] ACPI: PCI Interrupt Link [LNKA] (IRQs 10 11) *0, disabled.
[17179573.472000] ACPI: PCI Interrupt Link [LNKB] (IRQs 10 11) *0, disabled.
[17179573.472000] ACPI: PCI Interrupt Link [LNKC] (IRQs 10 11) *0, disabled.
[17179573.472000] ACPI: PCI Interrupt Link [LNKD] (IRQs 10 11) *0, disabled.
[17179573.472000] ACPI: PCI Interrupt Link [LNKE] (IRQs 10 11) *0, disabled.
[17179573.476000] ACPI: PCI Interrupt Link [LNKF] (IRQs 10 11) *0, disabled.
[17179573.476000] ACPI: PCI Interrupt Link [LNKG] (IRQs 10 11) *0, disabled.
[17179573.476000] ACPI: PCI Interrupt Link [LNKH] (IRQs 10 11) *0, disabled.
[17179573.476000] ACPI: PCI Interrupt Link [LNKU] (IRQs 3 4 5 7) *0, disabled.
[17179573.524000] ACPI: Embedded Controller [EC0] (gpe 7) interrupt mode.
[17179573.524000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[17179573.524000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[17179573.524000] ACPI: Power Resource [PFA1] (off)
[17179573.524000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179573.524000] pnp: PnP ACPI init
[17179573.556000] pnp: PnP ACPI: found 10 devices
[17179573.556000] PnPBIOS: Disabled by ACPI PNP
[17179573.556000] PCI: Using ACPI for IRQ routing
[17179573.556000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179573.556000] PCI: Cannot allocate resource region 7 of bridge 0000:00:06.0
[17179573.556000] PCI: Cannot allocate resource region 8 of bridge 0000:00:06.0
[17179573.556000] PCI: Cannot allocate resource region 7 of bridge 0000:00:07.0
[17179573.556000] PCI: Cannot allocate resource region 8 of bridge 0000:00:07.0
[17179573.556000] pnp: 00:08: ioport range 0x1080-0x1080 has been reserved
[17179573.556000] pnp: 00:08: ioport range 0x220-0x22f has been reserved
[17179573.556000] pnp: 00:08: ioport range 0x400-0x401 has been reserved
[17179573.556000] pnp: 00:08: ioport range 0x40b-0x40b has been reserved
[17179573.556000] PCI: Bridge: 0000:00:01.0
[17179573.556000]   IO window: 9000-9fff
[17179573.556000]   MEM window: d0000000-d00fffff
[17179573.556000]   PREFETCH window: d8000000-dfffffff
[17179573.556000] PCI: Bridge: 0000:00:04.0
[17179573.556000]   IO window: disabled.
[17179573.556000]   MEM window: d0100000-d01fffff
[17179573.556000]   PREFETCH window: disabled.
[17179573.556000] PCI: Bridge: 0000:00:06.0
[17179573.556000]   IO window: disabled.
[17179573.556000]   MEM window: disabled.
[17179573.556000]   PREFETCH window: disabled.
[17179573.556000] PCI: Bridge: 0000:00:07.0
[17179573.556000]   IO window: disabled.
[17179573.556000]   MEM window: disabled.
[17179573.556000]   PREFETCH window: disabled.
[17179573.556000] PCI: Bus 12, cardbus bridge: 0000:0b:06.0
[17179573.556000]   IO window: 0000a400-0000a4ff
[17179573.556000]   IO window: 0000a800-0000a8ff
[17179573.556000]   PREFETCH window: 20000000-21ffffff
[17179573.556000]   MEM window: 24000000-25ffffff
[17179573.556000] PCI: Bridge: 0000:00:14.4
[17179573.556000]   IO window: a000-afff
[17179573.556000]   MEM window: d0200000-d02fffff
[17179573.556000]   PREFETCH window: 20000000-21ffffff
[17179573.556000] PCI: Setting latency timer of device 0000:00:04.0 to 64
[17179573.556000] PCI: Setting latency timer of device 0000:00:06.0 to 64
[17179573.556000] PCI: Setting latency timer of device 0000:00:07.0 to 64
[17179573.556000] PCI: Enabling device 0000:0b:06.0 (0000 -> 0003)
[17179573.556000] ACPI: PCI Interrupt 0000:0b:06.0[A] -> GSI 23 (level, low) -> IRQ 185
[17179573.556000] NET: Registered protocol family 2
[17179573.592000] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[17179573.592000] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[17179573.592000] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[17179573.592000] TCP: Hash tables configured (established 16384 bind 8192)
[17179573.592000] TCP reno registered
[17179573.592000] audit: initializing netlink socket (disabled)
[17179573.592000] audit(1165268968.592:1): initialized
[17179573.592000] VFS: Disk quotas dquot_6.5.1
[17179573.592000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179573.592000] Initializing Cryptographic API
[17179573.592000] io scheduler noop registered
[17179573.592000] io scheduler anticipatory registered
[17179573.592000] io scheduler deadline registered
[17179573.592000] io scheduler cfq registered (default)
[17179573.592000] PCI: Setting latency timer of device 0000:00:04.0 to 64
[17179573.592000] pcie_portdrv_probe->Dev[5a36:1002] has invalid IRQ. Check vendor BIOS
[17179573.592000] assign_interrupt_mode Found MSI capability
[17179573.592000] Allocate Port Service[0000:00:04.0:pcie00]
[17179573.592000] Allocate Port Service[0000:00:04.0:pcie01]
[17179573.592000] Allocate Port Service[0000:00:04.0:pcie03]
[17179573.592000] PCI: Setting latency timer of device 0000:00:06.0 to 64
[17179573.592000] pcie_portdrv_probe->Dev[5a38:1002] has invalid IRQ. Check vendor BIOS
[17179573.592000] assign_interrupt_mode Found MSI capability
[17179573.592000] Allocate Port Service[0000:00:06.0:pcie00]
[17179573.592000] Allocate Port Service[0000:00:06.0:pcie01]
[17179573.592000] Allocate Port Service[0000:00:06.0:pcie03]
[17179573.592000] PCI: Setting latency timer of device 0000:00:07.0 to 64
[17179573.592000] pcie_portdrv_probe->Dev[5a39:1002] has invalid IRQ. Check vendor BIOS
[17179573.592000] assign_interrupt_mode Found MSI capability
[17179573.592000] Allocate Port Service[0000:00:07.0:pcie00]
[17179573.592000] Allocate Port Service[0000:00:07.0:pcie01]
[17179573.592000] Allocate Port Service[0000:00:07.0:pcie03]
[17179573.592000] isapnp: Scanning for PnP cards...
[17179573.948000] isapnp: No Plug & Play device found
[17179573.972000] Real Time Clock Driver v1.12ac
[17179573.976000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[17179573.976000] mice: PS/2 mouse device common for all mice
[17179573.976000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179573.976000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179573.976000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179573.976000] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[17179573.976000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179573.976000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179573.980000] EISA: Probing bus 0 at eisa.0
[17179573.980000] Cannot allocate resource for EISA slot 1
[17179573.980000] Cannot allocate resource for EISA slot 8
[17179573.980000] EISA: Detected 0 cards.
[17179573.980000] TCP bic registered
[17179573.980000] NET: Registered protocol family 1
[17179573.980000] NET: Registered protocol family 8
[17179573.980000] NET: Registered protocol family 20
[17179573.980000] Using IPI No-Shortcut mode
[17179573.980000] ACPI: (supports S0 S3 S4 S5)
[17179573.980000] Freeing unused kernel memory: 308k freed
[17179574.072000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179575.112000] Capability LSM initialized
[17179575.144000] ACPI: Transitioning device [FAN1] to D3
[17179575.144000] ACPI: Transitioning device [FAN1] to D3
[17179575.144000] ACPI: Fan [FAN1] (off)
[17179575.148000] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[17179575.148000] ACPI: Processor [CPU0] (supports 8 throttling states)
[17179575.148000] ACPI Exception (acpi_processor-0693): AE_NOT_FOUND, Processor Device is not present [20060707]
[17179575.148000] ACPI: Getting cpuindex for acpiid 0x1
[17179575.356000] ACPI: Thermal Zone [TZCR] (39 C)
[17179575.692000] SCSI subsystem initialized
[17179575.696000] libata version 1.20 loaded.
[17179575.700000] sata_sil 0000:00:12.0: version 0.9
[17179575.700000] PCI: Enabling device 0000:00:12.0 (0005 -> 0007)
[17179575.700000] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 22 (level, low) -> IRQ 225
[17179575.700000] ata1: SATA max UDMA/100 cmd 0xDC83E080 ctl 0xDC83E08A bmdma 0xDC83E000 irq 225
[17179575.700000] ata2: SATA max UDMA/100 cmd 0xDC83E0C0 ctl 0xDC83E0CA bmdma 0xDC83E008 irq 225
[17179576.060000] ata1: SATA link up 1.5 Gbps (SStatus 113)
[17179576.068000] ata1: dev 0 cfg 49:2f00 82:746b 83:7d09 84:6023 85:7469 86:3d09 87:6023 88:203f
[17179576.068000] ata1: dev 0 ATA-6, max UDMA/100, 156301488 sectors: LBA48
[17179576.076000] ata1: dev 0 configured for UDMA/100
[17179576.076000] scsi0 : sata_sil
[17179576.280000] ata2: SATA link down (SStatus 0)
[17179576.288000] scsi1 : sata_sil
[17179576.288000]   Vendor: ATA       Model: TOSHIBA MK8032GS  Rev: AS11
[17179576.288000]   Type:   Direct-Access                      ANSI SCSI revision: 05
[17179576.300000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[17179576.300000] sda: Write Protect is off
[17179576.300000] sda: Mode Sense: 00 3a 00 00
[17179576.300000] SCSI device sda: drive cache: write back
[17179576.300000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[17179576.300000] sda: Write Protect is off
[17179576.300000] sda: Mode Sense: 00 3a 00 00
[17179576.300000] SCSI device sda: drive cache: write back
[17179576.300000]  sda: sda1 sda2 sda3
[17179576.340000] sd 0:0:0:0: Attached scsi disk sda
[17179576.696000] ATIIXP: IDE controller at PCI slot 0000:00:14.1
[17179576.696000] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 233
[17179576.696000] ATIIXP: chipset revision 128
[17179576.696000] ATIIXP: not 100% native mode: will probe irqs later
[17179576.696000]     ide0: BM-DMA at 0x8460-0x8467, BIOS settings: hda:pio, hdb:pio
[17179576.696000]     ide1: BM-DMA at 0x8468-0x846f, BIOS settings: hdc:DMA, hdd:pio
[17179576.696000] Probing IDE interface ide0...
[17179577.264000] Probing IDE interface ide1...
[17179578.000000] hdc: DVD/CDRW UJDA770, ATAPI CD/DVD-ROM drive
[17179578.336000] ide1 at 0x170-0x177,0x376 on irq 15
[17179578.344000] hdc: ATAPI 24X DVD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
[17179578.344000] Uniform CD-ROM driver Revision: 3.20
[17179578.408000] Probing IDE interface ide0...
[17179578.468000] usbcore: registered new driver usbfs
[17179578.468000] usbcore: registered new driver hub
[17179578.468000] ACPI: PCI Interrupt 0000:00:13.2[A] -> GSI 19 (level, low) -> IRQ 50
[17179578.468000] ehci_hcd 0000:00:13.2: EHCI Host Controller
[17179578.468000] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 1
[17179578.468000] ehci_hcd 0000:00:13.2: irq 50, io mem 0xd0506000
[17179578.468000] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179578.468000] usb usb1: configuration #1 chosen from 1 choice
[17179578.468000] hub 1-0:1.0: USB hub found
[17179578.468000] hub 1-0:1.0: 8 ports detected
[17179578.500000] ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[17179578.572000] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 19 (level, low) -> IRQ 50
[17179578.572000] ohci_hcd 0000:00:13.0: OHCI Host Controller
[17179578.572000] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 2
[17179578.572000] ohci_hcd 0000:00:13.0: irq 50, io mem 0xd0504000
[17179578.632000] usb usb2: configuration #1 chosen from 1 choice
[17179578.632000] hub 2-0:1.0: USB hub found
[17179578.632000] hub 2-0:1.0: 4 ports detected
[17179578.736000] ACPI: PCI Interrupt 0000:00:13.1[A] -> GSI 19 (level, low) -> IRQ 50
[17179578.736000] ohci_hcd 0000:00:13.1: OHCI Host Controller
[17179578.736000] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 3
[17179578.736000] ohci_hcd 0000:00:13.1: irq 50, io mem 0xd0505000
[17179578.796000] usb usb3: configuration #1 chosen from 1 choice
[17179578.796000] hub 3-0:1.0: USB hub found
[17179578.796000] hub 3-0:1.0: 4 ports detected
[17179579.096000] kjournald starting.  Commit interval 5 seconds
[17179579.096000] EXT3-fs: mounted filesystem with ordered data mode.
[17179592.048000] Linux agpgart interface v0.101 (c) Dave Jones
[17179592.096000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179592.132000] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x25a0b1, caps: 0xa04713/0x0
[17179592.132000] synaptics: Toshiba Satellite A105 detected, limiting rate to 40pps.
[17179592.132000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179592.164000] input: SynPS/2 Synaptics TouchPad as /class/input/input1
[17179592.192000] input: PC Speaker as /class/input/input2
[17179592.360000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[17179592.476000] ACPI: PCI Interrupt 0000:0b:06.0[A] -> GSI 23 (level, low) -> IRQ 185
[17179592.476000] Yenta: CardBus bridge found at 0000:0b:06.0 [1179:ff10]
[17179592.476000] Yenta: Using CSCINT to route CSC interrupts to PCI
[17179592.476000] Yenta: Routing CardBus interrupts to PCI
[17179592.476000] Yenta TI: socket 0000:0b:06.0, mfunc 0x01111002, devctl 0x44
[17179592.496000] 8139too Fast Ethernet driver 0.9.27
[17179592.592000] ts: Compaq touchscreen protocol output
[17179592.708000] Yenta: ISA IRQ mask 0x0ef8, PCI irq 185
[17179592.708000] Socket status: 30000006
[17179592.708000] pcmcia: parent PCI bridge I/O window: 0xa000 - 0xafff
[17179592.708000] cs: IO port probe 0xa000-0xafff: clean.
[17179592.708000] pcmcia: parent PCI bridge Memory window: 0xd0200000 - 0xd02fffff
[17179592.708000] pcmcia: parent PCI bridge Memory window: 0x20000000 - 0x21ffffff
[17179592.716000] ACPI: PCI Interrupt 0000:0b:07.0[A] -> GSI 20 (level, low) -> IRQ 58
[17179592.716000] eth0: RealTek RTL8139 at 0xdc840000, 00:a0:d1:47:39:01, IRQ 58
[17179592.716000] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[17179592.724000] 8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
[17179592.788000] ACPI: PCI Interrupt 0000:00:14.2[A] -> GSI 16 (level, low) -> IRQ 233
[17179592.940000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[17179593.036000] cs: IO port probe 0x100-0x3af: excluding 0x1f0-0x1f7
[17179593.040000] cs: IO port probe 0x3e0-0x4ff: excluding 0x3f0-0x3f7 0x4d0-0x4d7
[17179593.040000] cs: IO port probe 0x820-0x8ff: excluding 0x878-0x87f
[17179593.040000] cs: IO port probe 0xc00-0xcf7: excluding 0xc00-0xc07 0xc10-0xc17 0xc50-0xc57 0xc68-0xc6f 0xcd0-0xcdf
[17179593.044000] cs: IO port probe 0xa00-0xaff: clean.
[17179593.492000] hda_codec: Unknown model for ALC861, trying auto-probe from BIOS...
[17179593.868000] lp: driver loaded but no devices found
[17179594.008000] EXT3 FS on sda3, internal journal
[17179594.076000] NET: Registered protocol family 17
[17179594.264000] NTFS driver 2.1.27 [Flags: R/O MODULE].
[17179594.324000] NTFS volume version 3.1.
[17179594.348000] NTFS volume version 3.1.
[17179595.304000] ACPI: AC Adapter [ADP0] (on-line)
[17179595.348000] ACPI: Battery Slot [BAT0] (battery present)
[17179595.380000] ACPI: Power Button (FF) [PWRF]
[17179595.380000] ACPI: Power Button (CM) [PWRB]
[17179595.380000] ACPI: Lid Switch [LID]
[17179595.428000] NET: Registered protocol family 10
[17179595.428000] lo: Disabled Privacy Extensions
[17179595.428000] IPv6 over IPv4 tunneling driver
[17179595.600000] ibm_acpi: ec object not found
[17179595.628000] pcc_acpi: loading...
[17179598.284000] apm: BIOS not found.
[17179601.964000] hda-intel: Invalid position buffer, using LPIB read method instead.
[17179602.844000] Bluetooth: Core ver 2.8
[17179602.844000] NET: Registered protocol family 31
[17179602.844000] Bluetooth: HCI device and connection manager initialized
[17179602.844000] Bluetooth: HCI socket layer initialized
[17179602.860000] Bluetooth: L2CAP ver 2.8
[17179602.860000] Bluetooth: L2CAP socket layer initialized
[17179602.864000] Bluetooth: RFCOMM socket layer initialized
[17179602.864000] Bluetooth: RFCOMM TTY layer initialized
[17179602.864000] Bluetooth: RFCOMM ver 1.7
[17179617.728000] eth0: no IPv6 routers present
[17181005.396000] ath_hal: module license 'Proprietary' taints kernel.
[17181005.396000] ath_hal: 0.9.17.2 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[17181005.452000] wlan: 0.8.4.2 (0.9.2)
[17181005.452000] ath_rate_sample: 1.2 (0.9.2)
[17181005.456000] ath_pci: 0.9.4.5 (0.9.2)
[17181005.460000] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 233
[17181005.460000] PCI: Setting latency timer of device 0000:02:00.0 to 64
[17181005.460000] wifi%d: unable to attach hardware: 'Hardware revision not supported' (HAL status 13)
[17181005.460000] ACPI: PCI interrupt for device 0000:02:00.0 disabled

```

even after I installed ndiswrapper and the restricted modules, I get no ath0 in my iwconfig:

```
long@long-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

long@long-laptop:~$ 

```

I felt like I've done backflips while dribbling a basketball trying to figure out what's going while I've scoured through the forums and countless how-to's.  If I'm missing anything, please let me know and any help is appreciated in advance.](*,)

---

### Post by clouserw on 2006-12-05
[These guys]("http://madwifi.org/ticket/713") seem to have had the same trouble as you and got it resolved.  Not sure if you've tried everything there, but it could be a start.

---

