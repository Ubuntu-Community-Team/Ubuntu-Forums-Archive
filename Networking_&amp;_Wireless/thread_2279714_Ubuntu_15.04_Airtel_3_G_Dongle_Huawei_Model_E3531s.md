---
title: "Ubuntu 15.04 Airtel 3 G Dongle Huawei Model E3531s -1 : Signal not detected"
date: 2015-05-25
forum: Networking &amp; Wireless
---

### Post by Mohit_Jiindal on 2015-05-25
Hi!

  I am using Airtel3G Dongle of Huawei E3531s-1 on my HP Notebook 430 but I am unable to get the dongle working. Very rarely does it shows the signal and almost 99.99% of time it doesn't shows any signal and doesn't facilitate ability for me to get connected to Internet as visible from screenshots. Please help troubleshoot and get the dongle working again. Screenshots and dmesg | grep tty command result enclosed.


```

mjiindal@MJ-Lappy:~$ dmesg | grep tty
[    0.000000] console [tty0] enabled
[    8.150012] systemd[1]: Created slice system-getty.slice.
[    8.150022] systemd[1]: Starting system-getty.slice.
[  338.488317] usb 2-1.1: GSM modem (1-port) converter now attached to ttyUSB0
[  338.488667] usb 2-1.1: GSM modem (1-port) converter now attached to ttyUSB1
[  338.488965] usb 2-1.1: GSM modem (1-port) converter now attached to ttyUSB2
[ 4128.237343] option1 ttyUSB0: usb_wwan_indat_callback: resubmit read urb failed. (-2)
[ 4128.237357] option1 ttyUSB0: usb_wwan_indat_callback: resubmit read urb failed. (-2)
[ 4128.237398] option1 ttyUSB0: usb_wwan_indat_callback: resubmit read urb failed. (-2)
[ 4128.241578] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
[ 4128.263291] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
[ 4128.263825] option1 ttyUSB2: usb_wwan_indat_callback: resubmit read urb failed. (-2)
[ 4128.263829] option1 ttyUSB2: usb_wwan_indat_callback: resubmit read urb failed. (-2)
[ 4128.263831] option1 ttyUSB2: usb_wwan_indat_callback: resubmit read urb failed. (-2)
[ 4128.267891] option1 ttyUSB2: GSM modem (1-port) converter now disconnected from ttyUSB2
[ 4128.287724] usb 2-1.1: GSM modem (1-port) converter now attached to ttyUSB1
[ 4128.287892] usb 2-1.1: GSM modem (1-port) converter now attached to ttyUSB3
[ 4128.288010] usb 2-1.1: GSM modem (1-port) converter now attached to ttyUSB4
[ 4128.288157] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
[ 4128.288332] option1 ttyUSB3: GSM modem (1-port) converter now disconnected from ttyUSB3
[ 4128.288439] option1 ttyUSB4: GSM modem (1-port) converter now disconnected from ttyUSB4
[ 6574.098983] usb 2-1.1: GSM modem (1-port) converter now attached to ttyUSB1
[ 6574.099642] usb 2-1.1: GSM modem (1-port) converter now attached to ttyUSB4
[ 6574.099824] usb 2-1.1: GSM modem (1-port) converter now attached to ttyUSB5

```

[IMG]http://i.imgur.com/ae82dJr.png[/IMG]
[IMG]http://i.imgur.com/vgDssuN.png[/IMG][IMG]http://i.imgur.com/YmNgCmM.png[/IMG]
 Hi!

---

### Post by Mohit_Jiindal on 2015-05-25
Here is the output of lsusb command: 
```
Bus 002 Device 008: ID 12d1:1506 Huawei Technologies Co., Ltd. E398 LTE/UMTS/GSM Modem/Networkcard
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 0cf3:3005 Atheros Communications, Inc. AR3011 Bluetooth
Bus 001 Device 003: ID 0c45:6321 Microdia 
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


```

Here is the output of dmesg command which I thought may be required for diagnostic purpose:

```

mjiindal@MJ-Lappy:~$ dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 3.19.0-18-generic (buildd@lamiak) (gcc version 4.9.2 (Ubuntu 4.9.2-10ubuntu13) ) #18-Ubuntu SMP Tue May 19 18:30:59 UTC 2015 (Ubuntu 3.19.0-18.18-generic 3.19.6)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009cbff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009cc00-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x000000007763efff] usable
[    0.000000] BIOS-e820: [mem 0x000000007763f000-0x00000000776befff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000776bf000-0x00000000777befff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000777bf000-0x00000000777fefff] ACPI data
[    0.000000] BIOS-e820: [mem 0x00000000777ff000-0x00000000777fffff] usable
[    0.000000] BIOS-e820: [mem 0x0000000077800000-0x000000007bffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000e0000000-0x00000000efffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000feb00000-0x00000000feb03fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed10000-0x00000000fed13fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed18000-0x00000000fed19fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed1b000-0x00000000fed1ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ffe00000-0x00000000ffffffff] reserved
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.6 present.
[    0.000000] DMI: Hewlett-Packard HP 430 Notebook PC              /3674, BIOS F.24 09/22/2011
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] e820: last_pfn = 0x77800 max_arch_pfn = 0x1000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-EFFFF write-through
[    0.000000]   F0000-FFFFF write-combining
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask FC0000000 write-back
[    0.000000]   1 base 0FFE00000 mask FFFE00000 write-protect
[    0.000000]   2 base 040000000 mask FC0000000 write-back
[    0.000000]   3 base 078000000 mask FF8000000 uncachable
[    0.000000]   4 base 077800000 mask FFF800000 uncachable
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] PAT configuration [0-7]: WB  WC  UC- UC  WB  WC  UC- UC  
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] initial memory mapped: [mem 0x00000000-0x021fffff]
[    0.000000] Base memory trampoline at [c0098000] 98000 size 16384
[    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
[    0.000000]  [mem 0x00000000-0x000fffff] page 4k
[    0.000000] init_memory_mapping: [mem 0x37800000-0x379fffff]
[    0.000000]  [mem 0x37800000-0x379fffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x20000000-0x377fffff]
[    0.000000]  [mem 0x20000000-0x377fffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x00100000-0x1fffffff]
[    0.000000]  [mem 0x00100000-0x001fffff] page 4k
[    0.000000]  [mem 0x00200000-0x1fffffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x37a00000-0x37bfdfff]
[    0.000000]  [mem 0x37a00000-0x37bfdfff] page 4k
[    0.000000] BRK [0x01c52000, 0x01c52fff] PGTABLE
[    0.000000] BRK [0x01c53000, 0x01c53fff] PGTABLE
[    0.000000] RAMDISK: [mem 0x3571e000-0x36b86fff]
[    0.000000] ACPI: Early table checksum verification disabled
[    0.000000] ACPI: RSDP 0x000FE020 000024 (v02 HPQOEM)
[    0.000000] ACPI: XSDT 0x777FE120 000074 (v01 HPQOEM SLIC-MPC 00000001      01000013)
[    0.000000] ACPI: FACP 0x777FC000 0000F4 (v04 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
[    0.000000] ACPI: DSDT 0x777ED000 00BEC7 (v02 HP     INSYDE   00000001 MSFT 01000013)
[    0.000000] ACPI: FACS 0x7776D000 000040
[    0.000000] ACPI: ASF! 0x777FD000 0000A5 (v32 HP     INSYDE   00000001 MSFT 01000013)
[    0.000000] ACPI: HPET 0x777FB000 000038 (v01 HP     INSYDE   00000001 MSFT 01000013)
[    0.000000] ACPI: APIC 0x777FA000 00008C (v02 HP     INSYDE   00000001 MSFT 01000013)
[    0.000000] ACPI: MCFG 0x777F9000 00003C (v01 HP     INSYDE   00000001 MSFT 01000013)
[    0.000000] ACPI: SLIC 0x777EC000 000176 (v01 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
[    0.000000] ACPI: BOOT 0x777E8000 000028 (v01 HP     INSYDE   00000001 MSFT 01000013)
[    0.000000] ACPI: ASPT 0x777E5000 000034 (v04 HP     INSYDE   00000001 MSFT 01000013)
[    0.000000] ACPI: WDAT 0x777E4000 000224 (v01 HP     INSYDE   00000001 MSFT 01000013)
[    0.000000] ACPI: SSDT 0x777E3000 0009F1 (v01 PmRef  CpuPm    00003000 INTL 20051117)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 1020MB HIGHMEM available.
[    0.000000] 891MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 37bfe000
[    0.000000]   low ram: 0 - 37bfe000
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00001000-0x00ffffff]
[    0.000000]   Normal   [mem 0x01000000-0x37bfdfff]
[    0.000000]   HighMem  [mem 0x37bfe000-0x777fffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00001000-0x0009bfff]
[    0.000000]   node   0: [mem 0x00100000-0x7763efff]
[    0.000000]   node   0: [mem 0x777ff000-0x777fffff]
[    0.000000] Initmem setup node 0 [mem 0x00001000-0x777fffff]
[    0.000000] On node 0 totalpages: 488923
[    0.000000]   DMA zone: 40 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3995 pages, LIFO batch:0
[    0.000000]   Normal zone: 2190 pages used for memmap
[    0.000000]   Normal zone: 224254 pages, LIFO batch:31
[    0.000000]   HighMem zone: 260674 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] Reserving Intel graphics stolen memory at 0x7a000000-0x7bffffff
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x04] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x05] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x00] disabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] smpboot: Allowing 8 CPUs, 4 hotplug CPUs
[    0.000000] PM: Registered nosave memory: [mem 0x00000000-0x00000fff]
[    0.000000] PM: Registered nosave memory: [mem 0x0009c000-0x0009cfff]
[    0.000000] PM: Registered nosave memory: [mem 0x0009d000-0x0009ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000e0000-0x000fffff]
[    0.000000] e820: [mem 0x7c000000-0xdfffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:8 nr_node_ids:1
[    0.000000] PERCPU: Embedded 17 pages/cpu @f6c4f000 s40320 r0 d29312 u69632
[    0.000000] pcpu-alloc: s40320 r0 d29312 u69632 alloc=17*4096
[    0.000000] pcpu-alloc: [0] 0 [0] 1 [0] 2 [0] 3 [0] 4 [0] 5 [0] 6 [0] 7 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 486693
[    0.000000] Kernel command line: BOOT_IMAGE=/vmlinuz-3.19.0-18-generic root=/dev/mapper/ubuntu--vg-root ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] CPU0 microcode updated early to revision 0x4, date = 2013-06-28
[    0.000000] Initializing CPU#0
[    0.000000] Initializing HighMem for node 0 (00037bfe:00077800)
[    0.000000] Initializing Movable for node 0 (00000000:00000000)
[    0.000000] Memory: 1900116K/1955692K available (7110K kernel code, 709K rwdata, 2996K rodata, 888K init, 796K bss, 55576K reserved, 0K cma-reserved, 1042696K highmem)
[    0.000000] virtual kernel memory layout:
    fixmap  : 0xfff15000 - 0xfffff000   ( 936 kB)
    pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
    vmalloc : 0xf83fe000 - 0xffbfe000   ( 120 MB)
    lowmem  : 0xc0000000 - 0xf7bfe000   ( 891 MB)
      .init : 0xc1a93000 - 0xc1b71000   ( 888 kB)
      .data : 0xc16f1c36 - 0xc1a91780   (3710 kB)
      .text : 0xc1000000 - 0xc16f1c36   (7111 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:2304 nr_irqs:488 16
[    0.000000] CPU 0 irqstacks, hard=f4c38000 soft=f4c3a000
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.000000] tsc: Detected 2526.828 MHz processor
[    0.000034] Calibrating delay loop (skipped), value calculated using timer frequency.. 5053.65 BogoMIPS (lpj=10107312)
[    0.000037] pid_max: default: 32768 minimum: 301
[    0.000042] ACPI: Core revision 20141107
[    0.012048] ACPI: All ACPI Tables successfully acquired
[    0.041517] Security Framework initialized
[    0.041536] AppArmor: AppArmor initialized
[    0.041538] Yama: becoming mindful.
[    0.041580] Mount-cache hash table entries: 2048 (order: 1, 8192 bytes)
[    0.041582] Mountpoint-cache hash table entries: 2048 (order: 1, 8192 bytes)
[    0.041771] Initializing cgroup subsys memory
[    0.041777] Initializing cgroup subsys devices
[    0.041779] Initializing cgroup subsys freezer
[    0.041781] Initializing cgroup subsys net_cls
[    0.041784] Initializing cgroup subsys blkio
[    0.041786] Initializing cgroup subsys perf_event
[    0.041788] Initializing cgroup subsys net_prio
[    0.041791] Initializing cgroup subsys hugetlb
[    0.041812] CPU: Physical Processor ID: 0
[    0.041813] CPU: Processor Core ID: 0
[    0.041818] mce: CPU supports 9 MCE banks
[    0.041826] CPU0: Thermal monitoring handled by SMI
[    0.041838] Last level iTLB entries: 4KB 512, 2MB 7, 4MB 7
Last level dTLB entries: 4KB 512, 2MB 32, 4MB 32, 1GB 0
[    0.042291] Freeing SMP alternatives memory: 32K (c1b71000 - c1b79000)
[    0.043317] ftrace: allocating 29375 entries in 58 pages
[    0.056485] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.056993] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.096653] smpboot: CPU0: Intel(R) Core(TM) i3 CPU       M 380  @ 2.53GHz (fam: 06, model: 25, stepping: 05)
[    0.202838] Performance Events: PEBS fmt1+, 16-deep LBR, Westmere events, Intel PMU driver.
[    0.202856] perf_event_intel: CPUID marked event: 'bus cycles' unavailable
[    0.202858] ... version:                3
[    0.202859] ... bit width:              48
[    0.202860] ... generic registers:      4
[    0.202861] ... value mask:             0000ffffffffffff
[    0.202862] ... max period:             000000007fffffff
[    0.202863] ... fixed-purpose events:   3
[    0.202864] ... event mask:             000000070000000f
[    0.203738] CPU 1 irqstacks, hard=f4d98000 soft=f4d9a000
[    0.203740] x86: Booting SMP configuration:
[    0.203742] .... node  #0, CPUs:      #1
[    0.214661] Initializing CPU#1
[    0.214696] CPU1: Thermal monitoring handled by SMI
[    0.216900] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.217005] CPU 2 irqstacks, hard=f4e90000 soft=f4e92000
[    0.217007]  #2
[    0.227926] CPU2 microcode updated early to revision 0x4, date = 2013-06-28
[    0.227928] Initializing CPU#2
[    0.227959] CPU2: Thermal monitoring handled by SMI
[    0.230151] CPU 3 irqstacks, hard=f4ece000 soft=f4ed8000
[    0.230155]  #3
[    0.241072] Initializing CPU#3
[    0.241104] CPU3: Thermal monitoring handled by SMI
[    0.243216] x86: Booted up 1 node, 4 CPUs
[    0.243221] smpboot: Total of 4 processors activated (20214.62 BogoMIPS)
[    0.245774] devtmpfs: initialized
[    0.246074] evm: security.selinux
[    0.246075] evm: security.SMACK64
[    0.246076] evm: security.SMACK64EXEC
[    0.246077] evm: security.SMACK64TRANSMUTE
[    0.246078] evm: security.SMACK64MMAP
[    0.246079] evm: security.ima
[    0.246080] evm: security.capability
[    0.246168] PM: Registering ACPI NVS region [mem 0x776bf000-0x777befff] (1048576 bytes)
[    0.246364] pinctrl core: initialized pinctrl subsystem
[    0.246485] RTC time: 15:35:14, date: 05/25/15
[    0.246596] NET: Registered protocol family 16
[    0.246806] EISA bus registered
[    0.258793] cpuidle: using governor ladder
[    0.270038] cpuidle: using governor menu
[    0.270177] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.270179] ACPI: bus type PCI registered
[    0.270181] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.270270] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.270273] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    0.270274] PCI: Using MMCONFIG for extended config space
[    0.270276] PCI: Using configuration type 1 for base access
[    0.270429] mtrr: your CPUs had inconsistent variable MTRR settings
[    0.270430] mtrr: probably your BIOS does not setup all CPUs.
[    0.270431] mtrr: corrected configuration.
[    0.283273] ACPI: Added _OSI(Module Device)
[    0.283275] ACPI: Added _OSI(Processor Device)
[    0.283277] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.283278] ACPI: Added _OSI(Processor Aggregator Device)
[    0.286872] ACPI: Executed 1 blocks of module-level executable AML code
[    0.289264] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.289636] ACPI: Dynamic OEM Table Load:
[    0.289644] ACPI: SSDT 0xF4F91000 000474 (v01 PmRef  Cpu0Ist  00003000 INTL 20051117)
[    0.290246] ACPI: Dynamic OEM Table Load:
[    0.290253] ACPI: SSDT 0xF4EA1000 000891 (v01 PmRef  Cpu0Cst  00003001 INTL 20051117)
[    0.291148] ACPI: Dynamic OEM Table Load:
[    0.291154] ACPI: SSDT 0xF4E9A000 000303 (v01 PmRef  ApIst    00003000 INTL 20051117)
[    0.291754] ACPI: Dynamic OEM Table Load:
[    0.291759] ACPI: SSDT 0xF4F74800 000119 (v01 PmRef  ApCst    00003000 INTL 20051117)
[    0.713217] ACPI: Interpreter enabled
[    0.713233] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20141107/hwxface-580)
[    0.713239] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20141107/hwxface-580)
[    0.713258] ACPI: (supports S0 S3 S4 S5)
[    0.713260] ACPI: Using IOAPIC for interrupt routing
[    0.713293] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.764376] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-fe])
[    0.764382] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    0.764417] \_SB_.PCI0:_OSC invalid UUID
[    0.764419] _OSC request data:1 1f 0 
[    0.764423] acpi PNP0A08:00: _OSC failed (AE_ERROR); disabling ASPM
[    0.765175] PCI host bridge to bus 0000:00
[    0.765178] pci_bus 0000:00: root bus resource [bus 00-fe]
[    0.765180] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
[    0.765182] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
[    0.765184] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    0.765186] pci_bus 0000:00: root bus resource [mem 0x7c000000-0xfeafffff]
[    0.765195] pci 0000:00:00.0: [8086:0044] type 00 class 0x060000
[    0.765217] DMAR: Disabling batched IOTLB flush on Ironlake
[    0.765294] pci 0000:00:02.0: [8086:0046] type 00 class 0x030000
[    0.765306] pci 0000:00:02.0: reg 0x10: [mem 0x90000000-0x903fffff 64bit]
[    0.765313] pci 0000:00:02.0: reg 0x18: [mem 0x80000000-0x8fffffff 64bit pref]
[    0.765318] pci 0000:00:02.0: reg 0x20: [io  0x4050-0x4057]
[    0.765441] pci 0000:00:16.0: [8086:3b64] type 00 class 0x078000
[    0.765472] pci 0000:00:16.0: reg 0x10: [mem 0x96404000-0x9640400f 64bit]
[    0.765568] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    0.765671] pci 0000:00:1a.0: [8086:3b3c] type 00 class 0x0c0320
[    0.766138] pci 0000:00:1a.0: reg 0x10: [mem 0x9640a000-0x9640a3ff]
[    0.768800] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    0.768864] pci 0000:00:1a.0: System wakeup disabled by ACPI
[    0.768917] pci 0000:00:1b.0: [8086:3b56] type 00 class 0x040300
[    0.768941] pci 0000:00:1b.0: reg 0x10: [mem 0x96400000-0x96403fff 64bit]
[    0.769054] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.769103] pci 0000:00:1b.0: System wakeup disabled by ACPI
[    0.769151] pci 0000:00:1c.0: [8086:3b42] type 01 class 0x060400
[    0.769261] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.769311] pci 0000:00:1c.0: System wakeup disabled by ACPI
[    0.769361] pci 0000:00:1c.2: [8086:3b46] type 01 class 0x060400
[    0.769471] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.769520] pci 0000:00:1c.2: System wakeup disabled by ACPI
[    0.769570] pci 0000:00:1c.4: [8086:3b4a] type 01 class 0x060400
[    0.769678] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.769727] pci 0000:00:1c.4: System wakeup disabled by ACPI
[    0.769784] pci 0000:00:1d.0: [8086:3b34] type 00 class 0x0c0320
[    0.770237] pci 0000:00:1d.0: reg 0x10: [mem 0x96409000-0x964093ff]
[    0.772892] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    0.772956] pci 0000:00:1d.0: System wakeup disabled by ACPI
[    0.773002] pci 0000:00:1e.0: [8086:2448] type 01 class 0x060401
[    0.773111] pci 0000:00:1e.0: System wakeup disabled by ACPI
[    0.773157] pci 0000:00:1f.0: [8086:3b09] type 00 class 0x060100
[    0.773345] pci 0000:00:1f.2: [8086:3b29] type 00 class 0x010601
[    0.773373] pci 0000:00:1f.2: reg 0x10: [io  0x4048-0x404f]
[    0.773384] pci 0000:00:1f.2: reg 0x14: [io  0x405c-0x405f]
[    0.773395] pci 0000:00:1f.2: reg 0x18: [io  0x4040-0x4047]
[    0.773406] pci 0000:00:1f.2: reg 0x1c: [io  0x4058-0x405b]
[    0.773417] pci 0000:00:1f.2: reg 0x20: [io  0x4020-0x403f]
[    0.773428] pci 0000:00:1f.2: reg 0x24: [mem 0x96408000-0x964087ff]
[    0.773498] pci 0000:00:1f.2: PME# supported from D3hot
[    0.773580] pci 0000:00:1f.3: [8086:3b30] type 00 class 0x0c0500
[    0.773602] pci 0000:00:1f.3: reg 0x10: [mem 0x96406000-0x964060ff 64bit]
[    0.773632] pci 0000:00:1f.3: reg 0x20: [io  0x4000-0x401f]
[    0.773867] pci 0000:01:00.0: [10ec:8168] type 00 class 0x020000
[    0.773944] pci 0000:01:00.0: reg 0x10: [io  0x3000-0x30ff]
[    0.774031] pci 0000:01:00.0: reg 0x18: [mem 0x90404000-0x90404fff 64bit pref]
[    0.774101] pci 0000:01:00.0: reg 0x20: [mem 0x90400000-0x90403fff 64bit pref]
[    0.774457] pci 0000:01:00.0: supports D1 D2
[    0.774459] pci 0000:01:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.775466] pci 0000:01:00.0: System wakeup disabled by ACPI
[    0.775585] pci 0000:00:1c.0: PCI bridge to [bus 01]
[    0.775591] pci 0000:00:1c.0:   bridge window [io  0x3000-0x3fff]
[    0.775595] pci 0000:00:1c.0:   bridge window [mem 0x95400000-0x963fffff]
[    0.775603] pci 0000:00:1c.0:   bridge window [mem 0x90400000-0x913fffff 64bit pref]
[    0.775727] pci 0000:02:00.0: [168c:002b] type 00 class 0x028000
[    0.775775] pci 0000:02:00.0: reg 0x10: [mem 0x94400000-0x9440ffff 64bit]
[    0.776041] pci 0000:02:00.0: supports D1
[    0.776044] pci 0000:02:00.0: PME# supported from D0 D1 D3hot
[    0.776105] pci 0000:02:00.0: System wakeup disabled by ACPI
[    0.776171] pci 0000:00:1c.2: PCI bridge to [bus 02]
[    0.776176] pci 0000:00:1c.2:   bridge window [io  0x2000-0x2fff]
[    0.776180] pci 0000:00:1c.2:   bridge window [mem 0x94400000-0x953fffff]
[    0.776188] pci 0000:00:1c.2:   bridge window [mem 0x91400000-0x923fffff 64bit pref]
[    0.776354] pci 0000:03:00.0: [10ec:5209] type 00 class 0xff0000
[    0.776436] pci 0000:03:00.0: reg 0x10: [mem 0x93400000-0x93400fff]
[    0.776976] pci 0000:03:00.0: supports D1 D2
[    0.776977] pci 0000:03:00.0: PME# supported from D1 D2 D3hot
[    0.777053] pci 0000:03:00.0: System wakeup disabled by ACPI
[    0.777159] pci 0000:00:1c.4: PCI bridge to [bus 03]
[    0.777163] pci 0000:00:1c.4:   bridge window [io  0x1000-0x1fff]
[    0.777168] pci 0000:00:1c.4:   bridge window [mem 0x93400000-0x943fffff]
[    0.777176] pci 0000:00:1c.4:   bridge window [mem 0x92400000-0x933fffff 64bit pref]
[    0.777263] pci 0000:00:1e.0: PCI bridge to [bus 04] (subtractive decode)
[    0.777276] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.777278] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.777280] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.777282] pci 0000:00:1e.0:   bridge window [mem 0x7c000000-0xfeafffff] (subtractive decode)
[    0.777328] pci_bus 0000:00: on NUMA node 0
[    0.777743] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[    0.777798] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    0.777851] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    0.777904] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    0.777956] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    0.778009] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.778061] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[    0.778113] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.799646] ACPI: PCI Root Bridge [CPBG] (domain 0000 [bus ff])
[    0.799651] acpi PNP0A03:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    0.799656] acpi PNP0A03:00: _OSC failed (AE_NOT_FOUND); disabling ASPM
[    0.799725] PCI host bridge to bus 0000:ff
[    0.799728] pci_bus 0000:ff: root bus resource [bus ff]
[    0.799735] pci 0000:ff:00.0: [8086:2c62] type 00 class 0x060000
[    0.799788] pci 0000:ff:00.1: [8086:2d01] type 00 class 0x060000
[    0.799843] pci 0000:ff:02.0: [8086:2d10] type 00 class 0x060000
[    0.799892] pci 0000:ff:02.1: [8086:2d11] type 00 class 0x060000
[    0.799940] pci 0000:ff:02.2: [8086:2d12] type 00 class 0x060000
[    0.799990] pci 0000:ff:02.3: [8086:2d13] type 00 class 0x060000
[    0.800048] pci_bus 0000:ff: on NUMA node 0
[    0.800112] ACPI: Enabled 6 GPEs in block 00 to 3F
[    0.800170] ACPI : EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
[    0.800279] vgaarb: setting as boot device: PCI:0000:00:02.0
[    0.800281] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.800285] vgaarb: loaded
[    0.800286] vgaarb: bridge control possible 0000:00:02.0
[    0.800573] SCSI subsystem initialized
[    0.800618] libata version 3.00 loaded.
[    0.800645] ACPI: bus type USB registered
[    0.800666] usbcore: registered new interface driver usbfs
[    0.800676] usbcore: registered new interface driver hub
[    0.800697] usbcore: registered new device driver usb
[    0.800850] PCI: Using ACPI for IRQ routing
[    0.810718] PCI: pci_cache_line_size set to 64 bytes
[    0.810801] e820: reserve RAM buffer [mem 0x0009cc00-0x0009ffff]
[    0.810803] e820: reserve RAM buffer [mem 0x7763f000-0x77ffffff]
[    0.810804] e820: reserve RAM buffer [mem 0x77800000-0x77ffffff]
[    0.810925] NetLabel: Initializing
[    0.810927] NetLabel:  domain hash size = 128
[    0.810928] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.810939] NetLabel:  unlabeled traffic allowed by default
[    0.811052] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    0.811057] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    0.813102] Switched to clocksource hpet
[    0.820693] AppArmor: AppArmor Filesystem Enabled
[    0.820782] pnp: PnP ACPI init
[    0.820925] pnp 00:00: disabling [io  0x164e-0x164f] because it overlaps 0000:00:1c.4 BAR 13 [io  0x1000-0x1fff]
[    0.820971] system 00:00: [io  0x0680-0x069f] has been reserved
[    0.820973] system 00:00: [io  0x0800-0x080f] has been reserved
[    0.820975] system 00:00: [io  0x0810-0x0813] has been reserved
[    0.820977] system 00:00: [io  0xffff] has been reserved
[    0.820979] system 00:00: [io  0x0400-0x047f] could not be reserved
[    0.820981] system 00:00: [io  0x0500-0x057f] has been reserved
[    0.820985] system 00:00: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.821027] pnp 00:01: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.821058] pnp 00:02: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.821088] pnp 00:03: Plug and Play ACPI device, IDs SYN1e4a SYN1e00 SYN0002 PNP0f13 (active)
[    0.821393] system 00:04: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.821395] system 00:04: [mem 0xfed10000-0xfed13fff] has been reserved
[    0.821399] system 00:04: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.821401] system 00:04: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.821403] system 00:04: [mem 0xe0000000-0xefffffff] has been reserved
[    0.821405] system 00:04: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.821407] system 00:04: [mem 0xff000000-0xffffffff] could not be reserved
[    0.821409] system 00:04: [mem 0xfee00000-0xfeefffff] could not be reserved
[    0.821411] system 00:04: [mem 0x7c000000-0x7c000fff] has been reserved
[    0.821414] system 00:04: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.845750] pnp: PnP ACPI: found 5 devices
[    0.845757] PnPBIOS: Disabled by ACPI PNP
[    0.883182] pci 0000:00:1c.0: PCI bridge to [bus 01]
[    0.883188] pci 0000:00:1c.0:   bridge window [io  0x3000-0x3fff]
[    0.883195] pci 0000:00:1c.0:   bridge window [mem 0x95400000-0x963fffff]
[    0.883200] pci 0000:00:1c.0:   bridge window [mem 0x90400000-0x913fffff 64bit pref]
[    0.883207] pci 0000:00:1c.2: PCI bridge to [bus 02]
[    0.883211] pci 0000:00:1c.2:   bridge window [io  0x2000-0x2fff]
[    0.883217] pci 0000:00:1c.2:   bridge window [mem 0x94400000-0x953fffff]
[    0.883221] pci 0000:00:1c.2:   bridge window [mem 0x91400000-0x923fffff 64bit pref]
[    0.883229] pci 0000:00:1c.4: PCI bridge to [bus 03]
[    0.883232] pci 0000:00:1c.4:   bridge window [io  0x1000-0x1fff]
[    0.883238] pci 0000:00:1c.4:   bridge window [mem 0x93400000-0x943fffff]
[    0.883243] pci 0000:00:1c.4:   bridge window [mem 0x92400000-0x933fffff 64bit pref]
[    0.883250] pci 0000:00:1e.0: PCI bridge to [bus 04]
[    0.883265] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.883267] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.883269] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.883271] pci_bus 0000:00: resource 7 [mem 0x7c000000-0xfeafffff]
[    0.883273] pci_bus 0000:01: resource 0 [io  0x3000-0x3fff]
[    0.883275] pci_bus 0000:01: resource 1 [mem 0x95400000-0x963fffff]
[    0.883277] pci_bus 0000:01: resource 2 [mem 0x90400000-0x913fffff 64bit pref]
[    0.883279] pci_bus 0000:02: resource 0 [io  0x2000-0x2fff]
[    0.883280] pci_bus 0000:02: resource 1 [mem 0x94400000-0x953fffff]
[    0.883282] pci_bus 0000:02: resource 2 [mem 0x91400000-0x923fffff 64bit pref]
[    0.883284] pci_bus 0000:03: resource 0 [io  0x1000-0x1fff]
[    0.883286] pci_bus 0000:03: resource 1 [mem 0x93400000-0x943fffff]
[    0.883288] pci_bus 0000:03: resource 2 [mem 0x92400000-0x933fffff 64bit pref]
[    0.883290] pci_bus 0000:04: resource 4 [io  0x0000-0x0cf7]
[    0.883292] pci_bus 0000:04: resource 5 [io  0x0d00-0xffff]
[    0.883294] pci_bus 0000:04: resource 6 [mem 0x000a0000-0x000bffff]
[    0.883295] pci_bus 0000:04: resource 7 [mem 0x7c000000-0xfeafffff]
[    0.883329] NET: Registered protocol family 2
[    0.883526] TCP established hash table entries: 8192 (order: 3, 32768 bytes)
[    0.883542] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[    0.883564] TCP: Hash tables configured (established 8192 bind 8192)
[    0.883581] TCP: reno registered
[    0.883583] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.883589] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.883638] NET: Registered protocol family 1
[    0.883654] pci 0000:00:02.0: Video device with shadowed ROM
[    0.913239] PCI: CLS 64 bytes, default 64
[    0.913296] Trying to unpack rootfs image as initramfs...
[    1.291194] Freeing initrd memory: 20900K (f571e000 - f6b87000)
[    1.291307] Simple Boot Flag at 0x44 set to 0x1
[    1.291579] microcode: CPU0 sig=0x20655, pf=0x10, revision=0x4
[    1.291587] microcode: CPU1 sig=0x20655, pf=0x10, revision=0x4
[    1.291595] microcode: CPU2 sig=0x20655, pf=0x10, revision=0x4
[    1.291601] microcode: CPU3 sig=0x20655, pf=0x10, revision=0x4
[    1.291688] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    1.291720] Scanning for low memory corruption every 60 seconds
[    1.292191] futex hash table entries: 2048 (order: 5, 131072 bytes)
[    1.292245] Initialise system trusted keyring
[    1.292272] audit: initializing netlink subsys (disabled)
[    1.292290] audit: type=2000 audit(1432568115.156:1): initialized
[    1.292620] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.294372] zpool: loaded
[    1.294374] zbud: loaded
[    1.294471] VFS: Disk quotas dquot_6.5.2
[    1.294514] VFS: Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.295038] fuse init (API version 7.23)
[    1.295202] Key type big_key registered
[    1.295821] Key type asymmetric registered
[    1.295825] Asymmetric key parser 'x509' registered
[    1.295843] bounce: pool size: 64 pages
[    1.295881] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    1.295936] io scheduler noop registered
[    1.295939] io scheduler deadline registered (default)
[    1.295981] io scheduler cfq registered
[    1.296591] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.296609] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.296643] vesafb: mode is 1024x768x32, linelength=4096, pages=0
[    1.296644] vesafb: scrolling: redraw
[    1.296646] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    1.298252] vesafb: framebuffer at 0x80000000, mapped to 0xf8480000, using 3072k, total 3072k
[    1.298396] Console: switching to colour frame buffer device 128x48
[    1.298420] fb0: VESA VGA frame buffer device
[    1.298454] intel_idle: MWAIT substates: 0x1120
[    1.298456] intel_idle: v0.4 model 0x25
[    1.298457] intel_idle: lapic_timer_reliable_states 0xffffffff
[    1.299656] ACPI: AC Adapter [AC] (on-line)
[    1.299788] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
[    1.301623] ACPI: Lid Switch [LID]
[    1.301714] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1
[    1.301720] ACPI: Power Button [PWRB]
[    1.301777] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    1.301779] ACPI: Power Button [PWRF]
[    1.310596] thermal LNXTHERM:00: registered as thermal_zone0
[    1.310602] ACPI: Thermal Zone [TSZ0] (59 C)
[    1.318848] thermal LNXTHERM:01: registered as thermal_zone1
[    1.318852] ACPI: Thermal Zone [TSZ1] (56 C)
[    1.318902] GHES: HEST is not enabled!
[    1.319070] isapnp: Scanning for PnP cards...
[    1.319098] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.321222] Linux agpgart interface v0.103
[    1.321308] agpgart-intel 0000:00:00.0: Intel HD Graphics Chipset
[    1.321327] agpgart-intel 0000:00:00.0: detected gtt size: 2097152K total, 262144K mappable
[    1.321819] agpgart-intel 0000:00:00.0: detected 32768K stolen memory
[    1.321995] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0x80000000
[    1.323677] brd: module loaded
[    1.324515] loop: module loaded
[    1.324768] libphy: Fixed MDIO Bus: probed
[    1.324771] tun: Universal TUN/TAP device driver, 1.6
[    1.324772] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.324847] PPP generic driver version 2.4.2
[    1.324937] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.324942] ehci-pci: EHCI PCI platform driver
[    1.325127] ehci-pci 0000:00:1a.0: EHCI Host Controller
[    1.325134] ehci-pci 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    1.325150] ehci-pci 0000:00:1a.0: debug port 2
[    1.329111] ehci-pci 0000:00:1a.0: cache line size of 64 is not supported
[    1.329130] ehci-pci 0000:00:1a.0: irq 16, io mem 0x9640a000
[    1.340852] ehci-pci 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    1.340895] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    1.340897] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.340899] usb usb1: Product: EHCI Host Controller
[    1.340901] usb usb1: Manufacturer: Linux 3.19.0-18-generic ehci_hcd
[    1.340902] usb usb1: SerialNumber: 0000:00:1a.0
[    1.341041] hub 1-0:1.0: USB hub found
[    1.341049] hub 1-0:1.0: 3 ports detected
[    1.341291] ehci-pci 0000:00:1d.0: EHCI Host Controller
[    1.341298] ehci-pci 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.341319] ehci-pci 0000:00:1d.0: debug port 2
[    1.345320] ehci-pci 0000:00:1d.0: cache line size of 64 is not supported
[    1.345343] ehci-pci 0000:00:1d.0: irq 23, io mem 0x96409000
[    1.356838] ehci-pci 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    1.356871] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    1.356873] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.356875] usb usb2: Product: EHCI Host Controller
[    1.356877] usb usb2: Manufacturer: Linux 3.19.0-18-generic ehci_hcd
[    1.356878] usb usb2: SerialNumber: 0000:00:1d.0
[    1.357008] hub 2-0:1.0: USB hub found
[    1.357014] hub 2-0:1.0: 3 ports detected
[    1.357144] ehci-platform: EHCI generic platform driver
[    1.357155] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.357160] ohci-pci: OHCI PCI platform driver
[    1.357173] ohci-platform: OHCI generic platform driver
[    1.357181] uhci_hcd: USB Universal Host Controller Interface driver
[    1.357237] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.375184] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.375189] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.375344] mousedev: PS/2 mouse device common for all mice
[    1.375576] rtc_cmos 00:01: RTC can wake from S4
[    1.375722] rtc_cmos 00:01: rtc core: registered rtc_cmos as rtc0
[    1.375755] rtc_cmos 00:01: alarms up to one month, 242 bytes nvram, hpet irqs
[    1.375765] i2c /dev entries driver
[    1.375813] device-mapper: uevent: version 1.0.3
[    1.375897] device-mapper: ioctl: 4.29.0-ioctl (2014-10-28) initialised: dm-devel@redhat.com
[    1.375922] platform eisa.0: Probing EISA bus 0
[    1.375925] platform eisa.0: EISA: Cannot allocate resource for mainboard
[    1.375926] platform eisa.0: Cannot allocate resource for EISA slot 1
[    1.375928] platform eisa.0: Cannot allocate resource for EISA slot 2
[    1.375930] platform eisa.0: Cannot allocate resource for EISA slot 3
[    1.375931] platform eisa.0: Cannot allocate resource for EISA slot 4
[    1.375933] platform eisa.0: Cannot allocate resource for EISA slot 5
[    1.375934] platform eisa.0: Cannot allocate resource for EISA slot 6
[    1.375936] platform eisa.0: Cannot allocate resource for EISA slot 7
[    1.375938] platform eisa.0: Cannot allocate resource for EISA slot 8
[    1.375939] platform eisa.0: EISA: Detected 0 cards
[    1.375957] cpufreq-nforce2: No nForce2 chipset.
[    1.375966] ledtrig-cpu: registered to indicate activity on CPUs
[    1.375976] PCCT header not found.
[    1.375977] ACPI PCC probe failed.
[    1.376083] TCP: cubic registered
[    1.376199] NET: Registered protocol family 10
[    1.376439] NET: Registered protocol family 17
[    1.376455] Key type dns_resolver registered
[    1.376719] Using IPI No-Shortcut mode
[    1.376931] Loading compiled-in X.509 certificates
[    1.380131] Loaded X.509 cert 'Magrathea: Glacier signing key: a7fb1a1a386c62cc9cee94c238b077042aab58be'
[    1.380150] registered taskstats version 1
[    1.380735] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    1.384356] Key type trusted registered
[    1.394150] Key type encrypted registered
[    1.394157] AppArmor: AppArmor sha1 policy hashing enabled
[    1.394160] ima: No TPM chip found, activating TPM-bypass!
[    1.394214] evm: HMAC attrs: 0x1
[    1.394849]   Magic number: 15:492:589
[    1.395010] rtc_cmos 00:01: setting system clock to 2015-05-25 15:35:15 UTC (1432568115)
[    1.395568] ACPI: Battery Slot [BAT0] (battery present)
[    1.395846] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.395848] EDD information not available.
[    1.395932] PM: Hibernation image not present or could not be loaded.
[    1.636801] isapnp: No Plug & Play device found
[    1.637190] Freeing unused kernel memory: 888K (c1a93000 - c1b71000)
[    1.637334] Write protecting the kernel text: 7112k
[    1.637419] Write protecting the kernel read-only data: 3000k
[    1.637421] NX-protecting the kernel data: 5176k
[    1.649151] random: systemd-udevd urandom read with 4 bits of entropy available
[    1.652691] usb 1-1: new high-speed USB device number 2 using ehci-pci
[    1.668671] usb 2-1: new high-speed USB device number 2 using ehci-pci
[    1.678153] rtsx_pci 0000:03:00.0: rtsx_pci_acquire_irq: pcr->msi_en = 1, pci->irq = 24
[    1.683055] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.683067] r8169 0000:01:00.0: can't disable ASPM; OS doesn't have ASPM control
[    1.683725] r8169 0000:01:00.0 eth0: RTL8168e/8111e at 0xf845e000, ac:16:2d:53:e3:fc, XID 0c200000 IRQ 25
[    1.683729] r8169 0000:01:00.0 eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
[    1.689323] ahci 0000:00:1f.2: version 3.0
[    1.689541] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 4 ports 3 Gbps 0x3 impl SATA mode
[    1.689544] ahci 0000:00:1f.2: flags: 64bit ncq sntf ilck pm led clo pio slum part ems apst 
[    1.702839] scsi host0: ahci
[    1.703305] scsi host1: ahci
[    1.703464] scsi host2: ahci
[    1.703650] scsi host3: ahci
[    1.703735] ata1: SATA max UDMA/133 abar m2048@0x96408000 port 0x96408100 irq 26
[    1.703740] ata2: SATA max UDMA/133 abar m2048@0x96408000 port 0x96408180 irq 26
[    1.703742] ata3: DUMMY
[    1.703744] ata4: DUMMY
[    1.785360] usb 1-1: New USB device found, idVendor=8087, idProduct=0020
[    1.785373] usb 1-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.785798] hub 1-1:1.0: USB hub found
[    1.785959] hub 1-1:1.0: 6 ports detected
[    1.800979] usb 2-1: New USB device found, idVendor=8087, idProduct=0020
[    1.800987] usb 2-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.801394] hub 2-1:1.0: USB hub found
[    1.801630] hub 2-1:1.0: 8 ports detected
[    2.020559] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.020598] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.021898] ata1.00: ATA-8: Hitachi HTS543232A7A384, ES2OA60W, max UDMA/100
[    2.021904] ata1.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    2.023412] ata2.00: ATAPI: hp       DVDRAM GT50N, MP00, max UDMA/100
[    2.023441] ata1.00: configured for UDMA/100
[    2.023783] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS54323 A60W PQ: 0 ANSI: 5
[    2.024353] sd 0:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    2.024373] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.024452] sd 0:0:0:0: [sda] Write Protect is off
[    2.024456] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.024501] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.026369] ata2.00: configured for UDMA/100
[    2.028242] scsi 1:0:0:0: CD-ROM            hp       DVDRAM GT50N     MP00 PQ: 0 ANSI: 5
[    2.046896] sr 1:0:0:0: [sr0] scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.046904] cdrom: Uniform CD-ROM driver Revision: 3.20
[    2.047140] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.047235] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.056611] usb 1-1.3: new high-speed USB device number 3 using ehci-pci
[    2.070380]  sda: sda1 sda2 < sda5 >
[    2.071421] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.196508] usb 1-1.3: New USB device found, idVendor=0c45, idProduct=6321
[    2.196513] usb 1-1.3: New USB device strings: Mfr=2, Product=1, SerialNumber=0
[    2.196515] usb 1-1.3: Product: HP Webcam-101
[    2.196517] usb 1-1.3: Manufacturer: DCPKP019I2IEP5
[    2.276694] usb 1-1.4: new full-speed USB device number 4 using ehci-pci
[    2.288338] tsc: Refined TSC clocksource calibration: 2526.983 MHz
[    2.369401] usb 1-1.4: New USB device found, idVendor=0cf3, idProduct=3005
[    2.369406] usb 1-1.4: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    2.575943] psmouse serio1: synaptics: queried max coordinates: x [..5776], y [..5012]
[    2.656863] psmouse serio1: synaptics: Touchpad model: 1, fw: 7.5, id: 0x1e0b1, caps: 0xd00073/0x240000/0xa0400, board id: 1679, fw id: 724542
[    2.708532] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input5
[    2.896854] EXT4-fs (dm-0): mounted filesystem with ordered data mode. Opts: (null)
[    3.288195] Switched to clocksource tsc
[    3.587026] random: nonblocking pool is initialized
[    4.272301] systemd[1]: Inserted module 'autofs4'
[    4.413689] systemd[1]: systemd 219 running in system mode. (+PAM +AUDIT +SELINUX +IMA +APPARMOR +SMACK +SYSVINIT +UTMP +LIBCRYPTSETUP +GCRYPT -GNUTLS +ACL +XZ -LZ4 -SECCOMP +BLKID -ELFUTILS +KMOD -IDN)
[    4.413850] systemd[1]: Detected architecture x86.
[    4.462006] systemd[1]: Set hostname to <MJ-Lappy>.
[    6.871663] systemd[1]: Created slice Root Slice.
[    6.871678] systemd[1]: Starting Root Slice.
[    6.871720] systemd[1]: Listening on Journal Socket (/dev/log).
[    6.871730] systemd[1]: Starting Journal Socket (/dev/log).
[    6.871759] systemd[1]: Listening on Journal Audit Socket.
[    6.871767] systemd[1]: Starting Journal Audit Socket.
[    6.871859] systemd[1]: Created slice User and Session Slice.
[    6.871869] systemd[1]: Starting User and Session Slice.
[    6.871902] systemd[1]: Listening on udev Control Socket.
[    6.871911] systemd[1]: Starting udev Control Socket.
[    6.871921] systemd[1]: Reached target Remote File Systems (Pre).
[    6.871929] systemd[1]: Starting Remote File Systems (Pre).
[    6.871959] systemd[1]: Listening on /dev/initctl Compatibility Named Pipe.
[    6.871967] systemd[1]: Starting /dev/initctl Compatibility Named Pipe.
[    6.871992] systemd[1]: Listening on udev Kernel Socket.
[    6.872000] systemd[1]: Starting udev Kernel Socket.
[    6.872010] systemd[1]: Reached target Encrypted Volumes.
[    6.872018] systemd[1]: Starting Encrypted Volumes.
[    6.872099] systemd[1]: Created slice System Slice.
[    6.872116] systemd[1]: Starting System Slice.
[    6.872210] systemd[1]: Created slice system-getty.slice.
[    6.872219] systemd[1]: Starting system-getty.slice.
[    6.872739] systemd[1]: Starting Increase datagram queue length...
[    6.872765] systemd[1]: Reached target Slices.
[    6.872776] systemd[1]: Starting Slices.
[    6.872886] systemd[1]: Created slice system-systemd\x2dfsck.slice.
[    6.872896] systemd[1]: Starting system-systemd\x2dfsck.slice.
[    6.918258] systemd[1]: Listening on Device-mapper event daemon FIFOs.
[    6.918272] systemd[1]: Starting Device-mapper event daemon FIFOs.
[    6.918306] systemd[1]: Listening on Delayed Shutdown Socket.
[    6.918315] systemd[1]: Starting Delayed Shutdown Socket.
[    6.918357] systemd[1]: Listening on Journal Socket.
[    6.918374] systemd[1]: Starting Journal Socket.
[    6.918925] systemd[1]: Starting Create list of required static device nodes for the current kernel...
[    7.011043] systemd[1]: Starting Load Kernel Modules...
[    7.011555] systemd[1]: Starting Setup Virtual Console...
[    7.012093] systemd[1]: Starting Uncomplicated firewall...
[    7.012632] systemd[1]: Started Braille Device Support.
[    7.012797] systemd[1]: Starting Braille Device Support...
[    7.013366] systemd[1]: Mounting Debug File System...
[    7.013945] systemd[1]: Starting udev Coldplug all Devices...
[    7.014714] systemd[1]: Mounting Huge Pages File System...
[    7.015306] systemd[1]: Started Read required files in advance.
[    7.015380] systemd[1]: Starting Read required files in advance...
[    7.016089] systemd[1]: Mounting POSIX Message Queue File System...
[    7.016312] systemd[1]: Set up automount Arbitrary Executable File Formats File System Automount Point.
[    7.016332] systemd[1]: Starting Arbitrary Executable File Formats File System Automount Point.
[    7.543334] systemd[1]: Started Set Up Additional Binary Formats.
[    7.543421] systemd[1]: Listening on LVM2 metadata daemon socket.
[    7.543434] systemd[1]: Starting LVM2 metadata daemon socket.
[    7.544032] systemd[1]: Starting Monitoring of LVM2 mirrors, snapshots etc. using dmeventd or progress polling...
[    7.544109] systemd[1]: Started Forward Password Requests to Wall Directory Watch.
[    7.544126] systemd[1]: Starting Forward Password Requests to Wall Directory Watch.
[    7.544627] systemd[1]: Starting Nameserver information manager...
[    7.544669] systemd[1]: Listening on fsck to fsckd communication Socket.
[    7.544688] systemd[1]: Starting fsck to fsckd communication Socket.
[    7.545552] systemd[1]: Mounted POSIX Message Queue File System.
[    7.545582] systemd[1]: Mounted Debug File System.
[    7.545605] systemd[1]: Mounted Huge Pages File System.
[    7.545824] systemd[1]: Started Increase datagram queue length.
[    7.546071] systemd[1]: Started Create list of required static device nodes for the current kernel.
[    7.546290] systemd[1]: Started Setup Virtual Console.
[    7.546506] systemd[1]: Started Uncomplicated firewall.
[    7.567728] systemd[1]: Starting Create Static Device Nodes in /dev...
[    7.567797] systemd[1]: Listening on Syslog Socket.
[    7.567830] systemd[1]: Starting Syslog Socket.
[    7.568608] systemd[1]: Starting Journal Service...
[    7.573353] systemd[1]: Started udev Coldplug all Devices.
[    7.574241] systemd[1]: Starting udev Wait for Complete Device Initialization...
[    7.791615] systemd[1]: Started Nameserver information manager.
[    8.341549] lp: driver loaded but no devices found
[    8.494833] ppdev: user-space parallel port driver
[    8.708522] systemd[1]: Started Journal Service.
[   11.183062] ACPI Warning: SystemIO range 0x00000428-0x0000042f conflicts with OpRegion 0x00000400-0x0000047f (\PMIO) (20141107/utaddress-258)
[   11.183070] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   11.183073] ACPI Warning: SystemIO range 0x00000540-0x0000054f conflicts with OpRegion 0x00000500-0x00000563 (\GPIO) (20141107/utaddress-258)
[   11.183077] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   11.183078] ACPI Warning: SystemIO range 0x00000530-0x0000053f conflicts with OpRegion 0x00000500-0x00000563 (\GPIO) (20141107/utaddress-258)
[   11.183081] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   11.183082] ACPI Warning: SystemIO range 0x00000500-0x0000052f conflicts with OpRegion 0x00000500-0x00000563 (\GPIO) (20141107/utaddress-258)
[   11.183085] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   11.183086] lpc_ich: Resource conflict(s) found affecting gpio_ich
[   11.234743] wmi: Mapper loaded
[   11.260270] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   11.998356] input: HP WMI hotkeys as /devices/virtual/input/input6
[   12.006372] ACPI Error: Field [B128] at 1152 exceeds Buffer [NULL] size 160 (bits) (20141107/dsopcode-236)
[   12.006379] ACPI Error: Method parse/execution failed [\_SB_.WMID.HWCD] (Node f4c9df18), AE_AML_BUFFER_LIMIT (20141107/psparse-536)
[   12.006388] ACPI Error: Method parse/execution failed [\_SB_.WMID.WMAD] (Node f4c9e2d0), AE_AML_BUFFER_LIMIT (20141107/psparse-536)
[   12.006571] ACPI Error: Field [B128] at 1152 exceeds Buffer [NULL] size 160 (bits) (20141107/dsopcode-236)
[   12.006576] ACPI Error: Method parse/execution failed [\_SB_.WMID.HWCD] (Node f4c9df18), AE_AML_BUFFER_LIMIT (20141107/psparse-536)
[   12.006583] ACPI Error: Method parse/execution failed [\_SB_.WMID.WMAD] (Node f4c9e2d0), AE_AML_BUFFER_LIMIT (20141107/psparse-536)
[   12.131592] [drm] Initialized drm 1.1.0 20060810
[   12.164532] Bluetooth: Core ver 2.20
[   12.164564] NET: Registered protocol family 31
[   12.164566] Bluetooth: HCI device and connection manager initialized
[   12.164573] Bluetooth: HCI socket layer initialized
[   12.164576] Bluetooth: L2CAP socket layer initialized
[   12.164584] Bluetooth: SCO socket layer initialized
[   12.210421] cfg80211: Calling CRDA to update world regulatory domain
[   12.217625] media: Linux media interface: v0.10
[   12.227174] usbcore: registered new interface driver btusb
[   12.366192] Linux video capture interface: v2.00
[   12.386738] kvm: VM_EXIT_LOAD_IA32_PERF_GLOBAL_CTRL does not work properly. Using workaround
[   12.494006] [drm] Memory usable by graphics device = 2048M
[   12.494011] checking generic (80000000 300000) vs hw (80000000 10000000)
[   12.494013] fb: switching to inteldrmfb from VESA VGA
[   12.494057] Console: switching to colour dummy device 80x25
[   12.494123] [drm] Replacing VGA console driver
[   12.518631] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[   12.518635] [drm] Driver supports precise vblank timestamp query.
[   12.518720] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   12.537489] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   12.539415] acpi device:01: registered as cooling_device4
[   12.539531] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input7
[   12.539684] [drm] Initialized i915 1.6.0 20141121 for 0000:00:02.0 on minor 0
[   12.552519] fbcon: inteldrmfb (fb0) is primary device
[   12.552615] Console: switching to colour frame buffer device 170x48
[   12.552647] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[   12.552649] i915 0000:00:02.0: registered panic notifier
[   12.854636] uvcvideo: Found UVC 1.00 device HP Webcam-101 (0c45:6321)
[   12.869526] input: HP Webcam-101 as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3:1.0/input/input8
[   12.869626] usbcore: registered new interface driver uvcvideo
[   12.869629] USB Video Class driver (1.1.1)
[   13.283641] sound hdaudioC0D0: autoconfig: line_outs=1 (0x14/0x0/0x0/0x0/0x0) type:speaker
[   13.283665] sound hdaudioC0D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   13.283679] sound hdaudioC0D0:    hp_outs=1 (0x21/0x0/0x0/0x0/0x0)
[   13.283690] sound hdaudioC0D0:    mono: mono_out=0x0
[   13.283692] sound hdaudioC0D0:    inputs:
[   13.283704] sound hdaudioC0D0:      Mic=0x18
[   13.283717] sound hdaudioC0D0:      Internal Mic=0x12
[   13.285792] ath: phy0: ASPM enabled: 0x43
[   13.285795] ath: EEPROM regdomain: 0x60
[   13.285796] ath: EEPROM indicates we should expect a direct regpair map
[   13.285799] ath: Country alpha2 being used: 00
[   13.285800] ath: Regpair used: 0x60
[   13.350343] input: HDA Intel MID Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   13.350448] input: HDA Intel MID Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   13.352175] input: HDA Intel MID HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   13.363469] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   13.363885] ieee80211 phy0: Atheros AR9285 Rev:2 mem=0xf84e0000, irq=18
[   13.857396] cfg80211: World regulatory domain updated:
[   13.857401] cfg80211:  DFS Master region: unset
[   13.857403] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
[   13.857405] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[   13.857407] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[   13.857409] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm), (N/A)
[   13.857411] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[   13.857412] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[   14.226867] Adding 1953788k swap on /dev/mapper/ubuntu--vg-swap_1.  Priority:-1 extents:1 across:1953788k FS
[   17.149862] EXT4-fs (dm-0): re-mounted. Opts: errors=remount-ro
[   17.390441] ACPI Error: Field [B128] at 1152 exceeds Buffer [NULL] size 160 (bits) (20141107/dsopcode-236)
[   17.390448] ACPI Error: Method parse/execution failed [\_SB_.WMID.HWCD] (Node f4c9df18), AE_AML_BUFFER_LIMIT (20141107/psparse-536)
[   17.390459] ACPI Error: Method parse/execution failed [\_SB_.WMID.WMAD] (Node f4c9e2d0), AE_AML_BUFFER_LIMIT (20141107/psparse-536)
[   17.403182] ACPI Error: Field [B128] at 1152 exceeds Buffer [NULL] size 160 (bits) (20141107/dsopcode-236)
[   17.403189] ACPI Error: Method parse/execution failed [\_SB_.WMID.HWCD] (Node f4c9df18), AE_AML_BUFFER_LIMIT (20141107/psparse-536)
[   17.403197] ACPI Error: Method parse/execution failed [\_SB_.WMID.WMAD] (Node f4c9e2d0), AE_AML_BUFFER_LIMIT (20141107/psparse-536)
[   17.489302] systemd-journald[241]: Received request to flush runtime journal from PID 1
[   17.974486] EXT4-fs (sda1): mounting ext2 file system using the ext4 subsystem
[   18.027670] EXT4-fs (sda1): mounted filesystem without journal. Opts: (null)
[   20.609708] audit: type=1400 audit(1432568134.722:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/lightdm/lightdm-guest-session" pid=499 comm="apparmor_parser"
[   20.609717] audit: type=1400 audit(1432568134.722:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="chromium" pid=499 comm="apparmor_parser"
[   20.682792] audit: type=1400 audit(1432568134.794:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=499 comm="apparmor_parser"
[   20.682801] audit: type=1400 audit(1432568134.794:5): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=499 comm="apparmor_parser"
[   20.682807] audit: type=1400 audit(1432568134.794:6): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-helper" pid=499 comm="apparmor_parser"
[   20.682813] audit: type=1400 audit(1432568134.794:7): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=499 comm="apparmor_parser"
[   20.887960] audit: type=1400 audit(1432568134.998:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/evince" pid=499 comm="apparmor_parser"
[   20.887970] audit: type=1400 audit(1432568134.998:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="sanitized_helper" pid=499 comm="apparmor_parser"
[   20.887976] audit: type=1400 audit(1432568134.998:10): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/evince-previewer" pid=499 comm="apparmor_parser"
[   20.887981] audit: type=1400 audit(1432568134.998:11): apparmor="STATUS" operation="profile_load" profile="unconfined" name="sanitized_helper" pid=499 comm="apparmor_parser"
[   29.335393] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   29.335396] Bluetooth: BNEP filters: protocol multicast
[   29.335401] Bluetooth: BNEP socket layer initialized
[   29.672460] Bluetooth: RFCOMM TTY layer initialized
[   29.672471] Bluetooth: RFCOMM socket layer initialized
[   29.672480] Bluetooth: RFCOMM ver 1.11
[   33.183240] r8169 0000:01:00.0 eth0: link down
[   34.883963] wlan0: authenticate with 00:8e:f2:5c:f3:d2
[   34.897929] wlan0: send auth to 00:8e:f2:5c:f3:d2 (try 1/3)
[   34.902097] wlan0: authenticated
[   34.906143] wlan0: associate with 00:8e:f2:5c:f3:d2 (try 1/3)
[   34.910326] wlan0: RX AssocResp from 00:8e:f2:5c:f3:d2 (capab=0x411 status=0 aid=4)
[   34.910479] wlan0: associated
[   42.129634] ACPI Error: Field [B128] at 1152 exceeds Buffer [NULL] size 160 (bits) (20141107/dsopcode-236)
[   42.129642] ACPI Error: Method parse/execution failed [\_SB_.WMID.HWCD] (Node f4c9df18), AE_AML_BUFFER_LIMIT (20141107/psparse-536)
[   42.129652] ACPI Error: Method parse/execution failed [\_SB_.WMID.WMAD] (Node f4c9e2d0), AE_AML_BUFFER_LIMIT (20141107/psparse-536)
[   51.834409] ip_tables: (C) 2000-2006 Netfilter Core Team
[   52.002419] ip6_tables: (C) 2000-2006 Netfilter Core Team
[   52.888360] Ebtables v2.0 registered
[   54.231345] bridge: automatic filtering via arp/ip/ip6tables has been deprecated. Update your scripts to load br_netfilter if you need this.
[   54.311873] device virbr0-nic entered promiscuous mode
[   55.461332] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[   55.867066] virbr0: port 1(virbr0-nic) entered listening state
[   55.867086] virbr0: port 1(virbr0-nic) entered listening state
[   56.180330] virbr0: port 1(virbr0-nic) entered disabled state
[  161.600557] usb 2-1.1: new high-speed USB device number 3 using ehci-pci
[  161.693992] usb 2-1.1: New USB device found, idVendor=12d1, idProduct=1446
[  161.694002] usb 2-1.1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  161.694007] usb 2-1.1: Product: HUAWEI Mobile
[  161.694012] usb 2-1.1: Manufacturer: HUAWEI
[  161.694017] usb 2-1.1: SerialNumber: FFFFFFFFFFFFFFFF
[  161.919978] usb-storage 2-1.1:1.0: USB Mass Storage device detected
[  161.920096] scsi host4: usb-storage 2-1.1:1.0
[  161.920374] usbcore: registered new interface driver usb-storage
[  161.957098] usbcore: registered new interface driver uas
[  162.660092] usb 2-1.1: USB disconnect, device number 3
[  163.478184] usb 2-1.1: new high-speed USB device number 4 using ehci-pci
[  163.571477] usb 2-1.1: New USB device found, idVendor=12d1, idProduct=1506
[  163.571484] usb 2-1.1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[  163.571487] usb 2-1.1: Product: HUAWEI Mobile
[  163.571490] usb 2-1.1: Manufacturer: HUAWEI
[  163.927363] usb-storage 2-1.1:1.4: USB Mass Storage device detected
[  163.927650] scsi host5: usb-storage 2-1.1:1.4
[  163.928082] usb-storage 2-1.1:1.5: USB Mass Storage device detected
[  163.928403] scsi host6: usb-storage 2-1.1:1.5
[  163.991710] usbcore: registered new interface driver usbserial
[  163.991781] usbcore: registered new interface driver usbserial_generic
[  163.991829] usbserial: USB Serial support registered for generic
[  163.997882] usbcore: registered new interface driver cdc_ncm
[  164.011864] usbcore: registered new interface driver cdc_wdm
[  164.063175] huawei_cdc_ncm 2-1.1:1.1: MAC-Address: 00:1e:10:1f:00:00
[  164.075974] usbcore: registered new interface driver option
[  164.076020] usbserial: USB Serial support registered for GSM modem (1-port)
[  164.085127] huawei_cdc_ncm 2-1.1:1.1: cdc-wdm0: USB WDM device
[  164.085861] huawei_cdc_ncm 2-1.1:1.1 wwan0: register 'huawei_cdc_ncm' at usb-0000:00:1d.0-1.1, Huawei CDC NCM device, 00:1e:10:1f:00:00
[  164.085934] option 2-1.1:1.0: GSM modem (1-port) converter detected
[  164.086006] usbcore: registered new interface driver huawei_cdc_ncm
[  164.087341] usb 2-1.1: GSM modem (1-port) converter now attached to ttyUSB0
[  164.087421] option 2-1.1:1.2: GSM modem (1-port) converter detected
[  164.087763] usb 2-1.1: GSM modem (1-port) converter now attached to ttyUSB1
[  164.087808] option 2-1.1:1.3: GSM modem (1-port) converter detected
[  164.088149] usb 2-1.1: GSM modem (1-port) converter now attached to ttyUSB2
[  164.937463] scsi 5:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2
[  164.938035] scsi 6:0:0:0: Direct-Access     HUAWEI   TF CARD Storage  2.31 PQ: 0 ANSI: 2
[  164.938766] sr 5:0:0:0: [sr1] scsi-1 drive
[  164.938962] sr 5:0:0:0: Attached scsi CD-ROM sr1
[  164.939103] sr 5:0:0:0: Attached scsi generic sg2 type 5
[  164.941109] sd 6:0:0:0: Attached scsi generic sg3 type 0
[  164.945890] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[  164.996479] sr 5:0:0:0: [sr1] FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  164.996487] sr 5:0:0:0: [sr1] Sense Key : Medium Error [current]
[  164.996490] sr 5:0:0:0: [sr1] Add. Sense: Unrecovered read error
[  164.996491] sr 5:0:0:0: [sr1] CDB: 
[  164.996493] Read(10): 28 00 00 00 ff fe 00 00 02 00
[  164.996501] blk_update_request: critical medium error, dev sr1, sector 262136
[  165.002724] sr 5:0:0:0: [sr1] FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  165.002729] sr 5:0:0:0: [sr1] Sense Key : Medium Error [current]
[  165.002731] sr 5:0:0:0: [sr1] Add. Sense: Unrecovered read error
[  165.002733] sr 5:0:0:0: [sr1] CDB: 
[  165.002735] Read(10): 28 00 00 00 ff fe 00 00 02 00
[  165.002743] blk_update_request: critical medium error, dev sr1, sector 262136
[  165.002746] Buffer I/O error on dev sr1, logical block 32767, async page read
[  166.104769] sr 5:0:0:0: [sr1] FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  166.104778] sr 5:0:0:0: [sr1] Sense Key : Medium Error [current]
[  166.104782] sr 5:0:0:0: [sr1] Add. Sense: Unrecovered read error
[  166.104784] sr 5:0:0:0: [sr1] CDB: 
[  166.104787] Read(10): 28 00 00 00 ff fc 00 00 02 00
[  166.104798] blk_update_request: critical medium error, dev sr1, sector 262128
[  166.111148] sr 5:0:0:0: [sr1] FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  166.111157] sr 5:0:0:0: [sr1] Sense Key : Medium Error [current]
[  166.111160] sr 5:0:0:0: [sr1] Add. Sense: Unrecovered read error
[  166.111162] sr 5:0:0:0: [sr1] CDB: 
[  166.111165] Read(10): 28 00 00 00 ff fc 00 00 02 00
[  166.111176] blk_update_request: critical medium error, dev sr1, sector 262128
[  166.111181] Buffer I/O error on dev sr1, logical block 32766, async page read
[  166.285880] ISO 9660 Extensions: Microsoft Joliet Level 1
[  166.339984] ISOFS: changing to secondary root
[  177.861948] PPP BSD Compression module registered
[  177.885622] PPP Deflate Compression module registered
[  560.713978] usb 2-1.1: USB disconnect, device number 4
[  560.714272] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
[  560.714285] option 2-1.1:1.0: device disconnected
[  560.714363] huawei_cdc_ncm 2-1.1:1.1 wwan0: unregister 'huawei_cdc_ncm' usb-0000:00:1d.0-1.1, Huawei CDC NCM device
[  560.716716] option1 ttyUSB2: usb_wwan_indat_callback: resubmit read urb failed. (-19)
[  560.720981] option1 ttyUSB2: usb_wwan_indat_callback: resubmit read urb failed. (-19)
[  560.725234] option1 ttyUSB2: usb_wwan_indat_callback: resubmit read urb failed. (-19)
[  560.729472] option1 ttyUSB2: usb_wwan_indat_callback: resubmit read urb failed. (-19)
[  560.730113] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
[  560.730144] option 2-1.1:1.2: device disconnected
[  560.730327] option1 ttyUSB2: GSM modem (1-port) converter now disconnected from ttyUSB2
[  560.730342] option 2-1.1:1.3: device disconnected
[  566.497920] perf interrupt took too long (2507 > 2500), lowering kernel.perf_event_max_sample_rate to 50000
[  573.440568] usb 2-1.1: new high-speed USB device number 5 using ehci-pci
[  573.533700] usb 2-1.1: New USB device found, idVendor=12d1, idProduct=1446
[  573.533708] usb 2-1.1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  573.533712] usb 2-1.1: Product: HUAWEI Mobile
[  573.533717] usb 2-1.1: Manufacturer: HUAWEI
[  573.533721] usb 2-1.1: SerialNumber: FFFFFFFFFFFFFFFF
[  573.617571] usb-storage 2-1.1:1.0: USB Mass Storage device detected
[  573.617762] scsi host7: usb-storage 2-1.1:1.0
[  574.629009] scsi 7:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2
[  574.629750] scsi 7:0:0:1: Direct-Access     HUAWEI   TF CARD Storage  2.31 PQ: 0 ANSI: 2
[  574.631202] sr 7:0:0:0: [sr1] scsi-1 drive
[  574.631411] sr 7:0:0:0: Attached scsi CD-ROM sr1
[  574.632327] sr 7:0:0:0: Attached scsi generic sg2 type 5
[  574.634600] sd 7:0:0:1: Attached scsi generic sg3 type 0
[  574.639830] sd 7:0:0:1: [sdb] Attached SCSI removable disk
[  574.764189] sr 7:0:0:0: [sr1] FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  574.764202] sr 7:0:0:0: [sr1] Sense Key : Medium Error [current]
[  574.764208] sr 7:0:0:0: [sr1] Add. Sense: Unrecovered read error
[  574.764212] sr 7:0:0:0: [sr1] CDB: 
[  574.764216] Read(10): 28 00 00 00 ff fe 00 00 02 00
[  574.764235] blk_update_request: critical medium error, dev sr1, sector 262136
[  574.770408] sr 7:0:0:0: [sr1] FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  574.770418] sr 7:0:0:0: [sr1] Sense Key : Medium Error [current]
[  574.770424] sr 7:0:0:0: [sr1] Add. Sense: Unrecovered read error
[  574.770428] sr 7:0:0:0: [sr1] CDB: 
[  574.770431] Read(10): 28 00 00 00 ff fe 00 00 02 00
[  574.770448] blk_update_request: critical medium error, dev sr1, sector 262136
[  574.770455] Buffer I/O error on dev sr1, logical block 32767, async page read
[  576.374494] usb 2-1.1: USB disconnect, device number 5
[  577.018168] usb 2-1.1: new high-speed USB device number 6 using ehci-pci
[  577.111613] usb 2-1.1: New USB device found, idVendor=12d1, idProduct=1506
[  577.111623] usb 2-1.1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[  577.111628] usb 2-1.1: Product: HUAWEI Mobile
[  577.111633] usb 2-1.1: Manufacturer: HUAWEI
[  577.467296] option 2-1.1:1.0: GSM modem (1-port) converter detected
[  577.467469] usb 2-1.1: GSM modem (1-port) converter now attached to ttyUSB1
[  577.482356] huawei_cdc_ncm 2-1.1:1.1: MAC-Address: 00:1e:10:1f:00:00
[  577.504352] huawei_cdc_ncm 2-1.1:1.1: cdc-wdm0: USB WDM device
[  577.504647] huawei_cdc_ncm 2-1.1:1.1 wwan0: register 'huawei_cdc_ncm' at usb-0000:00:1d.0-1.1, Huawei CDC NCM device, 00:1e:10:1f:00:00
[  577.504740] option 2-1.1:1.2: GSM modem (1-port) converter detected
[  577.505115] usb 2-1.1: GSM modem (1-port) converter now attached to ttyUSB3
[  577.505224] option 2-1.1:1.3: GSM modem (1-port) converter detected
[  577.505319] usb 2-1.1: GSM modem (1-port) converter now attached to ttyUSB4
[  577.505747] usb-storage 2-1.1:1.4: USB Mass Storage device detected
[  577.505975] scsi host8: usb-storage 2-1.1:1.4
[  577.506165] usb-storage 2-1.1:1.5: USB Mass Storage device detected
[  577.506230] scsi host9: usb-storage 2-1.1:1.5
[  578.520032] scsi 8:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2
[  578.520298] scsi 9:0:0:0: Direct-Access     HUAWEI   TF CARD Storage  2.31 PQ: 0 ANSI: 2
[  578.524681] sr 8:0:0:0: [sr1] scsi-1 drive
[  578.524937] sr 8:0:0:0: Attached scsi CD-ROM sr1
[  578.525312] sr 8:0:0:0: Attached scsi generic sg2 type 5
[  578.527579] sd 9:0:0:0: Attached scsi generic sg3 type 0
[  578.534165] sd 9:0:0:0: [sdb] Attached SCSI removable disk
[  578.556973] sr 8:0:0:0: [sr1] FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  578.556985] sr 8:0:0:0: [sr1] Sense Key : Medium Error [current]
[  578.556992] sr 8:0:0:0: [sr1] Add. Sense: Unrecovered read error
[  578.556996] sr 8:0:0:0: [sr1] CDB: 
[  578.557000] Read(10): 28 00 00 00 ff fe 00 00 02 00
[  578.557019] blk_update_request: critical medium error, dev sr1, sector 262136
[  578.563278] sr 8:0:0:0: [sr1] FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  578.563282] sr 8:0:0:0: [sr1] Sense Key : Medium Error [current]
[  578.563284] sr 8:0:0:0: [sr1] Add. Sense: Unrecovered read error
[  578.563285] sr 8:0:0:0: [sr1] CDB: 
[  578.563287] Read(10): 28 00 00 00 ff fe 00 00 02 00
[  578.563293] blk_update_request: critical medium error, dev sr1, sector 262136
[  578.563296] Buffer I/O error on dev sr1, logical block 32767, async page read
[  578.923718] sr 8:0:0:0: [sr1] FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  578.923730] sr 8:0:0:0: [sr1] Sense Key : Medium Error [current]
[  578.923736] sr 8:0:0:0: [sr1] Add. Sense: Unrecovered read error
[  578.923740] sr 8:0:0:0: [sr1] CDB: 
[  578.923744] Read(10): 28 00 00 00 ff fc 00 00 02 00
[  578.923760] blk_update_request: critical medium error, dev sr1, sector 262128
[  578.930100] sr 8:0:0:0: [sr1] FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  578.930110] sr 8:0:0:0: [sr1] Sense Key : Medium Error [current]
[  578.930115] sr 8:0:0:0: [sr1] Add. Sense: Unrecovered read error
[  578.930119] sr 8:0:0:0: [sr1] CDB: 
[  578.930122] Read(10): 28 00 00 00 ff fc 00 00 02 00
[  578.930139] blk_update_request: critical medium error, dev sr1, sector 262128
[  578.930146] Buffer I/O error on dev sr1, logical block 32766, async page read
[  579.034487] ISO 9660 Extensions: Microsoft Joliet Level 1
[  579.034860] ISOFS: changing to secondary root
[ 1226.483477] show_signal_msg: 42 callbacks suppressed
[ 1226.483484] gimagereader[9881]: segfault at ad5944d0 ip b5ec3c09 sp b0efe670 error 4 in libgcc_s.so.1[b5eb0000+1c000]
[ 2228.209589] usb 2-1.1: USB disconnect, device number 6
[ 2228.212175] option1 ttyUSB1: usb_wwan_indat_callback: resubmit read urb failed. (-19)
[ 2228.212214] option1 ttyUSB1: usb_wwan_indat_callback: resubmit read urb failed. (-19)
[ 2228.212226] option1 ttyUSB1: usb_wwan_indat_callback: resubmit read urb failed. (-19)
[ 2228.212243] option1 ttyUSB1: usb_wwan_indat_callback: resubmit read urb failed. (-19)
[ 2228.212582] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
[ 2228.212625] option 2-1.1:1.0: device disconnected
[ 2228.212828] huawei_cdc_ncm 2-1.1:1.1 wwan0: unregister 'huawei_cdc_ncm' usb-0000:00:1d.0-1.1, Huawei CDC NCM device
[ 2228.213284] option1 ttyUSB4: usb_wwan_indat_callback: resubmit read urb failed. (-19)
[ 2228.217546] option1 ttyUSB4: usb_wwan_indat_callback: resubmit read urb failed. (-19)
[ 2228.221822] option1 ttyUSB4: usb_wwan_indat_callback: resubmit read urb failed. (-19)
[ 2228.226042] option1 ttyUSB4: usb_wwan_indat_callback: resubmit read urb failed. (-19)
[ 2228.230869] option1 ttyUSB3: GSM modem (1-port) converter now disconnected from ttyUSB3
[ 2228.230895] option 2-1.1:1.2: device disconnected
[ 2228.231405] option1 ttyUSB4: GSM modem (1-port) converter now disconnected from ttyUSB4
[ 2228.231424] option 2-1.1:1.3: device disconnected
[ 4044.688384] perf interrupt took too long (5003 > 5000), lowering kernel.perf_event_max_sample_rate to 25000
[ 4271.060175] usb 2-1.1: new high-speed USB device number 7 using ehci-pci
[ 4271.154030] usb 2-1.1: New USB device found, idVendor=12d1, idProduct=1446
[ 4271.154038] usb 2-1.1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 4271.154044] usb 2-1.1: Product: HUAWEI Mobile
[ 4271.154049] usb 2-1.1: Manufacturer: HUAWEI
[ 4271.154053] usb 2-1.1: SerialNumber: FFFFFFFFFFFFFFFF
[ 4271.241196] usb-storage 2-1.1:1.0: USB Mass Storage device detected
[ 4271.241472] scsi host10: usb-storage 2-1.1:1.0
[ 4272.105339] usb 2-1.1: USB disconnect, device number 7
[ 4272.827246] usb 2-1.1: new high-speed USB device number 8 using ehci-pci
[ 4272.920660] usb 2-1.1: New USB device found, idVendor=12d1, idProduct=1506
[ 4272.920668] usb 2-1.1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[ 4272.920674] usb 2-1.1: Product: HUAWEI Mobile
[ 4272.920679] usb 2-1.1: Manufacturer: HUAWEI
[ 4273.275216] option 2-1.1:1.0: GSM modem (1-port) converter detected
[ 4273.275463] usb 2-1.1: GSM modem (1-port) converter now attached to ttyUSB3
[ 4273.290333] huawei_cdc_ncm 2-1.1:1.1: MAC-Address: 00:1e:10:1f:00:00
[ 4273.312300] huawei_cdc_ncm 2-1.1:1.1: cdc-wdm0: USB WDM device
[ 4273.312939] huawei_cdc_ncm 2-1.1:1.1 wwan0: register 'huawei_cdc_ncm' at usb-0000:00:1d.0-1.1, Huawei CDC NCM device, 00:1e:10:1f:00:00
[ 4273.313160] option 2-1.1:1.2: GSM modem (1-port) converter detected
[ 4273.313429] usb 2-1.1: GSM modem (1-port) converter now attached to ttyUSB5
[ 4273.313694] option 2-1.1:1.3: GSM modem (1-port) converter detected
[ 4273.313908] usb 2-1.1: GSM modem (1-port) converter now attached to ttyUSB6
[ 4273.314428] usb-storage 2-1.1:1.4: USB Mass Storage device detected
[ 4273.315280] scsi host11: usb-storage 2-1.1:1.4
[ 4273.315746] usb-storage 2-1.1:1.5: USB Mass Storage device detected
[ 4273.315906] scsi host12: usb-storage 2-1.1:1.5
[ 4274.327679] scsi 11:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2
[ 4274.328203] scsi 12:0:0:0: Direct-Access     HUAWEI   TF CARD Storage  2.31 PQ: 0 ANSI: 2
[ 4274.329095] sr 11:0:0:0: [sr1] scsi-1 drive
[ 4274.329526] sr 11:0:0:0: Attached scsi CD-ROM sr1
[ 4274.329816] sr 11:0:0:0: Attached scsi generic sg2 type 5
[ 4274.330905] sd 12:0:0:0: Attached scsi generic sg3 type 0
[ 4274.332063] sd 12:0:0:0: [sdb] Attached SCSI removable disk
[ 4274.413271] sr 11:0:0:0: [sr1] FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 4274.413277] sr 11:0:0:0: [sr1] Sense Key : Medium Error [current]
[ 4274.413280] sr 11:0:0:0: [sr1] Add. Sense: Unrecovered read error
[ 4274.413282] sr 11:0:0:0: [sr1] CDB: 
[ 4274.413284] Read(10): 28 00 00 00 ff fe 00 00 02 00
[ 4274.413291] blk_update_request: critical medium error, dev sr1, sector 262136
[ 4274.419662] sr 11:0:0:0: [sr1] FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 4274.419672] sr 11:0:0:0: [sr1] Sense Key : Medium Error [current]
[ 4274.419677] sr 11:0:0:0: [sr1] Add. Sense: Unrecovered read error
[ 4274.419682] sr 11:0:0:0: [sr1] CDB: 
[ 4274.419685] Read(10): 28 00 00 00 ff fe 00 00 02 00
[ 4274.419702] blk_update_request: critical medium error, dev sr1, sector 262136
[ 4274.419712] Buffer I/O error on dev sr1, logical block 32767, async page read
[ 4275.090981] sr 11:0:0:0: [sr1] FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 4275.090987] sr 11:0:0:0: [sr1] Sense Key : Medium Error [current]
[ 4275.090990] sr 11:0:0:0: [sr1] Add. Sense: Unrecovered read error
[ 4275.090991] sr 11:0:0:0: [sr1] CDB: 
[ 4275.090993] Read(10): 28 00 00 00 ff fc 00 00 02 00
[ 4275.091002] blk_update_request: critical medium error, dev sr1, sector 262128
[ 4275.097260] sr 11:0:0:0: [sr1] FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 4275.097264] sr 11:0:0:0: [sr1] Sense Key : Medium Error [current]
[ 4275.097266] sr 11:0:0:0: [sr1] Add. Sense: Unrecovered read error
[ 4275.097268] sr 11:0:0:0: [sr1] CDB: 
[ 4275.097269] Read(10): 28 00 00 00 ff fc 00 00 02 00
[ 4275.097276] blk_update_request: critical medium error, dev sr1, sector 262128
[ 4275.097280] Buffer I/O error on dev sr1, logical block 32766, async page read
[ 4275.230534] ISO 9660 Extensions: Microsoft Joliet Level 1
[ 4275.230909] ISOFS: changing to secondary root
```

---

### Post by Mohit_Jiindal on 2015-05-26
Any words of wisdom from the experts?:rolleyes:

---

### Post by Mohit_Jiindal on 2015-05-27
No response - I am quite surprised..

Someone please........

---

### Post by chandan-rattan-k on 2015-07-19
Hey Mohit, Did you find out the solution ? Even i facing same issue.

---

