---
title: "VGA Nvidia"
date: 2009-04-15
forum: New to Ubuntu
---

### Post by ddg on 2009-04-15
Hallo every body,

I need help.
I am running ubuntu 7.10 on my pc pentium III with 512 MB RAM and Nvidia Vanta (16MB) graphic controller.
The driver for Nvidia is restricted driver.
The problem is: The screen (Genome) keep rebooting every now and then. I feel whenever I browse and open my tabs, suddenly the screen goes to text mode and back to gnome and prompting me to login again.

Beside that, I used to use S3 trio graphic controller with 4 MB video ram. I don't feel this Nvidia is performing better then S3

Can somebody help me with some tips???
Regards,
ddg

---

### Post by northern lights on 2009-04-15
The nvidia Vanta is a 128bit graphics core, a downgraded version of the TNT chip (note: TNT One, not TNT II). It shouldn't perform much better than the S3 GX2 for instance.

Both cards are highly outdated and it's no surprise to me that you won't feel a difference.

My advice: Spend 20 bucks on say a Geforce 7Series with 128MB.


As far as the resets of your xserver and/or session. This problem should be unrelated to your graphics device and needs solving. Can you post the output of ```
dmesg
```right after a crash? Thanks.

---

### Post by ddg on 2009-04-15
Hi,
Thanks for the reply.
I did not get output dmseg. It says command not found.
I don't know whether I can use Geforce 7 series since my pc's agp is agp 2.
I need to check whether Geforce can work on my pc.

Rgds,
ddg

> **northern lights said:**
> The nvidia Vanta is a 128bit graphics core, a downgraded version of the TNT chip (note: TNT One, not TNT II). It shouldn't perform much better than the S3 GX2 for instance.

Both cards are highly outdated and it's no surprise to me that you won't feel a difference.

My advice: Spend 20 bucks on say a Geforce 7Series with 128MB.


As far as the resets of your xserver and/or session. This problem should be unrelated to your graphics device and needs solving. Can you post the output of ```
dmseg
```right after a crash? Thanks.

---

### Post by northern lights on 2009-04-15
> **ddg said:**
> Hi,
Thanks for the reply.
I did not get output dmseg. It says command not found.
My bad. Typo. Please run *dmesg* (as corrected above) directly after an Xserver / Desktop Environment / session reset.

> **ddg said:**
> I don't know whether I can use Geforce 7 series since my pc's agp is agp 2.
You won't be able to actually, since those are PCIE cards already. It's simply the cheapest decently modern graphics device out there still sold on retail, hence my choice. For your setup, you'd fare well with a 64MB 4Series GeForce. Check ebay, shouldn't cost the world.

Note: A new graphics card is not required to run Ubuntu smoothly. However, none of the eye-candy gimmicks and desktop effects will work well with either card. The S3 can't do it at all, the Vanta might, if driver supports glx - but it won't be pretty and soon be more of a nuisance than anything. So while the Vanta might be 12 to 24 months younger, in reality, both can do the simple desktop but not more. Neither can run a modern 3D game. Both run 2D chess well. In essence, as said, you won't "feel" the difference. Invest in the best card you find on ebay that requires no further changes and you will make out a difference. High-end games will still be out of the question for cpu reasons, though.

---

### Post by ddg on 2009-04-15
Hi Nothern light,

Here is the output. 
[    0.000000] Linux version 2.6.22-16-generic (buildd@rothera) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Thu Apr 2 01:27:50 GMT 2009 (Ubuntu 2.6.22-16.62-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001fffd000 (usable)
[    0.000000]  BIOS-e820: 000000001fffd000 - 000000001ffff000 (ACPI data)
[    0.000000]  BIOS-e820: 000000001ffff000 - 0000000020000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 511MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 131069) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   131069
[    0.000000]   HighMem    131069 ->   131069
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   131069
[    0.000000] On node 0 totalpages: 131069
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 991 pages used for memmap
[    0.000000]   Normal zone: 125982 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI 2.0 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F7B90 checksum 0
[    0.000000] ACPI: RSDP 000F7B90, 0014 (r0 ASUS  )
[    0.000000] ACPI: RSDT 1FFFD000, 002C (r1 ASUS   P2V-B    58582E31 ASUS 31303030)
[    0.000000] ACPI: FACP 1FFFD080, 0074 (r1 ASUS   P2V-B    58582E31 ASUS 31303030)
[    0.000000] ACPI: DSDT 1FFFD100, 1C0F (r1   ASUS P2V-B        1000 MSFT  1000001)
[    0.000000] ACPI: FACS 1FFFF000, 0040
[    0.000000] ACPI: BOOT 1FFFD040, 0028 (r1 ASUS   P2V-B    58582E31 ASUS 31303030)
[    0.000000] ACPI: BIOS age (1999) fails cutoff (2000), acpi=force is required to enable ACPI
[    0.000000] ACPI: Disabling ACPI support
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:dfff0000)
[    0.000000] Built 1 zonelists.  Total pages: 130046
[    0.000000] Kernel command line: root=UUID=8e202cee-9b1a-4787-b82a-46b7813acdbc ro quiet splash
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] mapped APIC to ffffd000 (0140c000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] Detected 601.424 MHz processor.
[   20.909590] Console: colour VGA+ 80x25
[   20.910667] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   20.911712] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   20.993873] Memory: 508300k/524276k available (2017k kernel code, 15432k reserved, 918k data, 364k init, 0k highmem)
[   20.993910] virtual kernel memory layout:
[   20.993915]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   20.993920]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   20.993925]     vmalloc : 0xe0800000 - 0xff7fe000   ( 495 MB)
[   20.993930]     lowmem  : 0xc0000000 - 0xdfffd000   ( 511 MB)
[   20.993934]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[   20.993939]       .data : 0xc02f8506 - 0xc03dde84   ( 918 kB)
[   20.993944]       .text : 0xc0100000 - 0xc02f8506   (2017 kB)
[   20.993956] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   20.994085] SLUB: Genslabs=22, HWalign=32, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   21.074091] Calibrating delay using timer specific routine.. 1203.78 BogoMIPS (lpj=2407573)
[   21.074183] Security Framework v1.0.0 initialized
[   21.074215] SELinux:  Disabled at boot.
[   21.074269] Mount-cache hash table entries: 512
[   21.074703] CPU: After generic identify, caps: 0387f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[   21.074742] CPU: L1 I cache: 16K, L1 D cache: 16K
[   21.074751] CPU: L2 cache: 512K
[   21.074761] CPU serial number disabled.
[   21.074770] CPU: After all inits, caps: 0383f9ff 00000000 00000000 00000040 00000000 00000000 00000000
[   21.074806] Compat vDSO mapped to ffffe000.
[   21.074853] Checking 'hlt' instruction... OK.
[   21.090410] SMP alternatives: switching to UP code
[   21.090940] Freeing SMP alternatives: 11k freed
[   21.091840] Early unpacking initramfs... done
[   22.237415] CPU0: Intel Pentium III (Katmai) stepping 03
[   22.237449] SMP motherboard not detected.
[   22.237460] Local APIC not detected. Using dummy APIC emulation.
[   22.237734] Brought up 1 CPUs
[   22.238403] Booting paravirtualized kernel on bare hardware
[   22.238634] Time: 16:17:47  Date: 03/15/109
[   22.238780] NET: Registered protocol family 16
[   22.239267] EISA bus registered
[   22.242165] PCI: PCI BIOS revision 2.10 entry at 0xf0560, last bus=1
[   22.242176] PCI: Using configuration type 1
[   22.242183] Setting up standard PCI resources
[   22.248662] ACPI: Interpreter disabled.
[   22.248680] Linux Plug and Play Support v0.97 (c) Adam Belay
[   22.248712] pnp: PnP ACPI: disabled
[   22.248728] PnPBIOS: Scanning system for PnP BIOS support...
[   22.249234] PnPBIOS: Found PnP BIOS installation structure at 0xc00fd010
[   22.249253] PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0xd040, dseg 0xf0000
[   22.253098] PnPBIOS: 15 nodes reported by PnP BIOS; 15 recorded by driver
[   22.253307] PCI: Probing PCI hardware
[   22.253352] PCI: Probing PCI hardware (bus 00)
[   22.253813] PCI: 0000:00:04.3: class 604 doesn't match header type 00. Ignoring class.
[   22.256574] PCI: Using IRQ router VIA [1106/0596] at 0000:00:04.0
[   22.256610] PCI: setting IRQ 11 as level-triggered
[   22.256620] PCI: Found IRQ 11 for device 0000:00:04.2
[   22.275147] PCI: BIOS reporting unknown device 00:22
[   22.275156] PCI: Device 0000:00:0b.1 not found by BIOS
[   22.280497] NET: Registered protocol family 8
[   22.280506] NET: Registered protocol family 20
[   22.280796] pnp: 00:06: iomem range 0x0-0x9ffff could not be reserved
[   22.280810] pnp: 00:06: iomem range 0x100000-0x1fffffff could not be reserved
[   22.280821] pnp: 00:06: iomem range 0xe8000-0xeffff has been reserved
[   22.280832] pnp: 00:06: iomem range 0xf0000-0xf3fff could not be reserved
[   22.280862] pnp: 00:0f: ioport range 0x290-0x297 has been reserved
[   22.280873] pnp: 00:0f: ioport range 0xe400-0xe47f has been reserved
[   22.280884] pnp: 00:0f: ioport range 0xe800-0xe83f has been reserved
[   22.281607] Time: tsc clocksource has been installed.
[   22.282340] PCI: Bridge: 0000:00:01.0
[   22.282349]   IO window: disabled.
[   22.282362]   MEM window: e0000000-e1efffff
[   22.282372]   PREFETCH window: e1f00000-e3ffffff
[   22.282400] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   22.282447] NET: Registered protocol family 2
[   22.317790] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   22.318010] TCP established hash table entries: 16384 (order: 5, 196608 bytes)
[   22.319212] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[   22.320105] TCP: Hash tables configured (established 16384 bind 16384)
[   22.320118] TCP reno registered
[   22.330187] checking if image is initramfs... it is
[   24.470092] Freeing initrd memory: 7056k freed
[   24.470826] Simple Boot Flag at 0x46 set to 0x1
[   24.471760] audit: initializing netlink socket (disabled)
[   24.471831] audit(1239812268.292:1): initialized
[   24.481618] VFS: Disk quotas dquot_6.5.1
[   24.481889] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   24.482566] io scheduler noop registered
[   24.482578] io scheduler anticipatory registered
[   24.482585] io scheduler deadline registered
[   24.482678] io scheduler cfq registered (default)
[   24.482743] PCI: VIA PCI bridge detected. Disabling DAC.
[   24.482754] Activating ISA DMA hang workarounds.
[   24.482856] Boot video device is 0000:01:00.0
[   24.483443] isapnp: Scanning for PnP cards...
[   24.836900] isapnp: No Plug & Play device found
[   24.973258] Real Time Clock Driver v1.12ac
[   24.973596] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   24.973799] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   24.974284] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   24.976232] 00:02: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   24.977047] 00:03: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   24.980862] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   24.981600] input: Macintosh mouse button emulation as /class/input/input0
[   24.981961] PNP: PS/2 Controller [PNP0303,PNP0f13] at 0x60,0x64 irq 1,12
[   24.985104] serio: i8042 KBD port at 0x60,0x64 irq 1
[   24.985124] serio: i8042 AUX port at 0x60,0x64 irq 12
[   24.985875] mice: PS/2 mouse device common for all mice
[   24.986371] EISA: Probing bus 0 at eisa.0
[   24.986438] EISA: Detected 0 cards.
[   24.986826] TCP cubic registered
[   24.986893] NET: Registered protocol family 1
[   24.986999] Using IPI No-Shortcut mode
[   24.987336]   Magic number: 5:530:287
[   24.987395]   hash matches device ttyz1
[   24.987646]   hash matches device tty20
[   24.989066] Freeing unused kernel memory: 364k freed
[   24.989184] Write protecting the kernel read-only data: 726k
[   25.052680] input: AT Translated Set 2 keyboard as /class/input/input1
[   26.772391] AppArmor: AppArmor initialized<5>audit(1239812270.292:2):  type=1505 info="AppArmor initialized" pid=1124
[   26.800745] fuse init (API version 7.8)
[   26.827107] Failure registering capabilities with primary security module.
[   26.907322] thermal: Unknown symbol acpi_processor_set_thermal_limit
[   28.919379] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   28.919404] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   28.922892] VP_IDE: IDE controller at PCI slot 0000:00:04.1
[   28.922938] VP_IDE: chipset revision 6
[   28.922947] VP_IDE: not 100% native mode: will probe irqs later
[   28.922975] VP_IDE: VIA vt82c596a (rev 09) IDE UDMA33 controller on pci0000:00:04.1
[   28.922996]     ide0: BM-DMA at 0xd800-0xd807, BIOS settings: hda:DMA, hdb:DMA
[   28.923029]     ide1: BM-DMA at 0xd808-0xd80f, BIOS settings: hdc:pio, hdd:DMA
[   28.923050] Probing IDE interface ide0...
[   28.974694] usbcore: registered new interface driver usbfs
[   28.974797] usbcore: registered new interface driver hub
[   28.974946] usbcore: registered new device driver usb
[   28.981004] USB Universal Host Controller Interface driver v3.0
[   29.064853] 8139too Fast Ethernet driver 0.9.28
[   29.464652] FDC 0 is a post-1991 82077
[   29.550765] hda: Maxtor 2F020L0, ATA DISK drive
[   29.998548] hdb: PIONEER DVD-RW DVR-112, ATAPI CD/DVD-ROM drive
[   30.055163] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   30.055437] Probing IDE interface ide1...
[   30.470418] hdc: ST320410A, ATA DISK drive
[   30.750213] hdd: Maxtor 2F020L0, ATA DISK drive
[   30.812201] ide1 at 0x170-0x177,0x376 on irq 15
[   30.859424] PCI: Found IRQ 11 for device 0000:00:04.2
[   30.859504] PCI: Setting latency timer of device 0000:00:04.2 to 64
[   30.859516] uhci_hcd 0000:00:04.2: UHCI Host Controller
[   30.860974] uhci_hcd 0000:00:04.2: new USB bus registered, assigned bus number 1
[   30.861040] uhci_hcd 0000:00:04.2: irq 11, io base 0x0000d400
[   30.862602] usb usb1: configuration #1 chosen from 1 choice
[   30.863195] hub 1-0:1.0: USB hub found
[   30.863228] hub 1-0:1.0: 2 ports detected
[   30.867070] SCSI subsystem initialized
[   30.914889] libata version 2.21 loaded.
[   30.967717] PCI: setting IRQ 10 as level-triggered
[   30.967736] PCI: Found IRQ 10 for device 0000:00:0b.0
[   30.967799] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[   30.967810] uhci_hcd 0000:00:0b.0: UHCI Host Controller
[   30.968399] uhci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 2
[   30.968456] uhci_hcd 0000:00:0b.0: irq 10, io base 0x0000b800
[   30.969922] usb usb2: configuration #1 chosen from 1 choice
[   30.970569] hub 2-0:1.0: USB hub found
[   30.970600] hub 2-0:1.0: 2 ports detected
[   31.075504] PCI: setting IRQ 9 as level-triggered
[   31.075520] PCI: Found IRQ 9 for device 0000:00:0b.1
[   31.075577] PCI: Setting latency timer of device 0000:00:0b.1 to 64
[   31.075587] uhci_hcd 0000:00:0b.1: UHCI Host Controller
[   31.076220] uhci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 3
[   31.076268] uhci_hcd 0000:00:0b.1: irq 5, io base 0x0000b400
[   31.077759] usb usb3: configuration #1 chosen from 1 choice
[   31.078452] hub 3-0:1.0: USB hub found
[   31.078482] hub 3-0:1.0: 2 ports detected
[   31.184030] PCI: Found IRQ 9 for device 0000:00:0a.0
[   31.184095] PCI: Setting latency timer of device 0000:00:0a.0 to 64
[   31.185197] eth0: RealTek RTL8139 at 0xe0870000, 00:c0:26:2f:aa:d6, IRQ 5
[   31.185207] eth0:  Identified 8139 chip type 'RTL-8139C'
[   31.201588] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[   31.203246] PCI: Found IRQ 11 for device 0000:00:0b.2
[   31.203271] PCI: Sharing IRQ 11 with 0000:00:04.2
[   31.203328] PCI: Setting latency timer of device 0000:00:0b.2 to 64
[   31.203340] ehci_hcd 0000:00:0b.2: EHCI Host Controller
[   31.204249] ehci_hcd 0000:00:0b.2: new USB bus registered, assigned bus number 4
[   31.204382] ehci_hcd 0000:00:0b.2: irq 9, io mem 0xde000000
[   31.204400] ehci_hcd 0000:00:0b.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   31.206151] usb usb4: configuration #1 chosen from 1 choice
[   31.206955] hub 4-0:1.0: USB hub found
[   31.206993] hub 4-0:1.0: 4 ports detected
[   31.367314] hda: max request size: 128KiB
[   31.439358] hda: 40718160 sectors (20847 MB) w/2048KiB Cache, CHS=40395/16/63, UDMA(33)
[   31.442497] hda: cache flushes supported
[   31.442692]  hda: hda1 hda2 < hda5 >
[   31.496122] hdc: max request size: 128KiB
[   31.524645] hdc: 39102336 sectors (20020 MB) w/2048KiB Cache, CHS=38792/16/63, UDMA(33)
[   31.524669] hdc: cache flushes not supported
[   31.524818]  hdc:<6>hdb: ATAPI 40X DVD-ROM DVD-R-RAM CD-R/RW drive, 2000kB Cache, UDMA(33)
[   31.527212] Uniform CD-ROM driver Revision: 3.20
[   31.552194]  hdc1
[   31.569983] hdd: max request size: 128KiB
[   31.570768] hdd: 40718160 sectors (20847 MB) w/2048KiB Cache, CHS=40395/16/63, UDMA(33)
[   31.570925] hdd: cache flushes supported
[   31.571074]  hdd: hdd1
[   32.067806] Attempting manual resume
[   32.067822] swsusp: Resume From Partition 3:5
[   32.067828] PM: Checking swsusp image.
[   32.069768] PM: Resume from disk failed.
[   32.187679] kjournald starting.  Commit interval 5 seconds
[   32.187730] EXT3-fs: mounted filesystem with ordered data mode.
[   32.321515] usb 2-1: new full speed USB device using uhci_hcd and address 2
[   32.545248] usb 2-1: configuration #1 chosen from 1 choice
[   50.660238] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   50.718429] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   52.192824] Linux agpgart interface v0.102 (c) Dave Jones
[   52.383299] agpgart: Detected VIA Apollo Pro 133 chipset
[   52.390408] agpgart: AGP aperture is 64M @ 0xe4000000
[   53.000340] input: PS/2 Logitech Mouse as /class/input/input2
[   53.003384] parport_pc 00:00: reported by Plug and Play BIOS
[   53.003460] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   54.283632] nvidia: module license 'NVIDIA' taints kernel.
[   54.311644] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-7185  Mon Apr  2 18:29:54 PDT 2007
[   55.551698] input: PC Speaker as /class/input/input3
[   56.294057] Linux video capture interface: v2.00
[   56.342025] pwc: Philips webcam module version 10.0.13 loaded.
[   56.342039] pwc: Supports Philips PCA645/646, PCVC675/680/690, PCVC720[40]/730/740/750 & PCVC830/840.
[   56.342049] pwc: Also supports the Askey VC010, various Logitech Quickcams, Samsung MPC-C10 and MPC-C30,
[   56.342059] pwc: the Creative WebCam 5 & Pro Ex, SOTEC Afina Eye and Visionite VCS-UC300 and VCS-UM100.
[   56.342219] pwc: Logitech QuickCam Zoom USB webcam detected.
[   56.342403] pwc: Registered as /dev/video0.
[   56.345243] usbcore: registered new interface driver Philips webcam
[   57.317048] PCI: Found IRQ 11 for device 0000:00:09.0
[   57.317079] PCI: Sharing IRQ 11 with 0000:00:04.2
[   57.317115] PCI: Setting latency timer of device 0000:00:09.0 to 64
[   57.455293] gameport: CS4281 Gameport is pci0000:00:09.0/gameport0, speed 2593kHz
[   57.507974] usbcore: registered new interface driver snd-usb-audio
[   58.150965] lp0: using parport0 (interrupt-driven).
[   58.286148] Adding 891568k swap on /dev/hda5.  Priority:-1 extents:1 across:891568k
[   58.848951] EXT3 FS on hda1, internal journal
[   62.087746] acpi_cpufreq: Unknown symbol acpi_processor_notify_smm
[   62.088078] acpi_cpufreq: Unknown symbol acpi_processor_unregister_performance
[   62.089019] acpi_cpufreq: Unknown symbol acpi_processor_preregister_performance
[   62.089499] acpi_cpufreq: Unknown symbol acpi_processor_register_performance
[   64.255353] Failure registering capabilities with primary security module.
[   65.392243] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   65.914475] ppdev: user-space parallel port driver
[   66.467261] audit(1239783511.453:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4460 profile="/usr/sbin/cupsd"
[   66.780204] apm: BIOS version 1.2 Flags 0x0b (Driver version 1.16ac)
[   82.804681] Bluetooth: Core ver 2.11
[   82.805137] NET: Registered protocol family 31
[   82.805149] Bluetooth: HCI device and connection manager initialized
[   82.805162] Bluetooth: HCI socket layer initialized
[   82.891339] Bluetooth: L2CAP ver 2.8
[   82.891357] Bluetooth: L2CAP socket layer initialized
[   83.065675] Bluetooth: RFCOMM socket layer initialized
[   83.065981] Bluetooth: RFCOMM TTY layer initialized
[   83.065993] Bluetooth: RFCOMM ver 1.8
[   86.368480] agpgart: Found an AGP 1.0 compliant device at 0000:00:00.0.
[   86.368549] agpgart: Putting AGP V2 device at 0000:00:00.0 into 2x mode
[   86.368597] agpgart: Putting AGP V2 device at 0000:01:00.0 into 2x mode
[   86.639142] agpgart: Found an AGP 1.0 compliant device at 0000:00:00.0.
[   86.639223] agpgart: Putting AGP V2 device at 0000:00:00.0 into 2x mode
[   86.639272] agpgart: Putting AGP V2 device at 0000:01:00.0 into 2x mode
[   88.099777] NET: Registered protocol family 17
[   91.258987] NET: Registered protocol family 10
[   91.259475] lo: Disabled Privacy Extensions
[  101.740951] eth0: no IPv6 routers present
[ 1319.277910] agpgart: Found an AGP 1.0 compliant device at 0000:00:00.0.
[ 1319.279076] agpgart: Putting AGP V2 device at 0000:00:00.0 into 2x mode
[ 1319.279709] agpgart: Putting AGP V2 device at 0000:01:00.0 into 2x mode
[ 1319.543383] agpgart: Found an AGP 1.0 compliant device at 0000:00:00.0.
[ 1319.544607] agpgart: Putting AGP V2 device at 0000:00:00.0 into 2x mode
[ 1319.545231] agpgart: Putting AGP V2 device at 0000:01:00.0 into 2x mode
[ 3125.868487] agpgart: Found an AGP 1.0 compliant device at 0000:00:00.0.
[ 3125.869672] agpgart: Putting AGP V2 device at 0000:00:00.0 into 2x mode
[ 3125.870333] agpgart: Putting AGP V2 device at 0000:01:00.0 into 2x mode
[ 3126.133671] agpgart: Found an AGP 1.0 compliant device at 0000:00:00.0.
[ 3126.134855] agpgart: Putting AGP V2 device at 0000:00:00.0 into 2x mode
[ 3126.135490] agpgart: Putting AGP V2 device at 0000:01:00.0 into 2x mode

Yes, you are right about nvidia vanta or s3 trio 3D/2x. I will look for 4 series GE Force.
Or may be, I have to say good bye to Pentium III.

Thanks and rgds,
ddg


> **northern lights said:**
> My bad. Typo. Please run *dmesg* (as corrected above) directly after an Xserver / Desktop Environment / session reset.


You won't be able to actually, since those are PCIE cards already. It's simply the cheapest decently modern graphics device out there still sold on retail, hence my choice. For your setup, you'd fare well with a 64MB 4Series GeForce. Check ebay, shouldn't cost the world.

.

---

### Post by LowSky on 2009-04-15
> **ddg said:**
> 

Yes, you are right about nvidia vanta or s3 trio 3D/2x. I will look for 4 series GE Force.
Or may be, I have to say good bye to Pentium III.

Thanks and rgds,
ddg

A new computer today cost a fraction of what they did 10 years ago. Today you can pick up a machine for under $400US (I think that's about 300 Euro)

---

### Post by bobmatino17 on 2009-04-15
I use an Nvidia GeForce4 MX 420, it uses AGP 4x, it has 64MB of ram, it runs fine with me.

---

### Post by ddg on 2009-04-15
Hi Low Sky,

Yes, a new pc will cost me about US$ 400 (in bali Indonesia).
I just don't feel like throwing this pentium III since it still running well.
May be I have to donate it.
Rgds,
ddg


> **LowSky said:**
> A new computer today cost a fraction of what they did 10 years ago. Today you can pick up a machine for under $400US (I think that's about 300 Euro)

---

### Post by ddg on 2009-04-15
Hi,

Can I put this GeForce 4 on my pentium III.?
Thanks,
ddg

> **bobmatino17 said:**
> I use an Nvidia GeForce4 MX 420, it uses AGP 4x, it has 64MB of ram, it runs fine with me.

---

### Post by The_Doc_tor on 2009-04-15
Lucky you,
I couldnt even get Ubunto to load onto my Pent III with 1Gig Ram it just stalls half way through the load process and does nothing.
Donate the Pent III to some Win XP user & buy a P4 Mobo & Processor on Ebay, prices are pretty good at the moment.
Hey they should start an Ubuntu Auction site called Ubay or Ubuction.

:roll: Sorry that was terrible I need more sleep obviously.

---

### Post by ddg on 2009-04-15
Hi,

Thanks, have a good sleep.
It is also my time.
Rgds,
ddg 

> **The_Doc_tor said:**
> Lucky you,
I couldnt even get Ubunto to load onto my Pent III with 1Gig Ram it just stalls half way through the load process and does nothing.
Donate the Pent III to some Win XP user & buy a P4 Mobo & Processor on Ebay, prices are pretty good at the moment.
Hey they should start an Ubuntu Auction site called Ubay or Ubuction.

:roll: Sorry that was terrible I need more sleep obviously.

---

