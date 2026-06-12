---
title: "Interesting wireless problem (Intel 3945) after booting from Windows"
date: 2008-08-19
forum: Networking &amp; Wireless
---

### Post by rocklee on 2008-08-19
It seems my wireless in ubuntu can only work after booting from Windows Vista.  I think it could be something to do with catching the signal during the Windows session.

I also noticed that during a successful wireless boot, I see the wifi light come on...

Anyway here are 2 outputs from the system log comparing ubuntu booting after windows Vista (1) and cold booting Ubuntu :

1. Starting Ubuntu after booting from Windows Vista (I've highlighted in bold the interesting errors in 2 places) :

```

Aug 19 16:23:29 rock-laptop syslogd 1.5.0#1ubuntu1: restart.
Aug 19 16:23:29 rock-laptop kernel: Inspecting /boot/System.map-2.6.24-19-generic
Aug 19 16:23:29 rock-laptop kernel: Loaded 27884 symbols from /boot/System.map-2.6.24-19-generic.
Aug 19 16:23:29 rock-laptop kernel: Symbols match kernel version 2.6.24.
Aug 19 16:23:29 rock-laptop kernel: Loaded 38987 symbols from 102 modules.
Aug 19 16:23:29 rock-laptop kernel: [    0.000000] Initializing cgroup subsys cpuset
Aug 19 16:23:29 rock-laptop kernel: [    0.000000] Initializing cgroup subsys cpu
Aug 19 16:23:29 rock-laptop kernel: [    0.000000] Linux version 2.6.24-19-generic (buildd@terranova) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Fri Jul 11 23:41:49 UTC 2008 (Ubuntu 2.6.24-19.36-generic)
Aug 19 16:23:29 rock-laptop kernel: [    0.000000] BIOS-provided physical RAM map:
Aug 19 16:23:29 rock-laptop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
Aug 19 16:23:29 rock-laptop kernel: [    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
Aug 19 16:23:29 rock-laptop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000007fe72000 (usable)
Aug 19 16:23:29 rock-laptop kernel: [    0.000000]  BIOS-e820: 000000007fe72000 - 0000000080000000 (reserved)
Aug 19 16:23:29 rock-laptop kernel: [    0.000000]  BIOS-e820: 00000000f4000000 - 00000000f8000000 (reserved)
Aug 19 16:23:29 rock-laptop kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
Aug 19 16:23:29 rock-laptop kernel: [    0.000000]  BIOS-e820: 00000000fed18000 - 00000000fed1c000 (reserved)
Aug 19 16:23:29 rock-laptop kernel: [    0.000000]  BIOS-e820: 00000000fed20000 - 00000000fed90000 (reserved)
Aug 19 16:23:29 rock-laptop kernel: [    0.000000]  BIOS-e820: 00000000feda0000 - 00000000feda6000 (reserved)
Aug 19 16:23:29 rock-laptop kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee10000 (reserved)
Aug 19 16:23:29 rock-laptop kernel: [    0.000000]  BIOS-e820: 00000000ffe00000 - 0000000100000000 (reserved)
Aug 19 16:23:29 rock-laptop kernel: [    0.000000] 1150MB HIGHMEM available.
Aug 19 16:23:29 rock-laptop kernel: [    0.000000] 896MB LOWMEM available.
Aug 19 16:23:29 rock-laptop kernel: [    0.000000] Entering add_active_range(0, 0, 523890) 0 entries of 256 used
Aug 19 16:23:29 rock-laptop kernel: [    0.000000] Zone PFN ranges:
Aug 19 16:23:29 rock-laptop kernel: [    0.000000]   DMA             0 ->     4096
Aug 19 16:23:29 rock-laptop kernel: [    0.000000]   Normal       4096 ->   229376
Aug 19 16:23:29 rock-laptop kernel: [    0.000000]   HighMem    229376 ->   523890
Aug 19 16:23:29 rock-laptop kernel: [    0.000000] Movable zone start PFN for each node
Aug 19 16:23:29 rock-laptop kernel: [    0.000000] early_node_map[1] active PFN ranges
Aug 19 16:23:29 rock-laptop kernel: [    0.000000]     0:        0 ->   523890
Aug 19 16:23:29 rock-laptop kernel: [    0.000000] On node 0 totalpages: 523890
Aug 19 16:23:29 rock-laptop kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Aug 19 16:23:29 rock-laptop kernel: [    0.000000]   DMA zone: 0 pages reserved
Aug 19 16:23:29 rock-laptop kernel: [    0.000000]   DMA zone: 4064 pages, LIFO batch:0
Aug 19 16:23:29 rock-laptop kernel: [    0.000000]   Normal zone: 1760 pages used for memmap
Aug 19 16:23:29 rock-laptop kernel: [    0.000000]   Normal zone: 223520 pages, LIFO batch:31
Aug 19 16:23:29 rock-laptop kernel: [    0.000000]   HighMem zone: 2300 pages used for memmap
Aug 19 16:23:29 rock-laptop kernel: [    0.000000]   HighMem zone: 292214 pages, LIFO batch:31
Aug 19 16:23:29 rock-laptop kernel: [    0.000000]   Movable zone: 0 pages used for memmap
Aug 19 16:23:29 rock-laptop kernel: [    0.000000] DMI 2.4 present.
Aug 19 16:23:29 rock-laptop kernel: [    0.000000] ACPI: RSDP signature @ 0xC00FBC80 checksum 0
Aug 19 16:23:29 rock-laptop kernel: [    0.000000] ACPI: RSDP 000FBC80, 0024 (r2 DELL  )
Aug 19 16:23:29 rock-laptop kernel: [    0.000000] ACPI: XSDT 7FE73A00, 0064 (r1 DELL    M08     27D80313 ASL        61)
Aug 19 16:23:29 rock-laptop kernel: [    0.000000] ACPI: FACP 7FE7389C, 00F4 (r4 DELL    M08     27D80313 ASL        61)
Aug 19 16:23:29 rock-laptop kernel: [    0.000000] ACPI: DSDT 7FE74000, 4BD7 (r2 INT430 SYSFexxx     1001 INTL 20050624)
Aug 19 16:23:29 rock-laptop kernel: [    0.000000] ACPI: FACS 7FE82800, 0040
Aug 19 16:23:29 rock-laptop kernel: [    0.000000] ACPI: HPET 7FE73B00, 0038 (r1 DELL    M08            1 ASL        61)
Aug 19 16:23:29 rock-laptop kernel: [    0.000000] ACPI: APIC 7FE73C00, 0068 (r1 DELL    M08     27D80313 ASL        47)
Aug 19 16:23:29 rock-laptop kernel: [    0.000000] ACPI: MCFG 7FE73BC0, 003E (r16 DELL    M08     27D80313 ASL        61)
Aug 19 16:23:29 rock-laptop kernel: [    0.000000] ACPI: SLIC 7FE73C9C, 0176 (r1 DELL    M08     27D80313 ASL        61)
Aug 19 16:23:29 rock-laptop kernel: [    0.000000] ACPI: OSFR 7FE73200, 002C (r1 DELL    M08     27D80313 ASL        61)
Aug 19 16:23:29 rock-laptop kernel: [    0.000000] ACPI: BOOT 7FE737C0, 0028 (r1 DELL    M08     27D80313 ASL        61)
Aug 19 16:23:29 rock-laptop kernel: [    0.000000] ACPI: SSDT 7FE72202, 04CC (r1  PmRef    CpuPm     3000 INTL 20050624)
Aug 19 16:23:29 rock-laptop kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
Aug 19 16:23:29 rock-laptop kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Aug 19 16:23:29 rock-laptop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Aug 19 16:23:29 rock-laptop kernel: [    0.000000] Processor #0 6:15 APIC version 20
Aug 19 16:23:29 rock-laptop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Aug 19 16:23:29 rock-laptop kernel: [    0.000000] Processor #1 6:15 APIC version 20
Aug 19 16:23:29 rock-laptop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Aug 19 16:23:29 rock-laptop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Aug 19 16:23:29 rock-laptop kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Aug 19 16:23:29 rock-laptop kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
Aug 19 16:23:29 rock-laptop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Aug 19 16:23:29 rock-laptop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Aug 19 16:23:29 rock-laptop kernel: [    0.000000] ACPI: IRQ0 used by override.
Aug 19 16:23:29 rock-laptop kernel: [    0.000000] ACPI: IRQ2 used by override.
Aug 19 16:23:29 rock-laptop kernel: [    0.000000] ACPI: IRQ9 used by override.
Aug 19 16:23:29 rock-laptop kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Aug 19 16:23:29 rock-laptop kernel: [    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
Aug 19 16:23:29 rock-laptop kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Aug 19 16:23:29 rock-laptop kernel: [    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:74000000)
Aug 19 16:23:29 rock-laptop kernel: [    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
Aug 19 16:23:29 rock-laptop kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 0000000000100000
Aug 19 16:23:29 rock-laptop kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 519798
Aug 19 16:23:29 rock-laptop kernel: [    0.000000] Kernel command line: root=UUID=96616c7a-aa80-45cb-aea6-7845b990a3fb ro quiet splash i8042.nomux=1
Aug 19 16:23:29 rock-laptop kernel: [    0.000000] mapped APIC to ffffb000 (fee00000)
Aug 19 16:23:29 rock-laptop kernel: [    0.000000] mapped IOAPIC to ffffa000 (fec00000)
Aug 19 16:23:29 rock-laptop kernel: [    0.000000] Enabling fast FPU save and restore... done.
Aug 19 16:23:29 rock-laptop kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Aug 19 16:23:29 rock-laptop kernel: [    0.000000] Initializing CPU#0
Aug 19 16:23:29 rock-laptop kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Aug 19 16:23:29 rock-laptop kernel: [    0.000000] Detected 1995.012 MHz processor.
Aug 19 16:23:29 rock-laptop kernel: [    9.290258] Console: colour VGA+ 80x25
Aug 19 16:23:29 rock-laptop kernel: [    9.290261] console [tty0] enabled
Aug 19 16:23:29 rock-laptop kernel: [    9.290555] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Aug 19 16:23:29 rock-laptop kernel: [    9.290836] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Aug 19 16:23:29 rock-laptop kernel: [    9.370906] Memory: 2065576k/2095560k available (2177k kernel code, 28688k reserved, 1006k data, 368k init, 1178056k highmem)
Aug 19 16:23:29 rock-laptop kernel: [    9.370912] virtual kernel memory layout:
Aug 19 16:23:29 rock-laptop kernel: [    9.370913]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
Aug 19 16:23:29 rock-laptop kernel: [    9.370914]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Aug 19 16:23:29 rock-laptop kernel: [    9.370915]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
Aug 19 16:23:29 rock-laptop kernel: [    9.370916]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
Aug 19 16:23:29 rock-laptop kernel: [    9.370917]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
Aug 19 16:23:29 rock-laptop kernel: [    9.370918]       .data : 0xc0320474 - 0xc041bdc4   (1006 kB)
Aug 19 16:23:29 rock-laptop kernel: [    9.370918]       .text : 0xc0100000 - 0xc0320474   (2177 kB)
Aug 19 16:23:29 rock-laptop kernel: [    9.370921] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Aug 19 16:23:29 rock-laptop kernel: [    9.370959] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
Aug 19 16:23:29 rock-laptop kernel: [    9.371090] hpet clockevent registered
Aug 19 16:23:29 rock-laptop kernel: [    9.451052] Calibrating delay using timer specific routine.. 3994.55 BogoMIPS (lpj=7989104)
Aug 19 16:23:29 rock-laptop kernel: [    9.451073] Security Framework initialized
Aug 19 16:23:29 rock-laptop kernel: [    9.451079] SELinux:  Disabled at boot.
Aug 19 16:23:29 rock-laptop kernel: [    9.451092] AppArmor: AppArmor initialized
Aug 19 16:23:29 rock-laptop kernel: [    9.451096] Failure registering capabilities with primary security module.
Aug 19 16:23:29 rock-laptop kernel: [    9.451103] Mount-cache hash table entries: 512
Aug 19 16:23:29 rock-laptop kernel: [    9.451218] Initializing cgroup subsys ns
Aug 19 16:23:29 rock-laptop kernel: [    9.451223] Initializing cgroup subsys cpuacct
Aug 19 16:23:29 rock-laptop kernel: [    9.451232] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e39d 00000000 00000001 00000000
Aug 19 16:23:29 rock-laptop kernel: [    9.451239] monitor/mwait feature present.
Aug 19 16:23:29 rock-laptop kernel: [    9.451240] using mwait in idle threads.
Aug 19 16:23:29 rock-laptop kernel: [    9.451244] CPU: L1 I cache: 32K, L1 D cache: 32K
Aug 19 16:23:29 rock-laptop kernel: [    9.451246] CPU: L2 cache: 2048K
Aug 19 16:23:29 rock-laptop kernel: [    9.451248] CPU: Physical Processor ID: 0
Aug 19 16:23:29 rock-laptop kernel: [    9.451250] CPU: Processor Core ID: 0
Aug 19 16:23:29 rock-laptop kernel: [    9.451251] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e39d 00000000 00000001 00000000
Aug 19 16:23:29 rock-laptop kernel: [    9.451260] Compat vDSO mapped to ffffe000.
Aug 19 16:23:29 rock-laptop kernel: [    9.451271] Checking 'hlt' instruction... OK.
Aug 19 16:23:29 rock-laptop kernel: [    9.467388] SMP alternatives: switching to UP code
Aug 19 16:23:29 rock-laptop kernel: [    9.468819] Early unpacking initramfs... done
Aug 19 16:23:29 rock-laptop kernel: [    9.756180] ACPI: Core revision 20070126
Aug 19 16:23:29 rock-laptop kernel: [    9.756216] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Aug 19 16:23:29 rock-laptop kernel: [    9.760362] CPU0: Intel(R) Core(TM)2 Duo CPU     T5750  @ 2.00GHz stepping 0d
Aug 19 16:23:29 rock-laptop kernel: [    9.760376] SMP alternatives: switching to SMP code
Aug 19 16:23:29 rock-laptop kernel: [    9.760993] Booting processor 1/1 eip 3000
Aug 19 16:23:29 rock-laptop kernel: [    9.771196] Initializing CPU#1
Aug 19 16:23:29 rock-laptop kernel: [    9.850825] Calibrating delay using timer specific routine.. 3990.05 BogoMIPS (lpj=7980110)
Aug 19 16:23:29 rock-laptop kernel: [    9.850831] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e39d 00000000 00000001 00000000
Aug 19 16:23:29 rock-laptop kernel: [    9.850835] monitor/mwait feature present.
Aug 19 16:23:29 rock-laptop kernel: [    9.850837] CPU: L1 I cache: 32K, L1 D cache: 32K
Aug 19 16:23:29 rock-laptop kernel: [    9.850839] CPU: L2 cache: 2048K
Aug 19 16:23:29 rock-laptop kernel: [    9.850841] CPU: Physical Processor ID: 0
Aug 19 16:23:29 rock-laptop kernel: [    9.850842] CPU: Processor Core ID: 1
Aug 19 16:23:29 rock-laptop kernel: [    9.850843] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e39d 00000000 00000001 00000000
Aug 19 16:23:29 rock-laptop kernel: [    9.851308] CPU1: Intel(R) Core(TM)2 Duo CPU     T5750  @ 2.00GHz stepping 0d
Aug 19 16:23:29 rock-laptop kernel: [    9.851328] Total of 2 processors activated (7984.60 BogoMIPS).
Aug 19 16:23:29 rock-laptop kernel: [    9.851528] ENABLING IO-APIC IRQs
Aug 19 16:23:29 rock-laptop kernel: [    9.851717] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Aug 19 16:23:29 rock-laptop kernel: [    9.998841] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
Aug 19 16:23:29 rock-laptop kernel: [   10.018843] Brought up 2 CPUs
Aug 19 16:23:29 rock-laptop kernel: [   10.018864] CPU0 attaching sched-domain:
Aug 19 16:23:29 rock-laptop kernel: [   10.018867]  domain 0: span 03
Aug 19 16:23:29 rock-laptop kernel: [   10.018868]   groups: 01 02
Aug 19 16:23:29 rock-laptop kernel: [   10.018871] CPU1 attaching sched-domain:
Aug 19 16:23:29 rock-laptop kernel: [   10.018872]  domain 0: span 03
Aug 19 16:23:29 rock-laptop kernel: [   10.018873]   groups: 02 01
Aug 19 16:23:29 rock-laptop kernel: [   10.019058] net_namespace: 64 bytes
Aug 19 16:23:29 rock-laptop kernel: [   10.019067] Booting paravirtualized kernel on bare hardware
Aug 19 16:23:29 rock-laptop kernel: [   10.019462] Time: 16:22:44  Date: 08/19/08
Aug 19 16:23:29 rock-laptop kernel: [   10.019485] NET: Registered protocol family 16
Aug 19 16:23:29 rock-laptop kernel: [   10.019639] EISA bus registered
Aug 19 16:23:29 rock-laptop kernel: [   10.019643] ACPI: bus type pci registered
Aug 19 16:23:29 rock-laptop kernel: [   10.030282] PCI: PCI BIOS revision 2.10 entry at 0xfad66, last bus=13
Aug 19 16:23:29 rock-laptop kernel: [   10.030284] PCI: Using configuration type 1
Aug 19 16:23:29 rock-laptop kernel: [   10.030297] Setting up standard PCI resources
Aug 19 16:23:29 rock-laptop kernel: [   10.037328] ACPI: EC: Look up EC in DSDT
Aug 19 16:23:29 rock-laptop kernel: [   10.037440] ACPI: BIOS _OSI(Linux) query ignored
Aug 19 16:23:29 rock-laptop kernel: [   10.037442] ACPI: DMI System Vendor: Dell Inc.
Aug 19 16:23:29 rock-laptop kernel: [   10.037443] ACPI: DMI Product Name: XPS M1530                       
Aug 19 16:23:29 rock-laptop kernel: [   10.037444] ACPI: DMI Product Version: 
Aug 19 16:23:29 rock-laptop kernel: [   10.037446] ACPI: DMI Board Name: 0D501F
Aug 19 16:23:29 rock-laptop kernel: [   10.037447] ACPI: DMI BIOS Vendor: Dell Inc.
Aug 19 16:23:29 rock-laptop kernel: [   10.037448] ACPI: DMI BIOS Date: 03/19/2008
Aug 19 16:23:29 rock-laptop kernel: [   10.037449] ACPI: Please send DMI info above to [email]linux-acpi@vger.kernel.org[/email]
Aug 19 16:23:29 rock-laptop kernel: [   10.037451] ACPI: If "acpi_osi=Linux" works better, please notify [email]linux-acpi@vger.kernel.org[/email]
Aug 19 16:23:29 rock-laptop kernel: [   10.043042] ACPI: Interpreter enabled
Aug 19 16:23:29 rock-laptop kernel: [   10.043046] ACPI: (supports S0 S3 S4 S5)
Aug 19 16:23:29 rock-laptop kernel: [   10.043057] ACPI: Using IOAPIC for interrupt routing
Aug 19 16:23:29 rock-laptop kernel: [   10.061525] ACPI: PCI Root Bridge [PCI0] (0000:00)
Aug 19 16:23:29 rock-laptop kernel: [   10.062485] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
Aug 19 16:23:29 rock-laptop kernel: [   10.062489] PCI quirk: region 1080-10bf claimed by ICH6 GPIO
Aug 19 16:23:29 rock-laptop kernel: [   10.064005] PCI: Transparent bridge - 0000:00:1e.0
Aug 19 16:23:29 rock-laptop kernel: [   10.064052] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Aug 19 16:23:29 rock-laptop kernel: [   10.064451] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]
Aug 19 16:23:29 rock-laptop kernel: [   10.064578] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
Aug 19 16:23:29 rock-laptop kernel: [   10.064659] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
Aug 19 16:23:29 rock-laptop kernel: [   10.064759] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
Aug 19 16:23:29 rock-laptop kernel: [   10.064859] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP05._PRT]
Aug 19 16:23:29 rock-laptop kernel: [   10.073735] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 11) *7
Aug 19 16:23:29 rock-laptop kernel: [   10.073832] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *10
Aug 19 16:23:29 rock-laptop kernel: [   10.073926] ACPI: PCI Interrupt Link [LNKC] (IRQs 9 10 11) *5
Aug 19 16:23:29 rock-laptop kernel: [   10.074011] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 7 9 10 11) *0, disabled.
Aug 19 16:23:29 rock-laptop kernel: [   10.074106] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
Aug 19 16:23:29 rock-laptop kernel: [   10.074204] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
Aug 19 16:23:29 rock-laptop kernel: [   10.074300] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
Aug 19 16:23:29 rock-laptop kernel: [   10.074386] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Aug 19 16:23:29 rock-laptop kernel: [   10.074511] Linux Plug and Play Support v0.97 (c) Adam Belay
Aug 19 16:23:29 rock-laptop kernel: [   10.074538] pnp: PnP ACPI init
Aug 19 16:23:29 rock-laptop kernel: [   10.074544] ACPI: bus type pnp registered
Aug 19 16:23:29 rock-laptop kernel: [   10.108610] pnpacpi: exceeded the max number of mem resources: 12
Aug 19 16:23:29 rock-laptop kernel: [   10.108780] pnp: PnP ACPI: found 13 devices
Aug 19 16:23:29 rock-laptop kernel: [   10.108782] ACPI: ACPI bus type pnp unregistered
Aug 19 16:23:29 rock-laptop kernel: [   10.108785] PnPBIOS: Disabled by ACPI PNP
Aug 19 16:23:29 rock-laptop kernel: [   10.108962] PCI: Using ACPI for IRQ routing
Aug 19 16:23:29 rock-laptop kernel: [   10.108965] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Aug 19 16:23:29 rock-laptop kernel: [   10.194644] NET: Registered protocol family 8
Aug 19 16:23:29 rock-laptop kernel: [   10.194646] NET: Registered protocol family 20
Aug 19 16:23:29 rock-laptop kernel: [   10.194674] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
Aug 19 16:23:29 rock-laptop kernel: [   10.194677] hpet0: 3 64-bit timers, 14318180 Hz
Aug 19 16:23:29 rock-laptop kernel: [   10.195709] AppArmor: AppArmor Filesystem Enabled
Aug 19 16:23:29 rock-laptop kernel: [   10.198636] Time: tsc clocksource has been installed.
Aug 19 16:23:29 rock-laptop kernel: [   10.198644] Switched to high resolution mode on CPU 0
Aug 19 16:23:29 rock-laptop kernel: [   10.198739] Switched to high resolution mode on CPU 1
Aug 19 16:23:29 rock-laptop kernel: [   10.214615] system 00:01: iomem range 0xff800000-0xff8fffff has been reserved
Aug 19 16:23:29 rock-laptop kernel: [   10.214618] system 00:01: iomem range 0xffc00000-0xffcfffff has been reserved
Aug 19 16:23:29 rock-laptop kernel: [   10.214625] system 00:06: ioport range 0xc80-0xcff could not be reserved
Aug 19 16:23:29 rock-laptop kernel: [   10.214632] system 00:09: iomem range 0xfed00000-0xfed003ff has been reserved
Aug 19 16:23:29 rock-laptop kernel: [   10.214637] system 00:0a: ioport range 0x900-0x97f has been reserved
Aug 19 16:23:29 rock-laptop kernel: [   10.214639] system 00:0a: ioport range 0x4d0-0x4d1 has been reserved
Aug 19 16:23:29 rock-laptop kernel: [   10.214641] system 00:0a: ioport range 0x1000-0x1005 has been reserved
Aug 19 16:23:29 rock-laptop kernel: [   10.214643] system 00:0a: ioport range 0x1008-0x100f has been reserved
Aug 19 16:23:29 rock-laptop kernel: [   10.214649] system 00:0b: ioport range 0xf400-0xf4fe has been reserved
Aug 19 16:23:29 rock-laptop kernel: [   10.214651] system 00:0b: ioport range 0x1006-0x1007 has been reserved
Aug 19 16:23:29 rock-laptop kernel: [   10.214653] system 00:0b: ioport range 0x100a-0x1059 could not be reserved
Aug 19 16:23:29 rock-laptop kernel: [   10.214655] system 00:0b: ioport range 0x1080-0x10bf has been reserved
Aug 19 16:23:29 rock-laptop kernel: [   10.214658] system 00:0b: ioport range 0x10c0-0x10df has been reserved
Aug 19 16:23:29 rock-laptop kernel: [   10.214660] system 00:0b: ioport range 0x1010-0x102f has been reserved
Aug 19 16:23:29 rock-laptop kernel: [   10.214662] system 00:0b: ioport range 0x809-0x809 has been reserved
Aug 19 16:23:29 rock-laptop kernel: [   10.214667] system 00:0c: iomem range 0x0-0x9efff could not be reserved
Aug 19 16:23:29 rock-laptop kernel: [   10.214670] system 00:0c: iomem range 0x9f000-0x9ffff could not be reserved
Aug 19 16:23:29 rock-laptop kernel: [   10.214672] system 00:0c: iomem range 0xc0000-0xcffff could not be reserved
Aug 19 16:23:29 rock-laptop kernel: [   10.214674] system 00:0c: iomem range 0xe0000-0xfffff could not be reserved
Aug 19 16:23:29 rock-laptop kernel: [   10.214677] system 00:0c: iomem range 0x100000-0x7fe71fff could not be reserved
Aug 19 16:23:29 rock-laptop kernel: [   10.214679] system 00:0c: iomem range 0x7fe72000-0x7fefffff could not be reserved
Aug 19 16:23:29 rock-laptop kernel: [   10.214681] system 00:0c: iomem range 0x7ff00000-0x7fffffff could not be reserved
Aug 19 16:23:29 rock-laptop kernel: [   10.214684] system 00:0c: iomem range 0xffe00000-0xffffffff could not be reserved
Aug 19 16:23:29 rock-laptop kernel: [   10.214686] system 00:0c: iomem range 0xffa00000-0xffbfffff has been reserved
Aug 19 16:23:29 rock-laptop kernel: [   10.214689] system 00:0c: iomem range 0xfec00000-0xfec0ffff could not be reserved
Aug 19 16:23:29 rock-laptop kernel: [   10.214691] system 00:0c: iomem range 0xfee00000-0xfee0ffff could not be reserved
Aug 19 16:23:29 rock-laptop kernel: [   10.214694] system 00:0c: iomem range 0xfed20000-0xfed8ffff could not be reserved
Aug 19 16:23:29 rock-laptop kernel: [   10.245036] PCI: Bridge: 0000:00:01.0
Aug 19 16:23:29 rock-laptop kernel: [   10.245038]   IO window: e000-efff
Aug 19 16:23:29 rock-laptop kernel: [   10.245042]   MEM window: fa000000-feafffff
Aug 19 16:23:29 rock-laptop kernel: [   10.245045]   PREFETCH window: e0000000-efffffff
Aug 19 16:23:29 rock-laptop kernel: [   10.245048] PCI: Bridge: 0000:00:1c.0
Aug 19 16:23:29 rock-laptop kernel: [   10.245051]   IO window: d000-dfff
Aug 19 16:23:29 rock-laptop kernel: [   10.245057]   MEM window: f9f00000-f9ffffff
Aug 19 16:23:29 rock-laptop kernel: [   10.245061]   PREFETCH window: disabled.
Aug 19 16:23:29 rock-laptop kernel: [   10.245067] PCI: Bridge: 0000:00:1c.1
Aug 19 16:23:29 rock-laptop kernel: [   10.245068]   IO window: disabled.
Aug 19 16:23:29 rock-laptop kernel: [   10.245074]   MEM window: f9e00000-f9efffff
Aug 19 16:23:29 rock-laptop kernel: [   10.245078]   PREFETCH window: disabled.
Aug 19 16:23:29 rock-laptop kernel: [   10.245084] PCI: Bridge: 0000:00:1c.4
Aug 19 16:23:29 rock-laptop kernel: [   10.245087]   IO window: c000-cfff
Aug 19 16:23:29 rock-laptop kernel: [   10.245093]   MEM window: f9c00000-f9dfffff
Aug 19 16:23:29 rock-laptop kernel: [   10.245097]   PREFETCH window: f0000000-f01fffff
Aug 19 16:23:29 rock-laptop kernel: [   10.245103] PCI: Bridge: 0000:00:1e.0
Aug 19 16:23:29 rock-laptop kernel: [   10.245104]   IO window: disabled.
Aug 19 16:23:29 rock-laptop kernel: [   10.245110]   MEM window: f9b00000-f9bfffff
Aug 19 16:23:29 rock-laptop kernel: [   10.245114]   PREFETCH window: disabled.
Aug 19 16:23:29 rock-laptop kernel: [   10.245131] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
Aug 19 16:23:29 rock-laptop kernel: [   10.245136] PCI: Setting latency timer of device 0000:00:01.0 to 64
Aug 19 16:23:29 rock-laptop kernel: [   10.245160] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
Aug 19 16:23:29 rock-laptop kernel: [   10.245165] PCI: Setting latency timer of device 0000:00:1c.0 to 64
Aug 19 16:23:29 rock-laptop kernel: [   10.245190] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 17 (level, low) -> IRQ 17
Aug 19 16:23:29 rock-laptop kernel: [   10.245195] PCI: Setting latency timer of device 0000:00:1c.1 to 64
Aug 19 16:23:29 rock-laptop kernel: [   10.245219] ACPI: PCI Interrupt 0000:00:1c.4[A] -> GSI 16 (level, low) -> IRQ 16
Aug 19 16:23:29 rock-laptop kernel: [   10.245225] PCI: Setting latency timer of device 0000:00:1c.4 to 64
Aug 19 16:23:29 rock-laptop kernel: [   10.245239] PCI: Setting latency timer of device 0000:00:1e.0 to 64
Aug 19 16:23:29 rock-laptop kernel: [   10.245248] NET: Registered protocol family 2
Aug 19 16:23:29 rock-laptop kernel: [   10.282598] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Aug 19 16:23:29 rock-laptop kernel: [   10.282787] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Aug 19 16:23:29 rock-laptop kernel: [   10.283168] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Aug 19 16:23:29 rock-laptop kernel: [   10.283374] TCP: Hash tables configured (established 131072 bind 65536)
Aug 19 16:23:29 rock-laptop kernel: [   10.283376] TCP reno registered
Aug 19 16:23:29 rock-laptop kernel: [   10.294656] checking if image is initramfs... it is
Aug 19 16:23:29 rock-laptop kernel: [   10.859308] Freeing initrd memory: 7307k freed
Aug 19 16:23:29 rock-laptop kernel: [   10.859447] Simple Boot Flag at 0x79 set to 0x1
Aug 19 16:23:29 rock-laptop kernel: [   10.859963] audit: initializing netlink socket (disabled)
Aug 19 16:23:29 rock-laptop kernel: [   10.859975] audit(1219162964.365:1): initialized
Aug 19 16:23:29 rock-laptop kernel: [   10.860160] highmem bounce pool size: 64 pages
Aug 19 16:23:29 rock-laptop kernel: [   10.861765] VFS: Disk quotas dquot_6.5.1
Aug 19 16:23:29 rock-laptop kernel: [   10.861828] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Aug 19 16:23:29 rock-laptop kernel: [   10.861940] io scheduler noop registered
Aug 19 16:23:29 rock-laptop kernel: [   10.861941] io scheduler anticipatory registered
Aug 19 16:23:29 rock-laptop kernel: [   10.861943] io scheduler deadline registered
Aug 19 16:23:29 rock-laptop kernel: [   10.861952] io scheduler cfq registered (default)
Aug 19 16:23:29 rock-laptop kernel: [   10.862112] Boot video device is 0000:01:00.0
Aug 19 16:23:29 rock-laptop kernel: [   10.862202] PCI: Setting latency timer of device 0000:00:01.0 to 64
Aug 19 16:23:29 rock-laptop kernel: [   10.862248] assign_interrupt_mode Found MSI capability
Aug 19 16:23:29 rock-laptop kernel: [   10.862278] Allocate Port Service[0000:00:01.0:pcie00]
Aug 19 16:23:29 rock-laptop kernel: [   10.862307] Allocate Port Service[0000:00:01.0:pcie02]
Aug 19 16:23:29 rock-laptop kernel: [   10.862380] PCI: Setting latency timer of device 0000:00:1c.0 to 64
Aug 19 16:23:29 rock-laptop kernel: [   10.862441] assign_interrupt_mode Found MSI capability
Aug 19 16:23:29 rock-laptop kernel: [   10.862489] Allocate Port Service[0000:00:1c.0:pcie00]
Aug 19 16:23:29 rock-laptop kernel: [   10.862518] Allocate Port Service[0000:00:1c.0:pcie02]
Aug 19 16:23:29 rock-laptop kernel: [   10.862620] PCI: Setting latency timer of device 0000:00:1c.1 to 64
Aug 19 16:23:29 rock-laptop kernel: [   10.862681] assign_interrupt_mode Found MSI capability
Aug 19 16:23:29 rock-laptop kernel: [   10.862729] Allocate Port Service[0000:00:1c.1:pcie00]
Aug 19 16:23:29 rock-laptop kernel: [   10.862756] Allocate Port Service[0000:00:1c.1:pcie02]
Aug 19 16:23:29 rock-laptop kernel: [   10.862853] PCI: Setting latency timer of device 0000:00:1c.4 to 64
Aug 19 16:23:29 rock-laptop kernel: [   10.862914] assign_interrupt_mode Found MSI capability
Aug 19 16:23:29 rock-laptop kernel: [   10.862963] Allocate Port Service[0000:00:1c.4:pcie00]
Aug 19 16:23:29 rock-laptop kernel: [   10.862989] Allocate Port Service[0000:00:1c.4:pcie02]
Aug 19 16:23:29 rock-laptop kernel: [   10.863210] isapnp: Scanning for PnP cards...
Aug 19 16:23:29 rock-laptop kernel: [   11.217565] isapnp: No Plug & Play device found
Aug 19 16:23:29 rock-laptop kernel: [   11.238003] Real Time Clock Driver v1.12ac
Aug 19 16:23:29 rock-laptop kernel: [   11.238127] hpet_resources: 0xfed00000 is busy
Aug 19 16:23:29 rock-laptop kernel: [   11.238178] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Aug 19 16:23:29 rock-laptop kernel: [   11.239144] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Aug 19 16:23:29 rock-laptop kernel: [   11.239200] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Aug 19 16:23:29 rock-laptop kernel: [   11.239279] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Aug 19 16:23:29 rock-laptop kernel: [   11.252053] serio: i8042 KBD port at 0x60,0x64 irq 1
Aug 19 16:23:29 rock-laptop kernel: [   11.252057] serio: i8042 AUX port at 0x60,0x64 irq 12
Aug 19 16:23:29 rock-laptop kernel: [   11.278027] mice: PS/2 mouse device common for all mice
Aug 19 16:23:29 rock-laptop kernel: [   11.278116] EISA: Probing bus 0 at eisa.0
Aug 19 16:23:29 rock-laptop kernel: [   11.278124] Cannot allocate resource for EISA slot 1
Aug 19 16:23:29 rock-laptop kernel: [   11.278154] EISA: Detected 0 cards.
Aug 19 16:23:29 rock-laptop kernel: [   11.278156] cpuidle: using governor ladder
Aug 19 16:23:29 rock-laptop kernel: [   11.278158] cpuidle: using governor menu
Aug 19 16:23:29 rock-laptop kernel: [   11.278229] NET: Registered protocol family 1
Aug 19 16:23:29 rock-laptop kernel: [   11.278252] Using IPI No-Shortcut mode
Aug 19 16:23:29 rock-laptop kernel: [   11.278277] registered taskstats version 1
Aug 19 16:23:29 rock-laptop kernel: [   11.278389]   Magic number: 4:958:388
Aug 19 16:23:29 rock-laptop kernel: [   11.278456] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Aug 19 16:23:29 rock-laptop kernel: [   11.278457] EDD information not available.
Aug 19 16:23:29 rock-laptop kernel: [   11.278645] Freeing unused kernel memory: 368k freed
Aug 19 16:23:29 rock-laptop kernel: [   11.301196] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
Aug 19 16:23:29 rock-laptop kernel: [   12.466380] fuse init (API version 7.9)
Aug 19 16:23:29 rock-laptop kernel: [   12.503483] ACPI: SSDT 7FE72D38, 0244 (r1  PmRef  Cpu0Ist     3000 INTL 20050624)
Aug 19 16:23:29 rock-laptop kernel: [   12.503655] ACPI: SSDT 7FE726CE, 05E5 (r1  PmRef  Cpu0Cst     3001 INTL 20050624)
Aug 19 16:23:29 rock-laptop kernel: [   12.504141] Monitor-Mwait will be used to enter C-1 state
Aug 19 16:23:29 rock-laptop kernel: [   12.504144] Monitor-Mwait will be used to enter C-2 state
Aug 19 16:23:29 rock-laptop kernel: [   12.504146] Monitor-Mwait will be used to enter C-3 state
Aug 19 16:23:29 rock-laptop kernel: [   12.504253] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
Aug 19 16:23:29 rock-laptop kernel: [   12.504257] ACPI: Processor [CPU0] (supports 8 throttling states)
Aug 19 16:23:29 rock-laptop kernel: [   12.504447] ACPI: SSDT 7FE72F7C, 00C4 (r1  PmRef  Cpu1Ist     3000 INTL 20050624)
Aug 19 16:23:29 rock-laptop kernel: [   12.504604] ACPI: SSDT 7FE72CB3, 0085 (r1  PmRef  Cpu1Cst     3000 INTL 20050624)
Aug 19 16:23:29 rock-laptop kernel: [   12.505194] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
Aug 19 16:23:29 rock-laptop kernel: [   12.505198] ACPI: Processor [CPU1] (supports 8 throttling states)
Aug 19 16:23:29 rock-laptop kernel: [   12.506254] ACPI: Thermal Zone [THM] (59 C)
Aug 19 16:23:29 rock-laptop kernel: [   12.688744] usbcore: registered new interface driver usbfs
Aug 19 16:23:29 rock-laptop kernel: [   12.688763] usbcore: registered new interface driver hub
Aug 19 16:23:29 rock-laptop kernel: [   12.688958] usbcore: registered new device driver usb
Aug 19 16:23:29 rock-laptop kernel: [   12.698994] USB Universal Host Controller Interface driver v3.0
Aug 19 16:23:29 rock-laptop kernel: [   12.699057] ACPI: PCI Interrupt 0000:00:1a.0[A] -> GSI 20 (level, low) -> IRQ 18
Aug 19 16:23:29 rock-laptop kernel: [   12.699070] PCI: Setting latency timer of device 0000:00:1a.0 to 64
Aug 19 16:23:29 rock-laptop kernel: [   12.699074] uhci_hcd 0000:00:1a.0: UHCI Host Controller
Aug 19 16:23:29 rock-laptop kernel: [   12.699321] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
Aug 19 16:23:29 rock-laptop kernel: [   12.699356] uhci_hcd 0000:00:1a.0: irq 18, io base 0x00006f20
Aug 19 16:23:29 rock-laptop kernel: [   12.699476] usb usb1: configuration #1 chosen from 1 choice
Aug 19 16:23:29 rock-laptop kernel: [   12.699497] hub 1-0:1.0: USB hub found
Aug 19 16:23:29 rock-laptop kernel: [   12.699502] hub 1-0:1.0: 2 ports detected
Aug 19 16:23:29 rock-laptop kernel: [   12.801182] ACPI: PCI Interrupt 0000:00:1a.1[B] -> GSI 21 (level, low) -> IRQ 19
Aug 19 16:23:29 rock-laptop kernel: [   12.801194] PCI: Setting latency timer of device 0000:00:1a.1 to 64
Aug 19 16:23:29 rock-laptop kernel: [   12.801198] uhci_hcd 0000:00:1a.1: UHCI Host Controller
Aug 19 16:23:29 rock-laptop kernel: [   12.801219] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
Aug 19 16:23:29 rock-laptop kernel: [   12.801251] uhci_hcd 0000:00:1a.1: irq 19, io base 0x00006f00
Aug 19 16:23:29 rock-laptop kernel: [   12.801352] usb usb2: configuration #1 chosen from 1 choice
Aug 19 16:23:29 rock-laptop kernel: [   12.801372] hub 2-0:1.0: USB hub found
Aug 19 16:23:29 rock-laptop kernel: [   12.801376] hub 2-0:1.0: 2 ports detected
Aug 19 16:23:29 rock-laptop kernel: [   12.905088] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 20 (level, low) -> IRQ 18
Aug 19 16:23:29 rock-laptop kernel: [   12.905101] PCI: Setting latency timer of device 0000:00:1d.0 to 64
Aug 19 16:23:29 rock-laptop kernel: [   12.905105] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Aug 19 16:23:29 rock-laptop kernel: [   12.905126] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 3
Aug 19 16:23:29 rock-laptop kernel: [   12.905155] uhci_hcd 0000:00:1d.0: irq 18, io base 0x00006f80
Aug 19 16:23:29 rock-laptop kernel: [   12.905255] usb usb3: configuration #1 chosen from 1 choice
Aug 19 16:23:29 rock-laptop kernel: [   12.905275] hub 3-0:1.0: USB hub found
Aug 19 16:23:29 rock-laptop kernel: [   12.905279] hub 3-0:1.0: 2 ports detected
Aug 19 16:23:29 rock-laptop kernel: [   12.915902] SCSI subsystem initialized
Aug 19 16:23:29 rock-laptop kernel: [   12.953723] libata version 3.00 loaded.
Aug 19 16:23:29 rock-laptop kernel: [   13.009027] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 21 (level, low) -> IRQ 19
Aug 19 16:23:29 rock-laptop kernel: [   13.009039] PCI: Setting latency timer of device 0000:00:1d.1 to 64
Aug 19 16:23:29 rock-laptop kernel: [   13.009043] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Aug 19 16:23:29 rock-laptop kernel: [   13.009063] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 4
Aug 19 16:23:29 rock-laptop kernel: [   13.009093] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00006f60
Aug 19 16:23:29 rock-laptop kernel: [   13.009194] usb usb4: configuration #1 chosen from 1 choice
Aug 19 16:23:29 rock-laptop kernel: [   13.009214] hub 4-0:1.0: USB hub found
Aug 19 16:23:29 rock-laptop kernel: [   13.009218] hub 4-0:1.0: 2 ports detected
Aug 19 16:23:29 rock-laptop kernel: [   13.041940] usb 1-1: new full speed USB device using uhci_hcd and address 2
Aug 19 16:23:29 rock-laptop kernel: [   13.112980] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 22 (level, low) -> IRQ 20
Aug 19 16:23:29 rock-laptop kernel: [   13.112991] PCI: Setting latency timer of device 0000:00:1d.2 to 64
Aug 19 16:23:29 rock-laptop kernel: [   13.112995] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Aug 19 16:23:29 rock-laptop kernel: [   13.113017] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 5
Aug 19 16:23:29 rock-laptop kernel: [   13.113049] uhci_hcd 0000:00:1d.2: irq 20, io base 0x00006f40
Aug 19 16:23:29 rock-laptop kernel: [   13.113148] usb usb5: configuration #1 chosen from 1 choice
Aug 19 16:23:29 rock-laptop kernel: [   13.113169] hub 5-0:1.0: USB hub found
Aug 19 16:23:29 rock-laptop kernel: [   13.113173] hub 5-0:1.0: 2 ports detected
Aug 19 16:23:29 rock-laptop kernel: [   13.217962] ACPI: PCI Interrupt 0000:00:1a.7[C] -> GSI 22 (level, low) -> IRQ 20
Aug 19 16:23:29 rock-laptop kernel: [   13.217977] PCI: Setting latency timer of device 0000:00:1a.7 to 64
Aug 19 16:23:29 rock-laptop kernel: [   13.217980] ehci_hcd 0000:00:1a.7: EHCI Host Controller
Aug 19 16:23:29 rock-laptop kernel: [   13.218004] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 6
Aug 19 16:23:29 rock-laptop kernel: [   13.221929] ehci_hcd 0000:00:1a.7: debug port 1
Aug 19 16:23:29 rock-laptop kernel: [   13.221936] PCI: cache line size of 32 is not supported by device 0000:00:1a.7
Aug 19 16:23:29 rock-laptop kernel: [   13.221941] ehci_hcd 0000:00:1a.7: irq 20, io mem 0xfed1c400
Aug 19 16:23:29 rock-laptop kernel: [   13.236818] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Aug 19 16:23:29 rock-laptop kernel: [   13.236917] usb usb6: configuration #1 chosen from 1 choice
Aug 19 16:23:29 rock-laptop kernel: [   13.236938] hub 6-0:1.0: USB hub found
Aug 19 16:23:29 rock-laptop kernel: [   13.236943] hub 6-0:1.0: 4 ports detected
Aug 19 16:23:29 rock-laptop kernel: [   13.237115] usb 1-1: unable to read config index 0 descriptor/all
Aug 19 16:23:29 rock-laptop kernel: [   13.237119] usb 1-1: can't read configurations, error -71
Aug 19 16:23:29 rock-laptop kernel: [   13.340908] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 16 (level, low) -> IRQ 16
Aug 19 16:23:29 rock-laptop kernel: [   13.340945] PCI: Setting latency timer of device 0000:00:1f.1 to 64
Aug 19 16:23:29 rock-laptop kernel: [   13.340957] ACPI: PCI interrupt for device 0000:00:1f.1 disabled
Aug 19 16:23:29 rock-laptop kernel: [   13.341000] ahci 0000:00:1f.2: version 3.0
Aug 19 16:23:29 rock-laptop kernel: [   13.341027] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 17 (level, low) -> IRQ 17
Aug 19 16:23:29 rock-laptop kernel: [   13.341077] ahci 0000:00:1f.2: nr_ports (3) and implemented port map (0x5) don't match, using nr_ports
Aug 19 16:23:29 rock-laptop kernel: [   13.341079] ahci 0000:00:1f.2: forcing PORTS_IMPL to 0x7
Aug 19 16:23:29 rock-laptop kernel: [   13.492672] Clocksource tsc unstable (delta = -2197943058 ns)
Aug 19 16:23:29 rock-laptop kernel: [   13.496773] Time: hpet clocksource has been installed.
Aug 19 16:23:29 rock-laptop kernel: [   13.510044] usb 4-1: new low speed USB device using uhci_hcd and address 2
Aug 19 16:23:29 rock-laptop kernel: [   13.532086] usb 4-1: configuration #1 chosen from 1 choice
Aug 19 16:23:29 rock-laptop kernel: [   13.573103] usb 6-1: new high speed USB device using ehci_hcd and address 2
Aug 19 16:23:29 rock-laptop kernel: [   13.706142] usb 6-1: configuration #1 chosen from 1 choice
Aug 19 16:23:29 rock-laptop kernel: [   13.832822] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 3 Gbps 0x7 impl SATA mode
Aug 19 16:23:29 rock-laptop kernel: [   13.832829] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part 
Aug 19 16:23:29 rock-laptop kernel: [   13.832838] PCI: Setting latency timer of device 0000:00:1f.2 to 64
Aug 19 16:23:29 rock-laptop kernel: [   13.833125] scsi0 : ahci
Aug 19 16:23:29 rock-laptop kernel: [   13.833289] scsi1 : ahci
Aug 19 16:23:29 rock-laptop kernel: [   13.833424] scsi2 : ahci
Aug 19 16:23:29 rock-laptop kernel: [   13.833639] ata1: SATA max UDMA/133 abar m2048@0xfebfb800 port 0xfebfb900 irq 219
Aug 19 16:23:29 rock-laptop kernel: [   13.833643] ata2: SATA max UDMA/133 abar m2048@0xfebfb800 port 0xfebfb980 irq 219
Aug 19 16:23:29 rock-laptop kernel: [   13.833646] ata3: SATA max UDMA/133 abar m2048@0xfebfb800 port 0xfebfba00 irq 219
Aug 19 16:23:29 rock-laptop kernel: [   13.860205] usbcore: registered new interface driver hiddev
Aug 19 16:23:29 rock-laptop kernel: [   13.864207] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1d.1/usb4/4-1/4-1:1.0/input/input2
Aug 19 16:23:29 rock-laptop kernel: [   13.868162] input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.1-1
Aug 19 16:23:29 rock-laptop kernel: [   13.868189] usbcore: registered new interface driver usbhid
Aug 19 16:23:29 rock-laptop kernel: [   13.868194] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
Aug 19 16:23:29 rock-laptop kernel: [   13.933031] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Aug 19 16:23:29 rock-laptop kernel: [   13.934053] ata1.00: ATA-8: Hitachi HTS542516K9SA00, BBCOC39P, max UDMA/133
Aug 19 16:23:29 rock-laptop kernel: [   13.934059] ata1.00: 312581808 sectors, multi 8: LBA48 NCQ (depth 31/32)
Aug 19 16:23:29 rock-laptop kernel: [   13.935309] ata1.00: configured for UDMA/133
Aug 19 16:23:29 rock-laptop kernel: [   13.936158] usb 1-2: new full speed USB device using uhci_hcd and address 4
Aug 19 16:23:29 rock-laptop kernel: [   13.954775] usb 1-2: configuration #1 chosen from 1 choice
Aug 19 16:23:29 rock-laptop kernel: [   13.978227] ata2: SATA link down (SStatus 0 SControl 0)
Aug 19 16:23:29 rock-laptop kernel: [   14.000078] ata3: SATA link down (SStatus 0 SControl 300)
Aug 19 16:23:29 rock-laptop kernel: [   14.000328] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS54251 BBCO PQ: 0 ANSI: 5
Aug 19 16:23:29 rock-laptop kernel: [   14.000638] ACPI: PCI Interrupt 0000:03:09.0[A] -> GSI 16 (level, low) -> IRQ 16
Aug 19 16:23:29 rock-laptop kernel: [   14.001926] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 20 (level, low) -> IRQ 18
Aug 19 16:23:29 rock-laptop kernel: [   14.001935] PCI: Setting latency timer of device 0000:00:1d.7 to 64
Aug 19 16:23:29 rock-laptop kernel: [   14.001938] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Aug 19 16:23:29 rock-laptop kernel: [   14.001963] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 7
Aug 19 16:23:29 rock-laptop kernel: [   14.005868] ehci_hcd 0000:00:1d.7: debug port 1
Aug 19 16:23:29 rock-laptop kernel: [   14.005874] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
Aug 19 16:23:29 rock-laptop kernel: [   14.005880] ehci_hcd 0000:00:1d.7: irq 18, io mem 0xfed1c000
Aug 19 16:23:29 rock-laptop kernel: [   14.053318] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[16]  MMIO=[f9bff800-f9bfffff]  Max Packet=[2048]  IR/IT contexts=[4/4]
Aug 19 16:23:29 rock-laptop kernel: [   14.057324] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Aug 19 16:23:29 rock-laptop kernel: [   14.057428] usb usb7: configuration #1 chosen from 1 choice
Aug 19 16:23:29 rock-laptop kernel: [   14.057450] hub 7-0:1.0: USB hub found
Aug 19 16:23:29 rock-laptop kernel: [   14.057455] hub 7-0:1.0: 6 ports detected
Aug 19 16:23:29 rock-laptop kernel: [   14.057529] Driver 'sd' needs updating - please use bus_type methods
Aug 19 16:23:29 rock-laptop kernel: [   14.057593] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
Aug 19 16:23:29 rock-laptop kernel: [   14.057603] sd 0:0:0:0: [sda] Write Protect is off
Aug 19 16:23:29 rock-laptop kernel: [   14.057605] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Aug 19 16:23:29 rock-laptop kernel: [   14.057618] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Aug 19 16:23:29 rock-laptop kernel: [   14.057658] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
Aug 19 16:23:29 rock-laptop kernel: [   14.057667] sd 0:0:0:0: [sda] Write Protect is off
Aug 19 16:23:29 rock-laptop kernel: [   14.057668] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Aug 19 16:23:29 rock-laptop kernel: [   14.057681] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Aug 19 16:23:29 rock-laptop kernel: [   14.057684]  sda: sda1 sda2 sda3 sda4 < sda5 sda6 sda7 sda8 >
Aug 19 16:23:29 rock-laptop kernel: [   14.139723] sd 0:0:0:0: [sda] Attached SCSI disk
Aug 19 16:23:29 rock-laptop kernel: [   14.143698] sd 0:0:0:0: Attached scsi generic sg0 type 0
Aug 19 16:23:29 rock-laptop kernel: [   14.152798] usb 4-1: USB disconnect, address 2
Aug 19 16:23:29 rock-laptop kernel: [   14.163594] ata_piix 0000:00:1f.1: version 2.12
Aug 19 16:23:29 rock-laptop kernel: [   14.163615] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 16 (level, low) -> IRQ 16
Aug 19 16:23:29 rock-laptop kernel: [   14.163652] PCI: Setting latency timer of device 0000:00:1f.1 to 64
Aug 19 16:23:29 rock-laptop kernel: [   14.164154] scsi3 : ata_piix
Aug 19 16:23:29 rock-laptop kernel: [   14.164523] scsi4 : ata_piix
Aug 19 16:23:29 rock-laptop kernel: [   14.165056] ata4: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x6fa0 irq 14
Aug 19 16:23:29 rock-laptop kernel: [   14.165059] ata5: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x6fa8 irq 15
Aug 19 16:23:29 rock-laptop kernel: [   14.485188] ata4.00: ATAPI: Optiarc DVD+/-RW AD-7640A, JD05, max UDMA/33
Aug 19 16:23:29 rock-laptop kernel: [   14.600475] ata4.00: configured for UDMA/33
Aug 19 16:23:29 rock-laptop kernel: [   14.600576] ata5: port disabled. ignoring.
Aug 19 16:23:29 rock-laptop kernel: [   14.601484] scsi 3:0:0:0: CD-ROM            Optiarc  DVD+-RW AD-7640A JD05 PQ: 0 ANSI: 5
Aug 19 16:23:29 rock-laptop kernel: [   14.601603] scsi 3:0:0:0: Attached scsi generic sg1 type 5
Aug 19 16:23:29 rock-laptop kernel: [   14.607138] Driver 'sr' needs updating - please use bus_type methods
Aug 19 16:23:29 rock-laptop kernel: [   14.613518] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda caddy
Aug 19 16:23:29 rock-laptop kernel: [   14.613523] Uniform CD-ROM driver Revision: 3.20
Aug 19 16:23:29 rock-laptop kernel: [   14.613596] sr 3:0:0:0: Attached scsi CD-ROM sr0
Aug 19 16:23:29 rock-laptop kernel: [   14.674248] usb 4-1: new low speed USB device using uhci_hcd and address 3
Aug 19 16:23:29 rock-laptop kernel: [   14.692220] usb 4-1: configuration #1 chosen from 1 choice
Aug 19 16:23:29 rock-laptop kernel: [   14.705030] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1d.1/usb4/4-1/4-1:1.0/input/input3
Aug 19 16:23:29 rock-laptop kernel: [   14.716256] input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.1-1
Aug 19 16:23:29 rock-laptop kernel: [   14.734546] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[474fc00012dae470]
Aug 19 16:23:29 rock-laptop kernel: [   15.196618] kjournald starting.  Commit interval 5 seconds
Aug 19 16:23:29 rock-laptop kernel: [   15.196626] EXT3-fs: mounted filesystem with ordered data mode.
Aug 19 16:23:29 rock-laptop kernel: [   23.715325] input: PC Speaker as /devices/platform/pcspkr/input/input4
Aug 19 16:23:29 rock-laptop kernel: [   23.864093] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Aug 19 16:23:29 rock-laptop kernel: [   23.887491] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Aug 19 16:23:29 rock-laptop kernel: [   23.956055] iTCO_vendor_support: vendor-support=0
Aug 19 16:23:29 rock-laptop kernel: [   23.992035] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
Aug 19 16:23:29 rock-laptop kernel: [   24.031281] ACPI: AC Adapter [AC] (on-line)
Aug 19 16:23:29 rock-laptop kernel: [   24.055992] Linux agpgart interface v0.102
Aug 19 16:23:29 rock-laptop kernel: [   24.095329] input: Lid Switch as /devices/virtual/input/input5
Aug 19 16:23:29 rock-laptop kernel: [   24.264880] ACPI: Lid Switch [LID]
Aug 19 16:23:29 rock-laptop kernel: [   24.264933] input: Power Button (CM) as /devices/virtual/input/input6
Aug 19 16:23:29 rock-laptop kernel: [   24.323810] ACPI: Power Button (CM) [PBTN]
Aug 19 16:23:29 rock-laptop kernel: [   24.323868] input: Sleep Button (CM) as /devices/virtual/input/input7
Aug 19 16:23:29 rock-laptop kernel: [   24.387759] ACPI: Sleep Button (CM) [SBTN]
Aug 19 16:23:29 rock-laptop kernel: [   24.387909] ACPI: Battery Slot [BAT0] (battery absent)
Aug 19 16:23:29 rock-laptop kernel: [   24.387938] ACPI: WMI-Acer: Mapper loaded
Aug 19 16:23:29 rock-laptop kernel: [   24.940470] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:2e/LNXVIDEO:00/input/input8
Aug 19 16:23:29 rock-laptop kernel: [   24.995419] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
Aug 19 16:23:29 rock-laptop kernel: [   25.103604] ACPI: PCI Interrupt 0000:09:00.0[A] -> GSI 16 (level, low) -> IRQ 16
Aug 19 16:23:29 rock-laptop kernel: [   25.103619] PCI: Setting latency timer of device 0000:09:00.0 to 64
Aug 19 16:23:29 rock-laptop kernel: [   25.103659] sky2 0000:09:00.0: v1.20 addr 0xf9ffc000 irq 16 Yukon-FE+ (0xb8) rev 0
Aug 19 16:23:29 rock-laptop kernel: [   25.110063] sky2 eth0: addr 00:1d:09:56:15:d6
Aug 19 16:23:29 rock-laptop kernel: [   25.178031] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
Aug 19 16:23:29 rock-laptop kernel: [   25.276308] input: PS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input9
Aug 19 16:23:29 rock-laptop kernel: [   25.281063] sdhci: Secure Digital Host Controller Interface driver
Aug 19 16:23:29 rock-laptop kernel: [   25.281067] sdhci: Copyright(c) Pierre Ossman
Aug 19 16:23:29 rock-laptop kernel: [   25.288036] sdhci: SDHCI controller found at 0000:03:09.1 [1180:0822] (rev 22)
Aug 19 16:23:29 rock-laptop kernel: [   25.288066] ACPI: PCI Interrupt 0000:03:09.1[B] -> GSI 18 (level, low) -> IRQ 21
Aug 19 16:23:29 rock-laptop kernel: [   25.291108] mmc0: SDHCI at 0xf9bff500 irq 21 DMA
Aug 19 16:23:29 rock-laptop kernel: [   25.301887] usbcore: registered new interface driver ndiswrapper
Aug 19 16:23:29 rock-laptop kernel: [   25.334819] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
Aug 19 16:23:29 rock-laptop kernel: [   25.334833] iTCO_wdt: Found a ICH8M TCO device (Version=2, TCOBASE=0x1060)
Aug 19 16:23:29 rock-laptop kernel: [   25.334874] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
Aug 19 16:23:29 rock-laptop kernel: [   25.482212] mmc0: new high speed SD card at address 0002
Aug 19 16:23:29 rock-laptop kernel: [   26.037681] sky2 eth0: enabling interface
Aug 19 16:23:29 rock-laptop kernel: [   26.119257] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
Aug 19 16:23:29 rock-laptop kernel: [   26.119269] PCI: Setting latency timer of device 0000:01:00.0 to 64
Aug 19 16:23:29 rock-laptop kernel: [   26.119394] NVRM: loading NVIDIA UNIX x86 Kernel Module  173.14.12  Thu Jul 17 18:11:36 PDT 2008
Aug 19 16:23:29 rock-laptop kernel: [   26.189656] Linux video capture interface: v2.00
Aug 19 16:23:29 rock-laptop kernel: [   26.231995] mmcblk0: mmc0:0002       976896KiB 
Aug 19 16:23:29 rock-laptop kernel: [   26.232024]  mmcblk0: p1
Aug 19 16:23:29 rock-laptop kernel: [   26.385442] uvcvideo: Found UVC 1.00 device Laptop Integrated Webcam (05a9:2640)
Aug 19 16:23:29 rock-laptop kernel: [   26.385841] uvcvideo: Failed to query (135) UVC control 1 (unit 0) : -32 (exp. 26).
Aug 19 16:23:29 rock-laptop kernel: [   26.443073] usbcore: registered new interface driver uvcvideo
Aug 19 16:23:29 rock-laptop kernel: [   26.443080] USB Video Class driver (v0.1.0)
Aug 19 16:23:29 rock-laptop kernel: [   26.481865] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 21 (level, low) -> IRQ 19
Aug 19 16:23:29 rock-laptop kernel: [   26.481885] PCI: Setting latency timer of device 0000:00:1b.0 to 64
Aug 19 16:23:29 rock-laptop kernel: [   26.919642] lp: driver loaded but no devices found
Aug 19 16:23:29 rock-laptop kernel: [   27.628403] NET: Registered protocol family 17
Aug 19 16:23:29 rock-laptop kernel: [   28.058423] EXT3 FS on sda6, internal journal
Aug 19 16:23:29 rock-laptop kernel: [   29.310722] ip_tables: (C) 2000-2006 Netfilter Core Team
Aug 19 16:23:29 rock-laptop kernel: [   29.433463] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.25
Aug 19 16:23:29 rock-laptop kernel: [   29.433467] iwl3945: Copyright(c) 2003-2007 Intel Corporation
Aug 19 16:23:29 rock-laptop kernel: [   29.433606] ACPI: PCI Interrupt 0000:0b:00.0[A] -> GSI 17 (level, low) -> IRQ 17
Aug 19 16:23:29 rock-laptop kernel: [   29.433621] PCI: Setting latency timer of device 0000:0b:00.0 to 64
Aug 19 16:23:29 rock-laptop kernel: [   29.433640] iwl3945: Detected Intel PRO/Wireless 3945ABG Network Connection
Aug 19 16:23:29 rock-laptop kernel: [   29.495311] wmaster0: Selected rate control algorithm 'iwl-3945-rs'
Aug 19 16:23:29 rock-laptop kernel: [   29.595048] ACPI: PCI interrupt for device 0000:0b:00.0 disabled
Aug 19 16:23:29 rock-laptop kernel: [   29.595223] ACPI: PCI Interrupt 0000:0b:00.0[A] -> GSI 17 (level, low) -> IRQ 17
Aug 19 16:23:29 rock-laptop kernel: [   29.595377] PM: Writing back config space on device 0000:0b:00.0 at offset 1 (was 100102, writing 100106)
Aug 19 16:23:29 rock-laptop kernel: [   29.683413] iwl3945: Tunable channels: 13 802.11bg, 23 802.11a channels
Aug 19 16:23:29 rock-laptop kernel: [   29.685570] Registered led device: iwl-phy0:RX
Aug 19 16:23:29 rock-laptop kernel: [   29.685600] Registered led device: iwl-phy0:TX
[B]Aug 19 16:23:29 rock-laptop kernel: [   31.262684] iwl3945: Microcode SW error detected.  Restarting 0x82000008.
Aug 19 16:23:29 rock-laptop kernel: [   31.262785] iwl3945: Error Reply type 0x00000005 cmd REPLY_TX (0x1C) seq 0x000B ser 0x0000004B
Aug 19 16:23:29 rock-laptop kernel: [   31.262892] iwl3945: Error setting new configuration (-5).
Aug 19 16:23:29 rock-laptop kernel: [   32.257990] iwl3945: Can't stop Rx DMA.
Aug 19 16:23:29 rock-laptop kernel: [   32.411885] Registered led device: iwl-phy0:RX
Aug 19 16:23:29 rock-laptop kernel: [   32.411915] Registered led device: iwl-phy0:TX
Aug 19 16:23:29 rock-laptop kernel: [   32.685828] iwl3945: Microcode SW error detected.  Restarting 0x82000008.
Aug 19 16:23:29 rock-laptop kernel: [   32.685918] iwl3945: Error Reply type 0x00000005 cmd REPLY_TX (0x1C) seq 0x0000 ser 0x0000004B
Aug 19 16:23:29 rock-laptop kernel: [   32.686030] iwl3945: Error setting new configuration (-5).
Aug 19 16:23:29 rock-laptop kernel: [   33.679595] iwl3945: Can't stop Rx DMA.
Aug 19 16:23:29 rock-laptop kernel: [   33.830956] Registered led device: iwl-phy0:RX
Aug 19 16:23:29 rock-laptop kernel: [   33.830986] Registered led device: iwl-phy0:TX
Aug 19 16:23:29 rock-laptop kernel: [   34.204901] iwl3945: Microcode SW error detected.  Restarting 0x82000008.
Aug 19 16:23:29 rock-laptop kernel: [   34.204992] iwl3945: Error Reply type 0x00000005 cmd REPLY_TX (0x1C) seq 0x0000 ser 0x0000004B
Aug 19 16:23:29 rock-laptop kernel: [   34.205102] iwl3945: Error setting new configuration (-5).
Aug 19 16:23:29 rock-laptop kernel: [   35.197533] iwl3945: Can't stop Rx DMA.
Aug 19 16:23:29 rock-laptop kernel: [   35.350044] Registered led device: iwl-phy0:RX
Aug 19 16:23:29 rock-laptop kernel: [   35.350075] Registered led device: iwl-phy0:TX
Aug 19 16:23:29 rock-laptop kernel: [   35.723979] iwl3945: Microcode SW error detected.  Restarting 0x82000008.
Aug 19 16:23:29 rock-laptop kernel: [   35.724071] iwl3945: Error Reply type 0x00000005 cmd REPLY_TX (0x1C) seq 0x0000 ser 0x0000004B
Aug 19 16:23:29 rock-laptop kernel: [   35.724181] iwl3945: Error setting new configuration (-5).
Aug 19 16:23:29 rock-laptop kernel: [   36.716611] iwl3945: Can't stop Rx DMA.
Aug 19 16:23:29 rock-laptop kernel: [   36.869261] Registered led device: iwl-phy0:RX
Aug 19 16:23:29 rock-laptop kernel: [   36.869290] Registered led device: iwl-phy0:TX
Aug 19 16:23:29 rock-laptop kernel: [   40.210451] wlan0: Initial auth_alg=0
Aug 19 16:23:29 rock-laptop kernel: [   40.210457] wlan0: authenticate with AP 00:17:3f:de:62:31
Aug 19 16:23:29 rock-laptop kernel: [   40.409010] wlan0: authenticate with AP 00:17:3f:de:62:31
Aug 19 16:23:29 rock-laptop kernel: [   40.410808] wlan0: RX authentication from 00:17:3f:de:62:31 (alg=0 transaction=2 status=0)
Aug 19 16:23:29 rock-laptop kernel: [   40.410813] wlan0: authenticated
Aug 19 16:23:29 rock-laptop kernel: [   40.410816] wlan0: associate with AP 00:17:3f:de:62:31
Aug 19 16:23:29 rock-laptop kernel: [   40.420168] wlan0: RX AssocResp from 00:17:3f:de:62:31 (capab=0x431 status=0 aid=10)
Aug 19 16:23:29 rock-laptop kernel: [   40.420172] wlan0: associated
[/B]
Aug 19 16:23:29 rock-laptop kernel: [   43.448820] NET: Registered protocol family 10
Aug 19 16:23:29 rock-laptop kernel: [   43.449035] lo: Disabled Privacy Extensions
Aug 19 16:23:29 rock-laptop kernel: [   43.449378] ADDRCONF(NETDEV_UP): eth0: link is not ready
Aug 19 16:23:29 rock-laptop kernel: [   43.753781] No dock devices found.
Aug 19 16:23:29 rock-laptop avahi-daemon[5522]: Found user 'avahi' (UID 109) and group 'avahi' (GID 120).
Aug 19 16:23:29 rock-laptop avahi-daemon[5522]: Successfully dropped root privileges.
Aug 19 16:23:29 rock-laptop avahi-daemon[5522]: avahi-daemon 0.6.22 starting up.
Aug 19 16:23:29 rock-laptop avahi-daemon[5522]: Successfully called chroot().
Aug 19 16:23:29 rock-laptop avahi-daemon[5522]: Successfully dropped remaining capabilities.
Aug 19 16:23:29 rock-laptop avahi-daemon[5522]: No service file found in /etc/avahi/services.
Aug 19 16:23:29 rock-laptop avahi-daemon[5522]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.2.3.
Aug 19 16:23:29 rock-laptop avahi-daemon[5522]: New relevant interface wlan0.IPv4 for mDNS.
Aug 19 16:23:29 rock-laptop avahi-daemon[5522]: Network interface enumeration completed.
Aug 19 16:23:29 rock-laptop avahi-daemon[5522]: Registering new address record for fe80::21f:3cff:fe7e:9afe on wlan0.*.
Aug 19 16:23:29 rock-laptop avahi-daemon[5522]: Registering new address record for 192.168.2.3 on wlan0.IPv4.
Aug 19 16:23:29 rock-laptop avahi-daemon[5522]: Registering HINFO record with values 'I686'/'LINUX'.
Aug 19 16:23:29 rock-laptop kernel: [   44.834943] apm: BIOS not found.
Aug 19 16:23:29 rock-laptop kernel: [   44.961890] ppdev: user-space parallel port driver
Aug 19 16:23:30 rock-laptop kernel: [   45.065067] audit(1219159410.027:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5565 profile="/usr/sbin/cupsd" namespace="default"
Aug 19 16:23:30 rock-laptop avahi-daemon[5522]: Server startup complete. Host name is rock-laptop.local. Local service cookie is 516814728.
Aug 19 16:23:31 rock-laptop dhcdbd: Started up.
Aug 19 16:23:32 rock-laptop hcid[5895]: Bluetooth HCI daemon
Aug 19 16:23:32 rock-laptop kernel: [   47.049261] Bluetooth: Core ver 2.11
Aug 19 16:23:32 rock-laptop kernel: [   47.049654] NET: Registered protocol family 31
Aug 19 16:23:32 rock-laptop kernel: [   47.049659] Bluetooth: HCI device and connection manager initialized
Aug 19 16:23:32 rock-laptop kernel: [   47.049664] Bluetooth: HCI socket layer initialized
Aug 19 16:23:32 rock-laptop hcid[5895]: Starting SDP server
Aug 19 16:23:32 rock-laptop kernel: [   47.066385] Bluetooth: L2CAP ver 2.9
Aug 19 16:23:32 rock-laptop hcid[5895]: Created local server at unix:abstract=/var/run/dbus-CQa5MC8iFb,guid=d7a6ae8235c8c7ca796a66e548aae574
Aug 19 16:23:32 rock-laptop kernel: [   47.066392] Bluetooth: L2CAP socket layer initialized
Aug 19 16:23:32 rock-laptop audio[5913]: Bluetooth Audio daemon
Aug 19 16:23:32 rock-laptop input[5914]: Bluetooth Input daemon
Aug 19 16:23:32 rock-laptop input[5914]: Registered input manager path:/org/bluez/input
Aug 19 16:23:32 rock-laptop audio[5913]: Unix socket created: 5
Aug 19 16:23:32 rock-laptop audio[5913]: audio.conf: Key file does not have key 'Enable'
Aug 19 16:23:32 rock-laptop audio[5913]: audio.conf: Key file does not have key 'Disable'
Aug 19 16:23:32 rock-laptop kernel: [   47.127533] Bluetooth: RFCOMM socket layer initialized
Aug 19 16:23:32 rock-laptop kernel: [   47.127553] Bluetooth: RFCOMM TTY layer initialized
Aug 19 16:23:32 rock-laptop kernel: [   47.127557] Bluetooth: RFCOMM ver 1.8
Aug 19 16:23:32 rock-laptop audio[5913]: add_service_record: got record id 0x10000
Aug 19 16:23:32 rock-laptop audio[5913]: audio.conf: Key file does not have key 'Disable'
Aug 19 16:23:32 rock-laptop audio[5913]: audio.conf: Key file does not have group 'A2DP'
Aug 19 16:23:32 rock-laptop last message repeated 3 times
Aug 19 16:23:32 rock-laptop audio[5913]: SEP 0x806d790 registered: type:0 codec:0 seid:1
Aug 19 16:23:32 rock-laptop audio[5913]: add_service_record: got record id 0x10001
Aug 19 16:23:32 rock-laptop audio[5913]: add_service_record: got record id 0x10002
Aug 19 16:23:32 rock-laptop audio[5913]: add_service_record: got record id 0x10003
Aug 19 16:23:32 rock-laptop audio[5913]: Registered manager path:/org/bluez/audio
Aug 19 16:23:33 rock-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Aug 19 16:23:36 rock-laptop anacron[5985]: Anacron 2.3 started on 2008-08-19
Aug 19 16:23:36 rock-laptop anacron[5985]: Normal exit (0 jobs run)
Aug 19 16:23:36 rock-laptop /usr/sbin/cron[6018]: (CRON) INFO (pidfile fd = 3)
Aug 19 16:23:36 rock-laptop /usr/sbin/cron[6019]: (CRON) STARTUP (fork ok)
Aug 19 16:23:36 rock-laptop /usr/sbin/cron[6019]: (CRON) INFO (Running @reboot jobs)
[B]Aug 19 16:23:38 rock-laptop kernel: [   49.681708] iwl3945: Microcode SW error detected.  Restarting 0x82000008.
Aug 19 16:23:38 rock-laptop kernel: [   49.681718] iwl3945: Error Reply type 0x00000005 cmd REPLY_TX (0x1C) seq 0x000E ser 0x0000004B
Aug 19 16:23:39 rock-laptop kernel: [   49.682077] iwl3945: Error clearing ASSOC_MSK on current configuration (-5).
Aug 19 16:23:39 rock-laptop kernel: [   50.674580] iwl3945: Can't stop Rx DMA.
Aug 19 16:23:39 rock-laptop kernel: [   50.674852] wlan0: no IPv6 routers present
Aug 19 16:23:39 rock-laptop kernel: [   51.092227] Registered led device: iwl-phy0:RX
Aug 19 16:23:39 rock-laptop kernel: [   51.092260] Registered led device: iwl-phy0:TX
Aug 19 16:23:39 rock-laptop kernel: [   51.320757] iwl3945: Microcode SW error detected.  Restarting 0x82000008.
Aug 19 16:23:39 rock-laptop kernel: [   51.320770] iwl3945: Error Reply type 0x00000005 cmd REPLY_TX (0x1C) seq 0x0000 ser 0x0000004B
Aug 19 16:23:40 rock-laptop kernel: [   51.321066] iwl3945: Error clearing ASSOC_MSK on current configuration (-5).
Aug 19 16:23:40 rock-laptop kernel: [   52.314600] iwl3945: Can't stop Rx DMA.
Aug 19 16:23:40 rock-laptop kernel: [   52.470707] Registered led device: iwl-phy0:RX
Aug 19 16:23:40 rock-laptop kernel: [   52.470741] Registered led device: iwl-phy0:TX
Aug 19 16:23:41 rock-laptop dhclient: No DHCPOFFERS received.
Aug 19 16:23:41 rock-laptop dhclient: No working leases in persistent database - sleeping.
[/B]Aug 19 16:23:41 rock-laptop avahi-autoipd(eth0)[6146]: Found user 'avahi-autoipd' (UID 105) and group 'avahi-autoipd' (GID 113).
Aug 19 16:23:41 rock-laptop avahi-autoipd(eth0)[6146]: Successfully called chroot().
Aug 19 16:23:41 rock-laptop avahi-autoipd(eth0)[6146]: Successfully dropped root privileges.
Aug 19 16:23:41 rock-laptop avahi-autoipd(eth0)[6146]: Starting with address 169.254.5.180
Aug 19 16:23:41 rock-laptop kernel: [   52.584322] iwl3945: Microcode SW error detected.  Restarting 0x82000008.
Aug 19 16:23:41 rock-laptop kernel: [   52.584344] iwl3945: Error Reply type 0x00000005 cmd REPLY_TX (0x1C) seq 0x0000 ser 0x0000004B
Aug 19 16:23:41 rock-laptop kernel: [   52.584365] iwl3945: Error clearing ASSOC_MSK on current configuration (-5).
Aug 19 16:23:42 rock-laptop kernel: [   53.577597] iwl3945: Can't stop Rx DMA.
Aug 19 16:23:42 rock-laptop kernel: [   53.712126] Registered led device: iwl-phy0:RX
Aug 19 16:23:42 rock-laptop kernel: [   53.712161] Registered led device: iwl-phy0:TX
Aug 19 16:23:42 rock-laptop kernel: [   53.800273] iwl3945: Microcode SW error detected.  Restarting 0x82000008.
Aug 19 16:23:42 rock-laptop kernel: [   53.800293] iwl3945: Error Reply type 0x00000005 cmd REPLY_TX (0x1C) seq 0x0000 ser 0x0000004B
Aug 19 16:23:42 rock-laptop kernel: [   53.800775] iwl3945: Error clearing ASSOC_MSK on current configuration (-5).
Aug 19 16:23:43 rock-laptop kernel: [   54.793312] iwl3945: Can't stop Rx DMA.
Aug 19 16:23:43 rock-laptop kernel: [   54.939302] Registered led device: iwl-phy0:RX
Aug 19 16:23:43 rock-laptop kernel: [   54.939336] Registered led device: iwl-phy0:TX
Aug 19 16:23:46 rock-laptop avahi-autoipd(eth0)[6146]: Callout BIND, address 169.254.5.180 on interface eth0
Aug 19 16:23:46 rock-laptop avahi-daemon[5522]: Joining mDNS multicast group on interface eth0.IPv4 with address 169.254.5.180.
Aug 19 16:23:46 rock-laptop avahi-daemon[5522]: New relevant interface eth0.IPv4 for mDNS.
Aug 19 16:23:46 rock-laptop avahi-daemon[5522]: Registering new address record for 169.254.5.180 on eth0.IPv4.
Aug 19 16:23:47 rock-laptop kernel: [   55.942330] ACPI: PCI interrupt for device 0000:0b:00.0 disabled
Aug 19 16:23:47 rock-laptop avahi-daemon[5522]: Interface wlan0.IPv4 no longer relevant for mDNS.
Aug 19 16:23:47 rock-laptop avahi-daemon[5522]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.2.3.
Aug 19 16:23:47 rock-laptop dhclient: receive_packet failed on wlan0: Network is down
Aug 19 16:23:47 rock-laptop avahi-daemon[5522]: Withdrawing address record for fe80::21f:3cff:fe7e:9afe on wlan0.
Aug 19 16:23:47 rock-laptop avahi-daemon[5522]: Withdrawing address record for 192.168.2.3 on wlan0.
Aug 19 16:23:47 rock-laptop kernel: [   55.959819] ACPI: PCI Interrupt 0000:0b:00.0[A] -> GSI 17 (level, low) -> IRQ 17
Aug 19 16:23:47 rock-laptop kernel: [   55.959968] PM: Writing back config space on device 0000:0b:00.0 at offset 1 (was 100102, writing 100106)
Aug 19 16:23:47 rock-laptop kernel: [   55.987097] Registered led device: iwl-phy0:RX
Aug 19 16:23:47 rock-laptop kernel: [   55.987131] Registered led device: iwl-phy0:TX
Aug 19 16:23:47 rock-laptop kernel: [   55.994139] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Aug 19 16:23:47 rock-laptop kernel: [   56.135158] wlan0: Initial auth_alg=0
Aug 19 16:23:47 rock-laptop kernel: [   56.135169] wlan0: authenticate with AP 00:17:3f:de:62:31
Aug 19 16:23:47 rock-laptop dhclient: Internet Systems Consortium DHCP Client V3.0.6
Aug 19 16:23:47 rock-laptop dhclient: Copyright 2004-2007 Internet Systems Consortium.
Aug 19 16:23:47 rock-laptop dhclient: All rights reserved.
Aug 19 16:23:47 rock-laptop dhclient: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Aug 19 16:23:47 rock-laptop dhclient: 
Aug 19 16:23:47 rock-laptop dhclient: wmaster0: unknown hardware address type 801
Aug 19 16:23:47 rock-laptop kernel: [   56.295863] wlan0: authenticate with AP 00:17:3f:de:62:31
Aug 19 16:23:47 rock-laptop kernel: [   56.297732] wlan0: RX authentication from 00:17:3f:de:62:31 (alg=0 transaction=2 status=0)
Aug 19 16:23:47 rock-laptop kernel: [   56.297739] wlan0: authenticated
Aug 19 16:23:47 rock-laptop kernel: [   56.297742] wlan0: associate with AP 00:17:3f:de:62:31
Aug 19 16:23:47 rock-laptop kernel: [   56.307020] wlan0: RX ReassocResp from 00:17:3f:de:62:31 (capab=0x431 status=0 aid=10)
Aug 19 16:23:47 rock-laptop kernel: [   56.307026] wlan0: associated
Aug 19 16:23:47 rock-laptop kernel: [   56.310831] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Aug 19 16:23:48 rock-laptop dhclient: wmaster0: unknown hardware address type 801
Aug 19 16:23:48 rock-laptop dhclient: Listening on LPF/wlan0/00:1f:3c:7e:9a:fe
Aug 19 16:23:48 rock-laptop dhclient: Sending on   LPF/wlan0/00:1f:3c:7e:9a:fe
Aug 19 16:23:48 rock-laptop dhclient: Sending on   Socket/fallback
Aug 19 16:23:48 rock-laptop dhclient: DHCPREQUEST of 192.168.2.3 on wlan0 to 255.255.255.255 port 67
Aug 19 16:23:48 rock-laptop dhclient: DHCPACK of 192.168.2.3 from 192.168.2.1
Aug 19 16:23:48 rock-laptop avahi-daemon[5522]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.2.3.
Aug 19 16:23:48 rock-laptop avahi-daemon[5522]: New relevant interface wlan0.IPv4 for mDNS.
Aug 19 16:23:48 rock-laptop avahi-daemon[5522]: Registering new address record for 192.168.2.3 on wlan0.IPv4.
Aug 19 16:23:48 rock-laptop dhclient: bound to 192.168.2.3 -- renewal in 928324219 seconds.
Aug 19 16:23:49 rock-laptop avahi-daemon[5522]: Registering new address record for fe80::21f:3cff:fe7e:9afe on wlan0.*.
Aug 19 16:23:50 rock-laptop kernel: [   57.887749] input: Virtual ThinkFinger Keyboard as /devices/virtual/input/input10
Aug 19 16:23:50 rock-laptop avahi-autoipd(eth0)[6146]: Successfully claimed IP address 169.254.5.180
Aug 19 16:23:58 rock-laptop kernel: [   62.138888] wlan0: no IPv6 routers present
Aug 19 16:24:01 rock-laptop anacron[6444]: Anacron 2.3 started on 2008-08-19
Aug 19 16:24:01 rock-laptop anacron[6444]: Normal exit (0 jobs run)
Aug 19 16:24:01 rock-laptop kernel: [   64.667846] CPU0 attaching NULL sched-domain.
Aug 19 16:24:01 rock-laptop kernel: [   64.667856] CPU1 attaching NULL sched-domain.
Aug 19 16:24:01 rock-laptop kernel: [   64.682239] CPU0 attaching sched-domain:
Aug 19 16:24:01 rock-laptop kernel: [   64.682248]  domain 0: span 03
Aug 19 16:24:01 rock-laptop kernel: [   64.682252]   groups: 01 02
Aug 19 16:24:01 rock-laptop kernel: [   64.682257] CPU1 attaching sched-domain:
Aug 19 16:24:01 rock-laptop kernel: [   64.682260]  domain 0: span 03
Aug 19 16:24:01 rock-laptop kernel: [   64.682263]   groups: 02 01
Aug 19 16:24:04 rock-laptop hald: mounted /dev/mmcblk0p1 on behalf of uid 1000

```

---

### Post by rocklee on 2008-08-19
2. Cold booting Ubuntu.

Here, I've listed in bold the results of the wireless card, which is a lot shorter.

```

Aug 19 16:07:18 rock-laptop syslogd 1.5.0#1ubuntu1: restart.
Aug 19 16:07:18 rock-laptop kernel: Inspecting /boot/System.map-2.6.24-19-generic
Aug 19 16:07:18 rock-laptop kernel: Loaded 27884 symbols from /boot/System.map-2.6.24-19-generic.
Aug 19 16:07:18 rock-laptop kernel: Symbols match kernel version 2.6.24.
Aug 19 16:07:18 rock-laptop kernel: Loaded 39067 symbols from 103 modules.
Aug 19 16:07:18 rock-laptop kernel: [    0.000000] Initializing cgroup subsys cpuset
Aug 19 16:07:18 rock-laptop kernel: [    0.000000] Initializing cgroup subsys cpu
Aug 19 16:07:18 rock-laptop kernel: [    0.000000] Linux version 2.6.24-19-generic (buildd@terranova) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Fri Jul 11 23:41:49 UTC 2008 (Ubuntu 2.6.24-19.36-generic)
Aug 19 16:07:18 rock-laptop kernel: [    0.000000] BIOS-provided physical RAM map:
Aug 19 16:07:18 rock-laptop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
Aug 19 16:07:18 rock-laptop kernel: [    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
Aug 19 16:07:18 rock-laptop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000007fe72000 (usable)
Aug 19 16:07:18 rock-laptop kernel: [    0.000000]  BIOS-e820: 000000007fe72000 - 0000000080000000 (reserved)
Aug 19 16:07:18 rock-laptop kernel: [    0.000000]  BIOS-e820: 00000000f4000000 - 00000000f8000000 (reserved)
Aug 19 16:07:18 rock-laptop kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
Aug 19 16:07:18 rock-laptop kernel: [    0.000000]  BIOS-e820: 00000000fed18000 - 00000000fed1c000 (reserved)
Aug 19 16:07:18 rock-laptop kernel: [    0.000000]  BIOS-e820: 00000000fed20000 - 00000000fed90000 (reserved)
Aug 19 16:07:18 rock-laptop kernel: [    0.000000]  BIOS-e820: 00000000feda0000 - 00000000feda6000 (reserved)
Aug 19 16:07:18 rock-laptop kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee10000 (reserved)
Aug 19 16:07:18 rock-laptop kernel: [    0.000000]  BIOS-e820: 00000000ffe00000 - 0000000100000000 (reserved)
Aug 19 16:07:18 rock-laptop kernel: [    0.000000] 1150MB HIGHMEM available.
Aug 19 16:07:18 rock-laptop kernel: [    0.000000] 896MB LOWMEM available.
Aug 19 16:07:18 rock-laptop kernel: [    0.000000] Entering add_active_range(0, 0, 523890) 0 entries of 256 used
Aug 19 16:07:19 rock-laptop kernel: [    0.000000] Zone PFN ranges:
Aug 19 16:07:19 rock-laptop kernel: [    0.000000]   DMA             0 ->     4096
Aug 19 16:07:19 rock-laptop kernel: [    0.000000]   Normal       4096 ->   229376
Aug 19 16:07:19 rock-laptop kernel: [    0.000000]   HighMem    229376 ->   523890
Aug 19 16:07:19 rock-laptop kernel: [    0.000000] Movable zone start PFN for each node
Aug 19 16:07:19 rock-laptop kernel: [    0.000000] early_node_map[1] active PFN ranges
Aug 19 16:07:19 rock-laptop kernel: [    0.000000]     0:        0 ->   523890
Aug 19 16:07:19 rock-laptop kernel: [    0.000000] On node 0 totalpages: 523890
Aug 19 16:07:19 rock-laptop kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Aug 19 16:07:19 rock-laptop kernel: [    0.000000]   DMA zone: 0 pages reserved
Aug 19 16:07:19 rock-laptop kernel: [    0.000000]   DMA zone: 4064 pages, LIFO batch:0
Aug 19 16:07:19 rock-laptop kernel: [    0.000000]   Normal zone: 1760 pages used for memmap
Aug 19 16:07:19 rock-laptop kernel: [    0.000000]   Normal zone: 223520 pages, LIFO batch:31
Aug 19 16:07:19 rock-laptop kernel: [    0.000000]   HighMem zone: 2300 pages used for memmap
Aug 19 16:07:19 rock-laptop kernel: [    0.000000]   HighMem zone: 292214 pages, LIFO batch:31
Aug 19 16:07:19 rock-laptop kernel: [    0.000000]   Movable zone: 0 pages used for memmap
Aug 19 16:07:19 rock-laptop kernel: [    0.000000] DMI 2.4 present.
Aug 19 16:07:19 rock-laptop kernel: [    0.000000] ACPI: RSDP signature @ 0xC00FBC80 checksum 0
Aug 19 16:07:19 rock-laptop kernel: [    0.000000] ACPI: RSDP 000FBC80, 0024 (r2 DELL  )
Aug 19 16:07:19 rock-laptop kernel: [    0.000000] ACPI: XSDT 7FE73A00, 0064 (r1 DELL    M08     27D80313 ASL        61)
Aug 19 16:07:19 rock-laptop kernel: [    0.000000] ACPI: FACP 7FE7389C, 00F4 (r4 DELL    M08     27D80313 ASL        61)
Aug 19 16:07:19 rock-laptop kernel: [    0.000000] ACPI: DSDT 7FE74000, 4BD7 (r2 INT430 SYSFexxx     1001 INTL 20050624)
Aug 19 16:07:19 rock-laptop kernel: [    0.000000] ACPI: FACS 7FE82800, 0040
Aug 19 16:07:19 rock-laptop kernel: [    0.000000] ACPI: HPET 7FE73B00, 0038 (r1 DELL    M08            1 ASL        61)
Aug 19 16:07:19 rock-laptop kernel: [    0.000000] ACPI: APIC 7FE73C00, 0068 (r1 DELL    M08     27D80313 ASL        47)
Aug 19 16:07:19 rock-laptop kernel: [    0.000000] ACPI: MCFG 7FE73BC0, 003E (r16 DELL    M08     27D80313 ASL        61)
Aug 19 16:07:19 rock-laptop kernel: [    0.000000] ACPI: SLIC 7FE73C9C, 0176 (r1 DELL    M08     27D80313 ASL        61)
Aug 19 16:07:19 rock-laptop kernel: [    0.000000] ACPI: OSFR 7FE73200, 002C (r1 DELL    M08     27D80313 ASL        61)
Aug 19 16:07:19 rock-laptop kernel: [    0.000000] ACPI: BOOT 7FE737C0, 0028 (r1 DELL    M08     27D80313 ASL        61)
Aug 19 16:07:19 rock-laptop kernel: [    0.000000] ACPI: SSDT 7FE72202, 04CC (r1  PmRef    CpuPm     3000 INTL 20050624)
Aug 19 16:07:19 rock-laptop kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
Aug 19 16:07:19 rock-laptop kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Aug 19 16:07:19 rock-laptop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Aug 19 16:07:19 rock-laptop kernel: [    0.000000] Processor #0 6:15 APIC version 20
Aug 19 16:07:19 rock-laptop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Aug 19 16:07:19 rock-laptop kernel: [    0.000000] Processor #1 6:15 APIC version 20
Aug 19 16:07:19 rock-laptop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Aug 19 16:07:19 rock-laptop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Aug 19 16:07:19 rock-laptop kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Aug 19 16:07:19 rock-laptop kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
Aug 19 16:07:19 rock-laptop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Aug 19 16:07:19 rock-laptop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Aug 19 16:07:19 rock-laptop kernel: [    0.000000] ACPI: IRQ0 used by override.
Aug 19 16:07:19 rock-laptop kernel: [    0.000000] ACPI: IRQ2 used by override.
Aug 19 16:07:19 rock-laptop kernel: [    0.000000] ACPI: IRQ9 used by override.
Aug 19 16:07:19 rock-laptop kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Aug 19 16:07:19 rock-laptop kernel: [    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
Aug 19 16:07:19 rock-laptop kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Aug 19 16:07:19 rock-laptop kernel: [    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:74000000)
Aug 19 16:07:19 rock-laptop kernel: [    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
Aug 19 16:07:19 rock-laptop kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 0000000000100000
Aug 19 16:07:19 rock-laptop kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 519798
Aug 19 16:07:19 rock-laptop kernel: [    0.000000] Kernel command line: root=UUID=96616c7a-aa80-45cb-aea6-7845b990a3fb ro quiet splash i8042.nomux=1
Aug 19 16:07:19 rock-laptop kernel: [    0.000000] mapped APIC to ffffb000 (fee00000)
Aug 19 16:07:19 rock-laptop kernel: [    0.000000] mapped IOAPIC to ffffa000 (fec00000)
Aug 19 16:07:19 rock-laptop kernel: [    0.000000] Enabling fast FPU save and restore... done.
Aug 19 16:07:19 rock-laptop kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Aug 19 16:07:19 rock-laptop kernel: [    0.000000] Initializing CPU#0
Aug 19 16:07:19 rock-laptop kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Aug 19 16:07:19 rock-laptop kernel: [    0.000000] Detected 1995.066 MHz processor.
Aug 19 16:07:19 rock-laptop kernel: [    9.754234] Console: colour VGA+ 80x25
Aug 19 16:07:19 rock-laptop kernel: [    9.754237] console [tty0] enabled
Aug 19 16:07:19 rock-laptop kernel: [    9.754532] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Aug 19 16:07:19 rock-laptop kernel: [    9.754812] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Aug 19 16:07:19 rock-laptop kernel: [    9.834877] Memory: 2065576k/2095560k available (2177k kernel code, 28688k reserved, 1006k data, 368k init, 1178056k highmem)
Aug 19 16:07:19 rock-laptop kernel: [    9.834883] virtual kernel memory layout:
Aug 19 16:07:19 rock-laptop kernel: [    9.834884]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
Aug 19 16:07:19 rock-laptop kernel: [    9.834885]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Aug 19 16:07:19 rock-laptop kernel: [    9.834886]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
Aug 19 16:07:19 rock-laptop kernel: [    9.834887]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
Aug 19 16:07:19 rock-laptop kernel: [    9.834888]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
Aug 19 16:07:19 rock-laptop kernel: [    9.834888]       .data : 0xc0320474 - 0xc041bdc4   (1006 kB)
Aug 19 16:07:19 rock-laptop kernel: [    9.834889]       .text : 0xc0100000 - 0xc0320474   (2177 kB)
Aug 19 16:07:19 rock-laptop kernel: [    9.834892] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Aug 19 16:07:19 rock-laptop kernel: [    9.834930] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
Aug 19 16:07:19 rock-laptop kernel: [    9.835061] hpet clockevent registered
Aug 19 16:07:19 rock-laptop kernel: [    9.915023] Calibrating delay using timer specific routine.. 3994.73 BogoMIPS (lpj=7989466)
Aug 19 16:07:19 rock-laptop kernel: [    9.915043] Security Framework initialized
Aug 19 16:07:19 rock-laptop kernel: [    9.915049] SELinux:  Disabled at boot.
Aug 19 16:07:19 rock-laptop kernel: [    9.915062] AppArmor: AppArmor initialized
Aug 19 16:07:19 rock-laptop kernel: [    9.915065] Failure registering capabilities with primary security module.
Aug 19 16:07:19 rock-laptop kernel: [    9.915073] Mount-cache hash table entries: 512
Aug 19 16:07:19 rock-laptop kernel: [    9.915187] Initializing cgroup subsys ns
Aug 19 16:07:19 rock-laptop kernel: [    9.915192] Initializing cgroup subsys cpuacct
Aug 19 16:07:19 rock-laptop kernel: [    9.915201] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e39d 00000000 00000001 00000000
Aug 19 16:07:19 rock-laptop kernel: [    9.915208] monitor/mwait feature present.
Aug 19 16:07:19 rock-laptop kernel: [    9.915209] using mwait in idle threads.
Aug 19 16:07:19 rock-laptop kernel: [    9.915213] CPU: L1 I cache: 32K, L1 D cache: 32K
Aug 19 16:07:19 rock-laptop kernel: [    9.915215] CPU: L2 cache: 2048K
Aug 19 16:07:19 rock-laptop kernel: [    9.915217] CPU: Physical Processor ID: 0
Aug 19 16:07:19 rock-laptop kernel: [    9.915218] CPU: Processor Core ID: 0
Aug 19 16:07:19 rock-laptop kernel: [    9.915220] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e39d 00000000 00000001 00000000
Aug 19 16:07:19 rock-laptop kernel: [    9.915228] Compat vDSO mapped to ffffe000.
Aug 19 16:07:19 rock-laptop kernel: [    9.915240] Checking 'hlt' instruction... OK.
Aug 19 16:07:19 rock-laptop kernel: [    9.931358] SMP alternatives: switching to UP code
Aug 19 16:07:19 rock-laptop kernel: [    9.932787] Early unpacking initramfs... done
Aug 19 16:07:19 rock-laptop kernel: [   10.220462] ACPI: Core revision 20070126
Aug 19 16:07:19 rock-laptop kernel: [   10.220498] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Aug 19 16:07:19 rock-laptop kernel: [   10.225922] CPU0: Intel(R) Core(TM)2 Duo CPU     T5750  @ 2.00GHz stepping 0d
Aug 19 16:07:19 rock-laptop kernel: [   10.225936] SMP alternatives: switching to SMP code
Aug 19 16:07:19 rock-laptop kernel: [   10.226552] Booting processor 1/1 eip 3000
Aug 19 16:07:19 rock-laptop kernel: [   10.236754] Initializing CPU#1
Aug 19 16:07:19 rock-laptop kernel: [   10.314795] Calibrating delay using timer specific routine.. 3990.04 BogoMIPS (lpj=7980084)
Aug 19 16:07:19 rock-laptop kernel: [   10.314801] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e39d 00000000 00000001 00000000
Aug 19 16:07:19 rock-laptop kernel: [   10.314805] monitor/mwait feature present.
Aug 19 16:07:19 rock-laptop kernel: [   10.314808] CPU: L1 I cache: 32K, L1 D cache: 32K
Aug 19 16:07:19 rock-laptop kernel: [   10.314809] CPU: L2 cache: 2048K
Aug 19 16:07:19 rock-laptop kernel: [   10.314811] CPU: Physical Processor ID: 0
Aug 19 16:07:19 rock-laptop kernel: [   10.314812] CPU: Processor Core ID: 1
Aug 19 16:07:19 rock-laptop kernel: [   10.314813] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e39d 00000000 00000001 00000000
Aug 19 16:07:19 rock-laptop kernel: [   10.315278] CPU1: Intel(R) Core(TM)2 Duo CPU     T5750  @ 2.00GHz stepping 0d
Aug 19 16:07:19 rock-laptop kernel: [   10.315299] Total of 2 processors activated (7984.77 BogoMIPS).
Aug 19 16:07:19 rock-laptop kernel: [   10.315499] ENABLING IO-APIC IRQs
Aug 19 16:07:19 rock-laptop kernel: [   10.315687] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Aug 19 16:07:19 rock-laptop kernel: [   10.462810] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
Aug 19 16:07:19 rock-laptop kernel: [   10.482812] Brought up 2 CPUs
Aug 19 16:07:19 rock-laptop kernel: [   10.482833] CPU0 attaching sched-domain:
Aug 19 16:07:19 rock-laptop kernel: [   10.482836]  domain 0: span 03
Aug 19 16:07:19 rock-laptop kernel: [   10.482837]   groups: 01 02
Aug 19 16:07:19 rock-laptop kernel: [   10.482840] CPU1 attaching sched-domain:
Aug 19 16:07:19 rock-laptop kernel: [   10.482841]  domain 0: span 03
Aug 19 16:07:19 rock-laptop kernel: [   10.482843]   groups: 02 01
Aug 19 16:07:19 rock-laptop kernel: [   10.483027] net_namespace: 64 bytes
Aug 19 16:07:19 rock-laptop kernel: [   10.483036] Booting paravirtualized kernel on bare hardware
Aug 19 16:07:19 rock-laptop kernel: [   10.483431] Time: 16:04:39  Date: 08/19/08
Aug 19 16:07:19 rock-laptop kernel: [   10.483455] NET: Registered protocol family 16
Aug 19 16:07:19 rock-laptop kernel: [   10.483608] EISA bus registered
Aug 19 16:07:19 rock-laptop kernel: [   10.483612] ACPI: bus type pci registered
Aug 19 16:07:19 rock-laptop kernel: [   10.494724] PCI: PCI BIOS revision 2.10 entry at 0xfad66, last bus=13
Aug 19 16:07:19 rock-laptop kernel: [   10.494726] PCI: Using configuration type 1
Aug 19 16:07:19 rock-laptop kernel: [   10.494739] Setting up standard PCI resources
Aug 19 16:07:19 rock-laptop kernel: [   10.501766] ACPI: EC: Look up EC in DSDT
Aug 19 16:07:19 rock-laptop kernel: [   10.501877] ACPI: BIOS _OSI(Linux) query ignored
Aug 19 16:07:19 rock-laptop kernel: [   10.501879] ACPI: DMI System Vendor: Dell Inc.
Aug 19 16:07:19 rock-laptop kernel: [   10.501880] ACPI: DMI Product Name: XPS M1530                       
Aug 19 16:07:19 rock-laptop kernel: [   10.501882] ACPI: DMI Product Version: 
Aug 19 16:07:19 rock-laptop kernel: [   10.501883] ACPI: DMI Board Name: 0D501F
Aug 19 16:07:19 rock-laptop kernel: [   10.501884] ACPI: DMI BIOS Vendor: Dell Inc.
Aug 19 16:07:19 rock-laptop kernel: [   10.501885] ACPI: DMI BIOS Date: 03/19/2008
Aug 19 16:07:19 rock-laptop kernel: [   10.501887] ACPI: Please send DMI info above to [email]linux-acpi@vger.kernel.org[/email]
Aug 19 16:07:19 rock-laptop kernel: [   10.501889] ACPI: If "acpi_osi=Linux" works better, please notify [email]linux-acpi@vger.kernel.org[/email]
Aug 19 16:07:19 rock-laptop kernel: [   10.506820] ACPI: Interpreter enabled
Aug 19 16:07:19 rock-laptop kernel: [   10.506823] ACPI: (supports S0 S3 S4 S5)
Aug 19 16:07:19 rock-laptop kernel: [   10.506835] ACPI: Using IOAPIC for interrupt routing
Aug 19 16:07:19 rock-laptop kernel: [   10.525302] ACPI: PCI Root Bridge [PCI0] (0000:00)
Aug 19 16:07:19 rock-laptop kernel: [   10.526259] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
Aug 19 16:07:19 rock-laptop kernel: [   10.526264] PCI quirk: region 1080-10bf claimed by ICH6 GPIO
Aug 19 16:07:19 rock-laptop kernel: [   10.527770] PCI: Transparent bridge - 0000:00:1e.0
Aug 19 16:07:19 rock-laptop kernel: [   10.527817] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Aug 19 16:07:19 rock-laptop kernel: [   10.528216] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]
Aug 19 16:07:19 rock-laptop kernel: [   10.528343] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
Aug 19 16:07:19 rock-laptop kernel: [   10.528424] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
Aug 19 16:07:19 rock-laptop kernel: [   10.528525] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
Aug 19 16:07:19 rock-laptop kernel: [   10.528624] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP05._PRT]
Aug 19 16:07:19 rock-laptop kernel: [   10.537491] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 11) *7
Aug 19 16:07:19 rock-laptop kernel: [   10.537588] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *10
Aug 19 16:07:19 rock-laptop kernel: [   10.537682] ACPI: PCI Interrupt Link [LNKC] (IRQs 9 10 11) *5
Aug 19 16:07:19 rock-laptop kernel: [   10.537767] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 7 9 10 11) *0, disabled.
Aug 19 16:07:19 rock-laptop kernel: [   10.537862] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
Aug 19 16:07:19 rock-laptop kernel: [   10.537961] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
Aug 19 16:07:19 rock-laptop kernel: [   10.538057] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
Aug 19 16:07:19 rock-laptop kernel: [   10.538144] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Aug 19 16:07:19 rock-laptop kernel: [   10.538268] Linux Plug and Play Support v0.97 (c) Adam Belay
Aug 19 16:07:19 rock-laptop kernel: [   10.538292] pnp: PnP ACPI init
Aug 19 16:07:19 rock-laptop kernel: [   10.538299] ACPI: bus type pnp registered
Aug 19 16:07:19 rock-laptop kernel: [   10.572355] pnpacpi: exceeded the max number of mem resources: 12
Aug 19 16:07:19 rock-laptop kernel: [   10.572525] pnp: PnP ACPI: found 13 devices
Aug 19 16:07:19 rock-laptop kernel: [   10.572527] ACPI: ACPI bus type pnp unregistered
Aug 19 16:07:19 rock-laptop kernel: [   10.572529] PnPBIOS: Disabled by ACPI PNP
Aug 19 16:07:19 rock-laptop kernel: [   10.572705] PCI: Using ACPI for IRQ routing
Aug 19 16:07:19 rock-laptop kernel: [   10.572707] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Aug 19 16:07:19 rock-laptop kernel: [   10.658614] NET: Registered protocol family 8
Aug 19 16:07:19 rock-laptop kernel: [   10.658616] NET: Registered protocol family 20
Aug 19 16:07:19 rock-laptop kernel: [   10.658643] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
Aug 19 16:07:19 rock-laptop kernel: [   10.658647] hpet0: 3 64-bit timers, 14318180 Hz
Aug 19 16:07:19 rock-laptop kernel: [   10.659678] AppArmor: AppArmor Filesystem Enabled
Aug 19 16:07:19 rock-laptop kernel: [   10.662607] Time: tsc clocksource has been installed.
Aug 19 16:07:19 rock-laptop kernel: [   10.662614] Switched to high resolution mode on CPU 0
Aug 19 16:07:19 rock-laptop kernel: [   10.662708] Switched to high resolution mode on CPU 1
Aug 19 16:07:19 rock-laptop kernel: [   10.678586] system 00:01: iomem range 0xff800000-0xff8fffff has been reserved
Aug 19 16:07:19 rock-laptop kernel: [   10.678588] system 00:01: iomem range 0xffc00000-0xffcfffff has been reserved
Aug 19 16:07:19 rock-laptop kernel: [   10.678596] system 00:06: ioport range 0xc80-0xcff could not be reserved
Aug 19 16:07:19 rock-laptop kernel: [   10.678602] system 00:09: iomem range 0xfed00000-0xfed003ff has been reserved
Aug 19 16:07:19 rock-laptop kernel: [   10.678607] system 00:0a: ioport range 0x900-0x97f has been reserved
Aug 19 16:07:19 rock-laptop kernel: [   10.678610] system 00:0a: ioport range 0x4d0-0x4d1 has been reserved
Aug 19 16:07:19 rock-laptop kernel: [   10.678612] system 00:0a: ioport range 0x1000-0x1005 has been reserved
Aug 19 16:07:19 rock-laptop kernel: [   10.678614] system 00:0a: ioport range 0x1008-0x100f has been reserved
Aug 19 16:07:19 rock-laptop kernel: [   10.678619] system 00:0b: ioport range 0xf400-0xf4fe has been reserved
Aug 19 16:07:19 rock-laptop kernel: [   10.678621] system 00:0b: ioport range 0x1006-0x1007 has been reserved
Aug 19 16:07:19 rock-laptop kernel: [   10.678624] system 00:0b: ioport range 0x100a-0x1059 could not be reserved
Aug 19 16:07:19 rock-laptop kernel: [   10.678626] system 00:0b: ioport range 0x1080-0x10bf has been reserved
Aug 19 16:07:19 rock-laptop kernel: [   10.678628] system 00:0b: ioport range 0x10c0-0x10df has been reserved
Aug 19 16:07:19 rock-laptop kernel: [   10.678630] system 00:0b: ioport range 0x1010-0x102f has been reserved
Aug 19 16:07:19 rock-laptop kernel: [   10.678632] system 00:0b: ioport range 0x809-0x809 has been reserved
Aug 19 16:07:19 rock-laptop kernel: [   10.678637] system 00:0c: iomem range 0x0-0x9efff could not be reserved
Aug 19 16:07:19 rock-laptop kernel: [   10.678640] system 00:0c: iomem range 0x9f000-0x9ffff could not be reserved
Aug 19 16:07:19 rock-laptop kernel: [   10.678642] system 00:0c: iomem range 0xc0000-0xcffff could not be reserved
Aug 19 16:07:19 rock-laptop kernel: [   10.678644] system 00:0c: iomem range 0xe0000-0xfffff could not be reserved
Aug 19 16:07:19 rock-laptop kernel: [   10.678647] system 00:0c: iomem range 0x100000-0x7fe71fff could not be reserved
Aug 19 16:07:19 rock-laptop kernel: [   10.678649] system 00:0c: iomem range 0x7fe72000-0x7fefffff could not be reserved
Aug 19 16:07:19 rock-laptop kernel: [   10.678651] system 00:0c: iomem range 0x7ff00000-0x7fffffff could not be reserved
Aug 19 16:07:19 rock-laptop kernel: [   10.678654] system 00:0c: iomem range 0xffe00000-0xffffffff could not be reserved
Aug 19 16:07:19 rock-laptop kernel: [   10.678656] system 00:0c: iomem range 0xffa00000-0xffbfffff has been reserved
Aug 19 16:07:19 rock-laptop kernel: [   10.678659] system 00:0c: iomem range 0xfec00000-0xfec0ffff could not be reserved
Aug 19 16:07:19 rock-laptop kernel: [   10.678661] system 00:0c: iomem range 0xfee00000-0xfee0ffff could not be reserved
Aug 19 16:07:19 rock-laptop kernel: [   10.678663] system 00:0c: iomem range 0xfed20000-0xfed8ffff could not be reserved
Aug 19 16:07:19 rock-laptop kernel: [   10.709007] PCI: Bridge: 0000:00:01.0
Aug 19 16:07:19 rock-laptop kernel: [   10.709009]   IO window: e000-efff
Aug 19 16:07:19 rock-laptop kernel: [   10.709013]   MEM window: fa000000-feafffff
Aug 19 16:07:19 rock-laptop kernel: [   10.709016]   PREFETCH window: e0000000-efffffff
Aug 19 16:07:19 rock-laptop kernel: [   10.709019] PCI: Bridge: 0000:00:1c.0
Aug 19 16:07:19 rock-laptop kernel: [   10.709022]   IO window: d000-dfff
Aug 19 16:07:19 rock-laptop kernel: [   10.709028]   MEM window: f9f00000-f9ffffff
Aug 19 16:07:19 rock-laptop kernel: [   10.709032]   PREFETCH window: disabled.
Aug 19 16:07:19 rock-laptop kernel: [   10.709038] PCI: Bridge: 0000:00:1c.1
Aug 19 16:07:19 rock-laptop kernel: [   10.709039]   IO window: disabled.
Aug 19 16:07:19 rock-laptop kernel: [   10.709045]   MEM window: f9e00000-f9efffff
Aug 19 16:07:19 rock-laptop kernel: [   10.709049]   PREFETCH window: disabled.
Aug 19 16:07:19 rock-laptop kernel: [   10.709055] PCI: Bridge: 0000:00:1c.4
Aug 19 16:07:19 rock-laptop kernel: [   10.709058]   IO window: c000-cfff
Aug 19 16:07:19 rock-laptop kernel: [   10.709064]   MEM window: f9c00000-f9dfffff
Aug 19 16:07:19 rock-laptop kernel: [   10.709068]   PREFETCH window: f0000000-f01fffff
Aug 19 16:07:19 rock-laptop kernel: [   10.709074] PCI: Bridge: 0000:00:1e.0
Aug 19 16:07:19 rock-laptop kernel: [   10.709075]   IO window: disabled.
Aug 19 16:07:19 rock-laptop kernel: [   10.709081]   MEM window: f9b00000-f9bfffff
Aug 19 16:07:19 rock-laptop kernel: [   10.709085]   PREFETCH window: disabled.
Aug 19 16:07:19 rock-laptop kernel: [   10.709102] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
Aug 19 16:07:19 rock-laptop kernel: [   10.709107] PCI: Setting latency timer of device 0000:00:01.0 to 64
Aug 19 16:07:19 rock-laptop kernel: [   10.709131] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
Aug 19 16:07:19 rock-laptop kernel: [   10.709136] PCI: Setting latency timer of device 0000:00:1c.0 to 64
Aug 19 16:07:19 rock-laptop kernel: [   10.709161] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 17 (level, low) -> IRQ 17
Aug 19 16:07:19 rock-laptop kernel: [   10.709167] PCI: Setting latency timer of device 0000:00:1c.1 to 64
Aug 19 16:07:19 rock-laptop kernel: [   10.709190] ACPI: PCI Interrupt 0000:00:1c.4[A] -> GSI 16 (level, low) -> IRQ 16
Aug 19 16:07:19 rock-laptop kernel: [   10.709196] PCI: Setting latency timer of device 0000:00:1c.4 to 64
Aug 19 16:07:19 rock-laptop kernel: [   10.709210] PCI: Setting latency timer of device 0000:00:1e.0 to 64
Aug 19 16:07:19 rock-laptop kernel: [   10.709219] NET: Registered protocol family 2
Aug 19 16:07:19 rock-laptop kernel: [   10.746572] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Aug 19 16:07:19 rock-laptop kernel: [   10.746761] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Aug 19 16:07:19 rock-laptop kernel: [   10.747138] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Aug 19 16:07:19 rock-laptop kernel: [   10.747336] TCP: Hash tables configured (established 131072 bind 65536)
Aug 19 16:07:19 rock-laptop kernel: [   10.747338] TCP reno registered
Aug 19 16:07:19 rock-laptop kernel: [   10.758632] checking if image is initramfs... it is
Aug 19 16:07:19 rock-laptop kernel: [   11.324865] Freeing initrd memory: 7307k freed
Aug 19 16:07:19 rock-laptop kernel: [   11.325010] Simple Boot Flag at 0x79 set to 0x1
Aug 19 16:07:19 rock-laptop kernel: [   11.325528] audit: initializing netlink socket (disabled)
Aug 19 16:07:19 rock-laptop kernel: [   11.325541] audit(1219161879.365:1): initialized
Aug 19 16:07:19 rock-laptop kernel: [   11.325724] highmem bounce pool size: 64 pages
Aug 19 16:07:19 rock-laptop kernel: [   11.327351] VFS: Disk quotas dquot_6.5.1
Aug 19 16:07:19 rock-laptop kernel: [   11.327416] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Aug 19 16:07:19 rock-laptop kernel: [   11.327528] io scheduler noop registered
Aug 19 16:07:19 rock-laptop kernel: [   11.327530] io scheduler anticipatory registered
Aug 19 16:07:19 rock-laptop kernel: [   11.327532] io scheduler deadline registered
Aug 19 16:07:19 rock-laptop kernel: [   11.327541] io scheduler cfq registered (default)
Aug 19 16:07:19 rock-laptop kernel: [   11.327698] Boot video device is 0000:01:00.0
Aug 19 16:07:19 rock-laptop kernel: [   11.327788] PCI: Setting latency timer of device 0000:00:01.0 to 64
Aug 19 16:07:19 rock-laptop kernel: [   11.327825] assign_interrupt_mode Found MSI capability
Aug 19 16:07:19 rock-laptop kernel: [   11.327856] Allocate Port Service[0000:00:01.0:pcie00]
Aug 19 16:07:19 rock-laptop kernel: [   11.327883] Allocate Port Service[0000:00:01.0:pcie02]
Aug 19 16:07:19 rock-laptop kernel: [   11.327958] PCI: Setting latency timer of device 0000:00:1c.0 to 64
Aug 19 16:07:19 rock-laptop kernel: [   11.328019] assign_interrupt_mode Found MSI capability
Aug 19 16:07:19 rock-laptop kernel: [   11.328067] Allocate Port Service[0000:00:1c.0:pcie00]
Aug 19 16:07:19 rock-laptop kernel: [   11.328094] Allocate Port Service[0000:00:1c.0:pcie02]
Aug 19 16:07:19 rock-laptop kernel: [   11.328195] PCI: Setting latency timer of device 0000:00:1c.1 to 64
Aug 19 16:07:19 rock-laptop kernel: [   11.328256] assign_interrupt_mode Found MSI capability
Aug 19 16:07:19 rock-laptop kernel: [   11.328304] Allocate Port Service[0000:00:1c.1:pcie00]
Aug 19 16:07:19 rock-laptop kernel: [   11.328333] Allocate Port Service[0000:00:1c.1:pcie02]
Aug 19 16:07:19 rock-laptop kernel: [   11.328430] PCI: Setting latency timer of device 0000:00:1c.4 to 64
Aug 19 16:07:19 rock-laptop kernel: [   11.328491] assign_interrupt_mode Found MSI capability
Aug 19 16:07:19 rock-laptop kernel: [   11.328539] Allocate Port Service[0000:00:1c.4:pcie00]
Aug 19 16:07:19 rock-laptop kernel: [   11.328564] Allocate Port Service[0000:00:1c.4:pcie02]
Aug 19 16:07:19 rock-laptop kernel: [   11.328787] isapnp: Scanning for PnP cards...
Aug 19 16:07:19 rock-laptop kernel: [   11.683106] isapnp: No Plug & Play device found
Aug 19 16:07:19 rock-laptop kernel: [   11.703791] Real Time Clock Driver v1.12ac
Aug 19 16:07:19 rock-laptop kernel: [   11.703914] hpet_resources: 0xfed00000 is busy
Aug 19 16:07:19 rock-laptop kernel: [   11.703966] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Aug 19 16:07:19 rock-laptop kernel: [   11.704923] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Aug 19 16:07:19 rock-laptop kernel: [   11.704977] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Aug 19 16:07:19 rock-laptop kernel: [   11.705055] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Aug 19 16:07:19 rock-laptop kernel: [   11.718326] serio: i8042 KBD port at 0x60,0x64 irq 1
Aug 19 16:07:19 rock-laptop kernel: [   11.718330] serio: i8042 AUX port at 0x60,0x64 irq 12
Aug 19 16:07:19 rock-laptop kernel: [   11.746028] mice: PS/2 mouse device common for all mice
Aug 19 16:07:19 rock-laptop kernel: [   11.746119] EISA: Probing bus 0 at eisa.0
Aug 19 16:07:19 rock-laptop kernel: [   11.746127] Cannot allocate resource for EISA slot 1
Aug 19 16:07:19 rock-laptop kernel: [   11.746157] EISA: Detected 0 cards.
Aug 19 16:07:19 rock-laptop kernel: [   11.746159] cpuidle: using governor ladder
Aug 19 16:07:19 rock-laptop kernel: [   11.746161] cpuidle: using governor menu
Aug 19 16:07:19 rock-laptop kernel: [   11.746231] NET: Registered protocol family 1
Aug 19 16:07:19 rock-laptop kernel: [   11.746254] Using IPI No-Shortcut mode
Aug 19 16:07:19 rock-laptop kernel: [   11.746278] registered taskstats version 1
Aug 19 16:07:19 rock-laptop kernel: [   11.746388]   Magic number: 4:649:85
Aug 19 16:07:19 rock-laptop kernel: [   11.746455] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Aug 19 16:07:19 rock-laptop kernel: [   11.746457] EDD information not available.
Aug 19 16:07:19 rock-laptop kernel: [   11.746641] Freeing unused kernel memory: 368k freed
Aug 19 16:07:19 rock-laptop kernel: [   11.769174] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
Aug 19 16:07:19 rock-laptop kernel: [   12.945349] fuse init (API version 7.9)
Aug 19 16:07:19 rock-laptop kernel: [   13.030640] ACPI: SSDT 7FE72D38, 0244 (r1  PmRef  Cpu0Ist     3000 INTL 20050624)
Aug 19 16:07:19 rock-laptop kernel: [   13.030814] ACPI: SSDT 7FE726CE, 05E5 (r1  PmRef  Cpu0Cst     3001 INTL 20050624)
Aug 19 16:07:19 rock-laptop kernel: [   13.031299] Monitor-Mwait will be used to enter C-1 state
Aug 19 16:07:19 rock-laptop kernel: [   13.031302] Monitor-Mwait will be used to enter C-2 state
Aug 19 16:07:19 rock-laptop kernel: [   13.031304] Monitor-Mwait will be used to enter C-3 state
Aug 19 16:07:19 rock-laptop kernel: [   13.031412] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
Aug 19 16:07:19 rock-laptop kernel: [   13.031417] ACPI: Processor [CPU0] (supports 8 throttling states)
Aug 19 16:07:19 rock-laptop kernel: [   13.031604] ACPI: SSDT 7FE72F7C, 00C4 (r1  PmRef  Cpu1Ist     3000 INTL 20050624)
Aug 19 16:07:19 rock-laptop kernel: [   13.031762] ACPI: SSDT 7FE72CB3, 0085 (r1  PmRef  Cpu1Cst     3000 INTL 20050624)
Aug 19 16:07:19 rock-laptop kernel: [   13.032352] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
Aug 19 16:07:19 rock-laptop kernel: [   13.032356] ACPI: Processor [CPU1] (supports 8 throttling states)
Aug 19 16:07:19 rock-laptop kernel: [   13.033457] ACPI: Thermal Zone [THM] (68 C)
Aug 19 16:07:19 rock-laptop kernel: [   13.350613] usbcore: registered new interface driver usbfs
Aug 19 16:07:19 rock-laptop kernel: [   13.350634] usbcore: registered new interface driver hub
Aug 19 16:07:19 rock-laptop kernel: [   13.350657] usbcore: registered new device driver usb
Aug 19 16:07:19 rock-laptop kernel: [   13.351825] USB Universal Host Controller Interface driver v3.0
Aug 19 16:07:19 rock-laptop kernel: [   13.351871] ACPI: PCI Interrupt 0000:00:1a.0[A] -> GSI 20 (level, low) -> IRQ 18
Aug 19 16:07:19 rock-laptop kernel: [   13.351882] PCI: Setting latency timer of device 0000:00:1a.0 to 64
Aug 19 16:07:19 rock-laptop kernel: [   13.351886] uhci_hcd 0000:00:1a.0: UHCI Host Controller
Aug 19 16:07:19 rock-laptop kernel: [   13.352112] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
Aug 19 16:07:19 rock-laptop kernel: [   13.352145] uhci_hcd 0000:00:1a.0: irq 18, io base 0x00006f20
Aug 19 16:07:19 rock-laptop kernel: [   13.352256] usb usb1: configuration #1 chosen from 1 choice
Aug 19 16:07:19 rock-laptop kernel: [   13.352275] hub 1-0:1.0: USB hub found
Aug 19 16:07:19 rock-laptop kernel: [   13.352280] hub 1-0:1.0: 2 ports detected
Aug 19 16:07:19 rock-laptop kernel: [   13.454088] ACPI: PCI Interrupt 0000:00:1a.1[B] -> GSI 21 (level, low) -> IRQ 19
Aug 19 16:07:19 rock-laptop kernel: [   13.454099] PCI: Setting latency timer of device 0000:00:1a.1 to 64
Aug 19 16:07:19 rock-laptop kernel: [   13.454103] uhci_hcd 0000:00:1a.1: UHCI Host Controller
Aug 19 16:07:19 rock-laptop kernel: [   13.454124] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
Aug 19 16:07:19 rock-laptop kernel: [   13.454156] uhci_hcd 0000:00:1a.1: irq 19, io base 0x00006f00
Aug 19 16:07:19 rock-laptop kernel: [   13.454252] usb usb2: configuration #1 chosen from 1 choice
Aug 19 16:07:19 rock-laptop kernel: [   13.454273] hub 2-0:1.0: USB hub found
Aug 19 16:07:19 rock-laptop kernel: [   13.454278] hub 2-0:1.0: 2 ports detected
Aug 19 16:07:19 rock-laptop kernel: [   13.465374] SCSI subsystem initialized
Aug 19 16:07:19 rock-laptop kernel: [   13.495640] libata version 3.00 loaded.
Aug 19 16:07:19 rock-laptop kernel: [   13.558023] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 20 (level, low) -> IRQ 18
Aug 19 16:07:19 rock-laptop kernel: [   13.558036] PCI: Setting latency timer of device 0000:00:1d.0 to 64
Aug 19 16:07:19 rock-laptop kernel: [   13.558040] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Aug 19 16:07:19 rock-laptop kernel: [   13.558060] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 3
Aug 19 16:07:19 rock-laptop kernel: [   13.558089] uhci_hcd 0000:00:1d.0: irq 18, io base 0x00006f80
Aug 19 16:07:19 rock-laptop kernel: [   13.558188] usb usb3: configuration #1 chosen from 1 choice
Aug 19 16:07:19 rock-laptop kernel: [   13.558207] hub 3-0:1.0: USB hub found
Aug 19 16:07:19 rock-laptop kernel: [   13.558212] hub 3-0:1.0: 2 ports detected
Aug 19 16:07:19 rock-laptop kernel: [   13.661978] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 21 (level, low) -> IRQ 19
Aug 19 16:07:19 rock-laptop kernel: [   13.661990] PCI: Setting latency timer of device 0000:00:1d.1 to 64
Aug 19 16:07:19 rock-laptop kernel: [   13.661994] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Aug 19 16:07:19 rock-laptop kernel: [   13.662018] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 4
Aug 19 16:07:19 rock-laptop kernel: [   13.662048] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00006f60
Aug 19 16:07:19 rock-laptop kernel: [   13.662149] usb usb4: configuration #1 chosen from 1 choice
Aug 19 16:07:19 rock-laptop kernel: [   13.662168] hub 4-0:1.0: USB hub found
Aug 19 16:07:19 rock-laptop kernel: [   13.662172] hub 4-0:1.0: 2 ports detected
Aug 19 16:07:19 rock-laptop kernel: [   13.693879] usb 1-1: new full speed USB device using uhci_hcd and address 2
Aug 19 16:07:19 rock-laptop kernel: [   13.765927] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 22 (level, low) -> IRQ 20
Aug 19 16:07:19 rock-laptop kernel: [   13.765938] PCI: Setting latency timer of device 0000:00:1d.2 to 64
Aug 19 16:07:19 rock-laptop kernel: [   13.765942] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Aug 19 16:07:19 rock-laptop kernel: [   13.765963] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 5
Aug 19 16:07:19 rock-laptop kernel: [   13.765994] uhci_hcd 0000:00:1d.2: irq 20, io base 0x00006f40
Aug 19 16:07:19 rock-laptop kernel: [   13.766097] usb usb5: configuration #1 chosen from 1 choice
Aug 19 16:07:19 rock-laptop kernel: [   13.766117] hub 5-0:1.0: USB hub found
Aug 19 16:07:19 rock-laptop kernel: [   13.766121] hub 5-0:1.0: 2 ports detected
Aug 19 16:07:19 rock-laptop kernel: [   13.836380] usb 1-1: configuration #1 chosen from 1 choice
Aug 19 16:07:19 rock-laptop kernel: [   13.868978] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 16 (level, low) -> IRQ 16
Aug 19 16:07:19 rock-laptop kernel: [   13.869011] PCI: Setting latency timer of device 0000:00:1f.1 to 64
Aug 19 16:07:19 rock-laptop kernel: [   13.869024] ACPI: PCI interrupt for device 0000:00:1f.1 disabled
Aug 19 16:07:19 rock-laptop kernel: [   13.869063] ACPI: PCI Interrupt 0000:00:1a.7[C] -> GSI 22 (level, low) -> IRQ 20
Aug 19 16:07:19 rock-laptop kernel: [   13.869074] PCI: Setting latency timer of device 0000:00:1a.7 to 64
Aug 19 16:07:19 rock-laptop kernel: [   13.869078] ehci_hcd 0000:00:1a.7: EHCI Host Controller
Aug 19 16:07:19 rock-laptop kernel: [   13.869099] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 6
Aug 19 16:07:19 rock-laptop kernel: [   13.873010] ehci_hcd 0000:00:1a.7: debug port 1
Aug 19 16:07:19 rock-laptop kernel: [   13.873016] PCI: cache line size of 32 is not supported by device 0000:00:1a.7
Aug 19 16:07:19 rock-laptop kernel: [   13.873022] ehci_hcd 0000:00:1a.7: irq 20, io mem 0xfed1c400
Aug 19 16:07:19 rock-laptop kernel: [   13.888777] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Aug 19 16:07:19 rock-laptop kernel: [   13.888954] usb usb6: configuration #1 chosen from 1 choice
Aug 19 16:07:19 rock-laptop kernel: [   13.888992] hub 6-0:1.0: USB hub found
Aug 19 16:07:19 rock-laptop kernel: [   13.889005] hub 6-0:1.0: 4 ports detected
Aug 19 16:07:19 rock-laptop kernel: [   13.956731] Clocksource tsc unstable (delta = -1306912214 ns)
Aug 19 16:07:19 rock-laptop kernel: [   13.960759] Time: hpet clocksource has been installed.
Aug 19 16:07:19 rock-laptop kernel: [   13.964459] ahci 0000:00:1f.2: version 3.0
Aug 19 16:07:19 rock-laptop kernel: [   13.964495] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 17 (level, low) -> IRQ 17
Aug 19 16:07:19 rock-laptop kernel: [   13.964566] ahci 0000:00:1f.2: nr_ports (3) and implemented port map (0x5) don't match, using nr_ports
Aug 19 16:07:19 rock-laptop kernel: [   13.964569] ahci 0000:00:1f.2: forcing PORTS_IMPL to 0x7
Aug 19 16:07:19 rock-laptop kernel: [   14.025957] usb 4-1: new low speed USB device using uhci_hcd and address 2
Aug 19 16:07:19 rock-laptop kernel: [   14.048114] usb 4-1: configuration #1 chosen from 1 choice
Aug 19 16:07:19 rock-laptop kernel: [   14.082578] usb 6-1: new high speed USB device using ehci_hcd and address 2
Aug 19 16:07:19 rock-laptop kernel: [   14.219612] usb 6-1: configuration #1 chosen from 1 choice
Aug 19 16:07:19 rock-laptop kernel: [   14.368754] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 3 Gbps 0x7 impl SATA mode
Aug 19 16:07:19 rock-laptop kernel: [   14.368760] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part 
Aug 19 16:07:19 rock-laptop kernel: [   14.368769] PCI: Setting latency timer of device 0000:00:1f.2 to 64
Aug 19 16:07:19 rock-laptop kernel: [   14.369060] scsi0 : ahci
Aug 19 16:07:19 rock-laptop kernel: [   14.369233] scsi1 : ahci
Aug 19 16:07:19 rock-laptop kernel: [   14.369360] scsi2 : ahci
Aug 19 16:07:19 rock-laptop kernel: [   14.369581] ata1: SATA max UDMA/133 abar m2048@0xfebfb800 port 0xfebfb900 irq 219
Aug 19 16:07:19 rock-laptop kernel: [   14.369585] ata2: SATA max UDMA/133 abar m2048@0xfebfb800 port 0xfebfb980 irq 219
Aug 19 16:07:19 rock-laptop kernel: [   14.369588] ata3: SATA max UDMA/133 abar m2048@0xfebfb800 port 0xfebfba00 irq 219
Aug 19 16:07:19 rock-laptop kernel: [   14.375146] usb 1-1: USB disconnect, address 2
Aug 19 16:07:19 rock-laptop kernel: [   14.375399] usbcore: registered new interface driver hiddev
Aug 19 16:07:19 rock-laptop kernel: [   14.444880] usb 1-2: new full speed USB device using uhci_hcd and address 3
Aug 19 16:07:19 rock-laptop kernel: [   14.446876] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Aug 19 16:07:19 rock-laptop kernel: [   14.447890] ata1.00: ATA-8: Hitachi HTS542516K9SA00, BBCOC39P, max UDMA/133
Aug 19 16:07:19 rock-laptop kernel: [   14.447895] ata1.00: 312581808 sectors, multi 8: LBA48 NCQ (depth 31/32)
Aug 19 16:07:19 rock-laptop kernel: [   14.449142] ata1.00: configured for UDMA/133
Aug 19 16:07:19 rock-laptop kernel: [   14.545084] usb 1-2: configuration #1 chosen from 1 choice
Aug 19 16:07:19 rock-laptop kernel: [   14.557321] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1d.1/usb4/4-1/4-1:1.0/input/input2
Aug 19 16:07:19 rock-laptop kernel: [   14.563339] input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.1-1
Aug 19 16:07:19 rock-laptop kernel: [   14.563368] usbcore: registered new interface driver usbhid
Aug 19 16:07:19 rock-laptop kernel: [   14.563373] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
Aug 19 16:07:19 rock-laptop kernel: [   14.585545] ata2: SATA link down (SStatus 0 SControl 0)
Aug 19 16:07:19 rock-laptop kernel: [   14.609919] ata3: SATA link down (SStatus 0 SControl 300)
Aug 19 16:07:19 rock-laptop kernel: [   14.610167] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS54251 BBCO PQ: 0 ANSI: 5
Aug 19 16:07:19 rock-laptop kernel: [   14.610276] ACPI: PCI Interrupt 0000:03:09.0[A] -> GSI 16 (level, low) -> IRQ 16
Aug 19 16:07:19 rock-laptop kernel: [   14.663018] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[16]  MMIO=[f9bff800-f9bfffff]  Max Packet=[2048]  IR/IT contexts=[4/4]
Aug 19 16:07:19 rock-laptop kernel: [   14.667088] Driver 'sd' needs updating - please use bus_type methods
Aug 19 16:07:19 rock-laptop kernel: [   14.667154] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
Aug 19 16:07:19 rock-laptop kernel: [   14.667164] sd 0:0:0:0: [sda] Write Protect is off
Aug 19 16:07:19 rock-laptop kernel: [   14.667166] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Aug 19 16:07:19 rock-laptop kernel: [   14.667180] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Aug 19 16:07:19 rock-laptop kernel: [   14.667221] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
Aug 19 16:07:19 rock-laptop kernel: [   14.667230] sd 0:0:0:0: [sda] Write Protect is off
Aug 19 16:07:19 rock-laptop kernel: [   14.667231] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Aug 19 16:07:19 rock-laptop kernel: [   14.667245] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Aug 19 16:07:19 rock-laptop kernel: [   14.667248]  sda:<6>ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 20 (level, low) -> IRQ 18
Aug 19 16:07:19 rock-laptop kernel: [   14.667560] PCI: Setting latency timer of device 0000:00:1d.7 to 64
Aug 19 16:07:19 rock-laptop kernel: [   14.667564] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Aug 19 16:07:19 rock-laptop kernel: [   14.667588] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 7
Aug 19 16:07:19 rock-laptop kernel: [   14.671508] ehci_hcd 0000:00:1d.7: debug port 1
Aug 19 16:07:19 rock-laptop kernel: [   14.671515] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
Aug 19 16:07:19 rock-laptop kernel: [   14.671519] ehci_hcd 0000:00:1d.7: irq 18, io mem 0xfed1c000
Aug 19 16:07:19 rock-laptop kernel: [   14.689681] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Aug 19 16:07:19 rock-laptop kernel: [   14.689882] usb usb7: configuration #1 chosen from 1 choice
Aug 19 16:07:19 rock-laptop kernel: [   14.689915] hub 7-0:1.0: USB hub found
Aug 19 16:07:19 rock-laptop kernel: [   14.689923] hub 7-0:1.0: 6 ports detected
Aug 19 16:07:19 rock-laptop kernel: [   14.694644]  sda1 sda2 sda3 sda4 < sda5 sda6 sda7 sda8 >
Aug 19 16:07:19 rock-laptop kernel: [   14.753521] sd 0:0:0:0: [sda] Attached SCSI disk
Aug 19 16:07:19 rock-laptop kernel: [   14.757114] sd 0:0:0:0: Attached scsi generic sg0 type 0
Aug 19 16:07:19 rock-laptop kernel: [   14.789986] ata_piix 0000:00:1f.1: version 2.12
Aug 19 16:07:19 rock-laptop kernel: [   14.790004] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 16 (level, low) -> IRQ 16
Aug 19 16:07:19 rock-laptop kernel: [   14.790045] PCI: Setting latency timer of device 0000:00:1f.1 to 64
Aug 19 16:07:19 rock-laptop kernel: [   14.791152] scsi3 : ata_piix
Aug 19 16:07:19 rock-laptop kernel: [   14.791517] scsi4 : ata_piix
Aug 19 16:07:19 rock-laptop kernel: [   14.792044] ata4: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x6fa0 irq 14
Aug 19 16:07:19 rock-laptop kernel: [   14.792047] ata5: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x6fa8 irq 15
Aug 19 16:07:19 rock-laptop kernel: [   14.974567] usb 4-1: USB disconnect, address 2
Aug 19 16:07:19 rock-laptop kernel: [   15.109981] ata4.00: ATAPI: Optiarc DVD+/-RW AD-7640A, JD05, max UDMA/33
Aug 19 16:07:19 rock-laptop kernel: [   15.221783] usb 4-1: new low speed USB device using uhci_hcd and address 3
Aug 19 16:07:19 rock-laptop kernel: [   15.227128] ata4.00: configured for UDMA/33
Aug 19 16:07:19 rock-laptop kernel: [   15.227225] ata5: port disabled. ignoring.
Aug 19 16:07:19 rock-laptop kernel: [   15.228124] scsi 3:0:0:0: CD-ROM            Optiarc  DVD+-RW AD-7640A JD05 PQ: 0 ANSI: 5
Aug 19 16:07:19 rock-laptop kernel: [   15.228243] scsi 3:0:0:0: Attached scsi generic sg1 type 5
Aug 19 16:07:19 rock-laptop kernel: [   15.233800] Driver 'sr' needs updating - please use bus_type methods
Aug 19 16:07:19 rock-laptop kernel: [   15.240219] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda caddy
Aug 19 16:07:19 rock-laptop kernel: [   15.240225] Uniform CD-ROM driver Revision: 3.20
Aug 19 16:07:19 rock-laptop kernel: [   15.240275] sr 3:0:0:0: Attached scsi CD-ROM sr0
Aug 19 16:07:19 rock-laptop kernel: [   15.301719] usb 4-1: configuration #1 chosen from 1 choice
Aug 19 16:07:19 rock-laptop kernel: [   15.314188] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1d.1/usb4/4-1/4-1:1.0/input/input3
Aug 19 16:07:19 rock-laptop kernel: [   15.324937] input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.1-1
Aug 19 16:07:19 rock-laptop kernel: [   15.369046] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[474fc00012dae470]
Aug 19 16:07:19 rock-laptop kernel: [   15.891584] kjournald starting.  Commit interval 5 seconds
Aug 19 16:07:19 rock-laptop kernel: [   15.891613] EXT3-fs: mounted filesystem with ordered data mode.
Aug 19 16:07:19 rock-laptop kernel: [   24.569131] input: PC Speaker as /devices/platform/pcspkr/input/input4
Aug 19 16:07:19 rock-laptop kernel: [   24.683059] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Aug 19 16:07:19 rock-laptop kernel: [   24.684652] input: PS/2 Mouse as /devices/virtual/input/input5
Aug 19 16:07:19 rock-laptop kernel: [   24.719765] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Aug 19 16:07:19 rock-laptop kernel: [   24.776024] Linux agpgart interface v0.102
Aug 19 16:07:19 rock-laptop kernel: [   24.813937] iTCO_vendor_support: vendor-support=0
Aug 19 16:07:19 rock-laptop kernel: [   24.850344] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input6
Aug 19 16:07:19 rock-laptop kernel: [   24.850462] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
Aug 19 16:07:19 rock-laptop kernel: [   24.893232] input: Lid Switch as /devices/virtual/input/input7
Aug 19 16:07:19 rock-laptop kernel: [   24.913298] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
Aug 19 16:07:19 rock-laptop kernel: [   24.913360] iTCO_wdt: Found a ICH8M TCO device (Version=2, TCOBASE=0x1060)
Aug 19 16:07:19 rock-laptop kernel: [   24.913399] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
Aug 19 16:07:19 rock-laptop kernel: [   25.085536] ACPI: Lid Switch [LID]
Aug 19 16:07:19 rock-laptop kernel: [   25.085679] ACPI: AC Adapter [AC] (on-line)
Aug 19 16:07:19 rock-laptop kernel: [   25.085771] input: Power Button (CM) as /devices/virtual/input/input8
Aug 19 16:07:19 rock-laptop kernel: [   25.140392] ACPI: Power Button (CM) [PBTN]
Aug 19 16:07:19 rock-laptop kernel: [   25.140447] input: Sleep Button (CM) as /devices/virtual/input/input9
Aug 19 16:07:19 rock-laptop kernel: [   25.196342] ACPI: Sleep Button (CM) [SBTN]
Aug 19 16:07:19 rock-laptop kernel: [   25.301929] ACPI: WMI-Acer: Mapper loaded
Aug 19 16:07:19 rock-laptop kernel: [   25.354363] ACPI: Battery Slot [BAT0] (battery absent)
Aug 19 16:07:19 rock-laptop kernel: [   25.743460] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:2e/LNXVIDEO:00/input/input10
Aug 19 16:07:19 rock-laptop kernel: [   25.759732] sdhci: Secure Digital Host Controller Interface driver
Aug 19 16:07:19 rock-laptop kernel: [   25.759735] sdhci: Copyright(c) Pierre Ossman
Aug 19 16:07:19 rock-laptop kernel: [   25.759771] sdhci: SDHCI controller found at 0000:03:09.1 [1180:0822] (rev 22)
Aug 19 16:07:19 rock-laptop kernel: [   25.759798] ACPI: PCI Interrupt 0000:03:09.1[B] -> GSI 18 (level, low) -> IRQ 21
Aug 19 16:07:19 rock-laptop kernel: [   25.762844] mmc0: SDHCI at 0xf9bff500 irq 21 DMA
Aug 19 16:07:19 rock-laptop kernel: [   25.810964] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
Aug 19 16:07:19 rock-laptop kernel: [   25.851877] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
Aug 19 16:07:19 rock-laptop kernel: [   25.871017] ACPI: PCI Interrupt 0000:09:00.0[A] -> GSI 16 (level, low) -> IRQ 16
Aug 19 16:07:19 rock-laptop kernel: [   25.871031] PCI: Setting latency timer of device 0000:09:00.0 to 64
Aug 19 16:07:19 rock-laptop kernel: [   25.871068] sky2 0000:09:00.0: v1.20 addr 0xf9ffc000 irq 16 Yukon-FE+ (0xb8) rev 0
Aug 19 16:07:19 rock-laptop kernel: [   25.871923] sky2 eth0: addr 00:1d:09:56:15:d6
Aug 19 16:07:19 rock-laptop kernel: [   25.950773] mmc0: new high speed SD card at address 0002
Aug 19 16:07:19 rock-laptop kernel: [   26.102523] usbcore: registered new interface driver ndiswrapper
Aug 19 16:07:19 rock-laptop kernel: [   26.685325] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
Aug 19 16:07:19 rock-laptop kernel: [   26.685336] PCI: Setting latency timer of device 0000:01:00.0 to 64
Aug 19 16:07:19 rock-laptop kernel: [   26.685453] NVRM: loading NVIDIA UNIX x86 Kernel Module  173.14.12  Thu Jul 17 18:11:36 PDT 2008
Aug 19 16:07:19 rock-laptop kernel: [   26.745043] Linux video capture interface: v2.00
Aug 19 16:07:19 rock-laptop kernel: [   26.872359] uvcvideo: Found UVC 1.00 device Laptop Integrated Webcam (05a9:2640)
Aug 19 16:07:19 rock-laptop kernel: [   26.872690] uvcvideo: Failed to query (135) UVC control 1 (unit 0) : -32 (exp. 26).
Aug 19 16:07:19 rock-laptop kernel: [   26.929842] usbcore: registered new interface driver uvcvideo
Aug 19 16:07:19 rock-laptop kernel: [   26.929847] USB Video Class driver (v0.1.0)
Aug 19 16:07:19 rock-laptop kernel: [   27.078935] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 21 (level, low) -> IRQ 19
Aug 19 16:07:19 rock-laptop kernel: [   27.078961] PCI: Setting latency timer of device 0000:00:1b.0 to 64
Aug 19 16:07:19 rock-laptop kernel: [   27.090104] sky2 eth0: enabling interface
Aug 19 16:07:19 rock-laptop kernel: [   27.157117] mmcblk0: mmc0:0002       976896KiB 
Aug 19 16:07:19 rock-laptop kernel: [   27.157144]  mmcblk0: p1
Aug 19 16:07:19 rock-laptop kernel: [   27.509944] lp: driver loaded but no devices found
Aug 19 16:07:19 rock-laptop kernel: [   28.430236] NET: Registered protocol family 17
Aug 19 16:07:19 rock-laptop kernel: [   70.731600] NET: Registered protocol family 10
Aug 19 16:07:19 rock-laptop kernel: [   70.731792] lo: Disabled Privacy Extensions
Aug 19 16:07:19 rock-laptop kernel: [   70.732109] ADDRCONF(NETDEV_UP): eth0: link is not ready
Aug 19 16:07:19 rock-laptop kernel: [  115.374239] EXT3 FS on sda6, internal journal
Aug 19 16:07:19 rock-laptop kernel: [  116.391027] ip_tables: (C) 2000-2006 Netfilter Core Team
[B]Aug 19 16:07:19 rock-laptop kernel: [  116.496155] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.25
Aug 19 16:07:19 rock-laptop kernel: [  116.496159] iwl3945: Copyright(c) 2003-2007 Intel Corporation
Aug 19 16:07:19 rock-laptop kernel: [  116.496254] PCI: Enabling device 0000:0b:00.0 (0000 -> 0002)
Aug 19 16:07:19 rock-laptop kernel: [  116.496264] ACPI: PCI Interrupt 0000:0b:00.0[A] -> GSI 17 (level, low) -> IRQ 17
Aug 19 16:07:19 rock-laptop kernel: [  116.496285] PCI: Setting latency timer of device 0000:0b:00.0 to 64
Aug 19 16:07:19 rock-laptop kernel: [  116.496303] iwl3945: Detected Intel PRO/Wireless 3945ABG Network Connection
Aug 19 16:07:19 rock-laptop kernel: [  116.502303] wmaster0: Selected rate control algorithm 'iwl-3945-rs'
[/B]
Aug 19 16:07:19 rock-laptop kernel: [  116.585897] ACPI: PCI interrupt for device 0000:0b:00.0 disabled
Aug 19 16:07:19 rock-laptop kernel: [  132.548776] atkbd.c: Unknown key pressed (translated set 2, code 0x91 on isa0060/serio0).
Aug 19 16:07:19 rock-laptop kernel: [  132.548783] atkbd.c: Use 'setkeycodes e011 <keycode>' to make it known.
Aug 19 16:07:19 rock-laptop kernel: [  132.832774] atkbd.c: Unknown key released (translated set 2, code 0x91 on isa0060/serio0).
Aug 19 16:07:19 rock-laptop kernel: [  132.832780] atkbd.c: Use 'setkeycodes e011 <keycode>' to make it known.
Aug 19 16:07:19 rock-laptop kernel: [  162.684561] No dock devices found.
Aug 19 16:07:19 rock-laptop avahi-daemon[5581]: Found user 'avahi' (UID 109) and group 'avahi' (GID 120).
Aug 19 16:07:19 rock-laptop avahi-daemon[5581]: Successfully dropped root privileges.
Aug 19 16:07:19 rock-laptop avahi-daemon[5581]: avahi-daemon 0.6.22 starting up.
Aug 19 16:07:19 rock-laptop avahi-daemon[5581]: Successfully called chroot().
Aug 19 16:07:19 rock-laptop avahi-daemon[5581]: Successfully dropped remaining capabilities.
Aug 19 16:07:19 rock-laptop avahi-daemon[5581]: No service file found in /etc/avahi/services.
Aug 19 16:07:19 rock-laptop avahi-daemon[5581]: Joining mDNS multicast group on interface eth0.IPv4 with address 169.254.5.180.
Aug 19 16:07:19 rock-laptop avahi-daemon[5581]: New relevant interface eth0.IPv4 for mDNS.
Aug 19 16:07:19 rock-laptop avahi-daemon[5581]: Network interface enumeration completed.
Aug 19 16:07:19 rock-laptop avahi-daemon[5581]: Registering new address record for 169.254.5.180 on eth0.IPv4.
Aug 19 16:07:19 rock-laptop avahi-daemon[5581]: Registering HINFO record with values 'I686'/'LINUX'.
Aug 19 16:07:19 rock-laptop kernel: [  163.543597] apm: BIOS not found.
Aug 19 16:07:19 rock-laptop kernel: [  163.603970] ppdev: user-space parallel port driver
Aug 19 16:07:19 rock-laptop kernel: [  163.680374] audit(1219158439.370:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5624 profile="/usr/sbin/cupsd" namespace="default"
Aug 19 16:07:20 rock-laptop avahi-daemon[5581]: Server startup complete. Host name is rock-laptop.local. Local service cookie is 3261690994.
Aug 19 16:07:20 rock-laptop dhcdbd: Started up.
Aug 19 16:07:21 rock-laptop hcid[5954]: Bluetooth HCI daemon
Aug 19 16:07:21 rock-laptop kernel: [  165.568567] Bluetooth: Core ver 2.11
Aug 19 16:07:21 rock-laptop kernel: [  165.568702] NET: Registered protocol family 31
Aug 19 16:07:21 rock-laptop kernel: [  165.568705] Bluetooth: HCI device and connection manager initialized
Aug 19 16:07:21 rock-laptop kernel: [  165.568711] Bluetooth: HCI socket layer initialized
Aug 19 16:07:21 rock-laptop hcid[5954]: Starting SDP server
Aug 19 16:07:21 rock-laptop kernel: [  165.587037] Bluetooth: L2CAP ver 2.9
Aug 19 16:07:21 rock-laptop kernel: [  165.587043] Bluetooth: L2CAP socket layer initialized
Aug 19 16:07:21 rock-laptop hcid[5954]: Created local server at unix:abstract=/var/run/dbus-hbqkPeEfyO,guid=90e7fb9ebe58d31202d0a8c348aae1a9
Aug 19 16:07:22 rock-laptop audio[5971]: Bluetooth Audio daemon
Aug 19 16:07:22 rock-laptop audio[5971]: Unix socket created: 5
Aug 19 16:07:22 rock-laptop audio[5971]: audio.conf: Key file does not have key 'Enable'
Aug 19 16:07:22 rock-laptop audio[5971]: audio.conf: Key file does not have key 'Disable'
Aug 19 16:07:22 rock-laptop input[5973]: Bluetooth Input daemon
Aug 19 16:07:22 rock-laptop input[5973]: Registered input manager path:/org/bluez/input
Aug 19 16:07:22 rock-laptop kernel: [  165.625973] Bluetooth: RFCOMM socket layer initialized
Aug 19 16:07:22 rock-laptop kernel: [  165.625990] Bluetooth: RFCOMM TTY layer initialized
Aug 19 16:07:22 rock-laptop kernel: [  165.625993] Bluetooth: RFCOMM ver 1.8
Aug 19 16:07:22 rock-laptop audio[5971]: add_service_record: got record id 0x10000
Aug 19 16:07:22 rock-laptop audio[5971]: audio.conf: Key file does not have key 'Disable'
Aug 19 16:07:22 rock-laptop audio[5971]: audio.conf: Key file does not have group 'A2DP'
Aug 19 16:07:22 rock-laptop last message repeated 3 times
Aug 19 16:07:22 rock-laptop audio[5971]: SEP 0x806d790 registered: type:0 codec:0 seid:1
Aug 19 16:07:22 rock-laptop audio[5971]: add_service_record: got record id 0x10001
Aug 19 16:07:22 rock-laptop audio[5971]: add_service_record: got record id 0x10002
Aug 19 16:07:22 rock-laptop audio[5971]: add_service_record: got record id 0x10003
Aug 19 16:07:22 rock-laptop audio[5971]: Registered manager path:/org/bluez/audio
Aug 19 16:07:24 rock-laptop anacron[6050]: Anacron 2.3 started on 2008-08-19
Aug 19 16:07:24 rock-laptop anacron[6050]: Normal exit (0 jobs run)
Aug 19 16:07:24 rock-laptop /usr/sbin/cron[6079]: (CRON) INFO (pidfile fd = 3)
Aug 19 16:07:24 rock-laptop /usr/sbin/cron[6080]: (CRON) STARTUP (fork ok)
Aug 19 16:07:24 rock-laptop /usr/sbin/cron[6080]: (CRON) INFO (Running @reboot jobs)
Aug 19 16:07:34 rock-laptop kernel: [  172.173231] input: Virtual ThinkFinger Keyboard as /devices/virtual/input/input11
Aug 19 16:07:38 rock-laptop ntpdate[5010]: can't find host ntp.ubuntu.com 
Aug 19 16:07:38 rock-laptop ntpdate[5010]: no servers can be used, exiting
Aug 19 16:07:41 rock-laptop anacron[6428]: Anacron 2.3 started on 2008-08-19
Aug 19 16:07:41 rock-laptop anacron[6428]: Normal exit (0 jobs run)
Aug 19 16:07:41 rock-laptop kernel: [  177.275115] CPU0 attaching NULL sched-domain.
Aug 19 16:07:41 rock-laptop kernel: [  177.275121] CPU1 attaching NULL sched-domain.
Aug 19 16:07:41 rock-laptop kernel: [  177.303945] CPU0 attaching sched-domain:
Aug 19 16:07:41 rock-laptop kernel: [  177.303951]  domain 0: span 03
Aug 19 16:07:41 rock-laptop kernel: [  177.303953]   groups: 01 02
Aug 19 16:07:41 rock-laptop kernel: [  177.303956] CPU1 attaching sched-domain:
Aug 19 16:07:41 rock-laptop kernel: [  177.303958]  domain 0: span 03
Aug 19 16:07:41 rock-laptop kernel: [  177.303959]   groups: 02 01
Aug 19 16:07:44 rock-laptop hald: mounted /dev/mmcblk0p1 on behalf of uid 1000
Aug 19 16:08:05 rock-laptop kernel: [  194.035169] nautilus[6316]: segfault at b8000020 eip b76eb2d6 esp bfe01460 error 4
Aug 19 16:08:05 rock-laptop init: tty4 main process (5140) killed by TERM signal
Aug 19 16:08:05 rock-laptop init: tty5 main process (5141) killed by TERM signal
Aug 19 16:08:05 rock-laptop init: tty2 main process (5143) killed by TERM signal
Aug 19 16:08:05 rock-laptop init: tty3 main process (5145) killed by TERM signal
Aug 19 16:08:05 rock-laptop init: tty6 main process (5147) killed by TERM signal
Aug 19 16:08:05 rock-laptop init: tty1 main process (6190) killed by TERM signal
Aug 19 16:08:06 rock-laptop gdm[6004]: GLib-CRITICAL: g_hash_table_lookup_extended: assertion `hash_table != NULL' failed 
Aug 19 16:08:06 rock-laptop gdm[6004]: WARNING: Request for invalid configuration key xdmcp/Enable=false 
Aug 19 16:08:06 rock-laptop avahi-daemon[5581]: Got SIGTERM, quitting.
Aug 19 16:08:06 rock-laptop avahi-daemon[5581]: Leaving mDNS multicast group on interface eth0.IPv4 with address 169.254.5.180.
Aug 19 16:08:08 rock-laptop kernel: [  197.334728] ip6_tables: (C) 2000-2006 Netfilter Core Team
Aug 19 16:08:09 rock-laptop exiting on signal 15

```

I think the main part of the network diagnostic is somewhere at the bottom of these system logs.

It seems that booting after Windows produces ERRORS during bootup in Ubuntu, which enabled my wireless.

I would appreciate if someone could explain what this means and what I'm doing wrong with my settings.

---

### Post by rocklee on 2008-08-19
Bump! And I'll keep on bumping.

---

### Post by rocklee on 2008-08-19
Results from iwconfig :

```
rock@rock-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"clarendon"  Nickname:""
          Mode:Managed  Frequency:2.472 GHz  Access Point: 00:17:3F:DE:62:31   
          Bit Rate=36 Mb/s   Tx-Power=15 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Power Management:off
          Link Quality=55/100  Signal level=-72 dBm  Noise level=-93 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

and ifconfig :

```
rock@rock-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1d:09:56:15:d6  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

eth0:avahi Link encap:Ethernet  HWaddr 00:1d:09:56:15:d6  
          inet addr:169.254.5.180  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2360 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2360 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:118000 (115.2 KB)  TX bytes:118000 (115.2 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1f:3c:7e:9a:fe  
          inet addr:192.168.2.3  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:3cff:fe7e:9afe/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:22878 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27212 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:15595098 (14.8 MB)  TX bytes:19070356 (18.1 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1F-3C-7E-9A-FE-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

and lshw :

```
rock@rock-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 12
       serial: 00:1d:09:56:15:d6
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A latency=0 module=sky2 multicast=yes
  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: wmaster0
       version: 02
       serial: 00:1f:3c:7e:9a:fe
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 ip=192.168.2.3 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g
rock@rock-laptop:~$ 

```

These are outputs from a working connection.

---

### Post by rocklee on 2008-08-25
Bump!

---

