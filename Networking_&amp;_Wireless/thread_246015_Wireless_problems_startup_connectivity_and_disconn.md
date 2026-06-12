---
title: "Wireless problems: startup connectivity and disconnecting"
date: 2006-08-28
forum: Networking &amp; Wireless
---

### Post by jm2003uk on 2006-08-28
Hey!!

I've got my usb wireless dongle working nicely using ndiswrapper but there's a few problems which are getting quite frustrating now.

When i turn the computer on and login, the lights on the wireless device flash as if connected but kopete and firefox are both unable to connect. When i load up wireless assistant it also says i'm connected.....but i'm not. So i have to tell it to disconnect and then re-connect and then its fine...until...


Usually after the computers been on for a while the net will suddenly seem really slow and not responding.....which most likely means my wireless connection has died. But not only has it just disconnected....all the lights are out and the only way i can seem to get it to work again is to reboot the machine which throws me into a non-responsive CLI where i then have to hard-reboot out of and then go through the first problem again.

It's all doing my head in. Any idea what it could be and how to fix it?

---

### Post by gsdefender on 2006-08-28
Assuming that your dongle is detected as eth1, open /etc/network/interfaces and search for a

```
auto eth1
iface eth1 inet ...
[settings follow]

```

then make it as so

```
auto eth1
iface eth1 inet [either "static" or "dhcp"
**pre-up /sbin/iwpriv eth1 ndis_reset && /sbin/iwpriv eth1 usb_reset**
[settings follow]

```

then restart your computer, and see if the problem appears again.

I have a MiniPCI Broadcom 4306 on my AMD64-based laptop, and had what seems to be the same problem. IMRHO, some Windows drivers are so brain-damaged that they are good at storing connection settings somewhere into theirselves, but not so good at restoring them. I've thought about forcing a reset only after **months** of fiddling with /etc/network/interfaces. By invoking the private input/output controls ndis_reset and usb_reset, you are "cleaning" the card, thus preventing the mess to occur.


For what concerns your sudden connection lockups, they may well be misrouted IRQ troubles. Try posting your kernel debug message *after the error has occurred*, by simpling piping

```

dmesg >>$HOME/messages.txt

```

then pasting the content of your /home/[your user name]/messages.txt in a reply.

Hope this helps.

---

### Post by jm2003uk on 2006-09-01
Startup problem is gone now that i've changed it from static to dhcp. Haven't tried that extra code under dhcp yet (while it was set to static it just stayed on 'configuring network devices' during boot untill i hit Ctrl+c. 


Here's the dmesg output:

```

[17179569.184000] Linux version 2.6.15-26-386 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Thu Aug 3 02:52:00 UTC 2006
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[17179569.184000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000001fff0000 (usable)
[17179569.184000]  BIOS-e820: 000000001fff0000 - 000000001fff3000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 000000001fff3000 - 0000000020000000 (ACPI data)
[17179569.184000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 511MB LOWMEM available.
[17179569.184000] On node 0 totalpages: 131056
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   DMA32 zone: 0 pages, LIFO batch:0
[17179569.184000]   Normal zone: 126960 pages, LIFO batch:31
[17179569.184000]   HighMem zone: 0 pages, LIFO batch:0
[17179569.184000] DMI 2.2 present.
[17179569.184000] ACPI: RSDP (v000 KT600                                 ) @ 0x000f73c0
[17179569.184000] ACPI: RSDT (v001 KT600  AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x1fff3000
[17179569.184000] ACPI: FADT (v001 KT600  AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x1fff3040
[17179569.184000] ACPI: DSDT (v001 KT600  AWRDACPI 0x00001000 MSFT 0x0100000d) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x4008
[17179569.184000] Allocating PCI resources starting at 30000000 (gap: 20000000:dfff0000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hda1 ro quiet splash
[17179569.184000] Local APIC disabled by BIOS (or by default) -- you can enable it with "lapic"
[17179569.184000] mapped APIC to ffffd000 (01402000)
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 2048 (order: 11, 32768 bytes)
[17179569.184000] Detected 1917.648 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179573.348000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[17179573.348000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179573.364000] Memory: 508852k/524224k available (1976k kernel code, 14804k reserved, 606k data, 288k init, 0k highmem)
[17179573.364000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179573.444000] Calibrating delay using timer specific routine.. 3838.66 BogoMIPS (lpj=7677321)
[17179573.444000] Security Framework v1.0.0 initialized
[17179573.444000] SELinux:  Disabled at boot.
[17179573.444000] Mount-cache hash table entries: 512
[17179573.444000] CPU: After generic identify, caps: 0383f9ff c1c3f9ff 00000000 00000000 00000000 00000000 00000000
[17179573.444000] CPU: After vendor identify, caps: 0383f9ff c1c3f9ff 00000000 00000000 00000000 00000000 00000000
[17179573.444000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[17179573.444000] CPU: L2 Cache: 512K (64 bytes/line)
[17179573.444000] CPU: After all inits, caps: 0383f9ff c1c3f9ff 00000000 00000420 00000000 00000000 00000000
[17179573.444000] mtrr: v2.0 (20020519)
[17179573.444000] CPU: AMD Athlon(tm) XP 2600+ stepping 00
[17179573.444000] Enabling fast FPU save and restore... done.
[17179573.444000] Enabling unmasked SIMD FPU exception support... done.
[17179573.444000] Checking 'hlt' instruction... OK.
[17179573.460000] checking if image is initramfs... it is
[17179574.004000] Freeing initrd memory: 6614k freed
[17179574.020000] ACPI: Looking for DSDT ... not found!
[17179574.024000] ACPI: setting ELCR to 0200 (from 0a20)
[17179574.312000] NET: Registered protocol family 16
[17179574.312000] EISA bus registered
[17179574.312000] ACPI: bus type pci registered
[17179574.316000] PCI: PCI BIOS revision 2.10 entry at 0xfb2e0, last bus=1
[17179574.316000] PCI: Using configuration type 1
[17179574.316000] ACPI: Subsystem revision 20051216
[17179574.324000] ACPI: Interpreter enabled
[17179574.324000] ACPI: Using PIC for interrupt routing
[17179574.324000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179574.324000] PCI: Probing PCI hardware (bus 00)
[17179574.324000] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[17179574.324000] PCI quirk: region 4000-407f claimed by vt8235 PM
[17179574.324000] PCI quirk: region 5000-500f claimed by vt8235 SMB
[17179574.324000] Boot video device is 0000:01:00.0
[17179574.324000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179574.348000] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 *5 6 7 10 11 12 14 15)
[17179574.352000] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 10 *11 12 14 15)
[17179574.352000] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 10 *11 12 14 15)
[17179574.352000] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 *5 6 7 10 11 12 14 15)
[17179574.356000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179574.356000] pnp: PnP ACPI init
[17179574.360000] pnp: PnP ACPI: found 14 devices
[17179574.360000] PnPBIOS: Disabled by ACPI PNP
[17179574.360000] PCI: Using ACPI for IRQ routing
[17179574.360000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179574.380000] PCI: Bridge: 0000:00:01.0
[17179574.380000]   IO window: c000-cfff
[17179574.380000]   MEM window: e4000000-e40fffff
[17179574.380000]   PREFETCH window: c0000000-dfffffff
[17179574.380000] PCI: Setting latency timer of device 0000:00:01.0 to 64
[17179574.380000] audit: initializing netlink socket (disabled)
[17179574.380000] audit(1157125891.380:1): initialized
[17179574.380000] VFS: Disk quotas dquot_6.5.1
[17179574.380000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179574.380000] Initializing Cryptographic API
[17179574.380000] io scheduler noop registered
[17179574.380000] io scheduler anticipatory registered
[17179574.380000] io scheduler deadline registered
[17179574.380000] io scheduler cfq registered
[17179574.380000] isapnp: Scanning for PnP cards...
[17179574.732000] isapnp: No Plug & Play device found
[17179574.748000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[17179574.748000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179574.748000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179574.748000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[17179574.748000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179574.748000] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[17179574.748000] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179574.748000] 00:08: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[17179574.748000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179574.748000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179574.748000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179574.748000] mice: PS/2 mouse device common for all mice
[17179574.748000] EISA: Probing bus 0 at eisa.0
[17179574.748000] Cannot allocate resource for EISA slot 4
[17179574.748000] Cannot allocate resource for EISA slot 5
[17179574.748000] EISA: Detected 0 cards.
[17179574.748000] NET: Registered protocol family 2
[17179574.776000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179574.784000] IP route cache hash table entries: 8192 (order: 3, 32768 bytes)
[17179574.784000] TCP established hash table entries: 32768 (order: 5, 131072 bytes)
[17179574.784000] TCP bind hash table entries: 32768 (order: 5, 131072 bytes)
[17179574.784000] TCP: Hash tables configured (established 32768 bind 32768)
[17179574.784000] TCP reno registered
[17179574.784000] TCP bic registered
[17179574.784000] NET: Registered protocol family 1
[17179574.784000] NET: Registered protocol family 8
[17179574.784000] NET: Registered protocol family 20
[17179574.784000] Using IPI Shortcut mode
[17179574.784000] ACPI wakeup devices: 
[17179574.784000] SLPB PCI0 USB0 USB1 USB2 USB6 USB7 USB8 USB9 LAN0 MC97 UAR1 LPT1 
[17179574.784000] ACPI: (supports S0 S3 S4 S5)
[17179574.784000] Freeing unused kernel memory: 288k freed
[17179574.828000] vga16fb: initializing
[17179574.828000] vga16fb: mapped to 0xc00a0000
[17179574.924000] Console: switching to colour frame buffer device 80x25
[17179574.924000] fb0: VGA16 VGA frame buffer device
[17179576.020000] Capability LSM initialized
[17179576.048000] ACPI: Fan [FAN] (on)
[17179576.052000] ACPI: CPU0 (power states: C1[C1] C2[C2])
[17179576.052000] ACPI: Processor [CPU0] (supports 2 throttling states)
[17179576.052000] ACPI: Thermal Zone [THRM] (51 C)
[17179576.432000] VP_IDE: IDE controller at PCI slot 0000:00:11.1
[17179576.432000] **** SET: Misaligned resource pointer: dfc9e2c2 Type 07 Len 0
[17179576.432000] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 5
[17179576.432000] PCI: setting IRQ 5 as level-triggered
[17179576.432000] ACPI: PCI Interrupt 0000:00:11.1[A] -> Link [LNKA] -> GSI 5 (level, low) -> IRQ 5
[17179576.432000] PCI: VIA IRQ fixup for 0000:00:11.1, from 255 to 5
[17179576.432000] VP_IDE: chipset revision 6
[17179576.432000] VP_IDE: not 100% native mode: will probe irqs later
[17179576.432000] VP_IDE: VIA vt8235 (rev 00) IDE UDMA133 controller on pci0000:00:11.1
[17179576.432000]     ide0: BM-DMA at 0xe000-0xe007, BIOS settings: hda:DMA, hdb:DMA
[17179576.432000]     ide1: BM-DMA at 0xe008-0xe00f, BIOS settings: hdc:DMA, hdd:DMA
[17179576.432000] Probing IDE interface ide0...
[17179576.848000] hda: WDC WD200EB-00CSF0, ATA DISK drive
[17179577.128000] hdb: Maxtor 6E040L0, ATA DISK drive
[17179577.184000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179577.908000] Probing IDE interface ide1...
[17179578.772000] hdc: ATAPI CDRW 52X32, ATAPI CD/DVD-ROM drive
[17179579.556000] hdd: LITE-ON DVDRW SOHW-1633S, ATAPI CD/DVD-ROM drive
[17179579.612000] ide1 at 0x170-0x177,0x376 on irq 15
[17179579.620000] hda: max request size: 128KiB
[17179579.636000] hda: 39102336 sectors (20020 MB) w/2048KiB Cache, CHS=38792/16/63, UDMA(100)
[17179579.636000] hda: cache flushes not supported
[17179579.636000]  hda: hda1
[17179579.668000] hdb: max request size: 128KiB
[17179579.668000] hdb: 80293248 sectors (41110 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(133)
[17179579.668000] hdb: cache flushes supported
[17179579.668000]  hdb: hdb1 hdb2
[17179579.704000] hdc: ATAPI 52X CD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
[17179579.704000] Uniform CD-ROM driver Revision: 3.20
[17179579.712000] hdd: ATAPI 48X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(33)
[17179580.056000] usbcore: registered new driver usbfs
[17179580.056000] usbcore: registered new driver hub
[17179580.060000] USB Universal Host Controller Interface driver v2.3
[17179580.060000] ACPI: PCI Interrupt 0000:00:10.0[A] -> Link [LNKA] -> GSI 5 (level, low) -> IRQ 5
[17179580.060000] uhci_hcd 0000:00:10.0: UHCI Host Controller
[17179580.060000] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
[17179580.060000] uhci_hcd 0000:00:10.0: irq 5, io base 0x0000d400
[17179580.060000] hub 1-0:1.0: USB hub found
[17179580.060000] hub 1-0:1.0: 2 ports detected
[17179580.164000] **** SET: Misaligned resource pointer: dfbb0c02 Type 07 Len 0
[17179580.164000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 11
[17179580.164000] PCI: setting IRQ 11 as level-triggered
[17179580.164000] ACPI: PCI Interrupt 0000:00:10.1[B] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[17179580.164000] uhci_hcd 0000:00:10.1: UHCI Host Controller
[17179580.164000] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
[17179580.164000] uhci_hcd 0000:00:10.1: irq 11, io base 0x0000d800
[17179580.164000] hub 2-0:1.0: USB hub found
[17179580.164000] hub 2-0:1.0: 2 ports detected
[17179580.268000] **** SET: Misaligned resource pointer: dfbb0902 Type 07 Len 0
[17179580.268000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[17179580.268000] ACPI: PCI Interrupt 0000:00:10.2[C] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[17179580.268000] uhci_hcd 0000:00:10.2: UHCI Host Controller
[17179580.268000] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
[17179580.268000] uhci_hcd 0000:00:10.2: irq 11, io base 0x0000dc00
[17179580.268000] hub 3-0:1.0: USB hub found
[17179580.268000] hub 3-0:1.0: 2 ports detected
[17179580.372000] **** SET: Misaligned resource pointer: dfbb0602 Type 07 Len 0
[17179580.372000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 5
[17179580.372000] ACPI: PCI Interrupt 0000:00:10.3[D] -> Link [LNKD] -> GSI 5 (level, low) -> IRQ 5
[17179580.372000] ehci_hcd 0000:00:10.3: EHCI Host Controller
[17179580.372000] ehci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
[17179580.372000] ehci_hcd 0000:00:10.3: irq 5, io mem 0xe4101000
[17179580.372000] ehci_hcd 0000:00:10.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179580.372000] hub 4-0:1.0: USB hub found
[17179580.372000] hub 4-0:1.0: 6 ports detected
[17179580.404000] usb 1-1: new full speed USB device using uhci_hcd and address 2
[17179580.532000] Attempting manual resume
[17179580.572000] EXT3-fs: mounted filesystem with ordered data mode.
[17179580.584000] kjournald starting.  Commit interval 5 seconds
[17179581.532000] usb 4-3: new high speed USB device using ehci_hcd and address 3
[17179581.904000] usb 4-5: new high speed USB device using ehci_hcd and address 4
[17179582.276000] usb 1-1: new full speed USB device using uhci_hcd and address 3
[17179592.704000] Linux agpgart interface v0.101 (c) Dave Jones
[17179592.720000] agpgart: Detected VIA KT400/KT400A/KT600 chipset
[17179592.728000] agpgart: AGP aperture is 64M @ 0xe0000000
[17179592.780000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179592.780000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179593.188000] irda_init()
[17179593.188000] NET: Registered protocol family 23
[17179593.204000] Real Time Clock Driver v1.12
[17179593.340000] input: PC Speaker as /class/input/input1
[17179593.740000] Floppy drive(s): fd0 is 1.44M
[17179593.752000] parport: PnPBIOS parport detected.
[17179593.752000] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[17179593.760000] FDC 0 is a post-1991 82077
[17179593.764000] Linux video capture interface: v1.00
[17179593.844000] sn9c102: V4L2 driver for SN9C10x PC Camera Controllers v1:1.24a
[17179593.848000] usb 1-1: SN9C10[12] PC Camera Controller detected (vid/pid 0x0C45/0x602B)
[17179593.856000] usb 1-1: MI-0343 image sensor detected
[17179593.860000] via-rhine.c:v1.10-LK1.2.0-2.6 June-10-2004 Written by Donald Becker
[17179593.860000] ACPI: PCI Interrupt 0000:00:0e.0[A] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[17179593.868000] eth0: VIA Rhine III at 0x1d000, 00:10:5c:e1:88:f6, IRQ 11.
[17179593.868000] eth0: MII PHY found at address 1, status 0x7849 advertising 05e1 Link 0000.
[17179593.940000] usb 1-1: Initialization succeeded
[17179593.940000] usb 1-1: V4L2 device registered as /dev/video0
[17179593.940000] usb 1-1: Optional device control through 'sysfs' interface ready
[17179593.940000] usbcore: registered new driver sn9c102
[17179594.004000] ACPI: PCI Interrupt 0000:00:11.5[C] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[17179594.004000] PCI: Setting latency timer of device 0000:00:11.5 to 64
[17179594.480000] input: ImPS/2 Generic Wheel Mouse as /class/input/input2
[17179594.528000] ts: Compaq touchscreen protocol output
[17179595.056000] lp0: using parport0 (interrupt-driven).
[17179595.112000] Adding 1236996k swap on /dev/hdb2.  Priority:-1 extents:1 across:1236996k
[17179595.240000] EXT3 FS on hda1, internal journal
[17179595.408000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[17179595.408000] md: bitmap version 4.39
[17179595.956000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[17179596.648000] hdc: packet command error: status=0x51 { DriveReady SeekComplete Error }
[17179596.648000] hdc: packet command error: error=0x50 { LastFailedSense=0x05 }
[17179596.648000] ide: failed opcode was: unknown
[17179596.648000] cdrom: failed setting lba address space
[17179596.652000] cdrom: open failed.
[17179597.012000] kjournald starting.  Commit interval 5 seconds
[17179597.012000] EXT3 FS on hdb1, internal journal
[17179597.012000] EXT3-fs: mounted filesystem with ordered data mode.
[17179598.800000] NET: Registered protocol family 17
[17179601.436000] ndiswrapper version 1.8 loaded (preempt=yes,smp=no)
[17179601.524000] ndiswrapper: driver sis163u (Silicon Integrated Systems Corp.(1.02.05),11/29/2004,5.1.1039.1020) loaded
[17179602.732000] wlan0: vendor: 'Wireless Driver'
[17179602.732000] wlan0: ndiswrapper ethernet device 00:03:2f:26:7f:35 using driver sis163u, 0D8E:0163.F.conf
[17179602.732000] wlan0: encryption modes supported: WEP; TKIP with WPA; AES/CCMP with WPA
[17179602.736000] usbcore: registered new driver ndiswrapper
[17179611.240000] NET: Registered protocol family 10
[17179611.244000] lo: Disabled Privacy Extensions
[17179611.244000] IPv6 over IPv4 tunneling driver
[17179612.708000] ACPI: Power Button (FF) [PWRF]
[17179612.708000] ACPI: Power Button (CM) [PWRB]
[17179612.708000] ACPI: Sleep Button (CM) [SLPB]
[17179612.808000] ibm_acpi: ec object not found
[17179612.840000] pcc_acpi: loading...
[17179615.100000] ppdev: user-space parallel port driver
[17179615.720000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[17179615.720000] apm: overridden by ACPI.
[17179618.680000] cdrom: This disc doesn't have any tracks I recognize!
[17179620.076000] Bluetooth: Core ver 2.8
[17179620.076000] NET: Registered protocol family 31
[17179620.076000] Bluetooth: HCI device and connection manager initialized
[17179620.076000] Bluetooth: HCI socket layer initialized
[17179620.092000] Bluetooth: L2CAP ver 2.8
[17179620.092000] Bluetooth: L2CAP socket layer initialized
[17179620.104000] Bluetooth: RFCOMM socket layer initialized
[17179620.104000] Bluetooth: RFCOMM TTY layer initialized
[17179620.104000] Bluetooth: RFCOMM ver 1.7
[17179621.664000] wlan0: no IPv6 routers present
[17179622.784000] [drm] Initialized drm 1.0.1 20051102
[17179622.800000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 5 (level, low) -> IRQ 5
[17179622.800000] [drm] Initialized radeon 1.24.0 20060225 on minor 0
[17179623.880000] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
[17179623.880000] agpgart: Putting AGP V3 device at 0000:00:00.0 into 4x mode
[17179623.880000] agpgart: Putting AGP V3 device at 0000:01:00.0 into 4x mode
[17179640.236000] [drm] Setting GART location based on new memory map
[17179640.236000] [drm] Loading R300 Microcode
[17179640.236000] [drm] writeback test succeeded in 1 usecs
[17179677.844000] NET: Registered protocol family 4
[17179678.120000] NET: Registered protocol family 3
[17179678.384000] NET: Registered protocol family 5
[17183535.676000] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
[17183535.676000] agpgart: Putting AGP V3 device at 0000:00:00.0 into 4x mode
[17183535.676000] agpgart: Putting AGP V3 device at 0000:01:00.0 into 4x mode
[17183535.676000] [drm] Loading R300 Microcode
[17183588.000000] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
[17183588.000000] agpgart: Putting AGP V3 device at 0000:00:00.0 into 4x mode
[17183588.000000] agpgart: Putting AGP V3 device at 0000:01:00.0 into 4x mode
[17183588.000000] [drm] Loading R300 Microcode
[17184219.796000] usb 4-3: USB disconnect, address 3
[17184220.036000] usb 4-3: new high speed USB device using ehci_hcd and address 5

```

---

### Post by gsdefender on 2006-09-01
> **jm2003uk said:**
> 
```

[17179580.372000] **** SET: Misaligned resource pointer: dfbb0602 Type 07 Len 0

```


This message is strange enough to let me tell you to try appending the options

```

irqpoll pci=routeirq

```

to your 

```

# kopt= ...

```

line /boot/grub/menu.lst. Remember not to delete anything (not even the dash) from that line, just append the options. After that do

```

sudo /sbin/update-grub; sudo /sbin/reboot

```

If you have problems even after that, post your new dmesg and we will see what else can be done.

---

