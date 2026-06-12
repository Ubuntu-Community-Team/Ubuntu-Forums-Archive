---
title: "Intel Wireless 8260 fails after suspend"
date: 2016-03-03
forum: Networking &amp; Wireless
---

### Post by Astro96 on 2016-03-03
Hello,

I have an Alienware 15 R2 with the Intel 8260 3x3 802.11ac card.  The card works fine on Ubuntu 15.10 except that after suspend it does not work at all.


**Steps I have tried:**
1. I have added iwlwifi to SUSPEND_MODULES in /etc/pm/config.d/modules
1. a. I confirmed in /var/log that the module was removed and added before and after sleep
1. b. I have manually ```
modprobe -r iwlwifi
``` before suspend and re-added it after.

2. I upgraded to kernel 4.3.6 and installed the latest firmware iwlwifi-8000-ucode-16.242414.0 from [https://wireless.wiki.kernel.org/en/users/drivers/iwlwifi](https://wireless.wiki.kernel.org/en/users/drivers/iwlwifi) into /lib/firmware and confirmed that it loaded the correct version via ethtool -i wlp60s0

3. I tried ```
modprobe -r btintel
``` before suspen, but that also caused no change.

Here's my dmesg after a suspend with the latest driver:

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 4.3.6-040306-generic (kernel@gloin) (gcc version 5.2.1 20151010 (Ubuntu 5.2.1-22ubuntu2) ) #201602191831 SMP Fri Feb 19 23:33:41 UTC 2016
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-4.3.6-040306-generic root=UUID=03997fc3-18da-4551-bcc2-7366936f0616 ro noprompt persistent quiet splash vt.handoff=7
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
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x000000002fa81fff] usable
[    0.000000] BIOS-e820: [mem 0x000000002fa82000-0x000000002fa82fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x000000002fa83000-0x000000002faccfff] reserved
[    0.000000] BIOS-e820: [mem 0x000000002facd000-0x000000002fb24fff] usable
[    0.000000] BIOS-e820: [mem 0x000000002fb25000-0x0000000030087fff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000030088000-0x00000000361aafff] usable
[    0.000000] BIOS-e820: [mem 0x00000000361ab000-0x00000000371c4fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000371c5000-0x0000000037205fff] ACPI data
[    0.000000] BIOS-e820: [mem 0x0000000037206000-0x0000000037b86fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x0000000037b87000-0x0000000037f82fff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000037f83000-0x0000000037ffdfff] type 20
[    0.000000] BIOS-e820: [mem 0x0000000037ffe000-0x0000000037ffefff] usable
[    0.000000] BIOS-e820: [mem 0x0000000038000000-0x00000000380fffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000e0000000-0x00000000efffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fe000000-0x00000000fe010fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ff000000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x00000004c3ffffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] efi: EFI v2.40 by American Megatrends
[    0.000000] efi:  ESRT=0x37f7f018  ACPI=0x371d2000  ACPI 2.0=0x371d2000  SMBIOS=0x37ec9000 
[    0.000000] esrt: Reserving ESRT space from 0x0000000037f7f018 to 0x0000000037f7f050.
[    0.000000] SMBIOS 2.8 present.
[    0.000000] DMI: Alienware Alienware 15 R2/Alienware 15 R2, BIOS 1.2.3 11/11/2015
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] e820: last_pfn = 0x4c4000 max_arch_pfn = 0x400000000
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
[    0.000000] BRK [0x02ff4000, 0x02ff4fff] PGTABLE
[    0.000000] BRK [0x02ff5000, 0x02ff5fff] PGTABLE
[    0.000000] BRK [0x02ff6000, 0x02ff6fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x4c3e00000-0x4c3ffffff]
[    0.000000]  [mem 0x4c3e00000-0x4c3ffffff] page 2M
[    0.000000] BRK [0x02ff7000, 0x02ff7fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x4c0000000-0x4c3dfffff]
[    0.000000]  [mem 0x4c0000000-0x4c3dfffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x4a0000000-0x4bfffffff]
[    0.000000]  [mem 0x4a0000000-0x4bfffffff] page 1G
[    0.000000] init_memory_mapping: [mem 0x00100000-0x2fa81fff]
[    0.000000]  [mem 0x00100000-0x001fffff] page 4k
[    0.000000]  [mem 0x00200000-0x2f9fffff] page 2M
[    0.000000]  [mem 0x2fa00000-0x2fa81fff] page 4k
[    0.000000] init_memory_mapping: [mem 0x2facd000-0x2fb24fff]
[    0.000000]  [mem 0x2facd000-0x2fb24fff] page 4k
[    0.000000] init_memory_mapping: [mem 0x30088000-0x361aafff]
[    0.000000]  [mem 0x30088000-0x301fffff] page 4k
[    0.000000]  [mem 0x30200000-0x35ffffff] page 2M
[    0.000000]  [mem 0x36000000-0x361aafff] page 4k
[    0.000000] BRK [0x02ff8000, 0x02ff8fff] PGTABLE
[    0.000000] BRK [0x02ff9000, 0x02ff9fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x37ffe000-0x37ffefff]
[    0.000000]  [mem 0x37ffe000-0x37ffefff] page 4k
[    0.000000] init_memory_mapping: [mem 0x100000000-0x49fffffff]
[    0.000000]  [mem 0x100000000-0x49fffffff] page 1G
[    0.000000] RAMDISK: [mem 0x29b4b000-0x2bac1fff]
[    0.000000] ACPI: Early table checksum verification disabled
[    0.000000] ACPI: RSDP 0x00000000371D2000 000024 (v02 ALWARE)
[    0.000000] ACPI: XSDT 0x00000000371D20B8 0000F4 (v01 ALWARE ALIENWRE 01072009 AMI  00010013)
[    0.000000] ACPI: FACP 0x00000000371F54D0 00010C (v05 ALWARE ALIENWRE 01072009 AMI  00010013)
[    0.000000] ACPI: DSDT 0x00000000371D2240 02328A (v02 ALWARE ALIENWRE 01072009 INTL 20120913)
[    0.000000] ACPI: FACS 0x0000000037B85F80 000040
[    0.000000] ACPI: APIC 0x00000000371F55E0 0000BC (v03 ALWARE ALIENWRE 01072009 AMI  00010013)
[    0.000000] ACPI: FPDT 0x00000000371F56A0 000044 (v01 ALWARE ALIENWRE 01072009 AMI  00010013)
[    0.000000] ACPI: FIDT 0x00000000371F56E8 00009C (v01 ALWARE ALIENWRE 01072009 AMI  00010013)
[    0.000000] ACPI: MCFG 0x00000000371F5788 00003C (v01 ALWARE ALIENWRE 01072009 MSFT 00000097)
[    0.000000] ACPI: HPET 0x00000000371F57C8 000038 (v01 ALWARE ALIENWRE 01072009 AMI. 0005000B)
[    0.000000] ACPI: SSDT 0x00000000371F5800 0004B9 (v01 SataRe SataTabl 00001000 INTL 20120913)
[    0.000000] ACPI: LPIT 0x00000000371F5CC0 000094 (v01 INTEL  SKL      00000000 MSFT 0000005F)
[    0.000000] ACPI: SSDT 0x00000000371F5D58 000248 (v02 INTEL  sensrhub 00000000 INTL 20120913)
[    0.000000] ACPI: SSDT 0x00000000371F5FA0 002BAE (v02 INTEL  PtidDevc 00001000 INTL 20120913)
[    0.000000] ACPI: DBGP 0x00000000371F8B50 000034 (v01 INTEL           00000000 MSFT 0000005F)
[    0.000000] ACPI: DBG2 0x00000000371F8B88 000054 (v00 INTEL           00000000 MSFT 0000005F)
[    0.000000] ACPI: SSDT 0x00000000371F8BE0 00069D (v02 INTEL  xh_rvp10 00000000 INTL 20120913)
[    0.000000] ACPI: SSDT 0x00000000371F9280 003489 (v02 DptfTa DptfTabl 00001000 INTL 20120913)
[    0.000000] ACPI: TPM2 0x00000000371FC710 000034 (v03        Tpm2Tabl 00000001 AMI  00000000)
[    0.000000] ACPI: SSDT 0x00000000371FC748 00080B (v01 AMITCG _SynTCG_ 00000001 INTL 20120913)
[    0.000000] ACPI: SSDT 0x00000000371FCF58 005580 (v02 SaSsdt SaSsdt   00003000 INTL 20120913)
[    0.000000] ACPI: UEFI 0x00000000372024D8 000042 (v01                 00000000      00000000)
[    0.000000] ACPI: MSDM 0x0000000037202520 000055 (v03 ALWARE ALIENWRE 01072009 AMI  00010013)
[    0.000000] ACPI: SSDT 0x0000000037202578 000E58 (v02 CpuRef CpuSsdt  00003000 INTL 20120913)
[    0.000000] ACPI: BGRT 0x00000000372033D0 000038 (v01 ALWARE ALIENWRE 01072009 AMI  00010013)
[    0.000000] ACPI: SSDT 0x0000000037203408 0000CE (v02 SgRef  SgPeg    00001000 INTL 20120913)
[    0.000000] ACPI: DMAR 0x00000000372034D8 0000A8 (v01 INTEL  SKL      00000001 INTL 00000001)
[    0.000000] ACPI: UEFI 0x0000000037203580 00063A (v01 INTEL  RstSataE 00000000 ??   00000000)
[    0.000000] ACPI: UEFI 0x0000000037203BC0 00005C (v01 INTEL  RstSataV 00000000 ??   00000000)
[    0.000000] ACPI: SSDT 0x0000000037203C20 00198C (v01 OptRef OptTabl  00001000 INTL 20120913)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x00000004c3ffffff]
[    0.000000] NODE_DATA(0) allocated [mem 0x4c3ff9000-0x4c3ffdfff]
[    0.000000]  [ffffea0000000000-ffffea00131fffff] PMD -> [ffff8804b3600000-ffff8804c35fffff] on node 0
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x0000000000001000-0x0000000000ffffff]
[    0.000000]   DMA32    [mem 0x0000000001000000-0x00000000ffffffff]
[    0.000000]   Normal   [mem 0x0000000100000000-0x00000004c3ffffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x0000000000001000-0x0000000000057fff]
[    0.000000]   node   0: [mem 0x0000000000059000-0x000000000009dfff]
[    0.000000]   node   0: [mem 0x0000000000100000-0x000000002fa81fff]
[    0.000000]   node   0: [mem 0x000000002facd000-0x000000002fb24fff]
[    0.000000]   node   0: [mem 0x0000000030088000-0x00000000361aafff]
[    0.000000]   node   0: [mem 0x0000000037ffe000-0x0000000037ffefff]
[    0.000000]   node   0: [mem 0x0000000100000000-0x00000004c3ffffff]
[    0.000000] Initmem setup node 0 [mem 0x0000000000001000-0x00000004c3ffffff]
[    0.000000] On node 0 totalpages: 4168602
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 22 pages reserved
[    0.000000]   DMA zone: 3996 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 3376 pages used for memmap
[    0.000000]   DMA32 zone: 216062 pages, LIFO batch:31
[    0.000000]   Normal zone: 61696 pages used for memmap
[    0.000000]   Normal zone: 3948544 pages, LIFO batch:31
[    0.000000] Reserving Intel graphics stolen memory at 0x39000000-0x3affffff
[    0.000000] ACPI: PM-Timer IO Port: 0x1808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x04] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x05] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x06] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x07] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x08] high edge lint[0x1])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-119
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a701 base: 0xfed00000
[    0.000000] smpboot: Allowing 8 CPUs, 0 hotplug CPUs
[    0.000000] PM: Registered nosave memory: [mem 0x00000000-0x00000fff]
[    0.000000] PM: Registered nosave memory: [mem 0x00058000-0x00058fff]
[    0.000000] PM: Registered nosave memory: [mem 0x0009e000-0x0009ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000fffff]
[    0.000000] PM: Registered nosave memory: [mem 0x2fa82000-0x2fa82fff]
[    0.000000] PM: Registered nosave memory: [mem 0x2fa83000-0x2faccfff]
[    0.000000] PM: Registered nosave memory: [mem 0x2fb25000-0x30087fff]
[    0.000000] PM: Registered nosave memory: [mem 0x361ab000-0x371c4fff]
[    0.000000] PM: Registered nosave memory: [mem 0x371c5000-0x37205fff]
[    0.000000] PM: Registered nosave memory: [mem 0x37206000-0x37b86fff]
[    0.000000] PM: Registered nosave memory: [mem 0x37b87000-0x37f82fff]
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
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:8 nr_node_ids:1
[    0.000000] PERCPU: Embedded 33 pages/cpu @ffff8804c3c00000 s97240 r8192 d29736 u262144
[    0.000000] pcpu-alloc: s97240 r8192 d29736 u262144 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 4103444
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.3.6-040306-generic root=UUID=03997fc3-18da-4551-bcc2-7366936f0616 ro noprompt persistent quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 16195804K/16674408K available (8134K kernel code, 1248K rwdata, 3904K rodata, 1456K init, 1300K bss, 478604K reserved, 0K cma-reserved)
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	Build-time adjustment of leaf fanout to 64.
[    0.000000] 	RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=8.
[    0.000000] RCU: Adjusting geometry for rcu_fanout_leaf=64, nr_cpu_ids=8
[    0.000000] NR_IRQS:16640 nr_irqs:2048 16
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] clocksource: hpet: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 79635855245 ns
[    0.000000] hpet clockevent registered
[    0.000000] tsc: PIT calibration matches HPET. 1 loops
[    0.000000] tsc: Detected 2591.954 MHz processor
[    0.000022] Calibrating delay loop (skipped), value calculated using timer frequency.. 5183.90 BogoMIPS (lpj=10367816)
[    0.000024] pid_max: default: 32768 minimum: 301
[    0.000028] ACPI: Core revision 20150818
[    0.021791] ACPI Error: [\_SB_.PCI0.XHC_.RHUB.HS11] Namespace lookup failure, AE_NOT_FOUND (20150818/dswload-210)
[    0.021795] ACPI Exception: AE_NOT_FOUND, During name lookup/catalog (20150818/psobject-227)
[    0.021822] ACPI Exception: AE_NOT_FOUND, (SSDT:xh_rvp10) while loading table (20150818/tbxfload-193)
[    0.032511] ACPI Error: 1 table load failures, 10 successful (20150818/tbxfload-214)
[    0.034195] Security Framework initialized
[    0.034200] Yama: becoming mindful.
[    0.034209] AppArmor: AppArmor initialized
[    0.034957] Dentry cache hash table entries: 2097152 (order: 12, 16777216 bytes)
[    0.037541] Inode-cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.038550] Mount-cache hash table entries: 32768 (order: 6, 262144 bytes)
[    0.038563] Mountpoint-cache hash table entries: 32768 (order: 6, 262144 bytes)
[    0.038737] Initializing cgroup subsys io
[    0.038740] Initializing cgroup subsys memory
[    0.038744] Initializing cgroup subsys devices
[    0.038746] Initializing cgroup subsys freezer
[    0.038747] Initializing cgroup subsys net_cls
[    0.038749] Initializing cgroup subsys perf_event
[    0.038750] Initializing cgroup subsys net_prio
[    0.038751] Initializing cgroup subsys hugetlb
[    0.038753] Initializing cgroup subsys pids
[    0.038772] CPU: Physical Processor ID: 0
[    0.038773] CPU: Processor Core ID: 0
[    0.038776] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
[    0.038776] ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
[    0.039782] mce: CPU supports 10 MCE banks
[    0.039797] CPU0: Thermal monitoring enabled (TM1)
[    0.039805] process: using mwait in idle threads
[    0.039807] Last level iTLB entries: 4KB 64, 2MB 8, 4MB 8
[    0.039808] Last level dTLB entries: 4KB 64, 2MB 0, 4MB 0, 1GB 4
[    0.040085] Freeing SMP alternatives memory: 28K (ffffffff81ea6000 - ffffffff81ead000)
[    0.043887] ftrace: allocating 31176 entries in 122 pages
[    0.054105] DMAR: Host address width 39
[    0.054108] DMAR: DRHD base: 0x000000fed90000 flags: 0x0
[    0.054114] DMAR: dmar0: reg_base_addr fed90000 ver 1:0 cap 1c0000c40660462 ecap 7e3ff0501e
[    0.054115] DMAR: DRHD base: 0x000000fed91000 flags: 0x1
[    0.054118] DMAR: dmar1: reg_base_addr fed91000 ver 1:0 cap d2008c40660462 ecap f050da
[    0.054119] DMAR: RMRR base: 0x000000370ef000 end: 0x0000003710efff
[    0.054120] DMAR: RMRR base: 0x00000038800000 end: 0x0000003affffff
[    0.054121] DMAR-IR: IOAPIC id 2 under DRHD base  0xfed91000 IOMMU 1
[    0.054122] DMAR-IR: HPET id 0 under DRHD base 0xfed91000
[    0.054123] DMAR-IR: x2apic is disabled because BIOS sets x2apic opt out bit.
[    0.054124] DMAR-IR: Use 'intremap=no_x2apic_optout' to override the BIOS setting.
[    0.055523] DMAR-IR: Enabled IRQ remapping in xapic mode
[    0.055524] x2apic: IRQ remapping doesn't support X2APIC mode
[    0.059645] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.099328] TSC deadline timer enabled
[    0.099333] smpboot: CPU0: Intel(R) Core(TM) i7-6700HQ CPU @ 2.60GHz (family: 0x6, model: 0x5e, stepping: 0x3)
[    0.099349] Performance Events: PEBS fmt3+, 32-deep LBR, Skylake events, full-width counters, Intel PMU driver.
[    0.099371] ... version:                4
[    0.099372] ... bit width:              48
[    0.099372] ... generic registers:      4
[    0.099373] ... value mask:             0000ffffffffffff
[    0.099373] ... max period:             0000ffffffffffff
[    0.099374] ... fixed-purpose events:   3
[    0.099374] ... event mask:             000000070000000f
[    0.099966] x86: Booting SMP configuration:
[    0.099967] .... node  #0, CPUs:      #1
[    0.103454] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.103510]  #2 #3 #4 #5 #6 #7
[    0.124644] x86: Booted up 1 node, 8 CPUs
[    0.124646] smpboot: Total of 8 processors activated (41471.26 BogoMIPS)
[    0.130926] devtmpfs: initialized
[    0.132918] evm: security.selinux
[    0.132919] evm: security.SMACK64
[    0.132920] evm: security.SMACK64EXEC
[    0.132920] evm: security.SMACK64TRANSMUTE
[    0.132921] evm: security.SMACK64MMAP
[    0.132922] evm: security.ima
[    0.132922] evm: security.capability
[    0.132972] PM: Registering ACPI NVS region [mem 0x2fa82000-0x2fa82fff] (4096 bytes)
[    0.132973] PM: Registering ACPI NVS region [mem 0x37206000-0x37b86fff] (9965568 bytes)
[    0.133109] clocksource: jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645041785100000 ns
[    0.133186] pinctrl core: initialized pinctrl subsystem
[    0.133356] RTC time: 10:28:46, date: 03/03/16
[    0.133443] NET: Registered protocol family 16
[    0.142740] cpuidle: using governor ladder
[    0.154739] cpuidle: using governor menu
[    0.154748] PCCT header not found.
[    0.154849] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.154851] ACPI: bus type PCI registered
[    0.154852] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.154922] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.154924] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    0.154934] PCI: Using configuration type 1 for base access
[    0.167071] ACPI: Added _OSI(Module Device)
[    0.167073] ACPI: Added _OSI(Processor Device)
[    0.167074] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.167075] ACPI: Added _OSI(Processor Aggregator Device)
[    0.174013] ACPI: Executed 21 blocks of module-level executable AML code
[    0.180030] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.184224] ACPI: Dynamic OEM Table Load:
[    0.184230] ACPI: SSDT 0xFFFF8804B0988C00 00037F (v02 PmRef  Cpu0Cst  00003001 INTL 20120913)
[    0.185085] ACPI: Dynamic OEM Table Load:
[    0.185090] ACPI: SSDT 0xFFFF8804B0DD3000 0005DC (v02 PmRef  Cpu0Ist  00003000 INTL 20120913)
[    0.186784] ACPI: Dynamic OEM Table Load:
[    0.186789] ACPI: SSDT 0xFFFF8804B0DD3800 0005AA (v02 PmRef  ApIst    00003000 INTL 20120913)
[    0.187708] ACPI: Dynamic OEM Table Load:
[    0.187712] ACPI: SSDT 0xFFFF8804B096E000 000119 (v02 PmRef  ApCst    00003000 INTL 20120913)
[    0.192306] ACPI : EC: EC started
[    0.192603] ACPI: Interpreter enabled
[    0.192611] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20150818/hwxface-580)
[    0.192618] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20150818/hwxface-580)
[    0.192633] ACPI: (supports S0 S3 S4 S5)
[    0.192634] ACPI: Using IOAPIC for interrupt routing
[    0.192659] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.194246] ACPI: Power Resource [PG00] (on)
[    0.207340] ACPI: Power Resource [PG01] (on)
[    0.207669] ACPI: Power Resource [PG02] (on)
[    0.208198] ACPI: Power Resource [WRST] (off)
[    0.208487] ACPI: Power Resource [WRST] (off)
[    0.208769] ACPI: Power Resource [WRST] (off)
[    0.209046] ACPI: Power Resource [WRST] (off)
[    0.209324] ACPI: Power Resource [WRST] (off)
[    0.209596] ACPI: Power Resource [WRST] (off)
[    0.209872] ACPI: Power Resource [WRST] (off)
[    0.210148] ACPI: Power Resource [WRST] (off)
[    0.210425] ACPI: Power Resource [WRST] (off)
[    0.210696] ACPI: Power Resource [WRST] (off)
[    0.210988] ACPI: Power Resource [WRST] (off)
[    0.211271] ACPI: Power Resource [WRST] (off)
[    0.211555] ACPI: Power Resource [WRST] (off)
[    0.211834] ACPI: Power Resource [WRST] (off)
[    0.212111] ACPI: Power Resource [WRST] (off)
[    0.212388] ACPI: Power Resource [WRST] (off)
[    0.212666] ACPI: Power Resource [WRST] (off)
[    0.212942] ACPI: Power Resource [WRST] (off)
[    0.213221] ACPI: Power Resource [WRST] (off)
[    0.213499] ACPI: Power Resource [WRST] (off)
[    0.225164] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-fe])
[    0.225168] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    0.225191] \_SB_.PCI0:_OSC invalid UUID
[    0.225192] _OSC request data:1 1f 0 
[    0.225194] acpi PNP0A08:00: _OSC failed (AE_ERROR); disabling ASPM
[    0.225579] PCI host bridge to bus 0000:00
[    0.225581] pci_bus 0000:00: root bus resource [bus 00-fe]
[    0.225583] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7 window]
[    0.225584] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff window]
[    0.225585] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff window]
[    0.225586] pci_bus 0000:00: root bus resource [mem 0x000c0000-0x000c3fff window]
[    0.225587] pci_bus 0000:00: root bus resource [mem 0x000c4000-0x000c7fff window]
[    0.225588] pci_bus 0000:00: root bus resource [mem 0x000c8000-0x000cbfff window]
[    0.225589] pci_bus 0000:00: root bus resource [mem 0x000cc000-0x000cffff window]
[    0.225590] pci_bus 0000:00: root bus resource [mem 0x000d0000-0x000d3fff window]
[    0.225591] pci_bus 0000:00: root bus resource [mem 0x000d4000-0x000d7fff window]
[    0.225592] pci_bus 0000:00: root bus resource [mem 0x000d8000-0x000dbfff window]
[    0.225593] pci_bus 0000:00: root bus resource [mem 0x000dc000-0x000dffff window]
[    0.225593] pci_bus 0000:00: root bus resource [mem 0x000e0000-0x000e3fff window]
[    0.225594] pci_bus 0000:00: root bus resource [mem 0x000e4000-0x000e7fff window]
[    0.225595] pci_bus 0000:00: root bus resource [mem 0x000e8000-0x000ebfff window]
[    0.225596] pci_bus 0000:00: root bus resource [mem 0x000ec000-0x000effff window]
[    0.225597] pci_bus 0000:00: root bus resource [mem 0x3b000000-0xdfffffff window]
[    0.225598] pci_bus 0000:00: root bus resource [mem 0xfd000000-0xfe7fffff window]
[    0.225604] pci 0000:00:00.0: [8086:1910] type 00 class 0x060000
[    0.225829] pci 0000:00:01.0: [8086:1901] type 01 class 0x060400
[    0.225856] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.225941] pci 0000:00:01.0: System wakeup disabled by ACPI
[    0.225987] pci 0000:00:02.0: [8086:191b] type 00 class 0x030000
[    0.225998] pci 0000:00:02.0: reg 0x10: [mem 0xdb000000-0xdbffffff 64bit]
[    0.226003] pci 0000:00:02.0: reg 0x18: [mem 0x70000000-0x7fffffff 64bit pref]
[    0.226006] pci 0000:00:02.0: reg 0x20: [io  0xf000-0xf03f]
[    0.226094] pci 0000:00:04.0: [8086:1903] type 00 class 0x118000
[    0.226106] pci 0000:00:04.0: reg 0x10: [mem 0xdd420000-0xdd427fff 64bit]
[    0.226255] pci 0000:00:14.0: [8086:a12f] type 00 class 0x0c0330
[    0.226278] pci 0000:00:14.0: reg 0x10: [mem 0xdd410000-0xdd41ffff 64bit]
[    0.226323] pci 0000:00:14.0: PME# supported from D3hot D3cold
[    0.226401] pci 0000:00:14.0: System wakeup disabled by ACPI
[    0.226431] pci 0000:00:14.2: [8086:a131] type 00 class 0x118000
[    0.226454] pci 0000:00:14.2: reg 0x10: [mem 0xdd436000-0xdd436fff 64bit]
[    0.226579] pci 0000:00:16.0: [8086:a13a] type 00 class 0x078000
[    0.226628] pci 0000:00:16.0: reg 0x10: [mem 0xdd435000-0xdd435fff 64bit]
[    0.226707] pci 0000:00:16.0: PME# supported from D3hot
[    0.226821] pci 0000:00:17.0: [8086:282a] type 00 class 0x010400
[    0.226840] pci 0000:00:17.0: reg 0x10: [mem 0xdd430000-0xdd431fff]
[    0.226847] pci 0000:00:17.0: reg 0x14: [mem 0xdd434000-0xdd4340ff]
[    0.226853] pci 0000:00:17.0: reg 0x18: [io  0xf090-0xf097]
[    0.226859] pci 0000:00:17.0: reg 0x1c: [io  0xf080-0xf083]
[    0.226865] pci 0000:00:17.0: reg 0x20: [io  0xf060-0xf07f]
[    0.226871] pci 0000:00:17.0: reg 0x24: [mem 0xdd433000-0xdd4337ff]
[    0.226893] pci 0000:00:17.0: PME# supported from D3hot
[    0.226992] pci 0000:00:1c.0: [8086:a110] type 01 class 0x060400
[    0.227045] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.227129] pci 0000:00:1c.0: System wakeup disabled by ACPI
[    0.227162] pci 0000:00:1c.4: [8086:a114] type 01 class 0x060400
[    0.227206] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.227286] pci 0000:00:1c.4: System wakeup disabled by ACPI
[    0.227309] pci 0000:00:1c.5: [8086:a115] type 01 class 0x060400
[    0.227352] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    0.227432] pci 0000:00:1c.5: System wakeup disabled by ACPI
[    0.227455] pci 0000:00:1c.6: [8086:a116] type 01 class 0x060400
[    0.227500] pci 0000:00:1c.6: PME# supported from D0 D3hot D3cold
[    0.227579] pci 0000:00:1c.6: System wakeup disabled by ACPI
[    0.227612] pci 0000:00:1f.0: [8086:a14e] type 00 class 0x060100
[    0.227789] pci 0000:00:1f.2: [8086:a121] type 00 class 0x058000
[    0.227799] pci 0000:00:1f.2: reg 0x10: [mem 0xdd42c000-0xdd42ffff]
[    0.227916] pci 0000:00:1f.3: [8086:a170] type 00 class 0x040300
[    0.227946] pci 0000:00:1f.3: reg 0x10: [mem 0xdd428000-0xdd42bfff 64bit]
[    0.227968] pci 0000:00:1f.3: reg 0x20: [mem 0xdd400000-0xdd40ffff 64bit]
[    0.227994] pci 0000:00:1f.3: PME# supported from D3hot D3cold
[    0.228104] pci 0000:00:1f.3: System wakeup disabled by ACPI
[    0.228134] pci 0000:00:1f.4: [8086:a123] type 00 class 0x0c0500
[    0.228187] pci 0000:00:1f.4: reg 0x10: [mem 0xdd432000-0xdd4320ff 64bit]
[    0.228256] pci 0000:00:1f.4: reg 0x20: [io  0xf040-0xf05f]
[    0.228431] pci 0000:01:00.0: [10de:13d8] type 00 class 0x030200
[    0.228444] pci 0000:01:00.0: reg 0x10: [mem 0xdc000000-0xdcffffff]
[    0.228451] pci 0000:01:00.0: reg 0x14: [mem 0xb0000000-0xbfffffff 64bit pref]
[    0.228457] pci 0000:01:00.0: reg 0x1c: [mem 0xc0000000-0xc1ffffff 64bit pref]
[    0.228462] pci 0000:01:00.0: reg 0x24: [io  0xe000-0xe07f]
[    0.228467] pci 0000:01:00.0: reg 0x30: [mem 0xdd000000-0xdd07ffff pref]
[    0.228524] pci 0000:01:00.0: System wakeup disabled by ACPI
[    0.235065] pci 0000:00:01.0: PCI bridge to [bus 01]
[    0.235068] pci 0000:00:01.0:   bridge window [io  0xe000-0xefff]
[    0.235070] pci 0000:00:01.0:   bridge window [mem 0xdc000000-0xdd0fffff]
[    0.235073] pci 0000:00:01.0:   bridge window [mem 0xb0000000-0xc1ffffff 64bit pref]
[    0.235157] acpiphp: Slot [1] registered
[    0.235161] pci 0000:00:1c.0: PCI bridge to [bus 02-3a]
[    0.235165] pci 0000:00:1c.0:   bridge window [mem 0xc4000000-0xda0fffff]
[    0.235169] pci 0000:00:1c.0:   bridge window [mem 0x80000000-0xa1ffffff 64bit pref]
[    0.235253] pci 0000:3b:00.0: [1969:e0a1] type 00 class 0x020000
[    0.235296] pci 0000:3b:00.0: reg 0x10: [mem 0xdd300000-0xdd33ffff 64bit]
[    0.235306] pci 0000:3b:00.0: reg 0x18: [io  0xd000-0xd07f]
[    0.235380] pci 0000:3b:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.243073] pci 0000:00:1c.4: PCI bridge to [bus 3b]
[    0.243076] pci 0000:00:1c.4:   bridge window [io  0xd000-0xdfff]
[    0.243078] pci 0000:00:1c.4:   bridge window [mem 0xdd300000-0xdd3fffff]
[    0.243184] pci 0000:3c:00.0: [8086:24f3] type 00 class 0x028000
[    0.243249] pci 0000:3c:00.0: reg 0x10: [mem 0xdd200000-0xdd201fff 64bit]
[    0.243387] pci 0000:3c:00.0: PME# supported from D0 D3hot D3cold
[    0.251092] pci 0000:00:1c.5: PCI bridge to [bus 3c]
[    0.251096] pci 0000:00:1c.5:   bridge window [mem 0xdd200000-0xdd2fffff]
[    0.251196] pci 0000:3d:00.0: [10ec:5227] type 00 class 0xff0000
[    0.251229] pci 0000:3d:00.0: reg 0x10: [mem 0xdd100000-0xdd100fff]
[    0.251318] pci 0000:3d:00.0: supports D1 D2
[    0.251320] pci 0000:3d:00.0: PME# supported from D1 D2 D3hot D3cold
[    0.259090] pci 0000:00:1c.6: PCI bridge to [bus 3d]
[    0.259094] pci 0000:00:1c.6:   bridge window [mem 0xdd100000-0xdd1fffff]
[    0.263746] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 10 *11 12 14 15)
[    0.263788] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 *10 11 12 14 15)
[    0.263829] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 10 *11 12 14 15)
[    0.263868] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 10 *11 12 14 15)
[    0.263908] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 10 *11 12 14 15)
[    0.263947] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 10 *11 12 14 15)
[    0.263986] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 10 *11 12 14 15)
[    0.264025] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 10 *11 12 14 15)
[    0.264382] ACPI: Enabled 7 GPEs in block 00 to 7F
[    0.264411] ACPI : EC: GPE = 0x14, I/O: command/status = 0x66, data = 0x62
[    0.264494] vgaarb: setting as boot device: PCI:0000:00:02.0
[    0.264496] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.264498] vgaarb: loaded
[    0.264499] vgaarb: bridge control possible 0000:00:02.0
[    0.264679] SCSI subsystem initialized
[    0.264717] libata version 3.00 loaded.
[    0.264744] ACPI: bus type USB registered
[    0.264758] usbcore: registered new interface driver usbfs
[    0.264765] usbcore: registered new interface driver hub
[    0.264782] usbcore: registered new device driver usb
[    0.264937] PCI: Using ACPI for IRQ routing
[    0.287996] PCI: pci_cache_line_size set to 64 bytes
[    0.288075] e820: reserve RAM buffer [mem 0x00058000-0x0005ffff]
[    0.288076] e820: reserve RAM buffer [mem 0x0009e000-0x0009ffff]
[    0.288077] e820: reserve RAM buffer [mem 0x2fa82000-0x2fffffff]
[    0.288078] e820: reserve RAM buffer [mem 0x2fb25000-0x2fffffff]
[    0.288078] e820: reserve RAM buffer [mem 0x361ab000-0x37ffffff]
[    0.288080] e820: reserve RAM buffer [mem 0x37fff000-0x37ffffff]
[    0.288164] NetLabel: Initializing
[    0.288165] NetLabel:  domain hash size = 128
[    0.288166] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.288173] NetLabel:  unlabeled traffic allowed by default
[    0.288268] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    0.288272] hpet0: 8 comparators, 64-bit 24.000000 MHz counter
[    0.290315] clocksource: Switched to clocksource hpet
[    0.294697] AppArmor: AppArmor Filesystem Enabled
[    0.294740] pnp: PnP ACPI init
[    0.294892] pnp 00:00: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.294914] pnp 00:01: Plug and Play ACPI device, IDs DLL0708 PNP0f13 (active)
[    0.294999] system 00:02: [io  0x0680-0x069f] has been reserved
[    0.295000] system 00:02: [io  0xffff] has been reserved
[    0.295002] system 00:02: [io  0xffff] has been reserved
[    0.295003] system 00:02: [io  0xffff] has been reserved
[    0.295004] system 00:02: [io  0x1800-0x18fe] could not be reserved
[    0.295005] system 00:02: [io  0x164e-0x164f] has been reserved
[    0.295007] system 00:02: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.295065] system 00:03: [io  0x0800-0x087f] has been reserved
[    0.295067] system 00:03: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.295082] pnp 00:04: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.295106] system 00:05: [io  0x1854-0x1857] has been reserved
[    0.295107] system 00:05: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
[    0.298486] system 00:06: [mem 0xfed10000-0xfed17fff] has been reserved
[    0.298487] system 00:06: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.298489] system 00:06: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.298490] system 00:06: [mem 0xe0000000-0xefffffff] has been reserved
[    0.298491] system 00:06: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.298492] system 00:06: [mem 0xfed90000-0xfed93fff] could not be reserved
[    0.298493] system 00:06: [mem 0xfed45000-0xfed8ffff] has been reserved
[    0.298494] system 00:06: [mem 0xff000000-0xffffffff] has been reserved
[    0.298495] system 00:06: [mem 0xfee00000-0xfeefffff] could not be reserved
[    0.298497] system 00:06: [mem 0xdffe0000-0xdfffffff] has been reserved
[    0.298498] system 00:06: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.298528] system 00:07: [mem 0xfd000000-0xfdabffff] has been reserved
[    0.298529] system 00:07: [mem 0xfdad0000-0xfdadffff] has been reserved
[    0.298530] system 00:07: [mem 0xfdb00000-0xfdffffff] has been reserved
[    0.298531] system 00:07: [mem 0xfe000000-0xfe01ffff] could not be reserved
[    0.298533] system 00:07: [mem 0xfe036000-0xfe03bfff] has been reserved
[    0.298536] system 00:07: [mem 0xfe03d000-0xfe3fffff] has been reserved
[    0.298537] system 00:07: [mem 0xfe410000-0xfe7fffff] has been reserved
[    0.298538] system 00:07: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.299248] system 00:08: [mem 0xfdaf0000-0xfdafffff] has been reserved
[    0.299249] system 00:08: [mem 0xfdae0000-0xfdaeffff] has been reserved
[    0.299250] system 00:08: [mem 0xfdac0000-0xfdacffff] has been reserved
[    0.299252] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.299828] pnp: PnP ACPI: found 9 devices
[    0.308460] clocksource: acpi_pm: mask: 0xffffff max_cycles: 0xffffff, max_idle_ns: 2085701024 ns
[    0.308473] pci 0000:00:1c.0: bridge window [io  0x1000-0x0fff] to [bus 02-3a] add_size 1000
[    0.308487] pci 0000:00:1c.0: res[13]=[io  0x1000-0x0fff] res_to_dev_res add_size 1000 min_align 1000
[    0.308488] pci 0000:00:1c.0: res[13]=[io  0x1000-0x1fff] res_to_dev_res add_size 1000 min_align 1000
[    0.308490] pci 0000:00:1c.0: BAR 13: assigned [io  0x2000-0x2fff]
[    0.308492] pci 0000:00:01.0: PCI bridge to [bus 01]
[    0.308493] pci 0000:00:01.0:   bridge window [io  0xe000-0xefff]
[    0.308495] pci 0000:00:01.0:   bridge window [mem 0xdc000000-0xdd0fffff]
[    0.308497] pci 0000:00:01.0:   bridge window [mem 0xb0000000-0xc1ffffff 64bit pref]
[    0.308500] pci 0000:00:1c.0: PCI bridge to [bus 02-3a]
[    0.308502] pci 0000:00:1c.0:   bridge window [io  0x2000-0x2fff]
[    0.308505] pci 0000:00:1c.0:   bridge window [mem 0xc4000000-0xda0fffff]
[    0.308507] pci 0000:00:1c.0:   bridge window [mem 0x80000000-0xa1ffffff 64bit pref]
[    0.308511] pci 0000:00:1c.4: PCI bridge to [bus 3b]
[    0.308512] pci 0000:00:1c.4:   bridge window [io  0xd000-0xdfff]
[    0.308515] pci 0000:00:1c.4:   bridge window [mem 0xdd300000-0xdd3fffff]
[    0.308519] pci 0000:00:1c.5: PCI bridge to [bus 3c]
[    0.308522] pci 0000:00:1c.5:   bridge window [mem 0xdd200000-0xdd2fffff]
[    0.308527] pci 0000:00:1c.6: PCI bridge to [bus 3d]
[    0.308530] pci 0000:00:1c.6:   bridge window [mem 0xdd100000-0xdd1fffff]
[    0.308535] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7 window]
[    0.308536] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff window]
[    0.308537] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff window]
[    0.308538] pci_bus 0000:00: resource 7 [mem 0x000c0000-0x000c3fff window]
[    0.308539] pci_bus 0000:00: resource 8 [mem 0x000c4000-0x000c7fff window]
[    0.308540] pci_bus 0000:00: resource 9 [mem 0x000c8000-0x000cbfff window]
[    0.308541] pci_bus 0000:00: resource 10 [mem 0x000cc000-0x000cffff window]
[    0.308542] pci_bus 0000:00: resource 11 [mem 0x000d0000-0x000d3fff window]
[    0.308543] pci_bus 0000:00: resource 12 [mem 0x000d4000-0x000d7fff window]
[    0.308544] pci_bus 0000:00: resource 13 [mem 0x000d8000-0x000dbfff window]
[    0.308545] pci_bus 0000:00: resource 14 [mem 0x000dc000-0x000dffff window]
[    0.308546] pci_bus 0000:00: resource 15 [mem 0x000e0000-0x000e3fff window]
[    0.308547] pci_bus 0000:00: resource 16 [mem 0x000e4000-0x000e7fff window]
[    0.308547] pci_bus 0000:00: resource 17 [mem 0x000e8000-0x000ebfff window]
[    0.308548] pci_bus 0000:00: resource 18 [mem 0x000ec000-0x000effff window]
[    0.308550] pci_bus 0000:00: resource 19 [mem 0x3b000000-0xdfffffff window]
[    0.308550] pci_bus 0000:00: resource 20 [mem 0xfd000000-0xfe7fffff window]
[    0.308551] pci_bus 0000:01: resource 0 [io  0xe000-0xefff]
[    0.308552] pci_bus 0000:01: resource 1 [mem 0xdc000000-0xdd0fffff]
[    0.308553] pci_bus 0000:01: resource 2 [mem 0xb0000000-0xc1ffffff 64bit pref]
[    0.308554] pci_bus 0000:02: resource 0 [io  0x2000-0x2fff]
[    0.308555] pci_bus 0000:02: resource 1 [mem 0xc4000000-0xda0fffff]
[    0.308556] pci_bus 0000:02: resource 2 [mem 0x80000000-0xa1ffffff 64bit pref]
[    0.308557] pci_bus 0000:3b: resource 0 [io  0xd000-0xdfff]
[    0.308558] pci_bus 0000:3b: resource 1 [mem 0xdd300000-0xdd3fffff]
[    0.308559] pci_bus 0000:3c: resource 1 [mem 0xdd200000-0xdd2fffff]
[    0.308560] pci_bus 0000:3d: resource 1 [mem 0xdd100000-0xdd1fffff]
[    0.308584] NET: Registered protocol family 2
[    0.308726] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.308913] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.308997] TCP: Hash tables configured (established 131072 bind 65536)
[    0.309022] UDP hash table entries: 8192 (order: 6, 262144 bytes)
[    0.309055] UDP-Lite hash table entries: 8192 (order: 6, 262144 bytes)
[    0.309102] NET: Registered protocol family 1
[    0.309111] pci 0000:00:02.0: Video device with shadowed ROM
[    0.309744] PCI: CLS 0 bytes, default 64
[    0.309770] Trying to unpack rootfs image as initramfs...
[    0.690834] Freeing initrd memory: 32220K (ffff880029b4b000 - ffff88002bac2000)
[    0.690861] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.690863] software IO TLB [mem 0x25b4b000-0x29b4b000] (64MB) mapped at [ffff880025b4b000-ffff880029b4afff]
[    0.691064] microcode: CPU0 sig=0x506e3, pf=0x20, revision=0x49
[    0.691074] microcode: CPU1 sig=0x506e3, pf=0x20, revision=0x49
[    0.691084] microcode: CPU2 sig=0x506e3, pf=0x20, revision=0x49
[    0.691087] microcode: CPU3 sig=0x506e3, pf=0x20, revision=0x49
[    0.691094] microcode: CPU4 sig=0x506e3, pf=0x20, revision=0x49
[    0.691116] microcode: CPU5 sig=0x506e3, pf=0x20, revision=0x49
[    0.691126] microcode: CPU6 sig=0x506e3, pf=0x20, revision=0x49
[    0.691136] microcode: CPU7 sig=0x506e3, pf=0x20, revision=0x49
[    0.691178] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.691204] Scanning for low memory corruption every 60 seconds
[    0.691561] futex hash table entries: 2048 (order: 5, 131072 bytes)
[    0.691583] audit: initializing netlink subsys (disabled)
[    0.691592] audit: type=2000 audit(1457000926.684:1): initialized
[    0.691794] Initialise system trusted keyring
[    0.692187] HugeTLB registered 1 GB page size, pre-allocated 0 pages
[    0.692188] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.693210] zbud: loaded
[    0.693405] VFS: Disk quotas dquot_6.6.0
[    0.693427] VFS: Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.693813] fuse init (API version 7.23)
[    0.693953] Key type big_key registered
[    0.695285] Key type asymmetric registered
[    0.695290] Asymmetric key parser 'x509' registered
[    0.695305] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 249)
[    0.695442] io scheduler noop registered
[    0.695444] io scheduler deadline registered (default)
[    0.695467] io scheduler cfq registered
[    0.696056] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.696060] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.696083] efifb: probing for efifb
[    0.696093] efifb: framebuffer at 0x70000000, mapped to 0xffffc90002000000, using 32448k, total 32448k
[    0.696094] efifb: mode is 3840x2160x32, linelength=15360, pages=1
[    0.696095] efifb: scrolling: redraw
[    0.696096] efifb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    0.710152] Console: switching to colour frame buffer device 480x135
[    0.724287] fb0: EFI VGA frame buffer device
[    0.724293] intel_idle: MWAIT substates: 0x11142120
[    0.724294] intel_idle: v0.4 model 0x5E
[    0.724294] intel_idle: lapic_timer_reliable_states 0xffffffff
[    0.724697] ACPI: AC Adapter [ACAD] (on-line)
[    0.724750] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:3f/PNP0C0D:00/input/input0
[    0.724764] ACPI: Lid Switch [LID0]
[    0.724791] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1
[    0.724793] ACPI: Power Button [PWRB]
[    0.724815] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.724816] ACPI: Power Button [PWRF]
[    0.725199] GHES: HEST is not enabled!
[    0.725296] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.762444] ACPI: Battery Slot [BAT1] (battery present)
[    0.762963] Linux agpgart interface v0.103
[    0.771997] brd: module loaded
[    0.774633] loop: module loaded
[    0.774898] libphy: Fixed MDIO Bus: probed
[    0.774901] tun: Universal TUN/TAP device driver, 1.6
[    0.774901] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.774967] PPP generic driver version 2.4.2
[    0.775136] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    0.775139] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 1
[    0.776206] xhci_hcd 0000:00:14.0: hcc params 0x200077c1 hci version 0x100 quirks 0x00109810
[    0.776210] xhci_hcd 0000:00:14.0: cache line size of 64 is not supported
[    0.776323] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    0.776325] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.776326] usb usb1: Product: xHCI Host Controller
[    0.776327] usb usb1: Manufacturer: Linux 4.3.6-040306-generic xhci-hcd
[    0.776327] usb usb1: SerialNumber: 0000:00:14.0
[    0.776419] hub 1-0:1.0: USB hub found
[    0.776434] hub 1-0:1.0: 16 ports detected
[    0.784116] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    0.784118] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 2
[    0.784138] usb usb2: New USB device found, idVendor=1d6b, idProduct=0003
[    0.784139] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.784140] usb usb2: Product: xHCI Host Controller
[    0.784141] usb usb2: Manufacturer: Linux 4.3.6-040306-generic xhci-hcd
[    0.784142] usb usb2: SerialNumber: 0000:00:14.0
[    0.784235] hub 2-0:1.0: USB hub found
[    0.784244] hub 2-0:1.0: 8 ports detected
[    0.788132] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.788138] ehci-pci: EHCI PCI platform driver
[    0.788145] ehci-platform: EHCI generic platform driver
[    0.788154] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.788159] ohci-pci: OHCI PCI platform driver
[    0.788165] ohci-platform: OHCI generic platform driver
[    0.788171] uhci_hcd: USB Universal Host Controller Interface driver
[    0.788205] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.818175] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.818178] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.818500] mousedev: PS/2 mouse device common for all mice
[    0.818917] rtc_cmos 00:04: RTC can wake from S4
[    0.819358] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    0.819436] rtc_cmos 00:04: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    0.819441] i2c /dev entries driver
[    0.819476] device-mapper: uevent: version 1.0.3
[    0.819579] device-mapper: ioctl: 4.33.0-ioctl (2015-8-18) initialised: dm-devel@redhat.com
[    0.819592] Intel P-state driver initializing.
[    0.819600] intel_pstate: HWP enabled
[    0.819652] intel_pstate: HWP enabled
[    0.819722] intel_pstate: HWP enabled
[    0.819733] intel_pstate: HWP enabled
[    0.819791] intel_pstate: HWP enabled
[    0.819865] intel_pstate: HWP enabled
[    0.819934] intel_pstate: HWP enabled
[    0.819970] intel_pstate: HWP enabled
[    0.820082] ledtrig-cpu: registered to indicate activity on CPUs
[    0.820085] EFI Variables Facility v0.08 2004-May-17
[    0.825179] NET: Registered protocol family 10
[    0.825605] NET: Registered protocol family 17
[    0.825613] Key type dns_resolver registered
[    0.826413] registered taskstats version 1
[    0.826451] Loading compiled-in X.509 certificates
[    0.826995] Loaded X.509 cert 'Build time autogenerated kernel key: 9d988231aa04ac3221015a0011942c98146f07ab'
[    0.827007] zswap: loaded using pool lzo/zbud
[    0.829463] Key type trusted registered
[    0.829622] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    0.833699] Key type encrypted registered
[    0.833703] AppArmor: AppArmor sha1 policy hashing enabled
[    0.833706] ima: No TPM chip found, activating TPM-bypass!
[    0.833719] evm: HMAC attrs: 0x1
[    0.835102]   Magic number: 8:191:476
[    0.835508] rtc_cmos 00:04: setting system clock to 2016-03-03 10:28:47 UTC (1457000927)
[    0.835831] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.835833] EDD information not available.
[    0.835942] PM: Hibernation image not present or could not be loaded.
[    0.836574] Freeing unused kernel memory: 1456K (ffffffff81d3a000 - ffffffff81ea6000)
[    0.836575] Write protecting the kernel read-only data: 12288k
[    0.837288] Freeing unused kernel memory: 48K (ffff8800027f4000 - ffff880002800000)
[    0.837723] Freeing unused kernel memory: 192K (ffff880002bd0000 - ffff880002c00000)
[    0.847243] random: systemd-udevd urandom read with 11 bits of entropy available
[    0.867966] FUJITSU Extended Socket Network Device Driver - version 1.0 - Copyright (c) 2015 FUJITSU LIMITED
[    0.873336] hidraw: raw HID events driver (C) Jiri Kosina
[    0.898624] ahci 0000:00:17.0: version 3.0
[    0.899356] rtsx_pci 0000:3d:00.0: enabling device (0000 -> 0002)
[    0.899468] rtsx_pci 0000:3d:00.0: rtsx_pci_acquire_irq: pcr->msi_en = 1, pci->irq = 125
[    0.900055] [drm] Initialized drm 1.1.0 20060810
[    0.914497] ahci 0000:00:17.0: AHCI 0001.0301 32 slots 1 ports 6 Gbps 0x2 impl RAID mode
[    0.914500] ahci 0000:00:17.0: flags: 64bit ncq sntf pm led clo only pio slum part ems deso sadm sds apst 
[    0.915079] scsi host0: ahci
[    0.915472] scsi host1: ahci
[    0.915514] ata1: DUMMY
[    0.915518] ata2: SATA max UDMA/133 abar m2048@0xdd433000 port 0xdd433180 irq 124
[    0.924435] [drm] Memory usable by graphics device = 4096M
[    0.924441] checking generic (70000000 1fb0000) vs hw (70000000 10000000)
[    0.924442] fb: switching to inteldrmfb from EFI VGA
[    0.925832] Console: switching to colour dummy device 80x25
[    0.926027] [drm] Replacing VGA console driver
[    0.932927] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[    0.932928] [drm] Driver supports precise vblank timestamp query.
[    0.938498] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[    0.953219] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[    0.953425] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input6
[    0.953572] ACPI Exception: AE_NOT_FOUND, Evaluating _DOD (20150818/video-1153)
[    0.953574] ACPI: Video Device [PEGP] (multi-head: no  rom: yes  post: no)
[    0.953615] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:12/LNXVIDEO:01/input/input7
[    0.953812] [drm] Initialized i915 1.6.0 20150731 for 0000:00:02.0 on minor 0
[    0.972617] fbcon: inteldrmfb (fb0) is primary device
[    1.098372] usb 1-4: new full-speed USB device number 2 using xhci_hcd
[    1.214516] [drm:intel_dp_aux_ch [i915]] *ERROR* dp aux hw did not signal timeout (has irq: 1)!
[    1.226846] usb 1-4: config 1 interface 0 altsetting 0 has 2 endpoint descriptors, different from the interface descriptor's value: 1
[    1.227623] usb 1-4: New USB device found, idVendor=187c, idProduct=0528
[    1.227626] usb 1-4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    1.227628] usb 1-4: Product: AW1517
[    1.227631] usb 1-4: Manufacturer: Alienware
[    1.227633] usb 1-4: SerialNumber: 16.0
[    1.227863] usb 1-4: ep 0x81 - rounding interval to 64 microframes, ep desc says 80 microframes
[    1.230520] [drm:intel_dp_aux_ch [i915]] *ERROR* dp aux hw did not signal timeout (has irq: 1)!
[    1.233949] usbcore: registered new interface driver usbhid
[    1.233950] usbhid: USB HID core driver
[    1.234348] ata2: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    1.236705] hid-generic 0003:187C:0528.0001: hiddev0,hidraw0: USB HID v1.01 Device [Alienware AW1517] on usb-0000:00:14.0-4/input0
[    1.246562] [drm:intel_dp_aux_ch [i915]] *ERROR* dp aux hw did not signal timeout (has irq: 1)!
[    1.251800] ata2.00: ATA-8: HGST HTS721010A9E630, JB0OA3P0, max UDMA/133
[    1.251801] ata2.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.253026] ata2.00: configured for UDMA/133
[    1.253383] scsi 1:0:0:0: Direct-Access     ATA      HGST HTS721010A9 A3P0 PQ: 0 ANSI: 5
[    1.253803] sd 1:0:0:0: [sda] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    1.253804] sd 1:0:0:0: [sda] 4096-byte physical blocks
[    1.253808] sd 1:0:0:0: Attached scsi generic sg0 type 0
[    1.254412] sd 1:0:0:0: [sda] Write Protect is off
[    1.254414] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.254526] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.262545] [drm:intel_dp_aux_ch [i915]] *ERROR* dp aux hw did not signal timeout (has irq: 1)!
[    1.278504] [drm:intel_dp_aux_ch [i915]] *ERROR* dp aux hw did not signal timeout (has irq: 1)!
[    1.278519] [drm:intel_dp_aux_ch [i915]] *ERROR* dp_aux_ch not done status 0xad40001f
[    1.293035] psmouse serio1: synaptics: queried max coordinates: x [..5668], y [..4756]
[    1.302428] ------------[ cut here ]------------
[    1.302443] WARNING: CPU: 1 PID: 84 at /home/kernel/COD/linux/drivers/gpu/drm/i915/intel_dp.c:854 intel_dp_aux_ch+0x114/0x6a0 [i915]()
[    1.302443] dp_aux_ch not started status 0xad40001f
[    1.302449] Modules linked in: hid_generic usbhid rtsx_pci_sdmmc i915 i2c_algo_bit drm_kms_helper psmouse syscopyarea sysfillrect sysimgblt fb_sys_fops rtsx_pci drm ahci libahci video i2c_hid pinctrl_sunrisepoint hid pinctrl_intel fjes
[    1.302450] CPU: 1 PID: 84 Comm: kworker/1:1 Not tainted 4.3.6-040306-generic #201602191831
[    1.302451] Hardware name: Alienware Alienware 15 R2/Alienware 15 R2, BIOS 1.2.3 11/11/2015
[    1.302455] Workqueue: events output_poll_execute [drm_kms_helper]
[    1.302456]  0000000000000000 00000000ee74521f ffff8804aaf478d8 ffffffff813c2e44
[    1.302457]  ffff8804aaf47920 ffff8804aaf47910 ffffffff8107d152 00000000ad40001f
[    1.302458]  0000000000064010 0000000000064014 ffff8804a9f00000 0000000000000005
[    1.302459] Call Trace:
[    1.302463]  [<ffffffff813c2e44>] dump_stack+0x44/0x60
[    1.302464]  [<ffffffff8107d152>] warn_slowpath_common+0x82/0xc0
[    1.302465]  [<ffffffff8107d1ec>] warn_slowpath_fmt+0x5c/0x80
[    1.302479]  [<ffffffffc0212b24>] intel_dp_aux_ch+0x114/0x6a0 [i915]
[    1.302481]  [<ffffffff810bf440>] ? wake_atomic_t_function+0x60/0x60
[    1.302493]  [<ffffffffc0213185>] intel_dp_aux_transfer+0xd5/0x1e0 [i915]
[    1.302495]  [<ffffffff810e9819>] ? hrtimer_try_to_cancel+0x29/0x110
[    1.302498]  [<ffffffffc0148cf4>] drm_dp_dpcd_access+0x64/0x110 [drm_kms_helper]
[    1.302501]  [<ffffffffc0148ebb>] drm_dp_dpcd_write+0x1b/0x20 [drm_kms_helper]
[    1.302514]  [<ffffffffc02154ce>] intel_dp_sink_dpms+0x9e/0xe0 [i915]
[    1.302527]  [<ffffffffc0209fbf>] intel_ddi_post_disable+0x17f/0x1e0 [i915]
[    1.302543]  [<ffffffffc01e50a7>] haswell_crtc_disable+0x137/0x2f0 [i915]
[    1.302559]  [<ffffffffc01ee2a0>] intel_atomic_commit+0x110/0x670 [i915]
[    1.302570]  [<ffffffffc00af945>] ? drm_atomic_check_only+0x215/0x540 [drm]
[    1.302578]  [<ffffffffc00afca7>] drm_atomic_commit+0x37/0x60 [drm]
[    1.302582]  [<ffffffffc0150b3f>] drm_atomic_helper_set_config+0x1bf/0x420 [drm_kms_helper]
[    1.302590]  [<ffffffffc009f162>] drm_mode_set_config_internal+0x62/0x100 [drm]
[    1.302593]  [<ffffffffc01539c3>] restore_fbdev_mode+0xb3/0x110 [drm_kms_helper]
[    1.302597]  [<ffffffffc01558b5>] drm_fb_helper_restore_fbdev_mode_unlocked+0x25/0x70 [drm_kms_helper]
[    1.302600]  [<ffffffffc015592d>] drm_fb_helper_set_par+0x2d/0x50 [drm_kms_helper]
[    1.302603]  [<ffffffffc0155836>] drm_fb_helper_hotplug_event+0xc6/0x120 [drm_kms_helper]
[    1.302618]  [<ffffffffc0203c0e>] intel_fbdev_output_poll_changed+0x1e/0x30 [i915]
[    1.302621]  [<ffffffffc0149657>] drm_kms_helper_hotplug_event+0x27/0x30 [drm_kms_helper]
[    1.302623]  [<ffffffffc0149857>] output_poll_execute+0x197/0x1e0 [drm_kms_helper]
[    1.302625]  [<ffffffff8109628a>] process_one_work+0x1aa/0x440
[    1.302626]  [<ffffffff8109656b>] worker_thread+0x4b/0x4c0
[    1.302628]  [<ffffffff817e810c>] ? __schedule+0x36c/0x980
[    1.302629]  [<ffffffff81096520>] ? process_one_work+0x440/0x440
[    1.302630]  [<ffffffff81096520>] ? process_one_work+0x440/0x440
[    1.302632]  [<ffffffff8109c788>] kthread+0xd8/0xf0
[    1.302633]  [<ffffffff8109c6b0>] ? kthread_create_on_node+0x1a0/0x1a0
[    1.302635]  [<ffffffff817ecb4f>] ret_from_fork+0x3f/0x70
[    1.302636]  [<ffffffff8109c6b0>] ? kthread_create_on_node+0x1a0/0x1a0
[    1.302637] ---[ end trace 2a38e67e11a54352 ]---
[    1.321996]  sda: sda1 sda2 sda3 sda4 sda5 sda6 sda7
[    1.322735] psmouse serio1: synaptics: queried min coordinates: x [1274..], y [1098..]
[    1.323086] sd 1:0:0:0: [sda] Attached SCSI disk
[    1.380812] psmouse serio1: synaptics: Touchpad model: 1, fw: 8.1, id: 0x1e2b1, caps: 0xd00123/0x840300/0x26c00/0x0, board id: 2417, fw id: 1365292
[    1.398465] usb 1-5: new full-speed USB device number 3 using xhci_hcd
[    1.417797] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input5
[    1.527293] usb 1-5: New USB device found, idVendor=8087, idProduct=0a2b
[    1.527294] usb 1-5: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.690609] clocksource: tsc: mask: 0xffffffffffffffff max_cycles: 0x255c8b845b6, max_idle_ns: 440795293118 ns
[    1.694122] usb 1-7: new high-speed USB device number 4 using xhci_hcd
[    1.830360] usb 1-7: New USB device found, idVendor=1bcf, idProduct=2b8c
[    1.830360] usb 1-7: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.830361] usb 1-7: Product: Integrated_Webcam_HD
[    1.830362] usb 1-7: Manufacturer: CKFDF27I462040003292
[    2.690650] clocksource: Switched to clocksource tsc
[    2.734621] [drm] RC6 on
[    7.537363] [drm:intel_dp_start_link_train [i915]] *ERROR* failed to enable link training
[    8.305221] [drm:intel_dp_complete_link_train [i915]] *ERROR* failed to start channel equalization
[    9.126194] Console: switching to colour frame buffer device 480x135
[    9.143827] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[    9.851392] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
[   10.060830] random: nonblocking pool is initialized
[   10.329086] systemd[1]: RTC configured in localtime, applying delta of -300 minutes to system time.
[   10.571201] systemd[1]: Failed to insert module 'kdbus': Function not implemented
[   10.673409] systemd[1]: systemd 225 running in system mode. (+PAM +AUDIT +SELINUX +IMA +APPARMOR +SMACK +SYSVINIT +UTMP +LIBCRYPTSETUP +GCRYPT +GNUTLS +ACL +XZ -LZ4 +SECCOMP +BLKID -ELFUTILS +KMOD -IDN)
[   10.673862] systemd[1]: Detected architecture x86-64.
[   10.684338] systemd[1]: Set hostname to <AAAZZZL15>.
[   11.240287] systemd[1]: Set up automount Arbitrary Executable File Formats File System Automount Point.
[   11.240357] systemd[1]: Reached target Encrypted Volumes.
[   11.240429] systemd[1]: Started Forward Password Requests to Wall Directory Watch.
[   11.240447] systemd[1]: Reached target Swap.
[   11.240484] systemd[1]: Reached target Remote File Systems (Pre).
[   11.240539] systemd[1]: Created slice Root Slice.
[   11.240621] systemd[1]: Listening on Journal Socket.
[   11.240688] systemd[1]: Listening on fsck to fsckd communication Socket.
[   11.240848] systemd[1]: Created slice System Slice.
[   11.241700] systemd[1]: Mounting POSIX Message Queue File System...
[   11.241875] systemd[1]: Created slice system-getty.slice.
[   11.242877] systemd[1]: Started Braille Device Support.
[   11.244290] systemd[1]: Starting Uncomplicated firewall...
[   11.245306] systemd[1]: Mounting Huge Pages File System...
[   11.246310] systemd[1]: Started Read required files in advance.
[   11.302904] systemd[1]: Starting Load Kernel Modules...
[   11.306673] systemd[1]: Starting Increase datagram queue length...
[   11.306855] systemd[1]: Created slice User and Session Slice.
[   11.306944] systemd[1]: Listening on udev Kernel Socket.
[   11.306976] systemd[1]: Reached target Slices.
[   11.307116] systemd[1]: Listening on Journal Audit Socket.
[   11.307197] systemd[1]: Listening on udev Control Socket.
[   11.307260] systemd[1]: Listening on /dev/initctl Compatibility Named Pipe.
[   11.308166] systemd[1]: Starting Setup Virtual Console...
[   11.308389] systemd[1]: Created slice system-systemd\x2dfsck.slice.
[   11.309494] systemd[1]: Starting Create list of required static device nodes for the current kernel...
[   11.310418] systemd[1]: Starting udev Coldplug all Devices...
[   11.311246] systemd[1]: Mounting Debug File System...
[   11.311264] systemd[1]: Reached target User and Group Name Lookups.
[   11.311306] systemd[1]: Listening on Journal Socket (/dev/log).
[   11.338998] systemd[1]: Started Setup Virtual Console.
[   11.347129] systemd[1]: Started Create list of required static device nodes for the current kernel.
[   11.348280] systemd[1]: Starting Create Static Device Nodes in /dev...
[   11.431780] systemd[1]: Started Uncomplicated firewall.
[   11.565775] systemd[1]: Started udev Coldplug all Devices.
[   11.614601] systemd[1]: Mounted Huge Pages File System.
[   11.614672] systemd[1]: Mounted Debug File System.
[   11.614718] systemd[1]: Mounted POSIX Message Queue File System.
[   11.616375] systemd[1]: Started Increase datagram queue length.
[   11.626669] systemd[1]: Listening on Syslog Socket.
[   11.627713] systemd[1]: Starting Journal Service...
[   11.711832] lp: driver loaded but no devices found
[   11.729833] ppdev: user-space parallel port driver
[   11.788543] systemd[1]: Started Load Kernel Modules.
[   11.789736] systemd[1]: Starting Apply Kernel Variables...
[   11.791031] systemd[1]: Mounting FUSE Control File System...
[   11.794861] systemd[1]: Mounted FUSE Control File System.
[   11.900286] systemd[1]: Started Apply Kernel Variables.
[   12.062830] systemd[1]: Started Journal Service.
[   12.735830] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
[   12.805913] systemd-journald[274]: Received request to flush runtime journal from PID 1
[   12.886476] wmi: Mapper loaded
[   12.964189] tpm_crb MSFT0101:00: A TPM error (323) occurred continue selftest
[   12.964229] tpm_crb: probe of MSFT0101:00 failed with error 323
[   13.167167] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   13.176614] mei_me 0000:00:16.0: enabling device (0000 -> 0002)
[   13.275668] Bluetooth: Core ver 2.20
[   13.275677] NET: Registered protocol family 31
[   13.275677] Bluetooth: HCI device and connection manager initialized
[   13.275680] Bluetooth: HCI socket layer initialized
[   13.275681] Bluetooth: L2CAP socket layer initialized
[   13.275684] Bluetooth: SCO socket layer initialized
[   13.382671] usbcore: registered new interface driver btusb
[   13.383232] Bluetooth: hci0: Firmware revision 0.0 build 90 week 25 2015
[   13.408887] Bluetooth: HCI UART driver ver 2.3
[   13.408893] Bluetooth: HCI UART protocol H4 registered
[   13.408896] Bluetooth: HCI UART protocol BCSP registered
[   13.408899] Bluetooth: HCI UART protocol LL registered
[   13.408901] Bluetooth: HCI UART protocol ATH3K registered
[   13.408903] Bluetooth: HCI UART protocol Three-wire (H5) registered
[   13.408951] Bluetooth: HCI UART protocol Intel registered
[   13.408978] Bluetooth: HCI UART protocol BCM registered
[   13.408980] Bluetooth: HCI UART protocol QCA registered
[   13.533164] proc_thermal 0000:00:04.0: enabling device (0000 -> 0002)
[   13.547050] input: Dell WMI hotkeys as /devices/virtual/input/input8
[   13.785829] Intel(R) Wireless WiFi driver for Linux
[   13.785835] Copyright(c) 2003- 2015 Intel Corporation
[   13.786070] iwlwifi 0000:3c:00.0: enabling device (0000 -> 0002)
[   13.793178] AVX2 version of gcm_enc/dec engaged.
[   13.793184] AES CTR mode by8 optimization enabled
[   13.826350] iwlwifi 0000:3c:00.0: Direct firmware load for iwlwifi-8000C-17.ucode failed with error -2
[   14.104047] iwlwifi 0000:3c:00.0: loaded firmware version 16.242414.0 op_mode iwlmvm
[   14.329857] cfg80211: World regulatory domain updated:
[   14.329863] cfg80211:  DFS Master region: unset
[   14.329866] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
[   14.329871] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
[   14.329874] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
[   14.329877] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (N/A, 2000 mBm), (N/A)
[   14.329881] cfg80211:   (5170000 KHz - 5250000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (N/A)
[   14.329885] cfg80211:   (5250000 KHz - 5330000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (0 s)
[   14.329889] cfg80211:   (5490000 KHz - 5730000 KHz @ 160000 KHz), (N/A, 2000 mBm), (0 s)
[   14.329892] cfg80211:   (5735000 KHz - 5835000 KHz @ 80000 KHz), (N/A, 2000 mBm), (N/A)
[   14.329895] cfg80211:   (57240000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 0 mBm), (N/A)
[   14.341151] snd_hda_intel 0000:00:1f.3: enabling device (0000 -> 0002)
[   14.341228] snd_hda_intel 0000:00:1f.3: bound 0000:00:02.0 (ops i915_audio_component_bind_ops [i915])
[   14.538667] media: Linux media interface: v0.10
[   14.562559] intel_rapl: Found RAPL domain package
[   14.562568] intel_rapl: Found RAPL domain core
[   14.562575] intel_rapl: Found RAPL domain uncore
[   14.562581] intel_rapl: Found RAPL domain dram
[   14.587901] snd_hda_codec_ca0132 hdaudioC0D0: autoconfig for CA0132: line_outs=1 (0xb/0x0/0x0/0x0/0x0) type:speaker
[   14.587908] snd_hda_codec_ca0132 hdaudioC0D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   14.587912] snd_hda_codec_ca0132 hdaudioC0D0:    hp_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   14.587915] snd_hda_codec_ca0132 hdaudioC0D0:    mono: mono_out=0x0
[   14.587917] snd_hda_codec_ca0132 hdaudioC0D0:    inputs:
[   14.587921] snd_hda_codec_ca0132 hdaudioC0D0:      Mic=0x12
[   14.587928] snd_hda_codec_ca0132 hdaudioC0D0:      Line=0x11
[   14.600947] iwlwifi 0000:3c:00.0: Detected Intel(R) Dual Band Wireless AC 8260, REV=0x208
[   14.601043] iwlwifi 0000:3c:00.0: L1 Enabled - LTR Disabled
[   14.601343] iwlwifi 0000:3c:00.0: L1 Enabled - LTR Disabled
[   14.602032] iwlwifi 0000:3c:00.0: can't access the RSA semaphore it is write protected
[   14.613937] Linux video capture interface: v2.00
[   14.789963] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[   14.831596] iwlwifi 0000:3c:00.0 wlp60s0: renamed from wlan0
[   14.894305] uvcvideo: Found UVC 1.00 device Integrated_Webcam_HD (1bcf:2b8c)
[   14.901894] input: Integrated_Webcam_HD as /devices/pci0000:00/0000:00:14.0/usb1/1-7/1-7:1.0/input/input9
[   14.902018] usbcore: registered new interface driver uvcvideo
[   14.902021] USB Video Class driver (1.1.1)
[   14.925707] nvidia: module license 'NVIDIA' taints kernel.
[   14.925713] Disabling lock debugging due to kernel taint
[   14.930488] nvidia: module verification failed: signature and/or required key missing - tainting kernel
[   14.938945] nvidia 0000:01:00.0: enabling device (0006 -> 0007)
[   14.939299] [drm] Initialized nvidia-drm 0.0.0 20150116 for 0000:01:00.0 on minor 1
[   14.939307] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  352.63  Sat Nov  7 21:25:42 PST 2015
[   15.248054] ca0132 DOWNLOAD OK :-) DSP IS RUNNING.
[   15.510233] input: HDA Intel PCH Front Line Out as /devices/pci0000:00/0000:00:1f.3/sound/card0/input10
[   15.510297] input: HDA Intel PCH Line Out as /devices/pci0000:00/0000:00:1f.3/sound/card0/input11
[   15.510357] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1f.3/sound/card0/input12
[   15.510415] input: HDA Intel PCH HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:1f.3/sound/card0/input13
[   15.510469] input: HDA Intel PCH HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:1f.3/sound/card0/input14
[   16.131876] ca0132 DOWNLOAD OK :-) DSP IS RUNNING.
[   27.636482] EXT4-fs (sda7): mounted filesystem with ordered data mode. Opts: (null)
[   27.741418] audit: type=1400 audit(1457018954.403:2): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm-guest-session" pid=534 comm="apparmor_parser"
[   27.741424] audit: type=1400 audit(1457018954.403:3): apparmor="STATUS" operation="profile_load" name="chromium" pid=534 comm="apparmor_parser"
[   27.742671] audit: type=1400 audit(1457018954.407:4): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=534 comm="apparmor_parser"
[   27.742674] audit: type=1400 audit(1457018954.407:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=534 comm="apparmor_parser"
[   27.742677] audit: type=1400 audit(1457018954.407:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-helper" pid=534 comm="apparmor_parser"
[   27.742679] audit: type=1400 audit(1457018954.407:7): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=534 comm="apparmor_parser"
[   27.749296] audit: type=1400 audit(1457018954.411:8): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=534 comm="apparmor_parser"
[   27.749300] audit: type=1400 audit(1457018954.411:9): apparmor="STATUS" operation="profile_load" name="sanitized_helper" pid=534 comm="apparmor_parser"
[   27.749303] audit: type=1400 audit(1457018954.411:10): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=534 comm="apparmor_parser"
[   27.749305] audit: type=1400 audit(1457018954.411:11): apparmor="STATUS" operation="profile_load" name="sanitized_helper" pid=534 comm="apparmor_parser"
[   27.980853] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   27.980859] Bluetooth: BNEP filters: protocol multicast
[   27.980865] Bluetooth: BNEP socket layer initialized
[   28.033499] cgroup: new mount options do not match the existing superblock, will be ignored
[   28.774423] IPv6: ADDRCONF(NETDEV_UP): wlp60s0: link is not ready
[   28.774608] iwlwifi 0000:3c:00.0: L1 Enabled - LTR Disabled
[   28.774902] iwlwifi 0000:3c:00.0: L1 Enabled - LTR Disabled
[   28.775449] iwlwifi 0000:3c:00.0: can't access the RSA semaphore it is write protected
[   28.919799] iwlwifi 0000:3c:00.0: L1 Enabled - LTR Disabled
[   28.920076] iwlwifi 0000:3c:00.0: L1 Enabled - LTR Disabled
[   28.920647] iwlwifi 0000:3c:00.0: can't access the RSA semaphore it is write protected
[   28.999195] IPv6: ADDRCONF(NETDEV_UP): wlp60s0: link is not ready
[   29.143233] IPv6: ADDRCONF(NETDEV_UP): wlp60s0: link is not ready
[   29.602141] bbswitch: version 0.7
[   29.602149] bbswitch: Found integrated VGA device 0000:00:02.0: \_SB_.PCI0.GFX0
[   29.602155] bbswitch: Found discrete VGA device 0000:01:00.0: \_SB_.PCI0.PEG0.PEGP
[   29.602166] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150818/nsarguments-95)
[   29.602267] bbswitch: detected an Optimus _DSM function
[   29.602285] bbswitch: Succesfully loaded. Discrete card 0000:01:00.0 is on
[   30.212003] vgaarb: this pci device is not a vga device
[   30.215712] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150818/nsarguments-95)
[   30.215757] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150818/nsarguments-95)
[   30.215785] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150818/nsarguments-95)
[   30.215811] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150818/nsarguments-95)
[   30.215837] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150818/nsarguments-95)
[   30.215862] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150818/nsarguments-95)
[   30.215901] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150818/nsarguments-95)
[   30.215928] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150818/nsarguments-95)
[   31.062623] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150818/nsarguments-95)
[   31.291941] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150818/nsarguments-95)
[   31.292041] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150818/nsarguments-95)
[   31.292135] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150818/nsarguments-95)
[   31.292199] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150818/nsarguments-95)
[   31.569188] [drm:intel_dp_aux_ch [i915]] *ERROR* dp aux hw did not signal timeout (has irq: 1)!
[   31.585170] [drm:intel_dp_aux_ch [i915]] *ERROR* dp aux hw did not signal timeout (has irq: 1)!
[   31.601165] [drm:intel_dp_aux_ch [i915]] *ERROR* dp aux hw did not signal timeout (has irq: 1)!
[   31.617161] [drm:intel_dp_aux_ch [i915]] *ERROR* dp aux hw did not signal timeout (has irq: 1)!
[   31.633158] [drm:intel_dp_aux_ch [i915]] *ERROR* dp aux hw did not signal timeout (has irq: 1)!
[   31.633169] [drm:intel_dp_aux_ch [i915]] *ERROR* dp_aux_ch not done status 0xad40001f
[   32.132232] wlp60s0: authenticate with 30:b5:c2:08:cb:88
[   32.134702] wlp60s0: send auth to 30:b5:c2:08:cb:88 (try 1/3)
[   32.145830] wlp60s0: authenticated
[   32.148820] wlp60s0: associate with 30:b5:c2:08:cb:88 (try 1/3)
[   32.182997] wlp60s0: RX AssocResp from 30:b5:c2:08:cb:88 (capab=0x411 status=0 aid=4)
[   32.184397] wlp60s0: associated
[   32.184411] IPv6: ADDRCONF(NETDEV_CHANGE): wlp60s0: link becomes ready
[   32.274131] wlp60s0: Limiting TX power to 27 (30 - 3) dBm as advertised by 30:b5:c2:08:cb:88
[   32.437312] vgaarb: this pci device is not a vga device
[   36.580370] [drm:intel_dp_aux_ch [i915]] *ERROR* dp aux hw did not signal timeout (has irq: 1)!
[   36.596344] [drm:intel_dp_aux_ch [i915]] *ERROR* dp aux hw did not signal timeout (has irq: 1)!
[   36.612334] [drm:intel_dp_aux_ch [i915]] *ERROR* dp aux hw did not signal timeout (has irq: 1)!
[   36.628329] [drm:intel_dp_aux_ch [i915]] *ERROR* dp aux hw did not signal timeout (has irq: 1)!
[   36.644324] [drm:intel_dp_aux_ch [i915]] *ERROR* dp aux hw did not signal timeout (has irq: 1)!
[   36.644362] [drm:intel_dp_aux_ch [i915]] *ERROR* dp_aux_ch not done status 0xad40001f
[   41.251486] [drm:intel_dp_start_link_train [i915]] *ERROR* failed to enable link training
[   42.019353] [drm:intel_dp_complete_link_train [i915]] *ERROR* failed to start channel equalization
[   43.087227] [drm:intel_dp_aux_ch [i915]] *ERROR* dp aux hw did not signal timeout (has irq: 1)!
[   43.103208] [drm:intel_dp_aux_ch [i915]] *ERROR* dp aux hw did not signal timeout (has irq: 1)!
[   43.119201] [drm:intel_dp_aux_ch [i915]] *ERROR* dp aux hw did not signal timeout (has irq: 1)!
[   43.135196] [drm:intel_dp_aux_ch [i915]] *ERROR* dp aux hw did not signal timeout (has irq: 1)!
[   43.151190] [drm:intel_dp_aux_ch [i915]] *ERROR* dp aux hw did not signal timeout (has irq: 1)!
[   43.151227] [drm:intel_dp_aux_ch [i915]] *ERROR* dp_aux_ch not done status 0xad40001f
[   48.142358] [drm:intel_dp_aux_ch [i915]] *ERROR* dp aux hw did not signal timeout (has irq: 1)!
[   48.158332] [drm:intel_dp_aux_ch [i915]] *ERROR* dp aux hw did not signal timeout (has irq: 1)!
[   48.174321] [drm:intel_dp_aux_ch [i915]] *ERROR* dp aux hw did not signal timeout (has irq: 1)!
[   48.190327] [drm:intel_dp_aux_ch [i915]] *ERROR* dp aux hw did not signal timeout (has irq: 1)!
[   48.206316] [drm:intel_dp_aux_ch [i915]] *ERROR* dp aux hw did not signal timeout (has irq: 1)!
[   48.206356] [drm:intel_dp_aux_ch [i915]] *ERROR* dp_aux_ch not done status 0xad40001f
[   52.813480] [drm:intel_dp_start_link_train [i915]] *ERROR* failed to enable link training
[   53.581339] [drm:intel_dp_complete_link_train [i915]] *ERROR* failed to start channel equalization
[   57.903732] Bluetooth: RFCOMM TTY layer initialized
[   57.903758] Bluetooth: RFCOMM socket layer initialized
[   57.903767] Bluetooth: RFCOMM ver 1.11
[  343.939302] vgaarb: this pci device is not a vga device
[  344.170037] [drm:intel_dp_aux_ch [i915]] *ERROR* dp aux hw did not signal timeout (has irq: 1)!
[  344.186028] [drm:intel_dp_aux_ch [i915]] *ERROR* dp aux hw did not signal timeout (has irq: 1)!
[  344.202015] [drm:intel_dp_aux_ch [i915]] *ERROR* dp aux hw did not signal timeout (has irq: 1)!
[  344.218012] [drm:intel_dp_aux_ch [i915]] *ERROR* dp aux hw did not signal timeout (has irq: 1)!
[  344.234007] [drm:intel_dp_aux_ch [i915]] *ERROR* dp aux hw did not signal timeout (has irq: 1)!
[  344.234018] [drm:intel_dp_aux_ch [i915]] *ERROR* dp_aux_ch not done status 0xad40001f
[  597.403269] vgaarb: this pci device is not a vga device
[  602.234659] [drm:intel_dp_start_link_train [i915]] *ERROR* failed to enable link training
[  603.002545] [drm:intel_dp_complete_link_train [i915]] *ERROR* failed to start channel equalization
[  634.333233] vgaarb: this pci device is not a vga device
[  634.366555] wlp60s0: deauthenticating from 30:b5:c2:08:cb:88 by local choice (Reason: 3=DEAUTH_LEAVING)
[  634.566035] [drm:intel_dp_aux_ch [i915]] *ERROR* dp aux hw did not signal timeout (has irq: 1)!
[  634.581995] [drm:intel_dp_aux_ch [i915]] *ERROR* dp aux hw did not signal timeout (has irq: 1)!
[  634.597970] [drm:intel_dp_aux_ch [i915]] *ERROR* dp aux hw did not signal timeout (has irq: 1)!
[  634.613964] [drm:intel_dp_aux_ch [i915]] *ERROR* dp aux hw did not signal timeout (has irq: 1)!
[  634.629960] [drm:intel_dp_aux_ch [i915]] *ERROR* dp aux hw did not signal timeout (has irq: 1)!
[  634.629971] [drm:intel_dp_aux_ch [i915]] *ERROR* dp_aux_ch not done status 0xad40001f
[  635.435989] vgaarb: this pci device is not a vga device
[  639.498577] PM: Syncing filesystems ... done.
[  639.659991] PM: Preparing system for sleep (mem)
[  640.841058] [drm:intel_dp_start_link_train [i915]] *ERROR* failed to enable link training
[  641.608942] [drm:intel_dp_complete_link_train [i915]] *ERROR* failed to start channel equalization
[  642.790867] Freezing user space processes ... (elapsed 0.001 seconds) done.
[  642.792627] Freezing remaining freezable tasks ... (elapsed 0.001 seconds) done.
[  642.793738] PM: Suspending system (mem)
[  642.793753] Suspending console(s) (use no_console_suspend to debug)
[  642.793927] sd 1:0:0:0: [sda] Synchronizing SCSI cache
[  642.810051] sd 1:0:0:0: [sda] Stopping disk
[  643.320656] PM: suspend of devices complete after 526.861 msecs
[  643.336762] PM: late suspend of devices complete after 16.099 msecs
[  643.338477] xhci_hcd 0000:00:14.0: System wakeup enabled by ACPI
[  643.353062] PM: noirq suspend of devices complete after 16.294 msecs
[  643.353806] ACPI: Preparing to enter system sleep state S3
[  643.354798] ACPI : EC: EC stopped
[  643.354799] PM: Saving platform NVS memory
[  643.354845] Disabling non-boot CPUs ...
[  643.355424] Broke affinity for irq 128
[  643.356519] smpboot: CPU 1 is now offline
[  643.377920] Broke affinity for irq 128
[  643.379013] smpboot: CPU 2 is now offline
[  643.393768] Broke affinity for irq 128
[  643.394843] smpboot: CPU 3 is now offline
[  643.405645] Broke affinity for irq 128
[  643.406727] smpboot: CPU 4 is now offline
[  643.417577] Broke affinity for irq 124
[  643.417587] Broke affinity for irq 128
[  643.418639] smpboot: CPU 5 is now offline
[  643.429460] Broke affinity for irq 124
[  643.429471] Broke affinity for irq 128
[  643.430521] smpboot: CPU 6 is now offline
[  643.441238] Broke affinity for irq 123
[  643.441243] Broke affinity for irq 124
[  643.441253] Broke affinity for irq 128
[  643.442309] smpboot: CPU 7 is now offline
[  643.459650] ACPI: Low-level resume complete
[  643.459730] ACPI : EC: EC started
[  643.459730] PM: Restoring platform NVS memory
[  643.460426] Enabling non-boot CPUs ...
[  643.479866] x86: Booting SMP configuration:
[  643.479867] smpboot: Booting Node 0 Processor 1 APIC 0x2
[  643.483384]  cache: parent cpu1 should not be sleeping
[  643.483433] intel_pstate: HWP enabled
[  643.483466] CPU1 is up
[  643.500039] smpboot: Booting Node 0 Processor 2 APIC 0x4
[  643.504996]  cache: parent cpu2 should not be sleeping
[  643.505082] intel_pstate: HWP enabled
[  643.505155] CPU2 is up
[  643.524099] smpboot: Booting Node 0 Processor 3 APIC 0x6
[  643.529187]  cache: parent cpu3 should not be sleeping
[  643.529286] intel_pstate: HWP enabled
[  643.529370] CPU3 is up
[  643.548170] smpboot: Booting Node 0 Processor 4 APIC 0x1
[  643.553347]  cache: parent cpu4 should not be sleeping
[  643.553443] intel_pstate: HWP enabled
[  643.553517] CPU4 is up
[  643.576231] smpboot: Booting Node 0 Processor 5 APIC 0x3
[  643.581423]  cache: parent cpu5 should not be sleeping
[  643.581517] intel_pstate: HWP enabled
[  643.581600] CPU5 is up
[  643.600320] smpboot: Booting Node 0 Processor 6 APIC 0x5
[  643.605923]  cache: parent cpu6 should not be sleeping
[  643.606024] intel_pstate: HWP enabled
[  643.606106] CPU6 is up
[  643.628391] smpboot: Booting Node 0 Processor 7 APIC 0x7
[  643.633975]  cache: parent cpu7 should not be sleeping
[  643.634077] intel_pstate: HWP enabled
[  643.634163] CPU7 is up
[  643.650713] ACPI: Waking up from system sleep state S3
[  643.835551] xhci_hcd 0000:00:14.0: System wakeup disabled by ACPI
[  643.849177] PM: noirq resume of devices complete after 14.606 msecs
[  643.865141] PM: early resume of devices complete after 15.899 msecs
[  643.867941] rtc_cmos 00:04: System wakeup disabled by ACPI
[  643.870612] sd 1:0:0:0: [sda] Starting disk
[  643.906757] xhci_hcd 0000:00:14.0: port 4 resume PLC timeout
[  644.132051] usb 1-5: reset full-speed USB device number 3 using xhci_hcd
[  644.216269] psmouse serio1: synaptics: queried max coordinates: x [..5668], y [..4756]
[  644.246102] psmouse serio1: synaptics: queried min coordinates: x [1274..], y [1098..]
[  644.371845] usb 1-7: reset high-speed USB device number 4 using xhci_hcd
[  644.439932] ca0132 DOWNLOAD OK :-) DSP IS RUNNING.
[  644.668881] PM: resume of devices complete after 803.852 msecs
[  644.669785] PM: Finishing wakeup.
[  644.669787] Restarting tasks ... 
[  644.670362] Bluetooth: hci0: Bootloader revision 0.0 build 2 week 52 2014
[  644.673012] done.
[  644.675350] Bluetooth: hci0: Device revision is 5
[  644.675352] Bluetooth: hci0: Secure boot is enabled
[  644.675353] Bluetooth: hci0: Minimum firmware build 1 week 10 2014
[  644.723659] iwlwifi 0000:3c:00.0: L1 Enabled - LTR Disabled
[  645.675794] [drm] RC6 on
[  646.091451] ata2: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[  646.094750] ata2.00: configured for UDMA/133
[  646.648754] Bluetooth: hci0: Found device firmware: intel/ibt-11-5.sfi
[  648.225663] Bluetooth: hci0: Waiting for firmware download to complete
[  648.225833] Bluetooth: hci0: Firmware loaded in 3473591 usecs
[  648.225974] Bluetooth: hci0: Waiting for device to boot
[  648.242850] Bluetooth: hci0: Device booted in 16575 usecs
[  648.268728] Bluetooth: hci0: Found Intel DDC parameters: intel/ibt-11-5.ddc
[  648.270904] Bluetooth: hci0: Applying Intel DDC parameters completed
[  660.031318] i915 0000:00:02.0: BAR 6: [??? 0x00000000 flags 0x2] has bogus alignment

```




I'm stuck at this point for other options.  Anyone out there have a suggestion?

---

### Post by jeremy31 on 2016-03-03
See Chili555's answer [http://askubuntu.com/a/741626/300665](http://askubuntu.com/a/741626/300665)

---

### Post by Astro96 on 2016-03-03
Thanks good fine.  I tried it, but no change.  It's like the card is not turning back on.  I also tried running:

```
sudo systemctl restart network-manager.service
``` which also had no effect other than to cause the "Disconnected" popup to appear.

---

### Post by jeremy31 on 2016-03-03
I requested this post gets moved to Networking, hopefully there are other ideas

---

### Post by Astro96 on 2016-03-03
Ok, thanks.  Let me know if there's anything I need to do to make that happen.

---

### Post by ajgreeny on 2016-03-03
I can't help with the problem, apart from moving the thread as suggested; a much better forum section for it.
Good luck!

---

### Post by havanahjoe on 2016-04-01
How is your WiFi failing after suspend? I have a problem with my WiFi after waking up, but my issue is that Network Manager thinks the adapter is Hardware Disabled.

My fix is to toggle the Hardware Switch (which is an actual switch on my Dell E7240) and then restarting the Network Service.

---

