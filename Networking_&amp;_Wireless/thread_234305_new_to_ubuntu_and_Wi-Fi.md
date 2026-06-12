---
title: "new to ubuntu and Wi-Fi"
date: 2006-08-11
forum: Networking &amp; Wireless
---

### Post by Lasborg on 2006-08-11
Just got a usb wi-fi adapter the phillips snu5600 and i cannot get it to work in ubuntu.

As far as i can find out, it is not one of the supported adaptors. So I used Ndiswrapper (with ndisgtk as frontend for ease of use) and the drivers seem to work. (even thoug ndiswrapper doesn't support my adapter).
In ndisgtk i can see the driver (named: cpwgu) and it says that hardware is present.
But when i go to ubuntus network settings, it just keeps "thinking" and all the buttons are greyed out.

Is this simply because my network adapter is unsuported, or is there something else i could do.

thanks in advance. I hope i can get it to work, because i've become quite fond of ubuntu, but if i can't get wi-fi, i really have no use for it :sad:

---

### Post by bensexson on 2006-08-11
Post the output from sudo ifconfig -a, sudo iwconfig, and dmesg.

---

### Post by Lasborg on 2006-08-11
IFCONFIG:
eth0      Link encap:Ethernet  HWaddr 00:0B:CD:A7:01:CF
          inet addr:192.168.1.34  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20b:cdff:fea7:1cf/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:529 errors:0 dropped:0 overruns:0 frame:0
          TX packets:432 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:553887 (540.9 KiB)  TX bytes:93991 (91.7 KiB)
          Interrupt:10 Base address:0xa000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:10 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:736 (736.0 b)  TX bytes:736 (736.0 b)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:12:BF:2F:CE:5C
          inet6 addr: fe80::212:bfff:fe2f:ce5c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

IWCONFIG:
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

DMESG:
17179569.184000] Linux version 2.6.15-26-386 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Thu Aug 3 02:52:00 UTC 2006
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[17179569.184000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000d8000 - 00000000000e0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000001bf70000 (usable)
[17179569.184000]  BIOS-e820: 000000001bf70000 - 000000001bf7f000 (ACPI data)
[17179569.184000]  BIOS-e820: 000000001bf7f000 - 000000001bf80000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 000000001bf80000 - 000000001c000000 (reserved)
[17179569.184000]  BIOS-e820: 000000002bf80000 - 000000002c000000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 447MB LOWMEM available.
[17179569.184000] On node 0 totalpages: 114544
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   DMA32 zone: 0 pages, LIFO batch:0
[17179569.184000]   Normal zone: 110448 pages, LIFO batch:31
[17179569.184000]   HighMem zone: 0 pages, LIFO batch:0
[17179569.184000] DMI 2.3 present.
[17179569.184000] ATI board detected. Disabling timer routing over 8254.
[17179569.184000] ACPI: RSDP (v000 PTLTD                                 ) @ 0x000f6ae0
[17179569.184000] ACPI: RSDT (v001 PTLTD    RSDT   0x06040000  LTP 0x00000000) @ 0x1bf78e5c
[17179569.184000] ACPI: FADT (v001 ATI    Salmon   0x06040000 ATI  0x000f4240) @ 0x1bf7ef64
[17179569.184000] ACPI: BOOT (v001 PTLTD  $SBFTBL$ 0x06040000  LTP 0x00000001) @ 0x1bf7efd8
[17179569.184000] ACPI: DSDT (v001    ATI MS2_1535 0x06040000 MSFT 0x0100000e) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x8008
[17179569.184000] Allocating PCI resources starting at 30000000 (gap: 2c000000:d3f80000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hda2 ro quiet splash
[17179569.184000] Local APIC disabled by BIOS (or by default) -- you can enable it with "lapic"
[17179569.184000] mapped APIC to ffffd000 (01381000)
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 2048 (order: 11, 32768 bytes)
[17179569.184000] Detected 2193.392 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179571.528000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179571.528000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)[17179571.544000] Memory: 443700k/458176k available (1976k kernel code, 13908k reserved, 606k data, 288k init, 0k highmem)
[17179571.544000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179571.624000] Calibrating delay using timer specific routine.. 4389.97 BogoMIPS (lpj=8779953)
[17179571.624000] Security Framework v1.0.0 initialized
[17179571.624000] SELinux:  Disabled at boot.
[17179571.624000] Mount-cache hash table entries: 512
[17179571.624000] CPU: After generic identify, caps: bfebf9ff 00000000 00000000 00000000 00000400 00000000 00000000
[17179571.624000] CPU: After vendor identify, caps: bfebf9ff 00000000 00000000 00000000 00000400 00000000 00000000
[17179571.624000] CPU: Trace cache: 12K uops, L1 D cache: 8K
[17179571.624000] CPU: L2 cache: 256K
[17179571.624000] CPU: After all inits, caps: bfebf9ff 00000000 00000000 00000080 00000400 00000000 00000000
[17179571.624000] mtrr: v2.0 (20020519)
[17179571.624000] CPU: Intel Mobile Intel(R) Celeron(R) CPU 2.20GHz stepping 07
[17179571.624000] Enabling fast FPU save and restore... done.
[17179571.624000] Enabling unmasked SIMD FPU exception support... done.
[17179571.624000] Checking 'hlt' instruction... OK.
[17179571.640000] checking if image is initramfs... it is
[17179572.280000] Freeing initrd memory: 6617k freed
[17179572.336000] ACPI: Looking for DSDT ... not found!
[17179572.336000] ACPI: setting ELCR to 0200 (from 0420)
[17179572.340000] NET: Registered protocol family 16
[17179572.340000] EISA bus registered
[17179572.340000] ACPI: bus type pci registered
[17179572.376000] PCI: PCI BIOS revision 2.10 entry at 0xfd89b, last bus=2
[17179572.376000] PCI: Using configuration type 1
[17179572.376000] ACPI: Subsystem revision 20051216
[17179574.604000] ACPI: Interpreter enabled
[17179574.604000] ACPI: Using PIC for interrupt routing
[17179574.604000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179574.604000] PCI: Probing PCI hardware (bus 00)
[17179574.608000] PCI quirk: region 8000-803f claimed by ali7101 ACPI
[17179574.608000] PCI quirk: region 8040-805f claimed by ali7101 SMB
[17179574.608000] Boot video device is 0000:01:05.0
[17179574.608000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179574.608000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGPB._PRT]
[17179574.612000] ACPI: PCI Interrupt Link [LNK0] (IRQs 7 10) *0, disabled.
[17179574.612000] ACPI: PCI Interrupt Link [LNK1] (IRQs 7 *10)
[17179574.612000] ACPI: PCI Interrupt Link [LNK2] (IRQs 7 10) *0, disabled.
[17179574.612000] ACPI: PCI Interrupt Link [LNK3] (IRQs 7 10) *0, disabled.
[17179574.612000] ACPI: PCI Interrupt Link [LNK4] (IRQs 7 10) *0, disabled.
[17179574.612000] ACPI: PCI Interrupt Link [LNK5] (IRQs 7 *11)
[17179574.612000] ACPI: PCI Interrupt Link [LNK6] (IRQs 7 10) *0, disabled.
[17179574.612000] ACPI: PCI Interrupt Link [LNK7] (IRQs *5)
[17179574.612000] ACPI: PCI Interrupt Link [LNK8] (IRQs 7 *10)
[17179574.616000] ACPI: Embedded Controller [EC0] (gpe 24) interrupt mode.
[17179574.620000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179574.620000] pnp: PnP ACPI init
[17179574.624000] pnp: PnP ACPI: found 13 devices
[17179574.624000] PnPBIOS: Disabled by ACPI PNP
[17179574.624000] PCI: Using ACPI for IRQ routing
[17179574.624000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179574.628000] pnp: 00:06: ioport range 0x40b-0x40b has been reserved
[17179574.628000] pnp: 00:06: ioport range 0x480-0x48f has been reserved
[17179574.628000] pnp: 00:06: ioport range 0x4d0-0x4d1 has been reserved
[17179574.628000] pnp: 00:06: ioport range 0x4d6-0x4d6 has been reserved
[17179574.628000] pnp: 00:06: ioport range 0x8000-0x807f could not be reserved
[17179574.628000] PCI: Bridge: 0000:00:01.0
[17179574.628000]   IO window: 9000-9fff
[17179574.628000]   MEM window: d0300000-d03fffff
[17179574.628000]   PREFETCH window: d8000000-dfffffff
[17179574.628000] PCI: Bus 2, cardbus bridge: 0000:00:0a.0
[17179574.628000]   IO window: 00001800-000018ff
[17179574.628000]   IO window: 00001c00-00001cff
[17179574.628000]   PREFETCH window: 30000000-31ffffff
[17179574.628000]   MEM window: 32000000-33ffffff
[17179574.628000] PCI: Enabling device 0000:00:0a.0 (0005 -> 0007)
[17179574.628000] **** SET: Misaligned resource pointer: db9165c2 Type 07 Len 0
[17179574.628000] ACPI: PCI Interrupt Link [LNK5] enabled at IRQ 11
[17179574.628000] PCI: setting IRQ 11 as level-triggered
[17179574.628000] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [LNK5] -> GSI 11 (level, low) -> IRQ 11
[17179574.628000] Simple Boot Flag at 0x37 set to 0x1
[17179574.628000] audit: initializing netlink socket (disabled)
[17179574.628000] audit(1155311338.628:1): initialized
[17179574.628000] VFS: Disk quotas dquot_6.5.1
[17179574.628000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179574.628000] Initializing Cryptographic API
[17179574.628000] io scheduler noop registered
[17179574.628000] io scheduler anticipatory registered
[17179574.628000] io scheduler deadline registered
[17179574.628000] io scheduler cfq registered
[17179574.628000] Activating ISA DMA hang workarounds.
[17179574.628000] isapnp: Scanning for PnP cards...
[17179574.984000] isapnp: No Plug & Play device found
[17179575.012000] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[17179575.024000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179575.024000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179575.024000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[17179575.024000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179575.028000] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179575.028000] PCI: Enabling device 0000:00:08.0 (0000 -> 0003)
[17179575.028000] **** SET: Misaligned resource pointer: db38b1c2 Type 07 Len 0
[17179575.028000] ACPI: PCI Interrupt Link [LNK6] enabled at IRQ 10
[17179575.028000] PCI: setting IRQ 10 as level-triggered
[17179575.028000] ACPI: PCI Interrupt 0000:00:08.0[A] -> Link [LNK6] -> GSI 10 (level, low) -> IRQ 10
[17179575.032000] 0000:00:08.0: ttyS9 at I/O 0x1428 (irq = 10) is a 8250
[17179575.032000] 0000:00:08.0: ttyS12 at I/O 0x1440 (irq = 10) is a 8250
[17179575.032000] 0000:00:08.0: ttyS14 at I/O 0x1450 (irq = 10) is a 8250
[17179575.036000] 0000:00:08.0: ttyS16 at I/O 0x1460 (irq = 10) is a 8250
[17179575.036000] 0000:00:08.0: ttyS18 at I/O 0x1470 (irq = 10) is a 8250
[17179575.044000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179575.044000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179575.044000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179575.044000] mice: PS/2 mouse device common for all mice
[17179575.044000] EISA: Probing bus 0 at eisa.0
[17179575.044000] Cannot allocate resource for EISA slot 1
[17179575.044000] Cannot allocate resource for EISA slot 2
[17179575.044000] Cannot allocate resource for EISA slot 8
[17179575.044000] EISA: Detected 0 cards.
[17179575.044000] NET: Registered protocol family 2
[17179575.080000] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[17179575.080000] TCP established hash table entries: 16384 (order: 4, 65536 bytes)
[17179575.080000] TCP bind hash table entries: 16384 (order: 4, 65536 bytes)
[17179575.080000] TCP: Hash tables configured (established 16384 bind 16384)
[17179575.080000] TCP reno registered
[17179575.080000] TCP bic registered
[17179575.080000] NET: Registered protocol family 1
[17179575.080000] NET: Registered protocol family 8
[17179575.080000] NET: Registered protocol family 20
[17179575.080000] Using IPI Shortcut mode
[17179575.080000] ACPI wakeup devices:
[17179575.080000] PCI0 MDEM  LAN COM1  LID
[17179575.080000] ACPI: (supports S0 S3 S4 S5)
[17179575.080000] Freeing unused kernel memory: 288k freed
[17179575.088000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179575.160000] vga16fb: initializing
[17179575.160000] vga16fb: mapped to 0xc00a0000
[17179575.288000] Console: switching to colour frame buffer device 80x25
[17179575.288000] fb0: VGA16 VGA frame buffer device
[17179576.464000] Capability LSM initialized
[17179576.528000] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[17179576.528000] ACPI: Processor [CPU0] (supports 8 throttling states)
[17179576.528000] ACPI: Thermal Zone [THRM] (59 C)
[17179577.640000] ALI15X3: IDE controller at PCI slot 0000:00:10.0
[17179577.640000] ACPI: PCI Interrupt 0000:00:10.0[A]: no GSI
[17179577.640000] ALI15X3: chipset revision 196
[17179577.640000] ALI15X3: not 100% native mode: will probe irqs later
[17179577.640000]     ide0: BM-DMA at 0x2000-0x2007, BIOS settings: hda:DMA, hdb:pio
[17179577.640000]     ide1: BM-DMA at 0x2008-0x200f, BIOS settings: hdc:pio, hdd:pio
[17179577.640000] Probing IDE interface ide0...
[17179577.928000] hda: HITACHI_DK23EA-30, ATA DISK drive
[17179578.600000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179578.600000] Probing IDE interface ide1...
[17179579.340000] hdc: TOSHIBA DVD-ROM SD-R2312, ATAPI CD/DVD-ROM drive
[17179580.020000] ide1 at 0x170-0x177,0x376 on irq 15
[17179580.044000] hda: max request size: 128KiB
[17179580.056000] hda: 58605120 sectors (30005 MB) w/2048KiB Cache, CHS=58140/16/63, UDMA(100)
[17179580.056000] hda: cache flushes supported
[17179580.060000]  hda: hda1 hda2 hda3 < hda5 >
[17179580.096000] hdc: ATAPI 24X DVD-ROM CD-R/RW drive, 2048kB Cache, DMA
[17179580.096000] Uniform CD-ROM driver Revision: 3.20
[17179580.512000] usbcore: registered new driver usbfs
[17179580.512000] usbcore: registered new driver hub
[17179580.516000] ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[17179580.516000] **** SET: Misaligned resource pointer: dbc1e402 Type 07 Len 0
[17179580.516000] ACPI: PCI Interrupt Link [LNK8] enabled at IRQ 10
[17179580.516000] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [LNK8] -> GSI 10 (level, low) -> IRQ 10
[17179580.516000] ohci_hcd 0000:00:02.0: OHCI Host Controller
[17179580.740000] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
[17179580.740000] ohci_hcd 0000:00:02.0: irq 10, io mem 0xd0000000
[17179580.796000] hub 1-0:1.0: USB hub found
[17179580.796000] hub 1-0:1.0: 4 ports detected
[17179580.992000] Attempting manual resume
[17179581.024000] EXT3-fs: mounted filesystem with ordered data mode.
[17179581.060000] kjournald starting.  Commit interval 5 seconds
[17179581.204000] usb 1-2: new full speed USB device using ohci_hcd and address 2
[17179597.528000] Linux agpgart interface v0.101 (c) Dave Jones
[17179597.528000] agpgart: Detected Ati IGP330/340/345/350/M chipset
[17179597.540000] agpgart: AGP aperture is 64M @ 0xd4000000
[17179597.584000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179597.588000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179597.628000] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [LNK5] -> GSI 11 (level, low) -> IRQ 11
[17179597.628000] Yenta: CardBus bridge found at 0000:00:0a.0 [103c:002a]
[17179597.628000] Yenta O2: res at 0x94/0xD4: 00/ea
[17179597.628000] Yenta O2: enabling read prefetch/write burst
[17179597.756000] Yenta: ISA IRQ mask 0x00b8, PCI irq 11
[17179597.756000] Socket status: 30000007
[17179598.180000] Real Time Clock Driver v1.12
[17179598.204000] natsemi dp8381x driver, version 1.07+LK1.0.17, Sep 27, 2002
[17179598.204000]   originally by Donald Becker <becker@scyld.com>
[17179598.204000]   [http://www.scyld.com/network/natsemi.html](http://www.scyld.com/network/natsemi.html)
[17179598.204000]   2.4.x kernel port by Jeff Garzik, Tjeerd Mulder
[17179598.204000] **** SET: Misaligned resource pointer: dbf56e02 Type 07 Len 0
[17179598.204000] ACPI: PCI Interrupt Link [LNK1] enabled at IRQ 10
[17179598.204000] ACPI: PCI Interrupt 0000:00:12.0[A] -> Link [LNK1] -> GSI 10 (level, low) -> IRQ 10
[17179598.208000] natsemi eth0: NatSemi DP8381[56] at 0xd0004000 (0000:00:12.0), 00:0b:cd:a7:01:cf, IRQ 10, port TP.
[17179598.240000] ali15x3_smbus 0000:00:11.0: ALI15X3_smb region uninitialized - upgrade BIOS or use force_addr=0xaddr
[17179598.240000] ali15x3_smbus 0000:00:11.0: ALI15X3 not detected, module not inserted.
[17179598.264000] Synaptics Touchpad, model: 1, fw: 5.8, id: 0x2348b3, caps: 0x904713/0x10008
[17179598.300000] input: SynPS/2 Synaptics TouchPad as /class/input/input1
[17179598.356000] parport: PnPBIOS parport detected.
[17179598.356000] parport0: PC-style at 0x378 (0x778), irq 7, dma 0 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[17179598.368000] Floppy drive(s): fd0 is 1.44M
[17179598.424000] FDC 0 is a post-1991 82077
[17179598.536000] input: PC Speaker as /class/input/input2
[17179598.560000] PCI: Enabling device 0000:00:06.0 (0005 -> 0007)
[17179598.560000] **** SET: Misaligned resource pointer: d82fcbc2 Type 07 Len 0
[17179598.560000] ACPI: PCI Interrupt Link [LNK7] enabled at IRQ 5
[17179598.560000] PCI: setting IRQ 5 as level-triggered
[17179598.560000] ACPI: PCI Interrupt 0000:00:06.0[A] -> Link [LNK7] -> GSI 5 (level, low) -> IRQ 5
[17179598.828000] ts: Compaq touchscreen protocol output
[17179598.844000] cs: IO port probe 0x100-0x3af: excluding 0x200-0x207 0x220-0x22f 0x330-0x337 0x388-0x38f
[17179598.844000] cs: IO port probe 0x3e0-0x4ff: clean.
[17179598.848000] cs: IO port probe 0x820-0x8ff: clean.
[17179598.848000] cs: IO port probe 0xc00-0xcf7: clean.
[17179598.848000] cs: IO port probe 0xa00-0xaff: clean.
[17179599.160000] eth0: DSPCFG accepted after 0 usec.
[17179599.160000] eth0: link up.
[17179599.160000] eth0: Setting full-duplex based on negotiated link capability.[17179599.604000] AC'97 1 does not respond - RESET
[17179599.604000] AC'97 1 access is not valid [0xffffffff], removing mixer.
[17179599.604000] ali mixer 1 creating error.
[17179600.064000] lp0: using parport0 (interrupt-driven).
[17179600.152000] Adding 787144k swap on /dev/hda5.  Priority:-1 extents:1 across:787144k
[17179600.344000] NET: Registered protocol family 17
[17179600.352000] EXT3 FS on hda2, internal journal
[17179600.612000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[17179600.612000] md: bitmap version 4.39
[17179601.464000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[17179602.376000] cdrom: open failed.
[17179603.032000] NTFS driver 2.1.25 [Flags: R/O MODULE].
[17179603.120000] NTFS volume version 3.1.
[17179607.696000] ndiswrapper version 1.8 loaded (preempt=yes,smp=no)
[17179607.784000] ndiswrapper: driver cpwgu (Philips,03/08/2006,6.3.4.16) loaded[17179609.020000] NET: Registered protocol family 10
[17179609.020000] lo: Disabled Privacy Extensions
[17179609.020000] IPv6 over IPv4 tunneling driver
[17179610.420000] wlan0: vendor: 'Philips SNU5600 Wireless USB Adapter 11b/g'
[17179610.420000] wlan0: ndiswrapper ethernet device 00:12:bf:2f:ce:5c using driver cpwgu, 0471:1236.F.conf
[17179610.420000] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[17179610.420000] usbcore: registered new driver ndiswrapper
[17179613.440000] Unable to handle kernel NULL pointer dereference at virtual address 00000000
[17179613.440000]  printing eip:
[17179613.440000] 00000000
[17179613.440000] *pde = 00000000
[17179613.440000] Oops: 0000 [#1]
[17179613.440000] PREEMPT
[17179613.440000] Modules linked in: ipv6 ndiswrapper nls_utf8 ntfs dm_mod md_mod af_packet lp joydev tsdev snd_ali5451 snd_ac97_codec snd_ac97_bus pcspkr pcmcia snd_pcm_oss snd_mixer_oss snd_pcm snd_timer floppy parport_pc parport snd soundcore i2c_ali1535 i2c_ali15x3 snd_page_alloc natsemi i2c_core rtc psmouse serio_raw yenta_socket rsrc_nonstatic pcmcia_core shpchp pci_hotplug ati_agp agpgart evdev ext3 jbd ide_generic ohci_hcd usbcore ide_cd cdrom ide_disk generic alim15x3 thermal processor fan capability commoncap vga16fb vgastate fbcon tileblit font bitblit softcursor
[17179613.440000] CPU:    0
[17179613.440000] EIP:    0060:[<00000000>]    Tainted: P      VLI
[17179613.440000] EFLAGS: 00010286   (2.6.15-26-386)
[17179613.440000] EIP is at _stext+0x3feffdc0/0x40
[17179613.440000] eax: c00000bb   ebx: dbbcfa40   ecx: 0001010e   edx: ffff000d
[17179613.440000] esi: d64e2000   edi: 00000246   ebp: d64e3f4c   esp: d64e3f40
[17179613.440000] ds: 007b   es: 007b   ss: 0068
[17179613.440000] Process wrapper_wq (pid: 3554, threadinfo=d64e2000 task=d6b3a550)
[17179613.440000] Stack: d6510000 00000000 00000000 00000000 dcb89c71 d651ccd8 d6510000 dcba81e0
[17179613.440000]        dcba81e4 c012cb0a 00000000 d64e2000 d7caa858 d7caa848 d7caa850 d64e2000
[17179613.440000]        dcb89be0 d64e2000 00000001 00000000 1e19c400 00010000 00000000 00000000
[17179613.440000] Call Trace:
[17179613.440000]  [<dcb89c71>] wrap_work_item_worker+0x91/0xf0 [ndiswrapper]
[17179613.440000]  [<c012cb0a>] worker_thread+0x1ba/0x290
[17179613.440000]  [<dcb89be0>] wrap_work_item_worker+0x0/0xf0 [ndiswrapper]
[17179613.440000]  [<c0118940>] default_wake_function+0x0/0x20
[17179613.440000]  [<c012c950>] worker_thread+0x0/0x290
[17179613.440000]  [<c0130d93>] kthread+0x93/0xa0
[17179613.440000]  [<c0130d00>] kthread+0x0/0xa0
[17179613.440000]  [<c0101385>] kernel_thread_helper+0x5/0x10
[17179613.440000] Code:  Bad EIP value.
[17179613.440000]  <7>eth0: no IPv6 routers present
[17179621.008000] wlan0: no IPv6 routers present
[17179677.284000] ACPI: AC Adapter [ACAD] (on-line)
[17179677.288000] ACPI: Battery Slot [BAT1] (battery present)
[17179677.404000] ACPI: Power Button (FF) [PWRF]
[17179677.404000] ACPI: Power Button (CM) [PWRB]
[17179677.404000] ACPI: Lid Switch [LID]
[17179677.548000] ibm_acpi: IBM ThinkPad ACPI Extras v0.12a
[17179677.548000] ibm_acpi: [http://ibm-acpi.sf.net/](http://ibm-acpi.sf.net/)
[17179677.592000] pcc_acpi: loading...
[17179677.736000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[17179683.932000] [drm] Initialized drm 1.0.1 20051102
[17179684.048000] **** SET: Misaligned resource pointer: d5ddef02 Type 07 Len 0
[17179684.048000] ACPI: PCI Interrupt Link [LNK0] enabled at IRQ 10
[17179684.048000] ACPI: PCI Interrupt 0000:01:05.0[A] -> Link [LNK0] -> GSI 10 (level, low) -> IRQ 10
[17179684.048000] [drm] Initialized radeon 1.24.0 20060225 on minor 0
[17179685.084000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[17179685.084000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[17179685.084000] agpgart: Putting AGP V2 device at 0000:01:05.0 into 4x mode
[17179685.348000] [drm] Setting GART location based on old memory map
[17179685.348000] [drm] writeback test succeeded in 1 usecs
[17179685.580000] ppdev: user-space parallel port driver
[17179686.772000] apm: BIOS not found.
[17179687.956000] serial8250: too much work for irq10
[17179687.972000] serial8250: too much work for irq10
[17179687.972000] serial8250: too much work for irq10
[17179687.972000] serial8250: too much work for irq10
[17179687.988000] serial8250: too much work for irq10
[17179688.004000] serial8250: too much work for irq10
[17179688.020000] serial8250: too much work for irq10
[17179688.056000] serial8250: too much work for irq10
[17179688.064000] serial8250: too much work for irq10
[17179688.064000] serial8250: too much work for irq10
[17179688.064000] serial8250: too much work for irq10
[17179688.068000] serial8250: too much work for irq10
[17179688.068000] serial8250: too much work for irq10
[17179688.068000] serial8250: too much work for irq10
[17179688.068000] serial8250: too much work for irq10
[17179688.072000] serial8250: too much work for irq10
[17179688.072000] serial8250: too much work for irq10
[17179688.072000] serial8250: too much work for irq10
[17179688.072000] serial8250: too much work for irq10
[17179688.072000] serial8250: too much work for irq10
[17179688.076000] serial8250: too much work for irq10
[17179688.076000] serial8250: too much work for irq10
[17179688.076000] serial8250: too much work for irq10
[17179688.080000] serial8250: too much work for irq10
[17179688.080000] serial8250: too much work for irq10
[17179688.080000] serial8250: too much work for irq10
[17179688.080000] serial8250: too much work for irq10
[17179688.084000] serial8250: too much work for irq10
[17179688.084000] serial8250: too much work for irq10
[17179688.084000] serial8250: too much work for irq10
[17179688.084000] serial8250: too much work for irq10
[17179688.088000] serial8250: too much work for irq10
[17179688.088000] serial8250: too much work for irq10
[17179688.088000] serial8250: too much work for irq10
[17179688.088000] serial8250: too much work for irq10
[17179688.088000] serial8250: too much work for irq10
[17179688.092000] serial8250: too much work for irq10
[17179688.092000] serial8250: too much work for irq10
[17179688.092000] serial8250: too much work for irq10
[17179688.104000] serial8250: too much work for irq10
[17179688.136000] serial8250: too much work for irq10
[17179688.140000] serial8250: too much work for irq10
[17179688.144000] serial8250: too much work for irq10
[17179688.156000] serial8250: too much work for irq10
[17179688.172000] serial8250: too much work for irq10
[17179688.176000] serial8250: too much work for irq10
[17179688.180000] serial8250: too much work for irq10
[17179688.188000] serial8250: too much work for irq10
[17179688.204000] serial8250: too much work for irq10
[17179688.232000] serial8250: too much work for irq10
[17179688.232000] serial8250: too much work for irq10
[17179688.232000] serial8250: too much work for irq10
[17179688.232000] serial8250: too much work for irq10
[17179688.236000] serial8250: too much work for irq10
[17179688.236000] serial8250: too much work for irq10
[17179688.236000] serial8250: too much work for irq10
[17179688.236000] serial8250: too much work for irq10
[17179688.240000] serial8250: too much work for irq10
[17179688.240000] serial8250: too much work for irq10
[17179688.244000] serial8250: too much work for irq10
[17179688.244000] serial8250: too much work for irq10
[17179688.256000] serial8250: too much work for irq10
[17179688.272000] serial8250: too much work for irq10
[17179688.280000] serial8250: too much work for irq10
[17179688.280000] serial8250: too much work for irq10
[17179688.288000] serial8250: too much work for irq10
[17179688.336000] serial8250: too much work for irq10
[17179688.348000] serial8250: too much work for irq10
[17179688.348000] serial8250: too much work for irq10
[17179688.356000] serial8250: too much work for irq10
[17179688.360000] serial8250: too much work for irq10
[17179688.360000] serial8250: too much work for irq10
[17179688.360000] serial8250: too much work for irq10
[17179688.360000] serial8250: too much work for irq10
[17179688.364000] serial8250: too much work for irq10
[17179688.364000] serial8250: too much work for irq10
[17179688.364000] serial8250: too much work for irq10
[17179688.364000] serial8250: too much work for irq10
[17179688.368000] serial8250: too much work for irq10
[17179688.368000] serial8250: too much work for irq10
[17179688.368000] serial8250: too much work for irq10
[17179688.368000] serial8250: too much work for irq10
[17179688.372000] serial8250: too much work for irq10
[17179688.372000] serial8250: too much work for irq10
[17179688.372000] serial8250: too much work for irq10
[17179688.372000] serial8250: too much work for irq10
[17179688.372000] serial8250: too much work for irq10
[17179688.376000] serial8250: too much work for irq10
[17179688.376000] serial8250: too much work for irq10
[17179688.376000] serial8250: too much work for irq10
[17179688.376000] serial8250: too much work for irq10
[17179688.380000] serial8250: too much work for irq10
[17179688.380000] serial8250: too much work for irq10
[17179688.380000] serial8250: too much work for irq10
[17179688.380000] serial8250: too much work for irq10
[17179688.384000] serial8250: too much work for irq10
[17179688.384000] serial8250: too much work for irq10
[17179688.384000] serial8250: too much work for irq10
[17179688.388000] serial8250: too much work for irq10
[17179688.388000] serial8250: too much work for irq10
[17179688.388000] serial8250: too much work for irq10
[17179688.388000] serial8250: too much work for irq10
[17179691.392000] ip_tables: (C) 2000-2002 Netfilter core team
[17179691.584000] Netfilter messages via NETLINK v0.30.
[17179691.628000] ip_conntrack version 2.4 (3579 buckets, 28632 max) - 232 bytes per conntrack
[17179695.856000] Bluetooth: Core ver 2.8
[17179695.856000] NET: Registered protocol family 31
[17179695.856000] Bluetooth: HCI device and connection manager initialized
[17179695.856000] Bluetooth: HCI socket layer initialized
[17179695.888000] Bluetooth: L2CAP ver 2.8
[17179695.888000] Bluetooth: L2CAP socket layer initialized
[17179695.940000] Bluetooth: RFCOMM socket layer initialized
[17179695.940000] Bluetooth: RFCOMM TTY layer initialized
[17179695.940000] Bluetooth: RFCOMM ver 1.7
[17179988.368000] ndiswrapper (iw_get_range:1415): getting bit rates failed: C0000001


That is all, hope you can help me.

---

### Post by bensexson on 2006-08-11
It looks like ndiswrapper is not working with your adapter.      [17179988.368000] ndiswrapper (iw_get_range:1415): getting bit rates failed: C0000001

You might try this: sudo iwconfig wlan0 rate 11M
I would search here [http://ndiswrapper.sourceforge.net/](http://ndiswrapper.sourceforge.net/)

---

### Post by Lasborg on 2006-08-11
the command you sugested returned this:e 

SET failed on device wlan0 ; Unknown error 524

but i will try and post on the ndiswrapper page.

---

### Post by Lasborg on 2006-08-12
Hmm couldn't really find anyting on the ndiswrapper page.

Hope someone else can help me.

---

### Post by Lasborg on 2006-08-17
I compiled and installed ndiswrapper 1.23 and now the network-setings works fine. I installed Network-Manager-Gnome to use WPA encryption. In the network manager I can see my wireless network, ant when I try to access, it asks for the WPA key. So far so good. But the network manager icon still says that it is waiting for the network key.

Maybe I need do install the latest network manager?

---

