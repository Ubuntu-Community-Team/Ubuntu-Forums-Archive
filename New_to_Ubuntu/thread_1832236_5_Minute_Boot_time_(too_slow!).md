---
title: "5 Minute Boot time (too slow!)"
date: 2011-08-24
forum: New to Ubuntu
---

### Post by halobium on 2011-08-24
**Problem:** Ubuntu takes about 5 min to boot. If suspended, crashes. If put to sleep takes about 3-5 minutes to resume. 

**Solutions tried:** tried using Xubuntu instead, same problem. Changed BIOS settings: disabled legacy USB (something suggested as a possible problem). 

**Hardware Specs:**
Processor -- 
Intel® AtomTM processor N450 (1.66GHz, 667MHz FSB, 512KB L2 Cache)
Memory -- 
Standard Memory: 1 x 1GB DDR2 (800MHz), Maximum Memory: 2GB DDR2 Expansion, Modules: 2GB
Hard Disk Drive -- 
250GB (5400 RPM); Serial-ATA hard disk drive
Graphics Controller -- 
Mobile Intel® GMA 3150 Express Chipset with up to 250MB of dynamically allocated shared graphics memory
BIOS -- 
TSETUP, ACPI, PnP, VESA, SM BIOS, PCI BIOS Support

Any help would be welcome. I can live with a five minute boot if the wake settings for sleep/suspend or hibernate are trimmed down. I'm fairly certain it is BIOS settings that need to change, but I really don't know how to do this (I'm also a first time Ubuntu user).

---

### Post by bhaverkamp on 2011-08-24
Attach some logs. Start with /var/log/messages & dmesg

---

### Post by halobium on 2011-08-24
Here it is: (One change, I currently have xubuntu installed. I wanted Ubuntu but am having too much trouble with the install usb. I'll stick with xubuntu)

```
[1] 1582
bash: /var/log/messages: No such file or directory
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.38-11-generic (buildd@rothera) (gcc  version 4.5.2 (Ubuntu/Linaro 4.5.2-8ubuntu4) ) #48-Ubuntu SMP Fri Jul 29  19:05:14 UTC 2011 (Ubuntu 2.6.38-11.48-generic 2.6.38.:cool:
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009dc00 (usable)
[    0.000000]  BIOS-e820: 000000000009dc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000dc000 - 00000000000e0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003f5d0000 (usable)
[    0.000000]  BIOS-e820: 000000003f5d0000 - 000000003f5e0000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003f5e0000 - 000000003f5e3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003f5e3000 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] Notice: NX (Execute Disable) protection cannot be enabled in hardware: non-PAE kernel!
[    0.000000] NX (Execute Disable) protection: approximated by x86 segment limits
[    0.000000] DMI present.
[    0.000000] DMI: TOSHIBA TOSHIBA NB300/NPVAA, BIOS V1.40 03/16/2010
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x3f5d0 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-DFFFF uncachable
[    0.000000]   E0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask 0C0000000 write-back
[    0.000000]   1 base 03F600000 mask 0FFE00000 uncachable
[    0.000000]   2 base 03F800000 mask 0FF800000 uncachable
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] found SMP MP-table at [c00f7da0] f7da0
[    0.000000] initial memory mapped : 0 - 01c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 1bfb000-1c00000
[    0.000000] RAMDISK: 36768000 - 373ac000
[    0.000000] ACPI: RSDP 000f7d00 00024 (v02 TOSCPL)
[    0.000000] ACPI: XSDT 3f5d4f25 00074 (v01 TOSCPL TOSCPL00 06040000  LTP 00000000)
[    0.000000] ACPI: FACP 3f5dfc60 000F4 (v03 TOSCPL TOSCPL00 06040000 PTL  00000002)
[    0.000000] ACPI: DSDT 3f5d60bb 09B31 (v01 TOSCPL TOSCPL00 06040000 MSFT 03000000)
[    0.000000] ACPI: FACS 3f5e2fc0 00040
[    0.000000] ACPI: TCPA 3f5dfd54 00032 (v01 Phoeni  x       06040000  TL  00000000)
[    0.000000] ACPI: HPET 3f5dfd86 00038 (v01 DELL   M09      06040000 LOHR 0000005A)
[    0.000000] ACPI: MCFG 3f5dfdbe 0003C (v01 INTEL  CRESTLNE 06040000 LOHR 0000005A)
[    0.000000] ACPI: SLIC 3f5dfdfa 00176 (v01 TOSCPL TOSCPL00 06040000 LOHR 00000000)
[    0.000000] ACPI: APIC 3f5dff70 00068 (v01 TOSCPL TOSCPL00 06040000  LTP 00000000)
[    0.000000] ACPI: BOOT 3f5dffd8 00028 (v01 TOSCPL TOSCPL00 06040000  LTP 00000001)
[    0.000000] ACPI: SSDT 3f5d551b 0025F (v01  PmRef  Cpu0Tst 00003000 INTL 20050624)
[    0.000000] ACPI: SSDT 3f5d5475 000A6 (v01  PmRef  Cpu1Tst 00003000 INTL 20050624)
[    0.000000] ACPI: SSDT 3f5d4f99 004DC (v02  PmRef    CpuPm 00003000 INTL 20050624)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 125MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0003f5d0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009d
[    0.000000]     0: 0x00000100 -> 0x0003f5d0
[    0.000000] On node 0 totalpages: 259421
[    0.000000] free_area_init_node: node 0, pgdat c1784180, node_mem_map f5f78200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3949 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 252 pages used for memmap
[    0.000000]   HighMem zone: 31958 pages, LIFO batch:7
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000dc000
[    0.000000] PM: Registered nosave memory: 00000000000dc000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 00000000000e4000
[    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 40000000:a0000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 13 pages/cpu @f5800000 s28800 r0 d24448 u2097152
[    0.000000] pcpu-alloc: s28800 r0 d24448 u2097152 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 1 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 257393
[    0.000000] Kernel command line:  BOOT_IMAGE=/boot/vmlinuz-2.6.38-11-generic  root=UUID=00774852-e3bb-4b20-b2e1-186697ac29f3 ro quiet splash  vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] allocated 5190400 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0003f5d0)
[    0.000000] Memory: 1001628k/1038144k available (5190k kernel code, 36056k reserved, 2538k data, 700k init, 128840k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc178d000 - 0xc183c000   ( 700 kB)
[    0.000000]       .data : 0xc1511ba1 - 0xc178c500   (2538 kB)
[    0.000000]       .text : 0xc1000000 - 0xc1511ba1   (5190 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU-based detection of stalled CPUs is disabled.
[    0.000000] NR_IRQS:2304 nr_irqs:512 16
[    0.000000] CPU 0 irqstacks, hard=f5408000 soft=f540a000
[    0.000000] Extended CMOS year: 2000
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1662.472 MHz processor.
[    0.004004] Calibrating delay loop (skipped), value calculated using timer frequency.. 3324.94 BogoMIPS (lpj=664988:cool:
[    0.004016] pid_max: default: 32768 minimum: 301
[    0.004068] Security Framework initialized
[    0.004102] AppArmor: AppArmor initialized
[    0.004106] Yama: becoming mindful.
[    0.004230] Mount-cache hash table entries: 512
[    0.004488] Initializing cgroup subsys ns
[    0.004496] ns_cgroup deprecated: consider using the 'clone_children' flag without the ns_cgroup.
[    0.004503] Initializing cgroup subsys cpuacct
[    0.004515] Initializing cgroup subsys memory
[    0.004533] Initializing cgroup subsys devices
[    0.004539] Initializing cgroup subsys freezer
[    0.004545] Initializing cgroup subsys net_cls
[    0.004550] Initializing cgroup subsys blkio
[    0.008065] CPU: Physical Processor ID: 0
[    0.008070] CPU: Processor Core ID: 0
[    0.008076] mce: CPU supports 5 MCE banks
[    0.008090] CPU0: Thermal monitoring handled by SMI
[    0.008098] using mwait in idle threads.
[    0.012332] ACPI: Core revision 20110112
[    0.024027] ftrace: allocating 23649 entries in 47 pages
[    0.028098] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.028454] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.071760] CPU0: Intel(R) Atom(TM) CPU N450   @ 1.66GHz stepping 0a
[    0.072003] Performance Events: PEBS fmt0+, Atom events, Intel PMU driver.
[    0.072003] ... version:                3
[    0.072003] ... bit width:              40
[    0.072003] ... generic registers:      2
[    0.072003] ... value mask:             000000ffffffffff
[    0.072003] ... max period:             000000007fffffff
[    0.072003] ... fixed-purpose events:   3
[    0.072003] ... event mask:             0000000700000003
[    0.072003] CPU 1 irqstacks, hard=f54ca000 soft=f54cc000
[    0.072003] Booting Node   0, Processors  #1 Ok.
[    0.008000] Initializing CPU#1
[    0.008000] CPU0: Thermal monitoring enabled (TM1)
[    0.160042] Brought up 2 CPUs
[    0.160051] Total of 2 processors activated (6649.95 BogoMIPS).
[    0.160557] devtmpfs: initialized
[    0.164361] print_constraints: dummy: 
[    0.164399] Time: 21:58:23  Date: 08/24/11
[    0.164487] NET: Registered protocol family 16
[    0.164578] Trying to unpack rootfs image as initramfs...
[    0.164850] EISA bus registered
[    0.164875] ACPI: bus type pci registered
[    0.165080] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.165091] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    0.165098] PCI: Using MMCONFIG for extended config space
[    0.165104] PCI: Using configuration type 1 for base access
[    0.168335] bio: create slab <bio-0> at 0
[    0.173005] ACPI: EC: Look up EC in DSDT
[    0.186610] ACPI: SSDT 3f5d5de4 00203 (v02  PmRef  Cpu0Ist 00003000 INTL 20050624)
[    0.187698] ACPI: Dynamic OEM Table Load:
[    0.187709] ACPI: SSDT   (null) 00203 (v02  PmRef  Cpu0Ist 00003000 INTL 20050624)
[    0.188269] ACPI: SSDT 3f5d577a 005E5 (v02  PmRef  Cpu0Cst 00003001 INTL 20050624)
[    0.189301] ACPI: Dynamic OEM Table Load:
[    0.189313] ACPI: SSDT   (null) 005E5 (v02  PmRef  Cpu0Cst 00003001 INTL 20050624)
[    0.190209] ACPI: SSDT 3f5d5fe7 000D4 (v02  PmRef  Cpu1Ist 00003000 INTL 20050624)
[    0.191283] ACPI: Dynamic OEM Table Load:
[    0.191295] ACPI: SSDT   (null) 000D4 (v02  PmRef  Cpu1Ist 00003000 INTL 20050624)
[    0.191646] ACPI: SSDT 3f5d5d5f 00085 (v02  PmRef  Cpu1Cst 00003000 INTL 20050624)
[    0.192718] ACPI: Dynamic OEM Table Load:
[    0.192729] ACPI: SSDT   (null) 00085 (v02  PmRef  Cpu1Cst 00003000 INTL 20050624)
[    0.194720] ACPI: Interpreter enabled
[    0.194720] ACPI: (supports S0 S3 S4 S5)
[    0.194720] ACPI: Using IOAPIC for interrupt routing
[    0.248632] ACPI: EC: GPE = 0x19, I/O: command/status = 0x66, data = 0x62
[    0.249117] ACPI: No dock devices found.
[    0.249124] HEST: Table not found.
[    0.249134] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.251539] ACPI Error: [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS (20110112/dsfield-143)
[    0.251562] ACPI Error: Method parse/execution failed  [\_SB_.PCI0._OSC] (Node f54252a0), AE_ALREADY_EXISTS  (20110112/psparse-536)
[    0.251589] ACPI: Marking method _OSC as Serialized because of AE_ALREADY_EXISTS error
[    0.251612] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-3f])
[    0.256049] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    0.256060] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.256071] pci_root PNP0A08:00: host bridge window [mem 0x000d0000-0x000d3fff]
[    0.256080] pci_root PNP0A08:00: host bridge window [mem 0x000d4000-0x000d7fff]
[    0.256089] pci_root PNP0A08:00: host bridge window [mem 0x000d8000-0x000dbfff]
[    0.256098] pci_root PNP0A08:00: host bridge window [mem 0x000e0000-0x000e3fff]
[    0.256109] pci_root PNP0A08:00: host bridge window [mem 0x40000000-0xf7ffffff]
[    0.256118] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xfdff]
[    0.256154] pci 0000:00:00.0: [8086:a010] type 0 class 0x000600
[    0.256230] pci 0000:00:02.0: [8086:a011] type 0 class 0x000300
[    0.256252] pci 0000:00:02.0: reg 10: [mem 0xf0200000-0xf027ffff]
[    0.256266] pci 0000:00:02.0: reg 14: [io  0x18d0-0x18d7]
[    0.256281] pci 0000:00:02.0: reg 18: [mem 0xd0000000-0xdfffffff pref]
[    0.256295] pci 0000:00:02.0: reg 1c: [mem 0xf0000000-0xf00fffff]
[    0.256355] pci 0000:00:02.1: [8086:a012] type 0 class 0x000380
[    0.256374] pci 0000:00:02.1: reg 10: [mem 0xf0280000-0xf02fffff]
[    0.256500] pci 0000:00:1b.0: [8086:27d8] type 0 class 0x000403
[    0.256531] pci 0000:00:1b.0: reg 10: [mem 0xf0500000-0xf0503fff 64bit]
[    0.256624] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.256635] pci 0000:00:1b.0: PME# disabled
[    0.256677] pci 0000:00:1c.0: [8086:27d0] type 1 class 0x000604
[    0.256778] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.256789] pci 0000:00:1c.0: PME# disabled
[    0.256831] pci 0000:00:1c.1: [8086:27d2] type 1 class 0x000604
[    0.256926] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.256937] pci 0000:00:1c.1: PME# disabled
[    0.256979] pci 0000:00:1c.2: [8086:27d4] type 1 class 0x000604
[    0.257074] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.257084] pci 0000:00:1c.2: PME# disabled
[    0.257130] pci 0000:00:1d.0: [8086:27c8] type 0 class 0x000c03
[    0.257197] pci 0000:00:1d.0: reg 20: [io  0x1820-0x183f]
[    0.257253] pci 0000:00:1d.1: [8086:27c9] type 0 class 0x000c03
[    0.257320] pci 0000:00:1d.1: reg 20: [io  0x1840-0x185f]
[    0.257377] pci 0000:00:1d.2: [8086:27ca] type 0 class 0x000c03
[    0.257449] pci 0000:00:1d.2: reg 20: [io  0x1860-0x187f]
[    0.257505] pci 0000:00:1d.3: [8086:27cb] type 0 class 0x000c03
[    0.257572] pci 0000:00:1d.3: reg 20: [io  0x1880-0x189f]
[    0.257641] pci 0000:00:1d.7: [8086:27cc] type 0 class 0x000c03
[    0.257676] pci 0000:00:1d.7: reg 10: [mem 0xf0504000-0xf05043ff]
[    0.257785] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.257796] pci 0000:00:1d.7: PME# disabled
[    0.257837] pci 0000:00:1e.0: [8086:2448] type 1 class 0x000604
[    0.257937] pci 0000:00:1f.0: [8086:27bc] type 0 class 0x000601
[    0.258051] pci 0000:00:1f.0: [Firmware Bug]: TigerPoint LPC.BM_STS cleared
[    0.258113] pci 0000:00:1f.2: [8086:27c1] type 0 class 0x000106
[    0.258146] pci 0000:00:1f.2: reg 10: [io  0x18e8-0x18ef]
[    0.258166] pci 0000:00:1f.2: reg 14: [io  0x18dc-0x18df]
[    0.258185] pci 0000:00:1f.2: reg 18: [io  0x18e0-0x18e7]
[    0.258205] pci 0000:00:1f.2: reg 1c: [io  0x18d8-0x18db]
[    0.258224] pci 0000:00:1f.2: reg 20: [io  0x18c0-0x18cf]
[    0.258242] pci 0000:00:1f.2: reg 24: [mem 0xf0504400-0xf05047ff]
[    0.258292] pci 0000:00:1f.2: PME# supported from D3hot
[    0.258302] pci 0000:00:1f.2: PME# disabled
[    0.258334] pci 0000:00:1f.3: [8086:27da] type 0 class 0x000c05
[    0.258412] pci 0000:00:1f.3: reg 20: [io  0x18a0-0x18bf]
[    0.258532] pci 0000:00:1c.0: PCI bridge to [bus 05-05]
[    0.258543] pci 0000:00:1c.0:   bridge window [io  0x0000-0x0000] (disabled)
[    0.258555] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.258571] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.258677] pci 0000:07:00.0: [168c:002b] type 0 class 0x000280
[    0.258727] pci 0000:07:00.0: reg 10: [mem 0xf0100000-0xf010ffff 64bit]
[    0.258869] pci 0000:07:00.0: supports D1
[    0.258877] pci 0000:07:00.0: PME# supported from D0 D1 D3hot
[    0.258890] pci 0000:07:00.0: PME# disabled
[    0.264087] pci 0000:00:1c.1: PCI bridge to [bus 07-07]
[    0.264102] pci 0000:00:1c.1:   bridge window [io  0xf000-0x0000] (disabled)
[    0.264117] pci 0000:00:1c.1:   bridge window [mem 0xf0100000-0xf01fffff]
[    0.264134] pci 0000:00:1c.1:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.264286] pci 0000:09:00.0: [10ec:8136] type 0 class 0x000200
[    0.264362] pci 0000:09:00.0: reg 10: [io  0x2000-0x20ff]
[    0.264479] pci 0000:09:00.0: reg 18: [mem 0xf0520000-0xf0520fff 64bit pref]
[    0.264557] pci 0000:09:00.0: reg 20: [mem 0xf0510000-0xf051ffff 64bit pref]
[    0.264610] pci 0000:09:00.0: reg 30: [mem 0x00000000-0x0001ffff pref]
[    0.264776] pci 0000:09:00.0: supports D1 D2
[    0.264785] pci 0000:09:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.264805] pci 0000:09:00.0: PME# disabled
[    0.265008] pci 0000:00:1c.2: PCI bridge to [bus 09-09]
[    0.265022] pci 0000:00:1c.2:   bridge window [io  0x2000-0x2fff]
[    0.265035] pci 0000:00:1c.2:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.265051] pci 0000:00:1c.2:   bridge window [mem 0xf0500000-0xf05fffff 64bit pref]
[    0.265157] pci 0000:00:1e.0: PCI bridge to [bus 11-11] (subtractive decode)
[    0.265170] pci 0000:00:1e.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.265182] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.265196] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.265207] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.265216] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.265226] pci 0000:00:1e.0:   bridge window [mem 0x000d0000-0x000d3fff] (subtractive decode)
[    0.265236] pci 0000:00:1e.0:   bridge window [mem 0x000d4000-0x000d7fff] (subtractive decode)
[    0.265246] pci 0000:00:1e.0:   bridge window [mem 0x000d8000-0x000dbfff] (subtractive decode)
[    0.265256] pci 0000:00:1e.0:   bridge window [mem 0x000e0000-0x000e3fff] (subtractive decode)
[    0.265266] pci 0000:00:1e.0:   bridge window [mem 0x40000000-0xf7ffffff] (subtractive decode)
[    0.265276] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xfdff] (subtractive decode)
[    0.265312] pci_bus 0000:00: on NUMA node 0
[    0.265328] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.265593] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP1._PRT]
[    0.265726] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP2._PRT]
[    0.265873] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP3._PRT]
[    0.266029] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[    0.266472] ACPI Error: [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS (20110112/dsfield-143)
[    0.266495] ACPI Error: Method parse/execution failed  [\_SB_.PCI0._OSC] (Node f54252a0), AE_ALREADY_EXISTS  (20110112/psparse-536)
[    0.266534]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.266759] ACPI Error: [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS (20110112/dsfield-143)
[    0.266782] ACPI Error: Method parse/execution failed  [\_SB_.PCI0._OSC] (Node f54252a0), AE_ALREADY_EXISTS  (20110112/psparse-536)
[    0.280136] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 *7 10 11 12 14 15)
[    0.280313] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.280481] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.280649] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.280840] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.281033] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.281218] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.281400] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.281755] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.281786] vgaarb: loaded
[    0.282436] SCSI subsystem initialized
[    0.282604] libata version 3.00 loaded.
[    0.282754] usbcore: registered new interface driver usbfs
[    0.282802] usbcore: registered new interface driver hub
[    0.282901] usbcore: registered new device driver usb
[    0.283289] wmi: Mapper loaded
[    0.283296] PCI: Using ACPI for IRQ routing
[    0.283305] PCI: pci_cache_line_size set to 64 bytes
[    0.283345] pci 0000:00:1b.0: address space collision: [mem  0xf0500000-0xf0503fff 64bit] conflicts with PCI Bus 0000:09 [mem  0xf0500000-0xf05fffff 64bit pref]
[    0.283389] pci 0000:00:1d.7: address space collision: [mem  0xf0504000-0xf05043ff] conflicts with PCI Bus 0000:09 [mem  0xf0500000-0xf05fffff 64bit pref]
[    0.283418] pci 0000:00:1f.2: address space collision: [mem  0xf0504400-0xf05047ff] conflicts with PCI Bus 0000:09 [mem  0xf0500000-0xf05fffff 64bit pref]
[    0.283506] reserve RAM buffer: 000000000009dc00 - 000000000009ffff 
[    0.283515] reserve RAM buffer: 000000003f5d0000 - 000000003fffffff 
[    0.283817] NetLabel: Initializing
[    0.283824] NetLabel:  domain hash size = 128
[    0.283830] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.283860] NetLabel:  unlabeled traffic allowed by default
[    0.283990] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.284040] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.284056] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.288481] Switching to clocksource hpet
[    0.291374] Switched to NOHz mode on CPU #0
[    0.291501] Switched to NOHz mode on CPU #1
[    0.310309] AppArmor: AppArmor Filesystem Enabled
[    0.310379] pnp: PnP ACPI init
[    0.310436] ACPI: bus type pnp registered
[    0.312734] pnp 00:00: [bus 00-3f]
[    0.312746] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.312755] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.312764] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.312772] pnp 00:00: [mem 0x000c0000-0x000c3fff window]
[    0.312781] pnp 00:00: [mem 0x000c4000-0x000c7fff window]
[    0.312790] pnp 00:00: [mem 0x000c8000-0x000cbfff window]
[    0.312798] pnp 00:00: [mem 0x000cc000-0x000cffff window]
[    0.312807] pnp 00:00: [mem 0x000d0000-0x000d3fff window]
[    0.312815] pnp 00:00: [mem 0x000d4000-0x000d7fff window]
[    0.312824] pnp 00:00: [mem 0x000d8000-0x000dbfff window]
[    0.312832] pnp 00:00: [mem 0x000dc000-0x000dffff window]
[    0.312840] pnp 00:00: [mem 0x000e0000-0x000e3fff window]
[    0.312849] pnp 00:00: [mem 0x000e4000-0x000e7fff window]
[    0.312857] pnp 00:00: [mem 0x000e8000-0x000ebfff window]
[    0.312866] pnp 00:00: [mem 0x000ec000-0x000effff window]
[    0.312874] pnp 00:00: [mem 0x000f0000-0x000fffff window]
[    0.312883] pnp 00:00: [mem 0x40000000-0xf7ffffff window]
[    0.312891] pnp 00:00: [io  0x0d00-0xfdff window]
[    0.312899] pnp 00:00: [mem 0x00000000 window]
[    0.312907] pnp 00:00: [mem 0xfed40000-0xfed44fff window]
[    0.313100] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    0.313489] pnp 00:01: [io  0x0010-0x001f]
[    0.313498] pnp 00:01: [io  0x0024-0x0025]
[    0.313506] pnp 00:01: [io  0x0028-0x0029]
[    0.313513] pnp 00:01: [io  0x002c-0x002d]
[    0.313521] pnp 00:01: [io  0x0030-0x0031]
[    0.313528] pnp 00:01: [io  0x0034-0x0035]
[    0.313535] pnp 00:01: [io  0x0038-0x0039]
[    0.313542] pnp 00:01: [io  0x003c-0x003d]
[    0.313550] pnp 00:01: [io  0x0068]
[    0.313556] pnp 00:01: [io  0x006c]
[    0.313563] pnp 00:01: [io  0x0072-0x0077]
[    0.313570] pnp 00:01: [io  0x0080]
[    0.313577] pnp 00:01: [io  0x0090-0x009f]
[    0.313585] pnp 00:01: [io  0x00a4-0x00a5]
[    0.313592] pnp 00:01: [io  0x00a8-0x00a9]
[    0.313599] pnp 00:01: [io  0x00ac-0x00ad]
[    0.313606] pnp 00:01: [io  0x00b0-0x00b5]
[    0.313613] pnp 00:01: [io  0x00b8-0x00b9]
[    0.313620] pnp 00:01: [io  0x00bc-0x00bd]
[    0.313634] pnp 00:01: [io  0x0800-0x080f]
[    0.313642] pnp 00:01: [io  0x1000-0x107f]
[    0.313649] pnp 00:01: [io  0x1180-0x11bf]
[    0.313656] pnp 00:01: [io  0x002e-0x002f]
[    0.313664] pnp 00:01: [io  0x04d0-0x04d1]
[    0.313671] pnp 00:01: [io  0xfe00]
[    0.313678] pnp 00:01: [io  0x164e-0x174c]
[    0.313686] pnp 00:01: [mem 0xe0000000-0xefffffff]
[    0.313694] pnp 00:01: [mem 0xfed14000-0xfed17fff]
[    0.313701] pnp 00:01: [mem 0xf8000000-0xfbffffff]
[    0.313709] pnp 00:01: [mem 0xfef00000-0xfeffffff]
[    0.313970] system 00:01: [io  0x0800-0x080f] has been reserved
[    0.313982] system 00:01: [io  0x1000-0x107f] has been reserved
[    0.313991] system 00:01: [io  0x1180-0x11bf] has been reserved
[    0.314002] system 00:01: [io  0x04d0-0x04d1] has been reserved
[    0.314011] system 00:01: [io  0xfe00] has been reserved
[    0.314020] system 00:01: [io  0x164e-0x174c] has been reserved
[    0.314032] system 00:01: [mem 0xe0000000-0xefffffff] has been reserved
[    0.314042] system 00:01: [mem 0xfed14000-0xfed17fff] has been reserved
[    0.314052] system 00:01: [mem 0xf8000000-0xfbffffff] has been reserved
[    0.314062] system 00:01: [mem 0xfef00000-0xfeffffff] has been reserved
[    0.314075] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.314118] pnp 00:02: [io  0x0000-0x000f]
[    0.314126] pnp 00:02: [io  0x0081-0x008f]
[    0.314134] pnp 00:02: [io  0x00c0-0x00df]
[    0.314141] pnp 00:02: [dma 4]
[    0.314240] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.314275] pnp 00:03: [io  0x00f0-0x00fe]
[    0.314298] pnp 00:03: [irq 13]
[    0.314398] pnp 00:03: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.314520] pnp 00:04: [io  0x0070-0x0071]
[    0.314537] pnp 00:04: [irq 8]
[    0.314641] pnp 00:04: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.314678] pnp 00:05: [io  0x0061]
[    0.314791] pnp 00:05: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.332205] pnp 00:06: [io  0x0060]
[    0.332216] pnp 00:06: [io  0x0064]
[    0.332242] pnp 00:06: [irq 1]
[    0.332407] pnp 00:06: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.332461] pnp 00:07: [irq 12]
[    0.332590] pnp 00:07: Plug and Play ACPI device, IDs SYN071a SYN0700 SYN0002 PNP0f13 (active)
[    0.333210] pnp: PnP ACPI: found 8 devices
[    0.333220] ACPI: ACPI bus type pnp unregistered
[    0.333230] PnPBIOS: Disabled by ACPI PNP
[    0.374533] pci 0000:00:1c.0: BAR 14: assigned [mem 0x40000000-0x401fffff]
[    0.374551] pci 0000:00:1c.0: BAR 15: assigned [mem 0x40200000-0x403fffff 64bit pref]
[    0.374566] pci 0000:00:1c.1: BAR 15: assigned [mem 0x40400000-0x405fffff 64bit pref]
[    0.374580] pci 0000:00:1c.2: BAR 14: assigned [mem 0x40600000-0x409fffff]
[    0.374594] pci 0000:00:1b.0: BAR 0: assigned [mem 0x40a00000-0x40a03fff 64bit]
[    0.374612] pci 0000:00:1b.0: BAR 0: set to [mem 0x40a00000-0x40a03fff 64bit] (PCI address [0x40a00000-0x40a03fff])
[    0.374627] pci 0000:00:1c.0: BAR 13: assigned [io  0x3000-0x3fff]
[    0.374640] pci 0000:00:1c.1: BAR 13: assigned [io  0x4000-0x4fff]
[    0.374653] pci 0000:00:1d.7: BAR 0: assigned [mem 0x40a04000-0x40a043ff]
[    0.374667] pci 0000:00:1d.7: BAR 0: set to [mem 0x40a04000-0x40a043ff] (PCI address [0x40a04000-0x40a043ff])
[    0.374683] pci 0000:00:1f.2: BAR 5: assigned [mem 0x40a04400-0x40a047ff]
[    0.374696] pci 0000:00:1f.2: BAR 5: set to [mem 0x40a04400-0x40a047ff] (PCI address [0x40a04400-0x40a047ff])
[    0.374707] pci 0000:00:1c.0: PCI bridge to [bus 05-05]
[    0.374716] pci 0000:00:1c.0:   bridge window [io  0x3000-0x3fff]
[    0.374729] pci 0000:00:1c.0:   bridge window [mem 0x40000000-0x401fffff]
[    0.374741] pci 0000:00:1c.0:   bridge window [mem 0x40200000-0x403fffff 64bit pref]
[    0.374756] pci 0000:00:1c.1: PCI bridge to [bus 07-07]
[    0.374765] pci 0000:00:1c.1:   bridge window [io  0x4000-0x4fff]
[    0.374778] pci 0000:00:1c.1:   bridge window [mem 0xf0100000-0xf01fffff]
[    0.374790] pci 0000:00:1c.1:   bridge window [mem 0x40400000-0x405fffff 64bit pref]
[    0.374808] pci 0000:09:00.0: BAR 6: assigned [mem 0xf0540000-0xf055ffff pref]
[    0.374817] pci 0000:00:1c.2: PCI bridge to [bus 09-09]
[    0.374826] pci 0000:00:1c.2:   bridge window [io  0x2000-0x2fff]
[    0.374838] pci 0000:00:1c.2:   bridge window [mem 0x40600000-0x409fffff]
[    0.374850] pci 0000:00:1c.2:   bridge window [mem 0xf0500000-0xf05fffff 64bit pref]
[    0.374865] pci 0000:00:1e.0: PCI bridge to [bus 11-11]
[    0.374872] pci 0000:00:1e.0:   bridge window [io  disabled]
[    0.374883] pci 0000:00:1e.0:   bridge window [mem disabled]
[    0.374892] pci 0000:00:1e.0:   bridge window [mem pref disabled]
[    0.374915] pci 0000:00:1c.0: enabling device (0000 -> 0003)
[    0.374952] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.374968] pci 0000:00:1c.0: setting latency timer to 64
[    0.374999] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.375013] pci 0000:00:1c.1: setting latency timer to 64
[    0.375043] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.375055] pci 0000:00:1c.2: setting latency timer to 64
[    0.375074] pci 0000:00:1e.0: setting latency timer to 64
[    0.375086] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.375095] pci_bus 0000:00: resource 5 [mem 0x000a0000-0x000bffff]
[    0.375104] pci_bus 0000:00: resource 6 [mem 0x000d0000-0x000d3fff]
[    0.375113] pci_bus 0000:00: resource 7 [mem 0x000d4000-0x000d7fff]
[    0.375122] pci_bus 0000:00: resource 8 [mem 0x000d8000-0x000dbfff]
[    0.375131] pci_bus 0000:00: resource 9 [mem 0x000e0000-0x000e3fff]
[    0.375140] pci_bus 0000:00: resource 10 [mem 0x40000000-0xf7ffffff]
[    0.375150] pci_bus 0000:00: resource 11 [io  0x0d00-0xfdff]
[    0.375160] pci_bus 0000:05: resource 0 [io  0x3000-0x3fff]
[    0.375169] pci_bus 0000:05: resource 1 [mem 0x40000000-0x401fffff]
[    0.375179] pci_bus 0000:05: resource 2 [mem 0x40200000-0x403fffff 64bit pref]
[    0.375188] pci_bus 0000:07: resource 0 [io  0x4000-0x4fff]
[    0.375197] pci_bus 0000:07: resource 1 [mem 0xf0100000-0xf01fffff]
[    0.375206] pci_bus 0000:07: resource 2 [mem 0x40400000-0x405fffff 64bit pref]
[    0.375215] pci_bus 0000:09: resource 0 [io  0x2000-0x2fff]
[    0.375224] pci_bus 0000:09: resource 1 [mem 0x40600000-0x409fffff]
[    0.375233] pci_bus 0000:09: resource 2 [mem 0xf0500000-0xf05fffff 64bit pref]
[    0.375242] pci_bus 0000:11: resource 4 [io  0x0000-0x0cf7]
[    0.375251] pci_bus 0000:11: resource 5 [mem 0x000a0000-0x000bffff]
[    0.375260] pci_bus 0000:11: resource 6 [mem 0x000d0000-0x000d3fff]
[    0.375269] pci_bus 0000:11: resource 7 [mem 0x000d4000-0x000d7fff]
[    0.375278] pci_bus 0000:11: resource 8 [mem 0x000d8000-0x000dbfff]
[    0.375286] pci_bus 0000:11: resource 9 [mem 0x000e0000-0x000e3fff]
[    0.375296] pci_bus 0000:11: resource 10 [mem 0x40000000-0xf7ffffff]
[    0.375304] pci_bus 0000:11: resource 11 [io  0x0d00-0xfdff]
[    0.375396] NET: Registered protocol family 2
[    0.375584] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.376248] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.377312] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.377862] TCP: Hash tables configured (established 131072 bind 65536)
[    0.377870] TCP reno registered
[    0.377882] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.377906] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.378206] NET: Registered protocol family 1
[    0.378252] pci 0000:00:02.0: Boot video device
[    0.378431] PCI: CLS 32 bytes, default 64
[    0.378486] Simple Boot Flag at 0x35 set to 0x1
[    0.379016] cpufreq-nforce2: No nForce2 chipset.
[    0.379405] audit: initializing netlink socket (disabled)
[    0.379430] type=2000 audit(1314223103.372:1): initialized
[    0.403354] highmem bounce pool size: 64 pages
[    0.403373] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.409750] VFS: Disk quotas dquot_6.5.2
[    0.409962] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.412447] fuse init (API version 7.16)
[    0.412790] msgmni has been set to 1704
[    0.413605] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.413725] io scheduler noop registered
[    0.413733] io scheduler deadline registered
[    0.413800] io scheduler cfq registered (default)
[    0.414109] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.414192] pcieport 0000:00:1c.0: irq 40 for MSI/MSI-X
[    0.414339] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.414416] pcieport 0000:00:1c.1: irq 41 for MSI/MSI-X
[    0.414575] pcieport 0000:00:1c.2: setting latency timer to 64
[    0.414648] pcieport 0000:00:1c.2: irq 42 for MSI/MSI-X
[    0.414869] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.414947] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.415117] intel_idle: MWAIT substates: 0x20220
[    0.415136] intel_idle: v0.4 model 0x1C
[    0.415143] intel_idle: lapic_timer_reliable_states 0x2
[    0.415161] Marking TSC unstable due to TSC halts in idle states deeper than C2
[    0.415584] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.415991] ACPI: AC Adapter [ACAD] (off-line)
[    0.416264] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:0d/PNP0C0D:00/input/input0
[    0.416333] ACPI: Lid Switch [LID0]
[    0.416498] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0A08:00/PNP0C0C:00/input/input1
[    0.416512] ACPI: Power Button [PWRB]
[    0.416668] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.416680] ACPI: Power Button [PWRF]
[    0.417139] ACPI: acpi_idle yielding to intel_idle
[    0.446225] ERST: Table is not found!
[    0.446439] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.447160] isapnp: Scanning for PnP cards...
[    0.656868] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.656894] ACPI: Battery Slot [BAT1] (battery present)
[    0.801560] isapnp: No Plug & Play device found
[    0.842263] Freeing initrd memory: 12560k freed
[    0.868044] Linux agpgart interface v0.103
[    0.868219] agpgart-intel 0000:00:00.0: Intel GMA3150 Chipset
[    0.868411] agpgart-intel 0000:00:00.0: detected gtt size: 524288K total, 262144K mappable
[    0.868662] agpgart-intel 0000:00:00.0: detected 8192K stolen memory
[    0.868883] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[    0.871946] brd: module loaded
[    0.873455] loop: module loaded
[    0.873683] i2c-core: driver [adp5520] using legacy suspend method
[    0.873688] i2c-core: driver [adp5520] using legacy resume method
[    0.874703] Fixed MDIO Bus: probed
[    0.874795] PPP generic driver version 2.4.2
[    0.874900] tun: Universal TUN/TAP device driver, 1.6
[    0.874905] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.875109] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.875173] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.875205] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.875213] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.875308] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.875423] ehci_hcd 0000:00:1d.7: using broken periodic workaround
[    0.875442] ehci_hcd 0000:00:1d.7: debug port 1
[    0.879324] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.879357] ehci_hcd 0000:00:1d.7: irq 23, io mem 0x40a04000
[    0.892028] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.892316] hub 1-0:1.0: USB hub found
[    0.892327] hub 1-0:1.0: 8 ports detected
[    0.892507] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.892543] uhci_hcd: USB Universal Host Controller Interface driver
[    0.892613] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.892627] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.892634] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.892741] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.892830] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001820
[    0.893138] hub 2-0:1.0: USB hub found
[    0.893149] hub 2-0:1.0: 2 ports detected
[    0.893312] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.893325] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.893332] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.893440] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.893538] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001840
[    0.893835] hub 3-0:1.0: USB hub found
[    0.893846] hub 3-0:1.0: 2 ports detected
[    0.893993] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.894006] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.894013] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.894106] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.900090] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001860
[    0.900408] hub 4-0:1.0: USB hub found
[    0.900419] hub 4-0:1.0: 2 ports detected
[    0.900562] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    0.900574] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    0.900581] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    0.900677] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    0.900782] uhci_hcd 0000:00:1d.3: irq 16, io base 0x00001880
[    0.901078] hub 5-0:1.0: USB hub found
[    0.901088] hub 5-0:1.0: 2 ports detected
[    0.901338] i8042: PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:razz:S2M] at 0x60,0x64 irq 1,12
[    0.926936] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.926954] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.927269] mousedev: PS/2 mouse device common for all mice
[    0.929079] rtc_cmos 00:04: RTC can wake from S4
[    0.929236] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    0.929276] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    0.929510] device-mapper: uevent: version 1.0.3
[    0.929715] device-mapper: ioctl: 4.19.1-ioctl (2011-01-07) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[    0.929886] device-mapper: multipath: version 1.2.0 loaded
[    0.929895] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.930101] EISA: Probing bus 0 at eisa.0
[    0.930107] EISA: Cannot allocate resource for mainboard
[    0.930112] Cannot allocate resource for EISA slot 1
[    0.930117] Cannot allocate resource for EISA slot 2
[    0.930121] Cannot allocate resource for EISA slot 3
[    0.930126] Cannot allocate resource for EISA slot 4
[    0.930130] Cannot allocate resource for EISA slot 5
[    0.930135] Cannot allocate resource for EISA slot 6
[    0.930139] Cannot allocate resource for EISA slot 7
[    0.930144] Cannot allocate resource for EISA slot 8
[    0.930148] EISA: Detected 0 cards.
[    0.930417] cpuidle: using governor ladder
[    0.930634] cpuidle: using governor menu
[    0.931242] TCP cubic registered
[    0.931577] NET: Registered protocol family 10
[    0.932845] NET: Registered protocol family 17
[    0.932889] Registering the dns_resolver key type
[    0.933685] Using IPI No-Shortcut mode
[    0.933970] PM: Hibernation image not present or could not be loaded.
[    0.934004] registered taskstats version 1
[    0.934447]   Magic number: 7:487:1006
[    0.934576] rtc_cmos 00:04: setting system clock to 2011-08-24 21:58:24 UTC (1314223104)
[    0.934585] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.934590] EDD information not available.
[    0.934807] Freeing unused kernel memory: 700k freed
[    0.935212] Write protecting the kernel text: 5192k
[    0.935302] Write protecting the kernel read-only data: 2148k
[    0.955080] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    0.985177] <30>udev[65]: starting version 167
[    1.204077] usb 1-4: new high speed USB device using ehci_hcd and address 2
[    1.222734] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.222784] r8169 0000:09:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.222853] r8169 0000:09:00.0: setting latency timer to 64
[    1.222948] r8169 0000:09:00.0: irq 43 for MSI/MSI-X
[    1.251030] r8169 0000:09:00.0: eth0: RTL8102e at 0xf8026000, 70:5a:b6:71:54:68, XID 04e00000 IRQ 43
[    1.290214] ahci 0000:00:1f.2: version 3.0
[    1.290247] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.290348] ahci 0000:00:1f.2: irq 44 for MSI/MSI-X
[    1.290472] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[    1.290485] ahci 0000:00:1f.2: flags: 64bit ncq pm led clo pio slum part 
[    1.290497] ahci 0000:00:1f.2: setting latency timer to 64
[    1.292563] scsi0 : ahci
[    1.292955] scsi1 : ahci
[    1.293247] scsi2 : ahci
[    1.293539] scsi3 : ahci
[    1.294014] ata1: SATA max UDMA/133 abar m1024@0x40a04400 port 0x40a04500 irq 44
[    1.294027] ata2: SATA max UDMA/133 abar m1024@0x40a04400 port 0x40a04580 irq 44
[    1.294038] ata3: SATA max UDMA/133 abar m1024@0x40a04400 port 0x40a04600 irq 44
[    1.294047] ata4: SATA max UDMA/133 abar m1024@0x40a04400 port 0x40a04680 irq 44
[    1.603724] usbcore: registered new interface driver uas
[    1.612106] ata4: SATA link down (SStatus 0 SControl 300)
[    1.612149] ata2: SATA link down (SStatus 0 SControl 300)
[    1.612183] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.612222] ata3: SATA link down (SStatus 0 SControl 300)
[    1.704075] usb 1-5: new high speed USB device using ehci_hcd and address 3
[    1.704125] ata1.00: ATA-8: TOSHIBA MK2555GSX, FG001M, max UDMA/100
[    1.704133] ata1.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.708232] ata1.00: configured for UDMA/100
[    1.708534] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK2555GS FG00 PQ: 0 ANSI: 5
[    1.709082] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.709208] sd 0:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    1.709471] sd 0:0:0:0: [sda] Write Protect is off
[    1.709482] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.709593] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.787397]  sda: sda1 sda2 < sda5 >
[    1.788392] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.810622] Initializing USB Mass Storage driver...
[    1.810944] scsi4 : usb-storage 1-4:1.0
[    1.811277] usbcore: registered new interface driver usb-storage
[    1.811285] USB Mass Storage support registered.
[    1.844947] scsi5 : usb-storage 1-5:1.0
[    1.960052] usb 1-8: new high speed USB device using ehci_hcd and address 4
[    2.397482] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    2.811155] scsi 4:0:0:0: Direct-Access     Generic- Multi-Card       1.00 PQ: 0 ANSI: 0 CCS
[    2.812351] sd 4:0:0:0: Attached scsi generic sg1 type 0
[    2.816738] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[    2.849152] scsi 5:0:0:0: Direct-Access     Kingston DataTraveler G3  PMAP PQ: 0 ANSI: 0 CCS
[    2.850358] sd 5:0:0:0: Attached scsi generic sg2 type 0
[    2.851089] sd 5:0:0:0: [sdc] 15636864 512-byte logical blocks: (8.00 GB/7.45 GiB)
[    2.851578] sd 5:0:0:0: [sdc] Write Protect is off
[    2.851587] sd 5:0:0:0: [sdc] Mode Sense: 23 00 00 00
[    2.851593] sd 5:0:0:0: [sdc] Assuming drive cache: write through
[    2.853953] sd 5:0:0:0: [sdc] Assuming drive cache: write through
[    2.855203]  sdc: sdc1
[    2.857078] sd 5:0:0:0: [sdc] Assuming drive cache: write through
[    2.857086] sd 5:0:0:0: [sdc] Attached SCSI removable disk
[  242.109861] Adding 1036284k swap on /dev/sda5.  Priority:-1 extents:1 across:1036284k 
[  242.172704] <30>udev[294]: starting version 167
[  242.336639] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[  242.453973] lp: driver loaded but no devices found
[  242.871613] type=1400 audit(1314223346.430:2): apparmor="STATUS"  operation="profile_load" name="/sbin/dhclient" pid=425  comm="apparmor_parser"
[  242.872742] type=1400 audit(1314223346.434:3): apparmor="STATUS"  operation="profile_load"  name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=425  comm="apparmor_parser"
[  242.873450] type=1400 audit(1314223346.434:4): apparmor="STATUS"  operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script"  pid=425 comm="apparmor_parser"
[  243.703473] r8169 0000:09:00.0: eth0: link down
[  243.706943] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  244.032191] Linux video capture interface: v2.00
[  244.228095] cfg80211: Calling CRDA to update world regulatory domain
[  244.284149] type=1400 audit(1314223347.846:5): apparmor="STATUS"  operation="profile_replace" name="/sbin/dhclient" pid=644  comm="apparmor_parser"
[  244.291269] type=1400 audit(1314223347.850:6): apparmor="STATUS"  operation="profile_replace"  name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=644  comm="apparmor_parser"
[  244.291970] type=1400 audit(1314223347.850:7): apparmor="STATUS"  operation="profile_replace"  name="/usr/lib/connman/scripts/dhclient-script" pid=644  comm="apparmor_parser"
[  244.323895] type=1400 audit(1314223347.882::cool:: apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=645 comm="apparmor_parser"
[  244.370771] type=1400 audit(1314223347.930:9): apparmor="STATUS"  operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=650  comm="apparmor_parser"
[  244.378625] type=1400 audit(1314223347.938:10): apparmor="STATUS"  operation="profile_load" name="/usr/sbin/cupsd" pid=650  comm="apparmor_parser"
[  244.414123] type=1400 audit(1314223347.974:11): apparmor="STATUS"  operation="profile_load" name="/usr/bin/evince-previewer" pid=645  comm="apparmor_parser"
[  244.597120] uvcvideo: Found UVC 1.00 device USB 2.0 PC Cam (090c:e37b)
[  244.777699] input: USB 2.0 PC Cam as /devices/pci0000:00/0000:00:1d.7/usb1/1-8/1-8:1.0/input/input4
[  244.778174] usbcore: registered new interface driver uvcvideo
[  244.778183] USB Video Class driver (v1.0.0)
[  245.103559] [drm] Initialized drm 1.1.0 20060810
[  245.353014] cfg80211: World regulatory domain updated:
[  245.353024] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  245.353035] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  245.353044] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  245.353054] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  245.353063] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  245.353072] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  245.960332] Synaptics Touchpad, model: 1, fw: 7.2, id: 0x1c0b1, caps: 0xd04733/0xa40000/0xa0000
[  246.002480] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[  246.002495] i915 0000:00:02.0: setting latency timer to 64
[  246.080083] i915 0000:00:02.0: irq 45 for MSI/MSI-X
[  246.080098] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[  246.080105] [drm] Driver supports precise vblank timestamp query.
[  246.089018] ath9k 0000:07:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[  246.089046] ath9k 0000:07:00.0: setting latency timer to 64
[  246.139787] ath: EEPROM regdomain: 0x65
[  246.139795] ath: EEPROM indicates we should expect a direct regpair map
[  246.139805] ath: Country alpha2 being used: 00
[  246.139810] ath: Regpair used: 0x65
[  246.139819] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[  246.139829] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[  246.139836] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[  246.139845] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[  246.139852] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[  246.139861] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[  246.139869] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[  246.139878] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[  246.139885] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[  246.139894] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[  246.139901] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[  246.139910] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[  246.139918] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[  246.139926] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[  246.139934] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[  246.139943] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[  246.139950] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[  246.139959] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[  246.139966] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[  246.139975] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[  246.139982] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[  246.139991] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[  246.140037] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[  246.140047] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[  246.140054] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[  246.140063] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[  246.140070] cfg80211: Disabling freq 2484 MHz as custom regd has no rule that fits a 20 MHz wide channel
[  246.145710] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[  246.173295] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input5
[  246.198771] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:eek:wns=io+mem
[  246.199298] [drm] initialized overlay support
[  246.392511] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
[  246.394583] Registered led device: ath9k-phy0::radio
[  246.394672] Registered led device: ath9k-phy0::assoc
[  246.394751] Registered led device: ath9k-phy0::tx
[  246.394833] Registered led device: ath9k-phy0::rx
[  246.394856] ieee80211 phy0: Atheros AR9285 Rev:2 mem=0xf8300000, irq=17
[  246.510463] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  246.524169] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=600
[  246.537248] fbcon: inteldrmfb (fb0) is primary device
[  246.544161] Console: switching to colour frame buffer device 128x37
[  246.544241] fb0: inteldrmfb frame buffer device
[  246.544247] drm: registered panic notifier
[  246.555228] acpi device:01: registered as cooling_device2
[  246.560751] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input6
[  246.561253] ACPI: Video Device [IGD0] (multi-head: yes  rom: no  post: no)
[  246.564150] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[  246.564279] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[  246.564395] HDA Intel 0000:00:1b.0: irq 46 for MSI/MSI-X
[  246.564454] HDA Intel 0000:00:1b.0: setting latency timer to 64
[  246.636164] fixme: max PWM is zero.
[  246.877719] hda_codec: ALC272: BIOS auto-probing.
[  246.906037] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[  246.906576] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[  247.485035] ppdev: user-space parallel port driver
[  251.276207] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=600
[  334.262007] wlan0: authenticate with 00:18:f8:f9:38:d5 (try 1)
[  334.266359] wlan0: authenticated
[  334.285213] wlan0: associate with 00:18:f8:f9:38:d5 (try 1)
[  334.290069] wlan0: RX AssocResp from 00:18:f8:f9:38:d5 (capab=0x401 status=0 aid=7)
[  334.290080] wlan0: associated
[  334.291050] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  344.648053] wlan0: no IPv6 routers present
[  348.201715] usb 1-5: USB disconnect, address 3
```

---

### Post by trozamon on 2011-08-24
It looks like it's taking almost 4 minutes just to mount the device sdc. Can you run the command:

```
mount
```

and post the output here?

---

### Post by halobium on 2011-08-24
```
/dev/sda1 on / type ext4 (rw,errors=remount-ro,commit=600)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/adejesus/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=adejesus)
```

---

### Post by trozamon on 2011-08-24
Well, I was hoping to see where /dev/sdc got mounted. Is there any chance you know what device "sdc" is? If not, open up a program called "Disk Utility", and choose different devices until you find /dev/sdc.

Others might be able to help better, this is the only way I know of to work around this problem

---

### Post by spcwingo on 2011-08-24
If I'm not mistaken /dev/sdc is usually your optical drive.  If your system lacks one, but the optical drive is still enabled in your BIOS, this could possibly cause issues like the one you're describing.

Another thing that might help get to the root of the issue is right after you power on the machine, but directly after the POST screen, press and hold the shift key.  At the GRUB menu with the first line selected press "e" (without quotes).  At the end of the string delete "quiet splash".  After that press "b" to boot.  This will allow you see the messages printed to the screen at the time of the hang.

---

### Post by westie457 on 2011-08-24
If the /sdc is a usb-drive try booting your computer without the stick plugged in. See if this makes any difference to the boot time.

If boot time is quicker plug the stick in and use Disk Utility to check the file system of the usb stick and hopefully fix any errors.

---

### Post by halobium on 2011-08-24
Hey, 

Thanks for all the help... Um, I'm officially giving up on Linux for this particular computer. I don't have any more time to devote to trying to get this to work (going on five days now). I've got to get my computer ready for school and only have a mere night left. 

Sadly, this does mean I'm going back to windows with my tail tucked between my legs. 

Never fear, I shall attempt to become a linux user again!

Ps. How do you close a thread?

---

### Post by halobium on 2011-08-25
Um... Sorry, my cup of frustration over-flowed yesterday, but I'm back at it. 

I did, however, decide that I liked ubuntu's unity desktop better than xubuntu. So, this is what I'm currently trying to fix (with the same problem as above).

---

### Post by halobium on 2011-08-25
/dev/sdc is the usb drive. 

Having a usb stick plugged in only shaves off about a minute from the boot (4m vs. 5m).

---

### Post by pqwoerituytrueiwoq on 2011-08-25
post the output of this line in the terminal
```
echo "------------------/etc/initramfs-tools/conf.d/resume--------------------";cat /etc/initramfs-tools/conf.d/resume;echo;echo "-----------------------------/etc/fstab---------------------------------";cat /etc/fstab
```

---

### Post by halobium on 2011-08-25
```
echo  "------------------/etc/initramfs-tools/conf.d/resume--------------------";cat  /etc/initramfs-tools/conf.d/resume;echo;echo  "-----------------------------/etc/fstab---------------------------------";cat  /etc/fstab
------------------/etc/initramfs-tools/conf.d/resume--------------------
RESUME=UUID=283dd40e-e16a-4284-aedc-1db4a72631ad

-----------------------------/etc/fstab---------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=942fae18-f6ef-4543-9f16-711d82f90933 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=283dd40e-e16a-4284-aedc-1db4a72631ad none            swap    sw              0       0
```

---

### Post by akand074 on 2011-08-25
I'm surprised no one mentioned it. Could you please post your output in a code bracket. I.e make sure you go advanced and not just quick reply. Press on the "#" to post code. Then copy paste anything in between the [.code] and [/code.] 

```
Like this!
```I'd recommend editing your posts and fixing that. Makes it easier to help you and keeps the thread clean.

---

### Post by pqwoerituytrueiwoq on 2011-08-25
lets make sure the swap partition is there
post output of:
```
sudo blkid
```

---

### Post by halobium on 2011-08-25
```
/dev/sda1: UUID="942fae18-f6ef-4543-9f16-711d82f90933" TYPE="ext4" 
/dev/sda5: UUID="283dd40e-e16a-4284-aedc-1db4a72631ad" TYPE="swap"
```

---

### Post by pqwoerituytrueiwoq on 2011-08-25
that was a dead end it seems
a boot chart may help
```
sudo apt-get install bootchart
```when you reboot look in /var/log/bootchart/ (upload image to [http://imgur.com/](http://imgur.com/) the forums will resize it making it unreadable if you do it here)
boot without the usb plugged in

i see a couple thing i could tell you how to disable but it would only get you about 3-8 seconds you could disable ipv6 since you don't have a ipv6 router and you could disable ppdev if you don't have/use a parallel port (eg old school printer)

---

