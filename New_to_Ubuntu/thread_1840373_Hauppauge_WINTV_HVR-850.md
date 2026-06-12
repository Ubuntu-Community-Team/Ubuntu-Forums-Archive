---
title: "Hauppauge WINTV HVR-850"
date: 2011-09-07
forum: New to Ubuntu
---

### Post by josue0098 on 2011-09-07
Hello, i thought this would be a good place to post this because I am a total newb. Please forgive me if I posted in wrong section. My laptop with windows was recently stolen, and I used that laptop for my tv tuner,now I only have my old desktop with Lubuntu on it, as Win7 runs as fast as a tortoise on it. I do not know much about commands but have tried some suggestions out there,to no avail. I will give any hardware or software info necesary, but please help me. and thank you in advance.

---

### Post by josue0098 on 2011-09-07
anyone? please i dont have money to buy a newer laptop just so I can watch tv :/

---

### Post by josue0098 on 2011-09-07
I will post dmesg and lspci -v: 

DMESG
> [    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.38-11-generic (buildd@rothera) (gcc version 4.5.2 (Ubuntu/Linaro 4.5.2-8ubuntu4) ) #48-Ubuntu SMP Fri Jul 29 19:05:14 UTC 2011 (Ubuntu 2.6.38-11.48-generic 2.6.38.8)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e8000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007ffe4000 (usable)
[    0.000000]  BIOS-e820: 000000007ffe4000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] Notice: NX (Execute Disable) protection missing in CPU!
[    0.000000] NX (Execute Disable) protection: approximated by x86 segment limits
[    0.000000] DMI 2.3 present.
[    0.000000] DMI: Hewlett-Packard HP Compaq dc5100 MT(AG152AW)/09E0h, BIOS 786C2 v01.07 08/25/2005
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x7ffe4 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-E7FFF write-protect
[    0.000000]   E8000-EFFFF write-back
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 disabled
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] found SMP MP-table at [c00fe700] fe700
[    0.000000] initial memory mapped : 0 - 01c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 1bfb000-1c00000
[    0.000000] RAMDISK: 35c98000 - 36e44000
[    0.000000] ACPI: RSDP 000e9c10 00014 (v00 COMPAQ)
[    0.000000] ACPI: RSDT 7fff4040 00038 (v01 COMPAQ CPQ0968  20050825      00000000)
[    0.000000] ACPI: FACP 7fff40ec 00074 (v01 COMPAQ GRANTSD  00000001      00000000)
[    0.000000] ACPI: DSDT 7fff4267 013F3 (v01 COMPAQ     DSDT 00000001 MSFT 0100000E)
[    0.000000] ACPI: FACS 7fff4000 00040
[    0.000000] ACPI: SSDT 7fff565a 03303 (v01 COMPAQ  PROJECT 00000001 MSFT 0100000E)
[    0.000000] ACPI: APIC 7fff4160 00068 (v01 COMPAQ GRANTSD  00000001      00000000)
[    0.000000] ACPI: ASF! 7fff41c8 00063 (v32 COMPAQ GRANTSD  00000001      00000000)
[    0.000000] ACPI: MCFG 7fff422b 0003C (v01 COMPAQ GRANTSD  00000001      00000000)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 1159MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0007ffe4
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0007ffe4
[    0.000000] On node 0 totalpages: 524147
[    0.000000] free_area_init_node: node 0, pgdat c1784180, node_mem_map f4c98200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2320 pages used for memmap
[    0.000000]   HighMem zone: 294614 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0xf808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e8000
[    0.000000] PM: Registered nosave memory: 00000000000e8000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 80000000:60000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 13 pages/cpu @f7000000 s28800 r0 d24448 u2097152
[    0.000000] pcpu-alloc: s28800 r0 d24448 u2097152 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 1 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 520051
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-11-generic root=UUID=e61ba64c-5eea-4112-b3f7-a6c398e60187 ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] allocated 10484880 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0007ffe4)
[    0.000000] Memory: 2041552k/2097040k available (5190k kernel code, 55036k reserved, 2538k data, 700k init, 1187736k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc178d000 - 0xc183c000   ( 700 kB)
[    0.000000]       .data : 0xc1511ba1 - 0xc178c500   (2538 kB)
[    0.000000]       .text : 0xc1000000 - 0xc1511ba1   (5190 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=15, HWalign=128, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] 	RCU-based detection of stalled CPUs is disabled.
[    0.000000] NR_IRQS:2304 nr_irqs:512 16
[    0.000000] CPU 0 irqstacks, hard=f3c08000 soft=f3c0a000
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 3191.554 MHz processor.
[    0.004003] Calibrating delay loop (skipped), value calculated using timer frequency.. 6383.10 BogoMIPS (lpj=12766216)
[    0.004009] pid_max: default: 32768 minimum: 301
[    0.004039] Security Framework initialized
[    0.004064] AppArmor: AppArmor initialized
[    0.004066] Yama: becoming mindful.
[    0.004143] Mount-cache hash table entries: 512
[    0.004320] Initializing cgroup subsys ns
[    0.004325] ns_cgroup deprecated: consider using the 'clone_children' flag without the ns_cgroup.
[    0.004329] Initializing cgroup subsys cpuacct
[    0.004335] Initializing cgroup subsys memory
[    0.004347] Initializing cgroup subsys devices
[    0.004350] Initializing cgroup subsys freezer
[    0.004352] Initializing cgroup subsys net_cls
[    0.004355] Initializing cgroup subsys blkio
[    0.004408] CPU: Physical Processor ID: 0
[    0.004411] CPU: Processor Core ID: 0
[    0.004414] mce: CPU supports 4 MCE banks
[    0.004428] CPU0: Thermal monitoring enabled (TM1)
[    0.004433] using mwait in idle threads.
[    0.011231] ACPI: Core revision 20110112
[    0.015184] ftrace: allocating 23649 entries in 47 pages
[    0.016069] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.016389] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.059463] CPU0: Intel(R) Pentium(R) 4 CPU 3.20GHz stepping 03
[    0.060003] Performance Events: Netburst events, Netburst P4/Xeon PMU driver.
[    0.060003] ... version:                0
[    0.060003] ... bit width:              40
[    0.060003] ... generic registers:      18
[    0.060003] ... value mask:             000000ffffffffff
[    0.060003] ... max period:             0000007fffffffff
[    0.060003] ... fixed-purpose events:   0
[    0.060003] ... event mask:             000000000003ffff
[    0.060003] CPU 1 irqstacks, hard=f3ca6000 soft=f3cb0000
[    0.060003] Booting Node   0, Processors  #1 Ok.
[    0.008000] Initializing CPU#1
[    0.148031] Brought up 2 CPUs
[    0.148037] Total of 2 processors activated (12767.63 BogoMIPS).
[    0.149013] devtmpfs: initialized
[    0.149013] HP Compaq Laptop series board detected. Selecting BIOS-method for reboots.
[    0.149749] print_constraints: dummy: 
[    0.149779] Time: 16:52:13  Date: 09/07/11
[    0.149826] NET: Registered protocol family 16
[    0.149841] Trying to unpack rootfs image as initramfs...
[    0.150045] EISA bus registered
[    0.150060] ACPI: bus type pci registered
[    0.150191] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.150198] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    0.150202] PCI: Using MMCONFIG for extended config space
[    0.150206] PCI: Using configuration type 1 for base access
[    0.153889] bio: create slab <bio-0> at 0
[    0.155910] ACPI: EC: Look up EC in DSDT
[    0.180471] ACPI: SSDT 7fffa11e 00453 (v01 COMPAQ  CPU_TM2 00000001 MSFT 0100000E)
[    0.181012] ACPI: Dynamic OEM Table Load:
[    0.181020] ACPI: SSDT   (null) 00453 (v01 COMPAQ  CPU_TM2 00000001 MSFT 0100000E)
[    0.212468] ACPI: Interpreter enabled
[    0.212482] ACPI: (supports S0 S1 S3 S4 S5)
[    0.212527] ACPI: Using IOAPIC for interrupt routing
[    0.260239] ACPI: No dock devices found.
[    0.260246] HEST: Table not found.
[    0.260256] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
[    0.292481] ACPI Error: [CAPD] Namespace lookup failure, AE_ALREADY_EXISTS (20110112/dsfield-143)
[    0.292497] ACPI Error: Method parse/execution failed [\_SB_.PCI0._OSC] (Node f3c271e0), AE_ALREADY_EXISTS (20110112/psparse-536)
[    0.292514] ACPI: Marking method _OSC as Serialized because of AE_ALREADY_EXISTS error
[    0.292527] ACPI Warning: For \_SB_.PCI0._OSC: Parameter count mismatch - ASL declared 5, ACPI requires 4 (20110112/nspredef-352)
[    0.292540] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.293268] pci_root PNP0A08:00: host bridge window [mem 0xf0000000-0xfebfffff] (ignored)
[    0.293276] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7] (ignored)
[    0.293281] pci_root PNP0A08:00: host bridge window [io  0x1000-0x2fff] (ignored)
[    0.293286] pci_root PNP0A08:00: host bridge window [io  0x3000-0x6fff] (ignored)
[    0.293292] pci_root PNP0A08:00: host bridge window [io  0x7000-0xafff] (ignored)
[    0.293297] pci_root PNP0A08:00: host bridge window [io  0xb000-0xffff] (ignored)
[    0.293302] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)
[    0.293308] pci_root PNP0A08:00: host bridge window [mem 0x80000000-0xdfffffff] (ignored)
[    0.293328] pci 0000:00:00.0: [8086:2580] type 0 class 0x000600
[    0.293430] pci 0000:00:1c.0: [8086:2660] type 1 class 0x000604
[    0.293507] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.293515] pci 0000:00:1c.0: PME# disabled
[    0.293551] pci 0000:00:1c.1: [8086:2662] type 1 class 0x000604
[    0.293630] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.293638] pci 0000:00:1c.1: PME# disabled
[    0.293675] pci 0000:00:1d.0: [8086:2658] type 0 class 0x000c03
[    0.293730] pci 0000:00:1d.0: reg 20: [io  0x3440-0x345f]
[    0.293772] pci 0000:00:1d.1: [8086:2659] type 0 class 0x000c03
[    0.293831] pci 0000:00:1d.1: reg 20: [io  0x3460-0x347f]
[    0.293875] pci 0000:00:1d.2: [8086:265a] type 0 class 0x000c03
[    0.293928] pci 0000:00:1d.2: reg 20: [io  0x3480-0x349f]
[    0.293971] pci 0000:00:1d.3: [8086:265b] type 0 class 0x000c03
[    0.294025] pci 0000:00:1d.3: reg 20: [io  0x34a0-0x34bf]
[    0.294078] pci 0000:00:1d.7: [8086:265c] type 0 class 0x000c03
[    0.294105] pci 0000:00:1d.7: reg 10: [mem 0xf0200000-0xf02003ff]
[    0.294195] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.294202] pci 0000:00:1d.7: PME# disabled
[    0.294229] pci 0000:00:1e.0: [8086:244e] type 1 class 0x000604
[    0.294307] pci 0000:00:1e.2: [8086:266e] type 0 class 0x000401
[    0.294329] pci 0000:00:1e.2: reg 10: [io  0x3000-0x30ff]
[    0.294344] pci 0000:00:1e.2: reg 14: [io  0x3400-0x343f]
[    0.294360] pci 0000:00:1e.2: reg 18: [mem 0xf0200400-0xf02005ff]
[    0.294375] pci 0000:00:1e.2: reg 1c: [mem 0xf0200600-0xf02006ff]
[    0.294424] pci 0000:00:1e.2: PME# supported from D0 D3hot D3cold
[    0.294431] pci 0000:00:1e.2: PME# disabled
[    0.294459] pci 0000:00:1f.0: [8086:2640] type 0 class 0x000601
[    0.294564] pci 0000:00:1f.0: Force enabled HPET at 0xfed00000
[    0.294576] pci 0000:00:1f.0: quirk: [io  0xf800-0xf87f] claimed by ICH6 ACPI/GPIO/TCO
[    0.294586] pci 0000:00:1f.0: quirk: [io  0xfa00-0xfa3f] claimed by ICH6 GPIO
[    0.294593] pci 0000:00:1f.0: LPC Generic IO decode 1 PIO at 0400-047f
[    0.294599] pci 0000:00:1f.0: LPC Generic IO decode 2 PIO at 0480-048f
[    0.294622] pci 0000:00:1f.1: [8086:266f] type 0 class 0x000101
[    0.294642] pci 0000:00:1f.1: reg 10: [io  0x3800-0x3807]
[    0.294656] pci 0000:00:1f.1: reg 14: [io  0x3820-0x3823]
[    0.294670] pci 0000:00:1f.1: reg 18: [io  0x3808-0x380f]
[    0.294683] pci 0000:00:1f.1: reg 1c: [io  0x3824-0x3827]
[    0.294697] pci 0000:00:1f.1: reg 20: [io  0x34e0-0x34ef]
[    0.294750] pci 0000:00:1f.2: [8086:2651] type 0 class 0x000101
[    0.294771] pci 0000:00:1f.2: reg 10: [io  0x3810-0x3817]
[    0.294784] pci 0000:00:1f.2: reg 14: [io  0x3828-0x382b]
[    0.294797] pci 0000:00:1f.2: reg 18: [io  0x3818-0x381f]
[    0.294810] pci 0000:00:1f.2: reg 1c: [io  0x382c-0x382f]
[    0.294823] pci 0000:00:1f.2: reg 20: [io  0x34f0-0x34ff]
[    0.294863] pci 0000:00:1f.2: PME# supported from D3hot
[    0.294870] pci 0000:00:1f.2: PME# disabled
[    0.294944] pci 0000:00:1c.0: PCI bridge to [bus 20-20]
[    0.294953] pci 0000:00:1c.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.294960] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.294971] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.295053] pci 0000:40:00.0: [14e4:1677] type 0 class 0x000200
[    0.295086] pci 0000:40:00.0: reg 10: [mem 0xf0300000-0xf030ffff 64bit]
[    0.295201] pci 0000:40:00.0: PME# supported from D3hot D3cold
[    0.295210] pci 0000:40:00.0: PME# disabled
[    0.295232] pci 0000:40:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    0.295249] pci 0000:00:1c.1: PCI bridge to [bus 40-40]
[    0.295256] pci 0000:00:1c.1:   bridge window [io  0xf000-0x0000] (disabled)
[    0.295264] pci 0000:00:1c.1:   bridge window [mem 0xf0300000-0xf05fffff]
[    0.295274] pci 0000:00:1c.1:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.295329] pci 0000:05:04.0: [1002:5960] type 0 class 0x000300
[    0.295354] pci 0000:05:04.0: reg 10: [mem 0xd0000000-0xd7ffffff pref]
[    0.295370] pci 0000:05:04.0: reg 14: [io  0x1000-0x10ff]
[    0.295386] pci 0000:05:04.0: reg 18: [mem 0xf0800000-0xf080ffff]
[    0.295432] pci 0000:05:04.0: reg 30: [mem 0x00000000-0x0001ffff pref]
[    0.295464] pci 0000:05:04.0: supports D1 D2
[    0.295490] pci 0000:05:04.1: [1002:5940] type 0 class 0x000380
[    0.295514] pci 0000:05:04.1: reg 10: [mem 0xd8000000-0xdfffffff pref]
[    0.295530] pci 0000:05:04.1: reg 14: [mem 0xf0810000-0xf081ffff]
[    0.295608] pci 0000:05:04.1: supports D1 D2
[    0.295673] pci 0000:00:1e.0: PCI bridge to [bus 05-05] (subtractive decode)
[    0.295680] pci 0000:00:1e.0:   bridge window [io  0x1000-0x1fff]
[    0.295688] pci 0000:00:1e.0:   bridge window [mem 0xf0600000-0xf08fffff]
[    0.295698] pci 0000:00:1e.0:   bridge window [mem 0xcfe00000-0xdfffffff 64bit pref]
[    0.295704] pci 0000:00:1e.0:   bridge window [io  0x0000-0xffff] (subtractive decode)
[    0.295710] pci 0000:00:1e.0:   bridge window [mem 0x00000000-0xffffffff] (subtractive decode)
[    0.295732] pci_bus 0000:00: on NUMA node 0
[    0.295739] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.296087] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCX1._PRT]
[    0.296212] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCX2._PRT]
[    0.296343] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB_._PRT]
[    0.296955] ACPI Error: [CAPD] Namespace lookup failure, AE_ALREADY_EXISTS (20110112/dsfield-143)
[    0.296968] ACPI Error: Method parse/execution failed [\_SB_.PCI0._OSC] (Node f3c271e0), AE_ALREADY_EXISTS (20110112/psparse-536)
[    0.296989] ACPI Warning: For \_SB_.PCI0._OSC: Parameter count mismatch - ASL declared 5, ACPI requires 4 (20110112/nspredef-352)
[    0.297003]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.297143] ACPI Error: [CAPD] Namespace lookup failure, AE_ALREADY_EXISTS (20110112/dsfield-143)
[    0.297156] ACPI Error: Method parse/execution failed [\_SB_.PCI0._OSC] (Node f3c271e0), AE_ALREADY_EXISTS (20110112/psparse-536)
[    0.297176] ACPI Warning: For \_SB_.PCI0._OSC: Parameter count mismatch - ASL declared 5, ACPI requires 4 (20110112/nspredef-352)
[    0.308084] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 14 15)
[    0.308210] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 7 10 11 14 15)
[    0.308326] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 10 11 14 15)
[    0.308441] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 10 11 14 15)
[    0.308557] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 *11 14 15)
[    0.308672] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 *10 11 14 15)
[    0.308794] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 *11 14 15)
[    0.308909] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 11 14 15) *0, disabled.
[    0.309123] vgaarb: device added: PCI:0000:05:04.0,decodes=io+mem,owns=io+mem,locks=none
[    0.309131] vgaarb: loaded
[    0.309568] SCSI subsystem initialized
[    0.309668] libata version 3.00 loaded.
[    0.309764] usbcore: registered new interface driver usbfs
[    0.309791] usbcore: registered new interface driver hub
[    0.309848] usbcore: registered new device driver usb
[    0.310237] wmi: Mapper loaded
[    0.310242] PCI: Using ACPI for IRQ routing
[    0.310247] PCI: pci_cache_line_size set to 64 bytes
[    0.310349] reserve RAM buffer: 000000000009fc00 - 000000000009ffff 
[    0.310355] reserve RAM buffer: 000000007ffe4000 - 000000007fffffff 
[    0.310549] NetLabel: Initializing
[    0.310553] NetLabel:  domain hash size = 128
[    0.310556] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.310576] NetLabel:  unlabeled traffic allowed by default
[    0.310722] hpet clockevent registered
[    0.310728] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.310735] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.310746] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.316381] Switching to clocksource hpet
[    0.319220] Switched to NOHz mode on CPU #0
[    0.319330] Switched to NOHz mode on CPU #1
[    0.331816] AppArmor: AppArmor Filesystem Enabled
[    0.331870] pnp: PnP ACPI init
[    0.331908] ACPI: bus type pnp registered
[    0.332334] pnp 00:00: [mem 0xf0000000-0xfebfffff window]
[    0.332347] pnp 00:00: [bus 00-ff]
[    0.332352] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.332358] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.332363] pnp 00:00: [io  0x1000-0x2fff window]
[    0.332368] pnp 00:00: [io  0x3000-0x6fff window]
[    0.332373] pnp 00:00: [io  0x7000-0xafff window]
[    0.332378] pnp 00:00: [io  0xb000-0xffff window]
[    0.332384] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.332390] pnp 00:00: [mem 0x80000000-0xdfffffff window]
[    0.332504] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    0.332565] pnp 00:01: [io  0x00f0-0x00ff]
[    0.332582] pnp 00:01: [irq 13]
[    0.332644] pnp 00:01: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.332674] pnp 00:02: [io  0x0000-0x000f]
[    0.332679] pnp 00:02: [io  0x0080-0x008f]
[    0.332683] pnp 00:02: [io  0x00c0-0x00df]
[    0.332688] pnp 00:02: [dma 4]
[    0.332748] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.332769] pnp 00:03: [io  0x0070-0x0071]
[    0.332779] pnp 00:03: [irq 8]
[    0.332847] pnp 00:03: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.332869] pnp 00:04: [io  0x0061]
[    0.332940] pnp 00:04: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.332969] pnp 00:05: [irq 12]
[    0.333037] pnp 00:05: Plug and Play ACPI device, IDs PNP0f13 PNP0f0e (active)
[    0.333059] pnp 00:06: [io  0x0060]
[    0.333064] pnp 00:06: [io  0x0064]
[    0.333072] pnp 00:06: [irq 1]
[    0.333135] pnp 00:06: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.333666] pnp 00:07: [irq 7]
[    0.333672] pnp 00:07: [dma 3]
[    0.333676] pnp 00:07: [io  0x0378-0x037f]
[    0.333681] pnp 00:07: [io  0x0778-0x077d]
[    0.333828] pnp 00:07: Plug and Play ACPI device, IDs PNP0401 (active)
[    0.334237] pnp 00:08: [irq 4]
[    0.334243] pnp 00:08: [io  0x03f8-0x03ff]
[    0.334391] pnp 00:08: Plug and Play ACPI device, IDs PNP0501 PNP0500 (active)
[    0.334761] pnp 00:09: [irq 6]
[    0.334767] pnp 00:09: [dma 2]
[    0.334775] pnp 00:09: [io  0x03f0-0x03f5]
[    0.334779] pnp 00:09: [io  0x03f7]
[    0.334869] pnp 00:09: Plug and Play ACPI device, IDs PNP0700 (active)
[    0.334972] pnp 00:0a: [mem 0xfec00000-0xfec00fff]
[    0.335057] pnp 00:0a: Plug and Play ACPI device, IDs PNP0003 (active)
[    0.335111] pnp 00:0b: [io  0x0010-0x001f]
[    0.335116] pnp 00:0b: [io  0x0050-0x0053]
[    0.335121] pnp 00:0b: [io  0x0072-0x0077]
[    0.335125] pnp 00:0b: [io  0x0090-0x009f]
[    0.335241] system 00:0b: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.335268] pnp 00:0c: [io  0x0400-0x041f]
[    0.335273] pnp 00:0c: [io  0x0420-0x043f]
[    0.335277] pnp 00:0c: [io  0x0440-0x045f]
[    0.335282] pnp 00:0c: [io  0x0460-0x047f]
[    0.335286] pnp 00:0c: [io  0x0480-0x048f]
[    0.335290] pnp 00:0c: [io  0xf800-0xf81f]
[    0.335294] pnp 00:0c: [io  0xf820-0xf83f]
[    0.335299] pnp 00:0c: [io  0xf840-0xf85f]
[    0.335303] pnp 00:0c: [io  0xf860-0xf87f]
[    0.335307] pnp 00:0c: [io  0xfa00-0xfa3f]
[    0.335311] pnp 00:0c: [io  0xfc00-0xfc7f]
[    0.335315] pnp 00:0c: [io  0xfc80-0xfcff]
[    0.335320] pnp 00:0c: [io  0xfe00-0xfe7f]
[    0.335324] pnp 00:0c: [io  0xfe80-0xfeff]
[    0.335354] pnp 00:0c: disabling [io  0xf800-0xf81f] because it overlaps 0000:00:1f.0 BAR 13 [io  0xf800-0xf87f]
[    0.335362] pnp 00:0c: disabling [io  0xf820-0xf83f] because it overlaps 0000:00:1f.0 BAR 13 [io  0xf800-0xf87f]
[    0.335369] pnp 00:0c: disabling [io  0xf840-0xf85f] because it overlaps 0000:00:1f.0 BAR 13 [io  0xf800-0xf87f]
[    0.335376] pnp 00:0c: disabling [io  0xf860-0xf87f] because it overlaps 0000:00:1f.0 BAR 13 [io  0xf800-0xf87f]
[    0.335472] system 00:0c: [io  0x0400-0x041f] has been reserved
[    0.335479] system 00:0c: [io  0x0420-0x043f] has been reserved
[    0.335485] system 00:0c: [io  0x0440-0x045f] has been reserved
[    0.335490] system 00:0c: [io  0x0460-0x047f] has been reserved
[    0.335496] system 00:0c: [io  0x0480-0x048f] has been reserved
[    0.335502] system 00:0c: [io  0xfa00-0xfa3f] has been reserved
[    0.335507] system 00:0c: [io  0xfc00-0xfc7f] has been reserved
[    0.335513] system 00:0c: [io  0xfc80-0xfcff] has been reserved
[    0.335519] system 00:0c: [io  0xfe00-0xfe7f] has been reserved
[    0.335524] system 00:0c: [io  0xfe80-0xfeff] has been reserved
[    0.335531] system 00:0c: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.335574] pnp 00:0d: [io  0x04d0-0x04d1]
[    0.335686] system 00:0d: [io  0x04d0-0x04d1] has been reserved
[    0.335695] system 00:0d: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.356054] pnp 00:0e: [mem 0x00000000-0x0009ffff]
[    0.356062] pnp 00:0e: [mem 0x00100000-0x7fffffff]
[    0.356067] pnp 00:0e: [mem 0x000e8000-0x000fffff]
[    0.356072] pnp 00:0e: [mem 0xfec01000-0xffffffff]
[    0.356077] pnp 00:0e: [mem 0xe0000000-0xefffffff]
[    0.356082] pnp 00:0e: [mem 0x000d0000-0x000e7fff]
[    0.356243] system 00:0e: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.356250] system 00:0e: [mem 0x00100000-0x7fffffff] could not be reserved
[    0.356256] system 00:0e: [mem 0x000e8000-0x000fffff] could not be reserved
[    0.356262] system 00:0e: [mem 0xfec01000-0xffffffff] has been reserved
[    0.356268] system 00:0e: [mem 0xe0000000-0xefffffff] has been reserved
[    0.356274] system 00:0e: [mem 0x000d0000-0x000e7fff] has been reserved
[    0.356282] system 00:0e: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.356307] pnp: PnP ACPI: found 15 devices
[    0.356311] ACPI: ACPI bus type pnp unregistered
[    0.356318] PnPBIOS: Disabled by ACPI PNP
[    0.395033] pci 0000:00:1c.0: BAR 14: assigned [mem 0x80000000-0x801fffff]
[    0.395043] pci 0000:00:1c.0: BAR 15: assigned [mem 0x80200000-0x803fffff 64bit pref]
[    0.395052] pci 0000:00:1c.1: BAR 15: assigned [mem 0x80400000-0x805fffff 64bit pref]
[    0.395060] pci 0000:00:1c.0: BAR 13: assigned [io  0x2000-0x2fff]
[    0.395067] pci 0000:00:1c.1: BAR 13: assigned [io  0x4000-0x4fff]
[    0.395073] pci 0000:00:1c.0: PCI bridge to [bus 20-20]
[    0.395079] pci 0000:00:1c.0:   bridge window [io  0x2000-0x2fff]
[    0.395088] pci 0000:00:1c.0:   bridge window [mem 0x80000000-0x801fffff]
[    0.395096] pci 0000:00:1c.0:   bridge window [mem 0x80200000-0x803fffff 64bit pref]
[    0.395107] pci 0000:00:1c.1: PCI bridge to [bus 40-40]
[    0.395113] pci 0000:00:1c.1:   bridge window [io  0x4000-0x4fff]
[    0.395121] pci 0000:00:1c.1:   bridge window [mem 0xf0300000-0xf05fffff]
[    0.395129] pci 0000:00:1c.1:   bridge window [mem 0x80400000-0x805fffff 64bit pref]
[    0.395141] pci 0000:05:04.0: BAR 6: assigned [mem 0xcfe00000-0xcfe1ffff pref]
[    0.395147] pci 0000:00:1e.0: PCI bridge to [bus 05-05]
[    0.395153] pci 0000:00:1e.0:   bridge window [io  0x1000-0x1fff]
[    0.395162] pci 0000:00:1e.0:   bridge window [mem 0xf0600000-0xf08fffff]
[    0.395170] pci 0000:00:1e.0:   bridge window [mem 0xcfe00000-0xdfffffff 64bit pref]
[    0.395190] pci 0000:00:1c.0: setting latency timer to 64
[    0.395218] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.395225] pci 0000:00:1c.1: setting latency timer to 64
[    0.395237] pci 0000:00:1e.0: setting latency timer to 64
[    0.395244] pci_bus 0000:00: resource 0 [io  0x0000-0xffff]
[    0.395250] pci_bus 0000:00: resource 1 [mem 0x00000000-0xffffffff]
[    0.395255] pci_bus 0000:20: resource 0 [io  0x2000-0x2fff]
[    0.395260] pci_bus 0000:20: resource 1 [mem 0x80000000-0x801fffff]
[    0.395266] pci_bus 0000:20: resource 2 [mem 0x80200000-0x803fffff 64bit pref]
[    0.395271] pci_bus 0000:40: resource 0 [io  0x4000-0x4fff]
[    0.395276] pci_bus 0000:40: resource 1 [mem 0xf0300000-0xf05fffff]
[    0.395281] pci_bus 0000:40: resource 2 [mem 0x80400000-0x805fffff 64bit pref]
[    0.395287] pci_bus 0000:05: resource 0 [io  0x1000-0x1fff]
[    0.395292] pci_bus 0000:05: resource 1 [mem 0xf0600000-0xf08fffff]
[    0.395297] pci_bus 0000:05: resource 2 [mem 0xcfe00000-0xdfffffff 64bit pref]
[    0.395302] pci_bus 0000:05: resource 4 [io  0x0000-0xffff]
[    0.395307] pci_bus 0000:05: resource 5 [mem 0x00000000-0xffffffff]
[    0.395376] NET: Registered protocol family 2
[    0.395504] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.395956] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.396569] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.396870] TCP: Hash tables configured (established 131072 bind 65536)
[    0.396875] TCP reno registered
[    0.396881] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.396894] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.397046] NET: Registered protocol family 1
[    0.397209] pci 0000:05:04.0: Boot video device
[    0.397221] PCI: CLS 64 bytes, default 64
[    0.397563] cpufreq-nforce2: No nForce2 chipset.
[    0.397815] audit: initializing netlink socket (disabled)
[    0.397830] type=2000 audit(1315414333.392:1): initialized
[    0.411384] highmem bounce pool size: 64 pages
[    0.411395] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.415326] VFS: Disk quotas dquot_6.5.2
[    0.415455] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.416951] fuse init (API version 7.16)
[    0.417160] msgmni has been set to 1667
[    0.417623] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.417675] io scheduler noop registered
[    0.417680] io scheduler deadline registered
[    0.417714] io scheduler cfq registered (default)
[    0.417916] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.417977] pcieport 0000:00:1c.0: irq 40 for MSI/MSI-X
[    0.418080] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.418137] pcieport 0000:00:1c.1: irq 41 for MSI/MSI-X
[    0.418288] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.418338] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.418647] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.492040] ACPI: Power Button [PBTN]
[    0.492175] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.492185] ACPI: Power Button [PWRF]
[    0.492513] ACPI: acpi_idle registered with cpuidle
[    0.494809] ERST: Table is not found!
[    0.494892] isapnp: Scanning for PnP cards...
[    0.494942] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.515402] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.758638] Freeing initrd memory: 18096k freed
[    0.848246] isapnp: No Plug & Play device found
[    0.875256] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.875666] Linux agpgart interface v0.103
[    0.877761] brd: module loaded
[    0.878642] loop: module loaded
[    0.878775] i2c-core: driver [adp5520] using legacy suspend method
[    0.878778] i2c-core: driver [adp5520] using legacy resume method
[    0.878920] ata_piix 0000:00:1f.1: version 2.13
[    0.878939] ata_piix 0000:00:1f.1: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.878988] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.879520] scsi0 : ata_piix
[    0.879657] scsi1 : ata_piix
[    0.879843] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x34e0 irq 14
[    0.879848] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x34e8 irq 15
[    0.879893] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.879903] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    1.032042] ata_piix 0000:00:1f.2: setting latency timer to 64
[    1.032655] scsi2 : ata_piix
[    1.032779] scsi3 : ata_piix
[    1.032970] ata3: SATA max UDMA/133 cmd 0x3810 ctl 0x3828 bmdma 0x34f0 irq 19
[    1.032975] ata4: SATA max UDMA/133 cmd 0x3818 ctl 0x382c bmdma 0x34f8 irq 19
[    1.033677] Fixed MDIO Bus: probed
[    1.033756] PPP generic driver version 2.4.2
[    1.033853] tun: Universal TUN/TAP device driver, 1.6
[    1.033857] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.034018] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.034051] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    1.034072] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    1.034078] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    1.034149] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    1.043091] ehci_hcd 0000:00:1d.7: debug port 1
[    1.046988] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
[    1.047009] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xf0200000
[    1.060023] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    1.060217] hub 1-0:1.0: USB hub found
[    1.060224] hub 1-0:1.0: 8 ports detected
[    1.060341] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.060362] uhci_hcd: USB Universal Host Controller Interface driver
[    1.060395] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    1.060404] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.060408] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    1.060466] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.060520] uhci_hcd 0000:00:1d.0: irq 20, io base 0x00003440
[    1.060704] hub 2-0:1.0: USB hub found
[    1.060711] hub 2-0:1.0: 2 ports detected
[    1.060812] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[    1.060820] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    1.060824] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    1.060885] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    1.060951] uhci_hcd 0000:00:1d.1: irq 18, io base 0x00003460
[    1.061132] hub 3-0:1.0: USB hub found
[    1.061139] hub 3-0:1.0: 2 ports detected
[    1.061241] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 21 (level, low) -> IRQ 21
[    1.061249] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    1.061253] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    1.061317] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    1.064329] ata1.00: ATAPI: LITE-ON DVD SOHD-16P9S, FQSC, max UDMA/44
[    1.064684] uhci_hcd 0000:00:1d.2: irq 21, io base 0x00003480
[    1.064869] hub 4-0:1.0: USB hub found
[    1.064876] hub 4-0:1.0: 2 ports detected
[    1.064978] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 22 (level, low) -> IRQ 22
[    1.064986] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    1.064990] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    1.065048] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    1.065113] uhci_hcd 0000:00:1d.3: irq 22, io base 0x000034a0
[    1.065297] hub 5-0:1.0: USB hub found
[    1.065304] hub 5-0:1.0: 2 ports detected
[    1.065495] i8042: PNP: PS/2 Controller [PNP0303:KBD,PNP0f0e:PS2M] at 0x60,0x64 irq 1,12
[    1.068406] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.068415] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.068611] mousedev: PS/2 mouse device common for all mice
[    1.068814] rtc_cmos 00:03: RTC can wake from S4
[    1.068908] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    1.068936] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    1.069056] device-mapper: uevent: version 1.0.3
[    1.069173] device-mapper: ioctl: 4.19.1-ioctl (2011-01-07) initialised: [email]dm-devel@redhat.com[/email]
[    1.069276] device-mapper: multipath: version 1.2.0 loaded
[    1.069282] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.069388] EISA: Probing bus 0 at eisa.0
[    1.069396] Cannot allocate resource for EISA slot 1
[    1.069398] Cannot allocate resource for EISA slot 2
[    1.069401] Cannot allocate resource for EISA slot 3
[    1.069403] Cannot allocate resource for EISA slot 4
[    1.069419] EISA: Detected 0 cards.
[    1.069506] cpuidle: using governor ladder
[    1.069511] cpuidle: using governor menu
[    1.069930] TCP cubic registered
[    1.070116] NET: Registered protocol family 10
[    1.070981] NET: Registered protocol family 17
[    1.071003] Registering the dns_resolver key type
[    1.074705] Using IPI No-Shortcut mode
[    1.074848] PM: Hibernation image not present or could not be loaded.
[    1.074865] registered taskstats version 1
[    1.075110]   Magic number: 11:579:893
[    1.075196] rtc_cmos 00:03: setting system clock to 2011-09-07 16:52:14 UTC (1315414334)
[    1.075201] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.075203] EDD information not available.
[    1.088209] ata1.00: configured for UDMA/44
[    1.089113] scsi 0:0:0:0: CD-ROM            LITE-ON  DVD SOHD-16P9S   FQSC PQ: 0 ANSI: 5
[    1.090182] sr0: scsi3-mmc drive: 4x/48x cd/rw xa/form2 cdda tray
[    1.090188] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.090378] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    1.090476] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    1.199006] ata3.00: ATA-7: Maxtor 6N040T0, NAN51680, max UDMA/100
[    1.199011] ata3.00: 78165360 sectors, multi 16: LBA48 
[    1.212145] ata3.00: configured for UDMA/100
[    1.212277] scsi 2:0:0:0: Direct-Access     ATA      Maxtor 6N040T0   NAN5 PQ: 0 ANSI: 5
[    1.212472] sd 2:0:0:0: [sda] 78165360 512-byte logical blocks: (40.0 GB/37.2 GiB)
[    1.212529] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    1.212597] sd 2:0:0:0: [sda] Write Protect is off
[    1.212604] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.212669] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.257916]  sda: sda1 sda2 < sda5 >
[    1.258418] sd 2:0:0:0: [sda] Attached SCSI disk
[    1.258469] Freeing unused kernel memory: 700k freed
[    1.258853] Write protecting the kernel text: 5192k
[    1.258917] Write protecting the kernel read-only data: 2148k
[    1.292303] <30>udev[73]: starting version 167
[    1.372092] usb 1-1: new high speed USB device using ehci_hcd and address 2
[    1.396035] Refined TSC clocksource calibration: 3191.999 MHz.
[    1.396045] Switching to clocksource tsc
[    1.490101] FDC 0 is a post-1991 82077
[    1.494664] tg3.c:v3.116 (December 3, 2010)
[    1.494689] tg3 0000:40:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.494704] tg3 0000:40:00.0: setting latency timer to 64
[    1.554935] [drm] Initialized drm 1.1.0 20060810
[    1.623688] tg3 0000:40:00.0: eth0: Tigon3 [partno(BCM95751) rev 4001] (PCI Express) MAC address 00:0f:fe:2c:46:22
[    1.623697] tg3 0000:40:00.0: eth0: attached PHY is 5750 (10/100/1000Base-T Ethernet) (WireSpeed[1])
[    1.623703] tg3 0000:40:00.0: eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[    1.623709] tg3 0000:40:00.0: eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[    1.632745] [drm] radeon defaulting to kernel modesetting.
[    1.632750] [drm] radeon kernel modesetting enabled.
[    1.632819] radeon 0000:05:04.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.634316] [drm] initializing kernel modesetting (RV280 0x1002:0x5960).
[    1.634360] [drm] register mmio base: 0xF0800000
[    1.634364] [drm] register mmio size: 65536
[    1.634547] [drm] Generation 2 PCI interface, using max accessible memory
[    1.634556] radeon 0000:05:04.0: VRAM: 256M 0x00000000D0000000 - 0x00000000DFFFFFFF (256M used)
[    1.634560] radeon 0000:05:04.0: GTT: 512M 0x00000000B0000000 - 0x00000000CFFFFFFF
[    1.634571] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    1.634574] [drm] Driver supports precise vblank timestamp query.
[    1.634600] [drm] radeon: irq initialized.
[    1.635394] [drm] Detected VRAM RAM=256M, BAR=128M
[    1.635399] [drm] RAM width 128bits DDR
[    1.635502] [TTM] Zone  kernel: Available graphics memory: 436306 kiB.
[    1.635506] [TTM] Zone highmem: Available graphics memory: 1030174 kiB.
[    1.635509] [TTM] Initializing pool allocator.
[    1.635533] [drm] radeon: 256M of VRAM memory ready
[    1.635537] [drm] radeon: 512M of GTT memory ready.
[    1.635565] [drm] GART: num cpu pages 131072, num gpu pages 131072
[    1.637860] radeon 0000:05:04.0: WB enabled
[    1.637940] [drm] Loading R200 Microcode
[    1.641953] [drm] radeon: ring at 0x00000000B0001000
[    1.641981] [drm] ring test succeeded in 2 usecs
[    1.642213] [drm] radeon: ib pool ready.
[    1.642331] [drm] ib test succeeded in 0 usecs
[    1.642838] [drm] Radeon Display Connectors
[    1.642842] [drm] Connector 0:
[    1.642845] [drm]   VGA
[    1.642848] [drm]   DDC: 0x60 0x60 0x60 0x60 0x60 0x60 0x60 0x60
[    1.642850] [drm]   Encoders:
[    1.642852] [drm]     CRT1: INTERNAL_DAC1
[    1.642854] [drm] Connector 1:
[    1.642856] [drm]   DVI-I
[    1.642858] [drm]   HPD1
[    1.642860] [drm]   DDC: 0x64 0x64 0x64 0x64 0x64 0x64 0x64 0x64
[    1.642863] [drm]   Encoders:
[    1.642865] [drm]     CRT2: INTERNAL_DAC2
[    1.642867] [drm]     DFP1: INTERNAL_TMDS1
[    1.642869] [drm] Connector 2:
[    1.642870] [drm]   S-video
[    1.642872] [drm]   Encoders:
[    1.642874] [drm]     TV1: INTERNAL_DAC2
[    1.831528] [drm] fb mappable at 0xD0040000
[    1.831534] [drm] vram apper at 0xD0000000
[    1.831537] [drm] size 5763072
[    1.831539] [drm] fb depth is 24
[    1.831542] [drm]    pitch is 6400
[    1.831651] fbcon: radeondrmfb (fb0) is primary device
[    1.831760] Console: switching to colour frame buffer device 200x56
[    1.831827] fb0: radeondrmfb frame buffer device
[    1.831831] drm: registered panic notifier
[    1.832040] [drm] Initialized radeon 2.8.0 20080528 for 0000:05:04.0 on minor 0
[    1.932040] usb 4-1: new low speed USB device using uhci_hcd and address 2
[    2.224203] input: USB-compliant keyboard as /devices/pci0000:00/0000:00:1d.2/usb4/4-1/4-1:1.0/input/input2
[    2.224458] generic-usb 0003:0B38:0003.0001: input,hidraw0: USB HID v1.10 Keyboard [USB-compliant keyboard] on usb-0000:00:1d.2-1/input0
[    2.250041] input: USB-compliant keyboard as /devices/pci0000:00/0000:00:1d.2/usb4/4-1/4-1:1.1/input/input3
[    2.250522] generic-usb 0003:0B38:0003.0002: input,hiddev0,hidraw1: USB HID v1.10 Mouse [USB-compliant keyboard] on usb-0000:00:1d.2-1/input1
[    2.250684] usbcore: registered new interface driver usbhid
[    2.250689] usbhid: USB HID core driver
[    2.344027] usb 4-2: new low speed USB device using uhci_hcd and address 3
[    2.536210] Btrfs loaded
[    2.538495] input: Logitech USB Optical Mouse as /devices/pci0000:00/0000:00:1d.2/usb4/4-2/4-2:1.0/input/input4
[    2.538746] generic-usb 0003:046D:C05A.0003: input,hidraw2: USB HID v1.11 Mouse [Logitech USB Optical Mouse] on usb-0000:00:1d.2-2/input0
[    2.547402] xor: automatically using best checksumming function: pIII_sse
[    2.564012]    pIII_sse  :  4797.000 MB/sec
[    2.564016] xor: using function: pIII_sse (4797.000 MB/sec)
[    2.567817] device-mapper: dm-raid45: initialized v0.2594b
[    2.780434] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
[    2.780441] EXT4-fs (sda1): write access will be enabled during recovery
[    8.052101] EXT4-fs (sda1): orphan cleanup on readonly fs
[    8.052114] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 1308949
[    8.052193] EXT4-fs (sda1): 1 orphan inode deleted
[    8.052197] EXT4-fs (sda1): recovery complete
[    8.218756] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[   10.254818] Adding 2095100k swap on /dev/sda5.  Priority:-1 extents:1 across:2095100k 
[   10.794535] <30>udev[326]: starting version 167
[   11.080262] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   12.005962] type=1400 audit(1315414345.426:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=476 comm="apparmor_parser"
[   12.005981] type=1400 audit(1315414345.426:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=475 comm="apparmor_parser"
[   12.006992] type=1400 audit(1315414345.426:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=476 comm="apparmor_parser"
[   12.007014] type=1400 audit(1315414345.426:5): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=475 comm="apparmor_parser"
[   12.007647] type=1400 audit(1315414345.426:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=476 comm="apparmor_parser"
[   12.007674] type=1400 audit(1315414345.426:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=475 comm="apparmor_parser"
[   13.308770] type=1400 audit(1315414346.730:8): apparmor="STATUS" operation="profile_load" name="/usr/sbin/ntpd" pid=510 comm="apparmor_parser"
[   13.308849] type=1400 audit(1315414346.730:9): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/ntpd" pid=511 comm="apparmor_parser"
[   13.779115] parport_pc 00:07: reported by Plug and Play ACPI
[   13.779178] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   13.827185] ppdev: user-space parallel port driver
[   14.007627] Linux video capture interface: v2.00
[   14.128611] intel_rng: Firmware space is locked read-only. If you can't or
[   14.128616] intel_rng: don't want to disable this in firmware setup, and if
[   14.128618] intel_rng: you are certain that your system has a functional
[   14.128620] intel_rng: RNG, try using the 'no_fwh_detect' option.
[   14.136387] lp0: using parport0 (interrupt-driven).
[   14.649482] au0828 driver loaded
[   15.012113] au0828: i2c bus registered
[   15.283573] tveeprom 5-0050: Hauppauge model 72301, rev B3F0, serial# 6804132
[   15.283580] tveeprom 5-0050: MAC address is 00:0d:fe:67:d2:a4
[   15.283585] tveeprom 5-0050: tuner model is Xceive XC5000 (idx 150, type 76)
[   15.283589] tveeprom 5-0050: TV standards NTSC(M) ATSC/DVB Digital (eeprom 0x88)
[   15.283593] tveeprom 5-0050: audio processor is AU8522 (idx 44)
[   15.283597] tveeprom 5-0050: decoder processor is AU8522 (idx 42)
[   15.283601] tveeprom 5-0050: has no radio, has IR receiver, has no IR transmitter
[   15.283604] hauppauge_eeprom: hauppauge eeprom: model=72301
[   15.353802] au8522 5-0047: creating new instance
[   15.353808] au8522_decoder creating new instance...
[   15.628159] i2c-core: driver [tuner] using legacy suspend method
[   15.628165] i2c-core: driver [tuner] using legacy resume method
[   15.628648] tuner 5-0061: chip found @ 0xc2 (au0828)
[   15.748881] xc5000 5-0061: creating new instance
[   15.753572] xc5000: Successfully identified at address 0x61
[   15.753578] xc5000: Firmware has not been loaded previously
[   15.755658] au8522 5-0047: attaching existing instance
[   15.762956] xc5000 5-0061: attaching existing instance
[   15.767691] xc5000: Successfully identified at address 0x61
[   15.767695] xc5000: Firmware has not been loaded previously
[   15.767700] DVB: registering new adapter (au0828)
[   15.767705] DVB: registering adapter 0 frontend 0 (Auvitek AU8522 QAM/8VSB Frontend)...
[   15.768527] Registered device AU0828 [Hauppauge HVR850]
[   15.828689] Intel ICH 0000:00:1e.2: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   15.828737] Intel ICH 0000:00:1e.2: setting latency timer to 64
[   15.874379] usbcore: registered new interface driver snd-usb-audio
[   15.874498] usbcore: registered new interface driver au0828
[   16.248033] intel8x0_measure_ac97_clock: measured 54649 usecs (2633 samples)
[   16.248039] intel8x0: clocking to 48000
[   17.131787] type=1400 audit(1315414350.550:10): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=753 comm="apparmor_parser"
[   17.134235] type=1400 audit(1315414350.554:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=753 comm="apparmor_parser"
[   17.134810] type=1400 audit(1315414350.554:12): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=753 comm="apparmor_parser"
[   17.387003] type=1400 audit(1315414350.806:13): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=754 comm="apparmor_parser"
[   17.398972] type=1400 audit(1315414350.818:14): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=754 comm="apparmor_parser"
[   17.406199] type=1400 audit(1315414350.826:15): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-thumbnailer" pid=754 comm="apparmor_parser"
[   17.415039] type=1400 audit(1315414350.834:16): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/ntpd" pid=763 comm="apparmor_parser"
[   17.423361] type=1400 audit(1315414350.842:17): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=755 comm="apparmor_parser"
[   17.423382] type=1400 audit(1315414350.842:18): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=762 comm="apparmor_parser"
[   17.424591] type=1400 audit(1315414350.846:19): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=755 comm="apparmor_parser"
[   21.730180] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   23.957473] tg3 0000:40:00.0: eth0: Link is up at 100 Mbps, full duplex
[   23.957479] tg3 0000:40:00.0: eth0: Flow control is on for TX and on for RX
[   23.957628] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   32.917069] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   34.800011] eth0: no IPv6 routers present

LSPCI -V

> 00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 04)
	Subsystem: Hewlett-Packard Company Device 300c
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>

00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=20, subordinate=20, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: 80000000-801fffff
	Prefetchable memory behind bridge: 0000000080200000-00000000803fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=40, subordinate=40, sec-latency=0
	I/O behind bridge: 00004000-00004fff
	Memory behind bridge: f0300000-f05fffff
	Prefetchable memory behind bridge: 0000000080400000-00000000805fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Hewlett-Packard Company Device 300c
	Flags: bus master, medium devsel, latency 0, IRQ 20
	I/O ports at 3440 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Hewlett-Packard Company Device 300c
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 3460 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Hewlett-Packard Company Device 300c
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at 3480 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Hewlett-Packard Company Device 300c
	Flags: bus master, medium devsel, latency 0, IRQ 22
	I/O ports at 34a0 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03) (prog-if 20 [EHCI])
	Subsystem: Hewlett-Packard Company Device 300c
	Flags: bus master, medium devsel, latency 0, IRQ 20
	Memory at f0200000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3) (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=32
	I/O behind bridge: 00001000-00001fff
	Memory behind bridge: f0600000-f08fffff
	Prefetchable memory behind bridge: 00000000cfe00000-00000000dfffffff
	Capabilities: <access denied>

00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
	Subsystem: Hewlett-Packard Company Device 300c
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at 3000 [size=256]
	I/O ports at 3400 [size=64]
	Memory at f0200400 (32-bit, non-prefetchable) [size=512]
	Memory at f0200600 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: Intel ICH
	Kernel modules: snd-intel8x0

00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
	Flags: bus master, medium devsel, latency 0
	Kernel modules: iTCO_wdt, intel-rng

00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
	Subsystem: Hewlett-Packard Company Device 300c
	Flags: bus master, medium devsel, latency 0, IRQ 17
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 34e0 [size=16]
	Kernel driver in use: ata_piix

00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 03) (prog-if 8f [Master SecP SecO PriP PriO])
	Subsystem: Hewlett-Packard Company Device 300c
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
	I/O ports at 3810 [size=8]
	I/O ports at 3828 [size=4]
	I/O ports at 3818 [size=8]
	I/O ports at 382c [size=4]
	I/O ports at 34f0 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: ata_piix

05:04.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (rev 01) (prog-if 00 [VGA controller])
	Subsystem: Diamond Multimedia Systems Device 0160
	Flags: bus master, medium devsel, latency 32, IRQ 16
	Memory at d0000000 (32-bit, prefetchable) [size=128M]
	I/O ports at 1000 [size=256]
	Memory at f0800000 (32-bit, non-prefetchable) [size=64K]
	[virtual] Expansion ROM at cfe00000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: radeon
	Kernel modules: radeon, radeonfb

05:04.1 Display controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (Secondary) (rev 01)
	Subsystem: Diamond Multimedia Systems Device 0161
	Flags: bus master, medium devsel, latency 32
	Memory at d8000000 (32-bit, prefetchable) [size=128M]
	Memory at f0810000 (32-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>

40:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express (rev 01)
	Subsystem: Hewlett-Packard Company Device 3005
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at f0300000 (64-bit, non-prefetchable) [size=64K]
	Expansion ROM at <ignored> [disabled]
	Capabilities: <access denied>
	Kernel driver in use: tg3
	Kernel modules: tg3

---

### Post by josue0098 on 2011-09-07
Ok got it to work. I installed the v4ldvb drivers in sudo firmware ratherthan user firmware, then installed tvtime and thats it i did not even have to set up anything. the audio is a little off but atleast it works

---

