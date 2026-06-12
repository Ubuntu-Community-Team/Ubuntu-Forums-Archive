---
title: "PCLOS-gnome: Net_Applet only connects to unsecure networks, not encryptes ones"
date: 2008-02-23
forum: Networking &amp; Wireless
---

### Post by SkittleLinux18 on 2008-02-23
The title pretty much sums up my whole problem. I can connect to unsecured networks, but not encrypted ones. This is what I have tried so far:

1) downloading another network manager; same results: could connect to unsecure networks, but not encrypted ones.

2) using WiFi Radar to create and edit profiles; same results as above.

3) gedit /etc/network/interfaces; but the request was rejected because the authentication protocols are not supported. (?)

4) updating drakxtools in synaptic package manager.

5) researching other similar problems on linuxforums.com and ubuntuforums.com

6) terminal command: "lspci" gives me this:
> 
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 81)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller (rev 80)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 80)
00:14.6 Modem: ATI Technologies Inc SB400 AC'97 Modem Controller (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS485 [Radeon Xpress 1100 IGP]
02:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:04.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)

7) Terminal command: "iwconfig" just tells me that the bash: command not found

8) Terminal command: "dmesg" gives me this:

> Linux version 2.6.22.15.tex1 (root@localhost) (gcc version 4.1.1 20060724 (prerelease) (4.1.1-4pclos2007)) #1 SMP Sat Dec 15 13:15:05 CST 2007
BIOS-provided physical RAM map:
BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
BIOS-e820: 0000000000100000 - 0000000027fd0000 (usable)
BIOS-e820: 0000000027fd0000 - 0000000027fde000 (ACPI data)
BIOS-e820: 0000000027fde000 - 0000000028000000 (ACPI NVS)
BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
Malformed early option 'acpi'
0MB HIGHMEM available.
639MB LOWMEM available.
found SMP MP-table at 000ff780
Entering add_active_range(0, 0, 163792) 0 entries of 256 used
Zone PFN ranges:
DMA 0 -> 4096
Normal 4096 -> 163792
HighMem 163792 -> 163792
early_node_map[1] active PFN ranges
0: 0 -> 163792
On node 0 totalpages: 163792
DMA zone: 32 pages used for memmap
DMA zone: 0 pages reserved
DMA zone: 4064 pages, LIFO batch:0
Normal zone: 1247 pages used for memmap
Normal zone: 158449 pages, LIFO batch:31
HighMem zone: 0 pages used for memmap
DMI 2.3 present.
ACPI: RSDP 000F9730, 0014 (r0 ACPIAM)
ACPI: RSDT 27FD0000, 0034 (r1 A M I OEMRSDT 10000528 MSFT 97)
ACPI: FACP 27FD0200, 0084 (r2 A M I OEMFACP 10000528 MSFT 97)
ACPI: DSDT 27FD0430, 364F (r1 1ABZQ 1ABZQB43 B43 INTL 2002026)
ACPI: FACS 27FDE000, 0040
ACPI: APIC 27FD0390, 0054 (r1 A M I OEMAPIC 10000528 MSFT 97)
ACPI: MCFG 27FD03F0, 003C (r1 A M I OEMMCFG 10000528 MSFT 97)
ACPI: OEMB 27FDE040, 0047 (r1 A M I AMI_OEM 10000528 MSFT 97)
ATI board detected. Disabling timer routing over 8254.
ACPI: PM-Timer IO Port: 0x808
ACPI: Local APIC address 0xfee00000
ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Processor #0 15:4 APIC version 16
ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
IOAPIC[0]: apic_id 1, version 33, address 0xfec00000, GSI 0-23
ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 21 low level)
ACPI: IRQ0 used by override.
ACPI: IRQ2 used by override.
Enabling APIC mode: Flat. Using 1 I/O APICs
Using ACPI (MADT) for SMP configuration information
Allocating PCI resources starting at 30000000 (gap: 28000000:d7f80000)
swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000e4000
swsusp: Registered nosave memory region: 00000000000e4000 - 0000000000100000
Built 1 zonelists. Total pages: 162513
Kernel command line: BOOT_IMAGE=linux root=/dev/hda7 acpi=on resume=/dev/hda6 splash=silent vga=788
bootsplash: silent mode.
mapped APIC to ffffd000 (fee00000)
mapped IOAPIC to ffffc000 (fec00000)
Enabling fast FPU save and restore... done.
Enabling unmasked SIMD FPU exception support... done.
Initializing CPU#0
PID hash table entries: 4096 (order: 12, 16384 bytes)
Detected 1607.548 MHz processor.
Console: colour dummy device 80x25
Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Memory: 643824k/655168k available (2204k kernel code, 10228k reserved, 730k data, 292k init, 0k highmem, 0k BadRAM)
virtual kernel memory layout:
fixmap : 0xffe16000 - 0xfffff000 (1956 kB)
pkmap : 0xff800000 - 0xffc00000 (4096 kB)
vmalloc : 0xe8800000 - 0xff7fe000 ( 367 MB)
lowmem : 0xc0000000 - 0xe7fd0000 ( 639 MB)
.init : 0xc03e4000 - 0xc042d000 ( 292 kB)
.data : 0xc03273db - 0xc03ddc84 ( 730 kB)
.text : 0xc0100000 - 0xc03273db (2204 kB)
Checking if this processor honours the WP bit even in supervisor mode... Ok.
Calibrating delay using timer specific routine.. 3217.06 BogoMIPS (lpj=1608534)
Security Framework v1.0.0 initialized
Mount-cache hash table entries: 512
CPU: After generic identify, caps: 078bfbff e3d3fbff 00000000 00000000 00000001 00000000 00000001
CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
CPU: L2 Cache: 1024K (64 bytes/line)
CPU: After all inits, caps: 078bfbff e3d3fbff 00000000 00000410 00000001 00000000 00000001
Intel machine check architecture supported.
Intel machine check reporting enabled on CPU#0.
Compat vDSO mapped to ffffe000.
Checking 'hlt' instruction... OK.
SMP alternatives: switching to UP code
Freeing SMP alternatives: 12k freed
Early unpacking initramfs... done
Freeing initrd memory: 552k freed
ACPI: Core revision 20070126
ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
CPU0: AMD Turion(tm) 64 Mobile Technology MT-30 stepping 02
Total of 1 processors activated (3217.06 BogoMIPS).
ENABLING IO-APIC IRQs
..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
..MP-BIOS bug: 8254 timer not connected to IO-APIC
...trying to set up timer (IRQ0) through the 8259A ... failed.
...trying to set up timer as Virtual Wire IRQ... works.
Brought up 1 CPUs
Booting paravirtualized kernel on bare hardware
NET: Registered protocol family 16
ACPI: bus type pci registered
PCI: BIOS Bug: MCFG area at e0000000 is not E820-reserved
PCI: Not using MMCONFIG.
PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=2
PCI: Using configuration type 1
Setting up standard PCI resources
ACPI: EC: Look up EC in DSDT
ACPI: EC: GPE = 0x11, I/O: command/status = 0x66, data = 0x62
ACPI: Interpreter enabled
ACPI: (supports S0 S1 S3 S4 S5)
ACPI: Using IOAPIC for interrupt routing
ACPI: EC: GPE = 0x11, I/O: command/status = 0x66, data = 0x62
ACPI: PCI Root Bridge [PCI0] (0000:00)
PCI: Probing PCI hardware (bus 00)
PCI: Transparent bridge - 0000:00:14.4
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P9._PRT]
ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
ACPI: PCI Interrupt Link [LNKF] (IRQs 9) *0, disabled.
ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
Linux Plug and Play Support v0.97 (c) Adam Belay
pnp: PnP ACPI init
ACPI: bus type pnp registered
pnp: PnP ACPI: found 11 devices
ACPI: ACPI bus type pnp unregistered
PnPBIOS: Disabled
PCI: Using ACPI for IRQ routing
PCI: If a device doesn't work, try "pci=routeirq". If it helps, post a report
ACPI: RTC can wake from S4
pnp: 00:05: iomem range 0xfff80000-0xffffffff could not be reserved
pnp: 00:06: ioport range 0x22c-0x22c has been reserved
pnp: 00:06: ioport range 0x22d-0x22d has been reserved
pnp: 00:06: ioport range 0x22e-0x22e has been reserved
pnp: 00:06: ioport range 0x22f-0x22f has been reserved
pnp: 00:06: iomem range 0xfec00000-0xfec00fff has been reserved
pnp: 00:06: iomem range 0xfee00000-0xfee00fff has been reserved
pnp: 00:09: iomem range 0xe0000000-0xefffffff has been reserved
pnp: 00:0a: iomem range 0x0-0x9ffff could not be reserved
pnp: 00:0a: iomem range 0xc0000-0xcffff could not be reserved
pnp: 00:0a: iomem range 0xe0000-0xfffff could not be reserved
pnp: 00:0a: iomem range 0x100000-0x2fffffff could not be reserved
Time: tsc clocksource has been installed.
PCI: Bridge: 0000:00:01.0
IO window: d000-dfff
MEM window: fea00000-feafffff
PREFETCH window: d0000000-dfffffff
PCI: Bridge: 0000:00:14.4
IO window: e000-efff
MEM window: feb00000-febfffff
PREFETCH window: disabled.
NET: Registered protocol family 2
IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
TCP: Hash tables configured (established 131072 bind 65536)
TCP reno registered
apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
apm: overridden by ACPI.
audit: initializing netlink socket (disabled)
audit(1203774545.139:1): initialized
Total HugeTLB memory allocated, 0
VFS: Disk quotas dquot_6.5.1
Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
io scheduler noop registered
io scheduler anticipatory registered
io scheduler deadline registered
io scheduler cfq registered (default)
Boot video device is 0000:01:05.0
vesafb: framebuffer at 0xd0000000, mapped to 0xe8880000, using 3750k, total 131072k
vesafb: mode is 800x600x16, linelength=1600, pages=135
vesafb: protected mode interface info at c000:5435
vesafb: pmi: set display start = c00c54a3, set palette = c00c54dd
vesafb: pmi: ports = d810 d816 d854 d838 d83c d85c d800 d804 d8b0 d8b2 d8b4
vesafb: scrolling: redraw
vesafb: Truecolor: size=0:5:6:5, shift=0:11:5:0
bootsplash 3.1.6-2004/03/31: looking for picture...<6> silentjpeg size 224171 bytes,<6>...found (800x600, 224123 bytes, v3).
Console: switching to colour frame buffer device 92x32
fb0: VESA VGA frame buffer device
isapnp: Scanning for PnP cards...
Switched to high resolution mode on CPU 0
isapnp: No Plug & Play device found
Generic RTC Driver v1.07
Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
ACPI: PCI Interrupt 0000:00:14.6[b] -> GSI 17 (level, low) -> IRQ 16
ACPI: PCI interrupt for device 0000:00:14.6 disabled
RAMDISK driver initialized: 16 RAM disks of 32000K size 1024 blocksize
Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
ATIIXP: IDE controller at PCI slot 0000:00:14.1
ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 17
ATIIXP: chipset revision 128
ATIIXP: not 100% native mode: will probe irqs later
ide0: BM-DMA at 0xff00-0xff07, BIOS settings: hda:DMA, hdb:pio
ide1: BM-DMA at 0xff08-0xff0f, BIOS settings: hdc:DMA, hdd:pio
Probing IDE interface ide0...
hda: HTS541040G9AT00, ATA DISK drive
hda: selected mode 0x45
ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
Probing IDE interface ide1...
hdc: TSSTcorpCDW/DVD TS-L462C, ATAPI CD/DVD-ROM drive
hdc: selected mode 0x42
ide1 at 0x170-0x177,0x376 on irq 15
hda: max request size: 512KiB
hda: 78140160 sectors (40007 MB) w/7539KiB Cache, CHS=16383/255/63, UDMA(100)
hda: cache flushes supported
hda: hda1 hda2 < hda5 hda6 hda7 >
PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
i8042.c: Detected active multiplexing controller, rev 1.1.
serio: i8042 KBD port at 0x60,0x64 irq 1
serio: i8042 AUX0 port at 0x60,0x64 irq 12
serio: i8042 AUX1 port at 0x60,0x64 irq 12
serio: i8042 AUX2 port at 0x60,0x64 irq 12
serio: i8042 AUX3 port at 0x60,0x64 irq 12
mice: PS/2 mouse device common for all mice
TCP cubic registered
NET: Registered protocol family 1
Using IPI No-Shortcut mode
BIOS EDD facility v0.16 2004-Jun-25, 1 devices found
Freeing unused kernel memory: 292k freed
kjournald starting. Commit interval 5 seconds
EXT3-fs: mounted filesystem with ordered data mode.
Synaptics Touchpad, model: 1, fw: 5.9, id: 0x256eb1, caps: 0x804713/0x0
input: SynPS/2 Synaptics TouchPad as /class/input/input0
input: AT Translated Set 2 keyboard as /class/input/input1
usbcore: registered new interface driver usbfs
usbcore: registered new interface driver hub
usbcore: registered new device driver usb
ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 19 (level, low) -> IRQ 18
ohci_hcd 0000:00:13.0: OHCI Host Controller
ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
ohci_hcd 0000:00:13.0: irq 18, io mem 0xfe9ff000
usb usb1: configuration #1 chosen from 1 choice
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 4 ports detected
ACPI: PCI Interrupt 0000:00:13.1[A] -> GSI 19 (level, low) -> IRQ 18
ohci_hcd 0000:00:13.1: OHCI Host Controller
ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
ohci_hcd 0000:00:13.1: irq 18, io mem 0xfe9fe000
usb usb2: configuration #1 chosen from 1 choice
hub 2-0:1.0: USB hub found
hub 2-0:1.0: 4 ports detected
usb 1-1: new full speed USB device using ohci_hcd and address 2
usb 1-1: configuration #1 chosen from 1 choice
hub 1-1:1.0: USB hub found
hub 1-1:1.0: 4 ports detected
ACPI: PCI Interrupt 0000:00:13.2[A] -> GSI 19 (level, low) -> IRQ 18
ehci_hcd 0000:00:13.2: EHCI Host Controller
ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
ehci_hcd 0000:00:13.2: irq 18, io mem 0xfe9fd000
ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
usb usb3: configuration #1 chosen from 1 choice
hub 3-0:1.0: USB hub found
hub 3-0:1.0: 8 ports detected
usb 1-1: USB disconnect, address 2
usb 3-1: new high speed USB device using ehci_hcd and address 2
usb 3-1: configuration #1 chosen from 1 choice
hub 3-1:1.0: USB hub found
hub 3-1:1.0: 4 ports detected
usb 3-5: new high speed USB device using ehci_hcd and address 3
usb 3-5: configuration #1 chosen from 1 choice
SCSI subsystem initialized
Initializing USB Mass Storage driver...
scsi0 : SCSI emulation for USB Mass Storage devices
usbcore: registered new interface driver usb-storage
USB Mass Storage support registered.
usb-storage: device found at 3
usb-storage: waiting for device to settle before scanning
Capability LSM initialized
Floppy drive(s): fd0 is 1.44M
floppy0: no floppy controllers found
Linux video capture interface: v2.00
bttv: driver version 0.9.17 loaded
bttv: using 8 buffers with 2080k (520 pages) each for capture
sdhci: Secure Digital Host Controller Interface driver
sdhci: Copyright(c) Pierre Ossman
sonypi: Sony Programmable I/O Controller Driver v1.26.
Non-volatile memory driver v1.2
Linux agpgart interface v0.102 (c) Dave Jones
ACPI: duty_cycle spans bit 4
powernow-k8: Found 1 AMD Turion(tm) 64 Mobile Technology MT-30 processors (version 2.00.00)
powernow-k8: 0 : fid 0x8 (1600 MHz), vid 0xa
powernow-k8: 1 : fid 0x0 (800 MHz), vid 0x16
device-mapper: ioctl: 4.11.0-ioctl (2006-10-12) initialised: [email]dm-devel@redhat.com[/email]
EXT3 FS on hda7, internal journal
scsi 0:0:0:0: Direct-Access Generic 2.0 Reader-SD/MS 1.00 PQ: 0 ANSI: 0 CCS
usb-storage: device scan complete
sd 0:0:0:0: [sda] Attached SCSI removable disk
sd 0:0:0:0: Attached scsi generic sg0 type 0
Adding 1485972k swap on /dev/hda6. Priority:-1 extents:1 across:1485972k
NTFS driver 2.1.28 [Flags: R/O DEBUG MODULE].
NTFS volume version 3.1.
kjournald starting. Commit interval 5 seconds
EXT3 FS on hda5, internal journal
EXT3-fs: mounted filesystem with ordered data mode.
loop: module loaded
hdc: ATAPI 24X DVD-ROM CD-R/RW drive, 1536kB Cache, UDMA(33)
Uniform CD-ROM driver Revision: 3.20
bootsplash 3.1.6-2004/03/31: looking for picture...<6> silentjpeg size 224171 bytes,<6>...found (800x600, 224123 bytes, v3).
bootsplash: status on console 0 changed to on
ACPI: AC Adapter [ADP0] (on-line)
ACPI: Battery Slot [BAT0] (battery present)
No dock devices found.
input: Power Button (FF) as /class/input/input2
ACPI: Power Button (FF) [PWRF]
input: Lid Switch as /class/input/input3
ACPI: Lid Switch [LID0]
input: Power Button (CM) as /class/input/input4
ACPI: Power Button (CM) [PWRB]
Marking TSC unstable due to: cpufreq changes.
Time: acpi_pm clocksource has been installed.
Clocksource tsc unstable (delta = -151448463 ns)
NET: Registered protocol family 10
lo: Disabled Privacy Extensions
Mobile IPv6
ACPI: PCI Interrupt 0000:00:14.5[b] -> GSI 17 (level, low) -> IRQ 16
NET: Registered protocol family 17
8139too Fast Ethernet driver 0.9.28
ACPI: PCI Interrupt 0000:02:02.0[A] -> GSI 20 (level, low) -> IRQ 19
eth0: RealTek RTL8139 at 0xe902cc00, 00:14:2a:ac:3f:5f, IRQ 19
eth0: Identified 8139 chip type 'RTL-8100B/8139D'
eth0: link down
ADDRCONF(NETDEV_UP): eth0: link is not ready
ACPI: PCI Interrupt 0000:02:04.0[A] -> GSI 22 (level, low) -> IRQ 20
rt2500 1.1.0 CVS 2007112309 [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
rt2500 EEPROM: 1 2 3 4 5 6 7 8 9 10 11 12 13 14 Channel
rt2500 EEPROM: 5 5 5 5 5 5 5 5 5 5 5 5 5 5 dBm Maximum
fuse init (API version 7.8)
ieee80211_crypt: registered algorithm 'NULL'
ieee80211: 802.11 data/management/control stack, git-1.1.13
ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
bcm43xx driver
bootsplash 3.1.6-2004/03/31: looking for picture...<6>...found (800x600, 3177 bytes, v3).
bootsplash: status on console 0 changed to on
bootsplash 3.1.6-2004/03/31: looking for picture...<6>...found (800x600, 3177 bytes, v3).
bootsplash: status on console 1 changed to on
bootsplash 3.1.6-2004/03/31: looking for picture...<6>...found (800x600, 3177 bytes, v3).
bootsplash: status on console 2 changed to on
bootsplash 3.1.6-2004/03/31: looking for picture...<6>...found (800x600, 3177 bytes, v3).
bootsplash: status on console 3 changed to on
bootsplash 3.1.6-2004/03/31: looking for picture...<6>...found (800x600, 3177 bytes, v3).
bootsplash: status on console 4 changed to on
bootsplash 3.1.6-2004/03/31: looking for picture...<6>...found (800x600, 3177 bytes, v3).
bootsplash: status on console 5 changed to on
ra0: no IPv6 routers present
Floppy drive(s): fd0 is 1.44M
floppy0: no floppy controllers found
Floppy drive(s): fd0 is 1.44M
floppy0: no floppy controllers found
rt2500 EEPROM: 1 2 3 4 5 6 7 8 9 10 11 12 13 14 Channel
rt2500 EEPROM: 5 5 5 5 5 5 5 5 5 5 5 5 5 5 dBm Maximum
ra0: no IPv6 routers present
rt2500 EEPROM: 1 2 3 4 5 6 7 8 9 10 11 12 13 14 Channel
rt2500 EEPROM: 5 5 5 5 5 5 5 5 5 5 5 5 5 5 dBm Maximum
ra0: no IPv6 routers present
rt2500 EEPROM: 1 2 3 4 5 6 7 8 9 10 11 12 13 14 Channel
rt2500 EEPROM: 5 5 5 5 5 5 5 5 5 5 5 5 5 5 dBm Maximum
ra0: no IPv6 routers present
rt2500 EEPROM: 1 2 3 4 5 6 7 8 9 10 11 12 13 14 Channel
rt2500 EEPROM: 5 5 5 5 5 5 5 5 5 5 5 5 5 5 dBm Maximum
ra0: no IPv6 routers present
rt2500 EEPROM: 1 2 3 4 5 6 7 8 9 10 11 12 13 14 Channel
rt2500 EEPROM: 5 5 5 5 5 5 5 5 5 5 5 5 5 5 dBm Maximum
rt2500 EEPROM: 1 2 3 4 5 6 7 8 9 10 11 12 13 14 Channel
rt2500 EEPROM: 5 5 5 5 5 5 5 5 5 5 5 5 5 5 dBm Maximum
ra0: no IPv6 routers present
rt2500 EEPROM: 1 2 3 4 5 6 7 8 9 10 11 12 13 14 Channel
rt2500 EEPROM: 5 5 5 5 5 5 5 5 5 5 5 5 5 5 dBm Maximum
ra0: no IPv6 routers present
rt2500 EEPROM: 1 2 3 4 5 6 7 8 9 10 11 12 13 14 Channel
rt2500 EEPROM: 5 5 5 5 5 5 5 5 5 5 5 5 5 5 dBm Maximum
ra0: no IPv6 routers present
rt2500 EEPROM: 1 2 3 4 5 6 7 8 9 10 11 12 13 14 Channel
rt2500 EEPROM: 5 5 5 5 5 5 5 5 5 5 5 5 5 5 dBm Maximum
ra0: no IPv6 routers present
rt2500 EEPROM: 1 2 3 4 5 6 7 8 9 10 11 12 13 14 Channel
rt2500 EEPROM: 5 5 5 5 5 5 5 5 5 5 5 5 5 5 dBm Maximum
ra0: no IPv6 routers present
rt2500 EEPROM: 1 2 3 4 5 6 7 8 9 10 11 12 13 14 Channel
rt2500 EEPROM: 5 5 5 5 5 5 5 5 5 5 5 5 5 5 dBm Maximum
rt2500 EEPROM: 1 2 3 4 5 6 7 8 9 10 11 12 13 14 Channel
rt2500 EEPROM: 5 5 5 5 5 5 5 5 5 5 5 5 5 5 dBm Maximum
ra0: no IPv6 routers present
rt2500 EEPROM: 1 2 3 4 5 6 7 8 9 10 11 12 13 14 Channel
rt2500 EEPROM: 5 5 5 5 5 5 5 5 5 5 5 5 5 5 dBm Maximum
ra0: no IPv6 routers present
rt2500 EEPROM: 1 2 3 4 5 6 7 8 9 10 11 12 13 14 Channel
rt2500 EEPROM: 5 5 5 5 5 5 5 5 5 5 5 5 5 5 dBm Maximum
rt2500 EEPROM: 1 2 3 4 5 6 7 8 9 10 11 12 13 14 Channel
rt2500 EEPROM: 5 5 5 5 5 5 5 5 5 5 5 5 5 5 dBm Maximum
eth0: link down
ADDRCONF(NETDEV_UP): eth0: link is not ready
ra0: no IPv6 routers present
rt2500 EEPROM: 1 2 3 4 5 6 7 8 9 10 11 12 13 14 Channel
rt2500 EEPROM: 5 5 5 5 5 5 5 5 5 5 5 5 5 5 dBm Maximum
ra0: no IPv6 routers present
rt2500 EEPROM: 1 2 3 4 5 6 7 8 9 10 11 12 13 14 Channel
rt2500 EEPROM: 5 5 5 5 5 5 5 5 5 5 5 5 5 5 dBm Maximum
rt2500 EEPROM: 1 2 3 4 5 6 7 8 9 10 11 12 13 14 Channel
rt2500 EEPROM: 5 5 5 5 5 5 5 5 5 5 5 5 5 5 dBm Maximum
rt2500 EEPROM: 1 2 3 4 5 6 7 8 9 10 11 12 13 14 Channel
rt2500 EEPROM: 5 5 5 5 5 5 5 5 5 5 5 5 5 5 dBm Maximum
rt2500 EEPROM: 1 2 3 4 5 6 7 8 9 10 11 12 13 14 Channel
rt2500 EEPROM: 5 5 5 5 5 5 5 5 5 5 5 5 5 5 dBm Maximum
rt2500 EEPROM: 1 2 3 4 5 6 7 8 9 10 11 12 13 14 Channel
rt2500 EEPROM: 5 5 5 5 5 5 5 5 5 5 5 5 5 5 dBm Maximum
ra0: no IPv6 routers present

So I am pretty much at a loss. My house uses WEP HEX Encryption. I need to connect to it and not rely on the neighboring unsecure networks. Lastly, I am obviously entering the correct encryption key when I try to connect. Any help, please?

---

### Post by nixscripter on 2008-02-24
First thing that jumps out at me is from dmesg:

```

ieee80211_crypt: registered algorithm 'NULL'
ieee80211: 802.11 data/management/control stack, git-1.1.13
ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
bcm43xx driver

```

That looks like the kernel driver isn't loading other drivers which do encryption, such as ieee80211_crypt_wep. Try this: ```
sudo modprobe ieee80211_crypt_wep
``` to load the driver

---

