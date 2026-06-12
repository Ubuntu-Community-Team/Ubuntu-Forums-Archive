---
title: "- PLZ help my ubuntu freezes so often -"
date: 2011-01-18
forum: New to Ubuntu
---

### Post by Objectivity on 2011-01-18
Hi,

 I was wathing movie and was downloading few files with Vuze ( Torrent ) ... got freezed totally. I could move the mouse but could not type anything. NOTHING was working but the mouse. This happnes every week or so! here is the log file of messages druing the crash... PLZ examine it and   [I]look for any anomaly as I can't.

I HATE getting freezed so often using linux !](*,)  I feel like I am STILL using damn shaky windows.  

 ```
Jan 18 18:30:09 x-laptop kernel: [ 6865.423312] warning: `VirtualBox' uses 32-bit capabilities (legacy support in use)
Jan 18 18:34:45 x-laptop kernel: [ 7141.153286] atkbd.c: Unknown key pressed (translated set 2, code 0x81 on isa0060/serio0).
Jan 18 18:34:45 x-laptop kernel: [ 7141.153295] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
Jan 18 18:34:45 x-laptop kernel: [ 7141.441151] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
Jan 18 18:34:45 x-laptop kernel: [ 7141.441159] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
Jan 18 19:31:14 x-laptop kernel: [10530.700395] atkbd.c: Unknown key pressed (translated set 2, code 0x81 on isa0060/serio0).
Jan 18 19:31:14 x-laptop kernel: [10530.700399] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
Jan 18 19:31:14 x-laptop kernel: [10530.988585] atkbd.c: Unknown key released (translated set 2, code 0x81 on isa0060/serio0).
Jan 18 19:31:14 x-laptop kernel: [10530.988589] atkbd.c: Use 'setkeycodes e001 <keycode>' to make it known.
Jan 18 19:32:50 x-laptop kernel: imklog 4.2.0, log source = /proc/kmsg started.
Jan 18 19:32:50 x-laptop rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="501" x-info="http://www.rsyslog.com"] (re)start
Jan 18 19:32:50 x-laptop rsyslogd: rsyslogd's groupid changed to 103
Jan 18 19:32:50 x-laptop rsyslogd: rsyslogd's userid changed to 101
Jan 18 19:32:50 x-laptop kernel: [    0.000000] Initializing cgroup subsys cpuset
Jan 18 19:32:50 x-laptop kernel: [    0.000000] Initializing cgroup subsys cpu
Jan 18 19:32:50 x-laptop kernel: [    0.000000] Linux version 2.6.32-27-generic (buildd@crested) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #49-Ubuntu SMP Thu Dec 2 00:51:09 UTC 2010 (Ubuntu 2.6.32-27.49-generic 2.6.32.26+drm33.12)
Jan 18 19:32:50 x-laptop kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-27-generic root=UUID=417b0aaa-3b9d-4239-9f91-7984ec2842fe ro quiet splash
Jan 18 19:32:50 x-laptop kernel: [    0.000000] KERNEL supported cpus:
Jan 18 19:32:50 x-laptop kernel: [    0.000000]   Intel GenuineIntel
Jan 18 19:32:50 x-laptop kernel: [    0.000000]   AMD AuthenticAMD
Jan 18 19:32:50 x-laptop kernel: [    0.000000]   Centaur CentaurHauls
Jan 18 19:32:50 x-laptop kernel: [    0.000000] BIOS-provided physical RAM map:
Jan 18 19:32:50 x-laptop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 0000000000099400 (usable)
Jan 18 19:32:50 x-laptop kernel: [    0.000000]  BIOS-e820: 0000000000099400 - 00000000000a0000 (reserved)
Jan 18 19:32:50 x-laptop kernel: [    0.000000]  BIOS-e820: 00000000000d0000 - 00000000000d4000 (reserved)
Jan 18 19:32:50 x-laptop kernel: [    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
Jan 18 19:32:50 x-laptop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 00000000bf8a1000 (usable)
Jan 18 19:32:50 x-laptop kernel: [    0.000000]  BIOS-e820: 00000000bf8a1000 - 00000000bf8a7000 (reserved)
Jan 18 19:32:50 x-laptop kernel: [    0.000000]  BIOS-e820: 00000000bf8a7000 - 00000000bf9bb000 (usable)
Jan 18 19:32:50 x-laptop kernel: [    0.000000]  BIOS-e820: 00000000bf9bb000 - 00000000bfa0f000 (reserved)
Jan 18 19:32:50 x-laptop kernel: [    0.000000]  BIOS-e820: 00000000bfa0f000 - 00000000bfb08000 (usable)
Jan 18 19:32:50 x-laptop kernel: [    0.000000]  BIOS-e820: 00000000bfb08000 - 00000000bfd0f000 (reserved)
Jan 18 19:32:50 x-laptop kernel: [    0.000000]  BIOS-e820: 00000000bfd0f000 - 00000000bfd18000 (usable)
Jan 18 19:32:50 x-laptop kernel: [    0.000000]  BIOS-e820: 00000000bfd18000 - 00000000bfd1f000 (reserved)
Jan 18 19:32:50 x-laptop kernel: [    0.000000]  BIOS-e820: 00000000bfd1f000 - 00000000bfd67000 (usable)
Jan 18 19:32:50 x-laptop kernel: [    0.000000]  BIOS-e820: 00000000bfd67000 - 00000000bfd9f000 (ACPI NVS)
Jan 18 19:32:50 x-laptop kernel: [    0.000000]  BIOS-e820: 00000000bfd9f000 - 00000000bfde3000 (usable)
Jan 18 19:32:50 x-laptop kernel: [    0.000000]  BIOS-e820: 00000000bfde3000 - 00000000bfdff000 (ACPI data)
Jan 18 19:32:50 x-laptop kernel: [    0.000000]  BIOS-e820: 00000000bfdff000 - 00000000bfe00000 (usable)
Jan 18 19:32:50 x-laptop kernel: [    0.000000]  BIOS-e820: 0000000100000000 - 0000000140000000 (usable)
Jan 18 19:32:50 x-laptop kernel: [    0.000000] DMI present.
Jan 18 19:32:50 x-laptop kernel: [    0.000000] Phoenix BIOS detected: BIOS may corrupt low RAM, working around it.
Jan 18 19:32:50 x-laptop kernel: [    0.000000] last_pfn = 0x140000 max_arch_pfn = 0x400000000
Jan 18 19:32:50 x-laptop kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Jan 18 19:32:50 x-laptop kernel: [    0.000000] last_pfn = 0xbfe00 max_arch_pfn = 0x400000000
Jan 18 19:32:50 x-laptop kernel: [    0.000000] Scanning 0 areas for low memory corruption
Jan 18 19:32:50 x-laptop kernel: [    0.000000] modified physical RAM map:
Jan 18 19:32:50 x-laptop kernel: [    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
Jan 18 19:32:50 x-laptop kernel: [    0.000000]  modified: 0000000000010000 - 0000000000099400 (usable)
Jan 18 19:32:50 x-laptop kernel: [    0.000000]  modified: 0000000000099400 - 00000000000a0000 (reserved)
Jan 18 19:32:50 x-laptop kernel: [    0.000000]  modified: 00000000000d0000 - 00000000000d4000 (reserved)
Jan 18 19:32:50 x-laptop kernel: [    0.000000]  modified: 00000000000e4000 - 0000000000100000 (reserved)
Jan 18 19:32:50 x-laptop kernel: [    0.000000]  modified: 0000000000100000 - 00000000bf8a1000 (usable)
Jan 18 19:32:50 x-laptop kernel: [    0.000000]  modified: 00000000bf8a1000 - 00000000bf8a7000 (reserved)
Jan 18 19:32:50 x-laptop kernel: [    0.000000]  modified: 00000000bf8a7000 - 00000000bf9bb000 (usable)
Jan 18 19:32:50 x-laptop kernel: [    0.000000]  modified: 00000000bf9bb000 - 00000000bfa0f000 (reserved)
Jan 18 19:32:50 x-laptop kernel: [    0.000000]  modified: 00000000bfa0f000 - 00000000bfb08000 (usable)
Jan 18 19:32:50 x-laptop kernel: [    0.000000]  modified: 00000000bfb08000 - 00000000bfd0f000 (reserved)
Jan 18 19:32:50 x-laptop kernel: [    0.000000]  modified: 00000000bfd0f000 - 00000000bfd18000 (usable)
Jan 18 19:32:50 x-laptop kernel: [    0.000000]  modified: 00000000bfd18000 - 00000000bfd1f000 (reserved)
Jan 18 19:32:50 x-laptop kernel: [    0.000000]  modified: 00000000bfd1f000 - 00000000bfd67000 (usable)
Jan 18 19:32:50 x-laptop kernel: [    0.000000]  modified: 00000000bfd67000 - 00000000bfd9f000 (ACPI NVS)
Jan 18 19:32:50 x-laptop kernel: [    0.000000]  modified: 00000000bfd9f000 - 00000000bfde3000 (usable)
Jan 18 19:32:50 x-laptop kernel: [    0.000000]  modified: 00000000bfde3000 - 00000000bfdff000 (ACPI data)
Jan 18 19:32:50 x-laptop kernel: [    0.000000]  modified: 00000000bfdff000 - 00000000bfe00000 (usable)
Jan 18 19:32:50 x-laptop kernel: [    0.000000]  modified: 0000000100000000 - 0000000140000000 (usable)
Jan 18 19:32:50 x-laptop kernel: [    0.000000] init_memory_mapping: 0000000000000000-00000000bfe00000
Jan 18 19:32:50 x-laptop kernel: [    0.000000] NX (Execute Disable) protection: active
Jan 18 19:32:50 x-laptop kernel: [    0.000000] init_memory_mapping: 0000000100000000-0000000140000000
Jan 18 19:32:50 x-laptop kernel: [    0.000000] NX (Execute Disable) protection: active
Jan 18 19:32:50 x-laptop kernel: [    0.000000] RAMDISK: 377fc000 - 37fefbd9
Jan 18 19:32:50 x-laptop kernel: [    0.000000] ACPI: RSDP 00000000000f7240 00024 (v02 PTLTD )
Jan 18 19:32:50 x-laptop kernel: [    0.000000] ACPI: XSDT 00000000bfdf762b 00064 (v01 MSTEST TESTONLY 06040000  LTP 00000000)
Jan 18 19:32:50 x-laptop kernel: [    0.000000] ACPI: FACP 00000000bfde3000 000F4 (v03 INTEL  CRESTLNE 06040000 ALAN 00000001)
Jan 18 19:32:50 x-laptop kernel: [    0.000000] ACPI: DSDT 00000000bfde8000 07567 (v02 Intel  CANTIGA  06040000 INTL 20050624)
Jan 18 19:32:50 x-laptop kernel: [    0.000000] ACPI: FACS 00000000bfd9efc0 00040
Jan 18 19:32:50 x-laptop kernel: [    0.000000] ACPI: HPET 00000000bfdfed86 00038 (v01 INTEL  CRESTLNE 06040000 LOHR 0000005A)
Jan 18 19:32:50 x-laptop kernel: [    0.000000] ACPI: MCFG 00000000bfdfedbe 0003C (v01 INTEL  CRESTLNE 06040000 LOHR 0000005A)
Jan 18 19:32:50 x-laptop kernel: [    0.000000] ACPI: APIC 00000000bfdfedfa 00068 (v01 PTLTD  ? APIC   06040000  LTP 00000000)
Jan 18 19:32:50 x-laptop kernel: [    0.000000] ACPI: SLIC 00000000bfdfee62 00176 (v01 MSTEST TESTONLY 06040000  LTP 00000000)
Jan 18 19:32:50 x-laptop kernel: [    0.000000] ACPI: SSDT 00000000bfde7000 00655 (v01  PmRef    CpuPm 00003000 INTL 20050624)
Jan 18 19:32:50 x-laptop kernel: [    0.000000] ACPI: SSDT 00000000bfde6000 00259 (v01  PmRef  Cpu0Tst 00003000 INTL 20050624)
Jan 18 19:32:50 x-laptop kernel: [    0.000000] ACPI: SSDT 00000000bfde5000 0020F (v01  PmRef    ApTst 00003000 INTL 20050624)
Jan 18 19:32:50 x-laptop kernel: [    0.000000] No NUMA configuration found
Jan 18 19:32:50 x-laptop kernel: [    0.000000] Faking a node at 0000000000000000-0000000140000000
Jan 18 19:32:50 x-laptop kernel: [    0.000000] Bootmem setup node 0 0000000000000000-0000000140000000
Jan 18 19:32:50 x-laptop kernel: [    0.000000]   NODE_DATA [0000000000013000 - 0000000000017fff]
Jan 18 19:32:50 x-laptop kernel: [    0.000000]   bootmap [0000000000018000 -  000000000003ffff] pages 28
Jan 18 19:32:50 x-laptop kernel: [    0.000000] (8 early reservations) ==> bootmem [0000000000 - 0140000000]
Jan 18 19:32:50 x-laptop kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
Jan 18 19:32:50 x-laptop kernel: [    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
Jan 18 19:32:50 x-laptop kernel: [    0.000000]   #2 [0001000000 - 0001a2fa64]    TEXT DATA BSS ==> [0001000000 - 0001a2fa64]
Jan 18 19:32:50 x-laptop kernel: [    0.000000]   #3 [00377fc000 - 0037fefbd9]          RAMDISK ==> [00377fc000 - 0037fefbd9]
Jan 18 19:32:50 x-laptop kernel: [    0.000000]   #4 [0000099400 - 0000100000]    BIOS reserved ==> [0000099400 - 0000100000]
Jan 18 19:32:50 x-laptop kernel: [    0.000000]   #5 [0001a30000 - 0001a3023c]              BRK ==> [0001a30000 - 0001a3023c]
Jan 18 19:32:50 x-laptop kernel: [    0.000000]   #6 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]
Jan 18 19:32:50 x-laptop kernel: [    0.000000]   #7 [0000012000 - 0000013000]          PGTABLE ==> [0000012000 - 0000013000]
Jan 18 19:32:50 x-laptop kernel: [    0.000000] found SMP MP-table at [ffff8800000f72d0] f72d0
Jan 18 19:32:50 x-laptop kernel: [    0.000000] Zone PFN ranges:
Jan 18 19:32:50 x-laptop kernel: [    0.000000]   DMA      0x00000010 -> 0x00001000
Jan 18 19:32:50 x-laptop kernel: [    0.000000]   DMA32    0x00001000 -> 0x00100000
Jan 18 19:32:50 x-laptop kernel: [    0.000000]   Normal   0x00100000 -> 0x00140000
Jan 18 19:32:50 x-laptop kernel: [    0.000000] Movable zone start PFN for each node
Jan 18 19:32:50 x-laptop kernel: [    0.000000] early_node_map[9] active PFN ranges
Jan 18 19:32:50 x-laptop kernel: [    0.000000]     0: 0x00000010 -> 0x00000099
Jan 18 19:32:50 x-laptop kernel: [    0.000000]     0: 0x00000100 -> 0x000bf8a1
Jan 18 19:32:50 x-laptop kernel: [    0.000000]     0: 0x000bf8a7 -> 0x000bf9bb
Jan 18 19:32:50 x-laptop kernel: [    0.000000]     0: 0x000bfa0f -> 0x000bfb08
Jan 18 19:32:50 x-laptop kernel: [    0.000000]     0: 0x000bfd0f -> 0x000bfd18
Jan 18 19:32:50 x-laptop kernel: [    0.000000]     0: 0x000bfd1f -> 0x000bfd67
Jan 18 19:32:50 x-laptop kernel: [    0.000000]     0: 0x000bfd9f -> 0x000bfde3
Jan 18 19:32:50 x-laptop kernel: [    0.000000]     0: 0x000bfdff -> 0x000bfe00
Jan 18 19:32:50 x-laptop kernel: [    0.000000]     0: 0x00100000 -> 0x00140000
Jan 18 19:32:50 x-laptop kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x408
Jan 18 19:32:50 x-laptop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Jan 18 19:32:50 x-laptop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Jan 18 19:32:50 x-laptop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Jan 18 19:32:50 x-laptop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Jan 18 19:32:50 x-laptop kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Jan 18 19:32:50 x-laptop kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
Jan 18 19:32:50 x-laptop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
Jan 18 19:32:50 x-laptop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Jan 18 19:32:50 x-laptop kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Jan 18 19:32:50 x-laptop kernel: [    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
Jan 18 19:32:50 x-laptop kernel: [    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
Jan 18 19:32:50 x-laptop kernel: [    0.000000] PM: Registered nosave memory: 0000000000099000 - 000000000009a000
Jan 18 19:32:50 x-laptop kernel: [    0.000000] PM: Registered nosave memory: 000000000009a000 - 00000000000a0000
Jan 18 19:32:50 x-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d0000
Jan 18 19:32:50 x-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000d0000 - 00000000000d4000
Jan 18 19:32:50 x-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000d4000 - 00000000000e4000
Jan 18 19:32:50 x-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
Jan 18 19:32:50 x-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000bf8a1000 - 00000000bf8a7000
Jan 18 19:32:50 x-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000bf9bb000 - 00000000bfa0f000
Jan 18 19:32:50 x-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000bfb08000 - 00000000bfd0f000
Jan 18 19:32:50 x-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000bfd18000 - 00000000bfd1f000
Jan 18 19:32:50 x-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000bfd67000 - 00000000bfd9f000
Jan 18 19:32:50 x-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000bfde3000 - 00000000bfdff000
Jan 18 19:32:50 x-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000bfe00000 - 0000000100000000
Jan 18 19:32:50 x-laptop kernel: [    0.000000] Allocating PCI resources starting at bfe00000 (gap: bfe00000:40200000)
Jan 18 19:32:50 x-laptop kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Jan 18 19:32:50 x-laptop kernel: [    0.000000] NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:2 nr_node_ids:1
Jan 18 19:32:50 x-laptop kernel: [    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880028200000 s91544 r8192 d23144 u1048576
Jan 18 19:32:50 x-laptop kernel: [    0.000000] pcpu-alloc: s91544 r8192 d23144 u1048576 alloc=1*2097152
Jan 18 19:32:50 x-laptop kernel: [    0.000000] pcpu-alloc: [0] 0 1 
Jan 18 19:32:50 x-laptop kernel: [    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1029217
Jan 18 19:32:50 x-laptop kernel: [    0.000000] Policy zone: Normal
Jan 18 19:32:50 x-laptop kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-27-generic root=UUID=417b0aaa-3b9d-4239-9f91-7984ec2842fe ro quiet splash
Jan 18 19:32:50 x-laptop kernel: [    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
Jan 18 19:32:50 x-laptop kernel: [    0.000000] Initializing CPU#0
Jan 18 19:32:50 x-laptop kernel: [    0.000000] Checking aperture...
Jan 18 19:32:50 x-laptop kernel: [    0.000000] No AGP bridge found
Jan 18 19:32:50 x-laptop kernel: [    0.000000] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
Jan 18 19:32:50 x-laptop kernel: [    0.000000] Placing 64MB software IO TLB between ffff880020000000 - ffff880024000000
Jan 18 19:32:50 x-laptop kernel: [    0.000000] software IO TLB at phys 0x20000000 - 0x24000000
Jan 18 19:32:50 x-laptop kernel: [    0.000000] Memory: 4046620k/5242880k available (5422k kernel code, 1053900k absent, 142360k reserved, 2979k data, 876k init)
Jan 18 19:32:50 x-laptop kernel: [    0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
Jan 18 19:32:50 x-laptop kernel: [    0.000000] Hierarchical RCU implementation.
Jan 18 19:32:50 x-laptop kernel: [    0.000000] NR_IRQS:4352 nr_irqs:424
Jan 18 19:32:50 x-laptop kernel: [    0.000000] Extended CMOS year: 2000
Jan 18 19:32:50 x-laptop kernel: [    0.000000] Console: colour VGA+ 80x25
Jan 18 19:32:50 x-laptop kernel: [    0.000000] console [tty0] enabled
Jan 18 19:32:50 x-laptop kernel: [    0.000000] allocated 41943040 bytes of page_cgroup
Jan 18 19:32:50 x-laptop kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Jan 18 19:32:50 x-laptop kernel: [    0.000000] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
Jan 18 19:32:50 x-laptop kernel: [    0.000000] Fast TSC calibration using PIT
Jan 18 19:32:50 x-laptop kernel: [    0.000000] Detected 3457.926 MHz processor.
Jan 18 19:32:50 x-laptop kernel: [    0.010005] Calibrating delay loop (skipped), value calculated using timer frequency.. 6915.85 BogoMIPS (lpj=34579260)
Jan 18 19:32:50 x-laptop kernel: [    0.010028] Security Framework initialized
Jan 18 19:32:50 x-laptop kernel: [    0.010045] AppArmor: AppArmor initialized
Jan 18 19:32:50 x-laptop kernel: [    0.010286] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
Jan 18 19:32:50 x-laptop kernel: [    0.012308] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
Jan 18 19:32:50 x-laptop kernel: [    0.013262] Mount-cache hash table entries: 256
Jan 18 19:32:50 x-laptop kernel: [    0.013381] Initializing cgroup subsys ns
Jan 18 19:32:50 x-laptop kernel: [    0.013385] Initializing cgroup subsys cpuacct
Jan 18 19:32:50 x-laptop kernel: [    0.013387] Initializing cgroup subsys memory
Jan 18 19:32:50 x-laptop kernel: [    0.013394] Initializing cgroup subsys devices
Jan 18 19:32:50 x-laptop kernel: [    0.013396] Initializing cgroup subsys freezer
Jan 18 19:32:50 x-laptop kernel: [    0.013397] Initializing cgroup subsys net_cls
Jan 18 19:32:50 x-laptop kernel: [    0.013414] CPU: L1 I cache: 32K, L1 D cache: 32K
Jan 18 19:32:50 x-laptop kernel: [    0.013415] CPU: L2 cache: 6144K
Jan 18 19:32:50 x-laptop kernel: [    0.013418] CPU 0/0x0 -> Node 0
Jan 18 19:32:50 x-laptop kernel: [    0.013419] CPU: Physical Processor ID: 0
Jan 18 19:32:50 x-laptop kernel: [    0.013420] CPU: Processor Core ID: 0
Jan 18 19:32:50 x-laptop kernel: [    0.013422] mce: CPU supports 6 MCE banks
Jan 18 19:32:50 x-laptop kernel: [    0.013432] using mwait in idle threads.
Jan 18 19:32:50 x-laptop kernel: [    0.013433] Performance Events: Core2 events, Intel PMU driver.
Jan 18 19:32:50 x-laptop kernel: [    0.013438] ... version:                2
Jan 18 19:32:50 x-laptop kernel: [    0.013438] ... bit width:              40
Jan 18 19:32:50 x-laptop kernel: [    0.013439] ... generic registers:      2
Jan 18 19:32:50 x-laptop kernel: [    0.013440] ... value mask:             000000ffffffffff
Jan 18 19:32:50 x-laptop kernel: [    0.013441] ... max period:             000000007fffffff
Jan 18 19:32:50 x-laptop kernel: [    0.013442] ... fixed-purpose events:   3
Jan 18 19:32:50 x-laptop kernel: [    0.013443] ... event mask:             0000000700000003
Jan 18 19:32:50 x-laptop kernel: [    0.015227] ACPI: Core revision 20090903
Jan 18 19:32:50 x-laptop kernel: [    0.026336] ftrace: converting mcount calls to 0f 1f 44 00 00
Jan 18 19:32:50 x-laptop kernel: [    0.026342] ftrace: allocating 22535 entries in 89 pages
Jan 18 19:32:50 x-laptop kernel: [    0.030038] Setting APIC routing to flat
Jan 18 19:32:50 x-laptop kernel: [    0.030346] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Jan 18 19:32:50 x-laptop kernel: [    0.133137] CPU0: Intel(R) Core(TM)2 Extreme CPU X9100  @ 3.06GHz stepping 06
Jan 18 19:32:50 x-laptop kernel: [    0.140000] Booting processor 1 APIC 0x1 ip 0x6000
Jan 18 19:32:50 x-laptop kernel: [    0.020000] Initializing CPU#1
Jan 18 19:32:50 x-laptop kernel: [    0.020000] CPU: L1 I cache: 32K, L1 D cache: 32K
Jan 18 19:32:50 x-laptop kernel: [    0.020000] CPU: L2 cache: 6144K
Jan 18 19:32:50 x-laptop kernel: [    0.020000] CPU 1/0x1 -> Node 0
Jan 18 19:32:50 x-laptop kernel: [    0.020000] CPU: Physical Processor ID: 0
Jan 18 19:32:50 x-laptop kernel: [    0.020000] CPU: Processor Core ID: 1
Jan 18 19:32:50 x-laptop kernel: [    0.290045] CPU1: Intel(R) Core(TM)2 Extreme CPU X9100  @ 3.06GHz stepping 06
Jan 18 19:32:50 x-laptop kernel: [    0.290051] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
Jan 18 19:32:50 x-laptop kernel: [    0.300021] Brought up 2 CPUs
Jan 18 19:32:50 x-laptop kernel: [    0.300023] Total of 2 processors activated (13831.90 BogoMIPS).
Jan 18 19:32:50 x-laptop kernel: [    0.300759] devtmpfs: initialized
Jan 18 19:32:50 x-laptop kernel: [    0.300759] regulator: core version 0.5
Jan 18 19:32:50 x-laptop kernel: [    0.300759] Time: 19:32:47  Date: 01/18/11
Jan 18 19:32:50 x-laptop kernel: [    0.300759] NET: Registered protocol family 16
Jan 18 19:32:50 x-laptop kernel: [    0.300759] Trying to unpack rootfs image as initramfs...
Jan 18 19:32:50 x-laptop kernel: [    0.300759] ACPI: bus type pci registered
Jan 18 19:32:50 x-laptop kernel: [    0.300759] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
Jan 18 19:32:50 x-laptop kernel: [    0.300759] PCI: Not using MMCONFIG.
Jan 18 19:32:50 x-laptop kernel: [    0.300759] PCI: Using configuration type 1 for base access
Jan 18 19:32:50 x-laptop kernel: [    0.310145] bio: create slab <bio-0> at 0
Jan 18 19:32:50 x-laptop kernel: [    0.313496] ACPI: BIOS _OSI(Linux) query ignored
Jan 18 19:32:50 x-laptop kernel: [    0.315274] ACPI: Interpreter enabled
Jan 18 19:32:50 x-laptop kernel: [    0.315274] ACPI: (supports S0 S3 S4 S5)
Jan 18 19:32:50 x-laptop kernel: [    0.315274] ACPI: Using IOAPIC for interrupt routing
Jan 18 19:32:50 x-laptop kernel: [    0.315274] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
Jan 18 19:32:50 x-laptop kernel: [    0.315274] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
Jan 18 19:32:50 x-laptop kernel: [    0.324219] PCI: Using MMCONFIG at e0000000 - efffffff
Jan 18 19:32:50 x-laptop kernel: [    0.326937] ACPI: EC: GPE storm detected, transactions will use polling mode
Jan 18 19:32:50 x-laptop kernel: [    0.326937] ACPI: EC: GPE = 0x18, I/O: command/status = 0x66, data = 0x62
Jan 18 19:32:50 x-laptop kernel: [    0.330058] ACPI: No dock devices found.
Jan 18 19:32:50 x-laptop kernel: [    0.330442] ACPI: PCI Root Bridge [PCI0] (0000:00)
Jan 18 19:32:50 x-laptop kernel: [    0.330523] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
Jan 18 19:32:50 x-laptop kernel: [    0.330526] pci 0000:00:01.0: PME# disabled
Jan 18 19:32:50 x-laptop kernel: [    0.330885] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
Jan 18 19:32:50 x-laptop kernel: [    0.330889] pci 0000:00:1a.7: PME# disabled
Jan 18 19:32:50 x-laptop kernel: [    0.330960] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
Jan 18 19:32:50 x-laptop kernel: [    0.330963] pci 0000:00:1b.0: PME# disabled
Jan 18 19:32:50 x-laptop kernel: [    0.331019] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
Jan 18 19:32:50 x-laptop kernel: [    0.331021] pci 0000:00:1c.0: PME# disabled
Jan 18 19:32:50 x-laptop kernel: [    0.331077] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
Jan 18 19:32:50 x-laptop kernel: [    0.331080] pci 0000:00:1c.1: PME# disabled
Jan 18 19:32:50 x-laptop kernel: [    0.331137] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
Jan 18 19:32:50 x-laptop kernel: [    0.331140] pci 0000:00:1c.2: PME# disabled
Jan 18 19:32:50 x-laptop kernel: [    0.331197] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
Jan 18 19:32:50 x-laptop kernel: [    0.331199] pci 0000:00:1c.4: PME# disabled
Jan 18 19:32:50 x-laptop kernel: [    0.331255] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
Jan 18 19:32:50 x-laptop kernel: [    0.331258] pci 0000:00:1c.5: PME# disabled
Jan 18 19:32:50 x-laptop kernel: [    0.331568] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
Jan 18 19:32:50 x-laptop kernel: [    0.331572] pci 0000:00:1d.7: PME# disabled
Jan 18 19:32:50 x-laptop kernel: [    0.331783] pci 0000:00:1f.2: PME# supported from D3hot
Jan 18 19:32:50 x-laptop kernel: [    0.331785] pci 0000:00:1f.2: PME# disabled
Jan 18 19:32:50 x-laptop kernel: [    0.332094] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
Jan 18 19:32:50 x-laptop kernel: [    0.332098] pci 0000:02:00.0: PME# disabled
Jan 18 19:32:50 x-laptop kernel: [    0.333080] pci 0000:07:00.0: PME# supported from D0 D3hot D3cold
Jan 18 19:32:50 x-laptop kernel: [    0.333085] pci 0000:07:00.0: PME# disabled
Jan 18 19:32:50 x-laptop kernel: [    0.333186] pci 0000:00:1e.0: transparent bridge
Jan 18 19:32:50 x-laptop kernel: [    0.341451] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 *5 6 7 10 12 14 15)
Jan 18 19:32:50 x-laptop kernel: [    0.341519] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
Jan 18 19:32:50 x-laptop kernel: [    0.341584] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 *10 12 14 15)
Jan 18 19:32:50 x-laptop kernel: [    0.341649] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
Jan 18 19:32:50 x-laptop kernel: [    0.341715] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
Jan 18 19:32:50 x-laptop kernel: [    0.341780] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 *11 12 14 15)
Jan 18 19:32:50 x-laptop kernel: [    0.341846] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
Jan 18 19:32:50 x-laptop kernel: [    0.341911] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 *7 11 12 14 15)
Jan 18 19:32:50 x-laptop kernel: [    0.342006] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
Jan 18 19:32:50 x-laptop kernel: [    0.342010] vgaarb: loaded
Jan 18 19:32:50 x-laptop kernel: [    0.342089] SCSI subsystem initialized
Jan 18 19:32:50 x-laptop kernel: [    0.342223] usbcore: registered new interface driver usbfs
Jan 18 19:32:50 x-laptop kernel: [    0.342235] usbcore: registered new interface driver hub
Jan 18 19:32:50 x-laptop kernel: [    0.342279] usbcore: registered new device driver usb
Jan 18 19:32:50 x-laptop kernel: [    0.342356] ACPI: WMI: Mapper loaded
Jan 18 19:32:50 x-laptop kernel: [    0.342357] PCI: Using ACPI for IRQ routing
Jan 18 19:32:50 x-laptop kernel: [    0.342513] NetLabel: Initializing
Jan 18 19:32:50 x-laptop kernel: [    0.342514] NetLabel:  domain hash size = 128
Jan 18 19:32:50 x-laptop kernel: [    0.342515] NetLabel:  protocols = UNLABELED CIPSOv4
Jan 18 19:32:50 x-laptop kernel: [    0.342525] NetLabel:  unlabeled traffic allowed by default
Jan 18 19:32:50 x-laptop kernel: [    0.342546] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
Jan 18 19:32:50 x-laptop kernel: [    0.342549] hpet0: 4 comparators, 64-bit 14.318180 MHz counter
Jan 18 19:32:50 x-laptop kernel: [    0.350020] Switching to clocksource tsc
Jan 18 19:32:50 x-laptop kernel: [    0.351254] AppArmor: AppArmor Filesystem Enabled
Jan 18 19:32:50 x-laptop kernel: [    0.351264] pnp: PnP ACPI init
Jan 18 19:32:50 x-laptop kernel: [    0.351276] ACPI: bus type pnp registered
Jan 18 19:32:50 x-laptop kernel: [    0.389932] pnp: PnP ACPI: found 11 devices
Jan 18 19:32:50 x-laptop kernel: [    0.389935] ACPI: ACPI bus type pnp unregistered
Jan 18 19:32:50 x-laptop kernel: [    0.389963] system 00:03: iomem range 0xfed00000-0xfed003ff has been reserved
Jan 18 19:32:50 x-laptop kernel: [    0.389971] system 00:05: ioport range 0x680-0x69f has been reserved
Jan 18 19:32:50 x-laptop kernel: [    0.389972] system 00:05: ioport range 0x480-0x48f has been reserved
Jan 18 19:32:50 x-laptop kernel: [    0.389974] system 00:05: ioport range 0x900-0x903 has been reserved
Jan 18 19:32:50 x-laptop kernel: [    0.389977] system 00:05: ioport range 0xffff-0xffff has been reserved
Jan 18 19:32:50 x-laptop kernel: [    0.389979] system 00:05: ioport range 0x1000-0x107f has been reserved
Jan 18 19:32:50 x-laptop kernel: [    0.389980] system 00:05: ioport range 0x1180-0x11ff has been reserved
Jan 18 19:32:50 x-laptop kernel: [    0.389982] system 00:05: ioport range 0x164e-0x164f has been reserved
Jan 18 19:32:50 x-laptop kernel: [    0.389983] system 00:05: ioport range 0xfe00-0xfe00 has been reserved
Jan 18 19:32:50 x-laptop kernel: [    0.389989] system 00:0a: ioport range 0x400-0x47f has been reserved
Jan 18 19:32:50 x-laptop kernel: [    0.389991] system 00:0a: iomem range 0xfed1c000-0xfed1ffff has been reserved
Jan 18 19:32:50 x-laptop kernel: [    0.389993] system 00:0a: iomem range 0xfed10000-0xfed13fff has been reserved
Jan 18 19:32:50 x-laptop kernel: [    0.389995] system 00:0a: iomem range 0xfed18000-0xfed18fff has been reserved
Jan 18 19:32:50 x-laptop kernel: [    0.389996] system 00:0a: iomem range 0xfed19000-0xfed19fff has been reserved
Jan 18 19:32:50 x-laptop kernel: [    0.389998] system 00:0a: iomem range 0xe0000000-0xefffffff has been reserved
Jan 18 19:32:50 x-laptop kernel: [    0.389999] system 00:0a: iomem range 0xfed20000-0xfed3ffff has been reserved
Jan 18 19:32:50 x-laptop kernel: [    0.390001] system 00:0a: iomem range 0xfed45000-0xfed8ffff has been reserved
Jan 18 19:32:50 x-laptop kernel: [    0.394734] pci 0000:01:00.0: BAR 6: can't allocate mem resource [0xe0000000-0xdfffffff]
Jan 18 19:32:50 x-laptop kernel: [    0.394737] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
Jan 18 19:32:50 x-laptop kernel: [    0.394738] pci 0000:00:01.0:   IO window: 0x2000-0x2fff
Jan 18 19:32:50 x-laptop kernel: [    0.394741] pci 0000:00:01.0:   MEM window: 0xf0000000-0xf2ffffff
Jan 18 19:32:50 x-laptop kernel: [    0.394743] pci 0000:00:01.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
Jan 18 19:32:50 x-laptop kernel: [    0.394748] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
Jan 18 19:32:50 x-laptop kernel: [    0.394750] pci 0000:00:1c.0:   IO window: 0x3000-0x3fff
Jan 18 19:32:50 x-laptop kernel: [    0.394753] pci 0000:00:1c.0:   MEM window: 0xf3100000-0xf31fffff
Jan 18 19:32:50 x-laptop kernel: [    0.394756] pci 0000:00:1c.0:   PREFETCH window: 0x000000f8000000-0x000000f80fffff
Jan 18 19:32:50 x-laptop kernel: [    0.394761] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:03
Jan 18 19:32:50 x-laptop kernel: [    0.394763] pci 0000:00:1c.1:   IO window: 0x4000-0x4fff
Jan 18 19:32:50 x-laptop kernel: [    0.394767] pci 0000:00:1c.1:   MEM window: 0xf3300000-0xf33fffff
Jan 18 19:32:50 x-laptop kernel: [    0.394770] pci 0000:00:1c.1:   PREFETCH window: 0xc0000000-0xc01fffff
Jan 18 19:32:50 x-laptop kernel: [    0.394775] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:04
Jan 18 19:32:50 x-laptop kernel: [    0.394777] pci 0000:00:1c.2:   IO window: 0x6000-0x6fff
Jan 18 19:32:50 x-laptop kernel: [    0.394780] pci 0000:00:1c.2:   MEM window: 0xf3200000-0xf32fffff
Jan 18 19:32:50 x-laptop kernel: [    0.394783] pci 0000:00:1c.2:   PREFETCH window: 0x000000c0200000-0x000000c03fffff
Jan 18 19:32:50 x-laptop kernel: [    0.394788] pci 0000:00:1c.4: PCI bridge, secondary bus 0000:05
Jan 18 19:32:50 x-laptop kernel: [    0.394790] pci 0000:00:1c.4:   IO window: 0x5000-0x5fff
Jan 18 19:32:50 x-laptop kernel: [    0.394793] pci 0000:00:1c.4:   MEM window: 0xf4000000-0xf5ffffff
Jan 18 19:32:50 x-laptop kernel: [    0.394796] pci 0000:00:1c.4:   PREFETCH window: 0x000000f6000000-0x000000f7ffffff
Jan 18 19:32:50 x-laptop kernel: [    0.394801] pci 0000:00:1c.5: PCI bridge, secondary bus 0000:07
Jan 18 19:32:50 x-laptop kernel: [    0.394803] pci 0000:00:1c.5:   IO window: 0x7000-0x7fff
Jan 18 19:32:50 x-laptop kernel: [    0.394807] pci 0000:00:1c.5:   MEM window: 0xf3000000-0xf30fffff
Jan 18 19:32:50 x-laptop kernel: [    0.394809] pci 0000:00:1c.5:   PREFETCH window: 0x000000c0400000-0x000000c05fffff
Jan 18 19:32:50 x-laptop kernel: [    0.394814] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:08
Jan 18 19:32:50 x-laptop kernel: [    0.394815] pci 0000:00:1e.0:   IO window: disabled
Jan 18 19:32:50 x-laptop kernel: [    0.394819] pci 0000:00:1e.0:   MEM window: disabled
Jan 18 19:32:50 x-laptop kernel: [    0.394821] pci 0000:00:1e.0:   PREFETCH window: disabled
Jan 18 19:32:50 x-laptop kernel: [    0.394841] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jan 18 19:32:50 x-laptop kernel: [    0.394854] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Jan 18 19:32:50 x-laptop kernel: [    0.394865] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
Jan 18 19:32:50 x-laptop kernel: [    0.394877] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Jan 18 19:32:50 x-laptop kernel: [    0.394887] pci 0000:00:1c.4: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Jan 18 19:32:50 x-laptop kernel: [    0.394896] pci 0000:00:1c.5: PCI INT B -> GSI 16 (level, low) -> IRQ 16
Jan 18 19:32:50 x-laptop kernel: [    0.394963] NET: Registered protocol family 2
Jan 18 19:32:50 x-laptop kernel: [    0.395078] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
Jan 18 19:32:50 x-laptop kernel: [    0.395990] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
Jan 18 19:32:50 x-laptop kernel: [    0.399912] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
Jan 18 19:32:50 x-laptop kernel: [    0.400447] TCP: Hash tables configured (established 524288 bind 65536)
Jan 18 19:32:50 x-laptop kernel: [    0.400449] TCP reno registered
Jan 18 19:32:50 x-laptop kernel: [    0.400538] NET: Registered protocol family 1
Jan 18 19:32:50 x-laptop kernel: [    0.400864] Scanning for low memory corruption every 60 seconds
Jan 18 19:32:50 x-laptop kernel: [    0.400972] audit: initializing netlink socket (disabled)
Jan 18 19:32:50 x-laptop kernel: [    0.400983] type=2000 audit(1295379166.399:1): initialized
Jan 18 19:32:50 x-laptop kernel: [    0.406938] HugeTLB registered 2 MB page size, pre-allocated 0 pages
Jan 18 19:32:50 x-laptop kernel: [    0.407802] VFS: Disk quotas dquot_6.5.2
Jan 18 19:32:50 x-laptop kernel: [    0.407836] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
Jan 18 19:32:50 x-laptop kernel: [    0.408215] fuse init (API version 7.13)
Jan 18 19:32:50 x-laptop kernel: [    0.408269] msgmni has been set to 7903
Jan 18 19:32:50 x-laptop kernel: [    0.408406] alg: No test for stdrng (krng)
Jan 18 19:32:50 x-laptop kernel: [    0.408442] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
Jan 18 19:32:50 x-laptop kernel: [    0.408444] io scheduler noop registered
Jan 18 19:32:50 x-laptop kernel: [    0.408445] io scheduler anticipatory registered
Jan 18 19:32:50 x-laptop kernel: [    0.408446] io scheduler deadline registered
Jan 18 19:32:50 x-laptop kernel: [    0.408467] io scheduler cfq registered (default)
Jan 18 19:32:50 x-laptop kernel: [    0.409129] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jan 18 19:32:50 x-laptop kernel: [    0.409255] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Jan 18 19:32:50 x-laptop kernel: [    0.417693] Freeing initrd memory: 8142k freed
Jan 18 19:32:50 x-laptop kernel: [    0.440001] ACPI: AC Adapter [ADP0] (on-line)
Jan 18 19:32:50 x-laptop kernel: [    0.440077] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
Jan 18 19:32:50 x-laptop kernel: [    0.479890] ACPI: Lid Switch [LID0]
Jan 18 19:32:50 x-laptop kernel: [    0.479919] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1
Jan 18 19:32:50 x-laptop kernel: [    0.479923] ACPI: Power Button [PWRB]
Jan 18 19:32:50 x-laptop kernel: [    0.479948] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input2
Jan 18 19:32:50 x-laptop kernel: [    0.479951] ACPI: Sleep Button [SLPB]
Jan 18 19:32:50 x-laptop kernel: [    0.479981] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
Jan 18 19:32:50 x-laptop kernel: [    0.479983] ACPI: Power Button [PWRF]
Jan 18 19:32:50 x-laptop kernel: [    0.480584] ACPI: SSDT 00000000bfd1ac20 002A7 (v01  PmRef  Cpu0Ist 00003000 INTL 20050624)
Jan 18 19:32:50 x-laptop kernel: [    0.482078] processor LNXCPU:00: registered as cooling_device0
Jan 18 19:32:50 x-laptop kernel: [    0.483175] ACPI: SSDT 00000000bfd19ca0 001CF (v01  PmRef    ApIst 00003000 INTL 20050624)
Jan 18 19:32:50 x-laptop kernel: [    0.484829] processor LNXCPU:01: registered as cooling_device1
Jan 18 19:32:50 x-laptop kernel: [    1.400023] thermal LNXTHERM:01: registered as thermal_zone0
Jan 18 19:32:50 x-laptop kernel: [    1.400028] ACPI: Thermal Zone [THM0] (25 C)
Jan 18 19:32:50 x-laptop kernel: [    1.440089] Linux agpgart interface v0.103
Jan 18 19:32:50 x-laptop kernel: [    1.440114] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
Jan 18 19:32:50 x-laptop kernel: [    1.440908] brd: module loaded
Jan 18 19:32:50 x-laptop kernel: [    1.441204] loop: module loaded
Jan 18 19:32:50 x-laptop kernel: [    1.441252] input: Macintosh mouse button emulation as /devices/virtual/input/input4
Jan 18 19:32:50 x-laptop kernel: [    1.441501] Fixed MDIO Bus: probed
Jan 18 19:32:50 x-laptop kernel: [    1.441521] PPP generic driver version 2.4.2
Jan 18 19:32:50 x-laptop kernel: [    1.441539] tun: Universal TUN/TAP device driver, 1.6
Jan 18 19:32:50 x-laptop kernel: [    1.441540] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Jan 18 19:32:50 x-laptop kernel: [    1.441593] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Jan 18 19:32:50 x-laptop kernel: [    1.441618] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 19 (level, low) -> IRQ 19
Jan 18 19:32:50 x-laptop kernel: [    1.441631] ehci_hcd 0000:00:1a.7: EHCI Host Controller
Jan 18 19:32:50 x-laptop kernel: [    1.441655] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
Jan 18 19:32:50 x-laptop kernel: [    1.441682] ehci_hcd 0000:00:1a.7: debug port 1
Jan 18 19:32:50 x-laptop kernel: [    1.445582] ehci_hcd 0000:00:1a.7: irq 19, io mem 0xf3604800
Jan 18 19:32:50 x-laptop kernel: [    1.462505] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
Jan 18 19:32:50 x-laptop kernel: [    1.462554] usb usb1: configuration #1 chosen from 1 choice
Jan 18 19:32:50 x-laptop kernel: [    1.462574] hub 1-0:1.0: USB hub found
Jan 18 19:32:50 x-laptop kernel: [    1.462579] hub 1-0:1.0: 6 ports detected
Jan 18 19:32:50 x-laptop kernel: [    1.462621] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Jan 18 19:32:50 x-laptop kernel: [    1.462630] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Jan 18 19:32:50 x-laptop kernel: [    1.462651] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
Jan 18 19:32:50 x-laptop kernel: [    1.462673] ehci_hcd 0000:00:1d.7: debug port 1
Jan 18 19:32:50 x-laptop kernel: [    1.466576] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xf3604c00
Jan 18 19:32:50 x-laptop kernel: [    1.482505] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
Jan 18 19:32:50 x-laptop kernel: [    1.482541] usb usb2: configuration #1 chosen from 1 choice
Jan 18 19:32:50 x-laptop kernel: [    1.482558] hub 2-0:1.0: USB hub found
Jan 18 19:32:50 x-laptop kernel: [    1.482562] hub 2-0:1.0: 6 ports detected
Jan 18 19:32:50 x-laptop kernel: [    1.482597] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Jan 18 19:32:50 x-laptop kernel: [    1.482606] uhci_hcd: USB Universal Host Controller Interface driver
Jan 18 19:32:50 x-laptop kernel: [    1.482617] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jan 18 19:32:50 x-laptop kernel: [    1.482623] uhci_hcd 0000:00:1a.0: UHCI Host Controller
Jan 18 19:32:50 x-laptop kernel: [    1.482647] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
Jan 18 19:32:50 x-laptop kernel: [    1.482672] uhci_hcd 0000:00:1a.0: irq 16, io base 0x00001800
Jan 18 19:32:50 x-laptop kernel: [    1.482728] usb usb3: configuration #1 chosen from 1 choice
Jan 18 19:32:50 x-laptop kernel: [    1.482744] hub 3-0:1.0: USB hub found
Jan 18 19:32:50 x-laptop kernel: [    1.482748] hub 3-0:1.0: 2 ports detected
Jan 18 19:32:50 x-laptop kernel: [    1.482778] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
Jan 18 19:32:50 x-laptop kernel: [    1.482784] uhci_hcd 0000:00:1a.1: UHCI Host Controller
Jan 18 19:32:50 x-laptop kernel: [    1.482803] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
Jan 18 19:32:50 x-laptop kernel: [    1.482829] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00001820
Jan 18 19:32:50 x-laptop kernel: [    1.482881] usb usb4: configuration #1 chosen from 1 choice
Jan 18 19:32:50 x-laptop kernel: [    1.482898] hub 4-0:1.0: USB hub found
Jan 18 19:32:50 x-laptop kernel: [    1.482902] hub 4-0:1.0: 2 ports detected
Jan 18 19:32:50 x-laptop kernel: [    1.482929] uhci_hcd 0000:00:1a.2: PCI INT C -> GSI 19 (level, low) -> IRQ 19
Jan 18 19:32:50 x-laptop kernel: [    1.482935] uhci_hcd 0000:00:1a.2: UHCI Host Controller
Jan 18 19:32:50 x-laptop kernel: [    1.482954] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
Jan 18 19:32:50 x-laptop kernel: [    1.482976] uhci_hcd 0000:00:1a.2: irq 19, io base 0x00001840
Jan 18 19:32:50 x-laptop kernel: [    1.483032] usb usb5: configuration #1 chosen from 1 choice
Jan 18 19:32:50 x-laptop kernel: [    1.483047] hub 5-0:1.0: USB hub found
Jan 18 19:32:50 x-laptop kernel: [    1.483051] hub 5-0:1.0: 2 ports detected
Jan 18 19:32:50 x-laptop kernel: [    1.483081] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Jan 18 19:32:50 x-laptop kernel: [    1.483088] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Jan 18 19:32:50 x-laptop kernel: [    1.483106] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
Jan 18 19:32:50 x-laptop kernel: [    1.483125] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001860
Jan 18 19:32:50 x-laptop kernel: [    1.483186] usb usb6: configuration #1 chosen from 1 choice
Jan 18 19:32:50 x-laptop kernel: [    1.483200] hub 6-0:1.0: USB hub found
Jan 18 19:32:50 x-laptop kernel: [    1.483204] hub 6-0:1.0: 2 ports detected
Jan 18 19:32:50 x-laptop kernel: [    1.483234] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Jan 18 19:32:50 x-laptop kernel: [    1.483240] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Jan 18 19:32:50 x-laptop kernel: [    1.483262] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
Jan 18 19:32:50 x-laptop kernel: [    1.483281] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001880
Jan 18 19:32:50 x-laptop kernel: [    1.483335] usb usb7: configuration #1 chosen from 1 choice
Jan 18 19:32:50 x-laptop kernel: [    1.483349] hub 7-0:1.0: USB hub found
Jan 18 19:32:50 x-laptop kernel: [    1.483353] hub 7-0:1.0: 2 ports detected
Jan 18 19:32:50 x-laptop kernel: [    1.483382] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Jan 18 19:32:50 x-laptop kernel: [    1.483388] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Jan 18 19:32:50 x-laptop kernel: [    1.483404] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
Jan 18 19:32:50 x-laptop kernel: [    1.483429] uhci_hcd 0000:00:1d.2: irq 18, io base 0x000018a0
Jan 18 19:32:50 x-laptop kernel: [    1.483482] usb usb8: configuration #1 chosen from 1 choice
Jan 18 19:32:50 x-laptop kernel: [    1.483495] hub 8-0:1.0: USB hub found
Jan 18 19:32:50 x-laptop kernel: [    1.483501] hub 8-0:1.0: 2 ports detected
Jan 18 19:32:50 x-laptop kernel: [    1.483555] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Jan 18 19:32:50 x-laptop kernel: [    1.487420] i8042.c: Detected active multiplexing controller, rev 1.1.
Jan 18 19:32:50 x-laptop kernel: [    1.490077] serio: i8042 KBD port at 0x60,0x64 irq 1
Jan 18 19:32:50 x-laptop kernel: [    1.490081] serio: i8042 AUX0 port at 0x60,0x64 irq 12
Jan 18 19:32:50 x-laptop kernel: [    1.490083] serio: i8042 AUX1 port at 0x60,0x64 irq 12
Jan 18 19:32:50 x-laptop kernel: [    1.490084] serio: i8042 AUX2 port at 0x60,0x64 irq 12
Jan 18 19:32:50 x-laptop kernel: [    1.490086] serio: i8042 AUX3 port at 0x60,0x64 irq 12
Jan 18 19:32:50 x-laptop kernel: [    1.490138] mice: PS/2 mouse device common for all mice
Jan 18 19:32:50 x-laptop kernel: [    1.490244] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
Jan 18 19:32:50 x-laptop kernel: [    1.490264] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
Jan 18 19:32:50 x-laptop kernel: [    1.490334] device-mapper: uevent: version 1.0.3
Jan 18 19:32:50 x-laptop kernel: [    1.490405] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
Jan 18 19:32:50 x-laptop kernel: [    1.490450] device-mapper: multipath: version 1.1.0 loaded
Jan 18 19:32:50 x-laptop kernel: [    1.490452] device-mapper: multipath round-robin: version 1.0.0 loaded
Jan 18 19:32:50 x-laptop kernel: [    1.490550] cpuidle: using governor ladder
Jan 18 19:32:50 x-laptop kernel: [    1.490551] cpuidle: using governor menu
Jan 18 19:32:50 x-laptop kernel: [    1.490753] TCP cubic registered
Jan 18 19:32:50 x-laptop kernel: [    1.490840] NET: Registered protocol family 10
Jan 18 19:32:50 x-laptop kernel: [    1.491107] lo: Disabled Privacy Extensions
Jan 18 19:32:50 x-laptop kernel: [    1.491271] NET: Registered protocol family 17
Jan 18 19:32:50 x-laptop kernel: [    1.492835] registered taskstats version 1
Jan 18 19:32:50 x-laptop kernel: [    1.493304]   Magic number: 11:813:546
Jan 18 19:32:50 x-laptop kernel: [    1.493324] mem null: hash matches
Jan 18 19:32:50 x-laptop kernel: [    1.493362] rtc_cmos 00:07: setting system clock to 2011-01-18 19:32:48 UTC (1295379168)
Jan 18 19:32:50 x-laptop kernel: [    1.493364] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Jan 18 19:32:50 x-laptop kernel: [    1.493364] EDD information not available.
Jan 18 19:32:50 x-laptop kernel: [    1.493408] Freeing unused kernel memory: 876k freed
Jan 18 19:32:50 x-laptop kernel: [    1.493688] Write protecting the kernel read-only data: 7696k
Jan 18 19:32:50 x-laptop kernel: [    1.502090] udev: starting version 151
Jan 18 19:32:50 x-laptop kernel: [    1.530183] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
Jan 18 19:32:50 x-laptop kernel: [    1.537660] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Jan 18 19:32:50 x-laptop kernel: [    1.537744] ahci: SSS flag set, parallel bus scan disabled
Jan 18 19:32:50 x-laptop kernel: [    1.537767] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 4 ports 3 Gbps 0x33 impl SATA mode
Jan 18 19:32:50 x-laptop kernel: [    1.537769] ahci 0000:00:1f.2: flags: 64bit ncq sntf stag led clo pio slum part ccc ems sxs 
Jan 18 19:32:50 x-laptop kernel: [    1.543931] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
Jan 18 19:32:50 x-laptop kernel: [    1.543957] r8169 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jan 18 19:32:50 x-laptop kernel: [    1.544434] eth0: RTL8168c/8111c at 0xffffc9000065a000, 00:90:f5:87:e5:af, XID 1c4000c0 IRQ 31
Jan 18 19:32:50 x-laptop kernel: [    1.571538] ohci1394 0000:04:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Jan 18 19:32:50 x-laptop kernel: [    1.600035] scsi0 : ahci
Jan 18 19:32:50 x-laptop kernel: [    1.600113] scsi1 : ahci
Jan 18 19:32:50 x-laptop kernel: [    1.600149] scsi2 : ahci
Jan 18 19:32:50 x-laptop kernel: [    1.600184] scsi3 : ahci
Jan 18 19:32:50 x-laptop kernel: [    1.600220] scsi4 : ahci
Jan 18 19:32:50 x-laptop kernel: [    1.600257] scsi5 : ahci
Jan 18 19:32:50 x-laptop kernel: [    1.600288] ata1: SATA max UDMA/133 abar m2048@0xf3604000 port 0xf3604100 irq 30
Jan 18 19:32:50 x-laptop kernel: [    1.600290] ata2: SATA max UDMA/133 abar m2048@0xf3604000 port 0xf3604180 irq 30
Jan 18 19:32:50 x-laptop kernel: [    1.600291] ata3: DUMMY
Jan 18 19:32:50 x-laptop kernel: [    1.600292] ata4: DUMMY
Jan 18 19:32:50 x-laptop kernel: [    1.600293] ata5: SATA max UDMA/133 abar m2048@0xf3604000 port 0xf3604300 irq 30
Jan 18 19:32:50 x-laptop kernel: [    1.600295] ata6: SATA max UDMA/133 abar m2048@0xf3604000 port 0xf3604380 irq 30
Jan 18 19:32:50 x-laptop kernel: [    1.633538] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[18]  MMIO=[f3200000-f32007ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
Jan 18 19:32:50 x-laptop kernel: [    1.942511] ata1: SATA link down (SStatus 0 SControl 300)
Jan 18 19:32:50 x-laptop kernel: [    2.120048] ACPI: Battery Slot [BAT0] (battery present)
Jan 18 19:32:50 x-laptop kernel: [    2.250004] usb 3-1: new low speed USB device using uhci_hcd and address 2
Jan 18 19:32:50 x-laptop kernel: [    2.280012] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Jan 18 19:32:50 x-laptop kernel: [    2.320613] ata2.00: ATA-8: OCZ-AGILITY2, 1.25, max UDMA/133
Jan 18 19:32:50 x-laptop kernel: [    2.320615] ata2.00: 234441648 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
Jan 18 19:32:50 x-laptop kernel: [    2.350621] ata2.00: configured for UDMA/133
Jan 18 19:32:50 x-laptop kernel: [    2.350688] scsi 1:0:0:0: Direct-Access     ATA      OCZ-AGILITY2     1.25 PQ: 0 ANSI: 5
Jan 18 19:32:50 x-laptop kernel: [    2.350784] sd 1:0:0:0: Attached scsi generic sg0 type 0
Jan 18 19:32:50 x-laptop kernel: [    2.350836] sd 1:0:0:0: [sda] 234441648 512-byte logical blocks: (120 GB/111 GiB)
Jan 18 19:32:50 x-laptop kernel: [    2.350871] sd 1:0:0:0: [sda] Write Protect is off
Jan 18 19:32:50 x-laptop kernel: [    2.350890] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jan 18 19:32:50 x-laptop kernel: [    2.350985]  sda: sda1 sda2 < sda5 sda6 >
Jan 18 19:32:50 x-laptop kernel: [    2.351543] sd 1:0:0:0: [sda] Attached SCSI disk
Jan 18 19:32:50 x-laptop kernel: [    2.509766] usb 3-1: configuration #1 chosen from 1 choice
Jan 18 19:32:50 x-laptop kernel: [    2.520875] usbcore: registered new interface driver hiddev
Jan 18 19:32:50 x-laptop kernel: [    2.564871] input:   USB Keyboard as /devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1:1.0/input/input6
Jan 18 19:32:50 x-laptop kernel: [    2.564913] generic-usb 0003:04D9:1702.0001: input,hidraw0: USB HID v1.10 Keyboard [  USB Keyboard] on usb-0000:00:1a.0-1/input0
Jan 18 19:32:50 x-laptop kernel: [    2.653767] input:   USB Keyboard as /devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1:1.1/input/input7
Jan 18 19:32:50 x-laptop kernel: [    2.653801] generic-usb 0003:04D9:1702.0002: input,hidraw1: USB HID v1.10 Device [  USB Keyboard] on usb-0000:00:1a.0-1/input1
Jan 18 19:32:50 x-laptop kernel: [    2.653812] usbcore: registered new interface driver usbhid
Jan 18 19:32:50 x-laptop kernel: [    2.653813] usbhid: v2.6:USB HID core driver
Jan 18 19:32:50 x-laptop kernel: [    2.700011] ata5: SATA link down (SStatus 0 SControl 300)
Jan 18 19:32:50 x-laptop kernel: [    2.800006] usb 4-2: new full speed USB device using uhci_hcd and address 2
Jan 18 19:32:50 x-laptop kernel: [    2.982920] usb 4-2: configuration #1 chosen from 1 choice
Jan 18 19:32:50 x-laptop kernel: [    2.991029] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1a.1/usb4/4-2/4-2:1.0/input/input8
Jan 18 19:32:50 x-laptop kernel: [    2.991077] generic-usb 0003:046D:C526.0003: input,hidraw2: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:1a.1-2/input0
Jan 18 19:32:50 x-laptop kernel: [    2.995935] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1a.1/usb4/4-2/4-2:1.1/input/input9
Jan 18 19:32:50 x-laptop kernel: [    2.995992] generic-usb 0003:046D:C526.0004: input,hiddev96,hidraw3: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1a.1-2/input1
Jan 18 19:32:50 x-laptop kernel: [    3.052510] ata6: SATA link down (SStatus 0 SControl 300)
Jan 18 19:32:50 x-laptop kernel: [    3.095302] EXT4-fs (sda5): INFO: recovery required on readonly filesystem
Jan 18 19:32:50 x-laptop kernel: [    3.095305] EXT4-fs (sda5): write access will be enabled during recovery
Jan 18 19:32:50 x-laptop kernel: [    3.272517] usb 5-1: new full speed USB device using uhci_hcd and address 2
Jan 18 19:32:50 x-laptop kernel: [    3.284682] EXT4-fs (sda5): orphan cleanup on readonly fs
Jan 18 19:32:50 x-laptop kernel: [    3.285845] EXT4-fs (sda5): 9 orphan inodes deleted
Jan 18 19:32:50 x-laptop kernel: [    3.285847] EXT4-fs (sda5): recovery complete
Jan 18 19:32:50 x-laptop kernel: [    3.294602] EXT4-fs (sda5): mounted filesystem with ordered data mode
Jan 18 19:32:50 x-laptop kernel: [    3.452114] usb 5-1: configuration #1 chosen from 1 choice
Jan 18 19:32:50 x-laptop kernel: [    3.465110] Adding 2847736k swap on /dev/sda6.  Priority:-1 extents:1 across:2847736k SS
Jan 18 19:32:50 x-laptop kernel: [    3.498541] udev: starting version 151
Jan 18 19:32:50 x-laptop kernel: [    3.654424] lp: driver loaded but no devices found
Jan 18 19:32:50 x-laptop kernel: [    3.677945] [Firmware Bug]: ACPI(VGA) defines _DOD but not _DOS
Jan 18 19:32:50 x-laptop kernel: [    3.685534] lirc_dev: IR Remote Control driver registered, major 61 
Jan 18 19:32:50 x-laptop kernel: [    3.685944] lirc_dev: lirc_register_driver: sample_rate: 0
Jan 18 19:32:50 x-laptop kernel: [    3.687749] lirc_ite8709: device found : irq=6 io=0x260
Jan 18 19:32:50 x-laptop kernel: [    3.762957] type=1505 audit(1295397170.769:2):  operation="profile_load" pid=524 name="/sbin/dhclient3"
Jan 18 19:32:50 x-laptop kernel: [    3.763487] type=1505 audit(1295397170.769:3):  operation="profile_load" pid=524 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Jan 18 19:32:50 x-laptop kernel: [    3.763715] type=1505 audit(1295397170.769:4):  operation="profile_load" pid=524 name="/usr/lib/connman/scripts/dhclient-script"
Jan 18 19:32:50 x-laptop kernel: [    3.803927] r8169: eth0: link down
Jan 18 19:32:50 x-laptop kernel: [    3.804266] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jan 18 19:32:50 x-laptop kernel: [    3.892695] acpi device:01: registered as cooling_device2
Jan 18 19:32:50 x-laptop kernel: [    3.892837] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:00/LNXVIDEO:00/input/input10
Jan 18 19:32:50 x-laptop kernel: [    3.892876] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
Jan 18 19:32:50 x-laptop kernel: [    3.916839] vga16fb: mapped to 0xffff8800000a0000
Jan 18 19:32:50 x-laptop kernel: [    3.916900] fb0: VGA16 VGA frame buffer device
Jan 18 19:32:51 x-laptop kernel: [    4.016493] nvidia: module license 'NVIDIA' taints kernel.
Jan 18 19:32:51 x-laptop kernel: [    4.016495] Disabling lock debugging due to kernel taint
Jan 18 19:32:51 x-laptop kernel: [    4.084867] type=1505 audit(1295397171.089:5):  operation="profile_replace" pid=805 name="/sbin/dhclient3"
Jan 18 19:32:51 x-laptop kernel: [    4.085388] type=1505 audit(1295397171.089:6):  operation="profile_replace" pid=805 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Jan 18 19:32:51 x-laptop kernel: [    4.086533] type=1505 audit(1295397171.089:7):  operation="profile_load" pid=804 name="/usr/share/gdm/guest-session/Xsession"
Jan 18 19:32:51 x-laptop kernel: [    4.087055] type=1505 audit(1295397171.089:8):  operation="profile_replace" pid=805 name="/usr/lib/connman/scripts/dhclient-script"
Jan 18 19:32:51 x-laptop kernel: [    4.096040] type=1505 audit(1295397171.099:9):  operation="profile_load" pid=807 name="/usr/bin/evince"
Jan 18 19:32:51 x-laptop kernel: [    4.097303] type=1505 audit(1295397171.099:10):  operation="profile_load" pid=810 name="/usr/lib/cups/backend/cups-pdf"
Jan 18 19:32:51 x-laptop kernel: [    4.304534] sdhci: Secure Digital Host Controller Interface driver
Jan 18 19:32:51 x-laptop kernel: [    4.304536] sdhci: Copyright(c) Pierre Ossman
Jan 18 19:32:51 x-laptop kernel: [    4.306401] sdhci-pci 0000:04:00.1: SDHCI controller found [197b:2382] (rev 0)
Jan 18 19:32:51 x-laptop kernel: [    4.306419] sdhci-pci 0000:04:00.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Jan 18 19:32:51 x-laptop kernel: [    4.306552] Registered led device: mmc0::
Jan 18 19:32:51 x-laptop kernel: [    4.314942] mmc0: SDHCI controller on PCI [0000:04:00.1] using DMA
Jan 18 19:32:51 x-laptop kernel: [    4.314953] sdhci-pci 0000:04:00.2: SDHCI controller found [197b:2381] (rev 0)
Jan 18 19:32:51 x-laptop kernel: [    4.314967] sdhci-pci 0000:04:00.2: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Jan 18 19:32:51 x-laptop kernel: [    4.314972] sdhci-pci 0000:04:00.2: Refusing to bind to secondary interface.
Jan 18 19:32:51 x-laptop kernel: [    4.314977] sdhci-pci 0000:04:00.2: PCI INT A disabled
Jan 18 19:32:51 x-laptop kernel: [    4.488880] cfg80211: Calling CRDA to update world regulatory domain
Jan 18 19:32:51 x-laptop kernel: [    4.514827] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
Jan 18 19:32:51 x-laptop kernel: [    4.514828] iwlagn: Copyright(c) 2003-2009 Intel Corporation
Jan 18 19:32:51 x-laptop kernel: [    4.514882] iwlagn 0000:07:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Jan 18 19:32:51 x-laptop kernel: [    4.514922] iwlagn 0000:07:00.0: Detected Intel Wireless WiFi Link 5300AGN REV=0x24
Jan 18 19:32:51 x-laptop kernel: [    4.554089] jmb38x_ms 0000:04:00.3: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Jan 18 19:32:51 x-laptop kernel: [    4.554623] iwlagn 0000:07:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
Jan 18 19:32:51 x-laptop kernel: [    4.562854] cfg80211: World regulatory domain updated:
Jan 18 19:32:51 x-laptop kernel: [    4.562855]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Jan 18 19:32:51 x-laptop kernel: [    4.562857]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jan 18 19:32:51 x-laptop kernel: [    4.562858]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jan 18 19:32:51 x-laptop kernel: [    4.562859]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jan 18 19:32:51 x-laptop kernel: [    4.562861]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jan 18 19:32:51 x-laptop kernel: [    4.562862]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jan 18 19:32:51 x-laptop kernel: [    4.607988] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Jan 18 19:32:51 x-laptop kernel: [    4.608418] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jan 18 19:32:51 x-laptop kernel: [    4.608426] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
Jan 18 19:32:51 x-laptop kernel: [    4.608608] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  260.19.29  Wed Dec  8 12:08:56 PST 2010
Jan 18 19:32:51 x-laptop kernel: [    4.627022] Console: switching to colour frame buffer device 80x30
Jan 18 19:32:51 x-laptop kernel: [    4.631297] iwlagn 0000:07:00.0: firmware: requesting iwlwifi-5000-2.ucode
Jan 18 19:32:51 x-laptop kernel: [    4.635532] iwlagn 0000:07:00.0: loaded firmware version 8.24.2.12
Jan 18 19:32:51 x-laptop kernel: [    4.795295] hda_codec: ALC662 rev1: BIOS auto-probing.
Jan 18 19:32:51 x-laptop kernel: [    4.796553] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input11
Jan 18 19:32:51 x-laptop kernel: [    4.838606] Registered led device: iwl-phy0::radio
Jan 18 19:32:51 x-laptop kernel: [    4.838617] Registered led device: iwl-phy0::assoc
Jan 18 19:32:51 x-laptop kernel: [    4.838627] Registered led device: iwl-phy0::RX
Jan 18 19:32:51 x-laptop kernel: [    4.838637] Registered led device: iwl-phy0::TX
Jan 18 19:32:51 x-laptop kernel: [    4.860815] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jan 18 19:32:52 x-laptop kernel: [    5.209430] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x1280b1, caps: 0xa04711/0xa04000
Jan 18 19:32:52 x-laptop kernel: [    5.248246] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input12
Jan 18 19:32:52 x-laptop kernel: [    5.452561] VBoxDrv: dbg - g_abExecMemory=ffffffffa0d8fa20
Jan 18 19:32:52 x-laptop kernel: [    5.452580] vboxdrv: fAsync=0 offMin=0x145 offMax=0x1c2f
Jan 18 19:32:52 x-laptop kernel: [    5.452934] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
Jan 18 19:32:52 x-laptop kernel: [    5.476347] ACPI Warning for \_SB_.PCI0.P0P2.VGA_.MXMI: Excess arguments - needs 1, found 2 (20090903/nspredef-303)
Jan 18 19:32:52 x-laptop kernel: [    5.476375] ACPI Warning for \_SB_.PCI0.P0P2.VGA_.MXMS: Excess arguments - needs 1, found 2 (20090903/nspredef-303)
Jan 18 19:32:53 x-laptop kernel: [    6.306202] ppdev: user-space parallel port driver
Jan 18 19:33:01 x-laptop nautilus: [N-A] Nautilus-Actions Menu Extender 2.30.2 initializing...
Jan 18 19:33:01 x-laptop nautilus: [N-A] Nautilus-Actions Tracker 2.30.2 initializing...
Jan 18 19:33:04 x-laptop kernel: [   17.307903] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Jan 18 19:33:04 x-laptop kernel: [   17.347422] Intel AES-NI instructions are not detected.
Jan 18 19:33:04 x-laptop kernel: [   17.383219] padlock: VIA PadLock not detected.

[/I]
```

---

### Post by mikewhatever on 2011-01-18
Try testing your RAM with memtest.
PS: Posting your hardware specs would have been nice.

---

### Post by Objectivity on 2011-01-18
> **mikewhatever said:**
> Try testing your RAM with memtest.
PS: Posting your hardware specs would have been nice.

 I will.  Let you know. Thank you

---

### Post by Objectivity on 2011-01-18
> **mikewhatever said:**
> Try testing your RAM with memtest.
PS: Posting your hardware specs would have been nice.


 I think It would take few hours or so ... So I let it run tonight will get back to you tomorrow :- ) :popcorn:

---

### Post by Objectivity on 2011-01-18
> **mikewhatever said:**
> Try testing your RAM with memtest.
PS: Posting your hardware specs would have been nice.


 by the way, here is hardware specs ..

code:
```

x-laptop                  
    description: Laptop
    product: M570TU
    vendor: CLEVO CO.
    version: Not Applicable
    serial: Not Applicable
    width: 64 bits
    capabilities: smbios-2.5 dmi-2.5 vsyscall64 vsyscall32
    configuration: boot=normal chassis=laptop uuid=0090F587-E5AF-0000-0000-000000000000
  *-core
       description: Motherboard
       physical id: 0
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies LTD
          physical id: 0
          version: 1.00.12c (01/08/2009)
          size: 106KiB
          capacity: 1472KiB
          capabilities: isa pci pcmcia pnp upgrade shadowing escd cdboot bootselect int9keyboard int10video acpi usb agp smartbattery biosbootspecification
     *-board UNCLAIMED
          description: Mother Board
          product: M570TU
          vendor: CLEVO CO.
          physical id: 2
          version: Not Applicable
          serial: Not Applicable
          slot: Not Applicable
     *-cpu
          description: CPU
          product: Intel(R) Core(TM)2 Extreme CPU X9100  @ 3.06GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: CPU Version
          slot: U22
          size: 3466MHz
          capacity: 4096MHz
          width: 64 bits
          clock: 266MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx x86-64 constant_tsc arch_perfmon pebs bts rep_good aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 lahf_lm tpr_shadow vnmi flexpriority cpufreq
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1 Cache
             size: 64KiB
             capacity: 64KiB
             capabilities: asynchronous internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2 Cache
             size: 6MiB
             capabilities: burst internal write-back unified
     *-memory
          description: System Memory
          physical id: 1d
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: SODIMM Synchronous 1066 MHz (0.9 ns)
             product: 16JSF25664HY-1G1D1
             vendor: 802C
             physical id: 0
             serial: EA190F9A
             slot: M1
             size: 2GiB
             width: 64 bits
             clock: 1066MHz (0.9ns)
        *-bank:1
             description: SODIMM Synchronous 1066 MHz (0.9 ns)
             product: 16JSF25664HY-1G1D1
             vendor: 802C
             physical id: 1
             serial: E328B3EF
             slot: M2
             size: 2GiB
             width: 64 bits
             clock: 1066MHz (0.9ns)
     *-pci
          description: Host bridge
          product: Mobile 4 Series Chipset Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 07
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: Mobile 4 Series Chipset PCI Express Graphics Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 07
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress bus_master cap_list
             configuration: driver=pcieport
             resources: irq:24 ioport:2000(size=4096) memory:f0000000-f2ffffff ioport:d0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: GT200 [GeForce GTX 280M]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a2
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:16 memory:f2000000-f2ffffff memory:d0000000-dfffffff(prefetchable) memory:f0000000-f1ffffff ioport:2000(size=128)
        *-usb:0
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:1800(size=32)
        *-usb:1
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:21 ioport:1820(size=32)
        *-usb:2
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #6
             vendor: Intel Corporation
             physical id: 1a.2
             bus info: pci@0000:00:1a.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:1840(size=32)
        *-usb:3
             description: USB Controller
             product: 82801I (ICH9 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:19 memory:f3604800-f3604bff
        *-multimedia
             description: Audio device
             product: 82801I (ICH9 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:22 memory:f3600000-f3603fff
        *-pci:1
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport
             resources: irq:25 ioport:3000(size=4096) memory:f3100000-f31fffff ioport:f8000000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8111/8168B PCI Express Gigabit Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: 02
                serial: 00:90:f5:87:e5:af
                size: 10MB/s
                capacity: 1GB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
                resources: irq:31 ioport:3000(size=256) memory:f3100000-f3100fff memory:f8000000-f800ffff(prefetchable) memory:f8020000-f803ffff(prefetchable)
        *-pci:2
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport
             resources: irq:26 ioport:4000(size=4096) memory:f3300000-f33fffff memory:c0000000-c01fffff(prefetchable)
           *-memory UNCLAIMED
                description: Memory controller
                product: Turbo Memory Controller
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                version: 11
                width: 32 bits
                clock: 33MHz (30.3ns)
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: latency=0
                resources: memory:f3300000-f33003ff ioport:4000(size=256) memory:c0000000-c000ffff(prefetchable)
        *-pci:3
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport
             resources: irq:27 ioport:6000(size=4096) memory:f3200000-f32fffff memory:c0200000-c03fffff(prefetchable)
           *-firewire
                description: FireWire (IEEE 1394)
                product: IEEE 1394 Host Controller
                vendor: JMicron Technology Corp.
                physical id: 0
                bus info: pci@0000:04:00.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: driver=ohci1394 latency=0
                resources: irq:18 memory:f3200000-f32007ff memory:f3201000-f320107f memory:f3200c00-f3200c7f memory:f3200800-f320087f
           *-generic:0
                description: System peripheral
                product: SD/MMC Host Controller
                vendor: JMicron Technology Corp.
                physical id: 0.1
                bus info: pci@0000:04:00.1
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: driver=sdhci-pci latency=0
                resources: irq:18 memory:f3201400-f32014ff
           *-generic:1 UNCLAIMED
                description: SD Host controller
                product: Standard SD Host Controller
                vendor: JMicron Technology Corp.
                physical id: 0.2
                bus info: pci@0000:04:00.2
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi cap_list
                configuration: latency=0
                resources: memory:f3201800-f32018ff
           *-generic:2
                description: System peripheral
                product: MS Host Controller
                vendor: JMicron Technology Corp.
                physical id: 0.3
                bus info: pci@0000:04:00.3
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: driver=jmb38x_ms latency=0
                resources: irq:18 memory:f3201c00-f3201cff
        *-pci:4
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport
             resources: irq:28 ioport:5000(size=4096) memory:f4000000-f5ffffff ioport:f6000000(size=33554432)
        *-pci:5
             description: PCI bridge
             product: 82801I (ICH9 Family) PCI Express Port 6
             vendor: Intel Corporation
             physical id: 1c.5
             bus info: pci@0000:00:1c.5
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport
             resources: irq:29 ioport:7000(size=4096) memory:f3000000-f30fffff memory:c0400000-c05fffff(prefetchable)
           *-network
                description: Wireless interface
                product: PRO/Wireless 5300 AGN [Shiloh] Network Connection
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:07:00.0
                logical name: wlan0
                version: 00
                serial: 00:16:ea:c3:4e:7c
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=iwlagn ip=192.168.1.100 latency=0 multicast=yes wireless=IEEE 802.11abgn
                resources: irq:32 memory:f3000000-f3001fff
        *-usb:4
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:1860(size=32)
        *-usb:5
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:1880(size=32)
        *-usb:6
             description: USB Controller
             product: 82801I (ICH9 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:18a0(size=32)
        *-usb:7
             description: USB Controller
             product: 82801I (ICH9 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:f3604c00-f3604fff
        *-pci:6
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 93
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
        *-isa
             description: ISA bridge
             product: ICH9M LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-storage
             description: SATA controller
             product: ICH9M/M-E SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi1
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm bus_master cap_list emulated
             configuration: driver=ahci latency=0
             resources: irq:30 ioport:18f0(size=8) ioport:18e4(size=4) ioport:18e8(size=8) ioport:18e0(size=4) ioport:18c0(size=32) memory:f3604000-f36047ff
           *-disk
                description: ATA Disk
                product: OCZ-AGILITY2
                physical id: 0.0.0
                bus info: scsi@1:0.0.0
                logical name: /dev/sda
                version: 1.25
                serial: OCZ-0H74424K0FI3J745
                size: 111GiB (120GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=0007ac31
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@1:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: a00c9ced-0a29-5741-ad32-33d7301d318b
                   size: 46GiB
                   capacity: 46GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2010-12-29 05:48:45 filesystem=ntfs modified_by_chkdsk=true mounted_on_nt4=true resize_log_file=true state=dirty upgrade_on_mount=true
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@1:0.0.0,2
                   logical name: /dev/sda2
                   size: 65GiB
                   capacity: 65GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux filesystem partition
                      physical id: 5
                      logical name: /dev/sda5
                      logical name: /
                      capacity: 62GiB
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered state=mounted
                 *-logicalvolume:1
                      description: Linux swap / Solaris partition
                      physical id: 6
                      logical name: /dev/sda6
                      capacity: 2781MiB
                      capabilities: nofs
        *-serial UNCLAIMED
             description: SMBus
             product: 82801I (ICH9 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 03
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:c0600000-c06000ff ioport:1c00(size=32)
  *-power UNCLAIMED
       description: To Be Defined By O.E.M
       product: To Be Defined By O.E.M
       vendor: To Be Defined By O.E.M
       physical id: 1
       version: 2.50
       serial: To Be Defined By O.E.M
       capacity: 32768mWh
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes
x@x-laptop:~$

```

---

### Post by adrien214 on 2011-02-23
So... nothing was working but you were able to move the mouse? how about the keyboard ? Alt+TAB ? Alt+F1 ? If you manage to get a terminal and type

  ```
 x@x-laptop:~$ top
``` 

while you are experiencing difficulties, it would be nice ;)

Also, what version of ubuntu ? Your system looks much much much more recent than mine and I download several torrents at insane speeds and watch a movie at the same time with VLC.

Also, how much space on your drive ?
I'm not using azureus aynmore, try Transmission it's light!

---

