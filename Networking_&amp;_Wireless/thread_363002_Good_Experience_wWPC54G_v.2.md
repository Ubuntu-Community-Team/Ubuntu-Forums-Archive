---
title: "Good Experience w/WPC54G v.2?"
date: 2007-02-16
forum: Networking &amp; Wireless
---

### Post by Naubra on 2007-02-16
need some help with mine. can ping localhost, and scan for networks, but i cannot ping my router or beyond.  dhcp doesnt work, so i use static settings and it works fine on ethernet.

router is a linksys WRT54G, properly set up using WEP.


here's a list of everything i've done and my settings:

installed ndiswrapper from synaptic, and used it to install the 2nd newest (if the link from another thread is true) linksys drivers.

card is a WPC54G v.2




///////interfaces
```

auto lo
iface lo inet loopback

#auto eth0
#iface eth0 inet static
#address 192.168.1.24
#netmask 255.255.255.0
#network 192.168.1.1
#gateway 192.168.1.1

#auto eth1
#iface eth1 inet dhcp

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp



iface eth0 inet static
address 192.168.1.24
netmask 255.255.255.0
gateway 192.168.1.1

iface wlan0 inet static
address 192.168.1.24
netmask 255.255.255.0
gateway 192.168.1.1
wireless-essid entac
wireless-key xxxxxxxxxxxxxxxxxxxxxxx

auto wlan0
```

//////////////////////////////////////////

$ iwconfig

```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11b+/g+  ESSID:"entac"  Nickname:"acx v0.3.21"
          Mode:Managed  Frequency:2.422 GHz  Access Point: 00:16:B6:31:F4:DA   
          Bit Rate:11 Mb/s   Tx-Power=15 dBm   Sensitivity=1/3  
          Retry min limit:7   RTS thr:off   
          Power Management:off
          Link Quality=47/100  Signal level=26/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.
```

/////////////////////////////////////////////

```
 sudo echo ndiswrapper >> /etc/modules
bash: /etc/modules: [COLOR="Red"]**Permission denied**[/COLOR]
```


////////////////////////////////////////////////


```
 sudo iwconfig wlan0 channel 3 essid entac mode Managed
```

////////////////////////////////////////////////////


```
resolv.conf is
nameserver xx.xxx.x.xx
nameserver xx.xxx.x.xx
search entac

```
///////////////////////////////////////////////////////////

 lspci | grep ontroller
```

00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #1) (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M6 LY
02:00.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)
07:00.0 Network controller: Texas Instruments ACX 111 54Mbps Wireless Interface

```

//////////////////////////////////////////////////////

dmesg

```
 UTC 2006 (Ubuntu 2.6.17-10.33-generic)
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[17179569.184000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000000ffe2800 (usable)
[17179569.184000]  BIOS-e820: 000000000ffe2800 - 0000000010000000 (reserved)
[17179569.184000]  BIOS-e820: 00000000feda0000 - 00000000fee00000 (reserved)
[17179569.184000]  BIOS-e820: 00000000ffb80000 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 255MB LOWMEM available.
[17179569.184000] On node 0 totalpages: 65506
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   Normal zone: 61410 pages, LIFO batch:15
[17179569.184000] DMI 2.3 present.
[17179569.184000] ACPI: RSDP (v000 DELL                                  ) @ 0x000fde50
[17179569.184000] ACPI: RSDT (v001 DELL    CPi R   0x27d2020d ASL  0x00000061) @ 0x000fde64
[17179569.184000] ACPI: FADT (v001 DELL    CPi R   0x27d2020d ASL  0x00000061) @ 0x000fde90
[17179569.184000] ACPI: DSDT (v001 INT430 SYSFexxx 0x00001001 MSFT 0x0100000d) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x808
[17179569.184000] Allocating PCI resources starting at 20000000 (gap: 10000000:eeda0000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hda1 ro quiet splash
[17179569.184000] Local APIC disabled by BIOS (or by default) -- you can enable it with "lapic"
[17179569.184000] mapped APIC to ffffd000 (0120a000)
[17179569.184000] Enabling fast FPU save and restore... done.
[17179569.184000] Enabling unmasked SIMD FPU exception support... done.
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 1024 (order: 10, 4096 bytes)
[17179569.184000] Detected 996.896 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179571.892000] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179571.892000] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
[17179571.908000] Memory: 249576k/262024k available (1910k kernel code, 11948k reserved, 1070k data, 308k init, 0k highmem)
[17179571.908000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179571.988000] Calibrating delay using timer specific routine.. 1995.59 BogoMIPS (lpj=3991191)
[17179571.988000] Security Framework v1.0.0 initialized
[17179571.988000] SELinux:  Disabled at boot.
[17179571.988000] Mount-cache hash table entries: 512
[17179571.988000] CPU: After generic identify, caps: 0383f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[17179571.988000] CPU: After vendor identify, caps: 0383f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[17179571.988000] CPU: L1 I cache: 16K, L1 D cache: 16K
[17179571.988000] CPU: L2 cache: 512K
[17179571.988000] CPU: After all inits, caps: 0383f9ff 00000000 00000000 00000040 00000000 00000000 00000000
[17179571.988000] Checking 'hlt' instruction... OK.
[17179572.004000] SMP alternatives: switching to UP code
[17179572.004000] Freeing SMP alternatives: 16k freed
[17179572.004000] checking if image is initramfs... it is
[17179572.964000] Freeing initrd memory: 5912k freed
[17179572.964000] ACPI: Core revision 20060707
[17179572.968000] ACPI: Looking for DSDT ... not found!
[17179573.000000] ACPI: setting ELCR to 0200 (from 0800)
[17179573.624000] CPU0: Intel(R) Pentium(R) III Mobile CPU      1000MHz stepping 01
[17179573.624000] SMP motherboard not detected.
[17179573.624000] Local APIC not detected. Using dummy APIC emulation.
[17179573.624000] Brought up 1 CPUs
[17179573.624000] migration_cost=0
[17179573.624000] NET: Registered protocol family 16
[17179573.624000] EISA bus registered
[17179573.624000] ACPI: bus type pci registered
[17179573.636000] PCI: PCI BIOS revision 2.10 entry at 0xfbfee, last bus=2
[17179573.636000] PCI: Using configuration type 1
[17179573.636000] Setting up standard PCI resources
[17179573.668000] ACPI: Interpreter enabled
[17179573.668000] ACPI: Using PIC for interrupt routing
[17179573.676000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179573.676000] PCI: Probing PCI hardware (bus 00)
[17179573.676000] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[17179573.748000] PCI quirk: region 0800-087f claimed by ICH4 ACPI/GPIO/TCO
[17179573.748000] PCI quirk: region 0880-08bf claimed by ICH4 GPIO
[17179573.748000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
[17179573.748000] Boot video device is 0000:01:00.0
[17179573.748000] PCI: Transparent bridge - 0000:00:1e.0
[17179573.748000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179573.864000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[17179573.868000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[17179573.868000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[17179573.868000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[17179573.872000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[17179573.872000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]
[17179573.876000] ACPI: Power Resource [PADA] (on)
[17179573.876000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179573.876000] pnp: PnP ACPI init
[17179574.084000] pnp: PnP ACPI: found 17 devices
[17179574.084000] PnPBIOS: Disabled by ACPI PNP
[17179574.084000] PCI: Using ACPI for IRQ routing
[17179574.084000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179574.120000] pnp: 00:02: ioport range 0x4d0-0x4d1 has been reserved
[17179574.120000] pnp: 00:02: ioport range 0x800-0x805 could not be reserved
[17179574.120000] pnp: 00:02: ioport range 0x808-0x80f could not be reserved
[17179574.120000] pnp: 00:03: ioport range 0x806-0x807 has been reserved
[17179574.120000] pnp: 00:03: ioport range 0x810-0x85f could not be reserved
[17179574.120000] pnp: 00:03: ioport range 0x860-0x87f has been reserved
[17179574.120000] pnp: 00:03: ioport range 0x880-0x8bf has been reserved
[17179574.120000] pnp: 00:03: ioport range 0x8c0-0x8df has been reserved
[17179574.120000] pnp: 00:03: ioport range 0x8e0-0x8ff has been reserved
[17179574.120000] pnp: 00:04: ioport range 0xf000-0xf0fe has been reserved
[17179574.120000] pnp: 00:04: ioport range 0xf100-0xf1fe has been reserved
[17179574.120000] pnp: 00:04: ioport range 0xf200-0xf2fe has been reserved
[17179574.120000] pnp: 00:04: ioport range 0xf400-0xf4fe has been reserved
[17179574.120000] pnp: 00:04: ioport range 0xf500-0xf5fe has been reserved
[17179574.120000] pnp: 00:04: ioport range 0xf600-0xf6fe has been reserved
[17179574.120000] pnp: 00:04: ioport range 0xf800-0xf8fe has been reserved
[17179574.120000] pnp: 00:04: ioport range 0xf900-0xf9fe has been reserved
[17179574.120000] pnp: 00:09: ioport range 0x900-0x91f has been reserved
[17179574.120000] pnp: 00:09: ioport range 0x3f0-0x3f1 has been reserved
[17179574.120000] pnp: 00:0f: ioport range 0xbf40-0xbf5f has been reserved
[17179574.120000] pnp: 00:0f: ioport range 0xbf20-0xbf3f has been reserved
[17179574.120000] PCI: Bridge: 0000:00:01.0
[17179574.120000]   IO window: c000-cfff
[17179574.120000]   MEM window: fc000000-fdffffff
[17179574.120000]   PREFETCH window: e0000000-e7ffffff
[17179574.120000] PCI: Bus 3, cardbus bridge: 0000:02:01.0
[17179574.120000]   IO window: 0000e000-0000e0ff
[17179574.120000]   IO window: 0000e400-0000e4ff
[17179574.120000]   PREFETCH window: 20000000-21ffffff
[17179574.120000]   MEM window: f4000000-f5ffffff
[17179574.120000] PCI: Bus 7, cardbus bridge: 0000:02:01.1
[17179574.120000]   IO window: 0000e800-0000e8ff
[17179574.120000]   IO window: 00001000-000010ff
[17179574.120000]   PREFETCH window: 22000000-23ffffff
[17179574.120000]   MEM window: f6000000-f7ffffff
[17179574.120000] PCI: Bridge: 0000:00:1e.0
[17179574.120000]   IO window: e000-ffff
[17179574.120000]   MEM window: f4000000-fbffffff
[17179574.120000]   PREFETCH window: 20000000-24ffffff
[17179574.120000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[17179574.120000] PCI: Enabling device 0000:02:01.0 (0000 -> 0003)
[17179574.120000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[17179574.120000] PCI: setting IRQ 11 as level-triggered
[17179574.120000] ACPI: PCI Interrupt 0000:02:01.0[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[17179574.120000] PCI: Enabling device 0000:02:01.1 (0000 -> 0003)
[17179574.120000] ACPI: PCI Interrupt 0000:02:01.1[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[17179574.120000] NET: Registered protocol family 2
[17179574.156000] IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
[17179574.156000] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
[17179574.156000] TCP bind hash table entries: 4096 (order: 3, 32768 bytes)
[17179574.156000] TCP: Hash tables configured (established 8192 bind 4096)
[17179574.156000] TCP reno registered
[17179574.156000] audit: initializing netlink socket (disabled)
[17179574.156000] audit(1171634638.156:1): initialized
[17179574.156000] VFS: Disk quotas dquot_6.5.1
[17179574.156000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179574.156000] Initializing Cryptographic API
[17179574.156000] io scheduler noop registered
[17179574.156000] io scheduler anticipatory registered
[17179574.156000] io scheduler deadline registered
[17179574.156000] io scheduler cfq registered (default)
[17179574.156000] isapnp: Scanning for PnP cards...
[17179574.508000] isapnp: No Plug & Play device found
[17179574.556000] Real Time Clock Driver v1.12ac
[17179574.556000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[17179574.560000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179574.560000] 00:0d: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179574.560000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 11
[17179574.560000] ACPI: PCI Interrupt 0000:00:1f.6[B] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[17179574.560000] ACPI: PCI interrupt for device 0000:00:1f.6 disabled
[17179574.560000] mice: PS/2 mouse device common for all mice
[17179574.560000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179574.564000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179574.564000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179574.564000] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[17179574.568000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179574.568000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179574.568000] EISA: Probing bus 0 at eisa.0
[17179574.568000] Cannot allocate resource for EISA slot 1
[17179574.568000] EISA: Detected 0 cards.
[17179574.568000] TCP bic registered
[17179574.568000] NET: Registered protocol family 1
[17179574.568000] NET: Registered protocol family 8
[17179574.568000] NET: Registered protocol family 20
[17179574.568000] Using IPI No-Shortcut mode
[17179574.568000] ACPI: (supports S0 S1 S3 S4 S5)
[17179574.568000] Freeing unused kernel memory: 308k freed
[17179574.576000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179575.812000] Capability LSM initialized
[17179576.028000] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[17179576.048000] ACPI: Thermal Zone [THM] (56 C)
[17179576.720000] ICH3M: IDE controller at PCI slot 0000:00:1f.1
[17179576.720000] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
[17179576.720000] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[17179576.720000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[17179576.720000] ICH3M: chipset revision 2
[17179576.720000] ICH3M: not 100% native mode: will probe irqs later
[17179576.720000]     ide0: BM-DMA at 0xbfa0-0xbfa7, BIOS settings: hda:DMA, hdb:pio
[17179576.720000]     ide1: BM-DMA at 0xbfa8-0xbfaf, BIOS settings: hdc:DMA, hdd:pio
[17179576.720000] Probing IDE interface ide0...
[17179577.008000] hda: HITACHI_DK23DA-20, ATA DISK drive
[17179577.680000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179577.684000] Probing IDE interface ide1...
[17179578.420000] hdc: LG DVD-ROM DRN-8080B, ATAPI CD/DVD-ROM drive
[17179579.092000] ide1 at 0x170-0x177,0x376 on irq 15
[17179579.104000] hda: max request size: 128KiB
[17179579.120000] hda: 39070080 sectors (20003 MB) w/2048KiB Cache, CHS=38760/16/63, UDMA(100)
[17179579.120000] hda: cache flushes supported
[17179579.120000]  hda: hda1 hda2 < hda5 >
[17179579.204000] hdc: ATAPI 24X DVD-ROM drive, 512kB Cache, DMA
[17179579.204000] Uniform CD-ROM driver Revision: 3.20
[17179579.452000] usbcore: registered new driver usbfs
[17179579.452000] usbcore: registered new driver hub
[17179579.456000] USB Universal Host Controller Interface driver v3.0
[17179579.456000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[17179579.456000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[17179579.456000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[17179579.460000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[17179579.460000] uhci_hcd 0000:00:1d.0: irq 11, io base 0x0000bf80
[17179579.460000] usb usb1: configuration #1 chosen from 1 choice
[17179579.460000] hub 1-0:1.0: USB hub found
[17179579.460000] hub 1-0:1.0: 2 ports detected
[17179579.596000] Attempting manual resume
[17179579.652000] kjournald starting.  Commit interval 5 seconds
[17179579.652000] EXT3-fs: mounted filesystem with ordered data mode.
[17179579.804000] usb 1-1: new full speed USB device using uhci_hcd and address 2
[17179579.980000] usb 1-1: configuration #1 chosen from 1 choice
[17179594.288000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179594.296000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179594.336000] hw_random: RNG not detected
[17179594.360000] Linux agpgart interface v0.101 (c) Dave Jones
[17179594.364000] agpgart: Detected an Intel 830M Chipset.
[17179594.376000] agpgart: AGP aperture is 256M @ 0xd0000000
[17179595.532000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[17179595.532000] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[17179595.532000] 3c59x: Donald Becker and others. www.scyld.com/network/vortex.html
[17179595.532000] 0000:02:00.0: 3Com PCI 3c905C Tornado at d08dcc00.
[17179595.604000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[17179595.604000] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[17179596.020000] Synaptics Touchpad, model: 1, fw: 5.7, id: 0x9b48b1, caps: 0x804793/0x0
[17179596.020000] serio: Synaptics pass-through port at isa0060/serio1/input0
[17179596.064000] input: SynPS/2 Synaptics TouchPad as /class/input/input1
[17179596.084000] input: PC Speaker as /class/input/input2
[17179596.172000] intel8x0_measure_ac97_clock: measured 55459 usecs
[17179596.172000] intel8x0: clocking to 48000
[17179596.172000] ACPI: PCI Interrupt 0000:02:01.0[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[17179596.172000] Yenta: CardBus bridge found at 0000:02:01.0 [1028:00e3]
[17179596.172000] Yenta: Using CSCINT to route CSC interrupts to PCI
[17179596.172000] Yenta: Routing CardBus interrupts to PCI
[17179596.172000] Yenta TI: socket 0000:02:01.0, mfunc 0x01261222, devctl 0x64
[17179596.228000] Floppy drive(s): fd0 is 1.44M
[17179596.248000] FDC 0 is a post-1991 82077
[17179596.324000] ts: Compaq touchscreen protocol output
[17179596.404000] Yenta: ISA IRQ mask 0x04b8, PCI irq 11
[17179596.404000] Socket status: 30000006
[17179596.404000] pcmcia: parent PCI bridge I/O window: 0xe000 - 0xffff
[17179596.404000] cs: IO port probe 0xe000-0xffff: clean.
[17179596.404000] pcmcia: parent PCI bridge Memory window: 0xf4000000 - 0xfbffffff
[17179596.404000] pcmcia: parent PCI bridge Memory window: 0x20000000 - 0x24ffffff
[17179596.404000] ACPI: PCI Interrupt 0000:02:01.1[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[17179596.404000] Yenta: CardBus bridge found at 0000:02:01.1 [1028:00e3]
[17179596.404000] Yenta: Using CSCINT to route CSC interrupts to PCI
[17179596.404000] Yenta: Routing CardBus interrupts to PCI
[17179596.404000] Yenta TI: socket 0000:02:01.1, mfunc 0x01261222, devctl 0x64
[17179596.440000] parport: PnPBIOS parport detected.
[17179596.440000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[17179596.636000] Yenta: ISA IRQ mask 0x0438, PCI irq 11
[17179596.636000] Socket status: 30000020
[17179596.636000] pcmcia: parent PCI bridge I/O window: 0xe000 - 0xffff
[17179596.636000] cs: IO port probe 0xe000-0xffff: clean.
[17179596.636000] pcmcia: parent PCI bridge Memory window: 0xf4000000 - 0xfbffffff
[17179596.636000] pcmcia: parent PCI bridge Memory window: 0x20000000 - 0x24ffffff
[17179597.292000] usbcore: registered new driver hiddev
[17179597.356000] input: Razer Razer Copperhead Laser Mouse as /class/input/input3
[17179597.356000] input: USB HID v1.00 Mouse [Razer Razer Copperhead Laser Mouse] on usb-0000:00:1d.0-1
[17179597.360000] input: Razer Razer Copperhead Laser Mouse as /class/input/input4
[17179597.364000] input: USB HID v0.01 Keyboard [Razer Razer Copperhead Laser Mouse] on usb-0000:00:1d.0-1
[17179597.364000] usbcore: registered new driver usbhid
[17179597.364000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[17179597.388000] pccard: CardBus card inserted into slot 1
[17179597.828000] cs: IO port probe 0x100-0x3af: clean.
[17179597.828000] cs: IO port probe 0x3e0-0x4ff: clean.
[17179597.828000] cs: IO port probe 0x820-0x8ff: clean.
[17179597.828000] cs: IO port probe 0xc00-0xcf7: clean.
[17179597.828000] cs: IO port probe 0xa00-0xaff: clean.
[17179597.828000] cs: IO port probe 0x100-0x3af: clean.
[17179597.832000] cs: IO port probe 0x3e0-0x4ff: clean.
[17179597.832000] cs: IO port probe 0x820-0x8ff: clean.
[17179597.832000] cs: IO port probe 0xc00-0xcf7: clean.
[17179597.832000] cs: IO port probe 0xa00-0xaff: clean.
[17179598.040000] acx: Loaded combined PCI/USB driver, firmware_ver=default
[17179598.040000] acx: compiled to use 32bit I/O access. I/O timing issues might occur, such as non-working firmware upload. Report them
[17179598.044000] PCI: Enabling device 0000:07:00.0 (0000 -> 0002)
[17179598.044000] ACPI: PCI Interrupt 0000:07:00.0[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[17179598.044000] PCI: Setting latency timer of device 0000:07:00.0 to 64
[17179598.044000] acx: found ACX111-based wireless network card at 0000:07:00.0, irq:11, phymem1:0xF6020000, phymem2:0xF6000000, mem1:0xd0a00000, mem1_size:8192, mem2:0xd0ac0000, mem2_size:131072
[17179599.004000] acx: form factor 0x01 ((mini-)PCI / CardBus), radio type 0x16 (Radia), EEPROM version 0x05, uploaded firmware 'Rev 1.2.1.34' (0x03010101)
[17179599.004000] acx v0.3.21: net device wlan0, driver compiled against wireless extensions 20 and Linux 2.6.17-10-generic
[17179599.004000] usbcore: registered new driver acx_usb
[17179599.056000] wlan0 (WE) : Driver using old /proc/net/wireless support, please fix driver !
[17179600.800000] lp0: using parport0 (interrupt-driven).
[17179600.844000] Adding 746980k swap on /dev/disk/by-uuid/38c724d4-1b1c-4520-94c4-d5d0fd6d57e9.  Priority:-1 extents:1 across:746980k
[17179600.884000] IBM TrackPoint firmware: 0x0b, buttons: 2/3
[17179600.932000] EXT3 FS on hda1, internal journal
[17179601.128000] input: TPPS/2 IBM TrackPoint as /class/input/input5
[17179603.304000] ACPI: AC Adapter [AC] (on-line)
[17179603.376000] ACPI: Battery Slot [BAT0] (battery absent)
[17179603.376000] ACPI: Battery Slot [BAT1] (battery absent)
[17179603.408000] ACPI: Lid Switch [LID]
[17179603.408000] ACPI: Power Button (CM) [PBTN]
[17179603.408000] ACPI: Sleep Button (CM) [SBTN]
[17179603.564000] ACPI: ACPI Dock Station Driver 
[17179603.688000] ibm_acpi: ec object not found
[17179603.736000] pcc_acpi: loading...
[17179603.936000] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[17179607.608000] [drm] Initialized drm 1.0.1 20051102
[17179607.752000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[17179607.756000] [drm] Initialized radeon 1.25.0 20060524 on minor 0
[17179608.720000] mtrr: 0xe0000000,0x8000000 overlaps existing 0xe0000000,0x1000000
[17179608.720000] mtrr: 0xe0000000,0x8000000 overlaps existing 0xe0000000,0x1000000
[17179608.720000] mtrr: 0xe0000000,0x8000000 overlaps existing 0xe0000000,0x1000000
[17179608.720000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[17179608.720000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 1x mode
[17179608.720000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 1x mode
[17179608.904000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[17179608.904000] apm: overridden by ACPI.
[17179609.012000] [drm] Setting GART location based on new memory map
[17179609.012000] [drm] writeback test succeeded in 1 usecs
[17179622.596000] Bluetooth: Core ver 2.8
[17179622.596000] NET: Registered protocol family 31
[17179622.596000] Bluetooth: HCI device and connection manager initialized
[17179622.596000] Bluetooth: HCI socket layer initialized
[17179622.664000] Bluetooth: L2CAP ver 2.8
[17179622.664000] Bluetooth: L2CAP socket layer initialized
[17179622.704000] Bluetooth: RFCOMM socket layer initialized
[17179622.704000] Bluetooth: RFCOMM TTY layer initialized
[17179622.704000] Bluetooth: RFCOMM ver 1.7
[17179624.612000] NET: Registered protocol family 10
[17179624.612000] lo: Disabled Privacy Extensions
[17179624.612000] IPv6 over IPv4 tunneling driver
[17179630.188000] ISO 9660 Extensions: Microsoft Joliet Level 3
[17179630.428000] ISOFS: changing to secondary root
[17179635.008000] wlan0: no IPv6 routers present
[17179635.648000] acx: got IV_ICV_Failure IRQ(s)
[17179635.648000] acx: got IV_ICV_Failure IRQ(s)
[17179635.748000] acx: got IV_ICV_Failure IRQ(s)
[17179635.752000] acx: got IV_ICV_Failure IRQ(s)
[17179635.756000] acx: got IV_ICV_Failure IRQ(s)
[17179635.760000] acx: got IV_ICV_Failure IRQ(s)
[17179635.760000] acx: got IV_ICV_Failure IRQ(s)
[17179635.772000] acx: got IV_ICV_Failure IRQ(s)
[17179635.776000] acx: got IV_ICV_Failure IRQ(s)
[17179635.780000] acx: got IV_ICV_Failure IRQ(s)
[17179635.784000] acx: got IV_ICV_Failure IRQ(s)
[17179689.908000] acx: got IV_ICV_Failure IRQ(s)
[17179696.152000] acx: got IV_ICV_Failure IRQ(s)
[17179714.072000] acx: got IV_ICV_Failure IRQ(s)
[17179717.040000] acx: got IV_ICV_Failure IRQ(s)
[17179722.976000] acx: got IV_ICV_Failure IRQ(s)
[17179779.428000] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[17179779.428000] eth0:  setting full-duplex.
[17179790.244000] eth0: no IPv6 routers present
[17184257.556000] acx: got IV_ICV_Failure IRQ(s)
[17184257.748000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[17184259.504000] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[17184269.752000] wlan0: no IPv6 routers present
[17184357.092000] acx: got IV_ICV_Failure IRQ(s)
[17184357.096000] acx: got IV_ICV_Failure IRQ(s)
[17184357.100000] acx: got IV_ICV_Failure IRQ(s)
[17184357.104000] acx: got IV_ICV_Failure IRQ(s)
[17184357.108000] acx: got IV_ICV_Failure IRQ(s)
[17184357.112000] acx: got IV_ICV_Failure IRQ(s)
[17184357.116000] acx: got IV_ICV_Failure IRQ(s)
[17184357.120000] acx: got IV_ICV_Failure IRQ(s)
[17184357.124000] acx: got IV_ICV_Failure IRQ(s)
[17184357.128000] acx: got IV_ICV_Failure IRQ(s)
[17184357.132000] acx: got IV_ICV_Failure IRQ(s)
[17184366.512000] NET: Registered protocol family 17
[17184478.120000] acx: got IV_ICV_Failure IRQ(s)
[17184478.120000] acx: got IV_ICV_Failure IRQ(s)
[17184478.124000] acx: got IV_ICV_Failure IRQ(s)
[17184478.128000] acx: got IV_ICV_Failure IRQ(s)
[17184478.132000] acx: got IV_ICV_Failure IRQ(s)
[17184478.136000] acx: got IV_ICV_Failure IRQ(s)
[17184478.140000] acx: got IV_ICV_Failure IRQ(s)
[17184478.144000] acx: got IV_ICV_Failure IRQ(s)
[17184478.148000] acx: got IV_ICV_Failure IRQ(s)
[17184478.152000] acx: got IV_ICV_Failure IRQ(s)
[17184599.032000] acx: got IV_ICV_Failure IRQ(s)
[17184599.036000] acx: got IV_ICV_Failure IRQ(s)
[17184599.040000] acx: got IV_ICV_Failure IRQ(s)
[17184599.044000] acx: got IV_ICV_Failure IRQ(s)
[17184599.048000] acx: got IV_ICV_Failure IRQ(s)
[17184599.052000] acx: got IV_ICV_Failure IRQ(s)
[17184599.056000] acx: got IV_ICV_Failure IRQ(s)
[17184599.060000] acx: got IV_ICV_Failure IRQ(s)
[17184599.064000] acx: got IV_ICV_Failure IRQ(s)
[17184599.064000] acx: got IV_ICV_Failure IRQ(s)
[17184599.068000] acx: got IV_ICV_Failure IRQ(s)
[17184662.100000] acx: got IV_ICV_Failure IRQ(s)
[17184720.052000] acx: got IV_ICV_Failure IRQ(s)
[17184720.056000] acx: got IV_ICV_Failure IRQ(s)
[17184720.060000] acx: got IV_ICV_Failure IRQ(s)
[17184720.064000] acx: got IV_ICV_Failure IRQ(s)
[17184720.068000] acx: got IV_ICV_Failure IRQ(s)
[17184720.072000] acx: got IV_ICV_Failure IRQ(s)
[17184720.076000] acx: got IV_ICV_Failure IRQ(s)
[17184720.080000] acx: got IV_ICV_Failure IRQ(s)
[17184720.084000] acx: got IV_ICV_Failure IRQ(s)
[17184720.088000] acx: got IV_ICV_Failure IRQ(s)
[17184720.092000] acx: got IV_ICV_Failure IRQ(s)
[17184841.076000] acx: got IV_ICV_Failure IRQ(s)
[17184841.080000] acx: got IV_ICV_Failure IRQ(s)
[17184841.080000] acx: got IV_ICV_Failure IRQ(s)
[17184841.084000] acx: got IV_ICV_Failure IRQ(s)
[17184841.088000] acx: got IV_ICV_Failure IRQ(s)
[17184841.092000] acx: got IV_ICV_Failure IRQ(s)
[17184841.096000] acx: got IV_ICV_Failure IRQ(s)
[17184841.100000] acx: got IV_ICV_Failure IRQ(s)
[17184841.104000] acx: got IV_ICV_Failure IRQ(s)
[17184841.108000] acx: got IV_ICV_Failure IRQ(s)
[17184841.112000] acx: got IV_ICV_Failure IRQ(s)
[17184841.116000] acx: got IV_ICV_Failure IRQ(s)
[17184941.208000] acx: got IV_ICV_Failure IRQ(s)
[17184962.096000] acx: got IV_ICV_Failure IRQ(s)
[17184962.100000] acx: got IV_ICV_Failure IRQ(s)
[17184962.104000] acx: got IV_ICV_Failure IRQ(s)
[17184962.108000] acx: got IV_ICV_Failure IRQ(s)
[17184962.108000] acx: got IV_ICV_Failure IRQ(s)
[17184962.112000] acx: got IV_ICV_Failure IRQ(s)
[17184962.116000] acx: got IV_ICV_Failure IRQ(s)
[17184962.120000] acx: got IV_ICV_Failure IRQ(s)
[17184962.124000] acx: got IV_ICV_Failure IRQ(s)
[17184962.128000] acx: got IV_ICV_Failure IRQ(s)
[17184962.132000] acx: got IV_ICV_Failure IRQ(s)
[17184968.852000] acx: got IV_ICV_Failure IRQ(s)
[17184969.568000] acx: got IV_ICV_Failure IRQ(s)
[17184970.284000] acx: got IV_ICV_Failure IRQ(s)
[17184983.668000] ndiswrapper version 1.22 loaded (preempt=no,smp=yes)
[17185083.116000] acx: got IV_ICV_Failure IRQ(s)
[17185083.120000] acx: got IV_ICV_Failure IRQ(s)
[17185083.124000] acx: got IV_ICV_Failure IRQ(s)
[17185083.128000] acx: got IV_ICV_Failure IRQ(s)
[17185083.132000] acx: got IV_ICV_Failure IRQ(s)
[17185083.136000] acx: got IV_ICV_Failure IRQ(s)
[17185083.140000] acx: got IV_ICV_Failure IRQ(s)
[17185083.140000] acx: got IV_ICV_Failure IRQ(s)
[17185083.144000] acx: got IV_ICV_Failure IRQ(s)
[17185083.148000] acx: got IV_ICV_Failure IRQ(s)


```

---

### Post by Naubra on 2007-02-16
Still clueless. Any ideas?

---

### Post by Naubra on 2007-02-16
Hopeful bump, up you go sad little thread.

---

### Post by dmizer on 2007-02-17
i wrote a howto on this.  it's one of two threads that appear by searching with the following terms:
howto wpc54g

here is the thread: [http://www.ubuntuforums.org/showthread.php?t=324148](http://www.ubuntuforums.org/showthread.php?t=324148)

if you have any problems with it, please post in that thread as i have it marked as watched, so i will get a notification.

---

