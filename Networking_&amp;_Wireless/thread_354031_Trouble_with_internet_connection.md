---
title: "Trouble with internet connection"
date: 2007-02-05
forum: Networking &amp; Wireless
---

### Post by JoeS on 2007-02-05
Computer: Dell Optiplex GX100
Using Ubuntu Breezy Badger
I'm connected to a router through an ethernet cable

In **Network Settings **I chose ethernet connection.
In **Interface Properties **I enabled this connection.
For configuration I chose DHCP and pressed o.k., but it wouldn't connect.

I tried a couple of ethernet cards.  One a used in another computer with Linux.
Why won't this work?

Appreciate help.

---

### Post by Ryan450 on 2007-02-05
The problem with going the gui way is that if something goes wrong it doesnt give you much information to go by. I know the terminal looks a little scary, but it tells you exactly what goes wrong. 

first thing I'd want to check is make sure your cards are detected and working properly. type in ifconfig and show us the output of that please. eth0 is the default choice, with eth1 and eth2 following if you have multiple cards installed at once. lo is the localloopback.

if a network card doesnt show up there, then type in dmesg and post its output up here. 

after verifying that eth0 is indeed there then try 

sudo dhclient eth0

that will send out a dhcp request to your router, set up your ip and dns at same time if all goes well. be sure to include the output of dhclient as well and we'll work from there.

NOTE: easiest way to put up the output of these commands is by adding redirection at the end of each of them. for example. 

```
ifconfig > ifconfig.txt
sudo dhclient eth0 > dhclient.txt
dmesg > dmesg.txt
```

then you just copy over the .txt files to a floppy, copy and paste onto here once back in windows if your running a dual-boot.

---

### Post by JoeS on 2007-02-07
In Network Settings I enabled the ethernet connection.  It says "The
interface eth0 is active."  I'm still having problems with the ip and dns. 

I typed in the following commands:
```
ifconfig
sudo dhclient eth0
dmesg
```

here are the results:

```
ifconfig
```
eth0      Link encap:Ethernet  HWaddr 00:B0:D0:E6:29:66  
          inet6 addr: fe80::2b0:d0ff:fee6:2966/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:9 Base address:0xec00 

------------------------------------------------

```
sudo dhclient eth0
```
joe@ubuntu:~$    sudo dhclient eth0 > dhclient.txt
There is already a pid file /var/run/dhclient.pid with pid 7494
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/eth0/00:b0:d0:e6:29:66
Sending on   LPF/eth0/00:b0:d0:e6:29:66
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

----------------------------------------------------------

```
dmesg
```
[4294667.296000] Linux version 2.6.12-9-386 (buildd@rothera) (gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8)) #1 Mon Oct 10 13:14:36 BST 2005
[4294667.296000] BIOS-provided physical RAM map:
[4294667.296000]  BIOS-e820: 0000000000000000 - 00000000000a0000 (usable)
[4294667.296000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[4294667.296000]  BIOS-e820: 0000000000100000 - 0000000017eac000 (usable)
[4294667.296000]  BIOS-e820: 0000000017eac000 - 0000000018000000 (reserved)
[4294667.296000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[4294667.296000] 0MB HIGHMEM available.
[4294667.296000] 382MB LOWMEM available.
[4294667.296000] On node 0 totalpages: 97964
[4294667.296000]   DMA zone: 4096 pages, LIFO batch:1
[4294667.296000]   Normal zone: 93868 pages, LIFO batch:31
[4294667.296000]   HighMem zone: 0 pages, LIFO batch:1
[4294667.296000] DMI 2.3 present.
[4294667.296000] ACPI: RSDP (v000 DELL                                  ) @ 0x000fd790
[4294667.296000] ACPI: RSDT (v001 DELL    GX100   0x00000007 ASL  0x00000061) @ 0x000fd7a4
[4294667.296000] ACPI: FADT (v001 DELL    GX100   0x00000007 ASL  0x00000061) @ 0x000fd7cc
[4294667.296000] ACPI: DSDT (v001   DELL    dt_ex 0x00001000 MSFT 0x0100000b) @ 0x00000000
[4294667.296000] ACPI: PM-Timer IO Port: 0x808

[4294667.296000] Allocating PCI resources starting at 18000000 (gap: 18000000:e7b00000)
[4294667.296000] Built 1 zonelists
[4294667.296000] Kernel command line: root=/dev/hda1 ro quiet splash
[4294667.296000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[4294667.296000] mapped APIC to ffffd000 (012ff000)
[4294667.296000] Initializing CPU#0
[4294667.296000] PID hash table entries: 2048 (order: 11, 32768 bytes)
[4294667.296000] Detected 797.862 MHz processor.
[4294667.296000] Using pmtmr for high-res timesource
[4294667.296000] Console: colour VGA+ 80x25
[4294667.962000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[4294667.964000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[4294668.010000] Memory: 380292k/391856k available (1415k kernel code, 10988k reserved, 763k data, 224k init, 0k highmem)
[4294668.010000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[4294668.010000] Calibrating delay loop... 1581.05 BogoMIPS (lpj=790528)
[4294668.033000] Security Framework v1.0.0 initialized
[4294668.033000] SELinux:  Disabled at boot.
[4294668.033000] Mount-cache hash table entries: 512
[4294668.033000] CPU: After generic identify, caps: 0383f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[4294668.033000] CPU: After vendor identify, caps: 0383f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[4294668.033000] CPU: L1 I cache: 16K, L1 D cache: 16K
[4294668.033000] CPU: L2 cache: 128K
[4294668.033000] CPU: After all inits, caps: 0383f9ff 00000000 00000000 00000040 00000000 00000000 00000000
[4294668.033000] CPU: Intel Celeron (Coppermine) stepping 0a
[4294668.033000] Enabling fast FPU save and restore... done.
[4294668.033000] Enabling unmasked SIMD FPU exception support... done.
[4294668.033000] Checking 'hlt' instruction... OK.
[4294668.037000] Checking for popad bug... OK.
[4294668.037000] checking if image is initramfs... it is
[4294669.030000] Freeing initrd memory: 4828k freed
[4294669.037000] ACPI: Looking for DSDT in initrd... not found!
[4294669.194000]  not found!
[4294669.219000] NET: Registered protocol family 16
[4294669.219000] EISA bus registered
[4294669.219000] ACPI: bus type pci registered
[4294669.232000] PCI: PCI BIOS revision 2.10 entry at 0xfc0be, last bus=1
[4294669.232000] PCI: Using configuration type 1
[4294669.232000] mtrr: v2.0 (20020519)
[4294669.233000] ACPI: Subsystem revision 20050729
[4294669.247000] ACPI: Interpreter enabled
[4294669.247000] ACPI: Using PIC for interrupt routing
[4294669.247000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[4294669.247000] PCI: Probing PCI hardware (bus 00)
[4294669.247000] ACPI: Assume root bridge [\_SB_.PCI0] segment is 0
[4294669.247000] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[4294669.251000] Boot video device is 0000:00:01.0
[4294669.252000] PCI: Transparent bridge - 0000:00:1e.0
[4294669.255000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[4294669.256000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[4294669.265000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *9 10 11 12 15)
[4294669.266000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *9 10 11 12 15)
[4294669.267000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *9 10 11 12 15)
[4294669.268000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 *9 10 11 12 15)
[4294669.268000] Linux Plug and Play Support v0.97 (c) Adam Belay
[4294669.268000] pnp: PnP ACPI init
[4294669.289000] pnp: PnP ACPI: found 12 devices
[4294669.289000] PnPBIOS: Disabled by ACPI PNP
[4294669.290000] PCI: Using ACPI for IRQ routing
[4294669.290000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[4294669.299000] pnp: 00:0b: ioport range 0x800-0x85f could not be reserved
[4294669.299000] pnp: 00:0b: ioport range 0xc00-0xc7f has been reserved
[4294669.299000] pnp: 00:0b: ioport range 0x860-0x8ff could not be reserved
[4294669.301000] audit: initializing netlink socket (disabled)
[4294669.301000] audit: initialized
[4294669.301000] VFS: Disk quotas dquot_6.5.1
[4294669.301000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[4294669.301000] devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
[4294669.301000] devfs: boot_options: 0x0
[4294669.301000] Initializing Cryptographic API
[4294669.302000] isapnp: Scanning for PnP cards...
[4294669.656000] isapnp: No Plug & Play device found
[4294669.739000] PNP: PS/2 Controller [PNP0303:KBD,PNP0f13:MOU] at 0x60,0x64 irq 1,12
[4294669.743000] serio: i8042 AUX port at 0x60,0x64 irq 12
[4294669.743000] serio: i8042 KBD port at 0x60,0x64 irq 1
[4294669.743000] Serial: 8250/16550 driver $Revision: 1.90 $ 54 ports, IRQ sharing enabled
[4294669.743000] ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294669.744000] ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[4294669.753000] ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294669.754000] ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[4294669.754000] io scheduler noop registered
[4294669.754000] io scheduler anticipatory registered
[4294669.754000] io scheduler deadline registered
[4294669.754000] io scheduler cfq registered
[4294669.755000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[4294669.756000] EISA: Probing bus 0 at eisa.0
[4294669.756000] EISA: Detected 0 cards.
[4294669.756000] NET: Registered protocol family 2
[4294669.765000] IP: routing cache hash table of 4096 buckets, 32Kbytes
[4294669.765000] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[4294669.766000] TCP bind hash table entries: 16384 (order: 4, 65536 bytes)
[4294669.766000] TCP: Hash tables configured (established 16384 bind 16384)
[4294669.766000] NET: Registered protocol family 8
[4294669.766000] NET: Registered protocol family 20
[4294669.767000] ACPI wakeup devices: 
[4294669.767000] PCI0 USB0 PCI1  KBD 
[4294669.767000] ACPI: (supports S0 S1 S4 S5)
[4294669.768000] Freeing unused kernel memory: 224k freed
[4294669.809000] input: AT Translated Set 2 keyboard on isa0060/serio0
[4294669.837000] vga16fb: initializing
[4294669.837000] vga16fb: mapped to 0xc00a0000
[4294669.954000] Console: switching to colour frame buffer device 80x30
[4294669.954000] fb0: VGA16 VGA frame buffer device
[4294671.125000] Capability LSM initialized
[4294671.159000] NET: Registered protocol family 1
[4294671.198000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[4294671.198000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[4294671.199000] ACPI: bus type ide registered
[4294671.218000] ICH: IDE controller at PCI slot 0000:00:1f.1
[4294671.218000] ICH: chipset revision 2
[4294671.218000] ICH: not 100% native mode: will probe irqs later
[4294671.218000]     ide0: BM-DMA at 0xffa0-0xffa7, BIOS settings: hda:DMA, hdb:pio
[4294671.218000]     ide1: BM-DMA at 0xffa8-0xffaf, BIOS settings: hdc:DMA, hdd:pio
[4294671.218000] Probing IDE interface ide0...
[4294671.482000] hda: Maxtor 5T040H4, ATA DISK drive
[4294672.094000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[4294672.094000] Probing IDE interface ide1...
[4294672.766000] hdc: LG CD-RW CED-8080B, ATAPI CD/DVD-ROM drive
[4294673.378000] ide1 at 0x170-0x177,0x376 on irq 15
[4294673.378000] Probing IDE interface ide2...
[4294673.891000] Probing IDE interface ide3...
[4294674.404000] Probing IDE interface ide4...
[4294674.917000] Probing IDE interface ide5...
[4294675.442000] hda: max request size: 128KiB
[4294675.448000] hda: 80043264 sectors (40982 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(66)
[4294675.448000] hda: cache flushes not supported
[4294675.448000]  /dev/ide/host0/bus0/target0/lun0: p1 p2 p3
[4294675.491000] hdc: ATAPI 32X CD-ROM CD-R/RW drive, 2048kB Cache
[4294675.491000] Uniform CD-ROM driver Revision: 3.20
[4294676.609000] Attempting manual resume
[4294676.609000] swsusp: Suspend partition has wrong signature?
[4294676.736000] usbcore: registered new driver usbfs
[4294676.736000] usbcore: registered new driver hub
[4294676.740000] USB Universal Host Controller Interface driver v2.2
[4294676.741000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 9
[4294676.741000] PCI: setting IRQ 9 as level-triggered
[4294676.741000] ACPI: PCI Interrupt 0000:00:1f.2[D] -> Link [LNKD] -> GSI 9 (level, low) -> IRQ 9
[4294676.741000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[4294676.741000] uhci_hcd 0000:00:1f.2: Intel Corporation 82801AA USB
[4294676.803000] uhci_hcd 0000:00:1f.2: new USB bus registered, assigned bus number 1
[4294676.803000] uhci_hcd 0000:00:1f.2: irq 9, io base 0x0000ff80
[4294676.803000] hub 1-0:1.0: USB hub found
[4294676.803000] hub 1-0:1.0: 2 ports detected
[4294676.849000] ohci_hcd: 2004 Nov 08 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[4294676.850000] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 9
[4294676.850000] ACPI: PCI Interrupt 0000:01:07.0[A] -> Link [LNKA] -> GSI 9 (level, low) -> IRQ 9
[4294676.850000] ohci_hcd 0000:01:07.0: OPTi Inc. 82C861
[4294676.850000] ohci_hcd 0000:01:07.0: new USB bus registered, assigned bus number 2
[4294676.850000] ohci_hcd 0000:01:07.0: irq 9, io mem 0xfdfff000
[4294676.903000] hub 2-0:1.0: USB hub found
[4294676.903000] hub 2-0:1.0: 2 ports detected
[4294676.952000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 9
[4294676.952000] ACPI: PCI Interrupt 0000:01:0c.0[A] -> Link [LNKC] -> GSI 9 (level, low) -> IRQ 9
[4294676.952000] 3c59x: Donald Becker and others. [www.scyld.com/network/vortex.html](www.scyld.com/network/vortex.html)
[4294676.952000] 0000:01:0c.0: 3Com PCI 3c905C Tornado at 0xec00. Vers LK1.1.19
[4294677.098000] usb 2-1: new low speed USB device using ohci_hcd and address 2
[4294679.043000] usbcore: registered new driver hiddev
[4294679.052000] input: USB HID v1.10 Mouse [Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)] on usb-0000:01:07.0-1
[4294679.052000] usbcore: registered new driver usbhid
[4294679.052000] drivers/usb/input/hid-core.c: v2.01:USB HID core driver
[4294680.270000] ACPI: CPU0 (power states: C1[C1])
[4294680.541000] Attempting manual resume
[4294680.541000] swsusp: Suspend partition has wrong signature?
[4294680.561000] ReiserFS: hda1: found reiserfs format "3.6" with standard journal
[4294680.737000] ReiserFS: hda1: using ordered data mode
[4294680.748000] ReiserFS: hda1: journal params: device hda1, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[4294680.755000] ReiserFS: hda1: checking transaction log (hda1)
[4294680.790000] ReiserFS: hda1: Using r5 hash to sort names
[4294681.932000] md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294687.704000] Adding 489972k swap on /dev/hda2.  Priority:-1 extents:1
[4294696.899000] parport: PnPBIOS parport detected.
[4294696.899000] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,EPP,ECP]
[4294696.998000] lp0: using parport0 (interrupt-driven).
[4294697.109000] mice: PS/2 mouse device common for all mice
[4294701.216000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[4294702.013000] cdrom: open failed.
[4294707.349000] ReiserFS: hda3: found reiserfs format "3.6" with standard journal
[4294709.838000] ReiserFS: hda3: using ordered data mode
[4294709.855000] ReiserFS: hda3: journal params: device hda3, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[4294709.861000] ReiserFS: hda3: checking transaction log (hda3)
[4294709.893000] ReiserFS: hda3: Using r5 hash to sort names
[4294711.533000] Linux agpgart interface v0.101 (c) Dave Jones
[4294711.563000] agpgart: Detected an Intel i810 DC100 Chipset.
[4294711.568000] agpgart: detected 4MB dedicated video ram.
[4294711.591000] agpgart: AGP aperture is 64M @ 0xf8000000
[4294711.948000] hw_random hardware driver 1.0.0 loaded
[4294712.079000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[4294712.097000] shpchp: acpi_shpchprm:\_SB_.PCI0 evaluate _BBN fail=0x5
[4294712.097000] shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x5
[4294713.672000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 9
[4294713.672000] ACPI: PCI Interrupt 0000:01:08.0[A] -> Link [LNKB] -> GSI 9 (level, low) -> IRQ 9
[4294716.962000] input: PC Speaker
[4294717.283000] Real Time Clock Driver v1.12
[4294717.366000] Floppy drive(s): fd0 is 1.44M
[4294717.378000] FDC 0 is a National Semiconductor PC87306
[4294718.406000] ts: Compaq touchscreen protocol output
[4294719.381000] ACPI: PCI Interrupt 0000:01:0c.0[A] -> Link [LNKC] -> GSI 9 (level, low) -> IRQ 9
[4294719.431000] NET: Registered protocol family 17
[4294784.734000] ACPI: Power Button (FF) [PWRF]
[4294784.914000] ibm_acpi: ec object not found
[4294796.740000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[4294796.740000] apm: overridden by ACPI.
[4294799.262000] Bluetooth: Core ver 2.7
[4294799.262000] NET: Registered protocol family 31
[4294799.262000] Bluetooth: HCI device and connection manager initialized
[4294799.262000] Bluetooth: HCI socket layer initialized
[4294799.331000] Bluetooth: L2CAP ver 2.7
[4294799.331000] Bluetooth: L2CAP socket layer initialized
[4294799.401000] Bluetooth: RFCOMM ver 1.5
[4294799.401000] Bluetooth: RFCOMM socket layer initialized
[4294799.401000] Bluetooth: RFCOMM TTY layer initialized
[4295108.520000] NET: Registered protocol family 10
[4295108.520000] Disabled Privacy Extensions on device c02eb280(lo)
[4295108.520000] IPv6 over IPv4 tunneling driver
[4295118.572000] eth0: no IPv6 routers present

---

### Post by IcemanV9 on 2007-02-08
It seems that your box is not getting IP assigned from the router. Can you make sure your router's DHCP is enabled?

---

### Post by mips on 2007-02-08
Also try manually configuring your ip parameters and see if you get connectivity in order to eliminate lower level problems.

---

### Post by JoeS on 2007-02-11
I'm sharing the internet with someone.  He switched the ports for the internet connections of mine and his computer.  He got a connection with both; I didn't with any.  His wife also gets a connection with her laptop, so doesn't think it's a problem with the router.

I tried 2 NIC cards plus the integrated card.  I didn't get a connection with any.  I tried all 3 settings in the setup for Network Interface: 
1. On
2. On w/ MBA
3. Off

Only one card that gave me a green light (computer detecting a physical connection to the network) when the ethernet cable was connected.
I think I used this  card on another computer with Linux.
I couldn't get a Desktop after I logged in with name and password.  It must have been waiting for something; could get the Desktop when the cable was disconnected. 

Is there some settings I need to change to get the internet working?

Appreciate help, thanks.

---

### Post by sdide on 2007-02-11
Hey,

to check if the  link, duplex and speed settings of your NIC, I suggest ethtool.
(as root) example:

```
# ethtool eth0
Settings for eth0:
        Supported ports: [ TP ]
        Supported link modes:   10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Full 
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Full 
        Advertised auto-negotiation: Yes
        Speed: 1000Mb/s
        Duplex: Full
        Port: Twisted Pair
        PHYAD: 1
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: d
        Wake-on: d
        Link detected: yes
# 
```

you should have at least Link detected: Yes.
you can set autonegotiation to yes with

```
# ethtool -s eth0 autoneg on 
```

Once link is established.

you can try and see if your router answers  DHCP requests.

```
# dhclient eth0
```

if that succeds you should get IP-addresses and your resolv.conf will be updates as well (DNS resolving) 

if it doesn't work - you'll need to guess an IP adress for yourself.
# ip neigh
will show your layer 2 neighbours, and probably show your default gateway, say 192.168.0.1

so you try and give yourself an ip address, 192.168.0.x where x is preferably a number not  already used on that network and 0<x<255. 

# ip addr add 192.168.0.x/24 dev eth0

(/24 indicates the subnet mask eg. 255.255.255.0)

then you need a default route 

# ip route add default via 192.168.0.1

and you should be running on ipadresses, to make DNS work
you need to know your DNS servers and add them in /etc/resolv.conf.

If it works, you need to make these settings permanent.
see /etc/network/interfaces
and man interfaces

---

### Post by JoeS on 2007-02-13
I got as far as :
```
# dhclient eth0
```

This put the following information in /etc/Resolv.conf:
> search cg.shawcable.net
nameserver 64.59.135.133
nameserver 64.59.135.135


and the following in /etc/Network/Interfaces:
> # Used by ifup(8) and ifdown(8). See the interfaces(5) manpage or
# /usr/share/doc/ifupdown/examples for more information.

iface lo inet loopback


iface eth0 inet dhcp

auto eth0


iface eth1 inet dhcp



auto eth1

I can connect to the internet now but I have to disconnect the ethernet cable when I boot up or I can't get a Desktop.  Then I need to use ```
dhclient eth0 
```again to connect to the internet.  The information is still in the above files, so I don't understand this.  I read ```
man interfaces
```, but didn't understand it that well.

---

