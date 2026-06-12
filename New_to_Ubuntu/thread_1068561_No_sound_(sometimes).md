---
title: "No sound (sometimes)"
date: 2009-02-13
forum: New to Ubuntu
---

### Post by laffinet on 2009-02-13
Hi all !

This is really annoying: I recently installed a new USB wireless adapter (D-Link DWA-110), which worked out of the box (no ndiswrapper necessary).

After booting I now sometimes have no sound whatsoever. Reboot most of the time seems to fix it, but it looks like I have a 50/50 chance of sound/no sound.

Here's a dmesg after I'm left with no sound. Any help is much appreciated.

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.27-11-generic (buildd@rothera) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Thu Jan 29 19:24:39 UTC 2009 (Ubuntu 2.6.27-11.27-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e2000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000b7fa0000 (usable)
[    0.000000]  BIOS-e820: 00000000b7fa0000 - 00000000b7fae000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000b7fae000 - 00000000b7fe0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000b7fe0000 - 00000000b7fee000 (reserved)
[    0.000000]  BIOS-e820: 00000000b7ff0000 - 00000000b8000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fef00000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] DMI present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working it around.
[    0.000000] last_pfn = 0xb7fa0 max_arch_pfn = 0x100000
[    0.000000] kernel direct mapping tables up to 38000000 @ 10000-15000
[    0.000000] RAMDISK: 37819000 - 37fef8ef
[    0.000000] ACPI: RSDP 000FB720, 0024 (r2 ACPIAM)
[    0.000000] ACPI: XSDT B7FA0100, 005C (r1 071808 XSDT1351 20080718 MSFT       97)
[    0.000000] ACPI: FACP B7FA0290, 00F4 (r3 071808 FACP1351 20080718 MSFT       97)
[    0.000000] ACPI: DSDT B7FA0450, 7362 (r1  A1059 A1059000        0 INTL 20051117)
[    0.000000] ACPI: FACS B7FAE000, 0040
[    0.000000] ACPI: APIC B7FA0390, 0080 (r1 071808 APIC1351 20080718 MSFT       97)
[    0.000000] ACPI: MCFG B7FA0410, 003C (r1 071808 OEMMCFG  20080718 MSFT       97)
[    0.000000] ACPI: OEMB B7FAE040, 0071 (r1 071808 OEMB1351 20080718 MSFT       97)
[    0.000000] ACPI: HPET B7FA77C0, 0038 (r1 071808 OEMHPET0 20080718 MSFT       97)
[    0.000000] ACPI: NVHD B7FAE0C0, 0554 (r1 071808  NVHDCP  20080718 MSFT       97)
[    0.000000] ACPI: SSDT B7FA7800, 028A (r1 A_M_I_ POWERNOW        1 AMD         1)
[    0.000000] 2047MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 38000000
[    0.000000]   low ram: 00000000 - 38000000
[    0.000000]   bootmap 00011000 - 00018000
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 0038000000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00005c29e0]    TEXT DATA BSS ==> [0000100000 - 00005c29e0]
[    0.000000]   #4 [0037819000 - 0037fef8ef]          RAMDISK ==> [0037819000 - 0037fef8ef]
[    0.000000]   #5 [00005c3000 - 00005c6000]    INIT_PG_TABLE ==> [00005c3000 - 00005c6000]
[    0.000000]   #6 [000009f000 - 0000100000]    BIOS reserved ==> [000009f000 - 0000100000]
[    0.000000]   #7 [0000010000 - 0000011000]          PGTABLE ==> [0000010000 - 0000011000]
[    0.000000]   #8 [0000011000 - 0000018000]          BOOTMAP ==> [0000011000 - 0000018000]
[    0.000000] found SMP MP-table at [c00ff780] 000ff780
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x00038000
[    0.000000]   HighMem  0x00038000 -> 0x000b7fa0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x000b7fa0
[    0.000000] On node 0 totalpages: 753455
[    0.000000] free_area_init_node: node 0, pgdat c048c680, node_mem_map c1000240
[    0.000000]   DMA zone: 3947 pages, LIFO batch:0
[    0.000000]   Normal zone: 223300 pages, LIFO batch:31
[    0.000000]   HighMem zone: 519584 pages, LIFO batch:31
[    0.000000] Detected use of extended apic ids on hypertransport bus
[    0.000000] ACPI: PM-Timer IO Port: 0x508
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e2000
[    0.000000] PM: Registered nosave memory: 00000000000e2000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at c0000000 (gap: b8000000:46c00000)
[    0.000000] PERCPU: Allocating 41628 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 4, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 746831
[    0.000000] Kernel command line: root=UUID=d9905ae1-0b35-4e76-a97f-ac0b7363fefe ro quiet nosplash 
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Extended CMOS year: 2000
[    0.000000] TSC: Unable to calibrate against PIT
[    0.000000] TSC: using PMTIMER reference calibration
[    0.000000] Detected 2600.233 MHz processor.
[    0.004000] spurious 8259A interrupt: IRQ7.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] Memory: 2972524k/3014272k available (2576k kernel code, 40440k reserved, 1165k data, 424k init, 2096768k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xf8800000 - 0xff3fe000   ( 107 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[    0.004000]       .init : 0xc04ad000 - 0xc0517000   ( 424 kB)
[    0.004000]       .data : 0xc03840da - 0xc04a7680   (1165 kB)
[    0.004000]       .text : 0xc0100000 - 0xc03840da   (2576 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] CPA: page pool initialized 1 of 1 pages preallocated
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.004000] hpet clockevent registered
[    0.004000] Calibrating delay loop (skipped), value calculated using timer frequency.. 5200.46 BogoMIPS (lpj=10400932)
[    0.004000] Security Framework initialized
[    0.004000] SELinux:  Disabled at boot.
[    0.004000] AppArmor: AppArmor initialized
[    0.004000] Mount-cache hash table entries: 512
[    0.004000] Initializing cgroup subsys ns
[    0.004000] Initializing cgroup subsys cpuacct
[    0.004000] Initializing cgroup subsys memory
[    0.004000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.004000] CPU 0(2) -> Core 0
[    0.004000] using C1E aware idle routine
[    0.004000] Checking 'hlt' instruction... OK.
[    0.017346] ACPI: Core revision 20080609
[    0.019696] ACPI: Checking initramfs for custom DSDT
[    0.286929] ENABLING IO-APIC IRQs
[    0.287154] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.326850] CPU0: AMD Athlon(tm) 64 X2 Dual Core Processor 5000+ stepping 02
[    0.328020] Booting processor 1/1 ip 6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 5200.50 BogoMIPS (lpj=10401013)
[    0.004000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.004000] CPU 1(2) -> Core 1
[    0.412160] CPU1: AMD Athlon(tm) 64 X2 Dual Core Processor 5000+ stepping 02
[    0.412183] Brought up 2 CPUs
[    0.412186] Total of 2 processors activated (10400.97 BogoMIPS).
[    0.412221] CPU0 attaching sched-domain:
[    0.412223]  domain 0: span 0-1 level CPU
[    0.412225]   groups: 0 1
[    0.412230] CPU1 attaching sched-domain:
[    0.412232]  domain 0: span 0-1 level CPU
[    0.412234]   groups: 1 0
[    0.412289] net_namespace: 840 bytes
[    0.412289] Booting paravirtualized kernel on bare hardware
[    0.412289] Time:  7:17:50  Date: 02/13/09
[    0.412289] NET: Registered protocol family 16
[    0.412289] EISA bus registered
[    0.412289] ACPI: bus type pci registered
[    0.412289] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.412289] PCI: Not using MMCONFIG.
[    0.412695] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=8
[    0.412697] PCI: Using configuration type 1 for base access
[    0.412714] mtrr: your CPUs had inconsistent fixed MTRR settings
[    0.412714] mtrr: probably your BIOS does not setup all CPUs.
[    0.412714] mtrr: corrected configuration.
[    0.412812] ACPI: EC: Look up EC in DSDT
[    0.427232] ACPI: Interpreter enabled
[    0.427235] ACPI: (supports S0 S1 S3 S4 S5)
[    0.427250] ACPI: Using IOAPIC for interrupt routing
[    0.427304] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.434022] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
[    0.434025] PCI: Using MMCONFIG for extended config space
[    0.444261] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.444261] PCI: 0000:00:01.0 reg 10 io port: [900, 9ff]
[    0.444261] PCI: 0000:00:01.1 reg 10 io port: [ec00, ec3f]
[    0.444261] PCI: 0000:00:01.1 reg 20 io port: [600, 63f]
[    0.444261] PCI: 0000:00:01.1 reg 24 io port: [700, 73f]
[    0.444261] pci 0000:00:01.1: PME# supported from D3hot D3cold
[    0.444261] pci 0000:00:01.1: PME# disabled
[    0.444261] PCI: 0000:00:02.0 reg 10 32bit mmio: [d9fff000, d9ffffff]
[    0.444262] pci 0000:00:02.0: supports D1
[    0.444264] pci 0000:00:02.0: supports D2
[    0.444265] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.444268] pci 0000:00:02.0: PME# disabled
[    0.444286] PCI: 0000:00:02.1 reg 10 32bit mmio: [d9ffec00, d9ffecff]
[    0.444308] pci 0000:00:02.1: supports D1
[    0.444309] pci 0000:00:02.1: supports D2
[    0.444311] pci 0000:00:02.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.444314] pci 0000:00:02.1: PME# disabled
[    0.444333] PCI: 0000:00:04.0 reg 10 32bit mmio: [d9ffd000, d9ffdfff]
[    0.444352] pci 0000:00:04.0: supports D1
[    0.444353] pci 0000:00:04.0: supports D2
[    0.444355] pci 0000:00:04.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.444358] pci 0000:00:04.0: PME# disabled
[    0.444376] PCI: 0000:00:04.1 reg 10 32bit mmio: [d9ffe800, d9ffe8ff]
[    0.444397] pci 0000:00:04.1: supports D1
[    0.444399] pci 0000:00:04.1: supports D2
[    0.444400] pci 0000:00:04.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.444403] pci 0000:00:04.1: PME# disabled
[    0.444430] PCI: 0000:00:06.0 reg 20 io port: [ffa0, ffaf]
[    0.444459] PCI: 0000:00:07.0 reg 10 32bit mmio: [d9ff8000, d9ffbfff]
[    0.444480] pci 0000:00:07.0: PME# supported from D3hot D3cold
[    0.444483] pci 0000:00:07.0: PME# disabled
[    0.444522] PCI: 0000:00:09.0 reg 10 io port: [e480, e487]
[    0.444525] PCI: 0000:00:09.0 reg 14 io port: [e400, e403]
[    0.444528] PCI: 0000:00:09.0 reg 18 io port: [e080, e087]
[    0.444531] PCI: 0000:00:09.0 reg 1c io port: [e000, e003]
[    0.444535] PCI: 0000:00:09.0 reg 20 io port: [dc00, dc0f]
[    0.444538] PCI: 0000:00:09.0 reg 24 32bit mmio: [d9ff6000, d9ff7fff]
[    0.444570] PCI: 0000:00:0a.0 reg 10 32bit mmio: [d9ffc000, d9ffcfff]
[    0.444574] PCI: 0000:00:0a.0 reg 14 io port: [d880, d887]
[    0.444577] PCI: 0000:00:0a.0 reg 18 32bit mmio: [d9ffe400, d9ffe4ff]
[    0.444581] PCI: 0000:00:0a.0 reg 1c 32bit mmio: [d9ffe000, d9ffe00f]
[    0.444595] pci 0000:00:0a.0: supports D1
[    0.444597] pci 0000:00:0a.0: supports D2
[    0.444599] pci 0000:00:0a.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.444603] pci 0000:00:0a.0: PME# disabled
[    0.444625] pci 0000:00:0b.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.444628] pci 0000:00:0b.0: PME# disabled
[    0.444648] pci 0000:00:0c.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.444651] pci 0000:00:0c.0: PME# disabled
[    0.444672] pci 0000:00:0d.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.444674] pci 0000:00:0d.0: PME# disabled
[    0.444695] pci 0000:00:0e.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.444697] pci 0000:00:0e.0: PME# disabled
[    0.444718] pci 0000:00:0f.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.444720] pci 0000:00:0f.0: PME# disabled
[    0.444743] pci 0000:00:10.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.444745] pci 0000:00:10.0: PME# disabled
[    0.444766] pci 0000:00:11.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.444768] pci 0000:00:11.0: PME# disabled
[    0.444779] PCI: 0000:00:12.0 reg 10 32bit mmio: [d8000000, d8ffffff]
[    0.444784] PCI: 0000:00:12.0 reg 14 64bit mmio: [c0000000, cfffffff]
[    0.444788] PCI: 0000:00:12.0 reg 1c 64bit mmio: [d7000000, d7ffffff]
[    0.444792] PCI: 0000:00:12.0 reg 30 32bit mmio: [d9fc0000, d9fdffff]
[    0.444883] PCI: 0000:01:06.0 reg 10 32bit mmio: [df000000, dfffffff]
[    0.444927] PCI: 0000:01:06.1 reg 10 32bit mmio: [de000000, deffffff]
[    0.444971] PCI: 0000:01:06.2 reg 10 32bit mmio: [dd000000, ddffffff]
[    0.445023] PCI: 0000:01:07.0 reg 10 32bit mmio: [dc000000, dcffffff]
[    0.445067] PCI: 0000:01:07.1 reg 10 32bit mmio: [db000000, dbffffff]
[    0.445110] PCI: 0000:01:07.2 reg 10 32bit mmio: [da000000, daffffff]
[    0.445162] pci 0000:00:08.0: transparent bridge
[    0.445166] PCI: bridge 0000:00:08.0 32bit mmio: [da000000, dfffffff]
[    0.445409] bus 00 -> node 0
[    0.445415] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.445666] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.445819] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR10._PRT]
[    0.445937] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR11._PRT]
[    0.464288] ACPI: PCI Interrupt Link [LNKA] (IRQs 16 17 18 19) *11
[    0.464558] ACPI: PCI Interrupt Link [LNKB] (IRQs 16 17 18 19) *11
[    0.464822] ACPI: PCI Interrupt Link [LNKC] (IRQs 16 17 18 19) *0, disabled.
[    0.465086] ACPI: PCI Interrupt Link [LNKD] (IRQs 16 17 18 19) *0, disabled.
[    0.465350] ACPI: PCI Interrupt Link [LNEA] (IRQs 16 17 18 19) *0, disabled.
[    0.465614] ACPI: PCI Interrupt Link [LNEB] (IRQs 16 17 18 19) *0, disabled.
[    0.465877] ACPI: PCI Interrupt Link [LNEC] (IRQs 16 17 18 19) *0, disabled.
[    0.466141] ACPI: PCI Interrupt Link [LNED] (IRQs 16 17 18 19) *0, disabled.
[    0.466410] ACPI: PCI Interrupt Link [LUB0] (IRQs 20 21 22 23) *11
[    0.466683] ACPI: PCI Interrupt Link [LUB2] (IRQs 20 21 22 23) *10
[    0.466951] ACPI: PCI Interrupt Link [LMAC] (IRQs 20 21 22 23) *10
[    0.467220] ACPI: PCI Interrupt Link [LAZA] (IRQs 20 21 22 23) *11
[    0.468229] ACPI: PCI Interrupt Link [SGRU] (IRQs 20 21 22 23) *11
[    0.468497] ACPI: PCI Interrupt Link [LSMB] (IRQs 20 21 22 23) *10
[    0.468761] ACPI: PCI Interrupt Link [LPMU] (IRQs 20 21 22 23) *0, disabled.
[    0.469030] ACPI: PCI Interrupt Link [LSA0] (IRQs 20 21 22 23) *15
[    0.469338] ACPI: PCI Interrupt Link [LATA] (IRQs 20 21 22 23) *0, disabled.
[    0.469607] ACPI: PCI Interrupt Link [UB11] (IRQs 20 21 22 23) *11
[    0.469877] ACPI: PCI Interrupt Link [UB12] (IRQs 20 21 22 23) *11
[    0.469931] ACPI Warning (tbutils-0217): Incorrect checksum in table [OEMB] - 6D, should be 60 [20080609]
[    0.469931] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.469931] pnp: PnP ACPI init
[    0.469931] ACPI: bus type pnp registered
[    0.473493] pnp 00:06: io resource (0x900-0x97f) overlaps 0000:00:01.0 BAR 0 (0x900-0x9ff), disabling
[    0.473493] pnp 00:06: io resource (0x980-0x9ff) overlaps 0000:00:01.0 BAR 0 (0x900-0x9ff), disabling
[    0.477415] pnp: PnP ACPI: found 14 devices
[    0.477417] ACPI: ACPI bus type pnp unregistered
[    0.477420] PnPBIOS: Disabled by ACPI PNP
[    0.477437] PCI: Using ACPI for IRQ routing
[    0.484039] NET: Registered protocol family 8
[    0.484041] NET: Registered protocol family 20
[    0.484062] NetLabel: Initializing
[    0.484063] NetLabel:  domain hash size = 128
[    0.484065] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.484080] NetLabel:  unlabeled traffic allowed by default
[    0.484087] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 31
[    0.484091] hpet0: 3 32-bit timers, 25000000 Hz
[    0.486064] tracer: 772 pages allocated for 65536 entries of 48 bytes
[    0.486066]    actual entries 65620
[    0.486208] AppArmor: AppArmor Filesystem Enabled
[    0.486235] ACPI: RTC can wake from S4
[    0.488045] Switched to high resolution mode on CPU 0
[    0.488201] Switched to high resolution mode on CPU 1
[    0.492036] system 00:06: ioport range 0x4d0-0x4d1 has been reserved
[    0.492038] system 00:06: ioport range 0x800-0x80f has been reserved
[    0.492041] system 00:06: ioport range 0x500-0x57f has been reserved
[    0.492043] system 00:06: ioport range 0x580-0x5ff has been reserved
[    0.492046] system 00:06: ioport range 0x800-0x87f could not be reserved
[    0.492048] system 00:06: ioport range 0x880-0x8ff has been reserved
[    0.492050] system 00:06: ioport range 0xd00-0xd7f has been reserved
[    0.492053] system 00:06: ioport range 0xd80-0xdff has been reserved
[    0.492056] system 00:06: ioport range 0x1100-0x117f has been reserved
[    0.492058] system 00:06: ioport range 0x1180-0x11ff has been reserved
[    0.492062] system 00:06: iomem range 0xfefe0000-0xfefe01ff has been reserved
[    0.492064] system 00:06: iomem range 0xfefe1000-0xfefe1fff has been reserved
[    0.492067] system 00:06: iomem range 0xfee01000-0xfeefffff could not be reserved
[    0.492073] system 00:09: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.492076] system 00:09: iomem range 0xfee00000-0xfee00fff could not be reserved
[    0.492079] system 00:09: iomem range 0xb8000000-0xbfffffff has been reserved
[    0.492084] system 00:0a: ioport range 0x230-0x23f has been reserved
[    0.492086] system 00:0a: ioport range 0x290-0x29f has been reserved
[    0.492088] system 00:0a: ioport range 0xa00-0xa0f has been reserved
[    0.492091] system 00:0a: ioport range 0xa10-0xa1f has been reserved
[    0.492097] system 00:0c: iomem range 0xe0000000-0xefffffff has been reserved
[    0.492103] system 00:0d: iomem range 0x0-0x9ffff could not be reserved
[    0.492105] system 00:0d: iomem range 0xc0000-0xcffff could not be reserved
[    0.492108] system 00:0d: iomem range 0xe0000-0xfffff could not be reserved
[    0.492110] system 00:0d: iomem range 0x100000-0xb7ffffff could not be reserved
[    0.492113] system 00:0d: iomem range 0xfec00000-0xffffffff could not be reserved
[    0.527338] pci 0000:00:08.0: PCI bridge, secondary bus 0000:01
[    0.527340] pci 0000:00:08.0:   IO window: disabled
[    0.527344] pci 0000:00:08.0:   MEM window: 0xda000000-0xdfffffff
[    0.527347] pci 0000:00:08.0:   PREFETCH window: disabled
[    0.527350] pci 0000:00:0b.0: PCI bridge, secondary bus 0000:02
[    0.527352] pci 0000:00:0b.0:   IO window: disabled
[    0.527354] pci 0000:00:0b.0:   MEM window: disabled
[    0.527357] pci 0000:00:0b.0:   PREFETCH window: disabled
[    0.527360] pci 0000:00:0c.0: PCI bridge, secondary bus 0000:03
[    0.527361] pci 0000:00:0c.0:   IO window: disabled
[    0.527364] pci 0000:00:0c.0:   MEM window: disabled
[    0.527366] pci 0000:00:0c.0:   PREFETCH window: disabled
[    0.527369] pci 0000:00:0d.0: PCI bridge, secondary bus 0000:04
[    0.527371] pci 0000:00:0d.0:   IO window: disabled
[    0.527373] pci 0000:00:0d.0:   MEM window: disabled
[    0.527375] pci 0000:00:0d.0:   PREFETCH window: disabled
[    0.527378] pci 0000:00:0e.0: PCI bridge, secondary bus 0000:05
[    0.527380] pci 0000:00:0e.0:   IO window: disabled
[    0.527382] pci 0000:00:0e.0:   MEM window: disabled
[    0.527384] pci 0000:00:0e.0:   PREFETCH window: disabled
[    0.527387] pci 0000:00:0f.0: PCI bridge, secondary bus 0000:06
[    0.527389] pci 0000:00:0f.0:   IO window: disabled
[    0.527392] pci 0000:00:0f.0:   MEM window: disabled
[    0.527394] pci 0000:00:0f.0:   PREFETCH window: disabled
[    0.527397] pci 0000:00:10.0: PCI bridge, secondary bus 0000:07
[    0.527398] pci 0000:00:10.0:   IO window: disabled
[    0.527401] pci 0000:00:10.0:   MEM window: disabled
[    0.527403] pci 0000:00:10.0:   PREFETCH window: disabled
[    0.527406] pci 0000:00:11.0: PCI bridge, secondary bus 0000:08
[    0.527408] pci 0000:00:11.0:   IO window: disabled
[    0.527410] pci 0000:00:11.0:   MEM window: disabled
[    0.527412] pci 0000:00:11.0:   PREFETCH window: disabled
[    0.527421] pci 0000:00:08.0: setting latency timer to 64
[    0.527425] pci 0000:00:0b.0: setting latency timer to 64
[    0.527429] pci 0000:00:0c.0: setting latency timer to 64
[    0.527433] pci 0000:00:0d.0: setting latency timer to 64
[    0.527436] pci 0000:00:0e.0: setting latency timer to 64
[    0.527440] pci 0000:00:0f.0: setting latency timer to 64
[    0.527443] pci 0000:00:10.0: setting latency timer to 64
[    0.527447] pci 0000:00:11.0: setting latency timer to 64
[    0.527450] bus: 00 index 0 io port: [0, ffff]
[    0.527451] bus: 00 index 1 mmio: [0, ffffffff]
[    0.527453] bus: 01 index 0 mmio: [0, 0]
[    0.527455] bus: 01 index 1 mmio: [da000000, dfffffff]
[    0.527457] bus: 01 index 2 mmio: [0, 0]
[    0.527458] bus: 01 index 3 io port: [0, ffff]
[    0.527460] bus: 01 index 4 mmio: [0, ffffffff]
[    0.527462] bus: 02 index 0 mmio: [0, 0]
[    0.527463] bus: 02 index 1 mmio: [0, 0]
[    0.527465] bus: 02 index 2 mmio: [0, 0]
[    0.527466] bus: 02 index 3 mmio: [0, 0]
[    0.527468] bus: 03 index 0 mmio: [0, 0]
[    0.527469] bus: 03 index 1 mmio: [0, 0]
[    0.527471] bus: 03 index 2 mmio: [0, 0]
[    0.527472] bus: 03 index 3 mmio: [0, 0]
[    0.527474] bus: 04 index 0 mmio: [0, 0]
[    0.527476] bus: 04 index 1 mmio: [0, 0]
[    0.527477] bus: 04 index 2 mmio: [0, 0]
[    0.527479] bus: 04 index 3 mmio: [0, 0]
[    0.527480] bus: 05 index 0 mmio: [0, 0]
[    0.527482] bus: 05 index 1 mmio: [0, 0]
[    0.527483] bus: 05 index 2 mmio: [0, 0]
[    0.527485] bus: 05 index 3 mmio: [0, 0]
[    0.527487] bus: 06 index 0 mmio: [0, 0]
[    0.527488] bus: 06 index 1 mmio: [0, 0]
[    0.527490] bus: 06 index 2 mmio: [0, 0]
[    0.527492] bus: 06 index 3 mmio: [0, 0]
[    0.527493] bus: 07 index 0 mmio: [0, 0]
[    0.527495] bus: 07 index 1 mmio: [0, 0]
[    0.527496] bus: 07 index 2 mmio: [0, 0]
[    0.527498] bus: 07 index 3 mmio: [0, 0]
[    0.527499] bus: 08 index 0 mmio: [0, 0]
[    0.527501] bus: 08 index 1 mmio: [0, 0]
[    0.527502] bus: 08 index 2 mmio: [0, 0]
[    0.527504] bus: 08 index 3 mmio: [0, 0]
[    0.527516] NET: Registered protocol family 2
[    0.540058] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.540327] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.541055] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.541436] TCP: Hash tables configured (established 131072 bind 65536)
[    0.541439] TCP reno registered
[    0.548097] NET: Registered protocol family 1
[    0.548214] checking if image is initramfs... it is
[    1.094308] Freeing initrd memory: 8026k freed
[    1.095238] audit: initializing netlink socket (disabled)
[    1.095257] type=2000 audit(1234509470.092:1): initialized
[    1.099994] highmem bounce pool size: 64 pages
[    1.100000] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.102283] VFS: Disk quotas dquot_6.5.1
[    1.102363] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.102455] msgmni has been set to 1727
[    1.102562] io scheduler noop registered
[    1.102564] io scheduler anticipatory registered
[    1.102566] io scheduler deadline registered
[    1.102576] io scheduler cfq registered (default)
[    1.102607] pci 0000:00:00.0: Enabling HT MSI Mapping
[    1.148563] pci 0000:00:07.0: Enabling HT MSI Mapping
[    1.148578] pci 0000:00:08.0: Enabling HT MSI Mapping
[    1.148604] pci 0000:00:0a.0: Enabling HT MSI Mapping
[    1.148618] pci 0000:00:0b.0: Enabling HT MSI Mapping
[    1.148632] pci 0000:00:0c.0: Enabling HT MSI Mapping
[    1.148647] pci 0000:00:0d.0: Enabling HT MSI Mapping
[    1.148661] pci 0000:00:0e.0: Enabling HT MSI Mapping
[    1.148676] pci 0000:00:0f.0: Enabling HT MSI Mapping
[    1.148690] pci 0000:00:10.0: Enabling HT MSI Mapping
[    1.148705] pci 0000:00:11.0: Enabling HT MSI Mapping
[    1.148718] pci 0000:00:12.0: Boot video device
[    1.148833] pcieport-driver 0000:00:0b.0: setting latency timer to 64
[    1.148855] pcieport-driver 0000:00:0b.0: found MSI capability
[    1.148874] pci_express 0000:00:0b.0:pcie00: allocate port service
[    1.148917] pci_express 0000:00:0b.0:pcie03: allocate port service
[    1.148985] pcieport-driver 0000:00:0c.0: setting latency timer to 64
[    1.149005] pcieport-driver 0000:00:0c.0: found MSI capability
[    1.149019] pci_express 0000:00:0c.0:pcie00: allocate port service
[    1.149063] pci_express 0000:00:0c.0:pcie03: allocate port service
[    1.149129] pcieport-driver 0000:00:0d.0: setting latency timer to 64
[    1.149149] pcieport-driver 0000:00:0d.0: found MSI capability
[    1.149163] pci_express 0000:00:0d.0:pcie00: allocate port service
[    1.149203] pci_express 0000:00:0d.0:pcie03: allocate port service
[    1.149270] pcieport-driver 0000:00:0e.0: setting latency timer to 64
[    1.149290] pcieport-driver 0000:00:0e.0: found MSI capability
[    1.149305] pci_express 0000:00:0e.0:pcie00: allocate port service
[    1.149344] pci_express 0000:00:0e.0:pcie03: allocate port service
[    1.149411] pcieport-driver 0000:00:0f.0: setting latency timer to 64
[    1.149431] pcieport-driver 0000:00:0f.0: found MSI capability
[    1.149445] pci_express 0000:00:0f.0:pcie00: allocate port service
[    1.149485] pci_express 0000:00:0f.0:pcie03: allocate port service
[    1.149552] pcieport-driver 0000:00:10.0: setting latency timer to 64
[    1.149572] pcieport-driver 0000:00:10.0: found MSI capability
[    1.149586] pci_express 0000:00:10.0:pcie00: allocate port service
[    1.149626] pci_express 0000:00:10.0:pcie03: allocate port service
[    1.149697] pcieport-driver 0000:00:11.0: setting latency timer to 64
[    1.149716] pcieport-driver 0000:00:11.0: found MSI capability
[    1.149731] pci_express 0000:00:11.0:pcie00: allocate port service
[    1.149770] pci_express 0000:00:11.0:pcie03: allocate port service
[    1.150076] isapnp: Scanning for PnP cards...
[    1.503477] isapnp: No Plug & Play device found
[    1.535820] hpet_resources: 0xfed00000 is busy
[    1.535917] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.536048] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.536724] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.538426] brd: module loaded
[    1.538490] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    1.538675] PNP: No PS/2 controller found. Probing ports directly.
[    1.539056] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.539061] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.539336] mice: PS/2 mouse device common for all mice
[    1.539457] rtc_cmos 00:08: rtc core: registered rtc_cmos as rtc0
[    1.539491] rtc0: alarms up to one year, y3k, hpet irqs
[    1.539620] EISA: Probing bus 0 at eisa.0
[    1.539644] EISA: Detected 0 cards.
[    1.539648] cpuidle: using governor ladder
[    1.539650] cpuidle: using governor menu
[    1.540091] TCP cubic registered
[    1.540120] Using IPI No-Shortcut mode
[    1.540300] registered taskstats version 1
[    1.540438]   Magic number: 13:410:268
[    1.540483] tty ttyud: hash matches
[    1.540662] rtc_cmos 00:08: setting system clock to 2009-02-13 07:17:51 UTC (1234509471)
[    1.540666] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.540667] EDD information not available.
[    1.540965] Freeing unused kernel memory: 424k freed
[    1.541016] Write protecting the kernel text: 2580k
[    1.541049] Write protecting the kernel read-only data: 940k
[    1.654518] fuse init (API version 7.9)
[    1.675888] processor ACPI0007:00: registered as cooling_device0
[    1.676169] processor ACPI0007:01: registered as cooling_device1
[    1.999334] usbcore: registered new interface driver usbfs
[    1.999357] usbcore: registered new interface driver hub
[    1.999398] usbcore: registered new device driver usb
[    1.999549] No dock devices found.
[    2.001437] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
[    2.001894] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 23
[    2.001906] forcedeth 0000:00:0a.0: PCI INT A -> Link[LMAC] -> GSI 23 (level, low) -> IRQ 23
[    2.001910] forcedeth 0000:00:0a.0: setting latency timer to 64
[    2.019843] SCSI subsystem initialized
[    2.036177] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.036204] libata version 3.00 loaded.
[    2.069103] forcedeth 0000:00:0a.0: ifname eth0, PHY OUI 0x732 @ 3, addr 00:22:15:d4:b9:c6
[    2.069107] forcedeth 0000:00:0a.0: highdma pwrctl mgmt timirq gbit lnktim msi desc-v3
[    2.069609] ACPI: PCI Interrupt Link [LUB0] enabled at IRQ 22
[    2.069622] ohci_hcd 0000:00:02.0: PCI INT A -> Link[LUB0] -> GSI 22 (level, low) -> IRQ 22
[    2.069636] ohci_hcd 0000:00:02.0: setting latency timer to 64
[    2.069639] ohci_hcd 0000:00:02.0: OHCI Host Controller
[    2.069694] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
[    2.069718] ohci_hcd 0000:00:02.0: irq 22, io mem 0xd9fff000
[    2.126722] usb usb1: configuration #1 chosen from 1 choice
[    2.126752] hub 1-0:1.0: USB hub found
[    2.126763] hub 1-0:1.0: 6 ports detected
[    2.333289] ACPI: PCI Interrupt Link [LUB2] enabled at IRQ 21
[    2.333301] ehci_hcd 0000:00:02.1: PCI INT B -> Link[LUB2] -> GSI 21 (level, low) -> IRQ 21
[    2.333315] ehci_hcd 0000:00:02.1: setting latency timer to 64
[    2.333318] ehci_hcd 0000:00:02.1: EHCI Host Controller
[    2.333341] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 2
[    2.333370] ehci_hcd 0000:00:02.1: debug port 1
[    2.333374] ehci_hcd 0000:00:02.1: cache line size of 64 is not supported
[    2.333391] ehci_hcd 0000:00:02.1: irq 21, io mem 0xd9ffec00
[    2.344520] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    2.344718] usb usb2: configuration #1 chosen from 1 choice
[    2.344743] hub 2-0:1.0: USB hub found
[    2.344752] hub 2-0:1.0: 6 ports detected
[    2.552689] ACPI: PCI Interrupt Link [UB11] enabled at IRQ 20
[    2.552702] ohci_hcd 0000:00:04.0: PCI INT A -> Link[UB11] -> GSI 20 (level, low) -> IRQ 20
[    2.552716] ohci_hcd 0000:00:04.0: setting latency timer to 64
[    2.552718] ohci_hcd 0000:00:04.0: OHCI Host Controller
[    2.552742] ohci_hcd 0000:00:04.0: new USB bus registered, assigned bus number 3
[    2.552766] ohci_hcd 0000:00:04.0: irq 20, io mem 0xd9ffd000
[    2.610106] usb usb3: configuration #1 chosen from 1 choice
[    2.610129] hub 3-0:1.0: USB hub found
[    2.610138] hub 3-0:1.0: 6 ports detected
[    2.700013] usb 2-2: new high speed USB device using ehci_hcd and address 2
[    2.816563] ACPI: PCI Interrupt Link [UB12] enabled at IRQ 23
[    2.816568] ehci_hcd 0000:00:04.1: PCI INT B -> Link[UB12] -> GSI 23 (level, low) -> IRQ 23
[    2.816578] ehci_hcd 0000:00:04.1: setting latency timer to 64
[    2.816580] ehci_hcd 0000:00:04.1: EHCI Host Controller
[    2.816600] ehci_hcd 0000:00:04.1: new USB bus registered, assigned bus number 4
[    2.816623] ehci_hcd 0000:00:04.1: debug port 1
[    2.816627] ehci_hcd 0000:00:04.1: cache line size of 64 is not supported
[    2.816642] ehci_hcd 0000:00:04.1: irq 23, io mem 0xd9ffe800
[    2.840013] ehci_hcd 0000:00:04.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    2.840110] usb usb4: configuration #1 chosen from 1 choice
[    2.840133] hub 4-0:1.0: USB hub found
[    2.840140] hub 4-0:1.0: 6 ports detected
[    2.994101] usb 2-2: configuration #1 chosen from 1 choice
[    3.052806] ahci 0000:00:09.0: version 3.0
[    3.053256] ACPI: PCI Interrupt Link [LSA0] enabled at IRQ 22
[    3.053261] ahci 0000:00:09.0: PCI INT A -> Link[LSA0] -> GSI 22 (level, low) -> IRQ 22
[    3.053523] ahci 0000:00:09.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl IDE mode
[    3.053526] ahci 0000:00:09.0: flags: 64bit ncq sntf led clo pmp pio 
[    3.053530] ahci 0000:00:09.0: setting latency timer to 64
[    3.055116] scsi0 : ahci
[    3.055253] scsi1 : ahci
[    3.055311] scsi2 : ahci
[    3.055394] scsi3 : ahci
[    3.055699] ata1: SATA max UDMA/133 abar m8192@0xd9ff6000 port 0xd9ff6100 irq 22
[    3.055702] ata2: SATA max UDMA/133 irq_stat 0x00400040, connection status changed irq 22
[    3.055705] ata3: SATA max UDMA/133 irq_stat 0x00400040, connection status changed irq 22
[    3.055707] ata4: SATA max UDMA/133 irq_stat 0x00400040, connection status changed irq 22
[    3.372027] ata1: SATA link down (SStatus 0 SControl 300)
[    3.612014] usb 1-3: new low speed USB device using ohci_hcd and address 2
[    3.827984] usb 1-3: configuration #1 chosen from 1 choice
[    3.996054] usbcore: registered new interface driver hiddev
[    4.260015] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    4.260868] ata2.00: ATAPI: TSSTcorp CDDVDW SH-S223F, SB00, max UDMA/100, ATAPI AN
[    4.261821] ata2.00: configured for UDMA/100
[    4.300014] usb 3-2: new full speed USB device using ohci_hcd and address 2
[    4.512033] usb 3-2: config 1 interface 0 altsetting 0 endpoint 0x1 has an invalid bInterval 0, changing to 32
[    4.512037] usb 3-2: config 1 interface 0 altsetting 0 endpoint 0x82 has an invalid bInterval 0, changing to 32
[    4.524162] usb 3-2: configuration #1 chosen from 1 choice
[    4.828513] usb 3-3: new low speed USB device using ohci_hcd and address 3
[    5.042164] usb 3-3: configuration #1 chosen from 1 choice
[    5.054855] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:02.0/usb1/1-3/1-3:1.0/input/input1
[    5.056626] input,hidraw0: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:02.0-3
[    5.068638] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:02.0/usb1/1-3/1-3:1.1/input/input2
[    5.068957] input,hidraw1: USB HID v1.10 Device [Logitech USB Receiver] on usb-0000:00:02.0-3
[    5.076311] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:04.0/usb3/3-3/3-3:1.0/input/input3
[    5.076589] input,hidraw2: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:04.0-3
[    5.076608] usbcore: registered new interface driver usbhid
[    5.076611] usbhid: v2.6:USB HID core driver
[    5.148022] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    5.148819] ata3.00: ATA-8: WDC WD3200AAKS-00B3A0, 01.03A01, max UDMA/133
[    5.148822] ata3.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    5.149675] ata3.00: configured for UDMA/133
[    6.036015] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    6.036826] ata4.00: ATA-8: WDC WD6400AAKS-22A7B0, 01.03B01, max UDMA/133
[    6.036828] ata4.00: 1250263728 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    6.037720] ata4.00: configured for UDMA/133
[    6.038263] scsi 1:0:0:0: CD-ROM            TSSTcorp CDDVDW SH-S223F  SB00 PQ: 0 ANSI: 5
[    6.038381] scsi 2:0:0:0: Direct-Access     ATA      WDC WD3200AAKS-0 01.0 PQ: 0 ANSI: 5
[    6.038470] scsi 3:0:0:0: Direct-Access     ATA      WDC WD6400AAKS-2 01.0 PQ: 0 ANSI: 5
[    6.038622] pata_amd 0000:00:06.0: version 0.3.10
[    6.038676] pata_amd 0000:00:06.0: setting latency timer to 64
[    6.038763] scsi4 : pata_amd
[    6.038850] scsi5 : pata_amd
[    6.039787] ata5: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    6.039790] ata6: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    6.202923] ata6: port disabled. ignoring.
[    6.216417] scsi 1:0:0:0: Attached scsi generic sg0 type 5
[    6.216452] scsi 2:0:0:0: Attached scsi generic sg1 type 0
[    6.216667] scsi 3:0:0:0: Attached scsi generic sg2 type 0
[    6.230485] Driver 'sd' needs updating - please use bus_type methods
[    6.230609] sd 2:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
[    6.230622] sd 2:0:0:0: [sda] Write Protect is off
[    6.230625] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    6.230644] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.230709] sd 2:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
[    6.230720] sd 2:0:0:0: [sda] Write Protect is off
[    6.230722] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    6.230740] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.230744]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[    6.239151]  sda1 sda2 <sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    6.242043] Uniform CD-ROM driver Revision: 3.20
[    6.242130] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    6.246031]  sda5 sda6 >
[    6.255338] sd 2:0:0:0: [sda] Attached SCSI disk
[    6.255401] sd 3:0:0:0: [sdb] 1250263728 512-byte hardware sectors (640135 MB)
[    6.255414] sd 3:0:0:0: [sdb] Write Protect is off
[    6.255416] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    6.255436] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.255478] sd 3:0:0:0: [sdb] 1250263728 512-byte hardware sectors (640135 MB)
[    6.255489] sd 3:0:0:0: [sdb] Write Protect is off
[    6.255491] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    6.255510] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.255513]  sdb: sdb1
[    6.260142] sd 3:0:0:0: [sdb] Attached SCSI disk
[    6.482938] PM: Starting manual resume from disk
[    6.482941] PM: Resume from partition 8:5
[    6.482943] PM: Checking hibernation image.
[    6.483080] PM: Resume from disk failed.
[    6.519361] kjournald starting.  Commit interval 5 seconds
[    6.519371] EXT3-fs: mounted filesystem with ordered data mode.
[    7.733199] udevd version 124 started
[    8.206515] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    8.277989] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    8.689434] Linux agpgart interface v0.103
[    8.749706] Linux video capture interface: v2.00
[    8.780246] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input4
[    8.800539] ACPI: Power Button (FF) [PWRF]
[    8.800679] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input5
[    8.832540] ACPI: Power Button (CM) [PWRB]
[    8.958670] cx88/2: cx2388x MPEG-TS Driver Manager version 0.0.6 loaded
[    8.960416] cx88[0]: subsystem: 107d:6f2b, board: WinFast DTV2000 H [card=51,insmod option], frontend(s): 1
[    8.960419] cx88[0]: TV tuner type 63, Radio tuner type -1
[    9.108103] nvidia: module license 'NVIDIA' taints kernel.
[    9.425510] cx88/0: cx2388x v4l2 driver version 0.0.6 loaded
[    9.472256] tuner' 0-0061: chip found @ 0xc2 (cx88[0])
[    9.473005] tuner' 0-0063: chip found @ 0xc6 (cx88[0])
[    9.479272] lirc_dev: IR Remote Control driver registered, major 61 
[    9.562567] input: PC Speaker as /devices/platform/pcspkr/input/input6
[    9.571239] 
[    9.571242] lirc_mceusb2: Philips eHome USB IR Transceiver and Microsoft MCE 2005 Remote Control driver for LIRC $Revision: 1.44 $
[    9.571245] lirc_mceusb2: Daniel Melander <lirc@rajidae.se>, Martin Blatter <martin_a_blatter@yahoo.com>
[    9.588560] parport_pc 00:05: reported by Plug and Play ACPI
[    9.588604] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[    9.597018] cx2388x alsa driver version 0.0.6 loaded
[    9.633313] ACPI: WMI: Mapper loaded
[    9.708018] tuner-simple 0-0061: creating new instance
[    9.708023] tuner-simple 0-0061: type set to 63 (Philips FMD1216ME MK3 Hybrid Tuner)
[    9.708683] input: cx88 IR (WinFast DTV2000 H) as /devices/pci0000:00/0000:00:08.0/0000:01:06.2/input/input7
[    9.808538] usb 3-2: reset full speed USB device using ohci_hcd and address 2
[    9.844643] cx88[0]/2: cx2388x 8802 Driver Manager
[    9.845095] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 19
[    9.845107] cx88-mpeg driver manager 0000:01:06.2: PCI INT A -> Link[LNKA] -> GSI 19 (level, low) -> IRQ 19
[    9.845115] cx88[0]/2: found at 0000:01:06.2, rev: 5, irq: 19, latency: 64, mmio: 0xdd000000
[    9.849311] cx88[1]: subsystem: 107d:6f2b, board: WinFast DTV2000 H [card=51,insmod option], frontend(s): 1
[    9.849315] cx88[1]: TV tuner type 63, Radio tuner type -1
[    9.971920] tuner' 1-0061: chip found @ 0xc2 (cx88[1])
[    9.972620] tuner' 1-0063: chip found @ 0xc6 (cx88[1])
[   10.037338] lirc_dev: lirc_register_plugin: sample_rate: 0
[   10.038087] tuner-simple 1-0061: creating new instance
[   10.038092] tuner-simple 1-0061: type set to 63 (Philips FMD1216ME MK3 Hybrid Tuner)
[   10.038758] input: cx88 IR (WinFast DTV2000 H) as /devices/pci0000:00/0000:00:08.0/0000:01:07.2/input/input8
[   10.043046] lirc_mceusb2[2]: Topseed Technology Corp. eHome Infrared Transceiver on usb3:2
[   10.043107] usbcore: registered new interface driver lirc_mceusb2
[   10.079539] cx88[1]/2: cx2388x 8802 Driver Manager
[   10.079981] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 18
[   10.079993] cx88-mpeg driver manager 0000:01:07.2: PCI INT A -> Link[LNKB] -> GSI 18 (level, low) -> IRQ 18
[   10.080002] cx88[1]/2: found at 0000:01:07.2, rev: 5, irq: 18, latency: 64, mmio: 0xda000000
[   10.080544] ACPI: PCI Interrupt Link [SGRU] enabled at IRQ 21
[   10.080547] nvidia 0000:00:12.0: PCI INT A -> Link[SGRU] -> GSI 21 (level, low) -> IRQ 21
[   10.080552] nvidia 0000:00:12.0: setting latency timer to 64
[   10.080828] NVRM: loading NVIDIA UNIX x86 Kernel Module  173.14.12  Thu Jul 17 18:11:36 PDT 2008
[   10.081991] cx8800 0000:01:06.0: PCI INT A -> Link[LNKA] -> GSI 19 (level, low) -> IRQ 19
[   10.082001] cx88[0]/0: found at 0000:01:06.0, rev: 5, irq: 19, latency: 64, mmio: 0xdf000000
[   10.082154] cx88[0]/0: registered device video0 [v4l2]
[   10.082191] cx88[0]/0: registered device vbi0
[   10.082308] cx88[0]/0: registered device radio0
[   10.085390] cx88_audio 0000:01:06.1: PCI INT A -> Link[LNKA] -> GSI 19 (level, low) -> IRQ 19
[   10.085419] cx88[0]/1: CX88x/0: ALSA support for cx2388x boards
[   10.085805] cx8800 0000:01:07.0: PCI INT A -> Link[LNKB] -> GSI 18 (level, low) -> IRQ 18
[   10.085810] cx88[1]/0: found at 0000:01:07.0, rev: 5, irq: 18, latency: 64, mmio: 0xdc000000
[   10.085932] cx88[1]/0: registered device video1 [v4l2]
[   10.085978] cx88[1]/0: registered device vbi1
[   10.086025] cx88[1]/0: registered device radio1
[   10.086871] cx88_audio 0000:01:07.1: PCI INT A -> Link[LNKB] -> GSI 18 (level, low) -> IRQ 18
[   10.086887] cx88[1]/1: CX88x/1: ALSA support for cx2388x boards
[   10.235840] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 20
[   10.235846] HDA Intel 0000:00:07.0: PCI INT A -> Link[LAZA] -> GSI 20 (level, low) -> IRQ 20
[   10.235867] HDA Intel 0000:00:07.0: setting latency timer to 64
[   10.255842] cx88/2: cx2388x dvb driver version 0.0.6 loaded
[   10.255846] cx88/2: registering cx8802 driver, type: dvb access: shared
[   10.255850] cx88[0]/2: subsystem: 107d:6f2b, board: WinFast DTV2000 H [card=51]
[   10.255853] cx88[0]/2: cx2388x based DVB/ATSC card
[   10.255855] cx8802_alloc_frontends() allocating 1 frontend(s)
[   10.309242] tuner-simple 0-0061: attaching existing instance
[   10.309249] tuner-simple 0-0061: type set to 63 (Philips FMD1216ME MK3 Hybrid Tuner)
[   10.310905] DVB: registering new adapter (cx88[0])
[   10.310908] DVB: registering adapter 0 frontend -1 (Conexant CX22702 DVB-T)...
[   10.311366] cx88[1]/2: subsystem: 107d:6f2b, board: WinFast DTV2000 H [card=51]
[   10.311369] cx88[1]/2: cx2388x based DVB/ATSC card
[   10.311371] cx8802_alloc_frontends() allocating 1 frontend(s)
[   10.315579] tuner-simple 1-0061: attaching existing instance
[   10.315583] tuner-simple 1-0061: type set to 63 (Philips FMD1216ME MK3 Hybrid Tuner)
[   10.317260] DVB: registering new adapter (cx88[1])
[   10.317262] DVB: registering adapter 1 frontend -1 (Conexant CX22702 DVB-T)...
[   10.587087] phy0: Selected rate control algorithm 'pid'
[   10.735431] Registered led device: rt73usb-phy0:radio
[   10.735448] Registered led device: rt73usb-phy0:assoc
[   10.735462] Registered led device: rt73usb-phy0:quality
[   10.735965] usbcore: registered new interface driver rt73usb
[   10.767847] udev: renamed network interface wlan0 to wlan3
[   11.070398] lp0: using parport0 (interrupt-driven).
[   11.272434] Adding 995988k swap on /dev/sda5.  Priority:-1 extents:1 across:995988k
[   11.564408] EXT3 FS on sda1, internal journal
[   11.942298] SGI XFS with ACLs, security attributes, realtime, large block numbers, no debug enabled
[   11.943657] SGI XFS Quota Management subsystem
[   11.984169] XFS mounting filesystem sda6
[   12.102871] Ending clean XFS mount for filesystem: sda6
[   12.160576] XFS mounting filesystem sdb1
[   12.281546] Ending clean XFS mount for filesystem: sdb1
[   12.838332] type=1505 audit(1234509482.795:2): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4458
[   12.838565] type=1505 audit(1234509482.795:3): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4458
[   12.928358] type=1505 audit(1234509482.883:4): operation="profile_load" name="/usr/sbin/mysqld" name2="default" pid=4462
[   13.103867] ip_tables: (C) 2000-2006 Netfilter Core Team
[   13.594527] RPC: Registered udp transport module.
[   13.594531] RPC: Registered tcp transport module.
[   14.813048] powernow-k8: Found 1 AMD Athlon(tm) 64 X2 Dual Core Processor 5000+ processors (2 cpu cores) (version 2.20.00)
[   14.813105] powernow-k8:    0 : fid 0x12 (2600 MHz), vid 0x8
[   14.813109] powernow-k8:    1 : fid 0x10 (2400 MHz), vid 0xa
[   14.813111] powernow-k8:    2 : fid 0xe (2200 MHz), vid 0xc
[   14.813113] powernow-k8:    3 : fid 0xc (2000 MHz), vid 0xe
[   14.813115] powernow-k8:    4 : fid 0xa (1800 MHz), vid 0x10
[   14.813117] powernow-k8:    5 : fid 0x2 (1000 MHz), vid 0x12
[   14.813358] powernow-k8: ph2 null fid transition 0x12
[   15.717620] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   16.060257] NET: Registered protocol family 10
[   16.061177] lo: Disabled Privacy Extensions
[   16.922816] ppdev: user-space parallel port driver
[   22.126805] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
[   22.211113] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[   22.259485] NFSD: starting 90-second grace period
[   24.050776] Bluetooth: Core ver 2.13
[   24.050842] NET: Registered protocol family 31
[   24.050844] Bluetooth: HCI device and connection manager initialized
[   24.050848] Bluetooth: HCI socket layer initialized
[   24.063571] Bluetooth: L2CAP ver 2.11
[   24.063577] Bluetooth: L2CAP socket layer initialized
[   24.068527] Bluetooth: RFCOMM socket layer initialized
[   24.068548] Bluetooth: RFCOMM TTY layer initialized
[   24.068550] Bluetooth: RFCOMM ver 1.10
[   24.108270] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   24.108277] Bluetooth: BNEP filters: protocol multicast
[   24.129065] Bridge firewalling registered
[   24.190563] Bluetooth: SCO (Voice Link) ver 0.6
[   24.190571] Bluetooth: SCO socket layer initialized
[   28.272985] eth0: no link during initialization.
[   28.273929] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   28.276189] firmware: requesting rt73.bin
[   28.429588] ADDRCONF(NETDEV_UP): wlan3: link is not ready
[   28.476641] NET: Registered protocol family 17
[   30.500015] Clocksource tsc unstable (delta = -76920739 ns)
[   35.181509] wlan3: authenticate with AP 00:13:d3:7e:0e:81
[   35.380539] wlan3: authenticate with AP 00:13:d3:7e:0e:81
[   35.580532] wlan3: authenticate with AP 00:13:d3:7e:0e:81
[   35.784519] wlan3: authentication with AP 00:13:d3:7e:0e:81 timed out
[   45.991004] wlan3: authenticate with AP 00:13:d3:7e:0e:81
[   45.993506] wlan3: authenticated
[   45.993518] wlan3: associate with AP 00:13:d3:7e:0e:81
[   45.995737] wlan3: RX AssocResp from 00:13:d3:7e:0e:81 (capab=0x411 status=0 aid=1)
[   45.995744] wlan3: associated
[   45.996449] ADDRCONF(NETDEV_CHANGE): wlan3: link becomes ready
[   56.668550] wlan3: no IPv6 routers present

```

---

### Post by laffinet on 2009-02-16
bump

---

### Post by laffinet on 2009-02-17
I should probably mention that I'm running Mythbuntu 8.10

When this occurs I have no sound whatsoever, regardless of being within MythTV Frontened or anywhere else on the system (say VLC or so).

---

### Post by kansasnoob on 2009-02-17
[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

---

### Post by laffinet on 2009-02-17
I'm assuiming you're telling me to follow the steps outlined in that guide :)

Will it work for Mythbuntu too ? 

I noticed that the guide does backup the current configuration files. If something goes seriously wrong, how do I revert the changes ?

---

### Post by Crafty Kisses on 2009-02-17
Have you updated recently?

---

### Post by laffinet on 2009-02-17
Yep, I'm fully up to date.

---

### Post by Crafty Kisses on 2009-02-17
Next time you don't have any sound, run the following command:
```
alsamixer
```
See if all the volumes are up and what not.

---

### Post by laffinet on 2009-02-17
Checked that, they are.

I have a suspicion though that alsamixe showed different controls when sound wasn't working. Have to compare next time it doesn't work.

---

### Post by handy on 2009-02-18
I would go here:

*_[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)_*

---

### Post by Mister.Vash on 2009-02-18
Next time sound is working, could you post the dmesg for that?  From what I see, it looks like you have a card using the CX23880 driver.  I saw a while ago, but can't find it now, that sometimes that gets set as you output card.  So a comparison may show that.  Also, if you grep /var/log/udev for the word sound in both cases, it might give a better idea of what is loading one time and what is not loading the other.

---

### Post by laffinet on 2009-02-18
> **Mister.Vash said:**
> Next time sound is working, could you post the dmesg for that?  From what I see, it looks like you have a card using the CX23880 driver.  I saw a while ago, but can't find it now, that sometimes that gets set as you output card.  So a comparison may show that.  Also, if you grep /var/log/udev for the word sound in both cases, it might give a better idea of what is loading one time and what is not loading the other.

The dmesg in my original post is from when sound isn't working. I will post a dmesg from when it's working later today.

I will also post an alsa mixer screenshot of both working/non working when it happens again. 
From memory, alsa mixer shows only two controls when sound isn't working (master & something else, some input I think), while I have quiete a few more controls when sound is working. Also, the device is different (CXsomething when it's not working, will post what it is when it's working, on board chipset is VT1708B).

Will do a /var/log/udev for both scenarios as well.

---

### Post by laffinet on 2009-02-19
OK, attached are files for

udev no sound
alsamixer screenshot no sound

and

udev with sound
alsamixer with sound

Below is dmesg with sound working:

```
dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.27-11-generic (buildd@rothera) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Thu Jan 29 19:24:39 UTC 2009 (Ubuntu 2.6.27-11.27-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e2000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000b7fa0000 (usable)
[    0.000000]  BIOS-e820: 00000000b7fa0000 - 00000000b7fae000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000b7fae000 - 00000000b7fe0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000b7fe0000 - 00000000b7fee000 (reserved)
[    0.000000]  BIOS-e820: 00000000b7ff0000 - 00000000b8000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fef00000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] DMI present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working it around.
[    0.000000] last_pfn = 0xb7fa0 max_arch_pfn = 0x100000
[    0.000000] kernel direct mapping tables up to 38000000 @ 10000-15000
[    0.000000] RAMDISK: 37819000 - 37fef8ef
[    0.000000] ACPI: RSDP 000FB720, 0024 (r2 ACPIAM)
[    0.000000] ACPI: XSDT B7FA0100, 005C (r1 071808 XSDT1351 20080718 MSFT       97)
[    0.000000] ACPI: FACP B7FA0290, 00F4 (r3 071808 FACP1351 20080718 MSFT       97)
[    0.000000] ACPI: DSDT B7FA0450, 7362 (r1  A1059 A1059000        0 INTL 20051117)
[    0.000000] ACPI: FACS B7FAE000, 0040
[    0.000000] ACPI: APIC B7FA0390, 0080 (r1 071808 APIC1351 20080718 MSFT       97)
[    0.000000] ACPI: MCFG B7FA0410, 003C (r1 071808 OEMMCFG  20080718 MSFT       97)
[    0.000000] ACPI: OEMB B7FAE040, 0071 (r1 071808 OEMB1351 20080718 MSFT       97)
[    0.000000] ACPI: HPET B7FA77C0, 0038 (r1 071808 OEMHPET0 20080718 MSFT       97)
[    0.000000] ACPI: NVHD B7FAE0C0, 0554 (r1 071808  NVHDCP  20080718 MSFT       97)
[    0.000000] ACPI: SSDT B7FA7800, 028A (r1 A_M_I_ POWERNOW        1 AMD         1)
[    0.000000] 2047MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 38000000
[    0.000000]   low ram: 00000000 - 38000000
[    0.000000]   bootmap 00011000 - 00018000
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 0038000000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00005c29e0]    TEXT DATA BSS ==> [0000100000 - 00005c29e0]
[    0.000000]   #4 [0037819000 - 0037fef8ef]          RAMDISK ==> [0037819000 - 0037fef8ef]
[    0.000000]   #5 [00005c3000 - 00005c6000]    INIT_PG_TABLE ==> [00005c3000 - 00005c6000]
[    0.000000]   #6 [000009f000 - 0000100000]    BIOS reserved ==> [000009f000 - 0000100000]
[    0.000000]   #7 [0000010000 - 0000011000]          PGTABLE ==> [0000010000 - 0000011000]
[    0.000000]   #8 [0000011000 - 0000018000]          BOOTMAP ==> [0000011000 - 0000018000]
[    0.000000] found SMP MP-table at [c00ff780] 000ff780
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x00038000
[    0.000000]   HighMem  0x00038000 -> 0x000b7fa0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x000b7fa0
[    0.000000] On node 0 totalpages: 753455
[    0.000000] free_area_init_node: node 0, pgdat c048c680, node_mem_map c1000240
[    0.000000]   DMA zone: 3947 pages, LIFO batch:0
[    0.000000]   Normal zone: 223300 pages, LIFO batch:31
[    0.000000]   HighMem zone: 519584 pages, LIFO batch:31
[    0.000000] Detected use of extended apic ids on hypertransport bus
[    0.000000] ACPI: PM-Timer IO Port: 0x508
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e2000
[    0.000000] PM: Registered nosave memory: 00000000000e2000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at c0000000 (gap: b8000000:46c00000)
[    0.000000] PERCPU: Allocating 41628 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 4, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 746831
[    0.000000] Kernel command line: root=UUID=d9905ae1-0b35-4e76-a97f-ac0b7363fefe ro quiet nosplash 
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Extended CMOS year: 2000
[    0.000000] TSC: PIT calibration confirmed by PMTIMER.
[    0.000000] TSC: using PIT calibration value
[    0.000000] Detected 2600.198 MHz processor.
[    0.004000] spurious 8259A interrupt: IRQ7.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] Memory: 2972524k/3014272k available (2576k kernel code, 40440k reserved, 1165k data, 424k init, 2096768k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xf8800000 - 0xff3fe000   ( 107 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[    0.004000]       .init : 0xc04ad000 - 0xc0517000   ( 424 kB)
[    0.004000]       .data : 0xc03840da - 0xc04a7680   (1165 kB)
[    0.004000]       .text : 0xc0100000 - 0xc03840da   (2576 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] CPA: page pool initialized 1 of 1 pages preallocated
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.004000] hpet clockevent registered
[    0.004000] Calibrating delay loop (skipped), value calculated using timer frequency.. 5200.39 BogoMIPS (lpj=10400792)
[    0.004000] Security Framework initialized
[    0.004000] SELinux:  Disabled at boot.
[    0.004000] AppArmor: AppArmor initialized
[    0.004000] Mount-cache hash table entries: 512
[    0.004000] Initializing cgroup subsys ns
[    0.004000] Initializing cgroup subsys cpuacct
[    0.004000] Initializing cgroup subsys memory
[    0.004000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.004000] CPU 0(2) -> Core 0
[    0.004000] using C1E aware idle routine
[    0.004000] Checking 'hlt' instruction... OK.
[    0.017339] ACPI: Core revision 20080609
[    0.019689] ACPI: Checking initramfs for custom DSDT
[    0.286927] ENABLING IO-APIC IRQs
[    0.287152] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.326847] CPU0: AMD Athlon(tm) 64 X2 Dual Core Processor 5000+ stepping 02
[    0.328020] Booting processor 1/1 ip 6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 5200.54 BogoMIPS (lpj=10401090)
[    0.004000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.004000] CPU 1(2) -> Core 1
[    0.412213] CPU1: AMD Athlon(tm) 64 X2 Dual Core Processor 5000+ stepping 02
[    0.412236] Brought up 2 CPUs
[    0.412239] Total of 2 processors activated (10400.94 BogoMIPS).
[    0.412274] CPU0 attaching sched-domain:
[    0.412276]  domain 0: span 0-1 level CPU
[    0.412278]   groups: 0 1
[    0.412283] CPU1 attaching sched-domain:
[    0.412284]  domain 0: span 0-1 level CPU
[    0.412287]   groups: 1 0
[    0.412342] net_namespace: 840 bytes
[    0.412342] Booting paravirtualized kernel on bare hardware
[    0.412342] Time:  6:08:42  Date: 02/19/09
[    0.412342] NET: Registered protocol family 16
[    0.412342] EISA bus registered
[    0.412342] ACPI: bus type pci registered
[    0.412342] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.412342] PCI: Not using MMCONFIG.
[    0.412695] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=8
[    0.412697] PCI: Using configuration type 1 for base access
[    0.412713] mtrr: your CPUs had inconsistent fixed MTRR settings
[    0.412713] mtrr: probably your BIOS does not setup all CPUs.
[    0.412713] mtrr: corrected configuration.
[    0.412813] ACPI: EC: Look up EC in DSDT
[    0.427282] ACPI: Interpreter enabled
[    0.427286] ACPI: (supports S0 S1 S3 S4 S5)
[    0.427301] ACPI: Using IOAPIC for interrupt routing
[    0.427355] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.434073] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
[    0.434076] PCI: Using MMCONFIG for extended config space
[    0.444216] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.444216] PCI: 0000:00:01.0 reg 10 io port: [900, 9ff]
[    0.444216] PCI: 0000:00:01.1 reg 10 io port: [ec00, ec3f]
[    0.444216] PCI: 0000:00:01.1 reg 20 io port: [600, 63f]
[    0.444216] PCI: 0000:00:01.1 reg 24 io port: [700, 73f]
[    0.444219] pci 0000:00:01.1: PME# supported from D3hot D3cold
[    0.444224] pci 0000:00:01.1: PME# disabled
[    0.444243] PCI: 0000:00:02.0 reg 10 32bit mmio: [d9fff000, d9ffffff]
[    0.444262] pci 0000:00:02.0: supports D1
[    0.444263] pci 0000:00:02.0: supports D2
[    0.444265] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.444268] pci 0000:00:02.0: PME# disabled
[    0.444286] PCI: 0000:00:02.1 reg 10 32bit mmio: [d9ffec00, d9ffecff]
[    0.444307] pci 0000:00:02.1: supports D1
[    0.444308] pci 0000:00:02.1: supports D2
[    0.444310] pci 0000:00:02.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.444313] pci 0000:00:02.1: PME# disabled
[    0.444332] PCI: 0000:00:04.0 reg 10 32bit mmio: [d9ffd000, d9ffdfff]
[    0.444351] pci 0000:00:04.0: supports D1
[    0.444352] pci 0000:00:04.0: supports D2
[    0.444354] pci 0000:00:04.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.444357] pci 0000:00:04.0: PME# disabled
[    0.444375] PCI: 0000:00:04.1 reg 10 32bit mmio: [d9ffe800, d9ffe8ff]
[    0.444397] pci 0000:00:04.1: supports D1
[    0.444398] pci 0000:00:04.1: supports D2
[    0.444400] pci 0000:00:04.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.444403] pci 0000:00:04.1: PME# disabled
[    0.444429] PCI: 0000:00:06.0 reg 20 io port: [ffa0, ffaf]
[    0.444458] PCI: 0000:00:07.0 reg 10 32bit mmio: [d9ff8000, d9ffbfff]
[    0.444479] pci 0000:00:07.0: PME# supported from D3hot D3cold
[    0.444482] pci 0000:00:07.0: PME# disabled
[    0.444521] PCI: 0000:00:09.0 reg 10 io port: [e480, e487]
[    0.444524] PCI: 0000:00:09.0 reg 14 io port: [e400, e403]
[    0.444527] PCI: 0000:00:09.0 reg 18 io port: [e080, e087]
[    0.444530] PCI: 0000:00:09.0 reg 1c io port: [e000, e003]
[    0.444533] PCI: 0000:00:09.0 reg 20 io port: [dc00, dc0f]
[    0.444536] PCI: 0000:00:09.0 reg 24 32bit mmio: [d9ff6000, d9ff7fff]
[    0.444569] PCI: 0000:00:0a.0 reg 10 32bit mmio: [d9ffc000, d9ffcfff]
[    0.444572] PCI: 0000:00:0a.0 reg 14 io port: [d880, d887]
[    0.444575] PCI: 0000:00:0a.0 reg 18 32bit mmio: [d9ffe400, d9ffe4ff]
[    0.444579] PCI: 0000:00:0a.0 reg 1c 32bit mmio: [d9ffe000, d9ffe00f]
[    0.444594] pci 0000:00:0a.0: supports D1
[    0.444595] pci 0000:00:0a.0: supports D2
[    0.444597] pci 0000:00:0a.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.444601] pci 0000:00:0a.0: PME# disabled
[    0.444623] pci 0000:00:0b.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.444625] pci 0000:00:0b.0: PME# disabled
[    0.444646] pci 0000:00:0c.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.444649] pci 0000:00:0c.0: PME# disabled
[    0.444669] pci 0000:00:0d.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.444672] pci 0000:00:0d.0: PME# disabled
[    0.444692] pci 0000:00:0e.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.444694] pci 0000:00:0e.0: PME# disabled
[    0.444715] pci 0000:00:0f.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.444717] pci 0000:00:0f.0: PME# disabled
[    0.444739] pci 0000:00:10.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.444742] pci 0000:00:10.0: PME# disabled
[    0.444762] pci 0000:00:11.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.444765] pci 0000:00:11.0: PME# disabled
[    0.444776] PCI: 0000:00:12.0 reg 10 32bit mmio: [d8000000, d8ffffff]
[    0.444780] PCI: 0000:00:12.0 reg 14 64bit mmio: [c0000000, cfffffff]
[    0.444784] PCI: 0000:00:12.0 reg 1c 64bit mmio: [d7000000, d7ffffff]
[    0.444789] PCI: 0000:00:12.0 reg 30 32bit mmio: [d9fc0000, d9fdffff]
[    0.444879] PCI: 0000:01:06.0 reg 10 32bit mmio: [df000000, dfffffff]
[    0.444923] PCI: 0000:01:06.1 reg 10 32bit mmio: [de000000, deffffff]
[    0.444966] PCI: 0000:01:06.2 reg 10 32bit mmio: [dd000000, ddffffff]
[    0.445019] PCI: 0000:01:07.0 reg 10 32bit mmio: [dc000000, dcffffff]
[    0.445063] PCI: 0000:01:07.1 reg 10 32bit mmio: [db000000, dbffffff]
[    0.445106] PCI: 0000:01:07.2 reg 10 32bit mmio: [da000000, daffffff]
[    0.445158] pci 0000:00:08.0: transparent bridge
[    0.445162] PCI: bridge 0000:00:08.0 32bit mmio: [da000000, dfffffff]
[    0.445404] bus 00 -> node 0
[    0.445410] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.445648] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.445790] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR10._PRT]
[    0.445900] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR11._PRT]
[    0.464305] ACPI: PCI Interrupt Link [LNKA] (IRQs 16 17 18 19) *11
[    0.464576] ACPI: PCI Interrupt Link [LNKB] (IRQs 16 17 18 19) *11
[    0.464840] ACPI: PCI Interrupt Link [LNKC] (IRQs 16 17 18 19) *0, disabled.
[    0.465104] ACPI: PCI Interrupt Link [LNKD] (IRQs 16 17 18 19) *0, disabled.
[    0.465368] ACPI: PCI Interrupt Link [LNEA] (IRQs 16 17 18 19) *0, disabled.
[    0.465633] ACPI: PCI Interrupt Link [LNEB] (IRQs 16 17 18 19) *0, disabled.
[    0.465897] ACPI: PCI Interrupt Link [LNEC] (IRQs 16 17 18 19) *0, disabled.
[    0.466161] ACPI: PCI Interrupt Link [LNED] (IRQs 16 17 18 19) *0, disabled.
[    0.466431] ACPI: PCI Interrupt Link [LUB0] (IRQs 20 21 22 23) *11
[    0.466703] ACPI: PCI Interrupt Link [LUB2] (IRQs 20 21 22 23) *10
[    0.466972] ACPI: PCI Interrupt Link [LMAC] (IRQs 20 21 22 23) *10
[    0.467241] ACPI: PCI Interrupt Link [LAZA] (IRQs 20 21 22 23) *11
[    0.467511] ACPI: PCI Interrupt Link [SGRU] (IRQs 20 21 22 23) *11
[    0.468229] ACPI: PCI Interrupt Link [LSMB] (IRQs 20 21 22 23) *10
[    0.468495] ACPI: PCI Interrupt Link [LPMU] (IRQs 20 21 22 23) *0, disabled.
[    0.468767] ACPI: PCI Interrupt Link [LSA0] (IRQs 20 21 22 23) *15
[    0.469078] ACPI: PCI Interrupt Link [LATA] (IRQs 20 21 22 23) *0, disabled.
[    0.469360] ACPI: PCI Interrupt Link [UB11] (IRQs 20 21 22 23) *11
[    0.469632] ACPI: PCI Interrupt Link [UB12] (IRQs 20 21 22 23) *11
[    0.469687] ACPI Warning (tbutils-0217): Incorrect checksum in table [OEMB] - 6D, should be 60 [20080609]
[    0.469687] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.469687] pnp: PnP ACPI init
[    0.469687] ACPI: bus type pnp registered
[    0.473598] pnp 00:06: io resource (0x900-0x97f) overlaps 0000:00:01.0 BAR 0 (0x900-0x9ff), disabling
[    0.473598] pnp 00:06: io resource (0x980-0x9ff) overlaps 0000:00:01.0 BAR 0 (0x900-0x9ff), disabling
[    0.477421] pnp: PnP ACPI: found 14 devices
[    0.477423] ACPI: ACPI bus type pnp unregistered
[    0.477426] PnPBIOS: Disabled by ACPI PNP
[    0.477442] PCI: Using ACPI for IRQ routing
[    0.484039] NET: Registered protocol family 8
[    0.484041] NET: Registered protocol family 20
[    0.484055] NetLabel: Initializing
[    0.484056] NetLabel:  domain hash size = 128
[    0.484058] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.484073] NetLabel:  unlabeled traffic allowed by default
[    0.484080] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 31
[    0.484084] hpet0: 3 32-bit timers, 25000000 Hz
[    0.486052] tracer: 772 pages allocated for 65536 entries of 48 bytes
[    0.486054]    actual entries 65620
[    0.486199] AppArmor: AppArmor Filesystem Enabled
[    0.486227] ACPI: RTC can wake from S4
[    0.488045] Switched to high resolution mode on CPU 0
[    0.488254] Switched to high resolution mode on CPU 1
[    0.492035] system 00:06: ioport range 0x4d0-0x4d1 has been reserved
[    0.492038] system 00:06: ioport range 0x800-0x80f has been reserved
[    0.492040] system 00:06: ioport range 0x500-0x57f has been reserved
[    0.492043] system 00:06: ioport range 0x580-0x5ff has been reserved
[    0.492045] system 00:06: ioport range 0x800-0x87f could not be reserved
[    0.492048] system 00:06: ioport range 0x880-0x8ff has been reserved
[    0.492050] system 00:06: ioport range 0xd00-0xd7f has been reserved
[    0.492053] system 00:06: ioport range 0xd80-0xdff has been reserved
[    0.492055] system 00:06: ioport range 0x1100-0x117f has been reserved
[    0.492058] system 00:06: ioport range 0x1180-0x11ff has been reserved
[    0.492062] system 00:06: iomem range 0xfefe0000-0xfefe01ff has been reserved
[    0.492064] system 00:06: iomem range 0xfefe1000-0xfefe1fff has been reserved
[    0.492067] system 00:06: iomem range 0xfee01000-0xfeefffff could not be reserved
[    0.492074] system 00:09: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.492077] system 00:09: iomem range 0xfee00000-0xfee00fff could not be reserved
[    0.492079] system 00:09: iomem range 0xb8000000-0xbfffffff has been reserved
[    0.492084] system 00:0a: ioport range 0x230-0x23f has been reserved
[    0.492087] system 00:0a: ioport range 0x290-0x29f has been reserved
[    0.492089] system 00:0a: ioport range 0xa00-0xa0f has been reserved
[    0.492092] system 00:0a: ioport range 0xa10-0xa1f has been reserved
[    0.492098] system 00:0c: iomem range 0xe0000000-0xefffffff has been reserved
[    0.492103] system 00:0d: iomem range 0x0-0x9ffff could not be reserved
[    0.492106] system 00:0d: iomem range 0xc0000-0xcffff could not be reserved
[    0.492108] system 00:0d: iomem range 0xe0000-0xfffff could not be reserved
[    0.492111] system 00:0d: iomem range 0x100000-0xb7ffffff could not be reserved
[    0.492114] system 00:0d: iomem range 0xfec00000-0xffffffff could not be reserved
[    0.527330] pci 0000:00:08.0: PCI bridge, secondary bus 0000:01
[    0.527332] pci 0000:00:08.0:   IO window: disabled
[    0.527336] pci 0000:00:08.0:   MEM window: 0xda000000-0xdfffffff
[    0.527339] pci 0000:00:08.0:   PREFETCH window: disabled
[    0.527342] pci 0000:00:0b.0: PCI bridge, secondary bus 0000:02
[    0.527344] pci 0000:00:0b.0:   IO window: disabled
[    0.527346] pci 0000:00:0b.0:   MEM window: disabled
[    0.527349] pci 0000:00:0b.0:   PREFETCH window: disabled
[    0.527352] pci 0000:00:0c.0: PCI bridge, secondary bus 0000:03
[    0.527353] pci 0000:00:0c.0:   IO window: disabled
[    0.527356] pci 0000:00:0c.0:   MEM window: disabled
[    0.527358] pci 0000:00:0c.0:   PREFETCH window: disabled
[    0.527361] pci 0000:00:0d.0: PCI bridge, secondary bus 0000:04
[    0.527362] pci 0000:00:0d.0:   IO window: disabled
[    0.527365] pci 0000:00:0d.0:   MEM window: disabled
[    0.527367] pci 0000:00:0d.0:   PREFETCH window: disabled
[    0.527370] pci 0000:00:0e.0: PCI bridge, secondary bus 0000:05
[    0.527372] pci 0000:00:0e.0:   IO window: disabled
[    0.527374] pci 0000:00:0e.0:   MEM window: disabled
[    0.527376] pci 0000:00:0e.0:   PREFETCH window: disabled
[    0.527379] pci 0000:00:0f.0: PCI bridge, secondary bus 0000:06
[    0.527381] pci 0000:00:0f.0:   IO window: disabled
[    0.527383] pci 0000:00:0f.0:   MEM window: disabled
[    0.527385] pci 0000:00:0f.0:   PREFETCH window: disabled
[    0.527388] pci 0000:00:10.0: PCI bridge, secondary bus 0000:07
[    0.527390] pci 0000:00:10.0:   IO window: disabled
[    0.527392] pci 0000:00:10.0:   MEM window: disabled
[    0.527394] pci 0000:00:10.0:   PREFETCH window: disabled
[    0.527397] pci 0000:00:11.0: PCI bridge, secondary bus 0000:08
[    0.527399] pci 0000:00:11.0:   IO window: disabled
[    0.527401] pci 0000:00:11.0:   MEM window: disabled
[    0.527403] pci 0000:00:11.0:   PREFETCH window: disabled
[    0.527412] pci 0000:00:08.0: setting latency timer to 64
[    0.527416] pci 0000:00:0b.0: setting latency timer to 64
[    0.527420] pci 0000:00:0c.0: setting latency timer to 64
[    0.527424] pci 0000:00:0d.0: setting latency timer to 64
[    0.527427] pci 0000:00:0e.0: setting latency timer to 64
[    0.527431] pci 0000:00:0f.0: setting latency timer to 64
[    0.527434] pci 0000:00:10.0: setting latency timer to 64
[    0.527438] pci 0000:00:11.0: setting latency timer to 64
[    0.527440] bus: 00 index 0 io port: [0, ffff]
[    0.527442] bus: 00 index 1 mmio: [0, ffffffff]
[    0.527444] bus: 01 index 0 mmio: [0, 0]
[    0.527446] bus: 01 index 1 mmio: [da000000, dfffffff]
[    0.527447] bus: 01 index 2 mmio: [0, 0]
[    0.527449] bus: 01 index 3 io port: [0, ffff]
[    0.527451] bus: 01 index 4 mmio: [0, ffffffff]
[    0.527452] bus: 02 index 0 mmio: [0, 0]
[    0.527454] bus: 02 index 1 mmio: [0, 0]
[    0.527456] bus: 02 index 2 mmio: [0, 0]
[    0.527457] bus: 02 index 3 mmio: [0, 0]
[    0.527459] bus: 03 index 0 mmio: [0, 0]
[    0.527460] bus: 03 index 1 mmio: [0, 0]
[    0.527462] bus: 03 index 2 mmio: [0, 0]
[    0.527463] bus: 03 index 3 mmio: [0, 0]
[    0.527465] bus: 04 index 0 mmio: [0, 0]
[    0.527466] bus: 04 index 1 mmio: [0, 0]
[    0.527468] bus: 04 index 2 mmio: [0, 0]
[    0.527469] bus: 04 index 3 mmio: [0, 0]
[    0.527471] bus: 05 index 0 mmio: [0, 0]
[    0.527473] bus: 05 index 1 mmio: [0, 0]
[    0.527474] bus: 05 index 2 mmio: [0, 0]
[    0.527476] bus: 05 index 3 mmio: [0, 0]
[    0.527477] bus: 06 index 0 mmio: [0, 0]
[    0.527479] bus: 06 index 1 mmio: [0, 0]
[    0.527481] bus: 06 index 2 mmio: [0, 0]
[    0.527482] bus: 06 index 3 mmio: [0, 0]
[    0.527484] bus: 07 index 0 mmio: [0, 0]
[    0.527485] bus: 07 index 1 mmio: [0, 0]
[    0.527487] bus: 07 index 2 mmio: [0, 0]
[    0.527488] bus: 07 index 3 mmio: [0, 0]
[    0.527490] bus: 08 index 0 mmio: [0, 0]
[    0.527491] bus: 08 index 1 mmio: [0, 0]
[    0.527493] bus: 08 index 2 mmio: [0, 0]
[    0.527494] bus: 08 index 3 mmio: [0, 0]
[    0.527506] NET: Registered protocol family 2
[    0.540060] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.540334] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.541062] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.541445] TCP: Hash tables configured (established 131072 bind 65536)
[    0.541448] TCP reno registered
[    0.548097] NET: Registered protocol family 1
[    0.548214] checking if image is initramfs... it is
[    1.093961] Freeing initrd memory: 8026k freed
[    1.094901] audit: initializing netlink socket (disabled)
[    1.094920] type=2000 audit(1235023722.092:1): initialized
[    1.099657] highmem bounce pool size: 64 pages
[    1.099663] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.101870] VFS: Disk quotas dquot_6.5.1
[    1.101950] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.102041] msgmni has been set to 1727
[    1.102149] io scheduler noop registered
[    1.102151] io scheduler anticipatory registered
[    1.102153] io scheduler deadline registered
[    1.102163] io scheduler cfq registered (default)
[    1.102194] pci 0000:00:00.0: Enabling HT MSI Mapping
[    1.148558] pci 0000:00:07.0: Enabling HT MSI Mapping
[    1.148573] pci 0000:00:08.0: Enabling HT MSI Mapping
[    1.148599] pci 0000:00:0a.0: Enabling HT MSI Mapping
[    1.148613] pci 0000:00:0b.0: Enabling HT MSI Mapping
[    1.148627] pci 0000:00:0c.0: Enabling HT MSI Mapping
[    1.148642] pci 0000:00:0d.0: Enabling HT MSI Mapping
[    1.148656] pci 0000:00:0e.0: Enabling HT MSI Mapping
[    1.148670] pci 0000:00:0f.0: Enabling HT MSI Mapping
[    1.148685] pci 0000:00:10.0: Enabling HT MSI Mapping
[    1.148699] pci 0000:00:11.0: Enabling HT MSI Mapping
[    1.148713] pci 0000:00:12.0: Boot video device
[    1.148829] pcieport-driver 0000:00:0b.0: setting latency timer to 64
[    1.148851] pcieport-driver 0000:00:0b.0: found MSI capability
[    1.148870] pci_express 0000:00:0b.0:pcie00: allocate port service
[    1.148913] pci_express 0000:00:0b.0:pcie03: allocate port service
[    1.148982] pcieport-driver 0000:00:0c.0: setting latency timer to 64
[    1.149002] pcieport-driver 0000:00:0c.0: found MSI capability
[    1.149016] pci_express 0000:00:0c.0:pcie00: allocate port service
[    1.149058] pci_express 0000:00:0c.0:pcie03: allocate port service
[    1.149124] pcieport-driver 0000:00:0d.0: setting latency timer to 64
[    1.149144] pcieport-driver 0000:00:0d.0: found MSI capability
[    1.149158] pci_express 0000:00:0d.0:pcie00: allocate port service
[    1.149198] pci_express 0000:00:0d.0:pcie03: allocate port service
[    1.149266] pcieport-driver 0000:00:0e.0: setting latency timer to 64
[    1.149286] pcieport-driver 0000:00:0e.0: found MSI capability
[    1.149300] pci_express 0000:00:0e.0:pcie00: allocate port service
[    1.149341] pci_express 0000:00:0e.0:pcie03: allocate port service
[    1.149405] pcieport-driver 0000:00:0f.0: setting latency timer to 64
[    1.149424] pcieport-driver 0000:00:0f.0: found MSI capability
[    1.149439] pci_express 0000:00:0f.0:pcie00: allocate port service
[    1.149481] pci_express 0000:00:0f.0:pcie03: allocate port service
[    1.149544] pcieport-driver 0000:00:10.0: setting latency timer to 64
[    1.149564] pcieport-driver 0000:00:10.0: found MSI capability
[    1.149578] pci_express 0000:00:10.0:pcie00: allocate port service
[    1.149620] pci_express 0000:00:10.0:pcie03: allocate port service
[    1.149686] pcieport-driver 0000:00:11.0: setting latency timer to 64
[    1.149706] pcieport-driver 0000:00:11.0: found MSI capability
[    1.149720] pci_express 0000:00:11.0:pcie00: allocate port service
[    1.149761] pci_express 0000:00:11.0:pcie03: allocate port service
[    1.150071] isapnp: Scanning for PnP cards...
[    1.503455] isapnp: No Plug & Play device found
[    1.534965] hpet_resources: 0xfed00000 is busy
[    1.535062] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.535187] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.535843] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.537576] brd: module loaded
[    1.537640] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    1.537803] PNP: No PS/2 controller found. Probing ports directly.
[    1.538186] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.538191] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.538469] mice: PS/2 mouse device common for all mice
[    1.538588] rtc_cmos 00:08: rtc core: registered rtc_cmos as rtc0
[    1.538622] rtc0: alarms up to one year, y3k, hpet irqs
[    1.538755] EISA: Probing bus 0 at eisa.0
[    1.538779] EISA: Detected 0 cards.
[    1.538782] cpuidle: using governor ladder
[    1.538784] cpuidle: using governor menu
[    1.539225] TCP cubic registered
[    1.539254] Using IPI No-Shortcut mode
[    1.539437] registered taskstats version 1
[    1.539576]   Magic number: 13:101:115
[    1.539778] rtc_cmos 00:08: setting system clock to 2009-02-19 06:08:43 UTC (1235023723)
[    1.539781] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.539783] EDD information not available.
[    1.540080] Freeing unused kernel memory: 424k freed
[    1.540132] Write protecting the kernel text: 2580k
[    1.540164] Write protecting the kernel read-only data: 940k
[    1.653773] fuse init (API version 7.9)
[    1.675082] processor ACPI0007:00: registered as cooling_device0
[    1.675353] processor ACPI0007:01: registered as cooling_device1
[    1.948745] usbcore: registered new interface driver usbfs
[    1.948768] usbcore: registered new interface driver hub
[    1.948791] usbcore: registered new device driver usb
[    1.950401] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.950853] ACPI: PCI Interrupt Link [LUB0] enabled at IRQ 23
[    1.950864] ohci_hcd 0000:00:02.0: PCI INT A -> Link[LUB0] -> GSI 23 (level, low) -> IRQ 23
[    1.950878] ohci_hcd 0000:00:02.0: setting latency timer to 64
[    1.950880] ohci_hcd 0000:00:02.0: OHCI Host Controller
[    1.950929] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
[    1.951057] ohci_hcd 0000:00:02.0: irq 23, io mem 0xd9fff000
[    1.961870] Warning! ehci_hcd should always be loaded before uhci_hcd and ohci_hcd, not after
[    1.981770] No dock devices found.
[    2.000686] SCSI subsystem initialized
[    2.015305] usb usb1: configuration #1 chosen from 1 choice
[    2.015331] hub 1-0:1.0: USB hub found
[    2.015343] hub 1-0:1.0: 6 ports detected
[    2.015747] libata version 3.00 loaded.
[    2.220857] ACPI: PCI Interrupt Link [UB11] enabled at IRQ 22
[    2.220870] ohci_hcd 0000:00:04.0: PCI INT A -> Link[UB11] -> GSI 22 (level, low) -> IRQ 22
[    2.220885] ohci_hcd 0000:00:04.0: setting latency timer to 64
[    2.220888] ohci_hcd 0000:00:04.0: OHCI Host Controller
[    2.220913] ohci_hcd 0000:00:04.0: new USB bus registered, assigned bus number 2
[    2.220937] ohci_hcd 0000:00:04.0: irq 22, io mem 0xd9ffd000
[    2.278186] usb usb2: configuration #1 chosen from 1 choice
[    2.278213] hub 2-0:1.0: USB hub found
[    2.278224] hub 2-0:1.0: 6 ports detected
[    2.396021] usb 1-2: new full speed USB device using ohci_hcd and address 2
[    2.484961] ACPI: PCI Interrupt Link [LUB2] enabled at IRQ 21
[    2.484973] ehci_hcd 0000:00:02.1: PCI INT B -> Link[LUB2] -> GSI 21 (level, low) -> IRQ 21
[    2.484985] ehci_hcd 0000:00:02.1: setting latency timer to 64
[    2.484988] ehci_hcd 0000:00:02.1: EHCI Host Controller
[    2.485014] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 3
[    2.485039] ehci_hcd 0000:00:02.1: debug port 1
[    2.485043] ehci_hcd 0000:00:02.1: cache line size of 64 is not supported
[    2.485058] ehci_hcd 0000:00:02.1: irq 21, io mem 0xd9ffec00
[    2.600014] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    2.600151] usb usb3: configuration #1 chosen from 1 choice
[    2.600174] hub 3-0:1.0: USB hub found
[    2.600183] hub 3-0:1.0: 6 ports detected
[    2.808884] ACPI: PCI Interrupt Link [UB12] enabled at IRQ 20
[    2.808896] ehci_hcd 0000:00:04.1: PCI INT B -> Link[UB12] -> GSI 20 (level, low) -> IRQ 20
[    2.808908] ehci_hcd 0000:00:04.1: setting latency timer to 64
[    2.808911] ehci_hcd 0000:00:04.1: EHCI Host Controller
[    2.808939] ehci_hcd 0000:00:04.1: new USB bus registered, assigned bus number 4
[    2.808964] ehci_hcd 0000:00:04.1: debug port 1
[    2.808967] ehci_hcd 0000:00:04.1: cache line size of 64 is not supported
[    2.808983] ehci_hcd 0000:00:04.1: irq 20, io mem 0xd9ffe800
[    2.820012] ehci_hcd 0000:00:04.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    2.820108] usb usb4: configuration #1 chosen from 1 choice
[    2.820135] hub 4-0:1.0: USB hub found
[    2.820142] hub 4-0:1.0: 6 ports detected
[    2.996018] usb 1-2: device not accepting address 2, error -62
[    3.028545] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
[    3.028975] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 23
[    3.028980] forcedeth 0000:00:0a.0: PCI INT A -> Link[LMAC] -> GSI 23 (level, low) -> IRQ 23
[    3.028984] forcedeth 0000:00:0a.0: setting latency timer to 64
[    3.052020] hub 1-0:1.0: unable to enumerate USB device on port 2
[    3.093089] forcedeth 0000:00:0a.0: ifname eth0, PHY OUI 0x732 @ 3, addr 00:22:15:d4:b9:c6
[    3.093093] forcedeth 0000:00:0a.0: highdma pwrctl mgmt timirq gbit lnktim msi desc-v3
[    3.098880] ahci 0000:00:09.0: version 3.0
[    3.099300] ACPI: PCI Interrupt Link [LSA0] enabled at IRQ 22
[    3.099305] ahci 0000:00:09.0: PCI INT A -> Link[LSA0] -> GSI 22 (level, low) -> IRQ 22
[    3.099373] ahci 0000:00:09.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl IDE mode
[    3.099376] ahci 0000:00:09.0: flags: 64bit ncq sntf led clo pmp pio 
[    3.099379] ahci 0000:00:09.0: setting latency timer to 64
[    3.101845] scsi0 : ahci
[    3.101965] scsi1 : ahci
[    3.102504] scsi2 : ahci
[    3.102563] scsi3 : ahci
[    3.102645] ata1: SATA max UDMA/133 abar m8192@0xd9ff6000 port 0xd9ff6100 irq 22
[    3.102647] ata2: SATA max UDMA/133 irq_stat 0x00400040, connection status changed
[    3.102650] ata3: SATA max UDMA/133 irq_stat 0x00400040, connection status changed
[    3.102652] ata4: SATA max UDMA/133 irq_stat 0x00400040, connection status changed
[    3.420018] ata1: SATA link down (SStatus 0 SControl 300)
[    3.676014] usb 3-2: new high speed USB device using ehci_hcd and address 2
[    3.969954] usb 3-2: configuration #1 chosen from 1 choice
[    4.312015] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    4.312870] ata2.00: ATAPI: TSSTcorp CDDVDW SH-S223F, SB00, max UDMA/100, ATAPI AN
[    4.313818] ata2.00: configured for UDMA/100
[    4.496012] usb 2-2: new full speed USB device using ohci_hcd and address 2
[    4.708044] usb 2-2: config 1 interface 0 altsetting 0 endpoint 0x1 has an invalid bInterval 0, changing to 32
[    4.708047] usb 2-2: config 1 interface 0 altsetting 0 endpoint 0x82 has an invalid bInterval 0, changing to 32
[    4.720426] usb 2-2: configuration #1 chosen from 1 choice
[    5.024015] usb 2-3: new low speed USB device using ohci_hcd and address 3
[    5.200023] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    5.200808] ata3.00: ATA-8: WDC WD3200AAKS-00B3A0, 01.03A01, max UDMA/133
[    5.200811] ata3.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    5.201677] ata3.00: configured for UDMA/133
[    5.238416] usb 2-3: configuration #1 chosen from 1 choice
[    5.544016] usb 1-3: new low speed USB device using ohci_hcd and address 4
[    5.759521] usb 1-3: configuration #1 chosen from 1 choice
[    5.762425] usbcore: registered new interface driver hiddev
[    5.770340] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:04.0/usb2/2-3/2-3:1.0/input/input1
[    5.773075] input,hidraw0: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:04.0-3
[    5.779462] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:02.0/usb1/1-3/1-3:1.0/input/input2
[    5.780094] input,hidraw1: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:02.0-3
[    5.791252] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:02.0/usb1/1-3/1-3:1.1/input/input3
[    5.791524] input,hidraw2: USB HID v1.10 Device [Logitech USB Receiver] on usb-0000:00:02.0-3
[    5.791544] usbcore: registered new interface driver usbhid
[    5.791548] usbhid: v2.6:USB HID core driver
[    6.088015] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    6.088845] ata4.00: ATA-8: WDC WD6400AAKS-22A7B0, 01.03B01, max UDMA/133
[    6.088849] ata4.00: 1250263728 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    6.089741] ata4.00: configured for UDMA/133
[    6.090313] scsi 1:0:0:0: CD-ROM            TSSTcorp CDDVDW SH-S223F  SB00 PQ: 0 ANSI: 5
[    6.090444] scsi 2:0:0:0: Direct-Access     ATA      WDC WD3200AAKS-0 01.0 PQ: 0 ANSI: 5
[    6.090532] scsi 3:0:0:0: Direct-Access     ATA      WDC WD6400AAKS-2 01.0 PQ: 0 ANSI: 5
[    6.090682] pata_amd 0000:00:06.0: version 0.3.10
[    6.090732] pata_amd 0000:00:06.0: setting latency timer to 64
[    6.090820] scsi4 : pata_amd
[    6.090905] scsi5 : pata_amd
[    6.091848] ata5: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    6.091850] ata6: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    6.254921] ata6: port disabled. ignoring.
[    6.268565] scsi 1:0:0:0: Attached scsi generic sg0 type 5
[    6.268602] scsi 2:0:0:0: Attached scsi generic sg1 type 0
[    6.268808] scsi 3:0:0:0: Attached scsi generic sg2 type 0
[    6.283771] Driver 'sd' needs updating - please use bus_type methods
[    6.283904] sd 2:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
[    6.283920] sd 2:0:0:0: [sda] Write Protect is off
[    6.283922] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    6.283943] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.284029] sd 2:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
[    6.284040] sd 2:0:0:0: [sda] Write Protect is off
[    6.284042] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    6.284060] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.284065]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[    6.291203] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    6.291207] Uniform CD-ROM driver Revision: 3.20
[    6.291285] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    6.299305]  sda1 sda2 < sda5 sda6 >
[    6.315556] sd 2:0:0:0: [sda] Attached SCSI disk
[    6.315622] sd 3:0:0:0: [sdb] 1250263728 512-byte hardware sectors (640135 MB)
[    6.315637] sd 3:0:0:0: [sdb] Write Protect is off
[    6.315639] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    6.315659] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.315711] sd 3:0:0:0: [sdb] 1250263728 512-byte hardware sectors (640135 MB)
[    6.315722] sd 3:0:0:0: [sdb] Write Protect is off
[    6.315724] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    6.315743] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.315747]  sdb: sdb1
[    6.325352] sd 3:0:0:0: [sdb] Attached SCSI disk
[    6.581170] PM: Starting manual resume from disk
[    6.581174] PM: Resume from partition 8:5
[    6.581175] PM: Checking hibernation image.
[    6.581309] PM: Resume from disk failed.
[    6.621218] kjournald starting.  Commit interval 5 seconds
[    6.621238] EXT3-fs: mounted filesystem with ordered data mode.
[    7.835045] udevd version 124 started
[    8.309837] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    8.360221] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    8.584168] Linux video capture interface: v2.00
[    8.708733] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input4
[    8.732525] ACPI: Power Button (FF) [PWRF]
[    8.732634] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input5
[    8.770364] ACPI: Power Button (CM) [PWRB]
[    9.006639] cx88/0: cx2388x v4l2 driver version 0.0.6 loaded
[    9.007532] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 19
[    9.007544] cx8800 0000:01:06.0: PCI INT A -> Link[LNKA] -> GSI 19 (level, low) -> IRQ 19
[    9.013000] cx88[0]: subsystem: 107d:6f2b, board: WinFast DTV2000 H [card=51,insmod option], frontend(s): 1
[    9.013004] cx88[0]: TV tuner type 63, Radio tuner type -1
[    9.016772] cx88/2: cx2388x MPEG-TS Driver Manager version 0.0.6 loaded
[    9.109835] parport_pc 00:05: reported by Plug and Play ACPI
[    9.109879] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[    9.144056] ACPI: WMI: Mapper loaded
[    9.344692] lirc_dev: IR Remote Control driver registered, major 61 
[    9.456677] 
[    9.456681] lirc_mceusb2: Philips eHome USB IR Transceiver and Microsoft MCE 2005 Remote Control driver for LIRC $Revision: 1.44 $
[    9.456684] lirc_mceusb2: Daniel Melander <lirc@rajidae.se>, Martin Blatter <martin_a_blatter@yahoo.com>
[    9.481093] Linux agpgart interface v0.103
[    9.569986] tuner' 0-0043: chip found @ 0x86 (cx88[0])
[    9.630823] tda9887 0-0043: creating new instance
[    9.630828] tda9887 0-0043: tda988[5/6/7] found
[    9.631698] input: PC Speaker as /devices/platform/pcspkr/input/input6
[    9.638744] tuner' 0-0061: chip found @ 0xc2 (cx88[0])
[    9.639439] tuner' 0-0063: chip found @ 0xc6 (cx88[0])
[    9.740533] usb 2-2: reset full speed USB device using ohci_hcd and address 2
[    9.863456] nvidia: module license 'NVIDIA' taints kernel.
[   10.157040] lirc_dev: lirc_register_plugin: sample_rate: 0
[   10.163031] lirc_mceusb2[2]: Topseed Technology Corp. eHome Infrared Transceiver on usb2:2
[   10.163078] usbcore: registered new interface driver lirc_mceusb2
[   10.315752] cx2388x alsa driver version 0.0.6 loaded
[   10.353551] tuner-simple 0-0061: creating new instance
[   10.353556] tuner-simple 0-0061: type set to 63 (Philips FMD1216ME MK3 Hybrid Tuner)
[   10.355323] input: cx88 IR (WinFast DTV2000 H) as /devices/pci0000:00/0000:00:08.0/0000:01:06.0/input/input7
[   10.384716] cx88[0]/0: found at 0000:01:06.0, rev: 5, irq: 19, latency: 64, mmio: 0xdf000000
[   10.384798] cx88[0]/0: registered device video0 [v4l2]
[   10.384840] cx88[0]/0: registered device vbi0
[   10.384881] cx88[0]/0: registered device radio0
[   10.388174] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 18
[   10.388187] cx8800 0000:01:07.0: PCI INT A -> Link[LNKB] -> GSI 18 (level, low) -> IRQ 18
[   10.388751] cx88[1]: subsystem: 107d:6f2b, board: WinFast DTV2000 H [card=51,insmod option], frontend(s): 1
[   10.388753] cx88[1]: TV tuner type 63, Radio tuner type -1
[   10.514061] tuner' 1-0043: chip found @ 0x86 (cx88[1])
[   10.514119] tda9887 1-0043: creating new instance
[   10.514121] tda9887 1-0043: tda988[5/6/7] found
[   10.516481] tuner' 1-0061: chip found @ 0xc2 (cx88[1])
[   10.517177] tuner' 1-0063: chip found @ 0xc6 (cx88[1])
[   10.561267] tuner-simple 1-0061: creating new instance
[   10.561271] tuner-simple 1-0061: type set to 63 (Philips FMD1216ME MK3 Hybrid Tuner)
[   10.563152] input: cx88 IR (WinFast DTV2000 H) as /devices/pci0000:00/0000:00:08.0/0000:01:07.0/input/input8
[   10.588687] cx88[1]/0: found at 0000:01:07.0, rev: 5, irq: 18, latency: 64, mmio: 0xdc000000
[   10.588756] cx88[1]/0: registered device video1 [v4l2]
[   10.588790] cx88[1]/0: registered device vbi1
[   10.588821] cx88[1]/0: registered device radio1
[   10.590201] cx88[0]/2: cx2388x 8802 Driver Manager
[   10.590217] cx88-mpeg driver manager 0000:01:06.2: PCI INT A -> Link[LNKA] -> GSI 19 (level, low) -> IRQ 19
[   10.590224] cx88[0]/2: found at 0000:01:06.2, rev: 5, irq: 19, latency: 64, mmio: 0xdd000000
[   10.594237] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 21
[   10.594244] HDA Intel 0000:00:07.0: PCI INT A -> Link[LAZA] -> GSI 21 (level, low) -> IRQ 21
[   10.594272] HDA Intel 0000:00:07.0: setting latency timer to 64
[   10.594328] cx88[1]/2: cx2388x 8802 Driver Manager
[   10.594336] cx88-mpeg driver manager 0000:01:07.2: PCI INT A -> Link[LNKB] -> GSI 18 (level, low) -> IRQ 18
[   10.594342] cx88[1]/2: found at 0000:01:07.2, rev: 5, irq: 18, latency: 64, mmio: 0xda000000
[   10.616141] phy0: Selected rate control algorithm 'pid'
[   10.662209] ACPI: PCI Interrupt Link [SGRU] enabled at IRQ 20
[   10.662215] nvidia 0000:00:12.0: PCI INT A -> Link[SGRU] -> GSI 20 (level, low) -> IRQ 20
[   10.662221] nvidia 0000:00:12.0: setting latency timer to 64
[   10.662764] NVRM: loading NVIDIA UNIX x86 Kernel Module  173.14.12  Thu Jul 17 18:11:36 PDT 2008
[   10.664002] cx88_audio 0000:01:06.1: PCI INT A -> Link[LNKA] -> GSI 19 (level, low) -> IRQ 19
[   10.664032] cx88[0]/1: CX88x/0: ALSA support for cx2388x boards
[   10.664429] cx88_audio 0000:01:07.1: PCI INT A -> Link[LNKB] -> GSI 18 (level, low) -> IRQ 18
[   10.664447] cx88[1]/1: CX88x/1: ALSA support for cx2388x boards
[   10.722280] cx88/2: cx2388x dvb driver version 0.0.6 loaded
[   10.722284] cx88/2: registering cx8802 driver, type: dvb access: shared
[   10.722287] cx88[0]/2: subsystem: 107d:6f2b, board: WinFast DTV2000 H [card=51]
[   10.722290] cx88[0]/2: cx2388x based DVB/ATSC card
[   10.722292] cx8802_alloc_frontends() allocating 1 frontend(s)
[   10.753605] tuner-simple 0-0061: attaching existing instance
[   10.753611] tuner-simple 0-0061: type set to 63 (Philips FMD1216ME MK3 Hybrid Tuner)
[   10.755251] DVB: registering new adapter (cx88[0])
[   10.755254] DVB: registering adapter 0 frontend -136927104 (Conexant CX22702 DVB-T)...
[   10.755665] cx88[1]/2: subsystem: 107d:6f2b, board: WinFast DTV2000 H [card=51]
[   10.755668] cx88[1]/2: cx2388x based DVB/ATSC card
[   10.755670] cx8802_alloc_frontends() allocating 1 frontend(s)
[   10.758247] tuner-simple 1-0061: attaching existing instance
[   10.758250] tuner-simple 1-0061: type set to 63 (Philips FMD1216ME MK3 Hybrid Tuner)
[   10.759884] DVB: registering new adapter (cx88[1])
[   10.759887] DVB: registering adapter 1 frontend -136927620 (Conexant CX22702 DVB-T)...
[   10.766800] Registered led device: rt73usb-phy0:radio
[   10.766815] Registered led device: rt73usb-phy0:assoc
[   10.766829] Registered led device: rt73usb-phy0:quality
[   10.767355] usbcore: registered new interface driver rt73usb
[   10.880845] udev: renamed network interface wlan0 to wlan3
[   11.222294] lp0: using parport0 (interrupt-driven).
[   11.424332] Adding 995988k swap on /dev/sda5.  Priority:-1 extents:1 across:995988k
[   11.688062] EXT3 FS on sda1, internal journal
[   12.027117] SGI XFS with ACLs, security attributes, realtime, large block numbers, no debug enabled
[   12.028887] SGI XFS Quota Management subsystem
[   12.069353] XFS mounting filesystem sda6
[   12.282750] Ending clean XFS mount for filesystem: sda6
[   12.325775] XFS mounting filesystem sdb1
[   12.421261] Ending clean XFS mount for filesystem: sdb1
[   13.046278] type=1505 audit(1235023735.004:2): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4473
[   13.046508] type=1505 audit(1235023735.004:3): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4473
[   13.110627] type=1505 audit(1235023735.068:4): operation="profile_load" name="/usr/sbin/mysqld" name2="default" pid=4477
[   13.255448] ip_tables: (C) 2000-2006 Netfilter Core Team
[   13.813078] RPC: Registered udp transport module.
[   13.813082] RPC: Registered tcp transport module.
[   15.023373] powernow-k8: Found 1 AMD Athlon(tm) 64 X2 Dual Core Processor 5000+ processors (2 cpu cores) (version 2.20.00)
[   15.023430] powernow-k8:    0 : fid 0x12 (2600 MHz), vid 0x8
[   15.023433] powernow-k8:    1 : fid 0x10 (2400 MHz), vid 0xa
[   15.023436] powernow-k8:    2 : fid 0xe (2200 MHz), vid 0xc
[   15.023437] powernow-k8:    3 : fid 0xc (2000 MHz), vid 0xe
[   15.023439] powernow-k8:    4 : fid 0xa (1800 MHz), vid 0x10
[   15.023441] powernow-k8:    5 : fid 0x2 (1000 MHz), vid 0x12
[   15.023682] powernow-k8: ph2 null fid transition 0x12
[   15.894538] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   16.228639] NET: Registered protocol family 10
[   16.229095] lo: Disabled Privacy Extensions
[   17.106934] ppdev: user-space parallel port driver
[   22.147654] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
[   22.220975] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[   22.253062] NFSD: starting 90-second grace period
[   23.577784] tda9887 0-0043: i2c i/o error: rc == -6 (should be 4)
[   23.642924] tda9887 1-0043: i2c i/o error: rc == -6 (should be 4)
[   24.052275] Bluetooth: Core ver 2.13
[   24.052710] NET: Registered protocol family 31
[   24.052712] Bluetooth: HCI device and connection manager initialized
[   24.052716] Bluetooth: HCI socket layer initialized
[   24.065389] Bluetooth: L2CAP ver 2.11
[   24.065398] Bluetooth: L2CAP socket layer initialized
[   24.070457] Bluetooth: RFCOMM socket layer initialized
[   24.070475] Bluetooth: RFCOMM TTY layer initialized
[   24.070476] Bluetooth: RFCOMM ver 1.10
[   24.109917] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   24.109925] Bluetooth: BNEP filters: protocol multicast
[   24.131236] Bridge firewalling registered
[   24.182818] Bluetooth: SCO (Voice Link) ver 0.6
[   24.182824] Bluetooth: SCO socket layer initialized
[   28.280967] eth0: no link during initialization.
[   28.281909] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   28.289503] firmware: requesting rt73.bin
[   28.515589] ADDRCONF(NETDEV_UP): wlan3: link is not ready
[   28.570147] NET: Registered protocol family 17
[   29.500017] Clocksource tsc unstable (delta = -76930797 ns)
[   35.159723] wlan3: authenticate with AP 00:13:d3:7e:0e:81
[   35.163717] wlan3: authenticated
[   35.163731] wlan3: associate with AP 00:13:d3:7e:0e:81
[   35.165866] wlan3: RX AssocResp from 00:13:d3:7e:0e:81 (capab=0x411 status=0 aid=1)
[   35.165873] wlan3: associated
[   35.167047] ADDRCONF(NETDEV_CHANGE): wlan3: link becomes ready
[   45.948518] wlan3: no IPv6 routers present

```

dmesg without sound is in my original post

Hope this helps.

---

### Post by laffinet on 2009-02-20
Bump.

Help, this is really annoying.

---

### Post by laffinet on 2009-02-21
bump

---

### Post by markbuntu on 2009-02-21
What does aplay -l tell you?

---

### Post by laffinet on 2009-02-22
> **markbuntu said:**
> What does aplay -l tell you?

I will post the output next time I'm left without sound.

---

### Post by laffinet on 2009-02-25
Ok, here's my aplay -l when I have no sound (which is no different to when I have sound):

```
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 2: NVidia [HDA NVidia], device 0: VT1708B Analog [VT1708B Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

Sooo, the most obvious difference is in the alsa-mixer (as posted in post #13), which shows completely different devices with sound/without sound. 

Any ideas how to get rid of this problem ?

---

### Post by markbuntu on 2009-02-25
Either you have two sound card/chip devices or your sound device is being misdetected occaisionally. We need some more in depth info. This is how to get it

[http://ubuntuforums.org/showthread.php?p=6628921](http://ubuntuforums.org/showthread.php?p=6628921)

---

### Post by laffinet on 2009-02-25
This in only a guess (slightly educated though :D), but I think what gets wrongly detected as a sound device occasionaly is my TV tuner card.

If I have a look at the alsa-mixer screen shot it shows cx88 when there's no sound.

Compared that with the dmesg and it shows the cx88 here for example:
```
[    8.960416] cx88[0]: subsystem: 107d:6f2b, board: WinFast DTV2000 H [card=51,insmod option], frontend(s): 1

```

Sorry, can't give you an lspci etc. at the moment, not at home.

Sooo, if that chip gets detected as soundcard but shouldn't, what can I do ?

---

### Post by laffinet on 2009-02-26
lspci

```
lspci
00:00.0 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP67 ISA Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP67 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:04.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:04.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP67 IDE Controller (rev a1)
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP67 PCI Bridge (rev a2)
00:09.0 IDE interface: nVidia Corporation MCP67 AHCI Controller (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0d.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0e.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0f.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:10.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:11.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:12.0 VGA compatible controller: nVidia Corporation GeForce 7050 PV / nForce 630a (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:06.0 Multimedia video controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
01:06.1 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [Audio Port] (rev 05)
01:06.2 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)
01:07.0 Multimedia video controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
01:07.1 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [Audio Port] (rev 05)
01:07.2 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)

```

lsusb
```
lsusb
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 003: ID 046d:c501 Logitech, Inc. Cordless Mouse Receiver
Bus 003 Device 002: ID 1784:0008 TopSeed Technology Corp. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 07d1:3c07 D-Link System Wireless G DWA-110 Adapter
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 046d:c503 Logitech, Inc. Cordless Mouse+Keyboard Receiver
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

cat /proc/asound/cards
```
 cat /proc/asound/cards
 0 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xd9ff8000 irq 21
 1 [CX8801         ]: CX88x - Conexant CX8801
                      Conexant CX8801 at 0xde000000
 2 [CX8811         ]: CX88x - Conexant CX8811
                      Conexant CX8811 at 0xdb000000

```

cat /proc/asound/modules
```
cat /proc/asound/modules
 0 snd_hda_intel
 1 cx88_alsa
 2 cx88_alsa

```

aplay -l

```
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: VT1708B Analog [VT1708B Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

arecord -l

```
 arecord -l
**** List of CAPTURE Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: VT1708B Analog [VT1708B Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 1: CX8801 [Conexant CX8801], device 0: CX88 Digital [CX88 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: CX8811 [Conexant CX8811], device 0: CX88 Digital [CX88 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

All this is with sound working.

---

### Post by markbuntu on 2009-02-26
I would bet that the connexant card, which is probably your tv tuner is sometimes seen first and given default status. You would see this in cat /proc/asound/modules which would probably look like this in that case. 

 cat /proc/asound/modules 
 0 cx88_alsa
 1 cx88_alsa
 2 snd_hda_intel


The problem is that pci devices are detected and assigned somewhat randomly. You can go here, where there is an explanation about how to force the order of your cards so the nvidia (snd_hda_intel) is always card 0.

[http://ubuntuforums.org/showthread.php?t=922860](http://ubuntuforums.org/showthread.php?t=922860)

---

### Post by laffinet on 2009-02-27
Okay, this is what I did.

Added the following lines to /etc/modprobe.d/alsa-base
```
options snd_hda_intel index=0
options cx88_alsa index=1
options cx88_alsa index=2
```

That didn't do the trick, though. I'm once again left with no sound and cat /proc/asound/modules shows only this:
```
 
 0 cx88_alsa
 1 cx88_alsa

```

 so I guess the proper device hasn't been loaded. Why ?

Also, my /etc/modprobe.d/alsa-base already contained the line
```
options cx88_alsa index=-2
```
which I commented out.

So why is the right device still not loading as 0 ?

As reference, this is the complete file:

```
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe --quiet snd-ioctl32 ; : ; }
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm && { /sbin/modprobe --quiet snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer && { /sbin/modprobe --quiet snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq && { /sbin/modprobe --quiet snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi && { /sbin/modprobe --quiet snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
# options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from beeing loaded as first soundcard
options snd-pcsp index=-2

# assign default order for sound devices
options snd_hda_intel index=0
options cx88_alsa index=1
options cx88_alsa index=2
```

---

### Post by markbuntu on 2009-02-27
Hmm, that is weird, like the nvidia is not even being detected sometimes. I wonder if it is an irq problem, not likely these days but possible. If the nvidia sound needs a fixed irq and udev has already assigned it....check your bios next time you boot up.

---

### Post by laffinet on 2009-02-27
Can you give me some more detail on what to check in the bios ? Thanks.

---

### Post by laffinet on 2009-03-07
Okay, I had a look at the BIOS and changed one setting:

Plug and Play O/S was set to "NO". I changed it to "Yes", thinking that it might be better for the Operating system to take control of the the PCI devices not needed for boot. Hasn't changed anything, though. Still left without sound sometimes. 

Any more ideas ?

---

### Post by laffinet on 2009-03-17
Anyone ? This is quite an annoying problem...

---

### Post by SunnyRabbiera on 2009-03-17
Are you sure you are not running more sound app at once?

---

### Post by laffinet on 2009-03-17
> **SunnyRabbiera said:**
> Are you sure you are not running more sound app at once?

Like what ? Can you provide more detail.

Also, please note that this doesn't happen all the time, only once in a while. Reboot fixes it.

---

### Post by laffinet on 2009-03-23
Bump

---

### Post by laffinet on 2009-03-24
Help ? Anyone ?

---

### Post by laffinet on 2009-03-25
Oops, another bump in the road...

---

### Post by scott2 on 2009-03-26
maybe your getting overexcited on the matter. its neat to see all this stuff works the first time, but its easy to forget why. sound is very poor on ubuntu, its true. the hp speakers i have are awful, and the volume control on the desktop doesnt do much. whatever plugin your using has to be jacked up to the max just to get something. it probably works and you just dont know it! sometimes if you leave the computer on too long, it will just stop! then you have to restart.

---

### Post by laffinet on 2009-03-28
I don't think I'm getting overexcited over the matter.

Nor are the symptoms you're describing what is happening on my machine.

Issue seems to be that Mythbuntu sometimes recognizes my sound device, sometimes it doesn't. Don't know why, don't know how to fix it.

Someone else maybe ?

---

### Post by miegiel on 2009-03-29
I apologize for not reading the whole thread, but if hardware is sometimes there and sometimes not, it's often power related.

Assuming it's not a laptop go to [http://www.extreme.outervision.com/psucalculatorlite.jsp](http://www.extreme.outervision.com/psucalculatorlite.jsp) and check if your PSU is up to the task. If it is it might be defective.

---

