---
title: "TV Time"
date: 2009-12-03
forum: New to Ubuntu
---

### Post by theozzlives on 2009-12-03
I can't get TV time to recognize my ADS USB TV Tuner. It says "no input device" (or something like that). Any ideas?

---

### Post by cariboo on 2009-12-03
What's the output of dmesg when you plug the device in?

---

### Post by theozzlives on 2009-12-04
> **cariboo907 said:**
> What's the output of dmesg when you plug the device in?

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.31-15-generic (buildd@yellow) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #50-Ubuntu SMP Tue Nov 10 14:53:52 UTC 2009 (Ubuntu 2.6.31-15.50-generic)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-15-generic root=UUID=bbedca1b-f443-4838-aec8-1c876d6705af ro quiet splash
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000df66d800 (usable)
[    0.000000]  BIOS-e820: 00000000df66d800 - 00000000e0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000f8000000 - 00000000fc000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed18000 - 00000000fed1c000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed20000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000feda0000 - 00000000feda6000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee10000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffe00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000120000000 (usable)
[    0.000000] DMI 2.4 present.
[    0.000000] last_pfn = 0x120000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 080000000 mask FC0000000 write-back
[    0.000000]   2 base 0C0000000 mask FE0000000 write-back
[    0.000000]   3 base 100000000 mask F00000000 write-back
[    0.000000]   4 base 0DF800000 mask FFF800000 uncachable
[    0.000000]   5 base 0DF700000 mask FFFF00000 uncachable
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 00000000df700000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0xdf66d max_arch_pfn = 0x400000000
[    0.000000] e820 update range: 0000000000001000 - 0000000000006000 (usable) ==> (reserved)
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000001000 (usable)
[    0.000000]  modified: 0000000000001000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 000000000009f000 (usable)
[    0.000000]  modified: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000df66d800 (usable)
[    0.000000]  modified: 00000000df66d800 - 00000000e0000000 (reserved)
[    0.000000]  modified: 00000000f8000000 - 00000000fc000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  modified: 00000000fed18000 - 00000000fed1c000 (reserved)
[    0.000000]  modified: 00000000fed20000 - 00000000fed90000 (reserved)
[    0.000000]  modified: 00000000feda0000 - 00000000feda6000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee10000 (reserved)
[    0.000000]  modified: 00000000ffe00000 - 0000000100000000 (reserved)
[    0.000000]  modified: 0000000100000000 - 0000000120000000 (usable)
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] init_memory_mapping: 0000000000000000-00000000df66d000
[    0.000000] Warning: NX (Execute Disable) protection missing in CPU or disabled in BIOS!
[    0.000000]  0000000000 - 00df600000 page 2M
[    0.000000]  00df600000 - 00df66d000 page 4k
[    0.000000] kernel direct mapping tables up to df66d000 @ 8000-e000
[    0.000000] init_memory_mapping: 0000000100000000-0000000120000000
[    0.000000] Warning: NX (Execute Disable) protection missing in CPU or disabled in BIOS!
[    0.000000]  0100000000 - 0120000000 page 2M
[    0.000000] kernel direct mapping tables up to 120000000 @ c000-12000
[    0.000000] RAMDISK: 37831000 - 37fef179
[    0.000000] ACPI: RSDP 00000000000fbc60 00024 (v02 DELL  )
[    0.000000] ACPI: XSDT 00000000df66f200 00064 (v01 DELL    M08     27D80A10 ASL  00000061)
[    0.000000] ACPI: FACP 00000000df66f09c 000F4 (v04 DELL    M08     27D80A10 ASL  00000061)
[    0.000000] ACPI: DSDT 00000000df66f800 05477 (v02 INT430 SYSFexxx 00001001 INTL 20050624)
[    0.000000] ACPI: FACS 00000000df67e000 00040
[    0.000000] ACPI: HPET 00000000df66f300 00038 (v01 DELL    M08     00000001 ASL  00000061)
[    0.000000] ACPI: APIC 00000000df66f400 00068 (v01 DELL    M08     27D80A10 ASL  00000047)
[    0.000000] ACPI: MCFG 00000000df66f3c0 0003E (v16 DELL    M08     27D80A10 ASL  00000061)
[    0.000000] ACPI: SLIC 00000000df66f49c 00176 (v01 DELL    M08     27D80A10 ASL  00000061)
[    0.000000] ACPI: OSFR 00000000df66ea00 0008A (v01 DELL    M08     27D80A10 ASL  00000061)
[    0.000000] ACPI: BOOT 00000000df66efc0 00028 (v01 DELL    M08     27D80A10 ASL  00000061)
[    0.000000] ACPI: SSDT 00000000df66da02 004CC (v01  PmRef    CpuPm 00003000 INTL 20050624)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-0000000120000000
[    0.000000] Bootmem setup node 0 0000000000000000-0000000120000000
[    0.000000]   NODE_DATA [000000000000d000 - 0000000000011fff]
[    0.000000]   bootmap [0000000000012000 -  0000000000035fff] pages 24
[    0.000000] (8 early reservations) ==> bootmem [0000000000 - 0120000000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
[    0.000000]   #2 [0001000000 - 00019e4ccc]    TEXT DATA BSS ==> [0001000000 - 00019e4ccc]
[    0.000000]   #3 [0037831000 - 0037fef179]          RAMDISK ==> [0037831000 - 0037fef179]
[    0.000000]   #4 [000009f000 - 0000100000]    BIOS reserved ==> [000009f000 - 0000100000]
[    0.000000]   #5 [00019e5000 - 00019e51e8]              BRK ==> [00019e5000 - 00019e51e8]
[    0.000000]   #6 [0000008000 - 000000c000]          PGTABLE ==> [0000008000 - 000000c000]
[    0.000000]   #7 [000000c000 - 000000d000]          PGTABLE ==> [000000c000 - 000000d000]
[    0.000000]  [ffffea0000000000-ffffea0003ffffff] PMD -> [ffff880028600000-ffff88002bffffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00120000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[4] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000001
[    0.000000]     0: 0x00000006 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x000df66d
[    0.000000]     0: 0x00100000 -> 0x00120000
[    0.000000] On node 0 totalpages: 1046023
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 105 pages reserved
[    0.000000]   DMA zone: 3833 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14280 pages used for memmap
[    0.000000]   DMA32 zone: 896677 pages, LIFO batch:31
[    0.000000]   Normal zone: 1792 pages used for memmap
[    0.000000]   Normal zone: 129280 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 0000000000001000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000df66d000 - 00000000df66e000
[    0.000000] PM: Registered nosave memory: 00000000df66e000 - 00000000e0000000
[    0.000000] PM: Registered nosave memory: 00000000e0000000 - 00000000f8000000
[    0.000000] PM: Registered nosave memory: 00000000f8000000 - 00000000fc000000
[    0.000000] PM: Registered nosave memory: 00000000fc000000 - 00000000fec00000
[    0.000000] PM: Registered nosave memory: 00000000fec00000 - 00000000fec10000
[    0.000000] PM: Registered nosave memory: 00000000fec10000 - 00000000fed18000
[    0.000000] PM: Registered nosave memory: 00000000fed18000 - 00000000fed1c000
[    0.000000] PM: Registered nosave memory: 00000000fed1c000 - 00000000fed20000
[    0.000000] PM: Registered nosave memory: 00000000fed20000 - 00000000fed90000
[    0.000000] PM: Registered nosave memory: 00000000fed90000 - 00000000feda0000
[    0.000000] PM: Registered nosave memory: 00000000feda0000 - 00000000feda6000
[    0.000000] PM: Registered nosave memory: 00000000feda6000 - 00000000fee00000
[    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee10000
[    0.000000] PM: Registered nosave memory: 00000000fee10000 - 00000000ffe00000
[    0.000000] PM: Registered nosave memory: 00000000ffe00000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at e0000000 (gap: e0000000:18000000)
[    0.000000] NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 30 pages at ffff88002801f000, static data 90720 bytes
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1029790
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-15-generic root=UUID=bbedca1b-f443-4838-aec8-1c876d6705af ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.000000] Placing 64MB software IO TLB between ffff880020000000 - ffff880024000000
[    0.000000] software IO TLB at phys 0x20000000 - 0x24000000
[    0.000000] Memory: 4040200k/4718592k available (5315k kernel code, 534500k absent, 143892k reserved, 3018k data, 660k init)
[    0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] NR_IRQS:4352 nr_irqs:424
[    0.000000] Extended CMOS year: 2000
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1728.734 MHz processor.
[    0.001455] Console: colour VGA+ 80x25
[    0.001459] console [tty0] enabled
[    0.010000] allocated 41943040 bytes of page_cgroup
[    0.010000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.010000] hpet clockevent registered
[    0.010000] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.010000] Calibrating delay loop (skipped), value calculated using timer frequency.. 3457.46 BogoMIPS (lpj=17287340)
[    0.010000] Security Framework initialized
[    0.010000] AppArmor: AppArmor initialized
[    0.010000] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.010000] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.010000] Mount-cache hash table entries: 256
[    0.010000] Initializing cgroup subsys ns
[    0.010000] Initializing cgroup subsys cpuacct
[    0.010000] Initializing cgroup subsys memory
[    0.010000] Initializing cgroup subsys freezer
[    0.010000] Initializing cgroup subsys net_cls
[    0.010000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.010000] CPU: L2 cache: 1024K
[    0.010000] CPU 0/0x0 -> Node 0
[    0.010000] CPU: Physical Processor ID: 0
[    0.010000] CPU: Processor Core ID: 0
[    0.010000] mce: CPU supports 6 MCE banks
[    0.010000] CPU0: Thermal monitoring enabled (TM2)
[    0.010000] using mwait in idle threads.
[    0.010000] Performance Counters: Core2 events, Intel PMU driver.
[    0.010000] ... version:                 2
[    0.010000] ... bit width:               40
[    0.010000] ... generic counters:        2
[    0.010000] ... value mask:              000000ffffffffff
[    0.010000] ... max period:              000000007fffffff
[    0.010000] ... fixed-purpose counters:  3
[    0.010000] ... counter mask:            0000000700000003
[    0.010000] ACPI: Core revision 20090521
[    0.020076] Setting APIC routing to flat
[    0.020471] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.121474] CPU0: Intel(R) Pentium(R) Dual  CPU  T2370  @ 1.73GHz stepping 0d
[    0.130000] Booting processor 1 APIC 0x1 ip 0x6000
[    0.010000] Initializing CPU#1
[    0.010000] Calibrating delay using timer specific routine.. 3458.01 BogoMIPS (lpj=17290070)
[    0.010000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.010000] CPU: L2 cache: 1024K
[    0.010000] CPU 1/0x1 -> Node 0
[    0.010000] CPU: Physical Processor ID: 0
[    0.010000] CPU: Processor Core ID: 1
[    0.010000] mce: CPU supports 6 MCE banks
[    0.010000] CPU1: Thermal monitoring enabled (TM2)
[    0.010000] x86 PAT enabled: cpu 1, old 0x7040600070406, new 0x7010600070106
[    0.281500] CPU1: Intel(R) Pentium(R) Dual  CPU  T2370  @ 1.73GHz stepping 0d
[    0.281512] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.290030] Brought up 2 CPUs
[    0.290033] Total of 2 processors activated (6915.48 BogoMIPS).
[    0.290097] CPU0 attaching sched-domain:
[    0.290100]  domain 0: span 0-1 level MC
[    0.290103]   groups: 0 1
[    0.290109] CPU1 attaching sched-domain:
[    0.290111]  domain 0: span 0-1 level MC
[    0.290114]   groups: 1 0
[    0.290202] Booting paravirtualized kernel on bare hardware
[    0.290202] regulator: core version 0.5
[    0.290202] Time: 13:22:01  Date: 12/04/09
[    0.290202] NET: Registered protocol family 16
[    0.290270] ACPI: bus type pci registered
[    0.290357] PCI: MCFG configuration 0: base f8000000 segment 0 buses 0 - 63
[    0.290360] PCI: MCFG area at f8000000 reserved in E820
[    0.292627] PCI: Using MMCONFIG at f8000000 - fbffffff
[    0.292629] PCI: Using configuration type 1 for base access
[    0.293671] bio: create slab <bio-0> at 0
[    0.293671] ACPI: EC: Look up EC in DSDT
[    0.329579] ACPI: Interpreter enabled
[    0.329584] ACPI: (supports S0 S3 S4 S5)
[    0.329607] ACPI: Using IOAPIC for interrupt routing
[    0.377371] ACPI: No dock devices found.
[    0.395950] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.396078] pci 0000:00:02.0: reg 10 64bit mmio: [0xfea00000-0xfeafffff]
[    0.396088] pci 0000:00:02.0: reg 18 64bit mmio: [0xe0000000-0xefffffff]
[    0.396094] pci 0000:00:02.0: reg 20 io port: [0xefe8-0xefef]
[    0.396146] pci 0000:00:02.1: reg 10 64bit mmio: [0xfeb00000-0xfebfffff]
[    0.396285] pci 0000:00:1a.0: reg 20 io port: [0x6f20-0x6f3f]
[    0.396362] pci 0000:00:1a.1: reg 20 io port: [0x6f00-0x6f1f]
[    0.396448] pci 0000:00:1a.7: reg 10 32bit mmio: [0xfed1c400-0xfed1c7ff]
[    0.396524] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.396531] pci 0000:00:1a.7: PME# disabled
[    0.396598] pci 0000:00:1b.0: reg 10 64bit mmio: [0xfe9fc000-0xfe9fffff]
[    0.396671] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.396677] pci 0000:00:1b.0: PME# disabled
[    0.396780] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.396785] pci 0000:00:1c.0: PME# disabled
[    0.396892] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.396897] pci 0000:00:1c.1: PME# disabled
[    0.397008] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.397013] pci 0000:00:1c.4: PME# disabled
[    0.397090] pci 0000:00:1d.0: reg 20 io port: [0x6f80-0x6f9f]
[    0.397168] pci 0000:00:1d.1: reg 20 io port: [0x6f60-0x6f7f]
[    0.397245] pci 0000:00:1d.2: reg 20 io port: [0x6f40-0x6f5f]
[    0.397329] pci 0000:00:1d.7: reg 10 32bit mmio: [0xfed1c000-0xfed1c3ff]
[    0.397405] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.397411] pci 0000:00:1d.7: PME# disabled
[    0.397608] pci 0000:00:1f.0: quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[    0.397614] pci 0000:00:1f.0: quirk: region 1080-10bf claimed by ICH6 GPIO
[    0.397619] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0900 (mask 007f)
[    0.397624] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 2 PIO at 006c (mask 0007)
[    0.397629] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 3 PIO at 0c80 (mask 003f)
[    0.397691] pci 0000:00:1f.1: reg 10 io port: [0x1f0-0x1f7]
[    0.397701] pci 0000:00:1f.1: reg 14 io port: [0x3f4-0x3f7]
[    0.397710] pci 0000:00:1f.1: reg 18 io port: [0x170-0x177]
[    0.397719] pci 0000:00:1f.1: reg 1c io port: [0x374-0x377]
[    0.397729] pci 0000:00:1f.1: reg 20 io port: [0x6fa0-0x6faf]
[    0.397796] pci 0000:00:1f.2: reg 10 io port: [0x6eb0-0x6eb7]
[    0.397805] pci 0000:00:1f.2: reg 14 io port: [0x6eb8-0x6ebb]
[    0.397815] pci 0000:00:1f.2: reg 18 io port: [0x6ec0-0x6ec7]
[    0.397824] pci 0000:00:1f.2: reg 1c io port: [0x6ec8-0x6ecb]
[    0.397833] pci 0000:00:1f.2: reg 20 io port: [0x6ee0-0x6eef]
[    0.397842] pci 0000:00:1f.2: reg 24 io port: [0xeff0-0xefff]
[    0.397878] pci 0000:00:1f.2: PME# supported from D3hot
[    0.397884] pci 0000:00:1f.2: PME# disabled
[    0.397916] pci 0000:00:1f.3: reg 10 32bit mmio: [0xfe9fbf00-0xfe9fbfff]
[    0.397946] pci 0000:00:1f.3: reg 20 io port: [0x10c0-0x10df]
[    0.398068] pci 0000:09:00.0: reg 10 64bit mmio: [0xfe8fc000-0xfe8fffff]
[    0.398081] pci 0000:09:00.0: reg 18 io port: [0xde00-0xdeff]
[    0.398180] pci 0000:09:00.0: supports D1 D2
[    0.398182] pci 0000:09:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.398190] pci 0000:09:00.0: PME# disabled
[    0.398284] pci 0000:00:1c.0: bridge io port: [0xd000-0xdfff]
[    0.398290] pci 0000:00:1c.0: bridge 32bit mmio: [0xfe800000-0xfe8fffff]
[    0.398513] pci 0000:0b:00.0: reg 10 64bit mmio: [0xfe7fc000-0xfe7fffff]
[    0.398744] pci 0000:0b:00.0: supports D1 D2
[    0.398747] pci 0000:0b:00.0: PME# supported from D0 D3hot D3cold
[    0.398759] pci 0000:0b:00.0: PME# disabled
[    0.398916] pci 0000:00:1c.1: bridge 32bit mmio: [0xfe700000-0xfe7fffff]
[    0.398998] pci 0000:00:1c.4: bridge io port: [0xc000-0xcfff]
[    0.399004] pci 0000:00:1c.4: bridge 32bit mmio: [0xfe400000-0xfe6fffff]
[    0.399014] pci 0000:00:1c.4: bridge 64bit mmio pref: [0xf0000000-0xf01fffff]
[    0.399086] pci 0000:02:09.0: reg 10 32bit mmio: [0xfe3ff800-0xfe3fffff]
[    0.399157] pci 0000:02:09.0: supports D1 D2
[    0.399159] pci 0000:02:09.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.399165] pci 0000:02:09.0: PME# disabled
[    0.399217] pci 0000:02:09.1: reg 10 32bit mmio: [0xfe3ff400-0xfe3ff4ff]
[    0.399287] pci 0000:02:09.1: supports D1 D2
[    0.399290] pci 0000:02:09.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.399296] pci 0000:02:09.1: PME# disabled
[    0.399348] pci 0000:02:09.2: reg 10 32bit mmio: [0xfe3ff500-0xfe3ff5ff]
[    0.399418] pci 0000:02:09.2: supports D1 D2
[    0.399420] pci 0000:02:09.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.399426] pci 0000:02:09.2: PME# disabled
[    0.399477] pci 0000:02:09.3: reg 10 32bit mmio: [0xfe3ff600-0xfe3ff6ff]
[    0.399549] pci 0000:02:09.3: supports D1 D2
[    0.399552] pci 0000:02:09.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.399558] pci 0000:02:09.3: PME# disabled
[    0.399608] pci 0000:02:09.4: reg 10 32bit mmio: [0xfe3ff700-0xfe3ff7ff]
[    0.399680] pci 0000:02:09.4: supports D1 D2
[    0.399682] pci 0000:02:09.4: PME# supported from D0 D1 D2 D3hot D3cold
[    0.399688] pci 0000:02:09.4: PME# disabled
[    0.399754] pci 0000:00:1e.0: transparent bridge
[    0.399763] pci 0000:00:1e.0: bridge 32bit mmio: [0xfe300000-0xfe3fffff]
[    0.399806] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.400134] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]
[    0.400287] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.400373] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    0.400463] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP05._PRT]
[    0.414424] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 *11)
[    0.414568] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *10
[    0.414709] ACPI: PCI Interrupt Link [LNKC] (IRQs 9 10 11) *5
[    0.414834] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 7 9 10 11) *0, disabled.
[    0.414976] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[    0.415121] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[    0.415265] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 *7 9 10 11 12 14 15)
[    0.415392] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.415628] SCSI subsystem initialized
[    0.415685] libata version 3.00 loaded.
[    0.415685] usbcore: registered new interface driver usbfs
[    0.415685] usbcore: registered new interface driver hub
[    0.415685] usbcore: registered new device driver usb
[    0.415685] ACPI: WMI: Mapper loaded
[    0.415685] PCI: Using ACPI for IRQ routing
[    0.440009] Bluetooth: Core ver 2.15
[    0.440030] NET: Registered protocol family 31
[    0.440030] Bluetooth: HCI device and connection manager initialized
[    0.440030] Bluetooth: HCI socket layer initialized
[    0.440030] NetLabel: Initializing
[    0.440030] NetLabel:  domain hash size = 128
[    0.440030] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.440045] NetLabel:  unlabeled traffic allowed by default
[    0.440108] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.440114] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.480018] pnp: PnP ACPI init
[    0.480047] ACPI: bus type pnp registered
[    0.499817] pnp 00:0a: io resource (0x1000-0x1005) overlaps 0000:00:1f.0 BAR 13 (0x1000-0x107f), disabling
[    0.499822] pnp 00:0a: io resource (0x1008-0x100f) overlaps 0000:00:1f.0 BAR 13 (0x1000-0x107f), disabling
[    0.499929] pnp 00:0b: io resource (0x1006-0x1007) overlaps 0000:00:1f.0 BAR 13 (0x1000-0x107f), disabling
[    0.499934] pnp 00:0b: io resource (0x100a-0x1059) overlaps 0000:00:1f.0 BAR 13 (0x1000-0x107f), disabling
[    0.499938] pnp 00:0b: io resource (0x1060-0x107f) overlaps 0000:00:1f.0 BAR 13 (0x1000-0x107f), disabling
[    0.499942] pnp 00:0b: io resource (0x1010-0x102f) overlaps 0000:00:1f.0 BAR 13 (0x1000-0x107f), disabling
[    0.501566] Switched to high resolution mode on CPU 1
[    0.510006] Switched to high resolution mode on CPU 0
[    0.523614] pnp: PnP ACPI: found 13 devices
[    0.523617] ACPI: ACPI bus type pnp unregistered
[    0.523631] system 00:01: iomem range 0xff800000-0xff8fffff has been reserved
[    0.523635] system 00:01: iomem range 0xffc00000-0xffcfffff has been reserved
[    0.523646] system 00:06: ioport range 0xc80-0xcff could not be reserved
[    0.523653] system 00:09: iomem range 0xfed00000-0xfed003ff has been reserved
[    0.523660] system 00:0a: ioport range 0x900-0x97f has been reserved
[    0.523663] system 00:0a: ioport range 0x4d0-0x4d1 has been reserved
[    0.523670] system 00:0b: ioport range 0xf400-0xf4fe has been reserved
[    0.523674] system 00:0b: ioport range 0x1080-0x10bf has been reserved
[    0.523677] system 00:0b: ioport range 0x10c0-0x10df has been reserved
[    0.523680] system 00:0b: ioport range 0x809-0x809 has been reserved
[    0.523687] system 00:0c: iomem range 0x0-0x9efff could not be reserved
[    0.523691] system 00:0c: iomem range 0x9f000-0x9ffff could not be reserved
[    0.523694] system 00:0c: iomem range 0xc0000-0xcffff has been reserved
[    0.523697] system 00:0c: iomem range 0xe0000-0xfffff has been reserved
[    0.523700] system 00:0c: iomem range 0x100000-0xdf66d7ff could not be reserved
[    0.523703] system 00:0c: iomem range 0xdf66d800-0xdf6fffff has been reserved
[    0.523707] system 00:0c: iomem range 0xdf700000-0xdf7fffff has been reserved
[    0.523710] system 00:0c: iomem range 0xdf700000-0xdfefffff could not be reserved
[    0.523714] system 00:0c: iomem range 0xffe00000-0xffffffff has been reserved
[    0.523717] system 00:0c: iomem range 0xffa00000-0xffbfffff has been reserved
[    0.523720] system 00:0c: iomem range 0xfec00000-0xfec0ffff could not be reserved
[    0.523724] system 00:0c: iomem range 0xfee00000-0xfee0ffff has been reserved
[    0.523727] system 00:0c: iomem range 0xfed20000-0xfed8ffff has been reserved
[    0.523730] system 00:0c: iomem range 0xfeda0000-0xfeda3fff has been reserved
[    0.523733] system 00:0c: iomem range 0xfeda4000-0xfeda4fff has been reserved
[    0.523737] system 00:0c: iomem range 0xfeda5000-0xfeda5fff has been reserved
[    0.523740] system 00:0c: iomem range 0xfeda6000-0xfeda6fff has been reserved
[    0.523743] system 00:0c: iomem range 0xfed18000-0xfed1bfff has been reserved
[    0.523746] system 00:0c: iomem range 0xf8000000-0xfbffffff has been reserved
[    0.528479] AppArmor: AppArmor Filesystem Enabled
[    0.528557] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:09
[    0.528562] pci 0000:00:1c.0:   IO window: 0xd000-0xdfff
[    0.528569] pci 0000:00:1c.0:   MEM window: 0xfe800000-0xfe8fffff
[    0.528575] pci 0000:00:1c.0:   PREFETCH window: disabled
[    0.528581] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:0b
[    0.528584] pci 0000:00:1c.1:   IO window: disabled
[    0.528591] pci 0000:00:1c.1:   MEM window: 0xfe700000-0xfe7fffff
[    0.528597] pci 0000:00:1c.1:   PREFETCH window: disabled
[    0.528603] pci 0000:00:1c.4: PCI bridge, secondary bus 0000:0c
[    0.528607] pci 0000:00:1c.4:   IO window: 0xc000-0xcfff
[    0.528614] pci 0000:00:1c.4:   MEM window: 0xfe400000-0xfe6fffff
[    0.528621] pci 0000:00:1c.4:   PREFETCH window: 0x000000f0000000-0x000000f01fffff
[    0.528631] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:02
[    0.528633] pci 0000:00:1e.0:   IO window: disabled
[    0.528640] pci 0000:00:1e.0:   MEM window: 0xfe300000-0xfe3fffff
[    0.528646] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.528665]   alloc irq_desc for 16 on node 0
[    0.528667]   alloc kstat_irqs on node 0
[    0.528675] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.528682] pci 0000:00:1c.0: setting latency timer to 64
[    0.528692]   alloc irq_desc for 17 on node 0
[    0.528694]   alloc kstat_irqs on node 0
[    0.528698] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.528704] pci 0000:00:1c.1: setting latency timer to 64
[    0.528714] pci 0000:00:1c.4: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.528720] pci 0000:00:1c.4: setting latency timer to 64
[    0.528730] pci 0000:00:1e.0: setting latency timer to 64
[    0.528736] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.528740] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]
[    0.528743] pci_bus 0000:09: resource 0 io:  [0xd000-0xdfff]
[    0.528745] pci_bus 0000:09: resource 1 mem: [0xfe800000-0xfe8fffff]
[    0.528748] pci_bus 0000:0b: resource 1 mem: [0xfe700000-0xfe7fffff]
[    0.528751] pci_bus 0000:0c: resource 0 io:  [0xc000-0xcfff]
[    0.528754] pci_bus 0000:0c: resource 1 mem: [0xfe400000-0xfe6fffff]
[    0.528757] pci_bus 0000:0c: resource 2 pref mem [0xf0000000-0xf01fffff]
[    0.528760] pci_bus 0000:02: resource 1 mem: [0xfe300000-0xfe3fffff]
[    0.528762] pci_bus 0000:02: resource 3 io:  [0x00-0xffff]
[    0.528765] pci_bus 0000:02: resource 4 mem: [0x000000-0xffffffffffffffff]
[    0.528812] NET: Registered protocol family 2
[    0.529030] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.530786] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.536852] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.537584] TCP: Hash tables configured (established 524288 bind 65536)
[    0.537588] TCP reno registered
[    0.537744] NET: Registered protocol family 1
[    0.537843] Trying to unpack rootfs image as initramfs...
[    0.761225] Freeing initrd memory: 7928k freed
[    0.766702] Simple Boot Flag at 0x79 set to 0x1
[    0.766945] Scanning for low memory corruption every 60 seconds
[    0.767129] audit: initializing netlink socket (disabled)
[    0.767151] type=2000 audit(1259932921.760:1): initialized
[    0.778865] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.780543] VFS: Disk quotas dquot_6.5.2
[    0.780612] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.781305] fuse init (API version 7.12)
[    0.781405] msgmni has been set to 7906
[    0.781658] alg: No test for stdrng (krng)
[    0.781675] io scheduler noop registered
[    0.781678] io scheduler anticipatory registered
[    0.781680] io scheduler deadline registered
[    0.781734] io scheduler cfq registered (default)
[    0.781750] pci 0000:00:02.0: Boot video device
[    0.782124]   alloc irq_desc for 24 on node 0
[    0.782127]   alloc kstat_irqs on node 0
[    0.782142] pcieport-driver 0000:00:1c.0: irq 24 for MSI/MSI-X
[    0.782155] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    0.782368]   alloc irq_desc for 25 on node 0
[    0.782371]   alloc kstat_irqs on node 0
[    0.782381] pcieport-driver 0000:00:1c.1: irq 25 for MSI/MSI-X
[    0.782394] pcieport-driver 0000:00:1c.1: setting latency timer to 64
[    0.782608]   alloc irq_desc for 26 on node 0
[    0.782610]   alloc kstat_irqs on node 0
[    0.782621] pcieport-driver 0000:00:1c.4: irq 26 for MSI/MSI-X
[    0.782634] pcieport-driver 0000:00:1c.4: setting latency timer to 64
[    0.782765] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.782882] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.783075] ACPI: AC Adapter [AC] (on-line)
[    0.783162] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    0.784017] ACPI: Lid Switch [LID]
[    0.784081] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.784088] ACPI: Power Button [PBTN]
[    0.784139] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    0.784143] ACPI: Sleep Button [SBTN]
[    0.784896] ACPI: SSDT 00000000df66e538 00244 (v01  PmRef  Cpu0Ist 00003000 INTL 20050624)
[    0.785430] ACPI: SSDT 00000000df66dece 005E5 (v01  PmRef  Cpu0Cst 00003001 INTL 20050624)
[    0.785843] Monitor-Mwait will be used to enter C-1 state
[    0.785880] Monitor-Mwait will be used to enter C-2 state
[    0.785905] Monitor-Mwait will be used to enter C-3 state
[    0.785914] Marking TSC unstable due to TSC halts in idle
[    0.785937] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    0.785967] processor LNXCPU:00: registered as cooling_device0
[    0.785972] ACPI: Processor [CPU0] (supports 8 throttling states)
[    0.786383] ACPI: SSDT 00000000df66e77c 000C4 (v01  PmRef  Cpu1Ist 00003000 INTL 20050624)
[    0.786733] ACPI: SSDT 00000000df66e4b3 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20050624)
[    0.787281] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    0.787306] processor LNXCPU:01: registered as cooling_device1
[    0.787311] ACPI: Processor [CPU1] (supports 8 throttling states)
[    0.789420] thermal LNXTHERM:01: registered as thermal_zone0
[    0.789429] ACPI: Thermal Zone [THM] (35 C)
[    0.790773] Linux agpgart interface v0.103
[    0.790786] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.792234] brd: module loaded
[    0.792811] loop: module loaded
[    0.792913] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    0.810202] ata_piix 0000:00:1f.1: version 2.13
[    0.810220] ata_piix 0000:00:1f.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.810272] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.823751] ACPI: Battery Slot [BAT0] (battery present)
[    0.823805] scsi0 : ata_piix
[    0.823928] scsi1 : ata_piix
[    0.824619] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x6fa0 irq 14
[    0.824623] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x6fa8 irq 15
[    0.824706] ata2: port disabled. ignoring.
[    0.824900] ata_piix 0000:00:1f.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.824907] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    0.980065] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.980294] scsi2 : ata_piix
[    0.980371] scsi3 : ata_piix
[    0.981063] ata3: SATA max UDMA/133 cmd 0x6eb0 ctl 0x6eb8 bmdma 0x6ee0 irq 17
[    0.981072] ata4: SATA max UDMA/133 cmd 0x6ec0 ctl 0x6ec8 bmdma 0x6ee8 irq 17
[    0.982086] Fixed MDIO Bus: probed
[    0.982127] PPP generic driver version 2.4.2
[    0.982261] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.982341]   alloc irq_desc for 22 on node 0
[    0.982344]   alloc kstat_irqs on node 0
[    0.982352] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    0.982389] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    0.982394] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    0.982468] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    0.986399] ehci_hcd 0000:00:1a.7: debug port 1
[    0.986407] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    0.986425] ehci_hcd 0000:00:1a.7: irq 22, io mem 0xfed1c400
[    1.010026] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    1.010106] usb usb1: configuration #1 chosen from 1 choice
[    1.010146] hub 1-0:1.0: USB hub found
[    1.010158] hub 1-0:1.0: 4 ports detected
[    1.010272]   alloc irq_desc for 20 on node 0
[    1.010275]   alloc kstat_irqs on node 0
[    1.010280] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    1.010295] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    1.010300] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    1.010345] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    1.014261] ehci_hcd 0000:00:1d.7: debug port 1
[    1.014269] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    1.014284] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xfed1c000
[    1.022911] ata1.00: ATAPI: PBDS DVD+/-RW DS-8W1P, BD1B, max UDMA/33
[    1.030016] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    1.030085] usb usb2: configuration #1 chosen from 1 choice
[    1.030120] hub 2-0:1.0: USB hub found
[    1.030128] hub 2-0:1.0: 6 ports detected
[    1.030213] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.030236] uhci_hcd: USB Universal Host Controller Interface driver
[    1.030368] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    1.030379] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    1.030383] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    1.030434] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    1.030465] uhci_hcd 0000:00:1a.0: irq 20, io base 0x00006f20
[    1.030560] usb usb3: configuration #1 chosen from 1 choice
[    1.030590] hub 3-0:1.0: USB hub found
[    1.030599] hub 3-0:1.0: 2 ports detected
[    1.030702]   alloc irq_desc for 21 on node 0
[    1.030705]   alloc kstat_irqs on node 0
[    1.030711] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    1.030719] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    1.030723] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    1.030762] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    1.030800] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00006f00
[    1.030894] usb usb4: configuration #1 chosen from 1 choice
[    1.030924] hub 4-0:1.0: USB hub found
[    1.030931] hub 4-0:1.0: 2 ports detected
[    1.031032] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    1.031040] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.031045] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    1.031084] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    1.031115] uhci_hcd 0000:00:1d.0: irq 20, io base 0x00006f80
[    1.031207] usb usb5: configuration #1 chosen from 1 choice
[    1.031237] hub 5-0:1.0: USB hub found
[    1.031245] hub 5-0:1.0: 2 ports detected
[    1.031339] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    1.031347] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    1.031351] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    1.031398] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    1.031429] uhci_hcd 0000:00:1d.1: irq 21, io base 0x00006f60
[    1.031519] usb usb6: configuration #1 chosen from 1 choice
[    1.031551] hub 6-0:1.0: USB hub found
[    1.031558] hub 6-0:1.0: 2 ports detected
[    1.031654] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    1.031663] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    1.031667] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    1.031704] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    1.031735] uhci_hcd 0000:00:1d.2: irq 22, io base 0x00006f40
[    1.031835] usb usb7: configuration #1 chosen from 1 choice
[    1.031869] hub 7-0:1.0: USB hub found
[    1.031883] hub 7-0:1.0: 2 ports detected
[    1.032014] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.050016] i8042.c: Detected active multiplexing controller, rev 1.1.
[    1.061898] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.061905] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    1.061909] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    1.061912] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    1.061916] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    1.062003] mice: PS/2 mouse device common for all mice
[    1.062133] rtc_cmos 00:04: RTC can wake from S4
[    1.062183] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    1.062219] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    1.062347] device-mapper: uevent: version 1.0.3
[    1.062591] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    1.062708] device-mapper: multipath: version 1.1.0 loaded
[    1.062716] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.062970] cpuidle: using governor ladder
[    1.063111] cpuidle: using governor menu
[    1.063593] TCP cubic registered
[    1.063746] NET: Registered protocol family 10
[    1.064254] lo: Disabled Privacy Extensions
[    1.064592] NET: Registered protocol family 17
[    1.064617] Bluetooth: L2CAP ver 2.13
[    1.064620] Bluetooth: L2CAP socket layer initialized
[    1.064624] Bluetooth: SCO (Voice Link) ver 0.6
[    1.064627] Bluetooth: SCO socket layer initialized
[    1.064668] Bluetooth: RFCOMM TTY layer initialized
[    1.064671] Bluetooth: RFCOMM socket layer initialized
[    1.064673] Bluetooth: RFCOMM ver 1.11
[    1.065395] PM: Resume from disk failed.
[    1.065417] registered taskstats version 1
[    1.065583]   Magic number: 5:537:381
[    1.065727] rtc_cmos 00:04: setting system clock to 2009-12-04 13:22:02 UTC (1259932922)
[    1.065731] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.065733] EDD information not available.
[    1.082872] ata1.00: configured for UDMA/33
[    1.087208] scsi 0:0:0:0: CD-ROM            PBDS     DVD+-RW DS-8W1P  BD1B PQ: 0 ANSI: 5
[    1.087335] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    1.098358] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    1.098362] Uniform CD-ROM driver Revision: 3.20
[    1.098478] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    1.098540] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    1.500069] Clocksource tsc unstable (delta = -347283543 ns)
[    1.690131] ata4.00: SATA link down (SStatus 0 SControl 300)
[    1.690155] ata4.01: SATA link down (SStatus 0 SControl 0)
[    1.850160] ata3.00: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.850180] ata3.01: SATA link down (SStatus 0 SControl 300)
[    1.912674] ata3.00: ATA-8: WDC WD3200BEVT-00ZCT0, 11.01A11, max UDMA/133
[    1.912678] ata3.00: 625142448 sectors, multi 8: LBA48 NCQ (depth 0/32)
[    1.951640] ata3.00: configured for UDMA/133
[    1.951756] scsi 2:0:0:0: Direct-Access     ATA      WDC WD3200BEVT-0 11.0 PQ: 0 ANSI: 5
[    1.951896] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    1.951938] sd 2:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    1.951991] sd 2:0:0:0: [sda] Write Protect is off
[    1.951994] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.952021] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.952163]  sda: sda1 sda2 < sda5 > sda3
[    1.987815] sd 2:0:0:0: [sda] Attached SCSI disk
[    1.987858] Freeing unused kernel memory: 660k freed
[    1.988139] Write protecting the kernel read-only data: 7584k
[    2.120896] agpgart-intel 0000:00:00.0: Intel 965GM Chipset
[    2.121317] agpgart-intel 0000:00:00.0: detected 7676K stolen memory
[    2.124774] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xe0000000
[    2.139570] sky2 driver version 1.23
[    2.150575] sky2 0000:09:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.150596] sky2 0000:09:00.0: setting latency timer to 64
[    2.150669] sky2 0000:09:00.0: Yukon-2 FE+ chip revision 0
[    2.150786]   alloc irq_desc for 27 on node 0
[    2.150788]   alloc kstat_irqs on node 0
[    2.150809] sky2 0000:09:00.0: irq 27 for MSI/MSI-X
[    2.151807] sky2 eth0: addr 00:1d:09:50:aa:d5
[    2.171793] ohci1394 0000:02:09.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.241265] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[16]  MMIO=[fe3ff800-fe3fffff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    2.267558] [drm] Initialized drm 1.1.0 20060810
[    2.283021] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.283030] i915 0000:00:02.0: setting latency timer to 64
[    2.301335]   alloc irq_desc for 28 on node 0
[    2.301340]   alloc kstat_irqs on node 0
[    2.301351] i915 0000:00:02.0: irq 28 for MSI/MSI-X
[    2.404233] integrated sync not supported
[    2.882195] integrated sync not supported
[    3.281867] [drm] TV-16: set mode NTSC 480i 0
[    3.423448] [drm] fb0: inteldrmfb frame buffer device
[    3.436564] acpi device:31: registered as cooling_device2
[    3.436997] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:2e/input/input5
[    3.437050] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[    3.437119] ACPI Warning: \_SB_.PCI0.VID2._DOD: Return Package has no elements (empty) 20090521 nspredef-434
[    3.437205] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:33/input/input6
[    3.437242] ACPI: Video Device [VID2] (multi-head: yes  rom: no  post: no)
[    3.437274] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    3.521469] [drm] LVDS-8: set mode 1280x800 19
[    3.622665] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[374fc0000948d1a1]
[    3.831393] Console: switching to colour frame buffer device 160x50
[    4.058546] xor: automatically using best checksumming function: generic_sse
[    4.100018]    generic_sse:  6331.200 MB/sec
[    4.100020] xor: using function: generic_sse (6331.200 MB/sec)
[    4.102657] device-mapper: dm-raid45: initialized v0.2594b
[    4.294238] PM: Starting manual resume from disk
[    4.294244] PM: Resume from partition 8:5
[    4.294246] PM: Checking hibernation image.
[    4.294492] PM: Resume from disk failed.
[    4.325351] EXT4-fs (sda1): barriers enabled
[    4.344692] kjournald2 starting: pid 422, dev sda1:8, commit interval 5 seconds
[    4.344723] EXT4-fs (sda1): delayed allocation enabled
[    4.344727] EXT4-fs: file extents enabled
[    4.345219] EXT4-fs: mballoc enabled
[    4.345239] EXT4-fs (sda1): mounted filesystem with ordered data mode
[    4.942600] type=1505 audit(1259932926.376:2): operation="profile_load" pid=445 name=/usr/share/gdm/guest-session/Xsession
[    4.945753] type=1505 audit(1259932926.376:3): operation="profile_load" pid=446 name=/sbin/dhclient3
[    4.946600] type=1505 audit(1259932926.376:4): operation="profile_load" pid=446 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    4.947066] type=1505 audit(1259932926.376:5): operation="profile_load" pid=446 name=/usr/lib/connman/scripts/dhclient-script
[    4.982691] type=1505 audit(1259932926.416:6): operation="profile_load" pid=447 name=/usr/bin/evince
[    4.996529] type=1505 audit(1259932926.426:7): operation="profile_load" pid=447 name=/usr/bin/evince-previewer
[    5.004708] type=1505 audit(1259932926.436:8): operation="profile_load" pid=447 name=/usr/bin/evince-thumbnailer
[    5.021920] type=1505 audit(1259932926.446:9): operation="profile_load" pid=449 name=/usr/lib/cups/backend/cups-pdf
[    5.022918] type=1505 audit(1259932926.456:10): operation="profile_load" pid=449 name=/usr/sbin/cupsd
[   16.242803] udev: starting version 147
[   16.317064] Adding 4000176k swap on /dev/sda5.  Priority:-1 extents:1 across:4000176k 
[   16.492751] sdhci: Secure Digital Host Controller Interface driver
[   16.492755] sdhci: Copyright(c) Pierre Ossman
[   16.494267] sdhci-pci 0000:02:09.1: SDHCI controller found [1180:0822] (rev 22)
[   16.494295]   alloc irq_desc for 18 on node 0
[   16.494297]   alloc kstat_irqs on node 0
[   16.494307] sdhci-pci 0000:02:09.1: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[   16.496474] Registered led device: mmc0::
[   16.497526] mmc0: SDHCI controller on PCI [0000:02:09.1] using DMA
[   16.499935] lib80211: common routines for IEEE802.11 drivers
[   16.499939] lib80211_crypt: registered algorithm 'NULL'
[   16.504771] wl: module license 'MIXED/Proprietary' taints kernel.
[   16.504776] Disabling lock debugging due to kernel taint
[   16.514290] ricoh-mmc: Ricoh MMC Controller disabling driver
[   16.514294] ricoh-mmc: Copyright(c) Philip Langdale
[   16.516060] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   16.521124] lp: driver loaded but no devices found
[   16.521565] wl 0000:0b:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   16.521581] wl 0000:0b:00.0: setting latency timer to 64
[   16.531291] ip_tables: (C) 2000-2006 Netfilter Core Team
[   16.551043] input: Dell WMI hotkeys as /devices/virtual/input/input7
[   16.554814] ricoh-mmc: Ricoh MMC controller found at 0000:02:09.2 [1180:0843] (rev 12)
[   16.554845] ricoh-mmc: Controller is now disabled.
[   16.584486] lib80211_crypt: registered algorithm 'TKIP'
[   16.584684] eth1: Broadcom BCM4315 802.11 Wireless Controller 5.10.91.9
[   16.589662] EXT4-fs (sda1): internal journal on sda1:8
[   16.599976] udev: renamed network interface eth1 to eth2
[   16.660459] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   16.660556] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   17.090939] input: PS/2 Mouse as /devices/platform/i8042/serio2/input/input8
[   17.117143] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio2/input/input9
[   17.205337] EXT4-fs (sda3): barriers enabled
[   17.220998] kjournald2 starting: pid 839, dev sda3:8, commit interval 5 seconds
[   17.221404] EXT4-fs (sda3): internal journal on sda3:8
[   17.221409] EXT4-fs (sda3): delayed allocation enabled
[   17.221412] EXT4-fs: file extents enabled
[   17.241552] EXT4-fs: mballoc enabled
[   17.241578] EXT4-fs (sda3): mounted filesystem with ordered data mode
[   17.869903] __ratelimit: 3 callbacks suppressed
[   17.869907] type=1505 audit(1259932939.294:12): operation="profile_replace" pid=1000 name=/usr/share/gdm/guest-session/Xsession
[   17.870023] hda-intel: azx_get_response timeout, switching to polling mode: last cmd=0x20af000e
[   17.870483] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input10
[   17.882095] type=1505 audit(1259932939.314:13): operation="profile_replace" pid=1009 name=/sbin/dhclient3
[   17.882932] type=1505 audit(1259932939.314:14): operation="profile_replace" pid=1009 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   17.883405] type=1505 audit(1259932939.314:15): operation="profile_replace" pid=1009 name=/usr/lib/connman/scripts/dhclient-script
[   17.888394] type=1505 audit(1259932939.314:16): operation="profile_replace" pid=1010 name=/usr/bin/evince
[   17.903784] type=1505 audit(1259932939.334:17): operation="profile_replace" pid=1010 name=/usr/bin/evince-previewer
[   17.912199] type=1505 audit(1259932939.344:18): operation="profile_replace" pid=1010 name=/usr/bin/evince-thumbnailer
[   17.935963] type=1505 audit(1259932939.364:19): operation="profile_replace" pid=1023 name=/usr/lib/cups/backend/cups-pdf
[   17.936947] type=1505 audit(1259932939.364:20): operation="profile_replace" pid=1023 name=/usr/sbin/cupsd
[   17.940269] type=1505 audit(1259932939.374:21): operation="profile_replace" pid=1024 name=/usr/sbin/tcpdump
[   17.998178] sky2 eth0: enabling interface
[   17.998738] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   18.475476] input: HDA Intel Mic at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   18.475575] input: HDA Intel HP Out at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[   18.475648] input: HDA Intel HP Out at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input13
[   18.732578] integrated sync not supported
[   18.824374] [drm] TV-16: set mode NTSC 480i 0
[   18.993397] [drm] TV-16: set mode NTSC 480i 0
[   19.243605] integrated sync not supported
[   19.328576] [drm] TV-16: set mode NTSC 480i 0
[   19.497489] [drm] TV-16: set mode NTSC 480i 0
[   20.192930] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   20.192935] vboxdrv: Warning: 2.6.31+ kernel detected. Most likely the hwardware performance
[   20.192937] vboxdrv: counter framework which can generate NMIs is active. You have to prevent
[   20.192938] vboxdrv: the usage of hardware performance counters by
[   20.192939] vboxdrv:   echo 2 > /proc/sys/kernel/perf_counter_paranoid
[   20.192944] vboxdrv: Found 2 processor cores.
[   20.193031] VBoxDrv: dbg - g_abExecMemory=ffffffffa03ab480
[   20.193062] vboxdrv: fAsync=0 offMin=0x1d4 offMax=0x14b8
[   20.193118] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   20.193120] vboxdrv: Successfully loaded version 3.0.12 (interface 0x00110000).
[   20.400369] VBoxNetFlt: dbg - g_abExecMemory=ffffffffa054a220
[   20.403626] VBoxNetAdp: dbg - g_abExecMemory=ffffffffa0563b20
[   20.469178] ppdev: user-space parallel port driver
[   21.554909] integrated sync not supported
[   21.638699] [drm] TV-16: set mode NTSC 480i 0
[   21.805263] [drm] TV-16: set mode NTSC 480i 0
[   22.062288] integrated sync not supported
[   22.145935] [drm] TV-16: set mode NTSC 480i 0
[   22.312565] [drm] TV-16: set mode NTSC 480i 0
[   22.572259] integrated sync not supported
[   22.655919] [drm] TV-16: set mode NTSC 480i 0
[   22.823924] [drm] TV-16: set mode NTSC 480i 0
[   28.790039] eth2: no IPv6 routers present
[   35.962392] integrated sync not supported
[   36.045912] [drm] TV-16: set mode NTSC 480i 0
[   36.213819] [drm] TV-16: set mode NTSC 480i 0
[   36.472336] integrated sync not supported
[   36.557262] [drm] TV-16: set mode NTSC 480i 0
[   36.725834] [drm] TV-16: set mode NTSC 480i 0
[   36.982258] integrated sync not supported
[   37.066000] [drm] TV-16: set mode NTSC 480i 0
[   37.232977] [drm] TV-16: set mode NTSC 480i 0
[   38.382443] integrated sync not supported
[   38.465978] [drm] TV-16: set mode NTSC 480i 0
[   38.637827] [drm] TV-16: set mode NTSC 480i 0
[  556.932627] CE: hpet increasing min_delta_ns to 15000 nsec
[ 9407.130106] sky2 eth0: disabling interface
[ 9407.845553] PM: Syncing filesystems ... done.
[ 9407.849777] PM: Preparing system for mem sleep
[ 9407.849782] Freezing user space processes ... (elapsed 0.00 seconds) done.
[ 9407.850889] Freezing remaining freezable tasks ... (elapsed 0.00 seconds) done.
[ 9407.850996] PM: Entering mem sleep
[ 9407.851012] Suspending console(s) (use no_console_suspend to debug)
[ 9407.851378] sd 2:0:0:0: [sda] Synchronizing SCSI cache
[ 9407.874363] sd 2:0:0:0: [sda] Stopping disk
[ 9408.714650] sdhci-pci 0000:02:09.1: PME# disabled
[ 9408.714660] sdhci-pci 0000:02:09.1: PCI INT B disabled
[ 9408.750306] wl 0000:0b:00.0: PCI INT A disabled
[ 9408.770200] sky2 0000:09:00.0: PME# disabled
[ 9408.790262] ata_piix 0000:00:1f.2: PCI INT B disabled
[ 9408.810141] ata2: port disabled. ignoring.
[ 9408.810192] ata_piix 0000:00:1f.1: PCI INT A disabled
[ 9408.810205] ehci_hcd 0000:00:1d.7: PCI INT A disabled
[ 9408.810215] uhci_hcd 0000:00:1d.2: PCI INT C disabled
[ 9408.810224] uhci_hcd 0000:00:1d.1: PCI INT B disabled
[ 9408.810233] uhci_hcd 0000:00:1d.0: PCI INT A disabled
[ 9409.340096] HDA Intel 0000:00:1b.0: PCI INT A disabled
[ 9409.360068] ehci_hcd 0000:00:1a.7: PCI INT C disabled
[ 9409.360077] uhci_hcd 0000:00:1a.1: PCI INT B disabled
[ 9409.360086] uhci_hcd 0000:00:1a.0: PCI INT A disabled
[ 9409.422663] PM: suspend devices took 1.570 seconds
[ 9409.422821] ricoh-mmc: Suspending.
[ 9409.422832] ricoh-mmc: Controller is now re-enabled.
[ 9409.423063] ehci_hcd 0000:00:1d.7: PME# disabled
[ 9409.442847] ehci_hcd 0000:00:1a.7: PME# disabled
[ 9409.465919] ACPI: Preparing to enter system sleep state S3
[ 9409.469438] Disabling non-boot CPUs ...
[ 9409.471752] CPU 1 is now offline
[ 9409.471755] SMP alternatives: switching to UP code
[ 9409.479468] CPU0 attaching NULL sched-domain.
[ 9409.479473] CPU1 attaching NULL sched-domain.
[ 9409.479485] CPU0 attaching NULL sched-domain.
[ 9409.479763] CPU1 is down
[ 9409.479817] Extended CMOS year: 2000
[ 9409.479817] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[ 9409.479817] Back to C!
[ 9409.479817] CPU0: Thermal LVT vector (0xfa) already installed
[ 9409.479817] Extended CMOS year: 2000
[ 9409.479817] Enabling non-boot CPUs ...
[ 9409.480156] SMP alternatives: switching to SMP code
[ 9409.487395] Booting processor 1 APIC 0x1 ip 0x6000
[ 9409.479263] Initializing CPU#1
[ 9409.479263] Calibrating delay using timer specific routine.. 3457.98 BogoMIPS (lpj=17289940)
[ 9409.479263] CPU: L1 I cache: 32K, L1 D cache: 32K
[ 9409.479263] CPU: L2 cache: 1024K
[ 9409.479263] CPU 1/0x1 -> Node 0
[ 9409.479263] CPU: Physical Processor ID: 0
[ 9409.479263] CPU: Processor Core ID: 1
[ 9409.479263] mce: CPU supports 6 MCE banks
[ 9409.479263] CPU1: Thermal monitoring enabled (TM2)
[ 9409.479263] x86 PAT enabled: cpu 1, old 0x7040600070406, new 0x7010600070106
[ 9409.641622] CPU1: Intel(R) Pentium(R) Dual  CPU  T2370  @ 1.73GHz stepping 0d
[ 9409.641695] CPU0 attaching NULL sched-domain.
[ 9409.650027] Switched to high resolution mode on CPU 1
[ 9409.680038] CPU0 attaching sched-domain:
[ 9409.680042]  domain 0: span 0-1 level MC
[ 9409.680044]   groups: 0 1
[ 9409.680049] CPU1 attaching sched-domain:
[ 9409.680052]  domain 0: span 0-1 level MC
[ 9409.680054]   groups: 1 0
[ 9409.682520] CPU1 is up
[ 9409.682523] ACPI: Waking up from system sleep state S3
[ 9409.693143] i915 0000:00:02.0: restoring config space at offset 0xf (was 0x100, writing 0x10b)
[ 9409.693153] i915 0000:00:02.0: restoring config space at offset 0x8 (was 0x1, writing 0xefe9)
[ 9409.693158] i915 0000:00:02.0: restoring config space at offset 0x6 (was 0xc, writing 0xe000000c)
[ 9409.693163] i915 0000:00:02.0: restoring config space at offset 0x4 (was 0x4, writing 0xfea00004)
[ 9409.693169] i915 0000:00:02.0: restoring config space at offset 0x1 (was 0x900000, writing 0x900407)
[ 9409.693201] pci 0000:00:02.1: restoring config space at offset 0x4 (was 0x4, writing 0xfeb00004)
[ 9409.693206] pci 0000:00:02.1: restoring config space at offset 0x1 (was 0x900000, writing 0x900007)
[ 9409.693219] uhci_hcd 0000:00:1a.0: restoring config space at offset 0xf (was 0x100, writing 0x10a)
[ 9409.693235] uhci_hcd 0000:00:1a.0: restoring config space at offset 0x8 (was 0x1, writing 0x6f21)
[ 9409.693251] uhci_hcd 0000:00:1a.0: restoring config space at offset 0x1 (was 0x2800000, writing 0x2800001)
[ 9409.693265] uhci_hcd 0000:00:1a.1: restoring config space at offset 0xf (was 0x200, writing 0x209)
[ 9409.693281] uhci_hcd 0000:00:1a.1: restoring config space at offset 0x8 (was 0x1, writing 0x6f01)
[ 9409.693297] uhci_hcd 0000:00:1a.1: restoring config space at offset 0x1 (was 0x2800000, writing 0x2800001)
[ 9409.693320] ehci_hcd 0000:00:1a.7: restoring config space at offset 0xf (was 0x300, writing 0x307)
[ 9409.693344] ehci_hcd 0000:00:1a.7: restoring config space at offset 0x4 (was 0x0, writing 0xfed1c400)
[ 9409.693353] ehci_hcd 0000:00:1a.7: restoring config space at offset 0x1 (was 0x2900000, writing 0x2900102)
[ 9409.693374] ehci_hcd 0000:00:1a.7: PME# disabled
[ 9409.693397] HDA Intel 0000:00:1b.0: restoring config space at offset 0xf (was 0x100, writing 0x109)
[ 9409.693420] HDA Intel 0000:00:1b.0: restoring config space at offset 0x4 (was 0xfebfc004, writing 0xfe9fc004)
[ 9409.693426] HDA Intel 0000:00:1b.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[ 9409.693434] HDA Intel 0000:00:1b.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100102)
[ 9409.693471] pcieport-driver 0000:00:1c.0: restoring config space at offset 0xf (was 0x100, writing 0x20100)
[ 9409.693486] pcieport-driver 0000:00:1c.0: restoring config space at offset 0x9 (was 0x10001, writing 0x1fff1)
[ 9409.693492] pcieport-driver 0000:00:1c.0: restoring config space at offset 0x8 (was 0x0, writing 0xfe80fe80)
[ 9409.693498] pcieport-driver 0000:00:1c.0: restoring config space at offset 0x7 (was 0x0, writing 0xd0d0)
[ 9409.693505] pcieport-driver 0000:00:1c.0: restoring config space at offset 0x6 (was 0x0, writing 0x90900)
[ 9409.693514] pcieport-driver 0000:00:1c.0: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
[ 9409.693522] pcieport-driver 0000:00:1c.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100407)
[ 9409.693578] pcieport-driver 0000:00:1c.1: restoring config space at offset 0xf (was 0x200, writing 0x20200)
[ 9409.693593] pcieport-driver 0000:00:1c.1: restoring config space at offset 0x9 (was 0x10001, writing 0x1fff1)
[ 9409.693599] pcieport-driver 0000:00:1c.1: restoring config space at offset 0x8 (was 0x0, writing 0xfe70fe70)
[ 9409.693605] pcieport-driver 0000:00:1c.1: restoring config space at offset 0x7 (was 0x0, writing 0xf0)
[ 9409.693611] pcieport-driver 0000:00:1c.1: restoring config space at offset 0x6 (was 0x0, writing 0xb0b00)
[ 9409.693621] pcieport-driver 0000:00:1c.1: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
[ 9409.693629] pcieport-driver 0000:00:1c.1: restoring config space at offset 0x1 (was 0x100000, writing 0x100507)
[ 9409.693685] pcieport-driver 0000:00:1c.4: restoring config space at offset 0xf (was 0x100, writing 0x20100)
[ 9409.693699] pcieport-driver 0000:00:1c.4: restoring config space at offset 0x9 (was 0x10001, writing 0xf011f001)
[ 9409.693705] pcieport-driver 0000:00:1c.4: restoring config space at offset 0x8 (was 0x0, writing 0xfe60fe40)
[ 9409.693712] pcieport-driver 0000:00:1c.4: restoring config space at offset 0x7 (was 0x0, writing 0xc0c0)
[ 9409.693718] pcieport-driver 0000:00:1c.4: restoring config space at offset 0x6 (was 0x0, writing 0xd0c00)
[ 9409.693727] pcieport-driver 0000:00:1c.4: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
[ 9409.693735] pcieport-driver 0000:00:1c.4: restoring config space at offset 0x1 (was 0x100000, writing 0x100407)
[ 9409.693802] uhci_hcd 0000:00:1d.0: restoring config space at offset 0x1 (was 0x2800005, writing 0x2800001)
[ 9409.693814] uhci_hcd 0000:00:1d.1: restoring config space at offset 0xf (was 0x200, writing 0x209)
[ 9409.693831] uhci_hcd 0000:00:1d.1: restoring config space at offset 0x8 (was 0x1, writing 0x6f61)
[ 9409.693847] uhci_hcd 0000:00:1d.1: restoring config space at offset 0x1 (was 0x2800000, writing 0x2800001)
[ 9409.693859] uhci_hcd 0000:00:1d.2: restoring config space at offset 0xf (was 0x300, writing 0x307)
[ 9409.693876] uhci_hcd 0000:00:1d.2: restoring config space at offset 0x8 (was 0x1, writing 0x6f41)
[ 9409.693892] uhci_hcd 0000:00:1d.2: restoring config space at offset 0x1 (was 0x2800000, writing 0x2800001)
[ 9409.693938] ehci_hcd 0000:00:1d.7: restoring config space at offset 0x1 (was 0x2900106, writing 0x2900102)
[ 9409.693959] ehci_hcd 0000:00:1d.7: PME# disabled
[ 9409.693981] pci 0000:00:1e.0: restoring config space at offset 0x9 (was 0x100f1, writing 0x1fff1)
[ 9409.693987] pci 0000:00:1e.0: restoring config space at offset 0x8 (was 0x30, writing 0xfe30fe30)
[ 9409.693993] pci 0000:00:1e.0: restoring config space at offset 0x7 (was 0x2280e0f0, writing 0x228000f0)
[ 9409.694008] pci 0000:00:1e.0: restoring config space at offset 0x1 (was 0x100007, writing 0x100107)
[ 9409.694063] pci 0000:00:1f.0: restoring config space at offset 0x1 (was 0x2100007, writing 0x2100107)
[ 9409.694084] ata_piix 0000:00:1f.1: restoring config space at offset 0xf (was 0x100, writing 0x10b)
[ 9409.694126] ata_piix 0000:00:1f.2: restoring config space at offset 0xf (was 0x200, writing 0x20a)
[ 9409.694140] ata_piix 0000:00:1f.2: restoring config space at offset 0x9 (was 0x1, writing 0xeff1)
[ 9409.694158] ata_piix 0000:00:1f.2: restoring config space at offset 0x1 (was 0x2b00000, writing 0x2b00007)
[ 9409.694175] pci 0000:00:1f.3: restoring config space at offset 0xf (was 0x200, writing 0x20a)
[ 9409.694198] pci 0000:00:1f.3: restoring config space at offset 0x4 (was 0x0, writing 0xfe9fbf00)
[ 9409.694207] pci 0000:00:1f.3: restoring config space at offset 0x1 (was 0x2800001, writing 0x2800103)
[ 9409.694260] sky2 0000:09:00.0: restoring config space at offset 0xf (was 0x100, writing 0x10b)
[ 9409.694289] sky2 0000:09:00.0: restoring config space at offset 0x6 (was 0x1, writing 0xde01)
[ 9409.694299] sky2 0000:09:00.0: restoring config space at offset 0x4 (was 0x4, writing 0xfe8fc004)
[ 9409.694307] sky2 0000:09:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[ 9409.694317] sky2 0000:09:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100507)
[ 9409.694479] wl 0000:0b:00.0: restoring config space at offset 0xf (was 0x100, writing 0x10b)
[ 9409.694543] wl 0000:0b:00.0: restoring config space at offset 0x4 (was 0x4, writing 0xfe7fc004)
[ 9409.694555] wl 0000:0b:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[ 9409.694573] wl 0000:0b:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100106)
[ 9409.694650] ohci1394 0000:02:09.0: restoring config space at offset 0xf (was 0x4020100, writing 0x402010b)
[ 9409.694675] ohci1394 0000:02:09.0: restoring config space at offset 0x3 (was 0x800000, writing 0x804010)
[ 9409.694684] ohci1394 0000:02:09.0: restoring config space at offset 0x1 (was 0x2100000, writing 0x2100106)
[ 9409.694709] sdhci-pci 0000:02:09.1: restoring config space at offset 0xf (was 0x200, writing 0x205)
[ 9409.694733] sdhci-pci 0000:02:09.1: restoring config space at offset 0x4 (was 0x0, writing 0xfe3ff400)
[ 9409.694740] sdhci-pci 0000:02:09.1: restoring config space at offset 0x3 (was 0x800000, writing 0x804010)
[ 9409.694748] sdhci-pci 0000:02:09.1: restoring config space at offset 0x1 (was 0x2100000, writing 0x2100106)
[ 9409.694774] ricoh-mmc 0000:02:09.2: restoring config space at offset 0xf (was 0x200, writing 0x205)
[ 9409.694798] ricoh-mmc 0000:02:09.2: restoring config space at offset 0x4 (was 0x0, writing 0xfe3ff500)
[ 9409.694805] ricoh-mmc 0000:02:09.2: restoring config space at offset 0x3 (was 0x800000, writing 0x804010)
[ 9409.694813] ricoh-mmc 0000:02:09.2: restoring config space at offset 0x1 (was 0x2100000, writing 0x2100106)
[ 9409.694827] ricoh-mmc: Resuming.
[ 9409.694837] ricoh-mmc: Controller is now disabled.
[ 9409.694850] pci 0000:02:09.3: restoring config space at offset 0xf (was 0x200, writing 0x205)
[ 9409.694874] pci 0000:02:09.3: restoring config space at offset 0x4 (was 0x0, writing 0xfe3ff700)
[ 9409.694881] pci 0000:02:09.3: restoring config space at offset 0x3 (was 0x800000, writing 0x804010)
[ 9409.694889] pci 0000:02:09.3: restoring config space at offset 0x1 (was 0x2100000, writing 0x2100106)
[ 9409.748777] i915 0000:00:02.0: setting latency timer to 64
[ 9409.824174] [drm] LVDS-8: set mode 1280x800 19
[ 9409.857049] pci 0000:00:02.1: PME# disabled
[ 9409.857062] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[ 9409.857070] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[ 9409.857097] usb usb3: root hub lost power or was reset
[ 9409.857120] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[ 9409.857128] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[ 9409.857155] usb usb4: root hub lost power or was reset
[ 9409.857177] ehci_hcd 0000:00:1a.7: PME# disabled
[ 9409.857183] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[ 9409.857190] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[ 9409.857203] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[ 9409.857210] HDA Intel 0000:00:1b.0: setting latency timer to 64
[ 9409.857242] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[ 9409.857249] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[ 9409.857278] usb usb5: root hub lost power or was reset
[ 9409.857299] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[ 9409.857306] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[ 9409.857333] usb usb6: root hub lost power or was reset
[ 9409.857354] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[ 9409.857361] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[ 9409.857388] usb usb7: root hub lost power or was reset
[ 9409.857410] ehci_hcd 0000:00:1d.7: PME# disabled
[ 9409.857415] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[ 9409.857422] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[ 9409.857436] pci 0000:00:1e.0: setting latency timer to 64
[ 9409.857448] ata_piix 0000:00:1f.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 9409.857454] ata_piix 0000:00:1f.1: setting latency timer to 64
[ 9409.857514] ata2: port disabled. ignoring.
[ 9409.857528] ata_piix 0000:00:1f.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[ 9409.857534] ata_piix 0000:00:1f.2: setting latency timer to 64
[ 9409.857554] sky2 0000:09:00.0: PME# disabled
[ 9409.857657] wl 0000:0b:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 9409.857669] wl 0000:0b:00.0: setting latency timer to 64
[ 9409.858845] ata1.00: _GTF evaluation failed (AE 0x1001)
[ 9409.858988] ata3.00: _GTF evaluation failed (AE 0x1001)
[ 9409.912098] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[16]  MMIO=[fe3ff800-fe3fffff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[ 9409.918127] sdhci-pci 0000:02:09.1: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[ 9409.919155] pci 0000:02:09.3: PME# disabled
[ 9409.919162] pci 0000:02:09.4: PME# disabled
[ 9410.014451] sd 2:0:0:0: [sda] Starting disk
[ 9410.072888] ata1.00: configured for UDMA/33
[ 9410.552655] ata4.00: SATA link down (SStatus 4 SControl 300)
[ 9410.552678] ata4.01: SATA link down (SStatus 0 SControl 0)
[ 9412.932669] ata3.00: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[ 9412.932688] ata3.01: SATA link down (SStatus 4 SControl 300)
[ 9412.990993] ata3.00: configured for UDMA/133
[ 9412.995277] PM: resume devices took 3.280 seconds
[ 9412.995321] PM: Finishing wakeup.
[ 9412.995323] Restarting tasks ... done.
[ 9413.145804] sky2 eth0: enabling interface
[ 9413.146475] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 9414.938646] input: PS/2 Mouse as /devices/platform/i8042/serio2/input/input14
[ 9414.966627] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio2/input/input15
[ 9417.820037] eth2: no IPv6 routers present
[ 9642.500102] usb 2-4: new high speed USB device using ehci_hcd and address 2
[ 9642.847586] usb 2-4: configuration #1 chosen from 1 choice
```

---

### Post by OffAxis on 2009-12-04
does it show up in 
```
lsusb
```
?

---

### Post by theozzlives on 2009-12-04
Yes, as "ADS Technologies". I just installed it on my roomates XP box to see if it works. It's great for XP, but not for Ubuntu and 7.

EDIT: Won't work in a VirtualBox either.

---

### Post by theozzlives on 2009-12-05
Well, I resized my partitions and put XP on dual boot on my laptop. I'd rather use Ubuntu for my TV and be done with XP forever! If anyone can help it would be appreciated (I'll mail you a free CD of Ubuntu, hehe).

---

### Post by theozzlives on 2009-12-07
bump

---

### Post by theozzlives on 2009-12-08
Someone in this world has to have this tuner besides me!
BUMP!

---

### Post by theozzlives on 2009-12-09
bump

---

### Post by theozzlives on 2009-12-11
bump

---

### Post by ukripper on 2009-12-11
can you post output of ```
lsusb
```
and for god sake calm down on bumps..:)

---

### Post by theozzlives on 2009-12-12
> **ukripper said:**
> can you post output of ```
lsusb
```
and for god sake calm down on bumps..:)

I waited 24 hrs between bumps, and I'm just frustrated because I spent money for this tuner and I can't use it! For what good it'll do, here's lsusb:
```
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 06e1:a371 ADS Technologies, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

---

### Post by frenchn00b on 2009-12-13
> **theozzlives said:**
> bump

post the type of the video/tuner u have:
+ 
 ```
xawtv -hwscan
```
```

lsusb

lspci
```

your dmesg is empty :( no relevant info

I knew that there is a hardware database for linux with drivers, but dont remember it.

google this:
06e1:a371 

and gives us news. you can bump, dont worry, its good cuz hoping you get issue solved.

---

### Post by frenchn00b on 2009-12-13
> **theozzlives said:**
> I can't get TV time to recognize my ADS USB TV Tuner. It says "no input device" (or something like that). Any ideas?

[http://ubuntuforums.org/showthread.php?p=8490233#post8490233](http://ubuntuforums.org/showthread.php?p=8490233#post8490233)

---

### Post by theozzlives on 2009-12-13
```
ozzie@ozzie-laptop:~$ xawtv -hwscan
This is xawtv-3.95.dfsg.1, running on Linux/x86_64 (2.6.31-16-generic)
looking for available devices
port 67-82
    type : Xvideo, image scaler
    name : Intel(R) Textured Video

```

lsusb is on post #12, lspci won't do any good on a USB device. It's an ADS Technologies MiniTVUSB. I'm about ready to buy a PCI card and sell this to an XP user.

---

### Post by frenchn00b on 2009-12-13
> **theozzlives said:**
> ```
ozzie@ozzie-laptop:~$ xawtv -hwscan
This is xawtv-3.95.dfsg.1, running on Linux/x86_64 (2.6.31-16-generic)
looking for available devices
port 67-82
    type : Xvideo, image scaler
    name : Intel(R) Textured Video

```

lsusb is on post #12, lspci won't do any good on a USB device. It's an ADS Technologies MiniTVUSB. I'm about ready to buy a PCI card and sell this to an XP user.

that's so sad that linux cannot handle hardware. Did you explain your story to some coders of the video for linux, or tvtime, maybe they can help you.

try linuxquestions.org
Ubuntu and skill levels of the admins or moderators is not so high compared to other forums, or they are few. Maybe other forums can give you more chances

---

### Post by ukripper on 2009-12-14
can you post output of this command, so that we can see what chipset is there in your card:
```
sudo lshw -C multimedia
```

---

### Post by theozzlives on 2009-12-14
> **ukripper said:**
> can you post output of this command, so that we can see what chipset is there in your card:
```
sudo lshw -C multimedia
```

It wasn't a card and I gave up, sold it, and got a card on the way. So stay tuned, TV cards and I have never gotten along.

---

### Post by frenchn00b on 2009-12-14
> **ukripper said:**
> can you post output of this command, so that we can see what chipset is there in your card:
```
sudo lshw -C multimedia
```

you see that's typically why people will never use linux.

People wont screw up their life just doing computer, and loosing time. 
Windows xp works for everybody.

That's sad for linux. HardwareLinux = Health_destruction_n_time :( 
thats a reality, he sold his card

> **theozzlives said:**
> It wasn't a card and I gave up, sold it, and got a card on the way. So stay tuned, TV cards and I have never gotten along.


Well, how many days did I loose installing new hardware on linux, lot. I dont wish it any anyone.

---

### Post by ukripper on 2009-12-14
> **frenchn00b said:**
> you see that's typically why people will never use linux.


People are using Linux

> **frenchn00b said:**
> 
People wont screw up their life just doing computer, and loosing time. 

Not entirely true for everyone.
> **frenchn00b said:**
> 
Windows xp works for everybody.

Again, one's personal experience doesn't give the insight of what others might be going through. Pushing own personal experience on "everybody" is as absurd as saying "I rule the world".

---

### Post by theozzlives on 2009-12-17
Well, I got my PCI tuner card and TV Time still don't work. No errors, just black where the "tv screen" is.

So here goes:
dmesg
```
[    0.000000] BIOS EBDA/lowmem at: 0009f000/0009f000
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.28-17-generic (buildd@crested) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #58-Ubuntu SMP Tue Dec 1 21:27:25 UTC 2009 (Ubuntu 2.6.28-17.58-generic)
[    0.000000] Command line: root=UUID=15e4b3cc-0e42-4073-913b-1efbccfb57d0 ro quiet splash 
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e6000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003bfc0000 (usable)
[    0.000000]  BIOS-e820: 000000003bfc0000 - 000000003bfce000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003bfce000 - 000000003bff0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003bff0000 - 000000003bffe000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fef00000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] DMI present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working it around.
[    0.000000] last_pfn = 0x3bfc0 max_arch_pfn = 0x3ffffffff
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009f000 (usable)
[    0.000000]  modified: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e6000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000003bfc0000 (usable)
[    0.000000]  modified: 000000003bfc0000 - 000000003bfce000 (ACPI data)
[    0.000000]  modified: 000000003bfce000 - 000000003bff0000 (ACPI NVS)
[    0.000000]  modified: 000000003bff0000 - 000000003bffe000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fef00000 (reserved)
[    0.000000]  modified: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] init_memory_mapping: 0000000000000000-000000003bfc0000
[    0.000000]  0000000000 - 003be00000 page 2M
[    0.000000]  003be00000 - 003bfc0000 page 4k
[    0.000000] kernel direct mapping tables up to 3bfc0000 @ 10000-13000
[    0.000000] last_map_addr: 3bfc0000 end: 3bfc0000
[    0.000000] RAMDISK: 3785d000 - 37fefe77
[    0.000000] ACPI: RSDP 000FA200, 0014 (r0 ACPIAM)
[    0.000000] ACPI: RSDT 3BFC0000, 0038 (r1 040909 RSDT1129 20090409 MSFT       97)
[    0.000000] ACPI: FACP 3BFC0200, 0084 (r1 040909 FACP1129 20090409 MSFT       97)
[    0.000000] ACPI: DSDT 3BFC04A0, 48A6 (r1  1ADKR 1ADKR017       17 INTL 20051117)
[    0.000000] ACPI: FACS 3BFCE000, 0040
[    0.000000] ACPI: APIC 3BFC0390, 0080 (r1 040909 APIC1129 20090409 MSFT       97)
[    0.000000] ACPI: MCFG 3BFC0410, 003C (r1 040909 OEMMCFG  20090409 MSFT       97)
[    0.000000] ACPI: WDRT 3BFC0450, 0047 (r1 040909 NV-WDRT  20090409 MSFT       97)
[    0.000000] ACPI: OEMB 3BFCE040, 0072 (r1 040909 OEMB1129 20090409 MSFT       97)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] (6 early reservations) ==> bootmem [0000000000 - 003bfc0000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
[    0.000000]   #2 [0000200000 - 0000b7cbb0]    TEXT DATA BSS ==> [0000200000 - 0000b7cbb0]
[    0.000000]   #3 [003785d000 - 0037fefe77]          RAMDISK ==> [003785d000 - 0037fefe77]
[    0.000000]   #4 [000009f000 - 0000100000]    BIOS reserved ==> [000009f000 - 0000100000]
[    0.000000]   #5 [0000010000 - 0000011000]          PGTABLE ==> [0000010000 - 0000011000]
[    0.000000] found SMP MP-table at [ffff8800000ff780] 000ff780
[    0.000000]  [ffffe20000000000-ffffe20000dfffff] PMD -> [ffff880001200000-ffff880001ffffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00100000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0003bfc0
[    0.000000] On node 0 totalpages: 245583
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 2531 pages reserved
[    0.000000]   DMA zone: 1396 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 3304 pages used for memmap
[    0.000000]   DMA32 zone: 238296 pages, LIFO batch:31
[    0.000000]   Normal zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] Nvidia board detected. Ignoring ACPI timer override.
[    0.000000] If you got timer trouble try acpi_use_timer_override
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 0, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: BIOS IRQ0 pin2 override ignored.
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e6000
[    0.000000] PM: Registered nosave memory: 00000000000e6000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 3bffe000:c2c02000)
[    0.000000] PERCPU: Allocating 69632 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 4, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 239692
[    0.000000] Kernel command line: root=UUID=15e4b3cc-0e42-4073-913b-1efbccfb57d0 ro quiet splash 
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2913.117 MHz processor.
[    0.004000] spurious 8259A interrupt: IRQ7.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.004000] Inode-cache hash table entries: 65536 (order: 7, 524288 bytes)
[    0.004000] allocated 10485760 bytes of page_cgroup
[    0.004000] please try cgroup_disable=memory option if you don't want
[    0.004000] Scanning for low memory corruption every 60 seconds
[    0.004000] Checking aperture...
[    0.004000] No AGP bridge found
[    0.004000] Node 0: aperture @ 9922000000 size 32 MB
[    0.004000] Aperture beyond 4GB. Ignoring.
[    0.004000] Memory: 937644k/982784k available (4750k kernel code, 452k absent, 43972k reserved, 2523k data, 536k init)
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.004009] Calibrating delay loop (skipped), value calculated using timer frequency.. 5826.22 BogoMIPS (lpj=11652452)
[    0.004025] Security Framework initialized
[    0.004030] SELinux:  Disabled at boot.
[    0.004043] AppArmor: AppArmor initialized
[    0.004049] Mount-cache hash table entries: 256
[    0.004160] Initializing cgroup subsys ns
[    0.004163] Initializing cgroup subsys cpuacct
[    0.004165] Initializing cgroup subsys memory
[    0.004167] Initializing cgroup subsys freezer
[    0.004178] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004180] CPU: L2 Cache: 1024K (64 bytes/line)
[    0.004182] tseg: 0000000000
[    0.004194] CPU: Physical Processor ID: 0
[    0.004195] CPU: Processor Core ID: 0
[    0.004197] using C1E aware idle routine
[    0.005362] ACPI: Core revision 20080926
[    0.006899] ACPI: Checking initramfs for custom DSDT
[    0.193770] Setting APIC routing to flat
[    0.194273] ..TIMER: vector=0x30 apic1=0 pin1=0 apic2=-1 pin2=-1
[    0.233966] CPU0: AMD Athlon(tm) II X2 245 Processor stepping 02
[    0.236001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 5827.29 BogoMIPS (lpj=11654592)
[    0.004000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004000] CPU: L2 Cache: 1024K (64 bytes/line)
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.320208] CPU1: AMD Athlon(tm) II X2 245 Processor stepping 02
[    0.320214] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.324030] Brought up 2 CPUs
[    0.324032] Total of 2 processors activated (11653.52 BogoMIPS).
[    0.324118] CPU0 attaching sched-domain:
[    0.324119]  domain 0: span 0-1 level CPU
[    0.324121]   groups: 0 1
[    0.324125] CPU1 attaching sched-domain:
[    0.324126]  domain 0: span 0-1 level CPU
[    0.324127]   groups: 1 0
[    0.324167] net_namespace: 1400 bytes
[    0.324167] Booting paravirtualized kernel on bare hardware
[    0.324228] Time: 13:35:15  Date: 12/17/09
[    0.324228] regulator: core version 0.5
[    0.324228] NET: Registered protocol family 16
[    0.324228] node 0 link 0: io port [1000, ffffff]
[    0.324228] TOM: 0000000040000000 aka 1024M
[    0.324228] Fam 10h mmconf [e0000000, efffffff]
[    0.324228] node 0 link 0: mmio [e0000000, efffffff] ==> none
[    0.324228] node 0 link 0: mmio [a0000, bffff]
[    0.324228] node 0 link 0: mmio [40000000, fe0bffff] ==> [40000000, dfffffff] and [f0000000, fe0bffff]
[    0.324228] bus: [00,07] on node 0 link 0
[    0.324228] bus: 00 index 0 io port: [0, ffff]
[    0.324228] bus: 00 index 1 mmio: [a0000, bffff]
[    0.324228] bus: 00 index 2 mmio: [40000000, dfffffff]
[    0.324228] bus: 00 index 3 mmio: [f0000000, fcffffffff]
[    0.324228] ACPI: bus type pci registered
[    0.324228] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.324228] PCI: Not using MMCONFIG.
[    0.324228] PCI: Using configuration type 1 for base access
[    0.324228] PCI: Using configuration type 1 for extended access
[    0.324585] ACPI: EC: Look up EC in DSDT
[    0.332318] ACPI: Interpreter enabled
[    0.332320] ACPI: (supports S0 S1 S3 S4 S5)
[    0.332332] ACPI: Using IOAPIC for interrupt routing
[    0.332372] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.335979] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
[    0.344900] PCI: Using MMCONFIG at e0000000 - efffffff
[    0.350147] ACPI: No dock devices found.
[    0.350187] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.350325] pci 0000:00:01.0: reg 10 io port: [0x4f00-0x4fff]
[    0.350359] pci 0000:00:01.1: reg 10 io port: [0x4900-0x493f]
[    0.350368] pci 0000:00:01.1: reg 20 io port: [0x4d00-0x4d3f]
[    0.350371] pci 0000:00:01.1: reg 24 io port: [0x4e00-0x4e3f]
[    0.350380] pci 0000:00:01.1: PME# supported from D3hot D3cold
[    0.350385] pci 0000:00:01.1: PME# disabled
[    0.350428] pci 0000:00:01.3: reg 10 32bit mmio: [0xfec80000-0xfecfffff]
[    0.350498] pci 0000:00:02.0: reg 10 32bit mmio: [0xdfe7f000-0xdfe7ffff]
[    0.350513] pci 0000:00:02.0: supports D1 D2
[    0.350514] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.350517] pci 0000:00:02.0: PME# disabled
[    0.350535] pci 0000:00:02.1: reg 10 32bit mmio: [0xdfe7ec00-0xdfe7ecff]
[    0.350552] pci 0000:00:02.1: supports D1 D2
[    0.350554] pci 0000:00:02.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.350556] pci 0000:00:02.1: PME# disabled
[    0.350604] pci 0000:00:05.0: reg 10 32bit mmio: [0xdfe78000-0xdfe7bfff]
[    0.350620] pci 0000:00:05.0: PME# supported from D3hot D3cold
[    0.350622] pci 0000:00:05.0: PME# disabled
[    0.350650] pci 0000:00:06.0: reg 20 io port: [0xfff0-0xffff]
[    0.350678] pci 0000:00:07.0: reg 10 32bit mmio: [0xdfe7d000-0xdfe7dfff]
[    0.350681] pci 0000:00:07.0: reg 14 io port: [0xde00-0xde07]
[    0.350692] pci 0000:00:07.0: supports D1 D2
[    0.350694] pci 0000:00:07.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.350697] pci 0000:00:07.0: PME# disabled
[    0.350715] pci 0000:00:08.0: reg 10 io port: [0xdd80-0xdd87]
[    0.350718] pci 0000:00:08.0: reg 14 io port: [0xdd00-0xdd03]
[    0.350720] pci 0000:00:08.0: reg 18 io port: [0xdc00-0xdc07]
[    0.350723] pci 0000:00:08.0: reg 1c io port: [0xdb80-0xdb83]
[    0.350726] pci 0000:00:08.0: reg 20 io port: [0xdb00-0xdb0f]
[    0.350728] pci 0000:00:08.0: reg 24 32bit mmio: [0xdfe7c000-0xdfe7cfff]
[    0.350749] pci 0000:00:08.1: reg 10 io port: [0xda80-0xda87]
[    0.350752] pci 0000:00:08.1: reg 14 io port: [0xda00-0xda03]
[    0.350755] pci 0000:00:08.1: reg 18 io port: [0xd980-0xd987]
[    0.350757] pci 0000:00:08.1: reg 1c io port: [0xd900-0xd903]
[    0.350760] pci 0000:00:08.1: reg 20 io port: [0xd880-0xd88f]
[    0.350763] pci 0000:00:08.1: reg 24 32bit mmio: [0xdfe77000-0xdfe77fff]
[    0.350791] pci 0000:00:09.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.350793] pci 0000:00:09.0: PME# disabled
[    0.350813] pci 0000:00:0b.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.350814] pci 0000:00:0b.0: PME# disabled
[    0.350833] pci 0000:00:0c.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.350835] pci 0000:00:0c.0: PME# disabled
[    0.350848] pci 0000:00:0d.0: reg 10 32bit mmio: [0xde000000-0xdeffffff]
[    0.350852] pci 0000:00:0d.0: reg 14 64bit mmio: [0xc0000000-0xcfffffff]
[    0.350856] pci 0000:00:0d.0: reg 1c 64bit mmio: [0xdd000000-0xddffffff]
[    0.350860] pci 0000:00:0d.0: reg 30 32bit mmio: [0xdfe40000-0xdfe5ffff]
[    0.350965] pci 0000:01:09.0: reg 20 io port: [0xef80-0xef9f]
[    0.350977] pci 0000:01:09.0: supports D1 D2
[    0.350978] pci 0000:01:09.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.350981] pci 0000:01:09.0: PME# disabled
[    0.351013] pci 0000:01:09.1: reg 20 io port: [0xef00-0xef1f]
[    0.351025] pci 0000:01:09.1: supports D1 D2
[    0.351027] pci 0000:01:09.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.351029] pci 0000:01:09.1: PME# disabled
[    0.351050] pci 0000:01:09.2: reg 10 32bit mmio: [0xdffffc00-0xdffffcff]
[    0.351074] pci 0000:01:09.2: supports D1 D2
[    0.351075] pci 0000:01:09.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.351078] pci 0000:01:09.2: PME# disabled
[    0.351104] pci 0000:01:0a.0: reg 10 32bit mmio: [0xdffff800-0xdffffbff]
[    0.351128] pci 0000:01:0a.0: supports D1 D2
[    0.351150] pci 0000:00:04.0: transparent bridge
[    0.351152] pci 0000:00:04.0: bridge io port: [0xe000-0xefff]
[    0.351154] pci 0000:00:04.0: bridge 32bit mmio: [0xdff00000-0xdfffffff]
[    0.351256] bus 00 -> node 0
[    0.351260] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.351436] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.351537] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR10._PRT]
[    0.351610] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR11._PRT]
[    0.351682] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR12._PRT]
[    0.357183] ACPI: PCI Interrupt Link [LNKA] (IRQs 16 17 18 19) *0, disabled.
[    0.357360] ACPI: PCI Interrupt Link [LNKB] (IRQs 16 17 18 19) *5
[    0.357534] ACPI: PCI Interrupt Link [LNKC] (IRQs 16 17 18 19) *10
[    0.357709] ACPI: PCI Interrupt Link [LNKD] (IRQs 16 17 18 19) *10
[    0.357879] ACPI: PCI Interrupt Link [LNEA] (IRQs 16 17 18 19) *0, disabled.
[    0.358048] ACPI: PCI Interrupt Link [LNEB] (IRQs 16 17 18 19) *0, disabled.
[    0.358219] ACPI: PCI Interrupt Link [LNEC] (IRQs 16 17 18 19) *0, disabled.
[    0.358389] ACPI: PCI Interrupt Link [LNED] (IRQs 16 17 18 19) *0, disabled.
[    0.358562] ACPI: PCI Interrupt Link [LUB0] (IRQs 20 21 22 23) *10
[    0.358737] ACPI: PCI Interrupt Link [LUB2] (IRQs 20 21 22 23) *11
[    0.358910] ACPI: PCI Interrupt Link [LMAC] (IRQs 20 21 22 23) *10
[    0.359085] ACPI: PCI Interrupt Link [LAZA] (IRQs 20 21 22 23) *5
[    0.359258] ACPI: PCI Interrupt Link [LMC9] (IRQs 20 21 22 23) *10
[    0.359431] ACPI: PCI Interrupt Link [LSMB] (IRQs 20 21 22 23) *11
[    0.359605] ACPI: PCI Interrupt Link [LPMU] (IRQs 20 21 22 23) *5
[    0.359778] ACPI: PCI Interrupt Link [LSA0] (IRQs 20 21 22 23) *10
[    0.359953] ACPI: PCI Interrupt Link [LSA1] (IRQs 20 21 22 23) *11
[    0.360158] ACPI: PCI Interrupt Link [LATA] (IRQs 20 21 22 23) *0, disabled.
[    0.360256] ACPI Warning (tbutils-0217): Incorrect checksum in table [OEMB] - 35, should be 28 [20080926]
[    0.360270] ACPI: WMI: Mapper loaded
[    0.360340] SCSI subsystem initialized
[    0.360340] libata version 3.00 loaded.
[    0.360340] usbcore: registered new interface driver usbfs
[    0.360340] usbcore: registered new interface driver hub
[    0.360340] usbcore: registered new device driver usb
[    0.360340] PCI: Using ACPI for IRQ routing
[    0.376028] Bluetooth: Core ver 2.13
[    0.376064] NET: Registered protocol family 31
[    0.376064] Bluetooth: HCI device and connection manager initialized
[    0.376064] Bluetooth: HCI socket layer initialized
[    0.376064] NET: Registered protocol family 8
[    0.376064] NET: Registered protocol family 20
[    0.376064] NetLabel: Initializing
[    0.376064] NetLabel:  domain hash size = 128
[    0.376064] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.376064] NetLabel:  unlabeled traffic allowed by default
[    0.376217] AppArmor: AppArmor Filesystem Enabled
[    0.388035] pnp: PnP ACPI init
[    0.388051] ACPI: bus type pnp registered
[    0.392085] pnp: PnP ACPI: found 13 devices
[    0.392086] ACPI: ACPI bus type pnp unregistered
[    0.392095] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
[    0.392097] system 00:08: ioport range 0x800-0x80f has been reserved
[    0.392098] system 00:08: ioport range 0x4000-0x407f has been reserved
[    0.392100] system 00:08: ioport range 0x4080-0x40ff has been reserved
[    0.392101] system 00:08: ioport range 0x4400-0x447f has been reserved
[    0.392103] system 00:08: ioport range 0x4480-0x44ff has been reserved
[    0.392104] system 00:08: ioport range 0x4800-0x487f has been reserved
[    0.392106] system 00:08: ioport range 0x4880-0x48ff has been reserved
[    0.392107] system 00:08: ioport range 0x4c00-0x4c7f has been reserved
[    0.392109] system 00:08: ioport range 0x4c80-0x4cff has been reserved
[    0.392111] system 00:08: iomem range 0xfec80000-0x1fd93ffff could not be reserved
[    0.392113] system 00:08: iomem range 0xfefe0000-0xfefe01ff has been reserved
[    0.392114] system 00:08: iomem range 0xfefe1000-0xfefe1fff has been reserved
[    0.392116] system 00:08: iomem range 0xfee01000-0xfeefffff has been reserved
[    0.392118] system 00:08: iomem range 0xffb80000-0xffffffff could not be reserved
[    0.392121] system 00:09: iomem range 0xfec00000-0xfec00fff has been reserved
[    0.392122] system 00:09: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.392125] system 00:0a: ioport range 0xa00-0xadf has been reserved
[    0.392127] system 00:0a: ioport range 0xae0-0xaef has been reserved
[    0.392129] system 00:0b: iomem range 0xe0000000-0xefffffff has been reserved
[    0.392132] system 00:0c: iomem range 0x0-0x9ffff could not be reserved
[    0.392134] system 00:0c: iomem range 0xc0000-0xcffff has been reserved
[    0.392135] system 00:0c: iomem range 0xe0000-0xfffff could not be reserved
[    0.392137] system 00:0c: iomem range 0x100000-0x3fffffff could not be reserved
[    0.392138] system 00:0c: iomem range 0xfec00000-0xffffffff could not be reserved
[    0.396764] pci 0000:00:04.0: PCI bridge, secondary bus 0000:01
[    0.396766] pci 0000:00:04.0:   IO window: 0xe000-0xefff
[    0.396769] pci 0000:00:04.0:   MEM window: 0xdff00000-0xdfffffff
[    0.396771] pci 0000:00:04.0:   PREFETCH window: disabled
[    0.396774] pci 0000:00:09.0: PCI bridge, secondary bus 0000:02
[    0.396775] pci 0000:00:09.0:   IO window: disabled
[    0.396777] pci 0000:00:09.0:   MEM window: disabled
[    0.396779] pci 0000:00:09.0:   PREFETCH window: disabled
[    0.396781] pci 0000:00:0b.0: PCI bridge, secondary bus 0000:03
[    0.396782] pci 0000:00:0b.0:   IO window: disabled
[    0.396784] pci 0000:00:0b.0:   MEM window: disabled
[    0.396786] pci 0000:00:0b.0:   PREFETCH window: disabled
[    0.396788] pci 0000:00:0c.0: PCI bridge, secondary bus 0000:04
[    0.396789] pci 0000:00:0c.0:   IO window: disabled
[    0.396791] pci 0000:00:0c.0:   MEM window: disabled
[    0.396792] pci 0000:00:0c.0:   PREFETCH window: disabled
[    0.396798] pci 0000:00:04.0: setting latency timer to 64
[    0.396802] pci 0000:00:09.0: setting latency timer to 64
[    0.396805] pci 0000:00:0b.0: setting latency timer to 64
[    0.396808] pci 0000:00:0c.0: setting latency timer to 64
[    0.396810] bus: 00 index 0 io port: [0x00-0xffff]
[    0.396811] bus: 00 index 1 mmio: [0x000000-0xffffffffffffffff]
[    0.396813] bus: 01 index 0 io port: [0xe000-0xefff]
[    0.396814] bus: 01 index 1 mmio: [0xdff00000-0xdfffffff]
[    0.396815] bus: 01 index 2 mmio: [0x0-0x0]
[    0.396817] bus: 01 index 3 io port: [0x00-0xffff]
[    0.396818] bus: 01 index 4 mmio: [0x000000-0xffffffffffffffff]
[    0.396819] bus: 02 index 0 mmio: [0x0-0x0]
[    0.396820] bus: 02 index 1 mmio: [0x0-0x0]
[    0.396821] bus: 02 index 2 mmio: [0x0-0x0]
[    0.396822] bus: 02 index 3 mmio: [0x0-0x0]
[    0.396823] bus: 03 index 0 mmio: [0x0-0x0]
[    0.396824] bus: 03 index 1 mmio: [0x0-0x0]
[    0.396825] bus: 03 index 2 mmio: [0x0-0x0]
[    0.396826] bus: 03 index 3 mmio: [0x0-0x0]
[    0.396827] bus: 04 index 0 mmio: [0x0-0x0]
[    0.396828] bus: 04 index 1 mmio: [0x0-0x0]
[    0.396829] bus: 04 index 2 mmio: [0x0-0x0]
[    0.396830] bus: 04 index 3 mmio: [0x0-0x0]
[    0.396840] NET: Registered protocol family 2
[    0.432086] IP route cache hash table entries: 32768 (order: 6, 262144 bytes)
[    0.432271] TCP established hash table entries: 131072 (order: 9, 2097152 bytes)
[    0.432946] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.433345] TCP: Hash tables configured (established 131072 bind 65536)
[    0.433346] TCP reno registered
[    0.444112] NET: Registered protocol family 1
[    0.444189] checking if image is initramfs... it is
[    0.819688] Freeing initrd memory: 7755k freed
[    0.823094] audit: initializing netlink socket (disabled)
[    0.823110] type=2000 audit(1261056914.820:1): initialized
[    0.828123] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.828872] VFS: Disk quotas dquot_6.5.1
[    0.828902] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.829246] fuse init (API version 7.10)
[    0.829289] msgmni has been set to 1847
[    0.829403] alg: No test for stdrng (krng)
[    0.829413] io scheduler noop registered
[    0.829414] io scheduler anticipatory registered
[    0.829415] io scheduler deadline registered
[    0.829438] io scheduler cfq registered (default)
[    0.829466] pci 0000:00:00.0: Enabling HT MSI Mapping
[    0.860396] pci 0000:00:04.0: Enabling HT MSI Mapping
[    0.860412] pci 0000:00:05.0: Enabling HT MSI Mapping
[    0.860436] pci 0000:00:07.0: Enabling HT MSI Mapping
[    0.860448] pci 0000:00:08.0: Enabling HT MSI Mapping
[    0.860460] pci 0000:00:08.1: Enabling HT MSI Mapping
[    0.860473] pci 0000:00:09.0: Enabling HT MSI Mapping
[    0.860486] pci 0000:00:0b.0: Enabling HT MSI Mapping
[    0.860498] pci 0000:00:0c.0: Enabling HT MSI Mapping
[    0.860511] pci 0000:00:0d.0: Boot video device
[    0.864305] pcieport-driver 0000:00:09.0: setting latency timer to 64
[    0.864333] pcieport-driver 0000:00:09.0: found MSI capability
[    0.864346] pcieport-driver 0000:00:09.0: irq 2303 for MSI/MSI-X
[    0.864352] pci_express 0000:00:09.0:pcie00: allocate port service
[    0.864364] pci_express 0000:00:09.0:pcie03: allocate port service
[    0.864390] pcieport-driver 0000:00:0b.0: setting latency timer to 64
[    0.864408] pcieport-driver 0000:00:0b.0: found MSI capability
[    0.864418] pcieport-driver 0000:00:0b.0: irq 2302 for MSI/MSI-X
[    0.864422] pci_express 0000:00:0b.0:pcie00: allocate port service
[    0.864430] pci_express 0000:00:0b.0:pcie03: allocate port service
[    0.864455] pcieport-driver 0000:00:0c.0: setting latency timer to 64
[    0.864473] pcieport-driver 0000:00:0c.0: found MSI capability
[    0.864482] pcieport-driver 0000:00:0c.0: irq 2301 for MSI/MSI-X
[    0.864487] pci_express 0000:00:0c.0:pcie00: allocate port service
[    0.864495] pci_express 0000:00:0c.0:pcie03: allocate port service
[    0.864525] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.864530] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.864614] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    0.864615] ACPI: Power Button (FF) [PWRF]
[    0.864643] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.864651] ACPI: Power Button (CM) [PWRB]
[    0.864805] processor ACPI_CPU:00: registered as cooling_device0
[    0.864823] processor ACPI_CPU:01: registered as cooling_device1
[    0.892491] Linux agpgart interface v0.103
[    0.892499] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    0.892581] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.892762] 00:05: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.893157] brd: module loaded
[    0.893309] loop: module loaded
[    0.893346] Fixed MDIO Bus: probed
[    0.893349] PPP generic driver version 2.4.2
[    0.893383] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    0.893399] Driver 'sd' needs updating - please use bus_type methods
[    0.893404] Driver 'sr' needs updating - please use bus_type methods
[    0.893506] sata_nv 0000:00:08.0: version 3.5
[    0.893794] ACPI: PCI Interrupt Link [LSA0] enabled at IRQ 23
[    0.893803] sata_nv 0000:00:08.0: PCI INT A -> Link[LSA0] -> GSI 23 (level, low) -> IRQ 23
[    0.893846] sata_nv 0000:00:08.0: setting latency timer to 64
[    0.893928] scsi0 : sata_nv
[    0.893994] scsi1 : sata_nv
[    0.894079] ata1: SATA max UDMA/133 cmd 0xdd80 ctl 0xdd00 bmdma 0xdb00 irq 23
[    0.894081] ata2: SATA max UDMA/133 cmd 0xdc00 ctl 0xdb80 bmdma 0xdb08 irq 23
[    0.912341] Switched to high resolution mode on CPU 1
[    0.916103] Switched to high resolution mode on CPU 0
[    1.344558] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.352651] ata1.00: ATA-8: WDC WD800AAJS-60M0A0, 02.03E02, max UDMA/100
[    1.352654] ata1.00: 156301488 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.368661] ata1.00: configured for UDMA/100
[    1.690339] isa bounce pool size: 16 pages
[    1.690394] scsi 0:0:0:0: Direct-Access     ATA      WDC WD800AAJS-60 02.0 PQ: 0 ANSI: 5
[    1.690462] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[    1.690471] sd 0:0:0:0: [sda] Write Protect is off
[    1.690473] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.690484] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.690537] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors: (80.0 GB/74.5 GiB)
[    1.690544] sd 0:0:0:0: [sda] Write Protect is off
[    1.690545] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.690556] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.690558]  sda: sda1 sda2 < sda5 > sda3
[    1.717049] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.717089] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.717384] ACPI: PCI Interrupt Link [LSA1] enabled at IRQ 22
[    1.717393] sata_nv 0000:00:08.1: PCI INT B -> Link[LSA1] -> GSI 22 (level, low) -> IRQ 22
[    1.717422] sata_nv 0000:00:08.1: setting latency timer to 64
[    1.717504] scsi2 : sata_nv
[    1.717543] scsi3 : sata_nv
[    1.717627] ata3: SATA max UDMA/133 cmd 0xda80 ctl 0xda00 bmdma 0xd880 irq 22
[    1.717629] ata4: SATA max UDMA/133 cmd 0xd980 ctl 0xd900 bmdma 0xd888 irq 22
[    2.358383] pata_amd 0000:00:06.0: version 0.3.10
[    2.358414] pata_amd 0000:00:06.0: setting latency timer to 64
[    2.358504] scsi4 : pata_amd
[    2.358550] scsi5 : pata_amd
[    2.359442] ata5: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xfff0 irq 14
[    2.359444] ata6: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xfff8 irq 15
[    2.529230] ata5.00: ATA-5: WDC WD400BB-53AUA1, 18.20D18, max UDMA/100
[    2.529233] ata5.00: 78165360 sectors, multi 16: LBA 
[    2.529252] ata5.01: ATAPI: HL-DT-ST GCE-8487B, F109, max UDMA/33
[    2.529266] ata5: nv_mode_filter: 0x3f39f&0x3f01f->0x3f01f, BIOS=0x3f000 (0xc6c00000) ACPI=0x3f01f (20:60:0x15)
[    2.529269] ata5: nv_mode_filter: 0x739f&0x701f->0x701f, BIOS=0x7000 (0xc6c00000) ACPI=0x701f (20:60:0x15)
[    2.545204] ata5.00: configured for UDMA/100
[    2.576262] ata5.01: configured for UDMA/33
[    2.576518] ata6: port disabled. ignoring.
[    2.576587] scsi 4:0:0:0: Direct-Access     ATA      WDC WD400BB-53AU 18.2 PQ: 0 ANSI: 5
[    2.576656] sd 4:0:0:0: [sdb] 78165360 512-byte hardware sectors: (40.0 GB/37.2 GiB)
[    2.576664] sd 4:0:0:0: [sdb] Write Protect is off
[    2.576665] sd 4:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    2.576677] sd 4:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.576718] sd 4:0:0:0: [sdb] 78165360 512-byte hardware sectors: (40.0 GB/37.2 GiB)
[    2.576725] sd 4:0:0:0: [sdb] Write Protect is off
[    2.576726] sd 4:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    2.576737] sd 4:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.576740]  sdb: sdb1
[    2.597170] sd 4:0:0:0: [sdb] Attached SCSI disk
[    2.597204] sd 4:0:0:0: Attached scsi generic sg1 type 0
[    2.597489] scsi 4:0:1:0: CD-ROM            HL-DT-ST CD-RW GCE-8487B  F109 PQ: 0 ANSI: 5
[    2.599911] sr0: scsi3-mmc drive: 52x/48x writer cd/rw xa/form2 cdda tray
[    2.599914] Uniform CD-ROM driver Revision: 3.20
[    2.600012] sr 4:0:1:0: Attached scsi CD-ROM sr0
[    2.600046] sr 4:0:1:0: Attached scsi generic sg2 type 5
[    2.600289] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.600601] ACPI: PCI Interrupt Link [LUB2] enabled at IRQ 21
[    2.600610] ehci_hcd 0000:00:02.1: PCI INT B -> Link[LUB2] -> GSI 21 (level, low) -> IRQ 21
[    2.600624] ehci_hcd 0000:00:02.1: setting latency timer to 64
[    2.600626] ehci_hcd 0000:00:02.1: EHCI Host Controller
[    2.600661] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 1
[    2.600682] ehci_hcd 0000:00:02.1: debug port 1
[    2.600684] ehci_hcd 0000:00:02.1: cache line size of 64 is not supported
[    2.600701] ehci_hcd 0000:00:02.1: irq 21, io mem 0xdfe7ec00
[    2.612535] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00
[    2.612614] usb usb1: configuration #1 chosen from 1 choice
[    2.612629] hub 1-0:1.0: USB hub found
[    2.612635] hub 1-0:1.0: 10 ports detected
[    2.612993] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 19
[    2.613002] ehci_hcd 0000:01:09.2: PCI INT C -> Link[LNKD] -> GSI 19 (level, low) -> IRQ 19
[    2.613017] ehci_hcd 0000:01:09.2: EHCI Host Controller
[    2.613047] ehci_hcd 0000:01:09.2: new USB bus registered, assigned bus number 2
[    2.613085] ehci_hcd 0000:01:09.2: irq 19, io mem 0xdffffc00
[    2.624036] ehci_hcd 0000:01:09.2: USB 2.0 started, EHCI 1.00
[    2.624100] usb usb2: configuration #1 chosen from 1 choice
[    2.624119] hub 2-0:1.0: USB hub found
[    2.624125] hub 2-0:1.0: 4 ports detected
[    2.624191] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.624482] ACPI: PCI Interrupt Link [LUB0] enabled at IRQ 20
[    2.624491] ohci_hcd 0000:00:02.0: PCI INT A -> Link[LUB0] -> GSI 20 (level, low) -> IRQ 20
[    2.624518] ohci_hcd 0000:00:02.0: setting latency timer to 64
[    2.624521] ohci_hcd 0000:00:02.0: OHCI Host Controller
[    2.624549] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 3
[    2.624573] ohci_hcd 0000:00:02.0: irq 20, io mem 0xdfe7f000
[    2.682098] usb usb3: configuration #1 chosen from 1 choice
[    2.682114] hub 3-0:1.0: USB hub found
[    2.682121] hub 3-0:1.0: 10 ports detected
[    2.682192] uhci_hcd: USB Universal Host Controller Interface driver
[    2.682502] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 18
[    2.682511] uhci_hcd 0000:01:09.0: PCI INT A -> Link[LNKB] -> GSI 18 (level, low) -> IRQ 18
[    2.682518] uhci_hcd 0000:01:09.0: UHCI Host Controller
[    2.682547] uhci_hcd 0000:01:09.0: new USB bus registered, assigned bus number 4
[    2.682578] uhci_hcd 0000:01:09.0: irq 18, io base 0x0000ef80
[    2.682620] usb usb4: configuration #1 chosen from 1 choice
[    2.682632] hub 4-0:1.0: USB hub found
[    2.682636] hub 4-0:1.0: 2 ports detected
[    2.682921] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 17
[    2.682927] uhci_hcd 0000:01:09.1: PCI INT B -> Link[LNKC] -> GSI 17 (level, low) -> IRQ 17
[    2.682930] uhci_hcd 0000:01:09.1: UHCI Host Controller
[    2.682958] uhci_hcd 0000:01:09.1: new USB bus registered, assigned bus number 5
[    2.682984] uhci_hcd 0000:01:09.1: irq 17, io base 0x0000ef00
[    2.683022] usb usb5: configuration #1 chosen from 1 choice
[    2.683035] hub 5-0:1.0: USB hub found
[    2.683038] hub 5-0:1.0: 2 ports detected
[    2.683110] PNP: No PS/2 controller found. Probing ports directly.
[    2.685391] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.685394] serio: i8042 AUX port at 0x60,0x64 irq 12
[    2.696581] mice: PS/2 mouse device common for all mice
[    2.732616] rtc_cmos 00:02: RTC can wake from S4
[    2.732641] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    2.732675] rtc0: alarms up to one year, y3k, 114 bytes nvram
[    2.732731] device-mapper: uevent: version 1.0.3
[    2.732831] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
[    2.732897] device-mapper: multipath: version 1.0.5 loaded
[    2.732899] device-mapper: multipath round-robin: version 1.0.0 loaded
[    2.732979] cpuidle: using governor ladder
[    2.732980] cpuidle: using governor menu
[    2.733235] TCP cubic registered
[    2.733276] NET: Registered protocol family 10
[    2.733505] lo: Disabled Privacy Extensions
[    2.733667] NET: Registered protocol family 17
[    2.733679] Bluetooth: L2CAP ver 2.11
[    2.733680] Bluetooth: L2CAP socket layer initialized
[    2.733681] Bluetooth: SCO (Voice Link) ver 0.6
[    2.733682] Bluetooth: SCO socket layer initialized
[    2.733742] Bluetooth: RFCOMM socket layer initialized
[    2.733746] Bluetooth: RFCOMM TTY layer initialized
[    2.733747] Bluetooth: RFCOMM ver 1.10
[    2.733777] powernow-k8: Found 1 AMD Athlon(tm) II X2 245 Processor processors (2 cpu cores) (version 2.20.00)
[    2.733792] [Firmware Bug]: powernow-k8: Your BIOS does not provide ACPI _PSS objects in a way that Linux understands. Please report this to the Linux ACPI maintainers and complain to your BIOS vendor.
[    2.733881] [Firmware Bug]: powernow-k8: Your BIOS does not provide ACPI _PSS objects in a way that Linux understands. Please report this to the Linux ACPI maintainers and complain to your BIOS vendor.
[    2.734007] registered taskstats version 1
[    2.734099]   Magic number: 5:721:584
[    2.734177] rtc_cmos 00:02: setting system clock to 2009-12-17 13:35:17 UTC (1261056917)
[    2.734179] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.734180] EDD information not available.
[    2.734206] Freeing unused kernel memory: 536k freed
[    2.734367] Write protecting the kernel read-only data: 6688k
[    2.889170] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
[    2.889478] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 23
[    2.889481] forcedeth 0000:00:07.0: PCI INT A -> Link[LMAC] -> GSI 23 (level, low) -> IRQ 23
[    2.889485] forcedeth 0000:00:07.0: setting latency timer to 64
[    2.924514] usb 1-1: new high speed USB device using ehci_hcd and address 2
[    2.963916] Floppy drive(s): fd0 is 1.44M
[    2.979941] FDC 0 is a post-1991 82077
[    3.059973] usb 1-1: configuration #1 chosen from 1 choice
[    3.071105] Initializing USB Mass Storage driver...
[    3.072224] scsi6 : SCSI emulation for USB Mass Storage devices
[    3.072372] usbcore: registered new interface driver usb-storage
[    3.072374] USB Mass Storage support registered.
[    3.073077] usb-storage: device found at 2
[    3.073078] usb-storage: waiting for device to settle before scanning
[    3.408816] forcedeth 0000:00:07.0: ifname eth0, PHY OUI 0x732 @ 1, addr 00:24:21:a9:86:18
[    3.408819] forcedeth 0000:00:07.0: highdma pwrctl mgmt timirq lnktim msi desc-v3
[    3.473900] PM: Starting manual resume from disk
[    3.473902] PM: Resume from partition 8:5
[    3.473903] PM: Checking hibernation image.
[    3.474048] PM: Resume from disk failed.
[    3.492307] EXT4-fs: barriers enabled
[    3.501334] kjournald2 starting.  Commit interval 5 seconds
[    3.501351] EXT4-fs: delayed allocation enabled
[    3.501352] EXT4-fs: file extents enabled
[    3.501830] EXT4-fs: mballoc enabled
[    3.501834] EXT4-fs: mounted filesystem with ordered data mode.
[    3.536545] usb 3-2: new low speed USB device using ohci_hcd and address 2
[    3.749233] usb 3-2: configuration #1 chosen from 1 choice
[    4.052555] usb 3-4: new full speed USB device using ohci_hcd and address 3
[    4.264311] usb 3-4: configuration #1 chosen from 1 choice
[    4.270264] hub 3-4:1.0: USB hub found
[    4.273235] hub 3-4:1.0: 3 ports detected
[    4.570281] usb 3-4.1: new full speed USB device using ohci_hcd and address 4
[    4.680353] usb 3-4.1: configuration #1 chosen from 1 choice
[    6.776674] udev: starting version 141
[    6.968603] input: PC Speaker as /devices/platform/pcspkr/input/input3
[    7.102750] parport_pc 00:07: reported by Plug and Play ACPI
[    7.102795] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[    7.295743] ppdev: user-space parallel port driver
[    7.310889] usbcore: registered new interface driver hiddev
[    7.316779] input: Logitech Optical USB Mouse as /devices/pci0000:00/0000:00:02.0/usb3/3-2/3-2:1.0/input/input4
[    7.337422] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x4d00
[    7.337447] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x4e00
[    7.352688] generic-usb 0003:046D:C016.0001: input,hidraw0: USB HID v1.10 Mouse [Logitech Optical USB Mouse] on usb-0000:00:02.0-2/input0
[    7.357881] input: Dell Dell USB Keyboard as /devices/pci0000:00/0000:00:02.0/usb3/3-4/3-4.1/3-4.1:1.0/input/input5
[    7.388668] generic-usb 0003:413C:2010.0002: input,hidraw1: USB HID v1.10 Keyboard [Dell Dell USB Keyboard] on usb-0000:00:02.0-4.1/input0
[    7.398678] input: Dell Dell USB Keyboard as /devices/pci0000:00/0000:00:02.0/usb3/3-4/3-4.1/3-4.1:1.1/input/input6
[    7.424668] generic-usb 0003:413C:2010.0003: input,hidraw2: USB HID v1.10 Device [Dell Dell USB Keyboard] on usb-0000:00:02.0-4.1/input1
[    7.424686] usbcore: registered new interface driver usbhid
[    7.424698] usbhid: v2.6:USB HID core driver
[    7.483504] nvidia: module license 'NVIDIA' taints kernel.
[    7.736111] ACPI: PCI Interrupt Link [LMC9] enabled at IRQ 22
[    7.736115] nvidia 0000:00:0d.0: PCI INT A -> Link[LMC9] -> GSI 22 (level, low) -> IRQ 22
[    7.736120] nvidia 0000:00:0d.0: setting latency timer to 64
[    7.737234] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  180.44  Tue Mar 24 05:46:32 PST 2009
[    7.981232] Linux video capture interface: v2.00
[    8.072121] saa7130/34: v4l2 driver version 0.2.14 loaded
[    8.072187] saa7134 0000:01:0a.0: PCI INT A -> Link[LNKC] -> GSI 17 (level, low) -> IRQ 17
[    8.072191] saa7130[0]: found at 0000:01:0a.0, rev: 1, irq: 17, latency: 64, mmio: 0xdffff800
[    8.072196] saa7134: <rant>
[    8.072196] saa7134:  Congratulations!  Your TV card vendor saved a few
[    8.072197] saa7134:  cents for a eeprom, thus your pci board has no
[    8.072198] saa7134:  subsystem ID and I can't identify it automatically
[    8.072199] saa7134: </rant>
[    8.072199] saa7134: I feel better now.  Ok, here are the good news:
[    8.072200] saa7134: You can use the card=<nr> insmod option to specify
[    8.072200] saa7134: which board do you have.  The list:
[    8.072202] saa7134:   card=0 -> UNKNOWN/GENERIC                         
[    8.072204] saa7134:   card=1 -> Proteus Pro [philips reference design]   1131:2001 1131:2001
[    8.072207] saa7134:   card=2 -> LifeView FlyVIDEO3000                    5168:0138 4e42:0138
[    8.072209] saa7134:   card=3 -> LifeView/Typhoon FlyVIDEO2000            5168:0138 4e42:0138
[    8.072212] saa7134:   card=4 -> EMPRESS                                  1131:6752
[    8.072213] saa7134:   card=5 -> SKNet Monster TV                         1131:4e85
[    8.072215] saa7134:   card=6 -> Tevion MD 9717                          
[    8.072217] saa7134:   card=7 -> KNC One TV-Station RDS / Typhoon TV Tune 1131:fe01 1894:fe01
[    8.072219] saa7134:   card=8 -> Terratec Cinergy 400 TV                  153b:1142
[    8.072221] saa7134:   card=9 -> Medion 5044                             
[    8.072223] saa7134:   card=10 -> Kworld/KuroutoShikou SAA7130-TVPCI      
[    8.072224] saa7134:   card=11 -> Terratec Cinergy 600 TV                  153b:1143
[    8.072226] saa7134:   card=12 -> Medion 7134                              16be:0003
[    8.072228] saa7134:   card=13 -> Typhoon TV+Radio 90031                  
[    8.072230] saa7134:   card=14 -> ELSA EX-VISION 300TV                     1048:226b
[    8.072232] saa7134:   card=15 -> ELSA EX-VISION 500TV                     1048:226a
[    8.072234] saa7134:   card=16 -> ASUS TV-FM 7134                          1043:4842 1043:4830 1043:4840
[    8.072236] saa7134:   card=17 -> AOPEN VA1000 POWER                       1131:7133
[    8.072238] saa7134:   card=18 -> BMK MPEX No Tuner                       
[    8.072240] saa7134:   card=19 -> Compro VideoMate TV                      185b:c100
[    8.072242] saa7134:   card=20 -> Matrox CronosPlus                        102b:48d0
[    8.072244] saa7134:   card=21 -> 10MOONS PCI TV CAPTURE CARD              1131:2001
[    8.072246] saa7134:   card=22 -> AverMedia M156 / Medion 2819             1461:a70b
[    8.072247] saa7134:   card=23 -> BMK MPEX Tuner                          
[    8.072249] saa7134:   card=24 -> KNC One TV-Station DVR                   1894:a006
[    8.072251] saa7134:   card=25 -> ASUS TV-FM 7133                          1043:4843
[    8.072253] saa7134:   card=26 -> Pinnacle PCTV Stereo (saa7134)           11bd:002b
[    8.072255] saa7134:   card=27 -> Manli MuchTV M-TV002                    
[    8.072256] saa7134:   card=28 -> Manli MuchTV M-TV001                    
[    8.072258] saa7134:   card=29 -> Nagase Sangyo TransGear 3000TV           1461:050c
[    8.072260] saa7134:   card=30 -> Elitegroup ECS TVP3XP FM1216 Tuner Card( 1019:4cb4
[    8.072262] saa7134:   card=31 -> Elitegroup ECS TVP3XP FM1236 Tuner Card  1019:4cb5
[    8.072264] saa7134:   card=32 -> AVACS SmartTV                           
[    8.072265] saa7134:   card=33 -> AVerMedia DVD EZMaker                    1461:10ff
[    8.072267] saa7134:   card=34 -> Noval Prime TV 7133                     
[    8.072269] saa7134:   card=35 -> AverMedia AverTV Studio 305              1461:2115
[    8.072270] saa7134:   card=36 -> UPMOST PURPLE TV                         12ab:0800
[    8.072272] saa7134:   card=37 -> Items MuchTV Plus / IT-005              
[    8.072274] saa7134:   card=38 -> Terratec Cinergy 200 TV                  153b:1152
[    8.072276] saa7134:   card=39 -> LifeView FlyTV Platinum Mini             5168:0212 4e42:0212 5169:1502
[    8.072278] saa7134:   card=40 -> Compro VideoMate TV PVR/FM               185b:c100
[    8.072280] saa7134:   card=41 -> Compro VideoMate TV Gold+                185b:c100
[    8.072282] saa7134:   card=42 -> Sabrent SBT-TVFM (saa7130)              
[    8.072284] saa7134:   card=43 -> :Zolid Xpert TV7134                     
[    8.072285] saa7134:   card=44 -> Empire PCI TV-Radio LE                  
[    8.072287] saa7134:   card=45 -> Avermedia AVerTV Studio 307              1461:9715
[    8.072289] saa7134:   card=46 -> AVerMedia Cardbus TV/Radio (E500)        1461:d6ee
[    8.072291] saa7134:   card=47 -> Terratec Cinergy 400 mobile              153b:1162
[    8.072293] saa7134:   card=48 -> Terratec Cinergy 600 TV MK3              153b:1158
[    8.072294] saa7134:   card=49 -> Compro VideoMate Gold+ Pal               185b:c200
[    8.072296] saa7134:   card=50 -> Pinnacle PCTV 300i DVB-T + PAL           11bd:002d
[    8.072298] saa7134:   card=51 -> ProVideo PV952                           1540:9524
[    8.072300] saa7134:   card=52 -> AverMedia AverTV/305                     1461:2108
[    8.072302] saa7134:   card=53 -> ASUS TV-FM 7135                          1043:4845
[    8.072304] saa7134:   card=54 -> LifeView FlyTV Platinum FM / Gold        5168:0214 5168:5214 1489:0214 5168:0304
[    8.072307] saa7134:   card=55 -> LifeView FlyDVB-T DUO / MSI TV@nywhere D 5168:0306 4e42:0306
[    8.072309] saa7134:   card=56 -> Avermedia AVerTV 307                     1461:a70a
[    8.072311] saa7134:   card=57 -> Avermedia AVerTV GO 007 FM               1461:f31f
[    8.072313] saa7134:   card=58 -> ADS Tech Instant TV (saa7135)            1421:0350 1421:0351 1421:0370 1421:1370
[    8.072315] saa7134:   card=59 -> Kworld/Tevion V-Stream Xpert TV PVR7134 
[    8.072317] saa7134:   card=60 -> LifeView/Typhoon/Genius FlyDVB-T Duo Car 5168:0502 4e42:0502 1489:0502
[    8.072320] saa7134:   card=61 -> Philips TOUGH DVB-T reference design     1131:2004
[    8.072322] saa7134:   card=62 -> Compro VideoMate TV Gold+II             
[    8.072323] saa7134:   card=63 -> Kworld Xpert TV PVR7134                 
[    8.072325] saa7134:   card=64 -> FlyTV mini Asus Digimatrix               1043:0210
[    8.072327] saa7134:   card=65 -> V-Stream Studio TV Terminator           
[    8.072328] saa7134:   card=66 -> Yuan TUN-900 (saa7135)                  
[    8.072330] saa7134:   card=67 -> Beholder BeholdTV 409 FM                 0000:4091
[    8.072332] saa7134:   card=68 -> GoTView 7135 PCI                         5456:7135
[    8.072334] saa7134:   card=69 -> Philips EUROPA V3 reference design       1131:2004
[    8.072336] saa7134:   card=70 -> Compro Videomate DVB-T300                185b:c900
[    8.072338] saa7134:   card=71 -> Compro Videomate DVB-T200                185b:c901
[    8.072340] saa7134:   card=72 -> RTD Embedded Technologies VFG7350        1435:7350
[    8.072341] saa7134:   card=73 -> RTD Embedded Technologies VFG7330        1435:7330
[    8.072343] saa7134:   card=74 -> LifeView FlyTV Platinum Mini2            14c0:1212
[    8.072345] saa7134:   card=75 -> AVerMedia AVerTVHD MCE A180              1461:1044
[    8.072347] saa7134:   card=76 -> SKNet MonsterTV Mobile                   1131:4ee9
[    8.072349] saa7134:   card=77 -> Pinnacle PCTV 40i/50i/110i (saa7133)     11bd:002e
[    8.072351] saa7134:   card=78 -> ASUSTeK P7131 Dual                       1043:4862
[    8.072353] saa7134:   card=79 -> Sedna/MuchTV PC TV Cardbus TV/Radio (ITO
[    8.072354] saa7134:   card=80 -> ASUS Digimatrix TV                       1043:0210
[    8.072356] saa7134:   card=81 -> Philips Tiger reference design           1131:2018
[    8.072358] saa7134:   card=82 -> MSI TV@Anywhere plus                     1462:6231 1462:8624
[    8.072360] saa7134:   card=83 -> Terratec Cinergy 250 PCI TV              153b:1160
[    8.072362] saa7134:   card=84 -> LifeView FlyDVB Trio                     5168:0319
[    8.072364] saa7134:   card=85 -> AverTV DVB-T 777                         1461:2c05 1461:2c05
[    8.072367] saa7134:   card=86 -> LifeView FlyDVB-T / Genius VideoWonder D 5168:0301 1489:0301
[    8.072369] saa7134:   card=87 -> ADS Instant TV Duo Cardbus PTV331        0331:1421
[    8.072371] saa7134:   card=88 -> Tevion/KWorld DVB-T 220RF                17de:7201
[    8.072373] saa7134:   card=89 -> ELSA EX-VISION 700TV                     1048:226c
[    8.072375] saa7134:   card=90 -> Kworld ATSC110/115                       17de:7350 17de:7352
[    8.072377] saa7134:   card=91 -> AVerMedia A169 B                         1461:7360
[    8.072379] saa7134:   card=92 -> AVerMedia A169 B1                        1461:6360
[    8.072381] saa7134:   card=93 -> Medion 7134 Bridge #2                    16be:0005
[    8.072383] saa7134:   card=94 -> LifeView FlyDVB-T Hybrid Cardbus/MSI TV  5168:3306 5168:3502 5168:3307 4e42:3502
[    8.072386] saa7134:   card=95 -> LifeView FlyVIDEO3000 (NTSC)             5169:0138
[    8.072387] saa7134:   card=96 -> Medion Md8800 Quadro                     16be:0007 16be:0008 16be:000d
[    8.072390] saa7134:   card=97 -> LifeView FlyDVB-S /Acorp TV134DS         5168:0300 4e42:0300
[    8.072392] saa7134:   card=98 -> Proteus Pro 2309                         0919:2003
[    8.072394] saa7134:   card=99 -> AVerMedia TV Hybrid A16AR                1461:2c00
[    8.072396] saa7134:   card=100 -> Asus Europa2 OEM                         1043:4860
[    8.072398] saa7134:   card=101 -> Pinnacle PCTV 310i                       11bd:002f
[    8.072400] saa7134:   card=102 -> Avermedia AVerTV Studio 507              1461:9715
[    8.072402] saa7134:   card=103 -> Compro Videomate DVB-T200A              
[    8.072404] saa7134:   card=104 -> Hauppauge WinTV-HVR1110 DVB-T/Hybrid     0070:6700 0070:6701 0070:6702 0070:6703 0070:6704 0070:6705
[    8.072407] saa7134:   card=105 -> Terratec Cinergy HT PCMCIA               153b:1172
[    8.072409] saa7134:   card=106 -> Encore ENLTV                             1131:2342 1131:2341 3016:2344
[    8.072412] saa7134:   card=107 -> Encore ENLTV-FM                          1131:230f
[    8.072414] saa7134:   card=108 -> Terratec Cinergy HT PCI                  153b:1175
[    8.072416] saa7134:   card=109 -> Philips Tiger - S Reference design      
[    8.072417] saa7134:   card=110 -> Avermedia M102                           1461:f31e
[    8.072419] saa7134:   card=111 -> ASUS P7131 4871                          1043:4871
[    8.072421] saa7134:   card=112 -> ASUSTeK P7131 Hybrid                     1043:4876
[    8.072423] saa7134:   card=113 -> Elitegroup ECS TVP3XP FM1246 Tuner Card  1019:4cb6
[    8.072425] saa7134:   card=114 -> KWorld DVB-T 210                         17de:7250
[    8.072427] saa7134:   card=115 -> Sabrent PCMCIA TV-PCB05                  0919:2003
[    8.072429] saa7134:   card=116 -> 10MOONS TM300 TV Card                    1131:2304
[    8.072431] saa7134:   card=117 -> Avermedia Super 007                      1461:f01d
[    8.072433] saa7134:   card=118 -> Beholder BeholdTV 401                    0000:4016
[    8.072435] saa7134:   card=119 -> Beholder BeholdTV 403                    0000:4036
[    8.072436] saa7134:   card=120 -> Beholder BeholdTV 403 FM                 0000:4037
[    8.072438] saa7134:   card=121 -> Beholder BeholdTV 405                    0000:4050
[    8.072440] saa7134:   card=122 -> Beholder BeholdTV 405 FM                 0000:4051
[    8.072442] saa7134:   card=123 -> Beholder BeholdTV 407                    0000:4070
[    8.072444] saa7134:   card=124 -> Beholder BeholdTV 407 FM                 0000:4071
[    8.072446] saa7134:   card=125 -> Beholder BeholdTV 409                    0000:4090
[    8.072448] saa7134:   card=126 -> Beholder BeholdTV 505 FM/RDS             0000:5051 0000:505b 5ace:5050
[    8.072450] saa7134:   card=127 -> Beholder BeholdTV 507 FM/RDS / BeholdTV  0000:5071 0000:507b 5ace:5070 5ace:5090
[    8.072453] saa7134:   card=128 -> Beholder BeholdTV Columbus TVFM          0000:5201
[    8.072455] saa7134:   card=129 -> Beholder BeholdTV 607 / BeholdTV 609     5ace:6070 5ace:6071 5ace:6072 5ace:6073 5ace:6090 5ace:6091 5ace:6092 5ace:6093
[    8.072459] saa7134:   card=130 -> Beholder BeholdTV M6                     5ace:6190
[    8.072461] saa7134:   card=131 -> Twinhan Hybrid DTV-DVB 3056 PCI          1822:0022
[    8.072463] saa7134:   card=132 -> Genius TVGO AM11MCE                     
[    8.072465] saa7134:   card=133 -> NXP Snake DVB-S reference design        
[    8.072466] saa7134:   card=134 -> Medion/Creatix CTX953 Hybrid             16be:0010
[    8.072468] saa7134:   card=135 -> MSI TV@nywhere A/D v1.1                  1462:8625
[    8.072470] saa7134:   card=136 -> AVerMedia Cardbus TV/Radio (E506R)       1461:f436
[    8.072472] saa7134:   card=137 -> AVerMedia Hybrid TV/Radio (A16D)         1461:f936
[    8.072474] saa7134:   card=138 -> Avermedia M115                           1461:a836
[    8.072476] saa7134:   card=139 -> Compro VideoMate T750                    185b:c900
[    8.072478] saa7134:   card=140 -> Avermedia DVB-S Pro A700                 1461:a7a1
[    8.072480] saa7134:   card=141 -> Avermedia DVB-S Hybrid+FM A700           1461:a7a2
[    8.072481] saa7134:   card=142 -> Beholder BeholdTV H6                     5ace:6290
[    8.072483] saa7134:   card=143 -> Beholder BeholdTV M63                    5ace:6191
[    8.072485] saa7134:   card=144 -> Beholder BeholdTV M6 Extra               5ace:6193
[    8.072487] saa7134:   card=145 -> AVerMedia MiniPCI DVB-T Hybrid M103      1461:f636
[    8.072489] saa7134:   card=146 -> ASUSTeK P7131 Analog                    
[    8.072491] saa7134:   card=147 -> Asus Tiger 3in1                          1043:4878
[    8.072493] saa7134:   card=148 -> Encore ENLTV-FM v5.3                     1a7f:2008
[    8.072504] saa7134:   card=149 -> Avermedia PCI pure analog (M135A)        1461:f11d
[    8.072506] saa7134:   card=150 -> Zogis Real Angel 220                    
[    8.072507] saa7134:   card=151 -> ADS Tech Instant HDTV                    1421:0380
[    8.072509] saa7134:   card=152 -> Asus Tiger Rev:1.00                      1043:4857
[    8.072512] saa7130[0]: subsystem: 1131:0000, board: UNKNOWN/GENERIC [card=0,autodetected]
[    8.072555] saa7130[0]: board init: gpio is 30500
[    8.072888] usb-storage: device scan complete
[    8.076468] scsi 6:0:0:0: Direct-Access     ST916082 7AS                   PQ: 0 ANSI: 2
[    8.080021] sd 6:0:0:0: [sdc] 312581808 512-byte hardware sectors: (160 GB/149 GiB)
[    8.082344] sd 6:0:0:0: [sdc] Write Protect is off
[    8.082348] sd 6:0:0:0: [sdc] Mode Sense: 38 00 00 00
[    8.082349] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[    8.083333] sd 6:0:0:0: [sdc] 312581808 512-byte hardware sectors: (160 GB/149 GiB)
[    8.085595] sd 6:0:0:0: [sdc] Write Protect is off
[    8.085598] sd 6:0:0:0: [sdc] Mode Sense: 38 00 00 00
[    8.085600] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[    8.085606]  sdc:<6>saa7130[0]: Huh, no eeprom present (err=-5)?
[    8.176846] saa7130[0]: registered device video0 [v4l2]
[    8.176881] saa7130[0]: registered device vbi0
[    8.185660] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 21
[    8.185666] HDA Intel 0000:00:05.0: PCI INT B -> Link[LAZA] -> GSI 21 (level, low) -> IRQ 21
[    8.185719] HDA Intel 0000:00:05.0: setting latency timer to 64
[    8.210112] saa7134 ALSA driver for DMA sound loaded
[    8.210139] saa7130[0]/alsa: saa7130[0] at 0xdffff800 irq 17 registered as card -2
[    8.215613]  sdc1
[    8.215806] sd 6:0:0:0: [sdc] Attached SCSI disk
[    8.215908] sd 6:0:0:0: Attached scsi generic sg3 type 0
[    8.576541] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[    9.117897] lp0: using parport0 (interrupt-driven).
[    9.168617] Adding 1003960k swap on /dev/sda5.  Priority:-1 extents:1 across:1003960k
[    9.704821] EXT4 FS on sda1, internal journal on sda1:8
[   10.448588] EXT4-fs: barriers enabled
[   10.465439] kjournald2 starting.  Commit interval 5 seconds
[   10.468748] EXT4 FS on sda3, internal journal on sda3:8
[   10.468751] EXT4-fs: delayed allocation enabled
[   10.468752] EXT4-fs: file extents enabled
[   10.473796] EXT4-fs: mballoc enabled
[   10.473800] EXT4-fs: mounted filesystem with ordered data mode.
[   10.869387] type=1505 audit(1261056925.634:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2135
[   10.897227] type=1505 audit(1261056925.662:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2139
[   10.897336] type=1505 audit(1261056925.662:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2139
[   10.897366] type=1505 audit(1261056925.662:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2139
[   10.897390] type=1505 audit(1261056925.662:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2139
[   10.980076] type=1505 audit(1261056925.742:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2144
[   10.980224] type=1505 audit(1261056925.742:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2144
[   11.021421] type=1505 audit(1261056925.786:9): operation="profile_load" name="/usr/sbin/mysqld" name2="default" pid=2148
[   11.039236] type=1505 audit(1261056925.802:10): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2152
[   15.639000] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   15.639002] Bluetooth: BNEP filters: protocol multicast
[   15.661735] Bridge firewalling registered
[   20.236509] forcedeth 0000:00:07.0: irq 2300 for MSI/MSI-X
[   30.428007] eth0: no IPv6 routers present
```

lspci
```
00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:01.3 Co-processor: nVidia Corporation MCP61 SMU (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:08.1 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0d.0 VGA compatible controller: nVidia Corporation GeForce 6150SE nForce 430 (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Link Control
01:09.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 62)
01:09.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 62)
01:09.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 65)
01:0a.0 Multimedia controller: Philips Semiconductors SAA7130 Video Broadcast Decoder (rev 01)

```

Hope someone can help, please,

---

### Post by ukripper on 2009-12-17
can you also post output of this:
```
sudo lshw -C multimedia
```

---

### Post by theozzlives on 2009-12-17
> **ukripper said:**
> can you also post output of this:
```
sudo lshw -C multimedia
```

```
  *-multimedia
       description: Multimedia controller
       product: SAA7130 Video Broadcast Decoder
       vendor: Philips Semiconductors
       physical id: a
       bus info: pci@0000:01:0a.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=saa7134 latency=64 maxlatency=38 mingnt=15 module=saa7134
  *-multimedia
       description: Audio device
       product: MCP61 High Definition Audio
       vendor: nVidia Corporation
       physical id: 5
       bus info: pci@0000:00:05.0
       version: a2
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list
       configuration: driver=HDA Intel latency=0 maxlatency=5 mingnt=2 module=snd_hda_intel
```

---

### Post by ukripper on 2009-12-17
Taken from here - [https://bugs.launchpad.net/ubuntu/+source/tvtime/+bug/458832](https://bugs.launchpad.net/ubuntu/+source/tvtime/+bug/458832)

> 
Using kernel 2.6.28 also fixed this for me.

I guess the 2.6.31 kernel broke something in the saa7134 module.


---

### Post by theozzlives on 2009-12-17
> **ukripper said:**
> Taken from here - [https://bugs.launchpad.net/ubuntu/+source/tvtime/+bug/458832](https://bugs.launchpad.net/ubuntu/+source/tvtime/+bug/458832)

I'm using Jaunty on that particular machine. I believe 2.26.31.xx came out on Karmic.

---

### Post by ukripper on 2009-12-17
Then it should be working fine. As I can see from the output of lshw that module saa7134 is already loaded for your kernel.

---

### Post by sydbat on 2009-12-17
I wonder if rebooting and going into the recovery option, then "fix X" might work?

---

### Post by theozzlives on 2009-12-17
> **ukripper said:**
> Then it should be working fine. As I can see from the output of lshw that module saa7134 is already loaded for your kernel.

Should it be set to NTSC for basic cable? I told you me and TV cards don't get along. hmmmph!

ALSO: I have compiz effects enabled, could that be it?

---

### Post by ukripper on 2009-12-18
> **theozzlives said:**
> Should it be set to NTSC for basic cable? I told you me and TV cards don't get along. hmmmph!

ALSO: I have compiz effects enabled, could that be it?

Here is a simple guide - may help [http://sites.google.com/site/jobinau2/saa7130basedtvtunercardunderlinux](http://sites.google.com/site/jobinau2/saa7130basedtvtunercardunderlinux)

in terminl run this command:
> tvtime-scanner

and if any error pops up then post here.

---

### Post by theozzlives on 2009-12-18
I haven't the time to read that link in detail. It looks informative. I did run```
tvtime-scanner
```and got```
ozzie@www-server:~$ tvtime-scanner
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/ozzie/.tvtime/tvtime.xml
Scanning using TV standard NTSC.
/home/ozzie/.tvtime/stationlist.xml: No existing NTSC station list "Custom".

    No tuner found on input 0.  If you have a tuner, please
    select a different input using --input=<num>.


```

---

