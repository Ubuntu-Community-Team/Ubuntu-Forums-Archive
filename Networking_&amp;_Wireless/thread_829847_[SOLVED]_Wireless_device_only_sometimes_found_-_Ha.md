---
title: "[SOLVED] Wireless device only sometimes found - Hardy"
date: 2008-06-15
forum: Networking &amp; Wireless
---

### Post by ddell on 2008-06-15
Greetings.

So, all my problems started last Thursday (previous to this using Gutsy which worked fine with ndiswrapper), after downloading an update (admittedly up until now I rarely ever looked at what goes through and normally just click install - just have enabled the standard repositories available in 'software sources') and restarting, my wireless disappeared.

I have a dual boot system on my laptop (HP tx1215nr {which is of the tx1000 series}), with windows xp on the other end.  My wireless card is now no longer found there either (not listed in device manager or anything - even if I try to reinstall drivers).  The wireless light just stays orange regardless.

So I ran a bunch of the fixes found online, to no avail after three nerve-wracking days.  So I did a format and fresh install - then ran the fixes from this forum:  

HOWTO: Dell Inspiron Wireless (Broadcom 1390 WLAN)
(install ndiswrapper - blacklist bcm43xx)
(sorry i don't have the original urls - am operating from saved html files!)

and 

HOWTO: Get Ndiswrapper working in Hardy Beta 
(sudo gedit /etc/init.d/wirelessfix.sh

and paste this:

Quote:
#!/bin/bash

modprobe -r b44
modprobe -r b43
modprobe -r b43legacy
modprobe -r ssb
modprobe -r ndiswrapper
modprobe ndiswrapper
modprobe b44 )

And that worked fine - wireless was back and all worked normal...  Until I shut down and restarted - and now it's dead again.  I did this twice actually, last night was the first time, and I thought all was well so I downloaded most of the updates again (this time excluding 'proposed updates').  And then today it broke again.  So I thought it must be one of the updates.  So am now working on a totally clean install, got it working, and now it's dead again (though, perhaps will work the next time I reboot?)

Any idea what this might be?  I've tried swapping out the wireless card for another confirmed working one, and even from windows side it does not register/locate it.  That it works sometimes is really odd - might it just be a hardware problem such as a loose connection?

I'm using hardy on the laptop now - just plugged into ethernet - so that' working.


Here are the related outputs that I know of:


dmesg states:

[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1 15:8 APIC version 16
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
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
[    0.000000] Kernel command line: root=UUID=3a9fc08e-370f-4dbf-a74f-679757acc83f ro quiet splash
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1795.219 MHz processor.
[   10.705291] spurious 8259A interrupt: IRQ7.
[   10.708456] Console: colour VGA+ 80x25
[   10.708460] console [tty0] enabled
[   10.708804] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   10.709205] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   10.801089] Memory: 2000752k/2030592k available (2157k kernel code, 28540k reserved, 998k data, 364k init, 1113088k highmem)
[   10.801097] virtual kernel memory layout:
[   10.801098]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   10.801099]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   10.801101]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   10.801102]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   10.801103]       .init : 0xc041b000 - 0xc0476000   ( 364 kB)
[   10.801104]       .data : 0xc031b5a4 - 0xc0414dc4   ( 998 kB)
[   10.801106]       .text : 0xc0100000 - 0xc031b5a4   (2157 kB)
[   10.801109] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   10.801147] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   10.801299] hpet clockevent registered
[   10.881242] Calibrating delay using timer specific routine.. 3593.61 BogoMIPS (lpj=7187230)
[   10.881265] Security Framework initialized
[   10.881271] SELinux:  Disabled at boot.
[   10.881286] AppArmor: AppArmor initialized
[   10.881290] Failure registering capabilities with primary security module.
[   10.881299] Mount-cache hash table entries: 512
[   10.881420] CPU: After generic identify, caps: 178bfbff ebd3fbff 00000000 00000000 00002001 00000000 0000011f 00000000
[   10.881429] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   10.881432] CPU: L2 Cache: 512K (64 bytes/line)
[   10.881434] CPU 0(2) -> Core 0
[   10.881436] CPU: After all inits, caps: 178bfbff ebd3fbff 00000000 00000410 00002001 00000000 0000011f 00000000
[   10.881446] Compat vDSO mapped to ffffe000.
[   10.881457] Checking 'hlt' instruction... OK.
[   10.897510] SMP alternatives: switching to UP code
[   10.898747] Early unpacking initramfs... done
[   11.255223] ACPI: Core revision 20070126
[   11.255302] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   11.463724] CPU0: AMD Turion(tm) 64 X2 Mobile Technology TL-56 stepping 01
[   11.463741] SMP alternatives: switching to SMP code
[   11.464189] Booting processor 1/1 eip 3000
[   11.474581] Initializing CPU#1
[   11.553124] Calibrating delay using timer specific routine.. 3590.35 BogoMIPS (lpj=7180707)
[   11.553130] CPU: After generic identify, caps: 178bfbff ebd3fbff 00000000 00000000 00002001 00000000 0000011f 00000000
[   11.553137] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   11.553140] CPU: L2 Cache: 512K (64 bytes/line)
[   11.553142] CPU 1(2) -> Core 1
[   11.553143] AMD C1E detected late. 	Force timer broadcast.
[   11.553145] CPU: After all inits, caps: 178bfbff ebd3fbff 00000000 00000410 00002001 00000000 0000011f 00000000
[   11.552940] CPU1: AMD Turion(tm) 64 X2 Mobile Technology TL-56 stepping 01
[   11.552955] Total of 2 processors activated (7183.96 BogoMIPS).
[   11.553259] ENABLING IO-APIC IRQs
[   11.553493] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   11.593311] Brought up 2 CPUs
[   11.593368] CPU0 attaching sched-domain:
[   11.593370]  domain 0: span 03
[   11.593372]   groups: 01 02
[   11.593375] CPU1 attaching sched-domain:
[   11.593377]  domain 0: span 03
[   11.593379]   groups: 02 01
[   11.593578] net_namespace: 64 bytes
[   11.593586] Booting paravirtualized kernel on bare hardware
[   11.594071] Time:  1:27:15  Date: 06/16/08
[   11.594097] NET: Registered protocol family 16
[   11.594277] EISA bus registered
[   11.594281] ACPI: bus type pci registered
[   11.609780] PCI: BIOS BUG #81[49435000] found
[   11.609825] PCI: Using configuration type 1
[   11.609827] Setting up standard PCI resources
[   11.611652] ACPI: EC: Look up EC in DSDT
[   11.638986] ACPI: BIOS _OSI(Linux) query ignored via DMI
[   11.639237] ACPI: Interpreter enabled
[   11.639240] ACPI: (supports S0 S3 S4 S5)
[   11.639251] ACPI: Using IOAPIC for interrupt routing
[   11.639918] ACPI: EC: non-query interrupt received, switching to interrupt mode
[   11.708448] ACPI: EC: GPE = 0x10, I/O: command/status = 0x66, data = 0x62
[   11.708451] ACPI: EC: driver started in interrupt mode
[   11.708511] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   11.709522] PCI: Transparent bridge - 0000:00:10.0
[   11.709538] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   11.709634] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P0._PRT]
[   11.709661] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR1._PRT]
[   11.709692] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR2._PRT]
[   11.746894] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 10 11 14 15) *0, disabled.
[   11.747102] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 *10 11 14 15)
[   11.747305] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 10 11 14 15) *0, disabled.
[   11.747509] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 10 11 14 15) *0, disabled.
[   11.747712] ACPI: PCI Interrupt Link [LK1E] (IRQs 19) *0, disabled.
[   11.747914] ACPI: PCI Interrupt Link [LK2E] (IRQs 16 17 20 22 23) *0, disabled.
[   11.748116] ACPI: PCI Interrupt Link [LK3E] (IRQs 18) *10
[   11.748317] ACPI: PCI Interrupt Link [LK4E] (IRQs 16 17 20 22 23) *0, disabled.
[   11.748520] ACPI: PCI Interrupt Link [LSMB] (IRQs 16 17 20 22 23) *10
[   11.748727] ACPI: PCI Interrupt Link [LPMU] (IRQs 16 17 20 22 23) *11
[   11.748930] ACPI: PCI Interrupt Link [LUS0] (IRQs 16 17 20 22 23) *11
[   11.749133] ACPI: PCI Interrupt Link [LUS2] (IRQs 16 17 20 22 23) *7
[   11.749335] ACPI: PCI Interrupt Link [LMAC] (IRQs 16 17 20 22 23) *11
[   11.749551] ACPI: PCI Interrupt Link [LAZA] (IRQs 16 17 20 22 23) *0, disabled.
[   11.749754] ACPI: PCI Interrupt Link [LACI] (IRQs 16 17 20 22 23) *0, disabled.
[   11.749957] ACPI: PCI Interrupt Link [LMCI] (IRQs 16 17 20 22 23) *0, disabled.
[   11.750160] ACPI: PCI Interrupt Link [LPID] (IRQs 16 17 20 22 23) *0, disabled.
[   11.750370] ACPI: PCI Interrupt Link [LTID] (IRQs 21) *5
[   11.750577] ACPI: PCI Interrupt Link [LSI1] (IRQs 21) *0
[   11.750719] Linux Plug and Play Support v0.97 (c) Adam Belay
[   11.750751] pnp: PnP ACPI init
[   11.750757] ACPI: bus type pnp registered
[   11.784277] pnp: PnP ACPI: found 13 devices
[   11.784279] ACPI: ACPI bus type pnp unregistered
[   11.784283] PnPBIOS: Disabled by ACPI PNP
[   11.784521] PCI: Using ACPI for IRQ routing
[   11.784524] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   11.793470] NET: Registered protocol family 8
[   11.793472] NET: Registered protocol family 20
[   11.793511] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 31
[   11.793515] hpet0: 3 32-bit timers, 25000000 Hz
[   11.794562] AppArmor: AppArmor Filesystem Enabled
[   11.797080] Time: hpet clocksource has been installed.
[   11.797084] Clockevents: could not switch to one-shot mode: lapic is not functional.
[   11.797087] Could not switch to high resolution mode on CPU 0
[   11.801460] Clockevents: could not switch to one-shot mode: lapic is not functional.
[   11.801464] Could not switch to high resolution mode on CPU 1
[   11.809489] system 00:00: iomem range 0xe0000000-0xefffffff could not be reserved
[   11.809495] system 00:01: iomem range 0xffc00000-0xffffffff could not be reserved
[   11.809499] system 00:01: iomem range 0xfec00000-0xfec00fff could not be reserved
[   11.809502] system 00:01: iomem range 0xfee00000-0xfeefffff could not be reserved
[   11.809505] system 00:01: iomem range 0xfed00000-0xfed00fff has been reserved
[   11.809511] system 00:03: iomem range 0xe0000000-0xefffffff could not be reserved
[   11.809517] system 00:04: ioport range 0x1000-0x107f has been reserved
[   11.809520] system 00:04: ioport range 0x1080-0x10ff has been reserved
[   11.809523] system 00:04: ioport range 0x1400-0x147f has been reserved
[   11.809526] system 00:04: ioport range 0x1480-0x14ff has been reserved
[   11.809528] system 00:04: ioport range 0x1800-0x187f has been reserved
[   11.809531] system 00:04: ioport range 0x1880-0x18ff has been reserved
[   11.809534] system 00:04: ioport range 0x2000-0x203f has been reserved
[   11.809539] system 00:05: ioport range 0x360-0x361 has been reserved
[   11.809542] system 00:05: ioport range 0x380-0x383 has been reserved
[   11.809545] system 00:05: ioport range 0x4d0-0x4d1 has been reserved
[   11.839970] PCI: Bridge: 0000:00:02.0
[   11.839972]   IO window: 4000-4fff
[   11.839975]   MEM window: c4000000-c7ffffff
[   11.839978]   PREFETCH window: c9000000-c91fffff
[   11.839981] PCI: Bridge: 0000:00:03.0
[   11.839982]   IO window: 5000-5fff
[   11.839985]   MEM window: c8000000-c8ffffff
[   11.839987]   PREFETCH window: c9200000-c93fffff
[   11.839990] PCI: Bridge: 0000:00:10.0
[   11.839991]   IO window: disabled.
[   11.839994]   MEM window: disabled.
[   11.839997]   PREFETCH window: disabled.
[   11.840009] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   11.840016] PCI: Setting latency timer of device 0000:00:03.0 to 64
[   11.840024] PCI: Setting latency timer of device 0000:00:10.0 to 64
[   11.840036] NET: Registered protocol family 2
[   11.877484] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   11.877781] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   11.878661] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   11.879122] TCP: Hash tables configured (established 131072 bind 65536)
[   11.879125] TCP reno registered
[   11.893540] checking if image is initramfs... it is
[   12.584325] Freeing initrd memory: 7701k freed
[   12.584432] Simple Boot Flag at 0x36 set to 0x1
[   12.585098] audit: initializing netlink socket (disabled)
[   12.585112] audit(1213579635.588:1): initialized
[   12.585294] highmem bounce pool size: 64 pages
[   12.587192] VFS: Disk quotas dquot_6.5.1
[   12.587268] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   12.587397] io scheduler noop registered
[   12.587399] io scheduler anticipatory registered
[   12.587401] io scheduler deadline registered
[   12.587415] io scheduler cfq registered (default)
[   12.587433] Boot video device is 0000:00:05.0
[   12.587570] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   12.587594] assign_interrupt_mode Found MSI capability
[   12.587615] Allocate Port Service[0000:00:02.0:pcie00]
[   12.587680] PCI: Setting latency timer of device 0000:00:03.0 to 64
[   12.587701] assign_interrupt_mode Found MSI capability
[   12.587717] Allocate Port Service[0000:00:03.0:pcie00]
[   12.587943] isapnp: Scanning for PnP cards...
[   12.940453] isapnp: No Plug & Play device found
[   12.972833] Real Time Clock Driver v1.12ac
[   12.973029] hpet_resources: 0xfed00000 is busy
[   12.973081] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   12.974310] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   12.974381] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   12.974478] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[   12.989972] serio: i8042 KBD port at 0x60,0x64 irq 1
[   12.989978] serio: i8042 AUX port at 0x60,0x64 irq 12
[   13.004632] mice: PS/2 mouse device common for all mice
[   13.004762] EISA: Probing bus 0 at eisa.0
[   13.004768] Cannot allocate resource for EISA slot 1
[   13.004770] Cannot allocate resource for EISA slot 2
[   13.004772] Cannot allocate resource for EISA slot 3
[   13.004774] Cannot allocate resource for EISA slot 4
[   13.004776] Cannot allocate resource for EISA slot 5
[   13.004787] EISA: Detected 0 cards.
[   13.004790] cpuidle: using governor ladder
[   13.004792] cpuidle: using governor menu
[   13.004886] NET: Registered protocol family 1
[   13.004913] Using IPI No-Shortcut mode
[   13.004949] registered taskstats version 1
[   13.005069]   Magic number: 12:230:458
[   13.005244] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   13.005246] EDD information not available.
[   13.005498] Freeing unused kernel memory: 364k freed
[   13.015217] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   14.291179] fuse init (API version 7.9)
[   14.318716] ACPI: Thermal Zone [THRM] (58 C)
[   14.887671] usbcore: registered new interface driver usbfs
[   14.887694] usbcore: registered new interface driver hub
[   14.888325] usbcore: registered new device driver usb
[   14.890202] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   14.890600] ACPI: PCI Interrupt Link [LUS0] enabled at IRQ 23
[   14.890611] ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [LUS0] -> GSI 23 (level, high) -> IRQ 16
[   14.890624] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[   14.890627] ohci_hcd 0000:00:0b.0: OHCI Host Controller
[   14.890985] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 1
[   14.891006] ohci_hcd 0000:00:0b.0: irq 16, io mem 0xc0004000
[   14.929918] SCSI subsystem initialized
[   14.948885] usb usb1: configuration #1 chosen from 1 choice
[   14.948910] hub 1-0:1.0: USB hub found
[   14.948921] hub 1-0:1.0: 8 ports detected
[   14.989574] libata version 3.00 loaded.
[   15.051269] sata_nv 0000:00:0e.0: version 3.5
[   15.051634] ACPI: PCI Interrupt Link [LTID] enabled at IRQ 21
[   15.051645] ACPI: PCI Interrupt 0000:00:0e.0[A] -> Link [LTID] -> GSI 21 (level, high) -> IRQ 17
[   15.051690] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[   15.055128] scsi0 : sata_nv
[   15.055203] scsi1 : sata_nv
[   15.055365] ata1: SATA max UDMA/133 cmd 0x30b0 ctl 0x30a4 bmdma 0x3090 irq 17
[   15.055369] ata2: SATA max UDMA/133 cmd 0x30a8 ctl 0x30a0 bmdma 0x3098 irq 17
[   15.354445] usb 1-2: new full speed USB device using ohci_hcd and address 2
[   15.522345] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   15.530568] ata1.00: ATA-7: Hitachi HTS541616J9SA00, SB4OC7BP, max UDMA/100
[   15.530572] ata1.00: 312581808 sectors, multi 16: LBA48 
[   15.546518] ata1.00: configured for UDMA/100
[   15.557429] usb 1-2: configuration #1 chosen from 1 choice
[   15.560351] hub 1-2:1.0: USB hub found
[   15.563328] hub 1-2:1.0: 4 ports detected
[   15.858068] ata2: SATA link down (SStatus 0 SControl 300)
[   15.868732] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS54161 SB4O PQ: 0 ANSI: 5
[   15.869470] ACPI: PCI Interrupt Link [LUS2] enabled at IRQ 22
[   15.869483] ACPI: PCI Interrupt 0000:00:0b.1[B] -> Link [LUS2] -> GSI 22 (level, high) -> IRQ 18
[   15.869497] PCI: Setting latency timer of device 0000:00:0b.1 to 64
[   15.869500] ehci_hcd 0000:00:0b.1: EHCI Host Controller
[   15.869532] ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 2
[   15.869565] ehci_hcd 0000:00:0b.1: debug port 1
[   15.869569] PCI: cache line size of 64 is not supported by device 0000:00:0b.1
[   15.869581] ehci_hcd 0000:00:0b.1: irq 18, io mem 0xc0005000
[   15.919455] usb 1-2.1: new full speed USB device using ohci_hcd and address 3
[   15.930012] ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   15.930124] usb usb2: configuration #1 chosen from 1 choice
[   15.930152] hub 2-0:1.0: USB hub found
[   15.930159] hub 2-0:1.0: 8 ports detected
[   15.931441] hub 1-2:1.0: cannot reset port 1 (err = -62)
[   15.934438] hub 1-2:1.0: cannot reset port 1 (err = -62)
[   15.937435] hub 1-2:1.0: cannot reset port 1 (err = -62)
[   15.940433] hub 1-2:1.0: cannot reset port 1 (err = -62)
[   15.943431] hub 1-2:1.0: cannot reset port 1 (err = -62)
[   15.943433] hub 1-2:1.0: Cannot enable port 1.  Maybe the USB cable is bad?
[   15.946429] hub 1-2:1.0: cannot disable port 1 (err = -62)
[   15.949426] hub 1-2:1.0: cannot reset port 1 (err = -62)
[   15.952424] hub 1-2:1.0: cannot reset port 1 (err = -62)
[   15.955422] hub 1-2:1.0: cannot reset port 1 (err = -62)
[   15.958420] hub 1-2:1.0: cannot reset port 1 (err = -62)
[   15.961418] hub 1-2:1.0: cannot reset port 1 (err = -62)
[   15.961420] hub 1-2:1.0: Cannot enable port 1.  Maybe the USB cable is bad?
[   15.964416] hub 1-2:1.0: cannot disable port 1 (err = -62)
[   15.967413] hub 1-2:1.0: cannot reset port 1 (err = -62)
[   15.970411] hub 1-2:1.0: cannot reset port 1 (err = -62)
[   15.973408] hub 1-2:1.0: cannot reset port 1 (err = -62)
[   15.976406] hub 1-2:1.0: cannot reset port 1 (err = -62)
[   15.979404] hub 1-2:1.0: cannot reset port 1 (err = -62)
[   15.979406] hub 1-2:1.0: Cannot enable port 1.  Maybe the USB cable is bad?
[   15.982402] hub 1-2:1.0: cannot disable port 1 (err = -62)
[   15.985400] hub 1-2:1.0: cannot reset port 1 (err = -62)
[   15.988398] hub 1-2:1.0: cannot reset port 1 (err = -62)
[   15.991395] hub 1-2:1.0: cannot reset port 1 (err = -62)
[   15.994392] hub 1-2:1.0: cannot reset port 1 (err = -62)
[   15.997391] hub 1-2:1.0: cannot reset port 1 (err = -62)
[   15.997394] hub 1-2:1.0: Cannot enable port 1.  Maybe the USB cable is bad?
[   16.000389] hub 1-2:1.0: cannot disable port 1 (err = -62)
[   16.003387] hub 1-2:1.0: cannot disable port 1 (err = -62)
[   16.006385] hub 1-2:1.0: hub_port_status failed (err = -62)
[   16.009382] hub 1-2:1.0: hub_port_status failed (err = -62)
[   16.012383] hub 1-2:1.0: hub_port_status failed (err = -62)
[   16.015378] hub 1-2:1.0: hub_port_status failed (err = -62)
[   16.015390] usb 1-2: USB disconnect, address 2
[   16.035062] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
[   16.035423] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 20
[   16.035433] ACPI: PCI Interrupt 0000:00:14.0[A] -> Link [LMAC] -> GSI 20 (level, high) -> IRQ 19
[   16.035439] PCI: Setting latency timer of device 0000:00:14.0 to 64
[   16.422025] usb 2-2: new high speed USB device using ehci_hcd and address 2
[   16.558630] forcedeth 0000:00:14.0: ifname eth0, PHY OUI 0x732 @ 1, addr 00:1b:24:50:43:36
[   16.558634] forcedeth 0000:00:14.0: highdma pwrctl timirq gbit lnktim desc-v3
[   16.558738] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[   16.561697] pata_amd 0000:00:0d.0: version 0.3.10
[   16.561731] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[   16.562939] usb 2-2: configuration #1 chosen from 1 choice
[   16.562966] scsi2 : pata_amd
[   16.563031] hub 2-2:1.0: USB hub found
[   16.563105] hub 2-2:1.0: 4 ports detected
[   16.563620] scsi3 : pata_amd
[   16.564280] ata3: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x3080 irq 14
[   16.564284] ata4: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x3088 irq 15
[   16.585659] Driver 'sd' needs updating - please use bus_type methods
[   16.587414] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[   16.587428] sd 0:0:0:0: [sda] Write Protect is off
[   16.587430] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   16.587447] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   16.587499] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[   16.587509] sd 0:0:0:0: [sda] Write Protect is off
[   16.587511] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   16.587526] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   16.587529]  sda: sda1 sda2 sda3 < sda5 >
[   16.635272] sd 0:0:0:0: [sda] Attached SCSI disk
[   16.641313] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   16.881765] usb 2-2.1: new high speed USB device using ehci_hcd and address 3
[   16.881624] ata3.00: ATAPI: HL-DT-ST DVDRAM GSA-T20L, NC08, max MWDMA2
[   16.990056] usb 2-2.1: configuration #1 chosen from 1 choice
[   17.021147] Attempting manual resume
[   17.021151] swsusp: Resume From Partition 8:5
[   17.021153] PM: Checking swsusp image.
[   17.021369] PM: Resume from disk failed.
[   17.053461] ata3.00: configured for MWDMA2
[   17.053887] ata4: port disabled. ignoring.
[   17.057499] scsi 2:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-T20L  NC08 PQ: 0 ANSI: 5
[   17.057584] scsi 2:0:0:0: Attached scsi generic sg1 type 5
[   17.066583] Driver 'sr' needs updating - please use bus_type methods
[   17.071225] kjournald starting.  Commit interval 5 seconds
[   17.071619] EXT3-fs: mounted filesystem with ordered data mode.
[   17.083563] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[   17.083569] Uniform CD-ROM driver Revision: 3.20
[   17.083632] sr 2:0:0:0: Attached scsi CD-ROM sr0
[   24.228444] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   24.268027] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   24.668051] Linux agpgart interface v0.102
[   24.944243] input: Power Button (FF) as /devices/virtual/input/input2
[   24.963692] ACPI: Power Button (FF) [PWRF]
[   24.963770] input: Power Button (CM) as /devices/virtual/input/input3
[   24.979674] ACPI: Power Button (CM) [PWRB]
[   24.979752] input: Sleep Button (CM) as /devices/virtual/input/input4
[   25.003677] ACPI: Sleep Button (CM) [SLPB]
[   25.003755] input: Lid Switch as /devices/virtual/input/input5
[   25.003835] ACPI: Lid Switch [LID]
[   25.021827] input: PC Speaker as /devices/platform/pcspkr/input/input6
[   25.053255] ACPI: AC Adapter [ACAD] (on-line)
[   25.327611] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x3040
[   25.327630] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x3000
[   25.887353] ACPI: Battery Slot [BAT0] (battery present)
[   25.887461] ACPI: WMI-Acer: Mapper loaded
[   25.889649] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:00/input/input7
[   25.915051] ACPI: Video Device [UVGA] (multi-head: yes  rom: no  post: no)
[   25.915351] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:2d/LNXVIDEO:01/input/input8
[   25.946962] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   25.997077] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 17
[   25.997090] ACPI: PCI Interrupt 0000:00:10.1[B] -> Link [LAZA] -> GSI 17 (level, high) -> IRQ 20
[   25.997117] PCI: Setting latency timer of device 0000:00:10.1 to 64
[   26.410529] Linux video capture interface: v2.00
[   26.514701] uvcvideo: Found UVC 1.00 device <unnamed> (05ca:1810)
[   26.514932] uvcvideo: Failed to query (135) UVC control 1 (unit 0) : -32 (exp. 26).
[   26.515306] uvcvideo: Failed to query (129) UVC control 1 (unit 0) : -32 (exp. 26).
[   26.515309] uvcvideo: Failed to initialize the device (-5).
[   26.515326] usbcore: registered new interface driver uvcvideo
[   26.515330] USB Video Class driver (v0.1.0)
[   27.045462] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x180b1, caps: 0xa04713/0x200000
[   27.105274] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input9
[   28.243391] lp: driver loaded but no devices found
[   28.301310] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   28.399181] usbcore: registered new interface driver ndiswrapper
[   28.463210] Adding 5887780k swap on /dev/sda5.  Priority:-1 extents:1 across:5887780k
[   29.021927] EXT3 FS on sda1, internal journal
[   30.409997] ip_tables: (C) 2000-2006 Netfilter Core Team
[   31.001893] No dock devices found.
[   31.099725] ACPI: \_SB_.PCI0.IDE0.PRI0.MAST: found ejectable bay
[   31.099732] ACPI: \_SB_.PCI0.IDE0.PRI0.MAST: Adding notify handler
[   31.099765] ACPI: Error installing bay notify handler
[   31.099768] ACPI: Bay [\_SB_.PCI0.IDE0.PRI0.MAST] Added
[   31.483416] powernow-k8: Found 1 AMD Turion(tm) 64 X2 Mobile Technology TL-56 processors (2 cpu cores) (version 2.20.00)
[   31.483087] powernow-k8:    0 : fid 0xa (1800 MHz), vid 0x13
[   31.483091] powernow-k8:    1 : fid 0x8 (1600 MHz), vid 0x14
[   31.483094] powernow-k8:    2 : fid 0x0 (800 MHz), vid 0x1e
[   32.243571] apm: BIOS not found.
[   32.407820] ppdev: user-space parallel port driver
[   32.509877] audit(1213554456.470:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5126 profile="/usr/sbin/cupsd" namespace="default"
[   32.781846] usbcore: deregistering interface driver ndiswrapper
[   32.804860] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   32.834607] usbcore: registered new interface driver ndiswrapper
[   34.130449] Bluetooth: Core ver 2.11
[   34.131084] NET: Registered protocol family 31
[   34.131087] Bluetooth: HCI device and connection manager initialized
[   34.131091] Bluetooth: HCI socket layer initialized
[   34.140074] Clocksource tsc unstable (delta = -217369806 ns)
[   34.152293] Bluetooth: L2CAP ver 2.9
[   34.152298] Bluetooth: L2CAP socket layer initialized
[   34.157976] Bluetooth: RFCOMM socket layer initialized
[   34.157990] Bluetooth: RFCOMM TTY layer initialized
[   34.157992] Bluetooth: RFCOMM ver 1.8
[   35.524643] NET: Registered protocol family 17
[   37.451054] NET: Registered protocol family 10
[   37.451280] lo: Disabled Privacy Extensions
[   42.616725] eth0: no IPv6 routers present
[   50.099927] CPU0 attaching NULL sched-domain.
[   50.099935] CPU1 attaching NULL sched-domain.
[   50.115556] CPU0 attaching sched-domain:
[   50.115560]  domain 0: span 03
[   50.115562]   groups: 01 02
[   50.115565] CPU1 attaching sched-domain:
[   50.115567]  domain 0: span 03
[   50.115569]   groups: 02 01



lshw -C network runs, but gives no output - it just returns me back to an empty command prompt (which when wireless is functioning it gives a readable response)

ndiswrapper -l shows
bcmwl5 : driver installed

lsmod | grep ndiswrapper shows
ndiswrapper           192920  0 
usbcore               146028  5 ndiswrapper,uvcvideo,ehci_hcd,ohci_hcd

ls -l /etc/rc.local shows
-rwxr-xr-x 1 root root 306 2008-04-23 00:49 /etc/rc.local

ifconfig:

eth0      Link encap:Ethernet  HWaddr 00:1b:24:50:43:36  
          inet addr:192.168.2.4  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:24ff:fe50:4336/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8184 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7303 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8964914 (8.5 MB)  TX bytes:1078085 (1.0 MB)
          Interrupt:19 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:280 errors:0 dropped:0 overruns:0 frame:0
          TX packets:280 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:14000 (13.6 KB)  TX bytes:14000 (13.6 KB)



Obviously since I'm asking I don't really yet understand all that dmesg and the like have to potentially offer!

Any help would be greatly appreciated!  I'm working in Indonesia so can't handle having to reinstall and download updates all over again on the slow connection speeds available here!  

Thanks!

-dave

---

### Post by llama320 on 2008-06-15
I've got a HP dv6000 (laptop) and a couple weeks back my wireless card crapped out on me, too. I went to HP's website and they said that some models had known hardware problems concerning wireless. I called them up and sent my comp in and they replaced the system board (I think, though I'm not sure what they did) and when I got it back the device was recognized again on both my windows box and ubuntu

Good Luck

---

### Post by ddell on 2008-06-15
Well I purchased the laptop in the states just this past November...  and am in Indonesia now until December, and don't have the receipt with me, so...  

Curses.


Maybe it's still a software/config issue?

---

### Post by jw5801 on 2008-06-15
This is a hardware issue. Contact the manufacturer! The device is getting power (based on the fact that the light is on) but cannot be located by an operating system, so one would assume that there is a faulty connection somewhere. As the above poster recommends, I would contact HP and get them to have a look at it, assuming it is still under warranty.

Also, please use code tags for terminal outputs, especially long ones such as dmesg, it prints in monospace, which can be handy, and gives rather long outputs their own scrollbar to preserve the length of each page. The title of this post shows how to use them. :)

---

### Post by jw5801 on 2008-06-15
> **ddell said:**
> Well I purchased the laptop in the states just this past November...  and am in Indonesia now until December, and don't have the receipt with me, so...  

Curses.


Maybe it's still a software/config issue?

It's not a software issue. If two independent operating systems both have the same issue with the card, I'd have to assume either the card, or it's connection is faulty. If you're feeling adventurous you could remove it and clean any dust from the connection and check if there's anything obvious that might be interfering, I can't give any particularly detailed advice in that department though. You could try contacting the store you purchased the laptop from and see if they have a record of your purchase (presumably, if it's under warranty they would have to) and see if there's any way they could help you out. Even if you had to have it shipped back to the states, it would still be better than having to pay to have it fixed.

---

### Post by ddell on 2008-06-16
Ok now I'm really confused, after some more searching, came across this post on the HP forums:

[http://www11.itrc.hp.com/service/james/dispDoc.do?docURL=http%3A%2F%2Fsearch.hp.com%2Fredirect.html%3Furl%3Dhttp%253A%2F%2Fforums11.itrc.hp.com%2Fservice%2Fforums%2Fquestionanswer.do%253FthreadId%253D1104931%26qt%3D%252BDV6000%2B%252BWireless%2B%2B%252Bdevice%2B%252Bvanishes%2B%26hit%3D1&aid=SEARCH_FORUMS&pil=1&serStr=DV6000+Wireless+device+vanishes&pir=1](http://www11.itrc.hp.com/service/james/dispDoc.do?docURL=http%3A%2F%2Fsearch.hp.com%2Fredirect.html%3Furl%3Dhttp%253A%2F%2Fforums11.itrc.hp.com%2Fservice%2Fforums%2Fquestionanswer.do%253FthreadId%253D1104931%26qt%3D%252BDV6000%2B%252BWireless%2B%2B%252Bdevice%2B%252Bvanishes%2B%26hit%3D1&aid=SEARCH_FORUMS&pil=1&serStr=DV6000+Wireless+device+vanishes&pir=1)

And within that, this suggested fix:

```

shadowchemist  	
May 31, 2007 11:47:50 GMT  8 pts 	
Hello,

I have a dv6000 laptop and my wireless driver, also, vanished without a trace. I went on Google and Yahoo and looked around to find any way on fixing this problem. I have read what other people have done and never worked. However I have found something interesting. When reinstalling the driver for the wireless and restarting the computer the wireless appears until the next restart/stand-by/hibernation. I have noticed that some of the configuration files get overwritten by either Windows or maybe an update. I do not know what is causing the files to be overwritten but because of that the computer can not recognize the wireless driver. So I have tried my own method of fixing this without sending the computer to be serviced which, by the way, some people have reported that sending it to be fixed with a new system board does not work. So here is my method and hopefully it will work for you. I have restarted my computer several times and each time the wireless driver is detected and running.

1) Restart the computer and enter into Safe Mode.
2) Uninstall the wireless driver from Control Panel.
3) Goto Program Files in your C drive and look for the Broadcom folder and delete it. Make sure that you remove it from the Recycle Bin too. Also you should have the latest version of the driver. (Boardcom 4.100.15.5) The HP website has this available (sp34152.exe). [Get the driver downloaded on your computer before doing any of these steps] In the SWSetup folder there should be a folder named WLAN delete all the files in there and replace it (copy and paste) the Boardcom files that you downloaded.
3) Restart the computer and enter into Safe Mode again.
4) Reinstall the driver. Check in Device Manager to see if the driver is there. If not then restart the computer and enter in Safe Mode again. The computer should see the wireless driver now.
5) In the C:\ProgramFiles\Boardcom there would be several system and configuration files. Right click on each of them and make the files Read-Only and click OK. The computer is going to give you an error. Ignore it and click on Cancel. Go back to the properties and you will see that the files are now Read-Only. Also goto C:\Windows\system32\drivers and look for a file named bcmwl5.sys and right click on the file and goto properties and make that file Read-Only.
6) Restart the computer and enter the computer in normal mode. The wireless driver should be installed and in the device manager and working 100%.

Hope this helps everyone. Good luck. 


```





which, after following on the XP side of my hard drive, now my wireless works on both the XP and Ubuntu end.  Have tried restarting multiple times, to moreorless try and break it, and it's still on.  That was last night, and it came on again this morning (am using wireless now - whereas previous posts were made using ethernet cable).

Of course, by me being pleased that it's working again, it's bound to break again soon.  :)



Any idea how this could have worked?  Could it be something that windows puts in bios/startup that cuts power to the wireless card?

Others in that same post claim it's a battery problem:

```

StuartR  	
Jun 6, 2007 10:48:29 GMT    Unassigned 	
Here's a tip to get it working. It has to do with the battery and some setting maintained on the motherboard about the status of the battery.

START SEQUENCE:

Remove the battery.

Remove the power tip for maybe 15 secs.

Re-apply power (but no battery).

Fire up and the wireless will work.

Power-down when you have finished and put the battery back. It may work now for a few re-starts but when it stops working go back to START OF SEQUENCE.

HP should have enough from this to know what the problem is. Please keep referring them back here until they listen.

A standard HP fix for many probloems over the years has been "take the battery out".
StuartR 	
Jun 6, 2007 11:13:48 GMT    Unassigned 	
IT'S THE BATTERY!!!!!!

I can prove it.

Follow my sequence of power-off, remove power tip, remove battery, fire-up. Wireless works.

Power-down, put back battery, power-up. Wireless works!

Power-down and next time you power-up the Wireless WON'T work!

Why? Because the motherboard has kept some memory status about the battery condition and for some reason won't apply power to the Wireless card.

This is why it takes a few months for it to stop working. Its something to do with the memory cells in the battery and some status saved on teh motherboard. 

```


Though I haven't had to do that - just doing the above once set everything right again...  for now!


It's still a bloody hardware problem, I know that.  But if this workaround works I'll stick with it, as HP won't honour the warranty outside the country.  And I really can't afford not having my laptop for all the time it takes to ship it to the states and back (which is incredibly stupid that they won't fix it here, considering there is an official HP service centre in the town I'm living in in Indonesia).

---

### Post by jw5801 on 2008-06-16
Hmm, that's very interesting. Windows should *never* touch the Bios, and presumably Grub is on the MBR so Windows doesn't have any control whatsoever over startup until you decide to boot into Windows. So that really doesn't make much sense. Perhaps the Windows safe mode clears some kind of motherboard cache when you boot into it provided it doesn't need to try and connect to the WLAN card. I have no idea! Ah well, at least it's working again.

---

### Post by ddell on 2008-06-17
ok...  turned off and on, and now it's missing again!

hooray!


so, it's a temporary solution - have turned it off and on a bunch of times before it broke.  so, fair enough.

now to bother HP to send me a mainboard so that I don't have to send my whole laptop across the world twice

---

### Post by jw5801 on 2008-06-17
> **ddell said:**
> ok...  turned off and on, and now it's missing again!

hooray!


so, it's a temporary solution - have turned it off and on a bunch of times before it broke.  so, fair enough.

now to bother HP to send me a mainboard so that I don't have to send my whole laptop across the world twice

Bugger, do the workarounds fix it up again?

---

### Post by ddell on 2008-06-17
greetings and thanks for following up!

yes, i did the workaround again, and wireless is back on.

though this time i went a step further and went into xp control panel and disabled 'power saving' and 'allow computer to turn this device off for power saving'.


also on my ubuntu side (which am using now - I only use XP to be able to use arcGIS and also endnote for ms word (the bibliography software alternatives in linux aren't that good yet I don't think and crossover only supports old versions of endnote) I made the wireless drivers 'read-only' as well, as I did on the xp side.

not sure if that'll make any difference.  but at least I have a way to turn on wireless when I need it (after a ten minute annoying rebooting session)

---

### Post by jw5801 on 2008-06-17
> **ddell said:**
> greetings and thanks for following up!

yes, i did the workaround again, and wireless is back on.

though this time i went a step further and went into xp control panel and disabled 'power saving' and 'allow computer to turn this device off for power saving'.


also on my ubuntu side (which am using now - I only use XP to be able to use arcGIS and also endnote for ms word (the bibliography software alternatives in linux aren't that good yet I don't think and crossover only supports old versions of endnote) I made the wireless drivers 'read-only' as well, as I did on the xp side.

not sure if that'll make any difference.  but at least I have a way to turn on wireless when I need it (after a ten minute annoying rebooting session)

Hmm... could be related to an issue I see occasionally. If I toggle off the power to my card and then reboot without toggling it back on, the card doesn't come back and isn't recognised until I reset the 'WiFi switch' option in my bios.

For bibliography management I'd be inclined to go with LaTeX and BibTeX on Windows and Linux, but LaTeX tends to be a bit hardcore for most people. It makes really pretty outputs though, and most of my documents are generally full of maths so LaTeX is much easier for that.

---

### Post by ddell on 2008-06-18
Right, I made the same mistake - turned it off with wireless switched off, and now it's gone again!

My BIOS doesn't have any sections for wireless, in fact there is very little I can change in it at all.  I'm also afraid to update the BIOS to the latest released version, as it's listed only for Vista (and I've read some posts talking about Vista getting into BIOS - microsoft is terrible).

Is there anything I could do from within Ubuntu to send a wakeup signal to the wireless card?  Or do I just have to go through the odd windows end fix?

---

### Post by jw5801 on 2008-06-18
I don't know that there's an easy way to do anything to it from Ubuntu, so you might be stuck with the odd Windows fix.

---

### Post by pigphish on 2008-06-23
what is this? 

```
[ 11.609780] PCI: BIOS BUG #81[49435000] found
```

I have a similar warning... is it something to be concerned about?

---

### Post by jw5801 on 2008-06-23
> **pigphish said:**
> what is this? 

```
[ 11.609780] PCI: BIOS BUG #81[49435000] found
```

I have a similar warning... is it something to be concerned about?

It means your BIOS does something non-conformist. Nothing to worry about.

---

