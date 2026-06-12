---
title: "feisty, no ip assigned via wired DHCP"
date: 2007-09-06
forum: Networking &amp; Wireless
---

### Post by chem132 on 2007-09-06
Having a problem getting DHCP on a fresh feisty install.  Tried to RTFM all the forum materials I could get my hands on.  Here's the list of experiments and particulars:

Installed 7.04 on a novell network running IPv4 (IPx), dual boot with XP.  Get IP on both OS'es (Compaq V2000 laptop - machine I teach with).

Install 7.04 on ten student lab computers (Dell OptiPlex GXi's, 400 - 500 MHz), no DHCP with onboard NIC.  Cards detected by install, no attachment to network
Tried to substitute a newer 10/100 card, no DHCP
Tried a static IP that was assigned by network administrator.  No DHCP
Forced the disable of IPv6 via modprobe.d, hosts, and Firefox settings.  Reboot to IPv4.  No DHCP
Power down and restart hub, DHCP, and fiber optic equipment.  No DHCP

Intalled and tried Fedora 6.  No DHCP
Intalled and tried Ubuntu 6.10, 5.10.  No DHCP
Installed and tried Suse 10.2, 9.3.  No DHCP
Installed and tried Vectorlinux (Slackware).  No DHCP
Installed Knoppix (KDE libs).  No DHCP

Installed Windows 98.  IP obtained through DHCP with both onboard NIC and the 10/100 card.

Does windows have the means to interpret Novell network architecture that Linux does not?  Is there a workaround?  Every "dead" cable will IP immediately with any version of Windows (98, 2000, XP) I try.

Are the OptiPlex machines just too old to work, even with legacy releases?  Should I try another type of ethernet card?  Since I have no IP, I would not be able to send output right away (would have to copy file to CD, then send through another machine as text - thx for patience, and sorry so long)

---

### Post by noob12 on 2007-09-07
When you boot in Ubuntu, what is the output of these commands

```


lspci -nn

sudo lshw -C network

sudo ethtool eth0

sudo ethtool eth1

dmesg

```


You could try this as well: shutdown; turn off the computer; unplug; wait ~15 seconds; plug in; boot.
That's not the solution, but it's diagnostic if it works.

---

### Post by chem132 on 2007-09-07
Here is the output, cabled to "dead" ethernet at one of the workstations.  They are all the same in terms of setup.  Have tried each one of the cards with no luck on any.

chemlab9@chemlab9-desktop:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge [8086:7190] (rev 03)
00:01.0 PCI bridge [0604]: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge [8086:7191] (rev 03)
00:07.0 ISA bridge [0601]: Intel Corporation 82371AB/EB/MB PIIX4 ISA [8086:7110] (rev 02)
00:07.1 IDE interface [0101]: Intel Corporation 82371AB/EB/MB PIIX4 IDE [8086:7111] (rev 01)
00:07.2 USB Controller [0c03]: Intel Corporation 82371AB/EB/MB PIIX4 USB [8086:7112] (rev 01)
00:07.3 Bridge [0680]: Intel Corporation 82371AB/EB/MB PIIX4 ACPI [8086:7113] (rev 02)
00:0d.0 USB Controller [0c03]: NEC Corporation USB [1033:0035] (rev 43)
00:0d.1 USB Controller [0c03]: NEC Corporation USB [1033:0035] (rev 43)
00:0d.2 USB Controller [0c03]: NEC Corporation USB 2.0 [1033:00e0] (rev 04)
00:0f.0 PCI bridge [0604]: Digital Equipment Corporation DECchip 21152 [1011:0024] (rev 03)
00:11.0 Ethernet controller [0200]: 3Com Corporation 3c905B 100BaseTX [Cyclone] [10b7:9055] (rev 24)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc 3D Rage Pro AGP 1X/2X [1002:4742] (rev 5c)
02:0a.0 Ethernet controller [0200]: D-Link System Inc RTL8139 Ethernet [1186:1300] (rev 10)
02:0b.0 Ethernet controller [0200]: ADMtek NC100 Network Everywhere Fast Ethernet 10/100 [1317:0985] (rev 11)

chemlab9@chemlab9-desktop:~$ sudo lshw -C network
Password:
  *-network:0             
       description: Ethernet interface
       product: RTL8139 Ethernet
       vendor: D-Link System Inc
       physical id: a
       bus info: pci@02:0a.0
       logical name: eth1
       version: 10
       serial: 00:11:95:62:0a:42
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s
       resources: ioport:dc00-dcff iomemory:fafffc00-fafffcff irq:11
  *-network:1
       description: Ethernet interface
       product: NC100 Network Everywhere Fast Ethernet 10/100
       vendor: ADMtek
       physical id: b
       bus info: pci@02:0b.0
       logical name: eth2
       version: 11
       serial: 00:0c:41:1e:d3:8c
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tulip driverversion=1.1.14 latency=64 maxlatency=128 mingnt=64 multicast=yes
       resources: ioport:d800-d8ff iomemory:fafff800-fafffbff irq:9
  *-network
       description: Ethernet interface
       product: 3c905B 100BaseTX [Cyclone]
       vendor: 3Com Corporation
       physical id: 11
       bus info: pci@00:11.0
       logical name: eth0
       version: 24
       serial: 00:c0:4f:23:e6:0e
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=3c59x duplex=full latency=64 link=no maxlatency=10 mingnt=10 multicast=yes port=MII speed=100MB/s
       resources: ioport:cc00-cc7f iomemory:ff002000-ff00207f irq:11

chemlab9@chemlab9-desktop:~$ sudo ethtool eth2
Settings for eth2:
No data available

chemlab9@chemlab9-desktop:~$ sudo ethtool eth0
Settings for eth0:
        Supported ports: [ TP MII ]
        Supported link modes:   10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
        Advertised auto-negotiation: Yes
        Speed: 100Mb/s
        Duplex: Full
        Port: MII
        PHYAD: 24
        Transceiver: internal
        Auto-negotiation: on
        Current message level: 0x00000001 (1)
        Link detected: no

chemlab9@chemlab9-desktop:~$ sudo ethtool eth1
Settings for eth1:
        Supported ports: [ TP MII ]
        Supported link modes:   10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
        Advertised auto-negotiation: Yes
        Speed: 10Mb/s
        Duplex: Half
        Port: MII
        PHYAD: 32
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: pumbg
        Wake-on: d
        Current message level: 0x00000007 (7)
        Link detected: no

chemlab9@chemlab9-desktop:~$ sudo ethtool eth2
Settings for eth2:
No data available

chemlab9@chemlab9-desktop:~$ dmesg
[    0.000000] Linux version 2.6.20-15-generic (root@palmer) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Apr 15 07:36:31 UTC 2007 (Ubuntu 2.6.20-15.27-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 00000000000a0000 end: 00000000000a0000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 00000000000f0000 size: 0000000000010000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000000ff00000 end: 0000000010000000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 00000000ffe00000 size: 0000000000200000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 00000000000a0000 (usable)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000010000000 (usable)
[    0.000000]  BIOS-e820: 00000000ffe00000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 256MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 65536) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->    65536
[    0.000000]   HighMem     65536 ->    65536
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->    65536
[    0.000000] On node 0 totalpages: 65536
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 480 pages used for memmap
[    0.000000]   Normal zone: 60960 pages, LIFO batch:15
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI 2.2 present.
[    0.000000] ACPI: RSDP (v000 DELL                                  ) @ 0x000fdf50
[    0.000000]   >>> ERROR: Invalid checksum
[    0.000000] Allocating PCI resources starting at 20000000 (gap: 10000000:efe00000)
[    0.000000] Detected 498.779 MHz processor.
[   28.177127] Built 1 zonelists.  Total pages: 65024
[   28.177140] Kernel command line: root=UUID=afad0ab3-3437-4df3-bc6f-e5430424398c ro quiet splash
[   28.177916] Local APIC disabled by BIOS -- you can enable it with "lapic"
[   28.177956] mapped APIC to ffffd000 (0120a000)
[   28.177971] Enabling fast FPU save and restore... done.
[   28.177981] Enabling unmasked SIMD FPU exception support... done.
[   28.178021] Initializing CPU#0
[   28.178158] PID hash table entries: 1024 (order: 10, 4096 bytes)
[   28.179817] Console: colour VGA+ 80x25
[   28.180483] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
[   28.181049] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
[   28.213909] Memory: 248640k/262144k available (1992k kernel code, 12964k reserved, 893k data, 328k init, 0k highmem)
[   28.213953] virtual kernel memory layout:
[   28.213958]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   28.213964]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   28.213970]     vmalloc : 0xd0800000 - 0xff7fe000   ( 751 MB)
[   28.213976]     lowmem  : 0xc0000000 - 0xd0000000   ( 256 MB)
[   28.213981]       .init : 0xc03d7000 - 0xc0429000   ( 328 kB)
[   28.213987]       .data : 0xc02f2264 - 0xc03d16d4   ( 893 kB)
[   28.213993]       .text : 0xc0100000 - 0xc02f2264   (1992 kB)
[   28.214007] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   28.294163] Calibrating delay using timer specific routine.. 998.59 BogoMIPS (lpj=1997188)
[   28.294328] Security Framework v1.0.0 initialized
[   28.294357] SELinux:  Disabled at boot.
[   28.294427] Mount-cache hash table entries: 512
[   28.294934] CPU: After generic identify, caps: 0383f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[   28.294976] CPU: L1 I cache: 16K, L1 D cache: 16K
[   28.294987] CPU: L2 cache: 512K
[   28.294998] CPU: After all inits, caps: 0383f9ff 00000000 00000000 00000040 00000000 00000000 00000000
[   28.295039] Compat vDSO mapped to ffffe000.
[   28.295067] Remapping vsyscall page to ffffe000
[   28.295100] Checking 'hlt' instruction... OK.
[   28.310471] SMP alternatives: switching to UP code
[   28.311040] Freeing SMP alternatives: 11k freed
[   28.311710] Early unpacking initramfs... done
[   29.603425] CPU0: Intel Pentium III (Katmai) stepping 03
[   29.603449] SMP motherboard not detected.
[   29.603458] Local APIC not detected. Using dummy APIC emulation.
[   29.603644] Brought up 1 CPUs
[   29.604605] Booting paravirtualized kernel on bare hardware
[   29.604820] Time: 12:13:36  Date: 07/24/107
[   29.604939] NET: Registered protocol family 16
[   29.605320] EISA bus registered
[   29.635842] PCI: PCI BIOS revision 2.10 entry at 0xfcaee, last bus=2
[   29.635853] PCI: Using configuration type 1
[   29.635861] Setting up standard PCI resources
[   29.639825] ACPI: Interpreter disabled.
[   29.639841] Linux Plug and Play Support v0.97 (c) Adam Belay
[   29.639881] pnp: PnP ACPI: disabled
[   29.639894] PnPBIOS: Scanning system for PnP BIOS support...
[   29.640004] PnPBIOS: Found PnP BIOS installation structure at 0xc00fe2d0
[   29.640018] PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0xe2f4, dseg 0x40
[   29.643127] PnPBIOS: 14 nodes reported by PnP BIOS; 14 recorded by driver
[   29.643357] PCI: Probing PCI hardware
[   29.643386] PCI: Probing PCI hardware (bus 00)
[   29.643876] * Found PM-Timer Bug on the chipset. Due to workarounds for a bug,
[   29.643884] * this clock source is slow. Consider trying other clock sources
[   29.643947] PCI quirk: region 0800-083f claimed by PIIX4 ACPI
[   29.643959] PCI quirk: region 0850-085f claimed by PIIX4 SMB
[   29.644528] Boot video device is 0000:01:00.0
[   29.647875] PCI: Using IRQ router PIIX/ICH [8086/7110] at 0000:00:07.0
[   29.654587] NET: Registered protocol family 8
[   29.654597] NET: Registered protocol family 20
[   29.654817] pnp: 00:00: ioport range 0x800-0x83f has been reserved
[   29.654831] pnp: 00:00: ioport range 0x850-0x85f has been reserved
[   29.656346] PCI: Bridge: 0000:00:01.0
[   29.656359]   IO window: e000-efff
[   29.656372]   MEM window: fc000000-feffffff
[   29.656384]   PREFETCH window: f6000000-f6ffffff
[   29.656396] PCI: Bridge: 0000:00:0f.0
[   29.656406]   IO window: d000-dfff
[   29.656418]   MEM window: fa000000-fbffffff
[   29.656429]   PREFETCH window: f5000000-f5ffffff
[   29.656534] NET: Registered protocol family 2
[   29.690433] IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
[   29.690755] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
[   29.691016] TCP bind hash table entries: 4096 (order: 3, 32768 bytes)
[   29.691155] TCP: Hash tables configured (established 8192 bind 4096)
[   29.691166] TCP reno registered
[   29.702598] checking if image is initramfs... it is
[   32.166564] Freeing initrd memory: 7013k freed
[   32.167994] audit: initializing netlink socket (disabled)
[   32.168041] audit(1187957618.172:1): initialized
[   32.168556] VFS: Disk quotas dquot_6.5.1
[   32.168633] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   32.168849] io scheduler noop registered
[   32.168862] io scheduler anticipatory registered
[   32.168871] io scheduler deadline registered
[   32.168920] io scheduler cfq registered (default)
[   32.168948] Limiting direct PCI/PCI transfers.
[   32.169771] isapnp: Scanning for PnP cards...
[   32.272822] isapnp: Card 'CS4236B'
[   32.272833] isapnp: 1 Plug & Play card detected total
[   32.414956] Real Time Clock Driver v1.12ac
[   32.415284] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   32.415588] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   32.416058] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   32.417880] 00:01: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   32.418723] 00:02: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   32.420350] mice: PS/2 mouse device common for all mice
[   32.423305] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   32.423969] input: Macintosh mouse button emulation as /class/input/input0
[   32.424145] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   32.424163] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   32.424864] PNP: PS/2 Controller [PNP0303,PNP0f13] at 0x60,0x64 irq 1,12
[   32.427064] serio: i8042 KBD port at 0x60,0x64 irq 1
[   32.427083] serio: i8042 AUX port at 0x60,0x64 irq 12
[   32.427606] EISA: Probing bus 0 at eisa.0
[   32.427682] EISA: Detected 0 cards.
[   32.427980] TCP cubic registered
[   32.428012] NET: Registered protocol family 1
[   32.428085] Using IPI No-Shortcut mode
[   32.428183]   Magic number: 3:256:229
[   32.429702] Freeing unused kernel memory: 328k freed
[   32.430136] Time: tsc clocksource has been installed.
[   32.457619] input: AT Translated Set 2 keyboard as /class/input/input1
[   34.321530] Capability LSM initialized
[   34.526076] thermal: Unknown symbol acpi_processor_set_thermal_limit
[   36.363980] PIIX4: IDE controller at PCI slot 0000:00:07.1
[   36.364023] PIIX4: chipset revision 1
[   36.364032] PIIX4: not 100% native mode: will probe irqs later
[   36.364054]     ide0: BM-DMA at 0xffa0-0xffa7, BIOS settings: hda:DMA, hdb:pio
[   36.364085]     ide1: BM-DMA at 0xffa8-0xffaf, BIOS settings: hdc:DMA, hdd:pio
[   36.364110] Probing IDE interface ide0...
[   36.488748] usbcore: registered new interface driver usbfs
[   36.488844] usbcore: registered new interface driver hub
[   36.488960] usbcore: registered new device driver usb
[   36.495900] USB Universal Host Controller Interface driver v3.0
[   36.545612] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   36.654265] hda: Maxtor 30768H1, ATA DISK drive
[   36.901035] 8139too Fast Ethernet driver 0.9.28
[   36.943443] Linux Tulip driver version 1.1.14 (December 15, 2004)
[   37.050794] Floppy drive(s): fd0 is 1.44M
[   37.223090] FDC 0 is a National Semiconductor PC87306
[   37.330437] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   37.330627] Probing IDE interface ide1...
[   38.066240] hdc: Hewlett-Packard CD-Writer Plus 9100, ATAPI CD/DVD-ROM drive
[   38.738624] ide1 at 0x170-0x177,0x376 on irq 15
[   38.742198] PCI: setting IRQ 11 as level-triggered
[   38.742211] PCI: Found IRQ 11 for device 0000:00:07.2
[   38.742243] PCI: Sharing IRQ 11 with 0000:00:11.0
[   38.742257] PCI: Sharing IRQ 11 with 0000:02:0a.0
[   38.742287] uhci_hcd 0000:00:07.2: UHCI Host Controller
[   38.743102] uhci_hcd 0000:00:07.2: new USB bus registered, assigned bus number 1
[   38.743157] uhci_hcd 0000:00:07.2: irq 11, io base 0x0000cce0
[   38.745051] usb usb1: configuration #1 chosen from 1 choice
[   38.745802] hub 1-0:1.0: USB hub found
[   38.745842] hub 1-0:1.0: 2 ports detected
[   38.848513] PCI: setting IRQ 10 as level-triggered
[   38.848529] PCI: Found IRQ 10 for device 0000:00:0d.0
[   38.848594] ohci_hcd 0000:00:0d.0: OHCI Host Controller
[   38.849100] ohci_hcd 0000:00:0d.0: new USB bus registered, assigned bus number 2
[   38.849151] ohci_hcd 0000:00:0d.0: irq 10, io mem 0xff001000
[   38.932352] usb usb2: configuration #1 chosen from 1 choice
[   38.932494] hub 2-0:1.0: USB hub found
[   38.932532] hub 2-0:1.0: 3 ports detected
[   39.034516] PCI: setting IRQ 9 as level-triggered
[   39.034531] PCI: Found IRQ 9 for device 0000:00:0d.1
[   39.034566] PCI: Sharing IRQ 9 with 0000:01:00.0
[   39.034580] PCI: Sharing IRQ 9 with 0000:02:0b.0
[   39.034615] ohci_hcd 0000:00:0d.1: OHCI Host Controller
[   39.034732] ohci_hcd 0000:00:0d.1: new USB bus registered, assigned bus number 3
[   39.034781] ohci_hcd 0000:00:0d.1: irq 9, io mem 0xff000000
[   39.120270] usb usb3: configuration #1 chosen from 1 choice
[   39.120388] hub 3-0:1.0: USB hub found
[   39.120434] hub 3-0:1.0: 2 ports detected
[   39.222753] PCI: Found IRQ 11 for device 0000:00:0d.2
[   39.222819] ehci_hcd 0000:00:0d.2: EHCI Host Controller
[   39.222947] ehci_hcd 0000:00:0d.2: new USB bus registered, assigned bus number 4
[   39.246139] ehci_hcd 0000:00:0d.2: irq 11, io mem 0xff002400
[   39.246162] ehci_hcd 0000:00:0d.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   39.246516] usb usb4: configuration #1 chosen from 1 choice
[   39.246643] hub 4-0:1.0: USB hub found
[   39.246683] hub 4-0:1.0: 5 ports detected
[   39.350799] PCI: Found IRQ 11 for device 0000:00:11.0
[   39.350825] PCI: Sharing IRQ 11 with 0000:00:07.2
[   39.350851] PCI: Sharing IRQ 11 with 0000:02:0a.0
[   39.350872] 3c59x: Donald Becker and others. [www.scyld.com/network/vortex.html](www.scyld.com/network/vortex.html)
[   39.350893] 0000:00:11.0: 3Com PCI 3c905B Cyclone 100baseTx at d0828000.
[   39.372687] PCI: Found IRQ 11 for device 0000:02:0a.0
[   39.372708] PCI: Sharing IRQ 11 with 0000:00:07.2
[   39.372728] PCI: Sharing IRQ 11 with 0000:00:11.0
[   39.373241] eth1: RealTek RTL8139 at 0xd082cc00, 00:11:95:62:0a:42, IRQ 11
[   39.373253] eth1:  Identified 8139 chip type 'RTL-8100B/8139D'
[   39.373970] PCI: Found IRQ 9 for device 0000:02:0b.0
[   39.373996] PCI: Sharing IRQ 9 with 0000:00:0d.1
[   39.374011] PCI: Sharing IRQ 9 with 0000:01:00.0
[   39.374827] tulip0:  MII transceiver #1 config 1000 status 7849 advertising 05e1.
[   39.383578] eth2: ADMtek Comet rev 17 at Port 0xd800, 00:0C:41:1E:D3:8C, IRQ 9.
[   39.433324] SCSI subsystem initialized
[   39.484413] libata version 2.20 loaded.
[   39.524665] hda: max request size: 128KiB
[   39.560190] hda: 15007104 sectors (7683 MB) w/512KiB Cache, CHS=14888/16/63, UDMA(33)
[   39.560217] hda: cache flushes not supported
[   39.560362]  hda: hda1 hda2 < hda5 >
[   39.835760] hdc: ATAPI 32X CD-ROM CD-R/RW drive, 4096kB Cache, UDMA(33)
[   39.835792] Uniform CD-ROM driver Revision: 3.20
[   40.810326] Attempting manual resume
[   40.810340] swsusp: Resume From Partition 3:5
[   40.810348] PM: Checking swsusp image.
[   40.844762] PM: Resume from disk failed.
[   40.994351] kjournald starting.  Commit interval 5 seconds
[   40.994394] EXT3-fs: mounted filesystem with ordered data mode.
[   67.296789] eth1: link down
[   67.378728] eth0:  setting full-duplex.
[   70.336482] NET: Registered protocol family 17
[   72.411955] Linux agpgart interface v0.102 (c) Dave Jones
[   72.431303] agpgart: Detected an Intel 440BX Chipset.
[   72.438940] agpgart: AGP aperture is 64M @ 0xf0000000
[   72.471600] piix4_smbus 0000:00:07.3: Found 0000:00:07.3 device
[   72.471630] piix4_smbus 0000:00:07.3: Host SMBus controller not enabled!
[   73.662122] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   74.032082] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   74.512590] parport: PnPBIOS parport detected.
[   74.512724] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,EPP,ECP]
[   74.625434] input: PS/2 Generic Mouse as /class/input/input2
[   75.444861] input: PC Speaker as /class/input/input3
[   75.698299] pnp: Device 01:01.01 activated.
[   75.715205] gameport: NS558 PnP Gameport is pnp01:01.01/gameport0, io 0x3a0, speed 718kHz
[   78.413287] pnp: Device 01:01.00 activated.
[   78.415968] pnp: Device 01:01.00 disabled.
[   78.415986] cs4232-pnpbios: probe of 01:01.00 failed with error -2
[   78.416127] CS4232 soundcard not found or device busy
[   78.855126] fuse init (API version 7.8)
[   78.917352] lp0: using parport0 (interrupt-driven).
[   79.022751] Adding 369452k swap on /dev/disk/by-uuid/f3a7d82e-49d7-4910-bc9c-2d5ea60b2d4b.  Priority:-1 extents:1 across:369452k
[   79.216256] EXT3 FS on hda1, internal journal
[   86.062509] acpi_cpufreq: Unknown symbol acpi_processor_notify_smm
[   86.062877] acpi_cpufreq: Unknown symbol acpi_processor_unregister_performance
[   86.063948] acpi_cpufreq: Unknown symbol acpi_processor_preregister_performance
[   86.064446] acpi_cpufreq: Unknown symbol acpi_processor_register_performance
[  100.099604] ppdev: user-space parallel port driver
[  106.147960] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[  110.311875] Bluetooth: Core ver 2.11
[  110.312064] NET: Registered protocol family 31
[  110.312074] Bluetooth: HCI device and connection manager initialized
[  110.312085] Bluetooth: HCI socket layer initialized
[  110.458457] Bluetooth: L2CAP ver 2.8
[  110.458474] Bluetooth: L2CAP socket layer initialized
[  111.378859] Bluetooth: RFCOMM socket layer initialized
[  111.378903] Bluetooth: RFCOMM TTY layer initialized
[  111.378912] Bluetooth: RFCOMM ver 1.8
[  112.758596] NET: Registered protocol family 10
[  112.758958] lo: Disabled Privacy Extensions
[  112.759389] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  112.759401] ADDRCONF(NETDEV_UP): eth2: link is not ready
[  123.689445] eth0: no IPv6 routers present
[  670.347243] 0000:02:0b.0: tulip_stop_rxtx() failed (CSR5 0xfc664010 CSR6 0xff972113)
[  670.347276] eth2: Setting full-duplex based on MII#1 link partner capability of 41e1.
[  670.347720] ADDRCONF(NETDEV_CHANGE): eth2: link becomes ready
[  689.717179] eth2: no IPv6 routers present
[598482.915560] ISO 9660 Extensions: Microsoft Joliet Level 3
[598483.071573] ISO 9660 Extensions: RRIP_1991A
[610367.121754] cdrom: This disc doesn't have any tracks I recognize!
[610532.410900] cdrom: This disc doesn't have any tracks I recognize!
[1034790.574302] ISO 9660 Extensions: Microsoft Joliet Level 3
[1034790.630257] ISO 9660 Extensions: RRIP_1991A
[1034879.173126] cdrom: This disc doesn't have any tracks I recognize!
[1109828.474121] eth2: no IPv6 routers present
[1200408.838281] 0000:02:0b.0: tulip_stop_rxtx() failed (CSR5 0xfc06c012 CSR6 0xff970111)
[1200412.811396] 0000:02:0b.0: tulip_stop_rxtx() failed (CSR5 0xfc664010 CSR6 0xff972113)
[1200412.811427] eth2: Setting full-duplex based on MII#1 link partner capability of 41e1.
[1200414.870916] 0000:02:0b.0: tulip_stop_rxtx() failed (CSR5 0xfc06c012 CSR6 0xff970111)
[1200415.107288] eth1: link down
[1200415.107589] ADDRCONF(NETDEV_UP): eth1: link is not ready
[1200417.927352] 0000:02:0b.0: tulip_stop_rxtx() failed (CSR5 0xfc664010 CSR6 0xff972113)
[1200417.927383] eth2: Setting full-duplex based on MII#1 link partner capability of 41e1.
[1200462.478702] hdc: tray open
[1200462.479679] end_request: I/O error, dev hdc, sector 0
[1200462.479700] Buffer I/O error on device hdc, logical block 0
[1200462.479718] Buffer I/O error on device hdc, logical block 1
[1200462.479731] Buffer I/O error on device hdc, logical block 2
[1200462.479743] Buffer I/O error on device hdc, logical block 3
[1200462.479755] Buffer I/O error on device hdc, logical block 4
[1200462.479766] Buffer I/O error on device hdc, logical block 5
[1200462.479777] Buffer I/O error on device hdc, logical block 6
[1200462.479788] Buffer I/O error on device hdc, logical block 7
[1200462.482856] hdc: tray open
[1200462.483687] end_request: I/O error, dev hdc, sector 0
[1200462.483706] Buffer I/O error on device hdc, logical block 0
[1200462.484223] hdc: tray open
[1200462.485052] end_request: I/O error, dev hdc, sector 4
[1200462.485070] Buffer I/O error on device hdc, logical block 1
[1200462.486175] hdc: tray open
[1200462.487005] end_request: I/O error, dev hdc, sector 0
[1200462.487529] hdc: tray open
[1200462.488356] end_request: I/O error, dev hdc, sector 4
[1200462.489181] hdc: tray open
[1200462.490009] end_request: I/O error, dev hdc, sector 0
[1200462.490533] hdc: tray open
[1200462.491360] end_request: I/O error, dev hdc, sector 4
[1200462.492181] hdc: tray open
[1200462.493009] end_request: I/O error, dev hdc, sector 0
[1200462.493545] hdc: tray open
[1200462.494374] end_request: I/O error, dev hdc, sector 4
[1200462.495211] hdc: tray open
[1200462.496040] end_request: I/O error, dev hdc, sector 0
[1200462.496565] hdc: tray open
[1200462.497394] end_request: I/O error, dev hdc, sector 4
chemlab9@chemlab9-desktop:~$ 

thanks, chem132

---

### Post by chem132 on 2007-09-07
sorry i forgot -- the power down didn't do anything to help the DHCP

chem132

---

### Post by noob12 on 2007-09-07
You seem to have three ethernet devices on that box, of which only one is actually plugged in: eth2 (ADMtek NC100 Network Everywhere Fast Ethernet 10/100). I'm not sure why ethtool is unable to get info on eth2, maybe **sudo mii-tool -v** will say something (?).  With things plugged in this way, provided you have eth2 configured for DHCP you should be able to run.  What does **cat /etc/network/interfaces** show?

You're unlikely to get anywhere with the other two cards until we can get the link state to be detected on the other two cards.  Do you actually have live cables plugged into all three cards, or are the other 2 cards unplugged?

---

### Post by chem132 on 2007-09-07
The three NIC's are all the variations that I tried in terms of network cards to get the thing to pull down IP.  Only eth2 is wired, the other two are just sitting there.  eth0 is the onboard NIC, eth1 and eth2 are PCI.  Will have to wait 'til Monday to check again (not at school).  OK for you to wait 'til then?

chem132

---

### Post by noob12 on 2007-09-09
Yeah.  I'm watching the thread.

---

### Post by chem132 on 2007-09-10
here is the output from your suggested commands:

chemlab9@chemlab9-desktop:~$ sudo mii-tool -v
eth0: no link
  product info: vendor 00:00:00, model 0 rev 0
  basic mode:   autonegotiation enabled
  basic status: no link
  capabilities: 100baseTx-FD 100baseTx-HD 10baseT-FD 10baseT-HD
  advertising:  100baseTx-FD 100baseTx-HD 10baseT-FD 10baseT-HD
eth1: no link
  product info: vendor 00:00:00, model 0 rev 0
  basic mode:   autonegotiation enabled
  basic status: no link
  capabilities: 100baseTx-FD 100baseTx-HD 10baseT-FD 10baseT-HD
  advertising:  100baseTx-FD 100baseTx-HD 10baseT-FD 10baseT-HD
eth2: negotiated 100baseTx-FD, link ok
  product info: vendor 00:07:49, model 1 rev 1
  basic mode:   autonegotiation enabled
  basic status: autonegotiation complete, link ok
  capabilities: 100baseTx-FD 100baseTx-HD 10baseT-FD 10baseT-HD
  advertising:  100baseTx-FD 100baseTx-HD 10baseT-FD 10baseT-HD flow-control
  link partner: 100baseTx-FD 100baseTx-HD 10baseT-FD 10baseT-HD
chemlab9@chemlab9-desktop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
address 10.0.9.201
netmask 255.255.248.0
gateway 10.0.8.1

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

---

### Post by noob12 on 2007-09-10
This looks fine for the situation that eth2 is plugged in and eth0, eth1 are not.

Can you post the output from the last two commands after you try this sequence?
```

sudo ifdown eth0
sudo ifdown eth1

sudo ifdown eth2
sudo ifup eth2

ifconfig eth2

grep dhclient /var/log/syslog | tail -25

```

Are these addresses from the static config on eth0 accurate for the net where you have eth2
plugged in?
> 
address 10.0.9.201
netmask 255.255.248.0
gateway 10.0.8.1


If not, do you know values we can use to test a manual configuration?  Is this something you have tried?

---

### Post by chem132 on 2007-09-12
The IP address on eth2 is an old static that I tried.  Didn't work.

---

### Post by chem132 on 2007-09-12
here is the output from the latest list of suggested commands:

chemlab9@chemlab9-desktop:~$ sudo ifdown eth0
Password:
RTNETLINK answers: No such process
There is already a pid file /var/run/dhclient.eth0.pid with pid 5045
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:c0:4f:23:e6:0e
Sending on   LPF/eth0/00:c0:4f:23:e6:0e
Sending on   Socket/fallback
chemlab9@chemlab9-desktop:~$ sudo ifdown eth1
RTNETLINK answers: No such process
There is already a pid file /var/run/dhclient.eth1.pid with pid 5019
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:11:95:62:0a:42
Sending on   LPF/eth1/00:11:95:62:0a:42
Sending on   Socket/fallback
chemlab9@chemlab9-desktop:~$ sudo ifdown eth2
RTNETLINK answers: No such process
There is already a pid file /var/run/dhclient.eth2.pid with pid 4936
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth2/00:0c:41:1e:d3:8c
Sending on   LPF/eth2/00:0c:41:1e:d3:8c
Sending on   Socket/fallback
DHCPRELEASE on eth2 to 10.0.8.11 port 67

chemlab9@chemlab9-desktop:~$ sudo ifup eth2
There is already a pid file /var/run/dhclient.eth2.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth2/00:0c:41:1e:d3:8c
Sending on   LPF/eth2/00:0c:41:1e:d3:8c
Sending on   Socket/fallback
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 9
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
chemlab9@chemlab9-desktop:~$ ifconfig eth2
eth2      Link encap:Ethernet  HWaddr 00:0C:41:1E:D3:8C  
          inet6 addr: fe80::20c:41ff:fe1e:d38c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1888098 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12672 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:253487744 (241.7 MiB)  TX bytes:1983166 (1.8 MiB)
          Interrupt:9 Base address:0xd800 

chemlab9@chemlab9-desktop:~$ grep dhclient /var/log/syslog | tail -25
Sep 12 08:02:35 chemlab9-desktop dhclient: DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 9
Sep 12 08:02:41 chemlab9-desktop dhclient: DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 4
Sep 12 08:02:44 chemlab9-desktop dhclient: No DHCPOFFERS received.
Sep 12 08:02:44 chemlab9-desktop dhclient: No working leases in persistent database - sleeping.
Sep 12 08:02:45 chemlab9-desktop dhclient: No DHCPOFFERS received.
chemlab9@chemlab9-desktop:~$ 

chem132

---

### Post by noob12 on 2007-09-12
Do you know the network, subnet mask and gateway address that you could use to test a manual configuration?   If you look at a windows box booting on the same net you should be able to get this information from the commands **ipconfig /all** and **route print**.    I know you tried the manual configuration, but we want to mimic what you're getting in windows and see if we can at least ping the router.  If you can't ping the router when manually configured, there's something more fundamentally wrong.

Also I think you said you disabled ipv6 at some point, but it looks like it is still enabled.  I don't think that is a factor here, but it is something I noticed.

---

### Post by chem132 on 2007-09-14
I got nothing by hard coding in the static.  XP pulls one down in like 5 seconds.  Aaaaaargh!

re:  IPv6; I was getting output from a different machine that day.

chem132

---

### Post by noob12 on 2007-09-14
If you mean you couldn't even ping the router with the static configuration, it sounds like there is something more fundamental wrong.

Is it the same behavior with the 8139 card (eth1) (when that is connected).  You can't ping the router even when manually configured?

I'm running out of ideas.

---

### Post by chem132 on 2007-09-15
No, I can't ping the server.  Interestingly enough, I am getting packets tallying up.  

Crazy idea, but would an ultra modern NIC work?  All of the machines that assign IP's, whether XP or Ubuntu, are newer machines.  Maybe the chip architecture in older NIC's don't understand the Novell IPv4 commands that our network uses.  Just a thought.  My laptop dual boots, and I get IP right away on both OS's.  Is it that the NIC gets the IP, and the OS picks it up?  If that were true, then both OS's just have to check in with the NIC to get the final hookup.  On the older desktops, with old NIC's, maybe the PCI cards don't know what to do and just sit there.  The old NIC's know a network is there, they just can't pull an IP off it.  Am I way off here?

chem132

---

### Post by gubemton on 2007-09-16
Hi. Got same problem on Centos 5 using HP Omnibook XE3 builtin NIC. It's based on same ADMTek Comet chip and I also get same tulip_stop_rxtx errors plus DHCP never gets reply from server. It does work if you add "noacpi" parameter to kernel commandline.

---

### Post by noob12 on 2007-09-16
Yes, it sounds more like either a timing or interrupt issue.  I would try booting with **pci=noacpi** or even **acpi=off**.

The theory about the old ethernet cards doesn't hold water.

When you say it is a Novell network, can you confirm you are running IP and not old IPX on the network?

If you can get the output of **ipconfig /all** and **route print** from one of your Windows boxes, it might help.

Before going to boot flags, you might want to try shutting down and removing the ADMTek card and then trying the 8139 card with a manually configured IP based on the information from a neighboring windows box.

---

### Post by chem132 on 2007-09-18
I passed the kernel commands pci=noacpi and acpi=off, and got no DHCP.  The Novell network runs IPx becasue we have a very old set of machines running on the network.  Its a public school.

---

### Post by noob12 on 2007-09-18
OK. That may be the problem.  

You should confirm.  On one of  your Windows machines, if you right click on your local network connection and look at the Connection Properties, the General tab will usually list the protocol "components in use" for the connection.  Can you say what you see there?

I'm not sure if there is support for Novell IPX available for Ubuntu, but I'm not an authority.

---

### Post by chem132 on 2007-09-20
It's listing IPX as the preferred network protocol, and the component entry says "naming".  Protocol component settings are "bindery", "NDS", and "SAP"

If the IPX is the weak spot, can I try SuSE or Fedora?  Or, is this going to be a chronic issue?  Can I try a legacy version of Ubuntu?

chem132

---

### Post by noob12 on 2007-09-20
OK.  That confirms it.

My suggestion (because this thread is titled wrong to attract answers on the underlying cause that we've found) is to start a new thread asking about Novell IPX support on Ubuntu or linux in general.  Also search for that.  

I will try to search as well for you and add pointers here to anything I find that I think you should look at.  But now we've jumped  from the normal IP networking and protocols realm (which I am more or less familiar with at my noob level) to a realm that I'm totally unfamiliar with, so I'm going to be pretty darn useless.

---

### Post by chem132 on 2007-09-20
thank you very much noob12.

---

### Post by noob12 on 2007-09-21
[http://www.faqs.org/docs/Linux-HOWTO/IPX-HOWTO.html](http://www.faqs.org/docs/Linux-HOWTO/IPX-HOWTO.html)

I think that
```

sudo aptitude install ipx

```
will get you the tools mentioned in this guide.  What I am not sure of is whether the Ubuntu kernel has the IPX support built-in or not.

Ask on the forum for more help.

---

