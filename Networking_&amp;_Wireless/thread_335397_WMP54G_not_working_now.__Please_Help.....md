---
title: "WMP54G not working now.  Please Help...."
date: 2007-01-10
forum: Networking &amp; Wireless
---

### Post by knichel on 2007-01-10
I recently had to replace the wireless network adapter in my 6.06 box.  I had a linksys WMP54G version 4 card.  It installed out of the box just fine.  The new card is a version 4.1 card.  When I installed the card and started up, the computer hangs on Configuring Network Adapters.  I tried to boot from a 6.10 live CD and it does not boot either. IT gives me an error about logical blocks on hdb1 (not sure what hdb1 is, I only have one hd).

Is the version 4.1 card not supported in ubuntu yet?

I really need to get this card up and running.

TIA,
Mike

---

### Post by dmizer on 2007-01-11
with wireless hardware support, always start here: [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)
for the future, it's a good idea to consult that list prior to purchasing a new card.

i don't see the 4.1 card listed, but that doesn't mean you can't get the thing working.  first, try booting without the adapter connected.  then, once you're logged in, and everything is working okay, connect the adapter.  if it hangs again, we may need to figure out how to disable whatever driver is attempting to load for your card.

if it does not hang, post the output of 
```
dmesg | tail
```
and
```
lspci
```

---

### Post by knichel on 2007-01-11
Thanks for the reply.  I have already removed the card and it boots fine without it.  As soon as I intstall card, it hangs on boot.

--
Mike

---

### Post by dmizer on 2007-01-11
i see ... this card is not a pcmcia card.  this is a pci card.

will it boot to the live cd?  any live cd?  try knoppix if ubuntu live doesn't work.  we'll need the output from my previous post in order to do much fixing.

---

### Post by knichel on 2007-01-11
I did try the Ubuntu Live CD.  It did not work.  I will download and try Knoppix.

---

### Post by knichel on 2007-01-11
OK, here goes. I have downloaded KNOPPIX and booted from it with the pci card in the computer.  It boots and sees the card (I think).  Here is some output...

```
dmesg | tail:
**************** dmesg | tail ****************
knoppix@Knoppix:~$ dmesg | tail
Bluetooth: Core ver 2.11
NET: Registered protocol family 31
Bluetooth: HCI device and connection manager initialized
Bluetooth: HCI socket layer initialized
Bluetooth: L2CAP ver 2.8
Bluetooth: L2CAP socket layer initialized
Bluetooth: RFCOMM socket layer initialized
Bluetooth: RFCOMM TTY layer initialized
Bluetooth: RFCOMM ver 1.8
wlan0: no IPv6 routers present
**********************************************

```
```
lspci:
*****************  LSPCI *********************
00:00.0 Host bridge: VIA Technologies, Inc. K8T800Pro Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. K8T800Pro Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. K8T800Pro Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. K8T800Pro Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. K8T800Pro Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. K8T800Pro Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
00:08.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)
00:0a.0 Network controller: RaLink RT2561/RT61 802.11g PCI
00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)

**********************************************

```
```
ifconfig -a
******************* ifconfig -a **************
knoppix@Knoppix:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:13:D3:E7:EB:B5
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:20 Base address:0x4800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:99 errors:0 dropped:0 overruns:0 frame:0
          TX packets:99 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:7310 (7.1 KiB)  TX bytes:7310 (7.1 KiB)
*********  I tried to configure the wlan0 card to talk with my wifi router
wlan0     Link encap:Ethernet  HWaddr 00:12:17:91:61:90
          inet addr:192.168.6.13  Mask:255.255.255.0
          inet6 addr: fe80::212:17ff:fe91:6190/64 Scope:Link
          UP RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:37 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:3636 (3.5 KiB)
          Base address:0xc000

wlan1     Link encap:Ethernet  HWaddr 00:16:B6:9B:60:89
          MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Base address:0x8000

wmaster0  Link encap:UNSPEC  HWaddr 00-12-17-91-61-90-00-80-00-00-00-00-00-00-00-00
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Base address:0xc000

wmaster1  Link encap:UNSPEC  HWaddr 00-16-B6-9B-60-89-00-C0-00-00-00-00-00-00-00-00
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Base address:0x8000
**********************************************

```
```
 And just for kicks ... dmesg...
***************** dmesg **********************
knoppix@Knoppix:~$ dmesg
Linux version 2.6.19 (root@Knoppix) (gcc version 4.1.2 20061028 (prerelease) (Debian 4.1.1-19)) #7 SMP PREEMPT Sun Dec 17 22:01:07 CET 2006
BIOS-provided physical RAM map:
 BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
 BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
 BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
 BIOS-e820: 0000000000100000 - 000000003ffd0000 (usable)
 BIOS-e820: 000000003ffd0000 - 000000003ffde000 (ACPI data)
 BIOS-e820: 000000003ffde000 - 0000000040000000 (ACPI NVS)
 BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
 BIOS-e820: 00000000ff780000 - 0000000100000000 (reserved)
127MB HIGHMEM available.
896MB LOWMEM available.
found SMP MP-table at 000ff780
Entering add_active_range(0, 0, 262096) 0 entries of 256 used
Zone PFN ranges:
  DMA             0 ->     4096
  Normal       4096 ->   229376
  HighMem    229376 ->   262096
early_node_map[1] active PFN ranges
    0:        0 ->   262096
On node 0 totalpages: 262096
  DMA zone: 32 pages used for memmap
  DMA zone: 0 pages reserved
  DMA zone: 4064 pages, LIFO batch:0
  Normal zone: 1760 pages used for memmap
  Normal zone: 223520 pages, LIFO batch:31
  HighMem zone: 255 pages used for memmap
  HighMem zone: 32465 pages, LIFO batch:7
DMI 2.3 present.
ACPI: RSDP (v000 ACPIAM                                ) @ 0x000f9360
ACPI: RSDT (v001 A M I  OEMRSDT  0x11000524 MSFT 0x00000097) @ 0x3ffd0000
ACPI: FADT (v002 A M I  OEMFACP  0x11000524 MSFT 0x00000097) @ 0x3ffd0200
ACPI: MADT (v001 A M I  OEMAPIC  0x11000524 MSFT 0x00000097) @ 0x3ffd0390
ACPI: OEMB (v001 A M I  AMI_OEM  0x11000524 MSFT 0x00000097) @ 0x3ffde040
ACPI: DSDT (v001  1XXXX 1XXXX005 0x00000005 INTL 0x02002026) @ 0x00000000
ACPI: PM-Timer IO Port: 0x808
ACPI: Local APIC address 0xfee00000
ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Processor #0 15:12 APIC version 16
ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
IOAPIC[0]: apic_id 1, version 3, address 0xfec00000, GSI 0-23
ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
ACPI: IRQ0 used by override.
ACPI: IRQ2 used by override.
ACPI: IRQ9 used by override.
Enabling APIC mode:  Flat.  Using 1 I/O APICs
Using ACPI (MADT) for SMP configuration information
Allocating PCI resources starting at 50000000 (gap: 40000000:bec00000)
Detected 1800.159 MHz processor.
Built 1 zonelists.  Total pages: 260049
Kernel command line: ramdisk_size=100000 init=/etc/init lang=us apm=power-off vga=791 initrd=minirt.gz nomce loglevel=0 quiet BOOT_IMAGE=knoppix BOOT_IMAGE=linux
mapped APIC to ffffd000 (fee00000)
mapped IOAPIC to ffffc000 (fec00000)
Enabling fast FPU save and restore... done.
Enabling unmasked SIMD FPU exception support... done.
Initializing CPU#0
PID hash table entries: 4096 (order: 12, 16384 bytes)
Console: colour dummy device 80x25
Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Memory: 1033108k/1048384k available (2747k kernel code, 14604k reserved, 958k data, 336k init, 130880k highmem)
virtual kernel memory layout:
    fixmap  : 0xffe16000 - 0xfffff000   (1956 kB)
    pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
    vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
    lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
      .init : 0xc04a6000 - 0xc04fa000   ( 336 kB)
      .data : 0xc03aef9c - 0xc049e7b4   ( 958 kB)
      .text : 0xc0100000 - 0xc03aef9c   (2747 kB)
Checking if this processor honours the WP bit even in supervisor mode... Ok.
Calibrating delay using timer specific routine.. 3605.24 BogoMIPS (lpj=7210481)
Security Framework v1.0.0 initialized
SELinux:  Disabled at boot.
Capability LSM initialized
Mount-cache hash table entries: 512
CPU: After generic identify, caps: 078bfbff e3d3fbff 00000000 00000000 00000001 00000000 00000001
CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
CPU: L2 Cache: 128K (64 bytes/line)
CPU: After all inits, caps: 078bfbff e3d3fbff 00000000 00000410 00000001 00000000 00000001
Compat vDSO mapped to ffffe000.
Checking 'hlt' instruction... OK.
Checking for popad bug... OK.
SMP alternatives: switching to UP code
Freeing SMP alternatives: 16k freed
ACPI: Core revision 20060707
CPU0: AMD Sempron(tm) Processor 3000+ stepping 02
Total of 1 processors activated (3605.24 BogoMIPS).
ENABLING IO-APIC IRQs
..TIMER: vector=0x31 apic1=0 pin1=2 apic2=0 pin2=0
Brought up 1 CPUs
checking if image is initramfs...it isn't (no cpio magic); looks like an initrd
Freeing initrd memory: 1188k freed
NET: Registered protocol family 16
EISA bus registered
ACPI: bus type pci registered
PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=1
PCI: Using configuration type 1
Setting up standard PCI resources
ACPI: Interpreter enabled
ACPI: Using IOAPIC for interrupt routing
ACPI: PCI Root Bridge [PCI0] (0000:00)
PCI: Probing PCI hardware (bus 00)
Boot video device is 0000:01:00.0
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12 14 15)
ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 7 10 11 12 14 15)
ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 *11 12 14 15)
ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
Linux Plug and Play Support v0.97 (c) Adam Belay
pnp: PnP ACPI init
pnp: PnP ACPI: found 15 devices
PnPBIOS: Disabled by ACPI PNP
SCSI subsystem initialized
libata version 2.00 loaded.
PCI: Using ACPI for IRQ routing
PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
NetLabel: Initializing
NetLabel:  domain hash size = 128
NetLabel:  protocols = UNLABELED CIPSOv4
NetLabel:  unlabeled traffic allowed by default
pnp: 00:0b: ioport range 0x680-0x6ff has been reserved
pnp: 00:0b: ioport range 0x295-0x296 has been reserved
PCI: Bridge: 0000:00:01.0
  IO window: disabled.
  MEM window: fca00000-feafffff
  PREFETCH window: dc900000-ec8fffff
PCI: Setting latency timer of device 0000:00:01.0 to 64
NET: Registered protocol family 2
IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
TCP bind hash table entries: 65536 (order: 7, 786432 bytes)
TCP: Hash tables configured (established 131072 bind 65536)
TCP reno registered
audit: initializing netlink socket (disabled)
audit(1168533466.508:1): initialized
highmem bounce pool size: 64 pages
Total HugeTLB memory allocated, 0
VFS: Disk quotas dquot_6.5.1
Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
fuse init (API version 7.8)
fuse distribution version: 2.6.1
io scheduler noop registered
io scheduler anticipatory registered
io scheduler deadline registered (default)
io scheduler cfq registered
vesafb: framebuffer at 0xe0000000, mapped to 0xf8880000, using 3072k, total 65536k
vesafb: mode is 1024x768x16, linelength=2048, pages=1
vesafb: protected mode interface info at c000:e340
vesafb: pmi: set display start = c00ce376, set palette = c00ce3e0
vesafb: pmi: ports = 3b4 3b5 3ba 3c0 3c1 3c4 3c5 3c6 3c7 3c8 3c9 3cc 3ce 3cf 3d0 3d1 3d2 3d3 3d4 3d5 3da
vesafb: scrolling: redraw
vesafb: Truecolor: size=0:5:6:5, shift=0:11:5:0
Console: switching to colour frame buffer device 128x48
fb0: VESA VGA frame buffer device
isapnp: Scanning for PnP cards...
isapnp: No Plug & Play device found
Real Time Clock Driver v1.12ac
Floppy drive(s): fd0 is 1.44M
FDC 0 is a post-1991 82077
RAMDISK driver initialized: 16 RAM disks of 100000K size 1024 blocksize
Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
VP_IDE: IDE controller at PCI slot 0000:00:0f.1
ACPI: PCI Interrupt 0000:00:0f.1[A] -> GSI 20 (level, low) -> IRQ 16
VP_IDE: chipset revision 6
VP_IDE: not 100% native mode: will probe irqs later
VP_IDE: VIA vt8237 (rev 00) IDE UDMA133 controller on pci0000:00:0f.1
    ide0: BM-DMA at 0xfc00-0xfc07, BIOS settings: hda:pio, hdb:DMA
    ide1: BM-DMA at 0xfc08-0xfc0f, BIOS settings: hdc:pio, hdd:pio
Probing IDE interface ide0...
hdb: SONY DVD RW DW-Q30A, ATAPI CD/DVD-ROM drive
ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
Probing IDE interface ide1...
Probing IDE interface ide1...
hdb: ATAPI 32X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache
Uniform CD-ROM driver Revision: 3.20
Loading iSCSI transport class v2.0-724.<7>sata_via 0000:00:0f.0: version 2.0
ACPI: PCI Interrupt 0000:00:0f.0[B] -> GSI 20 (level, low) -> IRQ 16
sata_via 0000:00:0f.0: routed to hard irq line 11
ata1: SATA max UDMA/133 cmd 0xEC00 ctl 0xE802 bmdma 0xDC00 irq 16
ata2: SATA max UDMA/133 cmd 0xE400 ctl 0xE002 bmdma 0xDC08 irq 16
scsi0 : sata_via
ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
ata1.00: ATA-7, max UDMA/133, 312581808 sectors: LBA48
ata1.00: ata1: dev 0 multi count 16
ata1.00: configured for UDMA/133
scsi1 : sata_via
ata2: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
ATA: abnormal status 0x7F on port 0xE407
scsi 0:0:0:0: Direct-Access     ATA      WDC WD1600JS-00M 02.0 PQ: 0 ANSI: 5
SCSI device sda: 312581808 512-byte hdwr sectors (160042 MB)
sda: Write Protect is off
sda: Mode Sense: 00 3a 00 00
SCSI device sda: drive cache: write back
SCSI device sda: 312581808 512-byte hdwr sectors (160042 MB)
sda: Write Protect is off
sda: Mode Sense: 00 3a 00 00
SCSI device sda: drive cache: write back
 sda: sda1 sda2 sda3 < sda5 sda6 >
sd 0:0:0:0: Attached scsi disk sda
PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
serio: i8042 KBD port at 0x60,0x64 irq 1
serio: i8042 AUX port at 0x60,0x64 irq 12
mice: PS/2 mouse device common for all mice
EISA: Probing bus 0 at eisa.0
EISA: Detected 0 cards.
Initializing XFRM netlink socket
NET: Registered protocol family 1
NET: Registered protocol family 15
Using IPI No-Shortcut mode
ACPI: (supports S0 S1 S3 S4 S5)
Time: tsc clocksource has been installed.
input: AT Translated Set 2 keyboard as /class/input/input0
input: ImPS/2 Generic Wheel Mouse as /class/input/input1
RAMDISK: Compressed image found at block 0
VFS: Mounted root (ext2 filesystem).
Failed initialization of WD-7000 SCSI card!
usbcore: registered new interface driver usbfs
usbcore: registered new interface driver hub
usbcore: registered new device driver usb
ACPI: PCI Interrupt 0000:00:10.4[C] -> GSI 21 (level, low) -> IRQ 17
ehci_hcd 0000:00:10.4: EHCI Host Controller
ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 1
ehci_hcd 0000:00:10.4: irq 17, io mem 0xfebefc00
ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
usb usb1: configuration #1 chosen from 1 choice
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 8 ports detected
USB Universal Host Controller Interface driver v3.0
ACPI: PCI Interrupt 0000:00:10.0[A] -> GSI 21 (level, low) -> IRQ 17
uhci_hcd 0000:00:10.0: UHCI Host Controller
uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 2
uhci_hcd 0000:00:10.0: irq 17, io base 0x0000d400
usb usb2: configuration #1 chosen from 1 choice
hub 2-0:1.0: USB hub found
hub 2-0:1.0: 2 ports detected
ACPI: PCI Interrupt 0000:00:10.1[A] -> GSI 21 (level, low) -> IRQ 17
uhci_hcd 0000:00:10.1: UHCI Host Controller
uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 3
uhci_hcd 0000:00:10.1: irq 17, io base 0x0000d000
usb usb3: configuration #1 chosen from 1 choice
hub 3-0:1.0: USB hub found
hub 3-0:1.0: 2 ports detected
ACPI: PCI Interrupt 0000:00:10.2[B] -> GSI 21 (level, low) -> IRQ 17
uhci_hcd 0000:00:10.2: UHCI Host Controller
uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 4
uhci_hcd 0000:00:10.2: irq 17, io base 0x0000cc00
usb usb4: configuration #1 chosen from 1 choice
hub 4-0:1.0: USB hub found
hub 4-0:1.0: 2 ports detected
ACPI: PCI Interrupt 0000:00:10.3[B] -> GSI 21 (level, low) -> IRQ 17
uhci_hcd 0000:00:10.3: UHCI Host Controller
uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 5
uhci_hcd 0000:00:10.3: irq 17, io base 0x0000c800
usb usb5: configuration #1 chosen from 1 choice
hub 5-0:1.0: USB hub found
hub 5-0:1.0: 2 ports detected
ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
usbcore: registered new interface driver libusual
usbcore: registered new interface driver hiddev
usbcore: registered new interface driver usbhid
drivers/usb/input/hid-core.c: v2.6:USB HID core driver
Initializing USB Mass Storage driver...
usbcore: registered new interface driver usb-storage
USB Mass Storage support registered.
ieee1394: Initialized config rom entry `ip1394'
ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)
ieee1394: sbp2: Try serialize_io=0 for better performance
Warning: /proc/ide/hd?/settings interface is obsolete, and will be removed soon!
ISO 9660 Extensions: Microsoft Joliet Level 3
ISO 9660 Extensions: RRIP_1991A
cloop: Initializing cloop v2.05
cloop: loaded (max 8 devices)
cloop: /cdrom/KNOPPIX/KNOPPIX: 15609 blocks, 131072 bytes/block, largest block is 131098 bytes.
cloop: loaded 256 blocks into cache.
ISO 9660 Extensions: RRIP_1991A
aufs 2.6.19-20061211
Freeing unused kernel memory: 336k freed
ACPI: Power Button (FF) [PWRF]
ACPI: Sleep Button (CM) [SLPB]
ACPI: Power Button (CM) [PWRB]
Using specific hotkey driver
ACPI: Processor [CPU1] (supports 16 throttling states)
cpufreq: No nForce2 chipset.
powernow: This module only works with AMD K7 CPUs
powernow-k8: Found 1 AMD Sempron(tm) Processor 3000+ processors (version 2.00.00)
powernow-k8:    0 : fid 0xa (1800 MHz), vid 0x6
powernow-k8:    1 : fid 0x2 (1000 MHz), vid 0x12
Time: acpi_pm clocksource has been installed.
Linux agpgart interface v0.101 (c) Dave Jones
agpgart: Detected AGP bridge 0
agpgart: AGP aperture is 128M @ 0xd0000000
pci_hotplug: PCI Hot Plug PCI Core version: 0.5
shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Loading module: rt2500pci - CVS (N/A) by http://rt2x00.serialmonkey.com.
ACPI: PCI Interrupt 0000:00:08.0[A] -> GSI 16 (level, low) -> IRQ 18
wmaster0: Selected rate control algorithm 'simple'
Loading module: rt61pci - CVS (N/A) by http://rt2x00.serialmonkey.com.
via-rhine.c:v1.10-LK1.4.2 Sept-11-2006 Written by Donald Becker
ACPI: PCI Interrupt 0000:00:0a.0[A] -> GSI 18 (level, low) -> IRQ 19
wmaster1: Selected rate control algorithm 'simple'
ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 23 (level, low) -> IRQ 20
eth0: VIA Rhine II at 0xfebef800, 00:13:d3:e7:eb:b5, IRQ 20.
eth0: MII PHY found at address 1, status 0x7849 advertising 01e1 Link 0000.
Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing disabled
serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
parport: PnPBIOS parport detected.
parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
eth0: link down
rt61pci->rt61pci_init_firmware_cont: Error - Failed to load Firmware.
ACPI: PCI Interrupt 0000:00:11.5[C] -> GSI 22 (level, low) -> IRQ 21
PCI: Setting latency timer of device 0000:00:11.5 to 64
NET: Registered protocol family 17
device-mapper: ioctl: 4.10.0-ioctl (2006-09-14) initialised: dm-devel@redhat.com
kjournald starting.  Commit interval 5 seconds
EXT3-fs: mounted filesystem with ordered data mode.
Adding 2048276k swap on /dev/sda2.  Priority:-1 extents:1 across:2048276k
kjournald starting.  Commit interval 5 seconds
EXT3-fs: mounted filesystem with ordered data mode.
kjournald starting.  Commit interval 5 seconds
EXT3-fs: mounted filesystem with ordered data mode.
NET: Registered protocol family 10
lo: Disabled Privacy Extensions
ADDRCONF(NETDEV_UP): eth0: link is not ready
Mobile IPv6
eth0: link down
ADDRCONF(NETDEV_UP): eth0: link is not ready
Bluetooth: Core ver 2.11
NET: Registered protocol family 31
Bluetooth: HCI device and connection manager initialized
Bluetooth: HCI socket layer initialized
Bluetooth: L2CAP ver 2.8
Bluetooth: L2CAP socket layer initialized
Bluetooth: RFCOMM socket layer initialized
Bluetooth: RFCOMM TTY layer initialized
Bluetooth: RFCOMM ver 1.8
wlan0: no IPv6 routers present
**********************************************


```

---

### Post by dmizer on 2007-01-11
wow ... knoppix made the thing get an ip address.  that's fantastic information.

with that ... here is your howto: [http://www.ubuntuforums.org/showthread.php?t=296822](http://www.ubuntuforums.org/showthread.php?t=296822)

before you do, boot ubuntu without the card atached, and perform the following:
```
sudo su
echo 'blacklist rt61pci' >> /etc/modprobe.d/blacklist
exit
```

power down, install the card, and your machine should boot with the card atached now.  then follow the howto.

---

### Post by knichel on 2007-01-12
Thank you for the post.  I did what you said and it still hangs on the configuring network devices when the card is intstalled.  As I read the contents of lspci, I see a rt2500.  Is rt61pci correct?

BTW, KNOPPIX did not assign the ip address, I was trying to configure the card to work with my network.  I was unsuccessful.

---

### Post by dmizer on 2007-01-12
assuming that you actually have two wireless cards installed (as indicated by knoppix) ...

have you tried escaping past the "configuring network devices" by hitting a ctrl + c ?

from what i've found, the rt61pci module is configured to work for both cards listed in the lspci output from knoppix.  you might also try blacklisting rt61

since both cards use the same driver, there might be a conflict of sorts?  try booting with just the new card installed and see if you get better results.

---

### Post by knichel on 2007-01-12
We do have 2 wireless cards.

I followed the directions.  The only way I can get the comptuer to boot is to blacklist rt61 and rt61pci.  I installed both cards and followed the directions on the other post and when I do iwconfig, ra1 (the card in question) is not loaded.  I am guessing that is because rt61 is blacklisted?  SO, I unblacklisted it and restarted.

I eventually got the computer to boot with both cards installed. I followed the directions in the how to again and when instructed to do iwconfig, it shows both interfaces, but ra1 is listed as ra1_ifrename with a blank ssid.  I checked /etc/network/interfaces and ra0 and ra1 are set up correctly.  

How do I rename ra1_ifrename to ra1?
When I let the computer boot, it hangs on configuring hardware for a bit and then loads, but both cards do not work when I do this.
I appreciate all the help you are giving me.

Mike

---

### Post by dmizer on 2007-01-17
i think your two cards may be conflicting with eachother (possible irq conflicts?) but i'm not sure, and i'm not sure where to look to determine if that's the case or not.

are you able to get connected if only one card is installed?

---

### Post by knichel on 2007-01-22
I can connect to either wireless router when the older card is installed, but neither when the newer card is installed.

---

