---
title: "ndiswrapper broadcom"
date: 2007-03-15
forum: Networking &amp; Wireless
---

### Post by dacool25 on 2007-03-15
So, i've been trying to get my wireless card to work for the past 3 days or so on ubuntu.  I have the 4318 broadcom, and i've installed ndiswrapper.  i had it so that my wireless card showed up in system > administration > networking, but then tried what they said in this forum ([http://www.ubuntuforums.org/showthread.php?t=223729](http://www.ubuntuforums.org/showthread.php?t=223729)) ... it was [HTML]sudo gedit /etc/modprobe.d/blacklist

add: "blacklist bcm43xx" (no quotes) and save the file

from the command line type in:

sudo modprobe -r bcm43xx

then

sudo modprobe ndiswrapper[/HTML] Anyways, now i don't have anything in networking and i really have no where to go.  Even when it was in there my light didn't come on.  I know this topic has been beaten to death, but i still can't seem to get it to work.  Here are some of my read outs...

**dmesg**
[HTML][17179569.184000] Linux version 2.6.17-11-generic (root@terranova) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Thu Feb 1 19:52:28 UTC 2007 (Ubuntu 2.6.17-11.35-generic)
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[17179569.184000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000d2000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 0000000027ef0000 (usable)
[17179569.184000]  BIOS-e820: 0000000027ef0000 - 0000000027eff000 (ACPI data)
[17179569.184000]  BIOS-e820: 0000000027eff000 - 0000000027f00000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 0000000027f00000 - 0000000030000000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 638MB LOWMEM available.
[17179569.184000] found SMP MP-table at 000f8130
[17179569.184000] On node 0 totalpages: 163568
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   Normal zone: 159472 pages, LIFO batch:31
[17179569.184000] DMI present.
[17179569.184000] ACPI: RSDP (v000 HP                                    ) @ 0x000f8080
[17179569.184000] ACPI: RSDT (v001 HP     3096     0x20040830  LTP 0x00000000) @ 0x27ef8bf0
[17179569.184000] ACPI: FADT (v001 HP     3096     0x20040830 PTL  0x0000005f) @ 0x27efee4b
[17179569.184000] ACPI: SSDT (v001 PTLTD  POWERNOW 0x20040830  LTP 0x00000001) @ 0x27efeebf
[17179569.184000] ACPI: MADT (v001 PTLTD         3096   0x20040830  LTP 0x00000000) @ 0x27efef74
[17179569.184000] ACPI: MCFG (v001 PTLTD    MCFG   0x20040830  LTP 0x00000000) @ 0x27efefc4
[17179569.184000] ACPI: DSDT (v001 HP     3091     0x20040830 MSFT 0x0100000e) @ 0x00000000
[17179569.184000] ATI board detected. Disabling timer routing over 8254.
[17179569.184000] ACPI: PM-Timer IO Port: 0x8008
[17179569.184000] ACPI: Local APIC address 0xfee00000
[17179569.184000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[17179569.184000] Processor #0 15:4 APIC version 16
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[17179569.184000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[17179569.184000] IOAPIC[0]: apic_id 1, version 33, address 0xfec00000, GSI 0-23
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 21 low level)
[17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[17179569.184000] Using ACPI (MADT) for SMP configuration information
[17179569.184000] Allocating PCI resources starting at 40000000 (gap: 30000000:cec00000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hda2 ro quiet splash
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
[17179569.184000] Enabling fast FPU save and restore... done.
[17179569.184000] Enabling unmasked SIMD FPU exception support... done.
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[17179569.184000] Detected 1592.097 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179573.064000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[17179573.064000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179573.080000] Memory: 638560k/654272k available (1911k kernel code, 15032k reserved, 1073k data, 308k init, 0k highmem)
[17179573.080000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179573.160000] Calibrating delay using timer specific routine.. 3189.13 BogoMIPS (lpj=6378261)
[17179573.160000] Security Framework v1.0.0 initialized
[17179573.160000] SELinux:  Disabled at boot.
[17179573.160000] Mount-cache hash table entries: 512
[17179573.160000] CPU: After generic identify, caps: 078bfbff e3d3fbff 00000000 00000000 00000001 00000000 00000001
[17179573.160000] CPU: After vendor identify, caps: 078bfbff e3d3fbff 00000000 00000000 00000001 00000000 00000001
[17179573.160000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[17179573.160000] CPU: L2 Cache: 512K (64 bytes/line)
[17179573.160000] CPU: After all inits, caps: 078bfbff e3d3fbff 00000000 00000410 00000001 00000000 00000001
[17179573.160000] Checking 'hlt' instruction... OK.
[17179573.176000] SMP alternatives: switching to UP code
[17179573.176000] Freeing SMP alternatives: 16k freed
[17179573.176000] checking if image is initramfs... it is
[17179573.740000] Freeing initrd memory: 5327k freed
[17179573.740000] ACPI: Core revision 20060707
[17179573.740000] ACPI: Looking for DSDT ... not found!
[17179573.744000] CPU0: AMD Turion(tm) 64 Mobile Technology ML-28 stepping 02
[17179573.744000] Total of 1 processors activated (3189.13 BogoMIPS).
[17179573.744000] ENABLING IO-APIC IRQs
[17179573.744000] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
[17179573.888000] Brought up 1 CPUs
[17179573.888000] migration_cost=0
[17179573.888000] NET: Registered protocol family 16
[17179573.888000] EISA bus registered
[17179573.888000] ACPI: bus type pci registered
[17179573.888000] PCI: BIOS Bug: MCFG area at e0000000 is not E820-reserved
[17179573.888000] PCI: Not using MMCONFIG.
[17179573.888000] PCI: PCI BIOS revision 2.10 entry at 0xfd8bc, last bus=5
[17179573.888000] PCI: Using configuration type 1
[17179573.888000] Setting up standard PCI resources
[17179573.888000] ACPI: Interpreter enabled
[17179573.888000] ACPI: Using IOAPIC for interrupt routing
[17179573.888000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179573.888000] PCI: Probing PCI hardware (bus 00)
[17179573.892000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:14.1
[17179573.892000] Boot video device is 0000:01:05.0
[17179573.892000] PCI: Transparent bridge - 0000:00:14.4
[17179573.892000] PCI: Bus #06 (-#09) is hidden behind transparent bridge #05 (-#05) (try 'pci=assign-busses')
[17179573.892000] Please report the result to linux-kernel to fix this permanently
[17179573.892000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179573.896000] ACPI: PCI Interrupt Link [LNKA] (IRQs 10 11) *0, disabled.
[17179573.896000] ACPI: PCI Interrupt Link [LNKB] (IRQs 10 11) *0, disabled.
[17179573.896000] ACPI: PCI Interrupt Link [LNKC] (IRQs 10 11) *0, disabled.
[17179573.896000] ACPI: PCI Interrupt Link [LNKD] (IRQs 10 11) *0, disabled.
[17179573.896000] ACPI: PCI Interrupt Link [LNKE] (IRQs 10 11) *0, disabled.
[17179573.896000] ACPI: PCI Interrupt Link [LNKF] (IRQs 10 11) *0, disabled.
[17179573.896000] ACPI: PCI Interrupt Link [LNKG] (IRQs 10 11) *0, disabled.
[17179573.896000] ACPI: PCI Interrupt Link [LNKH] (IRQs 10 11) *0, disabled.
[17179573.896000] ACPI: Embedded Controller [EC0] (gpe 24) interrupt mode.
[17179573.900000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[17179573.900000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[17179573.900000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179573.900000] pnp: PnP ACPI init
[17179573.904000] pnp: PnP ACPI: found 10 devices
[17179573.904000] PnPBIOS: Disabled by ACPI PNP
[17179573.904000] PCI: Using ACPI for IRQ routing
[17179573.904000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179573.916000] pnp: 00:08: ioport range 0x1080-0x1080 has been reserved
[17179573.916000] pnp: 00:08: ioport range 0x220-0x22f has been reserved
[17179573.916000] pnp: 00:08: ioport range 0x40b-0x40b has been reserved
[17179573.916000] pnp: 00:08: ioport range 0x4d0-0x4d1 has been reserved
[17179573.920000] PCI: Bridge: 0000:00:01.0
[17179573.920000]   IO window: 9000-9fff
[17179573.920000]   MEM window: c0100000-c01fffff
[17179573.920000]   PREFETCH window: c8000000-cfffffff
[17179573.920000] PCI: Bus 6, cardbus bridge: 0000:05:09.0
[17179573.920000]   IO window: 0000a400-0000a4ff
[17179573.920000]   IO window: 0000a800-0000a8ff
[17179573.920000]   PREFETCH window: 40000000-41ffffff
[17179573.920000]   MEM window: 42000000-43ffffff
[17179573.920000] PCI: Bridge: 0000:00:14.4
[17179573.920000]   IO window: a000-afff
[17179573.920000]   MEM window: c0200000-c02fffff
[17179573.920000]   PREFETCH window: 40000000-41ffffff
[17179573.920000] ACPI: PCI Interrupt 0000:05:09.0[A] -> GSI 17 (level, low) -> IRQ 185
[17179573.920000] PCI: Setting latency timer of device 0000:05:09.0 to 64
[17179573.920000] NET: Registered protocol family 2
[17179573.960000] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179573.960000] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[17179573.960000] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[17179573.960000] TCP: Hash tables configured (established 131072 bind 65536)
[17179573.960000] TCP reno registered
[17179573.960000] audit: initializing netlink socket (disabled)
[17179573.960000] audit(1173976066.960:1): initialized
[17179573.960000] VFS: Disk quotas dquot_6.5.1
[17179573.960000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179573.960000] Initializing Cryptographic API
[17179573.960000] io scheduler noop registered
[17179573.960000] io scheduler anticipatory registered
[17179573.960000] io scheduler deadline registered
[17179573.960000] io scheduler cfq registered (default)
[17179573.960000] isapnp: Scanning for PnP cards...
[17179574.316000] isapnp: No Plug & Play device found
[17179574.340000] Real Time Clock Driver v1.12ac
[17179574.340000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[17179574.340000] ACPI: PCI Interrupt 0000:00:14.6[B] -> GSI 17 (level, low) -> IRQ 185
[17179574.340000] ACPI: PCI interrupt for device 0000:00:14.6 disabled
[17179574.340000] mice: PS/2 mouse device common for all mice
[17179574.340000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179574.340000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179574.340000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179574.340000] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[17179574.352000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179574.352000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179574.352000] EISA: Probing bus 0 at eisa.0
[17179574.352000] Cannot allocate resource for EISA slot 1
[17179574.356000] Cannot allocate resource for EISA slot 8
[17179574.356000] EISA: Detected 0 cards.
[17179574.356000] TCP bic registered
[17179574.356000] NET: Registered protocol family 1
[17179574.356000] NET: Registered protocol family 8
[17179574.356000] NET: Registered protocol family 20
[17179574.356000] Using IPI No-Shortcut mode
[17179574.356000] ACPI: (supports S0 S3 S4 S5)
[17179574.356000] Freeing unused kernel memory: 308k freed
[17179574.448000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179575.484000] Capability LSM initialized
[17179575.516000] ACPI: CPU0 (power states: C1[C1] C2[C2])
[17179575.516000] ACPI: Processor [CPU0] (supports 8 throttling states)
[17179575.520000] ACPI: Thermal Zone [THRM] (62 C)
[17179575.852000] ATIIXP: IDE controller at PCI slot 0000:00:14.1
[17179575.852000] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 193
[17179575.852000] ATIIXP: chipset revision 0
[17179575.852000] ATIIXP: not 100% native mode: will probe irqs later
[17179575.852000]     ide0: BM-DMA at 0x8410-0x8417, BIOS settings: hda:DMA, hdb:pio
[17179575.852000]     ide1: BM-DMA at 0x8418-0x841f, BIOS settings: hdc:DMA, hdd:pio
[17179575.852000] Probing IDE interface ide0...
[17179576.140000] hda: IC25N060ATMR04-0, ATA DISK drive
[17179576.812000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179576.832000] Probing IDE interface ide1...
[17179577.572000] hdc: DV-28E-N, ATAPI CD/DVD-ROM drive
[17179578.244000] ide1 at 0x170-0x177,0x376 on irq 15
[17179578.252000] hda: max request size: 512KiB
[17179578.260000] hda: 117210240 sectors (60011 MB) w/7884KiB Cache, CHS=16383/255/63, UDMA(100)
[17179578.260000] hda: cache flushes supported
[17179578.260000]  hda: hda1 hda2 hda3
[17179578.348000] hdc: ATAPI 24X DVD-ROM drive, 256kB Cache, DMA
[17179578.348000] Uniform CD-ROM driver Revision: 3.20
[17179578.700000] usbcore: registered new driver usbfs
[17179578.700000] usbcore: registered new driver hub
[17179578.704000] ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[17179578.704000] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 19 (level, low) -> IRQ 201
[17179578.704000] ohci_hcd 0000:00:13.0: OHCI Host Controller
[17179578.704000] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
[17179579.092000] ohci_hcd 0000:00:13.0: irq 201, io mem 0xc0000000
[17179579.152000] usb usb1: configuration #1 chosen from 1 choice
[17179579.152000] hub 1-0:1.0: USB hub found
[17179579.152000] hub 1-0:1.0: 4 ports detected
[17179579.256000] ACPI: PCI Interrupt 0000:00:13.2[A] -> GSI 19 (level, low) -> IRQ 201
[17179579.256000] ehci_hcd 0000:00:13.2: EHCI Host Controller
[17179579.256000] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2
[17179579.256000] ehci_hcd 0000:00:13.2: irq 201, io mem 0xc0002000
[17179579.256000] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179579.256000] usb usb2: configuration #1 chosen from 1 choice
[17179579.256000] hub 2-0:1.0: USB hub found
[17179579.256000] hub 2-0:1.0: 8 ports detected
[17179579.360000] ACPI: PCI Interrupt 0000:00:13.1[A] -> GSI 19 (level, low) -> IRQ 201
[17179579.360000] ohci_hcd 0000:00:13.1: OHCI Host Controller
[17179579.360000] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 3
[17179579.692000] ohci_hcd 0000:00:13.1: irq 201, io mem 0xc0001000
[17179579.752000] usb usb3: configuration #1 chosen from 1 choice
[17179579.752000] hub 3-0:1.0: USB hub found
[17179579.752000] hub 3-0:1.0: 4 ports detected
[17179579.928000] Attempting manual resume
[17179579.980000] usb 1-1: new full speed USB device using ohci_hcd and address 2
[17179579.988000] kjournald starting.  Commit interval 5 seconds
[17179579.988000] EXT3-fs: mounted filesystem with ordered data mode.
[17179580.176000] usb 1-1: not running at top speed; connect to a high speed hub
[17179580.188000] usb 1-1: configuration #1 chosen from 1 choice
[17179580.496000] usb 3-1: new low speed USB device using ohci_hcd and address 2
[17179580.712000] usb 3-1: configuration #1 chosen from 1 choice
[17179596.524000] input: PC Speaker as /class/input/input1
[17179597.220000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179597.228000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179597.272000] Synaptics Touchpad, model: 1, fw: 5.10, id: 0x258eb1, caps: 0xa04713/0x0
[17179597.308000] input: SynPS/2 Synaptics TouchPad as /class/input/input2
[17179597.356000] 8139too Fast Ethernet driver 0.9.27
[17179597.356000] ACPI: PCI Interrupt 0000:05:00.0[A] -> GSI 18 (level, low) -> IRQ 209
[17179597.356000] eth0: RealTek RTL8139 at 0xe886e000, 00:c0:9f:d1:3d:8c, IRQ 209
[17179597.356000] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[17179597.372000] 8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
[17179597.604000] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[17179597.632000] Linux agpgart interface v0.101 (c) Dave Jones
[17179597.768000] ACPI: PCI Interrupt 0000:05:09.0[A] -> GSI 17 (level, low) -> IRQ 185
[17179597.768000] Yenta: CardBus bridge found at 0000:05:09.0 [103c:3091]
[17179597.768000] Yenta: Enabling burst memory read transactions
[17179597.768000] Yenta: Using CSCINT to route CSC interrupts to PCI
[17179597.768000] Yenta: Routing CardBus interrupts to PCI
[17179597.768000] Yenta TI: socket 0000:05:09.0, mfunc 0x01a01b22, devctl 0x66
[17179597.776000] ts: Compaq touchscreen protocol output
[17179597.816000] ieee80211_crypt: registered algorithm 'NULL'
[17179597.844000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[17179597.844000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[17179597.872000] usbcore: registered new driver hiddev
[17179597.928000] input: Microsoft Microsoft USB Wireless Mouse as /class/input/input3
[17179597.928000] input: USB HID v1.11 Mouse [Microsoft Microsoft USB Wireless Mouse] on usb-0000:00:13.1-1
[17179597.928000] usbcore: registered new driver usbhid
[17179597.928000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[17179597.952000] bcm43xx driver
[17179597.956000] usbcore: registered new driver libusual
[17179598.012000] Yenta: ISA IRQ mask 0x0ee8, PCI irq 185
[17179598.012000] Socket status: 30000006
[17179598.012000] Yenta: Raising subordinate bus# of parent bus (#05) from #05 to #09
[17179598.012000] pcmcia: parent PCI bridge I/O window: 0xa000 - 0xafff
[17179598.012000] cs: IO port probe 0xa000-0xafff: clean.
[17179598.012000] pcmcia: parent PCI bridge Memory window: 0xc0200000 - 0xc02fffff
[17179598.012000] pcmcia: parent PCI bridge Memory window: 0x40000000 - 0x41ffffff
[17179598.020000] ACPI: PCI Interrupt 0000:00:14.6[B] -> GSI 17 (level, low) -> IRQ 185
[17179598.052000] SCSI subsystem initialized
[17179598.052000] Initializing USB Mass Storage driver...
[17179598.072000] scsi0 : SCSI emulation for USB Mass Storage devices
[17179598.072000] usbcore: registered new driver usb-storage
[17179598.072000] USB Mass Storage support registered.
[17179598.072000] usb-storage: device found at 2
[17179598.072000] usb-storage: waiting for device to settle before scanning
[17179598.132000] MC'97 0 converters and GPIO not ready (0x1)
[17179598.132000] ACPI: PCI Interrupt 0000:00:14.5[B] -> GSI 17 (level, low) -> IRQ 185
[17179598.140000] ACPI: PCI Interrupt 0000:05:02.0[A] -> GSI 20 (level, low) -> IRQ 217
[17179598.452000] cs: IO port probe 0x100-0x3af: clean.
[17179598.456000] cs: IO port probe 0x3e0-0x4ff: clean.
[17179598.456000] cs: IO port probe 0x820-0x8ff: excluding 0x878-0x87f
[17179598.456000] cs: IO port probe 0xc00-0xcf7: excluding 0xc00-0xc07 0xc10-0xc17 0xc50-0xc57 0xc68-0xc6f 0xcd0-0xcdf
[17179598.460000] cs: IO port probe 0xa00-0xaff: clean.
[17179598.508000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[17179598.516000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[17179598.664000] NET: Registered protocol family 17
[17179598.668000] lp: driver loaded but no devices found
[17179598.696000] Adding 1052248k swap on /dev/disk/by-uuid/3bb31a84-bfb9-43aa-8ec3-c52042dd11b2.  Priority:-1 extents:1 across:1052248k
[17179598.800000] EXT3 FS on hda2, internal journal
[17179599.044000] NTFS driver 2.1.27 [Flags: R/O MODULE].
[17179599.120000] NTFS volume version 3.1.
[17179603.072000] usb-storage: device scan complete
[17179603.076000]   Vendor: Best Buy  Model: Geek Squad U3     Rev: 6.15
[17179603.076000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17179603.084000]   Vendor: Best Buy  Model: Geek Squad U3     Rev: 6.15
[17179603.084000]   Type:   CD-ROM                             ANSI SCSI revision: 00
[17179603.164000] SCSI device sda: 1994751 512-byte hdwr sectors (1021 MB)
[17179603.172000] sda: Write Protect is off
[17179603.172000] sda: Mode Sense: 45 00 00 08
[17179603.172000] sda: assuming drive cache: write through
[17179603.188000] SCSI device sda: 1994751 512-byte hdwr sectors (1021 MB)
[17179603.196000] sda: Write Protect is off
[17179603.196000] sda: Mode Sense: 45 00 00 08
[17179603.196000] sda: assuming drive cache: write through
[17179603.196000]  sda: sda1
[17179603.216000] sd 0:0:0:0: Attached scsi removable disk sda
[17179603.232000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[17179603.232000] sr 0:0:0:1: Attached scsi generic sg1 type 5
[17179603.348000] sr0: scsi3-mmc drive: 8x/40x writer xa/form2 cdda tray
[17179603.352000] sr 0:0:0:1: Attached scsi CD-ROM sr0
[17179603.752000] ACPI: AC Adapter [ACAD] (on-line)
[17179603.844000] ACPI: Battery Slot [BAT1] (battery present)
[17179603.880000] ACPI: Power Button (FF) [PWRF]
[17179603.880000] ACPI: Power Button (CM) [PWRB]
[17179603.880000] ACPI: Sleep Button (CM) [SLPB]
[17179603.880000] ACPI: Lid Switch [LID]
[17179604.088000] ibm_acpi: ec object not found
[17179604.120000] pcc_acpi: loading...
[17179604.172000] wmi_add device=dff5f400
[17179604.172000] calling WQBA
[17179604.232000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[17179604.456000] powernow-k8: Found 1 AMD Athlon 64 / Opteron processors (version 1.60.2)
[17179604.456000] powernow-k8:    0 : fid 0x8 (1600 MHz), vid 0x4 (1450 mV)
[17179604.456000] powernow-k8:    1 : fid 0x0 (800 MHz), vid 0x16 (1000 mV)
[17179604.456000] cpu_init done, current fid 0x8, vid 0x4
[17179607.468000] apm: BIOS not found.
[17179611.868000] NET: Registered protocol family 10
[17179611.868000] lo: Disabled Privacy Extensions
[17179611.868000] IPv6 over IPv4 tunneling driver
[17179612.104000] Bluetooth: Core ver 2.8
[17179612.104000] NET: Registered protocol family 31
[17179612.104000] Bluetooth: HCI device and connection manager initialized
[17179612.104000] Bluetooth: HCI socket layer initialized
[17179612.156000] Bluetooth: L2CAP ver 2.8
[17179612.156000] Bluetooth: L2CAP socket layer initialized
[17179612.160000] Bluetooth: RFCOMM socket layer initialized
[17179612.160000] Bluetooth: RFCOMM TTY layer initialized
[17179612.160000] Bluetooth: RFCOMM ver 1.7
[17179622.580000] eth0: no IPv6 routers present
[17179622.628000] UDF-fs: No VRS found
[17179622.752000] UDF-fs: No VRS found
[17179623.152000] ISO 9660 Extensions: Microsoft Joliet Level 3
[17179623.160000] ISOFS: changing to secondary root
[17179623.576000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[17180556.512000] ndiswrapper version 1.22 loaded (preempt=no,smp=yes)
[17181491.092000] ieee80211_crypt: registered algorithm 'WEP'
[17181491.216000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[17181491.232000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[17181748.116000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[17181748.132000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[17181810.676000] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[17181821.184000] eth0: no IPv6 routers present
[17182589.624000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[17182589.640000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[17183271.208000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[17183271.224000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[17183544.996000] ACPI: PCI interrupt for device 0000:05:02.0 disabled
[/HTML]

**ifconfig (p.s) i'm hardwired right now**
[HTML]eth0      Link encap:Ethernet  HWaddr 00:C0:9F:D1:3D:8C  
          inet addr:192.168.1.65  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2c0:9fff:fed1:3d8c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11745 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8590 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:12391264 (11.8 MiB)  TX bytes:996073 (972.7 KiB)
          Interrupt:209 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:28 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1400 (1.3 KiB)  TX bytes:1400 (1.3 KiB)
[/HTML]

**iwconfig**
[HTML]lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.[/HTML]

so is there anyone that can help me? aim would be great... dacool25 or post.

---

### Post by spd106 on 2007-03-15
What do you get with these three commands?```

sudo lshw -class network
sudo ndiswrapper -v
lsmod | grep bcm
```

---

### Post by breakuoff on 2007-03-16
yes im having a simular problem have power light on card but unable to manualy set essid or scann for networks broadcom shows up as eth0

---

