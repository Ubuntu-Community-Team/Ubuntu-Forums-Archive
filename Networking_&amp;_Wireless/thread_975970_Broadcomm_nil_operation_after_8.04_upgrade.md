---
title: "Broadcomm nil operation after 8.04 upgrade"
date: 2008-11-08
forum: Networking &amp; Wireless
---

### Post by NewNerd99 on 2008-11-08
During the week I downloaded several updates one of which killed my wireless ability.
I have hunted the threads but with no success.
When I open the box to enable drivers only my Nvidia card is there now not the broadcomm anymore.

Any pointers to a previous thread or suggestions on where to start would be appreciated.

Cheers
Chris

---

### Post by pytheas22 on 2008-11-08
What is the output of:
```

lspci -nn | grep -i broadcom
lshw -C Network
dmesg | grep -e wlan -e b43 -e bcm
```

---

### Post by NewNerd99 on 2008-11-09
From lspci :nn

00:00.0 RAM memory [0500]: nVidia Corporation C51 Host Bridge [10de:02f3] (rev a2)
00:00.1 RAM memory [0500]: nVidia Corporation C51 Memory Controller 0 [10de:02fa] (rev a2)
00:00.2 RAM memory [0500]: nVidia Corporation C51 Memory Controller 1 [10de:02fe] (rev a2)
00:00.3 RAM memory [0500]: nVidia Corporation C51 Memory Controller 5 [10de:02f8] (rev a2)
00:00.4 RAM memory [0500]: nVidia Corporation C51 Memory Controller 4 [10de:02f9] (rev a2)
00:00.5 RAM memory [0500]: nVidia Corporation C51 Host Bridge [10de:02ff] (rev a2)
00:00.6 RAM memory [0500]: nVidia Corporation C51 Memory Controller 3 [10de:027f] (rev a2)
00:00.7 RAM memory [0500]: nVidia Corporation C51 Memory Controller 2 [10de:027e] (rev a2)
00:02.0 PCI bridge [0604]: nVidia Corporation C51 PCI Express Bridge [10de:02fc] (rev a1)
00:03.0 PCI bridge [0604]: nVidia Corporation C51 PCI Express Bridge [10de:02fd] (rev a1)
00:05.0 VGA compatible controller [0300]: nVidia Corporation MCP51 PCI-X GeForce Go 6100 [10de:0247] (rev a2)
00:09.0 RAM memory [0500]: nVidia Corporation MCP51 Host Bridge [10de:0270] (rev a2)
00:0a.0 ISA bridge [0601]: nVidia Corporation MCP51 LPC Bridge [10de:0260] (rev a3)
00:0a.1 SMBus [0c05]: nVidia Corporation MCP51 SMBus [10de:0264] (rev a3)
00:0a.3 Co-processor [0b40]: nVidia Corporation MCP51 PMU [10de:0271] (rev a3)
00:0b.0 USB Controller [0c03]: nVidia Corporation MCP51 USB Controller [10de:026d] (rev a3)
00:0b.1 USB Controller [0c03]: nVidia Corporation MCP51 USB Controller [10de:026e] (rev a3)
00:0d.0 IDE interface [0101]: nVidia Corporation MCP51 IDE [10de:0265] (rev f1)
00:0e.0 IDE interface [0101]: nVidia Corporation MCP51 Serial ATA Controller [10de:0266] (rev f1)
00:10.0 PCI bridge [0604]: nVidia Corporation MCP51 PCI Bridge [10de:026f] (rev a2)
00:10.1 Audio device [0403]: nVidia Corporation MCP51 High Definition Audio [10de:026c] (rev a2)
00:14.0 Bridge [0680]: nVidia Corporation MCP51 Ethernet Controller [10de:0269] (rev a3)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
chris@chris-laptop:~$ 


Nothing printed from lshw -C Network ???


from dmesg:

  1)
[    0.000000] ACPI: SLIC 7BF16E8A, 0176 (r1 HPQOEM SLIC-MPC  6040000  LTP        1)
[    0.000000] ACPI: DMI detected: Hewlett-Packard
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:12 APIC version 16
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:60000000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009d000 - 000000000009e000
[    0.000000] swsusp: Registered nosave memory region: 000000000009e000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000d2000
[    0.000000] swsusp: Registered nosave memory region: 00000000000d2000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 503682
[    0.000000] Kernel command line: root=UUID=c94e8511-9946-452b-a262-60b93bf6df29 ro quiet splash
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 2009.177 MHz processor.
[   43.804475] spurious 8259A interrupt: IRQ7.
[   43.807622] Console: colour VGA+ 80x25
[   43.807626] console [tty0] enabled
[   43.807906] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   43.808259] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   43.886208] Memory: 2000848k/2030592k available (2177k kernel code, 28560k reserved, 1005k data, 368k init, 1113088k highmem)
[   43.886216] virtual kernel memory layout:
[   43.886217]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   43.886218]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   43.886219]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   43.886221]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   43.886222]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
[   43.886223]       .data : 0xc03205e4 - 0xc041bdc4   (1005 kB)
[   43.886224]       .text : 0xc0100000 - 0xc03205e4   (2177 kB)
[   43.886227] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   43.886262] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   43.886399] hpet clockevent registered
[   43.966296] Calibrating delay using timer specific routine.. 4021.85 BogoMIPS (lpj=8043709)
[   43.966316] Security Framework initialized
[   43.966322] SELinux:  Disabled at boot.
[   43.966336] AppArmor: AppArmor initialized
[   43.966339] Failure registering capabilities with primary security module.
[   43.966347] Mount-cache hash table entries: 512
[   43.966452] Initializing cgroup subsys ns
[   43.966455] Initializing cgroup subsys cpuacct
[   43.966465] CPU: After generic identify, caps: 078bfbff ebd3fbff 00000000 00000000 00002001 00000000 0000001d 00000000
[   43.966473] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   43.966475] CPU: L2 Cache: 512K (64 bytes/line)
[   43.966478] CPU: After all inits, caps: 078bfbff ebd3fbff 00000000 00020410 00002001 00000000 0000001d 00000000
[   43.966487] Compat vDSO mapped to ffffe000.
[   43.966496] Checking 'hlt' instruction... OK.
[   43.982529] SMP alternatives: switching to UP code
[   43.983529] Freeing SMP alternatives: 11k freed
[   43.983632] Early unpacking initramfs... done
[   44.300522] ACPI: Core revision 20070126
[   44.300604] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   44.306178] CPU0: AMD Turion(tm) 64 Mobile Technology MK-36 stepping 02
[   44.306190] Total of 1 processors activated (4021.85 BogoMIPS).
[   44.306491] ENABLING IO-APIC IRQs
[   44.306719] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   44.453697] Brought up 1 CPUs
[   44.453742] CPU0 attaching sched-domain:
[   44.453745]  domain 0: span 01
[   44.453746]   groups: 01
[   44.453881] net_namespace: 64 bytes
[   44.453888] Booting paravirtualized kernel on bare hardware
[   44.454297] Time: 12:22:17  Date: 11/09/08
[   44.454317] NET: Registered protocol family 16
[   44.454468] EISA bus registered
[   44.454472] ACPI: bus type pci registered
[   44.469984] PCI: BIOS BUG #81[49435000] found
[   44.470027] PCI: Using configuration type 1
[   44.470035] Setting up standard PCI resources
[   44.471605] ACPI: EC: Look up EC in DSDT
[   44.473341] ACPI: BIOS _OSI(Linux) query ignored via DMI
[   44.473537] ACPI: Interpreter enabled
[   44.473539] ACPI: (supports S0 S3 S4 S5)
[   44.473550] ACPI: Using IOAPIC for interrupt routing
[   44.474123] ACPI: EC: non-query interrupt received, switching to interrupt mode
[   44.480602] ACPI: EC: GPE = 0x10, I/O: command/status = 0x66, data = 0x62
[   44.480604] ACPI: EC: driver started in interrupt mode
[   44.480645] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   44.481561] PCI: Transparent bridge - 0000:00:10.0
[   44.481575] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   44.481751] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P0._PRT]
[   44.481774] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR1._PRT]
[   44.481800] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR2._PRT]
[   44.510581] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 10 11 14 15) *0, disabled.
[   44.510754] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 10 *11 14 15)
[   44.510925] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 10 11 14 15) *0, disabled.
[   44.511094] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 10 11 14 15) *0, disabled.
[   44.511264] ACPI: PCI Interrupt Link [LK1E] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[   44.511433] ACPI: PCI Interrupt Link [LK2E] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[   44.511603] ACPI: PCI Interrupt Link [LK3E] (IRQs 16 17 18 19 20 21 22 23) *11
[   44.511773] ACPI: PCI Interrupt Link [LK4E] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[   44.511943] ACPI: PCI Interrupt Link [LSMB] (IRQs 16 17 18 19 20 21 22 23) *10
[   44.512112] ACPI: PCI Interrupt Link [LPMU] (IRQs 16 17 18 19 20 21 22 23) *10
[   44.512282] ACPI: PCI Interrupt Link [LUS0] (IRQs 16 17 18 19 20 21 22 23) *11
[   44.512462] ACPI: PCI Interrupt Link [LUS2] (IRQs 16 17 18 19 20 21 22 23) *7
[   44.512636] ACPI: PCI Interrupt Link [LMAC] (IRQs 16 17 18 19 20 21 22 23) *10
[   44.512811] ACPI: PCI Interrupt Link [LAZA] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[   44.512985] ACPI: PCI Interrupt Link [LACI] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[   44.513160] ACPI: PCI Interrupt Link [LMCI] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[   44.513334] ACPI: PCI Interrupt Link [LPID] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
[   44.513515] ACPI: PCI Interrupt Link [LTID] (IRQs 16 17 18 19 20 21 22 23) *5
[   44.513700] ACPI: PCI Interrupt Link [LSI1] (IRQs 16 17 18 19 20 21 22 23) *10
[   44.513814] Linux Plug and Play Support v0.97 (c) Adam Belay
[   44.513838] pnp: PnP ACPI init
[   44.513844] ACPI: bus type pnp registered
[   44.516605] pnp: PnP ACPI: found 13 devices
[   44.516607] ACPI: ACPI bus type pnp unregistered
[   44.516610] PnPBIOS: Disabled by ACPI PNP
[   44.516783] PCI: Using ACPI for IRQ routing
[   44.516786] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   44.529585] NET: Registered protocol family 8
[   44.529587] NET: Registered protocol family 20
[   44.529615] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 31
[   44.529619] hpet0: 3 32-bit timers, 25000000 Hz
[   44.530658] AppArmor: AppArmor Filesystem Enabled
[   44.533553] Time: tsc clocksource has been installed.
[   44.533564] Switched to high resolution mode on CPU 0
[   44.541540] system 00:00: iomem range 0xe0000000-0xefffffff could not be reserved
[   44.541546] system 00:01: iomem range 0xffc00000-0xffffffff could not be reserved
[   44.541548] system 00:01: iomem range 0xfec00000-0xfec00fff could not be reserved
[   44.541551] system 00:01: iomem range 0xfee00000-0xfeefffff could not be reserved
[   44.541554] system 00:01: iomem range 0xfed00000-0xfed00fff has been reserved
[   44.541559] system 00:03: iomem range 0xe0000000-0xefffffff could not be reserved
[   44.541564] system 00:04: ioport range 0x1000-0x107f has been reserved
[   44.541567] system 00:04: ioport range 0x1080-0x10ff has been reserved
[   44.541569] system 00:04: ioport range 0x1400-0x147f has been reserved
[   44.541572] system 00:04: ioport range 0x1480-0x14ff has been reserved
[   44.541574] system 00:04: ioport range 0x1800-0x187f has been reserved
[   44.541577] system 00:04: ioport range 0x1880-0x18ff has been reserved
[   44.541579] system 00:04: ioport range 0x2000-0x203f has been reserved
[   44.541584] system 00:05: ioport range 0x360-0x361 has been reserved
[   44.541586] system 00:05: ioport range 0x380-0x383 has been reserved
[   44.541589] system 00:05: ioport range 0x4d0-0x4d1 has been reserved
[   44.571890] PCI: Bridge: 0000:00:02.0
[   44.571892]   IO window: 4000-4fff
[   44.571895]   MEM window: b4000000-b7ffffff
[   44.571897]   PREFETCH window: d0000000-d01fffff
[   44.571899] PCI: Bridge: 0000:00:03.0
[   44.571901]   IO window: 5000-5fff
[   44.571903]   MEM window: b8000000-bbffffff
[   44.571905]   PREFETCH window: d0200000-d03fffff
[   44.571908] PCI: Bridge: 0000:00:10.0
[   44.571909]   IO window: disabled.
[   44.571912]   MEM window: disabled.
[   44.571914]   PREFETCH window: disabled.
[   44.571926] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   44.571933] PCI: Setting latency timer of device 0000:00:03.0 to 64
[   44.571940] PCI: Setting latency timer of device 0000:00:10.0 to 64
[   44.571950] NET: Registered protocol family 2
[   44.609486] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   44.609744] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   44.610501] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   44.610881] TCP: Hash tables configured (established 131072 bind 65536)
[   44.610884] TCP reno registered
[   44.621529] checking if image is initramfs... it is
[   45.233502] Freeing initrd memory: 7724k freed
[   45.233627] Simple Boot Flag at 0x36 set to 0x1
[   45.234025] audit: initializing netlink socket (disabled)
[   45.234037] audit(1226233338.244:1): initialized
[   45.234176] highmem bounce pool size: 64 pages
[   45.235802] VFS: Disk quotas dquot_6.5.1
[   45.235864] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   45.235976] io scheduler noop registered
[   45.235978] io scheduler anticipatory registered
[   45.235980] io scheduler deadline registered
[   45.235992] io scheduler cfq registered (default)
[   45.236004] pci 0000:00:00.0: Enabling HT MSI Mapping
[   45.236032] pci 0000:00:02.0: Enabling HT MSI Mapping
[   45.236040] pci 0000:00:03.0: Enabling HT MSI Mapping
[   45.236047] Boot video device is 0000:00:05.0
[   45.236067] pci 0000:00:09.0: Enabling HT MSI Mapping
[   45.438135] pci 0000:00:0e.0: Enabling HT MSI Mapping
[   45.438143] pci 0000:00:10.0: Enabling HT MSI Mapping
[   45.438154] pci 0000:00:10.1: Enabling HT MSI Mapping
[   45.438252] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   45.438272] assign_interrupt_mode Found MSI capability
[   45.438290] Allocate Port Service[0000:00:02.0:pcie00]
[   45.438348] PCI: Setting latency timer of device 0000:00:03.0 to 64
[   45.438367] assign_interrupt_mode Found MSI capability
[   45.438381] Allocate Port Service[0000:00:03.0:pcie00]
[   45.438550] isapnp: Scanning for PnP cards...
[   45.791112] isapnp: No Plug & Play device found
[   45.814175] Real Time Clock Driver v1.12ac
[   45.814339] hpet_resources: 0xfed00000 is busy
[   45.814373] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   45.815278] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   45.815331] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   45.815405] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[   45.831864] serio: i8042 KBD port at 0x60,0x64 irq 1
[   45.831868] serio: i8042 AUX port at 0x60,0x64 irq 12
[   45.843823] mice: PS/2 mouse device common for all mice
[   45.843914] EISA: Probing bus 0 at eisa.0
[   45.843920] Cannot allocate resource for EISA slot 1
[   45.843922] Cannot allocate resource for EISA slot 2
[   45.843924] Cannot allocate resource for EISA slot 3
[   45.843925] Cannot allocate resource for EISA slot 4
[   45.843927] Cannot allocate resource for EISA slot 5
[   45.843937] EISA: Detected 0 cards.
[   45.843940] cpuidle: using governor ladder
[   45.843941] cpuidle: using governor menu
[   45.844019] NET: Registered protocol family 1
[   45.844042] Using IPI No-Shortcut mode
[   45.844069] registered taskstats version 1
[   45.844172]   Magic number: 0:800:379
[   45.844335] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   45.844337] EDD information not available.
[   45.844540] Freeing unused kernel memory: 368k freed
[   45.844560] Write protecting the kernel read-only data: 801k
[   45.863783] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   47.049049] fuse init (API version 7.9)
[   47.065012] ACPI Exception (processor_core-0822): AE_NOT_FOUND, Processor Device is not present [20070126]
[   47.067608] ACPI: Thermal Zone [THRM] (50 C)
[   47.929288] usbcore: registered new interface driver usbfs
[   47.929313] usbcore: registered new interface driver hub
[   47.936958] usbcore: registered new device driver usb
[   47.945368] SCSI subsystem initialized
[   47.976938] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   47.977273] ACPI: PCI Interrupt Link [LUS0] enabled at IRQ 23
[   47.977283] ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [LUS0] -> GSI 23 (level, high) -> IRQ 16
[   47.977294] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[   47.977297] ohci_hcd 0000:00:0b.0: OHCI Host Controller
[   47.977542] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 1
[   47.977559] ohci_hcd 0000:00:0b.0: irq 16, io mem 0xb0004000
[   48.012668] libata version 3.00 loaded.
[   48.034916] usb usb1: configuration #1 chosen from 1 choice
[   48.034941] hub 1-0:1.0: USB hub found
[   48.034949] hub 1-0:1.0: 8 ports detected
[   48.137208] ACPI: PCI Interrupt Link [LUS2] enabled at IRQ 22
[   48.137219] ACPI: PCI Interrupt 0000:00:0b.1[B] -> Link [LUS2] -> GSI 22 (level, high) -> IRQ 17
[   48.137229] PCI: Setting latency timer of device 0000:00:0b.1 to 64
[   48.137232] ehci_hcd 0000:00:0b.1: EHCI Host Controller
[   48.137254] ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 2
[   48.137285] ehci_hcd 0000:00:0b.1: debug port 1
[   48.137289] PCI: cache line size of 64 is not supported by device 0000:00:0b.1
[   48.137299] ehci_hcd 0000:00:0b.1: irq 17, io mem 0xb0005000
[   48.148657] ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   48.148766] usb usb2: configuration #1 chosen from 1 choice
[   48.148786] hub 2-0:1.0: USB hub found
[   48.148791] hub 2-0:1.0: 8 ports detected
[   48.252737] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
[   48.253039] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 21
[   48.253049] ACPI: PCI Interrupt 0000:00:14.0[A] -> Link [LMAC] -> GSI 21 (level, high) -> IRQ 18
[   48.253055] PCI: Setting latency timer of device 0000:00:14.0 to 64
[   48.772208] forcedeth 0000:00:14.0: ifname eth0, PHY OUI 0x20 @ 1, addr 00:1b:24:34:dc:bc
[   48.772213] forcedeth 0000:00:14.0: highdma pwrctl timirq lnktim desc-v3
[   48.775847] pata_amd 0000:00:0d.0: version 0.3.10
[   48.775898] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[   48.779445] scsi0 : pata_amd
[   48.780380] scsi1 : pata_amd
[   48.780880] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x3080 irq 14
[   48.780882] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x3088 irq 15
[   48.783811] usb 1-6: new low speed USB device using ohci_hcd and address 2
[   48.996634] usb 1-6: configuration #1 chosen from 1 choice
[   49.014879] usbcore: registered new interface driver hiddev
[   49.020666] input: Logitech Logitech USB Optical Mouse as /devices/pci0000:00/0000:00:0b.0/usb1/1-6/1-6:1.0/input/input2
[   49.031481] input,hidraw0: USB HID v1.11 Mouse [Logitech Logitech USB Optical Mouse] on usb-0000:00:0b.0-6
[   49.031495] usbcore: registered new interface driver usbhid
[   49.031498] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   50.226136] ata1.00: ATAPI: Optiarc DVD RW AD-7530A, EH31, max MWDMA2
[   50.397836] ata1.00: configured for MWDMA2
[   50.397867] ata2: port disabled. ignoring.
[   50.400014] scsi 0:0:0:0: CD-ROM            Optiarc  DVD RW AD-7530A  EH31 PQ: 0 ANSI: 5
[   50.402962] sata_nv 0000:00:0e.0: version 3.5
[   50.402979] PCI: Enabling device 0000:00:0e.0 (0005 -> 0007)
[   50.403270] ACPI: PCI Interrupt Link [LTID] enabled at IRQ 20
[   50.403279] ACPI: PCI Interrupt 0000:00:0e.0[A] -> Link [LTID] -> GSI 20 (level, high) -> IRQ 19
[   50.403316] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[   50.404191] scsi2 : sata_nv
[   50.404372] scsi3 : sata_nv
[   50.404505] ata3: SATA max UDMA/133 cmd 0x30c0 ctl 0x30b4 bmdma 0x3090 irq 19
[   50.404508] ata4: SATA max UDMA/133 cmd 0x30b8 ctl 0x30b0 bmdma 0x3098 irq 19
[   50.868979] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   50.877144] ata3.00: ATA-7: Hitachi HTS541680J9SA00, SB2OC7BP, max UDMA/100
[   50.877147] ata3.00: 156301488 sectors, multi 16: LBA48 
[   50.893124] ata3.00: configured for UDMA/100
[   51.204509] ata4: SATA link down (SStatus 0 SControl 300)
[   51.215132] scsi 2:0:0:0: Direct-Access     ATA      Hitachi HTS54168 SB2O PQ: 0 ANSI: 5
[   51.224669] Driver 'sr' needs updating - please use bus_type methods
[   51.227557] sr0: scsi3-mmc drive: 62x/62x writer dvd-ram cd/rw xa/form2 cdda tray
[   51.227562] Uniform CD-ROM driver Revision: 3.20
[   51.227605] sr 0:0:0:0: Attached scsi CD-ROM sr0
[   51.232335] Driver 'sd' needs updating - please use bus_type methods
[   51.233690] sd 2:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   51.233701] sd 2:0:0:0: [sda] Write Protect is off
[   51.233703] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   51.233718] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   51.233758] sd 2:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   51.233766] sd 2:0:0:0: [sda] Write Protect is off
[   51.233768] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   51.233781] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   51.233784]  sda:<5>sr 0:0:0:0: Attached scsi generic sg0 type 5
[   51.234542] sd 2:0:0:0: Attached scsi generic sg1 type 0
[   51.626993]  sda1 sda2 sda3 < sda5 sda6 >
[   51.660206] sd 2:0:0:0: [sda] Attached SCSI disk
[   52.000279] Attempting manual resume
[   52.000283] swsusp: Resume From Partition 8:6
[   52.000285] PM: Checking swsusp image.
[   52.000489] PM: Resume from disk failed.
[   52.048316] kjournald starting.  Commit interval 5 seconds
[   52.048328] EXT3-fs: mounted filesystem with ordered data mode.
[   62.125792] input: PC Speaker as /devices/platform/pcspkr/input/input3
[   62.195816] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   62.241601] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   62.492230] Linux agpgart interface v0.102
[   62.613112] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x3040
[   62.613127] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x3000
[   62.737752] input: Power Button (FF) as /devices/virtual/input/input4
[   62.748864] ACPI: Power Button (FF) [PWRF]
[   62.748932] input: Power Button (CM) as /devices/virtual/input/input5
[   62.764841] ACPI: Power Button (CM) [PWRB]
[   62.764910] input: Sleep Button (CM) as /devices/virtual/input/input6
[   62.780818] ACPI: Sleep Button (CM) [SLPB]
[   62.780892] input: Lid Switch as /devices/virtual/input/input7
[   62.781788] ACPI: Lid Switch [LID]
[   62.979833] nvidia: module license 'NVIDIA' taints kernel.
[   63.624720] ACPI: Battery Slot [BAT0] (battery present)
[   63.881464] ACPI: AC Adapter [ACAD] (on-line)
[   63.881546] ACPI: WMI-Acer: Mapper loaded
[   64.192328] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:00/input/input8
[   64.214929] ACPI: Video Device [UVGA] (multi-head: yes  rom: no  post: no)
[   64.221154] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:26/LNXVIDEO:01/input/input9
[   64.242869] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   64.472226] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x1a0b1, caps: 0xa04713/0x200000
[   64.529427] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input10
[   65.131047] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 19
[   65.131058] ACPI: PCI Interrupt 0000:00:10.1[B] -> Link [LAZA] -> GSI 19 (level, high) -> IRQ 20
[   65.131081] PCI: Setting latency timer of device 0000:00:10.1 to 64
[   65.387610] ACPI: PCI Interrupt Link [LK3E] enabled at IRQ 18
[   65.387622] ACPI: PCI Interrupt 0000:00:05.0[A] -> Link [LK3E] -> GSI 18 (level, high) -> IRQ 21
[   65.387629] PCI: Setting latency timer of device 0000:00:05.0 to 64
[   65.387823] NVRM: loading NVIDIA UNIX x86 Kernel Module  169.12  Thu Feb 14 17:53:07 PST 2008
[   67.494135] lp: driver loaded but no devices found
[   67.663654] Adding 2939852k swap on /dev/sda6.  Priority:-1 extents:1 across:2939852k
[   68.203539] EXT3 FS on sda5, internal journal
[   68.356300] device-mapper: uevent: version 1.0.3
[   68.356325] device-mapper: ioctl: 4.12.0-ioctl (2007-10-02) initialised: [email]dm-devel@redhat.com[/email]
[   69.719852] ip_tables: (C) 2000-2006 Netfilter Core Team
[   70.171742] No dock devices found.
[   70.514653] powernow-k8: Found 1 AMD Turion(tm) 64 Mobile Technology MK-36 processors (1 cpu cores) (version 2.20.00)
[   70.514686] powernow-k8:    0 : fid 0xc (2000 MHz), vid 0x10
[   70.514688] powernow-k8:    1 : fid 0xa (1800 MHz), vid 0x12
[   70.514690] powernow-k8:    2 : fid 0x8 (1600 MHz), vid 0x14
[   70.514692] powernow-k8:    3 : fid 0x0 (800 MHz), vid 0x18
[   71.322074] apm: BIOS not found.
[   71.461308] ppdev: user-space parallel port driver
[   71.647123] NET: Registered protocol family 10
[   71.647508] lo: Disabled Privacy Extensions
[   71.770813] audit(1226197364.438:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5134 profile="/usr/sbin/cupsd" namespace="default"
[  180.733333] Marking TSC unstable due to: cpufreq changes.
[  180.742820] Time: hpet clocksource has been installed.
[  180.982818] Clocksource tsc unstable (delta = -149837954 ns)
[  188.240409] Bluetooth: Core ver 2.11
[  188.241545] NET: Registered protocol family 31
[  188.241554] Bluetooth: HCI device and connection manager initialized
[  188.241563] Bluetooth: HCI socket layer initialized
[  188.374226] Bluetooth: L2CAP ver 2.9
[  188.374236] Bluetooth: L2CAP socket layer initialized
[  188.448863] Bluetooth: RFCOMM socket layer initialized
[  188.448896] Bluetooth: RFCOMM TTY layer initialized
[  188.448900] Bluetooth: RFCOMM ver 1.8
[  190.730507] NET: Registered protocol family 17
[  209.473314] eth0: no IPv6 routers present
[   97.558695] UDF-fs: Partition marked readonly; forcing readonly mount
[   97.618410] UDF-fs INFO UDF 0.9.8.1 (2004/29/09) Mounting volume '080305_1722', timestamp 2008/03/05 17:22 (1258)
[ 2522.838327] eth0: link down.
[ 2624.107502] usb 1-2: new full speed USB device using ohci_hcd and address 3
[ 2624.322001] usb 1-2: configuration #1 chosen from 1 choice
[ 2624.342488] input: Burr-Brown from TI               USB Audio CODEC  as /devices/pci0000:00/0000:00:0b.0/usb1/1-2/1-2:1.3/input/input11
[ 2624.371579] input,hidraw1: USB HID v1.00 Device [Burr-Brown from TI               USB Audio CODEC ] on usb-0000:00:0b.0-2
[ 1049.172359] usbcore: registered new interface driver snd-usb-audio
[ 3277.599322] eth0: link up.
[ 3277.601420] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 3285.078848] usb 1-2: USB disconnect, address 3
[ 3294.149734] eth0: no IPv6 routers present
[ 3584.269846] usb 1-2: new full speed USB device using ohci_hcd and address 4
[ 3584.484558] usb 1-2: configuration #1 chosen from 1 choice
[ 3584.654245] input: Burr-Brown from TI               USB Audio CODEC  as /devices/pci0000:00/0000:00:0b.0/usb1/1-2/1-2:1.3/input/input12
[ 3584.677872] input,hidraw1: USB HID v1.00 Device [Burr-Brown from TI               USB Audio CODEC ] on usb-0000:00:0b.0-2
[ 5183.503683] glmatrix[10365]: segfault at 0000015c eip b712a8ce esp bfa32f80 error 4
[ 5183.503819] NVRM: Xid (0000:05): 13, 0003 beef3097 00004497 0000021c 00000000 00000002
[ 5187.818590] NVRM: Xid (0000:05): 36,  L1 -> L0
[17484.842192] usb 1-1: new full speed USB device using ohci_hcd and address 5
[17485.056029] usb 1-1: configuration #1 chosen from 1 choice
[ 6986.061014] usbcore: registered new interface driver usbserial
[ 6986.061030] /build/buildd/linux-2.6.24/drivers/usb/serial/usb-serial.c: USB Serial support registered for generic
[ 6986.061049] usbcore: registered new interface driver usbserial_generic
[ 6986.061052] /build/buildd/linux-2.6.24/drivers/usb/serial/usb-serial.c: USB Serial Driver core
[ 6986.086415] /build/buildd/linux-2.6.24/drivers/usb/serial/usb-serial.c: USB Serial support registered for pl2303
[ 6986.086457] pl2303 1-1:1.0: pl2303 converter detected
[ 6986.086601] usb 1-1: pl2303 converter now attached to ttyUSB0
[ 6986.086610] usbcore: registered new interface driver pl2303
[ 6986.086613] /build/buildd/linux-2.6.24/drivers/usb/serial/pl2303.c: Prolific PL2303 USB to serial adaptor driver
[14222.626042] glmatrix[15814]: segfault at 0000015c eip b70ad8ce esp bf82a570 error 4
[14222.626196] NVRM: Xid (0000:05): 13, 0003 beef3097 00004497 0000021c 00000000 00000002
[14226.940969] NVRM: Xid (0000:05): 36,  L0 -> L0
chris@chris-laptop:~$ 

not familiar with '| grep' commands....didn't produce anything will search the noob's commands posts!!

Chris

---

### Post by pytheas22 on 2008-11-09
It doesn't look like the system is trying to load a driver for your card at all, but it should be if you're using 8.04.  Please try running these commands (make sure you are plugged into the Internet via ethernet first, if possible...if that's impossible we can work around it):
```

sudo apt-get update
sudo apt-get install b43-fwcutter
echo b43 | sudo tee -a /etc/modules
```

Then reboot.  Does the wireless work?  If not, what is the output of these commands, in this order:
```

lsmod | grep b43
sudo modprobe b43
lshw -C Network
dmesg | grep -e b43 -e wlan
```

(Note that with the 'lshw -C Network' command, you need to wait a few seconds before it shows meaningful information...just type it, press enter, count to five and by then you should see something on the screen that you can copy here.)

---

### Post by NewNerd99 on 2008-11-09
Thanks for your time.

All outputs from commands are listed below

When I put in the "lshw -C Network" command it went through a few functions (PCI etc) but did not print anything to the terminal.

...and the final command "dmesg | grep -e b43 -e wlan" did not print up anything

Just confirm that I'm entering them correctly. I simply copy each line as written and paste it into terminal?

Cheers
Chris



chris@chris-laptop:~$ sudo apt-get install b43-fwcutter
Reading package lists... Done
Building dependency tree       
Reading state information... Done
b43-fwcutter is already the newest version.
The following packages were automatically installed and are no longer required:
  libqt4-core libqt4-gui
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
chris@chris-laptop:~$ 

chris@chris-laptop:~$ echo b43 | sudo tee -a /etc/modules
b43
chris@chris-laptop:~$ 


chris@chris-laptop:~$ lsmod | grep b43
b43                   144548  0 
ssb                    34308  1 b43
rfkill                  8596  1 b43
mac80211              165652  1 b43
led_class               6020  1 b43
input_polldev           5896  1 b43
chris@chris-laptop:~$ sudo modprobe b43
[sudo] password for chris: 
WARNING: /etc/modprobe.d/blacklist line 43: ignoring bad line starting with 'sudo'
chris@chris-laptop:~$ lshw -C Network
WARNING: you should run this program as super-user.
chris@chris-laptop:~$ dmesg | grep -e b43 -e wlan
chris@chris-laptop:~$

---

### Post by pytheas22 on 2008-11-09
Quite strange...you have the b43 module loaded and the firmware seems to exist, but it doesn't seem to be bringing up an interface at all.  I'm not sure why.  Also, it's really weird that 'lshw -C Network' doesn't return anything--and yes, if you were copying and pasting those commands, you should have entered them correctly.

Could you please post the output of these commands, in this order:
```

iwconfig
sudo rmmod b43
sudo modprobe b43
iwconfig
sudo iwlist scan
ls /lib/firmware
cat /etc/modprobe.d/blacklist
modinfo b43
```

I know that's a lot of stuff but hopefully it will help to get to the bottom of whatever's going on.

Also, another thing worth testing is to see if your wireless works under an older kernel.  At the grub boot menu, which you should see on your screen right after BIOS finishes and before Ubuntu starts to boot (you may need to press escape to enter the boot menu; if so, you'll see a message to that effect displayed on your screen for a few seconds), you should have several different kernels to choose from, in addition to 'recovery-mode' stuff.  The newest kernel is at the top of the list.  Try choosing one of the older kernels; does your wireless work if you boot into that?

---

### Post by NewNerd99 on 2008-11-10
No joy on the older kernel....
If you don't here back from me for the rest of the week I'm not being rude, I have to go away until Friday with work.

Thanks for the ideas so far, hope the following helps

Cheers
Chris




chris@chris-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

chris@chris-laptop:~$ 


chris@chris-laptop:~$ sudo rmmod b43
[sudo] password for chris: 
chris@chris-laptop:~$ 


chris@chris-laptop:~$ sudo modprobe b43
WARNING: /etc/modprobe.d/blacklist line 43: ignoring bad line starting with 'sudo'
chris@chris-laptop:~$ 



chris@chris-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

chris@chris-laptop:~$ 


chris@chris-laptop:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

chris@chris-laptop:~$ 



chris@chris-laptop:~$ ls /lib/firmware
2.6.24-16-generic     bcm43xx_initval03.fw  bcm43xx_initval10.fw
2.6.24-19-generic     bcm43xx_initval04.fw  bcm43xx_microcode11.fw
2.6.24-21-generic     bcm43xx_initval05.fw  bcm43xx_microcode2.fw
b43                   bcm43xx_initval06.fw  bcm43xx_microcode4.fw
b43legacy             bcm43xx_initval07.fw  bcm43xx_microcode5.fw
bcm43xx_initval01.fw  bcm43xx_initval08.fw  bcm43xx_pcm4.fw
bcm43xx_initval02.fw  bcm43xx_initval09.fw  bcm43xx_pcm5.fw
chris@chris-laptop:~$ 


chris@chris-laptop:~$ cat /etc/modprobe.d/blacklist
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

blacklist ndiswrapper 


sudo apt-get install ndiswrapper-utils-1.9
chris@chris-laptop:~$ 



chris@chris-laptop:~$ modinfo b43
filename:       /lib/modules/2.6.24-21-generic/kernel/drivers/net/wireless/b43/b43.ko
license:        GPL
author:         Michael Buesch
author:         Stefano Brivio
author:         Martin Langer
description:    Broadcom B43 wireless driver
srcversion:     A63CC27F8D98EBDFDB9623F
alias:          ssb:v4243id0812rev0F*
alias:          ssb:v4243id0812rev0D*
alias:          ssb:v4243id0812rev0B*
alias:          ssb:v4243id0812rev0A*
alias:          ssb:v4243id0812rev09*
alias:          ssb:v4243id0812rev07*
alias:          ssb:v4243id0812rev06*
alias:          ssb:v4243id0812rev05*
depends:        mac80211,ssb,input-polldev,led-class,rfkill
vermagic:       2.6.24-21-generic SMP mod_unload 586 
parm:           pio:enable(1) / disable(0) PIO mode (int)
parm:           bad_frames_preempt:enable(1) / disable(0) Bad Frames Preemption (int)
parm:           short_retry:Short-Retry-Limit (0 - 15) (int)
parm:           long_retry:Long-Retry-Limit (0 - 15) (int)
parm:           fwpostfix:Postfix for the .fw files to load. (string)
parm:           hwpctl:Enable hardware-side power control (default off) (int)
parm:           nohwcrypt:Disable hardware encryption. (int)
chris@chris-laptop:~$

---

### Post by pytheas22 on 2008-11-10
I've noticed something interesting that I should have seen before.  In the output of 'lspci -nn', no Broadcom wireless card (or any other kind of wireless card) is mentioned anywhere.  This explains a lot--it appears that Ubuntu can't detect the presence of the hardware at all.

This means that either you're experiencing hardware failure, or that the wireless is disabled in BIOS or something.  Please check on that.  It would also be good to know whether the wireless works in Windows, if you have it installed on the same machine, or from the Ubuntu live CD (at least get an 'lspci' reading from the live environment to see if it detects the wireless card).

---

### Post by NewNerd99 on 2008-11-13
Thanks for the return.

I first noticed that it wasn't there to be enabled in the driver section which led me to suspect a bigger problem.

How do I run 'lspci in a live environment'?

Chris

---

### Post by pytheas22 on 2008-11-13
> 
How do I run 'lspci in a live environment'?

Easy: just boot to the Ubuntu live CD, open a terminal there and run the command 'lspci -nn'.  Then please post the output here.  Also, does Hardware Drivers detect your wireless card under the live CD?

This will help us to know whether the problem is with your hardware itself, or with some misconfiguration in your Ubuntu installation.

---

### Post by NewNerd99 on 2011-12-25
brushing some dust off a netbook and trying to work out why the wireless is not working....

Works fine in Windows 7

Hope I can get it running again.

Cheers
Chris

ubuntu@ubuntu:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GME Express Memory Controller Hub [8086:27ac] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GME Express Integrated Graphics Controller [8086:27ae] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 1 [8086:27d0] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 2 [8086:27d2] (rev 02)
00:1c.2 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 3 [8086:27d4] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 [8086:27c8] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 [8086:27c9] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 [8086:27ca] (rev 02)
00:1d.3 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 [8086:27cb] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller [8086:27cc] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801G (ICH7 Family) IDE Controller [8086:27df] (rev 02)
00:1f.2 IDE interface [0101]: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller [8086:27c4] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation N10/ICH 7 Family SMBus Controller [8086:27da] (rev 02)
04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 01)
ubuntu@ubuntu:~$

---

### Post by pytheas22 on 2011-12-25
I don't see anything in your lspci output that looks like a Broadcom wireless card, which means Ubuntu thinks the hardware is not even present.  I know you say it works in Windows but just to double-check, are you positive it's connected and enabled in BIOS, etc.?  It would also be helpful if you mentioned which version of Ubuntu you're currently using and posted the output of:
```

lshw -C Network
dmesg
```

---

### Post by NewNerd99 on 2011-12-25
Sorry Pytheas,
    After I posted I realised this thread was talking about a laptop with a separate issue so I closed the thread (SOLVED) and reposted under a new thread.

[http://ubuntuforums.org/showthread.php?t=1899999](http://ubuntuforums.org/showthread.php?t=1899999)

Sorry again for the inconvenience and thanks for your reply.

Cheers
Chris

---

### Post by pytheas22 on 2011-12-26
> Sorry Pytheas,
After I posted I realised this thread was talking about a laptop with a separate issue so I closed the thread (SOLVED) and reposted under a new thread.

[http://ubuntuforums.org/showthread.php?t=1899999](http://ubuntuforums.org/showthread.php?t=1899999)

Sorry again for the inconvenience and thanks for your reply.

Cheers
Chris

No worries.  I see that someone else has already helped you in the other thread.  Sorry that it appears there's no native Linux driver that will work as desired for your card, but I'd second the recommendation to try ndiswrapper, which should support all types of encryption.

---

