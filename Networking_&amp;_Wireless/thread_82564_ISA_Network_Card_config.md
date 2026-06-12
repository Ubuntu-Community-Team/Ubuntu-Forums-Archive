---
title: "ISA Network Card config"
date: 2005-10-26
forum: Networking &amp; Wireless
---

### Post by RichardF on 2005-10-26
Hi.

During installing ubuntu 5.10 the installer said it could not find a network card.  The card is an ISA 3Com Etherlink III 3c905B.

Heres some things that I have done:

- ifconfig shows only the loop back (lo)
- dmesg | grep -i eth shows 
isapnp: Card '3Com 3C509B Etherlink III'

so i have located the driver (/lib/modules/2.6.12-9-386/kernel/drivers/net/3c905.ko)

- insmod 3c905 or modprobe 3c905 works! 
I can configure the card in 'Network Settings' (it works by pinging another machine on the network).   However once I reboot this disappears.

How can I configure ubuntu to load the module on startup ? 

Thanks in advance.
Rich.

---

### Post by mlomker on 2005-10-26
> 
- insmod 3c905 or modprobe 3c905 works! 
I can configure the card in 'Network Settings' (it works by pinging another machine on the network).   However once I reboot this disappears.


Add it to /etc/modules.

---

### Post by RichardF on 2005-10-27
Hi,

I added the module into /etc/modules.  But this had no effect after I restarted.  


# /etc/modules
#

lp
mousedev
psmouse
3c905


Any Ideas.
Thanks.

---

### Post by az on 2005-10-27
Open a terminal and type

dmesg

and post the whole output...

---

### Post by RichardF on 2005-10-27
Hi,

Heres the entire output from dmesg:

L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[4294668.931000] CPU: L2 Cache: 256K (64 bytes/line)
[4294668.931000] CPU: After all inits, caps: 0183f9ff c1c7f9ff 00000000 00000020 00000000 00000000 00000000
[4294668.931000] CPU: AMD Athlon(tm) Processor stepping 02
[4294668.931000] Enabling fast FPU save and restore... done.
[4294668.931000] Checking 'hlt' instruction... OK.
[4294668.935000] Checking for popad bug... OK.
[4294668.935000] checking if image is initramfs... it is
[4294669.769000] Freeing initrd memory: 4822k freed
[4294669.776000] ACPI: Looking for DSDT in initrd... not found!
[4294669.895000]  not found!
[4294669.902000] ACPI: setting ELCR to 0008 (from 1c88)
[4294669.904000] NET: Registered protocol family 16
[4294669.904000] EISA bus registered
[4294669.904000] ACPI: bus type pci registered
[4294669.920000] PCI: PCI BIOS revision 2.10 entry at 0xfb430, last bus=1
[4294669.920000] PCI: Using configuration type 1
[4294669.920000] mtrr: v2.0 (20020519)
[4294669.921000] ACPI: Subsystem revision 20050729
[4294669.935000] ACPI: Interpreter enabled
[4294669.935000] ACPI: Using PIC for interrupt routing
[4294669.935000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[4294669.935000] PCI: Probing PCI hardware (bus 00)
[4294669.936000] ACPI: Assume root bridge [\_SB_.PCI0] segment is 0
[4294669.936000] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[4294669.939000] Boot video device is 0000:01:00.0
[4294669.977000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[4294669.979000] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 11 *12 14 15)
[4294669.979000] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 *10 11 12 14 15)
[4294669.980000] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 10 *11 12 14 15)
[4294669.981000] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 *7 10 11 12 14 15)
[4294669.984000] Linux Plug and Play Support v0.97 (c) Adam Belay
[4294669.984000] pnp: PnP ACPI init
[4294669.988000] pnp: PnP ACPI: found 8 devices
[4294669.988000] PnPBIOS: Disabled by ACPI PNP
[4294669.989000] PCI: Using ACPI for IRQ routing
[4294669.989000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[4294670.025000] audit: initializing netlink socket (disabled)
[4294670.025000] audit: initialized
[4294670.025000] VFS: Disk quotas dquot_6.5.1
[4294670.026000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[4294670.026000] devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
[4294670.026000] devfs: boot_options: 0x0
[4294670.026000] Initializing Cryptographic API
[4294670.026000] PCI: Disabling Via external APIC routing
[4294670.026000] isapnp: Scanning for PnP cards...
[4294670.121000] isapnp: Card '3Com 3C509B EtherLink III'
[4294670.121000] isapnp: 1 Plug & Play card detected total
[4294670.155000] PNP: PS/2 controller doesn't have AUX irq; using default 0xc
[4294670.155000] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 112
[4294670.155000] serio: i8042 AUX port at 0x60,0x64 irq 12
[4294670.156000] serio: i8042 KBD port at 0x60,0x64 irq 1


[4294670.156000] Serial: 8250/16550 driver $Revision: 1.90 $ 54 ports, IRQ sharing enabled
[4294670.160000] io scheduler noop registered
[4294670.160000] io scheduler anticipatory registered
[4294670.160000] io scheduler deadline registered
[4294670.160000] io scheduler cfq registered
[4294670.160000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[4294670.161000] EISA: Probing bus 0 at eisa.0
[4294670.161000] Cannot allocate resource for EISA slot 4
[4294670.161000] Cannot allocate resource for EISA slot 5
[4294670.161000] Cannot allocate resource for EISA slot 6
[4294670.161000] EISA: Detected 0 cards.
[4294670.161000] NET: Registered protocol family 2
[4294670.170000] IP: routing cache hash table of 4096 buckets, 32Kbytes
[4294670.170000] TCP established hash table entries: 32768 (order: 6, 262144 bytes)
[4294670.171000] TCP bind hash table entries: 32768 (order: 5, 131072 bytes)
[4294670.172000] TCP: Hash tables configured (established 32768 bind 32768)
[4294670.172000] NET: Registered protocol family 8
[4294670.172000] NET: Registered protocol family 20
[4294670.172000] ACPI wakeup devices: 
[4294670.172000] PCI0 USB0 USB1 MODM 
[4294670.172000] ACPI: (supports S0 S3 S4 S5)
[4294670.173000] Freeing unused kernel memory: 224k freed
[4294670.202000] vga16fb: initializing
[4294670.202000] vga16fb: mapped to 0xc00a0000
[4294670.322000] Console: switching to colour frame buffer device 80x30
[4294670.322000] fb0: VGA16 VGA frame buffer device
[4294670.348000] input: AT Translated Set 2 keyboard on isa0060/serio0
[4294671.471000] Capability LSM initialized
[4294671.495000] NET: Registered protocol family 1
[4294671.518000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[4294671.518000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[4294671.518000] ACPI: bus type ide registered
[4294671.531000] VP_IDE: IDE controller at PCI slot 0000:00:07.1
[4294671.531000] PCI: Via IRQ fixup for 0000:00:07.1, from 255 to 0
[4294671.531000] VP_IDE: chipset revision 16
[4294671.531000] VP_IDE: not 100% native mode: will probe irqs later
[4294671.531000] VP_IDE: VIA vt82c686a (rev 22) IDE UDMA66 controller on pci0000:00:07.1
[4294671.531000]     ide0: BM-DMA at 0xa000-0xa007, BIOS settings: hda:DMA, hdb:pio
[4294671.531000]     ide1: BM-DMA at 0xa008-0xa00f, BIOS settings: hdc:pio, hdd:pio
[4294671.531000] Probing IDE interface ide0...
[4294672.323000] hda: SONY CDU4811, ATAPI CD/DVD-ROM drive
[4294672.629000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[4294672.629000] Probing IDE interface ide1...
[4294673.115000] hdc: SONY CD-RW CRX140E, ATAPI CD/DVD-ROM drive
[4294673.727000] ide1 at 0x170-0x177,0x376 on irq 15
[4294673.727000] Probing IDE interface ide2...
[4294674.240000] Probing IDE interface ide3...
[4294674.753000] Probing IDE interface ide4...
[4294675.265000] Probing IDE interface ide5...
[4294675.786000] hda: ATAPI 48X CD-ROM drive, 120kB Cache
[4294675.786000] Uniform CD-ROM driver Revision: 3.20
[4294675.789000] hdc: ATAPI 32X CD-ROM CD-R/RW drive, 4096kB Cache
[4294676.487000] usbcore: registered new driver usbfs
[4294676.487000] usbcore: registered new driver hub
[4294676.489000] USB Universal Host Controller Interface driver v2.2
[4294676.490000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 7
[4294676.490000] PCI: setting IRQ 7 as level-triggered
[4294676.490000] ACPI: PCI Interrupt 0000:00:07.2[D] -> Link [LNKD] -> GSI 7 (level, low) -> IRQ 7
[4294676.490000] uhci_hcd 0000:00:07.2: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
[4294676.552000] uhci_hcd 0000:00:07.2: new USB bus registered, assigned bus number 1
[4294676.552000] uhci_hcd 0000:00:07.2: irq 7, io base 0x0000a400
[4294676.552000] hub 1-0:1.0: USB hub found
[4294676.552000] hub 1-0:1.0: 2 ports detected
[4294676.555000] ACPI: PCI Interrupt 0000:00:07.3[D] -> Link [LNKD] -> GSI 7 (level, low) -> IRQ 7
[4294676.555000] uhci_hcd 0000:00:07.3: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (#2)
[4294676.617000] uhci_hcd 0000:00:07.3: new USB bus registered, assigned bus number 2
[4294676.617000] uhci_hcd 0000:00:07.3: irq 7, io base 0x0000a800
[4294676.617000] hub 2-0:1.0: USB hub found
[4294676.617000] hub 2-0:1.0: 2 ports detected
[4294676.731000] HPT370: IDE controller at PCI slot 0000:00:13.0
[4294676.732000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[4294676.732000] PCI: setting IRQ 11 as level-triggered
[4294676.732000] ACPI: PCI Interrupt 0000:00:13.0[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[4294676.732000] HPT370: chipset revision 3
[4294676.732000] HPT37X: using 33MHz PCI clock
[4294676.732000] HPT370: 100% native mode on irq 11
[4294676.732000]     ide2: BM-DMA at 0xc400-0xc407, BIOS settings: hde:DMA, hdf:DMA
[4294676.732000]     ide3: BM-DMA at 0xc408-0xc40f, BIOS settings: hdg:pio, hdh:pio
[4294676.732000] Probing IDE interface ide2...
[4294676.741000] usb 1-1: new full speed USB device using uhci_hcd and address 2
[4294676.841000] hub 1-1:1.0: USB hub found
[4294676.845000] hub 1-1:1.0: 4 ports detected
[4294677.000000] hde: IBM-DTLA-307030, ATA DISK drive
[4294677.127000] usb 1-2: new low speed USB device using uhci_hcd and address 3
[4294677.256000] hdf: IC35L040AVVN07-0, ATA DISK drive
[4294677.307000] ide2 at 0xb400-0xb407,0xb802 on irq 11
[4294677.307000] Probing IDE interface ide3...
[4294677.606000] usb 1-1.3: new low speed USB device using uhci_hcd and address 4
[4294679.894000] usbcore: registered new driver hiddev
[4294679.913000] input: USB HID v1.10 Mouse [Logitech USB Mouse] on usb-0000:00:07.2-2
[4294679.931000] input: USB HID v1.10 Keyboard [CHESEN PS2 to USB Converter] on usb-0000:00:07.2-1.3
[4294679.961000] input: USB HID v1.10 Mouse [CHESEN PS2 to USB Converter] on usb-0000:00:07.2-1.3
[4294679.961000] usbcore: registered new driver usbhid
[4294679.961000] drivers/usb/input/hid-core.c: v2.01:USB HID core driver
[4294680.039000] hde: max request size: 128KiB
[4294680.060000] hde: 60036480 sectors (30738 MB) w/1916KiB Cache, CHS=59560/16/63, UDMA(66)
[4294680.060000] hde: cache flushes not supported
[4294680.060000]  /dev/ide/host2/bus0/target0/lun0: p1 p2 p3
[4294680.076000] hdf: max request size: 128KiB
[4294680.086000] hdf: 80418240 sectors (41174 MB) w/1863KiB Cache, CHS=65535/16/63, UDMA(100)
[4294680.086000] hdf: cache flushes supported
[4294680.086000]  /dev/ide/host2/bus0/target1/lun0: p1 p2 p3 < p5 >
[4294680.895000] ACPI: CPU0 (power states: C1[C1] C2[C2])
[4294680.895000] ACPI: Processor [CPU0] (supports 2 throttling states)
[4294681.145000] Attempting manual resume
[4294681.158000] swsusp: Suspend partition has wrong signature?
[4294681.216000] kjournald starting.  Commit interval 5 seconds
[4294681.216000] EXT3-fs: mounted filesystem with ordered data mode.
[4294682.375000] md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294687.786000] Adding 1076312k swap on /dev/hdf5.  Priority:-1 extents:1
[4294688.064000] EXT3 FS on hdf2, internal journal
[4294694.914000] parport_pc: VIA 686A/8231 detected
[4294694.914000] parport_pc: probing current configuration
[4294694.914000] parport_pc: Current parallel port base: 0x0
[4294694.914000] parport_pc: VIA parallel port disabled in BIOS
[4294694.941000] lp: driver loaded but no devices found
[4294695.014000] mice: PS/2 mouse device common for all mice
[4294699.085000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[4294704.515000] cdrom: open failed.
[4294704.519000] cdrom: open failed.
[4294706.871000] Linux agpgart interface v0.101 (c) Dave Jones
[4294706.892000] agpgart: Detected VIA Twister-K/KT133x/KM133 chipset
[4294706.935000] agpgart: AGP aperture is 64M @ 0xd0000000
[4294707.135000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[4294707.148000] shpchp: acpi_shpchprm:\_SB_.PCI0 evaluate _BBN fail=0x5
[4294707.148000] shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x5
[4294708.676000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 10
[4294708.676000] PCI: setting IRQ 10 as level-triggered
[4294708.676000] ACPI: PCI Interrupt 0000:00:0f.0[A] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
[4294710.259000] gameport: EMU10K1 is pci0000:00:0f.1/gameport0, io 0xb000, speed 1242kHz
[4294712.902000] Real Time Clock Driver v1.12
[4294713.019000] input: PC Speaker
[4294713.374000] Floppy drive(s): fd0 is 1.44M
[4294713.388000] FDC 0 is a post-1991 82077
[4294714.097000] ts: Compaq touchscreen protocol output
[4294717.381000] ACPI: Power Button (FF) [PWRF]
[4294717.381000] ACPI: Power Button (CM) [PWRB]
[4294717.621000] ibm_acpi: ec object not found
[4294727.478000] [drm] Initialized drm 1.0.0 20040925
[4294727.495000] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 12
[4294727.495000] PCI: setting IRQ 12 as level-triggered
[4294727.495000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 12 (level, low) -> IRQ 12
[4294727.512000] [drm] Initialized r128 2.5.0 20030725 on minor 0: ATI Technologies Inc Rage 128 PF/PRO AGP 4x TMDS
[4294727.514000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[4294727.514000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 1x mode
[4294727.514000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 1x mode
[4294728.498000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[4294728.498000] apm: overridden by ACPI.
[4294729.215000] powernow: No powernow capabilities detected
[4294729.585000] Bluetooth: Core ver 2.7
[4294729.585000] NET: Registered protocol family 31
[4294729.585000] Bluetooth: HCI device and connection manager initialized
[4294729.585000] Bluetooth: HCI socket layer initialized
[4294729.685000] Bluetooth: L2CAP ver 2.7
[4294729.685000] Bluetooth: L2CAP socket layer initialized
[4294729.745000] Bluetooth: RFCOMM ver 1.5
[4294729.745000] Bluetooth: RFCOMM socket layer initialized
[4294729.745000] Bluetooth: RFCOMM TTY layer initialized
[4294745.512000] NET: Registered protocol family 10
[4294745.512000] Disabled Privacy Extensions on device c02eb280(lo)
[4294745.512000] IPv6 over IPv4 tunneling driver
[4295197.125000] cdrom: open failed.
[4295201.504000] cdrom: open failed.
[4295484.156000] Warning: /proc/ide/hd?/settings interface is obsolete, and will be removed soon!
[4295484.586000] NTFS driver 2.1.22 [Flags: R/O MODULE].
[4295484.632000] NTFS volume version 3.0.
[4295485.205000] NTFS volume version 3.0.
[4295485.338000] NTFS volume version 3.0.
[4295485.469000] NTFS volume version 3.0.
[4295563.424000] NTFS volume version 3.0.
[4295589.977000] NTFS-fs error (device hde1): ntfs_ucstonls(): Unicode name contains characters that cannot be converted to character set cp437.
[4295589.977000] NTFS-fs error (device hde1): ntfs_ucstonls(): Unicode name contains characters that cannot be converted to character set cp437.
[4295590.434000] NTFS-fs error (device hde1): ntfs_ucstonls(): Unicode name contains characters that cannot be converted to character set cp437.
[4295751.605000] NTFS volume version 3.0.
[4298207.460000] NTFS volume version 3.0.
[4298517.404000] NTFS volume version 3.0.
[4301154.536000] usb 2-1: new full speed USB device using uhci_hcd and address 2
[4301155.539000] SCSI subsystem initialized
[4301155.550000] Initializing USB Mass Storage driver...
[4301155.565000] scsi0 : SCSI emulation for USB Mass Storage devices
[4301155.599000] usb-storage: device found at 2
[4301155.599000] usb-storage: waiting for device to settle before scanning
[4301155.599000] usbcore: registered new driver usb-storage
[4301155.599000] USB Mass Storage support registered.
[4301160.612000]   Vendor:           Model: USB DRIVE         Rev: 1.13
[4301160.613000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[4301160.674000] usb-storage: device scan complete
[4301161.211000] SCSI device sda: 4029440 512-byte hdwr sectors (2063 MB)
[4301161.232000] sda: Write Protect is off
[4301161.232000] sda: Mode Sense: 23 00 00 00
[4301161.232000] sda: assuming drive cache: write through
[4301161.308000] SCSI device sda: 4029440 512-byte hdwr sectors (2063 MB)
[4301161.326000] sda: Write Protect is off
[4301161.326000] sda: Mode Sense: 23 00 00 00
[4301161.326000] sda: assuming drive cache: write through
[4301161.326000]  /dev/scsi/host0/bus0/target0/lun0: p1
[4301161.363000] Attached scsi removable disk sda at scsi0, channel 0, id 0, lun 0
[4301162.999000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[4303100.740000] NTFS-fs error (device hde2): ntfs_ucstonls(): Unicode name contains characters that cannot be converted to character set cp437.

---

### Post by az on 2005-10-27
1.  If you have isapnptools installed, remove it.  You do not need it.

2.  lspci will tell you the irq of your isa card.  It may be in conflict with some other hardware.  I had the same problem once and the fact that it does not spit out an error threw me off.  Are you able to manually assign an irq to that device in your bios?  (Or manually assign the irq to isa, then the other device will get another one.)  What is the make of your motherboard?

---

### Post by OCFan on 2006-06-29
[QUOTE=RichardF] so i have located the driver (/lib/modules/2.6.12-9-386/kernel/drivers/net/3c905.ko)
[/QUOTE]

I know this thread is terribly old, but I am in need of the 3c905.ko driver, and I can't seem to find it anywhere. Could you send it to me? (I'll pm you my e-mail address if you can).
Regards,
Joe

---

