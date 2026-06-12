---
title: "USB External drive not being detected."
date: 2009-04-11
forum: New to Ubuntu
---

### Post by umanzor on 2009-04-11
Hi everyone. I'm having an issue here that didn't happen to me before. For some reason, whenever I reboot, Ubuntu won't recognize my external drive. I have to manually unplug it, and then plug it back in to get access to it. I'm not sure what's causing this. If I do a lsusb I can see it in there (not sure if the bus information and all that is correct though).

I have here the output of a dmesg. In the first 30 secs of boot time I don't see anything useful (I don't know what should I be looking for he he). But you can clearly see the moment where I unplug the USB drive and replugged it. How come it is not detecting it automatically?

Any ideas?

```
[    0.000000] BIOS EBDA/lowmem at: 00000000/000a0000
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.28-11-generic (buildd@palmer) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #37-Ubuntu SMP Mon Mar 23 16:40:23 UTC 2009 (Ubuntu 2.6.28-11.37-generic)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 00000000000a0000 (usable)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000004fff0000 (usable)
[    0.000000]  BIOS-e820: 000000004fff0000 - 000000004fff3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000004fff3000 - 0000000050000000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.2 present.
[    0.000000] Phoenix BIOS detected: BIOS may corrupt low RAM, working it around.
[    0.000000] last_pfn = 0x4fff0 max_arch_pfn = 0x100000
[    0.000000] Scanning Bus 001 Device 003: ID 1058:1100 Western Digital Technologies, Inc.0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 00000000000a0000 (usable)
[    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000004fff0000 (usable)
[    0.000000]  modified: 000000004fff0000 - 000000004fff3000 (ACPI NVS)
[    0.000000]  modified: 000000004fff3000 - 0000000050000000 (ACPI data)
[    0.000000]  modified: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000] kernel direct mapping tables up to 373fe000 @ 10000-16000
[    0.000000] RAMDISK: 378bc000 - 37fefd2a
[    0.000000] Allocated new RAMDISK: 00881000 - 00fb4d2a
[    0.000000] Move RAMDISK from 00000000378bc000 - 0000000037fefd29 to 00881000 - 00fb4d29
[    0.000000] ACPI: RSDP 000F6240, 0014 (r0 IntelR)
[    0.000000] ACPI: RSDT 4FFF3000, 002C (r1 IntelR AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: FACP 4FFF3040, 0074 (r1 IntelR AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: DSDT 4FFF30C0, 3C08 (r1 INTELR AWRDACPI     1000 MSFT  100000D)
[    0.000000] ACPI: FACS 4FFF0000, 0040
[    0.000000] ACPI: APIC 4FFF6D00, 0054 (r1 IntelR AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 395MB HIGHMEM available.
[    0.000000] 883MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 373fe000
[    0.000000]   low ram: 00000000 - 373fe000
[    0.000000]   bootmap 00012000 - 00018e80
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00373fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 000087c52c]    TEXT DATA BSS ==> [0000100000 - 000087c52c]
[    0.000000]   #4 [000087d000 - 0000881000]    INIT_PG_TABLE ==> [000087d000 - 0000881000]
[    0.000000]   #5 [000009f000 - 0000100000]    BIOS reserved ==> [000009f000 - 0000100000]
[    0.000000]   #6 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]
[    0.000000]   #7 [0000881000 - 0000fb4d2a]      NEW RAMDISK ==> [0000881000 - 0000fb4d2a]
[    0.000000]   #8 [0000012000 - 0000019000]          BOOTMAP ==> [0000012000 - 0000019000]
[    0.000000] found SMP MP-table at [c00f4830] 000f4830
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000373fe
[    0.000000]   HighMem  0x000373fe -> 0x0004fff0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x000000a0
[    0.000000]     0: 0x00000100 -> 0x0004fff0
[    0.000000] On node 0 totalpages: 327552
[    0.000000] free_area_init_node: node 0, pgdat c06d0f00, node_mem_map c1000200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3952 pages, LIFO batch:0
[    0.000000]   Normal zone: 1736 pages used for memmap
[    0.000000]   Normal zone: 220470 pages, LIFO batch:31
[    0.000000]   HighMem zone: 792 pages used for memmap
[    0.000000]   HighMem zone: 100570 pages, LIFO batch:31
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 60000000 (gap: 50000000:aec00000)
[    0.000000] PERCPU: Allocating 45056 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 1, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 324992
[    0.000000] Kernel command line: root=UUID=d0ce6f7d-b22d-4e07-87c8-473497d1bcfc ro vga=99999
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] TSC: PIT calibration matches PMTIMER. 1 loops
[    0.000000] Detected 2556.452 MHz processor.
[    0.004000] Console: colour dummy device 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] allocated 6552960 bytes of page_cgroup
[    0.004000] please try cgroup_disable=memory option if you don't want
[    0.004000] Scanning for low memory corruption every 60 seconds
[    0.004000] Memory: 1276748k/1310656k available (4126k kernel code, 32592k reserved, 2208k data, 532k init, 405448k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xf7bfe000 - 0xff3fe000   ( 120 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xf73fe000   ( 883 MB)
[    0.004000]       .init : 0xc0737000 - 0xc07bc000   ( 532 kB)
[    0.004000]       .data : 0xc0507a7f - 0xc072fe60   (2208 kB)
[    0.004000]       .text : 0xc0100000 - 0xc0507a7f   (4126 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] SLUB: Genslabs=12, HWalign=128, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.004018] Calibrating delay loop (skipped), value calculated using timer frequency.. 5112.90 BogoMIPS (lpj=10225808)
[    0.004047] Security Framework initialized
[    0.004063] SELinux:  Disabled at boot.
[    0.004091] AppArmor: AppArmor initialized
[    0.004108] Mount-cache hash table entries: 512
[    0.004304] Initializing cgroup subsys ns
[    0.004313] Initializing cgroup subsys cpuacct
[    0.004319] Initializing cgroup subsys memory
[    0.004327] Initializing cgroup subsys freezer
[    0.004351] CPU: Trace cache: 12K uops, L1 D cache: 8K
[    0.004358] CPU: L2 cache: 512K
[    0.004364] CPU: Hyper-Threading is disabled
[    0.004386] Checking 'hlt' instruction... OK.
[    0.020791] SMP alternatives: switching to UP code
[    0.132835] Freeing SMP alternatives: 18k freed
[    0.132850] ACPI: Core revision 20080926
[    0.134877] ACPI: Checking initramfs for custom DSDT
[    0.460554] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.501156] CPU0: Intel(R) Pentium(R) 4 CPU 2.40GHz stepping 07
[    0.504002] Brought up 1 CPUs
[    0.504002] Total of 1 processors activated (5112.90 BogoMIPS).
[    0.504002] CPU0 attaching NULL sched-domain.
[    0.504002] net_namespace: 776 bytes
[    0.504002] Booting paravirtualized kernel on bare hardware
[    0.504002] Time: 18:47:29  Date: 04/10/09
[    0.504002] regulator: core version 0.5
[    0.504002] NET: Registered protocol family 16
[    0.504002] EISA bus registered
[    0.504002] ACPI: bus type pci registered
[    0.524667] PCI: PCI BIOS revision 2.10 entry at 0xfb0b0, last bus=2
[    0.524673] PCI: Using configuration type 1 for base access
[    0.526302] ACPI: EC: Look up EC in DSDT
[    0.532826] ACPI: Interpreter enabled
[    0.532837] ACPI: (supports S0 S3 S4 S5)
[    0.532864] ACPI: Using IOAPIC for interrupt routing
[    0.538478] ACPI: No dock devices found.
[    0.538499] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.538554] pci 0000:00:00.0: reg 10 32bit mmio: [0xc0000000-0xcfffffff]
[    0.538705] pci 0000:00:1f.0: quirk: region 0400-047f claimed by ICH4 ACPI/GPIO/TCO
[    0.538713] pci 0000:00:1f.0: quirk: region 0480-04bf claimed by ICH4 GPIO
[    0.538753] pci 0000:00:1f.1: reg 20 io port: [0xf000-0xf00f]
[    0.538805] pci 0000:00:1f.2: reg 20 io port: [0xd000-0xd01f]
[    0.538855] pci 0000:00:1f.3: reg 20 io port: [0x500-0x50f]
[    0.538905] pci 0000:00:1f.4: reg 20 io port: [0xd800-0xd81f]
[    0.538936] pci 0000:00:1f.5: reg 10 io port: [0xdc00-0xdcff]
[    0.538943] pci 0000:00:1f.5: reg 14 io port: [0xe000-0xe03f]
[    0.538988] pci 0000:00:1f.6: reg 10 io port: [0xe400-0xe4ff]
[    0.538996] pci 0000:00:1f.6: reg 14 io port: [0xe800-0xe87f]
[    0.539057] pci 0000:01:00.0: reg 10 32bit mmio: [0xe0000000-0xe0ffffff]
[    0.539063] pci 0000:01:00.0: reg 14 32bit mmio: [0xd0000000-0xdfffffff]
[    0.539069] pci 0000:01:00.0: reg 18 32bit mmio: [0xe1000000-0xe1ffffff]
[    0.539084] pci 0000:01:00.0: reg 30 32bit mmio: [0x000000-0x01ffff]
[    0.539128] pci 0000:00:01.0: bridge 32bit mmio: [0xe0000000-0xe2ffffff]
[    0.539132] pci 0000:00:01.0: bridge 32bit mmio pref: [0xd0000000-0xdfffffff]
[    0.539165] pci 0000:02:01.0: reg 10 32bit mmio: [0xe3007000-0xe3007fff]
[    0.539200] pci 0000:02:01.0: supports D1 D2
[    0.539202] pci 0000:02:01.0: PME# supported from D0 D1 D2 D3hot
[    0.539209] pci 0000:02:01.0: PME# disabled
[    0.539242] pci 0000:02:01.1: reg 10 32bit mmio: [0xe3004000-0xe3004fff]
[    0.539276] pci 0000:02:01.1: supports D1 D2
[    0.539278] pci 0000:02:01.1: PME# supported from D0 D1 D2 D3hot
[    0.539284] pci 0000:02:01.1: PME# disabled
[    0.539317] pci 0000:02:01.2: reg 10 32bit mmio: [0xe3005000-0xe30050ff]
[    0.539351] pci 0000:02:01.2: supports D1 D2
[    0.539353] pci 0000:02:01.2: PME# supported from D0 D1 D2 D3hot
[    0.539359] pci 0000:02:01.2: PME# disabled
[    0.539393] pci 0000:02:01.3: reg 10 32bit mmio: [0xe3006000-0xe30067ff]
[    0.539400] pci 0000:02:01.3: reg 14 32bit mmio: [0xe3000000-0xe3003fff]
[    0.539433] pci 0000:02:01.3: supports D1 D2
[    0.539435] pci 0000:02:01.3: PME# supported from D0 D1 D2 D3hot
[    0.539442] pci 0000:02:01.3: PME# disabled
[    0.539481] pci 0000:02:02.0: reg 10 io port: [0xc000-0xc0ff]
[    0.539488] pci 0000:02:02.0: reg 14 32bit mmio: [0xe3008000-0xe30080ff]
[    0.539519] pci 0000:02:02.0: supports D1 D2
[    0.539522] pci 0000:02:02.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.539528] pci 0000:02:02.0: PME# disabled
[    0.539569] pci 0000:00:1e.0: transparent bridge
[    0.539576] pci 0000:00:1e.0: bridge io port: [0xc000-0xcfff]
[    0.539581] pci 0000:00:1e.0: bridge 32bit mmio: [0xe3000000-0xe30fffff]
[    0.539596] bus 00 -> node 0
[    0.539604] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.539843] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[    0.562083] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 10 11 *12 14 15)
[    0.562230] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 7 9 10 11 12 14 15)
[    0.562374] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[    0.562518] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[    0.562661] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[    0.562811] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[    0.562956] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[    0.563101] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 7 *9 10 11 12 14 15)
[    0.563254] ACPI: WMI: Mapper loaded
[    0.563507] SCSI subsystem initialized
[    0.563557] libata version 3.00 loaded.
[    0.563618] usbcore: registered new interface driver usbfs
[    0.563644] usbcore: registered new interface driver hub
[    0.563680] usbcore: registered new device driver usb
[    0.563822] PCI: Using ACPI for IRQ routing
[    0.563930] Bluetooth: Core ver 2.13
[    0.564022] NET: Registered protocol family 31
[    0.564028] Bluetooth: HCI device and connection manager initialized
[    0.564034] Bluetooth: HCI socket layer initialized
[    0.564038] NET: Registered protocol family 8
[    0.564042] NET: Registered protocol family 20
[    0.564061] NetLabel: Initializing
[    0.564065] NetLabel:  domain hash size = 128
[    0.564069] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.564086] NetLabel:  unlabeled traffic allowed by default
[    0.564185] AppArmor: AppArmor Filesystem Enabled
[    0.564198] pnp: PnP ACPI init
[    0.564198] ACPI: bus type pnp registered
[    0.568749] pnp: PnP ACPI: found 15 devices
[    0.568755] ACPI: ACPI bus type pnp unregistered
[    0.568762] PnPBIOS: Disabled by ACPI PNP
[    0.568777] system 00:00: iomem range 0xd0000-0xd3fff could not be reserved
[    0.568783] system 00:00: iomem range 0xf0000-0xf7fff could not be reserved
[    0.568789] system 00:00: iomem range 0xf8000-0xfbfff could not be reserved
[    0.568794] system 00:00: iomem range 0xfc000-0xfffff could not be reserved
[    0.568800] system 00:00: iomem range 0x4fff0000-0x4fffffff could not be reserved
[    0.568807] system 00:00: iomem range 0x0-0x9ffff could not be reserved
[    0.568812] system 00:00: iomem range 0x100000-0x4ffeffff could not be reserved
[    0.568819] system 00:00: iomem range 0xfec00000-0xfec00fff has been reserved
[    0.568825] system 00:00: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.568831] system 00:00: iomem range 0xffb00000-0xffbfffff has been reserved
[    0.568837] system 00:00: iomem range 0xfff00000-0xffffffff has been reserved
[    0.568843] system 00:00: iomem range 0xe0000-0xeffff has been reserved
[    0.568852] system 00:02: ioport range 0x400-0x4bf could not be reserved
[    0.568862] system 00:03: ioport range 0x4d0-0x4d1 has been reserved
[    0.568867] system 00:03: ioport range 0x290-0x29f has been reserved
[    0.568873] system 00:03: ioport range 0x800-0x805 has been reserved
[    0.603625] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.603631] pci 0000:00:01.0:   IO window: disabled
[    0.603638] pci 0000:00:01.0:   MEM window: 0xe0000000-0xe2ffffff
[    0.603644] pci 0000:00:01.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
[    0.603654] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:02
[    0.603659] pci 0000:00:1e.0:   IO window: 0xc000-0xcfff
[    0.603667] pci 0000:00:1e.0:   MEM window: 0xe3000000-0xe30fffff
[    0.603674] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.603693] pci 0000:00:1e.0: setting latency timer to 64
[    0.603698] bus: 00 index 0 io port: [0x00-0xffff]
[    0.603702] bus: 00 index 1 mmio: [0x000000-0xffffffff]
[    0.603707] bus: 01 index 0 mmio: [0x0-0x0]
[    0.603711] bus: 01 index 1 mmio: [0xe0000000-0xe2ffffff]
[    0.603715] bus: 01 index 2 mmio: [0xd0000000-0xdfffffff]
[    0.603719] bus: 01 index 3 mmio: [0x0-0x0]
[    0.603723] bus: 02 index 0 io port: [0xc000-0xcfff]
[    0.603728] bus: 02 index 1 mmio: [0xe3000000-0xe30fffff]
[    0.603732] bus: 02 index 2 mmio: [0x0-0x0]
[    0.603735] bus: 02 index 3 io port: [0x00-0xffff]
[    0.603740] bus: 02 index 4 mmio: [0x000000-0xffffffff]
[    0.603752] NET: Registered protocol family 2
[    0.603902] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.604302] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.605367] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.606051] TCP: Hash tables configured (established 131072 bind 65536)
[    0.606065] TCP reno registered
[    0.606247] NET: Registered protocol family 1
[    0.606406] checking if image is initramfs... it is
[    1.104044] Switched to high resolution mode on CPU 0
[    1.278860] Freeing initrd memory: 7375k freed
[    1.278959] cpufreq: No nForce2 chipset.
[    1.279152] audit: initializing netlink socket (disabled)
[    1.279181] type=2000 audit(1239389249.276:1): initialized
[    1.287088] highmem bounce pool size: 64 pages
[    1.287102] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.288447] VFS: Disk quotas dquot_6.5.1
[    1.288518] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.289239] fuse init (API version 7.10)
[    1.289340] msgmni has been set to 1717
[    1.289556] alg: No test for stdrng (krng)
[    1.289575] io scheduler noop registered
[    1.289580] io scheduler anticipatory registered
[    1.289584] io scheduler deadline registered
[    1.289608] io scheduler cfq registered (default)
[    1.289670] pci 0000:01:00.0: Boot video device
[    1.293676] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.293693] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.293846] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.293853] ACPI: Power Button (FF) [PWRF]
[    1.293905] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    1.293912] ACPI: Power Button (CM) [PWRB]
[    1.293965] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    1.293976] ACPI: Sleep Button (CM) [SLPB]
[    1.294031] fan PNP0C0B:00: registered as cooling_device0
[    1.294040] ACPI: Fan [FAN] (on)
[    1.294308] processor ACPI_CPU:00: registered as cooling_device1
[    1.294315] ACPI: Processor [CPU0] (supports 2 throttling states)
[    1.297180] thermal LNXTHERM:01: registered as thermal_zone0
[    1.297490] ACPI: Thermal Zone [THRM] (39 C)
[    1.297538] isapnp: Scanning for PnP cards...
[    1.651143] isapnp: No Plug & Play device found
[    1.652807] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.652900] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.652990] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    1.653360] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.653492] 00:0a: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    1.653626] serial 0000:00:1f.6: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.653636] serial 0000:00:1f.6: PCI INT B disabled
[    1.654427] brd: module loaded
[    1.654807] loop: module loaded
[    1.654922] Fixed MDIO Bus: probed
[    1.654932] PPP generic driver version 2.4.2
[    1.655012] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    1.655053] Driver 'sd' needs updating - please use bus_type methods
[    1.655068] Driver 'sr' needs updating - please use bus_type methods
[    1.655149] ata_piix 0000:00:1f.1: version 2.12
[    1.655212] ata_piix 0000:00:1f.1: setting latency timer to 64
[    1.655345] scsi0 : ata_piix
[    1.655467] scsi1 : ata_piix
[    1.656462] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[    1.656469] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[    1.829857] ata1.00: ATA-7: Maxtor 6L200P0, BAJ41G20, max UDMA/133
[    1.829864] ata1.00: 398297088 sectors, multi 16: LBA48 
[    1.836261] ata1.01: HPA unlocked: 66055248 -> 78242976, native 78242976
[    1.836267] ata1.01: ATA-7: SAMSUNG SP0411N, TW100-11, max UDMA/100
[    1.836272] ata1.01: 78242976 sectors, multi 16: LBA48 
[    1.853829] ata1.00: configured for UDMA/100
[    1.860335] ata1.01: configured for UDMA/100
[    2.040275] ata2.00: ATAPI: LITE-ON DVDRW LH-20A1P, KL0A, max UDMA/66
[    2.072234] ata2.00: configured for UDMA/66
[    2.073019] scsi 0:0:0:0: Direct-Access     ATA      Maxtor 6L200P0   BAJ4 PQ: 0 ANSI: 5
[    2.073145] sd 0:0:0:0: [sda] 398297088 512-byte hardware sectors: (203 GB/189 GiB)
[    2.073170] sd 0:0:0:0: [sda] Write Protect is off
[    2.073175] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.073206] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.073290] sd 0:0:0:0: [sda] 398297088 512-byte hardware sectors: (203 GB/189 GiB)
[    2.073312] sd 0:0:0:0: [sda] Write Protect is off
[    2.073317] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.073347] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.073355]  sda: sda1 sda2 sda3 sda4 < sda5 >
[    2.139989] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.140065] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.140162] scsi 0:0:1:0: Direct-Access     ATA      SAMSUNG SP0411N  TW10 PQ: 0 ANSI: 5
[    2.140271] sd 0:0:1:0: [sdb] 78242976 512-byte hardware sectors: (40.0 GB/37.3 GiB)
[    2.140294] sd 0:0:1:0: [sdb] Write Protect is off
[    2.140300] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[    2.140330] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.140404] sd 0:0:1:0: [sdb] 78242976 512-byte hardware sectors: (40.0 GB/37.3 GiB)
[    2.140425] sd 0:0:1:0: [sdb] Write Protect is off
[    2.140431] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[    2.140461] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.140469]  sdb: sdb1
[    2.149383] sd 0:0:1:0: [sdb] Attached SCSI disk
[    2.149440] sd 0:0:1:0: Attached scsi generic sg1 type 0
[    2.150472] scsi 1:0:0:0: CD-ROM            LITE-ON  DVDRW LH-20A1P   KL0A PQ: 0 ANSI: 5
[    2.155489] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.155497] Uniform CD-ROM driver Revision: 3.20
[    2.155622] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.155676] sr 1:0:0:0: Attached scsi generic sg2 type 5
[    2.156379] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.156415] ehci_hcd 0000:02:01.2: PCI INT C -> GSI 19 (level, low) -> IRQ 19
[    2.156444] ehci_hcd 0000:02:01.2: EHCI Host Controller
[    2.156521] ehci_hcd 0000:02:01.2: new USB bus registered, assigned bus number 1
[    2.180037] ehci_hcd 0000:02:01.2: irq 19, io mem 0xe3005000
[    2.192010] ehci_hcd 0000:02:01.2: USB 2.0 started, EHCI 1.00
[    2.192093] usb usb1: configuration #1 chosen from 1 choice
[    2.192130] hub 1-0:1.0: USB hub found
[    2.192150] hub 1-0:1.0: 5 ports detected
[    2.192285] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.192311] ohci_hcd 0000:02:01.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    2.192328] ohci_hcd 0000:02:01.0: OHCI Host Controller
[    2.192382] ohci_hcd 0000:02:01.0: new USB bus registered, assigned bus number 2
[    2.192410] ohci_hcd 0000:02:01.0: irq 17, io mem 0xe3007000
[    2.277836] usb usb2: configuration #1 chosen from 1 choice
[    2.277870] hub 2-0:1.0: USB hub found
[    2.277884] hub 2-0:1.0: 3 ports detected
[    2.277995] ohci_hcd 0000:02:01.1: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[    2.278011] ohci_hcd 0000:02:01.1: OHCI Host Controller
[    2.278064] ohci_hcd 0000:02:01.1: new USB bus registered, assigned bus number 3
[    2.278090] ohci_hcd 0000:02:01.1: irq 18, io mem 0xe3004000
[    2.361836] usb usb3: configuration #1 chosen from 1 choice
[    2.361870] hub 3-0:1.0: USB hub found
[    2.361883] hub 3-0:1.0: 2 ports detected
[    2.361980] uhci_hcd: USB Universal Host Controller Interface driver
[    2.362036] uhci_hcd 0000:00:1f.2: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    2.362048] uhci_hcd 0000:00:1f.2: setting latency timer to 64
[    2.362052] uhci_hcd 0000:00:1f.2: UHCI Host Controller
[    2.362110] uhci_hcd 0000:00:1f.2: new USB bus registered, assigned bus number 4
[    2.362135] uhci_hcd 0000:00:1f.2: irq 19, io base 0x0000d000
[    2.362217] usb usb4: configuration #1 chosen from 1 choice
[    2.362250] hub 4-0:1.0: USB hub found
[    2.362262] hub 4-0:1.0: 2 ports detected
[    2.362363] uhci_hcd 0000:00:1f.4: PCI INT C -> GSI 23 (level, low) -> IRQ 23
[    2.362374] uhci_hcd 0000:00:1f.4: setting latency timer to 64
[    2.362377] uhci_hcd 0000:00:1f.4: UHCI Host Controller
[    2.362445] uhci_hcd 0000:00:1f.4: new USB bus registered, assigned bus number 5
[    2.362478] uhci_hcd 0000:00:1f.4: irq 23, io base 0x0000d800
[    2.362564] usb usb5: configuration #1 chosen from 1 choice
[    2.362600] hub 5-0:1.0: USB hub found
[    2.362610] hub 5-0:1.0: 2 ports detected
[    2.362754] usbcore: registered new interface driver libusual
[    2.362800] usbcore: registered new interface driver usbserial
[    2.362815] USB Serial support registered for generic
[    2.362838] usbcore: registered new interface driver usbserial_generic
[    2.362843] usbserial: USB Serial Driver core
[    2.362909] PNP: No PS/2 controller found. Probing ports directly.
[    2.504012] usb 1-3: new high speed USB device using ehci_hcd and address 2
[    2.616396] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.616534] mice: PS/2 mouse device common for all mice
[    2.616733] rtc_cmos 00:05: RTC can wake from S4
[    2.616779] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    2.616805] rtc0: alarms up to one month, 242 bytes nvram
[    2.616912] device-mapper: uevent: version 1.0.3
[    2.617065] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: [email]dm-devel@redhat.com[/email]
[    2.617127] device-mapper: multipath: version 1.0.5 loaded
[    2.617133] device-mapper: multipath round-robin: version 1.0.0 loaded
[    2.617235] EISA: Probing bus 0 at eisa.0
[    2.617277] EISA: Detected 0 cards.
[    2.617313] cpuidle: using governor ladder
[    2.617318] cpuidle: using governor menu
[    2.617904] TCP cubic registered
[    2.617992] NET: Registered protocol family 10
[    2.618433] lo: Disabled Privacy Extensions
[    2.618791] NET: Registered protocol family 17
[    2.618818] Bluetooth: L2CAP ver 2.11
[    2.618823] Bluetooth: L2CAP socket layer initialized
[    2.618828] Bluetooth: SCO (Voice Link) ver 0.6
[    2.618832] Bluetooth: SCO socket layer initialized
[    2.618874] Bluetooth: RFCOMM socket layer initialized
[    2.618888] Bluetooth: RFCOMM TTY layer initialized
[    2.618892] Bluetooth: RFCOMM ver 1.10
[    2.618945] Using IPI No-Shortcut mode
[    2.619057] registered taskstats version 1
[    2.619181]   Magic number: 5:882:796
[    2.619271] rtc_cmos 00:05: setting system clock to 2009-04-10 18:47:31 UTC (1239389251)
[    2.619278] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.619283] EDD information not available.
[    2.619906] Freeing unused kernel memory: 532k freed
[    2.620062] Write protecting the kernel text: 4128k
[    2.620107] Write protecting the kernel read-only data: 1532k
[    2.649376] usb 1-3: configuration #1 chosen from 1 choice
[    2.716800] vesafb: framebuffer at 0xd0000000, mapped to 0xf7d00000, using 5120k, total 262144k
[    2.716814] vesafb: mode is 1280x1024x16, linelength=2560, pages=1
[    2.716819] vesafb: protected mode interface info at c000:d3a0
[    2.716824] vesafb: pmi: set display start = c00cd3d6, set palette = c00cd440
[    2.716828] vesafb: pmi: ports = 3b4 3b5 3ba 3c0 3c1 3c4 3c5 3c6 3c7 3c8 3c9 3cc 3ce 3cf 3d0 3d1 3d2 3d3 3d4 3d5 3da 
[    2.716852] vesafb: scrolling: redraw
[    2.716857] vesafb: Truecolor: size=0:5:6:5, shift=0:11:5:0
[    2.716974] Console: switching to colour frame buffer device 160x64
[    2.755124] fb0: VESA VGA frame buffer device
[    2.802814] usb 4-1: new low speed USB device using uhci_hcd and address 2
[    2.955155] Floppy drive(s): fd0 is 1.44M
[    2.975897] FDC 0 is a post-1991 82077
[    2.990723] usb 4-1: configuration #1 chosen from 1 choice
[    3.054764] via-rhine.c:v1.10-LK1.4.3 2007-03-06 Written by Donald Becker
[    3.055071] via-rhine: Broken BIOS detected, avoid_D3 enabled.
[    3.055371] via-rhine 0000:02:02.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    3.068868] eth0: VIA Rhine III at 0xe3008000, 00:08:54:22:42:bb, IRQ 18.
[    3.069836] eth0: MII PHY found at address 1, status 0x786d advertising 01e1 Link 41e1.
[    3.070215] ohci1394 0000:02:01.3: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    3.124003] ohci1394: fw-host0: Get PHY Reg timeout [0x00000000/0x00000000/100]
[    3.220016] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[17]  MMIO=[e3006000-e30067ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    3.224003] ohci1394: fw-host0: Get PHY Reg timeout [0x00000000/0x00000000/100]
[    3.650724] usbcore: registered new interface driver hiddev
[    3.651090] usbcore: registered new interface driver usbhid
[    3.651333] usbhid: v2.6:USB HID core driver
[    3.687365] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1f.2/usb4/4-1/4-1:1.0/input/input4
[    3.690791] logitech 0003:046D:C517.0001: input,hidraw0: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:1f.2-1/input0
[    3.718954] logitech 0003:046D:C517.0002: fixing up Logitech keyboard report descriptor
[    3.720386] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1f.2/usb4/4-1/4-1:1.1/input/input5
[    3.725689] logitech 0003:046D:C517.0002: input,hiddev96,hidraw1: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:1f.2-1/input1
[    4.204482] PM: Starting manual resume from disk
[    4.204685] PM: Resume from partition 8:5
[    4.204688] PM: Checking hibernation image.
[    4.204889] PM: Resume from disk failed.
[    4.258876] EXT4-fs: barriers enabled
[    4.289450] kjournald2 starting.  Commit interval 5 seconds
[    4.303568] EXT4-fs: delayed allocation enabled
[    4.317601] EXT4-fs: file extents enabled
[    4.344060] EXT4-fs: mballoc enabled
[    4.357842] EXT4-fs: mounted filesystem with ordered data mode.
[    4.384004] ohci1394: fw-host0: Get PHY Reg timeout [0x00000000/0x00000000/100]
[    7.820980] udev: starting version 140
[    8.007869] intel_rng: FWH not detected
[    8.143243] Linux agpgart interface v0.103
[    8.461107] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    8.785647] parport_pc 00:0b: reported by Plug and Play ACPI
[    8.798869] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[    8.824116] agpgart-intel 0000:00:00.0: Intel 845G Chipset
[    8.881954] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xc0000000
[    8.895997] iTCO_vendor_support: vendor-support=0
[    8.953745] input: PC Speaker as /devices/platform/pcspkr/input/input6
[    8.979373] ppdev: user-space parallel port driver
[    9.008211] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05
[    9.024079] iTCO_wdt: failed to reset NO_REBOOT flag, reboot disabled by hardware
[    9.037608] iTCO_wdt: No card detected
[    9.211298] nvidia: module license 'NVIDIA' taints kernel.
[    9.508223] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    9.526244] NVRM: loading NVIDIA UNIX x86 Kernel Module  180.44  Mon Mar 23 14:59:10 PST 2009
[    9.679379] Intel ICH 0000:00:1f.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    9.693390] Intel ICH 0000:00:1f.5: setting latency timer to 64
[   10.268013] intel8x0_measure_ac97_clock: measured 55402 usecs
[   10.281966] intel8x0: clocking to 48000
[   10.464021] lp0: using parport0 (interrupt-driven).
[   10.646973] Adding 1951856k swap on /dev/sda5.  Priority:-1 extents:1 across:1951856k
[   10.813920] EXT4 FS on sda2, internal journal on sda2:8
[   11.939064] type=1505 audit(1239410860.816:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=1830
[   12.009579] type=1505 audit(1239410860.888:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=1834
[   12.009838] type=1505 audit(1239410860.888:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=1834
[   12.009914] type=1505 audit(1239410860.888:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=1834
[   12.009975] type=1505 audit(1239410860.888:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=1834
[   12.183117] type=1505 audit(1239410861.060:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=1839
[   12.183441] type=1505 audit(1239410861.060:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=1839
[   12.221701] type=1505 audit(1239410861.100:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=1843
[   15.201233] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   15.201238] Bluetooth: BNEP filters: protocol multicast
[   15.227394] Bridge firewalling registered
[   17.937324] agpgart-intel 0000:00:00.0: AGP 2.0 bridge
[   17.937340] agpgart-intel 0000:00:00.0: putting AGP V2 device into 4x mode
[   17.937363] nvidia 0000:01:00.0: putting AGP V2 device into 4x mode
[   20.121505] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[   31.092018] eth0: no IPv6 routers present
[ 1230.607761] usb 1-3: USB disconnect, address 2
[ 1243.156025] usb 1-3: new high speed USB device using ehci_hcd and address 3
[ 1243.314302] usb 1-3: configuration #1 chosen from 1 choice
[ 1243.379082] Initializing USB Mass Storage driver...
[ 1243.380895] scsi2 : SCSI emulation for USB Mass Storage devices
[ 1243.383667] usbcore: registered new interface driver usb-storage
[ 1243.383674] USB Mass Storage support registered.
[ 1243.383794] usb-storage: device found at 3
[ 1243.383796] usb-storage: waiting for device to settle before scanning
[ 1248.382871] usb-storage: device scan complete
[ 1248.383349] scsi 2:0:0:0: Direct-Access     WD       5000AAV External 1.65 PQ: 0 ANSI: 4
[ 1248.387104] sd 2:0:0:0: [sdc] 976773168 512-byte hardware sectors: (500 GB/465 GiB)
[ 1248.434206] sd 2:0:0:0: [sdc] Write Protect is off
[ 1248.434211] sd 2:0:0:0: [sdc] Mode Sense: 21 00 00 00
[ 1248.434215] sd 2:0:0:0: [sdc] Assuming drive cache: write through
[ 1248.435196] sd 2:0:0:0: [sdc] 976773168 512-byte hardware sectors: (500 GB/465 GiB)
[ 1248.436937] sd 2:0:0:0: [sdc] Write Protect is off
[ 1248.436942] sd 2:0:0:0: [sdc] Mode Sense: 21 00 00 00
[ 1248.436946] sd 2:0:0:0: [sdc] Assuming drive cache: write through
[ 1248.436953]  sdc: sdc1
[ 1248.442892] sd 2:0:0:0: [sdc] Attached SCSI disk
[ 1248.442991] sd 2:0:0:0: Attached scsi generic sg3 type 0
```

---

### Post by llamabr on 2009-04-11
something in your /etc/fstab ?

Post it and we'll have a look.  this is a usb hard disk, or a flash drive, or what?

---

### Post by umanzor on 2009-04-11
> **llamabr said:**
> something in your /etc/fstab ?

Post it and we'll have a look.  this is a usb hard disk, or a flash drive, or what?

Hey there,

```
manuel@desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda2 :
UUID=d0ce6f7d-b22d-4e07-87c8-473497d1bcfc / ext4 relatime,errors=remount-ro 0 1
# Entry for /dev/sda5 :
UUID=95d00f9f-c06e-4845-a28f-130d19a18ed2 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0
/dev/sdb1 /media/Windows ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sda3 /media/documents ntfs-3g defaults,locale=en_US.UTF-8 0 0

```

That's my fstab. Also posting the output of df

```
manuel@desktop:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda2             92473576   3696932  84079240   5% /
tmpfs                   642772         0    642772   0% /lib/init/rw
varrun                  642772       108    642664   1% /var/run
varlock                 642772         0    642772   0% /var/lock
udev                    642772       108    642664   1% /dev
tmpfs                   642772       168    642604   1% /dev/shm
lrm                     642772      1992    640780   1% /lib/modules/2.6.28-11-generic/volatile
/dev/sdb1             33025020  12843136  20181884  39% /media/Windows
/dev/sda3            103137296   7064084  96073212   7% /media/documents
/dev/sdc1            488383996 285051936 203332060  59% /media/Media

```

/dev/sdc1, which is my external drive, is not on my fstab, I'll try adding it and see what happens.

Also, it is a an external USB hard drive.

Thanks.

---

### Post by umanzor on 2009-04-12
Any ideas? I had to move back to Windows due this and other small issues.

---

