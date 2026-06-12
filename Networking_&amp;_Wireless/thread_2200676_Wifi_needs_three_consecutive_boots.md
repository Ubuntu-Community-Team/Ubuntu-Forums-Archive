---
title: "Wifi needs three consecutive boots"
date: 2014-01-20
forum: Networking &amp; Wireless
---

### Post by jonckheerestijn on 2014-01-20
The problem is very simple, but also very annoying: my laptop needs three consecutive boots in Ubuntu 13.10 before I can use the WiFi.

It seems what's happening is this:
[LIST=1]
[*]The hardware isn't found
[*]The hardware can't connect
[*]It all works
[/LIST]

Anyone know a solution for this (other than writing an sh-script to do the three boots)?



Here are the dmesg-logs for the three consecutive boots:

Boot 1
```
[    0.000000] Initializing cgroup subsys cpuset[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 3.11.0-15-generic (buildd@tipua) (gcc version 4.8.1 (Ubuntu/Linaro 4.8.1-10ubuntu8) ) #23-Ubuntu SMP Mon Dec 9 18:16:27 UTC 2013 (Ubuntu 3.11.0-15.23-generic 3.11.10)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] Disabled fast string operations
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009f7ff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009f800-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000dc000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x000000003f68ffff] usable
[    0.000000] BIOS-e820: [mem 0x000000003f690000-0x000000003f6fffff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x000000003f700000-0x000000003fffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000e0000000-0x00000000efffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec0ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed00000-0x00000000fed003ff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed14000-0x00000000fed19fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed1c000-0x00000000fed8ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ff000000-0x00000000ffffffff] reserved
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.4 present.
[    0.000000] DMI: MEDION WIM2120/WIM2120, BIOS R01-B0F    01/15/2007
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] e820: last_pfn = 0x3f690 max_arch_pfn = 0x1000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-DFFFF uncachable
[    0.000000]   E0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask FC0000000 write-back
[    0.000000]   1 base 03F700000 mask FFFF00000 uncachable
[    0.000000]   2 base 03F800000 mask FFF800000 uncachable
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] PAT not supported by CPU.
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 1GB, type WB
[    0.000000] reg 1, base: 1015MB, range: 1MB, type UC
[    0.000000] reg 2, base: 1016MB, range: 8MB, type UC
[    0.000000] total RAM covered: 1015M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K     chunk_size: 16M     num_reg: 3      lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 1GB, type WB
[    0.000000] reg 1, base: 1015MB, range: 1MB, type UC
[    0.000000] reg 2, base: 1016MB, range: 8MB, type UC
[    0.000000] found SMP MP-table at [mem 0x000f68e0-0x000f68ef] mapped at [c00f68e0]
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] initial memory mapped: [mem 0x00000000-0x01ffffff]
[    0.000000] Base memory trampoline at [c009b000] 9b000 size 16384
[    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
[    0.000000]  [mem 0x00000000-0x000fffff] page 4k
[    0.000000] init_memory_mapping: [mem 0x37800000-0x379fffff]
[    0.000000]  [mem 0x37800000-0x379fffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x34000000-0x377fffff]
[    0.000000]  [mem 0x34000000-0x377fffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x00100000-0x33ffffff]
[    0.000000]  [mem 0x00100000-0x001fffff] page 4k
[    0.000000]  [mem 0x00200000-0x33ffffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x37a00000-0x37bfdfff]
[    0.000000]  [mem 0x37a00000-0x37bfdfff] page 4k
[    0.000000] BRK [0x01b49000, 0x01b49fff] PGTABLE
[    0.000000] RAMDISK: [mem 0x35f6c000-0x36fadfff]
[    0.000000] ACPI: RSDP 000f6770 00014 (v00 PTLTD )
[    0.000000] ACPI: RSDT 3f6916cf 00048 (v01 MEDION MEDIONAG 06040000 ZNEB 00000000)
[    0.000000] ACPI: FACP 3f697caa 00074 (v01 INTEL  CALISTGA 06040000 LOHR 00000065)
[    0.000000] ACPI: DSDT 3f692298 05A12 (v01 INTEL  CALISTGA 06040000 MSFT 0100000E)
[    0.000000] ACPI: FACS 3f698fc0 00040
[    0.000000] ACPI: APIC 3f697d1e 00068 (v01 INTEL  CALISTGA 06040000 LOHR 00000065)
[    0.000000] ACPI: HPET 3f697d86 00038 (v01 INTEL  CALISTGA 06040000 LOHR 00000065)
[    0.000000] ACPI: MCFG 3f697dbe 0003C (v01 INTEL  CALISTGA 06040000 LOHR 00000065)
[    0.000000] ACPI: SLIC 3f697dfa 00176 (v01 MEDION MEDIONAG 06040000 BENZ 00000001)
[    0.000000] ACPI: APIC 3f697f70 00068 (v01 PTLTD  ? APIC   06040000  LTP 00000000)
[    0.000000] ACPI: BOOT 3f697fd8 00028 (v01 PTLTD  $SBFTBL$ 06040000  LTP 00000001)
[    0.000000] ACPI: SSDT 3f69208e 0020A (v01 SataRe SataAhci 00001000 INTL 20050624)
[    0.000000] ACPI: SSDT 3f691717 004F6 (v01  PmRef    CpuPm 00003000 INTL 20050624)
[    0.000000] ACPI: BIOS bug: multiple APIC/MADT found, using 0
[    0.000000] ACPI: If "acpi_apic_instance=2" works better, notify linux-acpi@vger.kernel.org
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 122MB HIGHMEM available.
[    0.000000] 891MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 37bfe000
[    0.000000]   low ram: 0 - 37bfe000
[    0.000000] BRK [0x01b4a000, 0x01b4afff] PGTABLE
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00001000-0x00ffffff]
[    0.000000]   Normal   [mem 0x01000000-0x37bfdfff]
[    0.000000]   HighMem  [mem 0x37bfe000-0x3f68ffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00001000-0x0009efff]
[    0.000000]   node   0: [mem 0x00100000-0x3f68ffff]
[    0.000000] On node 0 totalpages: 259630
[    0.000000] free_area_init_node: node 0, pgdat c1958bc0, node_mem_map f740e020
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3998 pages, LIFO batch:0
[    0.000000]   Normal zone: 1752 pages used for memmap
[    0.000000]   Normal zone: 224254 pages, LIFO batch:31
[    0.000000]   HighMem zone: 246 pages used for memmap
[    0.000000]   HighMem zone: 31378 pages, LIFO batch:7
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
[    0.000000] smpboot: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: [mem 0x0009f000-0x0009ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dbfff]
[    0.000000] PM: Registered nosave memory: [mem 0x000dc000-0x000fffff]
[    0.000000] e820: [mem 0x40000000-0xdfffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @f73ec000 s36288 r0 d21056 u57344
[    0.000000] pcpu-alloc: s36288 r0 d21056 u57344 alloc=14*4096
[    0.000000] pcpu-alloc: [0] 0 [0] 1 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 257846
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.11.0-15-generic root=UUID=b1b16843-0173-40ed-a37c-8643572cc543 ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] allocated 2077816 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (00037bfe:0003f690)
[    0.000000] Memory: 999140K/1038520K available (6358K kernel code, 611K rwdata, 2692K rodata, 880K init, 908K bss, 39380K reserved, 125512K highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff14000 - 0xfffff000   ( 940 kB)
[    0.000000]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
[    0.000000]     vmalloc : 0xf83fe000 - 0xffbfe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf7bfe000   ( 891 MB)
[    0.000000]       .init : 0xc1972000 - 0xc1a4e000   ( 880 kB)
[    0.000000]       .data : 0xc1635ee4 - 0xc1971f80   (3312 kB)
[    0.000000]       .text : 0xc1000000 - 0xc1635ee4   (6359 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU restricting CPUs from NR_CPUS=8 to nr_cpu_ids=2.
[    0.000000] NR_IRQS:2304 nr_irqs:512 16
[    0.000000] CPU 0 irqstacks, hard=f5808000 soft=f580a000
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.000000] tsc: Detected 1662.459 MHz processor
[    0.004002] Calibrating delay loop (skipped), value calculated using timer frequency.. 3324.91 BogoMIPS (lpj=6649836)
[    0.004008] pid_max: default: 32768 minimum: 301
[    0.004054] Security Framework initialized
[    0.004082] AppArmor: AppArmor initialized
[    0.004085] Yama: becoming mindful.
[    0.004188] Mount-cache hash table entries: 512
[    0.004566] Initializing cgroup subsys memory
[    0.004583] Initializing cgroup subsys devices
[    0.004586] Initializing cgroup subsys freezer
[    0.004590] Initializing cgroup subsys blkio
[    0.004594] Initializing cgroup subsys perf_event
[    0.004599] Initializing cgroup subsys hugetlb
[    0.004635] Disabled fast string operations
[    0.004642] CPU: Physical Processor ID: 0
[    0.004645] CPU: Processor Core ID: 0
[    0.004649] mce: CPU supports 6 MCE banks
[    0.004661] CPU0: Thermal monitoring enabled (TM2)
[    0.004678] Last level iTLB entries: 4KB 128, 2MB 0, 4MB 2
[    0.004678] Last level dTLB entries: 4KB 128, 2MB 0, 4MB 8
[    0.004678] tlb_flushall_shift: 6
[    0.005169] Freeing SMP alternatives memory: 28K (c1a4e000 - c1a55000)
[    0.010703] ACPI: Core revision 20130517
[    0.016535] ACPI: All ACPI Tables successfully acquired
[    0.020013] ftrace: allocating 27182 entries in 54 pages
[    0.032134] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.032612] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.073258] smpboot: CPU0: Genuine Intel(R) CPU           T2300  @ 1.66GHz (fam: 06, model: 0e, stepping: 08)
[    0.076000] Performance Events: Core events, core PMU driver.
[    0.076000] ... version:                1
[    0.076000] ... bit width:              40
[    0.076000] ... generic registers:      2
[    0.076000] ... value mask:             000000ffffffffff
[    0.076000] ... max period:             000000007fffffff
[    0.076000] ... fixed-purpose events:   0
[    0.076000] ... event mask:             0000000000000003
[    0.076000] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.076000] CPU 1 irqstacks, hard=f58f0000 soft=f58f2000
[    0.076000] smpboot: Booting Node   0, Processors  #1 OK
[    0.008000] Initializing CPU#1
[    0.008000] Disabled fast string operations
[    0.088066] Brought up 2 CPUs
[    0.088074] smpboot: Total of 2 processors activated (6649.83 BogoMIPS)
[    0.092063] devtmpfs: initialized
[    0.092362] EVM: security.selinux
[    0.092364] EVM: security.SMACK64
[    0.092367] EVM: security.capability
[    0.092393] PM: Registering ACPI NVS region [mem 0x3f690000-0x3f6fffff] (458752 bytes)
[    0.094030] regulator-dummy: no parameters
[    0.094079] RTC time:  6:20:15, date: 01/20/14
[    0.094150] NET: Registered protocol family 16
[    0.094399] EISA bus registered
[    0.094517] ACPI: bus type PCI registered
[    0.094521] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.094613] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.094618] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    0.094621] PCI: Using MMCONFIG for extended config space
[    0.094623] PCI: Using configuration type 1 for base access
[    0.096849] bio: create slab <bio-0> at 0
[    0.096849] ACPI: Added _OSI(Module Device)
[    0.096849] ACPI: Added _OSI(Processor Device)
[    0.096849] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.096849] ACPI: Added _OSI(Processor Aggregator Device)
[    0.098201] ACPI: EC: Look up EC in DSDT
[    0.103354] ACPI: SSDT 3f691e5d 001A8 (v01  PmRef  Cpu0Ist 00003000 INTL 20050624)
[    0.103864] ACPI: Dynamic OEM Table Load:
[    0.103869] ACPI: SSDT   (null) 001A8 (v01  PmRef  Cpu0Ist 00003000 INTL 20050624)
[    0.104021] ACPI: SSDT 3f691c0d 001CB (v01  PmRef  Cpu0Cst 00003001 INTL 20050624)
[    0.104508] ACPI: Dynamic OEM Table Load:
[    0.104512] ACPI: SSDT   (null) 001CB (v01  PmRef  Cpu0Cst 00003001 INTL 20050624)
[    0.104879] ACPI: SSDT 3f692005 00089 (v01  PmRef  Cpu1Ist 00003000 INTL 20050624)
[    0.105379] ACPI: Dynamic OEM Table Load:
[    0.105383] ACPI: SSDT   (null) 00089 (v01  PmRef  Cpu1Ist 00003000 INTL 20050624)
[    0.105513] ACPI: SSDT 3f691dd8 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20050624)
[    0.106003] ACPI: Dynamic OEM Table Load:
[    0.106007] ACPI: SSDT   (null) 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20050624)
[    0.108115] ACPI: EC: GPE storm detected(9 GPEs), transactions will use polling mode
[    0.108192] ACPI: Interpreter enabled
[    0.108205] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20130517/hwxface-571)
[    0.108213] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20130517/hwxface-571)
[    0.108237] ACPI: (supports S0 S3 S4 S5)
[    0.108239] ACPI: Using IOAPIC for interrupt routing
[    0.108281] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
[    0.108452] ACPI: No dock devices found.
[    0.246763] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.246772] acpi PNP0A08:00: ACPI _OSC support notification failed, disabling PCIe ASPM
[    0.246776] acpi PNP0A08:00: Unable to request _OSC control (_OSC support mask: 0x08)
[    0.247649] acpi PNP0A08:00: host bridge window [io  0x0000-0x0cf7] (ignored)
[    0.247654] acpi PNP0A08:00: host bridge window [io  0x0d00-0xffff] (ignored)
[    0.247658] acpi PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)
[    0.247662] acpi PNP0A08:00: host bridge window [mem 0x000d0000-0x000d3fff] (ignored)
[    0.247666] acpi PNP0A08:00: host bridge window [mem 0x000d4000-0x000d7fff] (ignored)
[    0.247670] acpi PNP0A08:00: host bridge window [mem 0x000d8000-0x000dbfff] (ignored)
[    0.247675] acpi PNP0A08:00: host bridge window [mem 0x40000000-0xfebfffff] (ignored)
[    0.247679] PCI: root bus 00: using default resources
[    0.247898] PCI host bridge to bus 0000:00
[    0.247904] pci_bus 0000:00: root bus resource [bus 00-ff]
[    0.247908] pci_bus 0000:00: root bus resource [io  0x0000-0xffff]
[    0.247912] pci_bus 0000:00: root bus resource [mem 0x00000000-0xffffffff]
[    0.247928] pci 0000:00:00.0: [8086:27a0] type 00 class 0x060000
[    0.248119] pci 0000:00:02.0: [8086:27a2] type 00 class 0x030000
[    0.248137] pci 0000:00:02.0: reg 0x10: [mem 0xd8100000-0xd817ffff]
[    0.248147] pci 0000:00:02.0: reg 0x14: [io  0x1800-0x1807]
[    0.248157] pci 0000:00:02.0: reg 0x18: [mem 0xc0000000-0xcfffffff pref]
[    0.248167] pci 0000:00:02.0: reg 0x1c: [mem 0xd8200000-0xd823ffff]
[    0.248339] pci 0000:00:02.1: [8086:27a6] type 00 class 0x038000
[    0.248354] pci 0000:00:02.1: reg 0x10: [mem 0xd8180000-0xd81fffff]
[    0.248598] pci 0000:00:1b.0: [8086:27d8] type 00 class 0x040300
[    0.248626] pci 0000:00:1b.0: reg 0x10: [mem 0xd8440000-0xd8443fff 64bit]
[    0.248748] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.248851] pci 0000:00:1b.0: System wakeup disabled by ACPI
[    0.248917] pci 0000:00:1c.0: [8086:27d0] type 01 class 0x060400
[    0.249045] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.249207] pci 0000:00:1c.1: [8086:27d2] type 01 class 0x060400
[    0.249334] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.249498] pci 0000:00:1c.3: [8086:27d6] type 01 class 0x060400
[    0.249625] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.249789] pci 0000:00:1d.0: [8086:27c8] type 00 class 0x0c0300
[    0.249856] pci 0000:00:1d.0: reg 0x20: [io  0x1820-0x183f]
[    0.250017] pci 0000:00:1d.1: [8086:27c9] type 00 class 0x0c0300
[    0.250083] pci 0000:00:1d.1: reg 0x20: [io  0x1840-0x185f]
[    0.250246] pci 0000:00:1d.2: [8086:27ca] type 00 class 0x0c0300
[    0.250312] pci 0000:00:1d.2: reg 0x20: [io  0x1860-0x187f]
[    0.250473] pci 0000:00:1d.3: [8086:27cb] type 00 class 0x0c0300
[    0.250539] pci 0000:00:1d.3: reg 0x20: [io  0x1880-0x189f]
[    0.250716] pci 0000:00:1d.7: [8086:27cc] type 00 class 0x0c0320
[    0.250746] pci 0000:00:1d.7: reg 0x10: [mem 0xd8444000-0xd84443ff]
[    0.250869] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.251021] pci 0000:00:1e.0: [8086:2448] type 01 class 0x060401
[    0.251248] pci 0000:00:1f.0: [8086:27b9] type 00 class 0x060100
[    0.251376] pci 0000:00:1f.0: address space collision: [io  0x1000-0x107f] conflicts with ACPI CPU throttle [??? 0x00001010-0x00001015 flags 0x80000000]
[    0.251385] pci 0000:00:1f.0: quirk: [io  0x1180-0x11bf] claimed by ICH6 GPIO
[    0.251394] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 2 PIO at 1200 (mask 0007)
[    0.251574] pci 0000:00:1f.1: [8086:27df] type 00 class 0x01018a
[    0.251595] pci 0000:00:1f.1: reg 0x10: [io  0x0000-0x0007]
[    0.251610] pci 0000:00:1f.1: reg 0x14: [io  0x0000-0x0003]
[    0.251625] pci 0000:00:1f.1: reg 0x18: [io  0x0000-0x0007]
[    0.251640] pci 0000:00:1f.1: reg 0x1c: [io  0x0000-0x0003]
[    0.251655] pci 0000:00:1f.1: reg 0x20: [io  0x1810-0x181f]
[    0.251830] pci 0000:00:1f.2: [8086:27c5] type 00 class 0x010601
[    0.251859] pci 0000:00:1f.2: reg 0x10: [io  0x18d0-0x18d7]
[    0.251874] pci 0000:00:1f.2: reg 0x14: [io  0x18c4-0x18c7]
[    0.251890] pci 0000:00:1f.2: reg 0x18: [io  0x18c8-0x18cf]
[    0.251905] pci 0000:00:1f.2: reg 0x1c: [io  0x18c0-0x18c3]
[    0.251920] pci 0000:00:1f.2: reg 0x20: [io  0x18b0-0x18bf]
[    0.251935] pci 0000:00:1f.2: reg 0x24: [mem 0xd8444400-0xd84447ff]
[    0.252008] pci 0000:00:1f.2: PME# supported from D3hot
[    0.252158] pci 0000:00:1f.3: [8086:27da] type 00 class 0x0c0500
[    0.252241] pci 0000:00:1f.3: reg 0x20: [io  0x18e0-0x18ff]
[    0.252561] acpiphp: Slot [1] registered
[    0.252574] pci 0000:00:1c.0: PCI bridge to [bus 02-03]
[    0.252581] pci 0000:00:1c.0:   bridge window [io  0x2000-0x2fff]
[    0.252589] pci 0000:00:1c.0:   bridge window [mem 0xd4000000-0xd5ffffff]
[    0.252599] pci 0000:00:1c.0:   bridge window [mem 0xd0000000-0xd1ffffff 64bit pref]
[    0.252743] pci 0000:04:00.0: [10ec:8136] type 00 class 0x020000
[    0.252773] pci 0000:04:00.0: reg 0x10: [io  0x3000-0x30ff]
[    0.252821] pci 0000:04:00.0: reg 0x18: [mem 0xd6000000-0xd6000fff 64bit]
[    0.252876] pci 0000:04:00.0: reg 0x30: [mem 0x00000000-0x0001ffff pref]
[    0.252999] pci 0000:04:00.0: supports D1 D2
[    0.253003] pci 0000:04:00.0: PME# supported from D1 D2 D3hot D3cold
[    0.253049] pci 0000:04:00.0: System wakeup disabled by ACPI
[    0.253105] pci 0000:04:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    0.253122] pci 0000:00:1c.1: PCI bridge to [bus 04-05]
[    0.253129] pci 0000:00:1c.1:   bridge window [io  0x3000-0x3fff]
[    0.253136] pci 0000:00:1c.1:   bridge window [mem 0xd6000000-0xd7ffffff]
[    0.253147] pci 0000:00:1c.1:   bridge window [mem 0xd2000000-0xd3ffffff 64bit pref]
[    0.253255] pci 0000:00:1c.3: PCI bridge to [bus 06]
[    0.253367] pci 0000:0a:09.0: [1180:0832] type 00 class 0x0c0010
[    0.253386] pci 0000:0a:09.0: proprietary Ricoh MMC controller disabled (via firewire function)
[    0.253389] pci 0000:0a:09.0: MMC cards are now supported by standard SDHCI controller
[    0.253409] pci 0000:0a:09.0: reg 0x10: [mem 0xd8000000-0xd80007ff]
[    0.253525] pci 0000:0a:09.0: supports D1 D2
[    0.253529] pci 0000:0a:09.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.253609] pci 0000:0a:09.1: [1180:0822] type 00 class 0x080500
[    0.253637] pci 0000:0a:09.1: reg 0x10: [mem 0xd8000800-0xd80008ff]
[    0.253750] pci 0000:0a:09.1: supports D1 D2
[    0.253753] pci 0000:0a:09.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.253834] pci 0000:0a:09.2: [1180:0592] type 00 class 0x088000
[    0.253861] pci 0000:0a:09.2: reg 0x10: [mem 0xd8001000-0xd80010ff]
[    0.253974] pci 0000:0a:09.2: supports D1 D2
[    0.253977] pci 0000:0a:09.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.254061] pci 0000:0a:09.3: [1180:0852] type 00 class 0x088000
[    0.254089] pci 0000:0a:09.3: reg 0x10: [mem 0xd8001400-0xd80014ff]
[    0.254204] pci 0000:0a:09.3: supports D1 D2
[    0.254208] pci 0000:0a:09.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.254324] pci 0000:00:1e.0: PCI bridge to [bus 0a] (subtractive decode)
[    0.254335] pci 0000:00:1e.0:   bridge window [mem 0xd8000000-0xd80fffff]
[    0.254346] pci 0000:00:1e.0:   bridge window [io  0x0000-0xffff] (subtractive decode)
[    0.254350] pci 0000:00:1e.0:   bridge window [mem 0x00000000-0xffffffff] (subtractive decode)
[    0.254382] pci_bus 0000:00: on NUMA node 0
[    0.255228] ACPI: PCI Interrupt Link [LNKA] (IRQs 10 11) *7
[    0.255328] ACPI: PCI Interrupt Link [LNKB] (IRQs 10 11) *3
[    0.255426] ACPI: PCI Interrupt Link [LNKC] (IRQs 10 *11)
[    0.255523] ACPI: PCI Interrupt Link [LNKD] (IRQs *10 11)
[    0.255619] ACPI: PCI Interrupt Link [LNKE] (IRQs 10 11) *0, disabled.
[    0.255718] ACPI: PCI Interrupt Link [LNKF] (IRQs *10 11)
[    0.255813] ACPI: PCI Interrupt Link [LNKG] (IRQs 10 11) *0, disabled.
[    0.255912] ACPI: PCI Interrupt Link [LNKH] (IRQs 10 11) *5
[    0.288482] ACPI: Enabled 9 GPEs in block 00 to 1F
[    0.288497] ACPI: \_SB_.PCI0: notify handler is installed
[    0.288578] Found 1 acpi root devices
[    0.288676] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
[    0.288800] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.288800] vgaarb: loaded
[    0.288800] vgaarb: bridge control possible 0000:00:02.0
[    0.288800] SCSI subsystem initialized
[    0.288800] ACPI: bus type ATA registered
[    0.288800] libata version 3.00 loaded.
[    0.288800] ACPI: bus type USB registered
[    0.288800] usbcore: registered new interface driver usbfs
[    0.288800] usbcore: registered new interface driver hub
[    0.288800] usbcore: registered new device driver usb
[    0.288800] PCI: Using ACPI for IRQ routing
[    0.300969] PCI: pci_cache_line_size set to 64 bytes
[    0.301064] e820: reserve RAM buffer [mem 0x0009f800-0x0009ffff]
[    0.301071] e820: reserve RAM buffer [mem 0x3f690000-0x3fffffff]
[    0.301224] NetLabel: Initializing
[    0.301227] NetLabel:  domain hash size = 128
[    0.301229] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.301247] NetLabel:  unlabeled traffic allowed by default
[    0.301268] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.301268] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.301268] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.302165] Switched to clocksource hpet
[    0.312856] AppArmor: AppArmor Filesystem Enabled
[    0.312910] pnp: PnP ACPI init
[    0.312937] ACPI: bus type PNP registered
[    0.313127] system 00:00: [mem 0xe0000000-0xefffffff] has been reserved
[    0.313132] system 00:00: [mem 0xfed14000-0xfed17fff] has been reserved
[    0.313137] system 00:00: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.313142] system 00:00: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.313146] system 00:00: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.313151] system 00:00: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.313156] system 00:00: [mem 0xfed40000-0xfed44fff] has been reserved
[    0.313160] system 00:00: [mem 0xfed45000-0xfed8ffff] has been reserved
[    0.313167] system 00:00: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.344074] pnp 00:01: [dma 4]
[    0.344122] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.344183] pnp 00:02: Plug and Play ACPI device, IDs INT0800 (active)
[    0.344349] system 00:03: [mem 0xfed00000-0xfed003ff] has been reserved
[    0.344355] system 00:03: Plug and Play ACPI device, IDs PNP0103 PNP0c01 (active)
[    0.344436] pnp 00:04: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.344534] system 00:05: [io  0x0800-0x080f] has been reserved
[    0.344539] system 00:05: [io  0x1000-0x107f] could not be reserved
[    0.344544] system 00:05: [io  0x1180-0x11bf] has been reserved
[    0.344548] system 00:05: [io  0x1640-0x164f] has been reserved
[    0.344553] system 00:05: [io  0x1200-0x120f] has been reserved
[    0.344558] system 00:05: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.344656] system 00:06: [io  0x06a0-0x06af] has been reserved
[    0.344661] system 00:06: [io  0x06b0-0x06ff] has been reserved
[    0.344666] system 00:06: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.344733] pnp 00:07: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.344799] pnp 00:08: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.344862] pnp 00:09: Plug and Play ACPI device, IDs SYN030b SYN0300 PNP0f13 (active)
[    0.344895] pnp: PnP ACPI: found 10 devices
[    0.344898] ACPI: bus type PNP unregistered
[    0.344903] PnPBIOS: Disabled by ACPI PNP
[    0.383354] pci 0000:00:1c.3: bridge window [io  0x1000-0x0fff] to [bus 06] add_size 1000
[    0.383362] pci 0000:00:1c.3: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 06] add_size 200000
[    0.383366] pci 0000:00:1c.3: bridge window [mem 0x00100000-0x000fffff] to [bus 06] add_size 200000
[    0.383386] pci 0000:00:1f.0: BAR 13: [io  0x1000-0x107f] has bogus alignment
[    0.383392] pci 0000:00:1c.3: res[14]=[mem 0x00100000-0x000fffff] get_res_add_size add_size 200000
[    0.383396] pci 0000:00:1c.3: res[15]=[mem 0x00100000-0x000fffff 64bit pref] get_res_add_size add_size 200000
[    0.383400] pci 0000:00:1c.3: res[13]=[io  0x1000-0x0fff] get_res_add_size add_size 1000
[    0.383409] pci 0000:00:1c.3: BAR 14: assigned [mem 0x40000000-0x401fffff]
[    0.383415] pci 0000:00:1c.3: BAR 15: assigned [mem 0x40200000-0x403fffff 64bit pref]
[    0.383422] pci 0000:00:1c.3: BAR 13: assigned [io  0x4000-0x4fff]
[    0.383427] pci 0000:00:1c.0: PCI bridge to [bus 02-03]
[    0.383433] pci 0000:00:1c.0:   bridge window [io  0x2000-0x2fff]
[    0.383442] pci 0000:00:1c.0:   bridge window [mem 0xd4000000-0xd5ffffff]
[    0.383449] pci 0000:00:1c.0:   bridge window [mem 0xd0000000-0xd1ffffff 64bit pref]
[    0.383461] pci 0000:04:00.0: BAR 6: assigned [mem 0xd2000000-0xd201ffff pref]
[    0.383466] pci 0000:00:1c.1: PCI bridge to [bus 04-05]
[    0.383471] pci 0000:00:1c.1:   bridge window [io  0x3000-0x3fff]
[    0.383480] pci 0000:00:1c.1:   bridge window [mem 0xd6000000-0xd7ffffff]
[    0.383487] pci 0000:00:1c.1:   bridge window [mem 0xd2000000-0xd3ffffff 64bit pref]
[    0.383497] pci 0000:00:1c.3: PCI bridge to [bus 06]
[    0.383503] pci 0000:00:1c.3:   bridge window [io  0x4000-0x4fff]
[    0.383511] pci 0000:00:1c.3:   bridge window [mem 0x40000000-0x401fffff]
[    0.383519] pci 0000:00:1c.3:   bridge window [mem 0x40200000-0x403fffff 64bit pref]
[    0.383529] pci 0000:00:1e.0: PCI bridge to [bus 0a]
[    0.383538] pci 0000:00:1e.0:   bridge window [mem 0xd8000000-0xd80fffff]
[    0.384138] pci 0000:00:1e.0: setting latency timer to 64
[    0.384144] pci_bus 0000:00: resource 4 [io  0x0000-0xffff]
[    0.384148] pci_bus 0000:00: resource 5 [mem 0x00000000-0xffffffff]
[    0.384153] pci_bus 0000:02: resource 0 [io  0x2000-0x2fff]
[    0.384157] pci_bus 0000:02: resource 1 [mem 0xd4000000-0xd5ffffff]
[    0.384161] pci_bus 0000:02: resource 2 [mem 0xd0000000-0xd1ffffff 64bit pref]
[    0.384165] pci_bus 0000:04: resource 0 [io  0x3000-0x3fff]
[    0.384169] pci_bus 0000:04: resource 1 [mem 0xd6000000-0xd7ffffff]
[    0.384173] pci_bus 0000:04: resource 2 [mem 0xd2000000-0xd3ffffff 64bit pref]
[    0.384177] pci_bus 0000:06: resource 0 [io  0x4000-0x4fff]
[    0.384181] pci_bus 0000:06: resource 1 [mem 0x40000000-0x401fffff]
[    0.384185] pci_bus 0000:06: resource 2 [mem 0x40200000-0x403fffff 64bit pref]
[    0.384189] pci_bus 0000:0a: resource 1 [mem 0xd8000000-0xd80fffff]
[    0.384193] pci_bus 0000:0a: resource 4 [io  0x0000-0xffff]
[    0.384197] pci_bus 0000:0a: resource 5 [mem 0x00000000-0xffffffff]
[    0.384245] NET: Registered protocol family 2
[    0.384488] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
[    0.384539] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[    0.384590] TCP: Hash tables configured (established 8192 bind 8192)
[    0.384627] TCP: reno registered
[    0.384631] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.384645] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.384740] NET: Registered protocol family 1
[    0.384763] pci 0000:00:02.0: Boot video device
[    0.386657] PCI: CLS 64 bytes, default 64
[    0.386723] Trying to unpack rootfs image as initramfs...
[    0.884298] Freeing initrd memory: 16648K (f5f6c000 - f6fae000)
[    0.884418] Simple Boot Flag at 0x36 set to 0x1
[    0.884613] Scanning for low memory corruption every 60 seconds
[    0.885008] Initialise module verification
[    0.885083] audit: initializing netlink socket (disabled)
[    0.885104] type=2000 audit(1390198815.884:1): initialized
[    0.919140] bounce pool size: 64 pages
[    0.919168] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.921562] zbud: loaded
[    0.921650] VFS: Disk quotas dquot_6.5.2
[    0.921733] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.922636] fuse init (API version 7.22)
[    0.922793] msgmni has been set to 1738
[    0.923662] Key type asymmetric registered
[    0.923667] Asymmetric key parser 'x509' registered
[    0.923722] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    0.923781] io scheduler noop registered
[    0.923785] io scheduler deadline registered (default)
[    0.923833] io scheduler cfq registered
[    0.924058] pcieport 0000:00:1c.0: irq 40 for MSI/MSI-X
[    0.924182] pcieport 0000:00:1c.1: irq 41 for MSI/MSI-X
[    0.924298] pcieport 0000:00:1c.3: irq 42 for MSI/MSI-X
[    0.924430] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.924458] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.924602] intel_idle: does not run on family 6 model 14
[    0.956059] ACPI: AC Adapter [ADP1] (on-line)
[    0.956194] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    0.988079] ACPI: Lid Switch [LID0]
[    0.988148] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1
[    0.988155] ACPI: Sleep Button [SLPB]
[    0.988233] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.988238] ACPI: Power Button [PWRF]
[    0.988347] ACPI: Requesting acpi_cpufreq
[    1.004164] tsc: Marking TSC unstable due to TSC halts in idle
[    1.004178] ACPI: acpi_idle registered with cpuidle
[    1.220092] thermal LNXTHERM:00: registered as thermal_zone0
[    1.220096] ACPI: Thermal Zone [TZS0] (19 C)
[    1.340084] thermal LNXTHERM:01: registered as thermal_zone1
[    1.340088] ACPI: Thermal Zone [TZS1] (26 C)
[    1.340150] GHES: HEST is not enabled!
[    1.340241] isapnp: Scanning for PnP cards...
[    1.340288] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.408106] Linux agpgart interface v0.103
[    1.408231] agpgart-intel 0000:00:00.0: Intel 945GM Chipset
[    1.408296] agpgart-intel 0000:00:00.0: detected gtt size: 262144K total, 262144K mappable
[    1.408882] agpgart-intel 0000:00:00.0: detected 8192K stolen memory
[    1.409057] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xc0000000
[    1.411451] brd: module loaded
[    1.412713] loop: module loaded
[    1.412922] ata_piix 0000:00:1f.1: version 2.13
[    1.413197] ata_piix 0000:00:1f.1: setting latency timer to 64
[    1.413653] scsi0 : ata_piix
[    1.414167] scsi1 : ata_piix
[    1.414252] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1810 irq 14
[    1.414256] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1818 irq 15
[    1.414772] libphy: Fixed MDIO Bus: probed
[    1.414946] tun: Universal TUN/TAP device driver, 1.6
[    1.414949] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.415042] PPP generic driver version 2.4.2
[    1.415106] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.415110] ehci-pci: EHCI PCI platform driver
[    1.415328] ehci-pci 0000:00:1d.7: setting latency timer to 64
[    1.415347] ehci-pci 0000:00:1d.7: EHCI Host Controller
[    1.415357] ehci-pci 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    1.415378] ehci-pci 0000:00:1d.7: debug port 1
[    1.419282] ehci-pci 0000:00:1d.7: cache line size of 64 is not supported
[    1.419312] ehci-pci 0000:00:1d.7: irq 23, io mem 0xd8444000
[    1.419530] ata2: port disabled--ignoring
[    1.428026] ehci-pci 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    1.428089] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    1.428093] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.428097] usb usb1: Product: EHCI Host Controller
[    1.428101] usb usb1: Manufacturer: Linux 3.11.0-15-generic ehci_hcd
[    1.428105] usb usb1: SerialNumber: 0000:00:1d.7
[    1.428272] hub 1-0:1.0: USB hub found
[    1.428281] hub 1-0:1.0: 8 ports detected
[    1.428552] ehci-platform: EHCI generic platform driver
[    1.428565] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.428568] ohci-pci: OHCI PCI platform driver
[    1.428587] ohci-platform: OHCI generic platform driver
[    1.428599] uhci_hcd: USB Universal Host Controller Interface driver
[    1.428810] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.428816] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    1.428824] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.428858] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001820
[    1.428906] usb usb2: New USB device found, idVendor=1d6b, idProduct=0001
[    1.428910] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.428914] usb usb2: Product: UHCI Host Controller
[    1.428918] usb usb2: Manufacturer: Linux 3.11.0-15-generic uhci_hcd
[    1.428921] usb usb2: SerialNumber: 0000:00:1d.0
[    1.429070] hub 2-0:1.0: USB hub found
[    1.429077] hub 2-0:1.0: 2 ports detected
[    1.429383] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    1.429389] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    1.429397] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    1.429447] uhci_hcd 0000:00:1d.1: irq 17, io base 0x00001840
[    1.429496] usb usb3: New USB device found, idVendor=1d6b, idProduct=0001
[    1.429500] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.429504] usb usb3: Product: UHCI Host Controller
[    1.429508] usb usb3: Manufacturer: Linux 3.11.0-15-generic uhci_hcd
[    1.429511] usb usb3: SerialNumber: 0000:00:1d.1
[    1.429648] hub 3-0:1.0: USB hub found
[    1.429657] hub 3-0:1.0: 2 ports detected
[    1.429963] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    1.429969] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    1.429977] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    1.430025] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001860
[    1.430070] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
[    1.430074] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.430078] usb usb4: Product: UHCI Host Controller
[    1.430081] usb usb4: Manufacturer: Linux 3.11.0-15-generic uhci_hcd
[    1.430085] usb usb4: SerialNumber: 0000:00:1d.2
[    1.430223] hub 4-0:1.0: USB hub found
[    1.430230] hub 4-0:1.0: 2 ports detected
[    1.430536] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    1.430542] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    1.430549] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    1.430599] uhci_hcd 0000:00:1d.3: irq 19, io base 0x00001880
[    1.430644] usb usb5: New USB device found, idVendor=1d6b, idProduct=0001
[    1.430648] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.430652] usb usb5: Product: UHCI Host Controller
[    1.430656] usb usb5: Manufacturer: Linux 3.11.0-15-generic uhci_hcd
[    1.430659] usb usb5: SerialNumber: 0000:00:1d.3
[    1.430798] hub 5-0:1.0: USB hub found
[    1.430804] hub 5-0:1.0: 2 ports detected
[    1.431036] i8042: PNP: PS/2 Controller [PNP0303:KBD0,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.431558] i8042: Detected active multiplexing controller, rev 1.1
[    1.431653] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.431662] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    1.431708] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    1.431745] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    1.431784] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    1.431946] mousedev: PS/2 mouse device common for all mice
[    1.432204] rtc_cmos 00:07: RTC can wake from S4
[    1.432376] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
[    1.432414] rtc_cmos 00:07: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    1.432539] device-mapper: uevent: version 1.0.3
[    1.432651] device-mapper: ioctl: 4.25.0-ioctl (2013-06-26) initialised: dm-devel@redhat.com
[    1.432686] platform eisa.0: Probing EISA bus 0
[    1.432721] platform eisa.0: EISA: Detected 0 cards
[    1.432733] cpufreq-nforce2: No nForce2 chipset.
[    1.432820] cpuidle: using governor ladder
[    1.432916] cpuidle: using governor menu
[    1.432931] ledtrig-cpu: registered to indicate activity on CPUs
[    1.433075] TCP: cubic registered
[    1.433264] NET: Registered protocol family 10
[    1.433590] NET: Registered protocol family 17
[    1.433615] Key type dns_resolver registered
[    1.433881] Using IPI No-Shortcut mode
[    1.433997] PM: Hibernation image not present or could not be loaded.
[    1.434003] Loading module verification certificates
[    1.440317] MODSIGN: Loaded cert 'Magrathea: Glacier signing key: 20cb30850ee856675c288816dd8cff0153e91a4b'
[    1.440337] registered taskstats version 1
[    1.440937] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    1.443998] Key type trusted registered
[    1.446962] Key type encrypted registered
[    1.449860] AppArmor: AppArmor sha1 policy hashing enabled
[    1.450335]   Magic number: 14:376:317
[    1.450382] tty tty42: hash matches
[    1.450425] reg-dummy reg-dummy: hash matches
[    1.450472] rtc_cmos 00:07: setting system clock to 2014-01-20 06:20:17 UTC (1390198817)
[    1.508110] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.508113] EDD information not available.
[    1.580418] ata1.00: ATAPI: HL-DT-ST DVDRAM GSA-T10N, TM01, max UDMA/33
[    1.596292] ata1.00: configured for UDMA/33
[    1.694391] isapnp: No Plug & Play device found
[    1.980118] usb 3-2: new low-speed USB device number 2 using uhci_hcd
[    2.152534] usb 3-2: New USB device found, idVendor=0bc7, idProduct=0006
[    2.152542] usb 3-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    2.152549] usb 3-2: Product: RF receiver
[    2.152555] usb 3-2: Manufacturer: X10 WTI
[    2.696405] ACPI: Battery Slot [BAT0] (battery present)
[    2.700463] scsi 0:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-T10N  TM01 PQ: 0 ANSI: 5
[    2.705823] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.705828] cdrom: Uniform CD-ROM driver Revision: 3.20
[    2.706028] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    2.706171] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    2.706820] Freeing unused kernel memory: 880K (c1972000 - c1a4e000)
[    2.706926] Write protecting the kernel text: 6360k
[    2.707062] Write protecting the kernel read-only data: 2700k
[    2.707064] NX-protecting the kernel data: 5928k
[    2.724573] systemd-udevd[101]: starting version 204
[    2.792661] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    2.792680] r8169 0000:04:00.0: can't disable ASPM; OS doesn't have ASPM control
[    2.792942] r8169 0000:04:00.0: irq 43 for MSI/MSI-X
[    2.793207] r8169 0000:04:00.0 eth0: RTL8101e at 0xf840e000, 00:16:d3:80:26:49, XID 14000000 IRQ 43
[    2.805611] sdhci: Secure Digital Host Controller Interface driver
[    2.805616] sdhci: Copyright(c) Pierre Ossman
[    2.814478] sdhci-pci 0000:0a:09.1: SDHCI controller found [1180:0822] (rev 19)
[    2.815585] sdhci-pci 0000:0a:09.1: Will use DMA mode even though HW doesn't fully claim to support it.
[    2.815694] mmc0: no vqmmc regulator found
[    2.815697] mmc0: no vmmc regulator found
[    2.816704] sdhci-pci 0000:0a:09.1: Will use DMA mode even though HW doesn't fully claim to support it.
[    2.816812] mmc0: SDHCI controller on PCI [0000:0a:09.1] using DMA
[    2.828353] ahci 0000:00:1f.2: version 3.0
[    2.828582] ahci 0000:00:1f.2: irq 44 for MSI/MSI-X
[    2.828674] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 4 ports 1.5 Gbps 0x5 impl SATA mode
[    2.828679] ahci 0000:00:1f.2: flags: 64bit ncq pm led clo pio slum part 
[    2.828687] ahci 0000:00:1f.2: setting latency timer to 64
[    2.831125] scsi2 : ahci
[    2.832814] scsi3 : ahci
[    2.834414] scsi4 : ahci
[    2.836163] scsi5 : ahci
[    2.836293] ata3: SATA max UDMA/133 abar m1024@0xd8444400 port 0xd8444500 irq 44
[    2.836296] ata4: DUMMY
[    2.836301] ata5: SATA max UDMA/133 abar m1024@0xd8444400 port 0xd8444600 irq 44
[    2.836303] ata6: DUMMY
[    2.912173] firewire_ohci 0000:0a:09.0: added OHCI v1.10 device as card 0, 4 IR + 4 IT contexts, quirks 0x11
[    3.156144] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    3.156184] ata5: SATA link down (SStatus 0 SControl 300)
[    3.157236] ata3.00: ACPI cmd ef/90:03:00:00:00:a0 (SET FEATURES) rejected by device (Stat=0x51 Err=0x04)
[    3.187029] ata3.00: ATA-7: WDC WD1200BEVS-07LAT0, 01.06M01, max UDMA/133
[    3.187033] ata3.00: 234441648 sectors, multi 16: LBA48 NCQ (depth 1), AA
[    3.188127] ata3.00: ACPI cmd ef/90:03:00:00:00:a0 (SET FEATURES) rejected by device (Stat=0x51 Err=0x04)
[    3.188408] ata3.00: configured for UDMA/133
[    3.188750] scsi 2:0:0:0: Direct-Access     ATA      WDC WD1200BEVS-0 01.0 PQ: 0 ANSI: 5
[    3.188963] sd 2:0:0:0: [sda] 234441648 512-byte logical blocks: (120 GB/111 GiB)
[    3.188996] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    3.189058] sd 2:0:0:0: [sda] Write Protect is off
[    3.189063] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.189133] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.227102]  sda: sda1 sda2 < sda5 >
[    3.227848] sd 2:0:0:0: [sda] Attached SCSI disk
[    3.412206] firewire_core 0000:0a:09.0: created device fw0: GUID 07e40a0094267002, S400
[    3.768404] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[   38.596886] Adding 1036284k swap on /dev/sda5.  Priority:-1 extents:1 across:1036284k FS
[   39.896548] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   40.399583] systemd-udevd[269]: starting version 204
[   42.291382] lp: driver loaded but no devices found
[   43.324204] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   44.675296] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   44.675384] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input4
[   44.690227] wmi: Mapper loaded
[   45.152212] intel_rng: FWH not detected
[   45.623087] ACPI Warning: 0x00001028-0x0000102f SystemIO conflicts with Region \PMIO 1 (20130517/utaddress-251)
[   45.623100] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   45.623105] ACPI Warning: 0x000011b0-0x000011bf SystemIO conflicts with Region \GPIO 1 (20130517/utaddress-251)
[   45.623112] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   45.623114] ACPI Warning: 0x00001180-0x000011af SystemIO conflicts with Region \GPIO 1 (20130517/utaddress-251)
[   45.623120] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   45.623123] lpc_ich: Resource conflict(s) found affecting gpio_ich
[   45.735917] [drm] Initialized drm 1.1.0 20060810
[   45.802329] r592 0000:0a:09.2: setting latency timer to 64
[   45.802451] r592: driver successfully loaded
[   46.054452] leds_ss4200: no LED devices found
[   46.332551] microcode: CPU0 sig=0x6e8, pf=0x20, revision=0x39
[   46.391725] psmouse serio4: synaptics: Touchpad model: 1, fw: 5.9, id: 0x23aeb3, caps: 0xa04713/0x10008/0x0, board id: 3655, fw id: 28762
[   46.428128] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input5
[   46.462999] [drm] Memory usable by graphics device = 256M
[   46.463011] i915 0000:00:02.0: setting latency timer to 64
[   46.464713] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   46.464720] [drm] Driver supports precise vblank timestamp query.
[   46.464800] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   46.551098] [drm] initialized overlay support
[   46.650853] r852 0000:0a:09.3: setting latency timer to 64
[   46.650961] r852: Non dma capable device detected, dma disabled
[   46.650977] r852: driver loaded successfully
[   47.079088] fbcon: inteldrmfb (fb0) is primary device
[   47.420114] Console: switching to colour frame buffer device 160x50
[   47.426489] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[   47.426492] i915 0000:00:02.0: registered panic notifier
[   47.426502] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   47.427940] snd_hda_intel 0000:00:1b.0: irq 45 for MSI/MSI-X
[   47.501716] SKU: Nid=0x0 sku_cfg=0x0000952d
[   47.501721] SKU: port_connectivity=0x0
[   47.501724] SKU: enable_pcbeep=0x1
[   47.501726] SKU: check_sum=0x00000000
[   47.501728] SKU: customization=0x00000000
[   47.501730] SKU: external_amp=0x5
[   47.501732] SKU: platform_type=0x1
[   47.501734] SKU: swap=0x0
[   47.501736] SKU: override=0x1
[   47.501959] autoconfig: line_outs=1 (0x14/0x0/0x0/0x0/0x0) type:hp
[   47.501962]    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   47.501965]    hp_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   47.501967]    mono: mono_out=0x0
[   47.501970]    dig-out=0x1e/0x0
[   47.501972]    inputs:
[   47.501975]      Mic=0x18
[   47.501977]      Line=0x1a
[   47.501979]      CD=0x1c
[   47.501982] realtek: Enabling init ASM_ID=0x952d CODEC_ID=10ec0883
[   47.580453] input: HDA Intel Line as /devices/pci0000:00/0000:00:1b.0/sound/card0/input6
[   47.580581] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[   47.956064] Registered IR keymap rc-medion-x10-or2x
[   47.956215] input: X10 WTI RF receiver as /devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2:1.0/rc/rc0/input8
[   47.956308] rc0: X10 WTI RF receiver as /devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2:1.0/rc/rc0
[   47.956372] input: X10 WTI RF receiver mouse as /devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2:1.0/input/input9
[   47.956497] usbcore: registered new interface driver ati_remote
[   48.578423] type=1400 audit(1390198864.625:2): apparmor="STATUS" operation="profile_load" parent=388 profile="unconfined" name="/sbin/dhclient" pid=390 comm="apparmor_parser"
[   48.578437] type=1400 audit(1390198864.625:3): apparmor="STATUS" operation="profile_load" parent=388 profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=390 comm="apparmor_parser"
[   48.578446] type=1400 audit(1390198864.625:4): apparmor="STATUS" operation="profile_load" parent=388 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=390 comm="apparmor_parser"
[   48.579465] type=1400 audit(1390198864.625:5): apparmor="STATUS" operation="profile_replace" parent=388 profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=390 comm="apparmor_parser"
[   48.579476] type=1400 audit(1390198864.625:6): apparmor="STATUS" operation="profile_replace" parent=388 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=390 comm="apparmor_parser"
[   48.580542] type=1400 audit(1390198864.629:7): apparmor="STATUS" operation="profile_replace" parent=388 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=390 comm="apparmor_parser"
[   49.046744] acer_wmi: Acer Laptop ACPI-WMI Extras
[   49.047929] acer_wmi: Disabling ACPI video driver
[   49.083363] input: Acer BMA150 accelerometer as /devices/virtual/input/input10
[   49.273283] microcode: CPU1 sig=0x6e8, pf=0x20, revision=0x39
[   49.324848] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[   50.408637] init: failsafe main process (437) killed by TERM signal
[   54.076379] Bluetooth: Core ver 2.16
[   54.076449] NET: Registered protocol family 31
[   54.076452] Bluetooth: HCI device and connection manager initialized
[   54.076846] Bluetooth: HCI socket layer initialized
[   54.076853] Bluetooth: L2CAP socket layer initialized
[   54.076862] Bluetooth: SCO socket layer initialized
[   54.367694] Bluetooth: RFCOMM TTY layer initialized
[   54.367714] Bluetooth: RFCOMM socket layer initialized
[   54.367717] Bluetooth: RFCOMM ver 1.11
[   54.481252] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   54.481259] Bluetooth: BNEP filters: protocol multicast
[   54.481273] Bluetooth: BNEP socket layer initialized
[   54.915443] init: avahi-cups-reload main process (633) terminated with status 1
[   55.250755] ppdev: user-space parallel port driver
[   56.006402] type=1400 audit(1390198872.053:8): apparmor="STATUS" operation="profile_load" parent=645 profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=649 comm="apparmor_parser"
[   56.006417] type=1400 audit(1390198872.053:9): apparmor="STATUS" operation="profile_load" parent=645 profile="unconfined" name="/usr/sbin/cupsd" pid=649 comm="apparmor_parser"
[   56.007595] type=1400 audit(1390198872.053:10): apparmor="STATUS" operation="profile_replace" parent=645 profile="unconfined" name="/usr/sbin/cupsd" pid=649 comm="apparmor_parser"
[   60.404983] r8169 0000:04:00.0 eth0: link down
[   60.405017] r8169 0000:04:00.0 eth0: link down
[   60.405050] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   60.405416] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   61.951540] type=1400 audit(1390198877.997:11): apparmor="STATUS" operation="profile_load" parent=705 profile="unconfined" name="/usr/lib/i386-linux-gnu/lightdm-remote-session-freerdp/freerdp-session-wrapper" pid=711 comm="apparmor_parser"
[   61.951556] type=1400 audit(1390198877.997:12): apparmor="STATUS" operation="profile_load" parent=705 profile="unconfined" name="chromium_browser" pid=711 comm="apparmor_parser"
[   61.951897] type=1400 audit(1390198877.997:13): apparmor="STATUS" operation="profile_load" parent=705 profile="unconfined" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=710 comm="apparmor_parser"
[   61.951909] type=1400 audit(1390198877.997:14): apparmor="STATUS" operation="profile_load" parent=705 profile="unconfined" name="chromium_browser" pid=710 comm="apparmor_parser"
[   61.952683] type=1400 audit(1390198878.001:15): apparmor="STATUS" operation="profile_replace" parent=705 profile="unconfined" name="chromium_browser" pid=711 comm="apparmor_parser"
[   61.952785] type=1400 audit(1390198878.001:16): apparmor="STATUS" operation="profile_replace" parent=705 profile="unconfined" name="chromium_browser" pid=710 comm="apparmor_parser"
[   61.959239] type=1400 audit(1390198878.005:17): apparmor="STATUS" operation="profile_replace" parent=705 profile="unconfined" name="/sbin/dhclient" pid=713 comm="apparmor_parser"
[   61.959254] type=1400 audit(1390198878.005:18): apparmor="STATUS" operation="profile_replace" parent=705 profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=713 comm="apparmor_parser"
[   61.959264] type=1400 audit(1390198878.005:19): apparmor="STATUS" operation="profile_replace" parent=705 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=713 comm="apparmor_parser"
[   61.960323] type=1400 audit(1390198878.009:20): apparmor="STATUS" operation="profile_replace" parent=705 profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=713 comm="apparmor_parser"
[   62.023898] r8169 0000:04:00.0 eth0: link up
[   62.023912] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   64.334812] init: alsa-restore main process (825) terminated with status 99
[   79.572545] init: xbmc main process (1280) terminated with status 1
[   79.572588] init: xbmc main process ended, respawning
[   79.581401] init: xbmc main process (1298) terminated with status 1
[   79.581445] init: xbmc main process ended, respawning
[   79.592713] init: xbmc main process (1300) terminated with status 1
[   79.592757] init: xbmc main process ended, respawning
[   79.605235] init: xbmc main process (1302) terminated with status 1
[   79.605274] init: xbmc main process ended, respawning
[   79.622404] init: xbmc main process (1304) terminated with status 1
[   79.622446] init: xbmc main process ended, respawning
[   79.635561] init: xbmc main process (1306) terminated with status 1
[   79.635603] init: xbmc main process ended, respawning
[   79.648047] init: xbmc main process (1308) terminated with status 1
[   79.648093] init: xbmc main process ended, respawning
[   79.659886] init: xbmc main process (1310) terminated with status 1
[   79.659928] init: xbmc main process ended, respawning
[   79.671285] init: xbmc main process (1312) terminated with status 1
[   79.671327] init: xbmc main process ended, respawning
[   79.685147] init: xbmc main process (1314) terminated with status 1
[   79.685191] init: xbmc main process ended, respawning
[   79.697361] init: xbmc main process (1316) terminated with status 1
[   79.697402] init: xbmc respawning too fast, stopped

```

Boot 2
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 3.11.0-15-generic (buildd@tipua) (gcc version 4.8.1 (Ubuntu/Linaro 4.8.1-10ubuntu8) ) #23-Ubuntu SMP Mon Dec 9 18:16:27 UTC 2013 (Ubuntu 3.11.0-15.23-generic 3.11.10)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] Disabled fast string operations
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009f7ff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009f800-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000dc000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x000000003f68ffff] usable
[    0.000000] BIOS-e820: [mem 0x000000003f690000-0x000000003f6fffff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x000000003f700000-0x000000003fffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000e0000000-0x00000000efffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec0ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed00000-0x00000000fed003ff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed14000-0x00000000fed19fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed1c000-0x00000000fed8ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ff000000-0x00000000ffffffff] reserved
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.4 present.
[    0.000000] DMI: MEDION WIM2120/WIM2120, BIOS R01-B0F    01/15/2007
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] e820: last_pfn = 0x3f690 max_arch_pfn = 0x1000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-DFFFF uncachable
[    0.000000]   E0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask FC0000000 write-back
[    0.000000]   1 base 03F700000 mask FFFF00000 uncachable
[    0.000000]   2 base 03F800000 mask FFF800000 uncachable
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] PAT not supported by CPU.
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 1GB, type WB
[    0.000000] reg 1, base: 1015MB, range: 1MB, type UC
[    0.000000] reg 2, base: 1016MB, range: 8MB, type UC
[    0.000000] total RAM covered: 1015M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K     chunk_size: 16M     num_reg: 3      lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 1GB, type WB
[    0.000000] reg 1, base: 1015MB, range: 1MB, type UC
[    0.000000] reg 2, base: 1016MB, range: 8MB, type UC
[    0.000000] found SMP MP-table at [mem 0x000f68e0-0x000f68ef] mapped at [c00f68e0]
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] initial memory mapped: [mem 0x00000000-0x01ffffff]
[    0.000000] Base memory trampoline at [c009b000] 9b000 size 16384
[    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
[    0.000000]  [mem 0x00000000-0x000fffff] page 4k
[    0.000000] init_memory_mapping: [mem 0x37800000-0x379fffff]
[    0.000000]  [mem 0x37800000-0x379fffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x34000000-0x377fffff]
[    0.000000]  [mem 0x34000000-0x377fffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x00100000-0x33ffffff]
[    0.000000]  [mem 0x00100000-0x001fffff] page 4k
[    0.000000]  [mem 0x00200000-0x33ffffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x37a00000-0x37bfdfff]
[    0.000000]  [mem 0x37a00000-0x37bfdfff] page 4k
[    0.000000] BRK [0x01b49000, 0x01b49fff] PGTABLE
[    0.000000] RAMDISK: [mem 0x35f6c000-0x36fadfff]
[    0.000000] ACPI: RSDP 000f6770 00014 (v00 PTLTD )
[    0.000000] ACPI: RSDT 3f6916cf 00048 (v01 MEDION MEDIONAG 06040000 ZNEB 00000000)
[    0.000000] ACPI: FACP 3f697caa 00074 (v01 INTEL  CALISTGA 06040000 LOHR 00000065)
[    0.000000] ACPI: DSDT 3f692298 05A12 (v01 INTEL  CALISTGA 06040000 MSFT 0100000E)
[    0.000000] ACPI: FACS 3f698fc0 00040
[    0.000000] ACPI: APIC 3f697d1e 00068 (v01 INTEL  CALISTGA 06040000 LOHR 00000065)
[    0.000000] ACPI: HPET 3f697d86 00038 (v01 INTEL  CALISTGA 06040000 LOHR 00000065)
[    0.000000] ACPI: MCFG 3f697dbe 0003C (v01 INTEL  CALISTGA 06040000 LOHR 00000065)
[    0.000000] ACPI: SLIC 3f697dfa 00176 (v01 MEDION MEDIONAG 06040000 BENZ 00000001)
[    0.000000] ACPI: APIC 3f697f70 00068 (v01 PTLTD  ? APIC   06040000  LTP 00000000)
[    0.000000] ACPI: BOOT 3f697fd8 00028 (v01 PTLTD  $SBFTBL$ 06040000  LTP 00000001)
[    0.000000] ACPI: SSDT 3f69208e 0020A (v01 SataRe SataAhci 00001000 INTL 20050624)
[    0.000000] ACPI: SSDT 3f691717 004F6 (v01  PmRef    CpuPm 00003000 INTL 20050624)
[    0.000000] ACPI: BIOS bug: multiple APIC/MADT found, using 0
[    0.000000] ACPI: If "acpi_apic_instance=2" works better, notify linux-acpi@vger.kernel.org
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 122MB HIGHMEM available.
[    0.000000] 891MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 37bfe000
[    0.000000]   low ram: 0 - 37bfe000
[    0.000000] BRK [0x01b4a000, 0x01b4afff] PGTABLE
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00001000-0x00ffffff]
[    0.000000]   Normal   [mem 0x01000000-0x37bfdfff]
[    0.000000]   HighMem  [mem 0x37bfe000-0x3f68ffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00001000-0x0009efff]
[    0.000000]   node   0: [mem 0x00100000-0x3f68ffff]
[    0.000000] On node 0 totalpages: 259630
[    0.000000] free_area_init_node: node 0, pgdat c1958bc0, node_mem_map f740e020
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3998 pages, LIFO batch:0
[    0.000000]   Normal zone: 1752 pages used for memmap
[    0.000000]   Normal zone: 224254 pages, LIFO batch:31
[    0.000000]   HighMem zone: 246 pages used for memmap
[    0.000000]   HighMem zone: 31378 pages, LIFO batch:7
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
[    0.000000] smpboot: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: [mem 0x0009f000-0x0009ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dbfff]
[    0.000000] PM: Registered nosave memory: [mem 0x000dc000-0x000fffff]
[    0.000000] e820: [mem 0x40000000-0xdfffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @f73ec000 s36288 r0 d21056 u57344
[    0.000000] pcpu-alloc: s36288 r0 d21056 u57344 alloc=14*4096
[    0.000000] pcpu-alloc: [0] 0 [0] 1 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 257846
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.11.0-15-generic root=UUID=b1b16843-0173-40ed-a37c-8643572cc543 ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] allocated 2077816 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (00037bfe:0003f690)
[    0.000000] Memory: 999140K/1038520K available (6358K kernel code, 611K rwdata, 2692K rodata, 880K init, 908K bss, 39380K reserved, 125512K highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff14000 - 0xfffff000   ( 940 kB)
[    0.000000]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
[    0.000000]     vmalloc : 0xf83fe000 - 0xffbfe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf7bfe000   ( 891 MB)
[    0.000000]       .init : 0xc1972000 - 0xc1a4e000   ( 880 kB)
[    0.000000]       .data : 0xc1635ee4 - 0xc1971f80   (3312 kB)
[    0.000000]       .text : 0xc1000000 - 0xc1635ee4   (6359 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU restricting CPUs from NR_CPUS=8 to nr_cpu_ids=2.
[    0.000000] NR_IRQS:2304 nr_irqs:512 16
[    0.000000] CPU 0 irqstacks, hard=f5808000 soft=f580a000
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.000000] tsc: Detected 1662.429 MHz processor
[    0.004002] Calibrating delay loop (skipped), value calculated using timer frequency.. 3324.85 BogoMIPS (lpj=6649716)
[    0.004008] pid_max: default: 32768 minimum: 301
[    0.004054] Security Framework initialized
[    0.004083] AppArmor: AppArmor initialized
[    0.004085] Yama: becoming mindful.
[    0.004187] Mount-cache hash table entries: 512
[    0.004564] Initializing cgroup subsys memory
[    0.004581] Initializing cgroup subsys devices
[    0.004585] Initializing cgroup subsys freezer
[    0.004589] Initializing cgroup subsys blkio
[    0.004592] Initializing cgroup subsys perf_event
[    0.004598] Initializing cgroup subsys hugetlb
[    0.004634] Disabled fast string operations
[    0.004641] CPU: Physical Processor ID: 0
[    0.004644] CPU: Processor Core ID: 0
[    0.004648] mce: CPU supports 6 MCE banks
[    0.004661] CPU0: Thermal monitoring enabled (TM2)
[    0.004677] Last level iTLB entries: 4KB 128, 2MB 0, 4MB 2
[    0.004677] Last level dTLB entries: 4KB 128, 2MB 0, 4MB 8
[    0.004677] tlb_flushall_shift: 6
[    0.005168] Freeing SMP alternatives memory: 28K (c1a4e000 - c1a55000)
[    0.011126] ACPI: Core revision 20130517
[    0.016958] ACPI: All ACPI Tables successfully acquired
[    0.020013] ftrace: allocating 27182 entries in 54 pages
[    0.032133] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.032611] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.074790] smpboot: CPU0: Genuine Intel(R) CPU           T2300  @ 1.66GHz (fam: 06, model: 0e, stepping: 08)
[    0.076000] Performance Events: Core events, core PMU driver.
[    0.076000] ... version:                1
[    0.076000] ... bit width:              40
[    0.076000] ... generic registers:      2
[    0.076000] ... value mask:             000000ffffffffff
[    0.076000] ... max period:             000000007fffffff
[    0.076000] ... fixed-purpose events:   0
[    0.076000] ... event mask:             0000000000000003
[    0.076000] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.076000] CPU 1 irqstacks, hard=f58f0000 soft=f58f2000
[    0.076000] smpboot: Booting Node   0, Processors  #1 OK
[    0.008000] Initializing CPU#1
[    0.008000] Disabled fast string operations
[    0.087803] Brought up 2 CPUs
[    0.087811] smpboot: Total of 2 processors activated (6649.71 BogoMIPS)
[    0.092105] devtmpfs: initialized
[    0.092362] EVM: security.selinux
[    0.092365] EVM: security.SMACK64
[    0.092367] EVM: security.capability
[    0.092394] PM: Registering ACPI NVS region [mem 0x3f690000-0x3f6fffff] (458752 bytes)
[    0.094032] regulator-dummy: no parameters
[    0.094081] RTC time:  6:37:43, date: 01/20/14
[    0.094152] NET: Registered protocol family 16
[    0.094401] EISA bus registered
[    0.094519] ACPI: bus type PCI registered
[    0.094524] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.094615] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.094620] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    0.094623] PCI: Using MMCONFIG for extended config space
[    0.094625] PCI: Using configuration type 1 for base access
[    0.096105] bio: create slab <bio-0> at 0
[    0.096142] ACPI: Added _OSI(Module Device)
[    0.096147] ACPI: Added _OSI(Processor Device)
[    0.096150] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.096153] ACPI: Added _OSI(Processor Aggregator Device)
[    0.098202] ACPI: EC: Look up EC in DSDT
[    0.099651] ACPI: SSDT 3f691e5d 001A8 (v01  PmRef  Cpu0Ist 00003000 INTL 20050624)
[    0.100165] ACPI: Dynamic OEM Table Load:
[    0.100170] ACPI: SSDT   (null) 001A8 (v01  PmRef  Cpu0Ist 00003000 INTL 20050624)
[    0.100319] ACPI: SSDT 3f691c0d 001CB (v01  PmRef  Cpu0Cst 00003001 INTL 20050624)
[    0.100806] ACPI: Dynamic OEM Table Load:
[    0.100810] ACPI: SSDT   (null) 001CB (v01  PmRef  Cpu0Cst 00003001 INTL 20050624)
[    0.101176] ACPI: SSDT 3f692005 00089 (v01  PmRef  Cpu1Ist 00003000 INTL 20050624)
[    0.101675] ACPI: Dynamic OEM Table Load:
[    0.101680] ACPI: SSDT   (null) 00089 (v01  PmRef  Cpu1Ist 00003000 INTL 20050624)
[    0.101810] ACPI: SSDT 3f691dd8 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20050624)
[    0.102300] ACPI: Dynamic OEM Table Load:
[    0.102304] ACPI: SSDT   (null) 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20050624)
[    0.108231] ACPI: Interpreter enabled
[    0.108245] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20130517/hwxface-571)
[    0.108253] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20130517/hwxface-571)
[    0.108277] ACPI: (supports S0 S3 S4 S5)
[    0.108279] ACPI: Using IOAPIC for interrupt routing
[    0.108321] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
[    0.108492] ACPI: No dock devices found.
[    0.122647] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.122656] acpi PNP0A08:00: ACPI _OSC support notification failed, disabling PCIe ASPM
[    0.122660] acpi PNP0A08:00: Unable to request _OSC control (_OSC support mask: 0x08)
[    0.123535] acpi PNP0A08:00: host bridge window [io  0x0000-0x0cf7] (ignored)
[    0.123540] acpi PNP0A08:00: host bridge window [io  0x0d00-0xffff] (ignored)
[    0.123544] acpi PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)
[    0.123548] acpi PNP0A08:00: host bridge window [mem 0x000d0000-0x000d3fff] (ignored)
[    0.123552] acpi PNP0A08:00: host bridge window [mem 0x000d4000-0x000d7fff] (ignored)
[    0.123556] acpi PNP0A08:00: host bridge window [mem 0x000d8000-0x000dbfff] (ignored)
[    0.123561] acpi PNP0A08:00: host bridge window [mem 0x40000000-0xfebfffff] (ignored)
[    0.123564] PCI: root bus 00: using default resources
[    0.123784] PCI host bridge to bus 0000:00
[    0.123789] pci_bus 0000:00: root bus resource [bus 00-ff]
[    0.123793] pci_bus 0000:00: root bus resource [io  0x0000-0xffff]
[    0.123797] pci_bus 0000:00: root bus resource [mem 0x00000000-0xffffffff]
[    0.123813] pci 0000:00:00.0: [8086:27a0] type 00 class 0x060000
[    0.123998] pci 0000:00:02.0: [8086:27a2] type 00 class 0x030000
[    0.124019] pci 0000:00:02.0: reg 0x10: [mem 0xd8100000-0xd817ffff]
[    0.124029] pci 0000:00:02.0: reg 0x14: [io  0x1800-0x1807]
[    0.124039] pci 0000:00:02.0: reg 0x18: [mem 0xc0000000-0xcfffffff pref]
[    0.124049] pci 0000:00:02.0: reg 0x1c: [mem 0xd8200000-0xd823ffff]
[    0.124222] pci 0000:00:02.1: [8086:27a6] type 00 class 0x038000
[    0.124237] pci 0000:00:02.1: reg 0x10: [mem 0xd8180000-0xd81fffff]
[    0.124481] pci 0000:00:1b.0: [8086:27d8] type 00 class 0x040300
[    0.124509] pci 0000:00:1b.0: reg 0x10: [mem 0xd8440000-0xd8443fff 64bit]
[    0.124631] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.124734] pci 0000:00:1b.0: System wakeup disabled by ACPI
[    0.124800] pci 0000:00:1c.0: [8086:27d0] type 01 class 0x060400
[    0.124927] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.125090] pci 0000:00:1c.1: [8086:27d2] type 01 class 0x060400
[    0.125217] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.125381] pci 0000:00:1c.3: [8086:27d6] type 01 class 0x060400
[    0.125507] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.125672] pci 0000:00:1d.0: [8086:27c8] type 00 class 0x0c0300
[    0.125739] pci 0000:00:1d.0: reg 0x20: [io  0x1820-0x183f]
[    0.125900] pci 0000:00:1d.1: [8086:27c9] type 00 class 0x0c0300
[    0.125966] pci 0000:00:1d.1: reg 0x20: [io  0x1840-0x185f]
[    0.126129] pci 0000:00:1d.2: [8086:27ca] type 00 class 0x0c0300
[    0.126195] pci 0000:00:1d.2: reg 0x20: [io  0x1860-0x187f]
[    0.126356] pci 0000:00:1d.3: [8086:27cb] type 00 class 0x0c0300
[    0.126421] pci 0000:00:1d.3: reg 0x20: [io  0x1880-0x189f]
[    0.126598] pci 0000:00:1d.7: [8086:27cc] type 00 class 0x0c0320
[    0.126627] pci 0000:00:1d.7: reg 0x10: [mem 0xd8444000-0xd84443ff]
[    0.126750] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.126902] pci 0000:00:1e.0: [8086:2448] type 01 class 0x060401
[    0.127129] pci 0000:00:1f.0: [8086:27b9] type 00 class 0x060100
[    0.127258] pci 0000:00:1f.0: address space collision: [io  0x1000-0x107f] conflicts with ACPI CPU throttle [??? 0x00001010-0x00001015 flags 0x80000000]
[    0.127267] pci 0000:00:1f.0: quirk: [io  0x1180-0x11bf] claimed by ICH6 GPIO
[    0.127275] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 2 PIO at 1200 (mask 0007)
[    0.127455] pci 0000:00:1f.1: [8086:27df] type 00 class 0x01018a
[    0.127476] pci 0000:00:1f.1: reg 0x10: [io  0x0000-0x0007]
[    0.127491] pci 0000:00:1f.1: reg 0x14: [io  0x0000-0x0003]
[    0.127506] pci 0000:00:1f.1: reg 0x18: [io  0x0000-0x0007]
[    0.127522] pci 0000:00:1f.1: reg 0x1c: [io  0x0000-0x0003]
[    0.127537] pci 0000:00:1f.1: reg 0x20: [io  0x1810-0x181f]
[    0.127711] pci 0000:00:1f.2: [8086:27c5] type 00 class 0x010601
[    0.127740] pci 0000:00:1f.2: reg 0x10: [io  0x18d0-0x18d7]
[    0.127755] pci 0000:00:1f.2: reg 0x14: [io  0x18c4-0x18c7]
[    0.127770] pci 0000:00:1f.2: reg 0x18: [io  0x18c8-0x18cf]
[    0.127785] pci 0000:00:1f.2: reg 0x1c: [io  0x18c0-0x18c3]
[    0.127800] pci 0000:00:1f.2: reg 0x20: [io  0x18b0-0x18bf]
[    0.127816] pci 0000:00:1f.2: reg 0x24: [mem 0xd8444400-0xd84447ff]
[    0.127884] pci 0000:00:1f.2: PME# supported from D3hot
[    0.128040] pci 0000:00:1f.3: [8086:27da] type 00 class 0x0c0500
[    0.128123] pci 0000:00:1f.3: reg 0x20: [io  0x18e0-0x18ff]
[    0.128444] acpiphp: Slot [1] registered
[    0.128457] pci 0000:00:1c.0: PCI bridge to [bus 02-03]
[    0.128464] pci 0000:00:1c.0:   bridge window [io  0x2000-0x2fff]
[    0.128472] pci 0000:00:1c.0:   bridge window [mem 0xd4000000-0xd5ffffff]
[    0.128482] pci 0000:00:1c.0:   bridge window [mem 0xd0000000-0xd1ffffff 64bit pref]
[    0.128626] pci 0000:04:00.0: [10ec:8136] type 00 class 0x020000
[    0.128656] pci 0000:04:00.0: reg 0x10: [io  0x3000-0x30ff]
[    0.128704] pci 0000:04:00.0: reg 0x18: [mem 0xd6000000-0xd6000fff 64bit]
[    0.128759] pci 0000:04:00.0: reg 0x30: [mem 0x00000000-0x0001ffff pref]
[    0.128883] pci 0000:04:00.0: supports D1 D2
[    0.128886] pci 0000:04:00.0: PME# supported from D1 D2 D3hot D3cold
[    0.128932] pci 0000:04:00.0: System wakeup disabled by ACPI
[    0.128988] pci 0000:04:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    0.129005] pci 0000:00:1c.1: PCI bridge to [bus 04-05]
[    0.129012] pci 0000:00:1c.1:   bridge window [io  0x3000-0x3fff]
[    0.129020] pci 0000:00:1c.1:   bridge window [mem 0xd6000000-0xd7ffffff]
[    0.129030] pci 0000:00:1c.1:   bridge window [mem 0xd2000000-0xd3ffffff 64bit pref]
[    0.129139] pci 0000:00:1c.3: PCI bridge to [bus 06]
[    0.129253] pci 0000:0a:09.0: [1180:0832] type 00 class 0x0c0010
[    0.129272] pci 0000:0a:09.0: proprietary Ricoh MMC controller disabled (via firewire function)
[    0.129276] pci 0000:0a:09.0: MMC cards are now supported by standard SDHCI controller
[    0.129296] pci 0000:0a:09.0: reg 0x10: [mem 0xd8000000-0xd80007ff]
[    0.129409] pci 0000:0a:09.0: supports D1 D2
[    0.129413] pci 0000:0a:09.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.129493] pci 0000:0a:09.1: [1180:0822] type 00 class 0x080500
[    0.129521] pci 0000:0a:09.1: reg 0x10: [mem 0xd8000800-0xd80008ff]
[    0.129634] pci 0000:0a:09.1: supports D1 D2
[    0.129637] pci 0000:0a:09.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.129717] pci 0000:0a:09.2: [1180:0592] type 00 class 0x088000
[    0.129745] pci 0000:0a:09.2: reg 0x10: [mem 0xd8000c00-0xd8000cff]
[    0.129859] pci 0000:0a:09.2: supports D1 D2
[    0.129863] pci 0000:0a:09.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.129946] pci 0000:0a:09.3: [1180:0852] type 00 class 0x088000
[    0.129972] pci 0000:0a:09.3: reg 0x10: [mem 0xd8001000-0xd80010ff]
[    0.130087] pci 0000:0a:09.3: supports D1 D2
[    0.130091] pci 0000:0a:09.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.130207] pci 0000:00:1e.0: PCI bridge to [bus 0a] (subtractive decode)
[    0.130217] pci 0000:00:1e.0:   bridge window [mem 0xd8000000-0xd80fffff]
[    0.130228] pci 0000:00:1e.0:   bridge window [io  0x0000-0xffff] (subtractive decode)
[    0.130232] pci 0000:00:1e.0:   bridge window [mem 0x00000000-0xffffffff] (subtractive decode)
[    0.130265] pci_bus 0000:00: on NUMA node 0
[    0.131112] ACPI: PCI Interrupt Link [LNKA] (IRQs 10 11) *7
[    0.131213] ACPI: PCI Interrupt Link [LNKB] (IRQs 10 11) *3
[    0.131311] ACPI: PCI Interrupt Link [LNKC] (IRQs 10 *11)
[    0.131407] ACPI: PCI Interrupt Link [LNKD] (IRQs *10 11)
[    0.131504] ACPI: PCI Interrupt Link [LNKE] (IRQs 10 11) *0, disabled.
[    0.131602] ACPI: PCI Interrupt Link [LNKF] (IRQs *10 11)
[    0.131698] ACPI: PCI Interrupt Link [LNKG] (IRQs 10 11) *0, disabled.
[    0.131796] ACPI: PCI Interrupt Link [LNKH] (IRQs 10 11) *5
[    0.132565] ACPI: Enabled 9 GPEs in block 00 to 1F
[    0.132580] ACPI: \_SB_.PCI0: notify handler is installed
[    0.132661] Found 1 acpi root devices
[    0.132758] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
[    0.132880] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.132880] vgaarb: loaded
[    0.132880] vgaarb: bridge control possible 0000:00:02.0
[    0.132880] SCSI subsystem initialized
[    0.132880] ACPI: bus type ATA registered
[    0.132880] libata version 3.00 loaded.
[    0.132880] ACPI: bus type USB registered
[    0.132880] usbcore: registered new interface driver usbfs
[    0.132880] usbcore: registered new interface driver hub
[    0.132880] usbcore: registered new device driver usb
[    0.132880] PCI: Using ACPI for IRQ routing
[    0.141979] PCI: pci_cache_line_size set to 64 bytes
[    0.142074] e820: reserve RAM buffer [mem 0x0009f800-0x0009ffff]
[    0.142081] e820: reserve RAM buffer [mem 0x3f690000-0x3fffffff]
[    0.142234] NetLabel: Initializing
[    0.142237] NetLabel:  domain hash size = 128
[    0.142239] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.142257] NetLabel:  unlabeled traffic allowed by default
[    0.144134] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.144142] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.144149] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.148031] Switched to clocksource hpet
[    0.160846] AppArmor: AppArmor Filesystem Enabled
[    0.160899] pnp: PnP ACPI init
[    0.160925] ACPI: bus type PNP registered
[    0.161113] system 00:00: [mem 0xe0000000-0xefffffff] has been reserved
[    0.161119] system 00:00: [mem 0xfed14000-0xfed17fff] has been reserved
[    0.161123] system 00:00: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.161128] system 00:00: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.161133] system 00:00: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.161137] system 00:00: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.161142] system 00:00: [mem 0xfed40000-0xfed44fff] has been reserved
[    0.161147] system 00:00: [mem 0xfed45000-0xfed8ffff] has been reserved
[    0.161154] system 00:00: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.162946] pnp 00:01: [dma 4]
[    0.162993] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.163054] pnp 00:02: Plug and Play ACPI device, IDs INT0800 (active)
[    0.163218] system 00:03: [mem 0xfed00000-0xfed003ff] has been reserved
[    0.163225] system 00:03: Plug and Play ACPI device, IDs PNP0103 PNP0c01 (active)
[    0.163305] pnp 00:04: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.163402] system 00:05: [io  0x0800-0x080f] has been reserved
[    0.163408] system 00:05: [io  0x1000-0x107f] could not be reserved
[    0.163412] system 00:05: [io  0x1180-0x11bf] has been reserved
[    0.163417] system 00:05: [io  0x1640-0x164f] has been reserved
[    0.163421] system 00:05: [io  0x1200-0x120f] has been reserved
[    0.163427] system 00:05: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.163525] system 00:06: [io  0x06a0-0x06af] has been reserved
[    0.163530] system 00:06: [io  0x06b0-0x06ff] has been reserved
[    0.163535] system 00:06: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.163601] pnp 00:07: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.163668] pnp 00:08: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.163731] pnp 00:09: Plug and Play ACPI device, IDs SYN030b SYN0300 PNP0f13 (active)
[    0.163764] pnp: PnP ACPI: found 10 devices
[    0.163766] ACPI: bus type PNP unregistered
[    0.163771] PnPBIOS: Disabled by ACPI PNP
[    0.202212] pci 0000:00:1c.3: bridge window [io  0x1000-0x0fff] to [bus 06] add_size 1000
[    0.202220] pci 0000:00:1c.3: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 06] add_size 200000
[    0.202225] pci 0000:00:1c.3: bridge window [mem 0x00100000-0x000fffff] to [bus 06] add_size 200000
[    0.202244] pci 0000:00:1f.0: BAR 13: [io  0x1000-0x107f] has bogus alignment
[    0.202250] pci 0000:00:1c.3: res[14]=[mem 0x00100000-0x000fffff] get_res_add_size add_size 200000
[    0.202255] pci 0000:00:1c.3: res[15]=[mem 0x00100000-0x000fffff 64bit pref] get_res_add_size add_size 200000
[    0.202259] pci 0000:00:1c.3: res[13]=[io  0x1000-0x0fff] get_res_add_size add_size 1000
[    0.202268] pci 0000:00:1c.3: BAR 14: assigned [mem 0x40000000-0x401fffff]
[    0.202273] pci 0000:00:1c.3: BAR 15: assigned [mem 0x40200000-0x403fffff 64bit pref]
[    0.202280] pci 0000:00:1c.3: BAR 13: assigned [io  0x4000-0x4fff]
[    0.202285] pci 0000:00:1c.0: PCI bridge to [bus 02-03]
[    0.202291] pci 0000:00:1c.0:   bridge window [io  0x2000-0x2fff]
[    0.202300] pci 0000:00:1c.0:   bridge window [mem 0xd4000000-0xd5ffffff]
[    0.202307] pci 0000:00:1c.0:   bridge window [mem 0xd0000000-0xd1ffffff 64bit pref]
[    0.202319] pci 0000:04:00.0: BAR 6: assigned [mem 0xd2000000-0xd201ffff pref]
[    0.202324] pci 0000:00:1c.1: PCI bridge to [bus 04-05]
[    0.202329] pci 0000:00:1c.1:   bridge window [io  0x3000-0x3fff]
[    0.202338] pci 0000:00:1c.1:   bridge window [mem 0xd6000000-0xd7ffffff]
[    0.202345] pci 0000:00:1c.1:   bridge window [mem 0xd2000000-0xd3ffffff 64bit pref]
[    0.202355] pci 0000:00:1c.3: PCI bridge to [bus 06]
[    0.202361] pci 0000:00:1c.3:   bridge window [io  0x4000-0x4fff]
[    0.202370] pci 0000:00:1c.3:   bridge window [mem 0x40000000-0x401fffff]
[    0.202377] pci 0000:00:1c.3:   bridge window [mem 0x40200000-0x403fffff 64bit pref]
[    0.202388] pci 0000:00:1e.0: PCI bridge to [bus 0a]
[    0.202396] pci 0000:00:1e.0:   bridge window [mem 0xd8000000-0xd80fffff]
[    0.202984] pci 0000:00:1e.0: setting latency timer to 64
[    0.202991] pci_bus 0000:00: resource 4 [io  0x0000-0xffff]
[    0.202995] pci_bus 0000:00: resource 5 [mem 0x00000000-0xffffffff]
[    0.202999] pci_bus 0000:02: resource 0 [io  0x2000-0x2fff]
[    0.203003] pci_bus 0000:02: resource 1 [mem 0xd4000000-0xd5ffffff]
[    0.203007] pci_bus 0000:02: resource 2 [mem 0xd0000000-0xd1ffffff 64bit pref]
[    0.203011] pci_bus 0000:04: resource 0 [io  0x3000-0x3fff]
[    0.203015] pci_bus 0000:04: resource 1 [mem 0xd6000000-0xd7ffffff]
[    0.203019] pci_bus 0000:04: resource 2 [mem 0xd2000000-0xd3ffffff 64bit pref]
[    0.203023] pci_bus 0000:06: resource 0 [io  0x4000-0x4fff]
[    0.203027] pci_bus 0000:06: resource 1 [mem 0x40000000-0x401fffff]
[    0.203031] pci_bus 0000:06: resource 2 [mem 0x40200000-0x403fffff 64bit pref]
[    0.203035] pci_bus 0000:0a: resource 1 [mem 0xd8000000-0xd80fffff]
[    0.203039] pci_bus 0000:0a: resource 4 [io  0x0000-0xffff]
[    0.203043] pci_bus 0000:0a: resource 5 [mem 0x00000000-0xffffffff]
[    0.203092] NET: Registered protocol family 2
[    0.203334] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
[    0.203386] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[    0.203435] TCP: Hash tables configured (established 8192 bind 8192)
[    0.203472] TCP: reno registered
[    0.203477] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.203490] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.203586] NET: Registered protocol family 1
[    0.203608] pci 0000:00:02.0: Boot video device
[    0.205520] PCI: CLS 64 bytes, default 64
[    0.205586] Trying to unpack rootfs image as initramfs...
[    0.701306] Freeing initrd memory: 16648K (f5f6c000 - f6fae000)
[    0.701426] Simple Boot Flag at 0x36 set to 0x1
[    0.701632] Scanning for low memory corruption every 60 seconds
[    0.702032] Initialise module verification
[    0.702107] audit: initializing netlink socket (disabled)
[    0.702128] type=2000 audit(1390199863.700:1): initialized
[    0.736150] bounce pool size: 64 pages
[    0.736177] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.738558] zbud: loaded
[    0.738646] VFS: Disk quotas dquot_6.5.2
[    0.738729] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.739636] fuse init (API version 7.22)
[    0.739793] msgmni has been set to 1738
[    0.740685] Key type asymmetric registered
[    0.740689] Asymmetric key parser 'x509' registered
[    0.740745] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    0.740805] io scheduler noop registered
[    0.740808] io scheduler deadline registered (default)
[    0.740857] io scheduler cfq registered
[    0.741063] pcieport 0000:00:1c.0: irq 40 for MSI/MSI-X
[    0.741187] pcieport 0000:00:1c.1: irq 41 for MSI/MSI-X
[    0.741304] pcieport 0000:00:1c.3: irq 42 for MSI/MSI-X
[    0.741436] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.741463] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.741605] intel_idle: does not run on family 6 model 14
[    0.742747] ACPI: AC Adapter [ADP1] (on-line)
[    0.742878] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    0.744032] ACPI: Lid Switch [LID0]
[    0.744098] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1
[    0.744105] ACPI: Sleep Button [SLPB]
[    0.744185] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.744190] ACPI: Power Button [PWRF]
[    0.744294] ACPI: Requesting acpi_cpufreq
[    0.744765] tsc: Marking TSC unstable due to TSC halts in idle
[    0.744781] ACPI: acpi_idle registered with cpuidle
[    0.752270] thermal LNXTHERM:00: registered as thermal_zone0
[    0.752274] ACPI: Thermal Zone [TZS0] (31 C)
[    0.756173] thermal LNXTHERM:01: registered as thermal_zone1
[    0.756177] ACPI: Thermal Zone [TZS1] (36 C)
[    0.756246] GHES: HEST is not enabled!
[    0.756334] isapnp: Scanning for PnP cards...
[    0.760121] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.766695] Linux agpgart interface v0.103
[    0.766825] agpgart-intel 0000:00:00.0: Intel 945GM Chipset
[    0.766911] agpgart-intel 0000:00:00.0: detected gtt size: 262144K total, 262144K mappable
[    0.767505] agpgart-intel 0000:00:00.0: detected 8192K stolen memory
[    0.767683] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xc0000000
[    0.770232] brd: module loaded
[    0.771517] loop: module loaded
[    0.771726] ata_piix 0000:00:1f.1: version 2.13
[    0.772040] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.772556] scsi0 : ata_piix
[    0.776036] scsi1 : ata_piix
[    0.776122] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1810 irq 14
[    0.776126] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1818 irq 15
[    0.776644] libphy: Fixed MDIO Bus: probed
[    0.776818] tun: Universal TUN/TAP device driver, 1.6
[    0.776820] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.776905] PPP generic driver version 2.4.2
[    0.776969] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.776973] ehci-pci: EHCI PCI platform driver
[    0.777194] ehci-pci 0000:00:1d.7: setting latency timer to 64
[    0.777213] ehci-pci 0000:00:1d.7: EHCI Host Controller
[    0.777223] ehci-pci 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.777243] ehci-pci 0000:00:1d.7: debug port 1
[    0.781159] ehci-pci 0000:00:1d.7: cache line size of 64 is not supported
[    0.781191] ehci-pci 0000:00:1d.7: irq 23, io mem 0xd8444000
[    0.781402] ata2: port disabled--ignoring
[    0.792030] ehci-pci 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.792066] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    0.792070] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.792074] usb usb1: Product: EHCI Host Controller
[    0.792078] usb usb1: Manufacturer: Linux 3.11.0-15-generic ehci_hcd
[    0.792082] usb usb1: SerialNumber: 0000:00:1d.7
[    0.792249] hub 1-0:1.0: USB hub found
[    0.792257] hub 1-0:1.0: 8 ports detected
[    0.792532] ehci-platform: EHCI generic platform driver
[    0.792546] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.792548] ohci-pci: OHCI PCI platform driver
[    0.792568] ohci-platform: OHCI generic platform driver
[    0.792580] uhci_hcd: USB Universal Host Controller Interface driver
[    0.792795] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.792801] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.792809] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.792843] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001820
[    0.792890] usb usb2: New USB device found, idVendor=1d6b, idProduct=0001
[    0.792894] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.792898] usb usb2: Product: UHCI Host Controller
[    0.792901] usb usb2: Manufacturer: Linux 3.11.0-15-generic uhci_hcd
[    0.792905] usb usb2: SerialNumber: 0000:00:1d.0
[    0.793065] hub 2-0:1.0: USB hub found
[    0.793072] hub 2-0:1.0: 2 ports detected
[    0.793396] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.793404] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.793412] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.793461] uhci_hcd 0000:00:1d.1: irq 17, io base 0x00001840
[    0.793509] usb usb3: New USB device found, idVendor=1d6b, idProduct=0001
[    0.793513] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.793516] usb usb3: Product: UHCI Host Controller
[    0.793520] usb usb3: Manufacturer: Linux 3.11.0-15-generic uhci_hcd
[    0.793524] usb usb3: SerialNumber: 0000:00:1d.1
[    0.793673] hub 3-0:1.0: USB hub found
[    0.793680] hub 3-0:1.0: 2 ports detected
[    0.794008] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.794014] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.794022] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.794071] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001860
[    0.794116] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
[    0.794121] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.794124] usb usb4: Product: UHCI Host Controller
[    0.794128] usb usb4: Manufacturer: Linux 3.11.0-15-generic uhci_hcd
[    0.794132] usb usb4: SerialNumber: 0000:00:1d.2
[    0.794280] hub 4-0:1.0: USB hub found
[    0.794291] hub 4-0:1.0: 2 ports detected
[    0.794631] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    0.794639] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    0.794647] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    0.794710] uhci_hcd 0000:00:1d.3: irq 19, io base 0x00001880
[    0.794767] usb usb5: New USB device found, idVendor=1d6b, idProduct=0001
[    0.794771] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.794774] usb usb5: Product: UHCI Host Controller
[    0.794778] usb usb5: Manufacturer: Linux 3.11.0-15-generic uhci_hcd
[    0.794782] usb usb5: SerialNumber: 0000:00:1d.3
[    0.794935] hub 5-0:1.0: USB hub found
[    0.794942] hub 5-0:1.0: 2 ports detected
[    0.795173] i8042: PNP: PS/2 Controller [PNP0303:KBD0,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.797794] i8042: Detected active multiplexing controller, rev 1.1
[    0.797900] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.797909] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    0.797953] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    0.797993] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    0.798030] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    0.798248] mousedev: PS/2 mouse device common for all mice
[    0.798488] rtc_cmos 00:07: RTC can wake from S4
[    0.798752] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
[    0.798806] rtc_cmos 00:07: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    0.798917] device-mapper: uevent: version 1.0.3
[    0.799057] device-mapper: ioctl: 4.25.0-ioctl (2013-06-26) initialised: dm-devel@redhat.com
[    0.799090] platform eisa.0: Probing EISA bus 0
[    0.799123] platform eisa.0: EISA: Detected 0 cards
[    0.799136] cpufreq-nforce2: No nForce2 chipset.
[    0.799206] cpuidle: using governor ladder
[    0.799326] cpuidle: using governor menu
[    0.799342] ledtrig-cpu: registered to indicate activity on CPUs
[    0.799508] TCP: cubic registered
[    0.799678] NET: Registered protocol family 10
[    0.800041] NET: Registered protocol family 17
[    0.800072] Key type dns_resolver registered
[    0.800350] Using IPI No-Shortcut mode
[    0.800469] PM: Hibernation image not present or could not be loaded.
[    0.800475] Loading module verification certificates
[    0.806790] MODSIGN: Loaded cert 'Magrathea: Glacier signing key: 20cb30850ee856675c288816dd8cff0153e91a4b'
[    0.806811] registered taskstats version 1
[    0.807016] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    0.816794] ACPI: Battery Slot [BAT0] (battery present)
[    0.831106] Key type trusted registered
[    0.833998] Key type encrypted registered
[    0.836882] AppArmor: AppArmor sha1 policy hashing enabled
[    0.837359]   Magic number: 14:685:620
[    0.837490] rtc_cmos 00:07: setting system clock to 2014-01-20 06:37:44 UTC (1390199864)
[    0.837864] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.837867] EDD information not available.
[    0.944420] ata1.00: ATAPI: HL-DT-ST DVDRAM GSA-T10N, TM01, max UDMA/33
[    0.960295] ata1.00: configured for UDMA/33
[    1.112548] isapnp: No Plug & Play device found
[    1.116445] scsi 0:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-T10N  TM01 PQ: 0 ANSI: 5
[    1.121793] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.121798] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.121993] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    1.122137] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    1.122739] Freeing unused kernel memory: 880K (c1972000 - c1a4e000)
[    1.122838] Write protecting the kernel text: 6360k
[    1.122974] Write protecting the kernel read-only data: 2700k
[    1.122976] NX-protecting the kernel data: 5928k
[    1.140493] systemd-udevd[100]: starting version 204
[    1.195825] sdhci: Secure Digital Host Controller Interface driver
[    1.195830] sdhci: Copyright(c) Pierre Ossman
[    1.196969] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.196985] r8169 0000:04:00.0: can't disable ASPM; OS doesn't have ASPM control
[    1.197246] r8169 0000:04:00.0: irq 43 for MSI/MSI-X
[    1.197512] r8169 0000:04:00.0 eth0: RTL8101e at 0xf841a000, 00:16:d3:80:26:49, XID 14000000 IRQ 43
[    1.203759] sdhci-pci 0000:0a:09.1: SDHCI controller found [1180:0822] (rev 19)
[    1.204866] sdhci-pci 0000:0a:09.1: Will use DMA mode even though HW doesn't fully claim to support it.
[    1.204999] mmc0: no vqmmc regulator found
[    1.205002] mmc0: no vmmc regulator found
[    1.206011] sdhci-pci 0000:0a:09.1: Will use DMA mode even though HW doesn't fully claim to support it.
[    1.206105] mmc0: SDHCI controller on PCI [0000:0a:09.1] using DMA
[    1.237158] ahci 0000:00:1f.2: version 3.0
[    1.237399] ahci 0000:00:1f.2: irq 44 for MSI/MSI-X
[    1.237500] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 4 ports 1.5 Gbps 0x5 impl SATA mode
[    1.237505] ahci 0000:00:1f.2: flags: 64bit ncq pm led clo pio slum part 
[    1.237514] ahci 0000:00:1f.2: setting latency timer to 64
[    1.239741] scsi2 : ahci
[    1.240884] scsi3 : ahci
[    1.241042] scsi4 : ahci
[    1.241245] scsi5 : ahci
[    1.241357] ata3: SATA max UDMA/133 abar m1024@0xd8444400 port 0xd8444500 irq 44
[    1.241360] ata4: DUMMY
[    1.241364] ata5: SATA max UDMA/133 abar m1024@0xd8444400 port 0xd8444600 irq 44
[    1.241367] ata6: DUMMY
[    1.312153] firewire_ohci 0000:0a:09.0: added OHCI v1.10 device as card 0, 4 IR + 4 IT contexts, quirks 0x11
[    1.344042] usb 3-2: new low-speed USB device number 2 using uhci_hcd
[    1.517544] usb 3-2: New USB device found, idVendor=0bc7, idProduct=0006
[    1.517553] usb 3-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.517560] usb 3-2: Product: RF receiver
[    1.517566] usb 3-2: Manufacturer: X10 WTI
[    1.560131] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.560172] ata5: SATA link down (SStatus 0 SControl 300)
[    1.561188] ata3.00: ACPI cmd ef/90:03:00:00:00:a0 (SET FEATURES) rejected by device (Stat=0x51 Err=0x04)
[    1.598101] ata3.00: ATA-7: WDC WD1200BEVS-07LAT0, 01.06M01, max UDMA/133
[    1.598106] ata3.00: 234441648 sectors, multi 16: LBA48 NCQ (depth 1), AA
[    1.599197] ata3.00: ACPI cmd ef/90:03:00:00:00:a0 (SET FEATURES) rejected by device (Stat=0x51 Err=0x04)
[    1.599462] ata3.00: configured for UDMA/133
[    1.599711] scsi 2:0:0:0: Direct-Access     ATA      WDC WD1200BEVS-0 01.0 PQ: 0 ANSI: 5
[    1.599985] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    1.599991] sd 2:0:0:0: [sda] 234441648 512-byte logical blocks: (120 GB/111 GiB)
[    1.600110] sd 2:0:0:0: [sda] Write Protect is off
[    1.600115] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.600156] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.638149]  sda: sda1 sda2 < sda5 >
[    1.638849] sd 2:0:0:0: [sda] Attached SCSI disk
[    1.812215] firewire_core 0000:0a:09.0: created device fw0: GUID 07e40a0094267002, S400
[    2.000151] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
[    2.000157] EXT4-fs (sda1): write access will be enabled during recovery
[    3.720324] EXT4-fs (sda1): recovery complete
[    3.726961] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    4.488055] usb 1-8: new high-speed USB device number 16 using ehci-pci
[    4.620892] usb 1-8: New USB device found, idVendor=0ace, idProduct=1215
[    4.620897] usb 1-8: New USB device strings: Mfr=16, Product=32, SerialNumber=0
[    4.620901] usb 1-8: Product: USB Device
[    4.620905] usb 1-8: Manufacturer: ZyDAS
[    7.380396] Adding 1036284k swap on /dev/sda5.  Priority:-1 extents:1 across:1036284k FS
[    8.719050] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    9.060590] systemd-udevd[270]: starting version 204
[   10.908222] lp: driver loaded but no devices found
[   12.046751] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   13.247710] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   13.247948] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input4
[   13.580541] intel_rng: FWH not detected
[   13.794697] wmi: Mapper loaded
[   13.997609] ACPI Warning: 0x00001028-0x0000102f SystemIO conflicts with Region \PMIO 1 (20130517/utaddress-251)
[   13.997621] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   13.997626] ACPI Warning: 0x000011b0-0x000011bf SystemIO conflicts with Region \GPIO 1 (20130517/utaddress-251)
[   13.997633] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   13.997635] ACPI Warning: 0x00001180-0x000011af SystemIO conflicts with Region \GPIO 1 (20130517/utaddress-251)
[   13.997641] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   13.997644] lpc_ich: Resource conflict(s) found affecting gpio_ich
[   14.097666] r592 0000:0a:09.2: setting latency timer to 64
[   14.097812] r592: driver successfully loaded
[   14.205755] leds_ss4200: no LED devices found
[   14.387016] [drm] Initialized drm 1.1.0 20060810
[   14.763130] microcode: CPU0 sig=0x6e8, pf=0x20, revision=0x39
[   15.027289] psmouse serio4: synaptics: Touchpad model: 1, fw: 5.9, id: 0x23aeb3, caps: 0xa04713/0x10008/0x0, board id: 3655, fw id: 28762
[   15.058714] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input5
[   15.158636] r852 0000:0a:09.3: enabling device (0000 -> 0002)
[   15.158741] r852 0000:0a:09.3: setting latency timer to 64
[   15.158834] r852: Non dma capable device detected, dma disabled
[   15.158846] r852: driver loaded successfully
[   15.177629] [drm] Memory usable by graphics device = 256M
[   15.177643] i915 0000:00:02.0: setting latency timer to 64
[   15.180299] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   15.180305] [drm] Driver supports precise vblank timestamp query.
[   15.180386] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   15.271947] [drm] initialized overlay support
[   15.795155] fbcon: inteldrmfb (fb0) is primary device
[   16.196118] Console: switching to colour frame buffer device 160x50
[   16.202491] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[   16.202495] i915 0000:00:02.0: registered panic notifier
[   16.202506] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   16.202830] snd_hda_intel 0000:00:1b.0: irq 45 for MSI/MSI-X
[   16.303920] cfg80211: Calling CRDA to update world regulatory domain
[   16.318210] SKU: Nid=0x0 sku_cfg=0x0000952d
[   16.318214] SKU: port_connectivity=0x0
[   16.318217] SKU: enable_pcbeep=0x1
[   16.318219] SKU: check_sum=0x00000000
[   16.318221] SKU: customization=0x00000000
[   16.318223] SKU: external_amp=0x5
[   16.318225] SKU: platform_type=0x1
[   16.318227] SKU: swap=0x0
[   16.318229] SKU: override=0x1
[   16.318452] autoconfig: line_outs=1 (0x14/0x0/0x0/0x0/0x0) type:hp
[   16.318456]    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   16.318458]    hp_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   16.318461]    mono: mono_out=0x0
[   16.318463]    dig-out=0x1e/0x0
[   16.318465]    inputs:
[   16.318468]      Mic=0x18
[   16.318471]      Line=0x1a
[   16.318473]      CD=0x1c
[   16.318476] realtek: Enabling init ASM_ID=0x952d CODEC_ID=10ec0883
[   16.484451] input: HDA Intel Line as /devices/pci0000:00/0000:00:1b.0/sound/card0/input6
[   16.484613] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[   16.652066] Registered IR keymap rc-medion-x10-or2x
[   16.652208] input: X10 WTI RF receiver as /devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2:1.0/rc/rc0/input8
[   16.652317] rc0: X10 WTI RF receiver as /devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2:1.0/rc/rc0
[   16.652385] input: X10 WTI RF receiver mouse as /devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2:1.0/input/input9
[   16.652589] usbcore: registered new interface driver ati_remote
[   16.973581] type=1400 audit(1390199880.632:2): apparmor="STATUS" operation="profile_load" parent=383 profile="unconfined" name="/sbin/dhclient" pid=393 comm="apparmor_parser"
[   16.973595] type=1400 audit(1390199880.632:3): apparmor="STATUS" operation="profile_load" parent=383 profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=393 comm="apparmor_parser"
[   16.973604] type=1400 audit(1390199880.632:4): apparmor="STATUS" operation="profile_load" parent=383 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=393 comm="apparmor_parser"
[   16.974620] type=1400 audit(1390199880.632:5): apparmor="STATUS" operation="profile_replace" parent=383 profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=393 comm="apparmor_parser"
[   16.974631] type=1400 audit(1390199880.632:6): apparmor="STATUS" operation="profile_replace" parent=383 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=393 comm="apparmor_parser"
[   16.975181] type=1400 audit(1390199880.632:7): apparmor="STATUS" operation="profile_replace" parent=383 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=393 comm="apparmor_parser"
[   17.232051] usb 1-8: reset high-speed USB device number 16 using ehci-pci
[   17.519848] acer_wmi: Acer Laptop ACPI-WMI Extras
[   17.521051] acer_wmi: Disabling ACPI video driver
[   17.569578] input: Acer BMA150 accelerometer as /devices/virtual/input/input10
[   17.608798] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   17.609114] zd1211rw 1-8:1.0: phy0
[   17.609155] usbcore: registered new interface driver zd1211rw
[   17.616216] microcode: CPU1 sig=0x6e8, pf=0x20, revision=0x39
[   17.982550] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[   19.391328] init: failsafe main process (447) killed by TERM signal
[   19.548621] cfg80211: World regulatory domain updated:
[   19.548629] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   19.548632] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   19.548636] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   19.548639] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   19.548642] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   19.548645] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   21.498863] Bluetooth: Core ver 2.16
[   21.498901] NET: Registered protocol family 31
[   21.498903] Bluetooth: HCI device and connection manager initialized
[   21.498916] Bluetooth: HCI socket layer initialized
[   21.498920] Bluetooth: L2CAP socket layer initialized
[   21.498930] Bluetooth: SCO socket layer initialized
[   21.676768] Bluetooth: RFCOMM TTY layer initialized
[   21.676786] Bluetooth: RFCOMM socket layer initialized
[   21.676789] Bluetooth: RFCOMM ver 1.11
[   21.900858] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   21.900865] Bluetooth: BNEP filters: protocol multicast
[   21.900877] Bluetooth: BNEP socket layer initialized
[   22.246504] init: avahi-cups-reload main process (633) terminated with status 1
[   22.658390] ppdev: user-space parallel port driver
[   23.548097] type=1400 audit(1390199887.208:8): apparmor="STATUS" operation="profile_load" parent=646 profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=650 comm="apparmor_parser"
[   23.548114] type=1400 audit(1390199887.208:9): apparmor="STATUS" operation="profile_load" parent=646 profile="unconfined" name="/usr/sbin/cupsd" pid=650 comm="apparmor_parser"
[   23.549298] type=1400 audit(1390199887.208:10): apparmor="STATUS" operation="profile_replace" parent=646 profile="unconfined" name="/usr/sbin/cupsd" pid=650 comm="apparmor_parser"
[   26.644989] init: xbmc main process (672) terminated with status 1
[   26.645029] init: xbmc main process ended, respawning
[   26.657513] init: xbmc main process (739) terminated with status 1
[   26.657555] init: xbmc main process ended, respawning
[   26.673267] init: xbmc main process (741) terminated with status 1
[   26.673312] init: xbmc main process ended, respawning
[   26.691185] init: xbmc main process (744) terminated with status 1
[   26.691225] init: xbmc main process ended, respawning
[   26.707749] init: xbmc main process (746) terminated with status 1
[   26.707790] init: xbmc main process ended, respawning
[   26.724505] init: xbmc main process (748) terminated with status 1
[   26.724546] init: xbmc main process ended, respawning
[   26.741196] init: xbmc main process (750) terminated with status 1
[   26.741236] init: xbmc main process ended, respawning
[   26.757581] init: xbmc main process (752) terminated with status 1
[   26.757622] init: xbmc main process ended, respawning
[   26.773990] init: xbmc main process (754) terminated with status 1
[   26.774031] init: xbmc main process ended, respawning
[   26.790886] init: xbmc main process (756) terminated with status 1
[   26.790927] init: xbmc main process ended, respawning
[   26.804049] init: xbmc main process (759) terminated with status 1
[   26.804094] init: xbmc respawning too fast, stopped
[   29.072976] r8169 0000:04:00.0 eth0: link down
[   29.073019] r8169 0000:04:00.0 eth0: link down
[   29.073050] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   29.073474] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   29.076358] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   29.517286] zd1211rw 1-8:1.0: firmware version 4725
[   29.571286] zd1211rw 1-8:1.0: zd1211b chip 0ace:1215 v4810 high 00-60-b3 UW2453_RF pa0 g7---
[   29.683608] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   29.683643] cfg80211: Calling CRDA for country: DE
[   29.689594] cfg80211: Regulatory domain changed to country: DE
[   29.689601] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   29.689604] cfg80211:   (2400000 KHz - 2483500 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   29.689607] cfg80211:   (5150000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   29.689610] cfg80211:   (5250000 KHz - 5350000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   29.689613] cfg80211:   (5470000 KHz - 5725000 KHz @ 40000 KHz), (N/A, 2698 mBm)
[   29.689616] cfg80211:   (57240000 KHz - 65880000 KHz @ 2160000 KHz), (N/A, 4000 mBm)
[   30.632509] r8169 0000:04:00.0 eth0: link up
[   30.667412] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   30.667433] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   32.198107] type=1400 audit(1390199895.856:11): apparmor="STATUS" operation="profile_load" parent=815 profile="unconfined" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=820 comm="apparmor_parser"
[   32.198123] type=1400 audit(1390199895.856:12): apparmor="STATUS" operation="profile_load" parent=815 profile="unconfined" name="chromium_browser" pid=820 comm="apparmor_parser"
[   32.198992] type=1400 audit(1390199895.856:13): apparmor="STATUS" operation="profile_replace" parent=815 profile="unconfined" name="chromium_browser" pid=820 comm="apparmor_parser"
[   32.215842] type=1400 audit(1390199895.872:14): apparmor="STATUS" operation="profile_load" parent=815 profile="unconfined" name="/usr/lib/i386-linux-gnu/lightdm-remote-session-freerdp/freerdp-session-wrapper" pid=821 comm="apparmor_parser"
[   32.215856] type=1400 audit(1390199895.872:15): apparmor="STATUS" operation="profile_load" parent=815 profile="unconfined" name="chromium_browser" pid=821 comm="apparmor_parser"
[   32.216722] type=1400 audit(1390199895.876:16): apparmor="STATUS" operation="profile_replace" parent=815 profile="unconfined" name="chromium_browser" pid=821 comm="apparmor_parser"
[   32.221646] type=1400 audit(1390199895.880:17): apparmor="STATUS" operation="profile_replace" parent=815 profile="unconfined" name="/sbin/dhclient" pid=823 comm="apparmor_parser"
[   32.221660] type=1400 audit(1390199895.880:18): apparmor="STATUS" operation="profile_replace" parent=815 profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=823 comm="apparmor_parser"
[   32.221669] type=1400 audit(1390199895.880:19): apparmor="STATUS" operation="profile_replace" parent=815 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=823 comm="apparmor_parser"
[   32.222688] type=1400 audit(1390199895.880:20): apparmor="STATUS" operation="profile_replace" parent=815 profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=823 comm="apparmor_parser"
[   34.770758] init: alsa-restore main process (973) terminated with status 99

```

Boot 3:
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 3.11.0-15-generic (buildd@tipua) (gcc version 4.8.1 (Ubuntu/Linaro 4.8.1-10ubuntu8) ) #23-Ubuntu SMP Mon Dec 9 18:16:27 UTC 2013 (Ubuntu 3.11.0-15.23-generic 3.11.10)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] Disabled fast string operations
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009f7ff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009f800-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000dc000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x000000003f68ffff] usable
[    0.000000] BIOS-e820: [mem 0x000000003f690000-0x000000003f6fffff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x000000003f700000-0x000000003fffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000e0000000-0x00000000efffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec0ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed00000-0x00000000fed003ff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed14000-0x00000000fed19fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed1c000-0x00000000fed8ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ff000000-0x00000000ffffffff] reserved
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.4 present.
[    0.000000] DMI: MEDION WIM2120/WIM2120, BIOS R01-B0F    01/15/2007
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] e820: last_pfn = 0x3f690 max_arch_pfn = 0x1000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-DFFFF uncachable
[    0.000000]   E0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask FC0000000 write-back
[    0.000000]   1 base 03F700000 mask FFFF00000 uncachable
[    0.000000]   2 base 03F800000 mask FFF800000 uncachable
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] PAT not supported by CPU.
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 1GB, type WB
[    0.000000] reg 1, base: 1015MB, range: 1MB, type UC
[    0.000000] reg 2, base: 1016MB, range: 8MB, type UC
[    0.000000] total RAM covered: 1015M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K     chunk_size: 16M     num_reg: 3      lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 1GB, type WB
[    0.000000] reg 1, base: 1015MB, range: 1MB, type UC
[    0.000000] reg 2, base: 1016MB, range: 8MB, type UC
[    0.000000] found SMP MP-table at [mem 0x000f68e0-0x000f68ef] mapped at [c00f68e0]
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] initial memory mapped: [mem 0x00000000-0x01ffffff]
[    0.000000] Base memory trampoline at [c009b000] 9b000 size 16384
[    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
[    0.000000]  [mem 0x00000000-0x000fffff] page 4k
[    0.000000] init_memory_mapping: [mem 0x37800000-0x379fffff]
[    0.000000]  [mem 0x37800000-0x379fffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x34000000-0x377fffff]
[    0.000000]  [mem 0x34000000-0x377fffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x00100000-0x33ffffff]
[    0.000000]  [mem 0x00100000-0x001fffff] page 4k
[    0.000000]  [mem 0x00200000-0x33ffffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x37a00000-0x37bfdfff]
[    0.000000]  [mem 0x37a00000-0x37bfdfff] page 4k
[    0.000000] BRK [0x01b49000, 0x01b49fff] PGTABLE
[    0.000000] RAMDISK: [mem 0x35f6c000-0x36fadfff]
[    0.000000] ACPI: RSDP 000f6770 00014 (v00 PTLTD )
[    0.000000] ACPI: RSDT 3f6916cf 00048 (v01 MEDION MEDIONAG 06040000 ZNEB 00000000)
[    0.000000] ACPI: FACP 3f697caa 00074 (v01 INTEL  CALISTGA 06040000 LOHR 00000065)
[    0.000000] ACPI: DSDT 3f692298 05A12 (v01 INTEL  CALISTGA 06040000 MSFT 0100000E)
[    0.000000] ACPI: FACS 3f698fc0 00040
[    0.000000] ACPI: APIC 3f697d1e 00068 (v01 INTEL  CALISTGA 06040000 LOHR 00000065)
[    0.000000] ACPI: HPET 3f697d86 00038 (v01 INTEL  CALISTGA 06040000 LOHR 00000065)
[    0.000000] ACPI: MCFG 3f697dbe 0003C (v01 INTEL  CALISTGA 06040000 LOHR 00000065)
[    0.000000] ACPI: SLIC 3f697dfa 00176 (v01 MEDION MEDIONAG 06040000 BENZ 00000001)
[    0.000000] ACPI: APIC 3f697f70 00068 (v01 PTLTD  ? APIC   06040000  LTP 00000000)
[    0.000000] ACPI: BOOT 3f697fd8 00028 (v01 PTLTD  $SBFTBL$ 06040000  LTP 00000001)
[    0.000000] ACPI: SSDT 3f69208e 0020A (v01 SataRe SataAhci 00001000 INTL 20050624)
[    0.000000] ACPI: SSDT 3f691717 004F6 (v01  PmRef    CpuPm 00003000 INTL 20050624)
[    0.000000] ACPI: BIOS bug: multiple APIC/MADT found, using 0
[    0.000000] ACPI: If "acpi_apic_instance=2" works better, notify linux-acpi@vger.kernel.org
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 122MB HIGHMEM available.
[    0.000000] 891MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 37bfe000
[    0.000000]   low ram: 0 - 37bfe000
[    0.000000] BRK [0x01b4a000, 0x01b4afff] PGTABLE
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00001000-0x00ffffff]
[    0.000000]   Normal   [mem 0x01000000-0x37bfdfff]
[    0.000000]   HighMem  [mem 0x37bfe000-0x3f68ffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00001000-0x0009efff]
[    0.000000]   node   0: [mem 0x00100000-0x3f68ffff]
[    0.000000] On node 0 totalpages: 259630
[    0.000000] free_area_init_node: node 0, pgdat c1958bc0, node_mem_map f740e020
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3998 pages, LIFO batch:0
[    0.000000]   Normal zone: 1752 pages used for memmap
[    0.000000]   Normal zone: 224254 pages, LIFO batch:31
[    0.000000]   HighMem zone: 246 pages used for memmap
[    0.000000]   HighMem zone: 31378 pages, LIFO batch:7
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
[    0.000000] smpboot: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: [mem 0x0009f000-0x0009ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dbfff]
[    0.000000] PM: Registered nosave memory: [mem 0x000dc000-0x000fffff]
[    0.000000] e820: [mem 0x40000000-0xdfffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @f73ec000 s36288 r0 d21056 u57344
[    0.000000] pcpu-alloc: s36288 r0 d21056 u57344 alloc=14*4096
[    0.000000] pcpu-alloc: [0] 0 [0] 1 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 257846
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.11.0-15-generic root=UUID=b1b16843-0173-40ed-a37c-8643572cc543 ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] allocated 2077816 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (00037bfe:0003f690)
[    0.000000] Memory: 999140K/1038520K available (6358K kernel code, 611K rwdata, 2692K rodata, 880K init, 908K bss, 39380K reserved, 125512K highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff14000 - 0xfffff000   ( 940 kB)
[    0.000000]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
[    0.000000]     vmalloc : 0xf83fe000 - 0xffbfe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf7bfe000   ( 891 MB)
[    0.000000]       .init : 0xc1972000 - 0xc1a4e000   ( 880 kB)
[    0.000000]       .data : 0xc1635ee4 - 0xc1971f80   (3312 kB)
[    0.000000]       .text : 0xc1000000 - 0xc1635ee4   (6359 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU restricting CPUs from NR_CPUS=8 to nr_cpu_ids=2.
[    0.000000] NR_IRQS:2304 nr_irqs:512 16
[    0.000000] CPU 0 irqstacks, hard=f5808000 soft=f580a000
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.000000] tsc: Detected 1662.333 MHz processor
[    0.004002] Calibrating delay loop (skipped), value calculated using timer frequency.. 3324.66 BogoMIPS (lpj=6649332)
[    0.004008] pid_max: default: 32768 minimum: 301
[    0.004055] Security Framework initialized
[    0.004083] AppArmor: AppArmor initialized
[    0.004086] Yama: becoming mindful.
[    0.004188] Mount-cache hash table entries: 512
[    0.004566] Initializing cgroup subsys memory
[    0.004583] Initializing cgroup subsys devices
[    0.004586] Initializing cgroup subsys freezer
[    0.004590] Initializing cgroup subsys blkio
[    0.004594] Initializing cgroup subsys perf_event
[    0.004599] Initializing cgroup subsys hugetlb
[    0.004635] Disabled fast string operations
[    0.004642] CPU: Physical Processor ID: 0
[    0.004645] CPU: Processor Core ID: 0
[    0.004649] mce: CPU supports 6 MCE banks
[    0.004662] CPU0: Thermal monitoring enabled (TM2)
[    0.004678] Last level iTLB entries: 4KB 128, 2MB 0, 4MB 2
[    0.004678] Last level dTLB entries: 4KB 128, 2MB 0, 4MB 8
[    0.004678] tlb_flushall_shift: 6
[    0.005169] Freeing SMP alternatives memory: 28K (c1a4e000 - c1a55000)
[    0.010267] ACPI: Core revision 20130517
[    0.016095] ACPI: All ACPI Tables successfully acquired
[    0.020013] ftrace: allocating 27182 entries in 54 pages
[    0.032133] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.032610] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.074941] smpboot: CPU0: Genuine Intel(R) CPU           T2300  @ 1.66GHz (fam: 06, model: 0e, stepping: 08)
[    0.076000] Performance Events: Core events, core PMU driver.
[    0.076000] ... version:                1
[    0.076000] ... bit width:              40
[    0.076000] ... generic registers:      2
[    0.076000] ... value mask:             000000ffffffffff
[    0.076000] ... max period:             000000007fffffff
[    0.076000] ... fixed-purpose events:   0
[    0.076000] ... event mask:             0000000000000003
[    0.076000] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.076000] CPU 1 irqstacks, hard=f58f0000 soft=f58f2000
[    0.076000] smpboot: Booting Node   0, Processors  #1 OK
[    0.008000] Initializing CPU#1
[    0.008000] Disabled fast string operations
[    0.087799] Brought up 2 CPUs
[    0.087807] smpboot: Total of 2 processors activated (6649.33 BogoMIPS)
[    0.092105] devtmpfs: initialized
[    0.092362] EVM: security.selinux
[    0.092364] EVM: security.SMACK64
[    0.092367] EVM: security.capability
[    0.092393] PM: Registering ACPI NVS region [mem 0x3f690000-0x3f6fffff] (458752 bytes)
[    0.094030] regulator-dummy: no parameters
[    0.094079] RTC time:  6:39:43, date: 01/20/14
[    0.094149] NET: Registered protocol family 16
[    0.094399] EISA bus registered
[    0.094517] ACPI: bus type PCI registered
[    0.094522] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.094613] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.094618] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    0.094621] PCI: Using MMCONFIG for extended config space
[    0.094623] PCI: Using configuration type 1 for base access
[    0.096106] bio: create slab <bio-0> at 0
[    0.096142] ACPI: Added _OSI(Module Device)
[    0.096147] ACPI: Added _OSI(Processor Device)
[    0.096150] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.096153] ACPI: Added _OSI(Processor Aggregator Device)
[    0.098201] ACPI: EC: Look up EC in DSDT
[    0.099654] ACPI: SSDT 3f691e5d 001A8 (v01  PmRef  Cpu0Ist 00003000 INTL 20050624)
[    0.100169] ACPI: Dynamic OEM Table Load:
[    0.100174] ACPI: SSDT   (null) 001A8 (v01  PmRef  Cpu0Ist 00003000 INTL 20050624)
[    0.100323] ACPI: SSDT 3f691c0d 001CB (v01  PmRef  Cpu0Cst 00003001 INTL 20050624)
[    0.100809] ACPI: Dynamic OEM Table Load:
[    0.100813] ACPI: SSDT   (null) 001CB (v01  PmRef  Cpu0Cst 00003001 INTL 20050624)
[    0.101180] ACPI: SSDT 3f692005 00089 (v01  PmRef  Cpu1Ist 00003000 INTL 20050624)
[    0.101679] ACPI: Dynamic OEM Table Load:
[    0.101683] ACPI: SSDT   (null) 00089 (v01  PmRef  Cpu1Ist 00003000 INTL 20050624)
[    0.101814] ACPI: SSDT 3f691dd8 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20050624)
[    0.102304] ACPI: Dynamic OEM Table Load:
[    0.102308] ACPI: SSDT   (null) 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20050624)
[    0.108230] ACPI: Interpreter enabled
[    0.108244] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20130517/hwxface-571)
[    0.108252] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20130517/hwxface-571)
[    0.108276] ACPI: (supports S0 S3 S4 S5)
[    0.108278] ACPI: Using IOAPIC for interrupt routing
[    0.108320] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
[    0.108491] ACPI: No dock devices found.
[    0.122869] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.122878] acpi PNP0A08:00: ACPI _OSC support notification failed, disabling PCIe ASPM
[    0.122881] acpi PNP0A08:00: Unable to request _OSC control (_OSC support mask: 0x08)
[    0.124539] acpi PNP0A08:00: host bridge window [io  0x0000-0x0cf7] (ignored)
[    0.124544] acpi PNP0A08:00: host bridge window [io  0x0d00-0xffff] (ignored)
[    0.124548] acpi PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)
[    0.124552] acpi PNP0A08:00: host bridge window [mem 0x000d0000-0x000d3fff] (ignored)
[    0.124556] acpi PNP0A08:00: host bridge window [mem 0x000d4000-0x000d7fff] (ignored)
[    0.124560] acpi PNP0A08:00: host bridge window [mem 0x000d8000-0x000dbfff] (ignored)
[    0.124564] acpi PNP0A08:00: host bridge window [mem 0x40000000-0xfebfffff] (ignored)
[    0.124568] PCI: root bus 00: using default resources
[    0.124788] PCI host bridge to bus 0000:00
[    0.124794] pci_bus 0000:00: root bus resource [bus 00-ff]
[    0.124798] pci_bus 0000:00: root bus resource [io  0x0000-0xffff]
[    0.124802] pci_bus 0000:00: root bus resource [mem 0x00000000-0xffffffff]
[    0.124817] pci 0000:00:00.0: [8086:27a0] type 00 class 0x060000
[    0.125003] pci 0000:00:02.0: [8086:27a2] type 00 class 0x030000
[    0.125021] pci 0000:00:02.0: reg 0x10: [mem 0xd8100000-0xd817ffff]
[    0.125031] pci 0000:00:02.0: reg 0x14: [io  0x1800-0x1807]
[    0.125041] pci 0000:00:02.0: reg 0x18: [mem 0xc0000000-0xcfffffff pref]
[    0.125051] pci 0000:00:02.0: reg 0x1c: [mem 0xd8200000-0xd823ffff]
[    0.125223] pci 0000:00:02.1: [8086:27a6] type 00 class 0x038000
[    0.125238] pci 0000:00:02.1: reg 0x10: [mem 0xd8180000-0xd81fffff]
[    0.125482] pci 0000:00:1b.0: [8086:27d8] type 00 class 0x040300
[    0.125510] pci 0000:00:1b.0: reg 0x10: [mem 0xd8440000-0xd8443fff 64bit]
[    0.125632] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.125735] pci 0000:00:1b.0: System wakeup disabled by ACPI
[    0.125801] pci 0000:00:1c.0: [8086:27d0] type 01 class 0x060400
[    0.125928] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.126092] pci 0000:00:1c.1: [8086:27d2] type 01 class 0x060400
[    0.126219] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.126382] pci 0000:00:1c.3: [8086:27d6] type 01 class 0x060400
[    0.126509] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.126673] pci 0000:00:1d.0: [8086:27c8] type 00 class 0x0c0300
[    0.126739] pci 0000:00:1d.0: reg 0x20: [io  0x1820-0x183f]
[    0.126900] pci 0000:00:1d.1: [8086:27c9] type 00 class 0x0c0300
[    0.126966] pci 0000:00:1d.1: reg 0x20: [io  0x1840-0x185f]
[    0.127129] pci 0000:00:1d.2: [8086:27ca] type 00 class 0x0c0300
[    0.127195] pci 0000:00:1d.2: reg 0x20: [io  0x1860-0x187f]
[    0.127356] pci 0000:00:1d.3: [8086:27cb] type 00 class 0x0c0300
[    0.127422] pci 0000:00:1d.3: reg 0x20: [io  0x1880-0x189f]
[    0.127599] pci 0000:00:1d.7: [8086:27cc] type 00 class 0x0c0320
[    0.127628] pci 0000:00:1d.7: reg 0x10: [mem 0xd8444000-0xd84443ff]
[    0.127752] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.127904] pci 0000:00:1e.0: [8086:2448] type 01 class 0x060401
[    0.128136] pci 0000:00:1f.0: [8086:27b9] type 00 class 0x060100
[    0.128265] pci 0000:00:1f.0: address space collision: [io  0x1000-0x107f] conflicts with ACPI CPU throttle [??? 0x00001010-0x00001015 flags 0x80000000]
[    0.128274] pci 0000:00:1f.0: quirk: [io  0x1180-0x11bf] claimed by ICH6 GPIO
[    0.128282] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 2 PIO at 1200 (mask 0007)
[    0.128462] pci 0000:00:1f.1: [8086:27df] type 00 class 0x01018a
[    0.128484] pci 0000:00:1f.1: reg 0x10: [io  0x0000-0x0007]
[    0.128499] pci 0000:00:1f.1: reg 0x14: [io  0x0000-0x0003]
[    0.128514] pci 0000:00:1f.1: reg 0x18: [io  0x0000-0x0007]
[    0.128529] pci 0000:00:1f.1: reg 0x1c: [io  0x0000-0x0003]
[    0.128544] pci 0000:00:1f.1: reg 0x20: [io  0x1810-0x181f]
[    0.128718] pci 0000:00:1f.2: [8086:27c5] type 00 class 0x010601
[    0.128747] pci 0000:00:1f.2: reg 0x10: [io  0x18d0-0x18d7]
[    0.128762] pci 0000:00:1f.2: reg 0x14: [io  0x18c4-0x18c7]
[    0.128777] pci 0000:00:1f.2: reg 0x18: [io  0x18c8-0x18cf]
[    0.128792] pci 0000:00:1f.2: reg 0x1c: [io  0x18c0-0x18c3]
[    0.128808] pci 0000:00:1f.2: reg 0x20: [io  0x18b0-0x18bf]
[    0.128823] pci 0000:00:1f.2: reg 0x24: [mem 0xd8444400-0xd84447ff]
[    0.128891] pci 0000:00:1f.2: PME# supported from D3hot
[    0.129040] pci 0000:00:1f.3: [8086:27da] type 00 class 0x0c0500
[    0.129123] pci 0000:00:1f.3: reg 0x20: [io  0x18e0-0x18ff]
[    0.129444] acpiphp: Slot [1] registered
[    0.129457] pci 0000:00:1c.0: PCI bridge to [bus 02-03]
[    0.129464] pci 0000:00:1c.0:   bridge window [io  0x2000-0x2fff]
[    0.129471] pci 0000:00:1c.0:   bridge window [mem 0xd4000000-0xd5ffffff]
[    0.129482] pci 0000:00:1c.0:   bridge window [mem 0xd0000000-0xd1ffffff 64bit pref]
[    0.129626] pci 0000:04:00.0: [10ec:8136] type 00 class 0x020000
[    0.129656] pci 0000:04:00.0: reg 0x10: [io  0x3000-0x30ff]
[    0.129704] pci 0000:04:00.0: reg 0x18: [mem 0xd6000000-0xd6000fff 64bit]
[    0.129759] pci 0000:04:00.0: reg 0x30: [mem 0x00000000-0x0001ffff pref]
[    0.129882] pci 0000:04:00.0: supports D1 D2
[    0.129886] pci 0000:04:00.0: PME# supported from D1 D2 D3hot D3cold
[    0.129931] pci 0000:04:00.0: System wakeup disabled by ACPI
[    0.129987] pci 0000:04:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    0.130004] pci 0000:00:1c.1: PCI bridge to [bus 04-05]
[    0.130011] pci 0000:00:1c.1:   bridge window [io  0x3000-0x3fff]
[    0.130018] pci 0000:00:1c.1:   bridge window [mem 0xd6000000-0xd7ffffff]
[    0.130029] pci 0000:00:1c.1:   bridge window [mem 0xd2000000-0xd3ffffff 64bit pref]
[    0.130138] pci 0000:00:1c.3: PCI bridge to [bus 06]
[    0.130251] pci 0000:0a:09.0: [1180:0832] type 00 class 0x0c0010
[    0.130270] pci 0000:0a:09.0: proprietary Ricoh MMC controller disabled (via firewire function)
[    0.130273] pci 0000:0a:09.0: MMC cards are now supported by standard SDHCI controller
[    0.130293] pci 0000:0a:09.0: reg 0x10: [mem 0xd8000000-0xd80007ff]
[    0.130406] pci 0000:0a:09.0: supports D1 D2
[    0.130410] pci 0000:0a:09.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.130490] pci 0000:0a:09.1: [1180:0822] type 00 class 0x080500
[    0.130517] pci 0000:0a:09.1: reg 0x10: [mem 0xd8000800-0xd80008ff]
[    0.130634] pci 0000:0a:09.1: supports D1 D2
[    0.130637] pci 0000:0a:09.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.130718] pci 0000:0a:09.2: [1180:0592] type 00 class 0x088000
[    0.130745] pci 0000:0a:09.2: reg 0x10: [mem 0xd8000c00-0xd8000cff]
[    0.130857] pci 0000:0a:09.2: supports D1 D2
[    0.130861] pci 0000:0a:09.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.130943] pci 0000:0a:09.3: [1180:0852] type 00 class 0x088000
[    0.130970] pci 0000:0a:09.3: reg 0x10: [mem 0xd8001000-0xd80010ff]
[    0.131084] pci 0000:0a:09.3: supports D1 D2
[    0.131087] pci 0000:0a:09.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.131204] pci 0000:00:1e.0: PCI bridge to [bus 0a] (subtractive decode)
[    0.131214] pci 0000:00:1e.0:   bridge window [mem 0xd8000000-0xd80fffff]
[    0.131225] pci 0000:00:1e.0:   bridge window [io  0x0000-0xffff] (subtractive decode)
[    0.131229] pci 0000:00:1e.0:   bridge window [mem 0x00000000-0xffffffff] (subtractive decode)
[    0.131262] pci_bus 0000:00: on NUMA node 0
[    0.132118] ACPI: PCI Interrupt Link [LNKA] (IRQs 10 11) *7
[    0.132218] ACPI: PCI Interrupt Link [LNKB] (IRQs 10 11) *3
[    0.132316] ACPI: PCI Interrupt Link [LNKC] (IRQs 10 *11)
[    0.132413] ACPI: PCI Interrupt Link [LNKD] (IRQs *10 11)
[    0.132509] ACPI: PCI Interrupt Link [LNKE] (IRQs 10 11) *0, disabled.
[    0.132607] ACPI: PCI Interrupt Link [LNKF] (IRQs *10 11)
[    0.132703] ACPI: PCI Interrupt Link [LNKG] (IRQs 10 11) *0, disabled.
[    0.132801] ACPI: PCI Interrupt Link [LNKH] (IRQs 10 11) *5
[    0.132986] ACPI: Enabled 9 GPEs in block 00 to 1F
[    0.132986] ACPI: \_SB_.PCI0: notify handler is installed
[    0.132986] Found 1 acpi root devices
[    0.132986] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
[    0.132986] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.132986] vgaarb: loaded
[    0.132986] vgaarb: bridge control possible 0000:00:02.0
[    0.132986] SCSI subsystem initialized
[    0.132986] ACPI: bus type ATA registered
[    0.132986] libata version 3.00 loaded.
[    0.132986] ACPI: bus type USB registered
[    0.132986] usbcore: registered new interface driver usbfs
[    0.132986] usbcore: registered new interface driver hub
[    0.132986] usbcore: registered new device driver usb
[    0.132986] PCI: Using ACPI for IRQ routing
[    0.142999] PCI: pci_cache_line_size set to 64 bytes
[    0.143094] e820: reserve RAM buffer [mem 0x0009f800-0x0009ffff]
[    0.143101] e820: reserve RAM buffer [mem 0x3f690000-0x3fffffff]
[    0.143255] NetLabel: Initializing
[    0.143258] NetLabel:  domain hash size = 128
[    0.143260] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.143278] NetLabel:  unlabeled traffic allowed by default
[    0.144134] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.144142] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.144149] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.149012] Switched to clocksource hpet
[    0.160858] AppArmor: AppArmor Filesystem Enabled
[    0.160912] pnp: PnP ACPI init
[    0.160938] ACPI: bus type PNP registered
[    0.161127] system 00:00: [mem 0xe0000000-0xefffffff] has been reserved
[    0.161132] system 00:00: [mem 0xfed14000-0xfed17fff] has been reserved
[    0.161137] system 00:00: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.161142] system 00:00: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.161146] system 00:00: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.161151] system 00:00: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.161155] system 00:00: [mem 0xfed40000-0xfed44fff] has been reserved
[    0.161160] system 00:00: [mem 0xfed45000-0xfed8ffff] has been reserved
[    0.161168] system 00:00: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.163044] pnp 00:01: [dma 4]
[    0.163092] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.163153] pnp 00:02: Plug and Play ACPI device, IDs INT0800 (active)
[    0.163319] system 00:03: [mem 0xfed00000-0xfed003ff] has been reserved
[    0.163325] system 00:03: Plug and Play ACPI device, IDs PNP0103 PNP0c01 (active)
[    0.163405] pnp 00:04: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.163503] system 00:05: [io  0x0800-0x080f] has been reserved
[    0.163508] system 00:05: [io  0x1000-0x107f] could not be reserved
[    0.163513] system 00:05: [io  0x1180-0x11bf] has been reserved
[    0.163517] system 00:05: [io  0x1640-0x164f] has been reserved
[    0.163522] system 00:05: [io  0x1200-0x120f] has been reserved
[    0.163527] system 00:05: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.163625] system 00:06: [io  0x06a0-0x06af] has been reserved
[    0.163630] system 00:06: [io  0x06b0-0x06ff] has been reserved
[    0.163635] system 00:06: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.163702] pnp 00:07: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.163768] pnp 00:08: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.163831] pnp 00:09: Plug and Play ACPI device, IDs SYN030b SYN0300 PNP0f13 (active)
[    0.163865] pnp: PnP ACPI: found 10 devices
[    0.163867] ACPI: bus type PNP unregistered
[    0.163872] PnPBIOS: Disabled by ACPI PNP
[    0.202321] pci 0000:00:1c.3: bridge window [io  0x1000-0x0fff] to [bus 06] add_size 1000
[    0.202329] pci 0000:00:1c.3: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 06] add_size 200000
[    0.202334] pci 0000:00:1c.3: bridge window [mem 0x00100000-0x000fffff] to [bus 06] add_size 200000
[    0.202354] pci 0000:00:1f.0: BAR 13: [io  0x1000-0x107f] has bogus alignment
[    0.202360] pci 0000:00:1c.3: res[14]=[mem 0x00100000-0x000fffff] get_res_add_size add_size 200000
[    0.202364] pci 0000:00:1c.3: res[15]=[mem 0x00100000-0x000fffff 64bit pref] get_res_add_size add_size 200000
[    0.202368] pci 0000:00:1c.3: res[13]=[io  0x1000-0x0fff] get_res_add_size add_size 1000
[    0.202378] pci 0000:00:1c.3: BAR 14: assigned [mem 0x40000000-0x401fffff]
[    0.202383] pci 0000:00:1c.3: BAR 15: assigned [mem 0x40200000-0x403fffff 64bit pref]
[    0.202390] pci 0000:00:1c.3: BAR 13: assigned [io  0x4000-0x4fff]
[    0.202395] pci 0000:00:1c.0: PCI bridge to [bus 02-03]
[    0.202401] pci 0000:00:1c.0:   bridge window [io  0x2000-0x2fff]
[    0.202410] pci 0000:00:1c.0:   bridge window [mem 0xd4000000-0xd5ffffff]
[    0.202418] pci 0000:00:1c.0:   bridge window [mem 0xd0000000-0xd1ffffff 64bit pref]
[    0.202430] pci 0000:04:00.0: BAR 6: assigned [mem 0xd2000000-0xd201ffff pref]
[    0.202434] pci 0000:00:1c.1: PCI bridge to [bus 04-05]
[    0.202440] pci 0000:00:1c.1:   bridge window [io  0x3000-0x3fff]
[    0.202448] pci 0000:00:1c.1:   bridge window [mem 0xd6000000-0xd7ffffff]
[    0.202456] pci 0000:00:1c.1:   bridge window [mem 0xd2000000-0xd3ffffff 64bit pref]
[    0.202466] pci 0000:00:1c.3: PCI bridge to [bus 06]
[    0.202471] pci 0000:00:1c.3:   bridge window [io  0x4000-0x4fff]
[    0.202480] pci 0000:00:1c.3:   bridge window [mem 0x40000000-0x401fffff]
[    0.202487] pci 0000:00:1c.3:   bridge window [mem 0x40200000-0x403fffff 64bit pref]
[    0.202498] pci 0000:00:1e.0: PCI bridge to [bus 0a]
[    0.202507] pci 0000:00:1e.0:   bridge window [mem 0xd8000000-0xd80fffff]
[    0.203094] pci 0000:00:1e.0: setting latency timer to 64
[    0.203101] pci_bus 0000:00: resource 4 [io  0x0000-0xffff]
[    0.203105] pci_bus 0000:00: resource 5 [mem 0x00000000-0xffffffff]
[    0.203109] pci_bus 0000:02: resource 0 [io  0x2000-0x2fff]
[    0.203113] pci_bus 0000:02: resource 1 [mem 0xd4000000-0xd5ffffff]
[    0.203117] pci_bus 0000:02: resource 2 [mem 0xd0000000-0xd1ffffff 64bit pref]
[    0.203121] pci_bus 0000:04: resource 0 [io  0x3000-0x3fff]
[    0.203125] pci_bus 0000:04: resource 1 [mem 0xd6000000-0xd7ffffff]
[    0.203129] pci_bus 0000:04: resource 2 [mem 0xd2000000-0xd3ffffff 64bit pref]
[    0.203134] pci_bus 0000:06: resource 0 [io  0x4000-0x4fff]
[    0.203137] pci_bus 0000:06: resource 1 [mem 0x40000000-0x401fffff]
[    0.203142] pci_bus 0000:06: resource 2 [mem 0x40200000-0x403fffff 64bit pref]
[    0.203146] pci_bus 0000:0a: resource 1 [mem 0xd8000000-0xd80fffff]
[    0.203150] pci_bus 0000:0a: resource 4 [io  0x0000-0xffff]
[    0.203153] pci_bus 0000:0a: resource 5 [mem 0x00000000-0xffffffff]
[    0.203201] NET: Registered protocol family 2
[    0.203444] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
[    0.203496] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[    0.203545] TCP: Hash tables configured (established 8192 bind 8192)
[    0.203582] TCP: reno registered
[    0.203586] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.203600] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.203695] NET: Registered protocol family 1
[    0.203718] pci 0000:00:02.0: Boot video device
[    0.205630] PCI: CLS 64 bytes, default 64
[    0.205696] Trying to unpack rootfs image as initramfs...
[    0.701443] Freeing initrd memory: 16648K (f5f6c000 - f6fae000)
[    0.701564] Simple Boot Flag at 0x36 set to 0x1
[    0.701771] Scanning for low memory corruption every 60 seconds
[    0.702173] Initialise module verification
[    0.702247] audit: initializing netlink socket (disabled)
[    0.702269] type=2000 audit(1390199983.700:1): initialized
[    0.736288] bounce pool size: 64 pages
[    0.736316] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.738693] zbud: loaded
[    0.738781] VFS: Disk quotas dquot_6.5.2
[    0.738864] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.739770] fuse init (API version 7.22)
[    0.739927] msgmni has been set to 1738
[    0.740807] Key type asymmetric registered
[    0.740811] Asymmetric key parser 'x509' registered
[    0.740866] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    0.740925] io scheduler noop registered
[    0.740929] io scheduler deadline registered (default)
[    0.740977] io scheduler cfq registered
[    0.741184] pcieport 0000:00:1c.0: irq 40 for MSI/MSI-X
[    0.741309] pcieport 0000:00:1c.1: irq 41 for MSI/MSI-X
[    0.741424] pcieport 0000:00:1c.3: irq 42 for MSI/MSI-X
[    0.741556] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.741584] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.741729] intel_idle: does not run on family 6 model 14
[    0.743416] ACPI: AC Adapter [ADP1] (on-line)
[    0.743548] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    0.744418] ACPI: Lid Switch [LID0]
[    0.744484] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1
[    0.744491] ACPI: Sleep Button [SLPB]
[    0.744572] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.744577] ACPI: Power Button [PWRF]
[    0.744679] ACPI: Requesting acpi_cpufreq
[    0.745270] tsc: Marking TSC unstable due to TSC halts in idle
[    0.745285] ACPI: acpi_idle registered with cpuidle
[    0.752915] thermal LNXTHERM:00: registered as thermal_zone0
[    0.752918] ACPI: Thermal Zone [TZS0] (37 C)
[    0.756961] thermal LNXTHERM:01: registered as thermal_zone1
[    0.756965] ACPI: Thermal Zone [TZS1] (42 C)
[    0.757029] GHES: HEST is not enabled!
[    0.757116] isapnp: Scanning for PnP cards...
[    0.763599] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.767077] Linux agpgart interface v0.103
[    0.767204] agpgart-intel 0000:00:00.0: Intel 945GM Chipset
[    0.767289] agpgart-intel 0000:00:00.0: detected gtt size: 262144K total, 262144K mappable
[    0.767877] agpgart-intel 0000:00:00.0: detected 8192K stolen memory
[    0.768094] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xc0000000
[    0.770602] brd: module loaded
[    0.771890] loop: module loaded
[    0.772141] ata_piix 0000:00:1f.1: version 2.13
[    0.772423] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.772867] scsi0 : ata_piix
[    0.773393] scsi1 : ata_piix
[    0.773475] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1810 irq 14
[    0.773479] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1818 irq 15
[    0.773996] libphy: Fixed MDIO Bus: probed
[    0.774171] tun: Universal TUN/TAP device driver, 1.6
[    0.774174] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.774258] PPP generic driver version 2.4.2
[    0.774323] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.774326] ehci-pci: EHCI PCI platform driver
[    0.774543] ehci-pci 0000:00:1d.7: setting latency timer to 64
[    0.774562] ehci-pci 0000:00:1d.7: EHCI Host Controller
[    0.774572] ehci-pci 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.774593] ehci-pci 0000:00:1d.7: debug port 1
[    0.778516] ehci-pci 0000:00:1d.7: cache line size of 64 is not supported
[    0.778553] ehci-pci 0000:00:1d.7: irq 23, io mem 0xd8444000
[    0.778763] ata2: port disabled--ignoring
[    0.788027] ehci-pci 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.788065] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    0.788069] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.788073] usb usb1: Product: EHCI Host Controller
[    0.788076] usb usb1: Manufacturer: Linux 3.11.0-15-generic ehci_hcd
[    0.788080] usb usb1: SerialNumber: 0000:00:1d.7
[    0.788253] hub 1-0:1.0: USB hub found
[    0.788261] hub 1-0:1.0: 8 ports detected
[    0.788533] ehci-platform: EHCI generic platform driver
[    0.788549] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.788552] ohci-pci: OHCI PCI platform driver
[    0.788571] ohci-platform: OHCI generic platform driver
[    0.788583] uhci_hcd: USB Universal Host Controller Interface driver
[    0.788795] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.788800] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.788808] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.788842] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001820
[    0.788888] usb usb2: New USB device found, idVendor=1d6b, idProduct=0001
[    0.788893] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.788896] usb usb2: Product: UHCI Host Controller
[    0.788900] usb usb2: Manufacturer: Linux 3.11.0-15-generic uhci_hcd
[    0.788903] usb usb2: SerialNumber: 0000:00:1d.0
[    0.789052] hub 2-0:1.0: USB hub found
[    0.789059] hub 2-0:1.0: 2 ports detected
[    0.789373] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.789379] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.789387] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.789434] uhci_hcd 0000:00:1d.1: irq 17, io base 0x00001840
[    0.789481] usb usb3: New USB device found, idVendor=1d6b, idProduct=0001
[    0.789485] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.789489] usb usb3: Product: UHCI Host Controller
[    0.789492] usb usb3: Manufacturer: Linux 3.11.0-15-generic uhci_hcd
[    0.789496] usb usb3: SerialNumber: 0000:00:1d.1
[    0.789639] hub 3-0:1.0: USB hub found
[    0.789646] hub 3-0:1.0: 2 ports detected
[    0.789958] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.789964] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.789971] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.790022] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001860
[    0.790067] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
[    0.790071] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.790075] usb usb4: Product: UHCI Host Controller
[    0.790078] usb usb4: Manufacturer: Linux 3.11.0-15-generic uhci_hcd
[    0.790082] usb usb4: SerialNumber: 0000:00:1d.2
[    0.790220] hub 4-0:1.0: USB hub found
[    0.790229] hub 4-0:1.0: 2 ports detected
[    0.790537] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    0.790543] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    0.790551] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    0.790599] uhci_hcd 0000:00:1d.3: irq 19, io base 0x00001880
[    0.790644] usb usb5: New USB device found, idVendor=1d6b, idProduct=0001
[    0.790649] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.790652] usb usb5: Product: UHCI Host Controller
[    0.790656] usb usb5: Manufacturer: Linux 3.11.0-15-generic uhci_hcd
[    0.790660] usb usb5: SerialNumber: 0000:00:1d.3
[    0.790799] hub 5-0:1.0: USB hub found
[    0.790806] hub 5-0:1.0: 2 ports detected
[    0.791034] i8042: PNP: PS/2 Controller [PNP0303:KBD0,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.791597] i8042: Detected active multiplexing controller, rev 1.1
[    0.791687] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.791696] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    0.791741] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    0.791778] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    0.791818] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    0.791981] mousedev: PS/2 mouse device common for all mice
[    0.792234] rtc_cmos 00:07: RTC can wake from S4
[    0.792409] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
[    0.792446] rtc_cmos 00:07: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    0.792563] device-mapper: uevent: version 1.0.3
[    0.792679] device-mapper: ioctl: 4.25.0-ioctl (2013-06-26) initialised: dm-devel@redhat.com
[    0.792711] platform eisa.0: Probing EISA bus 0
[    0.792744] platform eisa.0: EISA: Detected 0 cards
[    0.792756] cpufreq-nforce2: No nForce2 chipset.
[    0.792838] cpuidle: using governor ladder
[    0.792933] cpuidle: using governor menu
[    0.792948] ledtrig-cpu: registered to indicate activity on CPUs
[    0.793092] TCP: cubic registered
[    0.793273] NET: Registered protocol family 10
[    0.793594] NET: Registered protocol family 17
[    0.793615] Key type dns_resolver registered
[    0.793860] Using IPI No-Shortcut mode
[    0.793988] PM: Hibernation image not present or could not be loaded.
[    0.793994] Loading module verification certificates
[    0.800298] MODSIGN: Loaded cert 'Magrathea: Glacier signing key: 20cb30850ee856675c288816dd8cff0153e91a4b'
[    0.800318] registered taskstats version 1
[    0.800919] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    0.803921] Key type trusted registered
[    0.806828] Key type encrypted registered
[    0.809743] AppArmor: AppArmor sha1 policy hashing enabled
[    0.810221]   Magic number: 14:238:671
[    0.810350] rtc_cmos 00:07: setting system clock to 2014-01-20 06:39:44 UTC (1390199984)
[    0.810739] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.810742] EDD information not available.
[    0.940427] ata1.00: ATAPI: HL-DT-ST DVDRAM GSA-T10N, TM01, max UDMA/33
[    0.956301] ata1.00: configured for UDMA/33
[    1.111917] isapnp: No Plug & Play device found
[    1.156043] usb 1-8: new high-speed USB device number 3 using ehci-pci
[    1.292916] usb 1-8: New USB device found, idVendor=0ace, idProduct=1215
[    1.292924] usb 1-8: New USB device strings: Mfr=16, Product=32, SerialNumber=0
[    1.292930] usb 1-8: Product: USB Device
[    1.292937] usb 1-8: Manufacturer: ZyDAS
[    1.299042] ACPI: Battery Slot [BAT0] (battery present)
[    1.303019] scsi 0:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-T10N  TM01 PQ: 0 ANSI: 5
[    1.308257] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.308261] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.308462] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    1.308601] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    1.309197] Freeing unused kernel memory: 880K (c1972000 - c1a4e000)
[    1.309308] Write protecting the kernel text: 6360k
[    1.309450] Write protecting the kernel read-only data: 2700k
[    1.309452] NX-protecting the kernel data: 5928k
[    1.327010] systemd-udevd[100]: starting version 204
[    1.387237] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.387256] r8169 0000:04:00.0: can't disable ASPM; OS doesn't have ASPM control
[    1.387531] r8169 0000:04:00.0: irq 43 for MSI/MSI-X
[    1.387789] r8169 0000:04:00.0 eth0: RTL8101e at 0xf841a000, 00:16:d3:80:26:49, XID 14000000 IRQ 43
[    1.392573] sdhci: Secure Digital Host Controller Interface driver
[    1.392577] sdhci: Copyright(c) Pierre Ossman
[    1.400304] sdhci-pci 0000:0a:09.1: SDHCI controller found [1180:0822] (rev 19)
[    1.401413] sdhci-pci 0000:0a:09.1: Will use DMA mode even though HW doesn't fully claim to support it.
[    1.401424] mmc0: no vqmmc regulator found
[    1.401426] mmc0: no vmmc regulator found
[    1.402434] sdhci-pci 0000:0a:09.1: Will use DMA mode even though HW doesn't fully claim to support it.
[    1.403660] mmc0: SDHCI controller on PCI [0000:0a:09.1] using DMA
[    1.413982] ahci 0000:00:1f.2: version 3.0
[    1.414234] ahci 0000:00:1f.2: irq 44 for MSI/MSI-X
[    1.414327] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 4 ports 1.5 Gbps 0x5 impl SATA mode
[    1.414332] ahci 0000:00:1f.2: flags: 64bit ncq pm led clo pio slum part 
[    1.414340] ahci 0000:00:1f.2: setting latency timer to 64
[    1.422242] scsi2 : ahci
[    1.425227] scsi3 : ahci
[    1.427968] scsi4 : ahci
[    1.431594] scsi5 : ahci
[    1.431734] ata3: SATA max UDMA/133 abar m1024@0xd8444400 port 0xd8444500 irq 44
[    1.431737] ata4: DUMMY
[    1.431742] ata5: SATA max UDMA/133 abar m1024@0xd8444400 port 0xd8444600 irq 44
[    1.431744] ata6: DUMMY
[    1.504161] firewire_ohci 0000:0a:09.0: added OHCI v1.10 device as card 0, 4 IR + 4 IT contexts, quirks 0x11
[    1.532137] usb 3-2: new low-speed USB device number 2 using uhci_hcd
[    1.705518] usb 3-2: New USB device found, idVendor=0bc7, idProduct=0006
[    1.705526] usb 3-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.705533] usb 3-2: Product: RF receiver
[    1.705539] usb 3-2: Manufacturer: X10 WTI
[    1.748129] ata5: SATA link down (SStatus 0 SControl 300)
[    1.748172] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.749268] ata3.00: ACPI cmd ef/90:03:00:00:00:a0 (SET FEATURES) rejected by device (Stat=0x51 Err=0x04)
[    1.781433] ata3.00: ATA-7: WDC WD1200BEVS-07LAT0, 01.06M01, max UDMA/133
[    1.781438] ata3.00: 234441648 sectors, multi 16: LBA48 NCQ (depth 1), AA
[    1.782526] ata3.00: ACPI cmd ef/90:03:00:00:00:a0 (SET FEATURES) rejected by device (Stat=0x51 Err=0x04)
[    1.782792] ata3.00: configured for UDMA/133
[    1.783041] scsi 2:0:0:0: Direct-Access     ATA      WDC WD1200BEVS-0 01.0 PQ: 0 ANSI: 5
[    1.783312] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    1.783361] sd 2:0:0:0: [sda] 234441648 512-byte logical blocks: (120 GB/111 GiB)
[    1.783548] sd 2:0:0:0: [sda] Write Protect is off
[    1.783553] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.783642] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.821509]  sda: sda1 sda2 < sda5 >
[    1.822246] sd 2:0:0:0: [sda] Attached SCSI disk
[    2.004190] firewire_core 0000:0a:09.0: created device fw0: GUID 07e40a0094267002, S400
[    2.194786] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
[    2.194793] EXT4-fs (sda1): write access will be enabled during recovery
[    2.994764] EXT4-fs (sda1): recovery complete
[    3.001395] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    7.408135] Adding 1036284k swap on /dev/sda5.  Priority:-1 extents:1 across:1036284k FS
[    8.696787] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    9.199614] systemd-udevd[270]: starting version 204
[   11.102598] lp: driver loaded but no devices found
[   12.465694] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   13.807535] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   13.807621] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input4
[   14.177540] wmi: Mapper loaded
[   14.195940] intel_rng: FWH not detected
[   14.524959] r592 0000:0a:09.2: setting latency timer to 64
[   14.525091] r592: driver successfully loaded
[   14.644793] ACPI Warning: 0x00001028-0x0000102f SystemIO conflicts with Region \PMIO 1 (20130517/utaddress-251)
[   14.644805] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   14.644810] ACPI Warning: 0x000011b0-0x000011bf SystemIO conflicts with Region \GPIO 1 (20130517/utaddress-251)
[   14.644817] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   14.644819] ACPI Warning: 0x00001180-0x000011af SystemIO conflicts with Region \GPIO 1 (20130517/utaddress-251)
[   14.644825] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   14.644828] lpc_ich: Resource conflict(s) found affecting gpio_ich
[   14.998769] leds_ss4200: no LED devices found
[   15.070074] [drm] Initialized drm 1.1.0 20060810
[   15.099322] microcode: CPU0 sig=0x6e8, pf=0x20, revision=0x39
[   15.517593] r852 0000:0a:09.3: enabling device (0000 -> 0002)
[   15.517701] r852 0000:0a:09.3: setting latency timer to 64
[   15.519729] r852: Non dma capable device detected, dma disabled
[   15.519748] r852: driver loaded successfully
[   15.589163] psmouse serio4: synaptics: Touchpad model: 1, fw: 5.9, id: 0x23aeb3, caps: 0xa04713/0x10008/0x0, board id: 3655, fw id: 28762
[   15.620704] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input5
[   15.723441] [drm] Memory usable by graphics device = 256M
[   15.723454] i915 0000:00:02.0: setting latency timer to 64
[   15.725041] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   15.725047] [drm] Driver supports precise vblank timestamp query.
[   15.725128] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   15.813266] [drm] initialized overlay support
[   16.340062] fbcon: inteldrmfb (fb0) is primary device
[   16.696105] Console: switching to colour frame buffer device 160x50
[   16.702478] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[   16.702482] i915 0000:00:02.0: registered panic notifier
[   16.702493] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   16.703954] snd_hda_intel 0000:00:1b.0: irq 45 for MSI/MSI-X
[   16.811641] SKU: Nid=0x0 sku_cfg=0x0000952d
[   16.811646] SKU: port_connectivity=0x0
[   16.811648] SKU: enable_pcbeep=0x1
[   16.811650] SKU: check_sum=0x00000000
[   16.811652] SKU: customization=0x00000000
[   16.811655] SKU: external_amp=0x5
[   16.811657] SKU: platform_type=0x1
[   16.811659] SKU: swap=0x0
[   16.811661] SKU: override=0x1
[   16.811884] autoconfig: line_outs=1 (0x14/0x0/0x0/0x0/0x0) type:hp
[   16.811887]    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   16.811890]    hp_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   16.811892]    mono: mono_out=0x0
[   16.811895]    dig-out=0x1e/0x0
[   16.811897]    inputs:
[   16.811900]      Mic=0x18
[   16.811902]      Line=0x1a
[   16.811904]      CD=0x1c
[   16.811907] realtek: Enabling init ASM_ID=0x952d CODEC_ID=10ec0883
[   16.912510] input: HDA Intel Line as /devices/pci0000:00/0000:00:1b.0/sound/card0/input6
[   16.912662] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[   17.097119] cfg80211: Calling CRDA to update world regulatory domain
[   17.288054] Registered IR keymap rc-medion-x10-or2x
[   17.288195] input: X10 WTI RF receiver as /devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2:1.0/rc/rc0/input8
[   17.288291] rc0: X10 WTI RF receiver as /devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2:1.0/rc/rc0
[   17.288354] input: X10 WTI RF receiver mouse as /devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2:1.0/input/input9
[   17.288480] usbcore: registered new interface driver ati_remote
[   17.666578] type=1400 audit(1390200001.350:2): apparmor="STATUS" operation="profile_load" parent=383 profile="unconfined" name="/sbin/dhclient" pid=393 comm="apparmor_parser"
[   17.666593] type=1400 audit(1390200001.350:3): apparmor="STATUS" operation="profile_load" parent=383 profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=393 comm="apparmor_parser"
[   17.666602] type=1400 audit(1390200001.350:4): apparmor="STATUS" operation="profile_load" parent=383 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=393 comm="apparmor_parser"
[   17.667621] type=1400 audit(1390200001.350:5): apparmor="STATUS" operation="profile_replace" parent=383 profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=393 comm="apparmor_parser"
[   17.667632] type=1400 audit(1390200001.350:6): apparmor="STATUS" operation="profile_replace" parent=383 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=393 comm="apparmor_parser"
[   17.668216] type=1400 audit(1390200001.354:7): apparmor="STATUS" operation="profile_replace" parent=383 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=393 comm="apparmor_parser"
[   17.884057] usb 1-8: reset high-speed USB device number 3 using ehci-pci
[   18.179697] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   18.180069] zd1211rw 1-8:1.0: phy0
[   18.180110] usbcore: registered new interface driver zd1211rw
[   18.190685] acer_wmi: Acer Laptop ACPI-WMI Extras
[   18.191901] acer_wmi: Disabling ACPI video driver
[   18.204493] input: Acer BMA150 accelerometer as /devices/virtual/input/input10
[   18.213997] microcode: CPU1 sig=0x6e8, pf=0x20, revision=0x39
[   18.530755] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[   20.029106] init: failsafe main process (447) killed by TERM signal
[   20.297215] cfg80211: World regulatory domain updated:
[   20.297222] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   20.297226] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.297230] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.297233] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   20.297236] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   20.297239] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   22.768470] Bluetooth: Core ver 2.16
[   22.768507] NET: Registered protocol family 31
[   22.768510] Bluetooth: HCI device and connection manager initialized
[   22.768521] Bluetooth: HCI socket layer initialized
[   22.768526] Bluetooth: L2CAP socket layer initialized
[   22.768535] Bluetooth: SCO socket layer initialized
[   23.035008] Bluetooth: RFCOMM TTY layer initialized
[   23.035028] Bluetooth: RFCOMM socket layer initialized
[   23.035030] Bluetooth: RFCOMM ver 1.11
[   23.492061] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   23.492067] Bluetooth: BNEP filters: protocol multicast
[   23.492085] Bluetooth: BNEP socket layer initialized
[   23.748825] init: avahi-cups-reload main process (636) terminated with status 1
[   24.227036] ppdev: user-space parallel port driver
[   25.305379] type=1400 audit(1390200008.990:8): apparmor="STATUS" operation="profile_load" parent=659 profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=663 comm="apparmor_parser"
[   25.305395] type=1400 audit(1390200008.990:9): apparmor="STATUS" operation="profile_load" parent=659 profile="unconfined" name="/usr/sbin/cupsd" pid=663 comm="apparmor_parser"
[   25.306580] type=1400 audit(1390200008.990:10): apparmor="STATUS" operation="profile_replace" parent=659 profile="unconfined" name="/usr/sbin/cupsd" pid=663 comm="apparmor_parser"
[   27.249512] init: xbmc main process (669) terminated with status 1
[   27.249554] init: xbmc main process ended, respawning
[   27.264378] init: xbmc main process (737) terminated with status 1
[   27.264421] init: xbmc main process ended, respawning
[   27.284678] init: xbmc main process (739) terminated with status 1
[   27.284724] init: xbmc main process ended, respawning
[   27.303779] init: xbmc main process (741) terminated with status 1
[   27.303823] init: xbmc main process ended, respawning
[   27.321916] init: xbmc main process (743) terminated with status 1
[   27.321956] init: xbmc main process ended, respawning
[   27.341820] init: xbmc main process (745) terminated with status 1
[   27.341863] init: xbmc main process ended, respawning
[   27.358533] init: xbmc main process (747) terminated with status 1
[   27.358576] init: xbmc main process ended, respawning
[   27.375352] init: xbmc main process (749) terminated with status 1
[   27.375395] init: xbmc main process ended, respawning
[   27.392571] init: xbmc main process (751) terminated with status 1
[   27.392614] init: xbmc main process ended, respawning
[   27.409661] init: xbmc main process (753) terminated with status 1
[   27.409709] init: xbmc main process ended, respawning
[   27.426682] init: xbmc main process (755) terminated with status 1
[   27.426726] init: xbmc respawning too fast, stopped
[   29.996970] r8169 0000:04:00.0 eth0: link down
[   29.997004] r8169 0000:04:00.0 eth0: link down
[   29.997038] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   29.997474] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   30.470631] zd1211rw 1-8:1.0: firmware version 4725
[   30.525638] zd1211rw 1-8:1.0: zd1211b chip 0ace:1215 v4810 high 00-60-b3 UW2453_RF pa0 g7---
[   30.645135] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   30.645169] cfg80211: Calling CRDA for country: DE
[   30.645972] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   30.651377] cfg80211: Regulatory domain changed to country: DE
[   30.651386] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   30.651389] cfg80211:   (2400000 KHz - 2483500 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   30.651392] cfg80211:   (5150000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   30.651395] cfg80211:   (5250000 KHz - 5350000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   30.651398] cfg80211:   (5470000 KHz - 5725000 KHz @ 40000 KHz), (N/A, 2698 mBm)
[   30.651401] cfg80211:   (57240000 KHz - 65880000 KHz @ 2160000 KHz), (N/A, 4000 mBm)
[   31.558366] r8169 0000:04:00.0 eth0: link up
[   31.558381] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   32.957782] type=1400 audit(1390200016.642:11): apparmor="STATUS" operation="profile_load" parent=815 profile="unconfined" name="/usr/lib/i386-linux-gnu/lightdm-remote-session-freerdp/freerdp-session-wrapper" pid=821 comm="apparmor_parser"
[   32.957798] type=1400 audit(1390200016.642:12): apparmor="STATUS" operation="profile_load" parent=815 profile="unconfined" name="chromium_browser" pid=821 comm="apparmor_parser"
[   32.958679] type=1400 audit(1390200016.642:13): apparmor="STATUS" operation="profile_replace" parent=815 profile="unconfined" name="chromium_browser" pid=821 comm="apparmor_parser"
[   32.975600] type=1400 audit(1390200016.658:14): apparmor="STATUS" operation="profile_load" parent=815 profile="unconfined" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=820 comm="apparmor_parser"
[   32.975615] type=1400 audit(1390200016.658:15): apparmor="STATUS" operation="profile_load" parent=815 profile="unconfined" name="chromium_browser" pid=820 comm="apparmor_parser"
[   32.976661] type=1400 audit(1390200016.662:16): apparmor="STATUS" operation="profile_replace" parent=815 profile="unconfined" name="chromium_browser" pid=820 comm="apparmor_parser"
[   32.981549] type=1400 audit(1390200016.666:17): apparmor="STATUS" operation="profile_replace" parent=815 profile="unconfined" name="/sbin/dhclient" pid=823 comm="apparmor_parser"
[   32.981564] type=1400 audit(1390200016.666:18): apparmor="STATUS" operation="profile_replace" parent=815 profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=823 comm="apparmor_parser"
[   32.981574] type=1400 audit(1390200016.666:19): apparmor="STATUS" operation="profile_replace" parent=815 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=823 comm="apparmor_parser"
[   32.982593] type=1400 audit(1390200016.666:20): apparmor="STATUS" operation="profile_replace" parent=815 profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=823 comm="apparmor_parser"
[   34.744694] init: alsa-restore main process (931) terminated with status 99
[   35.013128] wlan0: authenticate with 00:22:57:62:3e:86
[   35.234774] wlan0: send auth to 00:22:57:62:3e:86 (try 1/3)
[   35.236252] wlan0: authenticated
[   35.236434] zd1211rw 1-8:1.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[   35.236439] zd1211rw 1-8:1.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   35.236443] zd1211rw 1-8:1.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   35.240085] wlan0: associate with 00:22:57:62:3e:86 (try 1/3)
[   35.243007] wlan0: RX AssocResp from 00:22:57:62:3e:86 (capab=0x471 status=0 aid=2)
[   35.243745] wlan0: associated
[   35.243778] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

```

---

### Post by ian-weisser on 2014-01-20
I think your diagnosis of the symptoms is correct.

I don't see your USB dongle detected at all by the kernel on Boot #1. That could be a fault with the dongle, or with the USB port. When I see hardware-not-detected, I usually see faulty hardware. Since other USB hardware seems to work normally, try the wireless dongle in a different USB port.

If you can rule out a faulty USB port, then the problem seems to be a faulty wifi dongle.

---

### Post by jonckheerestijn on 2014-01-21
I think we can rule out both a faulty port and dongle, since everything works fine from the third boot on. Anyway, I can't check more thoroughly since it is a 'built-in dongle' (i.e. dongle hardware which is plugged in internally into an usb-hub). Also in Windows, everything works from first boot on.

Moreover, the led of the WiFi is working on first boot up to the point where it starts booting Ubuntu. Then it switches off. 
Somehow something seems to go wrong with the 'warm-up' by Ubuntu(?)

---

### Post by jonckheerestijn on 2014-01-24
At first boot, if I let the computer run for a while, the dmesg starts flooding with these messages, every 10-15 seconds

```
[ 1510.604210] usb 1-8: new high-speed USB device number 42 using ehci-pci[ 1510.737644] usb 1-8: New USB device found, idVendor=0ace, idProduct=1215
[ 1510.737656] usb 1-8: New USB device strings: Mfr=16, Product=32, SerialNumber=0
[ 1510.737664] usb 1-8: Product: USB Device
[ 1510.737670] usb 1-8: Manufacturer: ZyDAS
[ 1510.796493] zd1211rw 1-8:1.0: couldn't reset usb device. Error number -19
[ 1510.796747] usb 1-8: USB disconnect, device number 42
```

Does this add information for a possible solution?

---

