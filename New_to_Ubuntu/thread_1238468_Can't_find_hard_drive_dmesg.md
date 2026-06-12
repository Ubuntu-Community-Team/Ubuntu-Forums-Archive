---
title: "Can't find hard drive dmesg"
date: 2009-08-12
forum: New to Ubuntu
---

### Post by yogo on 2009-08-12
```
tu@ubuntu:~$ dmesg
[    0.000000] Using PowerMac machine description
[    0.000000] Total memory = 640MB; using 2048kB for hash table (at cfe00000)
[    0.000000] Linux version 2.6.28-6-powerpc (buildd@adare) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #20-Ubuntu Fri Apr 17 08:30:40 UTC 2009 (Ubuntu 2.6.28-6.20-powerpc)
[    0.000000] Found initrd at 0xc1a00000:0xc22a96e4
[    0.000000] Found UniNorth memory controller & host bridge @ 0xf8000000 revision: 0xc0
[    0.000000] Mapped at 0xff7c0000
[    0.000000] Found a Pangea mac-io controller, rev: 0, mapped at 0xff740000
[    0.000000] Processor NAP mode on idle enabled.
[    0.000000] PowerMac motherboard: iBook 2
[    0.000000] via-pmu: Server Mode is disabled
[    0.000000] PMU driver v2 initialized for Core99, firmware: 0c
[    0.000000] console [udbg0] enabled
[    0.000000] Found UniNorth PCI host bridge at 0x00000000f0000000. Firmware bus number: 0->0
[    0.000000] PCI host bridge /pci@f0000000  ranges:
[    0.000000]  MEM 0x00000000f1000000..0x00000000f1ffffff -> 0x00000000f1000000 
[    0.000000]   IO 0x00000000f0000000..0x00000000f07fffff -> 0x0000000000000000
[    0.000000]  MEM 0x0000000090000000..0x000000009fffffff -> 0x0000000090000000 
[    0.000000] Found UniNorth PCI host bridge at 0x00000000f2000000. Firmware bus number: 0->0
[    0.000000] PCI host bridge /pci@f2000000 (primary) ranges:
[    0.000000]  MEM 0x00000000f3000000..0x00000000f3ffffff -> 0x00000000f3000000 
[    0.000000]   IO 0x00000000f2000000..0x00000000f27fffff -> 0x0000000000000000
[    0.000000]  MEM 0x0000000080000000..0x000000008fffffff -> 0x0000000080000000 
[    0.000000] Found UniNorth PCI host bridge at 0x00000000f4000000. Firmware bus number: 0->0
[    0.000000] PCI host bridge /pci@f4000000  ranges:
[    0.000000]  MEM 0x00000000f5000000..0x00000000f5ffffff -> 0x00000000f5000000 
[    0.000000]   IO 0x00000000f4000000..0x00000000f47fffff -> 0x0000000000000000
[    0.000000] nvram: Checking bank 0...
[    0.000000] nvram: gen0=158, gen1=157
[    0.000000] nvram: Active bank is: 0
[    0.000000] nvram: OF partition at 0x410
[    0.000000] nvram: XP partition at 0xffffffff
[    0.000000] nvram: NR partition at 0xffffffff
[    0.000000] Top of RAM: 0x28000000, Total RAM: 0x28000000
[    0.000000] Memory hole size: 0MB
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00028000
[    0.000000]   Normal   0x00028000 -> 0x00028000
[    0.000000]   HighMem  0x00028000 -> 0x00028000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00028000
[    0.000000] On node 0 totalpages: 163840
[    0.000000] free_area_init_node: node 0, pgdat c045c5fc, node_mem_map c04d0000
[    0.000000]   DMA zone: 1280 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 162560 pages, LIFO batch:31
[    0.000000]   Normal zone: 0 pages used for memmap
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 162560
[    0.000000] Kernel command line: ro ramdisk_size=1048576 file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash -- 
[    0.000000] mpic: Setting up MPIC " MPIC 1   " version 1.2 at 80040000, max 4 CPUs
[    0.000000] mpic: ISU size: 64, shift: 6, mask: 3f
[    0.000000] mpic: Initializing for 64 sources
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] GMT Delta read from XPRAM: 0 minutes, DST: on
[    0.000000] time_init: decrementer frequency = 24.960000 MHz
[    0.000000] time_init: processor frequency   = 600.000000 MHz
[    0.000000] clocksource: timebase mult[a041a42] shift[22] registered
[    0.000000] clockevent: decrementer mult[663] shift[16] cpu[0]
[    0.000155] Console: colour dummy device 80x25
[    0.000165] console handover: boot [udbg0] -> real [tty0]
[    0.003533] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.008794] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.081242] High memory: 0k
[    0.081252] Memory: 632960k/655360k available (4296k kernel code, 21956k reserved, 176k data, 360k bss, 212k init)
[    0.081388] SLUB: Genslabs=12, HWalign=32, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.081409] Calibrating delay loop... 49.79 BogoMIPS (lpj=99584)
[    0.160534] Security Framework initialized
[    0.160571] SELinux:  Disabled at boot.
[    0.160674] AppArmor: AppArmor initialized
[    0.160697] Mount-cache hash table entries: 512
[    0.161334] device-tree: Duplicate name in /cpus/PowerPC,750@0, renamed to "l2-cache#1"
[    0.163838] Initializing cgroup subsys ns
[    0.163854] Initializing cgroup subsys freezer
[    0.164790] net_namespace: 752 bytes
[    0.164933] regulator: core version 0.5
[    0.165106] NET: Registered protocol family 16
[    0.165795] KeyWest i2c @0xf8001003 irq 42 /uni-n@f8000000/i2c@f8001000
[    0.165812]  channel 0 bus <multibus>
[    0.165817]  channel 1 bus <multibus>
[    0.165875] KeyWest i2c @0x80018000 irq 26 /pci@f2000000/mac-io@17/i2c@18000
[    0.165883]  channel 0 bus <multibus>
[    0.165909] PMU i2c /pci@f2000000/mac-io@17/via-pmu@16000
[    0.165915]  channel 1 bus <multibus>
[    0.165921]  channel 2 bus <multibus>
[    0.166148] PCI: Probing PCI hardware
[    0.166368] pci 0000:00:10.0: reg 10 32bit mmio: [0x94000000-0x97ffffff]
[    0.166381] pci 0000:00:10.0: reg 14 io port: [0x400-0x4ff]
[    0.166392] pci 0000:00:10.0: reg 18 32bit mmio: [0x90000000-0x90003fff]
[    0.166413] pci 0000:00:10.0: reg 30 32bit mmio: [0x90020000-0x9003ffff]
[    0.166432] pci 0000:00:10.0: supports D1 D2
[    0.166798] pci 0001:10:17.0: reg 10 32bit mmio: [0x80000000-0x8007ffff]
[    0.166866] pci 0001:10:18.0: reg 10 32bit mmio: [0x80081000-0x80081fff]
[    0.166903] pci 0001:10:18.0: supports D1 D2
[    0.166910] pci 0001:10:18.0: PME# supported from D1 D2 D3hot
[    0.166920] pci 0001:10:18.0: PME# disabled
[    0.166961] pci 0001:10:19.0: reg 10 32bit mmio: [0x80080000-0x80080fff]
[    0.166998] pci 0001:10:19.0: supports D1 D2
[    0.167004] pci 0001:10:19.0: PME# supported from D1 D2 D3hot
[    0.167011] pci 0001:10:19.0: PME# disabled
[    0.167465] pci 0002:20:0e.0: reg 10 32bit mmio: [0xf5000000-0xf5000fff]
[    0.167498] pci 0002:20:0e.0: supports D1 D2
[    0.167504] pci 0002:20:0e.0: PME# supported from D0 D1 D2 D3hot
[    0.167511] pci 0002:20:0e.0: PME# disabled
[    0.167538] pci 0002:20:0f.0: reg 10 32bit mmio: [0xf5200000-0xf53fffff]
[    0.167563] pci 0002:20:0f.0: reg 30 32bit mmio: [0xf5100000-0xf51fffff]
[    0.167908] bus: 00 index 0 io port: [0x802000-0x1001fff]
[    0.167916] bus: 00 index 1 mmio: [0xf1000000-0xf1ffffff]
[    0.167923] bus: 00 index 2 mmio: [0x90000000-0x9fffffff]
[    0.167930] bus: 10 index 0 io port: [0x00-0x7fffff]
[    0.167937] bus: 10 index 1 mmio: [0xf3000000-0xf3ffffff]
[    0.167944] bus: 10 index 2 mmio: [0x80000000-0x8fffffff]
[    0.167951] bus: 20 index 0 io port: [0xff7fe000-0xffffdfff]
[    0.167958] bus: 20 index 1 mmio: [0xf5000000-0xf5ffffff]
[    0.172088] usbcore: registered new interface driver usbfs
[    0.172145] usbcore: registered new interface driver hub
[    0.172255] usbcore: registered new device driver usb
[    0.184647] NET: Registered protocol family 8
[    0.184658] NET: Registered protocol family 20
[    0.184881] AppArmor: AppArmor Filesystem Enabled
[    0.185396] NET: Registered protocol family 2
[    0.188665] Switched to high resolution mode on CPU 0
[    0.220737] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.221856] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.228995] TCP bind hash table entries: 65536 (order: 6, 262144 bytes)
[    0.231104] TCP: Hash tables configured (established 131072 bind 65536)
[    0.231116] TCP reno registered
[    0.240902] NET: Registered protocol family 1
[    0.241416] checking if image is initramfs... it is
[    2.164035] Freeing initrd memory: 8869k freed
[    2.165921] Thermal assist unit using timers, shrink_timer: 500 jiffies
[    2.166275] Registering PowerMac CPU frequency driver
[    2.166282] Low: 400 Mhz, High: 600 Mhz, Boot: 600 Mhz
[    2.166763] audit: initializing netlink socket (disabled)
[    2.166829] type=2000 audit(197354194.164:1): initialized
[    2.185783] VFS: Disk quotas dquot_6.5.1
[    2.185861] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    2.186172] fuse init (API version 7.10)
[    2.186467] msgmni has been set to 1254
[    2.187137] alg: No test for stdrng (krng)
[    2.187187] io scheduler noop registered
[    2.187193] io scheduler anticipatory registered
[    2.187199] io scheduler deadline registered
[    2.187263] io scheduler cfq registered (default)
[    2.187747] aty128fb 0000:00:10.0: enabling device (0086 -> 0087)
[    2.188001] aty128fb 0000:00:10.0: Invalid ROM contents
[    2.188046] aty128fb: Invalid ROM signature 631c should  be 0xaa55
[    2.188060] aty128fb: BIOS not located, guessing timings.
[    2.188078] aty128fb: Rage128 LF M3 AGP [chip rev 0x0] 8M 128-bit SDR SGRAM (1:1)
[    2.188276] aty128: Backlight initialized (aty128bl0)
[    2.204745] Console: switching to colour frame buffer device 128x48
[    2.220335] fb0: ATY Rage128 frame buffer device on Rage128 LF M3 AGP
[    2.223918] Generic non-volatile memory driver v1.1
[    2.226346] brd: module loaded
[    2.226507] Fixed MDIO Bus: probed
[    2.226643] MacIO PCI driver attached to Pangea chipset
[    2.228389] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    2.228921] Uniform Multi-Platform E-IDE driver
[    2.229348] adb: starting probe task...
[    2.483786] adb devices: [2]: 2 c3 [3]: 3 1 [7]: 7 1f
[    2.490561] ADB keyboard at 2, handler 1
[    2.490593] Detected ADB keyboard, type ANSI.
[    2.490808] input: ADB keyboard as /devices/virtual/input/input1
[    2.500772] input: ADB Powerbook buttons as /devices/virtual/input/input2
[    2.527538] ADB mouse at 3, handler set to 4 (trackpad)
[    2.588085] input: ADB mouse as /devices/virtual/input/input3
[    2.588097] adb: finished probe task...
[    3.248639] ide-pmac: Found Apple KeyLargo ATA-4 controller (macio), bus ID 2, irq 19
[    3.248700] Probing IDE interface ide0...
[    4.600951] hdb: MATSHITADVD-ROM SR-8176, ATAPI CD/DVD-ROM drive
[    4.656741] hdb: host max PIO4 wanted PIO255(auto-tune) selected PIO4
[    4.656913] hdb: UDMA/33 mode selected
[    4.657147] ide0 at 0xe901e000-0xe901e070,0xe901e160 on irq 19
[    4.657541] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    4.657639] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    4.657725] ohci_hcd 0001:10:18.0: enabling device (0000 -> 0002)
[    4.657766] ohci_hcd 0001:10:18.0: OHCI Host Controller
[    4.658050] ohci_hcd 0001:10:18.0: new USB bus registered, assigned bus number 1
[    4.658112] ohci_hcd 0001:10:18.0: irq 27, io mem 0x80081000
[    4.732159] usb usb1: configuration #1 chosen from 1 choice
[    4.732254] hub 1-0:1.0: USB hub found
[    4.732315] hub 1-0:1.0: 2 ports detected
[    4.732710] ohci_hcd 0001:10:19.0: enabling device (0000 -> 0002)
[    4.732739] ohci_hcd 0001:10:19.0: OHCI Host Controller
[    4.732903] ohci_hcd 0001:10:19.0: new USB bus registered, assigned bus number 2
[    4.732958] ohci_hcd 0001:10:19.0: irq 28, io mem 0x80080000
[    4.808088] usb usb2: configuration #1 chosen from 1 choice
[    4.808201] hub 2-0:1.0: USB hub found
[    4.808249] hub 2-0:1.0: 2 ports detected
[    4.808539] uhci_hcd: USB Universal Host Controller Interface driver
[    4.808837] usbcore: registered new interface driver libusual
[    4.832744] mice: PS/2 mouse device common for all mice
[    4.832970] platform ppc-rtc.0: rtc core: registered ppc_md as rtc0
[    4.833076] PowerMac i2c bus pmu 2 registered
[    4.833133] PowerMac i2c bus pmu 1 registered
[    4.833187] PowerMac i2c bus mac-io 0 registered
[    4.833260] PowerMac i2c bus uni-n 1 registered
[    4.833330] PowerMac i2c bus uni-n 0 registered
[    4.833808] TCP cubic registered
[    4.834196] registered taskstats version 1
[    4.834610] input: PMU as /devices/virtual/input/input4
[    4.844745] Registered led device: pmu-front-led
[    4.844760] /build/buildd/linux-ports-2.6.28/drivers/rtc/hctosys.c: unable to open rtc device (y)
[    4.844805] Freeing unused kernel memory: 212k init
[    6.197604] ide-cd driver 5.00
[    6.199231] ide-cd: hdb: ATAPI 61X DVD-ROM drive, 256kB Cache
[    6.199254] Uniform CD-ROM driver Revision: 3.20
[    6.348884] sungem.c:v0.98 8/24/03 David S. Miller ([EMAIL="davem@redhat.com"]davem@redhat.com[/EMAIL])
[    6.413126] PHY ID: 4061e4, addr: 0
[    6.414146] eth0: Sun GEM (PCI) 10/100/1000BaseT Ethernet 00:03:93:58:2d:40
[    6.414155] eth0: Found BCM5221 PHY
[    6.470020] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[40]  MMIO=[f5000000-f50007ff]  Max Packet=[2048]  IR/IT contexts=[8/8]
[    7.765069] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[000393fffe582d40]
[   13.859655] ISO 9660 Extensions: RRIP_1991A
[   14.217685] aufs 20080922
[   14.255442] loop: module loaded
[   14.802404] squashfs: version 3.3 (2007/10/31) Phillip Lougher
[  148.368216] udev: starting version 141
[  148.747529] Linux agpgart interface v0.103
[  149.043321] agpgart-uninorth 0000:00:0b.0: Apple UniNorth/Pangea chipset
[  149.043744] agpgart-uninorth 0000:00:0b.0: configuring for size idx: 8
[  149.044280] agpgart-uninorth 0000:00:0b.0: AGP aperture is 32M @ 0x0
[  149.162481] pmac_zilog: 0.6 (Benjamin Herrenschmidt <[EMAIL="benh@kernel.crashing.org"]benh@kernel.crashing.org[/EMAIL]>)
[  149.182676] ttyPZ0 at MMIO 0x80013020 (irq = 22) is a Z85c30 ESCC - Serial port
[  149.183286] ttyPZ1 at MMIO 0x80013000 (irq = 23) is a Z85c30 ESCC - Serial port
[  149.790655] orinoco 0.15 (David Gibson <[EMAIL="hermes@gibson.dropbear.id.au"]hermes@gibson.dropbear.id.au[/EMAIL]>, Pavel Roskin <[EMAIL="proski@gnu.org"]proski@gnu.org[/EMAIL]>, et al)
[  150.024387] airport 0.15 (Benjamin Herrenschmidt <[EMAIL="benh@kernel.crashing.org"]benh@kernel.crashing.org[/EMAIL]>)
[  150.024500] airport: Physical address 80030000
[  151.356904] eth1: Hardware identity 0005:0001:0001:0002
[  151.357032] eth1: Station identity  001f:0001:0008:0028
[  151.357043] eth1: Firmware determined as Lucent/Agere 8.40
[  151.357060] eth1: Attempting to download firmware agere_sta_fw.bin
[  151.357083] hermes_dld: AUX enable returned 0
[  151.357827] hermes_dld: AUX disable returned 0
[  151.357834] hermes_dld: Actual PDA length 998, Max allowed 1000
[  151.357840] eth1: Read PDA returned 0
[  151.357851] airport 0.00030000:radio: firmware: requesting agere_sta_fw.bin
[  152.310204] eth1: Cannot find firmware agere_sta_fw.bin
[  152.310283] eth1: Hardware identity 0005:0001:0001:0002
[  152.310390] eth1: Station identity  001f:0001:0008:0028
[  152.310400] eth1: Firmware determined as Lucent/Agere 8.40
[  152.310407] eth1: Ad-hoc demo mode supported
[  152.310412] eth1: IEEE standard IBSS ad-hoc mode supported
[  152.310418] eth1: WEP supported, 104-bit key
[  152.310512] eth1: MAC address 00:30:65:06:1a:77
[  152.310598] eth1: Station name "HERMES I"
[  152.311143] eth1: ready
[  152.311918] airport: Card registered for interface eth1
[  153.470934] input: PowerMac Beep as /devices/pci0001:10/0001:10:17.0/input/input5
[  164.681333] NET: Registered protocol family 10
[  164.681868] lo: Disabled Privacy Extensions
[  173.077440] Bluetooth: Core ver 2.13
[  173.077784] NET: Registered protocol family 31
[  173.077792] Bluetooth: HCI device and connection manager initialized
[  173.077804] Bluetooth: HCI socket layer initialized
[  173.208018] Bluetooth: L2CAP ver 2.11
[  173.208041] Bluetooth: L2CAP socket layer initialized
[  173.583368] Bluetooth: RFCOMM socket layer initialized
[  173.583439] Bluetooth: RFCOMM TTY layer initialized
[  173.583446] Bluetooth: RFCOMM ver 1.10
[  173.780801] Bluetooth: SCO (Voice Link) ver 0.6
[  173.780817] Bluetooth: SCO socket layer initialized
[  174.344558] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[  174.344582] Bluetooth: BNEP filters: protocol multicast
[  174.611462] Bridge firewalling registered
[  185.888780] aty128fb 0000:00:10.0: Invalid ROM contents
[  186.863086] [drm] Initialized drm 1.1.0 20060810
[  186.928041] lp: driver loaded but no devices found
[  187.008349] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  187.023447] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  187.027970] [drm] Initialized r128 2.5.0 20030725 on minor 0
[  187.116439] agpgart-uninorth 0000:00:0b.0: putting AGP V2 device into 1x mode
[  187.116466] aty128fb 0000:00:10.0: putting AGP V2 device into 1x mode
[  187.177947] ppdev: user-space parallel port driver
[  187.195543] eth1: New link status: Connected (0001)
[  187.198330] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[  187.313114] NET: Registered protocol family 17
[  187.349167] eth1: New link status: Disconnected (0002)
[  187.606850] eth1: New link status: Connected (0001)
[  197.380643] eth1: no IPv6 routers present
[  200.338490] aty128fb 0000:00:10.0: Invalid ROM contents
[  200.496253] agpgart-uninorth 0000:00:0b.0: putting AGP V2 device into 1x mode
[  200.496281] aty128fb 0000:00:10.0: putting AGP V2 device into 1x mode
[  258.749545] ondemand governor failed, too long transition latency of HW, fallback to performance governor
[  980.412341] NTFS driver 2.1.29 [Flags: R/O MODULE].
[  981.736156] JFS: nTxBlock = 5019, nTxLock = 40155
[  982.468437] SGI XFS with ACLs, security attributes, realtime, large block numbers, no debug enabled
[  982.487308] SGI XFS Quota Management subsystem
[ 1491.609576] eth1: New link status: Disconnected (0002)
[ 1491.664954] eth1: Lucent/Agere firmware doesn't support manual roaming
[ 1492.929567] eth1: New link status: Connected (0001)
[ 8888.396653] usb 2-1: new full speed USB device using ohci_hcd and address 2
[ 8888.642245] usb 2-1: configuration #1 chosen from 1 choice
[ 8889.430823] SCSI subsystem initialized
[ 8889.757693] Initializing USB Mass Storage driver...
[ 8889.765132] scsi0 : SCSI emulation for USB Mass Storage devices
[ 8889.778078] usbcore: registered new interface driver usb-storage
[ 8889.778102] USB Mass Storage support registered.
[ 8889.778632] usb-storage: device found at 2
[ 8889.778642] usb-storage: waiting for device to settle before scanning
[ 8894.779164] usb-storage: device scan complete
[ 8894.783939] scsi 0:0:0:0: Direct-Access     Lexar    SAFE PSD         1.10 PQ: 0 ANSI: 1 CCS
[ 8894.899383] Driver 'sd' needs updating - please use bus_type methods
[ 8894.914807] sd 0:0:0:0: [sda] 2003904 512-byte hardware sectors: (1.02 GB/978 MiB)
[ 8894.921745] sd 0:0:0:0: [sda] Write Protect is off
[ 8894.921765] sd 0:0:0:0: [sda] Mode Sense: 23 00 00 00
[ 8894.921773] sd 0:0:0:0: [sda] Assuming drive cache: write through
[ 8894.953736] sd 0:0:0:0: [sda] 2003904 512-byte hardware sectors: (1.02 GB/978 MiB)
[ 8894.963841] sd 0:0:0:0: [sda] Write Protect is off
[ 8894.963866] sd 0:0:0:0: [sda] Mode Sense: 23 00 00 00
[ 8894.963874] sd 0:0:0:0: [sda] Assuming drive cache: write through
[ 8894.963899]  sda: sda1
[ 8894.981481] sd 0:0:0:0: [sda] Attached SCSI removable disk
[ 8895.084571] sd 0:0:0:0: Attached scsi generic sg0 type 0
ubuntu@ubuntu:~$ 

```

I do not think my hard drive is bad, just needs to be formatted so it can be read. 

What is needed to get hard drive to be recognized?

Thanks

---

### Post by Diabolis on 2009-08-13
what do you want to do?

this will show info about your drive:
```
sudo fdisk -l /dev/sda
```

---

### Post by Mark Phelps on 2009-08-14
Unless I read the log wrong (and maybe I did) ... it looks like you're running a Mac and you're trying to plugin an NTFS-formatted hard drive.  Can Macs do that?

---

