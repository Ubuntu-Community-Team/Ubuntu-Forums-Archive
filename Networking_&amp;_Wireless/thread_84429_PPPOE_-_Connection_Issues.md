---
title: "PPPOE - Connection Issues"
date: 2005-10-31
forum: Networking &amp; Wireless
---

### Post by salman_arabi on 2005-10-31
Hi,

I have installed Ubuntu 5.10 as a new installation (nat an upgrade from 5.04). I am facing a weird problem. I am not able to see any website / browse. Seem like I am getting connected to internet but not able to see any website.

-- I have a broadband connection.
-- I have a "RFC 1483 bridged" router connection settings.
-- I have installed rp-pppoe-3.6, done the configurations properly. I have also added the DNS address to the file /etc/resolv.conf by editing the file.
-- Opened firefox. Typed "about:config" in the address bar, type "ipv6" in the new search bar, set the "network.dns.disableIPV6" from "false" to "true".
-- Here is a summary of some of the messages I get:
1) sudo pppoe-start
```
Connected!
```
2) ping -c 3 [www.google.com:](www.google.com:)
```
unknown host www.google.com  
```
3) plog:
```

Oct 31 13:14:19 localhost pppd[9096]: Using interface ppp0
Oct 31 13:14:19 localhost pppd[9096]: Connect: ppp0 <--> /dev/pts/1
Oct 31 13:14:20 localhost pppd[9096]: PAP authentication succeeded
Oct 31 13:14:20 localhost pppd[9096]: Cannot determine ethernet address for proxy ARP
Oct 31 13:14:20 localhost pppd[9096]: local  IP address 61.247.249.246
Oct 31 13:14:20 localhost pppd[9096]: remote IP address 203.145.161.1

```
4) ifup eth0:
```
interface eth0 already configured. 
```
5) sudo dmesg:
```

00
[4294667.747000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[4294667.747000] CPU: L2 Cache: 256K (64 bytes/line)
[4294667.747000] CPU: After all inits, caps: 078bfbff e3d3fbff 00000000 00000010 00000001 00000000 00000000
[4294667.747000] CPU: AMD Hammer Family processor - Model Unknown stepping 02
[4294667.747000] Enabling fast FPU save and restore... done.
[4294667.747000] Enabling unmasked SIMD FPU exception support... done.
[4294667.747000] Checking 'hlt' instruction... OK.
[4294667.751000] Checking for popad bug... OK.
[4294667.751000] checking if image is initramfs... it is
[4294668.260000] Freeing initrd memory: 4821k freed
[4294668.264000] ACPI: Looking for DSDT in initrd... not found!
[4294668.329000]  not found!
[4294668.356000] ENABLING IO-APIC IRQs
[4294668.356000] ..TIMER: vector=0x31 pin1=2 pin2=-1
[4294668.468000] NET: Registered protocol family 16
[4294668.468000] EISA bus registered
[4294668.468000] ACPI: bus type pci registered
[4294668.472000] PCI: PCI BIOS revision 2.10 entry at 0xfb7c0, last bus=1
[4294668.472000] PCI: Using configuration type 1
[4294668.472000] mtrr: v2.0 (20020519)
[4294668.472000] ACPI: Subsystem revision 20050729
[4294668.484000] ACPI: Interpreter enabled
[4294668.484000] ACPI: Using IOAPIC for interrupt routing
[4294668.485000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[4294668.485000] PCI: Probing PCI hardware (bus 00)
[4294668.485000] ACPI: Assume root bridge [\_SB_.PCI0] segment is 0
[4294668.489000] Boot video device is 0000:01:00.0
[4294668.558000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[4294668.561000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 7 *10 11 12)
[4294668.561000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 6 7 10 *11 12)
[4294668.562000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 6 7 10 11 12) *5
[4294668.562000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[4294668.563000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[4294668.563000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[4294668.563000] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[4294668.564000] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[4294668.564000] ACPI: PCI Interrupt Link [ALKA] (IRQs *20)
[4294668.565000] ACPI: PCI Interrupt Link [ALKB] (IRQs *21)
[4294668.565000] ACPI: PCI Interrupt Link [ALKC] (IRQs *22)
[4294668.566000] ACPI: PCI Interrupt Link [ALKD] (IRQs *23)
[4294668.568000] Linux Plug and Play Support v0.97 (c) Adam Belay
[4294668.568000] pnp: PnP ACPI init
[4294668.574000] pnp: PnP ACPI: found 12 devices
[4294668.574000] PnPBIOS: Disabled by ACPI PNP
[4294668.574000] PCI: Using ACPI for IRQ routing
[4294668.574000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[4294668.603000] pnp: 00:01: ioport range 0x4000-0x407f could not be reserved
[4294668.603000] pnp: 00:01: ioport range 0x5000-0x500f has been reserved
[4294668.604000] audit: initializing netlink socket (disabled)
[4294668.604000] audit: initialized
[4294668.604000] VFS: Disk quotas dquot_6.5.1
[4294668.604000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[4294668.604000] devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
[4294668.604000] devfs: boot_options: 0x0
[4294668.604000] Initializing Cryptographic API
[4294668.604000] isapnp: Scanning for PnP cards...
[4294668.957000] isapnp: No Plug & Play device found
[4294668.975000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[4294668.975000] serio: i8042 AUX port at 0x60,0x64 irq 12
[4294668.975000] serio: i8042 KBD port at 0x60,0x64 irq 1
[4294668.975000] Serial: 8250/16550 driver $Revision: 1.90 $ 54 ports, IRQ sharing enabled
[4294668.975000] ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294668.977000] ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294668.977000] io scheduler noop registered
[4294668.977000] io scheduler anticipatory registered
[4294668.977000] io scheduler deadline registered
[4294668.977000] io scheduler cfq registered
[4294668.978000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[4294668.978000] EISA: Probing bus 0 at eisa.0
[4294668.978000] Cannot allocate resource for EISA slot 4
[4294668.978000] Cannot allocate resource for EISA slot 5
[4294668.978000] EISA: Detected 0 cards.
[4294668.978000] NET: Registered protocol family 2
[4294668.987000] IP: routing cache hash table of 4096 buckets, 32Kbytes
[4294668.987000] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[4294668.987000] TCP bind hash table entries: 16384 (order: 4, 65536 bytes)
[4294668.987000] TCP: Hash tables configured (established 16384 bind 16384)
[4294668.987000] NET: Registered protocol family 8
[4294668.987000] NET: Registered protocol family 20
[4294668.987000] ACPI wakeup devices:
[4294668.987000] SLPB PCI0 USB0 USB1 USB2 USB3 USB4 USB5 USB6 USB7 LAN0 AC97 MC97
[4294668.987000] ACPI: (supports S0 S1 S4 S5)
[4294668.987000] Freeing unused kernel memory: 224k freed
[4294669.001000] vga16fb: initializing
[4294669.001000] vga16fb: mapped to 0xc00a0000
[4294669.165000] Console: switching to colour frame buffer device 80x30
[4294669.165000] fb0: VGA16 VGA frame buffer device
[4294669.168000] input: AT Translated Set 2 keyboard on isa0060/serio0
[4294670.303000] Capability LSM initialized
[4294670.314000] NET: Registered protocol family 1
[4294670.328000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[4294670.328000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[4294670.328000] ACPI: bus type ide registered
[4294670.337000] VP_IDE: IDE controller at PCI slot 0000:00:0f.1
[4294670.337000] ACPI: PCI Interrupt Link [ALKA] enabled at IRQ 20
[4294670.337000] ACPI: PCI Interrupt 0000:00:0f.1[A] -> Link [ALKA] -> GSI 20 (level, low) -> IRQ 20
[4294670.337000] PCI: Via IRQ fixup for 0000:00:0f.1, from 255 to 4
[4294670.337000] VP_IDE: chipset revision 6
[4294670.337000] VP_IDE: not 100% native mode: will probe irqs later
[4294670.337000] VP_IDE: VIA vt8237 (rev 00) IDE UDMA133 controller on pci0000:00:0f.1
[4294670.337000]     ide0: BM-DMA at 0xe600-0xe607, BIOS settings: hda:DMA, hdb:DMA
[4294670.337000]     ide1: BM-DMA at 0xe608-0xe60f, BIOS settings: hdc:DMA, hdd:DMA
[4294670.337000] Probing IDE interface ide0...
[4294670.721000] hda: ST380011A, ATA DISK drive
[4294670.976000] hdb: ST380021A, ATA DISK drive
[4294671.028000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[4294671.028000] Probing IDE interface ide1...
[4294671.820000] hdc: SONY DVD RW DRU-720A, ATAPI CD/DVD-ROM drive
[4294672.534000] hdd: SAMSUNG CD-R/RW DRIVE SW-252F, ATAPI CD/DVD-ROM drive
[4294672.585000] ide1 at 0x170-0x177,0x376 on irq 15
[4294672.585000] Probing IDE interface ide2...
[4294673.098000] Probing IDE interface ide3...
[4294673.610000] Probing IDE interface ide4...
[4294674.122000] Probing IDE interface ide5...
[4294674.637000] hda: max request size: 1024KiB
[4294674.637000] hda: 156301488 sectors (80026 MB) w/2048KiB Cache, CHS=16383/255/63, UDMA(100)
[4294674.637000] hda: cache flushes supported
[4294674.638000]  /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 p6 > p3 p4
[4294674.688000] hdb: max request size: 128KiB
[4294674.688000] hdb: 156301488 sectors (80026 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(100)
[4294674.688000] hdb: cache flushes not supported
[4294674.688000]  /dev/ide/host0/bus0/target1/lun0: p1 p2 < p5 >
[4294674.720000] hdc: ATAPI 48X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache
[4294674.720000] Uniform CD-ROM driver Revision: 3.20
[4294674.724000] hdd: ATAPI 1X CD-ROM CD-R/RW drive, 2048kB Cache
[4294675.108000] Attempting manual resume
[4294675.108000] swsusp: Suspend partition has wrong signature?
[4294675.174000] SCSI subsystem initialized
[4294675.175000] libata version 1.11 loaded.
[4294675.176000] sata_via version 1.1
[4294675.176000] ACPI: PCI Interrupt 0000:00:0f.0[B] -> Link [ALKA] -> GSI 20 (level, low) -> IRQ 20
[4294675.176000] PCI: Via IRQ fixup for 0000:00:0f.0, from 11 to 4
[4294675.176000] sata_via(0000:00:0f.0): routed to hard irq line 4
[4294675.176000] ata1: SATA max UDMA/133 cmd 0xE000 ctl 0xE102 bmdma 0xE400 irq 20
[4294675.176000] ata2: SATA max UDMA/133 cmd 0xE200 ctl 0xE302 bmdma 0xE408 irq 20
[4294675.377000] ata1: no device found (phy stat 00000000)
[4294675.377000] scsi0 : sata_via
[4294675.578000] ata2: no device found (phy stat 00000000)
[4294675.578000] scsi1 : sata_via
[4294675.596000] usbcore: registered new driver usbfs
[4294675.596000] usbcore: registered new driver hub
[4294675.597000] USB Universal Host Controller Interface driver v2.2
[4294675.598000] ACPI: PCI Interrupt Link [ALKB] enabled at IRQ 21
[4294675.598000] ACPI: PCI Interrupt 0000:00:10.0[A] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 21
[4294675.598000] PCI: Via IRQ fixup for 0000:00:10.0, from 10 to 5
[4294675.598000] uhci_hcd 0000:00:10.0: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
[4294675.660000] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
[4294675.660000] uhci_hcd 0000:00:10.0: irq 21, io base 0x0000e700
[4294675.660000] hub 1-0:1.0: USB hub found
[4294675.660000] hub 1-0:1.0: 2 ports detected
[4294675.663000] ACPI: PCI Interrupt 0000:00:10.1[A] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 21
[4294675.663000] PCI: Via IRQ fixup for 0000:00:10.1, from 10 to 5
[4294675.663000] uhci_hcd 0000:00:10.1: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (#2)
[4294675.725000] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
[4294675.725000] uhci_hcd 0000:00:10.1: irq 21, io base 0x0000e800
[4294675.725000] hub 2-0:1.0: USB hub found
[4294675.725000] hub 2-0:1.0: 2 ports detected
[4294675.728000] ACPI: PCI Interrupt 0000:00:10.2[B] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 21
[4294675.728000] PCI: Via IRQ fixup for 0000:00:10.2, from 11 to 5
[4294675.728000] uhci_hcd 0000:00:10.2: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (#3)
[4294675.790000] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
[4294675.790000] uhci_hcd 0000:00:10.2: irq 21, io base 0x0000e900
[4294675.790000] hub 3-0:1.0: USB hub found
[4294675.790000] hub 3-0:1.0: 2 ports detected
[4294675.793000] ACPI: PCI Interrupt 0000:00:10.3[B] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 21
[4294675.793000] PCI: Via IRQ fixup for 0000:00:10.3, from 11 to 5
[4294675.793000] uhci_hcd 0000:00:10.3: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (#4)
[4294675.855000] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
[4294675.855000] uhci_hcd 0000:00:10.3: irq 21, io base 0x0000ea00
[4294675.855000] hub 4-0:1.0: USB hub found
[4294675.855000] hub 4-0:1.0: 2 ports detected
[4294675.891000] ACPI: PCI Interrupt 0000:00:10.4[C] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 21
[4294675.891000] ehci_hcd 0000:00:10.4: VIA Technologies, Inc. USB 2.0
[4294675.891000] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 5
[4294675.891000] ehci_hcd 0000:00:10.4: irq 21, io mem 0xf6000000
[4294675.891000] ehci_hcd 0000:00:10.4: USB 2.0 initialized, EHCI 1.00, driver 10 Dec 2004
[4294675.891000] hub 5-0:1.0: USB hub found
[4294675.891000] hub 5-0:1.0: 8 ports detected
[4294675.937000] via-rhine.c:v1.10-LK1.2.0-2.6 June-10-2004 Written by Donald Becker
[4294675.938000] ACPI: PCI Interrupt Link [ALKD] enabled at IRQ 23
[4294675.938000] ACPI: PCI Interrupt 0000:00:12.0[A] -> Link [ALKD] -> GSI 23 (level, low) -> IRQ 23
[4294675.938000] PCI: Via IRQ fixup for 0000:00:12.0, from 10 to 7
[4294675.942000] eth0: VIA Rhine II at 0x1ed00, 00:e0:4c:d6:01:ce, IRQ 23.
[4294675.942000] eth0: MII PHY found at address 1, status 0x786d advertising 05e1 Link 41e1.
[4294678.516000] ACPI: Fan [FAN] (on)
[4294678.519000] ACPI: CPU0 (power states: C1[C1])
[4294678.521000] ACPI: Thermal Zone [THRM] (38 C)
[4294678.756000] Attempting manual resume
[4294678.774000] swsusp: Suspend partition has wrong signature?
[4294678.794000] kjournald starting.  Commit interval 5 seconds
[4294678.794000] EXT3-fs: mounted filesystem with ordered data mode.
[4294679.736000] md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294683.028000] Adding 867500k swap on /dev/hda4.  Priority:-1 extents:1
[4294683.259000] EXT3 FS on hda3, internal journal
[4294688.070000] parport: PnPBIOS parport detected.
[4294688.070000] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[4294688.156000] lp0: using parport0 (interrupt-driven).
[4294688.186000] mice: PS/2 mouse device common for all mice
[4294688.518000] input: ImPS/2 Generic Wheel Mouse on isa0060/serio1
[4294689.031000] ts: Compaq touchscreen protocol output
[4294690.820000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@redhat.com
[4294691.618000] cdrom: open failed.
[4294691.620000] cdrom: open failed.
[4294692.606000] NTFS driver 2.1.22 [Flags: R/O MODULE].
[4294692.656000] NTFS volume version 3.1.
[4294692.689000] NTFS volume version 3.1.
[4294693.983000] Linux agpgart interface v0.101 (c) Dave Jones
[4294693.991000] agpgart: Detected AGP bridge 0
[4294694.011000] agpgart: AGP aperture is 128M @ 0xe8000000
[4294694.291000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[4294694.303000] shpchp: shpc_init : shpc_cap_offset == 0
[4294694.303000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[4294694.974000] via82xx: Assuming DXS channels with 48k fixed sample rate.
[4294694.974000]          Please try dxs_support=5 option
[4294694.974000]          and report if it works on your machine.
[4294694.974000]          For more details, read ALSA-Configuration.txt.
[4294694.974000] ACPI: PCI Interrupt Link [ALKC] enabled at IRQ 22
[4294694.974000] ACPI: PCI Interrupt 0000:00:11.5[C] -> Link [ALKC] -> GSI 22 (level, low) -> IRQ 22
[4294694.974000] PCI: Via IRQ fixup for 0000:00:11.5, from 5 to 6
[4294694.974000] PCI: Setting latency timer of device 0000:00:11.5 to 64
[4294697.795000] Real Time Clock Driver v1.12
[4294697.891000] input: PC Speaker
[4294697.984000] Floppy drive(s): fd0 is 1.44M
[4294697.999000] FDC 0 is a post-1991 82077
[4294698.958000] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[4294698.969000] NET: Registered protocol family 17
[4294705.785000] ACPI: Power Button (FF) [PWRF]
[4294705.785000] ACPI: Power Button (CM) [PWRB]
[4294705.785000] ACPI: Sleep Button (CM) [SLPB]
[4294705.893000] ibm_acpi: ec object not found
[4294721.631000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[4294721.631000] apm: overridden by ACPI.
[4294723.014000] powernow-k8: Power state transitions not supported
[4294723.140000] Bluetooth: Core ver 2.7
[4294723.140000] NET: Registered protocol family 31
[4294723.140000] Bluetooth: HCI device and connection manager initialized
[4294723.140000] Bluetooth: HCI socket layer initialized
[4294723.164000] Bluetooth: L2CAP ver 2.7
[4294723.164000] Bluetooth: L2CAP socket layer initialized
[4294723.193000] Bluetooth: RFCOMM ver 1.5
[4294723.193000] Bluetooth: RFCOMM socket layer initialized
[4294723.193000] Bluetooth: RFCOMM TTY layer initialized
[4294760.324000] NET: Registered protocol family 10
[4294760.324000] Disabled Privacy Extensions on device c02eb280(lo)
[4294760.324000] IPv6 over IPv4 tunneling driver
[4294771.232000] eth0: no IPv6 routers present
[4295187.126000] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[4295187.140000] CSLIP: code copyright 1989 Regents of the University of California
[4295187.145000] PPP generic driver version 2.4.2
[4295187.919000] PPP BSD Compression module registered
[4295198.014000] eth0: no IPv6 routers present

```
6) ifdown eth0:
```
ifdown: interface eth0 not configured
```
7) sudo pppoe-status
```

pppoe-status: Link is up and running on interface ppp0
ppp0      Link encap:Point-to-Point Protocol
          inet addr:61.247.249.246  P-t-P:203.145.161.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:26 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3
          RX bytes:1581 (1.5 KiB)  TX bytes:1440 (1.4 KiB)

```

I am a newbee to Ubuntu. Please help in solving this problem. Thanks in advance.

Salman.

---

### Post by mips on 2005-10-31
Have you tried a search on this forum ?

Please post the following info in this thread:

1) Router Make & Model
2) Did you buy it or was it provided by the ISP
2) Connection type, Ethernet, USB or Wireless
3) Running in Bridged or Routed mode
4) Country you live in.
5) Your ISP and/or Broadband provider
6) What service are you subscribing to from them
7) Full TCP/IP config of PC + Router config details (PPPoE, VPI/VCI, DHCP, NAT etc)

Please provide links where possible to the above questions.

---

### Post by salman_arabi on 2005-10-31
Hi mips,

Thanks for replying. Info you asked.

1) Router Make & Model - 
--Beetel Yozan - Web Distributor II
2) Did you buy it or was it provided by the ISP
-- It was provided by ISP.
2) Connection type, Ethernet, USB or Wireless
-- Ethernet
3) Running in Bridged or Routed mode
-- Bridged (RFC 1483 bridged)
4) Country you live in.
-- India
5) Your ISP and/or Broadband provider
-- Airtel
6) What service are you subscribing to from them
-- Broadband
7) Full TCP/IP config of PC + Router config details (PPPoE, VPI/VCI, DHCP, NAT etc)
-- PPPoE Protocol should be used and I have set VPI/VCI setting in router already.

In windows, I am able to connect to internet using PPPoE dialer like (RASPPPOE). I donno how to configure the same in ubuntu.

Thanks again.

Salman

---

### Post by salman_arabi on 2005-10-31
Hi,

Could someone please help. I am struck not able to proceed further.

Thanks,
Salman

---

### Post by mips on 2005-10-31
Hi,

Just give me a bit of time and i'l get back to you.

---

### Post by mips on 2005-10-31
[QUOTE=salman_arabi]Hi mips,

Thanks for replying. Info you asked.

1) Router Make & Model - 
--Beetel Yozan - Web Distributor II
2) Did you buy it or was it provided by the ISP
-- It was provided by ISP.
2) Connection type, Ethernet, USB or Wireless
-- Ethernet
3) Running in Bridged or Routed mode
-- Bridged (RFC 1483 bridged)
4) Country you live in.
-- India
5) Your ISP and/or Broadband provider
-- Airtel
6) What service are you subscribing to from them
-- Broadband
7) Full TCP/IP config of PC + Router config details (PPPoE, VPI/VCI, DHCP, NAT etc)
-- PPPoE Protocol should be used and I have set VPI/VCI setting in router already.

In windows, I am able to connect to internet using PPPoE dialer like (RASPPPOE). I donno how to configure the same in ubuntu.

Thanks again.

Salman[/QUOTE]


Ok,

1. We have to get the router out of bridged mode. The router has to handle the PPPoE/PPPoA stuff and login automatically.

2. Call you ISP and ask them for assistance to get your router into 'routed mode'. You will need the following info, Encapsulation type, VPI, VCI, username&password, DNS servers(just incase). As them to help you with the setup on the router. I noticed in point .7 above you have set VPI/VCI but please ensure it is correct and the device is in routed mode, please call the ISP.

3. to get into your router you should enter 192.168.1.1 (I think!) into your web browser. Username&password for access is 'admin' I think or ask your ISP.

4. Once you have your router configured you have to set your PC up for DHCP & auto DNS (both windows & linux). You no longer have to run any dialer or PPPoE applications on the PC!!!

5. Once you have done the above you should have no problems.

6. [http://broadbandforum.in/Airtel_Broadband_Forum-f23.html](http://broadbandforum.in/Airtel_Broadband_Forum-f23.html)   ,can alwasy ask for help here.


Please let us know all the settings etc once you have it working so other people can also gain from this thread.

---

### Post by salman_arabi on 2005-11-01
Hi mips,

Thankyou very for your reply. I had actually set the router to bridged mode for port forwarding stuff (long story -- I have got an cheap router from my isp). 

I have now changed the router setting to routed mode. I am able to connect to internet, and it is working perfectly allright. Thanks for your help.

Salman.

---

### Post by mips on 2005-11-01
Good news.

If you still need to do port forwarding have a look at the india broadband forum and do a google search for 'Beetel port forwarding' or something of the kind. I saw some stuff on port forwarding when I was looking for info on your router.

---

### Post by salman_arabi on 2005-11-01
Hi mips,

I have also figured out how to do port forwarding. Thanks again for the info.

Salman

---

