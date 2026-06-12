---
title: "How to find out what caused the Crash?"
date: 2010-04-07
forum: New to Ubuntu
---

### Post by deancasino on 2010-04-07
Hey guys in the last 3 days Ubuntu has locked up and crashed over 6 times.

Something is very wrong I suspect, how do I find out what's causing it so I can remove apps and fix it?

---

### Post by whoop on 2010-04-07
look in /var/log/
Maybe /var/log/kern.log or /var/log/messages

---

### Post by 3rdalbum on 2010-04-07
> **deancasino said:**
> Hey guys in the last 3 days Ubuntu has locked up and crashed over 6 times.

Something is very wrong I suspect, how do I find out what's causing it so I can remove apps and fix it?

Tonight, run Memtest from the GRUB menu. Run it overnight. If the computer has crashed when you wake up in the morning, or if it reports errors, then you've got faulty RAM.

Otherwise, whoop's advice is sound. But you must check your RAM first, because if faulty RAM causes the problem then the kernel logs will show absolutely any of your running programs as being the one that caused the crash, and you'll be lead on a wild goose chase.

---

### Post by deancasino on 2010-04-08
Memtest proved to be a success, as in, no crash. though I did get another crash last night, here is the messages log (if anyone can help):

Apr  8 19:01:39 Megatron kernel: imklog 4.2.0, log source = /proc/kmsg started.
Apr  8 19:01:39 Megatron rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="793" x-info="http://www.rsyslog.com"] (re)start
Apr  8 19:01:39 Megatron rsyslogd: rsyslogd's groupid changed to 103
Apr  8 19:01:39 Megatron rsyslogd: rsyslogd's userid changed to 101
Apr  8 19:01:39 Megatron kernel: [    0.000000] Initializing cgroup subsys cpuset
Apr  8 19:01:39 Megatron kernel: [    0.000000] Initializing cgroup subsys cpu
Apr  8 19:01:39 Megatron kernel: [    0.000000] Linux version 2.6.32-18-generic (buildd@rothera) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu4) ) #27-Ubuntu SMP Fri Mar 26 19:51:10 UTC 2010 (Ubuntu 2.6.32-18.27-generic 2.6.32.10+drm33.1)
Apr  8 19:01:39 Megatron kernel: [    0.000000] KERNEL supported cpus:
Apr  8 19:01:39 Megatron kernel: [    0.000000]   Intel GenuineIntel
Apr  8 19:01:39 Megatron kernel: [    0.000000]   AMD AuthenticAMD
Apr  8 19:01:39 Megatron kernel: [    0.000000]   NSC Geode by NSC
Apr  8 19:01:39 Megatron kernel: [    0.000000]   Cyrix CyrixInstead
Apr  8 19:01:39 Megatron kernel: [    0.000000]   Centaur CentaurHauls
Apr  8 19:01:39 Megatron kernel: [    0.000000]   Transmeta GenuineTMx86
Apr  8 19:01:39 Megatron kernel: [    0.000000]   Transmeta TransmetaCPU
Apr  8 19:01:39 Megatron kernel: [    0.000000]   UMC UMC UMC UMC
Apr  8 19:01:39 Megatron kernel: [    0.000000] BIOS-provided physical RAM map:
Apr  8 19:01:39 Megatron kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009dc00 (usable)
Apr  8 19:01:39 Megatron kernel: [    0.000000]  BIOS-e820: 000000000009dc00 - 00000000000a0000 (reserved)
Apr  8 19:01:39 Megatron kernel: [    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
Apr  8 19:01:39 Megatron kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 00000000bff80000 (usable)
Apr  8 19:01:39 Megatron kernel: [    0.000000]  BIOS-e820: 00000000bff80000 - 00000000bff8e000 (ACPI data)
Apr  8 19:01:39 Megatron kernel: [    0.000000]  BIOS-e820: 00000000bff8e000 - 00000000bffd0000 (ACPI NVS)
Apr  8 19:01:39 Megatron kernel: [    0.000000]  BIOS-e820: 00000000bffd0000 - 00000000c0000000 (reserved)
Apr  8 19:01:39 Megatron kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Apr  8 19:01:39 Megatron kernel: [    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
Apr  8 19:01:39 Megatron kernel: [    0.000000]  BIOS-e820: 0000000100000000 - 0000000140000000 (usable)
Apr  8 19:01:39 Megatron kernel: [    0.000000] DMI present.
Apr  8 19:01:39 Megatron kernel: [    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
Apr  8 19:01:39 Megatron kernel: [    0.000000] last_pfn = 0xbff80 max_arch_pfn = 0x100000
Apr  8 19:01:39 Megatron kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Apr  8 19:01:39 Megatron kernel: [    0.000000] Scanning 0 areas for low memory corruption
Apr  8 19:01:39 Megatron kernel: [    0.000000] modified physical RAM map:
Apr  8 19:01:39 Megatron kernel: [    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
Apr  8 19:01:39 Megatron kernel: [    0.000000]  modified: 0000000000010000 - 000000000009dc00 (usable)
Apr  8 19:01:39 Megatron kernel: [    0.000000]  modified: 000000000009dc00 - 00000000000a0000 (reserved)
Apr  8 19:01:39 Megatron kernel: [    0.000000]  modified: 00000000000e4000 - 0000000000100000 (reserved)
Apr  8 19:01:39 Megatron kernel: [    0.000000]  modified: 0000000000100000 - 00000000bff80000 (usable)
Apr  8 19:01:39 Megatron kernel: [    0.000000]  modified: 00000000bff80000 - 00000000bff8e000 (ACPI data)
Apr  8 19:01:39 Megatron kernel: [    0.000000]  modified: 00000000bff8e000 - 00000000bffd0000 (ACPI NVS)
Apr  8 19:01:39 Megatron kernel: [    0.000000]  modified: 00000000bffd0000 - 00000000c0000000 (reserved)
Apr  8 19:01:39 Megatron kernel: [    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
Apr  8 19:01:39 Megatron kernel: [    0.000000]  modified: 00000000fff00000 - 0000000100000000 (reserved)
Apr  8 19:01:39 Megatron kernel: [    0.000000]  modified: 0000000100000000 - 0000000140000000 (usable)
Apr  8 19:01:39 Megatron kernel: [    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
Apr  8 19:01:39 Megatron kernel: [    0.000000] Using x86 segment limits to approximate NX protection
Apr  8 19:01:39 Megatron kernel: [    0.000000] RAMDISK: 37878000 - 37fef992
Apr  8 19:01:39 Megatron kernel: [    0.000000] Allocated new RAMDISK: 008dc000 - 01053992
Apr  8 19:01:39 Megatron kernel: [    0.000000] Move RAMDISK from 0000000037878000 - 0000000037fef991 to 008dc000 - 01053991
Apr  8 19:01:39 Megatron kernel: [    0.000000] ACPI: RSDP 000fbb10 00014 (v00 ACPIAM)
Apr  8 19:01:39 Megatron kernel: [    0.000000] ACPI: RSDT bff80000 00040 (v01 A_M_I_ OEMRSDT  03000912 MSFT 00000097)
Apr  8 19:01:39 Megatron kernel: [    0.000000] ACPI: FACP bff80200 00084 (v02 A_M_I_ OEMFACP  03000912 MSFT 00000097)
Apr  8 19:01:39 Megatron kernel: [    0.000000] ACPI: DSDT bff80440 08888 (v01  A1014 A1014001 00000001 INTL 20051117)
Apr  8 19:01:39 Megatron kernel: [    0.000000] ACPI: FACS bff8e000 00040
Apr  8 19:01:39 Megatron kernel: [    0.000000] ACPI: APIC bff80390 0006C (v01 A_M_I_ OEMAPIC  03000912 MSFT 00000097)
Apr  8 19:01:39 Megatron kernel: [    0.000000] ACPI: MCFG bff80400 0003C (v01 A_M_I_ OEMMCFG  03000912 MSFT 00000097)
Apr  8 19:01:39 Megatron kernel: [    0.000000] ACPI: OEMB bff8e040 00081 (v01 A_M_I_ AMI_OEM  03000912 MSFT 00000097)
Apr  8 19:01:39 Megatron kernel: [    0.000000] ACPI: HPET bff88cd0 00038 (v01 A_M_I_ OEMHPET  03000912 MSFT 00000097)
Apr  8 19:01:39 Megatron kernel: [    0.000000] ACPI: OSFR bff88d10 000B0 (v01 A_M_I_ OEMOSFR  03000912 MSFT 00000097)
Apr  8 19:01:39 Megatron kernel: [    0.000000] ACPI: SSDT bff8e8d0 00A7C (v01 DpgPmm    CpuPm 00000012 INTL 20051117)
Apr  8 19:01:39 Megatron kernel: [    0.000000] 2183MB HIGHMEM available.
Apr  8 19:01:39 Megatron kernel: [    0.000000] 887MB LOWMEM available.
Apr  8 19:01:39 Megatron kernel: [    0.000000]   mapped low ram: 0 - 377fe000
Apr  8 19:01:39 Megatron kernel: [    0.000000]   low ram: 0 - 377fe000
Apr  8 19:01:39 Megatron kernel: [    0.000000]   node 0 low ram: 00000000 - 377fe000
Apr  8 19:01:39 Megatron kernel: [    0.000000]   node 0 bootmap 00011000 - 00017f00
Apr  8 19:01:39 Megatron kernel: [    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
Apr  8 19:01:39 Megatron kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
Apr  8 19:01:39 Megatron kernel: [    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
Apr  8 19:01:39 Megatron kernel: [    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
Apr  8 19:01:39 Megatron kernel: [    0.000000]   #3 [0000100000 - 00008d7e98]    TEXT DATA BSS ==> [0000100000 - 00008d7e98]
Apr  8 19:01:39 Megatron kernel: [    0.000000]   #4 [000009dc00 - 0000100000]    BIOS reserved ==> [000009dc00 - 0000100000]
Apr  8 19:01:39 Megatron kernel: [    0.000000]   #5 [00008d8000 - 00008db21c]              BRK ==> [00008d8000 - 00008db21c]
Apr  8 19:01:39 Megatron kernel: [    0.000000]   #6 [0000010000 - 0000011000]          PGTABLE ==> [0000010000 - 0000011000]
Apr  8 19:01:39 Megatron kernel: [    0.000000]   #7 [00008dc000 - 0001053992]      NEW RAMDISK ==> [00008dc000 - 0001053992]
Apr  8 19:01:39 Megatron kernel: [    0.000000]   #8 [0000011000 - 0000018000]          BOOTMAP ==> [0000011000 - 0000018000]
Apr  8 19:01:39 Megatron kernel: [    0.000000] found SMP MP-table at [c00ff780] ff780
Apr  8 19:01:39 Megatron kernel: [    0.000000] Zone PFN ranges:
Apr  8 19:01:39 Megatron kernel: [    0.000000]   DMA      0x00000010 -> 0x00001000
Apr  8 19:01:39 Megatron kernel: [    0.000000]   Normal   0x00001000 -> 0x000377fe
Apr  8 19:01:39 Megatron kernel: [    0.000000]   HighMem  0x000377fe -> 0x000bff80
Apr  8 19:01:39 Megatron kernel: [    0.000000] Movable zone start PFN for each node
Apr  8 19:01:39 Megatron kernel: [    0.000000] early_node_map[2] active PFN ranges
Apr  8 19:01:39 Megatron kernel: [    0.000000]     0: 0x00000010 -> 0x0000009d
Apr  8 19:01:39 Megatron kernel: [    0.000000]     0: 0x00000100 -> 0x000bff80
Apr  8 19:01:39 Megatron kernel: [    0.000000] Using APIC driver default
Apr  8 19:01:39 Megatron kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x808
Apr  8 19:01:39 Megatron kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Apr  8 19:01:39 Megatron kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
Apr  8 19:01:39 Megatron kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x02] enabled)
Apr  8 19:01:39 Megatron kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
Apr  8 19:01:39 Megatron kernel: [    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
Apr  8 19:01:39 Megatron kernel: [    0.000000] IOAPIC[0]: apic_id 4, version 32, address 0xfec00000, GSI 0-23
Apr  8 19:01:39 Megatron kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Apr  8 19:01:39 Megatron kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Apr  8 19:01:39 Megatron kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Apr  8 19:01:39 Megatron kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Apr  8 19:01:39 Megatron kernel: [    0.000000] ACPI: HPET id: 0x8086a301 base: 0xfed00000
Apr  8 19:01:39 Megatron kernel: [    0.000000] SMP: Allowing 4 CPUs, 0 hotplug CPUs
Apr  8 19:01:39 Megatron kernel: [    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
Apr  8 19:01:39 Megatron kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
Apr  8 19:01:39 Megatron kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e4000
Apr  8 19:01:39 Megatron kernel: [    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
Apr  8 19:01:39 Megatron kernel: [    0.000000] Allocating PCI resources starting at c0000000 (gap: c0000000:3ee00000)
Apr  8 19:01:39 Megatron kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Apr  8 19:01:39 Megatron kernel: [    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
Apr  8 19:01:39 Megatron kernel: [    0.000000] PERCPU: Embedded 14 pages/cpu @c2c00000 s35992 r0 d21352 u1048576
Apr  8 19:01:39 Megatron kernel: [    0.000000] pcpu-alloc: s35992 r0 d21352 u1048576 alloc=1*4194304
Apr  8 19:01:39 Megatron kernel: [    0.000000] pcpu-alloc: [0] 0 1 2 3 
Apr  8 19:01:39 Megatron kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 780045
Apr  8 19:01:39 Megatron kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-18-generic root=UUID=d487fee3-e236-48b3-a1a6-245593ff611f ro quiet splash
Apr  8 19:01:39 Megatron kernel: [    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
Apr  8 19:01:39 Megatron kernel: [    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Apr  8 19:01:39 Megatron kernel: [    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Apr  8 19:01:39 Megatron kernel: [    0.000000] Enabling fast FPU save and restore... done.
Apr  8 19:01:39 Megatron kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Apr  8 19:01:39 Megatron kernel: [    0.000000] Initializing CPU#0
Apr  8 19:01:39 Megatron kernel: [    0.000000] xsave/xrstor: enabled xstate_bv 0x3, cntxt size 0x240
Apr  8 19:01:39 Megatron kernel: [    0.000000] allocated 15725760 bytes of page_cgroup
Apr  8 19:01:39 Megatron kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Apr  8 19:01:39 Megatron kernel: [    0.000000] Initializing HighMem for node 0 (000377fe:000bff80)
Apr  8 19:01:39 Megatron kernel: [    0.000000] Memory: 3086840k/3145216k available (4671k kernel code, 56744k reserved, 2116k data, 656k init, 2235912k highmem)
Apr  8 19:01:39 Megatron kernel: [    0.000000] virtual kernel memory layout:
Apr  8 19:01:39 Megatron kernel: [    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
Apr  8 19:01:39 Megatron kernel: [    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Apr  8 19:01:39 Megatron kernel: [    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
Apr  8 19:01:39 Megatron kernel: [    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
Apr  8 19:01:39 Megatron kernel: [    0.000000]       .init : 0xc07a1000 - 0xc0845000   ( 656 kB)
Apr  8 19:01:39 Megatron kernel: [    0.000000]       .data : 0xc058fde3 - 0xc07a0e48   (2116 kB)
Apr  8 19:01:39 Megatron kernel: [    0.000000]       .text : 0xc0100000 - 0xc058fde3   (4671 kB)
Apr  8 19:01:39 Megatron kernel: [    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Apr  8 19:01:39 Megatron kernel: [    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
Apr  8 19:01:39 Megatron kernel: [    0.000000] Hierarchical RCU implementation.
Apr  8 19:01:39 Megatron kernel: [    0.000000] NR_IRQS:2304 nr_irqs:440
Apr  8 19:01:39 Megatron kernel: [    0.000000] Console: colour VGA+ 80x25
Apr  8 19:01:39 Megatron kernel: [    0.000000] console [tty0] enabled
Apr  8 19:01:39 Megatron kernel: [    0.000000] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
Apr  8 19:01:39 Megatron kernel: [    0.000000] Fast TSC calibration using PIT
Apr  8 19:01:39 Megatron kernel: [    0.000000] Detected 2330.959 MHz processor.
Apr  8 19:01:39 Megatron kernel: [    0.004005] Calibrating delay loop (skipped), value calculated using timer frequency.. 4661.91 BogoMIPS (lpj=9323836)
Apr  8 19:01:39 Megatron kernel: [    0.004019] Security Framework initialized
Apr  8 19:01:39 Megatron kernel: [    0.004036] AppArmor: AppArmor initialized
Apr  8 19:01:39 Megatron kernel: [    0.004041] Mount-cache hash table entries: 512
Apr  8 19:01:39 Megatron kernel: [    0.004147] Initializing cgroup subsys ns
Apr  8 19:01:39 Megatron kernel: [    0.004150] Initializing cgroup subsys cpuacct
Apr  8 19:01:39 Megatron kernel: [    0.004154] Initializing cgroup subsys memory
Apr  8 19:01:39 Megatron kernel: [    0.004160] Initializing cgroup subsys devices
Apr  8 19:01:39 Megatron kernel: [    0.004162] Initializing cgroup subsys freezer
Apr  8 19:01:39 Megatron kernel: [    0.004164] Initializing cgroup subsys net_cls
Apr  8 19:01:39 Megatron kernel: [    0.004181] CPU: L1 I cache: 32K, L1 D cache: 32K
Apr  8 19:01:39 Megatron kernel: [    0.004183] CPU: L2 cache: 2048K
Apr  8 19:01:39 Megatron kernel: [    0.004186] CPU: Physical Processor ID: 0
Apr  8 19:01:39 Megatron kernel: [    0.004187] CPU: Processor Core ID: 0
Apr  8 19:01:39 Megatron kernel: [    0.004191] mce: CPU supports 6 MCE banks
Apr  8 19:01:39 Megatron kernel: [    0.004198] CPU0: Thermal monitoring enabled (TM2)
Apr  8 19:01:39 Megatron kernel: [    0.004201] using mwait in idle threads.
Apr  8 19:01:39 Megatron kernel: [    0.004206] Performance Events: Core2 events, Intel PMU driver.
Apr  8 19:01:39 Megatron kernel: [    0.004213] ... version:                2
Apr  8 19:01:39 Megatron kernel: [    0.004215] ... bit width:              40
Apr  8 19:01:39 Megatron kernel: [    0.004216] ... generic registers:      2
Apr  8 19:01:39 Megatron kernel: [    0.004218] ... value mask:             000000ffffffffff
Apr  8 19:01:39 Megatron kernel: [    0.004219] ... max period:             000000007fffffff
Apr  8 19:01:39 Megatron kernel: [    0.004221] ... fixed-purpose events:   3
Apr  8 19:01:39 Megatron kernel: [    0.004222] ... event mask:             0000000700000003
Apr  8 19:01:39 Megatron kernel: [    0.004227] Checking 'hlt' instruction... OK.
Apr  8 19:01:39 Megatron kernel: [    0.022528] ACPI: Core revision 20090903
Apr  8 19:01:39 Megatron kernel: [    0.036007] ftrace: converting mcount calls to 0f 1f 44 00 00
Apr  8 19:01:39 Megatron kernel: [    0.036012] ftrace: allocating 21765 entries in 43 pages
Apr  8 19:01:39 Megatron kernel: [    0.040345] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Apr  8 19:01:39 Megatron kernel: [    0.081016] CPU0: Intel(R) Core(TM)2 Quad CPU    Q8200  @ 2.33GHz stepping 0a
Apr  8 19:01:39 Megatron kernel: [    0.084001] Booting processor 1 APIC 0x1 ip 0x6000
Apr  8 19:01:39 Megatron kernel: [    0.008000] Initializing CPU#1
Apr  8 19:01:39 Megatron kernel: [    0.008000] CPU: L1 I cache: 32K, L1 D cache: 32K
Apr  8 19:01:39 Megatron kernel: [    0.008000] CPU: L2 cache: 2048K
Apr  8 19:01:39 Megatron kernel: [    0.008000] CPU: Physical Processor ID: 0
Apr  8 19:01:39 Megatron kernel: [    0.008000] CPU: Processor Core ID: 1
Apr  8 19:01:39 Megatron kernel: [    0.008000] CPU1: Thermal monitoring enabled (TM2)
Apr  8 19:01:39 Megatron kernel: [    0.168066] CPU1: Intel(R) Core(TM)2 Quad CPU    Q8200  @ 2.33GHz stepping 0a
Apr  8 19:01:39 Megatron kernel: [    0.168077] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
Apr  8 19:01:39 Megatron kernel: [    0.172095] Booting processor 2 APIC 0x2 ip 0x6000
Apr  8 19:01:39 Megatron kernel: [    0.008000] Initializing CPU#2
Apr  8 19:01:39 Megatron kernel: [    0.008000] CPU: L1 I cache: 32K, L1 D cache: 32K
Apr  8 19:01:39 Megatron kernel: [    0.008000] CPU: L2 cache: 2048K
Apr  8 19:01:39 Megatron kernel: [    0.008000] CPU: Physical Processor ID: 0
Apr  8 19:01:39 Megatron kernel: [    0.008000] CPU: Processor Core ID: 2
Apr  8 19:01:39 Megatron kernel: [    0.008000] CPU2: Thermal monitoring enabled (TM2)
Apr  8 19:01:39 Megatron kernel: [    0.260115] CPU2: Intel(R) Core(TM)2 Quad CPU    Q8200  @ 2.33GHz stepping 0a
Apr  8 19:01:39 Megatron kernel: [    0.260126] checking TSC synchronization [CPU#0 -> CPU#2]: passed.
Apr  8 19:01:39 Megatron kernel: [    0.264085] Booting processor 3 APIC 0x3 ip 0x6000
Apr  8 19:01:39 Megatron kernel: [    0.008000] Initializing CPU#3
Apr  8 19:01:39 Megatron kernel: [    0.008000] CPU: L1 I cache: 32K, L1 D cache: 32K
Apr  8 19:01:39 Megatron kernel: [    0.008000] CPU: L2 cache: 2048K
Apr  8 19:01:39 Megatron kernel: [    0.008000] CPU: Physical Processor ID: 0
Apr  8 19:01:39 Megatron kernel: [    0.008000] CPU: Processor Core ID: 3
Apr  8 19:01:39 Megatron kernel: [    0.008000] CPU3: Thermal monitoring enabled (TM2)
Apr  8 19:01:39 Megatron kernel: [    0.352054] CPU3: Intel(R) Core(TM)2 Quad CPU    Q8200  @ 2.33GHz stepping 0a
Apr  8 19:01:39 Megatron kernel: [    0.352065] checking TSC synchronization [CPU#0 -> CPU#3]: passed.
Apr  8 19:01:39 Megatron kernel: [    0.356013] Brought up 4 CPUs
Apr  8 19:01:39 Megatron kernel: [    0.356015] Total of 4 processors activated (18647.92 BogoMIPS).
Apr  8 19:01:39 Megatron kernel: [    0.357692] devtmpfs: initialized
Apr  8 19:01:39 Megatron kernel: [    0.358004] regulator: core version 0.5
Apr  8 19:01:39 Megatron kernel: [    0.358025] Time: 19:01:20  Date: 04/08/10
Apr  8 19:01:39 Megatron kernel: [    0.358062] NET: Registered protocol family 16
Apr  8 19:01:39 Megatron kernel: [    0.358156] EISA bus registered
Apr  8 19:01:39 Megatron kernel: [    0.358163] ACPI: bus type pci registered
Apr  8 19:01:39 Megatron kernel: [    0.358221] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
Apr  8 19:01:39 Megatron kernel: [    0.358223] PCI: Not using MMCONFIG.
Apr  8 19:01:39 Megatron kernel: [    0.358278] PCI: Using configuration type 1 for base access
Apr  8 19:01:39 Megatron kernel: [    0.359119] Trying to unpack rootfs image as initramfs...
Apr  8 19:01:39 Megatron kernel: [    0.388251] bio: create slab <bio-0> at 0
Apr  8 19:01:39 Megatron kernel: [    0.391566] ACPI: Executed 1 blocks of module-level executable AML code
Apr  8 19:01:39 Megatron kernel: [    0.400540] ACPI: Interpreter enabled
Apr  8 19:01:39 Megatron kernel: [    0.400550] ACPI: (supports S0 S1 S3 S4 S5)
Apr  8 19:01:39 Megatron kernel: [    0.400572] ACPI: Using IOAPIC for interrupt routing
Apr  8 19:01:39 Megatron kernel: [    0.400618] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
Apr  8 19:01:39 Megatron kernel: [    0.402952] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
Apr  8 19:01:39 Megatron kernel: [    0.402954] PCI: Using MMCONFIG for extended config space
Apr  8 19:01:39 Megatron kernel: [    0.409881] ACPI Warning: Incorrect checksum in table [OEMB] - D4, should be D3 (20090903/tbutils-314)
Apr  8 19:01:39 Megatron kernel: [    0.410007] ACPI: No dock devices found.
Apr  8 19:01:39 Megatron kernel: [    0.410115] ACPI: PCI Root Bridge [PCI0] (0000:00)
Apr  8 19:01:39 Megatron kernel: [    0.410205] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
Apr  8 19:01:39 Megatron kernel: [    0.410208] pci 0000:00:01.0: PME# disabled
Apr  8 19:01:39 Megatron kernel: [    0.410512] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
Apr  8 19:01:39 Megatron kernel: [    0.410516] pci 0000:00:1a.7: PME# disabled
Apr  8 19:01:39 Megatron kernel: [    0.410591] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
Apr  8 19:01:39 Megatron kernel: [    0.410594] pci 0000:00:1b.0: PME# disabled
Apr  8 19:01:39 Megatron kernel: [    0.410650] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
Apr  8 19:01:39 Megatron kernel: [    0.410653] pci 0000:00:1c.0: PME# disabled
Apr  8 19:01:39 Megatron kernel: [    0.410712] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
Apr  8 19:01:39 Megatron kernel: [    0.410715] pci 0000:00:1c.4: PME# disabled
Apr  8 19:01:39 Megatron kernel: [    0.410772] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
Apr  8 19:01:39 Megatron kernel: [    0.410775] pci 0000:00:1c.5: PME# disabled
Apr  8 19:01:39 Megatron kernel: [    0.411067] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
Apr  8 19:01:39 Megatron kernel: [    0.411071] pci 0000:00:1d.7: PME# disabled
Apr  8 19:01:39 Megatron kernel: [    0.411675] pci 0000:03:00.0: PME# supported from D0 D1 D3hot
Apr  8 19:01:39 Megatron kernel: [    0.411680] pci 0000:03:00.0: PME# disabled
Apr  8 19:01:39 Megatron kernel: [    0.411842] pci 0000:02:00.0: PME# supported from D3hot D3cold
Apr  8 19:01:39 Megatron kernel: [    0.411846] pci 0000:02:00.0: PME# disabled
Apr  8 19:01:39 Megatron kernel: [    0.412021] pci 0000:00:1e.0: transparent bridge
Apr  8 19:01:39 Megatron kernel: [    0.427507] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12 14 15)
Apr  8 19:01:39 Megatron kernel: [    0.427612] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 *11 12 14 15)
Apr  8 19:01:39 Megatron kernel: [    0.427711] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11 12 14 *15)
Apr  8 19:01:39 Megatron kernel: [    0.427810] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 10 11 12 14 15)
Apr  8 19:01:39 Megatron kernel: [    0.427909] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
Apr  8 19:01:39 Megatron kernel: [    0.428015] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 *14 15)
Apr  8 19:01:39 Megatron kernel: [    0.428115] ACPI: PCI Interrupt Link [LNKG] (IRQs *3 4 5 6 7 10 11 12 14 15)
Apr  8 19:01:39 Megatron kernel: [    0.428218] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 *7 10 11 12 14 15)
Apr  8 19:01:39 Megatron kernel: [    0.428319] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
Apr  8 19:01:39 Megatron kernel: [    0.428323] vgaarb: loaded
Apr  8 19:01:39 Megatron kernel: [    0.428423] SCSI subsystem initialized
Apr  8 19:01:39 Megatron kernel: [    0.428562] usbcore: registered new interface driver usbfs
Apr  8 19:01:39 Megatron kernel: [    0.428573] usbcore: registered new interface driver hub
Apr  8 19:01:39 Megatron kernel: [    0.428593] usbcore: registered new device driver usb
Apr  8 19:01:39 Megatron kernel: [    0.428699] ACPI: WMI: Mapper loaded
Apr  8 19:01:39 Megatron kernel: [    0.428700] PCI: Using ACPI for IRQ routing
Apr  8 19:01:39 Megatron kernel: [    0.428842] NetLabel: Initializing
Apr  8 19:01:39 Megatron kernel: [    0.428844] NetLabel:  domain hash size = 128
Apr  8 19:01:39 Megatron kernel: [    0.428845] NetLabel:  protocols = UNLABELED CIPSOv4
Apr  8 19:01:39 Megatron kernel: [    0.428856] NetLabel:  unlabeled traffic allowed by default
Apr  8 19:01:39 Megatron kernel: [    0.428887] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
Apr  8 19:01:39 Megatron kernel: [    0.428892] hpet0: 4 comparators, 64-bit 14.318180 MHz counter
Apr  8 19:01:39 Megatron kernel: [    0.436013] Switching to clocksource tsc
Apr  8 19:01:39 Megatron kernel: [    0.437894] AppArmor: AppArmor Filesystem Enabled
Apr  8 19:01:39 Megatron kernel: [    0.437912] pnp: PnP ACPI init
Apr  8 19:01:39 Megatron kernel: [    0.437932] ACPI: bus type pnp registered
Apr  8 19:01:39 Megatron kernel: [    0.440694] pnp: PnP ACPI: found 15 devices
Apr  8 19:01:39 Megatron kernel: [    0.440697] ACPI: ACPI bus type pnp unregistered
Apr  8 19:01:39 Megatron kernel: [    0.440700] PnPBIOS: Disabled by ACPI PNP
Apr  8 19:01:39 Megatron kernel: [    0.440712] system 00:01: iomem range 0xfed14000-0xfed19fff has been reserved
Apr  8 19:01:39 Megatron kernel: [    0.440719] system 00:06: ioport range 0x290-0x29f has been reserved
Apr  8 19:01:39 Megatron kernel: [    0.440725] system 00:07: ioport range 0x4d0-0x4d1 has been reserved
Apr  8 19:01:39 Megatron kernel: [    0.440727] system 00:07: ioport range 0x800-0x87f has been reserved
Apr  8 19:01:39 Megatron kernel: [    0.440730] system 00:07: ioport range 0x500-0x57f has been reserved
Apr  8 19:01:39 Megatron kernel: [    0.440732] system 00:07: iomem range 0xfed08000-0xfed08fff has been reserved
Apr  8 19:01:39 Megatron kernel: [    0.440735] system 00:07: iomem range 0xfed1c000-0xfed1ffff has been reserved
Apr  8 19:01:39 Megatron kernel: [    0.440737] system 00:07: iomem range 0xfed20000-0xfed3ffff has been reserved
Apr  8 19:01:39 Megatron kernel: [    0.440740] system 00:07: iomem range 0xfed50000-0xfed8ffff has been reserved
Apr  8 19:01:39 Megatron kernel: [    0.440745] system 00:0a: iomem range 0xffc00000-0xffefffff has been reserved
Apr  8 19:01:39 Megatron kernel: [    0.440750] system 00:0b: iomem range 0xfec00000-0xfec00fff could not be reserved
Apr  8 19:01:39 Megatron kernel: [    0.440753] system 00:0b: iomem range 0xfee00000-0xfee00fff has been reserved
Apr  8 19:01:39 Megatron kernel: [    0.440758] system 00:0d: iomem range 0xe0000000-0xefffffff has been reserved
Apr  8 19:01:39 Megatron kernel: [    0.440763] system 00:0e: iomem range 0x0-0x9ffff could not be reserved
Apr  8 19:01:39 Megatron kernel: [    0.440766] system 00:0e: iomem range 0xc0000-0xcffff could not be reserved
Apr  8 19:01:39 Megatron kernel: [    0.440768] system 00:0e: iomem range 0xe0000-0xfffff could not be reserved
Apr  8 19:01:39 Megatron kernel: [    0.440771] system 00:0e: iomem range 0x100000-0xbfffffff could not be reserved
Apr  8 19:01:39 Megatron kernel: [    0.475467] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
Apr  8 19:01:39 Megatron kernel: [    0.475470] pci 0000:00:01.0:   IO window: 0xc000-0xcfff
Apr  8 19:01:39 Megatron kernel: [    0.475474] pci 0000:00:01.0:   MEM window: 0xfa000000-0xfe8fffff
Apr  8 19:01:39 Megatron kernel: [    0.475477] pci 0000:00:01.0:   PREFETCH window: 0x000000c0000000-0x000000dfffffff
Apr  8 19:01:39 Megatron kernel: [    0.475481] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:04
Apr  8 19:01:39 Megatron kernel: [    0.475484] pci 0000:00:1c.0:   IO window: 0x1000-0x1fff
Apr  8 19:01:39 Megatron kernel: [    0.475488] pci 0000:00:1c.0:   MEM window: 0xf0000000-0xf03fffff
Apr  8 19:01:39 Megatron kernel: [    0.475492] pci 0000:00:1c.0:   PREFETCH window: 0x000000f8f00000-0x000000f8ffffff
Apr  8 19:01:39 Megatron kernel: [    0.475497] pci 0000:00:1c.4: PCI bridge, secondary bus 0000:03
Apr  8 19:01:39 Megatron kernel: [    0.475500] pci 0000:00:1c.4:   IO window: 0xe000-0xefff
Apr  8 19:01:39 Megatron kernel: [    0.475504] pci 0000:00:1c.4:   MEM window: 0xfea00000-0xfeafffff
Apr  8 19:01:39 Megatron kernel: [    0.475508] pci 0000:00:1c.4:   PREFETCH window: 0x000000f0400000-0x000000f05fffff
Apr  8 19:01:39 Megatron kernel: [    0.475513] pci 0000:00:1c.5: PCI bridge, secondary bus 0000:02
Apr  8 19:01:39 Megatron kernel: [    0.475516] pci 0000:00:1c.5:   IO window: 0xd000-0xdfff
Apr  8 19:01:39 Megatron kernel: [    0.475520] pci 0000:00:1c.5:   MEM window: 0xfe900000-0xfe9fffff
Apr  8 19:01:39 Megatron kernel: [    0.475524] pci 0000:00:1c.5:   PREFETCH window: 0x000000f0600000-0x000000f07fffff
Apr  8 19:01:39 Megatron kernel: [    0.475529] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:05
Apr  8 19:01:39 Megatron kernel: [    0.475531] pci 0000:00:1e.0:   IO window: disabled
Apr  8 19:01:39 Megatron kernel: [    0.475535] pci 0000:00:1e.0:   MEM window: 0xfeb00000-0xfebfffff
Apr  8 19:01:39 Megatron kernel: [    0.475538] pci 0000:00:1e.0:   PREFETCH window: disabled
Apr  8 19:01:39 Megatron kernel: [    0.475565] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Apr  8 19:01:39 Megatron kernel: [    0.475576] pci 0000:00:1c.0: enabling device (0106 -> 0107)
Apr  8 19:01:39 Megatron kernel: [    0.475584] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Apr  8 19:01:39 Megatron kernel: [    0.475594] pci 0000:00:1c.4: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Apr  8 19:01:39 Megatron kernel: [    0.475605] pci 0000:00:1c.5: PCI INT B -> GSI 16 (level, low) -> IRQ 16
Apr  8 19:01:39 Megatron kernel: [    0.475691] NET: Registered protocol family 2
Apr  8 19:01:39 Megatron kernel: [    0.475789] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Apr  8 19:01:39 Megatron kernel: [    0.476084] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Apr  8 19:01:39 Megatron kernel: [    0.476480] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Apr  8 19:01:39 Megatron kernel: [    0.476653] TCP: Hash tables configured (established 131072 bind 65536)
Apr  8 19:01:39 Megatron kernel: [    0.476655] TCP reno registered
Apr  8 19:01:39 Megatron kernel: [    0.476719] NET: Registered protocol family 1
Apr  8 19:01:39 Megatron kernel: [    0.477116] cpufreq-nforce2: No nForce2 chipset.
Apr  8 19:01:39 Megatron kernel: [    0.477139] Scanning for low memory corruption every 60 seconds
Apr  8 19:01:39 Megatron kernel: [    0.477230] audit: initializing netlink socket (disabled)
Apr  8 19:01:39 Megatron kernel: [    0.477238] type=2000 audit(1270753280.475:1): initialized
Apr  8 19:01:39 Megatron kernel: [    0.496130] highmem bounce pool size: 64 pages
Apr  8 19:01:39 Megatron kernel: [    0.496134] HugeTLB registered 4 MB page size, pre-allocated 0 pages
Apr  8 19:01:39 Megatron kernel: [    0.497569] VFS: Disk quotas dquot_6.5.2
Apr  8 19:01:39 Megatron kernel: [    0.497623] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Apr  8 19:01:39 Megatron kernel: [    0.498131] fuse init (API version 7.13)
Apr  8 19:01:39 Megatron kernel: [    0.498204] msgmni has been set to 1664
Apr  8 19:01:39 Megatron kernel: [    0.498529] alg: No test for stdrng (krng)
Apr  8 19:01:39 Megatron kernel: [    0.498585] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
Apr  8 19:01:39 Megatron kernel: [    0.498588] io scheduler noop registered
Apr  8 19:01:39 Megatron kernel: [    0.498589] io scheduler anticipatory registered
Apr  8 19:01:39 Megatron kernel: [    0.498591] io scheduler deadline registered
Apr  8 19:01:39 Megatron kernel: [    0.498624] io scheduler cfq registered (default)
Apr  8 19:01:39 Megatron kernel: [    0.499154] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Apr  8 19:01:39 Megatron kernel: [    0.499248] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Apr  8 19:01:39 Megatron kernel: [    0.499336] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
Apr  8 19:01:39 Megatron kernel: [    0.499340] ACPI: Power Button [PWRB]
Apr  8 19:01:39 Megatron kernel: [    0.499378] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
Apr  8 19:01:39 Megatron kernel: [    0.499380] ACPI: Power Button [PWRF]
Apr  8 19:01:39 Megatron kernel: [    0.500009] ACPI: SSDT bff8e0d0 001F3 (v01 DpgPmm  P001Ist 00000011 INTL 20051117)
Apr  8 19:01:39 Megatron kernel: [    0.500287] processor LNXCPU:00: registered as cooling_device0
Apr  8 19:01:39 Megatron kernel: [    0.500636] ACPI: SSDT bff8e2d0 001F3 (v01 DpgPmm  P002Ist 00000012 INTL 20051117)
Apr  8 19:01:39 Megatron kernel: [    0.500898] processor LNXCPU:01: registered as cooling_device1
Apr  8 19:01:39 Megatron kernel: [    0.501243] ACPI: SSDT bff8e4d0 001F3 (v01 DpgPmm  P003Ist 00000012 INTL 20051117)
Apr  8 19:01:39 Megatron kernel: [    0.501505] processor LNXCPU:02: registered as cooling_device2
Apr  8 19:01:39 Megatron kernel: [    0.501854] ACPI: SSDT bff8e6d0 001F3 (v01 DpgPmm  P004Ist 00000012 INTL 20051117)
Apr  8 19:01:39 Megatron kernel: [    0.502118] processor LNXCPU:03: registered as cooling_device3
Apr  8 19:01:39 Megatron kernel: [    0.504336] isapnp: Scanning for PnP cards...
Apr  8 19:01:39 Megatron kernel: [    0.505474] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
Apr  8 19:01:39 Megatron kernel: [    0.505566] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Apr  8 19:01:39 Megatron kernel: [    0.505965] 00:0c: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Apr  8 19:01:39 Megatron kernel: [    0.506861] brd: module loaded
Apr  8 19:01:39 Megatron kernel: [    0.507269] loop: module loaded
Apr  8 19:01:39 Megatron kernel: [    0.507332] input: Macintosh mouse button emulation as /devices/virtual/input/input2
Apr  8 19:01:39 Megatron kernel: [    0.507420] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Apr  8 19:01:39 Megatron kernel: [    0.507424] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
Apr  8 19:01:39 Megatron kernel: [    0.527846] Freeing initrd memory: 7646k freed
Apr  8 19:01:39 Megatron kernel: [    0.553278] scsi0 : ata_piix
Apr  8 19:01:39 Megatron kernel: [    0.553384] scsi1 : ata_piix
Apr  8 19:01:39 Megatron kernel: [    0.554586] ata1: SATA max UDMA/133 cmd 0xa000 ctl 0x9c00 bmdma 0x9480 irq 19
Apr  8 19:01:39 Megatron kernel: [    0.554591] ata2: SATA max UDMA/133 cmd 0x9880 ctl 0x9800 bmdma 0x9488 irq 19
Apr  8 19:01:39 Megatron kernel: [    0.554627] ata_piix 0000:00:1f.5: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Apr  8 19:01:39 Megatron kernel: [    0.554632] ata_piix 0000:00:1f.5: MAP [ P0 -- P1 -- ]
Apr  8 19:01:39 Megatron kernel: [    0.554725] scsi2 : ata_piix
Apr  8 19:01:39 Megatron kernel: [    0.554789] scsi3 : ata_piix
Apr  8 19:01:39 Megatron kernel: [    0.555972] ata3: SATA max UDMA/133 cmd 0xb000 ctl 0xac00 bmdma 0xa480 irq 19
Apr  8 19:01:39 Megatron kernel: [    0.555975] ata4: SATA max UDMA/133 cmd 0xa880 ctl 0xa800 bmdma 0xa488 irq 19
Apr  8 19:01:39 Megatron kernel: [    0.556096] pata_acpi 0000:03:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Apr  8 19:01:39 Megatron kernel: [    0.556136] pata_acpi 0000:03:00.0: PCI INT A disabled
Apr  8 19:01:39 Megatron kernel: [    0.556390] Fixed MDIO Bus: probed
Apr  8 19:01:39 Megatron kernel: [    0.556418] PPP generic driver version 2.4.2
Apr  8 19:01:39 Megatron kernel: [    0.556445] tun: Universal TUN/TAP device driver, 1.6
Apr  8 19:01:39 Megatron kernel: [    0.556447] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Apr  8 19:01:39 Megatron kernel: [    0.556514] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Apr  8 19:01:39 Megatron kernel: [    0.556534] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Apr  8 19:01:39 Megatron kernel: [    0.556545] ehci_hcd 0000:00:1a.7: EHCI Host Controller
Apr  8 19:01:39 Megatron kernel: [    0.556581] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
Apr  8 19:01:39 Megatron kernel: [    0.556601] ehci_hcd 0000:00:1a.7: debug port 1
Apr  8 19:01:39 Megatron kernel: [    0.560498] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xf9fffc00
Apr  8 19:01:39 Megatron kernel: [    0.575911] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
Apr  8 19:01:39 Megatron kernel: [    0.575984] usb usb1: configuration #1 chosen from 1 choice
Apr  8 19:01:39 Megatron kernel: [    0.576008] hub 1-0:1.0: USB hub found
Apr  8 19:01:39 Megatron kernel: [    0.576016] hub 1-0:1.0: 6 ports detected
Apr  8 19:01:39 Megatron kernel: [    0.576070] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Apr  8 19:01:39 Megatron kernel: [    0.576080] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Apr  8 19:01:39 Megatron kernel: [    0.576106] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
Apr  8 19:01:39 Megatron kernel: [    0.576126] ehci_hcd 0000:00:1d.7: debug port 1
Apr  8 19:01:39 Megatron kernel: [    0.580029] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xf9fff800
Apr  8 19:01:39 Megatron kernel: [    0.595910] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
Apr  8 19:01:39 Megatron kernel: [    0.595973] usb usb2: configuration #1 chosen from 1 choice
Apr  8 19:01:39 Megatron kernel: [    0.595996] hub 2-0:1.0: USB hub found
Apr  8 19:01:39 Megatron kernel: [    0.596001] hub 2-0:1.0: 6 ports detected
Apr  8 19:01:39 Megatron kernel: [    0.596048] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Apr  8 19:01:39 Megatron kernel: [    0.596061] uhci_hcd: USB Universal Host Controller Interface driver
Apr  8 19:01:39 Megatron kernel: [    0.596078] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Apr  8 19:01:39 Megatron kernel: [    0.596085] uhci_hcd 0000:00:1a.0: UHCI Host Controller
Apr  8 19:01:39 Megatron kernel: [    0.596110] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
Apr  8 19:01:39 Megatron kernel: [    0.596137] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000b800
Apr  8 19:01:39 Megatron kernel: [    0.596205] usb usb3: configuration #1 chosen from 1 choice
Apr  8 19:01:39 Megatron kernel: [    0.596228] hub 3-0:1.0: USB hub found
Apr  8 19:01:39 Megatron kernel: [    0.596234] hub 3-0:1.0: 2 ports detected
Apr  8 19:01:39 Megatron kernel: [    0.596275] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
Apr  8 19:01:39 Megatron kernel: [    0.596283] uhci_hcd 0000:00:1a.1: UHCI Host Controller
Apr  8 19:01:39 Megatron kernel: [    0.596310] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
Apr  8 19:01:39 Megatron kernel: [    0.596335] uhci_hcd 0000:00:1a.1: irq 21, io base 0x0000b880
Apr  8 19:01:39 Megatron kernel: [    0.596406] usb usb4: configuration #1 chosen from 1 choice
Apr  8 19:01:39 Megatron kernel: [    0.596427] hub 4-0:1.0: USB hub found
Apr  8 19:01:39 Megatron kernel: [    0.596433] hub 4-0:1.0: 2 ports detected
Apr  8 19:01:39 Megatron kernel: [    0.596468] uhci_hcd 0000:00:1a.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Apr  8 19:01:39 Megatron kernel: [    0.596476] uhci_hcd 0000:00:1a.2: UHCI Host Controller
Apr  8 19:01:39 Megatron kernel: [    0.596501] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
Apr  8 19:01:39 Megatron kernel: [    0.596520] uhci_hcd 0000:00:1a.2: irq 18, io base 0x0000bc00
Apr  8 19:01:39 Megatron kernel: [    0.596591] usb usb5: configuration #1 chosen from 1 choice
Apr  8 19:01:39 Megatron kernel: [    0.596612] hub 5-0:1.0: USB hub found
Apr  8 19:01:39 Megatron kernel: [    0.596617] hub 5-0:1.0: 2 ports detected
Apr  8 19:01:39 Megatron kernel: [    0.596653] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Apr  8 19:01:39 Megatron kernel: [    0.596660] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Apr  8 19:01:39 Megatron kernel: [    0.596689] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
Apr  8 19:01:39 Megatron kernel: [    0.596709] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000b080
Apr  8 19:01:39 Megatron kernel: [    0.596780] usb usb6: configuration #1 chosen from 1 choice
Apr  8 19:01:39 Megatron kernel: [    0.596801] hub 6-0:1.0: USB hub found
Apr  8 19:01:39 Megatron kernel: [    0.596806] hub 6-0:1.0: 2 ports detected
Apr  8 19:01:39 Megatron kernel: [    0.596842] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Apr  8 19:01:39 Megatron kernel: [    0.596849] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Apr  8 19:01:39 Megatron kernel: [    0.596875] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
Apr  8 19:01:39 Megatron kernel: [    0.596895] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000b400
Apr  8 19:01:39 Megatron kernel: [    0.596966] usb usb7: configuration #1 chosen from 1 choice
Apr  8 19:01:39 Megatron kernel: [    0.596987] hub 7-0:1.0: USB hub found
Apr  8 19:01:39 Megatron kernel: [    0.596992] hub 7-0:1.0: 2 ports detected
Apr  8 19:01:39 Megatron kernel: [    0.597027] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Apr  8 19:01:39 Megatron kernel: [    0.597034] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Apr  8 19:01:39 Megatron kernel: [    0.597067] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
Apr  8 19:01:39 Megatron kernel: [    0.597086] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000b480
Apr  8 19:01:39 Megatron kernel: [    0.597158] usb usb8: configuration #1 chosen from 1 choice
Apr  8 19:01:39 Megatron kernel: [    0.597179] hub 8-0:1.0: USB hub found
Apr  8 19:01:39 Megatron kernel: [    0.597185] hub 8-0:1.0: 2 ports detected
Apr  8 19:01:39 Megatron kernel: [    0.597271] PNP: No PS/2 controller found. Probing ports directly.
Apr  8 19:01:39 Megatron kernel: [    0.600234] serio: i8042 KBD port at 0x60,0x64 irq 1
Apr  8 19:01:39 Megatron kernel: [    0.600242] serio: i8042 AUX port at 0x60,0x64 irq 12
Apr  8 19:01:39 Megatron kernel: [    0.600406] mice: PS/2 mouse device common for all mice
Apr  8 19:01:39 Megatron kernel: [    0.600518] rtc_cmos 00:03: RTC can wake from S4
Apr  8 19:01:39 Megatron kernel: [    0.600555] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
Apr  8 19:01:39 Megatron kernel: [    0.600577] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
Apr  8 19:01:39 Megatron kernel: [    0.600690] device-mapper: uevent: version 1.0.3
Apr  8 19:01:39 Megatron kernel: [    0.600772] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
Apr  8 19:01:39 Megatron kernel: [    0.600851] device-mapper: multipath: version 1.1.0 loaded
Apr  8 19:01:39 Megatron kernel: [    0.600854] device-mapper: multipath round-robin: version 1.0.0 loaded
Apr  8 19:01:39 Megatron kernel: [    0.600957] EISA: Probing bus 0 at eisa.0
Apr  8 19:01:39 Megatron kernel: [    0.600963] Cannot allocate resource for EISA slot 1
Apr  8 19:01:39 Megatron kernel: [    0.600981] EISA: Detected 0 cards.
Apr  8 19:01:39 Megatron kernel: [    0.601087] cpuidle: using governor ladder
Apr  8 19:01:39 Megatron kernel: [    0.601089] cpuidle: using governor menu
Apr  8 19:01:39 Megatron kernel: [    0.601477] TCP cubic registered
Apr  8 19:01:39 Megatron kernel: [    0.601606] NET: Registered protocol family 10
Apr  8 19:01:39 Megatron kernel: [    0.602016] lo: Disabled Privacy Extensions
Apr  8 19:01:39 Megatron kernel: [    0.602306] NET: Registered protocol family 17
Apr  8 19:01:39 Megatron kernel: [    0.603144] Using IPI No-Shortcut mode
Apr  8 19:01:39 Megatron kernel: [    0.603218] registered taskstats version 1
Apr  8 19:01:39 Megatron kernel: [    0.603593]   Magic number: 6:564:40
Apr  8 19:01:39 Megatron kernel: [    0.603605] bdi 7:5: hash matches
Apr  8 19:01:39 Megatron kernel: [    0.603626] serial 00:0c: hash matches
Apr  8 19:01:39 Megatron kernel: [    0.603664] rtc_cmos 00:03: setting system clock to 2010-04-08 19:01:21 UTC (1270753281)
Apr  8 19:01:39 Megatron kernel: [    0.603667] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Apr  8 19:01:39 Megatron kernel: [    0.603668] EDD information not available.
Apr  8 19:01:39 Megatron kernel: [    0.857240] isapnp: No Plug & Play device found
Apr  8 19:01:39 Megatron kernel: [    1.032041] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Apr  8 19:01:39 Megatron kernel: [    1.032194] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Apr  8 19:01:39 Megatron kernel: [    1.040533] ata4.00: ATA-8: ST3500418AS, CC35, max UDMA/133
Apr  8 19:01:39 Megatron kernel: [    1.040537] ata4.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 0/32)
Apr  8 19:01:39 Megatron kernel: [    1.056391] ata4.00: configured for UDMA/133
Apr  8 19:01:39 Megatron kernel: [    1.072314] ata3.00: ATA-7: ST3250820AS, 3.AAE, max UDMA/133
Apr  8 19:01:39 Megatron kernel: [    1.072318] ata3.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 0/32)
Apr  8 19:01:39 Megatron kernel: [    1.138969] ata3.00: configured for UDMA/133
Apr  8 19:01:39 Megatron kernel: [    1.232009] usb 6-1: new low speed USB device using uhci_hcd and address 2
Apr  8 19:01:39 Megatron kernel: [    1.348067] ata1.00: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Apr  8 19:01:39 Megatron kernel: [    1.348079] ata1.01: SATA link down (SStatus 0 SControl 300)
Apr  8 19:01:39 Megatron kernel: [    1.348084] ata2.00: SATA link down (SStatus 0 SControl 300)
Apr  8 19:01:39 Megatron kernel: [    1.348095] ata2.01: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Apr  8 19:01:39 Megatron kernel: [    1.360591] ata1.00: ATA-8: WDC WD10EADS-67M2B0, 01.00A01, max UDMA/133
Apr  8 19:01:39 Megatron kernel: [    1.360594] ata1.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 0/32)
Apr  8 19:01:39 Megatron kernel: [    1.365313] ata2.01: ATAPI: ASUS    DRW-22B1LT, 1.00, max UDMA/100
Apr  8 19:01:39 Megatron kernel: [    1.372590] ata1.00: configured for UDMA/133
Apr  8 19:01:39 Megatron kernel: [    1.372706] scsi 0:0:0:0: Direct-Access     ATA      WDC WD10EADS-67M 01.0 PQ: 0 ANSI: 5
Apr  8 19:01:39 Megatron kernel: [    1.372856] sd 0:0:0:0: Attached scsi generic sg0 type 0
Apr  8 19:01:39 Megatron kernel: [    1.372862] sd 0:0:0:0: [sda] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
Apr  8 19:01:39 Megatron kernel: [    1.372908] sd 0:0:0:0: [sda] Write Protect is off
Apr  8 19:01:39 Megatron kernel: [    1.372930] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr  8 19:01:39 Megatron kernel: [    1.373054]  sda:
Apr  8 19:01:39 Megatron kernel: [    1.380209] ata2.01: configured for UDMA/100
Apr  8 19:01:39 Megatron kernel: [    1.383938] scsi 1:0:1:0: CD-ROM            ASUS     DRW-22B1LT       1.00 PQ: 0 ANSI: 5
Apr  8 19:01:39 Megatron kernel: [    1.392388] sr0: scsi3-mmc drive: 48x/12x writer dvd-ram cd/rw xa/form2 cdda tray
Apr  8 19:01:39 Megatron kernel: [    1.392392] Uniform CD-ROM driver Revision: 3.20
Apr  8 19:01:39 Megatron kernel: [    1.392526] sr 1:0:1:0: Attached scsi generic sg1 type 5
Apr  8 19:01:39 Megatron kernel: [    1.392641] scsi 2:0:0:0: Direct-Access     ATA      ST3250820AS      3.AA PQ: 0 ANSI: 5
Apr  8 19:01:39 Megatron kernel: [    1.392738] sd 2:0:0:0: [sdb] 488397168 512-byte logical blocks: (250 GB/232 GiB)
Apr  8 19:01:39 Megatron kernel: [    1.392749] sd 2:0:0:0: Attached scsi generic sg2 type 0
Apr  8 19:01:39 Megatron kernel: [    1.392779] sd 2:0:0:0: [sdb] Write Protect is off
Apr  8 19:01:39 Megatron kernel: [    1.392802] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr  8 19:01:39 Megatron kernel: [    1.392841] scsi 3:0:0:0: Direct-Access     ATA      ST3500418AS      CC35 PQ: 0 ANSI: 5
Apr  8 19:01:39 Megatron kernel: [    1.392909]  sdb:
Apr  8 19:01:39 Megatron kernel: [    1.392954] sd 3:0:0:0: Attached scsi generic sg3 type 0
Apr  8 19:01:39 Megatron kernel: [    1.392990] sd 3:0:0:0: [sdc] 976773168 512-byte logical blocks: (500 GB/465 GiB)
Apr  8 19:01:39 Megatron kernel: [    1.393030] sd 3:0:0:0: [sdc] Write Protect is off
Apr  8 19:01:39 Megatron kernel: [    1.393052] sd 3:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr  8 19:01:39 Megatron kernel: [    1.393171]  sdc: sda1 sda2
Apr  8 19:01:39 Megatron kernel: [    1.400765] sd 0:0:0:0: [sda] Attached SCSI disk
Apr  8 19:01:39 Megatron kernel: [    1.407026]  sdc1
Apr  8 19:01:39 Megatron kernel: [    1.407225] sd 3:0:0:0: [sdc] Attached SCSI disk
Apr  8 19:01:39 Megatron kernel: [    1.411857]  sdb1
Apr  8 19:01:39 Megatron kernel: [    1.412050] sd 2:0:0:0: [sdb] Attached SCSI disk
Apr  8 19:01:39 Megatron kernel: [    1.412076] Freeing unused kernel memory: 656k freed
Apr  8 19:01:39 Megatron kernel: [    1.412369] Write protecting the kernel text: 4672k
Apr  8 19:01:39 Megatron kernel: [    1.412416] Write protecting the kernel read-only data: 1840k
Apr  8 19:01:39 Megatron kernel: [    1.417821] usb 6-1: configuration #1 chosen from 1 choice
Apr  8 19:01:39 Megatron kernel: [    1.427119] udev: starting version 151
Apr  8 19:01:39 Megatron kernel: [    1.456836] ATL1E 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Apr  8 19:01:39 Megatron kernel: [    1.469165] pata_marvell 0000:03:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Apr  8 19:01:39 Megatron kernel: [    1.478231] scsi4 : pata_marvell
Apr  8 19:01:39 Megatron kernel: [    1.483008] scsi5 : pata_marvell
Apr  8 19:01:39 Megatron kernel: [    1.483071] ata5: PATA max UDMA/100 cmd 0xec00 ctl 0xe880 bmdma 0xe400 irq 16
Apr  8 19:01:39 Megatron kernel: [    1.483074] ata6: DUMMY
Apr  8 19:01:39 Megatron kernel: [    1.659492] usb 7-1: new low speed USB device using uhci_hcd and address 2
Apr  8 19:01:39 Megatron kernel: [    1.673138] ata5.00: ATA-8: WDC WD5000AAKB-00H8A0, 05.04E05, max UDMA/133
Apr  8 19:01:39 Megatron kernel: [    1.673142] ata5.00: 976773168 sectors, multi 0: LBA48 
Apr  8 19:01:39 Megatron kernel: [    1.688661] ata5.00: configured for UDMA/100
Apr  8 19:01:39 Megatron kernel: [    1.688756] scsi 4:0:0:0: Direct-Access     ATA      WDC WD5000AAKB-0 05.0 PQ: 0 ANSI: 5
Apr  8 19:01:39 Megatron kernel: [    1.688907] sd 4:0:0:0: [sdd] 976773168 512-byte logical blocks: (500 GB/465 GiB)
Apr  8 19:01:39 Megatron kernel: [    1.688919] sd 4:0:0:0: Attached scsi generic sg4 type 0
Apr  8 19:01:39 Megatron kernel: [    1.688951] sd 4:0:0:0: [sdd] Write Protect is off
Apr  8 19:01:39 Megatron kernel: [    1.688976] sd 4:0:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr  8 19:01:39 Megatron kernel: [    1.689111]  sdd: sdd1
Apr  8 19:01:39 Megatron kernel: [    1.695273] sd 4:0:0:0: [sdd] Attached SCSI disk
Apr  8 19:01:39 Megatron kernel: [    1.698816] usbcore: registered new interface driver hiddev
Apr  8 19:01:39 Megatron kernel: [    1.727831] input: Logitech Logitech Dual Action as /devices/pci0000:00/0000:00:1d.0/usb6/6-1/6-1:1.0/input/input3
Apr  8 19:01:39 Megatron kernel: [    1.727906] generic-usb 0003:046D:C216.0001: input,hidraw0: USB HID v1.10 Joystick [Logitech Logitech Dual Action] on usb-0000:00:1d.0-1/input0
Apr  8 19:01:39 Megatron kernel: [    1.727935] usbcore: registered new interface driver usbhid
Apr  8 19:01:39 Megatron kernel: [    1.727938] usbhid: v2.6:USB HID core driver
Apr  8 19:01:39 Megatron kernel: [    1.838035] usb 7-1: configuration #1 chosen from 1 choice
Apr  8 19:01:39 Megatron kernel: [    1.855182] input: Logitech Logitech USB Keyboard as /devices/pci0000:00/0000:00:1d.1/usb7/7-1/7-1:1.0/input/input4
Apr  8 19:01:39 Megatron kernel: [    1.855246] generic-usb 0003:046D:C315.0002: input,hidraw1: USB HID v1.10 Keyboard [Logitech Logitech USB Keyboard] on usb-0000:00:1d.1-1/input0
Apr  8 19:01:39 Megatron kernel: [    2.092008] usb 7-2: new low speed USB device using uhci_hcd and address 3
Apr  8 19:01:39 Megatron kernel: [    2.270032] usb 7-2: configuration #1 chosen from 1 choice
Apr  8 19:01:39 Megatron kernel: [    2.297173] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.1/usb7/7-2/7-2:1.0/input/input5
Apr  8 19:01:39 Megatron kernel: [    2.297247] generic-usb 0003:046D:C51B.0003: input,hidraw2: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:1d.1-2/input0
Apr  8 19:01:39 Megatron kernel: [    2.311053] generic-usb 0003:046D:C51B.0004: hiddev96,hidraw3: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1d.1-2/input1
Apr  8 19:01:39 Megatron kernel: [    6.785318] EXT4-fs (sda2): mounted filesystem with ordered data mode
Apr  8 19:01:39 Megatron kernel: [   17.530623] udev: starting version 151
Apr  8 19:01:39 Megatron kernel: [   17.708622] type=1505 audit(1270724498.604:2):  operation="profile_load" pid=562 name="/sbin/dhclient3"
Apr  8 19:01:39 Megatron kernel: [   17.709235] type=1505 audit(1270724498.604:3):  operation="profile_load" pid=562 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Apr  8 19:01:39 Megatron kernel: [   17.709546] type=1505 audit(1270724498.604:4):  operation="profile_load" pid=562 name="/usr/lib/connman/scripts/dhclient-script"
Apr  8 19:01:39 Megatron kernel: [   17.928458] Linux agpgart interface v0.103
Apr  8 19:01:39 Megatron kernel: [   18.224977] lp: driver loaded but no devices found
Apr  8 19:01:39 Megatron kernel: [   18.231148] cfg80211: Calling CRDA to update world regulatory domain
Apr  8 19:01:39 Megatron kernel: [   18.271401] vga16fb: mapped to 0xc00a0000
Apr  8 19:01:39 Megatron kernel: [   18.271466] fb0: VGA16 VGA frame buffer device
Apr  8 19:01:39 Megatron kernel: [   18.450324] cfg80211: World regulatory domain updated:
Apr  8 19:01:39 Megatron kernel: [   18.450328] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Apr  8 19:01:39 Megatron kernel: [   18.450331] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Apr  8 19:01:39 Megatron kernel: [   18.450333] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Apr  8 19:01:39 Megatron kernel: [   18.450335] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Apr  8 19:01:39 Megatron kernel: [   18.450337] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Apr  8 19:01:39 Megatron kernel: [   18.450339] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Apr  8 19:01:39 Megatron kernel: [   18.533632] nvidia: module license 'NVIDIA' taints kernel.
Apr  8 19:01:39 Megatron kernel: [   18.533636] Disabling lock debugging due to kernel taint
Apr  8 19:01:39 Megatron kernel: [   18.692278] ADDRCONF(NETDEV_UP): eth0: link is not ready
Apr  8 19:01:39 Megatron kernel: [   18.699452] type=1505 audit(1270724499.592:5):  operation="profile_load" pid=831 name="/usr/share/gdm/guest-session/Xsession"
Apr  8 19:01:39 Megatron kernel: [   18.701091] type=1505 audit(1270724499.596:6):  operation="profile_replace" pid=832 name="/sbin/dhclient3"
Apr  8 19:01:39 Megatron kernel: [   18.701702] type=1505 audit(1270724499.596:7):  operation="profile_replace" pid=832 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Apr  8 19:01:39 Megatron kernel: [   18.702020] type=1505 audit(1270724499.596:8):  operation="profile_replace" pid=832 name="/usr/lib/connman/scripts/dhclient-script"
Apr  8 19:01:39 Megatron kernel: [   18.704965] type=1505 audit(1270724499.600:9):  operation="profile_load" pid=833 name="/usr/bin/evince"
Apr  8 19:01:39 Megatron kernel: [   18.712393] type=1505 audit(1270724499.608:10):  operation="profile_load" pid=833 name="/usr/bin/evince-previewer"
Apr  8 19:01:39 Megatron kernel: [   18.716971] type=1505 audit(1270724499.612:11):  operation="profile_load" pid=833 name="/usr/bin/evince-thumbnailer"
Apr  8 19:01:40 Megatron kernel: [   19.334997] vboxdrv: fAsync=0 offMin=0x42f offMax=0x17fb
Apr  8 19:01:40 Megatron kernel: [   19.335108] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
Apr  8 19:01:40 Megatron kernel: [   19.343856] ath5k 0000:05:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Apr  8 19:01:40 Megatron kernel: [   19.343988] ath5k 0000:05:00.0: registered as 'phy0'
Apr  8 19:01:40 Megatron kernel: [   19.477451] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Apr  8 19:01:40 Megatron kernel: [   19.477459] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
Apr  8 19:01:40 Megatron kernel: [   19.477857] NVRM: loading NVIDIA UNIX x86 Kernel Module  195.36.15  Thu Mar 11 21:41:46 PST 2010
Apr  8 19:01:40 Megatron kernel: [   19.494224] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Apr  8 19:01:40 Megatron kernel: [   19.516745] Console: switching to colour frame buffer device 80x30
Apr  8 19:01:40 Megatron kernel: [   19.523728] ppdev: user-space parallel port driver
Apr  8 19:01:40 Megatron kernel: [   19.895750] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input6
Apr  8 19:01:40 Megatron kernel: [   20.094960] ath5k phy0: Atheros AR2413 chip found (MAC: 0x78, PHY: 0x45)
Apr  8 19:01:40 Megatron kernel: [   20.095129] cfg80211: Calling CRDA for country: CN
Apr  8 19:01:40 Megatron kernel: [   20.097775] cfg80211: Regulatory domain changed to country: CN
Apr  8 19:01:40 Megatron kernel: [   20.097778] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Apr  8 19:01:40 Megatron kernel: [   20.097780] 	(2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
Apr  8 19:01:40 Megatron kernel: [   20.097782] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (N/A, 3000 mBm)
Apr  8 19:01:41 Megatron kernel: [   20.179788] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Apr  8 19:01:48 Megatron kernel: [   27.753171] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Apr  8 19:01:48 Megatron kernel: [   27.828211] padlock: VIA PadLock not detected.
Apr  8 19:02:38 Megatron pulseaudio[1298]: ratelimit.c: 2 events suppressed


Then it crashed

---

### Post by whoop on 2010-04-09
Did you experience a system crash, then reboot and then view /var/log/messages ? If yes, then you need earlier data in that log (or is that all the data there was).
All the data you provided was from around 19:01, if that was the last boot than there is no interesting data to be collected from that...

---

