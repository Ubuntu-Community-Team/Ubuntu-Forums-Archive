---
title: "brasero crashes"
date: 2009-04-29
forum: New to Ubuntu
---

### Post by gfunkera on 2009-04-29
im trying to burn an audio CD and every time i try burning with brasero it starts "normalizing" the tracks and then randomly disappears... i think its crashing or something..
i know that its not normal for it to do this because i have successfully burned audio discs before with it..
im running jaunty...

any ideas?

---

### Post by Dragonbite on 2009-04-29
Run it and after it crashes catch the dmesg and post here.

---

### Post by gfunkera on 2009-04-29
im not really sure what dmesg is/does but i guessed it was a command i was supposed to run in the console, and so i did that... by the way, this time i didnt start burning yet and it crashed.. i opened brasero again and tested it by waiting a few moments (like 2 or 3 minutes)... it crashed after the same length of time.. anyway, heres the dmesg output:

```
[    0.000000] BIOS EBDA/lowmem at: 0009b000/0009b000
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.28-11-generic (buildd@palmer) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 (Ubuntu 2.6.28-11.42-generic)
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
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009b000 (usable)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003fe53c00 (usable)
[    0.000000]  BIOS-e820: 000000003fe53c00 - 000000003fe55c00 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003fe55c00 - 000000003fe57c00 (ACPI data)
[    0.000000]  BIOS-e820: 000000003fe57c00 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fed00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fed20000 - 00000000feda0000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fef00000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.3 present.
[    0.000000] last_pfn = 0x3fe53 max_arch_pfn = 0x100000
[    0.000000] Scanning 2 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 0000000000007000 (usable)
[    0.000000]  modified: 0000000000007000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000008e000 (usable)
[    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000003fe53c00 (usable)
[    0.000000]  modified: 000000003fe53c00 - 000000003fe55c00 (ACPI NVS)
[    0.000000]  modified: 000000003fe55c00 - 000000003fe57c00 (ACPI data)
[    0.000000]  modified: 000000003fe57c00 - 0000000040000000 (reserved)
[    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fed00400 (reserved)
[    0.000000]  modified: 00000000fed20000 - 00000000feda0000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fef00000 (reserved)
[    0.000000]  modified: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000] kernel direct mapping tables up to 373fe000 @ 10000-16000
[    0.000000] RAMDISK: 378be000 - 37fefb7b
[    0.000000] Allocated new RAMDISK: 00881000 - 00fb2b7b
[    0.000000] Move RAMDISK from 00000000378be000 - 0000000037fefb7a to 00881000 - 00fb2b7a
[    0.000000] ACPI: RSDP 000FEBF0, 0024 (r2 DELL  )
[    0.000000] ACPI: XSDT 000FD08F, 0064 (r1 DELL    B8K           14 ASL        61)
[    0.000000] ACPI: FACP 000FD1AF, 00F4 (r3 DELL    B8K           14 ASL        61)
[    0.000000] ACPI: DSDT FFFCED62, 330F (r1   DELL    dt_ex     1000 INTL 20050624)
[    0.000000] ACPI: FACS 3FE53C00, 0040
[    0.000000] ACPI: SSDT FFFD234F, 009C (r1   DELL    st_ex     1000 INTL 20050624)
[    0.000000] ACPI: APIC 000FD2A3, 0092 (r1 DELL    B8K           14 ASL        61)
[    0.000000] ACPI: BOOT 000FD335, 0028 (r1 DELL    B8K           14 ASL        61)
[    0.000000] ACPI: MCFG 000FD35D, 003E (r1 DELL    B8K           14 ASL        61)
[    0.000000] ACPI: HPET 000FD39B, 0038 (r1 DELL    B8K           14 ASL        61)
[    0.000000] ACPI: DUMY 3FE55C00, 0024 (r1 DELL    B8K           14 ASL        61)
[    0.000000] ACPI: SLIC 000FD3D3, 0176 (r1 DELL    B8K           14 ASL        61)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 138MB HIGHMEM available.
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
[    0.000000]   #5 [000009b000 - 0000100000]    BIOS reserved ==> [000009b000 - 0000100000]
[    0.000000]   #6 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]
[    0.000000]   #7 [0000881000 - 0000fb2b7b]      NEW RAMDISK ==> [0000881000 - 0000fb2b7b]
[    0.000000]   #8 [0000012000 - 0000019000]          BOOTMAP ==> [0000012000 - 0000019000]
[    0.000000] found SMP MP-table at [c00fe710] 000fe710
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000373fe
[    0.000000]   HighMem  0x000373fe -> 0x0003fe53
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[4] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x00000007
[    0.000000]     0: 0x00000010 -> 0x0000008e
[    0.000000]     0: 0x00000100 -> 0x0003fe53
[    0.000000] On node 0 totalpages: 261588
[    0.000000] free_area_init_node: node 0, pgdat c06d0f80, node_mem_map c1000000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3937 pages, LIFO batch:0
[    0.000000]   Normal zone: 1736 pages used for memmap
[    0.000000]   Normal zone: 220470 pages, LIFO batch:31
[    0.000000]   HighMem zone: 277 pages used for memmap
[    0.000000]   HighMem zone: 35136 pages, LIFO batch:7
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x05] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x07] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x01] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x02] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x03] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0xff] high level lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x08] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 8, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 8 CPUs, 6 hotplug CPUs
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 0000000000007000 - 0000000000010000
[    0.000000] PM: Registered nosave memory: 000000000008e000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:a0000000)
[    0.000000] PERCPU: Allocating 45056 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 8, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 259543
[    0.000000] Kernel command line: root=UUID=59f52362-c41a-41b0-9d4e-8038cfa6bfb5 ro quiet splash
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1861.873 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] allocated 5234300 bytes of page_cgroup
[    0.004000] please try cgroup_disable=memory option if you don't want
[    0.004000] Scanning for low memory corruption every 60 seconds
[    0.004000] Memory: 1016408k/1046860k available (4126k kernel code, 29556k reserved, 2208k data, 532k init, 141652k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xf7bfe000 - 0xff3fe000   ( 120 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xf73fe000   ( 883 MB)
[    0.004000]       .init : 0xc0737000 - 0xc07bc000   ( 532 kB)
[    0.004000]       .data : 0xc0507a6f - 0xc072fe60   (2208 kB)
[    0.004000]       .text : 0xc0100000 - 0xc0507a6f   (4126 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.004000] hpet clockevent registered
[    0.004000] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.004000] Calibrating delay loop (skipped), value calculated using timer frequency.. 3723.74 BogoMIPS (lpj=7447492)
[    0.004000] Security Framework initialized
[    0.004000] SELinux:  Disabled at boot.
[    0.004000] AppArmor: AppArmor initialized
[    0.004000] Mount-cache hash table entries: 512
[    0.004000] Initializing cgroup subsys ns
[    0.004000] Initializing cgroup subsys cpuacct
[    0.004000] Initializing cgroup subsys memory
[    0.004000] Initializing cgroup subsys freezer
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 2048K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 0
[    0.004000] using mwait in idle threads.
[    0.004000] Checking 'hlt' instruction... OK.
[    0.018513] ACPI: Core revision 20080926
[    0.072760] ACPI: Checking initramfs for custom DSDT
[    0.480182] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.519864] CPU0: Intel(R) Core(TM)2 CPU          6300  @ 1.86GHz stepping 02
[    0.520002] Booting processor 1 APIC 0x1 ip 0x6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 3724.01 BogoMIPS (lpj=7448021)
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 2048K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.608479] CPU1: Intel(R) Core(TM)2 CPU          6300  @ 1.86GHz stepping 02
[    0.608495] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.612036] Brought up 2 CPUs
[    0.612039] Total of 2 processors activated (7447.75 BogoMIPS).
[    0.612086] CPU0 attaching sched-domain:
[    0.612089]  domain 0: span 0-1 level MC
[    0.612092]   groups: 0 1
[    0.612098] CPU1 attaching sched-domain:
[    0.612100]  domain 0: span 0-1 level MC
[    0.612102]   groups: 1 0
[    0.612172] net_namespace: 776 bytes
[    0.612172] Dell Dimension 9200 series board detected. Selecting BIOS-method for reboots.
[    0.612172] Booting paravirtualized kernel on bare hardware
[    0.612340] Time:  0:05:31  Date: 04/30/09
[    0.612340] regulator: core version 0.5
[    0.612340] NET: Registered protocol family 16
[    0.612340] EISA bus registered
[    0.612340] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.612340] ACPI: bus type pci registered
[    0.612340] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.612340] PCI: MCFG area at e0000000 reserved in E820
[    0.612340] PCI: Using MMCONFIG for extended config space
[    0.612340] PCI: Using configuration type 1 for base access
[    0.613234] ACPI: EC: Look up EC in DSDT
[    0.658975] ACPI: BIOS _OSI(Linux) query ignored
[    0.680247] ACPI: Interpreter enabled
[    0.680254] ACPI: (supports S0 S3 S4 S5)
[    0.680273] ACPI: Using IOAPIC for interrupt routing
[    0.763985] ACPI: No dock devices found.
[    0.764010] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.764101] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.764105] pci 0000:00:01.0: PME# disabled
[    0.764163] pci 0000:00:19.0: reg 10 32bit mmio: [0xdffe0000-0xdfffffff]
[    0.764170] pci 0000:00:19.0: reg 14 32bit mmio: [0xdffdf000-0xdffdffff]
[    0.764176] pci 0000:00:19.0: reg 18 io port: [0xecc0-0xecdf]
[    0.764201] pci 0000:00:19.0: PME# supported from D0 D3hot D3cold
[    0.764205] pci 0000:00:19.0: PME# disabled
[    0.764243] pci 0000:00:1a.0: reg 20 io port: [0xff20-0xff3f]
[    0.764289] pci 0000:00:1a.1: reg 20 io port: [0xff00-0xff1f]
[    0.764341] pci 0000:00:1a.7: reg 10 32bit mmio: [0xdffdec00-0xdffdefff]
[    0.764379] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.764384] pci 0000:00:1a.7: PME# disabled
[    0.764429] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.764433] pci 0000:00:1c.0: PME# disabled
[    0.764482] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.764486] pci 0000:00:1c.4: PME# disabled
[    0.764531] pci 0000:00:1d.0: reg 20 io port: [0xff80-0xff9f]
[    0.764577] pci 0000:00:1d.1: reg 20 io port: [0xff60-0xff7f]
[    0.764622] pci 0000:00:1d.2: reg 20 io port: [0xff40-0xff5f]
[    0.764674] pci 0000:00:1d.7: reg 10 32bit mmio: [0xff980800-0xff980bff]
[    0.764711] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.764716] pci 0000:00:1d.7: PME# disabled
[    0.764826] pci 0000:00:1f.0: quirk: region 0800-087f claimed by ICH6 ACPI/GPIO/TCO
[    0.764829] pci 0000:00:1f.0: quirk: region 0880-08bf claimed by ICH6 GPIO
[    0.764875] pci 0000:00:1f.2: reg 10 io port: [0xfe00-0xfe07]
[    0.764882] pci 0000:00:1f.2: reg 14 io port: [0xfe10-0xfe13]
[    0.764887] pci 0000:00:1f.2: reg 18 io port: [0xfe20-0xfe27]
[    0.764894] pci 0000:00:1f.2: reg 1c io port: [0xfe30-0xfe33]
[    0.764899] pci 0000:00:1f.2: reg 20 io port: [0xfec0-0xfedf]
[    0.764905] pci 0000:00:1f.2: reg 24 32bit mmio: [0xff970000-0xff9707ff]
[    0.764920] pci 0000:00:1f.2: PME# supported from D3hot
[    0.764923] pci 0000:00:1f.2: PME# disabled
[    0.764945] pci 0000:00:1f.3: reg 10 32bit mmio: [0xdffdeb00-0xdffdebff]
[    0.764963] pci 0000:00:1f.3: reg 20 io port: [0xece0-0xecff]
[    0.765007] pci 0000:01:00.0: reg 10 32bit mmio: [0xdd000000-0xddffffff]
[    0.765016] pci 0000:01:00.0: reg 14 64bit mmio: [0xc0000000-0xcfffffff]
[    0.765025] pci 0000:01:00.0: reg 1c 64bit mmio: [0xde000000-0xdeffffff]
[    0.765034] pci 0000:01:00.0: reg 30 32bit mmio: [0xdfe00000-0xdfe1ffff]
[    0.765082] pci 0000:00:01.0: bridge 32bit mmio: [0xdd000000-0xdfefffff]
[    0.765086] pci 0000:00:01.0: bridge 64bit mmio pref: [0xc0000000-0xcfffffff]
[    0.765130] pci 0000:00:1c.0: bridge 32bit mmio: [0xdcf00000-0xdcffffff]
[    0.765220] pci 0000:04:03.0: reg 10 32bit mmio: [0xdb000000-0xdbffffff]
[    0.765306] pci 0000:04:04.0: reg 10 io port: [0xdce0-0xdcff]
[    0.765317] pci 0000:04:04.0: reg 14 64bit mmio: [0xdcc00000-0xdcdfffff]
[    0.765329] pci 0000:04:04.0: reg 1c 64bit mmio: [0xd4000000-0xd7ffffff]
[    0.765348] pci 0000:04:04.0: supports D1 D2
[    0.765384] pci 0000:04:05.0: reg 10 32bit mmio: [0xdcef8000-0xdcefffff]
[    0.765460] pci 0000:00:1e.0: transparent bridge
[    0.765464] pci 0000:00:1e.0: bridge io port: [0xd000-0xdfff]
[    0.765469] pci 0000:00:1e.0: bridge 32bit mmio: [0xd4000000-0xdcefffff]
[    0.765490] bus 00 -> node 0
[    0.765496] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.766324] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI4._PRT]
[    0.766989] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI2._PRT]
[    0.767500] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[    0.768030] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI5._PRT]
[    1.665433] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 15)
[    1.666205] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *9 10 11 12 15)
[    1.666988] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 7 9 10 11 12 15)
[    1.667764] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 9 10 11 12 15)
[    1.668686] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 *10 11 12 15)
[    1.669456] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 *10 11 12 15)
[    1.670230] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 *5 6 7 9 10 11 12 15)
[    1.671015] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 *4 5 6 7 9 10 11 12 15)
[    1.671441] ACPI: WMI: Mapper loaded
[    1.671479] SCSI subsystem initialized
[    1.671479] libata version 3.00 loaded.
[    1.671479] usbcore: registered new interface driver usbfs
[    1.671479] usbcore: registered new interface driver hub
[    1.671479] usbcore: registered new device driver usb
[    1.671479] PCI: Using ACPI for IRQ routing
[    1.676014] Bluetooth: Core ver 2.13
[    1.676031] NET: Registered protocol family 31
[    1.676031] Bluetooth: HCI device and connection manager initialized
[    1.676031] Bluetooth: HCI socket layer initialized
[    1.676031] NET: Registered protocol family 8
[    1.676031] NET: Registered protocol family 20
[    1.676044] NetLabel: Initializing
[    1.676046] NetLabel:  domain hash size = 128
[    1.676048] NetLabel:  protocols = UNLABELED CIPSOv4
[    1.676062] NetLabel:  unlabeled traffic allowed by default
[    1.676077] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    1.676083] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    1.680069] AppArmor: AppArmor Filesystem Enabled
[    1.684014] Switched to high resolution mode on CPU 0
[    1.684550] Switched to high resolution mode on CPU 1
[    1.688053] pnp: PnP ACPI init
[    1.688063] ACPI: bus type pnp registered
[    1.698473] pnp 00:01: io resource (0x800-0x85f) overlaps 0000:00:1f.0 BAR 7 (0x800-0x87f), disabling
[    1.698477] pnp 00:01: io resource (0x860-0x8ff) overlaps 0000:00:1f.0 BAR 7 (0x800-0x87f), disabling
[    1.732342] pnp: PnP ACPI: found 9 devices
[    1.732344] ACPI: ACPI bus type pnp unregistered
[    1.732349] PnPBIOS: Disabled by ACPI PNP
[    1.732359] system 00:01: ioport range 0xc00-0xc7f has been reserved
[    1.732367] system 00:06: iomem range 0x0-0x9ffff could not be reserved
[    1.732370] system 00:06: iomem range 0x100000-0xffffff could not be reserved
[    1.732373] system 00:06: iomem range 0x1000000-0x3fe53bff could not be reserved
[    1.732376] system 00:06: iomem range 0xf0000-0xfffff could not be reserved
[    1.732379] system 00:06: iomem range 0xc0000-0xd7fff could not be reserved
[    1.732382] system 00:06: iomem range 0xfec00000-0xfecfffff has been reserved
[    1.732385] system 00:06: iomem range 0xfee00000-0xfeefffff has been reserved
[    1.732388] system 00:06: iomem range 0xffb00000-0xffbfffff has been reserved
[    1.732391] system 00:06: iomem range 0xffc00000-0xffffffff has been reserved
[    1.732396] system 00:07: ioport range 0x100-0x1fe has been reserved
[    1.732399] system 00:07: ioport range 0x200-0x277 has been reserved
[    1.732402] system 00:07: ioport range 0x280-0x2e7 has been reserved
[    1.732404] system 00:07: ioport range 0x2e8-0x2ef has been reserved
[    1.732407] system 00:07: ioport range 0x2f0-0x2f7 has been reserved
[    1.732410] system 00:07: ioport range 0x2f8-0x2ff has been reserved
[    1.732412] system 00:07: ioport range 0x300-0x377 has been reserved
[    1.732415] system 00:07: ioport range 0x380-0x3bb has been reserved
[    1.732417] system 00:07: ioport range 0x3c0-0x3e7 could not be reserved
[    1.732420] system 00:07: ioport range 0x3f6-0x3f7 has been reserved
[    1.732422] system 00:07: ioport range 0x400-0x4cf has been reserved
[    1.732425] system 00:07: ioport range 0x4d2-0x57f has been reserved
[    1.732428] system 00:07: ioport range 0x580-0x677 has been reserved
[    1.732430] system 00:07: ioport range 0x680-0x777 has been reserved
[    1.732433] system 00:07: ioport range 0x780-0x7bb has been reserved
[    1.732435] system 00:07: ioport range 0x7c0-0x7ff has been reserved
[    1.732438] system 00:07: ioport range 0x8e0-0x8ff has been reserved
[    1.732440] system 00:07: ioport range 0x900-0x9fe has been reserved
[    1.732443] system 00:07: ioport range 0xa00-0xafe has been reserved
[    1.732446] system 00:07: ioport range 0xb00-0xbfe has been reserved
[    1.732449] system 00:07: ioport range 0xc80-0xcaf has been reserved
[    1.732451] system 00:07: ioport range 0xcb0-0xcbf has been reserved
[    1.732454] system 00:07: ioport range 0xcc0-0xcf7 has been reserved
[    1.732456] system 00:07: ioport range 0xd00-0xdfe has been reserved
[    1.732459] system 00:07: ioport range 0xe00-0xefe has been reserved
[    1.732462] system 00:07: ioport range 0xf00-0xffe has been reserved
[    1.732466] system 00:07: ioport range 0x2000-0x20fe has been reserved
[    1.732469] system 00:07: ioport range 0x2100-0x21fe has been reserved
[    1.732472] system 00:07: ioport range 0x2200-0x22fe has been reserved
[    1.732475] system 00:07: ioport range 0x2300-0x23fe has been reserved
[    1.732477] system 00:07: ioport range 0x2400-0x24fe has been reserved
[    1.732480] system 00:07: ioport range 0x2500-0x25fe has been reserved
[    1.732483] system 00:07: ioport range 0x2600-0x26fe has been reserved
[    1.732485] system 00:07: ioport range 0x2700-0x27fe has been reserved
[    1.732488] system 00:07: ioport range 0x2800-0x28fe has been reserved
[    1.732491] system 00:07: ioport range 0x2900-0x29fe has been reserved
[    1.732493] system 00:07: ioport range 0x2a00-0x2afe has been reserved
[    1.732496] system 00:07: ioport range 0x2b00-0x2bfe has been reserved
[    1.732499] system 00:07: ioport range 0x2c00-0x2cfe has been reserved
[    1.732501] system 00:07: ioport range 0x2d00-0x2dfe has been reserved
[    1.732504] system 00:07: ioport range 0x2e00-0x2efe has been reserved
[    1.732507] system 00:07: ioport range 0x2f00-0x2ffe has been reserved
[    1.732510] system 00:07: ioport range 0x5000-0x50fe has been reserved
[    1.732513] system 00:07: ioport range 0x5100-0x51fe has been reserved
[    1.732515] system 00:07: ioport range 0x5200-0x52fe has been reserved
[    1.732518] system 00:07: ioport range 0x5300-0x53fe has been reserved
[    1.732521] system 00:07: ioport range 0x5400-0x54fe has been reserved
[    1.732524] system 00:07: ioport range 0x5500-0x55fe has been reserved
[    1.732526] system 00:07: ioport range 0x5600-0x56fe has been reserved
[    1.732529] system 00:07: ioport range 0x5700-0x57fe has been reserved
[    1.732532] system 00:07: ioport range 0x5800-0x58fe has been reserved
[    1.732535] system 00:07: ioport range 0x5900-0x59fe has been reserved
[    1.732538] system 00:07: ioport range 0x5a00-0x5afe has been reserved
[    1.732541] system 00:07: ioport range 0x5b00-0x5bfe has been reserved
[    1.732544] system 00:07: ioport range 0x5c00-0x5cfe has been reserved
[    1.732546] system 00:07: ioport range 0x5d00-0x5dfe has been reserved
[    1.732549] system 00:07: ioport range 0x5e00-0x5efe has been reserved
[    1.732552] system 00:07: ioport range 0x5f00-0x5ffe has been reserved
[    1.732555] system 00:07: ioport range 0x6000-0x60fe has been reserved
[    1.732558] system 00:07: ioport range 0x6100-0x61fe has been reserved
[    1.732560] system 00:07: ioport range 0x6200-0x62fe has been reserved
[    1.732563] system 00:07: ioport range 0x6300-0x63fe has been reserved
[    1.732566] system 00:07: ioport range 0x6400-0x64fe has been reserved
[    1.732569] system 00:07: ioport range 0x6500-0x65fe has been reserved
[    1.732572] system 00:07: ioport range 0x6600-0x66fe has been reserved
[    1.732575] system 00:07: ioport range 0x6700-0x67fe has been reserved
[    1.732577] system 00:07: ioport range 0x6800-0x68fe has been reserved
[    1.732580] system 00:07: ioport range 0x6900-0x69fe has been reserved
[    1.732583] system 00:07: ioport range 0x6a00-0x6afe has been reserved
[    1.732586] system 00:07: ioport range 0x6b00-0x6bfe has been reserved
[    1.732589] system 00:07: ioport range 0x6c00-0x6cfe has been reserved
[    1.732592] system 00:07: ioport range 0x6d00-0x6dfe has been reserved
[    1.732595] system 00:07: ioport range 0x6e00-0x6efe has been reserved
[    1.732598] system 00:07: ioport range 0x6f00-0x6ffe has been reserved
[    1.732601] system 00:07: ioport range 0xa000-0xa0fe has been reserved
[    1.732603] system 00:07: ioport range 0xa100-0xa1fe has been reserved
[    1.732606] system 00:07: ioport range 0xa200-0xa2fe has been reserved
[    1.732609] system 00:07: ioport range 0xa300-0xa3fe has been reserved
[    1.732612] system 00:07: ioport range 0xa400-0xa4fe has been reserved
[    1.732615] system 00:07: ioport range 0xa500-0xa5fe has been reserved
[    1.732618] system 00:07: ioport range 0xa600-0xa6fe has been reserved
[    1.732621] system 00:07: ioport range 0xa700-0xa7fe has been reserved
[    1.732624] system 00:07: ioport range 0xa800-0xa8fe has been reserved
[    1.732627] system 00:07: ioport range 0xa900-0xa9fe has been reserved
[    1.732629] system 00:07: ioport range 0xaa00-0xaafe has been reserved
[    1.732632] system 00:07: ioport range 0xab00-0xabfe has been reserved
[    1.732635] system 00:07: ioport range 0xac00-0xacfe has been reserved
[    1.732638] system 00:07: ioport range 0xad00-0xadfe has been reserved
[    1.732641] system 00:07: ioport range 0xae00-0xaefe has been reserved
[    1.732644] system 00:07: ioport range 0xaf00-0xaffe has been reserved
[    1.732647] system 00:07: iomem range 0xe0000000-0xefffffff has been reserved
[    1.732650] system 00:07: iomem range 0xfeda0000-0xfedacfff has been reserved
[    1.767347] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    1.767349] pci 0000:00:01.0:   IO window: disabled
[    1.767353] pci 0000:00:01.0:   MEM window: 0xdd000000-0xdfefffff
[    1.767357] pci 0000:00:01.0:   PREFETCH window: 0x000000c0000000-0x000000cfffffff
[    1.767362] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
[    1.767364] pci 0000:00:1c.0:   IO window: disabled
[    1.767369] pci 0000:00:1c.0:   MEM window: 0xdcf00000-0xdcffffff
[    1.767373] pci 0000:00:1c.0:   PREFETCH window: disabled
[    1.767378] pci 0000:00:1c.4: PCI bridge, secondary bus 0000:03
[    1.767380] pci 0000:00:1c.4:   IO window: disabled
[    1.767385] pci 0000:00:1c.4:   MEM window: disabled
[    1.767389] pci 0000:00:1c.4:   PREFETCH window: disabled
[    1.767395] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:04
[    1.767398] pci 0000:00:1e.0:   IO window: 0xd000-0xdfff
[    1.767403] pci 0000:00:1e.0:   MEM window: 0xd4000000-0xdcefffff
[    1.767407] pci 0000:00:1e.0:   PREFETCH window: disabled
[    1.767419] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.767423] pci 0000:00:01.0: setting latency timer to 64
[    1.767429] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.767434] pci 0000:00:1c.0: setting latency timer to 64
[    1.767440] pci 0000:00:1c.4: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.767444] pci 0000:00:1c.4: setting latency timer to 64
[    1.767451] pci 0000:00:1e.0: setting latency timer to 64
[    1.767454] bus: 00 index 0 io port: [0x00-0xffff]
[    1.767457] bus: 00 index 1 mmio: [0x000000-0xffffffff]
[    1.767459] bus: 01 index 0 mmio: [0x0-0x0]
[    1.767461] bus: 01 index 1 mmio: [0xdd000000-0xdfefffff]
[    1.767463] bus: 01 index 2 mmio: [0xc0000000-0xcfffffff]
[    1.767465] bus: 01 index 3 mmio: [0x0-0x0]
[    1.767467] bus: 02 index 0 mmio: [0x0-0x0]
[    1.767469] bus: 02 index 1 mmio: [0xdcf00000-0xdcffffff]
[    1.767471] bus: 02 index 2 mmio: [0x0-0x0]
[    1.767473] bus: 02 index 3 mmio: [0x0-0x0]
[    1.767474] bus: 03 index 0 mmio: [0x0-0x0]
[    1.767476] bus: 03 index 1 mmio: [0x0-0x0]
[    1.767478] bus: 03 index 2 mmio: [0x0-0x0]
[    1.767480] bus: 03 index 3 mmio: [0x0-0x0]
[    1.767482] bus: 04 index 0 io port: [0xd000-0xdfff]
[    1.767484] bus: 04 index 1 mmio: [0xd4000000-0xdcefffff]
[    1.767486] bus: 04 index 2 mmio: [0x0-0x0]
[    1.767488] bus: 04 index 3 io port: [0x00-0xffff]
[    1.767490] bus: 04 index 4 mmio: [0x000000-0xffffffff]
[    1.767498] NET: Registered protocol family 2
[    1.780091] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    1.780359] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    1.780669] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    1.780851] TCP: Hash tables configured (established 131072 bind 65536)
[    1.780853] TCP reno registered
[    1.788132] NET: Registered protocol family 1
[    1.788274] checking if image is initramfs... it is
[    2.429890] Freeing initrd memory: 7366k freed
[    2.429934] Simple Boot Flag at 0x7a set to 0x1
[    2.430117] cpufreq: No nForce2 chipset.
[    2.430260] audit: initializing netlink socket (disabled)
[    2.430283] type=2000 audit(1241049932.428:1): initialized
[    2.437753] highmem bounce pool size: 64 pages
[    2.437758] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    2.439164] VFS: Disk quotas dquot_6.5.1
[    2.439231] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    2.439853] fuse init (API version 7.10)
[    2.439939] msgmni has been set to 1723
[    2.440124] alg: No test for stdrng (krng)
[    2.440135] io scheduler noop registered
[    2.440138] io scheduler anticipatory registered
[    2.440140] io scheduler deadline registered
[    2.440153] io scheduler cfq registered (default)
[    2.440292] pci 0000:01:00.0: Boot video device
[    2.497084] pcieport-driver 0000:00:01.0: setting latency timer to 64
[    2.497120] pcieport-driver 0000:00:01.0: found MSI capability
[    2.497143] pcieport-driver 0000:00:01.0: irq 2303 for MSI/MSI-X
[    2.497152] pci_express 0000:00:01.0:pcie00: allocate port service
[    2.497167] pci_express 0000:00:01.0:pcie03: allocate port service
[    2.497215] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    2.497247] pcieport-driver 0000:00:1c.0: found MSI capability
[    2.497270] pcieport-driver 0000:00:1c.0: irq 2302 for MSI/MSI-X
[    2.497281] pci_express 0000:00:1c.0:pcie00: allocate port service
[    2.497294] pci_express 0000:00:1c.0:pcie02: allocate port service
[    2.497307] pci_express 0000:00:1c.0:pcie03: allocate port service
[    2.497361] pcieport-driver 0000:00:1c.4: setting latency timer to 64
[    2.497393] pcieport-driver 0000:00:1c.4: found MSI capability
[    2.497416] pcieport-driver 0000:00:1c.4: irq 2301 for MSI/MSI-X
[    2.497427] pci_express 0000:00:1c.4:pcie00: allocate port service
[    2.497440] pci_express 0000:00:1c.4:pcie02: allocate port service
[    2.497456] pci_express 0000:00:1c.4:pcie03: allocate port service
[    2.497522] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    2.521185] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    2.521316] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    2.521318] ACPI: Power Button (FF) [PWRF]
[    2.521366] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    2.521374] ACPI: Power Button (CM) [VBTN]
[    2.522118] processor ACPI_CPU:00: registered as cooling_device0
[    2.522154] processor ACPI_CPU:01: registered as cooling_device1
[    2.621672] isapnp: Scanning for PnP cards...
[    2.974499] isapnp: No Plug & Play device found
[    2.980605] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    2.981675] brd: module loaded
[    2.982027] loop: module loaded
[    2.982092] Fixed MDIO Bus: probed
[    2.982097] PPP generic driver version 2.4.2
[    2.982154] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    2.982184] Driver 'sd' needs updating - please use bus_type methods
[    2.982193] Driver 'sr' needs updating - please use bus_type methods
[    2.982234] ahci 0000:00:1f.2: version 3.0
[    2.982246] ahci 0000:00:1f.2: PCI INT C -> GSI 20 (level, low) -> IRQ 20
[    2.982277] ahci 0000:00:1f.2: irq 2300 for MSI/MSI-X
[    2.982361] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 6 ports 3 Gbps 0x3f impl RAID mode
[    2.982365] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part ems 
[    2.982369] ahci 0000:00:1f.2: setting latency timer to 64
[    2.982816] scsi0 : ahci
[    2.982904] scsi1 : ahci
[    2.982969] scsi2 : ahci
[    2.983029] scsi3 : ahci
[    2.983097] scsi4 : ahci
[    2.983159] scsi5 : ahci
[    2.983197] ata1: SATA max UDMA/133 abar m2048@0xff970000 port 0xff970100 irq 2300
[    2.983200] ata2: SATA max UDMA/133 abar m2048@0xff970000 port 0xff970180 irq 2300
[    2.983203] ata3: SATA max UDMA/133 abar m2048@0xff970000 port 0xff970200 irq 2300
[    2.983205] ata4: SATA max UDMA/133 abar m2048@0xff970000 port 0xff970280 irq 2300
[    2.983208] ata5: SATA max UDMA/133 abar m2048@0xff970000 port 0xff970300 irq 2300
[    2.983211] ata6: SATA max UDMA/133 abar m2048@0xff970000 port 0xff970380 irq 2300
[    3.300037] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    3.337319] ata1.00: ATA-7: ST3250820AS, 3.ADG, max UDMA/133
[    3.337322] ata1.00: 488281250 sectors, multi 0: LBA48 NCQ (depth 31/32)
[    3.395653] ata1.00: configured for UDMA/133
[    4.132035] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    4.134512] ata2.00: ATAPI: TSSTcorp DVD+/-RW TS-H653A, D400, max UDMA/33
[    4.134532] ata2.00: applying bridge limits
[    4.137251] ata2.00: configured for UDMA/33
[    4.472034] ata3: SATA link down (SStatus 0 SControl 300)
[    4.808034] ata4: SATA link down (SStatus 0 SControl 300)
[    5.144034] ata5: SATA link down (SStatus 0 SControl 300)
[    5.480034] ata6: SATA link down (SStatus 0 SControl 300)
[    5.496144] scsi 0:0:0:0: Direct-Access     ATA      ST3250820AS      3.AD PQ: 0 ANSI: 5
[    5.496269] sd 0:0:0:0: [sda] 488281250 512-byte hardware sectors: (250 GB/232 GiB)
[    5.496287] sd 0:0:0:0: [sda] Write Protect is off
[    5.496290] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.496317] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.496383] sd 0:0:0:0: [sda] 488281250 512-byte hardware sectors: (250 GB/232 GiB)
[    5.496398] sd 0:0:0:0: [sda] Write Protect is off
[    5.496400] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.496427] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.496430]  sda: sda1 sda2 < sda5 >
[    5.535471] sd 0:0:0:0: [sda] Attached SCSI disk
[    5.535517] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    5.535932] scsi 1:0:0:0: CD-ROM            TSSTcorp DVD+-RW TS-H653A D400 PQ: 0 ANSI: 5
[    5.539636] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[    5.539640] Uniform CD-ROM driver Revision: 3.20
[    5.539745] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    5.539789] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    5.540527] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    5.540547] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    5.540563] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    5.540566] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    5.540630] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    5.544533] ehci_hcd 0000:00:1a.7: debug port 1
[    5.544539] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    5.544553] ehci_hcd 0000:00:1a.7: irq 22, io mem 0xdffdec00
[    5.560041] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    5.560125] usb usb1: configuration #1 chosen from 1 choice
[    5.560158] hub 1-0:1.0: USB hub found
[    5.560166] hub 1-0:1.0: 4 ports detected
[    5.560291] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    5.560301] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    5.560304] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    5.560349] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    5.564249] ehci_hcd 0000:00:1d.7: debug port 1
[    5.564254] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    5.564266] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xff980800
[    5.580020] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    5.580090] usb usb2: configuration #1 chosen from 1 choice
[    5.580120] hub 2-0:1.0: USB hub found
[    5.580128] hub 2-0:1.0: 6 ports detected
[    5.580245] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    5.580262] uhci_hcd: USB Universal Host Controller Interface driver
[    5.580283] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    5.580291] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    5.580294] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    5.580335] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    5.580363] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000ff20
[    5.580437] usb usb3: configuration #1 chosen from 1 choice
[    5.580462] hub 3-0:1.0: USB hub found
[    5.580469] hub 3-0:1.0: 2 ports detected
[    5.580550] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    5.580556] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    5.580559] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    5.580603] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    5.580630] uhci_hcd 0000:00:1a.1: irq 17, io base 0x0000ff00
[    5.580702] usb usb4: configuration #1 chosen from 1 choice
[    5.580728] hub 4-0:1.0: USB hub found
[    5.580735] hub 4-0:1.0: 2 ports detected
[    5.580817] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    5.580823] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    5.580827] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    5.580868] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    5.580889] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000ff80
[    5.580962] usb usb5: configuration #1 chosen from 1 choice
[    5.580987] hub 5-0:1.0: USB hub found
[    5.580994] hub 5-0:1.0: 2 ports detected
[    5.581075] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    5.581081] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    5.581084] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    5.581139] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    5.581160] uhci_hcd 0000:00:1d.1: irq 17, io base 0x0000ff60
[    5.581233] usb usb6: configuration #1 chosen from 1 choice
[    5.581258] hub 6-0:1.0: USB hub found
[    5.581264] hub 6-0:1.0: 2 ports detected
[    5.581345] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    5.581350] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    5.581353] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    5.581398] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    5.581425] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000ff40
[    5.581497] usb usb7: configuration #1 chosen from 1 choice
[    5.581522] hub 7-0:1.0: USB hub found
[    5.581529] hub 7-0:1.0: 2 ports detected
[    5.581656] usbcore: registered new interface driver libusual
[    5.581689] usbcore: registered new interface driver usbserial
[    5.581700] USB Serial support registered for generic
[    5.581720] usbcore: registered new interface driver usbserial_generic
[    5.581722] usbserial: USB Serial Driver core
[    5.581773] PNP: No PS/2 controller found. Probing ports directly.
[    5.584321] serio: i8042 KBD port at 0x60,0x64 irq 1
[    5.584327] serio: i8042 AUX port at 0x60,0x64 irq 12
[    5.588060] mice: PS/2 mouse device common for all mice
[    5.600105] rtc_cmos 00:05: RTC can wake from S4
[    5.600142] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    5.600166] rtc0: alarms up to one day, 242 bytes nvram, hpet irqs
[    5.600247] device-mapper: uevent: version 1.0.3
[    5.600337] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
[    5.600413] device-mapper: multipath: version 1.0.5 loaded
[    5.600416] device-mapper: multipath round-robin: version 1.0.0 loaded
[    5.600495] EISA: Probing bus 0 at eisa.0
[    5.600499] EISA: Cannot allocate resource for mainboard
[    5.600505] Cannot allocate resource for EISA slot 2
[    5.600514] Cannot allocate resource for EISA slot 5
[    5.600517] Cannot allocate resource for EISA slot 6
[    5.600526] EISA: Detected 0 cards.
[    5.600577] cpuidle: using governor ladder
[    5.600580] cpuidle: using governor menu
[    5.601118] TCP cubic registered
[    5.601215] NET: Registered protocol family 10
[    5.601695] lo: Disabled Privacy Extensions
[    5.602040] NET: Registered protocol family 17
[    5.602057] Bluetooth: L2CAP ver 2.11
[    5.602059] Bluetooth: L2CAP socket layer initialized
[    5.602062] Bluetooth: SCO (Voice Link) ver 0.6
[    5.602064] Bluetooth: SCO socket layer initialized
[    5.602096] Bluetooth: RFCOMM socket layer initialized
[    5.602102] Bluetooth: RFCOMM TTY layer initialized
[    5.602104] Bluetooth: RFCOMM ver 1.10
[    5.602158] Using IPI No-Shortcut mode
[    5.602228] registered taskstats version 1
[    5.602368]   Magic number: 5:750:52
[    5.602426] rtc_cmos 00:05: setting system clock to 2009-04-30 00:05:36 UTC (1241049936)
[    5.602429] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    5.602431] EDD information not available.
[    5.602714] Freeing unused kernel memory: 532k freed
[    5.602846] Write protecting the kernel text: 4128k
[    5.602893] Write protecting the kernel read-only data: 1532k
[    5.810177] e1000e: Intel(R) PRO/1000 Network Driver - 0.3.3.3-k6
[    5.810180] e1000e: Copyright (c) 1999-2008 Intel Corporation.
[    5.810230] e1000e 0000:00:19.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    5.810239] e1000e 0000:00:19.0: setting latency timer to 64
[    5.810363] e1000e 0000:00:19.0: irq 2299 for MSI/MSI-X
[    6.015035] 0000:00:19.0: eth0: (PCI Express:2.5GB/s:Width x1) 00:19:d1:5e:f3:a0
[    6.015038] 0000:00:19.0: eth0: Intel(R) PRO/1000 Network Connection
[    6.015061] 0000:00:19.0: eth0: MAC: 5, PHY: 6, PBA No: 1021ff-0ff
[    6.120694] PM: Starting manual resume from disk
[    6.120697] PM: Resume from partition 8:5
[    6.120699] PM: Checking hibernation image.
[    6.120834] PM: Resume from disk failed.
[    6.152057] usb 4-1: new low speed USB device using uhci_hcd and address 2
[    6.159229] kjournald starting.  Commit interval 5 seconds
[    6.159237] EXT3-fs: mounted filesystem with ordered data mode.
[    6.327795] usb 4-1: configuration #1 chosen from 1 choice
[    6.568037] usb 6-1: new low speed USB device using uhci_hcd and address 2
[    6.752346] usb 6-1: configuration #1 chosen from 1 choice
[   11.413530] udev: starting version 141
[   11.560841] Linux agpgart interface v0.103
[   11.634741] end_request: I/O error, dev sr0, sector 0
[   11.634748] Buffer I/O error on device sr0, logical block 0
[   11.635471] end_request: I/O error, dev sr0, sector 0
[   11.635476] Buffer I/O error on device sr0, logical block 0
[   11.638050] iTCO_vendor_support: vendor-support=0
[   11.665257] usbcore: registered new interface driver hiddev
[   11.678451] input: Logitech Optical USB Mouse as /devices/pci0000:00/0000:00:1a.1/usb4/4-1/4-1:1.0/input/input3
[   11.702432] generic-usb 0003:046D:C016.0001: input,hidraw0: USB HID v1.10 Mouse [Logitech Optical USB Mouse] on usb-0000:00:1a.1-1/input0
[   11.702518] usbcore: registered new interface driver usbhid
[   11.702521] usbhid: v2.6:USB HID core driver
[   12.218665] nvidia: module license 'NVIDIA' taints kernel.
[   12.472019] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   12.472028] nvidia 0000:01:00.0: setting latency timer to 64
[   12.473140] NVRM: loading NVIDIA UNIX x86 Kernel Module  180.44  Mon Mar 23 14:59:10 PST 2009
[   12.512903] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05
[   12.513043] iTCO_wdt: failed to reset NO_REBOOT flag, reboot disabled by hardware
[   12.513054] iTCO_wdt: No card detected
[   12.690821] input: PC Speaker as /devices/platform/pcspkr/input/input4
[   12.732094] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   12.873085] input: Microsoft Microsoft Wireless Optical Desktop&#65533; 2.10 as /devices/pci0000:00/0000:00:1d.1/usb6/6-1/6-1:1.0/input/input5
[   12.880103] microsoft 0003:045E:009D.0002: input,hidraw1: USB HID v1.11 Keyboard [Microsoft Microsoft Wireless Optical Desktop&#65533; 2.10] on usb-0000:00:1d.1-1/input0
[   12.880159] cfg80211: Calling CRDA to update world regulatory domain
[   12.994522] cfg80211: World regulatory domain updated:
[   12.994526]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   12.994529]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   12.994531]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   12.994534]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   12.994536]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   12.994539]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.003902] Linux video capture interface: v2.00
[   13.016006] input: Microsoft Microsoft Wireless Optical Desktop&#65533; 2.10 as /devices/pci0000:00/0000:00:1d.1/usb6/6-1/6-1:1.1/input/input6
[   13.026839] microsoft 0003:045E:009D.0003: input,hidraw2: USB HID v1.11 Mouse [Microsoft Microsoft Wireless Optical Desktop&#65533; 2.10] on usb-0000:00:1d.1-1/input1
[   13.263809] cx88/0: cx2388x v4l2 driver version 0.0.6 loaded
[   13.263850] cx8800 0000:04:03.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   13.264627] cx88[0]: Your board isn't known (yet) to the driver.  You can
[   13.264628] cx88[0]: try to pick one of the existing card configs via
[   13.264629] cx88[0]: card=<n> insmod option.  Updating to the latest
[   13.264630] cx88[0]: version might help as well.
[   13.264634] cx88[0]: Here is a list of valid choices for the card=<n> insmod option:
[   13.264636] cx88[0]:    card=0 -> UNKNOWN/GENERIC
[   13.264639] cx88[0]:    card=1 -> Hauppauge WinTV 34xxx models
[   13.264641] cx88[0]:    card=2 -> GDI Black Gold
[   13.264643] cx88[0]:    card=3 -> PixelView
[   13.264645] cx88[0]:    card=4 -> ATI TV Wonder Pro
[   13.264647] cx88[0]:    card=5 -> Leadtek Winfast 2000XP Expert
[   13.264649] cx88[0]:    card=6 -> AverTV Studio 303 (M126)
[   13.264651] cx88[0]:    card=7 -> MSI TV-@nywhere Master
[   13.264654] cx88[0]:    card=8 -> Leadtek Winfast DV2000
[   13.264655] cx88[0]:    card=9 -> Leadtek PVR 2000
[   13.264658] cx88[0]:    card=10 -> IODATA GV-VCP3/PCI
[   13.264660] cx88[0]:    card=11 -> Prolink PlayTV PVR
[   13.264662] cx88[0]:    card=12 -> ASUS PVR-416
[   13.264664] cx88[0]:    card=13 -> MSI TV-@nywhere
[   13.264666] cx88[0]:    card=14 -> KWorld/VStream XPert DVB-T
[   13.264668] cx88[0]:    card=15 -> DViCO FusionHDTV DVB-T1
[   13.264670] cx88[0]:    card=16 -> KWorld LTV883RF
[   13.264672] cx88[0]:    card=17 -> DViCO FusionHDTV 3 Gold-Q
[   13.264674] cx88[0]:    card=18 -> Hauppauge Nova-T DVB-T
[   13.264676] cx88[0]:    card=19 -> Conexant DVB-T reference design
[   13.264679] cx88[0]:    card=20 -> Provideo PV259
[   13.264681] cx88[0]:    card=21 -> DViCO FusionHDTV DVB-T Plus
[   13.264683] cx88[0]:    card=22 -> pcHDTV HD3000 HDTV
[   13.264685] cx88[0]:    card=23 -> digitalnow DNTV Live! DVB-T
[   13.264687] cx88[0]:    card=24 -> Hauppauge WinTV 28xxx (Roslyn) models
[   13.264689] cx88[0]:    card=25 -> Digital-Logic MICROSPACE Entertainment Center (MEC)
[   13.264692] cx88[0]:    card=26 -> IODATA GV/BCTV7E
[   13.264694] cx88[0]:    card=27 -> PixelView PlayTV Ultra Pro (Stereo)
[   13.264696] cx88[0]:    card=28 -> DViCO FusionHDTV 3 Gold-T
[   13.264698] cx88[0]:    card=29 -> ADS Tech Instant TV DVB-T PCI
[   13.264700] cx88[0]:    card=30 -> TerraTec Cinergy 1400 DVB-T
[   13.264703] cx88[0]:    card=31 -> DViCO FusionHDTV 5 Gold
[   13.264705] cx88[0]:    card=32 -> AverMedia UltraTV Media Center PCI 550
[   13.264707] cx88[0]:    card=33 -> Kworld V-Stream Xpert DVD
[   13.264709] cx88[0]:    card=34 -> ATI HDTV Wonder
[   13.264711] cx88[0]:    card=35 -> WinFast DTV1000-T
[   13.264713] cx88[0]:    card=36 -> AVerTV 303 (M126)
[   13.264715] cx88[0]:    card=37 -> Hauppauge Nova-S-Plus DVB-S
[   13.264717] cx88[0]:    card=38 -> Hauppauge Nova-SE2 DVB-S
[   13.264719] cx88[0]:    card=39 -> KWorld DVB-S 100
[   13.264721] cx88[0]:    card=40 -> Hauppauge WinTV-HVR1100 DVB-T/Hybrid
[   13.264724] cx88[0]:    card=41 -> Hauppauge WinTV-HVR1100 DVB-T/Hybrid (Low Profile)
[   13.264726] cx88[0]:    card=42 -> digitalnow DNTV Live! DVB-T Pro
[   13.264728] cx88[0]:    card=43 -> KWorld/VStream XPert DVB-T with cx22702
[   13.264730] cx88[0]:    card=44 -> DViCO FusionHDTV DVB-T Dual Digital
[   13.264732] cx88[0]:    card=45 -> KWorld HardwareMpegTV XPert
[   13.264735] cx88[0]:    card=46 -> DViCO FusionHDTV DVB-T Hybrid
[   13.264737] cx88[0]:    card=47 -> pcHDTV HD5500 HDTV
[   13.264739] cx88[0]:    card=48 -> Kworld MCE 200 Deluxe
[   13.264741] cx88[0]:    card=49 -> PixelView PlayTV P7000
[   13.264743] cx88[0]:    card=50 -> NPG Tech Real TV FM Top 10
[   13.264745] cx88[0]:    card=51 -> WinFast DTV2000 H ver. I (old)
[   13.264748] cx88[0]:    card=52 -> Geniatech DVB-S
[   13.264750] cx88[0]:    card=53 -> Hauppauge WinTV-HVR3000 TriMode Analog/DVB-S/DVB-T
[   13.264752] cx88[0]:    card=54 -> Norwood Micro TV Tuner
[   13.264754] cx88[0]:    card=55 -> Shenzhen Tungsten Ages Tech TE-DTV-250 / Swann OEM
[   13.264757] cx88[0]:    card=56 -> Hauppauge WinTV-HVR1300 DVB-T/Hybrid MPEG Encoder
[   13.264759] cx88[0]:    card=57 -> ADS Tech Instant Video PCI
[   13.264761] cx88[0]:    card=58 -> Pinnacle PCTV HD 800i
[   13.264763] cx88[0]:    card=59 -> DViCO FusionHDTV 5 PCI nano
[   13.264765] cx88[0]:    card=60 -> Pinnacle Hybrid PCTV
[   13.264768] cx88[0]:    card=61 -> Winfast TV2000 XP Global
[   13.264770] cx88[0]:    card=62 -> PowerColor RA330
[   13.264772] cx88[0]:    card=63 -> Geniatech X8000-MT DVBT
[   13.264774] cx88[0]:    card=64 -> DViCO FusionHDTV DVB-T PRO
[   13.264776] cx88[0]:    card=65 -> DViCO FusionHDTV 7 Gold
[   13.264778] cx88[0]:    card=66 -> Prolink Pixelview MPEG 8000GT
[   13.264780] cx88[0]:    card=67 -> Kworld PlusTV HD PCI 120 (ATSC 120)
[   13.264783] cx88[0]:    card=68 -> Hauppauge WinTV-HVR4000 DVB-S/S2/T/Hybrid
[   13.264785] cx88[0]:    card=69 -> Hauppauge WinTV-HVR4000(Lite) DVB-S/S2
[   13.264787] cx88[0]:    card=70 -> TeVii S460 DVB-S/S2
[   13.264789] cx88[0]:    card=71 -> Omicom SS4 DVB-S/S2 PCI
[   13.264792] cx88[0]:    card=72 -> TBS 8920 DVB-S/S2
[   13.264794] cx88[0]:    card=73 -> TeVii S420 DVB-S
[   13.264796] cx88[0]:    card=74 -> Prolink Pixelview Global Extreme
[   13.264798] cx88[0]:    card=75 -> PROF 7300 DVB-S/S2
[   13.264800] cx88[0]:    card=76 -> WinFast DTV2000 H ver. J (new)
[   13.264803] cx88[0]: subsystem: 1043:4820, board: UNKNOWN/GENERIC [card=0,autodetected], frontend(s): 0
[   13.264806] cx88[0]: TV tuner type -1, Radio tuner type -1
[   13.442865] All bytes are equal. It is not a TEA5767
[   13.442937] tuner' 0-0060: chip found @ 0xc0 (cx88[0])
[   13.491175] cx88[0]/0: found at 0000:04:03.0, rev: 3, irq: 19, latency: 64, mmio: 0xdb000000
[   13.491278] cx88[0]/0: registered device video0 [v4l2]
[   13.491335] cx88[0]/0: registered device vbi0
[   13.491349] tuner' 0-0060: tuner type not set
[   13.491430] rt61pci 0000:04:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   13.498800] phy0: Selected rate control algorithm 'pid'
[   13.527105] Registered led device: rt61pci-phy0:radio
[   13.527124] Registered led device: rt61pci-phy0:assoc
[   13.527197] CTALSA 0000:04:04.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   13.974312] lp: driver loaded but no devices found
[   14.101223] Adding 3020180k swap on /dev/sda5.  Priority:-1 extents:1 across:3020180k
[   14.637805] EXT3 FS on sda1, internal journal
[   15.585293] type=1505 audit(1241049946.481:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2087
[   15.632657] type=1505 audit(1241049946.529:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2091
[   15.632751] type=1505 audit(1241049946.529:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2091
[   15.632792] type=1505 audit(1241049946.529:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2091
[   15.632834] type=1505 audit(1241049946.529:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2091
[   15.764447] type=1505 audit(1241049946.661:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2096
[   15.764620] type=1505 audit(1241049946.661:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2096
[   15.792689] type=1505 audit(1241049946.689:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2100
[   20.533921] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   20.533924] Bluetooth: BNEP filters: protocol multicast
[   20.547963] Bridge firewalling registered
[   22.037038] ppdev: user-space parallel port driver
[   26.236280] e1000e 0000:00:19.0: irq 2299 for MSI/MSI-X
[   26.292328] e1000e 0000:00:19.0: irq 2299 for MSI/MSI-X
[   26.292668] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   26.293658] rt61pci 0000:04:05.0: firmware: requesting rt2561s.bin
[   26.409671] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   37.153274] cdrom: This disc doesn't have any tracks I recognize!
[   97.472409] wlan0: authenticate with AP 00:c0:49:ed:ce:94
[   97.473683] wlan0: authenticated
[   97.473687] wlan0: associate with AP 00:c0:49:ed:ce:94
[   97.475870] wlan0: RX AssocResp from 00:c0:49:ed:ce:94 (capab=0x471 status=0 aid=3)
[   97.475873] wlan0: associated
[   97.476579] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  108.196028] wlan0: no IPv6 routers present
[  580.683276] brasero[3847]: segfault at 1e0e7e11 ip b1e17668 sp b26c3060 error 4 in libgstriff-0.10.so.0.16.0[b1e11000+b000]
[  665.366853] brasero[3853]: segfault at ffffffff ip b7376bcb sp b4e65a00 error 4 in libglib-2.0.so.0.2000.1[b731e000+b6000]

```

---

### Post by Dragonbite on 2009-04-30
I was hoping that there would be some telling message at the end of the dmesg output but I don't understand the last 2 lines.

---

### Post by Arthur Millar on 2009-06-06
segfault means segmentation fault thats all i know its somthing to do with memory allocation 
im trying to burn "mythbuntu-9.04-desktop-i386.iso" 
and every time its about to start burning the machine reboots 
i suspect its a segfault after reading this thread

---

### Post by mikechant on 2009-06-08
Deleted. Re-read problem and my comment turned out to not be useful.

---

### Post by abhiroopb on 2009-06-08
I have been having problems with brasero for some time now.

my older thread;
[http://ubuntuforums.org/showthread.php?t=1135957](http://ubuntuforums.org/showthread.php?t=1135957)

---

