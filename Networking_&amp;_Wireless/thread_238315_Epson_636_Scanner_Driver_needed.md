---
title: "Epson 636 Scanner Driver needed"
date: 2006-08-17
forum: Networking &amp; Wireless
---

### Post by wantolrn on 2006-08-17
Beginning user: Can't find the driver for Epson 636 Scanner 
Tried going to Epson's homesite & other web-googled sites, but failed.
Don't know what to do...anyone help me find the driver?:confused: 
------------------------------------------------------------------------------------

---

### Post by zxee on 2006-08-17
You are in luck the scanner is supported in sane [http://www.sane-project.org/cgi-bin/driver.pl?manu=epson&model=636&bus=any&v=&p=](http://www.sane-project.org/cgi-bin/driver.pl?manu=epson&model=636&bus=any&v=&p=)
Have you tried opening (from the Applications Menu) Graphics>Xsane Image Scanner?
If that doesn't work you may need to do some commandline stuff. Is your scanner usb or scsi?
Try opening Xsane first though and let us know how that goes.

---

### Post by wantolrn on 2006-08-17
Hi...thanks for the quick response.
Tried going to graphic menu, but response was negative.
The 636 Epson scanner is a SCSI.; don't know if it is color or B/W
I went to the XSANE add.but can't figure what to do next...command line needed?--don't know how to write specific commands.:confused:

---

### Post by zxee on 2006-08-17
First open a terminal i.e Applications>Acessories>Terminal and type > sane-find-scanner
You will also need to know the system address for your scanner and perhaps make a link to it. So while in the terminal do dmesg and look for your scanner or post the output.

---

### Post by wantolrn on 2006-08-17
Hi again...went to Terminal & here's the output...(what to do next?):
*I tried key stokes control c and control v  But not copy terminal data--
how do I post this long list of terminal info?:confused:

---

### Post by zxee on 2006-08-17
You can use the mouse in the terminal when the Xserver is running. So just highlight the text like you would in a word processor and right click-copy then paste here. You can also use the commands from the edit menu.

---

### Post by wantolrn on 2006-08-18
Here's the 2nd "copy/paste" try w/ help from the previous thread...(don't know why I didn't try it after my previous attempt).  There are two sections to this attempt--the first is obvious that the computer didn't recognize my turned-on/plugged in Epson 636 scanner; the second is way beyond my comprehension, therefore, I still at a loss for a driver. Thanks for your assistance & sorry to get back late in responding to the thread.:confused: 


guest@freekbox:~$ sane-find-scanner

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a SCSI driver for your SCSI adapter.
  # Also you need support for SCSI Generic (sg) in your operating system.
  # If using Linux, try "modprobe sg".

  # No USB scanners found. If you expected something different, make sure that
  # you have loaded a driver for your USB host controller and have installed a
  # kernel scanner module.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.
guest@freekbox:~$ dmesg
 16K, L1 D cache: 16K
[4294667.963000] CPU: L2 cache: 256K
[4294667.963000] CPU serial number disabled.
[4294667.963000] CPU: After all inits, caps: 0383f9ff 00000000 00000000 00000040 00000000 00000000 00000000
[4294667.963000] CPU: Intel Pentium III (Coppermine) stepping 03
[4294667.963000] Enabling fast FPU save and restore... done.
[4294667.963000] Enabling unmasked SIMD FPU exception support... done.
[4294667.963000] Checking 'hlt' instruction... OK.
[4294667.967000] Checking for popad bug... OK.
[4294667.967000] checking if image is initramfs... it is
[4294669.097000] Freeing initrd memory: 5165k freed
[4294669.105000] ACPI: Looking for DSDT in initrd... not found!
[4294669.267000]  not found!
[4294669.275000] ACPI: setting ELCR to 0020 (from 0c20)
[4294670.079000] NET: Registered protocol family 16
[4294670.079000] EISA bus registered
[4294670.079000] ACPI: bus type pci registered
[4294670.095000] PCI: PCI BIOS revision 2.10 entry at 0xfb1a0, last bus=1
[4294670.095000] PCI: Using configuration type 1
[4294670.095000] mtrr: v2.0 (20020519)
[4294670.096000] ACPI: Subsystem revision 20050729
[4294670.110000] ACPI: Interpreter enabled
[4294670.110000] ACPI: Using PIC for interrupt routing
[4294670.111000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[4294670.111000] PCI: Probing PCI hardware (bus 00)
[4294670.111000] ACPI: Assume root bridge [\_SB_.PCI0] segment is 0
[4294670.111000] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[4294670.116000] Boot video device is 0000:01:00.0
[4294670.119000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[4294670.121000] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 *11 12 14 15)
[4294670.122000] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 *5 6 7 10 11 12 14 15)
[4294670.123000] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 *5 6 7 10 11 12 14 15)
[4294670.124000] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 *10 11 12 14 15)
[4294670.130000] Linux Plug and Play Support v0.97 (c) Adam Belay
[4294670.130000] pnp: PnP ACPI init
[4294670.137000] pnp: PnP ACPI: found 12 devices
[4294670.137000] PnPBIOS: Disabled by ACPI PNP
[4294670.138000] PCI: Using ACPI for IRQ routing
[4294670.138000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[4294670.163000] audit: initializing netlink socket (disabled)
[4294670.163000] audit: initialized
[4294670.163000] VFS: Disk quotas dquot_6.5.1
[4294670.163000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[4294670.163000] devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
[4294670.163000] devfs: boot_options: 0x0
[4294670.164000] Initializing Cryptographic API
[4294670.164000] PCI: Disabling Via external APIC routing
[4294670.164000] isapnp: Scanning for PnP cards...
[4294670.518000] isapnp: No Plug & Play device found
[4294670.560000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[4294670.561000] serio: i8042 AUX port at 0x60,0x64 irq 12
[4294670.561000] serio: i8042 KBD port at 0x60,0x64 irq 1
[4294670.561000] Serial: 8250/16550 driver $Revision: 1.90 $ 54 ports, IRQ sharing enabled
[4294670.561000] ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294670.561000] ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[4294670.567000] ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294670.567000] ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[4294670.567000] io scheduler noop registered
[4294670.567000] io scheduler anticipatory registered
[4294670.568000] io scheduler deadline registered
[4294670.568000] io scheduler cfq registered
[4294670.569000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[4294670.569000] EISA: Probing bus 0 at eisa.0
[4294670.569000] Cannot allocate resource for EISA slot 4
[4294670.569000] Cannot allocate resource for EISA slot 5
[4294670.569000] Cannot allocate resource for EISA slot 6
[4294670.569000] EISA: Detected 0 cards.
[4294670.569000] NET: Registered protocol family 2
[4294670.579000] IP: routing cache hash table of 4096 buckets, 32Kbytes
[4294670.580000] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[4294670.581000] TCP bind hash table entries: 16384 (order: 4, 65536 bytes)
[4294670.582000] TCP: Hash tables configured (established 16384 bind 16384)
[4294670.583000] NET: Registered protocol family 8
[4294670.583000] NET: Registered protocol family 20
[4294670.583000] ACPI wakeup devices:
[4294670.583000] PCI0
[4294670.583000] ACPI: (supports S0 S1 S4bios S5)
[4294670.585000] Freeing unused kernel memory: 224k freed
[4294670.623000] input: AT Translated Set 2 keyboard on isa0060/serio0
[4294670.653000] vga16fb: initializing
[4294670.653000] vga16fb: mapped to 0xc00a0000
[4294670.724000] Console: switching to colour frame buffer device 80x30
[4294670.724000] fb0: VGA16 VGA frame buffer device
[4294671.925000] Capability LSM initialized
[4294671.968000] NET: Registered protocol family 1
[4294672.009000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[4294672.009000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[4294672.009000] ACPI: bus type ide registered
[4294672.067000] SCSI subsystem initialized
[4294672.084000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 5
[4294672.084000] PCI: setting IRQ 5 as level-triggered
[4294672.084000] ACPI: PCI Interrupt 0000:00:0c.0[A] -> Link [LNKC] -> GSI 5 (level, low) -> IRQ 5
[4294672.085000] ahc_pci:0:12:0: Host Adapter Bios disabled.  Using default SCSI device parameters
[4294672.091000] scsi0 : Adaptec AIC7XXX EISA/VLB/PCI SCSI HBA DRIVER, Rev 6.2.36
[4294672.091000]         <Adaptec aic7850 SCSI adapter>
[4294672.091000]         aic7850: Single Channel A, SCSI Id=7, 3/253 SCBs
[4294672.091000]
[4294687.622000]   Vendor: EPSON     Model: Perfection636     Rev: 1.09
[4294687.622000]   Type:   Processor                          ANSI SCSI revision: 02
[4294687.622000]  target0:0:2: Beginning Domain Validation
[4294687.627000]  target0:0:2: Ending Domain Validation
[4294688.691000] VP_IDE: IDE controller at PCI slot 0000:00:07.1
[4294688.691000] PCI: Via IRQ fixup for 0000:00:07.1, from 255 to 0
[4294688.691000] VP_IDE: chipset revision 6
[4294688.691000] VP_IDE: not 100% native mode: will probe irqs later
[4294688.691000] VP_IDE: VIA vt82c686a (rev 1b) IDE UDMA66 controller on pci0000:00:07.1
[4294688.691000]     ide0: BM-DMA at 0x9000-0x9007, BIOS settings: hda:DMA, hdb:pio
[4294688.691000]     ide1: BM-DMA at 0x9008-0x900f, BIOS settings: hdc:DMA, hdd:DMA
[4294688.691000] Probing IDE interface ide0...
[4294689.075000] hda: ST320423A, ATA DISK drive
[4294689.687000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[4294689.687000] Probing IDE interface ide1...
[4294690.479000] hdc: ATAPI CD ROM DRIVE 50X MAX, ATAPI CD/DVD-ROM drive
[4294691.193000] hdd: CD-RW IDE5224, ATAPI CD/DVD-ROM drive
[4294691.244000] ide1 at 0x170-0x177,0x376 on irq 15
[4294691.244000] Probing IDE interface ide2...
[4294691.757000] Probing IDE interface ide3...
[4294692.270000] Probing IDE interface ide4...
[4294692.783000] Probing IDE interface ide5...
[4294693.310000] hda: max request size: 128KiB
[4294693.311000] hda: 40011300 sectors (20485 MB) w/512KiB Cache, CHS=39693/16/63, UDMA(66)
[4294693.311000] hda: cache flushes not supported
[4294693.311000]  /dev/ide/host0/bus0/target0/lun0: p1 p2 p3
[4294693.367000] hdc: ATAPI 50X CD-ROM drive, 128kB Cache
[4294693.367000] Uniform CD-ROM driver Revision: 3.20
[4294693.371000] hdd: ATAPI 52X CD-ROM CD-R/RW drive, 2048kB Cache
[4294694.879000] Attempting manual resume
[4294694.880000] swsusp: Suspend partition has wrong signature?
[4294695.001000] usbcore: registered new driver usbfs
[4294695.002000] usbcore: registered new driver hub
[4294695.006000] USB Universal Host Controller Interface driver v2.2
[4294695.008000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 10
[4294695.008000] PCI: setting IRQ 10 as level-triggered
[4294695.008000] ACPI: PCI Interrupt 0000:00:07.2[D] -> Link [LNKD] -> GSI 10 (level, low) -> IRQ 10
[4294695.008000] uhci_hcd 0000:00:07.2: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
[4294695.070000] uhci_hcd 0000:00:07.2: new USB bus registered, assigned bus number 1
[4294695.070000] uhci_hcd 0000:00:07.2: irq 10, io base 0x00009400
[4294695.071000] hub 1-0:1.0: USB hub found
[4294695.071000] hub 1-0:1.0: 2 ports detected
[4294695.193000] e100: Intel(R) PRO/100 Network Driver, 3.4.8-k2-NAPI
[4294695.193000] e100: Copyright(c) 1999-2005 Intel Corporation
[4294695.194000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 5
[4294695.194000] ACPI: PCI Interrupt 0000:00:09.0[A] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
[4294695.217000] e100: eth0: e100_probe: addr 0xda101000, irq 5, MAC addr 00:90:27:24:96:BF
[4294695.265000] ohci_hcd: 2004 Nov 08 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[4294695.265000] ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [LNKD] -> GSI 10 (level, low) -> IRQ 10
[4294695.265000] ohci_hcd 0000:00:0b.0: OPTi Inc. 82C861
[4294695.265000] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 2
[4294695.266000] ohci_hcd 0000:00:0b.0: irq 10, io mem 0xda103000
[4294695.319000] hub 2-0:1.0: USB hub found
[4294695.319000] hub 2-0:1.0: 2 ports detected
[4294698.909000] ACPI: CPU0 (power states: C1[C1] C2[C2])
[4294698.909000] ACPI: Processor [CPU0] (supports 2 throttling states)
[4294699.121000] Attempting manual resume
[4294699.132000] swsusp: Suspend partition has wrong signature?
[4294699.176000] kjournald starting.  Commit interval 5 seconds
[4294699.177000] EXT3-fs: mounted filesystem with ordered data mode.
[4294701.974000] md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294710.923000] Adding 255520k swap on /dev/hda2.  Priority:-1 extents:1
[4294711.235000] EXT3 FS on hda3, internal journal
[4294722.314000] parport_pc: VIA 686A/8231 detected
[4294722.314000] parport_pc: probing current configuration
[4294722.314000] parport_pc: Current parallel port base: 0x378
[4294722.314000] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,ECP]
[4294722.341000] parport0: Printer, HEWLETT-PACKARD DESKJET 880C
[4294722.341000] parport_pc: VIA parallel port: io=0x378, irq=7
[4294722.368000] lp0: using parport0 (interrupt-driven).
[4294722.478000] mice: PS/2 mouse device common for all mice
[4294722.841000] ltmodem: module license 'Proprietary' taints kernel.
[4294722.854000] Loading Lucent Modem Controller driver version 8.26-alk
[4294722.909000] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[4294722.909000] PCI: setting IRQ 11 as level-triggered
[4294722.909000] ACPI: PCI Interrupt 0000:00:08.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[4294722.909000] Detected Parameters Irq=11 BaseAddress=0xb000 ComAddress=0xac00[4294722.909000] ttyLTM0 at I/O 0xb000 (irq = 11) is a Lucent/Agere Modem
[4294723.125000] input: ImPS/2 Generic Wheel Mouse on isa0060/serio1
[4294724.215000] ts: Compaq touchscreen protocol output
[4294727.290000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[4294728.565000] cdrom: open failed.
[4294729.686000] kjournald starting.  Commit interval 5 seconds
[4294729.686000] EXT3 FS on hda1, internal journal
[4294729.686000] EXT3-fs: mounted filesystem with ordered data mode.
[4294731.526000] Linux agpgart interface v0.101 (c) Dave Jones
[4294731.571000] agpgart: Detected VIA Apollo Pro 133 chipset
[4294731.604000] agpgart: AGP aperture is 64M @ 0xd0000000
[4294731.994000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[4294732.021000] shpchp: acpi_shpchprm:\_SB_.PCI0 evaluate _BBN fail=0x5
[4294732.021000] shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x5
[4294734.362000] ACPI: PCI Interrupt 0000:00:07.5[C] -> Link [LNKC] -> GSI 5 (level, low) -> IRQ 5
[4294734.362000] PCI: Setting latency timer of device 0000:00:07.5 to 64
[4294736.591000] ACPI: PCI Interrupt 0000:00:07.6[C] -> Link [LNKC] -> GSI 5 (level, low) -> IRQ 5
[4294737.342000] PCI: Setting latency timer of device 0000:00:07.6 to 64
[4294737.342000] ACPI: PCI interrupt for device 0000:00:07.6 disabled
[4294737.342000] VIA 82xx Modem: probe of 0000:00:07.6 failed with error -13
[4294738.236000] orinoco 0.14alpha2 (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski@gnu.org>, et al)
[4294738.259000] orinoco_plx 0.14alpha2 (Pavel Roskin <proski@gnu.org>, David Gibson <hermes@gibson.dropbear.id.au>, Daniel Barlow <dan@telent.net>)
[4294738.269000] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [LNKC] -> GSI 5 (level, low) -> IRQ 5
[4294738.269000] orinoco_plx: Detected Orinoco/Prism2 PLX device at 0000:00:0a.0 irq:5, io addr:0xbc00
[4294738.271000] orinoco_plx: CIS: 00:02:04:06:08:0A:08:0E:10:12:14:16:18:1A:1C:1E:
[4294738.271000] orinoco_plx: The CIS value of Prism2 PC card is unexpected
[4294738.271000] ACPI: PCI interrupt for device 0000:00:0a.0 disabled
[4294738.271000] orinoco_plx: probe of 0000:00:0a.0 failed with error -5
[4294738.474000] hostap_crypt: registered algorithm 'NULL'
[4294738.502000] hostap_plx: 0.4.1 - 2005-05-22 (Jouni Malinen <jkmaline@cc.hut.fi>)
[4294738.522000] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [LNKC] -> GSI 5 (level, low) -> IRQ 5
[4294738.522000] PLX9052 PCI/PCMCIA adapter: mem=0xda102000, plx_io=0xb800, irq=5, pccard_io=0xbc00
[4294738.522000] hostap_plx: CIS: 00 02 04 06 08 0a ...
[4294738.522000] hostap_plx: manfid=0x2220, 0x2a28
[4294738.522000] hostap_plx: invalid CIS data
[4294738.522000] Unknown PC Card CIS - not a Prism2/2.5 card?
[4294738.522000] ACPI: PCI interrupt for device 0000:00:0a.0 disabled
[4294740.735000] Real Time Clock Driver v1.12
[4294740.985000] input: PC Speaker
[4294741.523000] Floppy drive(s): fd0 is 1.44M
[4294741.537000] FDC 0 is a post-1991 82077
[4294744.368000] NET: Registered protocol family 17
[4294814.116000] ACPI: Power Button (FF) [PWRF]
[4294814.117000] ACPI: Power Button (CM) [PWRB]
[4294814.624000] ibm_acpi: ec object not found
[4294823.889000] lp0: ECP mode
[4294824.777000] lp0: ECP mode
[4294824.940000] lp0: ECP mode
[4294826.354000] [drm] Initialized drm 1.0.0 20040925
[4294826.382000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[4294826.403000] [drm] Initialized mga 3.1.0 20021029 on minor 0: Matrox Graphics, Inc. MGA G200 AGP
[4294826.408000] agpgart: Found an AGP 1.0 compliant device at 0000:00:00.0.
[4294826.408000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 1x mode
[4294826.408000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 1x mode
[4294835.112000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[4294835.112000] apm: overridden by ACPI.
[4294836.867000] Bluetooth: Core ver 2.7
[4294836.867000] NET: Registered protocol family 31
[4294836.867000] Bluetooth: HCI device and connection manager initialized
[4294836.867000] Bluetooth: HCI socket layer initialized
[4294836.960000] Bluetooth: L2CAP ver 2.7
[4294836.960000] Bluetooth: L2CAP socket layer initialized
[4294837.046000] Bluetooth: RFCOMM ver 1.5
[4294837.046000] Bluetooth: RFCOMM socket layer initialized
[4294837.046000] Bluetooth: RFCOMM TTY layer initialized
[4295498.296000] NET: Registered protocol family 10
[4295498.296000] Disabled Privacy Extensions on device c02eb280(lo)
[4295498.297000] IPv6 over IPv4 tunneling driver
[4295508.691000] eth0: no IPv6 routers present
[4295519.638000] ISO 9660 Extensions: Microsoft Joliet Level 3
[4295522.048000] ISOFS: changing to secondary root
[4295551.576000] CSLIP: code copyright 1989 Regents of the University of California
[4295551.593000] PPP generic driver version 2.4.2
[4295588.978000] PPP BSD Compression module registered
[4295589.094000] PPP Deflate Compression module registered
guest@freekbox:~$

---

### Post by zxee on 2006-08-18
Well your scsi card and scanner are being seen at boot up.
You may need to get and load the driver. It's been a while since I set up a scsi scanner, But the sane docs are here: [http://www.sane-project.org/docs.html](http://www.sane-project.org/docs.html) 
I would first try the sane-find-scanner command with sudo 
Just put sudo in front of the command and it will then run as root.
If you get the same results then you definately need to download the backend for your scanner and install it per the docs page.
If running the command with sudo finds the scanner then all you'll need to do is change permissions on the device.
Oh and it might help to have the output from lsmod.

---

### Post by wantolrn on 2006-08-18
Howdy...here's want I've found so far for the finding of the Epson 636 scanner drive :
1.Need to download the backend; funny, this cable starts from the scanner as a SCSI & plugs into the computer via a parallel port connection—kind of like a diff in front & back ends
2.Starting w/ command line of $ sudo /usr/local/etc/sane.d/epson.conf    
 No such file or directory
3.Then tied: $ lsmod  --:confused: produced a long list which I scanned, no pun or yes a pun, via eyeballs for something related and found:
 scsi_transport_spi     17920  1 aic7xxx
 scsi_mod              124872  2 aic7xxx,scsi_transport_spi
Have read [http://www.sane-project.org/docs.html](http://www.sane-project.org/docs.html) and don't know what to do with info to download backend or what the actual backend for the Epson 636 scanner is.

---

### Post by wantolrn on 2006-08-18
Hi...to clarify my previous thread this is what I tried to do from reading:                                    sane-epson.5

guest@freekbox:~$  /usr/local/lib/sane/libsane-epson.a
bash: /usr/local/lib/sane/libsane-epson.a: No such file or directory
guest@freekbox:~$ /usr/local/lib/sane/libsane-epson.so
bash: /usr/local/lib/sane/libsane-epson.so: No such file or directory
guest@freekbox:~$ file /usr/local/etc/sane.d/epson.conf
/usr/local/etc/sane.d/epson.conf: ERROR: cannot open `/usr/local/etc/sane.d/epson.conf' (No such file or directory)
guest@freekbox:~$ file /usr/local/etc/sane.d/epson.conf scsi EPSON
/usr/local/etc/sane.d/epson.conf:
ERROR: cannot open `/usr/local/etc/sane.d/epson.conf'(No such file or directory)
scsi: ERROR: cannot open `scsi' (No such file or directory)
EPSON:     ERROR: cannot open `EPSON' (No such file or directory)
guest@freekbox:~$  SANE_EPSON_CMD_LVL
bash: SANE_EPSON_CMD_LVL: command not found
guest@freekbox:~$ SANE_DEBUG_EPSON
bash: SANE_DEBUG_EPSON: command not found

Hence, although the Epson 636 scanner has a SCSI & recognized by SANE; still can find way to communicate to operating system or find driver.
Thanks for previous help.:confused:

---

### Post by WormRunner on 2006-08-24
I helped solve this problem

First, the scsi card that was being used was not recognized, so we put in a different card which ubuntu found without difficulty.  We also had to replace the cable since it was a newer card.

Next we added sg to /etc/modules so that it would be loaded automatically.  Then we installed scsiadd (apt-get install scsiadd).

The following two commands we put into a script which needs to be run after the scanner is connected and turned on.  (I am sure a more elegant solution is out there)
  sudo scsiadd -i 2   (the scanner was set to device 2)
  sudo chown scanner /dev/sg0 (to put the device into the scanner group)

The scanner works now with xsane.

---

### Post by TWFJR on 2007-06-12
This did not work for me.  I am using 7.04.  I have an Epson Perfection 636 SCSI scanner.  Xsane Image Scanner is not, nor is GIMP recognizing this scanner.  I believe the problem is with the SCSI card.  I followed the below instructions:  Adding sg to /etc/modules. Then installing scsiadd. The commands, sudo scsiadd -i 2 and sudo chown scanner /dev/sg0 were commands not found.

What command will establish setting the device and place the device in the scanner group?

This command did not work:  ls -R /lib/modules/X.XX/kernel/drivers (to identify kernel support for scsi.)


I helped solve this problem

First, the scsi card that was being used was not recognized, so we put in a different card which ubuntu found without difficulty. We also had to replace the cable since it was a newer card.

Next we added sg to /etc/modules so that it would be loaded automatically. Then we installed scsiadd (apt-get install scsiadd).

The following two commands we put into a script which needs to be run after the scanner is connected and turned on. (I am sure a more elegant solution is out there)
sudo scsiadd -i 2 (the scanner was set to device 2)
sudo chown scanner /dev/sg0 (to put the device into the scanner group)

The scanner works now with xsane.
__________________

---

### Post by TWFJR on 2007-06-12
It has become evident that my scsi card is not supported.  What advise has anyone for a supported scsi card? I read that support is better with a more expensive card.  I see that modules need to be added for the scsi card and modules for generic scsi too.  I almost feel as if this is all workable only the commands that are given are not accepted.  So, need assistance here doing it right the first time. My scsi card is an Adaptec AHA-7850.

---

