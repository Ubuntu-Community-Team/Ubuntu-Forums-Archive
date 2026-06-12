---
title: "Ubuntu crashes"
date: 2009-11-28
forum: New to Ubuntu
---

### Post by AndiBu on 2009-11-28
Hey together,

I got a new Notebook, so I tried to install Ubuntu 9.10. Everything worked quite fine (except the sound, but I think, this is a problem I'm going to solve by investing a little time in it).
But now to my real problem: After 1 - 2 hours in the xserver the whole notebook crashes and only a hard-restart works. After rebooting it's the same and the notebook crashes again.
I've tried to solve this problem by reinstalling ubuntu several times, and even installed different distributions. But the problem is always the same.

Has anyone an idea what's wrong about my installation,
what details do you need? Any log-files or hardware-information?

Thanks :) ,

 AndiBu

---

### Post by rudy.b on 2009-11-30
It would be useful to know what model of notebook you have, and what are the symptoms of the crashes you experience (e.g. 'screen goes black,' or 'screen is frozen and mouse is unresponsive').  Also, any entries in your kernel log ('dmesg') at the time of the crash could help identify the problem as well.

---

### Post by ukripper on 2009-11-30
> **AndiBu said:**
> Hey together,

I got a new Notebook, so I tried to install Ubuntu 9.10. Everything worked quite fine (except the sound, but I think, this is a problem I'm going to solve by investing a little time in it).
But now to my real problem: After 1 - 2 hours in the xserver the whole notebook crashes and only a hard-restart works. After rebooting it's the same and the notebook crashes again.
I've tried to solve this problem by reinstalling ubuntu several times, and even installed different distributions. But the problem is always the same.

Has anyone an idea what's wrong about my installation,
what details do you need? Any log-files or hardware-information?

Thanks :) ,

 AndiBu

Can you post output of the following commands:
```
tail -n 200 /var/log/messages
```

```
lspci
```

Seems to me problem with graphics card drivers. Is it ATI?

---

### Post by coffeecat on 2009-11-30
Another possibilty is faulty RAM. You don't say whether you've got Windows on that netbook, but if you have and Windows is OK that doesn't necessarily exclude bad RAM. Linux and Windows use memory differently and Linux is more likely to expose faulty RAM.

You could try running memtest from the grub menu, but you need to do this for many, many hours before being even half-confident that there isn't bad memory.

---

### Post by AndiBu on 2009-11-30
Thanks for those answers, yes It's true, I'm also running Win 7 on the Notebook without any problems.

Everytime Ubuntu crashes, the screen is frozen.

To my Hardware: It's an Asus Notebook of the Pro61 Series.
Graphic Card: GeForce GT 220 M
CPU: Intel Core Duo P7350, 2GHz
Memory: 4GB

Now to the several log files: 
Sorry for posting the whole entries, but I don't know what to filter out:

dmesg:

> 
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.31-15-generic (buildd@rothera) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #50-Ubuntu SMP Tue Nov 10 14:54:29 UTC 2009 (Ubuntu 2.6.31-15.50-generic)
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
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000bffb8000 (usable)
[    0.000000]  BIOS-e820: 00000000bffb8000 - 00000000bffc0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bffc0000 - 00000000bffce000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000bffce000 - 00000000c0000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000140000000 (usable)
[    0.000000] DMI present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0xbffb8 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0C0000000 mask FC0000000 uncachable
[    0.000000]   1 base 000000000 mask F00000000 write-back
[    0.000000]   2 base 100000000 mask FC0000000 write-back
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 00000000c0000000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009fc00 (usable)
[    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000bffb8000 (usable)
[    0.000000]  modified: 00000000bffb8000 - 00000000bffc0000 (ACPI NVS)
[    0.000000]  modified: 00000000bffc0000 - 00000000bffce000 (ACPI data)
[    0.000000]  modified: 00000000bffce000 - 00000000c0000000 (ACPI NVS)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 0000000100000000 - 0000000140000000 (usable)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 10000-15000
[    0.000000] RAMDISK: 378a5000 - 37fef1c1
[    0.000000] Allocated new RAMDISK: 008ad000 - 00ff71c1
[    0.000000] Move RAMDISK from 00000000378a5000 - 0000000037fef1c0 to 008ad000 - 00ff71c0
[    0.000000] ACPI: RSDP 000f9910 00014 (v00 ACPIAM)
[    0.000000] ACPI: RSDT bffc0000 0004C (v01 _ASUS_ Notebook 20090609 MSFT 00000097)
[    0.000000] ACPI: FACP bffc0200 00084 (v01 060909 FACP0857 20090609 MSFT 00000097)
[    0.000000] ACPI: DSDT bffc0680 09568 (v01  F50Sf F50Sf001 00000001 INTL 20051117)
[    0.000000] ACPI: FACS bffce000 00040
[    0.000000] ACPI: APIC bffc0390 0005C (v01 060909 APIC0857 20090609 MSFT 00000097)
[    0.000000] ACPI: MCFG bffc0430 0003C (v01 060909 OEMMCFG  20090609 MSFT 00000097)
[    0.000000] ACPI: SLIC bffc0470 00176 (v01 _ASUS_ Notebook 20090609 MSFT 00000097)
[    0.000000] ACPI: ECDT bffc0620 00055 (v01 060909 OEMECDT  20090609 MSFT 00000097)
[    0.000000] ACPI: DBGP bffc03f0 00034 (v01 060909 DBGP0857 20090609 MSFT 00000097)
[    0.000000] ACPI: BOOT bffc05f0 00028 (v01 060909 BOOT0857 20090609 MSFT 00000097)
[    0.000000] ACPI: OEMB bffce040 00071 (v01 060909 OEMB0857 20090609 MSFT 00000097)
[    0.000000] ACPI: HPET bffc9bf0 00038 (v01 060909 OEMHPET  20090609 MSFT 00000097)
[    0.000000] ACPI: SSDT bffcecc0 004E6 (v01  PmRef    CpuPm 00003000 INTL 20051117)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 2183MB HIGHMEM available.
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
[    0.000000]   #4 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #5 [00008a9000 - 00008ac1dc]              BRK ==> [00008a9000 - 00008ac1dc]
[    0.000000]   #6 [0000010000 - 0000011000]          PGTABLE ==> [0000010000 - 0000011000]
[    0.000000]   #7 [00008ad000 - 0000ff71c1]      NEW RAMDISK ==> [00008ad000 - 0000ff71c1]
[    0.000000]   #8 [0000011000 - 0000018000]          BOOTMAP ==> [0000011000 - 0000018000]
[    0.000000] found SMP MP-table at [c00ff780] ff780
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x000bffb8
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x000bffb8
[    0.000000] On node 0 totalpages: 786247
[    0.000000] free_area_init_node: node 0, pgdat c0784940, node_mem_map c1000200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 4368 pages used for memmap
[    0.000000]   HighMem zone: 554666 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 20, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x10398201 base: 0xfed00000
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at c0000000 (gap: c0000000:3ee00000)
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages at c2810000, static data 35612 bytes
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 780103
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-15-generic root=UUID=d3bb8ccf-36a6-4a75-83cb-3611ee0cd152 ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 15726880 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:000bffb8)
[    0.000000] Memory: 3087892k/3145440k available (4566k kernel code, 56252k reserved, 2142k data, 540k init, 2236136k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc078e000 - 0xc0815000   ( 540 kB)
[    0.000000]       .data : 0xc0575b44 - 0xc078d3c8   (2142 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0575b44   (4566 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] NR_IRQS:2304 nr_irqs:424
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1999.974 MHz processor.
[    0.002470] Console: colour VGA+ 80x25
[    0.002475] console [tty0] enabled
[    0.002664] hpet clockevent registered
[    0.002668] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.002677] Calibrating delay loop (skipped), value calculated using timer frequency.. 3999.94 BogoMIPS (lpj=7999896)
[    0.002704] Security Framework initialized
[    0.002741] AppArmor: AppArmor initialized
[    0.002750] Mount-cache hash table entries: 512
[    0.002958] Initializing cgroup subsys ns
[    0.002966] Initializing cgroup subsys cpuacct
[    0.002971] Initializing cgroup subsys memory
[    0.002980] Initializing cgroup subsys freezer
[    0.002983] Initializing cgroup subsys net_cls
[    0.003004] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.003007] CPU: L2 cache: 3072K
[    0.003010] CPU: Physical Processor ID: 0
[    0.003012] CPU: Processor Core ID: 0
[    0.003017] mce: CPU supports 6 MCE banks
[    0.003027] CPU0: Thermal monitoring handled by SMI
[    0.003033] using mwait in idle threads.
[    0.003045] Performance Counters: Core2 events, Intel PMU driver.
[    0.003055] ... version:                 2
[    0.003057] ... bit width:               40
[    0.003059] ... generic counters:        2
[    0.003061] ... value mask:              000000ffffffffff
[    0.003063] ... max period:              000000007fffffff
[    0.003065] ... fixed-purpose counters:  3
[    0.003066] ... counter mask:            0000000700000003
[    0.003073] Checking 'hlt' instruction... OK.
[    0.019153] ACPI: Core revision 20090521
[    0.036332] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.078226] CPU0: Intel(R) Core(TM)2 Duo CPU     P7350  @ 2.00GHz stepping 06
[    0.080001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 4000.13 BogoMIPS (lpj=8000276)
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 3072K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.004000] mce: CPU supports 6 MCE banks
[    0.004000] CPU1: Thermal monitoring handled by SMI
[    0.004000] x86 PAT enabled: cpu 1, old 0x7040600070406, new 0x7010600070106
[    0.170053] CPU1: Intel(R) Core(TM)2 Duo CPU     P7350  @ 2.00GHz stepping 06
[    0.170068] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.172028] Brought up 2 CPUs
[    0.172030] Total of 2 processors activated (8000.08 BogoMIPS).
[    0.172065] CPU0 attaching sched-domain:
[    0.172069]  domain 0: span 0-1 level MC
[    0.172071]   groups: 0 1
[    0.172077] CPU1 attaching sched-domain:
[    0.172079]  domain 0: span 0-1 level MC
[    0.172081]   groups: 1 0
[    0.172168] Booting paravirtualized kernel on bare hardware
[    0.172228] regulator: core version 0.5
[    0.172228] Time: 13:27:55  Date: 11/30/09
[    0.172228] NET: Registered protocol family 16
[    0.172228] EISA bus registered
[    0.172228] ACPI: bus type pci registered
[    0.172303] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.172306] PCI: Not using MMCONFIG.
[    0.176005] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=6
[    0.176007] PCI: Using configuration type 1 for base access
[    0.177065] bio: create slab <bio-0> at 0
[    0.177073] ACPI: EC: EC description table is found, configuring boot EC
[    0.177085] ACPI: EC: Look up EC in DSDT
[    0.189751] ACPI: Interpreter enabled
[    0.189761] ACPI: (supports S0 S3 S4 S5)
[    0.189786] ACPI: Using IOAPIC for interrupt routing
[    0.189871] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.192327] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
[    0.192329] PCI: Using MMCONFIG for extended config space
[    0.197970] ACPI: EC: GPE = 0x19, I/O: command/status = 0x66, data = 0x62
[    0.197972] ACPI: EC: driver started in poll mode
[    0.198263] ACPI: No dock devices found.
[    0.198624] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.198753] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.198758] pci 0000:00:01.0: PME# disabled
[    0.198873] pci 0000:00:02.5: reg 20 io port: [0xfff0-0xffff]
[    0.198903] pci 0000:00:02.5: PME# supported from D3cold
[    0.198907] pci 0000:00:02.5: PME# disabled
[    0.198933] pci 0000:00:03.0: reg 10 32bit mmio: [0xf9fff000-0xf9ffffff]
[    0.198984] pci 0000:00:03.1: reg 10 32bit mmio: [0xf9ffe000-0xf9ffefff]
[    0.199047] pci 0000:00:03.3: reg 10 32bit mmio: [0xf9ffd000-0xf9ffdfff]
[    0.199091] pci 0000:00:03.3: PME# supported from D0 D3hot D3cold
[    0.199096] pci 0000:00:03.3: PME# disabled
[    0.199133] pci 0000:00:04.0: reg 10 32bit mmio: [0xf9ffcc00-0xf9ffcc7f]
[    0.199140] pci 0000:00:04.0: reg 14 io port: [0xcc00-0xcc7f]
[    0.199181] pci 0000:00:04.0: supports D1 D2
[    0.199183] pci 0000:00:04.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.199187] pci 0000:00:04.0: PME# disabled
[    0.199220] pci 0000:00:05.0: reg 10 io port: [0xc800-0xc807]
[    0.199227] pci 0000:00:05.0: reg 14 io port: [0xc400-0xc403]
[    0.199234] pci 0000:00:05.0: reg 18 io port: [0xc000-0xc007]
[    0.199241] pci 0000:00:05.0: reg 1c io port: [0xbc00-0xbc03]
[    0.199248] pci 0000:00:05.0: reg 20 io port: [0xb800-0xb80f]
[    0.199255] pci 0000:00:05.0: reg 24 io port: [0xb400-0xb47f]
[    0.199280] pci 0000:00:05.0: PME# supported from D3cold
[    0.199284] pci 0000:00:05.0: PME# disabled
[    0.199360] pci 0000:00:06.0: PME# supported from D0 D3hot D3cold
[    0.199364] pci 0000:00:06.0: PME# disabled
[    0.199447] pci 0000:00:07.0: PME# supported from D0 D3hot D3cold
[    0.199451] pci 0000:00:07.0: PME# disabled
[    0.199501] pci 0000:00:0f.0: reg 10 32bit mmio: [0xf9ff4000-0xf9ff7fff]
[    0.199547] pci 0000:00:0f.0: PME# supported from D0 D3hot D3cold
[    0.199551] pci 0000:00:0f.0: PME# disabled
[    0.199626] pci 0000:01:00.0: reg 10 32bit mmio: [0xfc000000-0xfcffffff]
[    0.199642] pci 0000:01:00.0: reg 14 64bit mmio: [0xd0000000-0xdfffffff]
[    0.199656] pci 0000:01:00.0: reg 1c 64bit mmio: [0xfa000000-0xfbffffff]
[    0.199665] pci 0000:01:00.0: reg 24 io port: [0xdc00-0xdc7f]
[    0.199673] pci 0000:01:00.0: reg 30 32bit mmio: [0xfde80000-0xfdefffff]
[    0.199770] pci 0000:00:01.0: bridge io port: [0xd000-0xdfff]
[    0.199774] pci 0000:00:01.0: bridge 32bit mmio: [0xfa000000-0xfdefffff]
[    0.199781] pci 0000:00:01.0: bridge 64bit mmio pref: [0xd0000000-0xdfffffff]
[    0.199847] pci 0000:02:00.0: reg 10 64bit mmio: [0xfdff0000-0xfdffffff]
[    0.199925] pci 0000:02:00.0: supports D1
[    0.199928] pci 0000:02:00.0: PME# supported from D0 D1 D3hot D3cold
[    0.199934] pci 0000:02:00.0: PME# disabled
[    0.200013] pci 0000:00:06.0: bridge 32bit mmio: [0xfdf00000-0xfdffffff]
[    0.200074] pci 0000:00:07.0: bridge io port: [0xe000-0xefff]
[    0.200078] pci 0000:00:07.0: bridge 32bit mmio: [0xfe000000-0xfebfffff]
[    0.200086] pci 0000:00:07.0: bridge 64bit mmio pref: [0xf6000000-0xf8ffffff]
[    0.200103] pci_bus 0000:00: on NUMA node 0
[    0.200109] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.200356] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.207701] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 *10 11 12 14 15)
[    0.207842] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 10 *11 12 14 15)
[    0.207981] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 *4 5 7 10 11 12 14 15)
[    0.208124] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 *7 10 11 12 14 15)
[    0.208262] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 *5 7 10 11 12 14 15)
[    0.208401] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 10 11 12 14 *15)
[    0.208539] ACPI: PCI Interrupt Link [LNKG] (IRQs *3 4 5 7 10 11 12 14 15)
[    0.208678] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.208863] SCSI subsystem initialized
[    0.208884] libata version 3.00 loaded.
[    0.208884] usbcore: registered new interface driver usbfs
[    0.208884] usbcore: registered new interface driver hub
[    0.208884] usbcore: registered new device driver usb
[    0.208884] ACPI: WMI: Mapper loaded
[    0.208884] PCI: Using ACPI for IRQ routing
[    0.220008] Bluetooth: Core ver 2.15
[    0.220022] NET: Registered protocol family 31
[    0.220022] Bluetooth: HCI device and connection manager initialized
[    0.220022] Bluetooth: HCI socket layer initialized
[    0.220022] NetLabel: Initializing
[    0.220022] NetLabel:  domain hash size = 128
[    0.220022] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.220035] NetLabel:  unlabeled traffic allowed by default
[    0.220066] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.220072] hpet0: 3 comparators, 32-bit 14.318180 MHz counter
[    0.236011] pnp: PnP ACPI init
[    0.236020] ACPI: bus type pnp registered
[    0.238186] pnp: PnP ACPI: found 12 devices
[    0.238188] ACPI: ACPI bus type pnp unregistered
[    0.238192] PnPBIOS: Disabled by ACPI PNP
[    0.238205] system 00:06: ioport range 0x290-0x297 has been reserved
[    0.238208] system 00:06: ioport range 0xc00-0xc05 has been reserved
[    0.238211] system 00:06: ioport range 0xd00-0xd05 has been reserved
[    0.238215] system 00:06: ioport range 0x480-0x48f has been reserved
[    0.238217] system 00:06: ioport range 0x4d0-0x4d1 has been reserved
[    0.238220] system 00:06: ioport range 0x800-0x87f has been reserved
[    0.238223] system 00:06: ioport range 0x880-0x8ff has been reserved
[    0.238226] system 00:06: ioport range 0xc00-0xc7f could not be reserved
[    0.238229] system 00:06: ioport range 0x2000-0x20fe has been reserved
[    0.238233] system 00:06: iomem range 0xfff80000-0xffffffff has been reserved
[    0.238236] system 00:06: iomem range 0xffb80000-0xffbfffff has been reserved
[    0.238239] system 00:06: iomem range 0xffee0000-0xffefffff has been reserved
[    0.238242] system 00:06: iomem range 0xfed10000-0xfed3ffff has been reserved
[    0.238248] system 00:09: ioport range 0x250-0x253 has been reserved
[    0.238251] system 00:09: ioport range 0x256-0x25f has been reserved
[    0.238255] system 00:09: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.238258] system 00:09: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.238264] system 00:0a: iomem range 0xe0000000-0xefffffff has been reserved
[    0.238270] system 00:0b: iomem range 0x0-0x9ffff could not be reserved
[    0.238273] system 00:0b: iomem range 0xc0000-0xcffff could not be reserved
[    0.238276] system 00:0b: iomem range 0xe0000-0xfffff could not be reserved
[    0.238279] system 00:0b: iomem range 0x100000-0xbfffffff could not be reserved
[    0.238282] system 00:0b: iomem range 0xe0000000-0xffffffff could not be reserved
[    0.272921] AppArmor: AppArmor Filesystem Enabled
[    0.272959] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.272963] pci 0000:00:01.0:   IO window: 0xd000-0xdfff
[    0.272968] pci 0000:00:01.0:   MEM window: 0xfa000000-0xfdefffff
[    0.272973] pci 0000:00:01.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
[    0.272980] pci 0000:00:06.0: PCI bridge, secondary bus 0000:02
[    0.272982] pci 0000:00:06.0:   IO window: disabled
[    0.272987] pci 0000:00:06.0:   MEM window: 0xfdf00000-0xfdffffff
[    0.272992] pci 0000:00:06.0:   PREFETCH window: disabled
[    0.272996] pci 0000:00:07.0: PCI bridge, secondary bus 0000:03
[    0.273000] pci 0000:00:07.0:   IO window: 0xe000-0xefff
[    0.273005] pci 0000:00:07.0:   MEM window: 0xfe000000-0xfebfffff
[    0.273010] pci 0000:00:07.0:   PREFETCH window: 0x000000f6000000-0x000000f8ffffff
[    0.273026] pci 0000:00:01.0: setting latency timer to 64
[    0.273035] pci 0000:00:06.0: setting latency timer to 64
[    0.273045] pci 0000:00:07.0: setting latency timer to 64
[    0.273049] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.273052] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.273055] pci_bus 0000:01: resource 0 io:  [0xd000-0xdfff]
[    0.273057] pci_bus 0000:01: resource 1 mem: [0xfa000000-0xfdefffff]
[    0.273060] pci_bus 0000:01: resource 2 pref mem [0xd0000000-0xdfffffff]
[    0.273063] pci_bus 0000:02: resource 1 mem: [0xfdf00000-0xfdffffff]
[    0.273066] pci_bus 0000:03: resource 0 io:  [0xe000-0xefff]
[    0.273068] pci_bus 0000:03: resource 1 mem: [0xfe000000-0xfebfffff]
[    0.273071] pci_bus 0000:03: resource 2 pref mem [0xf6000000-0xf8ffffff]
[    0.273102] NET: Registered protocol family 2
[    0.273195] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.273519] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.274198] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.274612] TCP: Hash tables configured (established 131072 bind 65536)
[    0.274615] TCP reno registered
[    0.274691] NET: Registered protocol family 1
[    0.274761] Trying to unpack rootfs image as initramfs...
[    0.486801] Freeing initrd memory: 7464k freed
[    0.493729] Simple Boot Flag at 0x71 set to 0x1
[    0.493962] cpufreq-nforce2: No nForce2 chipset.
[    0.494005] Scanning for low memory corruption every 60 seconds
[    0.494160] audit: initializing netlink socket (disabled)
[    0.494192] type=2000 audit(1259587674.492:1): initialized
[    0.502112] Switched to high resolution mode on CPU 1
[    0.503905] highmem bounce pool size: 64 pages
[    0.503911] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.504014] Switched to high resolution mode on CPU 0
[    0.505547] VFS: Disk quotas dquot_6.5.2
[    0.505614] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.506225] fuse init (API version 7.12)
[    0.506319] msgmni has been set to 1679
[    0.506588] alg: No test for stdrng (krng)
[    0.506605] io scheduler noop registered
[    0.506607] io scheduler anticipatory registered
[    0.506609] io scheduler deadline registered
[    0.506652] io scheduler cfq registered (default)
[    0.576045] pci 0000:01:00.0: Boot video device
[    0.576165]   alloc irq_desc for 24 on node -1
[    0.576167]   alloc kstat_irqs on node -1
[    0.576181] pcieport-driver 0000:00:01.0: irq 24 for MSI/MSI-X
[    0.576191] pcieport-driver 0000:00:01.0: setting latency timer to 64
[    0.576313]   alloc irq_desc for 25 on node -1
[    0.576315]   alloc kstat_irqs on node -1
[    0.576324] pcieport-driver 0000:00:06.0: irq 25 for MSI/MSI-X
[    0.576333] pcieport-driver 0000:00:06.0: setting latency timer to 64
[    0.576461]   alloc irq_desc for 26 on node -1
[    0.576463]   alloc kstat_irqs on node -1
[    0.576472] pcieport-driver 0000:00:07.0: irq 26 for MSI/MSI-X
[    0.576481] pcieport-driver 0000:00:07.0: setting latency timer to 64
[    0.576575] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.576622] Firmware did not grant requested _OSC control
[    0.576665] Firmware did not grant requested _OSC control
[    0.576685] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.576917] ACPI: AC Adapter [AC0] (on-line)
[    0.576985] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    0.576991] ACPI: Power Button [PWRF]
[    0.577057] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.577060] ACPI: Power Button [PWRB]
[    0.577106] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    0.577112] ACPI: Sleep Button [SLPB]
[    0.577157] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input3
[    0.578376] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    0.587004] ACPI: Lid Switch [LID]
[    0.587903] ACPI: SSDT bffce390 001C0 (v01  PmRef  Cpu0Ist 00003000 INTL 20051117)
[    0.588656] ACPI: SSDT bffce5e0 006D9 (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.589186] Monitor-Mwait will be used to enter C-1 state
[    0.589212] Monitor-Mwait will be used to enter C-2 state
[    0.589221] Marking TSC unstable due to TSC halts in idle
[    0.589237] ACPI: CPU0 (power states: C1[C1] C2[C2])
[    0.589263] processor LNXCPU:00: registered as cooling_device0
[    0.589267] ACPI: Processor [CPU0] (supports 8 throttling states)
[    0.589668] ACPI: SSDT bffce2c0 000C8 (v01  PmRef  Cpu1Ist 00003000 INTL 20051117)
[    0.590084] ACPI: SSDT bffce550 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20051117)
[    0.590678] ACPI: CPU1 (power states: C1[C1] C2[C2])
[    0.590697] processor LNXCPU:01: registered as cooling_device1
[    0.590701] ACPI: Processor [CPU1] (supports 8 throttling states)
[    0.595280] thermal LNXTHERM:01: registered as thermal_zone0
[    0.595288] ACPI: Thermal Zone [THRM] (58 C)
[    0.595344] isapnp: Scanning for PnP cards...
[    0.663036] ACPI: Battery Slot [BAT0] (battery present)
[    0.948967] isapnp: No Plug & Play device found
[    0.950195] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.951623] brd: module loaded
[    0.952105] loop: module loaded
[    0.952178] input: Macintosh mouse button emulation as /devices/virtual/input/input4
[    0.952360] sata_sis 0000:00:05.0: version 1.0
[    0.952376]   alloc irq_desc for 17 on node -1
[    0.952378]   alloc kstat_irqs on node -1
[    0.952383] sata_sis 0000:00:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.952388] sata_sis 0000:00:05.0: Detected SiS 1183/966/966L/968/680 controller in PATA mode
[    0.952492] scsi0 : sata_sis
[    0.952580] scsi1 : sata_sis
[    0.953183] ata1: PATA max UDMA/133 cmd 0xc800 ctl 0xc400 bmdma 0xb800 irq 17
[    0.953186] ata2: PATA max UDMA/133 cmd 0xc000 ctl 0xbc00 bmdma 0xb808 irq 17
[    0.953632] pata_sis 0000:00:02.5: version 0.5.2
[    0.953723] scsi2 : pata_sis
[    0.953784] scsi3 : pata_sis
[    0.954336] ata3: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xfff0 irq 14
[    0.954339] ata4: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xfff8 irq 15
[    0.954697] Fixed MDIO Bus: probed
[    0.954733] PPP generic driver version 2.4.2
[    0.954823] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.954840]   alloc irq_desc for 22 on node -1
[    0.954842]   alloc kstat_irqs on node -1
[    0.954846] ehci_hcd 0000:00:03.3: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    0.954858] ehci_hcd 0000:00:03.3: EHCI Host Controller
[    0.954907] ehci_hcd 0000:00:03.3: new USB bus registered, assigned bus number 1
[    0.954947] ehci_hcd 0000:00:03.3: irq 22, io mem 0xf9ffd000
[    0.964012] ehci_hcd 0000:00:03.3: USB 2.0 started, EHCI 1.00
[    0.964098] usb usb1: configuration #1 chosen from 1 choice
[    0.964133] hub 1-0:1.0: USB hub found
[    0.964142] hub 1-0:1.0: 8 ports detected
[    0.964204] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.964218]   alloc irq_desc for 20 on node -1
[    0.964220]   alloc kstat_irqs on node -1
[    0.964224] ohci_hcd 0000:00:03.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.964232] ohci_hcd 0000:00:03.0: OHCI Host Controller
[    0.964263] ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus number 2
[    0.964280] ohci_hcd 0000:00:03.0: irq 20, io mem 0xf9fff000
[    1.022063] usb usb2: configuration #1 chosen from 1 choice
[    1.022100] hub 2-0:1.0: USB hub found
[    1.022109] hub 2-0:1.0: 4 ports detected
[    1.022155]   alloc irq_desc for 21 on node -1
[    1.022157]   alloc kstat_irqs on node -1
[    1.022161] ohci_hcd 0000:00:03.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    1.022169] ohci_hcd 0000:00:03.1: OHCI Host Controller
[    1.022209] ohci_hcd 0000:00:03.1: new USB bus registered, assigned bus number 3
[    1.022226] ohci_hcd 0000:00:03.1: irq 21, io mem 0xf9ffe000
[    1.078061] usb usb3: configuration #1 chosen from 1 choice
[    1.078088] hub 3-0:1.0: USB hub found
[    1.078096] hub 3-0:1.0: 4 ports detected
[    1.078146] uhci_hcd: USB Universal Host Controller Interface driver
[    1.078221] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    1.080976] i8042.c: Detected active multiplexing controller, rev 1.1.
[    1.081959] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.081965] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    1.081968] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    1.081971] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    1.081974] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    1.082024] mice: PS/2 mouse device common for all mice
[    1.082149] rtc_cmos 00:08: RTC can wake from S4
[    1.082180] rtc_cmos 00:08: rtc core: registered rtc_cmos as rtc0
[    1.082200] rtc0: alarms up to one year, 114 bytes nvram, hpet irqs
[    1.082296] device-mapper: uevent: version 1.0.3
[    1.082394] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[    1.082473] device-mapper: multipath: version 1.1.0 loaded
[    1.082476] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.082591] EISA: Probing bus 0 at eisa.0
[    1.082600] Cannot allocate resource for EISA slot 2
[    1.082623] EISA: Detected 0 cards.
[    1.082764] cpuidle: using governor ladder
[    1.082858] cpuidle: using governor menu
[    1.083375] TCP cubic registered
[    1.083535] NET: Registered protocol family 10
[    1.084011] lo: Disabled Privacy Extensions
[    1.084356] NET: Registered protocol family 17
[    1.084375] Bluetooth: L2CAP ver 2.13
[    1.084377] Bluetooth: L2CAP socket layer initialized
[    1.084380] Bluetooth: SCO (Voice Link) ver 0.6
[    1.084382] Bluetooth: SCO socket layer initialized
[    1.084412] Bluetooth: RFCOMM TTY layer initialized
[    1.084415] Bluetooth: RFCOMM socket layer initialized
[    1.084417] Bluetooth: RFCOMM ver 1.11
[    1.084789] Using IPI No-Shortcut mode
[    1.084848] PM: Resume from disk failed.
[    1.084860] registered taskstats version 1
[    1.084947]   Magic number: 1:590:484
[    1.085021] rtc_cmos 00:08: setting system clock to 2009-11-30 13:27:56 UTC (1259587676)
[    1.085025] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.085026] EDD information not available.
[    1.119297] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[    1.163468] ata1.00: ATA-8: ST9500325AS, 0002SDM1, max UDMA/133
[    1.163472] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.176633] ata1.00: configured for UDMA/133
[    1.176771] scsi 0:0:0:0: Direct-Access     ATA      ST9500325AS      0002 PQ: 0 ANSI: 5
[    1.176879] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.176916] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    1.176961] sd 0:0:0:0: [sda] Write Protect is off
[    1.176963] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.176986] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.177111]  sda: sda1 sda2 sda3 < sda5 sda6 sda7 sda8 >
[    1.263857] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.332029] usb 1-5: new high speed USB device using ehci_hcd and address 3
[    1.340237] ata2.00: ATAPI: HL-DT-ST BDDVDRW CT10N, WR06, max UDMA/133
[    1.356255] ata2.00: configured for UDMA/133
[    1.362003] scsi 1:0:0:0: CD-ROM            HL-DT-ST BDDVDRW CT10N    WR06 PQ: 0 ANSI: 5
[    1.374133] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.374138] Uniform CD-ROM driver Revision: 3.20
[    1.374221] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.374267] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.374305] ata4: port disabled. ignoring.
[    1.374335] Freeing unused kernel memory: 540k freed
[    1.374717] Write protecting the kernel text: 4568k
[    1.374761] Write protecting the kernel read-only data: 1836k
[    1.480593] Linux agpgart interface v0.103
[    1.518712] acpi device:19: registered as cooling_device2
[    1.518835] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:15/device:16/input/input6
[    1.518882] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[    1.532688] usb 1-5: configuration #1 chosen from 1 choice
[    1.700028] usb 3-2: new low speed USB device using ohci_hcd and address 2
[    2.047168] usb 3-2: configuration #1 chosen from 1 choice
[    2.059151] usbcore: registered new interface driver hiddev
[    2.066324] input: Razer Razer 1600dpi 3 button optical mouse as /devices/pci0000:00/0000:00:03.1/usb3/3-2/3-2:1.0/input/input7
[    2.066397] generic-usb 0003:1532:0003.0001: input,hidraw0: USB HID v1.10 Mouse [Razer Razer 1600dpi 3 button optical mouse] on usb-0000:00:03.1-2/input0
[    2.066410] usbcore: registered new interface driver usbhid
[    2.066413] usbhid: v2.6:USB HID core driver
[    3.467007] PM: Starting manual resume from disk
[    3.467011] PM: Resume from partition 8:8
[    3.467013] PM: Checking hibernation image.
[    3.467372] PM: Resume from disk failed.
[    3.470868] EXT4-fs (sda6): INFO: recovery required on readonly filesystem
[    3.470873] EXT4-fs (sda6): write access will be enabled during recovery
[    3.486558] EXT4-fs (sda6): barriers enabled
[    4.247609] kjournald2 starting: pid 386, dev sda6:8, commit interval 5 seconds
[    4.247634] EXT4-fs (sda6): delayed allocation enabled
[    4.247639] EXT4-fs: file extents enabled
[    4.249034] EXT4-fs: mballoc enabled
[    4.249050] EXT4-fs (sda6): orphan cleanup on readonly fs
[    4.249056] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 128
[    4.249083] EXT4-fs (sda6): 1 orphan inode deleted
[    4.249086] EXT4-fs (sda6): recovery complete
[    4.538034] EXT4-fs (sda6): mounted filesystem with ordered data mode
[    5.145818] type=1505 audit(1259587680.559:2): operation="profile_load" pid=409 name=/usr/share/gdm/guest-session/Xsession
[    5.149197] type=1505 audit(1259587680.562:3): operation="profile_load" pid=410 name=/sbin/dhclient3
[    5.149919] type=1505 audit(1259587680.562:4): operation="profile_load" pid=410 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    5.150312] type=1505 audit(1259587680.562:5): operation="profile_load" pid=410 name=/usr/lib/connman/scripts/dhclient-script
[    5.199028] type=1505 audit(1259587680.610:6): operation="profile_load" pid=411 name=/usr/bin/evince
[    5.210605] type=1505 audit(1259587680.622:7): operation="profile_load" pid=411 name=/usr/bin/evince-previewer
[    5.217445] type=1505 audit(1259587680.630:8): operation="profile_load" pid=411 name=/usr/bin/evince-thumbnailer
[    5.240927] type=1505 audit(1259587680.654:9): operation="profile_load" pid=413 name=/usr/lib/cups/backend/cups-pdf
[    5.976445] Adding 2104472k swap on /dev/sda8.  Priority:-1 extents:1 across:2104472k 
[    6.360544] EXT4-fs (sda6): internal journal on sda6:8
[    6.968818] EXT4-fs (sda7): barriers enabled
[    6.969689] kjournald2 starting: pid 467, dev sda7:8, commit interval 5 seconds
[    6.970145] EXT4-fs (sda7): internal journal on sda7:8
[    6.970149] EXT4-fs (sda7): delayed allocation enabled
[    6.970153] EXT4-fs: file extents enabled
[    6.975594] EXT4-fs: mballoc enabled
[    6.975610] EXT4-fs (sda7): mounted filesystem with ordered data mode
[    7.241025] udev: starting version 147
[    8.328072] cfg80211: Calling CRDA to update world regulatory domain
[    8.612370] Linux video capture interface: v2.00
[    8.803439] lp: driver loaded but no devices found
[    8.834715] asus_laptop: Asus Laptop Support version 0.42
[    8.839451] asus_laptop:   F50Sf model detected
[    8.847716] input: Asus Laptop extra buttons as /devices/virtual/input/input8
[    8.847851] asus_laptop: Brightness ignored, must be controlled by ACPI video driver
[    9.080519] cfg80211: World regulatory domain updated:
[    9.080523]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[    9.080527]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    9.080531]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    9.080539]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    9.080542]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    9.080544]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    9.519892] sis190 Gigabit Ethernet driver 1.3 loaded.
[    9.519918]   alloc irq_desc for 19 on node -1
[    9.519920]   alloc kstat_irqs on node -1
[    9.519929] sis190 0000:00:04.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    9.519941] sis190 0000:00:04.0: setting latency timer to 64
[    9.519953] 0000:00:04.0: Read MAC address from EEPROM
[    9.519955] 0000:00:04.0: Error EEPROM read 0.
[    9.519959] 0000:00:04.0: Read MAC address from APC.
[    9.552021] 0000:00:04.0: unknown PHY 0x4d:0xd040 transceiver at address 0
[   10.121678] 0000:00:04.0: SiS 191 PCI Gigabit Ethernet adapter at f804ac00 (IRQ: 19), 00:26:18:86:a2:b7
[   10.121682] eth0: RGMII mode.
[   10.121687] eth0: Enabling Auto-negotiation.
[   10.488568] nvidia: module license 'NVIDIA' taints kernel.
[   10.488574] Disabling lock debugging due to kernel taint
[   10.659390] uvcvideo: Found UVC 1.00 device USB2.0 UVC 1.3M WebCam (064e:a116)
[   10.676508] input: USB2.0 UVC 1.3M WebCam as /devices/pci0000:00/0000:00:03.3/usb1/1-5/1-5:1.0/input/input9
[   10.676555] usbcore: registered new interface driver uvcvideo
[   10.676558] USB Video Class driver (v0.1.0)
[   10.743006]   alloc irq_desc for 16 on node -1
[   10.743010]   alloc kstat_irqs on node -1
[   10.743017] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   10.743027] nvidia 0000:01:00.0: setting latency timer to 64
[   10.743172] NVRM: loading NVIDIA UNIX x86 Kernel Module  185.18.36  Fri Aug 14 17:18:04 PDT 2009
[   11.224200] ip_tables: (C) 2000-2006 Netfilter Core Team
[   11.247249] ath9k 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   11.247262] ath9k 0000:02:00.0: setting latency timer to 64
[   11.296996] ath: EEPROM regdomain: 0x60
[   11.296998] ath: EEPROM indicates we should expect a direct regpair map
[   11.297003] ath: Country alpha2 being used: 00
[   11.297005] ath: Regpair used: 0x60
[   11.376026] Synaptics Touchpad, model: 1, fw: 6.1, id: 0xa3a0b3, caps: 0xa04713/0x10008
[   11.413701] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input10
[   11.717774] phy0: Selected rate control algorithm 'ath9k_rate_control'
[   11.718489] Registered led device: ath9k-phy0::radio
[   11.718506] Registered led device: ath9k-phy0::assoc
[   11.718522] Registered led device: ath9k-phy0::tx
[   11.718537] Registered led device: ath9k-phy0::rx
[   11.718558] phy0: Atheros AR9285 MAC/BB Rev:2 AR5133 RF Rev:e0: mem=0xf97c0000, irq=16
[   12.778397] __ratelimit: 6 callbacks suppressed
[   12.778400] type=1505 audit(1259584088.190:12): operation="profile_replace" pid=847 name=/usr/share/gdm/guest-session/Xsession
[   12.780079] type=1505 audit(1259584088.194:13): operation="profile_replace" pid=848 name=/sbin/dhclient3
[   12.780889] type=1505 audit(1259584088.194:14): operation="profile_replace" pid=848 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   12.781289] type=1505 audit(1259584088.194:15): operation="profile_replace" pid=848 name=/usr/lib/connman/scripts/dhclient-script
[   12.786480] type=1505 audit(1259584088.198:16): operation="profile_replace" pid=849 name=/usr/bin/evince
[   12.798098] type=1505 audit(1259584088.210:17): operation="profile_replace" pid=849 name=/usr/bin/evince-previewer
[   12.804966] type=1505 audit(1259584088.218:18): operation="profile_replace" pid=849 name=/usr/bin/evince-thumbnailer
[   12.815685]   alloc irq_desc for 18 on node -1
[   12.815688]   alloc kstat_irqs on node -1
[   12.815698] HDA Intel 0000:00:0f.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   12.815737] HDA Intel 0000:00:0f.0: setting latency timer to 64
[   12.818518] type=1505 audit(1259584088.230:19): operation="profile_replace" pid=851 name=/usr/lib/cups/backend/cups-pdf
[   12.819456] type=1505 audit(1259584088.230:20): operation="profile_replace" pid=851 name=/usr/sbin/cupsd
[   12.822351] type=1505 audit(1259584088.234:21): operation="profile_replace" pid=852 name=/usr/sbin/tcpdump
[   12.892058] hda_codec: Unknown model for ALC663, trying auto-probe from BIOS...
[   12.892963] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:0f.0/input/input11
[   14.931676] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   14.969283] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   17.585139] ppdev: user-space parallel port driver
[   24.952022] eth0: auto-negotiating...
[   25.050214] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.
[   34.976019] eth0: auto-negotiating...
[   45.000020] eth0: auto-negotiating...
[   55.024022] eth0: auto-negotiating...
[   65.048024] eth0: auto-negotiating...
[   75.072022] eth0: auto-negotiating...
[   85.096021] eth0: auto-negotiating...
[   95.120027] eth0: auto-negotiating...
[  105.144026] eth0: auto-negotiating...
[  115.168023] eth0: auto-negotiating...
[  125.192023] eth0: auto-negotiating...
[  135.216026] eth0: auto-negotiating...
[  145.240022] eth0: auto-negotiating...
[  155.264024] eth0: auto-negotiating...
[  165.288037] eth0: auto-negotiating...
[  175.312022] eth0: auto-negotiating...
[  185.336023] eth0: auto-negotiating...
[  195.360026] eth0: auto-negotiating...
[  205.384022] eth0: auto-negotiating...
[  215.408023] eth0: auto-negotiating...
[  225.432025] eth0: auto-negotiating...
[  235.456023] eth0: auto-negotiating...
[  240.203410] wlan0: authenticate with AP 00:24:fe:04:43:28
[  240.207774] wlan0: authenticated
[  240.207778] wlan0: associate with AP 00:24:fe:04:43:28
[  240.211548] wlan0: RX AssocResp from 00:24:fe:04:43:28 (capab=0x411 status=0 aid=2)
[  240.211552] wlan0: associated
[  240.212085] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  240.294707] padlock: VIA PadLock not detected.
[  245.480028] eth0: auto-negotiating...
[  250.828018] wlan0: no IPv6 routers present
[  255.504020] eth0: auto-negotiating...
[  265.528022] eth0: auto-negotiating...
[  275.552023] eth0: auto-negotiating...
[  285.576026] eth0: auto-negotiating...
[  295.600022] eth0: auto-negotiating...
[  305.624022] eth0: auto-negotiating...
[  315.664018] eth0: auto-negotiating...
[  325.688022] eth0: auto-negotiating...
[  335.724031] eth0: auto-negotiating...
[  345.748030] eth0: auto-negotiating...
[  355.776027] eth0: auto-negotiating...
[  365.800219] eth0: auto-negotiating...
[  375.824025] eth0: auto-negotiating...
[  385.848030] eth0: auto-negotiating...
[  395.884043] eth0: auto-negotiating...
[  405.904029] eth0: auto-negotiating...
[  415.932020] eth0: auto-negotiating...
[  425.956028] eth0: auto-negotiating...
[  435.976030] eth0: auto-negotiating...
[  446.000019] eth0: auto-negotiating...
[  456.024136] eth0: auto-negotiating...
[  466.048021] eth0: auto-negotiating...
[  476.072021] eth0: auto-negotiating...
[  486.096023] eth0: auto-negotiating...
[  496.120025] eth0: auto-negotiating...
[  506.150339] eth0: auto-negotiating...
[  516.172026] eth0: auto-negotiating...
[  526.196025] eth0: auto-negotiating...
[  536.220023] eth0: auto-negotiating...
[  546.244026] eth0: auto-negotiating...
[  556.268024] eth0: auto-negotiating...
[  566.292021] eth0: auto-negotiating...
[  576.316026] eth0: auto-negotiating...

tail -n 200 /var/log/messages

> 
Nov 30 13:35:13 andibu2 rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="725" x-info="http://www.rsyslog.com"] rsyslogd was HUPed, type 'lightweight'.
Nov 30 13:35:13 andibu2 rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="725" x-info="http://www.rsyslog.com"] rsyslogd was HUPed, type 'lightweight'.
Nov 30 13:35:14 andibu2 kernel: [  446.000019] eth0: auto-negotiating...
Nov 30 13:35:25 andibu2 kernel: [  456.024136] eth0: auto-negotiating...
Nov 30 13:35:35 andibu2 kernel: [  466.048021] eth0: auto-negotiating...
Nov 30 13:35:45 andibu2 kernel: [  476.072021] eth0: auto-negotiating...
Nov 30 13:35:55 andibu2 kernel: [  486.096023] eth0: auto-negotiating...
Nov 30 13:36:05 andibu2 kernel: [  496.120025] eth0: auto-negotiating...
Nov 30 13:36:15 andibu2 kernel: [  506.150339] eth0: auto-negotiating...
Nov 30 13:36:25 andibu2 kernel: [  516.172026] eth0: auto-negotiating...
Nov 30 13:36:35 andibu2 kernel: [  526.196025] eth0: auto-negotiating...
Nov 30 13:36:45 andibu2 kernel: [  536.220023] eth0: auto-negotiating...
Nov 30 13:36:55 andibu2 kernel: [  546.244026] eth0: auto-negotiating...
Nov 30 13:37:05 andibu2 kernel: [  556.268024] eth0: auto-negotiating...
Nov 30 13:37:15 andibu2 kernel: [  566.292021] eth0: auto-negotiating...
Nov 30 13:37:25 andibu2 kernel: [  576.316026] eth0: auto-negotiating...
Nov 30 13:37:35 andibu2 kernel: [  586.340027] eth0: auto-negotiating...
Nov 30 13:37:45 andibu2 kernel: [  596.364029] eth0: auto-negotiating...
Nov 30 13:37:55 andibu2 kernel: [  606.388024] eth0: auto-negotiating...
Nov 30 13:38:05 andibu2 kernel: [  616.412021] eth0: auto-negotiating...
Nov 30 13:38:15 andibu2 kernel: [  626.440033] eth0: auto-negotiating...
Nov 30 13:38:25 andibu2 kernel: [  636.460029] eth0: auto-negotiating...
Nov 30 13:38:35 andibu2 kernel: [  646.484019] eth0: auto-negotiating...
Nov 30 13:38:45 andibu2 kernel: [  656.508025] eth0: auto-negotiating...
Nov 30 13:38:55 andibu2 kernel: [  666.532026] eth0: auto-negotiating...
Nov 30 13:39:05 andibu2 kernel: [  676.556022] eth0: auto-negotiating...
Nov 30 13:39:15 andibu2 kernel: [  686.580030] eth0: auto-negotiating...
Nov 30 13:39:25 andibu2 kernel: [  696.604026] eth0: auto-negotiating...
Nov 30 13:39:35 andibu2 kernel: [  706.628019] eth0: auto-negotiating...
Nov 30 13:39:45 andibu2 kernel: [  716.652023] eth0: auto-negotiating...
Nov 30 13:39:55 andibu2 kernel: [  726.676027] eth0: auto-negotiating...
Nov 30 13:40:05 andibu2 kernel: [  736.700021] eth0: auto-negotiating...
Nov 30 13:40:15 andibu2 kernel: [  746.724029] eth0: auto-negotiating...
Nov 30 13:40:25 andibu2 kernel: [  756.748028] eth0: auto-negotiating...
Nov 30 13:40:35 andibu2 kernel: [  766.772022] eth0: auto-negotiating...
Nov 30 13:40:45 andibu2 kernel: [  776.796030] eth0: auto-negotiating...
Nov 30 13:40:55 andibu2 kernel: [  786.820028] eth0: auto-negotiating...
Nov 30 13:41:05 andibu2 kernel: [  796.844020] eth0: auto-negotiating...
Nov 30 13:41:15 andibu2 kernel: [  806.868027] eth0: auto-negotiating...
Nov 30 13:41:25 andibu2 kernel: [  816.892026] eth0: auto-negotiating...
Nov 30 13:41:35 andibu2 kernel: [  826.916025] eth0: auto-negotiating...
Nov 30 13:41:45 andibu2 kernel: [  836.940042] eth0: auto-negotiating...
Nov 30 13:41:55 andibu2 kernel: [  846.964026] eth0: auto-negotiating...
Nov 30 13:42:05 andibu2 kernel: [  856.988020] eth0: auto-negotiating...
Nov 30 13:42:15 andibu2 kernel: [  867.016029] eth0: auto-negotiating...
Nov 30 13:42:26 andibu2 kernel: [  877.040020] eth0: auto-negotiating...
Nov 30 13:42:36 andibu2 kernel: [  887.064022] eth0: auto-negotiating...
Nov 30 13:42:46 andibu2 kernel: [  897.088027] eth0: auto-negotiating...
Nov 30 13:42:56 andibu2 kernel: [  907.112024] eth0: auto-negotiating...
Nov 30 13:43:06 andibu2 kernel: [  917.136026] eth0: auto-negotiating...
Nov 30 13:43:16 andibu2 kernel: [  927.160025] eth0: auto-negotiating...
Nov 30 13:43:26 andibu2 kernel: [  937.184021] eth0: auto-negotiating...
Nov 30 13:43:36 andibu2 kernel: [  947.208041] eth0: auto-negotiating...
Nov 30 13:43:46 andibu2 kernel: [  957.232026] eth0: auto-negotiating...
Nov 30 13:43:56 andibu2 kernel: [  967.256022] eth0: auto-negotiating...
Nov 30 13:44:06 andibu2 kernel: [  977.280027] eth0: auto-negotiating...
Nov 30 13:44:16 andibu2 kernel: [  987.304028] eth0: auto-negotiating...
Nov 30 13:44:26 andibu2 kernel: [  997.328025] eth0: auto-negotiating...
Nov 30 13:44:36 andibu2 kernel: [ 1007.352026] eth0: auto-negotiating...
Nov 30 13:44:46 andibu2 kernel: [ 1017.376027] eth0: auto-negotiating...
Nov 30 13:44:56 andibu2 kernel: [ 1027.400022] eth0: auto-negotiating...
Nov 30 13:45:06 andibu2 kernel: [ 1037.424023] eth0: auto-negotiating...
Nov 30 13:45:16 andibu2 kernel: [ 1047.448030] eth0: auto-negotiating...
Nov 30 13:45:26 andibu2 kernel: [ 1057.472018] eth0: auto-negotiating...
Nov 30 13:45:36 andibu2 kernel: [ 1067.496023] eth0: auto-negotiating...
Nov 30 13:45:46 andibu2 kernel: [ 1077.520028] eth0: auto-negotiating...
Nov 30 13:45:56 andibu2 kernel: [ 1087.544022] eth0: auto-negotiating...
Nov 30 13:46:06 andibu2 kernel: [ 1097.568029] eth0: auto-negotiating...
Nov 30 13:46:16 andibu2 kernel: [ 1107.592026] eth0: auto-negotiating...
Nov 30 13:46:26 andibu2 kernel: [ 1117.616021] eth0: auto-negotiating...
Nov 30 13:46:36 andibu2 kernel: [ 1127.640028] eth0: auto-negotiating...
Nov 30 13:46:46 andibu2 kernel: [ 1137.664026] eth0: auto-negotiating...
Nov 30 13:46:56 andibu2 kernel: [ 1147.688022] eth0: auto-negotiating...
Nov 30 13:47:06 andibu2 kernel: [ 1157.712030] eth0: auto-negotiating...
Nov 30 13:47:16 andibu2 kernel: [ 1167.736030] eth0: auto-negotiating...
Nov 30 13:47:26 andibu2 kernel: [ 1177.760023] eth0: auto-negotiating...
Nov 30 13:47:36 andibu2 kernel: [ 1187.784024] eth0: auto-negotiating...
Nov 30 13:47:46 andibu2 kernel: [ 1197.808024] eth0: auto-negotiating...
Nov 30 13:47:56 andibu2 kernel: [ 1207.832021] eth0: auto-negotiating...
Nov 30 13:48:06 andibu2 kernel: [ 1217.856027] eth0: auto-negotiating...
Nov 30 13:48:16 andibu2 kernel: [ 1227.880054] eth0: auto-negotiating...
Nov 30 13:48:26 andibu2 kernel: [ 1237.904022] eth0: auto-negotiating...
Nov 30 13:48:36 andibu2 kernel: [ 1247.928023] eth0: auto-negotiating...
Nov 30 13:48:46 andibu2 kernel: [ 1257.952028] eth0: auto-negotiating...
Nov 30 13:48:56 andibu2 kernel: [ 1267.976027] eth0: auto-negotiating...
Nov 30 13:49:06 andibu2 kernel: [ 1278.000174] eth0: auto-negotiating...
Nov 30 13:49:17 andibu2 kernel: [ 1288.024027] eth0: auto-negotiating...
Nov 30 13:49:27 andibu2 kernel: [ 1298.048485] eth0: auto-negotiating...
Nov 30 13:49:37 andibu2 kernel: [ 1308.072028] eth0: auto-negotiating...
Nov 30 13:49:47 andibu2 kernel: [ 1318.096019] eth0: auto-negotiating...
Nov 30 13:49:57 andibu2 kernel: [ 1328.120022] eth0: auto-negotiating...
Nov 30 13:50:07 andibu2 kernel: [ 1338.148787] eth0: auto-negotiating...
Nov 30 13:50:17 andibu2 kernel: [ 1348.172023] eth0: auto-negotiating...
Nov 30 13:50:27 andibu2 kernel: [ 1358.196028] eth0: auto-negotiating...
Nov 30 13:50:37 andibu2 kernel: [ 1368.220029] eth0: auto-negotiating...
Nov 30 13:50:47 andibu2 kernel: [ 1378.244023] eth0: auto-negotiating...
Nov 30 13:50:57 andibu2 kernel: [ 1388.268094] eth0: auto-negotiating...
Nov 30 13:51:07 andibu2 kernel: [ 1398.292028] eth0: auto-negotiating...
Nov 30 13:51:17 andibu2 kernel: [ 1408.316026] eth0: auto-negotiating...
Nov 30 13:51:27 andibu2 kernel: [ 1418.340029] eth0: auto-negotiating...
Nov 30 13:51:37 andibu2 kernel: [ 1428.368016] eth0: auto-negotiating...
Nov 30 13:51:47 andibu2 kernel: [ 1438.388023] eth0: auto-negotiating...
Nov 30 13:51:57 andibu2 kernel: [ 1448.412989] eth0: auto-negotiating...
Nov 30 13:52:07 andibu2 kernel: [ 1458.436049] eth0: auto-negotiating...


lspci

> 
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 671MX
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS968 [MuTIOL Media IO] (rev 01)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] 191 Gigabit Ethernet Adapter (rev 02)
00:05.0 IDE interface: Silicon Integrated Systems [SiS] SATA Controller / IDE mode (rev 03)
00:06.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:07.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:0f.0 Audio device: Silicon Integrated Systems [SiS] Azalia Audio Controller
01:00.0 VGA compatible controller: nVidia Corporation Device 0654 (rev a1)
02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)




Sorry for this long quoted information,

thanks for the answers

---

### Post by ukripper on 2009-11-30
can you check whether your nvidia drivers are enabled. Go to System-->Administration-->Hardware drivers your card drivers should show up there.

---

### Post by ukripper on 2009-11-30
just noticed you have atheros wireless card. That is another culprit causing network manager to freeze, i have noticed that in the past. installing wicd would resolve your issue if it was atheros.

Run below command:
```
sudo apt-get install wicd
```

---

### Post by AndiBu on 2009-11-30
The Nvidia drivers are already enabeled and in use.

I also installed wicd ,

I'm going to tell if this was the reason for the crashes.

Thanks for your help =)

---

### Post by ukripper on 2009-11-30
Bis dann, auf wiedersehen! Let us know how you get on with it. We take it from da hin! lol just tryin my broken german.

---

