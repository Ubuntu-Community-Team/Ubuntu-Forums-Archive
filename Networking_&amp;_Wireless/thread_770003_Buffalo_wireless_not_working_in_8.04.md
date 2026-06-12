---
title: "Buffalo wireless not working in 8.04"
date: 2008-04-27
forum: Networking &amp; Wireless
---

### Post by Ceox on 2008-04-27
Hey,

Yesterday I installed Ubuntu next to my Windows.
In my computer there is a Buffalo AirStation Wireless-G stick, which should connect to a Buffalo AirStation WHR-HP-G54 -adapter. It does do that in Windows, but in Ubuntu I've had problems. 
It did detect the adapter and when I clicked on it in the top right corner I had to give the password, I gave it and then it started connecting, but it got stuck in the phase where there was one green ball and this circling thing (see screenshot) and after a while it stopped trying. When there was that green ball it said "Retrieving key" or something like that.
Someone told me to enter dmesg into the command line thingy and here's the result:
```
[    0.000000]     0:        0 ->      159
[    0.000000]     0:      256 ->   262128
[    0.000000] On node 0 totalpages: 262031
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 1207 pages reserved
[    0.000000]   DMA zone: 2736 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 3527 pages used for memmap
[    0.000000]   DMA32 zone: 254505 pages, LIFO batch:31
[    0.000000]   Normal zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] Nvidia board detected. Ignoring ACPI timer override.
[    0.000000] If you got timer trouble try acpi_use_timer_override
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 (Bootup-CPU)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: BIOS IRQ0 pin2 override ignored.
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.
[    0.000000] Setting APIC routing to flat
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:a0000000)
[    0.000000] SMP: Allowing 2 CPUs, 1 hotplug CPUs
[    0.000000] PERCPU: Allocating 34656 bytes of per cpu data
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 257241
[    0.000000] Policy zone: DMA32
[    0.000000] Kernel command line: root=UUID=1A686EAA686E83FB loop=/ubuntu/disks/root.disk ro quiet splash
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] TSC calibrated against PM_TIMER
[   26.446207] time.c: Detected 2211.328 MHz processor.
[   26.447165] Console: colour VGA+ 80x25
[   26.447168] console [tty0] enabled
[   26.447182] Checking aperture...
[   26.447185] CPU 0: aperture @ 8c000000 size 32 MB
[   26.447186] Aperture too small (32 MB)
[   26.452090] No AGP bridge found
[   26.461327] Memory: 1020576k/1048512k available (2466k kernel code, 27548k reserved, 1309k data, 316k init)
[   26.461361] SLUB: Genslabs=12, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   26.540185] Calibrating delay using timer specific routine.. 4425.42 BogoMIPS (lpj=8850841)
[   26.540215] Security Framework initialized
[   26.540222] SELinux:  Disabled at boot.
[   26.540235] AppArmor: AppArmor initialized
[   26.540239] Failure registering capabilities with primary security module.
[   26.540320] Dentry cache hash table entries: 131072 (order: 8, 1048576 bytes)
[   26.540960] Inode-cache hash table entries: 65536 (order: 7, 524288 bytes)
[   26.541264] Mount-cache hash table entries: 256
[   26.541394] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   26.541395] CPU: L2 Cache: 512K (64 bytes/line)
[   26.541398] CPU 0/0 -> Node 0
[   26.541419] SMP alternatives: switching to UP code
[   26.541953] Early unpacking initramfs... done
[   26.836537] ACPI: Core revision 20070126
[   26.836592] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   26.881078] Using local APIC timer interrupts.
[   26.926297] APIC timer calibration result 12564366
[   26.926298] Detected 12.564 MHz APIC timer.
[   26.926349] Brought up 1 CPUs
[   26.926414] CPU0 attaching sched-domain:
[   26.926416]  domain 0: span 01
[   26.926418]   groups: 01
[   26.926557] net_namespace: 120 bytes
[   26.926923] Time: 14:37:25  Date: 04/26/08
[   26.926949] NET: Registered protocol family 16
[   26.927095] ACPI: bus type pci registered
[   26.927155] PCI: Using configuration type 1
[   26.928396] ACPI: EC: Look up EC in DSDT
[   26.935516] ACPI: Interpreter enabled
[   26.935519] ACPI: (supports S0 S3 S4 S5)
[   26.935533] ACPI: Using IOAPIC for interrupt routing
[   26.943180] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   26.943591] PCI: Transparent bridge - 0000:00:09.0
[   26.943844] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   26.944138] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[   26.998881] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   26.999068] ACPI: PCI Interrupt Link [LNK2] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   26.999255] ACPI: PCI Interrupt Link [LNK3] (IRQs 3 4 *5 7 9 10 11 12 14 15)
[   26.999443] ACPI: PCI Interrupt Link [LNK4] (IRQs 3 4 5 7 9 *10 11 12 14 15)
[   26.999628] ACPI: PCI Interrupt Link [LNK5] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   26.999820] ACPI: PCI Interrupt Link [LUBA] (IRQs 3 4 *5 7 9 10 11 12 14 15)
[   27.000009] ACPI: PCI Interrupt Link [LUBB] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   27.000196] ACPI: PCI Interrupt Link [LMAC] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[   27.000382] ACPI: PCI Interrupt Link [LACI] (IRQs *3 4 5 7 9 10 11 12 14 15)
[   27.000568] ACPI: PCI Interrupt Link [LMCI] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   27.000755] ACPI: PCI Interrupt Link [LSMB] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[   27.000941] ACPI: PCI Interrupt Link [LUB2] (IRQs *3 4 5 7 9 10 11 12 14 15)
[   27.001129] ACPI: PCI Interrupt Link [LIDE] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   27.001323] ACPI: PCI Interrupt Link [LSID] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[   27.001520] ACPI: PCI Interrupt Link [LFID] (IRQs 3 4 5 7 9 *10 11 12 14 15)
[   27.001715] ACPI: PCI Interrupt Link [LPCA] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   27.001918] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0, disabled.
[   27.002115] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.
[   27.002318] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0
[   27.002515] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0
[   27.002648] ACPI: PCI Interrupt Link [APC5] (IRQs *16), disabled.
[   27.002848] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22 23) *0
[   27.003047] ACPI: PCI Interrupt Link [APCG] (IRQs 20 21 22 23) *0, disabled.
[   27.003247] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0
[   27.003446] ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22 23) *0
[   27.003645] ACPI: PCI Interrupt Link [APCK] (IRQs 20 21 22 23) *0, disabled.
[   27.003844] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0
[   27.004043] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22 23) *0
[   27.004242] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.
[   27.004451] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0
[   27.004657] ACPI: PCI Interrupt Link [APSJ] (IRQs 20 21 22 23) *0
[   27.004862] ACPI: PCI Interrupt Link [APCP] (IRQs 20 21 22 23) *0, disabled.
[   27.004978] Linux Plug and Play Support v0.97 (c) Adam Belay
[   27.005000] pnp: PnP ACPI init
[   27.005007] ACPI: bus type pnp registered
[   27.008637] pnpacpi: exceeded the max number of mem resources: 12
[   27.008691] pnp: PnP ACPI: found 11 devices
[   27.008693] ACPI: ACPI bus type pnp unregistered
[   27.008877] PCI: Using ACPI for IRQ routing
[   27.008880] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   27.018328] NET: Registered protocol family 8
[   27.018330] NET: Registered protocol family 20
[   27.018427] AppArmor: AppArmor Filesystem Enabled
[   27.022298] Time: tsc clocksource has been installed.
[   27.030325] system 00:01: ioport range 0x4000-0x407f has been reserved
[   27.030327] system 00:01: ioport range 0x4080-0x40ff has been reserved
[   27.030329] system 00:01: ioport range 0x4400-0x447f has been reserved
[   27.030331] system 00:01: ioport range 0x4480-0x44ff has been reserved
[   27.030333] system 00:01: ioport range 0x4800-0x487f has been reserved
[   27.030335] system 00:01: ioport range 0x4880-0x48ff has been reserved
[   27.030341] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
[   27.030343] system 00:02: ioport range 0x800-0x87f has been reserved
[   27.030350] system 00:09: iomem range 0xe0000000-0xefffffff could not be reserved
[   27.030356] system 00:0a: iomem range 0xf0000-0xf3fff could not be reserved
[   27.030359] system 00:0a: iomem range 0xf4000-0xf7fff could not be reserved
[   27.030361] system 00:0a: iomem range 0xf8000-0xfbfff could not be reserved
[   27.030363] system 00:0a: iomem range 0xfc000-0xfffff could not be reserved
[   27.030365] system 00:0a: iomem range 0x3fff0000-0x3fffffff could not be reserved
[   27.030367] system 00:0a: iomem range 0xffff0000-0xffffffff has been reserved
[   27.030369] system 00:0a: iomem range 0x0-0x9ffff could not be reserved
[   27.030371] system 00:0a: iomem range 0x100000-0x3ffeffff could not be reserved
[   27.030374] system 00:0a: iomem range 0xfec00000-0xfec00fff has been reserved
[   27.030376] system 00:0a: iomem range 0xfee00000-0xfeefffff could not be reserved
[   27.030378] system 00:0a: iomem range 0xfefff000-0xfeffffff has been reserved
[   27.030380] system 00:0a: iomem range 0xfff80000-0xfff80fff has been reserved
[   27.030681] PCI: Bridge: 0000:00:09.0
[   27.030683]   IO window: a000-afff
[   27.030686]   MEM window: d6000000-d60fffff
[   27.030687]   PREFETCH window: disabled.
[   27.030689] PCI: Bridge: 0000:00:0b.0
[   27.030690]   IO window: disabled.
[   27.030692]   MEM window: disabled.
[   27.030693]   PREFETCH window: disabled.
[   27.030695] PCI: Bridge: 0000:00:0c.0
[   27.030696]   IO window: disabled.
[   27.030698]   MEM window: disabled.
[   27.030699]   PREFETCH window: disabled.
[   27.030701] PCI: Bridge: 0000:00:0d.0
[   27.030702]   IO window: disabled.
[   27.030704]   MEM window: disabled.
[   27.030705]   PREFETCH window: disabled.
[   27.030709] PCI: Bridge: 0000:00:0e.0
[   27.030711]   IO window: 9000-9fff
[   27.030713]   MEM window: d4000000-d5ffffff
[   27.030714]   PREFETCH window: d0000000-d3ffffff
[   27.030721] PCI: Setting latency timer of device 0000:00:09.0 to 64
[   27.030729] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[   27.030735] PCI: Setting latency timer of device 0000:00:0c.0 to 64
[   27.030739] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[   27.030744] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[   27.030787] NET: Registered protocol family 2
[   27.066365] IP route cache hash table entries: 32768 (order: 6, 262144 bytes)
[   27.066761] TCP established hash table entries: 131072 (order: 9, 2097152 bytes)
[   27.068022] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   27.068624] TCP: Hash tables configured (established 131072 bind 65536)
[   27.068627] TCP reno registered
[   27.078429] checking if image is initramfs... it is
[   27.534225] Switched to high resolution mode on CPU 0
[   27.733534] Freeing initrd memory: 8212k freed
[   27.739020] audit: initializing netlink socket (disabled)
[   27.739033] audit(1209220645.260:1): initialized
[   27.740601] VFS: Disk quotas dquot_6.5.1
[   27.740662] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   27.740776] io scheduler noop registered
[   27.740778] io scheduler anticipatory registered
[   27.740780] io scheduler deadline registered
[   27.740863] io scheduler cfq registered (default)
[   27.754319] PCI: Found disabled HT MSI Mapping on 0000:00:0b.0
[   27.754329] PCI: Found enabled HT MSI Mapping on 0000:00:00.0
[   27.754334] PCI: Found disabled HT MSI Mapping on 0000:00:0c.0
[   27.754340] PCI: Found enabled HT MSI Mapping on 0000:00:00.0
[   27.754345] PCI: Found disabled HT MSI Mapping on 0000:00:0d.0
[   27.754351] PCI: Found enabled HT MSI Mapping on 0000:00:00.0
[   27.754355] PCI: Found disabled HT MSI Mapping on 0000:00:0e.0
[   27.754361] PCI: Found enabled HT MSI Mapping on 0000:00:00.0
[   27.754368] Boot video device is 0000:01:00.0
[   27.754502] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[   27.754519] assign_interrupt_mode Found MSI capability
[   27.754534] Allocate Port Service[0000:00:0b.0:pcie00]
[   27.754583] PCI: Setting latency timer of device 0000:00:0c.0 to 64
[   27.754598] assign_interrupt_mode Found MSI capability
[   27.754610] Allocate Port Service[0000:00:0c.0:pcie00]
[   27.754654] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[   27.754670] assign_interrupt_mode Found MSI capability
[   27.754681] Allocate Port Service[0000:00:0d.0:pcie00]
[   27.754726] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[   27.754742] assign_interrupt_mode Found MSI capability
[   27.754752] Allocate Port Service[0000:00:0e.0:pcie00]
[   27.776522] Real Time Clock Driver v1.12ac
[   27.776597] Linux agpgart interface v0.102
[   27.776599] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   27.776702] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   27.777148] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   27.777696] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   27.777749] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   27.777849] PNP: No PS/2 controller found. Probing ports directly.
[   27.780350] serio: i8042 KBD port at 0x60,0x64 irq 1
[   27.780354] serio: i8042 AUX port at 0x60,0x64 irq 12
[   27.786281] mice: PS/2 mouse device common for all mice
[   27.786309] cpuidle: using governor ladder
[   27.786311] cpuidle: using governor menu
[   27.786435] NET: Registered protocol family 1
[   27.786482] registered taskstats version 1
[   27.786597]   Magic number: 4:8:638
[   27.786713] /build/buildd/linux-2.6.24/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   27.786717] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   27.786718] EDD information not available.
[   27.786725] Freeing unused kernel memory: 316k freed
[   28.949828] fuse init (API version 7.9)
[   28.962043] ACPI: Fan [FAN] (on)
[   28.966836] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[   28.970832] ACPI: Thermal Zone [THRM] (40 C)
[   29.563155] usbcore: registered new interface driver usbfs
[   29.563175] usbcore: registered new interface driver hub
[   29.573846] usbcore: registered new device driver usb
[   29.603568] SCSI subsystem initialized
[   29.612667] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   29.613041] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 23
[   29.613049] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [APCF] -> GSI 23 (level, low) -> IRQ 23
[   29.613120] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   29.613126] ohci_hcd 0000:00:02.0: OHCI Host Controller
[   29.613319] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
[   29.613334] ohci_hcd 0000:00:02.0: irq 23, io mem 0xd6104000
[   29.652585] libata version 3.00 loaded.
[   29.667906] usb usb1: configuration #1 chosen from 1 choice
[   29.667929] hub 1-0:1.0: USB hub found
[   29.667936] hub 1-0:1.0: 8 ports detected
[   29.770307] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 22
[   29.770316] ACPI: PCI Interrupt 0000:00:02.1[B] -> Link [APCL] -> GSI 22 (level, low) -> IRQ 22
[   29.770406] PCI: Setting latency timer of device 0000:00:02.1 to 64
[   29.770412] ehci_hcd 0000:00:02.1: EHCI Host Controller
[   29.770457] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 2
[   29.770482] ehci_hcd 0000:00:02.1: debug port 1
[   29.770485] PCI: cache line size of 64 is not supported by device 0000:00:02.1
[   29.770495] ehci_hcd 0000:00:02.1: irq 22, io mem 0xfeb00000
[   29.781745] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   29.781852] usb usb2: configuration #1 chosen from 1 choice
[   29.781875] hub 2-0:1.0: USB hub found
[   29.781881] hub 2-0:1.0: 8 ports detected
[   29.885873] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
[   29.886222] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 21
[   29.886230] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [APCH] -> GSI 21 (level, low) -> IRQ 21
[   29.886234] PCI: Setting latency timer of device 0000:00:0a.0 to 64
[   30.405937] forcedeth 0000:00:0a.0: ifname eth0, PHY OUI 0x20 @ 1, addr 00:17:31:08:5a:89
[   30.405942] forcedeth 0000:00:0a.0: highdma csum timirq lnktim desc-v3
[   30.406253] pata_amd 0000:00:06.0: version 0.3.10
[   30.406303] PCI: Setting latency timer of device 0000:00:06.0 to 64
[   30.407104] scsi0 : pata_amd
[   30.407455] scsi1 : pata_amd
[   30.408005] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[   30.408008] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[   30.681549] usb 2-1: new high speed USB device using ehci_hcd and address 2
[   30.847432] usb 2-1: configuration #1 chosen from 1 choice
[   30.889783] ata2.00: ATAPI: _NEC DVD_RW ND-4550A, 1.84, max UDMA/33
[   31.061671] ata2.00: configured for UDMA/33
[   31.062836] scsi 1:0:0:0: CD-ROM            _NEC     DVD_RW ND-4550A  1.84 PQ: 0 ANSI: 5
[   31.065478] sata_nv 0000:00:07.0: version 3.5
[   31.065882] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 20
[   31.065889] ACPI: PCI Interrupt 0000:00:07.0[A] -> Link [APSI] -> GSI 20 (level, low) -> IRQ 20
[   31.065893] sata_nv 0000:00:07.0: Using ADMA mode
[   31.066011] PCI: Setting latency timer of device 0000:00:07.0 to 64
[   31.067097] scsi2 : sata_nv
[   31.067362] scsi3 : sata_nv
[   31.067533] ata3: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xd800 irq 20
[   31.067536] ata4: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xd808 irq 20
[   31.377394] ata3: SATA link down (SStatus 0 SControl 300)
[   31.689336] ata4: SATA link down (SStatus 0 SControl 300)
[   31.689783] ACPI: PCI Interrupt Link [APSJ] enabled at IRQ 23
[   31.689786] ACPI: PCI Interrupt 0000:00:08.0[A] -> Link [APSJ] -> GSI 23 (level, low) -> IRQ 23
[   31.689790] sata_nv 0000:00:08.0: Using ADMA mode
[   31.689917] PCI: Setting latency timer of device 0000:00:08.0 to 64
[   31.690020] scsi4 : sata_nv
[   31.690263] scsi5 : sata_nv
[   31.690423] ata5: SATA max UDMA/133 cmd 0x9e0 ctl 0xbe0 bmdma 0xc400 irq 23
[   31.690426] ata6: SATA max UDMA/133 cmd 0x960 ctl 0xb60 bmdma 0xc408 irq 23
[   31.693340] usb 2-7: new high speed USB device using ehci_hcd and address 6
[   31.916779] usb 2-7: configuration #1 chosen from 1 choice
[   32.157239] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   32.207902] ata5.00: ATA-7: ST3250824AS, 3.AAE, max UDMA/133
[   32.207906] ata5.00: 488397168 sectors, multi 1: LBA48 NCQ (depth 31/32)
[   32.221220] usb 1-2: new low speed USB device using ohci_hcd and address 2
[   32.274518] ata5.00: configured for UDMA/133
[   32.435474] usb 1-2: configuration #1 chosen from 1 choice
[   32.585141] ata6: SATA link down (SStatus 0 SControl 300)
[   32.585236] scsi 4:0:0:0: Direct-Access     ATA      ST3250824AS      3.AA PQ: 0 ANSI: 5
[   32.585242] ata5: bounce limit 0xFFFFFFFFFFFFFFFF, segment boundary 0xFFFFFFFF, hw segs 61
[   32.587018] ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19
[   32.587027] ACPI: PCI Interrupt 0000:05:02.0[A] -> Link [APC4] -> GSI 19 (level, low) -> IRQ 19
[   32.640173] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[19]  MMIO=[d6000000-d60007ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   32.660944] Driver 'sr' needs updating - please use bus_type methods
[   32.665202] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[   32.665207] Uniform CD-ROM driver Revision: 3.20
[   32.665250] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   32.670099] Driver 'sd' needs updating - please use bus_type methods
[   32.671408] sd 4:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[   32.671417] sd 4:0:0:0: [sda] Write Protect is off
[   32.671419] sd 4:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   32.671431] sd 4:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   32.671466] sd 4:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[   32.671473] sd 4:0:0:0: [sda] Write Protect is off
[   32.671475] sd 4:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   32.671485] sd 4:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   32.671488]  sda:<5>sr 1:0:0:0: Attached scsi generic sg0 type 5
[   32.672083] sd 4:0:0:0: Attached scsi generic sg1 type 0
[   32.688972]  sda1
[   32.689028] sd 4:0:0:0: [sda] Attached SCSI disk
[   32.757262] usb 1-3: new low speed USB device using ohci_hcd and address 3
[   32.962401] usb 1-3: configuration #1 chosen from 1 choice
[   33.224824] loop: module loaded
[   33.236551] EXT3-fs: INFO: recovery required on readonly filesystem.
[   33.236555] EXT3-fs: write access will be enabled during recovery.
[   33.269016] usb 1-4: new full speed USB device using ohci_hcd and address 4
[   33.346040] kjournald starting.  Commit interval 5 seconds
[   33.346057] EXT3-fs: loop0: orphan cleanup on readonly fs
[   33.346063] ext3_orphan_cleanup: deleting unreferenced inode 72300
[   33.346088] EXT3-fs: loop0: 1 orphan inode deleted
[   33.346090] EXT3-fs: recovery complete.
[   33.346759] EXT3-fs: mounted filesystem with ordered data mode.
[   33.483350] usb 1-4: configuration #1 chosen from 1 choice
[   33.486429] usbcore: registered new interface driver libusual
[   33.486559] usbcore: registered new interface driver hiddev
[   33.491376] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:02.0/usb1/1-2/1-2:1.0/input/input1
[   33.505008] input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:02.0-2
[   33.511392] input: HID 1267:0103 as /devices/pci0000:00/0000:00:02.0/usb1/1-3/1-3:1.0/input/input2
[   33.520990] input,hidraw1: USB HID v1.10 Keyboard [HID 1267:0103] on usb-0000:00:02.0-3
[   33.531296] input: HID 1267:0103 as /devices/pci0000:00/0000:00:02.0/usb1/1-3/1-3:1.1/input/input3
[   33.540962] input,hidraw2: USB HID v1.10 Device [HID 1267:0103] on usb-0000:00:02.0-3
[   33.540979] usbcore: registered new interface driver usbhid
[   33.540982] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   33.845375] Initializing USB Mass Storage driver...
[   33.845433] scsi6 : SCSI emulation for USB Mass Storage devices
[   33.845485] usbcore: registered new interface driver usb-storage
[   33.845488] USB Mass Storage support registered.
[   33.845965] usb-storage: device found at 6
[   33.845969] usb-storage: waiting for device to settle before scanning
[   33.916966] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0011d800009e40a9]
[   38.843967] usb-storage: device scan complete
[   38.874714] scsi 6:0:0:0: Direct-Access     Generic  2.0 Reader   -CF 1.20 PQ: 0 ANSI: 0 CCS
[   38.905708] scsi 6:0:0:1: Direct-Access     Generic  2.0 Reader   -SM 1.20 PQ: 0 ANSI: 0 CCS
[   38.936702] scsi 6:0:0:2: Direct-Access     Generic  2.0 Reader   -SD 1.20 PQ: 0 ANSI: 0 CCS
[   38.967698] scsi 6:0:0:3: Direct-Access     Generic  2.0 Reader   -MS 1.20 PQ: 0 ANSI: 0 CCS
[   38.998692] scsi 6:0:0:4: Direct-Access     Generic  2.0 Reader   -xD 1.20 PQ: 0 ANSI: 0 CCS
[   39.002478] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[   39.002517] sd 6:0:0:0: Attached scsi generic sg2 type 0
[   39.006490] sd 6:0:0:1: [sdc] Attached SCSI removable disk
[   39.006526] sd 6:0:0:1: Attached scsi generic sg3 type 0
[   39.010468] sd 6:0:0:2: [sdd] Attached SCSI removable disk
[   39.010505] sd 6:0:0:2: Attached scsi generic sg4 type 0
[   39.014525] sd 6:0:0:3: [sde] Attached SCSI removable disk
[   39.014559] sd 6:0:0:3: Attached scsi generic sg5 type 0
[   39.018591] sd 6:0:0:4: [sdf] Attached SCSI removable disk
[   39.018627] sd 6:0:0:4: Attached scsi generic sg6 type 0
[   39.507845] input: Power Button (FF) as /devices/virtual/input/input4
[   39.523709] ACPI: Power Button (FF) [PWRF]
[   39.523788] input: Power Button (CM) as /devices/virtual/input/input5
[   39.539704] ACPI: Power Button (CM) [PWRB]
[   39.559797] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x4c00
[   39.559810] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x4c40
[   41.291929] ACPI: PCI Interrupt Link [APCJ] enabled at IRQ 22
[   41.291934] ACPI: PCI Interrupt 0000:00:04.0[A] -> Link [APCJ] -> GSI 22 (level, low) -> IRQ 22
[   41.292046] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   41.615279] intel8x0_measure_ac97_clock: measured 54881 usecs
[   41.615284] intel8x0: clocking to 46901
[   41.811957] usbcore: registered new interface driver snd-usb-audio
[   42.150582] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   42.179204] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   42.242411] phy0: Selected rate control algorithm 'simple'
[   42.331248] input: PC Speaker as /devices/platform/pcspkr/input/input6
[   42.491467] usbcore: registered new interface driver rt2500usb
[   42.827130] parport_pc 00:08: reported by Plug and Play ACPI
[   42.827156] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
[   45.835288] lp0: using parport0 (interrupt-driven).
[   46.473926] EXT3 FS on loop0, internal journal
[   49.812795] Adding 390616k swap on /host/ubuntu/disks/swap.disk.  Priority:-1 extents:1 across:390616k
[   50.105342] ip_tables: (C) 2000-2006 Netfilter Core Team
[   50.400236] No dock devices found.
[   50.606945] powernow-k8: Found 1 AMD Athlon(tm) 64 Processor 3500+ processors (1 cpu cores) (version 2.20.00)
[   50.606983] powernow-k8:    0 : fid 0xe (2200 MHz), vid 0x6
[   50.606985] powernow-k8:    1 : fid 0xc (2000 MHz), vid 0x8
[   50.606986] powernow-k8:    2 : fid 0xa (1800 MHz), vid 0xa
[   50.606988] powernow-k8:    3 : fid 0x2 (1000 MHz), vid 0x12
[   51.276095] ppdev: user-space parallel port driver
[   51.349266] audit(1209209869.590:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5161 profile="/usr/sbin/cupsd" namespace="default"
[   52.051685] eth0: no link during initialization.
[   52.089839] Bluetooth: Core ver 2.11
[   52.090589] NET: Registered protocol family 31
[   52.090593] Bluetooth: HCI device and connection manager initialized
[   52.090596] Bluetooth: HCI socket layer initialized
[   52.115089] Bluetooth: L2CAP ver 2.9
[   52.115093] Bluetooth: L2CAP socket layer initialized
[   52.133088] Bluetooth: RFCOMM socket layer initialized
[   52.133105] Bluetooth: RFCOMM TTY layer initialized
[   52.133107] Bluetooth: RFCOMM ver 1.8
[   53.412947] Marking TSC unstable due to cpufreq changes
[   53.416798] Time: acpi_pm clocksource has been installed.
[   53.465890] Clocksource tsc unstable (delta = -63640697 ns)
[   53.646948] [drm] Initialized drm 1.1.0 20060810
[   53.652743] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
[   53.652750] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [APC3] -> GSI 18 (level, low) -> IRQ 18
[   53.652754] PCI: Setting latency timer of device 0000:01:00.0 to 64
[   53.652810] [drm] Initialized radeon 1.28.0 20060524 on minor 0
[   54.052226] [drm] Setting GART location based on new memory map
[   54.052355] [drm] Loading R300 Microcode
[   54.052368] [drm] writeback test succeeded in 1 usecs
[   73.941301] usb 1-4: USB disconnect, address 4
```

What's wrong?

---

### Post by Ceox on 2008-04-27
Now I'm in ubuntu and the wireless is working! This happened once before but then when I re-booted connection was gone again. Why did that happen?

---

