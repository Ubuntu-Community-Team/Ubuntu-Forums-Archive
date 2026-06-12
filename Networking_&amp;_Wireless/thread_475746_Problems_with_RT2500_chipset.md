---
title: "Problems with RT2500 chipset"
date: 2007-06-16
forum: Networking &amp; Wireless
---

### Post by freshr on 2007-06-16
I just installed Ubuntu 7.04 on an old Toshiba Satellite 4080XCDT, Pentium II, 196MB RAM. I have an **Edimax EW-7108PCG** wireless card with **RT2500** chipset. It is not being recognised. Nothing, no lights flashing when I boot, no HDD activity when I plug/unplug it. I don't even know if it is getting power, although another PCMCIA card was working in Windows 98 before I upgraded so there's no reason to believe something hardware related has broken...

I attach the output of all the logs that I have looked at. I have tried ndiswrapper with the Windows driver for this card (still not recognised), and have tried compiling the driver's source for the chipset from here: [http://rt2x00.serialmonkey.com/wiki/index.php?title=Downloads](http://rt2x00.serialmonkey.com/wiki/index.php?title=Downloads). However I could not get it to compile. I don't think the Makefile is set up for Ubuntu Feisty, and I have no inclination to learn how they work to try and fix it.

I'm fairly noob with Linux, so please don't assume tooo much prior knowledge when you reply! Can you see anything that would be stopping this card from being detected? Can I look anywhere else for clues?

Much appreciated,

Ross


**iwconfig**
lo        no wireless extensions.

rda0    no wireless extensions.

**ifconfig**
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

**lspci**
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (AGP disabled) (rev 03)
00:04.0 VGA compatible controller: Trident Microsystems Cyber 9525 (rev 49)
00:05.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:05.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:05.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:05.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
00:07.0 Communication controller: Agere Systems 56k WinModem (rev 01)
00:0a.0 Communication controller: Toshiba America Info Systems FIR Port (rev 23)
00:0c.0 Multimedia audio controller: ESS Technology ES1978 Maestro 2E (rev 10)

**/etc/network/interfaces**
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

**dmesg**
[    0.000000] Linux version 2.6.20-15-generic (root@palmer) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Apr 15 07:36:31 UTC 2007 (Ubuntu 2.6.20-15.27-generic)
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
[    0.000000] DMI 2.1 present.
[    0.000000] ACPI: RSDP (v000 TOSHIB                                ) @ 0x000f0160
[    0.000000] ACPI: RSDT (v001 TOSHIB 750      0x00970814 TASM 0x04010000) @ 0x0bfe0000
[    0.000000] ACPI: FADT (v001 TOSHIB 750      0x00970814 TASM 0x04010000) @ 0x0bfe0054
[    0.000000] ACPI: DSDT (v001 TOSHIB 4030     0x19991112 MSFT 0x0100000a) @ 0x00000000
[    0.000000] ACPI: BIOS age (1999) fails cutoff (2000), acpi=force is required to enable ACPI
[    0.000000] ACPI: acpi=force override
[    0.000000] ACPI: PM-Timer IO Port: 0xfe08
[    0.000000] Allocating PCI resources starting at 20000000 (gap: 10100000:efe80000)
[    0.000000] Detected 366.608 MHz processor.
[ 7712.873292] Built 1 zonelists.  Total pages: 48737
[ 7712.873311] Kernel command line: root=UUID=d024d1bd-2998-4e33-b1a2-b515e77d794c acpi=force ro quiet splash
[ 7712.874400] Local APIC disabled by BIOS -- you can enable it with "lapic"
[ 7712.874452] mapped APIC to ffffd000 (0118a000)
[ 7712.874470] Enabling fast FPU save and restore... done.
[ 7712.874524] Initializing CPU#0
[ 7712.874690] PID hash table entries: 1024 (order: 10, 4096 bytes)
[ 7712.877660] Console: colour VGA+ 80x25
[ 7712.878518] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
[ 7712.879268] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
[ 7712.910873] Memory: 183744k/196480k available (1992k kernel code, 12208k reserved, 893k data, 328k init, 0k highmem)
[ 7712.910931] virtual kernel memory layout:
[ 7712.910938]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[ 7712.910947]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[ 7712.910955]     vmalloc : 0xcc800000 - 0xff7fe000   ( 815 MB)
[ 7712.910963]     lowmem  : 0xc0000000 - 0xcbfe0000   ( 191 MB)
[ 7712.910972]       .init : 0xc03d7000 - 0xc0429000   ( 328 kB)
[ 7712.910980]       .data : 0xc02f2264 - 0xc03d16d4   ( 893 kB)
[ 7712.910988]       .text : 0xc0100000 - 0xc02f2264   (1992 kB)
[ 7712.911007] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[ 7712.990691] Calibrating delay using timer specific routine.. 734.18 BogoMIPS (lpj=1468367)
[ 7712.990901] Security Framework v1.0.0 initialized
[ 7712.990933] SELinux:  Disabled at boot.
[ 7712.991021] Mount-cache hash table entries: 512
[ 7712.991631] CPU: After generic identify, caps: 0183f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[ 7712.991685] CPU: L1 I cache: 16K, L1 D cache: 16K
[ 7712.991700] CPU: L2 cache: 256K
[ 7712.991715] CPU: After all inits, caps: 0183f9ff 00000000 00000000 00000040 00000000 00000000 00000000
[ 7712.991765] Compat vDSO mapped to ffffe000.
[ 7712.991798] Remapping vsyscall page to ffffe000
[ 7712.991840] Checking 'hlt' instruction... OK.
[ 7713.006796] SMP alternatives: switching to UP code
[ 7713.007539] Freeing SMP alternatives: 11k freed
[ 7713.008410] Early unpacking initramfs... done
[ 7714.653797] ACPI: Core revision 20060707
[ 7714.656606] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[ 7714.665938] ACPI: setting ELCR to 0200 (from 0a08)
[ 7714.666209] CPU0: Intel Mobile Pentium II stepping 0a
[ 7714.666236] SMP motherboard not detected.
[ 7714.666249] Local APIC not detected. Using dummy APIC emulation.
[ 7714.666431] Brought up 1 CPUs
[ 7714.667804] Booting paravirtualized kernel on bare hardware
[ 7714.668093] Time: 16:42:59  Date: 05/16/107
[ 7714.668237] NET: Registered protocol family 16
[ 7714.668756] EISA bus registered
[ 7714.668780] ACPI: bus type pci registered
[ 7714.673562] PCI: PCI BIOS revision 2.10 entry at 0xfedcd, last bus=21
[ 7714.673577] PCI: Using configuration type 1
[ 7714.673587] Setting up standard PCI resources
[ 7714.688364] ACPI: Interpreter enabled
[ 7714.688383] ACPI: Using PIC for interrupt routing
[ 7714.693529] ACPI: PCI Interrupt Link [LNKA] (IRQs 5 6 7 10 *11 12)
[ 7714.699508] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 6 7 10 *11 12)
[ 7714.705321] ACPI: PCI Interrupt Link [LNKC] (IRQs 5 6 7 10 *11 12)
[ 7714.711183] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 6 7 10 *11 12)
[ 7714.717827] ACPI: PCI Interrupt Link [LNKE] (IRQs *3 4)
[ 7714.719919] ACPI: PCI Root Bridge [PCI0] (0000:00)
[ 7714.719943] PCI: Probing PCI hardware (bus 00)
[ 7714.723737] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[ 7714.724812] Boot video device is 0000:00:04.0
[ 7714.725090] * Found PM-Timer Bug on the chipset. Due to workarounds for a bug,
[ 7714.725101] * this clock source is slow. Consider trying other clock sources
[ 7714.725186] PCI quirk: region fe00-fe3f claimed by PIIX4 ACPI
[ 7714.725202] PCI quirk: region fe70-fe7f claimed by PIIX4 SMB
[ 7714.725220] PIIX4 devres B PIO at 006c-006f
[ 7714.725559] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[ 7714.750781] ACPI: Power Resource [PIHD] (on)
[ 7714.752639] ACPI: Power Resource [PMHD] (on)
[ 7714.759187] ACPI: Power Resource [PFAN] (off)
[ 7714.759681] Linux Plug and Play Support v0.97 (c) Adam Belay
[ 7714.759764] pnp: PnP ACPI init
[ 7714.768727] PCI: setting IRQ 13 as level-triggered
[ 7714.802491] pnp: PnP ACPI: found 13 devices
[ 7714.802513] PnPBIOS: Disabled by ACPI PNP
[ 7714.802826] PCI: Using ACPI for IRQ routing
[ 7714.802844] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[ 7714.812650] NET: Registered protocol family 8
[ 7714.812663] NET: Registered protocol family 20
[ 7714.818255] NET: Registered protocol family 2
[ 7714.854975] IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
[ 7714.855337] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
[ 7714.855647] TCP bind hash table entries: 4096 (order: 3, 32768 bytes)
[ 7714.855819] TCP: Hash tables configured (established 8192 bind 4096)
[ 7714.855833] TCP reno registered
[ 7714.867207] checking if image is initramfs... it is
[ 7718.022978] Freeing initrd memory: 6774k freed
[ 7718.024668] audit: initializing netlink socket (disabled)
[ 7718.024722] audit(1182012183.336:1): initialized
[ 7718.025356] VFS: Disk quotas dquot_6.5.1
[ 7718.025449] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[ 7718.025663] io scheduler noop registered
[ 7718.025678] io scheduler anticipatory registered
[ 7718.025691] io scheduler deadline registered
[ 7718.025742] io scheduler cfq registered (default)
[ 7718.025776] Limiting direct PCI/PCI transfers.
[ 7718.026737] isapnp: Scanning for PnP cards...
[ 7718.380174] isapnp: No Plug & Play device found
[ 7718.552630] Real Time Clock Driver v1.12ac
[ 7718.552900] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[ 7718.553242] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[ 7718.556763] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[ 7718.557991] mice: PS/2 mouse device common for all mice
[ 7718.561284] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[ 7718.562081] input: Macintosh mouse button emulation as /class/input/input0
[ 7718.562288] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[ 7718.562310] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[ 7718.563088] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[ 7718.566121] serio: i8042 KBD port at 0x60,0x64 irq 1
[ 7718.566147] serio: i8042 AUX port at 0x60,0x64 irq 12
[ 7718.566885] EISA: Probing bus 0 at eisa.0
[ 7718.566918] Cannot allocate resource for EISA slot 1
[ 7718.566970] EISA: Detected 0 cards.
[ 7718.597375] TCP cubic registered
[ 7718.597410] NET: Registered protocol family 1
[ 7718.597511] Using IPI No-Shortcut mode
[ 7718.597796] ACPI: (supports S0 S1 S3 S4 S5)
[ 7718.598012]   Magic number: 11:582:742
[ 7718.598460] Time: tsc clocksource has been installed.
[ 7718.599933] Freeing unused kernel memory: 328k freed
[ 7718.606950] input: AT Translated Set 2 keyboard as /class/input/input1
[ 7720.719794] Capability LSM initialized
[ 7720.909328] ACPI: Transitioning device [FAN] to D3
[ 7720.909346] ACPI: Transitioning device [FAN] to D3
[ 7720.909366] ACPI: Fan [FAN] (off)
[ 7720.932853] ACPI: CPU0 (power states: C1[C1] C2[C2])
[ 7720.940209] ACPI: Thermal Zone [THRM] (71 C)
[ 7723.400694] PIIX4: IDE controller at PCI slot 0000:00:05.1
[ 7723.400744] PIIX4: chipset revision 1
[ 7723.400756] PIIX4: not 100% native mode: will probe irqs later
[ 7723.400783]     ide0: BM-DMA at 0xfe60-0xfe67, BIOS settings: hda:DMA, hdb:pio
[ 7723.400822]     ide1: BM-DMA at 0xfe68-0xfe6f, BIOS settings: hdc:DMA, hdd:pio
[ 7723.400855] Probing IDE interface ide0...
[ 7723.482788] usbcore: registered new interface driver usbfs
[ 7723.482903] usbcore: registered new interface driver hub
[ 7723.483024] usbcore: registered new device driver usb
[ 7723.491053] USB Universal Host Controller Interface driver v3.0
[ 7723.834449] hda: IBM-DBCA-206480, ATA DISK drive
[ 7724.183766] Floppy drive(s): fd0 is 1.44M
[ 7724.368727] FDC 0 is an 8272A
[   11.584000] Time: acpi_pm clocksource has been installed.
[   11.636000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   11.656000] Probing IDE interface ide1...
[   12.392000] hdc: TOSHIBA CD-ROM XM-1802D, ATAPI CD/DVD-ROM drive
[   12.760000] ide1 at 0x170-0x177,0x376 on irq 15
[   12.836000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[   12.836000] PCI: setting IRQ 11 as level-triggered
[   12.836000] ACPI: PCI Interrupt 0000:00:05.2[D] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[   12.836000] uhci_hcd 0000:00:05.2: UHCI Host Controller
[   12.836000] uhci_hcd 0000:00:05.2: new USB bus registered, assigned bus number 1
[   12.836000] uhci_hcd 0000:00:05.2: irq 11, io base 0x0000ffe0
[   12.844000] usb usb1: configuration #1 chosen from 1 choice
[   12.844000] hub 1-0:1.0: USB hub found
[   12.844000] hub 1-0:1.0: 2 ports detected
[   12.848000] SCSI subsystem initialized
[   12.904000] libata version 2.20 loaded.
[   12.980000] hda: max request size: 128KiB
[   13.020000] hda: 12685680 sectors (6495 MB) w/420KiB Cache, CHS=13424/15/63, UDMA(33)
[   13.020000] hda: cache flushes not supported
[   13.020000]  hda: hda1 hda2 < hda5 >
[   13.144000] hdc: ATAPI 24X CD-ROM drive, 128kB Cache, DMA
[   13.144000] Uniform CD-ROM driver Revision: 3.20
[   13.616000] Attempting manual resume
[   13.616000] swsusp: Resume From Partition 3:5
[   13.616000] PM: Checking swsusp image.
[   13.628000] PM: Resume from disk failed.
[   13.756000] kjournald starting.  Commit interval 5 seconds
[   13.760000] EXT3-fs: mounted filesystem with ordered data mode.
[   50.844000] piix4_smbus 0000:00:05.3: Found 0000:00:05.3 device
[   52.244000] Linux video capture interface: v2.00
[   52.456000] input: PC Speaker as /class/input/input2
[   52.612000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 11
[   52.612000] ACPI: PCI Interrupt 0000:00:0c.0[A] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[   52.612000] videodev: "Maestro radio" has no release callback. Please fix your driver for proper sysfs support, see [http://lwn.net/Articles/36850/](http://lwn.net/Articles/36850/)
[   52.744000] maestro_radio: probe of 0000:00:0c.0 failed with error -5
[   53.040000] irda_init()
[   53.040000] NET: Registered protocol family 23
[   53.352000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[   53.352000] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[   53.352000] IrDA: Registered device irda0
[   53.352000] toshoboe: Using multiple tasks, version $Id: donauboe.c V2.18 ven jan 10 03:14:16 2003$
[   53.772000] parport: PnPBIOS parport detected.
[   53.772000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   54.136000] input: PS/2 Generic Mouse as /class/input/input3
[   56.644000] es1968: clocking to 48000
[   57.128000] lp0: using parport0 (interrupt-driven).
[   57.264000] Adding 321260k swap on /dev/disk/by-uuid/e5f13071-1cd5-4706-8cfa-236728c05993.  Priority:-1 extents:1 across:321260k
[   57.512000] EXT3 FS on hda1, internal journal
[   60.508000] toshiba_acpi: Toshiba Laptop ACPI Extras version 0.19a-dev
[   60.508000] toshiba_acpi:     HCI method: \_SB_.VALD.GHCI
[   60.520000] toshiba_acpi: Toshiba hotkeys are sent as ACPI events
[   60.520000] toshiba_acpi: ktoshkeyd will check 2 times per second
[   60.548000] toshiba_acpi: Dropped 0 keys from the queue on startup
[   60.684000] input: Power Button (FF) as /class/input/input4
[   60.684000] ACPI: Power Button (FF) [PWRF]
[   60.720000] input: Lid Switch as /class/input/input5
[   60.720000] ACPI: Lid Switch [LID]
[   61.128000] ACPI: AC Adapter [ADP1] (on-line)
[   61.312000] ACPI: ACPI Dock Station Driver 
[   61.408000] ACPI: Battery Slot [BAT1] (battery present)
[   61.504000] ACPI: Video Device [VGA] (multi-head: yes  rom: yes  post: no)
[   61.592000] ibm_acpi: ec object not found
[   61.696000] Using specific hotkey driver
[   61.980000] pcc_acpi: loading...
[   78.728000] ppdev: user-space parallel port driver
[   84.536000] apm: BIOS version 1.2 Flags 0x02 (Driver version 1.16ac)
[   84.536000] apm: overridden by ACPI.
[   87.132000] Bluetooth: Core ver 2.11
[   87.132000] NET: Registered protocol family 31
[   87.132000] Bluetooth: HCI device and connection manager initialized
[   87.132000] Bluetooth: HCI socket layer initialized
[   87.444000] Bluetooth: L2CAP ver 2.8
[   87.444000] Bluetooth: L2CAP socket layer initialized
[   87.492000] Bluetooth: RFCOMM socket layer initialized
[   87.492000] Bluetooth: RFCOMM TTY layer initialized
[   87.492000] Bluetooth: RFCOMM ver 1.8
[  125.148000] NET: Registered protocol family 10
[  125.148000] lo: Disabled Privacy Extensions

---

### Post by freshr on 2007-06-17
Any clues? Just a couple of pointers for where to look would be appreciated. Thanks!

---

### Post by borris.morris on 2007-06-22
You may need to enter the ra0 interface into the /etc/network/interfaces file. just follow the wlan0 setting, but instead replace ra0 for wlan0.

---

### Post by freshr on 2007-06-27
Hmm... I don't have a wlan0 setting in the interfaces file... The file reads:

auto lo
iface lo inet loopback

That's it! I'll try to find out more about this file in the meantime, but any more advice would be appreciated. I'll post back here if I manage to make any progress.

Cheers.

---

### Post by borris.morris on 2007-07-02
actually, it looks like hardware. judging by your lspci your hardware isn't working mine reads like this...

00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:02.0 CardBus bridge: Texas Instruments PCI1450 (rev 03)
00:02.1 CardBus bridge: Texas Instruments PCI1450 (rev 03)
00:03.0 Communication controller: Agere Systems WinModem 56k (rev 01)
00:06.0 Multimedia audio controller: Cirrus Logic CS 4614/22/24/30 [CrystalClear SoundFusion Audio Accelerator] (rev 01)
00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 03)
01:00.0 VGA compatible controller: Neomagic Corporation NM2360 [MagicMedia 256ZX]
06:00.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)


See that last line, yours doesn't have it.

---

