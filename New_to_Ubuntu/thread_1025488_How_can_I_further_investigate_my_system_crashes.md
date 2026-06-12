---
title: "How can I further investigate my system crashes ?"
date: 2008-12-30
forum: New to Ubuntu
---

### Post by mrwaistcoat on 2008-12-30
I recently installed Intrepid Ubuntu, having removed windows completely

At seemingly random intervals, the caps and scroll lock keys start to flash and the system crashes totally.

So far I've tried

* running a memory test - no errors, but does say "Chipset Intel i845 (ECC : Disabled" - should it be disabled ?   I am also having multi-media problems - is there a connection here   ?

* Alt / SysRq / F1 has not effect after a crash

* I've tried removing all USB devices - thats not the problem

* I've tried removing all desktop effects - thats no the problem

Any ideas for other things I can try ?  

Thanks in advance for any ideas

---

### Post by freesitebuilder on 2008-12-30
System > Admin > System log gives you access to various system event logs which may help.

---

### Post by linux_tech on 2008-12-30
caps and scroll lock keys start to flash- sounds like kernel panic

-you should try memtest86 and let run for at least 1 hr.

-check your bios, see if ecc setting is disabled or not. Try opposite setting,  run memtest86 again

-Also try reseating memory, if you have more than one stick, you may try running just one.

-if you get errors from memtest, then sometimes there are a few things to try to fix, but sometimes you need to get new memory

-You can also do fsck

-run "dmesg" right after next crash and post output

- you can try loading different kernel

---

### Post by mrwaistcoat on 2008-12-30
Many thanks

Here is the results of the dmesg. Im online via ethernet - yet there seems to be lots of "wireless" activity below.  I do have ( I think ) 2 wireless cards in the PC, neither of which I use

Any advice deeply appreciated

Thanks again



[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] Memory: 635204k/655232k available (2572k kernel code, 19516k reserved, 1160k data, 424k init, 0k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xe8800000 - 0xff3fe000   ( 363 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xe7fe0000   ( 639 MB)
[    0.004000]       .init : 0xc04ab000 - 0xc0515000   ( 424 kB)
[    0.004000]       .data : 0xc038335a - 0xc04a5680   (1160 kB)
[    0.004000]       .text : 0xc0100000 - 0xc038335a   (2572 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] CPA: page pool initialized 1 of 1 pages preallocated
[    0.004000] SLUB: Genslabs=12, HWalign=128, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.004019] Calibrating delay loop (skipped), value calculated using timer frequency.. 3389.98 BogoMIPS (lpj=6779960)
[    0.004058] Security Framework initialized
[    0.004074] SELinux:  Disabled at boot.
[    0.004115] AppArmor: AppArmor initialized
[    0.004136] Mount-cache hash table entries: 512
[    0.004524] Initializing cgroup subsys ns
[    0.004538] Initializing cgroup subsys cpuacct
[    0.004544] Initializing cgroup subsys memory
[    0.004580] CPU: Trace cache: 12K uops, L1 D cache: 8K
[    0.004587] CPU: L2 cache: 256K
[    0.004593] CPU: Hyper-Threading is disabled
[    0.004628] Checking 'hlt' instruction... OK.
[    0.020915] SMP alternatives: switching to UP code
[    0.032072] Freeing SMP alternatives: 11k freed
[    0.032083] ACPI: Core revision 20080609
[    0.032195] ACPI: Checking initramfs for custom DSDT
[    0.619932] ENABLING IO-APIC IRQs
[    0.620031] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.659875] CPU0: Intel(R) Pentium(R) 4 CPU 1.70GHz stepping 02
[    0.660031] Brought up 1 CPUs
[    0.660031] Total of 1 processors activated (3389.98 BogoMIPS).
[    0.660031] CPU0 attaching sched-domain:
[    0.660031]  domain 0: span 0 level CPU
[    0.660031]   groups: 0
[    0.660031] net_namespace: 840 bytes
[    0.660031] Booting paravirtualized kernel on bare hardware
[    0.660031] Time: 20:50:55  Date: 12/30/08
[    0.660031] NET: Registered protocol family 16
[    0.660031] EISA bus registered
[    0.660031] ACPI: bus type pci registered
[    0.660031] PCI: PCI BIOS revision 2.10 entry at 0xebb57, last bus=2
[    0.660031] PCI: Using configuration type 1 for base access
[    0.662523] ACPI: EC: Look up EC in DSDT
[    0.667977] ACPI: Interpreter enabled
[    0.667986] ACPI: (supports S0 S1 S3 S4 S5)
[    0.668155] ACPI: Using IOAPIC for interrupt routing
[    0.678543] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.678737] PCI: 0000:00:00.0 reg 10 32bit mmio: [ec000000, efffffff]
[    0.678957] pci 0000:00:1f.0: quirk: region f800-f87f claimed by ICH4 ACPI/GPIO/TCO
[    0.678964] pci 0000:00:1f.0: quirk: region fa00-fa3f claimed by ICH4 GPIO
[    0.679024] PCI: 0000:00:1f.1 reg 20 io port: [2460, 246f]
[    0.679097] PCI: 0000:00:1f.2 reg 20 io port: [2440, 245f]
[    0.679146] PCI: 0000:00:1f.5 reg 10 io port: [2000, 20ff]
[    0.679156] PCI: 0000:00:1f.5 reg 14 io port: [2400, 243f]
[    0.679248] PCI: 0000:01:00.0 reg 10 32bit mmio: [f9000000, f9ffffff]
[    0.679257] PCI: 0000:01:00.0 reg 14 32bit mmio: [f0000000, f7ffffff]
[    0.679285] PCI: 0000:01:00.0 reg 30 32bit mmio: [0, 1ffff]
[    0.679349] PCI: bridge 0000:00:01.0 32bit mmio: [f9000000, fa1fffff]
[    0.679356] PCI: bridge 0000:00:01.0 32bit mmio pref: [f0000000, f81fffff]
[    0.679415] PCI: 0000:02:08.0 reg 10 32bit mmio: [f8422000, f8422fff]
[    0.679426] PCI: 0000:02:08.0 reg 14 io port: [1000, 103f]
[    0.679474] pci 0000:02:08.0: supports D1
[    0.679477] pci 0000:02:08.0: supports D2
[    0.679481] pci 0000:02:08.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.679488] pci 0000:02:08.0: PME# disabled
[    0.679526] PCI: 0000:02:09.0 reg 10 32bit mmio: [f8420000, f8421fff]
[    0.679536] PCI: 0000:02:09.0 reg 14 32bit mmio: [f8400000, f841ffff]
[    0.679583] pci 0000:02:09.0: supports D1
[    0.679586] pci 0000:02:09.0: supports D2
[    0.679590] pci 0000:02:09.0: PME# supported from D0 D1 D2 D3hot
[    0.679597] pci 0000:02:09.0: PME# disabled
[    0.679634] pci 0000:00:1e.0: transparent bridge
[    0.679641] PCI: bridge 0000:00:1e.0 io port: [1000, 1fff]
[    0.679648] PCI: bridge 0000:00:1e.0 32bit mmio: [f8200000, f84fffff]
[    0.679668] bus 00 -> node 0
[    0.679690] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.680164] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB_._PRT]
[    0.686083] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 11 14 15) *0, disabled.
[    0.686265] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *10 11 14 15)
[    0.686440] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *10 11 14 15)
[    0.686613] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 *11 14 15)
[    0.686788] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 *5 6 7 10 11 14 15)
[    0.686962] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 14 15) *0, disabled.
[    0.687138] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 14 15) *0, disabled.
[    0.687314] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 11 14 15) *0, disabled.
[    0.687793] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.687905] pnp: PnP ACPI init
[    0.687932] ACPI: bus type pnp registered
[    0.694293] pnp 00:0d: io resource (0xf800-0xf81f) overlaps 0000:00:1f.0 BAR 7 (0xf800-0xf87f), disabling
[    0.694302] pnp 00:0d: io resource (0xf820-0xf83f) overlaps 0000:00:1f.0 BAR 7 (0xf800-0xf87f), disabling
[    0.694309] pnp 00:0d: io resource (0xf840-0xf85f) overlaps 0000:00:1f.0 BAR 7 (0xf800-0xf87f), disabling
[    0.694315] pnp 00:0d: io resource (0xf860-0xf87f) overlaps 0000:00:1f.0 BAR 7 (0xf800-0xf87f), disabling
[    0.695692] pnp: PnP ACPI: found 15 devices
[    0.695700] ACPI: ACPI bus type pnp unregistered
[    0.695708] PnPBIOS: Disabled by ACPI PNP
[    0.696944] PCI: Using ACPI for IRQ routing
[    0.697218] NET: Registered protocol family 8
[    0.697218] NET: Registered protocol family 20
[    0.697218] NetLabel: Initializing
[    0.697218] NetLabel:  domain hash size = 128
[    0.697218] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.697218] NetLabel:  unlabeled traffic allowed by default
[    0.697218] tracer: 772 pages allocated for 65536 entries of 48 bytes
[    0.697218]    actual entries 65620
[    0.697244] AppArmor: AppArmor Filesystem Enabled
[    0.697282] ACPI: RTC can wake from S4
[    0.697334] system 00:0c: ioport range 0x4d0-0x4d1 has been reserved
[    0.697334] system 00:0d: ioport range 0x400-0x41f has been reserved
[    0.697334] system 00:0d: ioport range 0x420-0x43f has been reserved
[    0.697334] system 00:0d: ioport range 0x440-0x45f has been reserved
[    0.697334] system 00:0d: ioport range 0x460-0x47f has been reserved
[    0.697334] system 00:0d: ioport range 0xfa00-0xfa3f has been reserved
[    0.697334] system 00:0d: ioport range 0xfc00-0xfc7f has been reserved
[    0.697334] system 00:0d: ioport range 0xfc80-0xfcff has been reserved
[    0.697334] system 00:0d: ioport range 0xfe00-0xfe7f has been reserved
[    0.697334] system 00:0d: ioport range 0xfe80-0xfeff has been reserved
[    0.697334] system 00:0e: iomem range 0x0-0x9ffff could not be reserved
[    0.697334] system 00:0e: iomem range 0xe8000-0xfffff could not be reserved
[    0.697334] system 00:0e: iomem range 0x100000-0x280fffff could not be reserved
[    0.697334] system 00:0e: iomem range 0xfff80000-0xffffffff could not be reserved
[    0.697334] system 00:0e: iomem range 0xfeea0000-0xfeebffff could not be reserved
[    0.697334] system 00:0e: iomem range 0xfee00000-0xfee00fff could not be reserved
[    0.697334] system 00:0e: iomem range 0xd0c00-0xd3fff has been reserved
[    0.697334] system 00:0e: iomem range 0xffb80000-0xffbfffff could not be reserved
[    0.735097] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.735105] pci 0000:00:01.0:   IO window: disabled
[    0.735113] pci 0000:00:01.0:   MEM window: 0xf9000000-0xfa1fffff
[    0.735121] pci 0000:00:01.0:   PREFETCH window: 0x000000f0000000-0x000000f81fffff
[    0.735130] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:02
[    0.735137] pci 0000:00:1e.0:   IO window: 0x1000-0x1fff
[    0.735147] pci 0000:00:1e.0:   MEM window: 0xf8200000-0xf84fffff
[    0.735154] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.735184] pci 0000:00:1e.0: setting latency timer to 64
[    0.735192] bus: 00 index 0 io port: [0, ffff]
[    0.735196] bus: 00 index 1 mmio: [0, ffffffff]
[    0.735199] bus: 01 index 0 mmio: [0, 0]
[    0.735203] bus: 01 index 1 mmio: [f9000000, fa1fffff]
[    0.735208] bus: 01 index 2 mmio: [f0000000, f81fffff]
[    0.735211] bus: 01 index 3 mmio: [0, 0]
[    0.735215] bus: 02 index 0 io port: [1000, 1fff]
[    0.735219] bus: 02 index 1 mmio: [f8200000, f84fffff]
[    0.735223] bus: 02 index 2 mmio: [0, 0]
[    0.735227] bus: 02 index 3 io port: [0, ffff]
[    0.735230] bus: 02 index 4 mmio: [0, ffffffff]
[    0.735261] NET: Registered protocol family 2
[    0.735580] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.736389] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.738949] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.740445] TCP: Hash tables configured (established 131072 bind 65536)
[    0.740458] TCP reno registered
[    0.740820] NET: Registered protocol family 1
[    0.741114] checking if image is initramfs...<7>Switched to high resolution mode on CPU 0
[    1.322157]  it is
[    1.996563] Freeing initrd memory: 7990k freed
[    1.998423] audit: initializing netlink socket (disabled)
[    1.998464] type=2000 audit(1230670255.996:1): initialized
[    2.006335] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    2.012505] VFS: Disk quotas dquot_6.5.1
[    2.012816] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    2.013756] msgmni has been set to 1256
[    2.014195] io scheduler noop registered
[    2.014203] io scheduler anticipatory registered
[    2.014207] io scheduler deadline registered
[    2.014256] io scheduler cfq registered (default)
[    2.014333] pci 0000:01:00.0: Boot video device
[    2.014358] pci 0000:02:08.0: Firmware left e100 interrupts enabled; disabling
[    2.015378] isapnp: Scanning for PnP cards...
[    2.369400] isapnp: No Plug & Play device found
[    2.567207] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    2.567464] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    2.568102] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    2.570715] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    2.572118] 00:09: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    2.577799] brd: module loaded
[    2.578011] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    2.578387] PNP: PS/2 Controller [PNP0303:KBD,PNP0f0e:PS2M] at 0x60,0x64 irq 1,12
[    2.581181] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.581198] serio: i8042 AUX port at 0x60,0x64 irq 12
[    2.582904] mice: PS/2 mouse device common for all mice
[    2.583517] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    2.583559] rtc0: alarms up to one month, y3k
[    2.583976] EISA: Probing bus 0 at eisa.0
[    2.583991] Cannot allocate resource for EISA slot 1
[    2.583995] Cannot allocate resource for EISA slot 2
[    2.584060] EISA: Detected 0 cards.
[    2.584069] cpuidle: using governor ladder
[    2.584073] cpuidle: using governor menu
[    2.585275] TCP cubic registered
[    2.585356] Using IPI No-Shortcut mode
[    2.586534] registered taskstats version 1
[    2.586716]   Magic number: 4:203:853
[    2.586853] tty ptyv5: hash matches
[    2.586968] rtc_cmos 00:03: setting system clock to 2008-12-30 20:50:57 UTC (1230670257)
[    2.586974] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.586978] EDD information not available.
[    2.587996] Freeing unused kernel memory: 424k freed
[    2.588142] Write protecting the kernel text: 2576k
[    2.588200] Write protecting the kernel read-only data: 936k
[    2.607579] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    3.032478] fuse init (API version 7.9)
[    3.213528] processor ACPI0007:00: registered as cooling_device0
[    3.213550] ACPI: Processor [CPU0] (supports 8 throttling states)
[    4.445788] No dock devices found.
[    4.716550] SCSI subsystem initialized
[    4.731197] e100: Intel(R) PRO/100 Network Driver, 3.5.23-k4-NAPI
[    4.731205] e100: Copyright(c) 1999-2006 Intel Corporation
[    4.731297] e100 0000:02:08.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    4.821349] e100 0000:02:08.0: PME# disabled
[    4.948525] usbcore: registered new interface driver usbfs
[    4.948582] usbcore: registered new interface driver hub
[    4.951790] usbcore: registered new device driver usb
[    4.954327] e100: eth0: e100_probe: addr 0xf8422000, irq 20, MAC addr 00:08:02:22:a2:26
[    4.965453] USB Universal Host Controller Interface driver v3.0
[    4.965579] uhci_hcd 0000:00:1f.2: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    4.965600] uhci_hcd 0000:00:1f.2: setting latency timer to 64
[    4.965606] uhci_hcd 0000:00:1f.2: UHCI Host Controller
[    4.965732] uhci_hcd 0000:00:1f.2: new USB bus registered, assigned bus number 1
[    4.965784] uhci_hcd 0000:00:1f.2: irq 19, io base 0x00002440
[    4.967287] usb usb1: configuration #1 chosen from 1 choice
[    4.967362] hub 1-0:1.0: USB hub found
[    4.967391] hub 1-0:1.0: 2 ports detected
[    4.969606] libata version 3.00 loaded.
[    5.185593] pata_acpi 0000:00:1f.1: setting latency timer to 64
[    5.208148] ata_piix 0000:00:1f.1: version 2.12
[    5.208273] ata_piix 0000:00:1f.1: setting latency timer to 64
[    5.210447] scsi0 : ata_piix
[    5.210782] scsi1 : ata_piix
[    5.211199] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x2460 irq 14
[    5.211205] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x2468 irq 15
[    5.296170] usb 1-1: new full speed USB device using uhci_hcd and address 2
[    5.372447] ata1.00: ATA-5: MAXTOR 6L020J1, A93.0500, max UDMA/100
[    5.372455] ata1.00: 39102336 sectors, multi 16: LBA 
[    5.388406] ata1.00: configured for UDMA/100
[    5.460268] usb 1-1: configuration #1 chosen from 1 choice
[    5.560542] ata2.00: ATAPI: SAMSUNG CDRW/DVD SM-308B, BB02, max MWDMA2
[    5.560582] ata2.01: ATAPI: Compaq CD-ROM SC-148E,     B902, max MWDMA2
[    5.576459] ata2.00: configured for MWDMA2
[    5.584610] ata2.01: configured for MWDMA2
[    5.584913] scsi 0:0:0:0: Direct-Access     ATA      MAXTOR 6L020J1   A93. PQ: 0 ANSI: 5
[    5.585303] usb 1-2: new full speed USB device using uhci_hcd and address 3
[    5.586106] scsi 1:0:0:0: CD-ROM            SAMSUNG  CDRW/DVD SM-308B BB02 PQ: 0 ANSI: 5
[    5.586792] scsi 1:0:1:0: CD-ROM            Compaq   CD-ROM SC-148E   B902 PQ: 0 ANSI: 5
[    5.747133] usb 1-2: configuration #1 chosen from 1 choice
[    5.750912] hub 1-2:1.0: USB hub found
[    5.752786] hub 1-2:1.0: 4 ports detected
[    6.045745] usb 1-2.1: new full speed USB device using uhci_hcd and address 4
[    6.327471] usb 1-2.1: configuration #1 chosen from 1 choice
[    6.630155] scsi 0:0:0:0: Attached scsi generic sg0 type 0
[    6.630293] scsi 1:0:0:0: Attached scsi generic sg1 type 5
[    6.630421] scsi 1:0:1:0: Attached scsi generic sg2 type 5
[    6.718674] usbcore: registered new interface driver libusual
[    6.753589] Initializing USB Mass Storage driver...
[    6.781083] scsi2 : SCSI emulation for USB Mass Storage devices
[    6.784990] Driver 'sd' needs updating - please use bus_type methods
[    6.786844] sd 0:0:0:0: [sda] 39102336 512-byte hardware sectors (20020 MB)
[    6.786897] sd 0:0:0:0: [sda] Write Protect is off
[    6.786904] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    6.786980] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.787208] sd 0:0:0:0: [sda] 39102336 512-byte hardware sectors (20020 MB)
[    6.787252] sd 0:0:0:0: [sda] Write Protect is off
[    6.787257] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    6.787329] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.787340]  sda:<6>usbcore: registered new interface driver usb-storage
[    6.800167] USB Mass Storage support registered.
[    6.800188] usb-storage: device found at 2
[    6.800192] usb-storage: waiting for device to settle before scanning
[    6.805921]  sda1 sda2 < sda5 >
[    6.825085] sd 0:0:0:0: [sda] Attached SCSI disk
[    6.876255] Driver 'sr' needs updating - please use bus_type methods
[    6.880134] sr0: scsi3-mmc drive: 0x/32x writer cd/rw xa/form2 cdda tray
[    6.880147] Uniform CD-ROM driver Revision: 3.20
[    6.880405] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    6.887097] sr1: scsi3-mmc drive: 4x/48x cd/rw xa/form2 cdda tray
[    6.887371] sr 1:0:1:0: Attached scsi CD-ROM sr1
[    7.377115] PM: Starting manual resume from disk
[    7.377128] PM: Resume from partition 8:5
[    7.377131] PM: Checking hibernation image.
[    7.377564] PM: Resume from disk failed.
[    7.432705] EXT3-fs: INFO: recovery required on readonly filesystem.
[    7.432715] EXT3-fs: write access will be enabled during recovery.
[    9.425715] kjournald starting.  Commit interval 5 seconds
[    9.425765] EXT3-fs: sda1: orphan cleanup on readonly fs
[    9.425779] ext3_orphan_cleanup: deleting unreferenced inode 434572
[    9.425904] ext3_orphan_cleanup: deleting unreferenced inode 737229
[    9.731224] ext3_orphan_cleanup: deleting unreferenced inode 737230
[    9.741484] ext3_orphan_cleanup: deleting unreferenced inode 687494
[    9.741528] ext3_orphan_cleanup: deleting unreferenced inode 687495
[    9.741552] ext3_orphan_cleanup: deleting unreferenced inode 656920
[    9.762924] EXT3-fs: sda1: 6 orphan inodes deleted
[    9.762931] EXT3-fs: recovery complete.
[    9.773365] EXT3-fs: mounted filesystem with ordered data mode.
[   11.801869] usb-storage: device scan complete
[   11.804820] scsi 2:0:0:0: Direct-Access     EPSON    Stylus Storage   1.00 PQ: 0 ANSI: 2
[   11.811093] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[   11.811418] sd 2:0:0:0: Attached scsi generic sg3 type 0
[   16.037726] udevd version 124 started
[   17.040869] Linux agpgart interface v0.103
[   17.124842] agpgart-intel 0000:00:00.0: Intel 845G Chipset
[   17.133174] agpgart-intel 0000:00:00.0: AGP aperture is 64M @ 0xec000000
[   17.182243] intel_rng: Firmware space is locked read-only. If you can't or
[   17.182248] intel_rng: don't want to disable this in firmware setup, and if
[   17.182250] intel_rng: you are certain that your system has a functional
[   17.182253] intel_rng: RNG, try using the 'no_fwh_detect' option.
[   17.255881] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   17.354245] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   17.484455] iTCO_vendor_support: vendor-support=0
[   17.563960] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.03 (30-Apr-2008)
[   17.572707] iTCO_wdt: Found a ICH2 TCO device (Version=1, TCOBASE=0xf860)
[   17.573105] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   17.973892] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[   17.987561] ACPI: Power Button (FF) [PWRF]
[   17.987914] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input3
[   18.002861] ACPI: Power Button (CM) [PBTN]
[   18.800271] acx: Loaded combined PCI/USB driver, firmware_ver=default
[   18.800279] acx: compiled to use 32bit I/O access. I/O timing issues might occur, such as non-working firmware upload. Report them
[   18.800364] acx_pci 0000:02:09.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   18.800402] acx: found ACX111-based wireless network card at 0000:02:09.0, irq:18, phymem1:0xF8420000, phymem2:0xF8400000, mem1:0xe8890000, mem1_size:8192, mem2:0xe8a80000, mem2_size:131072
[   18.801440] acx: loading firmware for acx1111 chipset with radio ID 16
[   18.801449] firmware: requesting acx/1.2.1.34/tiacx111c16
[   19.281587] input: PC Speaker as /devices/platform/pcspkr/input/input4
[   19.960392] parport_pc 00:07: reported by Plug and Play ACPI
[   19.960457] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   21.163826] usblp0: USB Bidirectional printer dev 2 if 1 alt 0 proto 2 vid 0x04B8 pid 0x0838
[   21.163899] usbcore: registered new interface driver usblp
[   21.165293] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input5
[   21.393094] Bluetooth: Core ver 2.13
[   21.394803] NET: Registered protocol family 31
[   21.394810] Bluetooth: HCI device and connection manager initialized
[   21.394817] Bluetooth: HCI socket layer initialized
[   21.603218] Bluetooth: Generic Bluetooth USB driver ver 0.3
[   21.605034] usbcore: registered new interface driver btusb
[   26.244549] NVS_vendor_offs:01CD probe_delay:200 eof_memory:1114112
[   26.244561] CCAModes:04 Diversity:01 ShortPreOpt:01 PBCC:01 ChanAgil:00 PHY:05 Temp:01
[   26.244570] AntennaID:00 Len:02 Data:01 02 
[   26.244579] PowerLevelID:01 Len:02 Data:001E 000A 
[   26.244589] DataRatesID:02 Len:05 Data:02 04 11 22 44 
[   26.244602] DomainID:03 Len:06 Data:30 20 30 31 32 40 
[   26.244616] ProductID:04 Len:09 Data:TI ACX100
[   26.244623] ManufacturerID:05 Len:07 Data:TI Test
[   26.304033] acx: === chipset TNETW1130, radio type 0x16 (Radia), form factor 0x01 ((mini-)PCI / CardBus), EEPROM version 0x05: uploaded firmware 'Rev 1.2.1.34' ===
[   26.305366] acx v0.3.36: net device wlan0, driver compiled against wireless extensions 22 and Linux 2.6.27-9-generic
[   26.306667] Intel ICH 0000:00:1f.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   26.306705] Intel ICH 0000:00:1f.5: setting latency timer to 64
[   26.307039] usbcore: registered new interface driver acx_usb
[   26.928027] intel8x0_measure_ac97_clock: measured 55914 usecs
[   26.928035] intel8x0: clocking to 41159
[   27.988347] lp0: using parport0 (interrupt-driven).
[   28.299888] Adding 859436k swap on /dev/sda5.  Priority:-1 extents:1 across:859436k
[   28.949099] EXT3 FS on sda1, internal journal
[   30.252849] type=1505 audit(1230670285.487:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=3868
[   30.605911] type=1505 audit(1230670285.839:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=3873
[   30.606856] type=1505 audit(1230670285.839:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=3873
[   30.814208] ip_tables: (C) 2000-2006 Netfilter Core Team
[   31.812391] ACPI: WMI: Mapper loaded
[   33.695676] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   33.776131] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   33.776148] apm: overridden by ACPI.
[   33.967362] ppdev: user-space parallel port driver
[   36.774312] Bluetooth: L2CAP ver 2.11
[   36.774327] Bluetooth: L2CAP socket layer initialized
[   36.890761] Bluetooth: RFCOMM socket layer initialized
[   36.891374] Bluetooth: RFCOMM TTY layer initialized
[   36.891396] Bluetooth: RFCOMM ver 1.10
[   36.932478] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   36.932496] Bluetooth: BNEP filters: protocol multicast
[   37.090039] Bridge firewalling registered
[   37.091999] pan0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature.
[   37.178811] Bluetooth: SCO (Voice Link) ver 0.6
[   37.178826] Bluetooth: SCO socket layer initialized
[   41.440160] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[   42.060875] NET: Registered protocol family 17
[   62.192044] wlan0: issue_cmd(): timed out waiting for CMD_COMPLETE. irq bits:0x0000 irq_status:0x0000 timeout:49ms cmd_status:1 (Success)
[   62.192061] wlan0: issue_cmd(cmd:0x0002) FAILED
[   62.192069] Pid: 4798, comm: wpa_supplicant Not tainted 2.6.27-9-generic #1
[   62.192077]  [<c037c4b6>] ? printk+0x1d/0x1f
[   62.192119]  [<e8a36749>] acxpci_s_issue_cmd_timeo+0x269/0x3b0 [acx]
[   62.192165]  [<e8a30599>] acx_s_configure+0x99/0xc0 [acx]
[   62.192183]  [<e8a32217>] acx_s_update_card_settings+0x5f7/0x1110 [acx]
[   62.192199]  [<c012a571>] ? hrtick_start_fair+0x181/0x1a0
[   62.192211]  [<c012ad2d>] ? check_preempt_wakeup+0x14d/0x1b0
[   62.192219]  [<c012b4ee>] ? try_to_wake_up+0xde/0x290
[   62.192226]  [<c030ec2d>] ? __nla_put+0x1d/0x50
[   62.192237]  [<c03694cf>] ? wireless_send_event+0x15f/0x230
[   62.192246]  [<c03694cf>] ? wireless_send_event+0x15f/0x230
[   62.192253]  [<c014c0f0>] ? up+0x30/0x50
[   62.192262]  [<c0369d37>] ? ioctl_standard_iw_point+0x127/0x290
[   62.192270]  [<c0369d37>] ? ioctl_standard_iw_point+0x127/0x290
[   62.192280]  [<e8a2cfd6>] acx_ioctl_commit+0x26/0x40 [acx]
[   62.192295]  [<e8a2cfb0>] ? acx_ioctl_commit+0x0/0x40 [acx]
[   62.192308]  [<c0369f5c>] ioctl_standard_call+0xbc/0x110
[   62.192315]  [<c02f2485>] ? __dev_get_by_name+0x85/0xb0
[   62.192325]  [<c03697ce>] wireless_process_ioctl+0xbe/0x150
[   62.192333]  [<e8a2ca50>] ? acx_ioctl_set_encode+0x0/0x1a0 [acx]
[   62.192347]  [<c037d4e0>] ? mutex_lock+0x10/0x20
[   62.192354]  [<c03698d0>] wext_handle_ioctl+0x70/0xe0
[   62.192360]  [<c0369ea0>] ? ioctl_standard_call+0x0/0x110
[   62.192367]  [<c0369a90>] ? ioctl_private_call+0x0/0x180
[   62.192373]  [<c02f45df>] dev_ioctl+0x45f/0x520
[   62.192380]  [<c01954b0>] ? unmap_vmas+0x1a0/0x360
[   62.192389]  [<c037e6dd>] ? _spin_lock+0xd/0x10
[   62.192396]  [<c0199434>] ? unlink_file_vma+0x14/0xa0
[   62.192404]  [<c02e4b50>] ? sock_ioctl+0x0/0x250
[   62.192414]  [<c02e4c45>] sock_ioctl+0xf5/0x250
[   62.192420]  [<c02e4b50>] ? sock_ioctl+0x0/0x250
[   62.192427]  [<c01bee9d>] vfs_ioctl+0x2d/0x90
[   62.192436]  [<c01bf086>] do_vfs_ioctl+0x66/0x1f0
[   62.192441]  [<c02147d8>] ? cap_file_ioctl+0x8/0x10
[   62.192452]  [<c01bf27b>] sys_ioctl+0x6b/0x70
[   62.192458]  [<c0103f7b>] sysenter_do_call+0x12/0x2f
[   62.192466]  =======================
[   62.192470] wlan0: configure(type:0x1010) FAILED
[   77.536034] wlan0: issue_cmd(): timed out waiting for CMD_COMPLETE. irq bits:0x0000 irq_status:0x0000 timeout:49ms cmd_status:1 (Success)
[   77.536051] wlan0: issue_cmd(cmd:0x0002) FAILED
[   77.536058] Pid: 4798, comm: wpa_supplicant Not tainted 2.6.27-9-generic #1
[   77.536066]  [<c037c4b6>] ? printk+0x1d/0x1f
[   77.536108]  [<e8a36749>] acxpci_s_issue_cmd_timeo+0x269/0x3b0 [acx]
[   77.536155]  [<e8a30599>] acx_s_configure+0x99/0xc0 [acx]
[   77.536173]  [<e8a32217>] acx_s_update_card_settings+0x5f7/0x1110 [acx]
[   77.536189]  [<c02eae1c>] ? skb_put+0xc/0xa0
[   77.536201]  [<c018a053>] ? get_page_from_freelist+0xc3/0x160
[   77.536212]  [<c030ebc6>] ? __nla_reserve+0x26/0x70
[   77.536222]  [<c030ec2d>] ? __nla_put+0x1d/0x50
[   77.536228]  [<c030ecaf>] ? nla_put+0x4f/0x60
[   77.536234]  [<c03694cf>] ? wireless_send_event+0x15f/0x230
[   77.536244]  [<c03694cf>] ? wireless_send_event+0x15f/0x230
[   77.536251]  [<c014c0f0>] ? up+0x30/0x50
[   77.536261]  [<c0369d37>] ? ioctl_standard_iw_point+0x127/0x290
[   77.536268]  [<c0369d37>] ? ioctl_standard_iw_point+0x127/0x290
[   77.536279]  [<e8a2cfd6>] acx_ioctl_commit+0x26/0x40 [acx]
[   77.536294]  [<e8a2cfb0>] ? acx_ioctl_commit+0x0/0x40 [acx]
[   77.536307]  [<c0369f5c>] ioctl_standard_call+0xbc/0x110
[   77.536314]  [<c02f2485>] ? __dev_get_by_name+0x85/0xb0
[   77.536322]  [<c03697ce>] wireless_process_ioctl+0xbe/0x150
[   77.536331]  [<e8a2ca50>] ? acx_ioctl_set_encode+0x0/0x1a0 [acx]
[   77.536346]  [<c037d4e0>] ? mutex_lock+0x10/0x20
[   77.536353]  [<c03698d0>] wext_handle_ioctl+0x70/0xe0
[   77.536360]  [<c0369ea0>] ? ioctl_standard_call+0x0/0x110
[   77.536366]  [<c0369a90>] ? ioctl_private_call+0x0/0x180
[   77.536373]  [<c02f45df>] dev_ioctl+0x45f/0x520
[   77.536380]  [<c01954b0>] ? unmap_vmas+0x1a0/0x360
[   77.536387]  [<c037e6dd>] ? _spin_lock+0xd/0x10
[   77.536395]  [<c0199434>] ? unlink_file_vma+0x14/0xa0
[   77.536402]  [<c02e4b50>] ? sock_ioctl+0x0/0x250
[   77.536412]  [<c02e4c45>] sock_ioctl+0xf5/0x250
[   77.536418]  [<c02e4b50>] ? sock_ioctl+0x0/0x250
[   77.536425]  [<c01bee9d>] vfs_ioctl+0x2d/0x90
[   77.536435]  [<c01bf086>] do_vfs_ioctl+0x66/0x1f0
[   77.536441]  [<c02147d8>] ? cap_file_ioctl+0x8/0x10
[   77.536452]  [<c01bf27b>] sys_ioctl+0x6b/0x70
[   77.536458]  [<c0103f7b>] sysenter_do_call+0x12/0x2f
[   77.536467]  =======================
[   77.536472] wlan0: configure(type:0x1010) FAILED
rickcoyle@rickcoyle-desktop:~$

---

### Post by mrwaistcoat on 2008-12-30
Also noticed this - any comments ?  What is the swap memory ?  I do have two memory rams - should I replace with one ? Why is this swap memory totally unused? 

             total       used       free     shared    buffers     cached
Mem:        643752     489160     154592          0      23244     226904
-/+ buffers/cache:     239012     404740
Swap:       859436          0     859436

---

### Post by pdtpatrick on 2008-12-30
you shouldnt worry about swap memory .. swap memory is like virtual memory in windows. It's memory borrowed from your harddrive and the OS will use when it needs to :) 

Anyway you can google it for more information but its safe to say that in this case, you needn't worry about it as its not a message saying to swap your memory :)

---

