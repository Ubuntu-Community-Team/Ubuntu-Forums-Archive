---
title: "hp tx2 touchscreen laggy"
date: 2010-10-20
forum: New to Ubuntu
---

### Post by ihlinuxdude on 2010-10-20
Hi all! 
I have an hp tx2 1020us I've recently updated to U 10.10.  I was under the impression that it would enable the multitouch capability, it hasn't.  Should it have?      
Also the touchscreen has become more laggy or sticky, it's most notice able when using the onboard on screen keyboard, the   cursor gets stuck on a key and no matter where you touch it stays stuck on the previous key.
like thisssst jst sticks and mmmes it veryyynnoying to use. :confused:
any ideas?
Thanks iin advance

---

### Post by Ayuthia on 2010-10-21
The only place where multitouch is visible is in the Unity desktop.  This comes as the default desktop for the Ubuntu Netbook Edition.  The other requirement for multitouch here is that it will need to have the firmware bundle from 2.184 or 2.239 for HP (for Win 7 only).  Those are the only ones right now that will register correctly for multitouch.  If you want to see if the gestures work, you can install utouch and then run (from the Terminal):
```
gesturetest 0 0 0xffffffff
```

As for the laggy problem, do you know which firmware you are using (and if it came from Vista or Win 7)?

Which on screen keyboard are you using?  I can try to see if I can duplicate the issue.

One other question, do you know if you installed the fglrx graphics driver from Hardware Drivers or are you using what came with the default installation?

---

### Post by lawrencegoodman on 2010-10-25
I have the TX 2 and had the same problem. I had to go back to 10.04. My dmesg output is below if it is any help. I tried to do it when the laggy/sticky problem occurred. 


> 0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.36-020636rc7-generic (root@zinc) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #201010070908 SMP Thu Oct 7 10:21:05 UTC 2010
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000afb8f000 (usable)
[    0.000000]  BIOS-e820: 00000000afb8f000 - 00000000afc3c000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000afc3c000 - 00000000afd70000 (usable)
[    0.000000]  BIOS-e820: 00000000afd70000 - 00000000afdbf000 (reserved)
[    0.000000]  BIOS-e820: 00000000afdbf000 - 00000000afe57000 (usable)
[    0.000000]  BIOS-e820: 00000000afe57000 - 00000000afebf000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000afebf000 - 00000000afee9000 (usable)
[    0.000000]  BIOS-e820: 00000000afee9000 - 00000000afeff000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000afeff000 - 00000000aff00000 (usable)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000e4000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000140000000 (usable)
[    0.000000] Notice: NX (Execute Disable) protection cannot be enabled: non-PAE kernel!
[    0.000000] DMI 2.4 present.
[    0.000000] e820 update range: 0000000000000000 - 0000000000001000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0xaff00 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-FFFFF write-through
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 00FFF00000 mask FFFFF00000 write-protect
[    0.000000]   1 base 0000000000 mask FF80000000 write-back
[    0.000000]   2 base 0080000000 mask FFE0000000 write-back
[    0.000000]   3 base 00A0000000 mask FFF0000000 write-back
[    0.000000]   4 base 0100000000 mask FFC0000000 write-back
[    0.000000]   5 disabled
[    0.000000]   6 disabled                                                                                                        
[    0.000000]   7 disabled                                                                                                        
[    0.000000] TOM2: 0000000140000000 aka 5120M                                                                                    
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106                                                    
[    0.000000] e820 update range: 0000000000002000 - 0000000000010000 (usable) ==> (reserved)                                      
[    0.000000] Scanning 1 areas for low memory corruption                                                                          
[    0.000000] modified physical RAM map:                                                                                          
[    0.000000]  modified: 0000000000000000 - 0000000000001000 (reserved)                                                           
[    0.000000]  modified: 0000000000001000 - 0000000000002000 (usable)                                                             
[    0.000000]  modified: 0000000000002000 - 0000000000010000 (reserved)                                                           
[    0.000000]  modified: 0000000000010000 - 000000000009fc00 (usable)                                                             
[    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)                                                           
[    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)                                                           
[    0.000000]  modified: 0000000000100000 - 00000000afb8f000 (usable)                                                             
[    0.000000]  modified: 00000000afb8f000 - 00000000afc3c000 (ACPI NVS)                                                           
[    0.000000]  modified: 00000000afc3c000 - 00000000afd70000 (usable)                                                             
[    0.000000]  modified: 00000000afd70000 - 00000000afdbf000 (reserved)                                                           
[    0.000000]  modified: 00000000afdbf000 - 00000000afe57000 (usable)                                                             
[    0.000000]  modified: 00000000afe57000 - 00000000afebf000 (ACPI NVS)                                                           
[    0.000000]  modified: 00000000afebf000 - 00000000afee9000 (usable)                                                             
[    0.000000]  modified: 00000000afee9000 - 00000000afeff000 (ACPI data)                                                          
[    0.000000]  modified: 00000000afeff000 - 00000000aff00000 (usable)
[    0.000000]  modified: 00000000e0000000 - 00000000e4000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000]  modified: 0000000100000000 - 0000000140000000 (usable)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 15000-1a000
[    0.000000] RAMDISK: 37583000 - 37ff0000
[    0.000000] Allocated new RAMDISK: 009d8000 - 01444fef
[    0.000000] Move RAMDISK from 0000000037583000 - 0000000037feffee to 009d8000 - 01444fee
[    0.000000] ACPI: RSDP 000fe020 00024 (v02 HP    )
[    0.000000] ACPI: XSDT afefe120 00064 (v01 HPQOEM SLIC-MPC 00000003      01000013)
[    0.000000] ACPI: FACP afefd000 000F4 (v04 HP     3045     00000003 MSFT 0100000D)
[    0.000000] ACPI: DSDT afef1000 08BC6 (v01 HP     3045     F0000000 INTL 20051117)
[    0.000000] ACPI: FACS afe60000 00040
[    0.000000] ACPI: HPET afefc000 00038 (v01 HP     3045     00000001 MSFT 000F4240)
[    0.000000] ACPI: APIC afefb000 00084 (v02 HP     3045     00000001 TFSM 000F4240)
[    0.000000] ACPI: MCFG afefa000 0003C (v01 HP     3045     00000001 TFSM 000F4240)
[    0.000000] ACPI: BOOT afef0000 00028 (v01 HP     3045     00000001    ? 00000001)
[    0.000000] ACPI: SLIC afeef000 00176 (v01 HPQOEM SLIC-MPC 06040000  LTP 00000001)
[    0.000000] ACPI: SSDT afeee000 00386 (v01 AMD    PowerNow 00000001 AMD  00000001)
[    0.000000] ACPI: SRAT afeed000 000A0 (v03 AMD    AMD CRB  00000001 AMD  00000001)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 1927MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000001 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x000aff00
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[7] active PFN ranges
[    0.000000]     0: 0x00000001 -> 0x00000002
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x000afb8f
[    0.000000]     0: 0x000afc3c -> 0x000afd70
[    0.000000]     0: 0x000afdbf -> 0x000afe57
[    0.000000]     0: 0x000afebf -> 0x000afee9
[    0.000000]     0: 0x000afeff -> 0x000aff00
[    0.000000] On node 0 totalpages: 720150
[    0.000000] free_area_init_node: node 0, pgdat c0820bc0, node_mem_map c1446020
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3952 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 3855 pages used for memmap
[    0.000000]   HighMem zone: 489081 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x1002a201 base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] early_res array is doubled to 64 at [16000 - 167ff]
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000010000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at aff00000 (gap: aff00000:30100000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @c2c00000 s32896 r0 d24448 u1048576
[    0.000000] pcpu-alloc: s32896 r0 d24448 u1048576 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 714519
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.36-020636rc7-generic root=UUID=161977ea-9a37-4d09-820b-c79169681c71 ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 14412780 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Subtract (55 early reservations)
[    0.000000]   #1 [0000001000 - 0000002000]   EX TRAMPOLINE
[    0.000000]   #2 [0000100000 - 00009d3824]   TEXT DATA BSS
[    0.000000]   #3 [000009fc00 - 0000100000]   BIOS reserved
[    0.000000]   #4 [00009d4000 - 00009d7194]             BRK
[    0.000000]   #5 [0000010000 - 0000011000]      TRAMPOLINE
[    0.000000]   #6 [0000011000 - 0000015000]     ACPI WAKEUP
[    0.000000]   #7 [0000015000 - 0000016000]         PGTABLE
[    0.000000]   #8 [00009d8000 - 0001445000]     NEW RAMDISK
[    0.000000]   #9 [0001445000 - 0001446000]         BOOTMEM
[    0.000000]   #10 [0001446000 - 0002a46000]         BOOTMEM
[    0.000000]   #11 [0002a46000 - 0002a46004]         BOOTMEM
[    0.000000]   #12 [0002a46040 - 0002a46100]         BOOTMEM
[    0.000000]   #13 [0002a46100 - 0002a46154]         BOOTMEM
[    0.000000]   #14 [0002a46180 - 0002a49180]         BOOTMEM
[    0.000000]   #15 [0002a49180 - 0002a49238]         BOOTMEM
[    0.000000]   #16 [0002a49240 - 0002a4f240]         BOOTMEM
[    0.000000]   #17 [0002a4f240 - 0002a4f265]         BOOTMEM
[    0.000000]   #18 [0002a4f280 - 0002a4f2a7]         BOOTMEM
[    0.000000]   #19 [0002a4f2c0 - 0002a4f4f0]         BOOTMEM
[    0.000000]   #20 [0002a4f500 - 0002a4f540]         BOOTMEM
[    0.000000]   #21 [0002a4f540 - 0002a4f580]         BOOTMEM
[    0.000000]   #22 [0002a4f580 - 0002a4f5c0]         BOOTMEM
[    0.000000]   #23 [0002a4f5c0 - 0002a4f600]         BOOTMEM
[    0.000000]   #24 [0002a4f600 - 0002a4f640]         BOOTMEM
[    0.000000]   #25 [0002a4f640 - 0002a4f680]         BOOTMEM
[    0.000000]   #26 [0002a4f680 - 0002a4f6c0]         BOOTMEM
[    0.000000]   #27 [0002a4f6c0 - 0002a4f700]         BOOTMEM
[    0.000000]   #28 [0002a4f700 - 0002a4f740]         BOOTMEM
[    0.000000]   #29 [0002a4f740 - 0002a4f780]         BOOTMEM
[    0.000000]   #30 [0002a4f780 - 0002a4f7c0]         BOOTMEM
[    0.000000]   #31 [0002a4f7c0 - 0002a4f800]         BOOTMEM
[    0.000000]   #32 [0002a4f800 - 0002a4f840]         BOOTMEM
[    0.000000]   #33 [0002a4f840 - 0002a4f880]         BOOTMEM
[    0.000000]   #34 [0002a4f880 - 0002a4f8c0]         BOOTMEM
[    0.000000]   #35 [0002a4f8c0 - 0002a4f900]         BOOTMEM
[    0.000000]   #36 [0002a4f900 - 0002a4f940]         BOOTMEM
[    0.000000]   #37 [0002a4f940 - 0002a4f950]         BOOTMEM
[    0.000000]   #38 [0002a4f980 - 0002a4f990]         BOOTMEM
[    0.000000]   #39 [0002a4f9c0 - 0002a4fa31]         BOOTMEM
[    0.000000]   #40 [0002a4fa40 - 0002a4fab1]         BOOTMEM
[    0.000000]   #41 [0002c00000 - 0002c0e000]         BOOTMEM
[    0.000000]   #42 [0002d00000 - 0002d0e000]         BOOTMEM
[    0.000000]   #43 [0002e00000 - 0002e0e000]         BOOTMEM
[    0.000000]   #44 [0002f00000 - 0002f0e000]         BOOTMEM
[    0.000000]   #45 [0002a51ac0 - 0002a51ac4]         BOOTMEM
[    0.000000]   #46 [0002a51b00 - 0002a51b04]         BOOTMEM
[    0.000000]   #47 [0002a51b40 - 0002a51b50]         BOOTMEM
[    0.000000]   #48 [0002a51b80 - 0002a51b90]         BOOTMEM
[    0.000000]   #49 [0002a51bc0 - 0002a51c60]         BOOTMEM
[    0.000000]   #50 [0002a51c80 - 0002a51cc8]         BOOTMEM
[    0.000000]   #51 [0002a51d00 - 0002a55d00]         BOOTMEM
[    0.000000]   #52 [0002a55d00 - 0002ad5d00]         BOOTMEM
[    0.000000]   #53 [0002ad5d00 - 0002b15d00]         BOOTMEM
[    0.000000]   #54 [0002f0e000 - 0003cccbec]         BOOTMEM
[    0.000000] Initializing HighMem for node 0 (000377fe:000aff00)
[    0.000000] Memory: 2823180k/2882560k available (4999k kernel code, 57420k reserved, 2399k data, 740k init, 1971744k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc083a000 - 0xc08f3000   ( 740 kB)
[    0.000000]       .data : 0xc05e1f1f - 0xc0839b28   (2399 kB)
[    0.000000]       .text : 0xc0100000 - 0xc05e1f1f   (4999 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]  RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]  RCU-based detection of stalled CPUs is disabled.
[    0.000000]  Verbose stalled-CPUs detection is disabled.
[    0.000000] NR_IRQS:2304 nr_irqs:712
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2300.259 MHz processor.
[    0.004011] Calibrating delay loop (skipped), value calculated using timer frequency.. 4600.51 BogoMIPS (lpj=9201036)
[    0.004024] pid_max: default: 32768 minimum: 301
[    0.004086] Security Framework initialized
[    0.008029] AppArmor: AppArmor initialized
[    0.008144] Mount-cache hash table entries: 512
[    0.008453] Initializing cgroup subsys ns
[    0.008461] Initializing cgroup subsys cpuacct
[    0.008473] Initializing cgroup subsys memory
[    0.008495] Initializing cgroup subsys devices
[    0.008502] Initializing cgroup subsys freezer
[    0.008508] Initializing cgroup subsys net_cls
[    0.008571] CPU: Physical Processor ID: 0
[    0.008577] CPU: Processor Core ID: 0
[    0.008584] mce: CPU supports 5 MCE banks
[    0.008611] Performance Events: AMD PMU driver.
[    0.008628] ... version:                0
[    0.008634] ... bit width:              48
[    0.008639] ... generic registers:      4
[    0.008644] ... value mask:             0000ffffffffffff
[    0.008650] ... max period:             00007fffffffffff
[    0.008656] ... fixed-purpose events:   0
[    0.008661] ... event mask:             000000000000000f
[    0.015973] ACPI: Core revision 20100702
[    0.036045] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.036066] ftrace: allocating 26008 entries in 51 pages
[    0.040129] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.040506] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.080490] CPU0: AMD Turion(tm) X2 Ultra Dual-Core Mobile ZM-85 stepping 01
[    0.084000] Booting Node   0, Processors  #1
[    0.008000] Initializing CPU#1
[    0.172000] TSC synchronization [CPU#0 -> CPU#1]:
[    0.172000] Measured 228409446 cycles TSC warp between CPUs, turning off TSC clock.
[    0.172000] Marking TSC unstable due to check_tsc_sync_source failed
[    0.172017] Brought up 2 CPUs
[    0.172022] Total of 2 processors activated (9189.36 BogoMIPS).
[    0.172431] devtmpfs: initialized
[    0.172946] regulator: core version 0.5
[    0.173006] Time: 15:10:21  Date: 10/14/10
[    0.173049] NET: Registered protocol family 16
[    0.173179] EISA bus registered
[    0.173190] TOM: 00000000c0000000 aka 3072M
[    0.173193] Fam 10h mmconf [e0000000, e0ffffff]
[    0.173202] TOM2: 0000000140000000 aka 5120M
[    0.173213] ACPI: bus type pci registered
[    0.173328] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xe0000000-0xe3ffffff] (base 0xe0000000)
[    0.173332] PCI: MMCONFIG at [mem 0xe0000000-0xe3ffffff] reserved in E820
[    0.173334] PCI: Using MMCONFIG for extended config space
[    0.173336] PCI: Using configuration type 1 for base access
[    0.173361] mtrr: your CPUs had inconsistent fixed MTRR settings
[    0.173362] mtrr: probably your BIOS does not setup all CPUs.
[    0.173364] mtrr: corrected configuration.
[    0.174265] bio: create slab <bio-0> at 0
[    0.177026] ACPI: EC: Look up EC in DSDT
[    0.178338] ACPI: Executed 1 blocks of module-level executable AML code
[    0.181530] ACPI: BIOS _OSI(Linux) query ignored
[    0.184059] ACPI: Interpreter enabled
[    0.184064] ACPI: (supports S0 S3 S4 S5)
[    0.184086] ACPI: Using IOAPIC for interrupt routing
[    0.189708] ACPI: EC: GPE = 0x3, I/O: command/status = 0x66, data = 0x62
[    0.189708] ACPI: No dock devices found.
[    0.189708] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.189708] \_SB_.PCI0:_OSC request failed
[    0.189708] _OSC request data:1 8 1f 
[    0.189708] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.193044] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    0.193048] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    0.193051] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.193054] pci_root PNP0A08:00: host bridge window [mem 0x000c0000-0x000c3fff]
[    0.193057] pci_root PNP0A08:00: host bridge window [mem 0x000c4000-0x000c7fff]
[    0.193060] pci_root PNP0A08:00: host bridge window [mem 0x000c8000-0x000cbfff]
[    0.193064] pci_root PNP0A08:00: address space collision: host bridge window [mem 0x000cc000-0x000cffff] conflicts with Video ROM [mem 0x000c0000-0x000cedff]
[    0.193148] pci_root PNP0A08:00: host bridge window [mem 0x000d0000-0x000d3fff]
[    0.193151] pci_root PNP0A08:00: host bridge window [mem 0x000d4000-0x000d7fff]
[    0.193154] pci_root PNP0A08:00: host bridge window [mem 0x000d8000-0x000dbfff]
[    0.193157] pci_root PNP0A08:00: host bridge window [mem 0x000dc000-0x000dffff]
[    0.193160] pci_root PNP0A08:00: host bridge window [mem 0x000e0000-0x000e3fff]
[    0.193163] pci_root PNP0A08:00: host bridge window [mem 0x000e4000-0x000e7fff]
[    0.193166] pci_root PNP0A08:00: host bridge window [mem 0x000e8000-0x000ebfff]
[    0.193169] pci_root PNP0A08:00: host bridge window [mem 0x000ec000-0x000effff]
[    0.193172] pci_root PNP0A08:00: host bridge window [mem 0xc0000000-0xdfffffff]
[    0.193175] pci_root PNP0A08:00: host bridge window [mem 0xe4000000-0xffffffff]
[    0.193373] pci 0000:00:04.0: PME# supported from D0 D3hot D3cold
[    0.193377] pci 0000:00:04.0: PME# disabled
[    0.193434] pci 0000:00:05.0: PME# supported from D0 D3hot D3cold
[    0.193437] pci 0000:00:05.0: PME# disabled
[    0.193493] pci 0000:00:06.0: PME# supported from D0 D3hot D3cold
[    0.193497] pci 0000:00:06.0: PME# disabled
[    0.193558] pci 0000:00:11.0: reg 10: [io  0x6038-0x603f]
[    0.193571] pci 0000:00:11.0: reg 14: [io  0x604c-0x604f]
[    0.193583] pci 0000:00:11.0: reg 18: [io  0x6030-0x6037]
[    0.193595] pci 0000:00:11.0: reg 1c: [io  0x6048-0x604b]
[    0.193607] pci 0000:00:11.0: reg 20: [io  0x6010-0x601f]
[    0.193619] pci 0000:00:11.0: reg 24: [mem 0xd2409000-0xd24093ff]
[    0.193688] pci 0000:00:12.0: reg 10: [mem 0xd2408000-0xd2408fff]
[    0.193779] pci 0000:00:12.1: reg 10: [mem 0xd2407000-0xd2407fff]
[    0.193779] pci 0000:00:12.2: reg 10: [mem 0xd2409500-0xd24095ff]
[    0.193779] pci 0000:00:12.2: supports D1 D2
[    0.193779] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
[    0.193779] pci 0000:00:12.2: PME# disabled
[    0.193779] pci 0000:00:13.0: reg 10: [mem 0xd2406000-0xd2406fff]
[    0.193779] pci 0000:00:13.1: reg 10: [mem 0xd2405000-0xd2405fff]
[    0.196017] pci 0000:00:13.2: reg 10: [mem 0xd2409400-0xd24094ff]
[    0.196049] pci 0000:00:13.2: supports D1 D2
[    0.196055] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
[    0.196061] pci 0000:00:13.2: PME# disabled
[    0.196229] pci 0000:00:14.1: reg 10: [io  0x0000-0x0007]
[    0.196241] pci 0000:00:14.1: reg 14: [io  0x0000-0x0003]
[    0.196253] pci 0000:00:14.1: reg 18: [io  0x0000-0x0007]
[    0.196265] pci 0000:00:14.1: reg 1c: [io  0x0000-0x0003]
[    0.196277] pci 0000:00:14.1: reg 20: [io  0x6000-0x600f]
[    0.196369] pci 0000:00:14.2: reg 10: [mem 0xd2400000-0xd2403fff 64bit]
[    0.196439] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
[    0.196444] pci 0000:00:14.2: PME# disabled
[    0.196609] pci 0000:00:14.5: reg 10: [mem 0xd2404000-0xd2404fff]
[    0.196905] pci 0000:01:05.0: reg 10: [mem 0xc0000000-0xcfffffff pref]
[    0.196912] pci 0000:01:05.0: reg 14: [io  0x5000-0x50ff]
[    0.196919] pci 0000:01:05.0: reg 18: [mem 0xd2300000-0xd230ffff]
[    0.196935] pci 0000:01:05.0: reg 24: [mem 0xd2200000-0xd22fffff]
[    0.196954] pci 0000:01:05.0: supports D1 D2
[    0.197036] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.197041] pci 0000:00:01.0:   bridge window [io  0x5000-0x5fff]
[    0.197046] pci 0000:00:01.0:   bridge window [mem 0xd2200000-0xd23fffff]
[    0.197051] pci 0000:00:01.0:   bridge window [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.197088] pci 0000:00:04.0: PCI bridge to [bus 02-07]
[    0.197093] pci 0000:00:04.0:   bridge window [io  0x3000-0x4fff]
[    0.197097] pci 0000:00:04.0:   bridge window [mem 0xd1200000-0xd21fffff]
[    0.197102] pci 0000:00:04.0:   bridge window [mem 0xd0000000-0xd0ffffff 64bit pref]
[    0.197179] pci 0000:08:00.0: reg 10: [mem 0xd1100000-0xd1103fff 64bit]
[    0.197263] pci 0000:08:00.0: supports D1 D2
[    0.208025] pci 0000:00:05.0: PCI bridge to [bus 08-08]
[    0.208031] pci 0000:00:05.0:   bridge window [io  0xfffff000-0x0000] (disabled)
[    0.208035] pci 0000:00:05.0:   bridge window [mem 0xd1100000-0xd11fffff]
[    0.208041] pci 0000:00:05.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.208108] pci 0000:09:00.0: reg 10: [io  0x2000-0x20ff]
[    0.208134] pci 0000:09:00.0: reg 18: [mem 0xd1010000-0xd1010fff 64bit pref]
[    0.208151] pci 0000:09:00.0: reg 20: [mem 0xd1000000-0xd100ffff 64bit pref]
[    0.208163] pci 0000:09:00.0: reg 30: [mem 0xffff0000-0xffffffff pref]
[    0.208198] pci 0000:09:00.0: supports D1 D2
[    0.208201] pci 0000:09:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.208206] pci 0000:09:00.0: PME# disabled
[    0.216013] pci 0000:00:06.0: PCI bridge to [bus 09-09]
[    0.216018] pci 0000:00:06.0:   bridge window [io  0x2000-0x2fff]
[    0.216022] pci 0000:00:06.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.216028] pci 0000:00:06.0:   bridge window [mem 0xd1000000-0xd10fffff 64bit pref]
[    0.216101] pci 0000:00:14.4: PCI bridge to [bus 80-8f] (subtractive decode)
[    0.216107] pci 0000:00:14.4:   bridge window [io  0x1000-0x1fff]
[    0.216112] pci 0000:00:14.4:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.216118] pci 0000:00:14.4:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.216121] pci 0000:00:14.4:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.216124] pci 0000:00:14.4:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.216127] pci 0000:00:14.4:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.216130] pci 0000:00:14.4:   bridge window [mem 0x000c0000-0x000c3fff] (subtractive decode)
[    0.216133] pci 0000:00:14.4:   bridge window [mem 0x000c4000-0x000c7fff] (subtractive decode)
[    0.216136] pci 0000:00:14.4:   bridge window [mem 0x000c8000-0x000cbfff] (subtractive decode)
[    0.216140] pci 0000:00:14.4:   bridge window [mem 0x000d0000-0x000d3fff] (subtractive decode)
[    0.216143] pci 0000:00:14.4:   bridge window [mem 0x000d4000-0x000d7fff] (subtractive decode)
[    0.216146] pci 0000:00:14.4:   bridge window [mem 0x000d8000-0x000dbfff] (subtractive decode)
[    0.216149] pci 0000:00:14.4:   bridge window [mem 0x000dc000-0x000dffff] (subtractive decode)
[    0.216152] pci 0000:00:14.4:   bridge window [mem 0x000e0000-0x000e3fff] (subtractive decode)
[    0.216155] pci 0000:00:14.4:   bridge window [mem 0x000e4000-0x000e7fff] (subtractive decode)
[    0.216158] pci 0000:00:14.4:   bridge window [mem 0x000e8000-0x000ebfff] (subtractive decode)
[    0.216161] pci 0000:00:14.4:   bridge window [mem 0x000ec000-0x000effff] (subtractive decode)
[    0.216164] pci 0000:00:14.4:   bridge window [mem 0xc0000000-0xdfffffff] (subtractive decode)
[    0.216167] pci 0000:00:14.4:   bridge window [mem 0xe4000000-0xffffffff] (subtractive decode)
[    0.216218] pci_bus 0000:00: on NUMA node 0
[    0.216227] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.216502] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    0.216557] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB4_._PRT]
[    0.216619] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB5_._PRT]
[    0.216674] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB6_._PRT]
[    0.216760] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[    0.216914] \_SB_.PCI0:_OSC request failed
[    0.216915] _OSC request data:1 1f 1f 
[    0.223108] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.223168] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.223225] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.223283] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.223340] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.223397] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.223457] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.223515] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.223541] HEST: Table is not found!
[    0.223645] vgaarb: device added: PCI:0000:01:05.0,decodes=io+mem,owns=io+mem,locks=none
[    0.223648] vgaarb: loaded
[    0.223816] SCSI subsystem initialized
[    0.224068] libata version 3.00 loaded.
[    0.224173] usbcore: registered new interface driver usbfs
[    0.224198] usbcore: registered new interface driver hub
[    0.224210] usbcore: registered new device driver usb
[    0.224210] ACPI: WMI: Mapper loaded
[    0.224210] PCI: Using ACPI for IRQ routing
[    0.224210] PCI: pci_cache_line_size set to 64 bytes
[    0.224306] reserve RAM buffer: 0000000000002000 - 000000000000ffff 
[    0.224309] reserve RAM buffer: 000000000009fc00 - 000000000009ffff 
[    0.224311] reserve RAM buffer: 00000000afb8f000 - 00000000afffffff 
[    0.224315] reserve RAM buffer: 00000000afd70000 - 00000000afffffff 
[    0.224318] reserve RAM buffer: 00000000afe57000 - 00000000afffffff 
[    0.224321] reserve RAM buffer: 00000000afee9000 - 00000000afffffff 
[    0.224323] reserve RAM buffer: 00000000aff00000 - 00000000afffffff 
[    0.224426] NetLabel: Initializing
[    0.224428] NetLabel:  domain hash size = 128
[    0.224430] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.224442] NetLabel:  unlabeled traffic allowed by default
[    0.224479] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.224484] hpet0: 4 comparators, 32-bit 14.318180 MHz counter
[    0.226510] Switching to clocksource hpet
[    0.231566] AppArmor: AppArmor Filesystem Enabled
[    0.231585] pnp: PnP ACPI init
[    0.231608] ACPI: bus type pnp registered
[    0.233885] pnp: PnP ACPI: found 12 devices
[    0.233888] ACPI: ACPI bus type pnp unregistered
[    0.233891] PnPBIOS: Disabled by ACPI PNP
[    0.233905] system 00:01: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.233909] system 00:01: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.233917] system 00:09: [io  0x0400-0x04cf] has been reserved
[    0.233920] system 00:09: [io  0x04d0-0x04d1] has been reserved
[    0.233923] system 00:09: [io  0x04d6] has been reserved
[    0.233926] system 00:09: [io  0x0680-0x06ff] has been reserved
[    0.233929] system 00:09: [io  0x077a] has been reserved
[    0.233932] system 00:09: [io  0x0c00-0x0c01] has been reserved
[    0.233935] system 00:09: [io  0x0c14] has been reserved
[    0.233937] system 00:09: [io  0x0c50-0x0c52] has been reserved
[    0.233940] system 00:09: [io  0x0c6c] has been reserved
[    0.233943] system 00:09: [io  0x0c6f] has been reserved
[    0.233946] system 00:09: [io  0x0cd0-0x0cdb] has been reserved
[    0.233951] system 00:0a: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.233955] system 00:0a: [mem 0xfff00000-0xffffffff] has been reserved
[    0.270267] pci 0000:09:00.0: no compatible bridge window for [mem 0xffff0000-0xffffffff pref]
[    0.270302] pci 0000:00:06.0: BAR 14: assigned [mem 0xd2500000-0xd25fffff]
[    0.270305] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.270309] pci 0000:00:01.0:   bridge window [io  0x5000-0x5fff]
[    0.270314] pci 0000:00:01.0:   bridge window [mem 0xd2200000-0xd23fffff]
[    0.270318] pci 0000:00:01.0:   bridge window [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.270323] pci 0000:00:04.0: PCI bridge to [bus 02-07]
[    0.270326] pci 0000:00:04.0:   bridge window [io  0x3000-0x4fff]
[    0.270331] pci 0000:00:04.0:   bridge window [mem 0xd1200000-0xd21fffff]
[    0.270335] pci 0000:00:04.0:   bridge window [mem 0xd0000000-0xd0ffffff 64bit pref]
[    0.270340] pci 0000:00:05.0: PCI bridge to [bus 08-08]
[    0.270342] pci 0000:00:05.0:   bridge window [io  disabled]
[    0.270346] pci 0000:00:05.0:   bridge window [mem 0xd1100000-0xd11fffff]
[    0.270350] pci 0000:00:05.0:   bridge window [mem pref disabled]
[    0.270356] pci 0000:09:00.0: BAR 6: assigned [mem 0xd1020000-0xd102ffff pref]
[    0.270359] pci 0000:00:06.0: PCI bridge to [bus 09-09]
[    0.270362] pci 0000:00:06.0:   bridge window [io  0x2000-0x2fff]
[    0.270366] pci 0000:00:06.0:   bridge window [mem 0xd2500000-0xd25fffff]
[    0.270370] pci 0000:00:06.0:   bridge window [mem 0xd1000000-0xd10fffff 64bit pref]
[    0.270376] pci 0000:00:14.4: PCI bridge to [bus 80-8f]
[    0.270413] pci 0000:00:14.4:   bridge window [io  0x1000-0x1fff]
[    0.270419] pci 0000:00:14.4:   bridge window [mem disabled]
[    0.270424] pci 0000:00:14.4:   bridge window [mem pref disabled]
[    0.270438] pci 0000:00:01.0: setting latency timer to 64
[    0.270447]   alloc irq_desc for 16 on node -1
[    0.270449]   alloc kstat_irqs on node -1
[    0.270461] pci 0000:00:04.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.270464] pci 0000:00:04.0: setting latency timer to 64
[    0.270471]   alloc irq_desc for 17 on node -1
[    0.270473]   alloc kstat_irqs on node -1
[    0.270477] pci 0000:00:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.270481] pci 0000:00:05.0: setting latency timer to 64
[    0.270487]   alloc irq_desc for 18 on node -1
[    0.270489]   alloc kstat_irqs on node -1
[    0.270493] pci 0000:00:06.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.270497] pci 0000:00:06.0: setting latency timer to 64
[    0.270506] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.270508] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.270511] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.270514] pci_bus 0000:00: resource 7 [mem 0x000c0000-0x000c3fff]
[    0.270517] pci_bus 0000:00: resource 8 [mem 0x000c4000-0x000c7fff]
[    0.270519] pci_bus 0000:00: resource 9 [mem 0x000c8000-0x000cbfff]
[    0.270522] pci_bus 0000:00: resource 10 [mem 0x000d0000-0x000d3fff]
[    0.270525] pci_bus 0000:00: resource 11 [mem 0x000d4000-0x000d7fff]
[    0.270527] pci_bus 0000:00: resource 12 [mem 0x000d8000-0x000dbfff]
[    0.270530] pci_bus 0000:00: resource 13 [mem 0x000dc000-0x000dffff]
[    0.270533] pci_bus 0000:00: resource 14 [mem 0x000e0000-0x000e3fff]
[    0.270536] pci_bus 0000:00: resource 15 [mem 0x000e4000-0x000e7fff]
[    0.270538] pci_bus 0000:00: resource 16 [mem 0x000e8000-0x000ebfff]
[    0.270541] pci_bus 0000:00: resource 17 [mem 0x000ec000-0x000effff]
[    0.270544] pci_bus 0000:00: resource 18 [mem 0xc0000000-0xdfffffff]
[    0.270547] pci_bus 0000:00: resource 19 [mem 0xe4000000-0xffffffff]
[    0.270550] pci_bus 0000:01: resource 0 [io  0x5000-0x5fff]
[    0.270552] pci_bus 0000:01: resource 1 [mem 0xd2200000-0xd23fffff]
[    0.270555] pci_bus 0000:01: resource 2 [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.270558] pci_bus 0000:02: resource 0 [io  0x3000-0x4fff]
[    0.270561] pci_bus 0000:02: resource 1 [mem 0xd1200000-0xd21fffff]
[    0.270564] pci_bus 0000:02: resource 2 [mem 0xd0000000-0xd0ffffff 64bit pref]
[    0.270567] pci_bus 0000:08: resource 1 [mem 0xd1100000-0xd11fffff]
[    0.270570] pci_bus 0000:09: resource 0 [io  0x2000-0x2fff]
[    0.270572] pci_bus 0000:09: resource 1 [mem 0xd2500000-0xd25fffff]
[    0.270575] pci_bus 0000:09: resource 2 [mem 0xd1000000-0xd10fffff 64bit pref]
[    0.270578] pci_bus 0000:80: resource 0 [io  0x1000-0x1fff]
[    0.270581] pci_bus 0000:80: resource 4 [io  0x0000-0x0cf7]
[    0.270584] pci_bus 0000:80: resource 5 [io  0x0d00-0xffff]
[    0.270586] pci_bus 0000:80: resource 6 [mem 0x000a0000-0x000bffff]
[    0.270589] pci_bus 0000:80: resource 7 [mem 0x000c0000-0x000c3fff]
[    0.270592] pci_bus 0000:80: resource 8 [mem 0x000c4000-0x000c7fff]
[    0.270594] pci_bus 0000:80: resource 9 [mem 0x000c8000-0x000cbfff]
[    0.270597] pci_bus 0000:80: resource 10 [mem 0x000d0000-0x000d3fff]
[    0.270600] pci_bus 0000:80: resource 11 [mem 0x000d4000-0x000d7fff]
[    0.270603] pci_bus 0000:80: resource 12 [mem 0x000d8000-0x000dbfff]
[    0.270605] pci_bus 0000:80: resource 13 [mem 0x000dc000-0x000dffff]
[    0.270608] pci_bus 0000:80: resource 14 [mem 0x000e0000-0x000e3fff]
[    0.270611] pci_bus 0000:80: resource 15 [mem 0x000e4000-0x000e7fff]
[    0.270614] pci_bus 0000:80: resource 16 [mem 0x000e8000-0x000ebfff]
[    0.270616] pci_bus 0000:80: resource 17 [mem 0x000ec000-0x000effff]
[    0.270619] pci_bus 0000:80: resource 18 [mem 0xc0000000-0xdfffffff]
[    0.270622] pci_bus 0000:80: resource 19 [mem 0xe4000000-0xffffffff]
[    0.270665] NET: Registered protocol family 2
[    0.270735] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.271009] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.271653] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.271973] TCP: Hash tables configured (established 131072 bind 65536)
[    0.271976] TCP reno registered
[    0.271979] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.272061] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.272166] NET: Registered protocol family 1
[    0.272181] pci 0000:00:01.0: MSI quirk detected; subordinate MSI disabled
[    0.484094] pci 0000:01:05.0: Boot video device
[    0.484110] PCI: CLS 64 bytes, default 64
[    0.484177] Trying to unpack rootfs image as initramfs...
[    0.789334] Freeing initrd memory: 10676k freed
[    0.796779] Simple Boot Flag at 0x44 set to 0x1
[    0.796990] cpufreq-nforce2: No nForce2 chipset.
[    0.797021] Scanning for low memory corruption every 60 seconds
[    0.797157] audit: initializing netlink socket (disabled)
[    0.797231] type=2000 audit(1287069021.796:1): initialized
[    0.808320] highmem bounce pool size: 64 pages
[    0.808326] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.811199] VFS: Disk quotas dquot_6.5.2
[    0.811315] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.812512] fuse init (API version 7.15)
[    0.812619] msgmni has been set to 1683
[    0.813004] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.813007] io scheduler noop registered
[    0.813009] io scheduler deadline registered
[    0.813024] io scheduler cfq registered (default)
[    0.813255] \_SB_.PCI0:_OSC request failed
[    0.813257] _OSC request data:1 0 1d 
[    0.813314] \_SB_.PCI0:_OSC request failed
[    0.813316] _OSC request data:1 0 1d 
[    0.813370] \_SB_.PCI0:_OSC request failed
[    0.813372] _OSC request data:1 0 1d 
[    0.813419] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.813444] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.813979] ACPI: AC Adapter [ACAD] (on-line)
[    0.814055] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.814061] ACPI: Power Button [PWRB]
[    0.814099] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1
[    0.814103] ACPI: Sleep Button [SLPB]
[    0.814157] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input2
[    0.814478] ACPI: Lid Switch [LID]
[    0.814521] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    0.814524] ACPI: Power Button [PWRF]
[    0.814687] ACPI: acpi_idle registered with cpuidle
[    0.817479] [Firmware Bug]: Invalid critical threshold (0)
[    0.818771] thermal LNXTHERM:01: registered as thermal_zone0
[    0.818778] ACPI: Thermal Zone [THRM] (73 C)
[    0.818831] ERST: Table is not found!
[    0.818860] isapnp: Scanning for PnP cards...
[    0.839116] ACPI: Battery Slot [BAT0] (battery present)
[    1.203018] isapnp: No Plug & Play device found
[    1.203269] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    1.204787] brd: module loaded
[    1.205324] loop: module loaded
[    1.205583] pata_acpi 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.205666] pata_acpi 0000:00:14.1: setting latency timer to 64
[    1.206016] Fixed MDIO Bus: probed
[    1.206054] PPP generic driver version 2.4.2
[    1.206089] tun: Universal TUN/TAP device driver, 1.6
[    1.206091] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.206177] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.206231] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.206246] ehci_hcd 0000:00:12.2: setting latency timer to 64
[    1.206250] ehci_hcd 0000:00:12.2: EHCI Host Controller
[    1.206282] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
[    1.206311] ehci_hcd 0000:00:12.2: applying AMD SB600/SB700 USB freeze workaround
[    1.206327] ehci_hcd 0000:00:12.2: debug port 1
[    1.206357] ehci_hcd 0000:00:12.2: irq 17, io mem 0xd2409500
[    1.216055] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00
[    1.216193] hub 1-0:1.0: USB hub found
[    1.216199] hub 1-0:1.0: 6 ports detected
[    1.216355]   alloc irq_desc for 19 on node -1
[    1.216358]   alloc kstat_irqs on node -1
[    1.216366] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.216377] ehci_hcd 0000:00:13.2: setting latency timer to 64
[    1.216381] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    1.216414] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2
[    1.216439] ehci_hcd 0000:00:13.2: applying AMD SB600/SB700 USB freeze workaround
[    1.216454] ehci_hcd 0000:00:13.2: debug port 1
[    1.216475] ehci_hcd 0000:00:13.2: irq 19, io mem 0xd2409400
[    1.228052] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    1.228164] hub 2-0:1.0: USB hub found
[    1.228168] hub 2-0:1.0: 6 ports detected
[    1.228278] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.228325] ohci_hcd 0000:00:12.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.228337] ohci_hcd 0000:00:12.0: setting latency timer to 64
[    1.228341] ohci_hcd 0000:00:12.0: OHCI Host Controller
[    1.228372] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 3
[    1.228399] ohci_hcd 0000:00:12.0: irq 16, io mem 0xd2408000
[    1.288135] hub 3-0:1.0: USB hub found
[    1.288176] hub 3-0:1.0: 3 ports detected
[    1.288240] ohci_hcd 0000:00:12.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.288251] ohci_hcd 0000:00:12.1: setting latency timer to 64
[    1.288255] ohci_hcd 0000:00:12.1: OHCI Host Controller
[    1.288286] ohci_hcd 0000:00:12.1: new USB bus registered, assigned bus number 4
[    1.288302] ohci_hcd 0000:00:12.1: irq 16, io mem 0xd2407000
[    1.348133] hub 4-0:1.0: USB hub found
[    1.348173] hub 4-0:1.0: 3 ports detected
[    1.348235] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.348246] ohci_hcd 0000:00:13.0: setting latency timer to 64
[    1.348250] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    1.348284] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 5
[    1.348310] ohci_hcd 0000:00:13.0: irq 18, io mem 0xd2406000
[    1.408131] hub 5-0:1.0: USB hub found
[    1.408172] hub 5-0:1.0: 3 ports detected
[    1.408233] ohci_hcd 0000:00:13.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.408245] ohci_hcd 0000:00:13.1: setting latency timer to 64
[    1.408248] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    1.408282] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 6
[    1.408344] ohci_hcd 0000:00:13.1: irq 18, io mem 0xd2405000
[    1.468128] hub 6-0:1.0: USB hub found
[    1.468168] hub 6-0:1.0: 3 ports detected
[    1.468235] ohci_hcd 0000:00:14.5: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.468246] ohci_hcd 0000:00:14.5: setting latency timer to 64
[    1.468250] ohci_hcd 0000:00:14.5: OHCI Host Controller
[    1.468281] ohci_hcd 0000:00:14.5: new USB bus registered, assigned bus number 7
[    1.468298] ohci_hcd 0000:00:14.5: irq 18, io mem 0xd2404000
[    1.528130] hub 7-0:1.0: USB hub found
[    1.528137] hub 7-0:1.0: 2 ports detected
[    1.528201] uhci_hcd: USB Universal Host Controller Interface driver
[    1.528284] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.544340] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.544348] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.544431] mice: PS/2 mouse device common for all mice
[    1.544607] rtc_cmos 00:05: RTC can wake from S4
[    1.544644] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    1.544673] rtc0: alarms up to one day, 114 bytes nvram, hpet irqs
[    1.544779] device-mapper: uevent: version 1.0.3
[    1.544936] device-mapper: ioctl: 4.18.0-ioctl (2010-06-29) initialised: [email]dm-devel@redhat.com[/email]
[    1.545001] device-mapper: multipath: version 1.1.1 loaded
[    1.545004] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.545156] EISA: Probing bus 0 at eisa.0
[    1.545158] EISA: Cannot allocate resource for mainboard
[    1.545161] Cannot allocate resource for EISA slot 1
[    1.545163] Cannot allocate resource for EISA slot 2
[    1.545166] Cannot allocate resource for EISA slot 3
[    1.545168] Cannot allocate resource for EISA slot 4
[    1.545170] Cannot allocate resource for EISA slot 5
[    1.545173] Cannot allocate resource for EISA slot 6
[    1.545175] Cannot allocate resource for EISA slot 7
[    1.545177] Cannot allocate resource for EISA slot 8
[    1.545179] EISA: Detected 0 cards.
[    1.545236] cpuidle: using governor ladder
[    1.545238] cpuidle: using governor menu
[    1.545548] TCP cubic registered
[    1.545672] NET: Registered protocol family 10
[    1.546027] lo: Disabled Privacy Extensions
[    1.546258] NET: Registered protocol family 17
[    1.546276] Registering the dns_resolver key type
[    1.546344] powernow-k8: Found 1 AMD Turion(tm) X2 Ultra Dual-Core Mobile ZM-85 (2 cpu cores) (version 2.20.00)
[    1.546391] powernow-k8:    0 : pstate 0 (2300 MHz)
[    1.546393] powernow-k8:    1 : pstate 1 (1150 MHz)
[    1.546395] powernow-k8:    2 : pstate 2 (575 MHz)
[    1.547582] Using IPI No-Shortcut mode
[    1.547660] PM: Resume from disk failed.
[    1.547671] registered taskstats version 1
[    1.548052]   Magic number: 14:283:184
[    1.548102] acpi LNXTHERM:00: hash matches
[    1.548192] rtc_cmos 00:05: setting system clock to 2010-10-14 15:10:23 UTC (1287069023)
[    1.548196] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.548198] EDD information not available.
[    1.548333] Freeing unused kernel memory: 740k freed
[    1.548977] Write protecting the kernel text: 5000k
[    1.549017] Write protecting the kernel read-only data: 2048k
[    1.561019] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    1.567703] udev[64]: starting version 163
[    1.640075] usb 1-4: new high speed USB device using ehci_hcd and address 3
[    1.698153] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.698208] r8169 0000:09:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.698254] r8169 0000:09:00.0: setting latency timer to 64
[    1.698294]   alloc irq_desc for 40 on node -1
[    1.698296]   alloc kstat_irqs on node -1
[    1.698311] r8169 0000:09:00.0: irq 40 for MSI/MSI-X
[    1.698862] r8169 0000:09:00.0: eth0: RTL8168c/8111c at 0xf80c4000, 00:26:9e:77:04:15, XID 1c4000c0 IRQ 40
[    1.710424] scsi0 : pata_atiixp
[    1.720798] scsi1 : pata_atiixp
[    1.721431] ata1: DUMMY
[    1.721434] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x6008 irq 15
[    1.727619] ahci 0000:00:11.0: version 3.0
[    1.727661]   alloc irq_desc for 22 on node -1
[    1.727664]   alloc kstat_irqs on node -1
[    1.727674] ahci 0000:00:11.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    1.727845] ahci 0000:00:11.0: AHCI 0001.0100 32 slots 2 ports 3 Gbps 0x3 impl SATA mode
[    1.727849] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck led clo pmp pio ccc sxs 
[    1.728543] scsi2 : ahci
[    1.728692] scsi3 : ahci
[    1.728775] ata3: SATA max UDMA/133 abar m1024@0xd2409000 port 0xd2409100 irq 22
[    1.728779] ata4: SATA max UDMA/133 abar m1024@0xd2409000 port 0xd2409180 irq 22
[    1.797622] Initializing USB Mass Storage driver...
[    1.797790] scsi4 : usb-storage 1-4:1.0
[    1.797943] usbcore: registered new interface driver usb-storage
[    1.797947] USB Mass Storage support registered.
[    1.896059] usb 2-1: new high speed USB device using ehci_hcd and address 2
[    2.029876] hub 2-1:1.0: USB hub found
[    2.030224] hub 2-1:1.0: 4 ports detected
[    2.140061] usb 2-2: new high speed USB device using ehci_hcd and address 3
[    2.220053] ata4: softreset failed (device not ready)
[    2.220094] ata4: applying SB600 PMP SRST workaround and retrying
[    2.220110] ata3: softreset failed (device not ready)
[    2.220147] ata3: applying SB600 PMP SRST workaround and retrying
[    2.392057] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.392085] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.394287] ata3.00: ATA-8: WDC WD3200BEKT-60F3T1, 12.01A12, max UDMA/100
[    2.394290] ata3.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    2.396539] ata3.00: configured for UDMA/100
[    2.396796] scsi 2:0:0:0: Direct-Access     ATA      WDC WD3200BEKT-6 12.0 PQ: 0 ANSI: 5
[    2.396985] sd 2:0:0:0: Attached scsi generic sg0 type 0
[    2.396993] sd 2:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    2.397062] sd 2:0:0:0: [sda] Write Protect is off
[    2.397066] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.397092] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.409497] ata4.00: ATAPI: hp       CDDVDW TS-L633M, 0301, max UDMA/100
[    2.426050] ata4.00: configured for UDMA/100
[    2.429222] scsi 3:0:0:0: CD-ROM            hp       CDDVDW TS-L633M  0301 PQ: 0 ANSI: 5
[    2.439599] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.439603] cdrom: Uniform CD-ROM driver Revision: 3.20
[    2.439701] sr 3:0:0:0: Attached scsi CD-ROM sr0
[    2.439777] sr 3:0:0:0: Attached scsi generic sg1 type 5
[    2.495697]  sda: sda1 sda2 < sda5 sda6 sda7 sda8 sda9 > sda3
[    2.496182] sd 2:0:0:0: [sda] Attached SCSI disk
[    2.572067] usb 3-2: new full speed USB device using ohci_hcd and address 2
[    2.753069] usbcore: registered new interface driver hiddev
[    2.753268] usbcore: registered new interface driver usbhid
[    2.753270] usbhid: USB HID core driver
[    2.798363] scsi 4:0:0:0: Direct-Access     Generic- Multi-Card       1.00 PQ: 0 ANSI: 0 CCS
[    2.799040] sd 4:0:0:0: Attached scsi generic sg2 type 0
[    2.803226] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[    2.876025] usb 7-1: new full speed USB device using ohci_hcd and address 2
[    3.030600] EXT4-fs (sda8): mounted filesystem with ordered data mode. Opts: (null)
[    3.180026] usb 7-2: new full speed USB device using ohci_hcd and address 3
[    3.420344] usb 2-1.3: new high speed USB device using ehci_hcd and address 4
[    3.513718] hub 2-1.3:1.0: USB hub found
[    3.514057] hub 2-1.3:1.0: 4 ports detected
[    3.784886] usb 2-1.3.2: new full speed USB device using ehci_hcd and address 5
[    3.878142] hub 2-1.3.2:1.0: USB hub found
[    3.878359] hub 2-1.3.2:1.0: 3 ports detected
[    4.148574] usb 2-1.3.2.1: new full speed USB device using ehci_hcd and address 6
[    4.242826] input: Mitsumi Electric Apple Extended USB Keyboard as /devices/pci0000:00/0000:00:13.2/usb2/2-1/2-1.3/2-1.3.2/2-1.3.2.1/2-1.3.2.1:1.0/input/input5
[    4.242906] generic-usb 0003:05AC:0204.0004: input,hidraw0: USB HID v1.10 Keyboard [Mitsumi Electric Apple Extended USB Keyboard] on usb-0000:00:13.2-1.3.2.1/input0
[    4.245349] input: Mitsumi Electric Apple Extended USB Keyboard as /devices/pci0000:00/0000:00:13.2/usb2/2-1/2-1.3/2-1.3.2/2-1.3.2.1/2-1.3.2.1:1.1/input/input6
[    4.245408] generic-usb 0003:05AC:0204.0005: input,hidraw1: USB HID v1.10 Device [Mitsumi Electric Apple Extended USB Keyboard] on usb-0000:00:13.2-1.3.2.1/input1
[    4.316174] usb 2-1.3.2.2: new low speed USB device using ehci_hcd and address 7
[    4.418119] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:13.2/usb2/2-1/2-1.3/2-1.3.2/2-1.3.2.2/2-1.3.2.2:1.0/input/input7
[    4.418211] generic-usb 0003:046D:C044.0006: input,hidraw2: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:13.2-1.3.2.2/input0
[   16.535462] udev[354]: starting version 163
[   16.587025] Adding 3034108k swap on /dev/sda9.  Priority:-1 extents:1 across:3034108k 
[   16.832403] input: Quanta Computer Inc. Optical Touch Screen as /devices/pci0000:00/0000:00:12.0/usb3/3-2/3-2:1.0/input/input8
[   16.832528] quanta-touch 0003:0408:3000.0001: input,hidraw3: USB HID v1.10 Device [Quanta Computer Inc. Optical Touch Screen] on usb-0000:00:12.0-2/input0
[   16.889400] ntrig 0003:1B96:0001.0002: hidraw4: USB HID v1.10 Device [N-trig DuoSense] on usb-0000:00:14.5-2/input0
[   16.893425] lp: driver loaded but no devices found
[   16.899149] input: N-trig DuoSense as /devices/pci0000:00/0000:00:14.5/usb7/7-2/7-2:1.1/input/input9
[   16.899454] input: N-trig DuoSense as /devices/pci0000:00/0000:00:14.5/usb7/7-2/7-2:1.1/input/input10
[   16.899745] input: N-trig DuoSense as /devices/pci0000:00/0000:00:14.5/usb7/7-2/7-2:1.1/input/input11
[   16.899977] ntrig 0003:1B96:0001.0003: input,hidraw5: USB HID v1.10 Device [N-trig DuoSense] on usb-0000:00:14.5-2/input1
[   16.974193] Linux video capture interface: v2.00
[   17.014932] input: HP WMI hotkeys as /devices/virtual/input/input12
[   17.063488] uvcvideo: Found UVC 1.00 device CNF8038 (04f2:b132)
[   17.085085] input: CNF8038 as /devices/pci0000:00/0000:00:13.2/usb2/2-2/2-2:1.0/input/input13
[   17.085169] usbcore: registered new interface driver uvcvideo
[   17.085171] USB Video Class driver (v0.1.0)
[   17.132141] shpchp 0000:00:01.0: HPC vendor_id 1022 device_id 9602 ss_vid 1022 ss_did 9602
[   17.132148] shpchp 0000:00:01.0: Cannot reserve MMIO region
[   17.132239] shpchp 0000:00:04.0: HPC vendor_id 1022 device_id 9604 ss_vid 103c ss_did 3045
[   17.132242] shpchp 0000:00:04.0: Cannot reserve MMIO region
[   17.132286] shpchp 0000:00:05.0: HPC vendor_id 1022 device_id 9605 ss_vid 103c ss_did 3045
[   17.132588] shpchp 0000:00:05.0: Cannot reserve MMIO region
[   17.132634] shpchp 0000:00:06.0: HPC vendor_id 1022 device_id 9606 ss_vid 103c ss_did 3045
[   17.132637] shpchp 0000:00:06.0: Cannot reserve MMIO region
[   17.132796] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   17.165132] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0xb00, revision 0
[   17.207369] type=1400 audit(1287083439.153:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=642 comm="apparmor_parser"
[   17.207437] type=1400 audit(1287083439.153:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=642 comm="apparmor_parser"
[   17.207488] type=1400 audit(1287083439.153:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=642 comm="apparmor_parser"
[   17.213791] Linux agpgart interface v0.103
[   17.288480] [drm] Initialized drm 1.1.0 20060810
[   17.295863] acpi device:03: registered as cooling_device2
[   17.296731] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:00/LNXVIDEO:00/input/input14
[   17.296865] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   17.429215] EXT4-fs (sda8): re-mounted. Opts: errors=remount-ro
[   17.524198] [drm] radeon defaulting to kernel modesetting.
[   17.524204] [drm] radeon kernel modesetting enabled.
[   17.524306] radeon 0000:01:05.0: power state changed by ACPI to D0
[   17.524314] radeon 0000:01:05.0: power state changed by ACPI to D0
[   17.524325] radeon 0000:01:05.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   17.524331] radeon 0000:01:05.0: setting latency timer to 64
[   17.526274] [drm] initializing kernel modesetting (RS780 0x1002:0x9612).
[   17.528853] [drm] register mmio base: 0xD2300000
[   17.528856] [drm] register mmio size: 65536
[   17.530341] ATOM BIOS: HP_Soyuz30
[   17.530379] radeon 0000:01:05.0: VRAM: 320M 0xC0000000 - 0xD3FFFFFF (320M used)
[   17.530383] radeon 0000:01:05.0: GTT: 512M 0xA0000000 - 0xBFFFFFFF
[   17.530690] [drm] Detected VRAM RAM=320M, BAR=256M
[   17.530696] [drm] RAM width 32bits DDR
[   17.531164] [TTM] Zone  kernel: Available graphics memory: 431426 kiB.
[   17.531167] [TTM] Zone highmem: Available graphics memory: 1417298 kiB.
[   17.531169] [TTM] Initializing pool allocator.
[   17.531193] [drm] radeon: 320M of VRAM memory ready
[   17.531196] [drm] radeon: 512M of GTT memory ready.
[   17.531238] [drm] radeon: irq initialized.
[   17.531242] [drm] GART: num cpu pages 131072, num gpu pages 131072
[   17.533739] [drm] Loading RS780 Microcode
[   17.541663] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   17.541753] HDA Intel 0000:00:14.2: setting latency timer to 64
[   17.694257] [drm] ring test succeeded in 0 usecs
[   17.694557] [drm] radeon: ib pool ready.
[   17.694641] [drm] ib test succeeded in 0 usecs
[   17.694644] [drm] Enabling audio support
[   17.695955] [drm] Default TV standard: NTSC
[   17.696077] [drm] Default TV standard: NTSC
[   17.696214] [drm] Radeon Display Connectors
[   17.696216] [drm] Connector 0:
[   17.696218] [drm]   VGA
[   17.696220] [drm]   DDC: 0x7e40 0x7e40 0x7e44 0x7e44 0x7e48 0x7e48 0x7e4c 0x7e4c
[   17.696222] [drm]   Encoders:
[   17.696224] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
[   17.696226] [drm] Connector 1:
[   17.696228] [drm]   DIN
[   17.696229] [drm]   Encoders:
[   17.696231] [drm]     TV1: INTERNAL_KLDSCP_DAC1
[   17.696233] [drm] Connector 2:
[   17.696234] [drm]   LVDS
[   17.696237] [drm]   DDC: 0x7e50 0x7e50 0x7e54 0x7e54 0x7e58 0x7e58 0x7e5c 0x7e5c
[   17.696239] [drm]   Encoders:
[   17.696240] [drm]     LCD1: INTERNAL_KLDSCP_LVTMA
[   17.807755] [drm] radeon: power management initialized
[   17.823212] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x180b1, caps: 0xa04711/0xa00000/0x0
[   17.892835] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input15
[   18.877396] [drm] fb mappable at 0xC0141000
[   18.877400] [drm] vram apper at 0xC0000000
[   18.877403] [drm] size 8294400
[   18.877404] [drm] fb depth is 24
[   18.877406] [drm]    pitch is 7680
[   18.926655] Console: switching to colour frame buffer device 160x50
[   18.942403] fb0: radeondrmfb frame buffer device
[   18.942406] drm: registered panic notifier
[   18.942533] [drm] Initialized radeon 2.6.0 20080528 for 0000:01:05.0 on minor 0
[   19.580751] apparmor_parser[954]: segfault at 0 ip 08051034 sp bfcd8430 error 4 in apparmor_parser[8048000+be000]
[   19.629298] apparmor_parser[988]: segfault at 0 ip 08051034 sp bfc9cfe0 error 4 in apparmor_parser[8048000+be000]
[   19.630389] apparmor_parser[987]: segfault at 0 ip 08051034 sp bfff2170 error 4 in apparmor_parser[8048000+be000]
[   19.651750] ppdev: user-space parallel port driver
[   20.713171] EXT4-fs (sda8): re-mounted. Opts: errors=remount-ro,commit=0
[   25.064050] r8169 0000:09:00.0: eth0: link up
[   25.064058] r8169 0000:09:00.0: eth0: link up
[   27.660308] r8169 0000:09:00.0: eth0: link up
[   27.715146] start_kdeinit (1562): /proc/1578/oom_adj is deprecated, please use /proc/1578/oom_score_adj instead.
[   27.850100] r8169 0000:09:00.0: eth0: link up
[   29.894730] type=1400 audit(1287083451.841:5): apparmor="DENIED" operation="open" parent=1577 profile="/sbin/dhclient3" name="/var/lib/wicd/dhclient.conf" pid=1612 comm="dhclient" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
[   30.682157] EXT4-fs (sda8): re-mounted. Opts: errors=remount-ro,commit=600
[   38.520031] eth0: no IPv6 routers present
[   87.052349] lo: Disabled Privacy Extensions
lg@lg-laptop:~$ 

---

### Post by Ayuthia on 2010-10-25
The only thing that I can think of right now is the temperature.  Have you checked the temp?  

@lawrencegoodman, I see that you are using the radeon driver instead of fglrx.  Have you tried switching the profile to low:
```

echo low | sudo tee /sys/class/drm/card0/device/power_profile

```
and see if it makes a difference?

---

### Post by ihlinuxdude on 2010-11-16
You know, it might help if I subscribed to my own posts.:rolleyes:
I'm a noob, so could you tell me how to check the firmware?
I'm using the fglrx graphics driver, and installing unity right now.
I've been using onBoard but it happens when I'm not using it too.

---

### Post by Ayuthia on 2010-11-16
> **ihlinuxdude said:**
> You know, it might help if I subscribed to my own posts.:rolleyes:
I'm a noob, so could you tell me how to check the firmware?
I'm using the fglrx graphics driver, and installing unity right now.
I've been using onBoard but it happens when I'm not using it too.

You can try this [link]("https://wiki.ubuntu.com/Multitouch/Calibration/Ntrig").  The application will give you the firmware information.

---

