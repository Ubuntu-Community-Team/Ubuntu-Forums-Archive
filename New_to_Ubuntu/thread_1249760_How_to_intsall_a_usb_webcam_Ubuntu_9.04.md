---
title: "How to intsall a usb webcam Ubuntu 9.04?"
date: 2009-08-25
forum: New to Ubuntu
---

### Post by aierlan on 2009-08-25
Hi I'm using ubuntu 9.04 and have an ANC U690V webcam but I can't get it to work.  I've tried using cheese but as soon as it opens it closes again by itself.  
Any help in beginner's lingo is much appreciated

---

### Post by infurnus on 2009-08-25
What is the make/model and output from lsusb and dmesg?

[https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)

Also have you checked the webcam help?

lsusb
Bus 001 Device 007: ID 046d:092f Logitech, Inc. QuickCam Express Plus

This is my cheapo Logitech QuickCam - some work out of the box and some do not. You need to find if yours is supported out of the box or if you need to install additional drivers etc.

---

### Post by aierlan on 2009-08-26
I'll have to figure out how to do that

---

### Post by aierlan on 2009-08-26
Ok, gotta run those commands in a terminal - slowly learning.

The camera's make and model is ANC U690V Vista

The output from lsusb is:

Bus 001 Device 005: ID 067b:2506 Prolific Technology, Inc. 
Bus 001 Device 007: ID 0458:003a KYE Systems Corp. (Mouse Systems) 
Bus 001 Device 006: ID 046d:c309 Logitech, Inc. Internet Keyboard
Bus 001 Device 004: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 003: ID 0c45:62f0 Microdia 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 1604:8007 Tascam US-122 Audio/Midi Interface
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


And from dmesg:  this is a long one 

[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2605.814 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] allocated 5201280 bytes of page_cgroup
[    0.004000] please try cgroup_disable=memory option if you don't want
[    0.004000] Scanning for low memory corruption every 60 seconds
[    0.004000] Memory: 1010324k/1040320k available (4115k kernel code, 29172k reserved, 2199k data, 532k init, 135112k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xf7bfe000 - 0xff3fe000   ( 120 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xf73fe000   ( 883 MB)
[    0.004000]       .init : 0xc0733000 - 0xc07b8000   ( 532 kB)
[    0.004000]       .data : 0xc0504f5f - 0xc072ae60   (2199 kB)
[    0.004000]       .text : 0xc0100000 - 0xc0504f5f   (4115 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] SLUB: Genslabs=12, HWalign=128, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.004015] Calibrating delay loop (skipped), value calculated using timer frequency.. 5211.62 BogoMIPS (lpj=10423256)
[    0.004039] Security Framework initialized
[    0.004053] SELinux:  Disabled at boot.
[    0.004079] AppArmor: AppArmor initialized
[    0.004095] Mount-cache hash table entries: 512
[    0.004289] Initializing cgroup subsys ns
[    0.004295] Initializing cgroup subsys cpuacct
[    0.004299] Initializing cgroup subsys memory
[    0.004305] Initializing cgroup subsys freezer
[    0.004325] CPU: Trace cache: 12K uops, L1 D cache: 8K
[    0.004329] CPU: L2 cache: 512K
[    0.004334] CPU: Physical Processor ID: 0
[    0.004338] CPU: Processor Core ID: 0
[    0.004355] Checking 'hlt' instruction... OK.
[    0.023246] ACPI: Core revision 20080926
[    0.025907] ACPI: Checking initramfs for custom DSDT
[    0.352559] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.392305] CPU0: Intel(R) Pentium(R) 4 CPU 2.60GHz stepping 09
[    0.396001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 5212.20 BogoMIPS (lpj=10424417)
[    0.004000] CPU: Trace cache: 12K uops, L1 D cache: 8K
[    0.004000] CPU: L2 cache: 512K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 0
[    0.480291] CPU1: Intel(R) Pentium(R) 4 CPU 2.60GHz stepping 09
[    0.480317] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.484073] Brought up 2 CPUs
[    0.484078] Total of 2 processors activated (10423.83 BogoMIPS).
[    0.484131] CPU0 attaching sched-domain:
[    0.484135]  domain 0: span 0-1 level SIBLING
[    0.484139]   groups: 0 1
[    0.484149] CPU1 attaching sched-domain:
[    0.484152]  domain 0: span 0-1 level SIBLING
[    0.484155]   groups: 1 0
[    0.484255] net_namespace: 776 bytes
[    0.484265] Booting paravirtualized kernel on bare hardware
[    0.484528] Time: 10:36:10  Date: 08/26/09
[    0.484528] regulator: core version 0.5
[    0.484528] NET: Registered protocol family 16
[    0.484528] EISA bus registered
[    0.484528] ACPI: bus type pci registered
[    0.509528] PCI: PCI BIOS revision 2.10 entry at 0xfb4f0, last bus=1
[    0.509532] PCI: Using configuration type 1 for base access
[    0.512156] ACPI: EC: Look up EC in DSDT
[    0.519282] ACPI: Interpreter enabled
[    0.519288] ACPI: (supports S0 S1 S4 S5)
[    0.519316] ACPI: Using IOAPIC for interrupt routing
[    0.525198] ACPI: No dock devices found.
[    0.525215] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.525279] pci 0000:00:00.0: reg 10 32bit mmio: [0xf0000000-0xf3ffffff]
[    0.525344] pci 0000:00:02.0: reg 10 32bit mmio: [0xe8000000-0xefffffff]
[    0.525352] pci 0000:00:02.0: reg 14 32bit mmio: [0xf6000000-0xf607ffff]
[    0.525359] pci 0000:00:02.0: reg 18 io port: [0xb000-0xb007]
[    0.525458] pci 0000:00:1d.0: reg 20 io port: [0xa000-0xa01f]
[    0.525514] pci 0000:00:1d.1: reg 20 io port: [0xa400-0xa41f]
[    0.525572] pci 0000:00:1d.2: reg 20 io port: [0xa800-0xa81f]
[    0.525627] pci 0000:00:1d.3: reg 20 io port: [0xac00-0xac1f]
[    0.525682] pci 0000:00:1d.7: reg 10 32bit mmio: [0xf6080000-0xf60803ff]
[    0.525730] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.525736] pci 0000:00:1d.7: PME# disabled
[    0.525826] pci 0000:00:1f.0: Force enabled HPET at 0xfed00000
[    0.525833] pci 0000:00:1f.0: quirk: region 0400-047f claimed by ICH4 ACPI/GPIO/TCO
[    0.525839] pci 0000:00:1f.0: quirk: region 0480-04bf claimed by ICH4 GPIO
[    0.525863] pci 0000:00:1f.1: reg 10 io port: [0x00-0x07]
[    0.525871] pci 0000:00:1f.1: reg 14 io port: [0x00-0x03]
[    0.525879] pci 0000:00:1f.1: reg 18 io port: [0x00-0x07]
[    0.525887] pci 0000:00:1f.1: reg 1c io port: [0x00-0x03]
[    0.525895] pci 0000:00:1f.1: reg 20 io port: [0xf000-0xf00f]
[    0.525903] pci 0000:00:1f.1: reg 24 32bit mmio: [0x000000-0x0003ff]
[    0.525956] pci 0000:00:1f.3: reg 20 io port: [0x500-0x51f]
[    0.526002] pci 0000:00:1f.5: reg 10 io port: [0xb800-0xb8ff]
[    0.526009] pci 0000:00:1f.5: reg 14 io port: [0xbc00-0xbc3f]
[    0.526017] pci 0000:00:1f.5: reg 18 32bit mmio: [0xf6081000-0xf60811ff]
[    0.526025] pci 0000:00:1f.5: reg 1c 32bit mmio: [0xf6082000-0xf60820ff]
[    0.526050] pci 0000:00:1f.5: PME# supported from D0 D3hot D3cold
[    0.526055] pci 0000:00:1f.5: PME# disabled
[    0.526105] pci 0000:01:06.0: reg 10 io port: [0x9000-0x90ff]
[    0.526113] pci 0000:01:06.0: reg 14 32bit mmio: [0xf5005000-0xf50050ff]
[    0.526140] pci 0000:01:06.0: reg 30 32bit mmio: [0x000000-0x00ffff]
[    0.526151] pci 0000:01:06.0: supports D1 D2
[    0.526154] pci 0000:01:06.0: PME# supported from D1 D2 D3hot D3cold
[    0.526159] pci 0000:01:06.0: PME# disabled
[    0.526192] pci 0000:01:07.0: reg 10 io port: [0x9400-0x943f]
[    0.526231] pci 0000:01:07.0: supports D1 D2
[    0.526264] pci 0000:01:07.1: reg 10 io port: [0x9800-0x9807]
[    0.526303] pci 0000:01:07.1: supports D1 D2
[    0.526338] pci 0000:01:07.2: reg 10 32bit mmio: [0xf5004000-0xf50047ff]
[    0.526346] pci 0000:01:07.2: reg 14 32bit mmio: [0xf5000000-0xf5003fff]
[    0.526382] pci 0000:01:07.2: supports D1 D2
[    0.526385] pci 0000:01:07.2: PME# supported from D0 D1 D2 D3hot
[    0.526390] pci 0000:01:07.2: PME# disabled
[    0.526431] pci 0000:01:08.0: reg 10 32bit mmio: [0xf5006000-0xf50067ff]
[    0.526439] pci 0000:01:08.0: reg 14 io port: [0x9c00-0x9c7f]
[    0.526475] pci 0000:01:08.0: supports D2
[    0.526477] pci 0000:01:08.0: PME# supported from D2 D3hot D3cold
[    0.526482] pci 0000:01:08.0: PME# disabled
[    0.526518] pci 0000:00:1e.0: transparent bridge
[    0.526524] pci 0000:00:1e.0: bridge io port: [0x9000-0x9fff]
[    0.526530] pci 0000:00:1e.0: bridge 32bit mmio: [0xf4000000-0xf5ffffff]
[    0.526542] bus 00 -> node 0
[    0.526552] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.526785] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[    0.534772] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 *10 11 12 14 15)
[    0.534928] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 7 9 10 11 12 14 15)
[    0.535084] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[    0.535239] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 10 11 *12 14 15)
[    0.535395] ACPI: PCI Interrupt Link [LNKE] (IRQs *3 4 5 7 9 10 11 12 14 15)
[    0.535549] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[    0.535707] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[    0.535864] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 7 *9 10 11 12 14 15)
[    0.536074] ACPI: WMI: Mapper loaded
[    0.536182] SCSI subsystem initialized
[    0.536212] libata version 3.00 loaded.
[    0.536212] usbcore: registered new interface driver usbfs
[    0.536212] usbcore: registered new interface driver hub
[    0.536212] usbcore: registered new device driver usb
[    0.536212] PCI: Using ACPI for IRQ routing
[    0.544015] Bluetooth: Core ver 2.13
[    0.544045] NET: Registered protocol family 31
[    0.544045] Bluetooth: HCI device and connection manager initialized
[    0.544045] Bluetooth: HCI socket layer initialized
[    0.544045] NET: Registered protocol family 8
[    0.544045] NET: Registered protocol family 20
[    0.544056] NetLabel: Initializing
[    0.544059] NetLabel:  domain hash size = 128
[    0.544061] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.544085] NetLabel:  unlabeled traffic allowed by default
[    0.544201] hpet clockevent registered
[    0.544206] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.544212] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.544220] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.548111] AppArmor: AppArmor Filesystem Enabled
[    0.556015] pnp: PnP ACPI init
[    0.556032] ACPI: bus type pnp registered
[    0.560180] pnp: PnP ACPI: found 12 devices
[    0.560183] ACPI: ACPI bus type pnp unregistered
[    0.560189] PnPBIOS: Disabled by ACPI PNP
[    0.560203] system 00:01: ioport range 0x4d0-0x4d1 has been reserved
[    0.560207] system 00:01: ioport range 0x290-0x29f has been reserved
[    0.560211] system 00:01: ioport range 0x800-0x805 has been reserved
[    0.560223] system 00:09: ioport range 0x400-0x4bf could not be reserved
[    0.560233] system 00:0b: iomem range 0xca600-0xcbfff has been reserved
[    0.560237] system 00:0b: iomem range 0xf0000-0xf7fff could not be reserved
[    0.560241] system 00:0b: iomem range 0xf8000-0xfbfff could not be reserved
[    0.560245] system 00:0b: iomem range 0xfc000-0xfffff could not be reserved
[    0.560249] system 00:0b: iomem range 0x3f7f0000-0x3f7fffff could not be reserved
[    0.560253] system 00:0b: iomem range 0x0-0x9ffff could not be reserved
[    0.560257] system 00:0b: iomem range 0x100000-0x3f7effff could not be reserved
[    0.560261] system 00:0b: iomem range 0xfec00000-0xfec00fff has been reserved
[    0.560265] system 00:0b: iomem range 0xfec01000-0xfed8ffff has been reserved
[    0.560269] system 00:0b: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.560272] system 00:0b: iomem range 0xffb00000-0xffb7ffff has been reserved
[    0.560276] system 00:0b: iomem range 0xfff00000-0xffffffff has been reserved
[    0.560280] system 00:0b: iomem range 0xe0000-0xeffff has been reserved
[    0.595060] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:01
[    0.595065] pci 0000:00:1e.0:   IO window: 0x9000-0x9fff
[    0.595071] pci 0000:00:1e.0:   MEM window: 0xf4000000-0xf5ffffff
[    0.595077] pci 0000:00:1e.0:   PREFETCH window: 0x00000040000000-0x000000400fffff
[    0.595093] pci 0000:00:1e.0: setting latency timer to 64
[    0.595099] bus: 00 index 0 io port: [0x00-0xffff]
[    0.595102] bus: 00 index 1 mmio: [0x000000-0xffffffff]
[    0.595105] bus: 01 index 0 io port: [0x9000-0x9fff]
[    0.595109] bus: 01 index 1 mmio: [0xf4000000-0xf5ffffff]
[    0.595112] bus: 01 index 2 mmio: [0x40000000-0x400fffff]
[    0.595115] bus: 01 index 3 io port: [0x00-0xffff]
[    0.595118] bus: 01 index 4 mmio: [0x000000-0xffffffff]
[    0.595130] NET: Registered protocol family 2
[    0.608089] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.608521] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.609232] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.609876] TCP: Hash tables configured (established 131072 bind 65536)
[    0.609880] TCP reno registered
[    0.616144] NET: Registered protocol family 1
[    0.616326] checking if image is initramfs... it is
[    1.044440] Switched to high resolution mode on CPU 1
[    1.048051] Switched to high resolution mode on CPU 0
[    1.293325] Freeing initrd memory: 7364k freed
[    1.293403] cpufreq: No nForce2 chipset.
[    1.293595] audit: initializing netlink socket (disabled)
[    1.293617] type=2000 audit(1251282970.293:1): initialized
[    1.300758] highmem bounce pool size: 64 pages
[    1.300767] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.302565] VFS: Disk quotas dquot_6.5.1
[    1.302660] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.303550] fuse init (API version 7.10)
[    1.303672] msgmni has been set to 1724
[    1.304175] alg: No test for stdrng (krng)
[    1.304201] io scheduler noop registered
[    1.304206] io scheduler anticipatory registered
[    1.304212] io scheduler deadline registered
[    1.304246] io scheduler cfq registered (default)
[    1.304266] pci 0000:00:02.0: Boot video device
[    1.308270] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.308285] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.308472] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.308476] ACPI: Power Button (FF) [PWRF]
[    1.308539] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    1.308543] ACPI: Power Button (CM) [PWRB]
[    1.308620] fan PNP0C0B:00: registered as cooling_device0
[    1.308629] ACPI: Fan [FAN] (on)
[    1.308901] processor ACPI_CPU:00: registered as cooling_device1
[    1.308958] processor ACPI_CPU:01: registered as cooling_device2
[    1.311929] thermal LNXTHERM:01: registered as thermal_zone0
[    1.312289] ACPI: Thermal Zone [THRM] (35 C)
[    1.312365] isapnp: Scanning for PnP cards...
[    1.666103] isapnp: No Plug & Play device found
[    1.676201] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.676295] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.676699] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.677833] brd: module loaded
[    1.678313] loop: module loaded
[    1.678432] Fixed MDIO Bus: probed
[    1.678441] PPP generic driver version 2.4.2
[    1.678535] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    1.678585] Driver 'sd' needs updating - please use bus_type methods
[    1.678601] Driver 'sr' needs updating - please use bus_type methods
[    1.678710] ata_piix 0000:00:1f.1: version 2.12
[    1.678733] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.678798] ata_piix 0000:00:1f.1: setting latency timer to 64
[    1.678945] scsi0 : ata_piix
[    1.679106] scsi1 : ata_piix
[    1.680222] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[    1.680226] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[    1.844429] ata1.00: ATAPI: SONY    DVD RW DW-U14A, 1.0c, max UDMA/33
[    1.860376] ata1.00: configured for UDMA/33
[    2.032584] ata2.00: ATA-6: HDS722580VLAT20, V32OA60A, max UDMA/100
[    2.032588] ata2.00: 160836480 sectors, multi 16: LBA48 
[    2.056532] ata2.00: configured for UDMA/100
[    2.058111] scsi 0:0:0:0: CD-ROM            SONY     DVD RW DW-U14A   1.0c PQ: 0 ANSI: 5
[    2.061908] sr0: scsi3-mmc drive: 32x/32x writer cd/rw xa/form2 cdda tray
[    2.061913] Uniform CD-ROM driver Revision: 3.20
[    2.062073] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    2.062145] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    2.062246] scsi 1:0:0:0: Direct-Access     ATA      HDS722580VLAT20  V32O PQ: 0 ANSI: 5
[    2.062385] sd 1:0:0:0: [sda] 160836480 512-byte hardware sectors: (82.3 GB/76.6 GiB)
[    2.062410] sd 1:0:0:0: [sda] Write Protect is off
[    2.062414] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.062454] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.062537] sd 1:0:0:0: [sda] 160836480 512-byte hardware sectors: (82.3 GB/76.6 GiB)
[    2.062559] sd 1:0:0:0: [sda] Write Protect is off
[    2.062562] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.062601] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.062607]  sda: sda1 sda2 < sda5 >
[    2.095593] sd 1:0:0:0: [sda] Attached SCSI disk
[    2.095661] sd 1:0:0:0: Attached scsi generic sg1 type 0
[    2.096664] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.096702] ehci_hcd 0000:00:1d.7: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    2.096735] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    2.096740] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    2.096838] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    2.100753] ehci_hcd 0000:00:1d.7: cache line size of 128 is not supported
[    2.100772] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xf6080000
[    2.116014] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    2.116126] usb usb1: configuration #1 chosen from 1 choice
[    2.116166] hub 1-0:1.0: USB hub found
[    2.116177] hub 1-0:1.0: 8 ports detected
[    2.116349] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.116378] uhci_hcd: USB Universal Host Controller Interface driver
[    2.116430] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.116441] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    2.116445] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    2.116515] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    2.116547] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000a000
[    2.116645] usb usb2: configuration #1 chosen from 1 choice
[    2.116682] hub 2-0:1.0: USB hub found
[    2.116695] hub 2-0:1.0: 2 ports detected
[    2.116818] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    2.116827] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    2.116831] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    2.116893] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    2.116924] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000a400
[    2.117030] usb usb3: configuration #1 chosen from 1 choice
[    2.117065] hub 3-0:1.0: USB hub found
[    2.117077] hub 3-0:1.0: 2 ports detected
[    2.117192] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    2.117201] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    2.117205] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    2.117286] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    2.117317] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000a800
[    2.117423] usb usb4: configuration #1 chosen from 1 choice
[    2.117459] hub 4-0:1.0: USB hub found
[    2.117471] hub 4-0:1.0: 2 ports detected
[    2.117587] uhci_hcd 0000:00:1d.3: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.117595] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    2.117599] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    2.117668] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    2.117691] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000ac00
[    2.117797] usb usb5: configuration #1 chosen from 1 choice
[    2.117835] hub 5-0:1.0: USB hub found
[    2.117847] hub 5-0:1.0: 2 ports detected
[    2.118048] PNP: No PS/2 controller found. Probing ports directly.
[    2.368396] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.372067] mice: PS/2 mouse device common for all mice
[    2.384114] rtc_cmos 00:03: RTC can wake from S4
[    2.384168] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    2.384195] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
[    2.384301] device-mapper: uevent: version 1.0.3
[    2.384450] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: [email]dm-devel@redhat.com[/email]
[    2.384581] device-mapper: multipath: version 1.0.5 loaded
[    2.384588] device-mapper: multipath round-robin: version 1.0.0 loaded
[    2.384722] EISA: Probing bus 0 at eisa.0
[    2.384772] EISA: Detected 0 cards.
[    2.384858] cpuidle: using governor ladder
[    2.384864] cpuidle: using governor menu
[    2.385691] TCP cubic registered
[    2.385789] NET: Registered protocol family 10
[    2.386441] lo: Disabled Privacy Extensions
[    2.386972] NET: Registered protocol family 17
[    2.387003] Bluetooth: L2CAP ver 2.11
[    2.387006] Bluetooth: L2CAP socket layer initialized
[    2.387011] Bluetooth: SCO (Voice Link) ver 0.6
[    2.387014] Bluetooth: SCO socket layer initialized
[    2.387084] Bluetooth: RFCOMM socket layer initialized
[    2.387100] Bluetooth: RFCOMM TTY layer initialized
[    2.387104] Bluetooth: RFCOMM ver 1.10
[    2.387187] Using IPI No-Shortcut mode
[    2.387325] registered taskstats version 1
[    2.387493]   Magic number: 5:606:629
[    2.387596] rtc_cmos 00:03: setting system clock to 2009-08-26 10:36:12 UTC (1251282972)
[    2.387600] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.387603] EDD information not available.
[    2.388164] Freeing unused kernel memory: 532k freed
[    2.388384] Write protecting the kernel text: 4116k
[    2.388462] Write protecting the kernel read-only data: 1528k
[    2.541059] usb 1-5: new high speed USB device using ehci_hcd and address 3
[    2.714431] usb 1-5: configuration #1 chosen from 1 choice
[    2.762027] Floppy drive(s): fd0 is 1.44M
[    2.783854] FDC 0 is a post-1991 82077
[    2.828105] usb 1-6: new high speed USB device using ehci_hcd and address 4
[    2.965581] usb 1-6: configuration #1 chosen from 1 choice
[    2.965896] hub 1-6:1.0: USB hub found
[    2.966200] hub 1-6:1.0: 4 ports detected
[    2.968538] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    2.968593] 8139cp 0000:01:06.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
[    2.973175] 8139too Fast Ethernet driver 0.9.28
[    2.973255] 8139too 0000:01:06.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    2.975442] eth0: RealTek RTL8139 at 0x9000, 00:30:1b:b0:4e:44, IRQ 18
[    2.975446] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[    3.019276] ohci1394 0000:01:07.2: PCI INT B -> GSI 20 (level, low) -> IRQ 20
[    3.075430] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[20]  MMIO=[f5004000-f50047ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    3.085140] ohci1394 0000:01:08.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    3.138076] ohci1394: fw-host1: OHCI-1394 1.0 (PCI): IRQ=[20]  MMIO=[f5006000-f50067ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    3.208245] usb 3-2: new full speed USB device using uhci_hcd and address 2
[    3.362046] usb 3-2: configuration #1 chosen from 1 choice
[    3.440444] usb 1-6.1: new high speed USB device using ehci_hcd and address 5
[    3.545400] PM: Starting manual resume from disk
[    3.545406] PM: Resume from partition 8:5
[    3.545409] PM: Checking hibernation image.
[    3.545595] PM: Resume from disk failed.
[    3.572565] kjournald starting.  Commit interval 5 seconds
[    3.572583] EXT3-fs: mounted filesystem with ordered data mode.
[    3.658627] usb 1-6.1: configuration #1 chosen from 1 choice
[    3.728379] usb 1-6.2: new low speed USB device using ehci_hcd and address 6
[    3.828968] usb 1-6.2: configuration #1 chosen from 1 choice
[    3.900341] usb 1-6.3: new low speed USB device using ehci_hcd and address 7
[    3.996077] usb 1-6.3: configuration #1 chosen from 1 choice
[    4.356187] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00023c01410048d0]
[    4.424173] ieee1394: Host added: ID:BUS[1-00:1023]  GUID[00301bb000004ea8]
[    9.074863] udev: starting version 141
[    9.819572] Initializing USB Mass Storage driver...
[    9.827002] scsi2 : SCSI emulation for USB Mass Storage devices
[    9.829746] usbcore: registered new interface driver usb-storage
[    9.829828] USB Mass Storage support registered.
[    9.829838] usb-storage: device found at 5
[    9.829842] usb-storage: waiting for device to settle before scanning
[    9.989029] parport_pc 00:08: reported by Plug and Play ACPI
[    9.989086] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   10.014400] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   10.029079] usbcore: registered new interface driver hiddev
[   10.034128] input: Logitech Logitech USB Keyboard as /devices/pci0000:00/0000:00:1d.7/usb1/1-6/1-6.2/1-6.2:1.0/input/input3
[   10.035378] input: PC Speaker as /devices/platform/pcspkr/input/input4
[   10.058896] generic-usb 0003:046D:C309.0001: input,hidraw0: USB HID v1.10 Keyboard [Logitech Logitech USB Keyboard] on usb-0000:00:1d.7-6.2/input0
[   10.063875] Linux video capture interface: v2.00
[   10.073597] input: Logitech Logitech USB Keyboard as /devices/pci0000:00/0000:00:1d.7/usb1/1-6/1-6.2/1-6.2:1.1/input/input5
[   10.082079] generic-usb 0003:046D:C309.0002: input,hidraw1: USB HID v1.10 Mouse [Logitech Logitech USB Keyboard] on usb-0000:00:1d.7-6.2/input1
[   10.085190] input: Genius Optical Mouse as /devices/pci0000:00/0000:00:1d.7/usb1/1-6/1-6.3/1-6.3:1.0/input/input6
[   10.119698] generic-usb 0003:0458:003A.0003: input,hidraw2: USB HID v1.10 Mouse [Genius Optical Mouse] on usb-0000:00:1d.7-6.3/input0
[   10.119750] usbcore: registered new interface driver usbhid
[   10.119809] usbhid: v2.6:USB HID core driver
[   10.186553] Linux agpgart interface v0.103
[   10.220367] agpgart-intel 0000:00:00.0: Intel 865 Chipset
[   10.221015] agpgart-intel 0000:00:00.0: detected 8060K stolen memory
[   10.223147] agpgart-intel 0000:00:00.0: AGP aperture is 128M @ 0xe8000000
[   10.252525] intel_rng: FWH not detected
[   10.288587] ppdev: user-space parallel port driver
[   10.417267] uvcvideo: Found UVC 1.00 device USB 2.0 Camera (0c45:62f0)
[   10.420065] input: USB 2.0 Camera as /devices/pci0000:00/0000:00:1d.7/usb1/1-5/1-5:1.0/input/input7
[   10.434346] usbcore: registered new interface driver uvcvideo
[   10.434413] USB Video Class driver (v0.1.0)
[   10.539322] iTCO_vendor_support: vendor-support=0
[   10.544393] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05
[   10.544698] iTCO_wdt: Found a ICH5 or ICH5R TCO device (Version=1, TCOBASE=0x0460)
[   10.544944] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   10.571037] gameport: EMU10K1 is pci0000:01:07.1/gameport0, io 0x9800, speed 1217kHz
[   10.688259] usbcore: registered new interface driver snd-usb-usx2y
[   10.735550] Intel ICH 0000:00:1f.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   10.735751] Intel ICH 0000:00:1f.5: setting latency timer to 64
[   10.788817] EMU10K1_Audigy 0000:01:07.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   10.794329] Installing spdif_bug patch: Audigy 2 ZS [2001]
[   10.808443] Control name 'Sigmatel Surround Phase Inversion Playback Switch' truncated to 'Sigmatel Surround Phase Inversion Playback '
[   11.056341] intel8x0_measure_ac97_clock: measured 52698 usecs
[   11.056348] intel8x0: clocking to 48000
[   13.416886] lp0: using parport0 (interrupt-driven).
[   13.591061] Adding 2980016k swap on /dev/sda5.  Priority:-1 extents:1 across:2980016k
[   14.158028] EXT3 FS on sda1, internal journal
[   14.828259] usb-storage: device scan complete
[   14.863567] scsi 2:0:0:0: Direct-Access     HTC42603 0G5CE00          00P9 PQ: 0 ANSI: 0
[   14.864958] sd 2:0:0:0: [sdb] 58605120 512-byte hardware sectors: (30.0 GB/27.9 GiB)
[   14.865803] sd 2:0:0:0: [sdb] Write Protect is off
[   14.865808] sd 2:0:0:0: [sdb] Mode Sense: 03 00 00 00
[   14.865812] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[   14.866720] sd 2:0:0:0: [sdb] 58605120 512-byte hardware sectors: (30.0 GB/27.9 GiB)
[   14.867570] sd 2:0:0:0: [sdb] Write Protect is off
[   14.867577] sd 2:0:0:0: [sdb] Mode Sense: 03 00 00 00
[   14.867582] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[   14.867592]  sdb: sdb1 sdb2 < sdb5 >
[   15.109201] sd 2:0:0:0: [sdb] Attached SCSI disk
[   15.109405] sd 2:0:0:0: Attached scsi generic sg2 type 0
[   15.572816] type=1505 audit(1251282985.684:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2320
[   15.640410] type=1505 audit(1251282985.749:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2324
[   15.640628] type=1505 audit(1251282985.749:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2324
[   15.640699] type=1505 audit(1251282985.749:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2324
[   15.640753] type=1505 audit(1251282985.749:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2324
[   15.805854] type=1505 audit(1251282985.917:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2329
[   15.806137] type=1505 audit(1251282985.917:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2329
[   15.845815] type=1505 audit(1251282985.957:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2333
[   19.633285] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   19.633290] Bluetooth: BNEP filters: protocol multicast
[   19.654072] Bridge firewalling registered
[   24.888537] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[   35.173022] eth0: no IPv6 routers present


Thanks again

---

### Post by SunnyRabbiera on 2009-08-26
Its a good possibility that your current webcam wont work with Ubuntu, depending on the brand/ model.
I am unsure on ANC and rather if they are able to work with linux or not.
But dont despair, if you cant get it to work save up for a good decent logitech.
Logitech webcams have a very high rate of linux compatibility.

But to further confirm your issue give wxCam a shot:
[http://www.getdeb.net/app/wxCam](http://www.getdeb.net/app/wxCam)

---

### Post by aierlan on 2009-08-26
its working now with wxcam thanks 

hopefully this means it will work with aMSN

---

### Post by Jose Catre-Vandis on 2009-08-26
Have a look here:

[http://groups.google.com/group/microdia?pli=1](http://groups.google.com/group/microdia?pli=1)

---

### Post by SunnyRabbiera on 2009-08-26
> **aierlan said:**
> its working now with wxcam thanks 

hopefully this means it will work with aMSN

Yeh who knows, some webcams are the devil with linux

---

