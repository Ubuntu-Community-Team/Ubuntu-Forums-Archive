---
title: "Ubuntu Maverick takes forever to launch!"
date: 2011-01-20
forum: New to Ubuntu
---

### Post by haydemon on 2011-01-20
I have a dual boot system, running Windows XP and Ubuntu 10.10. After one of the more recent updates, I've been having difficulty with Ubuntu taking about 10-15 minutes to launch (after Grub loads with all the different OS choices listed). After clicking on the Ubuntu OS it feels like nothing is going to happen, with the screen going black with just a cursor blinking at the top of the screen. I've been giving up and launching Windows for work, but the other day I just let it run after a re-start and after about 15 minutes, Ubuntu eventually launched! So I tried again, and the same thing happened.

I thought I'd need to do a new install (even ordered the CD), but I'd rather not do that so as not to loose all my settings, etc. Is there an explanation for this, or if there is something that needs to be fixed, can I get detailed information as to what to do? Even though I've been using Linux for a couple of years now, I've never had a lot of time to learn a lot of the technical stuff, and when I succeed in resolving an issue, I forget steps I've taken.:( So I still consider myself a "newbie.":?

If you need more information, please tell me how to find it. Thanks!

---

### Post by mikewhatever on 2011-01-20
In Ubuntu, run the following and attach the boot.txt to your post.
```
dmesg > ~/Desktop/boot.txt
```

---

### Post by haydemon on 2011-01-21
I ran the code at the command line, but nothing happened. I just gave me a new prompt. I even tried with 'sudo' but still the same result.

---

### Post by mikewhatever on 2011-01-21
Look for boot.txt on the desktop. If you run is with sudo, the file will be owned by root, nothing else, but it's obviously redundant.

---

### Post by haydemon on 2011-01-21
Right! Here it is (below; too large to attach):

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.35-25-generic (buildd@roseapple) (gcc version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu5) ) #43-Ubuntu SMP Thu Jan 6 22:25:16 UTC 2011 (Ubuntu 2.6.35-25.43-generic 2.6.35.10)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000001e00000 (usable)
[    0.000000]  BIOS-e820: 0000000001e00000 - 0000000001e80040 (reserved)
[    0.000000]  BIOS-e820: 0000000001e80040 - 000000007bed0000 (usable)
[    0.000000]  BIOS-e820: 000000007bed0000 - 000000007bed3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007bed3000 - 000000007bee0000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007bee0000 - 000000007bf00000 (reserved)
[    0.000000]  BIOS-e820: 000000007c000000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f4000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] Notice: NX (Execute Disable) protection cannot be enabled: non-PAE kernel!
[    0.000000] DMI 2.4 present.
[    0.000000] e820 update range: 0000000000000000 - 0000000000001000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x7bed0 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-C7FFF write-protect
[    0.000000]   C8000-FFFFF uncachable
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0000000000 mask FF80000000 write-back
[    0.000000]   1 base 007FF00000 mask FFFFF00000 uncachable
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 0000000000002000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000001000 (reserved)
[    0.000000]  modified: 0000000000001000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000002000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009f800 (usable)
[    0.000000]  modified: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 0000000001e00000 (usable)
[    0.000000]  modified: 0000000001e00000 - 0000000001e80040 (reserved)
[    0.000000]  modified: 0000000001e80040 - 000000007bed0000 (usable)
[    0.000000]  modified: 000000007bed0000 - 000000007bed3000 (ACPI NVS)
[    0.000000]  modified: 000000007bed3000 - 000000007bee0000 (ACPI data)
[    0.000000]  modified: 000000007bee0000 - 000000007bf00000 (reserved)
[    0.000000]  modified: 000000007c000000 - 0000000080000000 (reserved)
[    0.000000]  modified: 00000000f0000000 - 00000000f4000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] found SMP MP-table at [c00f3ff0] f3ff0
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 15000-1a000
[    0.000000] RAMDISK: 375ad000 - 37ff0000
[    0.000000] Allocated new RAMDISK: 009a7000 - 013e992e
[    0.000000] Move RAMDISK from 00000000375ad000 - 0000000037fef92d to 009a7000 - 013e992d
[    0.000000] ACPI: RSDP 000f8710 00014 (v00 DELL  )
[    0.000000] ACPI: RSDT 7bed3040 00048 (v01 DELL    bMk     42302E31 AWRD 00000000)
[    0.000000] ACPI: FACP 7bed3100 00074 (v01 DELL    bMk     42302E31 AWRD 00000000)
[    0.000000] ACPI: DSDT 7bed31c0 06C0B (v01 DELL   AWRDACPI 00001000 MSFT 03000001)
[    0.000000] ACPI: FACS 7bed0000 00040
[    0.000000] ACPI: BOOT 7bed9e40 00028 (v01 DELL    bMk     42302E31 AWRD 00000000)
[    0.000000] ACPI: TCPA 7bed9f80 00032 (v01 DELL    bMk     42302E31 AWRD 00000000)
[    0.000000] ACPI: SSDT 7beda000 00115 (v01 PTLTD  POWERNOW 00000001  LTP 00000001)
[    0.000000] ACPI: ASF! 7beda180 0008A (v32 DELL    bMk     42302E31 AWRD 00000000)
[    0.000000] ACPI: HPET 7beda280 00038 (v01 DELL    bMk     42302E31 AWRD 00000098)
[    0.000000] ACPI: MCFG 7beda300 0003C (v01 DELL    bMk     42302E31 AWRD 00000000)
[    0.000000] ACPI: SLIC 7beda380 00176 (v01 DELL    bMk     42302E31 AWRD 0100000E)
[    0.000000] ACPI: APIC 7bed9ec0 0007C (v01 DELL    bMk     42302E31 AWRD 00000000)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 1094MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000001 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0007bed0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[4] active PFN ranges
[    0.000000]     0: 0x00000001 -> 0x00000002
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x00001e00
[    0.000000]     0: 0x00001e81 -> 0x0007bed0
[    0.000000] On node 0 totalpages: 507359
[    0.000000] free_area_init_node: node 0, pgdat c07fffc0, node_mem_map c1e81020
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3952 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221357 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2190 pages used for memmap
[    0.000000]   HighMem zone: 278084 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] Detected use of extended apic ids on hypertransport bus
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x10b9a201 base: 0xfeff0000
[    0.000000] SMP: Allowing 2 CPUs, 1 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] early_res array is doubled to 64 at [16000 - 167ff]
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000010000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 0000000001e00000 - 0000000001e80000
[    0.000000] PM: Registered nosave memory: 0000000001e80000 - 0000000001e81000
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 80000000:70000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @c1400000 s36416 r0 d20928 u2097152
[    0.000000] pcpu-alloc: s36416 r0 d20928 u2097152 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 1 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 503393
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-25-generic root=UUID=a33acf9c-0574-45bc-8f14-a07000149892 ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 10151980 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Subtract (53 early reservations)
[    0.000000]   #1 [0000001000 - 0000002000]   EX TRAMPOLINE
[    0.000000]   #2 [0000100000 - 00009a2adc]   TEXT DATA BSS
[    0.000000]   #3 [00009a3000 - 00009a61cc]             BRK
[    0.000000]   #4 [00000f4000 - 0000100000]   BIOS reserved
[    0.000000]   #5 [00000f3ff0 - 00000f4000]    MP-table mpf
[    0.000000]   #6 [000009f800 - 00000f21e4]   BIOS reserved
[    0.000000]   #7 [00000f2304 - 00000f3ff0]   BIOS reserved
[    0.000000]   #8 [00000f21e4 - 00000f2304]    MP-table mpc
[    0.000000]   #9 [0000010000 - 0000011000]      TRAMPOLINE
[    0.000000]   #10 [0000011000 - 0000015000]     ACPI WAKEUP
[    0.000000]   #11 [0000015000 - 0000016000]         PGTABLE
[    0.000000]   #12 [00009a7000 - 00013ea000]     NEW RAMDISK
[    0.000000]   #13 [00013ea000 - 00013eb000]         BOOTMEM
[    0.000000]   #14 [0001e81000 - 0002e01000]         BOOTMEM
[    0.000000]   #15 [00013eb000 - 00013eb004]         BOOTMEM
[    0.000000]   #16 [00013eb040 - 00013eb100]         BOOTMEM
[    0.000000]   #17 [00013eb100 - 00013eb154]         BOOTMEM
[    0.000000]   #18 [00013eb180 - 00013ee180]         BOOTMEM
[    0.000000]   #19 [00013ee180 - 00013ee1e8]         BOOTMEM
[    0.000000]   #20 [00013ee200 - 00013f4200]         BOOTMEM
[    0.000000]   #21 [00013f4200 - 00013f4225]         BOOTMEM
[    0.000000]   #22 [00013f4240 - 00013f4267]         BOOTMEM
[    0.000000]   #23 [00013f4280 - 00013f4424]         BOOTMEM
[    0.000000]   #24 [00013f4440 - 00013f4480]         BOOTMEM
[    0.000000]   #25 [00013f4480 - 00013f44c0]         BOOTMEM
[    0.000000]   #26 [00013f44c0 - 00013f4500]         BOOTMEM
[    0.000000]   #27 [00013f4500 - 00013f4540]         BOOTMEM
[    0.000000]   #28 [00013f4540 - 00013f4580]         BOOTMEM
[    0.000000]   #29 [00013f4580 - 00013f45c0]         BOOTMEM
[    0.000000]   #30 [00013f45c0 - 00013f4600]         BOOTMEM
[    0.000000]   #31 [00013f4600 - 00013f4640]         BOOTMEM
[    0.000000]   #32 [00013f4640 - 00013f4680]         BOOTMEM
[    0.000000]   #33 [00013f4680 - 00013f46c0]         BOOTMEM
[    0.000000]   #34 [00013f46c0 - 00013f4700]         BOOTMEM
[    0.000000]   #35 [00013f4700 - 00013f4740]         BOOTMEM
[    0.000000]   #36 [00013f4740 - 00013f4750]         BOOTMEM
[    0.000000]   #37 [00013f4780 - 00013f4790]         BOOTMEM
[    0.000000]   #38 [00013f47c0 - 00013f47d0]         BOOTMEM
[    0.000000]   #39 [00013f4800 - 00013f486a]         BOOTMEM
[    0.000000]   #40 [00013f4880 - 00013f48ea]         BOOTMEM
[    0.000000]   #41 [0001400000 - 000140e000]         BOOTMEM
[    0.000000]   #42 [0001600000 - 000160e000]         BOOTMEM
[    0.000000]   #43 [00013f6900 - 00013f6904]         BOOTMEM
[    0.000000]   #44 [00013f6940 - 00013f6944]         BOOTMEM
[    0.000000]   #45 [00013f6980 - 00013f6988]         BOOTMEM
[    0.000000]   #46 [00013f69c0 - 00013f69c8]         BOOTMEM
[    0.000000]   #47 [00013f6a00 - 00013f6aa8]         BOOTMEM
[    0.000000]   #48 [00013f6ac0 - 00013f6b28]         BOOTMEM
[    0.000000]   #49 [00013f6b40 - 00013fab40]         BOOTMEM
[    0.000000]   #50 [000140e000 - 000148e000]         BOOTMEM
[    0.000000]   #51 [000148e000 - 00014ce000]         BOOTMEM
[    0.000000]   #52 [0002e01000 - 00037af82c]         BOOTMEM
[    0.000000] Initializing HighMem for node 0 (000377fe:0007bed0)
[    0.000000] Memory: 1983308k/2030400k available (4933k kernel code, 46128k reserved, 2331k data, 688k init, 1121096k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc0819000 - 0xc08c5000   ( 688 kB)
[    0.000000]       .data : 0xc05d17ce - 0xc08187a8   (2331 kB)
[    0.000000]       .text : 0xc0100000 - 0xc05d17ce   (4933 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU-based detection of stalled CPUs is disabled.
[    0.000000]     Verbose stalled-CPUs detection is disabled.
[    0.000000] NR_IRQS:2304 nr_irqs:512
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2204.318 MHz processor.
[    0.004006] Calibrating delay loop (skipped), value calculated using timer frequency.. 4408.63 BogoMIPS (lpj=8817272)
[    0.004013] pid_max: default: 32768 minimum: 301
[    0.004035] Security Framework initialized
[    0.004058] AppArmor: AppArmor initialized
[    0.004061] Yama: becoming mindful.
[    0.004129] Mount-cache hash table entries: 512
[    0.004278] Initializing cgroup subsys ns
[    0.004283] Initializing cgroup subsys cpuacct
[    0.004288] Initializing cgroup subsys memory
[    0.004299] Initializing cgroup subsys devices
[    0.004302] Initializing cgroup subsys freezer
[    0.004306] Initializing cgroup subsys net_cls
[    0.004334] mce: CPU supports 5 MCE banks
[    0.004346] using C1E aware idle routine
[    0.004354] Performance Events: AMD PMU driver.
[    0.004362] ... version:                0
[    0.004365] ... bit width:              48
[    0.004367] ... generic registers:      4
[    0.008004] ... value mask:             0000ffffffffffff
[    0.008007] ... max period:             00007fffffffffff
[    0.008010] ... fixed-purpose events:   0
[    0.008012] ... event mask:             000000000000000f
[    0.008850] SMP alternatives: switching to UP code
[    0.016244] ACPI: Core revision 20100428
[    0.026247] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.026252] ftrace: allocating 21756 entries in 43 pages
[    0.028082] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.028609] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.071586] CPU0: AMD Athlon(tm) 64 Processor 3500+ stepping 02
[    0.072000] Brought up 1 CPUs
[    0.072000] Total of 1 processors activated (4408.63 BogoMIPS).
[    0.072000] devtmpfs: initialized
[    0.072000] regulator: core version 0.5
[    0.072000] Time:  9:11:51  Date: 01/20/11
[    0.072000] NET: Registered protocol family 16
[    0.072000] EISA bus registered
[    0.072000] node 0 link 0: io port [8000, ffff]
[    0.072000] TOM: 0000000080000000 aka 2048M
[    0.072000] node 0 link 0: mmio [a0000, bffff]
[    0.072000] node 0 link 0: mmio [80000000, efffffff]
[    0.072000] node 0 link 0: mmio [f4000000, fe02ffff]
[    0.072000] node 0 link 0: mmio [f0000000, f04fffff]
[    0.072000] bus: [00, 04] on node 0 link 0
[    0.072000] bus: 00 index 0 [io  0x0000-0xffff]
[    0.072000] bus: 00 index 1 [mem 0x000a0000-0x000bffff]
[    0.072000] bus: 00 index 2 [mem 0x80000000-0xf3ffffff]
[    0.072000] bus: 00 index 3 [mem 0xf4000000-0xffffffff]
[    0.072000] ACPI: bus type pci registered
[    0.072000] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf0000000-0xf3ffffff] (base 0xf0000000)
[    0.072000] PCI: MMCONFIG at [mem 0xf0000000-0xf3ffffff] reserved in E820
[    0.072000] PCI: Using MMCONFIG for extended config space
[    0.072000] PCI: Using configuration type 1 for base access
[    0.072000] bio: create slab <bio-0> at 0
[    0.072202] ACPI: EC: Look up EC in DSDT
[    0.077562] ACPI: Interpreter enabled
[    0.077565] ACPI: (supports S0 S1 S3 S4 S5)
[    0.077592] ACPI: Using IOAPIC for interrupt routing
[    0.087523] ACPI: No dock devices found.
[    0.087527] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
[    0.088486] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-04])
[    0.090349] pci_root PNP0A08:00: host bridge window [io  0x0000-0x03af] (ignored)
[    0.090352] pci_root PNP0A08:00: host bridge window [io  0x03e0-0x0cf7] (ignored)
[    0.090355] pci_root PNP0A08:00: host bridge window [io  0x8000-0xffff] (ignored)
[    0.090357] pci_root PNP0A08:00: host bridge window [io  0x03b0-0x03df] (ignored)
[    0.090360] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)
[    0.090363] pci_root PNP0A08:00: host bridge window [mem 0x80000000-0xefffffff] (ignored)
[    0.090366] pci_root PNP0A08:00: host bridge window [mem 0xf4000000-0xfe02ffff] (ignored)
[    0.090369] pci_root PNP0A08:00: host bridge window [mem 0xfed40000-0xfed44fff] (ignored)
[    0.090371] pci_root PNP0A08:00: host bridge window [io  0x0cb0-0x0cbf] (ignored)
[    0.090374] pci_root PNP0A08:00: host bridge window [io  0x1c00-0x1c80] (ignored)
[    0.090377] pci_root PNP0A08:00: host bridge window [mem 0xfec80000-0xfecbffff] (ignored)
[    0.090583] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.090586] pci 0000:00:02.0: PME# disabled
[    0.090614] pci 0000:00:03.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.090617] pci 0000:00:03.0: PME# disabled
[    0.090644] pci 0000:00:04.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.090647] pci 0000:00:04.0: PME# disabled
[    0.090662] pci 0000:00:05.0: reg 10: [mem 0xfc000000-0xfcffffff]
[    0.090667] pci 0000:00:05.0: reg 14: [mem 0xe0000000-0xefffffff 64bit pref]
[    0.090672] pci 0000:00:05.0: reg 1c: [mem 0xfb000000-0xfbffffff 64bit]
[    0.090677] pci 0000:00:05.0: reg 30: [mem 0x00000000-0x0001ffff pref]
[    0.090896] pci 0000:00:0a.1: reg 20: [io  0x1c00-0x1c3f]
[    0.090901] pci 0000:00:0a.1: reg 24: [io  0x1c40-0x1c7f]
[    0.090924] pci 0000:00:0a.1: PME# supported from D3hot D3cold
[    0.090930] pci 0000:00:0a.1: PME# disabled
[    0.090989] pci 0000:00:0b.0: reg 10: [mem 0xfe02f000-0xfe02ffff]
[    0.091016] pci 0000:00:0b.0: supports D1 D2
[    0.091018] pci 0000:00:0b.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.091021] pci 0000:00:0b.0: PME# disabled
[    0.091042] pci 0000:00:0b.1: reg 10: [mem 0xfe02e000-0xfe02e0ff]
[    0.091070] pci 0000:00:0b.1: supports D1 D2
[    0.091072] pci 0000:00:0b.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.091076] pci 0000:00:0b.1: PME# disabled
[    0.091107] pci 0000:00:0e.0: reg 10: [io  0x09f0-0x09f7]
[    0.091111] pci 0000:00:0e.0: reg 14: [io  0x0bf0-0x0bf3]
[    0.091116] pci 0000:00:0e.0: reg 18: [io  0x0970-0x0977]
[    0.091120] pci 0000:00:0e.0: reg 1c: [io  0x0b70-0x0b73]
[    0.091124] pci 0000:00:0e.0: reg 20: [io  0xe000-0xe00f]
[    0.091129] pci 0000:00:0e.0: reg 24: [mem 0xfe02d000-0xfe02dfff]
[    0.091169] pci 0000:00:0f.0: reg 10: [io  0x09e0-0x09e7]
[    0.091173] pci 0000:00:0f.0: reg 14: [io  0x0be0-0x0be3]
[    0.091178] pci 0000:00:0f.0: reg 18: [io  0x0960-0x0967]
[    0.091182] pci 0000:00:0f.0: reg 1c: [io  0x0b60-0x0b63]
[    0.091187] pci 0000:00:0f.0: reg 20: [io  0xcc00-0xcc0f]
[    0.091191] pci 0000:00:0f.0: reg 24: [mem 0xfe02c000-0xfe02cfff]
[    0.091264] pci 0000:00:10.1: reg 10: [mem 0xfe024000-0xfe027fff]
[    0.091296] pci 0000:00:10.1: PME# supported from D3hot D3cold
[    0.091300] pci 0000:00:10.1: PME# disabled
[    0.091382] PCI: peer root bus 00 res updated from pci conf
[    0.091405] pci 0000:00:02.0: PCI bridge to [bus 01-01]
[    0.091408] pci 0000:00:02.0:   bridge window [io  0xa000-0xafff]
[    0.091412] pci 0000:00:02.0:   bridge window [mem 0xfd800000-0xfd8fffff]
[    0.091415] pci 0000:00:02.0:   bridge window [mem 0xfd700000-0xfd7fffff 64bit pref]
[    0.091460] pci 0000:02:00.0: reg 10: [mem 0xfdef0000-0xfdefffff 64bit]
[    0.091507] pci 0000:02:00.0: PME# supported from D3hot D3cold
[    0.091510] pci 0000:02:00.0: PME# disabled
[    0.096014] pci 0000:00:03.0: PCI bridge to [bus 02-02]
[    0.096018] pci 0000:00:03.0:   bridge window [io  0x8000-0x8fff]
[    0.096021] pci 0000:00:03.0:   bridge window [mem 0xfde00000-0xfdefffff]
[    0.096024] pci 0000:00:03.0:   bridge window [mem 0xfdd00000-0xfddfffff 64bit pref]
[    0.096045] pci 0000:00:04.0: PCI bridge to [bus 03-03]
[    0.096048] pci 0000:00:04.0:   bridge window [io  0xb000-0xbfff]
[    0.096051] pci 0000:00:04.0:   bridge window [mem 0xfdc00000-0xfdcfffff]
[    0.096055] pci 0000:00:04.0:   bridge window [mem 0xfd900000-0xfd9fffff 64bit pref]
[    0.096102] pci 0000:00:10.0: PCI bridge to [bus 04-04] (subtractive decode)
[    0.096106] pci 0000:00:10.0:   bridge window [io  0x9000-0x9fff]
[    0.096109] pci 0000:00:10.0:   bridge window [mem 0xfdb00000-0xfdbfffff]
[    0.096113] pci 0000:00:10.0:   bridge window [mem 0xfda00000-0xfdafffff pref]
[    0.096116] pci 0000:00:10.0:   bridge window [io  0x0000-0xffff] (subtractive decode)
[    0.096118] pci 0000:00:10.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.096121] pci 0000:00:10.0:   bridge window [mem 0x80000000-0xf3ffffff] (subtractive decode)
[    0.096124] pci 0000:00:10.0:   bridge window [mem 0xf4000000-0xffffffff] (subtractive decode)
[    0.096133] pci_bus 0000:00: on NUMA node 0
[    0.096138] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.096368] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[    0.188662] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.188816] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.188969] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.189122] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.189276] ACPI: PCI Interrupt Link [LNK5] (IRQs 5 7 9 10 11 *14 15)
[    0.189428] ACPI: PCI Interrupt Link [LNK6] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.189582] ACPI: PCI Interrupt Link [LNK7] (IRQs *5 7 9 10 11 14 15)
[    0.189734] ACPI: PCI Interrupt Link [LNK8] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.189889] ACPI: PCI Interrupt Link [LUBA] (IRQs 5 7 9 10 11 14 *15)
[    0.190041] ACPI: PCI Interrupt Link [LUBB] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.190195] ACPI: PCI Interrupt Link [LMAC] (IRQs 5 7 9 *10 11 14 15)
[    0.190348] ACPI: PCI Interrupt Link [LACI] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.190502] ACPI: PCI Interrupt Link [LAZA] (IRQs 5 7 9 10 *11 14 15)
[    0.190656] ACPI: PCI Interrupt Link [LPMU] (IRQs 5 7 9 10 11 *14 15)
[    0.190809] ACPI: PCI Interrupt Link [LMCI] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.190964] ACPI: PCI Interrupt Link [LSMB] (IRQs 5 7 9 *10 11 14 15)
[    0.191118] ACPI: PCI Interrupt Link [LUB2] (IRQs *5 7 9 10 11 14 15)
[    0.191282] ACPI: PCI Interrupt Link [LIDE] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.191437] ACPI: PCI Interrupt Link [LSID] (IRQs 5 7 9 *10 11 14 15)
[    0.191597] ACPI: PCI Interrupt Link [LFID] (IRQs 5 7 9 10 *11 14 15)
[    0.191800] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0, disabled.
[    0.191993] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.
[    0.192193] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0, disabled.
[    0.192385] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0, disabled.
[    0.192578] ACPI: PCI Interrupt Link [APC5] (IRQs 16) *0
[    0.192770] ACPI: PCI Interrupt Link [APC6] (IRQs 16) *0, disabled.
[    0.192963] ACPI: PCI Interrupt Link [APC7] (IRQs 16) *0
[    0.193155] ACPI: PCI Interrupt Link [APC8] (IRQs 16) *0, disabled.
[    0.193348] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22 23) *0
[    0.193542] ACPI: PCI Interrupt Link [APCG] (IRQs 20 21 22 23) *0, disabled.
[    0.193736] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0
[    0.193934] ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22 23) *0, disabled.
[    0.194128] ACPI: PCI Interrupt Link [APMU] (IRQs 20 21 22 23) *0
[    0.194321] ACPI: PCI Interrupt Link [AAZA] (IRQs 20 21 22 23) *0
[    0.194515] ACPI: PCI Interrupt Link [APCK] (IRQs 20 21 22 23) *0, disabled.
[    0.194709] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0
[    0.194903] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22 23) *0
[    0.195097] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22 23) *0, disabled.
[    0.195291] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.
[    0.195485] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0
[    0.195679] ACPI: PCI Interrupt Link [APSJ] (IRQs 20 21 22 23) *0
[    0.195733] HEST: Table is not found!
[    0.195818] vgaarb: device added: PCI:0000:00:05.0,decodes=io+mem,owns=io+mem,locks=none
[    0.195825] vgaarb: loaded
[    0.195992] SCSI subsystem initialized
[    0.196060] libata version 3.00 loaded.
[    0.196113] usbcore: registered new interface driver usbfs
[    0.196127] usbcore: registered new interface driver hub
[    0.196150] usbcore: registered new device driver usb
[    0.196281] ACPI: WMI: Mapper loaded
[    0.196283] PCI: Using ACPI for IRQ routing
[    0.196288] PCI: pci_cache_line_size set to 64 bytes
[    0.196354] reserve RAM buffer: 0000000000002000 - 000000000000ffff 
[    0.196357] reserve RAM buffer: 000000000009f800 - 000000000009ffff 
[    0.196359] reserve RAM buffer: 0000000001e00000 - 0000000003ffffff 
[    0.196362] reserve RAM buffer: 000000007bed0000 - 000000007bffffff 
[    0.196459] NetLabel: Initializing
[    0.196461] NetLabel:  domain hash size = 128
[    0.196463] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.196475] NetLabel:  unlabeled traffic allowed by default
[    0.196509] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.196518] hpet0: at MMIO 0xfeff0000, IRQs 2, 8, 31
[    0.196522] hpet0: 3 comparators, 32-bit 25.000000 MHz counter
[    0.200029] Switching to clocksource hpet
[    0.208871] AppArmor: AppArmor Filesystem Enabled
[    0.208892] pnp: PnP ACPI init
[    0.208912] ACPI: bus type pnp registered
[    0.214328] pnp: PnP ACPI: found 12 devices
[    0.214330] ACPI: ACPI bus type pnp unregistered
[    0.214334] PnPBIOS: Disabled by ACPI PNP
[    0.214346] system 00:01: [io  0x1000-0x107f] has been reserved
[    0.214349] system 00:01: [io  0x1080-0x10ff] has been reserved
[    0.214352] system 00:01: [io  0x1400-0x147f] has been reserved
[    0.214355] system 00:01: [io  0x1480-0x14ff] has been reserved
[    0.214357] system 00:01: [io  0x1800-0x187f] has been reserved
[    0.214360] system 00:01: [io  0x1880-0x18ff] has been reserved
[    0.214363] system 00:01: [io  0x2000-0x207f] has been reserved
[    0.214366] system 00:01: [io  0x2080-0x20ff] has been reserved
[    0.214369] system 00:01: [mem 0xfec80000-0xfecbffff] has been reserved
[    0.214373] system 00:01: [mem 0xfefe0000-0xfefe01ff] has been reserved
[    0.214376] system 00:01: [mem 0x7c000000-0x7fffffff] has been reserved
[    0.214381] system 00:03: [io  0x04d0-0x04d1] has been reserved
[    0.214384] system 00:03: [io  0x0800-0x087f] has been reserved
[    0.214390] system 00:0a: [mem 0xf0000000-0xf3ffffff] has been reserved
[    0.214395] system 00:0b: [mem 0x000cec00-0x000cffff] has been reserved
[    0.214398] system 00:0b: [mem 0x000f0000-0x000f7fff] could not be reserved
[    0.214401] system 00:0b: [mem 0x000f8000-0x000fbfff] could not be reserved
[    0.214404] system 00:0b: [mem 0x000fc000-0x000fffff] could not be reserved
[    0.214408] system 00:0b: [mem 0x7bed0000-0x7befffff] could not be reserved
[    0.214411] system 00:0b: [mem 0xffff0000-0xffffffff] has been reserved
[    0.214414] system 00:0b: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.214417] system 00:0b: [mem 0x00100000-0x7becffff] could not be reserved
[    0.214420] system 00:0b: [mem 0x7bf00000-0x7fefffff] could not be reserved
[    0.214423] system 00:0b: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.214426] system 00:0b: [mem 0xfee00000-0xfeefffff] has been reserved
[    0.214429] system 00:0b: [mem 0xfefff000-0xfeffffff] has been reserved
[    0.214432] system 00:0b: [mem 0xfff80000-0xfff80fff] has been reserved
[    0.214435] system 00:0b: [mem 0xfff90000-0xfffbffff] has been reserved
[    0.214438] system 00:0b: [mem 0xfffed000-0xfffeffff] has been reserved
[    0.250434] pci 0000:00:05.0: BAR 6: assigned [mem 0x80000000-0x8001ffff pref]
[    0.250438] pci 0000:00:02.0: PCI bridge to [bus 01-01]
[    0.250441] pci 0000:00:02.0:   bridge window [io  0xa000-0xafff]
[    0.250445] pci 0000:00:02.0:   bridge window [mem 0xfd800000-0xfd8fffff]
[    0.250448] pci 0000:00:02.0:   bridge window [mem 0xfd700000-0xfd7fffff 64bit pref]
[    0.250452] pci 0000:00:03.0: PCI bridge to [bus 02-02]
[    0.250454] pci 0000:00:03.0:   bridge window [io  0x8000-0x8fff]
[    0.250458] pci 0000:00:03.0:   bridge window [mem 0xfde00000-0xfdefffff]
[    0.250461] pci 0000:00:03.0:   bridge window [mem 0xfdd00000-0xfddfffff 64bit pref]
[    0.250465] pci 0000:00:04.0: PCI bridge to [bus 03-03]
[    0.250467] pci 0000:00:04.0:   bridge window [io  0xb000-0xbfff]
[    0.250470] pci 0000:00:04.0:   bridge window [mem 0xfdc00000-0xfdcfffff]
[    0.250474] pci 0000:00:04.0:   bridge window [mem 0xfd900000-0xfd9fffff 64bit pref]
[    0.250477] pci 0000:00:10.0: PCI bridge to [bus 04-04]
[    0.250480] pci 0000:00:10.0:   bridge window [io  0x9000-0x9fff]
[    0.250484] pci 0000:00:10.0:   bridge window [mem 0xfdb00000-0xfdbfffff]
[    0.250488] pci 0000:00:10.0:   bridge window [mem 0xfda00000-0xfdafffff pref]
[    0.250498] pci 0000:00:02.0: setting latency timer to 64
[    0.250503] pci 0000:00:03.0: setting latency timer to 64
[    0.250508] pci 0000:00:04.0: setting latency timer to 64
[    0.250513] pci 0000:00:10.0: setting latency timer to 64
[    0.250516] pci_bus 0000:00: resource 4 [io  0x0000-0xffff]
[    0.250519] pci_bus 0000:00: resource 5 [mem 0x000a0000-0x000bffff]
[    0.250522] pci_bus 0000:00: resource 6 [mem 0x80000000-0xf3ffffff]
[    0.250524] pci_bus 0000:00: resource 7 [mem 0xf4000000-0xffffffff]
[    0.250527] pci_bus 0000:01: resource 0 [io  0xa000-0xafff]
[    0.250529] pci_bus 0000:01: resource 1 [mem 0xfd800000-0xfd8fffff]
[    0.250532] pci_bus 0000:01: resource 2 [mem 0xfd700000-0xfd7fffff 64bit pref]
[    0.250535] pci_bus 0000:02: resource 0 [io  0x8000-0x8fff]
[    0.250537] pci_bus 0000:02: resource 1 [mem 0xfde00000-0xfdefffff]
[    0.250540] pci_bus 0000:02: resource 2 [mem 0xfdd00000-0xfddfffff 64bit pref]
[    0.250543] pci_bus 0000:03: resource 0 [io  0xb000-0xbfff]
[    0.250545] pci_bus 0000:03: resource 1 [mem 0xfdc00000-0xfdcfffff]
[    0.250548] pci_bus 0000:03: resource 2 [mem 0xfd900000-0xfd9fffff 64bit pref]
[    0.250551] pci_bus 0000:04: resource 0 [io  0x9000-0x9fff]
[    0.250553] pci_bus 0000:04: resource 1 [mem 0xfdb00000-0xfdbfffff]
[    0.250556] pci_bus 0000:04: resource 2 [mem 0xfda00000-0xfdafffff pref]
[    0.250559] pci_bus 0000:04: resource 4 [io  0x0000-0xffff]
[    0.250561] pci_bus 0000:04: resource 5 [mem 0x000a0000-0x000bffff]
[    0.250564] pci_bus 0000:04: resource 6 [mem 0x80000000-0xf3ffffff]
[    0.250566] pci_bus 0000:04: resource 7 [mem 0xf4000000-0xffffffff]
[    0.250603] NET: Registered protocol family 2
[    0.250661] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.250917] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.251486] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.251767] TCP: Hash tables configured (established 131072 bind 65536)
[    0.251769] TCP reno registered
[    0.251773] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.251786] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.251875] NET: Registered protocol family 1
[    0.251925] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.251946] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.251970] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.251975] pci 0000:00:05.0: Boot video device
[    0.268081] pci 0000:00:09.0: Found disabled HT MSI Mapping
[    0.268088] pci 0000:00:0e.0: Enabling HT MSI Mapping
[    0.268139] pci 0000:00:09.0: Found disabled HT MSI Mapping
[    0.268146] pci 0000:00:0f.0: Enabling HT MSI Mapping
[    0.268199] pci 0000:00:09.0: Found disabled HT MSI Mapping
[    0.268205] pci 0000:00:10.0: Enabling HT MSI Mapping
[    0.268260] pci 0000:00:09.0: Found disabled HT MSI Mapping
[    0.268268] pci 0000:00:10.1: Enabling HT MSI Mapping
[    0.268280] PCI: CLS 64 bytes, default 64
[    0.268348] Simple Boot Flag at 0x3a set to 0x1
[    0.268483] cpufreq-nforce2: No nForce2 chipset.
[    0.268518] Scanning for low memory corruption every 60 seconds
[    0.268658] audit: initializing netlink socket (disabled)
[    0.268669] type=2000 audit(1295514394.268:1): initialized
[    0.278926] Trying to unpack rootfs image as initramfs...
[    0.292267] highmem bounce pool size: 64 pages
[    0.292274] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.300362] VFS: Disk quotas dquot_6.5.2
[    0.300451] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.301020] fuse init (API version 7.14)
[    0.301111] msgmni has been set to 1684
[    0.308382] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.308387] io scheduler noop registered
[    0.308388] io scheduler deadline registered
[    0.308402] io scheduler cfq registered (default)
[    0.308526] pcieport 0000:00:02.0: setting latency timer to 64
[    0.308543]   alloc irq_desc for 40 on node -1
[    0.308545]   alloc kstat_irqs on node -1
[    0.308554] pcieport 0000:00:02.0: irq 40 for MSI/MSI-X
[    0.308604] pcieport 0000:00:03.0: setting latency timer to 64
[    0.308618]   alloc irq_desc for 41 on node -1
[    0.308619]   alloc kstat_irqs on node -1
[    0.308624] pcieport 0000:00:03.0: irq 41 for MSI/MSI-X
[    0.308666] pcieport 0000:00:04.0: setting latency timer to 64
[    0.308679]   alloc irq_desc for 42 on node -1
[    0.308681]   alloc kstat_irqs on node -1
[    0.308685] pcieport 0000:00:04.0: irq 42 for MSI/MSI-X
[    0.308757] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.308783] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.308966] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.308972] ACPI: Power Button [PWRB]
[    0.309037] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.309041] ACPI: Power Button [PWRF]
[    0.309504] ACPI: acpi_idle registered with cpuidle
[    0.313802] ERST: Table is not found!
[    0.313979] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.314092] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.314413] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.315575] brd: module loaded
[    0.320295] isapnp: Scanning for PnP cards...
[    0.325895] loop: module loaded
[    0.326554] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 23
[    0.326560]   alloc irq_desc for 23 on node -1
[    0.326562]   alloc kstat_irqs on node -1
[    0.326574] pata_acpi 0000:00:0e.0: PCI INT A -> Link[APSI] -> GSI 23 (level, low) -> IRQ 23
[    0.326609] pata_acpi 0000:00:0e.0: setting latency timer to 64
[    0.326621] pata_acpi 0000:00:0e.0: PCI INT A disabled
[    0.326953] ACPI: PCI Interrupt Link [APSJ] enabled at IRQ 22
[    0.326955]   alloc irq_desc for 22 on node -1
[    0.326957]   alloc kstat_irqs on node -1
[    0.326965] pata_acpi 0000:00:0f.0: PCI INT A -> Link[APSJ] -> GSI 22 (level, low) -> IRQ 22
[    0.326981] pata_acpi 0000:00:0f.0: setting latency timer to 64
[    0.326989] pata_acpi 0000:00:0f.0: PCI INT A disabled
[    0.327325] Fixed MDIO Bus: probed
[    0.327361] PPP generic driver version 2.4.2
[    0.327410] tun: Universal TUN/TAP device driver, 1.6
[    0.327412] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.327488] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.327819] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 21
[    0.327822]   alloc irq_desc for 21 on node -1
[    0.327823]   alloc kstat_irqs on node -1
[    0.327831] ehci_hcd 0000:00:0b.1: PCI INT B -> Link[APCL] -> GSI 21 (level, low) -> IRQ 21
[    0.327849] ehci_hcd 0000:00:0b.1: setting latency timer to 64
[    0.327852] ehci_hcd 0000:00:0b.1: EHCI Host Controller
[    0.327888] ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 1
[    0.327912] ehci_hcd 0000:00:0b.1: debug port 1
[    0.327920] ehci_hcd 0000:00:0b.1: cache line size of 64 is not supported
[    0.327945] ehci_hcd 0000:00:0b.1: irq 21, io mem 0xfe02e000
[    0.375640] ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00
[    0.375815] hub 1-0:1.0: USB hub found
[    0.375821] hub 1-0:1.0: 8 ports detected
[    0.375903] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.376317] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 20
[    0.376322]   alloc irq_desc for 20 on node -1
[    0.376325]   alloc kstat_irqs on node -1
[    0.376335] ohci_hcd 0000:00:0b.0: PCI INT A -> Link[APCF] -> GSI 20 (level, low) -> IRQ 20
[    0.376354] ohci_hcd 0000:00:0b.0: setting latency timer to 64
[    0.376357] ohci_hcd 0000:00:0b.0: OHCI Host Controller
[    0.376398] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 2
[    0.376432] ohci_hcd 0000:00:0b.0: irq 20, io mem 0xfe02f000
[    0.465689] hub 2-0:1.0: USB hub found
[    0.465698] hub 2-0:1.0: 8 ports detected
[    0.465785] uhci_hcd: USB Universal Host Controller Interface driver
[    0.465888] PNP: No PS/2 controller found. Probing ports directly.
[    0.727733] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.727838] mice: PS/2 mouse device common for all mice
[    0.727968] rtc_cmos 00:05: RTC can wake from S4
[    0.728020] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    0.728058] rtc0: alarms up to one year, y3k, 242 bytes nvram, hpet irqs
[    0.728175] device-mapper: uevent: version 1.0.3
[    0.732365] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: [email]dm-devel@redhat.com[/email]
[    0.736283] device-mapper: multipath: version 1.1.1 loaded
[    0.736288] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.739203] EISA: Probing bus 0 at eisa.0
[    0.739207] EISA: Cannot allocate resource for mainboard
[    0.739210] Cannot allocate resource for EISA slot 1
[    0.739213] Cannot allocate resource for EISA slot 2
[    0.739215] Cannot allocate resource for EISA slot 3
[    0.739217] Cannot allocate resource for EISA slot 4
[    0.739219] Cannot allocate resource for EISA slot 5
[    0.739221] Cannot allocate resource for EISA slot 6
[    0.739224] Cannot allocate resource for EISA slot 7
[    0.739226] Cannot allocate resource for EISA slot 8
[    0.739228] EISA: Detected 0 cards.
[    0.744202] cpuidle: using governor ladder
[    0.744207] cpuidle: using governor menu
[    0.744493] TCP cubic registered
[    0.744621] NET: Registered protocol family 10
[    0.744984] lo: Disabled Privacy Extensions
[    0.745212] NET: Registered protocol family 17
[    0.745245] powernow-k8: Found 1 AMD Athlon(tm) 64 Processor 3500+ (1 cpu cores) (version 2.20.00)
[    0.745304] powernow-k8:    0 : fid 0xe (2200 MHz), vid 0x8
[    0.745307] powernow-k8:    1 : fid 0xc (2000 MHz), vid 0xa
[    0.745309] powernow-k8:    2 : fid 0xa (1800 MHz), vid 0xc
[    0.745312] powernow-k8:    3 : fid 0x2 (1000 MHz), vid 0x12
[    0.745353] Using IPI No-Shortcut mode
[    0.745456] PM: Resume from disk failed.
[    0.745468] registered taskstats version 1
[    0.745704]   Magic number: 11:41:172
[    0.745805] rtc_cmos 00:05: setting system clock to 2011-01-20 09:11:52 UTC (1295514712)
[    0.745808] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.745809] EDD information not available.
[    0.843443] Freeing initrd memory: 10508k freed
[    0.935492] isapnp: No Plug & Play device found
[    0.935504] Freeing unused kernel memory: 688k freed
[    0.935957] Write protecting the kernel text: 4936k
[    0.935986] Write protecting the kernel read-only data: 1976k
[    0.960207] udev[63]: starting version 163
[    1.000052] usb 1-6: new high speed USB device using ehci_hcd and address 4
[    1.166225] tg3.c:v3.110 (April 9, 2010)
[    1.166619] ACPI: PCI Interrupt Link [APC5] enabled at IRQ 16
[    1.166625]   alloc irq_desc for 16 on node -1
[    1.166627]   alloc kstat_irqs on node -1
[    1.166639] tg3 0000:02:00.0: PCI INT A -> Link[APC5] -> GSI 16 (level, low) -> IRQ 16
[    1.166648] tg3 0000:02:00.0: setting latency timer to 64
[    1.197001] sata_nv 0000:00:0e.0: version 3.5
[    1.197017] sata_nv 0000:00:0e.0: PCI INT A -> Link[APSI] -> GSI 23 (level, low) -> IRQ 23
[    1.197020] sata_nv 0000:00:0e.0: Using SWNCQ mode
[    1.197074] sata_nv 0000:00:0e.0: setting latency timer to 64
[    1.221374] scsi0 : sata_nv
[    1.228938] scsi1 : sata_nv
[    1.229184] ata1: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xe000 irq 23
[    1.229188] ata2: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xe008 irq 23
[    1.229229] sata_nv 0000:00:0f.0: PCI INT A -> Link[APSJ] -> GSI 22 (level, low) -> IRQ 22
[    1.229232] sata_nv 0000:00:0f.0: Using SWNCQ mode
[    1.229290] sata_nv 0000:00:0f.0: setting latency timer to 64
[    1.238913] scsi2 : sata_nv
[    1.239651] tg3 0000:02:00.0: eth0: Tigon3 [partno(BCM95754) rev b002] (PCI Express) MAC address 00:1a:a0:17:48:26
[    1.239655] tg3 0000:02:00.0: eth0: attached PHY is 5787 (10/100/1000Base-T Ethernet) (WireSpeed[1])
[    1.239659] tg3 0000:02:00.0: eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[    1.239662] tg3 0000:02:00.0: eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[    1.239850] scsi3 : sata_nv
[    1.240118] ata3: SATA max UDMA/133 cmd 0x9e0 ctl 0xbe0 bmdma 0xcc00 irq 22
[    1.240122] ata4: SATA max UDMA/133 cmd 0x960 ctl 0xb60 bmdma 0xcc08 irq 22
[    1.240525] Initializing USB Mass Storage driver...
[    1.240614] scsi4 : usb-storage 1-6:1.2
[    1.240726] usbcore: registered new interface driver usb-storage
[    1.240728] USB Mass Storage support registered.
[    1.244029] usb 1-8: new high speed USB device using ehci_hcd and address 5
[    1.384749] scsi5 : usb-storage 1-8:1.0
[    1.552022] ata3: SATA link down (SStatus 0 SControl 300)
[    1.688015] usb 2-2: new full speed USB device using ohci_hcd and address 2
[    1.696029] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.704784] ata1.00: ATA-8: WDC WD1602ABKS-18N8A0, 02.03B04, max UDMA/133
[    1.704787] ata1.00: 312500000 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    1.720776] ata1.00: configured for UDMA/133
[    1.720883] scsi 0:0:0:0: Direct-Access     ATA      WDC WD1602ABKS-1 02.0 PQ: 0 ANSI: 5
[    1.721032] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.722319] sd 0:0:0:0: [sda] 312500000 512-byte logical blocks: (160 GB/149 GiB)
[    1.722370] sd 0:0:0:0: [sda] Write Protect is off
[    1.722374] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.722395] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.722723]  sda: sda1 sda2 < sda5 sda6 sda7 >
[    1.760830] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.909581] hub 2-2:1.0: USB hub found
[    1.912555] hub 2-2:1.0: 3 ports detected
[    2.053444] EXT4-fs (sda6): INFO: recovery required on readonly filesystem
[    2.053449] EXT4-fs (sda6): write access will be enabled during recovery
[    2.188033] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.196203] ata2.00: ATAPI: HL-DT-ST DVD+/-RW GSA-T11N, A103, max UDMA/33
[    2.196215] ata2.00: applying bridge limits
[    2.212209] ata2.00: configured for UDMA/33
[    2.217763] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVD+-RW GSA-T11N A103 PQ: 0 ANSI: 5
[    2.228022] usb 2-5: new full speed USB device using ohci_hcd and address 3
[    2.229662] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    2.229678] Uniform CD-ROM driver Revision: 3.20
[    2.229790] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.229852] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.242245] scsi 4:0:0:0: Direct-Access     HP       Photosmart D7300 1.00 PQ: 0 ANSI: 2
[    2.242823] sd 4:0:0:0: Attached scsi generic sg2 type 0
[    2.244352] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[    2.386247] scsi 5:0:0:0: Direct-Access     Motorola A855             0001 PQ: 0 ANSI: 2
[    2.387381] sd 5:0:0:0: Attached scsi generic sg3 type 0
[    2.390990] sd 5:0:0:0: [sdc] Attached SCSI removable disk
[    2.537555] usb 2-2.1: new full speed USB device using ohci_hcd and address 4
[    2.540021] ata4: SATA link down (SStatus 0 SControl 300)
[    2.685677] usbcore: registered new interface driver hiddev
[    2.691200] input: Dell Dell USB Keyboard Hub as /devices/pci0000:00/0000:00:0b.0/usb2/2-2/2-2.1/2-2.1:1.0/input/input2
[    2.691358] generic-usb 0003:413C:2010.0001: input,hidraw0: USB HID v1.10 Keyboard [Dell Dell USB Keyboard Hub] on usb-0000:00:0b.0-2.1/input0
[    2.702133] input: Dell Dell USB Keyboard Hub as /devices/pci0000:00/0000:00:0b.0/usb2/2-2/2-2.1/2-2.1:1.1/input/input3
[    2.702566] generic-usb 0003:413C:2010.0002: input,hidraw1: USB HID v1.10 Device [Dell Dell USB Keyboard Hub] on usb-0000:00:0b.0-2.1/input1
[    2.702702] usbcore: registered new interface driver usbhid
[    2.702704] usbhid: USB HID core driver
[    2.737566] usb 2-2.3: new low speed USB device using ohci_hcd and address 5
[    2.859479] input: Logitech Optical USB Mouse as /devices/pci0000:00/0000:00:0b.0/usb2/2-2/2-2.3/2-2.3:1.0/input/input4
[    2.859972] generic-usb 0003:046D:C016.0003: input,hidraw2: USB HID v1.10 Mouse [Logitech Optical USB Mouse] on usb-0000:00:0b.0-2.3/input0
[    4.168664] EXT4-fs (sda6): orphan cleanup on readonly fs
[    4.168675] EXT4-fs (sda6): ext4_orphan_cleanup: deleting unreferenced inode 17651
[    4.168772] EXT4-fs (sda6): 1 orphan inode deleted
[    4.168776] EXT4-fs (sda6): recovery complete
[    4.548217] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
[    6.759878] Adding 1606464k swap on /dev/sda7.  Priority:-1 extents:1 across:1606464k 
[    7.219274] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
[    7.648152] udev[454]: starting version 163
[    7.981678] WARNING! power/level is deprecated; use power/control instead
[    8.861925] i2c i2c-0: nForce2 SMBus adapter at 0x1c00
[    8.861946] i2c i2c-1: nForce2 SMBus adapter at 0x1c40
[    8.872516] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[    8.886974] k8temp 0000:00:18.3: Temperature readouts might be wrong - check erratum #141
[    8.907248] parport_pc 00:09: reported by Plug and Play ACPI
[    8.907282] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
[    8.916545] Linux agpgart interface v0.103
[    8.921011] lp: driver loaded but no devices found
[    8.974394] ppdev: user-space parallel port driver
[    8.986423] dell-wmi-aio: No known WMI GUID found
[    9.004171] lp0: using parport0 (interrupt-driven).
[    9.467988] tpm_tis 00:02: 1.2 TPM (device-id 0x3203, rev-id 5)
[   10.158765] type=1400 audit(1295532721.908:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=646 comm="apparmor_parser"
[   10.159049] type=1400 audit(1295532721.908:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=646 comm="apparmor_parser"
[   10.159213] type=1400 audit(1295532721.908:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=646 comm="apparmor_parser"
[   10.159811] type=1400 audit(1295532721.908:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=647 comm="apparmor_parser"
[   10.160131] type=1400 audit(1295532721.912:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=647 comm="apparmor_parser"
[   10.160294] type=1400 audit(1295532721.912:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=647 comm="apparmor_parser"
[   10.199147] nvidia: module license 'NVIDIA' taints kernel.
[   10.199153] Disabling lock debugging due to kernel taint
[   11.508840] ACPI: PCI Interrupt Link [APC7] enabled at IRQ 16
[   11.508848] nvidia 0000:00:05.0: PCI INT A -> Link[APC7] -> GSI 16 (level, low) -> IRQ 16
[   11.508856] nvidia 0000:00:05.0: setting latency timer to 64
[   11.508861] vgaarb: device changed decodes: PCI:0000:00:05.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   11.509698] NVRM: loading NVIDIA UNIX x86 Kernel Module  260.19.06  Mon Sep 13 06:35:06 PDT 2010
[   11.597244] usblp0: USB Bidirectional printer dev 4 if 0 alt 0 proto 2 vid 0x03F0 pid 0xC702
[   11.597726] usbcore: registered new interface driver usblp
[   12.258496] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 23
[   12.258504] HDA Intel 0000:00:10.1: PCI INT B -> Link[AAZA] -> GSI 23 (level, low) -> IRQ 23
[   12.258508] hda_intel: Disable MSI for Nvidia chipset
[   12.258538] HDA Intel 0000:00:10.1: setting latency timer to 64
[   12.860324] input: HDA NVidia Line In at Ext Rear Jack as /devices/pci0000:00/0000:00:10.1/sound/card0/input5
[   12.860559] input: HDA NVidia Mic at Ext Front Jack as /devices/pci0000:00/0000:00:10.1/sound/card0/input6
[   12.860750] input: HDA NVidia Line Out at Ext Rear Jack as /devices/pci0000:00/0000:00:10.1/sound/card0/input7
[   12.860944] input: HDA NVidia HP Out at Ext Front Jack as /devices/pci0000:00/0000:00:10.1/sound/card0/input8
[   16.010853] type=1400 audit(1295532727.760:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=1061 comm="apparmor_parser"
[   16.011230] type=1400 audit(1295532727.760:9): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=1061 comm="apparmor_parser"
[   16.465582] type=1400 audit(1295532728.216:10): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=1091 comm="apparmor_parser"
[   16.468548] type=1400 audit(1295532728.220:11): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=1100 comm="apparmor_parser"
[   16.468837] type=1400 audit(1295532728.220:12): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1100 comm="apparmor_parser"
[   16.469003] type=1400 audit(1295532728.220:13): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1100 comm="apparmor_parser"
[   16.580226]   alloc irq_desc for 43 on node -1
[   16.580231]   alloc kstat_irqs on node -1
[   16.580243] tg3 0000:02:00.0: irq 43 for MSI/MSI-X
[   16.612686] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   16.841855] type=1400 audit(1295532728.592:14): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=1101 comm="apparmor_parser"
[   16.845737] type=1400 audit(1295532728.596:15): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=1101 comm="apparmor_parser"
[   16.848133] type=1400 audit(1295532728.600:16): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-thumbnailer" pid=1101 comm="apparmor_parser"
[   17.006410] type=1400 audit(1295532728.756:17): apparmor="STATUS" operation="profile_load" name="/usr/bin/freshclam" pid=1174 comm="apparmor_parser"
[   19.107275] usb 1-6: usbfs: interface 0 claimed by usblp while 'usb' sets config #1
[   19.750544] tg3 0000:02:00.0: eth0: Link is up at 1000 Mbps, full duplex
[   19.750548] tg3 0000:02:00.0: eth0: Flow control is off for TX and off for RX
[   19.932978] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   24.847858] RPC: Registered udp transport module.
[   24.847862] RPC: Registered tcp transport module.
[   24.847864] RPC: Registered tcp NFSv4.1 backchannel transport module.
[   25.289445] Installing knfsd (copyright (C) 1996 [email]okir@monad.swb.de[/email]).
[   25.612672] svc: failed to register lockdv1 RPC service (errno 97).
[   25.615684] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[   25.625853] NFSD: starting 90-second grace period
[   30.096025] eth0: no IPv6 routers present
[   33.541902] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro,commit=0
[   95.004018] Clocksource tsc unstable (delta = -93750390 ns)
[ 2667.223376] usb 1-8: USB disconnect, address 5
[ 8935.780030] usb 1-8: new high speed USB device using ehci_hcd and address 6
[ 8935.923574] scsi6 : usb-storage 1-8:1.0
[ 8936.930264] scsi 6:0:0:0: Direct-Access     Motorola A855             0001 PQ: 0 ANSI: 2
[ 8936.930711] sd 6:0:0:0: Attached scsi generic sg3 type 0
[ 8936.943865] sd 6:0:0:0: [sdc] Attached SCSI removable disk
[14781.432139] usb 1-8: USB disconnect, address 6
[14781.712096] hub 1-0:1.0: unable to enumerate USB device on port 8
[14802.716058] usb 1-8: new high speed USB device using ehci_hcd and address 8
[14802.867486] scsi7 : usb-storage 1-8:1.0
[14803.880164] scsi 7:0:0:0: Direct-Access     Motorola A855             0001 PQ: 0 ANSI: 2
[14803.884490] sd 7:0:0:0: Attached scsi generic sg3 type 0
[14803.905642] sd 7:0:0:0: [sdc] Attached SCSI removable disk
[22948.435907] usblp0: removed
[28680.465651] usb 1-8: USB disconnect, address 8
[82525.956043] usb 1-8: new high speed USB device using ehci_hcd and address 9
[82526.097894] scsi8 : usb-storage 1-8:1.0
[82527.098317] scsi 8:0:0:0: Direct-Access     Motorola A855             0001 PQ: 0 ANSI: 2
[82527.099506] sd 8:0:0:0: Attached scsi generic sg3 type 0
[82527.117382] sd 8:0:0:0: [sdc] Attached SCSI removable disk
```

---

### Post by oldfred on 2011-01-21
Is this an overclocked system? Large time jumps between these entries. Not normal.

[   33.541902] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro,commit=0
[   95.004018] [COLOR=Red]Clocksource tsc unstable [/COLOR](delta = -93750390 ns)
[ 2667.223376] usb 1-8: USB disconnect, address 5
[ 8935.780030] usb 1-8: new high speed USB device using ehci_hcd and address 6

---

### Post by haydemon on 2011-01-21
What do you mean by "overclocked?":confused:

---

### Post by oldfred on 2011-01-21
Did you go into the BIOS and boost the speeds. Some vendors even do it to make their systems look better. 

May be something else in BIOS settings? Or system is starting to fail as it cannot hold settings.

---

### Post by haydemon on 2011-01-21
I haven't done anything to the BIOS. What should I look for? What could be possible causes for the system to fail (not hold settings)?

---

### Post by oldfred on 2011-01-21
If not a setting it might be power supply or capacitors on motherboard.

Have you run memory tests to see if memory is ok? Does windows boot, as that might say it is a setting & not hardware.

---

### Post by haydemon on 2011-01-21
I haven't run memory tests lately. Windows boots with no problems.

---

### Post by mikewhatever on 2011-01-21
Looks like something is wrong with the file system on sda6:

```
[ 2.053444] EXT4-fs (sda6): INFO: recovery required on readonly filesystem
[ 2.053449] EXT4-fs (sda6): write access will be enabled during recovery

```
It could be trying to do the recovery, which might be taking the time. What's on sda6?

---

### Post by haydemon on 2011-01-24
ext4

---

### Post by oldfred on 2011-01-24
I would try filechecks:

From liveCD so everything is unmounted,swap off if necessary, change sda6 to your partition(s)
sudo e2fsck -C0 -p -f -v /dev/sda6
if errors:
sudo e2fsck -f -y -v /dev/sda6

---

### Post by haydemon on 2011-01-24
Please bear with me. So, to clarify:
a) without rebooting, insert live CD
b) open command line
c) sudo e2fsck -C0 -p -f -v /dev/sda6
d) if errors, sudo e2fsck -f -y -v /dev/sda6

Is that correct? What do you mean by "swap off if necessary?"

---

### Post by oldfred on 2011-01-24
The extended partition is one container and counts as one partition. So any logical partition mounted in the extended mounts the entire extended partition. Many liveCDs including Ubuntu use the swap to speed up liveCD, if it sees a swap partition. So you have to in gparted right click and click on the swap off for the swap partition.

---

### Post by haydemon on 2011-01-26
I haven't done anything yet. BUT: yesterday I was prompted to restart system due to the latest update, and when I did, the problem wasn't there anymore (meaning, it booted normally, without extraordinary delays).

I'm not sure if I should mark this thread SOLVED, because I didn't do anything, even tho the problem seems to have disappeared, but I don't know why. Any thoughts?

---

