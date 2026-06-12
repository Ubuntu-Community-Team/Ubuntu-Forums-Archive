---
title: "Ethernet adapter working, wireless isn't"
date: 2010-06-10
forum: New to Ubuntu
---

### Post by edanto on 2010-06-10
UPDATE TO TITLE - ETHERNET ADAPTER WORKING, WIRELESS ISN'T

All of a sudden, my ubuntu laptop can't connect to anything.  There is an '!' over the wireless icon at the top of the screen and during bootup I think I see a brief flash of some unusual error messages but I can't make them out as they disappear too quickly.

How can I give more detailed information to troubleshoot this, i.e. what should I put in the terminal to give a readout of the network settings?

Before this happened, I hadn't made any changes to any settings or done anything unusual as regards new software - not that I know of!!

---

### Post by Peter09 on 2010-06-10
Look in 
 
System->Admin->Logs
 
The syslog log and the dmesg log will show errors during boot (and after) see if there is anything there.

---

### Post by edanto on 2010-06-10
dmesg:



```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.32-22-generic (buildd@palmer) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #36-Ubuntu SMP Thu Jun 3 22:02:19 UTC 2010 (Ubuntu 2.6.32-22.36-generic 2.6.32.11+drm33.2)
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
[    0.000000]  BIOS-e820: 0000000000100000 - 000000005f7d0000 (usable)
[    0.000000]  BIOS-e820: 000000005f7d0000 - 000000005f7efc00 (reserved)
[    0.000000]  BIOS-e820: 000000005f7efc00 - 000000005f7fb000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000005f7fb000 - 000000005f800000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec02000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed20000 - 00000000fed9b000 (reserved)
[    0.000000]  BIOS-e820: 00000000feda0000 - 00000000fedc0000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb00000 - 00000000ffc00000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.3 present.
[    0.000000] last_pfn = 0x5f7d0 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask FC0000000 write-back
[    0.000000]   1 base 040000000 mask FE0000000 write-back
[    0.000000]   2 base 05F800000 mask FFF800000 uncachable
[    0.000000]   3 base 0FEDA0000 mask FFFFE0000 uncachable
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] PAT not supported by CPU.
[    0.000000] e820 update range: 0000000000002000 - 0000000000006000 (usable) ==> (reserved)
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 000000000009fc00 (usable)
[    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000005f7d0000 (usable)
[    0.000000]  modified: 000000005f7d0000 - 000000005f7efc00 (reserved)
[    0.000000]  modified: 000000005f7efc00 - 000000005f7fb000 (ACPI NVS)
[    0.000000]  modified: 000000005f7fb000 - 000000005f800000 (reserved)
[    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec02000 (reserved)
[    0.000000]  modified: 00000000fed20000 - 00000000fed9b000 (reserved)
[    0.000000]  modified: 00000000feda0000 - 00000000fedc0000 (reserved)
[    0.000000]  modified: 00000000ffb00000 - 00000000ffc00000 (reserved)
[    0.000000]  modified: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 7000-c000
[    0.000000] RAMDISK: 37855000 - 37fef73e
[    0.000000] Allocated new RAMDISK: 008de000 - 0107873e
[    0.000000] Move RAMDISK from 0000000037855000 - 0000000037fef73d to 008de000 - 0107873d
[    0.000000] ACPI: RSDP 000fe270 00014 (v00 HP    )
[    0.000000] ACPI: RSDT 5f7efc84 00034 (v01 HP     099C     21110520 HP   00000001)
[    0.000000] ACPI: FACP 5f7efc00 00084 (v02 HP     099C     00000002 HP   00000001)
[    0.000000] ACPI: DSDT 5f7efd50 07D58 (v01 HP       DAU00  00010000 MSFT 0100000E)
[    0.000000] ACPI: FACS 5f7fae80 00040
[    0.000000] ACPI: APIC 5f7efcb8 0005A (v01 HP     099C     00000001 HP   00000001)
[    0.000000] ACPI: MCFG 5f7efd14 0003C (v01 HP     099C     00000001 HP   00000001)
[    0.000000] ACPI: SSDT 5f7f7aa8 00371 (v01 HP       HPQPpc 00001001 MSFT 0100000E)
[    0.000000] ACPI: Local APIC address 0xfec01000
[    0.000000] 639MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000]   node 0 low ram: 00000000 - 377fe000
[    0.000000]   node 0 bootmap 00008000 - 0000ef00
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008d9e98]    TEXT DATA BSS ==> [0000100000 - 00008d9e98]
[    0.000000]   #4 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #5 [00008da000 - 00008dd164]              BRK ==> [00008da000 - 00008dd164]
[    0.000000]   #6 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
[    0.000000]   #7 [00008de000 - 000107873e]      NEW RAMDISK ==> [00008de000 - 000107873e]
[    0.000000]   #8 [0000008000 - 000000f000]          BOOTMAP ==> [0000008000 - 000000f000]
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0005f7d0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0005f7d0
[    0.000000] On node 0 totalpages: 391019
[    0.000000] free_area_init_node: node 0, pgdat c0798720, node_mem_map c107a000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3963 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 1280 pages used for memmap
[    0.000000]   HighMem zone: 162514 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfec01000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 5f800000 (gap: 5f800000:80800000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @c2000000 s36024 r0 d21320 u4194304
[    0.000000] pcpu-alloc: s36024 r0 d21320 u4194304 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 387963
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-22-generic root=UUID=e9058085-b421-4a3d-95ea-5b18603e38ad ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 7822400 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0005f7d0)
[    0.000000] Memory: 1526484k/1564480k available (4673k kernel code, 36620k reserved, 2121k data, 656k init, 655176k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc07a3000 - 0xc0847000   ( 656 kB)
[    0.000000]       .data : 0xc0590663 - 0xc07a2e48   (2121 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0590663   (4673 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] NR_IRQS:2304 nr_irqs:256
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 800.225 MHz processor.
[    0.004009] Calibrating delay loop (skipped), value calculated using timer frequency.. 1600.45 BogoMIPS (lpj=3200900)
[    0.004051] Security Framework initialized
[    0.004109] AppArmor: AppArmor initialized
[    0.004125] Mount-cache hash table entries: 512
[    0.004396] Initializing cgroup subsys ns
[    0.004406] Initializing cgroup subsys cpuacct
[    0.004416] Initializing cgroup subsys memory
[    0.004437] Initializing cgroup subsys devices
[    0.004443] Initializing cgroup subsys freezer
[    0.004449] Initializing cgroup subsys net_cls
[    0.004497] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004505] CPU: L2 cache: 2048K
[    0.004514] mce: CPU supports 5 MCE banks
[    0.004532] CPU0: Thermal monitoring enabled (TM2)
[    0.004553] Performance Events: p6 PMU driver.
[    0.004570] ... version:                0
[    0.004575] ... bit width:              32
[    0.004580] ... generic registers:      2
[    0.004585] ... value mask:             00000000ffffffff
[    0.004591] ... max period:             000000007fffffff
[    0.004596] ... fixed-purpose events:   0
[    0.004601] ... event mask:             0000000000000003
[    0.004610] Checking 'hlt' instruction... OK.
[    0.021697] SMP alternatives: switching to UP code
[    0.037971] Freeing SMP alternatives: 19k freed
[    0.037989] ACPI: Core revision 20090903
[    0.060034] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.060053] ftrace: allocating 21771 entries in 43 pages
[    0.068101] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.068500] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.110077] CPU0: Intel(R) Pentium(R) M processor 1.73GHz stepping 08
[    0.112001] Brought up 1 CPUs
[    0.112001] Total of 1 processors activated (1600.45 BogoMIPS).
[    0.112001] CPU0 attaching NULL sched-domain.
[    0.112001] devtmpfs: initialized
[    0.112001] HP Compaq Laptop series board detected. Selecting BIOS-method for reboots.
[    0.112001] regulator: core version 0.5
[    0.112001] Time:  9:02:04  Date: 06/10/10
[    0.112001] NET: Registered protocol family 16
[    0.112001] EISA bus registered
[    0.112001] ACPI: bus type pci registered
[    0.112001] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.112001] PCI: MCFG area at e0000000 reserved in E820
[    0.112001] PCI: Using MMCONFIG for extended config space
[    0.112001] PCI: Using configuration type 1 for base access
[    0.112120] bio: create slab <bio-0> at 0
[    0.114124] ACPI: EC: Look up EC in DSDT
[    0.160266] ACPI: Interpreter enabled
[    0.160299] ACPI: (supports S0 S3 S4 S5)
[    0.160345] ACPI: Using IOAPIC for interrupt routing
[    0.185064] ACPI: EC: GPE = 0x10, I/O: command/status = 0x66, data = 0x62
[    0.185453] ACPI: Power Resource [C1A6] (on)
[    0.185792] ACPI: Power Resource [C1AE] (on)
[    0.186103] ACPI: Power Resource [C1B5] (on)
[    0.186194] ACPI: Power Resource [C1C5] (on)
[    0.186412] ACPI: Power Resource [C244] (off)
[    0.186598] ACPI: Power Resource [C245] (off)
[    0.186783] ACPI: Power Resource [C246] (off)
[    0.186969] ACPI: Power Resource [C247] (off)
[    0.187427] ACPI: No dock devices found.
[    0.197367] ACPI: PCI Root Bridge [C002] (0000:00)
[    0.197518] pci 0000:00:02.0: reg 10 32bit mmio: [0xd0400000-0xd047ffff]
[    0.197529] pci 0000:00:02.0: reg 14 io port: [0x7000-0x7007]
[    0.197540] pci 0000:00:02.0: reg 18 32bit mmio pref: [0xc0000000-0xcfffffff]
[    0.197550] pci 0000:00:02.0: reg 1c 32bit mmio: [0xd0480000-0xd04bffff]
[    0.197604] pci 0000:00:02.1: reg 10 32bit mmio: [0xd0500000-0xd057ffff]
[    0.197790] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.197799] pci 0000:00:1c.0: PME# disabled
[    0.197886] pci 0000:00:1d.0: reg 20 io port: [0x2000-0x201f]
[    0.197965] pci 0000:00:1d.1: reg 20 io port: [0x2020-0x203f]
[    0.198048] pci 0000:00:1d.2: reg 20 io port: [0x2040-0x205f]
[    0.198127] pci 0000:00:1d.3: reg 20 io port: [0x2060-0x207f]
[    0.198212] pci 0000:00:1d.7: reg 10 32bit mmio: [0xd0580000-0xd05803ff]
[    0.198287] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.198296] pci 0000:00:1d.7: PME# disabled
[    0.198434] pci 0000:00:1e.2: reg 10 io port: [0x2100-0x21ff]
[    0.198447] pci 0000:00:1e.2: reg 14 io port: [0x2200-0x223f]
[    0.198461] pci 0000:00:1e.2: reg 18 32bit mmio: [0xd0581000-0xd05811ff]
[    0.198474] pci 0000:00:1e.2: reg 1c 32bit mmio: [0xd0582000-0xd05820ff]
[    0.198523] pci 0000:00:1e.2: PME# supported from D0 D3hot D3cold
[    0.198532] pci 0000:00:1e.2: PME# disabled
[    0.198583] pci 0000:00:1e.3: reg 10 io port: [0x2400-0x24ff]
[    0.198596] pci 0000:00:1e.3: reg 14 io port: [0x2500-0x257f]
[    0.198657] pci 0000:00:1e.3: PME# supported from D0 D3hot D3cold
[    0.198666] pci 0000:00:1e.3: PME# disabled
[    0.198775] pci 0000:00:1f.0: Force enabled HPET at 0xfed00000
[    0.198789] pci 0000:00:1f.0: quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[    0.198799] pci 0000:00:1f.0: quirk: region 1100-113f claimed by ICH6 GPIO
[    0.198808] pci 0000:00:1f.0: LPC Generic IO decode 1 PIO at 0500-057f
[    0.198851] pci 0000:00:1f.1: reg 10 io port: [0x00-0x07]
[    0.198863] pci 0000:00:1f.1: reg 14 io port: [0x00-0x03]
[    0.198876] pci 0000:00:1f.1: reg 18 io port: [0x00-0x07]
[    0.198889] pci 0000:00:1f.1: reg 1c io port: [0x00-0x03]
[    0.198902] pci 0000:00:1f.1: reg 20 io port: [0x2580-0x258f]
[    0.199013] pci 0000:00:1c.0: bridge io port: [0x00-0xfff]
[    0.199022] pci 0000:00:1c.0: bridge 32bit mmio: [0x000000-0x0fffff]
[    0.199036] pci 0000:00:1c.0: bridge 64bit mmio pref: [0x000000-0x0fffff]
[    0.199113] pci 0000:02:04.0: reg 10 32bit mmio: [0xd0000000-0xd0000fff]
[    0.199202] pci 0000:02:04.0: PME# supported from D0 D3hot D3cold
[    0.199212] pci 0000:02:04.0: PME# disabled
[    0.199279] pci 0000:02:06.0: reg 10 32bit mmio: [0xd0001000-0xd0001fff]
[    0.199317] pci 0000:02:06.0: supports D1 D2
[    0.199323] pci 0000:02:06.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.199332] pci 0000:02:06.0: PME# disabled
[    0.199397] pci 0000:02:06.1: reg 10 32bit mmio: [0xd0002000-0xd0002fff]
[    0.199435] pci 0000:02:06.1: supports D1 D2
[    0.199441] pci 0000:02:06.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.199450] pci 0000:02:06.1: PME# disabled
[    0.199515] pci 0000:02:06.2: reg 10 32bit mmio: [0xd0003000-0xd00037ff]
[    0.199531] pci 0000:02:06.2: reg 14 32bit mmio: [0xd0004000-0xd0007fff]
[    0.199614] pci 0000:02:06.2: supports D1 D2
[    0.199620] pci 0000:02:06.2: PME# supported from D0 D1 D2 D3hot
[    0.199630] pci 0000:02:06.2: PME# disabled
[    0.199693] pci 0000:02:06.3: reg 10 32bit mmio: [0xd0008000-0xd0009fff]
[    0.199780] pci 0000:02:06.3: supports D1 D2
[    0.199785] pci 0000:02:06.3: PME# supported from D0 D1 D2 D3hot
[    0.199795] pci 0000:02:06.3: PME# disabled
[    0.199859] pci 0000:02:06.4: reg 10 32bit mmio: [0xd000a000-0xd000a0ff]
[    0.199874] pci 0000:02:06.4: reg 14 32bit mmio: [0xd000b000-0xd000b0ff]
[    0.199890] pci 0000:02:06.4: reg 18 32bit mmio: [0xd000c000-0xd000c0ff]
[    0.199960] pci 0000:02:06.4: supports D1 D2
[    0.199965] pci 0000:02:06.4: PME# supported from D0 D1 D2 D3hot
[    0.199975] pci 0000:02:06.4: PME# disabled
[    0.200047] pci 0000:02:06.5: reg 10 32bit mmio: [0xd000d000-0xd000dfff]
[    0.200063] pci 0000:02:06.5: reg 14 32bit mmio: [0xd000e000-0xd000efff]
[    0.200078] pci 0000:02:06.5: reg 18 32bit mmio: [0xd000f000-0xd000ffff]
[    0.200094] pci 0000:02:06.5: reg 1c 32bit mmio: [0xd0010000-0xd0010fff]
[    0.200155] pci 0000:02:06.5: supports D1 D2
[    0.200161] pci 0000:02:06.5: PME# supported from D0 D1 D2 D3hot
[    0.200170] pci 0000:02:06.5: PME# disabled
[    0.200292] pci 0000:02:0e.0: reg 10 64bit mmio: [0xd0020000-0xd002ffff]
[    0.200392] pci 0000:02:0e.0: PME# supported from D3hot D3cold
[    0.200402] pci 0000:02:0e.0: PME# disabled
[    0.200456] pci 0000:00:1e.0: transparent bridge
[    0.200469] pci 0000:00:1e.0: bridge 32bit mmio: [0xd0000000-0xd03fffff]
[    0.200557] pci_bus 0000:00: on NUMA node 0
[    0.200568] ACPI: PCI Interrupt Routing Table [\_SB_.C002._PRT]
[    0.201034] ACPI: PCI Interrupt Routing Table [\_SB_.C002.C068._PRT]
[    0.201420] ACPI: PCI Interrupt Routing Table [\_SB_.C002.C0CC._PRT]
[    0.263501] ACPI: PCI Interrupt Link [C0D8] (IRQs 10 *11)
[    0.263925] ACPI: PCI Interrupt Link [C0D9] (IRQs *10 11)
[    0.264355] ACPI: PCI Interrupt Link [C0DA] (IRQs *10 11)
[    0.264773] ACPI: PCI Interrupt Link [C0DB] (IRQs *10 11)
[    0.265193] ACPI: PCI Interrupt Link [C0EE] (IRQs *10 11)
[    0.265616] ACPI: PCI Interrupt Link [C0EF] (IRQs 10 *11)
[    0.266028] ACPI: PCI Interrupt Link [C0F0] (IRQs *10 11)
[    0.266427] ACPI: PCI Interrupt Link [C0F1] (IRQs 10 11) *0, disabled.
[    0.266757] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.266782] vgaarb: loaded
[    0.267046] SCSI subsystem initialized
[    0.267141] libata version 3.00 loaded.
[    0.267300] usbcore: registered new interface driver usbfs
[    0.267331] usbcore: registered new interface driver hub
[    0.267389] usbcore: registered new device driver usb
[    0.267730] ACPI: WMI: Mapper loaded
[    0.267735] PCI: Using ACPI for IRQ routing
[    0.267743] pci 0000:00:1c.0: BAR 13: can't allocate resource
[    0.267749] pci 0000:00:1c.0: BAR 14: can't allocate resource
[    0.267755] pci 0000:00:1c.0: BAR 15: can't allocate resource
[    0.268074] NetLabel: Initializing
[    0.268079] NetLabel:  domain hash size = 128
[    0.268084] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.268112] NetLabel:  unlabeled traffic allowed by default
[    0.268443] hpet clockevent registered
[    0.268450] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.268461] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.268474] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.272019] Switching to clocksource tsc
[    0.276461] AppArmor: AppArmor Filesystem Enabled
[    0.276486] pnp: PnP ACPI init
[    0.276507] ACPI: bus type pnp registered
[    0.299966] pnp: PnP ACPI: found 14 devices
[    0.299972] ACPI: ACPI bus type pnp unregistered
[    0.299981] PnPBIOS: Disabled by ACPI PNP
[    0.300002] system 00:00: iomem range 0x0-0x9ffff could not be reserved
[    0.300010] system 00:00: iomem range 0xe0000-0xfffff could not be reserved
[    0.300018] system 00:00: iomem range 0x100000-0x5f7fffff could not be reserved
[    0.300041] system 00:0b: ioport range 0x500-0x57f has been reserved
[    0.300050] system 00:0b: iomem range 0xffb00000-0xffbfffff has been reserved
[    0.300058] system 00:0b: iomem range 0xfff00000-0xffffffff has been reserved
[    0.300071] system 00:0c: ioport range 0x4d0-0x4d1 has been reserved
[    0.300079] system 00:0c: ioport range 0x1000-0x107f has been reserved
[    0.300086] system 00:0c: ioport range 0x1100-0x113f has been reserved
[    0.300094] system 00:0c: ioport range 0x1200-0x121f has been reserved
[    0.300102] system 00:0c: iomem range 0xe0000000-0xefffffff has been reserved
[    0.300110] system 00:0c: iomem range 0xfec00000-0xfec000ff could not be reserved
[    0.300118] system 00:0c: iomem range 0xfed20000-0xff41ffff could not be reserved
[    0.300126] system 00:0c: iomem range 0xfed90000-0xfed9afff has been reserved
[    0.300140] system 00:0d: iomem range 0xfeda0000-0xfedbffff has been reserved
[    0.300148] system 00:0d: iomem range 0xfec01000-0xfec01fff has been reserved
[    0.335100] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:10
[    0.335109] pci 0000:00:1c.0:   IO window: 0x3000-0x3fff
[    0.335120] pci 0000:00:1c.0:   MEM window: 0x68000000-0x681fffff
[    0.335131] pci 0000:00:1c.0:   PREFETCH window: 0x00000068200000-0x000000683fffff
[    0.335155] pci 0000:02:06.0: CardBus bridge, secondary bus 0000:03
[    0.335161] pci 0000:02:06.0:   IO window: 0x004000-0x0040ff
[    0.335171] pci 0000:02:06.0:   IO window: 0x004400-0x0044ff
[    0.335182] pci 0000:02:06.0:   PREFETCH window: 0x60000000-0x63ffffff
[    0.335192] pci 0000:02:06.0:   MEM window: 0x6c000000-0x6fffffff
[    0.335203] pci 0000:02:06.1: CardBus bridge, secondary bus 0000:04
[    0.335209] pci 0000:02:06.1:   IO window: 0x004800-0x0048ff
[    0.335219] pci 0000:02:06.1:   IO window: 0x004c00-0x004cff
[    0.335229] pci 0000:02:06.1:   PREFETCH window: 0x64000000-0x67ffffff
[    0.335240] pci 0000:02:06.1:   MEM window: 0x70000000-0x73ffffff
[    0.335250] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:02
[    0.335258] pci 0000:00:1e.0:   IO window: 0x4000-0x4fff
[    0.335269] pci 0000:00:1e.0:   MEM window: 0xd0000000-0xd03fffff
[    0.335278] pci 0000:00:1e.0:   PREFETCH window: 0x60000000-0x67ffffff
[    0.335304] pci 0000:00:1c.0: enabling device (0000 -> 0003)
[    0.335314]   alloc irq_desc for 16 on node -1
[    0.335320]   alloc kstat_irqs on node -1
[    0.335331] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.335344] pci 0000:00:1c.0: setting latency timer to 64
[    0.335357] pci 0000:00:1e.0: setting latency timer to 64
[    0.335377]   alloc irq_desc for 18 on node -1
[    0.335382]   alloc kstat_irqs on node -1
[    0.335390] pci 0000:02:06.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.335411]   alloc irq_desc for 19 on node -1
[    0.335415]   alloc kstat_irqs on node -1
[    0.335423] pci 0000:02:06.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.335437] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.335444] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.335451] pci_bus 0000:10: resource 0 io:  [0x3000-0x3fff]
[    0.335458] pci_bus 0000:10: resource 1 mem: [0x68000000-0x681fffff]
[    0.335465] pci_bus 0000:10: resource 2 pref mem [0x68200000-0x683fffff]
[    0.335473] pci_bus 0000:02: resource 0 io:  [0x4000-0x4fff]
[    0.335479] pci_bus 0000:02: resource 1 mem: [0xd0000000-0xd03fffff]
[    0.335486] pci_bus 0000:02: resource 2 pref mem [0x60000000-0x67ffffff]
[    0.335493] pci_bus 0000:02: resource 3 io:  [0x00-0xffff]
[    0.335500] pci_bus 0000:02: resource 4 mem: [0x000000-0xffffffff]
[    0.335507] pci_bus 0000:03: resource 0 io:  [0x4000-0x40ff]
[    0.335514] pci_bus 0000:03: resource 1 io:  [0x4400-0x44ff]
[    0.335521] pci_bus 0000:03: resource 2 pref mem [0x60000000-0x63ffffff]
[    0.335528] pci_bus 0000:03: resource 3 mem: [0x6c000000-0x6fffffff]
[    0.335535] pci_bus 0000:04: resource 0 io:  [0x4800-0x48ff]
[    0.335542] pci_bus 0000:04: resource 1 io:  [0x4c00-0x4cff]
[    0.335549] pci_bus 0000:04: resource 2 pref mem [0x64000000-0x67ffffff]
[    0.335556] pci_bus 0000:04: resource 3 mem: [0x70000000-0x73ffffff]
[    0.335628] NET: Registered protocol family 2
[    0.335828] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.336535] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.338125] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.338936] TCP: Hash tables configured (established 131072 bind 65536)
[    0.338945] TCP reno registered
[    0.339145] NET: Registered protocol family 1
[    0.339190] pci 0000:00:02.0: Boot video device
[    0.339654] cpufreq-nforce2: No nForce2 chipset.
[    0.339718] Scanning for low memory corruption every 60 seconds
[    0.340000] audit: initializing netlink socket (disabled)
[    0.340032] type=2000 audit(1276160523.339:1): initialized
[    0.365887] Trying to unpack rootfs image as initramfs...
[    0.392333] highmem bounce pool size: 64 pages
[    0.392346] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.400352] VFS: Disk quotas dquot_6.5.2
[    0.400486] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.408292] fuse init (API version 7.13)
[    0.408501] msgmni has been set to 1703
[    0.408943] alg: No test for stdrng (krng)
[    0.409071] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.409078] io scheduler noop registered
[    0.409083] io scheduler anticipatory registered
[    0.409088] io scheduler deadline registered
[    0.409186] io scheduler cfq registered (default)
[    0.409481]   alloc irq_desc for 24 on node -1
[    0.409486]   alloc kstat_irqs on node -1
[    0.409506] pcieport 0000:00:1c.0: irq 24 for MSI/MSI-X
[    0.409524] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.409709] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.409837] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.412472] ACPI: AC Adapter [C172] (off-line)
[    0.412659] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input0
[    0.412668] ACPI: Sleep Button [C1E8]
[    0.412774] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input1
[    0.412905] ACPI: Lid Switch [C1E9]
[    0.413022] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.413029] ACPI: Power Button [PWRF]
[    0.413492] fan PNP0C0B:00: registered as cooling_device0
[    0.413506] ACPI: Fan [C248] (off)
[    0.413882] fan PNP0C0B:01: registered as cooling_device1
[    0.413896] ACPI: Fan [C249] (off)
[    0.414274] fan PNP0C0B:02: registered as cooling_device2
[    0.414287] ACPI: Fan [C24A] (off)
[    0.414663] fan PNP0C0B:03: registered as cooling_device3
[    0.414676] ACPI: Fan [C24B] (off)
[    0.420801] Marking TSC unstable due to TSC halts in idle
[    0.420933] processor LNXCPU:00: registered as cooling_device4
[    0.424888] Switching to clocksource hpet
[    0.461627] thermal LNXTHERM:01: registered as thermal_zone0
[    0.461649] ACPI: Thermal Zone [TZ1] (31 C)
[    0.485267] thermal LNXTHERM:02: registered as thermal_zone1
[    0.485289] ACPI: Thermal Zone [TZ2] (23 C)
[    0.499457] thermal LNXTHERM:03: registered as thermal_zone2
[    0.499479] ACPI: Thermal Zone [TZ3] (19 C)
[    0.504058] thermal LNXTHERM:04: registered as thermal_zone3
[    0.504079] ACPI: Thermal Zone [TZ4] (64 C)
[    0.512571] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.512733] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.512945] serial8250: ttyS2 at I/O 0x3e8 (irq = 4) is a 16550A
[    0.513381] 00:02: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.513950]   alloc irq_desc for 22 on node -1
[    0.513956]   alloc kstat_irqs on node -1
[    0.513972] serial 0000:00:1e.3: PCI INT B -> GSI 22 (level, low) -> IRQ 22
[    0.513984] serial 0000:00:1e.3: PCI INT B disabled
[    0.517494] ACPI: Battery Slot [C173] (battery absent)
[    0.517517] isapnp: Scanning for PnP cards...
[    0.523422] brd: module loaded
[    0.524657] loop: module loaded
[    0.524856] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    0.525070] ata_piix 0000:00:1f.1: version 2.13
[    0.525095] ata_piix 0000:00:1f.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.525169] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.528387] scsi0 : ata_piix
[    0.528590] scsi1 : ata_piix
[    0.530305] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x2580 irq 14
[    0.530313] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x2588 irq 15
[    0.575038] Fixed MDIO Bus: probed
[    0.575124] PPP generic driver version 2.4.2
[    0.575224] tun: Universal TUN/TAP device driver, 1.6
[    0.575229] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.575404] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.575440]   alloc irq_desc for 23 on node -1
[    0.575445]   alloc kstat_irqs on node -1
[    0.575457] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.575487] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.575495] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.575562] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.575613] ehci_hcd 0000:00:1d.7: debug port 1
[    0.579501] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.583330] ata2: port disabled. ignoring.
[    0.586252] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xd0580000
[    0.608883] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.609110] usb usb1: configuration #1 chosen from 1 choice
[    0.609180] hub 1-0:1.0: USB hub found
[    0.609200] hub 1-0:1.0: 8 ports detected
[    0.609344] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.609381] uhci_hcd: USB Universal Host Controller Interface driver
[    0.609459] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.609473] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.609481] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.609559] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.609600] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00002000
[    0.609830] usb usb2: configuration #1 chosen from 1 choice
[    0.609936] hub 2-0:1.0: USB hub found
[    0.609951] hub 2-0:1.0: 2 ports detected
[    0.610043]   alloc irq_desc for 17 on node -1
[    0.610051]   alloc kstat_irqs on node -1
[    0.610063] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.610077] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.610084] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.610153] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.610204] uhci_hcd 0000:00:1d.1: irq 17, io base 0x00002020
[    0.610400] usb usb3: configuration #1 chosen from 1 choice
[    0.610462] hub 3-0:1.0: USB hub found
[    0.610476] hub 3-0:1.0: 2 ports detected
[    0.610566] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.610578] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.610585] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.610662] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.610711] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00002040
[    0.610930] usb usb4: configuration #1 chosen from 1 choice
[    0.610993] hub 4-0:1.0: USB hub found
[    0.611009] hub 4-0:1.0: 2 ports detected
[    0.611100] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.611112] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    0.611119] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    0.611188] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    0.611234] uhci_hcd 0000:00:1d.3: irq 19, io base 0x00002060
[    0.611427] usb usb5: configuration #1 chosen from 1 choice
[    0.611491] hub 5-0:1.0: USB hub found
[    0.611505] hub 5-0:1.0: 2 ports detected
[    0.611726] PNP: PS/2 Controller [PNP0303:C1C2,PNP0f13:C1C3] at 0x60,0x64 irq 1,12
[    0.613468] i8042.c: Detected active multiplexing controller, rev 1.1.
[    0.615954] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.615968] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    0.617361] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    0.617424] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    0.617480] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    0.617747] mice: PS/2 mouse device common for all mice
[    0.618133] rtc_cmos 00:08: RTC can wake from S4
[    0.618253] rtc_cmos 00:08: rtc core: registered rtc_cmos as rtc0
[    0.618294] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    0.618538] device-mapper: uevent: version 1.0.3
[    0.619740] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
[    0.623154] ACPI: Battery Slot [C174] (battery present)
[    0.625222] device-mapper: multipath: version 1.1.0 loaded
[    0.625230] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.625506] EISA: Probing bus 0 at eisa.0
[    0.625518] Cannot allocate resource for EISA slot 1
[    0.625524] Cannot allocate resource for EISA slot 2
[    0.625530] Cannot allocate resource for EISA slot 3
[    0.625535] Cannot allocate resource for EISA slot 4
[    0.625551] Cannot allocate resource for EISA slot 7
[    0.625561] EISA: Detected 0 cards.
[    0.628230] cpuidle: using governor ladder
[    0.628406] cpuidle: using governor menu
[    0.629404] TCP cubic registered
[    0.629783] NET: Registered protocol family 10
[    0.630788] lo: Disabled Privacy Extensions
[    0.631542] NET: Registered protocol family 17
[    0.640196] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    0.646148] Using IPI No-Shortcut mode
[    0.646247] PM: Resume from disk failed.
[    0.646261] registered taskstats version 1
[    0.646681]   Magic number: 14:663:19
[    0.646817] rtc_cmos 00:08: setting system clock to 2010-06-10 09:02:04 UTC (1276160524)
[    0.646821] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.646823] EDD information not available.
[    0.708542] ata1.00: ATA-6: FUJITSU MHV2060AH, 00830096, max UDMA/100
[    0.708547] ata1.00: 117210240 sectors, multi 16: LBA 
[    0.708589] ata1.01: ATAPI: DW-224E-C, A.8D, max MWDMA2
[    0.724423] ata1.00: configured for UDMA/100
[    0.740338] ata1.01: configured for MWDMA2
[    1.055456] Freeing initrd memory: 7785k freed
[    1.149756] isapnp: No Plug & Play device found
[    1.150004] scsi 0:0:0:0: Direct-Access     ATA      FUJITSU MHV2060A 0083 PQ: 0 ANSI: 5
[    1.150254] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.152436] sd 0:0:0:0: [sda] 117210240 512-byte logical blocks: (60.0 GB/55.8 GiB)
[    1.152494] sd 0:0:0:0: [sda] Write Protect is off
[    1.152497] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.152526] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.152641] scsi 0:0:1:0: CD-ROM            TEAC     DW-224E-C        A.8D PQ: 0 ANSI: 5
[    1.153195]  sda: sda1 sda2 <sr0: scsi3-mmc drive: 61x/61x writer cd/rw xa/form2 cdda tray
[    1.187621] Uniform CD-ROM driver Revision: 3.20
[    1.187740] sr 0:0:1:0: Attached scsi CD-ROM sr0
[    1.187796] sr 0:0:1:0: Attached scsi generic sg1 type 5
[    1.213745]  sda5 >
[    1.214044] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.214065] Freeing unused kernel memory: 656k freed
[    1.214560] Write protecting the kernel text: 4676k
[    1.214601] Write protecting the kernel read-only data: 1840k
[    1.232439] udev: starting version 151
[    1.260074] usb 3-2: new full speed USB device using uhci_hcd and address 2
[    1.424399] usb 3-2: configuration #1 chosen from 1 choice
[    1.553771] tg3.c:v3.102 (September 1, 2009)
[    1.553800] tg3 0000:02:0e.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.594703] eth0: Tigon3 [partno(BCM95705A50) rev 3003] (PCI:33MHz:32-bit) MAC address 00:15:60:be:2c:34
[    1.594709] eth0: attached PHY is 5705 (10/100/1000Base-T Ethernet) (WireSpeed[0])
[    1.594712] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[    1.594716] eth0: dma_rwctrl[763f0000] dma_mask[64-bit]
[    1.594748] ohci1394 0000:02:06.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    1.648088] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[22]  MMIO=[d0003000-d00037ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    1.678847] EXT4-fs (sda1): mounted filesystem with ordered data mode
[   23.765112] udev: starting version 151
[   23.849650] Adding 2441840k swap on /dev/sda5.  Priority:-1 extents:1 across:2441840k 
[   24.113094] Linux agpgart interface v0.103
[   24.132023] lib80211: common routines for IEEE802.11 drivers
[   24.132028] lib80211_crypt: registered algorithm 'NULL'
[   24.137430] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input5
[   24.137498] ACPI: Video Device [C055] (multi-head: yes  rom: no  post: no)
[   24.197870] intel_rng: FWH not detected
[   24.267529] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   24.267533] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   24.316199] lp: driver loaded but no devices found
[   24.414466] Bluetooth: Core ver 2.15
[   24.420086] NET: Registered protocol family 31
[   24.420089] Bluetooth: HCI device and connection manager initialized
[   24.420093] Bluetooth: HCI socket layer initialized
[   24.428887] Bluetooth: Generic Bluetooth USB driver ver 0.6
[   24.429150] usbcore: registered new interface driver btusb
[   24.436643] sdhci: Secure Digital Host Controller Interface driver
[   24.436650] sdhci: Copyright(c) Pierre Ossman
[   24.466843] agpgart-intel 0000:00:00.0: Intel 915GM Chipset
[   24.467541] agpgart-intel 0000:00:00.0: detected 7932K stolen memory
[   24.488539] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xc0000000
[   24.558470] [drm] Initialized drm 1.1.0 20060810
[   24.559081] parport_pc 00:04: reported by Plug and Play ACPI
[   24.559157] parport0: PC-style at 0x378 (0x778), irq 7, dma 1 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   24.621744] irda_init()
[   24.621766] NET: Registered protocol family 23
[   24.632395] type=1505 audit(1276156948.485:2):  operation="profile_load" pid=654 name="/sbin/dhclient3"
[   24.633092] type=1505 audit(1276156948.485:3):  operation="profile_load" pid=654 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   24.633471] type=1505 audit(1276156948.485:4):  operation="profile_load" pid=654 name="/usr/lib/connman/scripts/dhclient-script"
[   24.647695] sdhci-pci 0000:02:06.4: SDHCI controller found [104c:8034] (rev 0)
[   24.647721]   alloc irq_desc for 20 on node -1
[   24.647724]   alloc kstat_irqs on node -1
[   24.647733] sdhci-pci 0000:02:06.4: PCI INT D -> GSI 20 (level, low) -> IRQ 20
[   24.647813] Registered led device: mmc0::
[   24.647856] mmc0: SDHCI controller on PCI [0000:02:06.4] using PIO
[   24.648400] lp0: using parport0 (interrupt-driven).
[   24.656140] Registered led device: mmc1::
[   24.656203] mmc1: SDHCI controller on PCI [0000:02:06.4] using PIO
[   24.656275] Registered led device: mmc2::
[   24.656330] mmc2: SDHCI controller on PCI [0000:02:06.4] using PIO
[   24.656690] tifm_7xx1 0000:02:06.3: PCI INT D -> GSI 20 (level, low) -> IRQ 20
[   24.657042] yenta_cardbus 0000:02:06.0: CardBus bridge found [103c:099c]
[   24.657065] yenta_cardbus 0000:02:06.0: Enabling burst memory read transactions
[   24.657072] yenta_cardbus 0000:02:06.0: Using INTVAL to route CSC interrupts to PCI
[   24.657075] yenta_cardbus 0000:02:06.0: Routing CardBus interrupts to PCI
[   24.657082] yenta_cardbus 0000:02:06.0: TI: mfunc 0x01aa1b22, devctl 0x64
[   24.657194] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   24.657196] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   24.725001] ppdev: user-space parallel port driver
[   24.739433] found SMC SuperIO Chip (devid=0x7a rev=01 base=0x004e): LPC47N227
[   24.739456] smsc_superio_flat(): fir: 0x100, sir: 0x3e8, dma: 03, irq: 3, mode: 0x0e
[   24.739462] smsc_ircc_present: can't get sir_base of 0x3e8
[   24.785688] ip_tables: (C) 2000-2006 Netfilter Core Team
[   24.825004] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   24.825012] i915 0000:00:02.0: setting latency timer to 64
[   24.836993] [drm] set up 7M of stolen space
[   24.940302] yenta_cardbus 0000:02:06.0: ISA IRQ mask 0x0c78, PCI irq 18
[   24.940307] yenta_cardbus 0000:02:06.0: Socket status: 30000006
[   24.940315] yenta_cardbus 0000:02:06.0: pcmcia: parent PCI bridge I/O window: 0x4000 - 0x4fff
[   24.940319] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x4000-0x4fff: clean.
[   24.940567] yenta_cardbus 0000:02:06.0: pcmcia: parent PCI bridge Memory window: 0xd0000000 - 0xd03fffff
[   24.940571] yenta_cardbus 0000:02:06.0: pcmcia: parent PCI bridge Memory window: 0x60000000 - 0x67ffffff
[   24.943267]   alloc irq_desc for 21 on node -1
[   24.943271]   alloc kstat_irqs on node -1
[   24.943282] ipw2200 0000:02:04.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   24.944104] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   24.944162] ipw2200 0000:02:04.0: firmware: requesting ipw2200-bss.fw
[   25.047305] sr 0:0:1:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   25.047312] sr 0:0:1:0: [sr0] Sense Key : Illegal Request [current] 
[   25.047318] sr 0:0:1:0: [sr0] Add. Sense: Read of scrambled sector without authentication
[   25.047329] sr 0:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 04 00 00 00 02 00
[   25.047340] end_request: I/O error, dev sr0, sector 4096
[   25.047394] Buffer I/O error on device sr0, logical block 1024
[   25.047444] Buffer I/O error on device sr0, logical block 1025
[   25.053472] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[   25.054881] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Please use
[   25.054885] nf_conntrack.acct=1 kernel parameter, acct=1 nf_conntrack module option or
[   25.054887] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
[   25.071780] sr 0:0:1:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   25.071787] sr 0:0:1:0: [sr0] Sense Key : Illegal Request [current] 
[   25.071792] sr 0:0:1:0: [sr0] Add. Sense: Read of scrambled sector without authentication
[   25.071802] sr 0:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 04 00 00 00 02 00
[   25.071812] end_request: I/O error, dev sr0, sector 4096
[   25.071867] Buffer I/O error on device sr0, logical block 1024
[   25.071918] Buffer I/O error on device sr0, logical block 1025
[   25.104536] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x25a0b1, caps: 0xa04793/0x300000
[   25.104545] serio: Synaptics pass-through port at isa0060/serio4/input0
[   25.156085] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input6
[   25.286846] ip6_tables: (C) 2000-2006 Netfilter Core Team
[   25.331391] type=1505 audit(1276156949.181:5):  operation="profile_load" pid=796 name="/usr/share/gdm/guest-session/Xsession"
[   25.334964] type=1505 audit(1276156949.185:6):  operation="profile_replace" pid=797 name="/sbin/dhclient3"
[   25.335668] type=1505 audit(1276156949.185:7):  operation="profile_replace" pid=797 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   25.347137] [drm] initialized overlay support
[   25.670444] ipw2200: Detected geography ZZR (14 802.11bg channels, 0 802.11a channels)
[   25.672641] yenta_cardbus 0000:02:06.1: CardBus bridge found [103c:099c]
[   25.672670] yenta_cardbus 0000:02:06.1: Using CSCINT to route CSC interrupts to PCI
[   25.672673] yenta_cardbus 0000:02:06.1: Routing CardBus interrupts to PCI
[   25.672680] yenta_cardbus 0000:02:06.1: TI: mfunc 0x01aa1b22, devctl 0x64
[   25.750472] tg3 0000:02:0e.0: firmware: requesting tigon/tg3_tso5.bin
[   26.200703] yenta_cardbus 0000:02:06.1: ISA IRQ mask 0x0c78, PCI irq 19
[   26.200710] yenta_cardbus 0000:02:06.1: Socket status: 30000006
[   26.200715] pci_bus 0000:02: Raising subordinate bus# of parent bus (#02) from #04 to #07
[   26.200726] yenta_cardbus 0000:02:06.1: pcmcia: parent PCI bridge I/O window: 0x4000 - 0x4fff
[   26.200731] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x4000-0x4fff: clean.
[   26.200979] yenta_cardbus 0000:02:06.1: pcmcia: parent PCI bridge Memory window: 0xd0000000 - 0xd03fffff
[   26.200983] yenta_cardbus 0000:02:06.1: pcmcia: parent PCI bridge Memory window: 0x60000000 - 0x67ffffff
```

---

### Post by edanto on 2010-06-10
syslog is very very big!

Here's one of the last lines of it that might be relevant:

Jun 10 09:14:01 eoin-laptop wpa_supplicant[1119]: Association request to the driver failed

---

### Post by Peter09 on 2010-06-10
As its only your wireless card please can you provide the output of the commands. Do them without the hardwire card connected.
 
```
ifconfig
```
 
and (for a usb wirless card)
 
```
lsusb
```
 
for an onboard card
 
```
lshw -C network
```

---

### Post by anewguy on 2010-06-10
> **Peter09 said:**
> As its only your wireless card please can you provide the output of the commands. Do them without the hardwire card connected.
 
```
ifconfig
```
 
and (for a usb wirless card)
 
```
lsusb
```
 
for an onboard card
 
```
lshw -C network
```

If it's a laptop, as this appears to be, always have them do the lsusb anyway.  Some laptops internal wireless actually connects to the internal USB bus and it's the only way you'll see them.

Dave ;)

---

### Post by edanto on 2010-06-10
thanks guys.  Hope this tells us something!

I've been out all day at work, hence the delay.

ifconfig
```

eth0      Link encap:Ethernet  HWaddr 00:15:60:be:2c:34  
          inet6 addr: fe80::215:60ff:febe:2c34/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:93991 errors:0 dropped:0 overruns:0 frame:0
          TX packets:45716 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:54692073 (54.6 MB)  TX bytes:42393504 (42.3 MB)
          Interrupt:16 

eth1      Link encap:Ethernet  HWaddr 00:16:6f:7c:ee:1d  
          inet addr:192.168.1.7  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:6fff:fe7c:ee1d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:100 errors:11 dropped:11 overruns:0 frame:0
          TX packets:49 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:17167 (17.1 KB)  TX bytes:7421 (7.4 KB)
          Interrupt:21 Base address:0xc000 Memory:d0000000-d0000fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)
```

lsusb:
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 03f0:011d Hewlett-Packard Integrated Bluetooth Module
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Wireless interface
       product: PRO/Wireless 2200BG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 4
       bus info: pci@0000:02:04.0
       logical name: eth1
       version: 05
       serial: 00:16:6f:7c:ee:1d
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007) ip=192.168.1.7 latency=64 maxlatency=24 mingnt=3 multicast=yes wireless=IEEE 802.11g
       resources: irq:21 memory:d0000000-d0000fff
  *-network:1
       description: Ethernet interface
       product: NetXtreme BCM5705M_2 Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: e
       bus info: pci@0000:02:0e.0
       logical name: eth0
       version: 03
       serial: 00:15:60:be:2c:34
       width: 64 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.102 firmware=5705-v3.24 latency=64 mingnt=64 multicast=yes
       resources: irq:16 memory:d0020000-d002ffff

---

### Post by Peter09 on 2010-06-10
Well according to this you are connected to your network, you have an IP address.

inet addr:192.168.1.7  Bcast:192.168.1.255  Mask:255.255.255.

---

### Post by edanto on 2010-06-10
I see that indeed under eth1.  It's bizarre, it's working now on wireless, but I didn't do anything.

The wireless network icon that was in the top right of the screen is gone now - something is certainly a bit odd about the network settings.  Any way I can get that icon back?

---

### Post by Iowan on 2010-06-10
Revised thread title - hope it hasn't reverted...

The Network Manager icon  can sometimes be regained by installing a "Notification Area" to the panel.

---

### Post by edanto on 2010-06-18
Now, I'm back to the situation when no network connections at all are working!

I tried to add a notification area to the panel, but there is no sign of the network manager.

When I put in ifconfig, all I see is:

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:13652 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13652 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1045520 (1.0 MB)  TX bytes:1045520 (1.0 MB)

---

