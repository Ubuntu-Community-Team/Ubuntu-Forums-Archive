---
title: "pavilion dv9074 wireless bcm4311 working, but wont load at boot"
date: 2006-10-07
forum: Networking &amp; Wireless
---

### Post by joergenlie on 2006-10-07
Got my wireless working like a charm after compiling ndiswrapper 1.25 and using the windows drivers from windows partition. I have tried everything. Ndiswrapper wont load at boot. I've tried to uninstall and when i install again and ndiswrapper -m it says that the module already contains alias.

When i modprobe ndiswrapper though it runs like a charm with wep. This is annoying!

here's dmesg after boot and dmesg after modprobe ndiswrapper:

[   78.254558] IPv6 over IPv4 tunneling driver
joergenlie@joergenlie-laptop:~$ sudo modprobe ndiswrapper
Password:
joergenlie@joergenlie-laptop:~$ dmesg
[    0.000000] Bootdata ok (command line is root=/dev/sdb1 ro quiet splash noapic nolapic)
[    0.000000] Linux version 2.6.15-26-amd64-generic (buildd@king) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 SMP PREEMPT Fri Sep 8 19:55:50 UTC 2006
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009dc00 (usable)
[    0.000000]  BIOS-e820: 000000000009dc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003ff00000 (usable)
[    0.000000]  BIOS-e820: 000000003ff00000 - 000000003ff17000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003ff17000 - 000000003ff80000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003ff80000 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] ACPI: RSDP (v000 HP                                    ) @ 0x00000000000f89a0
[    0.000000] ACPI: RSDT (v001 HP       RSDT   0x06040000  LTP 0x00000000) @ 0x000000003ff0fba5
[    0.000000] ACPI: FADT (v001 HP     MCP51M   0x06040000 PTL_ 0x000f4240) @ 0x000000003ff16d10
[    0.000000] ACPI: SSDT (v001 HP     POWERNOW 0x06040000  LTP 0x00000001) @ 0x000000003ff16d84
[    0.000000] ACPI: MCFG (v001 HP       MCFG   0x06040000  LTP 0x00000000) @ 0x000000003ff16f48
[    0.000000] ACPI: MADT (v001 HP       APIC   0x06040000  LTP 0x00000000) @ 0x000000003ff16f84
[    0.000000] ACPI: BOOT (v001     HP $SBFTBL$ 0x06040000  LTP 0x00000001) @ 0x000000003ff16fd8
[    0.000000] ACPI: DSDT (v001 HP       MCP51M 0x06040000 MSFT 0x0100000e) @ 0x0000000000000000
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] Number of nodes 1
[    0.000000] Node 0 MemBase 0000000000000000 Limit 000000003ff00000
[    0.000000] Using 63 for the hash shift.
[    0.000000] Using node hash shift of 63
[    0.000000] Bootmem setup node 0 0000000000000000-000000003ff00000
[    0.000000] On node 0 totalpages: 257281
[    0.000000]   DMA zone: 3013 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 254268 pages, LIFO batch:31
[    0.000000]   Normal zone: 0 pages, LIFO batch:0
[    0.000000]   HighMem zone: 0 pages, LIFO batch:0
[    0.000000] Nvidia board detected. Ignoring ACPI timer override.
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:8 APIC version 16
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1 15:8 APIC version 16
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: Skipping IOAPIC probe due to 'noapic' option.
[    0.000000] Using ACPI for processor (LAPIC) configuration information
[    0.000000] Intel MultiProcessor Specification v1.4
[    0.000000]     Virtual Wire compatibility mode.
[    0.000000] OEM ID: nVIDIA   <6>Product ID: C51-MCP51    <6>APIC at: 0xFEE00000
[    0.000000] I/O APIC #2 Version 17 at 0xFEC00000.
[    0.000000] Setting APIC routing to physical flat
[    0.000000] Processors: 2
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:a0000000)
[    0.000000] Checking aperture...
[    0.000000] CPU 0: aperture @ 830c000000 size 32 MB
[    0.000000] Aperture from northbridge cpu 0 too small (32 MB)
[    0.000000] No AGP bridge found
[    0.000000] SMP: Allowing 3 CPUs, 1 hotplug CPUs
[    0.000000] Built 1 zonelists
[    0.000000] Kernel command line: root=/dev/sdb1 ro quiet splash noapic nolapic
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 131072 bytes)
[    0.000000] time.c: Using 3.579545 MHz PM timer.
[    0.000000] time.c: Detected 1808.284 MHz processor.
[   23.813567] Console: colour VGA+ 80x25
[   23.814246] Dentry cache hash table entries: 131072 (order: 8, 1048576 bytes)[   23.815393] Inode-cache hash table entries: 65536 (order: 7, 524288 bytes)
[   23.826416] Memory: 1020208k/1047552k available (2151k kernel code, 26948k reserved, 757k data, 180k init)
[   23.904844] Calibrating delay using timer specific routine.. 3623.75 BogoMIPS (lpj=7247517)
[   23.904901] Security Framework v1.0.0 initialized
[   23.904907] SELinux:  Disabled at boot.
[   23.904929] Mount-cache hash table entries: 256
[   23.905051] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)[   23.905054] CPU: L2 Cache: 512K (64 bytes/line)
[   23.905057] CPU 0(2) -> Node 0 -> Core 0
[   23.905065] mtrr: v2.0 (20020519)
[   23.905073] SMP alternatives: switching to UP code
[   23.905343] checking if image is initramfs... it is
[   24.509722] Freeing initrd memory: 7099k freed
[   24.517209] ACPI: Looking for DSDT ... not found!
[   24.519307] ACPI: setting ELCR to 0200 (from 0ca0)
[   24.676285] Using local APIC timer interrupts.
[   24.731561] Detected 12.557 MHz APIC timer.
[   24.731681] SMP alternatives: switching to SMP code
[   24.731787] Booting processor 1/2 APIC 0x1
[   24.894317] Initializing CPU#1
[   24.897144] spurious 8259A interrupt: IRQ7.
[   24.973117] Calibrating delay using timer specific routine.. 3627.31 BogoMIPS (lpj=7254639)
[   24.973123] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)[   24.973126] CPU: L2 Cache: 512K (64 bytes/line)
[   24.973129] CPU 1(2) -> Node 0 -> Core 1
[   24.973207] AMD Turion(tm) 64 X2 Mobile Technology TL-56 stepping 02
[   24.973215] CPU 1: Syncing TSC to CPU 0.
[   24.972546] CPU 1: synchronized TSC with CPU 0 (last diff 0 cycles, maxerr 488 cycles)
[   24.972554] Brought up 2 CPUs
[   24.972567] Disabling vsyscall due to use of PM timer
[   24.972569] time.c: Using PM based timekeeping.
[   24.972571] testing NMI watchdog ... OK.
[   25.012966] NET: Registered protocol family 16
[   25.012993] ACPI: bus type pci registered
[   25.013327] PCI: Using configuration type 1
[   25.017406] PCI: Using MMCONFIG at e0000000
[   25.018025] ACPI: Subsystem revision 20051216
[   25.022763] ACPI: Interpreter enabled
[   25.022766] ACPI: Using PIC for interrupt routing
[   25.023614] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   25.023617] PCI: Probing PCI hardware (bus 00)
[   25.023788] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[   25.026056] Boot video device is 0000:05:00.0
[   25.026392] PCI: Transparent bridge - 0000:00:10.0
[   25.026420] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   25.059367] ACPI: Embedded Controller [EC0] (gpe 16) interrupt mode.
[   25.059796] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P0._PRT]
[   25.060725] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR0._PRT]
[   25.061009] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR1._PRT]
[   25.061174] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR2._PRT]
[   25.061494] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   25.061790] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 9 10 *11 14 15)
[   25.062079] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 9 10 *11 14 15)
[   25.062369] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   25.062657] ACPI: PCI Interrupt Link [LK1E] (IRQs 5 7 9 10 *11 14 15)
[   25.062944] ACPI: PCI Interrupt Link [LK2E] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   25.063235] ACPI: PCI Interrupt Link [LK3E] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   25.063532] ACPI: PCI Interrupt Link [LK4E] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   25.063822] ACPI: PCI Interrupt Link [LSMB] (IRQs 5 7 9 *10 11 14 15)
[   25.064110] ACPI: PCI Interrupt Link [LPMU] (IRQs 5 7 9 *10 11 14 15)
[   25.064426] ACPI: PCI Interrupt Link [LUS0] (IRQs 5 7 9 10 *11 14 15)
[   25.064714] ACPI: PCI Interrupt Link [LUS2] (IRQs 5 *7 9 10 11 14 15)
[   25.065005] ACPI: PCI Interrupt Link [LMAC] (IRQs 5 7 9 *10 11 14 15)
[   25.065299] ACPI: PCI Interrupt Link [LAZA] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   25.065592] ACPI: PCI Interrupt Link [LACI] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   25.065881] ACPI: PCI Interrupt Link [LMCI] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   25.066170] ACPI: PCI Interrupt Link [LPID] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   25.066468] ACPI: PCI Interrupt Link [LTID] (IRQs *5 7 9 10 11 14 15)
[   25.066758] ACPI: PCI Interrupt Link [LSI1] (IRQs 5 7 9 *10 11 14 15), disabled.
[   25.066885] Linux Plug and Play Support v0.97 (c) Adam Belay
[   25.066894] pnp: PnP ACPI init
[   25.069150] pnp: PnP ACPI: found 12 devices
[   25.069167] PCI: Using ACPI for IRQ routing
[   25.069171] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   25.069312] PCI-DMA: Disabling IOMMU.
[   25.069785] pnp: 00:04: ioport range 0x1000-0x107f could not be reserved
[   25.069788] pnp: 00:04: ioport range 0x1080-0x10ff has been reserved
[   25.069792] pnp: 00:04: ioport range 0x1400-0x147f has been reserved
[   25.069795] pnp: 00:04: ioport range 0x1480-0x14ff could not be reserved
[   25.069799] pnp: 00:04: ioport range 0x1800-0x187f has been reserved
[   25.069802] pnp: 00:04: ioport range 0x1880-0x18ff has been reserved
[   25.069805] pnp: 00:04: ioport range 0x2000-0x203f has been reserved
[   25.070009] PCI: Bridge: 0000:00:02.0
[   25.070012]   IO window: 4000-4fff
[   25.070016]   MEM window: c0200000-c03fffff
[   25.070019]   PREFETCH window: c3200000-c33fffff
[   25.070021] PCI: Bridge: 0000:00:03.0
[   25.070023]   IO window: disabled.
[   25.070026]   MEM window: c0400000-c05fffff
[   25.070028]   PREFETCH window: disabled.
[   25.070033] PCI: Failed to allocate mem resource #6:20000@e0000000 for 0000:05:00.0
[   25.070084] PCI: Bridge: 0000:00:04.0
[   25.070086]   IO window: 5000-5fff
[   25.070089]   MEM window: c1000000-c2ffffff
[   25.070092]   PREFETCH window: d0000000-dfffffff
[   25.070095] PCI: Bridge: 0000:00:10.0
[   25.070097]   IO window: disabled.
[   25.070101]   MEM window: c3000000-c30fffff
[   25.070103]   PREFETCH window: disabled.
[   25.070113] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   25.070118] PCI: Setting latency timer of device 0000:00:03.0 to 64
[   25.070123] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   25.070130] PCI: Setting latency timer of device 0000:00:10.0 to 64
[   25.070247] Simple Boot Flag at 0x36 set to 0x1
[   25.070447] IA32 emulation $Id: sys_ia32.c,v 1.32 2002/03/24 13:02:28 ak Exp $
[   25.070792] audit: initializing netlink socket (disabled)
[   25.070801] audit(1160231939.176:1): initialized
[   25.070958] VFS: Disk quotas dquot_6.5.1
[   25.070977] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   25.071032] Initializing Cryptographic API
[   25.071035] io scheduler noop registered
[   25.071045] io scheduler anticipatory registered
[   25.071053] io scheduler deadline registered
[   25.071072] io scheduler cfq registered
[   25.071564] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   25.071568] pcie_portdrv_probe->Dev[02fc:10de] has invalid IRQ. Check vendor BIOS
[   25.071585] assign_interrupt_mode Found MSI capability
[   25.071621] Allocate Port Service[pcie00]
[   25.071657] Allocate Port Service[pcie03]
[   25.071695] PCI: Setting latency timer of device 0000:00:03.0 to 64
[   25.071698] pcie_portdrv_probe->Dev[02fd:10de] has invalid IRQ. Check vendor BIOS
[   25.071712] assign_interrupt_mode Found MSI capability
[   25.071729] Allocate Port Service[pcie00]
[   25.071758] Allocate Port Service[pcie03]
[   25.071791] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   25.071795] pcie_portdrv_probe->Dev[02fb:10de] has invalid IRQ. Check vendor BIOS
[   25.071809] assign_interrupt_mode Found MSI capability
[   25.071826] Allocate Port Service[pcie00]
[   25.071857] Allocate Port Service[pcie03]
[   25.087697] Real Time Clock Driver v1.12
[   25.087737] Linux agpgart interface v0.101 (c) Dave Jones
[   25.087837] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[   25.114844] serio: i8042 AUX port at 0x60,0x64 irq 12
[   25.116909] serio: i8042 KBD port at 0x60,0x64 irq 1
[   25.116947] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[   25.119206] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   25.119256] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   25.119259] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   25.119489] mice: PS/2 mouse device common for all mice
[   25.122335] NET: Registered protocol family 2
[   25.180427] IP route cache hash table entries: 32768 (order: 6, 262144 bytes)[   25.180633] TCP established hash table entries: 131072 (order: 9, 2097152 bytes)
[   25.187507] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   25.188397] TCP: Hash tables configured (established 131072 bind 65536)
[   25.188400] TCP reno registered
[   25.188493] TCP bic registered
[   25.188503] NET: Registered protocol family 1
[   25.188510] NET: Registered protocol family 8
[   25.188512] NET: Registered protocol family 20
[   25.188622] ACPI wakeup devices:
[   25.188624] MAC0
[   25.188625] ACPI: (supports S0 S3 S4 S5)
[   25.188692] Freeing unused kernel memory: 180k freed
[   25.192043] input: AT Translated Set 2 keyboard as /class/input/input0
[   25.235695] vga16fb: initializing
[   25.235700] vga16fb: mapped to 0xffff8100000a0000
[   25.486678] Console: switching to colour frame buffer device 80x25
[   25.486684] fb0: VGA16 VGA frame buffer device
[   26.506251] Capability LSM initialized
[   26.578740] ACPI: Thermal Zone [THRM] (65 C)
[   27.086042] SCSI subsystem initialized
[   27.087979] ACPI: bus type scsi registered
[   27.087982] libata version 1.20 loaded.
[   27.089704] sata_nv 0000:00:0e.0: version 0.8
[   27.089717] PCI: Enabling device 0000:00:0e.0 (0005 -> 0007)
[   27.090013] ACPI: PCI Interrupt Link [LTID] enabled at IRQ 5
[   27.090016] PCI: setting IRQ 5 as level-triggered
[   27.090022] ACPI: PCI Interrupt 0000:00:0e.0[A] -> Link [LTID] -> GSI 5 (level, low) -> IRQ 5
[   27.090203] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[   27.090283] ata1: SATA max UDMA/133 cmd 0x30C0 ctl 0x30B6 bmdma 0x3090 irq 5
[   27.090306] ata2: SATA max UDMA/133 cmd 0x30B8 ctl 0x30B2 bmdma 0x3098 irq 5
[   27.455381] ata1: dev 0 cfg 00:0c5a 49:2f00 82:306b 83:7c09 84:6003 85:3069 86:3c09 87:6003 88:203f 93:0000
[   27.455387] ata1: dev 0 ATA-7, max UDMA/100, 156301488 sectors: LBA48
[   27.456635] sata_get_dev_handle: SATA dev addr=0xe0000, handle=0xffff810037fdf300
[   27.460058] ata1: dev 0 configured for UDMA/100
[   27.461266] sata_get_dev_handle: SATA dev addr=0xe0000, handle=0xffff810037fdf300
[   27.464394] scsi0 : sata_nv
[   27.667088] ata2: no device found (phy stat 00000000)
[   27.667092] scsi1 : sata_nv
[   27.667816]   Vendor: ATA       Model: ST98823AS         Rev: 7.24
[   27.667826]   Type:   Direct-Access                      ANSI SCSI revision: 05
[   27.668278] PCI: Enabling device 0000:00:0f.0 (0005 -> 0007)
[   27.668568] ACPI: PCI Interrupt Link [LSI1] enabled at IRQ 10
[   27.668572] PCI: setting IRQ 10 as level-triggered
[   27.668577] ACPI: PCI Interrupt 0000:00:0f.0[A] -> Link [LSI1] -> GSI 10 (level, low) -> IRQ 10
[   27.668734] PCI: Setting latency timer of device 0000:00:0f.0 to 64
[   27.668787] ata3: SATA max UDMA/133 cmd 0x30D8 ctl 0x30CE bmdma 0x30A0 irq 10[   27.668810] ata4: SATA max UDMA/133 cmd 0x30D0 ctl 0x30CA bmdma 0x30A8 irq 10[   27.672978] Driver 'sd' needs updating - please use bus_type methods
[   27.673053] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[   27.673073] SCSI device sda: drive cache: write back
[   27.673128] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[   27.673144] SCSI device sda: drive cache: write back
[   27.673149]  sda: sda1 sda2 sda3
[   27.681570] sd 0:0:0:0: Attached scsi disk sda
[   28.035106] ata3: dev 0 cfg 00:0c5a 49:2f00 82:306b 83:7c09 84:6003 85:3069 86:3c09 87:6003 88:203f 93:0000
[   28.035113] ata3: dev 0 ATA-7, max UDMA/100, 156301488 sectors: LBA48
[   28.036368] sata_get_dev_handle: SATA dev addr=0xf0000, handle=0xffff810037fdf7c0
[   28.039795] ata3: dev 0 configured for UDMA/100
[   28.041006] sata_get_dev_handle: SATA dev addr=0xf0000, handle=0xffff810037fdf7c0
[   28.044140] scsi2 : sata_nv
[   28.246815] ata4: no device found (phy stat 00000000)
[   28.246820] scsi3 : sata_nv
[   28.247585]   Vendor: ATA       Model: ST98823AS         Rev: 7.24
[   28.247596]   Type:   Direct-Access                      ANSI SCSI revision: 05
[   28.248055] SCSI device sdb: 156301488 512-byte hdwr sectors (80026 MB)
[   28.248074] SCSI device sdb: drive cache: write back
[   28.248234] SCSI device sdb: 156301488 512-byte hdwr sectors (80026 MB)
[   28.248251] SCSI device sdb: drive cache: write back
[   28.248254]  sdb: sdb1 sdb2 < sdb5 >
[   28.288297] sd 2:0:0:0: Attached scsi disk sdb
[   28.289949] NFORCE-MCP51: IDE controller at PCI slot 0000:00:0d.0
[   28.289968] NFORCE-MCP51: chipset revision 241
[   28.289971] NFORCE-MCP51: not 100% native mode: will probe irqs later
[   28.289975] NFORCE-MCP51: BIOS didn't set cable bits correctly. Enabling workaround.
[   28.289980] NFORCE-MCP51: 0000:00:0d.0 (rev f1) UDMA133 controller
[   28.289988]     ide0: BM-DMA at 0x3080-0x3087, BIOS settings: hda:DMA, hdb:pio
[   28.289998] Probing IDE interface ide0...
[   29.026557] hda: HL-DT-ST DVDRAM GSA-4084N, ATAPI CD/DVD-ROM drive
[   29.363582] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   29.375497] hda: ATAPI 24X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, DMA[   29.375505] Uniform CD-ROM driver Revision: 3.20
[   29.478405] ieee1394: Initialized config rom entry `ip1394'
[   29.478456] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.54.
[   29.478812] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 10
[   29.478815] ACPI: PCI Interrupt 0000:00:14.0[A] -> Link [LMAC] -> GSI 10 (level, low) -> IRQ 10
[   29.478822] PCI: Setting latency timer of device 0000:00:14.0 to 64
[   29.478831] forcedeth: using HIGHDMA
[   29.489819] usbcore: registered new driver usbfs
[   29.490576] usbcore: registered new driver hub
[   29.492392] ACPI: PCI Interrupt Link [LUS2] enabled at IRQ 7
[   29.492396] PCI: setting IRQ 7 as level-triggered
[   29.492401] ACPI: PCI Interrupt 0000:00:0b.1[B] -> Link [LUS2] -> GSI 7 (level, low) -> IRQ 7
[   29.492592] PCI: Setting latency timer of device 0000:00:0b.1 to 64
[   29.492598] ehci_hcd 0000:00:0b.1: EHCI Host Controller
[   29.492639] ehci_hcd 0000:00:0b.1: debug port 1
[   29.492643] PCI: cache line size of 64 is not supported by device 0000:00:0b.1
[   29.492902] ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 1
[   29.492911] ehci_hcd 0000:00:0b.1: irq 7, io mem 0xc0005000
[   29.492921] ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   29.495226] hub 1-0:1.0: USB hub found
[   29.495234] hub 1-0:1.0: 8 ports detected
[   29.500704] ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[   29.501059] ACPI: PCI Interrupt Link [LUS0] enabled at IRQ 11
[   29.501062] PCI: setting IRQ 11 as level-triggered
[   29.501068] ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [LUS0] -> GSI 11 (level, low) -> IRQ 11
[   29.501263] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[   29.501269] ohci_hcd 0000:00:0b.0: OHCI Host Controller
[   29.706291] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 2
[   29.706300] ohci_hcd 0000:00:0b.0: irq 11, io mem 0xc0004000
[   29.764353] hub 2-0:1.0: USB hub found
[   29.764364] hub 2-0:1.0: 8 ports detected
[   30.006192] eth0: forcedeth.c: subsystem: 0103c:30b7 bound to 0000:00:14.0
[   30.006318] ohci1394: $Rev: 1313 $ Ben Collins <bcollins@debian.org>
[   30.006643] ACPI: PCI Interrupt Link [LNK1] enabled at IRQ 11
[   30.006647] ACPI: PCI Interrupt 0000:07:05.0[A] -> Link [LNK1] -> GSI 11 (level, low) -> IRQ 11
[   30.058966] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[11]  MMIO=[c3000000-c30007ff]  Max Packet=[2048]
[   30.088359] Probing IDE interface ide1...
[   30.161911] usb 1-4: new high speed USB device using ehci_hcd and address 3
[   30.597703] usb 2-3: new full speed USB device using ohci_hcd and address 2
[   30.714366] Attempting manual resume
[   30.752321] EXT3-fs: mounted filesystem with ordered data mode.
[   30.752650] kjournald starting.  Commit interval 5 seconds
[   31.353531] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[009fc0009226ad00]
[   38.327099] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   38.327121] sd 2:0:0:0: Attached scsi generic sg1 type 0
[   39.901144] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   39.919226] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   40.066955] nvidia: module license 'NVIDIA' taints kernel.
[   40.071455] ACPI: PCI Interrupt Link [LK1E] enabled at IRQ 11
[   40.071459] ACPI: PCI Interrupt 0000:05:00.0[A] -> Link [LK1E] -> GSI 11 (level, low) -> IRQ 11
[   40.071469] PCI: Setting latency timer of device 0000:05:00.0 to 64
[   40.071631] NVRM: loading NVIDIA Linux x86_64 Kernel Module  1.0-8762  Mon May 15 13:58:14 PDT 2006
[   40.164363] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 9
[   40.164367] PCI: setting IRQ 9 as level-triggered
[   40.164371] ACPI: PCI Interrupt 0000:00:10.1[B] -> Link [LAZA] -> GSI 9 (level, low) -> IRQ 9
[   40.164533] PCI: Setting latency timer of device 0000:00:10.1 to 64
[   40.177437] sdhci: Secure Digital Host Controller Interface driver, 0.10
[   40.177440] sdhci: Copyright(c) Pierre Ossman
[   40.290344] Bluetooth: Core ver 2.8
[   40.290348] NET: Registered protocol family 31
[   40.290351] Bluetooth: HCI device and connection manager initialized
[   40.290361] Bluetooth: HCI socket layer initialized
[   40.308377] Bluetooth: HCI USB driver ver 2.9
[   40.309669] usbcore: registered new driver hci_usb
[   40.574211] input: PC Speaker as /class/input/input1
[   40.913307] ACPI: PCI Interrupt Link [LNK2] enabled at IRQ 11
[   40.913312] ACPI: PCI Interrupt 0000:07:05.1[B] -> Link [LNK2] -> GSI 11 (level, low) -> IRQ 11
[   40.968632] sdhci: ============== REGISTER DUMP ==============
[   40.968639] sdhci: Sys addr: 0x00000000 | Version:  0x00000200
[   40.968643] sdhci: Blk size: 0x00000000 | Blk cnt:  0x00000000
[   40.968647] sdhci: Argument: 0x00000000 | Trn mode: 0x00000000
[   40.968650] sdhci: Present:  0x01f20000 | Host ctl: 0x00000000
[   40.968654] sdhci: Power:    0x00000000 | Blk gap:  0x00000000
[   40.968657] sdhci: Walk up:  0x00000000 | Clock:    0x00000000
[   40.968661] sdhci: Timeout:  0x0000000e | Int stat: 0x00000000
[   40.968665] sdhci: Int enab: 0xe1ff00cf | Sig enab: 0xe1ff00cf
[   40.968669] sdhci: AC12 err: 0x00000000 | Slot int: 0x00000000
[   40.968673] sdhci: Caps:     0x018021a1 | Max curr: 0x00000040
[   40.968676] sdhci: ===========================================
[   41.018807] mmc0: SDHCI at 0xc3000800 irq 11 DMA
[   41.170052] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x1a0b1, caps: 0xa04713/0x200000
[   41.234760] input: SynPS/2 Synaptics TouchPad as /class/input/input2
[   41.271935] lp: driver loaded but no devices found
[   41.420428] sbp2: $Rev: 1306 $ Ben Collins <bcollins@debian.org>
[   41.420432] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)
[   41.420434] ieee1394: sbp2: Try serialize_io=0 for better performance
[   41.429138] ts: Compaq touchscreen protocol output
[   41.517532] Adding 3004112k swap on /dev/sdb5.  Priority:-1 extents:1 across:3004112k
[   41.593357] EXT3 FS on sdb1, internal journal
[   41.779586] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[   41.779591] md: bitmap version 4.39
[   42.192967] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[   42.818477] cdrom: open failed.
[   44.913908] NET: Registered protocol family 17
[   54.516024] vbetool[4072]: segfault at 0000000000003632 rip 0000000000425781 rsp 00007fffffa76940 error 4
[   54.683749] ACPI: AC Adapter [ACAD] (on-line)
[   54.717694] ACPI: Battery Slot [BAT0] (battery present)
[   54.791717] ACPI: Power Button (FF) [PWRF]
[   54.791727] ACPI: Power Button (CM) [PWRB]
[   54.791734] ACPI: Sleep Button (CM) [SLPB]
[   54.791740] ACPI: Lid Switch [LID]
[   54.876397] ibm_acpi: ec object not found
[   56.130140] pcc_acpi: loading...
[   56.168765] wmi_add device=ffff810037ec3800
[   56.168769] calling WQBA
[   57.355180] ACPI: Video Device [UVGA] (multi-head: yes  rom: no  post: no)
[   57.355311] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   57.742812] powernow-k8: Found 2 AMD Athlon 64 / Opteron processors (version 1.50.4)
[   57.742951] powernow-k8:    0 : fid 0xa (1800 MHz), vid 0x13 (1075 mV)
[   57.742955] powernow-k8:    1 : fid 0x8 (1600 MHz), vid 0x15 (1025 mV)
[   57.742959] powernow-k8:    2 : fid 0x0 (800 MHz), vid 0x1e (800 mV)
[   57.742964] cpu_init done, current fid 0xa, vid 0x13
[   63.609506] ppdev: user-space parallel port driver
[   69.987984] Bluetooth: L2CAP ver 2.8
[   69.987988] Bluetooth: L2CAP socket layer initialized
[   70.001124] Bluetooth: RFCOMM socket layer initialized
[   70.001138] Bluetooth: RFCOMM TTY layer initialized
[   70.001140] Bluetooth: RFCOMM ver 1.7
[   78.254355] NET: Registered protocol family 10
[   78.254473] lo: Disabled Privacy Extensions
[   78.254558] IPv6 over IPv4 tunneling driver
[  152.671440] ndiswrapper version 1.25 loaded (preempt=yes,smp=yes)
[  152.766929] ndiswrapper (load_pe_images:577): fixing KI_USER_SHARED_DATA address in the driver
[  152.768855] ndiswrapper: driver bcmwl5 (Broadcom,03/23/2006, 4.40.19.0) loaded
[  152.769149] ACPI: PCI Interrupt 0000:03:00.0[A] -> Link [LK1E] -> GSI 11 (level, low) -> IRQ 11
[  152.769181] PCI: Setting latency timer of device 0000:03:00.0 to 64
[  152.775715] ndiswrapper: using IRQ 11
[  153.458651] wlan0: vendor: ''
[  153.458657] wlan0: ethernet device 00:14:a5:c4:1d:bd using NDIS driver bcmwl5, 14E4:4312.5.conf
[  153.458692] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[  153.464037] usbcore: registered new driver ndiswrapper
[  153.493874] ndiswrapper: changing interface name from 'wlan0' to 'eth1'
[  153.538451] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  154.184709] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[  164.705668] eth1: no IPv6 routers present
joergenlie@joergenlie-laptop:~$

there mist be a solution to this. Does it have something to do with the fact that I hawe eth1 and ndiswrapper wants wlan0?

Another thing how do i paste this in here with a scroll option?

the laptop is great. I'll write a resume when i get things working.

thanks!

Jørgen Norway

---

### Post by joergenlie on 2006-10-07
ok now I've reinstalled everything and when i modprobe ndiswrapper iget:

adding "alias wlan0 ndiswrapper" to /etc/modprobe.d/ndiswrapper ...
couldn't add module alias:  at /usr/sbin/ndiswrapper line 705.

what ever that means. 

jørgen

---

### Post by joergenlie on 2006-10-08
Man that was easy! Just manually added ndiswrapper to /etc/modules by writing ndiswrapper at the end of the modules file.

now I can configure the rest:-D 

jørgen

---

### Post by hakoni on 2006-10-30
Hi Jørgen, I'm about to buy a Pavilion dv9074 to run linux on, do you have any more info to share about this laptop? what works and what doesn't? Hows the nvidia driver? tried dual-screen on it? 3D support ok?

Also interrested in the harddrive speed, (big bottleneck in my current laptop) if you could do any benchmarks, (hdparm, bonnie++ or similiar), it would have been great!!!

Håkon.

---

### Post by elizleisndahizle on 2006-11-01
I haven't had any problems with the video drivers, but I have read about people having problems with it.  I have the 7600 go.  I have a dv9000z, I have not gotten wireless to work with ubuntu the broadcom wireless card is not minipci either so no swapping it out with an atheros which i was hoping to do.  Sound absolutely sucks in linux but is beautiful in windows.  The headphone jack and spdif jack doesn't work, when you plug something in it just keeps playing out of the laptop speaker, suck.  Quickplay buttons work though.  I imagine that they are working on HD Audio for linux, once they finish this I am sure it will work wonderfully.

---

### Post by drunken-wallaby on 2006-12-12
joergenlie: do you have problems with messages like "irq 7 disabling" and that the usb adaptor doesn't work afterwards? i'm asking because i have a pavilion dv9043ea and having _big_ problems to get this beast running. i've tried almost every combination of noapic nolapic routeirq biosirq pnpbios=off ... but the bios is still buggy. so i'm wondering, if you experience anything like this as well...

elizleisdahilzle: audio (headphone jack) does work. with dapper/edgy you have to compile alsa1.0.13 from source and add a line to /etc/modprobe.d/alsa-base. in feisty it works out of the box!

i haven't gotten wlan to work with the free bcm43xx drivers as well, but managed to got it working with ndiswrapper quite easily.

---

### Post by joergenlie on 2006-12-28
yes; I get the irq 7 message as well, do not know what thats about?
the lap boots  with the "noapic" option. 
The best wireles I get with a compiled ndiswrapper 1.26, works wonderfully with network-manager too.

webcam is a pain in the a...., You got it to work?

I tried the 32 bit version of ubuntu and that did npt work well for some reason, so I'm using 64-bit.

Also problems with sound through the jack.


Jørgen

---

### Post by Kimlorentz on 2007-03-24
How did install the Ubuntu 6.10 on the HP Pavilion dv9074.
When I try to install it, it hangs during boot up.

---

### Post by jogu on 2007-03-25
> **Kimlorentz said:**
> How did install the Ubuntu 6.10 on the HP Pavilion dv9074.
When I try to install it, it hangs during boot up.

If you're installing using a live-CD you press F6 in the main menu and extra boot options (for example "noapic noacpi nosmp") between "splash" and "--".

See also 
[https://wiki.ubuntu.com/LaptopTestingTeam/HPPavilionDV9074ea](https://wiki.ubuntu.com/LaptopTestingTeam/HPPavilionDV9074ea)
To all, feel free to add comments to this testing report :)

---

