---
title: "webcam not working"
date: 2009-05-13
forum: New to Ubuntu
---

### Post by James Dee on 2009-05-13
hello everybody,
i need help with setting up my camera to work properly. i try million things from net but still nothing.
does anybody have some idea?
atb
james

this is lsusb:
```
print "Bus 002 Device 002: ID 0c45:612c Microdia PC Camera (SN9C110)
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 046d:c510 Logitech, Inc. Cordless Mouse
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 1058:1102 Western Digital Technologies, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub"
```

this is from dmesg:

```
print " [    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.27-14-generic (buildd@palmer) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu12) ) #1 SMP Wed Apr 15 18:59:16 UTC 2009 (Ubuntu 2.6.27-14.33-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007ff80000 (usable)
[    0.000000]  BIOS-e820: 000000007ff80000 - 000000007ff8e000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007ff8e000 - 000000007ffe0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007ffe0000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.4 present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working it around.
[    0.000000] last_pfn = 0x7ff80 max_arch_pfn = 0x100000
[    0.000000] kernel direct mapping tables up to 38000000 @ 10000-15000
[    0.000000] RAMDISK: 3782a000 - 37fefe76
[    0.000000] ACPI: RSDP 000FBDC0, 0014 (r0 ACPIAM)
[    0.000000] ACPI: RSDT 7FF80000, 003C (r1 A_M_I_ OEMRSDT   7000719 MSFT       97)
[    0.000000] ACPI: FACP 7FF80200, 0084 (r2 A_M_I_ OEMFACP   7000719 MSFT       97)
[    0.000000] ACPI: DSDT 7FF805C0, 7A0C (r1  A0807 A0807000        0 INTL 20060113)
[    0.000000] ACPI: FACS 7FF8E000, 0040
[    0.000000] ACPI: APIC 7FF80390, 006C (r1 A_M_I_ OEMAPIC   7000719 MSFT       97)
[    0.000000] ACPI: MCFG 7FF80400, 003C (r1 A_M_I_ OEMMCFG   7000719 MSFT       97)
[    0.000000] ACPI: OEMB 7FF8E040, 0081 (r1 A_M_I_ AMI_OEM   7000719 MSFT       97)
[    0.000000] ACPI: HPET 7FF87FD0, 0038 (r1 A_M_I_ OEMHPET   7000719 MSFT       97)
[    0.000000] ACPI: OSFR 7FF88010, 00B0 (r1 A_M_I_ OEMOSFR   7000719 MSFT       97)
[    0.000000] 1151MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 38000000
[    0.000000]   low ram: 00000000 - 38000000
[    0.000000]   bootmap 00011000 - 00018000
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 0038000000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00005c39e0]    TEXT DATA BSS ==> [0000100000 - 00005c39e0]
[    0.000000]   #4 [003782a000 - 0037fefe76]          RAMDISK ==> [003782a000 - 0037fefe76]
[    0.000000]   #5 [00005c4000 - 00005c7000]    INIT_PG_TABLE ==> [00005c4000 - 00005c7000]
[    0.000000]   #6 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000]
[    0.000000]   #7 [0000010000 - 0000011000]          PGTABLE ==> [0000010000 - 0000011000]
[    0.000000]   #8 [0000011000 - 0000018000]          BOOTMAP ==> [0000011000 - 0000018000]
[    0.000000] found SMP MP-table at [c00ff780] 000ff780
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x00038000
[    0.000000]   HighMem  0x00038000 -> 0x0007ff80
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0007ff80
[    0.000000] On node 0 totalpages: 524047
[    0.000000] free_area_init_node: node 0, pgdat c048c700, node_mem_map c1000240
[    0.000000]   DMA zone: 3947 pages, LIFO batch:0
[    0.000000]   Normal zone: 223300 pages, LIFO batch:31
[    0.000000]   HighMem zone: 292193 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
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
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e4000
[    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:7ee00000)
[    0.000000] PERCPU: Allocating 41628 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 4, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 519440
[    0.000000] Kernel command line: root=UUID=cb76defa-f2ef-4f5b-ba59-de658539fc20 ro quiet splash 
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] TSC: PIT calibration confirmed by PMTIMER.
[    0.000000] TSC: using PIT calibration value
[    0.000000] Detected 2669.764 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] Memory: 2063112k/2096640k available (2578k kernel code, 32312k reserved, 1162k data, 428k init, 1179136k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xf8800000 - 0xff3fe000   ( 107 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[    0.004000]       .init : 0xc04ad000 - 0xc0518000   ( 428 kB)
[    0.004000]       .data : 0xc0384a8a - 0xc04a7680   (1162 kB)
[    0.004000]       .text : 0xc0100000 - 0xc0384a8a   (2578 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] CPA: page pool initialized 1 of 1 pages preallocated
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.004000] hpet clockevent registered
[    0.004000] Calibrating delay loop (skipped), value calculated using timer frequency.. 5339.52 BogoMIPS (lpj=10679056)
[    0.004000] Security Framework initialized
[    0.004000] SELinux:  Disabled at boot.
[    0.004000] AppArmor: AppArmor initialized
[    0.004000] Mount-cache hash table entries: 512
[    0.004000] Initializing cgroup subsys ns
[    0.004000] Initializing cgroup subsys cpuacct
[    0.004000] Initializing cgroup subsys memory
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 4096K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 0
[    0.004000] using mwait in idle threads.
[    0.004000] Checking 'hlt' instruction... OK.
[    0.017431] ACPI: Core revision 20080609
[    0.019667] ACPI: Checking initramfs for custom DSDT
[    0.272185] ENABLING IO-APIC IRQs
[    0.272349] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.316830] CPU0: Intel(R) Core(TM)2 Duo CPU     E6750  @ 2.66GHz stepping 0b
[    0.320020] Booting processor 1/1 ip 6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 5339.51 BogoMIPS (lpj=10679032)
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 4096K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.404543] CPU1: Intel(R) Core(TM)2 Duo CPU     E6750  @ 2.66GHz stepping 0b
[    0.404555] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.408040] Brought up 2 CPUs
[    0.408042] Total of 2 processors activated (10679.04 BogoMIPS).
[    0.408059] CPU0 attaching sched-domain:
[    0.408062]  domain 0: span 0-1 level MC
[    0.408063]   groups: 0 1
[    0.408068] CPU1 attaching sched-domain:
[    0.408070]  domain 0: span 0-1 level MC
[    0.408071]   groups: 1 0
[    0.408125] net_namespace: 840 bytes
[    0.408125] Booting paravirtualized kernel on bare hardware
[    0.408218] Time: 16:52:19  Date: 05/13/09
[    0.408237] NET: Registered protocol family 16
[    0.408251] EISA bus registered
[    0.408251] ACPI: bus type pci registered
[    0.408251] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.408251] PCI: Not using MMCONFIG.
[    0.408251] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=5
[    0.408251] PCI: Using configuration type 1 for base access
[    0.408748] ACPI: EC: Look up EC in DSDT
[    0.419177] ACPI: Interpreter enabled
[    0.419182] ACPI: (supports S0 S1 S3 S4 S5)
[    0.419195] ACPI: Using IOAPIC for interrupt routing
[    0.419240] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.421320] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
[    0.421322] PCI: Using MMCONFIG for extended config space
[    0.428129] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.428129] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.428129] pci 0000:00:01.0: PME# disabled
[    0.428151] PCI: 0000:00:1a.0 reg 20 io port: [b800, b81f]
[    0.428210] PCI: 0000:00:1a.1 reg 20 io port: [b880, b89f]
[    0.428268] PCI: 0000:00:1a.2 reg 20 io port: [bc00, bc1f]
[    0.428330] PCI: 0000:00:1a.7 reg 10 32bit mmio: [f9fffc00, f9ffffff]
[    0.428386] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.428390] pci 0000:00:1a.7: PME# disabled
[    0.428441] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.428444] pci 0000:00:1c.0: PME# disabled
[    0.428495] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.428498] pci 0000:00:1c.4: PME# disabled
[    0.428546] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    0.428550] pci 0000:00:1c.5: PME# disabled
[    0.428586] PCI: 0000:00:1d.0 reg 20 io port: [b080, b09f]
[    0.428645] PCI: 0000:00:1d.1 reg 20 io port: [b400, b41f]
[    0.428703] PCI: 0000:00:1d.2 reg 20 io port: [b480, b49f]
[    0.428765] PCI: 0000:00:1d.7 reg 10 32bit mmio: [f9fff800, f9fffbff]
[    0.428821] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.428824] pci 0000:00:1d.7: PME# disabled
[    0.428923] pci 0000:00:1f.0: quirk: region 0800-087f claimed by ICH6 ACPI/GPIO/TCO
[    0.428926] pci 0000:00:1f.0: quirk: region 0480-04bf claimed by ICH6 GPIO
[    0.428964] PCI: 0000:00:1f.2 reg 10 io port: [a000, a007]
[    0.428969] PCI: 0000:00:1f.2 reg 14 io port: [9c00, 9c03]
[    0.428974] PCI: 0000:00:1f.2 reg 18 io port: [9880, 9887]
[    0.428979] PCI: 0000:00:1f.2 reg 1c io port: [9800, 9803]
[    0.428983] PCI: 0000:00:1f.2 reg 20 io port: [9480, 948f]
[    0.428988] PCI: 0000:00:1f.2 reg 24 io port: [9400, 940f]
[    0.429026] PCI: 0000:00:1f.3 reg 10 64bit mmio: [f9fff400, f9fff4ff]
[    0.429037] PCI: 0000:00:1f.3 reg 20 io port: [400, 41f]
[    0.429073] PCI: 0000:00:1f.5 reg 10 io port: [b000, b007]
[    0.429077] PCI: 0000:00:1f.5 reg 14 io port: [ac00, ac03]
[    0.429082] PCI: 0000:00:1f.5 reg 18 io port: [a880, a887]
[    0.429086] PCI: 0000:00:1f.5 reg 1c io port: [a800, a803]
[    0.429091] PCI: 0000:00:1f.5 reg 20 io port: [a480, a48f]
[    0.429095] PCI: 0000:00:1f.5 reg 24 io port: [a400, a40f]
[    0.429143] PCI: 0000:01:00.0 reg 10 32bit mmio: [fd000000, fdffffff]
[    0.429150] PCI: 0000:01:00.0 reg 14 64bit mmio: [d0000000, dfffffff]
[    0.429158] PCI: 0000:01:00.0 reg 1c 64bit mmio: [fa000000, fbffffff]
[    0.429162] PCI: 0000:01:00.0 reg 24 io port: [cc00, cc7f]
[    0.429167] PCI: 0000:01:00.0 reg 30 32bit mmio: [fe9e0000, fe9fffff]
[    0.429215] PCI: bridge 0000:00:01.0 io port: [c000, cfff]
[    0.429218] PCI: bridge 0000:00:01.0 32bit mmio: [fa000000, fe9fffff]
[    0.429221] PCI: bridge 0000:00:01.0 64bit mmio pref: [d0000000, dfffffff]
[    0.429258] PCI: bridge 0000:00:1c.0 64bit mmio pref: [f8f00000, f8ffffff]
[    0.429297] PCI: 0000:03:00.0 reg 10 io port: [dc00, dc07]
[    0.429304] PCI: 0000:03:00.0 reg 14 io port: [d880, d883]
[    0.429311] PCI: 0000:03:00.0 reg 18 io port: [d800, d807]
[    0.429318] PCI: 0000:03:00.0 reg 1c io port: [d480, d483]
[    0.429324] PCI: 0000:03:00.0 reg 20 io port: [d400, d40f]
[    0.429331] PCI: 0000:03:00.0 reg 24 32bit mmio: [febffc00, febfffff]
[    0.429379] pci 0000:03:00.0: supports D1
[    0.429380] pci 0000:03:00.0: PME# supported from D0 D1 D3hot
[    0.429384] pci 0000:03:00.0: PME# disabled
[    0.429411] PCI: bridge 0000:00:1c.4 io port: [d000, dfff]
[    0.429415] PCI: bridge 0000:00:1c.4 32bit mmio: [feb00000, febfffff]
[    0.429464] PCI: 0000:02:00.0 reg 10 64bit mmio: [feac0000, feafffff]
[    0.429493] PCI: 0000:02:00.0 reg 30 32bit mmio: [feaa0000, feabffff]
[    0.429534] pci 0000:02:00.0: PME# supported from D3hot D3cold
[    0.429538] pci 0000:02:00.0: PME# disabled
[    0.429567] PCI: bridge 0000:00:1c.5 32bit mmio: [fea00000, feafffff]
[    0.429598] PCI: 0000:05:00.0 reg 10 io port: [ec00, ec1f]
[    0.429643] pci 0000:05:00.0: supports D1
[    0.429644] pci 0000:05:00.0: supports D2
[    0.429679] pci 0000:00:1e.0: transparent bridge
[    0.429682] PCI: bridge 0000:00:1e.0 io port: [e000, efff]
[    0.429704] bus 00 -> node 0
[    0.429709] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.429935] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P2._PRT]
[    0.430028] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.430158] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P8._PRT]
[    0.430249] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P9._PRT]
[    0.430353] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[    0.444822] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.444822] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.444822] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.444822] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11 12 *14 15)
[    0.444822] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.444822] ACPI: PCI Interrupt Link [LNKF] (IRQs *3 4 5 6 7 10 11 12 14 15)
[    0.444822] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 *15)
[    0.444904] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 *7 10 11 12 14 15)
[    0.444954] ACPI Warning (tbutils-0217): Incorrect checksum in table [OEMB] - C7, should be BE [20080609]
[    0.444954] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.444954] pnp: PnP ACPI init
[    0.444954] ACPI: bus type pnp registered
[    0.448557] pnp: PnP ACPI: found 15 devices
[    0.448557] ACPI: ACPI bus type pnp unregistered
[    0.448557] PnPBIOS: Disabled by ACPI PNP
[    0.448557] PCI: Using ACPI for IRQ routing
[    0.456036] NET: Registered protocol family 8
[    0.456039] NET: Registered protocol family 20
[    0.456054] NetLabel: Initializing
[    0.456054] NetLabel:  domain hash size = 128
[    0.456054] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.456061] NetLabel:  unlabeled traffic allowed by default
[    0.456067] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.456072] hpet0: 4 64-bit timers, 14318180 Hz
[    0.457729] tracer: 772 pages allocated for 65536 entries of 48 bytes
[    0.457731]    actual entries 65620
[    0.457784] AppArmor: AppArmor Filesystem Enabled
[    0.457800] ACPI: RTC can wake from S4
[    0.464066] system 00:01: iomem range 0xfed14000-0xfed19fff has been reserved
[    0.464076] system 00:07: ioport range 0x290-0x297 has been reserved
[    0.464082] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
[    0.464085] system 00:08: ioport range 0x800-0x87f has been reserved
[    0.464088] system 00:08: ioport range 0x480-0x4bf has been reserved
[    0.464091] system 00:08: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    0.464095] system 00:08: iomem range 0xfed20000-0xfed3ffff has been reserved
[    0.464098] system 00:08: iomem range 0xfed50000-0xfed8ffff has been reserved
[    0.464100] system 00:08: iomem range 0xffa00000-0xffafffff has been reserved
[    0.464104] system 00:08: iomem range 0xffb00000-0xffbfffff has been reserved
[    0.464107] system 00:08: iomem range 0xffe00000-0xffefffff has been reserved
[    0.464110] system 00:08: iomem range 0xfff00000-0xfffffffe could not be reserved
[    0.464117] system 00:0b: iomem range 0xfec00000-0xfec00fff has been reserved
[    0.464120] system 00:0b: iomem range 0xfee00000-0xfee00fff could not be reserved
[    0.464126] system 00:0d: iomem range 0xe0000000-0xefffffff has been reserved
[    0.464132] system 00:0e: iomem range 0x0-0x9ffff could not be reserved
[    0.464135] system 00:0e: iomem range 0xc0000-0xcffff could not be reserved
[    0.464137] system 00:0e: iomem range 0xe0000-0xfffff could not be reserved
[    0.464141] system 00:0e: iomem range 0x100000-0x7fffffff could not be reserved
[    0.499040] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.499042] pci 0000:00:01.0:   IO window: 0xc000-0xcfff
[    0.499046] pci 0000:00:01.0:   MEM window: 0xfa000000-0xfe9fffff
[    0.499048] pci 0000:00:01.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
[    0.499052] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:04
[    0.499053] pci 0000:00:1c.0:   IO window: disabled
[    0.499057] pci 0000:00:1c.0:   MEM window: disabled
[    0.499060] pci 0000:00:1c.0:   PREFETCH window: 0x000000f8f00000-0x000000f8ffffff
[    0.499065] pci 0000:00:1c.4: PCI bridge, secondary bus 0000:03
[    0.499067] pci 0000:00:1c.4:   IO window: 0xd000-0xdfff
[    0.499071] pci 0000:00:1c.4:   MEM window: 0xfeb00000-0xfebfffff
[    0.499074] pci 0000:00:1c.4:   PREFETCH window: disabled
[    0.499079] pci 0000:00:1c.5: PCI bridge, secondary bus 0000:02
[    0.499081] pci 0000:00:1c.5:   IO window: disabled
[    0.499085] pci 0000:00:1c.5:   MEM window: 0xfea00000-0xfeafffff
[    0.499088] pci 0000:00:1c.5:   PREFETCH window: disabled
[    0.499092] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:05
[    0.499095] pci 0000:00:1e.0:   IO window: 0xe000-0xefff
[    0.499099] pci 0000:00:1e.0:   MEM window: disabled
[    0.499102] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.499111] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.499114] pci 0000:00:01.0: setting latency timer to 64
[    0.499120] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.499123] pci 0000:00:1c.0: setting latency timer to 64
[    0.499129] pci 0000:00:1c.4: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.499132] pci 0000:00:1c.4: setting latency timer to 64
[    0.499138] pci 0000:00:1c.5: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.499141] pci 0000:00:1c.5: setting latency timer to 64
[    0.499146] pci 0000:00:1e.0: setting latency timer to 64
[    0.499149] bus: 00 index 0 io port: [0, ffff]
[    0.499150] bus: 00 index 1 mmio: [0, ffffffff]
[    0.499152] bus: 01 index 0 io port: [c000, cfff]
[    0.499153] bus: 01 index 1 mmio: [fa000000, fe9fffff]
[    0.499155] bus: 01 index 2 mmio: [d0000000, dfffffff]
[    0.499156] bus: 01 index 3 mmio: [0, 0]
[    0.499158] bus: 04 index 0 mmio: [0, 0]
[    0.499160] bus: 04 index 1 mmio: [0, 0]
[    0.499161] bus: 04 index 2 mmio: [f8f00000, f8ffffff]
[    0.499163] bus: 04 index 3 mmio: [0, 0]
[    0.499164] bus: 03 index 0 io port: [d000, dfff]
[    0.499166] bus: 03 index 1 mmio: [feb00000, febfffff]
[    0.499167] bus: 03 index 2 mmio: [0, 0]
[    0.499169] bus: 03 index 3 mmio: [0, 0]
[    0.499170] bus: 02 index 0 mmio: [0, 0]
[    0.499172] bus: 02 index 1 mmio: [fea00000, feafffff]
[    0.499173] bus: 02 index 2 mmio: [0, 0]
[    0.499175] bus: 02 index 3 mmio: [0, 0]
[    0.499176] bus: 05 index 0 io port: [e000, efff]
[    0.499178] bus: 05 index 1 mmio: [0, 0]
[    0.499179] bus: 05 index 2 mmio: [0, 0]
[    0.499181] bus: 05 index 3 io port: [0, ffff]
[    0.499182] bus: 05 index 4 mmio: [0, ffffffff]
[    0.499188] NET: Registered protocol family 2
[    0.500617] Switched to high resolution mode on CPU 1
[    0.504082] Switched to high resolution mode on CPU 0
[    0.512068] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.512256] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.512480] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.512601] TCP: Hash tables configured (established 131072 bind 65536)
[    0.512604] TCP reno registered
[    0.520084] NET: Registered protocol family 1
[    0.520182] checking if image is initramfs... it is
[    1.027114] Freeing initrd memory: 7959k freed
[    1.027901] audit: initializing netlink socket (disabled)
[    1.027918] type=2000 audit(1242233539.024:1): initialized
[    1.031669] highmem bounce pool size: 64 pages
[    1.031674] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.033335] VFS: Disk quotas dquot_6.5.1
[    1.033394] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.033464] msgmni has been set to 1743
[    1.033550] io scheduler noop registered
[    1.033552] io scheduler anticipatory registered
[    1.033554] io scheduler deadline registered
[    1.033562] io scheduler cfq registered (default)
[    1.033683] pci 0000:01:00.0: Boot video device
[    1.033765] pcieport-driver 0000:00:01.0: setting latency timer to 64
[    1.033790] pcieport-driver 0000:00:01.0: found MSI capability
[    1.033812] pci_express 0000:00:01.0:pcie00: allocate port service
[    1.033839] pci_express 0000:00:01.0:pcie03: allocate port service
[    1.033898] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    1.033924] pcieport-driver 0000:00:1c.0: found MSI capability
[    1.033950] pci_express 0000:00:1c.0:pcie00: allocate port service
[    1.033981] pci_express 0000:00:1c.0:pcie02: allocate port service
[    1.034008] pci_express 0000:00:1c.0:pcie03: allocate port service
[    1.034073] pcieport-driver 0000:00:1c.4: setting latency timer to 64
[    1.034100] pcieport-driver 0000:00:1c.4: found MSI capability
[    1.034126] pci_express 0000:00:1c.4:pcie00: allocate port service
[    1.034153] pci_express 0000:00:1c.4:pcie02: allocate port service
[    1.034181] pci_express 0000:00:1c.4:pcie03: allocate port service
[    1.034246] pcieport-driver 0000:00:1c.5: setting latency timer to 64
[    1.034272] pcieport-driver 0000:00:1c.5: found MSI capability
[    1.034298] pci_express 0000:00:1c.5:pcie00: allocate port service
[    1.034327] pci_express 0000:00:1c.5:pcie02: allocate port service
[    1.034353] pci_express 0000:00:1c.5:pcie03: allocate port service
[    1.034579] isapnp: Scanning for PnP cards...
[    1.387356] isapnp: No Plug & Play device found
[    1.410166] hpet_resources: 0xfed00000 is busy
[    1.410224] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.410325] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.410831] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.412016] brd: module loaded
[    1.412067] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    1.412149] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    1.412151] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    1.412663] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.420621] mice: PS/2 mouse device common for all mice
[    1.420731] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    1.420750] rtc0: alarms up to one month, y3k, hpet irqs
[    1.420834] EISA: Probing bus 0 at eisa.0
[    1.420856] EISA: Detected 0 cards.
[    1.420858] cpuidle: using governor ladder
[    1.420860] cpuidle: using governor menu
[    1.421220] TCP cubic registered
[    1.421239] Using IPI No-Shortcut mode
[    1.421356] registered taskstats version 1
[    1.421446]   Magic number: 9:7:894
[    1.421460] tty ptyy4: hash matches
[    1.421498] rtc_cmos 00:03: setting system clock to 2009-05-13 16:52:20 UTC (1242233540)
[    1.421500] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.421502] EDD information not available.
[    1.421641] Freeing unused kernel memory: 428k freed
[    1.421669] Write protecting the kernel text: 2580k
[    1.421687] Write protecting the kernel read-only data: 940k
[    1.438843] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    1.529564] fuse init (API version 7.9)
[    1.685681] ACPI: SSDT 7FF8E0D0, 01D2 (r1    AMI   CPU1PM        1 INTL 20060113)
[    1.685985] processor ACPI0007:00: registered as cooling_device0
[    1.686197] ACPI: SSDT 7FF8E2B0, 0143 (r1    AMI   CPU2PM        1 INTL 20060113)
[    1.686481] processor ACPI0007:01: registered as cooling_device1
[    2.015447] Floppy drive(s): fd0 is 1.44M
[    2.025498] usbcore: registered new interface driver usbfs
[    2.025519] usbcore: registered new interface driver hub
[    2.025673] usbcore: registered new device driver usb
[    2.028427] atl1 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    2.028435] atl1 0000:02:00.0: setting latency timer to 64
[    2.028449] atl1 0000:02:00.0: version 2.1.3
[    2.035633] No dock devices found.
[    2.046420] FDC 0 is a post-1991 82077
[    2.053672] SCSI subsystem initialized
[    2.066659] libata version 3.00 loaded.
[    2.075644] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    2.075656] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    2.075656] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    2.075685] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    2.079579] ehci_hcd 0000:00:1a.7: debug port 1
[    2.079584] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    2.079594] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xf9fffc00
[    2.092518] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    2.092610] usb usb1: configuration #1 chosen from 1 choice
[    2.092630] hub 1-0:1.0: USB hub found
[    2.092635] hub 1-0:1.0: 6 ports detected
[    2.100388] USB Universal Host Controller Interface driver v3.0
[    2.300986] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.300994] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    2.300997] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    2.301017] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 2
[    2.301043] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000b800
[    2.301110] usb usb2: configuration #1 chosen from 1 choice
[    2.301130] hub 2-0:1.0: USB hub found
[    2.301135] hub 2-0:1.0: 2 ports detected
[    2.508182] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    2.508196] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    2.508198] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    2.508216] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 3
[    2.508241] uhci_hcd 0000:00:1a.1: irq 21, io base 0x0000b880
[    2.508307] usb usb3: configuration #1 chosen from 1 choice
[    2.508327] hub 3-0:1.0: USB hub found
[    2.508331] hub 3-0:1.0: 2 ports detected
[    2.524031] usb 1-2: new high speed USB device using ehci_hcd and address 3
[    2.612147] uhci_hcd 0000:00:1a.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    2.612153] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[    2.612156] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    2.612182] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 4
[    2.612204] uhci_hcd 0000:00:1a.2: irq 18, io base 0x0000bc00
[    2.612263] usb usb4: configuration #1 chosen from 1 choice
[    2.612281] hub 4-0:1.0: USB hub found
[    2.612285] hub 4-0:1.0: 2 ports detected
[    2.775206] usb 1-2: configuration #1 chosen from 1 choice
[    2.820154] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    2.820166] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    2.820169] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    2.820201] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[    2.824085] ehci_hcd 0000:00:1d.7: debug port 1
[    2.824090] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    2.824098] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xf9fff800
[    2.836539] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    2.836619] usb usb5: configuration #1 chosen from 1 choice
[    2.836645] hub 5-0:1.0: USB hub found
[    2.836650] hub 5-0:1.0: 6 ports detected
[    2.940400] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    2.940405] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    2.940408] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    2.940546] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
[    2.940565] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000b080
[    2.940751] usb usb6: configuration #1 chosen from 1 choice
[    2.940773] hub 6-0:1.0: USB hub found
[    2.940778] hub 6-0:1.0: 2 ports detected
[    3.004021] usb 2-1: new full speed USB device using uhci_hcd and address 2
[    3.044415] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    3.044419] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    3.044422] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    3.044440] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
[    3.044462] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000b400
[    3.044523] usb usb7: configuration #1 chosen from 1 choice
[    3.044544] hub 7-0:1.0: USB hub found
[    3.044548] hub 7-0:1.0: 2 ports detected
[    3.148470] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    3.148475] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    3.148477] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    3.148496] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
[    3.148514] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000b480
[    3.148577] usb usb8: configuration #1 chosen from 1 choice
[    3.148596] hub 8-0:1.0: USB hub found
[    3.148601] hub 8-0:1.0: 2 ports detected
[    3.161342] usb 2-1: configuration #1 chosen from 1 choice
[    3.252168] ata_piix 0000:00:1f.2: version 2.12
[    3.252179] ata_piix 0000:00:1f.2: PCI INT B -> GSI 22 (level, low) -> IRQ 22
[    3.252183] ata_piix 0000:00:1f.2: MAP [ P0 -- P1 -- ]
[    3.252226] ata_piix 0000:00:1f.2: setting latency timer to 64
[    3.252892] scsi0 : ata_piix
[    3.252956] scsi1 : ata_piix
[    3.254111] ata1: SATA max UDMA/133 cmd 0xa000 ctl 0x9c00 bmdma 0x9480 irq 22
[    3.254114] ata2: SATA max UDMA/133 cmd 0x9880 ctl 0x9800 bmdma 0x9488 irq 22
[    3.404019] usb 4-1: new low speed USB device using uhci_hcd and address 2
[    3.578522] usb 4-1: configuration #1 chosen from 1 choice
[    3.581924] usbcore: registered new interface driver hiddev
[    3.581928] usbcore: registered new interface driver libusual
[    3.586713] Initializing USB Mass Storage driver...
[    3.633840] input: Western Digital My Book as /devices/pci0000:00/0000:00:1a.7/usb1/1-2/1-2:1.1/input/input2
[    3.633888] input,hidraw0: USB HID v1.11 Device [Western Digital My Book] on usb-0000:00:1a.7-2
[    3.634322] scsi2 : SCSI emulation for USB Mass Storage devices
[    3.635020] usb-storage: device found at 3
[    3.635022] usb-storage: waiting for device to settle before scanning
[    3.652482] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1a.2/usb4/4-1/4-1:1.0/input/input3
[    3.652721] input,hidraw1: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:1a.2-1
[    3.652742] usbcore: registered new interface driver usb-storage
[    3.652744] USB Mass Storage support registered.
[    3.653393] usbcore: registered new interface driver usbhid
[    3.653396] usbhid: v2.6:USB HID core driver
[    3.728048] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    3.752191] ata1.00: ATAPI: LITE-ON DVDRW LH-20A1S, 9L08, max UDMA/100
[    3.784201] ata1.00: configured for UDMA/100
[    4.260044] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    4.292195] ata2.00: ATAPI: ATAPI   DVD D  DH16D2S, EP53, max UDMA/100
[    4.332201] ata2.00: configured for UDMA/100
[    4.333373] scsi 0:0:0:0: CD-ROM            LITE-ON  DVDRW LH-20A1S   9L08 PQ: 0 ANSI: 5
[    4.333477] scsi 0:0:0:0: Attached scsi generic sg0 type 5
[    4.334837] scsi 1:0:0:0: CD-ROM            ATAPI    DVD D  DH16D2S   EP53 PQ: 0 ANSI: 5
[    4.334923] scsi 1:0:0:0: Attached scsi generic sg1 type 5
[    4.334963] ata_piix 0000:00:1f.5: PCI INT B -> GSI 22 (level, low) -> IRQ 22
[    4.334967] ata_piix 0000:00:1f.5: MAP [ P0 -- P1 -- ]
[    4.335008] ata_piix 0000:00:1f.5: setting latency timer to 64
[    4.335733] scsi3 : ata_piix
[    4.336155] scsi4 : ata_piix
[    4.337226] ata3: SATA max UDMA/133 cmd 0xb000 ctl 0xac00 bmdma 0xa480 irq 22
[    4.337229] ata4: SATA max UDMA/133 cmd 0xa880 ctl 0xa800 bmdma 0xa488 irq 22
[    4.666548] ata3: SATA link down (SStatus 0 SControl 300)
[    5.140067] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    5.148204] ata4.00: ATA-8: WDC WD5000AAKS-65YGA0, 12.01C02, max UDMA/133
[    5.148206] ata4.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    5.164201] ata4.00: configured for UDMA/133
[    5.164260] scsi 4:0:0:0: Direct-Access     ATA      WDC WD5000AAKS-6 12.0 PQ: 0 ANSI: 5
[    5.164552] scsi 4:0:0:0: Attached scsi generic sg2 type 0
[    5.164607] ahci 0000:03:00.0: version 3.0
[    5.171369] pata_acpi 0000:03:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    5.171391] pata_acpi 0000:03:00.0: setting latency timer to 64
[    5.171402] pata_acpi 0000:03:00.0: PCI INT A disabled
[    5.173535] pata_marvell 0000:03:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    5.173553] pata_marvell 0000:03:00.0: setting latency timer to 64
[    5.173586] scsi5 : pata_marvell
[    5.173635] scsi6 : pata_marvell
[    5.173662] ata5: PATA max UDMA/100 cmd 0xdc00 ctl 0xd880 bmdma 0xd400 irq 16
[    5.173664] ata6: PATA max UDMA/133 cmd 0xd800 ctl 0xd480 bmdma 0xd408 irq 16
[    5.221386] Driver 'sr' needs updating - please use bus_type methods
[    5.224606] Driver 'sd' needs updating - please use bus_type methods
[    5.229269] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    5.229272] Uniform CD-ROM driver Revision: 3.20
[    5.229350] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    5.234765] sr1: scsi3-mmc drive: 48x/48x cd/rw xa/form2 cdda tray
[    5.234829] sr 1:0:0:0: Attached scsi CD-ROM sr1
[    5.234903] sd 4:0:0:0: [sda] 976773168 512-byte hardware sectors (500108 MB)
[    5.234918] sd 4:0:0:0: [sda] Write Protect is off
[    5.234920] sd 4:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.234946] sd 4:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.234984] sd 4:0:0:0: [sda] 976773168 512-byte hardware sectors (500108 MB)
[    5.234994] sd 4:0:0:0: [sda] Write Protect is off
[    5.234996] sd 4:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.235014] sd 4:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.235016]  sda: sda1 sda2 < sda5 sda6 sda7 > sda3 sda4
[    5.302383] sd 4:0:0:0: [sda] Attached SCSI disk
[    5.930308] PM: Starting manual resume from disk
[    5.930311] PM: Resume from partition 8:4
[    5.930312] PM: Checking hibernation image.
[    5.930513] PM: Resume from disk failed.
[    5.966257] kjournald starting.  Commit interval 5 seconds
[    5.966270] EXT3-fs: mounted filesystem with ordered data mode.
[    8.643617] usb-storage: device scan complete
[    8.660361] scsi 2:0:0:0: Direct-Access     WD       My Book          1028 PQ: 0 ANSI: 4
[    8.683095] sd 2:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
[    8.696343] sd 2:0:0:0: [sdb] Write Protect is off
[    8.696345] sd 2:0:0:0: [sdb] Mode Sense: 10 00 00 00
[    8.696348] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[    8.718842] sd 2:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
[    8.732093] sd 2:0:0:0: [sdb] Write Protect is off
[    8.732096] sd 2:0:0:0: [sdb] Mode Sense: 10 00 00 00
[    8.732098] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[    8.732102]  sdb: sdb1
[    9.304813] sd 2:0:0:0: [sdb] Attached SCSI disk
[    9.304904] sd 2:0:0:0: Attached scsi generic sg3 type 0
[   12.095685] ip_tables: (C) 2000-2006 Netfilter Core Team
[   12.122699] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[   12.122793] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Plase use
[   12.122795] nf_conntrack.acct=1 kernel paramater, acct=1 nf_conntrack module option or
[   12.122797] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
[   12.230041] udevd version 124 started
[   12.376143] Linux agpgart interface v0.103
[   12.515317] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   12.517773] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input4
[   12.520547] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   12.548016] ACPI: Power Button (FF) [PWRF]
[   12.548098] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input5
[   12.580016] ACPI: Power Button (CM) [PWRB]
[   13.053880] nvidia: module license 'NVIDIA' taints kernel.
[   13.313132] iTCO_vendor_support: vendor-support=0
[   13.364374] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   13.364381] nvidia 0000:01:00.0: setting latency timer to 64
[   13.365384] NVRM: loading NVIDIA UNIX x86 Kernel Module  180.11  Wed Nov 26 10:53:26 PST 2008
[   13.432684] input: PC Speaker as /devices/platform/pcspkr/input/input6
[   13.463136] Linux video capture interface: v2.00
[   13.473837] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.03 (30-Apr-2008)
[   13.563135] gspca: main v2.2.0 registered
[   13.569760] gspca: probing 0c45:612c
[   13.574174] sonixj: Sonix chip id: 12
[   13.577231] gspca: probe ok
[   13.577246] usbcore: registered new interface driver sonixj
[   13.577248] sonixj: registered
[   13.616739] iTCO_wdt: Found a ICH9 TCO device (Version=2, TCOBASE=0x0860)
[   13.616789] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   14.122572] CA0106 0000:05:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   14.122587] snd-ca0106: Model 100a Rev 00000000 Serial 100a1102
[   15.020898] lp: driver loaded but no devices found
[   15.062489] w83627ehf: Found W83627DHG chip at 0x290
[   15.062575] w83627ehf w83627ehf.656: VID pins in output mode, CPU VID not available
[   15.078256] coretemp coretemp.0: Using relative temperature scale!
[   15.078286] coretemp coretemp.1: Using relative temperature scale!
[   15.182893] Adding 979956k swap on /dev/sda4.  Priority:-1 extents:1 across:979956k
[   15.721236] EXT3 FS on sda3, internal journal
[   18.005419] type=1505 audit(1242226357.097:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4397
[   18.123804] type=1505 audit(1242226357.213:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4402
[   18.123924] type=1505 audit(1242226357.213:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4402
[   18.603288] ACPI: WMI: Mapper loaded
[   19.447064] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   19.492404] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   19.492407] apm: disabled - APM is not SMP safe.
[   19.625758] ppdev: user-space parallel port driver
[   22.873435] Bluetooth: Core ver 2.13
[   22.873590] NET: Registered protocol family 31
[   22.873593] Bluetooth: HCI device and connection manager initialized
[   22.873596] Bluetooth: HCI socket layer initialized
[   22.889062] Bluetooth: L2CAP ver 2.11
[   22.889066] Bluetooth: L2CAP socket layer initialized
[   22.896789] Bluetooth: RFCOMM socket layer initialized
[   22.897189] Bluetooth: RFCOMM TTY layer initialized
[   22.897192] Bluetooth: RFCOMM ver 1.10
[   22.909421] Bluetooth: SCO (Voice Link) ver 0.6
[   22.909425] Bluetooth: SCO socket layer initialized
[   22.930517] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   22.930522] Bluetooth: BNEP filters: protocol multicast
[   22.959443] Bridge firewalling registered
[   27.024611] atl1 0000:02:00.0: eth0 link is up 100 Mbps full duplex
[   27.332127] NET: Registered protocol family 17
[   41.739387] NET: Registered protocol family 10
[   41.740437] lo: Disabled Privacy Extensions
[   52.696006] eth0: no IPv6 routers present
[  110.400417] process `skype' is using obsolete setsockopt SO_BSDCOMPAT
```

---

### Post by Mauro22 on 2009-05-13
This is a spanish forum, my friend...


I translated to spanish, so someone could help you.

"Hola a todo el mundo,
Necesito ayuda para configurar mi camara correctamente. Intente millones de cosas de internet pero todavia no funciona.
Alguien tiene alguna idea?
atte
James"

lsusb y dmesg.

---

### Post by James Dee on 2009-05-13
sorry...
i will change the group...

> **Mauro22 said:**
> This is a spanish forum, my friend...


I translated to spanish, so someone could help you.

"Hola a todo el mundo,
Necesito ayuda para configurar mi camara correctamente. Intente millones de cosas de internet pero todavia no funciona.
Alguien tiene alguna idea?
atte
James"

lsusb y dmesg.

---

### Post by James Dee on 2009-05-13
hello everybody,
i need help with setting up my camera to work properly. i try million things from net but still nothing.
does anybody have some idea?
atb
james

this is lsusb:
```
print "Bus 002 Device 002: ID 0c45:612c Microdia PC Camera (SN9C110)
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 046d:c510 Logitech, Inc. Cordless Mouse
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 1058:1102 Western Digital Technologies, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub"
```

this is from dmesg:

```
print " [    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.27-14-generic (buildd@palmer) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu12) ) #1 SMP Wed Apr 15 18:59:16 UTC 2009 (Ubuntu 2.6.27-14.33-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007ff80000 (usable)
[    0.000000]  BIOS-e820: 000000007ff80000 - 000000007ff8e000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007ff8e000 - 000000007ffe0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007ffe0000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.4 present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working it around.
[    0.000000] last_pfn = 0x7ff80 max_arch_pfn = 0x100000
[    0.000000] kernel direct mapping tables up to 38000000 @ 10000-15000
[    0.000000] RAMDISK: 3782a000 - 37fefe76
[    0.000000] ACPI: RSDP 000FBDC0, 0014 (r0 ACPIAM)
[    0.000000] ACPI: RSDT 7FF80000, 003C (r1 A_M_I_ OEMRSDT   7000719 MSFT       97)
[    0.000000] ACPI: FACP 7FF80200, 0084 (r2 A_M_I_ OEMFACP   7000719 MSFT       97)
[    0.000000] ACPI: DSDT 7FF805C0, 7A0C (r1  A0807 A0807000        0 INTL 20060113)
[    0.000000] ACPI: FACS 7FF8E000, 0040
[    0.000000] ACPI: APIC 7FF80390, 006C (r1 A_M_I_ OEMAPIC   7000719 MSFT       97)
[    0.000000] ACPI: MCFG 7FF80400, 003C (r1 A_M_I_ OEMMCFG   7000719 MSFT       97)
[    0.000000] ACPI: OEMB 7FF8E040, 0081 (r1 A_M_I_ AMI_OEM   7000719 MSFT       97)
[    0.000000] ACPI: HPET 7FF87FD0, 0038 (r1 A_M_I_ OEMHPET   7000719 MSFT       97)
[    0.000000] ACPI: OSFR 7FF88010, 00B0 (r1 A_M_I_ OEMOSFR   7000719 MSFT       97)
[    0.000000] 1151MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 38000000
[    0.000000]   low ram: 00000000 - 38000000
[    0.000000]   bootmap 00011000 - 00018000
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 0038000000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00005c39e0]    TEXT DATA BSS ==> [0000100000 - 00005c39e0]
[    0.000000]   #4 [003782a000 - 0037fefe76]          RAMDISK ==> [003782a000 - 0037fefe76]
[    0.000000]   #5 [00005c4000 - 00005c7000]    INIT_PG_TABLE ==> [00005c4000 - 00005c7000]
[    0.000000]   #6 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000]
[    0.000000]   #7 [0000010000 - 0000011000]          PGTABLE ==> [0000010000 - 0000011000]
[    0.000000]   #8 [0000011000 - 0000018000]          BOOTMAP ==> [0000011000 - 0000018000]
[    0.000000] found SMP MP-table at [c00ff780] 000ff780
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x00038000
[    0.000000]   HighMem  0x00038000 -> 0x0007ff80
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0007ff80
[    0.000000] On node 0 totalpages: 524047
[    0.000000] free_area_init_node: node 0, pgdat c048c700, node_mem_map c1000240
[    0.000000]   DMA zone: 3947 pages, LIFO batch:0
[    0.000000]   Normal zone: 223300 pages, LIFO batch:31
[    0.000000]   HighMem zone: 292193 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
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
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e4000
[    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:7ee00000)
[    0.000000] PERCPU: Allocating 41628 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 4, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 519440
[    0.000000] Kernel command line: root=UUID=cb76defa-f2ef-4f5b-ba59-de658539fc20 ro quiet splash 
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] TSC: PIT calibration confirmed by PMTIMER.
[    0.000000] TSC: using PIT calibration value
[    0.000000] Detected 2669.764 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] Memory: 2063112k/2096640k available (2578k kernel code, 32312k reserved, 1162k data, 428k init, 1179136k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xf8800000 - 0xff3fe000   ( 107 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[    0.004000]       .init : 0xc04ad000 - 0xc0518000   ( 428 kB)
[    0.004000]       .data : 0xc0384a8a - 0xc04a7680   (1162 kB)
[    0.004000]       .text : 0xc0100000 - 0xc0384a8a   (2578 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] CPA: page pool initialized 1 of 1 pages preallocated
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.004000] hpet clockevent registered
[    0.004000] Calibrating delay loop (skipped), value calculated using timer frequency.. 5339.52 BogoMIPS (lpj=10679056)
[    0.004000] Security Framework initialized
[    0.004000] SELinux:  Disabled at boot.
[    0.004000] AppArmor: AppArmor initialized
[    0.004000] Mount-cache hash table entries: 512
[    0.004000] Initializing cgroup subsys ns
[    0.004000] Initializing cgroup subsys cpuacct
[    0.004000] Initializing cgroup subsys memory
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 4096K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 0
[    0.004000] using mwait in idle threads.
[    0.004000] Checking 'hlt' instruction... OK.
[    0.017431] ACPI: Core revision 20080609
[    0.019667] ACPI: Checking initramfs for custom DSDT
[    0.272185] ENABLING IO-APIC IRQs
[    0.272349] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.316830] CPU0: Intel(R) Core(TM)2 Duo CPU     E6750  @ 2.66GHz stepping 0b
[    0.320020] Booting processor 1/1 ip 6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 5339.51 BogoMIPS (lpj=10679032)
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 4096K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.404543] CPU1: Intel(R) Core(TM)2 Duo CPU     E6750  @ 2.66GHz stepping 0b
[    0.404555] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.408040] Brought up 2 CPUs
[    0.408042] Total of 2 processors activated (10679.04 BogoMIPS).
[    0.408059] CPU0 attaching sched-domain:
[    0.408062]  domain 0: span 0-1 level MC
[    0.408063]   groups: 0 1
[    0.408068] CPU1 attaching sched-domain:
[    0.408070]  domain 0: span 0-1 level MC
[    0.408071]   groups: 1 0
[    0.408125] net_namespace: 840 bytes
[    0.408125] Booting paravirtualized kernel on bare hardware
[    0.408218] Time: 16:52:19  Date: 05/13/09
[    0.408237] NET: Registered protocol family 16
[    0.408251] EISA bus registered
[    0.408251] ACPI: bus type pci registered
[    0.408251] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.408251] PCI: Not using MMCONFIG.
[    0.408251] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=5
[    0.408251] PCI: Using configuration type 1 for base access
[    0.408748] ACPI: EC: Look up EC in DSDT
[    0.419177] ACPI: Interpreter enabled
[    0.419182] ACPI: (supports S0 S1 S3 S4 S5)
[    0.419195] ACPI: Using IOAPIC for interrupt routing
[    0.419240] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.421320] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
[    0.421322] PCI: Using MMCONFIG for extended config space
[    0.428129] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.428129] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.428129] pci 0000:00:01.0: PME# disabled
[    0.428151] PCI: 0000:00:1a.0 reg 20 io port: [b800, b81f]
[    0.428210] PCI: 0000:00:1a.1 reg 20 io port: [b880, b89f]
[    0.428268] PCI: 0000:00:1a.2 reg 20 io port: [bc00, bc1f]
[    0.428330] PCI: 0000:00:1a.7 reg 10 32bit mmio: [f9fffc00, f9ffffff]
[    0.428386] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.428390] pci 0000:00:1a.7: PME# disabled
[    0.428441] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.428444] pci 0000:00:1c.0: PME# disabled
[    0.428495] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.428498] pci 0000:00:1c.4: PME# disabled
[    0.428546] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    0.428550] pci 0000:00:1c.5: PME# disabled
[    0.428586] PCI: 0000:00:1d.0 reg 20 io port: [b080, b09f]
[    0.428645] PCI: 0000:00:1d.1 reg 20 io port: [b400, b41f]
[    0.428703] PCI: 0000:00:1d.2 reg 20 io port: [b480, b49f]
[    0.428765] PCI: 0000:00:1d.7 reg 10 32bit mmio: [f9fff800, f9fffbff]
[    0.428821] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.428824] pci 0000:00:1d.7: PME# disabled
[    0.428923] pci 0000:00:1f.0: quirk: region 0800-087f claimed by ICH6 ACPI/GPIO/TCO
[    0.428926] pci 0000:00:1f.0: quirk: region 0480-04bf claimed by ICH6 GPIO
[    0.428964] PCI: 0000:00:1f.2 reg 10 io port: [a000, a007]
[    0.428969] PCI: 0000:00:1f.2 reg 14 io port: [9c00, 9c03]
[    0.428974] PCI: 0000:00:1f.2 reg 18 io port: [9880, 9887]
[    0.428979] PCI: 0000:00:1f.2 reg 1c io port: [9800, 9803]
[    0.428983] PCI: 0000:00:1f.2 reg 20 io port: [9480, 948f]
[    0.428988] PCI: 0000:00:1f.2 reg 24 io port: [9400, 940f]
[    0.429026] PCI: 0000:00:1f.3 reg 10 64bit mmio: [f9fff400, f9fff4ff]
[    0.429037] PCI: 0000:00:1f.3 reg 20 io port: [400, 41f]
[    0.429073] PCI: 0000:00:1f.5 reg 10 io port: [b000, b007]
[    0.429077] PCI: 0000:00:1f.5 reg 14 io port: [ac00, ac03]
[    0.429082] PCI: 0000:00:1f.5 reg 18 io port: [a880, a887]
[    0.429086] PCI: 0000:00:1f.5 reg 1c io port: [a800, a803]
[    0.429091] PCI: 0000:00:1f.5 reg 20 io port: [a480, a48f]
[    0.429095] PCI: 0000:00:1f.5 reg 24 io port: [a400, a40f]
[    0.429143] PCI: 0000:01:00.0 reg 10 32bit mmio: [fd000000, fdffffff]
[    0.429150] PCI: 0000:01:00.0 reg 14 64bit mmio: [d0000000, dfffffff]
[    0.429158] PCI: 0000:01:00.0 reg 1c 64bit mmio: [fa000000, fbffffff]
[    0.429162] PCI: 0000:01:00.0 reg 24 io port: [cc00, cc7f]
[    0.429167] PCI: 0000:01:00.0 reg 30 32bit mmio: [fe9e0000, fe9fffff]
[    0.429215] PCI: bridge 0000:00:01.0 io port: [c000, cfff]
[    0.429218] PCI: bridge 0000:00:01.0 32bit mmio: [fa000000, fe9fffff]
[    0.429221] PCI: bridge 0000:00:01.0 64bit mmio pref: [d0000000, dfffffff]
[    0.429258] PCI: bridge 0000:00:1c.0 64bit mmio pref: [f8f00000, f8ffffff]
[    0.429297] PCI: 0000:03:00.0 reg 10 io port: [dc00, dc07]
[    0.429304] PCI: 0000:03:00.0 reg 14 io port: [d880, d883]
[    0.429311] PCI: 0000:03:00.0 reg 18 io port: [d800, d807]
[    0.429318] PCI: 0000:03:00.0 reg 1c io port: [d480, d483]
[    0.429324] PCI: 0000:03:00.0 reg 20 io port: [d400, d40f]
[    0.429331] PCI: 0000:03:00.0 reg 24 32bit mmio: [febffc00, febfffff]
[    0.429379] pci 0000:03:00.0: supports D1
[    0.429380] pci 0000:03:00.0: PME# supported from D0 D1 D3hot
[    0.429384] pci 0000:03:00.0: PME# disabled
[    0.429411] PCI: bridge 0000:00:1c.4 io port: [d000, dfff]
[    0.429415] PCI: bridge 0000:00:1c.4 32bit mmio: [feb00000, febfffff]
[    0.429464] PCI: 0000:02:00.0 reg 10 64bit mmio: [feac0000, feafffff]
[    0.429493] PCI: 0000:02:00.0 reg 30 32bit mmio: [feaa0000, feabffff]
[    0.429534] pci 0000:02:00.0: PME# supported from D3hot D3cold
[    0.429538] pci 0000:02:00.0: PME# disabled
[    0.429567] PCI: bridge 0000:00:1c.5 32bit mmio: [fea00000, feafffff]
[    0.429598] PCI: 0000:05:00.0 reg 10 io port: [ec00, ec1f]
[    0.429643] pci 0000:05:00.0: supports D1
[    0.429644] pci 0000:05:00.0: supports D2
[    0.429679] pci 0000:00:1e.0: transparent bridge
[    0.429682] PCI: bridge 0000:00:1e.0 io port: [e000, efff]
[    0.429704] bus 00 -> node 0
[    0.429709] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.429935] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P2._PRT]
[    0.430028] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.430158] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P8._PRT]
[    0.430249] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P9._PRT]
[    0.430353] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[    0.444822] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.444822] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.444822] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.444822] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11 12 *14 15)
[    0.444822] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.444822] ACPI: PCI Interrupt Link [LNKF] (IRQs *3 4 5 6 7 10 11 12 14 15)
[    0.444822] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 *15)
[    0.444904] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 *7 10 11 12 14 15)
[    0.444954] ACPI Warning (tbutils-0217): Incorrect checksum in table [OEMB] - C7, should be BE [20080609]
[    0.444954] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.444954] pnp: PnP ACPI init
[    0.444954] ACPI: bus type pnp registered
[    0.448557] pnp: PnP ACPI: found 15 devices
[    0.448557] ACPI: ACPI bus type pnp unregistered
[    0.448557] PnPBIOS: Disabled by ACPI PNP
[    0.448557] PCI: Using ACPI for IRQ routing
[    0.456036] NET: Registered protocol family 8
[    0.456039] NET: Registered protocol family 20
[    0.456054] NetLabel: Initializing
[    0.456054] NetLabel:  domain hash size = 128
[    0.456054] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.456061] NetLabel:  unlabeled traffic allowed by default
[    0.456067] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.456072] hpet0: 4 64-bit timers, 14318180 Hz
[    0.457729] tracer: 772 pages allocated for 65536 entries of 48 bytes
[    0.457731]    actual entries 65620
[    0.457784] AppArmor: AppArmor Filesystem Enabled
[    0.457800] ACPI: RTC can wake from S4
[    0.464066] system 00:01: iomem range 0xfed14000-0xfed19fff has been reserved
[    0.464076] system 00:07: ioport range 0x290-0x297 has been reserved
[    0.464082] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
[    0.464085] system 00:08: ioport range 0x800-0x87f has been reserved
[    0.464088] system 00:08: ioport range 0x480-0x4bf has been reserved
[    0.464091] system 00:08: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    0.464095] system 00:08: iomem range 0xfed20000-0xfed3ffff has been reserved
[    0.464098] system 00:08: iomem range 0xfed50000-0xfed8ffff has been reserved
[    0.464100] system 00:08: iomem range 0xffa00000-0xffafffff has been reserved
[    0.464104] system 00:08: iomem range 0xffb00000-0xffbfffff has been reserved
[    0.464107] system 00:08: iomem range 0xffe00000-0xffefffff has been reserved
[    0.464110] system 00:08: iomem range 0xfff00000-0xfffffffe could not be reserved
[    0.464117] system 00:0b: iomem range 0xfec00000-0xfec00fff has been reserved
[    0.464120] system 00:0b: iomem range 0xfee00000-0xfee00fff could not be reserved
[    0.464126] system 00:0d: iomem range 0xe0000000-0xefffffff has been reserved
[    0.464132] system 00:0e: iomem range 0x0-0x9ffff could not be reserved
[    0.464135] system 00:0e: iomem range 0xc0000-0xcffff could not be reserved
[    0.464137] system 00:0e: iomem range 0xe0000-0xfffff could not be reserved
[    0.464141] system 00:0e: iomem range 0x100000-0x7fffffff could not be reserved
[    0.499040] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.499042] pci 0000:00:01.0:   IO window: 0xc000-0xcfff
[    0.499046] pci 0000:00:01.0:   MEM window: 0xfa000000-0xfe9fffff
[    0.499048] pci 0000:00:01.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
[    0.499052] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:04
[    0.499053] pci 0000:00:1c.0:   IO window: disabled
[    0.499057] pci 0000:00:1c.0:   MEM window: disabled
[    0.499060] pci 0000:00:1c.0:   PREFETCH window: 0x000000f8f00000-0x000000f8ffffff
[    0.499065] pci 0000:00:1c.4: PCI bridge, secondary bus 0000:03
[    0.499067] pci 0000:00:1c.4:   IO window: 0xd000-0xdfff
[    0.499071] pci 0000:00:1c.4:   MEM window: 0xfeb00000-0xfebfffff
[    0.499074] pci 0000:00:1c.4:   PREFETCH window: disabled
[    0.499079] pci 0000:00:1c.5: PCI bridge, secondary bus 0000:02
[    0.499081] pci 0000:00:1c.5:   IO window: disabled
[    0.499085] pci 0000:00:1c.5:   MEM window: 0xfea00000-0xfeafffff
[    0.499088] pci 0000:00:1c.5:   PREFETCH window: disabled
[    0.499092] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:05
[    0.499095] pci 0000:00:1e.0:   IO window: 0xe000-0xefff
[    0.499099] pci 0000:00:1e.0:   MEM window: disabled
[    0.499102] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.499111] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.499114] pci 0000:00:01.0: setting latency timer to 64
[    0.499120] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.499123] pci 0000:00:1c.0: setting latency timer to 64
[    0.499129] pci 0000:00:1c.4: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.499132] pci 0000:00:1c.4: setting latency timer to 64
[    0.499138] pci 0000:00:1c.5: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.499141] pci 0000:00:1c.5: setting latency timer to 64
[    0.499146] pci 0000:00:1e.0: setting latency timer to 64
[    0.499149] bus: 00 index 0 io port: [0, ffff]
[    0.499150] bus: 00 index 1 mmio: [0, ffffffff]
[    0.499152] bus: 01 index 0 io port: [c000, cfff]
[    0.499153] bus: 01 index 1 mmio: [fa000000, fe9fffff]
[    0.499155] bus: 01 index 2 mmio: [d0000000, dfffffff]
[    0.499156] bus: 01 index 3 mmio: [0, 0]
[    0.499158] bus: 04 index 0 mmio: [0, 0]
[    0.499160] bus: 04 index 1 mmio: [0, 0]
[    0.499161] bus: 04 index 2 mmio: [f8f00000, f8ffffff]
[    0.499163] bus: 04 index 3 mmio: [0, 0]
[    0.499164] bus: 03 index 0 io port: [d000, dfff]
[    0.499166] bus: 03 index 1 mmio: [feb00000, febfffff]
[    0.499167] bus: 03 index 2 mmio: [0, 0]
[    0.499169] bus: 03 index 3 mmio: [0, 0]
[    0.499170] bus: 02 index 0 mmio: [0, 0]
[    0.499172] bus: 02 index 1 mmio: [fea00000, feafffff]
[    0.499173] bus: 02 index 2 mmio: [0, 0]
[    0.499175] bus: 02 index 3 mmio: [0, 0]
[    0.499176] bus: 05 index 0 io port: [e000, efff]
[    0.499178] bus: 05 index 1 mmio: [0, 0]
[    0.499179] bus: 05 index 2 mmio: [0, 0]
[    0.499181] bus: 05 index 3 io port: [0, ffff]
[    0.499182] bus: 05 index 4 mmio: [0, ffffffff]
[    0.499188] NET: Registered protocol family 2
[    0.500617] Switched to high resolution mode on CPU 1
[    0.504082] Switched to high resolution mode on CPU 0
[    0.512068] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.512256] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.512480] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.512601] TCP: Hash tables configured (established 131072 bind 65536)
[    0.512604] TCP reno registered
[    0.520084] NET: Registered protocol family 1
[    0.520182] checking if image is initramfs... it is
[    1.027114] Freeing initrd memory: 7959k freed
[    1.027901] audit: initializing netlink socket (disabled)
[    1.027918] type=2000 audit(1242233539.024:1): initialized
[    1.031669] highmem bounce pool size: 64 pages
[    1.031674] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.033335] VFS: Disk quotas dquot_6.5.1
[    1.033394] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.033464] msgmni has been set to 1743
[    1.033550] io scheduler noop registered
[    1.033552] io scheduler anticipatory registered
[    1.033554] io scheduler deadline registered
[    1.033562] io scheduler cfq registered (default)
[    1.033683] pci 0000:01:00.0: Boot video device
[    1.033765] pcieport-driver 0000:00:01.0: setting latency timer to 64
[    1.033790] pcieport-driver 0000:00:01.0: found MSI capability
[    1.033812] pci_express 0000:00:01.0:pcie00: allocate port service
[    1.033839] pci_express 0000:00:01.0:pcie03: allocate port service
[    1.033898] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    1.033924] pcieport-driver 0000:00:1c.0: found MSI capability
[    1.033950] pci_express 0000:00:1c.0:pcie00: allocate port service
[    1.033981] pci_express 0000:00:1c.0:pcie02: allocate port service
[    1.034008] pci_express 0000:00:1c.0:pcie03: allocate port service
[    1.034073] pcieport-driver 0000:00:1c.4: setting latency timer to 64
[    1.034100] pcieport-driver 0000:00:1c.4: found MSI capability
[    1.034126] pci_express 0000:00:1c.4:pcie00: allocate port service
[    1.034153] pci_express 0000:00:1c.4:pcie02: allocate port service
[    1.034181] pci_express 0000:00:1c.4:pcie03: allocate port service
[    1.034246] pcieport-driver 0000:00:1c.5: setting latency timer to 64
[    1.034272] pcieport-driver 0000:00:1c.5: found MSI capability
[    1.034298] pci_express 0000:00:1c.5:pcie00: allocate port service
[    1.034327] pci_express 0000:00:1c.5:pcie02: allocate port service
[    1.034353] pci_express 0000:00:1c.5:pcie03: allocate port service
[    1.034579] isapnp: Scanning for PnP cards...
[    1.387356] isapnp: No Plug & Play device found
[    1.410166] hpet_resources: 0xfed00000 is busy
[    1.410224] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.410325] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.410831] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.412016] brd: module loaded
[    1.412067] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    1.412149] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    1.412151] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    1.412663] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.420621] mice: PS/2 mouse device common for all mice
[    1.420731] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    1.420750] rtc0: alarms up to one month, y3k, hpet irqs
[    1.420834] EISA: Probing bus 0 at eisa.0
[    1.420856] EISA: Detected 0 cards.
[    1.420858] cpuidle: using governor ladder
[    1.420860] cpuidle: using governor menu
[    1.421220] TCP cubic registered
[    1.421239] Using IPI No-Shortcut mode
[    1.421356] registered taskstats version 1
[    1.421446]   Magic number: 9:7:894
[    1.421460] tty ptyy4: hash matches
[    1.421498] rtc_cmos 00:03: setting system clock to 2009-05-13 16:52:20 UTC (1242233540)
[    1.421500] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.421502] EDD information not available.
[    1.421641] Freeing unused kernel memory: 428k freed
[    1.421669] Write protecting the kernel text: 2580k
[    1.421687] Write protecting the kernel read-only data: 940k
[    1.438843] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    1.529564] fuse init (API version 7.9)
[    1.685681] ACPI: SSDT 7FF8E0D0, 01D2 (r1    AMI   CPU1PM        1 INTL 20060113)
[    1.685985] processor ACPI0007:00: registered as cooling_device0
[    1.686197] ACPI: SSDT 7FF8E2B0, 0143 (r1    AMI   CPU2PM        1 INTL 20060113)
[    1.686481] processor ACPI0007:01: registered as cooling_device1
[    2.015447] Floppy drive(s): fd0 is 1.44M
[    2.025498] usbcore: registered new interface driver usbfs
[    2.025519] usbcore: registered new interface driver hub
[    2.025673] usbcore: registered new device driver usb
[    2.028427] atl1 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    2.028435] atl1 0000:02:00.0: setting latency timer to 64
[    2.028449] atl1 0000:02:00.0: version 2.1.3
[    2.035633] No dock devices found.
[    2.046420] FDC 0 is a post-1991 82077
[    2.053672] SCSI subsystem initialized
[    2.066659] libata version 3.00 loaded.
[    2.075644] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    2.075656] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    2.075656] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    2.075685] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    2.079579] ehci_hcd 0000:00:1a.7: debug port 1
[    2.079584] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    2.079594] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xf9fffc00
[    2.092518] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    2.092610] usb usb1: configuration #1 chosen from 1 choice
[    2.092630] hub 1-0:1.0: USB hub found
[    2.092635] hub 1-0:1.0: 6 ports detected
[    2.100388] USB Universal Host Controller Interface driver v3.0
[    2.300986] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.300994] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    2.300997] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    2.301017] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 2
[    2.301043] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000b800
[    2.301110] usb usb2: configuration #1 chosen from 1 choice
[    2.301130] hub 2-0:1.0: USB hub found
[    2.301135] hub 2-0:1.0: 2 ports detected
[    2.508182] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    2.508196] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    2.508198] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    2.508216] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 3
[    2.508241] uhci_hcd 0000:00:1a.1: irq 21, io base 0x0000b880
[    2.508307] usb usb3: configuration #1 chosen from 1 choice
[    2.508327] hub 3-0:1.0: USB hub found
[    2.508331] hub 3-0:1.0: 2 ports detected
[    2.524031] usb 1-2: new high speed USB device using ehci_hcd and address 3
[    2.612147] uhci_hcd 0000:00:1a.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    2.612153] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[    2.612156] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    2.612182] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 4
[    2.612204] uhci_hcd 0000:00:1a.2: irq 18, io base 0x0000bc00
[    2.612263] usb usb4: configuration #1 chosen from 1 choice
[    2.612281] hub 4-0:1.0: USB hub found
[    2.612285] hub 4-0:1.0: 2 ports detected
[    2.775206] usb 1-2: configuration #1 chosen from 1 choice
[    2.820154] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    2.820166] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    2.820169] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    2.820201] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[    2.824085] ehci_hcd 0000:00:1d.7: debug port 1
[    2.824090] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    2.824098] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xf9fff800
[    2.836539] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    2.836619] usb usb5: configuration #1 chosen from 1 choice
[    2.836645] hub 5-0:1.0: USB hub found
[    2.836650] hub 5-0:1.0: 6 ports detected
[    2.940400] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    2.940405] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    2.940408] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    2.940546] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
[    2.940565] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000b080
[    2.940751] usb usb6: configuration #1 chosen from 1 choice
[    2.940773] hub 6-0:1.0: USB hub found
[    2.940778] hub 6-0:1.0: 2 ports detected
[    3.004021] usb 2-1: new full speed USB device using uhci_hcd and address 2
[    3.044415] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    3.044419] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    3.044422] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    3.044440] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
[    3.044462] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000b400
[    3.044523] usb usb7: configuration #1 chosen from 1 choice
[    3.044544] hub 7-0:1.0: USB hub found
[    3.044548] hub 7-0:1.0: 2 ports detected
[    3.148470] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    3.148475] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    3.148477] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    3.148496] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
[    3.148514] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000b480
[    3.148577] usb usb8: configuration #1 chosen from 1 choice
[    3.148596] hub 8-0:1.0: USB hub found
[    3.148601] hub 8-0:1.0: 2 ports detected
[    3.161342] usb 2-1: configuration #1 chosen from 1 choice
[    3.252168] ata_piix 0000:00:1f.2: version 2.12
[    3.252179] ata_piix 0000:00:1f.2: PCI INT B -> GSI 22 (level, low) -> IRQ 22
[    3.252183] ata_piix 0000:00:1f.2: MAP [ P0 -- P1 -- ]
[    3.252226] ata_piix 0000:00:1f.2: setting latency timer to 64
[    3.252892] scsi0 : ata_piix
[    3.252956] scsi1 : ata_piix
[    3.254111] ata1: SATA max UDMA/133 cmd 0xa000 ctl 0x9c00 bmdma 0x9480 irq 22
[    3.254114] ata2: SATA max UDMA/133 cmd 0x9880 ctl 0x9800 bmdma 0x9488 irq 22
[    3.404019] usb 4-1: new low speed USB device using uhci_hcd and address 2
[    3.578522] usb 4-1: configuration #1 chosen from 1 choice
[    3.581924] usbcore: registered new interface driver hiddev
[    3.581928] usbcore: registered new interface driver libusual
[    3.586713] Initializing USB Mass Storage driver...
[    3.633840] input: Western Digital My Book as /devices/pci0000:00/0000:00:1a.7/usb1/1-2/1-2:1.1/input/input2
[    3.633888] input,hidraw0: USB HID v1.11 Device [Western Digital My Book] on usb-0000:00:1a.7-2
[    3.634322] scsi2 : SCSI emulation for USB Mass Storage devices
[    3.635020] usb-storage: device found at 3
[    3.635022] usb-storage: waiting for device to settle before scanning
[    3.652482] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1a.2/usb4/4-1/4-1:1.0/input/input3
[    3.652721] input,hidraw1: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:1a.2-1
[    3.652742] usbcore: registered new interface driver usb-storage
[    3.652744] USB Mass Storage support registered.
[    3.653393] usbcore: registered new interface driver usbhid
[    3.653396] usbhid: v2.6:USB HID core driver
[    3.728048] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    3.752191] ata1.00: ATAPI: LITE-ON DVDRW LH-20A1S, 9L08, max UDMA/100
[    3.784201] ata1.00: configured for UDMA/100
[    4.260044] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    4.292195] ata2.00: ATAPI: ATAPI   DVD D  DH16D2S, EP53, max UDMA/100
[    4.332201] ata2.00: configured for UDMA/100
[    4.333373] scsi 0:0:0:0: CD-ROM            LITE-ON  DVDRW LH-20A1S   9L08 PQ: 0 ANSI: 5
[    4.333477] scsi 0:0:0:0: Attached scsi generic sg0 type 5
[    4.334837] scsi 1:0:0:0: CD-ROM            ATAPI    DVD D  DH16D2S   EP53 PQ: 0 ANSI: 5
[    4.334923] scsi 1:0:0:0: Attached scsi generic sg1 type 5
[    4.334963] ata_piix 0000:00:1f.5: PCI INT B -> GSI 22 (level, low) -> IRQ 22
[    4.334967] ata_piix 0000:00:1f.5: MAP [ P0 -- P1 -- ]
[    4.335008] ata_piix 0000:00:1f.5: setting latency timer to 64
[    4.335733] scsi3 : ata_piix
[    4.336155] scsi4 : ata_piix
[    4.337226] ata3: SATA max UDMA/133 cmd 0xb000 ctl 0xac00 bmdma 0xa480 irq 22
[    4.337229] ata4: SATA max UDMA/133 cmd 0xa880 ctl 0xa800 bmdma 0xa488 irq 22
[    4.666548] ata3: SATA link down (SStatus 0 SControl 300)
[    5.140067] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    5.148204] ata4.00: ATA-8: WDC WD5000AAKS-65YGA0, 12.01C02, max UDMA/133
[    5.148206] ata4.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    5.164201] ata4.00: configured for UDMA/133
[    5.164260] scsi 4:0:0:0: Direct-Access     ATA      WDC WD5000AAKS-6 12.0 PQ: 0 ANSI: 5
[    5.164552] scsi 4:0:0:0: Attached scsi generic sg2 type 0
[    5.164607] ahci 0000:03:00.0: version 3.0
[    5.171369] pata_acpi 0000:03:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    5.171391] pata_acpi 0000:03:00.0: setting latency timer to 64
[    5.171402] pata_acpi 0000:03:00.0: PCI INT A disabled
[    5.173535] pata_marvell 0000:03:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    5.173553] pata_marvell 0000:03:00.0: setting latency timer to 64
[    5.173586] scsi5 : pata_marvell
[    5.173635] scsi6 : pata_marvell
[    5.173662] ata5: PATA max UDMA/100 cmd 0xdc00 ctl 0xd880 bmdma 0xd400 irq 16
[    5.173664] ata6: PATA max UDMA/133 cmd 0xd800 ctl 0xd480 bmdma 0xd408 irq 16
[    5.221386] Driver 'sr' needs updating - please use bus_type methods
[    5.224606] Driver 'sd' needs updating - please use bus_type methods
[    5.229269] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    5.229272] Uniform CD-ROM driver Revision: 3.20
[    5.229350] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    5.234765] sr1: scsi3-mmc drive: 48x/48x cd/rw xa/form2 cdda tray
[    5.234829] sr 1:0:0:0: Attached scsi CD-ROM sr1
[    5.234903] sd 4:0:0:0: [sda] 976773168 512-byte hardware sectors (500108 MB)
[    5.234918] sd 4:0:0:0: [sda] Write Protect is off
[    5.234920] sd 4:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.234946] sd 4:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.234984] sd 4:0:0:0: [sda] 976773168 512-byte hardware sectors (500108 MB)
[    5.234994] sd 4:0:0:0: [sda] Write Protect is off
[    5.234996] sd 4:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.235014] sd 4:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.235016]  sda: sda1 sda2 < sda5 sda6 sda7 > sda3 sda4
[    5.302383] sd 4:0:0:0: [sda] Attached SCSI disk
[    5.930308] PM: Starting manual resume from disk
[    5.930311] PM: Resume from partition 8:4
[    5.930312] PM: Checking hibernation image.
[    5.930513] PM: Resume from disk failed.
[    5.966257] kjournald starting.  Commit interval 5 seconds
[    5.966270] EXT3-fs: mounted filesystem with ordered data mode.
[    8.643617] usb-storage: device scan complete
[    8.660361] scsi 2:0:0:0: Direct-Access     WD       My Book          1028 PQ: 0 ANSI: 4
[    8.683095] sd 2:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
[    8.696343] sd 2:0:0:0: [sdb] Write Protect is off
[    8.696345] sd 2:0:0:0: [sdb] Mode Sense: 10 00 00 00
[    8.696348] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[    8.718842] sd 2:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
[    8.732093] sd 2:0:0:0: [sdb] Write Protect is off
[    8.732096] sd 2:0:0:0: [sdb] Mode Sense: 10 00 00 00
[    8.732098] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[    8.732102]  sdb: sdb1
[    9.304813] sd 2:0:0:0: [sdb] Attached SCSI disk
[    9.304904] sd 2:0:0:0: Attached scsi generic sg3 type 0
[   12.095685] ip_tables: (C) 2000-2006 Netfilter Core Team
[   12.122699] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[   12.122793] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Plase use
[   12.122795] nf_conntrack.acct=1 kernel paramater, acct=1 nf_conntrack module option or
[   12.122797] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
[   12.230041] udevd version 124 started
[   12.376143] Linux agpgart interface v0.103
[   12.515317] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   12.517773] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input4
[   12.520547] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   12.548016] ACPI: Power Button (FF) [PWRF]
[   12.548098] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input5
[   12.580016] ACPI: Power Button (CM) [PWRB]
[   13.053880] nvidia: module license 'NVIDIA' taints kernel.
[   13.313132] iTCO_vendor_support: vendor-support=0
[   13.364374] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   13.364381] nvidia 0000:01:00.0: setting latency timer to 64
[   13.365384] NVRM: loading NVIDIA UNIX x86 Kernel Module  180.11  Wed Nov 26 10:53:26 PST 2008
[   13.432684] input: PC Speaker as /devices/platform/pcspkr/input/input6
[   13.463136] Linux video capture interface: v2.00
[   13.473837] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.03 (30-Apr-2008)
[   13.563135] gspca: main v2.2.0 registered
[   13.569760] gspca: probing 0c45:612c
[   13.574174] sonixj: Sonix chip id: 12
[   13.577231] gspca: probe ok
[   13.577246] usbcore: registered new interface driver sonixj
[   13.577248] sonixj: registered
[   13.616739] iTCO_wdt: Found a ICH9 TCO device (Version=2, TCOBASE=0x0860)
[   13.616789] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   14.122572] CA0106 0000:05:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   14.122587] snd-ca0106: Model 100a Rev 00000000 Serial 100a1102
[   15.020898] lp: driver loaded but no devices found
[   15.062489] w83627ehf: Found W83627DHG chip at 0x290
[   15.062575] w83627ehf w83627ehf.656: VID pins in output mode, CPU VID not available
[   15.078256] coretemp coretemp.0: Using relative temperature scale!
[   15.078286] coretemp coretemp.1: Using relative temperature scale!
[   15.182893] Adding 979956k swap on /dev/sda4.  Priority:-1 extents:1 across:979956k
[   15.721236] EXT3 FS on sda3, internal journal
[   18.005419] type=1505 audit(1242226357.097:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4397
[   18.123804] type=1505 audit(1242226357.213:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4402
[   18.123924] type=1505 audit(1242226357.213:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4402
[   18.603288] ACPI: WMI: Mapper loaded
[   19.447064] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   19.492404] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   19.492407] apm: disabled - APM is not SMP safe.
[   19.625758] ppdev: user-space parallel port driver
[   22.873435] Bluetooth: Core ver 2.13
[   22.873590] NET: Registered protocol family 31
[   22.873593] Bluetooth: HCI device and connection manager initialized
[   22.873596] Bluetooth: HCI socket layer initialized
[   22.889062] Bluetooth: L2CAP ver 2.11
[   22.889066] Bluetooth: L2CAP socket layer initialized
[   22.896789] Bluetooth: RFCOMM socket layer initialized
[   22.897189] Bluetooth: RFCOMM TTY layer initialized
[   22.897192] Bluetooth: RFCOMM ver 1.10
[   22.909421] Bluetooth: SCO (Voice Link) ver 0.6
[   22.909425] Bluetooth: SCO socket layer initialized
[   22.930517] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   22.930522] Bluetooth: BNEP filters: protocol multicast
[   22.959443] Bridge firewalling registered
[   27.024611] atl1 0000:02:00.0: eth0 link is up 100 Mbps full duplex
[   27.332127] NET: Registered protocol family 17
[   41.739387] NET: Registered protocol family 10
[   41.740437] lo: Disabled Privacy Extensions
[   52.696006] eth0: no IPv6 routers present
[  110.400417] process `skype' is using obsolete setsockopt SO_BSDCOMPAT
```

---

### Post by rburkartjo on 2009-05-13
have you tried to install the application cheese webcam booth. go to applications /add/remove do a search for cheese and install. will install under graphics

---

### Post by Hei Ku on 2009-05-13
Moved from Argentina LoCo Team forum to Absolute Beginners.

---

### Post by sajinsj on 2009-05-13
Is your Web-cam an integrated one (eg., as the Web-cam in a laptop), or an external one.
If it is the former then it is very likely that there is a button in your Laptop keyboard which can toggle the On/Off state of the web-Cam. In my Laptop it is Fn+Esc, it may be different in yours.
 If this is your case then you may refer to the Laptop user-manual to find the Toggle button, and your Web-Cam should be working fine.

---

### Post by James Dee on 2009-05-14
> **rburkartjo said:**
> have you tried to install the application cheese webcam booth. go to applications /add/remove do a search for cheese and install. will install under graphics

yes, i try and it works. the colors are strange, to much red  color. can i somehow adjust the colors? i can't found adjusters in the cheese.
ok... camera is working in cheese, but still nothing in skype, camorama. what is the difference between fe. cheese and skype?

---

### Post by James Dee on 2009-05-14
> **sajinsj said:**
> Is your Web-cam an integrated one (eg., as the Web-cam in a laptop), or an external one.
If it is the former then it is very likely that there is a button in your Laptop keyboard which can toggle the On/Off state of the web-Cam. In my Laptop it is Fn+Esc, it may be different in yours.
 If this is your case then you may refer to the Laptop user-manual to find the Toggle button, and your Web-Cam should be working fine.
hello sajinsj,
it is external camera.
atb

[color=blue]P.S.
Everyone can countinue disscussion on the forum Absolute Beginner Talk. I opened new thread. Here is the [link](http://ubuntuforums.org/showthread.php?t=1158221).[/color]

---

### Post by overdrank on 2009-05-14
Threads merged

---

### Post by sajinsj on 2009-05-14
> **James Dee said:**
> hello sajinsj,
it is external camera.
atb


Maybe this driver replacement can help you, i'm not sure about this I just did some googling and hit upon this link-
[http://www.linux-projects.org/modules/newbb/viewtopic.php?topic_id=239&forum=3](http://www.linux-projects.org/modules/newbb/viewtopic.php?topic_id=239&forum=3)

Please visit that link and I think that this particular driver should help you.

---

### Post by Paulzy on 2009-05-15
Where does it say it's a spanish forum? My url has no language indicating spanish. :confused::confused:

> **Mauro22 said:**
> This is a spanish forum, my friend...


I translated to spanish, so someone could help you.

"Hola a todo el mundo,
Necesito ayuda para configurar mi camara correctamente. Intente millones de cosas de internet pero todavia no funciona.
Alguien tiene alguna idea?
atte
James"

lsusb y dmesg.

---

