---
title: "Bootloading problem"
date: 2010-03-17
forum: New to Ubuntu
---

### Post by Rowen91 on 2010-03-17
Hi, I need some help, when evger i try to boot normaly in 9.10 I get to the white Ubuntu symbol but then my screen goes blank and it doesn't appear to load. But when I got into recovery mode I can load it up to the login space and then I have to do startx to get on. I think I messed up the kernal or something.

Any help would be appreciated.

---

### Post by coffeecat on 2010-03-17
Have you tried booting into an earlier kernel? They should still be there in the menu if you haven't uninstalled them.

---

### Post by Rowen91 on 2010-03-17
> **coffeecat said:**
> Have you tried booting into an earlier kernel? They should still be there in the menu if you haven't uninstalled them.
I have tried and failed i got the same result...

---

### Post by wjm on 2010-03-17
while in console type:

dmesg > dmesg.txt

Link the txt file here, someone can see why your X Server is failing to load (you may just have a jacked up ATI/nVidia driver)

---

### Post by Rowen91 on 2010-03-17
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
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000b7fb0000 (usable)
[    0.000000]  BIOS-e820: 00000000b7fb0000 - 00000000b7fbe000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000b7fbe000 - 00000000b7ff0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000b7ff0000 - 00000000b8000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] DMI present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0xb7fb0 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-DFFFF uncachable
[    0.000000]   E0000-EFFFF write-through
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 080000000 mask FC0000000 write-back
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009fc00 (usable)
[    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000b7fb0000 (usable)
[    0.000000]  modified: 00000000b7fb0000 - 00000000b7fbe000 (ACPI data)
[    0.000000]  modified: 00000000b7fbe000 - 00000000b7ff0000 (ACPI NVS)
[    0.000000]  modified: 00000000b7ff0000 - 00000000b8000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 10000-15000
[    0.000000] RAMDISK: 37867000 - 37fef729
[    0.000000] Allocated new RAMDISK: 008b2000 - 0103a729
[    0.000000] Move RAMDISK from 0000000037867000 - 0000000037fef728 to 008b2000 - 0103a728
[    0.000000] ACPI: RSDP 000f9ac0 00014 (v00 ACPIAM)
[    0.000000] ACPI: RSDT b7fb0000 0003C (v01 040308 RSDT0929 20080403 MSFT 00000097)
[    0.000000] ACPI: FACP b7fb0200 00084 (v01 040308 FACP0929 20080403 MSFT 00000097)
[    0.000000] ACPI: DSDT b7fb04a0 0580B (v01  1ADSY 1ADSY004 00000004 INTL 20051117)
[    0.000000] ACPI: FACS b7fbe000 00040
[    0.000000] ACPI: APIC b7fb0390 00080 (v01 040308 APIC0929 20080403 MSFT 00000097)
[    0.000000] ACPI: MCFG b7fb0410 0003C (v01 040308 OEMMCFG  20080403 MSFT 00000097)
[    0.000000] ACPI: WDRT b7fb0450 00047 (v01 040308 NV-WDRT  20080403 MSFT 00000097)
[    0.000000] ACPI: OEMB b7fbe040 00072 (v01 040308 OEMB0929 20080403 MSFT 00000097)
[    0.000000] ACPI: NVHD b7fbe0c0 00554 (v01 040308  NVHDCP  20080403 MSFT 00000097)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 2055MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000]   node 0 low ram: 00000000 - 377fe000
[    0.000000]   node 0 bootmap 00011000 - 00017f00
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008ad060]    TEXT DATA BSS ==> [0000100000 - 00008ad060]
[    0.000000]   #4 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #5 [00008ae000 - 00008b1180]              BRK ==> [00008ae000 - 00008b1180]
[    0.000000]   #6 [0000010000 - 0000011000]          PGTABLE ==> [0000010000 - 0000011000]
[    0.000000]   #7 [00008b2000 - 000103a729]      NEW RAMDISK ==> [00008b2000 - 000103a729]
[    0.000000]   #8 [0000011000 - 0000018000]          BOOTMAP ==> [0000011000 - 0000018000]
[    0.000000] found SMP MP-table at [c00ff780] ff780
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x000b7fb0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x000b7fb0
[    0.000000] On node 0 totalpages: 753471
[    0.000000] free_area_init_node: node 0, pgdat c0788900, node_mem_map c103b200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 4112 pages used for memmap
[    0.000000]   HighMem zone: 522146 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] Nvidia board detected. Ignoring ACPI timer override.
[    0.000000] If you got timer trouble try acpi_use_timer_override
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: BIOS IRQ0 pin2 override ignored.
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at b8000000 (gap: b8000000:46c00000)
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages at c274b000, static data 35612 bytes
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 747583
[    0.000000] Kernel command line: root=UUID=0570b72c-2438-464f-a1e5-0ec108d8a37c ro  single
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 15071360 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:000b7fb0)
[    0.000000] Memory: 2958072k/3014336k available (4578k kernel code, 54968k reserved, 2146k data, 540k init, 2105032k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc0792000 - 0xc0819000   ( 540 kB)
[    0.000000]       .data : 0xc0578948 - 0xc0791408   (2146 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0578948   (4578 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=128, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] NR_IRQS:2304 nr_irqs:440
[    0.000000] Fast TSC calibration failed
[    0.000000] TSC: PIT calibration matches PMTIMER. 2 loops
[    0.000000] Detected 3199.510 MHz processor.
[    0.000014] spurious 8259A interrupt: IRQ7.
[    0.003156] Console: colour VGA+ 80x25
[    0.003160] console [tty0] enabled
[    0.004008] Calibrating delay loop (skipped), value calculated using timer frequency.. 6399.02 BogoMIPS (lpj=12798040)
[    0.004158] Security Framework initialized
[    0.004243] AppArmor: AppArmor initialized
[    0.004315] Mount-cache hash table entries: 512
[    0.004523] Initializing cgroup subsys ns
[    0.004592] Initializing cgroup subsys cpuacct
[    0.004660] Initializing cgroup subsys memory
[    0.004730] Initializing cgroup subsys freezer
[    0.004796] Initializing cgroup subsys net_cls
[    0.004881] CPU: Trace cache: 12K uops, L1 D cache: 16K
[    0.004997] CPU: L2 cache: 2048K
[    0.005061] CPU: Physical Processor ID: 0
[    0.005126] CPU: Processor Core ID: 0
[    0.005192] mce: CPU supports 4 MCE banks
[    0.005268] CPU0: Thermal monitoring enabled (TM1)
[    0.005336] using mwait in idle threads.
[    0.005406] Performance Counters: no PMU driver, software counters only.
[    0.005528] Checking 'hlt' instruction... OK.
[    0.023354] ACPI: Core revision 20090521
[    0.033380] ..TIMER: vector=0x30 apic1=0 pin1=0 apic2=-1 pin2=-1
[    0.073133] CPU0: Intel(R) Pentium(R) D CPU 3.20GHz stepping 02
[    0.076001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 6384.59 BogoMIPS (lpj=12769188)
[    0.004000] CPU: Trace cache: 12K uops, L1 D cache: 16K
[    0.004000] CPU: L2 cache: 2048K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.004000] mce: CPU supports 4 MCE banks
[    0.004000] CPU1: Thermal monitoring enabled (TM1)
[    0.004000] x86 PAT enabled: cpu 1, old 0x7040600070406, new 0x7010600070106
[    0.161018] CPU1: Intel(R) Pentium(R) D CPU 3.20GHz stepping 02
[    0.161777] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.164019] Brought up 2 CPUs
[    0.164089] Total of 2 processors activated (12783.61 BogoMIPS).
[    0.164224] CPU0 attaching sched-domain:
[    0.164228]  domain 0: span 0-1 level CPU
[    0.164232]   groups: 0 1
[    0.164239] CPU1 attaching sched-domain:
[    0.164242]  domain 0: span 0-1 level CPU
[    0.164245]   groups: 1 0
[    0.164321] Booting paravirtualized kernel on bare hardware
[    0.164327] regulator: core version 0.5
[    0.164327] Time: 17:11:04  Date: 03/17/10
[    0.164327] NET: Registered protocol family 16
[    0.164450] EISA bus registered
[    0.164525] ACPI: bus type pci registered
[    0.164672] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.164742] PCI: Not using MMCONFIG.
[    0.168144] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=4
[    0.168212] PCI: Using configuration type 1 for base access
[    0.169603] bio: create slab <bio-0> at 0
[    0.173217] ACPI: EC: Look up EC in DSDT
[    0.184458] ACPI: Interpreter enabled
[    0.184526] ACPI: (supports S0 S1 S3 S4 S5)
[    0.184862] ACPI: Using IOAPIC for interrupt routing
[    0.184984] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.192158] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
[    0.192228] PCI: Using MMCONFIG for extended config space
[    0.202273] ACPI Warning: Incorrect checksum in table [OEMB] - A3, should be A2 20090521 tbutils-246
[    0.202735] ACPI: No dock devices found.
[    0.203257] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.204418] pci 0000:00:03.0: reg 10 io port: [0x4f00-0x4fff]
[    0.204481] pci 0000:00:03.1: reg 10 io port: [0x4900-0x493f]
[    0.204500] pci 0000:00:03.1: reg 20 io port: [0x4d00-0x4d3f]
[    0.204507] pci 0000:00:03.1: reg 24 io port: [0x4e00-0x4e3f]
[    0.204535] pci 0000:00:03.1: PME# supported from D3hot D3cold
[    0.204607] pci 0000:00:03.1: PME# disabled
[    0.204756] pci 0000:00:03.3: reg 10 32bit mmio: [0xfeb80000-0xfebfffff]
[    0.204968] pci 0000:00:04.0: reg 10 32bit mmio: [0xfeb7f000-0xfeb7ffff]
[    0.205008] pci 0000:00:04.0: supports D1 D2
[    0.205011] pci 0000:00:04.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.205082] pci 0000:00:04.0: PME# disabled
[    0.205182] pci 0000:00:04.1: reg 10 32bit mmio: [0xfeb7ec00-0xfeb7ecff]
[    0.205230] pci 0000:00:04.1: supports D1 D2
[    0.205232] pci 0000:00:04.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.205303] pci 0000:00:04.1: PME# disabled
[    0.205428] pci 0000:00:08.0: reg 20 io port: [0xffa0-0xffaf]
[    0.205488] pci 0000:00:09.0: reg 10 32bit mmio: [0xfeb78000-0xfeb7bfff]
[    0.205533] pci 0000:00:09.0: PME# supported from D3hot D3cold
[    0.205603] pci 0000:00:09.0: PME# disabled
[    0.205768] pci 0000:00:0b.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.205839] pci 0000:00:0b.0: PME# disabled
[    0.205964] pci 0000:00:0c.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.206034] pci 0000:00:0c.0: PME# disabled
[    0.206159] pci 0000:00:0d.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.206229] pci 0000:00:0d.0: PME# disabled
[    0.206333] pci 0000:00:0e.0: reg 10 io port: [0xe480-0xe487]
[    0.206340] pci 0000:00:0e.0: reg 14 io port: [0xe400-0xe403]
[    0.206346] pci 0000:00:0e.0: reg 18 io port: [0xe080-0xe087]
[    0.206352] pci 0000:00:0e.0: reg 1c io port: [0xe000-0xe003]
[    0.206358] pci 0000:00:0e.0: reg 20 io port: [0xdc00-0xdc0f]
[    0.206365] pci 0000:00:0e.0: reg 24 32bit mmio: [0xfeb7c000-0xfeb7dfff]
[    0.206428] pci 0000:00:0f.0: reg 10 32bit mmio: [0xfeb77000-0xfeb77fff]
[    0.206436] pci 0000:00:0f.0: reg 14 io port: [0xd880-0xd887]
[    0.206443] pci 0000:00:0f.0: reg 18 32bit mmio: [0xfeb7e800-0xfeb7e8ff]
[    0.206450] pci 0000:00:0f.0: reg 1c 32bit mmio: [0xfeb7e400-0xfeb7e40f]
[    0.206483] pci 0000:00:0f.0: supports D1 D2
[    0.206486] pci 0000:00:0f.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.206558] pci 0000:00:0f.0: PME# disabled
[    0.206656] pci 0000:00:10.0: reg 10 32bit mmio: [0xfd000000-0xfdffffff]
[    0.206666] pci 0000:00:10.0: reg 14 64bit mmio: [0xd0000000-0xdfffffff]
[    0.206675] pci 0000:00:10.0: reg 1c 64bit mmio: [0xfc000000-0xfcffffff]
[    0.206685] pci 0000:00:10.0: reg 30 32bit mmio: [0xfeb40000-0xfeb5ffff]
[    0.206786] pci 0000:00:0a.0: transparent bridge
[    0.207044] pci_bus 0000:00: on NUMA node 0
[    0.207050] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.207276] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.207404] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR10._PRT]
[    0.207480] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR11._PRT]
[    0.207556] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR12._PRT]
[    0.220539] ACPI: PCI Interrupt Link [LNKA] (IRQs 16 17 18 19) *0, disabled.
[    0.221266] ACPI: PCI Interrupt Link [LNKB] (IRQs 16 17 18 19) *0, disabled.
[    0.221989] ACPI: PCI Interrupt Link [LNKC] (IRQs 16 17 18 19) *0, disabled.
[    0.222711] ACPI: PCI Interrupt Link [LNKD] (IRQs 16 17 18 19) *0, disabled.
[    0.223432] ACPI: PCI Interrupt Link [LNEA] (IRQs 16 17 18 19) *0, disabled.
[    0.224161] ACPI: PCI Interrupt Link [LNEB] (IRQs 16 17 18 19) *0, disabled.
[    0.224882] ACPI: PCI Interrupt Link [LNEC] (IRQs 16 17 18 19) *0, disabled.
[    0.225607] ACPI: PCI Interrupt Link [LNED] (IRQs 16 17 18 19) *0, disabled.
[    0.226335] ACPI: PCI Interrupt Link [LUB0] (IRQs 20 21 22 23) *10
[    0.227015] ACPI: PCI Interrupt Link [LUB2] (IRQs 20 21 22 23) *11
[    0.227692] ACPI: PCI Interrupt Link [LMAC] (IRQs 20 21 22 23) *7
[    0.228333] ACPI: PCI Interrupt Link [LAZA] (IRQs 20 21 22 23) *7
[    0.229013] ACPI: PCI Interrupt Link [SGRU] (IRQs 20 21 22 23) *10
[    0.229694] ACPI: PCI Interrupt Link [LSMB] (IRQs 20 21 22 23) *11
[    0.230375] ACPI: PCI Interrupt Link [LPMU] (IRQs 20 21 22 23) *7
[    0.231062] ACPI: PCI Interrupt Link [LSA0] (IRQs 20 21 22 23) *5
[    0.232186] ACPI: PCI Interrupt Link [LATA] (IRQs 20 21 22 23) *0, disabled.
[    0.232865] SCSI subsystem initialized
[    0.232955] libata version 3.00 loaded.
[    0.232955] usbcore: registered new interface driver usbfs
[    0.232955] usbcore: registered new interface driver hub
[    0.232955] usbcore: registered new device driver usb
[    0.232955] ACPI: WMI: Mapper loaded
[    0.232955] PCI: Using ACPI for IRQ routing
[    0.244010] Bluetooth: Core ver 2.15
[    0.244092] NET: Registered protocol family 31
[    0.244092] Bluetooth: HCI device and connection manager initialized
[    0.244151] Bluetooth: HCI socket layer initialized
[    0.244217] NetLabel: Initializing
[    0.244281] NetLabel:  domain hash size = 128
[    0.244346] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.244425] NetLabel:  unlabeled traffic allowed by default
[    0.256012] pnp: PnP ACPI init
[    0.256086] ACPI: bus type pnp registered
[    0.262108] pnp: PnP ACPI: found 13 devices
[    0.262176] ACPI: ACPI bus type pnp unregistered
[    0.262243] PnPBIOS: Disabled by ACPI PNP
[    0.262321] system 00:05: ioport range 0x4d0-0x4d1 has been reserved
[    0.262390] system 00:05: ioport range 0x800-0x80f has been reserved
[    0.262459] system 00:05: ioport range 0x4000-0x407f has been reserved
[    0.262528] system 00:05: ioport range 0x4080-0x40ff has been reserved
[    0.262597] system 00:05: ioport range 0x4400-0x447f has been reserved
[    0.262666] system 00:05: ioport range 0x4480-0x44ff has been reserved
[    0.262735] system 00:05: ioport range 0x4800-0x487f has been reserved
[    0.262804] system 00:05: ioport range 0x4880-0x48ff has been reserved
[    0.262873] system 00:05: iomem range 0xfed02000-0xfed03fff has been reserved
[    0.262943] system 00:05: iomem range 0xfed04000-0xfed04fff has been reserved
[    0.263013] system 00:05: iomem range 0xfee01000-0xfeefffff has been reserved
[    0.263088] system 00:07: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.263168] system 00:07: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.263243] system 00:0a: ioport range 0xa00-0xa0f has been reserved
[    0.263312] system 00:0a: ioport range 0xa10-0xa1f has been reserved
[    0.263381] system 00:0a: ioport range 0xa20-0xa2f has been reserved
[    0.263449] system 00:0a: ioport range 0xa30-0xa3f has been reserved
[    0.263522] system 00:0b: iomem range 0xe0000000-0xefffffff has been reserved
[    0.263596] system 00:0c: iomem range 0x0-0x9ffff could not be reserved
[    0.263667] system 00:0c: iomem range 0xc0000-0xcffff could not be reserved
[    0.263736] system 00:0c: iomem range 0xe0000-0xfffff could not be reserved
[    0.263806] system 00:0c: iomem range 0x100000-0xbfffffff could not be reserved
[    0.263885] system 00:0c: iomem range 0xfec00000-0xffffffff could not be reserved
[    0.298684] AppArmor: AppArmor Filesystem Enabled
[    0.298797] pci 0000:00:0a.0: PCI bridge, secondary bus 0000:01
[    0.298865] pci 0000:00:0a.0:   IO window: disabled
[    0.298934] pci 0000:00:0a.0:   MEM window: disabled
[    0.299001] pci 0000:00:0a.0:   PREFETCH window: disabled
[    0.299070] pci 0000:00:0b.0: PCI bridge, secondary bus 0000:02
[    0.299137] pci 0000:00:0b.0:   IO window: disabled
[    0.299205] pci 0000:00:0b.0:   MEM window: disabled
[    0.299272] pci 0000:00:0b.0:   PREFETCH window: disabled
[    0.299341] pci 0000:00:0c.0: PCI bridge, secondary bus 0000:03
[    0.299408] pci 0000:00:0c.0:   IO window: disabled
[    0.299475] pci 0000:00:0c.0:   MEM window: disabled
[    0.299543] pci 0000:00:0c.0:   PREFETCH window: disabled
[    0.299611] pci 0000:00:0d.0: PCI bridge, secondary bus 0000:04
[    0.299678] pci 0000:00:0d.0:   IO window: disabled
[    0.299746] pci 0000:00:0d.0:   MEM window: disabled
[    0.299813] pci 0000:00:0d.0:   PREFETCH window: disabled
[    0.299888] pci 0000:00:0a.0: setting latency timer to 64
[    0.299897] pci 0000:00:0b.0: setting latency timer to 64
[    0.299905] pci 0000:00:0c.0: setting latency timer to 64
[    0.299913] pci 0000:00:0d.0: setting latency timer to 64
[    0.299919] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.299922] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.299926] pci_bus 0000:01: resource 3 io:  [0x00-0xffff]
[    0.299929] pci_bus 0000:01: resource 4 mem: [0x000000-0xffffffff]
[    0.299974] NET: Registered protocol family 2
[    0.300160] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.300631] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.301248] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.301585] TCP: Hash tables configured (established 131072 bind 65536)
[    0.301653] TCP reno registered
[    0.301803] NET: Registered protocol family 1
[    0.301943] Trying to unpack rootfs image as initramfs...
[    0.529526] Freeing initrd memory: 7713k freed
[    0.533869] cpufreq-nforce2: No nForce2 chipset.
[    0.533969] Scanning for low memory corruption every 60 seconds
[    0.534148] audit: initializing netlink socket (disabled)
[    0.534237] type=2000 audit(1268845864.532:1): initialized
[    0.542946] highmem bounce pool size: 64 pages
[    0.543018] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.544859] VFS: Disk quotas dquot_6.5.2
[    0.544998] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.545772] fuse init (API version 7.12)
[    0.545943] msgmni has been set to 1682
[    0.546287] alg: No test for stdrng (krng)
[    0.546379] io scheduler noop registered
[    0.546445] io scheduler anticipatory registered
[    0.546511] io scheduler deadline registered
[    0.546629] io scheduler cfq registered (default)
[    0.568157] pci 0000:00:10.0: Boot video device
[    0.568313]   alloc irq_desc for 24 on node -1
[    0.568316]   alloc kstat_irqs on node -1
[    0.568329] pcieport-driver 0000:00:0b.0: irq 24 for MSI/MSI-X
[    0.568338] pcieport-driver 0000:00:0b.0: setting latency timer to 64
[    0.568461]   alloc irq_desc for 25 on node -1
[    0.568464]   alloc kstat_irqs on node -1
[    0.568472] pcieport-driver 0000:00:0c.0: irq 25 for MSI/MSI-X
[    0.568480] pcieport-driver 0000:00:0c.0: setting latency timer to 64
[    0.568600]   alloc irq_desc for 26 on node -1
[    0.568603]   alloc kstat_irqs on node -1
[    0.568612] pcieport-driver 0000:00:0d.0: irq 26 for MSI/MSI-X
[    0.568619] pcieport-driver 0000:00:0d.0: setting latency timer to 64
[    0.568704] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.568805] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.569030] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    0.569111] ACPI: Power Button [PWRF]
[    0.569246] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.569327] ACPI: Power Button [PWRB]
[    0.569755] processor LNXCPU:00: registered as cooling_device0
[    0.569826] ACPI: Processor [CPU0] (supports 8 throttling states)
[    0.570039] processor LNXCPU:01: registered as cooling_device1
[    0.574540] isapnp: Scanning for PnP cards...
[    0.806036] Switched to high resolution mode on CPU 1
[    0.808115] Switched to high resolution mode on CPU 0
[    0.927689] isapnp: No Plug & Play device found
[    0.929163] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.929348] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.929741] 00:04: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.931172] brd: module loaded
[    0.931781] loop: module loaded
[    0.931933] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    0.932112] ahci 0000:00:0e.0: version 3.0
[    0.932536] ACPI: PCI Interrupt Link [LSA0] enabled at IRQ 23
[    0.932607]   alloc irq_desc for 23 on node -1
[    0.932609]   alloc kstat_irqs on node -1
[    0.932617] ahci 0000:00:0e.0: PCI INT A -> Link[LSA0] -> GSI 23 (level, low) -> IRQ 23
[    0.932731]   alloc irq_desc for 27 on node -1
[    0.932734]   alloc kstat_irqs on node -1
[    0.932744] ahci 0000:00:0e.0: irq 27 for MSI/MSI-X
[    0.932752] ahci 0000:00:0e.0: controller can do NCQ, turning on CAP_NCQ
[    0.932875] ahci 0000:00:0e.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl IDE mode
[    0.932957] ahci 0000:00:0e.0: flags: 64bit ncq sntf led clo pmp pio 
[    0.933027] ahci 0000:00:0e.0: setting latency timer to 64
[    0.933366] scsi0 : ahci
[    0.933535] scsi1 : ahci
[    0.933673] scsi2 : ahci
[    0.933807] scsi3 : ahci
[    0.933993] ata1: SATA max UDMA/133 abar m8192@0xfeb7c000 port 0xfeb7c100 irq 27
[    0.934074] ata2: SATA max UDMA/133 abar m8192@0xfeb7c000 port 0xfeb7c180 irq 27
[    0.934153] ata3: SATA max UDMA/133 abar m8192@0xfeb7c000 port 0xfeb7c200 irq 27
[    0.934233] ata4: SATA max UDMA/133 abar m8192@0xfeb7c000 port 0xfeb7c280 irq 27
[    0.934611] pata_amd 0000:00:08.0: version 0.4.1
[    0.934655] pata_amd 0000:00:08.0: setting latency timer to 64
[    0.934736] scsi4 : pata_amd
[    0.934880] scsi5 : pata_amd
[    0.936718] ata5: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    0.936788] ata6: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    0.937850] Fixed MDIO Bus: probed
[    0.937956] PPP generic driver version 2.4.2
[    0.938139] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.940911] ACPI: PCI Interrupt Link [LUB2] enabled at IRQ 22
[    0.940981]   alloc irq_desc for 22 on node -1
[    0.940984]   alloc kstat_irqs on node -1
[    0.940990] ehci_hcd 0000:00:04.1: PCI INT B -> Link[LUB2] -> GSI 22 (level, low) -> IRQ 22
[    0.941080] ehci_hcd 0000:00:04.1: setting latency timer to 64
[    0.941084] ehci_hcd 0000:00:04.1: EHCI Host Controller
[    0.941186] ehci_hcd 0000:00:04.1: new USB bus registered, assigned bus number 1
[    0.941292] ehci_hcd 0000:00:04.1: debug port 1
[    0.941362] ehci_hcd 0000:00:04.1: cache line size of 128 is not supported
[    0.941377] ehci_hcd 0000:00:04.1: irq 22, io mem 0xfeb7ec00
[    0.952015] ehci_hcd 0000:00:04.1: USB 2.0 started, EHCI 1.00
[    0.952163] usb usb1: configuration #1 chosen from 1 choice
[    0.952265] hub 1-0:1.0: USB hub found
[    0.952337] hub 1-0:1.0: 8 ports detected
[    0.952476] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.952956] ACPI: PCI Interrupt Link [LUB0] enabled at IRQ 21
[    0.953025]   alloc irq_desc for 21 on node -1
[    0.953028]   alloc kstat_irqs on node -1
[    0.953034] ohci_hcd 0000:00:04.0: PCI INT A -> Link[LUB0] -> GSI 21 (level, low) -> IRQ 21
[    0.953122] ohci_hcd 0000:00:04.0: setting latency timer to 64
[    0.953126] ohci_hcd 0000:00:04.0: OHCI Host Controller
[    0.953226] ohci_hcd 0000:00:04.0: new USB bus registered, assigned bus number 2
[    0.953325] ohci_hcd 0000:00:04.0: irq 21, io mem 0xfeb7f000
[    1.010068] usb usb2: configuration #1 chosen from 1 choice
[    1.010169] hub 2-0:1.0: USB hub found
[    1.010242] hub 2-0:1.0: 8 ports detected
[    1.010370] uhci_hcd: USB Universal Host Controller Interface driver
[    1.010526] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    1.010952] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.011024] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.011174] mice: PS/2 mouse device common for all mice
[    1.011357] rtc_cmos 00:06: RTC can wake from S4
[    1.011460] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    1.011560] rtc0: alarms up to one year, y3k, 114 bytes nvram
[    1.011758] device-mapper: uevent: version 1.0.3
[    1.011925] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    1.012111] device-mapper: multipath: version 1.1.0 loaded
[    1.012179] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.012391] EISA: Probing bus 0 at eisa.0
[    1.012469] Cannot allocate resource for EISA slot 4
[    1.012547] EISA: Detected 0 cards.
[    1.012729] cpuidle: using governor ladder
[    1.012795] cpuidle: using governor menu
[    1.013525] TCP cubic registered
[    1.013748] NET: Registered protocol family 10
[    1.014404] lo: Disabled Privacy Extensions
[    1.014906] NET: Registered protocol family 17
[    1.014990] Bluetooth: L2CAP ver 2.13
[    1.015054] Bluetooth: L2CAP socket layer initialized
[    1.015122] Bluetooth: SCO (Voice Link) ver 0.6
[    1.015196] Bluetooth: SCO socket layer initialized
[    1.015295] Bluetooth: RFCOMM TTY layer initialized
[    1.015365] Bluetooth: RFCOMM socket layer initialized
[    1.015431] Bluetooth: RFCOMM ver 1.11
[    1.015525] Using IPI No-Shortcut mode
[    1.015658] PM: Resume from disk failed.
[    1.015673] registered taskstats version 1
[    1.015876]   Magic number: 2:677:188
[    1.015964] acpi device:1a: hash matches
[    1.016083] rtc_cmos 00:06: setting system clock to 2010-03-17 17:11:05 UTC (1268845865)
[    1.016164] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.016240] EDD information not available.
[    1.030528] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    1.128312] ata5.00: ATAPI: TSSTcorp CD-RW/DVD-ROM TS-H492C, DE02, max UDMA/33
[    1.128435] ata5.01: ATAPI: HL-DT-ST DVDRAM GSA-4167B, DL11, max UDMA/33
[    1.128536] ata5: nv_mode_filter: 0x739f&0x739f->0x739f, BIOS=0x7000 (0xc0c00000) ACPI=0x701f (60:60:0x15)
[    1.128542] ata5: nv_mode_filter: 0x739f&0x739f->0x739f, BIOS=0x7000 (0xc0c00000) ACPI=0x701f (60:60:0x15)
[    1.160272] ata5.00: configured for UDMA/33
[    1.176265] ata5.01: configured for UDMA/33
[    1.252521] ata2: SATA link down (SStatus 0 SControl 300)
[    1.260015] ata4: SATA link down (SStatus 0 SControl 300)
[    1.416031] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.416109] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.416930] ata3.00: ATA-8: WDC WD5000AAKS-00A7B2, 01.03B01, max UDMA/133
[    1.417001] ata3.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    1.417983] ata3.00: configured for UDMA/133
[    1.456681] ata1.00: ATA-7: ST3160812AS, 3.ADJ, max UDMA/133
[    1.456749] ata1.00: 312500000 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    1.515019] ata1.00: configured for UDMA/133
[    1.515216] scsi 0:0:0:0: Direct-Access     ATA      ST3160812AS      3.AD PQ: 0 ANSI: 5
[    1.515469] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.515584] sd 0:0:0:0: [sda] 312500000 512-byte logical blocks: (160 GB/149 GiB)
[    1.515725] sd 0:0:0:0: [sda] Write Protect is off
[    1.515792] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.515825] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.516073]  sda:
[    1.516250] scsi 2:0:0:0: Direct-Access     ATA      WDC WD5000AAKS-0 01.0 PQ: 0 ANSI: 5
[    1.516520] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    1.516628] sd 2:0:0:0: [sdb] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    1.516766] sd 2:0:0:0: [sdb] Write Protect is off
[    1.516833] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    1.516866] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.517091]  sdb:
[    1.517748] scsi 4:0:0:0: CD-ROM            TSSTcorp CDRWDVD TS-H492C DE02 PQ: 0 ANSI: 5
[    1.520722] sr0: scsi3-mmc drive: 8x/48x writer cd/rw xa/form2 cdda tray
[    1.520793] Uniform CD-ROM driver Revision: 3.20
[    1.520955] sr 4:0:0:0: Attached scsi CD-ROM sr0
[    1.521025] sr 4:0:0:0: Attached scsi generic sg2 type 5
[    1.524875] scsi 4:0:1:0: CD-ROM            HL-DT-ST DVDRAM GSA-4167B DL11 PQ: 0 ANSI: 5
[    1.529671]  sdb1
[    1.530038] sd 2:0:0:0: [sdb] Attached SCSI disk
[    1.530116] sr1: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.530275] sr 4:0:1:0: Attached scsi CD-ROM sr1
[    1.530326] sr 4:0:1:0: Attached scsi generic sg3 type 5
[    1.530434] ata6: port disabled. ignoring.
[    1.554700]  sda1 sda2 < sda5 >
[    1.578915] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.579001] Freeing unused kernel memory: 540k freed
[    1.579462] Write protecting the kernel text: 4580k
[    1.579581] Write protecting the kernel read-only data: 1840k
[    1.746680] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
[    1.747247] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 20
[    1.747320]   alloc irq_desc for 20 on node -1
[    1.747323]   alloc kstat_irqs on node -1
[    1.747333] forcedeth 0000:00:0f.0: PCI INT A -> Link[LMAC] -> GSI 20 (level, low) -> IRQ 20
[    1.747418] forcedeth 0000:00:0f.0: setting latency timer to 64
[    2.265249] forcedeth 0000:00:0f.0: ifname eth0, PHY OUI 0x732 @ 1, addr 00:1d:92:e1:51:c0
[    2.265335] forcedeth 0000:00:0f.0: highdma pwrctl mgmt lnktim msi desc-v3
[    2.424623] xor: automatically using best checksumming function: pIII_sse
[    2.444507]    pIII_sse  :  4827.000 MB/sec
[    2.444575] xor: using function: pIII_sse (4827.000 MB/sec)
[    2.447511] device-mapper: dm-raid45: initialized v0.2594b
[    2.723414] PM: Starting manual resume from disk
[    2.723485] PM: Resume from partition 8:5
[    2.723487] PM: Checking hibernation image.
[    2.723602] PM: Resume from disk failed.
[    2.728707] EXT3-fs: INFO: recovery required on readonly filesystem.
[    2.728780] EXT3-fs: write access will be enabled during recovery.
[    2.840207] kjournald starting.  Commit interval 5 seconds
[    2.840217] EXT3-fs: sda1: orphan cleanup on readonly fs
[    2.840225] ext3_orphan_cleanup: deleting unreferenced inode 3153929
[    2.840252] ext3_orphan_cleanup: deleting unreferenced inode 3153928
[    2.840262] ext3_orphan_cleanup: deleting unreferenced inode 3153927
[    2.840270] ext3_orphan_cleanup: deleting unreferenced inode 3153925
[    2.840279] ext3_orphan_cleanup: deleting unreferenced inode 3153922
[    2.840286] EXT3-fs: sda1: 5 orphan inodes deleted
[    2.840288] EXT3-fs: recovery complete.
[    2.842132] EXT3-fs: mounted filesystem with writeback data mode.
[    3.572906] type=1505 audit(1268845868.055:2): operation="profile_load" pid=446 name=/usr/share/gdm/guest-session/Xsession
[    3.588359] type=1505 audit(1268845868.071:3): operation="profile_load" pid=447 name=/sbin/dhclient3
[    3.589129] type=1505 audit(1268845868.071:4): operation="profile_load" pid=447 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    3.589585] type=1505 audit(1268845868.071:5): operation="profile_load" pid=447 name=/usr/lib/connman/scripts/dhclient-script
[    3.607930] type=1505 audit(1268845868.087:6): operation="profile_load" pid=448 name=/usr/bin/evince
[    3.619085] type=1505 audit(1268845868.099:7): operation="profile_load" pid=448 name=/usr/bin/evince-previewer
[    3.625614] type=1505 audit(1268845868.107:8): operation="profile_load" pid=448 name=/usr/bin/evince-thumbnailer
[    3.661838] type=1505 audit(1268845868.143:9): operation="profile_load" pid=450 name=/usr/lib/cups/backend/cups-pdf
[    3.662722] type=1505 audit(1268845868.143:10): operation="profile_load" pid=450 name=/usr/sbin/cupsd
[   18.853964] udev: starting version 147
[   18.885525] Adding 6385796k swap on /dev/sda5.  Priority:-1 extents:1 across:6385796k 
[   18.905986] lp: driver loaded but no devices found
[   18.915710] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x4d00
[   18.915737] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x4e00
[   18.929814] Linux agpgart interface v0.103
[   19.079114] nvidia: module license 'NVIDIA' taints kernel.
[   19.079119] Disabling lock debugging due to kernel taint
[   19.162218] EXT3 FS on sda1, internal journal
[   19.339887] ACPI: PCI Interrupt Link [SGRU] enabled at IRQ 23
[   19.339894] nvidia 0000:00:10.0: PCI INT A -> Link[SGRU] -> GSI 23 (level, low) -> IRQ 23
[   19.339902] nvidia 0000:00:10.0: setting latency timer to 64
[   19.340134] NVRM: loading NVIDIA UNIX x86 Kernel Module  185.18.36  Fri Aug 14 17:18:04 PDT 2009
[   19.370389] HDA Intel 0000:00:09.0: power state changed by ACPI to D0
[   19.370815] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 22
[   19.370822] HDA Intel 0000:00:09.0: PCI INT A -> Link[LAZA] -> GSI 22 (level, low) -> IRQ 22
[   19.370850] HDA Intel 0000:00:09.0: setting latency timer to 64
[   19.377760] ip_tables: (C) 2000-2006 Netfilter Core Team
[   19.469058]   alloc irq_desc for 28 on node -1
[   19.469067]   alloc kstat_irqs on node -1
[   19.469086] forcedeth 0000:00:0f.0: irq 28 for MSI/MSI-X
[   19.645429] __ratelimit: 6 callbacks suppressed
[   19.645433] type=1505 audit(1268860284.127:13): operation="profile_replace" pid=992 name=/usr/share/gdm/guest-session/Xsession
[   19.647499] type=1505 audit(1268860284.127:14): operation="profile_replace" pid=995 name=/sbin/dhclient3
[   19.648194] type=1505 audit(1268860284.131:15): operation="profile_replace" pid=995 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   19.648589] type=1505 audit(1268860284.131:16): operation="profile_replace" pid=995 name=/usr/lib/connman/scripts/dhclient-script
[   19.654464] type=1505 audit(1268860284.135:17): operation="profile_replace" pid=998 name=/usr/bin/evince
[   19.673859] type=1505 audit(1268860284.155:18): operation="profile_replace" pid=998 name=/usr/bin/evince-previewer
[   19.680365] type=1505 audit(1268860284.163:19): operation="profile_replace" pid=998 name=/usr/bin/evince-thumbnailer
[   19.693507] type=1505 audit(1268860284.175:20): operation="profile_replace" pid=1019 name=/usr/lib/cups/backend/cups-pdf
[   19.694311] type=1505 audit(1268860284.175:21): operation="profile_replace" pid=1019 name=/usr/sbin/cupsd
[   19.697183] type=1505 audit(1268860284.179:22): operation="profile_replace" pid=1020 name=/usr/sbin/mysqld
[   19.811235] psmouse serio1: ID: 10 00 64
[   19.879548] logips2pp: Detected unknown logitech mouse model 62
[   20.021120] hda_codec: Unknown model for ALC1200, trying auto-probe from BIOS...
[   20.036618] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:09.0/input/input4
[   20.379341] input: ImExPS/2 Logitech Explorer Mouse as /devices/platform/i8042/serio1/input/input5
[   29.564047] eth0: no IPv6 routers present
[   32.811371] __ratelimit: 3 callbacks suppressed
[   32.811375] type=1503 audit(1268860297.291:24): operation="open" pid=1347 parent=1346 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   32.847298] type=1503 audit(1268860297.327:25): operation="open" pid=1376 parent=1375 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   32.935481] type=1503 audit(1268860297.415:26): operation="open" pid=1491 parent=1383 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   33.871295] type=1503 audit(1268860298.351:27): operation="open" pid=1507 parent=1506 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   33.899501] type=1503 audit(1268860298.379:28): operation="open" pid=1518 parent=1517 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   34.767840] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   34.767845] vboxdrv: Successfully done.
[   34.767847] vboxdrv: Found 2 processor cores.
[   34.767940] vboxdrv: fAsync=0 offMin=0x9e0 offMax=0x2710
[   34.767989] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   34.767992] vboxdrv: Successfully loaded version 3.1.2 (interface 0x00100001).
[   35.098682] ppdev: user-space parallel port driver
[   35.448903] CPU0 attaching NULL sched-domain.
[   35.448910] CPU1 attaching NULL sched-domain.
[   35.464073] CPU0 attaching sched-domain:
[   35.464078]  domain 0: span 0-1 level MC
[   35.464082]   groups: 0 1
[   35.464087]   domain 1: span 0-1 level CPU
[   35.464091]    groups: 0-1 (__cpu_power = 2048)
[   35.464097] CPU1 attaching sched-domain:
[   35.464100]  domain 0: span 0-1 level MC
[   35.464103]   groups: 1 0
[   35.464107]   domain 1: span 0-1 level CPU
[   35.464110]    groups: 0-1 (__cpu_power = 2048)
[   56.357349] CPU0 attaching NULL sched-domain.
[   56.357356] CPU1 attaching NULL sched-domain.
[   56.368571] CPU0 attaching sched-domain:
[   56.368576]  domain 0: span 0-1 level CPU
[   56.368580]   groups: 0 1
[   56.368587] CPU1 attaching sched-domain:
[   56.368590]  domain 0: span 0-1 level CPU
[   56.368593]   groups: 1 0
[ 4640.131598] type=1503 audit(1268868495.267:29): operation="open" pid=9393 parent=9392 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
```

---

