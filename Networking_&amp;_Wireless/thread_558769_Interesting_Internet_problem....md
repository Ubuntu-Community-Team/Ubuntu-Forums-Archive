---
title: "Interesting Internet problem..."
date: 2007-09-24
forum: Networking &amp; Wireless
---

### Post by ThinAlbert14 on 2007-09-24
I'm a new user to Feisty Fawn and I'm running it on a dual boot with Win XP but heres the problem.  When I first installed 7.04 I lost my internet connection in both Win XP and Unbuntu.  So I got my motherboard disk and i was going to try and re-install my network card drivers but when I started up my computer the internet was magically working all of a sudden in Win XP. So proceeded to boot in Unbuntu and the internet was workin there fine too.  So I had 200 undates that it said i needed to install so I did so and then I restarted my computer back to ubuntu again and when it loaded up I had lost my internet connection.  So I restarted back to Win XP and my internet was gone there too.  Any thoughts...

When trying some of the fixes on other pages I got these results:
Output from lspci -nn :



00:00.0 Host bridge [0600]: VIA Technologies, Inc. K8M890CE Host Bridge [1106:0336]

00:00.1 Host bridge [0600]: VIA Technologies, Inc. K8M890CE Host Bridge [1106:1336]

00:00.2 Host bridge [0600]: VIA Technologies, Inc. K8M890CE Host Bridge [1106:2336]

00:00.3 Host bridge [0600]: VIA Technologies, Inc. K8M890CE Host Bridge [1106:3336]

00:00.4 Host bridge [0600]: VIA Technologies, Inc. K8M890CE Host Bridge [1106:4336]

00:00.5 PIC [0800]: VIA Technologies, Inc. K8M890CE I/O APIC Interrupt Controller [1106:5336]

00:00.6 Host bridge [0600]: VIA Technologies, Inc. Unknown device [1106:6290]

00:00.7 Host bridge [0600]: VIA Technologies, Inc. K8M890CE Host Bridge [1106:7336]

00:01.0 PCI bridge [0604]: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South] [1106:b188]

00:02.0 PCI bridge [0604]: VIA Technologies, Inc. K8T890 PCI to PCI Bridge Controller [1106:a238]

00:03.0 PCI bridge [0604]: VIA Technologies, Inc. K8T890 PCI to PCI Bridge Controller [1106:c238]

00:0f.0 IDE interface [0101]: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller [1106:3149] (rev 80)

00:0f.1 IDE interface [0101]: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE [1106:0571] (rev 06)

00:10.0 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 81)

00:10.1 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 81)

00:10.2 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 81)

00:10.3 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 81)

00:10.4 USB Controller [0c03]: VIA Technologies, Inc. USB 2.0 [1106:3104] (rev 86)

00:11.0 ISA bridge [0601]: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South] [1106:3227]

00:11.5 Multimedia audio controller [0401]: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller [1106:3059] (rev 60)

00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]

00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]

00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]

00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]

01:00.0 VGA compatible controller [0300]: VIA Technologies, Inc. Unknown device [1106:3230] (rev 11)



Output for sudo ethtool eth0



Settings for eth0:

Cannot get device settings: No such device

Cannot get wake-on-lan settings: No such device

Cannot get message level: No such device

Cannot get link status: No such device

No data available



Output for ifconfig -a



lo        Link encap:Local Loopback  

          inet addr:127.0.0.1  Mask:255.0.0.0

          inet6 addr: ::1/128 Scope:Host

          UP LOOPBACK RUNNING  MTU:16436  Metric:1

          RX packets:4 errors:0 dropped:0 overruns:0 frame:0

          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0 

          RX bytes:200 (200.0 b)  TX bytes:200 (200.0 b)

---

### Post by noob12 on 2007-09-24
If you have an onboard LAN make sure it is enabled in the BIOS. 

It doesn't seem to showing up in your lspci output so my guess is either it is disabled in the BIOS or there is some kind of PCI routing issue during boot.

Once you've verified the BIOS settings, if it still doesn't show up post the output of these:

```

lspci -nn

sudo lshw -C network

dmesg

```

---

### Post by ThinAlbert14 on 2007-09-27
I checked my bios and it seemed like everything than need to be enabled was so I don't think that is the problem.  But here is the output using the code you ask for but the second one didn't give me any output.  It seem like it went thru some kinda process but it didn't output anything.

 lspci -nn

00:00.0 Host bridge [0600]: VIA Technologies, Inc. K8M890CE Host Bridge [1106:0336]
00:00.1 Host bridge [0600]: VIA Technologies, Inc. K8M890CE Host Bridge [1106:1336]
00:00.2 Host bridge [0600]: VIA Technologies, Inc. K8M890CE Host Bridge [1106:2336]
00:00.3 Host bridge [0600]: VIA Technologies, Inc. K8M890CE Host Bridge [1106:3336]
00:00.4 Host bridge [0600]: VIA Technologies, Inc. K8M890CE Host Bridge [1106:4336]
00:00.5 PIC [0800]: VIA Technologies, Inc. K8M890CE I/O APIC Interrupt Controller [1106:5336]
00:00.6 Host bridge [0600]: VIA Technologies, Inc. Unknown device [1106:6290]
00:00.7 Host bridge [0600]: VIA Technologies, Inc. K8M890CE Host Bridge [1106:7336]
00:01.0 PCI bridge [0604]: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South] [1106:b188]
00:02.0 PCI bridge [0604]: VIA Technologies, Inc. K8T890 PCI to PCI Bridge Controller [1106:a238]
00:03.0 PCI bridge [0604]: VIA Technologies, Inc. K8T890 PCI to PCI Bridge Controller [1106:c238]
00:0f.0 IDE interface [0101]: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller [1106:3149] (rev 80)
00:0f.1 IDE interface [0101]: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE [1106:0571] (rev 06)
00:10.0 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 81)
00:10.1 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 81)
00:10.2 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 81)
00:10.3 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 81)
00:10.4 USB Controller [0c03]: VIA Technologies, Inc. USB 2.0 [1106:3104] (rev 86)
00:11.0 ISA bridge [0601]: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South] [1106:3227]
00:11.5 Multimedia audio controller [0401]: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller [1106:3059] (rev 60)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
01:00.0 VGA compatible controller [0300]: VIA Technologies, Inc. Unknown device [1106:3230] (rev 11)

---

### Post by ThinAlbert14 on 2007-09-27
dmesg

[18.213551] Freeing unused kernel memory: 304k freed
[   18.231579] input: AT Translated Set 2 keyboard as /class/input/input1
[   19.397169] Capability LSM initialized
[   19.434251] ACPI: Processor [P001] (supports 16 throttling states)
[   19.435278] ACPI: Thermal Zone [THRM] (30 C)
[   19.926876] SCSI subsystem initialized
[   19.932210] libata version 2.20 loaded.
[   19.933632] sata_via 0000:00:0f.0: version 2.1
[   19.933658] ACPI: PCI Interrupt 0000:00:0f.0[B] -> GSI 20 (level, low) -> IRQ 20
[   19.933681] sata_via 0000:00:0f.0: routed to hard irq line 5
[   19.933749] ata1: SATA max UDMA/133 cmd 0x000000000001e800 ctl 0x000000000001e402 bmdma 0x000000000001d400 irq 20
[   19.933781] ata2: SATA max UDMA/133 cmd 0x000000000001e000 ctl 0x000000000001d802 bmdma 0x000000000001d408 irq 20
[   19.933801] scsi0 : sata_via
[   19.981472] usbcore: registered new interface driver usbfs
[   19.981501] usbcore: registered new interface driver hub
[   19.981527] usbcore: registered new device driver usb
[   19.982568] USB Universal Host Controller Interface driver v3.0
[   19.998364] Floppy drive(s): fd0 is 1.44M
[   20.021650] FDC 0 is a post-1991 82077
[   20.137729] ata1: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[   20.148417] ATA: abnormal status 0x7F on port 0x000000000001e807
[   20.148433] scsi1 : sata_via
[   20.353611] ata2: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[   20.364296] ATA: abnormal status 0x7F on port 0x000000000001e007
[   20.367498] ACPI: PCI Interrupt 0000:00:10.0[A] -> GSI 21 (level, low) -> IRQ 21
[   20.367514] uhci_hcd 0000:00:10.0: UHCI Host Controller
[   20.367682] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
[   20.367713] uhci_hcd 0000:00:10.0: irq 21, io base 0x0000c800
[   20.367847] usb usb1: configuration #1 chosen from 1 choice
[   20.367873] hub 1-0:1.0: USB hub found
[   20.367881] hub 1-0:1.0: 2 ports detected
[   20.473707] ACPI: PCI Interrupt 0000:00:10.1[A] -> GSI 21 (level, low) -> IRQ 21
[   20.473721] uhci_hcd 0000:00:10.1: UHCI Host Controller
[   20.473745] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
[   20.473768] uhci_hcd 0000:00:10.1: irq 21, io base 0x0000c400
[   20.473859] usb usb2: configuration #1 chosen from 1 choice
[   20.473882] hub 2-0:1.0: USB hub found
[   20.473889] hub 2-0:1.0: 2 ports detected
[   20.581614] ACPI: PCI Interrupt 0000:00:10.2[B] -> GSI 21 (level, low) -> IRQ 21
[   20.581628] uhci_hcd 0000:00:10.2: UHCI Host Controller
[   20.581648] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
[   20.581670] uhci_hcd 0000:00:10.2: irq 21, io base 0x0000c000
[   20.581763] usb usb3: configuration #1 chosen from 1 choice
[   20.581787] hub 3-0:1.0: USB hub found
[   20.581793] hub 3-0:1.0: 2 ports detected
[   20.689555] ACPI: PCI Interrupt 0000:00:10.3[B] -> GSI 21 (level, low) -> IRQ 21
[   20.689570] uhci_hcd 0000:00:10.3: UHCI Host Controller
[   20.689593] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
[   20.689616] uhci_hcd 0000:00:10.3: irq 21, io base 0x0000b800
[   20.689705] usb usb4: configuration #1 chosen from 1 choice
[   20.689733] hub 4-0:1.0: USB hub found
[   20.689740] hub 4-0:1.0: 2 ports detected
[   20.797508] VP_IDE: IDE controller at PCI slot 0000:00:0f.1
[   20.797530] ACPI: PCI Interrupt 0000:00:0f.1[A] -> GSI 20 (level, low) -> IRQ 20
[   20.797544] VP_IDE: chipset revision 6
[   20.797547] VP_IDE: not 100% native mode: will probe irqs later
[   20.797557] VP_IDE: VIA vt8237 (rev 00) IDE UDMA133 controller on pci0000:00:0f.1
[   20.797566]     ide0: BM-DMA at 0xfc00-0xfc07, BIOS settings: hda:DMA, hdb:DMA
[   20.797577]     ide1: BM-DMA at 0xfc08-0xfc0f, BIOS settings: hdc:DMA, hdd:DMA
[   20.797584] Probing IDE interface ide0...
[   21.221233] hda: WDC WD400BB-22DEA0, ATA DISK drive
[   21.229149] usb 3-1: new full speed USB device using uhci_hcd and address 2
[   21.419356] usb 3-1: configuration #1 chosen from 1 choice
[   21.505082] hdb: WDC WD3200JB-00KFA0, ATA DISK drive
[   21.563231] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   21.592108] Probing IDE interface ide1...
[   21.808897] usbcore: registered new interface driver libusual
[   21.811974] Initializing USB Mass Storage driver...
[   21.812063] scsi2 : SCSI emulation for USB Mass Storage devices
[   21.812138] usb-storage: device found at 2
[   21.812141] usb-storage: waiting for device to settle before scanning
[   21.812126] usbcore: registered new interface driver usb-storage
[   21.812129] USB Mass Storage support registered.
[   22.460593] hdc: TSSTcorpCD/DVDW SH-S182M, ATAPI CD/DVD-ROM drive
[   23.244175] hdd: FX54++W, ATAPI CD/DVD-ROM drive
[   23.300835] ide1 at 0x170-0x177,0x376 on irq 15
[   23.304612] ACPI: PCI Interrupt 0000:00:10.4[C] -> GSI 21 (level, low) -> IRQ 21
[   23.304629] ehci_hcd 0000:00:10.4: EHCI Host Controller
[   23.304666] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 5
[   23.304703] ehci_hcd 0000:00:10.4: irq 21, io mem 0xfcfffc00
[   23.304710] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   23.304805] usb usb5: configuration #1 chosen from 1 choice
[   23.304831] hub 5-0:1.0: USB hub found
[   23.304838] hub 5-0:1.0: 8 ports detected
[   23.313868] hda: max request size: 128KiB
[   23.317095] hda: 78165360 sectors (40020 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(100)
[   23.317103] hda: cache flushes not supported
[   23.317150]  hda: hda1
[   23.333705] hdb: max request size: 512KiB
[   23.333789] hdb: 625142448 sectors (320072 MB) w/8192KiB Cache, CHS=38913/255/63, UDMA(100)
[   23.333869] hdb: cache flushes supported
[   23.333897]  hdb: hdb1 hdb2 hdb3 hdb4 < hdb5 >
[   23.392050] hdc: ATAPI 48X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(33)
[   23.392059] Uniform CD-ROM driver Revision: 3.20
[   23.412878] hdd: ATAPI 54X CD-ROM drive, 128kB Cache, UDMA(33)
[   23.651864] usb 5-5: new high speed USB device using ehci_hcd and address 2
[   23.698687] Attempting manual resume
[   23.698691] swsusp: Resume From Partition 3:69
[   23.698693] PM: Checking swsusp image.
[   23.698876] PM: Resume from disk failed.
[   23.729724] kjournald starting.  Commit interval 5 seconds
[   23.729740] EXT3-fs: mounted filesystem with ordered data mode.
[   23.803858] usb 5-5: configuration #1 chosen from 1 choice
[   23.804468] scsi3 : SCSI emulation for USB Mass Storage devices
[   23.804611] usb 3-1: USB disconnect, address 2
[   23.804834] usb-storage: device found at 2
[   23.804835] usb-storage: waiting for device to settle before scanning
[   28.805230] usb-storage: device scan complete
[   28.809122] scsi 3:0:0:0: Direct-Access     Memorex  TD 2C            1.04 PQ: 0 ANSI: 0 CCS
[   31.993480] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   32.141748] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   32.394015] parport: PnPBIOS parport detected.
[   32.394104] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   32.427558] SCSI device sda: 501760 512-byte hdwr sectors (257 MB)
[   32.429069] sda: Write Protect is off
[   32.429071] sda: Mode Sense: 23 00 00 00
[   32.429073] sda: assuming drive cache: write through
[   32.431179] SCSI device sda: 501760 512-byte hdwr sectors (257 MB)
[   32.431783] sda: Write Protect is off
[   32.431785] sda: Mode Sense: 23 00 00 00
[   32.431787] sda: assuming drive cache: write through
[   32.431791]  sda: sda1
[   32.433189] sd 3:0:0:0: Attached scsi removable disk sda
[   32.460848] input: PC Speaker as /class/input/input2
[   32.523047] sd 3:0:0:0: Attached scsi generic sg0 type 0
[   32.710317] ACPI: PCI Interrupt 0000:00:11.5[C] -> GSI 22 (level, low) -> IRQ 22
[   32.710459] PCI: Setting latency timer of device 0000:00:11.5 to 64
[   33.169580] input: ImPS/2 Logitech Wheel Mouse as /class/input/input3
[   33.367340] fuse init (API version 7.8)
[   33.383891] lp0: using parport0 (interrupt-driven).
[   33.433059] Adding 2634620k swap on /dev/disk/by-uuid/d64e3ae9-0221-4039-9012-0fd24be2518b.  Priority:-1 extents:1 across:2634620k
[   33.533095] EXT3 FS on hdb3, internal journal
[   34.972152] NET: Registered protocol family 17
[   41.207299] ibm_acpi: ec object not found
[   41.250091] No dock devices found.
[   41.264732] Using specific hotkey driver
[   41.400156] input: Power Button (FF) as /class/input/input4
[   41.400412] ACPI: Power Button (FF) [PWRF]
[   41.401656] input: Sleep Button (CM) as /class/input/input5
[   41.401916] ACPI: Sleep Button (CM) [SLPB]
[   41.430298] input: Power Button (CM) as /class/input/input6
[   41.434472] ACPI: Power Button (CM) [PWRB]
[   41.474060] pcc_acpi: loading...
[   41.669374] powernow-k8: Found 2 AMD Athlon(tm) 64 X2 Dual Core Processor 3800+ processors (version 2.00.00)
[   41.669442] powernow-k8:    0 : fid 0xc (2000 MHz), vid 0xe
[   41.669447] powernow-k8:    1 : fid 0xa (1800 MHz), vid 0x10
[   41.669449] powernow-k8:    2 : fid 0x2 (1000 MHz), vid 0x12
[   53.423746] ppdev: user-space parallel port driver
[   54.224003] Bluetooth: Core ver 2.11
[   54.224073] NET: Registered protocol family 31
[   54.224074] Bluetooth: HCI device and connection manager initialized
[   54.224078] Bluetooth: HCI socket layer initialized
[   54.257262] Bluetooth: L2CAP ver 2.8
[   54.257267] Bluetooth: L2CAP socket layer initialized
[   54.398445] Bluetooth: RFCOMM socket layer initialized
[   54.398471] Bluetooth: RFCOMM TTY layer initialized
[   54.398472] Bluetooth: RFCOMM ver 1.8
[   62.201509] NET: Registered protocol family 10
[   62.201624] lo: Disabled Privacy Extensions
[   63.295057] cdrom: hdc: mrw address space DMA selected
[   63.383252] cdrom: hdc: mrw address space DMA selected
[   63.430660] ISO 9660 Extensions: Microsoft Joliet Level 3
[   63.537060] ISOFS: changing to secondary root
[  339.899573] PM: suspend-to-disk mode set to 'shutdown'
[  339.899708] Disabling non-boot CPUs ...
[  339.986140] CPU 1 is now offline
[  339.986143] SMP alternatives: switching to UP code
[  339.990729] CPU1 is down
[  339.990734] Stopping tasks ... done.
[  340.015631] Shrinking memory... done (12512 pages freed)
[  340.113334] Freed 50048 kbytes in 0.14 seconds (357.48 MB/s)
[  340.113337] Suspending console(s)
[  340.113340] platform bluetooth: freeze
[  340.113347] ac97 0-0:ALC655: freeze
[  340.113353] sd 3:0:0:0: freeze
[  340.113359] usb-storage 5-5:1.0: freeze
[  340.113361] usb 5-5: freeze
[  340.122069] hub 5-0:1.0: freeze
[  340.122071] usb usb5: freeze
[  340.122084] ide-cdrom 1.1: freeze
[  340.122093] ide-cdrom 1.0: freeze
[  340.123078] ide-disk 0.1: freeze
[  340.170390] ide-disk 0.0: freeze
[  340.171252]  usbdev4.1_ep81: PM: suspend 0->1, parent 4-0:1.0 already 2
[  340.171254] hub 4-0:1.0: PM: suspend 2-->1
[  340.171256] hub 4-0:1.0: PM: suspend 2->1, parent usb4 already 2
[  340.171259]  usbdev4.1_ep00: PM: suspend 0->1, parent usb4 already 2
[  340.171261] usb usb4: PM: suspend 2-->1
[  340.171263]  usbdev3.1_ep81: PM: suspend 0->1, parent 3-0:1.0 already 2
[  340.171266] hub 3-0:1.0: PM: suspend 2-->1
[  340.171267] hub 3-0:1.0: PM: suspend 2->1, parent usb3 already 2
[  340.171270]  usbdev3.1_ep00: PM: suspend 0->1, parent usb3 already 2
[  340.171272] usb usb3: PM: suspend 2-->1
[  340.171274]  usbdev2.1_ep81: PM: suspend 0->1, parent 2-0:1.0 already 2
[  340.171276] hub 2-0:1.0: PM: suspend 2-->1
[  340.171278] hub 2-0:1.0: PM: suspend 2->1, parent usb2 already 2
[  340.171281]  usbdev2.1_ep00: PM: suspend 0->1, parent usb2 already 2
[  340.171283] usb usb2: PM: suspend 2-->1
[  340.171286]  usbdev1.1_ep81: PM: suspend 0->1, parent 1-0:1.0 already 2
[  340.171288] hub 1-0:1.0: PM: suspend 2-->1
[  340.171289] hub 1-0:1.0: PM: suspend 2->1, parent usb1 already 2
[  340.171292]  usbdev1.1_ep00: PM: suspend 0->1, parent usb1 already 2
[  340.171294] usb usb1: PM: suspend 2-->1
[  340.171296] platform floppy.0: freeze
[  340.171298] platform vesafb.0: freeze
[  340.171301] i8042 i8042: freeze
[  340.609061] serial8250 serial8250: freeze
[  340.609185] pci_express 0000:00:03.0:pcie02: freeze
[  340.609187] pci_express 0000:00:03.0:pcie00: freeze
[  340.609190] pci_express 0000:00:02.0:pcie02: freeze
[  340.609192] pci_express 0000:00:02.0:pcie00: freeze
[  340.609194] pcspkr pcspkr: freeze
[  340.609202] system 00:10: freeze
[  340.609205] system 00:0f: freeze
[  340.609206] system 00:0e: freeze
[  340.609208] system 00:0d: freeze
[  340.609210] system 00:0c: freeze
[  340.609212] system 00:0b: freeze
[  340.609214] parport_pc 00:0a: freeze
[  340.609783] pnp: Device 00:0a disabled.
[  340.609786] pnp 00:09: freeze
[  340.609787] serial 00:08: freeze
[  340.610324] pnp: Device 00:08 disabled.
[  340.610326] serial 00:07: freeze
[  340.610859] pnp: Device 00:07 disabled.
[  340.610861] pnp 00:06: freeze
[  340.610863] pnp 00:05: freeze
[  340.610865] i8042 aux 00:04: freeze
[  340.610866] i8042 kbd 00:03: freeze
[  340.610868] pnp 00:02: freeze
[  340.610870] pnp 00:01: freeze
[  340.610872] pnp 00:00: freeze
[  340.610874] pci 0000:01:00.0: freeze
[  340.610895] k8temp 0000:00:18.3: freeze
[  340.610904] pci 0000:00:18.2: freeze
[  340.610909] pci 0000:00:18.1: freeze
[  340.610914] pci 0000:00:18.0: freeze
[  340.610923] VIA 82xx Audio 0000:00:11.5: freeze
[  340.611217] ACPI: PCI interrupt for device 0000:00:11.5 disabled
[  340.619805] pci 0000:00:11.0: freeze
[  340.619826] ehci_hcd 0000:00:10.4: freeze
[  340.619849] ACPI: PCI interrupt for device 0000:00:10.4 disabled
[  340.627807] uhci_hcd 0000:00:10.3: freeze
[  340.627830] ACPI: PCI interrupt for device 0000:00:10.3 disabled
[  340.635802] uhci_hcd 0000:00:10.2: freeze
[  340.635825] ACPI: PCI interrupt for device 0000:00:10.2 disabled
[  340.643798] uhci_hcd 0000:00:10.1: freeze
[  340.643821] ACPI: PCI interrupt for device 0000:00:10.1 disabled
[  340.651794] uhci_hcd 0000:00:10.0: freeze
[  340.651817] ACPI: PCI interrupt for device 0000:00:10.0 disabled
[  340.659790] VIA_IDE 0000:00:0f.1: freeze
[  340.659810] sata_via 0000:00:0f.0: freeze
[  340.659830] pcieport-driver 0000:00:03.0: freeze
[  340.659863] pcieport-driver 0000:00:02.0: freeze
[  340.659890] pci 0000:00:01.0: freeze
[  340.659906] pci 0000:00:00.7: freeze
[  340.659918] pci 0000:00:00.6: freeze
[  340.659929] pci 0000:00:00.5: freeze
[  340.659940] pci 0000:00:00.4: freeze
[  340.659951] pci 0000:00:00.3: freeze
[  340.659962] pci 0000:00:00.2: freeze
[  340.659973] pci 0000:00:00.1: freeze
[  340.659984] agpgart-amd64 0000:00:00.0: freeze
[  340.660015] pci_set_power_state(): 0000:00:00.0: state=3, current state=5
[  340.660018] acpi acpi: freeze
[  340.660025] PM: snapshotting memory.
[  340.660027] platform bluetooth: LATE freeze
[  340.660036] platform floppy.0: LATE freeze
[  340.660038] platform vesafb.0: LATE freeze
[  340.660040] i8042 i8042: LATE freeze
[  340.660042] serial8250 serial8250: LATE freeze
[  340.660104] pcspkr pcspkr: LATE freeze
[  340.660108] pci 0000:01:00.0: LATE freeze
[  340.660110] k8temp 0000:00:18.3: LATE freeze
[  340.660112] pci 0000:00:18.2: LATE freeze
[  340.660113] pci 0000:00:18.1: LATE freeze
[  340.660115] pci 0000:00:18.0: LATE freeze
[  340.660117] VIA 82xx Audio 0000:00:11.5: LATE freeze
[  340.660119] pci 0000:00:11.0: LATE freeze
[  340.660121] VIA_IDE 0000:00:0f.1: LATE freeze
[  340.660123] sata_via 0000:00:0f.0: LATE freeze
[  340.660125] pcieport-driver 0000:00:03.0: LATE freeze
[  340.660127] pcieport-driver 0000:00:02.0: LATE freeze
[  340.660129] pci 0000:00:01.0: LATE freeze
[  340.660130] pci 0000:00:00.7: LATE freeze
[  340.660132] pci 0000:00:00.6: LATE freeze
[  340.660134] pci 0000:00:00.5: LATE freeze
[  340.660135] pci 0000:00:00.4: LATE freeze
[  340.660137] pci 0000:00:00.3: LATE freeze
[  340.660139] pci 0000:00:00.2: LATE freeze
[  340.660140] pci 0000:00:00.1: LATE freeze
[  340.660142] agpgart-amd64 0000:00:00.0: LATE freeze
[  340.660338] swsusp: critical section: 
[  340.680690] swsusp: Need to copy 111297 pages
[  340.680693] swsusp: Normal pages needed: 111297 + 1024 + 20, available pages: 117917
[   39.110856] agpgart-amd64 0000:00:00.0: EARLY resume
[   39.110861] pci 0000:00:00.1: EARLY resume
[   39.110863] pci 0000:00:00.2: EARLY resume
[   39.110865] pci 0000:00:00.3: EARLY resume
[   39.110867] pci 0000:00:00.4: EARLY resume
[   39.110869] pci 0000:00:00.5: EARLY resume
[   39.110871] pci 0000:00:00.6: EARLY resume
[   39.110873] pci 0000:00:00.7: EARLY resume
[   39.110875] pci 0000:00:01.0: EARLY resume
[   39.110877] pcieport-driver 0000:00:02.0: EARLY resume
[   39.110879] pcieport-driver 0000:00:03.0: EARLY resume
[   39.110881] sata_via 0000:00:0f.0: EARLY resume
[   39.110883] VIA_IDE 0000:00:0f.1: EARLY resume
[   39.110885] uhci_hcd 0000:00:10.0: EARLY resume
[   39.110887] uhci_hcd 0000:00:10.1: EARLY resume
[   39.110889] uhci_hcd 0000:00:10.2: EARLY resume
[   39.110891] uhci_hcd 0000:00:10.3: EARLY resume
[   39.110893] ehci_hcd 0000:00:10.4: EARLY resume
[   39.110895] pci 0000:00:11.0: EARLY resume
[   39.110901] VIA 82xx Audio 0000:00:11.5: EARLY resume
[   39.110903] pci 0000:00:18.0: EARLY resume
[   39.110905] pci 0000:00:18.1: EARLY resume
[   39.110907] pci 0000:00:18.2: EARLY resume
[   39.110909] k8temp 0000:00:18.3: EARLY resume
[   39.110911] pci 0000:01:00.0: EARLY resume
[   39.110915] pcspkr pcspkr: EARLY resume
[   39.110964] serial8250 serial8250: EARLY resume
[   39.110966] i8042 i8042: EARLY resume
[   39.110968] platform vesafb.0: EARLY resume
[   39.110970] platform floppy.0: EARLY resume
[   39.110980] platform bluetooth: EARLY resume
[   39.110982] PM: Image restored successfully.
[   39.623378] acpi acpi: resuming
[   39.623547] agpgart-amd64 0000:00:00.0: resuming
[   39.623599] pci 0000:00:00.1: resuming
[   39.623615] pci 0000:00:00.2: resuming
[   39.623632] pci 0000:00:00.3: resuming
[   39.623648] pci 0000:00:00.4: resuming
[   39.623665] pci 0000:00:00.5: resuming
[   39.623681] pci 0000:00:00.6: resuming
[   39.623698] pci 0000:00:00.7: resuming
[   39.623714] pci 0000:00:01.0: resuming
[   39.623747] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   39.623750] pcieport-driver 0000:00:02.0: resuming
[   39.623782] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   39.623787] pcieport-driver 0000:00:03.0: resuming
[   39.623826] PCI: Setting latency timer of device 0000:00:03.0 to 64
[   39.623830] sata_via 0000:00:0f.0: resuming
[   39.623869] ACPI: PCI Interrupt 0000:00:0f.0[B] -> GSI 20 (level, low) -> IRQ 20
[   39.623874] VIA_IDE 0000:00:0f.1: resuming
[   39.623910] ACPI: PCI Interrupt 0000:00:0f.1[A] -> GSI 20 (level, low) -> IRQ 20
[   39.623914] uhci_hcd 0000:00:10.0: resuming
[   39.638318] ACPI: PCI Interrupt 0000:00:10.0[A] -> GSI 21 (level, low) -> IRQ 21
[   39.638361] usb usb1: root hub lost power or was reset
[   39.638370] uhci_hcd 0000:00:10.1: resuming
[   39.654309] ACPI: PCI Interrupt 0000:00:10.1[A] -> GSI 21 (level, low) -> IRQ 21
[   39.654350] usb usb2: root hub lost power or was reset
[   39.654357] uhci_hcd 0000:00:10.2: resuming
[   39.670300] ACPI: PCI Interrupt 0000:00:10.2[B] -> GSI 21 (level, low) -> IRQ 21
[   39.670341] usb usb3: root hub lost power or was reset
[   39.670349] uhci_hcd 0000:00:10.3: resuming
[   39.691163] ACPI: PCI Interrupt 0000:00:10.3[B] -> GSI 21 (level, low) -> IRQ 21
[   39.691190] usb usb4: root hub lost power or was reset
[   39.691197] ehci_hcd 0000:00:10.4: resuming
[   39.698700] ACPI: PCI Interrupt 0000:00:10.4[C] -  GSI 21 (level, low) -> IRQ 21
[   39.698720] usb usb5: root hub lost power or was reset
[   39.698728] pci 0000:00:11.0: resuming
[   39.698754] VIA 82xx Audio 0000:00:11.5: resuming
[   39.706712] ACPI: PCI Interrupt 0000:00:11.5[C] -> GSI 22 (level, low) -> IRQ 22
[   39.706716] PCI: Setting latency timer of device 0000:00:11.5 to 64
[   39.708199] pci 0000:00:18.0: resuming
[   39.708206] pci 0000:00:18.1: resuming
[   39.708211] pci 0000:00:18.2: resuming
[   39.708216] k8temp 0000:00:18.3: resuming
[   39.708223] pci 0000:01:00.0: resuming
[   39.708240] pnp 00:00: resuming
[   39.708242] pnp 00:01: resuming
[   39.708243] pnp 00:02: resuming
[   39.708245] i8042 kbd 00:03: resuming
[   39.708260] pnp: Failed to activate device 00:03.
[   39.708262] i8042 aux 00:04: resuming
[   39.708270] pnp: Failed to activate device 00:04.
[   39.708272] pnp 00:05: resuming
[   39.708273] pnp 00:06: resuming
[   39.708275] serial 00:07: resuming
[   39.710305] pnp: Device 00:07 activated.
[   39.710308] serial 00:08: resuming
[   39.712305] pnp: Device 00:08 activated.
[   39.712308] pnp 00:09: resuming
[   39.712310] parport_pc 00:0a: resuming
[   39.715198] pnp: Device 00:0a activated.
[   39.715200] system 00:0b: resuming
[   39.715202] system 00:0c: resuming
[   39.715204] system 00:0d: resuming
[   39.715205] system 00:0e: resuming
[   39.715207] system 00:0f: resuming
[   39.715208] system 00:10: resuming
[   39.715213] pcspkr pcspkr: resuming
[   39.715215] pci_express 0000:00:02.0:pcie00: resuming
[   39.715217] pci_express 0000:00:02.0:pcie02: resuming
[   39.715219] pci_express 0000:00:03.0:pcie00: resuming
[   39.715221] pci_express 0000:00:03.0:pcie02: resuming
[   39.715345] serial8250 serial8250: resuming
[   39.715350] i8042 i8042: resuming
[   39.715368] atkbd serio0: resuming
[   39.729315] psmouse serio1: resuming
[   40.084091] platform vesafb.0: resuming
[   40.084093] platform floppy.0: resuming
[   40.084096] usb usb1: resuming
[   40.102486] usb usb2: resuming
[   40.122475] usb usb3: resuming
[   40.142464] usb usb4: resuming
[   40.162454] ide-disk 0.0: resuming
[   40.167610] ide-disk 0.1: resuming
[   40.170706] ide-cdrom 1.0: resuming
[   40.174378] ide-cdrom 1.1: resuming
[   40.175624] usb usb5: resuming
[   40.192438] hub 5-0:1.0: resuming
[   40.192440] usb 5-5: resuming
[   40.192442]  usbdev5.2_ep00: PM: resume from 0, parent 5-5 still 1
[   40.192445] usb-storage 5-5:1.0: PM: resume from 1, parent 5-5 still 1
[   40.192447] usb-storage 5-5:1.0: resuming
[   40.192449]  host3: PM: resume from 0, parent 5-5:1.0 still 1
[   40.192451]  usbdev5.2_ep81: PM: resume from 0, parent 5-5:1.0 still 1
[   40.192454]  usbdev5.2_ep02: PM: resume from 0, parent 5-5:1.0 still 1
[   40.192456]  usbdev5.2_ep83: PM: resume from 0, parent 5-5:1.0 still 1
[   40.192459] sd 3:0:0:0: resuming
[   40.192467] ac97 0-0:ALC655: resuming
[   40.192474] platform bluetooth: resuming
[   40.192625] Restarting tasks ... <5>sda : READ CAPACITY failed.
[   40.239184] sda : status=0, message=00, host=7, driver=00 
[   40.239188] sda : sense not available. 
[   40.242859] sda: Write Protect is off
[   40.242864] sda: Mode Sense: 00 00 00 00
[   40.242866] sda: assuming drive cache: write through
[   40.248473] done.
[   40.248509] Enabling non-boot CPUs ...
[   40.270537] SMP alternatives: switching to SMP code
[   40.270692] Booting processor 1/2 APIC 0x1
[   40.275830] Initializing CPU#1
[   40.316290] Calibrating delay using timer specific routine.. 1995.18 BogoMIPS (lpj=3990376)
[   40.316296] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   40.316299] CPU: L2 Cache: 512K (64 bytes/line)
[   40.316301] CPU 1/1 -> Node 0
[   40.316303] CPU: Physical Processor ID: 0
[   40.316304] CPU: Processor Core ID: 1
[   40.316375] AMD Athlon(tm) 64 X2 Dual Core Processor 3800+ stepping 02
[   40.318300] CPU 1: Syncing TSC to CPU 0.
[   40.318415] CPU 1: synchronized TSC with CPU 0 (last diff -4 cycles, maxerr 470 cycles)
[   40.322460] powernow-k8:    0 : fid 0xc (2000 MHz), vid 0xe
[   40.322467] powernow-k8:    1 : fid 0xa (1800 MHz), vid 0x10
[   40.322470] powernow-k8:    2 : fid 0x2 (1000 MHz), vid 0x12
[   40.322476] CPU1 is up
[   40.942014] sda : READ CAPACITY failed.
[   40.942017] sda : status=0, message=00, host=7, driver=00 
[   40.942021] sda : sense not available. 
[   40.942093] sda: Write Protect is off
[   40.942097] sda: Mode Sense: 00 00 00 00
[   40.942099] sda: assuming drive cache: write through
[   40.954576] usb 5-5: USB disconnect, address 2
[   41.230264] usb 1-2: new full speed USB device using uhci_hcd and address 2
[   41.271132] input: Power Button (FF) as /class/input/input7
[   41.271225] ACPI: Power Button (FF) [PWRF]
[   41.271319] input: Sleep Button (CM) as /class/input/input8
[   41.271338] ACPI: Sleep Button (CM) [SLPB]
[   41.271369] input: Power Button (CM) as /class/input/input9
[   41.271924] ACPI: Power Button (CM) [PWRB]
[   41.359245] ACPI: Thermal Zone [THRM] (30 C)
[   41.408305] usb 1-2: configuration #1 chosen from 1 choice
[   41.514991] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 2 if 0 alt 0 proto 2 vid 0x03F0 pid 0x7404
[   41.515403] usbcore: registered new interface driver usblp
[   41.515572] drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
[  197.266006] hdd: tray open
[  197.266182] end_request: I/O error, dev hdd, sector 0
[  197.266186] Buffer I/O error on device hdd, logical block 0
[  197.266190] Buffer I/O error on device hdd, logical block 1
[  197.266194] Buffer I/O error on device hdd, logical block 2
[  197.266197] Buffer I/O error on device hdd, logical block 3
[  197.266199] Buffer I/O error on device hdd, logical block 4
[  197.266202] Buffer I/O error on device hdd, logical block 5
[  197.266205] Buffer I/O error on device hdd, logical block 6
[  197.266208] Buffer I/O error on device hdd, logical block 7
[  197.266902] hdd: tray open
[  197.267078] end_request: I/O error, dev hdd, sector 0
[  197.267081] Buffer I/O error on device hdd, logical block 0
[  197.267172] hdd: tray open
[  197.267356] end_request: I/O error, dev hdd, sector 4
[  197.267359] Buffer I/O error on device hdd, logical block 1
[  197.267592] hdd: tray open
[  197.267768] end_request: I/O error, dev hdd, sector 0
[  197.267869] hdd: tray open
[  197.268046] end_request: I/O error, dev hdd, sector 4
[  197.268188] hdd: tray open
[  197.268371] end_request: I/O error, dev hdd, sector 0
[  197.268466] hdd: tray open
[  197.268642] end_request: I/O error, dev hdd, sector 4
[  197.268784] hdd: tray open
[  197.268967] end_request: I/O error, dev hdd, sector 0
[  197.269061] hdd: tray open
[  197.269239] end_request: I/O error, dev hdd, sector 4
[  197.269386] hdd: tray open
[  197.269563] end_request: I/O error, dev hdd, sector 0
[  197.269657] hdd: tray open
[  197.269840] end_request: I/O error, dev hdd, sector 4

---

### Post by noob12 on 2007-09-27
Hmm.  It isn't showing up in your lspci -nn output and I don't see signs of PCI routing issues at boot.

There are at least two other users now that have reported a similar problem. 

[http://ubuntuforums.org/showthread.php?t=545614](http://ubuntuforums.org/showthread.php?t=545614)

[http://ubuntuforums.org/showthread.php?t=559768](http://ubuntuforums.org/showthread.php?t=559768)

I don't know what it is but some interaction between Ubuntu and the BIOS disables the onboard LAN.  These users reported the setting actually "going away" in the BIOS.   I happened to pick up those threads as well, and couldn't help with either one.    I'm not sure if the other's issues are fundamentally related or just show similar symptoms.

I got the first user to boot with **acpi=off** hoping that would help but based on his feedback it didn't.  You could try this.

My suggestion is to file a bug on launchpad with the details as you've posted here.

I believe that resetting your BIOS to initial factory settings (which is usually an operation you can do in the BIOS) should recover the onboard lan settings in the BIOS.   You may lose them each time you boot Ubuntu again though.

Maybe there's another forum reader who understands this one?

---

### Post by f37u5g0d on 2007-09-29
I have the same problem you're having.  (I don't know if I am one of the threads he posted in that replay or not).  Everytime I log into ubuntu it deletes everytrace of my onboard LAN.  I have tried resetting the bios to the factory defaults but that doesn't do it.  I have to actually hit the switch on my powersupply while my comp is booting to get the enable ethernet option to even appear in my bios.  It is really annoying.  I am going to file a bug on luanchpad right now.

---

