---
title: "Wireless card help please"
date: 2007-05-26
forum: Networking &amp; Wireless
---

### Post by Major Pen0r on 2007-05-26
Yea my wireless card worked with window but i went to ubuntu awhile back and it wont detect my card...and i was wondering if anyone could help me...i have and Acer Aspire 3000 with a Acer InviLink 802.11b/g wireless card

---

### Post by digitalbenji on 2007-05-26
Hi,
   I believe this card should work with the bcm43xx driver.  I'm not sure if that driver requires ndiswrapper or not.  What version of Ubuntu are you using?  Can you also print the results of lspci and dmesg from the terminal, so we can try to see if you have the driver installed or not.

---

### Post by Major Pen0r on 2007-05-26
and i have fiesty

**_lspci results_**

00:00.0 Host bridge: Silicon Integrated Systems [SiS] 760/M760 Host (rev 03)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SG86C202
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 25)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
00:06.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)
00:0b.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760/761 PCI/AGP VGA Display Adapter

[B][U]
dmesg results[/U][/B]

[17179569.184000] Linux version 2.6.17-11-generic (root@terranova) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Fri May 18 23:39:08 UTC 2007 (Ubuntu 2.6.17-11.38-generic)
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009f400 (usable)
[17179569.184000]  BIOS-e820: 000000000009f400 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000000bef0000 (usable)
[17179569.184000]  BIOS-e820: 000000000bef0000 - 000000000befa000 (ACPI data)
[17179569.184000]  BIOS-e820: 000000000befa000 - 000000000bf00000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 000000000bf00000 - 0000000010000000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 190MB LOWMEM available.
[17179569.184000] found SMP MP-table at 000f7fd0
[17179569.184000] On node 0 totalpages: 48880
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   Normal zone: 44784 pages, LIFO batch:7
[17179569.184000] DMI present.
[17179569.184000] ACPI: RSDP (v000 PTLTD                                 ) @ 0x000f7f60
[17179569.184000] ACPI: RSDT (v001 PTLTD    RSDT   0x06040000  LTP 0x00000000) @ 0x0bef619d
[17179569.184000] ACPI: FADT (v001 SiS    755F     0x06040000 PTL  0x000f4240) @ 0x0bef9e3e
[17179569.184000] ACPI: SSDT (v001 PTLTD  POWERNOW 0x06040000  LTP 0x00000001) @ 0x0bef9eb2
[17179569.184000] ACPI: MADT (v001 PTLTD         APIC   0x06040000  LTP 0x00000000) @ 0x0bef9f88
[17179569.184000] ACPI: BOOT (v001 PTLTD  $SBFTBL$ 0x06040000  LTP 0x00000001) @ 0x0bef9fd8
[17179569.184000] ACPI: DSDT (v001 PTLTD       755 0x06040000 MSFT 0x0100000e) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x8008
[17179569.184000] ACPI: Local APIC address 0xfee00000
[17179569.184000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[17179569.184000] Processor #0 15:12 APIC version 16
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[17179569.184000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[17179569.184000] IOAPIC[0]: apic_id 1, version 17, address 0xfec00000, GSI 0-23
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
[17179569.184000] ACPI: IRQ0 used by override.
[17179569.184000] ACPI: IRQ2 used by override.
[17179569.184000] ACPI: IRQ11 used by override.
[17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[17179569.184000] Using ACPI (MADT) for SMP configuration information
[17179569.184000] Allocating PCI resources starting at 20000000 (gap: 10000000:eff00000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hda1 ro quiet splash
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
[17179569.184000] Enabling fast FPU save and restore... done.
[17179569.184000] Enabling unmasked SIMD FPU exception support... done.
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 1024 (order: 10, 4096 bytes)
[17179569.184000] Detected 1800.301 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179572.144000] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179572.144000] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
[17179572.148000] Memory: 184160k/195520k available (1911k kernel code, 10852k reserved, 1073k data, 308k init, 0k highmem)
[17179572.148000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179572.228000] Calibrating delay using timer specific routine.. 3602.72 BogoMIPS (lpj=7205441)
[17179572.228000] Security Framework v1.0.0 initialized
[17179572.228000] SELinux:  Disabled at boot.
[17179572.228000] Mount-cache hash table entries: 512
[17179572.228000] CPU: After generic identify, caps: 078bfbff c3d3fbff 00000000 00000000 00000001 00000000 00000001
[17179572.228000] CPU: After vendor identify, caps: 078bfbff c3d3fbff 00000000 00000000 00000001 00000000 00000001
[17179572.228000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[17179572.228000] CPU: L2 Cache: 128K (64 bytes/line)
[17179572.228000] CPU: After all inits, caps: 078bfbff c3d3fbff 00000000 00000410 00000001 00000000 00000001
[17179572.228000] Checking 'hlt' instruction... OK.
[17179572.244000] SMP alternatives: switching to UP code
[17179572.244000] Freeing SMP alternatives: 16k freed
[17179572.244000] checking if image is initramfs... it is
[17179572.744000] Freeing initrd memory: 5327k freed
[17179572.744000] ACPI: Core revision 20060707
[17179572.744000] ACPI: Looking for DSDT ... not found!
[17179572.748000] CPU0: AMD Mobile AMD Sempron(tm) Processor 3000+ stepping 02
[17179572.748000] Total of 1 processors activated (3602.72 BogoMIPS).
[17179572.748000] ENABLING IO-APIC IRQs
[17179572.748000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[17179572.892000] Brought up 1 CPUs
[17179572.892000] migration_cost=0
[17179572.892000] NET: Registered protocol family 16
[17179572.892000] EISA bus registered
[17179572.892000] ACPI: bus type pci registered
[17179572.892000] PCI: PCI BIOS revision 2.10 entry at 0xfd776, last bus=1
[17179572.892000] PCI: Using configuration type 1
[17179572.892000] Setting up standard PCI resources
[17179572.892000] ACPI: Interpreter enabled
[17179572.892000] ACPI: Using IOAPIC for interrupt routing
[17179572.892000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179572.892000] PCI: Probing PCI hardware (bus 00)
[17179572.896000] Uncovering SIS963 that hid as a SIS503 (compatible=0)
[17179572.896000] Enabling SiS 96x SMBus.
[17179572.896000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:02.5
[17179572.896000] Boot video device is 0000:01:00.0
[17179572.896000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179572.900000] ACPI: Embedded Controller [EC0] (gpe 25) interrupt mode.
[17179572.916000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 *7 9 10 11)
[17179572.916000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 *4 5 7 9 10 11)
[17179572.916000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 7 9 10 11)
[17179572.916000] ACPI: PCI Interrupt Link [LNKD] (IRQs *3 4 5 7 9 10 11)
[17179572.916000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 *9 10 11)
[17179572.916000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 *11)
[17179572.916000] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 9 10 11) *0, disabled.
[17179572.916000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 9 *10 11)
[17179572.916000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179572.916000] pnp: PnP ACPI init
[17179572.916000] pnp: PnP ACPI: found 8 devices
[17179572.916000] PnPBIOS: Disabled by ACPI PNP
[17179572.916000] PCI: Using ACPI for IRQ routing
[17179572.916000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179572.920000] pnp: 00:04: ioport range 0x8000-0x807f could not be reserved
[17179572.920000] pnp: 00:04: ioport range 0x8080-0x80ff has been reserved
[17179572.920000] pnp: 00:04: ioport range 0x8100-0x811f has been reserved
[17179572.920000] pnp: 00:04: ioport range 0x4d0-0x4d1 has been reserved
[17179572.920000] PCI: Ignore bogus resource 6 [0:0] of 0000:01:00.0
[17179572.920000] PCI: Bridge: 0000:00:01.0
[17179572.920000]   IO window: a000-afff
[17179572.920000]   MEM window: e2100000-e21fffff
[17179572.920000]   PREFETCH window: e8000000-efffffff
[17179572.920000] PCI: Bus 2, cardbus bridge: 0000:00:06.0
[17179572.920000]   IO window: 00002400-000024ff
[17179572.920000]   IO window: 00002800-000028ff
[17179572.920000]   PREFETCH window: 20000000-21ffffff
[17179572.920000]   MEM window: 22000000-23ffffff
[17179572.920000] PCI: Enabling device 0000:00:06.0 (0000 -> 0003)
[17179572.920000] ACPI: PCI Interrupt 0000:00:06.0[A] -> GSI 19 (level, low) -> IRQ 169
[17179572.920000] NET: Registered protocol family 2
[17179572.952000] IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
[17179572.952000] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
[17179572.952000] TCP bind hash table entries: 4096 (order: 3, 32768 bytes)
[17179572.952000] TCP: Hash tables configured (established 8192 bind 4096)
[17179572.952000] TCP reno registered
[17179572.952000] Simple Boot Flag at 0x38 set to 0x1
[17179572.952000] audit: initializing netlink socket (disabled)
[17179572.952000] audit(1180207369.952:1): initialized
[17179572.952000] VFS: Disk quotas dquot_6.5.1
[17179572.952000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179572.952000] Initializing Cryptographic API
[17179572.952000] io scheduler noop registered
[17179572.952000] io scheduler anticipatory registered
[17179572.952000] io scheduler deadline registered
[17179572.952000] io scheduler cfq registered (default)
[17179572.952000] isapnp: Scanning for PnP cards...
[17179573.304000] isapnp: No Plug & Play device found
[17179573.332000] Real Time Clock Driver v1.12ac
[17179573.332000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[17179573.332000] ACPI: PCI Interrupt 0000:00:02.6[C] -> GSI 18 (level, low) -> IRQ 177
[17179573.332000] ACPI: PCI interrupt for device 0000:00:02.6 disabled
[17179573.332000] mice: PS/2 mouse device common for all mice
[17179573.336000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179573.336000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179573.336000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179573.336000] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[17179573.344000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179573.344000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179573.344000] EISA: Probing bus 0 at eisa.0
[17179573.344000] Cannot allocate resource for EISA slot 1
[17179573.344000] Cannot allocate resource for EISA slot 2
[17179573.344000] Cannot allocate resource for EISA slot 8
[17179573.344000] EISA: Detected 0 cards.
[17179573.344000] TCP bic registered
[17179573.344000] NET: Registered protocol family 1
[17179573.344000] NET: Registered protocol family 8
[17179573.344000] NET: Registered protocol family 20
[17179573.344000] Using IPI No-Shortcut mode
[17179573.344000] ACPI: (supports S0 S3 S4 S5)
[17179573.344000] Freeing unused kernel memory: 308k freed
[17179573.384000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179574.480000] Capability LSM initialized
[17179574.520000] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[17179574.524000] ACPI: Thermal Zone [THRM] (57 C)
[17179575.024000] SIS5513: IDE controller at PCI slot 0000:00:02.5
[17179575.024000] ACPI: PCI Interrupt 0000:00:02.5[A] -> GSI 16 (level, low) -> IRQ 185
[17179575.024000] SIS5513: chipset revision 0
[17179575.024000] SIS5513: not 100% native mode: will probe irqs later
[17179575.024000] SIS5513: SiS 962/963 MuTIOL IDE UDMA133 controller
[17179575.024000]     ide0: BM-DMA at 0x2000-0x2007, BIOS settings: hda:DMA, hdb:pio
[17179575.024000]     ide1: BM-DMA at 0x2008-0x200f, BIOS settings: hdc:DMA, hdd:pio
[17179575.024000] Probing IDE interface ide0...
[17179575.312000] hda: WDC WD400UE-22HCT0, ATA DISK drive
[17179575.984000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179576.268000] Probing IDE interface ide1...
[17179577.008000] hdc: Slimtype COMBO SOSC-2483K, ATAPI CD/DVD-ROM drive
[17179577.680000] ide1 at 0x170-0x177,0x376 on irq 15
[17179577.684000] hda: max request size: 128KiB
[17179577.684000] hda: 78140160 sectors (40007 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(100)
[17179577.692000] hda: cache flushes supported
[17179577.692000]  hda: hda1 hda2 < hda5 >
[17179578.024000] hdc: ATAPI 24X DVD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
[17179578.024000] Uniform CD-ROM driver Revision: 3.20
[17179578.372000] usbcore: registered new driver usbfs
[17179578.372000] usbcore: registered new driver hub
[17179578.372000] ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[17179578.372000] ACPI: PCI Interrupt 0000:00:03.0[A] -> GSI 20 (level, low) -> IRQ 193
[17179578.372000] ohci_hcd 0000:00:03.0: OHCI Host Controller
[17179578.376000] ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus number 1
[17179578.572000] ohci_hcd 0000:00:03.0: irq 193, io mem 0xe2002000
[17179578.628000] usb usb1: configuration #1 chosen from 1 choice
[17179578.628000] hub 1-0:1.0: USB hub found
[17179578.628000] hub 1-0:1.0: 3 ports detected
[17179578.732000] ACPI: PCI Interrupt 0000:00:03.1[B] -> GSI 21 (level, low) -> IRQ 201
[17179578.732000] ohci_hcd 0000:00:03.1: OHCI Host Controller
[17179578.732000] ohci_hcd 0000:00:03.1: new USB bus registered, assigned bus number 2
[17179578.936000] ohci_hcd 0000:00:03.1: irq 201, io mem 0xe2003000
[17179578.992000] usb usb2: configuration #1 chosen from 1 choice
[17179578.992000] hub 2-0:1.0: USB hub found
[17179578.992000] hub 2-0:1.0: 3 ports detected
[17179579.096000] ACPI: PCI Interrupt 0000:00:03.2[D] -> GSI 23 (level, low) -> IRQ 209
[17179579.096000] ehci_hcd 0000:00:03.2: EHCI Host Controller
[17179579.096000] ehci_hcd 0000:00:03.2: new USB bus registered, assigned bus number 3
[17179579.096000] PCI: cache line size of 64 is not supported by device 0000:00:03.2
[17179579.096000] ehci_hcd 0000:00:03.2: irq 209, io mem 0xe2004000
[17179579.096000] ehci_hcd 0000:00:03.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179579.096000] usb usb3: configuration #1 chosen from 1 choice
[17179579.096000] hub 3-0:1.0: USB hub found
[17179579.096000] hub 3-0:1.0: 6 ports detected
[17179579.256000] Attempting manual resume
[17179579.552000] kjournald starting.  Commit interval 5 seconds
[17179579.552000] EXT3-fs: mounted filesystem with ordered data mode.
[17179579.688000] usb 1-2: new low speed USB device using ohci_hcd and address 3
[17179579.912000] usb 1-2: configuration #1 chosen from 1 choice
[17179592.092000] ieee80211_crypt: registered algorithm 'NULL'
[17179592.104000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[17179592.104000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[17179592.228000] sis96x_smbus 0000:00:02.1: SiS96x SMBus base address: 0x8100
[17179592.476000] bcm43xx driver
[17179592.476000] ACPI: PCI Interrupt 0000:00:0b.0[A] -> GSI 17 (level, low) -> IRQ 217
[17179592.552000] input: PC Speaker as /class/input/input1
[17179592.924000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179592.944000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179593.004000] Linux agpgart interface v0.101 (c) Dave Jones
[17179593.056000] ACPI: PCI Interrupt 0000:00:06.0[A] -> GSI 19 (level, low) -> IRQ 169
[17179593.056000] Yenta: CardBus bridge found at 0000:00:06.0 [1025:0083]
[17179593.056000] Yenta: Using CSCINT to route CSC interrupts to PCI
[17179593.056000] Yenta: Routing CardBus interrupts to PCI
[17179593.056000] Yenta TI: socket 0000:00:06.0, mfunc 0x00521d22, devctl 0x64
[17179593.152000] usbcore: registered new driver hiddev
[17179593.176000] input: Microsoft Microsoft Wheel Mouse Optical&#65533; as /class/input/input2
[17179593.176000] input: USB HID v1.00 Mouse [Microsoft Microsoft Wheel Mouse Optical&#65533;] on usb-0000:00:03.0-2
[17179593.176000] usbcore: registered new driver usbhid
[17179593.176000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[17179593.208000] sis900.c: v1.08.09 Sep. 19 2005
[17179593.288000] Yenta: ISA IRQ mask 0x06f8, PCI irq 169
[17179593.288000] Socket status: 30000006
[17179593.288000] agpgart: Detected SiS 760 chipset
[17179593.288000] agpgart: AGP aperture is 4M @ 0xe0000000
[17179593.288000] ACPI: PCI Interrupt 0000:00:04.0[A] -> GSI 19 (level, low) -> IRQ 169
[17179593.292000] 0000:00:04.0: Realtek RTL8201 PHY transceiver found at address 13.
[17179593.296000] 0000:00:04.0: Using transceiver found at address 13 as default
[17179593.300000] eth0: SiS 900 PCI Fast Ethernet at 0x1800, IRQ 169, 00:c0:9f:ce:90:4c.
[17179593.348000] ts: Compaq touchscreen protocol output
[17179593.580000] ACPI: PCI Interrupt 0000:00:02.7[C] -> GSI 18 (level, low) -> IRQ 177
[17179593.800000] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x126eb1, caps: 0xa04713/0x4000
[17179593.816000] cs: IO port probe 0x100-0x3af: clean.
[17179593.820000] cs: IO port probe 0x3e0-0x4ff: excluding 0x480-0x48f
[17179593.820000] cs: IO port probe 0x820-0x8ff: clean.
[17179593.820000] cs: IO port probe 0xc00-0xcf7: clean.
[17179593.820000] cs: IO port probe 0xa00-0xaff: clean.
[17179593.836000] input: SynPS/2 Synaptics TouchPad as /class/input/input3
[17179594.400000] intel8x0_measure_ac97_clock: measured 55466 usecs
[17179594.400000] intel8x0: clocking to 48000
[17179594.844000] lp: driver loaded but no devices found
[17179594.864000] NET: Registered protocol family 17
[17179594.896000] Adding 554200k swap on /dev/disk/by-uuid/280c30a5-3821-42c1-9c31-9ed3b2c91333.  Priority:-1 extents:1 across:554200k
[17179594.964000] EXT3 FS on hda1, internal journal
[17179595.552000] eth0: Media Link On 100mbps full-duplex 
[17179596.652000] NET: Registered protocol family 10
[17179596.652000] lo: Disabled Privacy Extensions
[17179596.652000] IPv6 over IPv4 tunneling driver
[17179599.840000] ACPI: AC Adapter [ACAD] (on-line)
[17179599.888000] ACPI: Battery Slot [BAT1] (battery present)
[17179599.904000] ACPI: Power Button (FF) [PWRF]
[17179599.904000] ACPI: Lid Switch [LID]
[17179599.904000] ACPI: Power Button (CM) [PWRB]
[17179599.904000] ACPI: Sleep Button (CM) [SLPB]
[17179600.052000] ibm_acpi: ec object not found
[17179600.080000] pcc_acpi: loading...
[17179600.512000] powernow-k8: Found 1 AMD Athlon 64 / Opteron processors (version 1.60.2)
[17179600.512000] powernow-k8:    0 : fid 0xa (1800 MHz), vid 0xa (1300 mV)
[17179600.512000] powernow-k8:    1 : fid 0x8 (1600 MHz), vid 0xc (1250 mV)
[17179600.512000] powernow-k8:    2 : fid 0x0 (800 MHz), vid 0x13 (1075 mV)
[17179600.512000] cpu_init done, current fid 0xa, vid 0xa
[17179604.304000] apm: BIOS not found.
[17179607.052000] eth0: no IPv6 routers present
[17179608.396000] Bluetooth: Core ver 2.8
[17179608.396000] NET: Registered protocol family 31
[17179608.396000] Bluetooth: HCI device and connection manager initialized
[17179608.396000] Bluetooth: HCI socket layer initialized
[17179608.500000] Bluetooth: L2CAP ver 2.8
[17179608.500000] Bluetooth: L2CAP socket layer initialized
[17179608.544000] Bluetooth: RFCOMM socket layer initialized
[17179608.544000] Bluetooth: RFCOMM TTY layer initialized
[17179608.544000] Bluetooth: RFCOMM ver 1.7
[17182038.504000] atkbd.c: Unknown key pressed (translated set 2, code 0xb4 on isa0060/serio0).
[17182038.504000] atkbd.c: Use 'setkeycodes e034 <keycode>' to make it known.
[17182038.584000] atkbd.c: Unknown key released (translated set 2, code 0xb4 on isa0060/serio0).
[17182038.584000] atkbd.c: Use 'setkeycodes e034 <keycode>' to make it known.
[17183231.172000] atkbd.c: Unknown key pressed (translated set 2, code 0xd5 on isa0060/serio0).
[17183231.172000] atkbd.c: Use 'setkeycodes e055 <keycode>' to make it known.
[17183231.180000] atkbd.c: Unknown key released (translated set 2, code 0xd5 on isa0060/serio0).
[17183231.180000] atkbd.c: Use 'setkeycodes e055 <keycode>' to make it known.
[17183241.396000] atkbd.c: Unknown key pressed (translated set 2, code 0xd6 on isa0060/serio0).
[17183241.396000] atkbd.c: Use 'setkeycodes e056 <keycode>' to make it known.
[17183241.404000] atkbd.c: Unknown key released (translated set 2, code 0xd6 on isa0060/serio0).
[17183241.404000] atkbd.c: Use 'setkeycodes e056 <keycode>' to make it known.
[17183244.916000] atkbd.c: Unknown key pressed (translated set 2, code 0xd8 on isa0060/serio0).
[17183244.916000] atkbd.c: Use 'setkeycodes e058 <keycode>' to make it known.
[17183244.924000] atkbd.c: Unknown key released (translated set 2, code 0xd8 on isa0060/serio0).
[17183244.924000] atkbd.c: Use 'setkeycodes e058 <keycode>' to make it known.
[17184031.552000] eth0: Media Link Off
[17184041.552000] eth0: Media Link On 100mbps full-duplex 
[17184362.552000] eth0: Media Link Off
[17184372.552000] eth0: Media Link On 100mbps full-duplex 
[17185133.552000] eth0: Media Link Off
[17185143.552000] eth0: Media Link On 100mbps full-duplex 
[17187729.552000] eth0: Media Link Off
[17188289.552000] eth0: Media Link On 100mbps full-duplex 
[17190410.552000] eth0: Media Link Off
[17190412.160000] atkbd.c: Unknown key pressed (translated set 2, code 0xd8 on isa0060/serio0).
[17190412.160000] atkbd.c: Use 'setkeycodes e058 <keycode>' to make it known.
[17190412.168000] atkbd.c: Unknown key released (translated set 2, code 0xd8 on isa0060/serio0).
[17190412.168000] atkbd.c: Use 'setkeycodes e058 <keycode>' to make it known.
[17190420.552000] eth0: Media Link On 100mbps full-duplex 
[17191590.196000] cdrom: This disc doesn't have any tracks I recognize!
[17191677.000000] usb 1-2: USB disconnect, address 3
[17191761.196000] cdrom: hdc: mrw address space DMA selected
[17191761.412000] cdrom: hdc: mrw address space DMA selected
[17191761.432000] attempt to access beyond end of device
[17191761.432000] hdc: rw=0, want=68, limit=4
[17191761.436000] isofs_fill_super: bread failed, dev=hdc, iso_blknum=16, block=16
[17191957.484000] scsi: unknown opcode 0x01
[17192183.364000] atkbd.c: Unknown key pressed (translated set 2, code 0xd8 on isa0060/serio0).
[17192183.364000] atkbd.c: Use 'setkeycodes e058 <keycode>' to make it known.
[17192183.376000] atkbd.c: Unknown key released (translated set 2, code 0xd8 on isa0060/serio0).
[17192183.376000] atkbd.c: Use 'setkeycodes e058 <keycode>' to make it known.
[17192186.064000] atkbd.c: Unknown key pressed (translated set 2, code 0xd8 on isa0060/serio0).
[17192186.064000] atkbd.c: Use 'setkeycodes e058 <keycode>' to make it known.
[17192186.076000] atkbd.c: Unknown key released (translated set 2, code 0xd8 on isa0060/serio0).
[17192186.076000] atkbd.c: Use 'setkeycodes e058 <keycode>' to make it known.
[17192199.544000] ohci_hcd 0000:00:03.0: wakeup
[17192199.928000] usb 1-2: new low speed USB device using ohci_hcd and address 4
[17192200.152000] usb 1-2: configuration #1 chosen from 1 choice
[17192200.168000] input: Microsoft Microsoft Wheel Mouse Optical&#65533; as /class/input/input4
[17192200.168000] input: USB HID v1.00 Mouse [Microsoft Microsoft Wheel Mouse Optical&#65533;] on usb-0000:00:03.0-2
[17192958.992000] atkbd.c: Unknown key pressed (translated set 2, code 0xb4 on isa0060/serio0).
[17192958.992000] atkbd.c: Use 'setkeycodes e034 <keycode>' to make it known.
[17192959.064000] atkbd.c: Unknown key released (translated set 2, code 0xb4 on isa0060/serio0).
[17192959.064000] atkbd.c: Use 'setkeycodes e034 <keycode>' to make it known.
[17193723.796000] atkbd.c: Unknown key pressed (translated set 2, code 0xd8 on isa0060/serio0).
[17193723.796000] atkbd.c: Use 'setkeycodes e058 <keycode>' to make it known.
[17193723.808000] atkbd.c: Unknown key released (translated set 2, code 0xd8 on isa0060/serio0).
[17193723.808000] atkbd.c: Use 'setkeycodes e058 <keycode>' to make it known.
[17194437.728000] cdrom: hdc: mrw address space DMA selected
[17194437.764000] cdrom: hdc: mrw address space DMA selected
[17194438.592000] ISO 9660 Extensions: Microsoft Joliet Level 3
[17194439.104000] ISO 9660 Extensions: RRIP_1991A
[17194861.308000] cdrom: hdc: mrw address space DMA selected
[17194861.348000] cdrom: hdc: mrw address space DMA selected
[17194861.404000] ISO 9660 Extensions: Microsoft Joliet Level 3
[17194861.452000] ISO 9660 Extensions: RRIP_1991A
[17197801.552000] eth0: Media Link Off
[17197811.552000] eth0: Media Link On 100mbps full-duplex 
[17200402.552000] eth0: Media Link Off
[17200412.552000] eth0: Media Link On 100mbps full-duplex 
[17205012.564000] usb 1-2: USB disconnect, address 4
[17205035.164000] ohci_hcd 0000:00:03.0: wakeup
[17205035.548000] usb 1-2: new low speed USB device using ohci_hcd and address 5
[17205035.772000] usb 1-2: configuration #1 chosen from 1 choice
[17205035.788000] input: Microsoft Microsoft Wheel Mouse Optical&#65533; as /class/input/input5
[17205035.788000] input: USB HID v1.00 Mouse [Microsoft Microsoft Wheel Mouse Optical&#65533;] on usb-0000:00:03.0-2
[17205568.552000] eth0: Media Link Off
[17205583.552000] eth0: Media Link On 100mbps full-duplex

---

### Post by Major Pen0r on 2007-05-27
*bump*

---

### Post by digitalbenji on 2007-05-27
00:0b.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

This shows that your wireless card is recognized.  I think this also means that the drivers are installed.  Can you please print out the results of sudo iwconfig.

It may be that we will have to configure the windows driver for this card.  This is easy to do, but I'm curious to see what sudo iwconfig prints.

Thanks,

---

### Post by Major Pen0r on 2007-05-28
**_iwconfig_**

lo        no wireless extensions.

sit0      no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4318"
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by scrooge_74 on 2007-05-28
The card is there and seems to be working.

It looks like a matter of config

---

### Post by digitalbenji on 2007-05-29
You may benefit from an easy to use network configuration application.  Feisty comes with Network Manager preinstalled.  Click on the Network Manager Icon in the upper right, and see if that shows available networks.  

You can also do this command in the terminal to determine if you have any networks within range and that the card is working:
sudo iwlist scanning

If you still can't get online, let us know.  Thanks

---

### Post by blackdog423 on 2007-05-29
I am trying to get the wireless working on an Acer Aspire 5050, and I tried Network Tools, but nothing works.  I have almost the same output for everything - except for the:  


lo        no wireless extensions.

eth1      no wireless extensions.

eth0      IEEE 802.11b/g  ESSID:""  Nickname:"Broadcom 4318"
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
         **[B] Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm**[/B]
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

In the first thing I put in the command prompt - everything was the same.  The wireless was disabeled.  How can I enable it?

---

### Post by tahuya_rat on 2007-05-29
Try [this thread]("http://ubuntuforums.org/showthread.php?t=285809"), I have a Gateway MX6450, which also uses the Broadcom 4318 chipset, and this howto worked like a charm.

---

### Post by whirl on 2007-08-15
Mates..

I (or actually my girl friend) have the same card as Major Pen0r and need a little help. Ill post lspci, dmesg and iwconfig here so that maybe someone could help me out with this one.. 

> lspci:

00:00.0 Host bridge: ATI Technologies Inc Unknown device 5a31 (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 83)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI (rev 80)
00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]
0a:00.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
0a:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0a:06.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02

> iwconfig:

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:""  Nickname:"Broadcom 4318"
          Mode:Managed  Access Point: Invalid
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

So any advice how I should proceed with this one?

Cheers!

---

### Post by whirl on 2007-08-15
Oops forgot these.. Silly me.
> dmesg:

[    0.000000] Linux version 2.6.20-16-generic (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Thu Jun 7 20:19:32 UTC 2007 (Ubuntu 2.6.20-16.29-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009dc00 end: 000000000009dc00 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009dc00 size: 0000000000002400 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000e4000 size: 000000000001c000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 0000000037da0000 end: 0000000037ea0000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 0000000037ea0000 size: 000000000000b000 end: 0000000037eab000 type: 3
[    0.000000] copy_e820_map() start: 0000000037eab000 size: 0000000000055000 end: 0000000037f00000 type: 4
[    0.000000] copy_e820_map() start: 0000000037f00000 size: 0000000000100000 end: 0000000038000000 type: 2
[    0.000000] copy_e820_map() start: 00000000fec00000 size: 0000000000010000 end: 00000000fec10000 type: 2
[    0.000000] copy_e820_map() start: 00000000fee00000 size: 0000000000001000 end: 00000000fee01000 type: 2
[    0.000000] copy_e820_map() start: 00000000fff80000 size: 0000000000080000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009dc00 (usable)
[    0.000000]  BIOS-e820: 000000000009dc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000037ea0000 (usable)
[    0.000000]  BIOS-e820: 0000000037ea0000 - 0000000037eab000 (ACPI data)
[    0.000000]  BIOS-e820: 0000000037eab000 - 0000000037f00000 (ACPI NVS)
[    0.000000]  BIOS-e820: 0000000037f00000 - 0000000038000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 894MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f8620
[    0.000000] Entering add_active_range(0, 0, 229024) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229024
[    0.000000]   HighMem    229024 ->   229024
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   229024
[    0.000000] On node 0 totalpages: 229024
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1757 pages used for memmap
[    0.000000]   Normal zone: 223171 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP (v000 PTLTD                                 ) @ 0x000f85f0
[    0.000000] ACPI: RSDT (v001 PTLTD    RSDT   0x06040000  LTP 0x00000000) @ 0x37ea405e
[    0.000000] ACPI: FADT (v001 ATI    Bonefish 0x06040000 ATI  0x000f4240) @ 0x37eaaeb0
[    0.000000] ACPI: MADT (v001 PTLTD    APIC   0x06040000  LTP 0x00000000) @ 0x37eaaf24
[    0.000000] ACPI: MADT (v001 PTLTD    APIC   0x06040000  LTP 0x00000000) @ 0x37eaaf74
[    0.000000] ACPI: MCFG (v001 PTLTD    MCFG   0x06040000  LTP 0x00000000) @ 0x37eaafc4
[    0.000000] ACPI: SSDT (v001  PmRef  Cpu0Cst 0x00003001 INTL 0x20050228) @ 0x37ea45cf
[    0.000000] ACPI: SSDT (v001  PmRef    CpuPm 0x00003000 INTL 0x20050228) @ 0x37ea409a
[    0.000000] ACPI: DSDT (v001    ATI    SB450 0x06040000 MSFT 0x0100000e) @ 0x00000000
[    0.000000] ATI board detected. Disabling timer routing over 8254.
[    0.000000] ACPI: PM-Timer IO Port: 0x8008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: 2 duplicate APIC table ignored.
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:14 APIC version 20
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 21 low level)
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 38000000:c6c00000)
[    0.000000] Detected 1463.194 MHz processor.
[   14.031873] Built 1 zonelists.  Total pages: 227235
[   14.031879] Kernel command line: root=UUID=82c0a147-acd8-492b-99cb-1e73f2841739 ro quiet splash
[   14.032072] mapped APIC to ffffd000 (fee00000)
[   14.032075] mapped IOAPIC to ffffc000 (fec00000)
[   14.032079] Enabling fast FPU save and restore... done.
[   14.032083] Enabling unmasked SIMD FPU exception support... done.
[   14.032097] Initializing CPU#0
[   14.032194] PID hash table entries: 4096 (order: 12, 16384 bytes)
[   14.033298] Console: colour VGA+ 80x25
[   14.034306] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   14.035050] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   14.064036] Memory: 896816k/916096k available (1992k kernel code, 18648k reserved, 900k data, 328k init, 0k highmem)
[   14.064047] virtual kernel memory layout:
[   14.064048]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   14.064050]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   14.064051]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   14.064053]     lowmem  : 0xc0000000 - 0xf7ea0000   ( 894 MB)
[   14.064054]       .init : 0xc03d9000 - 0xc042b000   ( 328 kB)
[   14.064056]       .data : 0xc02f2374 - 0xc03d36d4   ( 900 kB)
[   14.064057]       .text : 0xc0100000 - 0xc02f2374   (1992 kB)
[   14.064061] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   14.144060] Calibrating delay using timer specific routine.. 2929.55 BogoMIPS (lpj=5859103)
[   14.144108] Security Framework v1.0.0 initialized
[   14.144118] SELinux:  Disabled at boot.
[   14.144137] Mount-cache hash table entries: 512
[   14.144289] CPU: After generic identify, caps: afe9fbff 00100000 00000000 00000000 0000c109 00000000 00000000
[   14.144298] monitor/mwait feature present.
[   14.144300] using mwait in idle threads.
[   14.144306] CPU: L1 I cache: 32K, L1 D cache: 32K
[   14.144309] CPU: L2 cache: 1024K
[   14.144312] CPU: After all inits, caps: afe9fbff 00100000 00000000 00002940 0000c109 00000000 00000000
[   14.144324] Compat vDSO mapped to ffffe000.
[   14.144329] Remapping vsyscall page to ffffe000
[   14.144343] Checking 'hlt' instruction... OK.
[   14.160152] SMP alternatives: switching to UP code
[   14.160354] Freeing SMP alternatives: 11k freed
[   14.160562] Early unpacking initramfs... done
[   14.559157] ACPI: Core revision 20060707
[   14.577443] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   15.033952] CPU0: Intel(R) Celeron(R) M CPU        410  @ 1.46GHz stepping 08
[   15.033983] Total of 1 processors activated (2929.55 BogoMIPS).
[   15.034162] ENABLING IO-APIC IRQs
[   15.034377] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
[   15.178790] Brought up 1 CPUs
[   15.179049] Booting paravirtualized kernel on bare hardware
[   15.179145] Time: 21:21:00  Date: 07/15/107
[   15.179175] NET: Registered protocol family 16
[   15.179271] EISA bus registered
[   15.179276] ACPI: bus type pci registered
[   15.183912] PCI: BIOS BUG #81[49435000] found
[   15.183962] PCI: Using configuration type 1
[   15.183964] Setting up standard PCI resources
[   15.193276] ACPI: Interpreter enabled
[   15.193280] ACPI: Using IOAPIC for interrupt routing
[   15.193919] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   15.193924] PCI: Probing PCI hardware (bus 00)
[   15.195439] Boot video device is 0000:01:05.0
[   15.196023] PCI: Transparent bridge - 0000:00:14.4
[   15.196158] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   15.198492] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB4_._PRT]
[   15.198767] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB6_._PRT]
[   15.200234] ACPI: PCI Interrupt Link [LNKA] (IRQs 10 11) *0, disabled.
[   15.200531] ACPI: PCI Interrupt Link [LNKB] (IRQs 10 11) *0, disabled.
[   15.200822] ACPI: PCI Interrupt Link [LNKC] (IRQs 10 11) *0, disabled.
[   15.201114] ACPI: PCI Interrupt Link [LNKD] (IRQs 10 11) *0, disabled.
[   15.201404] ACPI: PCI Interrupt Link [LNKE] (IRQs 10 11) *0, disabled.
[   15.201698] ACPI: PCI Interrupt Link [LNKF] (IRQs 10 11) *0, disabled.
[   15.201986] ACPI: PCI Interrupt Link [LNKG] (IRQs 10 11) *0, disabled.
[   15.202277] ACPI: PCI Interrupt Link [LNKH] (IRQs 10 11) *0, disabled.
[   15.202569] ACPI: PCI Interrupt Link [LNKU] (IRQs 3 4 5 7) *0, disabled.
[   16.213100] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[   16.213493] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[   16.213946] Linux Plug and Play Support v0.97 (c) Adam Belay
[   16.213957] pnp: PnP ACPI init
[   16.217301] pnp: PnP ACPI: found 10 devices
[   16.217307] PnPBIOS: Disabled by ACPI PNP
[   16.217362] PCI: Using ACPI for IRQ routing
[   16.217365] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   16.217373] PCI: Cannot allocate resource region 7 of bridge 0000:00:04.0
[   16.217375] PCI: Cannot allocate resource region 8 of bridge 0000:00:04.0
[   16.217378] PCI: Cannot allocate resource region 7 of bridge 0000:00:06.0
[   16.217381] PCI: Cannot allocate resource region 8 of bridge 0000:00:06.0
[   16.217483] NET: Registered protocol family 8
[   16.217485] NET: Registered protocol family 20
[   16.217713] pnp: 00:06: ioport range 0x1080-0x1080 has been reserved
[   16.217717] pnp: 00:06: ioport range 0x220-0x22f has been reserved
[   16.217720] pnp: 00:06: ioport range 0x40b-0x40b has been reserved
[   16.217723] pnp: 00:06: ioport range 0x4d0-0x4d1 has been reserved
[   16.218031] PCI: Bridge: 0000:00:01.0
[   16.218034]   IO window: 9000-9fff
[   16.218039]   MEM window: c0100000-c01fffff
[   16.218043]   PREFETCH window: d0000000-dfffffff
[   16.218047] PCI: Bridge: 0000:00:04.0
[   16.218049]   IO window: disabled.
[   16.218053]   MEM window: disabled.
[   16.218056]   PREFETCH window: disabled.
[   16.218060] PCI: Bridge: 0000:00:06.0
[   16.218062]   IO window: disabled.
[   16.218065]   MEM window: disabled.
[   16.218068]   PREFETCH window: disabled.
[   16.218083] PCI: Bus 11, cardbus bridge: 0000:0a:00.0
[   16.218086]   IO window: 0000a400-0000a4ff
[   16.218093]   IO window: 0000a800-0000a8ff
[   16.218100]   PREFETCH window: 40000000-43ffffff
[   16.218107]   MEM window: 44000000-47ffffff
[   16.218114] PCI: Bridge: 0000:00:14.4
[   16.218118]   IO window: a000-afff
[   16.218126]   MEM window: c0200000-c02fffff
[   16.218132]   PREFETCH window: 40000000-43ffffff
[   16.218160] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   16.218172] PCI: Setting latency timer of device 0000:00:06.0 to 64
[   16.218205] ACPI: PCI Interrupt 0000:0a:00.0[A] -> GSI 22 (level, low) -> IRQ 16
[   16.218236] NET: Registered protocol family 2
[   16.253377] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   16.253575] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   16.255011] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   16.256016] TCP: Hash tables configured (established 131072 bind 65536)
[   16.256022] TCP reno registered
[   16.265463] checking if image is initramfs... it is
[   17.049425] Freeing initrd memory: 6980k freed
[   17.050085] audit: initializing netlink socket (disabled)
[   17.050104] audit(1187212861.652:1): initialized
[   17.050254] VFS: Disk quotas dquot_6.5.1
[   17.050275] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   17.050338] io scheduler noop registered
[   17.050342] io scheduler anticipatory registered
[   17.050344] io scheduler deadline registered
[   17.050354] io scheduler cfq registered (default)
[   17.050585] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   17.050625] assign_interrupt_mode Found MSI capability
[   17.050628] Allocate Port Service[0000:00:04.0:pcie00]
[   17.050734] PCI: Setting latency timer of device 0000:00:06.0 to 64
[   17.050772] assign_interrupt_mode Found MSI capability
[   17.050775] Allocate Port Service[0000:00:06.0:pcie00]
[   17.050933] isapnp: Scanning for PnP cards...
[   17.407868] isapnp: No Plug & Play device found
[   17.435807] Real Time Clock Driver v1.12ac
[   17.435888] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   17.436678] mice: PS/2 mouse device common for all mice
[   17.437292] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   17.437471] input: Macintosh mouse button emulation as /class/input/input0
[   17.437510] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   17.437515] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   17.437816] PNP: PS/2 Controller [PNP0303:KBD0,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   17.438170] i8042.c: Detected active multiplexing controller, rev 1.1.
[   17.438252] serio: i8042 KBD port at 0x60,0x64 irq 1
[   17.438256] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[   17.438259] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[   17.438262] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[   17.438265] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[   17.438390] EISA: Probing bus 0 at eisa.0
[   17.438402] Cannot allocate resource for EISA slot 1
[   17.438433] Cannot allocate resource for EISA slot 8
[   17.438436] EISA: Detected 0 cards.
[   17.468529] TCP cubic registered
[   17.468539] NET: Registered protocol family 1
[   17.468563] Using IPI No-Shortcut mode
[   17.468662] ACPI: (supports S0 S3 S4 S5)
[   17.468718]   Magic number: 3:191:399
[   17.469343] Freeing unused kernel memory: 328k freed
[   17.471817] Time: tsc clocksource has been installed.
[   17.495716] input: AT Translated Set 2 keyboard as /class/input/input1
[   18.700258] Capability LSM initialized
[   18.738562] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   18.738570] ACPI: Processor [CPU0] (supports 8 throttling states)
[   18.738579] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[    4.180000] Time: acpi_pm clocksource has been installed.
[    4.668000] ACPI: Thermal Zone [TZS0] (76 C)
[    5.168000] ACPI: Thermal Zone [TZS1] (77 C)
[    5.608000] usbcore: registered new interface driver usbfs
[    5.608000] usbcore: registered new interface driver hub
[    5.608000] usbcore: registered new device driver usb
[    5.612000] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[    5.612000] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 19 (level, low) -> IRQ 17
[    5.612000] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    5.612000] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
[    5.612000] ohci_hcd 0000:00:13.0: irq 17, io mem 0xc0005000
[    5.668000] SCSI subsystem initialized
[    5.672000] libata version 2.20 loaded.
[    5.704000] usb usb1: configuration #1 chosen from 1 choice
[    5.704000] hub 1-0:1.0: USB hub found
[    5.704000] hub 1-0:1.0: 4 ports detected
[    5.744000] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    5.808000] ACPI: PCI Interrupt 0000:00:13.1[A] -> GSI 19 (level, low) -> IRQ 17
[    5.808000] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    5.808000] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
[    5.808000] ohci_hcd 0000:00:13.1: irq 17, io mem 0xc0006000
[    5.864000] usb usb2: configuration #1 chosen from 1 choice
[    5.864000] hub 2-0:1.0: USB hub found
[    5.864000] hub 2-0:1.0: 4 ports detected
[    5.968000] ACPI: PCI Interrupt 0000:00:13.2[A] -> GSI 19 (level, low) -> IRQ 17
[    5.968000] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    5.968000] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
[    5.968000] ehci_hcd 0000:00:13.2: irq 17, io mem 0xc0007000
[    5.968000] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    5.968000] usb usb3: configuration #1 chosen from 1 choice
[    5.968000] hub 3-0:1.0: USB hub found
[    5.968000] hub 3-0:1.0: 8 ports detected
[    6.072000] ATIIXP: IDE controller at PCI slot 0000:00:14.1
[    6.072000] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 18
[    6.072000] ATIIXP: chipset revision 128
[    6.072000] ATIIXP: not 100% native mode: will probe irqs later
[    6.072000]     ide0: BM-DMA at 0x8460-0x8467, BIOS settings: hda:DMA, hdb:DMA
[    6.072000] ATIIXP: simplex device: DMA disabled
[    6.072000] ide1: ATIIXP Bus-Master DMA disabled (BIOS)
[    6.072000] Probing IDE interface ide0...
[    6.360000] hda: ST98823A, ATA DISK drive
[    6.720000] usb 3-6: new high speed USB device using ehci_hcd and address 3
[    6.856000] usb 3-6: configuration #1 chosen from 1 choice
[    7.144000] hdb: MATSHITADVD-RAM UJ-850S, ATAPI CD/DVD-ROM drive
[    7.164000] usb 1-2: new low speed USB device using ohci_hcd and address 3
[    7.200000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[    7.276000] Probing IDE interface ide1...
[    7.372000] usb 1-2: configuration #1 chosen from 1 choice
[    7.388000] usbcore: registered new interface driver hiddev
[    7.392000] input: Logitech Logitech USB Optical Mouse as /class/input/input2
[    7.392000] input: USB HID v1.11 Mouse [Logitech Logitech USB Optical Mouse] on usb-0000:00:13.0-2
[    7.392000] usbcore: registered new interface driver usbhid
[    7.392000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[    7.840000] 8139cp 0000:0a:01.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[    7.840000] 8139cp 0000:0a:01.0: Try the "8139too" driver instead.
[    7.844000] 8139too Fast Ethernet driver 0.9.28
[    7.844000] ACPI: PCI Interrupt 0000:0a:01.0[A] -> GSI 20 (level, low) -> IRQ 19
[    7.844000] eth0: RealTek RTL8139 at 0xf885a000, 00:16:d3:45:e3:8b, IRQ 19
[    7.844000] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[    7.852000] hda: max request size: 512KiB
[    7.864000] hda: 156301488 sectors (80026 MB) w/8192KiB Cache, CHS=16383/255/63, UDMA(100)
[    7.864000] hda: cache flushes supported
[    7.864000]  hda: hda1 hda2 < hda5 >
[    7.920000] hdb: ATAPI 24X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(33)
[    7.920000] Uniform CD-ROM driver Revision: 3.20
[    8.144000] Attempting manual resume
[    8.144000] swsusp: Resume From Partition 3:5
[    8.144000] PM: Checking swsusp image.
[    8.144000] PM: Resume from disk failed.
[    8.208000] kjournald starting.  Commit interval 5 seconds
[    8.208000] EXT3-fs: mounted filesystem with ordered data mode.
[   20.720000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   20.724000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   20.732000] piix4_smbus 0000:00:14.0: Found 0000:00:14.0 device
[   21.420000] Linux agpgart interface v0.102 (c) Dave Jones
[   21.832000] input: PC Speaker as /class/input/input3
[   21.872000] ieee80211_crypt: registered algorithm 'NULL'
[   21.880000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   21.880000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   21.928000] Yenta: CardBus bridge found at 0000:0a:00.0 [1025:0080]
[   21.928000] Yenta: Using CSCINT to route CSC interrupts to PCI
[   21.928000] Yenta: Routing CardBus interrupts to PCI
[   21.928000] Yenta TI: socket 0000:0a:00.0, mfunc 0x01aa1b22, devctl 0x44
[   22.060000] bcm43xx driver
[   22.164000] Yenta: ISA IRQ mask 0x0ef8, PCI irq 16
[   22.164000] Socket status: 30000006
[   22.164000] pcmcia: parent PCI bridge I/O window: 0xa000 - 0xafff
[   22.164000] cs: IO port probe 0xa000-0xafff: clean.
[   22.164000] pcmcia: parent PCI bridge Memory window: 0xc0200000 - 0xc02fffff
[   22.164000] pcmcia: parent PCI bridge Memory window: 0x40000000 - 0x43ffffff
[   22.168000] ACPI: PCI Interrupt 0000:0a:06.0[A] -> GSI 23 (level, low) -> IRQ 20
[   22.324000] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x1a0b1, caps: 0xa04713/0x204000
[   22.356000] input: SynPS/2 Synaptics TouchPad as /class/input/input4
[   22.360000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[   22.396000] ACPI: PCI Interrupt 0000:00:14.2[A] -> GSI 16 (level, low) -> IRQ 18
[   22.508000] cs: IO port probe 0x100-0x3af: clean.
[   22.508000] cs: IO port probe 0x3e0-0x4ff: clean.
[   22.508000] cs: IO port probe 0x820-0x8ff: excluding 0x878-0x87f
[   22.512000] cs: IO port probe 0xc00-0xcf7: excluding 0xc00-0xc07 0xc10-0xc17 0xc50-0xc57 0xc68-0xc6f 0xcd0-0xcdf
[   22.512000] cs: IO port probe 0xa00-0xaff: clean.
[   22.580000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[   22.592000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[   23.032000] fuse init (API version 7.8)
[   23.088000] lp: driver loaded but no devices found
[   23.116000] Adding 2642652k swap on /dev/disk/by-uuid/dd1cba2c-77b6-4112-96f2-bc20e2ecc49d.  Priority:-1 extents:1 across:2642652k
[   23.264000] EXT3 FS on hda1, internal journal
[   23.728000] NET: Registered protocol family 17
[   28.004000] ibm_acpi: ec object not found
[   28.048000] Using specific hotkey driver
[   28.120000] input: Power Button (FF) as /class/input/input5
[   28.124000] ACPI: Power Button (FF) [PWRF]
[   28.168000] input: Lid Switch as /class/input/input6
[   28.172000] ACPI: Lid Switch [LID0]
[   28.216000] input: Sleep Button (CM) as /class/input/input7
[   28.220000] ACPI: Sleep Button (CM) [SLPB]
[   28.268000] input: Power Button (CM) as /class/input/input8
[   28.272000] ACPI: Power Button (CM) [PWRB]
[   28.360000] No dock devices found.
[   28.376000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   28.392000] ACPI: AC Adapter [ADP1] (on-line)
[   30.484000] ACPI: Battery Slot [BAT0] (battery present)
[   30.544000] pcc_acpi: loading...
[   38.236000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[   40.040000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   40.048000] [fglrx] Maximum main memory to use for locked dma buffers: 803 MBytes.
[   40.048000] [fglrx] module loaded - fglrx 8.34.8 [Feb 20 2007] on minor 0
[   40.116000] ACPI: PCI Interrupt 0000:01:05.0[A] -> GSI 17 (level, low) -> IRQ 22
[   40.288000] ppdev: user-space parallel port driver
[   41.648000] [fglrx] total      GART = 130023424
[   41.648000] [fglrx] free       GART = 114032640
[   41.648000] [fglrx] max single GART = 114032640
[   41.648000] [fglrx] total      LFB  = 134217728
[   41.648000] [fglrx] free       LFB  = 119828480
[   41.648000] [fglrx] max single LFB  = 119828480
[   41.648000] [fglrx] total      Inv  = 0
[   41.648000] [fglrx] free       Inv  = 0
[   41.648000] [fglrx] max single Inv  = 0
[   41.648000] [fglrx] total      TIM  = 0
[   43.020000] apm: BIOS not found.
[   43.084000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[   43.136000] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[   44.248000] Bluetooth: Core ver 2.11
[   44.248000] NET: Registered protocol family 31
[   44.248000] Bluetooth: HCI device and connection manager initialized
[   44.248000] Bluetooth: HCI socket layer initialized
[   44.372000] Bluetooth: L2CAP ver 2.8
[   44.372000] Bluetooth: L2CAP socket layer initialized
[   44.472000] Bluetooth: RFCOMM socket layer initialized
[   44.472000] Bluetooth: RFCOMM TTY layer initialized
[   44.472000] Bluetooth: RFCOMM ver 1.8
[   47.728000] NET: Registered protocol family 10
[   47.728000] lo: Disabled Privacy Extensions
[   57.204000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[   58.096000] eth0: no IPv6 routers present
[   68.636000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[   93.368000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  118.108000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  142.868000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  167.648000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  262.240000] hda-intel: Invalid position buffer, using LPIB read method instead.
[  270.816000] ip_tables: (C) 2000-2006 Netfilter Core Team
[  271.232000] Netfilter messages via NETLINK v0.30.
[  271.304000] nf_conntrack version 0.5.0 (7157 buckets, 57256 max)
[  292.384000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  417.116000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  449.268000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  541.876000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  666.612000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  760.168000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  791.416000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  916.144000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 1040.872000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 1113.148000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 1153.648000] Inbound IN=eth0 OUT= MAC=00:16:d3:45:e3:8b:00:0f:35:b0:54:00:08:00 SRC=61.128.122.137 DST=87.94.152.192 LEN=404 TOS=0x1C PREC=0x20 TTL=116 ID=64173 PROTO=UDP SPT=1090 DPT=1434 LEN=384
[ 1165.728000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 1290.440000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 1318.172000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 1380.192000] Inbound IN=eth0 OUT= MAC=00:16:d3:45:e3:8b:00:0f:35:b0:54:00:08:00 SRC=128.39.2.28 DST=87.94.152.192 LEN=60 TOS=0x1C PREC=0x20 TTL=54 ID=53180 DF PROTO=TCP SPT=57140 DPT=113 WINDOW=5840 RES=0x00 SYN URGP=0
[ 1383.180000] Inbound IN=eth0 OUT= MAC=00:16:d3:45:e3:8b:00:0f:35:b0:54:00:08:00 SRC=128.39.2.28 DST=87.94.152.192 LEN=60 TOS=0x1C PREC=0x20 TTL=54 ID=53181 DF PROTO=TCP SPT=57140 DPT=113 WINDOW=5840 RES=0x00 SYN URGP=0
[ 1389.468000] Inbound IN=eth0 OUT= MAC=00:16:d3:45:e3:8b:00:0f:35:b0:54:00:08:00 SRC=195.1.77.77 DST=87.94.152.192 LEN=60 TOS=0x1C PREC=0x20 TTL=50 ID=54009 DF PROTO=TCP SPT=36784 DPT=8080 WINDOW=5840 RES=0x00 SYN URGP=0
[ 1389.468000] Inbound IN=eth0 OUT= MAC=00:16:d3:45:e3:8b:00:0f:35:b0:54:00:08:00 SRC=195.1.77.77 DST=87.94.152.192 LEN=60 TOS=0x1C PREC=0x20 TTL=50 ID=17248 DF PROTO=TCP SPT=32854 DPT=80 WINDOW=5840 RES=0x00 SYN URGP=0
[ 1389.468000] Inbound IN=eth0 OUT= MAC=00:16:d3:45:e3:8b:00:0f:35:b0:54:00:08:00 SRC=195.1.77.77 DST=87.94.152.192 LEN=60 TOS=0x1C PREC=0x20 TTL=50 ID=2671 DF PROTO=TCP SPT=35068 DPT=6588 WINDOW=5840 RES=0x00 SYN URGP=0
[ 1389.468000] Inbound IN=eth0 OUT= MAC=00:16:d3:45:e3:8b:00:0f:35:b0:54:00:08:00 SRC=195.1.77.77 DST=87.94.152.192 LEN=60 TOS=0x1C PREC=0x20 TTL=50 ID=20501 DF PROTO=TCP SPT=47787 DPT=8000 WINDOW=5840 RES=0x00 SYN URGP=0
[ 1389.468000] Inbound IN=eth0 OUT= MAC=00:16:d3:45:e3:8b:00:0f:35:b0:54:00:08:00 SRC=195.1.77.77 DST=87.94.152.192 LEN=60 TOS=0x1C PREC=0x20 TTL=50 ID=19238 DF PROTO=TCP SPT=36469 DPT=3128 WINDOW=5840 RES=0x00 SYN URGP=0
[ 1392.428000] Inbound IN=eth0 OUT= MAC=00:16:d3:45:e3:8b:00:0f:35:b0:54:00:08:00 SRC=195.1.77.77 DST=87.94.152.192 LEN=60 TOS=0x1C PREC=0x20 TTL=50 ID=54010 DF PROTO=TCP SPT=36784 DPT=8080 WINDOW=5840 RES=0x00 SYN URGP=0
[ 1392.432000] Inbound IN=eth0 OUT= MAC=00:16:d3:45:e3:8b:00:0f:35:b0:54:00:08:00 SRC=195.1.77.77 DST=87.94.152.192 LEN=60 TOS=0x1C PREC=0x20 TTL=50 ID=17249 DF PROTO=TCP SPT=32854 DPT=80 WINDOW=5840 RES=0x00 SYN URGP=0
[ 1398.476000] Inbound IN=eth0 OUT= MAC=00:16:d3:45:e3:8b:00:0f:35:b0:54:00:08:00 SRC=195.1.77.77 DST=87.94.152.192 LEN=60 TOS=0x1C PREC=0x20 TTL=50 ID=54011 DF PROTO=TCP SPT=36784 DPT=8080 WINDOW=5840 RES=0x00 SYN URGP=0
[ 1398.476000] Inbound IN=eth0 OUT= MAC=00:16:d3:45:e3:8b:00:0f:35:b0:54:00:08:00 SRC=195.1.77.77 DST=87.94.152.192 LEN=60 TOS=0x1C PREC=0x20 TTL=50 ID=17250 DF PROTO=TCP SPT=32854 DPT=80 WINDOW=5840 RES=0x00 SYN URGP=0
[ 1398.480000] Inbound IN=eth0 OUT= MAC=00:16:d3:45:e3:8b:00:0f:35:b0:54:00:08:00 SRC=195.1.77.77 DST=87.94.152.192 LEN=60 TOS=0x1C PREC=0x20 TTL=50 ID=20503 DF PROTO=TCP SPT=47787 DPT=8000 WINDOW=5840 RES=0x00 SYN URGP=0
[ 1398.480000] Inbound IN=eth0 OUT= MAC=00:16:d3:45:e3:8b:00:0f:35:b0:54:00:08:00 SRC=195.1.77.77 DST=87.94.152.192 LEN=60 TOS=0x1C PREC=0x20 TTL=50 ID=2673 DF PROTO=TCP SPT=35068 DPT=6588 WINDOW=5840 RES=0x00 SYN URGP=0
[ 1398.480000] Inbound IN=eth0 OUT= MAC=00:16:d3:45:e3:8b:00:0f:35:b0:54:00:08:00 SRC=195.1.77.77 DST=87.94.152.192 LEN=60 TOS=0x1C PREC=0x20 TTL=50 ID=19240 DF PROTO=TCP SPT=36469 DPT=3128 WINDOW=5840 RES=0x00 SYN URGP=0
[ 1410.444000] Inbound IN=eth0 OUT= MAC=00:16:d3:45:e3:8b:00:0f:35:b0:54:00:08:00 SRC=195.1.77.77 DST=87.94.152.192 LEN=60 TOS=0x1C PREC=0x20 TTL=50 ID=54012 DF PROTO=TCP SPT=36784 DPT=8080 WINDOW=5840 RES=0x00 SYN URGP=0
[ 1410.444000] Inbound IN=eth0 OUT= MAC=00:16:d3:45:e3:8b:00:0f:35:b0:54:00:08:00 SRC=195.1.77.77 DST=87.94.152.192 LEN=60 TOS=0x1C PREC=0x20 TTL=50 ID=17251 DF PROTO=TCP SPT=32854 DPT=80 WINDOW=5840 RES=0x00 SYN URGP=0
[ 1410.448000] Inbound IN=eth0 OUT= MAC=00:16:d3:45:e3:8b:00:0f:35:b0:54:00:08:00 SRC=195.1.77.77 DST=87.94.152.192 LEN=60 TOS=0x1C PREC=0x20 TTL=50 ID=2674 DF PROTO=TCP SPT=35068 DPT=6588 WINDOW=5840 RES=0x00 SYN URGP=0
[ 1410.448000] Inbound IN=eth0 OUT= MAC=00:16:d3:45:e3:8b:00:0f:35:b0:54:00:08:00 SRC=195.1.77.77 DST=87.94.152.192 LEN=60 TOS=0x1C PREC=0x20 TTL=50 ID=19241 DF PROTO=TCP SPT=36469 DPT=3128 WINDOW=5840 RES=0x00 SYN URGP=0
[ 1410.448000] Inbound IN=eth0 OUT= MAC=00:16:d3:45:e3:8b:00:0f:35:b0:54:00:08:00 SRC=195.1.77.77 DST=87.94.152.192 LEN=60 TOS=0x1C PREC=0x20 TTL=50 ID=20504 DF PROTO=TCP SPT=47787 DPT=8000 WINDOW=5840 RES=0x00 SYN URGP=0
[ 1415.120000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 1434.436000] Inbound IN=eth0 OUT= MAC=00:16:d3:45:e3:8b:00:0f:35:b0:54:00:08:00 SRC=195.1.77.77 DST=87.94.152.192 LEN=60 TOS=0x1C PREC=0x20 TTL=50 ID=54013 DF PROTO=TCP SPT=36784 DPT=8080 WINDOW=5840 RES=0x00 SYN URGP=0
[ 1434.436000] Inbound IN=eth0 OUT= MAC=00:16:d3:45:e3:8b:00:0f:35:b0:54:00:08:00 SRC=195.1.77.77 DST=87.94.152.192 LEN=60 TOS=0x1C PREC=0x20 TTL=50 ID=17252 DF PROTO=TCP SPT=32854 DPT=80 WINDOW=5840 RES=0x00 SYN URGP=0
[ 1434.440000] Inbound IN=eth0 OUT= MAC=00:16:d3:45:e3:8b:00:0f:35:b0:54:00:08:00 SRC=195.1.77.77 DST=87.94.152.192 LEN=60 TOS=0x1C PREC=0x20 TTL=50 ID=2675 DF PROTO=TCP SPT=35068 DPT=6588 WINDOW=5840 RES=0x00 SYN URGP=0
[ 1434.440000] Inbound IN=eth0 OUT= MAC=00:16:d3:45:e3:8b:00:0f:35:b0:54:00:08:00 SRC=195.1.77.77 DST=87.94.152.192 LEN=60 TOS=0x1C PREC=0x20 TTL=50 ID=20505 DF PROTO=TCP SPT=47787 DPT=8000 WINDOW=5840 RES=0x00 SYN URGP=0
[ 1434.440000] Inbound IN=eth0 OUT= MAC=00:16:d3:45:e3:8b:00:0f:35:b0:54:00:08:00 SRC=195.1.77.77 DST=87.94.152.192 LEN=60 TOS=0x1C PREC=0x20 TTL=50 ID=19242 DF PROTO=TCP SPT=36469 DPT=3128 WINDOW=5840 RES=0x00 SYN URGP=0
[ 1539.856000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 1593.196000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 1664.656000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 1789.400000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 1914.176000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 1920.072000] Inbound IN=eth0 OUT= MAC=00:16:d3:45:e3:8b:00:0f:35:b0:54:00:08:00 SRC=87.139.29.115 DST=87.94.152.192 LEN=48 TOS=0x1C PREC=0x20 TTL=113 ID=44265 DF PROTO=TCP SPT=9818 DPT=139 WINDOW=64240 RES=0x00 SYN URGP=0
[ 1923.276000] Inbound IN=eth0 OUT= MAC=00:16:d3:45:e3:8b:00:0f:35:b0:54:00:08:00 SRC=87.139.29.115 DST=87.94.152.192 LEN=48 TOS=0x1C PREC=0x20 TTL=113 ID=44566 DF PROTO=TCP SPT=9818 DPT=139 WINDOW=64240 RES=0x00 SYN URGP=0
[ 1937.176000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 2038.976000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 2123.812000] Inbound IN=eth0 OUT= MAC=00:16:d3:45:e3:8b:00:0f:35:b0:54:00:08:00 SRC=87.164.206.131 DST=87.94.152.192 LEN=48 TOS=0x1C PREC=0x20 TTL=114 ID=36612 DF PROTO=TCP SPT=3360 DPT=139 WINDOW=64800 RES=0x00 SYN URGP=0
[ 2126.680000] Inbound IN=eth0 OUT= MAC=00:16:d3:45:e3:8b:00:0f:35:b0:54:00:08:00 SRC=87.164.206.131 DST=87.94.152.192 LEN=48 TOS=0x1C PREC=0x20 TTL=114 ID=37088 DF PROTO=TCP SPT=3360 DPT=139 WINDOW=64800 RES=0x00 SYN URGP=0
[ 2132.704000] Inbound IN=eth0 OUT= MAC=00:16:d3:45:e3:8b:00:0f:35:b0:54:00:08:00 SRC=87.164.206.131 DST=87.94.152.192 LEN=48 TOS=0x1C PREC=0x20 TTL=114 ID=38068 DF PROTO=TCP SPT=3360 DPT=139 WINDOW=64800 RES=0x00 SYN URGP=0
[ 2141.164000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 2163.740000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 2288.528000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 2413.272000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 2447.088000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 2538.056000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 2658.528000] Inbound IN=eth0 OUT= MAC=00:16:d3:45:e3:8b:00:0f:35:b0:54:00:08:00 SRC=87.171.87.42 DST=87.94.152.192 LEN=48 TOS=0x1C PREC=0x20 TTL=114 ID=13727 DF PROTO=TCP SPT=2628 DPT=2967 WINDOW=16384 RES=0x00 SYN URGP=0
[ 2661.520000] Inbound IN=eth0 OUT= MAC=00:16:d3:45:e3:8b:00:0f:35:b0:54:00:08:00 SRC=87.171.87.42 DST=87.94.152.192 LEN=48 TOS=0x1C PREC=0x20 TTL=114 ID=14181 DF PROTO=TCP SPT=2628 DPT=2967 WINDOW=16384 RES=0x00 SYN URGP=0
[ 2662.828000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 2667.440000] Inbound IN=eth0 OUT= MAC=00:16:d3:45:e3:8b:00:0f:35:b0:54:00:08:00 SRC=87.171.87.42 DST=87.94.152.192 LEN=48 TOS=0x1C PREC=0x20 TTL=114 ID=14953 DF PROTO=TCP SPT=2628 DPT=2967 WINDOW=16384 RES=0x00 SYN URGP=0
[ 2787.524000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 2890.072000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 2912.212000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 3036.940000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 3161.612000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 3186.024000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 3286.360000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 3411.068000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 3417.032000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 3535.712000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 3582.428000] Inbound IN=eth0 OUT= MAC=00:16:d3:45:e3:8b:00:0f:35:b0:54:00:08:00 SRC=87.171.87.42 DST=87.94.152.192 LEN=48 TOS=0x1C PREC=0x20 TTL=114 ID=62529 DF PROTO=TCP SPT=4852 DPT=2967 WINDOW=16384 RES=0x00 SYN URGP=0
[ 3585.352000] Inbound IN=eth0 OUT= MAC=00:16:d3:45:e3:8b:00:0f:35:b0:54:00:08:00 SRC=87.171.87.42 DST=87.94.152.192 LEN=48 TOS=0x1C PREC=0x20 TTL=114 ID=62968 DF PROTO=TCP SPT=4852 DPT=2967 WINDOW=16384 RES=0x00 SYN URGP=0
[ 3591.376000] Inbound IN=eth0 OUT= MAC=00:16:d3:45:e3:8b:00:0f:35:b0:54:00:08:00 SRC=87.171.87.42 DST=87.94.152.192 LEN=48 TOS=0x1C PREC=0x20 TTL=114 ID=63759 DF PROTO=TCP SPT=4852 DPT=2967 WINDOW=16384 RES=0x00 SYN URGP=0
[ 3660.408000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 3785.212000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 3866.984000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 3900.864000] Inbound IN=eth0 OUT= MAC=00:16:d3:45:e3:8b:00:0f:35:b0:54:00:08:00 SRC=59.32.232.161 DST=87.94.152.192 LEN=48 TOS=0x1C PREC=0x20 TTL=115 ID=44282 PROTO=TCP SPT=9333 DPT=22 WINDOW=65535 RES=0x00 SYN URGP=0
[ 3909.912000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 4034.224000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 4158.636000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 4255.844000] Inbound IN=eth0 OUT= MAC=00:16:d3:45:e3:8b:00:0f:35:b0:54:00:08:00 SRC=201.19.9.195 DST=87.94.152.192 LEN=48 TOS=0x1C PREC=0x20 TTL=111 ID=6096 DF PROTO=TCP SPT=3833 DPT=139 WINDOW=64800 RES=0x00 SYN URGP=0
[ 4261.700000] Inbound IN=eth0 OUT= MAC=00:16:d3:45:e3:8b:00:0f:35:b0:54:00:08:00 SRC=201.19.9.195 DST=87.94.152.192 LEN=48 TOS=0x1C PREC=0x20 TTL=111 ID=7477 DF PROTO=TCP SPT=4255 DPT=445 WINDOW=64800 RES=0x00 SYN URGP=0
[ 4281.976000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 4283.676000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 4408.308000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 4532.844000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 4657.404000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 4698.944000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 4782.172000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 4906.504000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 4938.056000] Inbound IN=eth0 OUT= MAC=00:16:d3:45:e3:8b:00:0f:35:b0:54:00:08:00 SRC=121.97.147.102 DST=87.94.152.192 LEN=394 TOS=0x1C PREC=0x20 TTL=52 ID=64843 PROTO=UDP SPT=30841 DPT=1026 LEN=374
[ 4992.696000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 5031.032000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 5155.392000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 5266.912000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 5279.680000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 5404.196000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 5528.684000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 5653.076000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 5677.888000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 5777.536000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 5892.948000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 5901.960000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 6026.500000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 6121.868000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 6151.792000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 6276.144000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 6389.064000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 6400.536000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 6488.192000] Inbound IN=eth0 OUT= MAC=00:16:d3:45:e3:8b:00:0f:35:b0:54:00:08:00 SRC=193.71.160.171 DST=87.94.152.192 LEN=48 TOS=0x1C PREC=0x20 TTL=116 ID=8290 DF PROTO=TCP SPT=4998 DPT=139 WINDOW=64240 RES=0x00 SYN URGP=0
[ 6491.180000] Inbound IN=eth0 OUT= MAC=00:16:d3:45:e3:8b:00:0f:35:b0:54:00:08:00 SRC=193.71.160.171 DST=87.94.152.192 LEN=48 TOS=0x1C PREC=0x20 TTL=116 ID=8713 DF PROTO=TCP SPT=4998 DPT=139 WINDOW=64240 RES=0x00 SYN URGP=0
[ 6494.196000] Inbound IN=eth0 OUT= MAC=00:16:d3:45:e3:8b:00:0f:35:b0:54:00:08:00 SRC=193.71.160.171 DST=87.94.152.192 LEN=48 TOS=0x1C PREC=0x20 TTL=116 ID=9125 DF PROTO=TCP SPT=1087 DPT=445 WINDOW=64240 RES=0x00 SYN URGP=0
[ 6497.188000] Inbound IN=eth0 OUT= MAC=00:16:d3:45:e3:8b:00:0f:35:b0:54:00:08:00 SRC=193.71.160.171 DST=87.94.152.192 LEN=48 TOS=0x1C PREC=0x20 TTL=116 ID=9522 DF PROTO=TCP SPT=1087 DPT=445 WINDOW=64240 RES=0x00 SYN URGP=0
[ 6516.416000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[ 6516.416000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[ 6516.520000] atkbd.c: Unknown key released (translated set 2, code 0xd9 on isa0060/serio0).
[ 6516.520000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[ 6516.632000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[ 6516.632000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[ 6516.700000] atkbd.c: Unknown key released (translated set 2, code 0xd9 on isa0060/serio0).
[ 6516.700000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[ 6516.788000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[ 6516.788000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[ 6516.864000] atkbd.c: Unknown key released (translated set 2, code 0xd9 on isa0060/serio0).
[ 6516.864000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[ 6516.952000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[ 6516.952000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[ 6517.016000] atkbd.c: Unknown key released (translated set 2, code 0xd9 on isa0060/serio0).
[ 6517.016000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[ 6517.108000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[ 6517.108000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[ 6517.168000] atkbd.c: Unknown key released (translated set 2, code 0xd9 on isa0060/serio0).
[ 6517.168000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[ 6517.248000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[ 6517.248000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[ 6517.336000] atkbd.c: Unknown key released (translated set 2, code 0xd9 on isa0060/serio0).
[ 6517.336000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[ 6517.384000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[ 6517.384000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[ 6517.484000] atkbd.c: Unknown key released (translated set 2, code 0xd9 on isa0060/serio0).
[ 6517.484000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[ 6517.596000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[ 6517.596000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[ 6517.664000] atkbd.c: Unknown key released (translated set 2, code 0xd9 on isa0060/serio0).
[ 6517.664000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[ 6517.724000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[ 6517.724000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[ 6517.980000] atkbd.c: Unknown key released (translated set 2, code 0xd9 on isa0060/serio0).
[ 6517.980000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[ 6518.064000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[ 6518.064000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[ 6518.144000] atkbd.c: Unknown key released (translated set 2, code 0xd9 on isa0060/serio0).
[ 6518.144000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[ 6518.216000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[ 6518.216000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[ 6518.304000] atkbd.c: Unknown key released (translated set 2, code 0xd9 on isa0060/serio0).
[ 6518.304000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[ 6518.360000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[ 6518.360000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[ 6518.460000] atkbd.c: Unknown key released (translated set 2, code 0xd9 on isa0060/serio0).
[ 6518.460000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[ 6518.540000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[ 6518.540000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[ 6518.604000] atkbd.c: Unknown key released (translated set 2, code 0xd9 on isa0060/serio0).
[ 6518.604000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[ 6518.692000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[ 6518.692000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[ 6518.772000] atkbd.c: Unknown key released (translated set 2, code 0xd9 on isa0060/serio0).
[ 6518.772000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[ 6518.844000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[ 6518.844000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[ 6518.936000] atkbd.c: Unknown key released (translated set 2, code 0xd9 on isa0060/serio0).
[ 6518.936000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[ 6518.980000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[ 6518.980000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[ 6519.084000] atkbd.c: Unknown key released (translated set 2, code 0xd9 on isa0060/serio0).
[ 6519.084000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[ 6519.172000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[ 6519.172000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[ 6519.252000] atkbd.c: Unknown key released (translated set 2, code 0xd9 on isa0060/serio0).
[ 6519.252000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[ 6519.372000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[ 6519.372000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[ 6519.408000] atkbd.c: Unknown key released (translated set 2, code 0xd9 on isa0060/serio0).
[ 6519.408000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[ 6519.516000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[ 6519.516000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[ 6519.584000] atkbd.c: Unknown key released (translated set 2, code 0xd9 on isa0060/serio0).
[ 6519.584000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[ 6519.680000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[ 6519.680000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[ 6519.748000] atkbd.c: Unknown key released (translated set 2, code 0xd9 on isa0060/serio0).
[ 6519.748000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[ 6519.844000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[ 6519.844000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[ 6519.912000] atkbd.c: Unknown key released (translated set 2, code 0xd9 on isa0060/serio0).
[ 6519.912000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[ 6524.984000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 6538.284000] atkbd.c: Unknown key pressed (translated set 2, code 0xa6 on isa0060/serio0).
[ 6538.284000] atkbd.c: Use 'setkeycodes e026 <keycode>' to make it known.
[ 6538.472000] atkbd.c: Unknown key released (translated set 2, code 0xa6 on isa0060/serio0).
[ 6538.472000] atkbd.c: Use 'setkeycodes e026 <keycode>' to make it known.
[ 6540.912000] atkbd.c: Unknown key pressed (translated set 2, code 0xa7 on isa0060/serio0).
[ 6540.912000] atkbd.c: Use 'setkeycodes e027 <keycode>' to make it known.
[ 6541.300000] atkbd.c: Unknown key released (translated set 2, code 0xa7 on isa0060/serio0).
[ 6541.300000] atkbd.c: Use 'setkeycodes e027 <keycode>' to make it known.
[ 6649.388000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 6654.864000] Inbound IN=eth0 OUT= MAC=00:16:d3:45:e3:8b:00:0f:35:b0:54:00:08:00 SRC=70.233.163.66 DST=87.94.152.192 LEN=60 TOS=0x1C PREC=0x20 TTL=54 ID=34514 DF PROTO=TCP SPT=48061 DPT=80 WINDOW=5808 RES=0x00 SYN URGP=0
[ 6670.516000] Inbound IN=eth0 OUT= MAC=00:16:d3:45:e3:8b:00:0f:35:b0:54:00:08:00 SRC=216.95.62.139 DST=87.94.152.192 LEN=48 TOS=0x1C PREC=0x20 TTL=106 ID=42139 DF PROTO=TCP SPT=2044 DPT=139 WINDOW=8760 RES=0x00 SYN URGP=0
[ 6676.964000] Inbound IN=eth0 OUT= MAC=00:16:d3:45:e3:8b:00:0f:35:b0:54:00:08:00 SRC=216.95.62.139 DST=87.94.152.192 LEN=48 TOS=0x1C PREC=0x20 TTL=106 ID=43162 DF PROTO=TCP SPT=2072 DPT=445 WINDOW=8760 RES=0x00 SYN URGP=0
[ 6721.836000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 6773.732000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 6898.228000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 6990.324000] atkbd.c: Unknown key pressed (translated set 2, code 0xd5 on isa0060/serio0).
[ 6990.324000] atkbd.c: Use 'setkeycodes e055 <keycode>' to make it known.
[ 6990.948000] atkbd.c: Unknown key released (translated set 2, code 0xd5 on isa0060/serio0).
[ 6990.948000] atkbd.c: Use 'setkeycodes e055 <keycode>' to make it known.
[ 6991.652000] atkbd.c: Unknown key pressed (translated set 2, code 0xd5 on isa0060/serio0).
[ 6991.652000] atkbd.c: Use 'setkeycodes e055 <keycode>' to make it known.
[ 6992.176000] atkbd.c: Unknown key released (translated set 2, code 0xd5 on isa0060/serio0).
[ 6992.176000] atkbd.c: Use 'setkeycodes e055 <keycode>' to make it known.
[ 6993.056000] atkbd.c: Unknown key pressed (translated set 2, code 0xd8 on isa0060/serio0).
[ 6993.056000] atkbd.c: Use 'setkeycodes e058 <keycode>' to make it known.
[ 6993.504000] atkbd.c: Unknown key released (translated set 2, code 0xd8 on isa0060/serio0).
[ 6993.504000] atkbd.c: Use 'setkeycodes e058 <keycode>' to make it known.
[ 7022.636000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 7102.808000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 7147.016000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 7271.448000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 7395.956000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 7495.788000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 7520.348000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 7644.924000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 7769.472000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 7784.772000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 7893.700000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 8018.188000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 8067.756000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 8142.520000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 8266.692000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 8350.020000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 8391.008000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.


---

### Post by noob12 on 2007-08-15
You need to fix these.

> 
[ 22.580000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 22.592000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.


This thread will tell you how.

[http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990)

---

### Post by cai23 on 2007-10-04
im trying to install wireless to Acer Aspire 4310 laptop.
I believe it has Acer InviLink 802.11b/g wireless card. 
Im using Xubuntu edgy. with kernel 2.6.17-12-generic.
bcm43xx-fwcutter and bcm4400-source is installed as well as ndiswrapper-uitls-1.8. 
It seems that the wireless hardware is not detected using lspci, lshw and dmesg. 
When I tried to use wireless assistant it says " no usable wireless devices found"...
How can I fix this. 
Thanks!

---

### Post by cai23 on 2007-10-04
**_my lspci:_**
-------------------------------

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 Ethernet controller: Broadcom Corporation Unknown device 1693 (rev 02)
02:00.0 Ethernet controller: Atheros Communications, Inc. Unknown device 001c (rev 01)
04:06.0 FireWire (IEEE 1394): O2 Micro, Inc. Unknown device 00f7 (rev 02)
04:06.2 Class 0805: O2 Micro, Inc. Unknown device 7120 (rev 02)
04:06.3 Mass storage controller: O2 Micro, Inc. Unknown device 7130 (rev 01)

---

### Post by cai23 on 2007-10-04
**_ my lshw _**

description: Notebook
    product: Aspire 4310
    vendor: Acer
    version: 0100
    serial: LXAHU0C028736063C12000
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4
    configuration: boot=oem-specific chassis=notebook uuid=FD1A3580-5C9D-11DC-912D-CCDDE3C90DB6
  *-core
       description: Motherboard
       product: Volvi
       vendor: Acer
       physical id: 0
       version: Rev
       serial: LXAHU0C028736063C12000
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies LTD
          physical id: 0
          version: V1.08 (08/24/2007)
          size: 100KB
          capacity: 960KB
          capabilities: isa pci pcmcia pnp apm upgrade shadowing escd cdboot acpi usb agp biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Celeron(R) M CPU        530  @ 1.73GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.6.1
          serial: 0001-0661-0000-0000-0000-0000
          slot: U2E1
          size: 1730MHz
          capacity: 1730MHz
          width: 64 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss tm pbe nx x86-64 constant_tsc up pni monitor ds_cpl tm2 cx16 xtpr lahf_lm
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1 Cache
             size: 16KB
             capacity: 16KB
             capabilities: asynchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2 Cache
             size: 1MB
             capabilities: burst external write-back
     *-memory
          description: System Memory
          physical id: e
          slot: System board or motherboard
          size: 512MB
        *-bank:0
             description: SODIMM Synchronous
             physical id: 0
             slot: M1
             size: 512MB
             width: 32 bits
        *-bank:1
             description: SODIMM Synchronous [empty]
             physical id: 1
             slot: M2
     *-pci
          description: Host bridge
          product: Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
        *-display:0
             description: VGA compatible controller
             product: Mobile 945GM/GMS/940GML Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@00:02.0
             version: 03
             size: 256MB
             width: 32 bits
             clock: 33MHz
             capabilities: vga bus_master cap_list
             resources: iomemory:dc100000-dc17ffff ioport:1800-1807 iomemory:c0000000-cfffffff iomemory:dc200000-dc23ffff irq:177
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile 945GM/GMS/940GML Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@00:02.1
             version: 03
             size: 512KB
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             resources: iomemory:dc180000-dc1fffff
        *-multimedia
             description: Audio device
             product: 82801G (ICH7 Family) High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel
             resources: iomemory:dc240000-dc243fff irq:58
        *-pci:0
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Ethernet interface
                product: Broadcom Corporation
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@01:00.0
                logical name: eth0
                version: 02
                serial: 00:16:d3:e5:b8:e4
                size: 100MB/s
                capacity: 1GB/s
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegociation
                configuration: autonegociation=on broadcast=yes driver=tg3 driverversion=3.59.1 duplex=full firmware=5787m-v3.23 ip=192.168.10.202 link=yes multicast=yes port=twisted pair speed=100MB/s
                resources: iomemory:d6000000-d600ffff irq:66
        *-pci:1
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@00:1c.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-network UNCLAIMED
                description: Ethernet controller
                product: Atheros Communications, Inc.
                vendor: Atheros Communications, Inc.
                physical id: 0
                bus info: pci@02:00.0
                version: 01
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                resources: iomemory:d8000000-d800ffff irq:10
        *-pci:2
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@00:1c.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-usb:0
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd
             resources: ioport:1820-183f irq:233
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.17-12-generic uhci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:1
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd
             resources: ioport:1840-185f irq:169
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.17-12-generic uhci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:2
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd
             resources: ioport:1860-187f irq:185
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.17-12-generic uhci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:3
             description: USB Controller
             product: 82801G (ICH7 Family) USB UHCI #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@00:1d.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd
             resources: ioport:1880-189f irq:225
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.17-12-generic uhci_hcd
                physical id: 1
                bus info: usb@4
                logical name: usb4
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-usb:4
             description: USB Controller
             product: 82801G (ICH7 Family) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd
             resources: iomemory:dc444000-dc4443ff irq:233
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 2.6.17-12-generic ehci_hcd
                physical id: 1
                bus info: usb@5
                logical name: usb5
                version: 2.06
                capabilities: usb-2.00
                configuration: driver=hub maxpower=0mA slots=8 speed=480.0MB/s
              *-usb UNCLAIMED
                   description: Video
                   product: Acer CrystalEye webcam
                   vendor: SuYin
                   physical id: 7
                   bus info: usb@5:7
                   version: 1.00
                   serial: CN0314-OV03-VA-R02.00.00
                   capabilities: usb-2.00
                   configuration: maxpower=500mA speed=480.0MB/s
        *-pci:3
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@00:1e.0
             version: e2
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
           *-firewire
                description: FireWire (IEEE 1394)
                product: O2 Micro, Inc.
                vendor: O2 Micro, Inc.
                physical id: 6
                bus info: pci@04:06.0
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: ohci bus_master cap_list
                configuration: driver=ohci1394
                resources: iomemory:dc000000-dc000fff iomemory:dc002000-dc0027ff irq:50
           *-system
                description: Generic system peripheral
                product: O2 Micro, Inc.
                vendor: O2 Micro, Inc.
                physical id: 6.2
                bus info: pci@04:06.2
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=sdhci
                resources: iomemory:dc002800-dc0028ff irq:50
           *-storage UNCLAIMED
                description: Mass storage controller
                product: O2 Micro, Inc.
                vendor: O2 Micro, Inc.
                physical id: 6.3
                bus info: pci@04:06.3
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: storage cap_list
                resources: iomemory:dc001000-dc001fff irq:10
        *-isa UNCLAIMED
             description: ISA bridge
             product: 82801GBM (ICH7-M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
        *-ide:0
             description: IDE interface
             product: 82801G (ICH7 Family) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@00:1f.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=PIIX_IDE
             resources: ioport:1810-181f irq:225
           *-ide
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 33MHz
              *-cdrom
                   description: DVD-RAM writer
                   product: Optiarc DVD RW AD-7560A
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   version: DX06
                   serial: 30648490 1619211Q111
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio cd-r cd-rw dvd dvd-r dvd-ram
                   configuration: mode=udma2
                 *-disc
                      physical id: 0
                      logical name: /dev/hda
        *-ide:1
             description: IDE interface
             product: 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@00:1f.2
             logical name: scsi0
             logical name: scsi1
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list emulated scsi-host
             configuration: driver=ata_piix
             resources: ioport:18d0-18d7 ioport:18c4-18c7 ioport:18c8-18cf ioport:18c0-18c3 ioport:18b0-18bf iomemory:dc444400-dc4447ff irq:225
           *-disk
                description: SCSI Disk
                product: TOSHIBA MK8037GS
                vendor: ATA
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: DL25
                serial: 77LMF65LS
                size: 74GB
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5
              *-volume:0
                   description: Linux filesystem partition
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   capacity: 73GB
                   capabilities: primary bootable
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   capacity: 1443MB
                   capabilities: extended partitioned partitioned:extended
        *-serial UNCLAIMED
             description: SMBus
             product: 82801G (ICH7 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             resources: ioport:18e0-18ff irq:10

---

