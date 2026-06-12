---
title: "optical drives don't"
date: 2010-06-17
forum: New to Ubuntu
---

### Post by DarinB on 2010-06-17
I have three optical drives in lucid 
none are showing up i put in cd's and nothing happens. 
can't find them in /home/media/ in home/dev there are some text file on cd cd1 dvdrw but that seems to be it?

---

### Post by DarinB on 2010-06-17
this is the fstab shouldn't the optical drives be there???

# /etc/fstab: static file system information. 
# 
# Use 'blkid -o value -s UUID' to print the universally unique identifier 
# for a device; this may be used with UUID= as a more robust way to name 
# devices that works even if disks are added and removed. See fstab(5). 
# 
# <file system> <mount point>   <type>  <options>       <dump>  <pass> 
proc            /proc           proc    nodev,noexec,nosuid 0       0 
# / was on /dev/sda5 during installation 
UUID=6237f2fc-580f-4f64-b45a-71d0753debbd /               ext4    errors=remount-ro 0       1 
# /mnt/music was on /dev/sdb1 during installation 
UUID=63705dc6-133e-449e-9c9d-114a2a760102 /mnt/music      ext3    defaults        0       2 
# /mnt/o was on /dev/sdc1 during installation 
UUID=4242b0bf-b298-4911-bfc2-af4d442c195e /mnt/o          ext4    defaults        0       2 
# /mnt/o1 was on /dev/sdc2 during installation 
UUID=9a66b32b-8213-4469-a52b-ed24ba8357f7 /mnt/o1         ext4    defaults        0       2 
# swap was on /dev/sda6 during installation 
UUID=751c0a41-95f0-41b0-ab41-8964640b0a2c none            swap    sw              0       0 
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0opy

---

### Post by mbzn on 2010-06-17
i just checked mine and realized i also have no fstab entries for my optical drives. They work fine though.

EDIT: Your optical drives are /dev/cdrom and not /home/dev.

---

### Post by DarinB on 2010-06-18
this is not an answer anybody here are some things i found out i should post????

when I run dmesg

[    0.321026] pci 0000:00:10.0: setting latency timer to 64
[    0.321030] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.321032] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.321035] pci_bus 0000:01: resource 0 io:  [0xa000-0xafff]
[    0.321037] pci_bus 0000:01: resource 1 mem: [0xd0000000-0xd3ffffff]
[    0.321039] pci_bus 0000:01: resource 2 pref mem [0xc0000000-0xcfffffff]
[    0.321042] pci_bus 0000:06: resource 0 io:  [0xb000-0xbfff]
[    0.321044] pci_bus 0000:06: resource 1 mem: [0xd4000000-0xd5ffffff]
[    0.321046] pci_bus 0000:06: resource 2 pref mem [0xd6100000-0xd61fffff]
[    0.321048] pci_bus 0000:06: resource 3 io:  [0x00-0xffff]
[    0.321050] pci_bus 0000:06: resource 4 mem: [0x000000-0xffffffff]
[    0.321085] NET: Registered protocol family 2
[    0.321177] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.321476] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.322150] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.322484] TCP: Hash tables configured (established 131072 bind 65536)
[    0.322485] TCP reno registered
[    0.322548] NET: Registered protocol family 1
[    0.343522] pci 0000:01:00.0: Boot video device
[    0.343681] cpufreq-nforce2: No nForce2 chipset.
[    0.343705] Scanning for low memory corruption every 60 seconds
[    0.343783] audit: initializing netlink socket (disabled)
[    0.343795] type=2000 audit(1276841247.343:1): initialized
[    0.352177] highmem bounce pool size: 64 pages
[    0.352181] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.353464] VFS: Disk quotas dquot_6.5.2
[    0.353512] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.353997] fuse init (API version 7.13)
[    0.354070] msgmni has been set to 1653
[    0.354257] alg: No test for stdrng (krng)
[    0.354304] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.354307] io scheduler noop registered
[    0.354309] io scheduler anticipatory registered
[    0.354310] io scheduler deadline registered
[    0.354346] io scheduler cfq registered (default)
[    0.354469]   alloc irq_desc for 24 on node -1
[    0.354471]   alloc kstat_irqs on node -1
[    0.354479] pcieport 0000:00:02.0: irq 24 for MSI/MSI-X
[    0.354485] pcieport 0000:00:02.0: setting latency timer to 64
[    0.354561]   alloc irq_desc for 25 on node -1
[    0.354563]   alloc kstat_irqs on node -1
[    0.354568] pcieport 0000:00:04.0: irq 25 for MSI/MSI-X
[    0.354573] pcieport 0000:00:04.0: setting latency timer to 64
[    0.354643]   alloc irq_desc for 26 on node -1
[    0.354645]   alloc kstat_irqs on node -1
[    0.354650] pcieport 0000:00:05.0: irq 26 for MSI/MSI-X
[    0.354655] pcieport 0000:00:05.0: setting latency timer to 64
[    0.354722]   alloc irq_desc for 27 on node -1
[    0.354724]   alloc kstat_irqs on node -1
[    0.354729] pcieport 0000:00:06.0: irq 27 for MSI/MSI-X
[    0.354734] pcieport 0000:00:06.0: setting latency timer to 64
[    0.354804]   alloc irq_desc for 28 on node -1
[    0.354805]   alloc kstat_irqs on node -1
[    0.354810] pcieport 0000:00:07.0: irq 28 for MSI/MSI-X
[    0.354815] pcieport 0000:00:07.0: setting latency timer to 64
[    0.354871] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.354892] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.354978] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.354981] ACPI: Power Button [PWRB]
[    0.355036] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.355038] ACPI: Power Button [PWRF]
[    0.355093] fan PNP0C0B:00: registered as cooling_device0
[    0.355097] ACPI: Fan [FAN] (on)
[    0.355632] ACPI: SSDT bfefa940 00175 (v01 Nvidia ASUSACPI 42302E31 AWRD 00000000)
[    0.355890] processor LNXCPU:00: registered as cooling_device1
[    0.356036] ACPI: SSDT bfefad50 000CE (v01 Nvidia ASUSACPI 42302E31 AWRD 00000000)
[    0.356281] processor LNXCPU:01: registered as cooling_device2
[    0.360669] thermal LNXTHERM:01: registered as thermal_zone0
[    0.360677] ACPI: Thermal Zone [THRM] (40 C)
[    0.361891] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.361991] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.362346] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.363263] brd: module loaded
[    0.363663] loop: module loaded
[    0.363723] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    0.363862] pata_acpi 0000:00:0d.0: setting latency timer to 64
[    0.364134] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 23
[    0.364137]   alloc irq_desc for 23 on node -1
[    0.364139]   alloc kstat_irqs on node -1
[    0.364144] pata_acpi 0000:00:0e.0: PCI INT A -> Link[APSI] -> GSI 23 (level, low) -> IRQ 23
[    0.364158] pata_acpi 0000:00:0e.0: setting latency timer to 64
[    0.364166] pata_acpi 0000:00:0e.0: PCI INT A disabled
[    0.364417] ACPI: PCI Interrupt Link [APSJ] enabled at IRQ 22
[    0.364420]   alloc irq_desc for 22 on node -1
[    0.364421]   alloc kstat_irqs on node -1
[    0.364425] pata_acpi 0000:00:0f.0: PCI INT A -> Link[APSJ] -> GSI 22 (level, low) -> IRQ 22
[    0.364439] pata_acpi 0000:00:0f.0: setting latency timer to 64
[    0.364447] pata_acpi 0000:00:0f.0: PCI INT A disabled
[    0.364697] Fixed MDIO Bus: probed
[    0.364725] PPP generic driver version 2.4.2
[    0.364755] tun: Universal TUN/TAP device driver, 1.6
[    0.364757] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.364820] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.365084] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 21
[    0.365087]   alloc irq_desc for 21 on node -1
[    0.365088]   alloc kstat_irqs on node -1
[    0.365092] ehci_hcd 0000:00:0b.1: PCI INT B -> Link[APCL] -> GSI 21 (level, low) -> IRQ 21
[    0.365099] ehci_hcd 0000:00:0b.1: setting latency timer to 64
[    0.365102] ehci_hcd 0000:00:0b.1: EHCI Host Controller
[    0.365129] ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 1
[    0.365154] ehci_hcd 0000:00:0b.1: debug port 1
[    0.365163] ehci_hcd 0000:00:0b.1: cache line size of 32 is not supported
[    0.365177] ehci_hcd 0000:00:0b.1: irq 21, io mem 0xd6007000
[    0.365201] isapnp: Scanning for PnP cards...
[    0.414101] ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00
[    0.414240] usb usb1: configuration #1 chosen from 1 choice
[    0.414265] hub 1-0:1.0: USB hub found
[    0.414273] hub 1-0:1.0: 8 ports detected
[    0.414330] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.414642] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 20
[    0.414647]   alloc irq_desc for 20 on node -1
[    0.414649]   alloc kstat_irqs on node -1
[    0.414655] ohci_hcd 0000:00:0b.0: PCI INT A -> Link[APCF] -> GSI 20 (level, low) -> IRQ 20
[    0.414672] ohci_hcd 0000:00:0b.0: setting latency timer to 64
[    0.414675] ohci_hcd 0000:00:0b.0: OHCI Host Controller
[    0.414705] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 2
[    0.414728] ohci_hcd 0000:00:0b.0: irq 20, io mem 0xd6006000
[    0.467019] Freeing initrd memory: 13380k freed
[    0.503837] usb usb2: configuration #1 chosen from 1 choice
[    0.503863] hub 2-0:1.0: USB hub found
[    0.503875] hub 2-0:1.0: 8 ports detected
[    0.503938] uhci_hcd: USB Universal Host Controller Interface driver
[    0.504052] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.507056] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.507062] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.507160] mice: PS/2 mouse device common for all mice
[    0.507276] rtc_cmos 00:05: RTC can wake from S4
[    0.507312] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    0.507343] rtc0: alarms up to one year, y3k, 242 bytes nvram, hpet irqs
[    0.507436] device-mapper: uevent: version 1.0.3
[    0.507540] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
[    0.507595] device-mapper: multipath: version 1.1.0 loaded
[    0.507598] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.507689] EISA: Probing bus 0 at eisa.0
[    0.507703] Cannot allocate resource for EISA slot 4
[    0.507704] Cannot allocate resource for EISA slot 5
[    0.507714] EISA: Detected 0 cards.
[    0.507777] cpuidle: using governor ladder
[    0.507779] cpuidle: using governor menu
[    0.508172] TCP cubic registered
[    0.508296] NET: Registered protocol family 10
[    0.508715] lo: Disabled Privacy Extensions
[    0.508997] NET: Registered protocol family 17
[    0.509498] Using IPI No-Shortcut mode
[    0.509558] PM: Resume from disk failed.
[    0.509577] registered taskstats version 1
[    0.509933]   Magic number: 14:51:115
[    0.510040] rtc_cmos 00:05: setting system clock to 2010-06-18 06:07:28 UTC (1276841248)
[    0.510043] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.510044] EDD information not available.
[    0.527072] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    0.721008] isapnp: No Plug & Play device found
[    0.721026] Freeing unused kernel memory: 656k freed
[    0.721550] Write protecting the kernel text: 4676k
[    0.721584] Write protecting the kernel read-only data: 1840k
[    0.735846] udev: starting version 151
[    0.743436] usb 1-2: new high speed USB device using ehci_hcd and address 2
[    0.777265] vga16fb: initializing
[    0.777268] vga16fb: mapped to 0xc00a0000
[    0.777303] fb0: VGA16 VGA frame buffer device
[    0.810151] pata_amd 0000:00:0d.0: version 0.4.1
[    0.810193] pata_amd 0000:00:0d.0: setting latency timer to 64
[    0.821679] scsi0 : pata_amd
[    0.824620] scsi1 : pata_amd
[    0.825281] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[    0.825284] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[    0.827365] sata_nv 0000:00:0e.0: version 3.5
[    0.827375] sata_nv 0000:00:0e.0: PCI INT A -> Link[APSI] -> GSI 23 (level, low) -> IRQ 23
[    0.827378] sata_nv 0000:00:0e.0: Using SWNCQ mode
[    0.827414] sata_nv 0000:00:0e.0: setting latency timer to 64
[    0.827679] scsi2 : sata_nv
[    0.827863] scsi3 : sata_nv
[    0.828009] ata3: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xd400 irq 23
[    0.828012] ata4: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xd408 irq 23
[    0.828021] Floppy drive(s): fd0 is 1.44M
[    0.828027] sata_nv 0000:00:0f.0: PCI INT A -> Link[APSJ] -> GSI 22 (level, low) -> IRQ 22
[    0.828029] sata_nv 0000:00:0f.0: Using SWNCQ mode
[    0.828063] sata_nv 0000:00:0f.0: setting latency timer to 64
[    0.829947] scsi4 : sata_nv
[    0.830839] scsi5 : sata_nv
[    0.830984] ata5: SATA max UDMA/133 cmd 0x9e0 ctl 0xbe0 bmdma 0xe800 irq 22
[    0.830986] ata6: SATA max UDMA/133 cmd 0x960 ctl 0xb60 bmdma 0xe808 irq 22
[    0.831495] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
[    0.831499]   alloc irq_desc for 18 on node -1
[    0.831501]   alloc kstat_irqs on node -1
[    0.831506] skge 0000:06:0c.0: PCI INT A -> Link[APC3] -> GSI 18 (level, low) -> IRQ 18
[    0.831536] skge 1.13 addr 0xd5000000 irq 18 chip Yukon-Lite rev 9
[    0.832096] skge eth0: addr 00:24:8c:02:b0:cb
[    0.847348] FDC 0 is a post-1991 82077
[    0.879744] usb 1-2: configuration #1 chosen from 1 choice
[    0.885569] Initializing USB Mass Storage driver...
[    0.885624] scsi6 : SCSI emulation for USB Mass Storage devices
[    0.885685] usbcore: registered new interface driver usb-storage
[    0.885688] USB Mass Storage support registered.
[    0.885691] usb-storage: device found at 2
[    0.885692] usb-storage: waiting for device to settle before scanning
[    0.987695] ata1.00: ATAPI: HL-DT-ST GCE-8400B, B104, max UDMA/33
[    0.987719] ata1: nv_mode_filter: 0x739f&0x739f->0x739f, BIOS=0x7000 (0xc000c5c0) ACPI=0x701f (60:600:0x13)
[    0.991398] usb 1-3: new high speed USB device using ehci_hcd and address 3
[    1.003657] ata1.00: configured for UDMA/33
[    1.004121] scsi 0:0:0:0: CD-ROM            HL-DT-ST CD-RW GCE-8400B  B104 PQ: 0 ANSI: 5
[    1.005967] sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[    1.005970] Uniform CD-ROM driver Revision: 3.20
[    1.006066] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    1.006127] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    1.117209] usb 1-3: configuration #1 chosen from 1 choice
[    1.117594] scsi7 : SCSI emulation for USB Mass Storage devices
[    1.117673] usb-storage: device found at 3
[    1.117675] usb-storage: waiting for device to settle before scanning
[    1.228014] usb 1-4: new high speed USB device using ehci_hcd and address 4
[    1.288039] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.288186] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.296379] ata3.00: ATA-7: SAMSUNG HD753LJ, 1AA01114, max UDMA7
[    1.296382] ata3.00: 1465149168 sectors, multi 1: LBA48 NCQ (depth 31/32)
[    1.304206] ata3.00: configured for UDMA/133
[    1.328395] ata2.00: ATAPI: HL-DT-STDVD-RAM GH22NP20, 1.02, max UDMA/66
[    1.328426] ata2.01: ATAPI: JLMS DVD-ROM XJ-HD166, DD05, max UDMA/33
[    1.328448] ata2: nv_mode_filter: 0x1f39f&0x1f39f->0x1f39f, BIOS=0x1f000 (0xc000c5c0) ACPI=0x1f01f (30:60:0x1f)
[    1.328452] ata2: nv_mode_filter: 0x739f&0x739f->0x739f, BIOS=0x7000 (0xc000c5c0) ACPI=0x701f (30:60:0x1f)
[    1.337977] ata5.00: ATA-7: ST3750640AS, 3.AAE, max UDMA/133
[    1.337981] ata5.00: 1465149168 sectors, multi 1: LBA48 NCQ (depth 31/32)
[    1.344404] ata2.00: configured for UDMA/66
[    1.352487] ata2.01: configured for UDMA/33
[    1.354668] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVD-RAM GH22NP20 1.02 PQ: 0 ANSI: 5
[    1.357955] sr1: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.358051] sr 1:0:0:0: Attached scsi CD-ROM sr1
[    1.358110] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.358446] scsi 1:0:1:0: CD-ROM            JLMS     DVD-ROM XJ-HD166 DD05 PQ: 0 ANSI: 5
[    1.360022] sr2: scsi3-mmc drive: 48x/48x cd/rw xa/form2 cdda tray
[    1.360115] sr 1:0:1:0: Attached scsi CD-ROM sr2
[    1.360167] sr 1:0:1:0: Attached scsi generic sg2 type 5
[    1.360362] scsi 2:0:0:0: Direct-Access     ATA      SAMSUNG HD753LJ  1AA0 PQ: 0 ANSI: 5
[    1.360491] sd 2:0:0:0: Attached scsi generic sg3 type 0
[    1.360573] sd 2:0:0:0: [sda] 1465149168 512-byte logical blocks: (750 GB/698 GiB)
[    1.360611] sd 2:0:0:0: [sda] Write Protect is off
[    1.360613] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.360633] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.360734]  sda:
[    1.361438] usb 1-4: configuration #1 chosen from 1 choice
[    1.384607]  sda1 sda2 < sda5
[    1.404636] ata5.00: configured for UDMA/133
[    1.417077]  sda6 >
[    1.417378] sd 2:0:0:0: [sda] Attached SCSI disk
[    1.472014] usb 1-5: new high speed USB device using ehci_hcd and address 5
[    1.604544] usb 1-5: configuration #1 chosen from 1 choice
[    1.604641] hub 1-5:1.0: USB hub found
[    1.604736] hub 1-5:1.0: 4 ports detected
[    1.828036] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.836189] ata4.00: ATA-7: SAMSUNG HD753LJ, 1AA01114, max UDMA7
[    1.836193] ata4.00: 1465149168 sectors, multi 1: LBA48 NCQ (depth 31/32)
[    1.844203] ata4.00: configured for UDMA/133
[    1.844289] scsi 3:0:0:0: Direct-Access     ATA      SAMSUNG HD753LJ  1AA0 PQ: 0 ANSI: 5
[    1.844385] sd 3:0:0:0: Attached scsi generic sg4 type 0
[    1.844488] scsi 4:0:0:0: Direct-Access     ATA      ST3750640AS      3.AA PQ: 0 ANSI: 5
[    1.844589] sd 4:0:0:0: Attached scsi generic sg5 type 0
[    1.844662] sd 4:0:0:0: [sdc] 1465149168 512-byte logical blocks: (750 GB/698 GiB)
[    1.844700] sd 3:0:0:0: [sdb] 1465149168 512-byte logical blocks: (750 GB/698 GiB)
[    1.844729] sd 4:0:0:0: [sdc] Write Protect is off
[    1.844731] sd 4:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    1.844767] sd 3:0:0:0: [sdb] Write Protect is off
[    1.844770] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    1.844781] sd 4:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.844827] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.844968]  sdc:
[    1.845029]  sdb: sdb1
[    1.850610] sd 3:0:0:0: [sdb] Attached SCSI disk
[    1.860747]  sdc1 sdc2
[    1.860920] sd 4:0:0:0: [sdc] Attached SCSI disk
[    1.896214] usb 1-5.1: new high speed USB device using ehci_hcd and address 6
[    2.129758] usb 1-5.1: configuration #1 chosen from 1 choice
[    2.166487] ata6: SATA link down (SStatus 0 SControl 300)
[    2.326840] Console: switching to colour frame buffer device 80x30
[    2.563460] xor: automatically using best checksumming function: pIII_sse
[    2.579998]    pIII_sse  :  9182.000 MB/sec
[    2.580000] xor: using function: pIII_sse (9182.000 MB/sec)
[    2.582189] device-mapper: dm-raid45: initialized v0.2594b
[    2.872038] EXT4-fs (sda5): mounted filesystem with ordered data mode
[    5.876673] usb-storage: device scan complete
[    5.878053] scsi 6:0:0:0: Direct-Access     Generic  STORAGE DEVICE-A 9727 PQ: 0 ANSI: 0
[    5.878799] scsi 6:0:0:1: Direct-Access     Generic  STORAGE DEVICE-A 9727 PQ: 0 ANSI: 0
[    5.879423] scsi 6:0:0:2: Direct-Access     Generic  STORAGE DEVICE-A 9727 PQ: 0 ANSI: 0
[    5.880173] scsi 6:0:0:3: Direct-Access     Generic  STORAGE DEVICE-A 9727 PQ: 0 ANSI: 0 CCS
[    5.880923] scsi 6:0:0:4: Direct-Access     Generic  STORAGE DEVICE-A 9727 PQ: 0 ANSI: 0
[    5.881257] sd 6:0:0:0: Attached scsi generic sg6 type 0
[    5.881362] sd 6:0:0:1: Attached scsi generic sg7 type 0
[    5.881467] sd 6:0:0:2: Attached scsi generic sg8 type 0
[    5.881575] sd 6:0:0:3: Attached scsi generic sg9 type 0
[    5.881688] sd 6:0:0:4: Attached scsi generic sg10 type 0
[    5.885031] sd 6:0:0:0: [sdd] Attached SCSI removable disk
[    5.885655] sd 6:0:0:1: [sde] Attached SCSI removable disk
[    5.886283] sd 6:0:0:2: [sdf] Attached SCSI removable disk
[    5.886901] sd 6:0:0:3: [sdg] Attached SCSI removable disk
[    5.887525] sd 6:0:0:4: [sdh] Attached SCSI removable disk
[    6.116150] usb-storage: device scan complete
[    6.118033] scsi 7:0:0:0: Direct-Access     HP       Photosmart 2575  1.00 PQ: 0 ANSI: 2
[    6.118386] sd 7:0:0:0: Attached scsi generic sg11 type 0
[    6.119634] sd 7:0:0:0: [sdi] Attached SCSI removable disk
[   15.740062] udev: starting version 151
[   15.823453] lp: driver loaded but no devices found
[   15.828932] Adding 9116848k swap on /dev/sda6.  Priority:-1 extents:1 across:9116848k 
[   15.840931] Linux agpgart interface v0.103
[   16.066065] nvidia: module license 'NVIDIA' taints kernel.
[   16.066067] Disabling lock debugging due to kernel taint
[   16.754482] ACPI: resource nForce2_smbus [0x5000-0x503f] conflicts with ACPI region SM00 [0x5000-0x5005]
[   16.754486] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   16.754488] nForce2_smbus 0000:00:0a.1: Error probing SMB1.
[   16.754530] i2c i2c-0: nForce2 SMBus adapter at 0x5100
[   16.840969] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 23
[   16.840975] HDA Intel 0000:00:10.1: PCI INT B -> Link[AAZA] -> GSI 23 (level, low) -> IRQ 23
[   16.840977] hda_intel: Disable MSI for Nvidia chipset
[   16.841030] HDA Intel 0000:00:10.1: setting latency timer to 64
[   16.869401] usblp0: USB Bidirectional printer dev 3 if 1 alt 0 proto 2 vid 0x03F0 pid 0x4E11
[   16.871274] usblp1: USB Bidirectional printer dev 4 if 0 alt 0 proto 2 vid 0x03F0 pid 0x8904
[   16.871290] usbcore: registered new interface driver usblp
[   16.878095] Linux video capture interface: v2.00
[   16.884735] parport_pc 00:0a: reported by Plug and Play ACPI
[   16.884801] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   16.921376] ppdev: user-space parallel port driver
[   16.930945] usbcore: registered new interface driver snd-usb-audio
[   16.931324] uvcvideo: Found UVC 1.00 device <unnamed> (046d:09a1)
[   16.948605] input: UVC Camera (046d:09a1) as /devices/pci0000:00/0000:00:0b.1/usb1/1-5/1-5.1/1-5.1:1.0/input/input4
[   16.948649] usbcore: registered new interface driver uvcvideo
[   16.948651] USB Video Class driver (v0.1.0)
[   16.980154] lp0: using parport0 (interrupt-driven).
[   17.002893] ACPI: PCI Interrupt Link [APC5] enabled at IRQ 16
[   17.002898]   alloc irq_desc for 16 on node -1
[   17.002900]   alloc kstat_irqs on node -1
[   17.002906] nvidia 0000:01:00.0: PCI INT A -> Link[APC5] -> GSI 16 (level, low) -> IRQ 16
[   17.002912] nvidia 0000:01:00.0: setting latency timer to 64
[   17.002916] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   17.003106] NVRM: loading NVIDIA UNIX x86 Kernel Module  195.36.24  Thu Apr 22 09:18:20 PDT 2010
[   17.021329] EXT4-fs (sdc2): mounted filesystem with ordered data mode
[   17.045892] kjournald starting.  Commit interval 5 seconds
[   17.046330] EXT3 FS on sdb1, internal journal
[   17.046336] EXT3-fs: mounted filesystem with ordered data mode.
[   17.047156] psmouse serio1: ID: 10 00 64
[   17.229470] EXT4-fs (sdc1): mounted filesystem with ordered data mode
[   17.315215] skge eth0: enabling interface
[   17.318417] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   17.446087] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:10.1/input/input5
[   17.694201] input: ImPS/2 Logitech Wheel Mouse as /devices/platform/i8042/serio1/input/input6
[   19.063653] skge eth0: Link is up at 100 Mbps, full duplex, flow control both
[   23.505054] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   24.899348] CPU0 attaching NULL sched-domain.
[   24.899353] CPU1 attaching NULL sched-domain.
[   24.916048] CPU0 attaching sched-domain:
[   24.916051]  domain 0: span 0-1 level MC
[   24.916053]   groups: 0 1
[   24.916057] CPU1 attaching sched-domain:
[   24.916059]  domain 0: span 0-1 level MC
[   24.916061]   groups: 1 0
[   25.842669] usb 1-4: usbfs: interface 0 claimed by usblp while 'usb' sets config #1
[   25.842694] usb 1-3: usbfs: interface 1 claimed by usblp while 'usb' sets config #1
[   32.953346] usb 1-4: usbfs: interface 0 claimed by usblp while 'usb' sets config #1
[   32.953372] usb 1-3: usbfs: interface 1 claimed by usblp while 'usb' sets config #1
[   34.196005] eth0: no IPv6 routers present
[   46.804697] usblp0: removed
[   46.916015] usb 1-3: reset high speed USB device using ehci_hcd and address 3
[   47.049621] usblp0: USB Bidirectional printer dev 3 if 1 alt 0 proto 2 vid 0x03F0 pid 0x4E11
[   47.067385] CPU0 attaching NULL sched-domain.
[   47.067389] CPU1 attaching NULL sched-domain.
[   47.088105] CPU0 attaching sched-domain:
[   47.088108]  domain 0: span 0-1 level MC
[   47.088111]   groups: 0 1
[   47.088115] CPU1 attaching sched-domain:
[   47.088117]  domain 0: span 0-1 level MC
[   47.088119]   groups: 1 0
[  106.804519] ata2: lost interrupt (Status 0x51)
[  106.820029] ata1: lost interrupt (Status 0x51)
[  111.804529] ata2.00: qc timeout (cmd 0xa0)
[  111.804539] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[  111.804544] sr 1:0:0:0: CDB: Test Unit Ready: 00 00 00 00 00 00
[  111.804558] ata2.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
[  111.804560]          res 51/20:03:00:00:00/00:00:00:00:00/a0 Emask 0x5 (timeout)
[  111.804563] ata2.00: status: { DRDY ERR }
[  111.804588] ata2: soft resetting link
[  111.820039] ata1.00: qc timeout (cmd 0xa0)
[  111.820048] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[  111.820052] sr 0:0:0:0: CDB: Test Unit Ready: 00 00 00 00 00 00
[  111.820065] ata1.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
[  111.820066]          res 51/20:03:00:00:00/00:00:00:00:00/a0 Emask 0x5 (timeout)
[  111.820070] ata1.00: status: { DRDY ERR }
[  111.820091] ata1: soft resetting link
[  111.984348] ata1: nv_mode_filter: 0x739f&0x739f->0x739f, BIOS=0x7000 (0xc000c5c0) ACPI=0x701f (60:600:0x13)
[  111.997835] ata1.00: configured for UDMA/33
[  112.140403] ata2: nv_mode_filter: 0x1f39f&0x1f39f->0x1f39f, BIOS=0x1f000 (0xc000c5c0) ACPI=0x1f01f (30:60:0x1f)
[  112.140410] ata2: nv_mode_filter: 0x739f&0x739f->0x739f, BIOS=0x7000 (0xc000c5c0) ACPI=0x701f (30:60:0x1f)
[  112.157201] ata2.00: configured for UDMA/66
[  112.157681] ata2.01: configured for UDMA/33
[  117.000022] ata1.00: qc timeout (cmd 0xa0)
[  117.000030] ata1.00: TEST_UNIT_READY failed (err_mask=0x5)
[  117.000053] ata1: soft resetting link
[  117.160018] ata2.00: qc timeout (cmd 0xa0)
[  117.160024] ata2.00: TEST_UNIT_READY failed (err_mask=0x5)
[  117.160045] ata2: soft resetting link
[  117.164540] ata1: nv_mode_filter: 0x739f&0x739f->0x739f, BIOS=0x7000 (0xc000c5c0) ACPI=0x701f (60:600:0x13)
[  117.184269] ata1.00: configured for UDMA/33
[  117.496429] ata2: nv_mode_filter: 0x1f39f&0x1f39f->0x1f39f, BIOS=0x1f000 (0xc000c5c0) ACPI=0x1f01f (30:60:0x1f)
[  117.496436] ata2: nv_mode_filter: 0x739f&0x739f->0x739f, BIOS=0x7000 (0xc000c5c0) ACPI=0x701f (30:60:0x1f)
[  117.516364] ata2.00: configured for UDMA/66
[  117.516844] ata2.01: configured for UDMA/33
[  122.181115] ata1.00: qc timeout (cmd 0xa0)
[  122.181122] ata1.00: TEST_UNIT_READY failed (err_mask=0x5)
[  122.181130] ata1.00: limiting speed to UDMA/33:PIO3
[  122.181153] ata1: soft resetting link
[  122.344928] ata1: nv_mode_filter: 0x738f&0x739f->0x738f, BIOS=0x7000 (0xc000c5c0) ACPI=0x701f (60:600:0x13)
[  122.362135] ata1.00: configured for UDMA/33
[  122.517680] ata2.00: qc timeout (cmd 0xa0)
[  122.517687] ata2.00: TEST_UNIT_READY failed (err_mask=0x5)
[  122.517691] ata2.00: limiting speed to UDMA/66:PIO3
[  122.517711] ata2: soft resetting link
[  122.852401] ata2: nv_mode_filter: 0x1f38f&0x1f39f->0x1f38f, BIOS=0x1f000 (0xc000c5c0) ACPI=0x1f01f (30:60:0x1f)
[  122.852408] ata2: nv_mode_filter: 0x739f&0x739f->0x739f, BIOS=0x7000 (0xc000c5c0) ACPI=0x701f (30:60:0x1f)
[  122.872340] ata2.00: configured for UDMA/66
[  122.872827] ata2.01: configured for UDMA/33
[  127.361856] ata1.00: qc timeout (cmd 0xa0)
[  127.361863] ata1.00: TEST_UNIT_READY failed (err_mask=0x5)
[  127.361866] ata1.00: disabled
[  127.361895] ata1: soft resetting link
[  127.516639] ata1: EH complete
[  127.874023] ata2.00: qc timeout (cmd 0xa0)
[  127.874029] ata2.00: TEST_UNIT_READY failed (err_mask=0x5)
[  127.874032] ata2.00: disabled
[  127.874037] ata2.01: TEST_UNIT_READY failed (err_mask=0x40)
[  127.874057] ata2: soft resetting link
[  128.200500] ata2: nv_mode_filter: 0x739f&0x739f->0x739f, BIOS=0x7000 (0xc000c5c0) ACPI=0x701f (30:60:0x1f)
[  128.200992] ata2.01: configured for UDMA/33
[  133.204019] ata2.01: qc timeout (cmd 0xa0)
[  133.204025] ata2.01: TEST_UNIT_READY failed (err_mask=0x5)
[  133.204030] ata2.01: limiting speed to UDMA/33:PIO3
[  133.204050] ata2: soft resetting link
[  133.528497] ata2: nv_mode_filter: 0x738f&0x739f->0x738f, BIOS=0x7000 (0xc000c5c0) ACPI=0x701f (30:60:0x1f)
[  133.528989] ata2.01: configured for UDMA/33
[  138.532025] ata2.01: qc timeout (cmd 0xa0)
[  138.532032] ata2.01: TEST_UNIT_READY failed (err_mask=0x5)
[  138.532036] ata2.01: disabled
[  138.532068] ata2: soft resetting link
[  138.852687] ata2: EH complete
darin@darin-desktop ~ $

---

### Post by mk1w86 on 2010-06-18
Are the drives IDE or SATA? :-s

Could you please post the output of:

```
ls -l /dev | grep sd
```

and 

```
sudo fdisk -l
```

---

### Post by DarinB on 2010-06-18
sata

darin@darin-desktop ~ $ ls -l /dev | grep sd
lrwxrwxrwx  1 root root           4 2010-06-18 06:07 root -> sda5
brw-rw----  1 root disk      8,   0 2010-06-18 06:07 sda
brw-rw----  1 root disk      8,   1 2010-06-18 06:07 sda1
brw-rw----  1 root disk      8,   2 2010-06-18 06:07 sda2
brw-rw----  1 root disk      8,   5 2010-06-18 06:07 sda5
brw-rw----  1 root disk      8,   6 2010-06-18 06:07 sda6
brw-rw----  1 root disk      8,  16 2010-06-18 06:07 sdb
brw-rw----  1 root disk      8,  17 2010-06-18 06:07 sdb1
brw-rw----  1 root disk      8,  32 2010-06-18 06:07 sdc
brw-rw----  1 root disk      8,  33 2010-06-18 06:07 sdc1
brw-rw----  1 root disk      8,  34 2010-06-18 06:07 sdc2
brw-rw----  1 root disk      8,  48 2010-06-18 06:07 sdd
brw-rw----  1 root disk      8,  64 2010-06-18 06:07 sde
brw-rw----  1 root disk      8,  80 2010-06-18 06:07 sdf
brw-rw----  1 root disk      8,  96 2010-06-18 06:07 sdg
brw-rw----  1 root disk      8, 112 2010-06-18 06:07 sdh
brw-rw----  1 root disk      8, 128 2010-06-18 06:08 sdi
darin@darin-desktop ~ $ sudo fdisk -l
[sudo] password for darin: 

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x11446ceb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       48092   386296828    7  HPFS/NTFS
/dev/sda2           48093       91201   346273012    5  Extended
/dev/sda5           48093       90066   337156123+  83  Linux
/dev/sda6           90067       91201     9116856   82  Linux swap / Solaris

Disk /dev/sdc: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x790b9718

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       78453   630173691   83  Linux
/dev/sdc2           78454       91201   102398310   83  Linux

Disk /dev/sdb: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x790b971b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       91201   732572001   83  Linux
darin@darin-desktop ~ $

---

### Post by DarinB on 2010-06-18
sorry i made a mistake they are eide the hdd are sata.

---

### Post by mk1w86 on 2010-06-18
> **DarinB said:**
> sorry i made a mistake they are eide the hdd are sata.

It may seem like a silly question but are the drive jumpers set correctly to master and slave?

Out of interest, did you install Ubuntu using one of the optical drives?

---

### Post by DarinB on 2010-06-18
good question it worked fine for about a week.
I do remember seeing the cd cd0 and cd1 in the media of my home now there is only floppy floppy0
I think i may have hit unmount instead of eject for the dvd once but i don't see how that would cause all this and i did use it after that... i think
even so after reboot it would come back. do i need to recreate the mount points? and i am not sure how anymore

---

### Post by DarinB on 2010-06-18
darin@darin-desktop ~ $ ls /dev/cd*
/dev/cdrom  /dev/cdrom1  /dev/cdrw  /dev/cdrw1
darin@darin-desktop ~ $

---

### Post by mk1w86 on 2010-06-18
> **DarinB said:**
> good question it worked fine for about a week.
I do remember seeing the cd cd0 and cd1 in the media of my home now there is only floppy floppy0
I think i may have hit unmount instead of eject for the dvd once but i don't see how that would cause all this and i did use it after that... i think
even so after reboot it would come back. do i need to recreate the mount points? and i am not sure how anymore

I have checked my /media folder and my fstab and like you, I can only see the floppy drive (I have one SATA DVD burner by the way).  However, when I insert a disk a mount point with the name of the disk appears in /media and upon ejecting the disk it disappears.  Whatever system Ubuntu uses must automount and configure the drive.

I doesn't matter whether you use eject, unmount or safely remove; they all do the same thing as far as I know. 

You could try connecting one drive to an IDE channel by itself and see if Ubuntu detects it then. ;)

---

### Post by DarinB on 2010-06-18
i did mkdir /media/cdrom
and change permissions.
at least they are in the /media 
they were before and only the floppy ones are there
now i can boot up and the disk shows up but that is all
i am totally lost as to how this could work perfectly and now just suck...
i can always delete the dir i created to start again
this is making me nuts i thought i was home free with this system good for a few years.....

---

### Post by DarinB on 2010-06-18
hey Taurus here it is the screen shot[ATTACH]160832[/ATTACH]

---

### Post by DarinB on 2010-06-21
can anybody in the linux universe help me on this.
even if it is an unknown bug there must be some solution.....

---

### Post by gsocker on 2010-06-21
Looking at your dmesg output, the drives are found:
```

[ 1.328395] ata2.00: ATAPI: HL-DT-STDVD-RAM GH22NP20, 1.02, max UDMA/66
[ 1.328426] ata2.01: ATAPI: JLMS DVD-ROM XJ-HD166, DD05, max UDMA/33
[ 1.328448] ata2: nv_mode_filter: 0x1f39f&0x1f39f->0x1f39f, BIOS=0x1f000 (0xc000c5c0) ACPI=0x1f01f (30:60:0x1f)
[ 1.328452] ata2: nv_mode_filter: 0x739f&0x739f->0x739f, BIOS=0x7000 (0xc000c5c0) ACPI=0x701f (30:60:0x1f)
[ 1.337977] ata5.00: ATA-7: ST3750640AS, 3.AAE, max UDMA/133
[ 1.337981] ata5.00: 1465149168 sectors, multi 1: LBA48 NCQ (depth 31/32)
[ 1.344404] ata2.00: configured for UDMA/66
[ 1.352487] ata2.01: configured for UDMA/33
[ 1.354668] scsi 1:0:0:0: CD-ROM HL-DT-ST DVD-RAM GH22NP20 1.02 PQ: 0 ANSI: 5
[ 1.357955] sr1: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[ 1.358051] sr 1:0:0:0: Attached scsi CD-ROM sr1
[ 1.358110] sr 1:0:0:0: Attached scsi generic sg1 type 5
[ 1.358446] scsi 1:0:1:0: CD-ROM JLMS DVD-ROM XJ-HD166 DD05 PQ: 0 ANSI: 5
[ 1.360022] sr2: scsi3-mmc drive: 48x/48x cd/rw xa/form2 cdda tray
[ 1.360115] sr 1:0:1:0: Attached scsi CD-ROM sr2
[ 1.360167] sr 1:0:1:0: Attached scsi generic sg2 type 5

```

Then, below, we have the following:
```

 106.804519] ata2: lost interrupt (Status 0x51)
[ 106.820029] ata1: lost interrupt (Status 0x51)
[ 111.804529] ata2.00: qc timeout (cmd 0xa0)
[ 111.804539] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[ 111.804544] sr 1:0:0:0: CDB: Test Unit Ready: 00 00 00 00 00 00
[ 111.804558] ata2.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
[ 111.804560] res 51/20:03:00:00:00/00:00:00:00:00/a0 Emask 0x5 (timeout)
[ 111.804563] ata2.00: status: { DRDY ERR }
[ 111.804588] ata2: soft resetting link
[ 111.820039] ata1.00: qc timeout (cmd 0xa0)
[ 111.820048] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[ 111.820052] sr 0:0:0:0: CDB: Test Unit Ready: 00 00 00 00 00 00
[ 111.820065] ata1.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
[ 111.820066] res 51/20:03:00:00:00/00:00:00:00:00/a0 Emask 0x5 (timeout)
[ 111.820070] ata1.00: status: { DRDY ERR }
[ 111.820091] ata1: soft resetting link
[ 111.984348] ata1: nv_mode_filter: 0x739f&0x739f->0x739f, BIOS=0x7000 (0xc000c5c0) ACPI=0x701f (60:600:0x13)
[ 111.997835] ata1.00: configured for UDMA/33
[ 112.140403] ata2: nv_mode_filter: 0x1f39f&0x1f39f->0x1f39f, BIOS=0x1f000 (0xc000c5c0) ACPI=0x1f01f (30:60:0x1f)
[ 112.140410] ata2: nv_mode_filter: 0x739f&0x739f->0x739f, BIOS=0x7000 (0xc000c5c0) ACPI=0x701f (30:60:0x1f)
[ 112.157201] ata2.00: configured for UDMA/66
[ 112.157681] ata2.01: configured for UDMA/33
[ 117.000022] ata1.00: qc timeout (cmd 0xa0)
[ 117.000030] ata1.00: TEST_UNIT_READY failed (err_mask=0x5)
[ 117.000053] ata1: soft resetting link
[ 117.160018] ata2.00: qc timeout (cmd 0xa0)
[ 117.160024] ata2.00: TEST_UNIT_READY failed (err_mask=0x5)
[ 117.160045] ata2: soft resetting link

```
This continues for a couple of tries. Basically, the driver is missing interrupts, resetting the bus, checking status, not getting the answer it expects, and repeating the cycle.

 So, there is something going on with the interrupts or there is some bug in the IDE driver. 

Could you post the contents of /proc/interrupts?
Would like to see what, if anything is on the same IRQ as the IDE controllers.

---

### Post by DarinB on 2010-06-21
what code do i put into terminal to get what you need?

---

### Post by mk1w86 on 2010-06-21
> **DarinB said:**
> what code do i put into terminal to get what you need?

Post the output of:

```
cat /proc/interrupts
```

---

### Post by DarinB on 2010-06-21
darin@darin-desktop ~ $ cat /proc/interrupts
           CPU0       CPU1       
  0:         79          0   IO-APIC-edge      timer
  1:         13        871   IO-APIC-edge      i8042
  4:          4          0   IO-APIC-edge    
  6:          5          0   IO-APIC-edge      floppy
  7:          1          0   IO-APIC-edge      parport0
  8:          1          0   IO-APIC-edge      rtc0
  9:          0          0   IO-APIC-fasteoi   acpi
 12:     269795          0   IO-APIC-edge      i8042
 14:        371          0   IO-APIC-edge      pata_amd
 15:        934          0   IO-APIC-edge      pata_amd
 16:       5820          0   IO-APIC-fasteoi   nvidia
 18:         55     332767   IO-APIC-fasteoi   skge@pci:0000:06:0c.0
 20:          0          0   IO-APIC-fasteoi   ohci_hcd:usb2
 21:       6126     599347   IO-APIC-fasteoi   ehci_hcd:usb1
 22:       1255         57   IO-APIC-fasteoi   sata_nv
 23:      80834          0   IO-APIC-fasteoi   sata_nv, HDA Intel
NMI:          0          0   Non-maskable interrupts
LOC:     995159    1210137   Local timer interrupts
SPU:          0          0   Spurious interrupts
PMI:          0          0   Performance monitoring interrupts
PND:          0          0   Performance pending work
RES:     161041     124379   Rescheduling interrupts
CAL:        237       2039   Function call interrupts
TLB:       3650       4808   TLB shootdowns
TRM:          0          0   Thermal event interrupts
THR:          0          0   Threshold APIC interrupts
MCE:          0          0   Machine check exceptions
MCP:         18         18   Machine check polls
ERR:          2
MIS:          0

---

### Post by gsocker on 2010-06-21
Well, nothing is on the same IRQ as the IDE controller. Next guess would be something broken in the IRQ handling on your box or some corner case not handled correctly in the driver.

Does this happen as soon as you try to use the DVD drive or after a while?

---

### Post by DarinB on 2010-06-21
I am not sure what that means. as soon as i can put a dvd in and boot up it will show on my desktop but i will not be able to access it. after boot up the optical drives will open but then nothing happens when i put in a cd or dvd.
this worked fine for about 5 days no problem at all...
not sure if it was an update...if you see my posts i recreated the mount point in media that were not there. but as i am learning about this stuff it seems that is irrelevant. I think?
what next? some one on the linux mint forum thinks it is a bug but not high priority and may or may not get fixed...i wonder if i should go back to an earlier version of Linux mint built on karmic koala....
which worked fine. i like how well everything else works and a lot of the bugy stuff from karmic is gone. but then again i don't have a dvd writer or player either.

---

### Post by gsocker on 2010-06-21
You could try adding noapic to the kernel command line, and rebooting. Possibly also hpet=disable. 
If this doesn't help, the only other two options that come to mind are using an earlier version, or recompiling the kernel to see if the older EIDE driver works correctly.

You could also file a bug report.

The libata AMD/NVIDIA driver still has a few issues; one is failure to correctly detect 80 pin cables on some MB/BIOS combinations(mine is one), limiting the drives to UDMA/33.

---

### Post by DarinB on 2010-06-22
please tell me how to add these kernel lines? this is far above my skill level as well as how to add the line.
I do remember that no apic line used to come up every boot in past versions. i had no idea what that meant! maybe this is it.
and what are the down sides if this does not work? will it kill my system?  also i have never put in a bug report as well.
thanks this seems to be getting closer to a solution...

---

### Post by gsocker on 2010-06-22
When your computer is booting, after the BIOS finishes POST, "Press ESC to enter menu" will be displayed briefly - for 2 seconds, if I remember correctly. You may see "GRUB loading" instead.
Press ESC.

Press 'e' to edit, then go to the line which starts with "initrd".
Press the left arrow until the cursor is just to the right of "splash". 
Add "noapic". 
Press Ctrl-X to boot. 
If this works, then you can worry about adding it permanently.

---

### Post by DarinB on 2010-06-22
i put splashnoapic 
should it be splash noapic 
with no space it did not make a difference.
interesting when i made the mistake of putting on the line to the left of initrd/boot i got a kernel panic. 
ok now what?

---

### Post by DarinB on 2010-06-22
using splash noapic with the space
i got the dvd to burn an aptoncd using a dvd-r
i tried a dvd movie i got this error
> DBus error org.gtk.Private.RemoteVolumeMonitor.Failed: An operation is already pending

ok i tried another dvd and it plays but i have to jump through hoops to get through the menu and i have to go to places and mount it manually. and open it with vlc to play...
the cdrw does mount a cd automatically.
the cdrom does mount a cd automatically.
and now the dvd does as well but not sure why it did not the first time.
OK what do i do next...Captain???

---

### Post by DarinB on 2010-06-22
OK i rebooted again added the noapic and everything works great....
**now what do i do to make it permanent????**
also what happened why did it work originally and later not???
**and what will happen when i get a kernel upgrade in the future.**
i am very pleased so far i maybe ok!!!!

---

