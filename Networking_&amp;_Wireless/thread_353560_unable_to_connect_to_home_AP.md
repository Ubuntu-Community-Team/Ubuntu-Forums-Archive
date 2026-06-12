---
title: "unable to connect to home AP"
date: 2007-02-04
forum: Networking &amp; Wireless
---

### Post by skorpio11 on 2007-02-04
Hi I was wondering if anyone have experienced the same problem I a having.  My install is Edgy Ndiswrapper Bcm wireless laptop.  Ndiswrapper drivers seems to be install fine since gnome-network manager scans and fines my access points.  However, I cannot not get a lease from the dhcp server: 

One thing strikes me as odd.  Output from dmesg shows that wlan0 is being changed to eth1:

00:00.0 Host bridge: nVidia Corporation nForce3 Host Bridge (rev a4)
00:01.0 ISA bridge: nVidia Corporation nForce3 LPC Bridge (rev a6)
00:01.1 SMBus: nVidia Corporation nForce3 SMBus (rev a4)
00:02.0 USB Controller: nVidia Corporation nForce3 USB 1.1 (rev a5)
00:02.1 USB Controller: nVidia Corporation nForce3 USB 1.1 (rev a5)
00:02.2 USB Controller: nVidia Corporation nForce3 USB 2.0 (rev a2)
00:06.0 Multimedia audio controller: nVidia Corporation nForce3 Audio (rev a2)
00:06.1 Modem: nVidia Corporation nForce3 Audio (rev a2)
00:08.0 IDE interface: nVidia Corporation nForce3 IDE (rev a5)
00:0a.0 PCI bridge: nVidia Corporation nForce3 PCI Bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation nForce3 AGP Bridge (rev a4)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 420 Go 32M] (rev a3)
02:00.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
02:04.0 CardBus bridge: Texas Instruments PCI1620 PC Card Controller (rev 01)
02:04.1 CardBus bridge: Texas Instruments PCI1620 PC Card Controller (rev 01)
02:04.2 System peripheral: Texas Instruments PCI1620 Firmware Loading Function (rev 01)
leon@ubuntulaptop:~$ dmesg
[17179569.184000] Linux version 2.6.17-10-386 (root@terranova) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 Tue Dec 5 22:26:18 UTC 2006 (Ubuntu 2.6.17-10.34-386)
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[17179569.184000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000d0000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000003ff70000 (usable)
[17179569.184000]  BIOS-e820: 000000003ff70000 - 000000003ff7f000 (ACPI data)
[17179569.184000]  BIOS-e820: 000000003ff7f000 - 000000003ff80000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 000000003ff80000 - 0000000040000000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[17179569.184000] 127MB HIGHMEM available.
[17179569.184000] 896MB LOWMEM available.
[17179569.184000] On node 0 totalpages: 262000
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   Normal zone: 225280 pages, LIFO batch:31
[17179569.184000]   HighMem zone: 32624 pages, LIFO batch:7
[17179569.184000] DMI present.
[17179569.184000] ACPI: RSDP (v000 PTLTD                                 ) @ 0x000f7240
[17179569.184000] ACPI: RSDT (v001 PTLTD    RSDT   0x06040000  LTP 0x00000000) @ 0x3ff7a87e
[17179569.184000] ACPI: FADT (v001 NVIDIA CK8      0x06040000 PTL_ 0x000f4240) @ 0x3ff7ee13
[17179569.184000] ACPI: MADT (v001 NVIDIA NV_APIC_ 0x06040000  LTP 0x00000000) @ 0x3ff7ee87
[17179569.184000] ACPI: BOOT (v001 PTLTD  $SBFTBL$ 0x06040000  LTP 0x00000001) @ 0x3ff7eee1
[17179569.184000] ACPI: SSDT (v001 PTLTD  POWERNOW 0x06040000  LTP 0x00000001) @ 0x3ff7ef09
[17179569.184000] ACPI: DSDT (v001 NVIDIA      CK8 0x06040000 MSFT 0x0100000e) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x8008
[17179569.184000] ACPI: Local APIC address 0xfee00000
[17179569.184000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[17179569.184000] Processor #0 15:4 APIC version 16
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[17179569.184000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[17179569.184000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[17179569.184000] ACPI: BIOS IRQ0 pin2 override ignored.
[17179569.184000] ACPI: IRQ9 used by override.
[17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[17179569.184000] Using ACPI (MADT) for SMP configuration information
[17179569.184000] Allocating PCI resources starting at 50000000 (gap: 40000000:bff80000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hda1 ro #quiet splash
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
[17179569.184000] Enabling fast FPU save and restore... done.
[17179569.184000] Enabling unmasked SIMD FPU exception support... done.
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[17179569.184000] Detected 798.008 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179569.400000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[17179569.400000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179569.436000] Memory: 1029176k/1048000k available (1829k kernel code, 18072k reserved, 1038k data, 288k init, 130496k highmem)
[17179569.436000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179569.516000] Calibrating delay using timer specific routine.. 1597.86 BogoMIPS (lpj=3195724)
[17179569.516000] Security Framework v1.0.0 initialized
[17179569.516000] SELinux:  Disabled at boot.
[17179569.516000] Mount-cache hash table entries: 512
[17179569.516000] CPU: After generic identify, caps: 078bfbff e1d3fbff 00000000 00000000 00000000 00000000 00000000
[17179569.516000] CPU: After vendor identify, caps: 078bfbff e1d3fbff 00000000 00000000 00000000 00000000 00000000
[17179569.516000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[17179569.516000] CPU: L2 Cache: 1024K (64 bytes/line)
[17179569.516000] CPU: After all inits, caps: 078bfbff e1d3fbff 00000000 00000410 00000000 00000000 00000000
[17179569.516000] CPU: AMD Athlon(tm) 64 Processor 3000+ stepping 08
[17179569.516000] Checking 'hlt' instruction... OK.
[17179569.532000] SMP alternatives: switching to UP code
[17179569.532000] Freeing SMP alternatives: 0k freed
[17179569.532000] checking if image is initramfs... it is
[17179570.644000] Freeing initrd memory: 5510k freed
[17179570.644000] ACPI: Core revision 20060707
[17179570.644000] ACPI: Looking for DSDT ... not found!
[17179570.668000] ENABLING IO-APIC IRQs
[17179570.672000] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
[17179570.816000] NET: Registered protocol family 16
[17179570.816000] EISA bus registered
[17179570.816000] ACPI: bus type pci registered
[17179570.816000] PCI: PCI BIOS revision 2.10 entry at 0xfd8bc, last bus=2
[17179570.816000] PCI: Using configuration type 1
[17179570.816000] Setting up standard PCI resources
[17179570.820000] ACPI: Interpreter enabled
[17179570.820000] ACPI: Using IOAPIC for interrupt routing
[17179570.820000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179570.820000] PCI: Probing PCI hardware (bus 00)
[17179570.848000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:08.0
[17179570.848000] PCI: Bus #03 (-#06) is hidden behind  bridge #02 (-#02) (try 'pci=assign-busses')
[17179570.848000] Please report the result to linux-kernel to fix this permanently
[17179570.852000] PCI: Bus #07 (-#0a) is hidden behind  bridge #02 (-#02) (try 'pci=assign-busses')
[17179570.852000] Please report the result to linux-kernel to fix this permanently
[17179570.852000] Boot video device is 0000:01:00.0
[17179570.852000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179570.876000] ACPI: Embedded Controller [EC0] (gpe 33) interrupt mode.
[17179570.920000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P0._PRT]
[17179570.924000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP0._PRT]
[17179570.924000] ACPI: PCI Interrupt Link [LNK1] (IRQs 16 18 19) *0
[17179570.924000] ACPI: PCI Interrupt Link [LNK2] (IRQs 16 18 19) *0
[17179570.924000] ACPI: PCI Interrupt Link [LNK3] (IRQs 17) *0
[17179570.924000] ACPI: PCI Interrupt Link [LNK4] (IRQs 16 18 19) *0, disabled.
[17179570.928000] ACPI: PCI Interrupt Link [LNK5] (IRQs 16 18 19) *0
[17179570.928000] ACPI: PCI Interrupt Link [LSMB] (IRQs 20 21 22) *0
[17179570.928000] ACPI: PCI Interrupt Link [LUS0] (IRQs 20 21 22) *0
[17179570.928000] ACPI: PCI Interrupt Link [LUS1] (IRQs 20 21 22) *0
[17179570.928000] ACPI: PCI Interrupt Link [LUS2] (IRQs 20 21 22) *0
[17179570.932000] ACPI: PCI Interrupt Link [LMAC] (IRQs 20 21 22) *0, disabled.
[17179570.932000] ACPI: PCI Interrupt Link [LACI] (IRQs 20 21 22) *0
[17179570.932000] ACPI: PCI Interrupt Link [LMCI] (IRQs 20 21 22) *0
[17179570.932000] ACPI: PCI Interrupt Link [LPID] (IRQs 20 21 22) *0, disabled.
[17179570.936000] ACPI: PCI Interrupt Link [LTID] (IRQs 20 21 22) *0, disabled.
[17179570.936000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179570.936000] pnp: PnP ACPI init
[17179570.960000] pnp: PnP ACPI: found 12 devices
[17179570.960000] PnPBIOS: Disabled by ACPI PNP
[17179570.960000] PCI: Using ACPI for IRQ routing
[17179570.960000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179570.968000] pnp: 00:01: ioport range 0x8000-0x807f could not be reserved
[17179570.968000] pnp: 00:01: ioport range 0x8080-0x80ff has been reserved
[17179570.968000] pnp: 00:01: ioport range 0x8400-0x847f has been reserved
[17179570.968000] pnp: 00:01: ioport range 0x8480-0x84ff could not be reserved
[17179570.968000] pnp: 00:01: ioport range 0x8800-0x887f has been reserved
[17179570.968000] pnp: 00:01: ioport range 0x8880-0x88ff has been reserved
[17179570.968000] pnp: 00:01: ioport range 0x2040-0x207f has been reserved
[17179570.968000] pnp: 00:01: ioport range 0x2000-0x203f has been reserved
[17179570.968000] PCI: Failed to allocate mem resource #10:2000000@e2000000 for 0000:02:04.0
[17179570.968000] PCI: Failed to allocate mem resource #10:2000000@e2000000 for 0000:02:04.1
[17179570.968000] PCI: Bus 3, cardbus bridge: 0000:02:04.0
[17179570.968000]   IO window: 00003000-000030ff
[17179570.968000]   IO window: 00003400-000034ff
[17179570.968000]   PREFETCH window: 50000000-51ffffff
[17179570.968000] PCI: Bus 7, cardbus bridge: 0000:02:04.1
[17179570.968000]   IO window: 00003800-000038ff
[17179570.968000]   IO window: 00003c00-00003cff
[17179570.968000]   PREFETCH window: 52000000-53ffffff
[17179570.968000] PCI: Bridge: 0000:00:0a.0
[17179570.968000]   IO window: 3000-7fff
[17179570.968000]   MEM window: e0100000-e17fffff
[17179570.968000]   PREFETCH window: 50000000-53ffffff
[17179570.968000] PCI: Bridge: 0000:00:0b.0
[17179570.968000]   IO window: disabled.
[17179570.968000]   MEM window: e2000000-e2ffffff
[17179570.968000]   PREFETCH window: f0000000-f80fffff
[17179570.968000] PCI: Setting latency timer of device 0000:00:0a.0 to 64
[17179570.968000] ACPI: PCI Interrupt Link [LNK1] enabled at IRQ 19
[17179570.968000] ACPI: PCI Interrupt 0000:02:04.0[A] -> Link [LNK1] -> GSI 19 (level, low) -> IRQ 177
[17179570.968000] ACPI: PCI Interrupt Link [LNK2] enabled at IRQ 18
[17179570.968000] ACPI: PCI Interrupt 0000:02:04.1[B] -> Link [LNK2] -> GSI 18 (level, low) -> IRQ 185
[17179570.968000] NET: Registered protocol family 2
[17179571.004000] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179571.004000] TCP established hash table entries: 131072 (order: 7, 524288 bytes)
[17179571.004000] TCP bind hash table entries: 65536 (order: 6, 262144 bytes)
[17179571.004000] TCP: Hash tables configured (established 131072 bind 65536)
[17179571.004000] TCP reno registered
[17179571.004000] Simple Boot Flag at 0x37 set to 0x1
[17179571.004000] audit: initializing netlink socket (disabled)
[17179571.004000] audit(1170631005.004:1): initialized
[17179571.004000] highmem bounce pool size: 64 pages
[17179571.004000] VFS: Disk quotas dquot_6.5.1
[17179571.004000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179571.004000] Initializing Cryptographic API
[17179571.004000] io scheduler noop registered
[17179571.004000] io scheduler anticipatory registered
[17179571.004000] io scheduler deadline registered
[17179571.004000] io scheduler cfq registered (default)
[17179571.008000] isapnp: Scanning for PnP cards...
[17179571.360000] isapnp: No Plug & Play device found
[17179571.392000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[17179571.396000] ACPI: PCI Interrupt Link [LMCI] enabled at IRQ 22
[17179571.396000] ACPI: PCI Interrupt 0000:00:06.1[B] -> Link [LMCI] -> GSI 22 (level, low) -> IRQ 193
[17179571.396000] ACPI: PCI interrupt for device 0000:00:06.1 disabled
[17179571.396000] mice: PS/2 mouse device common for all mice
[17179571.396000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179571.396000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179571.396000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179571.396000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[17179571.404000] i8042.c: Detected active multiplexing controller, rev 1.1.
[17179571.412000] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[17179571.412000] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[17179571.412000] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[17179571.412000] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[17179571.416000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179571.416000] EISA: Probing bus 0 at eisa.0
[17179571.416000] Cannot allocate resource for EISA slot 1
[17179571.416000] Cannot allocate resource for EISA slot 2
[17179571.416000] Cannot allocate resource for EISA slot 3
[17179571.416000] Cannot allocate resource for EISA slot 4
[17179571.416000] Cannot allocate resource for EISA slot 5
[17179571.416000] Cannot allocate resource for EISA slot 6
[17179571.416000] Cannot allocate resource for EISA slot 7
[17179571.416000] Cannot allocate resource for EISA slot 8
[17179571.416000] EISA: Detected 0 cards.
[17179571.416000] TCP bic registered
[17179571.416000] NET: Registered protocol family 1
[17179571.416000] NET: Registered protocol family 8
[17179571.416000] NET: Registered protocol family 20
[17179571.416000] Using IPI Shortcut mode
[17179571.416000] ACPI: (supports S0 S3 S4 S5)
[17179571.416000] Freeing unused kernel memory: 288k freed
[17179571.460000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179572.604000] Capability LSM initialized
[17179572.700000] ACPI: CPU0 (power states: C1[C1] C2[C2])
[17179572.708000] ACPI Exception (acpi_thermal-0417): AE_NOT_FOUND, Invalid active threshold [0] [20060707]
[17179572.708000] ACPI: Thermal Zone [THRM] (47 C)
[17179573.564000] SCSI subsystem initialized
[17179573.568000] libata version 1.20 loaded.
[17179573.572000] NFORCE3-150: IDE controller at PCI slot 0000:00:08.0
[17179573.572000] NFORCE3-150: chipset revision 165
[17179573.572000] NFORCE3-150: not 100% native mode: will probe irqs later
[17179573.572000] NFORCE3-150: BIOS didn't set cable bits correctly. Enabling workaround.
[17179573.572000] NFORCE3-150: 0000:00:08.0 (rev a5) UDMA133 controller
[17179573.572000]     ide0: BM-DMA at 0x2080-0x2087, BIOS settings: hda:DMA, hdb:pio
[17179573.572000]     ide1: BM-DMA at 0x2088-0x208f, BIOS settings: hdc:DMA, hdd:pio
[17179573.572000] Probing IDE interface ide0...
[17179573.860000] hda: FUJITSU MHT2080AH PL, ATA DISK drive
[17179574.536000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179574.612000] Probing IDE interface ide1...
[17179575.348000] hdc: _NEC DVD+/-RW ND-6500A, ATAPI CD/DVD-ROM drive
[17179576.036000] ide1 at 0x170-0x177,0x376 on irq 15
[17179576.052000] hda: max request size: 128KiB
[17179576.068000] hda: 156301488 sectors (80026 MB) w/8192KiB Cache, CHS=65535/16/63, UDMA(100)
[17179576.068000] hda: cache flushes supported
[17179576.068000]  hda: hda1 hda2 < hda5 > hda3
[17179576.160000] hdc: ATAPI 24X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, DMA
[17179576.160000] Uniform CD-ROM driver Revision: 3.20
[17179576.556000] usbcore: registered new driver usbfs
[17179576.556000] usbcore: registered new driver hub
[17179576.556000] ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[17179576.556000] PCI: Enabling device 0000:00:02.0 (0004 -> 0006)
[17179576.556000] ACPI: PCI Interrupt Link [LUS0] enabled at IRQ 21
[17179576.556000] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [LUS0] -> GSI 21 (level, low) -> IRQ 201
[17179576.556000] PCI: Setting latency timer of device 0000:00:02.0 to 64
[17179576.556000] ohci_hcd 0000:00:02.0: OHCI Host Controller
[17179576.556000] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
[17179576.768000] ohci_hcd 0000:00:02.0: irq 201, io mem 0xe0000000
[17179576.820000] ieee1394: Initialized config rom entry `ip1394'
[17179576.856000] usb usb1: configuration #1 chosen from 1 choice
[17179576.856000] hub 1-0:1.0: USB hub found
[17179576.856000] hub 1-0:1.0: 3 ports detected
[17179576.960000] ACPI: PCI Interrupt Link [LUS2] enabled at IRQ 20
[17179576.960000] ACPI: PCI Interrupt 0000:00:02.2[C] -> Link [LUS2] -> GSI 20 (level, low) -> IRQ 209
[17179576.960000] PCI: Setting latency timer of device 0000:00:02.2 to 64
[17179576.960000] ehci_hcd 0000:00:02.2: EHCI Host Controller
[17179576.960000] ehci_hcd 0000:00:02.2: new USB bus registered, assigned bus number 2
[17179576.960000] PCI: cache line size of 64 is not supported by device 0000:00:02.2
[17179576.960000] ehci_hcd 0000:00:02.2: irq 209, io mem 0xe0004000
[17179576.960000] ehci_hcd 0000:00:02.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179576.960000] usb usb2: configuration #1 chosen from 1 choice
[17179576.960000] hub 2-0:1.0: USB hub found
[17179576.960000] hub 2-0:1.0: 6 ports detected
[17179577.080000] PCI: Enabling device 0000:00:02.1 (0004 -> 0006)
[17179577.084000] ACPI: PCI Interrupt Link [LUS1] enabled at IRQ 22
[17179577.084000] ACPI: PCI Interrupt 0000:00:02.1[B] -> Link [LUS1] -> GSI 22 (level, low) -> IRQ 193
[17179577.084000] PCI: Setting latency timer of device 0000:00:02.1 to 64
[17179577.084000] ohci_hcd 0000:00:02.1: OHCI Host Controller
[17179577.084000] ohci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 3
[17179577.288000] ohci_hcd 0000:00:02.1: irq 193, io mem 0xe0001000
[17179577.344000] usb usb3: configuration #1 chosen from 1 choice
[17179577.344000] hub 3-0:1.0: USB hub found
[17179577.344000] hub 3-0:1.0: 3 ports detected
[17179577.484000] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [LNK1] -> GSI 19 (level, low) -> IRQ 177
[17179577.536000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[177]  MMIO=[e0108000-e01087ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[17179577.636000] Attempting manual resume
[17179577.688000] kjournald starting.  Commit interval 5 seconds
[17179577.688000] EXT3-fs: mounted filesystem with ordered data mode.
[17179577.776000] usb 3-2: new full speed USB device using ohci_hcd and address 2
[17179577.996000] usb 3-2: configuration #1 chosen from 1 choice
[17179578.808000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[533f0200533f0200]
[17179590.224000] Real Time Clock Driver v1.12ac
[17179590.432000] input: PC Speaker as /class/input/input1
[17179590.448000] Linux agpgart interface v0.101 (c) Dave Jones
[17179590.452000] agpgart: Detected AGP bridge 0
[17179590.452000] agpgart: Setting up Nforce3 AGP.
[17179590.460000] agpgart: AGP aperture is 128M @ 0xe8000000
[17179590.584000] parport: PnPBIOS parport detected.
[17179590.584000] parport0: PC-style at 0x378 (0x778), irq 7, dma 1 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[17179590.768000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179590.768000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179590.812000] i2c_adapter i2c-0: nForce2 SMBus adapter at 0x2040
[17179590.812000] i2c_adapter i2c-1: nForce2 SMBus adapter at 0x2000
[17179590.928000] input: PS/2 Mouse as /class/input/input2
[17179590.956000] input: AlpsPS/2 ALPS GlidePoint as /class/input/input3
[17179591.160000] ACPI: PCI Interrupt Link [LACI] enabled at IRQ 21
[17179591.160000] ACPI: PCI Interrupt 0000:00:06.0[A] -> Link [LACI] -> GSI 21 (level, low) -> IRQ 201
[17179591.160000] PCI: Setting latency timer of device 0000:00:06.0 to 64
[17179591.732000] intel8x0_measure_ac97_clock: measured 55391 usecs
[17179591.732000] intel8x0: clocking to 47478
[17179592.408000] nvidia: module license 'NVIDIA' taints kernel.
[17179592.412000] ACPI: PCI Interrupt Link [LNK5] enabled at IRQ 16
[17179592.412000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNK5] -> GSI 16 (level, low) -> IRQ 217
[17179592.412000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-8776  Mon Oct 16 21:56:04 PDT 2006
[17179592.680000] Floppy drive(s): fd0 is 1.44M
[17179592.756000] ACPI: PCI Interrupt 0000:02:04.0[A] -> Link [LNK1] -> GSI 19 (level, low) -> IRQ 177
[17179592.756000] Yenta: CardBus bridge found at 0000:02:04.0 [103c:006d]
[17179592.756000] PCI: Bus 3, cardbus bridge: 0000:02:04.0
[17179592.756000]   IO window: 00003000-000030ff
[17179592.756000]   IO window: 00003400-000034ff
[17179592.756000]   PREFETCH window: 50000000-51ffffff
[17179592.756000]   MEM window: e0400000-e07fffff
[17179592.756000] Yenta: Enabling burst memory read transactions
[17179592.756000] Yenta: Using CSCINT to route CSC interrupts to PCI
[17179592.756000] Yenta: Routing CardBus interrupts to PCI
[17179592.756000] Yenta TI: socket 0000:02:04.0, mfunc 0x01111d22, devctl 0x64
[17179592.844000] 8139too Fast Ethernet driver 0.9.27
[17179592.988000] Yenta: ISA IRQ mask 0x0c38, PCI irq 177
[17179592.988000] Socket status: 30000006
[17179592.988000] Yenta: Raising subordinate bus# of parent bus (#02) from #02 to #06
[17179592.988000] pcmcia: parent PCI bridge I/O window: 0x3000 - 0x7fff
[17179592.988000] cs: IO port probe 0x3000-0x7fff: clean.
[17179592.988000] pcmcia: parent PCI bridge Memory window: 0xe0100000 - 0xe17fffff
[17179592.988000] pcmcia: parent PCI bridge Memory window: 0x50000000 - 0x53ffffff
[17179592.988000] ACPI: PCI Interrupt 0000:02:04.1[B] -> Link [LNK2] -> GSI 18 (level, low) -> IRQ 185
[17179592.988000] Yenta: CardBus bridge found at 0000:02:04.1 [103c:006d]
[17179592.988000] Yenta: Using CSCINT to route CSC interrupts to PCI
[17179592.988000] Yenta: Routing CardBus interrupts to PCI
[17179592.988000] Yenta TI: socket 0000:02:04.1, mfunc 0x01111d22, devctl 0x64
[17179592.992000] Bluetooth: Core ver 2.8
[17179592.992000] NET: Registered protocol family 31
[17179592.992000] Bluetooth: HCI device and connection manager initialized
[17179592.992000] Bluetooth: HCI socket layer initialized
[17179592.992000] FDC 0 is a post-1991 82077
[17179593.120000] Bluetooth: HCI USB driver ver 2.9
[17179593.136000] usbcore: registered new driver hci_usb
[17179593.220000] Yenta: ISA IRQ mask 0x0c38, PCI irq 185
[17179593.220000] Socket status: 30000006
[17179593.220000] Yenta: Raising subordinate bus# of parent bus (#02) from #06 to #0a
[17179593.220000] pcmcia: parent PCI bridge I/O window: 0x3000 - 0x7fff
[17179593.220000] cs: IO port probe 0x3000-0x7fff: clean.
[17179593.224000] pcmcia: parent PCI bridge Memory window: 0xe0100000 - 0xe17fffff
[17179593.224000] pcmcia: parent PCI bridge Memory window: 0x50000000 - 0x53ffffff
[17179593.232000] ACPI: PCI Interrupt 0000:02:01.0[A] -> Link [LNK2] -> GSI 18 (level, low) -> IRQ 185
[17179593.236000] eth0: RealTek RTL8139 at 0xf8956800, 00:0f:b0:4c:cb:aa, IRQ 185
[17179593.236000] eth0:  Identified 8139 chip type 'RTL-8101'
[17179593.260000] 8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
[17179593.960000] ts: Compaq touchscreen protocol output
[17179594.764000] cs: IO port probe 0x100-0x3af: excluding 0x200-0x20f
[17179594.764000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[17179594.768000] cs: IO port probe 0x820-0x8ff: clean.
[17179594.768000] cs: IO port probe 0xc00-0xcf7: clean.
[17179594.768000] cs: IO port probe 0xa00-0xaff: clean.
[17179594.768000] cs: IO port probe 0x100-0x3af: excluding 0x200-0x20f
[17179594.772000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[17179594.772000] cs: IO port probe 0x820-0x8ff: clean.
[17179594.772000] cs: IO port probe 0xc00-0xcf7: clean.
[17179594.772000] cs: IO port probe 0xa00-0xaff: clean.
[17179594.848000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[17179595.044000] lp0: using parport0 (interrupt-driven).
[17179595.076000] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)
[17179595.076000] ieee1394: sbp2: Try serialize_io=0 for better performance
[17179595.152000] Adding 1975952k swap on /dev/disk/by-uuid/27c30d06-985c-4e71-9b39-28e4c6189130.  Priority:-1 extents:1 across:1975952k
[17179595.276000] EXT3 FS on hda1, internal journal
[17179595.632000] kjournald starting.  Commit interval 5 seconds
[17179595.640000] EXT3 FS on hda3, internal journal
[17179595.640000] EXT3-fs: mounted filesystem with ordered data mode.
[17179595.900000] NET: Registered protocol family 17
[17179597.488000] ACPI: AC Adapter [ACAD] (on-line)
[17179597.688000] ACPI: Battery Slot [BAT1] (battery present)
[17179597.720000] ACPI: Power Button (FF) [PWRF]
[17179597.720000] ACPI: Power Button (CM) [PWRB]
[17179597.720000] ACPI: Lid Switch [LID]
[17179597.900000] ibm_acpi: ec object not found
[17179597.948000] pcc_acpi: loading...
[17179598.128000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[17179598.520000] powernow-k8: Found 1 AMD Athlon 64 / Opteron processors (version 1.60.2)
[17179598.520000] powernow-k8:    0 : fid 0xa (1800 MHz), vid 0x2 (1500 mV)
[17179598.520000] powernow-k8:    1 : fid 0x8 (1600 MHz), vid 0x6 (1400 mV)
[17179598.520000] powernow-k8:    2 : fid 0x0 (800 MHz), vid 0x12 (1100 mV)
[17179598.520000] cpu_init done, current fid 0x0, vid 0x12
[17179598.864000] NET: Registered protocol family 10
[17179598.864000] lo: Disabled Privacy Extensions
[17179598.864000] IPv6 over IPv4 tunneling driver
[17179601.056000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[17179601.056000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[17179601.056000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[17179603.272000] apm: BIOS not found.
[17179608.868000] Bluetooth: L2CAP ver 2.8
[17179608.868000] Bluetooth: L2CAP socket layer initialized
[17179608.868000] Bluetooth: RFCOMM socket layer initialized
[17179608.868000] Bluetooth: RFCOMM TTY layer initialized
[17179608.868000] Bluetooth: RFCOMM ver 1.7
[17179623.964000] eth0: no IPv6 routers present
[17179630.640000] eth0: link down
[17179684.132000] ndiswrapper version 1.22 loaded (preempt=no,smp=no)
[17179684.244000] ndiswrapper: driver bcmwl5 (Broadcom,04/21/2005, 3.100.65.1) loaded
[17179684.244000] ACPI: PCI Interrupt Link [LNK3] enabled at IRQ 17
[17179684.244000] ACPI: PCI Interrupt 0000:02:02.0[A] -> Link [LNK3] -> GSI 17 (level, low) -> IRQ 225
[17179684.248000] ndiswrapper: using irq 225
[17179685.016000] wlan0: vendor: ''
[17179685.016000] wlan0: ethernet device 00:90:4b:a8:db:6f using NDIS driver bcmwl5, 14E4:4320:103C:12F8.5.conf
[17179685.016000] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[17179685.020000] [COLOR="Red"]ndiswrapper: changing interface name from 'wlan0' to 'eth1'[/COLOR]
[17179685.072000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[17179816.608000] eth1: no IPv6 routers present
[17179835.800000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[17179837.832000] ndiswrapper (iw_set_freq:376): setting configuration failed (00010003)
[17179846.028000] eth1: no IPv6 routers present
[17179930.448000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[17179940.964000] eth1: no IPv6 routers present
[17180008.136000] eth1: no IPv6 routers present
[17180033.688000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[17180044.280000] eth1: no IPv6 routers present
[17180153.824000] eth1: no IPv6 routers present
[17180232.952000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[17180232.952000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[17180233.004000] eth0: link down
[17180234.788000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[17180243.904000] eth0: no IPv6 routers present
[17180256.408000] eth0: no IPv6 routers present
[17180289.632000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[17180311.772000] eth0: link down
[17180368.736000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[17180453.540000] eth1: no IPv6 routers present
[17180667.936000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[17180678.460000] eth1: no IPv6 routers present
[17180743.848000] eth1: no IPv6 routers present
[17181209.104000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[17181209.108000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[17181223.156000] eth0: no IPv6 routers present
[17181307.612000] eth0: link down
[17181360.120000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[17181370.776000] eth1: no IPv6 routers present
[17181443.632000] eth1: no IPv6 routers present
[17181555.572000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[17181565.624000] eth1: no IPv6 routers present
[17181642.768000] eth1: no IPv6 routers present
[17181794.544000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[17181794.544000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[17181810.252000] eth0: no IPv6 routers present


Any help is appreciated......

---

### Post by bnuytten on 2007-02-18
less /etc/network/interfaces, look for map or mapping. See man 5 interfaces for information. Probably has nothing to do with your DHCP issue however.

---

