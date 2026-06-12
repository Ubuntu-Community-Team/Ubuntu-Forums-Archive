---
title: "Random freezing in Ubuntu &amp; Kubuntu"
date: 2010-12-31
forum: New to Ubuntu
---

### Post by mechanizedmedic on 2010-12-31
was having some issues with ubuntu 10.04 (amd64) graphics freaking out and freezing up but i thought, after a ton of searching, it was a gnome issue. i couldn't find anything that would fix it so i backed up and installed kubuntu 10.10 (amd64) yesterday. today, the freezing started agian:confused:... please help! 

Hardware:
AMD Athlon II X3 435
Biostar A77E03 mobo
nVidia GT218 [GeForce 210] (proprietary driver is enabled and in use)
Patriot PS-100 SSD (30GB)
1TB SATA HDD
250GB PATA HDD

---

### Post by sandyd on 2010-12-31
> **mechanizedmedic said:**
> was having some issues with ubuntu 10.04 (amd64) graphics freaking out and freezing up but i thought, after a ton of searching, it was a gnome issue. i couldn't find anything that would fix it so i backed up and installed kubuntu 10.10 (amd64) yesterday. today, the freezing started agian:confused:... please help! 

Hardware:
AMD Athlon II X3 435
Biostar A77E03 mobo
nVidia GT218 [GeForce 210] (proprietary driver is enabled and in use)
Patriot PS-100 SSD (30GB)
1TB SATA HDD
250GB PATA HDD
post output of 
```

dmesg
``` after a freeze
also, have you checked your RAM via memtest

---

### Post by mechanizedmedic on 2010-12-31
here's the whole log file. the most recent freeze/crash was shortly before i changed some mounting options. it crashed three times within a short period but has been stable for a few hours now. (knock on wood)

also, i noticed that some of these log entries refer to bios settings. my bios are set to the "optimal defaults". is there anything i might need to change in there?

thank you for your assistance!
~matt

```
:~$ dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.35-24-generic (buildd@yellow) (gcc version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu5) ) #42-Ubuntu SMP Thu Dec 2 02:41:37 UTC 2010 (Ubuntu 2.6.35-24.42-generic 2.6.35.8)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-24-generic root=UUID=fe113d95-a3e3-4589-9694-b7680d591c38 ro quiet splash
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f400 (usable)
[    0.000000]  BIOS-e820: 000000000009f400 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e6000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000c7fb0000 (usable)
[    0.000000]  BIOS-e820: 00000000c7fb0000 - 00000000c7fbe000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000c7fbe000 - 00000000c7fe0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000c7fe0000 - 00000000c8000000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff700000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000138000000 (usable)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 update range: 0000000000000000 - 0000000000001000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] No AGP bridge found
[    0.000000] last_pfn = 0x138000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000000 mask FFFF80000000 write-back
[    0.000000]   1 base 000080000000 mask FFFFC0000000 write-back
[    0.000000]   2 base 0000C0000000 mask FFFFF8000000 write-back
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] TOM2: 0000000138000000 aka 4992M
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 00000000c8000000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0xc7fb0 max_arch_pfn = 0x400000000
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009f400 (usable)
[    0.000000]  modified: 000000000009f400 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e6000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000c7fb0000 (usable)
[    0.000000]  modified: 00000000c7fb0000 - 00000000c7fbe000 (ACPI data)
[    0.000000]  modified: 00000000c7fbe000 - 00000000c7fe0000 (ACPI NVS)
[    0.000000]  modified: 00000000c7fe0000 - 00000000c8000000 (reserved)
[    0.000000]  modified: 00000000ff700000 - 0000000100000000 (reserved)
[    0.000000]  modified: 0000000100000000 - 0000000138000000 (usable)
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] found SMP MP-table at [ffff8800000ff780] ff780
[    0.000000] Using GB pages for direct mapping
[    0.000000] init_memory_mapping: 0000000000000000-00000000c7fb0000
[    0.000000]  0000000000 - 00c0000000 page 1G
[    0.000000]  00c0000000 - 00c7e00000 page 2M
[    0.000000]  00c7e00000 - 00c7fb0000 page 4k
[    0.000000] kernel direct mapping tables up to c7fb0000 @ 16000-19000
[    0.000000] init_memory_mapping: 0000000100000000-0000000138000000
[    0.000000]  0100000000 - 0138000000 page 2M
[    0.000000] kernel direct mapping tables up to 138000000 @ 18000-1a000
[    0.000000] RAMDISK: 37571000 - 37ff0000
[    0.000000] ACPI: RSDP 00000000000fb460 00014 (v00 ACPIAM)
[    0.000000] ACPI: RSDT 00000000c7fb0000 0003C (v01 032410 RSDT1224 20100324 MSFT 00000097)
[    0.000000] ACPI: FACP 00000000c7fb0200 00084 (v02 032410 FACP1224 20100324 MSFT 00000097)
[    0.000000] ACPI: DSDT 00000000c7fb0450 096CD (v01  78XAD 78XAD324 00000004 INTL 20051117)
[    0.000000] ACPI: FACS 00000000c7fbe000 00040
[    0.000000] ACPI: APIC 00000000c7fb0390 0007C (v01 032410 APIC1224 20100324 MSFT 00000097)
[    0.000000] ACPI: MCFG 00000000c7fb0410 0003C (v01 032410 OEMMCFG  20100324 MSFT 00000097)
[    0.000000] ACPI: OEMB 00000000c7fbe040 00071 (v01 032410 OEMB1224 20100324 MSFT 00000097)
[    0.000000] ACPI: HPET 00000000c7fb9b20 00038 (v01 032410 OEMHPET  20100324 MSFT 00000097)
[    0.000000] ACPI: SSDT 00000000c7fb9b60 00672 (v01 A M I  POWERNOW 00000001 AMD  00000001)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-0000000138000000
[    0.000000] Initmem setup node 0 0000000000000000-0000000138000000
[    0.000000]   NODE_DATA [0000000100000000 - 0000000100004fff]
[    0.000000]  [ffffea0000000000-ffffea00045fffff] PMD -> [ffff880100200000-ffff880103bfffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00138000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x000c7fb0
[    0.000000]     0: 0x00100000 -> 0x00138000
[    0.000000] On node 0 totalpages: 1048383
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3927 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14280 pages used for memmap
[    0.000000]   DMA32 zone: 800744 pages, LIFO batch:31
[    0.000000]   Normal zone: 3136 pages used for memmap
[    0.000000]   Normal zone: 226240 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x84] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x85] disabled)
[    0.000000] ACPI: IOAPIC (id[0x03] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 3, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8300 base: 0xfed00000
[    0.000000] SMP: Allowing 6 CPUs, 3 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] early_res array is doubled to 64 at [19000 - 197ff]
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e6000
[    0.000000] PM: Registered nosave memory: 00000000000e6000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000c7fb0000 - 00000000c7fbe000
[    0.000000] PM: Registered nosave memory: 00000000c7fbe000 - 00000000c7fe0000
[    0.000000] PM: Registered nosave memory: 00000000c7fe0000 - 00000000c8000000
[    0.000000] PM: Registered nosave memory: 00000000c8000000 - 00000000ff700000
[    0.000000] PM: Registered nosave memory: 00000000ff700000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at c8000000 (gap: c8000000:37700000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:6 nr_node_ids:1
[    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880001e00000 s91520 r8192 d23168 u262144
[    0.000000] pcpu-alloc: s91520 r8192 d23168 u262144 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 - - 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1030911
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-24-generic root=UUID=fe113d95-a3e3-4589-9694-b7680d591c38 ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Node 0: aperture @ 20000000 size 32 MB
[    0.000000] Aperture pointing to e820 RAM. Ignoring.
[    0.000000] Your BIOS doesn't leave a aperture memory hole
[    0.000000] Please enable the IOMMU option in the BIOS setup
[    0.000000] This costs you 64 MB of RAM
[    0.000000] Mapping aperture over 65536 KB of RAM @ 20000000
[    0.000000] PM: Registered nosave memory: 0000000020000000 - 0000000024000000
[    0.000000] early_res array is doubled to 128 at [19800 - 1a7ff]
[    0.000000] Subtract (59 early reservations)
[    0.000000]   #1 [0001000000 - 0001d17114]   TEXT DATA BSS
[    0.000000]   #2 [0037571000 - 0037ff0000]         RAMDISK
[    0.000000]   #3 [0001d18000 - 0001d1811f]             BRK
[    0.000000]   #4 [00000ff790 - 0000100000]   BIOS reserved
[    0.000000]   #5 [00000ff780 - 00000ff790]    MP-table mpf
[    0.000000]   #6 [000009f400 - 00000e5e00]   BIOS reserved
[    0.000000]   #7 [00000e5f78 - 00000ff780]   BIOS reserved
[    0.000000]   #8 [00000e5e00 - 00000e5f78]    MP-table mpc
[    0.000000]   #9 [0000010000 - 0000012000]      TRAMPOLINE
[    0.000000]   #10 [0000012000 - 0000016000]     ACPI WAKEUP
[    0.000000]   #11 [0000016000 - 0000018000]         PGTABLE
[    0.000000]   #12 [0000018000 - 0000019000]         PGTABLE
[    0.000000]   #13 [0100000000 - 0100005000]       NODE_DATA
[    0.000000]   #14 [0001d18140 - 0001d19140]         BOOTMEM
[    0.000000]   #15 [0001d17140 - 0001d17440]         BOOTMEM
[    0.000000]   #16 [0100005000 - 0100006000]         BOOTMEM
[    0.000000]   #17 [0100006000 - 0100007000]         BOOTMEM
[    0.000000]   #18 [0100200000 - 0103c00000]        MEMMAP 0
[    0.000000]   #19 [0001d17440 - 0001d175c0]         BOOTMEM
[    0.000000]   #20 [0001d19140 - 0001d31140]         BOOTMEM
[    0.000000]   #21 [0001d31140 - 0001d37140]         BOOTMEM
[    0.000000]   #22 [0001d38000 - 0001d39000]         BOOTMEM
[    0.000000]   #23 [0001d175c0 - 0001d17601]         BOOTMEM
[    0.000000]   #24 [0001d17640 - 0001d17683]         BOOTMEM
[    0.000000]   #25 [0001d176c0 - 0001d178f0]         BOOTMEM
[    0.000000]   #26 [0001d17900 - 0001d17968]         BOOTMEM
[    0.000000]   #27 [0001d17980 - 0001d179e8]         BOOTMEM
[    0.000000]   #28 [0001d17a00 - 0001d17a68]         BOOTMEM
[    0.000000]   #29 [0001d17a80 - 0001d17ae8]         BOOTMEM
[    0.000000]   #30 [0001d17b00 - 0001d17b68]         BOOTMEM
[    0.000000]   #31 [0001d17b80 - 0001d17be8]         BOOTMEM
[    0.000000]   #32 [0001d17c00 - 0001d17c68]         BOOTMEM
[    0.000000]   #33 [0001d17c80 - 0001d17ce8]         BOOTMEM
[    0.000000]   #34 [0001d17d00 - 0001d17d68]         BOOTMEM
[    0.000000]   #35 [0001d17d80 - 0001d17da0]         BOOTMEM
[    0.000000]   #36 [0001d17dc0 - 0001d17de0]         BOOTMEM
[    0.000000]   #37 [0001d17e00 - 0001d17e6a]         BOOTMEM
[    0.000000]   #38 [0001d17e80 - 0001d17eea]         BOOTMEM
[    0.000000]   #39 [0001e00000 - 0001e1e000]         BOOTMEM
[    0.000000]   #40 [0001e40000 - 0001e5e000]         BOOTMEM
[    0.000000]   #41 [0001e80000 - 0001e9e000]         BOOTMEM
[    0.000000]   #42 [0001ec0000 - 0001ede000]         BOOTMEM
[    0.000000]   #43 [0001f00000 - 0001f1e000]         BOOTMEM
[    0.000000]   #44 [0001f40000 - 0001f5e000]         BOOTMEM
[    0.000000]   #45 [0001d17f00 - 0001d17f08]         BOOTMEM
[    0.000000]   #46 [0001d17f40 - 0001d17f48]         BOOTMEM
[    0.000000]   #47 [0001d17f80 - 0001d17f98]         BOOTMEM
[    0.000000]   #48 [0001d17fc0 - 0001d17ff0]         BOOTMEM
[    0.000000]   #49 [0001d37140 - 0001d37260]         BOOTMEM
[    0.000000]   #50 [0001d37280 - 0001d372c8]         BOOTMEM
[    0.000000]   #51 [0001d37300 - 0001d37348]         BOOTMEM
[    0.000000]   #52 [0001d39000 - 0001d41000]         BOOTMEM
[    0.000000]   #53 [0020000000 - 0024000000]         BOOTMEM
[    0.000000]   #54 [0001d37380 - 0001d373a0]         BOOTMEM
[    0.000000]   #55 [0001f5e000 - 0005f5e000]         BOOTMEM
[    0.000000]   #56 [0001d41000 - 0001d61000]         BOOTMEM
[    0.000000]   #57 [0001d61000 - 0001da1000]         BOOTMEM
[    0.000000]   #58 [000001a800 - 0000022800]         BOOTMEM
[    0.000000] Memory: 3977544k/5111808k available (5711k kernel code, 918276k absent, 215988k reserved, 5379k data, 908k init)
[    0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=6, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]  RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]  RCU-based detection of stalled CPUs is disabled.
[    0.000000]  Verbose stalled-CPUs detection is disabled.
[    0.000000] NR_IRQS:4352 nr_irqs:728
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 41943040 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2899.933 MHz processor.
[    0.020007] Calibrating delay loop (skipped), value calculated using timer frequency.. 5799.85 BogoMIPS (lpj=28999290)
[    0.020011] pid_max: default: 32768 minimum: 301
[    0.020027] Security Framework initialized
[    0.020040] AppArmor: AppArmor initialized
[    0.020041] Yama: becoming mindful.
[    0.020392] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.021616] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.022151] Mount-cache hash table entries: 256
[    0.022246] Initializing cgroup subsys ns
[    0.022249] Initializing cgroup subsys cpuacct
[    0.022252] Initializing cgroup subsys memory
[    0.022259] Initializing cgroup subsys devices
[    0.022260] Initializing cgroup subsys freezer
[    0.022262] Initializing cgroup subsys net_cls
[    0.022280] tseg: 0000000000
[    0.022291] CPU: Physical Processor ID: 0
[    0.022292] CPU: Processor Core ID: 0
[    0.022294] mce: CPU supports 6 MCE banks
[    0.022301] Performance Events: AMD PMU driver.
[    0.022305] ... version:                0
[    0.022306] ... bit width:              48
[    0.022307] ... generic registers:      4
[    0.022309] ... value mask:             0000ffffffffffff
[    0.022310] ... max period:             00007fffffffffff
[    0.022311] ... fixed-purpose events:   0
[    0.022312] ... event mask:             000000000000000f
[    0.023584] ACPI: Core revision 20100428
[    0.040006] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.040009] ftrace: allocating 22678 entries in 89 pages
[    0.045099] Setting APIC routing to flat
[    0.045402] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.147755] CPU0: AMD Athlon(tm) II X3 435 Processor stepping 02
[    0.150000] Booting Node   0, Processors  #1 #2
[    0.480004] Brought up 3 CPUs
[    0.480006] Total of 3 processors activated (17400.57 BogoMIPS).
[    0.480244] devtmpfs: initialized
[    0.480595] regulator: core version 0.5
[    0.480618] Time: 19:58:59  Date: 12/31/10
[    0.480644] NET: Registered protocol family 16
[    0.480735] node 0 link 0: io port [1000, ffffff]
[    0.480737] TOM: 00000000c8000000 aka 3200M
[    0.480739] Fam 10h mmconf [e0000000, efffffff]
[    0.480741] node 0 link 0: mmio [e0000000, efffffff] ==> none
[    0.480744] node 0 link 0: mmio [f0000000, ffffffff]
[    0.480746] node 0 link 0: mmio [a0000, bffff]
[    0.480748] node 0 link 0: mmio [c8000000, dfffffff]
[    0.480749] TOM2: 0000000138000000 aka 4992M
[    0.480751] bus: [00, 07] on node 0 link 0
[    0.480753] bus: 00 index 0 [io  0x0000-0xffff]
[    0.480754] bus: 00 index 1 [mem 0xf0000000-0xffffffff]
[    0.480756] bus: 00 index 2 [mem 0x000a0000-0x000bffff]
[    0.480757] bus: 00 index 3 [mem 0xc8000000-0xdfffffff]
[    0.480759] bus: 00 index 4 [mem 0x138000000-0xfcffffffff]
[    0.480767] ACPI: bus type pci registered
[    0.480651] Trying to unpack rootfs image as initramfs...
[    0.480819] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.480821] PCI: not using MMCONFIG
[    0.480822] PCI: Using configuration type 1 for base access
[    0.480824] PCI: Using configuration type 1 for extended access
[    0.481243] bio: create slab <bio-0> at 0
[    0.481243] ACPI: EC: Look up EC in DSDT
[    0.482226] ACPI: Executed 5 blocks of module-level executable AML code
[    0.491426] ACPI: Interpreter enabled
[    0.491428] ACPI: (supports S0 S1 S4 S5)
[    0.491444] ACPI: Using IOAPIC for interrupt routing
[    0.491485] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.493262] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in ACPI motherboard resources
[    0.517740] ACPI Warning: Incorrect checksum in table [OEMB] - 0xB2, should be 0xAD (20100428/tbutils-314)
[    0.517833] ACPI: No dock devices found.
[    0.517836] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.517959] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.518199] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7]
[    0.518201] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff]
[    0.518203] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.518205] pci_root PNP0A03:00: host bridge window [mem 0x000d0000-0x000dffff]
[    0.518206] pci_root PNP0A03:00: host bridge window [mem 0xc8000000-0xdfffffff]
[    0.518208] pci_root PNP0A03:00: host bridge window [mem 0xf0000000-0xfebfffff]
[    0.518228] pci 0000:00:00.0: reg 1c: [mem 0xe0000000-0xffffffff 64bit]
[    0.518283] pci 0000:00:02.0: PME# supported from D0 D3hot D3cold
[    0.518285] pci 0000:00:02.0: PME# disabled
[    0.518324] pci 0000:00:07.0: PME# supported from D0 D3hot D3cold
[    0.518326] pci 0000:00:07.0: PME# disabled
[    0.518376] pci 0000:00:11.0: reg 10: [io  0xc000-0xc007]
[    0.518382] pci 0000:00:11.0: reg 14: [io  0xb000-0xb003]
[    0.518389] pci 0000:00:11.0: reg 18: [io  0xa000-0xa007]
[    0.518395] pci 0000:00:11.0: reg 1c: [io  0x9000-0x9003]
[    0.518401] pci 0000:00:11.0: reg 20: [io  0x8000-0x800f]
[    0.518407] pci 0000:00:11.0: reg 24: [mem 0xfcfff800-0xfcfffbff]
[    0.518425] pci 0000:00:11.0: set SATA to AHCI mode
[    0.518478] pci 0000:00:12.0: reg 10: [mem 0xfcffe000-0xfcffefff]
[    0.518532] pci 0000:00:12.1: reg 10: [mem 0xfcffd000-0xfcffdfff]
[    0.518596] pci 0000:00:12.2: reg 10: [mem 0xfcfff000-0xfcfff0ff]
[    0.518648] pci 0000:00:12.2: supports D1 D2
[    0.518649] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
[    0.518653] pci 0000:00:12.2: PME# disabled
[    0.518683] pci 0000:00:13.0: reg 10: [mem 0xfcffc000-0xfcffcfff]
[    0.518735] pci 0000:00:13.1: reg 10: [mem 0xfcffb000-0xfcffbfff]
[    0.518799] pci 0000:00:13.2: reg 10: [mem 0xfcffa800-0xfcffa8ff]
[    0.518851] pci 0000:00:13.2: supports D1 D2
[    0.518853] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
[    0.518856] pci 0000:00:13.2: PME# disabled
[    0.518963] pci 0000:00:14.1: reg 10: [io  0x0000-0x0007]
[    0.518969] pci 0000:00:14.1: reg 14: [io  0x0000-0x0003]
[    0.518975] pci 0000:00:14.1: reg 18: [io  0x0000-0x0007]
[    0.518981] pci 0000:00:14.1: reg 1c: [io  0x0000-0x0003]
[    0.518987] pci 0000:00:14.1: reg 20: [io  0xff00-0xff0f]
[    0.519049] pci 0000:00:14.2: reg 10: [mem 0xfcff4000-0xfcff7fff 64bit]
[    0.519091] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
[    0.519095] pci 0000:00:14.2: PME# disabled
[    0.519196] pci 0000:00:14.5: reg 10: [mem 0xfcff9000-0xfcff9fff]
[    0.519360] pci 0000:01:00.0: reg 10: [mem 0xfd000000-0xfdffffff]
[    0.519368] pci 0000:01:00.0: reg 14: [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.519376] pci 0000:01:00.0: reg 1c: [mem 0xce000000-0xcfffffff 64bit pref]
[    0.519381] pci 0000:01:00.0: reg 24: [io  0xd800-0xd87f]
[    0.519386] pci 0000:01:00.0: reg 30: [mem 0xfe980000-0xfe9fffff pref]
[    0.519434] pci 0000:01:00.1: reg 10: [mem 0xfe97c000-0xfe97ffff]
[    0.530028] pci 0000:00:02.0: PCI bridge to [bus 01-01]
[    0.530033] pci 0000:00:02.0:   bridge window [io  0xd000-0xdfff]
[    0.530036] pci 0000:00:02.0:   bridge window [mem 0xfd000000-0xfe9fffff]
[    0.530040] pci 0000:00:02.0:   bridge window [mem 0xce000000-0xdfffffff 64bit pref]
[    0.530090] pci 0000:02:00.0: reg 10: [io  0xe800-0xe8ff]
[    0.530105] pci 0000:02:00.0: reg 18: [mem 0xfbfff000-0xfbffffff 64bit pref]
[    0.530115] pci 0000:02:00.0: reg 20: [mem 0xfbff8000-0xfbffbfff 64bit pref]
[    0.530121] pci 0000:02:00.0: reg 30: [mem 0xfeae0000-0xfeafffff pref]
[    0.530153] pci 0000:02:00.0: supports D1 D2
[    0.530154] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.530158] pci 0000:02:00.0: PME# disabled
[    0.550026] pci 0000:00:07.0: PCI bridge to [bus 02-02]
[    0.550032] pci 0000:00:07.0:   bridge window [io  0xe000-0xefff]
[    0.550034] pci 0000:00:07.0:   bridge window [mem 0xfea00000-0xfeafffff]
[    0.550038] pci 0000:00:07.0:   bridge window [mem 0xfbf00000-0xfbffffff 64bit pref]
[    0.550092] pci 0000:03:05.0: reg 10: [mem 0xfebf8000-0xfebfffff]
[    0.550204] pci 0000:00:14.4: PCI bridge to [bus 03-03] (subtractive decode)
[    0.550208] pci 0000:00:14.4:   bridge window [io  0xf000-0x0000] (disabled)
[    0.550212] pci 0000:00:14.4:   bridge window [mem 0xfeb00000-0xfebfffff]
[    0.550216] pci 0000:00:14.4:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.550218] pci 0000:00:14.4:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.550220] pci 0000:00:14.4:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.550222] pci 0000:00:14.4:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.550224] pci 0000:00:14.4:   bridge window [mem 0x000d0000-0x000dffff] (subtractive decode)
[    0.550225] pci 0000:00:14.4:   bridge window [mem 0xc8000000-0xdfffffff] (subtractive decode)
[    0.550227] pci 0000:00:14.4:   bridge window [mem 0xf0000000-0xfebfffff] (subtractive decode)
[    0.550246] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.550422] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE2._PRT]
[    0.550473] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE7._PRT]
[    0.550534] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0PC._PRT]
[    0.553926] ACPI: PCI Interrupt Link [LNKA] (IRQs 4 7 10 *11 12 14 15)
[    0.554008] ACPI: PCI Interrupt Link [LNKB] (IRQs 4 7 *10 11 12 14 15)
[    0.554087] ACPI: PCI Interrupt Link [LNKC] (IRQs 4 7 *10 11 12 14 15)
[    0.554166] ACPI: PCI Interrupt Link [LNKD] (IRQs 4 7 10 *11 12 14 15)
[    0.554245] ACPI: PCI Interrupt Link [LNKE] (IRQs 4 7 *10 11 12 14 15)
[    0.554323] ACPI: PCI Interrupt Link [LNKF] (IRQs 4 7 10 11 12 14 15) *0, disabled.
[    0.554402] ACPI: PCI Interrupt Link [LNKG] (IRQs 4 *10 11 12 14 15)
[    0.554481] ACPI: PCI Interrupt Link [LNKH] (IRQs 4 7 10 11 12 14 15) *0, disabled.
[    0.554511] HEST: Table is not found!
[    0.554578] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.554580] vgaarb: loaded
[    0.554680] SCSI subsystem initialized
[    0.554700] libata version 3.00 loaded.
[    0.554700] usbcore: registered new interface driver usbfs
[    0.554700] usbcore: registered new interface driver hub
[    0.554700] usbcore: registered new device driver usb
[    0.554700] ACPI: WMI: Mapper loaded
[    0.554700] PCI: Using ACPI for IRQ routing
[    0.554700] PCI: pci_cache_line_size set to 64 bytes
[    0.554700] pci 0000:00:00.0: no compatible bridge window for [mem 0xe0000000-0xffffffff 64bit]
[    0.554700] reserve RAM buffer: 000000000009f400 - 000000000009ffff 
[    0.554700] reserve RAM buffer: 00000000c7fb0000 - 00000000c7ffffff 
[    0.554700] NetLabel: Initializing
[    0.554700] NetLabel:  domain hash size = 128
[    0.554700] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.554700] NetLabel:  unlabeled traffic allowed by default
[    0.554700] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.554700] hpet0: 4 comparators, 32-bit 14.318180 MHz counter
[    0.554700] Switching to clocksource tsc
[    0.555512] AppArmor: AppArmor Filesystem Enabled
[    0.555527] pnp: PnP ACPI init
[    0.555540] ACPI: bus type pnp registered
[    0.559046] pnp 00:0c: disabling [mem 0x00000000-0x0009ffff] because it overlaps 0000:00:00.0 BAR 3 [mem 0x00000000-0x1fffffff 64bit]
[    0.559049] pnp 00:0c: disabling [mem 0x000c0000-0x000cffff] because it overlaps 0000:00:00.0 BAR 3 [mem 0x00000000-0x1fffffff 64bit]
[    0.559052] pnp 00:0c: disabling [mem 0x000e0000-0x000fffff] because it overlaps 0000:00:00.0 BAR 3 [mem 0x00000000-0x1fffffff 64bit]
[    0.559055] pnp 00:0c: disabling [mem 0x00100000-0xc7ffffff] because it overlaps 0000:00:00.0 BAR 3 [mem 0x00000000-0x1fffffff 64bit]
[    0.559293] pnp: PnP ACPI: found 13 devices
[    0.559294] ACPI: ACPI bus type pnp unregistered
[    0.559303] system 00:07: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.559305] system 00:07: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.559309] system 00:08: [io  0x04d0-0x04d1] has been reserved
[    0.559311] system 00:08: [io  0x040b] has been reserved
[    0.559313] system 00:08: [io  0x04d6] has been reserved
[    0.559315] system 00:08: [io  0x0c00-0x0c01] has been reserved
[    0.559316] system 00:08: [io  0x0c14] has been reserved
[    0.559318] system 00:08: [io  0x0c50-0x0c51] has been reserved
[    0.559319] system 00:08: [io  0x0c52] has been reserved
[    0.559321] system 00:08: [io  0x0c6c] has been reserved
[    0.559323] system 00:08: [io  0x0c6f] has been reserved
[    0.559324] system 00:08: [io  0x0cd0-0x0cd1] has been reserved
[    0.559326] system 00:08: [io  0x0cd2-0x0cd3] has been reserved
[    0.559328] system 00:08: [io  0x0cd4-0x0cd5] has been reserved
[    0.559329] system 00:08: [io  0x0cd6-0x0cd7] has been reserved
[    0.559331] system 00:08: [io  0x0cd8-0x0cdf] has been reserved
[    0.559333] system 00:08: [io  0x0800-0x089f] has been reserved
[    0.559335] system 00:08: [io  0x0b20-0x0b2f] has been reserved
[    0.559336] system 00:08: [io  0x0900-0x090f] has been reserved
[    0.559341] system 00:08: [io  0x0910-0x091f] has been reserved
[    0.559343] system 00:08: [io  0xfe00-0xfefe] has been reserved
[    0.559345] system 00:08: [mem 0xffb80000-0xffbfffff] has been reserved
[    0.559347] system 00:08: [mem 0xfec10000-0xfec1001f] has been reserved
[    0.559351] system 00:09: [io  0x0e00-0x0e0f] has been reserved
[    0.559353] system 00:09: [io  0x0e80-0x0e8f] has been reserved
[    0.559354] system 00:09: [io  0x0f40-0x0f4f] has been reserved
[    0.559356] system 00:09: [io  0x0a30-0x0a3f] has been reserved
[    0.559360] system 00:0b: [mem 0xe0000000-0xefffffff] has been reserved
[    0.559363] system 00:0c: [mem 0xfec00000-0xffffffff] could not be reserved
[    0.564796] pci 0000:00:02.0: PCI bridge to [bus 01-01]
[    0.564799] pci 0000:00:02.0:   bridge window [io  0xd000-0xdfff]
[    0.564802] pci 0000:00:02.0:   bridge window [mem 0xfd000000-0xfe9fffff]
[    0.564805] pci 0000:00:02.0:   bridge window [mem 0xce000000-0xdfffffff 64bit pref]
[    0.564808] pci 0000:00:07.0: PCI bridge to [bus 02-02]
[    0.564810] pci 0000:00:07.0:   bridge window [io  0xe000-0xefff]
[    0.564813] pci 0000:00:07.0:   bridge window [mem 0xfea00000-0xfeafffff]
[    0.564815] pci 0000:00:07.0:   bridge window [mem 0xfbf00000-0xfbffffff 64bit pref]
[    0.564819] pci 0000:00:14.4: PCI bridge to [bus 03-03]
[    0.564820] pci 0000:00:14.4:   bridge window [io  disabled]
[    0.564825] pci 0000:00:14.4:   bridge window [mem 0xfeb00000-0xfebfffff]
[    0.564828] pci 0000:00:14.4:   bridge window [mem pref disabled]
[    0.564840]   alloc irq_desc for 18 on node 0
[    0.564841]   alloc kstat_irqs on node 0
[    0.564846] pci 0000:00:02.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.564850] pci 0000:00:02.0: setting latency timer to 64
[    0.564854]   alloc irq_desc for 19 on node 0
[    0.564855]   alloc kstat_irqs on node 0
[    0.564858] pci 0000:00:07.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.564860] pci 0000:00:07.0: setting latency timer to 64
[    0.564868] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.564869] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.564871] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.564873] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff]
[    0.564874] pci_bus 0000:00: resource 8 [mem 0xc8000000-0xdfffffff]
[    0.564876] pci_bus 0000:00: resource 9 [mem 0xf0000000-0xfebfffff]
[    0.564878] pci_bus 0000:01: resource 0 [io  0xd000-0xdfff]
[    0.564880] pci_bus 0000:01: resource 1 [mem 0xfd000000-0xfe9fffff]
[    0.564881] pci_bus 0000:01: resource 2 [mem 0xce000000-0xdfffffff 64bit pref]
[    0.564883] pci_bus 0000:02: resource 0 [io  0xe000-0xefff]
[    0.564885] pci_bus 0000:02: resource 1 [mem 0xfea00000-0xfeafffff]
[    0.564887] pci_bus 0000:02: resource 2 [mem 0xfbf00000-0xfbffffff 64bit pref]
[    0.564889] pci_bus 0000:03: resource 1 [mem 0xfeb00000-0xfebfffff]
[    0.564890] pci_bus 0000:03: resource 4 [io  0x0000-0x0cf7]
[    0.564892] pci_bus 0000:03: resource 5 [io  0x0d00-0xffff]
[    0.564894] pci_bus 0000:03: resource 6 [mem 0x000a0000-0x000bffff]
[    0.564895] pci_bus 0000:03: resource 7 [mem 0x000d0000-0x000dffff]
[    0.564897] pci_bus 0000:03: resource 8 [mem 0xc8000000-0xdfffffff]
[    0.564899] pci_bus 0000:03: resource 9 [mem 0xf0000000-0xfebfffff]
[    0.564927] NET: Registered protocol family 2
[    0.565047] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.565981] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.568248] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.568525] TCP: Hash tables configured (established 524288 bind 65536)
[    0.568527] TCP reno registered
[    0.568537] UDP hash table entries: 2048 (order: 4, 65536 bytes)
[    0.568566] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
[    0.568658] NET: Registered protocol family 1
[    0.727010] Freeing initrd memory: 10748k freed
[    0.732622] pci 0000:01:00.0: Boot video device
[    0.732639] PCI: CLS 64 bytes, default 64
[    0.733321] PCI-DMA: Disabling AGP.
[    0.733398] PCI-DMA: aperture base @ 20000000 size 65536 KB
[    0.733399] PCI-DMA: using GART IOMMU.
[    0.733402] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture
[    0.736034] Scanning for low memory corruption every 60 seconds
[    0.736133] audit: initializing netlink socket (disabled)
[    0.736148] type=2000 audit(1293825538.730:1): initialized
[    0.745672] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.746676] VFS: Disk quotas dquot_6.5.2
[    0.746714] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.747153] fuse init (API version 7.14)
[    0.747205] msgmni has been set to 7918
[    0.749023] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.749026] io scheduler noop registered
[    0.749027] io scheduler deadline registered
[    0.749057] io scheduler cfq registered (default)
[    0.749167] pcieport 0000:00:02.0: setting latency timer to 64
[    0.749189]   alloc irq_desc for 40 on node 0
[    0.749190]   alloc kstat_irqs on node 0
[    0.749197] pcieport 0000:00:02.0: irq 40 for MSI/MSI-X
[    0.749276] pcieport 0000:00:07.0: setting latency timer to 64
[    0.749296]   alloc irq_desc for 41 on node 0
[    0.749297]   alloc kstat_irqs on node 0
[    0.749301] pcieport 0000:00:07.0: irq 41 for MSI/MSI-X
[    0.749358] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.749376] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.749493] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.749502] ACPI: Power Button [PWRB]
[    0.749530] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.749532] ACPI: Power Button [PWRF]
[    0.749735] ACPI: acpi_idle registered with cpuidle
[    0.752571] thermal LNXTHERM:01: registered as thermal_zone0
[    0.752576] ACPI: Thermal Zone [THRM] (35 C)
[    0.752610] ERST: Table is not found!
[    0.752754] Linux agpgart interface v0.103
[    0.752757] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.752863] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.753104] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.753789] brd: module loaded
[    0.754099] loop: module loaded
[    0.754337]   alloc irq_desc for 16 on node 0
[    0.754338]   alloc kstat_irqs on node 0
[    0.754344] pata_acpi 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.754369] pata_acpi 0000:00:14.1: setting latency timer to 64
[    0.754623] Fixed MDIO Bus: probed
[    0.754644] PPP generic driver version 2.4.2
[    0.754685] tun: Universal TUN/TAP device driver, 1.6
[    0.754687] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.754743] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.754772]   alloc irq_desc for 17 on node 0
[    0.754773]   alloc kstat_irqs on node 0
[    0.754776] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.754808] ehci_hcd 0000:00:12.2: EHCI Host Controller
[    0.754839] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
[    0.754875] ehci_hcd 0000:00:12.2: debug port 1
[    0.754895] ehci_hcd 0000:00:12.2: irq 17, io mem 0xfcfff000
[    0.772540] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00
[    0.772661] hub 1-0:1.0: USB hub found
[    0.772664] hub 1-0:1.0: 6 ports detected
[    0.772775] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.772794] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    0.772820] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2
[    0.772846] ehci_hcd 0000:00:13.2: debug port 1
[    0.772868] ehci_hcd 0000:00:13.2: irq 19, io mem 0xfcffa800
[    0.792507] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    0.792631] hub 2-0:1.0: USB hub found
[    0.792634] hub 2-0:1.0: 6 ports detected
[    0.792717] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.792767] ohci_hcd 0000:00:12.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.792789] ohci_hcd 0000:00:12.0: OHCI Host Controller
[    0.792816] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 3
[    0.792841] ohci_hcd 0000:00:12.0: irq 16, io mem 0xfcffe000
[    0.856638] hub 3-0:1.0: USB hub found
[    0.856645] hub 3-0:1.0: 3 ports detected
[    0.856756] ohci_hcd 0000:00:12.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.856774] ohci_hcd 0000:00:12.1: OHCI Host Controller
[    0.856801] ohci_hcd 0000:00:12.1: new USB bus registered, assigned bus number 4
[    0.856818] ohci_hcd 0000:00:12.1: irq 16, io mem 0xfcffd000
[    0.916637] hub 4-0:1.0: USB hub found
[    0.916644] hub 4-0:1.0: 3 ports detected
[    0.916755] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.916775] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    0.916803] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 5
[    0.916829] ohci_hcd 0000:00:13.0: irq 18, io mem 0xfcffc000
[    0.976640] hub 5-0:1.0: USB hub found
[    0.976647] hub 5-0:1.0: 3 ports detected
[    0.976760] ohci_hcd 0000:00:13.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.976779] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    0.976806] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 6
[    0.976823] ohci_hcd 0000:00:13.1: irq 18, io mem 0xfcffb000
[    1.036651] hub 6-0:1.0: USB hub found
[    1.036658] hub 6-0:1.0: 3 ports detected
[    1.036769] ohci_hcd 0000:00:14.5: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.036791] ohci_hcd 0000:00:14.5: OHCI Host Controller
[    1.036818] ohci_hcd 0000:00:14.5: new USB bus registered, assigned bus number 7
[    1.036835] ohci_hcd 0000:00:14.5: irq 18, io mem 0xfcff9000
[    1.084156] hub 7-0:1.0: USB hub found
[    1.084162] hub 7-0:1.0: 2 ports detected
[    1.084246] uhci_hcd: USB Universal Host Controller Interface driver
[    1.084335] PNP: No PS/2 controller found. Probing ports directly.
[    1.084730] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.084737] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.084812] mice: PS/2 mouse device common for all mice
[    1.084886] rtc_cmos 00:02: RTC can wake from S4
[    1.084913] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    1.084935] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    1.085014] device-mapper: uevent: version 1.0.3
[    1.085092] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: dm-devel@redhat.com
[    1.085164] device-mapper: multipath: version 1.1.1 loaded
[    1.085166] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.085312] cpuidle: using governor ladder
[    1.085313] cpuidle: using governor menu
[    1.085493] TCP cubic registered
[    1.085577] NET: Registered protocol family 10
[    1.085832] lo: Disabled Privacy Extensions
[    1.085971] NET: Registered protocol family 17
[    1.086012] powernow-k8: Found 1 AMD Athlon(tm) II X3 435 Processor (3 cpu cores) (version 2.20.00)
[    1.086047] powernow-k8:    0 : pstate 0 (2900 MHz)
[    1.086048] powernow-k8:    1 : pstate 1 (2200 MHz)
[    1.086049] powernow-k8:    2 : pstate 2 (1700 MHz)
[    1.086050] powernow-k8:    3 : pstate 3 (800 MHz)
[    1.086315] PM: Resume from disk failed.
[    1.086323] registered taskstats version 1
[    1.086548]   Magic number: 6:825:1002
[    1.086578] pnp 00:04: hash matches
[    1.086628] rtc_cmos 00:02: setting system clock to 2010-12-31 19:58:59 UTC (1293825539)
[    1.086630] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.086631] EDD information not available.
[    1.086681] Freeing unused kernel memory: 908k freed
[    1.086883] Write protecting the kernel read-only data: 10240k
[    1.086995] Freeing unused kernel memory: 412k freed
[    1.087175] Freeing unused kernel memory: 1644k freed
[    1.101095] udev[122]: starting version 163
[    1.145138] scsi0 : pata_atiixp
[    1.145255] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.145272] r8169 0000:02:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.145318] r8169 0000:02:00.0: setting latency timer to 64
[    1.145350]   alloc irq_desc for 42 on node 0
[    1.145352]   alloc kstat_irqs on node 0
[    1.145363] r8169 0000:02:00.0: irq 42 for MSI/MSI-X
[    1.148384] r8169 0000:02:00.0: eth0: RTL8168d/8111d at 0xffffc900110ca000, 00:30:67:41:0a:91, XID 081000c0 IRQ 42
[    1.199099] scsi1 : pata_atiixp
[    1.200095] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xff00 irq 14
[    1.200098] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xff08 irq 15
[    1.200177] ahci 0000:00:11.0: version 3.0
[    1.200193]   alloc irq_desc for 22 on node 0
[    1.200195]   alloc kstat_irqs on node 0
[    1.200201] ahci 0000:00:11.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    1.200282]   alloc irq_desc for 43 on node 0
[    1.200283]   alloc kstat_irqs on node 0
[    1.200297] ahci 0000:00:11.0: irq 43 for MSI/MSI-X
[    1.200388] ahci 0000:00:11.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[    1.200391] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part ccc 
[    1.200619] scsi2 : ahci
[    1.200705] scsi3 : ahci
[    1.200751] scsi4 : ahci
[    1.200794] scsi5 : ahci
[    1.200882] ata3: SATA max UDMA/133 abar m1024@0xfcfff800 port 0xfcfff900 irq 43
[    1.200885] ata4: SATA max UDMA/133 abar m1024@0xfcfff800 port 0xfcfff980 irq 43
[    1.200888] ata5: SATA max UDMA/133 abar m1024@0xfcfff800 port 0xfcfffa00 irq 43
[    1.200890] ata6: SATA max UDMA/133 abar m1024@0xfcfff800 port 0xfcfffa80 irq 43
[    1.340041] usb 5-1: new low speed USB device using ohci_hcd and address 2
[    1.380368] ata1.00: ATAPI: ASUS    DRW-24B1ST, 1.01, max UDMA/100
[    1.420629] ata1.00: configured for UDMA/100
[    1.440670] ata2.00: ATA-7: ST3250823A, 3.02, max UDMA/100
[    1.440673] ata2.00: 488397168 sectors, multi 16: LBA48 
[    1.440693] ata2.01: ATAPI: SAMSUNG DVD-ROM SD-616E, F501, max UDMA/33
[    1.442891] scsi 0:0:0:0: CD-ROM            ASUS     DRW-24B1ST       1.01 PQ: 0 ANSI: 5
[    1.460595] ata2.00: configured for UDMA/100
[    1.482182] ata2.01: configured for UDMA/33
[    1.487069] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.487072] Uniform CD-ROM driver Revision: 3.20
[    1.487172] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    1.487228] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    1.487395] scsi 1:0:0:0: Direct-Access     ATA      ST3250823A       3.02 PQ: 0 ANSI: 5
[    1.487521] sd 1:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    1.487535] sd 1:0:0:0: Attached scsi generic sg1 type 0
[    1.488008] scsi 1:0:1:0: CD-ROM            SAMSUNG  DVD-ROM SD-616E  F501 PQ: 0 ANSI: 5
[    1.489026] sd 1:0:0:0: [sda] Write Protect is off
[    1.489030] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.489803] sr1: scsi3-mmc drive: 1x/48x cd/rw xa/form2 cdda tray
[    1.489807] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.489890] sr 1:0:1:0: Attached scsi CD-ROM sr1
[    1.489928] sr 1:0:1:0: Attached scsi generic sg2 type 5
[    1.489943]  sda: sda1
[    1.507190] sd 1:0:0:0: [sda] Attached SCSI disk
[    1.560046] ata4: SATA link down (SStatus 0 SControl 300)
[    1.560912] ata6: SATA link down (SStatus 0 SControl 300)
[    1.572922] usbcore: registered new interface driver hiddev
[    1.579761] input: CHICONY USB Keyboard as /devices/pci0000:00/0000:00:13.0/usb5/5-1/5-1:1.0/input/input2
[    1.579833] generic-usb 0003:04F2:0111.0001: input,hidraw0: USB HID v1.10 Keyboard [CHICONY USB Keyboard] on usb-0000:00:13.0-1/input0
[    1.597646] input: CHICONY USB Keyboard as /devices/pci0000:00/0000:00:13.0/usb5/5-1/5-1:1.1/input/input3
[    1.597738] generic-usb 0003:04F2:0111.0002: input,hiddev96,hidraw1: USB HID v1.10 Device [CHICONY USB Keyboard] on usb-0000:00:13.0-1/input1
[    1.597757] usbcore: registered new interface driver usbhid
[    1.597758] usbhid: USB HID core driver
[    1.671703] usb 5-2: new low speed USB device using ohci_hcd and address 3
[    1.750068] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.750073] ata5: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.751176] ata5.00: ATA-8: ST31000528AS, CC38, max UDMA/133
[    1.751179] ata5.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    1.752465] ata5.00: configured for UDMA/133
[    1.752546] ata3.00: ATA-7: Patriot PS-100 32GB SSD, VER2.000, max UDMA/133
[    1.752548] ata3.00: 60292512 sectors, multi 0: LBA48 
[    1.755821] ata3.00: configured for UDMA/133
[    1.770167] scsi 2:0:0:0: Direct-Access     ATA      Patriot PS-100 3 VER2 PQ: 0 ANSI: 5
[    1.770294] sd 2:0:0:0: [sdb] 60292512 512-byte logical blocks: (30.8 GB/28.7 GiB)
[    1.770299] sd 2:0:0:0: Attached scsi generic sg3 type 0
[    1.770340] sd 2:0:0:0: [sdb] Write Protect is off
[    1.770345] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    1.770373] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.770465] scsi 4:0:0:0: Direct-Access     ATA      ST31000528AS     CC38 PQ: 0 ANSI: 5
[    1.770521]  sdb:
[    1.770564] sd 4:0:0:0: [sdc] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    1.770588] sd 4:0:0:0: Attached scsi generic sg4 type 0
[    1.770602] sd 4:0:0:0: [sdc] Write Protect is off
[    1.770605] sd 4:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    1.770625] sd 4:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.770752]  sdc: sdb1 sdb2 < sdb5 >
[    1.773592] sd 2:0:0:0: [sdb] Attached SCSI disk
[    1.783919]  sdc1
[    1.784207] sd 4:0:0:0: [sdc] Attached SCSI disk
[    1.862742] input: Logitech USB Optical Mouse as /devices/pci0000:00/0000:00:13.0/usb5/5-2/5-2:1.0/input/input4
[    1.862861] generic-usb 0003:046D:C00C.0003: input,hidraw2: USB HID v1.10 Mouse [Logitech USB Optical Mouse] on usb-0000:00:13.0-2/input0
[    1.879254] EXT4-fs (sdb1): mounted filesystem with ordered data mode. Opts: (null)
[    5.417292] Adding 3777532k swap on /dev/sdb5.  Priority:-1 extents:1 across:3777532k SS
[    5.422516] udev[399]: starting version 163
[    5.455767] lp: driver loaded but no devices found
[    5.551138] type=1400 audit(1293825543.958:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=575 comm="apparmor_parser"
[    5.551342] type=1400 audit(1293825543.958:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=575 comm="apparmor_parser"
[    5.551456] type=1400 audit(1293825543.958:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=575 comm="apparmor_parser"
[    5.568308] ACPI: resource piix4_smbus [io  0x0b00-0x0b07] conflicts with ACPI region SOR1 [mem 0x00000b00-0x00000b0f disabled]
[    5.568311] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    5.572249] EDAC MC: Ver: 2.1.0 Dec  2 2010
[    5.588443] EDAC amd64_edac:  Ver: 3.3.0 Dec  2 2010
[    5.590916] parport_pc 00:05: reported by Plug and Play ACPI
[    5.591090] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[    5.592403] cfg80211: Calling CRDA to update world regulatory domain
[    5.604025] EDAC amd64: This node reports that Memory ECC is currently disabled, set F3x44[22] (0000:00:18.3).
[    5.604034] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
[    5.604036]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
[    5.604037]  (Note that use of the override may cause unknown side effects.)
[    5.604057] amd64_edac: probe of 0000:00:18.2 failed with error -22
[    5.619666] cfg80211: World regulatory domain updated:
[    5.619669]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[    5.619671]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    5.619673]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    5.619675]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    5.619677]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    5.619678]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    5.630838] nvidia: module license 'NVIDIA' taints kernel.
[    5.630841] Disabling lock debugging due to kernel taint
[    5.631725] ppdev: user-space parallel port driver
[    5.642677]   alloc irq_desc for 20 on node 0
[    5.642680]   alloc kstat_irqs on node 0
[    5.642687] rt61pci 0000:03:05.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    5.670997] lp0: using parport0 (interrupt-driven).
[    5.695938] phy0: Selected rate control algorithm 'minstrel'
[    5.696362] Registered led device: rt61pci-phy0::radio
[    5.696372] Registered led device: rt61pci-phy0::assoc
[    5.702846] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    5.770065] hda_codec: ALC662 rev1: BIOS auto-probing.
[    5.777776] HDA Intel 0000:01:00.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    5.777779] hda_intel: Disable MSI for Nvidia chipset
[    5.777807] HDA Intel 0000:01:00.1: setting latency timer to 64
[    5.813527] EXT4-fs (sdb1): re-mounted. Opts: errors=remount-ro
[    5.939695] EXT4-fs (sdc1): mounted filesystem with ordered data mode. Opts: (null)
[    5.983502] type=1400 audit(1293825544.388:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=963 comm="apparmor_parser"
[    5.983709] type=1400 audit(1293825544.388:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=963 comm="apparmor_parser"
[    5.983823] type=1400 audit(1293825544.388:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=963 comm="apparmor_parser"
[    5.986002] type=1400 audit(1293825544.388:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=964 comm="apparmor_parser"
[    5.986264] type=1400 audit(1293825544.388:9): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=964 comm="apparmor_parser"
[    5.988787] type=1400 audit(1293825544.388:10): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=967 comm="apparmor_parser"
[    5.990429] type=1400 audit(1293825544.398:11): apparmor="STATUS" operation="profile_load" name="/usr/sbin/mysqld-akonadi" pid=965 comm="apparmor_parser"
[    5.996119] r8169 0000:02:00.0: eth0: link up
[    5.996127] r8169 0000:02:00.0: eth0: link up
[    6.110613] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    6.375175] EXT4-fs (sdb1): re-mounted. Opts: errors=remount-ro,commit=0
[    6.378826] EXT4-fs (sdc1): re-mounted. Opts: commit=0
[    7.820395] nvidia 0000:01:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    7.820403] nvidia 0000:01:00.0: setting latency timer to 64
[    7.820407] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[    7.820558] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  260.19.06  Mon Sep 13 04:29:19 PDT 2010
[   11.312309] EXT4-fs (sdb1): re-mounted. Opts: errors=remount-ro,commit=0
[   11.314278] EXT4-fs (sdc1): re-mounted. Opts: commit=0
[   16.546865] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
[   16.860020] eth0: no IPv6 routers present
[   47.033733] NVRM: os_raise_smp_barrier(), invalid context!
[   47.051089] NVRM: os_raise_smp_barrier(), invalid context!
[  171.753420] npviewer.bin[1891]: segfault at 0 ip 00000000f6182ed1 sp 00000000ffb01d40 error 4 in libflashplayer.so[f5de3000+b2e000]
[  178.715152] NVRM: os_raise_smp_barrier(), invalid context!
[  178.723468] NVRM: os_raise_smp_barrier(), invalid context!
[  191.723034] NVRM: os_raise_smp_barrier(), invalid context!
[  191.732467] NVRM: os_raise_smp_barrier(), invalid context!
[  415.191968] npviewer.bin[1943]: segfault at f584004c ip 00000000f617aee7 sp 00000000ffcd5d60 error 4 in libflashplayer.so[f5ddb000+b2e000]
[  435.574077] NVRM: os_raise_smp_barrier(), invalid context!
[  435.583317] NVRM: os_raise_smp_barrier(), invalid context!
[  483.413282] NVRM: os_raise_smp_barrier(), invalid context!
[  483.421599] NVRM: os_raise_smp_barrier(), invalid context!

```

---

### Post by ikt on 2010-12-31
> **mechanizedmedic said:**
> is there anything i might need to change in there?

If there's an option just for defaults or fail safe defaults? I'd go with that just to see if it helps, most of the time ubuntu freezing is a hardware issue.

---

### Post by mechanizedmedic on 2010-12-31
i ran memtest until it gave pass:1 fail:0

should i enable ECC?

---

### Post by ikt on 2010-12-31
> **mechanizedmedic said:**
> i ran memtest until it gave pass:1 fail:0

should i enable ECC?

nah, afaik eec is a more expensive type of ram and usually used in servers.

---

### Post by mechanizedmedic on 2011-01-01
fixed the problem... i installed KDE! hahaha! :D

EDIT: i should be honest... it was the graphics card going bad AND something with the nVidia driver. after i updated the driver the kernel error spam went away and things ran a little smoother. the card going bad caused the freezing issue.

---

