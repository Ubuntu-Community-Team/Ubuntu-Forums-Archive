---
title: "COMPLETE freeze/lockup"
date: 2009-04-24
forum: New to Ubuntu
---

### Post by psychomichael on 2009-04-24
I have had more problems in the last couple of days than I've ever had using Linux...I did a fresh install of 9.04 and am enjoying the thrills of the random freezups. No keyboard or mouse when it locks up. I have to use REISUB to soft-reboot or it will sit frozen for hours. 

This seems similar to the hundreds of reports of the same issue. Why call it "stable" if it clearly is not? Other than this weird issue, I am truly loving the new Ubuntu. 

Before anyone asks, here's some logs and my lspci:

```

KERN.LOG

Apr 24 22:28:44 greatshaitan kernel: Inspecting /boot/System.map-2.6.28-11-generic
Apr 24 22:28:44 greatshaitan kernel: Cannot find map file.
Apr 24 22:28:44 greatshaitan kernel: Loaded 72525 symbols from 43 modules.
Apr 24 22:28:44 greatshaitan kernel: [    0.000000] BIOS EBDA/lowmem at: 0009f000/0009f000
Apr 24 22:28:44 greatshaitan kernel: [    0.000000] Initializing cgroup subsys cpuset
Apr 24 22:28:44 greatshaitan kernel: [    0.000000] Initializing cgroup subsys cpu
Apr 24 22:28:44 greatshaitan kernel: [    0.000000] Linux version 2.6.28-11-generic (buildd@palmer) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 (Ubuntu 2.6.28-11.42-generic)
Apr 24 22:28:44 greatshaitan kernel: [    0.000000] KERNEL supported cpus:
Apr 24 22:28:44 greatshaitan kernel: [    0.000000]   Intel GenuineIntel
Apr 24 22:28:44 greatshaitan kernel: [    0.000000]   AMD AuthenticAMD
Apr 24 22:28:44 greatshaitan kernel: [    0.000000]   NSC Geode by NSC
Apr 24 22:28:44 greatshaitan kernel: [    0.000000]   Cyrix CyrixInstead
Apr 24 22:28:44 greatshaitan kernel: [    0.000000]   Centaur CentaurHauls
Apr 24 22:28:44 greatshaitan kernel: [    0.000000]   Transmeta GenuineTMx86
Apr 24 22:28:44 greatshaitan kernel: [    0.000000]   Transmeta TransmetaCPU
Apr 24 22:28:44 greatshaitan kernel: [    0.000000]   UMC UMC UMC UMC
Apr 24 22:28:44 greatshaitan kernel: [    0.000000] BIOS-provided physical RAM map:
Apr 24 22:28:44 greatshaitan kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
Apr 24 22:28:44 greatshaitan kernel: [    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
Apr 24 22:28:44 greatshaitan kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Apr 24 22:28:44 greatshaitan kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 00000000dfef0000 (usable)
Apr 24 22:28:44 greatshaitan kernel: [    0.000000]  BIOS-e820: 00000000dfef0000 - 00000000dfef3000 (ACPI NVS)
Apr 24 22:28:44 greatshaitan kernel: [    0.000000]  BIOS-e820: 00000000dfef3000 - 00000000dff00000 (ACPI data)
Apr 24 22:28:44 greatshaitan kernel: [    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f2000000 (reserved)
Apr 24 22:28:44 greatshaitan kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
Apr 24 22:28:44 greatshaitan kernel: [    0.000000]  BIOS-e820: 0000000100000000 - 0000000120000000 (usable)
Apr 24 22:28:44 greatshaitan kernel: [    0.000000] DMI 2.4 present.
Apr 24 22:28:44 greatshaitan kernel: [    0.000000] Phoenix BIOS detected: BIOS may corrupt low RAM, working it around.
Apr 24 22:28:44 greatshaitan kernel: [    0.000000] last_pfn = 0xdfef0 max_arch_pfn = 0x100000
Apr 24 22:28:44 greatshaitan kernel: [    0.000000] Scanning 0 areas for low memory corruption
Apr 24 22:28:44 greatshaitan kernel: [    0.000000] modified physical RAM map:
Apr 24 22:28:44 greatshaitan kernel: [    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
Apr 24 22:28:44 greatshaitan kernel: [    0.000000]  modified: 0000000000010000 - 000000000009f000 (usable)
Apr 24 22:28:44 greatshaitan kernel: [    0.000000]  modified: 000000000009f000 - 00000000000a0000 (reserved)
Apr 24 22:28:44 greatshaitan kernel: [    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
Apr 24 22:28:44 greatshaitan kernel: [    0.000000]  modified: 0000000000100000 - 00000000dfef0000 (usable)
Apr 24 22:28:44 greatshaitan kernel: [    0.000000]  modified: 00000000dfef0000 - 00000000dfef3000 (ACPI NVS)
Apr 24 22:28:44 greatshaitan kernel: [    0.000000]  modified: 00000000dfef3000 - 00000000dff00000 (ACPI data)
Apr 24 22:28:44 greatshaitan kernel: [    0.000000]  modified: 00000000f0000000 - 00000000f2000000 (reserved)
Apr 24 22:28:44 greatshaitan kernel: [    0.000000]  modified: 00000000fec00000 - 0000000100000000 (reserved)
Apr 24 22:28:44 greatshaitan kernel: [    0.000000]  modified: 0000000100000000 - 0000000120000000 (usable)
Apr 24 22:28:44 greatshaitan kernel: [    0.000000] kernel direct mapping tables up to 373fe000 @ 10000-16000
Apr 24 22:28:44 greatshaitan kernel: [    0.000000] RAMDISK: 378be000 - 37fefdf3
Apr 24 22:28:44 greatshaitan kernel: [    0.000000] Allocated new RAMDISK: 00881000 - 00fb2df3
Apr 24 22:28:44 greatshaitan kernel: [    0.000000] Move RAMDISK from 00000000378be000 - 0000000037fefdf2 to 00881000 - 00fb2df2
Apr 24 22:28:44 greatshaitan kernel: [    0.000000] ACPI: RSDP 000F7630, 0024 (r2 Nvidia)
Apr 24 22:28:44 greatshaitan kernel: [    0.000000] ACPI: XSDT DFEF30C0, 0044 (r1 Nvidia ASUSACPI 42302E31 AWRD        0)
Apr 24 22:28:44 greatshaitan kernel: [    0.000000] ACPI: FACP DFEF9700, 00F4 (r3 Nvidia ASUSACPI 42302E31 AWRD        0)
Apr 24 22:28:44 greatshaitan kernel: [    0.000000] FADT: X_PM1a_EVT_BLK.bit_width (8) does not match PM1_EVT_LEN (4)
Apr 24 22:28:44 greatshaitan kernel: [    0.000000] ACPI: DSDT DFEF3240, 6472 (r1 NVIDIA ASUSACPI     1000 MSFT  3000000)
Apr 24 22:28:44 greatshaitan kernel: [    0.000000] ACPI: FACS DFEF0000, 0040
Apr 24 22:28:44 greatshaitan kernel: [    0.000000] ACPI: HPET DFEF9940, 0038 (r1 Nvidia ASUSACPI 42302E31 AWRD       98)
Apr 24 22:28:44 greatshaitan kernel: [    0.000000] ACPI: MCFG DFEF99C0, 003C (r1 Nvidia ASUSACPI 42302E31 AWRD        0)
Apr 24 22:28:44 greatshaitan kernel: [    0.000000] ACPI: APIC DFEF9840, 0098 (r1 Nvidia ASUSACPI 42302E31 AWRD        0)
Apr 24 22:28:44 greatshaitan kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Apr 24 22:28:44 greatshaitan kernel: [    0.000000] 2698MB HIGHMEM available.
Apr 24 22:28:44 greatshaitan kernel: [    0.000000] 883MB LOWMEM available.
Apr 24 22:28:44 greatshaitan kernel: [    0.000000]   mapped low ram: 0 - 373fe000
Apr 24 22:28:44 greatshaitan kernel: [    0.000000]   low ram: 00000000 - 373fe000
Apr 24 22:28:44 greatshaitan kernel: [    0.000000]   bootmap 00012000 - 00018e80
Apr 24 22:28:44 greatshaitan kernel: [    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00373fe000]
Apr 24 22:28:44 greatshaitan kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
Apr 24 22:28:44 greatshaitan kernel: [    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
Apr 24 22:28:44 greatshaitan kernel: [    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
Apr 24 22:28:44 greatshaitan kernel: [    0.000000]   #3 [0000100000 - 000087c52c]    TEXT DATA BSS ==> [0000100000 - 000087c52c]
Apr 24 22:28:44 greatshaitan kernel: [    0.000000]   #4 [000087d000 - 0000881000]    INIT_PG_TABLE ==> [000087d000 - 0000881000]
Apr 24 22:28:44 greatshaitan kernel: [    0.000000]   #5 [000009f000 - 0000100000]    BIOS reserved ==> [000009f000 - 0000100000]
Apr 24 22:28:44 greatshaitan kernel: [    0.000000]   #6 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]
Apr 24 22:28:44 greatshaitan kernel: [    0.000000]   #7 [0000881000 - 0000fb2df3]      NEW RAMDISK ==> [0000881000 - 0000fb2df3]
Apr 24 22:28:44 greatshaitan kernel: [    0.000000]   #8 [0000012000 - 0000019000]          BOOTMAP ==> [0000012000 - 0000019000]
Apr 24 22:28:44 greatshaitan kernel: [    0.000000] found SMP MP-table at [c00f5bb0] 000f5bb0
Apr 24 22:28:44 greatshaitan kernel: [    0.000000] Zone PFN ranges:
Apr 24 22:28:44 greatshaitan kernel: [    0.000000]   DMA      0x00000010 -> 0x00001000
Apr 24 22:28:44 greatshaitan kernel: [    0.000000]   Normal   0x00001000 -> 0x000373fe
Apr 24 22:28:44 greatshaitan kernel: [    0.000000]   HighMem  0x000373fe -> 0x000dfef0
Apr 24 22:28:44 greatshaitan kernel: [    0.000000] Movable zone start PFN for each node
Apr 24 22:28:44 greatshaitan kernel: [    0.000000] early_node_map[2] active PFN ranges
Apr 24 22:28:44 greatshaitan kernel: [    0.000000]     0: 0x00000010 -> 0x0000009f
Apr 24 22:28:44 greatshaitan kernel: [    0.000000]     0: 0x00000100 -> 0x000dfef0
Apr 24 22:28:44 greatshaitan kernel: [    0.000000] On node 0 totalpages: 917119
Apr 24 22:28:44 greatshaitan kernel: [    0.000000] free_area_init_node: node 0, pgdat c06d0f80, node_mem_map c1000200
Apr 24 22:28:44 greatshaitan kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Apr 24 22:28:44 greatshaitan kernel: [    0.000000]   DMA zone: 0 pages reserved
Apr 24 22:28:44 greatshaitan kernel: [    0.000000]   DMA zone: 3951 pages, LIFO batch:0
Apr 24 22:28:44 greatshaitan kernel: [    0.000000]   Normal zone: 1736 pages used for memmap
Apr 24 22:28:44 greatshaitan kernel: [    0.000000]   Normal zone: 220470 pages, LIFO batch:31
Apr 24 22:28:44 greatshaitan kernel: [    0.000000]   HighMem zone: 5398 pages used for memmap
Apr 24 22:28:44 greatshaitan kernel: [    0.000000]   HighMem zone: 685532 pages, LIFO batch:31
Apr 24 22:28:44 greatshaitan kernel: [    0.000000]   Movable zone: 0 pages used for memmap
Apr 24 22:28:44 greatshaitan kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
Apr 24 22:28:44 greatshaitan kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Apr 24 22:28:44 greatshaitan kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Apr 24 22:28:44 greatshaitan kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Apr 24 22:28:44 greatshaitan kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
Apr 24 22:28:44 greatshaitan kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
Apr 24 22:28:44 greatshaitan kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Apr 24 22:28:44 greatshaitan kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Apr 24 22:28:44 greatshaitan kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
Apr 24 22:28:44 greatshaitan kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
Apr 24 22:28:44 greatshaitan kernel: [    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
Apr 24 22:28:44 greatshaitan kernel: [    0.000000] IOAPIC[0]: apic_id 4, version 17, address 0xfec00000, GSI 0-23
Apr 24 22:28:44 greatshaitan kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Apr 24 22:28:44 greatshaitan kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Apr 24 22:28:44 greatshaitan kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
Apr 24 22:28:44 greatshaitan kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
Apr 24 22:28:44 greatshaitan kernel: [    0.000000] ACPI: IRQ0 used by override.
Apr 24 22:28:44 greatshaitan kernel: [    0.000000] ACPI: IRQ2 used by override.
Apr 24 22:28:44 greatshaitan kernel: [    0.000000] ACPI: IRQ9 used by override.
Apr 24 22:28:44 greatshaitan kernel: [    0.000000] ACPI: IRQ14 used by override.
Apr 24 22:28:44 greatshaitan kernel: [    0.000000] ACPI: IRQ15 used by override.
Apr 24 22:28:44 greatshaitan kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Apr 24 22:28:44 greatshaitan kernel: [    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfeff0000
Apr 24 22:28:44 greatshaitan kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Apr 24 22:28:44 greatshaitan kernel: [    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
Apr 24 22:28:44 greatshaitan kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Apr 24 22:28:44 greatshaitan kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
Apr 24 22:28:44 greatshaitan kernel: [    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
Apr 24 22:28:44 greatshaitan kernel: [    0.000000] Allocating PCI resources starting at e0000000 (gap: dff00000:10100000)
Apr 24 22:28:44 greatshaitan kernel: [    0.000000] PERCPU: Allocating 45056 bytes of per cpu data
Apr 24 22:28:44 greatshaitan kernel: [    0.000000] NR_CPUS: 64, nr_cpu_ids: 4, nr_node_ids 1
Apr 24 22:28:44 greatshaitan kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 909953
Apr 24 22:28:44 greatshaitan kernel: [    0.000000] Kernel command line: root=UUID=5aa2466e-fc56-4b4f-a672-23c2cf891ac0 ro quiet splash 
Apr 24 22:28:44 greatshaitan kernel: [    0.000000] Enabling fast FPU save and restore... done.
Apr 24 22:28:44 greatshaitan kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Apr 24 22:28:44 greatshaitan kernel: [    0.000000] Initializing CPU#0
Apr 24 22:28:44 greatshaitan kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Apr 24 22:28:44 greatshaitan kernel: [    0.000000] Extended CMOS year: 2000
Apr 24 22:28:44 greatshaitan kernel: [    0.000000] Fast TSC calibration using PIT
Apr 24 22:28:44 greatshaitan kernel: [    0.000000] Detected 2133.054 MHz processor.
Apr 24 22:28:44 greatshaitan kernel: [    0.004000] spurious 8259A interrupt: IRQ7.
Apr 24 22:28:44 greatshaitan kernel: [    0.004000] Console: colour VGA+ 80x25
Apr 24 22:28:44 greatshaitan kernel: [    0.004000] console [tty0] enabled
Apr 24 22:28:44 greatshaitan kernel: [    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Apr 24 22:28:44 greatshaitan kernel: [    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Apr 24 22:28:44 greatshaitan kernel: [    0.004000] allocated 18344320 bytes of page_cgroup
Apr 24 22:28:44 greatshaitan kernel: [    0.004000] please try cgroup_disable=memory option if you don't want
Apr 24 22:28:44 greatshaitan kernel: [    0.004000] Scanning for low memory corruption every 60 seconds
Apr 24 22:28:44 greatshaitan kernel: [    0.004000] Memory: 3604904k/3668928k available (4126k kernel code, 62700k reserved, 2208k data, 532k init, 2763720k highmem)
Apr 24 22:28:44 greatshaitan kernel: [    0.004000] virtual kernel memory layout:
Apr 24 22:28:44 greatshaitan kernel: [    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
Apr 24 22:28:44 greatshaitan kernel: [    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
Apr 24 22:28:44 greatshaitan kernel: [    0.004000]     vmalloc : 0xf7bfe000 - 0xff3fe000   ( 120 MB)
Apr 24 22:28:44 greatshaitan kernel: [    0.004000]     lowmem  : 0xc0000000 - 0xf73fe000   ( 883 MB)
Apr 24 22:28:44 greatshaitan kernel: [    0.004000]       .init : 0xc0737000 - 0xc07bc000   ( 532 kB)
Apr 24 22:28:44 greatshaitan kernel: [    0.004000]       .data : 0xc0507a6f - 0xc072fe60   (2208 kB)
Apr 24 22:28:44 greatshaitan kernel: [    0.004000]       .text : 0xc0100000 - 0xc0507a6f   (4126 kB)
Apr 24 22:28:44 greatshaitan kernel: [    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Apr 24 22:28:44 greatshaitan kernel: [    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
Apr 24 22:28:44 greatshaitan kernel: [    0.004000] hpet clockevent registered
Apr 24 22:28:44 greatshaitan kernel: [    0.004000] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
Apr 24 22:28:44 greatshaitan kernel: [    0.004000] Calibrating delay loop (skipped), value calculated using timer frequency.. 4266.10 BogoMIPS (lpj=8532216)
Apr 24 22:28:44 greatshaitan kernel: [    0.004000] Security Framework initialized
Apr 24 22:28:44 greatshaitan kernel: [    0.004000] SELinux:  Disabled at boot.
Apr 24 22:28:44 greatshaitan kernel: [    0.004000] AppArmor: AppArmor initialized
Apr 24 22:28:44 greatshaitan kernel: [    0.004000] Mount-cache hash table entries: 512
Apr 24 22:28:44 greatshaitan kernel: [    0.004000] Initializing cgroup subsys ns
Apr 24 22:28:44 greatshaitan kernel: [    0.004000] Initializing cgroup subsys cpuacct
Apr 24 22:28:44 greatshaitan kernel: [    0.004000] Initializing cgroup subsys memory
Apr 24 22:28:44 greatshaitan kernel: [    0.004000] Initializing cgroup subsys freezer
Apr 24 22:28:44 greatshaitan kernel: [    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
Apr 24 22:28:44 greatshaitan kernel: [    0.004000] CPU: L2 cache: 4096K
Apr 24 22:28:44 greatshaitan kernel: [    0.004000] CPU: Physical Processor ID: 0
Apr 24 22:28:44 greatshaitan kernel: [    0.004000] CPU: Processor Core ID: 0
Apr 24 22:28:44 greatshaitan kernel: [    0.004000] using mwait in idle threads.
Apr 24 22:28:44 greatshaitan kernel: [    0.004000] Checking 'hlt' instruction... OK.
Apr 24 22:28:44 greatshaitan kernel: [    0.018137] ACPI: Core revision 20080926
Apr 24 22:28:44 greatshaitan kernel: [    0.019419] ACPI: Checking initramfs for custom DSDT
Apr 24 22:28:44 greatshaitan kernel: [    0.296338] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Apr 24 22:28:44 greatshaitan kernel: [    0.336031] CPU0: Intel(R) Core(TM)2 CPU          6420  @ 2.13GHz stepping 06
Apr 24 22:28:44 greatshaitan kernel: [    0.340001] Booting processor 1 APIC 0x1 ip 0x6000
Apr 24 22:28:44 greatshaitan kernel: [    0.004000] Initializing CPU#1
Apr 24 22:28:44 greatshaitan kernel: [    0.004000] Calibrating delay using timer specific routine.. 4266.65 BogoMIPS (lpj=8533312)
Apr 24 22:28:44 greatshaitan kernel: [    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
Apr 24 22:28:44 greatshaitan kernel: [    0.004000] CPU: L2 cache: 4096K
Apr 24 22:28:44 greatshaitan kernel: [    0.004000] CPU: Physical Processor ID: 0
Apr 24 22:28:44 greatshaitan kernel: [    0.004000] CPU: Processor Core ID: 1
Apr 24 22:28:44 greatshaitan kernel: [    0.424618] CPU1: Intel(R) Core(TM)2 CPU          6420  @ 2.13GHz stepping 06
Apr 24 22:28:44 greatshaitan kernel: [    0.424632] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
Apr 24 22:28:44 greatshaitan kernel: [    0.428031] Brought up 2 CPUs
Apr 24 22:28:44 greatshaitan kernel: [    0.428034] Total of 2 processors activated (8532.76 BogoMIPS).
Apr 24 22:28:44 greatshaitan kernel: [    0.428109] CPU0 attaching sched-domain:
Apr 24 22:28:44 greatshaitan kernel: [    0.428111]  domain 0: span 0-1 level MC
Apr 24 22:28:44 greatshaitan kernel: [    0.428114]   groups: 0 1
Apr 24 22:28:44 greatshaitan kernel: [    0.428119] CPU1 attaching sched-domain:
Apr 24 22:28:44 greatshaitan kernel: [    0.428121]  domain 0: span 0-1 level MC
Apr 24 22:28:44 greatshaitan kernel: [    0.428123]   groups: 1 0
Apr 24 22:28:44 greatshaitan kernel: [    0.428185] net_namespace: 776 bytes
Apr 24 22:28:44 greatshaitan kernel: [    0.428185] Booting paravirtualized kernel on bare hardware
Apr 24 22:28:44 greatshaitan kernel: [    0.428292] Time:  2:28:30  Date: 04/25/09
Apr 24 22:28:44 greatshaitan kernel: [    0.428292] regulator: core version 0.5
Apr 24 22:28:44 greatshaitan kernel: [    0.428292] NET: Registered protocol family 16
Apr 24 22:28:44 greatshaitan kernel: [    0.428292] EISA bus registered
Apr 24 22:28:44 greatshaitan kernel: [    0.428292] ACPI: bus type pci registered
Apr 24 22:28:44 greatshaitan kernel: [    0.428292] PCI: MCFG configuration 0: base f0000000 segment 0 buses 0 - 31
Apr 24 22:28:44 greatshaitan kernel: [    0.428292] PCI: MCFG area at f0000000 reserved in E820
Apr 24 22:28:44 greatshaitan kernel: [    0.428292] PCI: Using MMCONFIG for extended config space
Apr 24 22:28:44 greatshaitan kernel: [    0.428292] PCI: Using configuration type 1 for base access
Apr 24 22:28:44 greatshaitan kernel: [    0.428292] mtrr: your CPUs had inconsistent fixed MTRR settings
Apr 24 22:28:44 greatshaitan kernel: [    0.428292] mtrr: probably your BIOS does not setup all CPUs.
Apr 24 22:28:44 greatshaitan kernel: [    0.428292] mtrr: corrected configuration.
Apr 24 22:28:44 greatshaitan kernel: [    0.429159] ACPI: EC: Look up EC in DSDT
Apr 24 22:28:44 greatshaitan kernel: [    0.440077] ACPI: Interpreter enabled
Apr 24 22:28:44 greatshaitan kernel: [    0.440083] ACPI: (supports S0 S1 S3 S4 S5)
Apr 24 22:28:44 greatshaitan kernel: [    0.440106] ACPI: Using IOAPIC for interrupt routing
Apr 24 22:28:44 greatshaitan kernel: [    0.449350] ACPI: No dock devices found.
Apr 24 22:28:44 greatshaitan kernel: [    0.449360] ACPI: PCI Root Bridge [PCI0] (0000:00)
Apr 24 22:28:44 greatshaitan kernel: [    0.450202] pci 0000:00:03.0: PME# supported from D0 D1 D2 D3hot D3cold
Apr 24 22:28:44 greatshaitan kernel: [    0.450205] pci 0000:00:03.0: PME# disabled
Apr 24 22:28:44 greatshaitan kernel: [    0.450244] pci 0000:00:05.0: PME# supported from D0 D1 D2 D3hot D3cold
Apr 24 22:28:44 greatshaitan kernel: [    0.450247] pci 0000:00:05.0: PME# disabled
Apr 24 22:28:44 greatshaitan kernel: [    0.450285] pci 0000:00:06.0: PME# supported from D0 D1 D2 D3hot D3cold
Apr 24 22:28:44 greatshaitan kernel: [    0.450288] pci 0000:00:06.0: PME# disabled
Apr 24 22:28:44 greatshaitan kernel: [    0.450325] pci 0000:00:07.0: PME# supported from D0 D1 D2 D3hot D3cold
Apr 24 22:28:44 greatshaitan kernel: [    0.450327] pci 0000:00:07.0: PME# disabled
Apr 24 22:28:44 greatshaitan kernel: [    0.450561] pci 0000:00:0a.1: reg 20 io port: [0x1c00-0x1c3f]
Apr 24 22:28:44 greatshaitan kernel: [    0.450567] pci 0000:00:0a.1: reg 24 io port: [0x1c80-0x1cbf]
Apr 24 22:28:44 greatshaitan kernel: [    0.450582] pci 0000:00:0a.1: PME# supported from D3hot D3cold
Apr 24 22:28:44 greatshaitan kernel: [    0.450587] pci 0000:00:0a.1: PME# disabled
Apr 24 22:28:44 greatshaitan kernel: [    0.450660] pci 0000:00:0b.0: reg 10 32bit mmio: [0xfe02f000-0xfe02ffff]
Apr 24 22:28:44 greatshaitan kernel: [    0.450689] pci 0000:00:0b.0: supports D1 D2
Apr 24 22:28:44 greatshaitan kernel: [    0.450691] pci 0000:00:0b.0: PME# supported from D0 D1 D2 D3hot D3cold
Apr 24 22:28:44 greatshaitan kernel: [    0.450695] pci 0000:00:0b.0: PME# disabled
Apr 24 22:28:44 greatshaitan kernel: [    0.450725] pci 0000:00:0b.1: reg 10 32bit mmio: [0xfe02e000-0xfe02e0ff]
Apr 24 22:28:44 greatshaitan kernel: [    0.450754] pci 0000:00:0b.1: supports D1 D2
Apr 24 22:28:44 greatshaitan kernel: [    0.450755] pci 0000:00:0b.1: PME# supported from D0 D1 D2 D3hot D3cold
Apr 24 22:28:44 greatshaitan kernel: [    0.450759] pci 0000:00:0b.1: PME# disabled
Apr 24 22:28:44 greatshaitan kernel: [    0.450804] pci 0000:00:0d.0: reg 20 io port: [0xfd00-0xfd0f]
Apr 24 22:28:44 greatshaitan kernel: [    0.450850] pci 0000:00:0e.0: reg 10 io port: [0x9f0-0x9f7]
Apr 24 22:28:44 greatshaitan kernel: [    0.450855] pci 0000:00:0e.0: reg 14 io port: [0xbf0-0xbf3]
Apr 24 22:28:44 greatshaitan kernel: [    0.450861] pci 0000:00:0e.0: reg 18 io port: [0x970-0x977]
Apr 24 22:28:44 greatshaitan kernel: [    0.450866] pci 0000:00:0e.0: reg 1c io port: [0xb70-0xb73]
Apr 24 22:28:44 greatshaitan kernel: [    0.450871] pci 0000:00:0e.0: reg 20 io port: [0xf800-0xf80f]
Apr 24 22:28:44 greatshaitan kernel: [    0.450876] pci 0000:00:0e.0: reg 24 32bit mmio: [0xfe02d000-0xfe02dfff]
Apr 24 22:28:44 greatshaitan kernel: [    0.450921] pci 0000:00:0f.0: reg 10 io port: [0x9e0-0x9e7]
Apr 24 22:28:44 greatshaitan kernel: [    0.450926] pci 0000:00:0f.0: reg 14 io port: [0xbe0-0xbe3]
Apr 24 22:28:44 greatshaitan kernel: [    0.450931] pci 0000:00:0f.0: reg 18 io port: [0x960-0x967]
Apr 24 22:28:44 greatshaitan kernel: [    0.450936] pci 0000:00:0f.0: reg 1c io port: [0xb60-0xb63]
Apr 24 22:28:44 greatshaitan kernel: [    0.450942] pci 0000:00:0f.0: reg 20 io port: [0xf300-0xf30f]
Apr 24 22:28:44 greatshaitan kernel: [    0.450947] pci 0000:00:0f.0: reg 24 32bit mmio: [0xfe02c000-0xfe02cfff]
Apr 24 22:28:44 greatshaitan kernel: [    0.451031] pci 0000:00:14.0: reg 10 32bit mmio: [0xfe02b000-0xfe02bfff]
Apr 24 22:28:44 greatshaitan kernel: [    0.451036] pci 0000:00:14.0: reg 14 io port: [0xf200-0xf207]
Apr 24 22:28:44 greatshaitan kernel: [    0.451060] pci 0000:00:14.0: supports D1 D2
Apr 24 22:28:44 greatshaitan kernel: [    0.451061] pci 0000:00:14.0: PME# supported from D0 D1 D2 D3hot D3cold
Apr 24 22:28:44 greatshaitan kernel: [    0.451065] pci 0000:00:14.0: PME# disabled
Apr 24 22:28:44 greatshaitan kernel: [    0.451108] pci 0000:01:00.0: reg 10 32bit mmio: [0xfa000000-0xfaffffff]
Apr 24 22:28:44 greatshaitan kernel: [    0.451116] pci 0000:01:00.0: reg 14 64bit mmio: [0xe0000000-0xefffffff]
Apr 24 22:28:44 greatshaitan kernel: [    0.451125] pci 0000:01:00.0: reg 1c 64bit mmio: [0xfb000000-0xfbffffff]
Apr 24 22:28:44 greatshaitan kernel: [    0.451133] pci 0000:01:00.0: reg 30 32bit mmio: [0xfcfe0000-0xfcffffff]
Apr 24 22:28:44 greatshaitan kernel: [    0.451188] pci 0000:00:03.0: bridge io port: [0xc000-0xcfff]
Apr 24 22:28:44 greatshaitan kernel: [    0.451191] pci 0000:00:03.0: bridge 32bit mmio: [0xfa000000-0xfcffffff]
Apr 24 22:28:44 greatshaitan kernel: [    0.451196] pci 0000:00:03.0: bridge 64bit mmio pref: [0xe0000000-0xefffffff]
Apr 24 22:28:44 greatshaitan kernel: [    0.451242] pci 0000:00:05.0: bridge io port: [0xa000-0xafff]
Apr 24 22:28:44 greatshaitan kernel: [    0.451245] pci 0000:00:05.0: bridge 32bit mmio: [0xfde00000-0xfdefffff]
Apr 24 22:28:44 greatshaitan kernel: [    0.451249] pci 0000:00:05.0: bridge 64bit mmio pref: [0xfdd00000-0xfddfffff]
Apr 24 22:28:44 greatshaitan kernel: [    0.451297] pci 0000:00:06.0: bridge io port: [0xe000-0xefff]
Apr 24 22:28:44 greatshaitan kernel: [    0.451300] pci 0000:00:06.0: bridge 32bit mmio: [0xfdc00000-0xfdcfffff]
Apr 24 22:28:44 greatshaitan kernel: [    0.451304] pci 0000:00:06.0: bridge 64bit mmio pref: [0xfdb00000-0xfdbfffff]
Apr 24 22:28:44 greatshaitan kernel: [    0.451350] pci 0000:00:07.0: bridge io port: [0xd000-0xdfff]
Apr 24 22:28:44 greatshaitan kernel: [    0.451354] pci 0000:00:07.0: bridge 32bit mmio: [0xfd800000-0xfd8fffff]
Apr 24 22:28:44 greatshaitan kernel: [    0.451358] pci 0000:00:07.0: bridge 64bit mmio pref: [0xfdf00000-0xfdffffff]
Apr 24 22:28:44 greatshaitan kernel: [    0.451396] pci 0000:05:06.0: reg 10 io port: [0xbc00-0xbcff]
Apr 24 22:28:44 greatshaitan kernel: [    0.451433] pci 0000:05:06.0: supports D1 D2
Apr 24 22:28:44 greatshaitan kernel: [    0.451465] pci 0000:05:08.0: reg 10 32bit mmio: [0xfdaff000-0xfdaff7ff]
Apr 24 22:28:44 greatshaitan kernel: [    0.451472] pci 0000:05:08.0: reg 14 io port: [0xbf00-0xbf7f]
Apr 24 22:28:44 greatshaitan kernel: [    0.451505] pci 0000:05:08.0: supports D2
Apr 24 22:28:44 greatshaitan kernel: [    0.451506] pci 0000:05:08.0: PME# supported from D2 D3hot D3cold
Apr 24 22:28:44 greatshaitan kernel: [    0.451510] pci 0000:05:08.0: PME# disabled
Apr 24 22:28:44 greatshaitan kernel: [    0.451544] pci 0000:00:10.0: transparent bridge
Apr 24 22:28:44 greatshaitan kernel: [    0.451548] pci 0000:00:10.0: bridge io port: [0xb000-0xbfff]
Apr 24 22:28:44 greatshaitan kernel: [    0.451551] pci 0000:00:10.0: bridge 32bit mmio: [0xfda00000-0xfdafffff]
Apr 24 22:28:44 greatshaitan kernel: [    0.451555] pci 0000:00:10.0: bridge 32bit mmio pref: [0xfd900000-0xfd9fffff]
Apr 24 22:28:44 greatshaitan kernel: [    0.451570] bus 00 -> node 0
Apr 24 22:28:44 greatshaitan kernel: [    0.451577] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Apr 24 22:28:44 greatshaitan kernel: [    0.451982] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
Apr 24 22:28:44 greatshaitan kernel: [    0.529033] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 9 *10 11 14 15)
Apr 24 22:28:44 greatshaitan kernel: [    0.529209] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Apr 24 22:28:44 greatshaitan kernel: [    0.529385] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 9 *10 11 14 15)
Apr 24 22:28:44 greatshaitan kernel: [    0.529559] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Apr 24 22:28:44 greatshaitan kernel: [    0.529738] ACPI: PCI Interrupt Link [LNK5] (IRQs 5 7 9 10 *11 14 15)
Apr 24 22:28:44 greatshaitan kernel: [    0.529910] ACPI: PCI Interrupt Link [LNK6] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Apr 24 22:28:44 greatshaitan kernel: [    0.530084] ACPI: PCI Interrupt Link [LNK7] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Apr 24 22:28:44 greatshaitan kernel: [    0.530257] ACPI: PCI Interrupt Link [LNK8] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Apr 24 22:28:44 greatshaitan kernel: [    0.530432] ACPI: PCI Interrupt Link [LUBA] (IRQs 5 7 9 *10 11 14 15)
Apr 24 22:28:44 greatshaitan kernel: [    0.530605] ACPI: PCI Interrupt Link [LUBB] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Apr 24 22:28:44 greatshaitan kernel: [    0.530779] ACPI: PCI Interrupt Link [LMAC] (IRQs *5 7 9 10 11 14 15)
Apr 24 22:28:44 greatshaitan kernel: [    0.530955] ACPI: PCI Interrupt Link [LACI] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Apr 24 22:28:44 greatshaitan kernel: [    0.531129] ACPI: PCI Interrupt Link [LAZA] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Apr 24 22:28:44 greatshaitan kernel: [    0.531302] ACPI: PCI Interrupt Link [LPMU] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Apr 24 22:28:44 greatshaitan kernel: [    0.531475] ACPI: PCI Interrupt Link [LMCI] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Apr 24 22:28:44 greatshaitan kernel: [    0.531650] ACPI: PCI Interrupt Link [LSMB] (IRQs 5 7 9 10 *11 14 15)
Apr 24 22:28:44 greatshaitan kernel: [    0.531823] ACPI: PCI Interrupt Link [LUB2] (IRQs 5 7 9 10 *11 14 15)
Apr 24 22:28:44 greatshaitan kernel: [    0.531995] ACPI: PCI Interrupt Link [LIDE] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Apr 24 22:28:44 greatshaitan kernel: [    0.532173] ACPI: PCI Interrupt Link [LSID] (IRQs 5 7 9 10 *11 14 15)
Apr 24 22:28:44 greatshaitan kernel: [    0.532349] ACPI: PCI Interrupt Link [LFID] (IRQs 5 7 9 *10 11 14 15)
Apr 24 22:28:44 greatshaitan kernel: [    0.532560] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0
Apr 24 22:28:44 greatshaitan kernel: [    0.532764] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.
Apr 24 22:28:44 greatshaitan kernel: [    0.532967] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0
Apr 24 22:28:44 greatshaitan kernel: [    0.533170] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0, disabled.
Apr 24 22:28:44 greatshaitan kernel: [    0.533373] ACPI: PCI Interrupt Link [APC5] (IRQs 16) *0
Apr 24 22:28:44 greatshaitan kernel: [    0.533574] ACPI: PCI Interrupt Link [APC6] (IRQs 16) *0, disabled.
Apr 24 22:28:44 greatshaitan kernel: [    0.533777] ACPI: PCI Interrupt Link [APC7] (IRQs 16) *0, disabled.
Apr 24 22:28:44 greatshaitan kernel: [    0.533980] ACPI: PCI Interrupt Link [APC8] (IRQs 16) *0, disabled.
Apr 24 22:28:44 greatshaitan kernel: [    0.534183] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22 23) *0
Apr 24 22:28:44 greatshaitan kernel: [    0.534386] ACPI: PCI Interrupt Link [APCG] (IRQs 20 21 22 23) *0, disabled.
Apr 24 22:28:44 greatshaitan kernel: [    0.534590] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0
Apr 24 22:28:44 greatshaitan kernel: [    0.534794] ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22 23) *0, disabled.
Apr 24 22:28:44 greatshaitan kernel: [    0.534998] ACPI: PCI Interrupt Link [APMU] (IRQs 20 21 22 23) *0, disabled.
Apr 24 22:28:44 greatshaitan kernel: [    0.535203] ACPI: PCI Interrupt Link [AAZA] (IRQs 20 21 22 23) *0, disabled.
Apr 24 22:28:44 greatshaitan kernel: [    0.535408] ACPI: PCI Interrupt Link [APCK] (IRQs 20 21 22 23) *0, disabled.
Apr 24 22:28:44 greatshaitan kernel: [    0.535613] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0
Apr 24 22:28:44 greatshaitan kernel: [    0.535816] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22 23) *0
Apr 24 22:28:44 greatshaitan kernel: [    0.536024] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22 23) *0, disabled.
Apr 24 22:28:44 greatshaitan kernel: [    0.536230] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.
Apr 24 22:28:44 greatshaitan kernel: [    0.536435] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0
Apr 24 22:28:44 greatshaitan kernel: [    0.536638] ACPI: PCI Interrupt Link [APSJ] (IRQs 20 21 22 23) *0
Apr 24 22:28:44 greatshaitan kernel: [    0.536779] ACPI: WMI: Mapper loaded
Apr 24 22:28:44 greatshaitan kernel: [    0.536813] SCSI subsystem initialized
Apr 24 22:28:44 greatshaitan kernel: [    0.536813] libata version 3.00 loaded.
Apr 24 22:28:44 greatshaitan kernel: [    0.536813] usbcore: registered new interface driver usbfs
Apr 24 22:28:44 greatshaitan kernel: [    0.536813] usbcore: registered new interface driver hub
Apr 24 22:28:44 greatshaitan kernel: [    0.536813] usbcore: registered new device driver usb
Apr 24 22:28:44 greatshaitan kernel: [    0.536813] PCI: Using ACPI for IRQ routing
Apr 24 22:28:44 greatshaitan kernel: [    0.544009] Bluetooth: Core ver 2.13
Apr 24 22:28:44 greatshaitan kernel: [    0.544022] NET: Registered protocol family 31
Apr 24 22:28:44 greatshaitan kernel: [    0.544022] Bluetooth: HCI device and connection manager initialized
Apr 24 22:28:44 greatshaitan kernel: [    0.544022] Bluetooth: HCI socket layer initialized
Apr 24 22:28:44 greatshaitan kernel: [    0.544022] NET: Registered protocol family 8
Apr 24 22:28:44 greatshaitan kernel: [    0.544022] NET: Registered protocol family 20
Apr 24 22:28:44 greatshaitan kernel: [    0.544032] NetLabel: Initializing
Apr 24 22:28:44 greatshaitan kernel: [    0.544033] NetLabel:  domain hash size = 128
Apr 24 22:28:44 greatshaitan kernel: [    0.544035] NetLabel:  protocols = UNLABELED CIPSOv4
Apr 24 22:28:44 greatshaitan kernel: [    0.544045] NetLabel:  unlabeled traffic allowed by default
Apr 24 22:28:44 greatshaitan kernel: [    0.544059] hpet0: at MMIO 0xfeff0000, IRQs 2, 8, 31
Apr 24 22:28:44 greatshaitan kernel: [    0.544064] hpet0: 3 comparators, 32-bit 25.000000 MHz counter
Apr 24 22:28:44 greatshaitan kernel: [    0.548049] AppArmor: AppArmor Filesystem Enabled
Apr 24 22:28:44 greatshaitan kernel: [    0.552008] Switched to high resolution mode on CPU 0
Apr 24 22:28:44 greatshaitan kernel: [    0.552661] Switched to high resolution mode on CPU 1
Apr 24 22:28:44 greatshaitan kernel: [    0.556007] pnp: PnP ACPI init
Apr 24 22:28:44 greatshaitan kernel: [    0.556014] ACPI: bus type pnp registered
Apr 24 22:28:44 greatshaitan kernel: [    0.560788] pnp: PnP ACPI: found 15 devices
Apr 24 22:28:44 greatshaitan kernel: [    0.560790] ACPI: ACPI bus type pnp unregistered
Apr 24 22:28:44 greatshaitan kernel: [    0.560794] PnPBIOS: Disabled by ACPI PNP
Apr 24 22:28:44 greatshaitan kernel: [    0.560802] system 00:01: ioport range 0x1000-0x107f has been reserved
Apr 24 22:28:44 greatshaitan kernel: [    0.560805] system 00:01: ioport range 0x1080-0x10ff has been reserved
Apr 24 22:28:44 greatshaitan kernel: [    0.560807] system 00:01: ioport range 0x1400-0x147f has been reserved
Apr 24 22:28:44 greatshaitan kernel: [    0.560809] system 00:01: ioport range 0x1480-0x14ff has been reserved
Apr 24 22:28:44 greatshaitan kernel: [    0.560811] system 00:01: ioport range 0x1800-0x187f has been reserved
Apr 24 22:28:44 greatshaitan kernel: [    0.560814] system 00:01: ioport range 0x1880-0x18ff has been reserved
Apr 24 22:28:44 greatshaitan kernel: [    0.560819] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
Apr 24 22:28:44 greatshaitan kernel: [    0.560821] system 00:02: ioport range 0x800-0x87f has been reserved
Apr 24 22:28:44 greatshaitan kernel: [    0.560824] system 00:02: ioport range 0x290-0x297 has been reserved
Apr 24 22:28:44 greatshaitan kernel: [    0.560826] system 00:02: ioport range 0x880-0x88f has been reserved
Apr 24 22:28:44 greatshaitan kernel: [    0.560835] system 00:0d: iomem range 0xf0000000-0xf1ffffff has been reserved
Apr 24 22:28:44 greatshaitan kernel: [    0.560841] system 00:0e: iomem range 0xf0000-0xf3fff could not be reserved
Apr 24 22:28:44 greatshaitan kernel: [    0.560843] system 00:0e: iomem range 0xf4000-0xf7fff could not be reserved
Apr 24 22:28:44 greatshaitan kernel: [    0.560846] system 00:0e: iomem range 0xf8000-0xfbfff could not be reserved
Apr 24 22:28:44 greatshaitan kernel: [    0.560848] system 00:0e: iomem range 0xfc000-0xfffff could not be reserved
Apr 24 22:28:44 greatshaitan kernel: [    0.560850] system 00:0e: iomem range 0xfeff0000-0xfeff00ff has been reserved
Apr 24 22:28:44 greatshaitan kernel: [    0.560853] system 00:0e: iomem range 0xdfef0000-0xdfefffff could not be reserved
Apr 24 22:28:44 greatshaitan kernel: [    0.560855] system 00:0e: iomem range 0xffff0000-0xffffffff has been reserved
Apr 24 22:28:44 greatshaitan kernel: [    0.560858] system 00:0e: iomem range 0x0-0x9ffff could not be reserved
Apr 24 22:28:44 greatshaitan kernel: [    0.560860] system 00:0e: iomem range 0x100000-0xdfeeffff could not be reserved
Apr 24 22:28:44 greatshaitan kernel: [    0.560863] system 00:0e: iomem range 0xfec00000-0xfec00fff has been reserved
Apr 24 22:28:44 greatshaitan kernel: [    0.560865] system 00:0e: iomem range 0xfee00000-0xfee00fff has been reserved
Apr 24 22:28:44 greatshaitan kernel: [    0.560868] system 00:0e: iomem range 0xfeff0000-0xfeff03ff could not be reserved
Apr 24 22:28:44 greatshaitan kernel: [    0.595571] pci 0000:00:03.0: PCI bridge, secondary bus 0000:01
Apr 24 22:28:44 greatshaitan kernel: [    0.595573] pci 0000:00:03.0:   IO window: 0xc000-0xcfff
Apr 24 22:28:44 greatshaitan kernel: [    0.595577] pci 0000:00:03.0:   MEM window: 0xfa000000-0xfcffffff
Apr 24 22:28:44 greatshaitan kernel: [    0.595580] pci 0000:00:03.0:   PREFETCH window: 0x000000e0000000-0x000000efffffff
Apr 24 22:28:44 greatshaitan kernel: [    0.595585] pci 0000:00:05.0: PCI bridge, secondary bus 0000:02
Apr 24 22:28:44 greatshaitan kernel: [    0.595587] pci 0000:00:05.0:   IO window: 0xa000-0xafff
Apr 24 22:28:44 greatshaitan kernel: [    0.595591] pci 0000:00:05.0:   MEM window: 0xfde00000-0xfdefffff
Apr 24 22:28:44 greatshaitan kernel: [    0.595594] pci 0000:00:05.0:   PREFETCH window: 0x000000fdd00000-0x000000fddfffff
Apr 24 22:28:44 greatshaitan kernel: [    0.595598] pci 0000:00:06.0: PCI bridge, secondary bus 0000:03
Apr 24 22:28:44 greatshaitan kernel: [    0.595601] pci 0000:00:06.0:   IO window: 0xe000-0xefff
Apr 24 22:28:44 greatshaitan kernel: [    0.595604] pci 0000:00:06.0:   MEM window: 0xfdc00000-0xfdcfffff
Apr 24 22:28:44 greatshaitan kernel: [    0.595607] pci 0000:00:06.0:   PREFETCH window: 0x000000fdb00000-0x000000fdbfffff
Apr 24 22:28:44 greatshaitan kernel: [    0.595612] pci 0000:00:07.0: PCI bridge, secondary bus 0000:04
Apr 24 22:28:44 greatshaitan kernel: [    0.595614] pci 0000:00:07.0:   IO window: 0xd000-0xdfff
Apr 24 22:28:44 greatshaitan kernel: [    0.595618] pci 0000:00:07.0:   MEM window: 0xfd800000-0xfd8fffff
Apr 24 22:28:44 greatshaitan kernel: [    0.595621] pci 0000:00:07.0:   PREFETCH window: 0x000000fdf00000-0x000000fdffffff
Apr 24 22:28:44 greatshaitan kernel: [    0.595625] pci 0000:00:10.0: PCI bridge, secondary bus 0000:05
Apr 24 22:28:44 greatshaitan kernel: [    0.595628] pci 0000:00:10.0:   IO window: 0xb000-0xbfff
Apr 24 22:28:44 greatshaitan kernel: [    0.595632] pci 0000:00:10.0:   MEM window: 0xfda00000-0xfdafffff
Apr 24 22:28:44 greatshaitan kernel: [    0.595635] pci 0000:00:10.0:   PREFETCH window: 0x000000fd900000-0x000000fd9fffff
Apr 24 22:28:44 greatshaitan kernel: [    0.595645] pci 0000:00:03.0: setting latency timer to 64
Apr 24 22:28:44 greatshaitan kernel: [    0.595651] pci 0000:00:05.0: setting latency timer to 64
Apr 24 22:28:44 greatshaitan kernel: [    0.595657] pci 0000:00:06.0: setting latency timer to 64
Apr 24 22:28:44 greatshaitan kernel: [    0.595662] pci 0000:00:07.0: setting latency timer to 64
Apr 24 22:28:44 greatshaitan kernel: [    0.595667] pci 0000:00:10.0: setting latency timer to 64
Apr 24 22:28:44 greatshaitan kernel: [    0.595671] bus: 00 index 0 io port: [0x00-0xffff]
Apr 24 22:28:44 greatshaitan kernel: [    0.595673] bus: 00 index 1 mmio: [0x000000-0xffffffff]
Apr 24 22:28:44 greatshaitan kernel: [    0.595675] bus: 01 index 0 io port: [0xc000-0xcfff]
Apr 24 22:28:44 greatshaitan kernel: [    0.595677] bus: 01 index 1 mmio: [0xfa000000-0xfcffffff]
Apr 24 22:28:44 greatshaitan kernel: [    0.595679] bus: 01 index 2 mmio: [0xe0000000-0xefffffff]
Apr 24 22:28:44 greatshaitan kernel: [    0.595680] bus: 01 index 3 mmio: [0x0-0x0]
Apr 24 22:28:44 greatshaitan kernel: [    0.595682] bus: 02 index 0 io port: [0xa000-0xafff]
Apr 24 22:28:44 greatshaitan kernel: [    0.595684] bus: 02 index 1 mmio: [0xfde00000-0xfdefffff]
Apr 24 22:28:44 greatshaitan kernel: [    0.595686] bus: 02 index 2 mmio: [0xfdd00000-0xfddfffff]
Apr 24 22:28:44 greatshaitan kernel: [    0.595688] bus: 02 index 3 mmio: [0x0-0x0]
Apr 24 22:28:44 greatshaitan kernel: [    0.595689] bus: 03 index 0 io port: [0xe000-0xefff]
Apr 24 22:28:44 greatshaitan kernel: [    0.595691] bus: 03 index 1 mmio: [0xfdc00000-0xfdcfffff]
Apr 24 22:28:44 greatshaitan kernel: [    0.595693] bus: 03 index 2 mmio: [0xfdb00000-0xfdbfffff]
Apr 24 22:28:44 greatshaitan kernel: [    0.595695] bus: 03 index 3 mmio: [0x0-0x0]
Apr 24 22:28:44 greatshaitan kernel: [    0.595697] bus: 04 index 0 io port: [0xd000-0xdfff]
Apr 24 22:28:44 greatshaitan kernel: [    0.595698] bus: 04 index 1 mmio: [0xfd800000-0xfd8fffff]
Apr 24 22:28:44 greatshaitan kernel: [    0.595700] bus: 04 index 2 mmio: [0xfdf00000-0xfdffffff]
Apr 24 22:28:44 greatshaitan kernel: [    0.595702] bus: 04 index 3 mmio: [0x0-0x0]
Apr 24 22:28:44 greatshaitan kernel: [    0.595704] bus: 05 index 0 io port: [0xb000-0xbfff]
Apr 24 22:28:44 greatshaitan kernel: [    0.595706] bus: 05 index 1 mmio: [0xfda00000-0xfdafffff]
Apr 24 22:28:44 greatshaitan kernel: [    0.595707] bus: 05 index 2 mmio: [0xfd900000-0xfd9fffff]
Apr 24 22:28:44 greatshaitan kernel: [    0.595709] bus: 05 index 3 io port: [0x00-0xffff]
Apr 24 22:28:44 greatshaitan kernel: [    0.595711] bus: 05 index 4 mmio: [0x000000-0xffffffff]
Apr 24 22:28:44 greatshaitan kernel: [    0.595718] NET: Registered protocol family 2
Apr 24 22:28:44 greatshaitan kernel: [    0.608048] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Apr 24 22:28:44 greatshaitan kernel: [    0.608256] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Apr 24 22:28:44 greatshaitan kernel: [    0.608501] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Apr 24 22:28:44 greatshaitan kernel: [    0.608638] TCP: Hash tables configured (established 131072 bind 65536)
Apr 24 22:28:44 greatshaitan kernel: [    0.608640] TCP reno registered
Apr 24 22:28:44 greatshaitan kernel: [    0.616070] NET: Registered protocol family 1
Apr 24 22:28:44 greatshaitan kernel: [    0.616166] checking if image is initramfs... it is
Apr 24 22:28:44 greatshaitan kernel: [    1.175328] Freeing initrd memory: 7367k freed
Apr 24 22:28:44 greatshaitan kernel: [    1.175538] cpufreq: No nForce2 chipset.
Apr 24 22:28:44 greatshaitan kernel: [    1.175667] audit: initializing netlink socket (disabled)
Apr 24 22:28:44 greatshaitan kernel: [    1.175690] type=2000 audit(1240626510.172:1): initialized
Apr 24 22:28:44 greatshaitan kernel: [    1.182292] highmem bounce pool size: 64 pages
Apr 24 22:28:44 greatshaitan kernel: [    1.182296] HugeTLB registered 4 MB page size, pre-allocated 0 pages
Apr 24 22:28:44 greatshaitan kernel: [    1.183533] VFS: Disk quotas dquot_6.5.1
Apr 24 22:28:44 greatshaitan kernel: [    1.183586] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Apr 24 22:28:44 greatshaitan kernel: [    1.184135] fuse init (API version 7.10)
Apr 24 22:28:44 greatshaitan kernel: [    1.184211] msgmni has been set to 1659
Apr 24 22:28:44 greatshaitan kernel: [    1.184384] alg: No test for stdrng (krng)
Apr 24 22:28:44 greatshaitan kernel: [    1.184398] io scheduler noop registered
Apr 24 22:28:44 greatshaitan kernel: [    1.184400] io scheduler anticipatory registered
Apr 24 22:28:44 greatshaitan kernel: [    1.184402] io scheduler deadline registered
Apr 24 22:28:44 greatshaitan kernel: [    1.184414] io scheduler cfq registered (default)
Apr 24 22:28:44 greatshaitan kernel: [    1.184578] pci 0000:00:03.0: Disabling HT MSI mapping<6>pci 0000:00:05.0: Disabling HT MSI mapping<6>pci 0000:00:06.0: Disabling HT MSI mapping<6>pci 0000:00:07.0: Disabling HT MSI mapping<6>pci 0000:00:09.0: Disabling HT MSI mapping<6>pci 0000:00:0e.0: Disabling HT MSI mapping<6>pci 0000:00:0f.0: Disabling HT MSI mapping<6>pci 0000:00:10.0: Disabling HT MSI mapping<7>pci 0000:01:00.0: Boot video device
Apr 24 22:28:44 greatshaitan kernel: [    1.206593] pcieport-driver 0000:00:03.0: setting latency timer to 64
Apr 24 22:28:44 greatshaitan kernel: [    1.206631] pcieport-driver 0000:00:03.0: found MSI capability
Apr 24 22:28:44 greatshaitan kernel: [    1.206653] pcieport-driver 0000:00:03.0: irq 2303 for MSI/MSI-X
Apr 24 22:28:44 greatshaitan kernel: [    1.206662] pci_express 0000:00:03.0:pcie00: allocate port service
Apr 24 22:28:44 greatshaitan kernel: [    1.206675] pci_express 0000:00:03.0:pcie03: allocate port service
Apr 24 22:28:44 greatshaitan kernel: [    1.206723] pcieport-driver 0000:00:05.0: setting latency timer to 64
Apr 24 22:28:44 greatshaitan kernel: [    1.206760] pcieport-driver 0000:00:05.0: found MSI capability
Apr 24 22:28:44 greatshaitan kernel: [    1.206779] pcieport-driver 0000:00:05.0: irq 2302 for MSI/MSI-X
Apr 24 22:28:44 greatshaitan kernel: [    1.206787] pci_express 0000:00:05.0:pcie00: allocate port service
Apr 24 22:28:44 greatshaitan kernel: [    1.206799] pci_express 0000:00:05.0:pcie03: allocate port service
Apr 24 22:28:44 greatshaitan kernel: [    1.206846] pcieport-driver 0000:00:06.0: setting latency timer to 64
Apr 24 22:28:44 greatshaitan kernel: [    1.206882] pcieport-driver 0000:00:06.0: found MSI capability
Apr 24 22:28:44 greatshaitan kernel: [    1.206902] pcieport-driver 0000:00:06.0: irq 2301 for MSI/MSI-X
Apr 24 22:28:44 greatshaitan kernel: [    1.206910] pci_express 0000:00:06.0:pcie00: allocate port service
Apr 24 22:28:44 greatshaitan kernel: [    1.206925] pci_express 0000:00:06.0:pcie03: allocate port service
Apr 24 22:28:44 greatshaitan kernel: [    1.206973] pcieport-driver 0000:00:07.0: setting latency timer to 64
Apr 24 22:28:44 greatshaitan kernel: [    1.207009] pcieport-driver 0000:00:07.0: found MSI capability
Apr 24 22:28:44 greatshaitan kernel: [    1.207028] pcieport-driver 0000:00:07.0: irq 2300 for MSI/MSI-X
Apr 24 22:28:44 greatshaitan kernel: [    1.207036] pci_express 0000:00:07.0:pcie00: allocate port service
Apr 24 22:28:44 greatshaitan kernel: [    1.207050] pci_express 0000:00:07.0:pcie03: allocate port service
Apr 24 22:28:44 greatshaitan kernel: [    1.207105] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Apr 24 22:28:44 greatshaitan kernel: [    1.207114] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Apr 24 22:28:44 greatshaitan kernel: [    1.207264] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
Apr 24 22:28:44 greatshaitan kernel: [    1.207266] ACPI: Power Button (FF) [PWRF]
Apr 24 22:28:44 greatshaitan kernel: [    1.207309] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
Apr 24 22:28:44 greatshaitan kernel: [    1.207312] ACPI: Power Button (CM) [PWRB]
Apr 24 22:28:44 greatshaitan kernel: [    1.207372] fan PNP0C0B:00: registered as cooling_device0
Apr 24 22:28:44 greatshaitan kernel: [    1.207377] ACPI: Fan [FAN] (on)
Apr 24 22:28:44 greatshaitan kernel: [    1.207695] processor ACPI_CPU:00: registered as cooling_device1
Apr 24 22:28:44 greatshaitan kernel: [    1.207728] processor ACPI_CPU:01: registered as cooling_device2
Apr 24 22:28:44 greatshaitan kernel: [    1.211810] thermal LNXTHERM:01: registered as thermal_zone0
Apr 24 22:28:44 greatshaitan kernel: [    1.212115] ACPI: Thermal Zone [THRM] (40 C)
Apr 24 22:28:44 greatshaitan kernel: [    1.212168] isapnp: Scanning for PnP cards...
Apr 24 22:28:44 greatshaitan kernel: [    1.565083] isapnp: No Plug & Play device found
Apr 24 22:28:44 greatshaitan kernel: [    1.572687] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
Apr 24 22:28:44 greatshaitan kernel: [    1.572783] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Apr 24 22:28:44 greatshaitan kernel: [    1.573174] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Apr 24 22:28:44 greatshaitan kernel: [    1.573905] brd: module loaded
Apr 24 22:28:44 greatshaitan kernel: [    1.574194] loop: module loaded
Apr 24 22:28:44 greatshaitan kernel: [    1.574249] Fixed MDIO Bus: probed
Apr 24 22:28:44 greatshaitan kernel: [    1.574254] PPP generic driver version 2.4.2
Apr 24 22:28:44 greatshaitan kernel: [    1.574301] input: Macintosh mouse button emulation as /devices/virtual/input/input2
Apr 24 22:28:44 greatshaitan kernel: [    1.574326] Driver 'sd' needs updating - please use bus_type methods
Apr 24 22:28:44 greatshaitan kernel: [    1.574337] Driver 'sr' needs updating - please use bus_type methods
Apr 24 22:28:44 greatshaitan kernel: [    1.574529] sata_nv 0000:00:0e.0: version 3.5
Apr 24 22:28:44 greatshaitan kernel: [    1.574841] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 23
Apr 24 22:28:44 greatshaitan kernel: [    1.574847] sata_nv 0000:00:0e.0: PCI INT A -> Link[APSI] -> GSI 23 (level, low) -> IRQ 23
Apr 24 22:28:44 greatshaitan kernel: [    1.574849] sata_nv 0000:00:0e.0: Using SWNCQ mode
Apr 24 22:28:44 greatshaitan kernel: [    1.574888] sata_nv 0000:00:0e.0: setting latency timer to 64
Apr 24 22:28:44 greatshaitan kernel: [    1.575001] scsi0 : sata_nv
Apr 24 22:28:44 greatshaitan kernel: [    1.575078] scsi1 : sata_nv
Apr 24 22:28:44 greatshaitan kernel: [    1.575223] ata1: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xf800 irq 23
Apr 24 22:28:44 greatshaitan kernel: [    1.575226] ata2: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xf808 irq 23
Apr 24 22:28:44 greatshaitan kernel: [    2.306487] ata1: SATA link down (SStatus 0 SControl 300)
Apr 24 22:28:44 greatshaitan kernel: [    3.038472] ata2: SATA link down (SStatus 0 SControl 300)
Apr 24 22:28:44 greatshaitan kernel: [    3.038787] ACPI: PCI Interrupt Link [APSJ] enabled at IRQ 22
Apr 24 22:28:44 greatshaitan kernel: [    3.038791] sata_nv 0000:00:0f.0: PCI INT A -> Link[APSJ] -> GSI 22 (level, low) -> IRQ 22
Apr 24 22:28:44 greatshaitan kernel: [    3.038794] sata_nv 0000:00:0f.0: Using SWNCQ mode
Apr 24 22:28:44 greatshaitan kernel: [    3.038825] sata_nv 0000:00:0f.0: setting latency timer to 64
Apr 24 22:28:44 greatshaitan kernel: [    3.038938] scsi2 : sata_nv
Apr 24 22:28:44 greatshaitan kernel: [    3.038996] scsi3 : sata_nv
Apr 24 22:28:44 greatshaitan kernel: [    3.039140] ata3: SATA max UDMA/133 cmd 0x9e0 ctl 0xbe0 bmdma 0xf300 irq 22
Apr 24 22:28:44 greatshaitan kernel: [    3.039142] ata4: SATA max UDMA/133 cmd 0x960 ctl 0xb60 bmdma 0xf308 irq 22
Apr 24 22:28:44 greatshaitan kernel: [    3.916041] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Apr 24 22:28:44 greatshaitan kernel: [    3.924802] ata3.00: ATA-8: WL1000GSA3272^I, 05.00K05, max UDMA/133
Apr 24 22:28:44 greatshaitan kernel: [    3.924805] ata3.00: 1953525168 sectors, multi 1: LBA48 NCQ (depth 31/32)
Apr 24 22:28:44 greatshaitan kernel: [    3.940873] ata3.00: configured for UDMA/133
Apr 24 22:28:44 greatshaitan kernel: [    4.820040] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Apr 24 22:28:44 greatshaitan kernel: [    4.846099] ata4.00: ATA-7: WDC WD1600AAJS-00PSA0, 05.06H05, max UDMA/133
Apr 24 22:28:44 greatshaitan kernel: [    4.846101] ata4.00: 312581808 sectors, multi 1: LBA48 NCQ (depth 31/32)
Apr 24 22:28:44 greatshaitan kernel: [    4.861216] ata4.00: configured for UDMA/133
Apr 24 22:28:44 greatshaitan kernel: [    4.861314] scsi 2:0:0:0: Direct-Access     ATA      WL1000GSA3272    05.0 PQ: 0 ANSI: 5
Apr 24 22:28:44 greatshaitan kernel: [    4.861396] sd 2:0:0:0: [sda] 1953525168 512-byte hardware sectors: (1.00 TB/931 GiB)
Apr 24 22:28:44 greatshaitan kernel: [    4.861411] sd 2:0:0:0: [sda] Write Protect is off
Apr 24 22:28:44 greatshaitan kernel: [    4.861413] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 24 22:28:44 greatshaitan kernel: [    4.861436] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 24 22:28:44 greatshaitan kernel: [    4.861488] sd 2:0:0:0: [sda] 1953525168 512-byte hardware sectors: (1.00 TB/931 GiB)
Apr 24 22:28:44 greatshaitan kernel: [    4.861502] sd 2:0:0:0: [sda] Write Protect is off
Apr 24 22:28:44 greatshaitan kernel: [    4.861504] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 24 22:28:44 greatshaitan kernel: [    4.861526] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 24 22:28:44 greatshaitan kernel: [    4.861529]  sda: sda1 sda2 < sda5 >
Apr 24 22:28:44 greatshaitan kernel: [    4.896435] sd 2:0:0:0: [sda] Attached SCSI disk
Apr 24 22:28:44 greatshaitan kernel: [    4.896471] sd 2:0:0:0: Attached scsi generic sg0 type 0
Apr 24 22:28:44 greatshaitan kernel: [    4.896545] scsi 3:0:0:0: Direct-Access     ATA      WDC WD1600AAJS-0 05.0 PQ: 0 ANSI: 5
Apr 24 22:28:44 greatshaitan kernel: [    4.896622] sd 3:0:0:0: [sdb] 312581808 512-byte hardware sectors: (160 GB/149 GiB)
Apr 24 22:28:44 greatshaitan kernel: [    4.896636] sd 3:0:0:0: [sdb] Write Protect is off
Apr 24 22:28:44 greatshaitan kernel: [    4.896638] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
Apr 24 22:28:44 greatshaitan kernel: [    4.896661] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 24 22:28:44 greatshaitan kernel: [    4.896706] sd 3:0:0:0: [sdb] 312581808 512-byte hardware sectors: (160 GB/149 GiB)
Apr 24 22:28:44 greatshaitan kernel: [    4.896719] sd 3:0:0:0: [sdb] Write Protect is off
Apr 24 22:28:44 greatshaitan kernel: [    4.896721] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
Apr 24 22:28:44 greatshaitan kernel: [    4.896743] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 24 22:28:44 greatshaitan kernel: [    4.896746]  sdb: sdb1 sdb2
Apr 24 22:28:44 greatshaitan kernel: [    4.903399] sd 3:0:0:0: [sdb] Attached SCSI disk
Apr 24 22:28:44 greatshaitan kernel: [    4.903432] sd 3:0:0:0: Attached scsi generic sg1 type 0
Apr 24 22:28:44 greatshaitan kernel: [    4.903521] pata_amd 0000:00:0d.0: version 0.3.10
Apr 24 22:28:44 greatshaitan kernel: [    4.903551] pata_amd 0000:00:0d.0: setting latency timer to 64
Apr 24 22:28:44 greatshaitan kernel: [    4.903618] scsi4 : pata_amd
Apr 24 22:28:44 greatshaitan kernel: [    4.903676] scsi5 : pata_amd
Apr 24 22:28:44 greatshaitan kernel: [    4.904237] ata5: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xfd00 irq 14
Apr 24 22:28:44 greatshaitan kernel: [    4.904239] ata6: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xfd08 irq 15
Apr 24 22:28:44 greatshaitan kernel: [    5.240290] ata6.01: ATAPI: TSSTcorpCD/DVDW SH-S182D, SB03, max UDMA/33
Apr 24 22:28:44 greatshaitan kernel: [    5.240320] ata6: nv_mode_filter: 0x739f&0x701f->0x701f, BIOS=0x7000 (0xc0) ACPI=0x701f (600:60:0x1c)
Apr 24 22:28:44 greatshaitan kernel: [    5.256250] ata6.01: configured for UDMA/33
Apr 24 22:28:44 greatshaitan kernel: [    5.257439] scsi 5:0:1:0: CD-ROM            TSSTcorp CD/DVDW SH-S182D SB03 PQ: 0 ANSI: 5
Apr 24 22:28:44 greatshaitan kernel: [    5.264192] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
Apr 24 22:28:44 greatshaitan kernel: [    5.264195] Uniform CD-ROM driver Revision: 3.20
Apr 24 22:28:44 greatshaitan kernel: [    5.264271] sr 5:0:1:0: Attached scsi CD-ROM sr0
Apr 24 22:28:44 greatshaitan kernel: [    5.264306] sr 5:0:1:0: Attached scsi generic sg2 type 5
Apr 24 22:28:44 greatshaitan kernel: [    5.264820] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Apr 24 22:28:44 greatshaitan kernel: [    5.265136] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 21
Apr 24 22:28:44 greatshaitan kernel: [    5.265141] ehci_hcd 0000:00:0b.1: PCI INT B -> Link[APCL] -> GSI 21 (level, low) -> IRQ 21
Apr 24 22:28:44 greatshaitan kernel: [    5.265151] ehci_hcd 0000:00:0b.1: setting latency timer to 64
Apr 24 22:28:44 greatshaitan kernel: [    5.265154] ehci_hcd 0000:00:0b.1: EHCI Host Controller
Apr 24 22:28:44 greatshaitan kernel: [    5.265207] ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 1
Apr 24 22:28:44 greatshaitan kernel: [    5.265230] ehci_hcd 0000:00:0b.1: debug port 1
Apr 24 22:28:44 greatshaitan kernel: [    5.265234] ehci_hcd 0000:00:0b.1: cache line size of 32 is not supported
Apr 24 22:28:44 greatshaitan kernel: [    5.265248] ehci_hcd 0000:00:0b.1: irq 21, io mem 0xfe02e000
Apr 24 22:28:44 greatshaitan kernel: [    5.276010] ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00
Apr 24 22:28:44 greatshaitan kernel: [    5.276073] usb usb1: configuration #1 chosen from 1 choice
Apr 24 22:28:44 greatshaitan kernel: [    5.276104] hub 1-0:1.0: USB hub found
Apr 24 22:28:44 greatshaitan kernel: [    5.276111] hub 1-0:1.0: 8 ports detected
Apr 24 22:28:44 greatshaitan kernel: [    5.276204] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Apr 24 22:28:44 greatshaitan kernel: [    5.276517] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 20
Apr 24 22:28:44 greatshaitan kernel: [    5.276521] ohci_hcd 0000:00:0b.0: PCI INT A -> Link[APCF] -> GSI 20 (level, low) -> IRQ 20
Apr 24 22:28:44 greatshaitan kernel: [    5.276530] ohci_hcd 0000:00:0b.0: setting latency timer to 64
Apr 24 22:28:44 greatshaitan kernel: [    5.276533] ohci_hcd 0000:00:0b.0: OHCI Host Controller
Apr 24 22:28:44 greatshaitan kernel: [    5.276571] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 2
Apr 24 22:28:44 greatshaitan kernel: [    5.276593] ohci_hcd 0000:00:0b.0: irq 20, io mem 0xfe02f000
Apr 24 22:28:44 greatshaitan kernel: [    5.334051] usb usb2: configuration #1 chosen from 1 choice
Apr 24 22:28:44 greatshaitan kernel: [    5.334074] hub 2-0:1.0: USB hub found
Apr 24 22:28:44 greatshaitan kernel: [    5.334082] hub 2-0:1.0: 8 ports detected
Apr 24 22:28:44 greatshaitan kernel: [    5.334168] uhci_hcd: USB Universal Host Controller Interface driver
Apr 24 22:28:44 greatshaitan kernel: [    5.334210] usbcore: registered new interface driver libusual
Apr 24 22:28:44 greatshaitan kernel: [    5.334235] usbcore: registered new interface driver usbserial
Apr 24 22:28:44 greatshaitan kernel: [    5.334244] USB Serial support registered for generic
Apr 24 22:28:44 greatshaitan kernel: [    5.334256] usbcore: registered new interface driver usbserial_generic
Apr 24 22:28:44 greatshaitan kernel: [    5.334258] usbserial: USB Serial Driver core
Apr 24 22:28:44 greatshaitan kernel: [    5.334308] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Apr 24 22:28:44 greatshaitan kernel: [    5.334637] serio: i8042 KBD port at 0x60,0x64 irq 1
Apr 24 22:28:44 greatshaitan kernel: [    5.334642] serio: i8042 AUX port at 0x60,0x64 irq 12
Apr 24 22:28:44 greatshaitan kernel: [    5.336037] mice: PS/2 mouse device common for all mice
Apr 24 22:28:44 greatshaitan kernel: [    5.336168] rtc_cmos 00:05: RTC can wake from S4
Apr 24 22:28:44 greatshaitan kernel: [    5.336195] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
Apr 24 22:28:44 greatshaitan kernel: [    5.336225] rtc0: alarms up to one year, y3k, 242 bytes nvram, hpet irqs
Apr 24 22:28:44 greatshaitan kernel: [    5.336278] device-mapper: uevent: version 1.0.3
Apr 24 22:28:44 greatshaitan kernel: [    5.336353] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
Apr 24 22:28:44 greatshaitan kernel: [    5.336425] device-mapper: multipath: version 1.0.5 loaded
Apr 24 22:28:44 greatshaitan kernel: [    5.336427] device-mapper: multipath round-robin: version 1.0.0 loaded
Apr 24 22:28:44 greatshaitan kernel: [    5.336497] EISA: Probing bus 0 at eisa.0
Apr 24 22:28:44 greatshaitan kernel: [    5.336502] Cannot allocate resource for EISA slot 1
Apr 24 22:28:44 greatshaitan kernel: [    5.336523] EISA: Detected 0 cards.
Apr 24 22:28:44 greatshaitan kernel: [    5.336570] cpuidle: using governor ladder
Apr 24 22:28:44 greatshaitan kernel: [    5.336572] cpuidle: using governor menu
Apr 24 22:28:44 greatshaitan kernel: [    5.337027] TCP cubic registered
Apr 24 22:28:44 greatshaitan kernel: [    5.337112] NET: Registered protocol family 10
Apr 24 22:28:44 greatshaitan kernel: [    5.337504] lo: Disabled Privacy Extensions
Apr 24 22:28:44 greatshaitan kernel: [    5.337806] NET: Registered protocol family 17
Apr 24 22:28:44 greatshaitan kernel: [    5.337821] Bluetooth: L2CAP ver 2.11
Apr 24 22:28:44 greatshaitan kernel: [    5.337823] Bluetooth: L2CAP socket layer initialized
Apr 24 22:28:44 greatshaitan kernel: [    5.337827] Bluetooth: SCO (Voice Link) ver 0.6
Apr 24 22:28:44 greatshaitan kernel: [    5.337829] Bluetooth: SCO socket layer initialized
Apr 24 22:28:44 greatshaitan kernel: [    5.337857] Bluetooth: RFCOMM socket layer initialized
Apr 24 22:28:44 greatshaitan kernel: [    5.337862] Bluetooth: RFCOMM TTY layer initialized
Apr 24 22:28:44 greatshaitan kernel: [    5.337864] Bluetooth: RFCOMM ver 1.10
Apr 24 22:28:44 greatshaitan kernel: [    5.337906] Using IPI No-Shortcut mode
Apr 24 22:28:44 greatshaitan kernel: [    5.337965] registered taskstats version 1
Apr 24 22:28:44 greatshaitan kernel: [    5.338096]   Magic number: 5:2:461
Apr 24 22:28:44 greatshaitan kernel: [    5.338156] rtc_cmos 00:05: setting system clock to 2009-04-25 02:28:35 UTC (1240626515)
Apr 24 22:28:44 greatshaitan kernel: [    5.338159] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Apr 24 22:28:44 greatshaitan kernel: [    5.338160] EDD information not available.
Apr 24 22:28:44 greatshaitan kernel: [    5.338387] Freeing unused kernel memory: 532k freed
Apr 24 22:28:44 greatshaitan kernel: [    5.338502] Write protecting the kernel text: 4128k
Apr 24 22:28:44 greatshaitan kernel: [    5.338543] Write protecting the kernel read-only data: 1532k
Apr 24 22:28:44 greatshaitan kernel: [    5.362821] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
Apr 24 22:28:44 greatshaitan kernel: [    5.587182] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
Apr 24 22:28:44 greatshaitan kernel: [    5.587525] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 23
Apr 24 22:28:44 greatshaitan kernel: [    5.587529] forcedeth 0000:00:14.0: PCI INT A -> Link[APCH] -> GSI 23 (level, low) -> IRQ 23
Apr 24 22:28:44 greatshaitan kernel: [    5.587534] forcedeth 0000:00:14.0: setting latency timer to 64
Apr 24 22:28:44 greatshaitan kernel: [    5.613795] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
Apr 24 22:28:44 greatshaitan kernel: [    5.613801] ohci1394 0000:05:08.0: PCI INT A -> Link[APC3] -> GSI 18 (level, low) -> IRQ 18
Apr 24 22:28:44 greatshaitan kernel: [    5.666542] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[18]  MMIO=[fdaff000-fdaff7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
Apr 24 22:28:44 greatshaitan kernel: [    5.672680] nv_probe: set workaround bit for reversed mac addr
Apr 24 22:28:44 greatshaitan kernel: [    5.712659] Floppy drive(s): fd0 is 1.44M
Apr 24 22:28:44 greatshaitan kernel: [    5.816403] FDC 0 is a post-1991 82077
Apr 24 22:28:44 greatshaitan kernel: [    5.868708] usb 1-1: new high speed USB device using ehci_hcd and address 2
Apr 24 22:28:44 greatshaitan kernel: [    6.003608] usb 1-1: string descriptor 0 read error: -61
Apr 24 22:28:44 greatshaitan kernel: [    6.005857] usb 1-1: string descriptor 0 read error: -61
Apr 24 22:28:44 greatshaitan kernel: [    6.008108] usb 1-1: string descriptor 0 read error: -61
Apr 24 22:28:44 greatshaitan kernel: [    6.008172] usb 1-1: configuration #1 chosen from 1 choice
Apr 24 22:28:44 greatshaitan kernel: [    6.011504] Initializing USB Mass Storage driver...
Apr 24 22:28:44 greatshaitan kernel: [    6.012567] scsi6 : SCSI emulation for USB Mass Storage devices
Apr 24 22:28:44 greatshaitan kernel: [    6.012643] usbcore: registered new interface driver usb-storage
Apr 24 22:28:44 greatshaitan kernel: [    6.012645] USB Mass Storage support registered.
Apr 24 22:28:44 greatshaitan kernel: [    6.012699] usb-storage: device found at 2
Apr 24 22:28:44 greatshaitan kernel: [    6.012700] usb-storage: waiting for device to settle before scanning
Apr 24 22:28:44 greatshaitan kernel: [    6.193278] forcedeth 0000:00:14.0: ifname eth0, PHY OUI 0x5043 @ 1, addr 00:1a:92:82:40:a8
Apr 24 22:28:44 greatshaitan kernel: [    6.193282] forcedeth 0000:00:14.0: highdma pwrctl timirq gbit lnktim desc-v3
Apr 24 22:28:44 greatshaitan kernel: [    6.233057] PM: Starting manual resume from disk
Apr 24 22:28:44 greatshaitan kernel: [    6.233060] PM: Resume from partition 8:5
Apr 24 22:28:44 greatshaitan kernel: [    6.233062] PM: Checking hibernation image.
Apr 24 22:28:44 greatshaitan kernel: [    6.233203] PM: Resume from disk failed.
Apr 24 22:28:44 greatshaitan kernel: [    6.244172] EXT3-fs: INFO: recovery required on readonly filesystem.
Apr 24 22:28:44 greatshaitan kernel: [    6.244174] EXT3-fs: write access will be enabled during recovery.
Apr 24 22:28:44 greatshaitan kernel: [    6.761872] kjournald starting.  Commit interval 5 seconds
Apr 24 22:28:44 greatshaitan kernel: [    6.761885] EXT3-fs: sda1: orphan cleanup on readonly fs
Apr 24 22:28:44 greatshaitan kernel: [    6.761890] ext3_orphan_cleanup: deleting unreferenced inode 22044722
Apr 24 22:28:44 greatshaitan kernel: [    6.761917] ext3_orphan_cleanup: deleting unreferenced inode 22044721
Apr 24 22:28:44 greatshaitan kernel: [    6.761928] ext3_orphan_cleanup: deleting unreferenced inode 22044719
Apr 24 22:28:44 greatshaitan kernel: [    6.761937] ext3_orphan_cleanup: deleting unreferenced inode 22044718
Apr 24 22:28:44 greatshaitan kernel: [    6.761947] ext3_orphan_cleanup: deleting unreferenced inode 25289262
Apr 24 22:28:44 greatshaitan kernel: [    6.761956] ext3_orphan_cleanup: deleting unreferenced inode 22044695
Apr 24 22:28:44 greatshaitan kernel: [    6.761962] EXT3-fs: sda1: 6 orphan inodes deleted
Apr 24 22:28:44 greatshaitan kernel: [    6.761963] EXT3-fs: recovery complete.
Apr 24 22:28:44 greatshaitan kernel: [    6.766001] EXT3-fs: mounted filesystem with ordered data mode.
Apr 24 22:28:44 greatshaitan kernel: [    6.944113] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0011d800012baa60]
Apr 24 22:28:44 greatshaitan kernel: [   10.883350] udev: starting version 141
Apr 24 22:28:44 greatshaitan kernel: [   11.017991] usb-storage: device scan complete
Apr 24 22:28:44 greatshaitan kernel: [   11.021493] scsi 6:0:0:0: Direct-Access     Seagate  External Drive        PQ: 0 ANSI: 0
Apr 24 22:28:44 greatshaitan kernel: [   11.022475] sd 6:0:0:0: [sdc] 488397168 512-byte hardware sectors: (250 GB/232 GiB)
Apr 24 22:28:44 greatshaitan kernel: [   11.023347] sd 6:0:0:0: [sdc] Write Protect is off
Apr 24 22:28:44 greatshaitan kernel: [   11.023349] sd 6:0:0:0: [sdc] Mode Sense: 27 00 00 00
Apr 24 22:28:44 greatshaitan kernel: [   11.023352] sd 6:0:0:0: [sdc] Assuming drive cache: write through
Apr 24 22:28:44 greatshaitan kernel: [   11.023973] sd 6:0:0:0: [sdc] 488397168 512-byte hardware sectors: (250 GB/232 GiB)
Apr 24 22:28:44 greatshaitan kernel: [   11.024881] sd 6:0:0:0: [sdc] Write Protect is off
Apr 24 22:28:44 greatshaitan kernel: [   11.024883] sd 6:0:0:0: [sdc] Mode Sense: 27 00 00 00
Apr 24 22:28:44 greatshaitan kernel: [   11.024885] sd 6:0:0:0: [sdc] Assuming drive cache: write through
Apr 24 22:28:44 greatshaitan kernel: [   11.024889]  sdc: sdc1
Apr 24 22:28:44 greatshaitan kernel: [   11.043659] sd 6:0:0:0: [sdc] Attached SCSI disk
Apr 24 22:28:44 greatshaitan kernel: [   11.043777] sd 6:0:0:0: Attached scsi generic sg3 type 0
Apr 24 22:28:44 greatshaitan kernel: [   11.426516] parport_pc 00:0a: reported by Plug and Play ACPI
Apr 24 22:28:44 greatshaitan kernel: [   11.426542] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
Apr 24 22:28:44 greatshaitan kernel: [   11.439876] Linux agpgart interface v0.103
Apr 24 22:28:44 greatshaitan kernel: [   11.459356] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x1c00
Apr 24 22:28:44 greatshaitan kernel: [   11.459394] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x1c80
Apr 24 22:28:44 greatshaitan kernel: [   11.486579] input: PC Speaker as /devices/platform/pcspkr/input/input4
Apr 24 22:28:44 greatshaitan kernel: [   11.503988] ppdev: user-space parallel port driver
Apr 24 22:28:44 greatshaitan kernel: [   11.585362] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
Apr 24 22:28:44 greatshaitan kernel: [   11.611567] nvidia: module license 'NVIDIA' taints kernel.
Apr 24 22:28:44 greatshaitan kernel: [   11.754123] ACPI: PCI Interrupt Link [APC1] enabled at IRQ 16
Apr 24 22:28:44 greatshaitan kernel: [   11.754132] C-Media PCI 0000:05:06.0: PCI INT A -> Link[APC1] -> GSI 16 (level, low) -> IRQ 16
Apr 24 22:28:44 greatshaitan kernel: [   11.864900] ACPI: PCI Interrupt Link [APC5] enabled at IRQ 16
Apr 24 22:28:44 greatshaitan kernel: [   11.864904] nvidia 0000:01:00.0: PCI INT A -> Link[APC5] -> GSI 16 (level, low) -> IRQ 16
Apr 24 22:28:44 greatshaitan kernel: [   11.864910] nvidia 0000:01:00.0: setting latency timer to 64
Apr 24 22:28:44 greatshaitan kernel: [   11.865816] NVRM: loading NVIDIA UNIX x86 Kernel Module  180.44  Mon Mar 23 14:59:10 PST 2009
Apr 24 22:28:44 greatshaitan kernel: [   11.990016] lp0: using parport0 (interrupt-driven).
Apr 24 22:28:44 greatshaitan kernel: [   12.054819] Adding 10586792k swap on /dev/sda5.  Priority:-1 extents:1 across:10586792k
Apr 24 22:28:44 greatshaitan kernel: [   12.072048] psmouse serio1: ID: 10 00 64<6>EXT3 FS on sda1, internal journal
Apr 24 22:28:44 greatshaitan kernel: [   12.701072] input: ImPS/2 Logitech Wheel Mouse as /devices/platform/i8042/serio1/input/input5
Apr 24 22:28:44 greatshaitan kernel: [   13.428266] type=1505 audit(1240626523.589:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2161
Apr 24 22:28:44 greatshaitan kernel: [   13.469029] type=1505 audit(1240626523.629:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2165
Apr 24 22:28:44 greatshaitan kernel: [   13.469099] type=1505 audit(1240626523.629:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2165
Apr 24 22:28:44 greatshaitan kernel: [   13.469132] type=1505 audit(1240626523.629:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2165
Apr 24 22:28:44 greatshaitan kernel: [   13.469167] type=1505 audit(1240626523.629:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2165
Apr 24 22:28:44 greatshaitan kernel: [   13.582456] type=1505 audit(1240626523.742:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2170
Apr 24 22:28:44 greatshaitan kernel: [   13.582587] type=1505 audit(1240626523.742:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2170
Apr 24 22:28:44 greatshaitan kernel: [   13.606686] type=1505 audit(1240626523.766:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2174
Apr 24 22:28:46 greatshaitan kernel: [   16.143130] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Apr 24 22:28:46 greatshaitan kernel: [   16.143133] Bluetooth: BNEP filters: protocol multicast
Apr 24 22:28:46 greatshaitan kernel: [   16.150384] Bridge firewalling registered
Apr 24 22:29:02 greatshaitan kernel: [   31.176506] eth0: no IPv6 routers present
Apr 24 22:30:17 greatshaitan kernel: [  106.300484] NVRM: Xid (0001:00): 6, PE0000 0bc8 ffdddddd 00008d1c 00000000 ffdddddd


XORG.0.LOG


X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux greatshaitan 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686
Build Date: 09 April 2009  02:10:02AM
xorg-server 2:1.6.0-0ubuntu14 (buildd@rothera.buildd) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Apr 24 22:28:46 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
	If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(II) Loader magic: 0x3bc0
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 5.0
	X.Org XInput driver : 4.0
	X.Org Server Extension : 2.0
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0@1:0:0) nVidia Corporation G72 [GeForce 7300 LE] rev 161, Mem @ 0xfa000000/16777216, 0xe0000000/268435456, 0xfb000000/16777216, BIOS @ 0x????????/131072
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) "dri2" will be loaded by default.
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
(II) NVIDIA GLX Module  180.44  Mon Mar 23 15:29:02 PST 2009
(II) Loading extension GLX
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Video Driver
(II) NVIDIA dlloader X Driver  180.44  Mon Mar 23 15:05:32 PST 2009
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01@00:00:0
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules//libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(II) resource ranges after probing:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce 7300 LE (G72) at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 524288 kBytes
(--) NVIDIA(0): VideoBIOS: 05.72.22.43.05
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 7300 LE at PCI:1:0:0:
(--) NVIDIA(0):     LG L226W (DFP-0)
(--) NVIDIA(0): LG L226W (DFP-0): 165.0 MHz maximum pixel clock
(--) NVIDIA(0): LG L226W (DFP-0): Internal Single Link TMDS
(II) NVIDIA(0): Assigned Display Device: DFP-0
(==) NVIDIA(0): 
(==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
(==) NVIDIA(0):     will be used as the requested mode.
(==) NVIDIA(0): 
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "nvidia-auto-select"
(**) NVIDIA(0): Virtual screen size configured to be 1280 x 1024
(--) NVIDIA(0): DPI set to (66, 81); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) NVIDIA(0): Initialized GPU GART.
(II) NVIDIA(0): Setting mode "nvidia-auto-select"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(==) NVIDIA(0): Disabling shared memory pixmaps
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(II) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(II) Loading extension XINERAMA
(==) RandR enabled
(II) Initializing built-in extension Generic Event Extension
(II) Initializing built-in extension SHAPE
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension BIG-REQUESTS
(II) Initializing built-in extension SYNC
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-MISC
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing extension GLX
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 2.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) AT Translated Set 2 keyboard: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) AT Translated Set 2 keyboard: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) AT Translated Set 2 keyboard: xkb_layout: "us"
(II) config/hal: Adding input device Macintosh mouse button emulation
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event2"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: (accel) keeping acceleration scheme 1
(**) Macintosh mouse button emulation: (accel) filter chain progression: 2.00
(**) Macintosh mouse button emulation: (accel) filter stage 0: 20.00 ms
(**) Macintosh mouse button emulation: (accel) set acceleration profile 0
(II) config/hal: Adding input device ImPS/2 Logitech Wheel Mouse
(**) ImPS/2 Logitech Wheel Mouse: always reports core events
(**) ImPS/2 Logitech Wheel Mouse: Device: "/dev/input/event5"
(II) ImPS/2 Logitech Wheel Mouse: Found 3 mouse buttons
(II) ImPS/2 Logitech Wheel Mouse: Found x and y relative axes
(II) ImPS/2 Logitech Wheel Mouse: Configuring as mouse
(**) ImPS/2 Logitech Wheel Mouse: YAxisMapping: buttons 4 and 5
(**) ImPS/2 Logitech Wheel Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "ImPS/2 Logitech Wheel Mouse" (type: MOUSE)
(**) ImPS/2 Logitech Wheel Mouse: (accel) keeping acceleration scheme 1
(**) ImPS/2 Logitech Wheel Mouse: (accel) filter chain progression: 2.00
(**) ImPS/2 Logitech Wheel Mouse: (accel) filter stage 0: 20.00 ms
(**) ImPS/2 Logitech Wheel Mouse: (accel) set acceleration profile 0
(II) NVIDIA(0): Setting mode "1024x768"
(II) NVIDIA(0): Initialized GPU GART.

michael@greatshaitan:~$ lspci
00:00.0 Host bridge: nVidia Corporation C55 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a2)
00:00.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.7 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:03.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1)
00:05.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1)
00:06.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1)
00:07.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:0f.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
01:00.0 VGA compatible controller: nVidia Corporation G72 [GeForce 7300 LE] (rev a1)
05:06.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
05:08.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev c0)

```

I hope this issue can get resolved...I hate being forced to use my Windoze machine. :confused:

---

### Post by psychomichael on 2009-04-25
bump for the cause...

---

### Post by dirk_k on 2009-04-27
I had the same problem just now. But i have a complete log, thus maybe this is another bug. But the screen froze completely, although after about 3 seconds I saw my firefox window go dark as normal with unresponsive programs. There was therefore still something running, although it is a serious kernel bug: kjournald seems crashing.
It happened after about 2 minutes from a resume from hibernation and I just had started firefox (resuming a session with about 50+ tabs) plus audacious.

kjournald     D ffff8800ad055e48     0  4327      2
 ffff8800ad055dd0 0000000000000046 ffff880037908038 ffff8800010294a0 
 ffffffff807a6400 ffffffff807a6400 ffffffff807a6400 ffffffff807a6400 
 ffffffff807a6400 ffffffff807a6400 ffffffff807a6400 ffffffff807a6400 
Call Trace:
 [<ffffffffa01d2b71>] journal_commit_transaction+0x111/0xd00 [jbd]
 [<ffffffff8025a92b>] ? lock_timer_base+0x3b/0x70
 [<ffffffff80267120>] ? autoremove_wake_function+0x0/0x40
 [<ffffffff8025a9bf>] ? try_to_del_timer_sync+0x5f/0x70
 [<ffffffffa01d6ea9>] kjournald+0xe9/0x250 [jbd]
 [<ffffffff80267120>] ? autoremove_wake_function+0x0/0x40
 [<ffffffffa01d6dc0>] ? kjournald+0x0/0x250 [jbd]
 [<ffffffff80266cee>] kthread+0x4e/0x90
 [<ffffffff80213c99>] child_rip+0xa/0x11
 [<ffffffff80266ca0>] ? kthread+0x0/0x90
 [<ffffffff80213c8f>] ? child_rip+0x0/0x11

---

### Post by psychomichael on 2009-04-27
Yeah, you seem to have been doing more memory-intensive stuff than I was. I only had three tabs open and checking my Myspace at the time. I'm wondering if it isn't the NVIDIA bug because it doesn't crash until I use Firefox.

---

### Post by billgoldberg on 2009-04-27
I'm having the same problem.

But I also seem to have the "magically back to login window" problem.

I'm hoping updates will solve this soon.

---

### Post by psychomichael on 2009-04-28
As usual, the silence is deafening. It happened this time when I scrolled too fast to the bottom of a text file.

Here's my /var/log/messages.log:

```
Apr 28 08:23:59 greatshaitan -- MARK --
Apr 28 08:33:38 greatshaitan syslogd 1.5.0#5ubuntu3: restart.
Apr 28 08:33:38 greatshaitan kernel: Inspecting /boot/System.map-2.6.28-11-generic
Apr 28 08:33:38 greatshaitan kernel: Cannot find map file.
Apr 28 08:33:38 greatshaitan kernel: Loaded 72233 symbols from 42 modules.
Apr 28 08:33:38 greatshaitan kernel: [    0.000000] BIOS EBDA/lowmem at: 0009f000/0009f000
Apr 28 08:33:38 greatshaitan kernel: [    0.000000] Initializing cgroup subsys cpuset
Apr 28 08:33:38 greatshaitan kernel: [    0.000000] Initializing cgroup subsys cpu
Apr 28 08:33:38 greatshaitan kernel: [    0.000000] Linux version 2.6.28-11-generic (buildd@palmer) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 (Ubuntu 2.6.28-11.42-generic)
Apr 28 08:33:38 greatshaitan kernel: [    0.000000] KERNEL supported cpus:
Apr 28 08:33:38 greatshaitan kernel: [    0.000000]   Intel GenuineIntel
Apr 28 08:33:38 greatshaitan kernel: [    0.000000]   AMD AuthenticAMD
Apr 28 08:33:38 greatshaitan kernel: [    0.000000]   NSC Geode by NSC
Apr 28 08:33:38 greatshaitan kernel: [    0.000000]   Cyrix CyrixInstead
Apr 28 08:33:38 greatshaitan kernel: [    0.000000]   Centaur CentaurHauls
Apr 28 08:33:38 greatshaitan kernel: [    0.000000]   Transmeta GenuineTMx86
Apr 28 08:33:38 greatshaitan kernel: [    0.000000]   Transmeta TransmetaCPU
Apr 28 08:33:38 greatshaitan kernel: [    0.000000]   UMC UMC UMC UMC
Apr 28 08:33:38 greatshaitan kernel: [    0.000000] BIOS-provided physical RAM map:
Apr 28 08:33:38 greatshaitan kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
Apr 28 08:33:38 greatshaitan kernel: [    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
Apr 28 08:33:38 greatshaitan kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Apr 28 08:33:38 greatshaitan kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 00000000dfef0000 (usable)
Apr 28 08:33:38 greatshaitan kernel: [    0.000000]  BIOS-e820: 00000000dfef0000 - 00000000dfef3000 (ACPI NVS)
Apr 28 08:33:38 greatshaitan kernel: [    0.000000]  BIOS-e820: 00000000dfef3000 - 00000000dff00000 (ACPI data)
Apr 28 08:33:38 greatshaitan kernel: [    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f2000000 (reserved)
Apr 28 08:33:38 greatshaitan kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
Apr 28 08:33:38 greatshaitan kernel: [    0.000000]  BIOS-e820: 0000000100000000 - 0000000120000000 (usable)
Apr 28 08:33:38 greatshaitan kernel: [    0.000000] DMI 2.4 present.
Apr 28 08:33:38 greatshaitan kernel: [    0.000000] Phoenix BIOS detected: BIOS may corrupt low RAM, working it around.
Apr 28 08:33:38 greatshaitan kernel: [    0.000000] last_pfn = 0xdfef0 max_arch_pfn = 0x100000
Apr 28 08:33:38 greatshaitan kernel: [    0.000000] Scanning 0 areas for low memory corruption
Apr 28 08:33:38 greatshaitan kernel: [    0.000000] modified physical RAM map:
Apr 28 08:33:38 greatshaitan kernel: [    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
Apr 28 08:33:38 greatshaitan kernel: [    0.000000]  modified: 0000000000010000 - 000000000009f000 (usable)
Apr 28 08:33:38 greatshaitan kernel: [    0.000000]  modified: 000000000009f000 - 00000000000a0000 (reserved)
Apr 28 08:33:38 greatshaitan kernel: [    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
Apr 28 08:33:38 greatshaitan kernel: [    0.000000]  modified: 0000000000100000 - 00000000dfef0000 (usable)
Apr 28 08:33:38 greatshaitan kernel: [    0.000000]  modified: 00000000dfef0000 - 00000000dfef3000 (ACPI NVS)
Apr 28 08:33:38 greatshaitan kernel: [    0.000000]  modified: 00000000dfef3000 - 00000000dff00000 (ACPI data)
Apr 28 08:33:38 greatshaitan kernel: [    0.000000]  modified: 00000000f0000000 - 00000000f2000000 (reserved)
Apr 28 08:33:38 greatshaitan kernel: [    0.000000]  modified: 00000000fec00000 - 0000000100000000 (reserved)
Apr 28 08:33:38 greatshaitan kernel: [    0.000000]  modified: 0000000100000000 - 0000000120000000 (usable)
Apr 28 08:33:38 greatshaitan kernel: [    0.000000] RAMDISK: 378be000 - 37fefdf3
Apr 28 08:33:38 greatshaitan kernel: [    0.000000] Allocated new RAMDISK: 00881000 - 00fb2df3
Apr 28 08:33:38 greatshaitan kernel: [    0.000000] Move RAMDISK from 00000000378be000 - 0000000037fefdf2 to 00881000 - 00fb2df2
Apr 28 08:33:38 greatshaitan kernel: [    0.000000] ACPI: RSDP 000F7630, 0024 (r2 Nvidia)
Apr 28 08:33:38 greatshaitan kernel: [    0.000000] ACPI: XSDT DFEF30C0, 0044 (r1 Nvidia ASUSACPI 42302E31 AWRD        0)
Apr 28 08:33:38 greatshaitan kernel: [    0.000000] ACPI: FACP DFEF9700, 00F4 (r3 Nvidia ASUSACPI 42302E31 AWRD        0)
Apr 28 08:33:38 greatshaitan kernel: [    0.000000] FADT: X_PM1a_EVT_BLK.bit_width (8) does not match PM1_EVT_LEN (4)
Apr 28 08:33:38 greatshaitan kernel: [    0.000000] ACPI: DSDT DFEF3240, 6472 (r1 NVIDIA ASUSACPI     1000 MSFT  3000000)
Apr 28 08:33:38 greatshaitan kernel: [    0.000000] ACPI: FACS DFEF0000, 0040
Apr 28 08:33:38 greatshaitan kernel: [    0.000000] ACPI: HPET DFEF9940, 0038 (r1 Nvidia ASUSACPI 42302E31 AWRD       98)
Apr 28 08:33:38 greatshaitan kernel: [    0.000000] ACPI: MCFG DFEF99C0, 003C (r1 Nvidia ASUSACPI 42302E31 AWRD        0)
Apr 28 08:33:38 greatshaitan kernel: [    0.000000] ACPI: APIC DFEF9840, 0098 (r1 Nvidia ASUSACPI 42302E31 AWRD        0)
Apr 28 08:33:38 greatshaitan kernel: [    0.000000] 2698MB HIGHMEM available.
Apr 28 08:33:38 greatshaitan kernel: [    0.000000] 883MB LOWMEM available.
Apr 28 08:33:38 greatshaitan kernel: [    0.000000]   mapped low ram: 0 - 373fe000
Apr 28 08:33:38 greatshaitan kernel: [    0.000000]   low ram: 00000000 - 373fe000
Apr 28 08:33:38 greatshaitan kernel: [    0.000000]   bootmap 00012000 - 00018e80
Apr 28 08:33:38 greatshaitan kernel: [    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00373fe000]
Apr 28 08:33:38 greatshaitan kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
Apr 28 08:33:38 greatshaitan kernel: [    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
Apr 28 08:33:38 greatshaitan kernel: [    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
Apr 28 08:33:38 greatshaitan kernel: [    0.000000]   #3 [0000100000 - 000087c52c]    TEXT DATA BSS ==> [0000100000 - 000087c52c]
Apr 28 08:33:38 greatshaitan kernel: [    0.000000]   #4 [000087d000 - 0000881000]    INIT_PG_TABLE ==> [000087d000 - 0000881000]
Apr 28 08:33:38 greatshaitan kernel: [    0.000000]   #5 [000009f000 - 0000100000]    BIOS reserved ==> [000009f000 - 0000100000]
Apr 28 08:33:38 greatshaitan kernel: [    0.000000]   #6 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]
Apr 28 08:33:38 greatshaitan kernel: [    0.000000]   #7 [0000881000 - 0000fb2df3]      NEW RAMDISK ==> [0000881000 - 0000fb2df3]
Apr 28 08:33:38 greatshaitan kernel: [    0.000000]   #8 [0000012000 - 0000019000]          BOOTMAP ==> [0000012000 - 0000019000]
Apr 28 08:33:38 greatshaitan kernel: [    0.000000] found SMP MP-table at [c00f5bb0] 000f5bb0
Apr 28 08:33:38 greatshaitan kernel: [    0.000000] Zone PFN ranges:
Apr 28 08:33:38 greatshaitan kernel: [    0.000000]   DMA      0x00000010 -> 0x00001000
Apr 28 08:33:38 greatshaitan kernel: [    0.000000]   Normal   0x00001000 -> 0x000373fe
Apr 28 08:33:38 greatshaitan kernel: [    0.000000]   HighMem  0x000373fe -> 0x000dfef0
Apr 28 08:33:38 greatshaitan kernel: [    0.000000] Movable zone start PFN for each node
Apr 28 08:33:38 greatshaitan kernel: [    0.000000] early_node_map[2] active PFN ranges
Apr 28 08:33:38 greatshaitan kernel: [    0.000000]     0: 0x00000010 -> 0x0000009f
Apr 28 08:33:38 greatshaitan kernel: [    0.000000]     0: 0x00000100 -> 0x000dfef0
Apr 28 08:33:38 greatshaitan kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
Apr 28 08:33:38 greatshaitan kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Apr 28 08:33:38 greatshaitan kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Apr 28 08:33:38 greatshaitan kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
Apr 28 08:33:38 greatshaitan kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
Apr 28 08:33:38 greatshaitan kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Apr 28 08:33:38 greatshaitan kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Apr 28 08:33:38 greatshaitan kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
Apr 28 08:33:38 greatshaitan kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
Apr 28 08:33:38 greatshaitan kernel: [    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
Apr 28 08:33:38 greatshaitan kernel: [    0.000000] IOAPIC[0]: apic_id 4, version 17, address 0xfec00000, GSI 0-23
Apr 28 08:33:38 greatshaitan kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Apr 28 08:33:38 greatshaitan kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Apr 28 08:33:38 greatshaitan kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
Apr 28 08:33:38 greatshaitan kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
Apr 28 08:33:38 greatshaitan kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Apr 28 08:33:38 greatshaitan kernel: [    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfeff0000
Apr 28 08:33:38 greatshaitan kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Apr 28 08:33:38 greatshaitan kernel: [    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
Apr 28 08:33:38 greatshaitan kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Apr 28 08:33:38 greatshaitan kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
Apr 28 08:33:38 greatshaitan kernel: [    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
Apr 28 08:33:38 greatshaitan kernel: [    0.000000] Allocating PCI resources starting at e0000000 (gap: dff00000:10100000)
Apr 28 08:33:38 greatshaitan kernel: [    0.000000] PERCPU: Allocating 45056 bytes of per cpu data
Apr 28 08:33:38 greatshaitan kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 909953
Apr 28 08:33:38 greatshaitan kernel: [    0.000000] Kernel command line: root=UUID=5aa2466e-fc56-4b4f-a672-23c2cf891ac0 ro quiet splash 
Apr 28 08:33:38 greatshaitan kernel: [    0.000000] Enabling fast FPU save and restore... done.
Apr 28 08:33:38 greatshaitan kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Apr 28 08:33:38 greatshaitan kernel: [    0.000000] Initializing CPU#0
Apr 28 08:33:38 greatshaitan kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Apr 28 08:33:38 greatshaitan kernel: [    0.000000] Extended CMOS year: 2000
Apr 28 08:33:38 greatshaitan kernel: [    0.000000] Fast TSC calibration using PIT
Apr 28 08:33:38 greatshaitan kernel: [    0.000000] Detected 2133.051 MHz processor.
Apr 28 08:33:38 greatshaitan kernel: [    0.004000] Console: colour VGA+ 80x25
Apr 28 08:33:38 greatshaitan kernel: [    0.004000] console [tty0] enabled
Apr 28 08:33:38 greatshaitan kernel: [    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Apr 28 08:33:38 greatshaitan kernel: [    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Apr 28 08:33:38 greatshaitan kernel: [    0.004000] allocated 18344320 bytes of page_cgroup
Apr 28 08:33:38 greatshaitan kernel: [    0.004000] please try cgroup_disable=memory option if you don't want
Apr 28 08:33:38 greatshaitan kernel: [    0.004000] Scanning for low memory corruption every 60 seconds
Apr 28 08:33:38 greatshaitan kernel: [    0.004000] Memory: 3604904k/3668928k available (4126k kernel code, 62700k reserved, 2208k data, 532k init, 2763720k highmem)
Apr 28 08:33:38 greatshaitan kernel: [    0.004000] virtual kernel memory layout:
Apr 28 08:33:38 greatshaitan kernel: [    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
Apr 28 08:33:38 greatshaitan kernel: [    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
Apr 28 08:33:38 greatshaitan kernel: [    0.004000]     vmalloc : 0xf7bfe000 - 0xff3fe000   ( 120 MB)
Apr 28 08:33:38 greatshaitan kernel: [    0.004000]     lowmem  : 0xc0000000 - 0xf73fe000   ( 883 MB)
Apr 28 08:33:38 greatshaitan kernel: [    0.004000]       .init : 0xc0737000 - 0xc07bc000   ( 532 kB)
Apr 28 08:33:38 greatshaitan kernel: [    0.004000]       .data : 0xc0507a6f - 0xc072fe60   (2208 kB)
Apr 28 08:33:38 greatshaitan kernel: [    0.004000]       .text : 0xc0100000 - 0xc0507a6f   (4126 kB)
Apr 28 08:33:38 greatshaitan kernel: [    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Apr 28 08:33:38 greatshaitan kernel: [    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
Apr 28 08:33:38 greatshaitan kernel: [    0.004000] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
Apr 28 08:33:38 greatshaitan kernel: [    0.004000] Calibrating delay loop (skipped), value calculated using timer frequency.. 4266.10 BogoMIPS (lpj=8532204)
Apr 28 08:33:38 greatshaitan kernel: [    0.004000] Security Framework initialized
Apr 28 08:33:38 greatshaitan kernel: [    0.004000] SELinux:  Disabled at boot.
Apr 28 08:33:38 greatshaitan kernel: [    0.004000] AppArmor: AppArmor initialized
Apr 28 08:33:38 greatshaitan kernel: [    0.004000] Mount-cache hash table entries: 512
Apr 28 08:33:38 greatshaitan kernel: [    0.004000] Initializing cgroup subsys ns
Apr 28 08:33:38 greatshaitan kernel: [    0.004000] Initializing cgroup subsys cpuacct
Apr 28 08:33:38 greatshaitan kernel: [    0.004000] Initializing cgroup subsys memory
Apr 28 08:33:38 greatshaitan kernel: [    0.004000] Initializing cgroup subsys freezer
Apr 28 08:33:38 greatshaitan kernel: [    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
Apr 28 08:33:38 greatshaitan kernel: [    0.004000] CPU: L2 cache: 4096K
Apr 28 08:33:38 greatshaitan kernel: [    0.004000] CPU: Physical Processor ID: 0
Apr 28 08:33:38 greatshaitan kernel: [    0.004000] CPU: Processor Core ID: 0
Apr 28 08:33:38 greatshaitan kernel: [    0.004000] using mwait in idle threads.
Apr 28 08:33:38 greatshaitan kernel: [    0.004000] Checking 'hlt' instruction... OK.
Apr 28 08:33:38 greatshaitan kernel: [    0.018139] ACPI: Core revision 20080926
Apr 28 08:33:38 greatshaitan kernel: [    0.019422] ACPI: Checking initramfs for custom DSDT
Apr 28 08:33:38 greatshaitan kernel: [    0.296341] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Apr 28 08:33:38 greatshaitan kernel: [    0.336030] CPU0: Intel(R) Core(TM)2 CPU          6420  @ 2.13GHz stepping 06
Apr 28 08:33:38 greatshaitan kernel: [    0.340001] Booting processor 1 APIC 0x1 ip 0x6000
Apr 28 08:33:38 greatshaitan kernel: [    0.004000] Initializing CPU#1
Apr 28 08:33:38 greatshaitan kernel: [    0.004000] Calibrating delay using timer specific routine.. 4266.65 BogoMIPS (lpj=8533303)
Apr 28 08:33:38 greatshaitan kernel: [    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
Apr 28 08:33:38 greatshaitan kernel: [    0.004000] CPU: L2 cache: 4096K
Apr 28 08:33:38 greatshaitan kernel: [    0.004000] CPU: Physical Processor ID: 0
Apr 28 08:33:38 greatshaitan kernel: [    0.004000] CPU: Processor Core ID: 1
Apr 28 08:33:38 greatshaitan kernel: [    0.424617] CPU1: Intel(R) Core(TM)2 CPU          6420  @ 2.13GHz stepping 06
Apr 28 08:33:38 greatshaitan kernel: [    0.424631] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
Apr 28 08:33:38 greatshaitan kernel: [    0.428030] Brought up 2 CPUs
Apr 28 08:33:38 greatshaitan kernel: [    0.428033] Total of 2 processors activated (8532.75 BogoMIPS).
Apr 28 08:33:38 greatshaitan kernel: [    0.428185] net_namespace: 776 bytes
Apr 28 08:33:38 greatshaitan kernel: [    0.428185] Booting paravirtualized kernel on bare hardware
Apr 28 08:33:38 greatshaitan kernel: [    0.428292] Time: 12:33:23  Date: 04/28/09
Apr 28 08:33:38 greatshaitan kernel: [    0.428292] regulator: core version 0.5
Apr 28 08:33:38 greatshaitan kernel: [    0.428292] NET: Registered protocol family 16
Apr 28 08:33:38 greatshaitan kernel: [    0.428292] EISA bus registered
Apr 28 08:33:38 greatshaitan kernel: [    0.428292] ACPI: bus type pci registered
Apr 28 08:33:38 greatshaitan kernel: [    0.428292] PCI: MCFG configuration 0: base f0000000 segment 0 buses 0 - 31
Apr 28 08:33:38 greatshaitan kernel: [    0.428292] PCI: MCFG area at f0000000 reserved in E820
Apr 28 08:33:38 greatshaitan kernel: [    0.428292] PCI: Using MMCONFIG for extended config space
Apr 28 08:33:38 greatshaitan kernel: [    0.428292] PCI: Using configuration type 1 for base access
Apr 28 08:33:38 greatshaitan kernel: [    0.428292] mtrr: your CPUs had inconsistent fixed MTRR settings
Apr 28 08:33:38 greatshaitan kernel: [    0.428292] mtrr: probably your BIOS does not setup all CPUs.
Apr 28 08:33:38 greatshaitan kernel: [    0.428292] mtrr: corrected configuration.
Apr 28 08:33:38 greatshaitan kernel: [    0.440069] ACPI: Interpreter enabled
Apr 28 08:33:38 greatshaitan kernel: [    0.440074] ACPI: (supports S0 S1 S3 S4 S5)
Apr 28 08:33:38 greatshaitan kernel: [    0.440097] ACPI: Using IOAPIC for interrupt routing
Apr 28 08:33:38 greatshaitan kernel: [    0.449335] ACPI: No dock devices found.
Apr 28 08:33:38 greatshaitan kernel: [    0.449346] ACPI: PCI Root Bridge [PCI0] (0000:00)
Apr 28 08:33:38 greatshaitan kernel: [    0.450189] pci 0000:00:03.0: PME# supported from D0 D1 D2 D3hot D3cold
Apr 28 08:33:38 greatshaitan kernel: [    0.450192] pci 0000:00:03.0: PME# disabled
Apr 28 08:33:38 greatshaitan kernel: [    0.450230] pci 0000:00:05.0: PME# supported from D0 D1 D2 D3hot D3cold
Apr 28 08:33:38 greatshaitan kernel: [    0.450233] pci 0000:00:05.0: PME# disabled
Apr 28 08:33:38 greatshaitan kernel: [    0.450272] pci 0000:00:06.0: PME# supported from D0 D1 D2 D3hot D3cold
Apr 28 08:33:38 greatshaitan kernel: [    0.450275] pci 0000:00:06.0: PME# disabled
Apr 28 08:33:38 greatshaitan kernel: [    0.450312] pci 0000:00:07.0: PME# supported from D0 D1 D2 D3hot D3cold
Apr 28 08:33:38 greatshaitan kernel: [    0.450314] pci 0000:00:07.0: PME# disabled
Apr 28 08:33:38 greatshaitan kernel: [    0.450569] pci 0000:00:0a.1: PME# supported from D3hot D3cold
Apr 28 08:33:38 greatshaitan kernel: [    0.450575] pci 0000:00:0a.1: PME# disabled
Apr 28 08:33:38 greatshaitan kernel: [    0.450678] pci 0000:00:0b.0: PME# supported from D0 D1 D2 D3hot D3cold
Apr 28 08:33:38 greatshaitan kernel: [    0.450682] pci 0000:00:0b.0: PME# disabled
Apr 28 08:33:38 greatshaitan kernel: [    0.450742] pci 0000:00:0b.1: PME# supported from D0 D1 D2 D3hot D3cold
Apr 28 08:33:38 greatshaitan kernel: [    0.450746] pci 0000:00:0b.1: PME# disabled
Apr 28 08:33:38 greatshaitan kernel: [    0.451048] pci 0000:00:14.0: PME# supported from D0 D1 D2 D3hot D3cold
Apr 28 08:33:38 greatshaitan kernel: [    0.451052] pci 0000:00:14.0: PME# disabled
Apr 28 08:33:38 greatshaitan kernel: [    0.451492] pci 0000:05:08.0: PME# supported from D2 D3hot D3cold
Apr 28 08:33:38 greatshaitan kernel: [    0.451496] pci 0000:05:08.0: PME# disabled
Apr 28 08:33:38 greatshaitan kernel: [    0.451530] pci 0000:00:10.0: transparent bridge
Apr 28 08:33:38 greatshaitan kernel: [    0.529031] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 9 *10 11 14 15)
Apr 28 08:33:38 greatshaitan kernel: [    0.529207] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Apr 28 08:33:38 greatshaitan kernel: [    0.529383] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 9 *10 11 14 15)
Apr 28 08:33:38 greatshaitan kernel: [    0.529556] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Apr 28 08:33:38 greatshaitan kernel: [    0.529736] ACPI: PCI Interrupt Link [LNK5] (IRQs 5 7 9 10 *11 14 15)
Apr 28 08:33:38 greatshaitan kernel: [    0.529909] ACPI: PCI Interrupt Link [LNK6] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Apr 28 08:33:38 greatshaitan kernel: [    0.530083] ACPI: PCI Interrupt Link [LNK7] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Apr 28 08:33:38 greatshaitan kernel: [    0.530256] ACPI: PCI Interrupt Link [LNK8] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Apr 28 08:33:38 greatshaitan kernel: [    0.530431] ACPI: PCI Interrupt Link [LUBA] (IRQs 5 7 9 *10 11 14 15)
Apr 28 08:33:38 greatshaitan kernel: [    0.530603] ACPI: PCI Interrupt Link [LUBB] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Apr 28 08:33:38 greatshaitan kernel: [    0.530778] ACPI: PCI Interrupt Link [LMAC] (IRQs *5 7 9 10 11 14 15)
Apr 28 08:33:38 greatshaitan kernel: [    0.530954] ACPI: PCI Interrupt Link [LACI] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Apr 28 08:33:38 greatshaitan kernel: [    0.531128] ACPI: PCI Interrupt Link [LAZA] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Apr 28 08:33:38 greatshaitan kernel: [    0.531302] ACPI: PCI Interrupt Link [LPMU] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Apr 28 08:33:38 greatshaitan kernel: [    0.531475] ACPI: PCI Interrupt Link [LMCI] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Apr 28 08:33:38 greatshaitan kernel: [    0.531649] ACPI: PCI Interrupt Link [LSMB] (IRQs 5 7 9 10 *11 14 15)
Apr 28 08:33:38 greatshaitan kernel: [    0.531822] ACPI: PCI Interrupt Link [LUB2] (IRQs 5 7 9 10 *11 14 15)
Apr 28 08:33:38 greatshaitan kernel: [    0.531994] ACPI: PCI Interrupt Link [LIDE] (IRQs 5 7 9 10 11 14 15) *0, disabled.
Apr 28 08:33:38 greatshaitan kernel: [    0.532173] ACPI: PCI Interrupt Link [LSID] (IRQs 5 7 9 10 *11 14 15)
Apr 28 08:33:38 greatshaitan kernel: [    0.532349] ACPI: PCI Interrupt Link [LFID] (IRQs 5 7 9 *10 11 14 15)
Apr 28 08:33:38 greatshaitan kernel: [    0.532561] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0
Apr 28 08:33:38 greatshaitan kernel: [    0.532765] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.
Apr 28 08:33:38 greatshaitan kernel: [    0.532967] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0
Apr 28 08:33:38 greatshaitan kernel: [    0.533169] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0, disabled.
Apr 28 08:33:38 greatshaitan kernel: [    0.533373] ACPI: PCI Interrupt Link [APC5] (IRQs 16) *0
Apr 28 08:33:38 greatshaitan kernel: [    0.533574] ACPI: PCI Interrupt Link [APC6] (IRQs 16) *0, disabled.
Apr 28 08:33:38 greatshaitan kernel: [    0.533777] ACPI: PCI Interrupt Link [APC7] (IRQs 16) *0, disabled.
Apr 28 08:33:38 greatshaitan kernel: [    0.533979] ACPI: PCI Interrupt Link [APC8] (IRQs 16) *0, disabled.
Apr 28 08:33:38 greatshaitan kernel: [    0.534182] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22 23) *0
Apr 28 08:33:38 greatshaitan kernel: [    0.534386] ACPI: PCI Interrupt Link [APCG] (IRQs 20 21 22 23) *0, disabled.
Apr 28 08:33:38 greatshaitan kernel: [    0.534591] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0
Apr 28 08:33:38 greatshaitan kernel: [    0.534794] ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22 23) *0, disabled.
Apr 28 08:33:38 greatshaitan kernel: [    0.534999] ACPI: PCI Interrupt Link [APMU] (IRQs 20 21 22 23) *0, disabled.
Apr 28 08:33:38 greatshaitan kernel: [    0.535203] ACPI: PCI Interrupt Link [AAZA] (IRQs 20 21 22 23) *0, disabled.
Apr 28 08:33:38 greatshaitan kernel: [    0.535407] ACPI: PCI Interrupt Link [APCK] (IRQs 20 21 22 23) *0, disabled.
Apr 28 08:33:38 greatshaitan kernel: [    0.535612] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0
Apr 28 08:33:38 greatshaitan kernel: [    0.535816] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22 23) *0
Apr 28 08:33:38 greatshaitan kernel: [    0.536023] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22 23) *0, disabled.
Apr 28 08:33:38 greatshaitan kernel: [    0.536228] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.
Apr 28 08:33:38 greatshaitan kernel: [    0.536432] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0
Apr 28 08:33:38 greatshaitan kernel: [    0.536636] ACPI: PCI Interrupt Link [APSJ] (IRQs 20 21 22 23) *0
Apr 28 08:33:38 greatshaitan kernel: [    0.536776] ACPI: WMI: Mapper loaded
Apr 28 08:33:38 greatshaitan kernel: [    0.536810] SCSI subsystem initialized
Apr 28 08:33:38 greatshaitan kernel: [    0.536810] usbcore: registered new interface driver usbfs
Apr 28 08:33:38 greatshaitan kernel: [    0.536810] usbcore: registered new interface driver hub
Apr 28 08:33:38 greatshaitan kernel: [    0.536810] usbcore: registered new device driver usb
Apr 28 08:33:38 greatshaitan kernel: [    0.536810] PCI: Using ACPI for IRQ routing
Apr 28 08:33:38 greatshaitan kernel: [    0.544009] Bluetooth: Core ver 2.13
Apr 28 08:33:38 greatshaitan kernel: [    0.544022] NET: Registered protocol family 31
Apr 28 08:33:38 greatshaitan kernel: [    0.544022] Bluetooth: HCI device and connection manager initialized
Apr 28 08:33:38 greatshaitan kernel: [    0.544022] Bluetooth: HCI socket layer initialized
Apr 28 08:33:38 greatshaitan kernel: [    0.544022] NET: Registered protocol family 8
Apr 28 08:33:38 greatshaitan kernel: [    0.544022] NET: Registered protocol family 20
Apr 28 08:33:38 greatshaitan kernel: [    0.544031] NetLabel: Initializing
Apr 28 08:33:38 greatshaitan kernel: [    0.544033] NetLabel:  domain hash size = 128
Apr 28 08:33:38 greatshaitan kernel: [    0.544035] NetLabel:  protocols = UNLABELED CIPSOv4
Apr 28 08:33:38 greatshaitan kernel: [    0.544046] NetLabel:  unlabeled traffic allowed by default
Apr 28 08:33:38 greatshaitan kernel: [    0.544060] hpet0: at MMIO 0xfeff0000, IRQs 2, 8, 31
Apr 28 08:33:38 greatshaitan kernel: [    0.544064] hpet0: 3 comparators, 32-bit 25.000000 MHz counter
Apr 28 08:33:38 greatshaitan kernel: [    0.548050] AppArmor: AppArmor Filesystem Enabled
Apr 28 08:33:38 greatshaitan kernel: [    0.556007] pnp: PnP ACPI init
Apr 28 08:33:38 greatshaitan kernel: [    0.556014] ACPI: bus type pnp registered
Apr 28 08:33:38 greatshaitan kernel: [    0.560785] pnp: PnP ACPI: found 15 devices
Apr 28 08:33:38 greatshaitan kernel: [    0.560787] ACPI: ACPI bus type pnp unregistered
Apr 28 08:33:38 greatshaitan kernel: [    0.560790] PnPBIOS: Disabled by ACPI PNP
Apr 28 08:33:38 greatshaitan kernel: [    0.560798] system 00:01: ioport range 0x1000-0x107f has been reserved
Apr 28 08:33:38 greatshaitan kernel: [    0.560801] system 00:01: ioport range 0x1080-0x10ff has been reserved
Apr 28 08:33:38 greatshaitan kernel: [    0.560803] system 00:01: ioport range 0x1400-0x147f has been reserved
Apr 28 08:33:38 greatshaitan kernel: [    0.560806] system 00:01: ioport range 0x1480-0x14ff has been reserved
Apr 28 08:33:38 greatshaitan kernel: [    0.560808] system 00:01: ioport range 0x1800-0x187f has been reserved
Apr 28 08:33:38 greatshaitan kernel: [    0.560810] system 00:01: ioport range 0x1880-0x18ff has been reserved
Apr 28 08:33:38 greatshaitan kernel: [    0.560816] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
Apr 28 08:33:38 greatshaitan kernel: [    0.560818] system 00:02: ioport range 0x800-0x87f has been reserved
Apr 28 08:33:38 greatshaitan kernel: [    0.560820] system 00:02: ioport range 0x290-0x297 has been reserved
Apr 28 08:33:38 greatshaitan kernel: [    0.560822] system 00:02: ioport range 0x880-0x88f has been reserved
Apr 28 08:33:38 greatshaitan kernel: [    0.560832] system 00:0d: iomem range 0xf0000000-0xf1ffffff has been reserved
Apr 28 08:33:38 greatshaitan kernel: [    0.560837] system 00:0e: iomem range 0xf0000-0xf3fff could not be reserved
Apr 28 08:33:38 greatshaitan kernel: [    0.560840] system 00:0e: iomem range 0xf4000-0xf7fff could not be reserved
Apr 28 08:33:38 greatshaitan kernel: [    0.560842] system 00:0e: iomem range 0xf8000-0xfbfff could not be reserved
Apr 28 08:33:38 greatshaitan kernel: [    0.560844] system 00:0e: iomem range 0xfc000-0xfffff could not be reserved
Apr 28 08:33:38 greatshaitan kernel: [    0.560847] system 00:0e: iomem range 0xfeff0000-0xfeff00ff has been reserved
Apr 28 08:33:38 greatshaitan kernel: [    0.560849] system 00:0e: iomem range 0xdfef0000-0xdfefffff could not be reserved
Apr 28 08:33:38 greatshaitan kernel: [    0.560852] system 00:0e: iomem range 0xffff0000-0xffffffff has been reserved
Apr 28 08:33:38 greatshaitan kernel: [    0.560854] system 00:0e: iomem range 0x0-0x9ffff could not be reserved
Apr 28 08:33:38 greatshaitan kernel: [    0.560856] system 00:0e: iomem range 0x100000-0xdfeeffff could not be reserved
Apr 28 08:33:38 greatshaitan kernel: [    0.560859] system 00:0e: iomem range 0xfec00000-0xfec00fff has been reserved
Apr 28 08:33:38 greatshaitan kernel: [    0.560861] system 00:0e: iomem range 0xfee00000-0xfee00fff has been reserved
Apr 28 08:33:38 greatshaitan kernel: [    0.560864] system 00:0e: iomem range 0xfeff0000-0xfeff03ff could not be reserved
Apr 28 08:33:38 greatshaitan kernel: [    0.595567] pci 0000:00:03.0: PCI bridge, secondary bus 0000:01
Apr 28 08:33:38 greatshaitan kernel: [    0.595570] pci 0000:00:03.0:   IO window: 0xc000-0xcfff
Apr 28 08:33:38 greatshaitan kernel: [    0.595574] pci 0000:00:03.0:   MEM window: 0xfa000000-0xfcffffff
Apr 28 08:33:38 greatshaitan kernel: [    0.595577] pci 0000:00:03.0:   PREFETCH window: 0x000000e0000000-0x000000efffffff
Apr 28 08:33:38 greatshaitan kernel: [    0.595582] pci 0000:00:05.0: PCI bridge, secondary bus 0000:02
Apr 28 08:33:38 greatshaitan kernel: [    0.595584] pci 0000:00:05.0:   IO window: 0xa000-0xafff
Apr 28 08:33:38 greatshaitan kernel: [    0.595588] pci 0000:00:05.0:   MEM window: 0xfde00000-0xfdefffff
Apr 28 08:33:38 greatshaitan kernel: [    0.595591] pci 0000:00:05.0:   PREFETCH window: 0x000000fdd00000-0x000000fddfffff
Apr 28 08:33:38 greatshaitan kernel: [    0.595595] pci 0000:00:06.0: PCI bridge, secondary bus 0000:03
Apr 28 08:33:38 greatshaitan kernel: [    0.595598] pci 0000:00:06.0:   IO window: 0xe000-0xefff
Apr 28 08:33:38 greatshaitan kernel: [    0.595601] pci 0000:00:06.0:   MEM window: 0xfdc00000-0xfdcfffff
Apr 28 08:33:38 greatshaitan kernel: [    0.595604] pci 0000:00:06.0:   PREFETCH window: 0x000000fdb00000-0x000000fdbfffff
Apr 28 08:33:38 greatshaitan kernel: [    0.595609] pci 0000:00:07.0: PCI bridge, secondary bus 0000:04
Apr 28 08:33:38 greatshaitan kernel: [    0.595611] pci 0000:00:07.0:   IO window: 0xd000-0xdfff
Apr 28 08:33:38 greatshaitan kernel: [    0.595615] pci 0000:00:07.0:   MEM window: 0xfd800000-0xfd8fffff
Apr 28 08:33:38 greatshaitan kernel: [    0.595618] pci 0000:00:07.0:   PREFETCH window: 0x000000fdf00000-0x000000fdffffff
Apr 28 08:33:38 greatshaitan kernel: [    0.595622] pci 0000:00:10.0: PCI bridge, secondary bus 0000:05
Apr 28 08:33:38 greatshaitan kernel: [    0.595625] pci 0000:00:10.0:   IO window: 0xb000-0xbfff
Apr 28 08:33:38 greatshaitan kernel: [    0.595629] pci 0000:00:10.0:   MEM window: 0xfda00000-0xfdafffff
Apr 28 08:33:38 greatshaitan kernel: [    0.595632] pci 0000:00:10.0:   PREFETCH window: 0x000000fd900000-0x000000fd9fffff
Apr 28 08:33:38 greatshaitan kernel: [    0.595668] bus: 00 index 0 io port: [0x00-0xffff]
Apr 28 08:33:38 greatshaitan kernel: [    0.595670] bus: 00 index 1 mmio: [0x000000-0xffffffff]
Apr 28 08:33:38 greatshaitan kernel: [    0.595672] bus: 01 index 0 io port: [0xc000-0xcfff]
Apr 28 08:33:38 greatshaitan kernel: [    0.595674] bus: 01 index 1 mmio: [0xfa000000-0xfcffffff]
Apr 28 08:33:38 greatshaitan kernel: [    0.595676] bus: 01 index 2 mmio: [0xe0000000-0xefffffff]
Apr 28 08:33:38 greatshaitan kernel: [    0.595678] bus: 01 index 3 mmio: [0x0-0x0]
Apr 28 08:33:38 greatshaitan kernel: [    0.595680] bus: 02 index 0 io port: [0xa000-0xafff]
Apr 28 08:33:38 greatshaitan kernel: [    0.595681] bus: 02 index 1 mmio: [0xfde00000-0xfdefffff]
Apr 28 08:33:38 greatshaitan kernel: [    0.595683] bus: 02 index 2 mmio: [0xfdd00000-0xfddfffff]
Apr 28 08:33:38 greatshaitan kernel: [    0.595685] bus: 02 index 3 mmio: [0x0-0x0]
Apr 28 08:33:38 greatshaitan kernel: [    0.595687] bus: 03 index 0 io port: [0xe000-0xefff]
Apr 28 08:33:38 greatshaitan kernel: [    0.595689] bus: 03 index 1 mmio: [0xfdc00000-0xfdcfffff]
Apr 28 08:33:38 greatshaitan kernel: [    0.595690] bus: 03 index 2 mmio: [0xfdb00000-0xfdbfffff]
Apr 28 08:33:38 greatshaitan kernel: [    0.595692] bus: 03 index 3 mmio: [0x0-0x0]
Apr 28 08:33:38 greatshaitan kernel: [    0.595694] bus: 04 index 0 io port: [0xd000-0xdfff]
Apr 28 08:33:38 greatshaitan kernel: [    0.595695] bus: 04 index 1 mmio: [0xfd800000-0xfd8fffff]
Apr 28 08:33:38 greatshaitan kernel: [    0.595697] bus: 04 index 2 mmio: [0xfdf00000-0xfdffffff]
Apr 28 08:33:38 greatshaitan kernel: [    0.595699] bus: 04 index 3 mmio: [0x0-0x0]
Apr 28 08:33:38 greatshaitan kernel: [    0.595701] bus: 05 index 0 io port: [0xb000-0xbfff]
Apr 28 08:33:38 greatshaitan kernel: [    0.595703] bus: 05 index 1 mmio: [0xfda00000-0xfdafffff]
Apr 28 08:33:38 greatshaitan kernel: [    0.595704] bus: 05 index 2 mmio: [0xfd900000-0xfd9fffff]
Apr 28 08:33:38 greatshaitan kernel: [    0.595706] bus: 05 index 3 io port: [0x00-0xffff]
Apr 28 08:33:38 greatshaitan kernel: [    0.595708] bus: 05 index 4 mmio: [0x000000-0xffffffff]
Apr 28 08:33:38 greatshaitan kernel: [    0.595715] NET: Registered protocol family 2
Apr 28 08:33:38 greatshaitan kernel: [    0.608048] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Apr 28 08:33:38 greatshaitan kernel: [    0.608258] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Apr 28 08:33:38 greatshaitan kernel: [    0.608503] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Apr 28 08:33:38 greatshaitan kernel: [    0.608640] TCP: Hash tables configured (established 131072 bind 65536)
Apr 28 08:33:38 greatshaitan kernel: [    0.608642] TCP reno registered
Apr 28 08:33:38 greatshaitan kernel: [    0.616068] NET: Registered protocol family 1
Apr 28 08:33:38 greatshaitan kernel: [    0.616164] checking if image is initramfs... it is
Apr 28 08:33:38 greatshaitan kernel: [    1.175265] Freeing initrd memory: 7367k freed
Apr 28 08:33:38 greatshaitan kernel: [    1.175472] cpufreq: No nForce2 chipset.
Apr 28 08:33:38 greatshaitan kernel: [    1.175602] audit: initializing netlink socket (disabled)
Apr 28 08:33:38 greatshaitan kernel: [    1.175624] type=2000 audit(1240922003.172:1): initialized
Apr 28 08:33:38 greatshaitan kernel: [    1.182227] highmem bounce pool size: 64 pages
Apr 28 08:33:38 greatshaitan kernel: [    1.182232] HugeTLB registered 4 MB page size, pre-allocated 0 pages
Apr 28 08:33:38 greatshaitan kernel: [    1.183464] VFS: Disk quotas dquot_6.5.1
Apr 28 08:33:38 greatshaitan kernel: [    1.183517] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Apr 28 08:33:38 greatshaitan kernel: [    1.184066] fuse init (API version 7.10)
Apr 28 08:33:38 greatshaitan kernel: [    1.184141] msgmni has been set to 1659
Apr 28 08:33:38 greatshaitan kernel: [    1.184315] alg: No test for stdrng (krng)
Apr 28 08:33:38 greatshaitan kernel: [    1.184328] io scheduler noop registered
Apr 28 08:33:38 greatshaitan kernel: [    1.184331] io scheduler anticipatory registered
Apr 28 08:33:38 greatshaitan kernel: [    1.184332] io scheduler deadline registered
Apr 28 08:33:38 greatshaitan kernel: [    1.184344] io scheduler cfq registered (default)
Apr 28 08:33:38 greatshaitan kernel: [    1.184507] pci 0000:00:03.0: Disabling HT MSI mapping<6>pci 0000:00:05.0: Disabling HT MSI mapping<6>pci 0000:00:06.0: Disabling HT MSI mapping<6>pci 0000:00:07.0: Disabling HT MSI mapping<6>pci 0000:00:09.0: Disabling HT MSI mapping<6>pci 0000:00:0e.0: Disabling HT MSI mapping<6>pci 0000:00:0f.0: Disabling HT MSI mapping<6>pci 0000:00:10.0: Disabling HT MSI mapping<7>pci 0000:01:00.0: Boot video device
Apr 28 08:33:38 greatshaitan kernel: [    1.206632] pcieport-driver 0000:00:03.0: found MSI capability
Apr 28 08:33:38 greatshaitan kernel: [    1.206761] pcieport-driver 0000:00:05.0: found MSI capability
Apr 28 08:33:38 greatshaitan kernel: [    1.206884] pcieport-driver 0000:00:06.0: found MSI capability
Apr 28 08:33:38 greatshaitan kernel: [    1.207010] pcieport-driver 0000:00:07.0: found MSI capability
Apr 28 08:33:38 greatshaitan kernel: [    1.207107] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Apr 28 08:33:38 greatshaitan kernel: [    1.207116] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Apr 28 08:33:38 greatshaitan kernel: [    1.207265] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
Apr 28 08:33:38 greatshaitan kernel: [    1.207267] ACPI: Power Button (FF) [PWRF]
Apr 28 08:33:38 greatshaitan kernel: [    1.207310] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
Apr 28 08:33:38 greatshaitan kernel: [    1.207313] ACPI: Power Button (CM) [PWRB]
Apr 28 08:33:38 greatshaitan kernel: [    1.207373] fan PNP0C0B:00: registered as cooling_device0
Apr 28 08:33:38 greatshaitan kernel: [    1.207378] ACPI: Fan [FAN] (on)
Apr 28 08:33:38 greatshaitan kernel: [    1.207696] processor ACPI_CPU:00: registered as cooling_device1
Apr 28 08:33:38 greatshaitan kernel: [    1.207730] processor ACPI_CPU:01: registered as cooling_device2
Apr 28 08:33:38 greatshaitan kernel: [    1.211811] thermal LNXTHERM:01: registered as thermal_zone0
Apr 28 08:33:38 greatshaitan kernel: [    1.212115] ACPI: Thermal Zone [THRM] (40 C)
Apr 28 08:33:38 greatshaitan kernel: [    1.212169] isapnp: Scanning for PnP cards...
Apr 28 08:33:38 greatshaitan kernel: [    1.565083] isapnp: No Plug & Play device found
Apr 28 08:33:38 greatshaitan kernel: [    1.572686] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
Apr 28 08:33:38 greatshaitan kernel: [    1.572782] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Apr 28 08:33:38 greatshaitan kernel: [    1.573173] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Apr 28 08:33:38 greatshaitan kernel: [    1.573903] brd: module loaded
Apr 28 08:33:38 greatshaitan kernel: [    1.574191] loop: module loaded
Apr 28 08:33:38 greatshaitan kernel: [    1.574247] Fixed MDIO Bus: probed
Apr 28 08:33:38 greatshaitan kernel: [    1.574251] PPP generic driver version 2.4.2
Apr 28 08:33:38 greatshaitan kernel: [    1.574299] input: Macintosh mouse button emulation as /devices/virtual/input/input2
Apr 28 08:33:38 greatshaitan kernel: [    1.574324] Driver 'sd' needs updating - please use bus_type methods
Apr 28 08:33:38 greatshaitan kernel: [    1.574334] Driver 'sr' needs updating - please use bus_type methods
Apr 28 08:33:38 greatshaitan kernel: [    1.574836] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 23
Apr 28 08:33:38 greatshaitan kernel: [    1.574843] sata_nv 0000:00:0e.0: PCI INT A -> Link[APSI] -> GSI 23 (level, low) -> IRQ 23
Apr 28 08:33:38 greatshaitan kernel: [    1.574845] sata_nv 0000:00:0e.0: Using SWNCQ mode
Apr 28 08:33:38 greatshaitan kernel: [    1.574994] scsi0 : sata_nv
Apr 28 08:33:38 greatshaitan kernel: [    1.575070] scsi1 : sata_nv
Apr 28 08:33:38 greatshaitan kernel: [    1.575216] ata1: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xf800 irq 23
Apr 28 08:33:38 greatshaitan kernel: [    1.575218] ata2: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xf808 irq 23
Apr 28 08:33:38 greatshaitan kernel: [    2.306488] ata1: SATA link down (SStatus 0 SControl 300)
Apr 28 08:33:38 greatshaitan kernel: [    3.038471] ata2: SATA link down (SStatus 0 SControl 300)
Apr 28 08:33:38 greatshaitan kernel: [    3.038785] ACPI: PCI Interrupt Link [APSJ] enabled at IRQ 22
Apr 28 08:33:38 greatshaitan kernel: [    3.038789] sata_nv 0000:00:0f.0: PCI INT A -> Link[APSJ] -> GSI 22 (level, low) -> IRQ 22
Apr 28 08:33:38 greatshaitan kernel: [    3.038792] sata_nv 0000:00:0f.0: Using SWNCQ mode
Apr 28 08:33:38 greatshaitan kernel: [    3.038934] scsi2 : sata_nv
Apr 28 08:33:38 greatshaitan kernel: [    3.038992] scsi3 : sata_nv
Apr 28 08:33:38 greatshaitan kernel: [    3.039136] ata3: SATA max UDMA/133 cmd 0x9e0 ctl 0xbe0 bmdma 0xf300 irq 22
Apr 28 08:33:38 greatshaitan kernel: [    3.039138] ata4: SATA max UDMA/133 cmd 0x960 ctl 0xb60 bmdma 0xf308 irq 22
Apr 28 08:33:38 greatshaitan kernel: [    3.916041] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Apr 28 08:33:38 greatshaitan kernel: [    3.924403] ata3.00: ATA-8: WL1000GSA3272^I, 05.00K05, max UDMA/133
Apr 28 08:33:38 greatshaitan kernel: [    3.924406] ata3.00: 1953525168 sectors, multi 1: LBA48 NCQ (depth 31/32)
Apr 28 08:33:38 greatshaitan kernel: [    3.940434] ata3.00: configured for UDMA/133
Apr 28 08:33:38 greatshaitan kernel: [    4.820041] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Apr 28 08:33:38 greatshaitan kernel: [    4.845265] ata4.00: ATA-7: WDC WD1600AAJS-00PSA0, 05.06H05, max UDMA/133
Apr 28 08:33:38 greatshaitan kernel: [    4.845268] ata4.00: 312581808 sectors, multi 1: LBA48 NCQ (depth 31/32)
Apr 28 08:33:38 greatshaitan kernel: [    4.860384] ata4.00: configured for UDMA/133
Apr 28 08:33:38 greatshaitan kernel: [    4.860484] scsi 2:0:0:0: Direct-Access     ATA      WL1000GSA3272    05.0 PQ: 0 ANSI: 5
Apr 28 08:33:38 greatshaitan kernel: [    4.860571] sd 2:0:0:0: [sda] 1953525168 512-byte hardware sectors: (1.00 TB/931 GiB)
Apr 28 08:33:38 greatshaitan kernel: [    4.860585] sd 2:0:0:0: [sda] Write Protect is off
Apr 28 08:33:38 greatshaitan kernel: [    4.860610] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 28 08:33:38 greatshaitan kernel: [    4.860663] sd 2:0:0:0: [sda] 1953525168 512-byte hardware sectors: (1.00 TB/931 GiB)
Apr 28 08:33:38 greatshaitan kernel: [    4.860676] sd 2:0:0:0: [sda] Write Protect is off
Apr 28 08:33:38 greatshaitan kernel: [    4.860700] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 28 08:33:38 greatshaitan kernel: [    4.860703]  sda: sda1 sda2 < sda5 >
Apr 28 08:33:38 greatshaitan kernel: [    4.887664] sd 2:0:0:0: [sda] Attached SCSI disk
Apr 28 08:33:38 greatshaitan kernel: [    4.887700] sd 2:0:0:0: Attached scsi generic sg0 type 0
Apr 28 08:33:38 greatshaitan kernel: [    4.887775] scsi 3:0:0:0: Direct-Access     ATA      WDC WD1600AAJS-0 05.0 PQ: 0 ANSI: 5
Apr 28 08:33:38 greatshaitan kernel: [    4.887852] sd 3:0:0:0: [sdb] 312581808 512-byte hardware sectors: (160 GB/149 GiB)
Apr 28 08:33:38 greatshaitan kernel: [    4.887866] sd 3:0:0:0: [sdb] Write Protect is off
Apr 28 08:33:38 greatshaitan kernel: [    4.887891] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 28 08:33:38 greatshaitan kernel: [    4.887936] sd 3:0:0:0: [sdb] 312581808 512-byte hardware sectors: (160 GB/149 GiB)
Apr 28 08:33:38 greatshaitan kernel: [    4.887949] sd 3:0:0:0: [sdb] Write Protect is off
Apr 28 08:33:38 greatshaitan kernel: [    4.887974] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 28 08:33:38 greatshaitan kernel: [    4.887977]  sdb: sdb1 sdb2
Apr 28 08:33:38 greatshaitan kernel: [    4.894232] sd 3:0:0:0: [sdb] Attached SCSI disk
Apr 28 08:33:38 greatshaitan kernel: [    4.894265] sd 3:0:0:0: Attached scsi generic sg1 type 0
Apr 28 08:33:38 greatshaitan kernel: [    4.894453] scsi4 : pata_amd
Apr 28 08:33:38 greatshaitan kernel: [    4.894511] scsi5 : pata_amd
Apr 28 08:33:38 greatshaitan kernel: [    4.895063] ata5: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xfd00 irq 14
Apr 28 08:33:38 greatshaitan kernel: [    4.895065] ata6: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xfd08 irq 15
Apr 28 08:33:38 greatshaitan kernel: [    5.228291] ata6.01: ATAPI: TSSTcorpCD/DVDW SH-S182D, SB03, max UDMA/33
Apr 28 08:33:38 greatshaitan kernel: [    5.244250] ata6.01: configured for UDMA/33
Apr 28 08:33:38 greatshaitan kernel: [    5.245366] scsi 5:0:1:0: CD-ROM            TSSTcorp CD/DVDW SH-S182D SB03 PQ: 0 ANSI: 5
Apr 28 08:33:38 greatshaitan kernel: [    5.251826] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
Apr 28 08:33:38 greatshaitan kernel: [    5.251829] Uniform CD-ROM driver Revision: 3.20
Apr 28 08:33:38 greatshaitan kernel: [    5.251941] sr 5:0:1:0: Attached scsi generic sg2 type 5
Apr 28 08:33:38 greatshaitan kernel: [    5.252462] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Apr 28 08:33:38 greatshaitan kernel: [    5.252778] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 21
Apr 28 08:33:38 greatshaitan kernel: [    5.252783] ehci_hcd 0000:00:0b.1: PCI INT B -> Link[APCL] -> GSI 21 (level, low) -> IRQ 21
Apr 28 08:33:38 greatshaitan kernel: [    5.252795] ehci_hcd 0000:00:0b.1: EHCI Host Controller
Apr 28 08:33:38 greatshaitan kernel: [    5.252848] ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 1
Apr 28 08:33:38 greatshaitan kernel: [    5.252871] ehci_hcd 0000:00:0b.1: debug port 1
Apr 28 08:33:38 greatshaitan kernel: [    5.252889] ehci_hcd 0000:00:0b.1: irq 21, io mem 0xfe02e000
Apr 28 08:33:38 greatshaitan kernel: [    5.264011] ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00
Apr 28 08:33:38 greatshaitan kernel: [    5.264067] usb usb1: configuration #1 chosen from 1 choice
Apr 28 08:33:38 greatshaitan kernel: [    5.264099] hub 1-0:1.0: USB hub found
Apr 28 08:33:38 greatshaitan kernel: [    5.264105] hub 1-0:1.0: 8 ports detected
Apr 28 08:33:38 greatshaitan kernel: [    5.264198] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Apr 28 08:33:38 greatshaitan kernel: [    5.264511] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 20
Apr 28 08:33:38 greatshaitan kernel: [    5.264515] ohci_hcd 0000:00:0b.0: PCI INT A -> Link[APCF] -> GSI 20 (level, low) -> IRQ 20
Apr 28 08:33:38 greatshaitan kernel: [    5.264527] ohci_hcd 0000:00:0b.0: OHCI Host Controller
Apr 28 08:33:38 greatshaitan kernel: [    5.264565] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 2
Apr 28 08:33:38 greatshaitan kernel: [    5.264587] ohci_hcd 0000:00:0b.0: irq 20, io mem 0xfe02f000
Apr 28 08:33:38 greatshaitan kernel: [    5.322051] usb usb2: configuration #1 chosen from 1 choice
Apr 28 08:33:38 greatshaitan kernel: [    5.322075] hub 2-0:1.0: USB hub found
Apr 28 08:33:38 greatshaitan kernel: [    5.322082] hub 2-0:1.0: 8 ports detected
Apr 28 08:33:38 greatshaitan kernel: [    5.322167] uhci_hcd: USB Universal Host Controller Interface driver
Apr 28 08:33:38 greatshaitan kernel: [    5.322209] usbcore: registered new interface driver libusual
Apr 28 08:33:38 greatshaitan kernel: [    5.322234] usbcore: registered new interface driver usbserial
Apr 28 08:33:38 greatshaitan kernel: [    5.322244] USB Serial support registered for generic
Apr 28 08:33:38 greatshaitan kernel: [    5.322255] usbcore: registered new interface driver usbserial_generic
Apr 28 08:33:38 greatshaitan kernel: [    5.322257] usbserial: USB Serial Driver core
Apr 28 08:33:38 greatshaitan kernel: [    5.322307] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Apr 28 08:33:38 greatshaitan kernel: [    5.322636] serio: i8042 KBD port at 0x60,0x64 irq 1
Apr 28 08:33:38 greatshaitan kernel: [    5.322642] serio: i8042 AUX port at 0x60,0x64 irq 12
Apr 28 08:33:38 greatshaitan kernel: [    5.323762] mice: PS/2 mouse device common for all mice
Apr 28 08:33:38 greatshaitan kernel: [    5.323884] rtc_cmos 00:05: RTC can wake from S4
Apr 28 08:33:38 greatshaitan kernel: [    5.323911] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
Apr 28 08:33:38 greatshaitan kernel: [    5.323940] rtc0: alarms up to one year, y3k, 242 bytes nvram, hpet irqs
Apr 28 08:33:38 greatshaitan kernel: [    5.323993] device-mapper: uevent: version 1.0.3
Apr 28 08:33:38 greatshaitan kernel: [    5.324084] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
Apr 28 08:33:38 greatshaitan kernel: [    5.324156] device-mapper: multipath: version 1.0.5 loaded
Apr 28 08:33:38 greatshaitan kernel: [    5.324158] device-mapper: multipath round-robin: version 1.0.0 loaded
Apr 28 08:33:38 greatshaitan kernel: [    5.324229] EISA: Probing bus 0 at eisa.0
Apr 28 08:33:38 greatshaitan kernel: [    5.324234] Cannot allocate resource for EISA slot 1
Apr 28 08:33:38 greatshaitan kernel: [    5.324255] EISA: Detected 0 cards.
Apr 28 08:33:38 greatshaitan kernel: [    5.324303] cpuidle: using governor ladder
Apr 28 08:33:38 greatshaitan kernel: [    5.324304] cpuidle: using governor menu
Apr 28 08:33:38 greatshaitan kernel: [    5.324761] TCP cubic registered
Apr 28 08:33:38 greatshaitan kernel: [    5.324845] NET: Registered protocol family 10
Apr 28 08:33:38 greatshaitan kernel: [    5.325236] lo: Disabled Privacy Extensions
Apr 28 08:33:38 greatshaitan kernel: [    5.325539] NET: Registered protocol family 17
Apr 28 08:33:38 greatshaitan kernel: [    5.325555] Bluetooth: L2CAP ver 2.11
Apr 28 08:33:38 greatshaitan kernel: [    5.325557] Bluetooth: L2CAP socket layer initialized
Apr 28 08:33:38 greatshaitan kernel: [    5.325560] Bluetooth: SCO (Voice Link) ver 0.6
Apr 28 08:33:38 greatshaitan kernel: [    5.325561] Bluetooth: SCO socket layer initialized
Apr 28 08:33:38 greatshaitan kernel: [    5.325590] Bluetooth: RFCOMM socket layer initialized
Apr 28 08:33:38 greatshaitan kernel: [    5.325596] Bluetooth: RFCOMM TTY layer initialized
Apr 28 08:33:38 greatshaitan kernel: [    5.325597] Bluetooth: RFCOMM ver 1.10
Apr 28 08:33:38 greatshaitan kernel: [    5.325638] Using IPI No-Shortcut mode
Apr 28 08:33:38 greatshaitan kernel: [    5.325697] registered taskstats version 1
Apr 28 08:33:38 greatshaitan kernel: [    5.325828]   Magic number: 5:393:583
Apr 28 08:33:38 greatshaitan kernel: [    5.325845] pci_bus 0000:04: hash matches
Apr 28 08:33:38 greatshaitan kernel: [    5.325850] pci_link PNP0C0F:26: hash matches
Apr 28 08:33:38 greatshaitan kernel: [    5.325891] rtc_cmos 00:05: setting system clock to 2009-04-28 12:33:28 UTC (1240922008)
Apr 28 08:33:38 greatshaitan kernel: [    5.325894] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Apr 28 08:33:38 greatshaitan kernel: [    5.325896] EDD information not available.
Apr 28 08:33:38 greatshaitan kernel: [    5.326121] Freeing unused kernel memory: 532k freed
Apr 28 08:33:38 greatshaitan kernel: [    5.326236] Write protecting the kernel text: 4128k
Apr 28 08:33:38 greatshaitan kernel: [    5.326278] Write protecting the kernel read-only data: 1532k
Apr 28 08:33:38 greatshaitan kernel: [    5.341743] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
Apr 28 08:33:38 greatshaitan kernel: [    5.509173] Floppy drive(s): fd0 is 1.44M
Apr 28 08:33:38 greatshaitan kernel: [    5.527859] FDC 0 is a post-1991 82077
Apr 28 08:33:38 greatshaitan kernel: [    5.599861] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
Apr 28 08:33:38 greatshaitan kernel: [    5.600213] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 23
Apr 28 08:33:38 greatshaitan kernel: [    5.600217] forcedeth 0000:00:14.0: PCI INT A -> Link[APCH] -> GSI 23 (level, low) -> IRQ 23
Apr 28 08:33:38 greatshaitan kernel: [    5.672050] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
Apr 28 08:33:38 greatshaitan kernel: [    5.672058] ohci1394 0000:05:08.0: PCI INT A -> Link[APC3] -> GSI 18 (level, low) -> IRQ 18
Apr 28 08:33:38 greatshaitan kernel: [    5.724779] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[18]  MMIO=[fdaff000-fdaff7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
Apr 28 08:33:38 greatshaitan kernel: [    6.124862] forcedeth 0000:00:14.0: ifname eth0, PHY OUI 0x5043 @ 1, addr 00:1a:92:82:40:a8
Apr 28 08:33:38 greatshaitan kernel: [    6.124866] forcedeth 0000:00:14.0: highdma pwrctl timirq gbit lnktim desc-v3
Apr 28 08:33:38 greatshaitan kernel: [    6.185620] PM: Starting manual resume from disk
Apr 28 08:33:38 greatshaitan kernel: [    6.196736] EXT3-fs: INFO: recovery required on readonly filesystem.
Apr 28 08:33:38 greatshaitan kernel: [    6.196738] EXT3-fs: write access will be enabled during recovery.
Apr 28 08:33:38 greatshaitan kernel: [    7.623944] kjournald starting.  Commit interval 5 seconds
Apr 28 08:33:38 greatshaitan kernel: [    7.623956] EXT3-fs: sda1: orphan cleanup on readonly fs
Apr 28 08:33:38 greatshaitan kernel: [    7.644007] EXT3-fs: sda1: 5 orphan inodes deleted
Apr 28 08:33:38 greatshaitan kernel: [    7.644008] EXT3-fs: recovery complete.
Apr 28 08:33:38 greatshaitan kernel: [    7.662457] EXT3-fs: mounted filesystem with ordered data mode.
Apr 28 08:33:38 greatshaitan kernel: [   12.299755] udev: starting version 141
Apr 28 08:33:38 greatshaitan kernel: [   12.412990] Linux agpgart interface v0.103
Apr 28 08:33:38 greatshaitan kernel: [   12.419942] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x1c00
Apr 28 08:33:38 greatshaitan kernel: [   12.419980] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x1c80
Apr 28 08:33:38 greatshaitan kernel: [   12.837006] nvidia: module license 'NVIDIA' taints kernel.
Apr 28 08:33:38 greatshaitan kernel: [   12.917861] parport_pc 00:0a: reported by Plug and Play ACPI
Apr 28 08:33:38 greatshaitan kernel: [   12.917888] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
Apr 28 08:33:38 greatshaitan kernel: [   12.956537] input: PC Speaker as /devices/platform/pcspkr/input/input4
Apr 28 08:33:38 greatshaitan kernel: [   13.010246] ppdev: user-space parallel port driver
Apr 28 08:33:38 greatshaitan kernel: [   13.090164] ACPI: PCI Interrupt Link [APC5] enabled at IRQ 16
Apr 28 08:33:38 greatshaitan kernel: [   13.090171] nvidia 0000:01:00.0: PCI INT A -> Link[APC5] -> GSI 16 (level, low) -> IRQ 16
Apr 28 08:33:38 greatshaitan kernel: [   13.090995] NVRM: loading NVIDIA UNIX x86 Kernel Module  180.44  Mon Mar 23 14:59:10 PST 2009
Apr 28 08:33:38 greatshaitan kernel: [   13.181395] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
Apr 28 08:33:38 greatshaitan kernel: [   13.195512] ACPI: PCI Interrupt Link [APC1] enabled at IRQ 16
Apr 28 08:33:38 greatshaitan kernel: [   13.195517] C-Media PCI 0000:05:06.0: PCI INT A -> Link[APC1] -> GSI 16 (level, low) -> IRQ 16
Apr 28 08:33:38 greatshaitan kernel: [   13.356428] lp0: using parport0 (interrupt-driven).
Apr 28 08:33:38 greatshaitan kernel: [   13.420290] Adding 10586792k swap on /dev/sda5.  Priority:-1 extents:1 across:10586792k
Apr 28 08:33:38 greatshaitan kernel: [   14.294287] input: ImPS/2 Logitech Wheel Mouse as /devices/platform/i8042/serio1/input/input5
Apr 28 08:33:38 greatshaitan kernel: [   14.811352] type=1505 audit(1240922017.982:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2109
Apr 28 08:33:38 greatshaitan kernel: [   14.852386] type=1505 audit(1240922018.026:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2113
Apr 28 08:33:38 greatshaitan kernel: [   14.852455] type=1505 audit(1240922018.026:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2113
Apr 28 08:33:38 greatshaitan kernel: [   14.852490] type=1505 audit(1240922018.026:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2113
Apr 28 08:33:38 greatshaitan kernel: [   14.852523] type=1505 audit(1240922018.026:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2113
Apr 28 08:33:38 greatshaitan kernel: [   14.965725] type=1505 audit(1240922018.138:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2118
Apr 28 08:33:38 greatshaitan kernel: [   14.965850] type=1505 audit(1240922018.138:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2118
Apr 28 08:33:38 greatshaitan kernel: [   14.989999] type=1505 audit(1240922018.162:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2122
Apr 28 08:33:40 greatshaitan kernel: [   17.559538] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Apr 28 08:33:40 greatshaitan kernel: [   17.559541] Bluetooth: BNEP filters: protocol multicast
Apr 28 08:33:40 greatshaitan kernel: [   17.567370] Bridge firewalling registered
```

---

### Post by buchan on 2009-04-28
I'm just going to post my two cents here... 

I have been seeing the same "freezing" issues with my install but I was chalking it up to a hardware problem.  I to have re-installed multiple times to see the same problems re-appear.  My latest attempt was a physically different MB/proc (different MB same type of proc) and ram but still had the same results.  I have also seen random CRC errors using the ubuntu repo based version of SABnzb, I have also posted in their forum but it also seems to be a random problem there as well.  

I haven't been using my system as a desktop unit, I was setting it up to be a headless server so my freeze seems to simply happen after a period of inactivity.  If I've left the system on and (as you would do with a headless server) and come back several hours later to find it completely unresponsive. 

I have already upgraded several servers at work and now I'm starting to wonder if I've made a mistake in doing so.

I think I'm going to stick with 8.10, it seems to be a far more stable release.

---

### Post by psychomichael on 2009-04-28
After searching and finding similar errors at launchpad and the x.org site, this is a known issue and because of it's "random" nature nobody seems to know what to do. 

I hate coming across as a complainer but damn, man. Do you really want people who have never used a terminal and are thinking of switching to linux going through this crap? I've been distro-hopping, looking for one that will truly "just work"...but seriously.

I *really* like Ubuntu...and here's where I'm going to ask a serious question: Do you really need to phase out past releases like 7.04 & early 7.10 that lived up to the mantra, "It just works", in favor of releases like 8.04, 8.10 & now 9.04 that "just doesn't work" on many machines? It's like I'm stuck back in "Windows release hell" except at least I'm not paying $399 for each "upgrade". 

If I could go back to 7.04, I would...but it's not supported anymore. It's been rendered worthless by later releases that are nicer looking and have cool features but don't work on any of my machines. It's not like I have ancient machinery, either. 

I will say that Jaunty is probably the closest I've seen to a truly good release since early 7.10...if it weren't for the constant random freezing...and I wish I had the technological knowledge to help fix it because I'd be there with you guys compiling and looking through logs and writing code, but I'm barely past the novice level.

Anyway, I'm off to try Mandriva Gnome...carry on my brothers.
[/rant]

---

### Post by northwestuntu on 2009-04-28
i feel your pain man.

this random freezing is very frustrating.  i have never had a problem like this on any os? so i don't really no what to do?

---

### Post by mkvnmtr on 2009-04-28
I think this is what happened on one of my installs. I could never get 9.04 and went back. On my other machine no problems at all.

---

### Post by northwestuntu on 2009-04-28
same here.  i have one computer works great on jaunty and then my other crashes and freezes all the time.  very similar hardware on both which confuses me even more.

---

### Post by psychomichael on 2009-04-29
Yeah...well, I found a solution. I tried Fedora and Mandriva and settled on Mandriva One Gnome 2009. Everything works perfectly. I didn't even have to load any of the drivers for Firefox and Youtube viewing, etc. Compiz Fusion even works for me now!

Ubuntu will always hold a special place in my heart for introducing me to the awesome world of linux, but I think I've found a good distro that "just works" for me.

---

### Post by screig on 2009-06-15
running 9.04, Asus P5N7A-VM with integrated nvidia 9300 freezes every day. think its related to Nvidia

Jun 15 20:07:20 NightFlyer NetworkManager: <info>  Activation (wlan0) successful, device activated. 
Jun 15 20:07:20 NightFlyer NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete. 
Jun 15 20:07:20 NightFlyer ntpdate[4114]: adjust time server 91.189.94.4 offset 0.433523 sec
Jun 15 20:07:26 NightFlyer kernel: [   54.536036] wlan0: no IPv6 routers present
Jun 15 20:08:36 NightFlyer kernel: [  123.868071] NVRM: Xid (0003:00): 13, 0001 00000000 0000502d 00000104 00000000 00000100
Jun 15 20:08:36 NightFlyer kernel: [  123.884637] NVRM: Xid (0003:00): 13, 0003 00000000 00008397 00001408 00000001 00000040
Jun 15 20:08:37 NightFlyer kernel: [  124.945726] NVRM: Xid (0003:00): 13, 0003 00000000 00008397 000015e0 00000000 00000040
Jun 15 20:08:37 NightFlyer kernel: [  124.960615] NVRM: Xid (0003:00): 13, 0001 00000000 0000502d 00000104 00000000 00000100
Jun 15 20:08:37 NightFlyer kernel: [  125.106931] NVRM: Xid (0003:00): 13, 0001 00000000 0000502d 00000104 00000000 00000100
Jun 15 20:09:53 NightFlyer syslogd 1.5.0#5ubuntu3: restart.
Jun 15 20:09:53 NightFlyer kernel: Inspecting /boot/System.map-2.6.29-020629-generic
Jun 15 20:09:53 NightFlyer kernel: Cannot find map file.
Jun 15 20:09:53 NightFlyer kernel: Loaded 82768 symbols from 52 modules.
Jun 15 20:09:53 NightFlyer kernel: [    0.000000] Initializing cgroup subs

---

### Post by epicoder on 2009-06-15
I use jaunty and aside from the occasional program glitch, I have no problems. If you don't have it, try getting this kernel:
2.6.28-11-generic

---

### Post by desertranger on 2009-08-14
I have the problem too. I'm sure it's a software problem because I have a dual XP and Ubuntu machine, and XP works just fine, and every now and then Ubuntu freezes.
I suspect the problem has something to do with firefox, specifically with running flash in firefox.
I don't have Nvidia hardware, so I don't think the problem is related to Nvidia.

---

### Post by cwmoser on 2009-08-25
My Ubuntu 9.04 64-bit has suddenly stated to freeze up.  I'm testing to see if it is the Screen Saver.  I've turned Screen Saver off to see what will happen.

Until a week ago, my 9.04 did not freeze - now it does.  Could it have been some update or something I've installed?

Carl

---

### Post by aYs-Halo on 2009-08-27
exact same situation here. any ideas? ;(

---

mine's solved -> [[ubuntu] HAL Internal Error! - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?p=7854627#post7854627")

---

### Post by cwmoser on 2009-08-27
Mine seems to have stopped freezing and locking up now that I have disabled Screen Saver.  Screen Saver was working until recently.  Maybe some errant update?

Carl

---

### Post by njnate on 2009-08-28
> **psychomichael said:**
> Yeah, you seem to have been doing more memory-intensive stuff than I was. I only had three tabs open and checking my Myspace at the time. I'm wondering if it isn't the NVIDIA bug because it doesn't crash until I use Firefox.

Well I have 8.04 and it is double booted with Vista well I have it installed in windows with Daemeon Lite I think I misspelled it but anyways it was running fine for the first 2 days after install then it started freezzing except the mouse I even went into windows and uninstalled then reinstalled and as I was downloading adobe it froze up again and also the top of the window the bar with the close minimize and maxamize buttons is missing it started doing that first no matter what I did it would not show up then it started freezzing please help me better understand what I need to do to fix either problem

---

### Post by cwmoser on 2009-08-30
I read on the Ubuntu bug reports that there is a freezing issue when the screen saver has to deal with random picture selections - i.e. the Fspot screen saver.

Also, I note that there are new drivers - 185.18.36.  Must be some confusion with these as I already had installed 190.18 drivers.  Anyway, I uninstalled the 190.18 and installed the 185.18.36 nVidia drivers.  Now my Ubuntu seems to be working without freezing and I am using the "Antinspect" screen saver.  Also, the graphical responsiveness seems better with Compiz.

So far so good.

Carl

---

### Post by Sin@Sin-Sacrifice on 2009-09-03
I have this problem now and didn´t for quite some time. I had 9.04 when it was first released as ¨stable¨ and it would almost never work but now it´s almost randomly freezing. I noticed that some strange occurrences will trigger the freeze like last 2 times was when I tried to change the font in gnome-terminal. Before some updates it would do it any time I opened an image, html, or pdf file. Now I can open PDFs and images but some other occurrences, like the font change make it happen. I&#472;e seen a lot of posting about this happening and am hoping I just missed a fix somewhere. Jaunty w/ 2.6.28-15 kernel. Help please.

---

### Post by jrader on 2009-09-03
I am runnin 9.04 and have just recently encountered problem. When inserting a picture CD into DVD/CD drive the system with freeze. The display changes and all attemps keyboard or mouse is locked. Only method to get out is a power off/on reboot. Now the CD in question is one with a onboard photo program provided. This program I'm sure automatically tries to load. 

I have gone to place / home floder / edit preferences media 

changed all to DO NOTHING.

Can anyone make suggestion what else I can do?

---

### Post by Babysitteronacid on 2009-09-27
The big freeze has also happened to me a few times as well. It seems, however, only to happen after the computer has woken up after hibernation. Even then it's not immediate but works for a few mins before freezing. Firefox has also always been running at the time.

(HP dv5, ATI, AMD)

---

### Post by manuelb on 2009-09-29
Unfortunately i'm experiencing the same lookup problems: i'm running an AMD 64X2 with Jaunty/32bit, nVidia GT9400 and everything worked flawlessy from the "alpha6" days until yesterday: i had an hard lookup and noticed these lines in syslog.0./kern.log.0

```

Sep 28 11:34:09 olanda kernel: [ 8461.629818] NVRM: Xid (0003:00): 13, 0001 00000000 0000502d 00000104 00000000 00000040
Sep 28 11:37:36 olanda kernel: [ 8669.101174] NVRM: Xid (0003:00): 8, Channel 00000003
Sep 28 11:37:48 olanda kernel: [ 8681.100050] NVRM: Xid (0003:00): 8, Channel 00000001
Sep 28 11:42:18 olanda kernel: [ 8951.101380] NVRM: Xid (0003:00): 8, Channel 00000001

```

Today happened another time and i don't have any message to look at. Now i'm inspecting what happened during updates in the last couple of days: it seems strange to me, everything worked perfectly until yesterday..


*UPDATED*

The updates just modified Firefox/Chromium and Apport-1, so nothing strange there.
Btw, my nVidia drivers are v185.18.14.

---

