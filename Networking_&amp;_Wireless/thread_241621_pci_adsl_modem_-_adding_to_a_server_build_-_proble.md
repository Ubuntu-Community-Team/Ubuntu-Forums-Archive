---
title: "pci adsl modem - adding to a server build - problems!"
date: 2006-08-22
forum: Networking &amp; Wireless
---

### Post by BrowneR on 2006-08-22
Hi,
I have a dapper server setup on one of my machines and now wish to use it as a router/gateway for my adsl connection.

I have an old PCI adsl modem card sitting here so wanted to try and use that however i have encountered problems (as may be expected with such cards i guess).

From lspci i have identified the modem as **"ATM network controller: Efficient Networks, Inc SpeedStream (LANAI)" with ID "0000:00:11.0 0203: 111a:0005"**

Firstly I backed up my system then installed pppoe as i figured i will need that later (although i think my isp uses pppoa). I then removed one of my PCI network cards (eth0) to make room for the adsl modem.
I have no experience with adding new hardware to an already up and running linux system... so i just plugged it in. on boot i get the following messages (**copied from dmesg**): (device specific info in bold below)

```

[17179569.184000] Linux version 2.6.15-26-386 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Thu Aug 3 02:52:00 UTC 2006
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[17179569.184000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 0000000010000000 (usable)
[17179569.184000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 256MB LOWMEM available.
[17179569.184000] On node 0 totalpages: 65536
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   DMA32 zone: 0 pages, LIFO batch:0
[17179569.184000]   Normal zone: 61440 pages, LIFO batch:15
[17179569.184000]   HighMem zone: 0 pages, LIFO batch:0
[17179569.184000] DMI 2.0 present.
[17179569.184000] ACPI: Unable to locate RSDP
[17179569.184000] Allocating PCI resources starting at 20000000 (gap: 10000000:efff0000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hdb1 ro quiet
[17179569.184000] No local APIC present or hardware disabled
[17179569.184000] mapped APIC to ffffd000 (01201000)
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 2048 (order: 11, 32768 bytes)
[    0.000000] Detected 200.484 MHz processor.
[   42.042445] Using tsc for high-res timesource
[   42.043979] Console: colour VGA+ 80x25
[   42.048311] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   42.052825] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   42.129689] Memory: 249140k/262144k available (1976k kernel code, 12348k reserved, 606k data, 288k init, 0k highmem)
[   42.129741] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   42.209958] Calibrating delay using timer specific routine.. 401.53 BogoMIPS (lpj=803079)
[   42.210294] Security Framework v1.0.0 initialized
[   42.210357] SELinux:  Disabled at boot.
[   42.210493] Mount-cache hash table entries: 512
[   42.211513] CPU: After generic identify, caps: 008001bf 00000000 00000000 00000000 00000000 00000000 00000000
[   42.211591] CPU: After vendor identify, caps: 008001bf 00000000 00000000 00000000 00000000 00000000 00000000
[   42.211657] Intel Pentium with F0 0F bug - workaround enabled.
[   42.211692] CPU: After all inits, caps: 008001bf 00000000 00000000 00000000 00000000 00000000 00000000
[   42.211861] mtrr: v2.0 (20020519)
[   42.211881] CPU: Intel Pentium MMX stepping 03
[   42.211923] Checking 'hlt' instruction... OK.
[   42.227246] checking if image is initramfs... it is
[   50.045567] Freeing initrd memory: 6595k freed
[   50.128683] NET: Registered protocol family 16
[   50.129025] EISA bus registered
[   50.143561] PCI: PCI BIOS revision 2.10 entry at 0xfb450, last bus=0
[   50.143615] PCI: Using configuration type 1
[   50.147361] ACPI: Subsystem revision 20051216
[   50.147390] ACPI: Interpreter disabled.
[   50.147417] Linux Plug and Play Support v0.97 (c) Adam Belay
[   50.147499] pnp: PnP ACPI: disabled
[   50.147535] PnPBIOS: Scanning system for PnP BIOS support...
[   50.148035] PnPBIOS: Found PnP BIOS installation structure at 0xc00fc020
[   50.148083] PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0xc048, dseg 0xf0000
[   50.156497] PnPBIOS: 15 nodes reported by PnP BIOS; 15 recorded by driver
[   50.156662] PCI: Probing PCI hardware
[   50.156703] PCI: Probing PCI hardware (bus 00)
[   50.157635] PCI quirk: region 4000-403f claimed by PIIX4 ACPI
[   50.157675] PCI quirk: region 5000-500f claimed by PIIX4 SMB
[   50.157823] Boot video device is 0000:00:10.0
[   50.162327] PCI: Using IRQ router PIIX/ICH [8086/7110] at 0000:00:07.0
[   50.176905] pnp: 00:0a: ioport range 0x208-0x20f has been reserved
[   50.185702] audit: initializing netlink socket (disabled)
[   50.185789] audit(1156268606.953:1): initialized
[   50.186853] VFS: Disk quotas dquot_6.5.1
[   50.187051] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   50.187616] Initializing Cryptographic API
[   50.187660] io scheduler noop registered
[   50.187716] io scheduler anticipatory registered
[   50.187764] io scheduler deadline registered
[   50.187860] io scheduler cfq registered
[   50.187892] Limiting direct PCI/PCI transfers.
[   50.189645] isapnp: Scanning for PnP cards...
[   50.339202] pnp: SB audio device quirk - increasing port range
[   50.351437] isapnp: Card 'Creative ViBRA16X PnP'
[   50.351470] isapnp: Card '3Com 3C509B EtherLink III'
[   50.351498] isapnp: 2 Plug & Play cards detected total
[   50.625460] PNP: PS/2 Controller [PNP0303,PNP0f13] at 0x60,0x64 irq 1,12
[   50.628482] serio: i8042 AUX port at 0x60,0x64 irq 12
[   50.629118] serio: i8042 KBD port at 0x60,0x64 irq 1
[   50.629720] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[   50.630399] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   50.631184] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   50.662377] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   50.664021] 00:0e: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   50.670982] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   50.671635] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   50.671678] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   50.672916] mice: PS/2 mouse device common for all mice
[   50.674590] EISA: Probing bus 0 at eisa.0
[   50.674689] Cannot allocate resource for EISA slot 4
[   50.674722] Cannot allocate resource for EISA slot 5
[   50.674756] Cannot allocate resource for EISA slot 6
[   50.674812] EISA: Detected 0 cards.
[   50.675141] NET: Registered protocol family 2
[   50.700566] input: AT Translated Set 2 keyboard as /class/input/input0
[   50.708633] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   50.710170] TCP established hash table entries: 16384 (order: 4, 65536 bytes)
[   50.710964] TCP bind hash table entries: 16384 (order: 4, 65536 bytes)
[   50.711744] TCP: Hash tables configured (established 16384 bind 16384)
[   50.711777] TCP reno registered
[   50.712700] TCP bic registered
[   50.712766] NET: Registered protocol family 1
[   50.712829] NET: Registered protocol family 8
[   50.712854] NET: Registered protocol family 20
[   50.713026] Using IPI Shortcut mode
[   50.713382] Freeing unused kernel memory: 288k freed
[   51.264388] Capability LSM initialized
[   56.723366] PIIX4: IDE controller at PCI slot 0000:00:07.1
[   56.723458] PIIX4: chipset revision 1
[   56.723483] PIIX4: not 100% native mode: will probe irqs later
[   56.723544]     ide0: BM-DMA at 0xf000-0xf007, BIOS settings: hda:pio, hdb:pio
[   56.723642]     ide1: BM-DMA at 0xf008-0xf00f, BIOS settings: hdc:pio, hdd:pio
[   56.723725] Probing IDE interface ide0...
[   57.234888] hdb: ST317242A, ATA DISK drive
[   57.291308] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   57.292738] Probing IDE interface ide1...
[   58.026680] hdc: ATAPI 44X CDROM, ATAPI CD/DVD-ROM drive
[   58.362725] ide1 at 0x170-0x177,0x376 on irq 15
[   58.455301] hdb: max request size: 128KiB
[   58.455348] hdb: 33683328 sectors (17245 MB) w/512KiB Cache, CHS=33416/16/63, UDMA(33)
[   58.455402] hdb: cache flushes not supported
[   58.456685]  hdb: hdb1 hdb2 < hdb5 >
[   58.638891] hdc: ATAPI 48X CD-ROM drive, 128kB Cache, UDMA(33)
[   58.638962] Uniform CD-ROM driver Revision: 3.20
[   59.437424] usbcore: registered new driver usbfs
[   59.440479] usbcore: registered new driver hub
[   59.457987] USB Universal Host Controller Interface driver v2.3
[   59.461266] uhci_hcd 0000:00:07.2: UHCI Host Controller
[   59.464175] uhci_hcd 0000:00:07.2: new USB bus registered, assigned bus number 1
[   59.464250] uhci_hcd 0000:00:07.2: irq 11, io base 0x00006400
[   59.467645] hub 1-0:1.0: USB hub found
[   59.467789] hub 1-0:1.0: 2 ports detected
[   59.993797] Attempting manual resume
[   60.099318] EXT3-fs: INFO: recovery required on readonly filesystem.
[   60.099364] EXT3-fs: write access will be enabled during recovery.
[   61.259724] EXT3-fs: recovery complete.
[   61.259874] kjournald starting.  Commit interval 5 seconds
[   61.265922] EXT3-fs: mounted filesystem with ordered data mode.
[   82.590709] piix4_smbus 0000:00:07.3: Found 0000:00:07.3 device
[   83.793203] Linux Tulip driver version 1.1.13 (December 15, 2004)
[   83.793607] PCI: Found IRQ 15 for device 0000:00:13.0
[   83.794220] tulip0:  MII transceiver #1 config 1000 status 7809 advertising 01e1.
[   84.765210] eth0: Lite-On 82c168 PNIC rev 33 at 00016600, 00:A0:CC:3A:00:60, IRQ 11.
[B][   86.615328] lanai: In lanai_dev_open()
[   86.615411] PCI: setting IRQ 10 as level-triggered
[   86.615441] PCI: Assigned IRQ 10 for device 0000:00:11.0
[   86.615513] lanai: PCI says board_id=2, board_rev=1
[   86.615540] lanai: Found PCI board-id 2 -- not a Lanai 25.6
[   86.615628] lanai: lanai_start() failed, err=19
[   86.615674] lanai(itf 0): shutting down interface
[   86.615743] Unable to handle kernel paging request at virtual address 49544365
[   86.615853]  printing eip:
[   86.616175] d08db8c7
[   86.616192] *pde = 00000000
[   86.616254] Oops: 0002 [#1]
[   86.616302] PREEMPT 
[   86.616377] Modules linked in: lanai psmouse serio_raw tulip i2c_piix4 i2c_core evdev ext3 jbd ide_generic uhci_hcd usbcore ide_cd cdrom ide_disk piix generic processor fbcon tileblit font bitblit softcursor capability commoncap
[   86.617290] CPU:    0
[   86.617302] EIP:    0060:[<d08db8c7>]    Not tainted VLI
[   86.617323] EFLAGS: 00010246   (2.6.15-26-386) 
[   86.617534] EIP is at lanai_dev_close+0x27/0xa0 [lanai]
[   86.617621] eax: 49544341   ebx: cdb86400   ecx: c03444e0   edx: 00002573
[   86.617715] esi: cdb86400   edi: ffffffed   ebp: d08df488   esp: ccd2fea8
[   86.617799] ds: 007b   es: 007b   ss: 0068
[   86.617875] Process modprobe (pid: 2689, threadinfo=ccd2e000 task=cdbc8070)
[   86.617946] Stack: cdb865e8 d08dd388 00000000 cd60ccc0 c02e8f62 cd60ccc0 cd60ccc0 d08dc4ff 
[   86.618313]        cd60ccc0 d08dd838 00000013 ce999400 d08df460 d08df488 c01e6ffc ce999400 
[   86.618678]        d08df41c d08df41c d08df460 ce999400 c01e703f d08df460 ce999400 ce999400 
[   86.619045] Call Trace:
[   86.619158]  [<c02e8f62>] atm_dev_deregister+0x82/0xb0
[   86.619338]  [<d08dc4ff>] lanai_init_one+0x6f/0xc0 [lanai]
[   86.619519]  [<c01e6ffc>] __pci_device_probe+0x3c/0x60
[   86.619670]  [<c01e703f>] pci_device_probe+0x1f/0x40
[   86.619817]  [<c024457b>] driver_probe_device+0x3b/0xc0
[   86.619988]  [<c0244670>] __driver_attach+0x0/0x40
[   86.620130]  [<c02446ab>] __driver_attach+0x3b/0x40
[   86.620278]  [<c0243c58>] bus_for_each_dev+0x48/0x80
[   86.620439]  [<c02446c5>] driver_attach+0x15/0x20
[   86.620585]  [<c0244670>] __driver_attach+0x0/0x40
[   86.620727]  [<c02440f9>] bus_add_driver+0x69/0xc0
[   86.620879]  [<c01e728a>] __pci_register_driver+0x6a/0xa0
[   86.621026]  [<d0827060>] lanai_module_init+0x10/0x2f [lanai]
[   86.621193]  [<c013820f>] sys_init_module+0x9f/0x1d0
[   86.621346]  [<c01030a9>] syscall_call+0x7/0xb
[   86.621511] Code: 12 ff ff ff 53 8b 44 24 08 8b 58 10 8b 83 24 02 00 00 50 68 88 d3 8d d0 e8 27 0e 84 ef 8d 83 e8 01 00 00 50 e8 fb 99 84 ef 8b 03 <c7> 40 24 fe ff 03 00 8b 83 e4 00 00 00 53 8b 80 78 01 00 00 50 [/B]
[   86.623558]  <6>Real Time Clock Driver v1.12
[   87.255837] input: ImPS/2 Generic Wheel Mouse as /class/input/input1
[   88.958096] input: PC Speaker as /class/input/input2
[   90.249535] parport: PnPBIOS parport detected.
[   90.249715] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   91.275520] FDC 0 is a post-1991 82077
[   92.085299] pnp: Device 01:01.01 activated.
[   92.101504] gameport: NS558 PnP Gameport is pnp01:01.01/gameport0, io 0x201, speed 852kHz
[   94.180595] ts: Compaq touchscreen protocol output
[  253.904195] lp0: using parport0 (interrupt-driven).
[  254.602097] Adding 192772k swap on /dev/hdb5.  Priority:-1 extents:1 across:192772k
[  254.853638] EXT3 FS on hdb1, internal journal
[  256.069056] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[  256.069167] md: bitmap version 4.39
[  258.174666] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@redhat.com
[  265.106365] NET: Registered protocol family 17
[  267.682697] ip_tables: (C) 2000-2002 Netfilter core team
[  268.020851] Netfilter messages via NETLINK v0.30.
[  268.049501] ip_conntrack version 2.4 (2048 buckets, 16384 max) - 232 bytes per conntrack
[  270.304955] ClusterIP Version 0.8 loaded successfully
[  274.058772] ipt_recent v0.3.1: Stephen Frost <sfrost@snowman.net>.  http://snowman.net/projects/ipt_recent/
[  319.074742] NET: Registered protocol family 10
[  319.076273] lo: Disabled Privacy Extensions
[  319.078135] IPv6 over IPv4 tunneling driver
[  329.812127] eth1: no IPv6 routers present

```

what does all this mean? i presume there is an error when loading drivers/kernel modules for the device?

any suggestions how i can get this card to work? and how i will configure it when it is setup?


Thanks in advance.

---

### Post by BrowneR on 2006-08-23
shall i take the silence to mean its a lost cause? :p

---

### Post by pastorhudson on 2008-02-05
Did you ever get a solution for that speedstream card? I'm having the same exact problem! I can't find any info on it. Any help would be greatly appreciated.

ROn,

---

