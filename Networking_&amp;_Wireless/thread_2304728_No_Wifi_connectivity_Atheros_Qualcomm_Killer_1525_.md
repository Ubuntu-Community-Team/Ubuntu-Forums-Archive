---
title: "No Wifi connectivity Atheros Qualcomm Killer 1525 on Ubuntu 15.10"
date: 2015-11-29
forum: Networking &amp; Wireless
---

### Post by wood3d on 2015-11-29
Hello all,

Recently switched over from Windows 10, so I am completely new to everything. Forgive me. 

Did a clean install of 15.10, had no Wifi abilities, so connected via Ethernet cable. Spent the next three days attempting every trick I could find on the internet; some with success, others absolute failure. 

Did another fresh install of 15.10 with updates. Installed Wicd Network Manager because I found it delivered higher speed and a flawless wired connection with my setup. After exhausting my patience I now seek the advice of the experts (you!). 

Let us begin:

[B][I]Basic System Specs:

[/I][/B]Alienware 15 R2
[LIST]
[*]4x Intel(R) Core(TM) i5-6300HQ CPU @ 2.30GHz 
[*]12202MB Memory 
[*]Nvidia Geforce GTX 965M 
[*]Qualcomm Atheros Killer QCA6174 802.11ac Network Adapter 
[/LIST]

Ubuntu 15.10
[LIST]
[*]Linux 4.2.0-18-generic (x86_64) 
[/LIST]

lshw -C network
```
 sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: Qualcomm Atheros
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:3b:00.0
       logical name: enp59s0
       version: 10
       serial: 20:47:47:f2:85:10
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi msix bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=alx duplex=full ip=10.0.0.19 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:138 memory:dd500000-dd53ffff ioport:d000(size=128)
  *-network DISABLED
       description: Wireless interface
       product: QCA6174 802.11ac Wireless Network Adapter
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:3c:00.0
       logical name: wlp60s0
       version: 32
       serial: 9c:b6:d0:03:f8:9d
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath10k_pci driverversion=4.2.0-18-generic firmware=WLAN.RM.2.0-00180-QCARMSWPZ-1 latency=0 link=no multicast=yes wireless=IEEE 802.11abgn
       resources: irq:129 memory:dd200000-dd3fffff
 


```

rfkill list all```
rfkill list all
0: dell-rbtn: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


```

dmesg```
sudo dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 4.2.0-18-generic (buildd@lgw01-38) (gcc version 5.2.1 20151010 (Ubuntu 5.2.1-22ubuntu2) ) #22-Ubuntu SMP Fri Nov 6 18:25:50 UTC 2015 (Ubuntu 4.2.0-18.22-generic 4.2.3)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-4.2.0-18-generic.efi.signed root=UUID=1c5f30cd-4a80-45fd-acd9-80a1d5b0497b ro noprompt persistent quiet splash vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] x86/fpu: xstate_offset[2]: 0240, xstate_sizes[2]: 0100
[    0.000000] x86/fpu: xstate_offset[3]: 03c0, xstate_sizes[3]: 0040
[    0.000000] x86/fpu: xstate_offset[4]: 0400, xstate_sizes[4]: 0040
[    0.000000] x86/fpu: Supporting XSAVE feature 0x01: 'x87 floating point registers'
[    0.000000] x86/fpu: Supporting XSAVE feature 0x02: 'SSE registers'
[    0.000000] x86/fpu: Supporting XSAVE feature 0x04: 'AVX registers'
[    0.000000] x86/fpu: Supporting XSAVE feature 0x08: 'MPX bounds registers'
[    0.000000] x86/fpu: Supporting XSAVE feature 0x10: 'MPX CSR'
[    0.000000] x86/fpu: Enabled xstate features 0x1f, context size is 0x440 bytes, using 'standard' format.
[    0.000000] x86/fpu: Using 'eager' FPU context switches.
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x0000000000057fff] usable
[    0.000000] BIOS-e820: [mem 0x0000000000058000-0x0000000000058fff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000059000-0x000000000009efff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009f000-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x000000003130bfff] usable
[    0.000000] BIOS-e820: [mem 0x000000003130c000-0x000000003130cfff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x000000003130d000-0x0000000031336fff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000031337000-0x000000003138efff] usable
[    0.000000] BIOS-e820: [mem 0x000000003138f000-0x00000000318e4fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000318e5000-0x00000000361abfff] usable
[    0.000000] BIOS-e820: [mem 0x00000000361ac000-0x0000000037191fff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000037192000-0x00000000371d2fff] ACPI data
[    0.000000] BIOS-e820: [mem 0x00000000371d3000-0x0000000037b4efff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x0000000037b4f000-0x0000000037f82fff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000037f83000-0x0000000037ffdfff] type 20
[    0.000000] BIOS-e820: [mem 0x0000000037ffe000-0x0000000037ffefff] usable
[    0.000000] BIOS-e820: [mem 0x0000000038000000-0x00000000380fffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000e0000000-0x00000000efffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fe000000-0x00000000fe010fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ff000000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x00000003c3ffffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] efi: EFI v2.40 by American Megatrends
[    0.000000] efi:  ESRT=0x37f7f018  ACPI=0x371a0000  ACPI 2.0=0x371a0000  SMBIOS=0xf05e0  MPS=0xfcd20 
[    0.000000] esrt: Reserving ESRT space from 0x0000000037f7f018 to 0x0000000037f7f050.
[    0.000000] SMBIOS 2.8 present.
[    0.000000] DMI: Alienware Alienware 15 R2/Alienware 15 R2, BIOS 1.1.5 09/18/2015
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] e820: last_pfn = 0x3c4000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: write-back
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0080000000 mask 7F80000000 uncachable
[    0.000000]   1 base 0040000000 mask 7FC0000000 uncachable
[    0.000000]   2 base 003C000000 mask 7FFC000000 uncachable
[    0.000000]   3 base 003A000000 mask 7FFE000000 uncachable
[    0.000000]   4 base 0039000000 mask 7FFF000000 uncachable
[    0.000000]   5 base 0038800000 mask 7FFF800000 uncachable
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000]   8 disabled
[    0.000000]   9 disabled
[    0.000000] x86/PAT: Configuration [0-7]: WB  WC  UC- UC  WB  WC  UC- WT  
[    0.000000] e820: last_pfn = 0x37fff max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [mem 0x000fcfb0-0x000fcfbf] mapped at [ffff8800000fcfb0]
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] Base memory trampoline at [ffff88000008a000] 8a000 size 24576
[    0.000000] Using GB pages for direct mapping
[    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
[    0.000000]  [mem 0x00000000-0x000fffff] page 4k
[    0.000000] BRK [0x02ff0000, 0x02ff0fff] PGTABLE
[    0.000000] BRK [0x02ff1000, 0x02ff1fff] PGTABLE
[    0.000000] BRK [0x02ff2000, 0x02ff2fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x3c3e00000-0x3c3ffffff]
[    0.000000]  [mem 0x3c3e00000-0x3c3ffffff] page 2M
[    0.000000] BRK [0x02ff3000, 0x02ff3fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x3c0000000-0x3c3dfffff]
[    0.000000]  [mem 0x3c0000000-0x3c3dfffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x3a0000000-0x3bfffffff]
[    0.000000]  [mem 0x3a0000000-0x3bfffffff] page 1G
[    0.000000] init_memory_mapping: [mem 0x00100000-0x3130bfff]
[    0.000000]  [mem 0x00100000-0x001fffff] page 4k
[    0.000000]  [mem 0x00200000-0x311fffff] page 2M
[    0.000000]  [mem 0x31200000-0x3130bfff] page 4k
[    0.000000] init_memory_mapping: [mem 0x31337000-0x3138efff]
[    0.000000]  [mem 0x31337000-0x3138efff] page 4k
[    0.000000] init_memory_mapping: [mem 0x318e5000-0x361abfff]
[    0.000000]  [mem 0x318e5000-0x319fffff] page 4k
[    0.000000]  [mem 0x31a00000-0x35ffffff] page 2M
[    0.000000]  [mem 0x36000000-0x361abfff] page 4k
[    0.000000] BRK [0x02ff4000, 0x02ff4fff] PGTABLE
[    0.000000] BRK [0x02ff5000, 0x02ff5fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x37ffe000-0x37ffefff]
[    0.000000]  [mem 0x37ffe000-0x37ffefff] page 4k
[    0.000000] init_memory_mapping: [mem 0x100000000-0x39fffffff]
[    0.000000]  [mem 0x100000000-0x39fffffff] page 1G
[    0.000000] RAMDISK: [mem 0x2d9d0000-0x2f9edfff]
[    0.000000] ACPI: Early table checksum verification disabled
[    0.000000] ACPI: RSDP 0x00000000371A0000 000024 (v02 ALWARE)
[    0.000000] ACPI: XSDT 0x00000000371A00B0 0000DC (v01 ALWARE ALIENWRE 01072009 AMI  00010013)
[    0.000000] ACPI: FACP 0x00000000371C33E0 00010C (v05 ALWARE ALIENWRE 01072009 AMI  00010013)
[    0.000000] ACPI: DSDT 0x00000000371A0218 0231C5 (v02 ALWARE ALIENWRE 01072009 INTL 20120913)
[    0.000000] ACPI: FACS 0x0000000037B4BF80 000040
[    0.000000] ACPI: APIC 0x00000000371C34F0 000084 (v03 ALWARE ALIENWRE 01072009 AMI  00010013)
[    0.000000] ACPI: FPDT 0x00000000371C3578 000044 (v01 ALWARE ALIENWRE 01072009 AMI  00010013)
[    0.000000] ACPI: FIDT 0x00000000371C35C0 00009C (v01 ALWARE ALIENWRE 01072009 AMI  00010013)
[    0.000000] ACPI: MCFG 0x00000000371C3660 00003C (v01 ALWARE ALIENWRE 01072009 MSFT 00000097)
[    0.000000] ACPI: HPET 0x00000000371C36A0 000038 (v01 ALWARE ALIENWRE 01072009 AMI. 0005000B)
[    0.000000] ACPI: SSDT 0x00000000371C36D8 0004B9 (v01 SataRe SataTabl 00001000 INTL 20120913)
[    0.000000] ACPI: LPIT 0x00000000371C3B98 000094 (v01 INTEL  SKL      00000000 MSFT 0000005F)
[    0.000000] ACPI: SSDT 0x00000000371C3C30 000248 (v02 INTEL  sensrhub 00000000 INTL 20120913)
[    0.000000] ACPI: SSDT 0x00000000371C3E78 002BAE (v02 INTEL  PtidDevc 00001000 INTL 20120913)
[    0.000000] ACPI: DBGP 0x00000000371C6A28 000034 (v01 INTEL           00000000 MSFT 0000005F)
[    0.000000] ACPI: DBG2 0x00000000371C6A60 000054 (v00 INTEL           00000000 MSFT 0000005F)
[    0.000000] ACPI: SSDT 0x00000000371C6AB8 00069D (v02 INTEL  xh_rvp10 00000000 INTL 20120913)
[    0.000000] ACPI: SSDT 0x00000000371C7158 003489 (v02 DptfTa DptfTabl 00001000 INTL 20120913)
[    0.000000] ACPI: TPM2 0x00000000371CA5E8 000034 (v03        Tpm2Tabl 00000001 AMI  00000000)
[    0.000000] ACPI: SSDT 0x00000000371CA620 00080B (v01 AMITCG _SynTCG_ 00000001 INTL 20120913)
[    0.000000] ACPI: SSDT 0x00000000371CAE30 005580 (v02 SaSsdt SaSsdt   00003000 INTL 20120913)
[    0.000000] ACPI: UEFI 0x00000000371D03B0 000042 (v01                 00000000      00000000)
[    0.000000] ACPI: MSDM 0x00000000371D03F8 000055 (v03 ALWARE ALIENWRE 01072009 AMI  00010013)
[    0.000000] ACPI: SSDT 0x00000000371D0450 000E58 (v02 CpuRef CpuSsdt  00003000 INTL 20120913)
[    0.000000] ACPI: SSDT 0x00000000371D12A8 0000CE (v02 SgRef  SgPeg    00001000 INTL 20120913)
[    0.000000] ACPI: DMAR 0x00000000371D1378 0000A8 (v01 INTEL  SKL      00000001 INTL 00000001)
[    0.000000] ACPI: SSDT 0x00000000371D1420 00198C (v01 OptRef OptTabl  00001000 INTL 20120913)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x00000003c3ffffff]
[    0.000000] NODE_DATA(0) allocated [mem 0x3c3ff9000-0x3c3ffdfff]
[    0.000000]  [ffffea0000000000-ffffea000f1fffff] PMD -> [ffff8803b7600000-ffff8803c35fffff] on node 0
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x0000000000001000-0x0000000000ffffff]
[    0.000000]   DMA32    [mem 0x0000000001000000-0x00000000ffffffff]
[    0.000000]   Normal   [mem 0x0000000100000000-0x00000003c3ffffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x0000000000001000-0x0000000000057fff]
[    0.000000]   node   0: [mem 0x0000000000059000-0x000000000009efff]
[    0.000000]   node   0: [mem 0x0000000000100000-0x000000003130bfff]
[    0.000000]   node   0: [mem 0x0000000031337000-0x000000003138efff]
[    0.000000]   node   0: [mem 0x00000000318e5000-0x00000000361abfff]
[    0.000000]   node   0: [mem 0x0000000037ffe000-0x0000000037ffefff]
[    0.000000]   node   0: [mem 0x0000000100000000-0x00000003c3ffffff]
[    0.000000] Initmem setup node 0 [mem 0x0000000000001000-0x00000003c3ffffff]
[    0.000000] On node 0 totalpages: 3120073
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 54 pages reserved
[    0.000000]   DMA zone: 3997 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 3377 pages used for memmap
[    0.000000]   DMA32 zone: 216108 pages, LIFO batch:31
[    0.000000]   Normal zone: 45312 pages used for memmap
[    0.000000]   Normal zone: 2899968 pages, LIFO batch:31
[    0.000000] Reserving Intel graphics stolen memory at 0x39000000-0x3affffff
[    0.000000] ACPI: PM-Timer IO Port: 0x1808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x04] high edge lint[0x1])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-119
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a701 base: 0xfed00000
[    0.000000] smpboot: Allowing 4 CPUs, 0 hotplug CPUs
[    0.000000] PM: Registered nosave memory: [mem 0x00000000-0x00000fff]
[    0.000000] PM: Registered nosave memory: [mem 0x00058000-0x00058fff]
[    0.000000] PM: Registered nosave memory: [mem 0x0009f000-0x0009ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000fffff]
[    0.000000] PM: Registered nosave memory: [mem 0x3130c000-0x3130cfff]
[    0.000000] PM: Registered nosave memory: [mem 0x3130d000-0x31336fff]
[    0.000000] PM: Registered nosave memory: [mem 0x3138f000-0x318e4fff]
[    0.000000] PM: Registered nosave memory: [mem 0x361ac000-0x37191fff]
[    0.000000] PM: Registered nosave memory: [mem 0x37192000-0x371d2fff]
[    0.000000] PM: Registered nosave memory: [mem 0x371d3000-0x37b4efff]
[    0.000000] PM: Registered nosave memory: [mem 0x37b4f000-0x37f82fff]
[    0.000000] PM: Registered nosave memory: [mem 0x37f83000-0x37ffdfff]
[    0.000000] PM: Registered nosave memory: [mem 0x37fff000-0x37ffffff]
[    0.000000] PM: Registered nosave memory: [mem 0x38000000-0x380fffff]
[    0.000000] PM: Registered nosave memory: [mem 0x38100000-0x38ffffff]
[    0.000000] PM: Registered nosave memory: [mem 0x39000000-0x3affffff]
[    0.000000] PM: Registered nosave memory: [mem 0x3b000000-0xdfffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xe0000000-0xefffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xf0000000-0xfdffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfe000000-0xfe010fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfe011000-0xfebfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xfec00fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec01000-0xfedfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfee00000-0xfee00fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfee01000-0xfeffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xff000000-0xffffffff]
[    0.000000] e820: [mem 0x3b000000-0xdfffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] clocksource: refined-jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645519600211568 ns
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 33 pages/cpu @ffff8803c3c00000 s96728 r8192 d30248 u524288
[    0.000000] pcpu-alloc: s96728 r8192 d30248 u524288 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 3071266
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.2.0-18-generic.efi.signed root=UUID=1c5f30cd-4a80-45fd-acd9-80a1d5b0497b ro noprompt persistent quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 12092108K/12480292K available (8146K kernel code, 1237K rwdata, 3800K rodata, 1460K init, 1292K bss, 388184K reserved, 0K cma-reserved)
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     Build-time adjustment of leaf fanout to 64.
[    0.000000]     RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=4.
[    0.000000] RCU: Adjusting geometry for rcu_fanout_leaf=64, nr_cpu_ids=4
[    0.000000] NR_IRQS:16640 nr_irqs:1024 16
[    0.000000]     Offload RCU callbacks from all CPUs
[    0.000000]     Offload RCU callbacks from CPUs: 0-3.
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] clocksource: hpet: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 79635855245 ns
[    0.000000] hpet clockevent registered
[    0.000000] tsc: PIT calibration matches HPET. 2 loops
[    0.000000] tsc: Detected 2302.980 MHz processor
[    0.000023] Calibrating delay loop (skipped), value calculated using timer frequency.. 4605.96 BogoMIPS (lpj=9211920)
[    0.000026] pid_max: default: 32768 minimum: 301
[    0.000029] ACPI: Core revision 20150619
[    0.023897] ACPI Error: [\_SB_.PCI0.XHC_.RHUB.HS11] Namespace lookup failure, AE_NOT_FOUND (20150619/dswload-210)
[    0.023903] ACPI Exception: AE_NOT_FOUND, During name lookup/catalog (20150619/psobject-224)
[    0.035762] ACPI: All ACPI Tables successfully acquired
[    0.037448] Security Framework initialized
[    0.037455] AppArmor: AppArmor initialized
[    0.037456] Yama: becoming mindful.
[    0.038268] Dentry cache hash table entries: 2097152 (order: 12, 16777216 bytes)
[    0.040967] Inode-cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.042031] Mount-cache hash table entries: 32768 (order: 6, 262144 bytes)
[    0.042044] Mountpoint-cache hash table entries: 32768 (order: 6, 262144 bytes)
[    0.042209] Initializing cgroup subsys blkio
[    0.042211] Initializing cgroup subsys memory
[    0.042216] Initializing cgroup subsys devices
[    0.042218] Initializing cgroup subsys freezer
[    0.042219] Initializing cgroup subsys net_cls
[    0.042221] Initializing cgroup subsys perf_event
[    0.042222] Initializing cgroup subsys net_prio
[    0.042223] Initializing cgroup subsys hugetlb
[    0.042243] CPU: Physical Processor ID: 0
[    0.042244] CPU: Processor Core ID: 0
[    0.042247] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
[    0.042248] ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
[    0.043359] mce: CPU supports 10 MCE banks
[    0.043374] CPU0: Thermal monitoring enabled (TM1)
[    0.043382] process: using mwait in idle threads
[    0.043384] Last level iTLB entries: 4KB 128, 2MB 8, 4MB 8
[    0.043385] Last level dTLB entries: 4KB 64, 2MB 0, 4MB 0, 1GB 4
[    0.043670] Freeing SMP alternatives memory: 28K (ffffffff81ea4000 - ffffffff81eab000)
[    0.046901] ftrace: allocating 30905 entries in 121 pages
[    0.057549] DMAR: Host address width 39
[    0.057551] DMAR: DRHD base: 0x000000fed90000 flags: 0x0
[    0.057557] DMAR: dmar0: reg_base_addr fed90000 ver 1:0 cap 1c0000c40660462 ecap 7e3ff0501e
[    0.057558] DMAR: DRHD base: 0x000000fed91000 flags: 0x1
[    0.057561] DMAR: dmar1: reg_base_addr fed91000 ver 1:0 cap d2008c40660462 ecap f050da
[    0.057562] DMAR: RMRR base: 0x000000370e4000 end: 0x00000037103fff
[    0.057563] DMAR: RMRR base: 0x00000038800000 end: 0x0000003affffff
[    0.057565] DMAR-IR: IOAPIC id 2 under DRHD base  0xfed91000 IOMMU 1
[    0.057566] DMAR-IR: HPET id 0 under DRHD base 0xfed91000
[    0.057566] DMAR-IR: x2apic is disabled because BIOS sets x2apic opt out bit.
[    0.057567] DMAR-IR: Use 'intremap=no_x2apic_optout' to override the BIOS setting.
[    0.057767] DMAR: DRHD: handling fault status reg 2
[    0.057770] DMAR: INTR-REMAP: Request device [[f0:1f.0] fault index 0
               INTR-REMAP:[fault reason 37] Blocked a compatibility format interrupt request
[    0.058974] DMAR-IR: Enabled IRQ remapping in xapic mode
[    0.058974] x2apic: IRQ remapping doesn't support X2APIC mode
[    0.062896] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.102618] TSC deadline timer enabled
[    0.102623] smpboot: CPU0: Intel(R) Core(TM) i5-6300HQ CPU @ 2.30GHz (fam: 06, model: 5e, stepping: 03)
[    0.102642] Performance Events: PEBS fmt3+, 32-deep LBR, Skylake events, full-width counters, Intel PMU driver.
[    0.102665] ... version:                4
[    0.102666] ... bit width:              48
[    0.102667] ... generic registers:      8
[    0.102667] ... value mask:             0000ffffffffffff
[    0.102668] ... max period:             0000ffffffffffff
[    0.102669] ... fixed-purpose events:   3
[    0.102669] ... event mask:             00000007000000ff
[    0.103295] x86: Booting SMP configuration:
[    0.103296] .... node  #0, CPUs:      #1
[    0.107688] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.107743]  #2 #3
[    0.116266] x86: Booted up 1 node, 4 CPUs
[    0.116268] smpboot: Total of 4 processors activated (18423.84 BogoMIPS)
[    0.119318] devtmpfs: initialized
[    0.121366] evm: security.selinux
[    0.121367] evm: security.SMACK64
[    0.121367] evm: security.SMACK64EXEC
[    0.121368] evm: security.SMACK64TRANSMUTE
[    0.121368] evm: security.SMACK64MMAP
[    0.121369] evm: security.ima
[    0.121370] evm: security.capability
[    0.121416] PM: Registering ACPI NVS region [mem 0x3130c000-0x3130cfff] (4096 bytes)
[    0.121417] PM: Registering ACPI NVS region [mem 0x371d3000-0x37b4efff] (9945088 bytes)
[    0.121546] clocksource: jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645041785100000 ns
[    0.121618] pinctrl core: initialized pinctrl subsystem
[    0.121772] RTC time: 16:18:47, date: 11/29/15
[    0.121867] NET: Registered protocol family 16
[    0.127666] cpuidle: using governor ladder
[    0.131689] cpuidle: using governor menu
[    0.131773] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.131774] ACPI: bus type PCI registered
[    0.131776] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.131843] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.131845] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    0.131857] PCI: Using configuration type 1 for base access
[    0.139978] ACPI: Added _OSI(Module Device)
[    0.139980] ACPI: Added _OSI(Processor Device)
[    0.139981] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.139982] ACPI: Added _OSI(Processor Aggregator Device)
[    0.147802] ACPI: Executed 21 blocks of module-level executable AML code
[    0.154646] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.158748] ACPI: Dynamic OEM Table Load:
[    0.158754] ACPI: SSDT 0xFFFF8803B4D03400 00037F (v02 PmRef  Cpu0Cst  00003001 INTL 20120913)
[    0.159607] ACPI: Dynamic OEM Table Load:
[    0.159611] ACPI: SSDT 0xFFFF8803B535A800 000579 (v02 PmRef  Cpu0Ist  00003000 INTL 20120913)
[    0.161431] ACPI: Dynamic OEM Table Load:
[    0.161435] ACPI: SSDT 0xFFFF8803B535B000 0005AA (v02 PmRef  ApIst    00003000 INTL 20120913)
[    0.162421] ACPI: Dynamic OEM Table Load:
[    0.162425] ACPI: SSDT 0xFFFF8803B4D23C00 000119 (v02 PmRef  ApCst    00003000 INTL 20120913)
[    0.164968] ACPI : EC: EC started
[    0.165307] ACPI: Interpreter enabled
[    0.165315] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20150619/hwxface-580)
[    0.165323] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20150619/hwxface-580)
[    0.165340] ACPI: (supports S0 S3 S4 S5)
[    0.165341] ACPI: Using IOAPIC for interrupt routing
[    0.165368] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.167116] ACPI: Power Resource [PG00] (on)
[    0.184541] ACPI: Power Resource [PG01] (on)
[    0.184912] ACPI: Power Resource [PG02] (on)
[    0.185484] ACPI: Power Resource [WRST] (off)
[    0.185793] ACPI: Power Resource [WRST] (off)
[    0.186100] ACPI: Power Resource [WRST] (off)
[    0.186407] ACPI: Power Resource [WRST] (off)
[    0.186714] ACPI: Power Resource [WRST] (off)
[    0.187015] ACPI: Power Resource [WRST] (off)
[    0.187326] ACPI: Power Resource [WRST] (off)
[    0.187640] ACPI: Power Resource [WRST] (off)
[    0.187954] ACPI: Power Resource [WRST] (off)
[    0.188268] ACPI: Power Resource [WRST] (off)
[    0.188618] ACPI: Power Resource [WRST] (off)
[    0.188928] ACPI: Power Resource [WRST] (off)
[    0.189235] ACPI: Power Resource [WRST] (off)
[    0.189542] ACPI: Power Resource [WRST] (off)
[    0.189848] ACPI: Power Resource [WRST] (off)
[    0.190155] ACPI: Power Resource [WRST] (off)
[    0.190442] ACPI: Power Resource [WRST] (off)
[    0.190706] ACPI: Power Resource [WRST] (off)
[    0.190968] ACPI: Power Resource [WRST] (off)
[    0.191234] ACPI: Power Resource [WRST] (off)
[    0.205020] ACPI Error: No object attached to node [_ADR] ffff8803b71104d8 (20150619/exresnte-128)
[    0.205023] ACPI Error: Method execution failed [\_SB_.PCI0.XHC_.RHUB.HS07.WCAM._ADR] (Node ffff8803b71104d8), AE_AML_NO_OPERAND (20150619/uteval-103)
[    0.212504] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-fe])
[    0.212510] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    0.212540] \_SB_.PCI0:_OSC invalid UUID
[    0.212541] _OSC request data:1 1f 0 
[    0.212545] acpi PNP0A08:00: _OSC failed (AE_ERROR); disabling ASPM
[    0.213127] PCI host bridge to bus 0000:00
[    0.213129] pci_bus 0000:00: root bus resource [bus 00-fe]
[    0.213131] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7 window]
[    0.213133] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff window]
[    0.213134] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff window]
[    0.213135] pci_bus 0000:00: root bus resource [mem 0x3b000000-0xdfffffff window]
[    0.213137] pci_bus 0000:00: root bus resource [mem 0xfd000000-0xfe7fffff window]
[    0.213144] pci 0000:00:00.0: [8086:1910] type 00 class 0x060000
[    0.213432] pci 0000:00:01.0: [8086:1901] type 01 class 0x060400
[    0.213468] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.213576] pci 0000:00:01.0: System wakeup disabled by ACPI
[    0.213631] pci 0000:00:02.0: [8086:191b] type 00 class 0x030000
[    0.213645] pci 0000:00:02.0: reg 0x10: [mem 0xdb000000-0xdbffffff 64bit]
[    0.213651] pci 0000:00:02.0: reg 0x18: [mem 0x70000000-0x7fffffff 64bit pref]
[    0.213655] pci 0000:00:02.0: reg 0x20: [io  0xf000-0xf03f]
[    0.213768] pci 0000:00:04.0: [8086:1903] type 00 class 0x118000
[    0.213783] pci 0000:00:04.0: reg 0x10: [mem 0xdd120000-0xdd127fff 64bit]
[    0.213957] pci 0000:00:14.0: [8086:a12f] type 00 class 0x0c0330
[    0.213984] pci 0000:00:14.0: reg 0x10: [mem 0xdd110000-0xdd11ffff 64bit]
[    0.214035] pci 0000:00:14.0: PME# supported from D3hot D3cold
[    0.214131] pci 0000:00:14.0: System wakeup disabled by ACPI
[    0.214167] pci 0000:00:14.2: [8086:a131] type 00 class 0x118000
[    0.214192] pci 0000:00:14.2: reg 0x10: [mem 0xdd136000-0xdd136fff 64bit]
[    0.214340] pci 0000:00:16.0: [8086:a13a] type 00 class 0x078000
[    0.214392] pci 0000:00:16.0: reg 0x10: [mem 0xdd135000-0xdd135fff 64bit]
[    0.214476] pci 0000:00:16.0: PME# supported from D3hot
[    0.214612] pci 0000:00:17.0: [8086:282a] type 00 class 0x010400
[    0.214633] pci 0000:00:17.0: reg 0x10: [mem 0xdd130000-0xdd131fff]
[    0.214640] pci 0000:00:17.0: reg 0x14: [mem 0xdd134000-0xdd1340ff]
[    0.214647] pci 0000:00:17.0: reg 0x18: [io  0xf090-0xf097]
[    0.214654] pci 0000:00:17.0: reg 0x1c: [io  0xf080-0xf083]
[    0.214661] pci 0000:00:17.0: reg 0x20: [io  0xf060-0xf07f]
[    0.214668] pci 0000:00:17.0: reg 0x24: [mem 0xdd133000-0xdd1337ff]
[    0.214694] pci 0000:00:17.0: PME# supported from D3hot
[    0.214817] pci 0000:00:1c.0: [8086:a110] type 01 class 0x060400
[    0.214876] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.214977] pci 0000:00:1c.0: System wakeup disabled by ACPI
[    0.215018] pci 0000:00:1c.4: [8086:a114] type 01 class 0x060400
[    0.215069] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.215168] pci 0000:00:1c.4: System wakeup disabled by ACPI
[    0.215199] pci 0000:00:1c.5: [8086:a115] type 01 class 0x060400
[    0.215261] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    0.215345] pci 0000:00:1c.5: System wakeup disabled by ACPI
[    0.215373] pci 0000:00:1c.6: [8086:a116] type 01 class 0x060400
[    0.215422] pci 0000:00:1c.6: PME# supported from D0 D3hot D3cold
[    0.215506] pci 0000:00:1c.6: System wakeup disabled by ACPI
[    0.215541] pci 0000:00:1f.0: [8086:a14e] type 00 class 0x060100
[    0.215726] pci 0000:00:1f.2: [8086:a121] type 00 class 0x058000
[    0.215737] pci 0000:00:1f.2: reg 0x10: [mem 0xdd12c000-0xdd12ffff]
[    0.215864] pci 0000:00:1f.3: [8086:a170] type 00 class 0x040300
[    0.215895] pci 0000:00:1f.3: reg 0x10: [mem 0xdd128000-0xdd12bfff 64bit]
[    0.215918] pci 0000:00:1f.3: reg 0x20: [mem 0xdd100000-0xdd10ffff 64bit]
[    0.215945] pci 0000:00:1f.3: PME# supported from D3hot D3cold
[    0.216066] pci 0000:00:1f.3: System wakeup disabled by ACPI
[    0.216100] pci 0000:00:1f.4: [8086:a123] type 00 class 0x0c0500
[    0.216153] pci 0000:00:1f.4: reg 0x10: [mem 0xdd132000-0xdd1320ff 64bit]
[    0.216222] pci 0000:00:1f.4: reg 0x20: [io  0xf040-0xf05f]
[    0.216410] pci 0000:01:00.0: [10de:13d9] type 00 class 0x030200
[    0.216424] pci 0000:01:00.0: reg 0x10: [mem 0xdc000000-0xdcffffff]
[    0.216431] pci 0000:01:00.0: reg 0x14: [mem 0xb0000000-0xbfffffff 64bit pref]
[    0.216438] pci 0000:01:00.0: reg 0x1c: [mem 0xc0000000-0xc1ffffff 64bit pref]
[    0.216443] pci 0000:01:00.0: reg 0x24: [io  0xe000-0xe07f]
[    0.216448] pci 0000:01:00.0: reg 0x30: [mem 0xdd000000-0xdd07ffff pref]
[    0.216507] pci 0000:01:00.0: System wakeup disabled by ACPI
[    0.228288] pci 0000:00:01.0: PCI bridge to [bus 01]
[    0.228290] pci 0000:00:01.0:   bridge window [io  0xe000-0xefff]
[    0.228293] pci 0000:00:01.0:   bridge window [mem 0xdc000000-0xdd0fffff]
[    0.228296] pci 0000:00:01.0:   bridge window [mem 0xb0000000-0xc1ffffff 64bit pref]
[    0.228385] acpiphp: Slot [1] registered
[    0.228390] pci 0000:00:1c.0: PCI bridge to [bus 02-3a]
[    0.228394] pci 0000:00:1c.0:   bridge window [mem 0xc4000000-0xda0fffff]
[    0.228399] pci 0000:00:1c.0:   bridge window [mem 0x80000000-0xa1ffffff 64bit pref]
[    0.228489] pci 0000:3b:00.0: [1969:e0a1] type 00 class 0x020000
[    0.228534] pci 0000:3b:00.0: reg 0x10: [mem 0xdd500000-0xdd53ffff 64bit]
[    0.228545] pci 0000:3b:00.0: reg 0x18: [io  0xd000-0xd07f]
[    0.228619] pci 0000:3b:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.240306] pci 0000:00:1c.4: PCI bridge to [bus 3b]
[    0.240309] pci 0000:00:1c.4:   bridge window [io  0xd000-0xdfff]
[    0.240312] pci 0000:00:1c.4:   bridge window [mem 0xdd500000-0xdd5fffff]
[    0.240501] pci 0000:3c:00.0: [168c:003e] type 00 class 0x028000
[    0.240682] pci 0000:3c:00.0: reg 0x10: [mem 0xdd200000-0xdd3fffff 64bit]
[    0.241104] pci 0000:3c:00.0: PME# supported from D0 D3hot D3cold
[    0.252414] pci 0000:00:1c.5: PCI bridge to [bus 3c]
[    0.252419] pci 0000:00:1c.5:   bridge window [mem 0xdd200000-0xdd3fffff]
[    0.252527] pci 0000:3d:00.0: [10ec:5227] type 00 class 0xff0000
[    0.252561] pci 0000:3d:00.0: reg 0x10: [mem 0xdd400000-0xdd400fff]
[    0.252651] pci 0000:3d:00.0: supports D1 D2
[    0.252653] pci 0000:3d:00.0: PME# supported from D1 D2 D3hot D3cold
[    0.264353] pci 0000:00:1c.6: PCI bridge to [bus 3d]
[    0.264357] pci 0000:00:1c.6:   bridge window [mem 0xdd400000-0xdd4fffff]
[    0.273086] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 10 *11 12 14 15)
[    0.273132] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 *10 11 12 14 15)
[    0.273176] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 10 *11 12 14 15)
[    0.273219] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 10 *11 12 14 15)
[    0.273264] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 10 *11 12 14 15)
[    0.273309] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 10 *11 12 14 15)
[    0.273352] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 10 *11 12 14 15)
[    0.273394] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 10 *11 12 14 15)
[    0.273788] ACPI: Enabled 7 GPEs in block 00 to 7F
[    0.273821] ACPI : EC: GPE = 0x14, I/O: command/status = 0x66, data = 0x62
[    0.273899] vgaarb: setting as boot device: PCI:0000:00:02.0
[    0.273901] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.273903] vgaarb: loaded
[    0.273904] vgaarb: bridge control possible 0000:00:02.0
[    0.274127] SCSI subsystem initialized
[    0.274156] libata version 3.00 loaded.
[    0.274174] ACPI: bus type USB registered
[    0.274189] usbcore: registered new interface driver usbfs
[    0.274196] usbcore: registered new interface driver hub
[    0.274209] usbcore: registered new device driver usb
[    0.274357] PCI: Using ACPI for IRQ routing
[    0.297537] PCI: pci_cache_line_size set to 64 bytes
[    0.297684] e820: reserve RAM buffer [mem 0x00058000-0x0005ffff]
[    0.297685] e820: reserve RAM buffer [mem 0x0009f000-0x0009ffff]
[    0.297686] e820: reserve RAM buffer [mem 0x3130c000-0x33ffffff]
[    0.297687] e820: reserve RAM buffer [mem 0x3138f000-0x33ffffff]
[    0.297688] e820: reserve RAM buffer [mem 0x361ac000-0x37ffffff]
[    0.297689] e820: reserve RAM buffer [mem 0x37fff000-0x37ffffff]
[    0.297763] NetLabel: Initializing
[    0.297764] NetLabel:  domain hash size = 128
[    0.297765] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.297773] NetLabel:  unlabeled traffic allowed by default
[    0.297857] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    0.297861] hpet0: 8 comparators, 64-bit 24.000000 MHz counter
[    0.299907] clocksource: Switched to clocksource hpet
[    0.304193] AppArmor: AppArmor Filesystem Enabled
[    0.304230] pnp: PnP ACPI init
[    0.304365] pnp 00:00: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.304388] pnp 00:01: Plug and Play ACPI device, IDs DLL0708 PNP0f13 (active)
[    0.304478] system 00:02: [io  0x0680-0x069f] has been reserved
[    0.304480] system 00:02: [io  0xffff] has been reserved
[    0.304481] system 00:02: [io  0xffff] has been reserved
[    0.304482] system 00:02: [io  0xffff] has been reserved
[    0.304483] system 00:02: [io  0x1800-0x18fe] could not be reserved
[    0.304484] system 00:02: [io  0x164e-0x164f] has been reserved
[    0.304486] system 00:02: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.304552] system 00:03: [io  0x0800-0x087f] has been reserved
[    0.304554] system 00:03: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.304568] pnp 00:04: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.304594] system 00:05: [io  0x1854-0x1857] has been reserved
[    0.304596] system 00:05: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
[    0.308111] system 00:06: [mem 0xfed10000-0xfed17fff] has been reserved
[    0.308113] system 00:06: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.308115] system 00:06: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.308116] system 00:06: [mem 0xe0000000-0xefffffff] has been reserved
[    0.308118] system 00:06: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.308119] system 00:06: [mem 0xfed90000-0xfed93fff] could not be reserved
[    0.308121] system 00:06: [mem 0xfed45000-0xfed8ffff] has been reserved
[    0.308122] system 00:06: [mem 0xff000000-0xffffffff] has been reserved
[    0.308124] system 00:06: [mem 0xfee00000-0xfeefffff] could not be reserved
[    0.308126] system 00:06: [mem 0xdffe0000-0xdfffffff] has been reserved
[    0.308128] system 00:06: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.308163] system 00:07: [mem 0xfd000000-0xfdabffff] has been reserved
[    0.308165] system 00:07: [mem 0xfdad0000-0xfdadffff] has been reserved
[    0.308166] system 00:07: [mem 0xfdb00000-0xfdffffff] has been reserved
[    0.308168] system 00:07: [mem 0xfe000000-0xfe01ffff] could not be reserved
[    0.308169] system 00:07: [mem 0xfe036000-0xfe03bfff] has been reserved
[    0.308171] system 00:07: [mem 0xfe03d000-0xfe3fffff] has been reserved
[    0.308172] system 00:07: [mem 0xfe410000-0xfe7fffff] has been reserved
[    0.308174] system 00:07: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.309126] system 00:08: [mem 0xfdaf0000-0xfdafffff] has been reserved
[    0.309128] system 00:08: [mem 0xfdae0000-0xfdaeffff] has been reserved
[    0.309130] system 00:08: [mem 0xfdac0000-0xfdacffff] has been reserved
[    0.309132] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.309881] pnp: PnP ACPI: found 9 devices
[    0.318051] clocksource: acpi_pm: mask: 0xffffff max_cycles: 0xffffff, max_idle_ns: 2085701024 ns
[    0.318065] pci 0000:00:1c.0: bridge window [io  0x1000-0x0fff] to [bus 02-3a] add_size 1000
[    0.318080] pci 0000:00:1c.0: res[13]=[io  0x1000-0x0fff] res_to_dev_res add_size 1000 min_align 1000
[    0.318082] pci 0000:00:1c.0: res[13]=[io  0x1000-0x1fff] res_to_dev_res add_size 1000 min_align 1000
[    0.318084] pci 0000:00:1c.0: BAR 13: assigned [io  0x2000-0x2fff]
[    0.318086] pci 0000:00:01.0: PCI bridge to [bus 01]
[    0.318088] pci 0000:00:01.0:   bridge window [io  0xe000-0xefff]
[    0.318090] pci 0000:00:01.0:   bridge window [mem 0xdc000000-0xdd0fffff]
[    0.318092] pci 0000:00:01.0:   bridge window [mem 0xb0000000-0xc1ffffff 64bit pref]
[    0.318095] pci 0000:00:1c.0: PCI bridge to [bus 02-3a]
[    0.318097] pci 0000:00:1c.0:   bridge window [io  0x2000-0x2fff]
[    0.318100] pci 0000:00:1c.0:   bridge window [mem 0xc4000000-0xda0fffff]
[    0.318102] pci 0000:00:1c.0:   bridge window [mem 0x80000000-0xa1ffffff 64bit pref]
[    0.318106] pci 0000:00:1c.4: PCI bridge to [bus 3b]
[    0.318108] pci 0000:00:1c.4:   bridge window [io  0xd000-0xdfff]
[    0.318111] pci 0000:00:1c.4:   bridge window [mem 0xdd500000-0xdd5fffff]
[    0.318115] pci 0000:00:1c.5: PCI bridge to [bus 3c]
[    0.318118] pci 0000:00:1c.5:   bridge window [mem 0xdd200000-0xdd3fffff]
[    0.318123] pci 0000:00:1c.6: PCI bridge to [bus 3d]
[    0.318126] pci 0000:00:1c.6:   bridge window [mem 0xdd400000-0xdd4fffff]
[    0.318131] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7 window]
[    0.318133] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff window]
[    0.318134] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff window]
[    0.318135] pci_bus 0000:00: resource 7 [mem 0x3b000000-0xdfffffff window]
[    0.318136] pci_bus 0000:00: resource 8 [mem 0xfd000000-0xfe7fffff window]
[    0.318137] pci_bus 0000:01: resource 0 [io  0xe000-0xefff]
[    0.318138] pci_bus 0000:01: resource 1 [mem 0xdc000000-0xdd0fffff]
[    0.318139] pci_bus 0000:01: resource 2 [mem 0xb0000000-0xc1ffffff 64bit pref]
[    0.318141] pci_bus 0000:02: resource 0 [io  0x2000-0x2fff]
[    0.318142] pci_bus 0000:02: resource 1 [mem 0xc4000000-0xda0fffff]
[    0.318143] pci_bus 0000:02: resource 2 [mem 0x80000000-0xa1ffffff 64bit pref]
[    0.318144] pci_bus 0000:3b: resource 0 [io  0xd000-0xdfff]
[    0.318145] pci_bus 0000:3b: resource 1 [mem 0xdd500000-0xdd5fffff]
[    0.318146] pci_bus 0000:3c: resource 1 [mem 0xdd200000-0xdd3fffff]
[    0.318147] pci_bus 0000:3d: resource 1 [mem 0xdd400000-0xdd4fffff]
[    0.318167] NET: Registered protocol family 2
[    0.318307] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.318511] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.318606] TCP: Hash tables configured (established 131072 bind 65536)
[    0.318630] UDP hash table entries: 8192 (order: 6, 262144 bytes)
[    0.318667] UDP-Lite hash table entries: 8192 (order: 6, 262144 bytes)
[    0.318716] NET: Registered protocol family 1
[    0.318727] pci 0000:00:02.0: Video device with shadowed ROM
[    0.319527] PCI: CLS 0 bytes, default 64
[    0.319558] Trying to unpack rootfs image as initramfs...
[    0.741693] Freeing initrd memory: 32888K (ffff88002d9d0000 - ffff88002f9ee000)
[    0.741717] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.741719] software IO TLB [mem 0x299d0000-0x2d9d0000] (64MB) mapped at [ffff8800299d0000-ffff88002d9cffff]
[    0.741864] microcode: CPU0 sig=0x506e3, pf=0x20, revision=0x33
[    0.741874] microcode: CPU1 sig=0x506e3, pf=0x20, revision=0x33
[    0.741885] microcode: CPU2 sig=0x506e3, pf=0x20, revision=0x33
[    0.741895] microcode: CPU3 sig=0x506e3, pf=0x20, revision=0x33
[    0.742016] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.742134] Scanning for low memory corruption every 60 seconds
[    0.742505] futex hash table entries: 1024 (order: 4, 65536 bytes)
[    0.742516] Initialise system trusted keyring
[    0.742532] audit: initializing netlink subsys (disabled)
[    0.742543] audit: type=2000 audit(1448813927.744:1): initialized
[    0.742842] HugeTLB registered 1 GB page size, pre-allocated 0 pages
[    0.742843] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.743881] zpool: loaded
[    0.743884] zbud: loaded
[    0.744098] VFS: Disk quotas dquot_6.6.0
[    0.744120] VFS: Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.744646] fuse init (API version 7.23)
[    0.744805] Key type big_key registered
[    0.746202] Key type asymmetric registered
[    0.746205] Asymmetric key parser 'x509' registered
[    0.746213] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 249)
[    0.746341] io scheduler noop registered
[    0.746344] io scheduler deadline registered (default)
[    0.746389] io scheduler cfq registered
[    0.746957] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.746962] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.746990] efifb: probing for efifb
[    0.747001] efifb: framebuffer at 0x70000000, mapped to 0xffffc90002000000, using 8128k, total 8128k
[    0.747002] efifb: mode is 1920x1080x32, linelength=7680, pages=1
[    0.747003] efifb: scrolling: redraw
[    0.747004] efifb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    0.747094] Console: switching to colour frame buffer device 240x67
[    0.747111] fb0: EFI VGA frame buffer device
[    0.747118] intel_idle: MWAIT substates: 0x11142120
[    0.747119] intel_idle: v0.4 model 0x5E
[    0.747119] intel_idle: lapic_timer_reliable_states 0xffffffff
[    0.747346] ACPI: AC Adapter [ACAD] (on-line)
[    0.747400] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:3f/PNP0C0D:00/input/input0
[    0.747413] ACPI: Lid Switch [LID0]
[    0.747444] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1
[    0.747446] ACPI: Power Button [PWRB]
[    0.747470] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.747472] ACPI: Power Button [PWRF]
[    0.747662] GHES: HEST is not enabled!
[    0.747770] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.780612] ACPI: Battery Slot [BAT1] (battery present)
[    0.780983] Linux agpgart interface v0.103
[    0.784199] brd: module loaded
[    0.785344] loop: module loaded
[    0.785542] libphy: Fixed MDIO Bus: probed
[    0.785543] tun: Universal TUN/TAP device driver, 1.6
[    0.785544] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.785676] PPP generic driver version 2.4.2
[    0.785911] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    0.785916] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 1
[    0.786015] xhci_hcd 0000:00:14.0: hcc params 0x200077c1 hci version 0x100 quirks 0x00109810
[    0.786019] xhci_hcd 0000:00:14.0: cache line size of 64 is not supported
[    0.786078] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    0.786080] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.786081] usb usb1: Product: xHCI Host Controller
[    0.786082] usb usb1: Manufacturer: Linux 4.2.0-18-generic xhci-hcd
[    0.786083] usb usb1: SerialNumber: 0000:00:14.0
[    0.786230] hub 1-0:1.0: USB hub found
[    0.786245] hub 1-0:1.0: 16 ports detected
[    0.794927] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    0.794930] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 2
[    0.794951] usb usb2: New USB device found, idVendor=1d6b, idProduct=0003
[    0.794952] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.794953] usb usb2: Product: xHCI Host Controller
[    0.794954] usb usb2: Manufacturer: Linux 4.2.0-18-generic xhci-hcd
[    0.794955] usb usb2: SerialNumber: 0000:00:14.0
[    0.795080] hub 2-0:1.0: USB hub found
[    0.795089] hub 2-0:1.0: 8 ports detected
[    0.799327] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.799331] ehci-pci: EHCI PCI platform driver
[    0.799338] ehci-platform: EHCI generic platform driver
[    0.799345] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.799347] ohci-pci: OHCI PCI platform driver
[    0.799353] ohci-platform: OHCI generic platform driver
[    0.799359] uhci_hcd: USB Universal Host Controller Interface driver
[    0.799393] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.824231] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.824233] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.824553] mousedev: PS/2 mouse device common for all mice
[    0.825336] rtc_cmos 00:04: RTC can wake from S4
[    0.825861] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    0.825941] rtc_cmos 00:04: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    0.825947] i2c /dev entries driver
[    0.825994] device-mapper: uevent: version 1.0.3
[    0.826096] device-mapper: ioctl: 4.33.0-ioctl (2015-8-18) initialised: dm-devel@redhat.com
[    0.826107] Intel P-state driver initializing.
[    0.826342] ledtrig-cpu: registered to indicate activity on CPUs
[    0.826348] EFI Variables Facility v0.08 2004-May-17
[    0.832739] PCCT header not found.
[    0.832919] NET: Registered protocol family 10
[    0.833299] NET: Registered protocol family 17
[    0.833309] Key type dns_resolver registered
[    0.834274] Loading compiled-in X.509 certificates
[    0.834951] Loaded X.509 cert 'Build time autogenerated kernel key: 93ad27021225ce1bb4865e4bab1e2b6a5f099429'
[    0.834975] registered taskstats version 1
[    0.834991] zswap: loading zswap
[    0.834993] zswap: using zbud pool
[    0.834998] zswap: using lzo compressor
[    0.838135] Key type trusted registered
[    0.840866] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    0.843523] Key type encrypted registered
[    0.843530] AppArmor: AppArmor sha1 policy hashing enabled
[    0.843534] ima: No TPM chip found, activating TPM-bypass!
[    0.843564] evm: HMAC attrs: 0x1
[    0.844733]   Magic number: 7:180:339
[    0.844738] usb usb1-port10: hash matches
[    0.844967] rtc_cmos 00:04: setting system clock to 2015-11-29 16:18:48 UTC (1448813928)
[    0.845147] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.845148] EDD information not available.
[    0.845224] PM: Hibernation image not present or could not be loaded.
[    0.845646] Freeing unused kernel memory: 1460K (ffffffff81d37000 - ffffffff81ea4000)
[    0.845647] Write protecting the kernel read-only data: 12288k
[    0.846065] Freeing unused kernel memory: 36K (ffff8800027f7000 - ffff880002800000)
[    0.846259] Freeing unused kernel memory: 296K (ffff880002bb6000 - ffff880002c00000)
[    0.857748] random: systemd-udevd urandom read with 7 bits of entropy available
[    0.883660] hidraw: raw HID events driver (C) Jiri Kosina
[    0.890718] wmi: Mapper loaded
[    0.911791] ahci 0000:00:17.0: version 3.0
[    0.912452] [drm] Initialized drm 1.1.0 20060810
[    0.914978] rtsx_pci 0000:3d:00.0: enabling device (0000 -> 0002)
[    0.915175] rtsx_pci 0000:3d:00.0: rtsx_pci_acquire_irq: pcr->msi_en = 1, pci->irq = 125
[    0.923749] alx 0000:3b:00.0 eth0: Qualcomm Atheros AR816x/AR817x Ethernet [20:47:47:f2:85:10]
[    0.924824] ahci 0000:00:17.0: AHCI 0001.0301 32 slots 1 ports 6 Gbps 0x2 impl RAID mode
[    0.924827] ahci 0000:00:17.0: flags: 64bit ncq sntf pm led clo only pio slum part ems deso sadm sds apst 
[    0.925353] scsi host0: ahci
[    0.925430] scsi host1: ahci
[    0.925463] ata1: DUMMY
[    0.925465] ata2: SATA max UDMA/133 abar m2048@0xdd133000 port 0xdd133180 irq 124
[    0.929435] [drm] Memory usable by graphics device = 4096M
[    0.929439] checking generic (70000000 7f0000) vs hw (70000000 10000000)
[    0.929440] fb: switching to inteldrmfb from EFI VGA
[    0.929457] Console: switching to colour dummy device 80x25
[    0.929532] [drm] Replacing VGA console driver
[    0.931070] MXM: GUID detected in BIOS
[    0.931094] ACPI Warning: \_SB_.PCI0.GFX0._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150619/nsarguments-95)
[    0.931134] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150619/nsarguments-95)
[    0.931171] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150619/nsarguments-95)
[    0.931305] pci 0000:01:00.0: optimus capabilities: enabled, status dynamic power, hda bios codec supported
[    0.931306] VGA switcheroo: detected Optimus DSM method \_SB_.PCI0.PEG0.PEGP handle
[    0.931332] nouveau 0000:01:00.0: enabling device (0006 -> 0007)
[    0.936935] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[    0.936936] [drm] Driver supports precise vblank timestamp query.
[    0.945729] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[    0.966966] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[    0.967200] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input7
[    0.967270] ACPI Exception: AE_NOT_FOUND, Evaluating _DOD (20150619/video-1157)
[    0.967273] ACPI: Video Device [PEGP] (multi-head: no  rom: yes  post: no)
[    0.967305] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:12/LNXVIDEO:01/input/input8
[    0.967348] [drm] Initialized i915 1.6.0 20150522 for 0000:00:02.0 on minor 0
[    0.968838] alx 0000:3b:00.0 enp59s0: renamed from eth0
[    0.968933] fbcon: inteldrmfb (fb0) is primary device
[    0.968977] nouveau  [  DEVICE][0000:01:00.0] BOOT0  : 0x124190a1
[    0.968978] nouveau  [  DEVICE][0000:01:00.0] Chipset: GM204 (NV124)
[    0.968979] nouveau  [  DEVICE][0000:01:00.0] Family : NV110
[    0.968984] Console: switching to colour frame buffer device 240x67
[    0.969004] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[    0.969005] i915 0000:00:02.0: registered panic notifier
[    1.105099] usb 1-4: new full-speed USB device number 2 using xhci_hcd
[    1.142714] nouveau  [   VBIOS][0000:01:00.0] using image from PROM
[    1.142831] nouveau  [   VBIOS][0000:01:00.0] BIT signature found
[    1.142833] nouveau  [   VBIOS][0000:01:00.0] version 84.04.79.00.0b
[    1.145837] nouveau  [ DEVINIT][0000:01:00.0] adaptor not initialised
[    1.178533] nouveau  [     PMC][0000:01:00.0] MSI interrupts enabled
[    1.178558] nouveau  [     PFB][0000:01:00.0] RAM type: GDDR5
[    1.178559] nouveau  [     PFB][0000:01:00.0] RAM size: 2048 MiB
[    1.178560] nouveau  [     PFB][0000:01:00.0]    ZCOMP: 0 tags
[    1.222765] nouveau  [  PGRAPH][0000:01:00.0] using external firmware
[    1.222775] nouveau 0000:01:00.0: Direct firmware load for nouveau/nv124_fuc409c failed with error -2
[    1.222798] nouveau 0000:01:00.0: Direct firmware load for nouveau/fuc409c failed with error -2
[    1.222799] nouveau E[  PGRAPH][0000:01:00.0] failed to load fuc409c
[    1.222869] vga_switcheroo: enabled
[    1.223248] [TTM] Zone  kernel: Available graphics memory: 6101076 kiB
[    1.223249] [TTM] Zone   dma32: Available graphics memory: 2097152 kiB
[    1.223249] [TTM] Initializing pool allocator
[    1.223252] [TTM] Initializing DMA pool allocator
[    1.223258] nouveau  [     DRM] VRAM: 2048 MiB
[    1.223259] nouveau  [     DRM] GART: 1048576 MiB
[    1.223261] nouveau  [     DRM] TMDS table version 2.0
[    1.223262] nouveau  [     DRM] DCB version 4.1
[    1.223264] nouveau  [     DRM] DCB outp 00: 02000f62 00020010
[    1.223265] nouveau  [     DRM] DCB outp 15: 01dffff8 00000000
[    1.223266] nouveau  [     DRM] DCB conn 00: 00010061
[    1.223268] nouveau  [     DRM] DCB conn 15: 00000f70
[    1.223269] nouveau W[     DRM] Pointer to flat panel table invalid
[    1.223900] nouveau W[     DRM] unknown connector type 70
[    1.223937] nouveau W[     DRM] failed to create encoder 1/8/0: -19
[    1.223939] nouveau W[     DRM] Unknown-1 has no encoders, removing
[    1.223957] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[    1.223957] [drm] Driver supports precise vblank timestamp query.
[    1.231370] nouveau E[   PFIFO][0000:01:00.0] unsupported engines 0x00000001
[    1.231452] nouveau E[     DRM] failed to create kernel channel, -22
[    1.234202] usb 1-4: config 1 interface 0 altsetting 0 has 2 endpoint descriptors, different from the interface descriptor's value: 1
[    1.235555] usb 1-4: New USB device found, idVendor=187c, idProduct=0528
[    1.235557] usb 1-4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    1.235559] usb 1-4: Product: AW1517
[    1.235560] usb 1-4: Manufacturer: Alienware
[    1.235561] usb 1-4: SerialNumber: 16.0
[    1.235824] usb 1-4: ep 0x81 - rounding interval to 64 microframes, ep desc says 80 microframes
[    1.239609] usbcore: registered new interface driver usbhid
[    1.239610] usbhid: USB HID core driver
[    1.241837] hid-generic 0003:187C:0528.0001: hiddev0,hidraw0: USB HID v1.01 Device [Alienware AW1517] on usb-0000:00:14.0-4/input0
[    1.245143] ata2: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    1.246551] ata2.00: ATA-8: HGST HTS721010A9E630, JB0OA3P0, max UDMA/133
[    1.246553] ata2.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.248248] ata2.00: configured for UDMA/133
[    1.248587] scsi 1:0:0:0: Direct-Access     ATA      HGST HTS721010A9 A3P0 PQ: 0 ANSI: 5
[    1.249145] sd 1:0:0:0: Attached scsi generic sg0 type 0
[    1.249183] sd 1:0:0:0: [sda] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    1.249185] sd 1:0:0:0: [sda] 4096-byte physical blocks
[    1.249707] sd 1:0:0:0: [sda] Write Protect is off
[    1.249709] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.249950] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.257676] [drm] Initialized nouveau 1.2.2 20120801 for 0000:01:00.0 on minor 1
[    1.300723] psmouse serio1: synaptics: queried max coordinates: x [..5668], y [..4756]
[    1.331364] psmouse serio1: synaptics: queried min coordinates: x [1274..], y [1098..]
[    1.359894]  sda: sda1 sda2 sda3
[    1.361003] sd 1:0:0:0: [sda] Attached SCSI disk
[    1.391628] psmouse serio1: synaptics: Touchpad model: 1, fw: 8.1, id: 0x1e2b1, caps: 0xd00123/0x840300/0x26c00/0x0, board id: 2417, fw id: 1365292
[    1.401400] usb 1-5: new full-speed USB device number 3 using xhci_hcd
[    1.429756] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input6
[    1.531080] usb 1-5: New USB device found, idVendor=0cf3, idProduct=e301
[    1.531083] usb 1-5: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.697757] usb 1-7: new high-speed USB device number 4 using xhci_hcd
[    1.741844] tsc: Refined TSC clocksource calibration: 2303.999 MHz
[    1.741847] clocksource: tsc: mask: 0xffffffffffffffff max_cycles: 0x2135f6faae8, max_idle_ns: 440795313647 ns
[    1.834823] usb 1-7: New USB device found, idVendor=1bcf, idProduct=2b8c
[    1.834825] usb 1-7: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.834827] usb 1-7: Product: Integrated_Webcam_HD
[    1.834829] usb 1-7: Manufacturer: SunplusIT Inc
[    2.743396] clocksource: Switched to clocksource tsc
[    2.779360] [drm] RC6 on
[    6.800087] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150619/nsarguments-95)
[    6.800697] ACPI: \_SB_.PCI0.PEG0.PEGP: failed to evaluate _DSM
[    6.800701] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150619/nsarguments-95)
[    7.766537] random: nonblocking pool is initialized
[    7.892895] EXT4-fs (sda2): mounted filesystem with ordered data mode. Opts: (null)
[    8.734802] systemd[1]: Failed to insert module 'kdbus': Function not implemented
[    8.842317] systemd[1]: systemd 225 running in system mode. (+PAM +AUDIT +SELINUX +IMA +APPARMOR +SMACK +SYSVINIT +UTMP +LIBCRYPTSETUP +GCRYPT +GNUTLS +ACL +XZ -LZ4 +SECCOMP +BLKID -ELFUTILS +KMOD -IDN)
[    8.842439] systemd[1]: Detected architecture x86-64.
[    8.857350] systemd[1]: Set hostname to <Alienware-15-R2>.
[    9.499261] systemd[1]: NetworkManager.service: Cannot add dependency job, ignoring: Unit NetworkManager.service is masked.
[    9.499832] systemd[1]: Set up automount Arbitrary Executable File Formats File System Automount Point.
[    9.499860] systemd[1]: Reached target Remote File Systems (Pre).
[    9.499886] systemd[1]: Created slice Root Slice.
[    9.499914] systemd[1]: Listening on Journal Socket (/dev/log).
[    9.499982] systemd[1]: Created slice System Slice.
[    9.500055] systemd[1]: Created slice system-systemd\x2dcryptsetup.slice.
[    9.500478] systemd[1]: Starting Increase datagram queue length...
[    9.500594] systemd[1]: Created slice User and Session Slice.
[    9.500607] systemd[1]: Reached target Slices.
[    9.500647] systemd[1]: Listening on udev Kernel Socket.
[    9.500689] systemd[1]: Listening on /dev/initctl Compatibility Named Pipe.
[    9.500721] systemd[1]: Listening on udev Control Socket.
[    9.500765] systemd[1]: Listening on Journal Socket.
[    9.512790] systemd[1]: Starting Load Kernel Modules...
[    9.513338] systemd[1]: Starting Create list of required static device nodes for the current kernel...
[    9.513845] systemd[1]: Starting Uncomplicated firewall...
[    9.514415] systemd[1]: Mounting Debug File System...
[    9.673506] systemd[1]: Starting udev Coldplug all Devices...
[    9.674045] systemd[1]: Mounting Huge Pages File System...
[    9.674139] systemd[1]: Created slice system-getty.slice.
[    9.674173] systemd[1]: Listening on fsck to fsckd communication Socket.
[    9.674259] systemd[1]: Listening on Journal Audit Socket.
[    9.674728] systemd[1]: Starting Setup Virtual Console...
[    9.674743] systemd[1]: Reached target User and Group Name Lookups.
[    9.674827] systemd[1]: Created slice system-systemd\x2dfsck.slice.
[    9.675369] systemd[1]: Started Braille Device Support.
[    9.675993] systemd[1]: Started Read required files in advance.
[    9.676125] systemd[1]: Started Forward Password Requests to Wall Directory Watch.
[    9.676564] systemd[1]: Mounting POSIX Message Queue File System...
[    9.677393] systemd[1]: Started Create list of required static device nodes for the current kernel.
[    9.677593] systemd[1]: Started Uncomplicated firewall.
[    9.679494] systemd[1]: Starting Create Static Device Nodes in /dev...
[    9.703602] systemd[1]: Started Setup Virtual Console.
[    9.745365] systemd[1]: Mounted Debug File System.
[    9.745431] systemd[1]: Mounted POSIX Message Queue File System.
[    9.745892] systemd[1]: Started Increase datagram queue length.
[    9.748676] systemd[1]: Listening on Syslog Socket.
[    9.749140] systemd[1]: Starting Journal Service...
[    9.749921] systemd[1]: Mounted Huge Pages File System.
[    9.786460] systemd[1]: Started udev Coldplug all Devices.
[   10.028209] lp: driver loaded but no devices found
[   10.030470] ppdev: user-space parallel port driver
[   10.255667] systemd[1]: Started Load Kernel Modules.
[   10.256171] systemd[1]: Mounting FUSE Control File System...
[   10.256737] systemd[1]: Starting Apply Kernel Variables...
[   10.258394] systemd[1]: Mounted FUSE Control File System.
[   10.265740] systemd[1]: Started Journal Service.
[   10.656184] EXT4-fs (sda2): re-mounted. Opts: errors=remount-ro
[   10.959624] tpm_crb MSFT0101:00: ioremap of the command buffer failed
[   10.959629] tpm_crb: probe of MSFT0101:00 failed with error -12
[   10.998908] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   11.064374] proc_thermal 0000:00:04.0: enabling device (0000 -> 0002)
[   11.094247] mei_me 0000:00:16.0: enabling device (0000 -> 0002)
[   11.171580] systemd-journald[277]: Received request to flush runtime journal from PID 1
[   11.529631] compat: module verification failed: signature and/or required key missing - tainting kernel
[   11.529763] Loading modules backported from Linux version next-20151120-0-ga78de01
[   11.529765] Backport generated by backports.git backports-20151120-0-g906a6b3
[   11.558982] media: Linux media interface: v0.10
[   11.726999] Linux video capture interface: v2.00
[   11.735688] AVX2 version of gcm_enc/dec engaged.
[   11.735690] AES CTR mode by8 optimization enabled
[   11.797203] input: Dell WMI hotkeys as /devices/virtual/input/input9
[   11.912273] Bluetooth: Core ver 2.20
[   11.912285] NET: Registered protocol family 31
[   11.912286] Bluetooth: HCI device and connection manager initialized
[   11.912289] Bluetooth: HCI socket layer initialized
[   11.912290] Bluetooth: L2CAP socket layer initialized
[   11.912293] Bluetooth: SCO socket layer initialized
[   11.982100] ath10k_pci 0000:3c:00.0: enabling device (0000 -> 0002)
[   11.983004] ath10k_pci 0000:3c:00.0: pci irq msi-x interrupts 8 irq_mode 0 reset_mode 0
[   12.065781] usbcore: registered new interface driver btusb
[   12.069206] uvcvideo: Found UVC 1.00 device Integrated_Webcam_HD (1bcf:2b8c)
[   12.076809] input: Integrated_Webcam_HD as /devices/pci0000:00/0000:00:14.0/usb1/1-7/1-7:1.0/input/input10
[   12.076888] usbcore: registered new interface driver uvcvideo
[   12.076890] USB Video Class driver (1.1.1)
[   12.233114] cfg80211: World regulatory domain updated:
[   12.233116] cfg80211:  DFS Master region: unset
[   12.233117] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
[   12.233119] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
[   12.233120] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
[   12.233121] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (N/A, 2000 mBm), (N/A)
[   12.233122] cfg80211:   (5170000 KHz - 5250000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (N/A)
[   12.233124] cfg80211:   (5250000 KHz - 5330000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (0 s)
[   12.233125] cfg80211:   (5490000 KHz - 5730000 KHz @ 160000 KHz), (N/A, 2000 mBm), (0 s)
[   12.233126] cfg80211:   (5735000 KHz - 5835000 KHz @ 80000 KHz), (N/A, 2000 mBm), (N/A)
[   12.233127] cfg80211:   (57240000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 0 mBm), (N/A)
[   12.325553] snd_hda_intel 0000:00:1f.3: enabling device (0000 -> 0002)
[   12.325684] snd_hda_intel 0000:00:1f.3: bound 0000:00:02.0 (ops i915_audio_component_bind_ops [i915])
[   12.375173] ath10k_pci 0000:3c:00.0: Direct firmware load for ath10k/cal-pci-0000:3c:00.0.bin failed with error -2
[   12.396136] ath10k_pci 0000:3c:00.0: Direct firmware load for ath10k/QCA6174/hw3.0/firmware-5.bin failed with error -2
[   12.396140] ath10k_pci 0000:3c:00.0: could not fetch firmware file 'ath10k/QCA6174/hw3.0/firmware-5.bin': -2
[   12.416020] intel_rapl: Found RAPL domain package
[   12.416023] intel_rapl: Found RAPL domain core
[   12.416024] intel_rapl: Found RAPL domain uncore
[   12.416025] intel_rapl: Found RAPL domain dram
[   12.527036] snd_hda_codec_ca0132 hdaudioC0D0: autoconfig for CA0132: line_outs=1 (0xb/0x0/0x0/0x0/0x0) type:speaker
[   12.527039] snd_hda_codec_ca0132 hdaudioC0D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   12.527040] snd_hda_codec_ca0132 hdaudioC0D0:    hp_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   12.527042] snd_hda_codec_ca0132 hdaudioC0D0:    mono: mono_out=0x0
[   12.527043] snd_hda_codec_ca0132 hdaudioC0D0:    inputs:
[   12.527044] snd_hda_codec_ca0132 hdaudioC0D0:      Mic=0x12
[   12.527046] snd_hda_codec_ca0132 hdaudioC0D0:      Line=0x11
[   12.604583] ath10k_pci 0000:3c:00.0: Direct firmware load for ath10k/QCA6174/hw3.0/board-2.bin failed with error -2
[   13.148247] ca0132 DOWNLOAD OK :-) DSP IS RUNNING.
[   13.405210] input: HDA Intel PCH Front Line Out as /devices/pci0000:00/0000:00:1f.3/sound/card0/input11
[   13.405382] input: HDA Intel PCH Line Out as /devices/pci0000:00/0000:00:1f.3/sound/card0/input12
[   13.407752] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1f.3/sound/card0/input13
[   13.407801] input: HDA Intel PCH HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:1f.3/sound/card0/input14
[   13.407839] input: HDA Intel PCH HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:1f.3/sound/card0/input15
[   14.013308] ca0132 DOWNLOAD OK :-) DSP IS RUNNING.
[   14.755381] ath10k_pci 0000:3c:00.0: qca6174 hw3.2 (0x05030000, 0x00340aff sub 1a56:1535) fw WLAN.RM.2.0-00180-QCARMSWPZ-1 fwapi 4 bdapi 1 htt-ver 3.26 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1 features wowlan,ignore-otp,no-4addr-pad
[   14.755387] ath10k_pci 0000:3c:00.0: debug 1 debugfs 1 tracing 0 dfs 0 testmode 0
[   14.875968] audit: type=1400 audit(1448813942.512:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/lightdm/lightdm-guest-session" pid=626 comm="apparmor_parser"
[   14.875974] audit: type=1400 audit(1448813942.512:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="chromium" pid=626 comm="apparmor_parser"
[   14.910410] audit: type=1400 audit(1448813942.544:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=626 comm="apparmor_parser"
[   14.910416] audit: type=1400 audit(1448813942.544:5): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=626 comm="apparmor_parser"
[   14.910420] audit: type=1400 audit(1448813942.544:6): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-helper" pid=626 comm="apparmor_parser"
[   14.910424] audit: type=1400 audit(1448813942.544:7): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=626 comm="apparmor_parser"
[   15.189667] audit: type=1400 audit(1448813942.820:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/evince" pid=626 comm="apparmor_parser"
[   15.189673] audit: type=1400 audit(1448813942.820:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="sanitized_helper" pid=626 comm="apparmor_parser"
[   15.189676] audit: type=1400 audit(1448813942.820:10): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/evince-previewer" pid=626 comm="apparmor_parser"
[   15.189680] audit: type=1400 audit(1448813942.820:11): apparmor="STATUS" operation="profile_load" profile="unconfined" name="sanitized_helper" pid=626 comm="apparmor_parser"
[   15.331647] Adding 12478972k swap on /dev/mapper/cryptswap1.  Priority:-1 extents:1 across:12478972k FS
[   16.812533] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150619/nsarguments-95)
[   16.813140] ACPI: \_SB_.PCI0.PEG0.PEGP: failed to evaluate _DSM
[   16.813144] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150619/nsarguments-95)
[   17.099319] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   17.099322] Bluetooth: BNEP filters: protocol multicast
[   17.099337] Bluetooth: BNEP socket layer initialized
[   17.757727] ath10k_pci 0000:3c:00.0: could not suspend target (-11)
[   17.829575] ath: EEPROM regdomain: 0x69
[   17.829578] ath: EEPROM indicates we should expect a direct regpair map
[   17.829580] ath: Country alpha2 being used: 00
[   17.829581] ath: Regpair used: 0x69
[   17.898921] cgroup: new mount options do not match the existing superblock, will be ignored
[   18.305190] ath10k_pci 0000:3c:00.0 wlp60s0: renamed from wlan0
[   26.356475] ath10k_pci 0000:3c:00.0: failed to enable dynamic BW: -11
[   27.990483] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150619/nsarguments-95)
[   27.991085] ACPI: \_SB_.PCI0.PEG0.PEGP: failed to evaluate _DSM
[   27.991089] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150619/nsarguments-95)
[   32.363973] ath10k_pci 0000:3c:00.0: could not suspend target (-11)
[   32.509021] IPv6: ADDRCONF(NETDEV_UP): enp59s0: link is not ready
[   32.509885] alx 0000:3b:00.0 enp59s0: NIC Up: 1 Gbps Full
[   32.510112] IPv6: ADDRCONF(NETDEV_CHANGE): enp59s0: link becomes ready
[   40.421997] ath10k_pci 0000:3c:00.0: failed to set rx-chainmask: -11, req 0x3
[   43.425761] ath10k_pci 0000:3c:00.0: failed to set arp ac override parameter: -11
[   49.433303] ath10k_pci 0000:3c:00.0: could not suspend target (-11)
[   52.772917] Bluetooth: RFCOMM TTY layer initialized
[   52.772928] Bluetooth: RFCOMM socket layer initialized
[   52.772931] Bluetooth: RFCOMM ver 1.11
[   54.755909] ath10k_pci 0000:3c:00.0: failed to enable dynamic BW: -11
[   58.865080] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150619/nsarguments-95)
[   58.865678] ACPI: \_SB_.PCI0.PEG0.PEGP: failed to evaluate _DSM
[   58.865682] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150619/nsarguments-95)
[   60.763380] ath10k_pci 0000:3c:00.0: could not suspend target (-11)
[   61.381443] IPv6: ADDRCONF(NETDEV_UP): enp59s0: link is not ready
[   61.382222] alx 0000:3b:00.0 enp59s0: NIC Up: 1 Gbps Full
[   61.382378] IPv6: ADDRCONF(NETDEV_CHANGE): enp59s0: link becomes ready
[   61.563098] IPv6: ADDRCONF(NETDEV_UP): enp59s0: link is not ready
[   61.563877] alx 0000:3b:00.0 enp59s0: NIC Up: 1 Gbps Full
[   61.564046] IPv6: ADDRCONF(NETDEV_CHANGE): enp59s0: link becomes ready
[   73.891828] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150619/nsarguments-95)
[   73.892431] ACPI: \_SB_.PCI0.PEG0.PEGP: failed to evaluate _DSM
[   73.892435] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150619/nsarguments-95)
[   89.082945] ath10k_pci 0000:3c:00.0: failed to enable dynamic BW: -11
[   95.161078] ath10k_pci 0000:3c:00.0: could not suspend target (-11)
[  101.316064] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150619/nsarguments-95)
[  101.316672] ACPI: \_SB_.PCI0.PEG0.PEGP: failed to evaluate _DSM
[  101.316677] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150619/nsarguments-95)
[ 2358.114262] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150619/nsarguments-95)
[ 2358.114877] ACPI: \_SB_.PCI0.PEG0.PEGP: failed to evaluate _DSM
[ 2358.114881] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150619/nsarguments-95)
[ 2866.750702] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150619/nsarguments-95)
[ 2866.751654] ACPI: \_SB_.PCI0.PEG0.PEGP: failed to evaluate _DSM
[ 2866.751664] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150619/nsarguments-95)
[ 3301.323667] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150619/nsarguments-95)
[ 3301.324281] ACPI: \_SB_.PCI0.PEG0.PEGP: failed to evaluate _DSM
[ 3301.324285] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150619/nsarguments-95)


```

Lines that stand out from dmesg
```
[   12.396140] ath10k_pci 0000:3c:00.0: could not fetch firmware file 'ath10k/QCA6174/hw3.0/firmware-5.bin': -2


```
```
[   10.959624] tpm_crb MSFT0101:00: ioremap of the command buffer failed


```
```
[    1.231370] nouveau E[   PFIFO][0000:01:00.0] unsupported engines 0x00000001
[    1.231452] nouveau E[     DRM] failed to create kernel channel, -22


```

Whatever else you need I will be happy to provide. I attempted to run the script in the "before posting" post, but I'm retarded. *c'est la vie*

---

### Post by jeremy31 on 2015-11-29
```
cd /lib/firmware/ath10k/QCA6174/hw3.0
wget https://github.com/FireWalkerX/ath10k-firmware/blob/7e56cbb94182a2fdab110cf5bfeded8fd1d44d30/QCA6174/hw3.0/board-2.bin
echo "options ath10k_core skip_otp=Y" | sudo tee /etc/modprobe.d/ath10k_core.conf
```

Reboot

---

### Post by wood3d on 2015-11-29
Thanks for hopping in on this with me!

So, I did as you said and still no wifi. 

rfkill list all didn't change

lshw -C network didn't change

dmesg

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 4.2.0-18-generic (buildd@lgw01-38) (gcc version 5.2.1 20151010 (Ubuntu 5.2.1-22ubuntu2) ) #22-Ubuntu SMP Fri Nov 6 18:25:50 UTC 2015 (Ubuntu 4.2.0-18.22-generic 4.2.3)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-4.2.0-18-generic.efi.signed root=UUID=1c5f30cd-4a80-45fd-acd9-80a1d5b0497b ro noprompt persistent quiet splash vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] x86/fpu: xstate_offset[2]: 0240, xstate_sizes[2]: 0100
[    0.000000] x86/fpu: xstate_offset[3]: 03c0, xstate_sizes[3]: 0040
[    0.000000] x86/fpu: xstate_offset[4]: 0400, xstate_sizes[4]: 0040
[    0.000000] x86/fpu: Supporting XSAVE feature 0x01: 'x87 floating point registers'
[    0.000000] x86/fpu: Supporting XSAVE feature 0x02: 'SSE registers'
[    0.000000] x86/fpu: Supporting XSAVE feature 0x04: 'AVX registers'
[    0.000000] x86/fpu: Supporting XSAVE feature 0x08: 'MPX bounds registers'
[    0.000000] x86/fpu: Supporting XSAVE feature 0x10: 'MPX CSR'
[    0.000000] x86/fpu: Enabled xstate features 0x1f, context size is 0x440 bytes, using 'standard' format.
[    0.000000] x86/fpu: Using 'eager' FPU context switches.
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x0000000000057fff] usable
[    0.000000] BIOS-e820: [mem 0x0000000000058000-0x0000000000058fff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000059000-0x000000000009dfff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009e000-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x000000003130bfff] usable
[    0.000000] BIOS-e820: [mem 0x000000003130c000-0x000000003130cfff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x000000003130d000-0x0000000031336fff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000031337000-0x000000003138efff] usable
[    0.000000] BIOS-e820: [mem 0x000000003138f000-0x00000000318e4fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000318e5000-0x00000000361abfff] usable
[    0.000000] BIOS-e820: [mem 0x00000000361ac000-0x0000000037191fff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000037192000-0x00000000371d2fff] ACPI data
[    0.000000] BIOS-e820: [mem 0x00000000371d3000-0x0000000037b4efff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x0000000037b4f000-0x0000000037ffdfff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000037ffe000-0x0000000037ffefff] usable
[    0.000000] BIOS-e820: [mem 0x0000000038000000-0x00000000380fffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000e0000000-0x00000000efffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fe000000-0x00000000fe010fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ff000000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x00000003c3ffffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] e820: update [mem 0x22aa0018-0x22abd657] usable ==> usable
[    0.000000] e820: update [mem 0x22a8f018-0x22a9f057] usable ==> usable
[    0.000000] e820: update [mem 0x22a71018-0x22a8ea57] usable ==> usable
[    0.000000] extended physical RAM map:
[    0.000000] reserve setup_data: [mem 0x0000000000000000-0x0000000000057fff] usable
[    0.000000] reserve setup_data: [mem 0x0000000000058000-0x0000000000058fff] reserved
[    0.000000] reserve setup_data: [mem 0x0000000000059000-0x000000000009dfff] usable
[    0.000000] reserve setup_data: [mem 0x000000000009e000-0x000000000009ffff] reserved
[    0.000000] reserve setup_data: [mem 0x0000000000100000-0x0000000022a71017] usable
[    0.000000] reserve setup_data: [mem 0x0000000022a71018-0x0000000022a8ea57] usable
[    0.000000] reserve setup_data: [mem 0x0000000022a8ea58-0x0000000022a8f017] usable
[    0.000000] reserve setup_data: [mem 0x0000000022a8f018-0x0000000022a9f057] usable
[    0.000000] reserve setup_data: [mem 0x0000000022a9f058-0x0000000022aa0017] usable
[    0.000000] reserve setup_data: [mem 0x0000000022aa0018-0x0000000022abd657] usable
[    0.000000] reserve setup_data: [mem 0x0000000022abd658-0x000000003130bfff] usable
[    0.000000] reserve setup_data: [mem 0x000000003130c000-0x000000003130cfff] ACPI NVS
[    0.000000] reserve setup_data: [mem 0x000000003130d000-0x0000000031336fff] reserved
[    0.000000] reserve setup_data: [mem 0x0000000031337000-0x000000003138efff] usable
[    0.000000] reserve setup_data: [mem 0x000000003138f000-0x00000000318e4fff] reserved
[    0.000000] reserve setup_data: [mem 0x00000000318e5000-0x00000000361abfff] usable
[    0.000000] reserve setup_data: [mem 0x00000000361ac000-0x0000000037191fff] reserved
[    0.000000] reserve setup_data: [mem 0x0000000037192000-0x00000000371d2fff] ACPI data
[    0.000000] reserve setup_data: [mem 0x00000000371d3000-0x0000000037b4efff] ACPI NVS
[    0.000000] reserve setup_data: [mem 0x0000000037b4f000-0x0000000037ffdfff] reserved
[    0.000000] reserve setup_data: [mem 0x0000000037ffe000-0x0000000037ffefff] usable
[    0.000000] reserve setup_data: [mem 0x0000000038000000-0x00000000380fffff] reserved
[    0.000000] reserve setup_data: [mem 0x00000000e0000000-0x00000000efffffff] reserved
[    0.000000] reserve setup_data: [mem 0x00000000fe000000-0x00000000fe010fff] reserved
[    0.000000] reserve setup_data: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
[    0.000000] reserve setup_data: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
[    0.000000] reserve setup_data: [mem 0x00000000ff000000-0x00000000ffffffff] reserved
[    0.000000] reserve setup_data: [mem 0x0000000100000000-0x00000003c3ffffff] usable
[    0.000000] efi: EFI v2.40 by American Megatrends
[    0.000000] efi:  ESRT=0x37f7f018  ACPI=0x3719f000  ACPI 2.0=0x3719f000  SMBIOS=0x37ec7000 
[    0.000000] esrt: Reserving ESRT space from 0x0000000037f7f018 to 0x0000000037f7f050.
[    0.000000] SMBIOS 2.8 present.
[    0.000000] DMI: Alienware Alienware 15 R2/Alienware 15 R2, BIOS 1.1.5 09/18/2015
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] e820: last_pfn = 0x3c4000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: write-back
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0080000000 mask 7F80000000 uncachable
[    0.000000]   1 base 0040000000 mask 7FC0000000 uncachable
[    0.000000]   2 base 003C000000 mask 7FFC000000 uncachable
[    0.000000]   3 base 003A000000 mask 7FFE000000 uncachable
[    0.000000]   4 base 0039000000 mask 7FFF000000 uncachable
[    0.000000]   5 base 0038800000 mask 7FFF800000 uncachable
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000]   8 disabled
[    0.000000]   9 disabled
[    0.000000] x86/PAT: Configuration [0-7]: WB  WC  UC- UC  WB  WC  UC- WT  
[    0.000000] e820: last_pfn = 0x37fff max_arch_pfn = 0x400000000
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] Base memory trampoline at [ffff880000098000] 98000 size 24576
[    0.000000] Using GB pages for direct mapping
[    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
[    0.000000]  [mem 0x00000000-0x000fffff] page 4k
[    0.000000] BRK [0x01ff0000, 0x01ff0fff] PGTABLE
[    0.000000] BRK [0x01ff1000, 0x01ff1fff] PGTABLE
[    0.000000] BRK [0x01ff2000, 0x01ff2fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x3c3e00000-0x3c3ffffff]
[    0.000000]  [mem 0x3c3e00000-0x3c3ffffff] page 2M
[    0.000000] BRK [0x01ff3000, 0x01ff3fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x3c0000000-0x3c3dfffff]
[    0.000000]  [mem 0x3c0000000-0x3c3dfffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x3a0000000-0x3bfffffff]
[    0.000000]  [mem 0x3a0000000-0x3bfffffff] page 1G
[    0.000000] init_memory_mapping: [mem 0x00100000-0x3130bfff]
[    0.000000]  [mem 0x00100000-0x001fffff] page 4k
[    0.000000]  [mem 0x00200000-0x311fffff] page 2M
[    0.000000]  [mem 0x31200000-0x3130bfff] page 4k
[    0.000000] init_memory_mapping: [mem 0x31337000-0x3138efff]
[    0.000000]  [mem 0x31337000-0x3138efff] page 4k
[    0.000000] init_memory_mapping: [mem 0x318e5000-0x361abfff]
[    0.000000]  [mem 0x318e5000-0x319fffff] page 4k
[    0.000000]  [mem 0x31a00000-0x35ffffff] page 2M
[    0.000000]  [mem 0x36000000-0x361abfff] page 4k
[    0.000000] BRK [0x01ff4000, 0x01ff4fff] PGTABLE
[    0.000000] BRK [0x01ff5000, 0x01ff5fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x37ffe000-0x37ffefff]
[    0.000000]  [mem 0x37ffe000-0x37ffefff] page 4k
[    0.000000] init_memory_mapping: [mem 0x100000000-0x39fffffff]
[    0.000000]  [mem 0x100000000-0x39fffffff] page 1G
[    0.000000] RAMDISK: [mem 0x22abe000-0x24a53fff]
[    0.000000] ACPI: Early table checksum verification disabled
[    0.000000] ACPI: RSDP 0x000000003719F000 000024 (v02 ALWARE)
[    0.000000] ACPI: XSDT 0x000000003719F0B8 0000F4 (v01 ALWARE ALIENWRE 01072009 AMI  00010013)
[    0.000000] ACPI: FACP 0x00000000371C2408 00010C (v05 ALWARE ALIENWRE 01072009 AMI  00010013)
[    0.000000] ACPI: DSDT 0x000000003719F240 0231C5 (v02 ALWARE ALIENWRE 01072009 INTL 20120913)
[    0.000000] ACPI: FACS 0x0000000037B4BF80 000040
[    0.000000] ACPI: APIC 0x00000000371C2518 000084 (v03 ALWARE ALIENWRE 01072009 AMI  00010013)
[    0.000000] ACPI: FPDT 0x00000000371C25A0 000044 (v01 ALWARE ALIENWRE 01072009 AMI  00010013)
[    0.000000] ACPI: FIDT 0x00000000371C25E8 00009C (v01 ALWARE ALIENWRE 01072009 AMI  00010013)
[    0.000000] ACPI: MCFG 0x00000000371C2688 00003C (v01 ALWARE ALIENWRE 01072009 MSFT 00000097)
[    0.000000] ACPI: HPET 0x00000000371C26C8 000038 (v01 ALWARE ALIENWRE 01072009 AMI. 0005000B)
[    0.000000] ACPI: SSDT 0x00000000371C2700 0004B9 (v01 SataRe SataTabl 00001000 INTL 20120913)
[    0.000000] ACPI: LPIT 0x00000000371C2BC0 000094 (v01 INTEL  SKL      00000000 MSFT 0000005F)
[    0.000000] ACPI: SSDT 0x00000000371C2C58 000248 (v02 INTEL  sensrhub 00000000 INTL 20120913)
[    0.000000] ACPI: SSDT 0x00000000371C2EA0 002BAE (v02 INTEL  PtidDevc 00001000 INTL 20120913)
[    0.000000] ACPI: DBGP 0x00000000371C5A50 000034 (v01 INTEL           00000000 MSFT 0000005F)
[    0.000000] ACPI: DBG2 0x00000000371C5A88 000054 (v00 INTEL           00000000 MSFT 0000005F)
[    0.000000] ACPI: SSDT 0x00000000371C5AE0 00069D (v02 INTEL  xh_rvp10 00000000 INTL 20120913)
[    0.000000] ACPI: SSDT 0x00000000371C6180 003489 (v02 DptfTa DptfTabl 00001000 INTL 20120913)
[    0.000000] ACPI: TPM2 0x00000000371C9610 000034 (v03        Tpm2Tabl 00000001 AMI  00000000)
[    0.000000] ACPI: SSDT 0x00000000371C9648 00080B (v01 AMITCG _SynTCG_ 00000001 INTL 20120913)
[    0.000000] ACPI: SSDT 0x00000000371C9E58 005580 (v02 SaSsdt SaSsdt   00003000 INTL 20120913)
[    0.000000] ACPI: UEFI 0x00000000371CF3D8 000042 (v01                 00000000      00000000)
[    0.000000] ACPI: MSDM 0x00000000371CF420 000055 (v03 ALWARE ALIENWRE 01072009 AMI  00010013)
[    0.000000] ACPI: SSDT 0x00000000371CF478 000E58 (v02 CpuRef CpuSsdt  00003000 INTL 20120913)
[    0.000000] ACPI: BGRT 0x00000000371D02D0 000038 (v01 ALWARE ALIENWRE 01072009 AMI  00010013)
[    0.000000] ACPI: SSDT 0x00000000371D0308 0000CE (v02 SgRef  SgPeg    00001000 INTL 20120913)
[    0.000000] ACPI: DMAR 0x00000000371D03D8 0000A8 (v01 INTEL  SKL      00000001 INTL 00000001)
[    0.000000] ACPI: UEFI 0x00000000371D0480 00063A (v01 INTEL  RstSataE 00000000 ??   00000000)
[    0.000000] ACPI: UEFI 0x00000000371D0AC0 00005C (v01 INTEL  RstSataV 00000000 ??   00000000)
[    0.000000] ACPI: SSDT 0x00000000371D0B20 00198C (v01 OptRef OptTabl  00001000 INTL 20120913)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x00000003c3ffffff]
[    0.000000] NODE_DATA(0) allocated [mem 0x3c3ff9000-0x3c3ffdfff]
[    0.000000]  [ffffea0000000000-ffffea000f1fffff] PMD -> [ffff8803b7600000-ffff8803c35fffff] on node 0
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x0000000000001000-0x0000000000ffffff]
[    0.000000]   DMA32    [mem 0x0000000001000000-0x00000000ffffffff]
[    0.000000]   Normal   [mem 0x0000000100000000-0x00000003c3ffffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x0000000000001000-0x0000000000057fff]
[    0.000000]   node   0: [mem 0x0000000000059000-0x000000000009dfff]
[    0.000000]   node   0: [mem 0x0000000000100000-0x000000003130bfff]
[    0.000000]   node   0: [mem 0x0000000031337000-0x000000003138efff]
[    0.000000]   node   0: [mem 0x00000000318e5000-0x00000000361abfff]
[    0.000000]   node   0: [mem 0x0000000037ffe000-0x0000000037ffefff]
[    0.000000]   node   0: [mem 0x0000000100000000-0x00000003c3ffffff]
[    0.000000] Initmem setup node 0 [mem 0x0000000000001000-0x00000003c3ffffff]
[    0.000000] On node 0 totalpages: 3120072
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 21 pages reserved
[    0.000000]   DMA zone: 3996 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 3377 pages used for memmap
[    0.000000]   DMA32 zone: 216108 pages, LIFO batch:31
[    0.000000]   Normal zone: 45312 pages used for memmap
[    0.000000]   Normal zone: 2899968 pages, LIFO batch:31
[    0.000000] tboot: non-0 tboot_addr but it is not of type E820_RESERVED
[    0.000000] Reserving Intel graphics stolen memory at 0x39000000-0x3affffff
[    0.000000] ACPI: PM-Timer IO Port: 0x1808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x04] high edge lint[0x1])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-119
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a701 base: 0xfed00000
[    0.000000] smpboot: Allowing 4 CPUs, 0 hotplug CPUs
[    0.000000] PM: Registered nosave memory: [mem 0x00000000-0x00000fff]
[    0.000000] PM: Registered nosave memory: [mem 0x00058000-0x00058fff]
[    0.000000] PM: Registered nosave memory: [mem 0x0009e000-0x0009ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000fffff]
[    0.000000] PM: Registered nosave memory: [mem 0x22a71000-0x22a71fff]
[    0.000000] PM: Registered nosave memory: [mem 0x22a8e000-0x22a8efff]
[    0.000000] PM: Registered nosave memory: [mem 0x22a8f000-0x22a8ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x22a9f000-0x22a9ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x22aa0000-0x22aa0fff]
[    0.000000] PM: Registered nosave memory: [mem 0x22abd000-0x22abdfff]
[    0.000000] PM: Registered nosave memory: [mem 0x3130c000-0x3130cfff]
[    0.000000] PM: Registered nosave memory: [mem 0x3130d000-0x31336fff]
[    0.000000] PM: Registered nosave memory: [mem 0x3138f000-0x318e4fff]
[    0.000000] PM: Registered nosave memory: [mem 0x361ac000-0x37191fff]
[    0.000000] PM: Registered nosave memory: [mem 0x37192000-0x371d2fff]
[    0.000000] PM: Registered nosave memory: [mem 0x371d3000-0x37b4efff]
[    0.000000] PM: Registered nosave memory: [mem 0x37b4f000-0x37ffdfff]
[    0.000000] PM: Registered nosave memory: [mem 0x37fff000-0x37ffffff]
[    0.000000] PM: Registered nosave memory: [mem 0x38000000-0x380fffff]
[    0.000000] PM: Registered nosave memory: [mem 0x38100000-0x38ffffff]
[    0.000000] PM: Registered nosave memory: [mem 0x39000000-0x3affffff]
[    0.000000] PM: Registered nosave memory: [mem 0x3b000000-0xdfffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xe0000000-0xefffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xf0000000-0xfdffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfe000000-0xfe010fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfe011000-0xfebfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xfec00fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec01000-0xfedfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfee00000-0xfee00fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfee01000-0xfeffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xff000000-0xffffffff]
[    0.000000] e820: [mem 0x3b000000-0xdfffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] clocksource: refined-jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645519600211568 ns
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 33 pages/cpu @ffff8803c3c00000 s96728 r8192 d30248 u524288
[    0.000000] pcpu-alloc: s96728 r8192 d30248 u524288 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 3071298
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.2.0-18-generic.efi.signed root=UUID=1c5f30cd-4a80-45fd-acd9-80a1d5b0497b ro noprompt persistent quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 12092316K/12480288K available (8146K kernel code, 1237K rwdata, 3800K rodata, 1460K init, 1292K bss, 387972K reserved, 0K cma-reserved)
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     Build-time adjustment of leaf fanout to 64.
[    0.000000]     RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=4.
[    0.000000] RCU: Adjusting geometry for rcu_fanout_leaf=64, nr_cpu_ids=4
[    0.000000] NR_IRQS:16640 nr_irqs:1024 16
[    0.000000]     Offload RCU callbacks from all CPUs
[    0.000000]     Offload RCU callbacks from CPUs: 0-3.
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] clocksource: hpet: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 79635855245 ns
[    0.000000] hpet clockevent registered
[    0.000000] tsc: PIT calibration matches HPET. 1 loops
[    0.000000] tsc: Detected 2302.980 MHz processor
[    0.000024] Calibrating delay loop (skipped), value calculated using timer frequency.. 4605.96 BogoMIPS (lpj=9211920)
[    0.000026] pid_max: default: 32768 minimum: 301
[    0.000030] ACPI: Core revision 20150619
[    0.023830] ACPI Error: [\_SB_.PCI0.XHC_.RHUB.HS11] Namespace lookup failure, AE_NOT_FOUND (20150619/dswload-210)
[    0.023834] ACPI Exception: AE_NOT_FOUND, During name lookup/catalog (20150619/psobject-224)
[    0.035721] ACPI: All ACPI Tables successfully acquired
[    0.037471] Security Framework initialized
[    0.037477] AppArmor: AppArmor initialized
[    0.037478] Yama: becoming mindful.
[    0.038433] Dentry cache hash table entries: 2097152 (order: 12, 16777216 bytes)
[    0.040936] Inode-cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.042072] Mount-cache hash table entries: 32768 (order: 6, 262144 bytes)
[    0.042086] Mountpoint-cache hash table entries: 32768 (order: 6, 262144 bytes)
[    0.042249] Initializing cgroup subsys blkio
[    0.042251] Initializing cgroup subsys memory
[    0.042256] Initializing cgroup subsys devices
[    0.042258] Initializing cgroup subsys freezer
[    0.042259] Initializing cgroup subsys net_cls
[    0.042260] Initializing cgroup subsys perf_event
[    0.042262] Initializing cgroup subsys net_prio
[    0.042263] Initializing cgroup subsys hugetlb
[    0.042283] CPU: Physical Processor ID: 0
[    0.042283] CPU: Processor Core ID: 0
[    0.042287] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
[    0.042287] ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
[    0.043337] mce: CPU supports 10 MCE banks
[    0.043352] CPU0: Thermal monitoring enabled (TM1)
[    0.043360] process: using mwait in idle threads
[    0.043363] Last level iTLB entries: 4KB 128, 2MB 8, 4MB 8
[    0.043363] Last level dTLB entries: 4KB 64, 2MB 0, 4MB 0, 1GB 4
[    0.043644] Freeing SMP alternatives memory: 28K (ffffffff81ea4000 - ffffffff81eab000)
[    0.046961] ftrace: allocating 30905 entries in 121 pages
[    0.057528] DMAR: Host address width 39
[    0.057530] DMAR: DRHD base: 0x000000fed90000 flags: 0x0
[    0.057536] DMAR: dmar0: reg_base_addr fed90000 ver 1:0 cap 1c0000c40660462 ecap 7e3ff0501e
[    0.057537] DMAR: DRHD base: 0x000000fed91000 flags: 0x1
[    0.057541] DMAR: dmar1: reg_base_addr fed91000 ver 1:0 cap d2008c40660462 ecap f050da
[    0.057542] DMAR: RMRR base: 0x000000370e4000 end: 0x00000037103fff
[    0.057543] DMAR: RMRR base: 0x00000038800000 end: 0x0000003affffff
[    0.057544] DMAR-IR: IOAPIC id 2 under DRHD base  0xfed91000 IOMMU 1
[    0.057545] DMAR-IR: HPET id 0 under DRHD base 0xfed91000
[    0.057546] DMAR-IR: x2apic is disabled because BIOS sets x2apic opt out bit.
[    0.057547] DMAR-IR: Use 'intremap=no_x2apic_optout' to override the BIOS setting.
[    0.058940] DMAR-IR: Enabled IRQ remapping in xapic mode
[    0.058941] x2apic: IRQ remapping doesn't support X2APIC mode
[    0.062854] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.102577] TSC deadline timer enabled
[    0.102582] smpboot: CPU0: Intel(R) Core(TM) i5-6300HQ CPU @ 2.30GHz (fam: 06, model: 5e, stepping: 03)
[    0.102601] Performance Events: PEBS fmt3+, 32-deep LBR, Skylake events, full-width counters, Intel PMU driver.
[    0.102625] ... version:                4
[    0.102625] ... bit width:              48
[    0.102626] ... generic registers:      8
[    0.102627] ... value mask:             0000ffffffffffff
[    0.102627] ... max period:             0000ffffffffffff
[    0.102628] ... fixed-purpose events:   3
[    0.102628] ... event mask:             00000007000000ff
[    0.103259] x86: Booting SMP configuration:
[    0.103260] .... node  #0, CPUs:      #1
[    0.107650] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.107706]  #2 #3
[    0.116228] x86: Booted up 1 node, 4 CPUs
[    0.116230] smpboot: Total of 4 processors activated (18423.84 BogoMIPS)
[    0.119281] devtmpfs: initialized
[    0.121350] evm: security.selinux
[    0.121351] evm: security.SMACK64
[    0.121352] evm: security.SMACK64EXEC
[    0.121353] evm: security.SMACK64TRANSMUTE
[    0.121353] evm: security.SMACK64MMAP
[    0.121354] evm: security.ima
[    0.121355] evm: security.capability
[    0.121396] PM: Registering ACPI NVS region [mem 0x3130c000-0x3130cfff] (4096 bytes)
[    0.121397] PM: Registering ACPI NVS region [mem 0x371d3000-0x37b4efff] (9945088 bytes)
[    0.121533] clocksource: jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645041785100000 ns
[    0.121591] pinctrl core: initialized pinctrl subsystem
[    0.121734] RTC time: 19:37:48, date: 11/29/15
[    0.121823] NET: Registered protocol family 16
[    0.127627] cpuidle: using governor ladder
[    0.131651] cpuidle: using governor menu
[    0.131757] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.131759] ACPI: bus type PCI registered
[    0.131761] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.131828] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.131831] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    0.131840] PCI: Using configuration type 1 for base access
[    0.139940] ACPI: Added _OSI(Module Device)
[    0.139942] ACPI: Added _OSI(Processor Device)
[    0.139943] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.139944] ACPI: Added _OSI(Processor Aggregator Device)
[    0.147758] ACPI: Executed 21 blocks of module-level executable AML code
[    0.154611] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.158741] ACPI: Dynamic OEM Table Load:
[    0.158747] ACPI: SSDT 0xFFFF8803B4D83400 00037F (v02 PmRef  Cpu0Cst  00003001 INTL 20120913)
[    0.159600] ACPI: Dynamic OEM Table Load:
[    0.159604] ACPI: SSDT 0xFFFF8803B53DA800 000579 (v02 PmRef  Cpu0Ist  00003000 INTL 20120913)
[    0.161429] ACPI: Dynamic OEM Table Load:
[    0.161434] ACPI: SSDT 0xFFFF8803B53DB000 0005AA (v02 PmRef  ApIst    00003000 INTL 20120913)
[    0.162420] ACPI: Dynamic OEM Table Load:
[    0.162424] ACPI: SSDT 0xFFFF8803B4DA3C00 000119 (v02 PmRef  ApCst    00003000 INTL 20120913)
[    0.164968] ACPI : EC: EC started
[    0.165302] ACPI: Interpreter enabled
[    0.165310] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20150619/hwxface-580)
[    0.165317] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20150619/hwxface-580)
[    0.165335] ACPI: (supports S0 S3 S4 S5)
[    0.165336] ACPI: Using IOAPIC for interrupt routing
[    0.165365] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.167113] ACPI: Power Resource [PG00] (on)
[    0.184543] ACPI: Power Resource [PG01] (on)
[    0.184915] ACPI: Power Resource [PG02] (on)
[    0.185486] ACPI: Power Resource [WRST] (off)
[    0.185795] ACPI: Power Resource [WRST] (off)
[    0.186103] ACPI: Power Resource [WRST] (off)
[    0.186409] ACPI: Power Resource [WRST] (off)
[    0.186716] ACPI: Power Resource [WRST] (off)
[    0.187018] ACPI: Power Resource [WRST] (off)
[    0.187328] ACPI: Power Resource [WRST] (off)
[    0.187642] ACPI: Power Resource [WRST] (off)
[    0.187957] ACPI: Power Resource [WRST] (off)
[    0.188270] ACPI: Power Resource [WRST] (off)
[    0.188620] ACPI: Power Resource [WRST] (off)
[    0.188931] ACPI: Power Resource [WRST] (off)
[    0.189239] ACPI: Power Resource [WRST] (off)
[    0.189545] ACPI: Power Resource [WRST] (off)
[    0.189852] ACPI: Power Resource [WRST] (off)
[    0.190159] ACPI: Power Resource [WRST] (off)
[    0.190456] ACPI: Power Resource [WRST] (off)
[    0.190719] ACPI: Power Resource [WRST] (off)
[    0.190982] ACPI: Power Resource [WRST] (off)
[    0.191246] ACPI: Power Resource [WRST] (off)
[    0.205018] ACPI Error: No object attached to node [_ADR] ffff8803b71104d8 (20150619/exresnte-128)
[    0.205021] ACPI Error: Method execution failed [\_SB_.PCI0.XHC_.RHUB.HS07.WCAM._ADR] (Node ffff8803b71104d8), AE_AML_NO_OPERAND (20150619/uteval-103)
[    0.212394] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-fe])
[    0.212401] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    0.212430] \_SB_.PCI0:_OSC invalid UUID
[    0.212431] _OSC request data:1 1f 0 
[    0.212434] acpi PNP0A08:00: _OSC failed (AE_ERROR); disabling ASPM
[    0.212914] PCI host bridge to bus 0000:00
[    0.212917] pci_bus 0000:00: root bus resource [bus 00-fe]
[    0.212919] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7 window]
[    0.212920] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff window]
[    0.212922] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff window]
[    0.212923] pci_bus 0000:00: root bus resource [mem 0x000c0000-0x000c3fff window]
[    0.212924] pci_bus 0000:00: root bus resource [mem 0x000c4000-0x000c7fff window]
[    0.212926] pci_bus 0000:00: root bus resource [mem 0x000c8000-0x000cbfff window]
[    0.212927] pci_bus 0000:00: root bus resource [mem 0x000cc000-0x000cffff window]
[    0.212928] pci_bus 0000:00: root bus resource [mem 0x000d0000-0x000d3fff window]
[    0.212929] pci_bus 0000:00: root bus resource [mem 0x000d4000-0x000d7fff window]
[    0.212931] pci_bus 0000:00: root bus resource [mem 0x000d8000-0x000dbfff window]
[    0.212932] pci_bus 0000:00: root bus resource [mem 0x000dc000-0x000dffff window]
[    0.212933] pci_bus 0000:00: root bus resource [mem 0x000e0000-0x000e3fff window]
[    0.212934] pci_bus 0000:00: root bus resource [mem 0x000e4000-0x000e7fff window]
[    0.212936] pci_bus 0000:00: root bus resource [mem 0x000e8000-0x000ebfff window]
[    0.212937] pci_bus 0000:00: root bus resource [mem 0x000ec000-0x000effff window]
[    0.212938] pci_bus 0000:00: root bus resource [mem 0x3b000000-0xdfffffff window]
[    0.212940] pci_bus 0000:00: root bus resource [mem 0xfd000000-0xfe7fffff window]
[    0.212947] pci 0000:00:00.0: [8086:1910] type 00 class 0x060000
[    0.213246] pci 0000:00:01.0: [8086:1901] type 01 class 0x060400
[    0.213282] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.213397] pci 0000:00:01.0: System wakeup disabled by ACPI
[    0.213452] pci 0000:00:02.0: [8086:191b] type 00 class 0x030000
[    0.213466] pci 0000:00:02.0: reg 0x10: [mem 0xdb000000-0xdbffffff 64bit]
[    0.213472] pci 0000:00:02.0: reg 0x18: [mem 0x70000000-0x7fffffff 64bit pref]
[    0.213476] pci 0000:00:02.0: reg 0x20: [io  0xf000-0xf03f]
[    0.213596] pci 0000:00:04.0: [8086:1903] type 00 class 0x118000
[    0.213610] pci 0000:00:04.0: reg 0x10: [mem 0xdd120000-0xdd127fff 64bit]
[    0.213792] pci 0000:00:14.0: [8086:a12f] type 00 class 0x0c0330
[    0.213818] pci 0000:00:14.0: reg 0x10: [mem 0xdd110000-0xdd11ffff 64bit]
[    0.213869] pci 0000:00:14.0: PME# supported from D3hot D3cold
[    0.213972] pci 0000:00:14.0: System wakeup disabled by ACPI
[    0.214008] pci 0000:00:14.2: [8086:a131] type 00 class 0x118000
[    0.214034] pci 0000:00:14.2: reg 0x10: [mem 0xdd136000-0xdd136fff 64bit]
[    0.214196] pci 0000:00:16.0: [8086:a13a] type 00 class 0x078000
[    0.214248] pci 0000:00:16.0: reg 0x10: [mem 0xdd135000-0xdd135fff 64bit]
[    0.214333] pci 0000:00:16.0: PME# supported from D3hot
[    0.214475] pci 0000:00:17.0: [8086:282a] type 00 class 0x010400
[    0.214497] pci 0000:00:17.0: reg 0x10: [mem 0xdd130000-0xdd131fff]
[    0.214504] pci 0000:00:17.0: reg 0x14: [mem 0xdd134000-0xdd1340ff]
[    0.214511] pci 0000:00:17.0: reg 0x18: [io  0xf090-0xf097]
[    0.214518] pci 0000:00:17.0: reg 0x1c: [io  0xf080-0xf083]
[    0.214525] pci 0000:00:17.0: reg 0x20: [io  0xf060-0xf07f]
[    0.214532] pci 0000:00:17.0: reg 0x24: [mem 0xdd133000-0xdd1337ff]
[    0.214558] pci 0000:00:17.0: PME# supported from D3hot
[    0.214688] pci 0000:00:1c.0: [8086:a110] type 01 class 0x060400
[    0.214747] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.214855] pci 0000:00:1c.0: System wakeup disabled by ACPI
[    0.214897] pci 0000:00:1c.4: [8086:a114] type 01 class 0x060400
[    0.214949] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.215054] pci 0000:00:1c.4: System wakeup disabled by ACPI
[    0.215086] pci 0000:00:1c.5: [8086:a115] type 01 class 0x060400
[    0.215137] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    0.215242] pci 0000:00:1c.5: System wakeup disabled by ACPI
[    0.215274] pci 0000:00:1c.6: [8086:a116] type 01 class 0x060400
[    0.215327] pci 0000:00:1c.6: PME# supported from D0 D3hot D3cold
[    0.215433] pci 0000:00:1c.6: System wakeup disabled by ACPI
[    0.215469] pci 0000:00:1f.0: [8086:a14e] type 00 class 0x060100
[    0.215661] pci 0000:00:1f.2: [8086:a121] type 00 class 0x058000
[    0.215672] pci 0000:00:1f.2: reg 0x10: [mem 0xdd12c000-0xdd12ffff]
[    0.215804] pci 0000:00:1f.3: [8086:a170] type 00 class 0x040300
[    0.215835] pci 0000:00:1f.3: reg 0x10: [mem 0xdd128000-0xdd12bfff 64bit]
[    0.215859] pci 0000:00:1f.3: reg 0x20: [mem 0xdd100000-0xdd10ffff 64bit]
[    0.215886] pci 0000:00:1f.3: PME# supported from D3hot D3cold
[    0.216012] pci 0000:00:1f.3: System wakeup disabled by ACPI
[    0.216046] pci 0000:00:1f.4: [8086:a123] type 00 class 0x0c0500
[    0.216100] pci 0000:00:1f.4: reg 0x10: [mem 0xdd132000-0xdd1320ff 64bit]
[    0.216169] pci 0000:00:1f.4: reg 0x20: [io  0xf040-0xf05f]
[    0.216365] pci 0000:01:00.0: [10de:13d9] type 00 class 0x030200
[    0.216379] pci 0000:01:00.0: reg 0x10: [mem 0xdc000000-0xdcffffff]
[    0.216386] pci 0000:01:00.0: reg 0x14: [mem 0xb0000000-0xbfffffff 64bit pref]
[    0.216394] pci 0000:01:00.0: reg 0x1c: [mem 0xc0000000-0xc1ffffff 64bit pref]
[    0.216399] pci 0000:01:00.0: reg 0x24: [io  0xe000-0xe07f]
[    0.216404] pci 0000:01:00.0: reg 0x30: [mem 0xdd000000-0xdd07ffff pref]
[    0.216472] pci 0000:01:00.0: System wakeup disabled by ACPI
[    0.228286] pci 0000:00:01.0: PCI bridge to [bus 01]
[    0.228289] pci 0000:00:01.0:   bridge window [io  0xe000-0xefff]
[    0.228292] pci 0000:00:01.0:   bridge window [mem 0xdc000000-0xdd0fffff]
[    0.228295] pci 0000:00:01.0:   bridge window [mem 0xb0000000-0xc1ffffff 64bit pref]
[    0.228387] acpiphp: Slot [1] registered
[    0.228392] pci 0000:00:1c.0: PCI bridge to [bus 02-3a]
[    0.228397] pci 0000:00:1c.0:   bridge window [mem 0xc4000000-0xda0fffff]
[    0.228401] pci 0000:00:1c.0:   bridge window [mem 0x80000000-0xa1ffffff 64bit pref]
[    0.228491] pci 0000:3b:00.0: [1969:e0a1] type 00 class 0x020000
[    0.228535] pci 0000:3b:00.0: reg 0x10: [mem 0xdd500000-0xdd53ffff 64bit]
[    0.228546] pci 0000:3b:00.0: reg 0x18: [io  0xd000-0xd07f]
[    0.228621] pci 0000:3b:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.240304] pci 0000:00:1c.4: PCI bridge to [bus 3b]
[    0.240307] pci 0000:00:1c.4:   bridge window [io  0xd000-0xdfff]
[    0.240309] pci 0000:00:1c.4:   bridge window [mem 0xdd500000-0xdd5fffff]
[    0.240498] pci 0000:3c:00.0: [168c:003e] type 00 class 0x028000
[    0.240679] pci 0000:3c:00.0: reg 0x10: [mem 0xdd200000-0xdd3fffff 64bit]
[    0.241098] pci 0000:3c:00.0: PME# supported from D0 D3hot D3cold
[    0.252412] pci 0000:00:1c.5: PCI bridge to [bus 3c]
[    0.252416] pci 0000:00:1c.5:   bridge window [mem 0xdd200000-0xdd3fffff]
[    0.252525] pci 0000:3d:00.0: [10ec:5227] type 00 class 0xff0000
[    0.252559] pci 0000:3d:00.0: reg 0x10: [mem 0xdd400000-0xdd400fff]
[    0.252650] pci 0000:3d:00.0: supports D1 D2
[    0.252651] pci 0000:3d:00.0: PME# supported from D1 D2 D3hot D3cold
[    0.264352] pci 0000:00:1c.6: PCI bridge to [bus 3d]
[    0.264357] pci 0000:00:1c.6:   bridge window [mem 0xdd400000-0xdd4fffff]
[    0.273089] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 10 *11 12 14 15)
[    0.273135] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 *10 11 12 14 15)
[    0.273179] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 10 *11 12 14 15)
[    0.273223] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 10 *11 12 14 15)
[    0.273266] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 10 *11 12 14 15)
[    0.273311] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 10 *11 12 14 15)
[    0.273353] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 10 *11 12 14 15)
[    0.273395] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 10 *11 12 14 15)
[    0.273789] ACPI: Enabled 7 GPEs in block 00 to 7F
[    0.273822] ACPI : EC: GPE = 0x14, I/O: command/status = 0x66, data = 0x62
[    0.273901] vgaarb: setting as boot device: PCI:0000:00:02.0
[    0.273903] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.273905] vgaarb: loaded
[    0.273906] vgaarb: bridge control possible 0000:00:02.0
[    0.274130] SCSI subsystem initialized
[    0.274160] libata version 3.00 loaded.
[    0.274177] ACPI: bus type USB registered
[    0.274190] usbcore: registered new interface driver usbfs
[    0.274198] usbcore: registered new interface driver hub
[    0.274209] usbcore: registered new device driver usb
[    0.274361] PCI: Using ACPI for IRQ routing
[    0.297544] PCI: pci_cache_line_size set to 64 bytes
[    0.297694] e820: reserve RAM buffer [mem 0x00058000-0x0005ffff]
[    0.297695] e820: reserve RAM buffer [mem 0x0009e000-0x0009ffff]
[    0.297696] e820: reserve RAM buffer [mem 0x22a71018-0x23ffffff]
[    0.297697] e820: reserve RAM buffer [mem 0x22a8f018-0x23ffffff]
[    0.297698] e820: reserve RAM buffer [mem 0x22aa0018-0x23ffffff]
[    0.297699] e820: reserve RAM buffer [mem 0x3130c000-0x33ffffff]
[    0.297700] e820: reserve RAM buffer [mem 0x3138f000-0x33ffffff]
[    0.297701] e820: reserve RAM buffer [mem 0x361ac000-0x37ffffff]
[    0.297703] e820: reserve RAM buffer [mem 0x37fff000-0x37ffffff]
[    0.297777] NetLabel: Initializing
[    0.297778] NetLabel:  domain hash size = 128
[    0.297779] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.297786] NetLabel:  unlabeled traffic allowed by default
[    0.297871] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    0.297875] hpet0: 8 comparators, 64-bit 24.000000 MHz counter
[    0.299921] clocksource: Switched to clocksource hpet
[    0.304183] AppArmor: AppArmor Filesystem Enabled
[    0.304218] pnp: PnP ACPI init
[    0.304356] pnp 00:00: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.304378] pnp 00:01: Plug and Play ACPI device, IDs DLL0708 PNP0f13 (active)
[    0.304469] system 00:02: [io  0x0680-0x069f] has been reserved
[    0.304471] system 00:02: [io  0xffff] has been reserved
[    0.304472] system 00:02: [io  0xffff] has been reserved
[    0.304473] system 00:02: [io  0xffff] has been reserved
[    0.304475] system 00:02: [io  0x1800-0x18fe] could not be reserved
[    0.304476] system 00:02: [io  0x164e-0x164f] has been reserved
[    0.304478] system 00:02: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.304542] system 00:03: [io  0x0800-0x087f] has been reserved
[    0.304544] system 00:03: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.304559] pnp 00:04: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.304584] system 00:05: [io  0x1854-0x1857] has been reserved
[    0.304586] system 00:05: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
[    0.308124] system 00:06: [mem 0xfed10000-0xfed17fff] has been reserved
[    0.308125] system 00:06: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.308127] system 00:06: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.308129] system 00:06: [mem 0xe0000000-0xefffffff] has been reserved
[    0.308130] system 00:06: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.308132] system 00:06: [mem 0xfed90000-0xfed93fff] could not be reserved
[    0.308133] system 00:06: [mem 0xfed45000-0xfed8ffff] has been reserved
[    0.308135] system 00:06: [mem 0xff000000-0xffffffff] has been reserved
[    0.308137] system 00:06: [mem 0xfee00000-0xfeefffff] could not be reserved
[    0.308138] system 00:06: [mem 0xdffe0000-0xdfffffff] has been reserved
[    0.308141] system 00:06: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.308178] system 00:07: [mem 0xfd000000-0xfdabffff] has been reserved
[    0.308180] system 00:07: [mem 0xfdad0000-0xfdadffff] has been reserved
[    0.308181] system 00:07: [mem 0xfdb00000-0xfdffffff] has been reserved
[    0.308183] system 00:07: [mem 0xfe000000-0xfe01ffff] could not be reserved
[    0.308184] system 00:07: [mem 0xfe036000-0xfe03bfff] has been reserved
[    0.308186] system 00:07: [mem 0xfe03d000-0xfe3fffff] has been reserved
[    0.308187] system 00:07: [mem 0xfe410000-0xfe7fffff] has been reserved
[    0.308189] system 00:07: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.309142] system 00:08: [mem 0xfdaf0000-0xfdafffff] has been reserved
[    0.309144] system 00:08: [mem 0xfdae0000-0xfdaeffff] has been reserved
[    0.309146] system 00:08: [mem 0xfdac0000-0xfdacffff] has been reserved
[    0.309148] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.309895] pnp: PnP ACPI: found 9 devices
[    0.318072] clocksource: acpi_pm: mask: 0xffffff max_cycles: 0xffffff, max_idle_ns: 2085701024 ns
[    0.318087] pci 0000:00:1c.0: bridge window [io  0x1000-0x0fff] to [bus 02-3a] add_size 1000
[    0.318102] pci 0000:00:1c.0: res[13]=[io  0x1000-0x0fff] res_to_dev_res add_size 1000 min_align 1000
[    0.318104] pci 0000:00:1c.0: res[13]=[io  0x1000-0x1fff] res_to_dev_res add_size 1000 min_align 1000
[    0.318106] pci 0000:00:1c.0: BAR 13: assigned [io  0x2000-0x2fff]
[    0.318108] pci 0000:00:01.0: PCI bridge to [bus 01]
[    0.318109] pci 0000:00:01.0:   bridge window [io  0xe000-0xefff]
[    0.318112] pci 0000:00:01.0:   bridge window [mem 0xdc000000-0xdd0fffff]
[    0.318114] pci 0000:00:01.0:   bridge window [mem 0xb0000000-0xc1ffffff 64bit pref]
[    0.318117] pci 0000:00:1c.0: PCI bridge to [bus 02-3a]
[    0.318119] pci 0000:00:1c.0:   bridge window [io  0x2000-0x2fff]
[    0.318122] pci 0000:00:1c.0:   bridge window [mem 0xc4000000-0xda0fffff]
[    0.318124] pci 0000:00:1c.0:   bridge window [mem 0x80000000-0xa1ffffff 64bit pref]
[    0.318128] pci 0000:00:1c.4: PCI bridge to [bus 3b]
[    0.318130] pci 0000:00:1c.4:   bridge window [io  0xd000-0xdfff]
[    0.318133] pci 0000:00:1c.4:   bridge window [mem 0xdd500000-0xdd5fffff]
[    0.318138] pci 0000:00:1c.5: PCI bridge to [bus 3c]
[    0.318141] pci 0000:00:1c.5:   bridge window [mem 0xdd200000-0xdd3fffff]
[    0.318146] pci 0000:00:1c.6: PCI bridge to [bus 3d]
[    0.318148] pci 0000:00:1c.6:   bridge window [mem 0xdd400000-0xdd4fffff]
[    0.318154] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7 window]
[    0.318155] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff window]
[    0.318156] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff window]
[    0.318158] pci_bus 0000:00: resource 7 [mem 0x000c0000-0x000c3fff window]
[    0.318159] pci_bus 0000:00: resource 8 [mem 0x000c4000-0x000c7fff window]
[    0.318160] pci_bus 0000:00: resource 9 [mem 0x000c8000-0x000cbfff window]
[    0.318161] pci_bus 0000:00: resource 10 [mem 0x000cc000-0x000cffff window]
[    0.318162] pci_bus 0000:00: resource 11 [mem 0x000d0000-0x000d3fff window]
[    0.318163] pci_bus 0000:00: resource 12 [mem 0x000d4000-0x000d7fff window]
[    0.318164] pci_bus 0000:00: resource 13 [mem 0x000d8000-0x000dbfff window]
[    0.318165] pci_bus 0000:00: resource 14 [mem 0x000dc000-0x000dffff window]
[    0.318166] pci_bus 0000:00: resource 15 [mem 0x000e0000-0x000e3fff window]
[    0.318167] pci_bus 0000:00: resource 16 [mem 0x000e4000-0x000e7fff window]
[    0.318168] pci_bus 0000:00: resource 17 [mem 0x000e8000-0x000ebfff window]
[    0.318169] pci_bus 0000:00: resource 18 [mem 0x000ec000-0x000effff window]
[    0.318170] pci_bus 0000:00: resource 19 [mem 0x3b000000-0xdfffffff window]
[    0.318171] pci_bus 0000:00: resource 20 [mem 0xfd000000-0xfe7fffff window]
[    0.318172] pci_bus 0000:01: resource 0 [io  0xe000-0xefff]
[    0.318173] pci_bus 0000:01: resource 1 [mem 0xdc000000-0xdd0fffff]
[    0.318175] pci_bus 0000:01: resource 2 [mem 0xb0000000-0xc1ffffff 64bit pref]
[    0.318176] pci_bus 0000:02: resource 0 [io  0x2000-0x2fff]
[    0.318177] pci_bus 0000:02: resource 1 [mem 0xc4000000-0xda0fffff]
[    0.318178] pci_bus 0000:02: resource 2 [mem 0x80000000-0xa1ffffff 64bit pref]
[    0.318179] pci_bus 0000:3b: resource 0 [io  0xd000-0xdfff]
[    0.318180] pci_bus 0000:3b: resource 1 [mem 0xdd500000-0xdd5fffff]
[    0.318181] pci_bus 0000:3c: resource 1 [mem 0xdd200000-0xdd3fffff]
[    0.318182] pci_bus 0000:3d: resource 1 [mem 0xdd400000-0xdd4fffff]
[    0.318208] NET: Registered protocol family 2
[    0.318350] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.318524] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.318610] TCP: Hash tables configured (established 131072 bind 65536)
[    0.318640] UDP hash table entries: 8192 (order: 6, 262144 bytes)
[    0.318679] UDP-Lite hash table entries: 8192 (order: 6, 262144 bytes)
[    0.318727] NET: Registered protocol family 1
[    0.318738] pci 0000:00:02.0: Video device with shadowed ROM
[    0.319753] PCI: CLS 0 bytes, default 64
[    0.319785] Trying to unpack rootfs image as initramfs...
[    0.733734] Freeing initrd memory: 32344K (ffff880022abe000 - ffff880024a54000)
[    0.733758] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.733760] software IO TLB [mem 0x2d0fe000-0x310fe000] (64MB) mapped at [ffff88002d0fe000-ffff8800310fdfff]
[    0.733876] microcode: CPU0 sig=0x506e3, pf=0x20, revision=0x33
[    0.733886] microcode: CPU1 sig=0x506e3, pf=0x20, revision=0x33
[    0.733897] microcode: CPU2 sig=0x506e3, pf=0x20, revision=0x33
[    0.733901] microcode: CPU3 sig=0x506e3, pf=0x20, revision=0x33
[    0.733980] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.734085] Scanning for low memory corruption every 60 seconds
[    0.734477] futex hash table entries: 1024 (order: 4, 65536 bytes)
[    0.734488] Initialise system trusted keyring
[    0.734504] audit: initializing netlink subsys (disabled)
[    0.734518] audit: type=2000 audit(1448825868.732:1): initialized
[    0.734830] HugeTLB registered 1 GB page size, pre-allocated 0 pages
[    0.734831] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.735915] zpool: loaded
[    0.735917] zbud: loaded
[    0.736131] VFS: Disk quotas dquot_6.6.0
[    0.736153] VFS: Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.736681] fuse init (API version 7.23)
[    0.736795] Key type big_key registered
[    0.738135] Key type asymmetric registered
[    0.738138] Asymmetric key parser 'x509' registered
[    0.738147] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 249)
[    0.738263] io scheduler noop registered
[    0.738265] io scheduler deadline registered (default)
[    0.738286] io scheduler cfq registered
[    0.738855] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.738861] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.738886] efifb: probing for efifb
[    0.738898] efifb: framebuffer at 0x70000000, mapped to 0xffffc90002000000, using 8100k, total 8100k
[    0.738899] efifb: mode is 1920x1080x32, linelength=7680, pages=1
[    0.738900] efifb: scrolling: redraw
[    0.738901] efifb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    0.738985] Console: switching to colour frame buffer device 240x67
[    0.739001] fb0: EFI VGA frame buffer device
[    0.739008] intel_idle: MWAIT substates: 0x11142120
[    0.739009] intel_idle: v0.4 model 0x5E
[    0.739010] intel_idle: lapic_timer_reliable_states 0xffffffff
[    0.739242] ACPI: AC Adapter [ACAD] (on-line)
[    0.739295] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:3f/PNP0C0D:00/input/input0
[    0.739309] ACPI: Lid Switch [LID0]
[    0.739338] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1
[    0.739340] ACPI: Power Button [PWRB]
[    0.739364] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.739366] ACPI: Power Button [PWRF]
[    0.739665] GHES: HEST is not enabled!
[    0.739753] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.772637] ACPI: Battery Slot [BAT1] (battery present)
[    0.772962] Linux agpgart interface v0.103
[    0.776097] brd: module loaded
[    0.777006] loop: module loaded
[    0.777157] libphy: Fixed MDIO Bus: probed
[    0.777159] tun: Universal TUN/TAP device driver, 1.6
[    0.777159] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.777221] PPP generic driver version 2.4.2
[    0.777397] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    0.777401] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 1
[    0.777485] xhci_hcd 0000:00:14.0: hcc params 0x200077c1 hci version 0x100 quirks 0x00109810
[    0.777490] xhci_hcd 0000:00:14.0: cache line size of 64 is not supported
[    0.777555] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    0.777556] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.777557] usb usb1: Product: xHCI Host Controller
[    0.777559] usb usb1: Manufacturer: Linux 4.2.0-18-generic xhci-hcd
[    0.777560] usb usb1: SerialNumber: 0000:00:14.0
[    0.777673] hub 1-0:1.0: USB hub found
[    0.777688] hub 1-0:1.0: 16 ports detected
[    0.786961] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    0.786963] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 2
[    0.786985] usb usb2: New USB device found, idVendor=1d6b, idProduct=0003
[    0.786986] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.786987] usb usb2: Product: xHCI Host Controller
[    0.786988] usb usb2: Manufacturer: Linux 4.2.0-18-generic xhci-hcd
[    0.786989] usb usb2: SerialNumber: 0000:00:14.0
[    0.787118] hub 2-0:1.0: USB hub found
[    0.787127] hub 2-0:1.0: 8 ports detected
[    0.791577] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.791581] ehci-pci: EHCI PCI platform driver
[    0.791587] ehci-platform: EHCI generic platform driver
[    0.791594] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.791596] ohci-pci: OHCI PCI platform driver
[    0.791602] ohci-platform: OHCI generic platform driver
[    0.791608] uhci_hcd: USB Universal Host Controller Interface driver
[    0.791638] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.818430] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.818433] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.818699] mousedev: PS/2 mouse device common for all mice
[    0.819157] rtc_cmos 00:04: RTC can wake from S4
[    0.819570] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    0.819648] rtc_cmos 00:04: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    0.819653] i2c /dev entries driver
[    0.819699] device-mapper: uevent: version 1.0.3
[    0.819870] device-mapper: ioctl: 4.33.0-ioctl (2015-8-18) initialised: dm-devel@redhat.com
[    0.819881] Intel P-state driver initializing.
[    0.820143] ledtrig-cpu: registered to indicate activity on CPUs
[    0.820151] EFI Variables Facility v0.08 2004-May-17
[    0.826126] PCCT header not found.
[    0.826309] NET: Registered protocol family 10
[    0.826570] NET: Registered protocol family 17
[    0.826585] Key type dns_resolver registered
[    0.827117] Loading compiled-in X.509 certificates
[    0.827694] Loaded X.509 cert 'Build time autogenerated kernel key: 93ad27021225ce1bb4865e4bab1e2b6a5f099429'
[    0.827707] registered taskstats version 1
[    0.827722] zswap: loading zswap
[    0.827723] zswap: using zbud pool
[    0.827726] zswap: using lzo compressor
[    0.830236] Key type trusted registered
[    0.833670] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    0.835620] Key type encrypted registered
[    0.835639] AppArmor: AppArmor sha1 policy hashing enabled
[    0.835642] ima: No TPM chip found, activating TPM-bypass!
[    0.835654] evm: HMAC attrs: 0x1
[    0.836744]   Magic number: 7:807:648
[    0.836820] acpi LNXCPU:01: hash matches
[    0.837103] rtc_cmos 00:04: setting system clock to 2015-11-29 19:37:48 UTC (1448825868)
[    0.837373] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.837374] EDD information not available.
[    0.837491] PM: Hibernation image not present or could not be loaded.
[    0.837875] Freeing unused kernel memory: 1460K (ffffffff81d37000 - ffffffff81ea4000)
[    0.837876] Write protecting the kernel read-only data: 12288k
[    0.838699] Freeing unused kernel memory: 36K (ffff8800017f7000 - ffff880001800000)
[    0.839211] Freeing unused kernel memory: 296K (ffff880001bb6000 - ffff880001c00000)
[    0.851277] random: systemd-udevd urandom read with 7 bits of entropy available
[    0.876352] hidraw: raw HID events driver (C) Jiri Kosina
[    0.905181] ahci 0000:00:17.0: version 3.0
[    0.906375] [drm] Initialized drm 1.1.0 20060810
[    0.912164] rtsx_pci 0000:3d:00.0: enabling device (0000 -> 0002)
[    0.912663] rtsx_pci 0000:3d:00.0: rtsx_pci_acquire_irq: pcr->msi_en = 1, pci->irq = 125
[    0.916881] alx 0000:3b:00.0 eth0: Qualcomm Atheros AR816x/AR817x Ethernet [20:47:47:f2:85:10]
[    0.920858] ahci 0000:00:17.0: AHCI 0001.0301 32 slots 1 ports 6 Gbps 0x2 impl RAID mode
[    0.920861] ahci 0000:00:17.0: flags: 64bit ncq sntf pm led clo only pio slum part ems deso sadm sds apst 
[    0.922894] scsi host0: ahci
[    0.923266] scsi host1: ahci
[    0.923326] ata1: DUMMY
[    0.923328] ata2: SATA max UDMA/133 abar m2048@0xdd133000 port 0xdd133180 irq 124
[    0.926240] [drm] Memory usable by graphics device = 4096M
[    0.926242] checking generic (70000000 7e9000) vs hw (70000000 10000000)
[    0.926243] fb: switching to inteldrmfb from EFI VGA
[    0.926260] Console: switching to colour dummy device 80x25
[    0.926460] [drm] Replacing VGA console driver
[    0.933348] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[    0.933350] [drm] Driver supports precise vblank timestamp query.
[    0.941305] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[    0.952783] alx 0000:3b:00.0 enp59s0: renamed from eth0
[    0.962207] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[    0.962504] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input7
[    0.962767] ACPI Exception: AE_NOT_FOUND, Evaluating _DOD (20150619/video-1157)
[    0.962771] ACPI: Video Device [PEGP] (multi-head: no  rom: yes  post: no)
[    0.962809] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:12/LNXVIDEO:01/input/input8
[    0.962856] fbcon: inteldrmfb (fb0) is primary device
[    0.962915] Console: switching to colour frame buffer device 240x67
[    0.962933] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[    0.962934] i915 0000:00:02.0: registered panic notifier
[    0.962961] [drm] Initialized i915 1.6.0 20150522 for 0000:00:02.0 on minor 0
[    1.097004] usb 1-4: new full-speed USB device number 2 using xhci_hcd
[    1.105054] usb 2-1: new SuperSpeed USB device number 2 using xhci_hcd
[    1.121797] usb 2-1: New USB device found, idVendor=0781, idProduct=5580
[    1.121800] usb 2-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    1.121801] usb 2-1: Product: Extreme
[    1.121803] usb 2-1: Manufacturer: SanDisk
[    1.121804] usb 2-1: SerialNumber: AA010611150056461768
[    1.125440] usb-storage 2-1:1.0: USB Mass Storage device detected
[    1.126112] scsi host2: usb-storage 2-1:1.0
[    1.126485] usbcore: registered new interface driver usb-storage
[    1.127788] usbcore: registered new interface driver uas
[    1.226359] usb 1-4: config 1 interface 0 altsetting 0 has 2 endpoint descriptors, different from the interface descriptor's value: 1
[    1.227802] usb 1-4: New USB device found, idVendor=187c, idProduct=0528
[    1.227805] usb 1-4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    1.227806] usb 1-4: Product: AW1517
[    1.227808] usb 1-4: Manufacturer: Alienware
[    1.227809] usb 1-4: SerialNumber: 16.0
[    1.228000] usb 1-4: ep 0x81 - rounding interval to 64 microframes, ep desc says 80 microframes
[    1.231800] usbcore: registered new interface driver usbhid
[    1.231801] usbhid: USB HID core driver
[    1.233970] hid-generic 0003:187C:0528.0001: hiddev0,hidraw0: USB HID v1.01 Device [Alienware AW1517] on usb-0000:00:14.0-4/input0
[    1.237290] ata2: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    1.238706] ata2.00: ATA-8: HGST HTS721010A9E630, JB0OA3P0, max UDMA/133
[    1.238709] ata2.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.240284] ata2.00: configured for UDMA/133
[    1.240516] scsi 1:0:0:0: Direct-Access     ATA      HGST HTS721010A9 A3P0 PQ: 0 ANSI: 5
[    1.241034] sd 1:0:0:0: Attached scsi generic sg0 type 0
[    1.241173] sd 1:0:0:0: [sda] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    1.241176] sd 1:0:0:0: [sda] 4096-byte physical blocks
[    1.241481] sd 1:0:0:0: [sda] Write Protect is off
[    1.241484] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.241696] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.300938] psmouse serio1: synaptics: queried max coordinates: x [..5668], y [..4756]
[    1.310741]  sda: sda1 sda2 sda3
[    1.311958] sd 1:0:0:0: [sda] Attached SCSI disk
[    1.331529] psmouse serio1: synaptics: queried min coordinates: x [1274..], y [1098..]
[    1.392183] psmouse serio1: synaptics: Touchpad model: 1, fw: 8.1, id: 0x1e2b1, caps: 0xd00123/0x840300/0x26c00/0x0, board id: 2417, fw id: 1365292
[    1.393389] usb 1-5: new full-speed USB device number 3 using xhci_hcd
[    1.430365] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input6
[    1.522987] usb 1-5: New USB device found, idVendor=0cf3, idProduct=e301
[    1.522990] usb 1-5: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.689778] usb 1-7: new high-speed USB device number 4 using xhci_hcd
[    1.733912] tsc: Refined TSC clocksource calibration: 2303.990 MHz
[    1.733915] clocksource: tsc: mask: 0xffffffffffffffff max_cycles: 0x2135eea1b5d, max_idle_ns: 440795323451 ns
[    1.826942] usb 1-7: New USB device found, idVendor=1bcf, idProduct=2b8c
[    1.826944] usb 1-7: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.826946] usb 1-7: Product: Integrated_Webcam_HD
[    1.826948] usb 1-7: Manufacturer: SunplusIT Inc
[    2.126890] scsi 2:0:0:0: Direct-Access     SanDisk  Extreme          0001 PQ: 0 ANSI: 6
[    2.127245] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    2.127599] sd 2:0:0:0: [sdb] 122544516 512-byte logical blocks: (62.7 GB/58.4 GiB)
[    2.128059] sd 2:0:0:0: [sdb] Write Protect is off
[    2.128063] sd 2:0:0:0: [sdb] Mode Sense: 53 00 00 08
[    2.128403] sd 2:0:0:0: [sdb] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[    2.134069] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[    2.572870] random: nonblocking pool is initialized
[    2.735462] clocksource: Switched to clocksource tsc
[    2.819398] [drm] RC6 on
[    8.028469] EXT4-fs (sda2): mounted filesystem with ordered data mode. Opts: (null)
[    8.877457] systemd[1]: Failed to insert module 'kdbus': Function not implemented
[    9.001682] systemd[1]: systemd 225 running in system mode. (+PAM +AUDIT +SELINUX +IMA +APPARMOR +SMACK +SYSVINIT +UTMP +LIBCRYPTSETUP +GCRYPT +GNUTLS +ACL +XZ -LZ4 +SECCOMP +BLKID -ELFUTILS +KMOD -IDN)
[    9.001803] systemd[1]: Detected architecture x86-64.
[    9.016693] systemd[1]: Set hostname to <Alienware-15-R2>.
[    9.608511] systemd[1]: NetworkManager.service: Cannot add dependency job, ignoring: Unit NetworkManager.service is masked.
[    9.608978] systemd[1]: Started Forward Password Requests to Wall Directory Watch.
[    9.609147] systemd[1]: Set up automount Arbitrary Executable File Formats File System Automount Point.
[    9.609160] systemd[1]: Reached target User and Group Name Lookups.
[    9.609182] systemd[1]: Created slice Root Slice.
[    9.609210] systemd[1]: Listening on Journal Socket (/dev/log).
[    9.609230] systemd[1]: Listening on /dev/initctl Compatibility Named Pipe.
[    9.609245] systemd[1]: Listening on udev Kernel Socket.
[    9.609258] systemd[1]: Listening on fsck to fsckd communication Socket.
[    9.609281] systemd[1]: Listening on Journal Socket.
[    9.609353] systemd[1]: Created slice System Slice.
[    9.609425] systemd[1]: Created slice system-systemd\x2dfsck.slice.
[    9.609795] systemd[1]: Started Braille Device Support.
[    9.610117] systemd[1]: Created slice system-getty.slice.
[    9.610617] systemd[1]: Started Read required files in advance.
[    9.622024] systemd[1]: Starting Load Kernel Modules...
[    9.622557] systemd[1]: Starting Increase datagram queue length...
[    9.682616] systemd[1]: Mounting Debug File System...
[    9.683143] systemd[1]: Starting Create list of required static device nodes for the current kernel...
[    9.683617] systemd[1]: Starting Setup Virtual Console...
[    9.684190] systemd[1]: Mounting Huge Pages File System...
[    9.684300] systemd[1]: Created slice User and Session Slice.
[    9.684768] systemd[1]: Mounting POSIX Message Queue File System...
[    9.684784] systemd[1]: Reached target Remote File Systems (Pre).
[    9.684838] systemd[1]: Listening on udev Control Socket.
[    9.685330] systemd[1]: Starting udev Coldplug all Devices...
[    9.685795] systemd[1]: Starting Uncomplicated firewall...
[    9.685880] systemd[1]: Created slice system-systemd\x2dcryptsetup.slice.
[    9.685967] systemd[1]: Listening on Journal Audit Socket.
[    9.685996] systemd[1]: Reached target Slices.
[    9.702408] systemd[1]: Started Setup Virtual Console.
[    9.741574] systemd[1]: Started Create list of required static device nodes for the current kernel.
[    9.742087] systemd[1]: Starting Create Static Device Nodes in /dev...
[    9.834949] systemd[1]: Started udev Coldplug all Devices.
[    9.903711] systemd[1]: Mounted Debug File System.
[    9.903765] systemd[1]: Mounted POSIX Message Queue File System.
[    9.903800] systemd[1]: Mounted Huge Pages File System.
[    9.923535] systemd[1]: Started Uncomplicated firewall.
[   10.000178] systemd[1]: Started Increase datagram queue length.
[   10.000305] systemd[1]: Listening on Syslog Socket.
[   10.000703] systemd[1]: Starting Journal Service...
[   10.262530] lp: driver loaded but no devices found
[   10.269110] ppdev: user-space parallel port driver
[   10.348209] systemd[1]: Started Load Kernel Modules.
[   10.348721] systemd[1]: Starting Apply Kernel Variables...
[   10.349216] systemd[1]: Mounting FUSE Control File System...
[   10.350794] systemd[1]: Mounted FUSE Control File System.
[   10.366462] systemd[1]: Started Journal Service.
[   11.146801] EXT4-fs (sda2): re-mounted. Opts: errors=remount-ro
[   11.303156] systemd-journald[284]: Received request to flush runtime journal from PID 1
[   11.534146] mei_me 0000:00:16.0: enabling device (0000 -> 0002)
[   11.577861] tpm_crb MSFT0101:00: ioremap of the command buffer failed
[   11.577866] tpm_crb: probe of MSFT0101:00 failed with error -12
[   11.583751] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   11.609854] wmi: Mapper loaded
[   11.658448] proc_thermal 0000:00:04.0: enabling device (0000 -> 0002)
[   11.764026] compat: module verification failed: signature and/or required key missing - tainting kernel
[   11.764187] Loading modules backported from Linux version next-20151120-0-ga78de01
[   11.764188] Backport generated by backports.git backports-20151120-0-g906a6b3
[   12.095815] AVX2 version of gcm_enc/dec engaged.
[   12.095817] AES CTR mode by8 optimization enabled
[   12.130492] Bluetooth: Core ver 2.20
[   12.130515] NET: Registered protocol family 31
[   12.130516] Bluetooth: HCI device and connection manager initialized
[   12.130518] Bluetooth: HCI socket layer initialized
[   12.130519] Bluetooth: L2CAP socket layer initialized
[   12.130522] Bluetooth: SCO socket layer initialized
[   12.410821] media: Linux media interface: v0.10
[   12.457339] input: Dell WMI hotkeys as /devices/virtual/input/input9
[   12.466941] ath10k_pci 0000:3c:00.0: enabling device (0000 -> 0002)
[   12.467832] ath10k_pci 0000:3c:00.0: pci irq msi-x interrupts 8 irq_mode 0 reset_mode 0
[   12.620699] Linux video capture interface: v2.00
[   12.642007] usbcore: registered new interface driver btusb
[   12.685064] snd_hda_intel 0000:00:1f.3: enabling device (0000 -> 0002)
[   12.685199] snd_hda_intel 0000:00:1f.3: bound 0000:00:02.0 (ops i915_audio_component_bind_ops [i915])
[   12.827656] ath10k_pci 0000:3c:00.0: Direct firmware load for ath10k/cal-pci-0000:3c:00.0.bin failed with error -2
[   12.836197] ath10k_pci 0000:3c:00.0: Direct firmware load for ath10k/QCA6174/hw3.0/firmware-5.bin failed with error -2
[   12.836201] ath10k_pci 0000:3c:00.0: could not fetch firmware file 'ath10k/QCA6174/hw3.0/firmware-5.bin': -2
[   12.945003] snd_hda_codec_ca0132 hdaudioC0D0: autoconfig for CA0132: line_outs=1 (0xb/0x0/0x0/0x0/0x0) type:speaker
[   12.945006] snd_hda_codec_ca0132 hdaudioC0D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   12.945008] snd_hda_codec_ca0132 hdaudioC0D0:    hp_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   12.945009] snd_hda_codec_ca0132 hdaudioC0D0:    mono: mono_out=0x0
[   12.945010] snd_hda_codec_ca0132 hdaudioC0D0:    inputs:
[   12.945012] snd_hda_codec_ca0132 hdaudioC0D0:      Mic=0x12
[   12.945013] snd_hda_codec_ca0132 hdaudioC0D0:      Line=0x11
[   13.159518] intel_rapl: Found RAPL domain package
[   13.159520] intel_rapl: Found RAPL domain core
[   13.159522] intel_rapl: Found RAPL domain uncore
[   13.159523] intel_rapl: Found RAPL domain dram
[   13.321546] uvcvideo: Found UVC 1.00 device Integrated_Webcam_HD (1bcf:2b8c)
[   13.328991] input: Integrated_Webcam_HD as /devices/pci0000:00/0000:00:14.0/usb1/1-7/1-7:1.0/input/input10
[   13.329037] usbcore: registered new interface driver uvcvideo
[   13.329038] USB Video Class driver (1.1.1)
[   13.415574] ath10k_pci 0000:3c:00.0: found invalid board magic
[   13.460568] cfg80211: World regulatory domain updated:
[   13.460571] cfg80211:  DFS Master region: unset
[   13.460572] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
[   13.460573] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
[   13.460574] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
[   13.460575] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (N/A, 2000 mBm), (N/A)
[   13.460576] cfg80211:   (5170000 KHz - 5250000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (N/A)
[   13.460578] cfg80211:   (5250000 KHz - 5330000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (0 s)
[   13.460579] cfg80211:   (5490000 KHz - 5730000 KHz @ 160000 KHz), (N/A, 2000 mBm), (0 s)
[   13.460580] cfg80211:   (5735000 KHz - 5835000 KHz @ 80000 KHz), (N/A, 2000 mBm), (N/A)
[   13.460581] cfg80211:   (57240000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 0 mBm), (N/A)
[   13.913142] ca0132 DOWNLOAD OK :-) DSP IS RUNNING.
[   14.382156] input: HDA Intel PCH Front Line Out as /devices/pci0000:00/0000:00:1f.3/sound/card0/input11
[   14.382198] input: HDA Intel PCH Line Out as /devices/pci0000:00/0000:00:1f.3/sound/card0/input12
[   14.382753] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1f.3/sound/card0/input13
[   14.382813] input: HDA Intel PCH HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:1f.3/sound/card0/input14
[   14.382898] input: HDA Intel PCH HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:1f.3/sound/card0/input15
[   14.791388] nvidia: module license 'NVIDIA' taints kernel.
[   14.791390] Disabling lock debugging due to kernel taint
[   14.796494] nvidia 0000:01:00.0: enabling device (0006 -> 0007)
[   14.796712] [drm] Initialized nvidia-drm 0.0.0 20150116 for 0000:01:00.0 on minor 1
[   14.796732] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  352.63  Sat Nov  7 21:25:42 PST 2015
[   15.002526] ca0132 DOWNLOAD OK :-) DSP IS RUNNING.
[   15.556260] ath10k_pci 0000:3c:00.0: qca6174 hw3.2 (0x05030000, 0x00340aff sub 1a56:1535) fw WLAN.RM.2.0-00180-QCARMSWPZ-1 fwapi 4 bdapi 1 htt-ver 3.26 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1 features wowlan,ignore-otp,no-4addr-pad
[   15.556268] ath10k_pci 0000:3c:00.0: debug 1 debugfs 1 tracing 0 dfs 0 testmode 0
[   15.626740] ath: EEPROM regdomain: 0x69
[   15.626742] ath: EEPROM indicates we should expect a direct regpair map
[   15.626744] ath: Country alpha2 being used: 00
[   15.626745] ath: Regpair used: 0x69
[   15.785854] ath10k_pci 0000:3c:00.0 wlp60s0: renamed from wlan0
[   17.235173] audit: type=1400 audit(1448825884.872:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/lightdm/lightdm-guest-session" pid=614 comm="apparmor_parser"
[   17.235179] audit: type=1400 audit(1448825884.872:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="chromium" pid=614 comm="apparmor_parser"
[   17.275741] audit: type=1400 audit(1448825884.912:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=614 comm="apparmor_parser"
[   17.275746] audit: type=1400 audit(1448825884.912:5): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=614 comm="apparmor_parser"
[   17.275750] audit: type=1400 audit(1448825884.912:6): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-helper" pid=614 comm="apparmor_parser"
[   17.275754] audit: type=1400 audit(1448825884.912:7): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=614 comm="apparmor_parser"
[   17.418828] audit: type=1400 audit(1448825885.056:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/evince" pid=614 comm="apparmor_parser"
[   17.418834] audit: type=1400 audit(1448825885.056:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="sanitized_helper" pid=614 comm="apparmor_parser"
[   17.418838] audit: type=1400 audit(1448825885.056:10): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/evince-previewer" pid=614 comm="apparmor_parser"
[   17.418842] audit: type=1400 audit(1448825885.056:11): apparmor="STATUS" operation="profile_load" profile="unconfined" name="sanitized_helper" pid=614 comm="apparmor_parser"
[   17.513720] Adding 12478972k swap on /dev/mapper/cryptswap1.  Priority:-1 extents:1 across:12478972k FS
[   21.555825] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   21.555828] Bluetooth: BNEP filters: protocol multicast
[   21.555831] Bluetooth: BNEP socket layer initialized
[   21.779812] cgroup: new mount options do not match the existing superblock, will be ignored
[   23.402802] bbswitch: version 0.7
[   23.402825] bbswitch: Found integrated VGA device 0000:00:02.0: \_SB_.PCI0.GFX0
[   23.402828] bbswitch: Found discrete VGA device 0000:01:00.0: \_SB_.PCI0.PEG0.PEGP
[   23.402849] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150619/nsarguments-95)
[   23.403045] bbswitch: detected an Optimus _DSM function
[   23.403053] bbswitch: Succesfully loaded. Discrete card 0000:01:00.0 is on
[   23.998044] vgaarb: this pci device is not a vga device
[   24.000122] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150619/nsarguments-95)
[   24.000165] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150619/nsarguments-95)
[   24.000189] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150619/nsarguments-95)
[   24.000212] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150619/nsarguments-95)
[   24.000233] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150619/nsarguments-95)
[   24.000255] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150619/nsarguments-95)
[   24.000289] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150619/nsarguments-95)
[   24.000312] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150619/nsarguments-95)
[   25.058310] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150619/nsarguments-95)
[   25.298876] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150619/nsarguments-95)
[   25.298943] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150619/nsarguments-95)
[   25.299009] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150619/nsarguments-95)
[   25.299121] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150619/nsarguments-95)
[   25.624386] vgaarb: this pci device is not a vga device
[   28.499099] ath10k_pci 0000:3c:00.0: failed to enable dynamic BW: -11
[   34.506572] ath10k_pci 0000:3c:00.0: could not suspend target (-11)
[   34.584639] IPv6: ADDRCONF(NETDEV_UP): enp59s0: link is not ready
[   34.585415] alx 0000:3b:00.0 enp59s0: NIC Up: 1 Gbps Full
[   34.585641] IPv6: ADDRCONF(NETDEV_CHANGE): enp59s0: link becomes ready
[   39.276887] Bluetooth: RFCOMM TTY layer initialized
[   39.276893] Bluetooth: RFCOMM socket layer initialized
[   39.276897] Bluetooth: RFCOMM ver 1.11
[   41.923804] ath10k_pci 0000:3c:00.0: failed to enable dynamic BW: -11
[   47.931250] ath10k_pci 0000:3c:00.0: could not suspend target (-11)
[   53.257911] ath10k_pci 0000:3c:00.0: failed to enable dynamic BW: -11
[   53.756891] UDF-fs: warning (device sdb): udf_load_vrs: No anchor found
[   53.756893] UDF-fs: Rescanning with blocksize 2048
[   53.768666] UDF-fs: warning (device sdb): udf_load_vrs: No anchor found
[   53.768668] UDF-fs: Rescanning with blocksize 2048
[   53.774789] UDF-fs: INFO Mounting volume 'UDF Volume', timestamp 2010/11/21 08:33 (1000)
[   59.265381] ath10k_pci 0000:3c:00.0: could not suspend target (-11)
[   59.854164] IPv6: ADDRCONF(NETDEV_UP): enp59s0: link is not ready
[   59.854936] alx 0000:3b:00.0 enp59s0: NIC Up: 1 Gbps Full
[   59.855092] IPv6: ADDRCONF(NETDEV_CHANGE): enp59s0: link becomes ready
[   59.988870] IPv6: ADDRCONF(NETDEV_UP): enp59s0: link is not ready
[   59.989643] alx 0000:3b:00.0 enp59s0: NIC Up: 1 Gbps Full
[   59.989812] IPv6: ADDRCONF(NETDEV_CHANGE): enp59s0: link becomes ready
[   94.729460] ath10k_pci 0000:3c:00.0: failed to enable dynamic BW: -11
[  100.736993] ath10k_pci 0000:3c:00.0: could not suspend target (-11)
[  123.917572] ath10k_pci 0000:3c:00.0: failed to enable dynamic BW: -11
[  129.924952] ath10k_pci 0000:3c:00.0: could not suspend target (-11)


```

dmesg | grep ath10k
```
sudo dmesg | grep ath10k
[   12.466941] ath10k_pci 0000:3c:00.0: enabling device (0000 -> 0002)
[   12.467832] ath10k_pci 0000:3c:00.0: pci irq msi-x interrupts 8 irq_mode 0 reset_mode 0
[   12.827656] ath10k_pci 0000:3c:00.0: Direct firmware load for ath10k/cal-pci-0000:3c:00.0.bin failed with error -2
[   12.836197] ath10k_pci 0000:3c:00.0: Direct firmware load for ath10k/QCA6174/hw3.0/firmware-5.bin failed with error -2
[   12.836201] ath10k_pci 0000:3c:00.0: could not fetch firmware file 'ath10k/QCA6174/hw3.0/firmware-5.bin': -2
[   13.415574] ath10k_pci 0000:3c:00.0: found invalid board magic
[   15.556260] ath10k_pci 0000:3c:00.0: qca6174 hw3.2 (0x05030000, 0x00340aff sub 1a56:1535) fw WLAN.RM.2.0-00180-QCARMSWPZ-1 fwapi 4 bdapi 1 htt-ver 3.26 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1 features wowlan,ignore-otp,no-4addr-pad
[   15.556268] ath10k_pci 0000:3c:00.0: debug 1 debugfs 1 tracing 0 dfs 0 testmode 0
[   15.785854] ath10k_pci 0000:3c:00.0 wlp60s0: renamed from wlan0
[   28.499099] ath10k_pci 0000:3c:00.0: failed to enable dynamic BW: -11
[   34.506572] ath10k_pci 0000:3c:00.0: could not suspend target (-11)
[   41.923804] ath10k_pci 0000:3c:00.0: failed to enable dynamic BW: -11
[   47.931250] ath10k_pci 0000:3c:00.0: could not suspend target (-11)
[   53.257911] ath10k_pci 0000:3c:00.0: failed to enable dynamic BW: -11
[   59.265381] ath10k_pci 0000:3c:00.0: could not suspend target (-11)
[   94.729460] ath10k_pci 0000:3c:00.0: failed to enable dynamic BW: -11
[  100.736993] ath10k_pci 0000:3c:00.0: could not suspend target (-11)
[  123.917572] ath10k_pci 0000:3c:00.0: failed to enable dynamic BW: -11
[  129.924952] ath10k_pci 0000:3c:00.0: could not suspend target (-11)


```

---

### Post by jeremy31 on 2015-11-29
Let's remove the new board file ```
sudo rm /lib/firmware/ath10k/QCA6174/hw3.0/board-2.bin
```

Shutdown and do a cold boot
Installing Pastebin might make it easier to post script result ```
sudo apt-get install pastebinit
```
Then try the wireless script ```
wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && chmod +x wireless-info && ./wireless-info
```
At the end it should ask if you want to upload to pastebin, press y then enter and copy the URL from terminal

---

### Post by wood3d on 2015-11-29
Removed Board-2

Pastebin URL:

[http://paste.ubuntu.com/13565735/](http://paste.ubuntu.com/13565735/)

---

### Post by jeremy31 on 2015-11-29
Only one more idea ```
sudo mv /lib/firmware/[COLOR=#000000][FONT=Ubuntu Mono]ath10k/QCA6174/hw3.0/firmware-4.bin /lib/firmware/[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]ath10k/QCA6174/hw3.0/firmware-5.bin
```

Reboot

If nothing else we will have to monitor the bug report [/FONT][/COLOR]https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1520343?comments=all

---

### Post by wood3d on 2015-11-29
No luck. I appreciate the effort you put into it though. I'll keep an eye on that bug report.

---

### Post by jeremy31 on 2015-12-02
Saw something in the bug report
```
[COLOR=#000000][FONT=Ubuntu Mono]cd /lib/firmware/ath10k/QCA6174/hw3.0[/FONT][/COLOR]wget https://github.com/FireWalkerX/ath10k-firmware/blob/7e56cbb94182a2fdab110cf5bfeded8fd1d44d30/QCA6174/hw3.0/board-2.bin
sudo mv board-2.bin board.bin
```
reboot

---

### Post by demo3 on 2015-12-29
I am having the same issue as well and I have tried what you have suggested and it has not worked.

dmesg:

[    0.553713] pnp: PnP ACPI: found 7 devices
[    0.563184] pci 0000:00:01.0: PCI bridge to [bus 01]
[    0.563192] pci 0000:00:01.0:   bridge window [io  0xe000-0xefff]
[    0.563201] pci 0000:00:01.0:   bridge window [mem 0xf5000000-0xf60fffff]
[    0.563208] pci 0000:00:01.0:   bridge window [mem 0xe0000000-0xf1ffffff 64bit pref]
[    0.563218] pci 0000:00:1c.0: PCI bridge to [bus 02]
[    0.563228] pci 0000:00:1c.0:   bridge window [io  0xd000-0xdfff]
[    0.563238] pci 0000:00:1c.0:   bridge window [mem 0xf7400000-0xf74fffff]
[    0.563260] pci 0000:00:1c.3: PCI bridge to [bus 03]
[    0.563276] pci 0000:00:1c.3:   bridge window [mem 0xf6800000-0xf69fffff]
[    0.563298] pci 0000:00:1c.4: PCI bridge to [bus 04]
[    0.563308] pci 0000:00:1c.4:   bridge window [io  0xc000-0xcfff]
[    0.563323] pci 0000:00:1c.4:   bridge window [mem 0xf6a00000-0xf73fffff]
[    0.563337] pci 0000:00:1c.4:   bridge window [mem 0xf2100000-0xf2afffff 64bit pref]
[    0.563356] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.563361] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.563365] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.563369] pci_bus 0000:00: resource 7 [mem 0xcfa00000-0xfeafffff]
[    0.563373] pci_bus 0000:01: resource 0 [io  0xe000-0xefff]
[    0.563377] pci_bus 0000:01: resource 1 [mem 0xf5000000-0xf60fffff]
[    0.563381] pci_bus 0000:01: resource 2 [mem 0xe0000000-0xf1ffffff 64bit pref]
[    0.563385] pci_bus 0000:02: resource 0 [io  0xd000-0xdfff]
[    0.563389] pci_bus 0000:02: resource 1 [mem 0xf7400000-0xf74fffff]
[    0.563393] pci_bus 0000:03: resource 1 [mem 0xf6800000-0xf69fffff]
[    0.563397] pci_bus 0000:04: resource 0 [io  0xc000-0xcfff]
[    0.563400] pci_bus 0000:04: resource 1 [mem 0xf6a00000-0xf73fffff]
[    0.563404] pci_bus 0000:04: resource 2 [mem 0xf2100000-0xf2afffff 64bit pref]
[    0.563466] NET: Registered protocol family 2
[    0.563943] TCP established hash table entries: 65536 (order: 7, 524288 bytes)
[    0.564322] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.564599] TCP: Hash tables configured (established 65536 bind 65536)
[    0.564636] TCP: reno registered
[    0.564663] UDP hash table entries: 4096 (order: 5, 131072 bytes)
[    0.564730] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
[    0.564862] NET: Registered protocol family 1
[    0.564899] pci 0000:00:02.0: Video device with shadowed ROM
[    0.604238] pci 0000:02:00.0: set MSI_INTX_DISABLE_BUG flag
[    0.604347] PCI: CLS 64 bytes, default 64
[    0.604469] Trying to unpack rootfs image as initramfs...
[    1.930779] Freeing initrd memory: 30332K (ffff8800344b2000 - ffff880036251000)
[    1.930868] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    1.930874] software IO TLB [mem 0xc5b6a000-0xc9b6a000] (64MB) mapped at [ffff8800c5b6a000-ffff8800c9b69fff]
[    1.931659] RAPL PMU detected, hw unit 2^-14 Joules, API unit is 2^-32 Joules, 4 fixed counters 655360 ms ovfl timer
[    1.931803] microcode: CPU0 sig=0x306c3, pf=0x20, revision=0x1c
[    1.931833] microcode: CPU1 sig=0x306c3, pf=0x20, revision=0x1c
[    1.931850] microcode: CPU2 sig=0x306c3, pf=0x20, revision=0x1c
[    1.931871] microcode: CPU3 sig=0x306c3, pf=0x20, revision=0x1c
[    1.931890] microcode: CPU4 sig=0x306c3, pf=0x20, revision=0x1c
[    1.931922] microcode: CPU5 sig=0x306c3, pf=0x20, revision=0x1c
[    1.931934] microcode: CPU6 sig=0x306c3, pf=0x20, revision=0x1c
[    1.931952] microcode: CPU7 sig=0x306c3, pf=0x20, revision=0x1c
[    1.932092] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    1.932162] Scanning for low memory corruption every 60 seconds
[    1.933046] futex hash table entries: 2048 (order: 5, 131072 bytes)
[    1.933098] Initialise system trusted keyring
[    1.933156] audit: initializing netlink subsys (disabled)
[    1.933182] audit: type=2000 audit(1451399925.932:1): initialized
[    1.933986] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.937722] zpool: loaded
[    1.937733] zbud: loaded
[    1.938136] VFS: Disk quotas dquot_6.5.2
[    1.938221] VFS: Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.939332] fuse init (API version 7.23)
[    1.939688] Key type big_key registered
[    1.940770] Key type asymmetric registered
[    1.940777] Asymmetric key parser 'x509' registered
[    1.940862] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    1.940971] io scheduler noop registered
[    1.940978] io scheduler deadline registered (default)
[    1.941050] io scheduler cfq registered
[    1.942369] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.942408] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.942510] intel_idle: MWAIT substates: 0x42120
[    1.942514] intel_idle: v0.4 model 0x3C
[    1.942516] intel_idle: lapic_timer_reliable_states 0xffffffff
[    1.943482] ACPI: AC Adapter [ACAD] (off-line)
[    1.943737] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:27/PNP0C0D:01/input/input0
[    1.943788] ACPI: Lid Switch [LID0]
[    1.943894] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1
[    1.943901] ACPI: Power Button [PWRB]
[    1.943986] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    1.943992] ACPI: Power Button [PWRF]
[    1.944936] thermal LNXTHERM:00: registered as thermal_zone0
[    1.944940] ACPI: Thermal Zone [TZ00] (28 C)
[    1.945454] thermal LNXTHERM:01: registered as thermal_zone1
[    1.945458] ACPI: Thermal Zone [TZ01] (30 C)
[    1.945540] GHES: HEST is not enabled!
[    1.945771] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.976111] ACPI: Battery Slot [BAT1] (battery present)
[    1.976435] Linux agpgart interface v0.103
[    1.979970] brd: module loaded
[    1.981536] loop: module loaded
[    1.982021] libphy: Fixed MDIO Bus: probed
[    1.982028] tun: Universal TUN/TAP device driver, 1.6
[    1.982031] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.982151] PPP generic driver version 2.4.2
[    1.982607] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    1.982621] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 1
[    1.983777] xhci_hcd 0000:00:14.0: cache line size of 64 is not supported
[    1.983958] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    1.983963] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.983967] usb usb1: Product: xHCI Host Controller
[    1.983971] usb usb1: Manufacturer: Linux 3.19.0-42-generic xhci-hcd
[    1.983974] usb usb1: SerialNumber: 0000:00:14.0
[    1.984266] hub 1-0:1.0: USB hub found
[    1.984296] hub 1-0:1.0: 14 ports detected
[    1.995819] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    1.995828] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 2
[    1.995922] usb usb2: New USB device found, idVendor=1d6b, idProduct=0003
[    1.995926] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.995930] usb usb2: Product: xHCI Host Controller
[    1.995934] usb usb2: Manufacturer: Linux 3.19.0-42-generic xhci-hcd
[    1.995937] usb usb2: SerialNumber: 0000:00:14.0
[    1.996238] hub 2-0:1.0: USB hub found
[    1.996263] hub 2-0:1.0: 6 ports detected
[    2.001763] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.001788] ehci-pci: EHCI PCI platform driver
[    2.002024] ehci-pci 0000:00:1a.0: EHCI Host Controller
[    2.002036] ehci-pci 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    2.002063] ehci-pci 0000:00:1a.0: debug port 2
[    2.005998] ehci-pci 0000:00:1a.0: cache line size of 64 is not supported
[    2.006030] ehci-pci 0000:00:1a.0: irq 16, io mem 0xf7523000
[    2.016049] ehci-pci 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    2.016123] usb usb3: New USB device found, idVendor=1d6b, idProduct=0002
[    2.016127] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    2.016131] usb usb3: Product: EHCI Host Controller
[    2.016135] usb usb3: Manufacturer: Linux 3.19.0-42-generic ehci_hcd
[    2.016138] usb usb3: SerialNumber: 0000:00:1a.0
[    2.016423] hub 3-0:1.0: USB hub found
[    2.016434] hub 3-0:1.0: 2 ports detected
[    2.016914] ehci-pci 0000:00:1d.0: EHCI Host Controller
[    2.016926] ehci-pci 0000:00:1d.0: new USB bus registered, assigned bus number 4
[    2.016953] ehci-pci 0000:00:1d.0: debug port 2
[    2.020860] ehci-pci 0000:00:1d.0: cache line size of 64 is not supported
[    2.020886] ehci-pci 0000:00:1d.0: irq 22, io mem 0xf7522000
[    2.032042] ehci-pci 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    2.032123] usb usb4: New USB device found, idVendor=1d6b, idProduct=0002
[    2.032127] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    2.032131] usb usb4: Product: EHCI Host Controller
[    2.032135] usb usb4: Manufacturer: Linux 3.19.0-42-generic ehci_hcd
[    2.032138] usb usb4: SerialNumber: 0000:00:1d.0
[    2.032482] hub 4-0:1.0: USB hub found
[    2.032498] hub 4-0:1.0: 2 ports detected
[    2.032806] ehci-platform: EHCI generic platform driver
[    2.032832] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.032845] ohci-pci: OHCI PCI platform driver
[    2.032871] ohci-platform: OHCI generic platform driver
[    2.032891] uhci_hcd: USB Universal Host Controller Interface driver
[    2.033013] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    2.072911] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.072921] serio: i8042 AUX port at 0x60,0x64 irq 12
[    2.073323] mousedev: PS/2 mouse device common for all mice
[    2.076998] rtc_cmos 00:04: RTC can wake from S4
[    2.077253] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    2.077308] rtc_cmos 00:04: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    2.077329] i2c /dev entries driver
[    2.077480] device-mapper: uevent: version 1.0.3
[    2.077690] device-mapper: ioctl: 4.29.0-ioctl (2014-10-28) initialised: [email]dm-devel@redhat.com[/email]
[    2.077737] Intel P-state driver initializing.
[    2.078063] Consider also installing thermald for improved thermal control.
[    2.078069] ledtrig-cpu: registered to indicate activity on CPUs
[    2.078324] PCCT header not found.
[    2.078325] ACPI PCC probe failed.
[    2.078429] TCP: cubic registered
[    2.078506] NET: Registered protocol family 10
[    2.078691] NET: Registered protocol family 17
[    2.078700] Key type dns_resolver registered
[    2.079148] Loading compiled-in X.509 certificates
[    2.079833] Loaded X.509 cert 'Magrathea: Glacier signing key: 759bcd6455a9dfaba6111485d04eded53ab83150'
[    2.079847] registered taskstats version 1
[    2.081314] Key type trusted registered
[    2.084154] Key type encrypted registered
[    2.084161] AppArmor: AppArmor sha1 policy hashing enabled
[    2.084164] ima: No TPM chip found, activating TPM-bypass!
[    2.084178] evm: HMAC attrs: 0x1
[    2.085010]   Magic number: 11:283:638
[    2.085118] rtc_cmos 00:04: setting system clock to 2015-12-29 14:38:46 UTC (1451399926)
[    2.085243] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.085245] EDD information not available.
[    2.085300] PM: Hibernation image not present or could not be loaded.
[    2.085588] Freeing unused kernel memory: 1408K (ffffffff81d27000 - ffffffff81e87000)
[    2.085590] Write protecting the kernel read-only data: 12288k
[    2.085776] Freeing unused kernel memory: 256K (ffff8800017c0000 - ffff880001800000)
[    2.085878] Freeing unused kernel memory: 340K (ffff880001bab000 - ffff880001c00000)
[    2.095408] systemd-udevd[148]: starting version 204
[    2.104765] sdhci: Secure Digital Host Controller Interface driver
[    2.104768] sdhci: Copyright(c) Pierre Ossman
[    2.106112] wmi: Mapper loaded
[    2.114044] rtsx_pci 0000:04:00.0: rtsx_pci_acquire_irq: pcr->msi_en = 1, pci->irq = 28
[    2.115545] ahci 0000:00:1f.2: version 3.0
[    2.115781] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 6 Gbps 0x1 impl RAID mode
[    2.115783] ahci 0000:00:1f.2: flags: 64bit ncq pm led clo pio slum part ems apst 
[    2.117357] alx 0000:02:00.0 eth0: Qualcomm Atheros AR816x/AR817x Ethernet [34:e6:d7:4e:78:a4]
[    2.117755] [drm] Initialized drm 1.1.0 20060810
[    2.118272] scsi host0: ahci
[    2.118397] scsi host1: ahci
[    2.118499] scsi host2: ahci
[    2.118610] scsi host3: ahci
[    2.118708] scsi host4: ahci
[    2.118808] scsi host5: ahci
[    2.118851] ata1: SATA max UDMA/133 abar m2048@0xf7521000 port 0xf7521100 irq 29
[    2.118853] ata2: DUMMY
[    2.118853] ata3: DUMMY
[    2.118854] ata4: DUMMY
[    2.118855] ata5: DUMMY
[    2.118855] ata6: DUMMY
[    2.129380] AVX2 version of gcm_enc/dec engaged.
[    2.129383] AES CTR mode by8 optimization enabled
[    2.133409] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    2.139906] [drm] Memory usable by graphics device = 2048M
[    2.139910] [drm] Replacing VGA console driver
[    2.141652] MXM: GUID detected in BIOS
[    2.141672] Console: switching to colour dummy device 80x25
[     2.141742] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type  mismatch - Found [Buffer], ACPI requires [Package]  (20141107/nsarguments-95)
[    2.141818] ACPI Warning:  \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer],  ACPI requires [Package] (20141107/nsarguments-95)
[    2.142128] pci 0000:01:00.0: optimus capabilities: enabled, status dynamic power, hda bios codec supported
[    2.142131] VGA switcheroo: detected Optimus DSM method \_SB_.PCI0.PEG0.PEGP handle
[    2.142621] [drm] ACPI BIOS requests an excessive sleep of 2000 ms, using 1500 ms instead
[    2.164069] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[    2.164071] [drm] Driver supports precise vblank timestamp query.
[    2.164146] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[    2.282302] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[    2.282409] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input6
[    2.282553] ACPI Exception: AE_NOT_FOUND, Evaluating _DOD (20141107/video-1230)
[    2.282556] ACPI: Video Device [PEGP] (multi-head: no  rom: yes  post: no)
[    2.282605] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:12/LNXVIDEO:01/input/input7
[    2.282692] [drm] Initialized i915 1.6.0 20141121 for 0000:00:02.0 on minor 0
[    2.282873] nouveau  [  DEVICE][0000:01:00.0] BOOT0  : 0x124180a1
[    2.282875] nouveau  [  DEVICE][0000:01:00.0] Chipset: GM204 (NV124)
[    2.282876] nouveau  [  DEVICE][0000:01:00.0] Family : NV110
[    2.304237] usb 1-4: new full-speed USB device number 2 using xhci_hcd
[    2.328275] usb 3-1: new high-speed USB device number 2 using ehci-pci
[    2.344206] usb 4-1: new high-speed USB device number 2 using ehci-pci
[    2.352256] [drm] GMBUS [i915 gmbus vga] timed out, falling back to bit banging on pin 2
[    2.374589] fbcon: inteldrmfb (fb0) is primary device
[     2.433527] usb 1-4: config 1 interface 0 altsetting 0 has 2 endpoint  descriptors, different from the interface descriptor's value: 1
[    2.434626] usb 1-4: New USB device found, idVendor=187c, idProduct=0528
[    2.434627] usb 1-4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    2.434628] usb 1-4: Product: AW1517
[    2.434629] usb 1-4: Manufacturer: Alienware
[    2.434629] usb 1-4: SerialNumber: 15.0
[    2.434880] usb 1-4: ep 0x81 - rounding interval to 64 microframes, ep desc says 80 microframes
[    2.436373] ata1: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    2.438836] hidraw: raw HID events driver (C) Jiri Kosina
[    2.444498] usbcore: registered new interface driver usbhid
[    2.444498] usbhid: USB HID core driver
[     2.447508] hid-generic 0003:187C:0528.0001: hiddev0,hidraw0: USB HID  v1.01 Device [Alienware AW1517] on usb-0000:00:14.0-4/input0
[    2.455744] nouveau  [   VBIOS][0000:01:00.0] using image from PROM
[    2.455849] nouveau  [   VBIOS][0000:01:00.0] BIT signature found
[    2.455851] nouveau  [   VBIOS][0000:01:00.0] version 84.04.29.00.17
[    2.456825] nouveau  [ DEVINIT][0000:01:00.0] adaptor not initialised
[    2.460343] usb 3-1: New USB device found, idVendor=8087, idProduct=8008
[    2.460344] usb 3-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    2.460609] hub 3-1:1.0: USB hub found
[    2.460891] hub 3-1:1.0: 6 ports detected
[    2.476785] usb 4-1: New USB device found, idVendor=8087, idProduct=8000
[    2.476786] usb 4-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    2.477100] hub 4-1:1.0: USB hub found
[    2.477299] hub 4-1:1.0: 8 ports detected
[    2.483384] nouveau  [     PMC][0000:01:00.0] MSI interrupts enabled
[    2.483415] nouveau  [     PFB][0000:01:00.0] RAM type: GDDR5
[    2.483416] nouveau  [     PFB][0000:01:00.0] RAM size: 3072 MiB
[    2.483417] nouveau  [     PFB][0000:01:00.0]    ZCOMP: 0 tags
[    2.483486] nouveau E[   PIBUS][0000:01:00.0] HUB0: 0x10ecc0 0xffffffff (0x1e40822c)
[    2.483606] ata1.00: ATA-8: TOSHIBA MQ01ABD100, AX0P2D, max UDMA/100
[    2.483607] ata1.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    2.485128] vga_switcheroo: enabled
[    2.485219] [TTM] Zone  kernel: Available graphics memory: 4029288 kiB
[    2.485220] [TTM] Zone   dma32: Available graphics memory: 2097152 kiB
[    2.485220] [TTM] Initializing pool allocator
[    2.485223] [TTM] Initializing DMA pool allocator
[    2.485228] nouveau  [     DRM] VRAM: 3072 MiB
[    2.485229] nouveau  [     DRM] GART: 1048576 MiB
[    2.485231] nouveau W[     DRM] Pointer to TMDS table invalid
[    2.485231] nouveau  [     DRM] DCB version 4.1
[    2.485232] nouveau W[     DRM] Pointer to flat panel table invalid
[    2.485242] nouveau E[     DRM] failed to initialise sync subsystem, -38
[    2.485246] [drm] Initialized nouveau 1.2.1 20120801 for 0000:01:00.0 on minor 1
[    2.485314] ata1.00: configured for UDMA/100
[    2.485405] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MQ01ABD1 2D   PQ: 0 ANSI: 5
[    2.485570] sd 0:0:0:0: [sda] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    2.485571] sd 0:0:0:0: [sda] 4096-byte physical blocks
[    2.485591] sd 0:0:0:0: [sda] Write Protect is off
[    2.485593] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.485602] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.485634] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.581693]  sda: sda1 sda2 < sda5 >
[    2.582093] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.600107] usb 1-9: new full-speed USB device number 3 using xhci_hcd
[    2.729093] usb 1-9: New USB device found, idVendor=0cf3, idProduct=3004
[    2.729095] usb 1-9: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    2.896106] usb 1-13: new high-speed USB device number 4 using xhci_hcd
[    3.153870] usb 1-13: New USB device found, idVendor=0c45, idProduct=6708
[    3.153871] usb 1-13: New USB device strings: Mfr=2, Product=1, SerialNumber=0
[    3.153873] usb 1-13: Product: Integrated_Webcam_FHD
[    3.153873] usb 1-13: Manufacturer: CN036P59724874BDA3YCA00
[    3.412098] Console: switching to colour frame buffer device 240x67
[    3.415646] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[    3.415647] i915 0000:00:02.0: registered panic notifier
[    3.492454] psmouse serio1: synaptics: queried max coordinates: x [..5668], y [..4756]
[    3.610066] psmouse serio1: synaptics: queried min coordinates: x [1274..], y [1098..]
[     3.830591] psmouse serio1: synaptics: Touchpad model: 1, fw: 8.1, id:  0x1e2b1, caps: 0xd00123/0x840300/0x26c00, board id: 2417, fw id: 1365292
[    3.966815] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input5
[     7.772113] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type  mismatch - Found [Buffer], ACPI requires [Package]  (20141107/nsarguments-95)
[    7.772456] ACPI: \_SB_.PCI0.PEG0.PEGP: failed to evaluate _DSM
[     7.772459] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type  mismatch - Found [Buffer], ACPI requires [Package]  (20141107/nsarguments-95)
[   12.784788] random: nonblocking pool is initialized
[   57.278789] EXT4-fs (dm-1): mounted filesystem with ordered data mode. Opts: (null)
[   63.489376] Adding 8269820k swap on /dev/mapper/ubuntu--vg-swap_1.  Priority:-1 extents:1 across:8269820k FS
[   63.796530] systemd-udevd[508]: starting version 204
[   63.905713] EXT4-fs (dm-1): re-mounted. Opts: errors=remount-ro
[   64.038374] lp: driver loaded but no devices found
[   64.041881] ppdev: user-space parallel port driver
[   64.091767] EXT4-fs (sda1): mounting ext2 file system using the ext4 subsystem
[   64.123132] EDAC MC: Ver: 3.0.0
[   64.124435] EDAC ie31200: No ECC support
[   64.125135] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   64.129576] EXT4-fs (sda1): mounted filesystem without journal. Opts: (null)
[   64.135730] snd_hda_intel 0000:00:03.0: bound 0000:00:02.0 (ops i915_audio_component_bind_ops [i915])
[   64.150284] Bluetooth: Core ver 2.20
[   64.150299] NET: Registered protocol family 31
[   64.150300] Bluetooth: HCI device and connection manager initialized
[   64.150307] Bluetooth: HCI socket layer initialized
[   64.150309] Bluetooth: L2CAP socket layer initialized
[   64.150314] Bluetooth: SCO socket layer initialized
[   64.151886] usbcore: registered new interface driver btusb
[   64.151976] sound hdaudioC1D0: autoconfig: line_outs=1 (0xb/0x0/0x0/0x0/0x0) type:speaker
[   64.151979] sound hdaudioC1D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   64.151982] sound hdaudioC1D0:    hp_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   64.151983] sound hdaudioC1D0:    mono: mono_out=0x0
[   64.151985] sound hdaudioC1D0:    inputs:
[   64.151986] sound hdaudioC1D0:      Mic=0x12
[   64.151988] sound hdaudioC1D0:      Line=0x11
[   64.184975] input: Dell WMI hotkeys as /devices/virtual/input/input8
[   64.468977] intel_rapl: Found RAPL domain package
[   64.468981] intel_rapl: Found RAPL domain core
[   64.468983] intel_rapl: Found RAPL domain uncore
[   64.468984] intel_rapl: Found RAPL domain dram
[   64.483685] input: HDA Intel HDMI HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:03.0/sound/card0/input9
[   64.483747] input: HDA Intel HDMI HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:03.0/sound/card0/input10
[   64.483811] input: HDA Intel HDMI HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:03.0/sound/card0/input11
[   64.500480] usb 1-9: Direct firmware load for ar3k/AthrBT_0x00000200.dfu failed with error -2
[   64.500484] Bluetooth: Patch file not found ar3k/AthrBT_0x00000200.dfu
[   64.500510] Bluetooth: Loading patch file failed
[   64.500529] ath3k: probe of 1-9:1.0 failed with error -2
[   64.500559] usbcore: registered new interface driver ath3k
[    64.530108] audit: type=1400 audit(1451399988.940:2): apparmor="STATUS"  operation="profile_load" profile="unconfined" name="/sbin/dhclient"  pid=670 comm="apparmor_parser"
[   64.530114] audit: type=1400  audit(1451399988.940:3): apparmor="STATUS" operation="profile_load"  profile="unconfined"  name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=670  comm="apparmor_parser"
[   64.530117] audit: type=1400  audit(1451399988.940:4): apparmor="STATUS" operation="profile_load"  profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script"  pid=670 comm="apparmor_parser"
[   64.530125] audit: type=1400  audit(1451399988.940:5): apparmor="STATUS" operation="profile_replace"  profile="unconfined" name="/sbin/dhclient" pid=669  comm="apparmor_parser"
[   64.530130] audit: type=1400  audit(1451399988.940:6): apparmor="STATUS" operation="profile_replace"  profile="unconfined"  name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=669  comm="apparmor_parser"
[   64.530134] audit: type=1400  audit(1451399988.940:7): apparmor="STATUS" operation="profile_replace"  profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script"  pid=669 comm="apparmor_parser"
[   64.530419] audit: type=1400  audit(1451399988.940:8): apparmor="STATUS" operation="profile_replace"  profile="unconfined"  name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=670  comm="apparmor_parser"
[   64.530423] audit: type=1400  audit(1451399988.940:9): apparmor="STATUS" operation="profile_replace"  profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script"  pid=670 comm="apparmor_parser"
[   64.530441] audit: type=1400  audit(1451399988.940:10): apparmor="STATUS" operation="profile_replace"  profile="unconfined"  name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=669  comm="apparmor_parser"
[   64.530446] audit: type=1400  audit(1451399988.940:11): apparmor="STATUS" operation="profile_replace"  profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script"  pid=669 comm="apparmor_parser"
[   64.717301] media: Linux media interface: v0.10
[   64.719805] Linux video capture interface: v2.00
[   64.725096] uvcvideo: Found UVC 1.00 device Integrated_Webcam_FHD (0c45:6708)
[   64.766070] input: Integrated_Webcam_FHD as /devices/pci0000:00/0000:00:14.0/usb1/1-13/1-13:1.0/input/input12
[   64.766194] usbcore: registered new interface driver uvcvideo
[   64.766196] USB Video Class driver (1.1.1)
[   65.177267] init: failsafe main process (769) killed by TERM signal
[   65.188262] ca0132 DOWNLOAD OK :-) DSP IS RUNNING.
[   65.433944] input: HDA Intel PCH Line as /devices/pci0000:00/0000:00:1b.0/sound/card1/input13
[   65.936575] Bluetooth: RFCOMM TTY layer initialized
[   65.936582] Bluetooth: RFCOMM socket layer initialized
[   65.936586] Bluetooth: RFCOMM ver 1.11
[   65.940261] init: cups main process (865) killed by HUP signal
[   65.940274] init: cups main process ended, respawning
[   65.983538] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   65.983541] Bluetooth: BNEP filters: protocol multicast
[   65.983543] Bluetooth: BNEP socket layer initialized
[   67.454434] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   67.455442] alx 0000:02:00.0 eth0: NIC Up: 1 Gbps Full
[   67.456188] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   70.380109] nouveau E[   PIBUS][0000:01:00.0] HUB0: 0x10ecc0 0xffffffff (0x1b40822c)
[   71.518011] init: plymouth-upstart-bridge main process ended, respawning
[   71.521495] init: plymouth-upstart-bridge main process (1622) terminated with status 1
[   71.521507] init: plymouth-upstart-bridge main process ended, respawning
[    76.748049] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type  mismatch - Found [Buffer], ACPI requires [Package]  (20141107/nsarguments-95)
[   76.748321] ACPI: \_SB_.PCI0.PEG0.PEGP: failed to evaluate _DSM
[    76.748324] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type  mismatch - Found [Buffer], ACPI requires [Package]  (20141107/nsarguments-95)
[   89.840309] ca0132 DOWNLOAD OK :-) DSP IS RUNNING.
[   95.443210] audit_printk_skb: 168 callbacks suppressed
[    95.443212] audit: type=1400 audit(1451400019.853:68): apparmor="STATUS"  operation="profile_replace" profile="unconfined"  name="/usr/lib/cups/backend/cups-pdf" pid=2457 comm="apparmor_parser"
[    95.443217] audit: type=1400 audit(1451400019.853:69): apparmor="STATUS"  operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd"  pid=2457 comm="apparmor_parser"
[   95.443439] audit: type=1400  audit(1451400019.853:70): apparmor="STATUS" operation="profile_replace"  profile="unconfined" name="/usr/sbin/cupsd" pid=2457  comm="apparmor_parser"
[  101.373598] alx 0000:02:00.0 eth0: Link Down
[  140.096833] alx 0000:02:00.0 eth0: NIC Up: 1 Gbps Full
[  1536.625166] systemd-hostnamed[5661]: Warning: nss-myhostname is not  installed. Changing the local hostname might make it unresolveable.  Please install nss-myhostname!
[ 1784.251550] atkbd serio0: Unknown key pressed (translated set 2, code 0x84 on isa0060/serio0).
[ 1784.251560] atkbd serio0: Use 'setkeycodes e004 <keycode>' to make it known.
[ 1784.268383] atkbd serio0: Unknown key released (translated set 2, code 0x84 on isa0060/serio0).
[ 1784.268398] atkbd serio0: Use 'setkeycodes e004 <keycode>' to make it known.
[ 3997.604042] nouveau E[   PIBUS][0000:01:00.0] HUB0: 0x10ecc0 0xffffffff (0x1b40822c)
[  4002.748149] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type  mismatch - Found [Buffer], ACPI requires [Package]  (20141107/nsarguments-95)
[ 4002.748961] ACPI: \_SB_.PCI0.PEG0.PEGP: failed to evaluate _DSM
[  4002.748974] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type  mismatch - Found [Buffer], ACPI requires [Package]  (20141107/nsarguments-95)
[ 4369.829806] e100: Intel(R) PRO/100 Network Driver, 3.5.24-k2-NAPI
[ 4369.829808] e100: Copyright(c) 1999-2006 Intel Corporation
[ 4667.044225] [Firmware Bug]: battery: (dis)charge rate invalid.


lshw -c network

WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: Killer E2200 Gigabit Ethernet Controller
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 10
       serial: 34:e6:d7:4e:78:a4
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=alx duplex=full ip=192.168.2.101 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:35 memory:f7400000-f743ffff ioport:d000(size=128)
  *-network UNCLAIMED
       description: Network controller
       product: Qualcomm Atheros
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 20
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: memory:f6800000-f69fffff
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.

rfkill list all

0: dell-rbtn: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes

---

### Post by chili555 on 2015-12-29
We need more information about your device. Please run and post:```
lspci -nn | grep 0280
```Thanks.

---

