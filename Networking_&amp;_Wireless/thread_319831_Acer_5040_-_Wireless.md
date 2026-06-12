---
title: "Acer 5040 - Wireless"
date: 2006-12-16
forum: Networking &amp; Wireless
---

### Post by Rubens V on 2006-12-16
Hi,

I'm trying to configure my wireless card on my Notebook Aspire 5040 on a Ubuntu 6.10 x64.

After some search in the Internet I find the acer_acpi Homepage ([http://www.archernar.co.uk/acer_acpi/acer_acpi_main.html](http://www.archernar.co.uk/acer_acpi/acer_acpi_main.html)) and now my led is on (light).

My question is a quite simple - what more I need to make my wireless works - I try to use the program Wireless  Assistant and I received de following message: no usable wireless  device found.

When I type de command dmesg:

[    0.000000] Bootdata ok (command line is root=/dev/hda7 ro quiet splash locale=pt_BR)
[    0.000000] Linux version 2.6.17-10-generic (root@king) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Tue Dec 5 21:16:35 UTC 2006 (Ubuntu 2.6.17-10.34-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009b800 (usable)
[    0.000000]  BIOS-e820: 000000000009b800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d2000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003bea0000 (usable)
[    0.000000]  BIOS-e820: 000000003bea0000 - 000000003bead000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003bead000 - 000000003bf00000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003bf00000 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP (v000 PTLTD                                 ) @ 0x00000000000f6d00
[    0.000000] ACPI: RSDT (v001 PTLTD    RSDT   0x06040000  LTP 0x00000000) @ 0x000000003bea7350
[    0.000000] ACPI: FADT (v001 ATI    Piranha  0x06040000 ATI  0x000f4240) @ 0x000000003beace20
[    0.000000] ACPI: SSDT (v001 PTLTD  POWERNOW 0x06040000  LTP 0x00000001) @ 0x000000003beace94
[    0.000000] ACPI: MADT (v001 PTLTD    APIC   0x06040000  LTP 0x00000000) @ 0x000000003beacf6a
[    0.000000] ACPI: MCFG (v001 PTLTD    MCFG   0x06040000  LTP 0x00000000) @ 0x000000003beacfc4
[    0.000000] ACPI: DSDT (v001    ATI    SB400 0x06040000 MSFT 0x0100000e) @ 0x0000000000000000
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] Number of nodes 1
[    0.000000] Node 0 MemBase 0000000000000000 Limit 000000003bea0000
[    0.000000] NUMA: Using 63 for the hash shift.
[    0.000000] Using node hash shift of 63
[    0.000000] Bootmem setup node 0 0000000000000000-000000003bea0000
[    0.000000] On node 0 totalpages: 240601
[    0.000000]   DMA zone: 2588 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 238013 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x8008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:4 APIC version 16
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 21 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] Setting APIC routing to physical flat
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:bec00000)
[    0.000000] Checking aperture...
[    0.000000] CPU 0: aperture @ 1ff4000000 size 32 MB
[    0.000000] Aperture from northbridge cpu 0 too small (32 MB)
[    0.000000] No AGP bridge found
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] Built 1 zonelists
[    0.000000] Kernel command line: root=/dev/hda7 ro quiet splash locale=pt_BR
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] time.c: Using 3.579545 MHz WALL PM GTOD PIT/TSC timer.
[    0.000000] time.c: Detected 1800.126 MHz processor.
[   11.725947] Console: colour VGA+ 80x25
[   11.727146] Dentry cache hash table entries: 131072 (order: 8, 1048576 bytes)
[   11.727955] Inode-cache hash table entries: 65536 (order: 7, 524288 bytes)
[   11.743665] Memory: 954996k/981632k available (2129k kernel code, 26232k reserved, 1424k data, 188k init)
[   11.822965] Calibrating delay using timer specific routine.. 3603.87 BogoMIPS (lpj=7207754)
[   11.823035] Security Framework v1.0.0 initialized
[   11.823043] SELinux:  Disabled at boot.
[   11.823069] Mount-cache hash table entries: 256
[   11.823263] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   11.823266] CPU: L2 Cache: 1024K (64 bytes/line)
[   11.823271] CPU 0/0(1) -> Node 0 -> Core 0
[   11.823290] SMP alternatives: switching to UP code
[   11.823551] Freeing SMP alternatives: 20k freed
[   11.823717] checking if image is initramfs... it is
[   12.377770] Freeing initrd memory: 5746k freed
[   12.384574] ACPI: Core revision 20060707
[   12.387370] ACPI: Looking for DSDT ... not found!
[   12.432020] Using local APIC timer interrupts.
[   12.487491] result 12500883
[   12.487494] Detected 12.500 MHz APIC timer.
[   12.490054] Brought up 1 CPUs
[   12.490092] testing NMI watchdog ... OK.
[   12.530119] migration_cost=0
[   12.530402] NET: Registered protocol family 16
[   12.530427] ACPI: bus type pci registered
[   12.530433] PCI: BIOS Bug: MCFG area at e0000000 is not E820-reserved
[   12.530436] PCI: Not using MMCONFIG.
[   12.530444] PCI: Using configuration type 1
[   12.534817] ACPI: Interpreter enabled
[   12.534820] ACPI: Using IOAPIC for interrupt routing
[   12.535349] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   12.535353] PCI: Probing PCI hardware (bus 00)
[   12.538564] PCI: Ignoring BAR0-3 of IDE controller 0000:00:14.1
[   12.538886] Boot video device is 0000:01:05.0
[   12.539255] PCI: Transparent bridge - 0000:00:14.4
[   12.539332] PCI: Bus #07 (-#0a) is hidden behind transparent bridge #06 (-#07) (try 'pci=assign-busses')
[   12.539335] Please report the result to linux-kernel to fix this permanently
[   12.539361] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   12.542111] ACPI: PCI Interrupt Link [LNKA] (IRQs 10 11) *0, disabled.
[   12.542369] ACPI: PCI Interrupt Link [LNKB] (IRQs 10 11) *0, disabled.
[   12.542614] ACPI: PCI Interrupt Link [LNKC] (IRQs 10 11) *0, disabled.
[   12.542872] ACPI: PCI Interrupt Link [LNKD] (IRQs 10 11) *0, disabled.
[   12.543125] ACPI: PCI Interrupt Link [LNKE] (IRQs 10 11) *0, disabled.
[   12.543377] ACPI: PCI Interrupt Link [LNKF] (IRQs 10 11) *0, disabled.
[   12.543623] ACPI: PCI Interrupt Link [LNKG] (IRQs 10 11) *0, disabled.
[   12.543874] ACPI: PCI Interrupt Link [LNKH] (IRQs 10 11) *0, disabled.
[   12.544433] ACPI: Embedded Controller [EC0] (gpe 3) interrupt mode.
[   13.193330] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[   13.193657] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[   13.194075] Linux Plug and Play Support v0.97 (c) Adam Belay
[   13.194084] pnp: PnP ACPI init
[   13.300946] pnp: PnP ACPI: found 10 devices
[   13.300997] PCI: Using ACPI for IRQ routing
[   13.301000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   13.301125] PCI-DMA: Disabling IOMMU.
[   13.301347] pnp: 00:08: ioport range 0x1080-0x1080 has been reserved
[   13.301350] pnp: 00:08: ioport range 0x1200-0x120f has been reserved
[   13.301354] pnp: 00:08: ioport range 0x500-0x51f has been reserved
[   13.301357] pnp: 00:08: ioport range 0x40b-0x40b has been reserved
[   13.301540] PCI: Bridge: 0000:00:01.0
[   13.301543]   IO window: 9000-9fff
[   13.301547]   MEM window: d0100000-d01fffff
[   13.301550]   PREFETCH window: d4000000-d7ffffff
[   13.301561] PCI: Bus 7, cardbus bridge: 0000:06:06.0
[   13.301564]   IO window: 0000a400-0000a4ff
[   13.301570]   IO window: 0000a800-0000a8ff
[   13.301577]   PREFETCH window: 50000000-51ffffff
[   13.301583]   MEM window: 54000000-55ffffff
[   13.301589] PCI: Bridge: 0000:00:14.4
[   13.301593]   IO window: a000-afff
[   13.301600]   MEM window: d0200000-d02fffff
[   13.301605]   PREFETCH window: 50000000-52ffffff
[   13.301643] GSI 16 sharing vector 0xB1 and IRQ 16
[   13.301647] ACPI: PCI Interrupt 0000:06:06.0[A] -> GSI 20 (level, low) -> IRQ 177
[   13.301710] NET: Registered protocol family 2
[   13.336803] IP route cache hash table entries: 32768 (order: 6, 262144 bytes)
[   13.337224] TCP established hash table entries: 131072 (order: 9, 2097152 bytes)
[   13.339585] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   13.340777] TCP: Hash tables configured (established 131072 bind 65536)
[   13.340782] TCP reno registered
[   13.341243] IA32 emulation $Id: sys_ia32.c,v 1.32 2002/03/24 13:02:28 ak Exp $
[   13.341642] audit: initializing netlink socket (disabled)
[   13.341655] audit(1166267114.624:1): initialized
[   13.341842] VFS: Disk quotas dquot_6.5.1
[   13.341869] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   13.341926] Initializing Cryptographic API
[   13.341931] io scheduler noop registered
[   13.341939] io scheduler anticipatory registered
[   13.341948] io scheduler deadline registered
[   13.341965] io scheduler cfq registered (default)
[   13.364471] Real Time Clock Driver v1.12ac
[   13.364514] Linux agpgart interface v0.101 (c) Dave Jones
[   13.364518] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   13.365116] mice: PS/2 mouse device common for all mice
[   13.365673] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   13.365911] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   13.365917] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   13.366207] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   13.375111] i8042.c: Detected active multiplexing controller, rev 1.9.
[   13.378703] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[   13.379277] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[   13.379803] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[   13.380370] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[   13.380980] serio: i8042 KBD port at 0x60,0x64 irq 1
[   13.381275] TCP bic registered
[   13.381288] NET: Registered protocol family 1
[   13.381294] NET: Registered protocol family 8
[   13.381296] NET: Registered protocol family 20
[   13.384885] ACPI: (supports S0 S3 S4 S5)
[   13.384933] drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   13.384957] Freeing unused kernel memory: 188k freed
[   13.439144] vga16fb: initializing
[   13.439152] vga16fb: mapped to 0xffff8100000a0000
[   13.527489] Console: switching to colour frame buffer device 80x25
[   13.527494] fb0: VGA16 VGA frame buffer device
[   14.569198] Capability LSM initialized
[   14.600356] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   14.785531] input: AT Translated Set 2 keyboard as /class/input/input0
[   15.761275] ACPI: Thermal Zone [TZS0] (60 C)
[   16.228581] ACPI: Thermal Zone [TZS1] (56 C)
[   16.522608] ATIIXP: IDE controller at PCI slot 0000:00:14.1
[   16.522631] GSI 17 sharing vector 0xB9 and IRQ 17
[   16.522634] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 185
[   16.522646] ATIIXP: chipset revision 128
[   16.522648] ATIIXP: not 100% native mode: will probe irqs later
[   16.522659]     ide0: BM-DMA at 0x8410-0x8417, BIOS settings: hda:DMA, hdb:pio
[   16.522673]     ide1: BM-DMA at 0x8418-0x841f, BIOS settings: hdc:DMA, hdd:pio
[   16.522681] Probing IDE interface ide0...
[   16.808068] hda: ST980829A, ATA DISK drive
[   17.480463] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   17.551981] Probing IDE interface ide1...
[   18.285900] hdc: PIONEER DVD-RW DVR-K16RA, ATAPI CD/DVD-ROM drive
[   18.957399] ide1 at 0x170-0x177,0x376 on irq 15
[   18.975394] hda: max request size: 512KiB
[   18.982930] hda: 156301488 sectors (80026 MB) w/8192KiB Cache, CHS=16383/255/63, UDMA(100)
[   18.984911] hda: cache flushes supported
[   18.984954]  hda: hda1 hda3 < hda5 hda6 hda7 >
[   19.117292] hdc: ATAPI 24X DVD-ROM DVD-R CD-R/RW drive, 2000kB Cache, UDMA(33)
[   19.117301] Uniform CD-ROM driver Revision: 3.20
[   19.467386] usbcore: registered new driver usbfs
[   19.467409] usbcore: registered new driver hub
[   19.468185] ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[   19.468219] GSI 18 sharing vector 0xC1 and IRQ 18
[   19.468223] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 19 (level, low) -> IRQ 193
[   19.468609] ohci_hcd 0000:00:13.0: OHCI Host Controller
[   19.468769] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
[   19.700193] ohci_hcd 0000:00:13.0: irq 193, io mem 0xd0004000
[   19.759513] usb usb1: configuration #1 chosen from 1 choice
[   19.759612] hub 1-0:1.0: USB hub found
[   19.759629] hub 1-0:1.0: 4 ports detected
[   19.863307] ACPI: PCI Interrupt 0000:00:13.1[A] -> GSI 19 (level, low) -> IRQ 193
[   19.863607] ohci_hcd 0000:00:13.1: OHCI Host Controller
[   19.863843] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
[   20.078855] ohci_hcd 0000:00:13.1: irq 193, io mem 0xd0005000
[   20.138909] usb usb2: configuration #1 chosen from 1 choice
[   20.139007] hub 2-0:1.0: USB hub found
[   20.139022] hub 2-0:1.0: 4 ports detected
[   20.242745] ACPI: PCI Interrupt 0000:00:13.2[A] -> GSI 19 (level, low) -> IRQ 193
[   20.242893] ehci_hcd 0000:00:13.2: EHCI Host Controller
[   20.243139] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
[   20.243201] ehci_hcd 0000:00:13.2: irq 193, io mem 0xd0006000
[   20.243214] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   20.243382] usb usb3: configuration #1 chosen from 1 choice
[   20.243478] hub 3-0:1.0: USB hub found
[   20.243486] hub 3-0:1.0: 8 ports detected
[   20.386835] Attempting manual resume
[   20.417342] kjournald starting.  Commit interval 5 seconds
[   20.417354] EXT3-fs: mounted filesystem with ordered data mode.
[   20.586125] ohci_hcd 0000:00:13.1: wakeup
[   20.969534] usb 2-2: new low speed USB device using ohci_hcd and address 2
[   21.177289] usb 2-2: configuration #1 chosen from 1 choice
[   32.902245] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   32.910061] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   33.420042] input: PC Speaker as /class/input/input1
[   33.874854] ath_hal: module license 'Proprietary' taints kernel.
[   33.876984] ath_hal: 0.9.17.2 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   33.979663] r8169 Gigabit Ethernet driver 2.2LK loaded
[   33.979695] GSI 19 sharing vector 0xC9 and IRQ 19
[   33.979699] ACPI: PCI Interrupt 0000:06:07.0[A] -> GSI 23 (level, low) -> IRQ 201
[   33.979852] eth0: Identified chip type is 'RTL8169s/8110s'.
[   33.979857] eth0: RTL8169 at 0xffffc20000048000, 00:16:d3:44:29:97, IRQ 201
[   34.100723] r8169: eth0: link down
[   34.106133] ACPI: PCI Interrupt 0000:06:06.0[A] -> GSI 20 (level, low) -> IRQ 177
[   34.106145] Yenta: CardBus bridge found at 0000:06:06.0 [1025:0080]
[   34.106175] Yenta: Using CSCINT to route CSC interrupts to PCI
[   34.106177] Yenta: Routing CardBus interrupts to PCI
[   34.106184] Yenta TI: socket 0000:06:06.0, mfunc 0x01001002, devctl 0x44
[   34.125713] usbcore: registered new driver hiddev
[   34.132548] input: USB-compliant keyboard as /class/input/input2
[   34.132585] input: USB HID v1.10 Keyboard [USB-compliant keyboard] on usb-0000:00:13.1-2
[   34.141516] input: USB-compliant keyboard as /class/input/input3
[   34.141567] input: USB HID v1.10 Mouse [USB-compliant keyboard] on usb-0000:00:13.1-2
[   34.141577] usbcore: registered new driver usbhid
[   34.141580] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   34.158748] wlan: 0.8.4.2 (0.9.2)
[   34.160716] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x12a0b1, caps: 0xa04713/0x204000
[   34.169333] ath_rate_sample: 1.2 (0.9.2.1)
[   34.185144] ath_pci: 0.9.4.5 (0.9.2.1)
[   34.193277] input: SynPS/2 Synaptics TouchPad as /class/input/input4
[   34.195550] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[   34.320298] ts: Compaq touchscreen protocol output
[   34.334707] Yenta: ISA IRQ mask 0x0cf8, PCI irq 177
[   34.334712] Socket status: 30000006
[   34.334716] Yenta: Raising subordinate bus# of parent bus (#06) from #07 to #0a
[   34.334723] pcmcia: parent PCI bridge I/O window: 0xa000 - 0xafff
[   34.334727] pcmcia: parent PCI bridge Memory window: 0xd0200000 - 0xd02fffff
[   34.334731] pcmcia: parent PCI bridge Memory window: 0x50000000 - 0x52ffffff
[   34.338909] ACPI: PCI Interrupt 0000:00:14.2[A] -> GSI 16 (level, low) -> IRQ 185
[   34.674411] hsfhda: no version for "OsHdaCodecWallclock" found: kernel tainted.
[   35.024876] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[   35.176608] NET: Registered protocol family 17
[   35.687630] r8169: eth0: link up
[   37.290434] ttySHSF0 at MMIO 0x0 (irq = 1) is a Conexant HSF softmodem (HDA-14f12bfa:10250080-1)
[   37.337582] GSI 20 sharing vector 0xD1 and IRQ 20
[   37.337587] ACPI: PCI Interrupt 0000:06:05.0[A] -> GSI 21 (level, low) -> IRQ 209
[   37.340087] wifi%d: unable to attach hardware: 'Hardware revision not supported' (HAL status 13)
[   37.340107] ACPI: PCI interrupt for device 0000:06:05.0 disabled
[   37.558081] lp: driver loaded but no devices found
[   37.612332] Adding 522072k swap on /dev/disk/by-uuid/f0a05da8-02a5-44d0-be5b-adc8fe86e3fa.  Priority:-1 extents:1 across:522072k
[   37.731654] EXT3 FS on hda7, internal journal
[   38.267533] NET: Registered protocol family 10
[   38.267641] lo: Disabled Privacy Extensions
[   38.267799] IPv6 over IPv4 tunneling driver
[   38.820670] NTFS driver 2.1.27 [Flags: R/O MODULE].
[   38.887493] NTFS volume version 3.1.
[   45.888941] ACPI: AC Adapter [ADP1] (on-line)
[   48.928547] ACPI: Battery Slot [BAT0] (battery present)
[   48.942468] ACPI: Power Button (FF) [PWRF]
[   48.942484] ACPI: Lid Switch [LID0]
[   48.942494] ACPI: Sleep Button (CM) [SLPB]
[   49.000307] eth0: no IPv6 routers present
[   49.172954] ibm_acpi: ec object not found
[   49.203077] pcc_acpi: loading...
[   49.287232] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   49.519378] powernow-k8: Found 1 AMD Athlon 64 / Opteron processors (version 1.60.2)
[   49.519420] powernow-k8:    0 : fid 0xa (1800 MHz), vid 0x4 (1450 mV)
[   49.519423] powernow-k8:    1 : fid 0x8 (1600 MHz), vid 0x6 (1400 mV)
[   49.519427] powernow-k8:    2 : fid 0x0 (800 MHz), vid 0x16 (1000 mV)
[   49.519432] cpu_init done, current fid 0xa, vid 0x4
[   52.415694] [fglrx] Maximum main memory to use for locked dma buffers: 857 MBytes.
[   52.415976] [fglrx] module loaded - fglrx 8.31.5 [Nov  9 2006] on minor 0
[   52.512276] GSI 21 sharing vector 0xA9 and IRQ 21
[   52.512285] ACPI: PCI Interrupt 0000:01:05.0[A] -> GSI 17 (level, low) -> IRQ 169
[   54.267025] [fglrx] total      GART = 134217728
[   54.267031] [fglrx] free       GART = 118226944
[   54.267034] [fglrx] max single GART = 118226944
[   54.267036] [fglrx] total      LFB  = 60780544
[   54.267038] [fglrx] free       LFB  = 52588544
[   54.267041] [fglrx] max single LFB  = 52588544
[   54.267043] [fglrx] total      Inv  = 0
[   54.267045] [fglrx] free       Inv  = 0
[   54.267047] [fglrx] max single Inv  = 0
[   54.267049] [fglrx] total      TIM  = 0
[   58.754695] hda-intel: Invalid position buffer, using LPIB read method instead.
[   68.426020] Bluetooth: Core ver 2.8
[   68.426027] NET: Registered protocol family 31
[   68.426030] Bluetooth: HCI device and connection manager initialized
[   68.426049] Bluetooth: HCI socket layer initialized
[   68.522168] Bluetooth: L2CAP ver 2.8
[   68.522172] Bluetooth: L2CAP socket layer initialized
[   68.625725] Bluetooth: RFCOMM socket layer initialized
[   68.625746] Bluetooth: RFCOMM TTY layer initialized
[   68.625749] Bluetooth: RFCOMM ver 1.7
[  269.501333] acer_acpi: Acer Laptop ACPI Extras version 0.3
[ 1881.347753] acer_acpi: Wireless value 1


Thanks,

Rubens

---

