---
title: "Beginner-My laptop freeze with 9.10"
date: 2009-10-31
forum: New to Ubuntu
---

### Post by lindix on 2009-10-31
I have an Advent laptop (Intel Celeron M 440,video card ATI Radeon Xpress 200M)
and keep crashing randomly(most of the times when I try to open and work with more applications-everytime I have tried diff. applications and the problem was still there)
Everything is freeze.I can move the mouse but I can't click.I can turn off the computer by pressing the power (only) .

Please I need some help.I don't know where to start looking.

---

### Post by Liolikas on 2009-10-31
Try keys like ctrl+alt+F1 ctrl+alt+F2 ctrl+alt+backspace.
Try to get dmesg command output, really possible if upper keys give some real result. Or over shh but if you do not know how to ssh then problem too..
Try to uninstall any drivers you installed (do as clean setup as possible for testing). 
If no luck simply try older Ubuntu versions.

---

### Post by mapes12 on 2009-10-31
> If no luck simply try older Ubuntu versions.8.04LTS would be my suggestion. Install then let Update Manager bring in the newer updates.

---

### Post by lindix on 2009-10-31
ubuntu 9.04 works great.
but ubuntu 9.10 is beautiful and is very fast until freeze.
i'd like to repot this bug.this is dmesg command output.maybe someone can tell me what's wrong
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.31-14-generic (buildd@rothera) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 (Ubuntu 2.6.31-14.48-generic)
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
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009dc00 (usable)
[    0.000000]  BIOS-e820: 000000000009dc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000ce000 - 00000000000d0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000dc000 - 00000000000e0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000006fe90000 (usable)
[    0.000000]  BIOS-e820: 000000006fe90000 - 000000006fea2000 (ACPI data)
[    0.000000]  BIOS-e820: 000000006fea2000 - 000000006ff00000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000006ff00000 - 0000000070000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] DMI present.
[    0.000000] Phoenix BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0x6fe90 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-DFFFF uncachable
[    0.000000]   E0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask FC0000000 write-back
[    0.000000]   1 base 040000000 mask FE0000000 write-back
[    0.000000]   2 base 060000000 mask FF0000000 write-back
[    0.000000]   3 base 06FF00000 mask FFFF00000 uncachable
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] PAT not supported by CPU.
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009dc00 (usable)
[    0.000000]  modified: 000000000009dc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000ce000 - 00000000000d0000 (reserved)
[    0.000000]  modified: 00000000000dc000 - 00000000000e0000 (reserved)
[    0.000000]  modified: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000006fe90000 (usable)
[    0.000000]  modified: 000000006fe90000 - 000000006fea2000 (ACPI data)
[    0.000000]  modified: 000000006fea2000 - 000000006ff00000 (ACPI NVS)
[    0.000000]  modified: 000000006ff00000 - 0000000070000000 (reserved)
[    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 10000-15000
[    0.000000] RAMDISK: 6f8e2000 - 6fe5f098
[    0.000000] Allocated new RAMDISK: 008ad000 - 00e2a098
[    0.000000] Move RAMDISK from 000000006f8e2000 - 000000006fe5f097 to 008ad000 - 00e2a097
[    0.000000] ACPI: RSDP 000f7260 00014 (v00 PTLTD )
[    0.000000] ACPI: RSDT 6fe9c599 0003C (v01 DSGLTD DSGVISTA 06040000  LTP 00000000)
[    0.000000] ACPI: FACP 6fea1d8a 00074 (v01 DSGLTD DSGVISTA 06040000 ATI  000F4240)
[    0.000000] ACPI: DSDT 6fe9ccfa 05090 (v01 DSGLTD DSGVISTA 06040000 MSFT 02000002)
[    0.000000] ACPI: FACS 6fea2fc0 00040
[    0.000000] ACPI: APIC 6fea1dfe 00050 (v01 DSGLTD DSGVISTA 06040000  LTP 00000000)
[    0.000000] ACPI: MCFG 6fea1e4e 0003C (v01 DSGLTD DSGVISTA 06040000  LTP 00000000)
[    0.000000] ACPI: SLIC 6fea1e8a 00176 (v01 DSGLTD DSGVISTA 06040000  LTP 00000000)
[    0.000000] ACPI: SSDT 6fe9cb0a 001F0 (v01  PmRef  Cpu0Cst 00003001 INTL 20050228)
[    0.000000] ACPI: SSDT 6fe9c5d5 00535 (v01  PmRef    CpuPm 00003000 INTL 20050228)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 902MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000]   node 0 low ram: 00000000 - 377fe000
[    0.000000]   node 0 bootmap 00011000 - 00017f00
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008a80a0]    TEXT DATA BSS ==> [0000100000 - 00008a80a0]
[    0.000000]   #4 [000009dc00 - 0000100000]    BIOS reserved ==> [000009dc00 - 0000100000]
[    0.000000]   #5 [00008a9000 - 00008ac244]              BRK ==> [00008a9000 - 00008ac244]
[    0.000000]   #6 [0000010000 - 0000011000]          PGTABLE ==> [0000010000 - 0000011000]
[    0.000000]   #7 [00008ad000 - 0000e2a098]      NEW RAMDISK ==> [00008ad000 - 0000e2a098]
[    0.000000]   #8 [0000011000 - 0000018000]          BOOTMAP ==> [0000011000 - 0000018000]
[    0.000000] found SMP MP-table at [c00f7320] f7320
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0006fe90
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009d
[    0.000000]     0: 0x00000100 -> 0x0006fe90
[    0.000000] On node 0 totalpages: 458269
[    0.000000] free_area_init_node: node 0, pgdat c0784900, node_mem_map c1000200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3949 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 1806 pages used for memmap
[    0.000000]   HighMem zone: 229252 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] SB4X0 revision 0x82
[    0.000000] Ignoring ACPI timer override.
[    0.000000] If you got timer trouble try acpi_use_timer_override
[    0.000000] ACPI: PM-Timer IO Port: 0x8008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 21 low level)
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000ce000
[    0.000000] PM: Registered nosave memory: 00000000000ce000 - 00000000000d0000
[    0.000000] PM: Registered nosave memory: 00000000000d0000 - 00000000000dc000
[    0.000000] PM: Registered nosave memory: 00000000000dc000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 00000000000e4000
[    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 70000000 (gap: 70000000:70000000)
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages at c1e07000, static data 35612 bytes
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 454687
[    0.000000] Kernel command line: BOOT_IMAGE=/casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash --
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 9167360 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0006fe90)
[    0.000000] Memory: 1794576k/1833536k available (4565k kernel code, 37672k reserved, 2143k data, 540k init, 924232k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc078e000 - 0xc0815000   ( 540 kB)
[    0.000000]       .data : 0xc0575554 - 0xc078d308   (2143 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0575554   (4565 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.000000] NR_IRQS:2304 nr_irqs:256
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1866.302 MHz processor.
[    0.000951] Console: colour VGA+ 80x25
[    0.000956] console [tty0] enabled
[    0.001032] Calibrating delay loop (skipped), value calculated using timer frequency.. 3732.60 BogoMIPS (lpj=7465208)
[    0.001065] Security Framework initialized
[    0.001111] AppArmor: AppArmor initialized
[    0.001121] Mount-cache hash table entries: 512
[    0.001323] Initializing cgroup subsys ns
[    0.001332] Initializing cgroup subsys cpuacct
[    0.001337] Initializing cgroup subsys memory
[    0.001348] Initializing cgroup subsys freezer
[    0.001351] Initializing cgroup subsys net_cls
[    0.001372] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.001375] CPU: L2 cache: 1024K
[    0.001382] mce: CPU supports 6 MCE banks
[    0.001396] CPU0: Thermal monitoring enabled (TM1)
[    0.001402] using mwait in idle threads.
[    0.001415] Performance Counters: no PMU driver, software counters only.
[    0.001425] Checking 'hlt' instruction... OK.
[    0.016942] SMP alternatives: switching to UP code
[    0.024022] Freeing SMP alternatives: 19k freed
[    0.024045] ACPI: Core revision 20090521
[    0.036319]   alloc irq_desc for 21 on node 0
[    0.036322]   alloc kstat_irqs on node 0
[    0.036465] ..TIMER: vector=0x30 apic1=0 pin1=0 apic2=-1 pin2=-1
[    0.077731] CPU0: Intel(R) Celeron(R) M CPU        440  @ 1.86GHz stepping 0c
[    0.080001] Brought up 1 CPUs
[    0.080001] Total of 1 processors activated (3732.60 BogoMIPS).
[    0.080001] CPU0 attaching NULL sched-domain.
[    0.080001] Booting paravirtualized kernel on bare hardware
[    0.080001] regulator: core version 0.5
[    0.080001] Time: 17:35:40  Date: 10/31/09
[    0.080001] NET: Registered protocol family 16
[    0.080001] EISA bus registered
[    0.080001] ACPI: bus type pci registered
[    0.080001] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 13
[    0.080001] PCI: MCFG area at e0000000 reserved in E820
[    0.080001] PCI: Using MMCONFIG for extended config space
[    0.080001] PCI: Using configuration type 1 for base access
[    0.080001] bio: create slab <bio-0> at 0
[    0.080001] ACPI: EC: Look up EC in DSDT
[    0.081894] ACPI Error (dswload-0674): [\___p] Namespace lookup failure, AE_NOT_FOUND
[    0.081900] ACPI Exception: AE_NOT_FOUND, During name lookup/catalog 20090521 psloop-227
[    0.081906] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._:
INI] (Node f700f690), AE_NOT_FOUND
[    0.082168] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    0.220081] ACPI: Interpreter enabled
[    0.220092] ACPI: (supports S0 S3 S4 S5)
[    0.220113] ACPI: Using IOAPIC for interrupt routing
[    0.226299] ACPI: EC: GPE = 0x10, I/O: command/status = 0x66, data = 0x62
[    0.226303] ACPI: EC: driver started in interrupt mode
[    0.226740] ACPI: No dock devices found.
[    0.227353] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.227552] pci 0000:00:12.0: reg 10 io port: [0x8440-0x8447]
[    0.227563] pci 0000:00:12.0: reg 14 io port: [0x8430-0x8433]
[    0.227573] pci 0000:00:12.0: reg 18 io port: [0x8420-0x8427]
[    0.227583] pci 0000:00:12.0: reg 1c io port: [0x8410-0x8413]
[    0.227594] pci 0000:00:12.0: reg 20 io port: [0x8400-0x840f]
[    0.227604] pci 0000:00:12.0: reg 24 32bit mmio: [0xc0407000-0xc04071ff]
[    0.227615] pci 0000:00:12.0: reg 30 32bit mmio: [0x000000-0x07ffff]
[    0.227655] pci 0000:00:12.0: supports D1 D2
[    0.227696] pci 0000:00:13.0: reg 10 32bit mmio: [0xc0404000-0xc0404fff]
[    0.227783] pci 0000:00:13.1: reg 10 32bit mmio: [0xc0405000-0xc0405fff]
[    0.227893] pci 0000:00:13.2: reg 10 32bit mmio: [0xc0406000-0xc0406fff]
[    0.227969] pci 0000:00:13.2: supports D1 D2
[    0.227972] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
[    0.227978] pci 0000:00:13.2: PME# disabled
[    0.228033] pci 0000:00:14.0: reg 10 io port: [0x8040-0x804f]
[    0.228043] pci 0000:00:14.0: reg 14 32bit mmio: [0xc0407400-0xc04077ff]
[    0.228087] HPET not enabled in BIOS. You might try hpet=force boot option
[    0.228142] pci 0000:00:14.1: reg 10 io port: [0x1f0-0x1f7]
[    0.228152] pci 0000:00:14.1: reg 14 io port: [0x3f4-0x3f7]
[    0.228162] pci 0000:00:14.1: reg 18 io port: [0x170-0x177]
[    0.228173] pci 0000:00:14.1: reg 1c io port: [0x374-0x377]
[    0.228183] pci 0000:00:14.1: reg 20 io port: [0x8460-0x846f]
[    0.228302] pci 0000:00:14.2: reg 10 64bit mmio: [0xc0400000-0xc0403fff]
[    0.228378] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
[    0.228384] pci 0000:00:14.2: PME# disabled
[    0.228586] pci 0000:01:05.0: reg 10 32bit mmio: [0xd0000000-0xdfffffff]
[    0.228593] pci 0000:01:05.0: reg 14 io port: [0x9000-0x90ff]
[    0.228599] pci 0000:01:05.0: reg 18 32bit mmio: [0xc0000000-0xc000ffff]
[    0.228614] pci 0000:01:05.0: reg 30 32bit mmio: [0x000000-0x01ffff]
[    0.228631] pci 0000:01:05.0: supports D1 D2
[    0.228660] pci 0000:00:01.0: bridge io port: [0x9000-0x9fff]
[    0.228664] pci 0000:00:01.0: bridge 32bit mmio: [0xc0000000-0xc00fffff]
[    0.228669] pci 0000:00:01.0: bridge 32bit mmio pref: [0xd0000000-0xdfffffff]
[    0.228739] pci 0000:09:02.0: reg 10 io port: [0xa000-0xa0ff]
[    0.228751] pci 0000:09:02.0: reg 14 32bit mmio: [0xc0100000-0xc01000ff]
[    0.228833] pci 0000:09:02.0: supports D1 D2
[    0.228836] pci 0000:09:02.0: PME# supported from D1 D2 D3hot D3cold
[    0.228842] pci 0000:09:02.0: PME# disabled
[    0.228909] pci 0000:09:04.0: reg 10 32bit mmio: [0xc0108000-0xc010ffff]
[    0.229072] pci 0000:00:14.4: transparent bridge
[    0.229082] pci 0000:00:14.4: bridge io port: [0xa000-0xafff]
[    0.229089] pci 0000:00:14.4: bridge 32bit mmio: [0xc0100000-0xc01fffff]
[    0.229108] pci_bus 0000:00: on NUMA node 0
[    0.229113] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.229316] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[    0.229422] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    0.231237] ACPI: PCI Interrupt Link [LNKA] (IRQs 10 11) *0, disabled.
[    0.231355] ACPI: PCI Interrupt Link [LNKB] (IRQs 10 11) *0, disabled.
[    0.231466] ACPI: PCI Interrupt Link [LNKC] (IRQs 10 11) *0, disabled.
[    0.231576] ACPI: PCI Interrupt Link [LNKD] (IRQs 10 11) *0, disabled.
[    0.231687] ACPI: PCI Interrupt Link [LNKE] (IRQs 10 11) *0, disabled.
[    0.231795] ACPI: PCI Interrupt Link [LNKF] (IRQs 10 11) *0, disabled.
[    0.231906] ACPI: PCI Interrupt Link [LNKG] (IRQs 10 11) *0, disabled.
[    0.232026] ACPI: PCI Interrupt Link [LNKH] (IRQs 10 11) *0, disabled.
[    0.232241] SCSI subsystem initialized
[    0.232303] libata version 3.00 loaded.
[    0.232379] usbcore: registered new interface driver usbfs
[    0.232397] usbcore: registered new interface driver hub
[    0.232424] usbcore: registered new device driver usb
[    0.232570] ACPI: WMI: Mapper loaded
[    0.232572] PCI: Using ACPI for IRQ routing
[    0.232747] Bluetooth: Core ver 2.15
[    0.232776] NET: Registered protocol family 31
[    0.232778] Bluetooth: HCI device and connection manager initialized
[    0.232782] Bluetooth: HCI socket layer initialized
[    0.232785] NetLabel: Initializing
[    0.232787] NetLabel:  domain hash size = 128
[    0.232789] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.232804] NetLabel:  unlabeled traffic allowed by default
[    0.234834] pnp: PnP ACPI init
[    0.234866] ACPI: bus type pnp registered
[    0.236630] pnp 00:09: mem resource (0x0-0xfff) overlaps 0000:00:12.0 BAR 6 (0x0-0x7ffff), disabling
[    0.236641] pnp 00:09: mem resource (0x0-0xfff) overlaps 0000:01:05.0 BAR 6 (0x0-0x1ffff), disabling
[    0.236828] pnp: PnP ACPI: found 10 devices
[    0.236830] ACPI: ACPI bus type pnp unregistered
[    0.236836] PnPBIOS: Disabled by ACPI PNP
[    0.236853] system 00:01: iomem range 0xe0000000-0xefffffff has been reserved
[    0.236862] system 00:08: ioport range 0x1080-0x1080 has been reserved
[    0.236866] system 00:08: ioport range 0x200-0x20f has been reserved
[    0.236869] system 00:08: ioport range 0x40b-0x40b has been reserved
[    0.236873] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
[    0.236876] system 00:08: ioport range 0x4d6-0x4d6 has been reserved
[    0.236879] system 00:08: ioport range 0x530-0x537 has been reserved
[    0.236882] system 00:08: ioport range 0xc00-0xc01 has been reserved
[    0.236886] system 00:08: ioport range 0xc14-0xc14 has been reserved
[    0.236889] system 00:08: ioport range 0xc50-0xc52 has been reserved
[    0.236892] system 00:08: ioport range 0xc6c-0xc6c has been reserved
[    0.236896] system 00:08: ioport range 0xc6f-0xc6f has been reserved
[    0.236899] system 00:08: ioport range 0xcd4-0xcd5 has been reserved
[    0.236902] system 00:08: ioport range 0xcd6-0xcd7 has been reserved
[    0.236906] system 00:08: ioport range 0xcd8-0xcdf has been reserved
[    0.236909] system 00:08: ioport range 0x8000-0x805f could not be reserved
[    0.236913] system 00:08: ioport range 0xf40-0xf47 has been reserved
[    0.236916] system 00:08: ioport range 0x280-0x293 has been reserved
[    0.236919] system 00:08: ioport range 0x87f-0x87f has been reserved
[    0.236926] system 00:09: iomem range 0xe0000-0xfffff could not be reserved
[    0.236929] system 00:09: iomem range 0xfff80000-0xffffffff has been reserved
[    0.271686] AppArmor: AppArmor Filesystem Enabled
[    0.271717] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.271720] pci 0000:00:01.0:   IO window: 0x9000-0x9fff
[    0.271726] pci 0000:00:01.0:   MEM window: 0xc0000000-0xc00fffff
[    0.271730] pci 0000:00:01.0:   PREFETCH window: 0xd0000000-0xdfffffff
[    0.271735] pci 0000:00:14.4: PCI bridge, secondary bus 0000:09
[    0.271739] pci 0000:00:14.4:   IO window: 0xa000-0xafff
[    0.271747] pci 0000:00:14.4:   MEM window: 0xc0100000-0xc01fffff
[    0.271753] pci 0000:00:14.4:   PREFETCH window: disabled
[    0.271776] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.271779] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.271782] pci_bus 0000:01: resource 0 io:  [0x9000-0x9fff]
[    0.271785] pci_bus 0000:01: resource 1 mem: [0xc0000000-0xc00fffff]
[    0.271788] pci_bus 0000:01: resource 2 pref mem [0xd0000000-0xdfffffff]
[    0.271791] pci_bus 0000:09: resource 0 io:  [0xa000-0xafff]
[    0.271794] pci_bus 0000:09: resource 1 mem: [0xc0100000-0xc01fffff]
[    0.271798] pci_bus 0000:09: resource 3 io:  [0x00-0xffff]
[    0.271800] pci_bus 0000:09: resource 4 mem: [0x000000-0xffffffff]
[    0.271844] NET: Registered protocol family 2
[    0.271951] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.272430] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.273967] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.274974] TCP: Hash tables configured (established 131072 bind 65536)
[    0.274979] TCP reno registered
[    0.275164] NET: Registered protocol family 1
[    0.275270] Trying to unpack rootfs image as initramfs...
[    0.772137] Switched to high resolution mode on CPU 0
[    1.934527] Freeing initrd memory: 5620k freed
[    1.947231] cpufreq-nforce2: No nForce2 chipset.
[    1.947272] Scanning for low memory corruption every 60 seconds
[    1.947436] audit: initializing netlink socket (disabled)
[    1.947473] type=2000 audit(1257010540.944:1): initialized
[    1.956978] highmem bounce pool size: 64 pages
[    1.956985] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.958535] VFS: Disk quotas dquot_6.5.2
[    1.958602] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.959192] fuse init (API version 7.12)
[    1.959284] msgmni has been set to 1712
[    1.959499] alg: No test for stdrng (krng)
[    1.959512] io scheduler noop registered
[    1.959515] io scheduler anticipatory registered
[    1.959517] io scheduler deadline registered
[    1.959565] io scheduler cfq registered (default)
[    1.959633] pci 0000:01:05.0: Boot video device
[    1.959723] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.959748] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.969434] ACPI: AC Adapter [ACAD] (on-line)
[    1.969508] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
nput1
[    1.969624] ACPI: Lid Switch [LID]
[    1.969675] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input2
[    1.969679] ACPI: Power Button [PWRB]
[    1.970311] Marking TSC unstable due to TSC halts in idle
[    1.970337] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    1.970363] processor LNXCPU:00: registered as cooling_device0
[    1.970367] ACPI: Processor [CPU0] (supports 8 throttling states)
[    1.994588] thermal LNXTHERM:01: registered as thermal_zone0
[    1.994598] ACPI: Thermal Zone [THRM] (79 C)
[    1.994652] isapnp: Scanning for PnP cards...
[    2.000299] ACPI: Battery Slot [BAT1] (battery absent)
[    2.351523] isapnp: No Plug & Play device found
[    2.352668] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    2.354042] brd: module loaded
[    2.354520] loop: module loaded
[    2.354608] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    2.354747] sata_sil 0000:00:12.0: version 2.4
[    2.354799] sata_sil 0000:00:12.0: enabling device (0005 -> 0007)
[    2.354809]   alloc irq_desc for 22 on node -1
[    2.354812]   alloc kstat_irqs on node -1
[    2.354821] sata_sil 0000:00:12.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    2.354937] scsi0 : sata_sil
[    2.355041] scsi1 : sata_sil
[    2.355255] ata1: SATA max UDMA/100 mmio m512@0xc0407000 tf 0xc0407080 irq 22
[    2.355260] ata2: SATA max UDMA/100 mmio m512@0xc0407000 tf 0xc04070c0 irq 22
[    2.355423]   alloc irq_desc for 16 on node -1
[    2.355426]   alloc kstat_irqs on node -1
[    2.355431] pata_atiixp 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.355479] pata_atiixp 0000:00:14.1: setting latency timer to 64
[    2.355597] scsi2 : pata_atiixp
[    2.355674] scsi3 : pata_atiixp
[    2.356030] ata3: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x8460 irq 14
[    2.356034] ata4: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x8468 irq 15
[    2.356693] Fixed MDIO Bus: probed
[    2.356731] PPP generic driver version 2.4.2
[    2.356837] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.356862]   alloc irq_desc for 19 on node -1
[    2.356864]   alloc kstat_irqs on node -1
[    2.356871] ehci_hcd 0000:00:13.2: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    2.356886] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    2.356952] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 1
[    2.357019] ehci_hcd 0000:00:13.2: irq 19, io mem 0xc0406000
[    2.368030] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    2.368137] usb usb1: configuration #1 chosen from 1 choice
[    2.368169] hub 1-0:1.0: USB hub found
[    2.368181] hub 1-0:1.0: 8 ports detected
[    2.368278] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.368295] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    2.368307] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    2.368339] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 2
[    2.368359] ohci_hcd 0000:00:13.0: irq 19, io mem 0xc0404000
[    2.424113] usb usb2: configuration #1 chosen from 1 choice
[    2.424145] hub 2-0:1.0: USB hub found
[    2.424161] hub 2-0:1.0: 4 ports detected
[    2.424217] ohci_hcd 0000:00:13.1: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    2.424228] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    2.424265] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 3
[    2.424284] ohci_hcd 0000:00:13.1: irq 19, io mem 0xc0405000
[    2.480119] usb usb3: configuration #1 chosen from 1 choice
[    2.480146] hub 3-0:1.0: USB hub found
[    2.480162] hub 3-0:1.0: 4 ports detected
[    2.480220] uhci_hcd: USB Universal Host Controller Interface driver
[    2.480317] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[    2.482750] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.482757] serio: i8042 AUX port at 0x60,0x64 irq 12
[    2.482819] mice: PS/2 mouse device common for all mice
[    2.482956] rtc_cmos 00:04: RTC can wake from S4
[    2.483000] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    2.483033] rtc0: alarms up to one month, 114 bytes nvram
[    2.483140] device-mapper: uevent: version 1.0.3
[    2.483246] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    2.483336] device-mapper: multipath: version 1.1.0 loaded
[    2.483340] device-mapper: multipath round-robin: version 1.0.0 loaded
[    2.483475] EISA: Probing bus 0 at eisa.0
[    2.483486] Cannot allocate resource for EISA slot 1
[    2.483516] Cannot allocate resource for EISA slot 8
[    2.483519] EISA: Detected 0 cards.
[    2.483618] cpuidle: using governor ladder
[    2.483681] cpuidle: using governor menu
[    2.484201] TCP cubic registered
[    2.484372] NET: Registered protocol family 10
[    2.484814] lo: Disabled Privacy Extensions
[    2.485121] NET: Registered protocol family 17
[    2.485140] Bluetooth: L2CAP ver 2.13
[    2.485142] Bluetooth: L2CAP socket layer initialized
[    2.485145] Bluetooth: SCO (Voice Link) ver 0.6
[    2.485147] Bluetooth: SCO socket layer initialized
[    2.485186] Bluetooth: RFCOMM TTY layer initialized
[    2.485189] Bluetooth: RFCOMM socket layer initialized
[    2.485192] Bluetooth: RFCOMM ver 1.11
[    2.485229] Using IPI No-Shortcut mode
[    2.485294] PM: Resume from disk failed.
[    2.485309] registered taskstats version 1
[    2.485411]   Magic number: 13:188:594
[    2.485527] rtc_cmos 00:04: setting system clock to 2009-10-31 17:35:42 UTC (1257010542)
[    2.485531] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.485533] EDD information not available.
[    2.515324] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    2.672082] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.680583] ata1.00: ATA-7: Hitachi HTS541680J9SA00, SB2OC70P, max UDMA/100
[    2.680587] ata1.00: 156301488 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    2.696584] ata1.00: configured for UDMA/100
[    2.696735] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS54168 SB2O PQ: 0 ANSI: 5
[    2.696866] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.696911] sd 0:0:0:0: [sda] 156301488 512-byte logical blocks: (80.0 GB/74.5 GiB)
[    2.696962] sd 0:0:0:0: [sda] Write Protect is off
[    2.696966] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.696992] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.697133]  sda:
[    2.736052] usb 1-3: new high speed USB device using ehci_hcd and address 3
[    2.871077] usb 1-3: configuration #1 chosen from 1 choice
[    3.016058] ata2: SATA link down (SStatus 0 SControl 300)
[    3.082035]  sda1 sda2 < sda5 sda6 >
[    3.121808] sd 0:0:0:0: [sda] Attached SCSI disk
[    3.172269] usb 2-1: new low speed USB device using ohci_hcd and address 2
[    3.180629] ata4.00: ATAPI: Optiarc DVD RW AD-7530A, EX33, max UDMA/33
[    3.196592] ata4.00: configured for UDMA/33
[    3.197578] scsi 3:0:0:0: CD-ROM            Optiarc  DVD RW AD-7530A  EX33 PQ: 0 ANSI: 5
[    3.200014] sr0: scsi3-mmc drive: 47x/47x writer dvd-ram cd/rw xa/form2 cdda tray
[    3.200018] Uniform CD-ROM driver Revision: 3.20
[    3.200105] sr 3:0:0:0: Attached scsi CD-ROM sr0
[    3.200158] sr 3:0:0:0: Attached scsi generic sg1 type 5
[    3.200182] Freeing unused kernel memory: 540k freed
[    3.200660] Write protecting the kernel text: 4568k
[    3.200698] Write protecting the kernel read-only data: 1836k
[    3.388361] Linux agpgart interface v0.103
[    3.392416] usb 2-1: configuration #1 chosen from 1 choice
[    3.537965] [drm] Initialized drm 1.1.0 20060810
[    3.561355] [drm] radeon default to kernel modesetting DISABLED.
[    3.561548]   alloc irq_desc for 17 on node -1
[    3.561551]   alloc kstat_irqs on node -1
[    3.561561] pci 0000:01:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    3.561727] [drm] Initialized radeon 1.31.0 20080528 for 0000:01:05.0 on minor 0
[    3.570965] <6>8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    3.571000] 8139cp 0000:09:02.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
[    3.575709] 8139too Fast Ethernet driver 0.9.28
[    3.575769] 8139too 0000:09:02.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    3.577398] eth0: RealTek RTL8139 at 0xa000, 00:1b:24:21:07:3c, IRQ 21
[    3.584979] Initializing USB Mass Storage driver...
[    3.585120] scsi4 : SCSI emulation for USB Mass Storage devices
[    3.585218] usbcore: registered new interface driver usb-storage
[    3.585222] USB Mass Storage support registered.
[    3.592315] usb-storage: device found at 3
[    3.592320] usb-storage: waiting for device to settle before scanning
[    3.593896] usbcore: registered new interface driver hiddev
[    3.606950] input: HID 04d9:048e as /devices/pci0000:00/0000:00:13.0/usb2/2-1/2-1:1.0/input/input5
[    3.607051] generic-usb 0003:04D9:048E.0001: input,hidraw0: USB HID v1.10 Mouse [HID 04d9:048e] on usb-0000:00:13.0-1/input0
[    3.607074] usbcore: registered new interface driver usbhid
[    3.607078] usbhid: v2.6:USB HID core driver
[    3.625356] acpi device:1e: registered as cooling_device1
[    3.625465] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:1b/device:1c/input/input6
[    3.625516] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[    4.480396] xor: automatically using best checksumming function: pIII_sse
[    4.500015]    pIII_sse  :  4745.000 MB/sec
[    4.500018] xor: using function: pIII_sse (4745.000 MB/sec)
[    4.503678] device-mapper: dm-raid45: initialized v0.2594b
[    4.665866] kjournald starting.  Commit interval 5 seconds
[    4.665882] EXT3-fs: mounted filesystem with writeback data mode.
[    6.007561] ISO 9660 Extensions: Microsoft Joliet Level 3
[    6.036604] ISO 9660 Extensions: RRIP_1991A
[    6.299451] aufs 2-standalone.tree-30-20090727
[    6.479354] squashfs: version 4.0 (2009/01/31) Phillip Lougher
[    8.592350] usb-storage: device scan complete
[    8.592931] scsi 4:0:0:0: Direct-Access     Kingston DataTraveler 2.0 PMAP PQ: 0 ANSI: 0 CCS
[    8.593435] sd 4:0:0:0: Attached scsi generic sg2 type 0
[    8.595417] sd 4:0:0:0: [sdb] 1953792 512-byte logical blocks: (1.00 GB/954 MiB)
[    8.595904] sd 4:0:0:0: [sdb] Write Protect is off
[    8.595907] sd 4:0:0:0: [sdb] Mode Sense: 23 00 00 00
[    8.595910] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[    8.598150] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[    8.598154]  sdb: sdb1
[    8.603921] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[    8.603928] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[   65.126190] Adding 2626588k swap on /dev/sda6.  Priority:-1 extents:1 across:2626588k 
[   66.674667] udev: starting version 147
[   69.494985] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0x8040, revision 0
[   69.853737] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   70.340432] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x25a0b1, caps: 0xa04713/0x0
[   70.374592] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input7
[   70.790901] cfg80211: Calling CRDA to update world regulatory domain
[   73.831149] rt61pci 0000:09:04.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   75.026161] ip_tables: (C) 2000-2006 Netfilter Core Team
[   75.433896] cfg80211: World regulatory domain updated:
[   75.433903]  (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   75.433907]  (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   75.433910]  (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   75.433913]  (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   75.433916]  (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   75.433919]  (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   76.103373] phy0: Selected rate control algorithm 'minstrel'
[   76.104112] Registered led device: rt61pci-phy0::radio
[   76.104136] Registered led device: rt61pci-phy0::assoc
[   76.974893] eth0: link down
[   76.975184] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   76.977684] rt61pci 0000:09:04.0: firmware: requesting rt2561.bin
[   77.092205] input: rt61pci as /devices/pci0000:00/0000:00:14.4/0000:09:04.0/input/input8
[   77.116343] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   77.494712] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   77.593675] hda_codec: Unknown model for ALC861-VD, trying auto-probe from BIOS...
[   77.593798] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:14.2/input/input9
[   85.270605] lp: driver loaded but no devices found
[   85.482356] ppdev: user-space parallel port driver
[   91.828967] [drm] Setting GART location based on new memory map
[   91.829644] [drm] Loading R300 Microcode
[   91.829679] [drm] Num pipes: 2
[   91.829687] [drm] writeback test succeeded in 1 usecs
[  184.387588] usb 1-3: USB disconnect, address 3
[  189.704055] usb 1-3: new high speed USB device using ehci_hcd and address 4
[  189.839107] usb 1-3: configuration #1 chosen from 1 choice
[  189.841129] scsi5 : SCSI emulation for USB Mass Storage devices
[  189.841255] usb-storage: device found at 4
[  189.841257] usb-storage: waiting for device to settle before scanning
[  194.840342] usb-storage: device scan complete
[  194.840941] scsi 5:0:0:0: Direct-Access     Kingston DataTraveler 2.0 PMAP PQ: 0 A:
NSI: 0 CCS
[  194.841423] sd 5:0:0:0: Attached scsi generic sg2 type 0
[  195.038205] sd 5:0:0:0: [sdb] 1953792 512-byte logical blocks: (1.00 GB/954 MiB)
[  195.038690] sd 5:0:0:0: [sdb] Write Protect is off
[  195.038693] sd 5:0:0:0: [sdb] Mode Sense: 23 00 00 00
[  195.038696] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[  195.042058] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[  195.042065]  sdb: sdb1
[  195.050195] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[  195.050203] sd 5:0:0:0: [sdb] Attached SCSI removable disk


```

---

