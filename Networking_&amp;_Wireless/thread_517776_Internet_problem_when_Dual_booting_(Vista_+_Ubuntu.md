---
title: "Internet problem when Dual booting (Vista + Ubuntu Feisty)"
date: 2007-08-05
forum: Networking &amp; Wireless
---

### Post by rubperezt on 2007-08-05
Hi all, I recently installed Ubuntu 7.04, everything worked well for a while, but as soon as I installed Windows Vista and used my internet connection for the first time, my internet connection stopped working on Ubuntu.
I reinstalled everything from scratch several times, Ubuntu works perfectly till i use my internet on Vista.

My router is a Westell Versalink 327w.

Any help would be greatly appreciated.

I hate Vista...

---

### Post by noob12 on 2007-08-05
OK.  Can you elaborate a bit?  We need more information to help you out.

Is it your wireless or wired connection that breaks?

Can you please provide the output of these commands

```

lspci -nn

dmesg

sudo lshw -C network

```

This will give us a basic idea of what you have and next steps to diagnosing this.

If you have a USB-based adapter, please replace the first line by **lsusb**

---

### Post by rubperezt on 2007-08-05
Im using a wired connection.

EDIT: At the same time, im using a laptop wirelessly and it runs just fine, even when Ubuntu is loaded. The laptop is running OS X. 

sudo lshw -C network:```

  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 3
       bus info: pci@02:03.0
       logical name: eth0
       version: 10
       serial: 00:13:d3:56:de:b8
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: ioport:da00-daff iomemory:fddfc000-fddfc0ff irq:17


```


dmesg: ```


[    1.304000] io scheduler noop registered
[    1.304000] io scheduler anticipatory registered
[    1.304000] io scheduler deadline registered
[    1.304000] io scheduler cfq registered (default)
[    1.352000] PCI: Setting latency timer of device 0000:00:02.0 to 64
[    1.352000] assign_interrupt_mode Found MSI capability
[    1.352000] Allocate Port Service[0000:00:02.0:pcie00]
[    1.352000] isapnp: Scanning for PnP cards...
[    1.704000] isapnp: No Plug & Play device found
[    1.724000] Real Time Clock Driver v1.12ac
[    1.724000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    1.724000] mice: PS/2 mouse device common for all mice
[    1.724000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    1.724000] input: Macintosh mouse button emulation as /class/input/input0
[    1.724000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[    1.724000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[    1.724000] PNP: PS/2 Controller [PNP0f13:PS2M] at 0x60,0x64 irq 12
[    1.724000] PNP: PS/2 controller doesn't have KBD irq; using default 1
[    1.728000] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.728000] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.728000] EISA: Probing bus 0 at eisa.0
[    1.728000] Cannot allocate resource for EISA slot 4
[    1.728000] EISA: Detected 0 cards.
[    1.760000] TCP cubic registered
[    1.760000] NET: Registered protocol family 1
[    1.760000] Starting balanced_irq
[    1.760000] Using IPI No-Shortcut mode
[    1.760000] ACPI: (supports S0 S1 S3 S4 S5)
[    1.760000]   Magic number: 3:618:758
[    1.760000] Freeing unused kernel memory: 328k freed
[    1.764000] Time: acpi_pm clocksource has been installed.
[    2.952000] Capability LSM initialized
[    2.988000] ACPI: Processor [CPU0] (supports 8 throttling states)
[    2.988000] ACPI: Processor [CPU1] (supports 8 throttling states)
[    3.384000] usbcore: registered new interface driver usbfs
[    3.384000] usbcore: registered new interface driver hub
[    3.384000] usbcore: registered new device driver usb
[    3.392000] ACPI: PCI Interrupt 0000:00:13.2[A] -> GSI 19 (level, low) -> IRQ 16
[    3.392000] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    3.392000] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 1
[    3.392000] ehci_hcd 0000:00:13.2: irq 16, io mem 0xfe02c000
[    3.392000] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.392000] usb usb1: configuration #1 chosen from 1 choice
[    3.392000] hub 1-0:1.0: USB hub found
[    3.392000] hub 1-0:1.0: 8 ports detected
[    3.424000] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[    3.432000] USB Universal Host Controller Interface driver v3.0
[    3.464000] ieee1394: Initialized config rom entry `ip1394'
[    3.500000] ACPI: PCI Interrupt 0000:02:02.2[C] -> GSI 20 (level, low) -> IRQ 17
[    3.500000] ehci_hcd 0000:02:02.2: EHCI Host Controller
[    3.500000] ehci_hcd 0000:02:02.2: new USB bus registered, assigned bus number 2
[    3.500000] ehci_hcd 0000:02:02.2: irq 17, io mem 0xfddfe000
[    3.500000] ehci_hcd 0000:02:02.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.500000] usb usb2: configuration #1 chosen from 1 choice
[    3.500000] hub 2-0:1.0: USB hub found
[    3.500000] hub 2-0:1.0: 4 ports detected
[    3.508000] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 19 (level, low) -> IRQ 16
[    3.508000] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    3.508000] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    3.608000] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 3
[    3.608000] ohci_hcd 0000:00:13.0: irq 16, io mem 0xfe02e000
[    3.672000] usb usb3: configuration #1 chosen from 1 choice
[    3.672000] hub 3-0:1.0: USB hub found
[    3.672000] hub 3-0:1.0: 4 ports detected
[    3.780000] ACPI: PCI Interrupt 0000:00:13.1[A] -> GSI 19 (level, low) -> IRQ 16
[    3.780000] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    3.780000] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 4
[    3.780000] ohci_hcd 0000:00:13.1: irq 16, io mem 0xfe02d000
[    3.840000] usb usb4: configuration #1 chosen from 1 choice
[    3.844000] hub 4-0:1.0: USB hub found
[    3.844000] hub 4-0:1.0: 4 ports detected
[    3.956000] ACPI: PCI Interrupt 0000:02:02.0[A] -> GSI 22 (level, low) -> IRQ 18
[    3.956000] uhci_hcd 0000:02:02.0: UHCI Host Controller
[    3.956000] uhci_hcd 0000:02:02.0: new USB bus registered, assigned bus number 5
[    3.956000] uhci_hcd 0000:02:02.0: irq 18, io base 0x0000dd00
[    3.956000] usb usb5: configuration #1 chosen from 1 choice
[    3.956000] SCSI subsystem initialized
[    3.956000] hub 5-0:1.0: USB hub found
[    3.956000] hub 5-0:1.0: 2 ports detected
[    3.960000] libata version 2.20 loaded.
[    4.064000] ACPI: PCI Interrupt 0000:02:02.1[B] -> GSI 23 (level, low) -> IRQ 19
[    4.064000] uhci_hcd 0000:02:02.1: UHCI Host Controller
[    4.064000] uhci_hcd 0000:02:02.1: new USB bus registered, assigned bus number 6
[    4.064000] uhci_hcd 0000:02:02.1: irq 19, io base 0x0000dc00
[    4.064000] usb usb6: configuration #1 chosen from 1 choice
[    4.064000] hub 6-0:1.0: USB hub found
[    4.064000] hub 6-0:1.0: 2 ports detected
[    4.120000] usb 2-1: new high speed USB device using ehci_hcd and address 2
[    4.172000] 8139cp 0000:02:03.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[    4.172000] 8139cp 0000:02:03.0: Try the "8139too" driver instead.
[    4.172000] ATIIXP: IDE controller at PCI slot 0000:00:14.1
[    4.172000] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 20
[    4.172000] ATIIXP: chipset revision 0
[    4.172000] ATIIXP: not 100% native mode: will probe irqs later
[    4.172000]     ide0: BM-DMA at 0xf800-0xf807, BIOS settings: hda:pio, hdb:pio
[    4.172000]     ide1: BM-DMA at 0xf808-0xf80f, BIOS settings: hdc:pio, hdd:pio
[    4.172000] Probing IDE interface ide0...
[    4.180000] 8139too Fast Ethernet driver 0.9.28
[    4.272000] usb 2-1: configuration #1 chosen from 1 choice
[    4.744000] Probing IDE interface ide1...
[    5.092000] usb 4-4: new full speed USB device using ohci_hcd and address 2
[    5.296000] usb 4-4: configuration #1 chosen from 1 choice
[    5.488000] hdc: HP DVD Writer 840b, ATAPI CD/DVD-ROM drive
[    5.980000] usb 6-1: new full speed USB device using uhci_hcd and address 2
[    6.148000] usb 6-1: configuration #1 chosen from 1 choice
[    6.276000] hdd: ASUS DVD-E616P3H, ATAPI CD/DVD-ROM drive
[    6.336000] ide1 at 0x170-0x177,0x376 on irq 15
[    6.340000] ACPI: PCI Interrupt 0000:02:02.3[A] -> GSI 22 (level, low) -> IRQ 18
[    6.392000] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[18]  MMIO=[fddfd000-fddfd7ff]  Max Packet=[2]  IR/IT contexts=[4/8]
[    6.396000] ohci1394: fw-host0: Serial EEPROM has suspicious values, attempting to setting max_packet_size to 512 bytes
[    6.396000] usb 6-2: new full speed USB device using uhci_hcd and address 3
[    6.396000] ACPI: PCI Interrupt 0000:02:04.0[A] -> GSI 21 (level, low) -> IRQ 21
[    6.448000] ohci1394: fw-host1: OHCI-1394 1.1 (PCI): IRQ=[21]  MMIO=[fddfb000-fddfb7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    6.452000] ACPI: PCI Interrupt 0000:02:03.0[A] -> GSI 20 (level, low) -> IRQ 17
[    6.452000] eth0: RealTek RTL8139 at 0xf884c000, 00:13:d3:56:de:b8, IRQ 17
[    6.452000] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[    6.452000] sata_sil 0000:00:12.0: version 2.2
[    6.452000] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 22 (level, low) -> IRQ 18
[    6.452000] ata1: SATA max UDMA/100 cmd 0xf8856080 ctl 0xf885608a bmdma 0xf8856000 irq 18
[    6.452000] ata2: SATA max UDMA/100 cmd 0xf88560c0 ctl 0xf88560ca bmdma 0xf8856008 irq 18
[    6.452000] scsi0 : sata_sil
[    6.596000] usb 6-2: configuration #1 chosen from 1 choice
[    6.904000] usb 4-1: new full speed USB device using ohci_hcd and address 3
[    6.920000] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    6.936000] ata1.00: ata_hpa_resize 1: sectors = 145226112, hpa_sectors = 145226112
[    6.936000] ata1.00: ATA-7: WDC WD740ADFD-00NLR1, 20.07P20, max UDMA/133
[    6.936000] ata1.00: 145226112 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    6.948000] ata1.00: ata_hpa_resize 1: sectors = 145226112, hpa_sectors = 145226112
[    6.948000] ata1.00: configured for UDMA/100
[    6.948000] scsi1 : sata_sil
[    7.104000] usb 4-1: configuration #1 chosen from 1 choice
[    7.104000] hub 4-1:1.0: USB hub found
[    7.108000] hub 4-1:1.0: 4 ports detected
[    7.224000] usbcore: registered new interface driver libusual
[    7.228000] Initializing USB Mass Storage driver...
[    7.228000] scsi2 : SCSI emulation for USB Mass Storage devices
[    7.228000] usb-storage: device found at 2
[    7.228000] usb-storage: waiting for device to settle before scanning
[    7.416000] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    7.432000] ata2.00: ATA-7: ST3250823AS, 3.03, max UDMA/100
[    7.432000] ata2.00: 488397168 sectors, multi 16: LBA48 
[    7.444000] ata2.00: configured for UDMA/100
[    7.444000] scsi 0:0:0:0: Direct-Access     ATA      WDC WD740ADFD-00 20.0 PQ: 0 ANSI: 5
[    7.444000] scsi 1:0:0:0: Direct-Access     ATA      ST3250823AS      3.03 PQ: 0 ANSI: 5
[    7.452000] hdc: ATAPI 40X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(33)
[    7.452000] Uniform CD-ROM driver Revision: 3.20
[    7.456000] usb 4-1.1: new low speed USB device using ohci_hcd and address 4
[    7.456000] SCSI device sda: 145226112 512-byte hdwr sectors (74356 MB)
[    7.456000] sda: Write Protect is off
[    7.456000] sda: Mode Sense: 00 3a 00 00
[    7.456000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.456000] SCSI device sda: 145226112 512-byte hdwr sectors (74356 MB)
[    7.456000] sda: Write Protect is off
[    7.456000] sda: Mode Sense: 00 3a 00 00
[    7.456000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.456000]  sda:<6>hdd: ATAPI 40X DVD-ROM drive, 512kB Cache, UDMA(33)
[    7.468000]  sda1 sda2 sda3
[    7.484000] sd 0:0:0:0: Attached scsi disk sda
[    7.484000] SCSI device sdb: 488397168 512-byte hdwr sectors (250059 MB)
[    7.484000] sdb: Write Protect is off
[    7.484000] sdb: Mode Sense: 00 3a 00 00
[    7.484000] SCSI device sdb: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.484000] SCSI device sdb: 488397168 512-byte hdwr sectors (250059 MB)
[    7.484000] sdb: Write Protect is off
[    7.484000] sdb: Mode Sense: 00 3a 00 00
[    7.484000] SCSI device sdb: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.484000]  sdb:
[    7.504000] sd 1:0:0:0: Attached scsi disk sdb
[    7.508000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    7.508000] sd 1:0:0:0: Attached scsi generic sg1 type 0
[    7.572000] usb 4-1.1: configuration #1 chosen from 1 choice
[    7.676000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[001106005350d195]
[    7.720000] Attempting manual resume
[    7.720000] swsusp: Resume From Partition 8:3
[    7.720000] PM: Checking swsusp image.
[    7.720000] PM: Resume from disk failed.
[    7.736000] kjournald starting.  Commit interval 5 seconds
[    7.736000] EXT3-fs: mounted filesystem with ordered data mode.
[    7.808000] usb 4-1.3: new low speed USB device using ohci_hcd and address 5
[    7.952000] ieee1394: Host added: ID:BUS[1-00:1023]  GUID[0010dc0000b83eea]
[   10.900000] usb 4-1.3: device descriptor read/64, error -110
[   12.056000] usb 4-1.3: configuration #1 chosen from 1 choice
[   12.232000] usb-storage: device scan complete
[   12.236000] scsi 2:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
[   12.244000] scsi 2:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
[   12.248000] scsi 2:0:0:2: Direct-Access     Generic  USB SM Reader    1.02 PQ: 0 ANSI: 0
[   12.256000] scsi 2:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0
[   12.264000] sd 2:0:0:0: Attached scsi removable disk sdc
[   12.264000] sd 2:0:0:0: Attached scsi generic sg2 type 0
[   12.276000] sd 2:0:0:1: Attached scsi removable disk sdd
[   12.276000] sd 2:0:0:1: Attached scsi generic sg3 type 0
[   12.284000] sd 2:0:0:2: Attached scsi removable disk sde
[   12.284000] sd 2:0:0:2: Attached scsi generic sg4 type 0
[   12.288000] usb 4-1.4: new full speed USB device using ohci_hcd and address 6
[   12.296000] sd 2:0:0:3: Attached scsi removable disk sdf
[   12.296000] sd 2:0:0:3: Attached scsi generic sg5 type 0
[   12.408000] usb 4-1.4: configuration #1 chosen from 1 choice
[   12.640000] usb 4-1.2: new full speed USB device using ohci_hcd and address 7
[   12.748000] usb 4-1.2: not running at top speed; connect to a high speed hub
[   12.760000] usb 4-1.2: configuration #1 chosen from 1 choice
[   12.764000] scsi3 : SCSI emulation for USB Mass Storage devices
[   12.764000] usb-storage: device found at 7
[   12.764000] usb-storage: waiting for device to settle before scanning
[   12.764000] usbcore: registered new interface driver usb-storage
[   12.764000] usbcore: registered new interface driver hiddev
[   12.764000] USB Mass Storage support registered.
[   12.828000] input: Gaming Keyboard as /class/input/input1
[   12.828000] input: USB HID v1.10 Keyboard [Gaming Keyboard] on usb-0000:00:13.1-1.1
[   12.840000] input: Gaming Keyboard as /class/input/input2
[   12.840000] input,hiddev96: USB HID v1.10 Device [Gaming Keyboard] on usb-0000:00:13.1-1.1
[   13.160000] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[   13.204000] hiddev97: USB HID v1.10 Device [American Power Conversion Back-UPS BR  800 FW:9.o2 .D USB FW:o2 ] on usb-0000:00:13.1-1.3
[   13.212000] input: G11 Keyboard as /class/input/input3
[   13.212000] input,hiddev98: USB HID v1.11 Keypad [G11 Keyboard] on usb-0000:00:13.1-1.4
[   13.212000] usbcore: registered new interface driver usbhid
[   13.212000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   14.312000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   14.316000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   14.364000] piix4_smbus 0000:00:14.0: Found 0000:00:14.0 device
[   14.440000] Linux video capture interface: v2.00
[   14.484000] NET: Registered protocol family 17
[   14.508000] ivtv:  ==================== START INIT IVTV ====================
[   14.508000] ivtv:  version 0.10.1 (tagged release) loading
[   14.508000] ivtv:  Linux version: 2.6.20-16-generic SMP mod_unload 586 
[   14.508000] ivtv:  In case of problems please include the debug info between
[   14.508000] ivtv:  the START INIT IVTV and END INIT IVTV lines, along with
[   14.508000] ivtv:  any module options, when mailing the ivtv-users mailinglist.
[   14.508000] ivtv0: Unknown card: vendor/device: 4444/0016
[   14.508000] ivtv0:               subsystem vendor/device: 1043/4b2e
[   14.508000] ivtv0:               cx23416 based
[   14.508000] ivtv0: Defaulting to Hauppauge WinTV PVR-150 card
[   14.508000] ivtv0: Please mail the vendor/device and subsystem vendor/device IDs and what kind of
[   14.508000] ivtv0: card you have to the ivtv-devel mailinglist (www.ivtvdriver.org)
[   14.508000] ivtv0: Prefix your subject line with [UNKNOWN CARD].
[   14.660000] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 20 (level, low) -> IRQ 17
[   14.672000] Linux agpgart interface v0.102 (c) Dave Jones
[   14.744000] input: PC Speaker as /class/input/input4
[   14.744000] usbcore: registered new interface driver xpad
[   14.744000] drivers/usb/input/xpad.c: driver for Xbox controllers v0.1.6
[   14.948000] ubuntu/media/gspcav1/gspca_core.c: USB SPCA5XX camera found.(ZC3XX) 
[   14.964000] parport: PnPBIOS parport detected.
[   14.964000] parport0: PC-style at 0x378, irq 7 [PCSPP,EPP]
[   15.188000] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 2 if 1 alt 0 proto 2 vid 0x04B8 pid 0x0820
[   15.340000] ivtv0: loaded v4l-cx2341x-enc.fw firmware (262144 bytes)
[   15.556000] ivtv0: Encoder revision: 0x02050032
[   15.556000] ivtv0: Recommended firmware version is 0x02060039.
[   15.568000] tveeprom 1-0050: Huh, no eeprom present (err=-121)?
[   15.568000] tveeprom 1-0050: Encountered bad packet header [02]. Corrupt or not a Hauppauge eeprom.
[   15.568000] ivtv0: Invalid EEPROM
[   15.588000] tuner 1-0043: chip found @ 0x86 (ivtv i2c driver #0)
[   15.588000] tda9887 1-0043: tda988[5/6/7] found @ 0x43 (tuner)
[   15.592000] tuner 1-0060: All bytes are equal. It is not a TEA5767
[   15.592000] tuner 1-0060: chip found @ 0xc0 (ivtv i2c driver #0)
[   15.616000] input: ImPS/2 Logitech Wheel Mouse as /class/input/input5
[   15.632000] cx25840 1-0044: cx25843-23 found @ 0x88 (ivtv i2c driver #0)
[   15.660000] usbcore: registered new interface driver gspca
[   15.660000] ubuntu/media/gspcav1/gspca_core.c: gspca driver 01.00.12 registered
[   15.660000] usbcore: registered new interface driver usblp
[   15.660000] drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
[   15.772000] usbcore: registered new interface driver snd-usb-audio
[   17.776000] usb-storage: device scan complete
[   17.784000] scsi 3:0:0:0: Direct-Access     SanDisk  U3 Cruzer Micro  3.27 PQ: 0 ANSI: 2
[   17.792000] SCSI device sdg: 8015502 512-byte hdwr sectors (4104 MB)
[   17.800000] sdg: Write Protect is off
[   17.800000] sdg: Mode Sense: 03 00 00 00
[   17.800000] sdg: assuming drive cache: write through
[   17.824000] SCSI device sdg: 8015502 512-byte hdwr sectors (4104 MB)
[   17.828000] sdg: Write Protect is off
[   17.828000] sdg: Mode Sense: 03 00 00 00
[   17.828000] sdg: assuming drive cache: write through
[   17.828000]  sdg: sdg1
[   17.840000] sd 3:0:0:0: Attached scsi removable disk sdg
[   17.840000] sd 3:0:0:0: Attached scsi generic sg6 type 0
[   20.596000] cx25840 1-0044: loaded v4l-cx25840.fw firmware (16382 bytes)
[   20.776000] ivtv0: Registered device video1 for encoder MPEG (4 MB)
[   20.776000] ivtv0: Registered device video32 for encoder YUV (2 MB)
[   20.776000] ivtv0: Registered device vbi0 for encoder VBI (1 MB)
[   20.776000] ivtv0: Registered device video24 for encoder PCM audio (1 MB)
[   20.776000] ivtv0: Registered device radio0 for encoder radio
[   20.836000] ivtv0: i2c hardware 0x00000020 (wm8775) not found for command 0x4008646d!
[   21.004000] tuner 1-0060: tuner type not set
[   21.040000] tuner 1-0060: tuner type not set
[   21.168000] ivtv0: Initialized Hauppauge WinTV PVR-150, card #0
[   21.168000] ivtv:  ====================  END INIT IVTV  ====================
[   21.168000] ACPI: PCI Interrupt 0000:00:14.5[B] -> GSI 17 (level, low) -> IRQ 22
[   21.300000] fuse init (API version 7.8)
[   21.312000] lp0: using parport0 (interrupt-driven).
[   21.356000] Adding 1510100k swap on /dev/disk/by-uuid/84f036bb-6018-4d46-a980-ba1e72e12a80.  Priority:-1 extents:1 across:1510100k
[   21.692000] EXT3 FS on sda2, internal journal
[   22.088000] NTFS driver 2.1.28 [Flags: R/O MODULE].
[   22.120000] NTFS volume version 3.1.
[   27.180000] ibm_acpi: ec object not found
[   27.224000] Using specific hotkey driver
[   27.344000] No dock devices found.
[   27.352000] input: Power Button (FF) as /class/input/input6
[   27.352000] ACPI: Power Button (FF) [PWRF]
[   27.352000] input: Power Button (CM) as /class/input/input7
[   27.352000] ACPI: Power Button (CM) [PWRB]
[   27.484000] pcc_acpi: loading...
[   27.660000] powernow-k8: Found 2 AMD Athlon(tm) 64 X2 Dual Core Processor 4200+ processors (version 2.00.00)
[   27.660000] powernow-k8:    0 : fid 0xe (2200 MHz), vid 0x8
[   27.660000] powernow-k8:    1 : fid 0xc (2000 MHz), vid 0xa
[   27.660000] powernow-k8:    2 : fid 0xa (1800 MHz), vid 0xc
[   27.660000] powernow-k8:    3 : fid 0x2 (1000 MHz), vid 0x12
[   28.744000] APIC error on CPU0: 00(40)
[   31.160000] NETDEV WATCHDOG: eth0: transmit timed out
[   33.716000] [drm] Initialized drm 1.1.0 20060810
[   33.724000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 18 (level, low) -> IRQ 23
[   33.724000] [drm] Initialized radeon 1.25.0 20060524 on minor 0
[   34.160000] eth0: Transmit timeout, status 0d 0000 c07f media 10.
[   34.160000] eth0: Tx queue start entry 4  dirty entry 0.
[   34.160000] eth0:  Tx descriptor 0 is 00082156. (queue head)
[   34.160000] eth0:  Tx descriptor 1 is 00082156.
[   34.160000] eth0:  Tx descriptor 2 is 00082156.
[   34.160000] eth0:  Tx descriptor 3 is 00082156.
[   34.160000] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[   34.556000] ppdev: user-space parallel port driver
[   34.976000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   34.976000] apm: disabled - APM is not SMP safe.
[   35.116000] Bluetooth: Core ver 2.11
[   35.116000] NET: Registered protocol family 31
[   35.116000] Bluetooth: HCI device and connection manager initialized
[   35.116000] Bluetooth: HCI socket layer initialized
[   35.132000] Bluetooth: L2CAP ver 2.8
[   35.132000] Bluetooth: L2CAP socket layer initialized
[   35.324000] Bluetooth: RFCOMM socket layer initialized
[   35.324000] Bluetooth: RFCOMM TTY layer initialized
[   35.324000] Bluetooth: RFCOMM ver 1.8
[   48.128000] [drm] Setting GART location based on new memory map
[   48.128000] [drm] Loading R300 Microcode
[   48.128000] [drm] writeback test succeeded in 1 usecs
[   52.160000] NETDEV WATCHDOG: eth0: transmit timed out
[   54.620000] NET: Registered protocol family 10
[   54.620000] lo: Disabled Privacy Extensions
[   55.160000] eth0: Transmit timeout, status 0d 0000 c07f media 10.
[   55.160000] eth0: Tx queue start entry 4  dirty entry 0.
[   55.160000] eth0:  Tx descriptor 0 is 00082156. (queue head)
[   55.160000] eth0:  Tx descriptor 1 is 00082156.
[   55.160000] eth0:  Tx descriptor 2 is 00082156.
[   55.160000] eth0:  Tx descriptor 3 is 00082156.
[   55.160000] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[   64.796000] eth0: no IPv6 routers present
[   67.160000] NETDEV WATCHDOG: eth0: transmit timed out
[   70.160000] eth0: Transmit timeout, status 0d 0000 c07f media 10.
[   70.160000] eth0: Tx queue start entry 4  dirty entry 0.
[   70.160000] eth0:  Tx descriptor 0 is 0008203c. (queue head)
[   70.160000] eth0:  Tx descriptor 1 is 0008203c.
[   70.160000] eth0:  Tx descriptor 2 is 0008203c.
[   70.160000] eth0:  Tx descriptor 3 is 0008203c.
[   70.160000] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[   82.160000] NETDEV WATCHDOG: eth0: transmit timed out
[   85.160000] eth0: Transmit timeout, status 0d 0000 c07f media 10.
[   85.160000] eth0: Tx queue start entry 4  dirty entry 0.
[   85.160000] eth0:  Tx descriptor 0 is 0008203c. (queue head)
[   85.160000] eth0:  Tx descriptor 1 is 000820a2.
[   85.160000] eth0:  Tx descriptor 2 is 00082126.
[   85.160000] eth0:  Tx descriptor 3 is 00082126.
[   85.160000] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[   97.160000] NETDEV WATCHDOG: eth0: transmit timed out
[  100.160000] eth0: Transmit timeout, status 0d 0000 c07f media 10.
[  100.160000] eth0: Tx queue start entry 4  dirty entry 0.
[  100.160000] eth0:  Tx descriptor 0 is 00082126. (queue head)
[  100.160000] eth0:  Tx descriptor 1 is 00082114.
[  100.160000] eth0:  Tx descriptor 2 is 000820a2.
[  100.160000] eth0:  Tx descriptor 3 is 00082114.
[  100.160000] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[  112.160000] NETDEV WATCHDOG: eth0: transmit timed out
[  115.160000] eth0: Transmit timeout, status 0d 0000 c07f media 10.
[  115.160000] eth0: Tx queue start entry 4  dirty entry 0.
[  115.160000] eth0:  Tx descriptor 0 is 0008203c. (queue head)
[  115.160000] eth0:  Tx descriptor 1 is 00082108.
[  115.160000] eth0:  Tx descriptor 2 is 00082114.
[  115.160000] eth0:  Tx descriptor 3 is 0008205a.
[  115.160000] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[  126.880000] hdc: tray open
[  126.880000] end_request: I/O error, dev hdc, sector 0
[  126.880000] Buffer I/O error on device hdc, logical block 0
[  126.880000] Buffer I/O error on device hdc, logical block 1
[  126.880000] Buffer I/O error on device hdc, logical block 2
[  126.880000] Buffer I/O error on device hdc, logical block 3
[  126.880000] Buffer I/O error on device hdc, logical block 4
[  126.880000] Buffer I/O error on device hdc, logical block 5
[  126.880000] Buffer I/O error on device hdc, logical block 6
[  126.880000] Buffer I/O error on device hdc, logical block 7
[  126.880000] hdc: tray open
[  126.880000] end_request: I/O error, dev hdc, sector 0
[  126.880000] Buffer I/O error on device hdc, logical block 0
[  126.880000] hdc: tray open
[  126.884000] end_request: I/O error, dev hdc, sector 4
[  126.884000] Buffer I/O error on device hdc, logical block 1
[  126.884000] hdc: tray open
[  126.884000] end_request: I/O error, dev hdc, sector 0
[  126.884000] hdc: tray open
[  126.884000] end_request: I/O error, dev hdc, sector 4
[  126.884000] hdc: tray open
[  126.884000] end_request: I/O error, dev hdc, sector 0
[  126.884000] hdc: tray open
[  126.884000] end_request: I/O error, dev hdc, sector 4
[  126.884000] hdc: tray open
[  126.888000] end_request: I/O error, dev hdc, sector 0
[  126.888000] hdc: tray open
[  126.888000] end_request: I/O error, dev hdc, sector 4
[  126.888000] hdc: tray open
[  126.888000] end_request: I/O error, dev hdc, sector 0
[  126.888000] hdc: tray open
[  126.888000] end_request: I/O error, dev hdc, sector 4
[  126.904000] hdd: tray open
[  126.904000] end_request: I/O error, dev hdd, sector 0
[  126.904000] hdd: tray open
[  126.904000] end_request: I/O error, dev hdd, sector 0
[  126.908000] hdd: tray open
[  126.908000] end_request: I/O error, dev hdd, sector 4
[  126.908000] hdd: tray open
[  126.908000] end_request: I/O error, dev hdd, sector 0
[  126.908000] hdd: tray open
[  126.908000] end_request: I/O error, dev hdd, sector 4
[  126.908000] hdd: tray open
[  126.908000] end_request: I/O error, dev hdd, sector 0
[  126.912000] hdd: tray open
[  126.912000] end_request: I/O error, dev hdd, sector 4
[  126.912000] hdd: tray open
[  126.912000] end_request: I/O error, dev hdd, sector 0
[  126.912000] hdd: tray open
[  126.912000] end_request: I/O error, dev hdd, sector 4
[  126.912000] hdd: tray open
[  126.912000] end_request: I/O error, dev hdd, sector 0
[  126.912000] hdd: tray open
[  126.916000] end_request: I/O error, dev hdd, sector 4
[  127.160000] NETDEV WATCHDOG: eth0: transmit timed out
[  130.160000] eth0: Transmit timeout, status 0d 0000 c07f media 10.
[  130.160000] eth0: Tx queue start entry 4  dirty entry 0.
[  130.160000] eth0:  Tx descriptor 0 is 0008203c. (queue head)
[  130.160000] eth0:  Tx descriptor 1 is 0008204e.
[  130.160000] eth0:  Tx descriptor 2 is 0008203c.
[  130.160000] eth0:  Tx descriptor 3 is 00082046.
[  130.160000] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[  142.160000] NETDEV WATCHDOG: eth0: transmit timed out


```



lspci -nn: ```


[    4.120000] usb 2-1: new high speed USB device using ehci_hcd and address 2
[    4.172000] 8139cp 0000:02:03.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[    4.172000] 8139cp 0000:02:03.0: Try the "8139too" driver instead.
[    4.172000] ATIIXP: IDE controller at PCI slot 0000:00:14.1
[    4.172000] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 20
[    4.172000] ATIIXP: chipset revision 0
[    4.172000] ATIIXP: not 100% native mode: will probe irqs later
[    4.172000]     ide0: BM-DMA at 0xf800-0xf807, BIOS settings: hda:pio, hdb:pio
[    4.172000]     ide1: BM-DMA at 0xf808-0xf80f, BIOS settings: hdc:pio, hdd:pio
[    4.172000] Probing IDE interface ide0...
[    4.180000] 8139too Fast Ethernet driver 0.9.28
[    4.272000] usb 2-1: configuration #1 chosen from 1 choice
[    4.744000] Probing IDE interface ide1...
[    5.092000] usb 4-4: new full speed USB device using ohci_hcd and address 2
[    5.296000] usb 4-4: configuration #1 chosen from 1 choice
[    5.488000] hdc: HP DVD Writer 840b, ATAPI CD/DVD-ROM drive
[    5.980000] usb 6-1: new full speed USB device using uhci_hcd and address 2
[    6.148000] usb 6-1: configuration #1 chosen from 1 choice
[    6.276000] hdd: ASUS DVD-E616P3H, ATAPI CD/DVD-ROM drive
[    6.336000] ide1 at 0x170-0x177,0x376 on irq 15
[    6.340000] ACPI: PCI Interrupt 0000:02:02.3[A] -> GSI 22 (level, low) -> IRQ 18
[    6.392000] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[18]  MMIO=[fddfd000-fddfd7ff]  Max Packet=[2]  IR/IT contexts=[4/8]
[    6.396000] ohci1394: fw-host0: Serial EEPROM has suspicious values, attempting to setting max_packet_size to 512 bytes
[    6.396000] usb 6-2: new full speed USB device using uhci_hcd and address 3
[    6.396000] ACPI: PCI Interrupt 0000:02:04.0[A] -> GSI 21 (level, low) -> IRQ 21
[    6.448000] ohci1394: fw-host1: OHCI-1394 1.1 (PCI): IRQ=[21]  MMIO=[fddfb000-fddfb7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    6.452000] ACPI: PCI Interrupt 0000:02:03.0[A] -> GSI 20 (level, low) -> IRQ 17
[    6.452000] eth0: RealTek RTL8139 at 0xf884c000, 00:13:d3:56:de:b8, IRQ 17
[    6.452000] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[    6.452000] sata_sil 0000:00:12.0: version 2.2
[    6.452000] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 22 (level, low) -> IRQ 18
[    6.452000] ata1: SATA max UDMA/100 cmd 0xf8856080 ctl 0xf885608a bmdma 0xf8856000 irq 18
[    6.452000] ata2: SATA max UDMA/100 cmd 0xf88560c0 ctl 0xf88560ca bmdma 0xf8856008 irq 18
[    6.452000] scsi0 : sata_sil
[    6.596000] usb 6-2: configuration #1 chosen from 1 choice
[    6.904000] usb 4-1: new full speed USB device using ohci_hcd and address 3
[    6.920000] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    6.936000] ata1.00: ata_hpa_resize 1: sectors = 145226112, hpa_sectors = 145226112
[    6.936000] ata1.00: ATA-7: WDC WD740ADFD-00NLR1, 20.07P20, max UDMA/133
[    6.936000] ata1.00: 145226112 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    6.948000] ata1.00: ata_hpa_resize 1: sectors = 145226112, hpa_sectors = 145226112
[    6.948000] ata1.00: configured for UDMA/100
[    6.948000] scsi1 : sata_sil
[    7.104000] usb 4-1: configuration #1 chosen from 1 choice
[    7.104000] hub 4-1:1.0: USB hub found
[    7.108000] hub 4-1:1.0: 4 ports detected
[    7.224000] usbcore: registered new interface driver libusual
[    7.228000] Initializing USB Mass Storage driver...
[    7.228000] scsi2 : SCSI emulation for USB Mass Storage devices
[    7.228000] usb-storage: device found at 2
[    7.228000] usb-storage: waiting for device to settle before scanning
[    7.416000] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    7.432000] ata2.00: ATA-7: ST3250823AS, 3.03, max UDMA/100
[    7.432000] ata2.00: 488397168 sectors, multi 16: LBA48 
[    7.444000] ata2.00: configured for UDMA/100
[    7.444000] scsi 0:0:0:0: Direct-Access     ATA      WDC WD740ADFD-00 20.0 PQ: 0 ANSI: 5
[    7.444000] scsi 1:0:0:0: Direct-Access     ATA      ST3250823AS      3.03 PQ: 0 ANSI: 5
[    7.452000] hdc: ATAPI 40X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(33)
[    7.452000] Uniform CD-ROM driver Revision: 3.20
[    7.456000] usb 4-1.1: new low speed USB device using ohci_hcd and address 4
[    7.456000] SCSI device sda: 145226112 512-byte hdwr sectors (74356 MB)
[    7.456000] sda: Write Protect is off
[    7.456000] sda: Mode Sense: 00 3a 00 00
[    7.456000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.456000] SCSI device sda: 145226112 512-byte hdwr sectors (74356 MB)
[    7.456000] sda: Write Protect is off
[    7.456000] sda: Mode Sense: 00 3a 00 00
[    7.456000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.456000]  sda:<6>hdd: ATAPI 40X DVD-ROM drive, 512kB Cache, UDMA(33)
[    7.468000]  sda1 sda2 sda3
[    7.484000] sd 0:0:0:0: Attached scsi disk sda
[    7.484000] SCSI device sdb: 488397168 512-byte hdwr sectors (250059 MB)
[    7.484000] sdb: Write Protect is off
[    7.484000] sdb: Mode Sense: 00 3a 00 00
[    7.484000] SCSI device sdb: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.484000] SCSI device sdb: 488397168 512-byte hdwr sectors (250059 MB)
[    7.484000] sdb: Write Protect is off
[    7.484000] sdb: Mode Sense: 00 3a 00 00
[    7.484000] SCSI device sdb: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.484000]  sdb:
[    7.504000] sd 1:0:0:0: Attached scsi disk sdb
[    7.508000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    7.508000] sd 1:0:0:0: Attached scsi generic sg1 type 0
[    7.572000] usb 4-1.1: configuration #1 chosen from 1 choice
[    7.676000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[001106005350d195]
[    7.720000] Attempting manual resume
[    7.720000] swsusp: Resume From Partition 8:3
[    7.720000] PM: Checking swsusp image.
[    7.720000] PM: Resume from disk failed.
[    7.736000] kjournald starting.  Commit interval 5 seconds
[    7.736000] EXT3-fs: mounted filesystem with ordered data mode.
[    7.808000] usb 4-1.3: new low speed USB device using ohci_hcd and address 5
[    7.952000] ieee1394: Host added: ID:BUS[1-00:1023]  GUID[0010dc0000b83eea]
[   10.900000] usb 4-1.3: device descriptor read/64, error -110
[   12.056000] usb 4-1.3: configuration #1 chosen from 1 choice
[   12.232000] usb-storage: device scan complete
[   12.236000] scsi 2:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
[   12.244000] scsi 2:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
[   12.248000] scsi 2:0:0:2: Direct-Access     Generic  USB SM Reader    1.02 PQ: 0 ANSI: 0
[   12.256000] scsi 2:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0
[   12.264000] sd 2:0:0:0: Attached scsi removable disk sdc
[   12.264000] sd 2:0:0:0: Attached scsi generic sg2 type 0
[   12.276000] sd 2:0:0:1: Attached scsi removable disk sdd
[   12.276000] sd 2:0:0:1: Attached scsi generic sg3 type 0
[   12.284000] sd 2:0:0:2: Attached scsi removable disk sde
[   12.284000] sd 2:0:0:2: Attached scsi generic sg4 type 0
[   12.288000] usb 4-1.4: new full speed USB device using ohci_hcd and address 6
[   12.296000] sd 2:0:0:3: Attached scsi removable disk sdf
[   12.296000] sd 2:0:0:3: Attached scsi generic sg5 type 0
[   12.408000] usb 4-1.4: configuration #1 chosen from 1 choice
[   12.640000] usb 4-1.2: new full speed USB device using ohci_hcd and address 7
[   12.748000] usb 4-1.2: not running at top speed; connect to a high speed hub
[   12.760000] usb 4-1.2: configuration #1 chosen from 1 choice
[   12.764000] scsi3 : SCSI emulation for USB Mass Storage devices
[   12.764000] usb-storage: device found at 7
[   12.764000] usb-storage: waiting for device to settle before scanning
[   12.764000] usbcore: registered new interface driver usb-storage
[   12.764000] usbcore: registered new interface driver hiddev
[   12.764000] USB Mass Storage support registered.
[   12.828000] input: Gaming Keyboard as /class/input/input1
[   12.828000] input: USB HID v1.10 Keyboard [Gaming Keyboard] on usb-0000:00:13.1-1.1
[   12.840000] input: Gaming Keyboard as /class/input/input2
[   12.840000] input,hiddev96: USB HID v1.10 Device [Gaming Keyboard] on usb-0000:00:13.1-1.1
[   13.160000] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[   13.204000] hiddev97: USB HID v1.10 Device [American Power Conversion Back-UPS BR  800 FW:9.o2 .D USB FW:o2 ] on usb-0000:00:13.1-1.3
[   13.212000] input: G11 Keyboard as /class/input/input3
[   13.212000] input,hiddev98: USB HID v1.11 Keypad [G11 Keyboard] on usb-0000:00:13.1-1.4
[   13.212000] usbcore: registered new interface driver usbhid
[   13.212000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   14.312000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   14.316000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   14.364000] piix4_smbus 0000:00:14.0: Found 0000:00:14.0 device
[   14.440000] Linux video capture interface: v2.00
[   14.484000] NET: Registered protocol family 17
[   14.508000] ivtv:  ==================== START INIT IVTV ====================
[   14.508000] ivtv:  version 0.10.1 (tagged release) loading
[   14.508000] ivtv:  Linux version: 2.6.20-16-generic SMP mod_unload 586 
[   14.508000] ivtv:  In case of problems please include the debug info between
[   14.508000] ivtv:  the START INIT IVTV and END INIT IVTV lines, along with
[   14.508000] ivtv:  any module options, when mailing the ivtv-users mailinglist.
[   14.508000] ivtv0: Unknown card: vendor/device: 4444/0016
[   14.508000] ivtv0:               subsystem vendor/device: 1043/4b2e
[   14.508000] ivtv0:               cx23416 based
[   14.508000] ivtv0: Defaulting to Hauppauge WinTV PVR-150 card
[   14.508000] ivtv0: Please mail the vendor/device and subsystem vendor/device IDs and what kind of
[   14.508000] ivtv0: card you have to the ivtv-devel mailinglist (www.ivtvdriver.org)
[   14.508000] ivtv0: Prefix your subject line with [UNKNOWN CARD].
[   14.660000] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 20 (level, low) -> IRQ 17
[   14.672000] Linux agpgart interface v0.102 (c) Dave Jones
[   14.744000] input: PC Speaker as /class/input/input4
[   14.744000] usbcore: registered new interface driver xpad
[   14.744000] drivers/usb/input/xpad.c: driver for Xbox controllers v0.1.6
[   14.948000] ubuntu/media/gspcav1/gspca_core.c: USB SPCA5XX camera found.(ZC3XX) 
[   14.964000] parport: PnPBIOS parport detected.
[   14.964000] parport0: PC-style at 0x378, irq 7 [PCSPP,EPP]
[   15.188000] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 2 if 1 alt 0 proto 2 vid 0x04B8 pid 0x0820
[   15.340000] ivtv0: loaded v4l-cx2341x-enc.fw firmware (262144 bytes)
[   15.556000] ivtv0: Encoder revision: 0x02050032
[   15.556000] ivtv0: Recommended firmware version is 0x02060039.
[   15.568000] tveeprom 1-0050: Huh, no eeprom present (err=-121)?
[   15.568000] tveeprom 1-0050: Encountered bad packet header [02]. Corrupt or not a Hauppauge eeprom.
[   15.568000] ivtv0: Invalid EEPROM
[   15.588000] tuner 1-0043: chip found @ 0x86 (ivtv i2c driver #0)
[   15.588000] tda9887 1-0043: tda988[5/6/7] found @ 0x43 (tuner)
[   15.592000] tuner 1-0060: All bytes are equal. It is not a TEA5767
[   15.592000] tuner 1-0060: chip found @ 0xc0 (ivtv i2c driver #0)
[   15.616000] input: ImPS/2 Logitech Wheel Mouse as /class/input/input5
[   15.632000] cx25840 1-0044: cx25843-23 found @ 0x88 (ivtv i2c driver #0)
[   15.660000] usbcore: registered new interface driver gspca
[   15.660000] ubuntu/media/gspcav1/gspca_core.c: gspca driver 01.00.12 registered
[   15.660000] usbcore: registered new interface driver usblp
[   15.660000] drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
[   15.772000] usbcore: registered new interface driver snd-usb-audio
[   17.776000] usb-storage: device scan complete
[   17.784000] scsi 3:0:0:0: Direct-Access     SanDisk  U3 Cruzer Micro  3.27 PQ: 0 ANSI: 2
[   17.792000] SCSI device sdg: 8015502 512-byte hdwr sectors (4104 MB)
[   17.800000] sdg: Write Protect is off
[   17.800000] sdg: Mode Sense: 03 00 00 00
[   17.800000] sdg: assuming drive cache: write through
[   17.824000] SCSI device sdg: 8015502 512-byte hdwr sectors (4104 MB)
[   17.828000] sdg: Write Protect is off
[   17.828000] sdg: Mode Sense: 03 00 00 00
[   17.828000] sdg: assuming drive cache: write through
[   17.828000]  sdg: sdg1
[   17.840000] sd 3:0:0:0: Attached scsi removable disk sdg
[   17.840000] sd 3:0:0:0: Attached scsi generic sg6 type 0
[   20.596000] cx25840 1-0044: loaded v4l-cx25840.fw firmware (16382 bytes)
[   20.776000] ivtv0: Registered device video1 for encoder MPEG (4 MB)
[   20.776000] ivtv0: Registered device video32 for encoder YUV (2 MB)
[   20.776000] ivtv0: Registered device vbi0 for encoder VBI (1 MB)
[   20.776000] ivtv0: Registered device video24 for encoder PCM audio (1 MB)
[   20.776000] ivtv0: Registered device radio0 for encoder radio
[   20.836000] ivtv0: i2c hardware 0x00000020 (wm8775) not found for command 0x4008646d!
[   21.004000] tuner 1-0060: tuner type not set
[   21.040000] tuner 1-0060: tuner type not set
[   21.168000] ivtv0: Initialized Hauppauge WinTV PVR-150, card #0
[   21.168000] ivtv:  ====================  END INIT IVTV  ====================
[   21.168000] ACPI: PCI Interrupt 0000:00:14.5[B] -> GSI 17 (level, low) -> IRQ 22
[   21.300000] fuse init (API version 7.8)
[   21.312000] lp0: using parport0 (interrupt-driven).
[   21.356000] Adding 1510100k swap on /dev/disk/by-uuid/84f036bb-6018-4d46-a980-ba1e72e12a80.  Priority:-1 extents:1 across:1510100k
[   21.692000] EXT3 FS on sda2, internal journal
[   22.088000] NTFS driver 2.1.28 [Flags: R/O MODULE].
[   22.120000] NTFS volume version 3.1.
[   27.180000] ibm_acpi: ec object not found
[   27.224000] Using specific hotkey driver
[   27.344000] No dock devices found.
[   27.352000] input: Power Button (FF) as /class/input/input6
[   27.352000] ACPI: Power Button (FF) [PWRF]
[   27.352000] input: Power Button (CM) as /class/input/input7
[   27.352000] ACPI: Power Button (CM) [PWRB]
[   27.484000] pcc_acpi: loading...
[   27.660000] powernow-k8: Found 2 AMD Athlon(tm) 64 X2 Dual Core Processor 4200+ processors (version 2.00.00)
[   27.660000] powernow-k8:    0 : fid 0xe (2200 MHz), vid 0x8
[   27.660000] powernow-k8:    1 : fid 0xc (2000 MHz), vid 0xa
[   27.660000] powernow-k8:    2 : fid 0xa (1800 MHz), vid 0xc
[   27.660000] powernow-k8:    3 : fid 0x2 (1000 MHz), vid 0x12
[   28.744000] APIC error on CPU0: 00(40)
[   31.160000] NETDEV WATCHDOG: eth0: transmit timed out
[   33.716000] [drm] Initialized drm 1.1.0 20060810
[   33.724000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 18 (level, low) -> IRQ 23
[   33.724000] [drm] Initialized radeon 1.25.0 20060524 on minor 0
[   34.160000] eth0: Transmit timeout, status 0d 0000 c07f media 10.
[   34.160000] eth0: Tx queue start entry 4  dirty entry 0.
[   34.160000] eth0:  Tx descriptor 0 is 00082156. (queue head)
[   34.160000] eth0:  Tx descriptor 1 is 00082156.
[   34.160000] eth0:  Tx descriptor 2 is 00082156.
[   34.160000] eth0:  Tx descriptor 3 is 00082156.
[   34.160000] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[   34.556000] ppdev: user-space parallel port driver
[   34.976000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   34.976000] apm: disabled - APM is not SMP safe.
[   35.116000] Bluetooth: Core ver 2.11
[   35.116000] NET: Registered protocol family 31
[   35.116000] Bluetooth: HCI device and connection manager initialized
[   35.116000] Bluetooth: HCI socket layer initialized
[   35.132000] Bluetooth: L2CAP ver 2.8
[   35.132000] Bluetooth: L2CAP socket layer initialized
[   35.324000] Bluetooth: RFCOMM socket layer initialized
[   35.324000] Bluetooth: RFCOMM TTY layer initialized
[   35.324000] Bluetooth: RFCOMM ver 1.8
[   48.128000] [drm] Setting GART location based on new memory map
[   48.128000] [drm] Loading R300 Microcode
[   48.128000] [drm] writeback test succeeded in 1 usecs
[   52.160000] NETDEV WATCHDOG: eth0: transmit timed out
[   54.620000] NET: Registered protocol family 10
[   54.620000] lo: Disabled Privacy Extensions
[   55.160000] eth0: Transmit timeout, status 0d 0000 c07f media 10.
[   55.160000] eth0: Tx queue start entry 4  dirty entry 0.
[   55.160000] eth0:  Tx descriptor 0 is 00082156. (queue head)
[   55.160000] eth0:  Tx descriptor 1 is 00082156.
[   55.160000] eth0:  Tx descriptor 2 is 00082156.
[   55.160000] eth0:  Tx descriptor 3 is 00082156.
[   55.160000] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[   64.796000] eth0: no IPv6 routers present
[   67.160000] NETDEV WATCHDOG: eth0: transmit timed out
[   70.160000] eth0: Transmit timeout, status 0d 0000 c07f media 10.
[   70.160000] eth0: Tx queue start entry 4  dirty entry 0.
[   70.160000] eth0:  Tx descriptor 0 is 0008203c. (queue head)
[   70.160000] eth0:  Tx descriptor 1 is 0008203c.
[   70.160000] eth0:  Tx descriptor 2 is 0008203c.
[   70.160000] eth0:  Tx descriptor 3 is 0008203c.
[   70.160000] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[   82.160000] NETDEV WATCHDOG: eth0: transmit timed out
[   85.160000] eth0: Transmit timeout, status 0d 0000 c07f media 10.
[   85.160000] eth0: Tx queue start entry 4  dirty entry 0.
[   85.160000] eth0:  Tx descriptor 0 is 0008203c. (queue head)
[   85.160000] eth0:  Tx descriptor 1 is 000820a2.
[   85.160000] eth0:  Tx descriptor 2 is 00082126.
[   85.160000] eth0:  Tx descriptor 3 is 00082126.
[   85.160000] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[   97.160000] NETDEV WATCHDOG: eth0: transmit timed out
[  100.160000] eth0: Transmit timeout, status 0d 0000 c07f media 10.
[  100.160000] eth0: Tx queue start entry 4  dirty entry 0.
[  100.160000] eth0:  Tx descriptor 0 is 00082126. (queue head)
[  100.160000] eth0:  Tx descriptor 1 is 00082114.
[  100.160000] eth0:  Tx descriptor 2 is 000820a2.
[  100.160000] eth0:  Tx descriptor 3 is 00082114.
[  100.160000] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[  112.160000] NETDEV WATCHDOG: eth0: transmit timed out
[  115.160000] eth0: Transmit timeout, status 0d 0000 c07f media 10.
[  115.160000] eth0: Tx queue start entry 4  dirty entry 0.
[  115.160000] eth0:  Tx descriptor 0 is 0008203c. (queue head)
[  115.160000] eth0:  Tx descriptor 1 is 00082108.
[  115.160000] eth0:  Tx descriptor 2 is 00082114.
[  115.160000] eth0:  Tx descriptor 3 is 0008205a.
[  115.160000] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[  126.880000] hdc: tray open
[  126.880000] end_request: I/O error, dev hdc, sector 0
[  126.880000] Buffer I/O error on device hdc, logical block 0
[  126.880000] Buffer I/O error on device hdc, logical block 1
[  126.880000] Buffer I/O error on device hdc, logical block 2
[  126.880000] Buffer I/O error on device hdc, logical block 3
[  126.880000] Buffer I/O error on device hdc, logical block 4
[  126.880000] Buffer I/O error on device hdc, logical block 5
[  126.880000] Buffer I/O error on device hdc, logical block 6
[  126.880000] Buffer I/O error on device hdc, logical block 7
[  126.880000] hdc: tray open
[  126.880000] end_request: I/O error, dev hdc, sector 0
[  126.880000] Buffer I/O error on device hdc, logical block 0
[  126.880000] hdc: tray open
[  126.884000] end_request: I/O error, dev hdc, sector 4
[  126.884000] Buffer I/O error on device hdc, logical block 1
[  126.884000] hdc: tray open
[  126.884000] end_request: I/O error, dev hdc, sector 0
[  126.884000] hdc: tray open
[  126.884000] end_request: I/O error, dev hdc, sector 4
[  126.884000] hdc: tray open
[  126.884000] end_request: I/O error, dev hdc, sector 0
[  126.884000] hdc: tray open
[  126.884000] end_request: I/O error, dev hdc, sector 4
[  126.884000] hdc: tray open
[  126.888000] end_request: I/O error, dev hdc, sector 0
[  126.888000] hdc: tray open
[  126.888000] end_request: I/O error, dev hdc, sector 4
[  126.888000] hdc: tray open
[  126.888000] end_request: I/O error, dev hdc, sector 0
[  126.888000] hdc: tray open
[  126.888000] end_request: I/O error, dev hdc, sector 4
[  126.904000] hdd: tray open
[  126.904000] end_request: I/O error, dev hdd, sector 0
[  126.904000] hdd: tray open
[  126.904000] end_request: I/O error, dev hdd, sector 0
[  126.908000] hdd: tray open
[  126.908000] end_request: I/O error, dev hdd, sector 4
[  126.908000] hdd: tray open
[  126.908000] end_request: I/O error, dev hdd, sector 0
[  126.908000] hdd: tray open
[  126.908000] end_request: I/O error, dev hdd, sector 4
[  126.908000] hdd: tray open
[  126.908000] end_request: I/O error, dev hdd, sector 0
[  126.912000] hdd: tray open
[  126.912000] end_request: I/O error, dev hdd, sector 4
[  126.912000] hdd: tray open
[  126.912000] end_request: I/O error, dev hdd, sector 0
[  126.912000] hdd: tray open
[  126.912000] end_request: I/O error, dev hdd, sector 4
[  126.912000] hdd: tray open
[  126.912000] end_request: I/O error, dev hdd, sector 0
[  126.912000] hdd: tray open
[  126.916000] end_request: I/O error, dev hdd, sector 4
[  127.160000] NETDEV WATCHDOG: eth0: transmit timed out
[  130.160000] eth0: Transmit timeout, status 0d 0000 c07f media 10.
[  130.160000] eth0: Tx queue start entry 4  dirty entry 0.
[  130.160000] eth0:  Tx descriptor 0 is 0008203c. (queue head)
[  130.160000] eth0:  Tx descriptor 1 is 0008204e.
[  130.160000] eth0:  Tx descriptor 2 is 0008203c.
[  130.160000] eth0:  Tx descriptor 3 is 00082046.
[  130.160000] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[  142.160000] NETDEV WATCHDOG: eth0: transmit timed out

 lspci -nn
00:00.0 Host bridge [0600]: ATI Technologies Inc RS480 Host Bridge [1002:5950] (rev 10)
00:02.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI-X Root Port [1002:5a34]
00:12.0 IDE interface [0101]: ATI Technologies Inc ATI 4379 Serial ATA Controller [1002:4379]
00:13.0 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB Host Controller [1002:4374]
00:13.1 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB Host Controller [1002:4375]
00:13.2 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB2 Host Controller [1002:4373]
00:14.0 SMBus [0c05]: ATI Technologies Inc IXP SB400 SMBus Controller [1002:4372] (rev 11)
00:14.1 IDE interface [0101]: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI [1002:4376]
00:14.3 ISA bridge [0601]: ATI Technologies Inc IXP SB400 PCI-ISA Bridge [1002:4377]
00:14.4 PCI bridge [0604]: ATI Technologies Inc IXP SB400 PCI-PCI Bridge [1002:4371]
00:14.5 Multimedia audio controller [0401]: ATI Technologies Inc IXP SB400 AC'97 Audio Controller [1002:4370] (rev 02)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)] [1002:5b60]
01:00.1 Display controller [0380]: ATI Technologies Inc RV370 [Radeon X300SE] [1002:5b70]
02:00.0 Multimedia video controller [0400]: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder [4444:0016] (rev 01)
02:01.0 Communication controller [0780]: Agere Systems V.92 56K WinModem [11c1:048c] (rev 03)
02:02.0 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 61)
02:02.1 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 61)
02:02.2 USB Controller [0c03]: VIA Technologies, Inc. USB 2.0 [1106:3104] (rev 63)
02:02.3 FireWire (IEEE 1394) [0c00]: VIA Technologies, Inc. IEEE 1394 Host Controller [1106:3044] (rev 46)
02:03.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
02:04.0 FireWire (IEEE 1394) [0c00]: VIA Technologies, Inc. IEEE 1394 Host Controller [1106:3044] (rev 80)

lspci -nn
00:00.0 Host bridge [0600]: ATI Technologies Inc RS480 Host Bridge [1002:5950] (rev 10)
00:02.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI-X Root Port [1002:5a34]
00:12.0 IDE interface [0101]: ATI Technologies Inc ATI 4379 Serial ATA Controller [1002:4379]
00:13.0 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB Host Controller [1002:4374]
00:13.1 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB Host Controller [1002:4375]
00:13.2 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB2 Host Controller [1002:4373]
00:14.0 SMBus [0c05]: ATI Technologies Inc IXP SB400 SMBus Controller [1002:4372] (rev 11)
00:14.1 IDE interface [0101]: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI [1002:4376]
00:14.3 ISA bridge [0601]: ATI Technologies Inc IXP SB400 PCI-ISA Bridge [1002:4377]
00:14.4 PCI bridge [0604]: ATI Technologies Inc IXP SB400 PCI-PCI Bridge [1002:4371]
00:14.5 Multimedia audio controller [0401]: ATI Technologies Inc IXP SB400 AC'97 Audio Controller [1002:4370] (rev 02)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)] [1002:5b60]
01:00.1 Display controller [0380]: ATI Technologies Inc RV370 [Radeon X300SE] [1002:5b70]
02:00.0 Multimedia video controller [0400]: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder [4444:0016] (rev 01)
02:01.0 Communication controller [0780]: Agere Systems V.92 56K WinModem [11c1:048c] (rev 03)
02:02.0 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 61)
02:02.1 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 61)
02:02.2 USB Controller [0c03]: VIA Technologies, Inc. USB 2.0 [1106:3104] (rev 63)
02:02.3 FireWire (IEEE 1394) [0c00]: VIA Technologies, Inc. IEEE 1394 Host Controller [1106:3044] (rev 46)
02:03.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
02:04.0 FireWire (IEEE 1394) [0c00]: VIA Technologies, Inc. IEEE 1394 Host Controller [1106:3044] (rev 80)

```

---

### Post by noob12 on 2007-08-05
This is bad.  But it generally indicates earlier errors during boot.  It looks like you gave us an exceprt of dmesg.  We need to see the full dmesg output.  Yes.  It might be long.

Typically this is preceded by some PCI or BIOS error or both.

> 
[   52.160000] NETDEV WATCHDOG: eth0: transmit timed out
[   54.620000] NET: Registered protocol family 10
[   54.620000] lo: Disabled Privacy Extensions
[   55.160000] eth0: Transmit timeout, status 0d 0000 c07f media 10.
[   55.160000] eth0: Tx queue start entry 4  dirty entry 0.
[   55.160000] eth0:  Tx descriptor 0 is 00082156. (queue head)
[   55.160000] eth0:  Tx descriptor 1 is 00082156.
[   55.160000] eth0:  Tx descriptor 2 is 00082156.
[   55.160000] eth0:  Tx descriptor 3 is 00082156.


---

### Post by rubperezt on 2007-08-05
sorry about that mate ^^

here's the full output:
```

[    0.000000] Linux version 2.6.20-16-generic (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Thu Jun 7 20:19:32 UTC 2007 (Ubuntu 2.6.20-16.29-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009f400 end: 000000000009f400 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009f400 size: 0000000000000c00 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000f0000 size: 0000000000010000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000003fdf0000 end: 000000003fef0000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000003fef0000 size: 0000000000003000 end: 000000003fef3000 type: 4
[    0.000000] copy_e820_map() start: 000000003fef3000 size: 000000000000d000 end: 000000003ff00000 type: 3
[    0.000000] copy_e820_map() start: 00000000e0000000 size: 0000000010000000 end: 00000000f0000000 type: 2
[    0.000000] copy_e820_map() start: 00000000fec00000 size: 0000000001400000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f400 (usable)
[    0.000000]  BIOS-e820: 000000000009f400 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003fef0000 (usable)
[    0.000000]  BIOS-e820: 000000003fef0000 - 000000003fef3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003fef3000 - 000000003ff00000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] 126MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f4730
[    0.000000] Entering add_active_range(0, 0, 261872) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   261872
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   261872
[    0.000000] On node 0 totalpages: 261872
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 253 pages used for memmap
[    0.000000]   HighMem zone: 32243 pages, LIFO batch:7
[    0.000000] DMI 2.4 present.
[    0.000000] ACPI: RSDP (v000 HP-CPC                                ) @ 0x000f8650
[    0.000000] ACPI: RSDT (v001 HP-CPC AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x3fef3040
[    0.000000] ACPI: FADT (v002 HP-CPC AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x3fef30c0
[    0.000000] ACPI: SSDT (v001 HP-CPC POWERNOW 0x00000001  LTP 0x00000001) @ 0x3fef6f40
[    0.000000] ACPI: MCFG (v001 HP-CPC AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x3fef7180
[    0.000000] ACPI: MADT (v001 HP-CPC AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x3fef6e80
[    0.000000] ACPI: DSDT (v001 HP-CPC AWRDACPI 0x00001000 MSFT 0x0100000e) @ 0x00000000
[    0.000000] ATI board detected. Disabling timer routing over 8254.
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:11 APIC version 16
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1 15:11 APIC version 16
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 3ff00000:a0100000)
[    0.000000] Detected 2188.915 MHz processor.
[   28.463192] Built 1 zonelists.  Total pages: 259827
[   28.463195] Kernel command line: root=UUID=4327a9b0-0b96-4e2a-8954-bd67dc235e62 ro quiet splash
[   28.463310] mapped APIC to ffffd000 (fee00000)
[   28.463312] mapped IOAPIC to ffffc000 (fec00000)
[   28.463315] Enabling fast FPU save and restore... done.
[   28.463317] Enabling unmasked SIMD FPU exception support... done.
[   28.463323] Initializing CPU#0
[   28.463379] PID hash table entries: 4096 (order: 12, 16384 bytes)
[   28.464659] Console: colour VGA+ 80x25
[   28.464986] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   28.465318] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   28.481738] Memory: 1027300k/1047488k available (1992k kernel code, 19516k reserved, 900k data, 328k init, 129984k highmem)
[   28.481747] virtual kernel memory layout:
[   28.481748]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   28.481749]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   28.481750]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   28.481751]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   28.481752]       .init : 0xc03d9000 - 0xc042b000   ( 328 kB)
[   28.481753]       .data : 0xc02f2374 - 0xc03d36d4   ( 900 kB)
[   28.481755]       .text : 0xc0100000 - 0xc02f2374   (1992 kB)
[   28.481757] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   28.559221] Calibrating delay using timer specific routine.. 4381.96 BogoMIPS (lpj=8763928)
[   28.559255] Security Framework v1.0.0 initialized
[   28.559261] SELinux:  Disabled at boot.
[   28.559274] Mount-cache hash table entries: 512
[   28.559388] CPU: After generic identify, caps: 178bfbff e3d3fbff 00000000 00000000 00000001 00000000 00000003
[   28.559395] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   28.559398] CPU: L2 Cache: 512K (64 bytes/line)
[   28.559400] CPU 0(2) -> Core 0
[   28.559402] CPU: After all inits, caps: 178bfbff e3d3fbff 00000000 00000410 00000001 00000000 00000003
[   28.559411] Compat vDSO mapped to ffffe000.
[   28.559414] Remapping vsyscall page to ffffe000
[   28.559423] Checking 'hlt' instruction... OK.
[   28.575307] SMP alternatives: switching to UP code
[   28.575634] Early unpacking initramfs... done
[   28.830362] ACPI: Core revision 20060707
[   28.839217] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   28.849613] CPU0: AMD Athlon(tm) 64 X2 Dual Core Processor 4200+ stepping 01
[   28.849635] SMP alternatives: switching to SMP code
[   28.849684] Booting processor 1/1 eip 3000
[   28.860339] Initializing CPU#1
[   28.939050] Calibrating delay using timer specific routine.. 4377.80 BogoMIPS (lpj=8755604)
[   28.939056] CPU: After generic identify, caps: 178bfbff e3d3fbff 00000000 00000000 00000001 00000000 00000003
[   28.939061] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   28.939063] CPU: L2 Cache: 512K (64 bytes/line)
[   28.939066] CPU 1(2) -> Core 1
[   28.939067] CPU: After all inits, caps: 178bfbff e3d3fbff 00000000 00000410 00000001 00000000 00000003
[   28.938732] CPU1: AMD Athlon(tm) 64 X2 Dual Core Processor 4200+ stepping 01
[   28.938748] Total of 2 processors activated (8759.76 BogoMIPS).
[   28.938910] ENABLING IO-APIC IRQs
[   28.939094] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   28.978751] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
[   28.978799] ...trying to set up timer (IRQ0) through the 8259A ...  failed.
[   28.978801] ...trying to set up timer as Virtual Wire IRQ... works.
[   29.126241] checking TSC synchronization across 2 CPUs: 
[    0.000001] CPU#0 had -245 usecs TSC skew, fixed it up.
[    0.000003] CPU#1 had 245 usecs TSC skew, fixed it up.
[    0.004000] Brought up 2 CPUs
[    0.034353] migration_cost=213
[    0.034563] Booting paravirtualized kernel on bare hardware
[    0.034647] Time:  1:14:11  Date: 07/05/107
[    0.034673] NET: Registered protocol family 16
[    0.034742] EISA bus registered
[    0.034745] ACPI: bus type pci registered
[    0.070054] PCI: PCI BIOS revision 3.00 entry at 0xfaaf0, last bus=2
[    0.070056] PCI: Using configuration type 1
[    0.070057] Setting up standard PCI resources
[    0.083228] ACPI: Interpreter enabled
[    0.083230] ACPI: Using IOAPIC for interrupt routing
[    0.083777] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.083781] PCI: Probing PCI hardware (bus 00)
[    0.083884] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[    0.084787] Boot video device is 0000:01:00.0
[    0.085665] PCI: Transparent bridge - 0000:00:14.4
[    0.085699] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.102798] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.102997] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.103196] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.103392] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.103588] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 *10 11)
[    0.103784] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 *4 5 6 7 10 11)
[    0.104051] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 10 *11), disabled.
[    0.104249] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 10 *11)
[    0.104552] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[    0.106674] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.106682] pnp: PnP ACPI init
[    0.109136] pnp: PnP ACPI: found 11 devices
[    0.109139] PnPBIOS: Disabled by ACPI PNP
[    0.109179] PCI: Using ACPI for IRQ routing
[    0.109182] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    0.109190] PCI: Cannot allocate resource region 3 of device 0000:00:00.0
[    0.179611] NET: Registered protocol family 8
[    0.179613] NET: Registered protocol family 20
[    0.180004] pnp: 00:01: ioport range 0x228-0x22f has been reserved
[    0.180007] pnp: 00:01: ioport range 0x40b-0x40b has been reserved
[    0.180009] pnp: 00:01: ioport range 0x4d6-0x4d6 has been reserved
[    0.180011] pnp: 00:01: ioport range 0xc00-0xc01 has been reserved
[    0.180013] pnp: 00:01: ioport range 0xc14-0xc14 has been reserved
[    0.180015] pnp: 00:01: ioport range 0xc50-0xc52 has been reserved
[    0.180017] pnp: 00:01: ioport range 0xc6c-0xc6d has been reserved
[    0.180019] pnp: 00:01: ioport range 0xc6f-0xc6f has been reserved
[    0.180262] PCI: Bridge: 0000:00:02.0
[    0.180264]   IO window: e000-efff
[    0.180268]   MEM window: fde00000-fdefffff
[    0.180271]   PREFETCH window: d8000000-dfffffff
[    0.180274] PCI: Bridge: 0000:00:14.4
[    0.180278]   IO window: d000-dfff
[    0.180284]   MEM window: fdd00000-fddfffff
[    0.180288]   PREFETCH window: f8000000-fbffffff
[    0.180302] PCI: Setting latency timer of device 0000:00:02.0 to 64
[    0.180337] NET: Registered protocol family 2
[    0.223660] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.223800] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.224521] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.224891] TCP: Hash tables configured (established 131072 bind 65536)
[    0.224894] TCP reno registered
[    0.239684] checking if image is initramfs... it is
[    0.741967] Freeing initrd memory: 6791k freed
[    1.260000] audit: initializing netlink socket (disabled)
[    1.260000] audit(1186276452.444:1): initialized
[    1.260000] highmem bounce pool size: 64 pages
[    1.260000] VFS: Disk quotas dquot_6.5.1
[    1.260000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.260000] io scheduler noop registered
[    1.260000] io scheduler anticipatory registered
[    1.260000] io scheduler deadline registered
[    1.260000] io scheduler cfq registered (default)
[    1.308000] pci 0000:02:02.0: HCRESET not completed yet!
[    1.308000] pci 0000:02:02.1: HCRESET not completed yet!
[    1.308000] PCI: Setting latency timer of device 0000:00:02.0 to 64
[    1.308000] assign_interrupt_mode Found MSI capability
[    1.308000] Allocate Port Service[0000:00:02.0:pcie00]
[    1.308000] isapnp: Scanning for PnP cards...
[    1.660000] isapnp: No Plug & Play device found
[    1.680000] Real Time Clock Driver v1.12ac
[    1.680000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    1.680000] mice: PS/2 mouse device common for all mice
[    1.680000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    1.680000] input: Macintosh mouse button emulation as /class/input/input0
[    1.680000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[    1.680000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[    1.680000] PNP: PS/2 Controller [PNP0f13:PS2M] at 0x60,0x64 irq 12
[    1.680000] PNP: PS/2 controller doesn't have KBD irq; using default 1
[    1.684000] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.684000] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.684000] EISA: Probing bus 0 at eisa.0
[    1.684000] Cannot allocate resource for EISA slot 4
[    1.684000] EISA: Detected 0 cards.
[    1.716000] TCP cubic registered
[    1.716000] NET: Registered protocol family 1
[    1.716000] Starting balanced_irq
[    1.716000] Using IPI No-Shortcut mode
[    1.716000] ACPI: (supports S0 S1 S3 S4 S5)
[    1.716000]   Magic number: 3:656:204
[    1.716000]   hash matches device ttyt2
[    1.716000] Freeing unused kernel memory: 328k freed
[    1.720000] Time: acpi_pm clocksource has been installed.
[    2.924000] Capability LSM initialized
[    2.960000] ACPI: Processor [CPU0] (supports 8 throttling states)
[    2.960000] ACPI: Processor [CPU1] (supports 8 throttling states)
[    3.396000] usbcore: registered new interface driver usbfs
[    3.396000] usbcore: registered new interface driver hub
[    3.396000] usbcore: registered new device driver usb
[    3.396000] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[    3.396000] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 19 (level, low) -> IRQ 16
[    3.396000] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    3.396000] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
[    3.396000] ohci_hcd 0000:00:13.0: irq 16, io mem 0xfe02e000
[    3.420000] ieee1394: Initialized config rom entry `ip1394'
[    3.452000] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    3.452000] USB Universal Host Controller Interface driver v3.0
[    3.464000] usb usb1: configuration #1 chosen from 1 choice
[    3.464000] hub 1-0:1.0: USB hub found
[    3.464000] hub 1-0:1.0: 4 ports detected
[    3.572000] ACPI: PCI Interrupt 0000:00:13.1[A] -> GSI 19 (level, low) -> IRQ 16
[    3.572000] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    3.572000] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
[    3.572000] ohci_hcd 0000:00:13.1: irq 16, io mem 0xfe02d000
[    3.632000] usb usb2: configuration #1 chosen from 1 choice
[    3.632000] hub 2-0:1.0: USB hub found
[    3.632000] hub 2-0:1.0: 4 ports detected
[    3.744000] SCSI subsystem initialized
[    3.748000] ACPI: PCI Interrupt 0000:00:13.2[A] -> GSI 19 (level, low) -> IRQ 16
[    3.748000] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    3.748000] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
[    3.748000] ehci_hcd 0000:00:13.2: irq 16, io mem 0xfe02c000
[    3.748000] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.748000] usb usb3: configuration #1 chosen from 1 choice
[    3.748000] hub 3-0:1.0: USB hub found
[    3.748000] hub 3-0:1.0: 8 ports detected
[    3.748000] libata version 2.20 loaded.
[    3.852000] ACPI: PCI Interrupt 0000:02:02.2[C] -> GSI 20 (level, low) -> IRQ 17
[    3.856000] ehci_hcd 0000:02:02.2: EHCI Host Controller
[    3.856000] ehci_hcd 0000:02:02.2: new USB bus registered, assigned bus number 4
[    3.856000] ehci_hcd 0000:02:02.2: irq 17, io mem 0xfddfe000
[    3.856000] ehci_hcd 0000:02:02.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.856000] usb usb4: configuration #1 chosen from 1 choice
[    3.856000] hub 4-0:1.0: USB hub found
[    3.856000] hub 4-0:1.0: 4 ports detected
[    3.964000] 8139cp 0000:02:03.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[    3.964000] 8139cp 0000:02:03.0: Try the "8139too" driver instead.
[    3.964000] ACPI: PCI Interrupt 0000:02:02.0[A] -> GSI 22 (level, low) -> IRQ 18
[    3.964000] uhci_hcd 0000:02:02.0: UHCI Host Controller
[    3.964000] uhci_hcd 0000:02:02.0: new USB bus registered, assigned bus number 5
[    3.964000] uhci_hcd 0000:02:02.0: irq 18, io base 0x0000dd00
[    3.964000] usb usb5: configuration #1 chosen from 1 choice
[    3.964000] hub 5-0:1.0: USB hub found
[    3.964000] hub 5-0:1.0: 2 ports detected
[    3.964000] 8139too Fast Ethernet driver 0.9.28
[    4.072000] ACPI: PCI Interrupt 0000:02:02.1[B] -> GSI 23 (level, low) -> IRQ 19
[    4.072000] uhci_hcd 0000:02:02.1: UHCI Host Controller
[    4.072000] uhci_hcd 0000:02:02.1: new USB bus registered, assigned bus number 6
[    4.072000] uhci_hcd 0000:02:02.1: irq 19, io base 0x0000dc00
[    4.072000] usb usb6: configuration #1 chosen from 1 choice
[    4.072000] hub 6-0:1.0: USB hub found
[    4.072000] hub 6-0:1.0: 2 ports detected
[    4.180000] ACPI: PCI Interrupt 0000:02:02.3[A] -> GSI 22 (level, low) -> IRQ 18
[    4.232000] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[18]  MMIO=[fddfd000-fddfd7ff]  Max Packet=[2]  IR/IT contexts=[4/8]
[    4.236000] ohci1394: fw-host0: Serial EEPROM has suspicious values, attempting to setting max_packet_size to 512 bytes
[    4.236000] ACPI: PCI Interrupt 0000:02:04.0[A] -> GSI 21 (level, low) -> IRQ 20
[    4.292000] ohci1394: fw-host1: OHCI-1394 1.1 (PCI): IRQ=[20]  MMIO=[fddfb000-fddfb7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    4.296000] ATIIXP: IDE controller at PCI slot 0000:00:14.1
[    4.296000] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 21
[    4.296000] ATIIXP: chipset revision 0
[    4.296000] ATIIXP: not 100% native mode: will probe irqs later
[    4.296000]     ide0: BM-DMA at 0xf800-0xf807, BIOS settings: hda:pio, hdb:pio
[    4.296000]     ide1: BM-DMA at 0xf808-0xf80f, BIOS settings: hdc:pio, hdd:pio
[    4.296000] Probing IDE interface ide0...
[    4.640000] usb 4-1: new high speed USB device using ehci_hcd and address 2
[    4.784000] usb 4-1: configuration #1 chosen from 1 choice
[    4.868000] Probing IDE interface ide1...
[    5.512000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[001106005350d195]
[    5.612000] hdc: HP DVD Writer 840b, ATAPI CD/DVD-ROM drive
[    5.660000] usb 6-1: new full speed USB device using uhci_hcd and address 2
[    5.788000] ieee1394: Host added: ID:BUS[1-00:1023]  GUID[0010dc0000b83eea]
[    5.828000] usb 6-1: configuration #1 chosen from 1 choice
[    6.072000] usb 6-2: new full speed USB device using uhci_hcd and address 3
[    6.264000] usb 6-2: configuration #1 chosen from 1 choice
[    6.400000] hdd: ASUS DVD-E616P3H, ATAPI CD/DVD-ROM drive
[    6.460000] ide1 at 0x170-0x177,0x376 on irq 15
[    6.460000] sata_sil 0000:00:12.0: version 2.2
[    6.460000] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 22 (level, low) -> IRQ 18
[    6.460000] ata1: SATA max UDMA/100 cmd 0xf887a080 ctl 0xf887a08a bmdma 0xf887a000 irq 18
[    6.460000] ata2: SATA max UDMA/100 cmd 0xf887a0c0 ctl 0xf887a0ca bmdma 0xf887a008 irq 18
[    6.460000] scsi0 : sata_sil
[    6.472000] hdc: ATAPI 40X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(33)
[    6.472000] Uniform CD-ROM driver Revision: 3.20
[    6.476000] hdd: ATAPI 40X DVD-ROM drive, 512kB Cache, UDMA(33)
[    6.572000] usb 2-1: new full speed USB device using ohci_hcd and address 2
[    6.772000] usb 2-1: configuration #1 chosen from 1 choice
[    6.772000] hub 2-1:1.0: USB hub found
[    6.776000] hub 2-1:1.0: 4 ports detected
[    6.928000] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    6.940000] ata1.00: ata_hpa_resize 1: sectors = 145226112, hpa_sectors = 145226112
[    6.940000] ata1.00: ATA-7: WDC WD740ADFD-00NLR1, 20.07P20, max UDMA/133
[    6.940000] ata1.00: 145226112 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    6.952000] ata1.00: ata_hpa_resize 1: sectors = 145226112, hpa_sectors = 145226112
[    6.952000] ata1.00: configured for UDMA/100
[    6.952000] scsi1 : sata_sil
[    7.196000] usb 2-4: new full speed USB device using ohci_hcd and address 3
[    7.400000] usb 2-4: configuration #1 chosen from 1 choice
[    7.420000] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    7.432000] ata2.00: ATA-7: ST3250823AS, 3.03, max UDMA/100
[    7.432000] ata2.00: 488397168 sectors, multi 16: LBA48 
[    7.444000] ata2.00: configured for UDMA/100
[    7.444000] scsi 0:0:0:0: Direct-Access     ATA      WDC WD740ADFD-00 20.0 PQ: 0 ANSI: 5
[    7.444000] scsi 1:0:0:0: Direct-Access     ATA      ST3250823AS      3.03 PQ: 0 ANSI: 5
[    7.444000] ACPI: PCI Interrupt 0000:02:03.0[A] -> GSI 20 (level, low) -> IRQ 17
[    7.444000] eth0: RealTek RTL8139 at 0xf89ea000, 00:13:d3:56:de:b8, IRQ 17
[    7.444000] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[    7.452000] SCSI device sda: 145226112 512-byte hdwr sectors (74356 MB)
[    7.452000] sda: Write Protect is off
[    7.452000] sda: Mode Sense: 00 3a 00 00
[    7.452000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.452000] SCSI device sda: 145226112 512-byte hdwr sectors (74356 MB)
[    7.452000] sda: Write Protect is off
[    7.452000] sda: Mode Sense: 00 3a 00 00
[    7.452000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.452000]  sda: sda1 sda2 sda3
[    7.476000] sd 0:0:0:0: Attached scsi disk sda
[    7.476000] SCSI device sdb: 488397168 512-byte hdwr sectors (250059 MB)
[    7.476000] sdb: Write Protect is off
[    7.476000] sdb: Mode Sense: 00 3a 00 00
[    7.476000] SCSI device sdb: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.476000] SCSI device sdb: 488397168 512-byte hdwr sectors (250059 MB)
[    7.476000] sdb: Write Protect is off
[    7.476000] sdb: Mode Sense: 00 3a 00 00
[    7.476000] SCSI device sdb: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.476000]  sdb: sdb1
[    7.496000] sd 1:0:0:0: Attached scsi disk sdb
[    7.500000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    7.500000] sd 1:0:0:0: Attached scsi generic sg1 type 0
[    7.632000] usb 2-1.1: new low speed USB device using ohci_hcd and address 4
[    7.700000] Attempting manual resume
[    7.700000] swsusp: Resume From Partition 8:3
[    7.700000] PM: Checking swsusp image.
[    7.700000] PM: Resume from disk failed.
[    7.716000] kjournald starting.  Commit interval 5 seconds
[    7.716000] EXT3-fs: mounted filesystem with ordered data mode.
[    7.748000] usb 2-1.1: configuration #1 chosen from 1 choice
[    7.980000] usb 2-1.2: new full speed USB device using ohci_hcd and address 5
[    8.088000] usb 2-1.2: not running at top speed; connect to a high speed hub
[    8.100000] usb 2-1.2: configuration #1 chosen from 1 choice
[    8.332000] usb 2-1.3: new low speed USB device using ohci_hcd and address 6
[   11.424000] usb 2-1.3: device descriptor read/64, error -110
[   11.708000] usb 2-1.3: configuration #1 chosen from 1 choice
[   11.940000] usb 2-1.4: new full speed USB device using ohci_hcd and address 7
[   12.060000] usb 2-1.4: configuration #1 chosen from 1 choice
[   12.180000] usb 2-1.2: USB disconnect, address 5
[   12.260000] usb 2-1.2: new full speed USB device using ohci_hcd and address 8
[   12.368000] usb 2-1.2: not running at top speed; connect to a high speed hub
[   12.380000] usb 2-1.2: configuration #1 chosen from 1 choice
[   12.384000] usbcore: registered new interface driver libusual
[   12.536000] Initializing USB Mass Storage driver...
[   12.536000] scsi2 : SCSI emulation for USB Mass Storage devices
[   12.536000] usb-storage: device found at 3
[   12.536000] usb-storage: waiting for device to settle before scanning
[   12.536000] scsi3 : SCSI emulation for USB Mass Storage devices
[   12.536000] usb-storage: device found at 8
[   12.536000] usb-storage: waiting for device to settle before scanning
[   12.536000] usbcore: registered new interface driver usb-storage
[   12.536000] USB Mass Storage support registered.
[   13.184000] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[   14.360000] Linux agpgart interface v0.102 (c) Dave Jones
[   14.592000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   14.600000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   14.656000] piix4_smbus 0000:00:14.0: Found 0000:00:14.0 device
[   14.740000] Linux video capture interface: v2.00
[   14.756000] NET: Registered protocol family 17
[   14.872000] usbcore: registered new interface driver xpad
[   14.872000] drivers/usb/input/xpad.c: driver for Xbox controllers v0.1.6
[   14.880000] usbcore: registered new interface driver hiddev
[   14.880000] input: PC Speaker as /class/input/input1
[   14.892000] input: Gaming Keyboard as /class/input/input2
[   14.892000] input: USB HID v1.10 Keyboard [Gaming Keyboard] on usb-0000:00:13.1-1.1
[   14.900000] input: Gaming Keyboard as /class/input/input3
[   14.900000] input,hiddev96: USB HID v1.10 Device [Gaming Keyboard] on usb-0000:00:13.1-1.1
[   14.968000] ivtv:  ==================== START INIT IVTV ====================
[   14.968000] ivtv:  version 0.10.1 (tagged release) loading
[   14.968000] ivtv:  Linux version: 2.6.20-16-generic SMP mod_unload 586 
[   14.968000] ivtv:  In case of problems please include the debug info between
[   14.968000] ivtv:  the START INIT IVTV and END INIT IVTV lines, along with
[   14.968000] ivtv:  any module options, when mailing the ivtv-users mailinglist.
[   14.968000] ivtv0: Unknown card: vendor/device: 4444/0016
[   14.968000] ivtv0:               subsystem vendor/device: 1043/4b2e
[   14.968000] ivtv0:               cx23416 based
[   14.968000] ivtv0: Defaulting to Hauppauge WinTV PVR-150 card
[   14.968000] ivtv0: Please mail the vendor/device and subsystem vendor/device IDs and what kind of
[   14.968000] ivtv0: card you have to the ivtv-devel mailinglist (www.ivtvdriver.org)
[   14.968000] ivtv0: Prefix your subject line with [UNKNOWN CARD].
[   14.972000] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 20 (level, low) -> IRQ 17
[   14.992000] parport: PnPBIOS parport detected.
[   14.992000] parport0: PC-style at 0x378, irq 7 [PCSPP,EPP]
[   15.004000] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 2 if 1 alt 0 proto 2 vid 0x04B8 pid 0x0820
[   15.128000] ubuntu/media/gspcav1/gspca_core.c: USB SPCA5XX camera found.(ZC3XX) 
[   15.216000] hiddev97: USB HID v1.10 Device [American Power Conversion Back-UPS BR  800 FW:9.o2 .D USB FW:o2 ] on usb-0000:00:13.1-1.3
[   15.224000] input: G11 Keyboard as /class/input/input4
[   15.224000] input,hiddev98: USB HID v1.11 Keypad [G11 Keyboard] on usb-0000:00:13.1-1.4
[   15.224000] usbcore: registered new interface driver usbhid
[   15.224000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   15.224000] usbcore: registered new interface driver usblp
[   15.224000] drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
[   15.604000] input: ImPS/2 Logitech Wheel Mouse as /class/input/input5
[   15.660000] ivtv0: loaded v4l-cx2341x-enc.fw firmware (262144 bytes)
[   15.788000] usbcore: registered new interface driver gspca
[   15.788000] ubuntu/media/gspcav1/gspca_core.c: gspca driver 01.00.12 registered
[   15.832000] usbcore: registered new interface driver snd-usb-audio
[   15.876000] ivtv0: Encoder revision: 0x02050032
[   15.876000] ivtv0: Recommended firmware version is 0x02060039.
[   15.888000] tveeprom 1-0050: Huh, no eeprom present (err=-121)?
[   15.888000] tveeprom 1-0050: Encountered bad packet header [00]. Corrupt or not a Hauppauge eeprom.
[   15.888000] ivtv0: Invalid EEPROM
[   15.912000] tuner 1-0043: chip found @ 0x86 (ivtv i2c driver #0)
[   15.912000] tda9887 1-0043: tda988[5/6/7] found @ 0x43 (tuner)
[   15.916000] tuner 1-0060: All bytes are equal. It is not a TEA5767
[   15.916000] tuner 1-0060: chip found @ 0xc0 (ivtv i2c driver #0)
[   15.956000] cx25840 1-0044: cx25843-23 found @ 0x88 (ivtv i2c driver #0)
[   17.536000] usb-storage: device scan complete
[   17.540000] usb-storage: device scan complete
[   17.544000] scsi 3:0:0:0: Direct-Access     SanDisk  U3 Cruzer Micro  3.27 PQ: 0 ANSI: 2
[   17.544000] scsi 2:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
[   17.552000] scsi 2:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
[   17.552000] SCSI device sdc: 8015502 512-byte hdwr sectors (4104 MB)
[   17.556000] scsi 2:0:0:2: Direct-Access     Generic  USB SM Reader    1.02 PQ: 0 ANSI: 0
[   17.556000] sdc: Write Protect is off
[   17.556000] sdc: Mode Sense: 03 00 00 00
[   17.556000] sdc: assuming drive cache: write through
[   17.560000] scsi 2:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0
[   17.580000] SCSI device sdc: 8015502 512-byte hdwr sectors (4104 MB)
[   17.588000] sdc: Write Protect is off
[   17.588000] sdc: Mode Sense: 03 00 00 00
[   17.588000] sdc: assuming drive cache: write through
[   17.588000]  sdc: sdc1
[   17.596000] sd 3:0:0:0: Attached scsi removable disk sdc
[   17.596000] sd 3:0:0:0: Attached scsi generic sg2 type 0
[   17.608000] sd 2:0:0:0: Attached scsi removable disk sdd
[   17.608000] sd 2:0:0:0: Attached scsi generic sg3 type 0
[   17.616000] sd 2:0:0:1: Attached scsi removable disk sde
[   17.616000] sd 2:0:0:1: Attached scsi generic sg4 type 0
[   17.628000] sd 2:0:0:2: Attached scsi removable disk sdf
[   17.628000] sd 2:0:0:2: Attached scsi generic sg5 type 0
[   17.644000] sd 2:0:0:3: Attached scsi removable disk sdg
[   17.644000] sd 2:0:0:3: Attached scsi generic sg6 type 0
[   20.764000] cx25840 1-0044: loaded v4l-cx25840.fw firmware (16382 bytes)
[   20.936000] ivtv0: Registered device video1 for encoder MPEG (4 MB)
[   20.936000] ivtv0: Registered device video32 for encoder YUV (2 MB)
[   20.936000] ivtv0: Registered device vbi0 for encoder VBI (1 MB)
[   20.936000] ivtv0: Registered device video24 for encoder PCM audio (1 MB)
[   20.936000] ivtv0: Registered device radio0 for encoder radio
[   20.992000] ivtv0: i2c hardware 0x00000020 (wm8775) not found for command 0x4008646d!
[   21.156000] tuner 1-0060: tuner type not set
[   21.192000] tuner 1-0060: tuner type not set
[   21.316000] ivtv0: Initialized Hauppauge WinTV PVR-150, card #0
[   21.316000] ivtv:  ====================  END INIT IVTV  ====================
[   21.316000] ACPI: PCI Interrupt 0000:00:14.5[B] -> GSI 17 (level, low) -> IRQ 22
[   21.484000] fuse init (API version 7.8)
[   21.504000] lp0: using parport0 (interrupt-driven).
[   21.544000] Adding 1510100k swap on /dev/disk/by-uuid/84f036bb-6018-4d46-a980-ba1e72e12a80.  Priority:-1 extents:1 across:1510100k
[   21.900000] EXT3 FS on sda2, internal journal
[   22.280000] NTFS driver 2.1.28 [Flags: R/O MODULE].
[   22.320000] NTFS volume version 3.1.
[   27.356000] ibm_acpi: ec object not found
[   27.404000] Using specific hotkey driver
[   27.528000] No dock devices found.
[   27.540000] input: Power Button (FF) as /class/input/input6
[   27.540000] ACPI: Power Button (FF) [PWRF]
[   27.540000] input: Power Button (CM) as /class/input/input7
[   27.540000] ACPI: Power Button (CM) [PWRB]
[   27.592000] pcc_acpi: loading...
[   27.736000] powernow-k8: Found 2 AMD Athlon(tm) 64 X2 Dual Core Processor 4200+ processors (version 2.00.00)
[   27.736000] powernow-k8:    0 : fid 0xe (2200 MHz), vid 0x8
[   27.736000] powernow-k8:    1 : fid 0xc (2000 MHz), vid 0xa
[   27.736000] powernow-k8:    2 : fid 0xa (1800 MHz), vid 0xc
[   27.736000] powernow-k8:    3 : fid 0x2 (1000 MHz), vid 0x12
[   33.680000] [drm] Initialized drm 1.1.0 20060810
[   33.684000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 18 (level, low) -> IRQ 23
[   33.688000] [drm] Initialized radeon 1.25.0 20060524 on minor 0
[   34.524000] ppdev: user-space parallel port driver
[   34.952000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   34.952000] apm: disabled - APM is not SMP safe.
[   35.100000] Bluetooth: Core ver 2.11
[   35.100000] NET: Registered protocol family 31
[   35.100000] Bluetooth: HCI device and connection manager initialized
[   35.100000] Bluetooth: HCI socket layer initialized
[   35.132000] Bluetooth: L2CAP ver 2.8
[   35.132000] Bluetooth: L2CAP socket layer initialized
[   35.304000] Bluetooth: RFCOMM socket layer initialized
[   35.304000] Bluetooth: RFCOMM TTY layer initialized
[   35.304000] Bluetooth: RFCOMM ver 1.8
[   47.884000] [drm] Setting GART location based on new memory map
[   47.884000] [drm] Loading R300 Microcode
[   47.884000] [drm] writeback test succeeded in 1 usecs
[   49.184000] NETDEV WATCHDOG: eth0: transmit timed out
[   52.184000] eth0: Transmit timeout, status 0d 0000 c07f media 10.
[   52.184000] eth0: Tx queue start entry 4  dirty entry 0.
[   52.184000] eth0:  Tx descriptor 0 is 00082156. (queue head)
[   52.184000] eth0:  Tx descriptor 1 is 00082156.
[   52.184000] eth0:  Tx descriptor 2 is 00082156.
[   52.184000] eth0:  Tx descriptor 3 is 00082156.
[   52.184000] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[   56.992000] NET: Registered protocol family 10
[   56.992000] lo: Disabled Privacy Extensions
[   64.184000] NETDEV WATCHDOG: eth0: transmit timed out
[   67.184000] eth0: Transmit timeout, status 0d 0000 c07f media 10.
[   67.184000] eth0: Tx queue start entry 4  dirty entry 0.
[   67.184000] eth0:  Tx descriptor 0 is 00082156. (queue head)
[   67.184000] eth0:  Tx descriptor 1 is 00082156.
[   67.184000] eth0:  Tx descriptor 2 is 0008203c.
[   67.184000] eth0:  Tx descriptor 3 is 0008203c.
[   67.184000] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[   67.640000] eth0: no IPv6 routers present
[   75.300000] APIC error on CPU0: 00(40)
[   79.184000] NETDEV WATCHDOG: eth0: transmit timed out
[   82.184000] eth0: Transmit timeout, status 0d 0000 c07f media 10.
[   82.184000] eth0: Tx queue start entry 4  dirty entry 0.
[   82.184000] eth0:  Tx descriptor 0 is 0008203c. (queue head)
[   82.184000] eth0:  Tx descriptor 1 is 0008203c.
[   82.184000] eth0:  Tx descriptor 2 is 0008203c.
[   82.184000] eth0:  Tx descriptor 3 is 00082126.
[   82.184000] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[   94.184000] NETDEV WATCHDOG: eth0: transmit timed out
[   97.184000] eth0: Transmit timeout, status 0d 0000 c07f media 10.
[   97.184000] eth0: Tx queue start entry 4  dirty entry 0.
[   97.184000] eth0:  Tx descriptor 0 is 000820a2. (queue head)
[   97.184000] eth0:  Tx descriptor 1 is 00082126.
[   97.184000] eth0:  Tx descriptor 2 is 00082126.
[   97.184000] eth0:  Tx descriptor 3 is 00082114.
[   97.184000] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[  109.184000] NETDEV WATCHDOG: eth0: transmit timed out
[  112.184000] eth0: Transmit timeout, status 0d 0000 c07f media 10.
[  112.184000] eth0: Tx queue start entry 4  dirty entry 0.
[  112.184000] eth0:  Tx descriptor 0 is 000820a2. (queue head)
[  112.184000] eth0:  Tx descriptor 1 is 0008203c.
[  112.184000] eth0:  Tx descriptor 2 is 00082114.
[  112.184000] eth0:  Tx descriptor 3 is 00082108.
[  112.184000] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[  124.184000] NETDEV WATCHDOG: eth0: transmit timed out
[  127.184000] eth0: Transmit timeout, status 0d 0000 c07f media 10.
[  127.184000] eth0: Tx queue start entry 4  dirty entry 0.
[  127.184000] eth0:  Tx descriptor 0 is 00082156. (queue head)
[  127.184000] eth0:  Tx descriptor 1 is 0008205a.
[  127.184000] eth0:  Tx descriptor 2 is 00082114.
[  127.184000] eth0:  Tx descriptor 3 is 0008203c.
[  127.184000] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[  139.184000] NETDEV WATCHDOG: eth0: transmit timed out
[  142.184000] eth0: Transmit timeout, status 0d 0000 c07f media 10.
[  142.184000] eth0: Tx queue start entry 4  dirty entry 0.
[  142.184000] eth0:  Tx descriptor 0 is 0008204e. (queue head)
[  142.184000] eth0:  Tx descriptor 1 is 0008203c.
[  142.184000] eth0:  Tx descriptor 2 is 00082046.
[  142.184000] eth0:  Tx descriptor 3 is 000820c7.
[  142.184000] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[  154.184000] NETDEV WATCHDOG: eth0: transmit timed out
[  157.184000] eth0: Transmit timeout, status 0d 0000 c07f media 10.
[  157.184000] eth0: Tx queue start entry 4  dirty entry 0.
[  157.184000] eth0:  Tx descriptor 0 is 00082070. (queue head)
[  157.184000] eth0:  Tx descriptor 1 is 0008203c.
[  157.184000] eth0:  Tx descriptor 2 is 000820c7.
[  157.184000] eth0:  Tx descriptor 3 is 000820c7.
[  157.184000] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[  169.184000] NETDEV WATCHDOG: eth0: transmit timed out
[  172.184000] eth0: Transmit timeout, status 0d 0000 c07f media 10.
[  172.184000] eth0: Tx queue start entry 4  dirty entry 0.
[  172.184000] eth0:  Tx descriptor 0 is 00082070. (queue head)
[  172.184000] eth0:  Tx descriptor 1 is 000820bb.
[  172.184000] eth0:  Tx descriptor 2 is 000820bb.
[  172.184000] eth0:  Tx descriptor 3 is 0008203c.
[  172.184000] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[  184.184000] NETDEV WATCHDOG: eth0: transmit timed out
[  187.184000] eth0: Transmit timeout, status 0d 0000 c07f media 10.
[  187.184000] eth0: Tx queue start entry 4  dirty entry 0.
[  187.184000] eth0:  Tx descriptor 0 is 00082046. (queue head)
[  187.184000] eth0:  Tx descriptor 1 is 000820bb.
[  187.184000] eth0:  Tx descriptor 2 is 0008203c.
[  187.184000] eth0:  Tx descriptor 3 is 0008203c.
[  187.184000] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[  199.184000] NETDEV WATCHDOG: eth0: transmit timed out
[  202.184000] eth0: Transmit timeout, status 0d 0000 c07f media 10.
[  202.184000] eth0: Tx queue start entry 4  dirty entry 0.
[  202.184000] eth0:  Tx descriptor 0 is 0008203c. (queue head)
[  202.184000] eth0:  Tx descriptor 1 is 00082046.
[  202.184000] eth0:  Tx descriptor 2 is 0008205a.
[  202.184000] eth0:  Tx descriptor 3 is 0008203c.
[  202.184000] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[  214.184000] NETDEV WATCHDOG: eth0: transmit timed out
[  217.184000] eth0: Transmit timeout, status 0d 0000 c07f media 10.
[  217.184000] eth0: Tx queue start entry 4  dirty entry 0.
[  217.184000] eth0:  Tx descriptor 0 is 0008203c. (queue head)
[  217.184000] eth0:  Tx descriptor 1 is 0008203c.
[  217.184000] eth0:  Tx descriptor 2 is 0008203c.
[  217.184000] eth0:  Tx descriptor 3 is 0008203c.
[  217.184000] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1

```

---

### Post by noob12 on 2007-08-05
I'm going to suggest that we try this suggestion from the kernel.

> 
[    0.109179] PCI: Using ACPI for IRQ routing
[    0.109182] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report


But before we get into that, can you post the output of **lsmod | grep 8139**

---

### Post by rubperezt on 2007-08-05
output:
```

8139too                27648  0 
8139cp                 25088  0 
mii                     6528  2 8139too,8139cp

```

---

### Post by noob12 on 2007-08-05
One more question: was this a clean boot or had you suspended/hibernated Ubuntu previously?

---

### Post by noob12 on 2007-08-05
Please add a line
```

blacklist 8139cp

```
to your /etc/modprobe.d/blacklist file.

Then, I want you to try to reboot, but when you boot when it says Grub is loading hit ESC until you get to the boot menu, and then select the top boot menu choice, click e to edit and use the arrow keys to move down to the line that starts with **kernel**.  Hit e again to edit this line and add the option **pci=routeirq** to the end of that line.  Then ESC , ESC to continue the boot.

I'll want to see the **dmesg** output after this, and will want you to see if the ethernet card starts to work.

---

### Post by rubperezt on 2007-08-05
> **noob12 said:**
> One more question: was this a clean boot or had you suspended/hibernated Ubuntu previously?

Yes, it was.

and no, after adding pci=routeirq to the kernel line, ethernet is still not working.

dmesg:
```

[    0.000000] Linux version 2.6.20-16-generic (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Thu Jun 7 20:19:32 UTC 2007 (Ubuntu 2.6.20-16.29-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009f400 end: 000000000009f400 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009f400 size: 0000000000000c00 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000f0000 size: 0000000000010000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000003fdf0000 end: 000000003fef0000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000003fef0000 size: 0000000000003000 end: 000000003fef3000 type: 4
[    0.000000] copy_e820_map() start: 000000003fef3000 size: 000000000000d000 end: 000000003ff00000 type: 3
[    0.000000] copy_e820_map() start: 00000000e0000000 size: 0000000010000000 end: 00000000f0000000 type: 2
[    0.000000] copy_e820_map() start: 00000000fec00000 size: 0000000001400000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f400 (usable)
[    0.000000]  BIOS-e820: 000000000009f400 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003fef0000 (usable)
[    0.000000]  BIOS-e820: 000000003fef0000 - 000000003fef3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003fef3000 - 000000003ff00000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] 126MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f4730
[    0.000000] Entering add_active_range(0, 0, 261872) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   261872
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   261872
[    0.000000] On node 0 totalpages: 261872
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 253 pages used for memmap
[    0.000000]   HighMem zone: 32243 pages, LIFO batch:7
[    0.000000] DMI 2.4 present.
[    0.000000] ACPI: RSDP (v000 HP-CPC                                ) @ 0x000f8650
[    0.000000] ACPI: RSDT (v001 HP-CPC AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x3fef3040
[    0.000000] ACPI: FADT (v002 HP-CPC AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x3fef30c0
[    0.000000] ACPI: SSDT (v001 HP-CPC POWERNOW 0x00000001  LTP 0x00000001) @ 0x3fef6f40
[    0.000000] ACPI: MCFG (v001 HP-CPC AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x3fef7180
[    0.000000] ACPI: MADT (v001 HP-CPC AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x3fef6e80
[    0.000000] ACPI: DSDT (v001 HP-CPC AWRDACPI 0x00001000 MSFT 0x0100000e) @ 0x00000000
[    0.000000] ATI board detected. Disabling timer routing over 8254.
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:11 APIC version 16
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1 15:11 APIC version 16
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 3ff00000:a0100000)
[    0.000000] Detected 2188.864 MHz processor.
[  139.826215] Built 1 zonelists.  Total pages: 259827
[  139.826218] Kernel command line: root=UUID=4327a9b0-0b96-4e2a-8954-bd67dc235e62 ro quiet splash
[  139.826333] mapped APIC to ffffd000 (fee00000)
[  139.826335] mapped IOAPIC to ffffc000 (fec00000)
[  139.826338] Enabling fast FPU save and restore... done.
[  139.826340] Enabling unmasked SIMD FPU exception support... done.
[  139.826347] Initializing CPU#0
[  139.826403] PID hash table entries: 4096 (order: 12, 16384 bytes)
[  139.827699] Console: colour VGA+ 80x25
[  139.828030] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[  139.828363] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[  139.844775] Memory: 1027300k/1047488k available (1992k kernel code, 19516k reserved, 900k data, 328k init, 129984k highmem)
[  139.844784] virtual kernel memory layout:
[  139.844785]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[  139.844786]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[  139.844788]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[  139.844789]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[  139.844790]       .init : 0xc03d9000 - 0xc042b000   ( 328 kB)
[  139.844791]       .data : 0xc02f2374 - 0xc03d36d4   ( 900 kB)
[  139.844792]       .text : 0xc0100000 - 0xc02f2374   (1992 kB)
[  139.844795] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[  139.922245] Calibrating delay using timer specific routine.. 4382.01 BogoMIPS (lpj=8764032)
[  139.922279] Security Framework v1.0.0 initialized
[  139.922284] SELinux:  Disabled at boot.
[  139.922297] Mount-cache hash table entries: 512
[  139.922412] CPU: After generic identify, caps: 178bfbff e3d3fbff 00000000 00000000 00000001 00000000 00000003
[  139.922419] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[  139.922421] CPU: L2 Cache: 512K (64 bytes/line)
[  139.922424] CPU 0(2) -> Core 0
[  139.922425] CPU: After all inits, caps: 178bfbff e3d3fbff 00000000 00000410 00000001 00000000 00000003
[  139.922434] Compat vDSO mapped to ffffe000.
[  139.922438] Remapping vsyscall page to ffffe000
[  139.922446] Checking 'hlt' instruction... OK.
[  139.938330] SMP alternatives: switching to UP code
[  139.938657] Early unpacking initramfs... done
[  140.193305] ACPI: Core revision 20060707
[  140.202162] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[  140.212583] CPU0: AMD Athlon(tm) 64 X2 Dual Core Processor 4200+ stepping 01
[  140.212604] SMP alternatives: switching to SMP code
[  140.212652] Booting processor 1/1 eip 3000
[  140.223641] Initializing CPU#1
[  140.302407] Calibrating delay using timer specific routine.. 4377.85 BogoMIPS (lpj=8755704)
[  140.302413] CPU: After generic identify, caps: 178bfbff e3d3fbff 00000000 00000000 00000001 00000000 00000003
[  140.302418] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[  140.302420] CPU: L2 Cache: 512K (64 bytes/line)
[  140.302423] CPU 1(2) -> Core 1
[  140.302424] CPU: After all inits, caps: 178bfbff e3d3fbff 00000000 00000410 00000001 00000000 00000003
[  140.301701] CPU1: AMD Athlon(tm) 64 X2 Dual Core Processor 4200+ stepping 01
[  140.301717] Total of 2 processors activated (8759.86 BogoMIPS).
[  140.301879] ENABLING IO-APIC IRQs
[  140.302063] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[  140.341721] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
[  140.341769] ...trying to set up timer (IRQ0) through the 8259A ...  failed.
[  140.341771] ...trying to set up timer as Virtual Wire IRQ... works.
[  140.485275] checking TSC synchronization across 2 CPUs: 
[    0.000001] CPU#0 had -412 usecs TSC skew, fixed it up.
[    0.000003] CPU#1 had 412 usecs TSC skew, fixed it up.
[    0.003994] Brought up 2 CPUs
[    0.077109] migration_cost=226
[    0.077318] Booting paravirtualized kernel on bare hardware
[    0.077401] Time:  2:13:17  Date: 07/05/107
[    0.077426] NET: Registered protocol family 16
[    0.077495] EISA bus registered
[    0.077497] ACPI: bus type pci registered
[    0.112800] PCI: PCI BIOS revision 3.00 entry at 0xfaaf0, last bus=2
[    0.112802] PCI: Using configuration type 1
[    0.112803] Setting up standard PCI resources
[    0.125969] ACPI: Interpreter enabled
[    0.125971] ACPI: Using IOAPIC for interrupt routing
[    0.126516] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.126521] PCI: Probing PCI hardware (bus 00)
[    0.126614] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[    0.127517] Boot video device is 0000:01:00.0
[    0.128407] PCI: Transparent bridge - 0000:00:14.4
[    0.128440] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.145540] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.145739] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.145937] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.146133] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.146327] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 *10 11)
[    0.146523] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 *4 5 6 7 10 11)
[    0.146719] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 10 *11), disabled.
[    0.146914] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 10 *11)
[    0.147200] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[    0.149296] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.149304] pnp: PnP ACPI init
[    0.151700] pnp: PnP ACPI: found 11 devices
[    0.151703] PnPBIOS: Disabled by ACPI PNP
[    0.151756] PCI: Using ACPI for IRQ routing
[    0.151758] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    0.151767] PCI: Cannot allocate resource region 3 of device 0000:00:00.0
[    0.222218] NET: Registered protocol family 8
[    0.222220] NET: Registered protocol family 20
[    0.222638] pnp: 00:01: ioport range 0x228-0x22f has been reserved
[    0.222641] pnp: 00:01: ioport range 0x40b-0x40b has been reserved
[    0.222643] pnp: 00:01: ioport range 0x4d6-0x4d6 has been reserved
[    0.222645] pnp: 00:01: ioport range 0xc00-0xc01 has been reserved
[    0.222647] pnp: 00:01: ioport range 0xc14-0xc14 has been reserved
[    0.222649] pnp: 00:01: ioport range 0xc50-0xc52 has been reserved
[    0.222651] pnp: 00:01: ioport range 0xc6c-0xc6d has been reserved
[    0.222654] pnp: 00:01: ioport range 0xc6f-0xc6f has been reserved
[    0.222896] PCI: Bridge: 0000:00:02.0
[    0.222898]   IO window: e000-efff
[    0.222902]   MEM window: fde00000-fdefffff
[    0.222904]   PREFETCH window: d8000000-dfffffff
[    0.222908] PCI: Bridge: 0000:00:14.4
[    0.222911]   IO window: d000-dfff
[    0.222917]   MEM window: fdd00000-fddfffff
[    0.222922]   PREFETCH window: f8000000-fbffffff
[    0.222937] PCI: Setting latency timer of device 0000:00:02.0 to 64
[    0.222972] NET: Registered protocol family 2
[    0.271585] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.271721] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.272440] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.272812] TCP: Hash tables configured (established 131072 bind 65536)
[    0.272814] TCP reno registered
[    0.283616] checking if image is initramfs... it is
[    0.785968] Freeing initrd memory: 6791k freed
[    1.304000] audit: initializing netlink socket (disabled)
[    1.304000] audit(1186279997.488:1): initialized
[    1.304000] highmem bounce pool size: 64 pages
[    1.304000] VFS: Disk quotas dquot_6.5.1
[    1.304000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.304000] io scheduler noop registered
[    1.304000] io scheduler anticipatory registered
[    1.304000] io scheduler deadline registered
[    1.308000] io scheduler cfq registered (default)
[    1.348000] PCI: Setting latency timer of device 0000:00:02.0 to 64
[    1.348000] assign_interrupt_mode Found MSI capability
[    1.348000] Allocate Port Service[0000:00:02.0:pcie00]
[    1.348000] isapnp: Scanning for PnP cards...
[    1.700000] isapnp: No Plug & Play device found
[    1.720000] Real Time Clock Driver v1.12ac
[    1.720000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    1.720000] mice: PS/2 mouse device common for all mice
[    1.720000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    1.720000] input: Macintosh mouse button emulation as /class/input/input0
[    1.720000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[    1.720000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[    1.720000] PNP: PS/2 Controller [PNP0f13:PS2M] at 0x60,0x64 irq 12
[    1.720000] PNP: PS/2 controller doesn't have KBD irq; using default 1
[    1.724000] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.724000] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.724000] EISA: Probing bus 0 at eisa.0
[    1.724000] Cannot allocate resource for EISA slot 4
[    1.724000] EISA: Detected 0 cards.
[    1.756000] TCP cubic registered
[    1.756000] NET: Registered protocol family 1
[    1.756000] Starting balanced_irq
[    1.756000] Using IPI No-Shortcut mode
[    1.756000] ACPI: (supports S0 S1 S3 S4 S5)
[    1.756000]   Magic number: 3:762:206
[    1.756000]   hash matches device ttyt4
[    1.756000] Freeing unused kernel memory: 328k freed
[    1.760000] Time: acpi_pm clocksource has been installed.
[    2.964000] Capability LSM initialized
[    3.000000] ACPI: Processor [CPU0] (supports 8 throttling states)
[    3.000000] ACPI: Processor [CPU1] (supports 8 throttling states)
[    3.440000] usbcore: registered new interface driver usbfs
[    3.440000] usbcore: registered new interface driver hub
[    3.440000] usbcore: registered new device driver usb
[    3.468000] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[    3.468000] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 19 (level, low) -> IRQ 16
[    3.468000] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    3.468000] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
[    3.468000] ohci_hcd 0000:00:13.0: irq 16, io mem 0xfe02e000
[    3.488000] ieee1394: Initialized config rom entry `ip1394'
[    3.500000] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    3.504000] USB Universal Host Controller Interface driver v3.0
[    3.528000] usb usb1: configuration #1 chosen from 1 choice
[    3.528000] hub 1-0:1.0: USB hub found
[    3.528000] hub 1-0:1.0: 4 ports detected
[    3.636000] SCSI subsystem initialized
[    3.636000] ACPI: PCI Interrupt 0000:02:02.3[A] -> GSI 22 (level, low) -> IRQ 17
[    3.640000] ACPI: PCI Interrupt 0000:00:13.1[A] -> GSI 19 (level, low) -> IRQ 16
[    3.640000] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    3.640000] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
[    3.640000] ohci_hcd 0000:00:13.1: irq 16, io mem 0xfe02d000
[    3.688000] libata version 2.20 loaded.
[    3.692000] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[17]  MMIO=[fddfd000-fddfd7ff]  Max Packet=[2]  IR/IT contexts=[4/8]
[    3.700000] ohci1394: fw-host0: Serial EEPROM has suspicious values, attempting to setting max_packet_size to 512 bytes
[    3.704000] ACPI: PCI Interrupt 0000:02:04.0[A] -> GSI 21 (level, low) -> IRQ 18
[    3.704000] usb usb2: configuration #1 chosen from 1 choice
[    3.704000] hub 2-0:1.0: USB hub found
[    3.704000] hub 2-0:1.0: 4 ports detected
[    3.756000] ohci1394: fw-host1: OHCI-1394 1.1 (PCI): IRQ=[18]  MMIO=[fddfb000-fddfb7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    3.808000] ACPI: PCI Interrupt 0000:00:13.2[A] -> GSI 19 (level, low) -> IRQ 16
[    3.808000] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    3.808000] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
[    3.808000] ehci_hcd 0000:00:13.2: irq 16, io mem 0xfe02c000
[    3.808000] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.808000] usb usb3: configuration #1 chosen from 1 choice
[    3.808000] hub 3-0:1.0: USB hub found
[    3.808000] hub 3-0:1.0: 8 ports detected
[    3.912000] ATIIXP: IDE controller at PCI slot 0000:00:14.1
[    3.912000] ACPI: PCI Interrupt 0000:02:02.2[C] -> GSI 20 (level, low) -> IRQ 19
[    3.912000] ehci_hcd 0000:02:02.2: EHCI Host Controller
[    3.912000] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 20
[    3.912000] ATIIXP: chipset revision 0
[    3.912000] ATIIXP: not 100% native mode: will probe irqs later
[    3.912000] ehci_hcd 0000:02:02.2: new USB bus registered, assigned bus number 4
[    3.912000]     ide0: BM-DMA at 0xf800-0xf807, BIOS settings: hda:pio, hdb:pio
[    3.912000]     ide1: BM-DMA at 0xf808-0xf80f, BIOS settings: hdc:pio, hdd:pio
[    3.912000] Probing IDE interface ide0...
[    3.912000] ehci_hcd 0000:02:02.2: irq 19, io mem 0xfddfe000
[    3.912000] ehci_hcd 0000:02:02.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.912000] usb usb4: configuration #1 chosen from 1 choice
[    3.912000] hub 4-0:1.0: USB hub found
[    3.912000] hub 4-0:1.0: 4 ports detected
[    4.480000] Probing IDE interface ide1...
[    4.704000] usb 4-1: new high speed USB device using ehci_hcd and address 2
[    4.840000] usb 4-1: configuration #1 chosen from 1 choice
[    4.976000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[001106005350d195]
[    5.216000] hdc: HP DVD Writer 840b, ATAPI CD/DVD-ROM drive
[    5.248000] ieee1394: Host added: ID:BUS[1-00:1023]  GUID[0010dc0000b83eea]
[    5.516000] usb 2-1: new full speed USB device using ohci_hcd and address 2
[    5.720000] usb 2-1: configuration #1 chosen from 1 choice
[    5.720000] hub 2-1:1.0: USB hub found
[    5.724000] hub 2-1:1.0: 4 ports detected
[    6.000000] hdd: ASUS DVD-E616P3H, ATAPI CD/DVD-ROM drive
[    6.056000] ide1 at 0x170-0x177,0x376 on irq 15
[    6.060000] 8139cp 0000:02:03.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[    6.060000] 8139cp 0000:02:03.0: Try the "8139too" driver instead.
[    6.060000] ACPI: PCI Interrupt 0000:02:02.0[A] -> GSI 22 (level, low) -> IRQ 17
[    6.060000] uhci_hcd 0000:02:02.0: UHCI Host Controller
[    6.060000] uhci_hcd 0000:02:02.0: new USB bus registered, assigned bus number 5
[    6.060000] uhci_hcd 0000:02:02.0: irq 17, io base 0x0000dd00
[    6.060000] usb usb5: configuration #1 chosen from 1 choice
[    6.060000] hub 5-0:1.0: USB hub found
[    6.060000] hub 5-0:1.0: 2 ports detected
[    6.060000] 8139too Fast Ethernet driver 0.9.28
[    6.144000] usb 2-4: new full speed USB device using ohci_hcd and address 3
[    6.164000] ACPI: PCI Interrupt 0000:02:02.1[B] -> GSI 23 (level, low) -> IRQ 21
[    6.164000] uhci_hcd 0000:02:02.1: UHCI Host Controller
[    6.164000] uhci_hcd 0000:02:02.1: new USB bus registered, assigned bus number 6
[    6.164000] uhci_hcd 0000:02:02.1: irq 21, io base 0x0000dc00
[    6.164000] usb usb6: configuration #1 chosen from 1 choice
[    6.164000] hub 6-0:1.0: USB hub found
[    6.164000] hub 6-0:1.0: 2 ports detected
[    6.268000] ACPI: PCI Interrupt 0000:02:03.0[A] -> GSI 20 (level, low) -> IRQ 19
[    6.268000] eth0: RealTek RTL8139 at 0xf8870000, 00:13:d3:56:de:b8, IRQ 19
[    6.268000] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[    6.268000] sata_sil 0000:00:12.0: version 2.2
[    6.268000] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 22 (level, low) -> IRQ 17
[    6.268000] ata1: SATA max UDMA/100 cmd 0xf8872080 ctl 0xf887208a bmdma 0xf8872000 irq 17
[    6.268000] ata2: SATA max UDMA/100 cmd 0xf88720c0 ctl 0xf88720ca bmdma 0xf8872008 irq 17
[    6.268000] scsi0 : sata_sil
[    6.288000] hdc: ATAPI 40X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(33)
[    6.288000] Uniform CD-ROM driver Revision: 3.20
[    6.292000] hdd: ATAPI 40X DVD-ROM drive, 512kB Cache, UDMA(33)
[    6.352000] usb 2-4: configuration #1 chosen from 1 choice
[    6.560000] usb 2-1.1: new low speed USB device using ohci_hcd and address 4
[    6.664000] usb 2-1.1: configuration #1 chosen from 1 choice
[    6.736000] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    6.744000] ata1.00: ata_hpa_resize 1: sectors = 145226112, hpa_sectors = 145226112
[    6.744000] ata1.00: ATA-7: WDC WD740ADFD-00NLR1, 20.07P20, max UDMA/133
[    6.744000] ata1.00: 145226112 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    6.752000] ata1.00: ata_hpa_resize 1: sectors = 145226112, hpa_sectors = 145226112
[    6.752000] ata1.00: configured for UDMA/100
[    6.752000] scsi1 : sata_sil
[    6.876000] usb 2-1.3: new low speed USB device using ohci_hcd and address 5
[    7.220000] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    7.228000] ata2.00: ATA-7: ST3250823AS, 3.03, max UDMA/100
[    7.228000] ata2.00: 488397168 sectors, multi 16: LBA48 
[    7.236000] ata2.00: configured for UDMA/100
[    7.236000] scsi 0:0:0:0: Direct-Access     ATA      WDC WD740ADFD-00 20.0 PQ: 0 ANSI: 5
[    7.236000] scsi 1:0:0:0: Direct-Access     ATA      ST3250823AS      3.03 PQ: 0 ANSI: 5
[    7.244000] SCSI device sda: 145226112 512-byte hdwr sectors (74356 MB)
[    7.244000] sda: Write Protect is off
[    7.244000] sda: Mode Sense: 00 3a 00 00
[    7.244000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.244000] SCSI device sda: 145226112 512-byte hdwr sectors (74356 MB)
[    7.244000] sda: Write Protect is off
[    7.244000] sda: Mode Sense: 00 3a 00 00
[    7.244000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.244000]  sda: sda1 sda2 sda3
[    7.260000] sd 0:0:0:0: Attached scsi disk sda
[    7.260000] SCSI device sdb: 488397168 512-byte hdwr sectors (250059 MB)
[    7.260000] sdb: Write Protect is off
[    7.260000] sdb: Mode Sense: 00 3a 00 00
[    7.260000] SCSI device sdb: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.260000] SCSI device sdb: 488397168 512-byte hdwr sectors (250059 MB)
[    7.260000] sdb: Write Protect is off
[    7.260000] sdb: Mode Sense: 00 3a 00 00
[    7.260000] SCSI device sdb: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.260000]  sdb: sdb1
[    7.276000] sd 1:0:0:0: Attached scsi disk sdb
[    7.280000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    7.280000] sd 1:0:0:0: Attached scsi generic sg1 type 0
[    7.420000] Attempting manual resume
[    7.420000] swsusp: Resume From Partition 8:3
[    7.420000] PM: Checking swsusp image.
[    7.420000] PM: Resume from disk failed.
[    7.432000] kjournald starting.  Commit interval 5 seconds
[    7.432000] EXT3-fs: mounted filesystem with ordered data mode.
[    9.948000] usb 2-1.3: device descriptor read/64, error -110
[   10.668000] usb 2-1.3: configuration #1 chosen from 1 choice
[   10.880000] usb 2-1.4: new full speed USB device using ohci_hcd and address 6
[   10.988000] usb 2-1.4: configuration #1 chosen from 1 choice
[   11.488000] usb 6-1: new full speed USB device using uhci_hcd and address 2
[   11.656000] usb 6-1: configuration #1 chosen from 1 choice
[   11.900000] usb 6-2: new full speed USB device using uhci_hcd and address 3
[   12.092000] usb 6-2: configuration #1 chosen from 1 choice
[   12.140000] usbcore: registered new interface driver libusual
[   12.140000] usbcore: registered new interface driver hiddev
[   12.200000] input: Gaming Keyboard as /class/input/input1
[   12.200000] input: USB HID v1.10 Keyboard [Gaming Keyboard] on usb-0000:00:13.1-1.1
[   12.208000] input: Gaming Keyboard as /class/input/input2
[   12.208000] input,hiddev96: USB HID v1.10 Device [Gaming Keyboard] on usb-0000:00:13.1-1.1
[   12.220000] Initializing USB Mass Storage driver...
[   12.220000] scsi2 : SCSI emulation for USB Mass Storage devices
[   12.220000] usb-storage: device found at 3
[   12.220000] usb-storage: waiting for device to settle before scanning
[   12.524000] hiddev97: USB HID v1.10 Device [American Power Conversion Back-UPS BR  800 FW:9.o2 .D USB FW:o2 ] on usb-0000:00:13.1-1.3
[   12.532000] input: G11 Keyboard as /class/input/input3
[   12.532000] input,hiddev98: USB HID v1.11 Keypad [G11 Keyboard] on usb-0000:00:13.1-1.4
[   12.532000] usbcore: registered new interface driver usbhid
[   12.532000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   12.532000] usbcore: registered new interface driver usb-storage
[   12.532000] USB Mass Storage support registered.
[   12.912000] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[   14.076000] input: PC Speaker as /class/input/input4
[   14.192000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   14.212000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   14.212000] Linux agpgart interface v0.102 (c) Dave Jones
[   14.356000] NET: Registered protocol family 17
[   14.364000] Linux video capture interface: v2.00
[   14.408000] ivtv:  ==================== START INIT IVTV ====================
[   14.408000] ivtv:  version 0.10.1 (tagged release) loading
[   14.408000] ivtv:  Linux version: 2.6.20-16-generic SMP mod_unload 586 
[   14.408000] ivtv:  In case of problems please include the debug info between
[   14.408000] ivtv:  the START INIT IVTV and END INIT IVTV lines, along with
[   14.408000] ivtv:  any module options, when mailing the ivtv-users mailinglist.
[   14.408000] ivtv0: Unknown card: vendor/device: 4444/0016
[   14.408000] ivtv0:               subsystem vendor/device: 1043/4b2e
[   14.408000] ivtv0:               cx23416 based
[   14.408000] ivtv0: Defaulting to Hauppauge WinTV PVR-150 card
[   14.408000] ivtv0: Please mail the vendor/device and subsystem vendor/device IDs and what kind of
[   14.408000] ivtv0: card you have to the ivtv-devel mailinglist (www.ivtvdriver.org)
[   14.408000] ivtv0: Prefix your subject line with [UNKNOWN CARD].
[   14.456000] piix4_smbus 0000:00:14.0: Found 0000:00:14.0 device
[   14.456000] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 20 (level, low) -> IRQ 19
[   14.532000] usbcore: registered new interface driver xpad
[   14.532000] drivers/usb/input/xpad.c: driver for Xbox controllers v0.1.6
[   14.556000] parport: PnPBIOS parport detected.
[   14.556000] parport0: PC-style at 0x378, irq 7 [PCSPP,EPP]
[   14.640000] ubuntu/media/gspcav1/gspca_core.c: USB SPCA5XX camera found.(ZC3XX) 
[   14.708000] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 2 if 1 alt 0 proto 2 vid 0x04B8 pid 0x0820
[   14.812000] input: ImPS/2 Logitech Wheel Mouse as /class/input/input5
[   15.128000] ivtv0: loaded v4l-cx2341x-enc.fw firmware (262144 bytes)
[   15.252000] usbcore: registered new interface driver gspca
[   15.252000] ubuntu/media/gspcav1/gspca_core.c: gspca driver 01.00.12 registered
[   15.252000] usbcore: registered new interface driver usblp
[   15.252000] drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
[   15.344000] ivtv0: Encoder revision: 0x02050032
[   15.344000] ivtv0: Recommended firmware version is 0x02060039.
[   15.352000] tveeprom 1-0050: Huh, no eeprom present (err=-121)?
[   15.352000] tveeprom 1-0050: Encountered bad packet header [02]. Corrupt or not a Hauppauge eeprom.
[   15.352000] ivtv0: Invalid EEPROM
[   15.372000] tuner 1-0043: chip found @ 0x86 (ivtv i2c driver #0)
[   15.372000] tda9887 1-0043: tda988[5/6/7] found @ 0x43 (tuner)
[   15.376000] tuner 1-0060: All bytes are equal. It is not a TEA5767
[   15.376000] tuner 1-0060: chip found @ 0xc0 (ivtv i2c driver #0)
[   15.416000] cx25840 1-0044: cx25843-23 found @ 0x88 (ivtv i2c driver #0)
[   15.420000] usbcore: registered new interface driver snd-usb-audio
[   17.228000] usb-storage: device scan complete
[   17.244000] scsi 2:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
[   17.248000] scsi 2:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
[   17.256000] scsi 2:0:0:2: Direct-Access     Generic  USB SM Reader    1.02 PQ: 0 ANSI: 0
[   17.260000] scsi 2:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0
[   17.272000] sd 2:0:0:0: Attached scsi removable disk sdc
[   17.272000] sd 2:0:0:0: Attached scsi generic sg2 type 0
[   17.280000] sd 2:0:0:1: Attached scsi removable disk sdd
[   17.280000] sd 2:0:0:1: Attached scsi generic sg3 type 0
[   17.292000] sd 2:0:0:2: Attached scsi removable disk sde
[   17.292000] sd 2:0:0:2: Attached scsi generic sg4 type 0
[   17.304000] sd 2:0:0:3: Attached scsi removable disk sdf
[   17.304000] sd 2:0:0:3: Attached scsi generic sg5 type 0
[   20.228000] cx25840 1-0044: loaded v4l-cx25840.fw firmware (16382 bytes)
[   20.396000] ivtv0: Registered device video1 for encoder MPEG (4 MB)
[   20.396000] ivtv0: Registered device video32 for encoder YUV (2 MB)
[   20.396000] ivtv0: Registered device vbi0 for encoder VBI (1 MB)
[   20.396000] ivtv0: Registered device video24 for encoder PCM audio (1 MB)
[   20.396000] ivtv0: Registered device radio0 for encoder radio
[   20.452000] ivtv0: i2c hardware 0x00000020 (wm8775) not found for command 0x4008646d!
[   20.616000] tuner 1-0060: tuner type not set
[   20.652000] tuner 1-0060: tuner type not set
[   20.772000] ivtv0: Initialized Hauppauge WinTV PVR-150, card #0
[   20.772000] ivtv:  ====================  END INIT IVTV  ====================
[   20.772000] ACPI: PCI Interrupt 0000:00:14.5[B] -> GSI 17 (level, low) -> IRQ 22
[   20.920000] fuse init (API version 7.8)
[   20.928000] lp0: using parport0 (interrupt-driven).
[   20.976000] Adding 1510100k swap on /dev/disk/by-uuid/84f036bb-6018-4d46-a980-ba1e72e12a80.  Priority:-1 extents:1 across:1510100k
[   21.128000] EXT3 FS on sda2, internal journal
[   21.296000] NTFS driver 2.1.28 [Flags: R/O MODULE].
[   21.332000] NTFS volume version 3.1.
[   26.328000] ibm_acpi: ec object not found
[   26.360000] Using specific hotkey driver
[   26.464000] No dock devices found.
[   26.472000] input: Power Button (FF) as /class/input/input6
[   26.472000] ACPI: Power Button (FF) [PWRF]
[   26.472000] input: Power Button (CM) as /class/input/input7
[   26.472000] ACPI: Power Button (CM) [PWRB]
[   26.532000] pcc_acpi: loading...
[   26.676000] powernow-k8: Found 2 AMD Athlon(tm) 64 X2 Dual Core Processor 4200+ processors (version 2.00.00)
[   26.676000] powernow-k8:    0 : fid 0xe (2200 MHz), vid 0x8
[   26.676000] powernow-k8:    1 : fid 0xc (2000 MHz), vid 0xa
[   26.676000] powernow-k8:    2 : fid 0xa (1800 MHz), vid 0xc
[   26.676000] powernow-k8:    3 : fid 0x2 (1000 MHz), vid 0x12
[   32.152000] [drm] Initialized drm 1.1.0 20060810
[   32.160000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 18 (level, low) -> IRQ 23
[   32.160000] [drm] Initialized radeon 1.25.0 20060524 on minor 0
[   32.976000] ppdev: user-space parallel port driver
[   33.396000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   33.396000] apm: disabled - APM is not SMP safe.
[   33.544000] Bluetooth: Core ver 2.11
[   33.544000] NET: Registered protocol family 31
[   33.544000] Bluetooth: HCI device and connection manager initialized
[   33.544000] Bluetooth: HCI socket layer initialized
[   33.572000] Bluetooth: L2CAP ver 2.8
[   33.572000] Bluetooth: L2CAP socket layer initialized
[   33.744000] Bluetooth: RFCOMM socket layer initialized
[   33.744000] Bluetooth: RFCOMM TTY layer initialized
[   33.744000] Bluetooth: RFCOMM ver 1.8
[   38.568000] APIC error on CPU1: 00(40)
[   42.876000] APIC error on CPU0: 00(40)
[   42.912000] NETDEV WATCHDOG: eth0: transmit timed out
[   44.308000] APIC error on CPU0: 40(40)
[   45.912000] eth0: Transmit timeout, status 0d 0000 c07f media 10.
[   45.912000] eth0: Tx queue start entry 4  dirty entry 0.
[   45.912000] eth0:  Tx descriptor 0 is 00082156. (queue head)
[   45.912000] eth0:  Tx descriptor 1 is 00082156.
[   45.912000] eth0:  Tx descriptor 2 is 00082156.
[   45.912000] eth0:  Tx descriptor 3 is 00082156.
[   45.912000] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[   47.384000] [drm] Setting GART location based on new memory map
[   47.384000] [drm] Loading R300 Microcode
[   47.384000] [drm] writeback test succeeded in 1 usecs
[   55.800000] NET: Registered protocol family 10
[   55.800000] lo: Disabled Privacy Extensions
[   57.912000] NETDEV WATCHDOG: eth0: transmit timed out
[   60.912000] eth0: Transmit timeout, status 0d 0000 c07f media 10.
[   60.912000] eth0: Tx queue start entry 4  dirty entry 0.
[   60.912000] eth0:  Tx descriptor 0 is 00082156. (queue head)
[   60.912000] eth0:  Tx descriptor 1 is 00082156.
[   60.912000] eth0:  Tx descriptor 2 is 0008203c.
[   60.912000] eth0:  Tx descriptor 3 is 00082156.
[   60.912000] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[   63.000000] APIC error on CPU0: 40(40)
[   64.432000] APIC error on CPU0: 40(40)
[   65.868000] APIC error on CPU1: 40(40)
[   66.184000] eth0: no IPv6 routers present
[   72.912000] NETDEV WATCHDOG: eth0: transmit timed out
[   75.912000] eth0: Transmit timeout, status 0d 0000 c07f media 10.
[   75.912000] eth0: Tx queue start entry 4  dirty entry 0.
[   75.912000] eth0:  Tx descriptor 0 is 0008203c. (queue head)
[   75.912000] eth0:  Tx descriptor 1 is 0008203c.
[   75.912000] eth0:  Tx descriptor 2 is 0008203c.
[   75.912000] eth0:  Tx descriptor 3 is 0008203c.
[   75.912000] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[   87.912000] NETDEV WATCHDOG: eth0: transmit timed out
[   88.852000] APIC error on CPU1: 40(40)
[   90.912000] eth0: Transmit timeout, status 0d 0000 c07f media 10.
[   90.912000] eth0: Tx queue start entry 4  dirty entry 0.
[   90.912000] eth0:  Tx descriptor 0 is 00082124. (queue head)
[   90.912000] eth0:  Tx descriptor 1 is 000820a2.
[   90.912000] eth0:  Tx descriptor 2 is 00082124.
[   90.912000] eth0:  Tx descriptor 3 is 00082124.
[   90.912000] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1

```

---

### Post by noob12 on 2007-08-05
My instructions must suck, because somehow you didn't get the option set right.  The dmesg output tells us what options it thinks it got, and still doesn't show the option.

> 
[   28.463195] Kernel command line: root=UUID=4327a9b0-0b96-4e2a-8954-bd67dc235e62 ro quiet splash


I'll try to post a better step by step in a minute.  I must have led you astray somehow.

---

### Post by noob12 on 2007-08-05
Ok.  On the last step.  After editing the entry.  Only one ESC, and then type b to boot.  I think the second ESC lost the edit.


Can you **cat /etc/blacklist** as well?  The 8139cp driver loaded this time again.  I wasn't expecting that.

---

### Post by rubperezt on 2007-08-05
Done:
[CODE]
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

# buggy driver causes kernel BUG on load (Ubuntu: #78255, #88430)
blacklist r818x
blacklist r8187

#noob12 recomendation to resolve the internet problem with dualboot
blacklist 8139cp
[CODE]


also the other time i modefied the kernel line i pressed enter instead of esc because esc would delete the changes.

btw your instructions are not bad, they are great but im 100% new into linux world. thanks for your help!

---

### Post by noob12 on 2007-08-05
To verify that this fixed the issue we were seeing with the ethernet, we need to see **dmesg** again.  

Did the network come up this time?

---

### Post by rubperezt on 2007-08-05
here is the dmesg

```
[    0.000000] Linux version 2.6.20-16-generic (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Thu Jun 7 20:19:32 UTC 2007 (Ubuntu 2.6.20-16.29-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009f400 end: 000000000009f400 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009f400 size: 0000000000000c00 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000f0000 size: 0000000000010000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000003fdf0000 end: 000000003fef0000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000003fef0000 size: 0000000000003000 end: 000000003fef3000 type: 4
[    0.000000] copy_e820_map() start: 000000003fef3000 size: 000000000000d000 end: 000000003ff00000 type: 3
[    0.000000] copy_e820_map() start: 00000000e0000000 size: 0000000010000000 end: 00000000f0000000 type: 2
[    0.000000] copy_e820_map() start: 00000000fec00000 size: 0000000001400000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f400 (usable)
[    0.000000]  BIOS-e820: 000000000009f400 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003fef0000 (usable)
[    0.000000]  BIOS-e820: 000000003fef0000 - 000000003fef3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003fef3000 - 000000003ff00000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] 126MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f4730
[    0.000000] Entering add_active_range(0, 0, 261872) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   261872
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   261872
[    0.000000] On node 0 totalpages: 261872
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 253 pages used for memmap
[    0.000000]   HighMem zone: 32243 pages, LIFO batch:7
[    0.000000] DMI 2.4 present.
[    0.000000] ACPI: RSDP (v000 HP-CPC                                ) @ 0x000f8650
[    0.000000] ACPI: RSDT (v001 HP-CPC AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x3fef3040
[    0.000000] ACPI: FADT (v002 HP-CPC AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x3fef30c0
[    0.000000] ACPI: SSDT (v001 HP-CPC POWERNOW 0x00000001  LTP 0x00000001) @ 0x3fef6f40
[    0.000000] ACPI: MCFG (v001 HP-CPC AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x3fef7180
[    0.000000] ACPI: MADT (v001 HP-CPC AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x3fef6e80
[    0.000000] ACPI: DSDT (v001 HP-CPC AWRDACPI 0x00001000 MSFT 0x0100000e) @ 0x00000000
[    0.000000] ATI board detected. Disabling timer routing over 8254.
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:11 APIC version 16
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1 15:11 APIC version 16
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 3ff00000:a0100000)
[    0.000000] Detected 2188.987 MHz processor.
[   71.001179] Built 1 zonelists.  Total pages: 259827
[   71.001183] Kernel command line: root=UUID=4327a9b0-0b96-4e2a-8954-bd67dc235e62 ro quiet splash
[   71.001297] mapped APIC to ffffd000 (fee00000)
[   71.001299] mapped IOAPIC to ffffc000 (fec00000)
[   71.001302] Enabling fast FPU save and restore... done.
[   71.001304] Enabling unmasked SIMD FPU exception support... done.
[   71.001310] Initializing CPU#0
[   71.001367] PID hash table entries: 4096 (order: 12, 16384 bytes)
[   71.002656] Console: colour VGA+ 80x25
[   71.002985] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   71.003318] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   71.019725] Memory: 1027300k/1047488k available (1992k kernel code, 19516k reserved, 900k data, 328k init, 129984k highmem)
[   71.019733] virtual kernel memory layout:
[   71.019734]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   71.019735]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   71.019737]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   71.019738]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   71.019739]       .init : 0xc03d9000 - 0xc042b000   ( 328 kB)
[   71.019740]       .data : 0xc02f2374 - 0xc03d36d4   ( 900 kB)
[   71.019741]       .text : 0xc0100000 - 0xc02f2374   (1992 kB)
[   71.019744] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   71.097209] Calibrating delay using timer specific routine.. 4382.00 BogoMIPS (lpj=8764016)
[   71.097243] Security Framework v1.0.0 initialized
[   71.097249] SELinux:  Disabled at boot.
[   71.097262] Mount-cache hash table entries: 512
[   71.097376] CPU: After generic identify, caps: 178bfbff e3d3fbff 00000000 00000000 00000001 00000000 00000003
[   71.097383] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   71.097385] CPU: L2 Cache: 512K (64 bytes/line)
[   71.097388] CPU 0(2) -> Core 0
[   71.097389] CPU: After all inits, caps: 178bfbff e3d3fbff 00000000 00000410 00000001 00000000 00000003
[   71.097398] Compat vDSO mapped to ffffe000.
[   71.097402] Remapping vsyscall page to ffffe000
[   71.097410] Checking 'hlt' instruction... OK.
[   71.113295] SMP alternatives: switching to UP code
[   71.113623] Early unpacking initramfs... done
[   71.368270] ACPI: Core revision 20060707
[   71.377127] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   71.387519] CPU0: AMD Athlon(tm) 64 X2 Dual Core Processor 4200+ stepping 01
[   71.387541] SMP alternatives: switching to SMP code
[   71.387589] Booting processor 1/1 eip 3000
[   71.399015] Initializing CPU#1
[   71.477808] Calibrating delay using timer specific routine.. 4377.92 BogoMIPS (lpj=8755854)
[   71.477814] CPU: After generic identify, caps: 178bfbff e3d3fbff 00000000 00000000 00000001 00000000 00000003
[   71.477820] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   71.477822] CPU: L2 Cache: 512K (64 bytes/line)
[   71.477824] CPU 1(2) -> Core 1
[   71.477825] CPU: After all inits, caps: 178bfbff e3d3fbff 00000000 00000410 00000001 00000000 00000003
[   71.476738] CPU1: AMD Athlon(tm) 64 X2 Dual Core Processor 4200+ stepping 01
[   71.476753] Total of 2 processors activated (8759.93 BogoMIPS).
[   71.476915] ENABLING IO-APIC IRQs
[   71.477099] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   71.516757] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
[   71.516805] ...trying to set up timer (IRQ0) through the 8259A ...  failed.
[   71.516807] ...trying to set up timer as Virtual Wire IRQ... works.
[   71.664230] checking TSC synchronization across 2 CPUs: 
[    0.000001] CPU#0 had -631 usecs TSC skew, fixed it up.
[    0.000003] CPU#1 had 631 usecs TSC skew, fixed it up.
[    0.003995] Brought up 2 CPUs
[    0.077121] migration_cost=219
[    0.077331] Booting paravirtualized kernel on bare hardware
[    0.077413] Time:  3:14:00  Date: 07/05/107
[    0.077439] NET: Registered protocol family 16
[    0.077507] EISA bus registered
[    0.077510] ACPI: bus type pci registered
[    0.112810] PCI: PCI BIOS revision 3.00 entry at 0xfaaf0, last bus=2
[    0.112812] PCI: Using configuration type 1
[    0.112813] Setting up standard PCI resources
[    0.125980] ACPI: Interpreter enabled
[    0.125982] ACPI: Using IOAPIC for interrupt routing
[    0.126527] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.126531] PCI: Probing PCI hardware (bus 00)
[    0.126625] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[    0.127527] Boot video device is 0000:01:00.0
[    0.128415] PCI: Transparent bridge - 0000:00:14.4
[    0.128449] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.144714] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.144913] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.145112] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.145307] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.145502] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 *10 11)
[    0.145697] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 *4 5 6 7 10 11)
[    0.145893] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 10 *11), disabled.
[    0.146088] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 10 *11)
[    0.146375] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[    0.148512] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.148520] pnp: PnP ACPI init
[    0.150966] pnp: PnP ACPI: found 11 devices
[    0.150969] PnPBIOS: Disabled by ACPI PNP
[    0.151011] PCI: Using ACPI for IRQ routing
[    0.151013] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    0.151022] PCI: Cannot allocate resource region 3 of device 0000:00:00.0
[    0.221470] NET: Registered protocol family 8
[    0.221471] NET: Registered protocol family 20
[    0.221853] pnp: 00:01: ioport range 0x228-0x22f has been reserved
[    0.221855] pnp: 00:01: ioport range 0x40b-0x40b has been reserved
[    0.221858] pnp: 00:01: ioport range 0x4d6-0x4d6 has been reserved
[    0.221860] pnp: 00:01: ioport range 0xc00-0xc01 has been reserved
[    0.221862] pnp: 00:01: ioport range 0xc14-0xc14 has been reserved
[    0.221864] pnp: 00:01: ioport range 0xc50-0xc52 has been reserved
[    0.221866] pnp: 00:01: ioport range 0xc6c-0xc6d has been reserved
[    0.221868] pnp: 00:01: ioport range 0xc6f-0xc6f has been reserved
[    0.222105] PCI: Bridge: 0000:00:02.0
[    0.222108]   IO window: e000-efff
[    0.222111]   MEM window: fde00000-fdefffff
[    0.222114]   PREFETCH window: d8000000-dfffffff
[    0.222118] PCI: Bridge: 0000:00:14.4
[    0.222121]   IO window: d000-dfff
[    0.222127]   MEM window: fdd00000-fddfffff
[    0.222132]   PREFETCH window: f8000000-fbffffff
[    0.222146] PCI: Setting latency timer of device 0000:00:02.0 to 64
[    0.222180] NET: Registered protocol family 2
[    0.263589] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.263726] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.264446] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.264817] TCP: Hash tables configured (established 131072 bind 65536)
[    0.264820] TCP reno registered
[    0.279614] checking if image is initramfs... it is
[    0.781486] Freeing initrd memory: 6791k freed
[    1.304000] audit: initializing netlink socket (disabled)
[    1.304000] audit(1186283640.488:1): initialized
[    1.304000] highmem bounce pool size: 64 pages
[    1.304000] VFS: Disk quotas dquot_6.5.1
[    1.304000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.304000] io scheduler noop registered
[    1.304000] io scheduler anticipatory registered
[    1.304000] io scheduler deadline registered
[    1.304000] io scheduler cfq registered (default)
[    1.344000] pci 0000:02:02.0: HCRESET not completed yet!
[    1.344000] pci 0000:02:02.1: HCRESET not completed yet!
[    1.344000] PCI: Setting latency timer of device 0000:00:02.0 to 64
[    1.344000] assign_interrupt_mode Found MSI capability
[    1.344000] Allocate Port Service[0000:00:02.0:pcie00]
[    1.344000] isapnp: Scanning for PnP cards...
[    1.696000] isapnp: No Plug & Play device found
[    1.716000] Real Time Clock Driver v1.12ac
[    1.716000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    1.716000] mice: PS/2 mouse device common for all mice
[    1.716000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    1.716000] input: Macintosh mouse button emulation as /class/input/input0
[    1.716000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[    1.716000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[    1.716000] PNP: PS/2 Controller [PNP0f13:PS2M] at 0x60,0x64 irq 12
[    1.716000] PNP: PS/2 controller doesn't have KBD irq; using default 1
[    1.720000] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.720000] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.720000] EISA: Probing bus 0 at eisa.0
[    1.720000] Cannot allocate resource for EISA slot 4
[    1.720000] EISA: Detected 0 cards.
[    1.748000] TCP cubic registered
[    1.748000] NET: Registered protocol family 1
[    1.748000] Starting balanced_irq
[    1.748000] Using IPI No-Shortcut mode
[    1.748000] ACPI: (supports<6>Time: acpi_pm clocksource has been installed.
[    1.752000]  S0 S1 S3 S4 S5)
[    1.752000]   Magic number: 3:868:208
[    1.752000]   hash matches device ttyt6
[    1.752000]   hash matches device vcsa
[    1.752000] Freeing unused kernel memory: 328k freed
[    2.940000] Capability LSM initialized
[    2.976000] ACPI: Processor [CPU0] (supports 8 throttling states)
[    2.976000] ACPI: Processor [CPU1] (supports 8 throttling states)
[    3.404000] usbcore: registered new interface driver usbfs
[    3.404000] usbcore: registered new interface driver hub
[    3.432000] usbcore: registered new device driver usb
[    3.436000] ATIIXP: IDE controller at PCI slot 0000:00:14.1
[    3.436000] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 16
[    3.436000] ATIIXP: chipset revision 0
[    3.436000] ATIIXP: not 100% native mode: will probe irqs later
[    3.436000]     ide0: BM-DMA at 0xf800-0xf807, BIOS settings: hda:pio, hdb:pio
[    3.436000]     ide1: BM-DMA at 0xf808-0xf80f, BIOS settings: hdc:pio, hdd:pio
[    3.436000] Probing IDE interface ide0...
[    3.448000] ieee1394: Initialized config rom entry `ip1394'
[    3.480000] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[    3.492000] USB Universal Host Controller Interface driver v3.0
[    3.504000] SCSI subsystem initialized
[    3.508000] libata version 2.20 loaded.
[    3.512000] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    4.008000] Probing IDE interface ide1...
[    4.752000] hdc: HP DVD Writer 840b, ATAPI CD/DVD-ROM drive
[    5.540000] hdd: ASUS DVD-E616P3H, ATAPI CD/DVD-ROM drive
[    5.600000] ide1 at 0x170-0x177,0x376 on irq 15
[    5.604000] ACPI: PCI Interrupt 0000:02:02.3[A] -> GSI 22 (level, low) -> IRQ 17
[    5.612000] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 19 (level, low) -> IRQ 18
[    5.612000] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    5.616000] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
[    5.616000] ohci_hcd 0000:00:13.0: irq 18, io mem 0xfe02e000
[    5.656000] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[17]  MMIO=[fddfd000-fddfd7ff]  Max Packet=[2]  IR/IT contexts=[4/8]
[    5.664000] ohci1394: fw-host0: Serial EEPROM has suspicious values, attempting to setting max_packet_size to 512 bytes
[    5.664000] ACPI: PCI Interrupt 0000:02:04.0[A] -> GSI 21 (level, low) -> IRQ 19
[    5.680000] usb usb1: configuration #1 chosen from 1 choice
[    5.680000] hub 1-0:1.0: USB hub found
[    5.680000] hub 1-0:1.0: 4 ports detected
[    5.716000] ohci1394: fw-host1: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[fddfb000-fddfb7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    5.788000] ACPI: PCI Interrupt 0000:00:13.1[A] -> GSI 19 (level, low) -> IRQ 18
[    5.788000] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    5.788000] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
[    5.788000] ohci_hcd 0000:00:13.1: irq 18, io mem 0xfe02d000
[    5.852000] usb usb2: configuration #1 chosen from 1 choice
[    5.852000] hub 2-0:1.0: USB hub found
[    5.852000] hub 2-0:1.0: 4 ports detected
[    5.960000] ACPI: PCI Interrupt 0000:00:13.2[A] -> GSI 19 (level, low) -> IRQ 18
[    5.960000] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    5.960000] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
[    5.960000] ehci_hcd 0000:00:13.2: irq 18, io mem 0xfe02c000
[    5.960000] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    5.960000] usb usb3: configuration #1 chosen from 1 choice
[    5.960000] hub 3-0:1.0: USB hub found
[    5.960000] hub 3-0:1.0: 8 ports detected
[    6.068000] ACPI: PCI Interrupt 0000:02:02.2[C] -> GSI 20 (level, low) -> IRQ 20
[    6.068000] ehci_hcd 0000:02:02.2: EHCI Host Controller
[    6.068000] ehci_hcd 0000:02:02.2: new USB bus registered, assigned bus number 4
[    6.068000] ehci_hcd 0000:02:02.2: irq 20, io mem 0xfddfe000
[    6.068000] ehci_hcd 0000:02:02.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    6.068000] usb usb4: configuration #1 chosen from 1 choice
[    6.068000] hub 4-0:1.0: USB hub found
[    6.068000] hub 4-0:1.0: 4 ports detected
[    6.176000] ACPI: PCI Interrupt 0000:02:02.0[A] -> GSI 22 (level, low) -> IRQ 17
[    6.176000] uhci_hcd 0000:02:02.0: UHCI Host Controller
[    6.176000] uhci_hcd 0000:02:02.0: new USB bus registered, assigned bus number 5
[    6.176000] uhci_hcd 0000:02:02.0: irq 17, io base 0x0000dd00
[    6.176000] usb usb5: configuration #1 chosen from 1 choice
[    6.176000] hub 5-0:1.0: USB hub found
[    6.176000] hub 5-0:1.0: 2 ports detected
[    6.284000] ACPI: PCI Interrupt 0000:02:02.1[B] -> GSI 23 (level, low) -> IRQ 21
[    6.284000] uhci_hcd 0000:02:02.1: UHCI Host Controller
[    6.284000] uhci_hcd 0000:02:02.1: new USB bus registered, assigned bus number 6
[    6.284000] uhci_hcd 0000:02:02.1: irq 21, io base 0x0000dc00
[    6.284000] usb usb6: configuration #1 chosen from 1 choice
[    6.284000] hub 6-0:1.0: USB hub found
[    6.284000] hub 6-0:1.0: 2 ports detected
[    6.392000] 8139cp 0000:02:03.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[    6.392000] 8139cp 0000:02:03.0: Try the "8139too" driver instead.
[    6.392000] 8139too Fast Ethernet driver 0.9.28
[    6.392000] ACPI: PCI Interrupt 0000:02:03.0[A] -> GSI 20 (level, low) -> IRQ 20
[    6.392000] eth0: RealTek RTL8139 at 0xf887a000, 00:13:d3:56:de:b8, IRQ 20
[    6.392000] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[    6.392000] sata_sil 0000:00:12.0: version 2.2
[    6.392000] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 22 (level, low) -> IRQ 17
[    6.392000] ata1: SATA max UDMA/100 cmd 0xf88b2080 ctl 0xf88b208a bmdma 0xf88b2000 irq 17
[    6.392000] ata2: SATA max UDMA/100 cmd 0xf88b20c0 ctl 0xf88b20ca bmdma 0xf88b2008 irq 17
[    6.392000] scsi0 : sata_sil
[    6.412000] hdc: ATAPI 40X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(33)
[    6.412000] Uniform CD-ROM driver Revision: 3.20
[    6.416000] hdd: ATAPI 40X DVD-ROM drive, 512kB Cache, UDMA(33)
[    6.860000] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    6.864000] usb 4-1: new high speed USB device using ehci_hcd and address 2
[    6.876000] ata1.00: ata_hpa_resize 1: sectors = 145226112, hpa_sectors = 145226112
[    6.876000] ata1.00: ATA-7: WDC WD740ADFD-00NLR1, 20.07P20, max UDMA/133
[    6.876000] ata1.00: 145226112 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    6.888000] ata1.00: ata_hpa_resize 1: sectors = 145226112, hpa_sectors = 145226112
[    6.888000] ata1.00: configured for UDMA/100
[    6.888000] scsi1 : sata_sil
[    6.944000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[001106005350d195]
[    7.008000] usb 4-1: configuration #1 chosen from 1 choice
[    7.220000] ieee1394: Host added: ID:BUS[1-00:1023]  GUID[0010dc0000b83eea]
[    7.356000] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    7.372000] ata2.00: ATA-7: ST3250823AS, 3.03, max UDMA/100
[    7.372000] ata2.00: 488397168 sectors, multi 16: LBA48 
[    7.384000] ata2.00: configured for UDMA/100
[    7.384000] scsi 0:0:0:0: Direct-Access     ATA      WDC WD740ADFD-00 20.0 PQ: 0 ANSI: 5
[    7.384000] scsi 1:0:0:0: Direct-Access     ATA      ST3250823AS      3.03 PQ: 0 ANSI: 5
[    7.388000] SCSI device sda: 145226112 512-byte hdwr sectors (74356 MB)
[    7.388000] sda: Write Protect is off
[    7.388000] sda: Mode Sense: 00 3a 00 00
[    7.388000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.388000] SCSI device sda: 145226112 512-byte hdwr sectors (74356 MB)
[    7.388000] sda: Write Protect is off
[    7.388000] sda: Mode Sense: 00 3a 00 00
[    7.388000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.388000]  sda: sda1 sda2 sda3
[    7.408000] sd 0:0:0:0: Attached scsi disk sda
[    7.408000] SCSI device sdb: 488397168 512-byte hdwr sectors (250059 MB)
[    7.408000] sdb: Write Protect is off
[    7.408000] sdb: Mode Sense: 00 3a 00 00
[    7.408000] SCSI device sdb: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.408000] SCSI device sdb: 488397168 512-byte hdwr sectors (250059 MB)
[    7.408000] sdb: Write Protect is off
[    7.408000] sdb: Mode Sense: 00 3a 00 00
[    7.408000] SCSI device sdb: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.408000]  sdb: sdb1
[    7.428000] sd 1:0:0:0: Attached scsi disk sdb
[    7.432000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    7.432000] sd 1:0:0:0: Attached scsi generic sg1 type 0
[    7.620000] Attempting manual resume
[    7.620000] swsusp: Resume From Partition 8:3
[    7.620000] PM: Checking swsusp image.
[    7.620000] PM: Resume from disk failed.
[    7.640000] kjournald starting.  Commit interval 5 seconds
[    7.640000] EXT3-fs: mounted filesystem with ordered data mode.
[    7.884000] usb 6-1: new full speed USB device using uhci_hcd and address 2
[    8.056000] usb 6-1: configuration #1 chosen from 1 choice
[    8.300000] usb 6-2: new full speed USB device using uhci_hcd and address 3
[    8.492000] usb 6-2: configuration #1 chosen from 1 choice
[    8.800000] usb 2-1: new full speed USB device using ohci_hcd and address 2
[    9.000000] usb 2-1: configuration #1 chosen from 1 choice
[    9.000000] hub 2-1:1.0: USB hub found
[    9.004000] hub 2-1:1.0: 4 ports detected
[    9.424000] usb 2-4: new full speed USB device using ohci_hcd and address 3
[    9.628000] usb 2-4: configuration #1 chosen from 1 choice
[    9.860000] usb 2-1.1: new low speed USB device using ohci_hcd and address 4
[    9.976000] usb 2-1.1: configuration #1 chosen from 1 choice
[   10.208000] usb 2-1.2: new full speed USB device using ohci_hcd and address 5
[   10.316000] usb 2-1.2: not running at top speed; connect to a high speed hub
[   10.328000] usb 2-1.2: configuration #1 chosen from 1 choice
[   10.560000] usb 2-1.3: new low speed USB device using ohci_hcd and address 6
[   13.056000] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[   13.652000] usb 2-1.3: device descriptor read/64, error -110
[   13.936000] usb 2-1.3: configuration #1 chosen from 1 choice
[   14.156000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   14.164000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   14.168000] usb 2-1.4: new full speed USB device using ohci_hcd and address 7
[   14.192000] Linux video capture interface: v2.00
[   14.224000] Linux agpgart interface v0.102 (c) Dave Jones
[   14.288000] usb 2-1.4: configuration #1 chosen from 1 choice
[   14.392000] tveeprom: Unknown symbol i2c_probe
[   14.392000] tveeprom: Unknown symbol i2c_master_recv
[   14.392000] tveeprom: Unknown symbol i2c_register_driver
[   14.392000] tveeprom: Unknown symbol i2c_del_driver
[   14.392000] tveeprom: Unknown symbol i2c_detach_client
[   14.392000] tveeprom: Unknown symbol i2c_attach_client
[   14.392000] tveeprom: Unknown symbol i2c_master_send
[   14.396000] i2c_algo_bit: Unknown symbol i2c_add_adapter
[   14.420000] ivtv: Unknown symbol i2c_bit_add_bus
[   14.420000] ivtv: Unknown symbol i2c_del_adapter
[   14.420000] ivtv: Unknown symbol tveeprom_read
[   14.420000] ivtv: Unknown symbol i2c_clients_command
[   14.420000] ivtv: Unknown symbol i2c_add_adapter
[   14.420000] ivtv: Unknown symbol tveeprom_hauppauge_analog
[   14.464000] piix4_smbus 0000:00:14.0: Found 0000:00:14.0 device
[   14.624000] parport: PnPBIOS parport detected.
[   14.624000] parport0: PC-style at 0x378, irq 7 [PCSPP,EPP]
[   14.624000] NET: Registered protocol family 17
[   14.700000] input: PC Speaker as /class/input/input1
[   14.732000] usbcore: registered new interface driver hiddev
[   14.800000] input: Gaming Keyboard as /class/input/input2
[   14.800000] input: USB HID v1.10 Keyboard [Gaming Keyboard] on usb-0000:00:13.1-1.1
[   14.812000] input: Gaming Keyboard as /class/input/input3
[   14.812000] input,hiddev96: USB HID v1.10 Device [Gaming Keyboard] on usb-0000:00:13.1-1.1
[   14.828000] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 2 if 1 alt 0 proto 2 vid 0x04B8 pid 0x0820
[   14.932000] ubuntu/media/gspcav1/gspca_core.c: USB SPCA5XX camera found.(ZC3XX) 
[   14.940000] usb 2-1.2: USB disconnect, address 5
[   15.004000] ACPI: PCI Interrupt 0000:00:14.5[B] -> GSI 17 (level, low) -> IRQ 22
[   15.024000] usb 2-1.2: new full speed USB device using ohci_hcd and address 8
[   15.128000] usb 2-1.2: not running at top speed; connect to a high speed hub
[   15.140000] usb 2-1.2: configuration #1 chosen from 1 choice
[   15.172000] hiddev97: USB HID v1.10 Device [American Power Conversion Back-UPS BR  800 FW:9.o2 .D USB FW:o2 ] on usb-0000:00:13.1-1.3
[   15.180000] input: G11 Keyboard as /class/input/input4
[   15.180000] input,hiddev98: USB HID v1.11 Keypad [G11 Keyboard] on usb-0000:00:13.1-1.4
[   15.180000] usbcore: registered new interface driver usbhid
[   15.180000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   15.180000] usbcore: registered new interface driver usblp
[   15.180000] drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
[   15.180000] usbcore: registered new interface driver libusual
[   15.300000] Initializing USB Mass Storage driver...
[   15.380000] input: ImPS/2 Logitech Wheel Mouse as /class/input/input5
[   15.608000] usbcore: registered new interface driver xpad
[   15.608000] drivers/usb/input/xpad.c: driver for Xbox controllers v0.1.6
[   15.608000] usbcore: registered new interface driver gspca
[   15.608000] ubuntu/media/gspcav1/gspca_core.c: gspca driver 01.00.12 registered
[   15.616000] scsi2 : SCSI emulation for USB Mass Storage devices
[   15.616000] usb-storage: device found at 3
[   15.616000] usb-storage: waiting for device to settle before scanning
[   15.616000] scsi3 : SCSI emulation for USB Mass Storage devices
[   15.616000] usb-storage: device found at 8
[   15.616000] usb-storage: waiting for device to settle before scanning
[   15.616000] usbcore: registered new interface driver usb-storage
[   15.616000] USB Mass Storage support registered.
[   15.724000] usbcore: registered new interface driver snd-usb-audio
[   15.852000] fuse init (API version 7.8)
[   15.864000] lp0: using parport0 (interrupt-driven).
[   15.908000] Adding 1510100k swap on /dev/disk/by-uuid/84f036bb-6018-4d46-a980-ba1e72e12a80.  Priority:-1 extents:1 across:1510100k
[   16.028000] EXT3 FS on sda2, internal journal
[   16.212000] NTFS driver 2.1.28 [Flags: R/O MODULE].
[   16.252000] NTFS volume version 3.1.
[   20.616000] usb-storage: device scan complete
[   20.620000] usb-storage: device scan complete
[   20.624000] scsi 3:0:0:0: Direct-Access     SanDisk  U3 Cruzer Micro  3.27 PQ: 0 ANSI: 2
[   20.624000] scsi 2:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
[   20.632000] scsi 2:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
[   20.632000] SCSI device sdc: 8015502 512-byte hdwr sectors (4104 MB)
[   20.636000] scsi 2:0:0:2: Direct-Access     Generic  USB SM Reader    1.02 PQ: 0 ANSI: 0
[   20.640000] sdc: Write Protect is off
[   20.640000] sdc: Mode Sense: 03 00 00 00
[   20.640000] sdc: assuming drive cache: write through
[   20.644000] scsi 2:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0
[   20.664000] SCSI device sdc: 8015502 512-byte hdwr sectors (4104 MB)
[   20.668000] sdc: Write Protect is off
[   20.668000] sdc: Mode Sense: 03 00 00 00
[   20.668000] sdc: assuming drive cache: write through
[   20.668000]  sdc: sdc1
[   20.680000] sd 3:0:0:0: Attached scsi removable disk sdc
[   20.680000] sd 3:0:0:0: Attached scsi generic sg2 type 0
[   20.688000] sd 2:0:0:0: Attached scsi removable disk sdd
[   20.688000] sd 2:0:0:0: Attached scsi generic sg3 type 0
[   20.700000] sd 2:0:0:1: Attached scsi removable disk sde
[   20.700000] sd 2:0:0:1: Attached scsi generic sg4 type 0
[   20.708000] sd 2:0:0:2: Attached scsi removable disk sdf
[   20.708000] sd 2:0:0:2: Attached scsi generic sg5 type 0
[   20.716000] sd 2:0:0:3: Attached scsi removable disk sdg
[   20.716000] sd 2:0:0:3: Attached scsi generic sg6 type 0
[   21.308000] ibm_acpi: ec object not found
[   21.344000] Using specific hotkey driver
[   21.448000] No dock devices found.
[   21.456000] input: Power Button (FF) as /class/input/input6
[   21.456000] ACPI: Power Button (FF) [PWRF]
[   21.456000] input: Power Button (CM) as /class/input/input7
[   21.456000] ACPI: Power Button (CM) [PWRB]
[   21.548000] pcc_acpi: loading...
[   21.704000] powernow-k8: Found 2 AMD Athlon(tm) 64 X2 Dual Core Processor 4200+ processors (version 2.00.00)
[   21.704000] powernow-k8:    0 : fid 0xe (2200 MHz), vid 0x8
[   21.704000] powernow-k8:    1 : fid 0xc (2000 MHz), vid 0xa
[   21.704000] powernow-k8:    2 : fid 0xa (1800 MHz), vid 0xc
[   21.704000] powernow-k8:    3 : fid 0x2 (1000 MHz), vid 0x12
[   27.688000] [drm] Initialized drm 1.1.0 20060810
[   27.700000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 18 (level, low) -> IRQ 23
[   27.700000] [drm] Initialized radeon 1.25.0 20060524 on minor 0
[   28.568000] ppdev: user-space parallel port driver
[   29.008000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   29.008000] apm: disabled - APM is not SMP safe.
[   29.156000] Bluetooth: Core ver 2.11
[   29.156000] NET: Registered protocol family 31
[   29.156000] Bluetooth: HCI device and connection manager initialized
[   29.156000] Bluetooth: HCI socket layer initialized
[   29.180000] Bluetooth: L2CAP ver 2.8
[   29.180000] Bluetooth: L2CAP socket layer initialized
[   29.364000] Bluetooth: RFCOMM socket layer initialized
[   29.364000] Bluetooth: RFCOMM TTY layer initialized
[   29.364000] Bluetooth: RFCOMM ver 1.8
[   42.120000] [drm] Setting GART location based on new memory map
[   42.120000] [drm] Loading R300 Microcode
[   42.120000] [drm] writeback test succeeded in 1 usecs
[   49.056000] NETDEV WATCHDOG: eth0: transmit timed out
[   52.056000] eth0: Transmit timeout, status 0d 0000 c07f media 10.
[   52.056000] eth0: Tx queue start entry 4  dirty entry 0.
[   52.056000] eth0:  Tx descriptor 0 is 00082156. (queue head)
[   52.056000] eth0:  Tx descriptor 1 is 00082156.
[   52.056000] eth0:  Tx descriptor 2 is 00082156.
[   52.056000] eth0:  Tx descriptor 3 is 00082156.
[   52.056000] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[   52.452000] NET: Registered protocol family 10
[   52.452000] lo: Disabled Privacy Extensions
[   63.252000] eth0: no IPv6 routers present
[   64.056000] NETDEV WATCHDOG: eth0: transmit timed out
[   67.056000] eth0: Transmit timeout, status 0d 0000 c07f media 10.
[   67.056000] eth0: Tx queue start entry 4  dirty entry 0.
[   67.056000] eth0:  Tx descriptor 0 is 00082156. (queue head)
[   67.056000] eth0:  Tx descriptor 1 is 00082156.
[   67.056000] eth0:  Tx descriptor 2 is 0008203c.
[   67.056000] eth0:  Tx descriptor 3 is 0008203c.
[   67.056000] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[   79.056000] NETDEV WATCHDOG: eth0: transmit timed out
[   82.056000] eth0: Transmit timeout, status 0d 0000 c07f media 10.
[   82.056000] eth0: Tx queue start entry 4  dirty entry 0.
[   82.056000] eth0:  Tx descriptor 0 is 0008203c. (queue head)
[   82.056000] eth0:  Tx descriptor 1 is 0008203c.
[   82.056000] eth0:  Tx descriptor 2 is 0008203c.
[   82.056000] eth0:  Tx descriptor 3 is 0008205a.
[   82.056000] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1


```

---

### Post by noob12 on 2007-08-05
Nope.  Still not setting the option.

> 
[   71.001183] Kernel command line: root=UUID=4327a9b0-0b96-4e2a-8954-bd67dc235e62 ro quiet splash


Here.  Let's try to set it in the grub configuration itself. No editing at boot.

```

cd /boot/grub
xhost +
sudo gedit menu.lst

```

Find the first line that says
```

kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=4327a9b0-0b96-4e2a-8954-bd67dc235e62 ro quiet splash

```
On the end of that line add **pci=routeirq**

Save and exit.  Reboot.  No editing this time.  Just let it boot, but sorry, we need to capture dmesg after it and verify what happened.

---

### Post by AcworthJack on 2007-08-12
Hi - I am seeing the exact same problem - but there is no answer in this thread.  Did you get it working?

I am running 2.6.20-15 low latency (the latest installed by WUBI Ubuntu).  I have been looking at avahi as the problem - with no progress.

Any luck in solving this problem with the Realtek lan card?

thanks,
John

---

### Post by AcworthJack on 2007-08-12
As documented elsewhere - I unplugged my PC for a minute, rebooted into Ubuntu (without going into Windows) and all worked fine!

see [http://gentoo-wiki.com/HARDWARE_RTL8168#Troubleshooting](http://gentoo-wiki.com/HARDWARE_RTL8168#Troubleshooting) for details

:)

---

### Post by darkangel on 2007-08-14
I had this exact problem after Vista upgraded the Ethernet driver a week or so ago as part of automatic updates. As mentioned above, pulling the plug for a few seconds does the trick.

---

