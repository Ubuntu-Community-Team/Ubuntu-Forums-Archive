---
title: "Random freezing in 9.04"
date: 2009-08-05
forum: New to Ubuntu
---

### Post by OisinT on 2009-08-05
Help!  I've posted this in general help and got nothing really.  I turned off all visual effects, but the problem persists.

Essentially everything was fine until all of a sudden my computer started freezing randomly.  I mean locked up nothing to do but hold down the power button frozen.  I'm at my wits end as it's driving me absolutely insane.  I'm not surprised turning off visual effects didn't help as I didn't change any settings to make the problem start in the first place.

I can put up any logs necessary and I guess I should start with my /var/log/dmesg


```
[    0.000000] BIOS EBDA/lowmem at: 00098800/00098800
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.28-14-generic (buildd@yellow) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #47-Ubuntu SMP Sat Jul 25 01:19:55 UTC 2009 (Ubuntu 2.6.28-14.47-generic)
[    0.000000] Command line: root=UUID=2cdd4917-fb62-4291-9ce9-89ae4d4afe24 ro quiet splash 
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 0000000000098800 (usable)
[    0.000000]  BIOS-e820: 0000000000098800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007fedf800 (usable)
[    0.000000]  BIOS-e820: 000000007fedf800 - 000000007fee0000 (reserved)
[    0.000000]  BIOS-e820: 000000007fee0000 - 000000007fee3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007fee3000 - 000000007fef0000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007fef0000 - 000000007ff00000 (reserved)
[    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f4000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] DMI present.
[    0.000000] Phoenix BIOS detected: BIOS may corrupt low RAM, working it around.
[    0.000000] last_pfn = 0x7fedf max_arch_pfn = 0x3ffffffff
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 0000000000098800 (usable)
[    0.000000]  modified: 0000000000098800 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000007fedf800 (usable)
[    0.000000]  modified: 000000007fedf800 - 000000007fee0000 (reserved)
[    0.000000]  modified: 000000007fee0000 - 000000007fee3000 (ACPI NVS)
[    0.000000]  modified: 000000007fee3000 - 000000007fef0000 (ACPI data)
[    0.000000]  modified: 000000007fef0000 - 000000007ff00000 (reserved)
[    0.000000]  modified: 00000000f0000000 - 00000000f4000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] init_memory_mapping: 0000000000000000-000000007fedf000
[    0.000000]  0000000000 - 007fe00000 page 2M
[    0.000000]  007fe00000 - 007fedf000 page 4k
[    0.000000] kernel direct mapping tables up to 7fedf000 @ 10000-14000
[    0.000000] last_map_addr: 7fedf000 end: 7fedf000
[    0.000000] RAMDISK: 37858000 - 37fef4a2
[    0.000000] ACPI: RSDP 000F82E0, 0014 (r0 HP-CPC)
[    0.000000] ACPI: RSDT 7FEE3040, 0038 (r1 HP-CPC AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: FACP 7FEE30C0, 0074 (r1 HP-CPC AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: DSDT 7FEE3180, 505D (r1 HP-CPC AWRDACPI     1000 MSFT  100000E)
[    0.000000] ACPI: FACS 7FEE0000, 0040
[    0.000000] ACPI: MCFG 7FEE8340, 003C (r1 HP-CPC AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: APIC 7FEE8240, 0084 (r1 HP-CPC AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: SSDT 7FEE83C0, 015C (r1 HP-CPC  Cpu0Ist     3000 INTL 20040311)
[    0.000000] ACPI: SSDT 7FEE8850, 0275 (r1 HP-CPC    CpuPm     3000 INTL 20040311)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] (6 early reservations) ==> bootmem [0000000000 - 007fedf000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
[    0.000000]   #2 [0000200000 - 0000b7bbb0]    TEXT DATA BSS ==> [0000200000 - 0000b7bbb0]
[    0.000000]   #3 [0037858000 - 0037fef4a2]          RAMDISK ==> [0037858000 - 0037fef4a2]
[    0.000000]   #4 [0000098800 - 0000100000]    BIOS reserved ==> [0000098800 - 0000100000]
[    0.000000]   #5 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]
[    0.000000] found SMP MP-table at [ffff8800000f5f80] 000f5f80
[    0.000000]  [ffffe20000000000-ffffe20001bfffff] PMD -> [ffff880001200000-ffff880002dfffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00100000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x00000098
[    0.000000]     0: 0x00000100 -> 0x0007fedf
[    0.000000] On node 0 totalpages: 523879
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 2537 pages reserved
[    0.000000]   DMA zone: 1383 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 7109 pages used for memmap
[    0.000000]   DMA32 zone: 512794 pages, LIFO batch:31
[    0.000000]   Normal zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 0, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] PM: Registered nosave memory: 0000000000098000 - 0000000000099000
[    0.000000] PM: Registered nosave memory: 0000000000099000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 7ff00000:70100000)
[    0.000000] PERCPU: Allocating 69632 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 4, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 514177
[    0.000000] Kernel command line: root=UUID=2cdd4917-fb62-4291-9ce9-89ae4d4afe24 ro quiet splash 
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 3201.027 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.004000] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.004000] allocated 20971520 bytes of page_cgroup
[    0.004000] please try cgroup_disable=memory option if you don't want
[    0.004000] Scanning for low memory corruption every 60 seconds
[    0.004000] Checking aperture...
[    0.004000] No AGP bridge found
[    0.004000] Calgary: detecting Calgary via BIOS EBDA area
[    0.004000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.004000] Memory: 2024728k/2095996k available (4748k kernel code, 480k absent, 70124k reserved, 2524k data, 532k init)
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.004010] Calibrating delay loop (skipped), value calculated using timer frequency.. 6402.05 BogoMIPS (lpj=12804108)
[    0.004034] Security Framework initialized
[    0.004041] SELinux:  Disabled at boot.
[    0.004060] AppArmor: AppArmor initialized
[    0.004072] Mount-cache hash table entries: 256
[    0.004239] Initializing cgroup subsys ns
[    0.004243] Initializing cgroup subsys cpuacct
[    0.004246] Initializing cgroup subsys memory
[    0.004251] Initializing cgroup subsys freezer
[    0.004271] CPU: Trace cache: 12K uops, L1 D cache: 16K
[    0.004274] CPU: L2 cache: 2048K
[    0.004278] CPU: Physical Processor ID: 0
[    0.004279] CPU: Processor Core ID: 0
[    0.004282] using mwait in idle threads.
[    0.006888] ACPI: Core revision 20080926
[    0.009587] ACPI: Checking initramfs for custom DSDT
[    0.304064] Setting APIC routing to flat
[    0.304470] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.346891] CPU0: Intel(R) Pentium(R) D CPU 3.20GHz stepping 04
[    0.348001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 6402.39 BogoMIPS (lpj=12804798)
[    0.004000] CPU: Trace cache: 12K uops, L1 D cache: 16K
[    0.004000] CPU: L2 cache: 2048K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.432484] CPU1: Intel(R) Pentium(R) D CPU 3.20GHz stepping 04
[    0.432515] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.436033] Brought up 2 CPUs
[    0.436037] Total of 2 processors activated (12804.45 BogoMIPS).
[    0.436088] CPU0 attaching sched-domain:
[    0.436091]  domain 0: span 0-1 level CPU
[    0.436093]   groups: 0 1
[    0.436100] CPU1 attaching sched-domain:
[    0.436101]  domain 0: span 0-1 level CPU
[    0.436104]   groups: 1 0
[    0.436229] net_namespace: 1400 bytes
[    0.436234] Booting paravirtualized kernel on bare hardware
[    0.436384] Time: 11:00:55  Date: 08/04/09
[    0.436384] regulator: core version 0.5
[    0.436384] NET: Registered protocol family 16
[    0.436384] ACPI: bus type pci registered
[    0.436384] PCI: Found Intel Corporation 945G/GZ/P/PL Express Memory Controller Hub without MMCONFIG support.
[    0.436384] PCI: Using configuration type 1 for base access
[    0.437099] ACPI: EC: Look up EC in DSDT
[    0.448585] ACPI: Interpreter enabled
[    0.448592] ACPI: (supports S0 S1 S3 S4 S5)
[    0.448602] ACPI: Using IOAPIC for interrupt routing
[    0.454613] ACPI: No dock devices found.
[    0.454628] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.454732] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.454736] pci 0000:00:01.0: PME# disabled
[    0.454801] pci 0000:00:1b.0: reg 10 64bit mmio: [0xfdff8000-0xfdffbfff]
[    0.454832] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.454836] pci 0000:00:1b.0: PME# disabled
[    0.454880] pci 0000:00:1d.0: reg 20 io port: [0xff00-0xff1f]
[    0.454930] pci 0000:00:1d.1: reg 20 io port: [0xfe00-0xfe1f]
[    0.454978] pci 0000:00:1d.2: reg 20 io port: [0xfd00-0xfd1f]
[    0.455027] pci 0000:00:1d.3: reg 20 io port: [0xfc00-0xfc1f]
[    0.455073] pci 0000:00:1d.7: reg 10 32bit mmio: [0xfdfff000-0xfdfff3ff]
[    0.455113] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.455117] pci 0000:00:1d.7: PME# disabled
[    0.455255] pci 0000:00:1f.1: reg 10 io port: [0x00-0x07]
[    0.455262] pci 0000:00:1f.1: reg 14 io port: [0x00-0x03]
[    0.455269] pci 0000:00:1f.1: reg 18 io port: [0x00-0x07]
[    0.455275] pci 0000:00:1f.1: reg 1c io port: [0x00-0x03]
[    0.455282] pci 0000:00:1f.1: reg 20 io port: [0xfb00-0xfb0f]
[    0.455328] pci 0000:00:1f.2: reg 10 io port: [0xfa00-0xfa07]
[    0.455334] pci 0000:00:1f.2: reg 14 io port: [0xf900-0xf903]
[    0.455340] pci 0000:00:1f.2: reg 18 io port: [0xf800-0xf807]
[    0.455346] pci 0000:00:1f.2: reg 1c io port: [0xf700-0xf703]
[    0.455352] pci 0000:00:1f.2: reg 20 io port: [0xf600-0xf60f]
[    0.455358] pci 0000:00:1f.2: reg 24 32bit mmio: [0xfdffe000-0xfdffe3ff]
[    0.455373] pci 0000:00:1f.2: PME# supported from D3hot
[    0.455377] pci 0000:00:1f.2: PME# disabled
[    0.455428] pci 0000:00:1f.3: reg 20 io port: [0x500-0x51f]
[    0.455479] pci 0000:01:00.0: reg 10 32bit mmio: [0xfa000000-0xfaffffff]
[    0.455489] pci 0000:01:00.0: reg 14 64bit mmio: [0xe0000000-0xefffffff]
[    0.455498] pci 0000:01:00.0: reg 1c 64bit mmio: [0xfb000000-0xfbffffff]
[    0.455504] pci 0000:01:00.0: reg 24 io port: [0xdf00-0xdf7f]
[    0.455510] pci 0000:01:00.0: reg 30 32bit mmio: [0xfcfe0000-0xfcffffff]
[    0.455558] pci 0000:00:01.0: bridge io port: [0xd000-0xdfff]
[    0.455561] pci 0000:00:01.0: bridge 32bit mmio: [0xfa000000-0xfcffffff]
[    0.455566] pci 0000:00:01.0: bridge 64bit mmio pref: [0xe0000000-0xefffffff]
[    0.455604] pci 0000:02:01.0: reg 10 32bit mmio: [0xfdeff000-0xfdeff7ff]
[    0.455612] pci 0000:02:01.0: reg 14 io port: [0xef00-0xef7f]
[    0.455649] pci 0000:02:01.0: supports D2
[    0.455651] pci 0000:02:01.0: PME# supported from D2 D3hot D3cold
[    0.455655] pci 0000:02:01.0: PME# disabled
[    0.455693] pci 0000:02:03.0: reg 10 32bit mmio: [0xfdee0000-0xfdeeffff]
[    0.455767] pci 0000:02:04.0: reg 10 32bit mmio: [0xfdefe000-0xfdefe7ff]
[    0.455808] pci 0000:02:04.0: supports D1 D2
[    0.455846] pci 0000:02:08.0: reg 10 32bit mmio: [0xfdefd000-0xfdefdfff]
[    0.455853] pci 0000:02:08.0: reg 14 io port: [0xee00-0xee3f]
[    0.455887] pci 0000:02:08.0: supports D1 D2
[    0.455889] pci 0000:02:08.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.455894] pci 0000:02:08.0: PME# disabled
[    0.455930] pci 0000:00:1e.0: transparent bridge
[    0.455934] pci 0000:00:1e.0: bridge io port: [0xe000-0xefff]
[    0.455938] pci 0000:00:1e.0: bridge 32bit mmio: [0xfde00000-0xfdefffff]
[    0.455953] bus 00 -> node 0
[    0.455963] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.456309] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[    0.470994] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 *5 7 9 10 11 12 14 15)
[    0.471170] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[    0.471346] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[    0.471522] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[    0.471697] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 *10 11 12 14 15)
[    0.471872] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[    0.472067] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[    0.472244] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[    0.472507] ACPI: WMI: Mapper loaded
[    0.472570] SCSI subsystem initialized
[    0.472570] libata version 3.00 loaded.
[    0.472570] usbcore: registered new interface driver usbfs
[    0.472570] usbcore: registered new interface driver hub
[    0.472570] usbcore: registered new device driver usb
[    0.472570] PCI: Using ACPI for IRQ routing
[    0.484027] Bluetooth: Core ver 2.13
[    0.484047] NET: Registered protocol family 31
[    0.484047] Bluetooth: HCI device and connection manager initialized
[    0.484047] Bluetooth: HCI socket layer initialized
[    0.484047] NET: Registered protocol family 8
[    0.484047] NET: Registered protocol family 20
[    0.484047] NetLabel: Initializing
[    0.484047] NetLabel:  domain hash size = 128
[    0.484047] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.484059] NetLabel:  unlabeled traffic allowed by default
[    0.484161] AppArmor: AppArmor Filesystem Enabled
[    0.496014] pnp: PnP ACPI init
[    0.496029] ACPI: bus type pnp registered
[    0.499295] pnp: PnP ACPI: found 11 devices
[    0.499298] ACPI: ACPI bus type pnp unregistered
[    0.499309] system 00:01: ioport range 0x4d0-0x4d1 has been reserved
[    0.499312] system 00:01: ioport range 0x800-0x87f has been reserved
[    0.499314] system 00:01: ioport range 0x880-0x88f has been reserved
[    0.499322] system 00:07: ioport range 0x400-0x4bf has been reserved
[    0.499329] system 00:09: iomem range 0xf0000000-0xf3ffffff has been reserved
[    0.499336] system 00:0a: iomem range 0xd4800-0xd7fff has been reserved
[    0.499339] system 00:0a: iomem range 0xf0000-0xf7fff could not be reserved
[    0.499342] system 00:0a: iomem range 0xf8000-0xfbfff could not be reserved
[    0.499344] system 00:0a: iomem range 0xfc000-0xfffff could not be reserved
[    0.499347] system 00:0a: iomem range 0x7fee0000-0x7fefffff could not be reserved
[    0.499350] system 00:0a: iomem range 0x0-0x9ffff could not be reserved
[    0.499352] system 00:0a: iomem range 0x100000-0x7fedffff could not be reserved
[    0.499355] system 00:0a: iomem range 0xfec00000-0xfec00fff has been reserved
[    0.499358] system 00:0a: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.499361] system 00:0a: iomem range 0xffb00000-0xffb7ffff has been reserved
[    0.499363] system 00:0a: iomem range 0xfff00000-0xffffffff has been reserved
[    0.499366] system 00:0a: iomem range 0xe0000-0xeffff has been reserved
[    0.504083] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.504087] pci 0000:00:01.0:   IO window: 0xd000-0xdfff
[    0.504091] pci 0000:00:01.0:   MEM window: 0xfa000000-0xfcffffff
[    0.504095] pci 0000:00:01.0:   PREFETCH window: 0x000000e0000000-0x000000efffffff
[    0.504100] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:02
[    0.504103] pci 0000:00:1e.0:   IO window: 0xe000-0xefff
[    0.504108] pci 0000:00:1e.0:   MEM window: 0xfde00000-0xfdefffff
[    0.504112] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.504126] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.504131] pci 0000:00:01.0: setting latency timer to 64
[    0.504138] pci 0000:00:1e.0: setting latency timer to 64
[    0.504142] bus: 00 index 0 io port: [0x00-0xffff]
[    0.504145] bus: 00 index 1 mmio: [0x000000-0xffffffffffffffff]
[    0.504148] bus: 01 index 0 io port: [0xd000-0xdfff]
[    0.504150] bus: 01 index 1 mmio: [0xfa000000-0xfcffffff]
[    0.504152] bus: 01 index 2 mmio: [0xe0000000-0xefffffff]
[    0.504154] bus: 01 index 3 mmio: [0x0-0x0]
[    0.504156] bus: 02 index 0 io port: [0xe000-0xefff]
[    0.504158] bus: 02 index 1 mmio: [0xfde00000-0xfdefffff]
[    0.504160] bus: 02 index 2 mmio: [0x0-0x0]
[    0.504161] bus: 02 index 3 io port: [0x00-0xffff]
[    0.504163] bus: 02 index 4 mmio: [0x000000-0xffffffffffffffff]
[    0.504174] NET: Registered protocol family 2
[    0.540085] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
[    0.540441] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
[    0.542315] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.542875] TCP: Hash tables configured (established 262144 bind 65536)
[    0.542878] TCP reno registered
[    0.552161] NET: Registered protocol family 1
[    0.552310] checking if image is initramfs... it is
[    1.004455] Switched to high resolution mode on CPU 1
[    1.008038] Switched to high resolution mode on CPU 0
[    1.149872] Freeing initrd memory: 7773k freed
[    1.153942] audit: initializing netlink socket (disabled)
[    1.153962] type=2000 audit(1249383655.152:1): initialized
[    1.160937] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.162338] VFS: Disk quotas dquot_6.5.1
[    1.162419] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.163136] fuse init (API version 7.10)
[    1.163257] msgmni has been set to 3971
[    1.163505] alg: No test for stdrng (krng)
[    1.163523] io scheduler noop registered
[    1.163526] io scheduler anticipatory registered
[    1.163529] io scheduler deadline registered
[    1.163593] io scheduler cfq registered (default)
[    1.163710] pci 0000:01:00.0: Boot video device
[    1.163747] pci 0000:02:08.0: Firmware left e100 interrupts enabled; disabling
[    1.167064] pcieport-driver 0000:00:01.0: setting latency timer to 64
[    1.167100] pcieport-driver 0000:00:01.0: found MSI capability
[    1.167124] pcieport-driver 0000:00:01.0: irq 2303 for MSI/MSI-X
[    1.167134] pci_express 0000:00:01.0:pcie00: allocate port service
[    1.167200] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.167212] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.167355] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.167359] ACPI: Power Button (FF) [PWRF]
[    1.167406] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    1.167409] ACPI: Power Button (CM) [PWRB]
[    1.167461] fan PNP0C0B:00: registered as cooling_device0
[    1.167468] ACPI: Fan [FAN] (on)
[    1.167773] processor ACPI_CPU:00: registered as cooling_device1
[    1.168034] ACPI: SSDT 7FEE87C0, 0087 (r1 HP-CPC  Cpu1Ist     3000 INTL 20040311)
[    1.168313] processor ACPI_CPU:01: registered as cooling_device2
[    1.177139] thermal LNXTHERM:01: registered as thermal_zone0
[    1.188743] ACPI: Thermal Zone [THRM] (40 C)
[    1.212666] Linux agpgart interface v0.103
[    1.212677] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.213723] brd: module loaded
[    1.214066] loop: module loaded
[    1.214144] Fixed MDIO Bus: probed
[    1.214150] PPP generic driver version 2.4.2
[    1.214211] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    1.214242] Driver 'sd' needs updating - please use bus_type methods
[    1.214253] Driver 'sr' needs updating - please use bus_type methods
[    1.214295] ahci 0000:00:1f.2: version 3.0
[    1.214310] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.214357] ahci 0000:00:1f.2: irq 2302 for MSI/MSI-X
[    1.214423] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl RAID mode
[    1.214426] ahci 0000:00:1f.2: flags: 64bit ncq led clo 
[    1.214430] ahci 0000:00:1f.2: setting latency timer to 64
[    1.214730] scsi0 : ahci
[    1.214861] scsi1 : ahci
[    1.214958] scsi2 : ahci
[    1.215046] scsi3 : ahci
[    1.215194] ata1: SATA max UDMA/133 abar m1024@0xfdffe000 port 0xfdffe100 irq 2302
[    1.215198] ata2: SATA max UDMA/133 abar m1024@0xfdffe000 port 0xfdffe180 irq 2302
[    1.215200] ata3: SATA max UDMA/133 abar m1024@0xfdffe000 port 0xfdffe200 irq 2302
[    1.215203] ata4: SATA max UDMA/133 abar m1024@0xfdffe000 port 0xfdffe280 irq 2302
[    1.532020] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.532820] ata1.00: ATA-7: ST3200827AS, 3.AHH, max UDMA/100
[    1.532824] ata1.00: 390721968 sectors, multi 0: LBA48 NCQ (depth 31/32)
[    1.533769] ata1.00: configured for UDMA/100
[    2.256019] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.256817] ata2.00: ATA-7: ST3200827AS, 3.AHH, max UDMA/100
[    2.256821] ata2.00: 390721968 sectors, multi 0: LBA48 NCQ (depth 31/32)
[    2.257780] ata2.00: configured for UDMA/100
[    2.576017] ata3: SATA link down (SStatus 0 SControl 300)
[    2.896016] ata4: SATA link down (SStatus 0 SControl 300)
[    2.896164] scsi 0:0:0:0: Direct-Access     ATA      ST3200827AS      3.AH PQ: 0 ANSI: 5
[    2.896273] sd 0:0:0:0: [sda] 390721968 512-byte hardware sectors: (200 GB/186 GiB)
[    2.896293] sd 0:0:0:0: [sda] Write Protect is off
[    2.896296] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.896329] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.896404] sd 0:0:0:0: [sda] 390721968 512-byte hardware sectors: (200 GB/186 GiB)
[    2.896422] sd 0:0:0:0: [sda] Write Protect is off
[    2.896425] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.896456] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.896460]  sda: sda1 sda2 < sda5 >
[    2.935809] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.935878] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.935978] scsi 1:0:0:0: Direct-Access     ATA      ST3200827AS      3.AH PQ: 0 ANSI: 5
[    2.936096] sd 1:0:0:0: [sdb] 390721968 512-byte hardware sectors: (200 GB/186 GiB)
[    2.936117] sd 1:0:0:0: [sdb] Write Protect is off
[    2.936120] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    2.936152] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.936216] sd 1:0:0:0: [sdb] 390721968 512-byte hardware sectors: (200 GB/186 GiB)
[    2.936235] sd 1:0:0:0: [sdb] Write Protect is off
[    2.936237] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    2.936269] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.936273]  sdb: sdb1
[    2.954104] sd 1:0:0:0: [sdb] Attached SCSI disk
[    2.954145] sd 1:0:0:0: Attached scsi generic sg1 type 0
[    2.954208] ata_piix 0000:00:1f.1: version 2.12
[    2.954228] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    2.954268] ata_piix 0000:00:1f.1: setting latency timer to 64
[    2.954369] scsi4 : ata_piix
[    2.954444] scsi5 : ata_piix
[    2.955065] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xfb00 irq 14
[    2.955068] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xfb08 irq 15
[    3.124448] ata5.00: ATAPI: HL-DT-STDVDRRW GSA-H20L, S742, max UDMA/33
[    3.124473] ata5.01: ATAPI: IDE-DVD DROM6216, HD08, max UDMA/100
[    3.124489] ata5.01: limited to UDMA/33 due to 40-wire cable
[    3.140388] ata5.00: configured for UDMA/33
[    3.156295] ata5.01: configured for UDMA/33
[    3.157900] ata6: port disabled. ignoring.
[    3.157936] isa bounce pool size: 16 pages
[    3.159492] scsi 4:0:0:0: CD-ROM            HL-DT-ST DVDRRW GSA-H20L  S742 PQ: 0 ANSI: 5
[    3.164551] sr0: scsi3-mmc drive: 40x/40x writer dvd-ram cd/rw xa/form2 cdda tray
[    3.164556] Uniform CD-ROM driver Revision: 3.20
[    3.164688] sr 4:0:0:0: Attached scsi CD-ROM sr0
[    3.164735] sr 4:0:0:0: Attached scsi generic sg2 type 5
[    3.165366] scsi 4:0:1:0: CD-ROM            IDE-DVD  DROM6216         HD08 PQ: 0 ANSI: 5
[    3.166318] sr1: scsi3-mmc drive: 5x/16x cd/rw xa/form2 cdda tray
[    3.166400] sr 4:0:1:0: Attached scsi CD-ROM sr1
[    3.166439] sr 4:0:1:0: Attached scsi generic sg3 type 5
[    3.167094] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    3.167117] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    3.167137] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    3.167141] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    3.167207] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    3.171109] ehci_hcd 0000:00:1d.7: cache line size of 128 is not supported
[    3.171126] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfdfff000
[    3.184018] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    3.184114] usb usb1: configuration #1 chosen from 1 choice
[    3.184148] hub 1-0:1.0: USB hub found
[    3.184158] hub 1-0:1.0: 8 ports detected
[    3.184281] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    3.184300] uhci_hcd: USB Universal Host Controller Interface driver
[    3.184327] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    3.184334] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    3.184337] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    3.184381] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    3.184405] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000ff00
[    3.184490] usb usb2: configuration #1 chosen from 1 choice
[    3.184518] hub 2-0:1.0: USB hub found
[    3.184525] hub 2-0:1.0: 2 ports detected
[    3.184611] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    3.184618] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    3.184621] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    3.184665] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    3.184697] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000fe00
[    3.184776] usb usb3: configuration #1 chosen from 1 choice
[    3.184802] hub 3-0:1.0: USB hub found
[    3.184810] hub 3-0:1.0: 2 ports detected
[    3.184895] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    3.184901] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    3.184904] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    3.184950] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    3.184979] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000fd00
[    3.185057] usb usb4: configuration #1 chosen from 1 choice
[    3.185084] hub 4-0:1.0: USB hub found
[    3.185091] hub 4-0:1.0: 2 ports detected
[    3.185178] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    3.185184] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    3.185187] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    3.185241] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    3.185271] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000fc00
[    3.185349] usb usb5: configuration #1 chosen from 1 choice
[    3.185379] hub 5-0:1.0: USB hub found
[    3.185386] hub 5-0:1.0: 2 ports detected
[    3.185535] PNP: No PS/2 controller found. Probing ports directly.
[    3.188218] serio: i8042 KBD port at 0x60,0x64 irq 1
[    3.188226] serio: i8042 AUX port at 0x60,0x64 irq 12
[    3.200054] mice: PS/2 mouse device common for all mice
[    3.236089] rtc_cmos 00:03: RTC can wake from S4
[    3.236127] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    3.236154] rtc0: alarms up to one month, 242 bytes nvram
[    3.236222] device-mapper: uevent: version 1.0.3
[    3.236350] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
[    3.236483] device-mapper: multipath: version 1.0.5 loaded
[    3.236486] device-mapper: multipath round-robin: version 1.0.0 loaded
[    3.236634] cpuidle: using governor ladder
[    3.236637] cpuidle: using governor menu
[    3.237095] TCP cubic registered
[    3.237181] NET: Registered protocol family 10
[    3.237620] lo: Disabled Privacy Extensions
[    3.237933] NET: Registered protocol family 17
[    3.237954] Bluetooth: L2CAP ver 2.11
[    3.237956] Bluetooth: L2CAP socket layer initialized
[    3.237959] Bluetooth: SCO (Voice Link) ver 0.6
[    3.237961] Bluetooth: SCO socket layer initialized
[    3.238006] Bluetooth: RFCOMM socket layer initialized
[    3.238017] Bluetooth: RFCOMM TTY layer initialized
[    3.238019] Bluetooth: RFCOMM ver 1.10
[    3.240144] registered taskstats version 1
[    3.240264]   Magic number: 5:438:23
[    3.240354] rtc_cmos 00:03: setting system clock to 2009-08-04 11:00:57 UTC (1249383657)
[    3.240358] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    3.240360] EDD information not available.
[    3.240406] Freeing unused kernel memory: 532k freed
[    3.240662] Write protecting the kernel read-only data: 6688k
[    3.504877] e100: Intel(R) PRO/100 Network Driver, 3.5.23-k6-NAPI
[    3.504881] e100: Copyright(c) 1999-2006 Intel Corporation
[    3.504942] e100 0000:02:08.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    3.525069] e100 0000:02:08.0: PME# disabled
[    3.525706] e100: eth0: e100_probe: addr 0xfdefd000, irq 20, MAC addr 00:17:31:f0:2b:af
[    3.525750] ohci1394 0000:02:01.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    3.586540] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[20]  MMIO=[fdeff000-fdeff7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    3.848030] usb 2-1: new low speed USB device using uhci_hcd and address 2
[    3.977595] PM: Starting manual resume from disk
[    3.977600] PM: Resume from partition 8:5
[    3.977602] PM: Checking hibernation image.
[    3.977774] PM: Resume from disk failed.
[    4.005630] EXT3-fs: INFO: recovery required on readonly filesystem.
[    4.005634] EXT3-fs: write access will be enabled during recovery.
[    4.023559] usb 2-1: configuration #1 chosen from 1 choice
[    4.031626] usbcore: registered new interface driver hiddev
[    4.049738] input: Logitech USB RECEIVER as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0/input/input3
[    4.076211] generic-usb 0003:046D:C50E.0001: input,hidraw0: USB HID v1.11 Mouse [Logitech USB RECEIVER] on usb-0000:00:1d.0-1/input0
[    4.076233] usbcore: registered new interface driver usbhid
[    4.076237] usbhid: v2.6:USB HID core driver
[    4.264038] usb 3-1: new low speed USB device using uhci_hcd and address 2
[    4.591830] usb 3-1: configuration #1 chosen from 1 choice
[    4.668284] input: Logitech HID compliant keyboard as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.0/input/input4
[    4.692124] generic-usb 0003:046D:C30E.0002: input,hidraw1: USB HID v1.10 Keyboard [Logitech HID compliant keyboard] on usb-0000:00:1d.1-1/input0
[    4.808853] input: Logitech HID compliant keyboard as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.1/input/input5
[    4.836132] generic-usb 0003:046D:C30E.0003: input,hidraw2: USB HID v1.10 Device [Logitech HID compliant keyboard] on usb-0000:00:1d.1-1/input1
[    4.872320] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0011d80000c0eaeb]
[    5.076050] usb 5-1: new full speed USB device using uhci_hcd and address 2
[    5.249412] usb 5-1: configuration #1 chosen from 1 choice
[    5.256822] Initializing USB Mass Storage driver...
[    5.256982] scsi6 : SCSI emulation for USB Mass Storage devices
[    5.257080] usbcore: registered new interface driver usb-storage
[    5.257084] USB Mass Storage support registered.
[    5.257429] usb-storage: device found at 2
[    5.257431] usb-storage: waiting for device to settle before scanning
[    7.870884] kjournald starting.  Commit interval 5 seconds
[    7.870909] EXT3-fs: sda1: orphan cleanup on readonly fs
[    7.870915] ext3_orphan_cleanup: deleting unreferenced inode 15089764
[    7.912017] ext3_orphan_cleanup: deleting unreferenced inode 2899985
[    7.922574] ext3_orphan_cleanup: deleting unreferenced inode 14106634
[    7.922586] ext3_orphan_cleanup: deleting unreferenced inode 14106633
[    7.922594] ext3_orphan_cleanup: deleting unreferenced inode 14106629
[    7.922601] ext3_orphan_cleanup: deleting unreferenced inode 14106628
[    7.922609] ext3_orphan_cleanup: deleting unreferenced inode 14106627
[    7.922615] EXT3-fs: sda1: 7 orphan inodes deleted
[    7.922617] EXT3-fs: recovery complete.
[    8.020353] EXT3-fs: mounted filesystem with ordered data mode.
[   10.258341] usb-storage: device scan complete
[   10.261314] scsi 6:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
[   10.264312] scsi 6:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
[   10.267307] scsi 6:0:0:2: Direct-Access     Generic  USB SM Reader    1.02 PQ: 0 ANSI: 0
[   10.270308] scsi 6:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0
[   10.275400] sd 6:0:0:0: [sdc] Attached SCSI removable disk
[   10.275469] sd 6:0:0:0: Attached scsi generic sg4 type 0
[   10.280375] sd 6:0:0:1: [sdd] Attached SCSI removable disk
[   10.280421] sd 6:0:0:1: Attached scsi generic sg5 type 0
[   10.285374] sd 6:0:0:2: [sde] Attached SCSI removable disk
[   10.285422] sd 6:0:0:2: Attached scsi generic sg6 type 0
[   10.290379] sd 6:0:0:3: [sdf] Attached SCSI removable disk
[   10.290422] sd 6:0:0:3: Attached scsi generic sg7 type 0
[   17.490563] udev: starting version 141
[   18.028066] cfg80211: Calling CRDA to update world regulatory domain
[   18.183358] parport_pc 00:06: reported by Plug and Play ACPI
[   18.183419] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   18.310480] cfg80211: World regulatory domain updated:
[   18.310484] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   18.310488] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   18.310490] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   18.310493] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   18.310495] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   18.310497] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   18.345120] input: PC Speaker as /devices/platform/pcspkr/input/input6
[   18.764666] nvidia: module license 'NVIDIA' taints kernel.
[   18.798973] iTCO_vendor_support: vendor-support=0
[   18.800370] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05
[   18.800670] iTCO_wdt: Found a ICH7DH TCO device (Version=2, TCOBASE=0x0460)
[   18.800756] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   18.886710] Linux video capture interface: v2.00
[   18.910851] ppdev: user-space parallel port driver
[   19.018183] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   19.018191] nvidia 0000:01:00.0: setting latency timer to 64
[   19.018463] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  185.18.14  Wed May 27 01:23:47 PDT 2009
[   19.044561] ath5k_pci 0000:02:03.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   19.044621] ath5k_pci 0000:02:03.0: registered as 'phy0'
[   19.064982] saa7130/34: v4l2 driver version 0.2.14 loaded
[   19.130908] phy0: Selected rate control algorithm 'pid'
[   19.186205] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   19.186267] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   19.211034] ath5k phy0: Atheros AR5414 chip found (MAC: 0xa2, PHY: 0x61)
[   19.211088] saa7134 0000:02:04.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   19.211099] saa7133[0]: found at 0000:02:04.0, rev: 209, irq: 16, latency: 32, mmio: 0xfdefe000
[   19.211109] saa7133[0]: subsystem: 1043:4871, board: ASUS P7131 4871 [card=111,autodetected]
[   19.211155] saa7133[0]: board init: gpio is 0
[   19.360514] saa7133[0]: i2c eeprom 00: 43 10 71 48 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
[   19.360531] saa7133[0]: i2c eeprom 10: ff ff ff 0f ff 20 ff ff ff ff ff ff ff ff ff ff
[   19.360546] saa7133[0]: i2c eeprom 20: 01 40 01 02 03 00 01 03 08 ff 00 cf ff ff ff ff
[   19.360560] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   19.360574] saa7133[0]: i2c eeprom 40: ff 21 00 c2 96 10 03 22 15 50 ff ff ff ff ff ff
[   19.360589] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   19.360603] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   19.360617] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   19.360631] saa7133[0]: i2c eeprom 80: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   19.360648] saa7133[0]: i2c eeprom 90: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   19.360659] saa7133[0]: i2c eeprom a0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   19.360669] saa7133[0]: i2c eeprom b0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   19.360680] saa7133[0]: i2c eeprom c0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   19.360691] saa7133[0]: i2c eeprom d0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   19.360701] saa7133[0]: i2c eeprom e0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   19.360712] saa7133[0]: i2c eeprom f0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   19.468100] tuner' 0-004b: chip found @ 0x96 (saa7133[0])
[   19.548017] tda829x 0-004b: setting tuner address to 61
[   19.620514] tda829x 0-004b: type set to tda8290+75a
[   23.477930] saa7133[0]: registered device video0 [v4l2]
[   23.478033] saa7133[0]: registered device vbi0
[   23.619546] dvb_init() allocating 1 frontend
[   23.636112] DVB: registering new adapter (saa7133[0])
[   23.636117] DVB: registering adapter 0 frontend 0 (Philips TDA10046H DVB-T)...
[   23.707102] lp0: using parport0 (interrupt-driven).
[   23.708023] tda1004x: setting up plls for 48MHz sampling clock
[   23.874878] Adding 6032368k swap on /dev/sda5.  Priority:-1 extents:1 across:6032368k
[   24.421326] EXT3 FS on sda1, internal journal
[   25.948517] tda1004x: timeout waiting for DSP ready
[   25.988016] tda1004x: found firmware revision 0 -- invalid
[   25.988020] tda1004x: trying to boot from eeprom
[   26.109231] type=1505 audit(1249383680.367:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2267
[   26.217413] type=1505 audit(1249383680.475:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2271
[   26.217538] type=1505 audit(1249383680.475:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2271
[   26.217581] type=1505 audit(1249383680.475:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2271
[   26.217620] type=1505 audit(1249383680.475:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2271
[   26.253467] type=1505 audit(1249383680.511:7): operation="profile_load" name="/usr/bin/freshclam" name2="default" pid=2276
[   26.374870] type=1505 audit(1249383680.631:8): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2280
[   26.375029] type=1505 audit(1249383680.631:9): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2280
[   26.418456] type=1505 audit(1249383680.676:10): operation="profile_load" name="/usr/sbin/mysqld" name2="default" pid=2286
[   26.445762] type=1505 audit(1249383680.704:11): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2290
[   28.316018] tda1004x: timeout waiting for DSP ready
[   28.356512] tda1004x: found firmware revision 0 -- invalid
[   28.356516] tda1004x: waiting for firmware upload...
[   28.356521] saa7134 0000:02:04.0: firmware: requesting dvb-fe-tda10046.fw
[   41.416053] tda1004x: found firmware revision 20 -- ok
[   42.955182] tun: Universal TUN/TAP device driver, 1.6
[   42.955186] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[   45.997648] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   45.997651] Bluetooth: BNEP filters: protocol multicast
[   46.038639] Bridge firewalling registered
```


Please any help you can offer is greatly greatly appreciated.

---

### Post by swoll1980 on 2009-08-05
I would try disabling compiz first see if that helps.

---

### Post by ELD on 2009-08-05
This from what i can see is affect a lot people, myself included :(, it is really frustrating, only release to do it, so i am patiently waiting for Karmic.

---

### Post by mapes12 on 2009-08-05
I had freezing issues with 9.04 with one of my machines. I installed 8.04LTS. It works fine now and all the updates are supported.

---

### Post by OisinT on 2009-08-05
> **swoll1980 said:**
> I would try disabling compiz first see if that helps.

tried that and it was exactly the same.

---

### Post by ronparent on 2009-08-05
I've had this problem on two machines, one both with 8.10 and 9.04. I successfully fixed it by using the noapic and nolapic options to install, or, by adding those to menu.lst as startup options for the kernel. You can test if it will work for you by booting on the 9.04 live cd. On the first boot screen (after language selection) hit F6 and use the spacebar to select the noapic and nolapic options. Then complete the boot by selecting boot without any changes to your system. If you can operate the system without any freezing for an hour or so, those boot option will probably work for you.

---

### Post by OisinT on 2009-08-05
> **ronparent said:**
> I've had this problem on two machines, one both with 8.10 and 9.04. I successfully fixed it by using the noapic and nolapic options to install, or, by adding those to menu.lst as startup options for the kernel. You can test if it will work for you by booting on the 9.04 live cd. On the first boot screen (after language selection) hit F6 and use the spacebar to select the noapic and nolapic options. Then complete the boot by selecting boot without any changes to your system. If you can operate the system without any freezing for an hour or so, those boot option will probably work for you.
I'll try that... thanks

---

### Post by OisinT on 2009-08-08
> **ronparent said:**
> I've had this problem on two machines, one both with 8.10 and 9.04. I successfully fixed it by using the noapic and nolapic options to install, or, by adding those to menu.lst as startup options for the kernel. You can test if it will work for you by booting on the 9.04 live cd. On the first boot screen (after language selection) hit F6 and use the spacebar to select the noapic and nolapic options. Then complete the boot by selecting boot without any changes to your system. If you can operate the system without any freezing for an hour or so, those boot option will probably work for you.
update: so far so good. you are a legend!

---

### Post by ELD on 2009-08-09
> **ronparent said:**
> I've had this problem on two machines, one both with 8.10 and 9.04. I successfully fixed it by using the noapic and nolapic options to install, or, by adding those to menu.lst as startup options for the kernel. You can test if it will work for you by booting on the 9.04 live cd. On the first boot screen (after language selection) hit F6 and use the spacebar to select the noapic and nolapic options. Then complete the boot by selecting boot without any changes to your system. If you can operate the system without any freezing for an hour or so, those boot option will probably work for you.

What do those boot options enable/disable?

---

### Post by ronparent on 2009-08-09
OisinT - Glad to hear it is working for you. Good luck and have fun.

ELD - I'm afraid I can't answer your question. In my case, when this particular computer boots, the bios assigns a hardware service called apic to  interupt nine. However, I've discovered for myself (with advice from this forum) that this computer will freeze if I try to run ubuntu without disabling the ubuntu apic and lapic implementation. In my newer hardware I don't have that problem. 

This in some way relates to the infamous kernel freeze. I have tried to follow that topic in all the forums to discover a definitive answer why it occurs to no avail. I have only discovered that this particular fix on this particular computer works for me!

---

### Post by RJARRRPCGP on 2009-08-09
> **OisinT said:**
> 

Essentially everything was fine until all of a sudden my computer started freezing randomly.  I mean locked up nothing to do but hold down the power button frozen.  

Sounds like the HDD may be disconnecting and reconnecting, because of a loose power connector or ATA cable connection. 

ATA does not support the HDD being disconnected while running.

And I'm pretty sure the OS don't tolerate the HDD connection being changed while running.

If it gets bumped loose, then prepare for a hard lock.

-> This problem may be caused by a bad PSU! 
-> In fact, if the HDD is making a repeated clicking sound, there's a good chance of a PSU connector problem!

---

### Post by bottlebags on 2009-08-10
the above reply is non-sense. I'm suffering from regular lock ups and all connections are stable and the power supply is healthy, also if booted in to xp there is no problem. As for a clicking noise from the hard drive means mechanical damage or ware primarily the actuator arm  :confused:

---

### Post by kaligus on 2009-09-23
My main machine has just started freezing like this as of 9/18/2009.

I can easily SYSRQ-RSEIUB but that is all I Can do.  This does not seem to cause grief in any way.  I am also going back over the various logs to see what has changed in the last week.

1) It seems to only lock up if I am sitting at the machine.  If i leave it doing some task or another it seem fine.

2) I have one at a time disabled everything that has ever given people grief according to these forums:
2.1) pulse audio (usually disabled anyway)
2.2) screenlets with my only screenlet being one I wrote to display 2 specific time clocks and which has been working fine since Feisty.
2.3) compiz (again functional since day one as far as I have known)
2.4) my mouse wheel, button assignment, etc stuff
2.5) ALL audio
2.6) NVIDIA 185 (not updated in quite some time as far as I can tell)
2.7) IM (pidgin, empathy)
2.8) since the freeze often happens with a web browser active, I have stopped using web browsers on the affected box.
2.9) anything else I could imagine causing grief...

Then I fresh installed 9.04 on the same drives only using a SRD to wipe /etc /boot /var /usr etc.

Then fresh install of 9.04 letting it remove the system files.

I can boot any operating system I have available and do anything I Want as long as I want EXCEPT 9.04

I am going back through all of the dpkg etc. logs but since it is now locking up even on a fresh install without any software loaded I am putting my money on some update to the core in the last week or so.

I will report back when I know more.

---

