---
title: "usb stick, can't read superblocks"
date: 2009-02-15
forum: New to Ubuntu
---

### Post by slymi2005 on 2009-02-15
My usb stick does not show up whenever I plug it in and I cannot mount it. It shows up in nautilus as usb drive and right clicking it gives me the option of rescanning it but I can't open it.

```
sudo mount /dev/sdb1
mount: /dev/sdb1: can't read superblock

```

Anyone know what this means? A google search brought up fsck and i tried something

```
sudo fsck -t vfat /dev/sdb1
fsck 1.41.3 (12-Oct-2008)
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
Read 512 bytes at 0:Input/output error

```

No luck though

---

### Post by lavinog on 2009-02-15
right after pluggin in the flash, type this in a terminal and post its output:
```
dmesg
```

also post the output of
```
lsusb
```

---

### Post by slymi2005 on 2009-02-18
dmesg
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.27-8-eeepc-lean (root@adamm-laptop) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Sun Nov 16 12:45:01 MST 2008 (Ubuntu 2.6.27-8.17eeepc1-eeepc-lean)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e2000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007f7a0000 (usable)
[    0.000000]  BIOS-e820: 000000007f7a0000 - 000000007f7ae000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007f7ae000 - 000000007f7f0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007f7f0000 - 000000007f800000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] DMI present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working it around.
[    0.000000] last_pfn = 0x7f7a0 max_arch_pfn = 0x100000
[    0.000000] kernel direct mapping tables up to 38000000 @ 10000-15000
[    0.000000] RAMDISK: 37900000 - 37fef4de
[    0.000000] ACPI: RSDP 000FB9E0, 0014 (r0 ACPIAM)
[    0.000000] ACPI: RSDT 7F7A0000, 003C (r1 A_M_I_ OEMRSDT  10000817 MSFT       97)
[    0.000000] ACPI: FACP 7F7A0200, 0084 (r2 A_M_I_ OEMFACP  10000817 MSFT       97)
[    0.000000] ACPI: DSDT 7F7A05B0, 5124 (r1  A1028 A1028000        0 INTL 20051117)
[    0.000000] ACPI: FACS 7F7AE000, 0040
[    0.000000] ACPI: APIC 7F7A0390, 005C (r1 A_M_I_ OEMAPIC  10000817 MSFT       97)
[    0.000000] ACPI: MCFG 7F7A03F0, 003C (r1 A_M_I_ OEMMCFG  10000817 MSFT       97)
[    0.000000] ACPI: OEMB 7F7AE040, 0061 (r1 A_M_I_ AMI_OEM  10000817 MSFT       97)
[    0.000000] ACPI: HPET 7F7A56E0, 0038 (r1 A_M_I_ OEMHPET  10000817 MSFT       97)
[    0.000000] ACPI: SSDT 7F7AEB80, 04F0 (r1  PmRef    CpuPm     3000 INTL 20051117)
[    0.000000] 1143MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 38000000
[    0.000000]   low ram: 00000000 - 38000000
[    0.000000]   bootmap 00011000 - 00018000
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 0038000000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 0000704d6c]    TEXT DATA BSS ==> [0000100000 - 0000704d6c]
[    0.000000]   #4 [0037900000 - 0037fef4de]          RAMDISK ==> [0037900000 - 0037fef4de]
[    0.000000]   #5 [0000705000 - 0000708000]    INIT_PG_TABLE ==> [0000705000 - 0000708000]
[    0.000000]   #6 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #7 [0000010000 - 0000011000]          PGTABLE ==> [0000010000 - 0000011000]
[    0.000000]   #8 [0000011000 - 0000018000]          BOOTMAP ==> [0000011000 - 0000018000]
[    0.000000] found SMP MP-table at [c00ff780] 000ff780
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x00038000
[    0.000000]   HighMem  0x00038000 -> 0x0007f7a0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0007f7a0
[    0.000000] On node 0 totalpages: 522031
[    0.000000] free_area_init_node: node 0, pgdat c0607800, node_mem_map c1000240
[    0.000000]   DMA zone: 3947 pages, LIFO batch:0
[    0.000000]   Normal zone: 223300 pages, LIFO batch:31
[    0.000000]   HighMem zone: 290194 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0xffffffff base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e2000
[    0.000000] PM: Registered nosave memory: 00000000000e2000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 7f800000:7f600000)
[    0.000000] PERCPU: Allocating 42140 bytes of per cpu data
[    0.000000] NR_CPUS: 2, nr_cpu_ids: 2, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 517441
[    0.000000] Kernel command line: root=UUID=f5ed5c2c-f327-4c41-b446-32caf458b55c ro quiet splash vga=769 
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] TSC: PIT calibration confirmed by PMTIMER.
[    0.000000] TSC: using PIT calibration value
[    0.000000] Detected 1595.970 MHz processor.
[    0.004000] Console: colour dummy device 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] Memory: 2054792k/2088576k available (3591k kernel code, 32580k reserved, 1633k data, 360k init, 1171072k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xfff9e000 - 0xfffff000   ( 388 kB)
[    0.004000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.004000]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[    0.004000]       .init : 0xc0622000 - 0xc067c000   ( 360 kB)
[    0.004000]       .data : 0xc0481e08 - 0xc061a390   (1633 kB)
[    0.004000]       .text : 0xc0100000 - 0xc0481e08   (3591 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] CPA: page pool initialized 1 of 1 pages preallocated
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.004000] hpet clockevent registered
[    0.004000] Calibrating delay loop (skipped), value calculated using timer frequency.. 3191.94 BogoMIPS (lpj=6383880)
[    0.004000] Security Framework initialized
[    0.004000] SELinux:  Disabled at boot.
[    0.004000] AppArmor: AppArmor initialized
[    0.004000] Mount-cache hash table entries: 512
[    0.004000] Initializing cgroup subsys ns
[    0.004000] Initializing cgroup subsys cpuacct
[    0.004000] Initializing cgroup subsys memory
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 24K
[    0.004000] CPU: L2 cache: 512K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] using mwait in idle threads.
[    0.004000] Checking 'hlt' instruction... OK.
[    0.019410] ACPI: Core revision 20080609
[    0.021578] ACPI: Checking initramfs for custom DSDT
[    0.480311] ENABLING IO-APIC IRQs
[    0.480527] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.523441] CPU0: Intel(R) Atom(TM) CPU N270   @ 1.60GHz stepping 02
[    0.524031] Booting processor 1/1 ip 6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 3191.93 BogoMIPS (lpj=6383875)
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 24K
[    0.004000] CPU: L2 cache: 512K
[    0.004000] CPU: Physical Processor ID: 0
[    0.608246] CPU1: Intel(R) Atom(TM) CPU N270   @ 1.60GHz stepping 02
[    0.608286] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.612060] Brought up 2 CPUs
[    0.612067] Total of 2 processors activated (6383.87 BogoMIPS).
[    0.612097] CPU0 attaching sched-domain:
[    0.612103]  domain 0: span 0-1 level SIBLING
[    0.612109]   groups: 0 1
[    0.612117]   domain 1: span 0-1 level CPU
[    0.612122]    groups: 0-1
[    0.612131] CPU1 attaching sched-domain:
[    0.612135]  domain 0: span 0-1 level SIBLING
[    0.612140]   groups: 1 0
[    0.612147]   domain 1: span 0-1 level CPU
[    0.612152]    groups: 0-1
[    0.612324] net_namespace: 792 bytes
[    0.612324] Booting paravirtualized kernel on bare hardware
[    0.612583] Time: 15:47:51  Date: 02/18/09
[    0.612641] NET: Registered protocol family 16
[    0.612685] No dock devices found.
[    0.613065] ACPI: bus type pci registered
[    0.613065] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 63
[    0.613065] PCI: Not using MMCONFIG.
[    0.613065] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=5
[    0.613065] PCI: Using configuration type 1 for base access
[    0.622080] ACPI: EC: Look up EC in DSDT
[    0.637416] ACPI: Interpreter enabled
[    0.637424] ACPI: (supports S0 S1 S3 S4 S5)
[    0.637467] ACPI: Using IOAPIC for interrupt routing
[    0.637611] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 63
[    0.642441] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
[    0.642448] PCI: Using MMCONFIG for extended config space
[    0.656396] ACPI: EC: GPE = 0x1c, I/O: command/status = 0x66, data = 0x62
[    0.656396] ACPI: EC: driver started in poll mode
[    0.660046] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.660155] PCI: 0000:00:02.0 reg 10 32bit mmio: [f7f00000, f7f7ffff]
[    0.660165] PCI: 0000:00:02.0 reg 14 io port: [dc00, dc07]
[    0.660174] PCI: 0000:00:02.0 reg 18 32bit mmio: [d0000000, dfffffff]
[    0.660183] PCI: 0000:00:02.0 reg 1c 32bit mmio: [f7ec0000, f7efffff]
[    0.660227] PCI: 0000:00:02.1 reg 10 32bit mmio: [f7f80000, f7ffffff]
[    0.660367] PCI: 0000:00:1b.0 reg 10 64bit mmio: [f7eb8000, f7ebbfff]
[    0.660434] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.660443] pci 0000:00:1b.0: PME# disabled
[    0.660530] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.660538] pci 0000:00:1c.0: PME# disabled
[    0.660623] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.660632] pci 0000:00:1c.1: PME# disabled
[    0.660719] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.660727] pci 0000:00:1c.3: PME# disabled
[    0.660790] PCI: 0000:00:1d.0 reg 20 io port: [d400, d41f]
[    0.660869] PCI: 0000:00:1d.1 reg 20 io port: [d480, d49f]
[    0.660948] PCI: 0000:00:1d.2 reg 20 io port: [d800, d81f]
[    0.661026] PCI: 0000:00:1d.3 reg 20 io port: [d880, d89f]
[    0.661109] PCI: 0000:00:1d.7 reg 10 32bit mmio: [f7eb7c00, f7eb7fff]
[    0.661179] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.661187] pci 0000:00:1d.7: PME# disabled
[    0.661365] pci 0000:00:1f.0: quirk: region 0800-087f claimed by ICH6 ACPI/GPIO/TCO
[    0.661374] pci 0000:00:1f.0: quirk: region 0480-04bf claimed by ICH6 GPIO
[    0.661428] PCI: 0000:00:1f.2 reg 10 io port: [0, 7]
[    0.661440] PCI: 0000:00:1f.2 reg 14 io port: [0, 3]
[    0.661452] PCI: 0000:00:1f.2 reg 18 io port: [0, 7]
[    0.661463] PCI: 0000:00:1f.2 reg 1c io port: [0, 3]
[    0.661475] PCI: 0000:00:1f.2 reg 20 io port: [ffa0, ffaf]
[    0.661515] pci 0000:00:1f.2: PME# supported from D3hot
[    0.661523] pci 0000:00:1f.2: PME# disabled
[    0.661692] PCI: 0000:03:00.0 reg 10 64bit mmio: [fbfc0000, fbffffff]
[    0.661707] PCI: 0000:03:00.0 reg 18 io port: [ec00, ec7f]
[    0.661784] pci 0000:03:00.0: PME# supported from D3hot D3cold
[    0.661794] pci 0000:03:00.0: PME# disabled
[    0.661856] PCI: bridge 0000:00:1c.1 io port: [e000, efff]
[    0.661865] PCI: bridge 0000:00:1c.1 32bit mmio: [fbf00000, fbffffff]
[    0.661955] PCI: 0000:01:00.0 reg 10 64bit mmio: [0, ffff]
[    0.662103] PCI: bridge 0000:00:1c.3 32bit mmio: [f8000000, fbefffff]
[    0.662116] PCI: bridge 0000:00:1c.3 64bit mmio pref: [f0000000, f6ffffff]
[    0.662189] pci 0000:00:1e.0: transparent bridge
[    0.662238] bus 00 -> node 0
[    0.662254] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.662839] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P5._PRT]
[    0.663073] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P7._PRT]
[    0.693419] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.693419] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.693419] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 *7 10 11 12 14 15)
[    0.693419] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.696055] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.696413] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.696769] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.697125] ACPI: PCI Interrupt Link [LNKH] (IRQs *3 4 5 6 7 10 11 12 14 15)
[    0.697286] ACPI: WMI: Mapper loaded
[    0.697286] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.697286] pnp: PnP ACPI init
[    0.697286] ACPI: bus type pnp registered
[    0.701037] pnp: PnP ACPI: found 13 devices
[    0.701037] ACPI: ACPI bus type pnp unregistered
[    0.704112] SCSI subsystem initialized
[    0.704112] libata version 3.00 loaded.
[    0.704112] PCI: Using ACPI for IRQ routing
[    0.712056] NET: Registered protocol family 8
[    0.712062] NET: Registered protocol family 20
[    0.712100] NetLabel: Initializing
[    0.712100] NetLabel:  domain hash size = 128
[    0.712100] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.712100] NetLabel:  unlabeled traffic allowed by default
[    0.712104] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.712115] hpet0: 3 64-bit timers, 14318180 Hz
[    0.714275] tracer: 772 pages allocated for 65536 entries of 48 bytes
[    0.714280]    actual entries 65620
[    0.714437] AppArmor: AppArmor Filesystem Enabled
[    0.714475] ACPI: RTC can wake from S4
[    0.716054] Switched to high resolution mode on CPU 0
[    0.716310] Switched to high resolution mode on CPU 1
[    0.716366] system 00:01: iomem range 0xfed13000-0xfed19fff has been reserved
[    0.716392] system 00:08: ioport range 0x25c-0x25f has been reserved
[    0.716399] system 00:08: ioport range 0x380-0x383 has been reserved
[    0.716405] system 00:08: ioport range 0x400-0x41f has been reserved
[    0.716412] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
[    0.716418] system 00:08: ioport range 0x800-0x87f has been reserved
[    0.716425] system 00:08: ioport range 0x480-0x4bf has been reserved
[    0.716433] system 00:08: iomem range 0x8c000000-0x8c01ffff has been reserved
[    0.716440] system 00:08: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    0.716447] system 00:08: iomem range 0xfed20000-0xfed3ffff has been reserved
[    0.716454] system 00:08: iomem range 0xfed50000-0xfed8ffff has been reserved
[    0.716461] system 00:08: iomem range 0xffb00000-0xffbfffff has been reserved
[    0.716469] system 00:08: iomem range 0xfff00000-0xffffffff could not be reserved
[    0.716485] system 00:0a: iomem range 0xfec00000-0xfec00fff has been reserved
[    0.716492] system 00:0a: iomem range 0xfee00000-0xfee00fff could not be reserved
[    0.716506] system 00:0b: iomem range 0xe0000000-0xe3ffffff has been reserved
[    0.716520] system 00:0c: iomem range 0x0-0x9ffff could not be reserved
[    0.716527] system 00:0c: iomem range 0xc0000-0xcffff could not be reserved
[    0.716533] system 00:0c: iomem range 0xe0000-0xfffff could not be reserved
[    0.716540] system 00:0c: iomem range 0x100000-0x7f7fffff could not be reserved
[    0.752690] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:04
[    0.752697] pci 0000:00:1c.0:   IO window: disabled
[    0.752708] pci 0000:00:1c.0:   MEM window: disabled
[    0.752715] pci 0000:00:1c.0:   PREFETCH window: disabled
[    0.752728] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:03
[    0.752735] pci 0000:00:1c.1:   IO window: 0xe000-0xefff
[    0.752746] pci 0000:00:1c.1:   MEM window: 0xfbf00000-0xfbffffff
[    0.752754] pci 0000:00:1c.1:   PREFETCH window: disabled
[    0.752779] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:01
[    0.752784] pci 0000:00:1c.3:   IO window: disabled
[    0.752794] pci 0000:00:1c.3:   MEM window: 0xf8000000-0xfbefffff
[    0.752803] pci 0000:00:1c.3:   PREFETCH window: 0x000000f0000000-0x000000f6ffffff
[    0.752816] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:05
[    0.752821] pci 0000:00:1e.0:   IO window: disabled
[    0.752830] pci 0000:00:1e.0:   MEM window: disabled
[    0.752838] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.752870] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.752881] pci 0000:00:1c.0: setting latency timer to 64
[    0.752898] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.752907] pci 0000:00:1c.1: setting latency timer to 64
[    0.752924] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.752933] pci 0000:00:1c.3: setting latency timer to 64
[    0.752947] pci 0000:00:1e.0: setting latency timer to 64
[    0.752954] bus: 00 index 0 io port: [0, ffff]
[    0.752959] bus: 00 index 1 mmio: [0, ffffffff]
[    0.752964] bus: 04 index 0 mmio: [0, 0]
[    0.752969] bus: 04 index 1 mmio: [0, 0]
[    0.752973] bus: 04 index 2 mmio: [0, 0]
[    0.752977] bus: 04 index 3 mmio: [0, 0]
[    0.752982] bus: 03 index 0 io port: [e000, efff]
[    0.752987] bus: 03 index 1 mmio: [fbf00000, fbffffff]
[    0.752992] bus: 03 index 2 mmio: [0, 0]
[    0.752996] bus: 03 index 3 mmio: [0, 0]
[    0.753011] bus: 01 index 0 mmio: [0, 0]
[    0.753016] bus: 01 index 1 mmio: [f8000000, fbefffff]
[    0.753021] bus: 01 index 2 mmio: [f0000000, f6ffffff]
[    0.753026] bus: 01 index 3 mmio: [0, 0]
[    0.753031] bus: 05 index 0 mmio: [0, 0]
[    0.753035] bus: 05 index 1 mmio: [0, 0]
[    0.753039] bus: 05 index 2 mmio: [0, 0]
[    0.753044] bus: 05 index 3 io port: [0, ffff]
[    0.753048] bus: 05 index 4 mmio: [0, ffffffff]
[    0.753069] NET: Registered protocol family 2
[    0.765132] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.765684] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.766500] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.766941] TCP: Hash tables configured (established 131072 bind 65536)
[    0.766948] TCP reno registered
[    0.769195] NET: Registered protocol family 1
[    0.769423] checking if image is initramfs... it is
[    1.708601] Freeing initrd memory: 7101k freed
[    1.711160] audit: initializing netlink socket (disabled)
[    1.711185] type=2000 audit(1234972070.708:1): initialized
[    1.724239] highmem bounce pool size: 64 pages
[    1.724255] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.731108] VFS: Disk quotas dquot_6.5.1
[    1.731328] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.732559] fuse init (API version 7.9)
[    1.733021] msgmni has been set to 1741
[    1.733328] io scheduler noop registered
[    1.733334] io scheduler anticipatory registered
[    1.733339] io scheduler deadline registered
[    1.733378] io scheduler cfq registered (default)
[    1.733402] pci 0000:00:02.0: Boot video device
[    1.733769] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    1.733832] pcieport-driver 0000:00:1c.0: found MSI capability
[    1.733897] pci_express 0000:00:1c.0:pcie00: allocate port service
[    1.734004] pci_express 0000:00:1c.0:pcie02: allocate port service
[    1.734117] pci_express 0000:00:1c.0:pcie03: allocate port service
[    1.734325] pcieport-driver 0000:00:1c.1: setting latency timer to 64
[    1.734386] pcieport-driver 0000:00:1c.1: found MSI capability
[    1.734446] pci_express 0000:00:1c.1:pcie00: allocate port service
[    1.734551] pci_express 0000:00:1c.1:pcie02: allocate port service
[    1.734667] pci_express 0000:00:1c.1:pcie03: allocate port service
[    1.734879] pcieport-driver 0000:00:1c.3: setting latency timer to 64
[    1.734940] pcieport-driver 0000:00:1c.3: found MSI capability
[    1.735000] pci_express 0000:00:1c.3:pcie00: allocate port service
[    1.735111] pci_express 0000:00:1c.3:pcie02: allocate port service
[    1.735226] pci_express 0000:00:1c.3:pcie03: allocate port service
[    1.735621] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.736970] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.737110] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    1.737775] ACPI: AC Adapter [AC0] (off-line)
[    1.739699] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    1.994729] ACPI: Battery Slot [BAT0] (battery present)
[    1.995593] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.995602] ACPI: Power Button (FF) [PWRF]
[    1.995824] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
[    2.014371] ACPI: Lid Switch [LID]
[    2.014555] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    2.014565] ACPI: Sleep Button (CM) [SLPB]
[    2.014749] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input3
[    2.014759] ACPI: Power Button (CM) [PWRB]
[    2.015901] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:19/input/input4
[    2.015913] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[    2.017578] ACPI: SSDT 7F7AE180, 023C (r1  PmRef  Cpu0Ist     3000 INTL 20051117)
[    2.018445] ACPI: SSDT 7F7AE450, 0724 (r1  PmRef  Cpu0Cst     3001 INTL 20051117)
[    2.019435] Monitor-Mwait will be used to enter C-1 state
[    2.019443] Monitor-Mwait will be used to enter C-2 state
[    2.019449] Monitor-Mwait will be used to enter C-3 state
[    2.019567] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    2.019709] processor ACPI0007:00: registered as cooling_device0
[    2.019724] ACPI: Processor [P001] (supports 8 throttling states)
[    2.020592] ACPI: SSDT 7F7AE0B0, 00CC (r1  PmRef  Cpu1Ist     3000 INTL 20051117)
[    2.021378] ACPI: SSDT 7F7AE3C0, 0085 (r1  PmRef  Cpu1Cst     3000 INTL 20051117)
[    2.022589] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    2.022721] processor ACPI0007:01: registered as cooling_device1
[    2.022737] ACPI: Processor [P002] (supports 8 throttling states)
[    2.054919] thermal LNXTHERM:01: registered as thermal_zone0
[    2.093672] ACPI: Thermal Zone [TZ00] (40 C)
[    2.213100] hpet_resources: 0xfed00000 is busy
[    2.213267] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    2.219022] brd: module loaded
[    2.219164] Atheros(R) L2 Ethernet Driver - version 2.2.3
[    2.219171] Copyright (c) 2007 Atheros Corporation.
[    2.219354] ATL1E 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    2.219375] ATL1E 0000:03:00.0: setting latency timer to 64
[    2.272838] Linux video capture interface: v2.00
[    2.273131] ata_piix 0000:00:1f.2: version 2.12
[    2.273154] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    2.273163] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[    2.273229] ata_piix 0000:00:1f.2: setting latency timer to 64
[    2.273358] scsi0 : ata_piix
[    2.273729] scsi1 : ata_piix
[    2.277431] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    2.277439] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    2.440404] ata1.00: ATA-8: ST9160827AS, 3.AAA, max UDMA/133
[    2.440411] ata1.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    2.456408] ata1.00: configured for UDMA/133
[    2.612298] scsi 0:0:0:0: Direct-Access     ATA      ST9160827AS      3.AA PQ: 0 ANSI: 5
[    2.613294] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    2.644544] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.644559] serio: i8042 AUX port at 0x60,0x64 irq 12
[    2.645216] mice: PS/2 mouse device common for all mice
[    2.668517] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    2.668565] rtc0: alarms up to one month, hpet irqs
[    2.668671] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.03 (30-Apr-2008)
[    2.692314] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[    2.697495] iTCO_wdt: Found a ICH7-M TCO device (Version=2, TCOBASE=0x0860)
[    2.697698] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[    2.697710] iTCO_vendor_support: vendor-support=0
[    2.698963] cpuidle: using governor ladder
[    2.700472] cpuidle: using governor menu
[    2.700620] Advanced Linux Sound Architecture Driver Version 1.0.17.
[    2.700761] Marking TSC unstable due to TSC halts in idle
[    2.700928] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.700975] HDA Intel 0000:00:1b.0: setting latency timer to 64
[    2.774726] ALSA device list:
[    2.774734]   #0: HDA Intel at 0xf7eb8000 irq 16
[    2.776074] ip_tables: (C) 2000-2006 Netfilter Core Team
[    2.776105] TCP cubic registered
[    2.776206] NET: Registered protocol family 10
[    2.777171] lo: Disabled Privacy Extensions
[    2.778478] NET: Registered protocol family 17
[    2.779847] Using IPI No-Shortcut mode
[    2.780540] registered taskstats version 1
[    2.780763]   Magic number: 13:154:791
[    2.780960] rtc_cmos 00:03: setting system clock to 2009-02-18 15:47:53 UTC (1234972073)
[    2.780969] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.780974] EDD information not available.
[    2.781295] Freeing unused kernel memory: 360k freed
[    2.889505] compcache: Compressed swap size set to: 515752 KB
[    2.890779] TLSF: pool: f8857000, init_size=16384, max_size=0, grow_size=16384
[    2.918191] vesafb: framebuffer at 0xd0000000, mapped to 0xf8a00000, using 600k, total 7872k
[    2.918200] vesafb: mode is 640x480x8, linelength=640, pages=23
[    2.918205] vesafb: scrolling: redraw
[    2.918210] vesafb: Pseudocolor: size=8:8:8:8, shift=0:0:0:0
[    2.922178] Console: switching to colour frame buffer device 80x30
[    2.925598] fb0: VESA VGA frame buffer device
[    3.892172] ACPI: EC: missing confirmations, switch off interrupt mode.
[    4.000166] Clocksource tsc unstable (delta = -406277094 ns)
[    4.412161] ACPI Exception (evregion-0419): AE_TIME, Returned by Handler for [EmbeddedControl] [20080609]
[    4.412204] ACPI Error (psparse-0530): Method parse/execution failed [\_SB_.PCI0.SBRG.EC0_.BST1] (Node f7414db0), AE_TIME
[    4.412397] ACPI Error (psparse-0530): Method parse/execution failed [\_SB_.PCI0.CBST] (Node f7417540), AE_TIME
[    4.412527] ACPI Error (psparse-0530): Method parse/execution failed [\_SB_.PCI0.BAT0._BST] (Node f7417480), AE_TIME
[    4.412617] ACPI Exception (battery-0360): AE_TIME, Evaluating _BST [20080609]
[    5.306626] usbcore: registered new interface driver usbfs
[    5.306694] usbcore: registered new interface driver hub
[    5.307797] usbcore: registered new device driver usb
[    5.316283] USB Universal Host Controller Interface driver v3.0
[    5.316395] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    5.316415] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    5.316425] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    5.316531] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[    5.316591] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000d400
[    5.316962] usb usb1: configuration #1 chosen from 1 choice
[    5.317093] hub 1-0:1.0: USB hub found
[    5.317116] hub 1-0:1.0: 2 ports detected
[    5.421591] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    5.421612] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    5.421624] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    5.421698] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[    5.421760] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000d480
[    5.422076] usb usb2: configuration #1 chosen from 1 choice
[    5.422163] hub 2-0:1.0: USB hub found
[    5.422185] hub 2-0:1.0: 2 ports detected
[    5.456369] Warning! ehci_hcd should always be loaded before uhci_hcd and ohci_hcd, not after
[    5.466922] scsi 0:0:0:0: Attached scsi generic sg0 type 0
[    5.531184] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    5.531205] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    5.531216] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    5.531307] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[    5.531368] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000d800
[    5.531674] usb usb3: configuration #1 chosen from 1 choice
[    5.531762] hub 3-0:1.0: USB hub found
[    5.531784] hub 3-0:1.0: 2 ports detected
[    5.533116] Driver 'sd' needs updating - please use bus_type methods
[    5.533365] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[    5.533423] sd 0:0:0:0: [sda] Write Protect is off
[    5.533433] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.533527] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.533729] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[    5.533783] sd 0:0:0:0: [sda] Write Protect is off
[    5.533792] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.533885] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.533899]  sda: sda1 sda2 < sda5 sda6 > sda3 sda4
[    5.575993] sd 0:0:0:0: [sda] Attached SCSI disk
[    5.611998] Adding 515748k swap on /dev/ramzswap0.  Priority:100 extents:1 across:515748k
[    5.633654] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    5.633677] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    5.633687] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    5.633772] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[    5.633823] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000d880
[    5.634195] usb usb4: configuration #1 chosen from 1 choice
[    5.634299] hub 4-0:1.0: USB hub found
[    5.634322] hub 4-0:1.0: 2 ports detected
[    5.841767] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    5.841800] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    5.841811] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    5.841902] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[    5.845860] ehci_hcd 0000:00:1d.7: debug port 1
[    5.845876] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    5.845900] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xf7eb7c00
[    5.861061] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    5.861442] usb usb5: configuration #1 chosen from 1 choice
[    5.861544] hub 5-0:1.0: USB hub found
[    5.861568] hub 5-0:1.0: 8 ports detected
[    6.181076] usb 5-8: new high speed USB device using ehci_hcd and address 2
[    6.357941] usb 5-8: configuration #1 chosen from 1 choice
[    6.783693] PM: Starting manual resume from disk
[    6.783702] PM: Resume from partition 8:5
[    6.783706] PM: Checking hibernation image.
[    6.783957] PM: Resume from disk failed.
[    6.844782] kjournald starting.  Commit interval 5 seconds
[    6.844812] EXT3-fs: mounted filesystem with ordered data mode.
[   12.952393] udevd version 124 started
[   14.564398] eeepc: Eee PC Hotkey Driver
[   14.565727] eeepc: Hotkey init flags 0x41
[   14.566535] eeepc: Get control methods supported: 0x101711
[   14.566752] input: Asus EeePC extra buttons as /devices/virtual/input/input6
[   15.072605] asus_eee module requires i2c-i801 module at load time if you like to access pll via proc too
[   15.072642] asus_eee version 0.3 init sucessfully
[   15.072651] sys_init_module: 'asus_eee'->init suspiciously returned 1, it should follow 0/-E convention
[   15.072658] sys_init_module: loading module anyway...
[   15.072669] Pid: 2617, comm: modprobe Not tainted 2.6.27-8-eeepc-lean #1
[   15.072678]  [<c047b132>] ? printk+0x1d/0x23
[   15.072697]  [<c015b8b7>] sys_init_module+0x1a7/0x1b0
[   15.072712]  [<c0103f23>] sysenter_do_call+0x12/0x2f
[   15.072724]  =======================
[   15.396408] Linux agpgart interface v0.103
[   15.574852] agpgart-intel 0000:00:00.0: Intel 945GME Chipset
[   15.575087] agpgart-intel 0000:00:00.0: detected 7932K stolen memory
[   15.653043] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[   17.157425] input: PC Speaker as /devices/platform/pcspkr/input/input7
[   17.300327] ath5k_pci 0000:01:00.0: enabling device (0000 -> 0002)
[   17.300347] ath5k_pci 0000:01:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   17.300374] ath5k_pci 0000:01:00.0: setting latency timer to 64
[   17.300425] ath5k_pci 0000:01:00.0: registered as 'phy0'
[   17.304811] ath5k phy0: Support for RF2425 is under development.
[   17.446185] phy0: Selected rate control algorithm 'pid'
[   18.127332] uvcvideo: Found UVC 1.00 device CNF7129 (04f2:b071)
[   18.143390] input: CNF7129 as /devices/pci0000:00/0000:00:1d.7/usb5/5-8/5-8:1.0/input/input8
[   18.160541] ath5k phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
[   18.161474] usbcore: registered new interface driver uvcvideo
[   18.161532] USB Video Class driver (v0.1.0)
[   20.228604] input: ImPS/2 Logitech Wheel Mouse as /devices/platform/i8042/serio1/input/input9
[   21.011944] Adding 4883720k swap on /dev/sda5.  Priority:-1 extents:1 across:4883720k
[   21.117698] EXT3 FS on sda6, internal journal
[   22.030884] type=1505 audit(1235000892.525:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4033
[   22.453026] type=1505 audit(1235000892.949:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4038
[   22.453492] type=1505 audit(1235000892.949:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4038
[   22.550388] type=1505 audit(1235000893.046:5): operation="profile_load" name="/usr/sbin/mysqld" name2="default" pid=4042
[   22.648300] type=1505 audit(1235000893.145:6): operation="profile_load" name="/usr/sbin/mysqld-akonadi" name2="default" pid=4046
[   25.712650] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   32.880749] RPC: Registered udp transport module.
[   32.880767] RPC: Registered tcp transport module.
[   33.004544] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
[   33.156829] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[   33.176571] NFSD: starting 90-second grace period
[   36.118004] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   36.118028] vboxdrv: Successfully done.
[   36.118040] vboxdrv: Found 2 processor cores.
[   36.118452] vboxdrv: fAsync=0 offMin=0x420 offMax=0x28a4
[   36.118685] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   36.118701] vboxdrv: Successfully loaded version 2.1.2 (interface 0x000a0009).
[   39.714269] Bluetooth: Core ver 2.13
[   39.716136] NET: Registered protocol family 31
[   39.716160] Bluetooth: HCI device and connection manager initialized
[   39.716178] Bluetooth: HCI socket layer initialized
[   39.766580] Bluetooth: L2CAP ver 2.11
[   39.766601] Bluetooth: L2CAP socket layer initialized
[   39.808491] Bluetooth: SCO (Voice Link) ver 0.6
[   39.808525] Bluetooth: SCO socket layer initialized
[   39.871228] Bluetooth: RFCOMM socket layer initialized
[   39.871265] Bluetooth: RFCOMM TTY layer initialized
[   39.871273] Bluetooth: RFCOMM ver 1.10
[   39.882007] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   39.882019] Bluetooth: BNEP filters: protocol multicast
[   39.929082] Bridge firewalling registered
[   39.930191] pan0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature.
[   44.231373] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   44.270138] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   44.339044] [drm] Initialized drm 1.1.0 20060810
[   44.360408] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   44.360429] pci 0000:00:02.0: setting latency timer to 64
[   44.360796] [drm] Initialized i915 1.6.0 20060119 on minor 0
[  208.723727] wlan0: authenticate with AP 00:1a:ef:01:cd:e4
[  208.728825] wlan0: authenticated
[  208.728862] wlan0: associate with AP 00:1a:ef:01:cd:e4
[  208.740638] wlan0: RX AssocResp from 00:1a:ef:01:cd:e4 (capab=0x411 status=0 aid=193)
[  208.740666] wlan0: invalid aid value 193; bits 15:14 not set
[  208.740679] wlan0: associated
[  208.741510] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  209.423739] padlock: VIA PadLock not detected.
[  219.056030] wlan0: no IPv6 routers present
[ 3665.344124] usb 5-4: new high speed USB device using ehci_hcd and address 3
[ 3665.483354] usb 5-4: configuration #1 chosen from 1 choice
[ 3665.731852] usbcore: registered new interface driver libusual
[ 3665.776125] Initializing USB Mass Storage driver...
[ 3665.777001] scsi2 : SCSI emulation for USB Mass Storage devices
[ 3665.778611] usb-storage: device found at 3
[ 3665.778625] usb-storage: waiting for device to settle before scanning
[ 3665.778645] usbcore: registered new interface driver usb-storage
[ 3665.778657] USB Mass Storage support registered.
[ 3670.777188] usb-storage: device scan complete
[ 3670.779536] scsi 2:0:0:0: Direct-Access     Corsair  Flash Voyager    1100 PQ: 0 ANSI: 0 CCS
[ 3670.797154] sd 2:0:0:0: [sdb] 6891520 512-byte hardware sectors (3528 MB)
[ 3670.798114] sd 2:0:0:0: [sdb] Write Protect is off
[ 3670.798134] sd 2:0:0:0: [sdb] Mode Sense: 43 00 00 00
[ 3670.798150] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[ 3670.807734] sd 2:0:0:0: [sdb] 6891520 512-byte hardware sectors (3528 MB)
[ 3670.810109] sd 2:0:0:0: [sdb] Write Protect is off
[ 3670.810140] sd 2:0:0:0: [sdb] Mode Sense: 43 00 00 00
[ 3670.810156] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[ 3670.813174]  sdb:<6>usb 5-4: reset high speed USB device using ehci_hcd and address 3
[ 3716.037117] usb 5-4: device descriptor read/64, error -110
[ 3731.252076] usb 5-4: device descriptor read/64, error -110
[ 3731.468089] usb 5-4: reset high speed USB device using ehci_hcd and address 3
[ 3732.246120] [drm:i915_vblank_swap] *ERROR* Invalid pipe 1
[ 3746.584108] usb 5-4: device descriptor read/64, error -110
[ 3761.796125] usb 5-4: device descriptor read/64, error -110
[ 3762.012160] usb 5-4: reset high speed USB device using ehci_hcd and address 3
[ 3772.420132] usb 5-4: device not accepting address 3, error -110
[ 3772.532132] usb 5-4: reset high speed USB device using ehci_hcd and address 3
[ 3782.940098] usb 5-4: device not accepting address 3, error -110
[ 3782.940207] usb 5-4: USB disconnect, address 3
[ 3782.944578] sd 2:0:0:0: Device offlined - not ready after error recovery
[ 3782.944620] sd 2:0:0:0: [sdb] Result: hostbyte=DID_ABORT driverbyte=DRIVER_OK,SUGGEST_OK
[ 3782.944644] end_request: I/O error, dev sdb, sector 0
[ 3782.944668] Buffer I/O error on device sdb, logical block 0
[ 3782.944798] sd 2:0:0:0: rejecting I/O to offline device
[ 3782.944821] Buffer I/O error on device sdb, logical block 0
[ 3782.944889] sd 2:0:0:0: rejecting I/O to offline device
[ 3782.944909] Buffer I/O error on device sdb, logical block 0
[ 3782.944975] sd 2:0:0:0: rejecting I/O to offline device
[ 3782.944994] Buffer I/O error on device sdb, logical block 0
[ 3782.945054] sd 2:0:0:0: rejecting I/O to offline device
[ 3782.945074] Buffer I/O error on device sdb, logical block 0
[ 3782.945106] ldm_validate_partition_table(): Disk read failed.
[ 3782.945152] sd 2:0:0:0: rejecting I/O to offline device
[ 3782.945171] Buffer I/O error on device sdb, logical block 0
[ 3782.945231] sd 2:0:0:0: rejecting I/O to offline device
[ 3782.945250] Buffer I/O error on device sdb, logical block 0
[ 3782.945309] sd 2:0:0:0: rejecting I/O to offline device
[ 3782.945329] Buffer I/O error on device sdb, logical block 0
[ 3782.945387] sd 2:0:0:0: rejecting I/O to offline device
[ 3782.945407] Buffer I/O error on device sdb, logical block 0
[ 3782.945438] Dev sdb: unable to read RDB block 0
[ 3782.945482] sd 2:0:0:0: rejecting I/O to offline device
[ 3782.945501] Buffer I/O error on device sdb, logical block 0
[ 3782.945559] sd 2:0:0:0: rejecting I/O to offline device
[ 3782.945638] sd 2:0:0:0: rejecting I/O to offline device
[ 3782.945694] sd 2:0:0:0: rejecting I/O to offline device
[ 3782.945757] sd 2:0:0:0: rejecting I/O to offline device
[ 3782.945819] sd 2:0:0:0: rejecting I/O to offline device
[ 3782.945851]  unable to read partition table
[ 3782.946278] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[ 3782.946835] sd 2:0:0:0: Attached scsi generic sg1 type 0
[ 3783.068192] usb 5-4: new high speed USB device using ehci_hcd and address 4
[ 3798.180143] usb 5-4: device descriptor read/64, error -110
[ 3813.397146] usb 5-4: device descriptor read/64, error -110
[ 3813.612130] usb 5-4: new high speed USB device using ehci_hcd and address 5

```

lsusb
```
Bus 005 Device 002: ID 04f2:b071 Chicony Electronics Co., Ltd 
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

This is on my eee pc 1000ha which has easy peasy installed but the problem is the same on my desktop which is running ubuntu 8.10

---

### Post by slymi2005 on 2009-02-24
bump

---

### Post by slymi2005 on 2009-02-25
Are you having the same problem as I am? 

My problem was with a corsair flash voyager 4gb and since I have not been able to get any help I decided to just get an rma and get it fixed or replaced.

---

### Post by mdhunn on 2009-03-20
Wait a minute, isn't the superblock where the file allocation table is stored.  I remember reading that it's what usually kills usb sticks.  Any given bit in a thumbdrive can be written to thousands of times.  But the FAT is all ways in the same place at the start of the drive and it gets written to whenever the drive gets accessed, even if it's just to log the last time a file was looked at.  

My advice would be to keep all your files on your computer and avoid mounting your flash memory until you want to move to another computer.

---

