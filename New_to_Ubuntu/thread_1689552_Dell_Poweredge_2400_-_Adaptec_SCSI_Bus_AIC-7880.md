---
title: "Dell Poweredge 2400 - Adaptec SCSI Bus AIC-7880"
date: 2011-02-16
forum: New to Ubuntu
---

### Post by hockey_man3 on 2011-02-16
Hello all,

I'm sorry if this isn't in the correct area, I wasn't sure if I should put this under the dell ubuntu support because I know this server is really old and didn't come with ubuntu so the post is here......onwards

As the title states, I have a Dell Poweredge 2400 with an Adaptec SCSI bus AIC-7880 which I'm currently using to post this message. (there's another scsi bus installed which has the hardware RAID array which I have 6 X 18GB 10K SCSI drives attached to and are working beautifully running ubuntu 10.10 server)

So with all that said, it seems ubuntu cannot talk to the  AIC-7880 SCSI bus and recognize I have a toshiba DVD/ROM drive and a python tape drive attached to it. And yes the hardware works....I used the DVD/ROM drive to install ubuntu 10.10 server from a cd attached to the 7880 scsi bus (which is the bus which is currently not working).

Nowhere in dmesg does it show it has found the 7880 bus or the corresponding drives attached to it as follows......

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.35-22-generic-pae (buildd@rothera) (gcc version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu4) ) #33-Ubuntu SMP Sun Sep 19 22:14:14 UTC 2010 (Ubuntu 2.6.35-22.33-generic-pae 2.6.35.4)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 00000000000a0000 (usable)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000002fffe000 (usable)
[    0.000000]  BIOS-e820: 000000002fffe000 - 0000000030000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] NX (Execute Disable) protection: approximated by x86 segment limits
[    0.000000] DMI 2.3 present.
[    0.000000] e820 update range: 0000000000000000 - 0000000000001000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x2fffe max_arch_pfn = 0x1000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask FE0000000 write-back
[    0.000000]   1 base 020000000 mask FF0000000 write-back
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] PAT not supported by CPU.
[    0.000000] e820 update range: 0000000000002000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000001000 (reserved)
[    0.000000]  modified: 0000000000001000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000002000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 00000000000a0000 (usable)
[    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000002fffe000 (usable)
[    0.000000]  modified: 000000002fffe000 - 0000000030000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee10000 (reserved)
[    0.000000]  modified: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00e00000
[    0.000000] found SMP MP-table at [c00fe710] fe710
[    0.000000] init_memory_mapping: 0000000000000000-000000002fffe000
[    0.000000]  0000000000 - 0000200000 page 4k
[    0.000000]  0000200000 - 002fe00000 page 2M
[    0.000000]  002fe00000 - 002fffe000 page 4k
[    0.000000] kernel direct mapping tables up to 2fffe000 @ 15000-1a000
[    0.000000] RAMDISK: 23601000 - 2403f000
[    0.000000] ACPI: RSDP 000fdcd0 00014 (v00 DELL  )
[    0.000000] ACPI: RSDT 000fdce4 0002C (v01 DELL   PE2400   00000001 MSFT 0100000A)
[    0.000000] ACPI: FACP 000fdd10 00074 (v01 DELL   PE2400   00000001 MSFT 0100000A)
[    0.000000] ACPI: DSDT ffff4800 026F3 (v01 DELL   PE2400   00000001 MSFT 0100000A)
[    0.000000] ACPI: FACS 2fffe000 00040
[    0.000000] ACPI: APIC 000fdd84 00060 (v01 DELL   PE2400   00000001 MSFT 0100000A)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 767MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 2fffe000
[    0.000000]   low ram: 0 - 2fffe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000001 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x0002fffe
[    0.000000]   HighMem  empty
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000001 -> 0x00000002
[    0.000000]     0: 0x00000010 -> 0x000000a0
[    0.000000]     0: 0x00000100 -> 0x0002fffe
[    0.000000] On node 0 totalpages: 196495
[    0.000000] free_area_init_node: node 0, pgdat c083ea40, node_mem_map c1001020
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3953 pages, LIFO batch:0
[    0.000000]   Normal zone: 1504 pages used for memmap
[    0.000000]   Normal zone: 191006 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-15
[    0.000000] ACPI: IOAPIC (id[0x03] address[0xfec01000] gsi_base[16])
[    0.000000] IOAPIC[1]: apic_id 3, version 17, address 0xfec01000, GSI 16-31
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 48
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000010000
[    0.000000] early_res array is doubled to 64 at [16000 - 167ff]
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 30000000:cec00000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 15 pages/cpu @c1800000 s39872 r0 d21568 u1048576
[    0.000000] pcpu-alloc: s39872 r0 d21568 u1048576 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 194959
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-22-generic-pae root=UUID=495bdd8e-d0ee-4620-a9a9-d148350108ce ro quiet
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 3932100 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Subtract (44 early reservations)
[    0.000000]   #1 [0000001000 - 0000002000]   EX TRAMPOLINE
[    0.000000]   #2 [0000100000 - 00009f965c]   TEXT DATA BSS
[    0.000000]   #3 [0023601000 - 002403f000]         RAMDISK
[    0.000000]   #4 [00009fa000 - 0000a01124]             BRK
[    0.000000]   #5 [00000fe720 - 0000100000]   BIOS reserved
[    0.000000]   #6 [00000fe710 - 00000fe720]    MP-table mpf
[    0.000000]   #7 [000009e000 - 00000f0000]   BIOS reserved
[    0.000000]   #8 [00000f01f4 - 00000fe710]   BIOS reserved
[    0.000000]   #9 [00000f0000 - 00000f01f4]    MP-table mpc
[    0.000000]   #10 [0000010000 - 0000011000]      TRAMPOLINE
[    0.000000]   #11 [0000011000 - 0000015000]     ACPI WAKEUP
[    0.000000]   #12 [0000015000 - 0000016000]         PGTABLE
[    0.000000]   #13 [0001000000 - 0001001000]         BOOTMEM
[    0.000000]   #14 [0001001000 - 0001601000]         BOOTMEM
[    0.000000]   #15 [0001601000 - 0001601004]         BOOTMEM
[    0.000000]   #16 [0001601040 - 0001601100]         BOOTMEM
[    0.000000]   #17 [0001601100 - 0001601190]         BOOTMEM
[    0.000000]   #18 [00016011c0 - 00016041c0]         BOOTMEM
[    0.000000]   #19 [00016041c0 - 000160421e]         BOOTMEM
[    0.000000]   #20 [0001604240 - 00016043a8]         BOOTMEM
[    0.000000]   #21 [00016043c0 - 0001604400]         BOOTMEM
[    0.000000]   #22 [0001604400 - 0001604440]         BOOTMEM
[    0.000000]   #23 [0001604440 - 0001604480]         BOOTMEM
[    0.000000]   #24 [0001604480 - 00016044c0]         BOOTMEM
[    0.000000]   #25 [00016044c0 - 0001604500]         BOOTMEM
[    0.000000]   #26 [0001604500 - 0001604540]         BOOTMEM
[    0.000000]   #27 [0001604540 - 0001604580]         BOOTMEM
[    0.000000]   #28 [0001604580 - 0001604590]         BOOTMEM
[    0.000000]   #29 [00016045c0 - 00016045d0]         BOOTMEM
[    0.000000]   #30 [0001604600 - 0001604667]         BOOTMEM
[    0.000000]   #31 [0001604680 - 00016046e7]         BOOTMEM
[    0.000000]   #32 [0001800000 - 000180f000]         BOOTMEM
[    0.000000]   #33 [0001900000 - 000190f000]         BOOTMEM
[    0.000000]   #34 [0001606700 - 0001606704]         BOOTMEM
[    0.000000]   #35 [0001606740 - 0001606744]         BOOTMEM
[    0.000000]   #36 [0001606780 - 0001606788]         BOOTMEM
[    0.000000]   #37 [00016067c0 - 00016067c8]         BOOTMEM
[    0.000000]   #38 [0001606800 - 00016068a0]         BOOTMEM
[    0.000000]   #39 [00016068c0 - 0001606908]         BOOTMEM
[    0.000000]   #40 [0001606940 - 000160a940]         BOOTMEM
[    0.000000]   #41 [000160a940 - 000168a940]         BOOTMEM
[    0.000000]   #42 [000168a940 - 00016ca940]         BOOTMEM
[    0.000000]   #43 [000190f000 - 0001ccefc4]         BOOTMEM
[    0.000000] Initializing HighMem for node 0 (00000000:00000000)
[    0.000000] Memory: 755320k/786424k available (5085k kernel code, 30660k reserved, 2432k data, 704k init, 0k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
[    0.000000]     vmalloc : 0xf07fe000 - 0xffbfe000   ( 244 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xefffe000   ( 767 MB)
[    0.000000]       .init : 0xc0858000 - 0xc0908000   ( 704 kB)
[    0.000000]       .data : 0xc05f748a - 0xc0857768   (2432 kB)
[    0.000000]       .text : 0xc0100000 - 0xc05f748a   (5085 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=32, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU-based detection of stalled CPUs is disabled.
[    0.000000]     Verbose stalled-CPUs detection is disabled.
[    0.000000] NR_IRQS:2304 nr_irqs:512
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 864.042 MHz processor.
[    0.004009] Calibrating delay loop (skipped), value calculated using timer frequency.. 1728.08 BogoMIPS (lpj=3456168)
[    0.004025] pid_max: default: 32768 minimum: 301
[    0.004074] Security Framework initialized
[    0.004132] AppArmor: AppArmor initialized
[    0.004139] Yama: becoming mindful.
[    0.004307] Mount-cache hash table entries: 512
[    0.004656] Initializing cgroup subsys ns
[    0.004668] Initializing cgroup subsys cpuacct
[    0.004683] Initializing cgroup subsys memory
[    0.004709] Initializing cgroup subsys devices
[    0.004718] Initializing cgroup subsys freezer
[    0.004725] Initializing cgroup subsys net_cls
[    0.004796] CPU serial number disabled.
[    0.004807] mce: CPU supports 5 MCE banks
[    0.004843] Performance Events: p6 PMU driver.
[    0.004858] ... version:                0
[    0.004865] ... bit width:              32
[    0.004871] ... generic registers:      2
[    0.004878] ... value mask:             00000000ffffffff
[    0.004885] ... max period:             000000007fffffff
[    0.004892] ... fixed-purpose events:   0
[    0.004898] ... event mask:             0000000000000003
[    0.014862] ACPI: Core revision 20100428
[    0.034001] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.034020] ftrace: allocating 22394 entries in 44 pages
[    0.036274] Enabling APIC mode:  Flat.  Using 2 I/O APICs
[    0.040339] ..TIMER: vector=0x30 apic1=0 pin1=0 apic2=-1 pin2=-1
[    0.044000] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
[    0.044000] ...trying to set up timer (IRQ0) through the 8259A ...
[    0.044000] ..... (found apic 0 pin 0) ...
[    0.083773] ....... works.
[    0.083779] CPU0: Intel Pentium III (Coppermine) stepping 06
[    0.084000] Booting Node   0, Processors  #1 Ok.
[    0.008000] Initializing CPU#1
[    0.008000] CPU serial number disabled.
[    0.176049] Brought up 2 CPUs
[    0.176063] Total of 2 processors activated (3456.04 BogoMIPS).
[    0.176832] devtmpfs: initialized
[    0.176832] Dell PowerEdge 2400 series board detected. Selecting BIOS-method for reboots.
[    0.182724] regulator: core version 0.5
[    0.182783] Time:  2:31:49  Date: 02/17/11
[    0.182928] NET: Registered protocol family 16
[    0.183077] Trying to unpack rootfs image as initramfs...
[    0.183446] EISA bus registered
[    0.183479] ACPI: bus type pci registered
[    0.212353] PCI: PCI BIOS revision 2.10 entry at 0xfc7de, last bus=3
[    0.212361] PCI: Using configuration type 1 for base access
[    0.224302] bio: create slab <bio-0> at 0
[    0.226608] ACPI: EC: Look up EC in DSDT
[    0.234780] ACPI: Interpreter enabled
[    0.234791] ACPI: (supports S0 S4 S5)
[    0.234844] ACPI: Using IOAPIC for interrupt routing
[    0.249343] ACPI: No dock devices found.
[    0.249362] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
[    0.254547] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-01])
[    0.264249] pci_root PNP0A03:00: host bridge window [io  0x0000-0x03af] (ignored)
[    0.264260] pci_root PNP0A03:00: host bridge window [io  0x03b0-0x03df] (ignored)
[    0.264269] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)
[    0.264279] pci_root PNP0A03:00: host bridge window [io  0x03e0-0x0fff] (ignored)
[    0.264288] pci_root PNP0A03:00: host bridge window [io  0xe000-0xffff] (ignored)
[    0.264297] pci_root PNP0A03:00: host bridge window [mem 0x000d0000-0x000effff] (ignored)
[    0.264306] pci_root PNP0A03:00: host bridge window [mem 0xf0000000-0xfe10ffff] (ignored)
[    0.264336] * The chipset may have PM-Timer Bug. Due to workarounds for a bug,
[    0.264341] * this clock source is slow. If you are sure your timer does not have
[    0.264345] * this bug, please use "acpi_pm_good" to disable the workaround
[    0.264365] pci 0000:00:00.0: CNB20LE PCI Host Bridge (domain 0000 [bus 00-01])
[    0.264374] pci 0000:00:00.0: host bridge window [io  0x01f0-0x01f7]
[    0.264382] pci 0000:00:00.0: host bridge window [io  0x03f6]
[    0.264390] pci 0000:00:00.0: host bridge window [io  0x0170-0x0177]
[    0.264397] pci 0000:00:00.0: host bridge window [io  0x0376]
[    0.264405] pci 0000:00:00.0: host bridge window [io  0xffa0-0xffaf]
[    0.264414] pci 0000:00:00.0: host bridge window [mem 0xfffffffff0000000-0xfffffffffe10ffff]
[    0.264423] pci 0000:00:00.0: host bridge window [io  0xe000-0xfffc]
[    0.264493] * The chipset may have PM-Timer Bug. Due to workarounds for a bug,
[    0.264498] * this clock source is slow. If you are sure your timer does not have
[    0.264502] * this bug, please use "acpi_pm_good" to disable the workaround
[    0.264521] pci 0000:00:00.1: CNB20LE PCI Host Bridge (domain 0000 [bus 02-ff])
[    0.264531] pci 0000:00:00.1: host bridge window [mem 0xffffffffe9000000-0xffffffffefffffff]
[    0.264540] pci 0000:00:00.1: host bridge window [io  0xd000-0xdffc]
[    0.264664] pci 0000:00:02.1: reg 10: [mem 0xf4000000-0xf7ffffff pref]
[    0.264706] pci 0000:00:02.1: reg 30: [mem 0xfb000000-0xfb00ffff pref]
[    0.264755] pci 0000:00:04.0: reg 10: [io  0xec80-0xecff]
[    0.264769] pci 0000:00:04.0: reg 14: [mem 0xfe103000-0xfe103fff]
[    0.264801] pci 0000:00:04.0: reg 30: [mem 0xfb000000-0xfb003fff pref]
[    0.264849] pci 0000:00:08.0: reg 10: [mem 0xfe102000-0xfe102fff]
[    0.264862] pci 0000:00:08.0: reg 14: [io  0xec40-0xec7f]
[    0.264875] pci 0000:00:08.0: reg 18: [mem 0xfe000000-0xfe0fffff]
[    0.264899] pci 0000:00:08.0: reg 30: [mem 0xfb000000-0xfb0fffff pref]
[    0.264925] pci 0000:00:08.0: supports D1 D2
[    0.264933] pci 0000:00:08.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.264943] pci 0000:00:08.0: PME# disabled
[    0.264989] pci 0000:00:0e.0: reg 10: [mem 0xf9000000-0xf9ffffff pref]
[    0.265002] pci 0000:00:0e.0: reg 14: [io  0xe800-0xe8ff]
[    0.265015] pci 0000:00:0e.0: reg 18: [mem 0xfe101000-0xfe101fff]
[    0.265042] pci 0000:00:0e.0: reg 30: [mem 0x00000000-0x0001ffff pref]
[    0.265144] pci 0000:00:0f.2: reg 10: [mem 0xfe100000-0xfe100fff]
[    0.265217] PCI: peer root bus 00 res updated from pci conf
[    0.265294] pci 0000:01:06.0: reg 10: [io  0xfc00-0xfcff]
[    0.265309] pci 0000:01:06.0: reg 14: [mem 0xfcfff000-0xfcffffff]
[    0.265346] pci 0000:01:06.0: reg 30: [mem 0xfd000000-0xfd00ffff pref]
[    0.265419] pci 0000:00:02.0: PCI bridge to [bus 01-01]
[    0.265431] pci 0000:00:02.0:   bridge window [io  0xf000-0xffff]
[    0.265443] pci 0000:00:02.0:   bridge window [mem 0xfc000000-0xfdffffff]
[    0.265455] pci 0000:00:02.0:   bridge window [mem 0xfa000000-0xfaffffff pref]
[    0.265473] pci_bus 0000:00: on NUMA node 0
[    0.265487] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.265999] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.I960._PRT]
[    0.273124] ACPI: PCI Root Bridge [PCI1] (domain 0000 [bus 02-ff])
[    0.280019] pci_root PNP0A03:01: host bridge window [io  0xd000-0xdfff] (ignored)
[    0.280030] pci_root PNP0A03:01: host bridge window [mem 0xe9000000-0xefffffff] (ignored)
[    0.280165] PCI: peer root bus 02 res updated from pci conf
[    0.280254] pci 0000:03:04.0: reg 10: [mem 0xecfff000-0xecffffff pref]
[    0.280270] pci 0000:03:04.0: reg 14: [io  0xdce0-0xdcff]
[    0.280284] pci 0000:03:04.0: reg 18: [mem 0xeef00000-0xeeffffff]
[    0.280317] pci 0000:03:04.0: reg 30: [mem 0xef000000-0xef0fffff pref]
[    0.280351] pci 0000:03:04.0: supports D1 D2
[    0.280360] pci 0000:03:04.0: PME# supported from D0 D1 D2 D3hot
[    0.280371] pci 0000:03:04.0: PME# disabled
[    0.280440] pci 0000:03:05.0: reg 10: [mem 0xecffe000-0xecffefff pref]
[    0.280455] pci 0000:03:05.0: reg 14: [io  0xdcc0-0xdcdf]
[    0.280470] pci 0000:03:05.0: reg 18: [mem 0xeee00000-0xeeefffff]
[    0.280501] pci 0000:03:05.0: reg 30: [mem 0xef000000-0xef0fffff pref]
[    0.280532] pci 0000:03:05.0: supports D1 D2
[    0.280540] pci 0000:03:05.0: PME# supported from D0 D1 D2 D3hot
[    0.280549] pci 0000:03:05.0: PME# disabled
[    0.280608] pci 0000:02:0a.0: PCI bridge to [bus 03-03]
[    0.280621] pci 0000:02:0a.0:   bridge window [io  0xd000-0xdfff]
[    0.280631] pci 0000:02:0a.0:   bridge window [mem 0xee000000-0xefffffff]
[    0.280645] pci 0000:02:0a.0:   bridge window [mem 0xeb000000-0xecffffff 64bit pref]
[    0.280661] pci_bus 0000:02: on NUMA node 0
[    0.280675] ACPI: PCI Interrupt Routing Table [\_SB_.PCI1._PRT]
[    0.282311] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 *10 11 12 14)
[    0.282822] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 *11 12 14)
[    0.283324] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 11 12 14) *0, disabled.
[    0.283834] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 11 12 14) *0, disabled.
[    0.284355] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14) *0, disabled.
[    0.284853] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 14) *0, disabled.
[    0.285352] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11 12 14) *0, disabled.
[    0.285844] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 11 12 14) *0, disabled.
[    0.286351] ACPI: PCI Interrupt Link [LNKI] (IRQs 3 4 5 6 7 9 10 *11 12 14)
[    0.286851] ACPI: PCI Interrupt Link [LNKJ] (IRQs 3 4 5 6 7 9 *10 11 12 14)
[    0.287343] ACPI: PCI Interrupt Link [LNKK] (IRQs 3 4 5 6 7 9 10 11 12 14) *0, disabled.
[    0.287837] ACPI: PCI Interrupt Link [LNKL] (IRQs 3 4 5 6 7 9 10 11 12 14) *0, disabled.
[    0.288367] ACPI: PCI Interrupt Link [LNKM] (IRQs 3 4 5 6 7 9 10 11 12 14) *0, disabled.
[    0.288874] ACPI: PCI Interrupt Link [LNKN] (IRQs 3 4 5 6 7 9 10 11 12 14) *0, disabled.
[    0.289393] ACPI: PCI Interrupt Link [LNKO] (IRQs 3 4 5 6 7 9 10 11 12 *14)
[    0.289891] ACPI: PCI Interrupt Link [LNKP] (IRQs 3 4 5 6 7 9 10 11 12 *14)
[    0.290399] ACPI: PCI Interrupt Link [LUSB] (IRQs 3 4 *5 6 7 10 11 12 14)
[    0.290605] HEST: Table is not found!
[    0.290865] vgaarb: device added: PCI:0000:00:0e.0,decodes=io+mem,owns=io+mem,locks=none
[    0.290889] vgaarb: loaded
[    0.291495] SCSI subsystem initialized
[    0.291820] libata version 3.00 loaded.
[    0.292028] usbcore: registered new interface driver usbfs
[    0.292073] usbcore: registered new interface driver hub
[    0.292157] usbcore: registered new device driver usb
[    0.292669] ACPI: WMI: Mapper loaded
[    0.292678] PCI: Using ACPI for IRQ routing
[    0.292701] PCI: pci_cache_line_size set to 32 bytes
[    0.292725] pci 0000:00:02.0: no compatible bridge window for [io  0xf000-0xffff]
[    0.292736] pci 0000:00:02.0: no compatible bridge window for [mem 0xfc000000-0xfdffffff]
[    0.292748] pci 0000:00:02.0: no compatible bridge window for [mem 0xfa000000-0xfaffffff pref]
[    0.292759] pci 0000:02:0a.0: no compatible bridge window for [io  0xd000-0xdfff]
[    0.292769] pci 0000:02:0a.0: no compatible bridge window for [mem 0xee000000-0xefffffff]
[    0.292779] pci 0000:02:0a.0: no compatible bridge window for [mem 0xeb000000-0xecffffff 64bit pref]
[    0.292811] pci 0000:00:02.1: no compatible bridge window for [mem 0xf4000000-0xf7ffffff pref]
[    0.292828] pci 0000:00:04.0: no compatible bridge window for [mem 0xfe103000-0xfe103fff]
[    0.292844] pci 0000:00:08.0: no compatible bridge window for [mem 0xfe102000-0xfe102fff]
[    0.292855] pci 0000:00:08.0: no compatible bridge window for [mem 0xfe000000-0xfe0fffff]
[    0.292870] pci 0000:00:0e.0: no compatible bridge window for [mem 0xf9000000-0xf9ffffff pref]
[    0.292881] pci 0000:00:0e.0: no compatible bridge window for [mem 0xfe101000-0xfe101fff]
[    0.292899] pci 0000:00:0f.2: no compatible bridge window for [mem 0xfe100000-0xfe100fff]
[    0.292913] pci 0000:01:06.0: no compatible bridge window for [io  0xfc00-0xfcff]
[    0.292923] pci 0000:01:06.0: no compatible bridge window for [mem 0xfcfff000-0xfcffffff]
[    0.292941] pci 0000:03:04.0: no compatible bridge window for [mem 0xecfff000-0xecffffff pref]
[    0.292951] pci 0000:03:04.0: no compatible bridge window for [io  0xdce0-0xdcff]
[    0.292960] pci 0000:03:04.0: no compatible bridge window for [mem 0xeef00000-0xeeffffff]
[    0.292975] pci 0000:03:05.0: no compatible bridge window for [mem 0xecffe000-0xecffefff pref]
[    0.292985] pci 0000:03:05.0: no compatible bridge window for [io  0xdcc0-0xdcdf]
[    0.292994] pci 0000:03:05.0: no compatible bridge window for [mem 0xeee00000-0xeeefffff]
[    0.293052] reserve RAM buffer: 0000000000002000 - 000000000000ffff 
[    0.293063] reserve RAM buffer: 000000002fffe000 - 000000002fffffff 
[    0.293404] NetLabel: Initializing
[    0.293411] NetLabel:  domain hash size = 128
[    0.293417] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.293469] NetLabel:  unlabeled traffic allowed by default
[    0.293622] Switching to clocksource tsc
[    0.330649] AppArmor: AppArmor Filesystem Enabled
[    0.330718] pnp: PnP ACPI init
[    0.330784] ACPI: bus type pnp registered
[    0.344990] pnp 00:0b: disabling [io  0x00e0-0x00ef] because it overlaps 0000:01:06.0 BAR 0 [io  0x0000-0x00ff]
[    0.353657] pnp 00:0d: disabling [mem 0x00000000-0x0009ffff] because it overlaps 0000:00:02.1 BAR 0 [mem 0x00000000-0x03ffffff pref]
[    0.353673] pnp 00:0d: disabling [mem 0x00100000-0x00ffffff] because it overlaps 0000:00:02.1 BAR 0 [mem 0x00000000-0x03ffffff pref]
[    0.353686] pnp 00:0d: disabling [mem 0x01000000-0x2fffffff] because it overlaps 0000:00:02.1 BAR 0 [mem 0x00000000-0x03ffffff pref]
[    0.353700] pnp 00:0d: disabling [mem 0x000f0000-0x000fffff] because it overlaps 0000:00:02.1 BAR 0 [mem 0x00000000-0x03ffffff pref]
[    0.353722] pnp 00:0d: disabling [mem 0x00000000-0x0009ffff disabled] because it overlaps 0000:00:08.0 BAR 2 [mem 0x00000000-0x000fffff]
[    0.353736] pnp 00:0d: disabling [mem 0x000f0000-0x000fffff disabled] because it overlaps 0000:00:08.0 BAR 2 [mem 0x00000000-0x000fffff]
[    0.353754] pnp 00:0d: disabling [mem 0x00000000-0x0009ffff disabled] because it overlaps 0000:00:0e.0 BAR 0 [mem 0x00000000-0x00ffffff pref]
[    0.353768] pnp 00:0d: disabling [mem 0x00100000-0x00ffffff disabled] because it overlaps 0000:00:0e.0 BAR 0 [mem 0x00000000-0x00ffffff pref]
[    0.353782] pnp 00:0d: disabling [mem 0x000f0000-0x000fffff disabled] because it overlaps 0000:00:0e.0 BAR 0 [mem 0x00000000-0x00ffffff pref]
[    0.353815] pnp 00:0d: disabling [mem 0x00000000-0x0009ffff disabled] because it overlaps 0000:03:04.0 BAR 2 [mem 0x00000000-0x000fffff]
[    0.353829] pnp 00:0d: disabling [mem 0x000f0000-0x000fffff disabled] because it overlaps 0000:03:04.0 BAR 2 [mem 0x00000000-0x000fffff]
[    0.353848] pnp 00:0d: disabling [mem 0x00000000-0x0009ffff disabled] because it overlaps 0000:03:05.0 BAR 2 [mem 0x00000000-0x000fffff]
[    0.353862] pnp 00:0d: disabling [mem 0x000f0000-0x000fffff disabled] because it overlaps 0000:03:05.0 BAR 2 [mem 0x00000000-0x000fffff]
[    0.357075] pnp: PnP ACPI: found 14 devices
[    0.357082] ACPI: ACPI bus type pnp unregistered
[    0.357094] PnPBIOS: Disabled by ACPI PNP
[    0.357158] system 00:0b: [io  0x0814-0x085b] has been reserved
[    0.357169] system 00:0b: [io  0x0580-0x058f] has been reserved
[    0.357179] system 00:0b: [io  0x0c00-0x0cd7] has been reserved
[    0.357189] system 00:0b: [io  0x0f50-0x0f58] has been reserved
[    0.357200] system 00:0b: [io  0x2c00-0x2c7f] has been reserved
[    0.357225] system 00:0d: [mem 0xfec00000-0xfec0ffff] could not be reserved
[    0.357237] system 00:0d: [mem 0xfee00000-0xfee0ffff] has been reserved
[    0.357247] system 00:0d: [mem 0xffe00000-0xffffffff] could not be reserved
[    0.397239] pci 0000:00:02.1: no compatible bridge window for [mem 0xfb000000-0xfb00ffff pref]
[    0.397256] pci 0000:00:04.0: no compatible bridge window for [mem 0xfb000000-0xfb003fff pref]
[    0.397270] pci 0000:00:08.0: no compatible bridge window for [mem 0xfb000000-0xfb0fffff pref]
[    0.397291] pci 0000:01:06.0: no compatible bridge window for [mem 0xfd000000-0xfd00ffff pref]
[    0.397308] pci 0000:03:04.0: no compatible bridge window for [mem 0xef000000-0xef0fffff pref]
[    0.397321] pci 0000:03:05.0: no compatible bridge window for [mem 0xef000000-0xef0fffff pref]
[    0.397391] pci 0000:00:02.1: BAR 0: trying firmware assignment [mem 0xf4000000-0xf7ffffff pref]
[    0.397405] pci 0000:00:02.1: BAR 0: assigned [mem 0xf4000000-0xf7ffffff pref]
[    0.397420] pci 0000:00:02.1: BAR 0: set to [mem 0xf4000000-0xf7ffffff pref] (PCI address [0xf4000000-0xf7ffffff]
[    0.397434] pci 0000:00:0e.0: BAR 0: trying firmware assignment [mem 0xf9000000-0xf9ffffff pref]
[    0.397444] pci 0000:00:0e.0: BAR 0: assigned [mem 0xf9000000-0xf9ffffff pref]
[    0.397457] pci 0000:00:0e.0: BAR 0: set to [mem 0xf9000000-0xf9ffffff pref] (PCI address [0xf9000000-0xf9ffffff]
[    0.397470] pci 0000:00:02.0: BAR 14: can't assign mem (size 0x100000)
[    0.397481] pci 0000:00:02.0: BAR 15: can't assign mem pref (size 0x100000)
[    0.397491] pci 0000:00:08.0: BAR 2: trying firmware assignment [mem 0xfe000000-0xfe0fffff]
[    0.397501] pci 0000:00:08.0: BAR 2: assigned [mem 0xfe000000-0xfe0fffff]
[    0.397514] pci 0000:00:08.0: BAR 2: set to [mem 0xfe000000-0xfe0fffff] (PCI address [0xfe000000-0xfe0fffff]
[    0.397526] pci 0000:00:08.0: BAR 6: can't assign mem pref (size 0x100000)
[    0.397536] pci 0000:00:0e.0: BAR 6: can't assign mem pref (size 0x20000)
[    0.397547] pci 0000:00:02.1: BAR 6: can't assign mem pref (size 0x10000)
[    0.397557] pci 0000:00:04.0: BAR 6: can't assign mem pref (size 0x4000)
[    0.397569] pci 0000:00:02.0: BAR 13: can't assign io (size 0x1000)
[    0.397579] pci 0000:00:04.0: BAR 1: trying firmware assignment [mem 0xfe103000-0xfe103fff]
[    0.397590] pci 0000:00:04.0: BAR 1: assigned [mem 0xfe103000-0xfe103fff]
[    0.397603] pci 0000:00:04.0: BAR 1: set to [mem 0xfe103000-0xfe103fff] (PCI address [0xfe103000-0xfe103fff]
[    0.397615] pci 0000:00:08.0: BAR 0: trying firmware assignment [mem 0xfe102000-0xfe102fff]
[    0.397625] pci 0000:00:08.0: BAR 0: assigned [mem 0xfe102000-0xfe102fff]
[    0.397638] pci 0000:00:08.0: BAR 0: set to [mem 0xfe102000-0xfe102fff] (PCI address [0xfe102000-0xfe102fff]
[    0.397650] pci 0000:00:0e.0: BAR 2: trying firmware assignment [mem 0xfe101000-0xfe101fff]
[    0.397660] pci 0000:00:0e.0: BAR 2: assigned [mem 0xfe101000-0xfe101fff]
[    0.397673] pci 0000:00:0e.0: BAR 2: set to [mem 0xfe101000-0xfe101fff] (PCI address [0xfe101000-0xfe101fff]
[    0.397685] pci 0000:00:0f.2: BAR 0: trying firmware assignment [mem 0xfe100000-0xfe100fff]
[    0.397695] pci 0000:00:0f.2: BAR 0: assigned [mem 0xfe100000-0xfe100fff]
[    0.397707] pci 0000:00:0f.2: BAR 0: set to [mem 0xfe100000-0xfe100fff] (PCI address [0xfe100000-0xfe100fff]
[    0.397720] pci 0000:01:06.0: BAR 6: can't assign mem pref (size 0x10000)
[    0.397731] pci 0000:01:06.0: BAR 1: trying firmware assignment [mem 0xfcfff000-0xfcffffff]
[    0.397742] pci 0000:01:06.0: BAR 1: assigned [mem 0xfcfff000-0xfcffffff]
[    0.397757] pci 0000:01:06.0: BAR 1: set to [mem 0xfcfff000-0xfcffffff] (PCI address [0xfcfff000-0xfcffffff]
[    0.397768] pci 0000:01:06.0: BAR 0: trying firmware assignment [io  0xfc00-0xfcff]
[    0.397783] pci 0000:01:06.0: BAR 0: [io  0xfc00-0xfcff] conflicts with  [io  0xe000-0xfffc]
[    0.397793] pci 0000:01:06.0: BAR 0: can't assign io (size 0x100)
[    0.397804] pci 0000:00:02.0: PCI bridge to [bus 01-01]
[    0.397812] pci 0000:00:02.0:   bridge window [io  disabled]
[    0.397825] pci 0000:00:02.0:   bridge window [mem disabled]
[    0.397835] pci 0000:00:02.0:   bridge window [mem pref disabled]
[    0.397871] pci 0000:02:0a.0: BAR 14: can't assign mem (size 0x200000)
[    0.397881] pci 0000:02:0a.0: BAR 15: can't assign mem pref (size 0x300000)
[    0.397891] pci 0000:02:0a.0: BAR 13: can't assign io (size 0x1000)
[    0.397904] pci 0000:03:04.0: BAR 2: trying firmware assignment [mem 0xeef00000-0xeeffffff]
[    0.397915] pci 0000:03:04.0: BAR 2: assigned [mem 0xeef00000-0xeeffffff]
[    0.397929] pci 0000:03:04.0: BAR 2: set to [mem 0xeef00000-0xeeffffff] (PCI address [0xeef00000-0xeeffffff]
[    0.397940] pci 0000:03:04.0: BAR 6: can't assign mem pref (size 0x100000)
[    0.397950] pci 0000:03:05.0: BAR 2: trying firmware assignment [mem 0xeee00000-0xeeefffff]
[    0.397960] pci 0000:03:05.0: BAR 2: assigned [mem 0xeee00000-0xeeefffff]
[    0.397973] pci 0000:03:05.0: BAR 2: set to [mem 0xeee00000-0xeeefffff] (PCI address [0xeee00000-0xeeefffff]
[    0.397984] pci 0000:03:05.0: BAR 6: can't assign mem pref (size 0x100000)
[    0.397993] pci 0000:03:04.0: BAR 0: trying firmware assignment [mem 0xecfff000-0xecffffff pref]
[    0.398004] pci 0000:03:04.0: BAR 0: assigned [mem 0xecfff000-0xecffffff pref]
[    0.398018] pci 0000:03:04.0: BAR 0: set to [mem 0xecfff000-0xecffffff pref] (PCI address [0xecfff000-0xecffffff]
[    0.398029] pci 0000:03:05.0: BAR 0: trying firmware assignment [mem 0xecffe000-0xecffefff pref]
[    0.398039] pci 0000:03:05.0: BAR 0: assigned [mem 0xecffe000-0xecffefff pref]
[    0.398053] pci 0000:03:05.0: BAR 0: set to [mem 0xecffe000-0xecffefff pref] (PCI address [0xecffe000-0xecffefff]
[    0.398064] pci 0000:03:04.0: BAR 1: trying firmware assignment [io  0xdce0-0xdcff]
[    0.398075] pci 0000:03:04.0: BAR 1: [io  0xdce0-0xdcff] conflicts with  [io  0xd000-0xdffc]
[    0.398085] pci 0000:03:04.0: BAR 1: can't assign io (size 0x20)
[    0.398094] pci 0000:03:05.0: BAR 1: trying firmware assignment [io  0xdcc0-0xdcdf]
[    0.398105] pci 0000:03:05.0: BAR 1: [io  0xdcc0-0xdcdf] conflicts with  [io  0xd000-0xdffc]
[    0.398114] pci 0000:03:05.0: BAR 1: can't assign io (size 0x20)
[    0.398122] pci 0000:02:0a.0: PCI bridge to [bus 03-03]
[    0.398129] pci 0000:02:0a.0:   bridge window [io  disabled]
[    0.398139] pci 0000:02:0a.0:   bridge window [mem disabled]
[    0.398148] pci 0000:02:0a.0:   bridge window [mem pref disabled]
[    0.398172] pci_bus 0000:00: resource 4 [io  0x01f0-0x01f7]
[    0.398180] pci_bus 0000:00: resource 5 [io  0x03f6]
[    0.398188] pci_bus 0000:00: resource 6 [io  0x0170-0x0177]
[    0.398196] pci_bus 0000:00: resource 7 [io  0x0376]
[    0.398204] pci_bus 0000:00: resource 8 [io  0xffa0-0xffaf]
[    0.398213] pci_bus 0000:00: resource 9 [mem 0xfffffffff0000000-0xfffffffffe10ffff]
[    0.398223] pci_bus 0000:00: resource 10 [io  0xe000-0xfffc]
[    0.398233] pci_bus 0000:02: resource 4 [mem 0xffffffffe9000000-0xffffffffefffffff]
[    0.398242] pci_bus 0000:02: resource 5 [io  0xd000-0xdffc]
[    0.398391] NET: Registered protocol family 2
[    0.398643] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.399773] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.405430] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.408314] TCP: Hash tables configured (established 131072 bind 65536)
[    0.408333] TCP reno registered
[    0.408362] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.408452] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.408902] NET: Registered protocol family 1
[    0.408972] PCI: CLS mismatch (32 != 64), using 32 bytes
[    0.409026] pci 0000:00:08.0: Firmware left e100 interrupts enabled; disabling
[    0.409045] pci 0000:00:0e.0: Boot video device
[    0.409644] cpufreq-nforce2: No nForce2 chipset.
[    0.409755] Scanning for low memory corruption every 60 seconds
[    0.410561] audit: initializing netlink socket (disabled)
[    0.410597] type=2000 audit(1297909908.408:1): initialized
[    0.440972] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.446459] VFS: Disk quotas dquot_6.5.2
[    0.446726] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.449333] fuse init (API version 7.14)
[    0.449697] msgmni has been set to 1475
[    0.451043] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.451056] io scheduler noop registered
[    0.451063] io scheduler deadline registered
[    0.451123] io scheduler cfq registered (default)
[    0.451538] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.451615] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.452238] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    0.452258] ACPI: Power Button [PWRF]
[    0.452715] ACPI: acpi_idle registered with cpuidle
[    0.459043] ERST: Table is not found!
[    0.459600] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.459819] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.460196] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    0.461015] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.461344] 00:08: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    0.465532] brd: module loaded
[    0.467037] isapnp: Scanning for PnP cards...
[    0.467609] loop: module loaded
[    0.469527] Fixed MDIO Bus: probed
[    0.469652] PPP generic driver version 2.4.2
[    0.469828] tun: Universal TUN/TAP device driver, 1.6
[    0.469837] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.470126] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.470189] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.471120] ACPI: PCI Interrupt Link [LUSB] enabled at IRQ 11
[    0.471154] ohci_hcd 0000:00:0f.2: PCI INT A -> Link[LUSB] -> GSI 11 (level, low) -> IRQ 11
[    0.471199] ohci_hcd 0000:00:0f.2: OHCI Host Controller
[    0.471374] ohci_hcd 0000:00:0f.2: new USB bus registered, assigned bus number 1
[    0.471434] ohci_hcd 0000:00:0f.2: irq 11, io mem 0xfe100000
[    0.529098] hub 1-0:1.0: USB hub found
[    0.529121] hub 1-0:1.0: 4 ports detected
[    0.529346] uhci_hcd: USB Universal Host Controller Interface driver
[    0.529707] PNP: PS/2 Controller [PNP0303:KBD,PNP0f13:MOU] at 0x60,0x64 irq 1,12
[    0.539124] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.539157] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.539658] mice: PS/2 mouse device common for all mice
[    0.540030] rtc_cmos 00:0a: RTC can wake from S4
[    0.540170] rtc_cmos 00:0a: rtc core: registered rtc_cmos as rtc0
[    0.540231] rtc0: alarms up to one day, y3k, 242 bytes nvram
[    0.540707] device-mapper: uevent: version 1.0.3
[    0.560401] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: dm-devel@redhat.com
[    0.571430] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    0.610383] device-mapper: multipath: version 1.1.1 loaded
[    0.610398] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.627470] EISA: Probing bus 0 at eisa.0
[    0.627488] EISA: Cannot allocate resource for mainboard
[    0.627508] Cannot allocate resource for EISA slot 2
[    0.627559] EISA: Detected 0 cards.
[    0.734165] cpuidle: using governor ladder
[    0.734177] cpuidle: using governor menu
[    0.735460] TCP cubic registered
[    0.736081] NET: Registered protocol family 10
[    0.737460] lo: Disabled Privacy Extensions
[    0.738430] NET: Registered protocol family 17
[    0.738615] Using IPI No-Shortcut mode
[    0.738939] PM: Resume from disk failed.
[    0.738977] registered taskstats version 1
[    0.739399]   Magic number: 15:936:510
[    0.739595] rtc_cmos 00:0a: setting system clock to 2011-02-17 02:31:49 UTC (1297909909)
[    0.739605] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.739612] EDD information not available.
[    0.820596] isapnp: No Plug & Play device found
[    0.902447] usb 1-1: new low speed USB device using ohci_hcd and address 2
[    1.078782] Freeing initrd memory: 10488k freed
[    1.108667] Freeing unused kernel memory: 704k freed
[    1.110933] Write protecting the kernel text: 5088k
[    1.111207] Write protecting the kernel read-only data: 2012k
[    1.175880] udev[75]: starting version 163
[    1.431649] Adaptec aacraid driver 1.1-5[26400]-ms
[    1.431740]   alloc irq_desc for 31 on node -1
[    1.431748]   alloc kstat_irqs on node -1
[    1.431776] aacraid 0000:00:02.1: PCI INT A -> GSI 31 (level, low) -> IRQ 31
[    1.519828] e100: Intel(R) PRO/100 Network Driver, 3.5.24-k2-NAPI
[    1.519840] e100: Copyright(c) 1999-2006 Intel Corporation
[    1.524684] AAC0: kernel 2.1-3[2939] 
[    1.524697] AAC0: monitor 2.1-3[2939]
[    1.524705] AAC0: bios 2.1-3[2939]
[    1.524715] AAC0: serial 493446D0
[    1.526370] scsi0 : percraid
[    1.546363]   alloc irq_desc for 16 on node -1
[    1.546373]   alloc kstat_irqs on node -1
[    1.546399] e100 0000:00:08.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.569167] e100 0000:00:08.0: PME# disabled
[    1.571696] scsi 0:0:0:0: Direct-Access     DELL     Inventory        V1.0 PQ: 0 ANSI: 2
[    1.579644] Floppy drive(s): fd0 is 1.44M
[    1.591948]   alloc irq_desc for 30 on node -1
[    1.591961]   alloc kstat_irqs on node -1
[    1.591987] aic7xxx 0000:01:06.0: PCI INT A -> GSI 30 (level, low) -> IRQ 30
[    1.592119] aic7xxx: PCI Device 1:6:0 failed memory mapped test.  Using PIO.
[    1.592134] aic7xxx: PCI1:6:0 IO region 0x0[0..255] unavailable. Cannot map device.
[    1.592158] aic7xxx: probe of 0000:01:06.0 failed with error -12
[    1.596150] FDC 0 is a National Semiconductor PC87306
[    1.619585] e100 0000:00:08.0: eth0: addr 0xfe102000, irq 16, MAC addr 00:b0:d0:21:1b:68
[    1.619691]   alloc irq_desc for 24 on node -1
[    1.619699]   alloc kstat_irqs on node -1
[    1.619725] e100 0000:03:04.0: PCI INT A -> GSI 24 (level, low) -> IRQ 24
[    1.656005] scsi 0:1:0:0: Direct-Access     SEAGATE  ST318203LC       0001 PQ: 0 ANSI: 2
[    1.658284] usbcore: registered new interface driver hiddev
[    1.662871] scsi 0:1:1:0: Direct-Access     SEAGATE  ST318203LC       0001 PQ: 0 ANSI: 2
[    1.667359] input: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) as /devices/pci0000:00/0000:00:0f.2/usb1/1-1/1-1:1.0/input/input2
[    1.668102] generic-usb 0003:045E:0040.0001: input,hidraw0: USB HID v1.10 Mouse [Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)] on usb-0000:00:0f.2-1/input0
[    1.668753] usbcore: registered new interface driver usbhid
[    1.668765] usbhid: USB HID core driver
[    1.679071] scsi 0:1:2:0: Direct-Access     SEAGATE  ST318203LC       0001 PQ: 0 ANSI: 2
[    1.683363] scsi 0:1:3:0: Direct-Access     SEAGATE  ST318203LC       0001 PQ: 0 ANSI: 2
[    1.688826] scsi 0:1:4:0: Direct-Access     SEAGATE  ST318406LC       8A03 PQ: 0 ANSI: 3
[    1.692685] scsi 0:1:5:0: Direct-Access     SEAGATE  ST318404LC       0002 PQ: 0 ANSI: 3
[    1.706014] e100 0000:03:04.0: (unregistered net_device): EEPROM corrupted
[    1.706049] e100 0000:03:04.0: PCI INT A disabled
[    1.706071] e100: probe of 0000:03:04.0 failed with error -11
[    1.706116]   alloc irq_desc for 25 on node -1
[    1.706123]   alloc kstat_irqs on node -1
[    1.706140] e100 0000:03:05.0: PCI INT A -> GSI 25 (level, low) -> IRQ 25
[    1.707320] scsi 0:1:6:0: Processor         DELL     1x6 U2W SCSI BP  5.24 PQ: 0 ANSI: 2
[    1.791111] e100 0000:03:05.0: (unregistered net_device): EEPROM corrupted
[    1.791136] e100 0000:03:05.0: PCI INT A disabled
[    1.791152] e100: probe of 0000:03:05.0 failed with error -11
[    3.793980] sd 0:0:0:0: [sda] 213267456 512-byte logical blocks: (109 GB/101 GiB)
[    3.794089] sd 0:0:0:0: [sda] Write Protect is off
[    3.794100] sd 0:0:0:0: [sda] Mode Sense: 06 00 00 00
[    3.794302] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[    3.794687] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    3.797693]  sda: sda1 sda2 <
[    3.798843] scsi 0:1:0:0: Attached scsi generic sg1 type 0
[    3.799894]  sda5 >
[    3.800090] scsi 0:1:1:0: Attached scsi generic sg2 type 0
[    3.802946] scsi 0:1:2:0: Attached scsi generic sg3 type 0
[    3.804368] sd 0:0:0:0: [sda] Attached SCSI removable disk
[    3.806959] scsi 0:1:3:0: Attached scsi generic sg4 type 0
[    3.810388] scsi 0:1:4:0: Attached scsi generic sg5 type 0
[    3.810906] scsi 0:1:5:0: Attached scsi generic sg6 type 0
[    3.811352] scsi 0:1:6:0: Attached scsi generic sg7 type 3
[    4.211061] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    6.432443] udev[288]: starting version 163
[    6.476527] Adding 2301948k swap on /dev/sda5.  Priority:-1 extents:1 across:2301948k 
[    7.039121] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[    7.228652] piix4_smbus 0000:00:0f.0: SMBus Host Controller at 0x580, revision 0
[    7.346081] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[    7.405083] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    7.581314] Linux agpgart interface v0.103
[    7.633260] type=1400 audit(1297909916.389:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=411 comm="apparmor_parser"
[    7.634663] type=1400 audit(1297909916.389:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=411 comm="apparmor_parser"
[    7.635502] type=1400 audit(1297909916.389:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=411 comm="apparmor_parser"
[    7.641159] agpgart-serverworks 0000:00:00.0: can't determine aperture size
[    7.641231] agpgart-serverworks 0000:00:00.0: agp_backend_initialize() failed
[    7.641250] agpgart-serverworks: probe of 0000:00:00.0 failed with error -22
[    7.641283] agpgart-serverworks 0000:00:00.1: can't determine aperture size
[    7.641336] agpgart-serverworks 0000:00:00.1: agp_backend_initialize() failed
[    7.641349] agpgart-serverworks: probe of 0000:00:00.1 failed with error -22
[    7.697861] lp: driver loaded but no devices found
[    7.716364] parport_pc 00:09: reported by Plug and Play ACPI
[    7.716478] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,ECP]
[    7.812700] lp0: using parport0 (interrupt-driven).
[    7.848523] ppdev: user-space parallel port driver
[    9.166112] ADDRCONF(NETDEV_UP): eth0: link is not ready
[    9.886106] type=1400 audit(1297909918.645:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=673 comm="apparmor_parser"
[    9.887449] type=1400 audit(1297909918.645:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=673 comm="apparmor_parser"
[    9.888234] type=1400 audit(1297909918.645:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=673 comm="apparmor_parser"
[    9.908961] type=1400 audit(1297909918.665:8): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=672 comm="apparmor_parser"
[    9.953489] type=1400 audit(1297909918.709:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=677 comm="apparmor_parser"
[    9.955367] type=1400 audit(1297909918.709:10): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=677 comm="apparmor_parser"
[    9.978751] type=1400 audit(1297909918.737:11): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=674 comm="apparmor_parser"
[   14.474302] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   14.490239] mtrr: Serverworks LE rev < 6 detected. Write-combining disabled.
[   14.490255] mtrr: your processor doesn't support write-combining
[   14.555043] mtrr: no MTRR for f9000000,400000 found
[   14.557586] mtrr: Serverworks LE rev < 6 detected. Write-combining disabled.
[   14.557600] mtrr: your processor doesn't support write-combining
[   21.370250] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
```AND the output of....awww crap I forgot the command....that's ok someone will know this one....actually shows the 7880 as UNCLAIMED (which I think means no driver)......

here's the snippet....
```
           *-scsi UNCLAIMED
                description: SCSI storage controller
                product: AIC-7880U
                vendor: Adaptec
                physical id: 6
                bus info: pci@0000:01:06.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: scsi pm bus_master cap_list
                configuration: latency=32 maxlatency=8 mingnt=8
                resources: memory:fcfff000-fcffffff

```here's the whole thing if you wanted to know...

```
petey
    description: System
    product: PowerEdge 2400
    vendor: Dell Computer Corporation
    serial: H0I4F
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.4 smp
    configuration: boot=normal chassis=server cpus=2 uuid=44454C4C-009B-1048-8030-80C04F493446
  *-core
       description: Motherboard
       physical id: 0
     *-firmware
          description: BIOS
          vendor: Dell Computer Corporation
          physical id: 0
          version: A08 (06/25/2001)
          size: 64KiB
          capacity: 448KiB
          capabilities: isa pci pnp upgrade shadowing escd cdboot bootselect edd int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int5printscreen int9keyboard int14serial int17printer int10video acpi biosbootspecification
     *-cpu:0
          description: CPU
          product: Pentium III (Coppermine)
          vendor: Intel Corp.
          physical id: 400
          bus info: cpu@0
          version: 6.8.6
          slot: Processor 1
          size: 866MHz
          capacity: 1066MHz
          width: 32 bits
          clock: 133MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pse36 mmx fxsr sse
        *-cache:0
             description: L1 cache
             physical id: 700
             size: 32KiB
             capacity: 32KiB
             capabilities: internal write-back
        *-cache:1
             description: L2 cache
             physical id: 701
             size: 256KiB
             capacity: 512KiB
             capabilities: pipeline-burst internal write-back unified
     *-cpu:1
          description: CPU
          product: Pentium III (Coppermine)
          vendor: Intel Corp.
          physical id: 401
          bus info: cpu@1
          version: 6.8.6
          slot: Processor 2
          size: 866MHz
          capacity: 1066MHz
          width: 32 bits
          clock: 133MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pse36 mmx fxsr sse
        *-cache:0
             description: L1 cache
             physical id: 702
             size: 32KiB
             capacity: 32KiB
             capabilities: internal write-back
        *-cache:1
             description: L2 cache
             physical id: 703
             size: 256KiB
             capacity: 512KiB
             capabilities: pipeline-burst internal write-back unified
     *-memory
          description: System Memory
          physical id: 1000
          slot: System board or motherboard
          size: 768MiB
          capacity: 2GiB
        *-bank:0
             description: DIMM SDRAM Synchronous 100 MHz (10.0 ns)
             physical id: 0
             slot: DIMM_A
             size: 256MiB
             width: 64 bits
             clock: 100MHz (10.0ns)
        *-bank:1
             description: DIMM SDRAM Synchronous 100 MHz (10.0 ns)
             physical id: 1
             slot: DIMM_B
             size: 256MiB
             width: 64 bits
             clock: 100MHz (10.0ns)
        *-bank:2
             description: DIMM SDRAM Synchronous 100 MHz (10.0 ns)
             physical id: 2
             slot: DIMM_C
             size: 256MiB
             width: 64 bits
             clock: 100MHz (10.0ns)
        *-bank:3
             description: DIMM SDRAM Synchronous 100 MHz (10.0 ns) [empty]
             physical id: 3
             slot: DIMM_D
             width: 64 bits
             clock: 100MHz (10.0ns)
     *-pci:0
          description: Host bridge
          product: CNB20LE Host Bridge
          vendor: Broadcom
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 05
          width: 32 bits
          clock: 33MHz
          configuration: latency=32
        *-pci
             description: PCI bridge
             product: 80960RM (i960RM) Bridge
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm normal_decode bus_master
           *-scsi UNCLAIMED
                description: SCSI storage controller
                product: AIC-7880U
                vendor: Adaptec
                physical id: 6
                bus info: pci@0000:01:06.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: scsi pm bus_master cap_list
                configuration: latency=32 maxlatency=8 mingnt=8
                resources: memory:fcfff000-fcffffff
        *-storage
             description: RAID bus controller
             product: PowerEdge Expandable RAID Controller 2/Si
             vendor: Dell
             physical id: 2.1
             bus info: pci@0000:00:02.1
             logical name: scsi0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: storage pm bus_master emulated
             configuration: driver=aacraid latency=32
             resources: irq:31 memory:f4000000-f7ffffff
           *-disk:0
                description: SCSI Disk
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                size: 101GiB (109GB)
                capabilities: partitioned partitioned:dos
                configuration: signature=0005472f
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: 495bdd8e-d0ee-4620-a9a9-d148350108ce
                   size: 99GiB
                   capacity: 99GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2011-02-13 15:03:01 filesystem=ext4 lastmountpoint=/&#65533;.&#65533;0&#65533;&#65533;C&#65533;&#65533;8&#65533;&#65533;P&#65533;&#65533;&#65533;&#65533;"&#65533;C&#65533;&#65533;@&#65533;&#65533;&#65533;&#65533;'v&#65533;&#65533;'v&#65533;0&#65533;&#65533;h&#65533;&#65533;&#65533;"&#65533; modified=2011-02-13 15:31:09 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2011-02-15 20:44:38 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 2248MiB
                   capacity: 2248MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 2248MiB
                      capabilities: nofs
           *-disk:1 UNCLAIMED
                description: SCSI Disk
                physical id: 1.0.0
                bus info: scsi@0:1.0.0
           *-disk:2 UNCLAIMED
                description: SCSI Disk
                physical id: 1.1.0
                bus info: scsi@0:1.1.0
           *-disk:3 UNCLAIMED
                description: SCSI Disk
                physical id: 1.2.0
                bus info: scsi@0:1.2.0
           *-disk:4 UNCLAIMED
                description: SCSI Disk
                physical id: 1.3.0
                bus info: scsi@0:1.3.0
           *-disk:5 UNCLAIMED
                description: SCSI Disk
                physical id: 1.4.0
                bus info: scsi@0:1.4.0
           *-disk:6 UNCLAIMED
                description: SCSI Disk
                physical id: 1.5.0
                bus info: scsi@0:1.5.0
           *-processor UNCLAIMED
                description: SCSI Processor
                product: 1x6 U2W SCSI BP
                vendor: DELL
                physical id: 1.6.0
                bus info: scsi@0:1.6.0
                version: 5.24
                configuration: ansiversion=2
        *-generic UNCLAIMED
             description: System peripheral
             product: MegaRAC
             vendor: American Megatrends Inc.
             physical id: 4
             bus info: pci@0000:00:04.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: latency=32
             resources: ioport:ec80(size=128) memory:fe103000-fe103fff
        *-network
             description: Ethernet interface
             product: 82557/8/9/0/1 Ethernet Pro 100
             vendor: Intel Corporation
             physical id: 8
             bus info: pci@0000:00:08.0
             logical name: eth0
             version: 08
             serial: 00:b0:d0:21:1b:68
             size: 100MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=full firmware=N/A ip=192.168.1.104 latency=32 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100MB/s
             resources: irq:16 memory:fe102000-fe102fff ioport:ec40(size=64) memory:fe000000-fe0fffff
        *-display UNCLAIMED
             description: VGA compatible controller
             product: 3D Rage IIC
             vendor: ATI Technologies Inc
             physical id: e
             bus info: pci@0000:00:0e.0
             version: 7a
             width: 32 bits
             clock: 33MHz
             capabilities: pm vga_controller bus_master cap_list
             configuration: latency=32 mingnt=8
             resources: memory:f9000000-f9ffffff ioport:e800(size=256) memory:fe101000-fe101fff
        *-isa
             description: ISA bridge
             product: OSB4 South Bridge
             vendor: Broadcom
             physical id: f
             bus info: pci@0000:00:0f.0
             version: 4f
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: driver=piix4_smbus latency=0
             resources: irq:0
        *-usb
             description: USB Controller
             product: OSB4/CSB5 OHCI USB Controller
             vendor: Broadcom
             physical id: f.2
             bus info: pci@0000:00:0f.2
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=32 maxlatency=80
             resources: irq:11 memory:fe100000-fe100fff
     *-pci:1
          description: Host bridge
          product: CNB20LE Host Bridge
          vendor: Broadcom
          physical id: 101
          bus info: pci@0000:00:00.1
          version: 05
          width: 32 bits
          clock: 33MHz
          configuration: latency=32
     *-pci:2
          description: PCI bridge
          product: DECchip 21152
          vendor: Digital Equipment Corporation
          physical id: a
          bus info: pci@0000:02:0a.0
          version: 03
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm normal_decode bus_master cap_list
        *-network:0 UNCLAIMED
             description: Ethernet controller
             product: 82557/8/9/0/1 Ethernet Pro 100
             vendor: Intel Corporation
             physical id: 4
             bus info: pci@0000:03:04.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: latency=32 maxlatency=56 mingnt=8
             resources: memory:ecfff000-ecffffff memory:eef00000-eeffffff
        *-network:1 UNCLAIMED
             description: Ethernet controller
             product: 82557/8/9/0/1 Ethernet Pro 100
             vendor: Intel Corporation
             physical id: 5
             bus info: pci@0000:03:05.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: latency=32 maxlatency=56 mingnt=8
             resources: memory:ecffe000-ecffefff memory:eee00000-eeefffff
```so, with many hours of patience and google searching (and yes ALL hardware shows up on bios post, and I can ctrl+A into the config bios to play with the hardware a bit)  I have only found this cryptic page:

[http://manpages.ubuntu.com/manpages/gutsy/man4/ahc.4.html](http://manpages.ubuntu.com/manpages/gutsy/man4/ahc.4.html)

which seems to be hijacked 40 different ways around the net talking about
```
"ahc - Adaptec VL/EISA/PCI SCSI host adapter driver"
```which is exactly what I need to make this crap work! (I think/hope)

however....the cryptic part is the directive....
```
to load the driver as a module at boot time, place the
      following lines in [loader.conf(5)]("http://manpages.ubuntu.com/manpages/gutsy/man5/loader.conf.5.html"):
            ahc_load="YES"
            ahc_eisa_load="YES"
            ahc_isa_load="YES"
            ahc_pci_load="YES"

```The problem with that is there's no loader.conf that I can find...
...with a few more google searches I see it "should" be in /boot 
and there also should be a loader.rc with a few fancy commands in it
...but, alas, even creating those files in those places do not help...

...and, in the same "man" page, I have no clue what is meant by...

```
      To compile this driver into the kernel, place the following lines in your
      kernel configuration file:
 
            device scbus
            device ahc
 
            For one or more VL/EISA cards:
            device eisa
 
            For one or more PCI cards:
            device pci
 
            To allow PCI adapters to use memory mapped I/O if enabled:
            options AHC_ALLOW_MEMIO
 
            To configure one or more controllers to assume the target role:
            options AHC_TMODE_ENABLE <bitmask of units>

```soooooo I'm at a loss. Please HELP! 

I know I'm going to be kicking myself if one of you 
come out with a 10 character command to solve this. ](*,)

---

### Post by hockey_man3 on 2011-02-18
Bump....anyone?

---

### Post by tgalati4 on 2011-02-18
Did you make a file called loader.conf?

cd /boot
sudo nano loader.conf

Cut and paste the following:

 ahc_load="YES"
 ahc_eisa_load="YES"
 ahc_isa_load="YES"
 ahc_pci_load="YES"

Control-O (return) Control-X (return)

Reboot.

Have you upgraded the BIOS to the latest?  Check Dell's support page.  Put in the service tag and look in the downloads section.  You probably need to update the main BIOS and the SCSI BIOS.  Then boot into the SCSI BIOS and see what switches are available.

---

### Post by hockey_man3 on 2011-02-18
Yeah, i did do the loader.conf file deal as stated in the post and have rebooted to the same problem.....however, i'm somewhat skeptical to upgrade the hardware firmware since the cdrom drive on the scsi bus that's in question worked when i installed 10.10 using a cd

---

### Post by hockey_man3 on 2011-02-20
Bump........anyone else with a suggestion of howto install a driver?  I've been searching the net but itt is not clear on how to do such a thing.

---

### Post by tgalati4 on 2011-02-20
It could be an interrupt problem.  Are the SCSI cards sharing an interrupt?

cat /proc/interrupts

When you originally installed 10.10 did you have two scsi cards installed?  Perhaps there is an issue with having both installed now will the full OS running, versus the LiveCD install mode.

---

### Post by wizard10000 on 2011-02-20
> **tgalati4 said:**
> It could be an interrupt problem.  Are the SCSI cards sharing an interrupt?

PCI devices can share interrupts.

---

### Post by wizard10000 on 2011-02-20
> **hockey_man3 said:**
> Yeah, i did do the loader.conf file deal as stated in the post and have rebooted to the same problem.....however, i'm somewhat skeptical to upgrade the hardware firmware since the cdrom drive on the scsi bus that's in question worked when i installed 10.10 using a cd

This might help -

[http://www.mjmwired.net/kernel/Documentation/scsi/aic7xxx.txt](http://www.mjmwired.net/kernel/Documentation/scsi/aic7xxx.txt)

---

### Post by hockey_man3 on 2011-02-20
Thanks tgalati4,

unfortunately this is a massive server, with all this scsi crap built in, there are physically no cards that I'm pulling in and out (there just aren't any cards to speak of in it).  everything hardware has NOT changed before, during and after install, so your concern of interrupts cannot be an issue.  However, thank you for taking your time to respond yet again; the clues do help!=)


Thanks wizard10000,

That has given me some major clues (I think), and I have gotten my hands on the  correct (I hope) drivers for this chip/hardware.

Also with some more searching the command lspci -vv yields the following snippet for that controller....
```
01:06.0 SCSI storage controller: Adaptec AIC-7880U (rev 01)
    Subsystem: Adaptec AIC-7880P Ultra/Ultra Wide SCSI Chipset
    Control: I/O- Mem- BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 32 (2000ns min, 2000ns max), Cache Line Size: 32 bytes
    Interrupt: pin A routed to IRQ 30
    Region 0: I/O ports at <ignored> [disabled]
    Region 1: Memory at fcfff000 (32-bit, non-prefetchable) [disabled] [size=4K]
    Expansion ROM at <ignored> [disabled]
    Capabilities: <access denied>
    Kernel modules: aic7xxx

```and the whole output of the command for those inquisitive minds...

```
00:00.0 Host bridge: Broadcom CNB20LE Host Bridge (rev 05)
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr+ Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ >SERR- <PERR- INTx-
    Latency: 32, Cache Line Size: 32 bytes
    Kernel modules: sworks-agp

00:00.1 Host bridge: Broadcom CNB20LE Host Bridge (rev 05)
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr+ Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 32, Cache Line Size: 32 bytes
    Kernel modules: sworks-agp

00:02.0 PCI bridge: Intel Corporation 80960RM (i960RM) Bridge (rev 01) (prog-if 00 [Normal decode])
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 32, Cache Line Size: 64 bytes
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
    Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
    BridgeCtl: Parity- SERR+ NoISA+ VGA- MAbort- >Reset- FastB2B-
        PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
    Kernel modules: shpchp

00:02.1 RAID bus controller: Dell PowerEdge Expandable RAID Controller 2/Si (rev 01)
    Subsystem: Dell PowerEdge 2400
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 32, Cache Line Size: 32 bytes
    Interrupt: pin A routed to IRQ 31
    Region 0: Memory at f4000000 (32-bit, prefetchable) [size=64M]
    Expansion ROM at <ignored> [disabled]
    Kernel driver in use: aacraid
    Kernel modules: aacraid

00:04.0 System peripheral: American Megatrends Inc. MegaRAC (rev 04)
    Subsystem: American Megatrends Inc. Dell Remote Assistant Card 2
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 32, Cache Line Size: 32 bytes
    Interrupt: pin A routed to IRQ 11
    BIST result: 00
    Region 0: I/O ports at ec80 [size=128]
    Region 1: Memory at fe103000 (32-bit, non-prefetchable) [size=4K]
    Expansion ROM at <ignored> [disabled]

00:08.0 Ethernet controller: Intel Corporation 82557/8/9/0/1 Ethernet Pro 100 (rev 08)
    Subsystem: Dell 10/100 Ethernet Server Adapter
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 32 (2000ns min, 14000ns max), Cache Line Size: 32 bytes
    Interrupt: pin A routed to IRQ 16
    Region 0: Memory at fe102000 (32-bit, non-prefetchable) [size=4K]
    Region 1: I/O ports at ec40 [size=64]
    Region 2: Memory at fe000000 (32-bit, non-prefetchable) [size=1M]
    Expansion ROM at <ignored> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: e100
    Kernel modules: e100

00:0e.0 VGA compatible controller: ATI Technologies Inc 3D Rage IIC (rev 7a) (prog-if 00 [VGA controller])
    Subsystem: Dell Device 009b
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping+ SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 32 (2000ns min), Cache Line Size: 32 bytes
    Region 0: Memory at f9000000 (32-bit, prefetchable) [size=16M]
    Region 1: I/O ports at e800 [size=256]
    Region 2: Memory at fe101000 (32-bit, non-prefetchable) [size=4K]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel modules: atyfb

00:0f.0 ISA bridge: Broadcom OSB4 South Bridge (rev 4f)
    Subsystem: Broadcom OSB4 South Bridge
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Kernel driver in use: piix4_smbus
    Kernel modules: i2c-piix4

00:0f.2 USB Controller: Broadcom OSB4/CSB5 OHCI USB Controller (rev 04) (prog-if 10 [OHCI])
    Subsystem: Broadcom OSB4/CSB5 OHCI USB Controller
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR+ INTx-
    Latency: 32 (20000ns max), Cache Line Size: 32 bytes
    Interrupt: pin A routed to IRQ 11
    Region 0: Memory at fe100000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

01:06.0 SCSI storage controller: Adaptec AIC-7880U (rev 01)
    Subsystem: Adaptec AIC-7880P Ultra/Ultra Wide SCSI Chipset
    Control: I/O- Mem- BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 32 (2000ns min, 2000ns max), Cache Line Size: 32 bytes
    Interrupt: pin A routed to IRQ 30
    Region 0: I/O ports at <ignored> [disabled]
    Region 1: Memory at fcfff000 (32-bit, non-prefetchable) [disabled] [size=4K]
    Expansion ROM at <ignored> [disabled]
    Capabilities: <access denied>
    Kernel modules: aic7xxx

02:0a.0 PCI bridge: Digital Equipment Corporation DECchip 21152 (rev 03) (prog-if 00 [Normal decode])
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 32, Cache Line Size: 32 bytes
    Bus: primary=02, secondary=03, subordinate=03, sec-latency=32
    Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
    BridgeCtl: Parity- SERR+ NoISA+ VGA- MAbort- >Reset- FastB2B-
        PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
    Capabilities: <access denied>
    Kernel modules: shpchp

03:04.0 Ethernet controller: Intel Corporation 82557/8/9/0/1 Ethernet Pro 100 (rev 05)
    Subsystem: Intel Corporation EtherExpress PRO/100+ Dual Port Adapter
    Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Interrupt: pin A routed to IRQ 24
    Region 0: Memory at ecfff000 (32-bit, prefetchable) [size=4K]
    Region 1: I/O ports at <ignored>
    Region 2: Memory at eef00000 (32-bit, non-prefetchable) [size=1M]
    Expansion ROM at <ignored> [disabled]
    Capabilities: <access denied>
    Kernel modules: e100

03:05.0 Ethernet controller: Intel Corporation 82557/8/9/0/1 Ethernet Pro 100 (rev 05)
    Subsystem: Intel Corporation EtherExpress PRO/100+ Dual Port Adapter
    Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Interrupt: pin A routed to IRQ 25
    Region 0: Memory at ecffe000 (32-bit, prefetchable) [size=4K]
    Region 1: I/O ports at <ignored>
    Region 2: Memory at eee00000 (32-bit, non-prefetchable) [size=1M]
    Expansion ROM at <ignored> [disabled]
    Capabilities: <access denied>
    Kernel modules: e100

```So I'm seeing "access denied" with the scsi controller (the aic-7880u)...I'm guessing again there's no driver for it, therefore it cannot talk to this thing.  I'm trying to compile the driver source files which I found @[ http://people.freebsd.org/~gibbs/linux/SRC/]("http://people.freebsd.org/%7Egibbs/linux/SRC/") which I downloaded the [aic79xx-linux-2.6-20040522-tar.gz]("http://people.freebsd.org/%7Egibbs/linux/SRC/aic79xx-linux-2.6-20040522-tar.gz") file.  

However, some problems have stemmed from this.  

I tried make but get...

 ```
make: *** No rule to make target `/53c7xx_d.h', needed by `/53c7xx.o'.  Stop.
```ok so I tried make dep, but then I get....

```
make: *** No rule to make target `dep'.  Stop.

```and I also played around with what was in the other directories and found a aic7xxx folder, which contains it's own Makefile which couldn't "make" because ....

```
make: *** No rule to make target `/aic7xxx_seq.h', needed by `/aic7xxx_core.o'.  Stop.

```so again.....I know there's a 10 character command I'm missing for this which will make this whole thing work! (I can feel I'm close)

---

### Post by wizard10000 on 2011-02-21
> **hockey_man3 said:**
> ...I know there's a 10 character command I'm missing for this which will make this whole thing work! (I can feel I'm close)

Thought about this some after I logged off last night.  aic7xxx support has been in Linux for a lot of years - you shouldn't have to compile a driver.  Back when I had an Adaptec 29160 SCSI controller in my desktop PC (uses the same driver) the thing just worked.  It even worked more years ago than that when I had an embedded Adaptec 2940 controller on my PC's motherboard - and that also uses the same driver.

Please post the output of lsmod, hockey_man.  I think the driver for this hardware may already be loading and the problem is Something Else  ;)

Also - are you sure the card is configured properly and that the SCSI chain is terminated properly?

cheers -

---

### Post by hockey_man3 on 2011-02-23
hmmmmm......you're right, aic7xxx is loading as follows...

```
Module                  Size  Used by
binfmt_misc             6599  1 
ppdev                   5556  0 
dell_wmi_aio            1733  0 
dcdbas                  5442  0 
psmouse                59033  0 
parport_pc             26378  1 
serio_raw               4022  0 
sworks_agp              5682  0 
i2c_piix4               8795  0 
shpchp                 29982  0 
lp                      7342  0 
agpgart                32075  1 sworks_agp
parport                31492  3 ppdev,parport_pc,lp
usbhid                 36978  0 
hid                    67742  1 usbhid
floppy                 54343  0 
aic7xxx               121556  0 
e100                   30676  0 
aacraid                67207  2 
mii                     4425  1 e100
```.....ha!  So what the hell now? =)

I'll take some screen shots later of BIOS POST so you can see my scsi chain coming up...all drives are listed in their configured address location, and I believe it's terminated correctly since the ribbon connector has the built in terminator and I've configured the jumpers not to terminate the scsi chain at the drives.

it's just funny how the kernel which was used to install ubuntu server on the cd was able to see everything without a hitch.

---

### Post by hockey_man3 on 2011-02-23
In my google searches I found a page 

[http://www.netadmintools.com/text/README.aic7xxx.txt](http://www.netadmintools.com/text/README.aic7xxx.txt)

which has a /proc support section and lays out a /proc/scsi/aic7xxx directory i should have if the driver loaded correctly.  And of course I cannot find it, there's nothing under the scsi directory other than what follows...

```
matt@petey:/proc/scsi$ ls -la
total 0
dr-xr-xr-x   3 root root 0 2011-02-23 16:06 .
dr-xr-xr-x 150 root root 0 2011-02-23 14:07 ..
-r--r--r--   1 root root 0 2011-02-23 16:07 device_info
-r--r--r--   1 root root 0 2011-02-23 16:07 scsi
dr-xr-xr-x   2 root root 0 2011-02-23 16:07 sg

```doing a "cat scsi" yields the following...

```
matt@petey:/proc/scsi$ cat scsi
Attached devices:
Host: scsi0 Channel: 00 Id: 00 Lun: 00
  Vendor: DELL     Model: Inventory        Rev: V1.0
  Type:   Direct-Access                    ANSI  SCSI revision: 02
Host: scsi0 Channel: 01 Id: 00 Lun: 00
  Vendor: SEAGATE  Model: ST318203LC       Rev: 0001
  Type:   Direct-Access                    ANSI  SCSI revision: 02
Host: scsi0 Channel: 01 Id: 01 Lun: 00
  Vendor: SEAGATE  Model: ST318203LC       Rev: 0001
  Type:   Direct-Access                    ANSI  SCSI revision: 02
Host: scsi0 Channel: 01 Id: 02 Lun: 00
  Vendor: SEAGATE  Model: ST318203LC       Rev: 0001
  Type:   Direct-Access                    ANSI  SCSI revision: 02
Host: scsi0 Channel: 01 Id: 03 Lun: 00
  Vendor: SEAGATE  Model: ST318203LC       Rev: 0001
  Type:   Direct-Access                    ANSI  SCSI revision: 02
Host: scsi0 Channel: 01 Id: 04 Lun: 00
  Vendor: SEAGATE  Model: ST318406LC       Rev: 8A03
  Type:   Direct-Access                    ANSI  SCSI revision: 03
Host: scsi0 Channel: 01 Id: 05 Lun: 00
  Vendor: SEAGATE  Model: ST318404LC       Rev: 0002
  Type:   Direct-Access                    ANSI  SCSI revision: 03
Host: scsi0 Channel: 01 Id: 06 Lun: 00
  Vendor: DELL     Model: 1x6 U2W SCSI BP  Rev: 5.24
  Type:   Processor                        ANSI  SCSI revision: 02
```...and again not tape or cd drive on scsi1 channel as it shows in the bios which I've yet to take a pic of (I will shortly with a follow up post)

now there's a directory "sg" in /proc/scsi which I caught my interest, which has a bunch of file which I "cat'ed" out for you as follows...

```
matt@petey:/proc/scsi$ cd sg
matt@petey:/proc/scsi/sg$ ls -la
total 0
dr-xr-xr-x 2 root root 0 2011-02-23 16:09 .
dr-xr-xr-x 3 root root 0 2011-02-23 16:06 ..
-rw-r--r-- 1 root root 0 2011-02-23 16:09 allow_dio
-r--r--r-- 1 root root 0 2011-02-23 16:09 debug
-rw-r--r-- 1 root root 0 2011-02-23 16:09 def_reserved_size
-r--r--r-- 1 root root 0 2011-02-23 16:09 device_hdr
-r--r--r-- 1 root root 0 2011-02-23 16:09 devices
-r--r--r-- 1 root root 0 2011-02-23 16:09 device_strs
-r--r--r-- 1 root root 0 2011-02-23 16:09 version
matt@petey:/proc/scsi/sg$ cat devices
0    0    0    0    0    1    256    0    1
0    1    0    0    0    1    1    0    1
0    1    1    0    0    1    1    0    1
0    1    2    0    0    1    1    0    1
0    1    3    0    0    1    1    0    1
0    1    4    0    0    1    1    0    1
0    1    5    0    0    1    1    0    1
0    1    6    0    3    1    1    0    1
matt@petey:/proc/scsi/sg$ cat allow_dio
0
matt@petey:/proc/scsi/sg$ cat debug
max_active_device=8(origin 1)
 def_reserved_size=32768
matt@petey:/proc/scsi/sg$ cat def_reserved_size
32768
matt@petey:/proc/scsi/sg$ cat device_hdr
host    chan    id    lun    type    opens    qdepth    busy    online
matt@petey:/proc/scsi/sg$ cat device_strs
DELL        Inventory           V1.0
SEAGATE     ST318203LC          0001
SEAGATE     ST318203LC          0001
SEAGATE     ST318203LC          0001
SEAGATE     ST318203LC          0001
SEAGATE     ST318406LC          8A03
SEAGATE     ST318404LC          0002
DELL        1x6 U2W SCSI BP     5.24
matt@petey:/proc/scsi/sg$ cat version
30534    3.5.34 [20061027]

```if you notice when I "cat debug"  

```
matt@petey:/proc/scsi/sg$ cat debug
max_active_device=8(origin 1)
 def_reserved_size=32768
```there's a "max_active_device=8(origin 1)" which is interesting (and am scared to change it....however, if there's a restriction on how many scsi things there are active in the system this would make sense to change.  This is because I have 6 hard drives and their controller running for a total of 7 devices, then the controller for the next channel which has the scsi cdrom and tape drives.......oh so scarry to change! =)

...BIOS POST screen shots coming soon!...

---

### Post by hockey_man3 on 2011-02-24
so it's screen shot time! (T-shirt time!!!)...anywho, you may investigate the pictures attached to this post at your will.  

there's 5 pics:

1) [[DSCF0155.jpg]("http://ubuntuforums.org/attachment.php?attachmentid=184408&stc=1&d=1298599450")] Main BIOS POST (for reference)
2) [[DSCF0162.jpg]("http://ubuntuforums.org/attachment.php?attachmentid=184409&stc=1&d=1298599450")] First SCSI controller waking up my RAID array (the aic-7890 chip)
3) [[DSCF0195.jpg]("http://ubuntuforums.org/attachment.php?attachmentid=184410&stc=1&d=1298599450")] Second SCSI controller waking up my tape and DVD-ROM drive, which report correctly (the aic-7880 chip)
4) [[DSCF0199.jpg]("http://ubuntuforums.org/attachment.php?attachmentid=184411&stc=1&d=1298599450")] Main BIOS setup showing secondary SCSI turn on and first SCSI on as RAID
5) [[DSCF0185.jpg]("http://ubuntuforums.org/attachment.php?attachmentid=184412&stc=1&d=1298599450")] And the utility BIOS for the AIC-7880 controller chip showing my tape and DVD-ROM drive correctly

I believe all the settings are correct....however, as always, any friendly advice is always appreciated!

---

### Post by wizard10000 on 2011-02-25
> **hockey_man3 said:**
> so it's screen shot time! (T-shirt time!!!)...anywho, you may investigate the pictures attached to this post at your will...

Time to start looking at system logs.

Also, does /dev/scd0 exist?  If so that's your optical drive and may just need to be mounted.

Re termination - both ends of the SCSI chain have to be terminated.  Sounds like you've got the card end terminated properly; what about termination on the SCSI card itself?  Unless there's an *external* SCSI device on the chain termination happens on the card as well.

---

### Post by hockey_man3 on 2011-02-26
hmmmm....so it looks like this was in the original dmsg log the whole time...

```
[    1.591987] aic7xxx 0000:01:06.0: PCI INT A -> GSI 30 (level, low) -> IRQ 30
[    1.592119] aic7xxx: PCI Device 1:6:0 failed memory mapped test.  Using PIO.
[    1.592134] aic7xxx: PCI1:6:0 IO region 0x0[0..255] unavailable. Cannot map device.
[    1.592158] aic7xxx: probe of 0000:01:06.0 failed with error -12

```I haven't a clue what the hell that means

On the termination issue....

There are no scsi cards on or in this computer...there are scsi controllers integrated into this server motherboard, and there isn't jumper or switches or buttons or doodads to terminate at the controller side.

The scsi cable I'm using has a terminator on the end of the chain (it's part of the scsi ribbon cable and cannot be removed).

The drives have a jumper setting on them to turn "active termination" on or off, and I've tried both ways....and have recently tried elimination techniques of booting only one drive with certain settings.  and again the same message about the driver comes up and no drives are found in /dev.

As always Thank You for your help and time.

---

### Post by wizard10000 on 2011-02-26
> **hockey_man3 said:**
> hmmmm....so it looks like this was in the original dmsg log the whole time...

```
[    1.591987] aic7xxx 0000:01:06.0: PCI INT A -> GSI 30 (level, low) -> IRQ 30
[    1.592119] aic7xxx: PCI Device 1:6:0 failed memory mapped test.  Using PIO.
[    1.592134] aic7xxx: PCI1:6:0 IO region 0x0[0..255] unavailable. Cannot map device.
[    1.592158] aic7xxx: probe of 0000:01:06.0 failed with error -12

```I haven't a clue what the hell that means

On the termination issue....

There are no scsi cards on or in this computer...there are scsi controllers integrated into this server motherboard, and there isn't jumper or switches or buttons or doodads to terminate at the controller side.

The scsi cable I'm using has a terminator on the end of the chain (it's part of the scsi ribbon cable and cannot be removed).

The drives have a jumper setting on them to turn "active termination" on or off, and I've tried both ways....and have recently tried elimination techniques of booting only one drive with certain settings.  and again the same message about the driver comes up and no drives are found in /dev.

As always Thank You for your help and time.

You might want to check to make sure the two SCSI adapters in the machine aren't using the same I/O addresses.  I saw something else about disabling SERR in the server's BIOS.

Hope this helps -

---

