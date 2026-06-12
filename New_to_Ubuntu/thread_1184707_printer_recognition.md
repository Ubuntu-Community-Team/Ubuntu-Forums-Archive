---
title: "printer recognition"
date: 2009-06-11
forum: New to Ubuntu
---

### Post by mpennell on 2009-06-11
First, Remember: I really should be writing from the "Utterly Clueless Forum" but since "Absolute Beginner's" is as low as it goes, here I am. My printer won't work. I searched the forum and found somebody with a similar prob and he was told to type the mysterious letters "dmsg" in the terminal. I did this myself and am pasting the result here in case one of you VERY kind and charitable hackers will be kind enough to give me some advice. I do note that part way down this long list I see my printer's name show up (Lexmark X5150). When I attempt to print, I get the usual motions, click PRINT and...nothing. The computer seems to act as if it printed just fine, but the printer itself shows no recognition whatsoever. 

Also, I just opened: Applications/System/Hardware drivers, and it told me No proprietary drivers found. Also, I went to Lexmark's page and all they had for linux was: "caldera openlinux." I tried to download it anyway and got: "cannot open n5wsu.hqx. Archive type not supported."


```
dmesg
mark@FamilyComputer:~$ dmesg
[    0.000000] BIOS EBDA/lowmem at: 0009fc00/0009fc00
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
[    0.000000]  BIOS-e820: 0000000000000000 - 00000000000a0000 (usable)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000000fe74000 (usable)
[    0.000000]  BIOS-e820: 000000000fe74000 - 000000000fe76000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000000fe76000 - 000000000fe97000 (ACPI data)
[    0.000000]  BIOS-e820: 000000000fe97000 - 000000000ff00000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee10000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.3 present.
[    0.000000] last_pfn = 0xfe74 max_arch_pfn = 0x100000
[    0.000000] Scanning 2 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 0000000000007000 (usable)
[    0.000000]  modified: 0000000000007000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 0000000000093000 (usable)
[    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000000fe74000 (usable)
[    0.000000]  modified: 000000000fe74000 - 000000000fe76000 (ACPI NVS)
[    0.000000]  modified: 000000000fe76000 - 000000000fe97000 (ACPI data)
[    0.000000]  modified: 000000000fe97000 - 000000000ff00000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee10000 (reserved)
[    0.000000]  modified: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000] kernel direct mapping tables up to fe74000 @ 10000-16000
[    0.000000] RAMDISK: 0f727000 - 0fe63faa
[    0.000000] ACPI: RSDP 000FEB80, 0014 (r0 DELL  )
[    0.000000] ACPI: RSDT 000FD22A, 0034 (r1 DELL    2400           7 ASL        61)
[    0.000000] ACPI: FACP 000FD25E, 0074 (r1 DELL    2400           7 ASL        61)
[    0.000000] ACPI: DSDT FFFCC0F1, 2404 (r1   DELL    dt_ex     1000 MSFT  100000D)
[    0.000000] ACPI: FACS 0FE74000, 0040
[    0.000000] ACPI: SSDT FFFCE4F5, 00A7 (r1   DELL    st_ex     1000 MSFT  100000D)
[    0.000000] ACPI: APIC 000FD2D2, 006C (r1 DELL    2400           7 ASL        61)
[    0.000000] ACPI: BOOT 000FD33E, 0028 (r1 DELL    2400           7 ASL        61)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 254MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 0fe74000
[    0.000000]   low ram: 00000000 - 0fe74000
[    0.000000]   bootmap 00012000 - 00013fd0
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 000fe74000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 000087c52c]    TEXT DATA BSS ==> [0000100000 - 000087c52c]
[    0.000000]   #4 [000f727000 - 000fe63faa]          RAMDISK ==> [000f727000 - 000fe63faa]
[    0.000000]   #5 [000087d000 - 0000881000]    INIT_PG_TABLE ==> [000087d000 - 0000881000]
[    0.000000]   #6 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #7 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]
[    0.000000]   #8 [0000012000 - 0000014000]          BOOTMAP ==> [0000012000 - 0000014000]
[    0.000000] found SMP MP-table at [c00fe710] 000fe710
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x0000fe74
[    0.000000]   HighMem  0x0000fe74 -> 0x0000fe74
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[4] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x00000007
[    0.000000]     0: 0x00000010 -> 0x00000093
[    0.000000]     0: 0x00000100 -> 0x0000fe74
[    0.000000] On node 0 totalpages: 65018
[    0.000000] free_area_init_node: node 0, pgdat c06d0f80, node_mem_map c1000000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3942 pages, LIFO batch:0
[    0.000000]   Normal zone: 477 pages used for memmap
[    0.000000]   Normal zone: 60567 pages, LIFO batch:15
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x01] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] disabled)
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 4 CPUs, 3 hotplug CPUs
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 0000000000007000 - 0000000000010000
[    0.000000] PM: Registered nosave memory: 0000000000093000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 10000000 (gap: ff00000:eed00000)
[    0.000000] PERCPU: Allocating 45056 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 4, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 64509
[    0.000000] Kernel command line: root=UUID=6565177b-6539-4857-b9b6-ea23cd342021 ro quiet splash 
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 1024 (order: 10, 4096 bytes)
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2657.718 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.004000] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
[    0.004000] allocated 1302800 bytes of page_cgroup
[    0.004000] please try cgroup_disable=memory option if you don't want
[    0.004000] Scanning for low memory corruption every 60 seconds
[    0.004000] Memory: 241132k/260560k available (4126k kernel code, 18844k reserved, 2208k data, 532k init, 0k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xd0674000 - 0xff3fe000   ( 749 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xcfe74000   ( 254 MB)
[    0.004000]       .init : 0xc0737000 - 0xc07bc000   ( 532 kB)
[    0.004000]       .data : 0xc0507a6f - 0xc072fe60   (2208 kB)
[    0.004000]       .text : 0xc0100000 - 0xc0507a6f   (4126 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] SLUB: Genslabs=12, HWalign=128, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.004012] Calibrating delay loop (skipped), value calculated using timer frequency.. 5315.43 BogoMIPS (lpj=10630872)
[    0.004036] Security Framework initialized
[    0.004044] SELinux:  Disabled at boot.
[    0.004066] AppArmor: AppArmor initialized
[    0.004081] Mount-cache hash table entries: 512
[    0.004257] Initializing cgroup subsys ns
[    0.004262] Initializing cgroup subsys cpuacct
[    0.004267] Initializing cgroup subsys memory
[    0.004277] Initializing cgroup subsys freezer
[    0.004297] CPU: Trace cache: 12K uops, L1 D cache: 8K
[    0.004302] CPU: L2 cache: 512K
[    0.004306] CPU: Hyper-Threading is disabled
[    0.004324] Checking 'hlt' instruction... OK.
[    0.020774] SMP alternatives: switching to UP code
[    0.128032] ACPI: Core revision 20080926
[    0.141317] ACPI: Checking initramfs for custom DSDT
[    0.486037] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.525729] CPU0: Intel(R) Pentium(R) 4 CPU 2.66GHz stepping 09
[    0.528002] Brought up 1 CPUs
[    0.528002] Total of 1 processors activated (5315.43 BogoMIPS).
[    0.528002] CPU0 attaching NULL sched-domain.
[    0.528002] net_namespace: 776 bytes
[    0.528002] Booting paravirtualized kernel on bare hardware
[    0.528002] Time: 11:20:17  Date: 06/11/09
[    0.528002] regulator: core version 0.5
[    0.528002] NET: Registered protocol family 16
[    0.528002] EISA bus registered
[    0.528002] ACPI: bus type pci registered
[    0.528002] PCI: PCI BIOS revision 2.10 entry at 0xfbbbf, last bus=1
[    0.528002] PCI: Using configuration type 1 for base access
[    0.528125] ACPI: EC: Look up EC in DSDT
[    0.552429] ACPI: Interpreter enabled
[    0.552437] ACPI: (supports S0 S1 S3 S4 S5)
[    0.552461] ACPI: Using IOAPIC for interrupt routing
[    0.585395] ACPI: No dock devices found.
[    0.585407] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.585460] pci 0000:00:00.0: reg 10 32bit mmio: [0xf0000000-0xf7ffffff]
[    0.585525] pci 0000:00:02.0: reg 10 32bit mmio: [0xe8000000-0xefffffff]
[    0.585532] pci 0000:00:02.0: reg 14 32bit mmio: [0xfeb80000-0xfebfffff]
[    0.585631] pci 0000:00:1d.0: reg 20 io port: [0xff80-0xff9f]
[    0.585682] pci 0000:00:1d.1: reg 20 io port: [0xff60-0xff7f]
[    0.585733] pci 0000:00:1d.2: reg 20 io port: [0xff40-0xff5f]
[    0.585793] pci 0000:00:1d.7: reg 10 32bit mmio: [0xffa80800-0xffa80bff]
[    0.585837] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.585842] pci 0000:00:1d.7: PME# disabled
[    0.585889] * The chipset may have PM-Timer Bug. Due to workarounds for a bug,
[    0.585891] * this clock source is slow. If you are sure your timer does not have
[    0.585892] * this bug, please use "acpi_pm_good" to disable the workaround
[    0.585932] HPET not enabled in BIOS. You might try hpet=force boot option
[    0.585940] pci 0000:00:1f.0: quirk: region 0800-087f claimed by ICH4 ACPI/GPIO/TCO
[    0.585943] pci 0000:00:1f.0: quirk: region 0880-08bf claimed by ICH4 GPIO
[    0.585964] pci 0000:00:1f.1: reg 10 io port: [0x1f0-0x1f7]
[    0.585973] pci 0000:00:1f.1: reg 14 io port: [0x3f4-0x3f7]
[    0.585980] pci 0000:00:1f.1: reg 18 io port: [0x170-0x177]
[    0.585986] pci 0000:00:1f.1: reg 1c io port: [0x374-0x377]
[    0.585993] pci 0000:00:1f.1: reg 20 io port: [0xffa0-0xffaf]
[    0.586001] pci 0000:00:1f.1: reg 24 32bit mmio: [0xfeb7fc00-0xfeb7ffff]
[    0.586053] pci 0000:00:1f.3: reg 20 io port: [0xeda0-0xedbf]
[    0.586097] pci 0000:00:1f.5: reg 10 io port: [0xee00-0xeeff]
[    0.586104] pci 0000:00:1f.5: reg 14 io port: [0xedc0-0xedff]
[    0.586111] pci 0000:00:1f.5: reg 18 32bit mmio: [0xfeb7fa00-0xfeb7fbff]
[    0.586118] pci 0000:00:1f.5: reg 1c 32bit mmio: [0xfeb7f900-0xfeb7f9ff]
[    0.586140] pci 0000:00:1f.5: PME# supported from D0 D3hot D3cold
[    0.586145] pci 0000:00:1f.5: PME# disabled
[    0.586191] pci 0000:01:05.0: reg 10 32bit mmio: [0xfe9f0000-0xfe9fffff]
[    0.586198] pci 0000:01:05.0: reg 14 io port: [0xdff8-0xdfff]
[    0.586229] pci 0000:01:05.0: PME# supported from D3hot D3cold
[    0.586233] pci 0000:01:05.0: PME# disabled
[    0.586267] pci 0000:01:09.0: reg 10 32bit mmio: [0xfe9ee000-0xfe9effff]
[    0.586294] pci 0000:01:09.0: reg 30 32bit mmio: [0xfea00000-0xfea03fff]
[    0.586304] pci 0000:01:09.0: supports D1 D2
[    0.586306] pci 0000:01:09.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.586310] pci 0000:01:09.0: PME# disabled
[    0.586341] pci 0000:00:1e.0: transparent bridge
[    0.586346] pci 0000:00:1e.0: bridge io port: [0xd000-0xdfff]
[    0.586351] pci 0000:00:1e.0: bridge 32bit mmio: [0xfe900000-0xfeafffff]
[    0.586363] bus 00 -> node 0
[    0.586370] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.586866] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[    0.733694] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 15)
[    0.734019] ACPI: PCI Interrupt Link [LNKB] (IRQs *3 4 5 6 7 9 10 11 12 15)
[    0.734342] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *9 10 11 12 15)
[    0.734665] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 *10 11 12 15)
[    0.734988] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
[    0.735308] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
[    0.735636] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
[    0.735961] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 7 9 10 11 12 15)
[    0.736160] ACPI: WMI: Mapper loaded
[    0.736423] SCSI subsystem initialized
[    0.736474] libata version 3.00 loaded.
[    0.736536] usbcore: registered new interface driver usbfs
[    0.736558] usbcore: registered new interface driver hub
[    0.736591] usbcore: registered new device driver usb
[    0.736744] PCI: Using ACPI for IRQ routing
[    0.736849] Bluetooth: Core ver 2.13
[    0.736849] NET: Registered protocol family 31
[    0.736849] Bluetooth: HCI device and connection manager initialized
[    0.736849] Bluetooth: HCI socket layer initialized
[    0.736849] NET: Registered protocol family 8
[    0.736849] NET: Registered protocol family 20
[    0.736849] NetLabel: Initializing
[    0.736849] NetLabel:  domain hash size = 128
[    0.736849] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.736849] NetLabel:  unlabeled traffic allowed by default
[    0.736849] AppArmor: AppArmor Filesystem Enabled
[    0.736849] pnp: PnP ACPI init
[    0.736849] ACPI: bus type pnp registered
[    0.758883] pnp 00:0b: io resource (0x800-0x85f) overlaps 0000:00:1f.0 BAR 7 (0x800-0x87f), disabling
[    0.758887] pnp 00:0b: io resource (0x860-0x8ff) overlaps 0000:00:1f.0 BAR 7 (0x800-0x87f), disabling
[    0.759612] pnp: PnP ACPI: found 12 devices
[    0.759615] ACPI: ACPI bus type pnp unregistered
[    0.759620] PnPBIOS: Disabled by ACPI PNP
[    0.759632] system 00:00: iomem range 0x0-0x9ffff could not be reserved
[    0.759637] system 00:00: iomem range 0x100000-0xffffff could not be reserved
[    0.759640] system 00:00: iomem range 0x1000000-0xfe73fff could not be reserved
[    0.759643] system 00:00: iomem range 0xc0000-0xfffff could not be reserved
[    0.759646] system 00:00: iomem range 0xfec00000-0xfec0ffff has been reserved
[    0.759649] system 00:00: iomem range 0xfee00000-0xfee0ffff has been reserved
[    0.759652] system 00:00: iomem range 0xfecf0000-0xfecf0fff has been reserved
[    0.759655] system 00:00: iomem range 0xffb00000-0xffbfffff has been reserved
[    0.759662] system 00:00: iomem range 0xffc00000-0xffffffff has been reserved
[    0.759674] system 00:0b: ioport range 0xc00-0xc7f has been reserved
[    0.794461] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:01
[    0.794465] pci 0000:00:1e.0:   IO window: 0xd000-0xdfff
[    0.794472] pci 0000:00:1e.0:   MEM window: 0xfe900000-0xfeafffff
[    0.794477] pci 0000:00:1e.0:   PREFETCH window: 0x00000010000000-0x000000100fffff
[    0.794492] pci 0000:00:1e.0: setting latency timer to 64
[    0.794497] bus: 00 index 0 io port: [0x00-0xffff]
[    0.794500] bus: 00 index 1 mmio: [0x000000-0xffffffff]
[    0.794503] bus: 01 index 0 io port: [0xd000-0xdfff]
[    0.794506] bus: 01 index 1 mmio: [0xfe900000-0xfeafffff]
[    0.794508] bus: 01 index 2 mmio: [0x10000000-0x100fffff]
[    0.794510] bus: 01 index 3 io port: [0x00-0xffff]
[    0.794513] bus: 01 index 4 mmio: [0x000000-0xffffffff]
[    0.794525] NET: Registered protocol family 2
[    0.794684] IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
[    0.794949] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
[    0.795005] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[    0.795057] TCP: Hash tables configured (established 8192 bind 8192)
[    0.795060] TCP reno registered
[    0.795177] NET: Registered protocol family 1
[    0.795327] checking if image is initramfs... it is
[    1.296060] Switched to high resolution mode on CPU 0
[    1.478771] Freeing initrd memory: 7411k freed
[    1.478840] Simple Boot Flag value 0x87 read from CMOS RAM was invalid
[    1.478843] Simple Boot Flag at 0x7a set to 0x1
[    1.478884] cpufreq: No nForce2 chipset.
[    1.479108] audit: initializing netlink socket (disabled)
[    1.479137] type=2000 audit(1244719217.476:1): initialized
[    1.486510] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.487868] VFS: Disk quotas dquot_6.5.1
[    1.487936] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.488684] fuse init (API version 7.10)
[    1.488781] msgmni has been set to 485
[    1.489002] alg: No test for stdrng (krng)
[    1.489018] io scheduler noop registered
[    1.489020] io scheduler anticipatory registered
[    1.489023] io scheduler deadline registered
[    1.489047] io scheduler cfq registered (default)
[    1.489066] pci 0000:00:02.0: Boot video device
[    1.506974] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.506986] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.507129] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.507132] ACPI: Power Button (FF) [PWRF]
[    1.507186] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    1.507194] ACPI: Power Button (CM) [VBTN]
[    1.507480] processor ACPI_CPU:00: registered as cooling_device0
[    1.530363] isapnp: Scanning for PnP cards...
[    1.884227] isapnp: No Plug & Play device found
[    1.885879] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.885977] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.886387] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.887323] brd: module loaded
[    1.887739] loop: module loaded
[    1.887841] Fixed MDIO Bus: probed
[    1.887849] PPP generic driver version 2.4.2
[    1.887929] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    1.887969] Driver 'sd' needs updating - please use bus_type methods
[    1.887982] Driver 'sr' needs updating - please use bus_type methods
[    1.888105] ata_piix 0000:00:1f.1: version 2.12
[    1.888131] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.888204] ata_piix 0000:00:1f.1: setting latency timer to 64
[    1.888350] scsi0 : ata_piix
[    1.888474] scsi1 : ata_piix
[    1.888515] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    1.888519] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    2.108492] ata1.00: ATA-6: ST340014A, 3.16, max UDMA/100
[    2.108495] ata1.00: 78125000 sectors, multi 8: LBA48 
[    2.124428] ata1.00: configured for UDMA/100
[    2.288296] ata2.00: ATAPI: SAMSUNG CD-R/RW SW-252S, R901, max UDMA/33
[    2.304252] ata2.00: configured for UDMA/33
[    2.304779] scsi 0:0:0:0: Direct-Access     ATA      ST340014A        3.16 PQ: 0 ANSI: 5
[    2.304909] sd 0:0:0:0: [sda] 78125000 512-byte hardware sectors: (40.0 GB/37.2 GiB)
[    2.304930] sd 0:0:0:0: [sda] Write Protect is off
[    2.304933] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.304964] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.305045] sd 0:0:0:0: [sda] 78125000 512-byte hardware sectors: (40.0 GB/37.2 GiB)
[    2.305062] sd 0:0:0:0: [sda] Write Protect is off
[    2.305065] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.305094] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.305099]  sda: sda1 sda2 < sda5 >
[    2.344640] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.344711] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.345593] scsi 1:0:0:0: CD-ROM            SAMSUNG  CD-R/RW SW-252S  R901 PQ: 0 ANSI: 5
[    2.349453] sr0: scsi3-mmc drive: 48x/16x writer cd/rw xa/form2 cdda tray
[    2.349458] Uniform CD-ROM driver Revision: 3.20
[    2.349575] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.349627] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.350341] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.350374] ehci_hcd 0000:00:1d.7: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    2.350404] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    2.350409] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    2.350488] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    2.354404] ehci_hcd 0000:00:1d.7: debug port 1
[    2.354411] ehci_hcd 0000:00:1d.7: cache line size of 128 is not supported
[    2.354428] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xffa80800
[    2.368011] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    2.368106] usb usb1: configuration #1 chosen from 1 choice
[    2.368142] hub 1-0:1.0: USB hub found
[    2.368154] hub 1-0:1.0: 6 ports detected
[    2.368282] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.368305] uhci_hcd: USB Universal Host Controller Interface driver
[    2.368358] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.368367] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    2.368371] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    2.368427] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    2.368457] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000ff80
[    2.368545] usb usb2: configuration #1 chosen from 1 choice
[    2.368574] hub 2-0:1.0: USB hub found
[    2.368585] hub 2-0:1.0: 2 ports detected
[    2.368681] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    2.368688] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    2.368692] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    2.368740] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    2.368768] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000ff60
[    2.368855] usb usb3: configuration #1 chosen from 1 choice
[    2.368884] hub 3-0:1.0: USB hub found
[    2.368896] hub 3-0:1.0: 2 ports detected
[    2.368991] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    2.368998] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    2.369002] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    2.369050] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    2.369079] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000ff40
[    2.369169] usb usb4: configuration #1 chosen from 1 choice
[    2.369198] hub 4-0:1.0: USB hub found
[    2.369209] hub 4-0:1.0: 2 ports detected
[    2.369350] usbcore: registered new interface driver libusual
[    2.369395] usbcore: registered new interface driver usbserial
[    2.369409] USB Serial support registered for generic
[    2.369427] usbcore: registered new interface driver usbserial_generic
[    2.369430] usbserial: USB Serial Driver core
[    2.369489] PNP: PS/2 Controller [PNP0303:KBD,PNP0f13:MOU] at 0x60,0x64 irq 1,12
[    2.372347] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.372355] serio: i8042 AUX port at 0x60,0x64 irq 12
[    2.372504] mice: PS/2 mouse device common for all mice
[    2.372655] rtc_cmos 00:05: RTC can wake from S4
[    2.372703] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    2.372726] rtc0: alarms up to one day, 242 bytes nvram
[    2.372830] device-mapper: uevent: version 1.0.3
[    2.372973] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[    2.373034] device-mapper: multipath: version 1.0.5 loaded
[    2.373037] device-mapper: multipath round-robin: version 1.0.0 loaded
[    2.373140] EISA: Probing bus 0 at eisa.0
[    2.373178] EISA: Detected 0 cards.
[    2.373212] cpuidle: using governor ladder
[    2.373215] cpuidle: using governor menu
[    2.373836] TCP cubic registered
[    2.373918] NET: Registered protocol family 10
[    2.374435] lo: Disabled Privacy Extensions
[    2.374786] NET: Registered protocol family 17
[    2.374811] Bluetooth: L2CAP ver 2.11
[    2.374813] Bluetooth: L2CAP socket layer initialized
[    2.374816] Bluetooth: SCO (Voice Link) ver 0.6
[    2.374819] Bluetooth: SCO socket layer initialized
[    2.374869] Bluetooth: RFCOMM socket layer initialized
[    2.374881] Bluetooth: RFCOMM TTY layer initialized
[    2.374883] Bluetooth: RFCOMM ver 1.10
[    2.374946] Using IPI No-Shortcut mode
[    2.375069] registered taskstats version 1
[    2.375202]   Magic number: 13:262:327
[    2.375293] rtc_cmos 00:05: setting system clock to 2009-06-11 11:20:19 UTC (1244719219)
[    2.375298] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.375300] EDD information not available.
[    2.376087] Freeing unused kernel memory: 532k freed
[    2.376203] Write protecting the kernel text: 4128k
[    2.376244] Write protecting the kernel read-only data: 1532k
[    2.412961] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    2.792047] usb 1-4: new high speed USB device using ehci_hcd and address 3
[    2.927782] FDC 0 is a post-1991 82077
[    2.947752] usb 1-4: configuration #1 chosen from 1 choice
[    2.956113] Initializing USB Mass Storage driver...
[    2.968049] scsi2 : SCSI emulation for USB Mass Storage devices
[    2.970237] usbcore: registered new interface driver usb-storage
[    2.970244] USB Mass Storage support registered.
[    2.970340] usb-storage: device found at 3
[    2.970343] usb-storage: waiting for device to settle before scanning
[    3.188048] usb 2-1: new full speed USB device using uhci_hcd and address 2
[    3.255798] b44 0000:01:09.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    3.312115] ssb: Sonics Silicon Backplane found on PCI device 0000:01:09.0
[    3.312142] b44.c:v2.0
[    3.332809] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:0f:1f:50:0e:f5
[    3.402465] usb 2-1: configuration #1 chosen from 1 choice
[    4.930868] usbcore: registered new interface driver hiddev
[    4.951322] generic-usb 0003:043D:0065.0001: hiddev96,hidraw0: USB HID v1.00 Device [Lexmark Lexmark X5100 Series] on usb-0000:00:1d.0-1/input2
[    4.951347] usbcore: registered new interface driver usbhid
[    4.951352] usbhid: v2.6:USB HID core driver
[    5.284548] PM: Starting manual resume from disk
[    5.284554] PM: Resume from partition 8:5
[    5.284556] PM: Checking hibernation image.
[    5.284898] PM: Resume from disk failed.
[    5.360029] kjournald starting.  Commit interval 5 seconds
[    5.360047] EXT3-fs: mounted filesystem with ordered data mode.
[    7.976028] usb-storage: device scan complete
[    8.003632] scsi 2:0:0:0: Direct-Access     Maxtor 6 L100P0           BAH4 PQ: 0 ANSI: 0
[    8.004869] sd 2:0:0:0: [sdb] 195813072 512-byte hardware sectors: (100 GB/93.3 GiB)
[    8.005608] sd 2:0:0:0: [sdb] Write Protect is off
[    8.005611] sd 2:0:0:0: [sdb] Mode Sense: 03 00 00 00
[    8.005614] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[    8.006488] sd 2:0:0:0: [sdb] 195813072 512-byte hardware sectors: (100 GB/93.3 GiB)
[    8.007357] sd 2:0:0:0: [sdb] Write Protect is off
[    8.007360] sd 2:0:0:0: [sdb] Mode Sense: 03 00 00 00
[    8.007362] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[    8.007366]  sdb: sdb1
[    8.040164] sd 2:0:0:0: [sdb] Attached SCSI disk
[    8.040250] sd 2:0:0:0: Attached scsi generic sg2 type 0
[   12.258341] udev: starting version 141
[   12.570329] Linux agpgart interface v0.103
[   12.575033] agpgart-intel 0000:00:00.0: Intel 830M Chipset
[   12.575241] agpgart-intel 0000:00:00.0: detected 892K stolen memory
[   12.577249] agpgart-intel 0000:00:00.0: AGP aperture is 128M @ 0xe8000000
[   12.649669] parport_pc 00:0a: reported by Plug and Play ACPI
[   12.649722] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,ECP]
[   12.849298] usblp0: USB Bidirectional printer dev 2 if 1 alt 0 proto 2 vid 0x043D pid 0x0065
[   12.849329] usbcore: registered new interface driver usblp
[   13.220954] intel_rng: FWH not detected
[   13.262155] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   13.303368] iTCO_vendor_support: vendor-support=0
[   13.305545] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05
[   13.305720] iTCO_wdt: Found a ICH4 TCO device (Version=1, TCOBASE=0x0860)
[   13.305823] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   13.776335] input: PC Speaker as /devices/platform/pcspkr/input/input4
[   13.896859] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[   14.038989] Intel ICH 0000:00:1f.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   14.039172] Intel ICH 0000:00:1f.5: setting latency timer to 64
[   14.250146] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   14.389943] psmouse serio1: ID: 10 00 64<6>intel8x0_measure_ac97_clock: measured 56496 usecs
[   14.461598] intel8x0: clocking to 48000
[   14.949749] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input5
[   15.068849] ppdev: user-space parallel port driver
[   16.193396] lp0: using parport0 (interrupt-driven).
[   16.826119] Adding 730916k swap on /dev/sda5.  Priority:-1 extents:1 across:730916k
[   17.692717] EXT3 FS on sda1, internal journal
[   19.719482] type=1505 audit(1244719236.840:2): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=1889
[   19.719754] type=1505 audit(1244719236.840:3): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=1889
[   19.719829] type=1505 audit(1244719236.840:4): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=1889
[   19.719882] type=1505 audit(1244719236.840:5): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=1889
[   19.881457] type=1505 audit(1244719237.004:6): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=1894
[   19.881817] type=1505 audit(1244719237.004:7): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=1894
[   19.919371] type=1505 audit(1244719237.040:8): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=1898
[   23.014416] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   23.014420] Bluetooth: BNEP filters: protocol multicast
[   23.196886] Bridge firewalling registered
[   26.569148] [drm] Initialized drm 1.1.0 20060810
[   26.582292] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   26.582300] pci 0000:00:02.0: setting latency timer to 64
[   26.582524] [drm] Initialized i915 1.6.0 20080730 on minor 0
[   26.586506] [drm:i915_setparam] *ERROR* unknown parameter 4
[   26.586540] [drm:i915_getparam] *ERROR* Unknown parameter 6
[   27.215050] [drm:i915_getparam] *ERROR* Unknown parameter 6
[   27.520372] ppdev0: registered pardevice
[   27.568298] ppdev0: unregistered pardevice
[   28.884460] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   32.816167] b44: eth0: Link is up at 100 Mbps, full duplex.
[   32.816172] b44: eth0: Flow control is off for TX and off for RX.
[   32.816257] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   43.208019] eth0: no IPv6 routers present
[ 1493.059107] [drm:i915_getparam] *ERROR* Unknown parameter 6
[ 1502.915984] [drm:i915_getparam] *ERROR* Unknown parameter 6
[ 2102.122547] [drm:i915_getparam] *ERROR* Unknown parameter 6
[ 4371.311284] [drm:i915_getparam] *ERROR* Unknown parameter 6
[ 4383.070590] [drm:i915_getparam] *ERROR* Unknown parameter 6
[ 4975.497168] [drm:i915_getparam] *ERROR* Unknown parameter 6
[ 5574.695357] [drm:i915_getparam] *ERROR* Unknown parameter 6
[ 6185.621410] [drm:i915_getparam] *ERROR* Unknown parameter 6
[12735.971088] [drm:i915_getparam] *ERROR* Unknown parameter 6
[12739.243950] [drm:i915_getparam] *ERROR* Unknown parameter 6
[13337.667072] [drm:i915_getparam] *ERROR* Unknown parameter 6
[14559.195649] [drm:i915_getparam] *ERROR* Unknown parameter 6
[14565.008491] [drm:i915_getparam] *ERROR* Unknown parameter 6
mark@FamilyComputer:~$ dmesg
```

---

### Post by oldos2er on 2009-06-11
I did some googling and found this thread: [http://ubuntuforums.org/showthread.php?p=3412992&posted=1#post3412992](http://ubuntuforums.org/showthread.php?p=3412992&posted=1#post3412992)

 Maybe that will help get you started.

---

### Post by mpennell on 2009-06-11
Thanks, Ann!
I'll check it out in a bit.
:p

actually, I just took a look-- you found the jackpot! Now this ignoramus (that would be me) needs to interpret what is being said...

---

### Post by mpennell on 2009-06-11
Um, does anyone want to try to explain such a thing in really simple terms? Like the Denzel Washington character in "Philadelphia": "Tell it to me like I'm a six year old."

Like, for just one example: "untar"... what does it mean to untar... I'm getting lost.

I need to read a book about all this!:confused:

(I may also have to invite James the Super Cool IT Guy over. Will free pizza do it? Probably!)

---

### Post by sti11_learning on 2009-06-11
Tar is an archiving tool and file format. In this case archiving means that a bunch of little files are put together into one big file. This is very similar to formats like zip and 7z but, tar itself does not compress (decrease the overall size of the file.) the contents and therefore is generally coupled with gzip or bzip. Any tar archive is known as a tarball and a tarball will generally end in either .tar.gz or .tar.bz2 depending on what was used to compress it.

To untar a tarball you would either use the archive manager and extract from there, or cd to the directory containing the tarball and run "tar -xvzf" ***Filename*** if it ends .tar.gz or "tar -xvjf" ***Filename*** if it ends in .tar.bz2 (Both without quotes.)

---

### Post by philinux on 2009-06-11
Or just double click the tar file and from the pop up window choose extract.

---

