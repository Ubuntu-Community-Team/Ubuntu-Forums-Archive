---
title: "Almost have wireless with Netgear WG311 v3 card working except cannot connect."
date: 2008-07-29
forum: Networking &amp; Wireless
---

### Post by UserNeedsHelp on 2008-07-29
Hello,

Having successfully installed Ubuntu 8.04 on this old computer so that it can be used in replacement of a broken XP install (no disk to fix) I have one last problem.

This computer did not initially have a wireless card. A Netgear WG311 v3 was installed recently. 

I used this tutorial-

[https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3]("https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3")

To use ndiswrapper with the Windows 2000 driver. The computer now recognizes the device, and all the steps in that tutorial (including specific device information) came out exactly as described.

However, although "Wireless" now appears in the network menu, I cannot despite my best efforts get it to connect. If I use "roaming mode" the network appears (along with others) in the network manager in the top right of the screen. It prompts for password, but then displays bars that are usually 0%, occasionally jumping to 50% or 60% closely following initial connection, but never with any actual networking functionality that I can detect.

When not using roaming mode, I enter the ID, the password, and password type (WPA Personal) and use "Automatic Configuration" which results in "Changing Interface Connection"...  the network manager displays a small orange arrow in the top right (network disabled in text I believe) for a second, and then the computer reverts to a wired connection. Unplugging the ethernet results in no network.

The router is a Netgear WgR614 v7. The network is encrypted (and this cannot be changed) with WPA-PSK [TKIP] according to the router.

I really hope someone is able to point to toward a solution. I have limited active Ubuntu experience, but I've been following documentation since Dapper Drake so I consider myself quite competent... theoretically.

If anymore information if required I'd be happy to do my best to provide it.

---

### Post by pytheas22 on 2008-07-29
You could try using [wicd]("http://wicd.sourceforge.net/") to connect instead; you can install using the package from [here]("http://downloads.sourceforge.net/wicd/wicd_1.4.2-1-all.deb?modtime=1203246585&big_mirror=0").  If it's the case that Network Manager is doing something weird that's making the device fail to connect, wicd may have better luck.

If that doesn't help, please try connecting again.  Immediately after the connection fails, open up a terminal and type:
```

dmesg
ndiswrapper -l
```

and post the output here (it's going to be long, but that's ok) and hopefully it will provide a clue as to why it doesn't want to connect.

---

### Post by UserNeedsHelp on 2008-07-29
Erm, sorry. Need some guidance with both.

Downloading the .deb for wicd and double clicking it yields the error "conflicts with network-manager" in the install window. Is it necessary to uninstall network manager or otherwise disable it first? If so, how do I go about doing so? Or should it be installed some other way?

Secondly, do I enter both of those lines in a single terminal command, or one after the other? The former gives me an error of-

```
dmesg: invalid option -- l
Usage: dmesg [-c] [-n level] [-s bufsize]
```


Sorry about the confusion, practical terminal use I'm still not experienced with.

However, to save time here's the output individually after the network attempt fails.

```
amy@amy-desktop:~$ dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-19-generic (buildd@terranova) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Fri Jul 11 23:41:49 UTC 2008 (Ubuntu 2.6.24-19.36-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001fcf0000 (usable)
[    0.000000]  BIOS-e820: 000000001fcf0000 - 000000001fcfc000 (ACPI data)
[    0.000000]  BIOS-e820: 000000001fcfc000 - 000000001fd00000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000001fd00000 - 000000001fe80000 (usable)
[    0.000000]  BIOS-e820: 000000001fe80000 - 0000000020000000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb80000 - 00000000ffc00000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 510MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 130688) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   130688
[    0.000000]   HighMem    130688 ->   130688
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   130688
[    0.000000] On node 0 totalpages: 130688
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 989 pages used for memmap
[    0.000000]   Normal zone: 125603 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F6670 checksum 0
[    0.000000] ACPI: RSDP 000F6670, 0014 (r0 PTLTD )
[    0.000000] ACPI: RSDT 1FCF7082, 0030 (r1 PTLTD    RSDT    6040000  LTP        0)
[    0.000000] ACPI: FACP 1FCFBF0A, 0074 (r1 INTEL  Whitney   6040000 PTL     F4240)
[    0.000000] ACPI: DSDT 1FCF70B2, 4E58 (r1  INTEL  Whitney  6040000 MSFT  100000D)
[    0.000000] ACPI: FACS 1FCFCFC0, 0040
[    0.000000] ACPI: APIC 1FCFBF7E, 005A (r1 PTLTD  	 APIC    6040000  LTP        0)
[    0.000000] ACPI: BOOT 1FCFBFD8, 0028 (r1 PTLTD  $SBFTBL$  6040000  LTP        1)
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:11 APIC version 17
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:dfb80000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000e0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000e0000 - 0000000000100000
[    0.000000] swsusp: Registered nosave memory region: 000000001fcf0000 - 000000001fcfc000
[    0.000000] swsusp: Registered nosave memory region: 000000001fcfc000 - 000000001fd00000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 129667
[    0.000000] Kernel command line: root=UUID=6728fb9c-a191-427e-b2e7-693b7165cc11 ro quiet splash
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] Detected 1295.700 MHz processor.
[   15.122742] Console: colour VGA+ 80x25
[   15.122750] console [tty0] enabled
[   15.123968] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   15.125492] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   15.172953] Memory: 506116k/522752k available (2177k kernel code, 15948k reserved, 1006k data, 368k init, 0k highmem)
[   15.172969] virtual kernel memory layout:
[   15.172971]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   15.172973]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   15.172975]     vmalloc : 0xe0800000 - 0xff7fe000   ( 495 MB)
[   15.172978]     lowmem  : 0xc0000000 - 0xdfe80000   ( 510 MB)
[   15.172980]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
[   15.172982]       .data : 0xc0320474 - 0xc041bdc4   (1006 kB)
[   15.172984]       .text : 0xc0100000 - 0xc0320474   (2177 kB)
[   15.172990] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   15.173069] SLUB: Genslabs=11, HWalign=32, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   15.253072] Calibrating delay using timer specific routine.. 2593.53 BogoMIPS (lpj=5187072)
[   15.253130] Security Framework initialized
[   15.253148] SELinux:  Disabled at boot.
[   15.253178] AppArmor: AppArmor initialized
[   15.253186] Failure registering capabilities with primary security module.
[   15.253202] Mount-cache hash table entries: 512
[   15.253448] Initializing cgroup subsys ns
[   15.253456] Initializing cgroup subsys cpuacct
[   15.253475] CPU: After generic identify, caps: 0383fbff 00000000 00000000 00000000 00000000 00000000 00000000 00000000
[   15.253494] CPU: L1 I cache: 16K, L1 D cache: 16K
[   15.253499] CPU: L2 cache: 256K
[   15.253504] CPU: After all inits, caps: 0383fbff 00000000 00000000 00000040 00000000 00000000 00000000 00000000
[   15.253522] Compat vDSO mapped to ffffe000.
[   15.253547] Checking 'hlt' instruction... OK.
[   15.269614] SMP alternatives: switching to UP code
[   15.272226] Freeing SMP alternatives: 11k freed
[   15.272491] Early unpacking initramfs... done
[   15.903952] ACPI: Core revision 20070126
[   15.904239] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   16.001042] CPU0: Intel(R) Celeron(TM) CPU                1300MHz stepping 01
[   16.001102] Total of 1 processors activated (2593.53 BogoMIPS).
[   16.001257] ENABLING IO-APIC IRQs
[   16.001473] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   16.148910] Brought up 1 CPUs
[   16.148972] CPU0 attaching sched-domain:
[   16.148978]  domain 0: span 01
[   16.148982]   groups: 01
[   16.149475] net_namespace: 64 bytes
[   16.149495] Booting paravirtualized kernel on bare hardware
[   16.150482] Time: 20:31:05  Date: 07/29/08
[   16.150569] NET: Registered protocol family 16
[   16.151025] EISA bus registered
[   16.151072] ACPI: bus type pci registered
[   16.152079] PCI: PCI BIOS revision 2.10 entry at 0xfd9a8, last bus=1
[   16.152087] PCI: Using configuration type 1
[   16.152114] Setting up standard PCI resources
[   16.159555] ACPI: EC: Look up EC in DSDT
[   16.165067] ACPI: Interpreter enabled
[   16.165080] ACPI: (supports S0 S1 S3 S4 S5)
[   16.165105] ACPI: Using IOAPIC for interrupt routing
[   16.169629] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   16.169952] PCI quirk: region 1000-107f claimed by ICH4 ACPI/GPIO/TCO
[   16.169959] PCI quirk: region 1180-11bf claimed by ICH4 GPIO
[   16.170524] PCI: Transparent bridge - 0000:00:1e.0
[   16.170564] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   16.170907] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB_._PRT]
[   16.173239] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   16.173369] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 *9 10 11 12 14 15)
[   16.173487] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 *10 11 12 14 15)
[   16.173603] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[   16.173839] ACPI: Power Resource [FN01] (on)
[   16.173935] Linux Plug and Play Support v0.97 (c) Adam Belay
[   16.174010] pnp: PnP ACPI init
[   16.174032] ACPI: bus type pnp registered
[   16.199108] pnp: PnP ACPI: found 12 devices
[   16.199117] ACPI: ACPI bus type pnp unregistered
[   16.199126] PnPBIOS: Disabled by ACPI PNP
[   16.199601] PCI: Using ACPI for IRQ routing
[   16.199608] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   16.216781] NET: Registered protocol family 8
[   16.216786] NET: Registered protocol family 20
[   16.216958] AppArmor: AppArmor Filesystem Enabled
[   16.220762] Time: tsc clocksource has been installed.
[   16.228851] system 00:01: ioport range 0x1000-0x107f has been reserved
[   16.228857] system 00:01: ioport range 0x1180-0x11bf has been reserved
[   16.228863] system 00:01: ioport range 0x4d0-0x4d1 has been reserved
[   16.228867] system 00:01: ioport range 0x600-0x67f has been reserved
[   16.228872] system 00:01: ioport range 0xfe00-0xfe0f has been reserved
[   16.228880] system 00:01: iomem range 0xff800000-0xffffffff could not be reserved
[   16.228885] system 00:01: iomem range 0xfec00000-0xfec00fff has been reserved
[   16.228890] system 00:01: iomem range 0xfee00000-0xfee00fff has been reserved
[   16.228907] system 00:02: iomem range 0x0-0x9ffff could not be reserved
[   16.228912] system 00:02: iomem range 0xe0000-0xfffff could not be reserved
[   16.228917] system 00:02: iomem range 0x100000-0x1fffffff could not be reserved
[   16.259745] PCI: Bridge: 0000:00:1e.0
[   16.259753]   IO window: 2000-2fff
[   16.259762]   MEM window: d0100000-d1ffffff
[   16.259768]   PREFETCH window: e0000000-efffffff
[   16.259788] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   16.259822] NET: Registered protocol family 2
[   16.296922] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   16.297368] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[   16.297848] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[   16.298466] TCP: Hash tables configured (established 16384 bind 16384)
[   16.298474] TCP reno registered
[   16.309152] checking if image is initramfs...<7>Switched to high resolution mode on CPU 0
[   16.779269]  it is
[   17.451082] Freeing initrd memory: 7308k freed
[   17.451730] Simple Boot Flag at 0x35 set to 0x1
[   17.452843] audit: initializing netlink socket (disabled)
[   17.452881] audit(1217363465.084:1): initialized
[   17.457486] VFS: Disk quotas dquot_6.5.1
[   17.457702] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   17.458118] io scheduler noop registered
[   17.458128] io scheduler anticipatory registered
[   17.458131] io scheduler deadline registered
[   17.458166] io scheduler cfq registered (default)
[   17.458236] Boot video device is 0000:01:0b.0
[   17.458828] isapnp: Scanning for PnP cards...
[   17.812887] isapnp: No Plug & Play device found
[   17.884764] Real Time Clock Driver v1.12ac
[   17.884976] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled

[   17.885169] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   17.886530] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   17.888217] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   17.888374] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   17.888688] PNP: No PS/2 controller found. Probing ports directly.
[   17.891779] serio: i8042 KBD port at 0x60,0x64 irq 1
[   17.891791] serio: i8042 AUX port at 0x60,0x64 irq 12
[   17.892519] mice: PS/2 mouse device common for all mice
[   17.892777] EISA: Probing bus 0 at eisa.0
[   17.892792] Cannot allocate resource for EISA slot 1
[   17.892797] Cannot allocate resource for EISA slot 2
[   17.892825] EISA: Detected 0 cards.
[   17.892831] cpuidle: using governor ladder
[   17.892834] cpuidle: using governor menu
[   17.893190] NET: Registered protocol family 1
[   17.893262] Using IPI No-Shortcut mode
[   17.893340] registered taskstats version 1
[   17.893537]   Magic number: 0:785:549
[   17.893762]   hash matches device PNP0C0F:00
[   17.893773] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   17.893777] EDD information not available.
[   17.895166] Freeing unused kernel memory: 368k freed
[   19.389244] fuse init (API version 7.9)
[   19.432221] ACPI: Fan [FAN1] (on)
[   19.446599] ACPI: Invalid PBLK length [5]
[   19.451611] ACPI: Thermal Zone [THRM] (-273 C)
[   20.189199] SCSI subsystem initialized
[   20.235059] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[   20.235169] 8139cp 0000:01:06.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[   20.235177] 8139cp 0000:01:06.0: Try the "8139too" driver instead.
[   20.251061] 8139too Fast Ethernet driver 0.9.28
[   20.251206] PCI: Enabling device 0000:01:06.0 (0100 -> 0103)
[   20.251229] ACPI: PCI Interrupt 0000:01:06.0[A] -> GSI 19 (level, low) -> IRQ 16
[   20.252034] eth0: RealTek RTL8139 at 0x2000, 00:40:2b:1c:0b:49, IRQ 16
[   20.252038] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[   20.355188] usbcore: registered new interface driver usbfs
[   20.355241] usbcore: registered new interface driver hub
[   20.395016] usbcore: registered new device driver usb
[   20.435700] USB Universal Host Controller Interface driver v3.0
[   20.435887] ACPI: PCI Interrupt 0000:00:1f.2[D] -> GSI 19 (level, low) -> IRQ 16
[   20.435908] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   20.435916] uhci_hcd 0000:00:1f.2: UHCI Host Controller
[   20.436519] uhci_hcd 0000:00:1f.2: new USB bus registered, assigned bus number 1
[   20.436568] uhci_hcd 0000:00:1f.2: irq 16, io base 0x000010a0
[   20.436886] usb usb1: configuration #1 chosen from 1 choice
[   20.436932] hub 1-0:1.0: USB hub found
[   20.436945] hub 1-0:1.0: 2 ports detected
[   20.451006] libata version 3.00 loaded.
[   20.539868] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   20.590857] ata_piix 0000:00:1f.1: version 2.12
[   20.590980] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   20.610863] scsi0 : ata_piix
[   20.626827] scsi1 : ata_piix
[   20.628023] ata1: PATA max UDMA/66 cmd 0x1f0 ctl 0x3f6 bmdma 0x1080 irq 14
[   20.628029] ata2: PATA max UDMA/66 cmd 0x170 ctl 0x376 bmdma 0x1088 irq 15
[   20.786758] usb 1-2: new full speed USB device using uhci_hcd and address 2
[   20.791323] ata1.00: ATA-6: ST340810A, 3.39, max UDMA/100
[   20.791332] ata1.00: 78165360 sectors, multi 16: LBA 
[   20.807238] ata1.00: configured for UDMA/66
[   20.937615] usb 1-2: configuration #1 chosen from 1 choice
[   20.940516] hub 1-2:1.0: USB hub found
[   20.942422] hub 1-2:1.0: 4 ports detected
[   21.019044] Floppy drive(s): fd0 is 1.44M
[   21.038358] FDC 0 is a post-1991 82077
[   21.162954] ata2.00: ATAPI: Hewlett-Packard CD-Writer  cd16f, 1.1D, max UDMA/33
[   21.252233] usb 1-2.1: new low speed USB device using uhci_hcd and address 3
[   21.350881] ata2.00: configured for UDMA/33
[   21.351202] scsi 0:0:0:0: Direct-Access     ATA      ST340810A        3.39 PQ: 0 ANSI: 5
[   21.356160] scsi 1:0:0:0: CD-ROM            HP       CD-Writer cd16f  1.1D PQ: 0 ANSI: 5
[   21.383360] usb 1-2.1: configuration #1 chosen from 1 choice
[   21.592049] usb 1-2.2: new low speed USB device using uhci_hcd and address 4
[   21.712226] usb 1-2.2: configuration #1 chosen from 1 choice
[   22.396230] Driver 'sd' needs updating - please use bus_type methods
[   22.399636] sd 0:0:0:0: [sda] 78165360 512-byte hardware sectors (40021 MB)
[   22.399673] sd 0:0:0:0: [sda] Write Protect is off
[   22.399679] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   22.399715] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   22.399831] sd 0:0:0:0: [sda] 78165360 512-byte hardware sectors (40021 MB)
[   22.399850] sd 0:0:0:0: [sda] Write Protect is off
[   22.399855] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   22.399887] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   22.399897]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   22.422625]  sda1 sda2 < sda5 >
[   22.459211] sd 0:0:0:0: [sda] Attached SCSI disk
[   22.470023] sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[   22.470037] Uniform CD-ROM driver Revision: 3.20
[   22.470154] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   22.500614] usbcore: registered new interface driver hiddev
[   22.505664] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   22.505710] sr 1:0:0:0: Attached scsi generic sg1 type 5
[   22.515649] input: USB Optical Mouse as /devices/pci0000:00/0000:00:1f.2/usb1/1-2/1-2.1/1-2.1:1.0/input/input1
[   22.526149] input,hidraw0: USB HID v1.11 Mouse [USB Optical Mouse] on usb-0000:00:1f.2-2.1
[   22.539052] input: HID 1267:0103 as /devices/pci0000:00/0000:00:1f.2/usb1/1-2/1-2.2/1-2.2:1.0/input/input2
[   22.550113] input,hidraw1: USB HID v1.10 Keyboard [HID 1267:0103] on usb-0000:00:1f.2-2.2
[   22.570745] input: HID 1267:0103 as /devices/pci0000:00/0000:00:1f.2/usb1/1-2/1-2.2/1-2.2:1.1/input/input3
[   22.582147] input,hidraw2: USB HID v1.10 Device [HID 1267:0103] on usb-0000:00:1f.2-2.2
[   22.582195] usbcore: registered new interface driver usbhid
[   22.582204] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   23.270732] Attempting manual resume
[   23.270741] swsusp: Resume From Partition 8:5
[   23.270745] PM: Checking swsusp image.
[   23.271120] PM: Resume from disk failed.
[   23.345209] EXT3-fs: INFO: recovery required on readonly filesystem.
[   23.345224] EXT3-fs: write access will be enabled during recovery.
[   24.457296] kjournald starting.  Commit interval 5 seconds
[   24.457346] EXT3-fs: sda1: orphan cleanup on readonly fs
[   24.457361] ext3_orphan_cleanup: deleting unreferenced inode 1433616
[   24.457439] EXT3-fs: sda1: 1 orphan inode deleted
[   24.457443] EXT3-fs: recovery complete.
[   24.480892] EXT3-fs: mounted filesystem with ordered data mode.
[   38.123433] input: PC Speaker as /devices/platform/pcspkr/input/input4
[   38.438997] Linux agpgart interface v0.102
[   38.539745] intel_rng: FWH not detected
[   38.695328] agpgart: Detected an Intel i810 Chipset.
[   38.700320] agpgart: detected 4MB dedicated video ram.
[   38.725789] agpgart: AGP aperture is 64M @ 0xd4000000
[   38.786868] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   39.046827] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   39.114673] iTCO_vendor_support: vendor-support=0
[   39.170645] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   39.170848] iTCO_wdt: Found a ICH TCO device (Version=1, TCOBASE=0x1060)
[   39.170904] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   39.250744] i810_smbus 0000:00:01.0: i810/i815 i2c device found.
[   39.643081] input: Power Button (FF) as /devices/virtual/input/input5
[   39.654429] ACPI: Power Button (FF) [PWRF]
[   39.654776] input: Power Button (CM) as /devices/virtual/input/input6
[   39.670374] ACPI: Power Button (CM) [PWRB]
[   40.442731] parport_pc 00:08: reported by Plug and Play ACPI
[   40.442802] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   42.308535] nvidia: module license 'NVIDIA' taints kernel.
[   43.889562] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 17
[   43.889595] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   44.560262] intel8x0_measure_ac97_clock: measured 54545 usecs
[   44.560274] intel8x0: clocking to 48000
[   44.561620] ACPI: PCI Interrupt 0000:01:0b.0[A] -> GSI 18 (level, low) -> IRQ 18
[   44.562579] NVRM: loading NVIDIA UNIX x86 Kernel Module  169.12  Thu Feb 14 17:53:07 PST 2008
[   48.326679] lp0: using parport0 (interrupt-driven).
[   48.390046] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   48.481958] ndiswrapper: driver wg311v3 (NETGEAR,02/22/2005,3.1.1.7) loaded
[   48.482596] PCI: Enabling device 0000:01:0e.0 (0100 -> 0102)
[   48.482624] ACPI: PCI Interrupt 0000:01:0e.0[A] -> GSI 16 (level, low) -> IRQ 19
[   48.491100] ndiswrapper: using IRQ 19
[   48.775280] wlan0: ethernet device 00:1e:2a:b0:39:bf using NDIS driver: wg311v3, version: 0x3000036, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 11AB:1FAA.5.conf
[   48.775328] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   48.775465] usbcore: registered new interface driver ndiswrapper
[   48.913979] Adding 1502036k swap on /dev/sda5.  Priority:-1 extents:1 across:1502036k
[   49.433408] NET: Registered protocol family 17
[   49.712126] EXT3 FS on sda1, internal journal
[   51.456662] ip_tables: (C) 2000-2006 Netfilter Core Team
[   51.575236] nf_conntrack version 0.5.0 (8192 buckets, 32768 max)
[   53.638421] No dock devices found.
[   55.603724] apm: BIOS not found.
[   55.782367] ppdev: user-space parallel port driver
[   56.080782] audit(1217363504.979:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=4886 profile="/usr/sbin/cupsd" namespace="default"
[   57.713987] Bluetooth: Core ver 2.11
[   57.715549] NET: Registered protocol family 31
[   57.715560] Bluetooth: HCI device and connection manager initialized
[   57.715569] Bluetooth: HCI socket layer initialized
[   57.828971] Bluetooth: L2CAP ver 2.9
[   57.828984] Bluetooth: L2CAP socket layer initialized
[   57.925476] Bluetooth: RFCOMM socket layer initialized
[   57.925989] Bluetooth: RFCOMM TTY layer initialized
[   57.925997] Bluetooth: RFCOMM ver 1.8
[   59.312943] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   69.293379] NET: Registered protocol family 10
[   69.294723] lo: Disabled Privacy Extensions
[   79.641309] wlan0: no IPv6 routers present
[   79.881338] eth0: no IPv6 routers present
[  325.214175] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  345.877832] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  351.597345] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  356.586701] wlan0: no IPv6 routers present
[  369.540213] eth0: no IPv6 routers present
[ 1064.490610] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1073.059932] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1083.325777] wlan0: no IPv6 routers present
[ 1090.734065] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
```

```
amy@amy-desktop:~$ ndiswrapper -l
wg311v3 : driver installed
	device (11AB:1FAA) present

```

I notice at the bottom of the first output, wlan0 complains about no IPv6 routers present. I have a general understanding Ubuntu uses IPv6 by default and it sometimes causes problems... could that be the case here?

Anyways, if I used the command incorrectly or something else is needed or there's a solution please let me know.

---

### Post by pytheas22 on 2008-07-29
> Downloading the .deb for wicd and double clicking it yields the error "conflicts with network-manager" in the install window. Is it necessary to uninstall network manager or otherwise disable it first? If so, how do I go about doing so? Or should it be installed some other way?

Sorry, should have mentioned it before, but yes, you have to uninstall Network Manager in order to install wicd because they conflict with each other.  I thought the wicd installer would just uninstall NM automatically, but I guess not.  So run the command:
```

sudo apt-get remove network-manager
```

which will uninstall NM, and then try clicking the wicd installer again.  It should work then

(in case you ever want NM back, use the command: "sudo apt-get install network-manager-gnome" to reinstall it).

> 
Secondly, do I enter both of those lines in a single terminal command, or one after the other?

You got it right; they had to be entered as a single command.
> 
I notice at the bottom of the first output, wlan0 complains about no IPv6 routers present. I have a general understanding Ubuntu uses IPv6 by default and it sometimes causes problems... could that be the case here?

It's just saying this because it's noting that there are no IPv6 routers available (will there ever be?), but Ubuntu can still use IPv4 without a problem, so this is nothing to worry about.

As for the dmesg output, did you try connecting using Network Manager (the applet in the top-right corner of the screen that lists wireless networks when you click on it) or wicd before running dmesg?  If not, please do so and post dmesg again--in the output that you provided I don't see any information about trying to connect, which is what we need.

It could also be helpful if you post the output of:
```

iwlist scanning
```

and tell me the name of the network you want to connect to, so that I can give you commands to try to connect from the command-line.

But before anything else, try getting wicd installed and connecting with that, as hopefully that will be all it takes to solve the problem.

---

### Post by DavidTangye on 2008-08-10
> **UserNeedsHelp said:**
> 
```

[   48.491100] ndiswrapper: using IRQ 19
[   48.775280] wlan0: ethernet device 00:1e:2a:b0:39:bf using NDIS driver: wg311v3, version: 0x3000036, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 11AB:1FAA.5.conf
[   48.775328] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK

```

Where did you get the driver from? Can you please post the URL? The only drivers that I have found on the internet so far do not seem to support WPA, yet yours seems to.

---

### Post by pytheas22 on 2008-08-10
> Where did you get the driver from? Can you please post the URL? The only drivers that I have found on the internet so far do not seem to support WPA, yet yours seems to.

If you figure out the device ID of your wireless card, you can usually find good drivers by consulting the ndiswrapper site.  See the link in my signature about troubleshooting ndiswrapper for instructions on figuring out your card's device ID and finding good Windows drivers for it.  I would recommend some drivers, but there are apparently several different versions of the WG3111 and I'm not sure exactly which one you have.

It's better to search based on the device ID, because that's the only reliable unique identifier for each kind of wireless card.  Sometimes cards are sold under the same exact name but contain different chipsets, so your WG311 may be completely different than my WG311, as far as Linux is concerned.

Also, to the original poster in this thread: did you solve your problem?

---

