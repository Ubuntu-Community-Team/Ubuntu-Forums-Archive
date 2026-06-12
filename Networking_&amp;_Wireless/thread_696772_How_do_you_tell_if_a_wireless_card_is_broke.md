---
title: "How do you tell if a wireless card is broke?"
date: 2008-02-14
forum: Networking &amp; Wireless
---

### Post by Dwiman89 on 2008-02-14
Hey IM having trouble with my wireless connection. When I boot up and load NDISwrapper. I get my connection and everything works fine. BUT in about 5 min or so the connection  gets really slow  then stops loading pages all together. The network manager says that im still connected(It has signal bars,IP gaitway, Router address, DNS and everything listed) It will stay like that for a long time then I loose the connection.
I have tried booting into windows and I get similar Issues. Maybe the Wifi card is broke. Please help.

---

### Post by dca on 2008-02-14
That's possible but don't rule out something upstream at your router or modem or ISP...  The interesting thing is you're saying that Windows exhibits the same attributes which coincides w/ possible wireless hardware issue.  Is there a newer driver avail from manf website that can be used?

---

### Post by Dwiman89 on 2008-02-14
All other comps on my network are hardwired to the network. None in my family has reported that they having issues. If the wifi card has an updated driver available, would the card continue to work with old drivers. I would assume that updated drivers would help performance, not fix a new found problem. I have been using the card for about 6 months or so.
is there a way i can find out if its a hardware issue. Im going to ook for updated drivers and run "dmsg" in terminal wen I get home. If I can get the connection working long enough, ill post the output.

---

### Post by Dwiman89 on 2008-02-15
Well My system has started to randomly freeze up. the mouse wont move. I cant even get into  the shell or hit ctrl alt backspace. the only solution is to hit the power button. Here is the output from "dmesg"


```
[    0.000000] Linux version 2.6.22-14-generic (buildd@terranova) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Fri Feb 1 04:59:50 UTC 2008 (Ubuntu 2.6.22-14.51-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001fff0000 (usable)
[    0.000000]  BIOS-e820: 000000001fff0000 - 000000001fff3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000001fff3000 - 0000000020000000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 511MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 131056) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   131056
[    0.000000]   HighMem    131056 ->   131056
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   131056
[    0.000000] On node 0 totalpages: 131056
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 991 pages used for memmap
[    0.000000]   Normal zone: 125969 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI 2.2 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F6D80 checksum 0
[    0.000000] ACPI: RSDP 000F6D80, 0014 (r0 Nvidia)
[    0.000000] ACPI: RSDT 1FFF3000, 002C (r1 Nvidia AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: FACP 1FFF3040, 0074 (r1 Nvidia AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: DSDT 1FFF30C0, 4489 (r1 NVIDIA AWRDACPI     1000 MSFT  100000E)
[    0.000000] ACPI: FACS 1FFF0000, 0040
[    0.000000] ACPI: APIC 1FFF7580, 005A (r1 Nvidia AWRDACPI 42302E31 AWRD        0)
[    0.000000] Nvidia board detected. Ignoring ACPI timer override.
[    0.000000] If you got timer trouble try acpi_use_timer_override
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:8 APIC version 16
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: BIOS IRQ0 pin2 override ignored.
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:dec00000)
[    0.000000] Built 1 zonelists.  Total pages: 130033
[    0.000000] Kernel command line: root=UUID=66648c0f-9f4e-4981-85fc-528e81f1924e ro quiet splash
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] Detected 1797.284 MHz processor.
[   40.212117] Console: colour VGA+ 80x25
[   40.212487] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   40.212768] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   40.227022] Memory: 508172k/524224k available (2015k kernel code, 15416k reserved, 916k data, 364k init, 0k highmem)
[   40.227034] virtual kernel memory layout:
[   40.227035]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   40.227036]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   40.227038]     vmalloc : 0xe0800000 - 0xff7fe000   ( 495 MB)
[   40.227039]     lowmem  : 0xc0000000 - 0xdfff0000   ( 511 MB)
[   40.227041]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[   40.227042]       .data : 0xc02f7e66 - 0xc03dce84   ( 916 kB)
[   40.227044]       .text : 0xc0100000 - 0xc02f7e66   (2015 kB)
[   40.227048] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   40.227094] SLUB: Genslabs=22, HWalign=32, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   40.307015] Calibrating delay using timer specific routine.. 3597.50 BogoMIPS (lpj=7195018)
[   40.307049] Security Framework v1.0.0 initialized
[   40.307057] SELinux:  Disabled at boot.
[   40.307075] Mount-cache hash table entries: 512
[   40.307224] CPU: After generic identify, caps: 0383fbff c1c3fbff 00000000 00000000 00000000 00000000 00000000
[   40.307234] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   40.307237] CPU: L2 Cache: 256K (64 bytes/line)
[   40.307240] CPU: After all inits, caps: 0383fbff c1c3fbff 00000000 00000420 00000000 00000000 00000000
[   40.307252] Compat vDSO mapped to ffffe000.
[   40.307266] Checking 'hlt' instruction... OK.
[   40.323138] SMP alternatives: switching to UP code
[   40.323430] Freeing SMP alternatives: 11k freed
[   40.323827] Early unpacking initramfs... done
[   40.665613] ACPI: Core revision 20070126
[   40.665722] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   40.668665] CPU0: AMD Athlon(tm) XP 2200+ stepping 00
[   40.668689] Total of 1 processors activated (3597.50 BogoMIPS).
[   40.668891] ENABLING IO-APIC IRQs
[   40.669087] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
[   40.814449] Brought up 1 CPUs
[   40.814598] Booting paravirtualized kernel on bare hardware
[   40.814671] Time:  2:15:52  Date: 01/15/108
[   40.814710] NET: Registered protocol family 16
[   40.814828] EISA bus registered
[   40.814842] ACPI: bus type pci registered
[   40.847006] PCI: PCI BIOS revision 2.10 entry at 0xfb560, last bus=3
[   40.847009] PCI: Using configuration type 1
[   40.847011] Setting up standard PCI resources
[   40.852077] ACPI: EC: Look up EC in DSDT
[   40.857163] ACPI: Interpreter enabled
[   40.857167] ACPI: (supports S0 S1 S4 S5)
[   40.857185] ACPI: Using IOAPIC for interrupt routing
[   40.866748] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   40.866760] PCI: Probing PCI hardware (bus 00)
[   40.866842] PCI: nForce2 C1 Halt Disconnect fixup
[   40.867942] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   40.868117] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[   40.868363] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGPB._PRT]
[   40.868482] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB1._PRT]
[   40.924051] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[   40.924208] ACPI: PCI Interrupt Link [LNK2] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   40.924363] ACPI: PCI Interrupt Link [LNK3] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[   40.924515] ACPI: PCI Interrupt Link [LNK4] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[   40.924667] ACPI: PCI Interrupt Link [LNK5] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   40.924821] ACPI: PCI Interrupt Link [LUBA] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[   40.924972] ACPI: PCI Interrupt Link [LUBB] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   40.925126] ACPI: PCI Interrupt Link [LMAC] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[   40.925279] ACPI: PCI Interrupt Link [LAPU] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[   40.925442] ACPI: PCI Interrupt Link [LACI] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[   40.925595] ACPI: PCI Interrupt Link [LMCI] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   40.925747] ACPI: PCI Interrupt Link [LSMB] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   40.925901] ACPI: PCI Interrupt Link [LUB2] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[   40.926061] ACPI: PCI Interrupt Link [LFIR] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[   40.926214] ACPI: PCI Interrupt Link [L3CM] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[   40.926383] ACPI: PCI Interrupt Link [LIDE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   40.926520] ACPI: PCI Interrupt Link [APC1] (IRQs *16)
[   40.926640] ACPI: PCI Interrupt Link [APC2] (IRQs *17), disabled.
[   40.926759] ACPI: PCI Interrupt Link [APC3] (IRQs *18)
[   40.926877] ACPI: PCI Interrupt Link [APC4] (IRQs *19)
[   40.927003] ACPI: PCI Interrupt Link [APC5] (IRQs *16), disabled.
[   40.927186] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22) *0
[   40.927359] ACPI: PCI Interrupt Link [APCG] (IRQs 20 21 22) *0, disabled.
[   40.927531] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22) *0
[   40.927701] ACPI: PCI Interrupt Link [APCI] (IRQs 20 21 22) *0
[   40.927872] ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22) *0
[   40.928043] ACPI: PCI Interrupt Link [APCK] (IRQs 20 21 22) *0, disabled.
[   40.928164] ACPI: PCI Interrupt Link [APCS] (IRQs *23), disabled.
[   40.928334] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22) *0
[   40.928505] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22) *0
[   40.928675] ACPI: PCI Interrupt Link [AP3C] (IRQs 20 21 22) *0
[   40.928846] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22) *0, disabled.
[   40.928969] Linux Plug and Play Support v0.97 (c) Adam Belay
[   40.928985] pnp: PnP ACPI init
[   40.929005] ACPI: bus type pnp registered
[   40.934305] pnp: PnP ACPI: found 17 devices
[   40.934309] ACPI: ACPI bus type pnp unregistered
[   40.934315] PnPBIOS: Disabled by ACPI PNP
[   40.934385] PCI: Using ACPI for IRQ routing
[   40.934391] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   41.005524] NET: Registered protocol family 8
[   41.005526] NET: Registered protocol family 20
[   41.005614] pnp: 00:00: ioport range 0x4000-0x407f has been reserved
[   41.005618] pnp: 00:00: ioport range 0x4080-0x40ff has been reserved
[   41.005621] pnp: 00:00: ioport range 0x4400-0x447f has been reserved
[   41.005624] pnp: 00:00: ioport range 0x4480-0x44ff has been reserved
[   41.005627] pnp: 00:00: ioport range 0x4200-0x427f has been reserved
[   41.005630] pnp: 00:00: ioport range 0x4280-0x42ff has been reserved
[   41.005637] pnp: 00:01: ioport range 0x5000-0x503f has been reserved
[   41.005640] pnp: 00:01: ioport range 0x5500-0x553f has been reserved
[   41.005647] pnp: 00:02: iomem range 0xd2800-0xd3fff has been reserved
[   41.005650] pnp: 00:02: iomem range 0xf0000-0xf7fff could not be reserved
[   41.005654] pnp: 00:02: iomem range 0xf8000-0xfbfff could not be reserved
[   41.005657] pnp: 00:02: iomem range 0xfc000-0xfffff could not be reserved
[   41.006157] Time: tsc clocksource has been installed.
[   41.035982] PCI: Bridge: 0000:00:08.0
[   41.035985]   IO window: a000-bfff
[   41.035991]   MEM window: e8000000-e9ffffff
[   41.035996]   PREFETCH window: 30000000-300fffff
[   41.036001] PCI: Bridge: 0000:00:0c.0
[   41.036004]   IO window: c000-cfff
[   41.036009]   MEM window: e4000000-e5ffffff
[   41.036013]   PREFETCH window: 30100000-301fffff
[   41.036019] PCI: Bridge: 0000:00:1e.0
[   41.036020]   IO window: disabled.
[   41.036025]   MEM window: e6000000-e7ffffff
[   41.036029]   PREFETCH window: d0000000-dfffffff
[   41.036040] PCI: Setting latency timer of device 0000:00:08.0 to 64
[   41.036047] PCI: Setting latency timer of device 0000:00:0c.0 to 64
[   41.036064] NET: Registered protocol family 2
[   41.074132] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   41.074196] TCP established hash table entries: 16384 (order: 5, 196608 bytes)
[   41.074494] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[   41.074709] TCP: Hash tables configured (established 16384 bind 16384)
[   41.074712] TCP reno registered
[   41.086220] checking if image is initramfs... it is
[   41.537516] Switched to high resolution mode on CPU 0
[   41.736443] Freeing initrd memory: 7045k freed
[   41.736958] audit: initializing netlink socket (disabled)
[   41.736975] audit(1203041752.176:1): initialized
[   41.739104] VFS: Disk quotas dquot_6.5.1
[   41.739166] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   41.739281] io scheduler noop registered
[   41.739284] io scheduler anticipatory registered
[   41.739287] io scheduler deadline registered
[   41.739302] io scheduler cfq registered (default)
[   41.739357] Boot video device is 0000:03:00.0
[   41.739581] isapnp: Scanning for PnP cards...
[   42.093679] isapnp: No Plug & Play device found
[   42.127116] Real Time Clock Driver v1.12ac
[   42.127243] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   42.127358] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   42.127689] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   42.128548] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   42.129039] 00:0b: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   42.129597] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
[   42.129608] ACPI: PCI Interrupt 0000:01:08.0[A] -> Link [APC3] -> GSI 18 (level, high) -> IRQ 16
[   42.132812] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   42.133080] input: Macintosh mouse button emulation as /class/input/input0
[   42.133186] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   42.136785] serio: i8042 KBD port at 0x60,0x64 irq 1
[   42.136795] serio: i8042 AUX port at 0x60,0x64 irq 12
[   42.137039] mice: PS/2 mouse device common for all mice
[   42.137190] EISA: Probing bus 0 at eisa.0
[   42.137216] Cannot allocate resource for EISA slot 4
[   42.137219] Cannot allocate resource for EISA slot 5
[   42.137235] EISA: Detected 0 cards.
[   42.137360] TCP cubic registered
[   42.137371] NET: Registered protocol family 1
[   42.137395] Using IPI No-Shortcut mode
[   42.137627]   Magic number: 12:30:258
[   42.137682]   hash matches device ttyx0
[   42.138328] Freeing unused kernel memory: 364k freed
[   42.172623] input: AT Translated Set 2 keyboard as /class/input/input1
[   43.378435] AppArmor: AppArmor initialized<5>audit(1203041753.676:2):  type=1505 info="AppArmor initialized" pid=1247
[   43.385816] fuse init (API version 7.8)
[   43.391386] Failure registering capabilities with primary security module.
[   44.092833] usbcore: registered new interface driver usbfs
[   44.092867] usbcore: registered new interface driver hub
[   44.092897] usbcore: registered new device driver usb
[   44.093818] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   44.094235] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 22
[   44.094246] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [APCF] -> GSI 22 (level, high) -> IRQ 17
[   44.094263] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   44.094267] ohci_hcd 0000:00:02.0: OHCI Host Controller
[   44.094497] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
[   44.094519] ohci_hcd 0000:00:02.0: irq 17, io mem 0xea087000
[   44.163703] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.60.
[   44.184019] usb usb1: configuration #1 chosen from 1 choice
[   44.184054] hub 1-0:1.0: USB hub found
[   44.184069] hub 1-0:1.0: 3 ports detected
[   44.273966] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   44.273974] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   44.286179] ACPI: PCI Interrupt Link [APCG] enabled at IRQ 21
[   44.286193] ACPI: PCI Interrupt 0000:00:02.1[B] -> Link [APCG] -> GSI 21 (level, high) -> IRQ 18
[   44.286212] PCI: Setting latency timer of device 0000:00:02.1 to 64
[   44.286217] ohci_hcd 0000:00:02.1: OHCI Host Controller
[   44.286245] ohci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 2
[   44.286267] ohci_hcd 0000:00:02.1: irq 18, io mem 0xea082000
[   44.343757] usb usb2: configuration #1 chosen from 1 choice
[   44.343795] hub 2-0:1.0: USB hub found
[   44.343811] hub 2-0:1.0: 3 ports detected
[   44.409832] Floppy drive(s): fd0 is 1.44M
[   44.435208] SCSI subsystem initialized
[   44.441106] libata version 2.21 loaded.
[   44.446290] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 20
[   44.446304] ACPI: PCI Interrupt 0000:00:02.2[C] -> Link [APCL] -> GSI 20 (level, high) -> IRQ 19
[   44.446320] PCI: Setting latency timer of device 0000:00:02.2 to 64
[   44.446324] ehci_hcd 0000:00:02.2: EHCI Host Controller
[   44.446365] ehci_hcd 0000:00:02.2: new USB bus registered, assigned bus number 3
[   44.446406] ehci_hcd 0000:00:02.2: selective suspend/wakeup unavailable
[   44.446413] ehci_hcd 0000:00:02.2: debug port 1
[   44.446419] PCI: cache line size of 64 is not supported by device 0000:00:02.2
[   44.446433] ehci_hcd 0000:00:02.2: irq 19, io mem 0xea083000
[   44.446442] ehci_hcd 0000:00:02.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   44.446550] usb usb3: configuration #1 chosen from 1 choice
[   44.446596] hub 3-0:1.0: USB hub found
[   44.446608] hub 3-0:1.0: 6 ports detected
[   44.502407] FDC 0 is a post-1991 82077
[   44.549988] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 22
[   44.549996] ACPI: PCI Interrupt 0000:00:04.0[A] -> Link [APCH] -> GSI 22 (level, high) -> IRQ 17
[   44.550004] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   45.068845] eth0: forcedeth.c: subsystem: 01043:80a7 bound to 0000:00:04.0
[   45.069656] ACPI: PCI Interrupt Link [APCM] enabled at IRQ 21
[   45.069663] ACPI: PCI Interrupt 0000:00:0d.0[A] -> Link [APCM] -> GSI 21 (level, high) -> IRQ 18
[   45.069672] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[   45.121561] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[18]  MMIO=[ea084000-ea0847ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[   45.126757] NFORCE2: IDE controller at PCI slot 0000:00:09.0
[   45.126782] NFORCE2: chipset revision 162
[   45.126785] NFORCE2: not 100% native mode: will probe irqs later
[   45.126794] NFORCE2: 0000:00:09.0 (rev a2) UDMA133 controller
[   45.126805]     ide0: BM-DMA at 0xf000-0xf007, BIOS settings: hda:DMA, hdb:DMA
[   45.126817]     ide1: BM-DMA at 0xf008-0xf00f, BIOS settings: hdc:DMA, hdd:DMA
[   45.126828] Probing IDE interface ide0...
[   45.412226] hda: WDC WD200BB-60CJA0, ATA DISK drive
[   46.084950] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   46.104391] Probing IDE interface ide1...
[   46.838276] hdc: OPTORITE CD-RW CW4802, ATAPI CD/DVD-ROM drive
[   47.621195] hdd: IDE DVD-ROM 16X, ATAPI CD/DVD-ROM drive
[   47.677649] ide1 at 0x170-0x177,0x376 on irq 15
[   47.682477] ACPI: PCI Interrupt Link [AP3C] enabled at IRQ 20
[   47.682485] ACPI: PCI Interrupt 0000:02:01.0[A] -> Link [AP3C] -> GSI 20 (level, high) -> IRQ 19
[   47.682494] 3c59x: Donald Becker and others.
[   47.682502] 0000:02:01.0: 3Com PCI 3c920 Tornado at e084c000.
[   47.705631] sata_sil 0000:01:0b.0: version 2.2
[   47.705710] ACPI: PCI Interrupt 0000:01:0b.0[A] -> Link [APC3] -> GSI 18 (level, high) -> IRQ 16
[   47.706446] scsi0 : sata_sil
[   47.706793] scsi1 : sata_sil
[   47.706952] ata1: SATA max UDMA/100 cmd 0xe0850080 ctl 0xe085008a bmdma 0xe0850000 irq 16
[   47.706958] ata2: SATA max UDMA/100 cmd 0xe08500c0 ctl 0xe08500ca bmdma 0xe0850008 irq 16
[   47.720982] hda: max request size: 128KiB
[   47.727648] hda: 39102336 sectors (20020 MB) w/2048KiB Cache, CHS=38792/16/63, UDMA(33)
[   47.727658] hda: cache flushes not supported
[   47.727718]  hda: hda1 hda2 < hda5 >
[   47.760916] hdc: ATAPI 48X CD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
[   47.760928] Uniform CD-ROM driver Revision: 3.20
[   47.771714] hdd: ATAPI 48X DVD-ROM drive, 512kB Cache, UDMA(33)
[   47.980076] Attempting manual resume
[   47.980081] swsusp: Resume From Partition 3:5
[   47.980083] PM: Checking swsusp image.
[   47.980325] PM: Resume from disk failed.
[   47.997963] EXT3-fs: INFO: recovery required on readonly filesystem.
[   47.997968] EXT3-fs: write access will be enabled during recovery.
[   48.016537] ata1: SATA link down (SStatus 0 SControl 310)
[   48.328109] ata2: SATA link down (SStatus 0 SControl 310)
[   51.120379] kjournald starting.  Commit interval 5 seconds
[   51.120406] EXT3-fs: hda1: orphan cleanup on readonly fs
[   51.120415] ext3_orphan_cleanup: deleting unreferenced inode 2044295
[   51.120482] EXT3-fs: hda1: 1 orphan inode deleted
[   51.120485] EXT3-fs: recovery complete.
[   51.151503] EXT3-fs: mounted filesystem with ordered data mode.
[   58.636368] eth1:  setting half-duplex.
[   58.654386] eth0: no link during initialization.
[   60.204169] NET: Registered protocol family 17
[   60.610246] Linux agpgart interface v0.102 (c) Dave Jones
[   60.621785] agpgart: Detected NVIDIA nForce2 chipset
[   60.626636] agpgart: AGP aperture is 64M @ 0xe0000000
[   60.730369] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x5000
[   60.730410] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x5500
[   61.719859] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   61.755286] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   62.321694] logips2pp: Detected unknown logitech mouse model 62
[   62.595589] nvidia: module license 'NVIDIA' taints kernel.
[   62.852977] ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19
[   62.852990] ACPI: PCI Interrupt 0000:03:00.0[A] -> Link [APC4] -> GSI 19 (level, high) -> IRQ 20
[   62.853465] NVRM: loading NVIDIA UNIX x86 Kernel Module  100.14.19  Wed Sep 12 14:12:24 PDT 2007
[   62.965266] input: ImExPS/2 Logitech Explorer Mouse as /class/input/input2
[   62.968724] parport_pc 00:0c: reported by Plug and Play ACPI
[   62.968786] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   62.971120] input: PC Speaker as /class/input/input3
[   63.462497] ACPI: PCI Interrupt Link [APCJ] enabled at IRQ 22
[   63.462505] ACPI: PCI Interrupt 0000:00:06.0[A] -> Link [APCJ] -> GSI 22 (level, high) -> IRQ 17
[   63.462533] PCI: Setting latency timer of device 0000:00:06.0 to 64
[   63.782891] intel8x0_measure_ac97_clock: measured 52741 usecs
[   63.782897] intel8x0: clocking to 47466
[   64.311142] lp0: using parport0 (interrupt-driven).
[   64.400674] Adding 859436k swap on /dev/hda5.  Priority:-1 extents:1 across:859436k
[   64.674747] EXT3 FS on hda1, internal journal
[   65.716749] No dock devices found.
[   65.805238] input: Power Button (FF) as /class/input/input4
[   65.810855] ACPI: Power Button (FF) [PWRF]
[   65.855745] input: Power Button (CM) as /class/input/input5
[   65.861320] ACPI: Power Button (CM) [PWRB]
[   67.400342] ppdev: user-space parallel port driver
[   67.642358] audit(1203041779.300:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4883 profile="/usr/sbin/cupsd"
[   67.679336] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   67.679343] apm: overridden by ACPI.
[   67.874400] NET: Registered protocol family 10
[   67.874605] lo: Disabled Privacy Extensions
[   67.874849] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   67.874936] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   67.982813] Failure registering capabilities with primary security module.
[   68.197599] Bluetooth: Core ver 2.11
[   68.197751] NET: Registered protocol family 31
[   68.197755] Bluetooth: HCI device and connection manager initialized
[   68.197759] Bluetooth: HCI socket layer initialized
[   68.220492] Bluetooth: L2CAP ver 2.8
[   68.220498] Bluetooth: L2CAP socket layer initialized
[   68.313412] Bluetooth: RFCOMM socket layer initialized
[   68.313517] Bluetooth: RFCOMM TTY layer initialized
[   68.313520] Bluetooth: RFCOMM ver 1.8
[   70.378370] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[   70.378388] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[   70.378466] agpgart: Putting AGP V3 device at 0000:03:00.0 into 8x mode
[  199.178242] ndiswrapper version 1.45 loaded (smp=yes)
[  199.263093] ndiswrapper: driver wg311v3 (NETGEAR,08/22/2005,3.2.1.3) loaded
[  199.264249] ACPI: PCI Interrupt Link [APC1] enabled at IRQ 16
[  199.264262] ACPI: PCI Interrupt 0000:01:06.0[A] -> Link [APC1] -> GSI 16 (level, high) -> IRQ 21
[  199.267267] ndiswrapper: using IRQ 21
[  199.533971] wlan0: ethernet device 00:14:6c:71:c6:ab using NDIS driver: wg311v3, version: 0x3020002, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 11AB:1FAA.5.conf
[  199.533999] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[  199.534662] usbcore: registered new interface driver ndiswrapper
[  201.322955] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  220.984351] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  237.220827] wlan0: no IPv6 routers present

```

Please hlep. I cant get anything done.

---

### Post by Dwiman89 on 2008-02-15
Anyone?

---

### Post by rustybronco on 2008-02-15
> **Dwiman89 said:**
> [  199.533971] wlan0: ethernet device 00:14:6c:71:c6:ab using NDIS driver: **wg311v3**, version: 0x3020002, NDIS version: 0x501, vendor: 'NDIS Network Adapter', **11AB:1FAA**.5.conf
[  199.533999] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[/CODE]

Please hlep. I cant get anything done.

GOOGLE>11AB:1FAA chipset, Marvell 88w8335 chipset

[http://ubuntuforums.org/showpost.php?p=3766787&postcount=10](http://ubuntuforums.org/showpost.php?p=3766787&postcount=10)

---

### Post by Dwiman89 on 2008-02-15
Is that a trusted place to get the drivers? It looks like a photo sharing site. Also are those drivers  up to date? My driver worked fine... How does this stuff work???

---

### Post by rustybronco on 2008-02-15
I don't know if he can be trusted or not, but by his posts he doesn't look dis-reputable.
My reasoning, if you run into frequent drops/disconnections usually it is because of the wrong driver being used for your chipset.
do you have the correct driver disc for your card? have you checked for updated drivers?
yes it could be a hardware issue, but don't rule out software/bad iso issues.

---

### Post by rustybronco on 2008-02-15
> **Dwiman89 said:**
> is there a way i can find out if its a hardware issue.  Substitution of a known good part, using it on a different machine and seeing if the issues show up on the 2nd machine.

---

### Post by Dwiman89 on 2008-02-16
I found a driver I got from the Netgear site. I am having trouble getting it to unzip so I can get the needed files. I try to unzip it and this is what I get.
```
e:~/driversxp/driverupdate$ unzip wg311v3_3_0_setup.exe
Archive:  wg311v3_3_0_setup.exe
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
unzip:  cannot find zipfile directory in one of wg311v3_3_0_setup.exe or
        wg311v3_3_0_setup.exe.zip, and cannot find wg311v3_3_0_setup.exe.ZIP, period.

```

Any suggestions?

---

### Post by Dwiman89 on 2008-02-18
Anyone know how to unzip this????

---

### Post by Dwiman89 on 2008-02-19
Should this thread be in another place?

---

### Post by Dwiman89 on 2008-02-21
bump

---

### Post by IamAcoconut on 2008-02-21
> **Dwiman89 said:**
> I found a driver I got from the Netgear site. I am having trouble getting it to unzip so I can get the needed files. I try to unzip it and this is what I get.
```
e:~/driversxp/driverupdate$ unzip wg311v3_3_0_setup.exe
Archive:  wg311v3_3_0_setup.exe
  End-of-central-directory signature not found.  Either [COLOR="Red"][B][U]this file is not
  a zipfile[/U][/B][/COLOR], or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
unzip:  cannot find zipfile directory in one of wg311v3_3_0_setup.exe or
        wg311v3_3_0_setup.exe.zip, and cannot find wg311v3_3_0_setup.exe.ZIP, period.

```

Any suggestions?
Ahm, well, to read what you posted?
It's an exe file, so it's a windows driver*. 
Why do you wanna install it? Absolutely sure there's no linux driver, or the device doesn't work with the linux driver? Absolutely sure there's no inf. file aviable to install via ndiswrapper?
Well, first of all you didn't even say why you wanna mess with the network interface. So please answer. And post what refers to the network card in question from the output of ```
lshw -C network
```

*You may try to install it via wine, and see whether it creates a  inf. or .sys file somewhere in your ~/.wine/drive_c/windows/ and then install the driver via ndiswrapper.

---

### Post by Dwiman89 on 2008-02-21
Im trying to update the driver for my Netgear card(Marvell chipset). in the past the drivers have alwase been in an .exe file.

This is what the ndiswrapper instructions say;
> Many Windows drivers are distributed either as zipped files or cab
files. Zipped files, even if they are .exe files, can be extracted
with 'unzip' in Linux; cab files can be extracted with combination of
'cabextract' and 'unshield' programs.

Once the driver has been unpacked, locate .inf and .sys files. If
necessary, move these files so both .inf and .sys are in the same
directory. Some drivers also come with firmware files, such as
fwrad16.bin etc. These files also should be in the same
directory. Then install the Windows driver with

Here is the output from that command;
```
ticast=yes
  *-network
       description: Wireless interface
       product: 88w8335 [Libertas] 802.11b/g Wireless
       vendor: Marvell Technology Group Ltd.
       physical id: 6
       bus info: pci@0000:01:06.0
       logical name: wlan0
       version: 03
       serial: 00:14:6c:71:c6:ab
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+wg311v3 driverversion=1.45+NETGEAR,08/22/2005,3.2.1.3 ip=192.168.1.102 latency=32 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network

```

I hope that helps you help me, thanks.

---

### Post by IamAcoconut on 2008-02-22
OK, now I see, there's no alternative to windows driver, but you still didn't say, **what's wrong** with the network card.
If you must install it, try maybe:
```
sudo apt-get install rar unace unrar p7zip arj unzoo lha libarchive1 libarchive-tar-perl libarchive-zip-perl dpkg-dev
```
if something wasn't already installed, install it and try to unzip again. If this, fails, then try:
 ```
wine  wg311v3_3_0_setup.exe
``` and look for an .inf or .sys file of that name somewhere in ~/.wine/drive_c/windows/

---

### Post by firecat53 on 2008-02-23
To extract, try:

sudo aptitude install cabextract
cabextract wg*exe

Good luck :)
Scott

---

