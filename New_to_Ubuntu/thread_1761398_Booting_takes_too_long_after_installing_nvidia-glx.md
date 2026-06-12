---
title: "Booting takes too long after installing nvidia-glx-185"
date: 2011-05-18
forum: New to Ubuntu
---

### Post by komoyon on 2011-05-18
I installed ubuntu 11.04 on my laptop (Gigabyte W566N) a few days ago.
At first boot it logged me with ubuntu classic not with unity.
W566N has GeForce 8400M GS so I installed nvidia-glx-185 in Synaptic package manager.
But after installation rebooting took about 6 minutes! :(
Please take a look at my dmesg log and give me some advice.
I'm lost now and any advice would be greatly helpful to me!

dmesg log
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.38-8-generic (buildd@vernadsky) (gcc version 4.5.2 (Ubuntu/Linaro 4.5.2-8ubuntu3) ) #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 (Ubuntu 2.6.38-8.42-generic 2.6.38.2)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009b800 (usable)
[    0.000000]  BIOS-e820: 000000000009b800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d2000 - 00000000000d4000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007fec0000 (usable)
[    0.000000]  BIOS-e820: 000000007fec0000 - 000000007fecb000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007fecb000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] Notice: NX (Execute Disable) protection cannot be enabled in hardware: non-PAE kernel!
[    0.000000] NX (Execute Disable) protection: approximated by x86 segment limits
[    0.000000] DMI present.
[    0.000000] DMI: GIGABYTE W566N/W566N                           , BIOS G3D18                          09/23/2008
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x7fec0 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 07FF00000 mask FFFF00000 uncachable
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] found SMP MP-table at [c00f7e50] f7e50
[    0.000000] initial memory mapped : 0 - 01c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 1bfb000-1c00000
[    0.000000] RAMDISK: 3677c000 - 373b6000
[    0.000000] ACPI: RSDP 000f7d40 00024 (v02 HP    )
[    0.000000] ACPI: XSDT 7fec314a 0008C (v01 GBT    GBTUACPI 06040000  LTP 00000000)
[    0.000000] ACPI: FACP 7fec9bd2 000F4 (v03 GBT    GBTUACPI 06040000 ALAN 00000001)
[    0.000000] ACPI: DSDT 7fec4662 054FC (v02 GBT    GBTUACPI 06040000 INTL 20060707)
[    0.000000] ACPI: FACS 7fecafc0 00040
[    0.000000] ACPI: APIC 7fec9cc6 00068 (v01 GBT    GBTUACPI 06040000 LOHR 0000005A)
[    0.000000] ACPI: HPET 7fec9d2e 00038 (v01 GBT    GBTUACPI 06040000 LOHR 0000005A)
[    0.000000] ACPI: MCFG 7fec9d66 0003C (v01 GBT    GBTUACPI 06040000 LOHR 0000005A)
[    0.000000] ACPI: TCPA 7fec9da2 00032 (v01 GBT    GBTUACPI 06040000  TL  00000000)
[    0.000000] ACPI: TMOR 7fec9dd4 00026 (v01 GBT    GBTUACPI 06040000 PTL  00000003)
[    0.000000] ACPI: APIC 7fec9dfa 00068 (v01 GBT    GBTUACPI 06040000  LTP 00000000)
[    0.000000] ACPI: BOOT 7fec9e62 00028 (v01 GBT    GBTUACPI 06040000  LTP 00000001)
[    0.000000] ACPI: SLIC 7fec9e8a 00176 (v01 GBT    GBTUACPI 06040000  LTP 00000000)
[    0.000000] ACPI: SSDT 7fec4385 002DD (v01 SataRe SataAhci 00001000 INTL 20060707)
[    0.000000] ACPI: SSDT 7fec3762 0025F (v01  PmRef  Cpu0Tst 00003000 INTL 20060707)
[    0.000000] ACPI: SSDT 7fec36bc 000A6 (v01  PmRef  Cpu1Tst 00003000 INTL 20060707)
[    0.000000] ACPI: SSDT 7fec31d6 004E6 (v01  PmRef    CpuPm 00003000 INTL 20060707)
[    0.000000] ACPI: BIOS bug: multiple APIC/MADT found, using 0
[    0.000000] ACPI: If "acpi_apic_instance=2" works better, notify linux-acpi@vger.kernel.org
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 1158MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0007fec0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009b
[    0.000000]     0: 0x00000100 -> 0x0007fec0
[    0.000000] On node 0 totalpages: 523851
[    0.000000] free_area_init_node: node 0, pgdat c1784100, node_mem_map f577c200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3947 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2318 pages used for memmap
[    0.000000]   HighMem zone: 294324 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009b000 - 000000000009c000
[    0.000000] PM: Registered nosave memory: 000000000009c000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d2000
[    0.000000] PM: Registered nosave memory: 00000000000d2000 - 00000000000d4000
[    0.000000] PM: Registered nosave memory: 00000000000d4000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 80000000:60000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 13 pages/cpu @f5000000 s28800 r0 d24448 u2097152
[    0.000000] pcpu-alloc: s28800 r0 d24448 u2097152 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 1 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 519757
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-8-generic root=UUID=a4cbcb02-10ce-435e-8c17-1b8bd9220d6c ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] allocated 10479040 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0007fec0)
[    0.000000] Memory: 2045948k/2095872k available (5188k kernel code, 49456k reserved, 2540k data, 700k init, 1186568k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc178d000 - 0xc183c000   ( 700 kB)
[    0.000000]       .data : 0xc15112a1 - 0xc178c480   (2540 kB)
[    0.000000]       .text : 0xc1000000 - 0xc15112a1   (5188 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU-based detection of stalled CPUs is disabled.
[    0.000000] NR_IRQS:2304 nr_irqs:512 16
[    0.000000] CPU 0 irqstacks, hard=f4008000 soft=f400a000
[    0.000000] Extended CMOS year: 2000
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2194.560 MHz processor.
[    0.004003] Calibrating delay loop (skipped), value calculated using timer frequency.. 4389.12 BogoMIPS (lpj=8778240)
[    0.004008] pid_max: default: 32768 minimum: 301
[    0.004029] Security Framework initialized
[    0.004044] AppArmor: AppArmor initialized
[    0.004045] Yama: becoming mindful.
[    0.004098] Mount-cache hash table entries: 512
[    0.004227] Initializing cgroup subsys ns
[    0.004231] ns_cgroup deprecated: consider using the 'clone_children' flag without the ns_cgroup.
[    0.004234] Initializing cgroup subsys cpuacct
[    0.004239] Initializing cgroup subsys memory
[    0.004246] Initializing cgroup subsys devices
[    0.004249] Initializing cgroup subsys freezer
[    0.004251] Initializing cgroup subsys net_cls
[    0.004253] Initializing cgroup subsys blkio
[    0.004286] CPU: Physical Processor ID: 0
[    0.004288] CPU: Processor Core ID: 0
[    0.004291] mce: CPU supports 6 MCE banks
[    0.004298] CPU0: Thermal monitoring enabled (TM2)
[    0.004302] using mwait in idle threads.
[    0.006521] ACPI: Core revision 20110112
[    0.012015] ftrace: allocating 23640 entries in 47 pages
[    0.016049] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.016392] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.058515] CPU0: Intel(R) Core(TM)2 Duo CPU     T7500  @ 2.20GHz stepping 0a
[    0.060003] Performance Events: PEBS fmt0+, Core2 events, Intel PMU driver.
[    0.060003] PEBS disabled due to CPU errata.
[    0.060003] ... version:                2
[    0.060003] ... bit width:              40
[    0.060003] ... generic registers:      2
[    0.060003] ... value mask:             000000ffffffffff
[    0.060003] ... max period:             000000007fffffff
[    0.060003] ... fixed-purpose events:   3
[    0.060003] ... event mask:             0000000700000003
[    0.060003] CPU 1 irqstacks, hard=f40ca000 soft=f40cc000
[    0.060003] Booting Node   0, Processors  #1 Ok.
[    0.008000] Initializing CPU#1
[    0.148025] Brought up 2 CPUs
[    0.148028] Total of 2 processors activated (8778.09 BogoMIPS).
[    0.148707] devtmpfs: initialized
[    0.149159] print_constraints: dummy: 
[    0.149190] Time: 16:09:38  Date: 05/18/11
[    0.149227] NET: Registered protocol family 16
[    0.149254] Trying to unpack rootfs image as initramfs...
[    0.149350] EISA bus registered
[    0.149358] ACPI: bus type pci registered
[    0.149435] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.149438] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    0.149440] PCI: Using MMCONFIG for extended config space
[    0.149442] PCI: Using configuration type 1 for base access
[    0.164267] bio: create slab <bio-0> at 0
[    0.165689] ACPI: EC: Look up EC in DSDT
[    0.168404] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.169470] ACPI: SSDT 7fec4043 0027A (v01  PmRef  Cpu0Ist 00003000 INTL 20060707)
[    0.169837] ACPI: Dynamic OEM Table Load:
[    0.169840] ACPI: SSDT   (null) 0027A (v01  PmRef  Cpu0Ist 00003000 INTL 20060707)
[    0.169995] ACPI: SSDT 7fec39c1 005FD (v01  PmRef  Cpu0Cst 00003001 INTL 20060707)
[    0.170340] ACPI: Dynamic OEM Table Load:
[    0.170343] ACPI: SSDT   (null) 005FD (v01  PmRef  Cpu0Cst 00003001 INTL 20060707)
[    0.170610] ACPI: SSDT 7fec42bd 000C8 (v01  PmRef  Cpu1Ist 00003000 INTL 20060707)
[    0.170967] ACPI: Dynamic OEM Table Load:
[    0.170970] ACPI: SSDT   (null) 000C8 (v01  PmRef  Cpu1Ist 00003000 INTL 20060707)
[    0.171089] ACPI: SSDT 7fec3fbe 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20060707)
[    0.171436] ACPI: Dynamic OEM Table Load:
[    0.171439] ACPI: SSDT   (null) 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20060707)
[    0.171756] ACPI: Interpreter enabled
[    0.171764] ACPI: (supports S0 S3 S4 S5)
[    0.171784] ACPI: Using IOAPIC for interrupt routing
[    0.177829] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
[    0.179119] ACPI: ACPI Dock Station Driver: 1 docks/bays found
[    0.179119] HEST: Table not found.
[    0.179119] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.179820] ACPI Error: [CDW1] Namespace lookup failure, AE_NOT_FOUND (20110112/psargs-359)
[    0.179820] ACPI Error: Method parse/execution failed [\_SB_.PCI0._OSC] (Node f40250d8), AE_NOT_FOUND (20110112/psparse-536)
[    0.179820] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.180431] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    0.180435] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    0.180437] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.180441] pci_root PNP0A08:00: host bridge window [mem 0x000d4000-0x000d7fff]
[    0.180443] pci_root PNP0A08:00: host bridge window [mem 0x000d8000-0x000dbfff]
[    0.180446] pci_root PNP0A08:00: host bridge window [mem 0x000dc000-0x000dffff]
[    0.180449] pci_root PNP0A08:00: host bridge window [mem 0x80000000-0xfebfffff]
[    0.180452] pci_root PNP0A08:00: host bridge window [mem 0xfed40000-0xfed44fff]
[    0.180467] pci 0000:00:00.0: [8086:2a00] type 0 class 0x000600
[    0.180519] pci 0000:00:01.0: [8086:2a01] type 1 class 0x000604
[    0.180559] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.180563] pci 0000:00:01.0: PME# disabled
[    0.180619] pci 0000:00:1a.0: [8086:2834] type 0 class 0x000c03
[    0.180675] pci 0000:00:1a.0: reg 20: [io  0x1800-0x181f]
[    0.180714] pci 0000:00:1a.1: [8086:2835] type 0 class 0x000c03
[    0.180770] pci 0000:00:1a.1: reg 20: [io  0x1820-0x183f]
[    0.180824] pci 0000:00:1a.7: [8086:283a] type 0 class 0x000c03
[    0.180848] pci 0000:00:1a.7: reg 10: [mem 0xf0c04800-0xf0c04bff]
[    0.180944] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.180950] pci 0000:00:1a.7: PME# disabled
[    0.180980] pci 0000:00:1b.0: [8086:284b] type 0 class 0x000403
[    0.181005] pci 0000:00:1b.0: reg 10: [mem 0xf0c00000-0xf0c03fff 64bit]
[    0.181095] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.181100] pci 0000:00:1b.0: PME# disabled
[    0.181128] pci 0000:00:1c.0: [8086:283f] type 1 class 0x000604
[    0.181220] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.181226] pci 0000:00:1c.0: PME# disabled
[    0.181257] pci 0000:00:1c.1: [8086:2841] type 1 class 0x000604
[    0.181343] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.181347] pci 0000:00:1c.1: PME# disabled
[    0.181380] pci 0000:00:1c.2: [8086:2843] type 1 class 0x000604
[    0.181475] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.181480] pci 0000:00:1c.2: PME# disabled
[    0.181517] pci 0000:00:1c.5: [8086:2849] type 1 class 0x000604
[    0.181610] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    0.181615] pci 0000:00:1c.5: PME# disabled
[    0.181647] pci 0000:00:1d.0: [8086:2830] type 0 class 0x000c03
[    0.181701] pci 0000:00:1d.0: reg 20: [io  0x1840-0x185f]
[    0.181742] pci 0000:00:1d.1: [8086:2831] type 0 class 0x000c03
[    0.181811] pci 0000:00:1d.1: reg 20: [io  0x1860-0x187f]
[    0.181860] pci 0000:00:1d.2: [8086:2832] type 0 class 0x000c03
[    0.181927] pci 0000:00:1d.2: reg 20: [io  0x1880-0x189f]
[    0.181986] pci 0000:00:1d.7: [8086:2836] type 0 class 0x000c03
[    0.182012] pci 0000:00:1d.7: reg 10: [mem 0xf0c04c00-0xf0c04fff]
[    0.182111] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.182117] pci 0000:00:1d.7: PME# disabled
[    0.182141] pci 0000:00:1e.0: [8086:2448] type 1 class 0x000604
[    0.182233] pci 0000:00:1f.0: [8086:2815] type 0 class 0x000601
[    0.182342] pci 0000:00:1f.0: quirk: [io  0x1000-0x107f] claimed by ICH6 ACPI/GPIO/TCO
[    0.182348] pci 0000:00:1f.0: quirk: [io  0x1180-0x11bf] claimed by ICH6 GPIO
[    0.182354] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 2 PIO at 1640 (mask 007f)
[    0.182359] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 3 PIO at 0380 (mask 0007)
[    0.182363] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 4 PIO at 0068 (mask 0007)
[    0.182403] pci 0000:00:1f.1: [8086:2850] type 0 class 0x000101
[    0.182421] pci 0000:00:1f.1: reg 10: [io  0x0000-0x0007]
[    0.182435] pci 0000:00:1f.1: reg 14: [io  0x0000-0x0003]
[    0.182448] pci 0000:00:1f.1: reg 18: [io  0x0000-0x0007]
[    0.182461] pci 0000:00:1f.1: reg 1c: [io  0x0000-0x0003]
[    0.182473] pci 0000:00:1f.1: reg 20: [io  0x18a0-0x18af]
[    0.182526] pci 0000:00:1f.2: [8086:2829] type 0 class 0x000106
[    0.182555] pci 0000:00:1f.2: reg 10: [io  0x18d8-0x18df]
[    0.182567] pci 0000:00:1f.2: reg 14: [io  0x18cc-0x18cf]
[    0.182580] pci 0000:00:1f.2: reg 18: [io  0x18d0-0x18d7]
[    0.182593] pci 0000:00:1f.2: reg 1c: [io  0x18c8-0x18cb]
[    0.182605] pci 0000:00:1f.2: reg 20: [io  0x18e0-0x18ff]
[    0.182617] pci 0000:00:1f.2: reg 24: [mem 0xf0c04000-0xf0c047ff]
[    0.182665] pci 0000:00:1f.2: PME# supported from D3hot
[    0.182670] pci 0000:00:1f.2: PME# disabled
[    0.182693] pci 0000:00:1f.3: [8086:283e] type 0 class 0x000c05
[    0.182711] pci 0000:00:1f.3: reg 10: [mem 0x00000000-0x000000ff]
[    0.182756] pci 0000:00:1f.3: reg 20: [io  0x1c00-0x1c1f]
[    0.182840] pci 0000:01:00.0: [10de:0427] type 0 class 0x000300
[    0.182853] pci 0000:01:00.0: reg 10: [mem 0xce000000-0xceffffff]
[    0.182866] pci 0000:01:00.0: reg 14: [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.182879] pci 0000:01:00.0: reg 1c: [mem 0xcc000000-0xcdffffff 64bit]
[    0.182888] pci 0000:01:00.0: reg 24: [io  0x2000-0x207f]
[    0.182898] pci 0000:01:00.0: reg 30: [mem 0x00000000-0x0001ffff pref]
[    0.188025] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.188029] pci 0000:00:01.0:   bridge window [io  0x2000-0x2fff]
[    0.188033] pci 0000:00:01.0:   bridge window [mem 0xcc000000-0xceffffff]
[    0.188038] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.188172] pci 0000:02:00.0: [8086:4229] type 0 class 0x000280
[    0.188222] pci 0000:02:00.0: reg 10: [mem 0xf0700000-0xf0701fff 64bit]
[    0.188392] pci 0000:02:00.0: PME# supported from D0 D3hot D3cold
[    0.188407] pci 0000:02:00.0: PME# disabled
[    0.196056] pci 0000:00:1c.0: PCI bridge to [bus 02-03]
[    0.196062] pci 0000:00:1c.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.196068] pci 0000:00:1c.0:   bridge window [mem 0xf0700000-0xf07fffff]
[    0.196077] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.196171] pci 0000:04:00.0: [11ab:4363] type 0 class 0x000200
[    0.196204] pci 0000:04:00.0: reg 10: [mem 0xf0600000-0xf0603fff 64bit]
[    0.196222] pci 0000:04:00.0: reg 18: [io  0x3000-0x30ff]
[    0.196280] pci 0000:04:00.0: reg 30: [mem 0x00000000-0x0001ffff pref]
[    0.196333] pci 0000:04:00.0: supports D1 D2
[    0.196335] pci 0000:04:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.196341] pci 0000:04:00.0: PME# disabled
[    0.204031] pci 0000:00:1c.1: PCI bridge to [bus 04-05]
[    0.204037] pci 0000:00:1c.1:   bridge window [io  0x3000-0x3fff]
[    0.204042] pci 0000:00:1c.1:   bridge window [mem 0xf0600000-0xf06fffff]
[    0.204050] pci 0000:00:1c.1:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.204145] pci 0000:06:00.0: [8086:444e] type 0 class 0x000580
[    0.204173] pci 0000:06:00.0: reg 10: [mem 0xf0900000-0xf09003ff]
[    0.204210] pci 0000:06:00.0: reg 18: [io  0x4000-0x407f]
[    0.204281] pci 0000:06:00.0: reg 30: [mem 0x00000000-0x0000ffff pref]
[    0.212033] pci 0000:00:1c.2: PCI bridge to [bus 06-07]
[    0.212039] pci 0000:00:1c.2:   bridge window [io  0x4000-0x4fff]
[    0.212044] pci 0000:00:1c.2:   bridge window [mem 0xf0900000-0xf09fffff]
[    0.212052] pci 0000:00:1c.2:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.212121] pci 0000:00:1c.5: PCI bridge to [bus 08-09]
[    0.212127] pci 0000:00:1c.5:   bridge window [io  0x5000-0x5fff]
[    0.212132] pci 0000:00:1c.5:   bridge window [mem 0xf0400000-0xf05fffff]
[    0.212140] pci 0000:00:1c.5:   bridge window [mem 0xf0000000-0xf03fffff 64bit pref]
[    0.212203] pci 0000:0b:09.0: [104c:8039] type 2 class 0x000607
[    0.212229] pci 0000:0b:09.0: reg 10: [mem 0xf0804000-0xf0804fff]
[    0.212258] pci 0000:0b:09.0: supports D1 D2
[    0.212260] pci 0000:0b:09.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.212266] pci 0000:0b:09.0: PME# disabled
[    0.212291] pci 0000:0b:09.1: [104c:803a] type 0 class 0x000c00
[    0.212317] pci 0000:0b:09.1: reg 10: [mem 0xf0806000-0xf08067ff]
[    0.212331] pci 0000:0b:09.1: reg 14: [mem 0xf0800000-0xf0803fff]
[    0.212421] pci 0000:0b:09.1: supports D1 D2
[    0.212423] pci 0000:0b:09.1: PME# supported from D0 D1 D2 D3hot
[    0.212429] pci 0000:0b:09.1: PME# disabled
[    0.212453] pci 0000:0b:09.2: [104c:803b] type 0 class 0x000180
[    0.212479] pci 0000:0b:09.2: reg 10: [mem 0xf0805000-0xf0805fff]
[    0.212576] pci 0000:0b:09.2: supports D1 D2
[    0.212578] pci 0000:0b:09.2: PME# supported from D0 D1 D2 D3hot
[    0.212583] pci 0000:0b:09.2: PME# disabled
[    0.212607] pci 0000:0b:09.3: [104c:803c] type 0 class 0x000805
[    0.212633] pci 0000:0b:09.3: reg 10: [mem 0xf0806800-0xf08068ff]
[    0.212732] pci 0000:0b:09.3: supports D1 D2
[    0.212735] pci 0000:0b:09.3: PME# supported from D0 D1 D2 D3hot
[    0.212740] pci 0000:0b:09.3: PME# disabled
[    0.212796] pci 0000:00:1e.0: PCI bridge to [bus 0b-0c] (subtractive decode)
[    0.212801] pci 0000:00:1e.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.212807] pci 0000:00:1e.0:   bridge window [mem 0xf0800000-0xf08fffff]
[    0.212816] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.212819] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.212821] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.212824] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.212827] pci 0000:00:1e.0:   bridge window [mem 0x000d4000-0x000d7fff] (subtractive decode)
[    0.212830] pci 0000:00:1e.0:   bridge window [mem 0x000d8000-0x000dbfff] (subtractive decode)
[    0.212832] pci 0000:00:1e.0:   bridge window [mem 0x000dc000-0x000dffff] (subtractive decode)
[    0.212835] pci 0000:00:1e.0:   bridge window [mem 0x80000000-0xfebfffff] (subtractive decode)
[    0.212838] pci 0000:00:1e.0:   bridge window [mem 0xfed40000-0xfed44fff] (subtractive decode)
[    0.212891] pci_bus 0000:0c: [bus 0c-0f] partially hidden behind transparent bridge 0000:0b [bus 0b-0c]
[    0.212927] pci_bus 0000:00: on NUMA node 0
[    0.212935] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.213155] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEGP._PRT]
[    0.213224] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.213284] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    0.213343] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[    0.213402] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP06._PRT]
[    0.213484] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[    0.213570] ACPI Error: [CDW1] Namespace lookup failure, AE_NOT_FOUND (20110112/psargs-359)
[    0.213577] ACPI Error: Method parse/execution failed [\_SB_.PCI0._OSC] (Node f40250d8), AE_NOT_FOUND (20110112/psparse-536)
[    0.213589]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.213609] ACPI Error: [CDW1] Namespace lookup failure, AE_NOT_FOUND (20110112/psargs-359)
[    0.213614] ACPI Error: Method parse/execution failed [\_SB_.PCI0._OSC] (Node f40250d8), AE_NOT_FOUND (20110112/psparse-536)
[    0.220323] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 *5 6 7 10 12 14 15)
[    0.220381] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.220437] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 *7 10 12 14 15)
[    0.220493] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.220548] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    0.220603] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    0.220658] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    0.220713] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.220846] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.220853] vgaarb: loaded
[    0.221075] SCSI subsystem initialized
[    0.221143] libata version 3.00 loaded.
[    0.221196] usbcore: registered new interface driver usbfs
[    0.221209] usbcore: registered new interface driver hub
[    0.221238] usbcore: registered new device driver usb
[    0.221357] wmi: Mapper loaded
[    0.221359] PCI: Using ACPI for IRQ routing
[    0.221362] PCI: pci_cache_line_size set to 64 bytes
[    0.221547] reserve RAM buffer: 000000000009b800 - 000000000009ffff 
[    0.221551] reserve RAM buffer: 000000007fec0000 - 000000007fffffff 
[    0.221662] NetLabel: Initializing
[    0.221664] NetLabel:  domain hash size = 128
[    0.221666] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.221677] NetLabel:  unlabeled traffic allowed by default
[    0.221713] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.221719] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.221724] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.228066] Switching to clocksource hpet
[    0.231695] Switched to NOHz mode on CPU #0
[    0.231794] Switched to NOHz mode on CPU #1
[    0.236425] AppArmor: AppArmor Filesystem Enabled
[    0.236457] pnp: PnP ACPI init
[    0.236481] ACPI: bus type pnp registered
[    0.237093] pnp 00:00: [bus 00-ff]
[    0.237096] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.237099] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.237101] pnp 00:00: [io  0x0d00-0xffff window]
[    0.237104] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.237106] pnp 00:00: [mem 0x000c0000-0x000c3fff window]
[    0.237109] pnp 00:00: [mem 0x000c4000-0x000c7fff window]
[    0.237111] pnp 00:00: [mem 0x000c8000-0x000cbfff window]
[    0.237114] pnp 00:00: [mem 0x000cc000-0x000cffff window]
[    0.237116] pnp 00:00: [mem 0x000d0000-0x000d3fff window]
[    0.237119] pnp 00:00: [mem 0x000d4000-0x000d7fff window]
[    0.237121] pnp 00:00: [mem 0x000d8000-0x000dbfff window]
[    0.237124] pnp 00:00: [mem 0x000dc000-0x000dffff window]
[    0.237126] pnp 00:00: [mem 0x000e0000-0x000e3fff window]
[    0.237128] pnp 00:00: [mem 0x000e4000-0x000e7fff window]
[    0.237131] pnp 00:00: [mem 0x000e8000-0x000ebfff window]
[    0.237133] pnp 00:00: [mem 0x000ec000-0x000effff window]
[    0.237139] pnp 00:00: [mem 0x000f0000-0x000fffff window]
[    0.237141] pnp 00:00: [mem 0x80000000-0xfebfffff window]
[    0.237144] pnp 00:00: [mem 0xfed40000-0xfed44fff window]
[    0.237228] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    0.237335] pnp 00:01: [mem 0xfed1c000-0xfed1ffff]
[    0.237338] pnp 00:01: [mem 0xfed14000-0xfed17fff]
[    0.237340] pnp 00:01: [mem 0xfed18000-0xfed18fff]
[    0.237343] pnp 00:01: [mem 0xfed19000-0xfed19fff]
[    0.237345] pnp 00:01: [mem 0xe0000000-0xefffffff]
[    0.237347] pnp 00:01: [mem 0xfed20000-0xfed3ffff]
[    0.237350] pnp 00:01: [mem 0xfed40000-0xfed3ffff disabled]
[    0.237352] pnp 00:01: [mem 0xfed45000-0xfed8ffff]
[    0.237425] system 00:01: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.237429] system 00:01: [mem 0xfed14000-0xfed17fff] has been reserved
[    0.237432] system 00:01: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.237435] system 00:01: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.237438] system 00:01: [mem 0xe0000000-0xefffffff] has been reserved
[    0.237440] system 00:01: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.237443] system 00:01: [mem 0xfed45000-0xfed8ffff] has been reserved
[    0.237447] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.238208] pnp 00:02: [io  0x0000-0x001f]
[    0.238211] pnp 00:02: [io  0x0081-0x0091]
[    0.238213] pnp 00:02: [io  0x0093-0x009f]
[    0.238215] pnp 00:02: [io  0x00c0-0x00df]
[    0.238218] pnp 00:02: [dma 4]
[    0.238277] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.238288] pnp 00:03: [mem 0xff000000-0xffffffff]
[    0.238340] pnp 00:03: Plug and Play ACPI device, IDs INT0800 (active)
[    0.238413] pnp 00:04: [mem 0xfed00000-0xfed003ff]
[    0.238495] system 00:04: [mem 0xfed00000-0xfed003ff] has been reserved
[    0.238499] system 00:04: Plug and Play ACPI device, IDs PNP0103 PNP0c01 (active)
[    0.238512] pnp 00:05: [io  0x00f0]
[    0.238526] pnp 00:05: [irq 13]
[    0.238578] pnp 00:05: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.238591] pnp 00:06: [io  0x002e-0x002f]
[    0.238593] pnp 00:06: [io  0x0061]
[    0.238595] pnp 00:06: [io  0x0063]
[    0.238597] pnp 00:06: [io  0x0065]
[    0.238599] pnp 00:06: [io  0x0067]
[    0.238601] pnp 00:06: [io  0x0070]
[    0.238603] pnp 00:06: [io  0x0080]
[    0.238605] pnp 00:06: [io  0x0092]
[    0.238607] pnp 00:06: [io  0x00b2-0x00b3]
[    0.238609] pnp 00:06: [io  0x0068-0x006f]
[    0.238611] pnp 00:06: [io  0x0380-0x0387]
[    0.238614] pnp 00:06: [io  0x0680-0x069f]
[    0.238616] pnp 00:06: [io  0x0800-0x080f]
[    0.238618] pnp 00:06: [io  0x1000-0x107f]
[    0.238620] pnp 00:06: [io  0x1180-0x11bf]
[    0.238622] pnp 00:06: [io  0x1640-0x164f]
[    0.238624] pnp 00:06: [io  0xfe00]
[    0.238720] system 00:06: [io  0x0380-0x0387] has been reserved
[    0.238723] system 00:06: [io  0x0680-0x069f] has been reserved
[    0.238726] system 00:06: [io  0x0800-0x080f] has been reserved
[    0.238729] system 00:06: [io  0x1000-0x107f] has been reserved
[    0.238731] system 00:06: [io  0x1180-0x11bf] has been reserved
[    0.238734] system 00:06: [io  0x1640-0x164f] has been reserved
[    0.238737] system 00:06: [io  0xfe00] has been reserved
[    0.238741] system 00:06: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.238768] pnp 00:07: [io  0x06a0-0x06af]
[    0.238770] pnp 00:07: [io  0x06b0-0x06ff]
[    0.238846] system 00:07: [io  0x06a0-0x06af] has been reserved
[    0.238849] system 00:07: [io  0x06b0-0x06ff] has been reserved
[    0.238853] system 00:07: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.238863] pnp 00:08: [io  0x0070-0x0077]
[    0.238869] pnp 00:08: [irq 8]
[    0.238920] pnp 00:08: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.238957] pnp 00:09: [mem 0xfed40000-0xfed44fff]
[    0.238959] pnp 00:09: [io  0x167e-0x167f]
[    0.238962] pnp 00:09: [io  0x1670-0x167b]
[    0.238967] pnp 00:09: [irq 3]
[    0.238972] pnp 00:09: [irq 5]
[    0.238977] pnp 00:09: [irq 7]
[    0.238979] pnp 00:09: IRQ 9 override to level, high
[    0.238981] pnp 00:09: [irq 9]
[    0.238986] pnp 00:09: [irq 10]
[    0.238991] pnp 00:09: [irq 11]
[    0.238993] pnp 00:09: [irq 13]
[    0.238997] pnp 00:09: [irq 15]
[    0.239051] pnp 00:09: Plug and Play ACPI device, IDs IFX0102 PNP0c31 (active)
[    0.239062] pnp 00:0a: [io  0x0060]
[    0.239064] pnp 00:0a: [io  0x0064]
[    0.239070] pnp 00:0a: [irq 1]
[    0.239124] pnp 00:0a: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.239138] pnp 00:0b: [irq 12]
[    0.239195] pnp 00:0b: Plug and Play ACPI device, IDs SYN100c SYN1000 SYN1002 PNP0f13 (active)
[    0.239221] pnp: PnP ACPI: found 12 devices
[    0.239223] ACPI: ACPI bus type pnp unregistered
[    0.239227] PnPBIOS: Disabled by ACPI PNP
[    0.275828] pci 0000:00:1e.0: BAR 15: assigned [mem 0x80000000-0x83ffffff pref]
[    0.275833] pci 0000:00:1c.0: BAR 15: assigned [mem 0x84000000-0x841fffff 64bit pref]
[    0.275838] pci 0000:00:1c.1: BAR 15: assigned [mem 0x84200000-0x843fffff pref]
[    0.275842] pci 0000:00:1c.2: BAR 15: assigned [mem 0x84400000-0x845fffff pref]
[    0.275846] pci 0000:00:1c.0: BAR 13: assigned [io  0x6000-0x6fff]
[    0.275850] pci 0000:00:1e.0: BAR 13: assigned [io  0x7000-0x7fff]
[    0.275854] pci 0000:00:1f.3: BAR 0: assigned [mem 0x84600000-0x846000ff]
[    0.275860] pci 0000:00:1f.3: BAR 0: set to [mem 0x84600000-0x846000ff] (PCI address [0x84600000-0x846000ff])
[    0.275864] pci 0000:01:00.0: BAR 6: can't assign mem pref (size 0x20000)
[    0.275867] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.275870] pci 0000:00:01.0:   bridge window [io  0x2000-0x2fff]
[    0.275875] pci 0000:00:01.0:   bridge window [mem 0xcc000000-0xceffffff]
[    0.275879] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.275884] pci 0000:00:1c.0: PCI bridge to [bus 02-03]
[    0.275888] pci 0000:00:1c.0:   bridge window [io  0x6000-0x6fff]
[    0.275895] pci 0000:00:1c.0:   bridge window [mem 0xf0700000-0xf07fffff]
[    0.275900] pci 0000:00:1c.0:   bridge window [mem 0x84000000-0x841fffff 64bit pref]
[    0.275908] pci 0000:04:00.0: BAR 6: assigned [mem 0x84200000-0x8421ffff pref]
[    0.275911] pci 0000:00:1c.1: PCI bridge to [bus 04-05]
[    0.275914] pci 0000:00:1c.1:   bridge window [io  0x3000-0x3fff]
[    0.275921] pci 0000:00:1c.1:   bridge window [mem 0xf0600000-0xf06fffff]
[    0.275926] pci 0000:00:1c.1:   bridge window [mem 0x84200000-0x843fffff pref]
[    0.275935] pci 0000:06:00.0: BAR 6: assigned [mem 0x84400000-0x8440ffff pref]
[    0.275937] pci 0000:00:1c.2: PCI bridge to [bus 06-07]
[    0.275941] pci 0000:00:1c.2:   bridge window [io  0x4000-0x4fff]
[    0.275947] pci 0000:00:1c.2:   bridge window [mem 0xf0900000-0xf09fffff]
[    0.275952] pci 0000:00:1c.2:   bridge window [mem 0x84400000-0x845fffff pref]
[    0.275961] pci 0000:00:1c.5: PCI bridge to [bus 08-09]
[    0.275965] pci 0000:00:1c.5:   bridge window [io  0x5000-0x5fff]
[    0.275972] pci 0000:00:1c.5:   bridge window [mem 0xf0400000-0xf05fffff]
[    0.275977] pci 0000:00:1c.5:   bridge window [mem 0xf0000000-0xf03fffff 64bit pref]
[    0.275987] pci 0000:0b:09.0: BAR 15: assigned [mem 0x80000000-0x83ffffff pref]
[    0.275992] pci 0000:0b:09.0: BAR 16: assigned [mem 0x88000000-0x8bffffff]
[    0.275994] pci 0000:0b:09.0: BAR 13: assigned [io  0x7000-0x70ff]
[    0.276014] pci 0000:0b:09.0: BAR 14: assigned [io  0x7400-0x74ff]
[    0.276017] pci 0000:0b:09.0: CardBus bridge to [bus 0c-0f]
[    0.276019] pci 0000:0b:09.0:   bridge window [io  0x7000-0x70ff]
[    0.276025] pci 0000:0b:09.0:   bridge window [io  0x7400-0x74ff]
[    0.276031] pci 0000:0b:09.0:   bridge window [mem 0x80000000-0x83ffffff pref]
[    0.276036] pci 0000:0b:09.0:   bridge window [mem 0x88000000-0x8bffffff]
[    0.276042] pci 0000:00:1e.0: PCI bridge to [bus 0b-0c]
[    0.276045] pci 0000:00:1e.0:   bridge window [io  0x7000-0x7fff]
[    0.276051] pci 0000:00:1e.0:   bridge window [mem 0xf0800000-0xf08fffff]
[    0.276056] pci 0000:00:1e.0:   bridge window [mem 0x80000000-0x83ffffff pref]
[    0.276084] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.276089] pci 0000:00:01.0: setting latency timer to 64
[    0.276100] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.276105] pci 0000:00:1c.0: setting latency timer to 64
[    0.276113] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.276117] pci 0000:00:1c.1: setting latency timer to 64
[    0.276128] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.276133] pci 0000:00:1c.2: setting latency timer to 64
[    0.276141] pci 0000:00:1c.5: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.276146] pci 0000:00:1c.5: setting latency timer to 64
[    0.276156] pci 0000:00:1e.0: setting latency timer to 64
[    0.276168] pci 0000:0b:09.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.276175] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.276177] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.276180] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.276182] pci_bus 0000:00: resource 7 [mem 0x000d4000-0x000d7fff]
[    0.276184] pci_bus 0000:00: resource 8 [mem 0x000d8000-0x000dbfff]
[    0.276187] pci_bus 0000:00: resource 9 [mem 0x000dc000-0x000dffff]
[    0.276189] pci_bus 0000:00: resource 10 [mem 0x80000000-0xfebfffff]
[    0.276192] pci_bus 0000:00: resource 11 [mem 0xfed40000-0xfed44fff]
[    0.276194] pci_bus 0000:01: resource 0 [io  0x2000-0x2fff]
[    0.276197] pci_bus 0000:01: resource 1 [mem 0xcc000000-0xceffffff]
[    0.276199] pci_bus 0000:01: resource 2 [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.276202] pci_bus 0000:02: resource 0 [io  0x6000-0x6fff]
[    0.276204] pci_bus 0000:02: resource 1 [mem 0xf0700000-0xf07fffff]
[    0.276207] pci_bus 0000:02: resource 2 [mem 0x84000000-0x841fffff 64bit pref]
[    0.276210] pci_bus 0000:04: resource 0 [io  0x3000-0x3fff]
[    0.276212] pci_bus 0000:04: resource 1 [mem 0xf0600000-0xf06fffff]
[    0.276215] pci_bus 0000:04: resource 2 [mem 0x84200000-0x843fffff pref]
[    0.276217] pci_bus 0000:06: resource 0 [io  0x4000-0x4fff]
[    0.276220] pci_bus 0000:06: resource 1 [mem 0xf0900000-0xf09fffff]
[    0.276222] pci_bus 0000:06: resource 2 [mem 0x84400000-0x845fffff pref]
[    0.276225] pci_bus 0000:08: resource 0 [io  0x5000-0x5fff]
[    0.276227] pci_bus 0000:08: resource 1 [mem 0xf0400000-0xf05fffff]
[    0.276230] pci_bus 0000:08: resource 2 [mem 0xf0000000-0xf03fffff 64bit pref]
[    0.276233] pci_bus 0000:0b: resource 0 [io  0x7000-0x7fff]
[    0.276235] pci_bus 0000:0b: resource 1 [mem 0xf0800000-0xf08fffff]
[    0.276238] pci_bus 0000:0b: resource 2 [mem 0x80000000-0x83ffffff pref]
[    0.276240] pci_bus 0000:0b: resource 4 [io  0x0000-0x0cf7]
[    0.276242] pci_bus 0000:0b: resource 5 [io  0x0d00-0xffff]
[    0.276245] pci_bus 0000:0b: resource 6 [mem 0x000a0000-0x000bffff]
[    0.276247] pci_bus 0000:0b: resource 7 [mem 0x000d4000-0x000d7fff]
[    0.276250] pci_bus 0000:0b: resource 8 [mem 0x000d8000-0x000dbfff]
[    0.276252] pci_bus 0000:0b: resource 9 [mem 0x000dc000-0x000dffff]
[    0.276255] pci_bus 0000:0b: resource 10 [mem 0x80000000-0xfebfffff]
[    0.276257] pci_bus 0000:0b: resource 11 [mem 0xfed40000-0xfed44fff]
[    0.276260] pci_bus 0000:0c: resource 0 [io  0x7000-0x70ff]
[    0.276262] pci_bus 0000:0c: resource 1 [io  0x7400-0x74ff]
[    0.276265] pci_bus 0000:0c: resource 2 [mem 0x80000000-0x83ffffff pref]
[    0.276267] pci_bus 0000:0c: resource 3 [mem 0x88000000-0x8bffffff]
[    0.276312] NET: Registered protocol family 2
[    0.276386] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.276652] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.277125] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.277355] TCP: Hash tables configured (established 131072 bind 65536)
[    0.277358] TCP reno registered
[    0.277361] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.277369] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.277452] NET: Registered protocol family 1
[    0.277644] pci 0000:01:00.0: Boot video device
[    0.277695] PCI: CLS 64 bytes, default 64
[    0.277721] Simple Boot Flag at 0x36 set to 0x1
[    0.277936] cpufreq-nforce2: No nForce2 chipset.
[    0.278076] audit: initializing netlink socket (disabled)
[    0.278086] type=2000 audit(1305734978.272:1): initialized
[    0.287472] highmem bounce pool size: 64 pages
[    0.287478] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.289412] VFS: Disk quotas dquot_6.5.2
[    0.289476] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.290173] fuse init (API version 7.16)
[    0.290273] msgmni has been set to 1678
[    0.290516] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.290541] io scheduler noop registered
[    0.290544] io scheduler deadline registered
[    0.290559] io scheduler cfq registered (default)
[    0.290698] pcieport 0000:00:01.0: setting latency timer to 64
[    0.290737] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
[    0.290793] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.290851] pcieport 0000:00:1c.0: irq 41 for MSI/MSI-X
[    0.290937] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.290995] pcieport 0000:00:1c.1: irq 42 for MSI/MSI-X
[    0.291083] pcieport 0000:00:1c.2: setting latency timer to 64
[    0.291141] pcieport 0000:00:1c.2: irq 43 for MSI/MSI-X
[    0.291226] pcieport 0000:00:1c.5: setting latency timer to 64
[    0.291284] pcieport 0000:00:1c.5: irq 44 for MSI/MSI-X
[    0.291395] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.291422] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.291504] intel_idle: MWAIT substates: 0x22220
[    0.291506] intel_idle: does not run on family 6 model 15
[    0.291824] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.292132] ACPI: AC Adapter [ACAD] (on-line)
[    0.292223] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    0.292458] ACPI: Lid Switch [LID]
[    0.292507] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.292512] ACPI: Power Button [PWRB]
[    0.292560] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    0.292564] ACPI: Sleep Button [SLPB]
[    0.292627] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    0.292631] ACPI: Power Button [PWRF]
[    0.292827] ACPI: acpi_idle registered with cpuidle
[    0.296251] Monitor-Mwait will be used to enter C-1 state
[    0.304014] Monitor-Mwait will be used to enter C-2 state
[    0.304314] Monitor-Mwait will be used to enter C-3 state
[    0.304323] Marking TSC unstable due to TSC halts in idle
[    0.309793] thermal LNXTHERM:00: registered as thermal_zone0
[    0.309796] ACPI: Thermal Zone [THR1] (55 C)
[    0.309817] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.309884] ERST: Table is not found!
[    0.309967] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.310177] isapnp: Scanning for PnP cards...
[    0.334552] ACPI: Battery Slot [BAT0] (battery present)
[    0.437497] Freeing initrd memory: 12520k freed
[    0.664148] isapnp: No Plug & Play device found
[    0.696630] Linux agpgart interface v0.103
[    0.698222] brd: module loaded
[    0.698875] loop: module loaded
[    0.698971] i2c-core: driver [adp5520] using legacy suspend method
[    0.698973] i2c-core: driver [adp5520] using legacy resume method
[    0.699085] ata_piix 0000:00:1f.1: version 2.13
[    0.699110] ata_piix 0000:00:1f.1: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.699158] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.699541] scsi0 : ata_piix
[    0.699647] scsi1 : ata_piix
[    0.700109] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x18a0 irq 14
[    0.700112] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x18a8 irq 15
[    0.700281] ata2: port disabled. ignoring.
[    0.700524] Fixed MDIO Bus: probed
[    0.700567] PPP generic driver version 2.4.2
[    0.700611] tun: Universal TUN/TAP device driver, 1.6
[    0.700613] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.700709] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.700729] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.700742] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    0.700746] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    0.700790] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    0.700847] ehci_hcd 0000:00:1a.7: debug port 1
[    0.704732] ehci_hcd 0000:00:1a.7: cache line size of 64 is not supported
[    0.704749] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xf0c04800
[    0.720018] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    0.720144] hub 1-0:1.0: USB hub found
[    0.720149] hub 1-0:1.0: 4 ports detected
[    0.720241] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.720252] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.720256] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.720297] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    0.720352] ehci_hcd 0000:00:1d.7: debug port 1
[    0.724233] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
[    0.724248] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xf0c04c00
[    0.740017] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.740148] hub 2-0:1.0: USB hub found
[    0.740152] hub 2-0:1.0: 6 ports detected
[    0.740241] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.740256] uhci_hcd: USB Universal Host Controller Interface driver
[    0.740279] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.740286] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    0.740290] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    0.740334] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    0.740389] uhci_hcd 0000:00:1a.0: irq 16, io base 0x00001800
[    0.740520] hub 3-0:1.0: USB hub found
[    0.740525] hub 3-0:1.0: 2 ports detected
[    0.740609] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.740617] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    0.740621] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    0.740664] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    0.740720] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00001820
[    0.740851] hub 4-0:1.0: USB hub found
[    0.740855] hub 4-0:1.0: 2 ports detected
[    0.740934] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.740941] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.740945] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.740984] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    0.744050] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001840
[    0.744187] hub 5-0:1.0: USB hub found
[    0.744191] hub 5-0:1.0: 2 ports detected
[    0.744273] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.744280] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.744284] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.744322] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    0.744375] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001860
[    0.744510] hub 6-0:1.0: USB hub found
[    0.744514] hub 6-0:1.0: 2 ports detected
[    0.744595] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.744604] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.744607] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.744645] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    0.744694] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001880
[    0.744830] hub 7-0:1.0: USB hub found
[    0.744834] hub 7-0:1.0: 2 ports detected
[    0.744984] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.763943] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.763949] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.764090] mousedev: PS/2 mouse device common for all mice
[    0.765274] rtc_cmos 00:08: RTC can wake from S4
[    0.765337] rtc_cmos 00:08: rtc core: registered rtc_cmos as rtc0
[    0.765372] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    0.765453] device-mapper: uevent: version 1.0.3
[    0.765542] device-mapper: ioctl: 4.19.1-ioctl (2011-01-07) initialised: dm-devel@redhat.com
[    0.765612] device-mapper: multipath: version 1.2.0 loaded
[    0.765615] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.765691] EISA: Probing bus 0 at eisa.0
[    0.765694] EISA: Cannot allocate resource for mainboard
[    0.765696] Cannot allocate resource for EISA slot 1
[    0.765698] Cannot allocate resource for EISA slot 2
[    0.765700] Cannot allocate resource for EISA slot 3
[    0.765702] Cannot allocate resource for EISA slot 4
[    0.765704] Cannot allocate resource for EISA slot 5
[    0.765705] Cannot allocate resource for EISA slot 6
[    0.765707] Cannot allocate resource for EISA slot 7
[    0.765709] Cannot allocate resource for EISA slot 8
[    0.765711] EISA: Detected 0 cards.
[    0.765832] cpuidle: using governor ladder
[    0.765938] cpuidle: using governor menu
[    0.766244] TCP cubic registered
[    0.766384] NET: Registered protocol family 10
[    0.767005] NET: Registered protocol family 17
[    0.767022] Registering the dns_resolver key type
[    0.767496] Using IPI No-Shortcut mode
[    0.767590] PM: Hibernation image not present or could not be loaded.
[    0.767602] registered taskstats version 1
[    0.768081]   Magic number: 11:658:186
[    0.768173] rtc_cmos 00:08: setting system clock to 2011-05-18 16:09:39 UTC (1305734979)
[    0.768176] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.768178] EDD information not available.
[    0.778031] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    0.864468] ata1.00: ATAPI: Optiarc DVD RW AD-7530B, NX02, max UDMA/33
[    0.880351] ata1.00: configured for UDMA/33
[    0.882481] scsi 0:0:0:0: CD-ROM            Optiarc  DVD RW AD-7530B  NX02 PQ: 0 ANSI: 5
[    0.890029] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    0.890034] cdrom: Uniform CD-ROM driver Revision: 3.20
[    0.890212] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    0.890278] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    0.890425] Freeing unused kernel memory: 700k freed
[    0.890741] Write protecting the kernel text: 5192k
[    0.890803] Write protecting the kernel read-only data: 2148k
[    0.913815] <30>udev[73]: starting version 167
[    1.018549] sky2: driver version 1.28
[    1.018591] sky2 0000:04:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.018608] sky2 0000:04:00.0: setting latency timer to 64
[    1.018639] sky2 0000:04:00.0: Yukon-2 EC Ultra chip revision 2
[    1.018773] sky2 0000:04:00.0: irq 45 for MSI/MSI-X
[    1.024965] sdhci: Secure Digital Host Controller Interface driver
[    1.024968] sdhci: Copyright(c) Pierre Ossman
[    1.026523] sdhci-pci 0000:0b:09.3: SDHCI controller found [104c:803c] (rev 0)
[    1.026539] sdhci-pci 0000:0b:09.3: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    1.026590] mmc0: no vmmc regulator found
[    1.026625] Registered led device: mmc0::
[    1.051629] sky2 0000:04:00.0: eth0: addr 00:1b:24:94:2a:d7
[    1.052680] ahci 0000:00:1f.2: version 3.0
[    1.052695] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.052754] ahci 0000:00:1f.2: irq 46 for MSI/MSI-X
[    1.052830] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 3 Gbps 0x7 impl SATA mode
[    1.052833] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part ccc 
[    1.052839] ahci 0000:00:1f.2: setting latency timer to 64
[    1.053429] mmc0: SDHCI controller on PCI [0000:0b:09.3] using DMA
[    1.056683] scsi2 : ahci
[    1.057790] firewire_ohci 0000:0b:09.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    1.058655] scsi3 : ahci
[    1.058740] scsi4 : ahci
[    1.058904] ata3: SATA max UDMA/133 abar m2048@0xf0c04000 port 0xf0c04100 irq 46
[    1.058908] ata4: SATA max UDMA/133 abar m2048@0xf0c04000 port 0xf0c04180 irq 46
[    1.058911] ata5: SATA max UDMA/133 abar m2048@0xf0c04000 port 0xf0c04200 irq 46
[    1.108089] usb 2-4: new high speed USB device using ehci_hcd and address 3
[    1.112116] firewire_ohci: Added fw-ohci device 0000:0b:09.1, OHCI v1.10, 4 IR + 8 IT contexts, quirks 0x2
[    1.376096] ata5: SATA link down (SStatus 0 SControl 300)
[    1.376131] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.376159] ata4: SATA link down (SStatus 0 SControl 300)
[    1.376700] ata3.00: unexpected _GTF length (8)
[    1.422088] ata3.00: ATA-7: WDC WD1600BEVS-00RST0, 04.01G04, max UDMA/133
[    1.422094] ata3.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.422929] ata3.00: unexpected _GTF length (8)
[    1.423207] ata3.00: configured for UDMA/133
[    1.423436] scsi 2:0:0:0: Direct-Access     ATA      WDC WD1600BEVS-0 04.0 PQ: 0 ANSI: 5
[    1.423631] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    1.423637] sd 2:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    1.423706] sd 2:0:0:0: [sda] Write Protect is off
[    1.423709] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.423731] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.473777]  sda: sda1 sda2 < sda5 sda6 sda7 sda8 sda9 >
[    1.474292] sd 2:0:0:0: [sda] Attached SCSI disk
[    1.484088] usb 6-1: new low speed USB device using uhci_hcd and address 2
[    1.612173] firewire_core: created device fw0: GUID 001b2400005287e7, S400
[    1.699980] input: PIXART USB OPTICAL MOUSE as /devices/pci0000:00/0000:00:1d.1/usb6/6-1/6-1:1.0/input/input5
[    1.700105] generic-usb 0003:093A:2510.0001: input,hidraw0: USB HID v1.11 Mouse [PIXART USB OPTICAL MOUSE] on usb-0000:00:1d.1-1/input0
[    1.700120] usbcore: registered new interface driver usbhid
[    1.700121] usbhid: USB HID core driver
[    2.123371] EXT4-fs (sda8): mounted filesystem with ordered data mode. Opts: (null)
[    4.210251] Adding 2094076k swap on /dev/sda9.  Priority:-1 extents:1 across:2094076k 
[    4.536313] EXT4-fs (sda8): re-mounted. Opts: errors=remount-ro
[    4.798565] <30>udev[346]: starting version 167
[    5.606259] lp: driver loaded but no devices found
[    5.963071] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:02/LNXVIDEO:00/input/input6
[    5.963195] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[    6.152154] cfg80211: Calling CRDA to update world regulatory domain
[    6.373881] tifm_7xx1 0000:0b:09.2: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    6.619303] yenta_cardbus 0000:0b:09.0: CardBus bridge found [152d:0763]
[    6.619325] yenta_cardbus 0000:0b:09.0: Enabling burst memory read transactions
[    6.619331] yenta_cardbus 0000:0b:09.0: Using CSCINT to route CSC interrupts to PCI
[    6.619334] yenta_cardbus 0000:0b:09.0: Routing CardBus interrupts to PCI
[    6.619340] yenta_cardbus 0000:0b:09.0: TI: mfunc 0x01001922, devctl 0x66
[    6.781944] tpm_tis 00:09: 1.2 TPM (device-id 0xB, rev-id 16)
[    6.848742] yenta_cardbus 0000:0b:09.0: ISA IRQ mask 0x0cf0, PCI irq 20
[    6.848746] yenta_cardbus 0000:0b:09.0: Socket status: 30000006
[    6.848750] pci_bus 0000:0b: Raising subordinate bus# of parent bus (#0b) from #0c to #0f
[    6.848758] yenta_cardbus 0000:0b:09.0: pcmcia: parent PCI bridge window: [io  0x7000-0x7fff]
[    6.848762] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x7000-0x7fff: excluding 0x7000-0x70ff 0x7400-0x74ff
[    6.855901] yenta_cardbus 0000:0b:09.0: pcmcia: parent PCI bridge window: [mem 0xf0800000-0xf08fffff]
[    6.855904] pcmcia_socket pcmcia_socket0: cs: memory probe 0xf0800000-0xf08fffff: excluding 0xf0800000-0xf080ffff
[    6.855918] yenta_cardbus 0000:0b:09.0: pcmcia: parent PCI bridge window: [mem 0x80000000-0x83ffffff pref]
[    6.855921] pcmcia_socket pcmcia_socket0: cs: memory probe 0x80000000-0x83ffffff: excluding 0x80000000-0x83ffffff
[    6.938458] Linux video capture interface: v2.00
[    6.994861] uvcvideo: Found UVC 1.00 device FO13FF-50 PC-CAM (05c8:0100)
[    6.996143] input: FO13FF-50 PC-CAM as /devices/pci0000:00/0000:00:1d.7/usb2/2-4/2-4:1.0/input/input7
[    6.996211] usbcore: registered new interface driver uvcvideo
[    6.996213] USB Video Class driver (v1.0.0)
[    7.037996] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[    7.038000] iwlagn: Copyright(c) 2003-2010 Intel Corporation
[    7.038102] iwlagn 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    7.038112] iwlagn 0000:02:00.0: setting latency timer to 64
[    7.038143] iwlagn 0000:02:00.0: Detected Intel(R) Wireless WiFi Link 4965AGN, REV=0x4
[    7.076595] iwlagn 0000:02:00.0: device EEPROM VER=0x36, CALIB=0x5
[    7.076598] iwlagn 0000:02:00.0: Device SKU: 0Xb
[    7.077250] iwlagn 0000:02:00.0: Tunable channels: 13 802.11bg, 19 802.11a channels
[    7.077335] iwlagn 0000:02:00.0: irq 47 for MSI/MSI-X
[    7.352095] Synaptics Touchpad, model: 1, fw: 5.10, id: 0x258eb1, caps: 0xa04713/0x0/0x0
[    7.380854] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: excluding 0x170-0x177 0x1f0-0x1f7 0x370-0x377 0x380-0x387
[    7.382984] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding 0x3f0-0x3f7 0x4d0-0x4d7
[    7.383899] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[    7.384663] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[    7.385489] pcmcia_socket pcmcia_socket0: cs: memory probe 0x0c0000-0x0fffff: excluding 0xc0000-0xd3fff 0xe0000-0xfffff
[    7.385553] pcmcia_socket pcmcia_socket0: cs: memory probe 0xa0000000-0xa0ffffff: clean.
[    7.385618] pcmcia_socket pcmcia_socket0: cs: memory probe 0x60000000-0x60ffffff: excluding 0x60000000-0x60ffffff
[    7.385684] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[    7.426186] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input8
[    7.471203] iwlagn 0000:02:00.0: loaded firmware version 228.61.2.24
[    7.471389] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[    7.989005] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[    7.989011] cfg80211: World regulatory domain updated:
[    7.989012] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[    7.989015] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    7.989018] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    7.989020] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    7.989022] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    7.989025] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    8.430875] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[    8.640227] type=1400 audit(1305702587.368:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=606 comm="apparmor_parser"
[    8.640237] type=1400 audit(1305702587.368:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=558 comm="apparmor_parser"
[    8.641094] type=1400 audit(1305702587.368:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=606 comm="apparmor_parser"
[    8.641119] type=1400 audit(1305702587.368:5): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=558 comm="apparmor_parser"
[    8.641650] type=1400 audit(1305702587.368:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=606 comm="apparmor_parser"
[    8.641677] type=1400 audit(1305702587.368:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=558 comm="apparmor_parser"
[    8.642481] type=1400 audit(1305702587.368:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=714 comm="apparmor_parser"
[    8.643347] type=1400 audit(1305702587.368:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=714 comm="apparmor_parser"
[    8.643896] type=1400 audit(1305702587.368:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=714 comm="apparmor_parser"
[    9.147641] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    9.147707] HDA Intel 0000:00:1b.0: irq 48 for MSI/MSI-X
[    9.147742] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   10.177098] nvidia: module license 'NVIDIA' taints kernel.
[   10.177104] Disabling lock debugging due to kernel taint
[   11.201029] nvidia 0000:01:00.0: power state changed by ACPI to D0
[   11.201034] nvidia 0000:01:00.0: power state changed by ACPI to D0
[   11.201042] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   11.201051] nvidia 0000:01:00.0: setting latency timer to 64
[   11.201056] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   11.201205] NVRM: loading NVIDIA UNIX x86 Kernel Module  270.41.06  Mon Apr 18 14:54:25 PDT 2011
[   12.131380] type=1400 audit(1305702590.856:11): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=823 comm="apparmor_parser"
[   14.444952] sky2 0000:04:00.0: eth0: enabling interface
[   14.445212] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   16.801640] EXT4-fs (sda8): re-mounted. Opts: errors=remount-ro,commit=0
[   17.376152] sky2 0000:04:00.0: eth0: Link is up at 100 Mbps, full duplex, flow control both
[   17.376302] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   28.232089] eth0: no IPv6 routers present
[   61.904116] usb 6-1: USB disconnect, address 2
[   63.384101] usb 6-1: new low speed USB device using uhci_hcd and address 3
[   63.586355] input: PIXART USB OPTICAL MOUSE as /devices/pci0000:00/0000:00:1d.1/usb6/6-1/6-1:1.0/input/input9
[   63.586480] generic-usb 0003:093A:2510.0002: input,hidraw0: USB HID v1.11 Mouse [PIXART USB OPTICAL MOUSE] on usb-0000:00:1d.1-1/input0
[  123.656170] usb 6-1: USB disconnect, address 3
[  125.136148] usb 6-1: new low speed USB device using uhci_hcd and address 4
[  125.337445] input: PIXART USB OPTICAL MOUSE as /devices/pci0000:00/0000:00:1d.1/usb6/6-1/6-1:1.0/input/input10
[  125.337801] generic-usb 0003:093A:2510.0003: input,hidraw0: USB HID v1.11 Mouse [PIXART USB OPTICAL MOUSE] on usb-0000:00:1d.1-1/input0
[  129.036118] tpm_tis 00:09: tpm_transmit: tpm_send: error 4294967234
[  185.096275] vesafb: framebuffer at 0xcd000000, mapped to 0xf8500000, using 1216k, total 1216k
[  185.096279] vesafb: mode is 640x480x32, linelength=2560, pages=0
[  185.096281] vesafb: scrolling: redraw
[  185.096284] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[  185.096428] Console: switching to colour frame buffer device 80x30
[  185.096441] fb0: VESA VGA frame buffer device
[  185.107282] ppdev: user-space parallel port driver
[  185.130755] audit_printk_skb: 27 callbacks suppressed
[  185.130759] type=1400 audit(1305702763.859:21): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=1222 comm="apparmor_parser"
[  185.131779] type=1400 audit(1305702763.859:22): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=1222 comm="apparmor_parser"
[  185.408084] usb 6-1: USB disconnect, address 4
[  186.888086] usb 6-1: new low speed USB device using uhci_hcd and address 5
[  187.146561] input: PIXART USB OPTICAL MOUSE as /devices/pci0000:00/0000:00:1d.1/usb6/6-1/6-1:1.0/input/input11
[  187.146688] generic-usb 0003:093A:2510.0004: input,hidraw0: USB HID v1.11 Mouse [PIXART USB OPTICAL MOUSE] on usb-0000:00:1d.1-1/input0
[  195.299578] EXT4-fs (sda8): re-mounted. Opts: errors=remount-ro,commit=0
```

---

### Post by spikoley on 2011-05-18
Check under Additional Drivers for "This driver is activated but not currently in use".  If you see that message then its related to [this bug]("https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/771788") in Jockey.

---

