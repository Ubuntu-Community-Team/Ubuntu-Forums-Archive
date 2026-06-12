---
title: "Shut down problem"
date: 2010-12-09
forum: New to Ubuntu
---

### Post by SungSean on 2010-12-09
Having problem shutting down Xubuntu OS. It does not shut down and screen turns black and Caps Lock and Scroll Lock keep blinking. To shut down the system I have to hard-shutdown by pressing and holding the power button. Help would be appreciated.;)

---

### Post by ubudog on 2010-12-09
Open a terminal and type:
```
dmesg
```

Post the output here.  This can show any recent errors.  It is very useful.

---

### Post by SungSean on 2010-12-09
seanc@seanc-desktop:~$ dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.32-26-generic (buildd@rothera) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #48-Ubuntu SMP Wed Nov 24 09:00:03 UTC 2010 (Ubuntu 2.6.32-26.48-generic 2.6.32.24+drm33.11)
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
[    0.000000]  BIOS-e820: 0000000000100000 - 000000000fee06c0 (usable)
[    0.000000]  BIOS-e820: 000000000fee06c0 - 000000000fee66c0 (ACPI data)
[    0.000000]  BIOS-e820: 000000000fee66c0 - 000000000feee700 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000000feee700 - 0000000010000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.3 present.
[    0.000000] last_pfn = 0xfee0 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-DFFFF uncachable
[    0.000000]   E0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask FF0000000 write-back
[    0.000000]   1 base 00FF00000 mask FFFF00000 uncachable
[    0.000000]   2 disabled
[    0.000000]   3 disabled
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
[    0.000000]  modified: 0000000000100000 - 000000000fee06c0 (usable)
[    0.000000]  modified: 000000000fee06c0 - 000000000fee66c0 (ACPI data)
[    0.000000]  modified: 000000000fee66c0 - 000000000feee700 (ACPI NVS)
[    0.000000]  modified: 000000000feee700 - 0000000010000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-000000000fee0000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 000fc00000 page 2M
[    0.000000]  000fc00000 - 000fee0000 page 4k
[    0.000000] kernel direct mapping tables up to fee0000 @ 7000-c000
[    0.000000] RAMDISK: 0b7cf000 - 0bf67728
[    0.000000] ACPI: RSDP 000fdfe0 00014 (v00 IBM   )
[    0.000000] ACPI: RSDT 0fee6640 0002C (v01 IBM    CDTPWSPI 00001010 IBM  00000000)
[    0.000000] ACPI: FACP 0fee65c0 00074 (v01 IBM    CDTPWSPI 00001010 IBM  00000000)
[    0.000000] ACPI: DSDT 0fee1d00 043FC (v01 IBM    CDTPWSPI 00001000 MSFT 01000007)
[    0.000000] ACPI: FACS 0feee680 00040
[    0.000000] ACPI: APIC 0fee6540 0005A (v01 IBM    CDTPWSPI 00001010 IBM  00000000)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 254MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 0fee0000
[    0.000000]   low ram: 0 - 0fee0000
[    0.000000]   node 0 low ram: 00000000 - 0fee0000
[    0.000000]   node 0 bootmap 00008000 - 00009fdc
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 000fee0000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008dced8]    TEXT DATA BSS ==> [0000100000 - 00008dced8]
[    0.000000]   #4 [000b7cf000 - 000bf67728]          RAMDISK ==> [000b7cf000 - 000bf67728]
[    0.000000]   #5 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #6 [00008dd000 - 00008e00fc]              BRK ==> [00008dd000 - 00008e00fc]
[    0.000000]   #7 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
[    0.000000]   #8 [0000008000 - 000000a000]          BOOTMAP ==> [0000008000 - 000000a000]
[    0.000000] found SMP MP-table at [c009fe00] 9fe00
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x0000fee0
[    0.000000]   HighMem  0x0000fee0 -> 0x0000fee0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0000fee0
[    0.000000] On node 0 totalpages: 65147
[    0.000000] free_area_init_node: node 0, pgdat c079a760, node_mem_map c1001000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3963 pages, LIFO batch:0
[    0.000000]   Normal zone: 478 pages used for memmap
[    0.000000]   Normal zone: 60674 pages, LIFO batch:15
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0xf808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
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
[    0.000000] Allocating PCI resources starting at 10000000 (gap: 10000000:eec00000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @c1400000 s36056 r0 d21288 u4194304
[    0.000000] pcpu-alloc: s36056 r0 d21288 u4194304 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 64637
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-26-generic root=UUID=089a8de6-c990-48f9-93af-3ab133a37547 ro quiet splash
[    0.000000] PID hash table entries: 1024 (order: 0, 4096 bytes)
[    0.000000] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.000000] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 1304960 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (00000000:00000000)
[    0.000000] Memory: 240772k/260992k available (4682k kernel code, 19476k reserved, 2121k data, 656k init, 0k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xd06e0000 - 0xff7fe000   ( 753 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xcfee0000   ( 254 MB)
[    0.000000]       .init : 0xc07a5000 - 0xc0849000   ( 656 kB)
[    0.000000]       .data : 0xc0592847 - 0xc07a4e68   (2121 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0592847   (4682 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=32, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] NR_IRQS:2304 nr_irqs:256
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 863.857 MHz processor.
[    0.008011] Calibrating delay loop (skipped), value calculated using timer frequency.. 1727.71 BogoMIPS (lpj=3455428)
[    0.008061] Security Framework initialized
[    0.008138] AppArmor: AppArmor initialized
[    0.008161] Mount-cache hash table entries: 512
[    0.008508] Initializing cgroup subsys ns
[    0.008522] Initializing cgroup subsys cpuacct
[    0.008534] Initializing cgroup subsys memory
[    0.008560] Initializing cgroup subsys devices
[    0.008569] Initializing cgroup subsys freezer
[    0.008577] Initializing cgroup subsys net_cls
[    0.008637] CPU: L1 I cache: 16K, L1 D cache: 16K
[    0.008646] CPU: L2 cache: 256K
[    0.008660] mce: CPU supports 5 MCE banks
[    0.008701] Performance Events: p6 PMU driver.
[    0.008759] ... version:                0
[    0.008765] ... bit width:              32
[    0.008771] ... generic registers:      2
[    0.008777] ... value mask:             00000000ffffffff
[    0.008784] ... max period:             000000007fffffff
[    0.008790] ... fixed-purpose events:   0
[    0.008797] ... event mask:             0000000000000003
[    0.008810] Checking 'hlt' instruction... OK.
[    0.025432] SMP alternatives: switching to UP code
[    0.039586] Freeing SMP alternatives: 19k freed
[    0.039657] ACPI: Core revision 20090903
[    0.050626] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.050662] ftrace: allocating 21794 entries in 43 pages
[    0.056347] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.056709] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.099512] CPU0: Intel Pentium III (Coppermine) stepping 06
[    0.100001] Brought up 1 CPUs
[    0.100001] Total of 1 processors activated (1727.71 BogoMIPS).
[    0.100001] CPU0 attaching NULL sched-domain.
[    0.100001] devtmpfs: initialized
[    0.100001] regulator: core version 0.5
[    0.100001] Time: 11:26:26  Date: 12/09/10
[    0.100001] NET: Registered protocol family 16
[    0.100001] EISA bus registered
[    0.100001] ACPI: bus type pci registered
[    0.100942] PCI: PCI BIOS revision 2.10 entry at 0xfd55c, last bus=1
[    0.100950] PCI: Using configuration type 1 for base access
[    0.104025] bio: create slab <bio-0> at 0
[    0.105452] ACPI: EC: Look up EC in DSDT
[    0.119353] ACPI: Interpreter enabled
[    0.119370] ACPI: (supports S0 S1 S3 S4 S5)
[    0.119444] ACPI: Using IOAPIC for interrupt routing
[    0.129347] ACPI: No dock devices found.
[    0.129408] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.129589] pci 0000:00:02.0: reg 10 32bit mmio pref: [0xf8000000-0xfbffffff]
[    0.129603] pci 0000:00:02.0: reg 14 32bit mmio: [0xfea80000-0xfeafffff]
[    0.129795] pci 0000:00:1f.0: quirk: region f800-f87f claimed by ICH4 ACPI/GPIO/TCO
[    0.129805] pci 0000:00:1f.0: quirk: region fc00-fc3f claimed by ICH4 GPIO
[    0.129866] pci 0000:00:1f.1: reg 20 io port: [0xfff0-0xffff]
[    0.129943] pci 0000:00:1f.2: reg 20 io port: [0xfb00-0xfb1f]
[    0.130024] pci 0000:00:1f.3: reg 20 io port: [0xfe00-0xfe0f]
[    0.130081] pci 0000:00:1f.5: reg 10 io port: [0xf000-0xf0ff]
[    0.130095] pci 0000:00:1f.5: reg 14 io port: [0xf400-0xf43f]
[    0.130199] pci 0000:01:08.0: reg 10 32bit mmio: [0xfebfc000-0xfebfcfff]
[    0.130213] pci 0000:01:08.0: reg 14 io port: [0x78c0-0x78ff]
[    0.130264] pci 0000:01:08.0: supports D1 D2
[    0.130271] pci 0000:01:08.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.130282] pci 0000:01:08.0: PME# disabled
[    0.130335] pci 0000:01:0d.0: reg 10 io port: [0x78a0-0x78bf]
[    0.130391] pci 0000:01:0d.0: supports D1 D2
[    0.130438] pci 0000:01:0d.1: reg 10 io port: [0x7898-0x789f]
[    0.130494] pci 0000:01:0d.1: supports D1 D2
[    0.130550] pci 0000:01:0e.0: reg 10 32bit mmio: [0xfebfd000-0xfebfdfff]
[    0.130606] pci 0000:01:0e.0: PME# supported from D0 D1 D3hot D3cold
[    0.130615] pci 0000:01:0e.0: PME# disabled
[    0.130662] pci 0000:01:0e.1: reg 10 32bit mmio: [0xfebfe000-0xfebfefff]
[    0.130718] pci 0000:01:0e.1: PME# supported from D0 D1 D3hot D3cold
[    0.130728] pci 0000:01:0e.1: PME# disabled
[    0.130776] pci 0000:01:0e.2: reg 10 32bit mmio: [0xfebff000-0xfebfffff]
[    0.130832] pci 0000:01:0e.2: PME# supported from D0 D1 D3hot D3cold
[    0.130841] pci 0000:01:0e.2: PME# disabled
[    0.130899] pci 0000:01:0e.3: reg 10 32bit mmio: [0xfebfbf00-0xfebfbfff]
[    0.130960] pci 0000:01:0e.3: PME# supported from D0 D3hot D3cold
[    0.130970] pci 0000:01:0e.3: PME# disabled
[    0.131015] pci 0000:00:1e.0: transparent bridge
[    0.131025] pci 0000:00:1e.0: bridge io port: [0x7000-0x7fff]
[    0.131036] pci 0000:00:1e.0: bridge 32bit mmio: [0xfeb00000-0xfebfffff]
[    0.131055] pci_bus 0000:00: on NUMA node 0
[    0.131068] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.131416] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI2._PRT]
[    0.145466] ACPI: PCI Interrupt Link [PIN1] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.145829] ACPI: PCI Interrupt Link [PIN2] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.146186] ACPI: PCI Interrupt Link [PIN3] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.146543] ACPI: PCI Interrupt Link [PIN4] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.146898] ACPI: PCI Interrupt Link [PIN5] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.147252] ACPI: PCI Interrupt Link [PIN6] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.147602] ACPI: PCI Interrupt Link [PIN7] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.147953] ACPI: PCI Interrupt Link [PIN8] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.148331] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.148356] vgaarb: loaded
[    0.148760] SCSI subsystem initialized
[    0.149007] libata version 3.00 loaded.
[    0.149245] usbcore: registered new interface driver usbfs
[    0.149286] usbcore: registered new interface driver hub
[    0.149374] usbcore: registered new device driver usb
[    0.149824] ACPI: WMI: Mapper loaded
[    0.149831] PCI: Using ACPI for IRQ routing
[    0.150215] NetLabel: Initializing
[    0.150221] NetLabel:  domain hash size = 128
[    0.150227] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.150266] NetLabel:  unlabeled traffic allowed by default
[    0.150404] Switching to clocksource tsc
[    0.153838] AppArmor: AppArmor Filesystem Enabled
[    0.153919] pnp: PnP ACPI init
[    0.153996] ACPI: bus type pnp registered
[    0.161566] pnp: PnP ACPI: found 16 devices
[    0.161575] ACPI: ACPI bus type pnp unregistered
[    0.161586] PnPBIOS: Disabled by ACPI PNP
[    0.161631] system 00:0c: ioport range 0x4d0-0x4d1 has been reserved
[    0.161641] system 00:0c: ioport range 0x800-0x87f has been reserved
[    0.161651] system 00:0c: ioport range 0xf800-0xf87f has been reserved
[    0.161660] system 00:0c: ioport range 0xfc00-0xfc3f has been reserved
[    0.161673] system 00:0c: iomem range 0xfff80000-0xffffffff has been reserved
[    0.161692] system 00:0e: iomem range 0x0-0x9ffff could not be reserved
[    0.161701] system 00:0e: iomem range 0x100000-0xffffff could not be reserved
[    0.161711] system 00:0e: iomem range 0x1000000-0xfffffff could not be reserved
[    0.161729] system 00:0f: iomem range 0xca000-0xcbfff has been reserved
[    0.161739] system 00:0f: iomem range 0xcd800-0xcffff has been reserved
[    0.161764] system 00:0f: iomem range 0xe0000-0xe0fff could not be reserved
[    0.161774] system 00:0f: iomem range 0xe1000-0xe1fff could not be reserved
[    0.161783] system 00:0f: iomem range 0xe2000-0xe2fff could not be reserved
[    0.161793] system 00:0f: iomem range 0xe3000-0xe3fff could not be reserved
[    0.161802] system 00:0f: iomem range 0xe4000-0xe4fff could not be reserved
[    0.161812] system 00:0f: iomem range 0xe5000-0xe5fff could not be reserved
[    0.161821] system 00:0f: iomem range 0xe6000-0xfffff could not be reserved
[    0.196952] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:01
[    0.196962] pci 0000:00:1e.0:   IO window: 0x7000-0x7fff
[    0.196976] pci 0000:00:1e.0:   MEM window: 0xfeb00000-0xfebfffff
[    0.196986] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.197014] pci 0000:00:1e.0: setting latency timer to 64
[    0.197028] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.197037] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.197045] pci_bus 0000:01: resource 0 io:  [0x7000-0x7fff]
[    0.197054] pci_bus 0000:01: resource 1 mem: [0xfeb00000-0xfebfffff]
[    0.197062] pci_bus 0000:01: resource 3 io:  [0x00-0xffff]
[    0.197069] pci_bus 0000:01: resource 4 mem: [0x000000-0xffffffff]
[    0.197189] NET: Registered protocol family 2
[    0.197536] IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
[    0.198459] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
[    0.198641] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[    0.198809] TCP: Hash tables configured (established 8192 bind 8192)
[    0.198817] TCP reno registered
[    0.199063] NET: Registered protocol family 1
[    0.199127] pci 0000:00:02.0: Boot video device
[    0.199198] pci 0000:01:08.0: Firmware left e100 interrupts enabled; disabling
[    0.199752] cpufreq-nforce2: No nForce2 chipset.
[    0.199839] Scanning for low memory corruption every 60 seconds
[    0.200294] audit: initializing netlink socket (disabled)
[    0.200331] type=2000 audit(1291893986.197:1): initialized
[    0.226174] Trying to unpack rootfs image as initramfs...
[    0.255080] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.265673] VFS: Disk quotas dquot_6.5.2
[    0.265991] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.268251] fuse init (API version 7.13)
[    0.268562] msgmni has been set to 470
[    0.274768] alg: No test for stdrng (krng)
[    0.274979] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.274990] io scheduler noop registered
[    0.274996] io scheduler anticipatory registered
[    0.275002] io scheduler deadline registered
[    0.275181] io scheduler cfq registered (default)
[    0.275520] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.275603] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.275905] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.275918] ACPI: Power Button [PWRB]
[    0.276054] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.276063] ACPI: Power Button [PWRF]
[    0.276671] processor LNXCPU:00: registered as cooling_device0
[    0.286113] isapnp: Scanning for PnP cards...
[    0.302728] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.302911] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.303074] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    0.303757] 00:05: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.304012] 00:06: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    0.351197] brd: module loaded
[    0.352819] loop: module loaded
[    0.353176] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    0.358138] ata_piix 0000:00:1f.1: version 2.13
[    0.358333] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.362074] scsi0 : ata_piix
[    0.362564] scsi1 : ata_piix
[    0.364243] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xfff0 irq 14
[    0.364254] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xfff8 irq 15
[    0.365803] Fixed MDIO Bus: probed
[    0.365927] PPP generic driver version 2.4.2
[    0.366143] tun: Universal TUN/TAP device driver, 1.6
[    0.366150] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.366431] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.366506]   alloc irq_desc for 22 on node -1
[    0.366513]   alloc kstat_irqs on node -1
[    0.366533] ehci_hcd 0000:01:0e.3: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    0.366573] ehci_hcd 0000:01:0e.3: EHCI Host Controller
[    0.366670] ehci_hcd 0000:01:0e.3: new USB bus registered, assigned bus number 1
[    0.366747] ehci_hcd 0000:01:0e.3: debug port 1
[    0.389687] ehci_hcd 0000:01:0e.3: irq 22, io mem 0xfebfbf00
[    0.401719] ehci_hcd 0000:01:0e.3: USB 2.0 started, EHCI 1.00
[    0.402153] usb usb1: configuration #1 chosen from 1 choice
[    0.402251] hub 1-0:1.0: USB hub found
[    0.402293] hub 1-0:1.0: 6 ports detected
[    0.402473] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.402547]   alloc irq_desc for 23 on node -1
[    0.402555]   alloc kstat_irqs on node -1
[    0.402577] ohci_hcd 0000:01:0e.0: PCI INT B -> GSI 23 (level, low) -> IRQ 23
[    0.402620] ohci_hcd 0000:01:0e.0: OHCI Host Controller
[    0.402766] ohci_hcd 0000:01:0e.0: new USB bus registered, assigned bus number 2
[    0.402843] ohci_hcd 0000:01:0e.0: irq 23, io mem 0xfebfd000
[    0.460183] usb usb2: configuration #1 chosen from 1 choice
[    0.460286] hub 2-0:1.0: USB hub found
[    0.460331] hub 2-0:1.0: 2 ports detected
[    0.460517]   alloc irq_desc for 20 on node -1
[    0.460525]   alloc kstat_irqs on node -1
[    0.460546] ohci_hcd 0000:01:0e.1: PCI INT C -> GSI 20 (level, low) -> IRQ 20
[    0.460590] ohci_hcd 0000:01:0e.1: OHCI Host Controller
[    0.460758] ohci_hcd 0000:01:0e.1: new USB bus registered, assigned bus number 3
[    0.460838] ohci_hcd 0000:01:0e.1: irq 20, io mem 0xfebfe000
[    0.540115] usb usb3: configuration #1 chosen from 1 choice
[    0.540219] hub 3-0:1.0: USB hub found
[    0.540261] hub 3-0:1.0: 2 ports detected
[    0.540429]   alloc irq_desc for 21 on node -1
[    0.540437]   alloc kstat_irqs on node -1
[    0.540458] ohci_hcd 0000:01:0e.2: PCI INT D -> GSI 21 (level, low) -> IRQ 21
[    0.540496] ohci_hcd 0000:01:0e.2: OHCI Host Controller
[    0.540632] ohci_hcd 0000:01:0e.2: new USB bus registered, assigned bus number 4
[    0.540706] ohci_hcd 0000:01:0e.2: irq 21, io mem 0xfebff000
[    0.541258] ata2.00: ATAPI: JLMS DVD-ROM XJ-HD166, DD05, max UDMA/33
[    0.541848] ata2.00: configured for UDMA/33
[    0.631641] usb usb4: configuration #1 chosen from 1 choice
[    0.631746] hub 4-0:1.0: USB hub found
[    0.631786] hub 4-0:1.0: 2 ports detected
[    0.631956] uhci_hcd: USB Universal Host Controller Interface driver
[    0.632139]   alloc irq_desc for 19 on node -1
[    0.632146]   alloc kstat_irqs on node -1
[    0.632168] uhci_hcd 0000:00:1f.2: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.632191] uhci_hcd 0000:00:1f.2: setting latency timer to 64
[    0.632201] uhci_hcd 0000:00:1f.2: UHCI Host Controller
[    0.632357] uhci_hcd 0000:00:1f.2: new USB bus registered, assigned bus number 5
[    0.632432] uhci_hcd 0000:00:1f.2: irq 19, io base 0x0000fb00
[    0.632747] usb usb5: configuration #1 chosen from 1 choice
[    0.632848] hub 5-0:1.0: USB hub found
[    0.632877] hub 5-0:1.0: 2 ports detected
[    0.633165] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.643047] ata1.00: ATA-6: ST380011A, 8.01, max UDMA/100
[    0.643060] ata1.00: 156301488 sectors, multi 16: LBA48 
[    0.643448] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.643472] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.644033] mice: PS/2 mouse device common for all mice
[    0.644422] rtc_cmos 00:09: RTC can wake from S4
[    0.644581] rtc_cmos 00:09: rtc core: registered rtc_cmos as rtc0
[    0.644628] rtc0: alarms up to one month, 242 bytes nvram
[    0.644973] device-mapper: uevent: version 1.0.3
[    0.645395] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
[    0.647325] device-mapper: multipath: version 1.1.0 loaded
[    0.647339] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.647998] EISA: Probing bus 0 at eisa.0
[    0.648043] Cannot allocate resource for EISA slot 7
[    0.648054] EISA: Detected 0 cards.
[    0.650466] cpuidle: using governor ladder
[    0.650478] cpuidle: using governor menu
[    0.652062] TCP cubic registered
[    0.652586] NET: Registered protocol family 10
[    0.656813] lo: Disabled Privacy Extensions
[    0.658078] ata1.00: configured for UDMA/100
[    0.658445] NET: Registered protocol family 17
[    0.658676] Using IPI No-Shortcut mode
[    0.662316] PM: Resume from disk failed.
[    0.662367] registered taskstats version 1
[    0.662871]   Magic number: 6:253:428
[    0.663051] rtc_cmos 00:09: setting system clock to 2010-12-09 11:26:27 UTC (1291893987)
[    0.663061] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.663067] EDD information not available.
[    0.666017] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    0.993192] isapnp: No Plug & Play device found
[    0.993280] usb 5-1: new full speed USB device using uhci_hcd and address 2
[    0.993773] scsi 0:0:0:0: Direct-Access     ATA      ST380011A        8.01 PQ: 0 ANSI: 5
[    0.994331] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    0.994883] sd 0:0:0:0: [sda] 156301488 512-byte logical blocks: (80.0 GB/74.5 GiB)
[    0.994954] scsi 1:0:0:0: CD-ROM            JLMS     DVD-ROM XJ-HD166 DD05 PQ: 0 ANSI: 5
[    0.995835] sd 0:0:0:0: [sda] Write Protect is off
[    0.995845] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    0.996090] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.997185]  sda:sr0: scsi3-mmc drive: 48x/48x cd/rw xa/form2 cdda tray
[    0.997389] Uniform CD-ROM driver Revision: 3.20
[    0.997728] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    0.997911] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.010134]  sda1 sda2 < sda5 >
[    1.036839] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.167031] usb 5-1: configuration #1 chosen from 1 choice
[    1.272802] Freeing initrd memory: 7777k freed
[    1.310490] usb 5-2: new full speed USB device using uhci_hcd and address 3
[    1.310622] Freeing unused kernel memory: 656k freed
[    1.313975] Write protecting the kernel text: 4684k
[    1.314078] Write protecting the kernel read-only data: 1840k
[    1.380909] udev: starting version 151
[    1.483831] usb 5-2: configuration #1 chosen from 1 choice
[    2.028529] usbcore: registered new interface driver hiddev
[    2.042543] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1f.2/usb5/5-2/5-2:1.0/input/input4
[    2.042884] generic-usb 0003:046D:C526.0001: input,hidraw0: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:1f.2-2/input0
[    2.055452] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1f.2/usb5/5-2/5-2:1.1/input/input5
[    2.055891] generic-usb 0003:046D:C526.0002: input,hiddev96,hidraw1: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1f.2-2/input1
[    2.055976] usbcore: registered new interface driver usbhid
[    2.055986] usbhid: v2.6:USB HID core driver
[    2.135035] e100: Intel(R) PRO/100 Network Driver, 3.5.24-k2-NAPI
[    2.135050] e100: Copyright(c) 1999-2006 Intel Corporation
[    2.135174] e100 0000:01:08.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    2.157695] e100 0000:01:08.0: PME# disabled
[    2.168901] Floppy drive(s): fd0 is 1.44M
[    2.187939] FDC 0 is a post-1991 82077
[    2.222400] e100: eth0: e100_probe: addr 0xfebfc000, irq 20, MAC addr 00:02:55:42:f9:50
[    2.237902] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
[    2.237919] EXT4-fs (sda1): write access will be enabled during recovery
[    7.426722] EXT4-fs (sda1): orphan cleanup on readonly fs
[    7.426759] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 2097208
[    7.427014] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 2888085
[    7.427127] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 2888081
[    7.427186] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 2888076
[    7.427240] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 2888072
[    7.427291] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 2888068
[    7.427343] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 2888066
[    7.427398] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 2888055
[    7.427622] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 2883700
[    7.427678] EXT4-fs (sda1): 9 orphan inodes deleted
[    7.427689] EXT4-fs (sda1): recovery complete
[    7.716236] EXT4-fs (sda1): mounted filesystem with ordered data mode
[   10.159975] Adding 729080k swap on /dev/sda5.  Priority:-1 extents:1 across:729080k 
[   10.850661] udev: starting version 151
[   12.274832] intel_rng: Firmware space is locked read-only. If you can't or
[   12.274838] intel_rng: don't want to disable this in firmware setup, and if
[   12.274842] intel_rng: you are certain that your system has a functional
[   12.274846] intel_rng: RNG, try using the 'no_fwh_detect' option.
[   12.369790] Linux agpgart interface v0.103
[   12.380090] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   12.682234] parport_pc 00:02: reported by Plug and Play ACPI
[   12.682302] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   12.691655] agpgart-intel 0000:00:00.0: Intel i815 Chipset
[   12.719345] agpgart-intel 0000:00:00.0: AGP aperture is 64M @ 0xf8000000
[   12.884448] lp0: using parport0 (interrupt-driven).
[   12.896749] ppdev: user-space parallel port driver
[   13.357189] vga16fb: initializing
[   13.357209] vga16fb: mapped to 0xc00a0000
[   13.358514] fb0: VGA16 VGA frame buffer device
[   13.388868] gameport: EMU10K1 is pci0000:01:0d.1/gameport0, io 0x7898, speed 1125kHz
[   14.481128] Console: switching to colour frame buffer device 80x30
[   14.611707]   alloc irq_desc for 17 on node -1
[   14.611717]   alloc kstat_irqs on node -1
[   14.611738] Intel ICH 0000:00:1f.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   14.611783] Intel ICH 0000:00:1f.5: setting latency timer to 64
[   14.725117] usblp0: USB Bidirectional printer dev 2 if 0 alt 0 proto 2 vid 0x04E8 pid 0x328F
[   14.725301] usbcore: registered new interface driver usblp
[   15.075609] type=1505 audit(1291894001.908:2):  operation="profile_load" pid=524 name="/sbin/dhclient3"
[   15.076951] type=1505 audit(1291894001.912:3):  operation="profile_load" pid=524 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   15.077659] type=1505 audit(1291894001.912:4):  operation="profile_load" pid=524 name="/usr/lib/connman/scripts/dhclient-script"
[   15.232058] intel8x0_measure_ac97_clock: measured 55891 usecs (3130 samples)
[   15.232070] intel8x0: clocking to 41142
[   15.375027] EMU10K1_Audigy 0000:01:0d.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   19.148832] type=1505 audit(1291894005.984:5):  operation="profile_replace" pid=660 name="/sbin/dhclient3"
[   19.150164] type=1505 audit(1291894005.984:6):  operation="profile_replace" pid=660 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   19.150921] type=1505 audit(1291894005.984:7):  operation="profile_replace" pid=660 name="/usr/lib/connman/scripts/dhclient-script"
[   19.351385] type=1505 audit(1291894006.184:8):  operation="profile_load" pid=661 name="/usr/bin/evince"
[   19.795899] type=1505 audit(1291894006.628:9):  operation="profile_load" pid=661 name="/usr/bin/evince-previewer"
[   20.038505] type=1505 audit(1291894006.873:10):  operation="profile_load" pid=661 name="/usr/bin/evince-thumbnailer"
[   20.407664] type=1505 audit(1291894007.243:11):  operation="profile_load" pid=666 name="/usr/lib/cups/backend/cups-pdf"
[   20.410284] type=1505 audit(1291894007.244:12):  operation="profile_load" pid=666 name="/usr/sbin/cupsd"
[   20.467386] type=1505 audit(1291894007.300:13):  operation="profile_load" pid=667 name="/usr/sbin/tcpdump"
[   26.061160] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   26.064175] e100: eth0 NIC Link is Up 100 Mbps Full Duplex
[   26.064415] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   35.652412] [drm] Initialized drm 1.1.0 20060810
[   35.722712]   alloc irq_desc for 16 on node -1
[   35.722723]   alloc kstat_irqs on node -1
[   35.722743] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   35.722755] pci 0000:00:02.0: setting latency timer to 64
[   35.723384] [drm] Initialized i810 1.4.0 20030605 for 0000:00:02.0 on minor 0
[   35.724526] mtrr: base(0xf8000000) is not aligned on a size(0x287000) boundary
[   35.875193] [drm] Using v1.4 init.
[   36.201900] usb 5-1: usbfs: interface 0 claimed by usblp while 'usb' sets config #1
[   39.164064] [drm:drm_reclaim_locked_buffers] *ERROR* reclaim_buffers_locked() deadlock. Please rework this
[   39.164075]     driver to use reclaim_buffers_idlelocked() instead.
[   39.164079]     I will go on reclaiming the buffers anyway.
[  135.748600] usb 5-1: usbfs: interface 0 claimed by usblp while 'usb' sets config #1
[50502.530275] intel_rng: Firmware space is locked read-only. If you can't or
[50502.530282] intel_rng: don't want to disable this in firmware setup, and if
[50502.530287] intel_rng: you are certain that your system has a functional
[50502.530291] intel_rng: RNG, try using the 'no_fwh_detect' option.
[50662.984220] usblp0: nonzero read bulk status received: -84
[50662.984279] usblp0: nonzero write bulk status received: -71
[51512.567228] intel_rng: Firmware space is locked read-only. If you can't or
[51512.567235] intel_rng: don't want to disable this in firmware setup, and if
[51512.567239] intel_rng: you are certain that your system has a functional
[51512.567243] intel_rng: RNG, try using the 'no_fwh_detect' option.
[51565.533336] usblp0: nonzero read bulk status received: -84
[51763.361848] usblp0: nonzero read bulk status received: -84
[51763.402786] usblp0: nonzero read bulk status received: -84
[52575.454344] usblp0: nonzero read bulk status received: -84
[52575.570300] usblp0: nonzero read bulk status received: -84
[52636.508019] [drm:drm_reclaim_locked_buffers] *ERROR* reclaim_buffers_locked() deadlock. Please rework this
[52636.508029]     driver to use reclaim_buffers_idlelocked() instead.
[52636.508033]     I will go on reclaiming the buffers anyway.
[52636.622719] [drm] DMA Cleanup
[52638.729998] mtrr: base(0xf8000000) is not aligned on a size(0x287000) boundary
[52638.850327] [drm] Using v1.4 init.
[52641.948017] [drm:drm_reclaim_locked_buffers] *ERROR* reclaim_buffers_locked() deadlock. Please rework this
[52641.948027]     driver to use reclaim_buffers_idlelocked() instead.
[52641.948031]     I will go on reclaiming the buffers anyway.

---

### Post by rburkartjo on 2010-12-10
sun have you tried  using the terminal to shutdown.  open terminal type sudo shutdown(space)-h now. will ask for your password. enter will not show when you type. hopefully this will allow you to avoid a hard shutdown. just a fix until someone gives you a specific answer.

---

### Post by SungSean on 2010-12-10
Thanks for your reply. Using the terminal to shut down almost worked because it restarted the computer. But it did not shut down the computer. Thanks again.
Even after shutting down using Terminal, the screen goes black and the Caps Lock and Scroll Lock lights (on keyboard) keeps blinking forever in slow intervals. The system hangs like that.

---

### Post by sml156 on 2010-12-10
> **SungSean said:**
> Thanks for your reply. Using the terminal to shut down almost worked because it restarted the computer. But it did not shut down the computer. Thanks again.
Even after shutting down using Terminal, the screen goes black and the Caps Lock and Scroll Lock lights (on keyboard) keeps blinking forever in slow intervals. The system hangs like that.


Try "  poweroff  " in the terminal it works for me also reboot is "  shutdown -r now  "

---

### Post by nm_geo on 2010-12-10
Try this one 
```
sudo shutdown -h -P now 
```-P  Requests that the system  be  powered  off  after  it  has  been
              brought down.

Question SungSean do you have an older kernel to boot from? You kernel has appears to have a number of errors.
Let me switch to my Xbuntu and take a look at mine.

---

### Post by SungSean on 2010-12-10
> **nm_geo said:**
> Try this one 
```
sudo shutdown -h -P now 
```-P  Requests that the system  be  powered  off  after  it  has  been
              brought down.

Question SungSean do you have an older kernel to boot from? You kernel has appears to have a number of errors.
Let me switch to my Xbuntu and take a look at mine.
May I ask what 'older kernel' refers to?
'sudo shutdown -h -P' give me blinking Caps and Scroll Locks. Thanks anyway.

---

### Post by nm_geo on 2010-12-10
Did you also type the word **now?**

Is this a single boot OS?  Do you see a Grub menu when you start the computer or does it go straight to the boot up?

---

### Post by SungSean on 2010-12-10
I did type the word 'now.' When I tried the command second time the computer rebooted. There is only Xubuntu installed in this computer. It gives me option to go into BIOS setup with Ctrl+s key combination when it reboots.
Thanks.

---

### Post by nm_geo on 2010-12-10
If your boot goes directly into the Xbuntu with no Grub try this.

The user can interrupt the boot process and display the menu by holding down the SHIFT key until the menu displays. GRUB  2 searches for a depressed SHIFT key signal during boot. If the key is  pressed or GRUB 2 cannot determine the status of the key, the menu is  displayed...

Maybe you will have a older kernel display try to boot on it, or a recovery mode to boot into.

---

### Post by SungSean on 2010-12-11
Boot into recovery or older kernal and then what am I going to do? Thanks.

---

