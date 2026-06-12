---
title: "[SOLVED] Wireless not working with Gutsy - Xubuntu"
date: 2007-10-21
forum: Networking &amp; Wireless
---

### Post by ushills on 2007-10-21
Hi

I have installed 7.10 Xubuntu on my daughters PC, however, while the RT61 card works on my PC it doesn't work on hers.  The problem seems to lie in the dmesg output at the bottom, however the network is currently open with encryption.

This lspci

```
00:00.0 Host bridge: VIA Technologies, Inc. VT82C693A/694x [Apollo PRO133x] (rev c4)
00:01.0 PCI bridge: VIA Technologies, Inc. VT82C598/694x [Apollo MVP3/Pro133x AGP]
00:07.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 22)
00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 10)
00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 10)
00:07.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 10)
00:07.4 Host bridge: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 30)
00:07.5 Multimedia audio controller: VIA Technologies, Inc. VT82C686 AC97 Audio Controller (rev 20)
00:0b.0 Network controller: RaLink RT2561/RT61 rev B 802.11g
00:0c.0 Communication controller: Intel Corporation 536EP Data Fax Modem
01:00.0 VGA compatible controller: 3Dfx Interactive, Inc. Voodoo 3 (rev 01)
```

This is my interfaces:

```
auto lo
iface lo inet loopback


auto wlan0
iface wlan0 inet static
address 192.168.1.5
netmask 255.255.255.0
gateway 192.168.1.1
wireless-essid DALI

 

```

This is what hapens when I type iwconfig

```
wlan0     IEEE 802.11g  ESSID:"DALI"  
          Mode:Managed  Frequency:2.442 GHz  Access Point: 00:19:7D:24:B2:0E   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

This is the output of ifconfig

```
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:212 errors:0 dropped:0 overruns:0 frame:0
          TX packets:212 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:19552 (19.0 KB)  TX bytes:19552 (19.0 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1B:11:06:AB:F1  
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:11ff:fe06:abf1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1601 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2052 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1885550 (1.7 MB)  TX bytes:254097 (248.1 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1B-11-06-AB-F1-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```

What happens when I ping

```
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
From 192.168.1.5 icmp_seq=1 Destination Host Unreachable
From 192.168.1.5 icmp_seq=2 Destination Host Unreachable
From 192.168.1.5 icmp_seq=3 Destination Host Unreachable

```

The problems seems to lie in dmesg, but I don't understand it!

```
[    0.000000] Linux version 2.6.22-14-generic (buildd@palmer) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Sun Oct 14 23:05:12 GMT 2007 (Ubuntu 2.6.22-14.46-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 00000000000a0000 (usable)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000013ff0000 (usable)
[    0.000000]  BIOS-e820: 0000000013ff0000 - 0000000013ff3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 0000000013ff3000 - 0000000014000000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 319MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 81904) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->    81904
[    0.000000]   HighMem     81904 ->    81904
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->    81904
[    0.000000] On node 0 totalpages: 81904
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 607 pages used for memmap
[    0.000000]   Normal zone: 77201 pages, LIFO batch:15
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI 2.2 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F70A0 checksum 0
[    0.000000] ACPI: RSDP 000F70A0, 0014 (r0 VT694X)
[    0.000000] ACPI: RSDT 13FF3000, 0028 (r1 VT694X AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: FACP 13FF3040, 0074 (r1 VT694X AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: DSDT 13FF30C0, 21A6 (r1 VT694X AWRDACPI     1000 MSFT  100000A)
[    0.000000] ACPI: FACS 13FF0000, 0040
[    0.000000] ACPI: DMI BIOS year==0, assuming ACPI-capable machine
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] Allocating PCI resources starting at 20000000 (gap: 14000000:ebff0000)
[    0.000000] Built 1 zonelists.  Total pages: 81265
[    0.000000] Kernel command line: root=UUID=c4dea5e8-43c2-45f5-a399-3d90679e35ef ro quiet splash
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] mapped APIC to ffffd000 (0128c000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] Detected 599.816 MHz processor.
[   40.772058] Console: colour VGA+ 80x25
[   40.773114] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   40.774162] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   40.813761] Memory: 312848k/327616k available (2015k kernel code, 14204k reserved, 916k data, 364k init, 0k highmem)
[   40.813797] virtual kernel memory layout:
[   40.813801]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   40.813807]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   40.813812]     vmalloc : 0xd4800000 - 0xff7fe000   ( 687 MB)
[   40.813817]     lowmem  : 0xc0000000 - 0xd3ff0000   ( 319 MB)
[   40.813821]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[   40.813826]       .data : 0xc02f7d26 - 0xc03dce84   ( 916 kB)
[   40.813831]       .text : 0xc0100000 - 0xc02f7d26   (2015 kB)
[   40.813843] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   40.813964] SLUB: Genslabs=22, HWalign=32, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   40.893994] Calibrating delay using timer specific routine.. 1201.04 BogoMIPS (lpj=2402095)
[   40.894080] Security Framework v1.0.0 initialized
[   40.894109] SELinux:  Disabled at boot.
[   40.894160] Mount-cache hash table entries: 512
[   40.894564] CPU: After generic identify, caps: 0387f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[   40.894601] CPU: L1 I cache: 16K, L1 D cache: 16K
[   40.894610] CPU: L2 cache: 512K
[   40.894620] CPU serial number disabled.
[   40.894628] CPU: After all inits, caps: 0383f9ff 00000000 00000000 00000040 00000000 00000000 00000000
[   40.894663] Compat vDSO mapped to ffffe000.
[   40.894707] Checking 'hlt' instruction... OK.
[   40.910294] SMP alternatives: switching to UP code
[   40.910798] Freeing SMP alternatives: 11k freed
[   40.911656] Early unpacking initramfs... done
[   42.060449] ACPI: Core revision 20070126
[   42.060674] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   42.063918] ACPI: setting ELCR to 0200 (from 1e20)
[   42.172285] CPU0: Intel Pentium III (Katmai) stepping 03
[   42.172305] SMP motherboard not detected.
[   42.172313] Local APIC not detected. Using dummy APIC emulation.
[   42.172469] Brought up 1 CPUs
[   42.172869] Booting paravirtualized kernel on bare hardware
[   42.173042] Time:  8:01:27  Date: 09/21/107
[   42.173129] NET: Registered protocol family 16
[   42.173470] EISA bus registered
[   42.173501] ACPI: bus type pci registered
[   42.204905] PCI: PCI BIOS revision 2.10 entry at 0xfb270, last bus=1
[   42.204914] PCI: Using configuration type 1
[   42.204921] Setting up standard PCI resources
[   42.214423] ACPI: EC: Look up EC in DSDT
[   42.221405] ACPI: Interpreter enabled
[   42.221416] ACPI: (supports S0 S1 S3 S4 S5)
[   42.221482] ACPI: Using PIC for interrupt routing
[   42.234471] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   42.234518] PCI: Probing PCI hardware (bus 00)
[   42.235040] PCI quirk: region 4000-40ff claimed by vt82c586 ACPI
[   42.235053] PCI quirk: region 6000-607f claimed by vt82c686 HW-mon
[   42.235064] PCI quirk: region 5000-500f claimed by vt82c686 SMB
[   42.235530] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   42.280293] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 *11 12 14 15)
[   42.280806] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 *5 6 7 10 11 12 14 15)
[   42.281329] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 10 11 *12 14 15)
[   42.281878] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 *10 11 12 14 15)
[   42.282186] Linux Plug and Play Support v0.97 (c) Adam Belay
[   42.282224] pnp: PnP ACPI init
[   42.282254] ACPI: bus type pnp registered
[   42.291623] pnp: PnP ACPI: found 11 devices
[   42.291632] ACPI: ACPI bus type pnp unregistered
[   42.291645] PnPBIOS: Disabled by ACPI PNP
[   42.291850] PCI: Using ACPI for IRQ routing
[   42.291862] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   42.361351] NET: Registered protocol family 8
[   42.361360] NET: Registered protocol family 20
[   42.361600] pnp: 00:00: iomem range 0xcc000-0xcdfff has been reserved
[   42.361612] pnp: 00:00: iomem range 0xca000-0xcbfff has been reserved
[   42.361623] pnp: 00:00: iomem range 0xf0000-0xfbfff could not be reserved
[   42.361634] pnp: 00:00: iomem range 0xfc000-0xfffff could not be reserved
[   42.361789] Time: tsc clocksource has been installed.
[   42.393346] PCI: Bridge: 0000:00:01.0
[   42.393357]   IO window: e000-efff
[   42.393369]   MEM window: e4000000-e7ffffff
[   42.393379]   PREFETCH window: e8000000-e9ffffff
[   42.393406] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   42.393446] NET: Registered protocol family 2
[   42.429937] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   42.430110] TCP established hash table entries: 16384 (order: 5, 196608 bytes)
[   42.430866] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[   42.431383] TCP: Hash tables configured (established 16384 bind 16384)
[   42.431394] TCP reno registered
[   42.442227] checking if image is initramfs...<6>Switched to high resolution mode on CPU 0
[   43.436984]  it is
[   44.621479] Freeing initrd memory: 7364k freed
[   44.622583] audit: initializing netlink socket (disabled)
[   44.622627] audit(1192953688.432:1): initialized
[   44.632387] VFS: Disk quotas dquot_6.5.1
[   44.632631] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   44.633033] io scheduler noop registered
[   44.633043] io scheduler anticipatory registered
[   44.633051] io scheduler deadline registered
[   44.633143] io scheduler cfq registered (default)
[   44.633185] PCI: VIA PCI bridge detected. Disabling DAC.
[   44.633196] PCI: Disabling Via external APIC routing
[   44.633252] Boot video device is 0000:01:00.0
[   44.633862] isapnp: Scanning for PnP cards...
[   44.988410] isapnp: No Plug & Play device found
[   45.118773] Real Time Clock Driver v1.12ac
[   45.119109] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   45.119315] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   45.119771] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   45.121852] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   45.122600] 00:08: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   45.125785] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   45.126321] input: Macintosh mouse button emulation as /class/input/input0
[   45.126628] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[   45.126640] PNP: PS/2 controller doesn't have AUX irq; using default 12
[   45.377354] serio: i8042 KBD port at 0x60,0x64 irq 1
[   45.377934] mice: PS/2 mouse device common for all mice
[   45.378392] EISA: Probing bus 0 at eisa.0
[   45.378434] Cannot allocate resource for EISA slot 4
[   45.378443] Cannot allocate resource for EISA slot 5
[   45.378451] Cannot allocate resource for EISA slot 6
[   45.378459] Cannot allocate resource for EISA slot 7
[   45.378473] EISA: Detected 0 cards.
[   45.378797] TCP cubic registered
[   45.378858] NET: Registered protocol family 1
[   45.378950] Using IPI No-Shortcut mode
[   45.379413]   Magic number: 11:410:18
[   45.379442]   hash matches device ttycf
[   45.381012] Freeing unused kernel memory: 364k freed
[   45.441382] input: AT Translated Set 2 keyboard as /class/input/input1
[   47.079974] AppArmor: AppArmor initialized<5>audit(1192953690.932:2):  type=1505 info="AppArmor initialized" pid=1093
[   47.105778] fuse init (API version 7.8)
[   47.125579] Failure registering capabilities with primary security module.
[   47.179095] ACPI: CPU0 (power states: C1[C1] C2[C2])
[   47.179116] ACPI: Processor [CPU0] (supports 2 throttling states)
[   48.990511] SCSI subsystem initialized
[   49.033974] libata version 2.21 loaded.
[   49.077128] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   49.077146] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   49.080056] VP_IDE: IDE controller at PCI slot 0000:00:07.1
[   49.080099] VP_IDE: chipset revision 16
[   49.080107] VP_IDE: not 100% native mode: will probe irqs later
[   49.080131] VP_IDE: VIA vt82c686a (rev 22) IDE UDMA66 controller on pci0000:00:07.1
[   49.080149]     ide0: BM-DMA at 0x6400-0x6407, BIOS settings: hda:DMA, hdb:pio
[   49.080177]     ide1: BM-DMA at 0x6408-0x640f, BIOS settings: hdc:DMA, hdd:pio
[   49.080197] Probing IDE interface ide0...
[   49.150536] usbcore: registered new interface driver usbfs
[   49.150622] usbcore: registered new interface driver hub
[   49.150719] usbcore: registered new device driver usb
[   49.156532] USB Universal Host Controller Interface driver v3.0
[   49.516687] hda: Maxtor 4R080L0, ATA DISK drive
[    9.004000] Marking TSC unstable due to: possible TSC halt in C2.
[    9.008000] Time: acpi_pm clocksource has been installed.
[    9.260000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[    9.260000] Probing IDE interface ide1...
[   10.124000] hdc: ATAPI DVD A DH20A3P, ATAPI CD/DVD-ROM drive
[   10.796000] ide1 at 0x170-0x177,0x376 on irq 15
[   10.860000] hda: max request size: 128KiB
[   10.864000] hdc: ATAPI 12X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(33)
[   10.864000] Uniform CD-ROM driver Revision: 3.20
[   10.864000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 10
[   10.864000] PCI: setting IRQ 10 as level-triggered
[   10.864000] ACPI: PCI Interrupt 0000:00:07.2[D] -> Link [LNKD] -> GSI 10 (level, low) -> IRQ 10
[   10.864000] uhci_hcd 0000:00:07.2: UHCI Host Controller
[   10.864000] uhci_hcd 0000:00:07.2: new USB bus registered, assigned bus number 1
[   10.864000] uhci_hcd 0000:00:07.2: irq 10, io base 0x00006800
[   10.904000] hda: 160086528 sectors (81964 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(66)
[   10.904000] usb usb1: configuration #1 chosen from 1 choice
[   10.904000] hda: cache flushes supported
[   10.904000]  hda:<6>hub 1-0:1.0: USB hub found
[   10.908000] hub 1-0:1.0: 2 ports detected
[   10.940000]  hda1 hda2 < hda5 > hda3
[   11.016000] ACPI: PCI Interrupt 0000:00:07.3[D] -> Link [LNKD] -> GSI 10 (level, low) -> IRQ 10
[   11.016000] uhci_hcd 0000:00:07.3: UHCI Host Controller
[   11.016000] uhci_hcd 0000:00:07.3: new USB bus registered, assigned bus number 2
[   11.016000] uhci_hcd 0000:00:07.3: irq 10, io base 0x00006c00
[   11.016000] usb usb2: configuration #1 chosen from 1 choice
[   11.016000] hub 2-0:1.0: USB hub found
[   11.016000] hub 2-0:1.0: 2 ports detected
[   11.256000] usb 1-1: new low speed USB device using uhci_hcd and address 2
[   11.376000] Attempting manual resume
[   11.376000] swsusp: Resume From Partition 3:5
[   11.376000] PM: Checking swsusp image.
[   11.384000] PM: Resume from disk failed.
[   11.452000] usb 1-1: configuration #1 chosen from 1 choice
[   11.560000] kjournald starting.  Commit interval 5 seconds
[   11.560000] EXT3-fs: mounted filesystem with ordered data mode.
[   11.696000] usb 1-2: new full speed USB device using uhci_hcd and address 3
[   11.860000] usb 1-2: configuration #1 chosen from 1 choice
[   12.116000] usbcore: registered new interface driver hiddev
[   12.132000] input: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) as /class/input/input2
[   12.132000] input: USB HID v1.10 Mouse [Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)] on usb-0000:00:07.2-1
[   12.132000] usbcore: registered new interface driver usbhid
[   12.132000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   24.312000] parport_pc: VIA 686A/8231 detected
[   24.312000] parport_pc: probing current configuration
[   24.312000] parport_pc: Current parallel port base: 0x378
[   24.312000] parport0: PC-style at 0x378, irq 7 [PCSPP,EPP]
[   24.340000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   24.352000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   24.416000] Linux agpgart interface v0.102 (c) Dave Jones
[   24.432000] agpgart: Detected VIA Apollo Pro 133 chipset
[   24.440000] agpgart: AGP aperture is 64M @ 0xe0000000
[   24.696000] parport_pc: VIA parallel port: io=0x378, irq=7
[   25.492000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 5
[   25.492000] PCI: setting IRQ 5 as level-triggered
[   25.492000] ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
[   26.864000] input: PC Speaker as /class/input/input3
[   26.972000] ieee80211_init: failed to initialize WME (err=-17)
[   26.984000] iwlwifi_rc80211_simple: Unknown symbol iwlwifi_ieee80211_rate_control_unregister
[   26.984000] iwlwifi_rc80211_simple: Unknown symbol iwlwifi_sta_info_put
[   26.984000] iwlwifi_rc80211_simple: Unknown symbol iwlwifi_sta_info_get
[   26.984000] iwlwifi_rc80211_simple: Unknown symbol iwlwifi_ieee80211_rate_control_register
[   26.988000] wmaster0: Selected rate control algorithm 'simple'
[   27.784000] voodoo3_smbus 0000:01:00.0: Using Banshee/Voodoo3 I2C device at d499e000
[   27.976000] usbcore: registered new interface driver libusual
[   28.032000] Initializing USB Mass Storage driver...
[   28.032000] scsi0 : SCSI emulation for USB Mass Storage devices
[   28.032000] usb-storage: device found at 3
[   28.032000] usb-storage: waiting for device to settle before scanning
[   28.032000] usbcore: registered new interface driver usb-storage
[   28.032000] USB Mass Storage support registered.
[   28.972000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 12
[   28.972000] PCI: setting IRQ 12 as level-triggered
[   28.972000] ACPI: PCI Interrupt 0000:00:07.5[C] -> Link [LNKC] -> GSI 12 (level, low) -> IRQ 12
[   28.976000] PCI: Setting latency timer of device 0000:00:07.5 to 64
[   29.920000] wlan0: Initial auth_alg=0
[   29.920000] wlan0: authenticate with AP 00:19:7d:24:b2:0e
[   29.920000] wlan0: RX authentication from 00:19:7d:24:b2:0e (alg=0 transaction=2 status=1)
[   29.920000] wlan0: AP denied authentication (auth_alg=0 code=1)
[   30.120000] wlan0: authenticate with AP 00:19:7d:24:b2:0e
[   30.120000] wlan0: RX authentication from 00:19:7d:24:b2:0e (alg=0 transaction=2 status=1)
[   30.120000] wlan0: AP denied authentication (auth_alg=0 code=1)
[   30.232000] lp0: using parport0 (interrupt-driven).
[   30.320000] wlan0: authenticate with AP 00:19:7d:24:b2:0e
[   30.320000] wlan0: RX authentication from 00:19:7d:24:b2:0e (alg=0 transaction=2 status=1)
[   30.320000] wlan0: AP denied authentication (auth_alg=0 code=1)
[   30.344000] Adding 738948k swap on /dev/hda5.  Priority:-1 extents:1 across:738948k
[   30.432000] NET: Registered protocol family 17
[   30.520000] wlan0: authentication with AP 00:19:7d:24:b2:0e timed out
[   30.948000] EXT3 FS on hda1, internal journal
[   32.000000] kjournald starting.  Commit interval 5 seconds
[   32.000000] EXT3 FS on hda3, internal journal
[   32.000000] EXT3-fs: mounted filesystem with ordered data mode.
[   33.032000] usb-storage: device scan complete
[   33.036000] scsi 0:0:0:0: Direct-Access     LEXAR    JD EXPRESSION    1.00 PQ: 0 ANSI: 1 CCS
[   33.104000] sd 0:0:0:0: [sda] 2014992 512-byte hardware sectors (1032 MB)
[   33.108000] sd 0:0:0:0: [sda] Write Protect is off
[   33.108000] sd 0:0:0:0: [sda] Mode Sense: 23 00 00 00
[   33.108000] sd 0:0:0:0: [sda] Assuming drive cache: write through
[   33.120000] sd 0:0:0:0: [sda] 2014992 512-byte hardware sectors (1032 MB)
[   33.124000] sd 0:0:0:0: [sda] Write Protect is off
[   33.124000] sd 0:0:0:0: [sda] Mode Sense: 23 00 00 00
[   33.124000] sd 0:0:0:0: [sda] Assuming drive cache: write through
[   33.124000]  sda: sda1
[   33.136000] sd 0:0:0:0: [sda] Attached SCSI removable disk
[   33.180000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   34.412000] No dock devices found.
[   34.596000] input: Power Button (FF) as /class/input/input4
[   34.596000] ACPI: Power Button (FF) [PWRF]
[   34.648000] input: Power Button (CM) as /class/input/input5
[   34.648000] ACPI: Power Button (CM) [PWRB]
[   37.704000] ppdev: user-space parallel port driver
[   38.400000] audit(1192953724.064:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4433 profile="/usr/sbin/cupsd"
[   38.544000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   38.544000] apm: overridden by ACPI.
[   39.024000] Failure registering capabilities with primary security module.
[   41.928000] [drm] Initialized drm 1.1.0 20060810
[   41.964000] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[   41.964000] PCI: setting IRQ 11 as level-triggered
[   41.964000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   41.972000] [drm] Initialized tdfx 1.0.0 20010216 on minor 0
[   71.880000] NET: Registered protocol family 10
[   71.880000] lo: Disabled Privacy Extensions
[   71.880000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  280.100000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  280.108000] wlan0: Initial auth_alg=0
[  280.108000] wlan0: authenticate with AP 00:19:7d:24:b2:0e
[  280.140000] wlan0: RX authentication from 00:19:7d:24:b2:0e (alg=0 transaction=2 status=1)
[  280.140000] wlan0: AP denied authentication (auth_alg=0 code=1)
[  280.308000] wlan0: authenticate with AP 00:19:7d:24:b2:0e
[  280.312000] wlan0: RX authentication from 00:19:7d:24:b2:0e (alg=0 transaction=2 status=1)
[  280.312000] wlan0: AP denied authentication (auth_alg=0 code=1)
[  280.312000] wlan0: RX authentication from 00:19:7d:24:b2:0e (alg=0 transaction=2 status=1)
[  280.312000] wlan0: AP denied authentication (auth_alg=0 code=1)
[  280.320000] wlan0: RX authentication from 00:19:7d:24:b2:0e (alg=0 transaction=2 status=1)
[  280.320000] wlan0: AP denied authentication (auth_alg=0 code=1)
[  280.324000] wlan0: RX authentication from 00:19:7d:24:b2:0e (alg=0 transaction=2 status=1)
[  280.324000] wlan0: AP denied authentication (auth_alg=0 code=1)
[  280.508000] wlan0: authenticate with AP 00:19:7d:24:b2:0e
[  280.520000] wlan0: RX authentication from 00:19:7d:24:b2:0e (alg=0 transaction=2 status=1)
[  280.520000] wlan0: AP denied authentication (auth_alg=0 code=1)
[  280.528000] wlan0: RX authentication from 00:19:7d:24:b2:0e (alg=0 transaction=2 status=1)
[  280.528000] wlan0: AP denied authentication (auth_alg=0 code=1)
[  280.532000] wlan0: RX authentication from 00:19:7d:24:b2:0e (alg=0 transaction=2 status=1)
[  280.532000] wlan0: AP denied authentication (auth_alg=0 code=1)
[  280.536000] wlan0: RX authentication from 00:19:7d:24:b2:0e (alg=0 transaction=2 status=1)
[  280.536000] wlan0: AP denied authentication (auth_alg=0 code=1)
[  280.540000] wlan0: RX authentication from 00:19:7d:24:b2:0e (alg=0 transaction=2 status=1)
[  280.540000] wlan0: AP denied authentication (auth_alg=0 code=1)
[  280.560000] wlan0: RX authentication from 00:19:7d:24:b2:0e (alg=0 transaction=2 status=1)
[  280.560000] wlan0: AP denied authentication (auth_alg=0 code=1)
[  280.708000] wlan0: authentication with AP 00:19:7d:24:b2:0e timed out
[  425.016000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  425.024000] wlan0: Initial auth_alg=0
[  425.024000] wlan0: authenticate with AP 00:19:7d:24:b2:0e
[  425.024000] wlan0: RX authentication from 00:19:7d:24:b2:0e (alg=0 transaction=2 status=0)
[  425.024000] wlan0: authenticated
[  425.024000] wlan0: associate with AP 00:19:7d:24:b2:0e
[  425.028000] wlan0: authentication frame received from 00:19:7d:24:b2:0e, but not in authenticate state - ignored
[  425.032000] wlan0: RX AssocResp from 00:19:7d:24:b2:0e (capab=0x401 status=0 aid=2)
[  425.032000] wlan0: associated
[  425.032000] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  435.788000] wlan0: no IPv6 routers present
[  611.032000] wlan0: No ProbeResp from current AP 00:19:7d:24:b2:0e - assume out of range
[  643.032000] wlan0: No STA entry for own AP 00:19:7d:24:b2:0e
[  675.032000] wlan0: No STA entry for own AP 00:19:7d:24:b2:0e
[  707.032000] wlan0: No STA entry for own AP 00:19:7d:24:b2:0e
[  739.032000] wlan0: No STA entry for own AP 00:19:7d:24:b2:0e
[  771.032000] wlan0: No STA entry for own AP 00:19:7d:24:b2:0e
[  803.032000] wlan0: No STA entry for own AP 00:19:7d:24:b2:0e
[  835.032000] wlan0: No STA entry for own AP 00:19:7d:24:b2:0e
[  867.032000] wlan0: No STA entry for own AP 00:19:7d:24:b2:0e
[  899.032000] wlan0: No STA entry for own AP 00:19:7d:24:b2:0e
[  931.032000] wlan0: No STA entry for own AP 00:19:7d:24:b2:0e
[  963.032000] wlan0: No STA entry for own AP 00:19:7d:24:b2:0e
[ 1006.376000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1006.392000] wlan0: Initial auth_alg=0
[ 1006.392000] wlan0: authenticate with AP 00:19:7d:24:b2:0e
[ 1006.392000] wlan0: RX authentication from 00:19:7d:24:b2:0e (alg=0 transaction=2 status=0)
[ 1006.392000] wlan0: authenticated
[ 1006.392000] wlan0: associate with AP 00:19:7d:24:b2:0e
[ 1006.396000] wlan0: authentication frame received from 00:19:7d:24:b2:0e, but not in authenticate state - ignored
[ 1006.400000] wlan0: authentication frame received from 00:19:7d:24:b2:0e, but not in authenticate state - ignored
[ 1006.416000] wlan0: authentication frame received from 00:19:7d:24:b2:0e, but not in authenticate state - ignored
[ 1006.416000] wlan0: authentication frame received from 00:19:7d:24:b2:0e, but not in authenticate state - ignored
[ 1006.420000] wlan0: authentication frame received from 00:19:7d:24:b2:0e, but not in authenticate state - ignored
[ 1006.592000] wlan0: associate with AP 00:19:7d:24:b2:0e
[ 1006.600000] wlan0: RX AssocResp from 00:19:7d:24:b2:0e (capab=0x401 status=0 aid=2)
[ 1006.600000] wlan0: associated
[ 1006.604000] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1017.500000] wlan0: no IPv6 routers present
[ 1402.600000] wlan0: No ProbeResp from current AP 00:19:7d:24:b2:0e - assume out of range
[ 1434.600000] wlan0: No STA entry for own AP 00:19:7d:24:b2:0e
[ 1466.600000] wlan0: No STA entry for own AP 00:19:7d:24:b2:0e
[ 1498.600000] wlan0: No STA entry for own AP 00:19:7d:24:b2:0e
[ 1530.600000] wlan0: No STA entry for own AP 00:19:7d:24:b2:0e
[ 1562.600000] wlan0: No STA entry for own AP 00:19:7d:24:b2:0e
[ 1594.600000] wlan0: No STA entry for own AP 00:19:7d:24:b2:0e
[ 1626.600000] wlan0: No STA entry for own AP 00:19:7d:24:b2:0e
[ 1658.600000] wlan0: No STA entry for own AP 00:19:7d:24:b2:0e
[ 1687.336000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1687.352000] wlan0: Initial auth_alg=0
[ 1687.352000] wlan0: authenticate with AP 00:19:7d:24:b2:0e
[ 1687.360000] wlan0: RX authentication from 00:19:7d:24:b2:0e (alg=0 transaction=2 status=0)
[ 1687.360000] wlan0: authenticated
[ 1687.360000] wlan0: associate with AP 00:19:7d:24:b2:0e
[ 1687.560000] wlan0: associate with AP 00:19:7d:24:b2:0e
[ 1687.572000] wlan0: RX AssocResp from 00:19:7d:24:b2:0e (capab=0x401 status=0 aid=2)
[ 1687.572000] wlan0: associated
[ 1687.572000] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1687.576000] wlan0: association frame received from 00:19:7d:24:b2:0e, but not in associate state - ignored
[ 1687.608000] wlan0: association frame received from 00:19:7d:24:b2:0e, but not in associate state - ignored
[ 1687.636000] wlan0: association frame received from 00:19:7d:24:b2:0e, but not in associate state - ignored
[ 1687.644000] wlan0: association frame received from 00:19:7d:24:b2:0e, but not in associate state - ignored
[ 1698.444000] wlan0: no IPv6 routers present
[ 1769.572000] wlan0: No ProbeResp from current AP 00:19:7d:24:b2:0e - assume out of range
[ 1785.220000] ppdev0: registered pardevice
[ 1785.264000] ppdev0: unregistered pardevice
[ 1785.512000] audit(1192955470.112:4):  type=1503 operation="sysctl" requested_mask="r" denied_mask="r" name="/proc/sys/dev/parport/parport0/autoprobe" pid=5836 profile="/usr/sbin/cupsd"
[ 1785.560000] ppdev0: registered pardevice
[ 1785.612000] ppdev0: unregistered pardevice
[ 1785.624000] audit(1192955470.612:5):  type=1503 operation="sysctl" requested_mask="r" denied_mask="r" name="/proc/sys/dev/parport/parport0/autoprobe" pid=5840 profile="/usr/sbin/cupsd"
[ 1801.572000] wlan0: No STA entry for own AP 00:19:7d:24:b2:0e
[ 1833.428000] ppdev0: registered pardevice
[ 1833.476000] ppdev0: unregistered pardevice
[ 1833.572000] wlan0: No STA entry for own AP 00:19:7d:24:b2:0e
[ 1833.668000] audit(1192955518.615:6):  type=1503 operation="sysctl" requested_mask="r" denied_mask="r" name="/proc/sys/dev/parport/parport0/autoprobe" pid=5869 profile="/usr/sbin/cupsd"
[ 1833.712000] ppdev0: registered pardevice
[ 1833.764000] ppdev0: unregistered pardevice
[ 1833.776000] audit(1192955518.615:7):  type=1503 operation="sysctl" requested_mask="r" denied_mask="r" name="/proc/sys/dev/parport/parport0/autoprobe" pid=5873 profile="/usr/sbin/cupsd"
[ 1865.572000] wlan0: No STA entry for own AP 00:19:7d:24:b2:0e
[ 1897.572000] wlan0: No STA entry for own AP 00:19:7d:24:b2:0e
[ 1929.572000] wlan0: No STA entry for own AP 00:19:7d:24:b2:0e
[ 1961.572000] wlan0: No STA entry for own AP 00:19:7d:24:b2:0e
[ 2005.556000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2005.572000] wlan0: Initial auth_alg=0
[ 2005.572000] wlan0: authenticate with AP 00:19:7d:24:b2:0e
[ 2005.584000] wlan0: RX authentication from 00:19:7d:24:b2:0e (alg=0 transaction=2 status=0)
[ 2005.584000] wlan0: authenticated
[ 2005.584000] wlan0: associate with AP 00:19:7d:24:b2:0e
[ 2005.604000] wlan0: authentication frame received from 00:19:7d:24:b2:0e, but not in authenticate state - ignored
[ 2005.624000] wlan0: authentication frame received from 00:19:7d:24:b2:0e, but not in authenticate state - ignored
[ 2005.688000] wlan0: RX AssocResp from 00:19:7d:24:b2:0e (capab=0x401 status=0 aid=2)
[ 2005.688000] wlan0: associated
[ 2005.688000] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 2005.700000] wlan0: association frame received from 00:19:7d:24:b2:0e, but not in associate state - ignored
[ 2005.720000] wlan0: association frame received from 00:19:7d:24:b2:0e, but not in associate state - ignored
[ 2016.572000] wlan0: no IPv6 routers present
[ 2065.688000] wlan0: No ProbeResp from current AP 00:19:7d:24:b2:0e - assume out of range
[ 2097.688000] wlan0: No STA entry for own AP 00:19:7d:24:b2:0e
[ 2129.688000] wlan0: No STA entry for own AP 00:19:7d:24:b2:0e
[ 2161.688000] wlan0: No STA entry for own AP 00:19:7d:24:b2:0e
[ 2193.688000] wlan0: No STA entry for own AP 00:19:7d:24:b2:0e
[ 2225.688000] wlan0: No STA entry for own AP 00:19:7d:24:b2:0e
[ 2257.688000] wlan0: No STA entry for own AP 00:19:7d:24:b2:0e
[ 2289.688000] wlan0: No STA entry for own AP 00:19:7d:24:b2:0e
[ 2321.688000] wlan0: No STA entry for own AP 00:19:7d:24:b2:0e
[ 2353.688000] wlan0: No STA entry for own AP 00:19:7d:24:b2:0e
[ 2385.688000] wlan0: No STA entry for own AP 00:19:7d:24:b2:0e
[ 2417.688000] wlan0: No STA entry for own AP 00:19:7d:24:b2:0e
[ 2449.688000] wlan0: No STA entry for own AP 00:19:7d:24:b2:0e
[ 2481.688000] wlan0: No STA entry for own AP 00:19:7d:24:b2:0e
[ 2513.688000] wlan0: No STA entry for own AP 00:19:7d:24:b2:0e
[ 2545.688000] wlan0: No STA entry for own AP 00:19:7d:24:b2:0e
[ 2577.688000] wlan0: No STA entry for own AP 00:19:7d:24:b2:0e
[ 2609.688000] wlan0: No STA entry for own AP 00:19:7d:24:b2:0e
[ 2641.688000] wlan0: No STA entry for own AP 00:19:7d:24:b2:0e
[ 2702.148000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2702.164000] wlan0: Initial auth_alg=0
[ 2702.164000] wlan0: authenticate with AP 00:19:7d:24:b2:0e
[ 2702.168000] wlan0: RX authentication from 00:19:7d:24:b2:0e (alg=0 transaction=2 status=0)
[ 2702.168000] wlan0: authenticated
[ 2702.168000] wlan0: associate with AP 00:19:7d:24:b2:0e
[ 2702.204000] wlan0: RX AssocResp from 00:19:7d:24:b2:0e (capab=0x401 status=0 aid=2)
[ 2702.204000] wlan0: associated
[ 2702.204000] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 2702.204000] wlan0: association frame received from 00:19:7d:24:b2:0e, but not in associate state - ignored
[ 2702.216000] wlan0: association frame received from 00:19:7d:24:b2:0e, but not in associate state - ignored
[ 2702.216000] wlan0: association frame received from 00:19:7d:24:b2:0e, but not in associate state - ignored
[ 2702.220000] wlan0: association frame received from 00:19:7d:24:b2:0e, but not in associate state - ignored
[ 2702.232000] wlan0: association frame received from 00:19:7d:24:b2:0e, but not in associate state - ignored
[ 2702.232000] wlan0: association frame received from 00:19:7d:24:b2:0e, but not in associate state - ignored
[ 2712.408000] wlan0: no IPv6 routers present
[ 2866.204000] wlan0: No ProbeResp from current AP 00:19:7d:24:b2:0e - assume out of range
[ 2898.204000] wlan0: No STA entry for own AP 00:19:7d:24:b2:0e
[ 2930.204000] wlan0: No STA entry for own AP 00:19:7d:24:b2:0e
[ 2962.204000] wlan0: No STA entry for own AP 00:19:7d:24:b2:0e
[ 2994.204000] wlan0: No STA entry for own AP 00:19:7d:24:b2:0e
[ 3026.204000] wlan0: No STA entry for own AP 00:19:7d:24:b2:0e
[ 3058.204000] wlan0: No STA entry for own AP 00:19:7d:24:b2:0e
[ 3090.204000] wlan0: No STA entry for own AP 00:19:7d:24:b2:0e
[ 3122.204000] wlan0: No STA entry for own AP 00:19:7d:24:b2:0e
[ 3154.204000] wlan0: No STA entry for own AP 00:19:7d:24:b2:0e
[ 3186.204000] wlan0: No STA entry for own AP 00:19:7d:24:b2:0e
[ 3218.204000] wlan0: No STA entry for own AP 00:19:7d:24:b2:0e
[ 3250.204000] wlan0: No STA entry for own AP 00:19:7d:24:b2:0e
[ 3282.204000] wlan0: No STA entry for own AP 00:19:7d:24:b2:0e
[ 3314.204000] wlan0: No STA entry for own AP 00:19:7d:24:b2:0e
[ 3346.204000] wlan0: No STA entry for own AP 00:19:7d:24:b2:0e
[ 3378.204000] wlan0: No STA entry for own AP 00:19:7d:24:b2:0e
[ 3410.204000] wlan0: No STA entry for own AP 00:19:7d:24:b2:0e
[ 3442.204000] wlan0: No STA entry for own AP 00:19:7d:24:b2:0e
[ 3474.204000] wlan0: No STA entry for own AP 00:19:7d:24:b2:0e
[ 3506.204000] wlan0: No STA entry for own AP 00:19:7d:24:b2:0e
[ 3538.204000] wlan0: No STA entry for own AP 00:19:7d:24:b2:0e
[ 3570.204000] wlan0: No STA entry for own AP 00:19:7d:24:b2:0e
[ 3593.200000] usb 1-2: USB disconnect, address 3
[ 3602.204000] wlan0: No STA entry for own AP 00:19:7d:24:b2:0e
[ 3634.204000] wlan0: No STA entry for own AP 00:19:7d:24:b2:0e
[ 3666.204000] wlan0: No STA entry for own AP 00:19:7d:24:b2:0e
[ 3698.204000] wlan0: No STA entry for own AP 00:19:7d:24:b2:0e
[ 3730.204000] wlan0: No STA entry for own AP 00:19:7d:24:b2:0e
[ 3762.204000] wlan0: No STA entry for own AP 00:19:7d:24:b2:0e
[ 3794.204000] wlan0: No STA entry for own AP 00:19:7d:24:b2:0e
[ 3826.204000] wlan0: No STA entry for own AP 00:19:7d:24:b2:0e
[ 3858.204000] wlan0: No STA entry for own AP 00:19:7d:24:b2:0e
[ 3890.204000] wlan0: No STA entry for own AP 00:19:7d:24:b2:0e
[ 3922.204000] wlan0: No STA entry for own AP 00:19:7d:24:b2:0e
[ 3954.204000] wlan0: No STA entry for own AP 00:19:7d:24:b2:0e
[ 3977.236000] usb 1-2: new full speed USB device using uhci_hcd and address 4
[ 3977.396000] usb 1-2: configuration #1 chosen from 1 choice
[ 3977.400000] scsi1 : SCSI emulation for USB Mass Storage devices
[ 3977.400000] usb-storage: device found at 4
[ 3977.400000] usb-storage: waiting for device to settle before scanning
[ 3982.400000] usb-storage: device scan complete
[ 3982.404000] scsi 1:0:0:0: Direct-Access     LEXAR    JD EXPRESSION    1.00 PQ: 0 ANSI: 1 CCS
[ 3982.412000] sd 1:0:0:0: [sda] 2014992 512-byte hardware sectors (1032 MB)
[ 3982.416000] sd 1:0:0:0: [sda] Write Protect is off
[ 3982.416000] sd 1:0:0:0: [sda] Mode Sense: 23 00 00 00
[ 3982.416000] sd 1:0:0:0: [sda] Assuming drive cache: write through
[ 3982.428000] sd 1:0:0:0: [sda] 2014992 512-byte hardware sectors (1032 MB)
[ 3982.432000] sd 1:0:0:0: [sda] Write Protect is off
[ 3982.432000] sd 1:0:0:0: [sda] Mode Sense: 23 00 00 00
[ 3982.432000] sd 1:0:0:0: [sda] Assuming drive cache: write through
[ 3982.432000]  sda: sda1
[ 3982.436000] sd 1:0:0:0: [sda] Attached SCSI removable disk
[ 3982.436000] sd 1:0:0:0: Attached scsi generic sg0 type 0
[ 3986.204000] wlan0: No STA entry for own AP 00:19:7d:24:b2:0e
[ 4018.204000] wlan0: No STA entry for own AP 00:19:7d:24:b2:0e
[ 4050.204000] wlan0: No STA entry for own AP 00:19:7d:24:b2:0e
[ 4082.204000] wlan0: No STA entry for own AP 00:19:7d:24:b2:0e
[ 4114.204000] wlan0: No STA entry for own AP 00:19:7d:24:b2:0e
[ 4146.204000] wlan0: No STA entry for own AP 00:19:7d:24:b2:0e
```

---

### Post by Hero of Time on 2007-10-21
Check your encryption key. If you have none, do you use MAC filtering? Check your router logs to see what happens there when you try to associate with your router. It looks like there is a misconfiguration with the connection to your router. Have you also tried the network manager (apps > system > network)? It should work just fine.

Do note that even if you don't use any encryption, you need to enter that aswell. E.g. encryption=none.

---

### Post by ushills on 2007-10-22
Thanks, I use an orange Livebox that has MAC filtering by default, I cannot get the livebox to pair with the new card so have disabled MAC filtering.  It worked but now I have enable WPA and it will now not connect.

---

### Post by Hero of Time on 2007-10-23
See the nice WPA howto on top of this forum for how to get it working.

---

### Post by Zeedok on 2007-10-23
I had a problem with the wireless setup on my Xubuntu laptop after upgrading to Xubuntu 7.10 too. Not sure if your problem is the same but thought it might be worth a go.

With my Feisty Xubuntu I had some trouble setting up the network, so I used WICD which is a great program for setting up wireless networks etc. It seems to be easier and better featured than the Ubuntu (and now Xubuntu 7.10) network manager which has just been included in Xubuntu 7.10.

Once upgrading my wireless network was not working, though I quickly realised (through System -> Network) that my WPA passkey was not recorded. After entering this the network is fine.

The only problem I have is that the password is replaced by an incorrect one every time I reboot. This means I have to re-enter it everytime . . . It reminds me of dial-up!!

Does anyone have a solution for this glitch?

---

### Post by Hero of Time on 2007-10-23
Remove all the configuration you have about your wireless network (SSID, key, etc.) then reboot and try it again. It should work and remember your key. I have seen this issue before here where after the upgrade, the way the keys are saved is different thus not saving them correctly. Removing them and readd them should work.

---

### Post by ushills on 2007-11-01
solved as I installed the serial monkey drivers and disabled MAC filtering

---

