---
title: "RTL8723BE Ubuntu 14.04. Wifi Connects, Drops and can't reconnect"
date: 2015-05-10
forum: Networking &amp; Wireless
---

### Post by davidlillie23 on 2015-05-10
Wifi connects for about 15-30 and then disconnects.  I am unable to reconnect.  I've tried some of the other solutions posted but none seem to have made a difference.  My laptop is a Lenovo G50.  I did notice this issue on the Live CD also.  Reboot resolves the issue for about 30mins or so.  I a bit of a newbie to Ubuntu.  Thanks in advance for the help and let me know what other logs may be needed.

Dmesg Code

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.00000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 3.16.0-30-generic (buildd@kissel) (gcc version 4.8.2 (Ubuntu 4.8.2-19ubuntu1) ) #40~14.04.1-Ubuntu SMP Thu Jan 15 17:43:14 UTC 2015 (Ubuntu 3.16.0-30.40~14.04.1-generic 3.16.7-ckt3)
[    0.000000] Command line: BOOT_IMAGE=/vmlinuz-3.16.0-30-generic.efi.signed root=/dev/mapper/ubuntu--vg-root ro quiet splash
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000006dfff] usable
[    0.000000] BIOS-e820: [mem 0x000000000006e000-0x000000000006ffff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x0000000000070000-0x0000000000085fff] usable
[    0.000000] BIOS-e820: [mem 0x0000000000086000-0x00000000000bffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x000000009a0bbfff] usable
[    0.000000] BIOS-e820: [mem 0x000000009a0bc000-0x000000009aabbfff] reserved
[    0.000000] BIOS-e820: [mem 0x000000009aabc000-0x000000009f2befff] usable
[    0.000000] BIOS-e820: [mem 0x000000009f2bf000-0x000000009f4befff] type 20
[    0.000000] BIOS-e820: [mem 0x000000009f4bf000-0x000000009fabefff] reserved
[    0.000000] BIOS-e820: [mem 0x000000009fabf000-0x000000009fbbefff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x000000009fbbf000-0x000000009fbfefff] ACPI data
[    0.000000] BIOS-e820: [mem 0x000000009fbff000-0x000000009fbfffff] usable
[    0.000000] BIOS-e820: [mem 0x000000009fc00000-0x00000000dfffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000f8000000-0x00000000fbffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec01fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec10000-0x00000000fec10fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed80000-0x00000000fed80fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ff800000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000019effffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] efi: EFI v2.31 by INSYDE Corp.
[    0.000000] efi:  ACPI=0x9fbfe000  ACPI 2.0=0x9fbfe014  SMBIOS=0x9fabef98 
[    0.000000] efi: mem00: type=3, attr=0xf, range=[0x0000000000000000-0x0000000000001000) (0MB)
[    0.000000] efi: mem01: type=7, attr=0xf, range=[0x0000000000001000-0x000000000006e000) (0MB)
[    0.000000] efi: mem02: type=10, attr=0xf, range=[0x000000000006e000-0x0000000000070000) (0MB)
[    0.000000] efi: mem03: type=7, attr=0xf, range=[0x0000000000070000-0x0000000000080000) (0MB)
[    0.000000] efi: mem04: type=3, attr=0xf, range=[0x0000000000080000-0x0000000000082000) (0MB)
[    0.000000] efi: mem05: type=7, attr=0xf, range=[0x0000000000082000-0x0000000000086000) (0MB)
[    0.000000] efi: mem06: type=0, attr=0xf, range=[0x0000000000086000-0x0000000000088000) (0MB)
[    0.000000] efi: mem07: type=6, attr=0x800000000000000f, range=[0x0000000000088000-0x00000000000a0000) (0MB)
[    0.000000] efi: mem08: type=2, attr=0xf, range=[0x0000000000100000-0x00000000014e2000) (19MB)
[    0.000000] efi: mem09: type=7, attr=0xf, range=[0x00000000014e2000-0x0000000002000000) (11MB)
[    0.000000] efi: mem10: type=2, attr=0xf, range=[0x0000000002000000-0x00000000033e2000) (19MB)
[    0.000000] efi: mem11: type=7, attr=0xf, range=[0x00000000033e2000-0x0000000034744000) (787MB)
[    0.000000] efi: mem12: type=2, attr=0xf, range=[0x0000000034744000-0x000000003639a000) (28MB)
[    0.000000] efi: mem13: type=7, attr=0xf, range=[0x000000003639a000-0x0000000070eca000) (939MB)
[    0.000000] efi: mem14: type=2, attr=0xf, range=[0x0000000070eca000-0x0000000097ac0000) (619MB)
[    0.000000] efi: mem15: type=4, attr=0xf, range=[0x0000000097ac0000-0x0000000097ae0000) (0MB)
[    0.000000] efi: mem16: type=7, attr=0xf, range=[0x0000000097ae0000-0x00000000992b4000) (23MB)
[    0.000000] efi: mem17: type=2, attr=0xf, range=[0x00000000992b4000-0x0000000099488000) (1MB)
[    0.000000] efi: mem18: type=4, attr=0xf, range=[0x0000000099488000-0x000000009a0bc000) (12MB)
[    0.000000] efi: mem19: type=0, attr=0xf, range=[0x000000009a0bc000-0x000000009aabc000) (10MB)
[    0.000000] efi: mem20: type=7, attr=0xf, range=[0x000000009aabc000-0x000000009aabd000) (0MB)
[    0.000000] efi: mem21: type=2, attr=0xf, range=[0x000000009aabd000-0x000000009aabf000) (0MB)
[    0.000000] efi: mem22: type=7, attr=0xf, range=[0x000000009aabf000-0x000000009ab8b000) (0MB)
[    0.000000] efi: mem23: type=1, attr=0xf, range=[0x000000009ab8b000-0x000000009acbf000) (1MB)
[    0.000000] efi: mem24: type=7, attr=0xf, range=[0x000000009acbf000-0x000000009c7b2000) (26MB)
[    0.000000] efi: mem25: type=4, attr=0xf, range=[0x000000009c7b2000-0x000000009d06a000) (8MB)
[    0.000000] efi: mem26: type=7, attr=0xf, range=[0x000000009d06a000-0x000000009d06c000) (0MB)
[    0.000000] efi: mem27: type=4, attr=0xf, range=[0x000000009d06c000-0x000000009d1b7000) (1MB)
[    0.000000] efi: mem28: type=7, attr=0xf, range=[0x000000009d1b7000-0x000000009d1bc000) (0MB)
[    0.000000] efi: mem29: type=4, attr=0xf, range=[0x000000009d1bc000-0x000000009d1c4000) (0MB)
[    0.000000] efi: mem30: type=7, attr=0xf, range=[0x000000009d1c4000-0x000000009d1c6000) (0MB)
[    0.000000] efi: mem31: type=4, attr=0xf, range=[0x000000009d1c6000-0x000000009d1ed000) (0MB)
[    0.000000] efi: mem32: type=7, attr=0xf, range=[0x000000009d1ed000-0x000000009d1ee000) (0MB)
[    0.000000] efi: mem33: type=4, attr=0xf, range=[0x000000009d1ee000-0x000000009d37a000) (1MB)
[    0.000000] efi: mem34: type=7, attr=0xf, range=[0x000000009d37a000-0x000000009d384000) (0MB)
[    0.000000] efi: mem35: type=4, attr=0xf, range=[0x000000009d384000-0x000000009d396000) (0MB)
[    0.000000] efi: mem36: type=7, attr=0xf, range=[0x000000009d396000-0x000000009d3b6000) (0MB)
[    0.000000] efi: mem37: type=4, attr=0xf, range=[0x000000009d3b6000-0x000000009ecbf000) (25MB)
[    0.000000] efi: mem38: type=7, attr=0xf, range=[0x000000009ecbf000-0x000000009ef0d000) (2MB)
[    0.000000] efi: mem39: type=2, attr=0xf, range=[0x000000009ef0d000-0x000000009ef17000) (0MB)
[    0.000000] efi: mem40: type=3, attr=0xf, range=[0x000000009ef17000-0x000000009f2bf000) (3MB)
[    0.000000] efi: mem41: type=5, attr=0x800000000000000f, range=[0x000000009f2bf000-0x000000009f4bf000) (2MB)
[    0.000000] efi: mem42: type=6, attr=0x800000000000000f, range=[0x000000009f4bf000-0x000000009f6bf000) (2MB)
[    0.000000] efi: mem43: type=0, attr=0xf, range=[0x000000009f6bf000-0x000000009fabf000) (4MB)
[    0.000000] efi: mem44: type=10, attr=0xf, range=[0x000000009fabf000-0x000000009fbbf000) (1MB)
[    0.000000] efi: mem45: type=9, attr=0xf, range=[0x000000009fbbf000-0x000000009fbff000) (0MB)
[    0.000000] efi: mem46: type=4, attr=0xf, range=[0x000000009fbff000-0x000000009fc00000) (0MB)
[    0.000000] efi: mem47: type=7, attr=0xf, range=[0x0000000100000000-0x000000019f000000) (2544MB)
[    0.000000] efi: mem48: type=0, attr=0x0, range=[0x00000000000a0000-0x00000000000c0000) (0MB)
[    0.000000] efi: mem49: type=0, attr=0x0, range=[0x000000009fc00000-0x00000000e0000000) (1028MB)
[    0.000000] efi: mem50: type=11, attr=0x8000000000000001, range=[0x00000000f8000000-0x00000000fc000000) (64MB)
[    0.000000] efi: mem51: type=11, attr=0x8000000000000001, range=[0x00000000fec00000-0x00000000fec02000) (0MB)
[    0.000000] efi: mem52: type=11, attr=0x8000000000000001, range=[0x00000000fec10000-0x00000000fec11000) (0MB)
[    0.000000] efi: mem53: type=11, attr=0x8000000000000001, range=[0x00000000fed80000-0x00000000fed81000) (0MB)
[    0.000000] efi: mem54: type=11, attr=0x8000000000000001, range=[0x00000000fee00000-0x00000000fee01000) (0MB)
[    0.000000] efi: mem55: type=11, attr=0x8000000000000000, range=[0x00000000ff800000-0x0000000100000000) (8MB)
[    0.000000] SMBIOS 2.8 present.
[    0.000000] DMI: LENOVO 80E3/Lancer 5B2, BIOS A2CN27WW(V1.09) 12/12/2014
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] AGP: No AGP bridge found
[    0.000000] e820: last_pfn = 0x19f000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-FFFFF write-through
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0000000000 mask FF80000000 write-back
[    0.000000]   1 base 0080000000 mask FFE0000000 write-back
[    0.000000]   2 base 009FBA8000 mask FFFFFFF000 uncachable
[    0.000000]   3 base 00FF800000 mask FFFF800000 write-protect
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] TOM2: 000000019f000000 aka 6640M
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820: last_pfn = 0x9fc00 max_arch_pfn = 0x400000000
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] Base memory trampoline at [ffff880000076000] 76000 size 24576
[    0.000000] Using GB pages for direct mapping
[    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
[    0.000000]  [mem 0x00000000-0x000fffff] page 4k
[    0.000000] BRK [0x02fbe000, 0x02fbefff] PGTABLE
[    0.000000] BRK [0x02fbf000, 0x02fbffff] PGTABLE
[    0.000000] BRK [0x02fc0000, 0x02fc0fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x19ee00000-0x19effffff]
[    0.000000]  [mem 0x19ee00000-0x19effffff] page 2M
[    0.000000] BRK [0x02fc1000, 0x02fc1fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x19c000000-0x19edfffff]
[    0.000000]  [mem 0x19c000000-0x19edfffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x180000000-0x19bffffff]
[    0.000000]  [mem 0x180000000-0x19bffffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x00100000-0x9a0bbfff]
[    0.000000]  [mem 0x00100000-0x001fffff] page 4k
[    0.000000]  [mem 0x00200000-0x3fffffff] page 2M
[    0.000000]  [mem 0x40000000-0x7fffffff] page 1G
[    0.000000]  [mem 0x80000000-0x99ffffff] page 2M
[    0.000000]  [mem 0x9a000000-0x9a0bbfff] page 4k
[    0.000000] init_memory_mapping: [mem 0x9aabc000-0x9f2befff]
[    0.000000]  [mem 0x9aabc000-0x9abfffff] page 4k
[    0.000000]  [mem 0x9ac00000-0x9f1fffff] page 2M
[    0.000000]  [mem 0x9f200000-0x9f2befff] page 4k
[    0.000000] BRK [0x02fc2000, 0x02fc2fff] PGTABLE
[    0.000000] BRK [0x02fc3000, 0x02fc3fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x9fbff000-0x9fbfffff]
[    0.000000]  [mem 0x9fbff000-0x9fbfffff] page 4k
[    0.000000] init_memory_mapping: [mem 0x100000000-0x17fffffff]
[    0.000000]  [mem 0x100000000-0x17fffffff] page 1G
[    0.000000] RAMDISK: [mem 0x34744000-0x36399fff]
[    0.000000] ACPI: Early table checksum verification disabled
[    0.000000] ACPI: RSDP 0x000000009FBFE014 000024 (v02 LENOVO)
[    0.000000] ACPI: XSDT 0x000000009FBFE120 0000B4 (v01 LENOVO CB-01    00000001      01000013)
[    0.000000] ACPI: FACP 0x000000009FBFC000 00010C (v05 LENOVO CB-01    00000001 ACPI 00040000)
[    0.000000] ACPI: DSDT 0x000000009FBF0000 007201 (v01 LENOVO CB-01    00000001 ACPI 00040000)
[    0.000000] ACPI: FACS 0x000000009FB67000 000040
[    0.000000] ACPI: UEFI 0x000000009FBFD000 000236 (v01 LENOVO CB-01    00000001 ACPI 00040000)
[    0.000000] ACPI: HPET 0x000000009FBFB000 000038 (v01 LENOVO CB-01    00000001 ACPI 00040000)
[    0.000000] ACPI: APIC 0x000000009FBFA000 000090 (v03 LENOVO CB-01    00000001 ACPI 00040000)
[    0.000000] ACPI: MCFG 0x000000009FBF9000 00003C (v01 LENOVO CB-01    00000001 ACPI 00040000)
[    0.000000] ACPI: ASF! 0x000000009FBF8000 0000A5 (v32 LENOVO CB-01    00000001 ACPI 00040000)
[    0.000000] ACPI: BOOT 0x000000009FBEF000 000028 (v01 LENOVO CB-01    00000001 ACPI 00040000)
[    0.000000] ACPI: FPDT 0x000000009FBED000 000044 (v01 LENOVO CB-01    00000001 ACPI 00040000)
[    0.000000] ACPI: MSDM 0x000000009FBEC000 000055 (v03 LENOVO CB-01    00000001 ACPI 00040000)
[    0.000000] ACPI: SSDT 0x000000009FBEB000 000CB4 (v01 LENOVO CB-01    00000001 ACPI 00040000)
[    0.000000] ACPI: SSDT 0x000000009FBE6000 00487A (v02 LENOVO CB-01    00000001 ACPI 00040000)
[    0.000000] ACPI: VFCT 0x000000009FBD7000 00EC84 (v01 LENOVO CB-01    00000001 ACPI 00040000)
[    0.000000] ACPI: SSDT 0x000000009FBD6000 000418 (v01 LENOVO CB-01    00000001 ACPI 00040000)
[    0.000000] ACPI: SSDT 0x000000009FBD4000 001442 (v01 LENOVO CB-01    00000001 ACPI 00040000)
[    0.000000] ACPI: SSDT 0x000000009FBD3000 00008C (v01 LENOVO CB-01    00000001 ACPI 00040000)
[    0.000000] ACPI: SSDT 0x000000009FBD1000 001138 (v01 LENOVO CB-01    00000001 ACPI 00040000)
[    0.000000] ACPI: SSDT 0x000000009FBCF000 000FB4 (v01 LENOVO CB-01    00000001 ACPI 00040000)
[    0.000000] ACPI: BGRT 0x000000009FBD0000 000038 (v01 LENOVO CB-01    00000001 ACPI 00040000)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x000000019effffff]
[    0.000000] Initmem setup node 0 [mem 0x00000000-0x19effffff]
[    0.000000]   NODE_DATA [mem 0x19eff8000-0x19effcfff]
[    0.000000]  [ffffea0000000000-ffffea00067fffff] PMD -> [ffff880199600000-ffff88019e5fffff] on node 0
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00001000-0x00ffffff]
[    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
[    0.000000]   Normal   [mem 0x100000000-0x19effffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00001000-0x0006dfff]
[    0.000000]   node   0: [mem 0x00070000-0x00085fff]
[    0.000000]   node   0: [mem 0x00100000-0x9a0bbfff]
[    0.000000]   node   0: [mem 0x9aabc000-0x9f2befff]
[    0.000000]   node   0: [mem 0x9fbff000-0x9fbfffff]
[    0.000000]   node   0: [mem 0x100000000-0x19effffff]
[    0.000000] On node 0 totalpages: 1300547
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 24 pages reserved
[    0.000000]   DMA zone: 3971 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 10083 pages used for memmap
[    0.000000]   DMA32 zone: 645312 pages, LIFO batch:31
[    0.000000]   Normal zone: 10176 pages used for memmap
[    0.000000]   Normal zone: 651264 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: IOAPIC (id[0x05] address[0xfec01000] gsi_base[24])
[    0.000000] IOAPIC[1]: apic_id 5, version 33, address 0xfec01000, GSI 24-55
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x10228210 base: 0xfed00000
[    0.000000] smpboot: Allowing 4 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 72
[    0.000000] PM: Registered nosave memory: [mem 0x0006e000-0x0006ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x00086000-0x000bffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000c0000-0x000fffff]
[    0.000000] PM: Registered nosave memory: [mem 0x9a0bc000-0x9aabbfff]
[    0.000000] PM: Registered nosave memory: [mem 0x9f2bf000-0x9f4befff]
[    0.000000] PM: Registered nosave memory: [mem 0x9f4bf000-0x9fabefff]
[    0.000000] PM: Registered nosave memory: [mem 0x9fabf000-0x9fbbefff]
[    0.000000] PM: Registered nosave memory: [mem 0x9fbbf000-0x9fbfefff]
[    0.000000] PM: Registered nosave memory: [mem 0x9fc00000-0xdfffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xe0000000-0xf7ffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xf8000000-0xfbffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfc000000-0xfebfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xfec01fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec02000-0xfec0ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec10000-0xfec10fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec11000-0xfed7ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed80000-0xfed80fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed81000-0xfedfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfee00000-0xfee00fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfee01000-0xff7fffff]
[    0.000000] PM: Registered nosave memory: [mem 0xff800000-0xffffffff]
[    0.000000] e820: [mem 0xe0000000-0xf7ffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 28 pages/cpu @ffff88019ec00000 s82304 r8192 d24192 u524288
[    0.000000] pcpu-alloc: s82304 r8192 d24192 u524288 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 1280200
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/vmlinuz-3.16.0-30-generic.efi.signed root=/dev/mapper/ubuntu--vg-root ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] xsave: enabled xstate_bv 0x7, cntxt size 0x340
[    0.000000] AGP: Checking aperture...
[    0.000000] AGP: No AGP bridge found
[    0.000000] AGP: Node 0: aperture [bus addr 0x00000000-0x01ffffff] (32MB)
[    0.000000] AGP: Your BIOS doesn't leave a aperture memory hole
[    0.000000] AGP: Please enable the IOMMU option in the BIOS setup
[    0.000000] AGP: This costs you 64MB of RAM
[    0.000000] AGP: Mapping aperture over RAM [mem 0x8c000000-0x8fffffff] (65536KB)
[    0.000000] PM: Registered nosave memory: [mem 0x8c000000-0x8fffffff]
[    0.000000] Memory: 4888588K/5202188K available (7615K kernel code, 1131K rwdata, 3596K rodata, 1356K init, 1300K bss, 313600K reserved)
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=4.
[    0.000000]     Offload RCU callbacks from all CPUs
[    0.000000]     Offload RCU callbacks from CPUs: 0-3.
[    0.000000] RCU: Adjusting geometry for rcu_fanout_leaf=16, nr_cpu_ids=4
[    0.000000] NR_IRQS:16640 nr_irqs:1024 16
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 20971520 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.000000] tsc: Detected 1996.170 MHz processor
[    0.000055] Calibrating delay loop (skipped), value calculated using timer frequency.. 3992.34 BogoMIPS (lpj=7984680)
[    0.000061] pid_max: default: 32768 minimum: 301
[    0.000077] ACPI: Core revision 20140424
[    0.020982] ACPI: All ACPI Tables successfully acquired
[    0.096592] Security Framework initialized
[    0.096645] AppArmor: AppArmor initialized
[    0.096648] Yama: becoming mindful.
[    0.097471] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.102163] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.104585] Mount-cache hash table entries: 16384 (order: 5, 131072 bytes)
[    0.104609] Mountpoint-cache hash table entries: 16384 (order: 5, 131072 bytes)
[    0.105147] Initializing cgroup subsys memory
[    0.105193] Initializing cgroup subsys devices
[    0.105206] Initializing cgroup subsys freezer
[    0.105212] Initializing cgroup subsys net_cls
[    0.105221] Initializing cgroup subsys blkio
[    0.105229] Initializing cgroup subsys perf_event
[    0.105234] Initializing cgroup subsys net_prio
[    0.105249] Initializing cgroup subsys hugetlb
[    0.105298] tseg: 009fc00000
[    0.105304] CPU: Physical Processor ID: 0
[    0.105305] CPU: Processor Core ID: 0
[    0.114155] mce: CPU supports 6 MCE banks
[    0.114173] Last level iTLB entries: 4KB 512, 2MB 8, 4MB 4
[    0.114173] Last level dTLB entries: 4KB 512, 2MB 256, 4MB 128, 1GB 0
[    0.114173] tlb_flushall_shift: 6
[    0.114397] Freeing SMP alternatives memory: 32K (ffffffff82e6f000 - ffffffff82e77000)
[    0.118416] ftrace: allocating 29209 entries in 115 pages
[    0.137262] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.176959] smpboot: CPU0: AMD A8-6410 APU with AMD Radeon R5 Graphics (fam: 16, model: 30, stepping: 01)
[    0.282847] Performance Events: AMD PMU driver.
[    0.282856] ... version:                0
[    0.282858] ... bit width:              48
[    0.282859] ... generic registers:      4
[    0.282861] ... value mask:             0000ffffffffffff
[    0.282863] ... max period:             00007fffffffffff
[    0.282864] ... fixed-purpose events:   0
[    0.282865] ... event mask:             000000000000000f
[    0.285757] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.285935] x86: Booting SMP configuration:
[    0.285938] .... node  #0, CPUs:      #1 #2 #3
[    0.352106] x86: Booted up 1 node, 4 CPUs
[    0.352117] smpboot: Total of 4 processors activated (15969.36 BogoMIPS)
[    0.353591] devtmpfs: initialized
[    0.360942] evm: security.selinux
[    0.360944] evm: security.SMACK64
[    0.360946] evm: security.SMACK64EXEC
[    0.360947] evm: security.SMACK64TRANSMUTE
[    0.360949] evm: security.SMACK64MMAP
[    0.360950] evm: security.ima
[    0.360952] evm: security.capability
[    0.361087] PM: Registering ACPI NVS region [mem 0x0006e000-0x0006ffff] (8192 bytes)
[    0.361091] PM: Registering ACPI NVS region [mem 0x9fabf000-0x9fbbefff] (1048576 bytes)
[    0.362664] pinctrl core: initialized pinctrl subsystem
[    0.362791] regulator-dummy: no parameters
[    0.362838] RTC time:  2:08:41, date: 05/10/15
[    0.362926] NET: Registered protocol family 16
[    0.363175] cpuidle: using governor ladder
[    0.363178] cpuidle: using governor menu
[    0.363351] ACPI: bus type PCI registered
[    0.363355] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.363491] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf8000000-0xfbffffff] (base 0xf8000000)
[    0.363496] PCI: MMCONFIG at [mem 0xf8000000-0xfbffffff] reserved in E820
[    0.363660] PCI: Using configuration type 1 for base access
[    0.367634] ACPI: Added _OSI(Module Device)
[    0.367639] ACPI: Added _OSI(Processor Device)
[    0.367641] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.367643] ACPI: Added _OSI(Processor Aggregator Device)
[    0.371551] ACPI: Executed 1 blocks of module-level executable AML code
[    0.377195] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.384738] ACPI: Interpreter enabled
[    0.384752] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20140424/hwxface-580)
[    0.384761] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20140424/hwxface-580)
[    0.384783] ACPI: (supports S0 S3 S4 S5)
[    0.384786] ACPI: Using IOAPIC for interrupt routing
[    0.385037] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.385653] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[    0.386323] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[    0.443133] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.443148] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    0.443469] acpi PNP0A08:00: _OSC: OS now controls [PCIeHotplug PME AER PCIeCapability]
[    0.443708] acpi PNP0A08:00: [Firmware Info]: MMCONFIG for domain 0000 [bus 00-3f] only partially covers this bridge
[    0.443920] PCI host bridge to bus 0000:00
[    0.443926] pci_bus 0000:00: root bus resource [bus 00-ff]
[    0.443929] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
[    0.443933] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
[    0.443936] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    0.443939] pci_bus 0000:00: root bus resource [mem 0x000c0000-0x000c3fff]
[    0.443942] pci_bus 0000:00: root bus resource [mem 0x000c4000-0x000c7fff]
[    0.443945] pci_bus 0000:00: root bus resource [mem 0x000c8000-0x000cbfff]
[    0.443947] pci_bus 0000:00: root bus resource [mem 0x000cc000-0x000cffff]
[    0.443950] pci_bus 0000:00: root bus resource [mem 0x000d0000-0x000d3fff]
[    0.443953] pci_bus 0000:00: root bus resource [mem 0x000d4000-0x000d7fff]
[    0.443955] pci_bus 0000:00: root bus resource [mem 0x000d8000-0x000dbfff]
[    0.443958] pci_bus 0000:00: root bus resource [mem 0x000dc000-0x000dffff]
[    0.443961] pci_bus 0000:00: root bus resource [mem 0x000e0000-0x000e3fff]
[    0.443964] pci_bus 0000:00: root bus resource [mem 0x000e4000-0x000e7fff]
[    0.443966] pci_bus 0000:00: root bus resource [mem 0x000e8000-0x000ebfff]
[    0.443969] pci_bus 0000:00: root bus resource [mem 0x000ec000-0x000effff]
[    0.443972] pci_bus 0000:00: root bus resource [mem 0xe0000000-0xf7ffffff]
[    0.443975] pci_bus 0000:00: root bus resource [mem 0xfc000000-0xfed3ffff]
[    0.443977] pci_bus 0000:00: root bus resource [mem 0xfed45000-0xffffffff]
[    0.443987] pci 0000:00:00.0: [1022:1566] type 00 class 0x060000
[    0.444111] pci 0000:00:01.0: [1002:9851] type 00 class 0x030000
[    0.444127] pci 0000:00:01.0: reg 0x10: [mem 0xe0000000-0xefffffff 64bit pref]
[    0.444137] pci 0000:00:01.0: reg 0x18: [mem 0xf0000000-0xf07fffff 64bit pref]
[    0.444145] pci 0000:00:01.0: reg 0x20: [io  0x4000-0x40ff]
[    0.444152] pci 0000:00:01.0: reg 0x24: [mem 0xf0c00000-0xf0c3ffff]
[    0.444159] pci 0000:00:01.0: reg 0x30: [mem 0xfffe0000-0xffffffff pref]
[    0.444200] pci 0000:00:01.0: supports D1 D2
[    0.444202] pci 0000:00:01.0: PME# supported from D1 D2 D3hot
[    0.444309] pci 0000:00:01.1: [1002:9840] type 00 class 0x040300
[    0.444323] pci 0000:00:01.1: reg 0x10: [mem 0xf0c60000-0xf0c63fff 64bit]
[    0.444378] pci 0000:00:01.1: supports D1 D2
[    0.444463] pci 0000:00:02.0: [1022:156b] type 00 class 0x060000
[    0.444572] pci 0000:00:02.3: [1022:1439] type 01 class 0x060400
[    0.444636] pci 0000:00:02.3: PME# supported from D0 D3hot D3cold
[    0.444738] pci 0000:00:02.4: [1022:1439] type 01 class 0x060400
[    0.444801] pci 0000:00:02.4: PME# supported from D0 D3hot D3cold
[    0.444850] pci 0000:00:02.4: System wakeup disabled by ACPI
[    0.444921] pci 0000:00:08.0: [1022:1537] type 00 class 0x108000
[    0.444935] pci 0000:00:08.0: reg 0x10: [mem 0xf0c40000-0xf0c5ffff 64bit pref]
[    0.444942] pci 0000:00:08.0: reg 0x18: [mem 0xf0900000-0xf09fffff]
[    0.444949] pci 0000:00:08.0: reg 0x1c: [mem 0xf0c70000-0xf0c70fff]
[    0.444959] pci 0000:00:08.0: reg 0x24: [mem 0xf0c6a000-0xf0c6bfff]
[    0.445081] pci 0000:00:10.0: [1022:7814] type 00 class 0x0c0330
[    0.445102] pci 0000:00:10.0: reg 0x10: [mem 0xf0c68000-0xf0c69fff 64bit]
[    0.445192] pci 0000:00:10.0: PME# supported from D0 D3hot D3cold
[    0.445244] pci 0000:00:10.0: System wakeup disabled by ACPI
[    0.445307] pci 0000:00:11.0: [1022:7801] type 00 class 0x010601
[    0.445325] pci 0000:00:11.0: reg 0x10: [io  0x4118-0x411f]
[    0.445334] pci 0000:00:11.0: reg 0x14: [io  0x4124-0x4127]
[    0.445343] pci 0000:00:11.0: reg 0x18: [io  0x4110-0x4117]
[    0.445352] pci 0000:00:11.0: reg 0x1c: [io  0x4120-0x4123]
[    0.445360] pci 0000:00:11.0: reg 0x20: [io  0x4100-0x410f]
[    0.445369] pci 0000:00:11.0: reg 0x24: [mem 0xf0c6f000-0xf0c6f3ff]
[    0.445413] pci 0000:00:11.0: PME# supported from D3hot
[    0.445511] pci 0000:00:12.0: [1022:7808] type 00 class 0x0c0320
[    0.445528] pci 0000:00:12.0: reg 0x10: [mem 0xf0c6e000-0xf0c6e0ff]
[    0.445593] pci 0000:00:12.0: supports D1 D2
[    0.445596] pci 0000:00:12.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.445639] pci 0000:00:12.0: System wakeup disabled by ACPI
[    0.445699] pci 0000:00:13.0: [1022:7808] type 00 class 0x0c0320
[    0.445716] pci 0000:00:13.0: reg 0x10: [mem 0xf0c6d000-0xf0c6d0ff]
[    0.445781] pci 0000:00:13.0: supports D1 D2
[    0.445784] pci 0000:00:13.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.445829] pci 0000:00:13.0: System wakeup disabled by ACPI
[    0.445885] pci 0000:00:14.0: [1022:780b] type 00 class 0x0c0500
[    0.446021] pci 0000:00:14.2: [1022:780d] type 00 class 0x040300
[    0.446041] pci 0000:00:14.2: reg 0x10: [mem 0xf0c64000-0xf0c67fff 64bit]
[    0.446102] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
[    0.446194] pci 0000:00:14.3: [1022:780e] type 00 class 0x060100
[    0.446333] pci 0000:00:14.7: [1022:7813] type 00 class 0x080501
[    0.446351] pci 0000:00:14.7: reg 0x10: [mem 0xf0c6c000-0xf0c6c0ff 64bit]
[    0.446404] pci 0000:00:14.7: PME# supported from D3cold
[    0.446496] pci 0000:00:18.0: [1022:1580] type 00 class 0x060000
[    0.446587] pci 0000:00:18.1: [1022:1581] type 00 class 0x060000
[    0.446675] pci 0000:00:18.2: [1022:1582] type 00 class 0x060000
[    0.446764] pci 0000:00:18.3: [1022:1583] type 00 class 0x060000
[    0.446868] pci 0000:00:18.4: [1022:1584] type 00 class 0x060000
[    0.446956] pci 0000:00:18.5: [1022:1585] type 00 class 0x060000
[    0.447154] pci 0000:01:00.0: [10ec:b723] type 00 class 0x028000
[    0.447175] pci 0000:01:00.0: reg 0x10: [io  0x3000-0x30ff]
[    0.447204] pci 0000:01:00.0: reg 0x18: [mem 0xf0b00000-0xf0b03fff 64bit]
[    0.447305] pci 0000:01:00.0: supports D1 D2
[    0.447307] pci 0000:01:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.454981] pci 0000:00:02.3: PCI bridge to [bus 01]
[    0.454993] pci 0000:00:02.3:   bridge window [io  0x3000-0x3fff]
[    0.454998] pci 0000:00:02.3:   bridge window [mem 0xf0b00000-0xf0bfffff]
[    0.455178] pci 0000:02:00.0: [10ec:8168] type 00 class 0x020000
[    0.455200] pci 0000:02:00.0: reg 0x10: [io  0x2000-0x20ff]
[    0.455226] pci 0000:02:00.0: reg 0x18: [mem 0xf0a04000-0xf0a04fff 64bit]
[    0.455243] pci 0000:02:00.0: reg 0x20: [mem 0xf0a00000-0xf0a03fff 64bit]
[    0.455331] pci 0000:02:00.0: supports D1 D2
[    0.455334] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.462989] pci 0000:00:02.4: PCI bridge to [bus 02]
[    0.463001] pci 0000:00:02.4:   bridge window [io  0x2000-0x2fff]
[    0.463006] pci 0000:00:02.4:   bridge window [mem 0xf0a00000-0xf0afffff]
[    0.475356] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 10 11 12 14 15) *0
[    0.475448] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 10 11 12 14 15) *0
[    0.475548] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 10 11 12 14 15) *0
[    0.475646] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 10 11 12 14 15) *0
[    0.475728] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 11 12 14 15) *0
[    0.475793] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 10 11 12 14 15) *0
[    0.475857] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10 11 12 14 15) *0
[    0.475921] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 10 11 12 14 15) *0
[    0.476117] ACPI: Enabled 4 GPEs in block 00 to 1F
[    0.476230] ACPI : EC: GPE = 0x3, I/O: command/status = 0x66, data = 0x62
[    0.476469] vgaarb: setting as boot device: PCI:0000:00:01.0
[    0.476473] vgaarb: device added: PCI:0000:00:01.0,decodes=io+mem,owns=io+mem,locks=none
[    0.476481] vgaarb: loaded
[    0.476484] vgaarb: bridge control possible 0000:00:01.0
[    0.476867] SCSI subsystem initialized
[    0.476948] libata version 3.00 loaded.
[    0.476994] ACPI: bus type USB registered
[    0.477025] usbcore: registered new interface driver usbfs
[    0.477048] usbcore: registered new interface driver hub
[    0.477091] usbcore: registered new device driver usb
[    0.477375] PCI: Using ACPI for IRQ routing
[    0.478938] PCI: pci_cache_line_size set to 64 bytes
[    0.479000] e820: reserve RAM buffer [mem 0x0006e000-0x0006ffff]
[    0.479003] e820: reserve RAM buffer [mem 0x00086000-0x0008ffff]
[    0.479005] e820: reserve RAM buffer [mem 0x9a0bc000-0x9bffffff]
[    0.479007] e820: reserve RAM buffer [mem 0x9f2bf000-0x9fffffff]
[    0.479009] e820: reserve RAM buffer [mem 0x9fc00000-0x9fffffff]
[    0.479012] e820: reserve RAM buffer [mem 0x19f000000-0x19fffffff]
[    0.479190] NetLabel: Initializing
[    0.479192] NetLabel:  domain hash size = 128
[    0.479194] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.479214] NetLabel:  unlabeled traffic allowed by default
[    0.479331] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.479336] hpet0: 3 comparators, 32-bit 14.318180 MHz counter
[    0.482422] Switched to clocksource hpet
[    0.490361] AppArmor: AppArmor Filesystem Enabled
[    0.490481] pnp: PnP ACPI init
[    0.490654] ACPI: bus type PNP registered
[    0.502961] system 00:00: [mem 0xfec00000-0xfec01fff] could not be reserved
[    0.502969] system 00:00: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.502974] system 00:00: [mem 0xff000000-0xff000fff] has been reserved
[    0.502981] system 00:00: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.503557] pnp 00:01: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.503672] pnp 00:02: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.503744] pnp 00:03: Plug and Play ACPI device, IDs ETD0624 ETD0000 PNP0f13 (active)
[    0.503833] system 00:04: [io  0x0400-0x04cf] could not be reserved
[    0.503837] system 00:04: [io  0x04d0-0x04d1] has been reserved
[    0.503844] system 00:04: [io  0x04d6] has been reserved
[    0.503848] system 00:04: [io  0x0680-0x06ff] has been reserved
[    0.503852] system 00:04: [io  0x077a] has been reserved
[    0.503855] system 00:04: [io  0x0c00-0x0c01] has been reserved
[    0.503859] system 00:04: [io  0x0c14] has been reserved
[    0.503863] system 00:04: [io  0x0c50-0x0c52] has been reserved
[    0.503866] system 00:04: [io  0x0c6c] has been reserved
[    0.503870] system 00:04: [io  0x0c6f] has been reserved
[    0.503873] system 00:04: [io  0x0cd0-0x0cdb] has been reserved
[    0.503877] system 00:04: [io  0x0840-0x0847] has been reserved
[    0.503882] system 00:04: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.504015] system 00:05: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.504020] system 00:05: [mem 0xff800000-0xffffffff] has been reserved
[    0.504024] system 00:05: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.519140] pnp: PnP ACPI: found 6 devices
[    0.519147] ACPI: bus type PNP unregistered
[    0.527570] pci 0000:00:01.0: can't claim BAR 6 [mem 0xfffe0000-0xffffffff pref]: address conflict with reserved [mem 0xff800000-0xffffffff]
[    0.527593] pci 0000:00:02.3: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 01] add_size 200000
[    0.527609] pci 0000:00:02.3: res[15]=[mem 0x00100000-0x000fffff 64bit pref] get_res_add_size add_size 200000
[    0.527632] pci 0000:00:02.3: BAR 15: assigned [mem 0xf0d00000-0xf0efffff 64bit pref]
[    0.527642] pci 0000:00:01.0: BAR 6: assigned [mem 0xf0800000-0xf081ffff pref]
[    0.527647] pci 0000:00:02.3: PCI bridge to [bus 01]
[    0.527651] pci 0000:00:02.3:   bridge window [io  0x3000-0x3fff]
[    0.527657] pci 0000:00:02.3:   bridge window [mem 0xf0b00000-0xf0bfffff]
[    0.527661] pci 0000:00:02.3:   bridge window [mem 0xf0d00000-0xf0efffff 64bit pref]
[    0.527667] pci 0000:00:02.4: PCI bridge to [bus 02]
[    0.527671] pci 0000:00:02.4:   bridge window [io  0x2000-0x2fff]
[    0.527675] pci 0000:00:02.4:   bridge window [mem 0xf0a00000-0xf0afffff]
[    0.527683] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.527686] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.527689] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.527692] pci_bus 0000:00: resource 7 [mem 0x000c0000-0x000c3fff]
[    0.527695] pci_bus 0000:00: resource 8 [mem 0x000c4000-0x000c7fff]
[    0.527697] pci_bus 0000:00: resource 9 [mem 0x000c8000-0x000cbfff]
[    0.527700] pci_bus 0000:00: resource 10 [mem 0x000cc000-0x000cffff]
[    0.527703] pci_bus 0000:00: resource 11 [mem 0x000d0000-0x000d3fff]
[    0.527705] pci_bus 0000:00: resource 12 [mem 0x000d4000-0x000d7fff]
[    0.527708] pci_bus 0000:00: resource 13 [mem 0x000d8000-0x000dbfff]
[    0.527711] pci_bus 0000:00: resource 14 [mem 0x000dc000-0x000dffff]
[    0.527713] pci_bus 0000:00: resource 15 [mem 0x000e0000-0x000e3fff]
[    0.527716] pci_bus 0000:00: resource 16 [mem 0x000e4000-0x000e7fff]
[    0.527719] pci_bus 0000:00: resource 17 [mem 0x000e8000-0x000ebfff]
[    0.527721] pci_bus 0000:00: resource 18 [mem 0x000ec000-0x000effff]
[    0.527724] pci_bus 0000:00: resource 19 [mem 0xe0000000-0xf7ffffff]
[    0.527727] pci_bus 0000:00: resource 20 [mem 0xfc000000-0xfed3ffff]
[    0.527729] pci_bus 0000:00: resource 21 [mem 0xfed45000-0xffffffff]
[    0.527732] pci_bus 0000:01: resource 0 [io  0x3000-0x3fff]
[    0.527735] pci_bus 0000:01: resource 1 [mem 0xf0b00000-0xf0bfffff]
[    0.527738] pci_bus 0000:01: resource 2 [mem 0xf0d00000-0xf0efffff 64bit pref]
[    0.527741] pci_bus 0000:02: resource 0 [io  0x2000-0x2fff]
[    0.527744] pci_bus 0000:02: resource 1 [mem 0xf0a00000-0xf0afffff]
[    0.527789] NET: Registered protocol family 2
[    0.528106] TCP established hash table entries: 65536 (order: 7, 524288 bytes)
[    0.528361] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.528608] TCP: Hash tables configured (established 65536 bind 65536)
[    0.528659] TCP: reno registered
[    0.528676] UDP hash table entries: 4096 (order: 5, 131072 bytes)
[    0.528725] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
[    0.528858] NET: Registered protocol family 1
[    0.528889] pci 0000:00:01.0: Video device with shadowed ROM
[    0.539158] PCI: CLS 64 bytes, default 64
[    0.539280] Trying to unpack rootfs image as initramfs...
[    1.150330] Freeing initrd memory: 29016K (ffff880034744000 - ffff88003639a000)
[    1.150404] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    1.150409] software IO TLB [mem 0x93ac0000-0x97ac0000] (64MB) mapped at [ffff880093ac0000-ffff880097abffff]
[    1.150506] Simple Boot Flag at 0x44 set to 0x1
[    1.150709] perf: AMD NB counters detected
[    1.150713] perf: AMD L2I counters detected
[    1.150818] microcode: CPU0: patch_level=0x07030104
[    1.150828] microcode: CPU1: patch_level=0x07030104
[    1.150834] microcode: CPU2: patch_level=0x07030104
[    1.150844] microcode: CPU3: patch_level=0x07030104
[    1.150936] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    1.150942] LVT offset 0 assigned for vector 0x400
[    1.150960] perf: AMD IBS detected (0x000000ff)
[    1.150995] Scanning for low memory corruption every 60 seconds
[    1.151493] futex hash table entries: 1024 (order: 4, 65536 bytes)
[    1.151521] Initialise system trusted keyring
[    1.151553] audit: initializing netlink subsys (disabled)
[    1.151577] audit: type=2000 audit(1431223721.972:1): initialized
[    1.152096] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.154616] zpool: loaded
[    1.154620] zbud: loaded
[    1.154848] VFS: Disk quotas dquot_6.5.2
[    1.154903] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.155665] fuse init (API version 7.23)
[    1.155799] msgmni has been set to 9710
[    1.155883] Key type big_key registered
[    1.156430] Key type asymmetric registered
[    1.156435] Asymmetric key parser 'x509' registered
[    1.156490] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    1.156566] io scheduler noop registered
[    1.156570] io scheduler deadline registered (default)
[    1.156649] io scheduler cfq registered
[    1.156780] pcieport 0000:00:02.3: device [1022:1439] has invalid IRQ; check vendor BIOS
[    1.156932] pcieport 0000:00:02.3: irq 72 for MSI/MSI-X
[    1.157021] pcieport 0000:00:02.4: device [1022:1439] has invalid IRQ; check vendor BIOS
[    1.157117] pcieport 0000:00:02.4: irq 73 for MSI/MSI-X
[    1.157228] pcieport 0000:00:02.3: Signaling PME through PCIe PME interrupt
[    1.157232] pci 0000:01:00.0: Signaling PME through PCIe PME interrupt
[    1.157237] pcie_pme 0000:00:02.3:pcie01: service driver pcie_pme loaded
[    1.157265] pcieport 0000:00:02.4: Signaling PME through PCIe PME interrupt
[    1.157269] pci 0000:02:00.0: Signaling PME through PCIe PME interrupt
[    1.157273] pcie_pme 0000:00:02.4:pcie01: service driver pcie_pme loaded
[    1.157299] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.157359] pciehp 0000:00:02.3:pcie04: Slot #0 AttnBtn- AttnInd- PwrInd- PwrCtrl- MRL- Interlock- NoCompl+ LLActRep+
[    1.157402] pciehp 0000:00:02.3:pcie04: service driver pciehp loaded
[    1.157411] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.163344] ACPI: AC Adapter [ACAD] (off-line)
[    1.163786] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    1.163792] ACPI: Power Button [PWRB]
[    1.163871] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input1
[    1.170757] ACPI: Lid Switch [LID]
[    1.170880] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    1.170887] ACPI: Power Button [PWRF]
[    1.171026] ACPI: acpi_idle registered with cpuidle
[    1.171593] GHES: HEST is not enabled!
[    1.171777] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.174786] Linux agpgart interface v0.103
[    1.177143] brd: module loaded
[    1.178315] loop: module loaded
[    1.178681] libphy: Fixed MDIO Bus: probed
[    1.178687] tun: Universal TUN/TAP device driver, 1.6
[    1.178689] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.178793] PPP generic driver version 2.4.2
[    1.178869] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.178877] ehci-pci: EHCI PCI platform driver
[    1.179015] ehci-pci 0000:00:12.0: EHCI Host Controller
[    1.179025] ehci-pci 0000:00:12.0: new USB bus registered, assigned bus number 1
[    1.179031] ehci-pci 0000:00:12.0: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    1.179041] ehci-pci 0000:00:12.0: debug port 2
[    1.179090] ehci-pci 0000:00:12.0: irq 18, io mem 0xf0c6e000
[    1.190663] ehci-pci 0000:00:12.0: USB 2.0 started, EHCI 1.00
[    1.190775] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    1.190779] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.190782] usb usb1: Product: EHCI Host Controller
[    1.190785] usb usb1: Manufacturer: Linux 3.16.0-30-generic ehci_hcd
[    1.190788] usb usb1: SerialNumber: 0000:00:12.0
[    1.191346] hub 1-0:1.0: USB hub found
[    1.191359] hub 1-0:1.0: 2 ports detected
[    1.191695] ehci-pci 0000:00:13.0: EHCI Host Controller
[    1.191704] ehci-pci 0000:00:13.0: new USB bus registered, assigned bus number 2
[    1.191710] ehci-pci 0000:00:13.0: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    1.191720] ehci-pci 0000:00:13.0: debug port 2
[    1.191759] ehci-pci 0000:00:13.0: irq 18, io mem 0xf0c6d000
[    1.202655] ehci-pci 0000:00:13.0: USB 2.0 started, EHCI 1.00
[    1.202773] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    1.202777] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.202780] usb usb2: Product: EHCI Host Controller
[    1.202784] usb usb2: Manufacturer: Linux 3.16.0-30-generic ehci_hcd
[    1.202786] usb usb2: SerialNumber: 0000:00:13.0
[    1.203059] hub 2-0:1.0: USB hub found
[    1.203072] hub 2-0:1.0: 2 ports detected
[    1.203330] ehci-platform: EHCI generic platform driver
[    1.203361] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.203370] ohci-pci: OHCI PCI platform driver
[    1.203394] ohci-platform: OHCI generic platform driver
[    1.203410] uhci_hcd: USB Universal Host Controller Interface driver
[    1.203580] xhci_hcd 0000:00:10.0: xHCI Host Controller
[    1.203593] xhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 3
[    1.203820] xhci_hcd 0000:00:10.0: irq 74 for MSI/MSI-X
[    1.203827] xhci_hcd 0000:00:10.0: irq 75 for MSI/MSI-X
[    1.203833] xhci_hcd 0000:00:10.0: irq 76 for MSI/MSI-X
[    1.203838] xhci_hcd 0000:00:10.0: irq 77 for MSI/MSI-X
[    1.203844] xhci_hcd 0000:00:10.0: irq 78 for MSI/MSI-X
[    1.203982] usb usb3: New USB device found, idVendor=1d6b, idProduct=0002
[    1.203985] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.203988] usb usb3: Product: xHCI Host Controller
[    1.203991] usb usb3: Manufacturer: Linux 3.16.0-30-generic xhci_hcd
[    1.203994] usb usb3: SerialNumber: 0000:00:10.0
[    1.204194] hub 3-0:1.0: USB hub found
[    1.204208] hub 3-0:1.0: 2 ports detected
[    1.204465] xhci_hcd 0000:00:10.0: xHCI Host Controller
[    1.204471] xhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 4
[    1.206589] ACPI: Battery Slot [BAT1] (battery present)
[    1.207215] usb usb4: New USB device found, idVendor=1d6b, idProduct=0003
[    1.207219] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.207222] usb usb4: Product: xHCI Host Controller
[    1.207224] usb usb4: Manufacturer: Linux 3.16.0-30-generic xhci_hcd
[    1.207227] usb usb4: SerialNumber: 0000:00:10.0
[    1.207420] hub 4-0:1.0: USB hub found
[    1.207434] hub 4-0:1.0: 2 ports detected
[    1.207780] i8042: PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:_MSS] at 0x60,0x64 irq 1,12
[    1.220673] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.220682] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.220929] mousedev: PS/2 mouse device common for all mice
[    1.221306] rtc_cmos 00:01: RTC can wake from S4
[    1.221450] rtc_cmos 00:01: rtc core: registered rtc_cmos as rtc0
[    1.221474] rtc_cmos 00:01: alarms up to one month, 114 bytes nvram, hpet irqs
[    1.221601] device-mapper: uevent: version 1.0.3
[    1.221739] device-mapper: ioctl: 4.27.0-ioctl (2013-10-30) initialised: dm-devel@redhat.com
[    1.221766] ledtrig-cpu: registered to indicate activity on CPUs
[    1.221779] EFI Variables Facility v0.08 2004-May-17
[    1.231451] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    1.244902] TCP: cubic registered
[    1.245161] NET: Registered protocol family 10
[    1.245614] NET: Registered protocol family 17
[    1.245638] Key type dns_resolver registered
[    1.246246] Loading compiled-in X.509 certificates
[    1.248140] Loaded X.509 cert 'Magrathea: Glacier signing key: 7be2a7200f17f00ca011f70e5a874c37e3e0f6be'
[    1.248169] registered taskstats version 1
[    1.251772] Key type trusted registered
[    1.254809] Key type encrypted registered
[    1.257942] AppArmor: AppArmor sha1 policy hashing enabled
[    1.257951] ima: No TPM chip found, activating TPM-bypass!
[    1.257994] evm: HMAC attrs: 0x1
[    1.258724]   Magic number: 15:18:106
[    1.258909] rtc_cmos 00:01: setting system clock to 2015-05-10 02:08:42 UTC (1431223722)
[    1.259183] acpi-cpufreq: overriding BIOS provided _PSD data
[    1.259559] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.259562] EDD information not available.
[    1.259722] PM: Hibernation image not present or could not be loaded.
[    1.262240] Freeing unused kernel memory: 1356K (ffffffff82d1c000 - ffffffff82e6f000)
[    1.262246] Write protecting the kernel read-only data: 12288k
[    1.265668] Freeing unused kernel memory: 564K (ffff880002773000 - ffff880002800000)
[    1.268421] Freeing unused kernel memory: 500K (ffff880002b83000 - ffff880002c00000)
[    1.291396] systemd-udevd[116]: starting version 204
[    1.313984] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[    1.314011] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[    1.331230] acpi device:00: registered as cooling_device4
[    1.331351] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input5
[    1.343097] sdhci: Secure Digital Host Controller Interface driver
[    1.343102] sdhci: Copyright(c) Pierre Ossman
[    1.343602] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.344740] ahci 0000:00:11.0: version 3.0
[    1.344885] ahci 0000:00:11.0: irq 79 for MSI/MSI-X
[    1.344940] ahci 0000:00:11.0: AHCI 0001.0300 32 slots 2 ports 6 Gbps 0x3 impl SATA mode
[    1.344946] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp fbs pio slum part 
[    1.348060] [drm] Initialized drm 1.1.0 20060810
[    1.353421] r8169 0000:02:00.0: irq 80 for MSI/MSI-X
[    1.353727] r8169 0000:02:00.0 eth0: RTL8168g/8111g at 0xffffc90004f42000, 68:f7:28:6d:0d:18, XID 10900800 IRQ 80
[    1.353732] r8169 0000:02:00.0 eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
[    1.372480] AVX version of gcm_enc/dec engaged.
[    1.397294] [drm] radeon kernel modesetting enabled.
[    1.475239] scsi0 : ahci
[    1.475528] scsi1 : ahci
[    1.475656] ata1: SATA max UDMA/133 abar m1024@0xf0c6f000 port 0xf0c6f100 irq 79
[    1.475661] ata2: SATA max UDMA/133 abar m1024@0xf0c6f000 port 0xf0c6f180 irq 79
[    1.475712] sdhci-pci 0000:00:14.7: SDHCI controller found [1022:7813] (rev 1)
[    1.475908] mmc0: no vqmmc regulator found
[    1.475912] mmc0: no vmmc regulator found
[    1.476109] mmc0: SDHCI controller on PCI [0000:00:14.7] using ADMA
[    1.476600] [drm] initializing kernel modesetting (MULLINS 0x1002:0x9851 0x17AA:0x3801).
[    1.476616] [drm] register mmio base: 0xF0C00000
[    1.476619] [drm] register mmio size: 262144
[    1.476628] [drm] doorbell mmio base: 0xF0000000
[    1.476631] [drm] doorbell mmio size: 8388608
[    1.476639] [drm] ACPI VFCT contains a BIOS for 00:01.0 1002:9851, size 60416
[    1.476668] ATOM BIOS: AMD
[    1.476781] radeon 0000:00:01.0: VRAM: 1024M 0x0000000000000000 - 0x000000003FFFFFFF (1024M used)
[    1.476786] radeon 0000:00:01.0: GTT: 1024M 0x0000000040000000 - 0x000000007FFFFFFF
[    1.476789] [drm] Detected VRAM RAM=1024M, BAR=256M
[    1.476792] [drm] RAM width 128bits DDR
[    1.476921] [TTM] Zone  kernel: Available graphics memory: 2487084 kiB
[    1.476924] [TTM] Zone   dma32: Available graphics memory: 2097152 kiB
[    1.476927] [TTM] Initializing pool allocator
[    1.476937] [TTM] Initializing DMA pool allocator
[    1.476971] [drm] radeon: 1024M of VRAM memory ready
[    1.476974] [drm] radeon: 1024M of GTT memory ready.
[    1.476993] [drm] Loading MULLINS Microcode
[    1.477178] [drm] Internal thermal controller without fan control
[    1.478076] [drm] radeon: dpm initialized
[    1.480383] [drm] Found VCE firmware/feedback version 40.2.2 / 15!
[    1.480396] [drm] GART: num cpu pages 262144, num gpu pages 262144
[    1.491413] [drm] PCIE GART of 1024M enabled (table at 0x000000000078B000).
[    1.491602] radeon 0000:00:01.0: WB enabled
[    1.491626] radeon 0000:00:01.0: fence driver on ring 0 use gpu addr 0x0000000040000c00 and cpu addr 0xffff880035ad4c00
[    1.491630] radeon 0000:00:01.0: fence driver on ring 1 use gpu addr 0x0000000040000c04 and cpu addr 0xffff880035ad4c04
[    1.491633] radeon 0000:00:01.0: fence driver on ring 2 use gpu addr 0x0000000040000c08 and cpu addr 0xffff880035ad4c08
[    1.491636] radeon 0000:00:01.0: fence driver on ring 3 use gpu addr 0x0000000040000c0c and cpu addr 0xffff880035ad4c0c
[    1.491640] radeon 0000:00:01.0: fence driver on ring 4 use gpu addr 0x0000000040000c10 and cpu addr 0xffff880035ad4c10
[    1.492115] radeon 0000:00:01.0: fence driver on ring 5 use gpu addr 0x0000000000076c98 and cpu addr 0xffffc90004fb6c98
[    1.492184] radeon 0000:00:01.0: fence driver on ring 6 use gpu addr 0x0000000040000c18 and cpu addr 0xffff880035ad4c18
[    1.492187] radeon 0000:00:01.0: fence driver on ring 7 use gpu addr 0x0000000040000c1c and cpu addr 0xffff880035ad4c1c
[    1.492191] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[    1.492193] [drm] Driver supports precise vblank timestamp query.
[    1.492221] radeon 0000:00:01.0: irq 81 for MSI/MSI-X
[    1.492241] radeon 0000:00:01.0: radeon: using MSI.
[    1.492272] [drm] radeon: irq initialized.
[    1.496196] [drm] ring test on 0 succeeded in 2 usecs
[    1.496282] [drm] ring test on 1 succeeded in 2 usecs
[    1.496302] [drm] ring test on 2 succeeded in 2 usecs
[    1.496448] [drm] ring test on 3 succeeded in 4 usecs
[    1.496456] [drm] ring test on 4 succeeded in 4 usecs
[    1.502586] usb 1-1: new high-speed USB device number 2 using ehci-pci
[    1.532220] [drm] ring test on 5 succeeded in 1 usecs
[    1.532235] [drm] UVD initialized successfully.
[    1.634843] usb 1-1: New USB device found, idVendor=0438, idProduct=7900
[    1.634847] usb 1-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.635275] hub 1-1:1.0: USB hub found
[    1.635340] hub 1-1:1.0: 4 ports detected
[    1.641470] [drm] ring test on 6 succeeded in 12 usecs
[    1.641480] [drm] ring test on 7 succeeded in 2 usecs
[    1.641482] [drm] VCE initialized successfully.
[    1.642092] [drm] ib test on ring 0 succeeded in 0 usecs
[    1.642241] [drm] ib test on ring 1 succeeded in 0 usecs
[    1.642384] [drm] ib test on ring 2 succeeded in 0 usecs
[    1.642543] [drm] ib test on ring 3 succeeded in 0 usecs
[    1.642691] [drm] ib test on ring 4 succeeded in 0 usecs
[    1.643402] [drm] ib test on ring 5 succeeded
[    1.643968] [drm] ib test on ring 6 succeeded
[    1.644428] [drm] ib test on ring 7 succeeded
[    1.649828] [drm] radeon atom DIG backlight initialized
[    1.649832] [drm] Radeon Display Connectors
[    1.649835] [drm] Connector 0:
[    1.649836] [drm]   eDP-1
[    1.649838] [drm]   HPD1
[    1.649842] [drm]   DDC: 0x6530 0x6530 0x6534 0x6534 0x6538 0x6538 0x653c 0x653c
[    1.649844] [drm]   Encoders:
[    1.649845] [drm]     LCD1: INTERNAL_UNIPHY
[    1.649847] [drm] Connector 1:
[    1.649849] [drm]   HDMI-A-1
[    1.649850] [drm]   HPD2
[    1.649852] [drm]   DDC: 0x6540 0x6540 0x6544 0x6544 0x6548 0x6548 0x654c 0x654c
[    1.649854] [drm]   Encoders:
[    1.649855] [drm]     DFP1: INTERNAL_UNIPHY
[    1.649857] [drm] Connector 2:
[    1.649858] [drm]   VGA-1
[    1.649860] [drm]   DDC: 0x65c0 0x65c0 0x65c4 0x65c4 0x65c8 0x65c8 0x65cc 0x65cc
[    1.649862] [drm]   Encoders:
[    1.649863] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
[    1.746580] usb 2-1: new high-speed USB device number 2 using ehci-pci
[    1.878890] usb 2-1: New USB device found, idVendor=0438, idProduct=7900
[    1.878894] usb 2-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.879324] hub 2-1:1.0: USB hub found
[    1.879510] hub 2-1:1.0: 4 ports detected
[    1.966592] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.966619] ata1: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    1.966697] usb 1-1.3: new high-speed USB device number 3 using ehci-pci
[    1.966909] ata1.00: ATA-9: TOSHIBA THNSNJ240PCS3, J3ET6102, max UDMA/100
[    1.966913] ata1.00: 468862128 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.967230] ata1.00: configured for UDMA/100
[    1.967423] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA THNSNJ24 6102 PQ: 0 ANSI: 5
[    1.967462] psmouse serio1: elantech: assuming hardware version 4 (with firmware version 0x594f03)
[    1.967791] sd 0:0:0:0: [sda] 468862128 512-byte logical blocks: (240 GB/223 GiB)
[    1.967841] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.967961] sd 0:0:0:0: [sda] Write Protect is off
[    1.967966] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.968035] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.969528]  sda: sda1 sda2 sda3
[    1.970297] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.970399] ata2.00: ATAPI: MATSHITA DVD-RAM UJ8HC, G801, max UDMA/100
[    1.972853] ata2.00: configured for UDMA/100
[    1.977750] scsi 1:0:0:0: CD-ROM            MATSHITA DVD-RAM UJ8HC    G801 PQ: 0 ANSI: 5
[    1.982578] psmouse serio1: elantech: Synaptics capabilities query result 0x70, 0x15, 0x0a.
[    1.994123] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.994127] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.994457] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.994592] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.067336] input: ETPS/2 Elantech Touchpad as /devices/platform/i8042/serio1/input/input6
[    2.075570] usb 1-1.3: New USB device found, idVendor=0bda, idProduct=0129
[    2.075575] usb 1-1.3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    2.075578] usb 1-1.3: Product: USB2.0-CRW
[    2.075581] usb 1-1.3: Manufacturer: Generic
[    2.075584] usb 1-1.3: SerialNumber: 20100201396000000
[    2.082574] usbcore: registered new interface driver rtsx_usb
[    2.150597] tsc: Refined TSC clocksource calibration: 1996.255 MHz
[    2.150738] usb 2-1.2: new high-speed USB device number 3 using ehci-pci
[    2.278352] usb 2-1.2: New USB device found, idVendor=13d3, idProduct=5727
[    2.278356] usb 2-1.2: New USB device strings: Mfr=3, Product=1, SerialNumber=2
[    2.278359] usb 2-1.2: Product: Lenovo EasyCamera
[    2.278362] usb 2-1.2: Manufacturer: Azurewave
[    2.278365] usb 2-1.2: SerialNumber: NULL
[    2.354722] usb 2-1.3: new full-speed USB device number 4 using ehci-pci
[    2.424235] [drm] fb mappable at 0xE098F000
[    2.424241] [drm] vram apper at 0xE0000000
[    2.424243] [drm] size 4325376
[    2.424245] [drm] fb depth is 24
[    2.424247] [drm]    pitch is 5632
[    2.424418] fbcon: radeondrmfb (fb0) is primary device
[    2.463214] usb 2-1.3: No LPM exit latency info found, disabling LPM.
[    2.465336] usb 2-1.3: New USB device found, idVendor=0bda, idProduct=b728
[    2.465339] usb 2-1.3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    2.465341] usb 2-1.3: Product: Bluetooth Radio 
[    2.465343] usb 2-1.3: Manufacturer: Realtek 
[    2.465344] usb 2-1.3: SerialNumber: 00e04c000001
[    3.157219] Switched to clocksource tsc
[    3.909840] Console: switching to colour frame buffer device 170x48
[    3.915003] radeon 0000:00:01.0: fb0: radeondrmfb frame buffer device
[    3.915007] radeon 0000:00:01.0: registered panic notifier
[    3.931053] [drm] Initialized radeon 2.39.0 20080528 for 0000:00:01.0 on minor 0
[   13.769747] random: cryptsetup urandom read with 119 bits of entropy available
[   13.771351] random: nonblocking pool is initialized
[   14.096768] EXT4-fs (dm-1): INFO: recovery required on readonly filesystem
[   14.096774] EXT4-fs (dm-1): write access will be enabled during recovery
[   14.137660] EXT4-fs (dm-1): orphan cleanup on readonly fs
[   14.146443] EXT4-fs (dm-1): 64 orphan inodes deleted
[   14.146448] EXT4-fs (dm-1): recovery complete
[   14.150604] EXT4-fs (dm-1): mounted filesystem with ordered data mode. Opts: (null)
[   14.534349] Adding 5206012k swap on /dev/mapper/ubuntu--vg-swap_1.  Priority:-1 extents:1 across:5206012k SSFS
[   14.546791] EXT4-fs (dm-1): re-mounted. Opts: errors=remount-ro
[   14.893062] systemd-udevd[461]: starting version 204
[   14.987466] EXT4-fs (sda2): mounting ext2 file system using the ext4 subsystem
[   14.992979] EXT4-fs (sda2): mounted filesystem without journal. Opts: (null)
[   15.006493] lp: driver loaded but no devices found
[   15.033581] ppdev: user-space parallel port driver
[   15.121043] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   15.141338] input: Ideapad extra buttons as /devices/pci0000:00/0000:00:14.3/PNP0C09:00/VPC2004:00/input/input7
[   15.154110] cfg80211: Calling CRDA to update world regulatory domain
[   15.182718] AMD Cryptographic Coprocessor 0000:00:08.0: 4 command queues available
[   15.182759] AMD Cryptographic Coprocessor 0000:00:08.0: irq 82 for MSI/MSI-X
[   15.182767] AMD Cryptographic Coprocessor 0000:00:08.0: irq 83 for MSI/MSI-X
[   15.208007] Bluetooth: Core ver 2.19
[   15.208041] NET: Registered protocol family 31
[   15.208044] Bluetooth: HCI device and connection manager initialized
[   15.208054] Bluetooth: HCI socket layer initialized
[   15.208058] Bluetooth: L2CAP socket layer initialized
[   15.208073] Bluetooth: SCO socket layer initialized
[   15.216567] AMD Cryptographic Coprocessor 0000:00:08.0: enabled
[   15.216622] ACPI Warning: SystemIO range 0x0000000000000b00-0x0000000000000b07 conflicts with OpRegion 0x0000000000000b00-0x0000000000000b0f (\_SB_.PCI0.SMBS.SMB0) (20140424/utaddress-258)
[   15.216631] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   15.257158] MCE: In-kernel MCE decoding enabled.
[   15.273609] EDAC MC: Ver: 3.0.0
[   15.311587] AMD64 EDAC driver v3.4.0
[   15.311656] EDAC amd64: DRAM ECC disabled.
[   15.311668] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
[   15.311668]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
[   15.311668]  (Note that use of the override may cause unknown side effects.)
[   15.311774] usbcore: registered new interface driver btusb
[   15.322540] media: Linux media interface: v0.10
[   15.363011] Linux video capture interface: v2.00
[   15.392292] kvm: disabled by bios
[   15.448455] kvm: disabled by bios
[   15.467365] rtl8723be: Using firmware rtlwifi/rtl8723befw.bin
[   15.476820] uvcvideo: Found UVC 1.00 device Lenovo EasyCamera (13d3:5727)
[   15.500518] audit: type=1400 audit(1431223736.737:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=673 comm="apparmor_parser"
[   15.500530] audit: type=1400 audit(1431223736.737:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=673 comm="apparmor_parser"
[   15.500538] audit: type=1400 audit(1431223736.737:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=673 comm="apparmor_parser"
[   15.501200] audit: type=1400 audit(1431223736.737:5): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=673 comm="apparmor_parser"
[   15.501212] audit: type=1400 audit(1431223736.737:6): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=673 comm="apparmor_parser"
[   15.501286] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   15.501681] rtlwifi: wireless switch is on
[   15.502185] input: Lenovo EasyCamera as /devices/pci0000:00/0000:00:13.0/usb2/2-1/2-1.2/2-1.2:1.0/input/input8
[   15.502240] audit: type=1400 audit(1431223736.737:7): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=673 comm="apparmor_parser"
[   15.502311] usbcore: registered new interface driver uvcvideo
[   15.502314] USB Video Class driver (1.1.1)
[   15.514282] snd_hda_intel 0000:00:01.1: irq 84 for MSI/MSI-X
[   15.514560] snd_hda_intel 0000:00:14.2: irq 85 for MSI/MSI-X
[   15.533551] input: HD-Audio Generic HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.1/sound/card0/input9
[   15.539757] sound hdaudioC1D0: CX20751/2: BIOS auto-probing.
[   15.539981] sound hdaudioC1D0: autoconfig: line_outs=1 (0x17/0x0/0x0/0x0/0x0) type:speaker
[   15.539986] sound hdaudioC1D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   15.539990] sound hdaudioC1D0:    hp_outs=1 (0x16/0x0/0x0/0x0/0x0)
[   15.539993] sound hdaudioC1D0:    mono: mono_out=0x0
[   15.539995] sound hdaudioC1D0:    inputs:
[   15.540000] sound hdaudioC1D0:      Internal Mic=0x1a
[   15.540003] sound hdaudioC1D0:      Mic=0x19
[   15.543834] input: HD-Audio Generic Mic as /devices/pci0000:00/0000:00:14.2/sound/card1/input10
[   15.543972] input: HD-Audio Generic Headphone as /devices/pci0000:00/0000:00:14.2/sound/card1/input11
[   15.553083] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   15.553089] Bluetooth: BNEP filters: protocol multicast
[   15.553103] Bluetooth: BNEP socket layer initialized
[   15.567577] Bluetooth: RFCOMM TTY layer initialized
[   15.567622] Bluetooth: RFCOMM socket layer initialized
[   15.567633] Bluetooth: RFCOMM ver 1.11
[   15.652003] cfg80211: World regulatory domain updated:
[   15.652012] cfg80211:  DFS Master region: unset
[   15.652015] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
[   15.652019] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[   15.652022] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[   15.652025] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm), (N/A)
[   15.652029] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[   15.652031] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[   15.652702] audit: type=1400 audit(1431223736.889:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=763 comm="apparmor_parser"
[   15.652716] audit: type=1400 audit(1431223736.889:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cupsd" pid=763 comm="apparmor_parser"
[   15.653527] audit: type=1400 audit(1431223736.889:10): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=763 comm="apparmor_parser"
[   15.954754] init: failsafe main process (874) killed by TERM signal
[   16.668664] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   16.688640] audit: type=1400 audit(1431223737.925:11): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/lightdm/lightdm-guest-session" pid=1127 comm="apparmor_parser"
[   16.689126] r8169 0000:02:00.0 eth0: link down
[   16.689482] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   17.598318] wlan0: authenticate with e0:88:5d:36:e1:47
[   17.608527] wlan0: send auth to e0:88:5d:36:e1:47 (try 1/3)
[   17.611092] wlan0: authenticated
[   17.611789] wlan0: associate with e0:88:5d:36:e1:47 (try 1/3)
[   17.620967] wlan0: RX AssocResp from e0:88:5d:36:e1:47 (capab=0x411 status=0 aid=4)
[   17.621104] wlan0: associated
[   17.621121] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   18.142365] init: plymouth-upstart-bridge main process ended, respawning
[   18.151667] init: plymouth-upstart-bridge main process (1406) terminated with status 1
[   18.151691] init: plymouth-upstart-bridge main process ended, respawning
[   20.807309] audit_printk_skb: 168 callbacks suppressed
[   20.807317] audit: type=1400 audit(1431223742.041:68): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=2196 comm="nm-dhcp-client." lport=64629 family="inet" sock_type="dgram" protocol=17
[   20.807334] audit: type=1400 audit(1431223742.041:69): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=2196 comm="nm-dhcp-client." lport=36247 family="inet6" sock_type="dgram" protocol=17
[   20.811772] audit: type=1400 audit(1431223742.045:70): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=2197 comm="nm-dhcp-client." lport=64629 family="inet" sock_type="dgram" protocol=17
[   20.811793] audit: type=1400 audit(1431223742.045:71): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=2197 comm="nm-dhcp-client." lport=36247 family="inet6" sock_type="dgram" protocol=17
[   20.824564] audit: type=1400 audit(1431223742.061:72): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=2198 comm="nm-dhcp-client." lport=64629 family="inet" sock_type="dgram" protocol=17
[   20.824583] audit: type=1400 audit(1431223742.061:73): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=2198 comm="nm-dhcp-client." lport=36247 family="inet6" sock_type="dgram" protocol=17
[   22.088950] audit: type=1400 audit(1431223743.325:74): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=2230 comm="nm-dhcp-client." lport=64629 family="inet" sock_type="dgram" protocol=17
[   22.088969] audit: type=1400 audit(1431223743.325:75): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=2230 comm="nm-dhcp-client." lport=36247 family="inet6" sock_type="dgram" protocol=17
[   37.117029] audit: type=1400 audit(1431223758.344:76): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=2407 comm="nm-dhcp-client." lport=64629 family="inet" sock_type="dgram" protocol=17
[   37.117048] audit: type=1400 audit(1431223758.344:77): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=2407 comm="nm-dhcp-client." lport=36247 family="inet6" sock_type="dgram" protocol=17
[   52.137878] audit: type=1400 audit(1431223773.356:78): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=2480 comm="nm-dhcp-client." lport=64629 family="inet" sock_type="dgram" protocol=17
[   52.137896] audit: type=1400 audit(1431223773.356:79): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=2480 comm="nm-dhcp-client." lport=36247 family="inet6" sock_type="dgram" protocol=17
[   67.157086] audit: type=1400 audit(1431223788.369:80): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=2534 comm="nm-dhcp-client." lport=64629 family="inet" sock_type="dgram" protocol=17
[   67.157105] audit: type=1400 audit(1431223788.369:81): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=2534 comm="nm-dhcp-client." lport=36247 family="inet6" sock_type="dgram" protocol=17
[   82.179689] audit: type=1400 audit(1431223803.381:82): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=2635 comm="nm-dhcp-client." lport=64629 family="inet" sock_type="dgram" protocol=17
[   82.179709] audit: type=1400 audit(1431223803.381:83): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=2635 comm="nm-dhcp-client." lport=36247 family="inet6" sock_type="dgram" protocol=17
[   97.197932] audit: type=1400 audit(1431223818.394:84): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=2659 comm="nm-dhcp-client." lport=64629 family="inet" sock_type="dgram" protocol=17
[   97.197963] audit: type=1400 audit(1431223818.394:85): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=2659 comm="nm-dhcp-client." lport=36247 family="inet6" sock_type="dgram" protocol=17
[  112.220649] audit: type=1400 audit(1431223833.406:86): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=3090 comm="nm-dhcp-client." lport=64629 family="inet" sock_type="dgram" protocol=17
[  112.220680] audit: type=1400 audit(1431223833.406:87): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=3090 comm="nm-dhcp-client." lport=36247 family="inet6" sock_type="dgram" protocol=17
[  127.251331] audit: type=1400 audit(1431223848.431:88): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=3103 comm="nm-dhcp-client." lport=64629 family="inet" sock_type="dgram" protocol=17
[  127.251363] audit: type=1400 audit(1431223848.431:89): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=3103 comm="nm-dhcp-client." lport=36247 family="inet6" sock_type="dgram" protocol=17
[  142.274558] audit: type=1400 audit(1431223863.439:90): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=3178 comm="nm-dhcp-client." lport=64629 family="inet" sock_type="dgram" protocol=17
[  142.274591] audit: type=1400 audit(1431223863.439:91): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=3178 comm="nm-dhcp-client." lport=36247 family="inet6" sock_type="dgram" protocol=17
[  157.307665] audit: type=1400 audit(1431223878.464:92): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=3183 comm="nm-dhcp-client." lport=64629 family="inet" sock_type="dgram" protocol=17
[  157.307697] audit: type=1400 audit(1431223878.464:93): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=3183 comm="nm-dhcp-client." lport=36247 family="inet6" sock_type="dgram" protocol=17
[  172.330556] audit: type=1400 audit(1431223893.480:94): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=3189 comm="nm-dhcp-client." lport=64629 family="inet" sock_type="dgram" protocol=17
[  172.330588] audit: type=1400 audit(1431223893.480:95): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=3189 comm="nm-dhcp-client." lport=36247 family="inet6" sock_type="dgram" protocol=17
[  187.355864] audit: type=1400 audit(1431223908.497:96): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=3194 comm="nm-dhcp-client." lport=64629 family="inet" sock_type="dgram" protocol=17
[  187.355895] audit: type=1400 audit(1431223908.497:97): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=3194 comm="nm-dhcp-client." lport=36247 family="inet6" sock_type="dgram" protocol=17
[  202.378243] audit: type=1400 audit(1431223923.513:98): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=3199 comm="nm-dhcp-client." lport=64629 family="inet" sock_type="dgram" protocol=17
[  202.378274] audit: type=1400 audit(1431223923.513:99): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=3199 comm="nm-dhcp-client." lport=36247 family="inet6" sock_type="dgram" protocol=17
[  217.402507] audit: type=1400 audit(1431223938.530:100): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=3204 comm="nm-dhcp-client." lport=64629 family="inet" sock_type="dgram" protocol=17
[  217.402539] audit: type=1400 audit(1431223938.530:101): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=3204 comm="nm-dhcp-client." lport=36247 family="inet6" sock_type="dgram" protocol=17
[  232.546505] audit: type=1400 audit(1431223953.662:102): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=3211 comm="nm-dhcp-client." lport=64629 family="inet" sock_type="dgram" protocol=17
[  232.546537] audit: type=1400 audit(1431223953.662:103): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=3211 comm="nm-dhcp-client." lport=36247 family="inet6" sock_type="dgram" protocol=17
[  247.571435] audit: type=1400 audit(1431223968.679:104): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=3216 comm="nm-dhcp-client." lport=64629 family="inet" sock_type="dgram" protocol=17
[  247.571466] audit: type=1400 audit(1431223968.679:105): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=3216 comm="nm-dhcp-client." lport=36247 family="inet6" sock_type="dgram" protocol=17
[  262.593263] audit: type=1400 audit(1431223983.695:106): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=3229 comm="nm-dhcp-client." lport=64629 family="inet" sock_type="dgram" protocol=17
[  262.593283] audit: type=1400 audit(1431223983.695:107): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=3229 comm="nm-dhcp-client." lport=36247 family="inet6" sock_type="dgram" protocol=17
[  277.619347] audit: type=1400 audit(1431223998.708:108): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=3254 comm="nm-dhcp-client." lport=64629 family="inet" sock_type="dgram" protocol=17
[  277.619378] audit: type=1400 audit(1431223998.708:109): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=3254 comm="nm-dhcp-client." lport=36247 family="inet6" sock_type="dgram" protocol=17
[  292.642498] audit: type=1400 audit(1431224013.724:110): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=3261 comm="nm-dhcp-client." lport=64629 family="inet" sock_type="dgram" protocol=17
[  292.642529] audit: type=1400 audit(1431224013.724:111): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=3261 comm="nm-dhcp-client." lport=36247 family="inet6" sock_type="dgram" protocol=17
[  307.666001] audit: type=1400 audit(1431224028.737:112): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=3266 comm="nm-dhcp-client." lport=64629 family="inet" sock_type="dgram" protocol=17
[  307.666032] audit: type=1400 audit(1431224028.737:113): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=3266 comm="nm-dhcp-client." lport=36247 family="inet6" sock_type="dgram" protocol=17
[  322.697627] audit: type=1400 audit(1431224043.761:114): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=3272 comm="nm-dhcp-client." lport=64629 family="inet" sock_type="dgram" protocol=17
[  322.697659] audit: type=1400 audit(1431224043.761:115): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=3272 comm="nm-dhcp-client." lport=36247 family="inet6" sock_type="dgram" protocol=17
[  337.720632] audit: type=1400 audit(1431224058.778:116): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=3277 comm="nm-dhcp-client." lport=64629 family="inet" sock_type="dgram" protocol=17
[  337.720663] audit: type=1400 audit(1431224058.778:117): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=3277 comm="nm-dhcp-client." lport=36247 family="inet6" sock_type="dgram" protocol=17
[  352.745191] audit: type=1400 audit(1431224073.794:118): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=3282 comm="nm-dhcp-client." lport=64629 family="inet" sock_type="dgram" protocol=17
[  352.745223] audit: type=1400 audit(1431224073.794:119): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=3282 comm="nm-dhcp-client." lport=36247 family="inet6" sock_type="dgram" protocol=17
[  367.770904] audit: type=1400 audit(1431224088.810:120): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=3287 comm="nm-dhcp-client." lport=64629 family="inet" sock_type="dgram" protocol=17
[  367.770936] audit: type=1400 audit(1431224088.810:121): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=3287 comm="nm-dhcp-client." lport=36247 family="inet6" sock_type="dgram" protocol=17
[  382.795983] audit: type=1400 audit(1431224103.827:122): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=3293 comm="nm-dhcp-client." lport=64629 family="inet" sock_type="dgram" protocol=17
[  382.796015] audit: type=1400 audit(1431224103.827:123): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=3293 comm="nm-dhcp-client." lport=36247 family="inet6" sock_type="dgram" protocol=17
[  397.820327] audit: type=1400 audit(1431224118.839:124): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=3299 comm="nm-dhcp-client." lport=64629 family="inet" sock_type="dgram" protocol=17
[  397.820359] audit: type=1400 audit(1431224118.839:125): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=3299 comm="nm-dhcp-client." lport=36247 family="inet6" sock_type="dgram" protocol=17
[  412.844819] audit: type=1400 audit(1431224133.856:126): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=3306 comm="nm-dhcp-client." lport=64629 family="inet" sock_type="dgram" protocol=17
[  412.844850] audit: type=1400 audit(1431224133.856:127): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=3306 comm="nm-dhcp-client." lport=36247 family="inet6" sock_type="dgram" protocol=17
[  427.869848] audit: type=1400 audit(1431224148.872:128): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=3358 comm="nm-dhcp-client." lport=64629 family="inet" sock_type="dgram" protocol=17
[  427.869882] audit: type=1400 audit(1431224148.872:129): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=3358 comm="nm-dhcp-client." lport=36247 family="inet6" sock_type="dgram" protocol=17
[  442.894156] audit: type=1400 audit(1431224163.889:130): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=3363 comm="nm-dhcp-client." lport=64629 family="inet" sock_type="dgram" protocol=17
[  442.894188] audit: type=1400 audit(1431224163.889:131): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=3363 comm="nm-dhcp-client." lport=36247 family="inet6" sock_type="dgram" protocol=17
[  453.504302] systemd-hostnamed[3370]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
[  457.917939] audit: type=1400 audit(1431224178.905:132): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=3384 comm="nm-dhcp-client." lport=64629 family="inet" sock_type="dgram" protocol=17
[  457.917958] audit: type=1400 audit(1431224178.905:133): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=3384 comm="nm-dhcp-client." lport=36247 family="inet6" sock_type="dgram" protocol=17
[  472.949625] audit: type=1400 audit(1431224193.926:134): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=3394 comm="nm-dhcp-client." lport=64629 family="inet" sock_type="dgram" protocol=17
[  472.949659] audit: type=1400 audit(1431224193.926:135): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=3394 comm="nm-dhcp-client." lport=36247 family="inet6" sock_type="dgram" protocol=17
[  485.695122] uvcvideo: Failed to query (GET_DEF) UVC control 8 on unit 1: -32 (exp. 1).
[  487.975069] audit: type=1400 audit(1431224208.946:136): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=3424 comm="nm-dhcp-client." lport=64629 family="inet" sock_type="dgram" protocol=17
[  487.975101] audit: type=1400 audit(1431224208.946:137): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=3424 comm="nm-dhcp-client." lport=36247 family="inet6" sock_type="dgram" protocol=17
[  502.997289] audit: type=1400 audit(1431224223.959:138): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=3447 comm="nm-dhcp-client." lport=64629 family="inet" sock_type="dgram" protocol=17
[  502.997321] audit: type=1400 audit(1431224223.959:139): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=3447 comm="nm-dhcp-client." lport=36247 family="inet6" sock_type="dgram" protocol=17
[  518.021861] audit: type=1400 audit(1431224238.971:140): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=3452 comm="nm-dhcp-client." lport=64629 family="inet" sock_type="dgram" protocol=17
[  518.021893] audit: type=1400 audit(1431224238.971:141): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=3452 comm="nm-dhcp-client." lport=36247 family="inet6" sock_type="dgram" protocol=17
[  533.049802] audit: type=1400 audit(1431224253.992:142): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=3457 comm="nm-dhcp-client." lport=64629 family="inet" sock_type="dgram" protocol=17
[  533.049833] audit: type=1400 audit(1431224253.992:143): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=3457 comm="nm-dhcp-client." lport=36247 family="inet6" sock_type="dgram" protocol=17
[  547.073738] audit: type=1400 audit(1431224268.009:144): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=3503 comm="nm-dhcp-client." lport=64629 family="inet" sock_type="dgram" protocol=17
[  547.073755] audit: type=1400 audit(1431224268.009:145): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=3503 comm="nm-dhcp-client." lport=36247 family="inet6" sock_type="dgram" protocol=17
[  562.099044] audit: type=1400 audit(1431224283.025:146): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=3515 comm="nm-dhcp-client." lport=64629 family="inet" sock_type="dgram" protocol=17
[  562.099076] audit: type=1400 audit(1431224283.025:147): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=3515 comm="nm-dhcp-client." lport=36247 family="inet6" sock_type="dgram" protocol=17
[  577.125132] audit: type=1400 audit(1431224298.042:148): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=3522 comm="nm-dhcp-client." lport=64629 family="inet" sock_type="dgram" protocol=17
[  577.125153] audit: type=1400 audit(1431224298.042:149): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=3522 comm="nm-dhcp-client." lport=36247 family="inet6" sock_type="dgram" protocol=17
[  592.369657] audit: type=1400 audit(1431224313.278:150): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=3566 comm="nm-dhcp-client." lport=64629 family="inet" sock_type="dgram" protocol=17
[  592.369677] audit: type=1400 audit(1431224313.278:151): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=3566 comm="nm-dhcp-client." lport=36247 family="inet6" sock_type="dgram" protocol=17
[  607.394885] audit: type=1400 audit(1431224328.295:152): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=3675 comm="nm-dhcp-client." lport=64629 family="inet" sock_type="dgram" protocol=17
[  607.394905] audit: type=1400 audit(1431224328.295:153): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=3675 comm="nm-dhcp-client." lport=36247 family="inet6" sock_type="dgram" protocol=17
[  622.418001] audit: type=1400 audit(1431224343.307:154): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=3752 comm="nm-dhcp-client." lport=64629 family="inet" sock_type="dgram" protocol=17
[  622.418022] audit: type=1400 audit(1431224343.307:155): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=3752 comm="nm-dhcp-client." lport=36247 family="inet6" sock_type="dgram" protocol=17
[  637.450811] audit: type=1400 audit(1431224358.332:156): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=3820 comm="nm-dhcp-client." lport=64629 family="inet" sock_type="dgram" protocol=17
[  637.450843] audit: type=1400 audit(1431224358.332:157): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=3820 comm="nm-dhcp-client." lport=36247 family="inet6" sock_type="dgram" protocol=17
[  652.477669] audit: type=1400 audit(1431224373.352:158): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=3827 comm="nm-dhcp-client." lport=64629 family="inet" sock_type="dgram" protocol=17
[  652.477700] audit: type=1400 audit(1431224373.352:159): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=3827 comm="nm-dhcp-client." lport=36247 family="inet6" sock_type="dgram" protocol=17
[  667.508042] audit: type=1400 audit(1431224388.373:160): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=3843 comm="nm-dhcp-client." lport=64629 family="inet" sock_type="dgram" protocol=17
[  667.508065] audit: type=1400 audit(1431224388.373:161): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=3843 comm="nm-dhcp-client." lport=36247 family="inet6" sock_type="dgram" protocol=17
[  682.527636] audit: type=1400 audit(1431224403.385:162): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=4438 comm="nm-dhcp-client." lport=64629 family="inet" sock_type="dgram" protocol=17
[  682.527659] audit: type=1400 audit(1431224403.385:163): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=4438 comm="nm-dhcp-client." lport=36247 family="inet6" sock_type="dgram" protocol=17
[  697.552004] audit: type=1400 audit(1431224418.402:164): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=5268 comm="nm-dhcp-client." lport=64629 family="inet" sock_type="dgram" protocol=17
[  697.552023] audit: type=1400 audit(1431224418.402:165): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=5268 comm="nm-dhcp-client." lport=36247 family="inet6" sock_type="dgram" protocol=17
[  712.577074] audit: type=1400 audit(1431224433.418:166): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=5278 comm="nm-dhcp-client." lport=64629 family="inet" sock_type="dgram" protocol=17
[  712.577093] audit: type=1400 audit(1431224433.418:167): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=5278 comm="nm-dhcp-client." lport=36247 family="inet6" sock_type="dgram" protocol=17
[  727.600982] audit: type=1400 audit(1431224448.435:168): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=5283 comm="nm-dhcp-client." lport=64629 family="inet" sock_type="dgram" protocol=17
[  727.601014] audit: type=1400 audit(1431224448.435:169): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=5283 comm="nm-dhcp-client." lport=36247 family="inet6" sock_type="dgram" protocol=17
[  742.627197] audit: type=1400 audit(1431224463.451:170): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=5670 comm="nm-dhcp-client." lport=64629 family="inet" sock_type="dgram" protocol=17
[  742.627229] audit: type=1400 audit(1431224463.451:171): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=5670 comm="nm-dhcp-client." lport=36247 family="inet6" sock_type="dgram" protocol=17
[  757.774913] audit: type=1400 audit(1431224478.599:172): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=6068 comm="nm-dhcp-client." lport=64629 family="inet" sock_type="dgram" protocol=17
[  757.774946] audit: type=1400 audit(1431224478.599:173): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=6068 comm="nm-dhcp-client." lport=36247 family="inet6" sock_type="dgram" protocol=17
[  772.793421] audit: type=1400 audit(1431224493.615:174): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=6461 comm="nm-dhcp-client." lport=64629 family="inet" sock_type="dgram" protocol=17
[  772.793440] audit: type=1400 audit(1431224493.615:175): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=6461 comm="nm-dhcp-client." lport=36247 family="inet6" sock_type="dgram" protocol=17
[  787.809817] audit: type=1400 audit(1431224508.631:176): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=6850 comm="nm-dhcp-client." lport=64629 family="inet" sock_type="dgram" protocol=17
[  787.809837] audit: type=1400 audit(1431224508.631:177): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=6850 comm="nm-dhcp-client." lport=36247 family="inet6" sock_type="dgram" protocol=17
[  802.826551] audit: type=1400 audit(1431224523.647:178): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=7246 comm="nm-dhcp-client." lport=64629 family="inet" sock_type="dgram" protocol=17
[  802.826570] audit: type=1400 audit(1431224523.647:179): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=7246 comm="nm-dhcp-client." lport=36247 family="inet6" sock_type="dgram" protocol=17
[  817.844680] audit: type=1400 audit(1431224538.663:180): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=7264 comm="nm-dhcp-client." lport=64629 family="inet" sock_type="dgram" protocol=17
[  817.844712] audit: type=1400 audit(1431224538.663:181): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=7264 comm="nm-dhcp-client." lport=36247 family="inet6" sock_type="dgram" protocol=17
[  832.867879] audit: type=1400 audit(1431224553.683:182): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=7269 comm="nm-dhcp-client." lport=64629 family="inet" sock_type="dgram" protocol=17
[  832.867912] audit: type=1400 audit(1431224553.683:183): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=7269 comm="nm-dhcp-client." lport=36247 family="inet6" sock_type="dgram" protocol=17
[  847.889163] audit: type=1400 audit(1431224568.703:184): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=7274 comm="nm-dhcp-client." lport=64629 family="inet" sock_type="dgram" protocol=17
[  847.889196] audit: type=1400 audit(1431224568.703:185): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=7274 comm="nm-dhcp-client." lport=36247 family="inet6" sock_type="dgram" protocol=17
[  862.908437] audit: type=1400 audit(1431224583.723:186): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=7280 comm="nm-dhcp-client." lport=64629 family="inet" sock_type="dgram" protocol=17
[  862.908469] audit: type=1400 audit(1431224583.723:187): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=7280 comm="nm-dhcp-client." lport=36247 family="inet6" sock_type="dgram" protocol=17
[  877.926324] audit: type=1400 audit(1431224598.739:188): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=7691 comm="nm-dhcp-client." lport=64629 family="inet" sock_type="dgram" protocol=17
[  877.926349] audit: type=1400 audit(1431224598.739:189): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=7691 comm="nm-dhcp-client." lport=36247 family="inet6" sock_type="dgram" protocol=17
[  892.943147] audit: type=1400 audit(1431224613.755:190): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=8080 comm="nm-dhcp-client." lport=64629 family="inet" sock_type="dgram" protocol=17
[  892.943166] audit: type=1400 audit(1431224613.755:191): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=8080 comm="nm-dhcp-client." lport=36247 family="inet6" sock_type="dgram" protocol=17
[  907.960704] audit: type=1400 audit(1431224628.771:192): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=8087 comm="nm-dhcp-client." lport=64629 family="inet" sock_type="dgram" protocol=17
[  907.960737] audit: type=1400 audit(1431224628.771:193): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=8087 comm="nm-dhcp-client." lport=36247 family="inet6" sock_type="dgram" protocol=17
[  922.977369] audit: type=1400 audit(1431224643.787:194): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=8220 comm="nm-dhcp-client." lport=64629 family="inet" sock_type="dgram" protocol=17
[  922.977387] audit: type=1400 audit(1431224643.787:195): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=8220 comm="nm-dhcp-client." lport=36247 family="inet6" sock_type="dgram" protocol=17
[  937.996190] audit: type=1400 audit(1431224658.803:196): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=9063 comm="nm-dhcp-client." lport=64629 family="inet" sock_type="dgram" protocol=17
[  937.996224] audit: type=1400 audit(1431224658.803:197): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=9063 comm="nm-dhcp-client." lport=36247 family="inet6" sock_type="dgram" protocol=17
[  953.022023] audit: type=1400 audit(1431224673.831:198): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=9070 comm="nm-dhcp-client." lport=64629 family="inet" sock_type="dgram" protocol=17
[  953.022055] audit: type=1400 audit(1431224673.831:199): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=9070 comm="nm-dhcp-client." lport=36247 family="inet6" sock_type="dgram" protocol=17
[  968.045874] audit: type=1400 audit(1431224688.851:200): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=9140 comm="nm-dhcp-client." lport=64629 family="inet" sock_type="dgram" protocol=17
[  968.045893] audit: type=1400 audit(1431224688.851:201): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=9140 comm="nm-dhcp-client." lport=36247 family="inet6" sock_type="dgram" protocol=17
[  983.059239] audit: type=1400 audit(1431224703.863:202): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=9155 comm="nm-dhcp-client." lport=64629 family="inet" sock_type="dgram" protocol=17
[  983.059259] audit: type=1400 audit(1431224703.863:203): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=9155 comm="nm-dhcp-client." lport=36247 family="inet6" sock_type="dgram" protocol=17
[  998.079167] audit: type=1400 audit(1431224718.883:204): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=9171 comm="nm-dhcp-client." lport=64629 family="inet" sock_type="dgram" protocol=17
[  998.079200] audit: type=1400 audit(1431224718.883:205): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=9171 comm="nm-dhcp-client." lport=36247 family="inet6" sock_type="dgram" protocol=17
[ 1013.301629] audit: type=1400 audit(1431224734.103:206): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=9198 comm="nm-dhcp-client." lport=64629 family="inet" sock_type="dgram" protocol=17
[ 1013.301655] audit: type=1400 audit(1431224734.103:207): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=9198 comm="nm-dhcp-client." lport=36247 family="inet6" sock_type="dgram" protocol=17
[ 1043.314447] audit: type=1400 audit(1431224764.115:208): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=9397 comm="nm-dhcp-client." lport=64629 family="inet" sock_type="dgram" protocol=17
[ 1043.314480] audit: type=1400 audit(1431224764.115:209): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=9397 comm="nm-dhcp-client." lport=36247 family="inet6" sock_type="dgram" protocol=17
[ 1073.328179] audit: type=1400 audit(1431224794.127:210): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=9432 comm="nm-dhcp-client." lport=64629 family="inet" sock_type="dgram" protocol=17
[ 1073.328212] audit: type=1400 audit(1431224794.127:211): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=9432 comm="nm-dhcp-client." lport=36247 family="inet6" sock_type="dgram" protocol=17
```

---

