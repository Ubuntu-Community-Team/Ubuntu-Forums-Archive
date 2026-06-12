---
title: "Weird CD Burning Problem"
date: 2009-06-09
forum: New to Ubuntu
---

### Post by gfunkera on 2009-06-09
i used intrepid ibex and brasero to burn CDs, they worked because the software didnt crash... i switched to jaunty and whenever i open either brasero or gnomebaker, they crash shortly after opening them.. 

at the very begining i thought it was because when this problem started occuring, i was attempting to burn mp3s that were converted from flv files... then i started thinking maybe brasero stopped working after i upgraded to jaunty (because all of the successfully burned audio CDs were done on itrepid ibex).. i downloaded gnomebaker and now the same thing is happening with it.. im not really sure what is really going on but its really annoying..

anyone know how to fix this?

---

### Post by gfunkera on 2009-06-09
heres the dmesg... kinda long!

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
[    0.000000] RAMDISK: 378be000 - 37fefa13
[    0.000000] Allocated new RAMDISK: 00881000 - 00fb2a13
[    0.000000] Move RAMDISK from 00000000378be000 - 0000000037fefa12 to 00881000 - 00fb2a12
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
[    0.000000]   #7 [0000881000 - 0000fb2a13]      NEW RAMDISK ==> [0000881000 - 0000fb2a13]
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
[    0.000000] TSC: PIT calibration matches PMTIMER. 1 loops
[    0.000000] Detected 1862.032 MHz processor.
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
[    0.004000] Calibrating delay loop (skipped), value calculated using timer frequency.. 3724.06 BogoMIPS (lpj=7448128)
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
[    0.018512] ACPI: Core revision 20080926
[    0.072701] ACPI: Checking initramfs for custom DSDT
[    0.480394] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.520298] CPU0: Intel(R) Core(TM)2 CPU          6300  @ 1.86GHz stepping 02
[    0.524002] Booting processor 1 APIC 0x1 ip 0x6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 3724.00 BogoMIPS (lpj=7448018)
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 2048K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.612478] CPU1: Intel(R) Core(TM)2 CPU          6300  @ 1.86GHz stepping 02
[    0.612493] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.616035] Brought up 2 CPUs
[    0.616038] Total of 2 processors activated (7448.07 BogoMIPS).
[    0.616086] CPU0 attaching sched-domain:
[    0.616089]  domain 0: span 0-1 level MC
[    0.616091]   groups: 0 1
[    0.616098] CPU1 attaching sched-domain:
[    0.616100]  domain 0: span 0-1 level MC
[    0.616102]   groups: 1 0
[    0.616172] net_namespace: 776 bytes
[    0.616172] Dell Dimension 9200 series board detected. Selecting BIOS-method for reboots.
[    0.616172] Booting paravirtualized kernel on bare hardware
[    0.616339] Time: 17:33:27  Date: 05/30/09
[    0.616339] regulator: core version 0.5
[    0.616339] NET: Registered protocol family 16
[    0.616339] EISA bus registered
[    0.616339] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.616339] ACPI: bus type pci registered
[    0.616339] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.616339] PCI: MCFG area at e0000000 reserved in E820
[    0.616339] PCI: Using MMCONFIG for extended config space
[    0.616339] PCI: Using configuration type 1 for base access
[    0.617230] ACPI: EC: Look up EC in DSDT
[    0.662910] ACPI: BIOS _OSI(Linux) query ignored
[    0.684247] ACPI: Interpreter enabled
[    0.684254] ACPI: (supports S0 S3 S4 S5)
[    0.684272] ACPI: Using IOAPIC for interrupt routing
[    0.767820] ACPI: No dock devices found.
[    0.767832] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.767923] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.767927] pci 0000:00:01.0: PME# disabled
[    0.767985] pci 0000:00:19.0: reg 10 32bit mmio: [0xdffe0000-0xdfffffff]
[    0.768004] pci 0000:00:19.0: reg 14 32bit mmio: [0xdffdf000-0xdffdffff]
[    0.768011] pci 0000:00:19.0: reg 18 io port: [0xecc0-0xecdf]
[    0.768036] pci 0000:00:19.0: PME# supported from D0 D3hot D3cold
[    0.768039] pci 0000:00:19.0: PME# disabled
[    0.768078] pci 0000:00:1a.0: reg 20 io port: [0xff20-0xff3f]
[    0.768123] pci 0000:00:1a.1: reg 20 io port: [0xff00-0xff1f]
[    0.768176] pci 0000:00:1a.7: reg 10 32bit mmio: [0xdffdec00-0xdffdefff]
[    0.768213] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.768218] pci 0000:00:1a.7: PME# disabled
[    0.768263] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.768266] pci 0000:00:1c.0: PME# disabled
[    0.768316] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.768319] pci 0000:00:1c.4: PME# disabled
[    0.768364] pci 0000:00:1d.0: reg 20 io port: [0xff80-0xff9f]
[    0.768409] pci 0000:00:1d.1: reg 20 io port: [0xff60-0xff7f]
[    0.768455] pci 0000:00:1d.2: reg 20 io port: [0xff40-0xff5f]
[    0.768506] pci 0000:00:1d.7: reg 10 32bit mmio: [0xff980800-0xff980bff]
[    0.768544] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.768548] pci 0000:00:1d.7: PME# disabled
[    0.768658] pci 0000:00:1f.0: quirk: region 0800-087f claimed by ICH6 ACPI/GPIO/TCO
[    0.768662] pci 0000:00:1f.0: quirk: region 0880-08bf claimed by ICH6 GPIO
[    0.768708] pci 0000:00:1f.2: reg 10 io port: [0xfe00-0xfe07]
[    0.768713] pci 0000:00:1f.2: reg 14 io port: [0xfe10-0xfe13]
[    0.768719] pci 0000:00:1f.2: reg 18 io port: [0xfe20-0xfe27]
[    0.768725] pci 0000:00:1f.2: reg 1c io port: [0xfe30-0xfe33]
[    0.768731] pci 0000:00:1f.2: reg 20 io port: [0xfec0-0xfedf]
[    0.768737] pci 0000:00:1f.2: reg 24 32bit mmio: [0xff970000-0xff9707ff]
[    0.768751] pci 0000:00:1f.2: PME# supported from D3hot
[    0.768754] pci 0000:00:1f.2: PME# disabled
[    0.768776] pci 0000:00:1f.3: reg 10 32bit mmio: [0xdffdeb00-0xdffdebff]
[    0.768794] pci 0000:00:1f.3: reg 20 io port: [0xece0-0xecff]
[    0.768837] pci 0000:01:00.0: reg 10 32bit mmio: [0xdd000000-0xddffffff]
[    0.768846] pci 0000:01:00.0: reg 14 64bit mmio: [0xc0000000-0xcfffffff]
[    0.768855] pci 0000:01:00.0: reg 1c 64bit mmio: [0xde000000-0xdeffffff]
[    0.768864] pci 0000:01:00.0: reg 30 32bit mmio: [0xdfe00000-0xdfe1ffff]
[    0.768912] pci 0000:00:01.0: bridge 32bit mmio: [0xdd000000-0xdfefffff]
[    0.768917] pci 0000:00:01.0: bridge 64bit mmio pref: [0xc0000000-0xcfffffff]
[    0.768961] pci 0000:00:1c.0: bridge 32bit mmio: [0xdcf00000-0xdcffffff]
[    0.769050] pci 0000:04:03.0: reg 10 32bit mmio: [0xdb000000-0xdbffffff]
[    0.769135] pci 0000:04:04.0: reg 10 io port: [0xdce0-0xdcff]
[    0.769147] pci 0000:04:04.0: reg 14 64bit mmio: [0xdcc00000-0xdcdfffff]
[    0.769159] pci 0000:04:04.0: reg 1c 64bit mmio: [0xd4000000-0xd7ffffff]
[    0.769178] pci 0000:04:04.0: supports D1 D2
[    0.769214] pci 0000:04:05.0: reg 10 32bit mmio: [0xdcef8000-0xdcefffff]
[    0.769290] pci 0000:00:1e.0: transparent bridge
[    0.769294] pci 0000:00:1e.0: bridge io port: [0xd000-0xdfff]
[    0.769298] pci 0000:00:1e.0: bridge 32bit mmio: [0xd4000000-0xdcefffff]
[    0.769320] bus 00 -> node 0
[    0.769326] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.770157] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI4._PRT]
[    0.770822] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI2._PRT]
[    0.771332] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[    0.771850] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI5._PRT]
[    1.668628] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 15)
[    1.669400] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *9 10 11 12 15)
[    1.670181] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 7 9 10 11 12 15)
[    1.670957] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 9 10 11 12 15)
[    1.671742] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 *10 11 12 15)
[    1.672517] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 *10 11 12 15)
[    1.673291] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 *5 6 7 9 10 11 12 15)
[    1.674075] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 *4 5 6 7 9 10 11 12 15)
[    1.674501] ACPI: WMI: Mapper loaded
[    1.674539] SCSI subsystem initialized
[    1.674539] libata version 3.00 loaded.
[    1.674539] usbcore: registered new interface driver usbfs
[    1.674539] usbcore: registered new interface driver hub
[    1.674539] usbcore: registered new device driver usb
[    1.674539] PCI: Using ACPI for IRQ routing
[    1.680013] Bluetooth: Core ver 2.13
[    1.680031] NET: Registered protocol family 31
[    1.680031] Bluetooth: HCI device and connection manager initialized
[    1.680031] Bluetooth: HCI socket layer initialized
[    1.680031] NET: Registered protocol family 8
[    1.680031] NET: Registered protocol family 20
[    1.680043] NetLabel: Initializing
[    1.680046] NetLabel:  domain hash size = 128
[    1.680048] NetLabel:  protocols = UNLABELED CIPSOv4
[    1.680062] NetLabel:  unlabeled traffic allowed by default
[    1.680077] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    1.680083] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    1.684068] AppArmor: AppArmor Filesystem Enabled
[    1.688014] Switched to high resolution mode on CPU 0
[    1.688549] Switched to high resolution mode on CPU 1
[    1.692053] pnp: PnP ACPI init
[    1.692062] ACPI: bus type pnp registered
[    1.702493] pnp 00:01: io resource (0x800-0x85f) overlaps 0000:00:1f.0 BAR 7 (0x800-0x87f), disabling
[    1.702497] pnp 00:01: io resource (0x860-0x8ff) overlaps 0000:00:1f.0 BAR 7 (0x800-0x87f), disabling
[    1.736393] pnp: PnP ACPI: found 9 devices
[    1.736396] ACPI: ACPI bus type pnp unregistered
[    1.736400] PnPBIOS: Disabled by ACPI PNP
[    1.736410] system 00:01: ioport range 0xc00-0xc7f has been reserved
[    1.736419] system 00:06: iomem range 0x0-0x9ffff could not be reserved
[    1.736421] system 00:06: iomem range 0x100000-0xffffff could not be reserved
[    1.736424] system 00:06: iomem range 0x1000000-0x3fe53bff could not be reserved
[    1.736427] system 00:06: iomem range 0xf0000-0xfffff could not be reserved
[    1.736430] system 00:06: iomem range 0xc0000-0xd7fff could not be reserved
[    1.736433] system 00:06: iomem range 0xfec00000-0xfecfffff has been reserved
[    1.736436] system 00:06: iomem range 0xfee00000-0xfeefffff has been reserved
[    1.736439] system 00:06: iomem range 0xffb00000-0xffbfffff has been reserved
[    1.736441] system 00:06: iomem range 0xffc00000-0xffffffff has been reserved
[    1.736447] system 00:07: ioport range 0x100-0x1fe has been reserved
[    1.736450] system 00:07: ioport range 0x200-0x277 has been reserved
[    1.736453] system 00:07: ioport range 0x280-0x2e7 has been reserved
[    1.736456] system 00:07: ioport range 0x2e8-0x2ef has been reserved
[    1.736458] system 00:07: ioport range 0x2f0-0x2f7 has been reserved
[    1.736461] system 00:07: ioport range 0x2f8-0x2ff has been reserved
[    1.736463] system 00:07: ioport range 0x300-0x377 has been reserved
[    1.736466] system 00:07: ioport range 0x380-0x3bb has been reserved
[    1.736468] system 00:07: ioport range 0x3c0-0x3e7 could not be reserved
[    1.736471] system 00:07: ioport range 0x3f6-0x3f7 has been reserved
[    1.736474] system 00:07: ioport range 0x400-0x4cf has been reserved
[    1.736476] system 00:07: ioport range 0x4d2-0x57f has been reserved
[    1.736479] system 00:07: ioport range 0x580-0x677 has been reserved
[    1.736481] system 00:07: ioport range 0x680-0x777 has been reserved
[    1.736484] system 00:07: ioport range 0x780-0x7bb has been reserved
[    1.736486] system 00:07: ioport range 0x7c0-0x7ff has been reserved
[    1.736489] system 00:07: ioport range 0x8e0-0x8ff has been reserved
[    1.736492] system 00:07: ioport range 0x900-0x9fe has been reserved
[    1.736494] system 00:07: ioport range 0xa00-0xafe has been reserved
[    1.736497] system 00:07: ioport range 0xb00-0xbfe has been reserved
[    1.736500] system 00:07: ioport range 0xc80-0xcaf has been reserved
[    1.736502] system 00:07: ioport range 0xcb0-0xcbf has been reserved
[    1.736505] system 00:07: ioport range 0xcc0-0xcf7 has been reserved
[    1.736507] system 00:07: ioport range 0xd00-0xdfe has been reserved
[    1.736510] system 00:07: ioport range 0xe00-0xefe has been reserved
[    1.736512] system 00:07: ioport range 0xf00-0xffe has been reserved
[    1.736517] system 00:07: ioport range 0x2000-0x20fe has been reserved
[    1.736520] system 00:07: ioport range 0x2100-0x21fe has been reserved
[    1.736523] system 00:07: ioport range 0x2200-0x22fe has been reserved
[    1.736525] system 00:07: ioport range 0x2300-0x23fe has been reserved
[    1.736528] system 00:07: ioport range 0x2400-0x24fe has been reserved
[    1.736531] system 00:07: ioport range 0x2500-0x25fe has been reserved
[    1.736533] system 00:07: ioport range 0x2600-0x26fe has been reserved
[    1.736536] system 00:07: ioport range 0x2700-0x27fe has been reserved
[    1.736539] system 00:07: ioport range 0x2800-0x28fe has been reserved
[    1.736542] system 00:07: ioport range 0x2900-0x29fe has been reserved
[    1.736544] system 00:07: ioport range 0x2a00-0x2afe has been reserved
[    1.736547] system 00:07: ioport range 0x2b00-0x2bfe has been reserved
[    1.736550] system 00:07: ioport range 0x2c00-0x2cfe has been reserved
[    1.736552] system 00:07: ioport range 0x2d00-0x2dfe has been reserved
[    1.736555] system 00:07: ioport range 0x2e00-0x2efe has been reserved
[    1.736558] system 00:07: ioport range 0x2f00-0x2ffe has been reserved
[    1.736561] system 00:07: ioport range 0x5000-0x50fe has been reserved
[    1.736564] system 00:07: ioport range 0x5100-0x51fe has been reserved
[    1.736566] system 00:07: ioport range 0x5200-0x52fe has been reserved
[    1.736569] system 00:07: ioport range 0x5300-0x53fe has been reserved
[    1.736572] system 00:07: ioport range 0x5400-0x54fe has been reserved
[    1.736574] system 00:07: ioport range 0x5500-0x55fe has been reserved
[    1.736577] system 00:07: ioport range 0x5600-0x56fe has been reserved
[    1.736580] system 00:07: ioport range 0x5700-0x57fe has been reserved
[    1.736583] system 00:07: ioport range 0x5800-0x58fe has been reserved
[    1.736586] system 00:07: ioport range 0x5900-0x59fe has been reserved
[    1.736589] system 00:07: ioport range 0x5a00-0x5afe has been reserved
[    1.736591] system 00:07: ioport range 0x5b00-0x5bfe has been reserved
[    1.736594] system 00:07: ioport range 0x5c00-0x5cfe has been reserved
[    1.736597] system 00:07: ioport range 0x5d00-0x5dfe has been reserved
[    1.736600] system 00:07: ioport range 0x5e00-0x5efe has been reserved
[    1.736603] system 00:07: ioport range 0x5f00-0x5ffe has been reserved
[    1.736606] system 00:07: ioport range 0x6000-0x60fe has been reserved
[    1.736608] system 00:07: ioport range 0x6100-0x61fe has been reserved
[    1.736611] system 00:07: ioport range 0x6200-0x62fe has been reserved
[    1.736614] system 00:07: ioport range 0x6300-0x63fe has been reserved
[    1.736617] system 00:07: ioport range 0x6400-0x64fe has been reserved
[    1.736620] system 00:07: ioport range 0x6500-0x65fe has been reserved
[    1.736623] system 00:07: ioport range 0x6600-0x66fe has been reserved
[    1.736625] system 00:07: ioport range 0x6700-0x67fe has been reserved
[    1.736628] system 00:07: ioport range 0x6800-0x68fe has been reserved
[    1.736631] system 00:07: ioport range 0x6900-0x69fe has been reserved
[    1.736634] system 00:07: ioport range 0x6a00-0x6afe has been reserved
[    1.736637] system 00:07: ioport range 0x6b00-0x6bfe has been reserved
[    1.736640] system 00:07: ioport range 0x6c00-0x6cfe has been reserved
[    1.736643] system 00:07: ioport range 0x6d00-0x6dfe has been reserved
[    1.736646] system 00:07: ioport range 0x6e00-0x6efe has been reserved
[    1.736648] system 00:07: ioport range 0x6f00-0x6ffe has been reserved
[    1.736651] system 00:07: ioport range 0xa000-0xa0fe has been reserved
[    1.736654] system 00:07: ioport range 0xa100-0xa1fe has been reserved
[    1.736657] system 00:07: ioport range 0xa200-0xa2fe has been reserved
[    1.736660] system 00:07: ioport range 0xa300-0xa3fe has been reserved
[    1.736663] system 00:07: ioport range 0xa400-0xa4fe has been reserved
[    1.736666] system 00:07: ioport range 0xa500-0xa5fe has been reserved
[    1.736669] system 00:07: ioport range 0xa600-0xa6fe has been reserved
[    1.736671] system 00:07: ioport range 0xa700-0xa7fe has been reserved
[    1.736674] system 00:07: ioport range 0xa800-0xa8fe has been reserved
[    1.736677] system 00:07: ioport range 0xa900-0xa9fe has been reserved
[    1.736680] system 00:07: ioport range 0xaa00-0xaafe has been reserved
[    1.736683] system 00:07: ioport range 0xab00-0xabfe has been reserved
[    1.736686] system 00:07: ioport range 0xac00-0xacfe has been reserved
[    1.736689] system 00:07: ioport range 0xad00-0xadfe has been reserved
[    1.736692] system 00:07: ioport range 0xae00-0xaefe has been reserved
[    1.736695] system 00:07: ioport range 0xaf00-0xaffe has been reserved
[    1.736698] system 00:07: iomem range 0xe0000000-0xefffffff has been reserved
[    1.736701] system 00:07: iomem range 0xfeda0000-0xfedacfff has been reserved
[    1.771395] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    1.771397] pci 0000:00:01.0:   IO window: disabled
[    1.771401] pci 0000:00:01.0:   MEM window: 0xdd000000-0xdfefffff
[    1.771405] pci 0000:00:01.0:   PREFETCH window: 0x000000c0000000-0x000000cfffffff
[    1.771409] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
[    1.771411] pci 0000:00:1c.0:   IO window: disabled
[    1.771416] pci 0000:00:1c.0:   MEM window: 0xdcf00000-0xdcffffff
[    1.771420] pci 0000:00:1c.0:   PREFETCH window: disabled
[    1.771426] pci 0000:00:1c.4: PCI bridge, secondary bus 0000:03
[    1.771428] pci 0000:00:1c.4:   IO window: disabled
[    1.771432] pci 0000:00:1c.4:   MEM window: disabled
[    1.771436] pci 0000:00:1c.4:   PREFETCH window: disabled
[    1.771442] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:04
[    1.771445] pci 0000:00:1e.0:   IO window: 0xd000-0xdfff
[    1.771450] pci 0000:00:1e.0:   MEM window: 0xd4000000-0xdcefffff
[    1.771454] pci 0000:00:1e.0:   PREFETCH window: disabled
[    1.771466] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.771470] pci 0000:00:01.0: setting latency timer to 64
[    1.771477] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.771481] pci 0000:00:1c.0: setting latency timer to 64
[    1.771488] pci 0000:00:1c.4: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.771492] pci 0000:00:1c.4: setting latency timer to 64
[    1.771498] pci 0000:00:1e.0: setting latency timer to 64
[    1.771501] bus: 00 index 0 io port: [0x00-0xffff]
[    1.771504] bus: 00 index 1 mmio: [0x000000-0xffffffff]
[    1.771506] bus: 01 index 0 mmio: [0x0-0x0]
[    1.771508] bus: 01 index 1 mmio: [0xdd000000-0xdfefffff]
[    1.771510] bus: 01 index 2 mmio: [0xc0000000-0xcfffffff]
[    1.771512] bus: 01 index 3 mmio: [0x0-0x0]
[    1.771514] bus: 02 index 0 mmio: [0x0-0x0]
[    1.771516] bus: 02 index 1 mmio: [0xdcf00000-0xdcffffff]
[    1.771518] bus: 02 index 2 mmio: [0x0-0x0]
[    1.771520] bus: 02 index 3 mmio: [0x0-0x0]
[    1.771522] bus: 03 index 0 mmio: [0x0-0x0]
[    1.771523] bus: 03 index 1 mmio: [0x0-0x0]
[    1.771525] bus: 03 index 2 mmio: [0x0-0x0]
[    1.771527] bus: 03 index 3 mmio: [0x0-0x0]
[    1.771529] bus: 04 index 0 io port: [0xd000-0xdfff]
[    1.771531] bus: 04 index 1 mmio: [0xd4000000-0xdcefffff]
[    1.771533] bus: 04 index 2 mmio: [0x0-0x0]
[    1.771535] bus: 04 index 3 io port: [0x00-0xffff]
[    1.771537] bus: 04 index 4 mmio: [0x000000-0xffffffff]
[    1.771545] NET: Registered protocol family 2
[    1.784090] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    1.784360] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    1.784670] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    1.784851] TCP: Hash tables configured (established 131072 bind 65536)
[    1.784853] TCP reno registered
[    1.792132] NET: Registered protocol family 1
[    1.792274] checking if image is initramfs... it is
[    2.433949] Freeing initrd memory: 7366k freed
[    2.433991] Simple Boot Flag at 0x7a set to 0x1
[    2.434173] cpufreq: No nForce2 chipset.
[    2.434316] audit: initializing netlink socket (disabled)
[    2.434339] type=2000 audit(1243704808.432:1): initialized
[    2.441809] highmem bounce pool size: 64 pages
[    2.441814] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    2.443218] VFS: Disk quotas dquot_6.5.1
[    2.443286] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    2.443910] fuse init (API version 7.10)
[    2.443996] msgmni has been set to 1723
[    2.444180] alg: No test for stdrng (krng)
[    2.444191] io scheduler noop registered
[    2.444194] io scheduler anticipatory registered
[    2.444196] io scheduler deadline registered
[    2.444209] io scheduler cfq registered (default)
[    2.444350] pci 0000:01:00.0: Boot video device
[    2.501296] pcieport-driver 0000:00:01.0: setting latency timer to 64
[    2.501331] pcieport-driver 0000:00:01.0: found MSI capability
[    2.501354] pcieport-driver 0000:00:01.0: irq 2303 for MSI/MSI-X
[    2.501363] pci_express 0000:00:01.0:pcie00: allocate port service
[    2.501378] pci_express 0000:00:01.0:pcie03: allocate port service
[    2.501426] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    2.501459] pcieport-driver 0000:00:1c.0: found MSI capability
[    2.501481] pcieport-driver 0000:00:1c.0: irq 2302 for MSI/MSI-X
[    2.501492] pci_express 0000:00:1c.0:pcie00: allocate port service
[    2.501506] pci_express 0000:00:1c.0:pcie02: allocate port service
[    2.501519] pci_express 0000:00:1c.0:pcie03: allocate port service
[    2.501572] pcieport-driver 0000:00:1c.4: setting latency timer to 64
[    2.501605] pcieport-driver 0000:00:1c.4: found MSI capability
[    2.501627] pcieport-driver 0000:00:1c.4: irq 2301 for MSI/MSI-X
[    2.501639] pci_express 0000:00:1c.4:pcie00: allocate port service
[    2.501652] pci_express 0000:00:1c.4:pcie02: allocate port service
[    2.501667] pci_express 0000:00:1c.4:pcie03: allocate port service
[    2.501733] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    2.525450] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    2.525580] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    2.525583] ACPI: Power Button (FF) [PWRF]
[    2.525631] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    2.525639] ACPI: Power Button (CM) [VBTN]
[    2.526382] processor ACPI_CPU:00: registered as cooling_device0
[    2.526418] processor ACPI_CPU:01: registered as cooling_device1
[    2.626069] isapnp: Scanning for PnP cards...
[    2.978858] isapnp: No Plug & Play device found
[    2.984624] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    2.985694] brd: module loaded
[    2.986046] loop: module loaded
[    2.986110] Fixed MDIO Bus: probed
[    2.986115] PPP generic driver version 2.4.2
[    2.986173] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    2.986202] Driver 'sd' needs updating - please use bus_type methods
[    2.986212] Driver 'sr' needs updating - please use bus_type methods
[    2.986253] ahci 0000:00:1f.2: version 3.0
[    2.986265] ahci 0000:00:1f.2: PCI INT C -> GSI 20 (level, low) -> IRQ 20
[    2.986297] ahci 0000:00:1f.2: irq 2300 for MSI/MSI-X
[    2.986380] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 6 ports 3 Gbps 0x3f impl RAID mode
[    2.986384] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part ems 
[    2.986388] ahci 0000:00:1f.2: setting latency timer to 64
[    2.986838] scsi0 : ahci
[    2.986932] scsi1 : ahci
[    2.986997] scsi2 : ahci
[    2.987056] scsi3 : ahci
[    2.987123] scsi4 : ahci
[    2.987184] scsi5 : ahci
[    2.987222] ata1: SATA max UDMA/133 abar m2048@0xff970000 port 0xff970100 irq 2300
[    2.987225] ata2: SATA max UDMA/133 abar m2048@0xff970000 port 0xff970180 irq 2300
[    2.987228] ata3: SATA max UDMA/133 abar m2048@0xff970000 port 0xff970200 irq 2300
[    2.987231] ata4: SATA max UDMA/133 abar m2048@0xff970000 port 0xff970280 irq 2300
[    2.987233] ata5: SATA max UDMA/133 abar m2048@0xff970000 port 0xff970300 irq 2300
[    2.987236] ata6: SATA max UDMA/133 abar m2048@0xff970000 port 0xff970380 irq 2300
[    3.304035] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    3.339345] ata1.00: ATA-7: ST3250820AS, 3.ADG, max UDMA/133
[    3.339349] ata1.00: 488281250 sectors, multi 0: LBA48 NCQ (depth 31/32)
[    3.397670] ata1.00: configured for UDMA/133
[    4.136032] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    4.138682] ata2.00: ATAPI: TSSTcorp DVD+/-RW TS-H653A, D400, max UDMA/33
[    4.138702] ata2.00: applying bridge limits
[    4.144631] ata2.00: configured for UDMA/33
[    4.480033] ata3: SATA link down (SStatus 0 SControl 300)
[    4.816033] ata4: SATA link down (SStatus 0 SControl 300)
[    5.152033] ata5: SATA link down (SStatus 0 SControl 300)
[    5.488033] ata6: SATA link down (SStatus 0 SControl 300)
[    5.504394] scsi 0:0:0:0: Direct-Access     ATA      ST3250820AS      3.AD PQ: 0 ANSI: 5
[    5.504506] sd 0:0:0:0: [sda] 488281250 512-byte hardware sectors: (250 GB/232 GiB)
[    5.504526] sd 0:0:0:0: [sda] Write Protect is off
[    5.504528] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.504560] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.504634] sd 0:0:0:0: [sda] 488281250 512-byte hardware sectors: (250 GB/232 GiB)
[    5.504652] sd 0:0:0:0: [sda] Write Protect is off
[    5.504655] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.504686] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.504690]  sda: sda1 sda2 < sda5 >
[    5.537302] sd 0:0:0:0: [sda] Attached SCSI disk
[    5.537348] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    5.537739] scsi 1:0:0:0: CD-ROM            TSSTcorp DVD+-RW TS-H653A D400 PQ: 0 ANSI: 5
[    5.539947] sr0: scsi3-mmc drive: 62x/62x writer cd/rw xa/form2 cdda tray
[    5.539950] Uniform CD-ROM driver Revision: 3.20
[    5.540061] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    5.540105] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    5.540836] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    5.540855] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    5.540871] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    5.540875] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    5.540938] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    5.544851] ehci_hcd 0000:00:1a.7: debug port 1
[    5.544856] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    5.544870] ehci_hcd 0000:00:1a.7: irq 22, io mem 0xdffdec00
[    5.560041] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    5.560125] usb usb1: configuration #1 chosen from 1 choice
[    5.560158] hub 1-0:1.0: USB hub found
[    5.560166] hub 1-0:1.0: 4 ports detected
[    5.560290] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    5.560300] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    5.560304] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    5.560348] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    5.564260] ehci_hcd 0000:00:1d.7: debug port 1
[    5.564266] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    5.564278] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xff980800
[    5.580019] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    5.580089] usb usb2: configuration #1 chosen from 1 choice
[    5.580119] hub 2-0:1.0: USB hub found
[    5.580127] hub 2-0:1.0: 6 ports detected
[    5.580244] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    5.580261] uhci_hcd: USB Universal Host Controller Interface driver
[    5.580281] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    5.580289] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    5.580293] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    5.580334] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    5.580362] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000ff20
[    5.580436] usb usb3: configuration #1 chosen from 1 choice
[    5.580462] hub 3-0:1.0: USB hub found
[    5.580469] hub 3-0:1.0: 2 ports detected
[    5.580549] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    5.580555] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    5.580558] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    5.580602] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    5.580629] uhci_hcd 0000:00:1a.1: irq 17, io base 0x0000ff00
[    5.580701] usb usb4: configuration #1 chosen from 1 choice
[    5.580726] hub 4-0:1.0: USB hub found
[    5.580733] hub 4-0:1.0: 2 ports detected
[    5.580816] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    5.580822] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    5.580825] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    5.580867] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    5.580888] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000ff80
[    5.580961] usb usb5: configuration #1 chosen from 1 choice
[    5.580986] hub 5-0:1.0: USB hub found
[    5.580993] hub 5-0:1.0: 2 ports detected
[    5.581076] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    5.581082] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    5.581085] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    5.581139] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    5.581160] uhci_hcd 0000:00:1d.1: irq 17, io base 0x0000ff60
[    5.581233] usb usb6: configuration #1 chosen from 1 choice
[    5.581258] hub 6-0:1.0: USB hub found
[    5.581265] hub 6-0:1.0: 2 ports detected
[    5.581345] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    5.581351] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    5.581355] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    5.581399] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    5.581427] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000ff40
[    5.581498] usb usb7: configuration #1 chosen from 1 choice
[    5.581523] hub 7-0:1.0: USB hub found
[    5.581530] hub 7-0:1.0: 2 ports detected
[    5.581657] usbcore: registered new interface driver libusual
[    5.581689] usbcore: registered new interface driver usbserial
[    5.581701] USB Serial support registered for generic
[    5.581721] usbcore: registered new interface driver usbserial_generic
[    5.581723] usbserial: USB Serial Driver core
[    5.581773] PNP: No PS/2 controller found. Probing ports directly.
[    5.584321] serio: i8042 KBD port at 0x60,0x64 irq 1
[    5.584327] serio: i8042 AUX port at 0x60,0x64 irq 12
[    5.588060] mice: PS/2 mouse device common for all mice
[    5.600104] rtc_cmos 00:05: RTC can wake from S4
[    5.600142] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    5.600166] rtc0: alarms up to one day, 242 bytes nvram, hpet irqs
[    5.600246] device-mapper: uevent: version 1.0.3
[    5.600337] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
[    5.600413] device-mapper: multipath: version 1.0.5 loaded
[    5.600415] device-mapper: multipath round-robin: version 1.0.0 loaded
[    5.600494] EISA: Probing bus 0 at eisa.0
[    5.600497] EISA: Cannot allocate resource for mainboard
[    5.600504] Cannot allocate resource for EISA slot 2
[    5.600513] Cannot allocate resource for EISA slot 5
[    5.600515] Cannot allocate resource for EISA slot 6
[    5.600525] EISA: Detected 0 cards.
[    5.600576] cpuidle: using governor ladder
[    5.600578] cpuidle: using governor menu
[    5.601116] TCP cubic registered
[    5.601213] NET: Registered protocol family 10
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
[    5.602226] registered taskstats version 1
[    5.602366]   Magic number: 9:82:594
[    5.602424] rtc_cmos 00:05: setting system clock to 2009-05-30 17:33:32 UTC (1243704812)
[    5.602427] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    5.602429] EDD information not available.
[    5.602713] Freeing unused kernel memory: 532k freed
[    5.602843] Write protecting the kernel text: 4128k
[    5.602890] Write protecting the kernel read-only data: 1532k
[    5.777187] e1000e: Intel(R) PRO/1000 Network Driver - 0.3.3.3-k6
[    5.777190] e1000e: Copyright (c) 1999-2008 Intel Corporation.
[    5.777240] e1000e 0000:00:19.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    5.777249] e1000e 0000:00:19.0: setting latency timer to 64
[    5.777362] e1000e 0000:00:19.0: irq 2299 for MSI/MSI-X
[    5.987089] 0000:00:19.0: eth0: (PCI Express:2.5GB/s:Width x1) 00:19:d1:5e:f3:a0
[    5.987093] 0000:00:19.0: eth0: Intel(R) PRO/1000 Network Connection
[    5.987117] 0000:00:19.0: eth0: MAC: 5, PHY: 6, PBA No: 1021ff-0ff
[    6.128055] usb 4-1: new low speed USB device using uhci_hcd and address 2
[    6.244807] PM: Starting manual resume from disk
[    6.244811] PM: Resume from partition 8:5
[    6.244812] PM: Checking hibernation image.
[    6.244914] PM: Resume from disk failed.
[    6.277638] kjournald starting.  Commit interval 5 seconds
[    6.277658] EXT3-fs: mounted filesystem with ordered data mode.
[    6.303727] usb 4-1: configuration #1 chosen from 1 choice
[    6.544031] usb 6-1: new low speed USB device using uhci_hcd and address 2
[    6.728251] usb 6-1: configuration #1 chosen from 1 choice
[   11.656448] udev: starting version 141
[   11.836752] Linux agpgart interface v0.103
[   11.929807] usbcore: registered new interface driver hiddev
[   11.942866] input: Logitech Optical USB Mouse as /devices/pci0000:00/0000:00:1a.1/usb4/4-1/4-1:1.0/input/input3
[   11.945307] generic-usb 0003:046D:C016.0001: input,hidraw0: USB HID v1.10 Mouse [Logitech Optical USB Mouse] on usb-0000:00:1a.1-1/input0
[   11.945569] usbcore: registered new interface driver usbhid
[   11.945592] usbhid: v2.6:USB HID core driver
[   12.561389] nvidia: module license 'NVIDIA' taints kernel.
[   12.814458] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   12.814466] nvidia 0000:01:00.0: setting latency timer to 64
[   12.815525] NVRM: loading NVIDIA UNIX x86 Kernel Module  180.44  Mon Mar 23 14:59:10 PST 2009
[   12.824904] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   12.862034] input: PC Speaker as /devices/platform/pcspkr/input/input4
[   12.896361] iTCO_vendor_support: vendor-support=0
[   12.919321] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05
[   12.919448] iTCO_wdt: failed to reset NO_REBOOT flag, reboot disabled by hardware
[   12.919459] iTCO_wdt: No card detected
[   13.124440] input: Microsoft Microsoft Wireless Optical Desktop&#65533; 2.10 as /devices/pci0000:00/0000:00:1d.1/usb6/6-1/6-1:1.0/input/input5
[   13.132313] cfg80211: Calling CRDA to update world regulatory domain
[   13.132616] microsoft 0003:045E:009D.0002: input,hidraw1: USB HID v1.11 Keyboard [Microsoft Microsoft Wireless Optical Desktop&#65533; 2.10] on usb-0000:00:1d.1-1/input0
[   13.254290] Linux video capture interface: v2.00
[   13.255356] cfg80211: World regulatory domain updated:
[   13.255360]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   13.255362]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.255365]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   13.255367]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   13.255370]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.255372]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.266351] input: Microsoft Microsoft Wireless Optical Desktop&#65533; 2.10 as /devices/pci0000:00/0000:00:1d.1/usb6/6-1/6-1:1.1/input/input6
[   13.276449] microsoft 0003:045E:009D.0003: input,hidraw2: USB HID v1.11 Mouse [Microsoft Microsoft Wireless Optical Desktop&#65533; 2.10] on usb-0000:00:1d.1-1/input1
[   13.488535] cx88/0: cx2388x v4l2 driver version 0.0.6 loaded
[   13.488603] cx8800 0000:04:03.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   13.489745] cx88[0]: Your board isn't known (yet) to the driver.  You can
[   13.489747] cx88[0]: try to pick one of the existing card configs via
[   13.489748] cx88[0]: card=<n> insmod option.  Updating to the latest
[   13.489749] cx88[0]: version might help as well.
[   13.489753] cx88[0]: Here is a list of valid choices for the card=<n> insmod option:
[   13.489755] cx88[0]:    card=0 -> UNKNOWN/GENERIC
[   13.489757] cx88[0]:    card=1 -> Hauppauge WinTV 34xxx models
[   13.489759] cx88[0]:    card=2 -> GDI Black Gold
[   13.489761] cx88[0]:    card=3 -> PixelView
[   13.489763] cx88[0]:    card=4 -> ATI TV Wonder Pro
[   13.489765] cx88[0]:    card=5 -> Leadtek Winfast 2000XP Expert
[   13.489767] cx88[0]:    card=6 -> AverTV Studio 303 (M126)
[   13.489769] cx88[0]:    card=7 -> MSI TV-@nywhere Master
[   13.489771] cx88[0]:    card=8 -> Leadtek Winfast DV2000
[   13.489773] cx88[0]:    card=9 -> Leadtek PVR 2000
[   13.489775] cx88[0]:    card=10 -> IODATA GV-VCP3/PCI
[   13.489777] cx88[0]:    card=11 -> Prolink PlayTV PVR
[   13.489779] cx88[0]:    card=12 -> ASUS PVR-416
[   13.489781] cx88[0]:    card=13 -> MSI TV-@nywhere
[   13.489783] cx88[0]:    card=14 -> KWorld/VStream XPert DVB-T
[   13.489785] cx88[0]:    card=15 -> DViCO FusionHDTV DVB-T1
[   13.489787] cx88[0]:    card=16 -> KWorld LTV883RF
[   13.489789] cx88[0]:    card=17 -> DViCO FusionHDTV 3 Gold-Q
[   13.489791] cx88[0]:    card=18 -> Hauppauge Nova-T DVB-T
[   13.489793] cx88[0]:    card=19 -> Conexant DVB-T reference design
[   13.489795] cx88[0]:    card=20 -> Provideo PV259
[   13.489797] cx88[0]:    card=21 -> DViCO FusionHDTV DVB-T Plus
[   13.489799] cx88[0]:    card=22 -> pcHDTV HD3000 HDTV
[   13.489801] cx88[0]:    card=23 -> digitalnow DNTV Live! DVB-T
[   13.489804] cx88[0]:    card=24 -> Hauppauge WinTV 28xxx (Roslyn) models
[   13.489806] cx88[0]:    card=25 -> Digital-Logic MICROSPACE Entertainment Center (MEC)
[   13.489808] cx88[0]:    card=26 -> IODATA GV/BCTV7E
[   13.489810] cx88[0]:    card=27 -> PixelView PlayTV Ultra Pro (Stereo)
[   13.489812] cx88[0]:    card=28 -> DViCO FusionHDTV 3 Gold-T
[   13.489814] cx88[0]:    card=29 -> ADS Tech Instant TV DVB-T PCI
[   13.489816] cx88[0]:    card=30 -> TerraTec Cinergy 1400 DVB-T
[   13.489818] cx88[0]:    card=31 -> DViCO FusionHDTV 5 Gold
[   13.489820] cx88[0]:    card=32 -> AverMedia UltraTV Media Center PCI 550
[   13.489822] cx88[0]:    card=33 -> Kworld V-Stream Xpert DVD
[   13.489824] cx88[0]:    card=34 -> ATI HDTV Wonder
[   13.489826] cx88[0]:    card=35 -> WinFast DTV1000-T
[   13.489828] cx88[0]:    card=36 -> AVerTV 303 (M126)
[   13.489830] cx88[0]:    card=37 -> Hauppauge Nova-S-Plus DVB-S
[   13.489832] cx88[0]:    card=38 -> Hauppauge Nova-SE2 DVB-S
[   13.489834] cx88[0]:    card=39 -> KWorld DVB-S 100
[   13.489836] cx88[0]:    card=40 -> Hauppauge WinTV-HVR1100 DVB-T/Hybrid
[   13.489838] cx88[0]:    card=41 -> Hauppauge WinTV-HVR1100 DVB-T/Hybrid (Low Profile)
[   13.489841] cx88[0]:    card=42 -> digitalnow DNTV Live! DVB-T Pro
[   13.489843] cx88[0]:    card=43 -> KWorld/VStream XPert DVB-T with cx22702
[   13.489845] cx88[0]:    card=44 -> DViCO FusionHDTV DVB-T Dual Digital
[   13.489847] cx88[0]:    card=45 -> KWorld HardwareMpegTV XPert
[   13.489849] cx88[0]:    card=46 -> DViCO FusionHDTV DVB-T Hybrid
[   13.489851] cx88[0]:    card=47 -> pcHDTV HD5500 HDTV
[   13.489853] cx88[0]:    card=48 -> Kworld MCE 200 Deluxe
[   13.489855] cx88[0]:    card=49 -> PixelView PlayTV P7000
[   13.489857] cx88[0]:    card=50 -> NPG Tech Real TV FM Top 10
[   13.489859] cx88[0]:    card=51 -> WinFast DTV2000 H ver. I (old)
[   13.489861] cx88[0]:    card=52 -> Geniatech DVB-S
[   13.489863] cx88[0]:    card=53 -> Hauppauge WinTV-HVR3000 TriMode Analog/DVB-S/DVB-T
[   13.489866] cx88[0]:    card=54 -> Norwood Micro TV Tuner
[   13.489868] cx88[0]:    card=55 -> Shenzhen Tungsten Ages Tech TE-DTV-250 / Swann OEM
[   13.489870] cx88[0]:    card=56 -> Hauppauge WinTV-HVR1300 DVB-T/Hybrid MPEG Encoder
[   13.489872] cx88[0]:    card=57 -> ADS Tech Instant Video PCI
[   13.489874] cx88[0]:    card=58 -> Pinnacle PCTV HD 800i
[   13.489876] cx88[0]:    card=59 -> DViCO FusionHDTV 5 PCI nano
[   13.489879] cx88[0]:    card=60 -> Pinnacle Hybrid PCTV
[   13.489881] cx88[0]:    card=61 -> Winfast TV2000 XP Global
[   13.489883] cx88[0]:    card=62 -> PowerColor RA330
[   13.489885] cx88[0]:    card=63 -> Geniatech X8000-MT DVBT
[   13.489887] cx88[0]:    card=64 -> DViCO FusionHDTV DVB-T PRO
[   13.489889] cx88[0]:    card=65 -> DViCO FusionHDTV 7 Gold
[   13.489891] cx88[0]:    card=66 -> Prolink Pixelview MPEG 8000GT
[   13.489893] cx88[0]:    card=67 -> Kworld PlusTV HD PCI 120 (ATSC 120)
[   13.489895] cx88[0]:    card=68 -> Hauppauge WinTV-HVR4000 DVB-S/S2/T/Hybrid
[   13.489898] cx88[0]:    card=69 -> Hauppauge WinTV-HVR4000(Lite) DVB-S/S2
[   13.489900] cx88[0]:    card=70 -> TeVii S460 DVB-S/S2
[   13.489902] cx88[0]:    card=71 -> Omicom SS4 DVB-S/S2 PCI
[   13.489904] cx88[0]:    card=72 -> TBS 8920 DVB-S/S2
[   13.489906] cx88[0]:    card=73 -> TeVii S420 DVB-S
[   13.489908] cx88[0]:    card=74 -> Prolink Pixelview Global Extreme
[   13.489910] cx88[0]:    card=75 -> PROF 7300 DVB-S/S2
[   13.489912] cx88[0]:    card=76 -> WinFast DTV2000 H ver. J (new)
[   13.489915] cx88[0]: subsystem: 1043:4820, board: UNKNOWN/GENERIC [card=0,autodetected], frontend(s): 0
[   13.489918] cx88[0]: TV tuner type -1, Radio tuner type -1
[   13.669319] All bytes are equal. It is not a TEA5767
[   13.669392] tuner' 0-0060: chip found @ 0xc0 (cx88[0])
[   13.717574] cx88[0]/0: found at 0000:04:03.0, rev: 3, irq: 19, latency: 64, mmio: 0xdb000000
[   13.717678] cx88[0]/0: registered device video0 [v4l2]
[   13.717729] cx88[0]/0: registered device vbi0
[   13.717744] tuner' 0-0060: tuner type not set
[   13.717823] rt61pci 0000:04:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   13.725196] phy0: Selected rate control algorithm 'pid'
[   13.753314] Registered led device: rt61pci-phy0:radio
[   13.753356] Registered led device: rt61pci-phy0:assoc
[   13.753503] CTALSA 0000:04:04.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   14.208074] lp: driver loaded but no devices found
[   14.335976] Adding 3020180k swap on /dev/sda5.  Priority:-1 extents:1 across:3020180k
[   14.872817] EXT3 FS on sda1, internal journal
[   15.872876] type=1505 audit(1243704822.769:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2086
[   15.920363] type=1505 audit(1243704822.817:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2090
[   15.920458] type=1505 audit(1243704822.817:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2090
[   15.920499] type=1505 audit(1243704822.817:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2090
[   15.920540] type=1505 audit(1243704822.817:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2090
[   16.055619] type=1505 audit(1243704822.949:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2095
[   16.055785] type=1505 audit(1243704822.949:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2095
[   16.102665] type=1505 audit(1243704822.997:9): operation="profile_load" name="/usr/sbin/mysqld" name2="default" pid=2099
[   16.129607] type=1505 audit(1243704823.025:10): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2103
[   23.251107] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   23.251110] Bluetooth: BNEP filters: protocol multicast
[   23.271269] Bridge firewalling registered
[   24.702435] ppdev: user-space parallel port driver
[   29.236228] e1000e 0000:00:19.0: irq 2299 for MSI/MSI-X
[   29.292075] e1000e 0000:00:19.0: irq 2299 for MSI/MSI-X
[   29.292400] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   29.293154] rt61pci 0000:04:05.0: firmware: requesting rt2561s.bin
[   29.430452] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   58.797407] UDF-fs: Partition marked readonly; forcing readonly mount
[   58.822436] UDF-fs INFO UDF: Mounting volume 'BURN_AFTER_READING', timestamp 2008/10/17 08:45 (1000)
[   61.340347] wlan0: authenticate with AP 00:c0:49:ed:ce:94
[   61.341553] wlan0: authenticated
[   61.341557] wlan0: associate with AP 00:c0:49:ed:ce:94
[   61.346297] wlan0: RX AssocResp from 00:c0:49:ed:ce:94 (capab=0x471 status=0 aid=2)
[   61.346301] wlan0: associated
[   61.346706] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   71.644007] wlan0: no IPv6 routers present
[78181.836055] usb 1-4: new high speed USB device using ehci_hcd and address 3
[78181.969165] usb 1-4: configuration #1 chosen from 1 choice
[78182.341623] Initializing USB Mass Storage driver...
[78182.344307] scsi6 : SCSI emulation for USB Mass Storage devices
[78182.345065] usbcore: registered new interface driver usb-storage
[78182.345069] USB Mass Storage support registered.
[78182.345165] usb-storage: device found at 3
[78182.345167] usb-storage: waiting for device to settle before scanning
[78187.344203] usb-storage: device scan complete
[78187.345690] scsi 6:0:0:0: Direct-Access     RIM      BlackBerry SD    0001 PQ: 0 ANSI: 0 CCS
[78187.346789] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[78187.346861] sd 6:0:0:0: Attached scsi generic sg2 type 0
[81941.192654] cdrom: This disc doesn't have any tracks I recognize!
[81941.253934] end_request: I/O error, dev sr0, sector 0
[81941.253941] Buffer I/O error on device sr0, logical block 0
[81941.254661] end_request: I/O error, dev sr0, sector 0
[81941.254665] Buffer I/O error on device sr0, logical block 0
[82168.438839] usb 1-4: USB disconnect, address 3
[125333.744049] usb 1-4: new high speed USB device using ehci_hcd and address 4
[125333.888278] usb 1-4: configuration #1 chosen from 1 choice
[125333.896071] scsi7 : SCSI emulation for USB Mass Storage devices
[125333.896157] usb-storage: device found at 4
[125333.896159] usb-storage: waiting for device to settle before scanning
[125335.090811] usb 1-4: USB disconnect, address 4
[125335.640277] usb 4-2: new full speed USB device using uhci_hcd and address 3
[125335.775863] usb 4-2: not running at top speed; connect to a high speed hub
[125335.804217] usb 4-2: configuration #1 chosen from 1 choice
[125335.816052] scsi8 : SCSI emulation for USB Mass Storage devices
[125335.816483] usb-storage: device found at 3
[125335.816485] usb-storage: waiting for device to settle before scanning
[125340.817816] usb-storage: device scan complete
[125340.820906] scsi 8:0:0:0: Direct-Access     RIM      BlackBerry SD    0001 PQ: 0 ANSI: 0 CCS
[125340.831796] sd 8:0:0:0: [sdb] 1984000 512-byte hardware sectors: (1.01 GB/968 MiB)
[125340.837875] sd 8:0:0:0: [sdb] Write Protect is off
[125340.837879] sd 8:0:0:0: [sdb] Mode Sense: 43 00 00 00
[125340.837882] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[125340.846792] sd 8:0:0:0: [sdb] 1984000 512-byte hardware sectors: (1.01 GB/968 MiB)
[125340.854796] sd 8:0:0:0: [sdb] Write Protect is off
[125340.854800] sd 8:0:0:0: [sdb] Mode Sense: 43 00 00 00
[125340.854803] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[125340.854811]  sdb: sdb1
[125340.876873] sd 8:0:0:0: [sdb] Attached SCSI removable disk
[125340.876954] sd 8:0:0:0: Attached scsi generic sg2 type 0
[154439.192107] usb 4-2: USB disconnect, address 3
[208440.820314] usb 1-4: new high speed USB device using ehci_hcd and address 6
[208440.953045] usb 1-4: configuration #1 chosen from 1 choice
[208440.957101] scsi9 : SCSI emulation for USB Mass Storage devices
[208440.957174] usb-storage: device found at 6
[208440.957176] usb-storage: waiting for device to settle before scanning
[208445.956443] usb-storage: device scan complete
[208445.958051] scsi 9:0:0:0: Direct-Access     RIM      BlackBerry SD    0001 PQ: 0 ANSI: 0 CCS
[208445.960982] sd 9:0:0:0: [sdb] Attached SCSI removable disk
[208445.961069] sd 9:0:0:0: Attached scsi generic sg2 type 0
[208620.284212] audacity[5571]: segfault at b5e81912 ip b5e81912 sp b4ea8170 error 4 in SYSV00000000 (deleted)[b5ebc000+60000]
[208750.420276] audacity[5629]: segfault at b5eba912 ip b5eba912 sp b4ee1170 error 4 in SYSV00000000 (deleted)[b5ef5000+60000]
[241032.693534] usb 1-4: USB disconnect, address 6
[243023.312247] type=1505 audit(1243947830.209:11): operation="profile_replace" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=23607
[243023.413879] type=1505 audit(1243947830.309:12): operation="profile_replace" name="/sbin/dhclient-script" name2="default" pid=23611
[243023.414144] type=1505 audit(1243947830.309:13): operation="profile_replace" name="/sbin/dhclient3" name2="default" pid=23611
[243023.414197] type=1505 audit(1243947830.309:14): operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=23611
[243023.414246] type=1505 audit(1243947830.309:15): operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=23611
[243023.569032] type=1505 audit(1243947830.465:16): operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=23616
[243023.569336] type=1505 audit(1243947830.465:17): operation="profile_replace" name="/usr/sbin/cupsd" name2="default" pid=23616
[243023.600351] type=1505 audit(1243947830.497:18): operation="profile_replace" name="/usr/sbin/mysqld" name2="default" pid=23620
[243023.640162] type=1505 audit(1243947830.537:19): operation="profile_replace" name="/usr/sbin/tcpdump" name2="default" pid=23624
[293990.028040] indicator-apple[3760]: segfault at 756d2f65 ip b789b07a sp bfec2dec error 4 in libc-2.9.so[b7824000+15c000]
[298297.527346] wlan0: disassociating by local choice (reason=3)
[329074.716645] wlan0: authenticate with AP 00:c0:49:ed:ce:94
[329074.717883] wlan0: authenticated
[329074.717887] wlan0: associate with AP 00:c0:49:ed:ce:94
[329074.720999] wlan0: RX AssocResp from 00:c0:49:ed:ce:94 (capab=0x471 status=0 aid=2)
[329074.721003] wlan0: associated
[357164.256044] wlan0: disassociating by local choice (reason=3)
[357198.796720] wlan0: authenticate with AP 00:c0:49:ed:ce:94
[357198.820023] wlan0: authenticated
[357198.820028] wlan0: associate with AP 00:c0:49:ed:ce:94
[357198.823016] wlan0: RX AssocResp from 00:c0:49:ed:ce:94 (capab=0x471 status=0 aid=2)
[357198.823019] wlan0: associated
[362356.420470] type=1505 audit(1244067175.021:20): operation="profile_replace" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=9766
[362356.507870] type=1505 audit(1244067175.105:21): operation="profile_replace" name="/sbin/dhclient-script" name2="default" pid=9770
[362356.508491] type=1505 audit(1244067175.109:22): operation="profile_replace" name="/sbin/dhclient3" name2="default" pid=9770
[362356.508540] type=1505 audit(1244067175.109:23): operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=9770
[362356.508585] type=1505 audit(1244067175.109:24): operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=9770
[362356.693560] type=1505 audit(1244067175.293:25): operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=9775
[362356.693854] type=1505 audit(1244067175.293:26): operation="profile_replace" name="/usr/sbin/cupsd" name2="default" pid=9775
[362356.738145] type=1505 audit(1244067175.337:27): operation="profile_load" name="/usr/sbin/dhcpd3" name2="default" pid=9779
[362356.774486] type=1505 audit(1244067175.373:28): operation="profile_replace" name="/usr/sbin/mysqld" name2="default" pid=9783
[362356.984596] warning: `dhcpd3' uses 32-bit capabilities (legacy support in use)
[364527.134423] __ratelimit: 3 callbacks suppressed
[364527.134426] type=1505 audit(1244069345.733:30): operation="profile_replace" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=15645
[364527.187092] type=1505 audit(1244069345.785:31): operation="profile_replace" name="/sbin/dhclient-script" name2="default" pid=15649
[364527.187342] type=1505 audit(1244069345.785:32): operation="profile_replace" name="/sbin/dhclient3" name2="default" pid=15649
[364527.187391] type=1505 audit(1244069345.785:33): operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=15649
[364527.187439] type=1505 audit(1244069345.785:34): operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=15649
[364527.332741] type=1505 audit(1244069345.933:35): operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=15654
[364527.333056] type=1505 audit(1244069345.933:36): operation="profile_replace" name="/usr/sbin/cupsd" name2="default" pid=15654
[364527.371406] type=1505 audit(1244069345.969:37): operation="profile_replace" name="/usr/sbin/dhcpd3" name2="default" pid=15658
[364527.401623] type=1505 audit(1244069346.001:38): operation="profile_replace" name="/usr/sbin/mysqld" name2="default" pid=15662
[364527.433673] type=1505 audit(1244069346.033:39): operation="profile_replace" name="/usr/sbin/tcpdump" name2="default" pid=15666
[375165.900033] wlan0: No ProbeResp from current AP 00:c0:49:ed:ce:94 - assume out of range
[375167.440092] wlan0: direct probe to AP 00:c0:49:ed:ce:94 try 1
[375167.440802] wlan0: direct probe to AP 00:c0:49:ed:ce:94 try 1
[375167.440838] wlan0: direct probe to AP 00:c0:49:ed:ce:94 try 1
[375167.640152] wlan0: direct probe to AP 00:c0:49:ed:ce:94 try 2
[375167.840114] wlan0: direct probe to AP 00:c0:49:ed:ce:94 try 3
[375168.040134] wlan0: direct probe to AP 00:c0:49:ed:ce:94 timed out
[375183.048453] wlan0: authenticate with AP 00:c0:49:ed:ce:94
[375183.248149] wlan0: authenticate with AP 00:c0:49:ed:ce:94
[375183.448080] wlan0: authenticate with AP 00:c0:49:ed:ce:94
[375183.648135] wlan0: authentication with AP 00:c0:49:ed:ce:94 timed out
[375194.492409] wlan0: direct probe to AP 00:c0:49:ed:ce:94 try 1
[375194.493613] wlan0 direct probe responded
[375194.493618] wlan0: authenticate with AP 00:c0:49:ed:ce:94
[375194.497633] wlan0: authenticated
[375194.497636] wlan0: associate with AP 00:c0:49:ed:ce:94
[375194.499812] wlan0: RX AssocResp from 00:c0:49:ed:ce:94 (capab=0x471 status=0 aid=3)
[375194.499814] wlan0: associated
[463828.692218] usb 1-4: new high speed USB device using ehci_hcd and address 7
[463828.825010] usb 1-4: configuration #1 chosen from 1 choice
[463828.829100] scsi10 : SCSI emulation for USB Mass Storage devices
[463828.829171] usb-storage: device found at 7
[463828.829173] usb-storage: waiting for device to settle before scanning
[463833.829692] usb-storage: device scan complete
[463833.831423] scsi 10:0:0:0: Direct-Access     RIM      BlackBerry SD    0001 PQ: 0 ANSI: 0 CCS
[463833.832798] sd 10:0:0:0: [sdb] Attached SCSI removable disk
[463833.833395] sd 10:0:0:0: Attached scsi generic sg2 type 0
[500573.708707] usb 1-4: USB disconnect, address 7
[628121.508053] wlan0: No ProbeResp from current AP 00:c0:49:ed:ce:94 - assume out of range
[628123.052204] wlan0: direct probe to AP 00:c0:49:ed:ce:94 try 1
[628123.252286] wlan0: direct probe to AP 00:c0:49:ed:ce:94 try 2
[628123.452263] wlan0: direct probe to AP 00:c0:49:ed:ce:94 try 3
[628123.652286] wlan0: direct probe to AP 00:c0:49:ed:ce:94 timed out
[628146.320197] wlan0: authenticate with AP 00:c0:49:ed:ce:94
[628146.321430] wlan0: authenticated
[628146.321435] wlan0: associate with AP 00:c0:49:ed:ce:94
[628146.324621] wlan0: RX AssocResp from 00:c0:49:ed:ce:94 (capab=0x471 status=0 aid=1)
[628146.324625] wlan0: associated
[628207.245545] wlan0 direct probe responded
[628207.245551] wlan0: authenticate with AP 00:c0:49:ed:ce:94
[628207.247031] wlan0: authenticated
[628207.247035] wlan0: associate with AP 00:c0:49:ed:ce:94
[628207.250389] wlan0: RX ReassocResp from 00:c0:49:ed:ce:94 (capab=0x471 status=0 aid=1)
[628207.250392] wlan0: associated
[684239.808283] usb 1-4: new high speed USB device using ehci_hcd and address 8
[684239.942472] usb 1-4: configuration #1 chosen from 1 choice
[684239.980309] scsi11 : SCSI emulation for USB Mass Storage devices
[684239.981283] usb-storage: device found at 8
[684239.981285] usb-storage: waiting for device to settle before scanning
[684244.980385] usb-storage: device scan complete
[684244.982002] scsi 11:0:0:0: Direct-Access     RIM      BlackBerry SD    0001 PQ: 0 ANSI: 0 CCS
[684244.984702] sd 11:0:0:0: [sdb] Attached SCSI removable disk
[684244.984780] sd 11:0:0:0: Attached scsi generic sg2 type 0
[686746.076295] usb 1-4: USB disconnect, address 8
[726716.584274] usb 1-4: new high speed USB device using ehci_hcd and address 9
[726716.721430] usb 1-4: configuration #1 chosen from 1 choice
[726716.728083] scsi12 : SCSI emulation for USB Mass Storage devices
[726716.729510] usb-storage: device found at 9
[726716.729513] usb-storage: waiting for device to settle before scanning
[726721.728218] usb-storage: device scan complete
[726721.729963] scsi 12:0:0:0: Direct-Access     RIM      BlackBerry SD    0001 PQ: 0 ANSI: 0 CCS
[726721.732917] sd 12:0:0:0: [sdb] Attached SCSI removable disk
[726721.732992] sd 12:0:0:0: Attached scsi generic sg2 type 0
[759395.801303] usb 1-4: USB disconnect, address 9
[818542.596074] usb 1-4: new high speed USB device using ehci_hcd and address 10
[818542.729321] usb 1-4: configuration #1 chosen from 1 choice
[818542.734152] scsi13 : SCSI emulation for USB Mass Storage devices
[818542.735697] usb-storage: device found at 10
[818542.735700] usb-storage: waiting for device to settle before scanning
[818547.732194] usb-storage: device scan complete
[818547.733812] scsi 13:0:0:0: Direct-Access     RIM      BlackBerry SD    0001 PQ: 0 ANSI: 0 CCS
[818547.739804] sd 13:0:0:0: [sdb] Attached SCSI removable disk
[818547.739886] sd 13:0:0:0: Attached scsi generic sg2 type 0
[845972.662089] usb 1-4: USB disconnect, address 10

```

---

### Post by QIII on 2009-06-09
I haven't had any problems with Brasero.

How old is your machine?  The fact that you are having problems across several applications might spell trouble.

Rule out hardware failure and then work on troubleshooting software.  Finding a hardware fault can be pretty easy, if a little spendy to correct.  Software troubleshooting can be a pain.

Are you set up to dual boot on that machine?  Can you transfer the CD drive to another machine?

---

