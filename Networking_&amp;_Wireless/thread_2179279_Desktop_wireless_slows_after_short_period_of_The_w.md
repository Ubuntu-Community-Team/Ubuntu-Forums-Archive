---
title: "Desktop wireless slows after short period of The wireless card I have installed isuse"
date: 2013-10-07
forum: Networking &amp; Wireless
---

### Post by Vikas_Biliyar on 2013-10-07
Hello,

I have a user-built desktop that has been having a strange issue with its wireless. I'm trying to figure out if the wireless card itself is the issue, if there's a firmware issue, or even if I have a virus of some sort. I switched to using a wireless network (from wired) a few months ago and have had this problem ever since.

Description: Following a reboot or a network-manager restart, my transfer speeds through the wireless are pretty standard at a little over 1 MBps down/up. After using the computer for a period of time, though, my down/up speeds drop to ~260/60 MBps. When I monitor the traffic with "tcptrack -i wlan0," it doesn't show any other usage from my computer. I don't run into these problems when connecting to it with my laptop (running Windows Vista), so I don't think it's network-wide issue.
 
- Running Ubuntu 13.04
- Wireless Card: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter (rev 01)

Various outputs:

```
dmesg output:

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.8.0-31-generic (buildd@panlong) (gcc version 4.7.3 (Ubuntu/Linaro 4.7.3-1ubuntu1) ) #46-Ubuntu SMP Tue Sep 10 20:03:44 UTC 2013 (Ubuntu 3.8.0-31.46-generic 3.8.13.8)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.8.0-31-generic root=UUID=3ca7092d-11e8-44c2-84fa-a0777fb1ce1a ro quiet splash vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009d7ff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009d800-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x000000001fffffff] usable
[    0.000000] BIOS-e820: [mem 0x0000000020000000-0x00000000201fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000020200000-0x0000000040003fff] usable
[    0.000000] BIOS-e820: [mem 0x0000000040004000-0x0000000040004fff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000040005000-0x00000000ccf6efff] usable
[    0.000000] BIOS-e820: [mem 0x00000000ccf6f000-0x00000000cd84afff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000cd84b000-0x00000000cd8d5fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000cd8d6000-0x00000000cd975fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000cd976000-0x00000000ce149fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ce14a000-0x00000000ce14afff] usable
[    0.000000] BIOS-e820: [mem 0x00000000ce14b000-0x00000000ce18dfff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000ce18e000-0x00000000cebf1fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000cebf2000-0x00000000ceff1fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ceff2000-0x00000000ceffffff] usable
[    0.000000] BIOS-e820: [mem 0x00000000cf800000-0x00000000df9fffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000f8000000-0x00000000fbffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed00000-0x00000000fed03fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed1c000-0x00000000fed1ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ff000000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000021f5fffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.7 present.
[    0.000000] DMI: To Be Filled By O.E.M. To Be Filled By O.E.M./Z77 Extreme4, BIOS P2.20 09/13/2012
[    0.000000] e820: update [mem 0x00000000-0x0000ffff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] No AGP bridge found
[    0.000000] e820: last_pfn = 0x21f600 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-E7FFF uncachable
[    0.000000]   E8000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask E00000000 write-back
[    0.000000]   1 base 200000000 mask FE0000000 write-back
[    0.000000]   2 base 0E0000000 mask FE0000000 uncachable
[    0.000000]   3 base 0D0000000 mask FF0000000 uncachable
[    0.000000]   4 base 0CF800000 mask FFF800000 uncachable
[    0.000000]   5 base 21F800000 mask FFF800000 uncachable
[    0.000000]   6 base 21F600000 mask FFFE00000 uncachable
[    0.000000]   7 disabled
[    0.000000]   8 disabled
[    0.000000]   9 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 8GB, type WB
[    0.000000] reg 1, base: 8GB, range: 512MB, type WB
[    0.000000] reg 2, base: 3584MB, range: 512MB, type UC
[    0.000000] reg 3, base: 3328MB, range: 256MB, type UC
[    0.000000] reg 4, base: 3320MB, range: 8MB, type UC
[    0.000000] reg 5, base: 8696MB, range: 8MB, type UC
[    0.000000] reg 6, base: 8694MB, range: 2MB, type UC
[    0.000000] total RAM covered: 7918M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K     chunk_size: 16M     num_reg: 8      lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 3GB, range: 256MB, type WB
[    0.000000] reg 3, base: 3320MB, range: 8MB, type UC
[    0.000000] reg 4, base: 4GB, range: 4GB, type WB
[    0.000000] reg 5, base: 8GB, range: 512MB, type WB
[    0.000000] reg 6, base: 8694MB, range: 2MB, type UC
[    0.000000] reg 7, base: 8696MB, range: 8MB, type UC
[    0.000000] e820: update [mem 0xcf800000-0xffffffff] usable ==> reserved
[    0.000000] e820: last_pfn = 0xcf000 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [mem 0x000fd8a0-0x000fd8af] mapped at [ffff8800000fd8a0]
[    0.000000] initial memory mapped: [mem 0x00000000-0x1fffffff]
[    0.000000] Base memory trampoline at [ffff880000097000] 97000 size 24576
[    0.000000] init_memory_mapping: [mem 0x00000000-0xceffffff]
[    0.000000]  [mem 0x00000000-0xceffffff] page 2M
[    0.000000] kernel direct mapping tables up to 0xceffffff @ [mem 0x1fffb000-0x1fffffff]
[    0.000000] init_memory_mapping: [mem 0x100000000-0x21f5fffff]
[    0.000000]  [mem 0x100000000-0x21f5fffff] page 2M
[    0.000000] kernel direct mapping tables up to 0x21f5fffff @ [mem 0xceffa000-0xceffffff]
[    0.000000] RAMDISK: [mem 0x360fc000-0x37075fff]
[    0.000000] ACPI: RSDP 00000000000f0490 00024 (v02 ALASKA)
[    0.000000] ACPI: XSDT 00000000cd95a080 0007C (v01 ALASKA    A M I 01072009 AMI  00010013)
[    0.000000] ACPI: FACP 00000000cd963f70 0010C (v05 ALASKA    A M I 01072009 AMI  00010013)
[    0.000000] ACPI: DSDT 00000000cd95a190 09DDD (v02 ALASKA    A M I 00000022 INTL 20051117)
[    0.000000] ACPI: FACS 00000000cd974080 00040
[    0.000000] ACPI: APIC 00000000cd964080 00072 (v03 ALASKA    A M I 01072009 AMI  00010013)
[    0.000000] ACPI: FPDT 00000000cd9640f8 00044 (v01 ALASKA    A M I 01072009 AMI  00010013)
[    0.000000] ACPI: MCFG 00000000cd964140 0003C (v01 ALASKA    A M I 01072009 MSFT 00000097)
[    0.000000] ACPI: SSDT 00000000cd964180 007E1 (v01 Intel_ AoacTabl 00001000 INTL 20091112)
[    0.000000] ACPI: AAFT 00000000cd964968 00112 (v01 ALASKA OEMAAFT  01072009 MSFT 00000097)
[    0.000000] ACPI: HPET 00000000cd964a80 00038 (v01 ALASKA    A M I 01072009 AMI. 00000005)
[    0.000000] ACPI: SSDT 00000000cd964ab8 0036D (v01 SataRe SataTabl 00001000 INTL 20091112)
[    0.000000] ACPI: SSDT 00000000cd964e28 009AA (v01  PmRef  Cpu0Ist 00003000 INTL 20051117)
[    0.000000] ACPI: SSDT 00000000cd9657d8 00A92 (v01  PmRef    CpuPm 00003000 INTL 20051117)
[    0.000000] ACPI: BGRT 00000000cd966270 00038 (v00 ALASKA    A M I 01072009 AMI  00010013)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x000000021f5fffff]
[    0.000000] Initmem setup node 0 [mem 0x00000000-0x21f5fffff]
[    0.000000]   NODE_DATA [mem 0x21f5fb000-0x21f5fffff]
[    0.000000]  [ffffea0000000000-ffffea00087fffff] PMD -> [ffff880217000000-ffff88021ebfffff] on node 0
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00010000-0x00ffffff]
[    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
[    0.000000]   Normal   [mem 0x100000000-0x21f5fffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00010000-0x0009cfff]
[    0.000000]   node   0: [mem 0x00100000-0x1fffffff]
[    0.000000]   node   0: [mem 0x20200000-0x40003fff]
[    0.000000]   node   0: [mem 0x40005000-0xccf6efff]
[    0.000000]   node   0: [mem 0xcd84b000-0xcd8d5fff]
[    0.000000]   node   0: [mem 0xce14a000-0xce14afff]
[    0.000000]   node   0: [mem 0xce18e000-0xcebf1fff]
[    0.000000]   node   0: [mem 0xceff2000-0xceffffff]
[    0.000000]   node   0: [mem 0x100000000-0x21f5fffff]
[    0.000000] On node 0 totalpages: 2018809
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 6 pages reserved
[    0.000000]   DMA zone: 3911 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 13090 pages used for memmap
[    0.000000]   DMA32 zone: 824650 pages, LIFO batch:31
[    0.000000]   Normal zone: 18392 pages used for memmap
[    0.000000]   Normal zone: 1158696 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x04] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x06] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0xff] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a701 base: 0xfed00000
[    0.000000] smpboot: Allowing 4 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 0000000020000000 - 0000000020200000
[    0.000000] PM: Registered nosave memory: 0000000040004000 - 0000000040005000
[    0.000000] PM: Registered nosave memory: 00000000ccf6f000 - 00000000cd84b000
[    0.000000] PM: Registered nosave memory: 00000000cd8d6000 - 00000000cd976000
[    0.000000] PM: Registered nosave memory: 00000000cd976000 - 00000000ce14a000
[    0.000000] PM: Registered nosave memory: 00000000ce14b000 - 00000000ce18e000
[    0.000000] PM: Registered nosave memory: 00000000cebf2000 - 00000000ceff2000
[    0.000000] PM: Registered nosave memory: 00000000cf000000 - 00000000cf800000
[    0.000000] PM: Registered nosave memory: 00000000cf800000 - 00000000dfa00000
[    0.000000] PM: Registered nosave memory: 00000000dfa00000 - 00000000f8000000
[    0.000000] PM: Registered nosave memory: 00000000f8000000 - 00000000fc000000
[    0.000000] PM: Registered nosave memory: 00000000fc000000 - 00000000fec00000
[    0.000000] PM: Registered nosave memory: 00000000fec00000 - 00000000fec01000
[    0.000000] PM: Registered nosave memory: 00000000fec01000 - 00000000fed00000
[    0.000000] PM: Registered nosave memory: 00000000fed00000 - 00000000fed04000
[    0.000000] PM: Registered nosave memory: 00000000fed04000 - 00000000fed1c000
[    0.000000] PM: Registered nosave memory: 00000000fed1c000 - 00000000fed20000
[    0.000000] PM: Registered nosave memory: 00000000fed20000 - 00000000fee00000
[    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
[    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ff000000
[    0.000000] PM: Registered nosave memory: 00000000ff000000 - 0000000100000000
[    0.000000] e820: [mem 0xdfa00000-0xf7ffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 28 pages/cpu @ffff88021f200000 s84928 r8192 d21568 u524288
[    0.000000] pcpu-alloc: s84928 r8192 d21568 u524288 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 1987257
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.8.0-31-generic root=UUID=3ca7092d-11e8-44c2-84fa-a0777fb1ce1a ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] __ex_table already sorted, skipping sort
[    0.000000] xsave: enabled xstate_bv 0x7, cntxt size 0x340
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 7850064k/8902656k available (7014k kernel code, 827420k absent, 225172k reserved, 6228k data, 996k init)
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=4.
[    0.000000] NR_IRQS:16640 nr_irqs:712 16
[    0.000000] Extended CMOS year: 2000
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 32505856 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.004000] tsc: Detected 3399.960 MHz processor
[    0.000001] Calibrating delay loop (skipped), value calculated using timer frequency.. 6799.92 BogoMIPS (lpj=13599840)
[    0.000003] pid_max: default: 32768 minimum: 301
[    0.000018] Security Framework initialized
[    0.000026] AppArmor: AppArmor initialized
[    0.000027] Yama: becoming mindful.
[    0.000356] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.001773] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.002400] Mount-cache hash table entries: 256
[    0.002507] Initializing cgroup subsys cpuacct
[    0.002508] Initializing cgroup subsys memory
[    0.002512] Initializing cgroup subsys devices
[    0.002513] Initializing cgroup subsys freezer
[    0.002514] Initializing cgroup subsys blkio
[    0.002515] Initializing cgroup subsys perf_event
[    0.002517] Initializing cgroup subsys hugetlb
[    0.002534] CPU: Physical Processor ID: 0
[    0.002534] CPU: Processor Core ID: 0
[    0.002538] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
[    0.002538] ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
[    0.002799] mce: CPU supports 9 MCE banks
[    0.002808] CPU0: Thermal monitoring enabled (TM1)
[    0.002813] process: using mwait in idle threads
[    0.002816] Last level iTLB entries: 4KB 512, 2MB 0, 4MB 0
[    0.002816] Last level dTLB entries: 4KB 512, 2MB 32, 4MB 32
[    0.002816] tlb_flushall_shift: 1
[    0.002928] Freeing SMP alternatives: 24k freed
[    0.004430] ACPI: Core revision 20121018
[    0.074669] ftrace: allocating 26713 entries in 105 pages
[    0.084043] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.123702] smpboot: CPU0: Intel(R) Core(TM) i5-3570K CPU @ 3.40GHz (fam: 06, model: 3a, stepping: 09)
[    0.123707] TSC deadline timer enabled
[    0.123710] Performance Events: PEBS fmt1+, 16-deep LBR, IvyBridge events, Intel PMU driver.
[    0.123714] ... version:                3
[    0.123715] ... bit width:              48
[    0.123715] ... generic registers:      8
[    0.123716] ... value mask:             0000ffffffffffff
[    0.123717] ... max period:             000000007fffffff
[    0.123717] ... fixed-purpose events:   3
[    0.123718] ... event mask:             00000007000000ff
[    0.137753] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.124389] smpboot: Booting Node   0, Processors  #1 #2 #3 OK
[    0.164716] Brought up 4 CPUs
[    0.164718] smpboot: Total of 4 processors activated (27199.68 BogoMIPS)
[    0.167264] devtmpfs: initialized
[    0.167902] EVM: security.selinux
[    0.167903] EVM: security.SMACK64
[    0.167903] EVM: security.capability
[    0.167930] PM: Registering ACPI NVS region [mem 0xcd8d6000-0xcd975fff] (655360 bytes)
[    0.167936] PM: Registering ACPI NVS region [mem 0xce14b000-0xce18dfff] (274432 bytes)
[    0.168408] regulator-dummy: no parameters
[    0.168436] NET: Registered protocol family 16
[    0.168525] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.168527] ACPI: bus type pci registered
[    0.168559] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf8000000-0xfbffffff] (base 0xf8000000)
[    0.168561] PCI: MMCONFIG at [mem 0xf8000000-0xfbffffff] reserved in E820
[    0.174067] PCI: Using configuration type 1 for base access
[    0.174585] bio: create slab <bio-0> at 0
[    0.174633] ACPI: Added _OSI(Module Device)
[    0.174634] ACPI: Added _OSI(Processor Device)
[    0.174635] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.174636] ACPI: Added _OSI(Processor Aggregator Device)
[    0.175585] ACPI: EC: Look up EC in DSDT
[    0.176597] ACPI: Executed 1 blocks of module-level executable AML code
[    0.178542] ACPI: SSDT 00000000cd7f8018 0083B (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.178779] ACPI: Dynamic OEM Table Load:
[    0.178780] ACPI: SSDT           (null) 0083B (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.178954] ACPI: SSDT 00000000cd7f9a98 00303 (v01  PmRef    ApIst 00003000 INTL 20051117)
[    0.179208] ACPI: Dynamic OEM Table Load:
[    0.179210] ACPI: SSDT           (null) 00303 (v01  PmRef    ApIst 00003000 INTL 20051117)
[    0.179305] ACPI: SSDT 00000000cd7fac18 00119 (v01  PmRef    ApCst 00003000 INTL 20051117)
[    0.179541] ACPI: Dynamic OEM Table Load:
[    0.179542] ACPI: SSDT           (null) 00119 (v01  PmRef    ApCst 00003000 INTL 20051117)
[    0.179903] ACPI: Interpreter enabled
[    0.179905] ACPI: (supports S0 S3 S4 S5)
[    0.179917] ACPI: Using IOAPIC for interrupt routing
[    0.183273] ACPI: No dock devices found.
[    0.183276] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.183420] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-3e])
[    0.183422] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.183835] PCI host bridge to bus 0000:00
[    0.183837] pci_bus 0000:00: root bus resource [bus 00-3e]
[    0.183838] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
[    0.183839] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
[    0.183841] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    0.183842] pci_bus 0000:00: root bus resource [mem 0x000d0000-0x000d3fff]
[    0.183843] pci_bus 0000:00: root bus resource [mem 0x000d4000-0x000d7fff]
[    0.183844] pci_bus 0000:00: root bus resource [mem 0x000d8000-0x000dbfff]
[    0.183845] pci_bus 0000:00: root bus resource [mem 0x000dc000-0x000dffff]
[    0.183846] pci_bus 0000:00: root bus resource [mem 0x000e0000-0x000e3fff]
[    0.183847] pci_bus 0000:00: root bus resource [mem 0x000e4000-0x000e7fff]
[    0.183849] pci_bus 0000:00: root bus resource [mem 0xdfa00000-0xfeafffff]
[    0.183855] pci 0000:00:00.0: [8086:0150] type 00 class 0x060000
[    0.183881] pci 0000:00:02.0: [8086:0162] type 00 class 0x030000
[    0.183889] pci 0000:00:02.0: reg 10: [mem 0xf7400000-0xf77fffff 64bit]
[    0.183893] pci 0000:00:02.0: reg 18: [mem 0xe0000000-0xefffffff 64bit pref]
[    0.183896] pci 0000:00:02.0: reg 20: [io  0xf000-0xf03f]
[    0.183937] pci 0000:00:14.0: [8086:1e31] type 00 class 0x0c0330
[    0.183956] pci 0000:00:14.0: reg 10: [mem 0xf7c00000-0xf7c0ffff 64bit]
[    0.184022] pci 0000:00:14.0: PME# supported from D3hot D3cold
[    0.184042] pci 0000:00:16.0: [8086:1e3a] type 00 class 0x078000
[    0.184063] pci 0000:00:16.0: reg 10: [mem 0xf7c1a000-0xf7c1a00f 64bit]
[    0.184131] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    0.184161] pci 0000:00:1a.0: [8086:1e2d] type 00 class 0x0c0320
[    0.184179] pci 0000:00:1a.0: reg 10: [mem 0xf7c18000-0xf7c183ff]
[    0.184263] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    0.184286] pci 0000:00:1b.0: [8086:1e20] type 00 class 0x040300
[    0.184299] pci 0000:00:1b.0: reg 10: [mem 0xf7c10000-0xf7c13fff 64bit]
[    0.184361] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.184380] pci 0000:00:1c.0: [8086:1e10] type 01 class 0x060400
[    0.184452] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.184476] pci 0000:00:1c.3: [8086:1e16] type 01 class 0x060400
[    0.184547] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.184569] pci 0000:00:1c.4: [8086:1e18] type 01 class 0x060400
[    0.184640] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.184661] pci 0000:00:1c.5: [8086:1e1a] type 01 class 0x060400
[    0.184735] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    0.184758] pci 0000:00:1c.7: [8086:1e1e] type 01 class 0x060400
[    0.184829] pci 0000:00:1c.7: PME# supported from D0 D3hot D3cold
[    0.184855] pci 0000:00:1d.0: [8086:1e26] type 00 class 0x0c0320
[    0.184873] pci 0000:00:1d.0: reg 10: [mem 0xf7c17000-0xf7c173ff]
[    0.184957] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    0.184979] pci 0000:00:1f.0: [8086:1e44] type 00 class 0x060100
[    0.185094] pci 0000:00:1f.2: [8086:1e02] type 00 class 0x010601
[    0.185110] pci 0000:00:1f.2: reg 10: [io  0xf0b0-0xf0b7]
[    0.185117] pci 0000:00:1f.2: reg 14: [io  0xf0a0-0xf0a3]
[    0.185123] pci 0000:00:1f.2: reg 18: [io  0xf090-0xf097]
[    0.185129] pci 0000:00:1f.2: reg 1c: [io  0xf080-0xf083]
[    0.185136] pci 0000:00:1f.2: reg 20: [io  0xf060-0xf07f]
[    0.185142] pci 0000:00:1f.2: reg 24: [mem 0xf7c16000-0xf7c167ff]
[    0.185182] pci 0000:00:1f.2: PME# supported from D3hot
[    0.185197] pci 0000:00:1f.3: [8086:1e22] type 00 class 0x0c0500
[    0.185210] pci 0000:00:1f.3: reg 10: [mem 0xf7c15000-0xf7c150ff 64bit]
[    0.185229] pci 0000:00:1f.3: reg 20: [io  0xf040-0xf05f]
[    0.185313] pci 0000:01:00.0: [10ec:8178] type 00 class 0x028000
[    0.185334] pci 0000:01:00.0: reg 10: [io  0xe000-0xe0ff]
[    0.185370] pci 0000:01:00.0: reg 18: [mem 0xf7b00000-0xf7b03fff 64bit]
[    0.185482] pci 0000:01:00.0: supports D1 D2
[    0.185483] pci 0000:01:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.192723] pci 0000:00:1c.0: PCI bridge to [bus 01]
[    0.192728] pci 0000:00:1c.0:   bridge window [io  0xe000-0xefff]
[    0.192733] pci 0000:00:1c.0:   bridge window [mem 0xf7b00000-0xf7bfffff]
[    0.192818] pci 0000:02:00.0: [1b21:0612] type 00 class 0x010601
[    0.192836] pci 0000:02:00.0: reg 10: [io  0xd050-0xd057]
[    0.192848] pci 0000:02:00.0: reg 14: [io  0xd040-0xd043]
[    0.192860] pci 0000:02:00.0: reg 18: [io  0xd030-0xd037]
[    0.192873] pci 0000:02:00.0: reg 1c: [io  0xd020-0xd023]
[    0.192885] pci 0000:02:00.0: reg 20: [io  0xd000-0xd01f]
[    0.192897] pci 0000:02:00.0: reg 24: [mem 0xf7a00000-0xf7a001ff]
[    0.200718] pci 0000:00:1c.3: PCI bridge to [bus 02]
[    0.200723] pci 0000:00:1c.3:   bridge window [io  0xd000-0xdfff]
[    0.200727] pci 0000:00:1c.3:   bridge window [mem 0xf7a00000-0xf7afffff]
[    0.200819] pci 0000:03:00.0: [14e4:16b1] type 00 class 0x020000
[    0.200845] pci 0000:03:00.0: reg 10: [mem 0xf0010000-0xf001ffff 64bit pref]
[    0.200867] pci 0000:03:00.0: reg 18: [mem 0xf0000000-0xf000ffff 64bit pref]
[    0.200906] pci 0000:03:00.0: reg 30: [mem 0xf7900000-0xf79007ff pref]
[    0.200982] pci 0000:03:00.0: PME# supported from D0 D3hot D3cold
[    0.208718] pci 0000:00:1c.4: PCI bridge to [bus 03]
[    0.208726] pci 0000:00:1c.4:   bridge window [mem 0xf7900000-0xf79fffff]
[    0.208733] pci 0000:00:1c.4:   bridge window [mem 0xf0000000-0xf00fffff 64bit pref]
[    0.208808] pci 0000:04:00.0: [1b21:1080] type 01 class 0x060401
[    0.208921] pci 0000:00:1c.5: PCI bridge to [bus 04-05]
[    0.209039] pci 0000:04:00.0: PCI bridge to [bus 05] (subtractive decode)
[    0.209060] pci 0000:04:00.0:   bridge window [??? 0x00000000 flags 0x0] (subtractive decode)
[    0.209061] pci 0000:04:00.0:   bridge window [??? 0x00000000 flags 0x0] (subtractive decode)
[    0.209062] pci 0000:04:00.0:   bridge window [??? 0x00000000 flags 0x0] (subtractive decode)
[    0.209063] pci 0000:04:00.0:   bridge window [??? 0x00000000 flags 0x0] (subtractive decode)
[    0.209138] pci 0000:06:00.0: [1b21:1042] type 00 class 0x0c0330
[    0.209165] pci 0000:06:00.0: reg 10: [mem 0xf7800000-0xf7807fff 64bit]
[    0.209306] pci 0000:06:00.0: PME# supported from D3hot D3cold
[    0.216715] pci 0000:00:1c.7: PCI bridge to [bus 06]
[    0.216723] pci 0000:00:1c.7:   bridge window [mem 0xf7800000-0xf78fffff]
[    0.216785] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.216821] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[    0.216837] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP05._PRT]
[    0.216853] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP06._PRT]
[    0.216870] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP06.BR40._PRT]
[    0.216893] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP08._PRT]
[    0.216974]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.217104]  pci0000:00: ACPI _OSC control (0x18) granted
[    0.217609] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 10 *11 12 14 15)
[    0.217636] ACPI: PCI Interrupt Link [LNKB] (IRQs *3 4 5 6 10 11 12 14 15)
[    0.217661] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 *10 11 12 14 15)
[    0.217686] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 *10 11 12 14 15)
[    0.217711] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.217737] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.217762] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 *5 6 10 11 12 14 15)
[    0.217787] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 10 *11 12 14 15)
[    0.217841] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.217843] vgaarb: loaded
[    0.217844] vgaarb: bridge control possible 0000:00:02.0
[    0.217935] SCSI subsystem initialized
[    0.217938] ACPI: bus type scsi registered
[    0.217955] libata version 3.00 loaded.
[    0.217965] ACPI: bus type usb registered
[    0.217973] usbcore: registered new interface driver usbfs
[    0.217979] usbcore: registered new interface driver hub
[    0.217989] usbcore: registered new device driver usb
[    0.218033] PCI: Using ACPI for IRQ routing
[    0.219389] PCI: pci_cache_line_size set to 64 bytes
[    0.219445] e820: reserve RAM buffer [mem 0x0009d800-0x0009ffff]
[    0.219446] e820: reserve RAM buffer [mem 0x40004000-0x43ffffff]
[    0.219447] e820: reserve RAM buffer [mem 0xccf6f000-0xcfffffff]
[    0.219449] e820: reserve RAM buffer [mem 0xcd8d6000-0xcfffffff]
[    0.219450] e820: reserve RAM buffer [mem 0xce14b000-0xcfffffff]
[    0.219451] e820: reserve RAM buffer [mem 0xcebf2000-0xcfffffff]
[    0.219452] e820: reserve RAM buffer [mem 0xcf000000-0xcfffffff]
[    0.219453] e820: reserve RAM buffer [mem 0x21f600000-0x21fffffff]
[    0.219499] NetLabel: Initializing
[    0.219500] NetLabel:  domain hash size = 128
[    0.219500] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.219506] NetLabel:  unlabeled traffic allowed by default
[    0.219536] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    0.219540] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    0.221549] Switching to clocksource hpet
[    0.224437] AppArmor: AppArmor Filesystem Enabled
[    0.224450] pnp: PnP ACPI init
[    0.224458] ACPI: bus type pnp registered
[    0.224505] system 00:00: [mem 0xfed40000-0xfed44fff] has been reserved
[    0.224508] system 00:00: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.224515] pnp 00:01: [dma 4]
[    0.224522] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.224531] pnp 00:02: Plug and Play ACPI device, IDs INT0800 (active)
[    0.224588] pnp 00:03: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.224612] system 00:04: [io  0x0680-0x069f] has been reserved
[    0.224614] system 00:04: [io  0x1000-0x100f] has been reserved
[    0.224615] system 00:04: [io  0xffff] has been reserved
[    0.224616] system 00:04: [io  0xffff] has been reserved
[    0.224617] system 00:04: [io  0x0400-0x0453] has been reserved
[    0.224618] system 00:04: [io  0x0458-0x047f] has been reserved
[    0.224619] system 00:04: [io  0x0500-0x057f] has been reserved
[    0.224621] system 00:04: [io  0x164e-0x164f] has been reserved
[    0.224622] system 00:04: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.224639] pnp 00:05: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.224665] system 00:06: [io  0x0454-0x0457] has been reserved
[    0.224667] system 00:06: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
[    0.224710] system 00:07: [io  0x0290-0x029f] has been reserved
[    0.224712] system 00:07: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.224845] system 00:08: [io  0x04d0-0x04d1] has been reserved
[    0.224846] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.224861] pnp 00:09: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.224958] pnp 00:0a: [dma 0 disabled]
[    0.224984] pnp 00:0a: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.225126] system 00:0b: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.225127] system 00:0b: [mem 0xfed10000-0xfed17fff] has been reserved
[    0.225128] system 00:0b: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.225129] system 00:0b: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.225131] system 00:0b: [mem 0xf8000000-0xfbffffff] has been reserved
[    0.225132] system 00:0b: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.225133] system 00:0b: [mem 0xfed90000-0xfed93fff] has been reserved
[    0.225134] system 00:0b: [mem 0xfed45000-0xfed8ffff] has been reserved
[    0.225136] system 00:0b: [mem 0xff000000-0xffffffff] has been reserved
[    0.225137] system 00:0b: [mem 0xfee00000-0xfeefffff] could not be reserved
[    0.225138] system 00:0b: [mem 0xdfa00000-0xdfa00fff] has been reserved
[    0.225140] system 00:0b: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.225237] system 00:0c: [mem 0x20000000-0x201fffff] has been reserved
[    0.225239] system 00:0c: [mem 0x40004000-0x40004fff] has been reserved
[    0.225240] system 00:0c: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.225256] pnp: PnP ACPI: found 13 devices
[    0.225257] ACPI: ACPI bus type pnp unregistered
[    0.230746] pci 0000:00:1c.0: PCI bridge to [bus 01]
[    0.230749] pci 0000:00:1c.0:   bridge window [io  0xe000-0xefff]
[    0.230753] pci 0000:00:1c.0:   bridge window [mem 0xf7b00000-0xf7bfffff]
[    0.230760] pci 0000:00:1c.3: PCI bridge to [bus 02]
[    0.230762] pci 0000:00:1c.3:   bridge window [io  0xd000-0xdfff]
[    0.230766] pci 0000:00:1c.3:   bridge window [mem 0xf7a00000-0xf7afffff]
[    0.230773] pci 0000:00:1c.4: PCI bridge to [bus 03]
[    0.230777] pci 0000:00:1c.4:   bridge window [mem 0xf7900000-0xf79fffff]
[    0.230780] pci 0000:00:1c.4:   bridge window [mem 0xf0000000-0xf00fffff 64bit pref]
[    0.230785] pci 0000:04:00.0: PCI bridge to [bus 05]
[    0.230803] pci 0000:00:1c.5: PCI bridge to [bus 04-05]
[    0.230813] pci 0000:00:1c.7: PCI bridge to [bus 06]
[    0.230817] pci 0000:00:1c.7:   bridge window [mem 0xf7800000-0xf78fffff]
[    0.230851] pci 0000:04:00.0: setting latency timer to 64
[    0.230858] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.230859] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.230860] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.230862] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000d3fff]
[    0.230863] pci_bus 0000:00: resource 8 [mem 0x000d4000-0x000d7fff]
[    0.230864] pci_bus 0000:00: resource 9 [mem 0x000d8000-0x000dbfff]
[    0.230865] pci_bus 0000:00: resource 10 [mem 0x000dc000-0x000dffff]
[    0.230866] pci_bus 0000:00: resource 11 [mem 0x000e0000-0x000e3fff]
[    0.230867] pci_bus 0000:00: resource 12 [mem 0x000e4000-0x000e7fff]
[    0.230868] pci_bus 0000:00: resource 13 [mem 0xdfa00000-0xfeafffff]
[    0.230870] pci_bus 0000:01: resource 0 [io  0xe000-0xefff]
[    0.230871] pci_bus 0000:01: resource 1 [mem 0xf7b00000-0xf7bfffff]
[    0.230872] pci_bus 0000:02: resource 0 [io  0xd000-0xdfff]
[    0.230873] pci_bus 0000:02: resource 1 [mem 0xf7a00000-0xf7afffff]
[    0.230874] pci_bus 0000:03: resource 1 [mem 0xf7900000-0xf79fffff]
[    0.230875] pci_bus 0000:03: resource 2 [mem 0xf0000000-0xf00fffff 64bit pref]
[    0.230877] pci_bus 0000:06: resource 1 [mem 0xf7800000-0xf78fffff]
[    0.230895] NET: Registered protocol family 2
[    0.230995] TCP established hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.231131] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.231236] TCP: Hash tables configured (established 65536 bind 65536)
[    0.231247] TCP: reno registered
[    0.231253] UDP hash table entries: 4096 (order: 5, 131072 bytes)
[    0.231273] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
[    0.231312] NET: Registered protocol family 1
[    0.231319] pci 0000:00:02.0: Boot video device
[    0.269612] PCI: CLS 64 bytes, default 64
[    0.269648] Trying to unpack rootfs image as initramfs...
[    0.433569] Freeing initrd memory: 15848k freed
[    0.434930] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.434934] software IO TLB [mem 0xc8f6f000-0xccf6f000] (64MB) mapped at [ffff8800c8f6f000-ffff8800ccf6efff]
[    0.435207] Initialise module verification
[    0.435231] audit: initializing netlink socket (disabled)
[    0.435241] type=2000 audit(1381085144.372:1): initialized
[    0.453761] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.454614] VFS: Disk quotas dquot_6.5.2
[    0.454635] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.454883] fuse init (API version 7.20)
[    0.454923] msgmni has been set to 15363
[    0.455158] Key type asymmetric registered
[    0.455159] Asymmetric key parser 'x509' registered
[    0.455176] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    0.455190] io scheduler noop registered
[    0.455191] io scheduler deadline registered (default)
[    0.455194] io scheduler cfq registered
[    0.455422] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.455429] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.455452] intel_idle: MWAIT substates: 0x1120
[    0.455453] intel_idle: v0.4 model 0x3A
[    0.455454] intel_idle: lapic_timer_reliable_states 0xffffffff
[    0.455503] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.455505] ACPI: Power Button [PWRB]
[    0.455523] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.455525] ACPI: Power Button [PWRF]
[    0.455585] ACPI: Requesting acpi_cpufreq
[    0.457769] GHES: HEST is not enabled!
[    0.457812] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.478209] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.478879] Linux agpgart interface v0.103
[    0.479461] brd: module loaded
[    0.479791] loop: module loaded
[    0.479959] libphy: Fixed MDIO Bus: probed
[    0.479989] tun: Universal TUN/TAP device driver, 1.6
[    0.479990] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.480007] PPP generic driver version 2.4.2
[    0.480025] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.480026] ehci-pci: EHCI PCI platform driver
[    0.480050] ehci-pci 0000:00:1a.0: setting latency timer to 64
[    0.480052] ehci-pci 0000:00:1a.0: EHCI Host Controller
[    0.480056] ehci-pci 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    0.480066] ehci-pci 0000:00:1a.0: debug port 2
[    0.483964] ehci-pci 0000:00:1a.0: cache line size of 64 is not supported
[    0.483976] ehci-pci 0000:00:1a.0: irq 16, io mem 0xf7c18000
[    0.493414] ehci-pci 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    0.493435] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    0.493438] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.493440] usb usb1: Product: EHCI Host Controller
[    0.493442] usb usb1: Manufacturer: Linux 3.8.0-31-generic ehci_hcd
[    0.493445] usb usb1: SerialNumber: 0000:00:1a.0
[    0.493531] hub 1-0:1.0: USB hub found
[    0.493534] hub 1-0:1.0: 2 ports detected
[    0.493602] ehci-pci 0000:00:1d.0: setting latency timer to 64
[    0.493604] ehci-pci 0000:00:1d.0: EHCI Host Controller
[    0.493606] ehci-pci 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.493617] ehci-pci 0000:00:1d.0: debug port 2
[    0.497505] ehci-pci 0000:00:1d.0: cache line size of 64 is not supported
[    0.497515] ehci-pci 0000:00:1d.0: irq 23, io mem 0xf7c17000
[    0.509402] ehci-pci 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    0.509416] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    0.509419] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.509421] usb usb2: Product: EHCI Host Controller
[    0.509423] usb usb2: Manufacturer: Linux 3.8.0-31-generic ehci_hcd
[    0.509426] usb usb2: SerialNumber: 0000:00:1d.0
[    0.509507] hub 2-0:1.0: USB hub found
[    0.509509] hub 2-0:1.0: 2 ports detected
[    0.509560] ehci-platform: EHCI generic platform driver
[    0.509563] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.509571] uhci_hcd: USB Universal Host Controller Interface driver
[    0.509597] xhci_hcd 0000:00:14.0: setting latency timer to 64
[    0.509599] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    0.509601] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 3
[    0.509671] xhci_hcd 0000:00:14.0: cache line size of 64 is not supported
[    0.509707] xhci_hcd 0000:00:14.0: irq 40 for MSI/MSI-X
[    0.509741] usb usb3: New USB device found, idVendor=1d6b, idProduct=0002
[    0.509742] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.509744] usb usb3: Product: xHCI Host Controller
[    0.509745] usb usb3: Manufacturer: Linux 3.8.0-31-generic xhci_hcd
[    0.509746] usb usb3: SerialNumber: 0000:00:14.0
[    0.509780] xHCI xhci_add_endpoint called for root hub
[    0.509781] xHCI xhci_check_bandwidth called for root hub
[    0.509791] hub 3-0:1.0: USB hub found
[    0.509796] hub 3-0:1.0: 4 ports detected
[    0.509956] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    0.509958] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 4
[    0.509971] usb usb4: New USB device found, idVendor=1d6b, idProduct=0003
[    0.509972] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.509973] usb usb4: Product: xHCI Host Controller
[    0.509974] usb usb4: Manufacturer: Linux 3.8.0-31-generic xhci_hcd
[    0.509975] usb usb4: SerialNumber: 0000:00:14.0
[    0.510010] xHCI xhci_add_endpoint called for root hub
[    0.510011] xHCI xhci_check_bandwidth called for root hub
[    0.510020] hub 4-0:1.0: USB hub found
[    0.510025] hub 4-0:1.0: 4 ports detected
[    0.510229] xhci_hcd 0000:06:00.0: xHCI Host Controller
[    0.510232] xhci_hcd 0000:06:00.0: new USB bus registered, assigned bus number 5
[    0.572964] xhci_hcd 0000:06:00.0: irq 41 for MSI/MSI-X
[    0.572967] xhci_hcd 0000:06:00.0: irq 42 for MSI/MSI-X
[    0.572970] xhci_hcd 0000:06:00.0: irq 43 for MSI/MSI-X
[    0.572973] xhci_hcd 0000:06:00.0: irq 44 for MSI/MSI-X
[    0.572976] xhci_hcd 0000:06:00.0: irq 45 for MSI/MSI-X
[    0.573054] usb usb5: New USB device found, idVendor=1d6b, idProduct=0002
[    0.573056] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.573057] usb usb5: Product: xHCI Host Controller
[    0.573058] usb usb5: Manufacturer: Linux 3.8.0-31-generic xhci_hcd
[    0.573059] usb usb5: SerialNumber: 0000:06:00.0
[    0.573094] xHCI xhci_add_endpoint called for root hub
[    0.573095] xHCI xhci_check_bandwidth called for root hub
[    0.573105] hub 5-0:1.0: USB hub found
[    0.573110] hub 5-0:1.0: 2 ports detected
[    0.573146] xhci_hcd 0000:06:00.0: xHCI Host Controller
[    0.573148] xhci_hcd 0000:06:00.0: new USB bus registered, assigned bus number 6
[    0.573177] usb usb6: New USB device found, idVendor=1d6b, idProduct=0003
[    0.573178] usb usb6: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.573179] usb usb6: Product: xHCI Host Controller
[    0.573180] usb usb6: Manufacturer: Linux 3.8.0-31-generic xhci_hcd
[    0.573181] usb usb6: SerialNumber: 0000:06:00.0
[    0.573212] xHCI xhci_add_endpoint called for root hub
[    0.573213] xHCI xhci_check_bandwidth called for root hub
[    0.573223] hub 6-0:1.0: USB hub found
[    0.573228] hub 6-0:1.0: 2 ports detected
[    0.573310] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    0.575847] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.575850] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.575907] mousedev: PS/2 mouse device common for all mice
[    0.575970] rtc_cmos 00:05: RTC can wake from S4
[    0.576067] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    0.576090] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    0.576133] device-mapper: uevent: version 1.0.3
[    0.576162] device-mapper: ioctl: 4.23.1-ioctl (2012-12-18) initialised: dm-devel@redhat.com
[    0.576196] cpuidle: using governor ladder
[    0.576239] cpuidle: using governor menu
[    0.576240] ledtrig-cpu: registered to indicate activity on CPUs
[    0.576241] EFI Variables Facility v0.08 2004-May-17
[    0.576330] ashmem: initialized
[    0.576391] TCP: cubic registered
[    0.576441] NET: Registered protocol family 10
[    0.576532] NET: Registered protocol family 17
[    0.576540] Key type dns_resolver registered
[    0.576668] Loading module verification certificates
[    0.577218] MODSIGN: Loaded cert 'Magrathea: Glacier signing key: beedac769733b6dde22c1ae0d3a2045ac52087e1'
[    0.577225] registered taskstats version 1
[    0.578597] Key type trusted registered
[    0.579855] Key type encrypted registered
[    0.581781] rtc_cmos 00:05: setting system clock to 2013-10-06 18:45:45 UTC (1381085145)
[    0.582428] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.582429] EDD information not available.
[    0.583313] Freeing unused kernel memory: 996k freed
[    0.583385] Write protecting the kernel read-only data: 12288k
[    0.585278] Freeing unused kernel memory: 1168k freed
[    0.586944] Freeing unused kernel memory: 1076k freed
[    0.593897] udevd[108]: starting version 175
[    0.608670] pps_core: LinuxPPS API ver. 1 registered
[    0.608672] pps_core: Software ver. 5.3.6 - Copyright 2005-2007 Rodolfo Giometti <giometti@linux.it>
[    0.609541] PTP clock support registered
[    0.610473] Disabling lock debugging due to kernel taint
[    0.610789] ahci 0000:00:1f.2: version 3.0
[    0.610828] ahci 0000:00:1f.2: irq 46 for MSI/MSI-X
[    0.611232] tg3.c:v3.128 (December 03, 2012)
[    0.625376] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 6 Gbps 0x3f impl SATA mode
[    0.625379] ahci 0000:00:1f.2: flags: 64bit ncq pm led clo pio slum part ems apst 
[    0.625383] ahci 0000:00:1f.2: setting latency timer to 64
[    0.636672] tg3 0000:03:00.0 eth0: Tigon3 [partno(BCM57781) rev 57785100] (PCI Express) MAC address bc:5f:f4:47:f8:79
[    0.636674] tg3 0000:03:00.0 eth0: attached PHY is 57765 (10/100/1000Base-T Ethernet) (WireSpeed[1], EEE[1])
[    0.636675] tg3 0000:03:00.0 eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[    0.636676] tg3 0000:03:00.0 eth0: dma_rwctrl[00000001] dma_mask[64-bit]
[    0.665635] scsi0 : ahci
[    0.665783] scsi1 : ahci
[    0.665921] scsi2 : ahci
[    0.666058] scsi3 : ahci
[    0.666176] scsi4 : ahci
[    0.666287] scsi5 : ahci
[    0.666353] ata1: SATA max UDMA/133 abar m2048@0xf7c16000 port 0xf7c16100 irq 46
[    0.666355] ata2: SATA max UDMA/133 abar m2048@0xf7c16000 port 0xf7c16180 irq 46
[    0.666357] ata3: SATA max UDMA/133 abar m2048@0xf7c16000 port 0xf7c16200 irq 46
[    0.666359] ata4: SATA max UDMA/133 abar m2048@0xf7c16000 port 0xf7c16280 irq 46
[    0.666360] ata5: SATA max UDMA/133 abar m2048@0xf7c16000 port 0xf7c16300 irq 46
[    0.666361] ata6: SATA max UDMA/133 abar m2048@0xf7c16000 port 0xf7c16380 irq 46
[    0.666530] ahci 0000:02:00.0: irq 47 for MSI/MSI-X
[    0.666570] ahci: SSS flag set, parallel bus scan disabled
[    0.666638] ahci 0000:02:00.0: AHCI 0001.0200 32 slots 2 ports 6 Gbps 0x3 impl SATA mode
[    0.666639] ahci 0000:02:00.0: flags: 64bit ncq sntf stag led clo pmp pio slum part ccc sxs 
[    0.666832] scsi6 : ahci
[    0.666908] scsi7 : ahci
[    0.666936] ata7: SATA max UDMA/133 abar m512@0xf7a00000 port 0xf7a00100 irq 47
[    0.666939] ata8: SATA max UDMA/133 abar m512@0xf7a00000 port 0xf7a00180 irq 47
[    0.805250] usb 1-1: new high-speed USB device number 2 using ehci-pci
[    0.937537] usb 1-1: New USB device found, idVendor=8087, idProduct=0024
[    0.937542] usb 1-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    0.937816] hub 1-1:1.0: USB hub found
[    0.937893] hub 1-1:1.0: 6 ports detected
[    0.985160] ata4: SATA link down (SStatus 0 SControl 300)
[    0.985184] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    0.985223] ata1: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    0.985233] ata7: SATA link down (SStatus 0 SControl 300)
[    0.985251] ata3: SATA link down (SStatus 0 SControl 300)
[    0.985268] ata6: SATA link down (SStatus 0 SControl 300)
[    0.985298] ata5: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    0.985924] ata1.00: ACPI cmd ef/10:06:00:00:00:00 (SET FEATURES) succeeded
[    0.985934] ata1.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
[    0.985936] ata1.00: ACPI cmd b1/c1:00:00:00:00:00 (DEVICE CONFIGURATION OVERLAY) filtered out
[    0.985944] ata5.00: ACPI cmd ef/10:06:00:00:00:00 (SET FEATURES) succeeded
[    0.985947] ata5.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
[    0.985948] ata5.00: ACPI cmd b1/c1:00:00:00:00:00 (DEVICE CONFIGURATION OVERLAY) filtered out
[    0.986358] ata1.00: ATA-9: M4-CT128M4SSD2, 000F, max UDMA/100
[    0.986360] ata1.00: 250069680 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    0.986493] ata5.00: ATA-8: ST3000DM001-9YN166, CC4B, max UDMA/133
[    0.986498] ata5.00: 5860533168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    0.986521] ata2.00: ACPI cmd ef/10:06:00:00:00:00 (SET FEATURES) succeeded
[    0.986525] ata2.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
[    0.986528] ata2.00: ACPI cmd b1/c1:00:00:00:00:00 (DEVICE CONFIGURATION OVERLAY) filtered out
[    0.986822] ata1.00: ACPI cmd ef/10:06:00:00:00:00 (SET FEATURES) succeeded
[    0.986828] ata1.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
[    0.986831] ata1.00: ACPI cmd b1/c1:00:00:00:00:00 (DEVICE CONFIGURATION OVERLAY) filtered out
[    0.986981] ata2.00: ATAPI: OPTIARC DVD-ROM DDU1681S, 1.06, max UDMA/100
[    0.987193] ata5.00: ACPI cmd ef/10:06:00:00:00:00 (SET FEATURES) succeeded
[    0.987195] ata5.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
[    0.987197] ata5.00: ACPI cmd b1/c1:00:00:00:00:00 (DEVICE CONFIGURATION OVERLAY) filtered out
[    0.987249] ata1.00: configured for UDMA/100
[    0.987432] scsi 0:0:0:0: Direct-Access     ATA      M4-CT128M4SSD2   000F PQ: 0 ANSI: 5
[    0.987534] sd 0:0:0:0: [sda] 250069680 512-byte logical blocks: (128 GB/119 GiB)
[    0.987538] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    0.987597] sd 0:0:0:0: [sda] Write Protect is off
[    0.987599] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    0.987607] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.987679] ata5.00: configured for UDMA/133
[    0.988081]  sda: sda1 sda2 < sda5 >
[    0.988282] sd 0:0:0:0: [sda] Attached SCSI disk
[    0.988893] ata2.00: ACPI cmd ef/10:06:00:00:00:00 (SET FEATURES) succeeded
[    0.988897] ata2.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
[    0.988900] ata2.00: ACPI cmd b1/c1:00:00:00:00:00 (DEVICE CONFIGURATION OVERLAY) filtered out
[    0.989253] ata2.00: configured for UDMA/100
[    0.991571] scsi 1:0:0:0: CD-ROM            OPTIARC  DVD-ROM DDU1681S 1.06 PQ: 0 ANSI: 5
[    0.994046] sr0: scsi3-mmc drive: 48x/48x cd/rw xa/form2 cdda tray
[    0.994050] cdrom: Uniform CD-ROM driver Revision: 3.20
[    0.994199] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    0.994342] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    0.994644] scsi 4:0:0:0: Direct-Access     ATA      ST3000DM001-9YN1 CC4B PQ: 0 ANSI: 5
[    0.994775] sd 4:0:0:0: [sdb] 5860533168 512-byte logical blocks: (3.00 TB/2.72 TiB)
[    0.994777] sd 4:0:0:0: [sdb] 4096-byte physical blocks
[    0.994807] sd 4:0:0:0: Attached scsi generic sg2 type 0
[    0.994901] sd 4:0:0:0: [sdb] Write Protect is off
[    0.994903] sd 4:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    0.994959] sd 4:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.015934]  sdb: sdb1
[    1.016535] sd 4:0:0:0: [sdb] Attached SCSI disk
[    1.049095] usb 2-1: new high-speed USB device number 2 using ehci-pci
[    1.181394] usb 2-1: New USB device found, idVendor=8087, idProduct=0024
[    1.181399] usb 2-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.181674] hub 2-1:1.0: USB hub found
[    1.181747] hub 2-1:1.0: 8 ports detected
[    1.312970] ata8: SATA link down (SStatus 0 SControl 300)
[    1.342711] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    1.348939] usb 3-2: new full-speed USB device number 2 using xhci_hcd
[    1.367221] usb 3-2: New USB device found, idVendor=046d, idProduct=c52e
[    1.367225] usb 3-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.367228] usb 3-2: Product: USB Receiver
[    1.367231] usb 3-2: Manufacturer: Logitech
[    1.432883] tsc: Refined TSC clocksource calibration: 3400.024 MHz
[    1.432888] Switching to clocksource tsc
[    1.518932] Adding 8074236k swap on /dev/sda5.  Priority:-1 extents:1 across:8074236k SS
[    1.547357] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    1.556002] udevd[380]: starting version 175
[    1.603331] mei 0000:00:16.0: setting latency timer to 64
[    1.603377] mei 0000:00:16.0: irq 48 for MSI/MSI-X
[    1.604022] type=1400 audit(1381085146.516:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=469 comm="apparmor_parser"
[    1.604254] type=1400 audit(1381085146.516:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=469 comm="apparmor_parser"
[    1.604381] type=1400 audit(1381085146.516:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=469 comm="apparmor_parser"
[    1.609116] lp: driver loaded but no devices found
[    1.612699] ACPI Warning: 0x0000000000000428-0x000000000000042f SystemIO conflicts with Region \PMIO 1 (20121018/utaddress-251)
[    1.612703] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    1.612706] ACPI Warning: 0x0000000000000530-0x000000000000053f SystemIO conflicts with Region \GPR2 1 (20121018/utaddress-251)
[    1.612708] ACPI Warning: 0x0000000000000530-0x000000000000053f SystemIO conflicts with Region \GPIO 2 (20121018/utaddress-251)
[    1.612710] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    1.612710] ACPI Warning: 0x0000000000000500-0x000000000000052f SystemIO conflicts with Region \GPR2 1 (20121018/utaddress-251)
[    1.612712] ACPI Warning: 0x0000000000000500-0x000000000000052f SystemIO conflicts with Region \GPIO 2 (20121018/utaddress-251)
[    1.612714] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    1.612714] lpc_ich: Resource conflict(s) found affecting gpio_ich
[    1.623953] microcode: CPU0 sig=0x306a9, pf=0x2, revision=0x12
[    1.627108] w83627ehf: Found NCT6776F chip at 0x290
[    1.639771] usbcore: registered new interface driver usbhid
[    1.639777] usbhid: USB HID core driver
[    1.643187] [drm] Initialized drm 1.1.0 20060810
[    1.649927] cfg80211: Calling CRDA to update world regulatory domain
[    1.679346] [drm] Memory usable by graphics device = 2048M
[    1.679350] i915 0000:00:02.0: setting latency timer to 64
[    1.679610] microcode: CPU1 sig=0x306a9, pf=0x2, revision=0x12
[    1.681564] microcode: CPU2 sig=0x306a9, pf=0x2, revision=0x12
[    1.682989] microcode: CPU3 sig=0x306a9, pf=0x2, revision=0x12
[    1.683626] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:14.0/usb3/3-2/3-2:1.0/input/input2
[    1.683677] hid-generic 0003:046D:C52E.0001: input,hidraw0: USB HID v1.11 Keyboard [Logitech USB Receiver] on usb-0000:00:14.0-2/input0
[    1.683806] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:14.0/usb3/3-2/3-2:1.1/input/input3
[    1.684032] hid-generic 0003:046D:C52E.0002: input,hiddev0,hidraw1: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:14.0-2/input1
[    1.686781] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    1.706391] i915 0000:00:02.0: irq 49 for MSI/MSI-X
[    1.706397] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    1.706398] [drm] Driver supports precise vblank timestamp query.
[    1.706453] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[    1.848301] rtl8192ce: Using firmware rtlwifi/rtl8192cfw.bin
[    1.919764] wmi: Mapper loaded
[    1.987487] cfg80211: World regulatory domain updated:
[    1.987489] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[    1.987490] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    1.987491] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    1.987492] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    1.987493] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    1.987494] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    1.987499] cfg80211: Calling CRDA for country: EC
[    1.987932] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[    1.988048] rtlwifi: wireless switch is on
[    1.989461] cfg80211: Regulatory domain changed to country: EC
[    1.989463] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[    1.989464] cfg80211:   (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[    1.989465] cfg80211:   (5170000 KHz - 5250000 KHz @ 20000 KHz), (300 mBi, 1700 mBm)
[    1.989466] cfg80211:   (5250000 KHz - 5330000 KHz @ 20000 KHz), (300 mBi, 2300 mBm)
[    1.989467] cfg80211:   (5735000 KHz - 5835000 KHz @ 20000 KHz), (300 mBi, 3000 mBm)
[    2.043720] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[    2.088448] init: failsafe main process (881) killed by TERM signal
[    2.121014] type=1400 audit(1381085147.036:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=958 comm="apparmor_parser"
[    2.121223] type=1400 audit(1381085147.036:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/x86_64-linux-gnu/lightdm-remote-session-freerdp/freerdp-session-wrapper" pid=956 comm="apparmor_parser"
[    2.121228] type=1400 audit(1381085147.036:7): apparmor="STATUS" operation="profile_load" name="/usr/lib/x86_64-linux-gnu/lightdm-remote-session-uccsconfigure/uccsconfigure-session-wrapper" pid=957 comm="apparmor_parser"
[    2.121239] type=1400 audit(1381085147.036:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=955 comm="apparmor_parser"
[    2.121254] type=1400 audit(1381085147.036:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=958 comm="apparmor_parser"
[    2.121382] type=1400 audit(1381085147.036:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=958 comm="apparmor_parser"
[    2.132465] [drm] GMBUS [i915 gmbus dpc] timed out, falling back to bit banging on pin 4
[    2.139721] Bluetooth: Core ver 2.16
[    2.139733] NET: Registered protocol family 31
[    2.139734] Bluetooth: HCI device and connection manager initialized
[    2.139738] Bluetooth: HCI socket layer initialized
[    2.139740] Bluetooth: L2CAP socket layer initialized
[    2.139742] Bluetooth: SCO socket layer initialized
[    2.150172] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    2.150174] Bluetooth: BNEP filters: protocol multicast
[    2.150180] Bluetooth: BNEP socket layer initialized
[    2.150420] Bluetooth: RFCOMM TTY layer initialized
[    2.150425] Bluetooth: RFCOMM socket layer initialized
[    2.150426] Bluetooth: RFCOMM ver 1.11
[    2.152533] init: avahi-cups-reload main process (992) terminated with status 1
[    2.159984] ppdev: user-space parallel port driver
[    2.198406] init: alsa-restore main process (1053) terminated with status 19
[    2.212954] fbcon: inteldrmfb (fb0) is primary device
[    2.452336] Console: switching to colour frame buffer device 240x67
[    2.455907] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[    2.455909] i915 0000:00:02.0: registered panic notifier
[    2.583429] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    2.583595] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    2.584819] tg3 0000:03:00.0: irq 50 for MSI/MSI-X
[    2.584823] tg3 0000:03:00.0: irq 51 for MSI/MSI-X
[    2.584825] tg3 0000:03:00.0: irq 52 for MSI/MSI-X
[    2.584828] tg3 0000:03:00.0: irq 53 for MSI/MSI-X
[    2.584830] tg3 0000:03:00.0: irq 54 for MSI/MSI-X
[    2.739380] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    2.739576] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    2.740536] acpi device:42: registered as cooling_device4
[    2.740635] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[    2.740752] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input4
[    2.740807] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    2.740900] snd_hda_intel 0000:00:1b.0: irq 55 for MSI/MSI-X
[    2.762654] init: plymouth-splash main process (1317) terminated with status 1
[    3.085813] [drm] Enabling RC6 states: RC6 on, RC6p on, RC6pp off
[    3.097507] input: HDA Intel PCH HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input5
[    3.097570] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input6
[    3.097621] input: HDA Intel PCH Line as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[    3.097651] input: HDA Intel PCH Rear Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[    3.097679] input: HDA Intel PCH Front Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[    3.097707] input: HDA Intel PCH Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[    3.097735] input: HDA Intel PCH Line Out CLFE as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[    3.097763] input: HDA Intel PCH Line Out Surround as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[    3.097791] input: HDA Intel PCH Line Out Front as /devices/pci0000:00/0000:00:1b.0/sound/card0/input13
[    4.759360] wlan0: authenticate with c0:3f:0e:65:fd:56
[    4.779192] wlan0: send auth to c0:3f:0e:65:fd:56 (try 1/3)
[    4.780648] wlan0: authenticated
[    4.782938] wlan0: associate with c0:3f:0e:65:fd:56 (try 1/3)
[    4.785187] wlan0: RX AssocResp from c0:3f:0e:65:fd:56 (capab=0x411 status=0 aid=2)
[    4.785295] wlan0: associated
[    4.785300] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[    4.795937] ------------[ cut here ]------------
[    4.795953] WARNING: at /build/buildd/linux-3.8.0/net/mac80211/tx.c:766 invoke_tx_handlers+0x881/0x1560 [mac80211]()
[    4.795954] Hardware name: To Be Filled By O.E.M.
[    4.795954] Modules linked in: snd_hda_codec_hdmi snd_hda_codec_realtek parport_pc(F) ppdev(F) bnep rfcomm bluetooth binfmt_misc(F) kvm_intel(F) snd_hda_intel kvm(F) snd_hda_codec snd_hwdep(F) ghash_clmulni_intel(F) snd_pcm(F) aesni_intel(F) aes_x86_64(F) xts(F) snd_page_alloc(F) lrw(F) arc4(F) mxm_wmi gf128mul(F) ablk_helper(F) snd_seq_midi(F) wmi snd_seq_midi_event(F) cryptd(F) rtl8192ce snd_rawmidi(F) joydev(F) rtlwifi hid_generic rtl8192c_common i915 mac80211 snd_seq(F) video(F) drm_kms_helper cfg80211 drm usbhid i2c_algo_bit psmouse(F) w83627ehf hid hwmon_vid microcode(F) snd_seq_device(F) coretemp snd_timer(F) mac_hid snd(F) serio_raw(F) lp(F) lpc_ich mei soundcore(F) parport(F) tg3 ahci(F) libahci(F) ptp pps_core
[    4.795975] Pid: 1284, comm: wpa_supplicant Tainted: GF            3.8.0-31-generic #46-Ubuntu
[    4.795977] Call Trace:
[    4.795981]  [<ffffffff810589af>] warn_slowpath_common+0x7f/0xc0
[    4.795982]  [<ffffffff81058a0a>] warn_slowpath_null+0x1a/0x20
[    4.795988]  [<ffffffffa025cd61>] invoke_tx_handlers+0x881/0x1560 [mac80211]
[    4.795991]  [<ffffffff8114d000>] ? zone_statistics+0x40/0xc0
[    4.795997]  [<ffffffffa025dbbe>] ieee80211_tx+0x7e/0x100 [mac80211]
[    4.796002]  [<ffffffffa025dcea>] ieee80211_xmit+0xaa/0x100 [mac80211]
[    4.796007]  [<ffffffffa025e4b5>] ieee80211_subif_start_xmit+0x445/0xe80 [mac80211]
[    4.796011]  [<ffffffff815be81b>] ? __alloc_skb+0x8b/0x2a0
[    4.796013]  [<ffffffff815cbd18>] dev_hard_start_xmit+0x278/0x4f0
[    4.796015]  [<ffffffff815e8d8e>] sch_direct_xmit+0x10e/0x1e0
[    4.796017]  [<ffffffff815cc397>] dev_queue_xmit+0x177/0x440
[    4.796019]  [<ffffffff81699737>] packet_sendmsg+0xc97/0xd50
[    4.796021]  [<ffffffff8134c7ae>] ? radix_tree_lookup_slot+0xe/0x10
[    4.796023]  [<ffffffff8112faae>] ? find_get_page+0x1e/0xa0
[    4.796025]  [<ffffffff815b1a90>] sock_sendmsg+0xb0/0xe0
[    4.796027]  [<ffffffff81158525>] ? handle_pte_fault+0x95/0x450
[    4.796028]  [<ffffffff815b500d>] sys_sendto+0x12d/0x180
[    4.796031]  [<ffffffff816d13be>] ? do_page_fault+0xe/0x10
[    4.796033]  [<ffffffff816d59dd>] system_call_fastpath+0x1a/0x1f
[    4.796034] ---[ end trace eaeaa88497c34cd5 ]---
[    4.796034] ------------[ cut here ]------------
[    4.796039] WARNING: at /build/buildd/linux-3.8.0/net/mac80211/tx.c:55 invoke_tx_handlers+0xe30/0x1560 [mac80211]()
[    4.796040] Hardware name: To Be Filled By O.E.M.
[    4.796040] Modules linked in: snd_hda_codec_hdmi snd_hda_codec_realtek parport_pc(F) ppdev(F) bnep rfcomm bluetooth binfmt_misc(F) kvm_intel(F) snd_hda_intel kvm(F) snd_hda_codec snd_hwdep(F) ghash_clmulni_intel(F) snd_pcm(F) aesni_intel(F) aes_x86_64(F) xts(F) snd_page_alloc(F) lrw(F) arc4(F) mxm_wmi gf128mul(F) ablk_helper(F) snd_seq_midi(F) wmi snd_seq_midi_event(F) cryptd(F) rtl8192ce snd_rawmidi(F) joydev(F) rtlwifi hid_generic rtl8192c_common i915 mac80211 snd_seq(F) video(F) drm_kms_helper cfg80211 drm usbhid i2c_algo_bit psmouse(F) w83627ehf hid hwmon_vid microcode(F) snd_seq_device(F) coretemp snd_timer(F) mac_hid snd(F) serio_raw(F) lp(F) lpc_ich mei soundcore(F) parport(F) tg3 ahci(F) libahci(F) ptp pps_core
[    4.796056] Pid: 1284, comm: wpa_supplicant Tainted: GF       W    3.8.0-31-generic #46-Ubuntu
[    4.796057] Call Trace:
[    4.796058]  [<ffffffff810589af>] warn_slowpath_common+0x7f/0xc0
[    4.796059]  [<ffffffff81058a0a>] warn_slowpath_null+0x1a/0x20
[    4.796064]  [<ffffffffa025d310>] invoke_tx_handlers+0xe30/0x1560 [mac80211]
[    4.796069]  [<ffffffffa025dbbe>] ieee80211_tx+0x7e/0x100 [mac80211]
[    4.796074]  [<ffffffffa025dcea>] ieee80211_xmit+0xaa/0x100 [mac80211]
[    4.796079]  [<ffffffffa025e4b5>] ieee80211_subif_start_xmit+0x445/0xe80 [mac80211]
[    4.796081]  [<ffffffff815be81b>] ? __alloc_skb+0x8b/0x2a0
[    4.796083]  [<ffffffff815cbd18>] dev_hard_start_xmit+0x278/0x4f0
[    4.796085]  [<ffffffff815e8d8e>] sch_direct_xmit+0x10e/0x1e0
[    4.796087]  [<ffffffff815cc397>] dev_queue_xmit+0x177/0x440
[    4.796088]  [<ffffffff81699737>] packet_sendmsg+0xc97/0xd50
[    4.796090]  [<ffffffff8134c7ae>] ? radix_tree_lookup_slot+0xe/0x10
[    4.796091]  [<ffffffff8112faae>] ? find_get_page+0x1e/0xa0
[    4.796092]  [<ffffffff815b1a90>] sock_sendmsg+0xb0/0xe0
[    4.796094]  [<ffffffff81158525>] ? handle_pte_fault+0x95/0x450
[    4.796096]  [<ffffffff815b500d>] sys_sendto+0x12d/0x180
[    4.796097]  [<ffffffff816d13be>] ? do_page_fault+0xe/0x10
[    4.796098]  [<ffffffff816d59dd>] system_call_fastpath+0x1a/0x1f
[    4.796099] ---[ end trace eaeaa88497c34cd6 ]---
[    4.796101] ------------[ cut here ]------------
[    4.796104] WARNING: at /build/buildd/linux-3.8.0/include/net/mac80211.h:1554 rtl_get_tcb_desc+0x40c/0x590 [rtlwifi]()
[    4.796104] Hardware name: To Be Filled By O.E.M.
[    4.796105] Modules linked in: snd_hda_codec_hdmi snd_hda_codec_realtek parport_pc(F) ppdev(F) bnep rfcomm bluetooth binfmt_misc(F) kvm_intel(F) snd_hda_intel kvm(F) snd_hda_codec snd_hwdep(F) ghash_clmulni_intel(F) snd_pcm(F) aesni_intel(F) aes_x86_64(F) xts(F) snd_page_alloc(F) lrw(F) arc4(F) mxm_wmi gf128mul(F) ablk_helper(F) snd_seq_midi(F) wmi snd_seq_midi_event(F) cryptd(F) rtl8192ce snd_rawmidi(F) joydev(F) rtlwifi hid_generic rtl8192c_common i915 mac80211 snd_seq(F) video(F) drm_kms_helper cfg80211 drm usbhid i2c_algo_bit psmouse(F) w83627ehf hid hwmon_vid microcode(F) snd_seq_device(F) coretemp snd_timer(F) mac_hid snd(F) serio_raw(F) lp(F) lpc_ich mei soundcore(F) parport(F) tg3 ahci(F) libahci(F) ptp pps_core
[    4.796120] Pid: 1284, comm: wpa_supplicant Tainted: GF       W    3.8.0-31-generic #46-Ubuntu
[    4.796121] Call Trace:
[    4.796122]  [<ffffffff810589af>] warn_slowpath_common+0x7f/0xc0
[    4.796123]  [<ffffffff81058a0a>] warn_slowpath_null+0x1a/0x20
[    4.796126]  [<ffffffffa02d19ac>] rtl_get_tcb_desc+0x40c/0x590 [rtlwifi]
[    4.796128]  [<ffffffffa00cc6b4>] rtl92ce_tx_fill_desc+0x1c4/0x740 [rtl8192ce]
[    4.796131]  [<ffffffff81364ce0>] ? swiotlb_map_sg+0x10/0x10
[    4.796134]  [<ffffffffa02d8c14>] rtl_pci_tx+0x194/0x410 [rtlwifi]
[    4.796136]  [<ffffffffa02d468e>] rtl_op_tx+0xae/0xb0 [rtlwifi]
[    4.796142]  [<ffffffffa025b905>] __ieee80211_tx+0x125/0x350 [mac80211]
[    4.796147]  [<ffffffffa025dc0f>] ieee80211_tx+0xcf/0x100 [mac80211]
[    4.796152]  [<ffffffffa025dcea>] ieee80211_xmit+0xaa/0x100 [mac80211]
[    4.796157]  [<ffffffffa025e4b5>] ieee80211_subif_start_xmit+0x445/0xe80 [mac80211]
[    4.796159]  [<ffffffff815be81b>] ? __alloc_skb+0x8b/0x2a0
[    4.796160]  [<ffffffff815cbd18>] dev_hard_start_xmit+0x278/0x4f0
[    4.796162]  [<ffffffff815e8d8e>] sch_direct_xmit+0x10e/0x1e0
[    4.796164]  [<ffffffff815cc397>] dev_queue_xmit+0x177/0x440
[    4.796165]  [<ffffffff81699737>] packet_sendmsg+0xc97/0xd50
[    4.796167]  [<ffffffff8134c7ae>] ? radix_tree_lookup_slot+0xe/0x10
[    4.796168]  [<ffffffff8112faae>] ? find_get_page+0x1e/0xa0
[    4.796170]  [<ffffffff815b1a90>] sock_sendmsg+0xb0/0xe0
[    4.796171]  [<ffffffff81158525>] ? handle_pte_fault+0x95/0x450
[    4.796173]  [<ffffffff815b500d>] sys_sendto+0x12d/0x180
[    4.796174]  [<ffffffff816d13be>] ? do_page_fault+0xe/0x10
[    4.796176]  [<ffffffff816d59dd>] system_call_fastpath+0x1a/0x1f
[    4.796176] ---[ end trace eaeaa88497c34cd7 ]---
[ 6396.491583] systemd-hostnamed[3647]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
[13799.934065] wlan0: deauthenticated from c0:3f:0e:65:fd:56 (Reason: 7)
[13799.943480] cfg80211: Calling CRDA to update world regulatory domain
[13799.947692] cfg80211: World regulatory domain updated:
[13799.947696] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[13799.947699] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[13799.947701] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[13799.947703] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[13799.947705] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[13799.947706] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[13801.203164] wlan0: authenticate with c0:3f:0e:65:fd:56
[13801.212910] wlan0: send auth to c0:3f:0e:65:fd:56 (try 1/3)
[13801.214439] wlan0: authenticated
[13801.214626] wlan0: associate with c0:3f:0e:65:fd:56 (try 1/3)
[13801.216973] wlan0: RX AssocResp from c0:3f:0e:65:fd:56 (capab=0x411 status=0 aid=2)
[13801.217083] wlan0: associated
[19548.854503] wlan0: deauthenticated from c0:3f:0e:65:fd:56 (Reason: 7)
[19548.866109] cfg80211: Calling CRDA to update world regulatory domain
[19548.871873] cfg80211: World regulatory domain updated:
[19548.871877] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[19548.871880] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[19548.871882] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[19548.871884] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[19548.871886] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[19548.871887] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[19550.125735] wlan0: authenticate with c0:3f:0e:65:fd:56
[19550.135511] wlan0: send auth to c0:3f:0e:65:fd:56 (try 1/3)
[19550.137005] wlan0: authenticated
[19550.137291] wlan0: associate with c0:3f:0e:65:fd:56 (try 1/3)
[19550.139619] wlan0: RX AssocResp from c0:3f:0e:65:fd:56 (capab=0x411 status=0 aid=2)
[19550.139730] wlan0: associated
[32345.087499] systemd-hostnamed[5694]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
[33057.328742] wlan0: deauthenticating from c0:3f:0e:65:fd:56 by local choice (reason=3)
[33057.359140] cfg80211: Calling CRDA to update world regulatory domain
[33057.361764] cfg80211: World regulatory domain updated:
[33057.361766] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[33057.361767] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[33057.361768] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[33057.361769] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[33057.361770] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[33057.361771] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[33057.840104] pcieport 0000:00:1c.4: System wakeup enabled by ACPI
[33057.855116] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[33057.855201] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[33058.299395] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[33058.299722] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[33058.314597] tg3 0000:03:00.0: irq 50 for MSI/MSI-X
[33058.314605] tg3 0000:03:00.0: irq 51 for MSI/MSI-X
[33058.314611] tg3 0000:03:00.0: irq 52 for MSI/MSI-X
[33058.314616] tg3 0000:03:00.0: irq 53 for MSI/MSI-X
[33058.314621] tg3 0000:03:00.0: irq 54 for MSI/MSI-X
[33058.767533] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[33058.767778] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[33060.801418] wlan0: authenticate with c0:3f:0e:65:fd:56
[33060.811171] wlan0: send auth to c0:3f:0e:65:fd:56 (try 1/3)
[33060.812685] wlan0: authenticated
[33060.812903] wlan0: associate with c0:3f:0e:65:fd:56 (try 1/3)
[33060.815177] wlan0: RX AssocResp from c0:3f:0e:65:fd:56 (capab=0x411 status=0 aid=2)
[33060.815285] wlan0: associated
[33060.815295] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[34968.708474] systemd-hostnamed[6032]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
[37333.291721] wlan0: deauthenticating from c0:3f:0e:65:fd:56 by local choice (reason=3)
[37333.304254] cfg80211: Calling CRDA to update world regulatory domain
[37333.307988] cfg80211: World regulatory domain updated:
[37333.307990] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[37333.307991] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[37333.307992] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[37333.307993] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[37333.307993] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[37333.307994] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[37333.807998] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[37333.808082] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[37334.239228] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[37334.239531] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[37334.255384] tg3 0000:03:00.0: irq 50 for MSI/MSI-X
[37334.255392] tg3 0000:03:00.0: irq 51 for MSI/MSI-X
[37334.255397] tg3 0000:03:00.0: irq 52 for MSI/MSI-X
[37334.255401] tg3 0000:03:00.0: irq 53 for MSI/MSI-X
[37334.255405] tg3 0000:03:00.0: irq 54 for MSI/MSI-X
[37334.708495] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[37334.708746] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[37336.750166] wlan0: authenticate with c0:3f:0e:65:fd:56
[37336.759994] wlan0: send auth to c0:3f:0e:65:fd:56 (try 1/3)
[37336.761508] wlan0: authenticated
[37336.761745] wlan0: associate with c0:3f:0e:65:fd:56 (try 1/3)
[37336.764025] wlan0: RX AssocResp from c0:3f:0e:65:fd:56 (capab=0x411 status=0 aid=2)
[37336.764135] wlan0: associated
[37336.764145] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[68590.711538] usb 1-1.3: new high-speed USB device number 3 using ehci-pci
[68591.931041] hub 1-1:1.0: unable to enumerate USB device on port 3
[68592.130675] usb 1-1.3: new high-speed USB device number 4 using ehci-pci
[68598.934969] hub 1-1:1.0: unable to enumerate USB device on port 3
[68599.310506] usb 1-1.3: new high-speed USB device number 5 using ehci-pci
[68599.403566] usb 1-1.3: New USB device found, idVendor=2080, idProduct=0001
[68599.403571] usb 1-1.3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[68599.403574] usb 1-1.3: Product: NOOK
[68599.403576] usb 1-1.3: Manufacturer: Linux 2.6.27-svn40739 with s3c-udc
[68599.403578] usb 1-1.3: SerialNumber: 372041756775
[68599.418738] Initializing USB Mass Storage driver...
[68599.418869] scsi8 : usb-storage 1-1.3:1.0
[68599.418963] usbcore: registered new interface driver usb-storage
[68599.418965] USB Mass Storage support registered.
[68600.420268] scsi 8:0:0:0: Direct-Access     B&N      NOOK             0322 PQ: 0 ANSI: 2
[68600.421102] sd 8:0:0:0: Attached scsi generic sg3 type 0
[68600.424191] sd 8:0:0:0: [sdc] Attached SCSI removable disk
[68639.703459] sd 8:0:0:0: [sdc] 2649276 512-byte logical blocks: (1.35 GB/1.26 GiB)
[68639.704685] sd 8:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[68639.711434]  sdc:
[71847.632814] wlan0: deauthenticating from c0:3f:0e:65:fd:56 by local choice (reason=3)
[71847.673500] cfg80211: Calling CRDA to update world regulatory domain
[71847.689776] cfg80211: World regulatory domain updated:
[71847.689781] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[71847.689783] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[71847.689786] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[71847.689788] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[71847.689789] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[71847.689791] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[71848.161632] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[71848.161715] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[71848.590457] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[71848.590782] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[71848.608843] tg3 0000:03:00.0: irq 50 for MSI/MSI-X
[71848.608850] tg3 0000:03:00.0: irq 51 for MSI/MSI-X
[71848.608855] tg3 0000:03:00.0: irq 52 for MSI/MSI-X
[71848.608859] tg3 0000:03:00.0: irq 53 for MSI/MSI-X
[71848.608864] tg3 0000:03:00.0: irq 54 for MSI/MSI-X
[71849.061897] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[71849.062111] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[71851.083840] wlan0: authenticate with c0:3f:0e:65:fd:56
[71851.093504] wlan0: send auth to c0:3f:0e:65:fd:56 (try 1/3)
[71851.095043] wlan0: authenticated
[71851.095209] wlan0: associate with c0:3f:0e:65:fd:56 (try 1/3)
[71851.099881] wlan0: RX AssocResp from c0:3f:0e:65:fd:56 (capab=0x411 status=0 aid=2)
[71851.099997] wlan0: associated
[71851.100007] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[72425.700517] systemd-hostnamed[8445]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
[72885.920880] wlan0: deauthenticating from c0:3f:0e:65:fd:56 by local choice (reason=3)
[72885.960792] cfg80211: Calling CRDA to update world regulatory domain
[72885.984167] cfg80211: World regulatory domain updated:
[72885.984170] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[72885.984171] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[72885.984172] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[72885.984173] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[72885.984174] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[72885.984174] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[72886.456173] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[72886.456255] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[72886.885275] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[72886.885435] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[72886.899569] tg3 0000:03:00.0: irq 50 for MSI/MSI-X
[72886.899576] tg3 0000:03:00.0: irq 51 for MSI/MSI-X
[72886.899580] tg3 0000:03:00.0: irq 52 for MSI/MSI-X
[72886.899585] tg3 0000:03:00.0: irq 53 for MSI/MSI-X
[72886.899589] tg3 0000:03:00.0: irq 54 for MSI/MSI-X
[72887.352438] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[72887.352701] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[72889.390393] wlan0: authenticate with c0:3f:0e:65:fd:56
[72889.400201] wlan0: send auth to c0:3f:0e:65:fd:56 (try 1/3)
[72889.401777] wlan0: authenticated
[72889.405890] wlan0: associate with c0:3f:0e:65:fd:56 (try 1/3)
[72889.408319] wlan0: RX AssocResp from c0:3f:0e:65:fd:56 (capab=0x411 status=0 aid=2)
[72889.408434] wlan0: associated
[72889.408443] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[73193.683639] device wlan0 entered promiscuous mode
[73417.590059] device wlan0 left promiscuous mode


=======================================================
=======================================================


"lshw -C network" output:


  *-network
       description: Wireless interface
       product: RTL8188CE 802.11b/g/n WiFi Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wlan0
       version: 01
       serial: 08:10:76:26:32:75
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192ce driverversion=3.8.0-31-generic firmware=N/A ip=192.168.1.6 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:16 ioport:e000(size=256) memory:f7b00000-f7b03fff




  *-network
       description: Ethernet interface
       product: NetLink BCM57781 Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 10
       serial: bc:5f:f4:47:f8:79
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi msix pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.128 firmware=sb latency=0 link=no multicast=yes port=twisted pair
       resources: irq:16 memory:f0010000-f001ffff memory:f0000000-f000ffff memory:f7900000-f79007ff


=======================================================
=======================================================


"iwlist wlan0 scan" output:


wlan0     Scan completed :
          Cell 01 - Address: C0:3F:0E:65:FD:56
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=58/70  Signal level=-52 dBm  
                    Encryption key:on
                    ESSID:"CG"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000006683b39b28
                    Extra: Last beacon: 80ms ago
                    IE: Unknown: 00024347
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030107
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD7F0050F204104A00011010440001021041000100103B0001031047001068C74F5740753E21F84F06938B5940371021000D4E4554474541522C20496E632E10230009574752363134763130102400095747523631347631301042000538333235381054000800060050F204000110110009574752363134763130100800020084
                    IE: Unknown: DD090010180206F0050000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 02 - Address: 84:1B:5E:53:3B:58
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=57/70  Signal level=-53 dBm  
                    Encryption key:on
                    ESSID:"NETGEAR09"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000051e8c052c5
                    Extra: Last beacon: 80ms ago
                    IE: Unknown: 00094E4554474541523039
                    IE: Unknown: 010882840B162430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AAC191BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606081500000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD7A0050F204104A0001101044000102103B00010310470010F4CDEE5FA8BAF4B3B6B926DA6AF93CB71021000D4E4554474541522C20496E632E1023000552363230301024000552363230301042000230311054000800060050F2040001101100055236323030100800020004103C0001031049000600372A000120
                    IE: Unknown: DD090010180202000C0000
                    IE: Unknown: DD180050F2020101880003A4000027A400004243BC0062326600
          Cell 03 - Address: E8:89:2C:36:7A:10
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=59/70  Signal level=-51 dBm  
                    Encryption key:on
                    ESSID:"HOME-7A12"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000025c330ed6ff
                    Extra: Last beacon: 80ms ago
                    IE: Unknown: 0009484F4D452D37413132
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1A0C0017FFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B000000000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05000021127A
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4303000000
                    IE: Unknown: 0706555320010B10
                    IE: Unknown: DD870050F204104A0001101044000102103B000103104700102880288028801880A880E8892C367A1010210005415252495310230006544738363247102400065254323836301042000831323334353637381054000800060050F204000110110012415252495320544738363220526F7574657210080002210C103C0001011049000600372A000120
          Cell 04 - Address: EA:89:2C:36:7A:10
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=59/70  Signal level=-51 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000025c33145bec
                    Extra: Last beacon: 152ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010B
                    IE: Unknown: 32040C183060
                    IE: Unknown: 070C55532001010F0209110B010F
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1A0C0017FFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B000000000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05000021127A
                    IE: Unknown: DD07000C4303000000
          Cell 05 - Address: 44:32:C8:BF:C1:78
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=59/70  Signal level=-51 dBm  
                    Encryption key:on
                    ESSID:"HOME-C178"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000072f3817636
                    Extra: Last beacon: 80ms ago
                    IE: Unknown: 0009484F4D452D43313738
                    IE: Unknown: 010882848B9624B0486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32048C129860
                    IE: Unknown: 2D1AFD181BFFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 3D160B081500000000000000000000000000000000000000
                    IE: Unknown: DD8C0050F204104A0001101044000102103B000103104700107FC31E62BB8674613C44ED57497A5BFC1021000B546563686E69636F6C6F721023000B546563686E69636F6C6F721024000631323334353610420007303030303030311054000800060050F20400011011000D546563686E69636F6C6F724150100800022008103C0001011049000600372A000120
                    IE: Unknown: DD090010180206F03C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00


=======================================================
=======================================================


"uname -mr" output:


3.8.0-31-generic x86_64
```

Thanks for any help.


P.S. if anyone reading this can update the HOWTO thread here ([http://ubuntuforums.org/showthread.php?p=6183681](http://ubuntuforums.org/showthread.php?p=6183681)), I think step 10 should be changed to restarting the "network-manager" service instead. Also, The options in step 7 are reversed (should be "iwlist wlan0 scan")

---

### Post by varunendra on 2013-10-10
Welcome to the forums Vikas!

> **Vikas_Biliyar said:**
> ```

"iwlist wlan0 scan" output:


wlan0     Scan completed :
          Cell 01 - Address: C0:3F:0E:65:FD:56
                    Channel:7
                    Frequency:2.442 GHz ([COLOR="#FF0000"]Channel 7[/COLOR])
                    Quality=58/70  Signal level=-52 dBm  
                    Encryption key:on
                    ESSID:"CG"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000006683b39b28
                    Extra: Last beacon: 80ms ago
                    IE: Unknown: 00024347
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030107
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/**WPA2** Version 1
                        Group Cipher : **[COLOR="#FF0000"]TKIP[/COLOR]**
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD7F0050F204104A00011010440001021041000100103B0001031047001068C74F5740753E21F84F06938B5940371021000D4E4554474541522C20496E632E10230009574752363134763130102400095747523631347631301042000538333235381054000800060050F204000110110009574752363134763130100800020084
                    IE: Unknown: DD090010180206F0050000
                    IE: **[COLOR="#FF0000"]WPA Version 1[/COLOR]**
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 02 - Address: 84:1B:5E:53:3B:58
                    Channel:6
                    Frequency:2.437 GHz ([COLOR="#FF0000"]Channel 6[/COLOR])
                    Quality=57/70  Signal level=-53 dBm  
                    Encryption key:on
                    ESSID:"NETGEAR09"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000051e8c052c5
                    Extra: Last beacon: 80ms ago
                    IE: Unknown: 00094E4554474541523039
                    IE: Unknown: 010882840B162430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AAC191BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606081500000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD7A0050F204104A0001101044000102103B00010310470010F4CDEE5FA8BAF4B3B6B926DA6AF93CB71021000D4E4554474541522C20496E632E1023000552363230301024000552363230301042000230311054000800060050F2040001101100055236323030100800020004103C0001031049000600372A000120
                    IE: Unknown: DD090010180202000C0000
                    IE: Unknown: DD180050F2020101880003A4000027A400004243BC0062326600
          Cell 03 - Address: E8:89:2C:36:7A:10
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=59/70  Signal level=-51 dBm  
                    Encryption key:on
                    ESSID:"HOME-7A12"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000025c330ed6ff
                    Extra: Last beacon: 80ms ago
                    IE: Unknown: 0009484F4D452D37413132
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1A0C0017FFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B000000000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: WPA Version 1
                        Group Cipher : **[COLOR="#FF0000"]TKIP[/COLOR]**
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05000021127A
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4303000000
                    IE: Unknown: 0706555320010B10
                    IE: Unknown: DD870050F204104A0001101044000102103B000103104700102880288028801880A880E8892C367A1010210005415252495310230006544738363247102400065254323836301042000831323334353637381054000800060050F204000110110012415252495320544738363220526F7574657210080002210C103C0001011049000600372A000120
          Cell 04 - Address: EA:89:2C:36:7A:10
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=59/70  Signal level=-51 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000025c33145bec
                    Extra: Last beacon: 152ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010B
                    IE: Unknown: 32040C183060
                    IE: Unknown: 070C55532001010F0209110B010F
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1A0C0017FFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B000000000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05000021127A
                    IE: Unknown: DD07000C4303000000
          Cell 05 - Address: 44:32:C8:BF:C1:78
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=59/70  Signal level=-51 dBm  
                    Encryption key:on
                    ESSID:"HOME-C178"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000072f3817636
                    Extra: Last beacon: 80ms ago
                    IE: Unknown: 0009484F4D452D43313738
                    IE: Unknown: 010882848B9624B0486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i**/WPA2 Version 1**
                        Group Cipher : **[COLOR="#FF0000"]TKIP[/COLOR]**
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32048C129860
                    IE: Unknown: 2D1AFD181BFFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 3D160B081500000000000000000000000000000000000000
                    IE: Unknown: DD8C0050F204104A0001101044000102103B000103104700107FC31E62BB8674613C44ED57497A5BFC1021000B546563686E69636F6C6F721023000B546563686E69636F6C6F721024000631323334353610420007303030303030311054000800060050F20400011011000D546563686E69636F6C6F724150100800022008103C0001011049000600372A000120
                    IE: Unknown: DD090010180206F03C0000
                    IE: **[COLOR="#FF0000"]WPA Version 1[/COLOR]**
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
```

Which one of the above is your access-point? Linux drivers usually work better with channel 1 or 11, and it is highly recommended to use the encryption type pure WPA2-PSK (AES or CCMP).

WPA/WPA2 mixed mode and TKIP should be avoided at all costs. Apart from above changes that need to be done in the router/access-point, try this with the driver in Ubuntu -
```
sudo modprobe -rv rtl8192ce
sudo modprobe -v rtl8192ce swenc=1
```
This is a temporary change that will be lost at next boot. If it seems to help, we can make it permanent. If not, you can try a couple of other parameters - "ips=0" and "fwlps=0" (one at a time, or a combination of the two or all three, like the following) -
```
sudo modprobe -rv rtl8192ce
sudo modprobe -v rtl8192ce swenc=1 ips=0 fwlps=0
```

> P.S. if anyone reading this can update the HOWTO thread here ([http://ubuntuforums.org/showthread.php?p=6183681](http://ubuntuforums.org/showthread.php?p=6183681)), I think step 10 should be changed to restarting the "network-manager" service instead. Also, The options in step 7 are reversed (should be "iwlist wlan0 scan")
I agree with you, the recommended method in newer versions is "**sudo service networking restart**" for step 10, and step 7 is clearly a typo.

I'll report it to the mods and see if they agree too.

---

### Post by Vikas_Biliyar on 2013-10-10
> **varunendra said:**
> Welcome to the forums Vikas!



Which one of the above is your access-point? Linux drivers usually work better with channel 1 or 11, and it is highly recommended to use the encryption type pure WPA2-PSK (AES or CCMP).

WPA/WPA2 mixed mode and TKIP should be avoided at all costs. Apart from above changes that need to be done in the router/access-point, try this with the driver in Ubuntu -
```
sudo modprobe -rv rtl8192ce
sudo modprobe -v rtl8192ce swenc=1
```
This is a temporary change that will be lost at next boot. If it seems to help, we can make it permanent. If not, you can try a couple of other parameters - "ips=0" and "fwlps=0" (one at a time, or a combination of the two or all three, like the following) -
```
sudo modprobe -rv rtl8192ce
sudo modprobe -v rtl8192ce swenc=1 ips=0 fwlps=0
```


I agree with you, the recommended method in newer versions is "**sudo service networking restart**" for step 10, and step 7 is clearly a typo.

I'll report it to the mods and see if they agree too.

Hi Varun, thanks for your response.

Unfortunately, I'm not in a position to change the router settings, as my landlord has it set to his preferences. I use the first network ("CG"), which is on Channel 7 and uses TKIP, so if that's the issue, I may not be able to resolve it.

For the second portion, I haven't been able to find out what the swenc, ips, or fwlps options passed to the kernel actually do. Could you elaborate on them (or send me a link with the kernel options described)?

---

### Post by varunendra on 2013-10-11
> **Vikas_Biliyar said:**
> For the second portion, I haven't been able to find out what the swenc, ips, or fwlps options passed to the kernel actually do. Could you elaborate on them (or send me a link with the kernel options described)?

Check out the output of -
```
modinfo rtl8192ce
```
and look at the bottom of the output for "parm (parameter)". It explains briefly what each option is supposed to do, what can be acceptable vlaues and what are the default values.

Basically, they are as following -
*** swenc** = Setting it to "1" disables the (WiFi card's) hardware encryption, and changes it to "**s**oft**w**are **enc**ryption", thus shifting the workload of encryption from the card's hardware to the OS/driver. It helps when the data rate is high and/or the card's hardware can't keep up with the encryption speed for some reasons. Since the computer's processing power is 'ultra-high' compared to that of the card's, it can easily bear that extra workload.

*** ips** = Setting it to "0" disables "Link Power Save", which (guessing by its name) is probably a power saving mode that kicks in when no link (or traffic) is detected. I believe this may cause inconsistent performance (not many people try it, but I have had a few positive feedbacks after using it).

*** fwlps** = Setting it to "0" disables "Firmware Control Power Save", which (again, guessing by its name) is yet another power saving feature. In essence, whenever there is an inconsistent performance (fluctuating speed, disconnecting after certain time etc.), power saving features are our prime suspects. You can say we (most of the wifi troubleshooters here) are kinda allergic to power saving on wifi (why turn it on if you need to save power?). :P

You may get authentic explanations in the comments within the source code of the driver, I never looked into it. The source code can be easily serached on the net (with keywords like "rtl8192ce source").

Not being able to change the properties in the router is a problem since it is using the dreaded mixed mode+TKIP, but not necessarily a big one. Developers know these kind of settings exist and are widely in use, so the drivers they design are *supposed* to work with these as well, even if not with the optimal performance.

So I'd suggest you try the two modprobe commands (with various parameters I suggested, or all three at once) first. If they don't help, we may try either a backported driver from newer kernels, or the Proprietary one from Realtek.

In general, the performance of these drivers in latest kernels has been good enough, so we shouldn't need to try those other ones.

---

### Post by Vikas_Biliyar on 2013-10-12
> **varunendra said:**
> 
*** fwlps** = Setting it to "0" disables "Firmware Control Power Save", which (again, guessing by its name) is yet another power saving feature. In essence, whenever there is an inconsistent performance (fluctuating speed, disconnecting after certain time etc.), power saving features are our prime suspects. You can say we (most of the wifi troubleshooters here) are kinda allergic to power saving on wifi (why turn it on if you need to save power?). :P


Hi Varun,

The first two commands didn't have a noticeable effect, but setting fwlps=0 seems to have done the trick.

Thanks a lot for your help. When I've got a bit of time, I'll try to figure out how to make the change permanent.

---

### Post by varunendra on 2013-10-12
> **Vikas_Biliyar said:**
> Hi Varun,

The first two commands didn't have a noticeable effect, but setting fwlps=0 seems to have done the trick.

Thanks a lot for your help. When I've got a bit of time, I'll try to figure out how to make the change permanent.

You're welcome. :)

To make it permanent -
```
echo "options rtl8192ce fwlps=0" | sudo tee /etc/modprobe.d/rtl8192ce.conf
```

This will create a .conf file (rtl8192ce.conf) in **/etc/modprobe.d** directory with a line "**options rtl8192ce fwlps=0**" in it. The .conf files in this directory are read each time before loading any modules, applying the extra settings mentioned in them, thus making them permanent.

If more than one parameter is required, mention it on the same line, for example - "options rtl8192ce swenc=1 fwlps=0".

If this seems to make the connection stable and reliable, please mark the thread **[SOLVED]** using the "**Thread Tools**" menu above the top post.

---

