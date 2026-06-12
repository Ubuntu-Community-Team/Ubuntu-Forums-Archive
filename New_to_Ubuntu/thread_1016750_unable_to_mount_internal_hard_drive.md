---
title: "unable to mount internal hard drive"
date: 2008-12-20
forum: New to Ubuntu
---

### Post by fletcham on 2008-12-20
Hi,
I have two internal hard drive, one just stores media. I have just formatted the media drive ext3 and now i am unable to mount it. I typed: "sudo mount /dev/sdb" in the terminal and get this:

fletch@fletch-desktop:~$ sudo mount /dev/sdb
mount: wrong fs type, bad option, bad superblock on /dev/sdb,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

fletch@fletch-desktop:~$ 

Anyone know what I need to do to sort this out.

Cheers, Fletch :popcorn:

---

### Post by fletcham on 2008-12-20
By the way, i typed dmesg in terminal. Results were:

[   18.217872] system 00:07: ioport range 0x800-0x80f has been reserved
[   18.217874] system 00:07: ioport range 0x500-0x57f has been reserved
[   18.217877] system 00:07: ioport range 0x580-0x5ff has been reserved
[   18.217879] system 00:07: ioport range 0x800-0x87f could not be reserved
[   18.217881] system 00:07: ioport range 0x880-0x8ff has been reserved
[   18.217883] system 00:07: ioport range 0xd00-0xd7f has been reserved
[   18.217886] system 00:07: ioport range 0xd80-0xdff has been reserved
[   18.217888] system 00:07: ioport range 0x900-0x97f has been reserved
[   18.217890] system 00:07: ioport range 0x980-0x9ff has been reserved
[   18.217893] system 00:07: ioport range 0x2000-0x207f has been reserved
[   18.217895] system 00:07: ioport range 0x2080-0x20ff has been reserved
[   18.217898] system 00:07: iomem range 0xfefe0000-0xfefe01ff has been reserved
[   18.217900] system 00:07: iomem range 0xfefe1000-0xfefe1fff has been reserved
[   18.217902] system 00:07: iomem range 0xfee01000-0xfeefffff could not be reserved
[   18.217905] system 00:07: iomem range 0xffb80000-0xffffffff could not be reserved
[   18.217907] system 00:07: iomem range 0xff300000-0xff3fffff has been reserved
[   18.217913] system 00:09: iomem range 0xfec00000-0xfec00fff could not be reserved
[   18.217915] system 00:09: iomem range 0xfee00000-0xfee00fff could not be reserved
[   18.217918] system 00:09: iomem range 0x78000000-0x7fffffff has been reserved
[   18.217923] system 00:0c: ioport range 0x230-0x23f has been reserved
[   18.217926] system 00:0c: ioport range 0x290-0x29f has been reserved
[   18.217928] system 00:0c: ioport range 0xa00-0xa0f has been reserved
[   18.217930] system 00:0c: ioport range 0xa10-0xa1f has been reserved
[   18.217935] system 00:0e: iomem range 0xe0000000-0xefffffff has been reserved
[   18.217940] system 00:0f: iomem range 0x0-0x9ffff could not be reserved
[   18.217942] system 00:0f: iomem range 0xc0000-0xcffff could not be reserved
[   18.217945] system 00:0f: iomem range 0xe0000-0xfffff could not be reserved
[   18.217947] system 00:0f: iomem range 0x100000-0x77ffffff could not be reserved
[   18.217949] system 00:0f: iomem range 0xff780000-0xffffffff could not be reserved
[   18.248257] PCI: Bridge: 0000:00:04.0
[   18.248258]   IO window: disabled.
[   18.248261]   MEM window: disabled.
[   18.248263]   PREFETCH window: disabled.
[   18.248266] PCI: Bridge: 0000:00:09.0
[   18.248267]   IO window: disabled.
[   18.248269]   MEM window: disabled.
[   18.248271]   PREFETCH window: disabled.
[   18.248272] PCI: Bridge: 0000:00:0b.0
[   18.248274]   IO window: disabled.
[   18.248275]   MEM window: disabled.
[   18.248277]   PREFETCH window: disabled.
[   18.248279] PCI: Bridge: 0000:00:0c.0
[   18.248280]   IO window: disabled.
[   18.248282]   MEM window: disabled.
[   18.248283]   PREFETCH window: disabled.
[   18.248292] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   18.248300] PCI: Setting latency timer of device 0000:00:09.0 to 64
[   18.248306] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[   18.248311] PCI: Setting latency timer of device 0000:00:0c.0 to 64
[   18.248320] NET: Registered protocol family 2
[   18.285870] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   18.286107] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   18.286843] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   18.287228] TCP: Hash tables configured (established 131072 bind 65536)
[   18.287230] TCP reno registered
[   18.297928] checking if image is initramfs... it is
[   18.835430] Freeing initrd memory: 7729k freed
[   18.835881] audit: initializing netlink socket (disabled)
[   18.835893] audit(1229770458.156:1): initialized
[   18.836050] highmem bounce pool size: 64 pages
[   18.837620] VFS: Disk quotas dquot_6.5.1
[   18.837677] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   18.837783] io scheduler noop registered
[   18.837784] io scheduler anticipatory registered
[   18.837786] io scheduler deadline registered
[   18.837797] io scheduler cfq registered (default)
[   18.837826] pci 0000:00:00.0: Enabling HT MSI Mapping
[   19.361810] pci 0000:00:04.0: Enabling HT MSI Mapping
[   19.361824] pci 0000:00:05.0: Enabling HT MSI Mapping
[   19.361848] pci 0000:00:07.0: Enabling HT MSI Mapping
[   19.361860] pci 0000:00:08.0: Enabling HT MSI Mapping
[   19.361872] pci 0000:00:08.1: Enabling HT MSI Mapping
[   19.361885] pci 0000:00:09.0: Enabling HT MSI Mapping
[   19.361898] pci 0000:00:0b.0: Enabling HT MSI Mapping
[   19.361911] pci 0000:00:0c.0: Enabling HT MSI Mapping
[   19.361923] Boot video device is 0000:00:0d.0
[   19.362016] PCI: Setting latency timer of device 0000:00:09.0 to 64
[   19.362040] assign_interrupt_mode Found MSI capability
[   19.362056] Allocate Port Service[0000:00:09.0:pcie00]
[   19.362110] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[   19.362128] assign_interrupt_mode Found MSI capability
[   19.362141] Allocate Port Service[0000:00:0b.0:pcie00]
[   19.362188] PCI: Setting latency timer of device 0000:00:0c.0 to 64
[   19.362206] assign_interrupt_mode Found MSI capability
[   19.362218] Allocate Port Service[0000:00:0c.0:pcie00]
[   19.362400] isapnp: Scanning for PnP cards...
[   19.715644] isapnp: No Plug & Play device found
[   19.741750] Real Time Clock Driver v1.12ac
[   19.741926] hpet_resources: 0xfed00000 is busy
[   19.741962] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   19.742078] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   19.742614] 00:0d: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   19.743277] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   19.743330] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   19.743412] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[   19.744015] serio: i8042 KBD port at 0x60,0x64 irq 1
[   19.744022] serio: i8042 AUX port at 0x60,0x64 irq 12
[   19.753258] mice: PS/2 mouse device common for all mice
[   19.753364] EISA: Probing bus 0 at eisa.0
[   19.753373] Cannot allocate resource for EISA slot 2
[   19.753388] EISA: Detected 0 cards.
[   19.753390] cpuidle: using governor ladder
[   19.753392] cpuidle: using governor menu
[   19.753468] NET: Registered protocol family 1
[   19.753495] Using IPI No-Shortcut mode
[   19.753525] registered taskstats version 1
[   19.753626]   Magic number: 4:490:932
[   19.753789] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   19.753791] EDD information not available.
[   19.754009] Freeing unused kernel memory: 368k freed
[   19.754032] Write protecting the kernel read-only data: 801k
[   19.774103] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   20.936809] fuse init (API version 7.9)
[   21.233499] usbcore: registered new interface driver usbfs
[   21.233519] usbcore: registered new interface driver hub
[   21.233749] usbcore: registered new device driver usb
[   21.234858] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   21.235134] ACPI: PCI Interrupt Link [LUB0] enabled at IRQ 11
[   21.235137] PCI: setting IRQ 11 as level-triggered
[   21.235140] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [LUB0] -> GSI 11 (level, low) -> IRQ 11
[   21.235153] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   21.235156] ohci_hcd 0000:00:02.0: OHCI Host Controller
[   21.235405] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
[   21.235419] ohci_hcd 0000:00:02.0: irq 11, io mem 0xdffff000
[   21.290427] usb usb1: configuration #1 chosen from 1 choice
[   21.290449] hub 1-0:1.0: USB hub found
[   21.290455] hub 1-0:1.0: 10 ports detected
[   21.296607] SCSI subsystem initialized
[   21.320098] libata version 3.00 loaded.
[   21.353162] Floppy drive(s): fd0 is 1.44M
[   21.372991] FDC 0 is a post-1991 82077
[   21.392120] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
[   21.392380] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 11
[   21.392383] ACPI: PCI Interrupt 0000:00:07.0[A] -> Link [LMAC] -> GSI 11 (level, low) -> IRQ 11
[   21.392388] PCI: Setting latency timer of device 0000:00:07.0 to 64
[   21.912166] forcedeth 0000:00:07.0: ifname eth0, PHY OUI 0x1374 @ 1, addr 00:1b:fc:8c:af:5a
[   21.912171] forcedeth 0000:00:07.0: highdma pwrctl mgmt timirq gbit lnktim msi desc-v3
[   21.912704] ACPI: PCI Interrupt Link [LUB2] enabled at IRQ 10
[   21.912708] PCI: setting IRQ 10 as level-triggered
[   21.912712] ACPI: PCI Interrupt 0000:00:02.1[B] -> Link [LUB2] -> GSI 10 (level, low) -> IRQ 10
[   21.912723] PCI: Setting latency timer of device 0000:00:02.1 to 64
[   21.912726] ehci_hcd 0000:00:02.1: EHCI Host Controller
[   21.912757] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 2
[   21.912782] ehci_hcd 0000:00:02.1: debug port 1
[   21.912786] PCI: cache line size of 64 is not supported by device 0000:00:02.1
[   21.912794] ehci_hcd 0000:00:02.1: irq 10, io mem 0xdfffec00
[   21.923985] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   21.924065] usb usb2: configuration #1 chosen from 1 choice
[   21.924085] hub 2-0:1.0: USB hub found
[   21.924089] hub 2-0:1.0: 10 ports detected
[   22.027887] PCI: Setting latency timer of device 0000:00:06.0 to 64
[   22.028149] ACPI: PCI Interrupt Link [LSA0] enabled at IRQ 15
[   22.028152] PCI: setting IRQ 15 as level-triggered
[   22.028155] ACPI: PCI Interrupt 0000:00:08.0[A] -> Link [LSA0] -> GSI 15 (level, low) -> IRQ 15
[   22.028171] PCI: Setting latency timer of device 0000:00:08.0 to 64
[   22.028178] ACPI: PCI interrupt for device 0000:00:08.0 disabled
[   22.028377] ACPI: PCI Interrupt Link [LSA1] enabled at IRQ 5
[   22.028379] PCI: setting IRQ 5 as level-triggered
[   22.028382] ACPI: PCI Interrupt 0000:00:08.1[B] -> Link [LSA1] -> GSI 5 (level, low) -> IRQ 5
[   22.028397] PCI: Setting latency timer of device 0000:00:08.1 to 64
[   22.028403] ACPI: PCI interrupt for device 0000:00:08.1 disabled
[   22.030704] pata_amd 0000:00:06.0: version 0.3.10
[   22.030747] PCI: Setting latency timer of device 0000:00:06.0 to 64
[   22.032799] scsi0 : pata_amd
[   22.033207] scsi1 : pata_amd
[   22.033695] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[   22.033698] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[   22.351795] ata1.00: ATAPI: TSSTcorpCD/DVDW SH-S182M, SB03, max UDMA/33
[   22.523641] ata1.00: configured for UDMA/33
[   22.523668] ata2: port disabled. ignoring.
[   22.524920] scsi 0:0:0:0: CD-ROM            TSSTcorp CD/DVDW SH-S182M SB03 PQ: 0 ANSI: 5
[   22.524760] sata_nv 0000:00:08.0: version 3.5
[   22.524772] ACPI: PCI Interrupt 0000:00:08.0[A] -> Link [LSA0] -> GSI 15 (level, low) -> IRQ 15
[   22.524812] PCI: Setting latency timer of device 0000:00:08.0 to 64
[   22.524853] scsi2 : sata_nv
[   22.524894] scsi3 : sata_nv
[   22.525023] ata3: SATA max UDMA/133 cmd 0xe400 ctl 0xe080 bmdma 0xd880 irq 15
[   22.525025] ata4: SATA max UDMA/133 cmd 0xe000 ctl 0xdc00 bmdma 0xd888 irq 15
[   23.494951] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   23.519384] ata3.00: ATA-8: SAMSUNG HD501LJ, CR100-10, max UDMA7
[   23.519388] ata3.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   23.527373] ata3.00: configured for UDMA/133
[   23.994697] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   24.003134] ata4.00: ATA-7: SAMSUNG HD103UJ, 1AA01112, max UDMA7
[   24.003137] ata4.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   24.011128] ata4.00: configured for UDMA/133
[   24.010964] scsi 2:0:0:0: Direct-Access     ATA      SAMSUNG HD501LJ  CR10 PQ: 0 ANSI: 5
[   24.011050] scsi 3:0:0:0: Direct-Access     ATA      SAMSUNG HD103UJ  1AA0 PQ: 0 ANSI: 5
[   24.011099] ACPI: PCI Interrupt 0000:00:08.1[B] -> Link [LSA1] -> GSI 5 (level, low) -> IRQ 5
[   24.011137] PCI: Setting latency timer of device 0000:00:08.1 to 64
[   24.011166] scsi4 : sata_nv
[   24.011197] scsi5 : sata_nv
[   24.011317] ata5: SATA max UDMA/133 cmd 0xd800 ctl 0xd480 bmdma 0xd000 irq 5
[   24.011319] ata6: SATA max UDMA/133 cmd 0xd400 ctl 0xd080 bmdma 0xd008 irq 5
[   24.322527] ata5: SATA link down (SStatus 0 SControl 300)
[   24.642364] ata6: SATA link down (SStatus 0 SControl 300)
[   24.665996] Driver 'sd' needs updating - please use bus_type methods
[   24.667113] sd 2:0:0:0: [sda] 976773168 512-byte hardware sectors (500108 MB)
[   24.667123] sd 2:0:0:0: [sda] Write Protect is off
[   24.667125] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   24.667138] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   24.667178] sd 2:0:0:0: [sda] 976773168 512-byte hardware sectors (500108 MB)
[   24.667184] sd 2:0:0:0: [sda] Write Protect is off
[   24.667186] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   24.667197] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   24.667200]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   24.675704] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[   24.675709] Uniform CD-ROM driver Revision: 3.20
[   24.675757] sr 0:0:0:0: Attached scsi CD-ROM sr0
[   24.710872]  sda1 sda2 sda3 < sda5 sda6 >
[   24.745987] sd 2:0:0:0: [sda] Attached SCSI disk
[   24.746029] sd 3:0:0:0: [sdb] 1953525168 512-byte hardware sectors (1000205 MB)
[   24.746038] sd 3:0:0:0: [sdb] Write Protect is off
[   24.746040] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   24.746053] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   24.746083] sd 3:0:0:0: [sdb] 1953525168 512-byte hardware sectors (1000205 MB)
[   24.746091] sd 3:0:0:0: [sdb] Write Protect is off
[   24.746093] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   24.746104] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   24.746106]  sdb:
[   24.752745] sd 3:0:0:0: [sdb] Attached SCSI disk
[   24.756402] sr 0:0:0:0: Attached scsi generic sg0 type 5
[   24.756421] sd 2:0:0:0: Attached scsi generic sg1 type 0
[   24.756435] sd 3:0:0:0: Attached scsi generic sg2 type 0
[   25.006653] Attempting manual resume
[   25.006656] swsusp: Resume From Partition 8:5
[   25.006658] PM: Checking swsusp image.
[   25.006813] PM: Resume from disk failed.
[   25.046981] kjournald starting.  Commit interval 5 seconds
[   25.047241] EXT3-fs: mounted filesystem with ordered data mode.
[   32.070038] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   32.133719] parport_pc 00:06: reported by Plug and Play ACPI
[   32.133765] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   32.168623] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   32.207930] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   32.371271] input: Power Button (FF) as /devices/virtual/input/input3
[   32.416113] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x600
[   32.416127] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x700
[   32.430468] Linux agpgart interface v0.102
[   32.511409] ACPI: Power Button (FF) [PWRF]
[   32.511479] input: Power Button (CM) as /devices/virtual/input/input4
[   32.571389] ACPI: Power Button (CM) [PWRB]
[   32.639156] nvidia: module license 'NVIDIA' taints kernel.
[   33.005306] ACPI: PCI Interrupt Link [LMC9] enabled at IRQ 11
[   33.005311] ACPI: PCI Interrupt 0000:00:0d.0[A] -> Link [LMC9] -> GSI 11 (level, low) -> IRQ 11
[   33.005317] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[   33.005515] NVRM: loading NVIDIA UNIX x86 Kernel Module  169.12  Thu Feb 14 17:53:07 PST 2008
[   33.099183] logips2pp: Detected unknown logitech mouse model 89
[   33.242054] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 11
[   33.242059] ACPI: PCI Interrupt 0000:00:05.0[B] -> Link [LAZA] -> GSI 11 (level, low) -> IRQ 11
[   33.242074] PCI: Setting latency timer of device 0000:00:05.0 to 64
[   33.570953] input: ImExPS/2 Logitech Explorer Mouse as /devices/platform/i8042/serio1/input/input5
[   34.261312] lp0: using parport0 (interrupt-driven).
[   34.441410] it87: Found IT8712F chip at 0x290, revision 8
[   34.441421] it87: in3 is VCC (+5V)
[   34.441422] it87: in7 is VCCH (+5V Stand-By)
[   34.501449] Adding 5694968k swap on /dev/sda5.  Priority:-1 extents:1 across:5694968k
[   35.034971] EXT3 FS on sda2, internal journal
[   35.142623] device-mapper: uevent: version 1.0.3
[   35.142648] device-mapper: ioctl: 4.12.0-ioctl (2007-10-02) initialised: [email]dm-devel@redhat.com[/email]
[   39.770423] kjournald starting.  Commit interval 5 seconds
[   39.770727] EXT3-fs warning: mounting fs with errors, running e2fsck is recommended
[   39.775060] EXT3 FS on sdb, internal journal
[   39.775064] EXT3-fs: mounted filesystem with ordered data mode.
[   40.246935] ip_tables: (C) 2000-2006 Netfilter Core Team
[   40.716724] No dock devices found.
[   41.003393] powernow-k8: Found 1 AMD Athlon(tm) 64 X2 Dual Core Processor 4400+ processors (2 cpu cores) (version 2.20.00)
[   41.003719] powernow-k8: MP systems not supported by PSB BIOS structure
[   41.003436] powernow-k8: MP systems not supported by PSB BIOS structure
[   41.968441] ppdev: user-space parallel port driver
[   42.170696] audit(1229770481.994:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5253 profile="/usr/sbin/cupsd" namespace="default"
[   42.237181] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   42.237187] apm: disabled - APM is not SMP safe.
[   42.711939] NET: Registered protocol family 10
[   42.712132] lo: Disabled Privacy Extensions
[   44.765391] Bluetooth: Core ver 2.11
[   44.765774] NET: Registered protocol family 31
[   44.765778] Bluetooth: HCI device and connection manager initialized
[   44.765782] Bluetooth: HCI socket layer initialized
[   44.798973] Bluetooth: L2CAP ver 2.9
[   44.798978] Bluetooth: L2CAP socket layer initialized
[   44.865619] Bluetooth: RFCOMM socket layer initialized
[   44.865771] Bluetooth: RFCOMM TTY layer initialized
[   44.865773] Bluetooth: RFCOMM ver 1.8
[   48.343251] NET: Registered protocol family 17
[   60.012232] eth0: no IPv6 routers present
[   94.150943] usb 2-9: new high speed USB device using ehci_hcd and address 2
[   94.283842] usb 2-9: configuration #1 chosen from 1 choice
[   94.368362] usbcore: registered new interface driver libusual
[   94.399366] Initializing USB Mass Storage driver...
[   94.400803] scsi6 : SCSI emulation for USB Mass Storage devices
[   94.402965] usbcore: registered new interface driver usb-storage
[   94.402971] USB Mass Storage support registered.
[   94.403739] usb-storage: device found at 2
[   94.403744] usb-storage: waiting for device to settle before scanning
[   99.400368] usb-storage: device scan complete
[  102.662611] scsi 6:0:0:0: Direct-Access     BUFFALO  External HDD          PQ: 0 ANSI: 2 CCS
[  102.663977] sd 6:0:0:0: [sdc] 1953525168 512-byte hardware sectors (1000205 MB)
[  102.664838] sd 6:0:0:0: [sdc] Write Protect is off
[  102.664841] sd 6:0:0:0: [sdc] Mode Sense: 34 00 00 00
[  102.664843] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[  102.666085] sd 6:0:0:0: [sdc] 1953525168 512-byte hardware sectors (1000205 MB)
[  102.666835] sd 6:0:0:0: [sdc] Write Protect is off
[  102.666838] sd 6:0:0:0: [sdc] Mode Sense: 34 00 00 00
[  102.666839] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[  102.667135]  sdc: sdc1
[  102.684431] sd 6:0:0:0: [sdc] Attached SCSI disk
[  102.684559] sd 6:0:0:0: Attached scsi generic sg3 type 0
[  119.772688] usb 2-9: USB disconnect, address 2
[ 1094.984452] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 1094.984459] ata4.00: BMDMA stat 0x24
[ 1094.984464] ata4.00: cmd 25/00:08:d8:bb:55/00:00:38:00:00/e0 tag 0 dma 4096 in
[ 1094.984465]          res 51/40:00:db:bb:55/40:00:38:00:00/e0 Emask 0x9 (media error)
[ 1094.984468] ata4.00: status: { DRDY ERR }
[ 1094.984470] ata4.00: error: { UNC }
[ 1097.618685] ata4.00: configured for UDMA/133
[ 1097.618694] ata4: EH complete
[ 1098.590312] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 1098.590315] ata4.00: BMDMA stat 0x24
[ 1098.590320] ata4.00: cmd 25/00:08:d8:bb:55/00:00:38:00:00/e0 tag 0 dma 4096 in
[ 1098.590321]          res 51/40:00:db:bb:55/40:00:38:00:00/e0 Emask 0x9 (media error)
[ 1098.590324] ata4.00: status: { DRDY ERR }
[ 1098.590326] ata4.00: error: { UNC }
[ 1099.565731] ata4.00: configured for UDMA/133
[ 1099.565736] ata4: EH complete
[ 1100.530108] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 1100.530111] ata4.00: BMDMA stat 0x24
[ 1100.530116] ata4.00: cmd 25/00:08:d8:bb:55/00:00:38:00:00/e0 tag 0 dma 4096 in
[ 1100.530117]          res 51/40:00:db:bb:55/40:00:38:00:00/e0 Emask 0x9 (media error)
[ 1100.530119] ata4.00: status: { DRDY ERR }
[ 1100.530120] ata4.00: error: { UNC }
[ 1101.508717] ata4.00: configured for UDMA/133
[ 1101.508722] ata4: EH complete
[ 1102.469907] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 1102.469910] ata4.00: BMDMA stat 0x24
[ 1102.469914] ata4.00: cmd 25/00:08:d8:bb:55/00:00:38:00:00/e0 tag 0 dma 4096 in
[ 1102.469915]          res 51/40:00:db:bb:55/40:00:38:00:00/e0 Emask 0x9 (media error)
[ 1102.469918] ata4.00: status: { DRDY ERR }
[ 1102.469919] ata4.00: error: { UNC }
[ 1103.447741] ata4.00: configured for UDMA/133
[ 1103.447745] ata4: EH complete
[ 1104.409707] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 1104.409709] ata4.00: BMDMA stat 0x24
[ 1104.409714] ata4.00: cmd 25/00:08:d8:bb:55/00:00:38:00:00/e0 tag 0 dma 4096 in
[ 1104.409715]          res 51/40:00:db:bb:55/40:00:38:00:00/e0 Emask 0x9 (media error)
[ 1104.409717] ata4.00: status: { DRDY ERR }
[ 1104.409719] ata4.00: error: { UNC }
[ 1105.382764] ata4.00: configured for UDMA/133
[ 1105.382769] ata4: EH complete
[ 1106.341217] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 1106.341220] ata4.00: BMDMA stat 0x24
[ 1106.341224] ata4.00: cmd 25/00:08:d8:bb:55/00:00:38:00:00/e0 tag 0 dma 4096 in
[ 1106.341225]          res 51/40:00:db:bb:55/40:00:38:00:00/e0 Emask 0x9 (media error)
[ 1106.341227] ata4.00: status: { DRDY ERR }
[ 1106.341229] ata4.00: error: { UNC }
[ 1107.325782] ata4.00: configured for UDMA/133
[ 1107.325789] sd 3:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 1107.325792] sd 3:0:0:0: [sdb] Sense Key : Medium Error [current] [descriptor]
[ 1107.325796] Descriptor sense data with sense descriptors (in hex):
[ 1107.325798]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[ 1107.325804]         38 55 bb db 
[ 1107.325806] sd 3:0:0:0: [sdb] Add. Sense: Unrecovered read error - auto reallocate failed
[ 1107.325811] end_request: I/O error, dev sdb, sector 945142747
[ 1107.325819] ata4: EH complete
[ 1107.324160] sd 3:0:0:0: [sdb] 1953525168 512-byte hardware sectors (1000205 MB)
[ 1107.324328] sd 3:0:0:0: [sdb] Write Protect is off
[ 1107.324330] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[ 1107.324656] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 1107.324984] sd 3:0:0:0: [sdb] 1953525168 512-byte hardware sectors (1000205 MB)
[ 1107.325148] sd 3:0:0:0: [sdb] Write Protect is off
[ 1107.325150] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[ 1107.325479] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 1107.328041] EXT3-fs error (device sdb): ext3_free_branches: Read failure, inode=50921576, block=118142843
[ 2417.228803] end_request: I/O error, dev fd0, sector 0
[ 2429.394109] end_request: I/O error, dev fd0, sector 0
[ 2449.735744] end_request: I/O error, dev fd0, sector 0
[ 2461.897222] end_request: I/O error, dev fd0, sector 0
[ 2474.059096] end_request: I/O error, dev fd0, sector 0
[ 2474.059104] Buffer I/O error on device fd0, logical block 0
[ 2486.224846] end_request: I/O error, dev fd0, sector 0
[ 2486.224854] Buffer I/O error on device fd0, logical block 0
[ 2585.363251] end_request: I/O error, dev fd0, sector 0
[ 2597.536668] end_request: I/O error, dev fd0, sector 0
[ 2609.710723] end_request: I/O error, dev fd0, sector 0
[ 2609.710731] Buffer I/O error on device fd0, logical block 0
[ 2621.876675] end_request: I/O error, dev fd0, sector 0
[ 2621.876683] Buffer I/O error on device fd0, logical block 0
[ 2677.224401] end_request: I/O error, dev fd0, sector 0
[ 2689.390817] end_request: I/O error, dev fd0, sector 0
[ 2701.548401] end_request: I/O error, dev fd0, sector 0
[ 2701.548409] Buffer I/O error on device fd0, logical block 0
[ 2713.730536] end_request: I/O error, dev fd0, sector 0
[ 2713.730544] Buffer I/O error on device fd0, logical block 0
[ 2796.531387] end_request: I/O error, dev fd0, sector 0
[ 2808.706598] end_request: I/O error, dev fd0, sector 0
[ 2829.019622] end_request: I/O error, dev fd0, sector 0
[ 2841.185236] end_request: I/O error, dev fd0, sector 0
[ 2853.343439] end_request: I/O error, dev fd0, sector 0
[ 2853.343448] Buffer I/O error on device fd0, logical block 0
[ 2865.509137] end_request: I/O error, dev fd0, sector 0
[ 2865.509146] Buffer I/O error on device fd0, logical block 0
[ 2948.587167] end_request: I/O error, dev fd0, sector 0
[ 2960.760699] end_request: I/O error, dev fd0, sector 0
[ 2972.922494] end_request: I/O error, dev fd0, sector 0
[ 2972.922501] Buffer I/O error on device fd0, logical block 0
[ 2985.092635] end_request: I/O error, dev fd0, sector 0
[ 2985.092642] Buffer I/O error on device fd0, logical block 0
[ 3282.413697] end_request: I/O error, dev fd0, sector 0
[ 3294.579891] end_request: I/O error, dev fd0, sector 0
[ 3306.741529] end_request: I/O error, dev fd0, sector 0
[ 3306.741536] Buffer I/O error on device fd0, logical block 0
[ 3318.907642] end_request: I/O error, dev fd0, sector 0
[ 3318.907649] Buffer I/O error on device fd0, logical block 0
[14656.756537] EXT3-fs error (device sdb): ext3_check_descriptors: Block bitmap for group 880 not in group (block 0)!
[14656.763552] EXT3-fs: group descriptors corrupted!
[14695.805332] EXT3-fs error (device sdb): ext3_check_descriptors: Block bitmap for group 880 not in group (block 0)!
[14695.811480] EXT3-fs: group descriptors corrupted!
[14725.217248] end_request: I/O error, dev fd0, sector 0
[14737.386885] end_request: I/O error, dev fd0, sector 0
[14757.728665] end_request: I/O error, dev fd0, sector 0
[14769.898442] end_request: I/O error, dev fd0, sector 0
[14782.064295] end_request: I/O error, dev fd0, sector 0
[14782.064303] Buffer I/O error on device fd0, logical block 0
[14794.230328] end_request: I/O error, dev fd0, sector 0
[14794.230336] Buffer I/O error on device fd0, logical block 0
[14924.083863] EXT3-fs error (device sdb): ext3_check_descriptors: Block bitmap for group 880 not in group (block 0)!
[14924.088018] EXT3-fs: group descriptors corrupted!
fletch@fletch-desktop:~$ 

Thanks for any help!!!

---

### Post by lovelyvik293 on 2008-12-20
post the output of
```

fdisk -l

```

---

### Post by mapes12 on 2008-12-20
> fletch@fletch-desktop:~$ sudo mount /dev/sdbYou need to specify the partition number e.g. "sdb1" or whatever the second HDD partition number is plus the directory to mount the drive to.

For example, I have a second HDD on my machine. To mount it I have made a new directory in the file system called HDD2: ```
sudo mkdir /HDD2
``` then to mount it I entire the command ```
sudo mount /dev/sdb1 /HDD2
``` I can then access it via the Nautilus GUI or commands via Terminal.

---

### Post by fletcham on 2008-12-20
At the isk of sounding really stupid, how do i make a new directory in the file system. I may as well call mine HDD2 as well. Would you mind just briefly running thru how i do it. Im not too good with computers.

Thanks a lot!! 

fdisk -l shows:


fletch@fletch-desktop:~$ sudo fdisk -l
[sudo] password for fletch: 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000ee876

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3589    28828611    7  HPFS/NTFS
/dev/sda2            3590       59382   448157272+  83  Linux
/dev/sda3           59383       60801    11398086    f  W95 Ext'd (LBA)
/dev/sda5           59383       60091     5694979+  82  Linux swap / Solaris
/dev/sda6           60092       60092        8001   82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000dba61

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121601   976760001   83  Linux
fletch@fletch-desktop:~$

---

### Post by BDNiner on 2008-12-20
yes you have to specify the partition on the drive that you want to mount and you should also specify the directory that you want to mount the hard disk to.

```

sudo mkdir /HDD2


```
that is the command to create a directory named HDD2 in the root of your file system.

---

### Post by pdtpatrick on 2008-12-20
looks like you just formatted and no file system exists on it so you might have to do that. 

in any case .. to make a directory say hdd2 .. switch to the directory where you want it made and type mkdir HDD2. Make sure you are not logged in as root or else when you mount that HDD2, only root would have access to it and im not sure if thats what you desire.

btw what did u use to format the drive?

---

### Post by mapes12 on 2008-12-20
Just enter the commands I posted previously in Terminal (**Applications>Terminal**). Then go **Places>Computer>Filesystem>HDD2** and you should be able to see everything on your second HDD.

Your > fdisk -loutput looks fine. It reports the second HDD as sdb1. You're good to go.

EDIT - If you need Root privileges to do stuff with the second HDD then launch Nautilus in super user mode like this: > gksudo nautilusfrom your Terminal.

---

### Post by bumanie on 2008-12-20
could you please post the output of > cat /etc/fstab

---

### Post by fletcham on 2008-12-20
Cheers for your help fellas.

Ive done what you said Mapes and I can now see everything on my 2nd hard drive when i go to Places>Computer>Filesystem>HDD2. What i want tho is for the the drive to show as an icon on my desktop. How do i do this?

The following is the output of cat /etc/fstab



fletch@fletch-desktop:~$ cat /etc/fstab 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=f43c90ee-e69b-4908-b2cf-e79590581064 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda6
UUID=878d426e-0221-465d-aaf8-a975ec30c4ae none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sdb    /media/mynewdrive   ext3    defaults     0        2
fletch@fletch-desktop:~$

---

### Post by logos34 on 2008-12-20
> **fletcham said:**
> 
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=f43c90ee-e69b-4908-b2cf-e79590581064 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda6
UUID=878d426e-0221-465d-aaf8-a975ec30c4ae none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
[COLOR="Red"]/dev/sdb    /media/mynewdrive   ext3    defaults     0        2[/COLOR]
fletch@fletch-desktop:~$

need a partition number:
> 
/dev/sdb**[COLOR="Blue"]1[/COLOR]**    /media/mynewdrive   ext3    defaults     0        2

sudo mkdir /media/mynewdrive

(if you haven't already)

sudo mount -a

You might have to set the permissions on sdb1:

[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
(see bottom)

---

### Post by fletcham on 2008-12-20
Ok i tried that and the results follow:

sudo mkdir /media/mynewdrive

fletch@fletch-desktop:~$ sudo mkdir /media/mynewdrive
mkdir: cannot create directory `/media/mynewdrive': File exists


sudo mount -a

fletch@fletch-desktop:~$ sudo mount -a
mount: wrong fs type, bad option, bad superblock on /dev/sdb,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

fletch@fletch-desktop:~$

---

### Post by newbee70 on 2008-12-20
> **fletcham said:**
> Ok i tried that and the results follow:

fletch@fletch-desktop:~$

Fletch:

what happens if you try: **sudo mount /media/mynewdrive**

---

### Post by mikjp on 2008-12-20
I think it would be a better idea to use some sensible path for the second internal hard drive using filesystem standard hierarchy. 

I would mount an external drive as /home/username, or if it contains only multimedia as /home/username/multimedia etc. Remember that you can mount a hard disk anywhere in the filesystem, even in a subdirectory in your home directory.

Isn't /media used for external media?

---

### Post by newbee70 on 2008-12-20
> **mikjp said:**
> 

Isn't /media used for external media?


you are right, I stand corrected. thanks.

---

### Post by fletcham on 2008-12-20
Righto then... so how do i mount it so it show on the desktop??:o

---

### Post by logos34 on 2008-12-20
> **newbee70 said:**
> you are right, I stand corrected. thanks.

/media is the standard mount directory for external and internal.

---

### Post by logos34 on 2008-12-20
> **fletcham said:**
> Ive done what you said Mapes and I can now see everything on my 2nd hard drive when i go to Places>Computer>Filesystem>HDD2. What i want tho is for the the drive to show as an icon on my desktop. How do i do this?

ok, so I see sdb1 is already mounted at /media/HDD2, which explains the error when trying to mount at mynewdrive.  Just make sure to edit fstab:
> 
/dev/sdb**[COLOR="Blue"]1[/COLOR]**    [COLOR="Blue"]**/media/HDD2**[/COLOR]   ext3    defaults     0        2

or wherever you decide to mount it (in /home, /media or whatnot)

To make it show desktop icon your need to go into gconf-editor and set 'show volumes'

---

### Post by fletcham on 2008-12-20
Nice one it is now showing on my desktop. So thanks for that but I now have another problem with it. I just tried to drag a fil into it and it says "Error while copying Donnie Brasco.avi" and under show more details it says: "Error opening file '/media/HDD2/DonnieBrasco.avi': Permission Denied"

This is so annoying. Thanks a lot for your help.

Any ideas how i sort this out now?

Fletch:popcorn:

---

### Post by mapes12 on 2008-12-20
> **fletcham said:**
> Cheers for your help fellas.

Ive done what you said Mapes and I can now see everything on my 2nd hard drive when i go to Places>Computer>Filesystem>HDD2. What i want tho is for the the drive to show as an icon on my desktop. How do i do this?

The following is the output of cat /etc/fstab



fletch@fletch-desktop:~$ cat /etc/fstab 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=f43c90ee-e69b-4908-b2cf-e79590581064 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda6
UUID=878d426e-0221-465d-aaf8-a975ec30c4ae none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sdb    /media/mynewdrive   ext3    defaults     0        2
fletch@fletch-desktop:~$Create the mount directory on your desktop like this: ```
sudo mkdir /home/fletch/Desktop/HDD2
``` then mount your second drive to it like this ```
sudo mount /dev/sdb1 /home/fletch/Desktop/HDD2
``` If you don't need the previous HDD2 folder we created in the Filesystem you can get rid of it like this > sudo rm -rf /HDD2

For the permission issue you probably need super user privileges. So launch Nautilus like this > gksudo nautilus and do your dragging and dropping from that window. EDIT - Having said that your new HDD2 folder will be in /home so you probably will not need super user privileges. See how it goes.

---

### Post by logos34 on 2008-12-20
> **fletcham said:**
> Nice one it is now showing on my desktop. So thanks for that but I now have another problem with it. I just tried to drag a fil into it and it says "Error while copying Donnie Brasco.avi" and under show more details it says: "Error opening file '/media/HDD2/DonnieBrasco.avi': Permission Denied"

See link I posted in #11 above

---

### Post by fletcham on 2008-12-20
Mapes, i did what you said and now I have the hard drive showing on the desktop as i want so thanks for that. I also now have a file called HDD2 on my desktop with a padlock on it and I cant delete it?

---

### Post by mapes12 on 2008-12-20
> **fletcham said:**
> Mapes, i did what you said and now I have the hard drive showing on the desktop as i want so thanks for that. I also now have a file called HDD2 on my desktop with a padlock on it and I cant delete it?Are you saying you have two HDD2 folders on your desktop? Can you post a screen shot please.

---

### Post by fletcham on 2008-12-20
Now i have one icon called 1000.2 GB Media and one folder called HDD2 (with the lock on it): /home/fletch/Desktop/mydesktop.png

---

### Post by fletcham on 2008-12-20
Hopefully the screenshot is attached now

---

### Post by fletcham on 2008-12-20
Im getting well lost with all this now lol. I only just noticed Logos' link on post no 11 and it looks pretty straight forward. How do i remove any current mount points so i can just start again and follow that link.

:(

---

### Post by mapes12 on 2008-12-20
> **fletcham said:**
> Im getting well lost with all this now lol. I only just noticed Logos' link on post no 11 and it looks pretty straight forward. How do i remove any current mount points so i can just start again and follow that link.

:(Post #11 link will create your mount point in your filesystem not your desktop. To unlock the HDD2 folder try this: ```
sudo chmod -R 7777 /home/fletch/Desktop/HDD2
```

---

### Post by fletcham on 2008-12-20
Ok i typed that code in. Im not sure what it did but I can drag things into the HDD" folder so will keep that one and would like to get rid of the 1000GB Media one. 

They seem to be the same thing tho. I can drag stuff into HDD2 and it shows in 1000GB media???? I just cant drag into the 1000GB media one? 

So now all i want to do is just have the HDD2 showing?

---

### Post by mapes12 on 2008-12-20
Next time you reboot ```
sudo mount /dev/sdb1 /home/fletch/Desktop/HDD2
``` in Terminal will make sure you can access the second HDD. That's because you already have the folder HDD2 on your desktop. 

I'm not sure how to get rid of the > **1000GB media one?** icon unless you can back track the instructions that created it. It will do no harm sitting there but try ```
gksudo nautilus
``` then go to **Places>Computer>Filesystem>home>fletch>Desktop** and delete it from there. **Important** at the last stage to delete it highlght it then press **Shift+Delete** to get rid of it. If you don't it will build as a deleted file (usually hidden in your file system) taking up space.

The above will be a permanent deletion.

---

