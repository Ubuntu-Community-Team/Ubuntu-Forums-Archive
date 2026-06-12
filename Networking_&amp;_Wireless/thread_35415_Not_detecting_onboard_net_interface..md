---
title: "Not detecting onboard net interface."
date: 2005-05-18
forum: Networking &amp; Wireless
---

### Post by persis on 2005-05-18
Just installed Ubuntu on a friends P3. The network is onboard and has no separate nic card. During the install it failed to detect network interface. Now that it is "fully" installed - I'd like to go about getting it to detect the built-in network interface.

What's the best way to do this?

Thanks for everything crew -

---

### Post by defkewl on 2005-05-18
What is the motherboard name? I have a gigabyte motherboard and on-board lan card and it is detected as via.

Type dmesg on the console
Could you please paste the message here?

---

### Post by persis on 2005-05-19
Since I couldn't get the onboard ethernet going, I installed a nic I had lieing around.  WIth the added nic it works fine, but I'd much rather save this nic for another day and utilize the mobo ethernet.

Btw, the computer is a:

Intellistation E Pro 68939RU

Thanks for the help in advance!

dmeg gives:


Linux version 2.6.10-5-386 (buildd@terranova) (gcc version 3.3.5 (Debian
1:3.3.5-8ubuntu2)) #1 Tue Apr 5 12:12:40 UTC 2005
BIOS-provided physical RAM map:
 BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
 BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
 BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
 BIOS-e820: 0000000000100000 - 000000000fffff00 (usable)
 BIOS-e820: 000000000fffff00 - 0000000010000000 (reserved)
 BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
 BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
 BIOS-e820: 00000000fffc0000 - 0000000100000000 (reserved)
255MB LOWMEM available.
On node 0 totalpages: 65535
  DMA zone: 4096 pages, LIFO batch:1
  Normal zone: 61439 pages, LIFO batch:14
  HighMem zone: 0 pages, LIFO batch:1
DMI 2.1 present.
ACPI: Unable to locate RSDP
Built 1 zonelists
Kernel command line: root=/dev/hda1 ro quiet splash
Local APIC disabled by BIOS -- you can enable it with "lapic"
mapped APIC to ffffd000 (01204000)
Initializing CPU#0
PID hash table entries: 1024 (order: 10, 16384 bytes)
Detected 597.544 MHz processor.
Using tsc for high-res timesource
Console: colour VGA+ 80x25
Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
Memory: 252188k/262140k available (1436k kernel code, 9356k reserved, 754k
data, 224k init, 0k highmem)
Checking if this processor honours the WP bit even in supervisor mode... Ok.
Calibrating delay loop... 1179.64 BogoMIPS (lpj=589824)
Security Framework v1.0.0 initialized
SELinux:  Disabled at boot.
Mount-cache hash table entries: 512 (order: 0, 4096 bytes)
CPU: After generic identify, caps: 0383f9ff 00000000 00000000 00000000
00000000 00000000
CPU: After vendor identify, caps: 0383f9ff 00000000 00000000 00000000
00000000 00000000
CPU: L1 I cache: 16K, L1 D cache: 16K
CPU: L2 cache: 512K
CPU: After all inits, caps: 0383f9ff 00000000 00000000 00000040 00000000
00000000
CPU: Intel Pentium III (Katmai) stepping 03
Enabling fast FPU save and restore... done.
Enabling unmasked SIMD FPU exception support... done.
Checking 'hlt' instruction... OK.
Checking for popad bug... OK.
checking if image is initramfs...it isn't (bad gzip magic numbers); looks
like an initrd
Freeing initrd memory: 4248k freed
NET: Registered protocol family 16
EISA bus registered
PCI: PCI BIOS revision 2.10 entry at 0xfd83c, last bus=1
PCI: Using configuration type 1
mtrr: v2.0 (20020519)
ACPI: Subsystem revision 20050211
ACPI: Interpreter disabled.
Linux Plug and Play Support v0.97 (c) Adam Belay
pnp: PnP ACPI: disabled
PnPBIOS: Scanning system for PnP BIOS support...
PnPBIOS: Found PnP BIOS installation structure at 0xc00fde50
PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0x5885, dseg 0xf0000
PnPBIOS: 21 nodes reported by PnP BIOS; 21 recorded by driver
PCI: Probing PCI hardware
PCI: Probing PCI hardware (bus 00)
PCI: Using IRQ router PIIX/ICH [8086/7110] at 0000:00:02.0
PCI: IRQ 0 for device 0000:00:02.2 doesn't match PIRQ mask - try
pci=usepirqmask
pnp: 00:0e: ioport range 0x370-0x371 has been reserved
pnp: 00:0e: ioport range 0x4d0-0x4d1 has been reserved
pnp: 00:0f: ioport range 0x290-0x297 has been reserved
pnp: 00:10: ioport range 0xfd00-0xfd3f has been reserved
pnp: 00:10: ioport range 0xfe00-0xfe0f has been reserved
audit: initializing netlink socket (disabled)
audit(1116508807.616:0): initialized
VFS: Disk quotas dquot_6.5.1
Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
devfs: boot_options: 0x0
Initializing Cryptographic API
Limiting direct PCI/PCI transfers.
isapnp: Scanning for PnP cards...
isapnp: Card 'Crystal Audio'
isapnp: 1 Plug & Play card detected total
serio: i8042 AUX port at 0x60,0x64 irq 12
serio: i8042 KBD port at 0x60,0x64 irq 1
Serial: 8250/16550 driver $Revision: 1.90 $ 54 ports, IRQ sharing enabled
ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
io scheduler noop registered
io scheduler anticipatory registered
io scheduler deadline registered
io scheduler cfq registered
RAMDISK driver initialized: 16 RAM disks of 8192K size 1024 blocksize
input: AT Translated Set 2 keyboard on isa0060/serio0
EISA: Probing bus 0 at eisa0
Cannot allocate resource for EISA slot 1
Cannot allocate resource for EISA slot 6
Cannot allocate resource for EISA slot 7
Cannot allocate resource for EISA slot 8
EISA: Detected 0 cards.
NET: Registered protocol family 2
IP: routing cache hash table of 2048 buckets, 16Kbytes
TCP: Hash tables configured (established 16384 bind 32768)
NET: Registered protocol family 8
NET: Registered protocol family 20
Restarting tasks...<6> Strange, kswapd0 not stopped
 Strange, kpnpbiosd not stopped
 Strange, kseriod not stopped
 done
RAMDISK: cramfs filesystem found at block 0
RAMDISK: Loading 4248KiB [1 disk] into ram disk... done.
VFS: Mounted root (cramfs filesystem) readonly.
Freeing unused kernel memory: 224k freed
NET: Registered protocol family 1
Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
PIIX4: IDE controller at PCI slot 0000:00:02.1
PIIX4: chipset revision 1
PIIX4: not 100% native mode: will probe irqs later
    ide0: BM-DMA at 0xfff0-0xfff7, BIOS settings: hda:DMA, hdb:pio
    ide1: BM-DMA at 0xfff8-0xffff, BIOS settings: hdc:DMA, hdd:pio
Probing IDE interface ide0...
hda: FUJITSU MPE3136AH B4, ATA DISK drive
elevator: using anticipatory as default io scheduler
ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
hda: max request size: 128KiB
hda: 26520480 sectors (13578 MB) w/2048KiB Cache, CHS=26310/16/63, UDMA(33)
hda: cache flushes not supported
 /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 >
Probing IDE interface ide1...
hdc: CRD-8400B, ATAPI CD/DVD-ROM drive
ide1 at 0x170-0x177,0x376 on irq 15
Probing IDE interface ide2...
Probing IDE interface ide3...
Probing IDE interface ide4...
Probing IDE interface ide5...
Stopping tasks: ==|
Freeing memory... done (458 pages freed)
Restarting tasks... done
EXT3-fs: mounted filesystem with ordered data mode.
kjournald starting.  Commit interval 5 seconds
Adding 570268k swap on /dev/hda5.  Priority:-1 extents:1
EXT3 FS on hda1, internal journal
hdc: ATAPI 40X CD-ROM drive, 128kB Cache
Uniform CD-ROM driver Revision: 3.20
parport: PnPBIOS parport detected.
parport0: PC-style at 0x278, irq 7 [PCSPP,EPP]
lp0: using parport0 (interrupt-driven).
mice: PS/2 mouse device common for all mice
input: PS/2 Generic Mouse on isa0060/serio1
ts: Compaq touchscreen protocol output
Capability LSM initialized
device-mapper: 4.3.0-ioctl (2004-09-30) initialised: [email]dm-devel@redhat.com[/email]
md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
cdrom: open failed.
Real Time Clock Driver v1.12
input: PC Speaker
inserting floppy driver for 2.6.10-5-386
Floppy drive(s): fd0 is 1.44M
FDC 0 is a post-1991 82077
Linux agpgart interface v0.100 (c) Dave Jones
agpgart: Detected an Intel 440BX Chipset.
agpgart: Maximum main memory to use for agp memory: 203M
agpgart: AGP aperture is 64M @ 0xf0000000
cpci_hotplug: CompactPCI Hot Plug Core version: 0.2
pci_hotplug: PCI Hot Plug PCI Core version: 0.5
shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x1001
pciehp: acpi_pciehprm:get_device PCI ROOT HID fail=0x1001
usbcore: registered new driver usbfs
usbcore: registered new driver hub
USB Universal Host Controller Interface driver v2.2
PCI: Enabling device 0000:00:02.2 (0000 -> 0001)
PCI: IRQ 0 for device 0000:00:02.2 doesn't match PIRQ mask - try
pci=usepirqmask
PCI: setting IRQ 10 as level-triggered
PCI: Assigned IRQ 10 for device 0000:00:02.2
uhci_hcd 0000:00:02.2: Intel Corp. 82371AB/EB/MB PIIX4 USB
uhci_hcd 0000:00:02.2: irq 10, io base 0x1000
uhci_hcd 0000:00:02.2: new USB bus registered, assigned bus number 1
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 2 ports detected
piix4_smbus 0000:00:02.3: Found 0000:00:02.3 device
piix4_smbus 0000:00:02.3: IBM Laptop detected; this module may corrupt
your serial eeprom! Refusing to load module!
piix4_smbus: probe of 0000:00:02.3 failed with error -1
Linux Tulip driver version 1.1.13 (May 11, 2002)
PCI: Found IRQ 11 for device 0000:00:14.0
tulip0:  EEPROM default media type Autosense.
tulip0:  Index #0 - Media MII (#11) described by a 21142 MII PHY (3) block.
tulip0:  MII transceiver #1 config 1000 status 782d advertising 01e1.
eth0: Digital DS21143 Tulip rev 65 at 00016880, 00:00:24:C8:B9:E6, IRQ 11.
NET: Registered protocol family 17
0000:00:14.0: tulip_stop_rxtx() failed
eth0: Setting full-duplex based on MII#1 link partner capability of 45e1.
NET: Registered protocol family 10
Disabled Privacy Extensions on device c02f0500(lo)
IPv6 over IPv4 tunneling driver
IBM machine detected. Enabling interrupts during APM calls.
apm: BIOS not found.
eth0: no IPv6 routers present

---

