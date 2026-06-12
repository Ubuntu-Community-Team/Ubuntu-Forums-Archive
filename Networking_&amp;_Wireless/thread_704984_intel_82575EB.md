---
title: "intel 82575EB"
date: 2008-02-22
forum: Networking &amp; Wireless
---

### Post by mthaddon on 2008-02-22
Hi Folks,

I have a new Thinkmate machine that includes an intel 82575EB integrated gigabit network controller, and for some reason it's not recognised by the Ubuntu Live CD (7.10 amd64). Does anyone have any recommendations for what I can try?

Here's the output of dmesg:

```
[    0.000000] Linux version 2.6.22-14-generic (buildd@crested) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Sun Oct 14 21:45:15 GMT 2007 (Ubuntu 2.6.22-14.46-generic)
[    0.000000] Command line: BOOT_IMAGE=/casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash --
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 0000000000096000 (usable)
[    0.000000]  BIOS-e820: 0000000000096000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d2000 - 00000000000d4000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000bff00000 (usable)
[    0.000000]  BIOS-e820: 00000000bff00000 - 00000000bff0b000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000bff0b000 - 00000000bff0c000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bff0c000 - 00000000c0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000440000000 (usable)
[    0.000000] Entering add_active_range(0, 0, 150) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 786176) 1 entries of 3200 used
[    0.000000] Entering add_active_range(0, 1048576, 4456448) 2 entries of 3200 used
[    0.000000] end_pfn_map = 4456448
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP signature @ 0xFFFF8100000F6550 checksum 0
[    0.000000] ACPI: RSDP 000F6550, 0024 (r2 PTLTD )
[    0.000000] ACPI: XSDT BFF048C5, 00A4 (r1 PTLTD  	 XSDT    6040000  LTP        0)
[    0.000000] ACPI: FACP BFF0AD22, 00F4 (r3 INTEL  STOAKLEY  6040000 PTL         3)
[    0.000000] ACPI: DSDT BFF0643B, 4873 (r1  Intel SEABURG   6040000 MSFT  100000E)
[    0.000000] ACPI: FACS BFF0BFC0, 0040
[    0.000000] ACPI: _MAR BFF0AE16, 0030 (r1 Intel  OEMDMAR   6040000 LOHR        1)
[    0.000000] ACPI: TCPA BFF0AE46, 0032 (r1 Intel  STOAKLEY  6040000 LOHR       5A)
[    0.000000] ACPI: APIC BFF0AE78, 00D4 (r1 PTLTD  	 APIC    6040000  LTP        0)
[    0.000000] ACPI: MCFG BFF0AF4C, 003C (r1 PTLTD    MCFG    6040000  LTP        0)
[    0.000000] ACPI: BOOT BFF0AF88, 0028 (r1 PTLTD  $SBFTBL$  6040000  LTP        1)
[    0.000000] ACPI: SPCR BFF0AFB0, 0050 (r1 PTLTD  $UCRTBL$  6040000 PTL         1)
[    0.000000] ACPI: SSDT BFF061DC, 025F (r1  PmRef  Cpu0Tst     3000 INTL 20050228)
[    0.000000] ACPI: SSDT BFF06136, 00A6 (r1  PmRef  Cpu7Tst     3000 INTL 20050228)
[    0.000000] ACPI: SSDT BFF06090, 00A6 (r1  PmRef  Cpu6Tst     3000 INTL 20050228)
[    0.000000] ACPI: SSDT BFF05FEA, 00A6 (r1  PmRef  Cpu5Tst     3000 INTL 20050228)
[    0.000000] ACPI: SSDT BFF05F44, 00A6 (r1  PmRef  Cpu4Tst     3000 INTL 20050228)
[    0.000000] ACPI: SSDT BFF05E9E, 00A6 (r1  PmRef  Cpu3Tst     3000 INTL 20050228)
[    0.000000] ACPI: SSDT BFF05DF8, 00A6 (r1  PmRef  Cpu2Tst     3000 INTL 20050228)
[    0.000000] ACPI: SSDT BFF05D52, 00A6 (r1  PmRef  Cpu1Tst     3000 INTL 20050228)
[    0.000000] ACPI: SSDT BFF04969, 13E9 (r1  PmRef    CpuPm     3000 INTL 20050228)
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-0000000440000000
[    0.000000] Entering add_active_range(0, 0, 150) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 786176) 1 entries of 3200 used
[    0.000000] Entering add_active_range(0, 1048576, 4456448) 2 entries of 3200 used
[    0.000000] Bootmem setup node 0 0000000000000000-0000000440000000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   DMA32        4096 ->  1048576
[    0.000000]   Normal    1048576 ->  4456448
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0:        0 ->      150
[    0.000000]     0:      256 ->   786176
[    0.000000]     0:  1048576 ->  4456448
[    0.000000] On node 0 totalpages: 4193942
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 1147 pages reserved
[    0.000000]   DMA zone: 2787 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14280 pages used for memmap
[    0.000000]   DMA32 zone: 767800 pages, LIFO batch:31
[    0.000000]   Normal zone: 46592 pages used for memmap
[    0.000000]   Normal zone: 3361280 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 (Bootup-CPU)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x04] enabled)
[    0.000000] Processor #4
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] Processor #1
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x05] enabled)
[    0.000000] Processor #5
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x02] enabled)
[    0.000000] Processor #2
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x06] enabled)
[    0.000000] Processor #6
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x03] enabled)
[    0.000000] Processor #3
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x07] enabled)
[    0.000000] Processor #7
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x04] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x05] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x06] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x07] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x08] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 8, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: IOAPIC (id[0x09] address[0xfec88000] gsi_base[24])
[    0.000000] IOAPIC[1]: apic_id 9, address 0xfec88000, GSI 24-47
[    0.000000] ACPI: IOAPIC (id[0x0a] address[0xfec89000] gsi_base[48])
[    0.000000] IOAPIC[2]: apic_id 10, address 0xfec89000, GSI 48-71
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Setting APIC routing to flat
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] swsusp: Registered nosave memory region: 0000000000096000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000d2000
[    0.000000] swsusp: Registered nosave memory region: 00000000000d2000 - 00000000000d4000
[    0.000000] swsusp: Registered nosave memory region: 00000000000d4000 - 00000000000e0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000e0000 - 0000000000100000
[    0.000000] swsusp: Registered nosave memory region: 00000000bff00000 - 00000000bff0b000
[    0.000000] swsusp: Registered nosave memory region: 00000000bff0b000 - 00000000bff0c000
[    0.000000] swsusp: Registered nosave memory region: 00000000bff0c000 - 00000000c0000000
[    0.000000] swsusp: Registered nosave memory region: 00000000c0000000 - 00000000e0000000
[    0.000000] swsusp: Registered nosave memory region: 00000000e0000000 - 00000000f0000000
[    0.000000] swsusp: Registered nosave memory region: 00000000f0000000 - 00000000fec00000
[    0.000000] swsusp: Registered nosave memory region: 00000000fec00000 - 00000000fec10000
[    0.000000] swsusp: Registered nosave memory region: 00000000fec10000 - 00000000fee00000
[    0.000000] swsusp: Registered nosave memory region: 00000000fee00000 - 00000000fee01000
[    0.000000] swsusp: Registered nosave memory region: 00000000fee01000 - 00000000ff000000
[    0.000000] swsusp: Registered nosave memory region: 00000000ff000000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at c2000000 (gap: c0000000:20000000)
[    0.000000] SMP: Allowing 8 CPUs, 0 hotplug CPUs
[    0.000000] PERCPU: Allocating 34696 bytes of per cpu data
[    0.000000] Built 1 zonelists.  Total pages: 4131867
[    0.000000] Kernel command line: BOOT_IMAGE=/casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash --
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] Extended CMOS year: 2000
[   50.733929] time.c: Detected 3000.187 MHz processor.
[   50.735075] Console: colour VGA+ 80x25
[   50.735091] Checking aperture...
[   50.735098] Calgary: detecting Calgary via BIOS EBDA area
[   50.735099] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[   50.735100] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[   50.760368] Placing software IO TLB between 0x1085000 - 0x5085000
[   50.865580] Memory: 16453288k/17825792k available (2274k kernel code, 322480k reserved, 1181k data, 296k init)
[   50.865609] SLUB: Genslabs=23, HWalign=64, Order=0-1, MinObjects=4, CPUs=8, Nodes=1
[   50.943743] Calibrating delay using timer specific routine.. 6004.53 BogoMIPS (lpj=12009070)
[   50.943765] Security Framework v1.0.0 initialized
[   50.943771] SELinux:  Disabled at boot.
[   50.944597] Dentry cache hash table entries: 2097152 (order: 12, 16777216 bytes)
[   50.951333] Inode-cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[   50.954486] Mount-cache hash table entries: 256
[   50.954588] CPU: L1 I cache: 32K, L1 D cache: 32K
[   50.954589] CPU: L2 cache: 6144K
[   50.954591] CPU 0/0 -> Node 0
[   50.954592] using mwait in idle threads.
[   50.954593] CPU: Physical Processor ID: 0
[   50.954594] CPU: Processor Core ID: 0
[   50.954599] CPU0: Thermal monitoring enabled (TM2)
[   50.954606] SMP alternatives: switching to UP code
[   50.954901] Early unpacking initramfs... done
[   51.186960] ACPI: Core revision 20070126
[   51.186995] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   51.608215] Using local APIC timer interrupts.
[   51.641517] result 25001539
[   51.641518] Detected 25.001 MHz APIC timer.
[   51.643176] SMP alternatives: switching to SMP code
[   51.643305] Booting processor 1/8 APIC 0x4
[   51.653854] Initializing CPU#1
[   51.731042] Calibrating delay using timer specific routine.. 6000.74 BogoMIPS (lpj=12001485)
[   51.731048] CPU: L1 I cache: 32K, L1 D cache: 32K
[   51.731050] CPU: L2 cache: 6144K
[   51.731051] CPU 1/4 -> Node 0
[   51.731053] CPU: Physical Processor ID: 1
[   51.731053] CPU: Processor Core ID: 0
[   51.731058] CPU1: Thermal monitoring enabled (TM2)
[   51.731693] Intel(R) Xeon(R) CPU           E5472  @ 3.00GHz stepping 06
[   51.731720] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[   51.755060] SMP alternatives: switching to SMP code
[   51.755080] Booting processor 2/8 APIC 0x1
[   51.765631] Initializing CPU#2
[   51.842944] Calibrating delay using timer specific routine.. 6000.75 BogoMIPS (lpj=12001510)
[   51.842949] CPU: L1 I cache: 32K, L1 D cache: 32K
[   51.842950] CPU: L2 cache: 6144K
[   51.842952] CPU 2/1 -> Node 0
[   51.842953] CPU: Physical Processor ID: 0
[   51.842954] CPU: Processor Core ID: 1
[   51.842959] CPU2: Thermal monitoring enabled (TM2)
[   51.843593] Intel(R) Xeon(R) CPU           E5472  @ 3.00GHz stepping 06
[   51.843651] checking TSC synchronization [CPU#0 -> CPU#2]: passed.
[   51.866986] SMP alternatives: switching to SMP code
[   51.867121] Booting processor 3/8 APIC 0x5
[   51.877670] Initializing CPU#3
[   51.954845] Calibrating delay using timer specific routine.. 6000.65 BogoMIPS (lpj=12001318)
[   51.954850] CPU: L1 I cache: 32K, L1 D cache: 32K
[   51.954851] CPU: L2 cache: 6144K
[   51.954853] CPU 3/5 -> Node 0
[   51.954855] CPU: Physical Processor ID: 1
[   51.954855] CPU: Processor Core ID: 1
[   51.954860] CPU3: Thermal monitoring enabled (TM2)
[   51.955494] Intel(R) Xeon(R) CPU           E5472  @ 3.00GHz stepping 06
[   51.955536] checking TSC synchronization [CPU#0 -> CPU#3]: passed.
[   51.978864] SMP alternatives: switching to SMP code
[   51.978884] Booting processor 4/8 APIC 0x2
[   51.989431] Initializing CPU#4
[   52.066746] Calibrating delay using timer specific routine.. 6000.66 BogoMIPS (lpj=12001334)
[   52.066751] CPU: L1 I cache: 32K, L1 D cache: 32K
[   52.066752] CPU: L2 cache: 6144K
[   52.066754] CPU 4/2 -> Node 0
[   52.066755] CPU: Physical Processor ID: 0
[   52.066756] CPU: Processor Core ID: 2
[   52.066760] CPU4: Thermal monitoring enabled (TM2)
[   52.067395] Intel(R) Xeon(R) CPU           E5472  @ 3.00GHz stepping 06
[   52.067399] checking TSC synchronization [CPU#0 -> CPU#4]: passed.
[   52.090762] SMP alternatives: switching to SMP code
[   52.090781] Booting processor 5/8 APIC 0x6
[   52.101330] Initializing CPU#5
[   52.178647] Calibrating delay using timer specific routine.. 6000.59 BogoMIPS (lpj=12001196)
[   52.178652] CPU: L1 I cache: 32K, L1 D cache: 32K
[   52.178654] CPU: L2 cache: 6144K
[   52.178655] CPU 5/6 -> Node 0
[   52.178657] CPU: Physical Processor ID: 1
[   52.178657] CPU: Processor Core ID: 2
[   52.178662] CPU5: Thermal monitoring enabled (TM2)
[   52.179297] Intel(R) Xeon(R) CPU           E5472  @ 3.00GHz stepping 06
[   52.179397] checking TSC synchronization [CPU#0 -> CPU#5]: passed.
[   52.202665] SMP alternatives: switching to SMP code
[   52.202685] Booting processor 6/8 APIC 0x3
[   52.213233] Initializing CPU#6
[   52.290548] Calibrating delay using timer specific routine.. 6000.58 BogoMIPS (lpj=12001166)
[   52.290553] CPU: L1 I cache: 32K, L1 D cache: 32K
[   52.290554] CPU: L2 cache: 6144K
[   52.290556] CPU 6/3 -> Node 0
[   52.290557] CPU: Physical Processor ID: 0
[   52.290558] CPU: Processor Core ID: 3
[   52.290562] CPU6: Thermal monitoring enabled (TM2)
[   52.291197] Intel(R) Xeon(R) CPU           E5472  @ 3.00GHz stepping 06
[   52.291300] checking TSC synchronization [CPU#0 -> CPU#6]: passed.
[   52.314568] SMP alternatives: switching to SMP code
[   52.314586] Booting processor 7/8 APIC 0x7
[   52.325134] Initializing CPU#7
[   52.402449] Calibrating delay using timer specific routine.. 6000.58 BogoMIPS (lpj=12001175)
[   52.402454] CPU: L1 I cache: 32K, L1 D cache: 32K
[   52.402455] CPU: L2 cache: 6144K
[   52.402457] CPU 7/7 -> Node 0
[   52.402459] CPU: Physical Processor ID: 1
[   52.402459] CPU: Processor Core ID: 3
[   52.402464] CPU7: Thermal monitoring enabled (TM2)
[   52.403098] Intel(R) Xeon(R) CPU           E5472  @ 3.00GHz stepping 06
[   52.403157] checking TSC synchronization [CPU#0 -> CPU#7]: passed.
[   52.426443] Brought up 8 CPUs
[   53.409453] migration_cost=13,9346
[   53.409671] NET: Registered protocol family 16
[   53.409742] ACPI: bus type pci registered
[   53.409748] PCI: Using configuration type 1
[   53.410467] ACPI: EC: Look up EC in DSDT
[   53.411722] ACPI: Interpreter enabled
[   53.411724] ACPI: (supports S0 S1 S4 S5)
[   53.411732] ACPI: Using IOAPIC for interrupt routing
[   53.414302] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   53.414308] PCI: Probing PCI hardware (bus 00)
[   53.415612] PCI: Transparent bridge - 0000:00:1e.0
[   53.415656] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   53.415845] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[   53.415905] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P5._PRT]
[   53.415964] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P9._PRT]
[   53.416004] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P9.BMF0._PRT]
[   53.416042] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P9.BMF0.BPD0._PRT]
[   53.416101] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P9.BMF3._PRT]
[   53.416192] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]
[   53.416256] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[   53.422362] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 14 15)
[   53.422407] ACPI: PCI Interrupt Link [LNKB] (IRQs *3 4 5 6 7 10 11 14 15)
[   53.422451] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *10 11 14 15)
[   53.422495] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11 14 15) *0, disabled.
[   53.422544] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 *5 6 7 10 11 14 15)
[   53.422588] ACPI: PCI Interrupt Link [LNKF] (IRQs 4 5 6 7 10 *11 14 15)
[   53.422631] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 14 15) *9
[   53.422675] ACPI: PCI Interrupt Link [LNKH] (IRQs 4 5 6 7 10 *11 14 15)
[   53.422727] Linux Plug and Play Support v0.97 (c) Adam Belay
[   53.422735] pnp: PnP ACPI init
[   53.422740] ACPI: bus type pnp registered
[   53.424278] pnp: PnP ACPI: found 11 devices
[   53.424280] ACPI: ACPI bus type pnp unregistered
[   53.424317] PCI: Using ACPI for IRQ routing
[   53.424319] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   53.424391] NET: Registered protocol family 8
[   53.424392] NET: Registered protocol family 20
[   53.424405] PCI-GART: No AMD northbridge found.
[   53.424435] pnp: 00:01: iomem range 0xe0000000-0xefffffff could not be reserved
[   53.424437] pnp: 00:01: iomem range 0xfee00000-0xfee0ffff could not be reserved
[   53.424439] pnp: 00:01: iomem range 0xfec88000-0xfec88fff has been reserved
[   53.424440] pnp: 00:01: iomem range 0xfec89000-0xfec89fff has been reserved
[   53.424646] PCI: Failed to allocate mem resource #6:20000@d0000000 for 0000:01:00.0
[   53.424687] PCI: Bridge: 0000:00:01.0
[   53.424689]   IO window: 2000-2fff
[   53.424691]   MEM window: d0000000-d2ffffff
[   53.424693]   PREFETCH window: c0000000-cfffffff
[   53.424695] PCI: Bridge: 0000:00:05.0
[   53.424696]   IO window: disabled.
[   53.424698]   MEM window: disabled.
[   53.424700]   PREFETCH window: disabled.
[   53.424702] PCI: Bridge: 0000:04:00.0
[   53.424703]   IO window: disabled.
[   53.424705]   MEM window: disabled.
[   53.424708]   PREFETCH window: disabled.
[   53.424710] PCI: Bridge: 0000:03:00.0
[   53.424711]   IO window: disabled.
[   53.424714]   MEM window: disabled.
[   53.424716]   PREFETCH window: disabled.
[   53.424719] PCI: Bridge: 0000:03:00.3
[   53.424720]   IO window: disabled.
[   53.424722]   MEM window: disabled.
[   53.424724]   PREFETCH window: disabled.
[   53.424727] PCI: Bridge: 0000:00:09.0
[   53.424728]   IO window: disabled.
[   53.424730]   MEM window: d3100000-d31fffff
[   53.424732]   PREFETCH window: disabled.
[   53.424734] PCI: Bridge: 0000:00:1c.0
[   53.424736]   IO window: 3000-3fff
[   53.424739]   MEM window: d3000000-d30fffff
[   53.424742]   PREFETCH window: d3300000-d33fffff
[   53.424745] PCI: Bridge: 0000:00:1e.0
[   53.424746]   IO window: disabled.
[   53.424749]   MEM window: d3200000-d32fffff
[   53.424751]   PREFETCH window: disabled.
[   53.424762] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 48 (level, low) -> IRQ 48
[   53.424765] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   53.424771] ACPI: PCI Interrupt 0000:00:05.0[A] -> GSI 52 (level, low) -> IRQ 52
[   53.424774] PCI: Setting latency timer of device 0000:00:05.0 to 64
[   53.424780] ACPI: PCI Interrupt 0000:00:09.0[A] -> GSI 56 (level, low) -> IRQ 56
[   53.424783] PCI: Setting latency timer of device 0000:00:09.0 to 64
[   53.424791] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 56 (level, low) -> IRQ 56
[   53.424794] PCI: Setting latency timer of device 0000:03:00.0 to 64
[   53.424804] ACPI: PCI Interrupt 0000:04:00.0[A] -> GSI 56 (level, low) -> IRQ 56
[   53.424807] PCI: Setting latency timer of device 0000:04:00.0 to 64
[   53.424816] PCI: Setting latency timer of device 0000:03:00.3 to 64
[   53.424828] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
[   53.424831] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   53.424838] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   53.424846] NET: Registered protocol family 2
[   53.425544] Time: tsc clocksource has been installed.
[   53.461687] IP route cache hash table entries: 524288 (order: 10, 4194304 bytes)
[   53.464963] TCP established hash table entries: 2097152 (order: 13, 50331648 bytes)
[   53.484071] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   53.484472] TCP: Hash tables configured (established 2097152 bind 65536)
[   53.484474] TCP reno registered
[   53.497570] checking if image is initramfs... it is
[   53.956910] Freeing initrd memory: 7706k freed
[   53.958976] Simple Boot Flag at 0x41 set to 0x1
[   53.960272] audit: initializing netlink socket (disabled)
[   53.960286] audit(1203706847.712:1): initialized
[   53.962020] VFS: Disk quotas dquot_6.5.1
[   53.962059] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   53.962117] io scheduler noop registered
[   53.962118] io scheduler anticipatory registered
[   53.962120] io scheduler deadline registered
[   53.962185] io scheduler cfq registered (default)
[   53.964715] Boot video device is 0000:01:00.0
[   53.964860] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   53.964882] assign_interrupt_mode Found MSI capability
[   53.964884] Allocate Port Service[0000:00:01.0:pcie00]
[   53.964946] PCI: Setting latency timer of device 0000:00:05.0 to 64
[   53.964966] assign_interrupt_mode Found MSI capability
[   53.964968] Allocate Port Service[0000:00:05.0:pcie00]
[   53.965022] PCI: Setting latency timer of device 0000:00:09.0 to 64
[   53.965045] assign_interrupt_mode Found MSI capability
[   53.965046] Allocate Port Service[0000:00:09.0:pcie00]
[   53.965103] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   53.965133] assign_interrupt_mode Found MSI capability
[   53.965134] Allocate Port Service[0000:00:1c.0:pcie00]
[   53.965158] Allocate Port Service[0000:00:1c.0:pcie02]
[   53.965232] PCI: Setting latency timer of device 0000:03:00.0 to 64
[   53.965258] Allocate Port Service[0000:03:00.0:pcie10]
[   53.965320] PCI: Setting latency timer of device 0000:04:00.0 to 64
[   53.965347] assign_interrupt_mode Found MSI capability
[   53.965348] Allocate Port Service[0000:04:00.0:pcie20]
[   53.981454] Real Time Clock Driver v1.12ac
[   53.981533] Linux agpgart interface v0.102 (c) Dave Jones
[   53.981535] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   53.981616] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   53.982001] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   53.982520] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   53.982617] input: Macintosh mouse button emulation as /class/input/input0
[   53.982676] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[   53.984624] serio: i8042 KBD port at 0x60,0x64 irq 1
[   53.984627] serio: i8042 AUX port at 0x60,0x64 irq 12
[   53.984736] mice: PS/2 mouse device common for all mice
[   53.984828] TCP cubic registered
[   53.984868] NET: Registered protocol family 1
[   53.985033] /build/buildd/linux-source-2.6.22-2.6.22/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   53.985042] Freeing unused kernel memory: 296k freed
[   54.006523] input: AT Translated Set 2 keyboard as /class/input/input1
[   55.100495] AppArmor: AppArmor initialized<5>audit(1203706848.856:2):  type=1505 info="AppArmor initialized" pid=1310
[   55.104565] fuse init (API version 7.8)
[   55.107530] Failure registering capabilities with primary security module.
[   55.137219] ACPI: Processor [CPU0] (supports 8 throttling states)
[   55.137566] ACPI: Processor [CPU1] (supports 8 throttling states)
[   55.137899] ACPI: Processor [CPU2] (supports 8 throttling states)
[   55.138243] ACPI: Processor [CPU3] (supports 8 throttling states)
[   55.138586] ACPI: Processor [CPU4] (supports 8 throttling states)
[   55.138914] ACPI: Processor [CPU5] (supports 8 throttling states)
[   55.139257] ACPI: Processor [CPU6] (supports 8 throttling states)
[   55.139599] ACPI: Processor [CPU7] (supports 8 throttling states)
[   55.378223] usbcore: registered new interface driver usbfs
[   55.378241] usbcore: registered new interface driver hub
[   55.378257] usbcore: registered new device driver usb
[   55.378679] USB Universal Host Controller Interface driver v3.0
[   55.378759] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 20 (level, low) -> IRQ 20
[   55.378768] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   55.378770] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   55.378854] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   55.378877] uhci_hcd 0000:00:1d.0: irq 20, io base 0x00001800
[   55.378951] usb usb1: configuration #1 chosen from 1 choice
[   55.378964] hub 1-0:1.0: USB hub found
[   55.378969] hub 1-0:1.0: 2 ports detected
[   55.384240] SCSI subsystem initialized
[   55.389755] libata version 2.21 loaded.
[   55.483879] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 23
[   55.485444] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   55.485450] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   55.485501] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[   55.485530] ehci_hcd 0000:00:1d.7: debug port 1
[   55.485534] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   55.485543] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xd3508000
[   55.489420] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   55.489490] usb usb2: configuration #1 chosen from 1 choice
[   55.489509] hub 2-0:1.0: USB hub found
[   55.489514] hub 2-0:1.0: 8 ports detected
[   55.595654] ACPI: PCI Interrupt 0000:08:08.0[A] -> GSI 20 (level, low) -> IRQ 20
[   55.645747] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[20]  MMIO=[d3204000-d32047ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   55.645819] ahci 0000:00:1f.2: version 2.2
[   55.645839] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 17 (level, low) -> IRQ 17
[   56.650562] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 6 ports 3 Gbps 0x3f impl RAID mode
[   56.650566] ahci 0000:00:1f.2: flags: 64bit ncq pm led pmp slum part 
[   56.650569] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   56.650953] scsi0 : ahci
[   56.651093] scsi1 : ahci
[   56.651208] scsi2 : ahci
[   56.651319] scsi3 : ahci
[   56.651432] scsi4 : ahci
[   56.651549] scsi5 : ahci
[   56.651660] ata1: SATA max UDMA/133 cmd 0xffffc20004d68500 ctl 0x0000000000000000 bmdma 0x0000000000000000 irq 17
[   56.651663] ata2: SATA max UDMA/133 cmd 0xffffc20004d68580 ctl 0x0000000000000000 bmdma 0x0000000000000000 irq 17
[   56.651665] ata3: SATA max UDMA/133 cmd 0xffffc20004d68600 ctl 0x0000000000000000 bmdma 0x0000000000000000 irq 17
[   56.651667] ata4: SATA max UDMA/133 cmd 0xffffc20004d68680 ctl 0x0000000000000000 bmdma 0x0000000000000000 irq 17
[   56.651670] ata5: SATA max UDMA/133 cmd 0xffffc20004d68700 ctl 0x0000000000000000 bmdma 0x0000000000000000 irq 17
[   56.651672] ata6: SATA max UDMA/133 cmd 0xffffc20004d68780 ctl 0x0000000000000000 bmdma 0x0000000000000000 irq 17
[   56.918410] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0030480000100c77]
[   57.138097] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   57.140300] ata1.00: ATA-7: WDC WD1500ADFD-00NLR5, 21.07QR5, max UDMA/133
[   57.140303] ata1.00: 293046768 sectors, multi 0: LBA48 NCQ (depth 31/32)
[   57.143094] ata1.00: configured for UDMA/133
[   57.629645] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   57.630848] ata2.00: ATA-6: ST31000340NS, SN04, max UDMA/133
[   57.630850] ata2.00: 1953525168 sectors, multi 0: LBA48 NCQ (depth 31/32)
[   57.632425] ata2.00: configured for UDMA/133
[   58.117198] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   58.118403] ata3.00: ATA-6: ST31000340NS, SN04, max UDMA/133
[   58.118405] ata3.00: 1953525168 sectors, multi 0: LBA48 NCQ (depth 31/32)
[   58.119980] ata3.00: configured for UDMA/133
[   58.432909] ata4: SATA link down (SStatus 0 SControl 300)
[   58.744622] ata5: SATA link down (SStatus 0 SControl 300)
[   59.056336] ata6: SATA link down (SStatus 0 SControl 300)
[   59.056409] scsi 0:0:0:0: Direct-Access     ATA      WDC WD1500ADFD-0 21.0 PQ: 0 ANSI: 5
[   59.056671] scsi 1:0:0:0: Direct-Access     ATA      ST31000340NS     SN04 PQ: 0 ANSI: 5
[   59.056919] scsi 2:0:0:0: Direct-Access     ATA      ST31000340NS     SN04 PQ: 0 ANSI: 5
[   59.057183] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 21 (level, low) -> IRQ 21
[   59.057193] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   59.057196] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   59.057224] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[   59.057249] uhci_hcd 0000:00:1d.1: irq 21, io base 0x00001820
[   59.057328] usb usb3: configuration #1 chosen from 1 choice
[   59.057350] hub 3-0:1.0: USB hub found
[   59.057354] hub 3-0:1.0: 2 ports detected
[   59.061877] sd 0:0:0:0: [sda] 293046768 512-byte hardware sectors (150040 MB)
[   59.061885] sd 0:0:0:0: [sda] Write Protect is off
[   59.061886] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   59.061894] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   59.061926] sd 0:0:0:0: [sda] 293046768 512-byte hardware sectors (150040 MB)
[   59.061933] sd 0:0:0:0: [sda] Write Protect is off
[   59.061934] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   59.061947] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   59.061950]  sda: sda1 sda2
[   59.071035] sd 0:0:0:0: [sda] Attached SCSI disk
[   59.071063] sd 1:0:0:0: [sdb] 1953525168 512-byte hardware sectors (1000205 MB)
[   59.071068] sd 1:0:0:0: [sdb] Write Protect is off
[   59.071069] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   59.071078] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   59.071100] sd 1:0:0:0: [sdb] 1953525168 512-byte hardware sectors (1000205 MB)
[   59.071105] sd 1:0:0:0: [sdb] Write Protect is off
[   59.071107] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   59.071114] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   59.071115]  sdb: sdb1
[   59.077167] sd 1:0:0:0: [sdb] Attached SCSI disk
[   59.077231] sd 2:0:0:0: [sdc] 1953525168 512-byte hardware sectors (1000205 MB)
[   59.077238] sd 2:0:0:0: [sdc] Write Protect is off
[   59.077240] sd 2:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[   59.077248] sd 2:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   59.077277] sd 2:0:0:0: [sdc] 1953525168 512-byte hardware sectors (1000205 MB)
[   59.077282] sd 2:0:0:0: [sdc] Write Protect is off
[   59.077283] sd 2:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[   59.077298] sd 2:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   59.077301]  sdc: sdc1
[   59.087090] sd 2:0:0:0: [sdc] Attached SCSI disk
[   59.089206] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   59.089219] sd 1:0:0:0: Attached scsi generic sg1 type 0
[   59.089232] sd 2:0:0:0: Attached scsi generic sg2 type 0
[   59.164332] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 22 (level, low) -> IRQ 22
[   59.164341] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   59.164344] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   59.164360] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[   59.164383] uhci_hcd 0000:00:1d.2: irq 22, io base 0x00001840
[   59.164456] usb usb4: configuration #1 chosen from 1 choice
[   59.164472] hub 4-0:1.0: USB hub found
[   59.164477] hub 4-0:1.0: 2 ports detected
[   59.272222] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 23 (level, low) -> IRQ 23
[   59.272230] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   59.272232] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   59.272249] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[   59.272268] uhci_hcd 0000:00:1d.3: irq 23, io base 0x00001860
[   59.272332] usb usb5: configuration #1 chosen from 1 choice
[   59.272348] hub 5-0:1.0: USB hub found
[   59.272353] hub 5-0:1.0: 2 ports detected
[   59.376156] ata_piix 0000:00:1f.1: version 2.11
[   59.376176] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 16 (level, low) -> IRQ 16
[   59.376200] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   59.376248] scsi6 : ata_piix
[   59.376293] scsi7 : ata_piix
[   59.376346] ata7: PATA max UDMA/100 cmd 0x00000000000101f0 ctl 0x00000000000103f6 bmdma 0x0000000000011880 irq 14
[   59.376348] ata8: PATA max UDMA/100 cmd 0x0000000000010170 ctl 0x0000000000010376 bmdma 0x0000000000011888 irq 15
[   60.067668] ata7.00: ATAPI: Optiarc DVD RW AD-7190A, 1.02, max UDMA/66
[   60.067673] ata7.01: ATAPI: Optiarc DVD RW AD-7190A, 1.02, max UDMA/66
[   60.259477] ata7.00: configured for UDMA/66
[   60.451299] ata7.01: configured for UDMA/66
[   60.451322] ata8: port disabled. ignoring.
[   60.452412] scsi 6:0:0:0: CD-ROM            Optiarc  DVD RW AD-7190A  1.02 PQ: 0 ANSI: 5
[   60.452480] scsi 6:0:0:0: Attached scsi generic sg3 type 5
[   60.453557] scsi 6:0:1:0: CD-ROM            Optiarc  DVD RW AD-7190A  1.02 PQ: 0 ANSI: 5
[   60.453629] scsi 6:0:1:0: Attached scsi generic sg4 type 5
[   60.462792] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[   60.462796] Uniform CD-ROM driver Revision: 3.20
[   60.462925] sr 6:0:0:0: Attached scsi CD-ROM sr0
[   60.471277] sr1: scsi3-mmc drive: 48x/12x writer dvd-ram cd/rw xa/form2 cdda tray
[   60.471314] sr 6:0:1:0: Attached scsi CD-ROM sr1
[   64.892756] ISO 9660 Extensions: Microsoft Joliet Level 3
[   64.932358] ISO 9660 Extensions: RRIP_1991A
[   65.209282] Registering unionfs 1.4
[   65.209285] unionfs: debugging is not enabled
[   65.213477] loop: module loaded
[   65.492712] squashfs: version 3.2-UBUNTU (2007/07/26) Phillip Lougher
[  105.277533] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[  105.380100] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[  105.480438] intel_rng: FWH not detected
[  105.598347] input: PC Speaker as /class/input/input2
[  106.106004] input: ImExPS/2 Generic Explorer Mouse as /class/input/input3
[  106.109200] parport_pc 00:0a: reported by Plug and Play ACPI
[  106.109304] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[  106.336607] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 20 (level, low) -> IRQ 20
[  106.338129] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[  106.544768] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[  108.598570] No dock devices found.
[  108.634460] input: Power Button (FF) as /class/input/input4
[  108.634475] ACPI: Power Button (FF) [PWRF]
[  108.634539] input: Power Button (CM) as /class/input/input5
[  108.634547] ACPI: Power Button (CM) [PWRB]
[  112.278251] lp0: using parport0 (interrupt-driven).
[  112.622110] ppdev: user-space parallel port driver
[  115.525751] Failure registering capabilities with primary security module.
[  116.075572] Bluetooth: Core ver 2.11
[  116.075681] NET: Registered protocol family 31
[  116.075682] Bluetooth: HCI device and connection manager initialized
[  116.075684] Bluetooth: HCI socket layer initialized
[  116.098389] Bluetooth: L2CAP ver 2.8
[  116.098392] Bluetooth: L2CAP socket layer initialized
[  116.349264] Bluetooth: RFCOMM socket layer initialized
[  116.349296] Bluetooth: RFCOMM TTY layer initialized
[  116.349297] Bluetooth: RFCOMM ver 1.8
[  518.474748] program gparted is using a deprecated SCSI ioctl, please convert it to SG_IO
```

and lsmod:```


Module                  Size  Used by
rfcomm                 47656  2 
l2cap                  28672  11 rfcomm
bluetooth              63876  4 rfcomm,l2cap
ppdev                  11272  0 
lp                     15048  0 
cpufreq_userspace       6048  0 
cpufreq_stats           8160  0 
cpufreq_powersave       3072  0 
cpufreq_ondemand       10896  0 
freq_table              6464  2 cpufreq_stats,cpufreq_ondemand
cpufreq_conservative     9608  0 
video                  21140  0 
sbs                    21520  0 
container               6400  0 
button                 10400  0 
dock                   12264  0 
ac                      7304  0 
snd_hda_intel         337192  1 
snd_pcm_oss            50048  0 
snd_mixer_oss          20096  1 snd_pcm_oss
snd_pcm                94344  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy           5380  0 
snd_seq_oss            36864  0 
snd_seq_midi           11008  0 
snd_rawmidi            29824  1 snd_seq_midi
snd_seq_midi_event      9984  2 snd_seq_oss,snd_seq_midi
snd_seq                62496  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              27272  2 snd_pcm,snd_seq
parport_pc             41896  1 
snd_seq_device         10260  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
i2c_core               30208  0 
parport                44172  3 ppdev,lp,parport_pc
serio_raw               9092  0 
snd                    69288  11 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
pcspkr                  4608  0 
psmouse                45596  0 
soundcore              10272  1 snd
shpchp                 38300  0 
snd_page_alloc         12560  2 snd_hda_intel,snd_pcm
pci_hotplug            36612  1 shpchp
evdev                  13056  3 
battery                12424  0 
squashfs               45192  1 
loop                   21764  2 
unionfs                87216  1 
nls_cp437               8192  1 
isofs                  39268  1 
sr_mod                 19876  1 
cdrom                  41768  1 sr_mod
sg                     41384  0 
sd_mod                 32512  0 
ata_piix               20996  1 
ohci1394               38984  0 
ieee1394              109528  1 ohci1394
ata_generic             9988  0 
ahci                   27012  0 
ehci_hcd               40076  0 
libata                138928  3 ata_piix,ata_generic,ahci
scsi_mod              172856  4 sr_mod,sg,sd_mod,libata
uhci_hcd               29600  0 
usbcore               161584  3 ehci_hcd,uhci_hcd
thermal                16528  0 
processor              36232  1 thermal
fan                     6920  0 
fuse                   52528  1 
apparmor               47008  0 
commoncap               9472  1 apparmor
```

---

### Post by Thraxarious on 2008-03-28
I seem to be getting this problem too, I have tried letting the system install without the network driver, then compiling the Intel driver from the server's CD, but no interfaces end up available. I don't see the driver initialize on the boot strangely, even though I did modprobe it into the kernel.

---

### Post by mthaddon on 2008-03-31
I tried Hardy beta and it seemed to work for me... I assume it's a new hardware device that didn't have drivers available in Gutsy.

---

### Post by CaveMole on 2008-04-03
Hardy beta worked for me too!  For AMD64.
(Other distros, including 7.10, and a somewhat recent Debian did not have the 82575EB su[pport)

This was a dual LGA 771 SuperMicro X7DWA-N mBoard.

It has taken me nearly two days to get things working for Windows XP x64!
(Needed to download drivers, etc...)

These Ubuntu guys are really, really fast at supporting new hardware!

---

### Post by kevmitch on 2008-06-25
You need the "igb" module which is included in kernel 2.6.25. If you upgrade to that kernel the interface should work. I've also got an X7DWA-N board and had to stick in an old 100Mbit NIC to run the Debian installer since even the daily build uses only 2.6.24. 

Has anyone been noticing that processes using this NIC will sometimes hang very intermittently? Sometimes they resume functioning after several seconds, sometimes not. For example, when rsyncing a large ammount of data, the transfer will just freeze. The processor use, disk i/o and network traffic go down, but other processes (even ones also using the network) continue to work fine. I have to stop and restart the transfer which will resume normally from the point where it froze.

It seems to occur relatively randomly and is difficult to reproduce consistently. As you can imagine this is a difficult problem to debug, so I can't be certain this NIC is actually responsible, but a brand new driver needing some kinks ironed out seems the the best explanation so far.

I might add that I did run memtester flawlessly on 7500 Mb of my 8006 Mb of fully buffered RAM. Maybe that final 500 Mb is the problem, but I kind of doubt it. Each DIMM is 2G which means that I'm guaranteed to have tested all of them even if I have't tested every last bit.

---

