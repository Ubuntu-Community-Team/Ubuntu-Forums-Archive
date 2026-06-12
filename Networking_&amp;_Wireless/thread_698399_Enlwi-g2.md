---
title: "Enlwi-g2"
date: 2008-02-16
forum: Networking &amp; Wireless
---

### Post by pbewig on 2008-02-16
I recently built a computer based on an Asus motherboard, AMD 64, 2GB RAM with an Encore ENLWI-G2 wifi card, running Ubuntu 7.10.  I am unable to get the wifi card to connect to my router.  Here is dmesg after a clean startup:

[    0.000000] Linux version 2.6.22-14-generic (buildd@king) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Thu Jan 31 23:33:13 UTC 2008 (Ubuntu 2.6.22-14.51-generic)
[    0.000000] Command line: root=UUID=a74fe032-7ae9-41c6-b168-82f3f3738250 ro quiet splash
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007dee0000 (usable)
[    0.000000]  BIOS-e820: 000000007dee0000 - 000000007dee3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007dee3000 - 000000007def0000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007def0000 - 000000007df00000 (reserved)
[    0.000000]  BIOS-e820: 000000007e000000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f4000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 515808) 1 entries of 3200 used
[    0.000000] end_pfn_map = 1048576
[    0.000000] DMI 2.4 present.
[    0.000000] ACPI: RSDP signature @ 0xFFFF8100000F6A90 checksum 0
[    0.000000] ACPI: RSDP 000F6A90, 0024 (r2 Nvidia)
[    0.000000] ACPI: XSDT 7DEE3100, 0054 (r1 _ASUS_ Notebook 42302E31 AWRD        0)
[    0.000000] ACPI: FACP 7DEEA400, 00F4 (r3 _ASUS_ Notebook 42302E31 AWRD        0)
[    0.000000] ACPI: DSDT 7DEE3280, 710A (r1 _ASUS_ Notebook     1000 MSFT  3000000)
[    0.000000] ACPI: FACS 7DEE0000, 0040
[    0.000000] ACPI: SLIC 7DEEA600, 0176 (r1 _ASUS_ Notebook 42302E31 AWRD        0)
[    0.000000] ACPI: SSDT 7DEEA7C0, 0115 (r1 _ASUS_ Notebook        1  LTP        1)
[    0.000000] ACPI: HPET 7DEEA940, 0038 (r1 _ASUS_ Notebook 42302E31 AWRD       98)
[    0.000000] ACPI: MCFG 7DEEA9C0, 003C (r1 _ASUS_ Notebook 42302E31 AWRD        0)
[    0.000000] ACPI: APIC 7DEEA540, 007C (r1 _ASUS_ Notebook 42302E31 AWRD        0)
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-000000007dee0000
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 515808) 1 entries of 3200 used
[    0.000000] Bootmem setup node 0 0000000000000000-000000007dee0000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   DMA32        4096 ->  1048576
[    0.000000]   Normal    1048576 ->  1048576
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0:        0 ->      159
[    0.000000]     0:      256 ->   515808
[    0.000000] On node 0 totalpages: 515711
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 1125 pages reserved
[    0.000000]   DMA zone: 2818 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 6996 pages used for memmap
[    0.000000]   DMA32 zone: 504716 pages, LIFO batch:31
[    0.000000]   Normal zone: 0 pages used for memmap
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 (Bootup-CPU)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.
[    0.000000] Setting APIC routing to flat
[    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfefff000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:70000000)
[    0.000000] SMP: Allowing 2 CPUs, 1 hotplug CPUs
[    0.000000] PERCPU: Allocating 34696 bytes of per cpu data
[    0.000000] Built 1 zonelists.  Total pages: 507534
[    0.000000] Kernel command line: root=UUID=a74fe032-7ae9-41c6-b168-82f3f3738250 ro quiet splash
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] Extended CMOS year: 2000
[   11.779531] time.c: Detected 2210.185 MHz processor.
[   11.782402] Console: colour VGA+ 80x25
[   11.782417] Checking aperture...
[   11.782420] CPU 0: aperture @ d818000000 size 32 MB
[   11.782421] Aperture too small (32 MB)
[   11.788249] No AGP bridge found
[   11.803816] Memory: 2022736k/2063232k available (2274k kernel code, 40108k reserved, 1181k data, 296k init)
[   11.803859] SLUB: Genslabs=23, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   11.882218] Calibrating delay using timer specific routine.. 4424.59 BogoMIPS (lpj=8849190)
[   11.882246] Security Framework v1.0.0 initialized
[   11.882251] SELinux:  Disabled at boot.
[   11.882397] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
[   11.883431] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
[   11.883937] Mount-cache hash table entries: 256
[   11.884050] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   11.884052] CPU: L2 Cache: 1024K (64 bytes/line)
[   11.884055] CPU 0/0 -> Node 0
[   11.884071] SMP alternatives: switching to UP code
[   11.884280] Early unpacking initramfs... done
[   12.146575] ACPI: Core revision 20070126
[   12.146631] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   12.191613] Using local APIC timer interrupts.
[   12.236832] result 12557872
[   12.236834] Detected 12.557 MHz APIC timer.
[   12.238000] Brought up 1 CPUs
[   12.238193] NET: Registered protocol family 16
[   12.238256] ACPI: bus type pci registered
[   12.238260] PCI: Using configuration type 1
[   12.239407] ACPI: EC: Look up EC in DSDT
[   12.245729] ACPI: Interpreter enabled
[   12.245734] ACPI: (supports S0 S1 S3 S4 S5)
[   12.245753] ACPI: Using IOAPIC for interrupt routing
[   12.254772] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   12.254780] PCI: Probing PCI hardware (bus 00)
[   12.255294] PCI: Transparent bridge - 0000:00:04.0
[   12.255474] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   12.255692] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[   12.295884] ACPI: PCI Interrupt Link [LNK1] (IRQs *5 7 9 10 11 14 15)
[   12.296058] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 9 *10 11 14 15)
[   12.296232] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   12.296403] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   12.296575] ACPI: PCI Interrupt Link [LNK5] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   12.296746] ACPI: PCI Interrupt Link [LNK6] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   12.296917] ACPI: PCI Interrupt Link [LNK7] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   12.297089] ACPI: PCI Interrupt Link [LNK8] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   12.297262] ACPI: PCI Interrupt Link [LIGP] (IRQs *5 7 9 10 11 14 15)
[   12.297433] ACPI: PCI Interrupt Link [LP2P] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   12.297606] ACPI: PCI Interrupt Link [LUBA] (IRQs 5 7 9 *10 11 14 15)
[   12.297779] ACPI: PCI Interrupt Link [LMAC] (IRQs 5 7 9 *10 11 14 15)
[   12.297961] ACPI: PCI Interrupt Link [LAZA] (IRQs 5 7 9 10 *11 14 15)
[   12.298134] ACPI: PCI Interrupt Link [LPMU] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   12.298307] ACPI: PCI Interrupt Link [LSMB] (IRQs *5 7 9 10 11 14 15)
[   12.298483] ACPI: PCI Interrupt Link [LUB2] (IRQs 5 7 9 10 *11 14 15)
[   12.298655] ACPI: PCI Interrupt Link [LIDE] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   12.298828] ACPI: PCI Interrupt Link [LSID] (IRQs 5 7 9 10 *11 14 15)
[   12.299036] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0
[   12.299235] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0
[   12.299433] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0, disabled.
[   12.299630] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0, disabled.
[   12.299827] ACPI: PCI Interrupt Link [APC5] (IRQs 16) *0, disabled.
[   12.300024] ACPI: PCI Interrupt Link [APC6] (IRQs 16) *0, disabled.
[   12.300221] ACPI: PCI Interrupt Link [APC7] (IRQs 16) *0, disabled.
[   12.300421] ACPI: PCI Interrupt Link [APC8] (IRQs 16) *0, disabled.
[   12.300619] ACPI: PCI Interrupt Link [AIGP] (IRQs 22 23) *0
[   12.300816] ACPI: PCI Interrupt Link [APCF] (IRQs 22 23) *0
[   12.301014] ACPI: PCI Interrupt Link [APCH] (IRQs 22 23) *0
[   12.301212] ACPI: PCI Interrupt Link [APMU] (IRQs 22 23) *0, disabled.
[   12.301410] ACPI: PCI Interrupt Link [AAZA] (IRQs 22 23) *0
[   12.301608] ACPI: PCI Interrupt Link [APCS] (IRQs 22 23) *0
[   12.301805] ACPI: PCI Interrupt Link [APCL] (IRQs 22 23) *0
[   12.302006] ACPI: PCI Interrupt Link [APCM] (IRQs 22 23) *0, disabled.
[   12.302204] ACPI: PCI Interrupt Link [APCZ] (IRQs 22 23) *0, disabled.
[   12.302402] ACPI: PCI Interrupt Link [APSI] (IRQs 20) *0
[   12.302483] Linux Plug and Play Support v0.97 (c) Adam Belay
[   12.302491] pnp: PnP ACPI init
[   12.302499] ACPI: bus type pnp registered
[   12.307180] pnp: PnP ACPI: found 14 devices
[   12.307181] ACPI: ACPI bus type pnp unregistered
[   12.307221] PCI: Using ACPI for IRQ routing
[   12.307224] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   12.307277] NET: Registered protocol family 8
[   12.307279] NET: Registered protocol family 20
[   12.307331] hpet0: at MMIO 0xfefff000, IRQs 2, 8, 31
[   12.307335] hpet0: 3 32-bit timers, 25000000 Hz
[   12.308378] pnp: 00:01: ioport range 0x1000-0x107f has been reserved
[   12.308381] pnp: 00:01: ioport range 0x1080-0x10ff has been reserved
[   12.308383] pnp: 00:01: ioport range 0x1400-0x147f has been reserved
[   12.308385] pnp: 00:01: ioport range 0x1480-0x14ff has been reserved
[   12.308388] pnp: 00:01: ioport range 0x1800-0x187f has been reserved
[   12.308390] pnp: 00:01: ioport range 0x1880-0x18ff has been reserved
[   12.308398] pnp: 00:0c: iomem range 0xf0000000-0xf3ffffff could not be reserved
[   12.308402] pnp: 00:0d: iomem range 0xcec00-0xcffff has been reserved
[   12.308405] pnp: 00:0d: iomem range 0xf0000-0xf7fff could not be reserved
[   12.308407] pnp: 00:0d: iomem range 0xf8000-0xfbfff could not be reserved
[   12.308410] pnp: 00:0d: iomem range 0xfc000-0xfffff could not be reserved
[   12.308621] PCI: Bridge: 0000:00:04.0
[   12.308624]   IO window: c000-cfff
[   12.308627]   MEM window: fdf00000-fdffffff
[   12.308629]   PREFETCH window: fd800000-fd8fffff
[   12.308632] PCI: Bridge: 0000:00:09.0
[   12.308634]   IO window: b000-bfff
[   12.308636]   MEM window: fde00000-fdefffff
[   12.308639]   PREFETCH window: fdd00000-fddfffff
[   12.308641] PCI: Bridge: 0000:00:0b.0
[   12.308643]   IO window: a000-afff
[   12.308645]   MEM window: fdc00000-fdcfffff
[   12.308647]   PREFETCH window: fdb00000-fdbfffff
[   12.308649] PCI: Bridge: 0000:00:0c.0
[   12.308651]   IO window: 9000-9fff
[   12.308654]   MEM window: fda00000-fdafffff
[   12.308656]   PREFETCH window: fd900000-fd9fffff
[   12.308664] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   12.308670] PCI: Setting latency timer of device 0000:00:09.0 to 64
[   12.308675] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[   12.308680] PCI: Setting latency timer of device 0000:00:0c.0 to 64
[   12.308689] NET: Registered protocol family 2
[   12.309927] Time: tsc clocksource has been installed.
[   12.341961] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
[   12.342533] TCP established hash table entries: 262144 (order: 10, 6291456 bytes)
[   12.345113] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   12.345623] TCP: Hash tables configured (established 262144 bind 65536)
[   12.345625] TCP reno registered
[   12.354001] checking if image is initramfs... it is
[   12.864123] Freeing initrd memory: 7201k freed
[   12.867851] audit: initializing netlink socket (disabled)
[   12.867861] audit(1203169295.044:1): initialized
[   12.869440] VFS: Disk quotas dquot_6.5.1
[   12.869483] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   12.869558] io scheduler noop registered
[   12.869560] io scheduler anticipatory registered
[   12.869561] io scheduler deadline registered
[   12.869634] io scheduler cfq registered (default)
[   12.897800] Boot video device is 0000:00:0d.0
[   12.897913] PCI: Setting latency timer of device 0000:00:09.0 to 64
[   12.897931] assign_interrupt_mode Found MSI capability
[   12.897933] Allocate Port Service[0000:00:09.0:pcie00]
[   12.897984] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[   12.898001] assign_interrupt_mode Found MSI capability
[   12.898003] Allocate Port Service[0000:00:0b.0:pcie00]
[   12.898047] PCI: Setting latency timer of device 0000:00:0c.0 to 64
[   12.898064] assign_interrupt_mode Found MSI capability
[   12.898066] Allocate Port Service[0000:00:0c.0:pcie00]
[   12.916573] Real Time Clock Driver v1.12ac
[   12.916735] hpet_resources: 0xfefff000 is busy
[   12.916761] Linux agpgart interface v0.102 (c) Dave Jones
[   12.916763] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   12.916928] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   12.917330] 00:08: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   12.917866] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   12.918022] input: Macintosh mouse button emulation as /class/input/input0
[   12.918075] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   12.918837] serio: i8042 KBD port at 0x60,0x64 irq 1
[   12.918841] serio: i8042 AUX port at 0x60,0x64 irq 12
[   12.918971] mice: PS/2 mouse device common for all mice
[   12.919068] TCP cubic registered
[   12.919118] NET: Registered protocol family 1
[   12.919275] /build/buildd/linux-source-2.6.22-2.6.22/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   12.919280] Freeing unused kernel memory: 296k freed
[   12.983344] input: AT Translated Set 2 keyboard as /class/input/input1
[   14.069680] AppArmor: AppArmor initialized<5>audit(1203169296.248:2):  type=1505 info="AppArmor initialized" pid=1253
[   14.073977] fuse init (API version 7.8)
[   14.077451] Failure registering capabilities with primary security module.
[   14.091195] ACPI: Fan [FAN] (on)
[   14.094288] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
[   14.095486] ACPI: Thermal Zone [THRM] (40 C)
[   14.524785] usbcore: registered new interface driver usbfs
[   14.524806] usbcore: registered new interface driver hub
[   14.524823] usbcore: registered new device driver usb
[   14.525349] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   14.525735] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 23
[   14.525744] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [APCF] -> GSI 23 (level, low) -> IRQ 23
[   14.525915] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   14.525922] ohci_hcd 0000:00:02.0: OHCI Host Controller
[   14.526056] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
[   14.526072] ohci_hcd 0000:00:02.0: irq 23, io mem 0xfe02f000
[   14.597278] SCSI subsystem initialized
[   14.601487] libata version 2.21 loaded.
[   14.608643] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.60.
[   14.622488] usb usb1: configuration #1 chosen from 1 choice
[   14.622512] hub 1-0:1.0: USB hub found
[   14.622521] hub 1-0:1.0: 8 ports detected
[   14.729041] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 22
[   14.729052] ACPI: PCI Interrupt 0000:00:02.1[B] -> Link [APCL] -> GSI 22 (level, low) -> IRQ 22
[   14.729252] PCI: Setting latency timer of device 0000:00:02.1 to 64
[   14.729259] ehci_hcd 0000:00:02.1: EHCI Host Controller
[   14.729302] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 2
[   14.729332] ehci_hcd 0000:00:02.1: debug port 1
[   14.729335] PCI: cache line size of 64 is not supported by device 0000:00:02.1
[   14.729346] ehci_hcd 0000:00:02.1: irq 22, io mem 0xfe02e000
[   14.729353] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   14.729420] usb usb2: configuration #1 chosen from 1 choice
[   14.729444] hub 2-0:1.0: USB hub found
[   14.729449] hub 2-0:1.0: 8 ports detected
[   14.841048] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   14.841052] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   14.841509] NFORCE-MCP61: IDE controller at PCI slot 0000:00:06.0
[   14.841525] NFORCE-MCP61: chipset revision 162
[   14.841527] NFORCE-MCP61: not 100% native mode: will probe irqs later
[   14.841533] NFORCE-MCP61: 0000:00:06.0 (rev a2) UDMA133 controller
[   14.841540]     ide0: BM-DMA at 0xf000-0xf007, BIOS settings: hda:DMA, hdb:DMA
[   14.841548] Probing IDE interface ide0...
[   15.132110] hda: Hitachi HDS721616PLAT80, ATA DISK drive
[   15.807896] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   15.816655] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 23
[   15.816658] ACPI: PCI Interrupt 0000:00:07.0[A] -> Link [APCH] -> GSI 23 (level, low) -> IRQ 23
[   15.816663] PCI: Setting latency timer of device 0000:00:07.0 to 64
[   15.816671] forcedeth: using HIGHDMA
[   15.821854] hda: max request size: 512KiB
[   15.822317] hda: 312581808 sectors (160041 MB) w/7376KiB Cache, CHS=19457/255/63, UDMA(133)
[   15.822449] hda: cache flushes supported
[   15.822479]  hda: hda1 hda2 < hda5 >
[   16.003021] Attempting manual resume
[   16.003024] swsusp: Resume From Partition 3:5
[   16.003026] PM: Checking swsusp image.
[   16.003112] PM: Resume from disk failed.
[   16.039462] kjournald starting.  Commit interval 5 seconds
[   16.039471] EXT3-fs: mounted filesystem with ordered data mode.
[   16.339508] eth0: forcedeth.c: subsystem: 01043:825a bound to 0000:00:07.0
[   16.339972] ACPI: PCI Interrupt Link [APC1] enabled at IRQ 16
[   16.339981] ACPI: PCI Interrupt 0000:01:07.0[A] -> Link [APC1] -> GSI 16 (level, low) -> IRQ 16
[   16.393163] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[16]  MMIO=[fdfff000-fdfff7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   16.398280] sata_nv 0000:00:08.0: version 3.4
[   16.398597] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 20
[   16.398603] ACPI: PCI Interrupt 0000:00:08.0[A] -> Link [APSI] -> GSI 20 (level, low) -> IRQ 20
[   16.398820] PCI: Setting latency timer of device 0000:00:08.0 to 64
[   16.398944] scsi0 : sata_nv
[   16.398979] scsi1 : sata_nv
[   16.399042] ata1: SATA max UDMA/133 cmd 0x00000000000109f0 ctl 0x0000000000010bf2 bmdma 0x000000000001d800 irq 20
[   16.399046] ata2: SATA max UDMA/133 cmd 0x0000000000010970 ctl 0x0000000000010b72 bmdma 0x000000000001d808 irq 20
[   16.870853] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   17.042822] ata1.00: ATAPI: TSSTcorp CDDVDW SH-S203B, SB01, max UDMA/100
[   17.222697] ata1.00: configured for UDMA/100
[   17.538394] ata2: SATA link down (SStatus 0 SControl 300)
[   17.549409] scsi 0:0:0:0: CD-ROM            TSSTcorp CDDVDW SH-S203B  SB01 PQ: 0 ANSI: 5
[   17.682357] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0011d800011e59a3]
[   22.483471] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x1c00
[   22.483494] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x1c40
[   22.799354] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   22.800783] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   23.199959] input: PC Speaker as /class/input/input2
[   23.235170] sr0: scsi3-mmc drive: 40x/40x writer dvd-ram cd/rw xa/form2 cdda tray
[   23.235176] Uniform CD-ROM driver Revision: 3.20
[   23.235435] sr 0:0:0:0: Attached scsi CD-ROM sr0
[   23.265777] sr 0:0:0:0: Attached scsi generic sg0 type 5
[   23.317449] logips2pp: Detected unknown logitech mouse model 127
[   23.445549] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 22
[   23.445555] ACPI: PCI Interrupt 0000:00:05.0[B] -> Link [AAZA] -> GSI 22 (level, low) -> IRQ 22
[   23.445734] PCI: Setting latency timer of device 0000:00:05.0 to 64
[   23.654304] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[   23.781136] input: ImExPS/2 Logitech Explorer Mouse as /class/input/input3
[   23.783810] parport_pc 00:09: reported by Plug and Play ACPI
[   23.783836] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
[   24.576555] lp0: using parport0 (interrupt-driven).
[   24.649718] Adding 5944008k swap on /dev/hda5.  Priority:-1 extents:1 across:5944008k
[   24.948569] EXT3 FS on hda1, internal journal
[   25.751383] No dock devices found.
[   25.889362] input: Power Button (FF) as /class/input/input4
[   25.892588] ACPI: Power Button (FF) [PWRF]
[   25.916680] input: Power Button (CM) as /class/input/input5
[   25.919906] ACPI: Power Button (CM) [PWRB]
[   26.077621] powernow-k8: Found 1 AMD Athlon(tm) Processor LE-1600 processors (version 2.00.00)
[   26.077656] powernow-k8:    0 : fid 0xe (2200 MHz), vid 0xc
[   26.077658] powernow-k8:    1 : fid 0xc (2000 MHz), vid 0xe
[   26.077661] powernow-k8:    2 : fid 0xa (1800 MHz), vid 0x10
[   26.077663] powernow-k8:    3 : fid 0x2 (1000 MHz), vid 0x12
[   27.158656] ppdev: user-space parallel port driver
[   27.317660] audit(1203169309.829:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4701 profile="/usr/sbin/cupsd"
[   27.493626] Failure registering capabilities with primary security module.
[   27.640666] Bluetooth: Core ver 2.11
[   27.640754] NET: Registered protocol family 31
[   27.640757] Bluetooth: HCI device and connection manager initialized
[   27.640760] Bluetooth: HCI socket layer initialized
[   27.648452] Bluetooth: L2CAP ver 2.8
[   27.648457] Bluetooth: L2CAP socket layer initialized
[   27.724036] Bluetooth: RFCOMM socket layer initialized
[   27.724103] Bluetooth: RFCOMM TTY layer initialized
[   27.724106] Bluetooth: RFCOMM ver 1.8
[   28.866879] Marking TSC unstable due to cpufreq changes
[   28.868665] Time: hpet clocksource has been installed.
[   30.692339] NET: Registered protocol family 17
[   33.277235] NET: Registered protocol family 10
[   33.277367] lo: Disabled Privacy Extensions
[   37.934587] eth0: no IPv6 routers present

And here is lspci:

00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a2)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0d.0 VGA compatible controller: nVidia Corporation GeForce 6100 nForce 405 (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:07.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev c0)
01:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)

I am not wise in the ways of wireless networking.  I have played with ndiswrapper without success, but I really don't know what I'm doing, and have probably messed things up.  Can somebody help me get this wifi card set up and running?

Many thanks,

Phil

---

### Post by shibu on 2008-02-16
hi ...

Try   [http://ndiswrapper.sourceforge.net/](http://ndiswrapper.sourceforge.net/)  

ndiswrapper and the original XP driver from the CD included with the card.

install the Windows XP driver through ndiswrapper, and finally add the ndiswrapper module to /etc/rc.local with: modprobe ndiswrapper, remove the native module.

Also have a look at [http://www.encore-usa.com/product_download.php?region=us&bid=3&pgid=83_11&pid=285](http://www.encore-usa.com/product_download.php?region=us&bid=3&pgid=83_11&pid=285)

hope this help you out to get connected...

---

### Post by pbewig on 2008-02-16
I have played with ndiswrapper previously without success.  Here's what I did this morning:

phil@bach:~$ sudo su
root@bach:/home/phil# ndiswrapper -i Desktop/net8185.inf
driver net8185 is already installed
root@bach:/home/phil# ndiswrapper -l
net8185 : driver installed
        device (10EC:8185) present (alternate driver: r8180)
root@bach:/home/phil# depmod -a
root@bach:/home/phil# modprobe ndiswrapper
root@bach:/home/phil# tail -n3 /var/log/messages
Feb 16 11:03:28 bach kernel: [  382.146781] ndiswrapper version 1.45 loaded (smp=yes)
Feb 16 11:03:28 bach loadndisdriver: loadndisdriver: load_driver(358): couldn't load driver net8185 
Feb 16 11:03:28 bach kernel: [  382.179200] usbcore: registered new interface driver ndiswrapper
root@bach:/home/phil# 

The error message shows that the driver is not loaded.  What should I do next?

---

### Post by shibu on 2008-02-16
hi ...

Have you check the docs at 
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper) 

I think you have to do some troubleshooting... check 

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#trouble](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#trouble)

---

### Post by pbewig on 2008-02-16
I was aware of the ndiswrapper doc but not the troubleshooting doc.  Thanks for the pointer.

I am concerned about a driver conflict.  In /etc/modprobe.d, based on something I read somewhere, I added the line "blacklist r8180" to disable that driver.  But I'm concerned I have done that incorrectly.  The output of "modprobe -l | egrep 'wifi|wireless|ieee'" is

/lib/modules/2.6.22-14-generic/madwifi/wlan_scan_sta.ko
/lib/modules/2.6.22-14-generic/madwifi/ath_pci.ko
/lib/modules/2.6.22-14-generic/madwifi/wlan_scan_ap.ko
/lib/modules/2.6.22-14-generic/madwifi/ath_rate_sample.ko
/lib/modules/2.6.22-14-generic/madwifi/wlan_acl.ko
/lib/modules/2.6.22-14-generic/madwifi/wlan_xauth.ko
/lib/modules/2.6.22-14-generic/madwifi/ath_rate_amrr.ko
/lib/modules/2.6.22-14-generic/madwifi/wlan_wep.ko
/lib/modules/2.6.22-14-generic/madwifi/wlan_tkip.ko
/lib/modules/2.6.22-14-generic/madwifi/wlan.ko
/lib/modules/2.6.22-14-generic/madwifi/wlan_ccmp.ko
/lib/modules/2.6.22-14-generic/madwifi/ath_rate_onoe.ko
/lib/modules/2.6.22-14-generic/kernel/net/wireless/cfg80211.ko
/lib/modules/2.6.22-14-generic/kernel/net/ieee80211/ieee80211_crypt_ccmp.ko
/lib/modules/2.6.22-14-generic/kernel/net/ieee80211/ieee80211_crypt.ko
/lib/modules/2.6.22-14-generic/kernel/net/ieee80211/softmac/ieee80211softmac.ko
/lib/modules/2.6.22-14-generic/kernel/net/ieee80211/ieee80211_crypt_tkip.ko
/lib/modules/2.6.22-14-generic/kernel/net/ieee80211/ieee80211_crypt_wep.ko
/lib/modules/2.6.22-14-generic/kernel/net/ieee80211/ieee80211.ko
/lib/modules/2.6.22-14-generic/kernel/drivers/net/wireless/zd1201.ko
/lib/modules/2.6.22-14-generic/kernel/drivers/net/wireless/ipw2100.ko
/lib/modules/2.6.22-14-generic/kernel/drivers/net/wireless/libertas/libertas.ko
/lib/modules/2.6.22-14-generic/kernel/drivers/net/wireless/libertas/usb8xxx.ko
/lib/modules/2.6.22-14-generic/kernel/drivers/net/wireless/netwave_cs.ko
/lib/modules/2.6.22-14-generic/kernel/drivers/net/wireless/spectrum_cs.ko
/lib/modules/2.6.22-14-generic/kernel/drivers/net/wireless/atmel_pci.ko
/lib/modules/2.6.22-14-generic/kernel/drivers/net/wireless/prism54/prism54.ko
/lib/modules/2.6.22-14-generic/kernel/drivers/net/wireless/ipw2200.ko
/lib/modules/2.6.22-14-generic/kernel/drivers/net/wireless/strip.ko
/lib/modules/2.6.22-14-generic/kernel/drivers/net/wireless/airo_cs.ko
/lib/modules/2.6.22-14-generic/kernel/drivers/net/wireless/bcm43xx/bcm43xx.ko
/lib/modules/2.6.22-14-generic/kernel/drivers/net/wireless/hostap/hostap_pci.ko
/lib/modules/2.6.22-14-generic/kernel/drivers/net/wireless/hostap/hostap_plx.ko
/lib/modules/2.6.22-14-generic/kernel/drivers/net/wireless/hostap/hostap.ko
/lib/modules/2.6.22-14-generic/kernel/drivers/net/wireless/hostap/hostap_cs.ko
/lib/modules/2.6.22-14-generic/kernel/drivers/net/wireless/wl3501_cs.ko
/lib/modules/2.6.22-14-generic/kernel/drivers/net/wireless/orinoco.ko
/lib/modules/2.6.22-14-generic/kernel/drivers/net/wireless/orinoco_cs.ko
/lib/modules/2.6.22-14-generic/kernel/drivers/net/wireless/ray_cs.ko
/lib/modules/2.6.22-14-generic/kernel/drivers/net/wireless/atmel_cs.ko
/lib/modules/2.6.22-14-generic/kernel/drivers/net/wireless/zd1211rw/zd1211rw.ko
/lib/modules/2.6.22-14-generic/kernel/drivers/net/wireless/airo.ko
/lib/modules/2.6.22-14-generic/kernel/drivers/net/wireless/atmel.ko
/lib/modules/2.6.22-14-generic/kernel/drivers/net/wireless/hermes.ko
/lib/modules/2.6.22-14-generic/kernel/drivers/net/wireless/wavelan_cs.ko
/lib/modules/2.6.22-14-generic/kernel/drivers/ieee1394/dv1394.ko
/lib/modules/2.6.22-14-generic/kernel/drivers/ieee1394/raw1394.ko
/lib/modules/2.6.22-14-generic/kernel/drivers/ieee1394/ieee1394.ko
/lib/modules/2.6.22-14-generic/kernel/drivers/ieee1394/pcilynx.ko
/lib/modules/2.6.22-14-generic/kernel/drivers/ieee1394/eth1394.ko
/lib/modules/2.6.22-14-generic/kernel/drivers/ieee1394/ohci1394.ko
/lib/modules/2.6.22-14-generic/kernel/drivers/ieee1394/video1394.ko
/lib/modules/2.6.22-14-generic/kernel/drivers/ieee1394/sbp2.ko
/lib/modules/2.6.22-14-generic/ubuntu/wireless/p80211/p80211.ko
/lib/modules/2.6.22-14-generic/ubuntu/wireless/acx/acx.ko
/lib/modules/2.6.22-14-generic/ubuntu/wireless/rtl818x/rtl8187.ko
/lib/modules/2.6.22-14-generic/ubuntu/wireless/iwlwifi/mac80211/origin/net/mac80211/iwlwifi_rc80211_simple.ko
/lib/modules/2.6.22-14-generic/ubuntu/wireless/iwlwifi/mac80211/origin/net/mac80211/iwlwifi_mac80211.ko
/lib/modules/2.6.22-14-generic/ubuntu/wireless/iwlwifi/iwlwifi/origin/iwl4965.ko
/lib/modules/2.6.22-14-generic/ubuntu/wireless/iwlwifi/iwlwifi/origin/iwl3945.ko
/lib/modules/2.6.22-14-generic/ubuntu/wireless/at76/at76_usb.ko
/lib/modules/2.6.22-14-generic/ubuntu/wireless/fsam7400.ko
/lib/modules/2.6.22-14-generic/ubuntu/wireless/ipw3945/ipw3945.ko
/lib/modules/2.6.22-14-generic/ubuntu/wireless/rt2x00/rt73usb.ko
/lib/modules/2.6.22-14-generic/ubuntu/wireless/rt2x00/rt2500usb.ko
/lib/modules/2.6.22-14-generic/ubuntu/wireless/rt2x00/rt2x00lib.ko
/lib/modules/2.6.22-14-generic/ubuntu/wireless/rt2x00/rt2x00pci.ko
/lib/modules/2.6.22-14-generic/ubuntu/wireless/rt2x00/eeprom_93cx6.ko
/lib/modules/2.6.22-14-generic/ubuntu/wireless/rt2x00/rt2400pci.ko
/lib/modules/2.6.22-14-generic/ubuntu/wireless/rt2x00/rt2x00usb.ko
/lib/modules/2.6.22-14-generic/ubuntu/wireless/rt2x00/rt61pci.ko
/lib/modules/2.6.22-14-generic/ubuntu/wireless/rt2x00/rt2500pci.ko
/lib/modules/2.6.22-14-generic/ubuntu/wireless/p54/p54usb.ko
/lib/modules/2.6.22-14-generic/ubuntu/wireless/p54/p54pci.ko
/lib/modules/2.6.22-14-generic/ubuntu/wireless/p54/p54common.ko
/lib/modules/2.6.22-14-generic/ubuntu/wireless/prism2_usb/prism2_usb.ko
/lib/modules/2.6.22-14-generic/ubuntu/wireless/rtl8180/rtl_ieee80211/ieee80211-rtl.ko
/lib/modules/2.6.22-14-generic/ubuntu/wireless/rtl8180/rtl8180/r8180.ko

I am particularly concerned about the last two lines that mention "rtl8180".  Have I properly blacklisted unneeded drivers?

Many thanks,

Phil

---

### Post by pbewig on 2008-02-16
I blacklisted rtl8180 in addition to r8180, then rebooted.  I see the same thing.  Ndiswrapper -l reports that driver net8185 is installed, I run depmode -a and modprobe ndiswrapper, and tail /var/log/messages reports "couldn't load driver net8185".  Help!

Many thanks,

Phil

---

### Post by shibu on 2008-02-16
hi ..

Can you check if you have these packages already installed from the repos and is the latest.

ndiswrapper-utils, ndiswrapper-common

---

### Post by pbewig on 2008-02-16
I have the latest version of both packages installed.

---

