---
title: "SD card"
date: 2010-04-06
forum: New to Ubuntu
---

### Post by NIGHTHAWKward on 2010-04-06
hey ok so, where would i go to find the SD card data.  I just inserted my card into the laptop and now i dont know where to go to access the photos. nothing came up on screen saying anything about "found new hardware." help

---

### Post by lavinog on 2010-04-06
Normally inserting the sd card should automatically mount the card...look in the places menu (this is assuming you are using karmic.)

If it is not there, open a terminal, and try:
```
dmesg
```

it should give you some messages about what is going on when you inserted the card.
It would be helpful to post that output here.

---

### Post by uRock on 2010-04-06
It should show in Places. Other wise you can go to Places click Computer and the media should show up there.

Let us know if it doesn't show.

Cheers,
uRock

---

### Post by NIGHTHAWKward on 2010-04-06
heres the output i got from the terminal. 
```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.31-20-generic (buildd@palmer) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #58-Ubuntu SMP Fri Mar 12 05:23:09 UTC 2010 (Ubuntu 2.6.31-20.58-generic)
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
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009c400 (usable)
[    0.000000]  BIOS-e820: 000000000009c400 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d2000 - 00000000000d4000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000bf8a1000 (usable)
[    0.000000]  BIOS-e820: 00000000bf8a1000 - 00000000bf8a7000 (reserved)
[    0.000000]  BIOS-e820: 00000000bf8a7000 - 00000000bf9ba000 (usable)
[    0.000000]  BIOS-e820: 00000000bf9ba000 - 00000000bfa0f000 (reserved)
[    0.000000]  BIOS-e820: 00000000bfa0f000 - 00000000bfb08000 (usable)
[    0.000000]  BIOS-e820: 00000000bfb08000 - 00000000bfd0f000 (reserved)
[    0.000000]  BIOS-e820: 00000000bfd0f000 - 00000000bfd18000 (usable)
[    0.000000]  BIOS-e820: 00000000bfd18000 - 00000000bfd1f000 (reserved)
[    0.000000]  BIOS-e820: 00000000bfd1f000 - 00000000bfd63000 (usable)
[    0.000000]  BIOS-e820: 00000000bfd63000 - 00000000bfd9f000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bfd9f000 - 00000000bfde4000 (usable)
[    0.000000]  BIOS-e820: 00000000bfde4000 - 00000000bfdff000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000bfdff000 - 00000000bfe00000 (usable)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000140000000 (usable)
[    0.000000] DMI present.
[    0.000000] last_pfn = 0xbfe00 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 080000000 mask FC0000000 write-back
[    0.000000]   2 base 100000000 mask FC0000000 write-back
[    0.000000]   3 base 0FFE00000 mask FFFE00000 write-protect
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 0000000000002000 - 0000000000006000 (usable) ==> (reserved)
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 000000000009c400 (usable)
[    0.000000]  modified: 000000000009c400 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000d2000 - 00000000000d4000 (reserved)
[    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000bf8a1000 (usable)
[    0.000000]  modified: 00000000bf8a1000 - 00000000bf8a7000 (reserved)
[    0.000000]  modified: 00000000bf8a7000 - 00000000bf9ba000 (usable)
[    0.000000]  modified: 00000000bf9ba000 - 00000000bfa0f000 (reserved)
[    0.000000]  modified: 00000000bfa0f000 - 00000000bfb08000 (usable)
[    0.000000]  modified: 00000000bfb08000 - 00000000bfd0f000 (reserved)
[    0.000000]  modified: 00000000bfd0f000 - 00000000bfd18000 (usable)
[    0.000000]  modified: 00000000bfd18000 - 00000000bfd1f000 (reserved)
[    0.000000]  modified: 00000000bfd1f000 - 00000000bfd63000 (usable)
[    0.000000]  modified: 00000000bfd63000 - 00000000bfd9f000 (ACPI NVS)
[    0.000000]  modified: 00000000bfd9f000 - 00000000bfde4000 (usable)
[    0.000000]  modified: 00000000bfde4000 - 00000000bfdff000 (ACPI data)
[    0.000000]  modified: 00000000bfdff000 - 00000000bfe00000 (usable)
[    0.000000]  modified: 0000000100000000 - 0000000140000000 (usable)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 7000-c000
[    0.000000] RAMDISK: 378a8000 - 37fefd1c
[    0.000000] Allocated new RAMDISK: 008b2000 - 00ff9d1c
[    0.000000] Move RAMDISK from 00000000378a8000 - 0000000037fefd1b to 008b2000 - 00ff9d1b
[    0.000000] ACPI: RSDP 000f7900 00024 (v02 PTLTD )
[    0.000000] ACPI: XSDT bfdf7b7d 00074 (v01 DELL    M09     06040000  LTP 00000000)
[    0.000000] ACPI: FACP bfde8000 000F4 (v03 INTEL  CRESTLNE 06040000 ALAN 00000001)
[    0.000000] ACPI: DSDT bfde9000 06F95 (v02 Intel  CANTIGA  06040000 INTL 20061109)
[    0.000000] ACPI: FACS bfd9efc0 00040
[    0.000000] ACPI: HPET bfdfed16 00038 (v01 INTEL  CRESTLNE 06040000 LOHR 0000005A)
[    0.000000] ACPI: MCFG bfdfed4e 0003C (v01 INTEL  CRESTLNE 06040000 LOHR 0000005A)
[    0.000000] ACPI: APIC bfdfed8a 00068 (v01 PTLTD       APIC   06040000  LTP 00000000)
[    0.000000] ACPI: BOOT bfdfedf2 00028 (v01 PTLTD  $SBFTBL$ 06040000  LTP 00000001)
[    0.000000] ACPI: SLIC bfdfee1a 00176 (v01 DELL    M09     06040000  LTP 00000000)
[    0.000000] ACPI: OSFR bfdfef90 00070 (v01 DELL   DELL     06040000 ASL  00000061)
[    0.000000] ACPI: SSDT bfde7000 00655 (v01  PmRef    CpuPm 00003000 INTL 20050624)
[    0.000000] ACPI: SSDT bfde6000 00259 (v01  PmRef  Cpu0Tst 00003000 INTL 20050624)
[    0.000000] ACPI: SSDT bfde5000 0020F (v01  PmRef    ApTst 00003000 INTL 20050624)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 2182MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000]   node 0 low ram: 00000000 - 377fe000
[    0.000000]   node 0 bootmap 00008000 - 0000ef00
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008ad060]    TEXT DATA BSS ==> [0000100000 - 00008ad060]
[    0.000000]   #4 [000009c400 - 0000100000]    BIOS reserved ==> [000009c400 - 0000100000]
[    0.000000]   #5 [00008ae000 - 00008b1168]              BRK ==> [00008ae000 - 00008b1168]
[    0.000000]   #6 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
[    0.000000]   #7 [00008b2000 - 0000ff9d1c]      NEW RAMDISK ==> [00008b2000 - 0000ff9d1c]
[    0.000000]   #8 [0000008000 - 000000f000]          BOOTMAP ==> [0000008000 - 000000f000]
[    0.000000] found SMP MP-table at [c00f79b0] f79b0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x000bfe00
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[9] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x0000009c
[    0.000000]     0: 0x00000100 -> 0x000bf8a1
[    0.000000]     0: 0x000bf8a7 -> 0x000bf9ba
[    0.000000]     0: 0x000bfa0f -> 0x000bfb08
[    0.000000]     0: 0x000bfd0f -> 0x000bfd18
[    0.000000]     0: 0x000bfd1f -> 0x000bfd63
[    0.000000]     0: 0x000bfd9f -> 0x000bfde4
[    0.000000]     0: 0x000bfdff -> 0x000bfe00
[    0.000000] On node 0 totalpages: 785112
[    0.000000] free_area_init_node: node 0, pgdat c0788900, node_mem_map c1000000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3960 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 4365 pages used for memmap
[    0.000000]   HighMem zone: 553525 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 000000000009c000 - 000000000009d000
[    0.000000] PM: Registered nosave memory: 000000000009d000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d2000
[    0.000000] PM: Registered nosave memory: 00000000000d2000 - 00000000000d4000
[    0.000000] PM: Registered nosave memory: 00000000000d4000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at bfe00000 (gap: bfe00000:40200000)
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages at c2810000, static data 35612 bytes
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 778971
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-20-generic root=UUID=416181ed-887b-4b42-808c-19a2293bf517 ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] xsave/xrstor: enabled xstate_bv 0x3, cntxt size 0x240
[    0.000000] allocated 15718400 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:000bfe00)
[    0.000000] Memory: 3083320k/3143680k available (4578k kernel code, 56264k reserved, 2146k data, 540k init, 2231560k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc0792000 - 0xc0819000   ( 540 kB)
[    0.000000]       .data : 0xc0578948 - 0xc0791408   (2146 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0578948   (4578 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] NR_IRQS:2304 nr_irqs:424
[    0.000000] Extended CMOS year: 2000
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2394.299 MHz processor.
[    0.001172] Console: colour VGA+ 80x25
[    0.001175] console [tty0] enabled
[    0.001317] hpet clockevent registered
[    0.001321] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
[    0.001327] Calibrating delay loop (skipped), value calculated using timer frequency.. 4788.59 BogoMIPS (lpj=9577196)
[    0.001341] Security Framework initialized
[    0.001358] AppArmor: AppArmor initialized
[    0.001363] Mount-cache hash table entries: 512
[    0.001467] Initializing cgroup subsys ns
[    0.001471] Initializing cgroup subsys cpuacct
[    0.001474] Initializing cgroup subsys memory
[    0.001480] Initializing cgroup subsys freezer
[    0.001481] Initializing cgroup subsys net_cls
[    0.001494] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.001496] CPU: L2 cache: 3072K
[    0.001498] CPU: Physical Processor ID: 0
[    0.001499] CPU: Processor Core ID: 0
[    0.001503] mce: CPU supports 6 MCE banks
[    0.001509] CPU0: Thermal monitoring enabled (TM2)
[    0.001512] using mwait in idle threads.
[    0.001517] Performance Counters: Core2 events, Intel PMU driver.
[    0.001524] ... version:                 2
[    0.001525] ... bit width:               40
[    0.001526] ... generic counters:        2
[    0.001528] ... value mask:              000000ffffffffff
[    0.001529] ... max period:              000000007fffffff
[    0.001531] ... fixed-purpose counters:  3
[    0.001532] ... counter mask:            0000000700000003
[    0.001537] Checking 'hlt' instruction... OK.
[    0.018287] ACPI: Core revision 20090521
[    0.028612] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.068455] CPU0: Intel(R) Core(TM)2 Duo CPU     P8600  @ 2.40GHz stepping 0a
[    0.072001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 4787.97 BogoMIPS (lpj=9575940)
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 3072K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.004000] mce: CPU supports 6 MCE banks
[    0.004000] CPU1: Thermal monitoring enabled (TM2)
[    0.004000] x86 PAT enabled: cpu 1, old 0x7040600070406, new 0x7010600070106
[    0.157473] CPU1: Intel(R) Core(TM)2 Duo CPU     P8600  @ 2.40GHz stepping 0a
[    0.157485] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.160020] Brought up 2 CPUs
[    0.160022] Total of 2 processors activated (9576.56 BogoMIPS).
[    0.160069] CPU0 attaching sched-domain:
[    0.160071]  domain 0: span 0-1 level MC
[    0.160073]   groups: 0 1
[    0.160078] CPU1 attaching sched-domain:
[    0.160080]  domain 0: span 0-1 level MC
[    0.160082]   groups: 1 0
[    0.160143] Booting paravirtualized kernel on bare hardware
[    0.160170] regulator: core version 0.5
[    0.160170] Time: 16:50:35  Date: 04/05/10
[    0.160170] NET: Registered protocol family 16
[    0.164081] EISA bus registered
[    0.164089] ACPI: bus type pci registered
[    0.164145] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.164148] PCI: Not using MMCONFIG.
[    0.164472] PCI: PCI BIOS revision 3.00 entry at 0xfde11, last bus=9
[    0.164474] PCI: Using configuration type 1 for base access
[    0.168024] bio: create slab <bio-0> at 0
[    0.169028] ACPI: EC: Look up EC in DSDT
[    0.172640] ACPI: BIOS _OSI(Linux) query ignored
[    0.177751] ACPI: Interpreter enabled
[    0.177756] ACPI: (supports S0 S3 S4 S5)
[    0.177774] ACPI: Using IOAPIC for interrupt routing
[    0.177815] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.178483] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    0.184461] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
[    0.184463] PCI: Using MMCONFIG for extended config space
[    0.188208] ACPI: EC: GPE = 0x1c, I/O: command/status = 0x66, data = 0x62
[    0.188208] ACPI: EC: driver started in interrupt mode
[    0.188432] ACPI: No dock devices found.
[    0.188832] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.188923] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.188926] pci 0000:00:01.0: PME# disabled
[    0.189022] pci 0000:00:1a.0: reg 20 io port: [0x1800-0x181f]
[    0.189114] pci 0000:00:1a.1: reg 20 io port: [0x1820-0x183f]
[    0.189206] pci 0000:00:1a.2: reg 20 io port: [0x1840-0x185f]
[    0.189301] pci 0000:00:1a.7: reg 10 32bit mmio: [0xfc504800-0xfc504bff]
[    0.189369] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.189373] pci 0000:00:1a.7: PME# disabled
[    0.189429] pci 0000:00:1b.0: reg 10 64bit mmio: [0xfc500000-0xfc503fff]
[    0.189488] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.189492] pci 0000:00:1b.0: PME# disabled
[    0.189575] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.189580] pci 0000:00:1c.0: PME# disabled
[    0.189665] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.189669] pci 0000:00:1c.1: PME# disabled
[    0.189757] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.189761] pci 0000:00:1c.3: PME# disabled
[    0.189848] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    0.189852] pci 0000:00:1c.5: PME# disabled
[    0.189926] pci 0000:00:1d.0: reg 20 io port: [0x1860-0x187f]
[    0.190018] pci 0000:00:1d.1: reg 20 io port: [0x1880-0x189f]
[    0.190109] pci 0000:00:1d.2: reg 20 io port: [0x18a0-0x18bf]
[    0.190202] pci 0000:00:1d.7: reg 10 32bit mmio: [0xfc504c00-0xfc504fff]
[    0.190270] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.190275] pci 0000:00:1d.7: PME# disabled
[    0.190524] pci 0000:00:1f.2: reg 10 io port: [0x18f0-0x18f7]
[    0.190531] pci 0000:00:1f.2: reg 14 io port: [0x18e4-0x18e7]
[    0.190538] pci 0000:00:1f.2: reg 18 io port: [0x18e8-0x18ef]
[    0.190546] pci 0000:00:1f.2: reg 1c io port: [0x18e0-0x18e3]
[    0.190553] pci 0000:00:1f.2: reg 20 io port: [0x18c0-0x18df]
[    0.190560] pci 0000:00:1f.2: reg 24 32bit mmio: [0xfc504000-0xfc5047ff]
[    0.190607] pci 0000:00:1f.2: PME# supported from D3hot
[    0.190611] pci 0000:00:1f.2: PME# disabled
[    0.190651] pci 0000:00:1f.3: reg 10 64bit mmio: [0x000000-0x0000ff]
[    0.190669] pci 0000:00:1f.3: reg 20 io port: [0x1c00-0x1c1f]
[    0.190730] pci 0000:01:00.0: reg 10 32bit mmio: [0xd0000000-0xdfffffff]
[    0.190738] pci 0000:01:00.0: reg 14 io port: [0x2000-0x20ff]
[    0.190745] pci 0000:01:00.0: reg 18 32bit mmio: [0xfc000000-0xfc00ffff]
[    0.190768] pci 0000:01:00.0: reg 30 32bit mmio: [0x000000-0x01ffff]
[    0.190796] pci 0000:01:00.0: supports D1 D2
[    0.190840] pci 0000:01:00.1: reg 10 32bit mmio: [0xfc010000-0xfc013fff]
[    0.190900] pci 0000:01:00.1: supports D1 D2
[    0.190968] pci 0000:00:01.0: bridge io port: [0x2000-0x2fff]
[    0.190971] pci 0000:00:01.0: bridge 32bit mmio: [0xfc000000-0xfc0fffff]
[    0.190976] pci 0000:00:01.0: bridge 64bit mmio pref: [0xd0000000-0xdfffffff]
[    0.191034] pci 0000:00:1c.0: bridge io port: [0x3000-0x3fff]
[    0.191038] pci 0000:00:1c.0: bridge 32bit mmio: [0xf6000000-0xf7ffffff]
[    0.191046] pci 0000:00:1c.0: bridge 64bit mmio pref: [0xf0000000-0xf1ffffff]
[    0.191134] pci 0000:04:00.0: reg 10 64bit mmio: [0xf8000000-0xf8001fff]
[    0.191248] pci 0000:04:00.0: PME# supported from D0 D3hot D3cold
[    0.191255] pci 0000:04:00.0: PME# disabled
[    0.191335] pci 0000:00:1c.1: bridge io port: [0x4000-0x4fff]
[    0.191340] pci 0000:00:1c.1: bridge 32bit mmio: [0xf8000000-0xf9ffffff]
[    0.191347] pci 0000:00:1c.1: bridge 64bit mmio pref: [0xf2000000-0xf3ffffff]
[    0.191405] pci 0000:00:1c.3: bridge io port: [0x5000-0x5fff]
[    0.191410] pci 0000:00:1c.3: bridge 32bit mmio: [0xfa000000-0xfbffffff]
[    0.191417] pci 0000:00:1c.3: bridge 64bit mmio pref: [0xf4000000-0xf5ffffff]
[    0.191687] pci 0000:08:00.0: reg 10 64bit mmio: [0xfc100000-0xfc10ffff]
[    0.191828] pci 0000:08:00.0: PME# supported from D3hot D3cold
[    0.191836] pci 0000:08:00.0: PME# disabled
[    0.191917] pci 0000:00:1c.5: bridge 32bit mmio: [0xfc100000-0xfc1fffff]
[    0.191970] pci 0000:09:01.0: reg 10 32bit mmio: [0xfc200000-0xfc2007ff]
[    0.192047] pci 0000:09:01.0: supports D1 D2
[    0.192049] pci 0000:09:01.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.192054] pci 0000:09:01.0: PME# disabled
[    0.192100] pci 0000:09:01.1: reg 10 32bit mmio: [0xfc200800-0xfc2008ff]
[    0.192167] pci 0000:09:01.1: supports D1 D2
[    0.192169] pci 0000:09:01.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.192174] pci 0000:09:01.1: PME# disabled
[    0.192219] pci 0000:09:01.2: reg 10 32bit mmio: [0xfc200c00-0xfc200cff]
[    0.192286] pci 0000:09:01.2: supports D1 D2
[    0.192288] pci 0000:09:01.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.192293] pci 0000:09:01.2: PME# disabled
[    0.192339] pci 0000:09:01.3: reg 10 32bit mmio: [0xfc201000-0xfc2010ff]
[    0.192406] pci 0000:09:01.3: supports D1 D2
[    0.192408] pci 0000:09:01.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.192413] pci 0000:09:01.3: PME# disabled
[    0.192458] pci 0000:09:01.4: reg 10 32bit mmio: [0xfc201400-0xfc2014ff]
[    0.192525] pci 0000:09:01.4: supports D1 D2
[    0.192527] pci 0000:09:01.4: PME# supported from D0 D1 D2 D3hot D3cold
[    0.192532] pci 0000:09:01.4: PME# disabled
[    0.192597] pci 0000:00:1e.0: transparent bridge
[    0.192604] pci 0000:00:1e.0: bridge 32bit mmio: [0xfc200000-0xfc2fffff]
[    0.192643] pci_bus 0000:00: on NUMA node 0
[    0.192647] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.192760] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P2._PRT]
[    0.192819] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.192899] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.192961] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    0.193021] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[    0.193072] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP06._PRT]
[    0.202937] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 *5 6 7 10 12 14 15)
[    0.203027] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.203117] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[    0.203205] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.203293] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    0.203382] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    0.203470] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    0.203558] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 *7 11 12 14 15)
[    0.203701] SCSI subsystem initialized
[    0.204012] libata version 3.00 loaded.
[    0.204035] usbcore: registered new interface driver usbfs
[    0.204035] usbcore: registered new interface driver hub
[    0.204035] usbcore: registered new device driver usb
[    0.204057] ACPI: WMI: Mapper loaded
[    0.204059] PCI: Using ACPI for IRQ routing
[    0.216006] Bluetooth: Core ver 2.15
[    0.216010] NET: Registered protocol family 31
[    0.216011] Bluetooth: HCI device and connection manager initialized
[    0.216013] Bluetooth: HCI socket layer initialized
[    0.216015] NetLabel: Initializing
[    0.216016] NetLabel:  domain hash size = 128
[    0.216018] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.216028] NetLabel:  unlabeled traffic allowed by default
[    0.216055] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.216059] hpet0: 4 comparators, 64-bit 14.318180 MHz counter
[    0.239467] pnp: PnP ACPI init
[    0.239475] ACPI: bus type pnp registered
[    0.241590] pnp: PnP ACPI: found 9 devices
[    0.241592] ACPI: ACPI bus type pnp unregistered
[    0.241595] PnPBIOS: Disabled by ACPI PNP
[    0.241604] system 00:02: iomem range 0xfed00000-0xfed003ff has been reserved
[    0.241610] system 00:04: ioport range 0x400-0x47f has been reserved
[    0.241612] system 00:04: ioport range 0x680-0x69f has been reserved
[    0.241614] system 00:04: ioport range 0x480-0x48f has been reserved
[    0.241617] system 00:04: ioport range 0xffff-0xffff has been reserved
[    0.241619] system 00:04: ioport range 0xffff-0xffff has been reserved
[    0.241621] system 00:04: ioport range 0x1000-0x107f has been reserved
[    0.241624] system 00:04: ioport range 0x1180-0x11ff has been reserved
[    0.241626] system 00:04: ioport range 0x164e-0x164f has been reserved
[    0.241628] system 00:04: ioport range 0xfe00-0xfe00 has been reserved
[    0.241631] system 00:04: ioport range 0x900-0x97f has been reserved
[    0.241636] system 00:08: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    0.241639] system 00:08: iomem range 0xfed10000-0xfed13fff has been reserved
[    0.241641] system 00:08: iomem range 0xfed18000-0xfed18fff has been reserved
[    0.241643] system 00:08: iomem range 0xfed19000-0xfed19fff has been reserved
[    0.241646] system 00:08: iomem range 0xe0000000-0xefffffff has been reserved
[    0.241648] system 00:08: iomem range 0xfeb00000-0xfeb03fff has been reserved
[    0.241650] system 00:08: iomem range 0xfed20000-0xfed3ffff has been reserved
[    0.241653] system 00:08: iomem range 0xfed40000-0xfed44fff has been reserved
[    0.241655] system 00:08: iomem range 0xfed45000-0xfed8ffff has been reserved
[    0.276277] AppArmor: AppArmor Filesystem Enabled
[    0.276350] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.276353] pci 0000:00:01.0:   IO window: 0x2000-0x2fff
[    0.276356] pci 0000:00:01.0:   MEM window: 0xfc000000-0xfc0fffff
[    0.276360] pci 0000:00:01.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
[    0.276364] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
[    0.276367] pci 0000:00:1c.0:   IO window: 0x3000-0x3fff
[    0.276373] pci 0000:00:1c.0:   MEM window: 0xf6000000-0xf7ffffff
[    0.276377] pci 0000:00:1c.0:   PREFETCH window: 0x000000f0000000-0x000000f1ffffff
[    0.276385] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:04
[    0.276388] pci 0000:00:1c.1:   IO window: 0x4000-0x4fff
[    0.276394] pci 0000:00:1c.1:   MEM window: 0xf8000000-0xf9ffffff
[    0.276398] pci 0000:00:1c.1:   PREFETCH window: 0x000000f2000000-0x000000f3ffffff
[    0.276406] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:06
[    0.276409] pci 0000:00:1c.3:   IO window: 0x5000-0x5fff
[    0.276415] pci 0000:00:1c.3:   MEM window: 0xfa000000-0xfbffffff
[    0.276419] pci 0000:00:1c.3:   PREFETCH window: 0x000000f4000000-0x000000f5ffffff
[    0.276427] pci 0000:00:1c.5: PCI bridge, secondary bus 0000:08
[    0.276428] pci 0000:00:1c.5:   IO window: disabled
[    0.276434] pci 0000:00:1c.5:   MEM window: 0xfc100000-0xfc1fffff
[    0.276438] pci 0000:00:1c.5:   PREFETCH window: disabled
[    0.276443] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:09
[    0.276445] pci 0000:00:1e.0:   IO window: disabled
[    0.276450] pci 0000:00:1e.0:   MEM window: 0xfc200000-0xfc2fffff
[    0.276455] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.276464]   alloc irq_desc for 16 on node -1
[    0.276466]   alloc kstat_irqs on node -1
[    0.276470] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.276473] pci 0000:00:01.0: setting latency timer to 64
[    0.276480]   alloc irq_desc for 17 on node -1
[    0.276482]   alloc kstat_irqs on node -1
[    0.276485] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.276489] pci 0000:00:1c.0: setting latency timer to 64
[    0.276497] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.276502] pci 0000:00:1c.1: setting latency timer to 64
[    0.276509]   alloc irq_desc for 19 on node -1
[    0.276511]   alloc kstat_irqs on node -1
[    0.276514] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.276518] pci 0000:00:1c.3: setting latency timer to 64
[    0.276526] pci 0000:00:1c.5: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.276531] pci 0000:00:1c.5: setting latency timer to 64
[    0.276538] pci 0000:00:1e.0: setting latency timer to 64
[    0.276542] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.276544] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.276547] pci_bus 0000:01: resource 0 io:  [0x2000-0x2fff]
[    0.276549] pci_bus 0000:01: resource 1 mem: [0xfc000000-0xfc0fffff]
[    0.276551] pci_bus 0000:01: resource 2 pref mem [0xd0000000-0xdfffffff]
[    0.276553] pci_bus 0000:02: resource 0 io:  [0x3000-0x3fff]
[    0.276555] pci_bus 0000:02: resource 1 mem: [0xf6000000-0xf7ffffff]
[    0.276558] pci_bus 0000:02: resource 2 pref mem [0xf0000000-0xf1ffffff]
[    0.276560] pci_bus 0000:04: resource 0 io:  [0x4000-0x4fff]
[    0.276562] pci_bus 0000:04: resource 1 mem: [0xf8000000-0xf9ffffff]
[    0.276564] pci_bus 0000:04: resource 2 pref mem [0xf2000000-0xf3ffffff]
[    0.276566] pci_bus 0000:06: resource 0 io:  [0x5000-0x5fff]
[    0.276568] pci_bus 0000:06: resource 1 mem: [0xfa000000-0xfbffffff]
[    0.276570] pci_bus 0000:06: resource 2 pref mem [0xf4000000-0xf5ffffff]
[    0.276573] pci_bus 0000:08: resource 1 mem: [0xfc100000-0xfc1fffff]
[    0.276575] pci_bus 0000:09: resource 1 mem: [0xfc200000-0xfc2fffff]
[    0.276577] pci_bus 0000:09: resource 3 io:  [0x00-0xffff]
[    0.276579] pci_bus 0000:09: resource 4 mem: [0x000000-0xffffffff]
[    0.276605] NET: Registered protocol family 2
[    0.276677] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.276912] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.277246] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.277406] TCP: Hash tables configured (established 131072 bind 65536)
[    0.277407] TCP reno registered
[    0.277459] NET: Registered protocol family 1
[    0.277503] Trying to unpack rootfs image as initramfs...
[    0.438262] Freeing initrd memory: 7455k freed
[    0.441175] Simple Boot Flag at 0x36 set to 0x1
[    0.441325] cpufreq-nforce2: No nForce2 chipset.
[    0.441350] Scanning for low memory corruption every 60 seconds
[    0.441438] audit: initializing netlink socket (disabled)
[    0.441452] type=2000 audit(1270486234.439:1): initialized
[    0.448739] highmem bounce pool size: 64 pages
[    0.448743] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.449946] VFS: Disk quotas dquot_6.5.2
[    0.449993] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.450434] fuse init (API version 7.12)
[    0.450502] msgmni has been set to 1679
[    0.450672] alg: No test for stdrng (krng)
[    0.450680] io scheduler noop registered
[    0.450682] io scheduler anticipatory registered
[    0.450684] io scheduler deadline registered
[    0.450716] io scheduler cfq registered (default)
[    0.450859] pci 0000:01:00.0: Boot video device
[    0.450968]   alloc irq_desc for 24 on node -1
[    0.450970]   alloc kstat_irqs on node -1
[    0.450978] pcieport-driver 0000:00:01.0: irq 24 for MSI/MSI-X
[    0.450984] pcieport-driver 0000:00:01.0: setting latency timer to 64
[    0.451098]   alloc irq_desc for 25 on node -1
[    0.451099]   alloc kstat_irqs on node -1
[    0.451107] pcieport-driver 0000:00:1c.0: irq 25 for MSI/MSI-X
[    0.451117] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    0.451255]   alloc irq_desc for 26 on node -1
[    0.451257]   alloc kstat_irqs on node -1
[    0.451265] pcieport-driver 0000:00:1c.1: irq 26 for MSI/MSI-X
[    0.451275] pcieport-driver 0000:00:1c.1: setting latency timer to 64
[    0.451415]   alloc irq_desc for 27 on node -1
[    0.451416]   alloc kstat_irqs on node -1
[    0.451424] pcieport-driver 0000:00:1c.3: irq 27 for MSI/MSI-X
[    0.451438] pcieport-driver 0000:00:1c.3: setting latency timer to 64
[    0.451578]   alloc irq_desc for 28 on node -1
[    0.451579]   alloc kstat_irqs on node -1
[    0.451587] pcieport-driver 0000:00:1c.5: irq 28 for MSI/MSI-X
[    0.451597] pcieport-driver 0000:00:1c.5: setting latency timer to 64
[    0.451691] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.451835] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.503431] Switched to high resolution mode on CPU 1
[    0.503965] Switched to high resolution mode on CPU 0
[    0.552062] ACPI: AC Adapter [ADP1] (on-line)
[    0.552112] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    0.552115] ACPI: Power Button [PWRF]
[    0.552166] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.552168] ACPI: Power Button [PWRB]
[    0.552202] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    0.552204] ACPI: Sleep Button [SLPB]
[    0.552238] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input3
[    0.552842] ACPI: Lid Switch [LID0]
[    0.553576] ACPI: SSDT bfd1ac20 00265 (v01  PmRef  Cpu0Ist 00003000 INTL 20050624)
[    0.554041] ACPI: SSDT bfd18620 00575 (v01  PmRef  Cpu0Cst 00003001 INTL 20050624)
[    0.559950] Monitor-Mwait will be used to enter C-1 state
[    0.559970] Monitor-Mwait will be used to enter C-2 state
[    0.559988] Monitor-Mwait will be used to enter C-3 state
[    0.559994] Marking TSC unstable due to TSC halts in idle
[    0.560017] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    0.560037] processor LNXCPU:00: registered as cooling_device0
[    0.560040] ACPI: Processor [CPU0] (supports 8 throttling states)
[    0.560425] ACPI: SSDT bfd19ca0 001CF (v01  PmRef    ApIst 00003000 INTL 20050624)
[    0.560776] ACPI: SSDT bfd19f20 0008D (v01  PmRef    ApCst 00003000 INTL 20050624)
[    0.565776] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    0.565792] processor LNXCPU:01: registered as cooling_device1
[    0.565795] ACPI: Processor [CPU1] (supports 8 throttling states)
[    0.569632] thermal LNXTHERM:01: registered as thermal_zone0
[    0.569639] ACPI: Thermal Zone [TZ00] (36 C)
[    0.571193] thermal LNXTHERM:02: registered as thermal_zone1
[    0.571199] ACPI: Thermal Zone [TZ01] (25 C)
[    0.572829] thermal LNXTHERM:03: registered as thermal_zone2
[    0.572836] ACPI: Thermal Zone [TZ02] (37 C)
[    0.572878] isapnp: Scanning for PnP cards...
[    0.683686] ACPI: Battery Slot [BAT0] (battery present)
[    0.927275] isapnp: No Plug & Play device found
[    0.928213] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.929273] brd: module loaded
[    0.929637] loop: module loaded
[    0.929690] input: Macintosh mouse button emulation as /devices/virtual/input/input4
[    0.929747] ahci 0000:00:1f.2: version 3.0
[    0.929758] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.929785]   alloc irq_desc for 29 on node -1
[    0.929787]   alloc kstat_irqs on node -1
[    0.929796] ahci 0000:00:1f.2: irq 29 for MSI/MSI-X
[    0.929871] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 4 ports 3 Gbps 0x33 impl SATA mode
[    0.929873] ahci 0000:00:1f.2: flags: 64bit ncq sntf led clo pmp pio slum part 
[    0.929878] ahci 0000:00:1f.2: setting latency timer to 64
[    0.930108] scsi0 : ahci
[    0.930178] scsi1 : ahci
[    0.930227] scsi2 : ahci
[    0.930274] scsi3 : ahci
[    0.930323] scsi4 : ahci
[    0.930370] scsi5 : ahci
[    0.930405] ata1: SATA max UDMA/133 abar m2048@0xfc504000 port 0xfc504100 irq 29
[    0.930409] ata2: SATA max UDMA/133 abar m2048@0xfc504000 port 0xfc504180 irq 29
[    0.930410] ata3: DUMMY
[    0.930412] ata4: DUMMY
[    0.930414] ata5: SATA max UDMA/133 abar m2048@0xfc504000 port 0xfc504300 irq 29
[    0.930417] ata6: SATA max UDMA/133 abar m2048@0xfc504000 port 0xfc504380 irq 29
[    0.931185] Fixed MDIO Bus: probed
[    0.931212] PPP generic driver version 2.4.2
[    0.931276] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.931291] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 19 (level, low) -> IRQ 19
[    0.931300] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    0.931303] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    0.931326] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    0.935235] ehci_hcd 0000:00:1a.7: debug port 1
[    0.935241] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    0.935253] ehci_hcd 0000:00:1a.7: irq 19, io mem 0xfc504800
[    0.948016] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    0.948072] usb usb1: configuration #1 chosen from 1 choice
[    0.948094] hub 1-0:1.0: USB hub found
[    0.948100] hub 1-0:1.0: 6 ports detected
[    0.948149]   alloc irq_desc for 23 on node -1
[    0.948150]   alloc kstat_irqs on node -1
[    0.948154] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.948162] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.948166] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.948189] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    0.952080] ehci_hcd 0000:00:1d.7: debug port 1
[    0.952086] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.952096] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfc504c00
[    0.964016] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.964063] usb usb2: configuration #1 chosen from 1 choice
[    0.964084] hub 2-0:1.0: USB hub found
[    0.964089] hub 2-0:1.0: 6 ports detected
[    0.964140] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.964155] uhci_hcd: USB Universal Host Controller Interface driver
[    0.964171] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.964177] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    0.964180] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    0.964205] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    0.964237] uhci_hcd 0000:00:1a.0: irq 16, io base 0x00001800
[    0.964300] usb usb3: configuration #1 chosen from 1 choice
[    0.964320] hub 3-0:1.0: USB hub found
[    0.964325] hub 3-0:1.0: 2 ports detected
[    0.964364]   alloc irq_desc for 21 on node -1
[    0.964365]   alloc kstat_irqs on node -1
[    0.964369] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.964374] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    0.964377] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    0.964399] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    0.964429] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00001820
[    0.964489] usb usb4: configuration #1 chosen from 1 choice
[    0.964509] hub 4-0:1.0: USB hub found
[    0.964514] hub 4-0:1.0: 2 ports detected
[    0.964552] uhci_hcd 0000:00:1a.2: PCI INT C -> GSI 19 (level, low) -> IRQ 19
[    0.964557] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[    0.964561] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    0.964582] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
[    0.964606] uhci_hcd 0000:00:1a.2: irq 19, io base 0x00001840
[    0.964666] usb usb5: configuration #1 chosen from 1 choice
[    0.964690] hub 5-0:1.0: USB hub found
[    0.964694] hub 5-0:1.0: 2 ports detected
[    0.964731] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.964737] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.964740] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.964762] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
[    0.964785] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001860
[    0.964847] usb usb6: configuration #1 chosen from 1 choice
[    0.964869] hub 6-0:1.0: USB hub found
[    0.964874] hub 6-0:1.0: 2 ports detected
[    0.964910] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.964915] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.964918] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.964942] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
[    0.964965] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001880
[    0.965036] usb usb7: configuration #1 chosen from 1 choice
[    0.965061] hub 7-0:1.0: USB hub found
[    0.965066] hub 7-0:1.0: 2 ports detected
[    0.965102]   alloc irq_desc for 18 on node -1
[    0.965103]   alloc kstat_irqs on node -1
[    0.965106] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.965112] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.965115] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.965137] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
[    0.965167] uhci_hcd 0000:00:1d.2: irq 18, io base 0x000018a0
[    0.965228] usb usb8: configuration #1 chosen from 1 choice
[    0.965248] hub 8-0:1.0: USB hub found
[    0.965253] hub 8-0:1.0: 2 ports detected
[    0.965325] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.973190] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.973194] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.973239] mice: PS/2 mouse device common for all mice
[    0.973345] rtc_cmos 00:05: RTC can wake from S4
[    0.973370] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    0.973401] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    0.973480] device-mapper: uevent: version 1.0.3
[    0.973548] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
[    0.973616] device-mapper: multipath: version 1.1.0 loaded
[    0.973618] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.973713] EISA: Probing bus 0 at eisa.0
[    0.973719] Cannot allocate resource for EISA slot 1
[    0.973721] Cannot allocate resource for EISA slot 2
[    0.973722] Cannot allocate resource for EISA slot 3
[    0.973724] Cannot allocate resource for EISA slot 4
[    0.973725] Cannot allocate resource for EISA slot 5
[    0.973738] EISA: Detected 0 cards.
[    0.973875] cpuidle: using governor ladder
[    0.973972] cpuidle: using governor menu
[    0.974370] TCP cubic registered
[    0.974495] NET: Registered protocol family 10
[    0.974854] lo: Disabled Privacy Extensions
[    0.975124] NET: Registered protocol family 17
[    0.975137] Bluetooth: L2CAP ver 2.13
[    0.975138] Bluetooth: L2CAP socket layer initialized
[    0.975141] Bluetooth: SCO (Voice Link) ver 0.6
[    0.975142] Bluetooth: SCO socket layer initialized
[    0.975187] Bluetooth: RFCOMM TTY layer initialized
[    0.975189] Bluetooth: RFCOMM socket layer initialized
[    0.975191] Bluetooth: RFCOMM ver 1.11
[    0.979851] Using IPI No-Shortcut mode
[    0.979899] PM: Resume from disk failed.
[    0.979911] registered taskstats version 1
[    0.980008]   Magic number: 6:845:842
[    0.980085] rtc_cmos 00:05: setting system clock to 2010-04-05 16:50:36 UTC (1270486236)
[    0.980087] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.980089] EDD information not available.
[    0.981874] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[    1.256088] ata5: SATA link down (SStatus 0 SControl 300)
[    1.256116] ata6: SATA link down (SStatus 0 SControl 300)
[    1.260083] usb 1-6: new high speed USB device using ehci_hcd and address 2
[    1.412072] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.420104] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.421674] ata1.00: ATA-8: SAMSUNG HM320II, 2AC101C4, max UDMA/133
[    1.421678] ata1.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    1.422901] ata2.00: ATAPI: PLDS DVD+/-RW DL-8ATS, XD13, max UDMA/100, ATAPI AN
[    1.426701] ata2.00: configured for UDMA/100
[    1.431362] ata1.00: configured for UDMA/133
[    1.431469] scsi 0:0:0:0: Direct-Access     ATA      SAMSUNG HM320II  2AC1 PQ: 0 ANSI: 5
[    1.431570] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.431600] sd 0:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    1.431636] sd 0:0:0:0: [sda] Write Protect is off
[    1.431639] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.431657] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.431755]  sda:
[    1.435137] scsi 1:0:0:0: CD-ROM            PLDS     DVD+-RW DL-8ATS  XD13 PQ: 0 ANSI: 5
[    1.441796] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda caddy
[    1.441800] Uniform CD-ROM driver Revision: 3.20
[    1.441884] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.441928] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.459723]  sda1 sda2 sda3 sda4 <
[    1.465249] usb 1-6: configuration #1 chosen from 1 choice
[    1.490561]  sda5
[    1.500039] Clocksource tsc unstable (delta = -381520260 ns)
[    1.505130]  sda6 >
[    1.505434] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.505469] Freeing unused kernel memory: 540k freed
[    1.505759] Write protecting the kernel text: 4580k
[    1.505811] Write protecting the kernel read-only data: 1840k
[    1.591978] Linux agpgart interface v0.103
[    1.599568] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/device:02/input/input6
[    1.599605] ACPI: Video Device [M86] (multi-head: yes  rom: no  post: no)
[    1.632092] tg3.c:v3.99 (April 20, 2009)
[    1.632261] tg3 0000:08:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.632273] tg3 0000:08:00.0: setting latency timer to 64
[    1.640651] tg3 0000:08:00.0: PME# disabled
[    1.654289] ohci1394 0000:09:01.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.711083] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[17]  MMIO=[fc200000-fc2007ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    2.193585] eth0: Tigon3 [partno(BCM95784M) rev 5784100] (PCI Express) MAC address 00:22:19:f9:07:6a
[    2.193588] eth0: attached PHY is 5784 (10/100/1000Base-T Ethernet) (WireSpeed[1])
[    2.193590] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[    2.193592] eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[    2.679813] PM: Starting manual resume from disk
[    2.679816] PM: Resume from partition 8:6
[    2.679818] PM: Checking hibernation image.
[    2.679941] PM: Resume from disk failed.
[    2.692414] EXT4-fs (sda5): barriers enabled
[    2.708800] kjournald2 starting: pid 431, dev sda5:8, commit interval 5 seconds
[    2.708879] EXT4-fs (sda5): delayed allocation enabled
[    2.708883] EXT4-fs: file extents enabled
[    2.715869] EXT4-fs: mballoc enabled
[    2.715880] EXT4-fs (sda5): mounted filesystem with ordered data mode
[    2.984435] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[354fc00036c51e21]
[    3.472054] usb 2-3: new high speed USB device using ehci_hcd and address 2
[    3.487507] type=1505 audit(1270486239.003:2): operation="profile_load" pid=456 name=/usr/share/gdm/guest-session/Xsession
[    3.500858] type=1505 audit(1270486239.019:3): operation="profile_load" pid=457 name=/sbin/dhclient3
[    3.501541] type=1505 audit(1270486239.019:4): operation="profile_load" pid=457 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    3.501850] type=1505 audit(1270486239.019:5): operation="profile_load" pid=457 name=/usr/lib/connman/scripts/dhclient-script
[    3.571413] type=1505 audit(1270486239.087:6): operation="profile_load" pid=458 name=/usr/bin/evince
[    3.580676] type=1505 audit(1270486239.099:7): operation="profile_load" pid=458 name=/usr/bin/evince-previewer
[    3.586131] type=1505 audit(1270486239.103:8): operation="profile_load" pid=458 name=/usr/bin/evince-thumbnailer
[    3.614897] usb 2-3: configuration #1 chosen from 1 choice
[    3.615999] type=1505 audit(1270486239.131:9): operation="profile_load" pid=460 name=/usr/lib/cups/backend/cups-pdf
[    3.623595] Initializing USB Mass Storage driver...
[    3.623681] scsi6 : SCSI emulation for USB Mass Storage devices
[    3.623750] usbcore: registered new interface driver usb-storage
[    3.623752] USB Mass Storage support registered.
[    3.623803] usb-storage: device found at 2
[    3.623805] usb-storage: waiting for device to settle before scanning
[    3.627865] usbcore: registered new interface driver hiddev
[    3.631871] generic-usb 0003:413C:5305.0001: hiddev96,hidraw0: USB HID v1.00 Device [Dell  V305] on usb-0000:00:1d.7-3/input3
[    3.631887] usbcore: registered new interface driver usbhid
[    3.631890] usbhid: v2.6:USB HID core driver
[    8.620883] usb-storage: device scan complete
[    8.638971] scsi 6:0:0:0: Direct-Access     Dell     USB Mass Storage  200 PQ: 0 ANSI: 0
[    8.639485] sd 6:0:0:0: Attached scsi generic sg2 type 0
[    8.698832] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[   13.307715] udev: starting version 147
[   13.322183] lp: driver loaded but no devices found
[   13.332821] Adding 3566388k swap on /dev/sda6.  Priority:-1 extents:1 across:3566388k 
[   13.390022] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   13.390027] Disabling lock debugging due to kernel taint
[   13.465031] [fglrx] Maximum main memory to use for locked dma buffers: 2873 MBytes.
[   13.465348] [fglrx]   vendor: 1002 device: 9553 count: 1
[   13.465795] [fglrx] ioport: bar 1, base 0x2000, size: 0x100
[   13.465811] pci 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   13.465816] pci 0000:01:00.0: setting latency timer to 64
[   13.465977] [fglrx] Kernel PAT support is enabled
[   13.465995] [fglrx] module loaded - fglrx 8.66.10 [Sep  3 2009] with 1 minors
[   13.468941] cfg80211: Calling CRDA to update world regulatory domain
[   13.485771] Linux video capture interface: v2.00
[   13.486895] sdhci: Secure Digital Host Controller Interface driver
[   13.486897] sdhci: Copyright(c) Pierre Ossman
[   13.489312] uvcvideo: Found UVC 1.00 device Laptop_Integrated_Webcam_2M (0c45:63eb)
[   13.497159] ricoh-mmc: Ricoh MMC Controller disabling driver
[   13.497161] ricoh-mmc: Copyright(c) Philip Langdale
[   13.497188] ricoh-mmc: Ricoh MMC controller found at 0000:09:01.2 [1180:0843] (rev 12)
[   13.497205] ricoh-mmc: Controller is now disabled.
[   13.498016] usblp0: USB Bidirectional printer dev 2 if 1 alt 0 proto 2 vid 0x413C pid 0x5305
[   13.498033] usbcore: registered new interface driver usblp
[   13.517873] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   13.526387] cfg80211: World regulatory domain updated:
[   13.526390]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   13.526392]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.526394]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   13.526396]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   13.526399]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.526401]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.552617] input: Laptop_Integrated_Webcam_2M as /devices/pci0000:00/0000:00:1a.7/usb1/1-6/1-6:1.0/input/input7
[   13.559973]   alloc irq_desc for 22 on node -1
[   13.559976]   alloc kstat_irqs on node -1
[   13.559982] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   13.560014] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   13.582556] usbcore: registered new interface driver uvcvideo
[   13.582559] USB Video Class driver (v0.1.0)
[   13.585822] EXT4-fs (sda5): internal journal on sda5:8
[   13.594443] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
[   13.594446] iwlagn: Copyright(c) 2003-2009 Intel Corporation
[   13.594510] iwlagn 0000:04:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   13.594518] iwlagn 0000:04:00.0: setting latency timer to 64
[   13.594552] iwlagn 0000:04:00.0: Detected Intel Wireless WiFi Link 5100AGN REV=0x54
[   13.634818] sdhci-pci 0000:09:01.1: SDHCI controller found [1180:0822] (rev 22)
[   13.634836] sdhci-pci 0000:09:01.1: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[   13.636874] Registered led device: mmc0::
[   13.637919] mmc0: SDHCI controller on PCI [0000:09:01.1] using DMA
[   13.647038] ip_tables: (C) 2000-2006 Netfilter Core Team
[   13.649447] input: Dell WMI hotkeys as /devices/virtual/input/input8
[   13.662308] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[   13.662463] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Please use
[   13.662465] nf_conntrack.acct=1 kernel parameter, acct=1 nf_conntrack module option or
[   13.662467] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
[   13.663498] iwlagn 0000:04:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[   13.663559]   alloc irq_desc for 30 on node -1
[   13.663561]   alloc kstat_irqs on node -1
[   13.663579] iwlagn 0000:04:00.0: irq 30 for MSI/MSI-X
[   13.704327] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input9
[   13.714575] ip6_tables: (C) 2000-2006 Netfilter Core Team
[   13.715683] input: HDA Intel Mic at Ext Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   13.715744] input: HDA Intel HP Out at Ext Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   13.715789] input: HDA Intel HP Out at Ext Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[   13.716279] HDA Intel 0000:01:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   13.716307] HDA Intel 0000:01:00.1: setting latency timer to 64
[   13.716869] phy0: Selected rate control algorithm 'iwl-agn-rs'
[   14.319446] Synaptics Touchpad, model: 1, fw: 7.2, id: 0x1c0b1, caps: 0xd04731/0xa40000
[   14.364578] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input13
[   14.923588] __ratelimit: 6 callbacks suppressed
[   14.923591] type=1505 audit(1270500650.439:12): operation="profile_replace" pid=1246 name=/usr/share/gdm/guest-session/Xsession
[   14.924953] type=1505 audit(1270500650.443:13): operation="profile_replace" pid=1247 name=/sbin/dhclient3
[   14.925583] type=1505 audit(1270500650.443:14): operation="profile_replace" pid=1247 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   14.925919] type=1505 audit(1270500650.443:15): operation="profile_replace" pid=1247 name=/usr/lib/connman/scripts/dhclient-script
[   14.928884] type=1505 audit(1270500650.447:16): operation="profile_replace" pid=1248 name=/usr/bin/evince
[   14.938569] type=1505 audit(1270500650.455:17): operation="profile_replace" pid=1248 name=/usr/bin/evince-previewer
[   14.944374] type=1505 audit(1270500650.463:18): operation="profile_replace" pid=1248 name=/usr/bin/evince-thumbnailer
[   14.953897] type=1505 audit(1270500650.471:19): operation="profile_replace" pid=1250 name=/usr/lib/cups/backend/cups-pdf
[   14.954609] type=1505 audit(1270500650.471:20): operation="profile_replace" pid=1250 name=/usr/sbin/cupsd
[   14.956547] type=1505 audit(1270500650.475:21): operation="profile_replace" pid=1251 name=/usr/sbin/tcpdump
[   15.112530] iwlagn 0000:04:00.0: firmware: requesting iwlwifi-5000-2.ucode
[   15.152974] iwlagn 0000:04:00.0: loaded firmware version 8.24.2.12
[   15.319028] Registered led device: iwl-phy0::radio
[   15.319045] Registered led device: iwl-phy0::assoc
[   15.319059] Registered led device: iwl-phy0::RX
[   15.319075] Registered led device: iwl-phy0::TX
[   15.361287] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   15.362408] tg3 0000:08:00.0: PME# disabled
[   15.362735]   alloc irq_desc for 31 on node -1
[   15.362737]   alloc kstat_irqs on node -1
[   15.362756] tg3 0000:08:00.0: irq 31 for MSI/MSI-X
[   15.509597] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   17.313879] ppdev: user-space parallel port driver
[   18.845881] usb 2-3: usbfs: interface 1 claimed by usblp while 'usb' sets config #1
[   21.368415]   alloc irq_desc for 32 on node -1
[   21.368418]   alloc kstat_irqs on node -1
[   21.368431] fglrx_pci 0000:01:00.0: irq 32 for MSI/MSI-X
[   21.378833] [fglrx] Firegl kernel thread PID: 2025
[   21.582238] [fglrx] Gart USWC size:942 M.
[   21.582241] [fglrx] Gart cacheable size:373 M.
[   21.582246] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
[   21.582249] [fglrx] Reserved FB block: Unshared offset:fd0b000, size:2f5000 
[   21.582251] [fglrx] Reserved FB block: Unshared offset:1fffb000, size:5000 
[   24.652811] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
[   94.187933] wlan0: authenticate with AP 00:17:df:36:5a:60
[   94.189384] wlan0: authenticated
[   94.189392] wlan0: associate with AP 00:17:df:36:5a:60
[   94.195597] wlan0: RX AssocResp from 00:17:df:36:5a:60 (capab=0x421 status=0 aid=62)
[   94.195605] wlan0: associated
[   94.204388] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  104.509033] wlan0: no IPv6 routers present
[  916.364121] ACPI: EC: input buffer is not empty, aborting transaction
[ 2600.697042] CE: hpet increasing min_delta_ns to 15000 nsec
[20809.993464] hda-intel: azx_get_response timeout, switching to polling mode: last cmd=0x024f0c00
[21225.984255] ACPI: EC: missing confirmations, switch off interrupt mode.
[21226.488095] ACPI Exception: AE_TIME, Returned by Handler for [EmbeddedControl] 20090521 evregion-424
[21226.488125] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.BAT0._BST] (Node f7011330), AE_TIME
[21226.488221] ACPI Exception: AE_TIME, Evaluating _BST 20090521 battery-385
matt@matt-laptop:~$
```

---

### Post by lavinog on 2010-04-06
Did your laptop go to sleep recently?
What happens when you insert a sd card after reboot?

What is the make and model of your laptop?

---

### Post by NIGHTHAWKward on 2010-04-06
its a dell studio studio15

---

### Post by NIGHTHAWKward on 2010-04-06
nvm. i reluctantly looked at the places menu again and there it was. thanks

---

### Post by RJ12 on 2010-04-07
Also, just a little tip, when you paste output from the terminal, can you put it in code tags (The # symbol).

```
When you post it will look like this.
```

---

### Post by lisati on 2010-04-07
> **RJ12 said:**
> Also, just a little tip, when you paste output from the terminal, can you put it in code tags (The # symbol).

```
When you post it will look like this.
```

Done.

@NIGHTHAWKWard: have a look here: [http://ubuntuforums.org/misc.php?do=bbcode](http://ubuntuforums.org/misc.php?do=bbcode)

---

### Post by tom.swartz07 on 2010-04-07
> **NIGHTHAWKward said:**
> nvm. i reluctantly looked at the places menu again and there it was. thanks

99% of the time, it will just silently add itself to that menu. If you want, you could add a dock, or a panel applet that lists your Places menu - just like the ones I have in the attachment:

Docky and Avant Window Navigator are in the image

Give a shoutout if you want help to install them, we could give you a ton of suggestions.

---

