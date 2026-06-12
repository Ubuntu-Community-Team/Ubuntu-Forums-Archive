---
title: "Airlink 101 on Feisty Fawn (Herd 2)"
date: 2007-01-31
forum: Networking &amp; Wireless
---

### Post by neverett on 2007-01-31
Just wanted to let everyone know that my Airlink 101 AWLL3026/NA is working perfectly on Feisty Fawn (Herd 2).  I couldn't get it to work on Edgy, so I thought I'd try Feisty and it worked!  Just plug it in and you're good to go.  Let me know whether the AWLL3026 works for you or does not work for you.  I'm trying to see how reliable this USB adapter is.  Thanks everyone, and enjoy!

---

### Post by FrodoB on 2007-02-01
My experience shows this to be a reliable device.  Good to hear that is now has out of the box support.  I am assuming that the driver is zd1211rw, is that the case?

---

### Post by neverett on 2007-02-01
> **FrodoB said:**
> My experience shows this to be a reliable device.  Good to hear that is now has out of the box support.  I am assuming that the driver is zd1211rw, is that the case?

I'm glad to hear that this is a reliable device.  I purchased it off of Amazon for around $14, which I thought was an amazing deal.  I checked the driver, and it is in fact using the zd1211rw driver.  I'm very happy with the progress of Ubuntu's wireless development within the last few releases.  Also Feisty Fawn Herd 2 appears to be very stable for me.  I don't know if you're using it or not, but I was surprised to find that the Airlink worked out of the box!

---

### Post by bruceleo on 2007-04-25
> **neverett said:**
> Just wanted to let everyone know that my Airlink 101 AWLL3026/NA is working perfectly on Feisty Fawn (Herd 2).  I couldn't get it to work on Edgy, so I thought I'd try Feisty and it worked!  Just plug it in and you're good to go.  Let me know whether the AWLL3026 works for you or does not work for you.  I'm trying to see how reliable this USB adapter is.  Thanks everyone, and enjoy!

Did this break in the final version? I have the same airlink101 and It didn't work in Edgy. Now final release of feisty is here and the light glows blue, but no wireless (same as edgy). here is dmsg output:
[ 1053.358653] usb 5-8: new high speed USB device using ehci_hcd and address 14
[ 1053.504884] usb 5-8: configuration #1 chosen from 1 choice
[ 1053.505618] scsi6 : SCSI emulation for USB Mass Storage devices
[ 1053.505680] usb-storage: device found at 14
[ 1053.505684] usb-storage: waiting for device to settle before scanning
[ 1053.857253] usb 5-7: new high speed USB device using ehci_hcd and address 15
[ 1053.989779] usb 5-7: configuration #1 chosen from 1 choice

It thinks that it's a storage device?

---

### Post by ubunton on 2007-04-28
great thread, i just got this device and it indeed works out of the box in feisty. thanks!

only problem is the signal is a bit weak, but nothing i wouldn't expect from a 20$ device.

---

### Post by bowie101 on 2007-08-08
hi all. i just installed (re install after things braking up in dapper) Feisty alternate CD Xubuntu. 

my airlink 101 3026 has an NA after that, so... AWLL3026/NA does that matter? what does it stand for? 

anyway, as in the case of the user above, solid blue light. no wireless recognition. exactly which driver do i get, from where, and install? confused with all the RWs flying around. 

here&#347; my dmesg: 

[    0.000000] Linux version 2.6.20-12-generic (root@palmer) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Wed Mar 21 20:55:46 UTC 2007 (Ubuntu 2.6.20-12.20-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009fc00 end: 000000000009fc00 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009fc00 size: 0000000000000400 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000e8000 size: 0000000000004000 end: 00000000000ec000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() lies in range...
[    0.000000] copy_e820_map() end <= 0x100000ULL
[    0.000000] copy_e820_map() start: 00000000000f0000 size: 0000000000010000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000000bee0000 end: 000000000bfe0000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000bfe0000 size: 0000000000010000 end: 000000000bff0000 type: 3
[    0.000000] copy_e820_map() start: 000000000bff0000 size: 0000000000010000 end: 000000000c000000 type: 2
[    0.000000] copy_e820_map() start: 00000000100a0000 size: 0000000000016e00 end: 00000000100b6e00 type: 2
[    0.000000] copy_e820_map() start: 00000000100b6e00 size: 0000000000000200 end: 00000000100b7000 type: 4
[    0.000000] copy_e820_map() start: 00000000100b7000 size: 0000000000049000 end: 0000000010100000 type: 2
[    0.000000] copy_e820_map() start: 00000000fff80000 size: 0000000000080000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000000bfe0000 (usable)
[    0.000000]  BIOS-e820: 000000000bfe0000 - 000000000bff0000 (ACPI data)
[    0.000000]  BIOS-e820: 000000000bff0000 - 000000000c000000 (reserved)
[    0.000000]  BIOS-e820: 00000000100a0000 - 00000000100b6e00 (reserved)
[    0.000000]  BIOS-e820: 00000000100b6e00 - 00000000100b7000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000100b7000 - 0000000010100000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 191MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 49120) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->    49120
[    0.000000]   HighMem     49120 ->    49120
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->    49120
[    0.000000] On node 0 totalpages: 49120
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 351 pages used for memmap
[    0.000000]   Normal zone: 44673 pages, LIFO batch:7
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP (v000 TOSHIB                                ) @ 0x000f0160
[    0.000000] ACPI: RSDT (v001 TOSHIB 750      0x00970814 TASM 0x04010000) @ 0x0bfe0000
[    0.000000] ACPI: FADT (v001 TOSHIB 750      0x00970814 TASM 0x04010000) @ 0x0bfe0054
[    0.000000] ACPI: DSDT (v001 TOSHIB 2550     0x19990423 MSFT 0x0100000a) @ 0x00000000
[    0.000000] ACPI: BIOS age (1999) fails cutoff (2000), acpi=force is required to enable ACPI
[    0.000000] ACPI: Disabling ACPI support
[    0.000000] Allocating PCI resources starting at 20000000 (gap: 10100000:efe80000)
[    0.000000] Detected 399.079 MHz processor.
[   15.522314] Built 1 zonelists.  Total pages: 48737
[   15.522331] Kernel command line: root=UUID=6782d43d-3660-4d45-ab51-60bd48b85999 ro quiet splash
[   15.523286] Local APIC disabled by BIOS -- you can enable it with "lapic"
[   15.523326] mapped APIC to ffffd000 (0118a000)
[   15.523342] Enabling fast FPU save and restore... done.
[   15.523384] Initializing CPU#0
[   15.523533] PID hash table entries: 1024 (order: 10, 4096 bytes)
[   15.525539] Console: colour VGA+ 80x25
[   15.526380] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
[   15.527326] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
[   15.557168] Memory: 183772k/196480k available (1990k kernel code, 12156k reserved, 890k data, 328k init, 0k highmem)
[   15.557223] virtual kernel memory layout:
[   15.557229]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   15.557237]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   15.557244]     vmalloc : 0xcc800000 - 0xff7fe000   ( 815 MB)
[   15.557251]     lowmem  : 0xc0000000 - 0xcbfe0000   ( 191 MB)
[   15.557259]       .init : 0xc03d7000 - 0xc0429000   ( 328 kB)
[   15.557266]       .data : 0xc02f1b04 - 0xc03d06d4   ( 890 kB)
[   15.557273]       .text : 0xc0100000 - 0xc02f1b04   (1990 kB)
[   15.557290] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   15.635501] Calibrating delay using timer specific routine.. 799.13 BogoMIPS (lpj=1598265)
[   15.635699] Security Framework v1.0.0 initialized
[   15.635730] SELinux:  Disabled at boot.
[   15.635814] Mount-cache hash table entries: 512
[   15.636406] CPU: After generic identify, caps: 0183f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[   15.636461] CPU: L1 I cache: 16K, L1 D cache: 16K
[   15.636475] CPU: L2 cache: 128K
[   15.636489] CPU: After all inits, caps: 0183f9ff 00000000 00000000 00000040 00000000 00000000 00000000
[   15.636539] Compat vDSO mapped to ffffe000.
[   15.636570] Remapping vsyscall page to ffffe000
[   15.636612] Checking 'hlt' instruction... OK.
[   15.651600] SMP alternatives: switching to UP code
[   15.652310] Freeing SMP alternatives: 11k freed
[   15.653187] Early unpacking initramfs... done
[   17.192639] CPU0: Intel Celeron (Mendocino) stepping 0a
[   17.192667] SMP motherboard not detected.
[   17.192679] Local APIC not detected. Using dummy APIC emulation.
[   17.192869] Brought up 1 CPUs
[   17.193977] Booting paravirtualized kernel on bare hardware
[   17.194264] Time: 12:13:47  Date: 07/08/107
[   17.194412] NET: Registered protocol family 16
[   17.194894] EISA bus registered
[   17.199309] PCI: PCI BIOS revision 2.10 entry at 0xfedcd, last bus=21
[   17.199323] PCI: Using configuration type 1
[   17.199333] Setting up standard PCI resources
[   17.203460] ACPI: Interpreter disabled.
[   17.203484] Linux Plug and Play Support v0.97 (c) Adam Belay
[   17.203525] pnp: PnP ACPI: disabled
[   17.203541] PnPBIOS: Scanning system for PnP BIOS support...
[   17.203677] PnPBIOS: Found PnP BIOS installation structure at 0xc00f8ed0
[   17.203694] PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0x933a, dseg 0x0
[   17.263132] PnPBIOS: 15 nodes reported by PnP BIOS; 15 recorded by driver
[   17.263352] PCI: Probing PCI hardware
[   17.263377] PCI: Probing PCI hardware (bus 00)
[   17.264106] * Found PM-Timer Bug on the chipset. Due to workarounds for a bug,
[   17.264116] * this clock source is slow. Consider trying other clock sources
[   17.264198] PCI quirk: region fe00-fe3f claimed by PIIX4 ACPI
[   17.264213] PCI quirk: region fe70-fe7f claimed by PIIX4 SMB
[   17.264230] PIIX4 devres B PIO at 006c-006f
[   17.264831] Boot video device is 0000:01:00.0
[   17.268962] PCI: Using IRQ router PIIX/ICH [8086/7110] at 0000:00:05.0
[   17.269003] PCI: setting IRQ 11 as level-triggered
[   17.269016] PCI: Found IRQ 11 for device 0000:00:02.0
[   17.269052] PCI: Sharing IRQ 11 with 0000:01:00.0
[   17.269069] PCI: Found IRQ 11 for device 0000:00:02.1
[   17.269103] PCI: Sharing IRQ 11 with 0000:00:0c.0
[   17.280966] NET: Registered protocol family 8
[   17.280980] NET: Registered protocol family 20
[   17.283168] PCI: Bridge: 0000:00:01.0
[   17.283183]   IO window: disabled.
[   17.283200]   MEM window: ff000000-ffbfffff
[   17.283215]   PREFETCH window: eff00000-efffffff
[   17.283230] PCI: Bus 2, cardbus bridge: 0000:00:02.0
[   17.283242]   IO window: 00001000-000010ff
[   17.283256]   IO window: 00001400-000014ff
[   17.283271]   PREFETCH window: 20000000-23ffffff
[   17.283286]   MEM window: 24000000-27ffffff
[   17.283299] PCI: Bus 6, cardbus bridge: 0000:00:02.1
[   17.283310]   IO window: 00001800-000018ff
[   17.283324]   IO window: 00002000-000020ff
[   17.283338]   PREFETCH window: 28000000-2bffffff
[   17.283353]   MEM window: 2c000000-2fffffff
[   17.283397] PCI: Found IRQ 11 for device 0000:00:02.0
[   17.283435] PCI: Sharing IRQ 11 with 0000:01:00.0
[   17.283450] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   17.283474] PCI: Found IRQ 11 for device 0000:00:02.1
[   17.283508] PCI: Sharing IRQ 11 with 0000:00:0c.0
[   17.283525] PCI: Setting latency timer of device 0000:00:02.1 to 64
[   17.283631] NET: Registered protocol family 2
[   17.319267] IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
[   17.319641] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
[   17.319960] TCP bind hash table entries: 4096 (order: 3, 32768 bytes)
[   17.320151] TCP: Hash tables configured (established 8192 bind 4096)
[   17.320165] TCP reno registered
[   17.331547] checking if image is initramfs... it is
[   20.242259] Freeing initrd memory: 6723k freed
[   20.243952] audit: initializing netlink socket (disabled)
[   20.244005] audit(1186575229.904:1): initialized
[   20.244649] VFS: Disk quotas dquot_6.5.1
[   20.244740] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   20.244987] io scheduler noop registered
[   20.245004] io scheduler anticipatory registered
[   20.245015] io scheduler deadline registered
[   20.245070] io scheduler cfq registered (default)
[   20.245103] Limiting direct PCI/PCI transfers.
[   20.246089] isapnp: Scanning for PnP cards...
[   20.599304] isapnp: No Plug & Play device found
[   20.832442] Real Time Clock Driver v1.12ac
[   20.832809] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   20.833170] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   20.837526] 00:0e: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   20.839177] mice: PS/2 mouse device common for all mice
[   20.842563] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   20.843415] input: Macintosh mouse button emulation as /class/input/input0
[   20.843628] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   20.843650] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   20.844452] PNP: PS/2 Controller [PNP0303,PNP0f13] at 0x60,0x64 irq 1,12
[   20.847695] serio: i8042 KBD port at 0x60,0x64 irq 1
[   20.847720] serio: i8042 AUX port at 0x60,0x64 irq 12
[   20.848441] EISA: Probing bus 0 at eisa.0
[   20.848482] Cannot allocate resource for EISA slot 1
[   20.848495] Cannot allocate resource for EISA slot 2
[   20.848539] EISA: Detected 0 cards.
[   20.848903] TCP cubic registered
[   20.848936] NET: Registered protocol family 1
[   20.849029] Using IPI No-Shortcut mode
[   20.849147]   Magic number: 3:53:228
[   20.849253]   hash matches device ttyrf
[   20.849738] Time: tsc clocksource has been installed.
[   20.851556] Freeing unused kernel memory: 328k freed
[   20.864400] input: AT Translated Set 2 keyboard as /class/input/input1
[   22.945751] Capability LSM initialized
[   23.209618] thermal: Unknown symbol acpi_processor_set_thermal_limit
[   25.882216] SCSI subsystem initialized
[   25.930094] libata version 2.20 loaded.
[   25.962176] ata_piix 0000:00:05.1: version 2.10ac1
[   25.962494] ata1: PATA max UDMA/33 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001fe60 irq 14
[   25.962648] ata2: PATA max UDMA/33 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001fe68 irq 15
[   25.962714] scsi0 : ata_piix
[   26.124259] ata1.00: ATA-4: TOSHIBA MK6411MAT, J0.07 H, max UDMA/33
[   26.124280] ata1.00: 12685680 sectors, multi 16: LBA 
[   26.132192] ata1.00: configured for UDMA/33
[   26.132236] scsi1 : ata_piix
[   26.193211] usbcore: registered new interface driver usbfs
[   26.193309] usbcore: registered new interface driver hub
[   26.193452] usbcore: registered new device driver usb
[   26.200887] USB Universal Host Controller Interface driver v3.0
[   26.468183] ata2.00: ATAPI, max MWDMA2
[   26.648099] ata2.00: configured for MWDMA2
[   26.655979] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK6411MA J0.0 PQ: 0 ANSI: 5
[   26.657558] scsi 1:0:0:0: CD-ROM            TEAC     CD-224E          7.5A PQ: 0 ANSI: 5
[   26.658798] PCI: Found IRQ 11 for device 0000:00:05.2
[   26.658870] uhci_hcd 0000:00:05.2: UHCI Host Controller
[   26.659313] uhci_hcd 0000:00:05.2: new USB bus registered, assigned bus number 1
[   26.659384] uhci_hcd 0000:00:05.2: irq 11, io base 0x0000ffe0
[   26.659992] usb usb1: configuration #1 chosen from 1 choice
[   26.660123] hub 1-0:1.0: USB hub found
[   26.660172] hub 1-0:1.0: 2 ports detected
[   26.753182] Floppy drive(s): fd0 is 1.44M
[   26.809978] FDC 0 is an 8272A
[   27.003685] usb 1-1: new full speed USB device using uhci_hcd and address 2
[   27.126850] usb 1-1: device descriptor read/64, error -71
[   27.131208] SCSI device sda: 12685680 512-byte hdwr sectors (6495 MB)
[   27.131279] sda: Write Protect is off
[   27.131292] sda: Mode Sense: 00 3a 00 00
[   27.131383] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   27.131725] SCSI device sda: 12685680 512-byte hdwr sectors (6495 MB)
[   27.131783] sda: Write Protect is off
[   27.131796] sda: Mode Sense: 00 3a 00 00
[   27.131885] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   27.131903]  sda:<3>usb 1-1: device descriptor read/64, error -71
[   27.563492] usb 1-1: new full speed USB device using uhci_hcd and address 3
[   27.602522]  sda1 sda2 < sda5 >
[   27.634982] sd 0:0:0:0: Attached scsi disk sda
[   27.660909] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   27.661021] sr 1:0:0:0: Attached scsi generic sg1 type 5
[   27.673475] sr0: scsi3-mmc drive: 24x/24x xa/form2 cdda tray
[   27.673498] Uniform CD-ROM driver Revision: 3.20
[   27.673731] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   27.683488] usb 1-1: device descriptor read/64, error -71
[   27.907433] usb 1-1: device descriptor read/64, error -71
[   28.123330] usb 1-1: new full speed USB device using uhci_hcd and address 4
[   28.254028] Attempting manual resume
[   28.254046] swsusp: Resume From Partition 8:5
[   28.254056] PM: Checking swsusp image.
[   28.254549] PM: Resume from disk failed.
[   28.355009] kjournald starting.  Commit interval 5 seconds
[   28.355067] EXT3-fs: mounted filesystem with ordered data mode.
[   28.539137] usb 1-1: device not accepting address 4, error -71
[   28.651115] usb 1-1: new full speed USB device using uhci_hcd and address 5
[   29.058952] usb 1-1: device not accepting address 5, error -71
[   57.729229] Linux agpgart interface v0.101 (c) Dave Jones
[   57.769781] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   57.780754] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   57.829262] Yenta: CardBus bridge found at 0000:00:02.0 [1179:0001]
[   57.961978] Yenta: ISA IRQ mask 0x04b0, PCI irq 11
[   57.961995] Socket status: 30000007
[   57.962605] Yenta: CardBus bridge found at 0000:00:02.1 [1179:0001]
[   58.089946] Yenta: ISA IRQ mask 0x04b0, PCI irq 11
[   58.089963] Socket status: 30000011
[   58.111682] agpgart: Detected an Intel 440BX Chipset.
[   58.123588] agpgart: AGP aperture is 128M @ 0xf0000000
[   58.700914] piix4_smbus 0000:00:05.3: Found 0000:00:05.3 device
[   59.044760] pccard: PCMCIA card inserted into slot 1
[   59.590878] Linux video capture interface: v2.00
[   59.685302] irda_init()
[   59.685364] NET: Registered protocol family 23
[   59.818749] PCI: Found IRQ 11 for device 0000:00:0c.0
[   59.818779] PCI: Sharing IRQ 11 with 0000:00:02.1
[   59.818964] videodev: "Maestro radio" has no release callback. Please fix your driver for proper sysfs support, see [http://lwn.net/Articles/36850/](http://lwn.net/Articles/36850/)
[   59.948898] maestro_radio: probe of 0000:00:0c.0 failed with error -5
[   59.996800] PCI: Found IRQ 11 for device 0000:00:0a.0
[   59.997251] IrDA: Registered device irda0
[   59.997267] toshoboe: Using multiple tasks, version $Id: donauboe.c V2.18 ven jan 10 03:14:16 2003$
[   61.123724] logips2pp: Detected unknown logitech mouse model 109
[   61.633353] input: ImExPS/2 Logitech Explorer Mouse as /class/input/input2
[   61.773503] input: PC Speaker as /class/input/input3
[   63.187746] parport: PnPBIOS parport detected.
[   63.187806] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   64.002824] cs: IO port probe 0x100-0x3af: clean.
[   64.288139] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   64.288708] cs: IO port probe 0x820-0x8ff: clean.
[   64.289198] cs: IO port probe 0xc00-0xcf7: clean.
[   64.290117] cs: IO port probe 0xa00-0xaff: clean.
[   64.339024] es1968: clocking to 48000
[   64.401150] cs: IO port probe 0x100-0x3af: clean.
[   64.402284] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   64.402846] cs: IO port probe 0x820-0x8ff: clean.
[   64.403414] cs: IO port probe 0xc00-0xcf7: clean.
[   64.404328] cs: IO port probe 0xa00-0xaff: clean.
[   64.404873] cs: memory probe 0xa0000000-0xa0ffffff: clean.
[   64.418931] pcmcia: registering new device pcmcia1.0
[   65.248520] eth0: NE2000 (DL10019 rev 05): io 0x300, irq 4, hw_addr 00:E0:98:09:B8:51
[   65.248602] pcmcia: registering new device pcmcia1.1
[   65.864018] lp0: using parport0 (interrupt-driven).
[   66.008765] Adding 321260k swap on /dev/disk/by-uuid/48e08289-2f21-4577-a341-749444ca6f91.  Priority:-1 extents:1 across:321260k
[   66.282597] EXT3 FS on sda1, internal journal
[   69.302164] acpi_cpufreq: Unknown symbol acpi_processor_notify_smm
[   69.302693] acpi_cpufreq: Unknown symbol acpi_processor_unregister_performance
[   69.303893] acpi_cpufreq: Unknown symbol acpi_processor_preregister_performance
[   69.304516] acpi_cpufreq: Unknown symbol acpi_processor_register_performance
[   80.393435] ppdev: user-space parallel port driver
[   90.228721] apm: BIOS version 1.2 Flags 0x02 (Driver version 1.16ac)
[  357.762470] NET: Registered protocol family 17
[  357.887688] eth0: found link beat
[  357.888168] eth0: autonegotiation complete: 100baseT-FD selected
[  360.568380] NET: Registered protocol family 10
[  360.569108] lo: Disabled Privacy Extensions
[  370.978514] eth0: no IPv6 routers present
[ 4053.148771] usb 1-1: new full speed USB device using uhci_hcd and address 6
[ 4053.272746] usb 1-1: device descriptor read/64, error -71
[ 4053.496655] usb 1-1: device descriptor read/64, error -71
[ 4053.712583] usb 1-1: new full speed USB device using uhci_hcd and address 7
[ 4053.832559] usb 1-1: device descriptor read/64, error -71
[ 4054.056491] usb 1-1: device descriptor read/64, error -71
[ 4054.272410] usb 1-1: new full speed USB device using uhci_hcd and address 8
[ 4054.680253] usb 1-1: device not accepting address 8, error -71
[ 4054.792226] usb 1-1: new full speed USB device using uhci_hcd and address 9
[ 4055.200070] usb 1-1: device not accepting address 9, error -71
[28079.640835] ISO 9660 Extensions: Microsoft Joliet Level 3
[28080.938789] ISO 9660 Extensions: RRIP_1991A
[28682.583660] usb 1-1: new full speed USB device using uhci_hcd and address 10
[28682.706582] usb 1-1: device descriptor read/64, error -71
[28682.930506] usb 1-1: device descriptor read/64, error -71
[28683.146418] usb 1-1: new full speed USB device using uhci_hcd and address 11
[28683.286384] usb 1-1: device descriptor read/64, error -71
[28683.510311] usb 1-1: device descriptor read/64, error -71
[28683.726228] usb 1-1: new full speed USB device using uhci_hcd and address 12
[28684.134105] usb 1-1: device not accepting address 12, error -71
[28684.246064] usb 1-1: new full speed USB device using uhci_hcd and address 13
[28684.653894] usb 1-1: device not accepting address 13, error -71
[30106.649753] usb 1-1: new full speed USB device using uhci_hcd and address 14
[30106.773700] usb 1-1: device descriptor read/64, error -71
[30107.001672] usb 1-1: device descriptor read/64, error -71
[30107.217594] usb 1-1: new full speed USB device using uhci_hcd and address 15
[30107.337561] usb 1-1: device descriptor read/64, error -71
[30107.561690] usb 1-1: device descriptor read/64, error -71
[30107.777422] usb 1-1: new full speed USB device using uhci_hcd and address 16
[30108.185246] usb 1-1: device not accepting address 16, error -71
[30108.297219] usb 1-1: new full speed USB device using uhci_hcd and address 17
[30108.705061] usb 1-1: device not accepting address 17, error -71

---

