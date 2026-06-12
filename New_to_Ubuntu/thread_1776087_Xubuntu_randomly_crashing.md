---
title: "Xubuntu randomly crashing"
date: 2011-06-05
forum: New to Ubuntu
---

### Post by GaryTheCat on 2011-06-05
Pretty much as the title says, I installed Xubuntu 11.04 on an old desktop for my son - it sometimes 'crashes' by that I mean the screen goes black and a load of text pops up.

What logs do I (or a kind more experienced person than I) need to look in? and where are they?

More importantly, if I post the contents of the logs, would someone be able to help me with a diagnosis and a fix?

Thanks in advance

G

---

### Post by ubudog on 2011-06-05
Hi there, could you post the output of dmesg?

```
dmesg
```

---

### Post by GaryTheCat on 2011-06-05
Here goes:

```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.38-8-generic (buildd@vernadsky) (gcc version 4.5.2 (Ubuntu/Linaro 4.5.2-8ubuntu3) ) #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 (Ubuntu 2.6.38-8.42-generic 2.6.38.2)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000037fd0000 (usable)
[    0.000000]  BIOS-e820: 0000000037fd0000 - 0000000037fde000 (ACPI data)
[    0.000000]  BIOS-e820: 0000000037fde000 - 0000000038000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000ff780000 - 0000000100000000 (reserved)
[    0.000000] Notice: NX (Execute Disable) protection cannot be enabled in hardware: non-PAE kernel!
[    0.000000] NX (Execute Disable) protection: approximated by x86 segment limits
[    0.000000] DMI 2.3 present.
[    0.000000] DMI: Packard Bell NEC 00000000000000000000000/MS-7168, BIOS 080012  09/06/2005
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x37fd0 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0000000000 mask FFE0000000 write-back
[    0.000000]   1 base 0020000000 mask FFF0000000 write-back
[    0.000000]   2 base 0030000000 mask FFF8000000 write-back
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] found SMP MP-table at [c00ff780] ff780
[    0.000000] initial memory mapped : 0 - 01c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 1bfb000-1c00000
[    0.000000] RAMDISK: 36780000 - 373b8000
[    0.000000] ACPI: RSDP 000f9210 00014 (v00 ACPIAM)
[    0.000000] ACPI: RSDT 37fd0000 00038 (v01 A M I  OEMRSDT  09000506 MSFT 00000097)
[    0.000000] ACPI: FACP 37fd0200 00084 (v02 A M I  OEMFACP  09000506 MSFT 00000097)
[    0.000000] ACPI: DSDT 37fd0430 0397A (v01  0AAAA 0AAAA000 00000000 INTL 02002026)
[    0.000000] ACPI: FACS 37fde000 00040
[    0.000000] ACPI: APIC 37fd0390 0005C (v01 A M I  OEMAPIC  09000506 MSFT 00000097)
[    0.000000] ACPI: MCFG 37fd03f0 0003C (v01 A M I  OEMMCFG  09000506 MSFT 00000097)
[    0.000000] ACPI: SSDT 37fd3db0 00D6E (v01    ATI ATIPATCH 00000001 INTL 02002026)
[    0.000000] ACPI: OEMB 37fde040 00056 (v01 A M I  AMI_OEM  09000506 MSFT 00000097)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 7MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x00037fd0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x00037fd0
[    0.000000] On node 0 totalpages: 229215
[    0.000000] free_area_init_node: node 0, pgdat c1784100, node_mem_map f6080200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 16 pages used for memmap
[    0.000000]   HighMem zone: 1986 pages, LIFO batch:0
[    0.000000] Using APIC driver default
[    0.000000] SB4X0 revision 0x10
[    0.000000] Ignoring ACPI timer override.
[    0.000000] If you got timer trouble try acpi_use_timer_override
[    0.000000] Detected use of extended apic ids on hypertransport bus
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x81] disabled)
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: BIOS IRQ0 pin2 override ignored.
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 21 low level)
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 2 CPUs, 1 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e4000
[    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 38000000 (gap: 38000000:c7780000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 13 pages/cpu @f5c00000 s28800 r0 d24448 u2097152
[    0.000000] pcpu-alloc: s28800 r0 d24448 u2097152 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 1 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 227423
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-8-generic root=UUID=e7099f9c-9617-4ad5-acf5-91aebe14bc05 ro vga=792 quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] allocated 4586240 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:00037fd0)
[    0.000000] Memory: 882408k/917312k available (5188k kernel code, 34452k reserved, 2540k data, 700k init, 8008k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc178d000 - 0xc183c000   ( 700 kB)
[    0.000000]       .data : 0xc15112a1 - 0xc178c480   (2540 kB)
[    0.000000]       .text : 0xc1000000 - 0xc15112a1   (5188 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU-based detection of stalled CPUs is disabled.
[    0.000000] NR_IRQS:2304 nr_irqs:512 16
[    0.000000] CPU 0 irqstacks, hard=f5008000 soft=f500a000
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] Fast TSC calibration failed
[    0.000000] TSC: Unable to calibrate against PIT
[    0.000000] TSC: using PMTIMER reference calibration
[    0.000000] Detected 2188.724 MHz processor.
[    0.000000] Marking TSC unstable due to TSCs unsynchronized
[    0.012006] Calibrating delay loop (skipped), value calculated using timer frequency.. 4377.44 BogoMIPS (lpj=8754896)
[    0.012013] pid_max: default: 32768 minimum: 301
[    0.012043] Security Framework initialized
[    0.012070] AppArmor: AppArmor initialized
[    0.012073] Yama: becoming mindful.
[    0.012145] Mount-cache hash table entries: 512
[    0.012306] Initializing cgroup subsys ns
[    0.012310] ns_cgroup deprecated: consider using the 'clone_children' flag without the ns_cgroup.
[    0.012315] Initializing cgroup subsys cpuacct
[    0.012321] Initializing cgroup subsys memory
[    0.012331] Initializing cgroup subsys devices
[    0.012335] Initializing cgroup subsys freezer
[    0.012338] Initializing cgroup subsys net_cls
[    0.012341] Initializing cgroup subsys blkio
[    0.012378] mce: CPU supports 5 MCE banks
[    0.013008] SMP alternatives: switching to UP code
[    0.022580] ACPI: Core revision 20110112
[    0.026348] ftrace: allocating 23640 entries in 47 pages
[    0.028115] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.028462] ..TIMER: vector=0x30 apic1=0 pin1=0 apic2=-1 pin2=-1
[    0.069646] CPU0: AMD Athlon(tm) 64 Processor 3400+ stepping 02
[    0.072003] Performance Events: AMD PMU driver.
[    0.072003] ... version:                0
[    0.072003] ... bit width:              48
[    0.072003] ... generic registers:      4
[    0.072003] ... value mask:             0000ffffffffffff
[    0.072003] ... max period:             00007fffffffffff
[    0.072003] ... fixed-purpose events:   0
[    0.072003] ... event mask:             000000000000000f
[    0.072003] Brought up 1 CPUs
[    0.072003] Total of 1 processors activated (4377.44 BogoMIPS).
[    0.072003] devtmpfs: initialized
[    0.072003] print_constraints: dummy: 
[    0.072003] Time:  0:41:24  Date: 06/06/11
[    0.072003] NET: Registered protocol family 16
[    0.072003] EISA bus registered
[    0.072003] node 0 link 0: io port [1000, ffffff]
[    0.072003] TOM: 0000000040000000 aka 1024M
[    0.072003] node 0 link 0: mmio [bff00000, dfeeffff]
[    0.072003] node 0 link 0: mmio [40000000, bfefffff]
[    0.072003] node 0 link 0: mmio [e0000000, efffffff]
[    0.072003] node 0 link 0: mmio [dfef0000, dfffffff]
[    0.072003] node 0 link 0: mmio [a0000, bffff]
[    0.072003] node 0 link 0: mmio [f0000000, ffffffff]
[    0.072003] bus: [00, ff] on node 0 link 0
[    0.072003] bus: 00 index 0 [io  0x0000-0xffff]
[    0.072003] bus: 00 index 1 [mem 0x40000000-0xdfffffff]
[    0.072003] bus: 00 index 2 [mem 0xe0000000-0xffffffff]
[    0.072003] bus: 00 index 3 [mem 0x000a0000-0x000bffff]
[    0.072003] ACPI: bus type pci registered
[    0.072003] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.072003] PCI: not using MMCONFIG
[    0.072003] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=2
[    0.072003] PCI: Using configuration type 1 for base access
[    0.072369] bio: create slab <bio-0> at 0
[    0.073257] ACPI: EC: Look up EC in DSDT
[    0.074111] ACPI: Executed 3 blocks of module-level executable AML code
[    0.075863] ACPI: Interpreter enabled
[    0.075870] ACPI: (supports S0 S3 S4 S5)
[    0.075888] ACPI: Using IOAPIC for interrupt routing
[    0.075966] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.077047] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in ACPI motherboard resources
[    0.077049] PCI: Using MMCONFIG for extended config space
[    0.081445] ACPI: No dock devices found.
[    0.081447] HEST: Table not found.
[    0.081452] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
[    0.081518] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.081660] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7] (ignored)
[    0.081663] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff] (ignored)
[    0.081666] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)
[    0.081669] pci_root PNP0A03:00: host bridge window [mem 0x000d0000-0x000dffff] (ignored)
[    0.081672] pci_root PNP0A03:00: host bridge window [mem 0x40000000-0xffffffff] (ignored)
[    0.081683] pci 0000:00:00.0: [1002:5950] type 0 class 0x000600
[    0.081717] pci 0000:00:01.0: [1002:5a3f] type 1 class 0x000604
[    0.081785] pci 0000:00:11.0: [1002:437a] type 0 class 0x000101
[    0.081811] pci 0000:00:11.0: reg 10: [io  0xbc00-0xbc07]
[    0.081824] pci 0000:00:11.0: reg 14: [io  0xb800-0xb803]
[    0.081837] pci 0000:00:11.0: reg 18: [io  0xb400-0xb407]
[    0.081851] pci 0000:00:11.0: reg 1c: [io  0xb000-0xb003]
[    0.081864] pci 0000:00:11.0: reg 20: [io  0xac00-0xac0f]
[    0.081878] pci 0000:00:11.0: reg 24: [mem 0xff6ffc00-0xff6ffdff]
[    0.081891] pci 0000:00:11.0: reg 30: [mem 0xff600000-0xff67ffff pref]
[    0.081925] pci 0000:00:11.0: supports D1 D2
[    0.081954] pci 0000:00:12.0: [1002:4379] type 0 class 0x000101
[    0.081981] pci 0000:00:12.0: reg 10: [io  0xa800-0xa807]
[    0.081994] pci 0000:00:12.0: reg 14: [io  0xa400-0xa403]
[    0.082007] pci 0000:00:12.0: reg 18: [io  0xa000-0xa007]
[    0.082020] pci 0000:00:12.0: reg 1c: [io  0x9c00-0x9c03]
[    0.082033] pci 0000:00:12.0: reg 20: [io  0x9800-0x980f]
[    0.082047] pci 0000:00:12.0: reg 24: [mem 0xff6ff800-0xff6ff9ff]
[    0.082061] pci 0000:00:12.0: reg 30: [mem 0xff580000-0xff5fffff pref]
[    0.082094] pci 0000:00:12.0: supports D1 D2
[    0.082120] pci 0000:00:13.0: [1002:4374] type 0 class 0x000c03
[    0.082143] pci 0000:00:13.0: reg 10: [mem 0xff6fe000-0xff6fefff]
[    0.082257] pci 0000:00:13.1: [1002:4375] type 0 class 0x000c03
[    0.082280] pci 0000:00:13.1: reg 10: [mem 0xff6fd000-0xff6fdfff]
[    0.082396] pci 0000:00:13.2: [1002:4373] type 0 class 0x000c03
[    0.082423] pci 0000:00:13.2: reg 10: [mem 0xff6fc000-0xff6fcfff]
[    0.082520] pci 0000:00:13.2: supports D1 D2
[    0.082522] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
[    0.082528] pci 0000:00:13.2: PME# disabled
[    0.082563] pci 0000:00:14.0: [1002:4372] type 0 class 0x000c05
[    0.082585] pci 0000:00:14.0: reg 10: [io  0x0b00-0x0b0f]
[    0.082598] pci 0000:00:14.0: reg 14: [mem 0x00000000-0x000003ff]
[    0.082657] HPET not enabled in BIOS. You might try hpet=force boot option
[    0.082699] pci 0000:00:14.1: [1002:4376] type 0 class 0x000101
[    0.082723] pci 0000:00:14.1: reg 10: [io  0x01f0-0x01f7]
[    0.082736] pci 0000:00:14.1: reg 14: [io  0x03f4-0x03f7]
[    0.082749] pci 0000:00:14.1: reg 18: [io  0x0170-0x0177]
[    0.082762] pci 0000:00:14.1: reg 1c: [io  0x0374-0x0377]
[    0.082775] pci 0000:00:14.1: reg 20: [io  0xff00-0xff0f]
[    0.082842] pci 0000:00:14.3: [1002:4377] type 0 class 0x000601
[    0.082944] pci 0000:00:14.4: [1002:4371] type 1 class 0x000604
[    0.083006] pci 0000:00:14.5: [1002:4370] type 0 class 0x000401
[    0.083028] pci 0000:00:14.5: reg 10: [mem 0xff6ff400-0xff6ff4ff]
[    0.083139] pci 0000:00:18.0: [1022:1100] type 0 class 0x000600
[    0.083162] pci 0000:00:18.1: [1022:1101] type 0 class 0x000600
[    0.083179] pci 0000:00:18.2: [1022:1102] type 0 class 0x000600
[    0.083197] pci 0000:00:18.3: [1022:1103] type 0 class 0x000600
[    0.083222] PCI: peer root bus 00 res updated from pci conf
[    0.083248] pci 0000:01:05.0: [1002:5954] type 0 class 0x000300
[    0.083256] pci 0000:01:05.0: reg 10: [mem 0xc0000000-0xcfffffff pref]
[    0.083262] pci 0000:01:05.0: reg 14: [io  0x7800-0x78ff]
[    0.083267] pci 0000:01:05.0: reg 18: [mem 0xff2f0000-0xff2fffff]
[    0.083281] pci 0000:01:05.0: reg 30: [mem 0xff2c0000-0xff2dffff pref]
[    0.083290] pci 0000:01:05.0: supports D1 D2
[    0.083305] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.083309] pci 0000:00:01.0:   bridge window [io  0x7000-0x7fff]
[    0.083312] pci 0000:00:01.0:   bridge window [mem 0xff200000-0xff2fffff]
[    0.083317] pci 0000:00:01.0:   bridge window [mem 0xbff00000-0xdfefffff 64bit pref]
[    0.083352] pci 0000:02:00.0: [163c:3052] type 0 class 0x000703
[    0.083381] pci 0000:02:00.0: reg 10: [mem 0xff3ff000-0xff3fffff]
[    0.083398] pci 0000:02:00.0: reg 14: [io  0x8800-0x88ff]
[    0.083500] pci 0000:02:00.0: PME# supported from D0 D3hot D3cold
[    0.083507] pci 0000:02:00.0: PME# disabled
[    0.083540] pci 0000:02:03.0: [10ec:8139] type 0 class 0x000200
[    0.083568] pci 0000:02:03.0: reg 10: [io  0x8400-0x84ff]
[    0.083584] pci 0000:02:03.0: reg 14: [mem 0xff3fec00-0xff3fecff]
[    0.083654] pci 0000:02:03.0: reg 30: [mem 0xff3e0000-0xff3effff pref]
[    0.083685] pci 0000:02:03.0: supports D1 D2
[    0.083687] pci 0000:02:03.0: PME# supported from D1 D2 D3hot D3cold
[    0.083693] pci 0000:02:03.0: PME# disabled
[    0.083721] pci 0000:02:04.0: [1106:3044] type 0 class 0x000c00
[    0.083750] pci 0000:02:04.0: reg 10: [mem 0xff3fe000-0xff3fe7ff]
[    0.083767] pci 0000:02:04.0: reg 14: [io  0x8c00-0x8c7f]
[    0.083871] pci 0000:02:04.0: supports D2
[    0.083873] pci 0000:02:04.0: PME# supported from D2 D3hot D3cold
[    0.083879] pci 0000:02:04.0: PME# disabled
[    0.083943] pci 0000:00:14.4: PCI bridge to [bus 02-02] (subtractive decode)
[    0.083952] pci 0000:00:14.4:   bridge window [io  0x8000-0x8fff]
[    0.083958] pci 0000:00:14.4:   bridge window [mem 0xff300000-0xff3fffff]
[    0.083964] pci 0000:00:14.4:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.083967] pci 0000:00:14.4:   bridge window [io  0x0000-0xffff] (subtractive decode)
[    0.083970] pci 0000:00:14.4:   bridge window [mem 0x40000000-0xdfffffff] (subtractive decode)
[    0.083972] pci 0000:00:14.4:   bridge window [mem 0xe0000000-0xffffffff] (subtractive decode)
[    0.083975] pci 0000:00:14.4:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.083988] pci_bus 0000:00: on NUMA node 0
[    0.083991] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.084048] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.084098] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P9._PRT]
[    0.084175]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.088803] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.088848] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.088890] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.088932] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.088975] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.089017] ACPI: PCI Interrupt Link [LNKF] (IRQs 9) *0, disabled.
[    0.089056] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.089099] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.089220] vgaarb: device added: PCI:0000:01:05.0,decodes=io+mem,owns=io+mem,locks=none
[    0.089223] vgaarb: loaded
[    0.089469] SCSI subsystem initialized
[    0.089547] libata version 3.00 loaded.
[    0.089608] usbcore: registered new interface driver usbfs
[    0.089624] usbcore: registered new interface driver hub
[    0.089650] usbcore: registered new device driver usb
[    0.089761] wmi: Mapper loaded
[    0.089763] PCI: Using ACPI for IRQ routing
[    0.089766] PCI: pci_cache_line_size set to 64 bytes
[    0.089846] reserve RAM buffer: 000000000009fc00 - 000000000009ffff 
[    0.089849] reserve RAM buffer: 0000000037fd0000 - 0000000037ffffff 
[    0.089965] NetLabel: Initializing
[    0.089967] NetLabel:  domain hash size = 128
[    0.089968] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.089981] NetLabel:  unlabeled traffic allowed by default
[    0.098564] AppArmor: AppArmor Filesystem Enabled
[    0.098610] pnp: PnP ACPI init
[    0.098642] ACPI: bus type pnp registered
[    0.098782] pnp 00:00: [bus 00-ff]
[    0.098786] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.098789] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.098791] pnp 00:00: [io  0x0d00-0xffff window]
[    0.098794] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.098800] pnp 00:00: [mem 0x000d0000-0x000dffff window]
[    0.098803] pnp 00:00: [mem 0x40000000-0xffffffff window]
[    0.098861] pnp 00:00: Plug and Play ACPI device, IDs PNP0a03 (active)
[    0.098901] pnp 00:01: [dma 4]
[    0.098903] pnp 00:01: [io  0x0000-0x000f]
[    0.098905] pnp 00:01: [io  0x0081-0x0083]
[    0.098907] pnp 00:01: [io  0x0087]
[    0.098909] pnp 00:01: [io  0x0089-0x008b]
[    0.098911] pnp 00:01: [io  0x008f]
[    0.098913] pnp 00:01: [io  0x00c0-0x00df]
[    0.098944] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.098955] pnp 00:02: [io  0x0070-0x0071]
[    0.098973] pnp 00:02: [irq 8]
[    0.099001] pnp 00:02: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.099009] pnp 00:03: [io  0x0061]
[    0.099041] pnp 00:03: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.099051] pnp 00:04: [io  0x00f0-0x00ff]
[    0.099056] pnp 00:04: [irq 13]
[    0.099084] pnp 00:04: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.099339] pnp 00:05: [io  0x03f8-0x03ff]
[    0.099345] pnp 00:05: [irq 4]
[    0.099347] pnp 00:05: [dma 0 disabled]
[    0.099413] pnp 00:05: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.099653] pnp 00:06: [io  0x02f8-0x02ff]
[    0.099658] pnp 00:06: [irq 3]
[    0.099660] pnp 00:06: [dma 0]
[    0.099750] pnp 00:06: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.100171] pnp 00:07: [io  0x0378-0x037f]
[    0.100176] pnp 00:07: [irq 7]
[    0.100178] pnp 00:07: [dma 0 disabled]
[    0.100306] pnp 00:07: Plug and Play ACPI device, IDs PNP0400 (active)
[    0.100381] pnp 00:08: [io  0x0010-0x001f]
[    0.100383] pnp 00:08: [io  0x0022-0x003f]
[    0.100385] pnp 00:08: [io  0x0044-0x005f]
[    0.100393] pnp 00:08: [io  0x0062-0x0063]
[    0.100395] pnp 00:08: [io  0x0065-0x006f]
[    0.100397] pnp 00:08: [io  0x0072-0x007f]
[    0.100399] pnp 00:08: [io  0x0080]
[    0.100401] pnp 00:08: [io  0x0084-0x0086]
[    0.100403] pnp 00:08: [io  0x0088]
[    0.100405] pnp 00:08: [io  0x008c-0x008e]
[    0.100407] pnp 00:08: [io  0x0090-0x009f]
[    0.100409] pnp 00:08: [io  0x00a2-0x00bf]
[    0.100411] pnp 00:08: [io  0x00e0-0x00ef]
[    0.100413] pnp 00:08: [io  0x04d0-0x04d1]
[    0.100415] pnp 00:08: [io  0x040b]
[    0.100417] pnp 00:08: [io  0x04d6]
[    0.100419] pnp 00:08: [io  0x0c00-0x0c01]
[    0.100422] pnp 00:08: [io  0x0c14]
[    0.100424] pnp 00:08: [io  0x0c50-0x0c51]
[    0.100426] pnp 00:08: [io  0x0c52]
[    0.100428] pnp 00:08: [io  0x0c6c]
[    0.100430] pnp 00:08: [io  0x0c6f]
[    0.100432] pnp 00:08: [io  0x0cd4-0x0cd5]
[    0.100434] pnp 00:08: [io  0x0cd6-0x0cd7]
[    0.100436] pnp 00:08: [io  0x0cd8-0x0cdf]
[    0.100438] pnp 00:08: [io  0x0800-0x089f]
[    0.100440] pnp 00:08: [io  0x0000-0xffffffff disabled]
[    0.100443] pnp 00:08: [io  0x0900-0x090f]
[    0.100445] pnp 00:08: [io  0x0910-0x091f]
[    0.100447] pnp 00:08: [mem 0xfff80000-0xffffffff]
[    0.100556] system 00:08: [io  0x04d0-0x04d1] has been reserved
[    0.100559] system 00:08: [io  0x040b] has been reserved
[    0.100562] system 00:08: [io  0x04d6] has been reserved
[    0.100565] system 00:08: [io  0x0c00-0x0c01] has been reserved
[    0.100568] system 00:08: [io  0x0c14] has been reserved
[    0.100571] system 00:08: [io  0x0c50-0x0c51] has been reserved
[    0.100574] system 00:08: [io  0x0c52] has been reserved
[    0.100576] system 00:08: [io  0x0c6c] has been reserved
[    0.100579] system 00:08: [io  0x0c6f] has been reserved
[    0.100582] system 00:08: [io  0x0cd4-0x0cd5] has been reserved
[    0.100585] system 00:08: [io  0x0cd6-0x0cd7] has been reserved
[    0.100588] system 00:08: [io  0x0cd8-0x0cdf] has been reserved
[    0.100591] system 00:08: [io  0x0800-0x089f] has been reserved
[    0.100594] system 00:08: [io  0x0900-0x090f] has been reserved
[    0.100597] system 00:08: [io  0x0910-0x091f] has been reserved
[    0.100601] system 00:08: [mem 0xfff80000-0xffffffff] has been reserved
[    0.100604] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.100691] pnp 00:09: [io  0x0000-0xffffffff disabled]
[    0.100694] pnp 00:09: [io  0x0e00-0x0e7f]
[    0.100743] system 00:09: [io  0x0e00-0x0e7f] has been reserved
[    0.100747] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.100791] pnp 00:0a: [mem 0xfec00000-0xfec00fff]
[    0.100793] pnp 00:0a: [mem 0xfee00000-0xfee00fff]
[    0.100837] system 00:0a: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.100840] system 00:0a: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.100844] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.100873] pnp 00:0b: [mem 0xe0000000-0xefffffff]
[    0.100916] system 00:0b: [mem 0xe0000000-0xefffffff] has been reserved
[    0.100919] system 00:0b: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.101035] pnp 00:0c: [mem 0x00000000-0x0009ffff]
[    0.101038] pnp 00:0c: [mem 0x000c0000-0x000cffff]
[    0.101040] pnp 00:0c: [mem 0x000e0000-0x000fffff]
[    0.101042] pnp 00:0c: [mem 0x00100000-0x3fffffff]
[    0.101045] pnp 00:0c: [mem 0x00000000-0xffffffff disabled]
[    0.101094] system 00:0c: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.101097] system 00:0c: [mem 0x000c0000-0x000cffff] could not be reserved
[    0.101100] system 00:0c: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.101103] system 00:0c: [mem 0x00100000-0x3fffffff] could not be reserved
[    0.101106] system 00:0c: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.101216] pnp: PnP ACPI: found 13 devices
[    0.101218] ACPI: ACPI bus type pnp unregistered
[    0.101222] PnPBIOS: Disabled by ACPI PNP
[    0.137608] Switching to clocksource acpi_pm
[    0.137650] pci 0000:00:14.0: BAR 1: assigned [mem 0x40000000-0x400003ff]
[    0.137657] pci 0000:00:14.0: BAR 1: set to [mem 0x40000000-0x400003ff] (PCI address [0x40000000-0x400003ff])
[    0.137661] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.137664] pci 0000:00:01.0:   bridge window [io  0x7000-0x7fff]
[    0.137668] pci 0000:00:01.0:   bridge window [mem 0xff200000-0xff2fffff]
[    0.137672] pci 0000:00:01.0:   bridge window [mem 0xbff00000-0xdfefffff 64bit pref]
[    0.137676] pci 0000:00:14.4: PCI bridge to [bus 02-02]
[    0.137680] pci 0000:00:14.4:   bridge window [io  0x8000-0x8fff]
[    0.137687] pci 0000:00:14.4:   bridge window [mem 0xff300000-0xff3fffff]
[    0.137693] pci 0000:00:14.4:   bridge window [mem pref disabled]
[    0.137713] pci_bus 0000:00: resource 4 [io  0x0000-0xffff]
[    0.137715] pci_bus 0000:00: resource 5 [mem 0x40000000-0xdfffffff]
[    0.137718] pci_bus 0000:00: resource 6 [mem 0xe0000000-0xffffffff]
[    0.137721] pci_bus 0000:00: resource 7 [mem 0x000a0000-0x000bffff]
[    0.137724] pci_bus 0000:01: resource 0 [io  0x7000-0x7fff]
[    0.137726] pci_bus 0000:01: resource 1 [mem 0xff200000-0xff2fffff]
[    0.137729] pci_bus 0000:01: resource 2 [mem 0xbff00000-0xdfefffff 64bit pref]
[    0.137732] pci_bus 0000:02: resource 0 [io  0x8000-0x8fff]
[    0.137735] pci_bus 0000:02: resource 1 [mem 0xff300000-0xff3fffff]
[    0.137737] pci_bus 0000:02: resource 4 [io  0x0000-0xffff]
[    0.137740] pci_bus 0000:02: resource 5 [mem 0x40000000-0xdfffffff]
[    0.137743] pci_bus 0000:02: resource 6 [mem 0xe0000000-0xffffffff]
[    0.137745] pci_bus 0000:02: resource 7 [mem 0x000a0000-0x000bffff]
[    0.137790] NET: Registered protocol family 2
[    0.137860] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.138185] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.139205] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.139741] TCP: Hash tables configured (established 131072 bind 65536)
[    0.139744] TCP reno registered
[    0.139748] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.139768] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.139890] NET: Registered protocol family 1
[    0.139903] pci 0000:00:00.0: MSI quirk detected; MSI disabled
[    0.139911] pci 0000:00:01.0: MSI quirk detected; subordinate MSI disabled
[    0.149045] Switched to NOHz mode on CPU #0
[    0.180061] pci 0000:01:05.0: Boot video device
[    0.180074] PCI: CLS 64 bytes, default 64
[    0.180347] cpufreq-nforce2: No nForce2 chipset.
[    0.180509] audit: initializing netlink socket (disabled)
[    0.180520] type=2000 audit(1307320884.176:1): initialized
[    0.190817] Trying to unpack rootfs image as initramfs...
[    0.208388] highmem bounce pool size: 64 pages
[    0.208396] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.216344] VFS: Disk quotas dquot_6.5.2
[    0.216462] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.217216] fuse init (API version 7.16)
[    0.217312] msgmni has been set to 1707
[    0.224414] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.224447] io scheduler noop registered
[    0.224449] io scheduler deadline registered
[    0.224468] io scheduler cfq registered (default)
[    0.224625] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.224656] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.224829] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.224837] ACPI: Power Button [PWRB]
[    0.224890] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.224893] ACPI: Power Button [PWRF]
[    0.225048] ACPI: acpi_idle registered with cpuidle
[    0.225067] ACPI: duty_cycle spans bit 4
[    0.226416] ERST: Table is not found!
[    0.226543] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.247215] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.247245] isapnp: Scanning for PnP cards...
[    0.337035] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    0.377790] 00:05: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.464915] 00:06: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    0.484308] serial 0000:02:00.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.484508] 0000:02:00.0: ttyS5 at I/O 0x8808 (irq = 20) is a 16450
[    0.484611] 0000:02:00.0: ttyS6 at I/O 0x8810 (irq = 20) is a 8250
[    0.484713] 0000:02:00.0: ttyS7 at I/O 0x8818 (irq = 20) is a 16450
[    0.484814] 0000:02:00.0: ttyS8 at I/O 0x8820 (irq = 20) is a 8250
[    0.484916] 0000:02:00.0: ttyS9 at I/O 0x8828 (irq = 20) is a 8250
[    0.486859] Linux agpgart interface v0.103
[    0.492671] brd: module loaded
[    0.493265] loop: module loaded
[    0.493406] i2c-core: driver [adp5520] using legacy suspend method
[    0.493409] i2c-core: driver [adp5520] using legacy resume method
[    0.493602] pata_acpi 0000:00:11.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.493680] pata_acpi 0000:00:12.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    0.493713] pata_acpi 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.493731] pata_acpi 0000:00:14.1: setting latency timer to 64
[    0.494141] Fixed MDIO Bus: probed
[    0.494184] PPP generic driver version 2.4.2
[    0.494223] tun: Universal TUN/TAP device driver, 1.6
[    0.494225] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.494318] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.494337] ehci_hcd 0000:00:13.2: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.494359] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    0.494395] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 1
[    0.494472] ehci_hcd 0000:00:13.2: irq 19, io mem 0xff6fc000
[    0.543842] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    0.628295] hub 1-0:1.0: USB hub found
[    0.628302] hub 1-0:1.0: 8 ports detected
[    0.628419] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.628448] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.628475] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    0.628551] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 2
[    0.628580] ohci_hcd 0000:00:13.0: irq 19, io mem 0xff6fe000
[    0.692245] hub 2-0:1.0: USB hub found
[    0.692256] hub 2-0:1.0: 4 ports detected
[    0.692356] ohci_hcd 0000:00:13.1: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.692383] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    0.692427] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 3
[    0.692456] ohci_hcd 0000:00:13.1: irq 19, io mem 0xff6fd000
[    0.844372] hub 3-0:1.0: USB hub found
[    0.844384] hub 3-0:1.0: 4 ports detected
[    0.844494] uhci_hcd: USB Universal Host Controller Interface driver
[    0.844616] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    0.853041] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.853058] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.853195] mousedev: PS/2 mouse device common for all mice
[    0.853333] rtc_cmos 00:02: RTC can wake from S4
[    0.853390] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    0.853420] rtc0: alarms up to one month, 114 bytes nvram
[    0.853540] device-mapper: uevent: version 1.0.3
[    0.853631] device-mapper: ioctl: 4.19.1-ioctl (2011-01-07) initialised: dm-devel@redhat.com
[    0.853765] device-mapper: multipath: version 1.2.0 loaded
[    0.853769] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.853863] EISA: Probing bus 0 at eisa.0
[    0.853866] EISA: Cannot allocate resource for mainboard
[    0.853869] Cannot allocate resource for EISA slot 1
[    0.853871] Cannot allocate resource for EISA slot 2
[    0.853874] Cannot allocate resource for EISA slot 3
[    0.853876] Cannot allocate resource for EISA slot 4
[    0.853878] Cannot allocate resource for EISA slot 5
[    0.853880] Cannot allocate resource for EISA slot 6
[    0.853882] Cannot allocate resource for EISA slot 7
[    0.853885] Cannot allocate resource for EISA slot 8
[    0.853886] EISA: Detected 0 cards.
[    0.856453] cpuidle: using governor ladder
[    0.856457] cpuidle: using governor menu
[    0.856759] TCP cubic registered
[    0.856904] NET: Registered protocol family 10
[    0.857474] NET: Registered protocol family 17
[    0.857503] Registering the dns_resolver key type
[    0.857534] powernow-k8: Found 1 AMD Athlon(tm) 64 Processor 3400+ (1 cpu cores) (version 2.20.00)
[    0.857603] powernow-k8:    0 : fid 0xe (2200 MHz), vid 0x6
[    0.857606] powernow-k8:    1 : fid 0xc (2000 MHz), vid 0x8
[    0.857608] powernow-k8:    2 : fid 0xa (1800 MHz), vid 0xa
[    0.857610] powernow-k8:    3 : fid 0x2 (1000 MHz), vid 0x12
[    0.857649] Using IPI No-Shortcut mode
[    0.857785] PM: Hibernation image not present or could not be loaded.
[    0.857797] registered taskstats version 1
[    0.858049]   Magic number: 15:577:657
[    0.858070] block ram10: hash matches
[    0.858182] rtc_cmos 00:02: setting system clock to 2011-06-06 00:41:25 UTC (1307320885)
[    0.858185] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.858187] EDD information not available.
[    0.919245] isapnp: No Plug & Play device found
[    0.972189] usb 1-2: new high speed USB device using ehci_hcd and address 2
[    0.981018] Freeing initrd memory: 12512k freed
[    0.994200] Freeing unused kernel memory: 700k freed
[    0.994945] Write protecting the kernel text: 5192k
[    0.994981] Write protecting the kernel read-only data: 2148k
[    1.021442] <30>udev[61]: starting version 167
[    1.228230] scsi0 : pata_atiixp
[    1.230442] scsi1 : pata_atiixp
[    1.231229] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xff00 irq 14
[    1.231233] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xff08 irq 15
[    1.246174] sata_sil 0000:00:11.0: version 2.4
[    1.249555] scsi2 : sata_sil
[    1.252179] scsi3 : sata_sil
[    1.252263] ata3: SATA max UDMA/100 mmio m512@0xff6ffc00 tf 0xff6ffc80 irq 23
[    1.252268] ata4: SATA max UDMA/100 mmio m512@0xff6ffc00 tf 0xff6ffcc0 irq 23
[    1.254550] scsi4 : sata_sil
[    1.255868] scsi5 : sata_sil
[    1.255938] ata5: SATA max UDMA/100 mmio m512@0xff6ff800 tf 0xff6ff880 irq 22
[    1.255943] ata6: SATA max UDMA/100 mmio m512@0xff6ff800 tf 0xff6ff8c0 irq 22
[    1.259666] 8139cp: 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    1.259697] 8139cp 0000:02:03.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
[    1.404652] ata2.00: ATAPI: _NEC DVD_RW ND-3550A, 1.52, max UDMA/33
[    1.420541] ata2.00: configured for UDMA/33
[    1.422360] scsi 1:0:0:0: CD-ROM            _NEC     DVD_RW ND-3550A  1.52 PQ: 0 ANSI: 5
[    1.423976] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[    1.423979] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.424132] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.424212] sr 1:0:0:0: Attached scsi generic sg0 type 5
[    1.572059] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.576037] ata5: SATA link down (SStatus 0 SControl 300)
[    1.580476] ata3.00: ATA-6: ST3160023AS, 3.00, max UDMA/133
[    1.580478] ata3.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.596461] ata3.00: configured for UDMA/100
[    1.596561] scsi 2:0:0:0: Direct-Access     ATA      ST3160023AS      3.00 PQ: 0 ANSI: 5
[    1.596735] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    1.596841] sd 2:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    1.596888] sd 2:0:0:0: [sda] Write Protect is off
[    1.596891] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.596912] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.645858]  sda: sda1 sda2 sda3 sda4 < sda5 sda6 >
[    1.646254] sd 2:0:0:0: [sda] Attached SCSI disk
[    1.708022] usb 2-2: new low speed USB device using ohci_hcd and address 2
[    1.916038] ata4: SATA link down (SStatus 0 SControl 300)
[    1.945952] input: CHESEN USB Keyboard as /devices/pci0000:00/0000:00:13.0/usb2/2-2/2-2:1.0/input/input2
[    1.946129] generic-usb 0003:0A81:0101.0001: input,hidraw0: USB HID v1.10 Keyboard [CHESEN USB Keyboard] on usb-0000:00:13.0-2/input0
[    1.956505] input: CHESEN USB Keyboard as /devices/pci0000:00/0000:00:13.0/usb2/2-2/2-2:1.1/input/input3
[    1.956641] generic-usb 0003:0A81:0101.0002: input,hidraw1: USB HID v1.10 Device [CHESEN USB Keyboard] on usb-0000:00:13.0-2/input1
[    1.956862] usbcore: registered new interface driver usbhid
[    1.956864] usbhid: USB HID core driver
[    2.224024] usb 2-3: new full speed USB device using ohci_hcd and address 3
[    2.236042] ata6: SATA link down (SStatus 0 SControl 300)
[    2.250192] firewire_ohci 0000:02:04.0: PCI INT A -> GSI 21 (level, low) -> IRQ 9
[    2.250280] 8139too: 8139too Fast Ethernet driver 0.9.28
[    2.312101] firewire_ohci: Added fw-ohci device 0000:02:04.0, OHCI v1.10, 4 IR + 8 IT contexts, quirks 0x11
[    2.312365] 8139too 0000:02:03.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    2.313801] 8139too 0000:02:03.0: eth0: RealTek RTL8139 at 0x8400, 00:13:d3:b6:87:61, IRQ 20
[    2.444947] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:13.0/usb2/2-3/2-3:1.0/input/input4
[    2.445075] generic-usb 0003:046D:C52F.0003: input,hidraw2: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:13.0-3/input0
[    2.452549] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:13.0/usb2/2-3/2-3:1.1/input/input5
[    2.452712] generic-usb 0003:046D:C52F.0004: input,hiddev0,hidraw3: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:13.0-3/input1
[    2.756031] usb 2-4: new full speed USB device using ohci_hcd and address 4
[    2.812143] firewire_core: created device fw0: GUID 0010dc0000d171d0, S400
[    2.970649] usbcore: registered new interface driver uas
[    2.976714] Initializing USB Mass Storage driver...
[    2.976857] scsi6 : usb-storage 2-4:1.0
[    2.977166] usbcore: registered new interface driver usb-storage
[    2.977168] USB Mass Storage support registered.
[    3.154624] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
[    3.982432] scsi 6:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
[    3.988431] scsi 6:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
[    3.994426] scsi 6:0:0:2: Direct-Access     Generic  USB SM Reader    1.02 PQ: 0 ANSI: 0
[    4.000428] scsi 6:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0
[    4.000860] sd 6:0:0:0: Attached scsi generic sg2 type 0
[    4.001011] sd 6:0:0:1: Attached scsi generic sg3 type 0
[    4.001159] sd 6:0:0:2: Attached scsi generic sg4 type 0
[    4.001301] sd 6:0:0:3: Attached scsi generic sg5 type 0
[    4.090419] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[    4.100422] sd 6:0:0:1: [sdc] Attached SCSI removable disk
[    4.110431] sd 6:0:0:2: [sdd] Attached SCSI removable disk
[    4.120417] sd 6:0:0:3: [sde] Attached SCSI removable disk
[   15.059893] Adding 914428k swap on /dev/sda6.  Priority:-1 extents:1 across:914428k 
[   15.108703] <30>udev[298]: starting version 167
[   15.177171] lp: driver loaded but no devices found
[   15.180251] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
[   15.184976] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro
[   15.241761] rtusb init --->
[   15.242194] === pAd = f823b000, size = 472668 ===
[   15.242196] <-- RTMPAllocAdapterBlock, Status=0
[   15.245255] usbcore: registered new interface driver rt2870
[   15.431059] type=1400 audit(1307317300.068:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=438 comm="apparmor_parser"
[   15.434598] type=1400 audit(1307317300.072:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=438 comm="apparmor_parser"
[   15.434848] type=1400 audit(1307317300.072:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=438 comm="apparmor_parser"
[   15.743858] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   15.908825] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0xb00, revision 0
[   15.913059] parport_pc 00:07: reported by Plug and Play ACPI
[   15.913099] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
[   16.200144] lp0: using parport0 (interrupt-driven).
[   16.726424] [drm] Initialized drm 1.1.0 20060810
[   17.081577] ppdev: user-space parallel port driver
[   17.181604] [drm] radeon defaulting to kernel modesetting.
[   17.181610] [drm] radeon kernel modesetting enabled.
[   17.181715] radeon 0000:01:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   17.187643] [drm] initializing kernel modesetting (RS480 0x1002:0x5954).
[   17.187678] [drm] register mmio base: 0xFF2F0000
[   17.187680] [drm] register mmio size: 65536
[   17.188940] [drm] Generation 2 PCI interface, using max accessible memory
[   17.188947] radeon 0000:01:05.0: VRAM: 128M 0x0000000038000000 - 0x000000003FFFFFFF (128M used)
[   17.188951] radeon 0000:01:05.0: GTT: 512M 0x0000000040000000 - 0x000000005FFFFFFF
[   17.189191] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   17.189193] [drm] Driver supports precise vblank timestamp query.
[   17.189216] [drm] radeon: irq initialized.
[   17.189393] [drm] Detected VRAM RAM=128M, BAR=256M
[   17.189398] [drm] RAM width 128bits DDR
[   17.191149] [TTM] Zone  kernel: Available graphics memory: 443806 kiB.
[   17.191153] [TTM] Zone highmem: Available graphics memory: 447810 kiB.
[   17.191156] [TTM] Initializing pool allocator.
[   17.191181] [drm] radeon: 128M of VRAM memory ready
[   17.191183] [drm] radeon: 512M of GTT memory ready.
[   17.191251] [drm] GART: num cpu pages 131072, num gpu pages 131072
[   17.198380] [drm] radeon: 4 quad pipes, 1 z pipes initialized.
[   17.204219] radeon 0000:01:05.0: WB enabled
[   17.205087] [drm] Loading R300 Microcode
[   17.231896] [drm] radeon: ring at 0x0000000040001000
[   17.231921] [drm] ring test succeeded in 3 usecs
[   17.232392] [drm] radeon: ib pool ready.
[   17.232501] [drm] ib test succeeded in 0 usecs
[   17.238929] [drm] Radeon Display Connectors
[   17.238933] [drm] Connector 0:
[   17.238935] [drm]   VGA
[   17.238938] [drm]   DDC: 0x68 0x68 0x68 0x68 0x68 0x68 0x68 0x68
[   17.238940] [drm]   Encoders:
[   17.238941] [drm]     CRT1: INTERNAL_DAC2
[   17.238943] [drm] Connector 1:
[   17.238944] [drm]   S-video
[   17.238946] [drm]   Encoders:
[   17.238947] [drm]     TV1: INTERNAL_DAC2
[   17.347835] ATI IXP AC97 controller 0000:00:14.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   17.365513] <-- RTMPAllocTxRxRingMemory, Status=0
[   17.371885] -->RTUSBVenderReset
[   17.372044] <--RTUSBVenderReset
[   17.532957] [drm] fb mappable at 0xC0040000
[   17.532961] [drm] vram apper at 0xC0000000
[   17.532963] [drm] size 5242880
[   17.532964] [drm] fb depth is 24
[   17.532966] [drm]    pitch is 5120
[   17.534350] Console: switching to colour frame buffer device 160x64
[   17.534398] fb0: radeondrmfb frame buffer device
[   17.534401] drm: registered panic notifier
[   17.534411] [drm] Initialized radeon 2.8.0 20080528 for 0000:01:05.0 on minor 0
[   17.730685] 1. Phy Mode = 0
[   17.730690] 2. Phy Mode = 0
[   17.730692] NVM is Efuse and its size =2d[2d0-2fc] 
[   17.794072] RTMPSetPhyMode: channel is out of range, use first channel=1 
[   17.808948] 3. Phy Mode = 0
[   17.824083] MCS Set = 00 00 00 00 00
[   17.868729] <==== rt28xx_init, Status=0
[   17.870455] 0x1300 = 00073200
[   18.196680] ---> RTMPFreeTxRxRingMemory
[   18.196712] <--- RTMPFreeTxRxRingMemory
[   18.387797] type=1400 audit(1307317303.024:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=913 comm="apparmor_parser"
[   18.392572] type=1400 audit(1307317303.032:6): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=913 comm="apparmor_parser"
[   18.455938] type=1400 audit(1307317303.092:7): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=926 comm="apparmor_parser"
[   18.457350] type=1400 audit(1307317303.096:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=926 comm="apparmor_parser"
[   18.457989] type=1400 audit(1307317303.096:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=926 comm="apparmor_parser"
[   18.490828] type=1400 audit(1307317303.128:10): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=927 comm="apparmor_parser"
[   18.511369] type=1400 audit(1307317303.148:11): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=927 comm="apparmor_parser"
[   18.557022] <-- RTMPAllocTxRxRingMemory, Status=0
[   18.570051] -->RTUSBVenderReset
[   18.570172] <--RTUSBVenderReset
[   19.109501] 1. Phy Mode = 0
[   19.109504] 2. Phy Mode = 0
[   19.109507] NVM is Efuse and its size =2d[2d0-2fc] 
[   19.189886] 3. Phy Mode = 0
[   19.207265] MCS Set = 00 00 00 00 00
[   19.255020] <==== rt28xx_init, Status=0
[   19.256765] 0x1300 = 00073200
[   19.270446] eth0: link down
[   19.279749] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   20.919992] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=0
[   22.265063] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=0
[   25.004123] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 316
[   30.096034] wlan0: no IPv6 routers present
[   33.056776] #
[   49.032123] #
[   49.064126] #
[   57.080195] #
[   57.112067] #
[   57.144201] #
[   59.068084] #
[   59.100087] #
[   59.132092] #
[   63.112126] #
[   63.148128] #
[   71.132196] #
[   73.136087] #
[   75.144106] #
[   77.144123] #
[   91.028100] #
[   91.060103] #
[   91.092108] #
[   91.124112] #
[   91.156121] #
[   93.040123] #
[   93.072122] #
[   93.104127] #
[  101.104196] #
[  101.136202] #
[  103.124092] #
[  105.144109] #
[  117.036197] #
[  117.068198] #
[  117.100081] #
[  117.132208] #
[  133.032083] #
[  133.064084] #
[  133.096089] #
[  133.128093] #
[  137.104125] #
[  137.136127] #
[  139.080141] #
[  139.116144] #
[  147.092083] #
[  147.124211] #
[  149.100100] #
[  149.132103] #
[  169.028133] #
[  169.060139] #
[  177.064082] #
[  177.096086] #
[  177.128088] #
[  179.052096] #
[  179.084229] #
[  179.116104] #
[  179.148108] #
[  183.108141] #
[  191.144086] #
[  195.028101] #
[  195.060109] #
[  195.092109] #
[  195.124115] #
[  195.156120] #
[  197.148139] #
[  209.028095] #
[  209.060098] #
[  211.028112] #
[  211.060115] #
[  211.092123] #
[  211.124127] #
[  211.156132] #
[  213.104146] #
[  213.144147] #
[  215.080157] #
[  223.056092] #
[  223.088096] #
[  223.120109] #
[  223.152105] #
[  225.048112] #
[  225.080116] #
[  225.116122] #
[  225.148120] #
[  237.136236] #
[  239.136116] #
[  241.144146] #
[  243.148165] #
[  243.824245] #
[  244.012146] #
[  244.636107] #
[  244.668111] #
[  244.848139] #
[  244.880138] #
[  248.472114] #
[  248.668140] #
[  248.700155] #
[  253.128120] #
[  259.032148] #
[  264.432123] #
[  267.040093] #
[  269.040109] #
[  269.072110] #
[  269.104114] #
[  269.136131] #
[  273.016143] #
[  273.049341] #
[  273.084150] #
[  273.120151] #
[  281.128213] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 316
[  281.132467] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=1)
[  301.380069] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 316
[  301.380395] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=1)
[  315.007067] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 316
[  322.496114] #
[  329.056115] #
[  348.696334] #
[  349.736126] #
[  350.500113] #
[  350.540113] #
[  350.580125] #
[  350.764166] #
[  351.540245] #
[  351.580253] #
[  351.616251] #
[  355.008174] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 140
[  359.140313] #
[  361.892124] #
[  362.936662] #
[  363.976708] #
[  373.072110] #
[  373.108247] #
[  373.144128] #


```

---

### Post by GaryTheCat on 2011-06-05
I'm not sure what any of that means :(

---

### Post by ubudog on 2011-06-05
That is a system log.  One of many.

Anyway, for how long has the desktop been crashing?  Only recently?

---

### Post by GaryTheCat on 2011-06-05
I did a fresh install on Thursday to try to prevent these crashes (after upgrading RAM from 383meg to 1 Gig. There doesn't seem to be a pattern to it.

Does that help?

---

### Post by ubudog on 2011-06-05
No way to reproduce the problem?  Eg. opening a program, etc.

---

### Post by KutWrite on 2011-06-06
Don't know if this is related, but it seems similar:

Ubuntu 11.04 with "studio" desktop
6gB of RAM
Toshiba A665 S2100x w/i7 Intel processor
Fully updated as of today

Locks up (no kbd nor mouse input from ext or int. kbd/mouse
Seems to happen just when on-line
Wired ethernet/cable hi-speed conn.

CTRL-ALT-DEL, Esc., nothing wakes it up.  Have to hold down the power button 'til the laptop shuts off, then restart.

After restart, works for a long time.

May be related to "screen darken" when unused for 15+ min.  
I have prefs set so it won't suspend by itself as long as AC power is plugged in (normal usage for me).  But I do have the screen set to darken if unused for 15+ min.

Anyone?
Anyone?
Buehller?

---

### Post by wildmanne39 on 2011-06-06
> **GaryTheCat said:**
> Pretty much as the title says, I installed Xubuntu 11.04 on an old desktop for my son - it sometimes 'crashes' by that I mean the screen goes black and a load of text pops up.

What logs do I (or a kind more experienced person than I) need to look in? and where are they?

More importantly, if I post the contents of the logs, would someone be able to help me with a diagnosis and a fix?

Thanks in advance

GHi, put this
```
sudo lshw
``` in a terminal and post the results between the code brackets. Also one older computers if they have not been cleaned out recently it is very likely it is getting hot and shutdown or locks up. I clean mine every six months.

---

### Post by GaryTheCat on 2011-06-10
here we go:

```

fraser-desktop            
    description: Desktop Computer
    version: PB34225301
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=1 family=To Be Filled By O.E.M. sku=To Be Filled By O.E.M. uuid=D430DA87-B769-DA11-8000-4E45435F4349
  *-core
       description: Motherboard
       product: MS-7168
       vendor: NEC COMPUTERS INTERNATIONAL
       physical id: 0
       version: 1.0
       slot: To Be Filled By O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 080012
          date: 09/06/2005
          size: 64KiB
          capacity: 448KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification netboot
     *-cpu
          description: CPU
          product: AMD Athlon(tm) 64 Processor 3400+
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 4
          bus info: cpu@0
          version: 15.15.2
          serial: To Be Filled By O.E.M.
          slot: CPU 1
          size: 1GHz
          capacity: 2200MHz
          width: 64 bits
          clock: 200MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt x86-64 3dnowext 3dnow up extd_apicid pni lahf_lm cpufreq
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 128KiB
             capabilities: pipeline-burst internal varies data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: pipeline-burst internal varies unified
     *-memory
          description: System Memory
          physical id: 2d
          slot: System board or motherboard
          size: 1GiB
        *-bank:0
             description: DIMM DDR Synchronous 333 MHz (3.0 ns)
             product: PartNum0
             vendor: Manufacturer0
             physical id: 0
             serial: SerNum0
             slot: DIMM0
             size: 1GiB
             width: 64 bits
             clock: 333MHz (3.0ns)
        *-bank:1
             description: DIMM SDRAM [empty]
             product: PartNum1
             vendor: Manufacturer1
             physical id: 1
             serial: SerNum1
             slot: DIMM1
        *-bank:2
             description: DIMM SDRAM [empty]
             product: PartNum2
             vendor: Manufacturer2
             physical id: 2
             serial: SerNum2
             slot: DIMM2
        *-bank:3
             description: DIMM SDRAM [empty]
             product: PartNum3
             vendor: Manufacturer3
             physical id: 3
             serial: SerNum3
             slot: DIMM3
     *-pci:0
          description: Host bridge
          product: RS480 Host Bridge
          vendor: ATI Technologies Inc
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 10
          width: 32 bits
          clock: 66MHz
        *-pci:0
             description: PCI bridge
             product: RS480 PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci ht normal_decode bus_master cap_list
             resources: ioport:7000(size=4096) memory:ff200000-ff2fffff ioport:bff00000(size=536870912)
           *-display
                description: VGA compatible controller
                product: RS480 [Radeon Xpress 200G Series]
                vendor: ATI Technologies Inc
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: pm vga_controller bus_master cap_list rom
                configuration: driver=radeon latency=64 mingnt=8
                resources: irq:17 memory:c0000000-cfffffff ioport:7800(size=256) memory:ff2f0000-ff2fffff memory:ff2c0000-ff2dffff
        *-ide:0
             description: IDE interface
             product: IXP SB400 Serial ATA Controller
             vendor: ATI Technologies Inc
             physical id: 11
             bus info: pci@0000:00:11.0
             logical name: scsi2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm msi bus_master cap_list rom emulated
             configuration: driver=sata_sil latency=64
             resources: irq:23 ioport:bc00(size=8) ioport:b800(size=4) ioport:b400(size=8) ioport:b000(size=4) ioport:ac00(size=16) memory:ff6ffc00-ff6ffdff memory:ff600000-ff67ffff
           *-disk
                description: ATA Disk
                product: ST3160023AS
                vendor: Seagate
                physical id: 0.0.0
                bus info: scsi@2:0.0.0
                logical name: /dev/sda
                version: 3.00
                serial: 4MT22KWW
                size: 149GiB (160GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=ace22e9e
              *-volume:0
                   description: Windows FAT volume
                   vendor: MSWIN4.1
                   physical id: 1
                   bus info: scsi@2:0.0.0,1
                   logical name: /dev/sda1
                   version: FAT32
                   serial: 18bf-ec79
                   size: 7993MiB
                   capacity: 7993MiB
                   capabilities: primary hidden fat initialized
                   configuration: FATs=2 filesystem=fat label=BACKUP
              *-volume:1
                   description: Windows NTFS volume
                   physical id: 2
                   bus info: scsi@2:0.0.0,2
                   logical name: /dev/sda2
                   version: 3.1
                   serial: c8f5d89b-2102-734b-aa78-6abb252a7fa8
                   size: 29GiB
                   capacity: 29GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2005-12-11 17:19:15 filesystem=ntfs label=HDD state=clean
              *-volume:2
                   description: Windows NTFS volume
                   physical id: 3
                   bus info: scsi@2:0.0.0,3
                   logical name: /dev/sda3
                   version: 3.1
                   serial: 585a1919-cede-9942-9aae-912112e2a591
                   size: 83GiB
                   capacity: 83GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2005-12-12 01:03:12 filesystem=ntfs label=DATA state=clean
              *-volume:3
                   description: Extended partition
                   physical id: 4
                   bus info: scsi@2:0.0.0,4
                   logical name: /dev/sda4
                   size: 27GiB
                   capacity: 27GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux filesystem partition
                      physical id: 5
                      logical name: /dev/sda5
                      logical name: /
                      capacity: 26GiB
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered state=mounted
                 *-logicalvolume:1
                      description: Linux swap / Solaris partition
                      physical id: 6
                      logical name: /dev/sda6
                      capacity: 893MiB
                      capabilities: nofs
        *-ide:1
             description: IDE interface
             product: IXP SB400 Serial ATA Controller
             vendor: ATI Technologies Inc
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm msi bus_master cap_list rom
             configuration: driver=sata_sil latency=64
             resources: irq:22 ioport:a800(size=8) ioport:a400(size=4) ioport:a000(size=8) ioport:9c00(size=4) ioport:9800(size=16) memory:ff6ff800-ff6ff9ff memory:ff580000-ff5fffff
        *-usb:0
             description: USB Controller
             product: IXP SB400 USB Host Controller
             vendor: ATI Technologies Inc
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: msi ohci bus_master cap_list
             configuration: driver=ohci_hcd latency=64
             resources: irq:19 memory:ff6fe000-ff6fefff
        *-usb:1
             description: USB Controller
             product: IXP SB400 USB Host Controller
             vendor: ATI Technologies Inc
             physical id: 13.1
             bus info: pci@0000:00:13.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: msi ohci bus_master cap_list
             configuration: driver=ohci_hcd latency=64
             resources: irq:19 memory:ff6fd000-ff6fdfff
        *-usb:2
             description: USB Controller
             product: IXP SB400 USB2 Host Controller
             vendor: ATI Technologies Inc
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm msi ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=64
             resources: irq:19 memory:ff6fc000-ff6fcfff
        *-serial
             description: SMBus
             product: IXP SB400 SMBus Controller
             vendor: ATI Technologies Inc
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 10
             width: 32 bits
             clock: 66MHz
             capabilities: ht cap_list
             configuration: driver=piix4_smbus latency=0
             resources: irq:0 ioport:b00(size=16) memory:40000000-400003ff
        *-ide:2
             description: IDE interface
             product: IXP SB400 IDE Controller
             vendor: ATI Technologies Inc
             physical id: 14.1
             bus info: pci@0000:00:14.1
             logical name: scsi1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide msi bus_master cap_list emulated
             configuration: driver=pata_atiixp latency=64
             resources: irq:16 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ff00(size=16)
           *-cdrom
                description: DVD writer
                product: DVD_RW ND-3550A
                vendor: _NEC
                physical id: 0.0.0
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.52
                serial: [
                capabilities: removable audio cd-r cd-rw dvd dvd-r
                configuration: ansiversion=5 status=nodisc
        *-isa
             description: ISA bridge
             product: IXP SB400 PCI-ISA Bridge
             vendor: ATI Technologies Inc
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:1
             description: PCI bridge
             product: IXP SB400 PCI-PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci subtractive_decode bus_master
             resources: ioport:8000(size=4096) memory:ff300000-ff3fffff
           *-communication
                description: Modem
                product: SmartLink SmartPCI562 56K Modem
                vendor: Smart Link Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 04
                width: 32 bits
                clock: 33MHz
                capabilities: pm generic bus_master cap_list
                configuration: driver=serial latency=64 maxlatency=62 mingnt=1
                resources: irq:20 memory:ff3ff000-ff3fffff ioport:8800(size=256)
           *-network
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 3
                bus info: pci@0000:02:03.0
                logical name: eth0
                version: 10
                serial: 00:13:d3:b6:87:61
                size: 10Mbit/s
                capacity: 100Mbit/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10Mbit/s
                resources: irq:20 ioport:8400(size=256) memory:ff3fec00-ff3fecff memory:ff3e0000-ff3effff
           *-firewire
                description: FireWire (IEEE 1394)
                product: VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller
                vendor: VIA Technologies, Inc.
                physical id: 4
                bus info: pci@0000:02:04.0
                version: 80
                width: 32 bits
                clock: 33MHz
                capabilities: pm ohci bus_master cap_list
                configuration: driver=firewire_ohci latency=64 maxlatency=32
                resources: irq:9 memory:ff3fe000-ff3fe7ff ioport:8c00(size=128)
        *-multimedia
             description: Multimedia audio controller
             product: IXP SB400 AC'97 Audio Controller
             vendor: ATI Technologies Inc
             physical id: 14.5
             bus info: pci@0000:00:14.5
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: msi bus_master cap_list
             configuration: driver=ATI IXP AC97 controller latency=64 mingnt=2
             resources: irq:17 memory:ff6ff400-ff6ff4ff
     *-pci:1
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp
          resources: irq:0
     *-scsi
          physical id: 1
          bus info: usb@2:4
          logical name: scsi6
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk:0
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@6:0.0.0
             logical name: /dev/sdb
        *-disk:1
             description: SCSI Disk
             physical id: 0.0.1
             bus info: scsi@6:0.0.1
             logical name: /dev/sdc
        *-disk:2
             description: SCSI Disk
             physical id: 0.0.2
             bus info: scsi@6:0.0.2
             logical name: /dev/sdd
        *-disk:3
             description: SCSI Disk
             physical id: 0.0.3
             bus info: scsi@6:0.0.3
             logical name: /dev/sde
  *-network
       description: Wireless interface
       physical id: 1
       bus info: firewire@1
       logical name: wlan0
       serial: 00:26:18:c5:12:fb
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=usb ip=192.168.1.13 multicast=yes wireless=Ralink STA


```

Thanks in advance

---

### Post by wildmanne39 on 2011-06-10
> **GaryTheCat said:**
> here we go:

```

fraser-desktop            
    description: Desktop Computer
    version: PB34225301
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=1 family=To Be Filled By O.E.M. sku=To Be Filled By O.E.M. uuid=D430DA87-B769-DA11-8000-4E45435F4349
  *-core
       description: Motherboard
       product: MS-7168
       vendor: NEC COMPUTERS INTERNATIONAL
       physical id: 0
       version: 1.0
       slot: To Be Filled By O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 080012
          date: 09/06/2005
          size: 64KiB
          capacity: 448KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification netboot
     *-cpu
          description: CPU
          product: AMD Athlon(tm) 64 Processor 3400+
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 4
          bus info: cpu@0
          version: 15.15.2
          serial: To Be Filled By O.E.M.
          slot: CPU 1
          size: 1GHz
          capacity: 2200MHz
          width: 64 bits
          clock: 200MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt x86-64 3dnowext 3dnow up extd_apicid pni lahf_lm cpufreq
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 128KiB
             capabilities: pipeline-burst internal varies data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: pipeline-burst internal varies unified
     *-memory
          description: System Memory
          physical id: 2d
          slot: System board or motherboard
          size: 1GiB
        *-bank:0
             description: DIMM DDR Synchronous 333 MHz (3.0 ns)
             product: PartNum0
             vendor: Manufacturer0
             physical id: 0
             serial: SerNum0
             slot: DIMM0
             size: 1GiB
             width: 64 bits
             clock: 333MHz (3.0ns)
        *-bank:1
             description: DIMM SDRAM [empty]
             product: PartNum1
             vendor: Manufacturer1
             physical id: 1
             serial: SerNum1
             slot: DIMM1
        *-bank:2
             description: DIMM SDRAM [empty]
             product: PartNum2
             vendor: Manufacturer2
             physical id: 2
             serial: SerNum2
             slot: DIMM2
        *-bank:3
             description: DIMM SDRAM [empty]
             product: PartNum3
             vendor: Manufacturer3
             physical id: 3
             serial: SerNum3
             slot: DIMM3
     *-pci:0
          description: Host bridge
          product: RS480 Host Bridge
          vendor: ATI Technologies Inc
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 10
          width: 32 bits
          clock: 66MHz
        *-pci:0
             description: PCI bridge
             product: RS480 PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci ht normal_decode bus_master cap_list
             resources: ioport:7000(size=4096) memory:ff200000-ff2fffff ioport:bff00000(size=536870912)
           *-display
                description: VGA compatible controller
                product: RS480 [Radeon Xpress 200G Series]
                vendor: ATI Technologies Inc
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: pm vga_controller bus_master cap_list rom
                configuration: driver=radeon latency=64 mingnt=8
                resources: irq:17 memory:c0000000-cfffffff ioport:7800(size=256) memory:ff2f0000-ff2fffff memory:ff2c0000-ff2dffff
        *-ide:0
             description: IDE interface
             product: IXP SB400 Serial ATA Controller
             vendor: ATI Technologies Inc
             physical id: 11
             bus info: pci@0000:00:11.0
             logical name: scsi2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm msi bus_master cap_list rom emulated
             configuration: driver=sata_sil latency=64
             resources: irq:23 ioport:bc00(size=8) ioport:b800(size=4) ioport:b400(size=8) ioport:b000(size=4) ioport:ac00(size=16) memory:ff6ffc00-ff6ffdff memory:ff600000-ff67ffff
           *-disk
                description: ATA Disk
                product: ST3160023AS
                vendor: Seagate
                physical id: 0.0.0
                bus info: scsi@2:0.0.0
                logical name: /dev/sda
                version: 3.00
                serial: 4MT22KWW
                size: 149GiB (160GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=ace22e9e
              *-volume:0
                   description: Windows FAT volume
                   vendor: MSWIN4.1
                   physical id: 1
                   bus info: scsi@2:0.0.0,1
                   logical name: /dev/sda1
                   version: FAT32
                   serial: 18bf-ec79
                   size: 7993MiB
                   capacity: 7993MiB
                   capabilities: primary hidden fat initialized
                   configuration: FATs=2 filesystem=fat label=BACKUP
              *-volume:1
                   description: Windows NTFS volume
                   physical id: 2
                   bus info: scsi@2:0.0.0,2
                   logical name: /dev/sda2
                   version: 3.1
                   serial: c8f5d89b-2102-734b-aa78-6abb252a7fa8
                   size: 29GiB
                   capacity: 29GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2005-12-11 17:19:15 filesystem=ntfs label=HDD state=clean
              *-volume:2
                   description: Windows NTFS volume
                   physical id: 3
                   bus info: scsi@2:0.0.0,3
                   logical name: /dev/sda3
                   version: 3.1
                   serial: 585a1919-cede-9942-9aae-912112e2a591
                   size: 83GiB
                   capacity: 83GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2005-12-12 01:03:12 filesystem=ntfs label=DATA state=clean
              *-volume:3
                   description: Extended partition
                   physical id: 4
                   bus info: scsi@2:0.0.0,4
                   logical name: /dev/sda4
                   size: 27GiB
                   capacity: 27GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux filesystem partition
                      physical id: 5
                      logical name: /dev/sda5
                      logical name: /
                      capacity: 26GiB
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered state=mounted
                 *-logicalvolume:1
                      description: Linux swap / Solaris partition
                      physical id: 6
                      logical name: /dev/sda6
                      capacity: 893MiB
                      capabilities: nofs
        *-ide:1
             description: IDE interface
             product: IXP SB400 Serial ATA Controller
             vendor: ATI Technologies Inc
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm msi bus_master cap_list rom
             configuration: driver=sata_sil latency=64
             resources: irq:22 ioport:a800(size=8) ioport:a400(size=4) ioport:a000(size=8) ioport:9c00(size=4) ioport:9800(size=16) memory:ff6ff800-ff6ff9ff memory:ff580000-ff5fffff
        *-usb:0
             description: USB Controller
             product: IXP SB400 USB Host Controller
             vendor: ATI Technologies Inc
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: msi ohci bus_master cap_list
             configuration: driver=ohci_hcd latency=64
             resources: irq:19 memory:ff6fe000-ff6fefff
        *-usb:1
             description: USB Controller
             product: IXP SB400 USB Host Controller
             vendor: ATI Technologies Inc
             physical id: 13.1
             bus info: pci@0000:00:13.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: msi ohci bus_master cap_list
             configuration: driver=ohci_hcd latency=64
             resources: irq:19 memory:ff6fd000-ff6fdfff
        *-usb:2
             description: USB Controller
             product: IXP SB400 USB2 Host Controller
             vendor: ATI Technologies Inc
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm msi ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=64
             resources: irq:19 memory:ff6fc000-ff6fcfff
        *-serial
             description: SMBus
             product: IXP SB400 SMBus Controller
             vendor: ATI Technologies Inc
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 10
             width: 32 bits
             clock: 66MHz
             capabilities: ht cap_list
             configuration: driver=piix4_smbus latency=0
             resources: irq:0 ioport:b00(size=16) memory:40000000-400003ff
        *-ide:2
             description: IDE interface
             product: IXP SB400 IDE Controller
             vendor: ATI Technologies Inc
             physical id: 14.1
             bus info: pci@0000:00:14.1
             logical name: scsi1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide msi bus_master cap_list emulated
             configuration: driver=pata_atiixp latency=64
             resources: irq:16 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ff00(size=16)
           *-cdrom
                description: DVD writer
                product: DVD_RW ND-3550A
                vendor: _NEC
                physical id: 0.0.0
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.52
                serial: [
                capabilities: removable audio cd-r cd-rw dvd dvd-r
                configuration: ansiversion=5 status=nodisc
        *-isa
             description: ISA bridge
             product: IXP SB400 PCI-ISA Bridge
             vendor: ATI Technologies Inc
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:1
             description: PCI bridge
             product: IXP SB400 PCI-PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci subtractive_decode bus_master
             resources: ioport:8000(size=4096) memory:ff300000-ff3fffff
           *-communication
                description: Modem
                product: SmartLink SmartPCI562 56K Modem
                vendor: Smart Link Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 04
                width: 32 bits
                clock: 33MHz
                capabilities: pm generic bus_master cap_list
                configuration: driver=serial latency=64 maxlatency=62 mingnt=1
                resources: irq:20 memory:ff3ff000-ff3fffff ioport:8800(size=256)
           *-network
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 3
                bus info: pci@0000:02:03.0
                logical name: eth0
                version: 10
                serial: 00:13:d3:b6:87:61
                size: 10Mbit/s
                capacity: 100Mbit/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10Mbit/s
                resources: irq:20 ioport:8400(size=256) memory:ff3fec00-ff3fecff memory:ff3e0000-ff3effff
           *-firewire
                description: FireWire (IEEE 1394)
                product: VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller
                vendor: VIA Technologies, Inc.
                physical id: 4
                bus info: pci@0000:02:04.0
                version: 80
                width: 32 bits
                clock: 33MHz
                capabilities: pm ohci bus_master cap_list
                configuration: driver=firewire_ohci latency=64 maxlatency=32
                resources: irq:9 memory:ff3fe000-ff3fe7ff ioport:8c00(size=128)
        *-multimedia
             description: Multimedia audio controller
             product: IXP SB400 AC'97 Audio Controller
             vendor: ATI Technologies Inc
             physical id: 14.5
             bus info: pci@0000:00:14.5
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: msi bus_master cap_list
             configuration: driver=ATI IXP AC97 controller latency=64 mingnt=2
             resources: irq:17 memory:ff6ff400-ff6ff4ff
     *-pci:1
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp
          resources: irq:0
     *-scsi
          physical id: 1
          bus info: usb@2:4
          logical name: scsi6
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk:0
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@6:0.0.0
             logical name: /dev/sdb
        *-disk:1
             description: SCSI Disk
             physical id: 0.0.1
             bus info: scsi@6:0.0.1
             logical name: /dev/sdc
        *-disk:2
             description: SCSI Disk
             physical id: 0.0.2
             bus info: scsi@6:0.0.2
             logical name: /dev/sdd
        *-disk:3
             description: SCSI Disk
             physical id: 0.0.3
             bus info: scsi@6:0.0.3
             logical name: /dev/sde
  *-network
       description: Wireless interface
       physical id: 1
       bus info: firewire@1
       logical name: wlan0
       serial: 00:26:18:c5:12:fb
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=usb ip=192.168.1.13 multicast=yes wireless=Ralink STA


```

Thanks in advance
Hi, there are a few things I can suggest,when you log in are you seeing the unity desktop? you will know it was the launcher bar on the left side of the screen.If so do this.
1. Log out and click on user name and choose ubuntu classic with no effects see if that helps.
2. Look in additional drivers and see if there is a driver for your video card and install it.
3. Clean your computer out, being older it is probably full of dirt and that will make it run hotter and have lock ups.

---

### Post by GaryTheCat on 2011-06-10
Thanks for that - there's no unity problem as it's xubuntu 11.04, I've tried the additional drivers to no avail, I'll get a little can of compressed air out and give it a good dusting.

---

### Post by ubudog on 2011-06-10
Do you have any desktop effects enabled?  Given the computer is old, this may cause it to crash.

---

### Post by Rifester on 2011-06-10
There are several bugs in Launchpad regarding random crashes (with text, then a return to the  the login screen, usually several times a day) in 11.04.   May people are having this occur when opening a browser, switching tabs in a browser, or save an application.  You may want to see if your issue resembles on of these (then mark it affecting you as well):

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/774978](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/774978)

[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/778490](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/778490)

[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/760695](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/760695)

---

