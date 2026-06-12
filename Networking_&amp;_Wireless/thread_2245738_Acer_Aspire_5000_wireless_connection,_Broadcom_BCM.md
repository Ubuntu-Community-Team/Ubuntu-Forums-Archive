---
title: "Acer Aspire 5000 wireless connection, Broadcom BCM4318"
date: 2014-09-25
forum: Networking &amp; Wireless
---

### Post by alin4 on 2014-09-25
Hello everybody. I have An Acer Aspire 5000 laptop. My problem is that i cannot connect to the wireless network, and the light from wireless card switch doesn't turn on for nothing. I have a BCM4318 wireless card, and the result of lspci is 
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 760/M760 Host (rev 03)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] LPC Controller (rev 25)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2/3 SMBus controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 IDE Controller
00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] SiS7012 AC'97 Sound Controller (rev a0)
00:03.0 USB controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.2 USB controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
00:06.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)
00:0b.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter

I have low-level skills with linux, but before this post i spend 6 hours tryin' to figure it out. I tried using fwcutter, acerhk, ndiswrapper, but i fail with all of them at some point. I'm doing something wrong, but can't put my finger on it. It drives me crazy. If someone could point me in the right direction, i'd appreciate.

---

### Post by xc3RnbFO8P on 2014-09-25
Can run this in Terminal and show the output:
> dmesg | grep b43

---

### Post by alin4 on 2014-09-25
Command <dmesg | grep b43> didn't had any result, just back to the command promp. so i ran a simple dmesg:

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 3.13.0-36-generic (buildd@toyol) (gcc version 4.8.2 (Ubuntu 4.8.2-19ubuntu1) ) #63-Ubuntu SMP Wed Sep 3 21:30:07 UTC 2014 (Ubuntu 3.13.0-36.63-generic 3.13.11.6)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-36-generic root=UUID=4bef1a37-253d-4a94-a336-968de4d5ddfc ro quiet splash vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009f3ff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009f400-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000dc000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x000000003beeffff] usable
[    0.000000] BIOS-e820: [mem 0x000000003bef0000-0x000000003bef9fff] ACPI data
[    0.000000] BIOS-e820: [mem 0x000000003befa000-0x000000003befffff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x000000003bf00000-0x000000003fffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fff00000-0x00000000ffffffff] reserved
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.3 present.
[    0.000000] DMI: Acer, inc. Aspire 5000     /Lugano M        , BIOS 3A32 02/20/06
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] AGP bridge at 00:00:00
[    0.000000] Aperture from AGP @ e0000000 old size 32 MB
[    0.000000] Aperture from AGP @ e0000000 size 32 MB (APSIZE f38)
[    0.000000] e820: last_pfn = 0x3bef0 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-D5FFF write-protect
[    0.000000]   D6000-DBFFF uncachable
[    0.000000]   DC000-E3FFF write-back
[    0.000000]   E4000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0000000000 mask FFC0000000 write-back
[    0.000000]   1 base 003C000000 mask FFFC000000 uncachable
[    0.000000]   2 base 00E0000000 mask FFFE000000 write-combining
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] found SMP MP-table at [mem 0x000f7fd0-0x000f7fdf] mapped at [ffff8800000f7fd0]
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] Base memory trampoline at [ffff880000099000] 99000 size 24576
[    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
[    0.000000]  [mem 0x00000000-0x000fffff] page 4k
[    0.000000] BRK [0x01fdf000, 0x01fdffff] PGTABLE
[    0.000000] BRK [0x01fe0000, 0x01fe0fff] PGTABLE
[    0.000000] BRK [0x01fe1000, 0x01fe1fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x3bc00000-0x3bdfffff]
[    0.000000]  [mem 0x3bc00000-0x3bdfffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x38000000-0x3bbfffff]
[    0.000000]  [mem 0x38000000-0x3bbfffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x00100000-0x37ffffff]
[    0.000000]  [mem 0x00100000-0x001fffff] page 4k
[    0.000000]  [mem 0x00200000-0x37ffffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x3be00000-0x3beeffff]
[    0.000000]  [mem 0x3be00000-0x3beeffff] page 4k
[    0.000000] BRK [0x01fe2000, 0x01fe2fff] PGTABLE
[    0.000000] RAMDISK: [mem 0x35b5c000-0x36da5fff]
[    0.000000] ACPI: RSDP 00000000000f7f60 000014 (v00 PTLTD )
[    0.000000] ACPI: RSDT 000000003bef61be 000034 (v01 PTLTD    RSDT   06040000  LTP 00000000)
[    0.000000] ACPI: FACP 000000003bef9e5f 000074 (v01 SiS    755F     06040000 PTL  000F4240)
[    0.000000] ACPI: DSDT 000000003bef61f2 003C6D (v01 PTLTD       755 06040000 MSFT 0100000E)
[    0.000000] ACPI: FACS 000000003befafc0 000040
[    0.000000] ACPI: SSDT 000000003bef9ed3 0000B5 (v01 PTLTD  POWERNOW 06040000  LTP 00000001)
[    0.000000] ACPI: APIC 000000003bef9f88 000050 (v01 PTLTD  ? APIC   06040000  LTP 00000000)
[    0.000000] ACPI: BOOT 000000003bef9fd8 000028 (v01 PTLTD  $SBFTBL$ 06040000  LTP 00000001)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x000000003beeffff]
[    0.000000] Initmem setup node 0 [mem 0x00000000-0x3beeffff]
[    0.000000]   NODE_DATA [mem 0x3beeb000-0x3beeffff]
[    0.000000]  [ffffea0000000000-ffffea0000ffffff] PMD -> [ffff88003a600000-ffff88003b5fffff] on node 0
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00001000-0x00ffffff]
[    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
[    0.000000]   Normal   empty
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00001000-0x0009efff]
[    0.000000]   node   0: [mem 0x00100000-0x3beeffff]
[    0.000000] On node 0 totalpages: 245390
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 21 pages reserved
[    0.000000]   DMA zone: 3998 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 3772 pages used for memmap
[    0.000000]   DMA32 zone: 241392 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x8008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ11 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] smpboot: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: [mem 0x0009f000-0x0009ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dbfff]
[    0.000000] PM: Registered nosave memory: [mem 0x000dc000-0x000fffff]
[    0.000000] e820: [mem 0x40000000-0xffefffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:1 nr_node_ids:1
[    0.000000] PERCPU: Embedded 29 pages/cpu @ffff88003bc00000 s86336 r8192 d24256 u2097152
[    0.000000] pcpu-alloc: s86336 r8192 d24256 u2097152 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 241533
[    0.000000] Policy zone: DMA32
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-36-generic root=UUID=4bef1a37-253d-4a94-a336-968de4d5ddfc ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Checking aperture...
[    0.000000] AGP bridge at 00:00:00
[    0.000000] Aperture from AGP @ e0000000 old size 32 MB
[    0.000000] Aperture from AGP @ e0000000 size 32 MB (APSIZE f38)
[    0.000000] Node 0: aperture @ e0000000 size 32 MB
[    0.000000] Aperture too small (32 MB) than (64 MB)
[    0.000000] Memory: 929700K/981560K available (7373K kernel code, 1144K rwdata, 3404K rodata, 1336K init, 1440K bss, 51860K reserved)
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=1.
[    0.000000]     Offload RCU callbacks from all CPUs
[    0.000000]     Offload RCU callbacks from CPUs: 0.
[    0.000000] NR_IRQS:16640 nr_irqs:256 16
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 4194304 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.000000] tsc: Detected 1600.047 MHz processor
[    0.004007] Calibrating delay loop (skipped), value calculated using timer frequency.. 3200.09 BogoMIPS (lpj=6400188)
[    0.004013] pid_max: default: 32768 minimum: 301
[    0.004068] Security Framework initialized
[    0.004113] AppArmor: AppArmor initialized
[    0.004115] Yama: becoming mindful.
[    0.008097] Dentry cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.009444] Inode-cache hash table entries: 65536 (order: 7, 524288 bytes)
[    0.010094] Mount-cache hash table entries: 2048 (order: 2, 16384 bytes)
[    0.010100] Mountpoint-cache hash table entries: 2048 (order: 2, 16384 bytes)
[    0.010590] Initializing cgroup subsys memory
[    0.010610] Initializing cgroup subsys devices
[    0.010614] Initializing cgroup subsys freezer
[    0.010619] Initializing cgroup subsys blkio
[    0.010622] Initializing cgroup subsys perf_event
[    0.010627] Initializing cgroup subsys hugetlb
[    0.010664] tseg: 003bf00000
[    0.010670] mce: CPU supports 5 MCE banks
[    0.010690] Last level iTLB entries: 4KB 512, 2MB 8, 4MB 4
[    0.010690] Last level dTLB entries: 4KB 512, 2MB 8, 4MB 4
[    0.010690] tlb_flushall_shift: 4
[    0.022617] Freeing SMP alternatives memory: 32K (ffffffff81e6d000 - ffffffff81e75000)
[    0.023952] ACPI: Core revision 20131115
[    0.026456] ACPI: All ACPI Tables successfully acquired
[    0.028012] ftrace: allocating 28537 entries in 112 pages
[    0.044656] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.086826] smpboot: CPU0: AMD Turion(tm) 64 Mobile Technology ML-30 (fam: 0f, model: 24, stepping: 02)
[    0.088000] Performance Events: AMD PMU driver.
[    0.088000] ... version:                0
[    0.088000] ... bit width:              48
[    0.088000] ... generic registers:      4
[    0.088000] ... value mask:             0000ffffffffffff
[    0.088000] ... max period:             00007fffffffffff
[    0.088000] ... fixed-purpose events:   0
[    0.088000] ... event mask:             000000000000000f
[    0.088000] x86: Booted up 1 node, 1 CPUs
[    0.088000] smpboot: Total of 1 processors activated (3200.09 BogoMIPS)
[    0.088000] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.088000] devtmpfs: initialized
[    0.094265] EVM: security.selinux
[    0.094267] EVM: security.SMACK64
[    0.094269] EVM: security.ima
[    0.094271] EVM: security.capability
[    0.094353] PM: Registering ACPI NVS region [mem 0x3befa000-0x3befffff] (24576 bytes)
[    0.096377] pinctrl core: initialized pinctrl subsystem
[    0.096487] regulator-dummy: no parameters
[    0.096524] RTC time: 17:48:46, date: 09/25/14
[    0.096588] NET: Registered protocol family 16
[    0.096815] cpuidle: using governor ladder
[    0.096819] cpuidle: using governor menu
[    0.096828] node 0 link 0: io port [0, fffff]
[    0.096832] TOM: 0000000040000000 aka 1024M
[    0.096837] node 0 link 0: mmio [a0000, bffff]
[    0.096842] node 0 link 0: mmio [40000000, fe0bffff]
[    0.096846] bus: [bus 00-ff] on node 0 link 0
[    0.096849] bus: 00 [io  0x0000-0xffff]
[    0.096851] bus: 00 [mem 0x000a0000-0x000bffff]
[    0.096854] bus: 00 [mem 0x40000000-0xfcffffffff]
[    0.096919] ACPI: bus type PCI registered
[    0.096922] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.097018] PCI: Using configuration type 1 for base access
[    0.098699] bio: create slab <bio-0> at 0
[    0.098959] ACPI: Added _OSI(Module Device)
[    0.098961] ACPI: Added _OSI(Processor Device)
[    0.098964] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.098966] ACPI: Added _OSI(Processor Aggregator Device)
[    0.112063] ACPI: Interpreter enabled
[    0.112073] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20131115/hwxface-580)
[    0.112079] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20131115/hwxface-580)
[    0.112099] ACPI: (supports S0 S3 S4 S5)
[    0.112101] ACPI: Using IOAPIC for interrupt routing
[    0.112134] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
[    0.112248] ACPI: No dock devices found.
[    0.120285] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.120294] acpi PNP0A03:00: _OSC: OS supports [ASPM ClockPM Segments MSI]
[    0.120303] acpi PNP0A03:00: _OSC failed (AE_NOT_FOUND); disabling ASPM
[    0.121919] acpi PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)
[    0.121924] acpi PNP0A03:00: host bridge window [mem 0x000d6000-0x000d7fff] (ignored)
[    0.121927] acpi PNP0A03:00: host bridge window [mem 0x000d8000-0x000d9fff] (ignored)
[    0.121931] acpi PNP0A03:00: host bridge window [mem 0x000da000-0x000dbfff] (ignored)
[    0.121935] acpi PNP0A03:00: host bridge window [mem 0x40000000-0xffffffff] (ignored)
[    0.121939] acpi PNP0A03:00: host bridge window [io  0x0000-0x0cf7] (ignored)
[    0.121942] acpi PNP0A03:00: host bridge window [io  0x0d00-0xffff] (ignored)
[    0.121946] PCI: root bus 00: hardware-probed resources
[    0.121952] acpi PNP0A03:00: fail to add MMCONFIG information, can't access extended PCI configuration space under this bridge.
[    0.122126] PCI host bridge to bus 0000:00
[    0.122131] pci_bus 0000:00: root bus resource [bus 00-ff]
[    0.122135] pci_bus 0000:00: root bus resource [io  0x0000-0xffff]
[    0.122139] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    0.122143] pci_bus 0000:00: root bus resource [mem 0x40000000-0xfcffffffff]
[    0.122160] pci 0000:00:00.0: [1039:0760] type 00 class 0x060000
[    0.122174] pci 0000:00:00.0: reg 0x10: [mem 0xe0000000-0xe1ffffff]
[    0.122314] pci 0000:00:01.0: [1039:0002] type 01 class 0x060400
[    0.122422] pci 0000:00:02.0: [1039:0008] type 00 class 0x060100
[    0.122469] pci 0000:00:02.0: Enabling SiS 96x SMBus
[    0.122566] pci 0000:00:02.1: [1039:0016] type 00 class 0x0c0500
[    0.122599] pci 0000:00:02.1: reg 0x20: [io  0x8100-0x811f]
[    0.122695] pci 0000:00:02.5: [1039:5513] type 00 class 0x01018a
[    0.122715] pci 0000:00:02.5: reg 0x10: [io  0x01f0-0x01f7]
[    0.122723] pci 0000:00:02.5: reg 0x14: [io  0x03f4-0x03f7]
[    0.122731] pci 0000:00:02.5: reg 0x18: [io  0x0170-0x0177]
[    0.122740] pci 0000:00:02.5: reg 0x1c: [io  0x0374-0x0377]
[    0.122748] pci 0000:00:02.5: reg 0x20: [io  0x2000-0x200f]
[    0.122848] pci 0000:00:02.6: [1039:7013] type 00 class 0x070300
[    0.122862] pci 0000:00:02.6: reg 0x10: [io  0x1000-0x10ff]
[    0.122872] pci 0000:00:02.6: reg 0x14: [io  0x1c00-0x1c7f]
[    0.122920] pci 0000:00:02.6: supports D1 D2
[    0.122923] pci 0000:00:02.6: PME# supported from D3hot D3cold
[    0.122972] pci 0000:00:02.6: System wakeup disabled by ACPI
[    0.123024] pci 0000:00:02.7: [1039:7012] type 00 class 0x040100
[    0.123038] pci 0000:00:02.7: reg 0x10: [io  0x1400-0x14ff]
[    0.123047] pci 0000:00:02.7: reg 0x14: [io  0x1c80-0x1cff]
[    0.123094] pci 0000:00:02.7: supports D1 D2
[    0.123097] pci 0000:00:02.7: PME# supported from D3hot D3cold
[    0.123187] pci 0000:00:03.0: [1039:7001] type 00 class 0x0c0310
[    0.123199] pci 0000:00:03.0: reg 0x10: [mem 0xe2002000-0xe2002fff]
[    0.123277] pci 0000:00:03.0: System wakeup disabled by ACPI
[    0.123326] pci 0000:00:03.1: [1039:7001] type 00 class 0x0c0310
[    0.123337] pci 0000:00:03.1: reg 0x10: [mem 0xe2003000-0xe2003fff]
[    0.123415] pci 0000:00:03.1: System wakeup disabled by ACPI
[    0.123470] pci 0000:00:03.2: [1039:7002] type 00 class 0x0c0320
[    0.123483] pci 0000:00:03.2: reg 0x10: [mem 0xe2004000-0xe2004fff]
[    0.123532] pci 0000:00:03.2: PME# supported from D0 D3hot D3cold
[    0.123579] pci 0000:00:03.2: System wakeup disabled by ACPI
[    0.123636] pci 0000:00:04.0: [1039:0900] type 00 class 0x020000
[    0.123650] pci 0000:00:04.0: reg 0x10: [io  0x1800-0x18ff]
[    0.123659] pci 0000:00:04.0: reg 0x14: [mem 0xe2005000-0xe2005fff]
[    0.123688] pci 0000:00:04.0: reg 0x30: [mem 0x00000000-0x0001ffff pref]
[    0.123710] pci 0000:00:04.0: supports D1 D2
[    0.123713] pci 0000:00:04.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.123780] pci 0000:00:04.0: System wakeup disabled by ACPI
[    0.123834] pci 0000:00:06.0: [104c:ac50] type 02 class 0x060700
[    0.123848] pci 0000:00:06.0: reg 0x10: [mem 0x00000000-0x00000fff]
[    0.123871] pci 0000:00:06.0: supports D1 D2
[    0.123875] pci 0000:00:06.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.123965] pci 0000:00:0b.0: [14e4:4318] type 00 class 0x028000
[    0.123977] pci 0000:00:0b.0: reg 0x10: [mem 0xe2000000-0xe2001fff]
[    0.124109] pci 0000:00:18.0: [1022:1100] type 00 class 0x060000
[    0.124203] pci 0000:00:18.1: [1022:1101] type 00 class 0x060000
[    0.124293] pci 0000:00:18.2: [1022:1102] type 00 class 0x060000
[    0.124380] pci 0000:00:18.3: [1022:1103] type 00 class 0x060000
[    0.124510] pci 0000:01:00.0: [1039:6330] type 00 class 0x030000
[    0.124521] pci 0000:01:00.0: reg 0x10: [mem 0xe8000000-0xefffffff pref]
[    0.124527] pci 0000:01:00.0: reg 0x14: [mem 0xe2100000-0xe211ffff]
[    0.124534] pci 0000:01:00.0: reg 0x18: [io  0xa000-0xa07f]
[    0.124561] pci 0000:01:00.0: supports D1 D2
[    0.124619] pci 0000:00:01.0: PCI bridge to [bus 01]
[    0.124624] pci 0000:00:01.0:   bridge window [io  0xa000-0xafff]
[    0.124629] pci 0000:00:01.0:   bridge window [mem 0xe2100000-0xe21fffff]
[    0.124634] pci 0000:00:01.0:   bridge window [mem 0xe8000000-0xefffffff pref]
[    0.124641] pci 0000:00:06.0: bridge configuration invalid ([bus 00-00]), reconfiguring
[    0.124690] pci_bus 0000:02: busn_res: [bus 02-ff] end is updated to 05
[    0.124963] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 *7 9 10 11)
[    0.125054] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 *4 5 7 9 10 11)
[    0.125137] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 7 9 10 11)
[    0.125219] ACPI: PCI Interrupt Link [LNKD] (IRQs *3 4 5 7 9 10 11)
[    0.125319] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 *9 10 11)
[    0.125401] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 *11)
[    0.125480] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 9 10 11) *0, disabled.
[    0.125559] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 9 *10 11)
[    0.125684] ACPI: \_SB_.PCI0: notify handler is installed
[    0.125715] Found 1 acpi root devices
[    0.125758] ACPI : EC: GPE = 0x19, I/O: command/status = 0x66, data = 0x62
[    0.125920] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.125922] vgaarb: loaded
[    0.125924] vgaarb: bridge control possible 0000:01:00.0
[    0.126266] SCSI subsystem initialized
[    0.126369] libata version 3.00 loaded.
[    0.126405] ACPI: bus type USB registered
[    0.126446] usbcore: registered new interface driver usbfs
[    0.126460] usbcore: registered new interface driver hub
[    0.126501] usbcore: registered new device driver usb
[    0.126670] PCI: Using ACPI for IRQ routing
[    0.126674] PCI: pci_cache_line_size set to 64 bytes
[    0.126685] pci 0000:00:00.0: address space collision: [mem 0xe0000000-0xe1ffffff] conflicts with GART [mem 0xe0000000-0xe1ffffff]
[    0.126723] e820: reserve RAM buffer [mem 0x0009f400-0x0009ffff]
[    0.126726] e820: reserve RAM buffer [mem 0x3bef0000-0x3bffffff]
[    0.126893] NetLabel: Initializing
[    0.126895] NetLabel:  domain hash size = 128
[    0.126897] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.126921] NetLabel:  unlabeled traffic allowed by default
[    0.127076] Switched to clocksource refined-jiffies
[    0.139482] AppArmor: AppArmor Filesystem Enabled
[    0.139559] pnp: PnP ACPI init
[    0.139587] ACPI: bus type PNP registered
[    0.139715] pnp 00:00: [dma 4]
[    0.139757] pnp 00:00: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.139826] pnp 00:01: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.139862] pnp 00:02: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.140088] system 00:03: [io  0x8000-0x807f] could not be reserved
[    0.140093] system 00:03: [io  0x8080-0x80ff] has been reserved
[    0.140097] system 00:03: [io  0x8100-0x811f] has been reserved
[    0.140102] system 00:03: [io  0x04d0-0x04d1] has been reserved
[    0.140106] system 00:03: [io  0x03f0-0x03f1] has been reserved
[    0.140112] system 00:03: [mem 0xfec00000-0xfecfffff] could not be reserved
[    0.140117] system 00:03: [mem 0xfed00000-0xfed003ff] has been reserved
[    0.140121] system 00:03: [mem 0xfee00000-0xfeefffff] has been reserved
[    0.140126] system 00:03: [mem 0xffc00000-0xffc00fff] has been reserved
[    0.140130] system 00:03: [mem 0xffe00000-0xffe00fff] has been reserved
[    0.140134] system 00:03: [mem 0xffe80000-0xffefffff] has been reserved
[    0.140139] system 00:03: [mem 0xfffe0000-0xfffeffff] has been reserved
[    0.140143] system 00:03: [mem 0xffff0000-0xffffffff] has been reserved
[    0.140149] system 00:03: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.140208] pnp 00:04: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.140252] pnp 00:05: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.140300] pnp 00:06: Plug and Play ACPI device, IDs SYN1003 SYN1002 SYN1000 PNP0f13 (active)
[    0.140512] pnp: PnP ACPI: found 7 devices
[    0.140514] ACPI: bus type PNP unregistered
[    0.147550] Switched to clocksource acpi_pm
[    0.147578] pci 0000:00:06.0: res[15]=[mem 0x04000000-0x03ffffff pref] get_res_add_size add_size 4000000
[    0.147583] pci 0000:00:06.0: res[16]=[mem 0x04000000-0x03ffffff] get_res_add_size add_size 4000000
[    0.147586] pci 0000:00:06.0: res[13]=[io  0x0100-0x00ff] get_res_add_size add_size 100
[    0.147590] pci 0000:00:06.0: res[14]=[io  0x0100-0x00ff] get_res_add_size add_size 100
[    0.147597] pci 0000:00:06.0: BAR 0: assigned [mem 0x40000000-0x40000fff]
[    0.147606] pci 0000:00:06.0: BAR 15: assigned [mem 0x44000000-0x47ffffff pref]
[    0.147611] pci 0000:00:06.0: BAR 16: assigned [mem 0x48000000-0x4bffffff]
[    0.147615] pci 0000:00:04.0: BAR 6: assigned [mem 0x40020000-0x4003ffff pref]
[    0.147620] pci 0000:00:06.0: BAR 13: assigned [io  0x2400-0x24ff]
[    0.147625] pci 0000:00:06.0: BAR 14: assigned [io  0x2800-0x28ff]
[    0.147631] pci 0000:00:01.0: PCI bridge to [bus 01]
[    0.147635] pci 0000:00:01.0:   bridge window [io  0xa000-0xafff]
[    0.147641] pci 0000:00:01.0:   bridge window [mem 0xe2100000-0xe21fffff]
[    0.147646] pci 0000:00:01.0:   bridge window [mem 0xe8000000-0xefffffff pref]
[    0.147652] pci 0000:00:06.0: CardBus bridge to [bus 02-05]
[    0.147655] pci 0000:00:06.0:   bridge window [io  0x2400-0x24ff]
[    0.147660] pci 0000:00:06.0:   bridge window [io  0x2800-0x28ff]
[    0.147665] pci 0000:00:06.0:   bridge window [mem 0x44000000-0x47ffffff pref]
[    0.147670] pci 0000:00:06.0:   bridge window [mem 0x48000000-0x4bffffff]
[    0.147675] pci_bus 0000:00: resource 4 [io  0x0000-0xffff]
[    0.147679] pci_bus 0000:00: resource 5 [mem 0x000a0000-0x000bffff]
[    0.147682] pci_bus 0000:00: resource 6 [mem 0x40000000-0xfcffffffff]
[    0.147686] pci_bus 0000:01: resource 0 [io  0xa000-0xafff]
[    0.147689] pci_bus 0000:01: resource 1 [mem 0xe2100000-0xe21fffff]
[    0.147693] pci_bus 0000:01: resource 2 [mem 0xe8000000-0xefffffff pref]
[    0.147697] pci_bus 0000:02: resource 0 [io  0x2400-0x24ff]
[    0.147700] pci_bus 0000:02: resource 1 [io  0x2800-0x28ff]
[    0.147703] pci_bus 0000:02: resource 2 [mem 0x44000000-0x47ffffff pref]
[    0.147707] pci_bus 0000:02: resource 3 [mem 0x48000000-0x4bffffff]
[    0.147768] NET: Registered protocol family 2
[    0.147987] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
[    0.147987] TCP bind hash table entries: 8192 (order: 5, 131072 bytes)
[    0.147987] TCP: Hash tables configured (established 8192 bind 8192)
[    0.147987] TCP: reno registered
[    0.147987] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.147987] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.147987] NET: Registered protocol family 1
[    0.672229] pci 0000:01:00.0: Boot video device
[    0.672233] PCI: CLS 0 bytes, default 64
[    0.672353] Trying to unpack rootfs image as initramfs...
[    1.260899] Freeing initrd memory: 18728K (ffff880035b5c000 - ffff880036da6000)
[    1.261072] agpgart-amd64 0000:00:00.0: AGP bridge [1039/0760]
[    1.263259] agpgart-amd64 0000:00:00.0: AGP aperture is 32M @ 0xe0000000
[    1.263352] Simple Boot Flag at 0x38 set to 0x1
[    1.263457] microcode: AMD CPU family 0xf not supported
[    1.263460] Scanning for low memory corruption every 60 seconds
[    1.263790] Initialise system trusted keyring
[    1.263877] audit: initializing netlink socket (disabled)
[    1.263896] type=2000 audit(1411667327.259:1): initialized
[    1.307683] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.309895] zbud: loaded
[    1.310114] VFS: Disk quotas dquot_6.5.2
[    1.310194] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.311124] fuse init (API version 7.22)
[    1.311257] msgmni has been set to 1852
[    1.311358] Key type big_key registered
[    1.311815] Key type asymmetric registered
[    1.311818] Asymmetric key parser 'x509' registered
[    1.311881] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    1.311925] io scheduler noop registered
[    1.311928] io scheduler deadline registered (default)
[    1.311979] io scheduler cfq registered
[    1.312189] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.312221] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.312291] vesafb: mode is 640x480x32, linelength=2560, pages=0
[    1.312293] vesafb: scrolling: redraw
[    1.312297] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    1.312381] vesafb: framebuffer at 0xe8000000, mapped to 0xffffc90000200000, using 1216k, total 1216k
[    1.318867] Console: switching to colour frame buffer device 80x30
[    1.325196] fb0: VESA VGA frame buffer device
[    1.325260] ipmi message handler version 39.2
[    1.326171] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    1.327851] ACPI: AC Adapter [ACAD] (on-line)
[    1.327943] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    1.329512] ACPI: Lid Switch [LID]
[    1.329577] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    1.329583] ACPI: Power Button [PWRB]
[    1.329644] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    1.329648] ACPI: Sleep Button [SLPB]
[    1.329708] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    1.329712] ACPI: Power Button [PWRF]
[    1.329757] tsc: Marking TSC unstable due to TSC halts in idle
[    1.329768] ACPI: acpi_idle registered with cpuidle
[    1.337963] thermal LNXTHERM:00: registered as thermal_zone0
[    1.337966] ACPI: Thermal Zone [THRM] (57 C)
[    1.338035] GHES: HEST is not enabled!
[    1.338157] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.340448] Linux agpgart interface v0.103
[    1.342435] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    1.342443] ACPI: Battery Slot [BAT1] (battery absent)
[    1.342899] brd: module loaded
[    1.344163] loop: module loaded
[    1.344407] pata_sis 0000:00:02.5: version 0.5.2
[    1.344528] pata_sis 0000:00:02.5: SiS 962/963 MuTIOL IDE UDMA133 controller
[    1.345144] scsi0 : pata_sis
[    1.345245] scsi1 : pata_sis
[    1.345300] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x2000 irq 14
[    1.345304] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x2008 irq 15
[    1.345840] libphy: Fixed MDIO Bus: probed
[    1.346021] tun: Universal TUN/TAP device driver, 1.6
[    1.346023] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.346147] PPP generic driver version 2.4.2
[    1.346220] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.346227] ehci-pci: EHCI PCI platform driver
[    1.346347] ehci-pci 0000:00:03.2: EHCI Host Controller
[    1.346361] ehci-pci 0000:00:03.2: new USB bus registered, assigned bus number 1
[    1.346416] ehci-pci 0000:00:03.2: cache line size of 64 is not supported
[    1.346441] ehci-pci 0000:00:03.2: irq 23, io mem 0xe2004000
[    1.356093] ehci-pci 0000:00:03.2: USB 2.0 started, EHCI 1.00
[    1.356191] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    1.356196] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.356199] usb usb1: Product: EHCI Host Controller
[    1.356203] usb usb1: Manufacturer: Linux 3.13.0-36-generic ehci_hcd
[    1.356207] usb usb1: SerialNumber: 0000:00:03.2
[    1.356380] hub 1-0:1.0: USB hub found
[    1.356395] hub 1-0:1.0: 6 ports detected
[    1.356643] ehci-platform: EHCI generic platform driver
[    1.356657] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.356660] ohci-pci: OHCI PCI platform driver
[    1.356747] ohci-pci 0000:00:03.0: OHCI PCI host controller
[    1.356757] ohci-pci 0000:00:03.0: new USB bus registered, assigned bus number 2
[    1.356788] ohci-pci 0000:00:03.0: irq 20, io mem 0xe2002000
[    1.412125] usb usb2: New USB device found, idVendor=1d6b, idProduct=0001
[    1.412129] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.412133] usb usb2: Product: OHCI PCI host controller
[    1.412137] usb usb2: Manufacturer: Linux 3.13.0-36-generic ohci_hcd
[    1.412140] usb usb2: SerialNumber: 0000:00:03.0
[    1.412306] hub 2-0:1.0: USB hub found
[    1.412321] hub 2-0:1.0: 3 ports detected
[    1.412539] ohci-pci 0000:00:03.1: OHCI PCI host controller
[    1.412548] ohci-pci 0000:00:03.1: new USB bus registered, assigned bus number 3
[    1.412581] ohci-pci 0000:00:03.1: irq 21, io mem 0xe2003000
[    1.468078] usb usb3: New USB device found, idVendor=1d6b, idProduct=0001
[    1.468082] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.468086] usb usb3: Product: OHCI PCI host controller
[    1.468089] usb usb3: Manufacturer: Linux 3.13.0-36-generic ohci_hcd
[    1.468093] usb usb3: SerialNumber: 0000:00:03.1
[    1.468241] hub 3-0:1.0: USB hub found
[    1.468253] hub 3-0:1.0: 3 ports detected
[    1.468400] ohci-platform: OHCI generic platform driver
[    1.468414] uhci_hcd: USB Universal Host Controller Interface driver
[    1.468515] i8042: PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.471666] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.471675] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.471842] mousedev: PS/2 mouse device common for all mice
[    1.472115] rtc_cmos 00:01: RTC can wake from S4
[    1.472265] rtc_cmos 00:01: rtc core: registered rtc_cmos as rtc0
[    1.472293] rtc_cmos 00:01: alarms up to one year, y3k, 114 bytes nvram
[    1.472429] device-mapper: uevent: version 1.0.3
[    1.472551] device-mapper: ioctl: 4.27.0-ioctl (2013-10-30) initialised: [email]dm-devel@redhat.com[/email]
[    1.472562] ledtrig-cpu: registered to indicate activity on CPUs
[    1.472748] TCP: cubic registered
[    1.472921] NET: Registered protocol family 10
[    1.473269] NET: Registered protocol family 17
[    1.473286] Key type dns_resolver registered
[    1.473558] Loading compiled-in X.509 certificates
[    1.475297] Loaded X.509 cert 'Magrathea: Glacier signing key: 38f3b6c63a85affdfbbe0e53339df8e0c6b6c9d5'
[    1.475330] registered taskstats version 1
[    1.479168] Key type trusted registered
[    1.482156] Key type encrypted registered
[    1.485170] AppArmor: AppArmor sha1 policy hashing enabled
[    1.485177] IMA: No TPM chip found, activating TPM-bypass!
[    1.485428] regulator-dummy: disabling
[    1.485494]   Magic number: 14:488:846
[    1.485641] rtc_cmos 00:01: setting system clock to 2014-09-25 17:48:48 UTC (1411667328)
[    1.485801] powernow-k8: fid 0x8 (1600 MHz), vid 0x4
[    1.485804] powernow-k8: fid 0x0 (800 MHz), vid 0x16
[    1.485846] powernow-k8: Found 1 AMD Turion(tm) 64 Mobile Technology ML-30 (1 cpu cores) (version 2.20.00)
[    1.485853] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.485855] EDD information not available.
[    1.485901] PM: Hibernation image not present or could not be loaded.
[    1.506091] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    1.508314] ata1.00: ATA-6: ST9100824A, 3.06, max UDMA/100
[    1.508318] ata1.00: 195371568 sectors, multi 16: LBA48 
[    1.524326] ata1.00: configured for UDMA/100
[    1.524496] scsi 0:0:0:0: Direct-Access     ATA      ST9100824A       3.06 PQ: 0 ANSI: 5
[    1.524750] sd 0:0:0:0: [sda] 195371568 512-byte logical blocks: (100 GB/93.1 GiB)
[    1.524827] sd 0:0:0:0: [sda] Write Protect is off
[    1.524832] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.524866] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.525241] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.561256]  sda: sda1 sda2 < sda5 sda6 sda7 >
[    1.561743] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.688267] ata2.00: ATAPI: Slimtype DVDRW SOSW-833S, VRS2, max UDMA/33
[    1.704257] ata2.00: configured for UDMA/33
[    1.705190] scsi 1:0:0:0: CD-ROM            Slimtype DVDRW SOSW-833S  VRS2 PQ: 0 ANSI: 5
[    1.706872] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    1.706875] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.706988] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.707056] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.710479] Freeing unused kernel memory: 1336K (ffffffff81d1f000 - ffffffff81e6d000)
[    1.710489] Write protecting the kernel read-only data: 12288k
[    1.715402] Freeing unused kernel memory: 808K (ffff880001736000 - ffff880001800000)
[    1.719705] Freeing unused kernel memory: 692K (ffff880001b53000 - ffff880001c00000)
[    1.744329] systemd-udevd[95]: starting version 204
[    1.834718] sis900.c: v1.08.10 Apr. 2 2006
[    1.845711] 0000:00:04.0: Realtek RTL8201 PHY transceiver found at address 13.
[    1.851641] 0000:00:04.0: Using transceiver found at address 13 as default
[    1.860592] eth0: SiS 900 PCI Fast Ethernet at 0x0000000000011800, IRQ 19, 00:16:36:10:00:6b
[    2.512760] psmouse serio1: synaptics: Touchpad model: 1, fw: 6.2, id: 0x12a0b1, caps: 0xa04713/0x204000/0x0, board id: 3655, fw id: 41763
[    2.548228] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input6
[    2.984279] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
[    3.519420] random: nonblocking pool is initialized
[   10.443582] Adding 1060860k swap on /dev/sda7.  Priority:-1 extents:1 across:1060860k FS
[   10.560337] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   10.844830] systemd-udevd[253]: starting version 204
[   11.058096] lp: driver loaded but no devices found
[   11.084456] ppdev: user-space parallel port driver
[   11.223334] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   11.254396] sis96x_smbus 0000:00:02.1: SiS96x SMBus base address: 0x8100
[   11.259963] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro
[   11.464636] MCE: In-kernel MCE decoding enabled.
[   11.544491] yenta_cardbus 0000:00:06.0: enabling device (0000 -> 0003)
[   11.544632] yenta_cardbus 0000:00:06.0: CardBus bridge found [1025:0083]
[   11.544648] yenta_cardbus 0000:00:06.0: Using CSCINT to route CSC interrupts to PCI
[   11.544652] yenta_cardbus 0000:00:06.0: Routing CardBus interrupts to PCI
[   11.544657] yenta_cardbus 0000:00:06.0: TI: mfunc 0x00521d22, devctl 0x64
[   11.607003] EDAC MC: Ver: 3.0.0
[   11.607396] cfg80211: Calling CRDA to update world regulatory domain
[   11.643179] AMD64 EDAC driver v3.4.0
[   11.694255] lib80211: common routines for IEEE802.11 drivers
[   11.694264] lib80211_crypt: registered algorithm 'NULL'
[   11.722607] type=1400 audit(1411656538.732:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=327 comm="apparmor_parser"
[   11.722620] type=1400 audit(1411656538.732:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=327 comm="apparmor_parser"
[   11.722628] type=1400 audit(1411656538.732:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=327 comm="apparmor_parser"
[   11.723543] type=1400 audit(1411656538.732:5): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=327 comm="apparmor_parser"
[   11.723552] type=1400 audit(1411656538.732:6): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=327 comm="apparmor_parser"
[   11.729111] type=1400 audit(1411656538.740:7): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=327 comm="apparmor_parser"
[   11.754817] type=1400 audit(1411656538.764:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/ntpd" pid=338 comm="apparmor_parser"
[   11.776944] yenta_cardbus 0000:00:06.0: ISA IRQ mask 0x06f8, PCI irq 19
[   11.776952] yenta_cardbus 0000:00:06.0: Socket status: 30000006
[   11.853380] EDAC amd64: DRAM ECC disabled.
[   11.853391] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
[   11.853391]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
[   11.853391]  (Note that use of the override may cause unknown side effects.)
[   12.814230] wl: module license 'MIXED/Proprietary' taints kernel.
[   12.814240] Disabling lock debugging due to kernel taint
[   12.867660] wl: module verification failed: signature and/or  required key missing - tainting kernel
[   12.875453] cfg80211: World regulatory domain updated:
[   12.875460] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   12.875464] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   12.875467] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   12.875469] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   12.875472] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   12.875475] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   12.912978] resource map sanity check conflict: 0xe2000000 0xe2003fff 0xe2000000 0xe2001fff 0000:00:0b.0
[   12.912986] ------------[ cut here ]------------
[   12.912995] WARNING: CPU: 0 PID: 300 at /build/buildd/linux-3.13.0/arch/x86/mm/ioremap.c:171 __ioremap_caller+0x2d3/0x380()
[   12.912998] Info: mapping multiple BARs. Your kernel is fine.
[   12.913001] Modules linked in: wl(POX+) ac97_bus snd_pcm snd_page_alloc snd_seq_midi snd_seq_midi_event snd_rawmidi snd_seq pcmcia snd_seq_device snd_timer lib80211 snd joydev cfg80211 yenta_socket edac_core serio_raw k8temp edac_mce_amd pcmcia_rsrc pcmcia_core soundcore i2c_sis96x shpchp mac_hid parport_pc ppdev lp parport sis900 psmouse mii
[   12.913050] CPU: 0 PID: 300 Comm: systemd-udevd Tainted: P           OX 3.13.0-36-generic #63-Ubuntu
[   12.913053] Hardware name: Acer, inc. Aspire 5000     /Lugano M        , BIOS 3A32 02/20/06
[   12.913056]  0000000000000009 ffff8800393dfa00 ffffffff8171e569 ffff8800393dfa48
[   12.913061]  ffff8800393dfa38 ffffffff8106775d ffffc90000370000 00000000e2004000
[   12.913066]  ffffc90000370000 ffffc90000370000 0000000000004000 ffff8800393dfa98
[   12.913070] Call Trace:
[   12.913078]  [<ffffffff8171e569>] dump_stack+0x45/0x56
[   12.913084]  [<ffffffff8106775d>] warn_slowpath_common+0x7d/0xa0
[   12.913088]  [<ffffffff810677cc>] warn_slowpath_fmt+0x4c/0x50
[   12.913094]  [<ffffffff8106e988>] ? iomem_map_sanity_check+0xc8/0xd0
[   12.913098]  [<ffffffff81056b23>] __ioremap_caller+0x2d3/0x380
[   12.913102]  [<ffffffff81056be7>] ioremap_nocache+0x17/0x20
[   12.913197]  [<ffffffffa033126a>] wl_pci_probe+0x21a/0x6f0 [wl]
[   12.913204]  [<ffffffff811a2392>] ? kmem_cache_alloc+0x1b2/0x1e0
[   12.913211]  [<ffffffff813a84a5>] local_pci_probe+0x45/0xa0
[   12.913215]  [<ffffffff813a9745>] ? pci_match_device+0xc5/0xd0
[   12.913219]  [<ffffffff813a9869>] pci_device_probe+0xd9/0x130
[   12.913225]  [<ffffffff8149596d>] driver_probe_device+0x12d/0x3e0
[   12.913229]  [<ffffffff81495cf3>] __driver_attach+0x93/0xa0
[   12.913233]  [<ffffffff81495c60>] ? __device_attach+0x40/0x40
[   12.913237]  [<ffffffff814938d3>] bus_for_each_dev+0x63/0xa0
[   12.913241]  [<ffffffff8149531e>] driver_attach+0x1e/0x20
[   12.913245]  [<ffffffff81494f00>] bus_add_driver+0x180/0x250
[   12.913250]  [<ffffffffa05c2000>] ? 0xffffffffa05c1fff
[   12.913255]  [<ffffffff81496374>] driver_register+0x64/0xf0
[   12.913258]  [<ffffffffa05c2000>] ? 0xffffffffa05c1fff
[   12.913263]  [<ffffffff813a7e3c>] __pci_register_driver+0x4c/0x50
[   12.913293]  [<ffffffffa05c201e>] wl_module_init+0x1e/0x1000 [wl]
[   12.913298]  [<ffffffff8100214a>] do_one_initcall+0xfa/0x1b0
[   12.913304]  [<ffffffff810598d3>] ? set_memory_nx+0x43/0x50
[   12.913309]  [<ffffffff810e21ed>] load_module+0x12dd/0x1b40
[   12.913315]  [<ffffffff810ddc80>] ? store_uevent+0x40/0x40
[   12.913320]  [<ffffffff810e2bc6>] SyS_finit_module+0x86/0xb0
[   12.913325]  [<ffffffff8172efad>] system_call_fastpath+0x1a/0x1f
[   12.913327] ---[ end trace 7d73cba02224e72a ]---
[   12.965676] malloc in abgphy done
[   12.965914] wl driver 6.30.223.141 (r415941) failed with code 21
[   12.965954] ------------[ cut here ]------------
[   12.966109] kernel BUG at include/net/cfg80211.h:3150!
[   12.966268] invalid opcode: 0000 [#1] SMP 
[   12.966408] Modules linked in: wl(POX+) ac97_bus snd_pcm snd_page_alloc snd_seq_midi snd_seq_midi_event snd_rawmidi snd_seq pcmcia snd_seq_device snd_timer lib80211 snd joydev cfg80211 yenta_socket edac_core serio_raw k8temp edac_mce_amd pcmcia_rsrc pcmcia_core soundcore i2c_sis96x shpchp mac_hid parport_pc ppdev lp parport sis900 psmouse mii
[   12.967538] CPU: 0 PID: 300 Comm: systemd-udevd Tainted: P        W  OX 3.13.0-36-generic #63-Ubuntu
[   12.967817] Hardware name: Acer, inc. Aspire 5000     /Lugano M        , BIOS 3A32 02/20/06
[   12.968003] task: ffff880036c2c800 ti: ffff8800393de000 task.ti: ffff8800393de000
[   12.968003] RIP: 0010:[<ffffffffa0338e96>]  [<ffffffffa0338e96>] wdev_priv.part.9+0x4/0x6 [wl]
[   12.968003] RSP: 0018:ffff8800393df9f8  EFLAGS: 00010246
[   12.968003] RAX: 0000000000000000 RBX: ffff8800379a9000 RCX: 0000000000000fba
[   12.968003] RDX: ffff8800379a9000 RSI: ffff880037d91a58 RDI: ffff880037f4a000
[   12.968003] RBP: ffff8800393df9f8 R08: 0000000000000092 R09: 0000000000000278
[   12.968003] R10: 0000000000000000 R11: ffff8800393df846 R12: ffff880037d91a18
[   12.968003] R13: ffff880037d91a58 R14: ffff8800379a9000 R15: ffff880037d91a00
[   12.968003] FS:  00007f026d173880(0000) GS:ffff88003bc00000(0000) knlGS:0000000000000000
[   12.968003] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
[   12.968003] CR2: 00007fca0a859dd0 CR3: 00000000393da000 CR4: 00000000000007f0
[   12.968003] Stack:
[   12.968003]  ffff8800393dfa28 ffffffffa0338857 ffff8800379a9000 ffff880037d91a18
[   12.968003]  ffff880037d91a58 ffff8800379a9000 ffff8800393dfa50 ffffffffa0330676
[   12.968003]  ffff880037d91a00 ffff880037f4a000 0000000000000000 ffff8800393dfb08
[   12.968003] Call Trace:
[   12.968003]  [<ffffffffa0338857>] wl_cfg80211_detach+0x127/0x130 [wl]
[   12.968003]  [<ffffffffa0330676>] wl_free_if.isra.12+0x26/0xc0 [wl]
[   12.968003]  [<ffffffffa0330e3d>] wl_free+0x8d/0x2a0 [wl]
[   12.968003]  [<ffffffff8171820b>] ? printk+0x67/0x69
[   12.968003]  [<ffffffffa03313c4>] wl_pci_probe+0x374/0x6f0 [wl]
[   12.968003]  [<ffffffff813a84a5>] local_pci_probe+0x45/0xa0
[   12.968003]  [<ffffffff813a9745>] ? pci_match_device+0xc5/0xd0
[   12.968003]  [<ffffffff813a9869>] pci_device_probe+0xd9/0x130
[   12.968003]  [<ffffffff8149596d>] driver_probe_device+0x12d/0x3e0
[   12.968003]  [<ffffffff81495cf3>] __driver_attach+0x93/0xa0
[   12.968003]  [<ffffffff81495c60>] ? __device_attach+0x40/0x40
[   12.968003]  [<ffffffff814938d3>] bus_for_each_dev+0x63/0xa0
[   12.968003]  [<ffffffff8149531e>] driver_attach+0x1e/0x20
[   12.968003]  [<ffffffff81494f00>] bus_add_driver+0x180/0x250
[   12.968003]  [<ffffffffa05c2000>] ? 0xffffffffa05c1fff
[   12.968003]  [<ffffffff81496374>] driver_register+0x64/0xf0
[   12.968003]  [<ffffffffa05c2000>] ? 0xffffffffa05c1fff
[   12.968003]  [<ffffffff813a7e3c>] __pci_register_driver+0x4c/0x50
[   12.968003]  [<ffffffffa05c201e>] wl_module_init+0x1e/0x1000 [wl]
[   12.968003]  [<ffffffff8100214a>] do_one_initcall+0xfa/0x1b0
[   12.968003]  [<ffffffff810598d3>] ? set_memory_nx+0x43/0x50
[   12.968003]  [<ffffffff810e21ed>] load_module+0x12dd/0x1b40
[   12.968003]  [<ffffffff810ddc80>] ? store_uevent+0x40/0x40
[   12.968003]  [<ffffffff810e2bc6>] SyS_finit_module+0x86/0xb0
[   12.968003]  [<ffffffff8172efad>] system_call_fastpath+0x1a/0x1f
[   12.968003] Code: d0 c1 e8 10 66 39 c2 74 0c 0f b7 f6 66 66 66 90 66 66 90 eb 0a 89 f0 f0 0f b1 17 39 f0 75 ea 5d c3 55 48 89 e5 0f 0b 55 48 89 e5 <0f> 0b 66 66 66 66 90 55 48 89 e5 0f 0b 66 66 66 66 90 55 48 89 
[   12.968003] RIP  [<ffffffffa0338e96>] wdev_priv.part.9+0x4/0x6 [wl]
[   12.968003]  RSP <ffff8800393df9f8>
[   13.110217] ---[ end trace 7d73cba02224e72b ]---
[   13.386768] init: failsafe main process (463) killed by TERM signal
[   14.010694] type=1400 audit(1411656541.020:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=561 comm="apparmor_parser"
[   14.020893] type=1400 audit(1411656541.032:10): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cupsd" pid=561 comm="apparmor_parser"
[   14.093143] type=1400 audit(1411656541.104:11): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=561 comm="apparmor_parser"
[   14.342854] Bluetooth: Core ver 2.17
[   14.350785] NET: Registered protocol family 31
[   14.355056] Bluetooth: HCI device and connection manager initialized
[   14.366151] Bluetooth: HCI socket layer initialized
[   14.380091] Bluetooth: L2CAP socket layer initialized
[   14.403786] Bluetooth: SCO socket layer initialized
[   14.462305] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   14.466647] Bluetooth: BNEP filters: protocol multicast
[   14.482048] Bluetooth: BNEP socket layer initialized
[   14.492413] Bluetooth: RFCOMM TTY layer initialized
[   14.510371] Bluetooth: RFCOMM socket layer initialized
[   14.528479] Bluetooth: RFCOMM ver 1.11
[   16.109910] init: alsa-restore main process (730) terminated with status 19
[   18.240336] eth0: Media Link Off
[   18.619836] init: plymouth-upstart-bridge main process (144) killed by TERM signal
[   22.002306] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   23.250190] eth0: Media Link On 100mbps full-duplex
[   23.250234] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   43.666070] init: udev-fallback-graphics main process (1590) terminated with status 1
[   43.917192] init: plymouth-splash main process (1608) terminated with status 1
[  385.718525] systemd-hostnamed[1859]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
[  774.448438] eth0: Media Link Off
[  779.206788] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[  804.498555] eth0: Media Link On 100mbps full-duplex
[  804.498622] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  886.580441] eth0: Media Link Off
[  891.004130] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[  891.586504] eth0: Media Link On 100mbps full-duplex
[  891.586557] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 5024.396677] mtrr: no MTRR for e8000000,4000000 found
[ 8433.664400] eth0: Media Link Off
[ 8438.048883] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 8473.730569] eth0: Media Link On 100mbps full-duplex
[ 8473.731009] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 8903.212250] systemd-hostnamed[5669]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
[ 9930.210994] perf samples too long (2511 > 2500), lowering kernel.perf_event_max_sample_rate to 50000
[10025.627742] ndiswrapper version 1.59 loaded (smp=yes, preempt=no)
[10879.212656] wmi: Mapper loaded
[10879.270260] acer_wmi: Acer Laptop ACPI-WMI Extras
[10879.270286] acer_wmi: No or unsupported WMI interface, unable to load
[10988.088149] acer_wmi: Acer Laptop ACPI-WMI Extras
[10988.088177] acer_wmi: No or unsupported WMI interface, unable to load
[11520.540111] acer_wmi: Acer Laptop ACPI-WMI Extras
[11520.540139] acer_wmi: No or unsupported WMI interface, unable to load

---

### Post by xc3RnbFO8P on 2014-09-25
Well you got ndiswrapper running and I haven't used that since 2008,
as I recall you need 2 files 
how did you get them? 

I would uninstall ndiswrapper and dont know if it is enough just remove in Synaptic Package Manager
and do sudo apt-get update

Waybe someone have answer how to.

---

### Post by alin4 on 2014-09-25
the laptop is dual boot, so i got the files form the windows xp driver, from the other partition. But it failed on me at one point. I tried everything i could find on the forums. Thanks.

---

### Post by xc3RnbFO8P on 2014-09-25
Can make a fresh install of Ubuntu, sometime it is easier than struggle to repair a damage one

---

### Post by alin4 on 2014-09-26
Yes, no problem. And after i make a fresh install, what should i run in the terminal, for not mixing the things again?

---

### Post by mörgæs on 2014-09-26
Please read the sticky notes.

---

