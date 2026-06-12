---
title: "wireless network card became disabled"
date: 2013-11-27
forum: Networking &amp; Wireless
---

### Post by Pandanus on 2013-11-27
Dear community,

unfortunately I got problems with my wireless recently, it has always been working ok, but one day last week it was down after waking up from a suspend. I fiddled around, but couldn't find a reason, and after a reboot it was up again, so I didn't think to much about it any longer. Now it is down again, and doesn't come up after rebooting. I really have no idea what could be wrong, and any pointers or help would be really appreciated.
The machine is a netbook from Packard Bell, dot s (DOT_SE-710UK) and I'm running 32bit Xubuntu 12.04.

Apparently the wireless isn't detected at all when the connection is down.

uname -a
```

Linux The-Dot 3.2.0-56-generic #86-Ubuntu SMP Wed Oct 23 17:31:43 UTC 2013 i686 i686 i386 GNU/Linux

```

sudo lshw -C network
```
  *-network
       description: Ethernet interface
       product: AR8152 v1.1 Fast Ethernet
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: c1
       serial: 1c:75:08:9f:92:be
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:45 memory:97000000-9703ffff ioport:5000(size=128)

```

lspci -nn
```
00:00.0 Host bridge [0600]: Intel Corporation Atom Processor D4xx/D5xx/N4xx/N5xx DMI Bridge [8086:a010] (rev 02)
00:02.0 VGA compatible controller [0300]: Intel Corporation Atom Processor D4xx/D5xx/N4xx/N5xx Integrated Graphics Controller [8086:a011] (rev 02)
00:02.1 Display controller [0380]: Intel Corporation Atom Processor D4xx/D5xx/N4xx/N5xx Integrated Graphics Controller [8086:a012] (rev 02)
00:1b.0 Audio device [0403]: Intel Corporation NM10/ICH7 Family High Definition Audio Controller [8086:27d8] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation NM10/ICH7 Family PCI Express Port 1 [8086:27d0] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation NM10/ICH7 Family PCI Express Port 2 [8086:27d2] (rev 02)
00:1d.0 USB controller [0c03]: Intel Corporation NM10/ICH7 Family USB UHCI Controller #1 [8086:27c8] (rev 02)
00:1d.1 USB controller [0c03]: Intel Corporation NM10/ICH7 Family USB UHCI Controller #2 [8086:27c9] (rev 02)
00:1d.2 USB controller [0c03]: Intel Corporation NM10/ICH7 Family USB UHCI Controller #3 [8086:27ca] (rev 02)
00:1d.3 USB controller [0c03]: Intel Corporation NM10/ICH7 Family USB UHCI Controller #4 [8086:27cb] (rev 02)
00:1d.7 USB controller [0c03]: Intel Corporation NM10/ICH7 Family USB2 EHCI Controller [8086:27cc] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation NM10 Family LPC Controller [8086:27bc] (rev 02)
00:1f.2 SATA controller [0106]: Intel Corporation NM10/ICH7 Family SATA Controller [AHCI mode] [8086:27c1] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation NM10/ICH7 Family SMBus Controller [8086:27da] (rev 02)
01:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8152 v1.1 Fast Ethernet [1969:2060] (rev c1)
```

dmesg
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.2.0-56-generic (buildd@batsu) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #86-Ubuntu SMP Wed Oct 23 17:31:43 UTC 2013 (Ubuntu 3.2.0-56.86-generic 3.2.51)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] Disabled fast string operations
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007f494000 (usable)
[    0.000000]  BIOS-e820: 000000007f494000 - 000000007f4bf000 (reserved)
[    0.000000]  BIOS-e820: 000000007f4bf000 - 000000007f577000 (usable)
[    0.000000]  BIOS-e820: 000000007f577000 - 000000007f5bf000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007f5bf000 - 000000007f5ec000 (usable)
[    0.000000]  BIOS-e820: 000000007f5ec000 - 000000007f5ff000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007f5ff000 - 000000007f600000 (usable)
[    0.000000]  BIOS-e820: 000000007f600000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed20000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffe00000 - 0000000100000000 (reserved)
[    0.000000] Notice: NX (Execute Disable) protection cannot be enabled in hardware: non-PAE kernel!
[    0.000000] NX (Execute Disable) protection: approximated by x86 segment limits
[    0.000000] SMBIOS 2.6 present.
[    0.000000] DMI: Packard Bell DOT SE/SJE02_PT, BIOS V3.12(DDR3) 12/16/2010
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x7f600 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-DFFFF write-through
[    0.000000]   E0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0FFE00000 mask 0FFE00000 write-protect
[    0.000000]   1 base 000000000 mask 0C0000000 write-back
[    0.000000]   2 base 040000000 mask 0C0000000 write-back
[    0.000000]   3 base 07F800000 mask 0FF800000 uncachable
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] initial memory mapped : 0 - 01c00000
[    0.000000] Base memory trampoline at [c009b000] 9b000 size 16384
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 1bf8000-1c00000
[    0.000000] RAMDISK: 364e0000 - 37268000
[    0.000000] ACPI: RSDP 000fe020 00024 (v02 ACRSYS)
[    0.000000] ACPI: XSDT 7f5fe120 00064 (v01 ACRSYS ACRPRDCT 00000001      01000013)
[    0.000000] ACPI: FACP 7f5fd000 000F4 (v04 ACRSYS ACRPRDCT 00000001 1025 01000013)
[    0.000000] ACPI: DSDT 7f5f1000 08DCF (v01 ACRSYS ACRPRDCT 00000001 1025 01000013)
[    0.000000] ACPI: FACS 7f584000 00040
[    0.000000] ACPI: HPET 7f5fc000 00038 (v01 ACRSYS ACRPRDCT 00000001 1025 01000013)
[    0.000000] ACPI: APIC 7f5fb000 00078 (v02 ACRSYS ACRPRDCT 00000001 1025 01000013)
[    0.000000] ACPI: MCFG 7f5fa000 0003C (v01 ACRSYS ACRPRDCT 00000001 1025 01000013)
[    0.000000] ACPI: SLIC 7f5f0000 00176 (v01 ACRSYS ACRPRDCT 00000001 1025 01000013)
[    0.000000] ACPI: BOOT 7f5ef000 00028 (v01 ACRSYS ACRPRDCT 00000001 1025 01000013)
[    0.000000] ACPI: SSDT 7f5ed000 00655 (v01  PmRef    CpuPm 00003000 INTL 20051117)
[    0.000000] ACPI: WDAT 7f5ec000 00194 (v01 INSYDE INSYDE   00000001 MSFT 01000013)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 1150MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0007f600
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[5] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0007f494
[    0.000000]     0: 0x0007f4bf -> 0x0007f577
[    0.000000]     0: 0x0007f5bf -> 0x0007f5ec
[    0.000000]     0: 0x0007f5ff -> 0x0007f600
[    0.000000] On node 0 totalpages: 521481
[    0.000000] free_area_init_node: node 0, pgdat c182bd80, node_mem_map f54f0200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2301 pages used for memmap
[    0.000000]   HighMem zone: 291967 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 80000000:60000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 13 pages/cpu @f77bd000 s31616 r0 d21632 u53248
[    0.000000] pcpu-alloc: s31616 r0 d21632 u53248 alloc=13*4096
[    0.000000] pcpu-alloc: [0] 0 [0] 1 [0] 2 [0] 3 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 517404
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-56-generic root=UUID=76e61700-9c91-40f6-84b6-35a4552819d4 ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] allocated 8347392 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0007f600)
[    0.000000] Memory: 2036484k/2086912k available (5637k kernel code, 49440k reserved, 2779k data, 716k init, 1177072k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc1839000 - 0xc18ec000   ( 716 kB)
[    0.000000]       .data : 0xc1581784 - 0xc18384c0   (2779 kB)
[    0.000000]       .text : 0xc1000000 - 0xc1581784   (5637 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:2304 nr_irqs:712 16
[    0.000000] CPU 0 irqstacks, hard=f480a000 soft=f480c000
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1496.418 MHz processor.
[    0.004004] Calibrating delay loop (skipped), value calculated using timer frequency.. 2992.83 BogoMIPS (lpj=5985672)
[    0.004018] pid_max: default: 32768 minimum: 301
[    0.004079] Security Framework initialized
[    0.004122] AppArmor: AppArmor initialized
[    0.004127] Yama: becoming mindful.
[    0.004262] Mount-cache hash table entries: 512
[    0.004562] Initializing cgroup subsys cpuacct
[    0.004579] Initializing cgroup subsys memory
[    0.004599] Initializing cgroup subsys devices
[    0.004606] Initializing cgroup subsys freezer
[    0.004612] Initializing cgroup subsys blkio
[    0.004628] Initializing cgroup subsys perf_event
[    0.004678] Disabled fast string operations
[    0.004688] CPU: Physical Processor ID: 0
[    0.004693] CPU: Processor Core ID: 0
[    0.004700] mce: CPU supports 5 MCE banks
[    0.004714] CPU0: Thermal monitoring enabled (TM2)
[    0.004723] using mwait in idle threads.
[    0.011924] ACPI: Core revision 20110623
[    0.028031] ftrace: allocating 25521 entries in 50 pages
[    0.036107] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.036602] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.078710] CPU0: Intel(R) Atom(TM) CPU N550   @ 1.50GHz stepping 0a
[    0.080004] Performance Events: PEBS fmt0+, Atom events, Intel PMU driver.
[    0.080004] ... version:                3
[    0.080004] ... bit width:              40
[    0.080004] ... generic registers:      2
[    0.080004] ... value mask:             000000ffffffffff
[    0.080004] ... max period:             000000007fffffff
[    0.080004] ... fixed-purpose events:   3
[    0.080004] ... event mask:             0000000700000003
[    0.080004] NMI watchdog enabled, takes one hw-pmu counter.
[    0.080004] CPU 1 irqstacks, hard=f4912000 soft=f4914000
[    0.080004] Booting Node   0, Processors  #1
[    0.080004] smpboot cpu 1: start_ip = 9b000
[    0.008000] Initializing CPU#1
[    0.008000] Disabled fast string operations
[    0.168076] NMI watchdog enabled, takes one hw-pmu counter.
[    0.168355] CPU 2 irqstacks, hard=f4920000 soft=f4922000
[    0.168361]  #2
[    0.168366] smpboot cpu 2: start_ip = 9b000
[    0.008000] Initializing CPU#2
[    0.008000] Disabled fast string operations
[    0.260015] TSC synchronization [CPU#0 -> CPU#2]:
[    0.260015] Measured 135 cycles TSC warp between CPUs, turning off TSC clock.
[    0.260015] Marking TSC unstable due to check_tsc_sync_source failed
[    0.260066] NMI watchdog enabled, takes one hw-pmu counter.
[    0.260321] CPU 3 irqstacks, hard=f492e000 soft=f4938000
[    0.260327]  #3 Ok.
[    0.260332] smpboot cpu 3: start_ip = 9b000
[    0.008000] Initializing CPU#3
[    0.008000] Disabled fast string operations
[    0.348145] NMI watchdog enabled, takes one hw-pmu counter.
[    0.348213] Brought up 4 CPUs
[    0.348220] Total of 4 processors activated (11970.87 BogoMIPS).
[    0.350964] devtmpfs: initialized
[    0.350964] EVM: security.selinux
[    0.350964] EVM: security.SMACK64
[    0.350964] EVM: security.capability
[    0.350964] PM: Registering ACPI NVS region at 7f577000 (294912 bytes)
[    0.355228] print_constraints: dummy: 
[    0.355285] RTC time: 12:06:21, date: 11/27/13
[    0.355387] NET: Registered protocol family 16
[    0.355415] Trying to unpack rootfs image as initramfs...
[    0.355940] EISA bus registered
[    0.356102] ACPI: bus type pci registered
[    0.356367] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.356380] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    0.356388] PCI: Using MMCONFIG for extended config space
[    0.356396] PCI: Using configuration type 1 for base access
[    0.362092] bio: create slab <bio-0> at 0
[    0.362092] ACPI: Added _OSI(Module Device)
[    0.362092] ACPI: Added _OSI(Processor Device)
[    0.362092] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.362092] ACPI: Added _OSI(Processor Aggregator Device)
[    0.369442] ACPI: EC: Look up EC in DSDT
[    0.376435] ACPI: Executed 1 blocks of module-level executable AML code
[    0.384200] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.385912] ACPI: SSDT 7f4b7710 006C6 (v01  PmRef  Cpu0Ist 00003000 INTL 20051117)
[    0.388372] ACPI: Dynamic OEM Table Load:
[    0.388387] ACPI: SSDT   (null) 006C6 (v01  PmRef  Cpu0Ist 00003000 INTL 20051117)
[    0.389043] ACPI: SSDT 7f4b5690 00646 (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.390635] ACPI: Dynamic OEM Table Load:
[    0.390649] ACPI: SSDT   (null) 00646 (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.441199] ACPI: SSDT 7f4b6d90 0015F (v01  PmRef    ApIst 00003000 INTL 20051117)
[    0.442937] ACPI: Dynamic OEM Table Load:
[    0.442950] ACPI: SSDT   (null) 0015F (v01  PmRef    ApIst 00003000 INTL 20051117)
[    0.472515] ACPI: SSDT 7f4b6f10 0008D (v01  PmRef    ApCst 00003000 INTL 20051117)
[    0.474172] ACPI: Dynamic OEM Table Load:
[    0.474186] ACPI: SSDT   (null) 0008D (v01  PmRef    ApCst 00003000 INTL 20051117)
[    0.504350] ACPI: Interpreter enabled
[    0.504378] ACPI: (supports S0 S3 S4 S5)
[    0.504487] ACPI: Using IOAPIC for interrupt routing
[    0.654161] ACPI: Power Resource [FN00] (on)
[    0.655724] ACPI: EC: GPE = 0x19, I/O: command/status = 0x66, data = 0x62
[    0.656444] ACPI: No dock devices found.
[    0.656454] HEST: Table not found.
[    0.656470] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.658084] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.660793] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    0.660808] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    0.660820] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.660834] pci_root PNP0A08:00: host bridge window [mem 0x80000000-0xfebfffff]
[    0.660885] pci 0000:00:00.0: [8086:a010] type 0 class 0x000600
[    0.660985] pci 0000:00:02.0: [8086:a011] type 0 class 0x000300
[    0.661012] pci 0000:00:02.0: reg 10: [mem 0x98180000-0x981fffff]
[    0.661030] pci 0000:00:02.0: reg 14: [io  0x60c0-0x60c7]
[    0.661047] pci 0000:00:02.0: reg 18: [mem 0x80000000-0x8fffffff pref]
[    0.661064] pci 0000:00:02.0: reg 1c: [mem 0x98000000-0x980fffff]
[    0.661147] pci 0000:00:02.1: [8086:a012] type 0 class 0x000380
[    0.661171] pci 0000:00:02.1: reg 10: [mem 0x98100000-0x9817ffff]
[    0.661343] pci 0000:00:1b.0: [8086:27d8] type 0 class 0x000403
[    0.661385] pci 0000:00:1b.0: reg 10: [mem 0x98200000-0x98203fff 64bit]
[    0.661540] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.661555] pci 0000:00:1b.0: PME# disabled
[    0.661614] pci 0000:00:1c.0: [8086:27d0] type 1 class 0x000604
[    0.661776] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.661791] pci 0000:00:1c.0: PME# disabled
[    0.661850] pci 0000:00:1c.1: [8086:27d2] type 1 class 0x000604
[    0.662011] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.662025] pci 0000:00:1c.1: PME# disabled
[    0.662091] pci 0000:00:1d.0: [8086:27c8] type 0 class 0x000c03
[    0.662177] pci 0000:00:1d.0: reg 20: [io  0x6080-0x609f]
[    0.662256] pci 0000:00:1d.1: [8086:27c9] type 0 class 0x000c03
[    0.662344] pci 0000:00:1d.1: reg 20: [io  0x6060-0x607f]
[    0.662423] pci 0000:00:1d.2: [8086:27ca] type 0 class 0x000c03
[    0.662509] pci 0000:00:1d.2: reg 20: [io  0x6040-0x605f]
[    0.662586] pci 0000:00:1d.3: [8086:27cb] type 0 class 0x000c03
[    0.662673] pci 0000:00:1d.3: reg 20: [io  0x6020-0x603f]
[    0.662767] pci 0000:00:1d.7: [8086:27cc] type 0 class 0x000c03
[    0.662809] pci 0000:00:1d.7: reg 10: [mem 0x98204400-0x982047ff]
[    0.662968] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.662982] pci 0000:00:1d.7: PME# disabled
[    0.663029] pci 0000:00:1e.0: [8086:2448] type 1 class 0x000604
[    0.663177] pci 0000:00:1f.0: [8086:27bc] type 0 class 0x000601
[    0.663385] pci 0000:00:1f.2: [8086:27c1] type 0 class 0x000106
[    0.663426] pci 0000:00:1f.2: reg 10: [io  0x60b8-0x60bf]
[    0.663450] pci 0000:00:1f.2: reg 14: [io  0x60cc-0x60cf]
[    0.663473] pci 0000:00:1f.2: reg 18: [io  0x60b0-0x60b7]
[    0.663497] pci 0000:00:1f.2: reg 1c: [io  0x60c8-0x60cb]
[    0.663520] pci 0000:00:1f.2: reg 20: [io  0x60a0-0x60af]
[    0.663544] pci 0000:00:1f.2: reg 24: [mem 0x98204000-0x982043ff]
[    0.663634] pci 0000:00:1f.2: PME# supported from D3hot
[    0.663647] pci 0000:00:1f.2: PME# disabled
[    0.663688] pci 0000:00:1f.3: [8086:27da] type 0 class 0x000c05
[    0.663775] pci 0000:00:1f.3: reg 20: [io  0x6000-0x601f]
[    0.663970] pci 0000:01:00.0: [1969:2060] type 0 class 0x000200
[    0.664026] pci 0000:01:00.0: reg 10: [mem 0x97000000-0x9703ffff 64bit]
[    0.664070] pci 0000:01:00.0: reg 18: [io  0x5000-0x507f]
[    0.664260] pci 0000:01:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.664276] pci 0000:01:00.0: PME# disabled
[    0.672089] pci 0000:00:1c.0: PCI bridge to [bus 01-01]
[    0.672105] pci 0000:00:1c.0:   bridge window [io  0x5000-0x5fff]
[    0.672120] pci 0000:00:1c.0:   bridge window [mem 0x97000000-0x97ffffff]
[    0.672139] pci 0000:00:1c.0:   bridge window [mem 0x90000000-0x90ffffff 64bit pref]
[    0.672239] pci 0000:00:1c.1: PCI bridge to [bus 02-02]
[    0.672253] pci 0000:00:1c.1:   bridge window [io  0x4000-0x4fff]
[    0.672267] pci 0000:00:1c.1:   bridge window [mem 0x96000000-0x96ffffff]
[    0.672286] pci 0000:00:1c.1:   bridge window [mem 0x91000000-0x91ffffff 64bit pref]
[    0.672414] pci 0000:00:1e.0: PCI bridge to [bus 05-05] (subtractive decode)
[    0.672441] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.672453] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.672465] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.672477] pci 0000:00:1e.0:   bridge window [mem 0x80000000-0xfebfffff] (subtractive decode)
[    0.672517] pci_bus 0000:00: on NUMA node 0
[    0.672532] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.673105] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP1._PRT]
[    0.673326] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP2._PRT]
[    0.673880]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.674662]  pci0000:00: ACPI _OSC control (0x1c) granted
[    0.686892] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 10 *11 12)
[    0.687145] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 9 *10 11 12)
[    0.687392] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 10 *11 12)
[    0.687638] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 10 *11 12)
[    0.687885] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
[    0.688165] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
[    0.688417] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
[    0.688669] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
[    0.689061] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.689061] vgaarb: loaded
[    0.689061] vgaarb: bridge control possible 0000:00:02.0
[    0.689061] i2c-core: driver [aat2870] using legacy suspend method
[    0.689061] i2c-core: driver [aat2870] using legacy resume method
[    0.689098] SCSI subsystem initialized
[    0.690325] libata version 3.00 loaded.
[    0.690325] usbcore: registered new interface driver usbfs
[    0.690325] usbcore: registered new interface driver hub
[    0.690325] usbcore: registered new device driver usb
[    0.690325] PCI: Using ACPI for IRQ routing
[    0.705067] PCI: pci_cache_line_size set to 64 bytes
[    0.705222] reserve RAM buffer: 000000000009fc00 - 000000000009ffff 
[    0.705233] reserve RAM buffer: 000000007f494000 - 000000007fffffff 
[    0.705244] reserve RAM buffer: 000000007f577000 - 000000007fffffff 
[    0.705254] reserve RAM buffer: 000000007f5ec000 - 000000007fffffff 
[    0.705264] reserve RAM buffer: 000000007f600000 - 000000007fffffff 
[    0.705691] NetLabel: Initializing
[    0.705700] NetLabel:  domain hash size = 128
[    0.705707] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.705747] NetLabel:  unlabeled traffic allowed by default
[    0.705857] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.705857] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.705857] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.720197] Switching to clocksource hpet
[    0.747821] AppArmor: AppArmor Filesystem Enabled
[    0.747913] pnp: PnP ACPI init
[    0.747972] ACPI: bus type pnp registered
[    0.749428] pnp 00:00: [bus 00-ff]
[    0.749442] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.749452] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.749462] pnp 00:00: [io  0x0d00-0xffff window]
[    0.749473] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.749484] pnp 00:00: [mem 0x000c0000-0x000c3fff window]
[    0.749494] pnp 00:00: [mem 0x000c4000-0x000c7fff window]
[    0.749504] pnp 00:00: [mem 0x000c8000-0x000cbfff window]
[    0.749514] pnp 00:00: [mem 0x000cc000-0x000cffff window]
[    0.749525] pnp 00:00: [mem 0x000d0000-0x000d3fff window]
[    0.749535] pnp 00:00: [mem 0x000d4000-0x000d7fff window]
[    0.749545] pnp 00:00: [mem 0x000d8000-0x000dbfff window]
[    0.749556] pnp 00:00: [mem 0x000dc000-0x000dffff window]
[    0.749566] pnp 00:00: [mem 0x000e0000-0x000e3fff window]
[    0.749576] pnp 00:00: [mem 0x000e4000-0x000e7fff window]
[    0.749586] pnp 00:00: [mem 0x000e8000-0x000ebfff window]
[    0.749597] pnp 00:00: [mem 0x000ec000-0x000effff window]
[    0.749615] pnp 00:00: [mem 0x000f0000-0x000fffff window]
[    0.749626] pnp 00:00: [mem 0x80000000-0xfebfffff window]
[    0.749830] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    0.812598] pnp 00:01: [io  0x0068]
[    0.812609] pnp 00:01: [io  0x006c]
[    0.812619] pnp 00:01: [io  0x164e-0x164f]
[    0.812628] pnp 00:01: [io  0x0061]
[    0.812636] pnp 00:01: [io  0x0070]
[    0.812645] pnp 00:01: [io  0x0080]
[    0.812653] pnp 00:01: [io  0x0092]
[    0.812662] pnp 00:01: [io  0x00b2-0x00b3]
[    0.812670] pnp 00:01: [io  0x0063]
[    0.812678] pnp 00:01: [io  0x0065]
[    0.812687] pnp 00:01: [io  0x0067]
[    0.812696] pnp 00:01: [io  0x0600-0x060f]
[    0.812704] pnp 00:01: [io  0x0610]
[    0.812713] pnp 00:01: [io  0x0800-0x080f]
[    0.812722] pnp 00:01: [io  0x0810-0x0817]
[    0.812731] pnp 00:01: [io  0x0400-0x047f]
[    0.812740] pnp 00:01: [io  0x0500-0x053f]
[    0.812749] pnp 00:01: [io  0xff2c-0xff2f]
[    0.812759] pnp 00:01: [mem 0xe0000000-0xefffffff]
[    0.812768] pnp 00:01: [mem 0xfed1c000-0xfed1ffff]
[    0.812778] pnp 00:01: [mem 0xfed14000-0xfed17fff]
[    0.812788] pnp 00:01: [mem 0xfed18000-0xfed18fff]
[    0.812797] pnp 00:01: [mem 0xfed19000-0xfed19fff]
[    0.812807] pnp 00:01: [mem 0xfec00000-0xfec00fff]
[    0.812816] pnp 00:01: [mem 0xfee00000-0xfee00fff]
[    0.813060] system 00:01: [io  0x164e-0x164f] has been reserved
[    0.813076] system 00:01: [io  0x0600-0x060f] has been reserved
[    0.813087] system 00:01: [io  0x0610] has been reserved
[    0.813098] system 00:01: [io  0x0800-0x080f] has been reserved
[    0.813109] system 00:01: [io  0x0810-0x0817] has been reserved
[    0.813120] system 00:01: [io  0x0400-0x047f] has been reserved
[    0.813132] system 00:01: [io  0x0500-0x053f] has been reserved
[    0.813144] system 00:01: [io  0xff2c-0xff2f] has been reserved
[    0.813157] system 00:01: [mem 0xe0000000-0xefffffff] has been reserved
[    0.813169] system 00:01: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.813182] system 00:01: [mem 0xfed14000-0xfed17fff] has been reserved
[    0.813194] system 00:01: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.813206] system 00:01: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.813219] system 00:01: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.813231] system 00:01: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.813246] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.813295] pnp 00:02: [io  0x0000-0x001f]
[    0.813306] pnp 00:02: [io  0x0081-0x0091]
[    0.813315] pnp 00:02: [io  0x0093-0x009f]
[    0.813323] pnp 00:02: [io  0x00c0-0x00df]
[    0.813333] pnp 00:02: [dma 4]
[    0.813454] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.813557] pnp 00:03: [io  0x0070-0x0077]
[    0.813689] pnp 00:03: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.813962] pnp 00:04: [irq 0 disabled]
[    0.813990] pnp 00:04: [irq 8]
[    0.814001] pnp 00:04: [mem 0xfed00000-0xfed003ff]
[    0.814126] pnp 00:04: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.814180] pnp 00:05: [io  0x00f0]
[    0.814200] pnp 00:05: [irq 13]
[    0.814332] pnp 00:05: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.814385] pnp 00:06: [mem 0xff800000-0xffffffff]
[    0.814509] pnp 00:06: Plug and Play ACPI device, IDs INT0800 (active)
[    0.814647] pnp 00:07: [io  0x0060]
[    0.814658] pnp 00:07: [io  0x0064]
[    0.814676] pnp 00:07: [irq 1]
[    0.814805] pnp 00:07: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.815000] pnp 00:08: [irq 12]
[    0.815148] pnp 00:08: Plug and Play ACPI device, IDs SYN1b1c SYN1b00 SYN0002 PNP0f13 (active)
[    0.815719] pnp: PnP ACPI: found 9 devices
[    0.815729] ACPI: ACPI bus type pnp unregistered
[    0.815741] PnPBIOS: Disabled by ACPI PNP
[    0.861982] PCI: max bus depth: 1 pci_try_num: 2
[    0.862050] pci 0000:00:1c.0: PCI bridge to [bus 01-01]
[    0.862064] pci 0000:00:1c.0:   bridge window [io  0x5000-0x5fff]
[    0.862081] pci 0000:00:1c.0:   bridge window [mem 0x97000000-0x97ffffff]
[    0.862097] pci 0000:00:1c.0:   bridge window [mem 0x90000000-0x90ffffff 64bit pref]
[    0.862115] pci 0000:00:1c.1: PCI bridge to [bus 02-02]
[    0.862127] pci 0000:00:1c.1:   bridge window [io  0x4000-0x4fff]
[    0.862143] pci 0000:00:1c.1:   bridge window [mem 0x96000000-0x96ffffff]
[    0.862158] pci 0000:00:1c.1:   bridge window [mem 0x91000000-0x91ffffff 64bit pref]
[    0.862177] pci 0000:00:1e.0: PCI bridge to [bus 05-05]
[    0.862249] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.862266] pci 0000:00:1c.0: setting latency timer to 64
[    0.862304] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.862319] pci 0000:00:1c.1: setting latency timer to 64
[    0.862340] pci 0000:00:1e.0: setting latency timer to 64
[    0.862354] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.862365] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.862376] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.862387] pci_bus 0000:00: resource 7 [mem 0x80000000-0xfebfffff]
[    0.862398] pci_bus 0000:01: resource 0 [io  0x5000-0x5fff]
[    0.862409] pci_bus 0000:01: resource 1 [mem 0x97000000-0x97ffffff]
[    0.862420] pci_bus 0000:01: resource 2 [mem 0x90000000-0x90ffffff 64bit pref]
[    0.862432] pci_bus 0000:02: resource 0 [io  0x4000-0x4fff]
[    0.862442] pci_bus 0000:02: resource 1 [mem 0x96000000-0x96ffffff]
[    0.862453] pci_bus 0000:02: resource 2 [mem 0x91000000-0x91ffffff 64bit pref]
[    0.862465] pci_bus 0000:05: resource 4 [io  0x0000-0x0cf7]
[    0.862475] pci_bus 0000:05: resource 5 [io  0x0d00-0xffff]
[    0.862486] pci_bus 0000:05: resource 6 [mem 0x000a0000-0x000bffff]
[    0.862497] pci_bus 0000:05: resource 7 [mem 0x80000000-0xfebfffff]
[    0.862640] NET: Registered protocol family 2
[    0.862874] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.863825] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.865440] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.866162] TCP: Hash tables configured (established 131072 bind 65536)
[    0.866172] TCP reno registered
[    0.866185] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.866218] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.866535] NET: Registered protocol family 1
[    0.866593] pci 0000:00:02.0: Boot video device
[    0.866678] pci 0000:00:1d.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.866713] pci 0000:00:1d.0: PCI INT A disabled
[    0.866754] pci 0000:00:1d.1: PCI INT B -> GSI 20 (level, low) -> IRQ 20
[    0.866786] pci 0000:00:1d.1: PCI INT B disabled
[    0.866827] pci 0000:00:1d.2: PCI INT C -> GSI 21 (level, low) -> IRQ 21
[    0.866859] pci 0000:00:1d.2: PCI INT C disabled
[    0.866899] pci 0000:00:1d.3: PCI INT D -> GSI 22 (level, low) -> IRQ 22
[    0.866931] pci 0000:00:1d.3: PCI INT D disabled
[    0.866958] pci 0000:00:1d.7: PCI INT D -> GSI 22 (level, low) -> IRQ 22
[    0.867123] pci 0000:00:1d.7: PCI INT D disabled
[    0.867166] PCI: CLS 64 bytes, default 64
[    0.867181] Simple Boot Flag at 0x44 set to 0x1
[    0.869157] audit: initializing netlink socket (disabled)
[    0.869190] type=2000 audit(1385553980.864:1): initialized
[    0.949015] highmem bounce pool size: 64 pages
[    0.949035] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.957177] VFS: Disk quotas dquot_6.5.2
[    0.957418] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.959799] fuse init (API version 7.17)
[    0.960278] msgmni has been set to 1678
[    0.961828] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.961946] io scheduler noop registered
[    0.961959] io scheduler deadline registered
[    0.961991] io scheduler cfq registered (default)
[    0.962427] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.962538] pcieport 0000:00:1c.0: irq 40 for MSI/MSI-X
[    0.962807] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.962908] pcieport 0000:00:1c.1: irq 41 for MSI/MSI-X
[    0.963268] pcieport 0000:00:1c.0: Signaling PME through PCIe PME interrupt
[    0.963280] pci 0000:01:00.0: Signaling PME through PCIe PME interrupt
[    0.963295] pcie_pme 0000:00:1c.0:pcie01: service driver pcie_pme loaded
[    0.963358] pcieport 0000:00:1c.1: Signaling PME through PCIe PME interrupt
[    0.963373] pcie_pme 0000:00:1c.1:pcie01: service driver pcie_pme loaded
[    0.963457] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.963558] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.963829] intel_idle: MWAIT substates: 0x20220
[    0.963860] intel_idle: v0.4 model 0x1C
[    0.963869] intel_idle: lapic_timer_reliable_states 0x2
[    1.028294] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    1.058435] Freeing initrd memory: 13856k freed
[    1.092311] ACPI: AC Adapter [AC] (off-line)
[    1.092539] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    1.092552] ACPI: Power Button [PWRB]
[    1.092674] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1
[    1.092684] ACPI: Sleep Button [SLPB]
[    1.092818] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input2
[    1.092878] ACPI: Lid Switch [LID0]
[    1.093030] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    1.093040] ACPI: Power Button [PWRF]
[    1.093205] ACPI: Fan [FAN] (on)
[    1.161159] thermal LNXTHERM:00: registered as thermal_zone0
[    1.161168] ACPI: Thermal Zone [THRM] (25 C)
[    1.161264] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    1.161288] ACPI: Battery Slot [BAT0] (battery present)
[    1.161400] ERST: Table is not found!
[    1.161406] GHES: HEST is not enabled!
[    1.161703] isapnp: Scanning for PnP cards...
[    1.161720] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.515839] isapnp: No Plug & Play device found
[    1.612920] Linux agpgart interface v0.103
[    1.613115] agpgart-intel 0000:00:00.0: Intel GMA3150 Chipset
[    1.613420] agpgart-intel 0000:00:00.0: detected gtt size: 524288K total, 262144K mappable
[    1.613835] agpgart-intel 0000:00:00.0: detected 8192K stolen memory
[    1.614170] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0x80000000
[    1.618968] brd: module loaded
[    1.621499] loop: module loaded
[    1.621835] ahci 0000:00:1f.2: version 3.0
[    1.621864] ahci 0000:00:1f.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.621969] ahci 0000:00:1f.2: irq 42 for MSI/MSI-X
[    1.622040] ahci: SSS flag set, parallel bus scan disabled
[    1.622093] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0x3 impl SATA mode
[    1.622103] ahci 0000:00:1f.2: flags: 64bit ncq ilck stag pm led clo pmp pio slum part 
[    1.622115] ahci 0000:00:1f.2: setting latency timer to 64
[    1.623682] scsi0 : ahci
[    1.623953] scsi1 : ahci
[    1.624220] scsi2 : ahci
[    1.624445] scsi3 : ahci
[    1.624974] ata1: SATA max UDMA/133 abar m1024@0x98204000 port 0x98204100 irq 42
[    1.624984] ata2: SATA max UDMA/133 abar m1024@0x98204000 port 0x98204180 irq 42
[    1.624991] ata3: DUMMY
[    1.624995] ata4: DUMMY
[    1.626385] Fixed MDIO Bus: probed
[    1.626457] tun: Universal TUN/TAP device driver, 1.6
[    1.626462] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.626650] PPP generic driver version 2.4.2
[    1.626980] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.627030] ehci_hcd 0000:00:1d.7: PCI INT D -> GSI 22 (level, low) -> IRQ 22
[    1.627077] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    1.627086] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    1.627231] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    1.627279] ehci_hcd 0000:00:1d.7: using broken periodic workaround
[    1.627299] ehci_hcd 0000:00:1d.7: debug port 1
[    1.631193] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
[    1.631237] ehci_hcd 0000:00:1d.7: irq 22, io mem 0x98204400
[    1.644041] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    1.644453] hub 1-0:1.0: USB hub found
[    1.644467] hub 1-0:1.0: 8 ports detected
[    1.644657] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.644704] uhci_hcd: USB Universal Host Controller Interface driver
[    1.644756] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.644776] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.644784] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    1.644937] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.645003] uhci_hcd 0000:00:1d.0: irq 18, io base 0x00006080
[    1.645397] hub 2-0:1.0: USB hub found
[    1.645411] hub 2-0:1.0: 2 ports detected
[    1.645561] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 20 (level, low) -> IRQ 20
[    1.645579] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    1.645587] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    1.645745] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    1.645807] uhci_hcd 0000:00:1d.1: irq 20, io base 0x00006060
[    1.646195] hub 3-0:1.0: USB hub found
[    1.646207] hub 3-0:1.0: 2 ports detected
[    1.646370] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 21 (level, low) -> IRQ 21
[    1.646388] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    1.646396] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    1.646544] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    1.646605] uhci_hcd 0000:00:1d.2: irq 21, io base 0x00006040
[    1.646985] hub 4-0:1.0: USB hub found
[    1.646998] hub 4-0:1.0: 2 ports detected
[    1.647152] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 22 (level, low) -> IRQ 22
[    1.647170] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    1.647178] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    1.647321] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    1.647364] uhci_hcd 0000:00:1d.3: irq 22, io base 0x00006020
[    1.647751] hub 5-0:1.0: USB hub found
[    1.647763] hub 5-0:1.0: 2 ports detected
[    1.648110] usbcore: registered new interface driver libusual
[    1.648227] i8042: PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSS0] at 0x60,0x64 irq 1,12
[    1.662501] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.662520] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.662965] mousedev: PS/2 mouse device common for all mice
[    1.663636] rtc_cmos 00:03: RTC can wake from S4
[    1.663861] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    1.663907] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
[    1.664136] device-mapper: uevent: version 1.0.3
[    1.664365] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
[    1.664429] EISA: Probing bus 0 at eisa.0
[    1.664437] EISA: Cannot allocate resource for mainboard
[    1.664444] Cannot allocate resource for EISA slot 1
[    1.664450] Cannot allocate resource for EISA slot 2
[    1.664456] Cannot allocate resource for EISA slot 3
[    1.664462] Cannot allocate resource for EISA slot 4
[    1.664468] Cannot allocate resource for EISA slot 5
[    1.664474] Cannot allocate resource for EISA slot 6
[    1.664481] Cannot allocate resource for EISA slot 7
[    1.664487] Cannot allocate resource for EISA slot 8
[    1.664492] EISA: Detected 0 cards.
[    1.664511] cpufreq-nforce2: No nForce2 chipset.
[    1.664889] cpuidle: using governor ladder
[    1.665514] cpuidle: using governor menu
[    1.665520] EFI Variables Facility v0.08 2004-May-17
[    1.666164] TCP cubic registered
[    1.666504] NET: Registered protocol family 10
[    1.668105] NET: Registered protocol family 17
[    1.668124] Registering the dns_resolver key type
[    1.668173] Using IPI No-Shortcut mode
[    1.668622] PM: Hibernation image not present or could not be loaded.
[    1.668650] registered taskstats version 1
[    1.679163] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    1.691621]   Magic number: 5:397:128
[    1.691718] acpi device:03: hash matches
[    1.691727] acpi PNP0C02:00: hash matches
[    1.691810] rtc_cmos 00:03: setting system clock to 2013-11-27 12:06:22 UTC (1385553982)
[    1.694112] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.694119] EDD information not available.
[    1.820348] ACPI: Battery Slot [BAT0] (battery present)
[    1.956145] usb 1-4: new high-speed USB device number 2 using ehci_hcd
[    2.116136] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.117205] ata1.00: unexpected _GTF length (4)
[    2.117546] ata1.00: ATA-8: WDC WD2500BEVT-22A23T0, 01.01A01, max UDMA/133
[    2.117560] ata1.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    2.118697] ata1.00: unexpected _GTF length (4)
[    2.118998] ata1.00: configured for UDMA/133
[    2.119389] scsi 0:0:0:0: Direct-Access     ATA      WDC WD2500BEVT-2 01.0 PQ: 0 ANSI: 5
[    2.119849] sd 0:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    2.119906] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.120164] sd 0:0:0:0: [sda] Write Protect is off
[    2.120178] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.120303] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.183006]  sda: sda1 sda2 < sda5 sda6 >
[    2.184411] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.440132] ata2: SATA link down (SStatus 0 SControl 300)
[    2.440492] Freeing unused kernel memory: 716k freed
[    2.441075] Write protecting the kernel text: 5640k
[    2.441192] Write protecting the kernel read-only data: 2332k
[    2.486247] udevd[103]: starting version 175
[    2.712405] atl1c 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.712436] atl1c 0000:01:00.0: setting latency timer to 64
[    2.841688] atl1c 0000:01:00.0: version 1.0.1.0-NAPI
[    3.049215] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[   13.886528] Adding 4100092k swap on /dev/sda5.  Priority:-1 extents:1 across:4100092k 
[   13.902492] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   13.937146] udevd[307]: starting version 175
[   13.991016] lp: driver loaded but no devices found
[   13.996769] coretemp coretemp.0: Using relative temperature scale!
[   13.996834] coretemp coretemp.0: Using relative temperature scale!
[   14.099807] wmi: Mapper loaded
[   14.179506] acer_wmi: Acer Laptop ACPI-WMI Extras
[   14.179560] acer_wmi: Function bitmap for Communication Button: 0x0
[   14.179867] acer_wmi: Brightness must be controlled by generic video driver
[   14.183558] input: Acer WMI hotkeys as /devices/virtual/input/input5
[   14.520938] [drm] Initialized drm 1.1.0 20060810
[   14.586550] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   14.586568] i915 0000:00:02.0: setting latency timer to 64
[   14.665392] Linux video capture interface: v2.00
[   14.668226] uvcvideo: Found UVC 1.00 device 1.3M WebCam (0402:9665)
[   14.673513] input: 1.3M WebCam as /devices/pci0000:00/0000:00:1d.7/usb1/1-4/1-4:1.0/input/input6
[   14.673809] usbcore: registered new interface driver uvcvideo
[   14.673819] USB Video Class driver (1.1.1)
[   14.686411] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   14.687881] type=1400 audit(1385553995.489:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=509 comm="apparmor_parser"
[   14.689685] type=1400 audit(1385553995.493:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=509 comm="apparmor_parser"
[   14.690894] i915 0000:00:02.0: irq 43 for MSI/MSI-X
[   14.690911] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   14.690920] [drm] Driver supports precise vblank timestamp query.
[   14.691230] type=1400 audit(1385553995.493:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=509 comm="apparmor_parser"
[   14.720962] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   14.777262] fixme: max PWM is zero.
[   15.042730] [drm] initialized overlay support
[   15.065563] fbcon: inteldrmfb (fb0) is primary device
[   15.065762] Console: switching to colour frame buffer device 128x37
[   15.065823] fb0: inteldrmfb frame buffer device
[   15.065827] drm: registered panic notifier
[   15.299852] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
[   15.657732] psmouse serio1: synaptics: Touchpad model: 1, fw: 7.2, id: 0x1c0b1, caps: 0xd04733/0xa40000/0xa0000
[   15.726477] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input7
[   15.892261] acpi device:27: registered as cooling_device5
[   15.892949] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input8
[   15.893134] ACPI: Video Device [OVGA] (multi-head: yes  rom: no  post: no)
[   15.893255] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   15.893412] snd_hda_intel 0000:00:1b.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   15.893547] snd_hda_intel 0000:00:1b.0: irq 44 for MSI/MSI-X
[   15.893610] snd_hda_intel 0000:00:1b.0: setting latency timer to 64
[   16.224708] init: failsafe main process (714) killed by TERM signal
[   16.494316] ppdev: user-space parallel port driver
[   16.576282] Bluetooth: Core ver 2.16
[   16.576391] NET: Registered protocol family 31
[   16.576401] Bluetooth: HCI device and connection manager initialized
[   16.576412] Bluetooth: HCI socket layer initialized
[   16.576421] Bluetooth: L2CAP socket layer initialized
[   16.576444] Bluetooth: SCO socket layer initialized
[   16.588099] Bluetooth: RFCOMM TTY layer initialized
[   16.588121] Bluetooth: RFCOMM socket layer initialized
[   16.588129] Bluetooth: RFCOMM ver 1.11
[   16.597117] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   16.597130] Bluetooth: BNEP filters: protocol multicast
[   16.624279] type=1400 audit(1385553997.429:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=790 comm="apparmor_parser"
[   16.626078] type=1400 audit(1385553997.429:6): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=790 comm="apparmor_parser"
[   18.778902] atl1c 0000:01:00.0: irq 45 for MSI/MSI-X
[   20.060603] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   20.061469] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   20.139233] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   20.148890] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   21.093854] type=1400 audit(1385554001.897:7): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=840 comm="apparmor_parser"
[   21.095495] type=1400 audit(1385554001.897:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=840 comm="apparmor_parser"
[   21.096643] type=1400 audit(1385554001.901:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=840 comm="apparmor_parser"
[   21.097303] type=1400 audit(1385554001.901:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=839 comm="apparmor_parser"
[   21.098664] type=1400 audit(1385554001.901:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper//chromium_browser" pid=839 comm="apparmor_parser"
[   21.102409] type=1400 audit(1385554001.905:12): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=843 comm="apparmor_parser"
[   21.104373] type=1400 audit(1385554001.909:13): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=843 comm="apparmor_parser"
[   21.109336] type=1400 audit(1385554001.913:14): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=845 comm="apparmor_parser"
[   21.120309] type=1400 audit(1385554001.925:15): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=841 comm="apparmor_parser"
[   21.132900] type=1400 audit(1385554001.937:16): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince//launchpad_integration" pid=841 comm="apparmor_parser"
[   22.369422] init: plymouth-stop pre-start process (1128) terminated with status 1
[  852.761432] acer_wmi: Unknown key number - 0x85
[ 1128.667544] acer_wmi: Unknown key number - 0x85
```


In case it helps here the output of lshw and lspci while the wireless was working:
sudo lshw -C network (while it was working)
```
  *-network
       description: Ethernet interface
       product: AR8152 v1.1 Fast Ethernet
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: c1
       serial: 1c:75:08:9f:92:be
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:45 memory:97000000-9703ffff ioport:5000(size=128)
  *-network
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 88:9f:fa:86:a0:83
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.2.0-56-generic firmware=N/A ip=192.168.1.66 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:96000000-9600ffff
```

lspci -nn (while wireles working)
```
00:00.0 Host bridge [0600]: Intel Corporation Atom Processor D4xx/D5xx/N4xx/N5xx DMI Bridge [8086:a010] (rev 02)
00:02.0 VGA compatible controller [0300]: Intel Corporation Atom Processor D4xx/D5xx/N4xx/N5xx Integrated Graphics Controller [8086:a011] (rev 02)
00:02.1 Display controller [0380]: Intel Corporation Atom Processor D4xx/D5xx/N4xx/N5xx Integrated Graphics Controller [8086:a012] (rev 02)
00:1b.0 Audio device [0403]: Intel Corporation NM10/ICH7 Family High Definition Audio Controller [8086:27d8] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation NM10/ICH7 Family PCI Express Port 1 [8086:27d0] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation NM10/ICH7 Family PCI Express Port 2 [8086:27d2] (rev 02)
00:1d.0 USB controller [0c03]: Intel Corporation NM10/ICH7 Family USB UHCI Controller #1 [8086:27c8] (rev 02)
00:1d.1 USB controller [0c03]: Intel Corporation NM10/ICH7 Family USB UHCI Controller #2 [8086:27c9] (rev 02)
00:1d.2 USB controller [0c03]: Intel Corporation NM10/ICH7 Family USB UHCI Controller #3 [8086:27ca] (rev 02)
00:1d.3 USB controller [0c03]: Intel Corporation NM10/ICH7 Family USB UHCI Controller #4 [8086:27cb] (rev 02)
00:1d.7 USB controller [0c03]: Intel Corporation NM10/ICH7 Family USB2 EHCI Controller [8086:27cc] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation NM10 Family LPC Controller [8086:27bc] (rev 02)
00:1f.2 SATA controller [0106]: Intel Corporation NM10/ICH7 Family SATA Controller [AHCI mode] [8086:27c1] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation NM10/ICH7 Family SMBus Controller [8086:27da] (rev 02)
01:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8152 v1.1 Fast Ethernet [1969:2060] (rev c1)
02:00.0 Network controller [0280]: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
```

If anything else would be needed please let me know, and thanks already

Tobi

---

### Post by Pandanus on 2013-11-27
Just randomly the wifi started working again, but I guess it will go down again at some point, not going to assume that all will be ok as before. I thought I post the working dmesg as well, and highlight the bits that are missing when wifi is down. To me it seems the card is never registered at a no-wifi boot, could there be a hardware issue? But why is it then 100% stable when it's up, and only goes down after a suspend? Any ideas would be great, as having a randomly working wifi is actually impacting quite considerably on my work...
Well, the working dmesg, I had a look with meld at the differences and parts in bold are plain missing when wifi is down.

```

(...same as above dmesg...)
[    0.668113] pci 0000:00:1c.0: PCI bridge to [bus 01-01]
[    0.668131] pci 0000:00:1c.0:   bridge window [io  0x5000-0x5fff]
[    0.668146] pci 0000:00:1c.0:   bridge window [mem 0x97000000-0x97ffffff]
[    0.668166] pci 0000:00:1c.0:   bridge window [mem 0x90000000-0x90ffffff 64bit pref]
[B][    0.668306] pci 0000:02:00.0: [168c:002b] type 0 class 0x000280
[    0.668356] pci 0000:02:00.0: reg 10: [mem 0x96000000-0x9600ffff 64bit]
[    0.668541] pci 0000:02:00.0: supports D1
[    0.668550] pci 0000:02:00.0: PME# supported from D0 D1 D3hot
[    0.668565] pci 0000:02:00.0: PME# disabled[/B]
[    0.676112] pci 0000:00:1c.1: PCI bridge to [bus 02-02]
[    0.676131] pci 0000:00:1c.1:   bridge window [io  0x4000-0x4fff]

(....)
[    0.963523] pcieport 0000:00:1c.1: Signaling PME through PCIe PME interrupt
**[    0.963534] pci 0000:02:00.0: Signaling PME through PCIe PME interrupt**
[    0.963550] pcie_pme 0000:00:1c.1:pcie01: service driver pcie_pme loaded

(...)
[   14.310482] acer_wmi: Acer Laptop ACPI-WMI Extras
[   14.310537] acer_wmi: Function bitmap for Communication Button: 0x1
[   14.310839] acer_wmi: Brightness must be controlled by generic video driver
[   14.314295] input: Acer WMI hotkeys as /devices/virtual/input/input5
**[   14.654035] cfg80211: Calling CRDA to update world regulatory domain**
[   14.665477] [drm] Initialized drm 1.1.0 20060810
[   14.715371] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   14.715389] i915 0000:00:02.0: setting latency timer to 64
[   14.738602] type=1400 audit(1385566061.572:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=500 comm="apparmor_parser"
[   14.740803] type=1400 audit(1385566061.576:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=500 comm="apparmor_parser"
[   14.741731] type=1400 audit(1385566061.576:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=500 comm="apparmor_parser"
[   14.759005] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[B][   14.780682] ath9k 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   14.780709] ath9k 0000:02:00.0: setting latency timer to 64[/B]
[   14.791242] Linux video capture interface: v2.00
[   14.806723] uvcvideo: Found UVC 1.00 device 1.3M WebCam (0402:9665)
[   14.815831] input: 1.3M WebCam as /devices/pci0000:00/0000:00:1d.7/usb1/1-4/1-4:1.0/input/input6
[B][   14.832981] ath: EEPROM regdomain: 0x65
[   14.832993] ath: EEPROM indicates we should expect a direct regpair map
[   14.833005] ath: Country alpha2 being used: 00
[   14.833013] ath: Regpair used: 0x65
[   14.833024] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:

(... lots of frequency stuff ...)

[   14.833286] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   14.833299] cfg80211: 2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   14.833309] cfg80211: Disabling freq 2484 MHz as custom regd has no rule that fits a 20 MHz wide channel
[   14.842918] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain[/B]
[   14.847736] i915 0000:00:02.0: irq 43 for MSI/MSI-X
[   14.847756] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   14.847764] [drm] Driver supports precise vblank timestamp query.
[   14.847901] usbcore: registered new interface driver uvcvideo
[   14.847911] USB Video Class driver (1.1.1)
[B][   14.862478] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   14.865109] Registered led device: ath9k-phy0
[   14.865144] ieee80211 phy0: Atheros AR9285 Rev:2 mem=0xf8220000, irq=17[/B]
[   14.885611] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   14.945173] fixme: max PWM is zero.
[   15.211124] [drm] initialized overlay support
[   15.237627] fbcon: inteldrmfb (fb0) is primary device
[   15.237949] Console: switching to colour frame buffer device 128x37
[   15.238055] fb0: inteldrmfb frame buffer device
[   15.238062] drm: registered panic notifier
[B][   15.264621] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[   15.264635] cfg80211: World regulatory domain updated:
[   15.264642] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   15.264654] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.264666] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   15.264676] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   15.264687] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.264697] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)[/B]
[   15.350325] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
[   15.560311] acpi device:27: registered as cooling_device5
[   15.560916] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input7
[   15.561096] ACPI: Video Device [OVGA] (multi-head: yes  rom: no  post: no)
[   15.561235] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   15.562150] snd_hda_intel 0000:00:1b.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   15.562858] snd_hda_intel 0000:00:1b.0: irq 44 for MSI/MSI-X
[   15.562949] snd_hda_intel 0000:00:1b.0: setting latency timer to 64
[   15.631260] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   15.631811] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   15.877688] psmouse serio1: synaptics: Touchpad model: 1, fw: 7.2, id: 0x1c0b1, caps: 0xd04733/0xa40000/0xa0000
[   15.945940] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input10
[   16.934143] init: failsafe main process (731) killed by TERM signal
[   17.053450] ppdev: user-space parallel port driver
[   17.075079] Bluetooth: Core ver 2.16
[   17.075170] NET: Registered protocol family 31
[   17.075180] Bluetooth: HCI device and connection manager initialized
[   17.075191] Bluetooth: HCI socket layer initialized
[   17.075200] Bluetooth: L2CAP socket layer initialized
[   17.075222] Bluetooth: SCO socket layer initialized
[   17.103744] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   17.103756] Bluetooth: BNEP filters: protocol multicast
[   17.156642] Bluetooth: RFCOMM TTY layer initialized
[   17.156665] Bluetooth: RFCOMM socket layer initialized
[   17.156674] Bluetooth: RFCOMM ver 1.11
[   17.274417] type=1400 audit(1385566064.108:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=808 comm="apparmor_parser"
[   17.276550] type=1400 audit(1385566064.112:6): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=808 comm="apparmor_parser"
[   19.727285] atl1c 0000:01:00.0: irq 45 for MSI/MSI-X
[   21.004137] sched: RT throttling activated
[   21.099562] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   21.108729] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   21.159189] type=1400 audit(1385566067.992:7): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=849 comm="apparmor_parser"
[   21.161175] type=1400 audit(1385566067.996:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=849 comm="apparmor_parser"
[   21.162112] type=1400 audit(1385566067.996:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=849 comm="apparmor_parser"
[   21.166141] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   21.171192] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   21.183203] type=1400 audit(1385566068.016:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=848 comm="apparmor_parser"
[   21.184767] type=1400 audit(1385566068.020:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper//chromium_browser" pid=848 comm="apparmor_parser"
[   21.187312] type=1400 audit(1385566068.020:12): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=854 comm="apparmor_parser"
[   21.200389] type=1400 audit(1385566068.036:13): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=852 comm="apparmor_parser"
[   21.202456] type=1400 audit(1385566068.036:14): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=852 comm="apparmor_parser"
[   21.212603] type=1400 audit(1385566068.048:15): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=850 comm="apparmor_parser"
[   21.225181] type=1400 audit(1385566068.060:16): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince//launchpad_integration" pid=850 comm="apparmor_parser"
[   22.456529] init: plymouth-stop pre-start process (1146) terminated with status 1
[   23.952637] wlan0: authenticate with xxx (try 1)
[   23.955838] wlan0: authenticated
[   23.990091] wlan0: associate with xxx (try 1)
[   23.994580] wlan0: RX AssocResp from xxx (capab=0x411 status=0 aid=1)
[   23.994591] wlan0: associated
[   24.002445] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   34.832062] wlan0: no IPv6 routers present
``` 

I hope someone has an idea what could be wrong.

---

