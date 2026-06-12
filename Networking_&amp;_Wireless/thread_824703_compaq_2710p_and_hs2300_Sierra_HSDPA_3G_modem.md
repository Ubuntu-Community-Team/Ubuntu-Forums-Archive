---
title: "compaq 2710p and hs2300 Sierra HSDPA 3G modem"
date: 2008-06-10
forum: Networking &amp; Wireless
---

### Post by nkostop on 2008-06-10
I have a compaq 2710p with an hs2300 module(MC8775 i think) which is enabled in the bios,has an enabled SIM card inside but doesn't show up and no /dev/ttyUSB is found.

lspci:
```

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:03.0 Communication controller: Intel Corporation Mobile PM965/GM965 MEI Controller (rev 0c)
00:03.2 IDE interface: Intel Corporation Mobile PM965/GM965 PT IDER Controller (rev 0c)
00:03.3 Serial controller: Intel Corporation Mobile PM965/GM965 KT Controller (rev 0c)
00:19.0 Ethernet controller: Intel Corporation 82566MM Gigabit Network Connection (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HBM (ICH8M-E) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
02:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
02:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
02:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev ff)
10:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)

```

lsusb:
```

Bus 007 Device 004: ID 04f2:b017 Chicony Electronics Co., Ltd 
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 004: ID 08ff:2580 AuthenTec, Inc. 
Bus 003 Device 003: ID 045e:007d Microsoft Corp. Notebook Optical Mouse
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 03f0:171d Hewlett-Packard 
Bus 001 Device 001: ID 0000:0000  

```

The ID 03f0:171d Hewlett-Packard is teh bluetooth and WLAN intergrated module

dmesg:
```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-18-generic (buildd@king) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed May 28 19:28:38 UTC 2008 (Ubuntu 2.6.24-18.32-generic)
[    0.000000] Command line: root=UUID=6d02d361-75d2-45ad-b612-ea1f40857d88 ro quiet splash
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007e7b0000 (usable)
[    0.000000]  BIOS-e820: 000000007e7b0000 - 000000007e7c5400 (reserved)
[    0.000000]  BIOS-e820: 000000007e7c5400 - 000000007e7e7fb8 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007e7e7fb8 - 000000007f000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed20000 - 00000000fed9a000 (reserved)
[    0.000000]  BIOS-e820: 00000000feda0000 - 00000000fedc0000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb00000 - 00000000ffc00000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 518064) 1 entries of 3200 used
[    0.000000] end_pfn_map = 1048576
[    0.000000] DMI 2.4 present.
[    0.000000] ACPI: RSDP signature @ 0xFFFF8100000F7820 checksum 0
[    0.000000] ACPI: RSDP 000F7820, 0024 (r2 HP    )
[    0.000000] ACPI: XSDT 7E7C81C8, 007C (r1 HPQOEM SLIC-MPC        1 HP          1)
[    0.000000] ACPI: FACP 7E7C8084, 00F4 (r4 HP     30C8            3 HP          1)
[    0.000000] ACPI: DSDT 7E7C8538, 128DB (r1 HP       nc65xx    10000 MSFT  3000001)
[    0.000000] ACPI: FACS 7E7E7D80, 0040
[    0.000000] ACPI: SLIC 7E7C8244, 0176 (r1 HPQOEM SLIC-MPC        1 HP          1)
[    0.000000] ACPI: HPET 7E7C83BC, 0038 (r1 HP     30C8            1 HP          1)
[    0.000000] ACPI: APIC 7E7C83F4, 0068 (r1 HP     30C8            1 HP          1)
[    0.000000] ACPI: MCFG 7E7C845C, 003C (r1 HP     30C8            1 HP          1)
[    0.000000] ACPI: TCPA 7E7C8498, 0032 (r2 HP     30C8            1 HP          1)
[    0.000000] ACPI: ASF! 7E7C84CC, 0069 (r16 HP     CHIMAYU         1 HP          0)
[    0.000000] ACPI: SSDT 7E7DAE13, 01AB (r1 HP       HPQPAT        1 MSFT  3000001)
[    0.000000] ACPI: SSDT 7E7DB900, 025F (r1 HP      Cpu0Tst     3000 INTL 20060317)
[    0.000000] ACPI: SSDT 7E7DBB5F, 00A6 (r1 HP      Cpu1Tst     3000 INTL 20060317)
[    0.000000] ACPI: SSDT 7E7DBC05, 04D7 (r1 HP        CpuPm     3000 INTL 20060317)
[    0.000000] ACPI: DMI detected: Hewlett-Packard
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-000000007e7b0000
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 518064) 1 entries of 3200 used
[    0.000000] Bootmem setup node 0 0000000000000000-000000007e7b0000
[    0.000000] No mptable found.
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   DMA32        4096 ->  1048576
[    0.000000]   Normal    1048576 ->  1048576
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0:        0 ->      159
[    0.000000]     0:      256 ->   518064
[    0.000000] On node 0 totalpages: 517967
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 1218 pages reserved
[    0.000000]   DMA zone: 2725 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 7026 pages used for memmap
[    0.000000]   DMA32 zone: 506942 pages, LIFO batch:31
[    0.000000]   Normal zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 (Bootup-CPU)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] Processor #1
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Setting APIC routing to flat
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000e0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 7f000000:7fc00000)
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] PERCPU: Allocating 34656 bytes of per cpu data
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 509667
[    0.000000] Policy zone: DMA32
[    0.000000] Kernel command line: root=UUID=6d02d361-75d2-45ad-b612-ea1f40857d88 ro quiet splash
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] Extended CMOS year: 2000
[    0.000000] hpet clockevent registered
[    0.000000] TSC calibrated against HPET
[   18.757564] time.c: Detected 1196.999 MHz processor.
[   18.759006] Console: colour VGA+ 80x25
[   18.759011] console [tty0] enabled
[   18.759037] Checking aperture...
[   18.759053] Calgary: detecting Calgary via BIOS EBDA area
[   18.759056] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[   18.788273] Memory: 2030904k/2072256k available (2488k kernel code, 40964k reserved, 1319k data, 320k init)
[   18.788322] SLUB: Genslabs=12, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   18.867485] Calibrating delay using timer specific routine.. 2397.01 BogoMIPS (lpj=4794035)
[   18.867529] Security Framework initialized
[   18.867537] SELinux:  Disabled at boot.
[   18.867554] AppArmor: AppArmor initialized
[   18.867559] Failure registering capabilities with primary security module.
[   18.867855] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
[   18.869627] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
[   18.870578] Mount-cache hash table entries: 256
[   18.870757] Initializing cgroup subsys ns
[   18.870765] Initializing cgroup subsys cpuacct
[   18.870786] CPU: L1 I cache: 32K, L1 D cache: 32K
[   18.870788] CPU: L2 cache: 2048K
[   18.870791] CPU 0/0 -> Node 0
[   18.870793] using mwait in idle threads.
[   18.870796] CPU: Physical Processor ID: 0
[   18.870798] CPU: Processor Core ID: 0
[   18.870805] CPU0: Thermal monitoring handled by SMI
[   18.870822] SMP alternatives: switching to UP code
[   18.871935] Early unpacking initramfs... done
[   19.394189] ACPI: Core revision 20070126
[   19.394308] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   19.544245] Using local APIC timer interrupts.
[   19.627746] APIC timer calibration result 8312485
[   19.627749] Detected 8.312 MHz APIC timer.
[   19.627858] SMP alternatives: switching to SMP code
[   19.628787] Booting processor 1/2 APIC 0x1
[   19.639237] Initializing CPU#1
[   19.719707] Calibrating delay using timer specific routine.. 2393.98 BogoMIPS (lpj=4787969)
[   19.719716] CPU: L1 I cache: 32K, L1 D cache: 32K
[   19.719719] CPU: L2 cache: 2048K
[   19.719722] CPU 1/1 -> Node 0
[   19.719724] CPU: Physical Processor ID: 0
[   19.719725] CPU: Processor Core ID: 1
[   19.719734] CPU1: Thermal monitoring enabled (TM2)
[   19.720204] Intel(R) Core(TM)2 Duo CPU     U7600  @ 1.20GHz stepping 0d
[   19.720243] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[   19.740267] Brought up 2 CPUs
[   19.740372] CPU0 attaching sched-domain:
[   19.740375]  domain 0: span 03
[   19.740377]   groups: 01 02
[   19.740382]   domain 1: span 03
[   19.740384]    groups: 03
[   19.740387] CPU1 attaching sched-domain:
[   19.740389]  domain 0: span 03
[   19.740391]   groups: 02 01
[   19.740395]   domain 1: span 03
[   19.740397]    groups: 03
[   19.740706] net_namespace: 120 bytes
[   19.741253] Time: 16:18:52  Date: 06/10/08
[   19.741287] NET: Registered protocol family 16
[   19.741569] ACPI: bus type pci registered
[   19.741676] PCI: Using configuration type 1
[   19.744044] ACPI: EC: Look up EC in DSDT
[   19.746677] ACPI: EC: non-query interrupt received, switching to interrupt mode
[   19.806024] ACPI: Interpreter enabled
[   19.806029] ACPI: (supports S0 S3 S4 S5)
[   19.806049] ACPI: Using IOAPIC for interrupt routing
[   19.822137] ACPI: EC: GPE = 0x16, I/O: command/status = 0x66, data = 0x62
[   19.822141] ACPI: EC: driver started in interrupt mode
[   19.822233] ACPI: PCI Root Bridge [C003] (0000:00)
[   19.823752] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[   19.823757] PCI quirk: region 1100-113f claimed by ICH6 GPIO
[   19.824752] PCI: Transparent bridge - 0000:00:1e.0
[   19.824806] ACPI: PCI Interrupt Routing Table [\_SB_.C003._PRT]
[   19.825472] ACPI: PCI Interrupt Routing Table [\_SB_.C003.C0B2._PRT]
[   19.825689] ACPI: PCI Interrupt Routing Table [\_SB_.C003.C11F._PRT]
[   19.825910] ACPI: PCI Interrupt Routing Table [\_SB_.C003.C133._PRT]
[   19.826131] ACPI: PCI Interrupt Routing Table [\_SB_.C003.C134._PRT]
[   19.905908] ACPI: PCI Interrupt Link [C12F] (IRQs *10 11)
[   19.906256] ACPI: PCI Interrupt Link [C130] (IRQs *10 11)
[   19.906598] ACPI: PCI Interrupt Link [C131] (IRQs 10 *11)
[   19.906928] ACPI: PCI Interrupt Link [C132] (IRQs 10 11) *0, disabled.
[   19.907269] ACPI: PCI Interrupt Link [C142] (IRQs 10 *11)
[   19.907597] ACPI: PCI Interrupt Link [C143] (IRQs 10 11) *0, disabled.
[   19.907936] ACPI: PCI Interrupt Link [C144] (IRQs 10 11) *5
[   19.908098] ACPI Exception (pci_link-0184): AE_NOT_FOUND, Evaluating _PRS [20070126]
[   19.908399] ACPI: Power Resource [C299] (on)
[   19.908493] ACPI: Power Resource [C1C9] (off)
[   19.908572] Linux Plug and Play Support v0.97 (c) Adam Belay
[   19.908614] pnp: PnP ACPI init
[   19.908624] ACPI: bus type pnp registered
[   19.922612] pnp: PnP ACPI: found 15 devices
[   19.922615] ACPI: ACPI bus type pnp unregistered
[   19.922951] PCI: Using ACPI for IRQ routing
[   19.922953] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   19.936150] NET: Registered protocol family 8
[   19.936152] NET: Registered protocol family 20
[   19.936202] PCI-GART: No AMD northbridge found.
[   19.936209] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   19.936214] hpet0: 3 64-bit timers, 14318180 Hz
[   19.937274] AppArmor: AppArmor Filesystem Enabled
[   19.939581] Time: tsc clocksource has been installed.
[   19.939596] Switched to high resolution mode on CPU 0
[   19.940142] Switched to high resolution mode on CPU 1
[   19.948569] system 00:00: iomem range 0x0-0x9ffff could not be reserved
[   19.948574] system 00:00: iomem range 0xe0000-0xfffff could not be reserved
[   19.948578] system 00:00: iomem range 0x100000-0x7e7fffff could not be reserved
[   19.948595] system 00:0b: ioport range 0x500-0x55f has been reserved
[   19.948599] system 00:0b: ioport range 0x800-0x80f has been reserved
[   19.948604] system 00:0b: iomem range 0xffb00000-0xffbfffff could not be reserved
[   19.948609] system 00:0b: iomem range 0xfff00000-0xffffffff could not be reserved
[   19.948618] system 00:0d: ioport range 0x4d0-0x4d1 has been reserved
[   19.948622] system 00:0d: ioport range 0x1000-0x107f has been reserved
[   19.948626] system 00:0d: ioport range 0x1100-0x113f has been reserved
[   19.948631] system 00:0d: ioport range 0x1200-0x121f has been reserved
[   19.948635] system 00:0d: iomem range 0xf8000000-0xfbffffff has been reserved
[   19.948640] system 00:0d: iomem range 0xfec00000-0xfec000ff could not be reserved
[   19.948644] system 00:0d: iomem range 0xfed20000-0xfed3ffff could not be reserved
[   19.948649] system 00:0d: iomem range 0xfed45000-0xfed8ffff could not be reserved
[   19.948654] system 00:0d: iomem range 0xfed90000-0xfed99fff could not be reserved
[   19.948662] system 00:0e: iomem range 0xcee00-0xcffff has been reserved
[   19.948666] system 00:0e: iomem range 0xd2000-0xd3fff has been reserved
[   19.948671] system 00:0e: iomem range 0xfeda0000-0xfedbffff could not be reserved
[   19.948675] system 00:0e: iomem range 0xfee00000-0xfee00fff could not be reserved
[   19.949256] PCI: Bridge: 0000:00:1c.0
[   19.949258]   IO window: disabled.
[   19.949265]   MEM window: disabled.
[   19.949270]   PREFETCH window: disabled.
[   19.949277] PCI: Bridge: 0000:00:1c.1
[   19.949279]   IO window: disabled.
[   19.949286]   MEM window: e4000000-e40fffff
[   19.949292]   PREFETCH window: disabled.
[   19.949299] PCI: Bridge: 0000:00:1c.2
[   19.949303]   IO window: 2000-3fff
[   19.949310]   MEM window: e0000000-e3ffffff
[   19.949315]   PREFETCH window: disabled.
[   19.949323] PCI: Bridge: 0000:00:1e.0
[   19.949325]   IO window: disabled.
[   19.949332]   MEM window: e4100000-e43fffff
[   19.949337]   PREFETCH window: disabled.
[   19.949376] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
[   19.949384] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   19.949415] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 17 (level, low) -> IRQ 17
[   19.949422] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   19.949453] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 18
[   19.949461] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   19.949478] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   19.949491] NET: Registered protocol family 2
[   19.992650] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
[   19.993709] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
[   19.997096] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   19.998028] TCP: Hash tables configured (established 262144 bind 65536)
[   19.998032] TCP reno registered
[   20.008726] checking if image is initramfs... it is
[   21.141371] Freeing initrd memory: 7548k freed
[   21.149100] audit: initializing netlink socket (disabled)
[   21.149117] audit(1213114733.200:1): initialized
[   21.152070] VFS: Disk quotas dquot_6.5.1
[   21.152170] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   21.152338] io scheduler noop registered
[   21.152341] io scheduler anticipatory registered
[   21.152343] io scheduler deadline registered
[   21.152484] io scheduler cfq registered (default)
[   21.152498] Boot video device is 0000:00:02.0
[   21.155878] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   21.155949] assign_interrupt_mode Found MSI capability
[   21.156010] Allocate Port Service[0000:00:1c.0:pcie00]
[   21.156145] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   21.156215] assign_interrupt_mode Found MSI capability
[   21.156272] Allocate Port Service[0000:00:1c.1:pcie00]
[   21.156405] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   21.156477] assign_interrupt_mode Found MSI capability
[   21.156534] Allocate Port Service[0000:00:1c.2:pcie00]
[   21.156577] Allocate Port Service[0000:00:1c.2:pcie02]
[   21.191494] Real Time Clock Driver v1.12ac
[   21.191856] hpet_resources: 0xfed00000 is busy
[   21.191932] Linux agpgart interface v0.102
[   21.191935] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   21.192716] 00:02: ttyS0 at I/O 0x200 (irq = 6) is a 16550A
[   21.193070] ACPI: PCI Interrupt 0000:00:03.3[B] -> GSI 17 (level, low) -> IRQ 17
[   21.193188] 0000:00:03.3: ttyS1 at I/O 0x4040 (irq = 17) is a 16550A
[   21.194094] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   21.194191] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   21.194331] PNP: PS/2 Controller [PNP0303:C296,PNP0f13:C297] at 0x60,0x64 irq 1,12
[   21.196283] i8042.c: Detected active multiplexing controller, rev 1.1.
[   21.197054] serio: i8042 KBD port at 0x60,0x64 irq 1
[   21.197059] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[   21.197063] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[   21.197069] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[   21.197072] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[   21.206958] mice: PS/2 mouse device common for all mice
[   21.207010] cpuidle: using governor ladder
[   21.207013] cpuidle: using governor menu
[   21.207201] NET: Registered protocol family 1
[   21.207331] registered taskstats version 1
[   21.207483]   Magic number: 12:717:337
[   21.207497]   hash matches device ttyzc
[   21.207572]   hash matches device tty58
[   21.207611] /build/buildd/linux-2.6.24/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   21.207615] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   21.207617] EDD information not available.
[   21.207626] Freeing unused kernel memory: 320k freed
[   21.228717] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   22.474123] fuse init (API version 7.9)
[   22.498501] ACPI: SSDT 7E7DB086, 01FB (r1 HP      Cpu0Ist     3000 INTL 20060317)
[   22.498876] ACPI: SSDT 7E7DB306, 05FA (r1 HP      Cpu0Cst     3001 INTL 20060317)
[   22.508029] Monitor-Mwait will be used to enter C-1 state
[   22.508034] Monitor-Mwait will be used to enter C-2 state
[   22.508163] ACPI: CPU0 (power states: C1[C1] C2[C2])
[   22.508169] ACPI: Processor [CPU0] (supports 8 throttling states)
[   22.508487] ACPI: SSDT 7E7DAFBE, 00C8 (r1 HP      Cpu1Ist     3000 INTL 20060317)
[   22.508835] ACPI: SSDT 7E7DB281, 0085 (r1 HP      Cpu1Cst     3000 INTL 20060317)
[   22.510620] Marking TSC unstable due to TSC halts in idle
[   22.510702] ACPI: CPU1 (power states: C1[C1] C2[C2])
[   22.510709] ACPI: Processor [CPU1] (supports 8 throttling states)
[   22.513081] ACPI: Thermal Zone [TZ0] (25 C)
[   22.514004] Time: hpet clocksource has been installed.
[   22.517825] ACPI: Thermal Zone [TZ1] (51 C)
[   22.522295] ACPI: Thermal Zone [TZ3] (42 C)
[   22.526189] ACPI: Thermal Zone [TZ4] (34 C)
[   22.989442] SCSI subsystem initialized
[   23.028266] Intel(R) PRO/1000 Network Driver - version 7.3.20-k2-NAPI
[   23.028271] Copyright (c) 1999-2006 Intel Corporation.
[   23.028354] ACPI: PCI Interrupt 0000:00:19.0[A] -> GSI 22 (level, low) -> IRQ 22
[   23.028372] PCI: Setting latency timer of device 0000:00:19.0 to 64
[   23.034622] usbcore: registered new interface driver usbfs
[   23.034656] usbcore: registered new interface driver hub
[   23.034693] usbcore: registered new device driver usb
[   23.035944] USB Universal Host Controller Interface driver v3.0
[   23.056753] e1000: 0000:00:19.0: e1000_probe: (PCI Express:2.5Gb/s:Width x1) 00:1e:0b:57:3f:88
[   23.073892] libata version 3.00 loaded.
[   23.149558] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
[   23.149598] ACPI: PCI Interrupt 0000:00:1a.0[A] -> GSI 16 (level, low) -> IRQ 16
[   23.149614] PCI: Setting latency timer of device 0000:00:1a.0 to 64
[   23.149619] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[   23.149976] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[   23.150016] uhci_hcd 0000:00:1a.0: irq 16, io base 0x00004080
[   23.150190] usb usb1: configuration #1 chosen from 1 choice
[   23.150220] hub 1-0:1.0: USB hub found
[   23.150228] hub 1-0:1.0: 2 ports detected
[   23.251409] ACPI: PCI Interrupt 0000:00:1a.1[B] -> GSI 17 (level, low) -> IRQ 17
[   23.251426] PCI: Setting latency timer of device 0000:00:1a.1 to 64
[   23.251432] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[   23.251461] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
[   23.251500] uhci_hcd 0000:00:1a.1: irq 17, io base 0x000040a0
[   23.251647] usb usb2: configuration #1 chosen from 1 choice
[   23.251679] hub 2-0:1.0: USB hub found
[   23.251686] hub 2-0:1.0: 2 ports detected
[   23.355298] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 20 (level, low) -> IRQ 20
[   23.355315] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   23.355320] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   23.355349] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 3
[   23.355385] uhci_hcd 0000:00:1d.0: irq 20, io base 0x000040c0
[   23.355524] usb usb3: configuration #1 chosen from 1 choice
[   23.355558] hub 3-0:1.0: USB hub found
[   23.355565] hub 3-0:1.0: 2 ports detected
[   23.459250] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 22 (level, low) -> IRQ 22
[   23.459268] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   23.459273] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   23.459305] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 4
[   23.459345] uhci_hcd 0000:00:1d.1: irq 22, io base 0x000040e0
[   23.459518] usb usb4: configuration #1 chosen from 1 choice
[   23.459548] hub 4-0:1.0: USB hub found
[   23.459555] hub 4-0:1.0: 2 ports detected
[   23.491112] usb 1-1: new full speed USB device using uhci_hcd and address 2
[   23.563163] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[   23.563181] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   23.563186] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   23.563215] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 5
[   23.563253] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00004100
[   23.563388] usb usb5: configuration #1 chosen from 1 choice
[   23.563417] hub 5-0:1.0: USB hub found
[   23.563424] hub 5-0:1.0: 2 ports detected
[   23.657924] usb 1-1: configuration #1 chosen from 1 choice
[   23.667296] ACPI: PCI Interrupt 0000:00:1a.7[C] -> GSI 18 (level, low) -> IRQ 18
[   23.668084] PCI: Setting latency timer of device 0000:00:1a.7 to 64
[   23.668092] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[   23.668155] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 6
[   23.672083] ehci_hcd 0000:00:1a.7: debug port 1
[   23.672092] PCI: cache line size of 32 is not supported by device 0000:00:1a.7
[   23.672102] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xe4641000
[   23.686990] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   23.687159] usb usb6: configuration #1 chosen from 1 choice
[   23.687191] hub 6-0:1.0: USB hub found
[   23.687200] hub 6-0:1.0: 4 ports detected
[   23.791055] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 20 (level, low) -> IRQ 20
[   23.791821] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   23.791830] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   23.791893] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 7
[   23.795826] ehci_hcd 0000:00:1d.7: debug port 1
[   23.795834] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   23.795843] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xe4648000
[   23.843539] usb 3-1: new low speed USB device using uhci_hcd and address 2
[   23.844868] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   23.845036] usb usb7: configuration #1 chosen from 1 choice
[   23.845069] hub 7-0:1.0: USB hub found
[   23.845077] hub 7-0:1.0: 6 ports detected
[   23.847207] Clocksource tsc unstable (delta = -91704210 ns)
[   23.853809] ACPI: PCI Interrupt 0000:02:09.0[A] -> GSI 20 (level, low) -> IRQ 20
[   23.906958] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[20]  MMIO=[e4100000-e41007ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[   23.915346] ACPI: PCI Interrupt 0000:00:03.2[C] -> GSI 18 (level, low) -> IRQ 18
[   23.915391] PCI: Setting latency timer of device 0000:00:03.2 to 64
[   23.915405] ACPI: PCI interrupt for device 0000:00:03.2 disabled
[   23.915431] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 16 (level, low) -> IRQ 16
[   23.915459] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   23.915472] ACPI: PCI interrupt for device 0000:00:1f.1 disabled
[   23.918474] ata_piix 0000:00:1f.1: version 2.12
[   23.918492] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 16 (level, low) -> IRQ 16
[   23.918531] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   23.919142] scsi0 : ata_piix
[   23.919827] scsi1 : ata_piix
[   23.920429] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x4120 irq 14
[   23.920433] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x4128 irq 15
[   23.934308] ata1.00: ATA-7: TOSHIBA MK1011GAH, BK001C, max UDMA/100
[   23.934312] ata1.00: 195371568 sectors, multi 16: LBA 
[   23.935255] ata1.00: configured for UDMA/100
[   23.935338] ata2: port disabled. ignoring.
[   23.935503] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK1011GA BK00 PQ: 0 ANSI: 5
[   23.943831] Driver 'sd' needs updating - please use bus_type methods
[   23.943930] sd 0:0:0:0: [sda] 195371568 512-byte hardware sectors (100030 MB)
[   23.943946] sd 0:0:0:0: [sda] Write Protect is off
[   23.943949] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   23.943972] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   23.944039] sd 0:0:0:0: [sda] 195371568 512-byte hardware sectors (100030 MB)
[   23.944053] sd 0:0:0:0: [sda] Write Protect is off
[   23.944056] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   23.944079] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   23.944084]  sda: sda1 < sda5 sda6 sda7 > sda2 sda3
[   23.988427] sd 0:0:0:0: [sda] Attached SCSI disk
[   23.992913] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   24.147724] usb 1-1: USB disconnect, address 2
[   24.387526] usb 1-1: new full speed USB device using uhci_hcd and address 3
[   24.536290] Attempting manual resume
[   24.536294] swsusp: Resume From Partition 8:5
[   24.536296] PM: Checking swsusp image.
[   24.536703] PM: Resume from disk failed.
[   24.564401] usb 1-1: configuration #1 chosen from 1 choice
[   24.598443] kjournald starting.  Commit interval 5 seconds
[   24.598462] EXT3-fs: mounted filesystem with ordered data mode.
[   25.027110] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00023f8429c5540e]
[   25.230025] usb 7-4: new high speed USB device using ehci_hcd and address 4
[   25.373891] usb 7-4: configuration #1 chosen from 1 choice
[   25.613784] usb 3-1: new low speed USB device using uhci_hcd and address 3
[   25.793829] usb 3-1: configuration #1 chosen from 1 choice
[   26.035173] usb 3-2: new full speed USB device using uhci_hcd and address 4
[   26.196638] usb 3-2: configuration #1 chosen from 1 choice
[   38.955382] tpm_inf_pnp 00:03: Found C27D with ID IFX0102
[   38.955443] tpm_inf_pnp 00:03: TPM found: config base 0x560, data base 0x570, chip version 0x000b, vendor id 0x15d1 (Infineon), product id 0x000b (SLB 9635 TT 1.2)
[   39.142933] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   39.182872] iTCO_vendor_support: vendor-support=0
[   39.222852] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   39.222968] iTCO_wdt: Found a ICH8M-E TCO device (Version=2, TCOBASE=0x1060)
[   39.223018] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   39.262883] agpgart: Detected an Intel 965GM Chipset.
[   39.264333] agpgart: Detected 7676K stolen memory.
[   39.279907] agpgart: AGP aperture is 256M @ 0xd0000000
[   39.342893] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   39.391244] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   39.443821] input: Power Button (FF) as /devices/virtual/input/input3
[   39.467976] ACPI: Power Button (FF) [PWRF]
[   39.468170] input: Sleep Button (CM) as /devices/virtual/input/input4
[   39.483949] ACPI: Sleep Button (CM) [C2B7]
[   39.484074] input: Lid Switch as /devices/virtual/input/input5
[   39.660005] ACPI: Lid Switch [C155]
[   39.660572] ACPI: AC Adapter [C23D] (on-line)
[   39.704333] ACPI: Battery Slot [C23F] (battery present)
[   39.704669] ACPI: Battery Slot [C23E] (battery absent)
[   39.705481] ACPI: WMI-Acer: Mapper loaded
[   40.099747] ricoh-mmc: Ricoh MMC Controller disabling driver
[   40.099752] ricoh-mmc: Copyright(c) Philip Langdale
[   40.099815] ricoh-mmc: Ricoh MMC controller found at 0000:02:09.2 [1180:0843] (rev 12)
[   40.099834] ricoh-mmc: Controller is now disabled.
[   40.399497] sdhci: Secure Digital Host Controller Interface driver
[   40.399502] sdhci: Copyright(c) Pierre Ossman
[   40.399571] sdhci: SDHCI controller found at 0000:02:09.1 [1180:0822] (rev 22)
[   40.399599] ACPI: PCI Interrupt 0000:02:09.1[B] -> GSI 22 (level, low) -> IRQ 22
[   40.400338] sdhci:slot0: Will use DMA mode even though HW doesn't fully claim to support it.
[   40.400433] mmc0: SDHCI at 0xe4101000 irq 22 DMA
[   40.613966] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input6
[   40.654278] ACPI: Video Device [C09A] (multi-head: yes  rom: no  post: no)
[   40.981131] input: PS/2 Generic Mouse as /devices/platform/i8042/serio4/input/input7
[   41.060371] iwl4965: Intel(R) Wireless WiFi Link 4965AGN driver for Linux, 1.2.0
[   41.060376] iwl4965: Copyright(c) 2003-2007 Intel Corporation
[   41.060495] ACPI: PCI Interrupt 0000:10:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[   41.060507] PCI: Setting latency timer of device 0000:10:00.0 to 64
[   41.061232] iwl4965: Detected Intel Wireless WiFi Link 4965AGN
[   41.175248] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 17 (level, low) -> IRQ 17
[   41.175977] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   41.407169] Bluetooth: Core ver 2.11
[   41.431091] NET: Registered protocol family 31
[   41.431095] Bluetooth: HCI device and connection manager initialized
[   41.431101] Bluetooth: HCI socket layer initialized
[   41.453230] Bluetooth: HCI USB driver ver 2.9
[   41.454896] usbcore: registered new interface driver hci_usb
[   41.533536] usbcore: registered new interface driver hiddev
[   41.538112] Linux video capture interface: v2.00
[   41.546369] input: Microsoft Microsoft Notebook/Mobile Optical Mouse 2.0 as /devices/pci0000:00/0000:00:1d.0/usb3/3-1/3-1:1.0/input/input8
[   41.706682] input,hidraw0: USB HID v1.10 Mouse [Microsoft Microsoft Notebook/Mobile Optical Mouse 2.0] on usb-0000:00:1d.0-1
[   41.706709] usbcore: registered new interface driver usbhid
[   41.706714] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   41.710054] uvcvideo: Found UVC 1.00 device HP Webcam (04f2:b017)
[   41.747567] usbcore: registered new interface driver uvcvideo
[   41.747572] USB Video Class driver (v0.1.0)
[   43.844483] iwl4965: Tunable channels: 13 802.11bg, 19 802.11a channels
[   43.845067] wmaster0: Selected rate control algorithm 'iwl-4965-rs'
[   44.572271] loop: module loaded
[   44.646497] lp: driver loaded but no devices found
[   44.864354] Adding 3574420k swap on /dev/sda5.  Priority:-1 extents:1 across:3574420k
[   45.417231] EXT3 FS on sda6, internal journal
[   46.281726] ip_tables: (C) 2000-2006 Netfilter Core Team
[   46.949523] No dock devices found.
[   48.690469] ppdev: user-space parallel port driver
[   48.878108] audit(1213103963.054:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5261 profile="/usr/sbin/cupsd" namespace="default"
[   51.955671] Bluetooth: L2CAP ver 2.9
[   51.955679] Bluetooth: L2CAP socket layer initialized
[   52.141391] Bluetooth: RFCOMM socket layer initialized
[   52.141415] Bluetooth: RFCOMM TTY layer initialized
[   52.141419] Bluetooth: RFCOMM ver 1.8
[   54.430302] [drm] Initialized drm 1.1.0 20060810
[   54.433672] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
[   54.433684] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   54.433760] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   66.090249] NET: Registered protocol family 10
[   66.090713] lo: Disabled Privacy Extensions
[   66.091509] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   66.092354] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   76.431904] CPU0 attaching NULL sched-domain.
[   76.431916] CPU1 attaching NULL sched-domain.
[   76.461338] CPU0 attaching sched-domain:
[   76.461349]  domain 0: span 03
[   76.461352]   groups: 01 02
[   76.461357]   domain 1: span 03
[   76.461360]    groups: 03
[   76.461363] CPU1 attaching sched-domain:
[   76.461366]  domain 0: span 03
[   76.461369]   groups: 02 01
[   76.461373]   domain 1: span 03
[   76.461375]    groups: 03
[   80.197633] NET: Registered protocol family 17
[   82.530138] wlan0: Initial auth_alg=0
[   82.530149] wlan0: authenticate with AP 00:0f:66:4c:cd:26
[   82.531995] wlan0: RX authentication from 00:0f:66:4c:cd:26 (alg=0 transaction=2 status=0)
[   82.532002] wlan0: authenticated
[   82.532005] wlan0: associate with AP 00:0f:66:4c:cd:26
[   82.534518] wlan0: RX AssocResp from 00:0f:66:4c:cd:26 (capab=0x411 status=0 aid=1)
[   82.534526] wlan0: associated
[   82.539027] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   87.913808] wlan0: no IPv6 routers present

```

So i've tried to do
> 
sudo modprobe usbserial vendo=0x03f0 product=0x1e1d
sudo modprobe sierra


and the new dmesg is:
```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-18-generic (buildd@king) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed May 28 19:28:38 UTC 2008 (Ubuntu 2.6.24-18.32-generic)
[    0.000000] Command line: root=UUID=6d02d361-75d2-45ad-b612-ea1f40857d88 ro quiet splash
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007e7b0000 (usable)
[    0.000000]  BIOS-e820: 000000007e7b0000 - 000000007e7c5400 (reserved)
[    0.000000]  BIOS-e820: 000000007e7c5400 - 000000007e7e7fb8 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007e7e7fb8 - 000000007f000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed20000 - 00000000fed9a000 (reserved)
[    0.000000]  BIOS-e820: 00000000feda0000 - 00000000fedc0000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb00000 - 00000000ffc00000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 518064) 1 entries of 3200 used
[    0.000000] end_pfn_map = 1048576
[    0.000000] DMI 2.4 present.
[    0.000000] ACPI: RSDP signature @ 0xFFFF8100000F7820 checksum 0
[    0.000000] ACPI: RSDP 000F7820, 0024 (r2 HP    )
[    0.000000] ACPI: XSDT 7E7C81C8, 007C (r1 HPQOEM SLIC-MPC        1 HP          1)
[    0.000000] ACPI: FACP 7E7C8084, 00F4 (r4 HP     30C8            3 HP          1)
[    0.000000] ACPI: DSDT 7E7C8538, 128DB (r1 HP       nc65xx    10000 MSFT  3000001)
[    0.000000] ACPI: FACS 7E7E7D80, 0040
[    0.000000] ACPI: SLIC 7E7C8244, 0176 (r1 HPQOEM SLIC-MPC        1 HP          1)
[    0.000000] ACPI: HPET 7E7C83BC, 0038 (r1 HP     30C8            1 HP          1)
[    0.000000] ACPI: APIC 7E7C83F4, 0068 (r1 HP     30C8            1 HP          1)
[    0.000000] ACPI: MCFG 7E7C845C, 003C (r1 HP     30C8            1 HP          1)
[    0.000000] ACPI: TCPA 7E7C8498, 0032 (r2 HP     30C8            1 HP          1)
[    0.000000] ACPI: ASF! 7E7C84CC, 0069 (r16 HP     CHIMAYU         1 HP          0)
[    0.000000] ACPI: SSDT 7E7DAE13, 01AB (r1 HP       HPQPAT        1 MSFT  3000001)
[    0.000000] ACPI: SSDT 7E7DB900, 025F (r1 HP      Cpu0Tst     3000 INTL 20060317)
[    0.000000] ACPI: SSDT 7E7DBB5F, 00A6 (r1 HP      Cpu1Tst     3000 INTL 20060317)
[    0.000000] ACPI: SSDT 7E7DBC05, 04D7 (r1 HP        CpuPm     3000 INTL 20060317)
[    0.000000] ACPI: DMI detected: Hewlett-Packard
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-000000007e7b0000
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 518064) 1 entries of 3200 used
[    0.000000] Bootmem setup node 0 0000000000000000-000000007e7b0000
[    0.000000] No mptable found.
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   DMA32        4096 ->  1048576
[    0.000000]   Normal    1048576 ->  1048576
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0:        0 ->      159
[    0.000000]     0:      256 ->   518064
[    0.000000] On node 0 totalpages: 517967
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 1218 pages reserved
[    0.000000]   DMA zone: 2725 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 7026 pages used for memmap
[    0.000000]   DMA32 zone: 506942 pages, LIFO batch:31
[    0.000000]   Normal zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 (Bootup-CPU)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] Processor #1
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Setting APIC routing to flat
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000e0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 7f000000:7fc00000)
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] PERCPU: Allocating 34656 bytes of per cpu data
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 509667
[    0.000000] Policy zone: DMA32
[    0.000000] Kernel command line: root=UUID=6d02d361-75d2-45ad-b612-ea1f40857d88 ro quiet splash
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] Extended CMOS year: 2000
[    0.000000] hpet clockevent registered
[    0.000000] TSC calibrated against HPET
[   18.757564] time.c: Detected 1196.999 MHz processor.
[   18.759006] Console: colour VGA+ 80x25
[   18.759011] console [tty0] enabled
[   18.759037] Checking aperture...
[   18.759053] Calgary: detecting Calgary via BIOS EBDA area
[   18.759056] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[   18.788273] Memory: 2030904k/2072256k available (2488k kernel code, 40964k reserved, 1319k data, 320k init)
[   18.788322] SLUB: Genslabs=12, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   18.867485] Calibrating delay using timer specific routine.. 2397.01 BogoMIPS (lpj=4794035)
[   18.867529] Security Framework initialized
[   18.867537] SELinux:  Disabled at boot.
[   18.867554] AppArmor: AppArmor initialized
[   18.867559] Failure registering capabilities with primary security module.
[   18.867855] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
[   18.869627] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
[   18.870578] Mount-cache hash table entries: 256
[   18.870757] Initializing cgroup subsys ns
[   18.870765] Initializing cgroup subsys cpuacct
[   18.870786] CPU: L1 I cache: 32K, L1 D cache: 32K
[   18.870788] CPU: L2 cache: 2048K
[   18.870791] CPU 0/0 -> Node 0
[   18.870793] using mwait in idle threads.
[   18.870796] CPU: Physical Processor ID: 0
[   18.870798] CPU: Processor Core ID: 0
[   18.870805] CPU0: Thermal monitoring handled by SMI
[   18.870822] SMP alternatives: switching to UP code
[   18.871935] Early unpacking initramfs... done
[   19.394189] ACPI: Core revision 20070126
[   19.394308] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   19.544245] Using local APIC timer interrupts.
[   19.627746] APIC timer calibration result 8312485
[   19.627749] Detected 8.312 MHz APIC timer.
[   19.627858] SMP alternatives: switching to SMP code
[   19.628787] Booting processor 1/2 APIC 0x1
[   19.639237] Initializing CPU#1
[   19.719707] Calibrating delay using timer specific routine.. 2393.98 BogoMIPS (lpj=4787969)
[   19.719716] CPU: L1 I cache: 32K, L1 D cache: 32K
[   19.719719] CPU: L2 cache: 2048K
[   19.719722] CPU 1/1 -> Node 0
[   19.719724] CPU: Physical Processor ID: 0
[   19.719725] CPU: Processor Core ID: 1
[   19.719734] CPU1: Thermal monitoring enabled (TM2)
[   19.720204] Intel(R) Core(TM)2 Duo CPU     U7600  @ 1.20GHz stepping 0d
[   19.720243] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[   19.740267] Brought up 2 CPUs
[   19.740372] CPU0 attaching sched-domain:
[   19.740375]  domain 0: span 03
[   19.740377]   groups: 01 02
[   19.740382]   domain 1: span 03
[   19.740384]    groups: 03
[   19.740387] CPU1 attaching sched-domain:
[   19.740389]  domain 0: span 03
[   19.740391]   groups: 02 01
[   19.740395]   domain 1: span 03
[   19.740397]    groups: 03
[   19.740706] net_namespace: 120 bytes
[   19.741253] Time: 16:18:52  Date: 06/10/08
[   19.741287] NET: Registered protocol family 16
[   19.741569] ACPI: bus type pci registered
[   19.741676] PCI: Using configuration type 1
[   19.744044] ACPI: EC: Look up EC in DSDT
[   19.746677] ACPI: EC: non-query interrupt received, switching to interrupt mode
[   19.806024] ACPI: Interpreter enabled
[   19.806029] ACPI: (supports S0 S3 S4 S5)
[   19.806049] ACPI: Using IOAPIC for interrupt routing
[   19.822137] ACPI: EC: GPE = 0x16, I/O: command/status = 0x66, data = 0x62
[   19.822141] ACPI: EC: driver started in interrupt mode
[   19.822233] ACPI: PCI Root Bridge [C003] (0000:00)
[   19.823752] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[   19.823757] PCI quirk: region 1100-113f claimed by ICH6 GPIO
[   19.824752] PCI: Transparent bridge - 0000:00:1e.0
[   19.824806] ACPI: PCI Interrupt Routing Table [\_SB_.C003._PRT]
[   19.825472] ACPI: PCI Interrupt Routing Table [\_SB_.C003.C0B2._PRT]
[   19.825689] ACPI: PCI Interrupt Routing Table [\_SB_.C003.C11F._PRT]
[   19.825910] ACPI: PCI Interrupt Routing Table [\_SB_.C003.C133._PRT]
[   19.826131] ACPI: PCI Interrupt Routing Table [\_SB_.C003.C134._PRT]
[   19.905908] ACPI: PCI Interrupt Link [C12F] (IRQs *10 11)
[   19.906256] ACPI: PCI Interrupt Link [C130] (IRQs *10 11)
[   19.906598] ACPI: PCI Interrupt Link [C131] (IRQs 10 *11)
[   19.906928] ACPI: PCI Interrupt Link [C132] (IRQs 10 11) *0, disabled.
[   19.907269] ACPI: PCI Interrupt Link [C142] (IRQs 10 *11)
[   19.907597] ACPI: PCI Interrupt Link [C143] (IRQs 10 11) *0, disabled.
[   19.907936] ACPI: PCI Interrupt Link [C144] (IRQs 10 11) *5
[   19.908098] ACPI Exception (pci_link-0184): AE_NOT_FOUND, Evaluating _PRS [20070126]
[   19.908399] ACPI: Power Resource [C299] (on)
[   19.908493] ACPI: Power Resource [C1C9] (off)
[   19.908572] Linux Plug and Play Support v0.97 (c) Adam Belay
[   19.908614] pnp: PnP ACPI init
[   19.908624] ACPI: bus type pnp registered
[   19.922612] pnp: PnP ACPI: found 15 devices
[   19.922615] ACPI: ACPI bus type pnp unregistered
[   19.922951] PCI: Using ACPI for IRQ routing
[   19.922953] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   19.936150] NET: Registered protocol family 8
[   19.936152] NET: Registered protocol family 20
[   19.936202] PCI-GART: No AMD northbridge found.
[   19.936209] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   19.936214] hpet0: 3 64-bit timers, 14318180 Hz
[   19.937274] AppArmor: AppArmor Filesystem Enabled
[   19.939581] Time: tsc clocksource has been installed.
[   19.939596] Switched to high resolution mode on CPU 0
[   19.940142] Switched to high resolution mode on CPU 1
[   19.948569] system 00:00: iomem range 0x0-0x9ffff could not be reserved
[   19.948574] system 00:00: iomem range 0xe0000-0xfffff could not be reserved
[   19.948578] system 00:00: iomem range 0x100000-0x7e7fffff could not be reserved
[   19.948595] system 00:0b: ioport range 0x500-0x55f has been reserved
[   19.948599] system 00:0b: ioport range 0x800-0x80f has been reserved
[   19.948604] system 00:0b: iomem range 0xffb00000-0xffbfffff could not be reserved
[   19.948609] system 00:0b: iomem range 0xfff00000-0xffffffff could not be reserved
[   19.948618] system 00:0d: ioport range 0x4d0-0x4d1 has been reserved
[   19.948622] system 00:0d: ioport range 0x1000-0x107f has been reserved
[   19.948626] system 00:0d: ioport range 0x1100-0x113f has been reserved
[   19.948631] system 00:0d: ioport range 0x1200-0x121f has been reserved
[   19.948635] system 00:0d: iomem range 0xf8000000-0xfbffffff has been reserved
[   19.948640] system 00:0d: iomem range 0xfec00000-0xfec000ff could not be reserved
[   19.948644] system 00:0d: iomem range 0xfed20000-0xfed3ffff could not be reserved
[   19.948649] system 00:0d: iomem range 0xfed45000-0xfed8ffff could not be reserved
[   19.948654] system 00:0d: iomem range 0xfed90000-0xfed99fff could not be reserved
[   19.948662] system 00:0e: iomem range 0xcee00-0xcffff has been reserved
[   19.948666] system 00:0e: iomem range 0xd2000-0xd3fff has been reserved
[   19.948671] system 00:0e: iomem range 0xfeda0000-0xfedbffff could not be reserved
[   19.948675] system 00:0e: iomem range 0xfee00000-0xfee00fff could not be reserved
[   19.949256] PCI: Bridge: 0000:00:1c.0
[   19.949258]   IO window: disabled.
[   19.949265]   MEM window: disabled.
[   19.949270]   PREFETCH window: disabled.
[   19.949277] PCI: Bridge: 0000:00:1c.1
[   19.949279]   IO window: disabled.
[   19.949286]   MEM window: e4000000-e40fffff
[   19.949292]   PREFETCH window: disabled.
[   19.949299] PCI: Bridge: 0000:00:1c.2
[   19.949303]   IO window: 2000-3fff
[   19.949310]   MEM window: e0000000-e3ffffff
[   19.949315]   PREFETCH window: disabled.
[   19.949323] PCI: Bridge: 0000:00:1e.0
[   19.949325]   IO window: disabled.
[   19.949332]   MEM window: e4100000-e43fffff
[   19.949337]   PREFETCH window: disabled.
[   19.949376] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
[   19.949384] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   19.949415] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 17 (level, low) -> IRQ 17
[   19.949422] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   19.949453] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 18
[   19.949461] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   19.949478] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   19.949491] NET: Registered protocol family 2
[   19.992650] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
[   19.993709] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
[   19.997096] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   19.998028] TCP: Hash tables configured (established 262144 bind 65536)
[   19.998032] TCP reno registered
[   20.008726] checking if image is initramfs... it is
[   21.141371] Freeing initrd memory: 7548k freed
[   21.149100] audit: initializing netlink socket (disabled)
[   21.149117] audit(1213114733.200:1): initialized
[   21.152070] VFS: Disk quotas dquot_6.5.1
[   21.152170] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   21.152338] io scheduler noop registered
[   21.152341] io scheduler anticipatory registered
[   21.152343] io scheduler deadline registered
[   21.152484] io scheduler cfq registered (default)
[   21.152498] Boot video device is 0000:00:02.0
[   21.155878] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   21.155949] assign_interrupt_mode Found MSI capability
[   21.156010] Allocate Port Service[0000:00:1c.0:pcie00]
[   21.156145] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   21.156215] assign_interrupt_mode Found MSI capability
[   21.156272] Allocate Port Service[0000:00:1c.1:pcie00]
[   21.156405] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   21.156477] assign_interrupt_mode Found MSI capability
[   21.156534] Allocate Port Service[0000:00:1c.2:pcie00]
[   21.156577] Allocate Port Service[0000:00:1c.2:pcie02]
[   21.191494] Real Time Clock Driver v1.12ac
[   21.191856] hpet_resources: 0xfed00000 is busy
[   21.191932] Linux agpgart interface v0.102
[   21.191935] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   21.192716] 00:02: ttyS0 at I/O 0x200 (irq = 6) is a 16550A
[   21.193070] ACPI: PCI Interrupt 0000:00:03.3[B] -> GSI 17 (level, low) -> IRQ 17
[   21.193188] 0000:00:03.3: ttyS1 at I/O 0x4040 (irq = 17) is a 16550A
[   21.194094] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   21.194191] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   21.194331] PNP: PS/2 Controller [PNP0303:C296,PNP0f13:C297] at 0x60,0x64 irq 1,12
[   21.196283] i8042.c: Detected active multiplexing controller, rev 1.1.
[   21.197054] serio: i8042 KBD port at 0x60,0x64 irq 1
[   21.197059] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[   21.197063] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[   21.197069] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[   21.197072] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[   21.206958] mice: PS/2 mouse device common for all mice
[   21.207010] cpuidle: using governor ladder
[   21.207013] cpuidle: using governor menu
[   21.207201] NET: Registered protocol family 1
[   21.207331] registered taskstats version 1
[   21.207483]   Magic number: 12:717:337
[   21.207497]   hash matches device ttyzc
[   21.207572]   hash matches device tty58
[   21.207611] /build/buildd/linux-2.6.24/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   21.207615] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   21.207617] EDD information not available.
[   21.207626] Freeing unused kernel memory: 320k freed
[   21.228717] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   22.474123] fuse init (API version 7.9)
[   22.498501] ACPI: SSDT 7E7DB086, 01FB (r1 HP      Cpu0Ist     3000 INTL 20060317)
[   22.498876] ACPI: SSDT 7E7DB306, 05FA (r1 HP      Cpu0Cst     3001 INTL 20060317)
[   22.508029] Monitor-Mwait will be used to enter C-1 state
[   22.508034] Monitor-Mwait will be used to enter C-2 state
[   22.508163] ACPI: CPU0 (power states: C1[C1] C2[C2])
[   22.508169] ACPI: Processor [CPU0] (supports 8 throttling states)
[   22.508487] ACPI: SSDT 7E7DAFBE, 00C8 (r1 HP      Cpu1Ist     3000 INTL 20060317)
[   22.508835] ACPI: SSDT 7E7DB281, 0085 (r1 HP      Cpu1Cst     3000 INTL 20060317)
[   22.510620] Marking TSC unstable due to TSC halts in idle
[   22.510702] ACPI: CPU1 (power states: C1[C1] C2[C2])
[   22.510709] ACPI: Processor [CPU1] (supports 8 throttling states)
[   22.513081] ACPI: Thermal Zone [TZ0] (25 C)
[   22.514004] Time: hpet clocksource has been installed.
[   22.517825] ACPI: Thermal Zone [TZ1] (51 C)
[   22.522295] ACPI: Thermal Zone [TZ3] (42 C)
[   22.526189] ACPI: Thermal Zone [TZ4] (34 C)
[   22.989442] SCSI subsystem initialized
[   23.028266] Intel(R) PRO/1000 Network Driver - version 7.3.20-k2-NAPI
[   23.028271] Copyright (c) 1999-2006 Intel Corporation.
[   23.028354] ACPI: PCI Interrupt 0000:00:19.0[A] -> GSI 22 (level, low) -> IRQ 22
[   23.028372] PCI: Setting latency timer of device 0000:00:19.0 to 64
[   23.034622] usbcore: registered new interface driver usbfs
[   23.034656] usbcore: registered new interface driver hub
[   23.034693] usbcore: registered new device driver usb
[   23.035944] USB Universal Host Controller Interface driver v3.0
[   23.056753] e1000: 0000:00:19.0: e1000_probe: (PCI Express:2.5Gb/s:Width x1) 00:1e:0b:57:3f:88
[   23.073892] libata version 3.00 loaded.
[   23.149558] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
[   23.149598] ACPI: PCI Interrupt 0000:00:1a.0[A] -> GSI 16 (level, low) -> IRQ 16
[   23.149614] PCI: Setting latency timer of device 0000:00:1a.0 to 64
[   23.149619] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[   23.149976] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[   23.150016] uhci_hcd 0000:00:1a.0: irq 16, io base 0x00004080
[   23.150190] usb usb1: configuration #1 chosen from 1 choice
[   23.150220] hub 1-0:1.0: USB hub found
[   23.150228] hub 1-0:1.0: 2 ports detected
[   23.251409] ACPI: PCI Interrupt 0000:00:1a.1[B] -> GSI 17 (level, low) -> IRQ 17
[   23.251426] PCI: Setting latency timer of device 0000:00:1a.1 to 64
[   23.251432] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[   23.251461] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
[   23.251500] uhci_hcd 0000:00:1a.1: irq 17, io base 0x000040a0
[   23.251647] usb usb2: configuration #1 chosen from 1 choice
[   23.251679] hub 2-0:1.0: USB hub found
[   23.251686] hub 2-0:1.0: 2 ports detected
[   23.355298] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 20 (level, low) -> IRQ 20
[   23.355315] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   23.355320] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   23.355349] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 3
[   23.355385] uhci_hcd 0000:00:1d.0: irq 20, io base 0x000040c0
[   23.355524] usb usb3: configuration #1 chosen from 1 choice
[   23.355558] hub 3-0:1.0: USB hub found
[   23.355565] hub 3-0:1.0: 2 ports detected
[   23.459250] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 22 (level, low) -> IRQ 22
[   23.459268] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   23.459273] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   23.459305] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 4
[   23.459345] uhci_hcd 0000:00:1d.1: irq 22, io base 0x000040e0
[   23.459518] usb usb4: configuration #1 chosen from 1 choice
[   23.459548] hub 4-0:1.0: USB hub found
[   23.459555] hub 4-0:1.0: 2 ports detected
[   23.491112] usb 1-1: new full speed USB device using uhci_hcd and address 2
[   23.563163] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[   23.563181] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   23.563186] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   23.563215] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 5
[   23.563253] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00004100
[   23.563388] usb usb5: configuration #1 chosen from 1 choice
[   23.563417] hub 5-0:1.0: USB hub found
[   23.563424] hub 5-0:1.0: 2 ports detected
[   23.657924] usb 1-1: configuration #1 chosen from 1 choice
[   23.667296] ACPI: PCI Interrupt 0000:00:1a.7[C] -> GSI 18 (level, low) -> IRQ 18
[   23.668084] PCI: Setting latency timer of device 0000:00:1a.7 to 64
[   23.668092] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[   23.668155] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 6
[   23.672083] ehci_hcd 0000:00:1a.7: debug port 1
[   23.672092] PCI: cache line size of 32 is not supported by device 0000:00:1a.7
[   23.672102] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xe4641000
[   23.686990] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   23.687159] usb usb6: configuration #1 chosen from 1 choice
[   23.687191] hub 6-0:1.0: USB hub found
[   23.687200] hub 6-0:1.0: 4 ports detected
[   23.791055] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 20 (level, low) -> IRQ 20
[   23.791821] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   23.791830] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   23.791893] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 7
[   23.795826] ehci_hcd 0000:00:1d.7: debug port 1
[   23.795834] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   23.795843] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xe4648000
[   23.843539] usb 3-1: new low speed USB device using uhci_hcd and address 2
[   23.844868] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   23.845036] usb usb7: configuration #1 chosen from 1 choice
[   23.845069] hub 7-0:1.0: USB hub found
[   23.845077] hub 7-0:1.0: 6 ports detected
[   23.847207] Clocksource tsc unstable (delta = -91704210 ns)
[   23.853809] ACPI: PCI Interrupt 0000:02:09.0[A] -> GSI 20 (level, low) -> IRQ 20
[   23.906958] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[20]  MMIO=[e4100000-e41007ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[   23.915346] ACPI: PCI Interrupt 0000:00:03.2[C] -> GSI 18 (level, low) -> IRQ 18
[   23.915391] PCI: Setting latency timer of device 0000:00:03.2 to 64
[   23.915405] ACPI: PCI interrupt for device 0000:00:03.2 disabled
[   23.915431] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 16 (level, low) -> IRQ 16
[   23.915459] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   23.915472] ACPI: PCI interrupt for device 0000:00:1f.1 disabled
[   23.918474] ata_piix 0000:00:1f.1: version 2.12
[   23.918492] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 16 (level, low) -> IRQ 16
[   23.918531] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   23.919142] scsi0 : ata_piix
[   23.919827] scsi1 : ata_piix
[   23.920429] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x4120 irq 14
[   23.920433] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x4128 irq 15
[   23.934308] ata1.00: ATA-7: TOSHIBA MK1011GAH, BK001C, max UDMA/100
[   23.934312] ata1.00: 195371568 sectors, multi 16: LBA 
[   23.935255] ata1.00: configured for UDMA/100
[   23.935338] ata2: port disabled. ignoring.
[   23.935503] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK1011GA BK00 PQ: 0 ANSI: 5
[   23.943831] Driver 'sd' needs updating - please use bus_type methods
[   23.943930] sd 0:0:0:0: [sda] 195371568 512-byte hardware sectors (100030 MB)
[   23.943946] sd 0:0:0:0: [sda] Write Protect is off
[   23.943949] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   23.943972] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   23.944039] sd 0:0:0:0: [sda] 195371568 512-byte hardware sectors (100030 MB)
[   23.944053] sd 0:0:0:0: [sda] Write Protect is off
[   23.944056] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   23.944079] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   23.944084]  sda: sda1 < sda5 sda6 sda7 > sda2 sda3
[   23.988427] sd 0:0:0:0: [sda] Attached SCSI disk
[   23.992913] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   24.147724] usb 1-1: USB disconnect, address 2
[   24.387526] usb 1-1: new full speed USB device using uhci_hcd and address 3
[   24.536290] Attempting manual resume
[   24.536294] swsusp: Resume From Partition 8:5
[   24.536296] PM: Checking swsusp image.
[   24.536703] PM: Resume from disk failed.
[   24.564401] usb 1-1: configuration #1 chosen from 1 choice
[   24.598443] kjournald starting.  Commit interval 5 seconds
[   24.598462] EXT3-fs: mounted filesystem with ordered data mode.
[   25.027110] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00023f8429c5540e]
[   25.230025] usb 7-4: new high speed USB device using ehci_hcd and address 4
[   25.373891] usb 7-4: configuration #1 chosen from 1 choice
[   25.613784] usb 3-1: new low speed USB device using uhci_hcd and address 3
[   25.793829] usb 3-1: configuration #1 chosen from 1 choice
[   26.035173] usb 3-2: new full speed USB device using uhci_hcd and address 4
[   26.196638] usb 3-2: configuration #1 chosen from 1 choice
[   38.955382] tpm_inf_pnp 00:03: Found C27D with ID IFX0102
[   38.955443] tpm_inf_pnp 00:03: TPM found: config base 0x560, data base 0x570, chip version 0x000b, vendor id 0x15d1 (Infineon), product id 0x000b (SLB 9635 TT 1.2)
[   39.142933] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   39.182872] iTCO_vendor_support: vendor-support=0
[   39.222852] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   39.222968] iTCO_wdt: Found a ICH8M-E TCO device (Version=2, TCOBASE=0x1060)
[   39.223018] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   39.262883] agpgart: Detected an Intel 965GM Chipset.
[   39.264333] agpgart: Detected 7676K stolen memory.
[   39.279907] agpgart: AGP aperture is 256M @ 0xd0000000
[   39.342893] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   39.391244] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   39.443821] input: Power Button (FF) as /devices/virtual/input/input3
[   39.467976] ACPI: Power Button (FF) [PWRF]
[   39.468170] input: Sleep Button (CM) as /devices/virtual/input/input4
[   39.483949] ACPI: Sleep Button (CM) [C2B7]
[   39.484074] input: Lid Switch as /devices/virtual/input/input5
[   39.660005] ACPI: Lid Switch [C155]
[   39.660572] ACPI: AC Adapter [C23D] (on-line)
[   39.704333] ACPI: Battery Slot [C23F] (battery present)
[   39.704669] ACPI: Battery Slot [C23E] (battery absent)
[   39.705481] ACPI: WMI-Acer: Mapper loaded
[   40.099747] ricoh-mmc: Ricoh MMC Controller disabling driver
[   40.099752] ricoh-mmc: Copyright(c) Philip Langdale
[   40.099815] ricoh-mmc: Ricoh MMC controller found at 0000:02:09.2 [1180:0843] (rev 12)
[   40.099834] ricoh-mmc: Controller is now disabled.
[   40.399497] sdhci: Secure Digital Host Controller Interface driver
[   40.399502] sdhci: Copyright(c) Pierre Ossman
[   40.399571] sdhci: SDHCI controller found at 0000:02:09.1 [1180:0822] (rev 22)
[   40.399599] ACPI: PCI Interrupt 0000:02:09.1[B] -> GSI 22 (level, low) -> IRQ 22
[   40.400338] sdhci:slot0: Will use DMA mode even though HW doesn't fully claim to support it.
[   40.400433] mmc0: SDHCI at 0xe4101000 irq 22 DMA
[   40.613966] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input6
[   40.654278] ACPI: Video Device [C09A] (multi-head: yes  rom: no  post: no)
[   40.981131] input: PS/2 Generic Mouse as /devices/platform/i8042/serio4/input/input7
[   41.060371] iwl4965: Intel(R) Wireless WiFi Link 4965AGN driver for Linux, 1.2.0
[   41.060376] iwl4965: Copyright(c) 2003-2007 Intel Corporation
[   41.060495] ACPI: PCI Interrupt 0000:10:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[   41.060507] PCI: Setting latency timer of device 0000:10:00.0 to 64
[   41.061232] iwl4965: Detected Intel Wireless WiFi Link 4965AGN
[   41.175248] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 17 (level, low) -> IRQ 17
[   41.175977] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   41.407169] Bluetooth: Core ver 2.11
[   41.431091] NET: Registered protocol family 31
[   41.431095] Bluetooth: HCI device and connection manager initialized
[   41.431101] Bluetooth: HCI socket layer initialized
[   41.453230] Bluetooth: HCI USB driver ver 2.9
[   41.454896] usbcore: registered new interface driver hci_usb
[   41.533536] usbcore: registered new interface driver hiddev
[   41.538112] Linux video capture interface: v2.00
[   41.546369] input: Microsoft Microsoft Notebook/Mobile Optical Mouse 2.0 as /devices/pci0000:00/0000:00:1d.0/usb3/3-1/3-1:1.0/input/input8
[   41.706682] input,hidraw0: USB HID v1.10 Mouse [Microsoft Microsoft Notebook/Mobile Optical Mouse 2.0] on usb-0000:00:1d.0-1
[   41.706709] usbcore: registered new interface driver usbhid
[   41.706714] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   41.710054] uvcvideo: Found UVC 1.00 device HP Webcam (04f2:b017)
[   41.747567] usbcore: registered new interface driver uvcvideo
[   41.747572] USB Video Class driver (v0.1.0)
[   43.844483] iwl4965: Tunable channels: 13 802.11bg, 19 802.11a channels
[   43.845067] wmaster0: Selected rate control algorithm 'iwl-4965-rs'
[   44.572271] loop: module loaded
[   44.646497] lp: driver loaded but no devices found
[   44.864354] Adding 3574420k swap on /dev/sda5.  Priority:-1 extents:1 across:3574420k
[   45.417231] EXT3 FS on sda6, internal journal
[   46.281726] ip_tables: (C) 2000-2006 Netfilter Core Team
[   46.949523] No dock devices found.
[   48.690469] ppdev: user-space parallel port driver
[   48.878108] audit(1213103963.054:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5261 profile="/usr/sbin/cupsd" namespace="default"
[   51.955671] Bluetooth: L2CAP ver 2.9
[   51.955679] Bluetooth: L2CAP socket layer initialized
[   52.141391] Bluetooth: RFCOMM socket layer initialized
[   52.141415] Bluetooth: RFCOMM TTY layer initialized
[   52.141419] Bluetooth: RFCOMM ver 1.8
[   54.430302] [drm] Initialized drm 1.1.0 20060810
[   54.433672] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
[   54.433684] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   54.433760] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   66.090249] NET: Registered protocol family 10
[   66.090713] lo: Disabled Privacy Extensions
[   66.091509] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   66.092354] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   76.431904] CPU0 attaching NULL sched-domain.
[   76.431916] CPU1 attaching NULL sched-domain.
[   76.461338] CPU0 attaching sched-domain:
[   76.461349]  domain 0: span 03
[   76.461352]   groups: 01 02
[   76.461357]   domain 1: span 03
[   76.461360]    groups: 03
[   76.461363] CPU1 attaching sched-domain:
[   76.461366]  domain 0: span 03
[   76.461369]   groups: 02 01
[   76.461373]   domain 1: span 03
[   76.461375]    groups: 03
[   80.197633] NET: Registered protocol family 17
[   82.530138] wlan0: Initial auth_alg=0
[   82.530149] wlan0: authenticate with AP 00:0f:66:4c:cd:26
[   82.531995] wlan0: RX authentication from 00:0f:66:4c:cd:26 (alg=0 transaction=2 status=0)
[   82.532002] wlan0: authenticated
[   82.532005] wlan0: associate with AP 00:0f:66:4c:cd:26
[   82.534518] wlan0: RX AssocResp from 00:0f:66:4c:cd:26 (capab=0x411 status=0 aid=1)
[   82.534526] wlan0: associated
[   82.539027] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   87.913808] wlan0: no IPv6 routers present
[  525.112262] usbcore: registered new interface driver usbserial
[  525.112685] /build/buildd/linux-2.6.24/drivers/usb/serial/usb-serial.c: USB Serial support registered for generic
[  525.113100] usbcore: registered new interface driver usbserial_generic
[  525.113107] /build/buildd/linux-2.6.24/drivers/usb/serial/usb-serial.c: USB Serial Driver core
[  526.702673] /build/buildd/linux-2.6.24/drivers/usb/serial/usb-serial.c: USB Serial support registered for Sierra USB modem (1 port)
[  526.702696] /build/buildd/linux-2.6.24/drivers/usb/serial/usb-serial.c: USB Serial support registered for Sierra USB modem (3 port)
[  526.702741] usbcore: registered new interface driver sierra
[  526.702745] /build/buildd/linux-2.6.24/drivers/usb/serial/sierra.c: USB Driver for Sierra Wireless USB modems: v.1.2.5b

```

So this gives us:
> 
diff dmesg dmesg2
539a540,547
> [  525.112262] usbcore: registered new interface driver usbserial
> [  525.112685] /build/buildd/linux-2.6.24/drivers/usb/serial/usb-serial.c: USB Serial support registered for generic
> [  525.113100] usbcore: registered new interface driver usbserial_generic
> [  525.113107] /build/buildd/linux-2.6.24/drivers/usb/serial/usb-serial.c: USB Serial Driver core
> [  526.702673] /build/buildd/linux-2.6.24/drivers/usb/serial/usb-serial.c: USB Serial support registered for Sierra USB modem (1 port)
> [  526.702696] /build/buildd/linux-2.6.24/drivers/usb/serial/usb-serial.c: USB Serial support registered for Sierra USB modem (3 port)
> [  526.702741] usbcore: registered new interface driver sierra
> [  526.702745] /build/buildd/linux-2.6.24/drivers/usb/serial/sierra.c: USB Driver for Sierra Wireless USB modems: v.1.2.5b


Every help appreciated!

---

