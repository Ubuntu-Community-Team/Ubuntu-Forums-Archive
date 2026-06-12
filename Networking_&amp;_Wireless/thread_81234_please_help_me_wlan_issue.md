---
title: "please help me wlan issue"
date: 2005-10-24
forum: Networking &amp; Wireless
---

### Post by steelisreal on 2005-10-24
I have a dell 600m laptop with a dell 1370 wireless card.

I installed 5.10 loaded ndiswrapper following the instructions provided by the how to, and everything worked fine for a day.

After 1 day the card was still recognized but no connection.  I followed many ideas on the forums as what could be wrong but nothing worked ( ifup ifdown and so forth)

Since I had little invested in this I did a complete reinstall of 5.10 and ndiswrapper and everything worked great for 4 days then the same thing happened again, no net connection nothing will solve the issue.

As a last ditch i reinstalled 5.10 again and ndiswrapper, this time everything show up fine, the card is there, as are the drivers but no connection.

I am not sure what the issue is.

My thought is at this step:

for conffile in /etc/ndiswrapper/bcmwl5/*.conf; do
sudo cat $conffile | sed -e 's/RadioState|1/RadioState|0/' > $conffile
done

I must be doing something wrong, it says bash ambigous redirect, when i do it correctly right after a reinstall it works fine. but if i do it wrong once, redoing it has no effect.

how important is this step? and what exactly do you type in newbie language.  
do you put done at the end? or is that just saying you are done with the install?  where it says for conffile in /etc/ndiswrapper/bcmwl5/*.conf;  do i type anything.

I am at my wits end please help me.

---

### Post by steelisreal on 2005-10-24
2: ioport range 0x810-0x85f could not be reserved
[4294668.476000] pnp: 00:02: ioport range 0x860-0x87f has been reserved
[4294668.476000] pnp: 00:02: ioport range 0x880-0x8bf has been reserved
[4294668.476000] pnp: 00:02: ioport range 0x8c0-0x8df has been reserved
[4294668.476000] pnp: 00:07: ioport range 0x900-0x97f has been reserved
[4294668.477000] audit: initializing netlink socket (disabled)
[4294668.477000] audit: initialized
[4294668.477000] VFS: Disk quotas dquot_6.5.1
[4294668.477000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[4294668.477000] devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
[4294668.477000] devfs: boot_options: 0x0
[4294668.477000] Initializing Cryptographic API
[4294668.477000] isapnp: Scanning for PnP cards...
[4294668.831000] isapnp: No Plug & Play device found
[4294668.848000] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[4294668.852000] serio: i8042 AUX port at 0x60,0x64 irq 12
[4294668.852000] serio: i8042 KBD port at 0x60,0x64 irq 1
[4294668.852000] Serial: 8250/16550 driver $Revision: 1.90 $ 54 ports, IRQ sharing enabled
[4294668.852000] ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294668.854000] ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294668.855000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 5
[4294668.855000] PCI: setting IRQ 5 as level-triggered
[4294668.855000] ACPI: PCI Interrupt 0000:00:1f.6[B] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
[4294668.855000] ACPI: PCI interrupt for device 0000:00:1f.6 disabled
[4294668.855000] io scheduler noop registered
[4294668.855000] io scheduler anticipatory registered
[4294668.855000] io scheduler deadline registered
[4294668.855000] io scheduler cfq registered
[4294668.855000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[4294668.856000] EISA: Probing bus 0 at eisa.0
[4294668.856000] EISA: Detected 0 cards.
[4294668.856000] NET: Registered protocol family 2
[4294668.865000] input: AT Translated Set 2 keyboard on isa0060/serio0
[4294668.866000] IP: routing cache hash table of 4096 buckets, 32Kbytes
[4294668.866000] TCP established hash table entries: 32768 (order: 6, 262144 bytes)
[4294668.866000] TCP bind hash table entries: 32768 (order: 5, 131072 bytes)
[4294668.866000] TCP: Hash tables configured (established 32768 bind 32768)
[4294668.866000] NET: Registered protocol family 8
[4294668.866000] NET: Registered protocol family 20
[4294668.866000] ACPI wakeup devices:
[4294668.866000]  LID PBTN PCI0 USB0 USB1 USB2 USB3 MODM PCIE
[4294668.866000] ACPI: (supports S0 S1 S3 S4 S4bios S5)
[4294668.867000] Freeing unused kernel memory: 224k freed
[4294668.879000] vga16fb: initializing
[4294668.879000] vga16fb: mapped to 0xc00a0000
[4294668.997000] Console: switching to colour frame buffer device 80x30
[4294668.997000] fb0: VGA16 VGA frame buffer device
[4294670.157000] Capability LSM initialized
[4294670.167000] NET: Registered protocol family 1
[4294670.181000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[4294670.181000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[4294670.181000] ACPI: bus type ide registered
[4294670.186000] ICH4: IDE controller at PCI slot 0000:00:1f.1
[4294670.186000] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
[4294670.186000] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[4294670.186000] PCI: setting IRQ 11 as level-triggered
[4294670.186000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[4294670.186000] ICH4: chipset revision 1
[4294670.186000] ICH4: not 100% native mode: will probe irqs later
[4294670.186000]     ide0: BM-DMA at 0xbfa0-0xbfa7, BIOS settings: hda:DMA, hdb:pio
[4294670.186000]     ide1: BM-DMA at 0xbfa8-0xbfaf, BIOS settings: hdc:DMA, hdd:pio
[4294670.186000] Probing IDE interface ide0...
[4294670.450000] hda: WDC WD400VE-75HDT0, ATA DISK drive
[4294671.062000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[4294671.062000] Probing IDE interface ide1...
[4294671.734000] hdc: PHILIPS CD-RW/DVD-ROM SCB5265, ATAPI CD/DVD-ROM drive
[4294672.346000] ide1 at 0x170-0x177,0x376 on irq 15
[4294672.346000] Probing IDE interface ide2...
[4294672.859000] Probing IDE interface ide3...
[4294673.371000] Probing IDE interface ide4...
[4294673.883000] Probing IDE interface ide5...
[4294674.398000] hda: max request size: 128KiB
[4294674.678000] hda: 78140160 sectors (40007 MB) w/8192KiB Cache, CHS=65535/16/63, UDMA(100)
[4294674.678000] hda: cache flushes supported
[4294674.678000]  /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 >
[4294674.732000] hdc: ATAPI 24X DVD-ROM CD-R/RW drive, 2048kB Cache
[4294674.732000] Uniform CD-ROM driver Revision: 3.20
[4294674.949000] Attempting manual resume
[4294674.949000] swsusp: Suspend partition has wrong signature?
[4294674.974000] usbcore: registered new driver usbfs
[4294674.974000] usbcore: registered new driver hub
[4294674.975000] USB Universal Host Controller Interface driver v2.2
[4294674.975000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[4294674.975000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[4294674.975000] uhci_hcd 0000:00:1d.0: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1
[4294675.037000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[4294675.037000] uhci_hcd 0000:00:1d.0: irq 11, io base 0x0000bf80
[4294675.037000] hub 1-0:1.0: USB hub found
[4294675.037000] hub 1-0:1.0: 2 ports detected
[4294675.040000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[4294675.040000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[4294675.040000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[4294675.040000] uhci_hcd 0000:00:1d.1: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2
[4294675.102000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[4294675.102000] uhci_hcd 0000:00:1d.1: irq 11, io base 0x0000bf40
[4294675.102000] hub 2-0:1.0: USB hub found
[4294675.102000] hub 2-0:1.0: 2 ports detected
[4294675.105000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[4294675.105000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[4294675.105000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[4294675.105000] uhci_hcd 0000:00:1d.2: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3
[4294675.167000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[4294675.167000] uhci_hcd 0000:00:1d.2: irq 11, io base 0x0000bf20
[4294675.167000] hub 3-0:1.0: USB hub found
[4294675.167000] hub 3-0:1.0: 2 ports detected
[4294675.194000] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 11
[4294675.194000] ACPI: PCI Interrupt 0000:00:1d.7[D] -> Link [LNKH] -> GSI 11 (level, low) -> IRQ 11
[4294675.194000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[4294675.194000] ehci_hcd 0000:00:1d.7: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller
[4294675.194000] ehci_hcd 0000:00:1d.7: debug port 1
[4294675.194000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
[4294675.194000] ehci_hcd 0000:00:1d.7: irq 11, io mem 0xf4fffc00
[4294675.198000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[4294675.198000] ehci_hcd 0000:00:1d.7: USB 2.0 initialized, EHCI 1.00, driver 10 Dec 2004
[4294675.198000] hub 4-0:1.0: USB hub found
[4294675.198000] hub 4-0:1.0: 6 ports detected
[4294675.274000] b44.c:v0.95 (Aug 3, 2004)
[4294675.274000] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[4294675.277000] eth0: Broadcom 4400 10/100BaseT Ethernet 00:12:3f:fa:30:96
[4294675.771000] usb 2-1: new low speed USB device using uhci_hcd and address 2
[4294677.325000] usbcore: registered new driver hiddev
[4294677.348000] input: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:1d.1-1
[4294677.348000] usbcore: registered new driver usbhid
[4294677.348000] drivers/usb/input/hid-core.c: v2.01:USB HID core driver
[4294677.712000] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3] C4[C3])
[4294677.712000] ACPI: Processor [CPU0] (supports 8 throttling states)
[4294677.718000] ACPI: Thermal Zone [THM] (31 C)
[4294678.203000] Attempting manual resume
[4294678.204000] swsusp: Suspend partition has wrong signature?
[4294678.211000] EXT3-fs: INFO: recovery required on readonly filesystem.
[4294678.211000] EXT3-fs: write access will be enabled during recovery.
[4294679.226000] kjournald starting.  Commit interval 5 seconds
[4294679.226000] EXT3-fs: hda1: orphan cleanup on readonly fs
[4294679.226000] ext3_orphan_cleanup: deleting unreferenced inode 4670345
[4294679.226000] ext3_orphan_cleanup: deleting unreferenced inode 4670344
[4294679.226000] EXT3-fs: hda1: 2 orphan inodes deleted
[4294679.227000] EXT3-fs: recovery complete.
[4294679.229000] EXT3-fs: mounted filesystem with ordered data mode.
[4294680.422000] md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294683.951000] Adding 1510068k swap on /dev/hda5.  Priority:-1 extents:1
[4294684.247000] EXT3 FS on hda1, internal journal
[4294690.798000] parport: PnPBIOS parport detected.
[4294690.798000] parport0: PC-style at 0x378 (0x778), irq 7, dma 1 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[4294690.882000] lp0: using parport0 (interrupt-driven).
[4294690.916000] mice: PS/2 mouse device common for all mice
[4294691.453000] alps.c: Enabling hardware tapping
[4294691.551000] input: PS/2 Mouse on isa0060/serio1
[4294691.553000] input: AlpsPS/2 ALPS GlidePoint on isa0060/serio1
[4294691.944000] ts: Compaq touchscreen protocol output
[4294695.025000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[4294695.876000] cdrom: open failed.
[4294698.336000] Linux agpgart interface v0.101 (c) Dave Jones
[4294698.344000] agpgart: Detected an Intel 855PM Chipset.
[4294698.365000] agpgart: AGP aperture is 128M @ 0xe0000000
[4294698.594000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[4294698.599000] shpchp: acpi_shpchprm:\_SB_.PCI0 evaluate _BBN fail=0x5
[4294698.599000] shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x5
[4294698.853000] shpchp: acpi_shpchprm:\_SB_.PCI0 evaluate _BBN fail=0x5
[4294698.853000] shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x5
[4294698.915000] hw_random: cannot enable RNG, aborting
[4294699.302000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
[4294699.302000] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[4294700.111000] intel8x0_measure_ac97_clock: measured 49462 usecs
[4294700.111000] intel8x0: clocking to 48000
[4294700.811000] Linux Kernel Card Services
[4294700.811000]   options:  [pci] [cardbus] [pm]
[4294700.823000] PCI: Enabling device 0000:02:01.0 (0000 -> 0002)
[4294700.823000] ACPI: PCI Interrupt 0000:02:01.0[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[4294700.823000] Yenta: CardBus bridge found at 0000:02:01.0 [1028:01be]
[4294700.823000] Yenta O2: res at 0x94/0xD4: 00/ea
[4294700.823000] Yenta O2: enabling read prefetch/write burst
[4294700.944000] Yenta: ISA IRQ mask 0x0418, PCI irq 11
[4294700.944000] Socket status: 30000006
[4294700.958000] PCI: Enabling device 0000:02:01.1 (0000 -> 0002)
[4294700.958000] ACPI: PCI Interrupt 0000:02:01.1[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[4294700.958000] Yenta: CardBus bridge found at 0000:02:01.1 [1028:01be]
[4294701.078000] Yenta: ISA IRQ mask 0x0418, PCI irq 11
[4294701.078000] Socket status: 30000006
[4294703.129000] Real Time Clock Driver v1.12
[4294703.217000] input: PC Speaker
[4294704.094000] ndiswrapper version 1.1 loaded (preempt=no,smp=no)
[4294704.184000] ndiswrapper: driver bcmwl5 (Broadcom,11/27/2004, 3.100.35.0) loaded
[4294704.184000] ACPI: PCI Interrupt 0000:02:03.0[A] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
[4294704.192000] ndiswrapper: using irq 5
[4294704.699000] wlan0: ndiswrapper ethernet device 00:14:a4:23:31:ae using driver bcmwl5, configuration file 14E4:4318.5.conf
[4294704.699000] wlan0: encryption modes supported: WEP, WPA with TKIP, WPA with AES/CCMP
[4294705.355000] NET: Registered protocol family 17
[4294769.181000] ACPI: AC Adapter [AC] (on-line)
[4294769.504000] ACPI: Battery Slot [BAT0] (battery present)
[4294769.504000] ACPI: Battery Slot [BAT1] (battery absent)
[4294769.524000] ACPI: Lid Switch [LID]
[4294769.524000] ACPI: Power Button (CM) [PBTN]
[4294769.524000] ACPI: Sleep Button (CM) [SBTN]
[4294769.634000] ibm_acpi: ec object not found
[4294769.755000] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[4294777.220000] [drm] Initialized drm 1.0.0 20040925
[4294777.225000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[4294777.229000] [drm] Initialized radeon 1.16.0 20050311 on minor 0: ATI Technologies Inc Radeon R250 Lf [FireGL 9000]
[4294777.230000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[4294777.230000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 1x mode
[4294777.230000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 1x mode
[4294777.399000] [drm] Loading R200 Microcode
[4294778.413000] apm: BIOS not found.
[4294779.742000] cs: IO port probe 0x100-0x4ff: clean.
[4294779.743000] cs: IO port probe 0x100-0x4ff: clean.
[4294779.745000] cs: IO port probe 0xc00-0xcf7: clean.
[4294779.745000] cs: IO port probe 0xc00-0xcf7: clean.
[4294779.746000] cs: IO port probe 0xa00-0xaff: clean.
[4294779.746000] cs: IO port probe 0xa00-0xaff: clean.
[4294780.622000] Bluetooth: Core ver 2.7
[4294780.622000] NET: Registered protocol family 31
[4294780.622000] Bluetooth: HCI device and connection manager initialized
[4294780.622000] Bluetooth: HCI socket layer initialized
[4294780.661000] Bluetooth: L2CAP ver 2.7
[4294780.661000] Bluetooth: L2CAP socket layer initialized
[4294781.344000] Bluetooth: RFCOMM ver 1.5
[4294781.344000] Bluetooth: RFCOMM socket layer initialized
[4294781.344000] Bluetooth: RFCOMM TTY layer initialized
[4294787.135000] usb 4-1: new high speed USB device using ehci_hcd and address 3[4294787.612000] SCSI subsystem initialized
[4294787.618000] Initializing USB Mass Storage driver...
[4294787.622000] scsi0 : SCSI emulation for USB Mass Storage devices
[4294787.623000] usb-storage: device found at 3
[4294787.623000] usb-storage: waiting for device to settle before scanning
[4294787.623000] usbcore: registered new driver usb-storage
[4294787.623000] USB Mass Storage support registered.
[4294792.623000]   Vendor: Memorex   Model: TD 2C             Rev: 1.00
[4294792.623000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[4294792.628000] usb-storage: device scan complete
[4294793.382000] SCSI device sda: 492544 512-byte hdwr sectors (252 MB)
[4294793.383000] sda: Write Protect is off
[4294793.383000] sda: Mode Sense: 23 00 00 00
[4294793.383000] sda: assuming drive cache: write through
[4294793.386000] SCSI device sda: 492544 512-byte hdwr sectors (252 MB)
[4294793.387000] sda: Write Protect is off
[4294793.387000] sda: Mode Sense: 23 00 00 00
[4294793.387000] sda: assuming drive cache: write through
[4294793.387000]  /dev/scsi/host0/bus0/target0/lun0: p1
[4294793.389000] Attached scsi removable disk sda at scsi0, channel 0, id 0, lun 0
[4294795.815000] NET: Registered protocol family 10
[4294795.815000] Disabled Privacy Extensions on device c02eb280(lo)
[4294795.815000] IPv6 over IPv4 tunneling driver
[4294804.482000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[4294806.392000] wlan0: no IPv6 routers present
steelisreal@ubuntu:~$

---

### Post by steelisreal on 2005-10-24
steelisreal@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate:54 Mb/s   Tx-Power:25 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Power Management:off
          Link Quality:100/100  Signal level:-10 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

---

### Post by steelisreal on 2005-10-24
steelisreal@ubuntu:~$ ifconfig
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:388 errors:0 dropped:0 overruns:0 frame:0
          TX packets:388 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:33539 (32.7 KiB)  TX bytes:33539 (32.7 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:14:A4:23:31:AE
          inet6 addr: fe80::214:a4ff:fe23:31ae/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Memory:faffc000-faffdfff

---

### Post by steelisreal on 2005-10-24
steelisreal@ubuntu:~$ sudo ifdown wlan0
There is already a pid file /var/run/dhclient.wlan0.pid with pid 6527
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/wlan0/00:14:a4:23:31:ae
Sending on   LPF/wlan0/00:14:a4:23:31:ae
Sending on   Socket/fallback
steelisreal@ubuntu:~$ sudo ifup wlan0
There is already a pid file /var/run/dhclient.wlan0.pid with pid 0
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/wlan0/00:14:a4:23:31:ae
Sending on   LPF/wlan0/00:14:a4:23:31:ae
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 1
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
steelisreal@ubuntu:~$ sudo dhclient
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/sit0/
Sending on   LPF/sit0/
Listening on LPF/wlan0/00:14:a4:23:31:ae
Sending on   LPF/wlan0/00:14:a4:23:31:ae
Listening on LPF/eth0/00:12:3f:fa:30:96
Sending on   LPF/eth0/00:12:3f:fa:30:96
Listening on LPF/lo/
Sending on   LPF/lo/
Sending on   Socket/fallback
DHCPDISCOVER on sit0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on lo to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on sit0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on lo to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on sit0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on lo to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on lo to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on sit0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on lo to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on sit0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on lo to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on sit0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on sit0 to 255.255.255.255 port 67 interval 2
DHCPDISCOVER on lo to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---

