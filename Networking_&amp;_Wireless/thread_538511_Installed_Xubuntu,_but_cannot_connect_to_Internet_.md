---
title: "Installed Xubuntu, but cannot connect to Internet (Router/Ethernetcard)"
date: 2007-08-30
forum: Networking &amp; Wireless
---

### Post by Zuinig on 2007-08-30
Hi there,

Last Saturday I installed Xubuntu 6.06.1 on a 6-7 year old PC. It took six (!) hours to complete the installation procedure, however, Xubuntu works fine and I'm quite excited about it! Finally there's a Linux version that has the potential to free regular PC users from expensive OS-alternatives.

However, I got a problem: I can't connect to the Internet.
Specifications:
- CableModem > Router > Ethernetcable > Ethernetcard
- Internet works fine on my Windows PC (using wireless connection in that case).

When I go to System (/ Administration) / Networking, the only thing I can select is a dialup modem connection; there is nothing that seems to indicate that I've got an ethernetcard installed in my PC and there's nothing I can "add". By the way, I don't understand what "location" means in this context.

What can be the problem? Should I try to plug the ethernet card into another slot and try again? Do I then have to do re-installation afterwards (another x amount of hours?), or will Xubuntu recognize it automatically? How can I see or test that Xubuntu views this piece of hardware? Should I buy a new ethernetcard? Is there a list of (X)ubuntu supported hardware? 

Thanks for your time,
Zuinig
(The Netherlands)

---

### Post by noob12 on 2007-08-30
Can you please post the result of these commands so we can see exactly what you have?

```

lspci -nn

sudo lshw -C network

```

Also, if you could post the full output of 

```

dmesg

```

It will probably help.

---

### Post by Zuinig on 2007-08-30
(deleted)

---

### Post by Zuinig on 2007-08-30
```
lspci -nn
0000:00:00.0 0600: 10b9:1541 (rev 04)
0000:00:01.0 0604: 10b9:5243 (rev 04)
0000:00:02.0 0c03: 10b9:5237 (rev 03)
0000:00:03.0 0680: 10b9:7101
0000:00:07.0 0601: 10b9:1533 (rev c3)
0000:00:0a.0 0401: 1274:1371 (rev 08)
0000:00:0b.0 0c03: 1106:3038 (rev 61)
0000:00:0b.1 0c03: 1106:3038 (rev 61)
0000:00:0b.2 0c03: 1106:3104 (rev 63)
0000:00:0d.0 0400: 109e:036e (rev 02)
0000:00:0d.1 0480: 109e:0878 (rev 02)
0000:00:0f.0 0101: 10b9:5229 (rev c1)
0000:01:00.0 0300: 5333:8a13 (rev 02)

sudo lshw -C network
(no fixed output after it runs through PCI, USB, IDE etc)

dmesg
[17179569.184000] Linux version 2.6.15-26-386 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Thu Aug 3 02:52:00 UTC 2006
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[17179569.184000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000000fffc000 (usable)
[17179569.184000]  BIOS-e820: 000000000fffc000 - 000000000ffff000 (ACPI data)
[17179569.184000]  BIOS-e820: 000000000ffff000 - 0000000010000000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 255MB LOWMEM available.
[17179569.184000] On node 0 totalpages: 65532
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   DMA32 zone: 0 pages, LIFO batch:0
[17179569.184000]   Normal zone: 61436 pages, LIFO batch:15
[17179569.184000]   HighMem zone: 0 pages, LIFO batch:0
[17179569.184000] DMI 2.0 present.
[17179569.184000] ACPI: RSDP (v000 ASUS                                  ) @ 0x000f81a0
[17179569.184000] ACPI: RSDT (v001 ASUS   P5A      0x58582e31 ASUS 0x31303030) @ 0x0fffc000
[17179569.184000] ACPI: FADT (v001 ASUS   P5A      0x58582e31 ASUS 0x31303030) @ 0x0fffc080
[17179569.184000] ACPI: BOOT (v001 ASUS   P5A      0x58582e31 ASUS 0x31303030) @ 0x0fffc040
[17179569.184000] ACPI: DSDT (v001   ASUS P5A      0x00001000 MSFT 0x01000001) @ 0x00000000
[17179569.184000] ACPI: BIOS age (1999) fails cutoff (2000), acpi=force is required to enable ACPI
[17179569.184000] ACPI: Disabling ACPI support
[17179569.184000] Allocating PCI resources starting at 20000000 (gap: 10000000:efff0000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hdb1 ro quiet splash
[17179569.184000] No local APIC present or hardware disabled
[17179569.184000] mapped APIC to ffffd000 (01201000)
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 1024 (order: 10, 16384 bytes)
[    0.000000] Detected 501.245 MHz processor.
[   21.897855] Using tsc for high-res timesource
[   21.899361] Console: colour VGA+ 80x25
[   21.902110] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   21.904604] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   21.945885] Memory: 248884k/262128k available (1976k kernel code, 12580k reserved, 606k data, 288k init, 0k highmem)
[   21.945900] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   22.023645] Calibrating delay using timer specific routine.. 1003.40 BogoMIPS (lpj=2006817)
[   22.023796] Security Framework v1.0.0 initialized
[   22.023831] SELinux:  Disabled at boot.
[   22.023899] Mount-cache hash table entries: 512
[   22.024381] CPU: After generic identify, caps: 008021bf 808029bf 00000000 00000000 00000000 00000000 00000000
[   22.024419] CPU: After vendor identify, caps: 008021bf 808029bf 00000000 00000000 00000000 00000000 00000000
[   22.024449] CPU: L1 I Cache: 32K (32 bytes/line), D cache 32K (32 bytes/line)[   22.024460] CPU: After all inits, caps: 008021bf 808029bf 00000000 00000002 00000000 00000000 00000000
[   22.024529] mtrr: v2.0 (20020519)
[   22.024538] CPU: AMD-K6(tm) 3D processor stepping 0c
[   22.024558] Checking 'hlt' instruction... OK.
[   22.040235] checking if image is initramfs... it is
[   25.077299] Freeing initrd memory: 6841k freed
[   25.151778] NET: Registered protocol family 16
[   25.151945] EISA bus registered
[   25.153003] PCI: PCI BIOS revision 2.10 entry at 0xf06c0, last bus=1
[   25.153028] PCI: Using configuration type 1
[   25.154862] ACPI: Subsystem revision 20051216
[   25.154874] ACPI: Interpreter disabled.
[   25.154887] Linux Plug and Play Support v0.97 (c) Adam Belay
[   25.154967] pnp: PnP ACPI: disabled
[   25.154982] PnPBIOS: Scanning system for PnP BIOS support...
[   25.155418] PnPBIOS: Found PnP BIOS installation structure at 0xc00fd1d0
[   25.155437] PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0xd200, dseg 0xf0000[   25.159343] PnPBIOS: 15 nodes reported by PnP BIOS; 15 recorded by driver
[   25.159418] PCI: Probing PCI hardware
[   25.159436] PCI: Probing PCI hardware (bus 00)
[   25.159881] PCI quirk: region 5c20-5c3f claimed by ali7101 SMB
[   25.160528] Boot video device is 0000:01:00.0
[   25.163147] PCI: Using ALI IRQ Router
[   25.163162] PCI: Using IRQ router ALI [10b9/1533] at 0000:00:07.0
[   25.170718] PCI: BIOS reporting unknown device 00:58
[   25.170727] PCI: Device 0000:00:0b.1 not found by BIOS
[   25.177004] pnp: 00:11: ioport range 0x290-0x297 has been reserved
[   25.177020] pnp: 00:11: ioport range 0x40b-0x40b has been reserved
[   25.177033] pnp: 00:11: ioport range 0x480-0x49f has been reserved
[   25.177045] pnp: 00:11: ioport range 0x4d6-0x4d6 has been reserved
[   25.177058] pnp: 00:11: ioport range 0xec00-0xec3f has been reserved
[   25.177071] pnp: 00:11: ioport range 0xe800-0xe83f has been reserved
[   25.178306] PCI: Bridge: 0000:00:01.0
[   25.178318]   IO window: disabled.
[   25.178331]   MEM window: cc000000-cfffffff
[   25.178342]   PREFETCH window: e7f00000-e7ffffff
[   25.178649] Simple Boot Flag at 0x46 set to 0x1
[   25.181122] audit: initializing netlink socket (disabled)
[   25.181176] audit(1188492696.244:1): initialized
[   25.181778] VFS: Disk quotas dquot_6.5.1
[   25.181914] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   25.182194] Initializing Cryptographic API
[   25.182217] io scheduler noop registered
[   25.182245] io scheduler anticipatory registered
[   25.182267] io scheduler deadline registered
[   25.182318] io scheduler cfq registered
[   25.182345] Activating ISA DMA hang workarounds.
[   25.183218] isapnp: Scanning for PnP cards...
[   25.537210] isapnp: No Plug & Play device found
[   25.656006] PNP: PS/2 Controller [PNP0303,PNP0f13] at 0x60,0x64 irq 1,12
[   25.658827] serio: i8042 AUX port at 0x60,0x64 irq 12
[   25.659159] serio: i8042 KBD port at 0x60,0x64 irq 1
[   25.659371] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[   25.659794] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   25.660228] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   25.674125] 00:02: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   25.674927] 00:03: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   25.678029] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   25.678305] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   25.678325] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   25.679048] mice: PS/2 mouse device common for all mice
[   25.680137] EISA: Probing bus 0 at eisa.0
[   25.680191] Cannot allocate resource for EISA slot 5
[   25.680218] EISA: Detected 0 cards.
[   25.680443] NET: Registered protocol family 2
[   25.710072] input: AT Translated Set 2 keyboard as /class/input/input0
[   25.713710] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   25.714511] TCP established hash table entries: 16384 (order: 4, 65536 bytes)[   25.715125] TCP bind hash table entries: 16384 (order: 4, 65536 bytes)
[   25.715699] TCP: Hash tables configured (established 16384 bind 16384)
[   25.715711] TCP reno registered
[   25.716164] TCP bic registered
[   25.716205] NET: Registered protocol family 1
[   25.716232] NET: Registered protocol family 8
[   25.716240] NET: Registered protocol family 20
[   25.716332] Using IPI Shortcut mode
[   25.716487] Freeing unused kernel memory: 288k freed
[   25.977234] vga16fb: initializing
[   25.977293] vga16fb: mapped to 0xc00a0000
[   26.092950] Console: switching to colour frame buffer device 80x25
[   26.092978] fb0: VGA16 VGA frame buffer device
[   27.227469] Capability LSM initialized
[   29.764158] ALI15X3: IDE controller at PCI slot 0000:00:0f.0
[   29.764218] ALI15X3: chipset revision 193
[   29.764228] ALI15X3: not 100% native mode: will probe irqs later
[   29.764323]     ide0: BM-DMA at 0xb800-0xb807, BIOS settings: hda:DMA, hdb:DMA
[   29.764382]     ide1: BM-DMA at 0xb808-0xb80f, BIOS settings: hdc:pio, hdd:pio
[   29.764422] Probing IDE interface ide0...
[   30.050930] hda: ST315320A, ATA DISK drive
[   30.330751] hdb: Maxtor 91021U2, ATA DISK drive
[   30.387084] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   30.388262] Probing IDE interface ide1...
[   31.122273] hdc: HL-DT-ST RW/DVD GCC-4480B, ATAPI CD/DVD-ROM drive
[   31.905796] hdd: LITEON DVD-ROM LTD163D, ATAPI CD/DVD-ROM drive
[   31.961999] ide1 at 0x170-0x177,0x376 on irq 15
[   32.006224] hda: max request size: 128KiB
[   32.006246] hda: 29888820 sectors (15303 MB) w/2048KiB Cache, CHS=29651/16/63, UDMA(33)
[   32.006268] hda: cache flushes not supported
[   32.007129]  hda: hda1
[   32.053105]  hda1: <bsd: hda5 hda6 hda7 hda8 hda9 >
[   32.055951] hdb: max request size: 128KiB
[   32.070705] hdb: 20010816 sectors (10245 MB) w/512KiB Cache, CHS=19852/16/63, UDMA(33)
[   32.070736] hdb: cache flushes not supported
[   32.071411]  hdb: hdb1 hdb2 < hdb5 >
[   32.172074] hdc: ATAPI 48X DVD-ROM CD-R/RW drive, 2048kB Cache, (U)DMA
[   32.172116] Uniform CD-ROM driver Revision: 3.20
[   32.175190] hdd: ATAPI 48X DVD-ROM drive, 512kB Cache, (U)DMA
[   32.970506] usbcore: registered new driver usbfs
[   32.972071] usbcore: registered new driver hub
[   32.980755] USB Universal Host Controller Interface driver v2.3
[   32.982491] PCI: Found IRQ 11 for device 0000:00:0b.0
[   32.982571] uhci_hcd 0000:00:0b.0: UHCI Host Controller
[   32.984474] uhci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 1
[   32.984512] uhci_hcd 0000:00:0b.0: irq 11, io base 0x0000d400
[   32.986167] hub 1-0:1.0: USB hub found
[   32.986240] hub 1-0:1.0: 2 ports detected
[   33.089916] PCI: Found IRQ 5 for device 0000:00:0b.1
[   33.089946] PCI: Sharing IRQ 5 with 0000:00:0a.0
[   33.090002] uhci_hcd 0000:00:0b.1: UHCI Host Controller
[   33.090556] uhci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 2
[   33.090597] uhci_hcd 0000:00:0b.1: irq 5, io base 0x0000d000
[   33.092089] hub 2-0:1.0: USB hub found
[   33.092151] hub 2-0:1.0: 2 ports detected
[   33.144048] ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[   33.145653] PCI: Found IRQ 9 for device 0000:00:02.0
[   33.145734] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   33.145751] ohci_hcd 0000:00:02.0: OHCI Host Controller
[   33.201293] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 3
[   33.201333] ohci_hcd 0000:00:02.0: irq 9, io mem 0xcb800000
[   33.201411] PCI: Found IRQ 10 for device 0000:00:0b.2
[   33.201446] PCI: Sharing IRQ 10 with 0000:00:0d.0
[   33.201458] PCI: Sharing IRQ 10 with 0000:00:0d.1
[   33.201502] ehci_hcd 0000:00:0b.2: EHCI Host Controller
[   33.202298] ehci_hcd 0000:00:0b.2: new USB bus registered, assigned bus number 4
[   33.202330] ehci_hcd 0000:00:0b.2: irq 10, io mem 0xcb000000
[   33.202357] ehci_hcd 0000:00:0b.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   33.203692] hub 4-0:1.0: USB hub found
[   33.203766] hub 4-0:1.0: 4 ports detected
[   33.310796] hub 3-0:1.0: USB hub found
[   33.310865] hub 3-0:1.0: 2 ports detected
[   33.769776] Attempting manual resume
[   33.868682] EXT3-fs: mounted filesystem with ordered data mode.
[   33.872903] kjournald starting.  Commit interval 5 seconds
[   53.605147] Linux agpgart interface v0.101 (c) Dave Jones
[   53.610015] agpgart: Detected ALi M1541 chipset
[   53.619978] agpgart: AGP aperture is 256M @ 0xd0000000
[   54.227253] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   54.267390] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   55.634379] Linux video capture interface: v1.00
[   56.078457] bttv: driver version 0.9.16 loaded
[   56.078477] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   56.078698] bttv: Bt8xx card found (0).
[   56.078742] PCI: Found IRQ 10 for device 0000:00:0d.0
[   56.078772] PCI: Sharing IRQ 10 with 0000:00:0b.2
[   56.078785] PCI: Sharing IRQ 10 with 0000:00:0d.1
[   56.078815] bttv0: Bt878 (rev 2) at 0000:00:0d.0, irq: 10, latency: 32, mmio: 0xe7000000
[   56.078862] bttv0: detected: Terratec TValue (Temic PAL B/G) [card=33], PCI subsystem ID is 153b:1118
[   56.078876] bttv0: using: Terratec TerraTValue Version Bt878 [card=33,autodetected]
[   56.078956] bttv0: gpio: en=00000000, out=00000000 in=00ffefff [init]
[   56.080531] bttv0: using tuner=5
[   56.080549] bttv0: i2c: checking for MSP34xx @ 0x80... not found
[   56.082766] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[   56.084974] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[   56.171379] bttv0: i2c: checking for TDA9887 @ 0x86... not found
[   56.271657] tuner 1-0060: All bytes are equal. It is not a TEA5767
[   56.271676] tuner 1-0060: chip found @ 0xc0 (bt878 #0 [sw])
[   56.271830] tuner 1-0060: type set to 5 (Philips PAL_BG (FI1216 and compatibles))
[   56.306019] bttv0: registered device video0
[   56.306268] bttv0: registered device vbi0
[   56.306331] bttv0: PLL: 28636363 => 35468950 .. ok
[   56.355427] bt878: AUDIO driver version 0.0.0 loaded
[   56.355580] bt878: Bt878 AUDIO function found (0).
[   56.355610] PCI: Found IRQ 10 for device 0000:00:0d.1
[   56.355640] PCI: Sharing IRQ 10 with 0000:00:0b.2
[   56.355652] PCI: Sharing IRQ 10 with 0000:00:0d.0
[   56.355682] bt878(0): Bt878 (rev 2) at 00:0d.1, irq: 10, latency: 32, memory: 0xe6800000
[   56.594432] logips2pp: Detected unknown logitech mouse model 1
[   56.784284] input: PS/2 Logitech Mouse as /class/input/input1
[   57.095434] PCI: Found IRQ 5 for device 0000:00:0a.0
[   57.095471] PCI: Sharing IRQ 5 with 0000:00:0b.1
[   57.388313] parport: PnPBIOS parport detected.
[   57.388401] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   58.431149] Floppy drive(s): fd0 is 1.44M
[   58.448863] FDC 0 is a post-1991 82077
[   59.496364] ts: Compaq touchscreen protocol output
[   59.851220] input: PC Speaker as /class/input/input2
[   60.186054] Real Time Clock Driver v1.12
[   62.552591] lp0: using parport0 (interrupt-driven).
[   62.838411] Adding 441748k swap on /dev/hdb5.  Priority:-1 extents:1 across:441748k
[   63.033988] EXT3 FS on hdb1, internal journal
[   63.598921] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[   63.598939] md: bitmap version 4.39
[   65.077739] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[   65.452158] cdrom: open failed.
[   66.117198] cdrom: open failed.
[   67.137667] cdrom: open failed.
[   71.077748] NET: Registered protocol family 17
[   93.833002] ppdev: user-space parallel port driver
[   94.656277] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   99.789222] hdc: drive_cmd: status=0x51 { DriveReady SeekComplete Error }
[   99.789253] hdc: drive_cmd: error=0x04 { AbortedCommand }
[   99.789266] ide: failed opcode was: 0xec
[   99.811698] hdd: drive_cmd: status=0x51 { DriveReady SeekComplete Error }
[   99.811755] hdd: drive_cmd: error=0x04 { AbortedCommand }
[   99.811772] ide: failed opcode was: 0xec
[  249.547785] hdc: tray open
[  249.547816] end_request: I/O error, dev hdc, sector 0
[  249.547833] Buffer I/O error on device hdc, logical block 0
[  249.548185] hdc: tray open
[  249.548195] end_request: I/O error, dev hdc, sector 4
[  249.548208] Buffer I/O error on device hdc, logical block 1
[  249.548546] hdc: tray open
[  249.548555] end_request: I/O error, dev hdc, sector 8
[  249.548567] Buffer I/O error on device hdc, logical block 2
[  249.548909] hdc: tray open
[  249.548917] end_request: I/O error, dev hdc, sector 12
[  249.548929] Buffer I/O error on device hdc, logical block 3
[  249.549272] hdc: tray open
[  249.549281] end_request: I/O error, dev hdc, sector 16
[  249.549293] Buffer I/O error on device hdc, logical block 4
[  249.549649] hdc: tray open
[  249.549660] end_request: I/O error, dev hdc, sector 20
[  249.549673] Buffer I/O error on device hdc, logical block 5
[  249.550016] hdc: tray open
[  249.550025] end_request: I/O error, dev hdc, sector 24
[  249.550038] Buffer I/O error on device hdc, logical block 6
[  249.550379] hdc: tray open
[  249.550387] end_request: I/O error, dev hdc, sector 28
[  249.550399] Buffer I/O error on device hdc, logical block 7
[  249.550730] hdc: tray open
[  249.550739] end_request: I/O error, dev hdc, sector 32
[  249.550751] Buffer I/O error on device hdc, logical block 8
[  249.551082] hdc: tray open
[  249.551091] end_request: I/O error, dev hdc, sector 36
[  249.551102] Buffer I/O error on device hdc, logical block 9
[  249.551433] hdc: tray open
[  249.551442] end_request: I/O error, dev hdc, sector 40
[  249.551775] hdc: tray open
[  249.551784] end_request: I/O error, dev hdc, sector 44
[  249.552117] hdc: tray open
[  249.552125] end_request: I/O error, dev hdc, sector 48
[  249.552460] hdc: tray open
[  249.552469] end_request: I/O error, dev hdc, sector 52
[  249.552804] hdc: tray open
[  249.552812] end_request: I/O error, dev hdc, sector 56
[  249.553147] hdc: tray open
[  249.553156] end_request: I/O error, dev hdc, sector 60
[  249.562102] hdc: tray open
[  249.562122] end_request: I/O error, dev hdc, sector 0
[  249.562467] hdc: tray open
[  249.562477] end_request: I/O error, dev hdc, sector 4
[  249.563598] hdc: tray open
[  249.563616] end_request: I/O error, dev hdc, sector 0
[  249.563972] hdc: tray open
[  249.563986] end_request: I/O error, dev hdc, sector 4
[  249.565499] hdc: tray open
[  249.565517] end_request: I/O error, dev hdc, sector 0
[  249.565889] hdc: tray open
[  249.565903] end_request: I/O error, dev hdc, sector 4
[  249.581889] hdd: tray open
[  249.581915] end_request: I/O error, dev hdd, sector 0
[  249.582283] hdd: tray open
[  249.582296] end_request: I/O error, dev hdd, sector 4
[  249.582646] hdd: tray open
[  249.582658] end_request: I/O error, dev hdd, sector 8
[  249.582985] hdd: tray open
[  249.582994] end_request: I/O error, dev hdd, sector 12
[  249.583325] hdd: tray open
[  249.583334] end_request: I/O error, dev hdd, sector 16
[  249.583656] hdd: tray open
[  249.583665] end_request: I/O error, dev hdd, sector 20
[  249.583987] hdd: tray open
[  249.583996] end_request: I/O error, dev hdd, sector 24
[  249.584309] hdd: tray open
[  249.584318] end_request: I/O error, dev hdd, sector 28
[  249.584631] hdd: tray open
[  249.584640] end_request: I/O error, dev hdd, sector 32
[  249.584953] hdd: tray open
[  249.584962] end_request: I/O error, dev hdd, sector 36
[  249.585275] hdd: tray open
[  249.585284] end_request: I/O error, dev hdd, sector 40
[  249.585599] hdd: tray open
[  249.585609] end_request: I/O error, dev hdd, sector 44
[  249.585937] hdd: tray open
[  249.585946] end_request: I/O error, dev hdd, sector 48
[  249.586259] hdd: tray open
[  249.586268] end_request: I/O error, dev hdd, sector 52
[  249.586581] hdd: tray open
[  249.586590] end_request: I/O error, dev hdd, sector 56
[  249.586903] hdd: tray open
[  249.586912] end_request: I/O error, dev hdd, sector 60
[  249.592724] hdd: tray open
[  249.592743] end_request: I/O error, dev hdd, sector 0
[  249.593090] hdd: tray open
[  249.593105] end_request: I/O error, dev hdd, sector 4
[  249.594550] hdd: tray open
[  249.594567] end_request: I/O error, dev hdd, sector 0
[  249.594916] hdd: tray open
[  249.594932] end_request: I/O error, dev hdd, sector 4
[  249.596273] hdd: tray open
[  249.596290] end_request: I/O error, dev hdd, sector 0
[  249.596640] hdd: tray open
[  249.596654] end_request: I/O error, dev hdd, sector 4
[  249.853191] SCSI subsystem initialized
[  256.653562] hdc: tray open
[  256.653591] end_request: I/O error, dev hdc, sector 0
[  256.653605] printk: 34 messages suppressed.
[  256.653616] Buffer I/O error on device hdc, logical block 0
[  256.653972] hdc: tray open
[  256.653983] end_request: I/O error, dev hdc, sector 4
[  256.654323] hdc: tray open
[  256.654332] end_request: I/O error, dev hdc, sector 8
[  256.654664] hdc: tray open
[  256.654673] end_request: I/O error, dev hdc, sector 12
[  256.655006] hdc: tray open
[  256.655015] end_request: I/O error, dev hdc, sector 16
[  256.655348] hdc: tray open
[  256.655356] end_request: I/O error, dev hdc, sector 20
[  256.655689] hdc: tray open
[  256.655698] end_request: I/O error, dev hdc, sector 24
[  256.656031] hdc: tray open
[  256.656040] end_request: I/O error, dev hdc, sector 28
[  256.656373] hdc: tray open
[  256.656381] end_request: I/O error, dev hdc, sector 32
[  256.656714] hdc: tray open
[  256.656723] end_request: I/O error, dev hdc, sector 36
[  256.657056] hdc: tray open
[  256.657064] end_request: I/O error, dev hdc, sector 40
[  256.657423] hdc: tray open
[  256.657434] end_request: I/O error, dev hdc, sector 44
[  256.657774] hdc: tray open
[  256.657783] end_request: I/O error, dev hdc, sector 48
[  256.658118] hdc: tray open
[  256.658127] end_request: I/O error, dev hdc, sector 52
[  256.658461] hdc: tray open
[  256.658470] end_request: I/O error, dev hdc, sector 56
[  256.658805] hdc: tray open
[  256.658813] end_request: I/O error, dev hdc, sector 60
[  256.664646] hdc: tray open
[  256.664665] end_request: I/O error, dev hdc, sector 0
[  256.665013] hdc: tray open
[  256.665023] end_request: I/O error, dev hdc, sector 4
[  256.666170] hdc: tray open
[  256.666188] end_request: I/O error, dev hdc, sector 0
[  256.666537] hdc: tray open
[  256.666550] end_request: I/O error, dev hdc, sector 4
[  256.668047] hdc: tray open
[  256.668067] end_request: I/O error, dev hdc, sector 0
[  256.668417] hdc: tray open
[  256.668430] end_request: I/O error, dev hdc, sector 4
[  256.682802] hdd: tray open
[  256.682828] end_request: I/O error, dev hdd, sector 0
[  256.683196] hdd: tray open
[  256.683211] end_request: I/O error, dev hdd, sector 4
[  256.683559] hdd: tray open
[  256.683572] end_request: I/O error, dev hdd, sector 8
[  256.683898] hdd: tray open
[  256.683906] end_request: I/O error, dev hdd, sector 12
[  256.684229] hdd: tray open
[  256.684238] end_request: I/O error, dev hdd, sector 16
[  256.684560] hdd: tray open
[  256.684568] end_request: I/O error, dev hdd, sector 20
[  256.684882] hdd: tray open
[  256.684890] end_request: I/O error, dev hdd, sector 24
[  256.685204] hdd: tray open
[  256.685212] end_request: I/O error, dev hdd, sector 28
[  256.685574] hdd: tray open
[  256.685588] end_request: I/O error, dev hdd, sector 32
[  256.685921] hdd: tray open
[  256.685929] end_request: I/O error, dev hdd, sector 36
[  256.686242] hdd: tray open
[  256.686251] end_request: I/O error, dev hdd, sector 40
[  256.686564] hdd: tray open
[  256.686573] end_request: I/O error, dev hdd, sector 44
[  256.686886] hdd: tray open
[  256.686895] end_request: I/O error, dev hdd, sector 48
[  256.687208] hdd: tray open
[  256.687218] end_request: I/O error, dev hdd, sector 52
[  256.687530] hdd: tray open
[  256.687540] end_request: I/O error, dev hdd, sector 56
[  256.687852] hdd: tray open
[  256.687861] end_request: I/O error, dev hdd, sector 60
[  256.693980] hdd: tray open
[  256.694001] end_request: I/O error, dev hdd, sector 0
[  256.694339] hdd: tray open
[  256.694349] end_request: I/O error, dev hdd, sector 4
[  256.695495] hdd: tray open
[  256.695512] end_request: I/O error, dev hdd, sector 0
[  256.695853] hdd: tray open
[  256.695869] end_request: I/O error, dev hdd, sector 4
[  256.697211] hdd: tray open
[  256.697229] end_request: I/O error, dev hdd, sector 0
[  256.697594] hdd: tray open
[  256.697608] end_request: I/O error, dev hdd, sector 4
[  272.119455] hdc: tray open
[  272.119484] end_request: I/O error, dev hdc, sector 0
[  272.119499] printk: 43 messages suppressed.
[  272.119510] Buffer I/O error on device hdc, logical block 0
[  272.119886] hdc: tray open
[  272.119898] end_request: I/O error, dev hdc, sector 4
[  272.119910] Buffer I/O error on device hdc, logical block 1
[  272.120254] hdc: tray open
[  272.120263] end_request: I/O error, dev hdc, sector 8
[  272.120274] Buffer I/O error on device hdc, logical block 2
[  272.120617] hdc: tray open
[  272.120626] end_request: I/O error, dev hdc, sector 12
[  272.120959] hdc: tray open
[  272.120968] end_request: I/O error, dev hdc, sector 16
[  272.121300] hdc: tray open
[  272.121309] end_request: I/O error, dev hdc, sector 20
[  272.121642] hdc: tray open
[  272.121651] end_request: I/O error, dev hdc, sector 24
[  272.122023] hdc: tray open
[  272.122032] end_request: I/O error, dev hdc, sector 28
[  272.122364] hdc: tray open
[  272.122374] end_request: I/O error, dev hdc, sector 32
[  272.122706] hdc: tray open
[  272.122715] end_request: I/O error, dev hdc, sector 36
[  272.123048] hdc: tray open
[  272.123056] end_request: I/O error, dev hdc, sector 40
[  272.123389] hdc: tray open
[  272.123398] end_request: I/O error, dev hdc, sector 44
[  272.123731] hdc: tray open
[  272.123740] end_request: I/O error, dev hdc, sector 48
[  272.124088] hdc: tray open
[  272.124101] end_request: I/O error, dev hdc, sector 52
[  272.124449] hdc: tray open
[  272.124459] end_request: I/O error, dev hdc, sector 56
[  272.124789] hdc: tray open
[  272.124798] end_request: I/O error, dev hdc, sector 60
[  272.131532] hdc: tray open
[  272.131551] end_request: I/O error, dev hdc, sector 0
[  272.131900] hdc: tray open
[  272.131910] end_request: I/O error, dev hdc, sector 4
[  272.133062] hdc: tray open
[  272.133080] end_request: I/O error, dev hdc, sector 0
[  272.133433] hdc: tray open
[  272.133446] end_request: I/O error, dev hdc, sector 4
[  272.134942] hdc: tray open
[  272.134961] end_request: I/O error, dev hdc, sector 0
[  272.135313] hdc: tray open
[  272.135327] end_request: I/O error, dev hdc, sector 4
[  272.148583] hdd: tray open
[  272.148606] end_request: I/O error, dev hdd, sector 0
[  272.148977] hdd: tray open
[  272.148992] end_request: I/O error, dev hdd, sector 4
[  272.149339] hdd: tray open
[  272.149352] end_request: I/O error, dev hdd, sector 8
[  272.149687] hdd: tray open
[  272.149696] end_request: I/O error, dev hdd, sector 12
[  272.150018] hdd: tray open
[  272.150027] end_request: I/O error, dev hdd, sector 16
[  272.150340] hdd: tray open
[  272.150348] end_request: I/O error, dev hdd, sector 20
[  272.150662] hdd: tray open
[  272.150671] end_request: I/O error, dev hdd, sector 24
[  272.150984] hdd: tray open
[  272.150993] end_request: I/O error, dev hdd, sector 28
[  272.151306] hdd: tray open
[  272.151315] end_request: I/O error, dev hdd, sector 32
[  272.151628] hdd: tray open
[  272.151637] end_request: I/O error, dev hdd, sector 36
[  272.151978] hdd: tray open
[  272.151988] end_request: I/O error, dev hdd, sector 40
[  272.152317] hdd: tray open
[  272.152326] end_request: I/O error, dev hdd, sector 44
[  272.152639] hdd: tray open
[  272.152648] end_request: I/O error, dev hdd, sector 48
[  272.152962] hdd: tray open
[  272.152970] end_request: I/O error, dev hdd, sector 52
[  272.153283] hdd: tray open
[  272.153292] end_request: I/O error, dev hdd, sector 56
[  272.153605] hdd: tray open
[  272.153614] end_request: I/O error, dev hdd, sector 60
[  272.159309] hdd: tray open
[  272.159326] end_request: I/O error, dev hdd, sector 0
[  272.159673] hdd: tray open
[  272.159687] end_request: I/O error, dev hdd, sector 4
[  272.161216] hdd: tray open
[  272.161234] end_request: I/O error, dev hdd, sector 0
[  272.161580] hdd: tray open
[  272.161594] end_request: I/O error, dev hdd, sector 4
[  272.162993] hdd: tray open
[  272.163011] end_request: I/O error, dev hdd, sector 0
[  272.163351] hdd: tray open
[  272.163364] end_request: I/O error, dev hdd, sector 4
[  312.244917] hdc: tray open
[  312.244949] end_request: I/O error, dev hdc, sector 0
[  312.244963] printk: 41 messages suppressed.
[  312.244975] Buffer I/O error on device hdc, logical block 0
[  312.245339] hdc: tray open
[  312.245350] end_request: I/O error, dev hdc, sector 4
[  312.245362] Buffer I/O error on device hdc, logical block 1
[  312.245711] hdc: tray open
[  312.245719] end_request: I/O error, dev hdc, sector 8
[  312.245731] Buffer I/O error on device hdc, logical block 2
[  312.246062] hdc: tray open
[  312.246071] end_request: I/O error, dev hdc, sector 12
[  312.246083] Buffer I/O error on device hdc, logical block 3
[  312.246426] hdc: tray open
[  312.246434] end_request: I/O error, dev hdc, sector 16
[  312.246446] Buffer I/O error on device hdc, logical block 4
[  312.246789] hdc: tray open
[  312.246798] end_request: I/O error, dev hdc, sector 20
[  312.246809] Buffer I/O error on device hdc, logical block 5
[  312.247140] hdc: tray open
[  312.247149] end_request: I/O error, dev hdc, sector 24
[  312.247162] Buffer I/O error on device hdc, logical block 6
[  312.247492] hdc: tray open
[  312.247501] end_request: I/O error, dev hdc, sector 28
[  312.247512] Buffer I/O error on device hdc, logical block 7
[  312.247895] hdc: tray open
[  312.247911] end_request: I/O error, dev hdc, sector 32
[  312.248271] hdc: tray open
[  312.248287] end_request: I/O error, dev hdc, sector 36
[  312.248641] hdc: tray open
[  312.248651] end_request: I/O error, dev hdc, sector 40
[  312.248982] hdc: tray open
[  312.248990] end_request: I/O error, dev hdc, sector 44
[  312.249323] hdc: tray open
[  312.249332] end_request: I/O error, dev hdc, sector 48
[  312.249665] hdc: tray open
[  312.249674] end_request: I/O error, dev hdc, sector 52
[  312.250008] hdc: tray open
[  312.250017] end_request: I/O error, dev hdc, sector 56
[  312.250352] hdc: tray open
[  312.250360] end_request: I/O error, dev hdc, sector 60
[  312.259286] hdc: tray open
[  312.259308] end_request: I/O error, dev hdc, sector 0
[  312.259685] hdc: tray open
[  312.259695] end_request: I/O error, dev hdc, sector 4
[  312.260817] hdc: tray open
[  312.260835] end_request: I/O error, dev hdc, sector 0
[  312.261184] hdc: tray open
[  312.261198] end_request: I/O error, dev hdc, sector 4
[  312.262704] hdc: tray open
[  312.262723] end_request: I/O error, dev hdc, sector 0
[  312.263162] hdc: tray open
[  312.263178] end_request: I/O error, dev hdc, sector 4
[  312.275937] hdd: tray open
[  312.275961] end_request: I/O error, dev hdd, sector 0
[  312.276328] hdd: tray open
[  312.276344] end_request: I/O error, dev hdd, sector 4
[  312.276766] hdd: tray open
[  312.276779] end_request: I/O error, dev hdd, sector 8
[  312.277114] hdd: tray open
[  312.277123] end_request: I/O error, dev hdd, sector 12
[  312.277454] hdd: tray open
[  312.277463] end_request: I/O error, dev hdd, sector 16
[  312.277785] hdd: tray open
[  312.277794] end_request: I/O error, dev hdd, sector 20
[  312.278125] hdd: tray open
[  312.278134] end_request: I/O error, dev hdd, sector 24
[  312.278447] hdd: tray open
[  312.278456] end_request: I/O error, dev hdd, sector 28
[  312.278769] hdd: tray open
[  312.278778] end_request: I/O error, dev hdd, sector 32
[  312.279091] hdd: tray open
[  312.279100] end_request: I/O error, dev hdd, sector 36
[  312.279413] hdd: tray open
[  312.279421] end_request: I/O error, dev hdd, sector 40
[  312.279745] hdd: tray open
[  312.279755] end_request: I/O error, dev hdd, sector 44
[  312.280075] hdd: tray open
[  312.280084] end_request: I/O error, dev hdd, sector 48
[  312.280397] hdd: tray open
[  312.280406] end_request: I/O error, dev hdd, sector 52
[  312.280719] hdd: tray open
[  312.280728] end_request: I/O error, dev hdd, sector 56
[  312.281041] hdd: tray open
[  312.281049] end_request: I/O error, dev hdd, sector 60
[  312.286640] hdd: tray open
[  312.286659] end_request: I/O error, dev hdd, sector 0
[  312.287006] hdd: tray open
[  312.287020] end_request: I/O error, dev hdd, sector 4
[  312.288543] hdd: tray open
[  312.288563] end_request: I/O error, dev hdd, sector 0
[  312.288904] hdd: tray open
[  312.288918] end_request: I/O error, dev hdd, sector 4
[  312.290346] hdd: tray open
[  312.290364] end_request: I/O error, dev hdd, sector 0
[  312.290712] hdd: tray open
[  312.290728] end_request: I/O error, dev hdd, sector 4
[  326.288056] hdc: tray open
[  326.288086] end_request: I/O error, dev hdc, sector 0
[  326.288100] printk: 36 messages suppressed.
[  326.288112] Buffer I/O error on device hdc, logical block 0
[  326.288466] hdc: tray open
[  326.288478] end_request: I/O error, dev hdc, sector 4
[  326.288491] Buffer I/O error on device hdc, logical block 1
[  326.288838] hdc: tray open
[  326.288846] end_request: I/O error, dev hdc, sector 8
[  326.288858] Buffer I/O error on device hdc, logical block 2
[  326.289201] hdc: tray open
[  326.289210] end_request: I/O error, dev hdc, sector 12
[  326.289542] hdc: tray open
[  326.289551] end_request: I/O error, dev hdc, sector 16
[  326.289884] hdc: tray open
[  326.289893] end_request: I/O error, dev hdc, sector 20
[  326.290226] hdc: tray open
[  326.290234] end_request: I/O error, dev hdc, sector 24
[  326.290568] hdc: tray open
[  326.290576] end_request: I/O error, dev hdc, sector 28
[  326.290909] hdc: tray open
[  326.290918] end_request: I/O error, dev hdc, sector 32
[  326.291264] hdc: tray open
[  326.291278] end_request: I/O error, dev hdc, sector 36
[  326.291635] hdc: tray open
[  326.291644] end_request: I/O error, dev hdc, sector 40
[  326.291977] hdc: tray open
[  326.291985] end_request: I/O error, dev hdc, sector 44
[  326.292319] hdc: tray open
[  326.292327] end_request: I/O error, dev hdc, sector 48
[  326.292660] hdc: tray open
[  326.292669] end_request: I/O error, dev hdc, sector 52
[  326.293002] hdc: tray open
[  326.293011] end_request: I/O error, dev hdc, sector 56
[  326.293345] hdc: tray open
[  326.293354] end_request: I/O error, dev hdc, sector 60
[  326.300146] hdc: tray open
[  326.300165] end_request: I/O error, dev hdc, sector 0
[  326.300511] hdc: tray open
[  326.300521] end_request: I/O error, dev hdc, sector 4
[  326.301650] hdc: tray open
[  326.301668] end_request: I/O error, dev hdc, sector 0
[  326.302034] hdc: tray open
[  326.302047] end_request: I/O error, dev hdc, sector 4
[  326.303575] hdc: tray open
[  326.303595] end_request: I/O error, dev hdc, sector 0
[  326.303954] hdc: tray open
[  326.303968] end_request: I/O error, dev hdc, sector 4
[  326.317562] hdd: tray open
[  326.317585] end_request: I/O error, dev hdd, sector 0
[  326.317951] hdd: tray open
[  326.317967] end_request: I/O error, dev hdd, sector 4
[  326.318332] hdd: tray open
[  326.318345] end_request: I/O error, dev hdd, sector 8
[  326.318679] hdd: tray open
[  326.318689] end_request: I/O error, dev hdd, sector 12
[  326.319021] hdd: tray open
[  326.319031] end_request: I/O error, dev hdd, sector 16
[  326.319359] hdd: tray open
[  326.319369] end_request: I/O error, dev hdd, sector 20
[  326.319700] hdd: tray open
[  326.319709] end_request: I/O error, dev hdd, sector 24
[  326.320031] hdd: tray open
[  326.320040] end_request: I/O error, dev hdd, sector 28
[  326.320362] hdd: tray open
[  326.320370] end_request: I/O error, dev hdd, sector 32
[  326.320693] hdd: tray open
[  326.320702] end_request: I/O error, dev hdd, sector 36
[  326.321024] hdd: tray open
[  326.321033] end_request: I/O error, dev hdd, sector 40
[  326.321355] hdd: tray open
[  326.321364] end_request: I/O error, dev hdd, sector 44
[  326.321686] hdd: tray open
[  326.321695] end_request: I/O error, dev hdd, sector 48
[  326.322017] hdd: tray open
[  326.322027] end_request: I/O error, dev hdd, sector 52
[  326.322348] hdd: tray open
[  326.322358] end_request: I/O error, dev hdd, sector 56
[  326.322680] hdd: tray open
[  326.322689] end_request: I/O error, dev hdd, sector 60
[  326.328625] hdd: tray open
[  326.328644] end_request: I/O error, dev hdd, sector 0
[  326.328998] hdd: tray open
[  326.329013] end_request: I/O error, dev hdd, sector 4
[  326.330441] hdd: tray open
[  326.330458] end_request: I/O error, dev hdd, sector 0
[  326.330805] hdd: tray open
[  326.330820] end_request: I/O error, dev hdd, sector 4
[  326.332258] hdd: tray open
[  326.332276] end_request: I/O error, dev hdd, sector 0
[  326.332632] hdd: tray open
[  326.332647] end_request: I/O error, dev hdd, sector 4
[  352.634066] hdc: tray open
[  352.634097] end_request: I/O error, dev hdc, sector 0
[  352.634112] printk: 41 messages suppressed.
[  352.634124] Buffer I/O error on device hdc, logical block 0
[  352.634488] hdc: tray open
[  352.634498] end_request: I/O error, dev hdc, sector 4
[  352.634510] Buffer I/O error on device hdc, logical block 1
[  352.634848] hdc: tray open
[  352.634857] end_request: I/O error, dev hdc, sector 8
[  352.634869] Buffer I/O error on device hdc, logical block 2
[  352.635228] hdc: tray open
[  352.635241] end_request: I/O error, dev hdc, sector 12
[  352.635254] Buffer I/O error on device hdc, logical block 3
[  352.635594] hdc: tray open
[  352.635603] end_request: I/O error, dev hdc, sector 16
[  352.635615] Buffer I/O error on device hdc, logical block 4
[  352.635946] hdc: tray open
[  352.635954] end_request: I/O error, dev hdc, sector 20
[  352.636287] hdc: tray open
[  352.636296] end_request: I/O error, dev hdc, sector 24
[  352.636629] hdc: tray open
[  352.636637] end_request: I/O error, dev hdc, sector 28
[  352.636970] hdc: tray open
[  352.636979] end_request: I/O error, dev hdc, sector 32
[  352.637312] hdc: tray open
[  352.637321] end_request: I/O error, dev hdc, sector 36
[  352.637654] hdc: tray open
[  352.637662] end_request: I/O error, dev hdc, sector 40
[  352.637997] hdc: tray open
[  352.638006] end_request: I/O error, dev hdc, sector 44
[  352.638339] hdc: tray open
[  352.638348] end_request: I/O error, dev hdc, sector 48
[  352.638682] hdc: tray open
[  352.638691] end_request: I/O error, dev hdc, sector 52
[  352.639027] hdc: tray open
[  352.639036] end_request: I/O error, dev hdc, sector 56
[  352.639368] hdc: tray open
[  352.639378] end_request: I/O error, dev hdc, sector 60
[  352.647098] hdc: tray open
[  352.647118] end_request: I/O error, dev hdc, sector 0
[  352.647467] hdc: tray open
[  352.647479] end_request: I/O error, dev hdc, sector 4
[  352.649105] hdc: tray open
[  352.649126] end_request: I/O error, dev hdc, sector 0
[  352.649472] hdc: tray open
[  352.649483] end_request: I/O error, dev hdc, sector 4
[  352.650596] hdc: tray open
[  352.650614] end_request: I/O error, dev hdc, sector 0
[  352.650965] hdc: tray open
[  352.650978] end_request: I/O error, dev hdc, sector 4
[  352.664188] hdd: tray open
[  352.664213] end_request: I/O error, dev hdd, sector 0
[  352.664585] hdd: tray open
[  352.664599] end_request: I/O error, dev hdd, sector 4
[  352.664948] hdd: tray open
[  352.664961] end_request: I/O error, dev hdd, sector 8
[  352.665287] hdd: tray open
[  352.665296] end_request: I/O error, dev hdd, sector 12
[  352.665627] hdd: tray open
[  352.665636] end_request: I/O error, dev hdd, sector 16
[  352.665949] hdd: tray open
[  352.665958] end_request: I/O error, dev hdd, sector 20
[  352.666281] hdd: tray open
[  352.666290] end_request: I/O error, dev hdd, sector 24
[  352.666612] hdd: tray open
[  352.666621] end_request: I/O error, dev hdd, sector 28
[  352.666933] hdd: tray open
[  352.666943] end_request: I/O error, dev hdd, sector 32
[  352.667292] hdd: tray open
[  352.667302] end_request: I/O error, dev hdd, sector 36
[  352.667614] hdd: tray open
[  352.667623] end_request: I/O error, dev hdd, sector 40
[  352.668002] hdd: tray open
[  352.668011] end_request: I/O error, dev hdd, sector 44
[  352.668324] hdd: tray open
[  352.668334] end_request: I/O error, dev hdd, sector 48
[  352.668646] hdd: tray open
[  352.668655] end_request: I/O error, dev hdd, sector 52
[  352.668968] hdd: tray open
[  352.668977] end_request: I/O error, dev hdd, sector 56
[  352.669290] hdd: tray open
[  352.669299] end_request: I/O error, dev hdd, sector 60
[  352.674890] hdd: tray open
[  352.674908] end_request: I/O error, dev hdd, sector 0
[  352.675255] hdd: tray open
[  352.675269] end_request: I/O error, dev hdd, sector 4
[  352.676706] hdd: tray open
[  352.676724] end_request: I/O error, dev hdd, sector 0
[  352.677071] hdd: tray open
[  352.677085] end_request: I/O error, dev hdd, sector 4
[  352.678457] hdd: tray open
[  352.678475] end_request: I/O error, dev hdd, sector 0
[  352.678824] hdd: tray open
[  352.678837] end_request: I/O error, dev hdd, sector 4
[  370.598988] hdc: tray open
[  370.599018] end_request: I/O error, dev hdc, sector 0
[  370.599033] printk: 39 messages suppressed.
[  370.599044] Buffer I/O error on device hdc, logical block 0
[  370.599398] hdc: tray open
[  370.599409] end_request: I/O error, dev hdc, sector 4
[  370.599421] Buffer I/O error on device hdc, logical block 1
[  370.599770] hdc: tray open
[  370.599779] end_request: I/O error, dev hdc, sector 8
[  370.599790] Buffer I/O error on device hdc, logical block 2
[  370.600135] hdc: tray open
[  370.600146] end_request: I/O error, dev hdc, sector 12
[  370.600159] Buffer I/O error on device hdc, logical block 3
[  370.600518] hdc: tray open
[  370.600528] end_request: I/O error, dev hdc, sector 16
[  370.600871] hdc: tray open
[  370.600880] end_request: I/O error, dev hdc, sector 20
[  370.601213] hdc: tray open
[  370.601222] end_request: I/O error, dev hdc, sector 24
[  370.601554] hdc: tray open
[  370.601564] end_request: I/O error, dev hdc, sector 28
[  370.601896] hdc: tray open
[  370.601905] end_request: I/O error, dev hdc, sector 32
[  370.602238] hdc: tray open
[  370.602247] end_request: I/O error, dev hdc, sector 36
[  370.602579] hdc: tray open
[  370.602589] end_request: I/O error, dev hdc, sector 40
[  370.602921] hdc: tray open
[  370.602930] end_request: I/O error, dev hdc, sector 44
[  370.603263] hdc: tray open
[  370.603272] end_request: I/O error, dev hdc, sector 48
[  370.603604] hdc: tray open
[  370.603613] end_request: I/O error, dev hdc, sector 52
[  370.603948] hdc: tray open
[  370.603957] end_request: I/O error, dev hdc, sector 56
[  370.604292] hdc: tray open
[  370.604301] end_request: I/O error, dev hdc, sector 60
[  370.611295] hdc: tray open
[  370.611316] end_request: I/O error, dev hdc, sector 0
[  370.611664] hdc: tray open
[  370.611673] end_request: I/O error, dev hdc, sector 4
[  370.612816] hdc: tray open
[  370.612835] end_request: I/O error, dev hdc, sector 0
[  370.613186] hdc: tray open
[  370.613200] end_request: I/O error, dev hdc, sector 4
[  370.614703] hdc: tray open
[  370.614722] end_request: I/O error, dev hdc, sector 0
[  370.615072] hdc: tray open
[  370.615086] end_request: I/O error, dev hdc, sector 4
[  370.628154] hdd: tray open
[  370.628179] end_request: I/O error, dev hdd, sector 0
[  370.628532] hdd: tray open
[  370.628541] end_request: I/O error, dev hdd, sector 4
[  370.628871] hdd: tray open
[  370.628880] end_request: I/O error, dev hdd, sector 8
[  370.629211] hdd: tray open
[  370.629220] end_request: I/O error, dev hdd, sector 12
[  370.629551] hdd: tray open
[  370.629560] end_request: I/O error, dev hdd, sector 16
[  370.629892] hdd: tray open
[  370.629901] end_request: I/O error, dev hdd, sector 20
[  370.630232] hdd: tray open
[  370.630241] end_request: I/O error, dev hdd, sector 24
[  370.630563] hdd: tray open
[  370.630572] end_request: I/O error, dev hdd, sector 28
[  370.630885] hdd: tray open
[  370.630894] end_request: I/O error, dev hdd, sector 32
[  370.631207] hdd: tray open
[  370.631215] end_request: I/O error, dev hdd, sector 36
[  370.631529] hdd: tray open
[  370.631538] end_request: I/O error, dev hdd, sector 40
[  370.631851] hdd: tray open
[  370.631860] end_request: I/O error, dev hdd, sector 44
[  370.632173] hdd: tray open
[  370.632183] end_request: I/O error, dev hdd, sector 48
[  370.632504] hdd: tray open
[  370.632513] end_request: I/O error, dev hdd, sector 52
[  370.632826] hdd: tray open
[  370.632836] end_request: I/O error, dev hdd, sector 56
[  370.633148] hdd: tray open
[  370.633157] end_request: I/O error, dev hdd, sector 60
[  370.638669] hdd: tray open
[  370.638687] end_request: I/O error, dev hdd, sector 0
[  370.639033] hdd: tray open
[  370.639047] end_request: I/O error, dev hdd, sector 4
[  370.640458] hdd: tray open
[  370.640475] end_request: I/O error, dev hdd, sector 0
[  370.640823] hdd: tray open
[  370.640836] end_request: I/O error, dev hdd, sector 4
[  370.642219] hdd: tray open
[  370.642237] end_request: I/O error, dev hdd, sector 0
[  370.642584] hdd: tray open
[  370.642598] end_request: I/O error, dev hdd, sector 4

```

---

### Post by noob12 on 2007-08-30
You seem to have posted the output of **lspci -n** not **lspci -nn**.   If you use the **-nn** we would normally be able to see the device names, which might help.  I traced device ids at pcidatabase.com, and I don't see an ethernet device in what you have shown.   I'm also not seeing anything in the dmesg related to your ethernet device but this might just indicate absence of a driver.

There is some oddness around here in your dmesg output.  This might be your ethernet device.  I can't tell.
> 
[   25.170718] PCI: BIOS reporting unknown device 00:58
[   25.170727] PCI: Device 0000:00:0b.1 not found by BIOS


---

### Post by Zuinig on 2007-08-30
I did use the -nn option, but it gives the same output as -n.
However, after looking through the command options, I tried
lspci -v
Does this help?
Is the card not supported bij Ubuntu? Do I need to try it in a different PCI slot? Or is it just not functioning anymore?

Here's the lspci -v output:

```
0000:00:00.0 Host bridge: ALi Corporation M1541 (rev 04)
        Subsystem: ALi Corporation ALI M1541 Aladdin V/V+ AGP System Controller
        Flags: bus master, slow devsel, latency 64
        Memory at d0000000 (32-bit, non-prefetchable) [size=256M]
        Capabilities: <available only to root>

0000:00:01.0 PCI bridge: ALi Corporation M1541 PCI to AGP Controller (rev 04) (prog-if 00 [Normal decode])
        Flags: bus master, slow devsel, latency 64
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
        Memory behind bridge: cc000000-cfffffff
        Prefetchable memory behind bridge: e7f00000-e7ffffff

0000:00:02.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03) (prog-if 10 [OHCI])
        Flags: bus master, medium devsel, latency 64, IRQ 9
        Memory at cb800000 (32-bit, non-prefetchable) [size=4K]

0000:00:03.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
        Subsystem: ALi Corporation M7101 Power Management Controller [PMU]
        Flags: medium devsel
        I/O ports at <ignored>
        I/O ports at <ignored>

0000:00:07.0 ISA bridge: ALi Corporation M1533 PCI to ISA Bridge [Aladdin IV] (rev c3)
        Flags: bus master, medium devsel, latency 0

0000:00:0a.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 08)
        Subsystem: Ensoniq Creative Sound Blaster AudioPCI64V, AudioPCI128
        Flags: bus master, slow devsel, latency 32, IRQ 5
        I/O ports at d800 [size=64]
        Capabilities: <available only to root>

0000:00:0b.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 61) (prog-if 00 [UHCI])
        Subsystem: SiteCom Europe BV CN-029 USB2.0 4 port PCI Card
        Flags: bus master, medium devsel, latency 32, IRQ 11
        I/O ports at d400 [size=32]
        Capabilities: <available only to root>

0000:00:0b.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 61) (prog-if 00 [UHCI])
        Subsystem: SiteCom Europe BV CN-029 USB2.0 4 port PCI Card
        Flags: bus master, medium devsel, latency 32, IRQ 5
        I/O ports at d000 [size=32]
        Capabilities: <available only to root>

0000:00:0b.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 63) (prog-if 20 [EHCI])
        Subsystem: SiteCom Europe BV CN-029 USB 2.0 4 port PCI Card
        Flags: bus master, medium devsel, latency 32, IRQ 10
        Memory at cb000000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <available only to root>

0000:00:0d.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 02)
        Subsystem: TERRATEC Electronic GmbH: Unknown device 1118
        Flags: bus master, medium devsel, latency 32, IRQ 10
        Memory at e7000000 (32-bit, prefetchable) [size=4K]

0000:00:0d.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 02)
        Subsystem: TERRATEC Electronic GmbH: Unknown device 1118
        Flags: bus master, medium devsel, latency 32, IRQ 10
        Memory at e6800000 (32-bit, prefetchable) [size=4K]

0000:00:0f.0 IDE interface: ALi Corporation M5229 IDE (rev c1) (prog-if 8a [Master SecP PriP])
        Flags: bus master, medium devsel, latency 32
        I/O ports at b800 [size=16]

0000:01:00.0 VGA compatible controller: S3 Inc. 86c368 [Trio 3D/2X] (rev 02) (prog-if 00 [VGA])
        Subsystem: S3 Inc. Trio3D/2X
        Flags: bus master, medium devsel, latency 64
        Memory at cc000000 (32-bit, non-prefetchable) [size=64M]
        Expansion ROM at e7ff0000 [disabled] [size=64K]
        Capabilities: <available only to root>

```

---

### Post by Zuinig on 2007-09-01
Problem solved!!!

I took off the case, pulled out the ethernetcard, carefully wiped it clean using a soft brush, plugged it into a different PCI slot, restarded PC, no result, then took it out again and plugged it into the original PCI slot, restarted PC and YES: ONLINE!

Anyway, thanks for your help!

---

### Post by noob12 on 2007-09-01
Glad to hear you resolved it!

---

