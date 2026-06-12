---
title: "Unable to boot with wlan unlocked in bios (Asus F50SL)"
date: 2016-12-20
forum: Networking &amp; Wireless
---

### Post by el3m3ntor on 2016-12-20
Hi Everyone, i have used Ubuntu 14.04 and upgraded dist to 16.04 after learning that my Asus F50SL could'nt use the graphic drivers straigth from 16.04. (this is off-post)

Now to the actual problem, I have exhausted my search for an answer about being able to boot into Ubuntu 16.04 with BIOS WLAN UNLOCKED.
When booting in recovery mode, im able to see that my magic number never comes up, and this happens every time, with every boot option (i have'nt tried command line yet)

RFKILL does'nt show anything actually

For some reason my WIFI and Bluetooth lights are permanently ON
 The WIFI hard switch is ON 
FN+F2 is non-responsive

When using dmesg, this comes up (im currently using tethered internet through my Sony Z5)

dmesg

```
torris@Torris:~$ dmesg
[    0.000000] microcode: microcode updated early to revision 0xa4, date = 2010-10-02
[    0.000000] Linux version 4.6.0-040600-generic (kernel@gloin) (gcc version 5.3.1 20160528 (Ubuntu 5.3.1-21ubuntu11) ) #201606100558 SMP Fri Jun 10 10:01:15 UTC 2016
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-4.6.0-040600-generic root=UUID=b9aeba5a-b494-4b33-9ce8-4335335a8aa4 ro quiet splash vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] x86/fpu: Legacy x87 FPU detected.
[    0.000000] x86/fpu: Using 'eager' FPU context switches.
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009fbff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009fc00-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000bffa7fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000bffa8000-0x00000000bffaffff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000bffb0000-0x00000000bffbdfff] ACPI data
[    0.000000] BIOS-e820: [mem 0x00000000bffbe000-0x00000000bfffffff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.5 present.
[    0.000000] DMI: ASUSTeK Computer Inc.  F50SL               /F50SL     , BIOS 209     11/12/2009
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] e820: last_pfn = 0xbffa8 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 080000000 mask FC0000000 write-back
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86/PAT: Configuration [0-7]: WB  WC  UC- UC  WB  WC  UC- WT  
[    0.000000] found SMP MP-table at [mem 0x000ff780-0x000ff78f] mapped at [ffff8800000ff780]
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] Base memory trampoline at [ffff880000099000] 99000 size 24576
[    0.000000] BRK [0x0216c000, 0x0216cfff] PGTABLE
[    0.000000] BRK [0x0216d000, 0x0216dfff] PGTABLE
[    0.000000] BRK [0x0216e000, 0x0216efff] PGTABLE
[    0.000000] BRK [0x0216f000, 0x0216ffff] PGTABLE
[    0.000000] BRK [0x02170000, 0x02170fff] PGTABLE
[    0.000000] RAMDISK: [mem 0x33742000-0x35b98fff]
[    0.000000] ACPI: Early table checksum verification disabled
[    0.000000] ACPI: RSDP 0x00000000000F98C0 000014 (v00 ACPIAM)
[    0.000000] ACPI: RSDT 0x00000000BFFB0000 00004C (v01 _ASUS_ Notebook 20091112 MSFT 00000097)
[    0.000000] ACPI: FACP 0x00000000BFFB0200 000084 (v01 111209 FACP1346 20091112 MSFT 00000097)
[    0.000000] ACPI: DSDT 0x00000000BFFB0680 0097A2 (v01 F50SL  F50SL001 00000001 INTL 20051117)
[    0.000000] ACPI: FACS 0x00000000BFFBE000 000040
[    0.000000] ACPI: APIC 0x00000000BFFB0390 00005C (v01 111209 APIC1346 20091112 MSFT 00000097)
[    0.000000] ACPI: MCFG 0x00000000BFFB0430 00003C (v01 111209 OEMMCFG  20091112 MSFT 00000097)
[    0.000000] ACPI: SLIC 0x00000000BFFB0470 000176 (v01 _ASUS_ Notebook 20091112 MSFT 00000097)
[    0.000000] ACPI: ECDT 0x00000000BFFB0620 000055 (v01 111209 OEMECDT  20091112 MSFT 00000097)
[    0.000000] ACPI: DBGP 0x00000000BFFB03F0 000034 (v01 111209 DBGP1346 20091112 MSFT 00000097)
[    0.000000] ACPI: BOOT 0x00000000BFFB05F0 000028 (v01 111209 BOOT1346 20091112 MSFT 00000097)
[    0.000000] ACPI: OEMB 0x00000000BFFBE040 000071 (v01 111209 OEMB1346 20091112 MSFT 00000097)
[    0.000000] ACPI: HPET 0x00000000BFFB9E30 000038 (v01 111209 OEMHPET  20091112 MSFT 00000097)
[    0.000000] ACPI: SSDT 0x00000000BFFBED50 0004E6 (v01 PmRef  CpuPm    00003000 INTL 20051117)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x00000000bffa7fff]
[    0.000000] NODE_DATA(0) allocated [mem 0xbff7d000-0xbffa7fff]
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x0000000000001000-0x0000000000ffffff]
[    0.000000]   DMA32    [mem 0x0000000001000000-0x00000000bffa7fff]
[    0.000000]   Normal   empty
[    0.000000]   Device   empty
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x0000000000001000-0x000000000009efff]
[    0.000000]   node   0: [mem 0x0000000000100000-0x00000000bffa7fff]
[    0.000000] Initmem setup node 0 [mem 0x0000000000001000-0x00000000bffa7fff]
[    0.000000] On node 0 totalpages: 786246
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 21 pages reserved
[    0.000000]   DMA zone: 3998 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 12223 pages used for memmap
[    0.000000]   DMA32 zone: 782248 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] IOAPIC[0]: apic_id 2, version 20, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x10398201 base: 0xfed00000
[    0.000000] smpboot: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] PM: Registered nosave memory: [mem 0x00000000-0x00000fff]
[    0.000000] PM: Registered nosave memory: [mem 0x0009f000-0x0009ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000e0000-0x000fffff]
[    0.000000] e820: [mem 0xc0000000-0xfedfffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] clocksource: refined-jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645519600211568 ns
[    0.000000] setup_percpu: NR_CPUS:8192 nr_cpumask_bits:2 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] percpu: Embedded 32 pages/cpu @ffff8800bfa00000 s93464 r8192 d29416 u1048576
[    0.000000] pcpu-alloc: s93464 r8192 d29416 u1048576 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 773938
[    0.000000] Policy zone: DMA32
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.6.0-040600-generic root=UUID=b9aeba5a-b494-4b33-9ce8-4335335a8aa4 ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 3039992K/3144984K available (6805K kernel code, 1330K rwdata, 3076K rodata, 1764K init, 2420K bss, 104992K reserved, 0K cma-reserved)
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     Build-time adjustment of leaf fanout to 64.
[    0.000000]     RCU restricting CPUs from NR_CPUS=8192 to nr_cpu_ids=2.
[    0.000000] RCU: Adjusting geometry for rcu_fanout_leaf=64, nr_cpu_ids=2
[    0.000000] NR_IRQS:524544 nr_irqs:440 16
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] clocksource: hpet: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 133484882848 ns
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.000000] tsc: Detected 2166.801 MHz processor
[    0.004022] Calibrating delay loop (skipped), value calculated using timer frequency.. 4333.60 BogoMIPS (lpj=8667204)
[    0.004026] pid_max: default: 32768 minimum: 301
[    0.004046] ACPI: Core revision 20160108
[    0.015359] ACPI: 2 ACPI AML tables successfully acquired and loaded

[    0.015400] Security Framework initialized
[    0.015404] Yama: becoming mindful.
[    0.015424] AppArmor: AppArmor initialized
[    0.015897] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.020368] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.022619] Mount-cache hash table entries: 8192 (order: 4, 65536 bytes)
[    0.022637] Mountpoint-cache hash table entries: 8192 (order: 4, 65536 bytes)
[    0.023373] CPU: Physical Processor ID: 0
[    0.023377] CPU: Processor Core ID: 0
[    0.023382] mce: CPU supports 6 MCE banks
[    0.023402] process: using mwait in idle threads
[    0.023413] Last level iTLB entries: 4KB 128, 2MB 4, 4MB 4
[    0.023414] Last level dTLB entries: 4KB 256, 2MB 0, 4MB 32, 1GB 0
[    0.023828] Freeing SMP alternatives memory: 24K (ffffffff81f07000 - ffffffff81f0d000)
[    0.028006] ftrace: allocating 27462 entries in 108 pages
[    0.040206] smpboot: Max logical packages: 1
[    0.040214] smpboot: APIC(0) Converting physical 0 to logical package 0
[    0.040538] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.084000] smpboot: CPU0: Intel(R) Core(TM)2 Duo CPU     T5850  @ 2.16GHz (family: 0x6, model: 0xf, stepping: 0xd)
[    0.084000] Performance Events: PEBS fmt0+, 4-deep LBR, Core2 events, Intel PMU driver.
[    0.084000] core: PEBS disabled due to CPU errata
[    0.084000] ... version:                2
[    0.084000] ... bit width:              40
[    0.084000] ... generic registers:      2
[    0.084000] ... value mask:             000000ffffffffff
[    0.084000] ... max period:             000000007fffffff
[    0.084000] ... fixed-purpose events:   3
[    0.084000] ... event mask:             0000000700000003
[    0.084000] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.084000] x86: Booting SMP configuration:
[    0.084000] .... node  #0, CPUs:      #1
[    0.162040] x86: Booted up 1 node, 2 CPUs
[    0.162040] smpboot: Total of 2 processors activated (8667.00 BogoMIPS)
[    0.162040] devtmpfs: initialized
[    0.162040] x86/mm: Memory block size: 128MB
[    0.165554] evm: security.selinux
[    0.165556] evm: security.SMACK64
[    0.165557] evm: security.SMACK64EXEC
[    0.165559] evm: security.SMACK64TRANSMUTE
[    0.165560] evm: security.SMACK64MMAP
[    0.165561] evm: security.ima
[    0.165563] evm: security.capability
[    0.165593] PM: Registering ACPI NVS region [mem 0xbffa8000-0xbffaffff] (32768 bytes)
[    0.165593] PM: Registering ACPI NVS region [mem 0xbffbe000-0xbfffffff] (270336 bytes)
[    0.165593] clocksource: jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645041785100000 ns
[    0.165593] pinctrl core: initialized pinctrl subsystem
[    0.168026] RTC time: 22:53:32, date: 12/20/16
[    0.168181] NET: Registered protocol family 16
[    0.180006] cpuidle: using governor ladder
[    0.192004] cpuidle: using governor menu
[    0.192009] PCCT header not found.
[    0.192045] Simple Boot Flag at 0x71 set to 0x1
[    0.192080] ACPI: bus type PCI registered
[    0.192083] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.192195] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.192198] PCI: not using MMCONFIG
[    0.192200] PCI: Using configuration type 1 for base access
[    0.192396] mtrr: your CPUs had inconsistent variable MTRR settings
[    0.192398] mtrr: probably your BIOS does not setup all CPUs.
[    0.192400] mtrr: corrected configuration.
[    0.204055] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.204122] ACPI: Added _OSI(Module Device)
[    0.204124] ACPI: Added _OSI(Processor Device)
[    0.204126] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.204128] ACPI: Added _OSI(Processor Aggregator Device)
[    0.204238] ACPI : EC: EC description table is found, configuring boot EC
[    0.204254] ACPI : EC: EC started
[    0.204502] ACPI: Executed 1 blocks of module-level executable AML code
[    0.212276] ACPI: Dynamic OEM Table Load:
[    0.212285] ACPI: SSDT 0xFFFF8800BB91DC00 000244 (v01 PmRef  Cpu0Ist  00003000 INTL 20051117)
[    0.212791] ACPI: Dynamic OEM Table Load:
[    0.212798] ACPI: SSDT 0xFFFF8800BB90A800 0006D9 (v01 PmRef  Cpu0Cst  00003001 INTL 20051117)
[    0.216595] ACPI: Dynamic OEM Table Load:
[    0.216601] ACPI: SSDT 0xFFFF8800BB92E500 0000C8 (v01 PmRef  Cpu1Ist  00003000 INTL 20051117)
[    0.217032] ACPI: Dynamic OEM Table Load:
[    0.217038] ACPI: SSDT 0xFFFF8800BB92AD80 000085 (v01 PmRef  Cpu1Cst  00003000 INTL 20051117)
[    0.217587] ACPI: Interpreter enabled
[    0.217612] ACPI: (supports S0 S3 S4 S5)
[    0.217614] ACPI: Using IOAPIC for interrupt routing
[    0.217654] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.218215] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in ACPI motherboard resources
[    0.218231] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.223884] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.223892] acpi PNP0A03:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    0.224074] acpi PNP0A03:00: _OSC: platform does not support [PME]
[    0.224224] acpi PNP0A03:00: _OSC: OS now controls [PCIeHotplug AER PCIeCapability]
[    0.224480] PCI host bridge to bus 0000:00
[    0.224484] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7 window]
[    0.224486] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff window]
[    0.224489] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff window]
[    0.224491] pci_bus 0000:00: root bus resource [mem 0x000d0000-0x000dffff window]
[    0.224494] pci_bus 0000:00: root bus resource [mem 0xc0000000-0xdfffffff window]
[    0.224496] pci_bus 0000:00: root bus resource [mem 0xf0000000-0xfed44fff window]
[    0.224499] pci_bus 0000:00: root bus resource [bus 00-ff]
[    0.224512] pci 0000:00:00.0: [1039:0671] type 00 class 0x060000
[    0.224650] pci 0000:00:01.0: [1039:0004] type 01 class 0x060400
[    0.224729] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.224829] pci 0000:00:02.0: [1039:0968] type 00 class 0x060100
[    0.224988] pci 0000:00:02.5: [1039:5513] type 00 class 0x010180
[    0.225037] pci 0000:00:02.5: reg 0x20: [io  0xfff0-0xffff]
[    0.225059] pci 0000:00:02.5: legacy IDE quirk: reg 0x10: [io  0x01f0-0x01f7]
[    0.225062] pci 0000:00:02.5: legacy IDE quirk: reg 0x14: [io  0x03f6]
[    0.225064] pci 0000:00:02.5: legacy IDE quirk: reg 0x18: [io  0x0170-0x0177]
[    0.225066] pci 0000:00:02.5: legacy IDE quirk: reg 0x1c: [io  0x0376]
[    0.225094] pci 0000:00:02.5: PME# supported from D3cold
[    0.225581] pci 0000:00:03.0: [1039:7001] type 00 class 0x0c0310
[    0.225596] pci 0000:00:03.0: reg 0x10: [mem 0xfddff000-0xfddfffff]
[    0.225690] pci 0000:00:03.0: System wakeup disabled by ACPI
[    0.225746] pci 0000:00:03.1: [1039:7001] type 00 class 0x0c0310
[    0.225760] pci 0000:00:03.1: reg 0x10: [mem 0xfddfe000-0xfddfefff]
[    0.225853] pci 0000:00:03.1: System wakeup disabled by ACPI
[    0.225915] pci 0000:00:03.3: [1039:7002] type 00 class 0x0c0320
[    0.225931] pci 0000:00:03.3: reg 0x10: [mem 0xfddfd000-0xfddfdfff]
[    0.226007] pci 0000:00:03.3: PME# supported from D0 D3hot D3cold
[    0.226045] pci 0000:00:03.3: System wakeup disabled by ACPI
[    0.226112] pci 0000:00:04.0: [1039:0191] type 00 class 0x020000
[    0.226128] pci 0000:00:04.0: reg 0x10: [mem 0xfddfcc00-0xfddfcc7f]
[    0.226139] pci 0000:00:04.0: reg 0x14: [io  0xcc00-0xcc7f]
[    0.226207] pci 0000:00:04.0: supports D1 D2
[    0.226210] pci 0000:00:04.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.226248] pci 0000:00:04.0: System wakeup disabled by ACPI
[    0.226306] pci 0000:00:05.0: [1039:1183] type 00 class 0x01018f
[    0.226323] pci 0000:00:05.0: reg 0x10: [io  0xc800-0xc807]
[    0.226333] pci 0000:00:05.0: reg 0x14: [io  0xc400-0xc403]
[    0.226343] pci 0000:00:05.0: reg 0x18: [io  0xc000-0xc007]
[    0.226354] pci 0000:00:05.0: reg 0x1c: [io  0xbc00-0xbc03]
[    0.226364] pci 0000:00:05.0: reg 0x20: [io  0xb800-0xb80f]
[    0.226374] pci 0000:00:05.0: reg 0x24: [io  0xb400-0xb47f]
[    0.226413] pci 0000:00:05.0: PME# supported from D3cold
[    0.226451] pci 0000:00:05.0: System wakeup disabled by ACPI
[    0.226516] pci 0000:00:07.0: [1039:000a] type 01 class 0x060400
[    0.226599] pci 0000:00:07.0: PME# supported from D0 D3hot D3cold
[    0.226642] pci 0000:00:07.0: System wakeup disabled by ACPI
[    0.226708] pci 0000:00:0f.0: [1039:7502] type 00 class 0x040300
[    0.226725] pci 0000:00:0f.0: reg 0x10: [mem 0xfddf4000-0xfddf7fff]
[    0.226803] pci 0000:00:0f.0: PME# supported from D0 D3hot D3cold
[    0.226841] pci 0000:00:0f.0: System wakeup disabled by ACPI
[    0.226990] pci 0000:01:00.0: [1002:9553] type 00 class 0x030000
[    0.227007] pci 0000:01:00.0: reg 0x10: [mem 0xc0000000-0xdfffffff pref]
[    0.227018] pci 0000:01:00.0: reg 0x14: [io  0xd800-0xd8ff]
[    0.227029] pci 0000:01:00.0: reg 0x18: [mem 0xfdef0000-0xfdefffff]
[    0.227065] pci 0000:01:00.0: reg 0x30: [mem 0xfdec0000-0xfdedffff pref]
[    0.227116] pci 0000:01:00.0: supports D1 D2
[    0.227192] pci 0000:01:00.1: [1002:aa38] type 00 class 0x040300
[    0.227208] pci 0000:01:00.1: reg 0x10: [mem 0xfdeec000-0xfdeeffff]
[    0.227309] pci 0000:01:00.1: supports D1 D2
[    0.232019] pci 0000:00:01.0: PCI bridge to [bus 01]
[    0.232026] pci 0000:00:01.0:   bridge window [io  0xd000-0xdfff]
[    0.232031] pci 0000:00:01.0:   bridge window [mem 0xfde00000-0xfdefffff]
[    0.232037] pci 0000:00:01.0:   bridge window [mem 0xc0000000-0xdfffffff 64bit pref]
[    0.232109] pci 0000:00:07.0: PCI bridge to [bus 03-06]
[    0.232117] pci 0000:00:07.0:   bridge window [io  0xe000-0xefff]
[    0.232122] pci 0000:00:07.0:   bridge window [mem 0xfe000000-0xfebfffff]
[    0.232128] pci 0000:00:07.0:   bridge window [mem 0xfa000000-0xfcffffff 64bit pref]
[    0.232730] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 *10 11 12 14 15)
[    0.232799] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 10 *11 12 14 15)
[    0.232866] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 *4 5 7 10 11 12 14 15)
[    0.232931] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 *7 10 11 12 14 15)
[    0.232997] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 *5 7 10 11 12 14 15)
[    0.233063] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 10 11 12 14 *15)
[    0.233129] ACPI: PCI Interrupt Link [LNKG] (IRQs *3 4 5 7 10 11 12 14 15)
[    0.233195] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.233371] ACPI: Enabled 2 GPEs in block 00 to 0F
[    0.233377] ACPI: Enabled 1 GPEs in block 10 to 1F
[    0.233468] ACPI : EC: GPE = 0x19, I/O: command/status = 0x66, data = 0x62
[    0.233602] vgaarb: setting as boot device: PCI:0000:01:00.0
[    0.233602] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.233602] vgaarb: loaded
[    0.233602] vgaarb: bridge control possible 0000:01:00.0
[    0.233602] PCI: Using ACPI for IRQ routing
[    0.241422] PCI: pci_cache_line_size set to 64 bytes
[    0.241465] e820: reserve RAM buffer [mem 0x0009fc00-0x0009ffff]
[    0.241468] e820: reserve RAM buffer [mem 0xbffa8000-0xbfffffff]
[    0.241667] NetLabel: Initializing
[    0.241669] NetLabel:  domain hash size = 128
[    0.241671] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.241692] NetLabel:  unlabeled traffic allowed by default
[    0.241723] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.241723] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.241723] hpet0: 3 comparators, 32-bit 14.318180 MHz counter
[    0.245023] clocksource: Switched to clocksource hpet
[    0.256570] VFS: Disk quotas dquot_6.6.0
[    0.256622] VFS: Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.256801] AppArmor: AppArmor Filesystem Enabled
[    0.256936] pnp: PnP ACPI init
[    0.257156] pnp 00:00: Plug and Play ACPI device, IDs PNP0303 PNP030b (active)
[    0.257235] pnp 00:01: Plug and Play ACPI device, IDs SYN0a06 SYN0a00 SYN0002 PNP0f03 PNP0f13 PNP0f12 (active)
[    0.257462] system 00:02: [io  0x0290-0x0297] has been reserved
[    0.257466] system 00:02: [io  0x0c00-0x0c05] has been reserved
[    0.257469] system 00:02: [io  0x0d00-0x0d05] has been reserved
[    0.257471] system 00:02: [io  0x0480-0x048f] has been reserved
[    0.257474] system 00:02: [io  0x04d0-0x04d1] has been reserved
[    0.257477] system 00:02: [io  0x0800-0x087f] could not be reserved
[    0.257479] system 00:02: [io  0x0880-0x08ff] has been reserved
[    0.257482] system 00:02: [io  0x0c00-0x0c7f] could not be reserved
[    0.257484] system 00:02: [io  0x2000-0x20fe] has been reserved
[    0.257487] system 00:02: [mem 0xfff80000-0xffffffff] has been reserved
[    0.257490] system 00:02: [mem 0xffb80000-0xffbfffff] has been reserved
[    0.257492] system 00:02: [mem 0xffee0000-0xffefffff] has been reserved
[    0.257495] system 00:02: [mem 0xfed10000-0xfed3ffff] has been reserved
[    0.257500] system 00:02: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.257586] pnp 00:03: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.257684] system 00:04: [io  0x0250-0x0253] has been reserved
[    0.257687] system 00:04: [io  0x0256-0x025f] has been reserved
[    0.257690] system 00:04: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.257693] system 00:04: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.257697] system 00:04: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.257837] system 00:05: [mem 0xe0000000-0xefffffff] has been reserved
[    0.257842] system 00:05: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.258077] system 00:06: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.258081] system 00:06: [mem 0x000c0000-0x000cffff] could not be reserved
[    0.258084] system 00:06: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.258086] system 00:06: [mem 0x00100000-0xbfffffff] could not be reserved
[    0.258089] system 00:06: [mem 0xe0000000-0xffffffff] could not be reserved
[    0.258093] system 00:06: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.258236] pnp: PnP ACPI: found 7 devices
[    0.265551] clocksource: acpi_pm: mask: 0xffffff max_cycles: 0xffffff, max_idle_ns: 2085701024 ns
[    0.265590] pci 0000:00:01.0: PCI bridge to [bus 01]
[    0.265595] pci 0000:00:01.0:   bridge window [io  0xd000-0xdfff]
[    0.265601] pci 0000:00:01.0:   bridge window [mem 0xfde00000-0xfdefffff]
[    0.265606] pci 0000:00:01.0:   bridge window [mem 0xc0000000-0xdfffffff 64bit pref]
[    0.265614] pci 0000:00:07.0: PCI bridge to [bus 03-06]
[    0.265617] pci 0000:00:07.0:   bridge window [io  0xe000-0xefff]
[    0.265623] pci 0000:00:07.0:   bridge window [mem 0xfe000000-0xfebfffff]
[    0.265627] pci 0000:00:07.0:   bridge window [mem 0xfa000000-0xfcffffff 64bit pref]
[    0.265636] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7 window]
[    0.265638] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff window]
[    0.265641] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff window]
[    0.265643] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff window]
[    0.265646] pci_bus 0000:00: resource 8 [mem 0xc0000000-0xdfffffff window]
[    0.265648] pci_bus 0000:00: resource 9 [mem 0xf0000000-0xfed44fff window]
[    0.265651] pci_bus 0000:01: resource 0 [io  0xd000-0xdfff]
[    0.265653] pci_bus 0000:01: resource 1 [mem 0xfde00000-0xfdefffff]
[    0.265655] pci_bus 0000:01: resource 2 [mem 0xc0000000-0xdfffffff 64bit pref]
[    0.265658] pci_bus 0000:03: resource 0 [io  0xe000-0xefff]
[    0.265660] pci_bus 0000:03: resource 1 [mem 0xfe000000-0xfebfffff]
[    0.265662] pci_bus 0000:03: resource 2 [mem 0xfa000000-0xfcffffff 64bit pref]
[    0.265713] NET: Registered protocol family 2
[    0.266049] TCP established hash table entries: 32768 (order: 6, 262144 bytes)
[    0.266327] TCP bind hash table entries: 32768 (order: 7, 524288 bytes)
[    0.266786] TCP: Hash tables configured (established 32768 bind 32768)
[    0.266865] UDP hash table entries: 2048 (order: 4, 65536 bytes)
[    0.266925] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
[    0.267049] NET: Registered protocol family 1
[    0.440253] pci 0000:01:00.0: Video device with shadowed ROM at [mem 0x000c0000-0x000dffff]
[    0.440260] PCI: CLS 32 bytes, default 64
[    0.440367] Unpacking initramfs...
[    1.263223] Freeing initrd memory: 37212K (ffff880033742000 - ffff880035b99000)
[    1.263720] Scanning for low memory corruption every 60 seconds
[    1.264455] futex hash table entries: 512 (order: 3, 32768 bytes)
[    1.264527] audit: initializing netlink subsys (disabled)
[    1.264575] audit: type=2000 audit(1482274413.264:1): initialized
[    1.265063] Initialise system trusted keyring
[    1.265262] workingset: timestamp_bits=33 max_order=20 bucket_order=0
[    1.268192] zbud: loaded
[    1.268489] Key type big_key registered
[    1.268984] Key type asymmetric registered
[    1.268989] Asymmetric key parser 'x509' registered
[    1.269053] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 247)
[    1.269098] io scheduler noop registered
[    1.269103] io scheduler deadline registered (default)
[    1.269158] io scheduler cfq registered
[    1.269504] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.269523] pciehp 0000:00:07.0:pcie04: Slot #0 AttnBtn- PwrCtrl- MRL- AttnInd- PwrInd- HotPlug+ Surprise+ Interlock- NoCompl- LLActRep-
[    1.269584] pciehp 0000:00:07.0:pcie04: service driver pciehp loaded
[    1.269592] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.269696] vesafb: mode is 1024x768x32, linelength=4096, pages=0
[    1.269697] vesafb: scrolling: redraw
[    1.269700] vesafb: Truecolor: size=0:8:8:8, shift=0:16:8:0
[    1.269723] vesafb: framebuffer at 0xc0000000, mapped to 0xffffc90000800000, using 3072k, total 3072k
[    1.307932] Console: switching to colour frame buffer device 128x48
[    1.345923] fb0: VESA VGA frame buffer device
[    1.345947] intel_idle: does not run on family 6 model 15
[    1.346001] GHES: HEST is not enabled!
[    1.346088] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.348717] PPP generic driver version 2.4.2
[    1.348808] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    1.351772] i8042: Detected active multiplexing controller, rev 1.1
[    1.352773] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.352781] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    1.352796] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    1.352799] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    1.352802] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    1.353116] mousedev: PS/2 mouse device common for all mice
[    1.353202] rtc_cmos 00:03: RTC can wake from S4
[    1.353349] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    1.353374] rtc_cmos 00:03: alarms up to one year, 114 bytes nvram, hpet irqs
[    1.353404] ledtrig-cpu: registered to indicate activity on CPUs
[    1.353828] NET: Registered protocol family 10
[    1.354142] NET: Registered protocol family 17
[    1.354374] microcode: CPU0 sig=0x6fd, pf=0x80, revision=0xa4
[    1.354383] microcode: CPU1 sig=0x6fd, pf=0x80, revision=0xa4
[    1.354426] microcode: Microcode Update Driver: v2.01 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    1.354641] registered taskstats version 1
[    1.354660] Loading compiled-in X.509 certificates
[    1.358910] Loaded X.509 cert 'Build time autogenerated kernel key: 6932164081ba34b3f8e1f863febb295414334a88'
[    1.358960] zswap: loaded using pool lzo/zbud
[    1.363770] Key type encrypted registered
[    1.363785] AppArmor: AppArmor sha1 policy hashing enabled
[    1.363791] ima: No TPM chip found, activating TPM-bypass!
[    1.363832] evm: HMAC attrs: 0x1
[    1.364151]   Magic number: 12:215:907
[    1.364314] rtc_cmos 00:03: setting system clock to 2016-12-20 22:53:34 UTC (1482274414)
[    1.364442] PM: Hibernation image not present or could not be loaded.
[    1.366858] Freeing unused kernel memory: 1764K (ffffffff81d4e000 - ffffffff81f07000)
[    1.366863] Write protecting the kernel read-only data: 12288k
[    1.368233] Freeing unused kernel memory: 1372K (ffff8800016a9000 - ffff880001800000)
[    1.371926] Freeing unused kernel memory: 1020K (ffff880001b01000 - ffff880001c00000)
[    1.387385] random: systemd-udevd urandom read with 2 bits of entropy available
[    1.393157] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input0
[    1.427323] Linux agpgart interface v0.103
[    1.442297] sis190: sis190 Gigabit Ethernet driver 1.4 loaded
[    1.442487] sis190: 0000:00:04.0: Read MAC address from EEPROM
[    1.442490] sis190: 0000:00:04.0: Error EEPROM read 0
[    1.442493] sis190: 0000:00:04.0: Read MAC address from APC
[    1.451159] SCSI subsystem initialized
[    1.463782] [drm] Initialized drm 1.1.0 20060810
[    1.464920] ACPI: bus type USB registered
[    1.464958] usbcore: registered new interface driver usbfs
[    1.464973] usbcore: registered new interface driver hub
[    1.468550] usbcore: registered new device driver usb
[    1.471492] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.474217] ehci-pci: EHCI PCI platform driver
[    1.475529] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input3
[    1.475605] ACPI: Power Button [PWRB]
[    1.475685] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input4
[    1.475724] ACPI: Sleep Button [SLPB]
[    1.475792] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input5
[    1.476647] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.481531] FUJITSU Extended Socket Network Device Driver - version 1.0 - Copyright (c) 2015 FUJITSU LIMITED
[    1.484959] libata version 3.00 loaded.
[    1.494927] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[    1.504050] sis190: 0000:00:04.0: unknown PHY 0x1c:0xc910 transceiver at address 1
[    1.507884] ACPI: Lid Switch [LID]
[    1.509399] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input6
[    1.509479] ACPI: Power Button [PWRF]
[    1.511271] acpi device:17: registered as cooling_device0
[    1.511357] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/device:14/LNXVIDEO:00/input/input7
[    1.529556] [drm] radeon kernel modesetting enabled.
[    1.533153] AMD IOMMUv2 driver by Joerg Roedel <jroedel@suse.de>
[    1.533156] AMD IOMMUv2 functionality not available on this system
[    1.537316] CRAT table not found
[    1.537319] Finished initializing topology ret=0
[    1.537401] kfd kfd: Initialized module
[    1.537745] checking generic (c0000000 300000) vs hw (c0000000 20000000)
[    1.537748] fb: switching to radeondrmfb from VESA VGA
[    1.537797] Console: switching to colour dummy device 80x25
[    1.538365] [drm] initializing kernel modesetting (RV710 0x1002:0x9553 0x1043:0x1B42 0x00).
[    1.538384] [drm] register mmio base: 0xFDEF0000
[    1.538386] [drm] register mmio size: 65536
[    1.538519] ATOM BIOS: BR32088
[    1.538570] radeon 0000:01:00.0: VRAM: 512M 0x0000000000000000 - 0x000000001FFFFFFF (512M used)
[    1.538574] radeon 0000:01:00.0: GTT: 1024M 0x0000000020000000 - 0x000000005FFFFFFF
[    1.538576] [drm] Detected VRAM RAM=512M, BAR=512M
[    1.538578] [drm] RAM width 64bits DDR
[    1.538659] [TTM] Zone  kernel: Available graphics memory: 1540692 kiB
[    1.538661] [TTM] Initializing pool allocator
[    1.538669] [TTM] Initializing DMA pool allocator
[    1.538704] [drm] radeon: 512M of VRAM memory ready
[    1.538706] [drm] radeon: 1024M of GTT memory ready.
[    1.538731] [drm] Loading RV710 Microcode
[    1.540674] [drm] radeon: dpm initialized
[    1.540851] [drm] GART: num cpu pages 262144, num gpu pages 262144
[    1.559559] [drm] PCIE GART of 1024M enabled (table at 0x000000000025E000).
[    1.559626] radeon 0000:01:00.0: WB enabled
[    1.559630] radeon 0000:01:00.0: fence driver on ring 0 use gpu addr 0x0000000020000c00 and cpu addr 0xffff880034a3fc00
[    1.559634] radeon 0000:01:00.0: fence driver on ring 3 use gpu addr 0x0000000020000c0c and cpu addr 0xffff880034a3fc0c
[    1.560577] radeon 0000:01:00.0: fence driver on ring 5 use gpu addr 0x000000000005c598 and cpu addr 0xffffc90000c1c598
[    1.560581] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[    1.560583] [drm] Driver supports precise vblank timestamp query.
[    1.560585] radeon 0000:01:00.0: radeon: MSI limited to 32-bit
[    1.560638] radeon 0000:01:00.0: radeon: using MSI.
[    1.560682] [drm] radeon: irq initialized.
[    1.603845] thermal LNXTHERM:00: registered as thermal_zone0
[    1.603852] ACPI: Thermal Zone [THRM] (38 C)
[    1.607039] [drm] ring test on 0 succeeded in 1 usecs
[    1.607048] [drm] ring test on 3 succeeded in 2 usecs
[    1.781730] [drm] ring test on 5 succeeded in 1 usecs
[    1.781741] [drm] UVD initialized successfully.
[    1.781954] [drm] ib test on ring 0 succeeded in 0 usecs
[    1.781982] [drm] ib test on ring 3 succeeded in 0 usecs
[    2.020013] sis190: 0000:00:04.0: Using transceiver at address 1 as default
[    2.052273] sis190 0000:00:04.0 eth0: 0000:00:04.0: SiS 191 PCI Gigabit Ethernet adapter at ffffc90000730c00 (IRQ: 19), 00:24:8c:67:18:a0
[    2.052277] sis190 0000:00:04.0 eth0: RGMII mode.
[    2.052284] sis190 0000:00:04.0 eth0: Enabling Auto-negotiation
[    2.084270] ehci-pci 0000:00:03.3: EHCI Host Controller
[    2.084281] ehci-pci 0000:00:03.3: new USB bus registered, assigned bus number 1
[    2.084346] ehci-pci 0000:00:03.3: irq 22, io mem 0xfddfd000
[    2.096035] ehci-pci 0000:00:03.3: USB 2.0 started, EHCI 1.00
[    2.096125] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    2.096128] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    2.096131] usb usb1: Product: EHCI Host Controller
[    2.096133] usb usb1: Manufacturer: Linux 4.6.0-040600-generic ehci_hcd
[    2.096136] usb usb1: SerialNumber: 0000:00:03.3
[    2.096336] hub 1-0:1.0: USB hub found
[    2.096347] hub 1-0:1.0: 8 ports detected
[    2.096633] pata_sis 0000:00:02.5: version 0.5.2
[    2.098553] ohci-pci: OHCI PCI platform driver
[    2.100121] scsi host0: pata_sis
[    2.100283] scsi host1: pata_sis
[    2.100361] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xfff0 irq 14
[    2.100364] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xfff8 irq 15
[    2.100618] ohci-pci 0000:00:03.0: OHCI PCI host controller
[    2.100630] ohci-pci 0000:00:03.0: new USB bus registered, assigned bus number 2
[    2.100675] ohci-pci 0000:00:03.0: irq 20, io mem 0xfddff000
[    2.158064] usb usb2: New USB device found, idVendor=1d6b, idProduct=0001
[    2.158068] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    2.158071] usb usb2: Product: OHCI PCI host controller
[    2.158073] usb usb2: Manufacturer: Linux 4.6.0-040600-generic ohci_hcd
[    2.158075] usb usb2: SerialNumber: 0000:00:03.0
[    2.158266] hub 2-0:1.0: USB hub found
[    2.158279] hub 2-0:1.0: 4 ports detected
[    2.158576] ohci-pci 0000:00:03.1: OHCI PCI host controller
[    2.158584] ohci-pci 0000:00:03.1: new USB bus registered, assigned bus number 3
[    2.158618] ohci-pci 0000:00:03.1: irq 21, io mem 0xfddfe000
[    2.214046] usb usb3: New USB device found, idVendor=1d6b, idProduct=0001
[    2.214049] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    2.214051] usb usb3: Product: OHCI PCI host controller
[    2.214054] usb usb3: Manufacturer: Linux 4.6.0-040600-generic ohci_hcd
[    2.214056] usb usb3: SerialNumber: 0000:00:03.1
[    2.214210] hub 3-0:1.0: USB hub found
[    2.214220] hub 3-0:1.0: 4 ports detected
[    2.216209] sata_sis 0000:00:05.0: version 1.0
[    2.216335] sata_sis 0000:00:05.0: Detected SiS 1183/966/966L/968/680 controller in PATA mode
[    2.217221] scsi host2: sata_sis
[    2.217370] scsi host3: sata_sis
[    2.217443] ata3: PATA max UDMA/133 cmd 0xc800 ctl 0xc400 bmdma 0xb800 irq 17
[    2.217446] ata4: PATA max UDMA/133 cmd 0xc000 ctl 0xbc00 bmdma 0xb808 irq 17
[    2.256127] ata2: port disabled--ignoring
[    2.260016] tsc: Refined TSC clocksource calibration: 2166.743 MHz
[    2.260020] clocksource: tsc: mask: 0xffffffffffffffff max_cycles: 0x1f3b7a14f70, max_idle_ns: 440795245921 ns
[    2.374792] ata3.00: ATA-8: ST9320320AS, 0303, max UDMA/133
[    2.374795] ata3.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    2.379648] ata3.00: configured for UDMA/133
[    2.379828] scsi 2:0:0:0: Direct-Access     ATA      ST9320320AS      0303 PQ: 0 ANSI: 5
[    2.428069] [drm] ib test on ring 5 succeeded
[    2.428786] [drm] Radeon Display Connectors
[    2.428788] [drm] Connector 0:
[    2.428790] [drm]   VGA-1
[    2.428792] [drm]   DDC: 0x7e40 0x7e40 0x7e44 0x7e44 0x7e48 0x7e48 0x7e4c 0x7e4c
[    2.428794] [drm]   Encoders:
[    2.428795] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
[    2.428797] [drm] Connector 1:
[    2.428798] [drm]   LVDS-1
[    2.428801] [drm]   DDC: 0x7f68 0x7f68 0x7f6c 0x7f6c 0x7f70 0x7f70 0x7f74 0x7f74
[    2.428802] [drm]   Encoders:
[    2.428804] [drm]     LCD1: INTERNAL_UNIPHY2
[    2.428805] [drm] Connector 2:
[    2.428806] [drm]   HDMI-A-1
[    2.428808] [drm]   HPD4
[    2.428810] [drm]   DDC: 0x7e50 0x7e50 0x7e54 0x7e54 0x7e58 0x7e58 0x7e5c 0x7e5c
[    2.428811] [drm]   Encoders:
[    2.428812] [drm]     DFP1: INTERNAL_UNIPHY
[    2.572222] ata4.00: ATAPI: HL-DT-ST DVDRAM GSA-T50N, RR07, max UDMA/133
[    2.592219] ata4.00: configured for UDMA/133
[    2.597706] scsi 3:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-T50N  RR07 PQ: 0 ANSI: 5
[    2.614676] sd 2:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    2.614737] sd 2:0:0:0: [sda] Write Protect is off
[    2.614741] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.614765] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.627225] sr 3:0:0:0: [sr0] scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.627230] cdrom: Uniform CD-ROM driver Revision: 3.20
[    2.627408] sr 3:0:0:0: Attached scsi CD-ROM sr0
[    2.668024] usb 1-5: new high-speed USB device number 3 using ehci-pci
[    2.708022] usb 2-2: new full-speed USB device number 2 using ohci-pci
[    2.844262] usb 1-5: New USB device found, idVendor=04f2, idProduct=b071
[    2.844267] usb 1-5: New USB device strings: Mfr=2, Product=1, SerialNumber=3
[    2.844270] usb 1-5: Product: CNF7129
[    2.844272] usb 1-5: Manufacturer: Chicony Electronics Co., Ltd.
[    2.844274] usb 1-5: SerialNumber: SN0001
[    2.932050] usb 2-2: New USB device found, idVendor=046d, idProduct=c332
[    2.932055] usb 2-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    2.932057] usb 2-2: Product: Gaming Mouse G502
[    2.932060] usb 2-2: Manufacturer: Logitech
[    2.932062] usb 2-2: SerialNumber: 0C6735573634
[    2.942641] hidraw: raw HID events driver (C) Jiri Kosina
[    2.962543] usbcore: registered new interface driver usbhid
[    2.962547] usbhid: USB HID core driver
[    2.964957] input: Logitech Gaming Mouse G502 as /devices/pci0000:00/0000:00:03.0/usb2/2-2/2-2:1.0/0003:046D:C332.0001/input/input14
[    2.965708] hid-generic 0003:046D:C332.0001: input,hidraw0: USB HID v1.11 Mouse [Logitech Gaming Mouse G502] on usb-0000:00:03.0-2/input0
[    2.969032]  sda: sda1 sda2 < sda5 > sda3
[    2.969524] sd 2:0:0:0: [sda] Attached SCSI disk
[    2.972295] input: Logitech Gaming Mouse G502 as /devices/pci0000:00/0000:00:03.0/usb2/2-2/2-2:1.1/0003:046D:C332.0002/input/input15
[    3.028219] hid-generic 0003:046D:C332.0002: input,hiddev0,hidraw1: USB HID v1.11 Keyboard [Logitech Gaming Mouse G502] on usb-0000:00:03.0-2/input1
[    3.260108] clocksource: Switched to clocksource tsc
[    3.409070] [drm] fb mappable at 0xC045F000
[    3.409075] [drm] vram apper at 0xC0000000
[    3.409077] [drm] size 4325376
[    3.409078] [drm] fb depth is 24
[    3.409080] [drm]    pitch is 5632
[    3.409200] fbcon: radeondrmfb (fb0) is primary device
[    3.872283] Console: switching to colour frame buffer device 170x48
[    3.875428] radeon 0000:01:00.0: fb0: radeondrmfb frame buffer device
[    3.884058] [drm] Initialized radeon 2.43.0 20080528 for 0000:01:00.0 on minor 0
[    4.755103] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
[    4.959611] random: nonblocking pool is initialized
[    6.563534] systemd[1]: RTC configured in localtime, applying delta of 540 minutes to system time.
[    7.477280] systemd[1]: systemd 229 running in system mode. (+PAM +AUDIT +SELINUX +IMA +APPARMOR +SMACK +SYSVINIT +UTMP +LIBCRYPTSETUP +GCRYPT +GNUTLS +ACL +XZ -LZ4 +SECCOMP +BLKID +ELFUTILS +KMOD -IDN)
[    7.477441] systemd[1]: Detected architecture x86-64.
[    7.504714] systemd[1]: Set hostname to <Torris>.
[   11.650769] systemd[1]: Reached target Remote File Systems (Pre).
[   11.650884] systemd[1]: Listening on fsck to fsckd communication Socket.
[   11.650920] systemd[1]: Listening on Syslog Socket.
[   11.650933] systemd[1]: Reached target User and Group Name Lookups.
[   11.650947] systemd[1]: Reached target Encrypted Volumes.
[   11.651086] systemd[1]: Created slice User and Session Slice.
[   11.651169] systemd[1]: Created slice System Slice.
[   11.651189] systemd[1]: Reached target Slices.
[   11.651230] systemd[1]: Listening on Journal Socket (/dev/log).
[   11.651333] systemd[1]: Listening on Journal Audit Socket.
[   11.651377] systemd[1]: Listening on udev Control Socket.
[   11.651432] systemd[1]: Started Forward Password Requests to Wall Directory Watch.
[   11.651470] systemd[1]: Listening on /dev/initctl Compatibility Named Pipe.
[   11.651515] systemd[1]: Listening on Journal Socket.
[   11.668215] systemd[1]: Starting Uncomplicated firewall...
[   11.816209] systemd[1]: Starting Load Kernel Modules...
[   11.817131] systemd[1]: Started Braille Device Support.
[   11.818258] systemd[1]: Mounting Huge Pages File System...
[   11.819242] systemd[1]: Starting Set console keymap...
[   11.820546] systemd[1]: Starting Create list of required static device nodes for the current kernel...
[   11.820668] systemd[1]: Reached target Remote File Systems.
[   11.822716] systemd[1]: Mounting Debug File System...
[   11.823702] systemd[1]: Started Read required files in advance.
[   11.824209] systemd[1]: Set up automount Arbitrary Executable File Formats File System Automount Point.
[   11.824313] systemd[1]: Listening on udev Kernel Socket.
[   11.825282] systemd[1]: Mounting POSIX Message Queue File System...
[   11.826541] systemd[1]: Starting Journal Service...
[   12.329610] systemd[1]: Started Uncomplicated firewall.
[   12.329918] systemd[1]: Started Create list of required static device nodes for the current kernel.
[   12.335231] systemd[1]: Starting Create Static Device Nodes in /dev...
[   13.021499] systemd[1]: Mounted POSIX Message Queue File System.
[   13.021568] systemd[1]: Mounted Huge Pages File System.
[   13.021593] systemd[1]: Mounted Debug File System.
[   13.467742] lp: driver loaded but no devices found
[   13.572084] ppdev: user-space parallel port driver
[   13.822278] systemd[1]: Started Journal Service.
[   16.089328] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro
[   16.426837] systemd-journald[211]: Received request to flush runtime journal from PID 1
[   17.164797] Monitor-Mwait will be used to enter C-1 state
[   17.164811] Monitor-Mwait will be used to enter C-2 state
[   17.164817] tsc: Marking TSC unstable due to TSC halts in idle
[   17.165050] clocksource: Switched to clocksource hpet
[   17.930533] ACPI: Battery Slot [BAT0] (battery present)
[   18.133645] ACPI: AC Adapter [AC0] (on-line)
[   18.583212] sd 2:0:0:0: Attached scsi generic sg0 type 0
[   18.583277] sr 3:0:0:0: Attached scsi generic sg1 type 5
[   18.712270] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   20.178676] asus_laptop: Asus Laptop Support version 0.42
[   20.178876] asus_laptop:   F50SL model detected
[   20.182553] input: Asus Laptop extra buttons as /devices/platform/asus_laptop/input/input16
[   21.629645] snd_hda_intel 0000:01:00.1: Handle vga_switcheroo audio client
[   21.635835] snd_hda_intel 0000:00:0f.0: CORB reset timeout#1, CORBRP = 0
[   21.726449] media: Linux media interface: v0.10
[   21.743686] input: HDA ATI HDMI HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input17
[   21.858591] snd_hda_codec_realtek hdaudioC0D0: autoconfig for ALC663: line_outs=1 (0x14/0x0/0x0/0x0/0x0) type:speaker
[   21.858598] snd_hda_codec_realtek hdaudioC0D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   21.858601] snd_hda_codec_realtek hdaudioC0D0:    hp_outs=1 (0x21/0x0/0x0/0x0/0x0)
[   21.858604] snd_hda_codec_realtek hdaudioC0D0:    mono: mono_out=0x0
[   21.858606] snd_hda_codec_realtek hdaudioC0D0:    dig-out=0x1e/0x0
[   21.858608] snd_hda_codec_realtek hdaudioC0D0:    inputs:
[   21.858611] snd_hda_codec_realtek hdaudioC0D0:      Internal Mic=0x19
[   21.858614] snd_hda_codec_realtek hdaudioC0D0:      Mic=0x18
[   21.866926] input: HDA SIS966 Mic as /devices/pci0000:00/0000:00:0f.0/sound/card0/input18
[   21.867034] input: HDA SIS966 Headphone as /devices/pci0000:00/0000:00:0f.0/sound/card0/input19
[   22.025885] Linux video capture interface: v2.00
[   22.706168] uvcvideo: Found UVC 1.00 device CNF7129 (04f2:b071)
[   22.729100] uvcvideo 1-5:1.0: Entity type for entity Extension 5 was not initialized!
[   22.729112] uvcvideo 1-5:1.0: Entity type for entity Extension 4 was not initialized!
[   22.729119] uvcvideo 1-5:1.0: Entity type for entity Processing 3 was not initialized!
[   22.729131] uvcvideo 1-5:1.0: Entity type for entity Camera 1 was not initialized!
[   22.729266] input: CNF7129 as /devices/pci0000:00/0000:00:03.3/usb1/1-5/1-5:1.0/input/input20
[   22.729380] usbcore: registered new interface driver uvcvideo
[   22.729382] USB Video Class driver (1.1.1)
[   26.278087] audit: type=1400 audit(1482242039.408:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=498 comm="apparmor_parser"
[   26.278101] audit: type=1400 audit(1482242039.408:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=498 comm="apparmor_parser"
[   26.278108] audit: type=1400 audit(1482242039.408:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-helper" pid=498 comm="apparmor_parser"
[   26.278115] audit: type=1400 audit(1482242039.408:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=498 comm="apparmor_parser"
[   26.439548] audit: type=1400 audit(1482242039.568:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm-guest-session" pid=497 comm="apparmor_parser"
[   26.439563] audit: type=1400 audit(1482242039.568:7): apparmor="STATUS" operation="profile_load" name="chromium" pid=497 comm="apparmor_parser"
[   27.504795] audit: type=1400 audit(1482242040.636:8): apparmor="STATUS" operation="profile_load" name="webbrowser-app" pid=510 comm="apparmor_parser"
[   27.504807] audit: type=1400 audit(1482242040.636:9): apparmor="STATUS" operation="profile_load" name="oxide_helper" pid=510 comm="apparmor_parser"
[   27.705576] audit: type=1400 audit(1482242040.836:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/snapd/snap-confine" pid=515 comm="apparmor_parser"
[   27.705590] audit: type=1400 audit(1482242040.836:11): apparmor="STATUS" operation="profile_load" name="mount-namespace-capture-helper" pid=515 comm="apparmor_parser"
[   28.810708] Adding 3072260k swap on /dev/sda3.  Priority:-1 extents:1 across:3072260k FS
[   35.943894] cgroup: new mount options do not match the existing superblock, will be ignored
[   47.127490] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   47.127663] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   57.172047] sis190 0000:00:04.0 eth0: auto-negotiating...
[   68.195529] fuse init (API version 7.24)
[   86.748068] usb 1-2: new high-speed USB device number 4 using ehci-pci
[   86.885191] usb 1-2: New USB device found, idVendor=0fce, idProduct=01da
[   86.885202] usb 1-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[   86.885208] usb 1-2: Product: E5823
[   86.885213] usb 1-2: Manufacturer: Sony
[   86.885218] usb 1-2: SerialNumber: CB5A29M1B5
[   87.813932] usb 1-2: USB disconnect, device number 4
[   88.368051] usb 1-2: new high-speed USB device number 5 using ehci-pci
[   88.501912] usb 1-2: New USB device found, idVendor=0fce, idProduct=71da
[   88.501920] usb 1-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[   88.501923] usb 1-2: Product: E5823
[   88.501925] usb 1-2: Manufacturer: Sony
[   88.501927] usb 1-2: SerialNumber: CB5A29M1B5
[   89.172690] usbcore: registered new interface driver cdc_ether
[   89.431134] rndis_host 1-2:1.0 usb0: register 'rndis_host' at usb-0000:00:03.3-2, RNDIS device, 4a:8a:a8:88:36:49
[   89.431178] usbcore: registered new interface driver rndis_host
[   89.664612] rndis_host 1-2:1.0 enp0s3f3u2: renamed from usb0
[   89.685112] IPv6: ADDRCONF(NETDEV_UP): enp0s3f3u2: link is not ready
[  280.560078] perf: interrupt took too long (2509 > 2500), lowering kernel.perf_event_max_sample_rate to 79500
[  306.501333] perf: interrupt took too long (3159 > 3136), lowering kernel.perf_event_max_sample_rate to 63250
[  337.809240] perf: interrupt took too long (3965 > 3948), lowering kernel.perf_event_max_sample_rate to 50250
[  380.769020] perf: interrupt took too long (4957 > 4956), lowering kernel.perf_event_max_sample_rate to 40250
[  453.334213] perf: interrupt took too long (6996 > 6196), lowering kernel.perf_event_max_sample_rate to 28500
[  779.210906] perf: interrupt took too long (8805 > 8745), lowering kernel.perf_event_max_sample_rate to 22500


```

sudo lshw -c network

```
torris@Torris:~$ sudo lshw -c network
[sudo] password for torris: 
  *-network               
       description: Ethernet interface
       product: 191 Gigabit Ethernet Adapter
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 02
       serial: 00:24:8c:67:18:a0
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sis190 driverversion=1.4 duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:19 memory:fddfcc00-fddfcc7f ioport:cc00(size=128)
  *-network
       description: Ethernet interface
       physical id: 1
       logical name: enp0s3f3u2
       serial: 4a:8a:a8:88:36:49
       capabilities: ethernet physical
       configuration: broadcast=yes driver=rndis_host driverversion=22-Aug-2005 firmware=RNDIS device ip=192.168.42.12 link=yes multicast=yes


```

sudo nano /home/torris/wireless-info.txt

```

########## wireless info START ##########

Report from: 19 Dec 2016 21:21 JST +0900

Booted last: 19 Dec 2016 00:00 JST +0900

Script from: 08 Jul 2016 02:16 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.1 LTS
Release:    16.04
Codename:    xenial

##### kernel ############################

Linux 4.4.0-53-generic #74-Ubuntu SMP Fri Dec 2 15:59:10 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

00:04.0 Ethernet controller [0200]: Silicon Integrated Systems [SiS] 191 Gigabit Ethernet Adapter [1039:0191] (rev 02)
    Subsystem: ASUSTeK Computer Inc. 191 Gigabit Ethernet Adapter [1043:1815]
    Kernel driver in use: sis190

##### lsusb #############################

Bus 001 Device 003: ID 04f2:b071 Chicony Electronics Co., Ltd 2.0M UVC Webcam / CNF7129
Bus 001 Device 006: ID 0fce:71da Sony Ericsson Mobile Communications AB 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 046d:c332 Logitech, Inc. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 056e:0082 Elecom Co., Ltd 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

##### rfkill ############################

##### lsmod #############################

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp0s3f3u3 Link encap:Ethernet  HWaddr <MAC 'enp0s3f3u3' [IF1]>  
          inet addr:192.168.42.234  Bcast:192.168.42.255  Mask:255.255.255.0
          inet6 addr: fe80::337a:bc5d:a434:698c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1140 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1223 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1121378 (1.1 MB)  TX bytes:189806 (189.8 KB)

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF2]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

lo        no wireless extensions.

enp0s3f3u3  no wireless extensions.

eth0      no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.42.129  0.0.0.0         UG    100    0        0 enp0s3f3u3
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enp0s3f3u3
192.168.42.0    0.0.0.0         255.255.255.0   U     100    0        0 enp0s3f3u3

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root       801     1  0 21:15 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp0s3f3u3
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Sony
GENERAL.PRODUCT:                        E5823
GENERAL.DRIVER:                         rndis_host
GENERAL.DRIVER-VERSION:                 22-Aug-2005
GENERAL.FIRMWARE-VERSION:               RNDIS device
GENERAL.HWADDR:                         <MAC 'enp0s3f3u3' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:03.3/usb1/1-3/1-3:1.0/net/enp0s3f3u3
GENERAL.IP-IFACE:                       enp0s3f3u3
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       5526d5a0-0db4-3054-8928-cec0778eb8fe
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        yes (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   5526d5a0-0db4-3054-8928-cec0778eb8fe | Wired connection 1
IP4.ADDRESS[1]:                         192.168.42.234/24
IP4.GATEWAY:                            192.168.42.129
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.42.129
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        domain_name_servers = 192.168.42.129
DHCP4.OPTION[5]:                        ip_address = 192.168.42.234
DHCP4.OPTION[6]:                        requested_static_routes = 1
DHCP4.OPTION[7]:                        dhcp_server_identifier = 192.168.42.129
DHCP4.OPTION[8]:                        requested_time_offset = 1
DHCP4.OPTION[9]:                        broadcast_address = 192.168.42.255
DHCP4.OPTION[10]:                       requested_interface_mtu = 1
DHCP4.OPTION[11]:                       dhcp_rebinding_time = 3150
DHCP4.OPTION[12]:                       requested_domain_name_servers = 1
DHCP4.OPTION[13]:                       dhcp_message_type = 5
DHCP4.OPTION[14]:                       requested_broadcast_address = 1
DHCP4.OPTION[15]:                       routers = 192.168.42.129
DHCP4.OPTION[16]:                       dhcp_renewal_time = 1800
DHCP4.OPTION[17]:                       requested_domain_name = 1
DHCP4.OPTION[18]:                       requested_routers = 1
DHCP4.OPTION[19]:                       expiry = 1482141150
DHCP4.OPTION[20]:                       requested_wpad = 1
DHCP4.OPTION[21]:                       host_name = Torris
DHCP4.OPTION[22]:                       requested_netbios_scope = 1
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[25]:                       network_number = 192.168.42.0
DHCP4.OPTION[26]:                       requested_domain_search = 1
DHCP4.OPTION[27]:                       vendor_encapsulated_options = ANDROID_METERED
DHCP4.OPTION[28]:                       next_server = 192.168.42.129
DHCP4.OPTION[29]:                       requested_host_name = 1
DHCP4.OPTION[30]:                       dhcp_lease_time = 3600
DHCP4.OPTION[31]:                       requested_ntp_servers = 1
IP6.ADDRESS[1]:                         fe80::337a:bc5d:a434:698c/64
IP6.GATEWAY:                            

GENERAL.DEVICE:                         eth0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Silicon Integrated Systems [SiS]
GENERAL.PRODUCT:                        191 Gigabit Ethernet Adapter
GENERAL.DRIVER:                         sis190
GENERAL.DRIVER-VERSION:                 1.4
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'eth0' [IF2]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:04.0/net/eth0
GENERAL.IP-IFACE:                       
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
GENERAL.METERED:                        unknown
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               off
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/Wi-Fi connection 1]] (600 root)
[connection] id=Wi-Fi connection 1 | type=wifi | permissions=
[wifi] mac-address-blacklist= | ssid=3101A02D
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Asia/Tokyo (based on set time zone)

country 00: DFS-UNSET
    (2402 - 2472 @ 40), (6, 20), (N/A)
    (2457 - 2482 @ 40), (6, 20), (N/A), PASSIVE-SCAN
    (2474 - 2494 @ 20), (6, 20), (N/A), NO-OFDM, PASSIVE-SCAN
    (5170 - 5250 @ 160), (6, 20), (N/A), PASSIVE-SCAN
    (5250 - 5330 @ 160), (6, 20), (0 ms), DFS, PASSIVE-SCAN
    (5490 - 5730 @ 160), (6, 20), (0 ms), DFS, PASSIVE-SCAN
    (5735 - 5835 @ 80), (6, 20), (N/A), PASSIVE-SCAN
    (57240 - 63720 @ 2160), (N/A, 0), (N/A)

##### iwlist channels ###################

lo        no frequency information.

enp0s3f3u3  no frequency information.

eth0      no frequency information.

##### iwlist scan #######################

lo        Interface doesn't support scanning.

enp0s3f3u3  Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

##### module infos ######################

##### module parameters #################

##### /etc/modules ######################

lp

##### modprobe options ##################

[/etc/modprobe.d/ath10k_core.conf]
options ath10k_core skip_otp=Y

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac

[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off

[/etc/modprobe.d/custom-wireless.conf]
options ath5k nohwcrypt

[/etc/modprobe.d/intel-microcode-blacklist.conf]
blacklist microcode

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x1039:0x0191 (sis190)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF2]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

##### dmesg #############################

[   53.193948] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready (repeated 2 times)
[   63.224067] sis190 0000:00:04.0 eth0: auto-negotiating...
[  229.793395] rndis_host 1-3:1.0 enp0s3f3u3: renamed from usb0
[  229.828823] IPv6: ADDRCONF(NETDEV_UP): enp0s3f3u3: link is not ready

########## wireless info END ############


```

I've never posted a thread anywhere because i've believed that the great internet has all the answers, but this seems to be quite troublesome because i feel like i have read every page there is now :P


I hope my post isn't too messed up

Thanks for any help

Kind Regards from Tor Olav

---

### Post by el3m3ntor on 2016-12-23
Solved it on my own, it turned out that by turning off wifi hard block and turn on "new card" hard block i was able to boot ubuntu and use WiFi.
Asus is NOT trying to do anything about Ubuntu/Linux support.. :/

---

