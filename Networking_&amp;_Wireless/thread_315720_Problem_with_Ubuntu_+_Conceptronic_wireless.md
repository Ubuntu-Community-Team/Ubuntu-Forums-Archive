---
title: "Problem with Ubuntu + Conceptronic wireless"
date: 2006-12-09
forum: Networking &amp; Wireless
---

### Post by zumbe on 2006-12-09
Hello everybody. I'm starting with LINUX (Ubuntu Edgy), and I'm having lots of problems.

The main problem is that I can't use internet. I don't really know why. I use [this model]("http://www.conceptronic.net/site/desktopdefault.aspx?tabindex=0&tabid=200&Cat=10&grp=1010&ar=350&Prod_ID=290&Prod=C54Ri") of Conceptronic, but I need the drivers.

Please, I'm in this situation fos 6 months, and I really need internet conection.](*,) 

Thanks 4 reading.

---

### Post by FrodoB on 2006-12-09
With the card in the machine type lspci -v from a terminal prompt and publish the data.

---

### Post by FrodoB on 2006-12-09
And give us the exact model and version of your device.

Also please provide the output of iwconfig and dmesg.

---

### Post by zumbe on 2006-12-09
Here's the output of lspci -v :

[INDENT]00:00.0 Host bridge: VIA Technologies, Inc. K8T800Pro Host Bridge
        Subsystem: VIA Technologies, Inc. K8T800Pro Host Bridge
        Flags: bus master, 66MHz, medium devsel, latency 8
        Memory at f0000000 (32-bit, prefetchable) [size=64M]
        Capabilities: <access denied>

00:00.1 Host bridge: VIA Technologies, Inc. K8T800Pro Host Bridge
        Flags: bus master, medium devsel, latency 0

00:00.2 Host bridge: VIA Technologies, Inc. K8T800Pro Host Bridge
        Flags: bus master, medium devsel, latency 0

00:00.3 Host bridge: VIA Technologies, Inc. K8T800Pro Host Bridge
        Flags: bus master, medium devsel, latency 0

00:00.4 Host bridge: VIA Technologies, Inc. K8T800Pro Host Bridge
        Flags: bus master, medium devsel, latency 0

00:00.7 Host bridge: VIA Technologies, Inc. K8T800Pro Host Bridge
        Flags: bus master, medium devsel, latency 0

00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South] (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 0000c000-0000cfff
        Memory behind bridge: f4000000-f5ffffff
        Prefetchable memory behind bridge: e0000000-efffffff
        Capabilities: <access denied>

00:0b.0 Network controller: RaLink Unknown device 0302
        Subsystem: Unknown device 1948:3c24
        Flags: bus master, slow devsel, latency 32, IRQ 185
        Memory at f6000000 (32-bit, non-prefetchable) [size=32K]
        Capabilities: <access denied>

00:0f.0 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06) (prog-if 8a [Master SecP PriP])
        Subsystem: Giga-byte Technology GA-7VAX Mainboard
        Flags: bus master, medium devsel, latency 32, IRQ 169
        I/O ports at d000 [size=16]
        Capabilities: <access denied>

00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) (prog-if 00 [UHCI])
        Subsystem: Giga-byte Technology GA-7VAX Mainboard
        Flags: bus master, medium devsel, latency 32, IRQ 177
        I/O ports at d400 [size=32]
        Capabilities: <access denied>

00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) (prog-if 00 [UHCI])
        Subsystem: Giga-byte Technology GA-7VAX Mainboard
        Flags: bus master, medium devsel, latency 32, IRQ 177
        I/O ports at d800 [size=32]
        Capabilities: <access denied>

00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) (prog-if 00 [UHCI])
        Subsystem: Giga-byte Technology GA-7VAX Mainboard
        Flags: bus master, medium devsel, latency 32, IRQ 177
        I/O ports at dc00 [size=32]
        Capabilities: <access denied>

00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) (prog-if 00 [UHCI])
        Subsystem: Giga-byte Technology GA-7VAX Mainboard
        Flags: bus master, medium devsel, latency 32, IRQ 177
        I/O ports at e000 [size=32]
        Capabilities: <access denied>

00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86) (prog-if 20 [EHCI])
        Subsystem: Giga-byte Technology GA-7VAX Mainboard
        Flags: bus master, medium devsel, latency 32, IRQ 177
        Memory at f6008000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
        Subsystem: Giga-byte Technology GA-7VT600 Motherboard
        Flags: bus master, stepping, medium devsel, latency 0
        Capabilities: <access denied>

00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
        Subsystem: Giga-byte Technology GA-7VAX Onboard Audio (Realtek ALC650)
        Flags: medium devsel, IRQ 201
        I/O ports at e400 [size=256]
        Capabilities: <access denied>

00:13.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
        Subsystem: Giga-byte Technology GA-7VM400M/7VT600 Motherboard
        Flags: bus master, medium devsel, latency 64, IRQ 193
        I/O ports at e800 [size=256]
        Memory at f6009000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
        Flags: fast devsel
        Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
        Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
        Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
        Flags: fast devsel

01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (rev 01) (prog-if 00 [VGA])
        Subsystem: ATI Technologies Inc RV280 [Radeon 9200 PRO]
        Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 209
        Memory at e0000000 (32-bit, prefetchable) [size=128M]
        I/O ports at c000 [size=256]
        Memory at f5000000 (32-bit, non-prefetchable) [size=64K]
        [virtual] Expansion ROM at f4000000 [disabled] [size=128K]
        Capabilities: <access denied>

01:00.1 Display controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (Secondary) (rev 01)
        Subsystem: ATI Technologies Inc Unknown device 5961
        Flags: bus master, 66MHz, medium devsel, latency 32
        Memory at e8000000 (32-bit, prefetchable) [size=128M]
        Memory at f5010000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>
[/INDENT]

Now I'll try the other two...

---

### Post by zumbe on 2006-12-09
iwconfig:
[INDENT]lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  IEEE 802.11g  Frequency:2.412 GHz  
          RTS thr:off   Fragment thr=2346 B   
          
wlan0     IEEE 802.11g  ESSID:"TI-AR7WRD"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          RTS thr:off   Fragment thr=2346 B   
          
sit0      no wireless extensions.[/INDENT]

dmesg:
[INDENT][17179569.184000] Linux version 2.6.17-10-generic (root@vernadsky) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Fri Oct 13 18:45:35 UTC 2006 (Ubuntu 2.6.17-10.33-generic)
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[17179569.184000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000001fff0000 (usable)
[17179569.184000]  BIOS-e820: 000000001fff0000 - 000000001fff3000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 000000001fff3000 - 0000000020000000 (ACPI data)
[17179569.184000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[17179569.184000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 511MB LOWMEM available.
[17179569.184000] found SMP MP-table at 000f5130
[17179569.184000] On node 0 totalpages: 131056
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   Normal zone: 126960 pages, LIFO batch:31
[17179569.184000] DMI 2.3 present.
[17179569.184000] ACPI: RSDP (v000 VIAK8                                 ) @ 0x000f6a90
[17179569.184000] ACPI: RSDT (v001 VIAK8  AWRDACPI 0x42302e31 AWRD 0x01010101) @ 0x1fff3000
[17179569.184000] ACPI: FADT (v001 VIAK8  AWRDACPI 0x42302e31 AWRD 0x01010101) @ 0x1fff3040
[17179569.184000] ACPI: MADT (v001 VIAK8  AWRDACPI 0x42302e31 AWRD 0x01010101) @ 0x1fff77c0
[17179569.184000] ACPI: DSDT (v001 VIAK8  AWRDACPI 0x00001000 MSFT 0x0100000c) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x4008
[17179569.184000] ACPI: Local APIC address 0xfee00000
[17179569.184000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[17179569.184000] Processor #0 15:12 APIC version 16
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
[17179569.184000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[17179569.184000] IOAPIC[0]: apic_id 2, version 3, address 0xfec00000, GSI 0-23
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[17179569.184000] ACPI: IRQ0 used by override.
[17179569.184000] ACPI: IRQ2 used by override.
[17179569.184000] ACPI: IRQ9 used by override.
[17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[17179569.184000] Using ACPI (MADT) for SMP configuration information
[17179569.184000] Allocating PCI resources starting at 30000000 (gap: 20000000:dec00000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hda2 ro quiet splash
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
[17179569.184000] Enabling fast FPU save and restore... done.
[17179569.184000] Enabling unmasked SIMD FPU exception support... done.
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[17179569.184000] Detected 1608.439 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179573.248000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179573.248000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179573.256000] Memory: 509800k/524224k available (1910k kernel code, 13836k reserved, 1070k data, 308k init, 0k highmem)
[17179573.256000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179573.336000] Calibrating delay using timer specific routine.. 3220.70 BogoMIPS (lpj=6441409)
[17179573.336000] Security Framework v1.0.0 initialized
[17179573.336000] SELinux:  Disabled at boot.
[17179573.336000] Mount-cache hash table entries: 512
[17179573.336000] CPU: After generic identify, caps: 078bfbff e3d3fbff 00000000 00000000 00000001 00000000 00000001
[17179573.336000] CPU: After vendor identify, caps: 078bfbff e3d3fbff 00000000 00000000 00000001 00000000 00000001
[17179573.336000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[17179573.336000] CPU: L2 Cache: 128K (64 bytes/line)
[17179573.336000] CPU: After all inits, caps: 078bfbff e3d3fbff 00000000 00000410 00000001 00000000 00000001
[17179573.336000] Checking 'hlt' instruction... OK.
[17179573.352000] SMP alternatives: switching to UP code
[17179573.352000] Freeing SMP alternatives: 16k freed
[17179573.352000] checking if image is initramfs... it is
[17179573.924000] Freeing initrd memory: 5563k freed
[17179573.924000] ACPI: Core revision 20060707
[17179573.928000] ACPI: Looking for DSDT ... not found!
[17179573.932000] CPU0: AMD Sempron(tm) Processor 2600+ stepping 02
[17179573.932000] Total of 1 processors activated (3220.70 BogoMIPS).
[17179573.932000] ENABLING IO-APIC IRQs
[17179573.932000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=0 pin2=0
[17179574.076000] Brought up 1 CPUs
[17179574.076000] migration_cost=0
[17179574.076000] NET: Registered protocol family 16
[17179574.076000] EISA bus registered
[17179574.076000] ACPI: bus type pci registered
[17179574.080000] PCI: PCI BIOS revision 2.10 entry at 0xfb320, last bus=1
[17179574.080000] PCI: Using configuration type 1
[17179574.080000] Setting up standard PCI resources
[17179574.088000] ACPI: Interpreter enabled
[17179574.088000] ACPI: Using IOAPIC for interrupt routing
[17179574.088000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179574.088000] PCI: Probing PCI hardware (bus 00)
[17179574.092000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:0f.0
[17179574.092000] PCI: Quirk-MSI-K8T Soundcard On
[17179574.092000] PCI: MSI-K8T soundcard on
[17179574.092000] Boot video device is 0000:01:00.0
[17179574.092000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179574.140000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 7 10 11 12) *5
[17179574.140000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 6 7 10 *11 12)
[17179574.140000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 6 7 10 *11 12)
[17179574.140000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 6 7 *10 11 12)
[17179574.140000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[17179574.140000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[17179574.140000] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[17179574.140000] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[17179574.140000] ACPI: PCI Interrupt Link [ALKA] (IRQs 20) *0, disabled.
[17179574.140000] ACPI: PCI Interrupt Link [ALKB] (IRQs 21) *0, disabled.
[17179574.140000] ACPI: PCI Interrupt Link [ALKC] (IRQs 22) *0, disabled.
[17179574.140000] ACPI: PCI Interrupt Link [ALKD] (IRQs 23) *0, disabled.
[17179574.144000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179574.144000] pnp: PnP ACPI init
[17179574.148000] pnp: PnP ACPI: found 13 devices
[17179574.148000] PnPBIOS: Disabled by ACPI PNP
[17179574.148000] PCI: Using ACPI for IRQ routing
[17179574.148000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179574.180000] pnp: 00:02: ioport range 0x4000-0x407f could not be reserved
[17179574.180000] pnp: 00:02: ioport range 0x40f0-0x40ff could not be reserved
[17179574.180000] pnp: 00:02: ioport range 0x5000-0x500f has been reserved
[17179574.180000] PCI: Bridge: 0000:00:01.0
[17179574.180000]   IO window: c000-cfff
[17179574.180000]   MEM window: f4000000-f5ffffff
[17179574.180000]   PREFETCH window: e0000000-efffffff
[17179574.180000] PCI: Setting latency timer of device 0000:00:01.0 to 64
[17179574.180000] NET: Registered protocol family 2
[17179574.212000] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[17179574.212000] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[17179574.212000] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[17179574.212000] TCP: Hash tables configured (established 16384 bind 8192)
[17179574.212000] TCP reno registered
[17179574.212000] audit: initializing netlink socket (disabled)
[17179574.212000] audit(1165707035.212:1): initialized
[17179574.212000] VFS: Disk quotas dquot_6.5.1
[17179574.212000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179574.212000] Initializing Cryptographic API
[17179574.212000] io scheduler noop registered
[17179574.212000] io scheduler anticipatory registered
[17179574.212000] io scheduler deadline registered
[17179574.212000] io scheduler cfq registered (default)
[17179574.212000] isapnp: Scanning for PnP cards...
[17179574.564000] isapnp: No Plug & Play device found
[17179574.596000] Real Time Clock Driver v1.12ac
[17179574.596000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[17179574.596000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179574.596000] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[17179574.596000] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179574.596000] 00:0a: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[17179574.596000] mice: PS/2 mouse device common for all mice
[17179574.596000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179574.596000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179574.596000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179574.600000] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[17179574.600000] PNP: PS/2 controller doesn't have AUX irq; using default 12
[17179574.604000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179574.604000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179574.604000] EISA: Probing bus 0 at eisa.0
[17179574.604000] Cannot allocate resource for EISA slot 4
[17179574.604000] Cannot allocate resource for EISA slot 5
[17179574.604000] EISA: Detected 0 cards.
[17179574.604000] TCP bic registered
[17179574.604000] NET: Registered protocol family 1
[17179574.604000] NET: Registered protocol family 8
[17179574.604000] NET: Registered protocol family 20
[17179574.604000] Using IPI No-Shortcut mode
[17179574.604000] ACPI: (supports S0 S1 S4 S5)
[17179574.604000] Freeing unused kernel memory: 308k freed
[17179575.036000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179575.740000] Capability LSM initialized
[17179576.272000] VP_IDE: IDE controller at PCI slot 0000:00:0f.0
[17179576.272000] ACPI: PCI Interrupt Link [ALKA] BIOS reported IRQ 0, using IRQ 20
[17179576.272000] ACPI: PCI Interrupt Link [ALKA] enabled at IRQ 20
[17179576.272000] ACPI: PCI Interrupt 0000:00:0f.0[A] -> Link [ALKA] -> GSI 20 (level, low) -> IRQ 169
[17179576.272000] PCI: Via IRQ fixup for 0000:00:0f.0, from 255 to 9
[17179576.272000] VP_IDE: chipset revision 6
[17179576.272000] VP_IDE: not 100% native mode: will probe irqs later
[17179576.272000] VP_IDE: VIA vt8237 (rev 00) IDE UDMA133 controller on pci0000:00:0f.0
[17179576.272000]     ide0: BM-DMA at 0xd000-0xd007, BIOS settings: hda:DMA, hdb:DMA
[17179576.272000]     ide1: BM-DMA at 0xd008-0xd00f, BIOS settings: hdc:DMA, hdd:pio
[17179576.272000] Probing IDE interface ide0...
[17179576.688000] hda: Maxtor 6L080L0, ATA DISK drive
[17179577.136000] hdb: HL-DT-STDVD-ROM GDR8164B, ATAPI CD/DVD-ROM drive
[17179577.196000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179577.216000] Probing IDE interface ide1...
[17179578.084000] hdc: HL-DT-ST DVDRAM GSA-H10A, ATAPI CD/DVD-ROM drive
[17179578.420000] ide1 at 0x170-0x177,0x376 on irq 15
[17179578.428000] hda: max request size: 128KiB
[17179578.440000] hda: Host Protected Area detected.
[17179578.440000]       current capacity is 160084415 sectors (81963 MB)
[17179578.440000]       native  capacity is 160086528 sectors (81964 MB)
[17179578.464000] hda: Host Protected Area disabled.
[17179578.464000] hda: 160086528 sectors (81964 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(133)
[17179578.464000] hda: cache flushes supported
[17179578.464000]  hda: hda1 hda2 hda3 < hda5 >
[17179578.512000] hdb: ATAPI 52X DVD-ROM drive, 256kB Cache, UDMA(33)
[17179578.512000] Uniform CD-ROM driver Revision: 3.20
[17179578.540000] hdc: ATAPI 48X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(33)
[17179578.820000] usbcore: registered new driver usbfs
[17179578.820000] usbcore: registered new driver hub
[17179578.820000] USB Universal Host Controller Interface driver v3.0
[17179578.820000] ACPI: PCI Interrupt Link [ALKB] BIOS reported IRQ 0, using IRQ 21
[17179578.820000] ACPI: PCI Interrupt Link [ALKB] enabled at IRQ 21
[17179578.820000] ACPI: PCI Interrupt 0000:00:10.0[A] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 177
[17179578.820000] PCI: Via IRQ fixup for 0000:00:10.0, from 5 to 1
[17179578.820000] uhci_hcd 0000:00:10.0: UHCI Host Controller
[17179578.820000] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
[17179578.820000] uhci_hcd 0000:00:10.0: irq 177, io base 0x0000d400
[17179578.820000] usb usb1: configuration #1 chosen from 1 choice
[17179578.820000] hub 1-0:1.0: USB hub found
[17179578.820000] hub 1-0:1.0: 2 ports detected
[17179578.924000] ACPI: PCI Interrupt 0000:00:10.1[A] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 177
[17179578.924000] PCI: Via IRQ fixup for 0000:00:10.1, from 5 to 1
[17179578.924000] uhci_hcd 0000:00:10.1: UHCI Host Controller
[17179578.924000] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
[17179578.924000] uhci_hcd 0000:00:10.1: irq 177, io base 0x0000d800
[17179578.924000] usb usb2: configuration #1 chosen from 1 choice
[17179578.924000] hub 2-0:1.0: USB hub found
[17179578.924000] hub 2-0:1.0: 2 ports detected
[17179579.028000] ACPI: PCI Interrupt 0000:00:10.2[B] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 177
[17179579.028000] PCI: Via IRQ fixup for 0000:00:10.2, from 11 to 1
[17179579.028000] uhci_hcd 0000:00:10.2: UHCI Host Controller
[17179579.028000] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
[17179579.028000] uhci_hcd 0000:00:10.2: irq 177, io base 0x0000dc00
[17179579.028000] usb usb3: configuration #1 chosen from 1 choice
[17179579.028000] hub 3-0:1.0: USB hub found
[17179579.028000] hub 3-0:1.0: 2 ports detected
[17179579.132000] ACPI: PCI Interrupt 0000:00:10.3[B] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 177
[17179579.132000] PCI: Via IRQ fixup for 0000:00:10.3, from 11 to 1
[17179579.132000] uhci_hcd 0000:00:10.3: UHCI Host Controller
[17179579.132000] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
[17179579.132000] uhci_hcd 0000:00:10.3: irq 177, io base 0x0000e000
[17179579.132000] usb usb4: configuration #1 chosen from 1 choice
[17179579.132000] hub 4-0:1.0: USB hub found
[17179579.132000] hub 4-0:1.0: 2 ports detected
[17179579.264000] ACPI: PCI Interrupt 0000:00:10.4[C] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 177
[17179579.264000] PCI: Via IRQ fixup for 0000:00:10.4, from 11 to 1
[17179579.264000] ehci_hcd 0000:00:10.4: EHCI Host Controller
[17179579.264000] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 5
[17179579.264000] ehci_hcd 0000:00:10.4: irq 177, io mem 0xf6008000
[17179579.264000] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179579.264000] usb usb5: configuration #1 chosen from 1 choice
[17179579.268000] hub 5-0:1.0: USB hub found
[17179579.268000] hub 5-0:1.0: 8 ports detected
[17179579.444000] Attempting manual resume
[17179579.488000] kjournald starting.  Commit interval 5 seconds
[17179579.488000] EXT3-fs: mounted filesystem with ordered data mode.
[17179580.372000] usb 5-6: new high speed USB device using ehci_hcd and address 3
[17179580.508000] usb 5-6: configuration #1 chosen from 1 choice
[17179580.748000] usb 2-2: new low speed USB device using uhci_hcd and address 2
[17179580.924000] usb 2-2: configuration #1 chosen from 1 choice
[17179587.792000] input: PC Speaker as /class/input/input1
[17179588.152000] Floppy drive(s): fd0 is 1.44M
[17179588.172000] FDC 0 is a post-1991 82077
[17179588.180000] Linux agpgart interface v0.101 (c) Dave Jones
[17179588.180000] agpgart: Detected AGP bridge 0
[17179588.184000] agpgart: AGP aperture is 64M @ 0xf0000000
[17179588.240000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179588.252000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179588.704000] 8139too Fast Ethernet driver 0.9.27
[17179588.704000] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 18 (level, low) -> IRQ 185
[17179588.704000] eth0: RealTek RTL8139 at 0xe0926000, 00:14:85:75:55:20, IRQ 185
[17179588.704000] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[17179588.712000] 8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
[17179588.804000] Loading module: rt61pci - CVS (N/A) by [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com).
[17179588.804000] ACPI: PCI Interrupt 0000:00:0b.0[A] -> GSI 19 (level, low) -> IRQ 193
[17179588.948000] atkbd.c: Spurious ACK on isa0060/serio0. Some program, like XFree86, might be trying access hardware directly.
[17179589.000000] wmaster0: Selected rate control algorithm 'simple'
[17179589.304000] usbcore: registered new driver hiddev
[17179589.320000] input: Microsoft Basic Optical Mouse as /class/input/input2
[17179589.320000] input: USB HID v1.10 Mouse [Microsoft Basic Optical Mouse] on usb-0000:00:10.1-2
[17179589.320000] usbcore: registered new driver usbhid
[17179589.320000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[17179589.328000] ACPI: PCI Interrupt Link [ALKC] BIOS reported IRQ 0, using IRQ 22
[17179589.328000] ACPI: PCI Interrupt Link [ALKC] enabled at IRQ 22
[17179589.328000] ACPI: PCI Interrupt 0000:00:11.5[C] -> Link [ALKC] -> GSI 22 (level, low) -> IRQ 201
[17179589.328000] PCI: Via IRQ fixup for 0000:00:11.5, from 11 to 9
[17179589.328000] PCI: Setting latency timer of device 0000:00:11.5 to 64
[17179589.520000] parport: PnPBIOS parport detected.
[17179589.520000] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[17179589.588000] usbcore: registered new driver libusual
[17179589.628000] SCSI subsystem initialized
[17179589.632000] Initializing USB Mass Storage driver...
[17179589.632000] scsi0 : SCSI emulation for USB Mass Storage devices
[17179589.632000] usbcore: registered new driver usb-storage
[17179589.632000] USB Mass Storage support registered.
[17179589.632000] usb-storage: device found at 3
[17179589.632000] usb-storage: waiting for device to settle before scanning
[17179589.656000] ts: Compaq touchscreen protocol output
[17179590.048000] lp0: using parport0 (interrupt-driven).
[17179590.076000] Adding 1510068k swap on /dev/disk/by-uuid/8391eaf3-edaf-4b2a-b11a-92c852577f2f.  Priority:-1 extents:1 across:1510068k
[17179590.172000] EXT3 FS on hda2, internal journal
[17179590.460000] NTFS driver 2.1.27 [Flags: R/O MODULE].
[17179590.508000] NTFS volume version 3.1.
[17179590.576000] NET: Registered protocol family 17
[17179594.636000] usb-storage: device scan complete
[17179594.636000]   Vendor:           Model: USB DISK 2.0      Rev: PMAP
[17179594.636000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17179594.668000] SCSI device sda: 2015232 512-byte hdwr sectors (1032 MB)
[17179594.668000] sda: Write Protect is off
[17179594.668000] sda: Mode Sense: 23 00 00 00
[17179594.668000] sda: assuming drive cache: write through
[17179594.672000] SCSI device sda: 2015232 512-byte hdwr sectors (1032 MB)
[17179594.680000] sda: Write Protect is off
[17179594.680000] sda: Mode Sense: 23 00 00 00
[17179594.680000] sda: assuming drive cache: write through
[17179594.680000]  sda: sda1
[17179594.692000] sd 0:0:0:0: Attached scsi removable disk sda
[17179594.724000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[17179595.068000] ACPI: Power Button (FF) [PWRF]
[17179595.068000] ACPI: Power Button (CM) [PWRB]
[17179595.216000] ibm_acpi: ec object not found
[17179595.284000] pcc_acpi: loading...
[17179595.612000] powernow-k8: Power state transitions not supported
[17179595.640000] ACPI Exception (acpi_processor-0240): AE_NOT_FOUND, Evaluating _PSS [20060707]
[17179597.760000] [drm] Initialized drm 1.0.1 20051102
[17179597.764000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 209
[17179597.768000] [drm] Initialized radeon 1.25.0 20060524 on minor 0
[17179598.280000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[17179598.280000] apm: overridden by ACPI.
[17179599.852000] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[17179599.852000] agpgart: Putting AGP V3 device at 0000:00:00.0 into 4x mode
[17179599.852000] agpgart: Putting AGP V3 device at 0000:01:00.0 into 4x mode
[17179600.164000] [drm] Setting GART location based on new memory map
[17179600.164000] [drm] Loading R200 Microcode
[17179600.164000] [drm] writeback test succeeded in 1 usecs
[17179603.380000] Bluetooth: Core ver 2.8
[17179603.380000] NET: Registered protocol family 31
[17179603.380000] Bluetooth: HCI device and connection manager initialized
[17179603.380000] Bluetooth: HCI socket layer initialized
[17179603.396000] Bluetooth: L2CAP ver 2.8
[17179603.396000] Bluetooth: L2CAP socket layer initialized
[17179603.424000] Bluetooth: RFCOMM socket layer initialized
[17179603.424000] Bluetooth: RFCOMM TTY layer initialized
[17179603.424000] Bluetooth: RFCOMM ver 1.7
[17179612.524000] NET: Registered protocol family 10
[17179612.524000] lo: Disabled Privacy Extensions
[17179612.524000] IPv6 over IPv4 tunneling driver
[17179616.688000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[17179623.268000] wlan0: no IPv6 routers present[/INDENT]

I hope you can help me.

---

### Post by FrodoB on 2006-12-09
Are you using an Access Point Router with WEP?

---

### Post by zumbe on 2006-12-09
Yes, I think so.

---

### Post by FrodoB on 2006-12-09
Using the Text Editor (gedit) we need to modify the interfaces file to get the device started correctly. Open a command line terminal and:

user@ubuntu:~$ sudo gedit /etc/network/interfaces 

Dynamic Address Assignment using DHCP: Add this data at the end of the file for a DHCP setup: (Choose one key type, either hex or ASCII, but not both, uncomment one, and fill in your key.)


iface wlan0 inet dhcp
pre-up ifconfig wlan0 up
wireless-essid MY_ESSID
wireless-key XXXXXXXXXXXXXXXXXXXXXXXXXX       # This line for hexidecimal keys
# wireless-key s:XXXXXXXXXXXXX                # This line for ASCII (string) keys
auto wlan0




You can hopefully see your access point with the following command from a terminal window:

user@ubuntu:~$ iwlist wlan0 scanning



You can now control the device with ifup and ifdown:

user@ubuntu:~$ sudo ifdown wlan0

user@ubuntu:~$ sudo ifup wlan0

---

### Post by zumbe on 2006-12-09
One question before triyn... 

with the password, do I choose now ASCII or Hex? or is it something i'm suposed to know?

---

### Post by FrodoB on 2006-12-09
Is is usually easier to use HEX. But if your access point only takes ASCII there is a solution.


Go to this WEP key generator and make some 128bit keys and it will give you the same key in both formats.  Save these in a text file and paste them into your access point and your computer workstations:

[http://www.andrewscompanies.com/tools/wep.asp](http://www.andrewscompanies.com/tools/wep.asp)

Examples:

ASCII:
a*ozW8Ex3iDq_

HEX:
612a6f7a57384578336944715f

This is the exact same key in the two formats.

---

### Post by zumbe on 2006-12-09
Hi, I've tried it, but gives me an error:

/etc/network/interfaces:21: duplicate interface
ifdown: couldn't read interfaces file "/etc/network/interfaces"

hmmmm...:-k

---

### Post by FrodoB on 2006-12-09
This means that you have the same interface called out twice in your interfaces file and the duplicated interface is on line 21. Duplicates are not allowed, so your system does not know what you want it to do.

If in doubt publish the contents of /etc/network/interfaces

---

### Post by zumbe on 2006-12-09
Hi, I've deleted the lines that were repeated. But now gives me another error:

ifdown: interface wlan0 not configured

---

### Post by FrodoB on 2006-12-09
You really need to publish what you have in /etc/network/interfaces

---

### Post by zumbe on 2006-12-09
Fine, sorry.

[INDENT]auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
pre-up ifconfig wlan0 up
wireless-essid TI-AR7WRD
wireless-key xxxxxxxxxxxxxx #the pw, not just x's[/INDENT]

---

### Post by FrodoB on 2006-12-09
That looks pretty good.

Try

sudo ifup wlan0

What does it say?

---

### Post by zumbe on 2006-12-09
says:

ifup: failed to open statefile /var/run/network/ifstate: Permission denied

---

### Post by FrodoB on 2006-12-09
you forgot to preface your command with sudo

sudo ifup wlan0

---

### Post by zumbe on 2006-12-09
I'm sorry, i've done it now with sudo before:

SIOCSIFFLAGS: Input/output error
Failed to bring up wlan0.

---

### Post by FrodoB on 2006-12-09
OK, I see what is going on here. You are going to have to compile and install the rt61 drivers from Ralink.

You will need to install the essential build files to compile the driver: 
 user@ubuntu:~$ sudo apt-get update  
user@ubuntu:~$ sudo apt-get install build-essential
Install the correct headers for your version of Ubuntu: (don't worry if it tells you that yours are up to date.) 
 user@ubuntu:~$ sudo apt-get install linux-headers-`uname -r`  
user@ubuntu:~$ sudo ln -s /usr/src/linux-headers-`uname -r` /lib/modules/`uname -r`/build

Here is the driver:

[http://www.ralinktech.com/drivers/Linux/RT61_Linux_STA_Drv1.1.0.0.tar.gz](http://www.ralinktech.com/drivers/Linux/RT61_Linux_STA_Drv1.1.0.0.tar.gz)

Download it, copy it to your home directory and untar it and read the README file inside it to see who to compile it.

Also search the forum for better instructions on how to do this. 

I have to leave for a while so good luck until tomorrow.

---

### Post by zumbe on 2006-12-09
I'm leaving too, so thanks a lot, really.

---

### Post by FrodoB on 2006-12-09
Here is a link to someone's blog, who has done this:

[http://translate.google.com/translate?hl=en&sl=de&u=http://micha.monsteradmin.de/&sa=X&oi=translate&resnum=2&ct=result&prev=/search%3Fq%3D1948:3c24%2BLinux%26hl%3Den%26lr%3D%26sa%3DG](http://translate.google.com/translate?hl=en&sl=de&u=http://micha.monsteradmin.de/&sa=X&oi=translate&resnum=2&ct=result&prev=/search%3Fq%3D1948:3c24%2BLinux%26hl%3Den%26lr%3D%26sa%3DG)

---

### Post by ultranoize on 2006-12-10
Take a look at this [http://ubuntuforums.org/showthread.php?t=296822](http://ubuntuforums.org/showthread.php?t=296822)

hope it works.

---

