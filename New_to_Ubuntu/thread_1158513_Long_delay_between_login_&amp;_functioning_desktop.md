---
title: "Long delay between login &amp; functioning desktop"
date: 2009-05-13
forum: New to Ubuntu
---

### Post by suitedaces on 2009-05-13
Jaunty Jackalope on HP G6062ea 2gb 1.6ghz.

Basically, there's on average a 60 second delay with a blank screen (except for white at top and bottom)and the spinning mouse circle, then a further 45 second delay for all the icons to appear and the desktop to become functional.

I'm not blaming Ubuntu for this, as it was super-fast after I installed it, so I know it's something I've done myself. Thing is, I cannot figure out what it is, and I'm wondering is there a less drastic fix than a re-install.

---

### Post by coffeeaddict22 on 2009-05-13
Not sure if it'll be your problem, but I've got a 3GB Core2 laptop that did the same, and slowed right up opening any window.  Turned out the ATI proprietary driver was the problem, and it sped up again when I went back to the open sourced one.
Suggest you have a look at the output of ```
dmesg
``` and also scan through /var/log/messages just after booting up to see if you can spot it.  If it's just a booting up issue another option would be to install bootchart (System/Administration/Synaptic Package Manager, search for bootchart) and use that to find what's causing the slowdown.

---

### Post by suitedaces on 2009-05-14
Edit, I've just timed it and was shocked. From entering password, I have about 20 seconds of black screen with ordinary mouse, then 40 seconds of white top and bottom with the spinning circle, followed by an inactive desktop wothout all the icons for another 44 seconds. I must have really underestimated the times when making my first post.

---

### Post by suitedaces on 2009-05-14
dmseg:
```
[    0.524062] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 31
[    0.524067] hpet0: 3 comparators, 32-bit 25.000000 MHz counter
[    0.528081] AppArmor: AppArmor Filesystem Enabled
[    0.536022] Switched to high resolution mode on CPU 0
[    0.536034] Switched to high resolution mode on CPU 1
[    0.536049] pnp: PnP ACPI init
[    0.536061] ACPI: bus type pnp registered
[    0.540079] pnp: PnP ACPI: found 12 devices
[    0.540081] ACPI: ACPI bus type pnp unregistered
[    0.540085] PnPBIOS: Disabled by ACPI PNP
[    0.540098] system 00:02: iomem range 0xe0000000-0xefffffff has been reserved
[    0.540105] system 00:03: ioport range 0x1000-0x107f has been reserved
[    0.540108] system 00:03: ioport range 0x1080-0x10ff has been reserved
[    0.540111] system 00:03: ioport range 0x1400-0x147f has been reserved
[    0.540114] system 00:03: ioport range 0x1480-0x14ff has been reserved
[    0.540116] system 00:03: ioport range 0x1800-0x187f has been reserved
[    0.540119] system 00:03: ioport range 0x1880-0x18ff has been reserved
[    0.540125] system 00:04: ioport range 0x360-0x361 has been reserved
[    0.540128] system 00:04: ioport range 0x4d0-0x4d1 has been reserved
[    0.540137] system 00:0b: iomem range 0xffc00000-0xffffffff could not be reserved
[    0.540140] system 00:0b: iomem range 0xfec00000-0xfec00fff has been reserved
[    0.540143] system 00:0b: iomem range 0xfee00000-0xfeefffff could not be reserved
[    0.540146] system 00:0b: iomem range 0xfed00000-0xfed00fff has been reserved
[    0.540149] system 00:0b: iomem range 0xfef00000-0xfef00fff has been reserved
[    0.574871] pci 0000:00:08.0: PCI bridge, secondary bus 0000:02
[    0.574873] pci 0000:00:08.0:   IO window: disabled
[    0.574877] pci 0000:00:08.0:   MEM window: disabled
[    0.574879] pci 0000:00:08.0:   PREFETCH window: disabled
[    0.574884] pci 0000:00:0c.0: PCI bridge, secondary bus 0000:04
[    0.574886] pci 0000:00:0c.0:   IO window: 0x4000-0x4fff
[    0.574890] pci 0000:00:0c.0:   MEM window: 0xf2000000-0xf3ffffff
[    0.574893] pci 0000:00:0c.0:   PREFETCH window: 0x000000f0000000-0x000000f1ffffff
[    0.574897] pci 0000:00:0d.0: PCI bridge, secondary bus 0000:03
[    0.574899] pci 0000:00:0d.0:   IO window: disabled
[    0.574902] pci 0000:00:0d.0:   MEM window: 0xf6000000-0xf60fffff
[    0.574905] pci 0000:00:0d.0:   PREFETCH window: disabled
[    0.574913] pci 0000:00:08.0: setting latency timer to 64
[    0.574918] pci 0000:00:0c.0: setting latency timer to 64
[    0.574923] pci 0000:00:0d.0: setting latency timer to 64
[    0.574926] bus: 00 index 0 io port: [0x00-0xffff]
[    0.574929] bus: 00 index 1 mmio: [0x000000-0xffffffff]
[    0.574931] bus: 02 index 0 mmio: [0x0-0x0]
[    0.574933] bus: 02 index 1 mmio: [0x0-0x0]
[    0.574935] bus: 02 index 2 mmio: [0x0-0x0]
[    0.574937] bus: 02 index 3 io port: [0x00-0xffff]
[    0.574939] bus: 02 index 4 mmio: [0x000000-0xffffffff]
[    0.574941] bus: 04 index 0 io port: [0x4000-0x4fff]
[    0.574943] bus: 04 index 1 mmio: [0xf2000000-0xf3ffffff]
[    0.574945] bus: 04 index 2 mmio: [0xf0000000-0xf1ffffff]
[    0.574947] bus: 04 index 3 mmio: [0x0-0x0]
[    0.574949] bus: 03 index 0 mmio: [0x0-0x0]
[    0.574952] bus: 03 index 1 mmio: [0xf6000000-0xf60fffff]
[    0.574954] bus: 03 index 2 mmio: [0x0-0x0]
[    0.574956] bus: 03 index 3 mmio: [0x0-0x0]
[    0.574968] NET: Registered protocol family 2
[    0.585075] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.585358] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.585966] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.586271] TCP: Hash tables configured (established 131072 bind 65536)
[    0.586274] TCP reno registered
[    0.589098] NET: Registered protocol family 1
[    0.589225] checking if image is initramfs... it is
[    1.232182] Freeing initrd memory: 7808k freed
[    1.232213] Simple Boot Flag at 0x36 set to 0x1
[    1.232384] cpufreq: No nForce2 chipset.
[    1.232506] audit: initializing netlink socket (disabled)
[    1.232519] type=2000 audit(1242285858.232:1): initialized
[    1.240830] highmem bounce pool size: 64 pages
[    1.240836] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.242138] VFS: Disk quotas dquot_6.5.1
[    1.242201] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.242841] fuse init (API version 7.10)
[    1.242927] msgmni has been set to 1699
[    1.243131] alg: No test for stdrng (krng)
[    1.243144] io scheduler noop registered
[    1.243146] io scheduler anticipatory registered
[    1.243148] io scheduler deadline registered
[    1.243164] io scheduler cfq registered (default)
[    1.243196] pci 0000:00:00.0: Enabling HT MSI Mapping
[    1.243371] pci 0000:00:07.0: Enabling HT MSI Mapping
[    1.243386] pci 0000:00:08.0: Enabling HT MSI Mapping
[    1.243403] pci 0000:00:09.0: Enabling HT MSI Mapping
[    1.243419] pci 0000:00:0a.0: Enabling HT MSI Mapping
[    1.243435] pci 0000:00:0c.0: Enabling HT MSI Mapping
[    1.243451] pci 0000:00:0d.0: Enabling HT MSI Mapping
[    1.243466] pci 0000:00:12.0: Boot video device
[    1.249346] pcieport-driver 0000:00:0c.0: setting latency timer to 64
[    1.249371] pcieport-driver 0000:00:0c.0: found MSI capability
[    1.249389] pcieport-driver 0000:00:0c.0: irq 2303 for MSI/MSI-X
[    1.249396] pci_express 0000:00:0c.0:pcie00: allocate port service
[    1.249411] pci_express 0000:00:0c.0:pcie03: allocate port service
[    1.249447] pcieport-driver 0000:00:0d.0: setting latency timer to 64
[    1.249471] pcieport-driver 0000:00:0d.0: found MSI capability
[    1.249484] pcieport-driver 0000:00:0d.0: irq 2302 for MSI/MSI-X
[    1.249491] pci_express 0000:00:0d.0:pcie00: allocate port service
[    1.249503] pci_express 0000:00:0d.0:pcie03: allocate port service
[    1.249550] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.249562] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.251152] ACPI: AC Adapter [ACAD] (off-line)
[    1.529701] ACPI: Battery Slot [BAT0] (battery present)
[    1.529782] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.529785] ACPI: Power Button (FF) [PWRF]
[    1.529827] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1
[    1.529830] ACPI: Sleep Button (CM) [SLPB]
[    1.529875] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input2
[    1.531377] ACPI: Lid Switch [LID]
[    1.531448] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input3
[    1.531451] ACPI: Power Button (CM) [PWRB]
[    1.531782] ACPI: processor limited to max C-state 1
[    1.531811] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    1.531842] processor ACPI_CPU:00: registered as cooling_device0
[    1.531847] ACPI: Processor [CPU0] (supports 8 throttling states)
[    1.531928] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    1.531950] processor ACPI_CPU:01: registered as cooling_device1
[    1.531954] ACPI: Processor [CPU1] (supports 8 throttling states)
[    1.795724] ACPI Exception (thermal-0377): AE_OK, No or invalid critical threshold [20080926]
[    1.795783] isapnp: Scanning for PnP cards...
[    2.148364] isapnp: No Plug & Play device found
[    2.161283] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    2.162253] brd: module loaded
[    2.162558] loop: module loaded
[    2.162636] Fixed MDIO Bus: probed
[    2.162642] PPP generic driver version 2.4.2
[    2.162704] input: Macintosh mouse button emulation as /devices/virtual/input/input4
[    2.162739] Driver 'sd' needs updating - please use bus_type methods
[    2.162748] Driver 'sr' needs updating - please use bus_type methods
[    2.162795] ahci 0000:00:09.0: version 3.0
[    2.163171] ACPI: PCI Interrupt Link [LSI0] enabled at IRQ 23
[    2.163182] ahci 0000:00:09.0: PCI INT A -> Link[LSI0] -> GSI 23 (level, low) -> IRQ 23
[    2.163228] ahci 0000:00:09.0: irq 2301 for MSI/MSI-X
[    2.163290] ahci 0000:00:09.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl IDE mode
[    2.163293] ahci 0000:00:09.0: flags: 64bit sntf led clo pmp pio slum part 
[    2.163297] ahci 0000:00:09.0: setting latency timer to 64
[    2.163728] scsi0 : ahci
[    2.163854] scsi1 : ahci
[    2.163943] scsi2 : ahci
[    2.164046] scsi3 : ahci
[    2.164149] ata1: SATA max UDMA/133 abar m8192@0xf6384000 port 0xf6384100 irq 2301
[    2.164152] ata2: SATA max UDMA/133 abar m8192@0xf6384000 port 0xf6384180 irq 2301
[    2.164155] ata3: SATA max UDMA/133 abar m8192@0xf6384000 port 0xf6384200 irq 2301
[    2.164158] ata4: SATA max UDMA/133 abar m8192@0xf6384000 port 0xf6384280 irq 2301
[    2.648033] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.648411] ata1.00: ATA-8: FUJITSU MHY2120BH, 890B, max UDMA/100
[    2.648414] ata1.00: 234441648 sectors, multi 16: LBA48 
[    2.648925] ata1.00: configured for UDMA/100
[    2.968032] ata2: SATA link down (SStatus 0 SControl 300)
[    3.288028] ata3: SATA link down (SStatus 0 SControl 300)
[    3.608026] ata4: SATA link down (SStatus 0 SControl 300)
[    3.608127] scsi 0:0:0:0: Direct-Access     ATA      FUJITSU MHY2120B 890B PQ: 0 ANSI: 5
[    3.608219] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors: (120 GB/111 GiB)
[    3.608236] sd 0:0:0:0: [sda] Write Protect is off
[    3.608239] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.608264] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.608334] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors: (120 GB/111 GiB)
[    3.608349] sd 0:0:0:0: [sda] Write Protect is off
[    3.608351] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.608376] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.608380]  sda: sda1 sda2 sda3 < sda5 sda6 >
[    3.682480] sd 0:0:0:0: [sda] Attached SCSI disk
[    3.682534] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    3.682760] pata_amd 0000:00:06.0: version 0.3.10
[    3.682803] pata_amd 0000:00:06.0: setting latency timer to 64
[    3.682899] scsi4 : pata_amd
[    3.682994] scsi5 : pata_amd
[    3.683351] ata5: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x30c0 irq 14
[    3.683354] ata6: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x30c8 irq 15
[    3.844310] ata5.00: ATAPI: HL-DT-ST DVDRAM GSA-T20L, NC08, max MWDMA2
[    3.844334] ata5: nv_mode_filter: 0x39f&0x39f->0x39f, BIOS=0x0 (0xc600) ACPI=0x39f (120:600:0x12)
[    3.860256] ata5.00: configured for MWDMA2
[    3.862538] ata6: port disabled. ignoring.
[    3.865591] scsi 4:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-T20L  NC08 PQ: 0 ANSI: 5
[    3.876434] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    3.876437] Uniform CD-ROM driver Revision: 3.20
[    3.876551] sr 4:0:0:0: Attached scsi CD-ROM sr0
[    3.876595] sr 4:0:0:0: Attached scsi generic sg1 type 5
[    3.877134] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    3.877516] ACPI: PCI Interrupt Link [LUS2] enabled at IRQ 22
[    3.877527] ehci_hcd 0000:00:02.1: PCI INT B -> Link[LUS2] -> GSI 22 (level, low) -> IRQ 22
[    3.877547] ehci_hcd 0000:00:02.1: setting latency timer to 64
[    3.877550] ehci_hcd 0000:00:02.1: EHCI Host Controller
[    3.877609] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 1
[    3.877636] ehci_hcd 0000:00:02.1: debug port 1
[    3.877640] ehci_hcd 0000:00:02.1: cache line size of 64 is not supported
[    3.877661] ehci_hcd 0000:00:02.1: irq 22, io mem 0xf6389000
[    3.888032] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00
[    3.888102] usb usb1: configuration #1 chosen from 1 choice
[    3.888128] hub 1-0:1.0: USB hub found
[    3.888136] hub 1-0:1.0: 7 ports detected
[    3.888573] ACPI: PCI Interrupt Link [Z015] enabled at IRQ 22
[    3.888577] ehci_hcd 0000:00:04.1: PCI INT B -> Link[Z015] -> GSI 22 (level, low) -> IRQ 22
[    3.888591] ehci_hcd 0000:00:04.1: setting latency timer to 64
[    3.888593] ehci_hcd 0000:00:04.1: EHCI Host Controller
[    3.888636] ehci_hcd 0000:00:04.1: new USB bus registered, assigned bus number 2
[    3.888660] ehci_hcd 0000:00:04.1: debug port 1
[    3.888664] ehci_hcd 0000:00:04.1: cache line size of 64 is not supported
[    3.888669] ehci_hcd 0000:00:04.1: irq 22, io mem 0xf6389400
[    3.900032] ehci_hcd 0000:00:04.1: USB 2.0 started, EHCI 1.00
[    3.900089] usb usb2: configuration #1 chosen from 1 choice
[    3.900113] hub 2-0:1.0: USB hub found
[    3.900120] hub 2-0:1.0: 2 ports detected
[    3.900211] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    3.900562] ACPI: PCI Interrupt Link [LUS0] enabled at IRQ 18
[    3.900571] ohci_hcd 0000:00:02.0: PCI INT A -> Link[LUS0] -> GSI 18 (level, low) -> IRQ 18
[    3.900584] ohci_hcd 0000:00:02.0: setting latency timer to 64
[    3.900587] ohci_hcd 0000:00:02.0: OHCI Host Controller
[    3.900631] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 3
[    3.900655] ohci_hcd 0000:00:02.0: irq 18, io mem 0xf6386000
[    3.958073] usb usb3: configuration #1 chosen from 1 choice
[    3.958100] hub 3-0:1.0: USB hub found
[    3.958108] hub 3-0:1.0: 7 ports detected
[    3.958517] ACPI: PCI Interrupt Link [Z014] enabled at IRQ 18
[    3.958521] ohci_hcd 0000:00:04.0: PCI INT A -> Link[Z014] -> GSI 18 (level, low) -> IRQ 18
[    3.958532] ohci_hcd 0000:00:04.0: setting latency timer to 64
[    3.958535] ohci_hcd 0000:00:04.0: OHCI Host Controller
[    3.958585] ohci_hcd 0000:00:04.0: new USB bus registered, assigned bus number 4
[    3.958596] ohci_hcd 0000:00:04.0: irq 18, io mem 0xf6387000
[    4.014064] usb usb4: configuration #1 chosen from 1 choice
[    4.014089] hub 4-0:1.0: USB hub found
[    4.014097] hub 4-0:1.0: 2 ports detected
[    4.014184] uhci_hcd: USB Universal Host Controller Interface driver
[    4.014275] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[    4.040983] serio: i8042 KBD port at 0x60,0x64 irq 1
[    4.040993] serio: i8042 AUX port at 0x60,0x64 irq 12
[    4.044056] mice: PS/2 mouse device common for all mice
[    4.065096] rtc_cmos 00:07: RTC can wake from S4
[    4.065129] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
[    4.065168] rtc0: alarms up to one year, y3k, 114 bytes nvram, hpet irqs
[    4.065234] device-mapper: uevent: version 1.0.3
[    4.065348] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
[    4.065516] device-mapper: multipath: version 1.0.5 loaded
[    4.065519] device-mapper: multipath round-robin: version 1.0.0 loaded
[    4.065631] EISA: Probing bus 0 at eisa.0
[    4.065637] Cannot allocate resource for EISA slot 1
[    4.065642] Cannot allocate resource for EISA slot 3
[    4.065645] Cannot allocate resource for EISA slot 4
[    4.065657] EISA: Detected 0 cards.
[    4.065804] cpuidle: using governor ladder
[    4.065866] cpuidle: using governor menu
[    4.066371] TCP cubic registered
[    4.066477] NET: Registered protocol family 10
[    4.066874] lo: Disabled Privacy Extensions
[    4.067184] NET: Registered protocol family 17
[    4.067202] Bluetooth: L2CAP ver 2.11
[    4.067204] Bluetooth: L2CAP socket layer initialized
[    4.067206] Bluetooth: SCO (Voice Link) ver 0.6
[    4.067208] Bluetooth: SCO socket layer initialized
[    4.067265] Bluetooth: RFCOMM socket layer initialized
[    4.067272] Bluetooth: RFCOMM TTY layer initialized
[    4.067273] Bluetooth: RFCOMM ver 1.10
[    4.067328] powernow-k8: Found 1 AMD Athlon(tm) 64 X2 Dual-Core Processor TK-57 processors (2 cpu cores) (version 2.20.00)
[    4.067380] powernow-k8:    0 : fid 0xb (1900 MHz), vid 0x12
[    4.067383] powernow-k8:    1 : fid 0xa (1800 MHz), vid 0x13
[    4.067385] powernow-k8:    2 : fid 0x8 (1600 MHz), vid 0x14
[    4.067387] powernow-k8:    3 : fid 0x0 (800 MHz), vid 0x1a
[    4.067438] Using IPI No-Shortcut mode
[    4.067524] registered taskstats version 1
[    4.067655]   Magic number: 9:160:420
[    4.067754] rtc_cmos 00:07: setting system clock to 2009-05-14 07:24:21 UTC (1242285861)
[    4.067757] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    4.067759] EDD information not available.
[    4.068138] Freeing unused kernel memory: 532k freed
[    4.068303] Write protecting the kernel text: 4112k
[    4.068359] Write protecting the kernel read-only data: 1524k
[    4.099336] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[    4.276027] usb 1-2: new high speed USB device using ehci_hcd and address 2
[   45.471013] usb 1-2: configuration #1 chosen from 1 choice
[   45.471338] hub 1-2:1.0: USB hub found
[   45.471679] hub 1-2:1.0: 4 ports detected
[   45.516939] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
[   45.517426] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 20
[   45.517443] forcedeth 0000:00:0a.0: PCI INT A -> Link[LMAC] -> GSI 20 (level, low) -> IRQ 20
[   45.517449] forcedeth 0000:00:0a.0: setting latency timer to 64
[   45.641035] usb 2-2: new high speed USB device using ehci_hcd and address 2
[   45.869270] usb 2-2: configuration #1 chosen from 1 choice
[   46.044686] forcedeth 0000:00:0a.0: ifname eth0, PHY OUI 0x732 @ 1, addr 00:1e:68:21:23:41
[   46.044691] forcedeth 0000:00:0a.0: highdma pwrctl mgmt timirq lnktim msi desc-v3
[   46.065766] usb 3-4: new low speed USB device using ohci_hcd and address 2
[   46.285276] PM: Starting manual resume from disk
[   46.285281] PM: Resume from partition 8:6
[   46.285283] PM: Checking hibernation image.
[   46.285476] PM: Resume from disk failed.
[   46.321360] usb 3-4: configuration #1 chosen from 1 choice
[   46.322836] kjournald starting.  Commit interval 5 seconds
[   46.322861] EXT3-fs: mounted filesystem with ordered data mode.
[   53.792654] udev: starting version 141
[   74.177853] Clocksource tsc unstable (delta = 4398046039209 ns)
[   74.189337] acpi device:25: registered as cooling_device2
[   74.189533] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:23/input/input6
[   74.217183] ACPI: Video Device [UVGA] (multi-head: yes  rom: no  post: no)
[   74.939436] usbcore: registered new interface driver hiddev
[   74.939504] usbcore: registered new interface driver usbhid
[   74.939507] usbhid: v2.6:USB HID core driver
[   74.942512] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[   75.108675] cfg80211: Calling CRDA to update world regulatory domain
[   75.179495] cfg80211: World regulatory domain updated:
[   75.179500] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   75.179503] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   75.179506] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   75.179508] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   75.179511] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   75.179513] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   75.983904] Linux agpgart interface v0.103
[   75.994443] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x1a0b1, caps: 0xa04713/0x200000
[   76.043430] input: USB Optical Mouse USB Optical Mouse as /devices/pci0000:00/0000:00:02.0/usb3/3-4/3-4:1.0/input/input7
[   76.056127] a4tech 0003:09DA:0006.0001: input,hidraw0: USB HID v1.10 Mouse [USB Optical Mouse USB Optical Mouse] on usb-0000:00:02.0-4/input0
[   76.076343] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input8
[   76.389679] Linux video capture interface: v2.00
[   76.964081] nvidia: module license 'NVIDIA' taints kernel.
[   77.218662] ACPI: PCI Interrupt Link [LGPU] enabled at IRQ 16
[   77.218676] nvidia 0000:00:12.0: PCI INT A -> Link[LGPU] -> GSI 16 (level, low) -> IRQ 16
[   77.218682] nvidia 0000:00:12.0: setting latency timer to 64
[   77.220045] NVRM: loading NVIDIA UNIX x86 Kernel Module  173.14.16  Sat Jan 24 19:42:59 PST 2009
[   77.264805] ACPI: PCI Interrupt Link [LK4E] enabled at IRQ 19
[   77.264819] ath5k_pci 0000:03:00.0: PCI INT A -> Link[LK4E] -> GSI 19 (level, low) -> IRQ 19
[   77.264828] ath5k_pci 0000:03:00.0: setting latency timer to 64
[   77.264889] ath5k_pci 0000:03:00.0: registered as 'phy0'
[   77.305489] phy0: Selected rate control algorithm 'pid'
[   77.322305] ip_tables: (C) 2000-2006 Netfilter Core Team
[   77.371522] uvcvideo: Found UVC 1.00 device Webcam-101 (064e:a102)
[   77.373190] input: Webcam-101 as /devices/pci0000:00/0000:00:04.1/usb2/2-2/2-2:1.0/input/input9
[   77.375190] usbcore: registered new interface driver uvcvideo
[   77.375194] USB Video Class driver (v0.1.0)
[   77.505340] ath5k phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
[   77.539539] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[   77.539762] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Please use
[   77.539764] nf_conntrack.acct=1 kernel paramater, acct=1 nf_conntrack module option or
[   77.539767] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
[   77.759883] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 21
[   77.759897] HDA Intel 0000:00:07.0: PCI INT A -> Link[LAZA] -> GSI 21 (level, low) -> IRQ 21
[   77.760009] HDA Intel 0000:00:07.0: setting latency timer to 64
[   78.432633] lp: driver loaded but no devices found
[   78.599497] Adding 1951856k swap on /dev/sda6.  Priority:-1 extents:1 across:1951856k
[   78.628746] EXT3 FS on sda5, internal journal
[   79.185472] type=1505 audit(1242282336.616:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2157
[   79.242323] type=1505 audit(1242282336.673:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2161
[   79.242470] type=1505 audit(1242282336.673:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2161
[   79.242523] type=1505 audit(1242282336.673:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2161
[   79.242570] type=1505 audit(1242282336.673:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2161
[   79.293186] type=1505 audit(1242282336.724:7): operation="profile_load" name="/usr/bin/freshclam" name2="default" pid=2166
[   79.455997] type=1505 audit(1242282336.884:8): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2170
[   79.456197] type=1505 audit(1242282336.888:9): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2170
[   79.488923] type=1505 audit(1242282336.920:10): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2174
[   83.733687] kvm: disabled by bios
[  103.137131] Bridge firewalling registered
[  103.175305] virbr0: starting userspace STP failed, starting kernel STP
[  104.670436] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[  104.670440] vboxdrv: Successfully done.
[  104.670442] vboxdrv: Found 2 processor cores.
[  104.670509] vboxdrv: fAsync=1 offMin=0xd52ef offMax=0xd52ef
[  104.670567] vboxdrv: TSC mode is 'asynchronous', kernel timer mode is 'normal'.
[  104.670570] vboxdrv: Successfully loaded version 2.1.4_OSE (interface 0x000a0009).
[  106.665132] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[  106.665135] Bluetooth: BNEP filters: protocol multicast
[  108.465403] ppdev: user-space parallel port driver
[  137.874943] forcedeth 0000:00:0a.0: irq 2300 for MSI/MSI-X
[  137.875171] eth0: no link during initialization.
[  137.875674] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  137.904665] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  138.873010] virbr0: no IPv6 routers present
[  162.238221] padlock: VIA PadLock not detected.
[  197.331861] wlan0: authenticate with AP 00:1c:df:3b:50:7d
[  197.334797] wlan0: authenticated
[  197.334801] wlan0: associate with AP 00:1c:df:3b:50:7d
[  197.344416] wlan0: RX AssocResp from 00:1c:df:3b:50:7d (capab=0x431 status=0 aid=3)
[  197.344419] wlan0: associated
[  197.344709] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  207.372043] wlan0: no IPv6 routers present
[  240.773380] Unknown OutputIN= OUT=virbr0 SRC=192.168.122.1 DST=239.255.255.250 LEN=332 TOS=0x00 PREC=0x00 TTL=4 ID=0 DF PROTO=UDP SPT=1900 DPT=1900 LEN=312 
[  240.773496] Unknown OutputIN= OUT=virbr0 SRC=192.168.122.1 DST=239.255.255.250 LEN=323 TOS=0x00 PREC=0x00 TTL=4 ID=0 DF PROTO=UDP SPT=1900 DPT=1900 LEN=303 
[  240.773600] Unknown OutputIN= OUT=virbr0 SRC=192.168.122.1 DST=239.255.255.250 LEN=375 TOS=0x00 PREC=0x00 TTL=4 ID=0 DF PROTO=UDP SPT=1900 DPT=1900 LEN=355 
[  240.773697] Unknown OutputIN= OUT=virbr0 SRC=192.168.122.1 DST=239.255.255.250 LEN=387 TOS=0x00 PREC=0x00 TTL=4 ID=0 DF PROTO=UDP SPT=1900 DPT=1900 LEN=367 
[  240.773795] Unknown OutputIN= OUT=virbr0 SRC=192.168.122.1 DST=239.255.255.250 LEN=389 TOS=0x00 PREC=0x00 TTL=4 ID=0 DF PROTO=UDP SPT=1900 DPT=1900 LEN=369 
[  302.115840] Unknown OutputIN= OUT=virbr0 SRC=192.168.122.1 DST=239.255.255.250 LEN=332 TOS=0x00 PREC=0x00 TTL=4 ID=0 DF PROTO=UDP SPT=1900 DPT=1900 LEN=312 
[  302.115953] Unknown OutputIN= OUT=virbr0 SRC=192.168.122.1 DST=239.255.255.250 LEN=323 TOS=0x00 PREC=0x00 TTL=4 ID=0 DF PROTO=UDP SPT=1900 DPT=1900 LEN=303 
[  302.116055] Unknown OutputIN= OUT=virbr0 SRC=192.168.122.1 DST=239.255.255.250 LEN=375 TOS=0x00 PREC=0x00 TTL=4 ID=0 DF PROTO=UDP SPT=1900 DPT=1900 LEN=355 
[  302.116154] Unknown OutputIN= OUT=virbr0 SRC=192.168.122.1 DST=239.255.255.250 LEN=387 TOS=0x00 PREC=0x00 TTL=4 ID=0 DF PROTO=UDP SPT=1900 DPT=1900 LEN=367 
[  302.116252] Unknown OutputIN= OUT=virbr0 SRC=192.168.122.1 DST=239.255.255.250 LEN=389 TOS=0x00 PREC=0x00 TTL=4 ID=0 DF PROTO=UDP SPT=1900 DPT=1900 LEN=369 
[  363.322235] Unknown OutputIN= OUT=virbr0 SRC=192.168.122.1 DST=239.255.255.250 LEN=332 TOS=0x00 PREC=0x00 TTL=4 ID=0 DF PROTO=UDP SPT=1900 DPT=1900 LEN=312 
[  363.322355] Unknown OutputIN= OUT=virbr0 SRC=192.168.122.1 DST=239.255.255.250 LEN=323 TOS=0x00 PREC=0x00 TTL=4 ID=0 DF PROTO=UDP SPT=1900 DPT=1900 LEN=303 
[  363.322460] Unknown OutputIN= OUT=virbr0 SRC=192.168.122.1 DST=239.255.255.250 LEN=375 TOS=0x00 PREC=0x00 TTL=4 ID=0 DF PROTO=UDP SPT=1900 DPT=1900 LEN=355 
[  363.322561] Unknown OutputIN= OUT=virbr0 SRC=192.168.122.1 DST=239.255.255.250 LEN=387 TOS=0x00 PREC=0x00 TTL=4 ID=0 DF PROTO=UDP SPT=1900 DPT=1900 LEN=367 
[  363.322659] Unknown OutputIN= OUT=virbr0 SRC=192.168.122.1 DST=239.255.255.250 LEN=389 TOS=0x00 PREC=0x00 TTL=4 ID=0 DF PROTO=UDP SPT=1900 DPT=1900 LEN=369 
[  424.307033] Unknown OutputIN= OUT=virbr0 SRC=192.168.122.1 DST=239.255.255.250 LEN=332 TOS=0x00 PREC=0x00 TTL=4 ID=0 DF PROTO=UDP SPT=1900 DPT=1900 LEN=312 
[  424.307157] Unknown OutputIN= OUT=virbr0 SRC=192.168.122.1 DST=239.255.255.250 LEN=323 TOS=0x00 PREC=0x00 TTL=4 ID=0 DF PROTO=UDP SPT=1900 DPT=1900 LEN=303 
[  424.307262] Unknown OutputIN= OUT=virbr0 SRC=192.168.122.1 DST=239.255.255.250 LEN=375 TOS=0x00 PREC=0x00 TTL=4 ID=0 DF PROTO=UDP SPT=1900 DPT=1900 LEN=355 
[  424.307363] Unknown OutputIN= OUT=virbr0 SRC=192.168.122.1 DST=239.255.255.250 LEN=387 TOS=0x00 PREC=0x00 TTL=4 ID=0 DF PROTO=UDP SPT=1900 DPT=1900 LEN=367 
[  424.307461] Unknown OutputIN= OUT=virbr0 SRC=192.168.122.1 DST=239.255.255.250 LEN=389 TOS=0x00 PREC=0x00 TTL=4 ID=0 DF PROTO=UDP SPT=1900 DPT=1900 LEN=369 
[  485.338565] Unknown OutputIN= OUT=virbr0 SRC=192.168.122.1 DST=239.255.255.250 LEN=332 TOS=0x00 PREC=0x00 TTL=4 ID=0 DF PROTO=UDP SPT=1900 DPT=1900 LEN=312 
[  485.338680] Unknown OutputIN= OUT=virbr0 SRC=192.168.122.1 DST=239.255.255.250 LEN=323 TOS=0x00 PREC=0x00 TTL=4 ID=0 DF PROTO=UDP SPT=1900 DPT=1900 LEN=303 
[  485.338780] Unknown OutputIN= OUT=virbr0 SRC=192.168.122.1 DST=239.255.255.250 LEN=375 TOS=0x00 PREC=0x00 TTL=4 ID=0 DF PROTO=UDP SPT=1900 DPT=1900 LEN=355 
[  485.338879] Unknown OutputIN= OUT=virbr0 SRC=192.168.122.1 DST=239.255.255.250 LEN=387 TOS=0x00 PREC=0x00 TTL=4 ID=0 DF PROTO=UDP SPT=1900 DPT=1900 LEN=367 
[  485.338975] Unknown OutputIN= OUT=virbr0 SRC=192.168.122.1 DST=239.255.255.250 LEN=389 TOS=0x00 PREC=0x00 TTL=4 ID=0 DF PROTO=UDP SPT=1900 DPT=1900 LEN=369 
[  492.520021] Inbound IN=wlan0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:03:0d:20:ab:7d:08:00 SRC=192.168.2.5 DST=192.168.2.255 LEN=229 TOS=0x00 PREC=0x00 TTL=128 ID=51423 PROTO=UDP SPT=138 DPT=138 LEN=209 
[  534.895704] Inbound IN=wlan0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:03:0d:20:ab:7d:08:00 SRC=192.168.2.5 DST=192.168.2.255 LEN=244 TOS=0x00 PREC=0x00 TTL=128 ID=51437 PROTO=UDP SPT=138 DPT=138 LEN=224 

```

---

### Post by Peter09 on 2009-05-14
Have you installed a bridged network?

---

### Post by suitedaces on 2009-05-14
I have installed twonkymedia? Though I removed it from the start up applications. Should I uninstall it?

---

### Post by binbash on 2009-05-14
I have same problem even i removed most of start up applications

---

### Post by Peter09 on 2009-05-14
No experience with TwonkyMedia.....

What is the contents of

/etc/network/interfaces

and the output of

```
ifconfig
```

---

### Post by suitedaces on 2009-05-14
/etc/network/interfaces:
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
#iface eth0 inet dhcp


ifconfig:

eth0      Link encap:Ethernet  HWaddr 00:1e:68:21:23:41  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:252 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:443 errors:0 dropped:0 overruns:0 frame:0
          TX packets:443 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:66590 (66.5 KB)  TX bytes:66590 (66.5 KB)

virbr0    Link encap:Ethernet  HWaddr 72:81:ce:34:df:cd  
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          inet6 addr: fe80::7081:ceff:fe34:dfcd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:51 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:11089 (11.0 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1f:3a:48:58:0c  
          inet addr:192.168.2.2  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:3aff:fe48:580c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7017 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6822 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7113172 (7.1 MB)  TX bytes:1398148 (1.3 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1F-3A-48-58-0C-38-30-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by Peter09 on 2009-05-14
I think you have a bridge configured there. This may be your problem because if there is a problem a bridge can take a considerable time to establish.

What is the output of the command

```
route
```

---

### Post by suitedaces on 2009-05-14
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.xxx.2.0     *               255.255.255.0   U     2      0        0 wlan0
192.xxx.122.0   *               255.255.255.0   U     0      0        0 virbr0
link-local      *               255.255.0.0     U     1000   0        0 wlan0
default         192.xxx.2.1     0.0.0.0         UG    0      0        0 wlan0


Not hiding my IP from you specifically, just playing it safe (i assume that's enough to hide it)

---

### Post by Peter09 on 2009-05-14
Hi - these are internal IP address, they do not go past your router, so one of the standard schema's is 192.168.something.something

So there is no problem publishing them. 

You will have an external IP adddress that your ISP gives you. That you should not publish here.

Can you look in the log files, say messages and syslog for anything.

You can use

System->Admin->Logfile Viewer

Aslo have a look in System->Preferences->Startup Applications

Se if you can stop your recent installed app from running at startup

---

### Post by suitedaces on 2009-05-14
Thanks. Not sure what I'm looking for, but there's an afwul lot of this in the log files.

 ubuntu kernel: [  550.159679] Unknown OutputIN= OUT=virbr0 SRC=192.168.122.1 DST=239.255.255.250 LEN=389 TOS=0x00 PREC=0x00 TTL=4 ID=0 DF PROTO=UDP SPT=1900 DPT=1900 LEN=369 
May 14 10:17:01 ubuntu kernel: [  610.250879] Unknown OutputIN= OUT=virbr0 SRC=192.168.122.1 DST=239.255.255.250 LEN=332 TOS=0x00 PREC=0x00 TTL=4 ID=0 DF PROTO=UDP SPT=1900 DPT=1900 LEN=312 
May 14 10:17:01 ubuntu kernel: [  610.250991] Unknown OutputIN= OUT=virbr0 SRC=192.168.122.1 DST=239.255.255.250 LEN=323 TOS=0x00 PREC=0x00 TTL=4 ID=0 DF PROTO=UDP SPT=1900 DPT=1900 LEN=303 
May 14 10:17:01

---

### Post by Peter09 on 2009-05-14
Can you find where the application starts and stop it?

---

### Post by suitedaces on 2009-05-14
> **Peter09 said:**
> Can you find where the application starts and stop it?

Not entirely sure if I'm honest, sorry.

---

### Post by Peter09 on 2009-05-14
Is it in

 System->Preferences->Startup Applications

---

### Post by suitedaces on 2009-05-14
I had it in that, but then I unchecked it then removed it, but the problem still persists.

---

### Post by Peter09 on 2009-05-14
Have you tried uninstalling it?

---

### Post by Peter09 on 2009-05-14
Have you been using a virtual machine software, I think this is a VMware bridge

---

### Post by suitedaces on 2009-05-14
I have ran OpenSuse once or twice in Virtual Box OSE, but I don't think I've got it set to start up automatically.

---

