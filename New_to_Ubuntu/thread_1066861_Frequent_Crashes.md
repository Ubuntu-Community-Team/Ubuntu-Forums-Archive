---
title: "Frequent Crashes"
date: 2009-02-11
forum: New to Ubuntu
---

### Post by fairy._.queen on 2009-02-11
Hi all!
I'm experiencing a LOT of kernel crashes since upgrading to Intrepid. By kernel crashes I mean that while I'm working on any application, my session suddenly restarts as if I had hit ctrl+alt+backspace.
This happens with any kind of application, sometimes even just after inserting username and password, when kde is still loading.
Have you any hints for that?

---

### Post by Crafty Kisses on 2009-02-11
Have you looked at your kernel logs? It would probably be better if you provided us more information, lets start with the kernel logs, you can run the following: ```
sudo nano /var/log/kern.log
```Please post the results back here on the forum, and I or somebody else can help you further.

---

### Post by fairy._.queen on 2009-02-15
Thanks for replying.
Below is the result of tail /var/log/kernel.log - I must add I've had 4 crashes in 45 mins just today... :-(
```
Feb 15 13:45:17 Enterprise kernel: [   29.809166] [drm] Initialized i915 1.6.0 20060119 on minor 0
Feb 15 13:45:17 Enterprise kernel: [   29.809183] pci 0000:00:02.1: setting latency timer to 64
Feb 15 13:45:17 Enterprise kernel: [   29.810676] [drm] Initialized i915 1.6.0 20060119 on minor 1
Feb 15 13:45:21 Enterprise kernel: [   32.936037] eth1: no IPv6 routers present
Feb 15 13:47:08 Enterprise kernel: [  139.968201] ppdev0: registered pardevice
Feb 15 13:47:08 Enterprise kernel: [  140.016070] ppdev0: unregistered pardevice
Feb 15 13:47:08 Enterprise kernel: [  140.436474] ppdev0: registered pardevice
Feb 15 13:47:08 Enterprise kernel: [  140.500713] ppdev0: unregistered pardevice
Feb 15 13:47:09 Enterprise kernel: [  141.554060] ppdev0: registered pardevice
Feb 15 13:47:09 Enterprise kernel: [  141.600256] ppdev0: unregistered pardevice

```

---

### Post by fairy._.queen on 2009-02-15
More output here: (the outs i posted were registered just after a crash)

```
uhci_hcd 0000:00:1d.0: irq 11, io base 0x0000bf80
Feb 15 13:45:11 Enterprise kernel: [    3.200605] usb usb2: configuration #1 chosen from 1 choice
Feb 15 13:45:11 Enterprise kernel: [    3.200639] hub 2-0:1.0: USB hub found
Feb 15 13:45:11 Enterprise kernel: [    3.200648] hub 2-0:1.0: 2 ports detected
Feb 15 13:45:11 Enterprise kernel: [    3.408607] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
Feb 15 13:45:11 Enterprise kernel: [    3.408614] uhci_hcd 0000:00:1d.1: PCI INT B -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11
Feb 15 13:45:11 Enterprise kernel: [    3.408629] uhci_hcd 0000:00:1d.1: setting latency timer to 64
Feb 15 13:45:11 Enterprise kernel: [    3.408633] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Feb 15 13:45:11 Enterprise kernel: [    3.408665] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
Feb 15 13:45:11 Enterprise kernel: [    3.408692] uhci_hcd 0000:00:1d.1: irq 11, io base 0x0000bf40
Feb 15 13:45:11 Enterprise kernel: [    3.408810] usb usb3: configuration #1 chosen from 1 choice
Feb 15 13:45:11 Enterprise kernel: [    3.408842] hub 3-0:1.0: USB hub found
Feb 15 13:45:11 Enterprise kernel: [    3.408852] hub 3-0:1.0: 2 ports detected
Feb 15 13:45:11 Enterprise kernel: [    3.512574] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
Feb 15 13:45:11 Enterprise kernel: [    3.512580] uhci_hcd 0000:00:1d.2: PCI INT C -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
Feb 15 13:45:11 Enterprise kernel: [    3.512594] uhci_hcd 0000:00:1d.2: setting latency timer to 64
Feb 15 13:45:11 Enterprise kernel: [    3.512598] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Feb 15 13:45:11 Enterprise kernel: [    3.512629] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
Feb 15 13:45:11 Enterprise kernel: [    3.512655] uhci_hcd 0000:00:1d.2: irq 11, io base 0x0000bf20
Feb 15 13:45:11 Enterprise kernel: [    3.512772] usb usb4: configuration #1 chosen from 1 choice
Feb 15 13:45:11 Enterprise kernel: [    3.512805] hub 4-0:1.0: USB hub found
Feb 15 13:45:11 Enterprise kernel: [    3.512814] hub 4-0:1.0: 2 ports detected
Feb 15 13:45:11 Enterprise kernel: [    3.520094] usb 2-2: new full speed USB device using uhci_hcd and address 2
Feb 15 13:45:11 Enterprise kernel: [    3.596010] Marking TSC unstable due to TSC halts in idle
Feb 15 13:45:11 Enterprise kernel: [    3.616371] pata_acpi 0000:00:1f.1: enabling device (0005 -> 0007)
Feb 15 13:45:11 Enterprise kernel: [    3.616381] pata_acpi 0000:00:1f.1: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
Feb 15 13:45:11 Enterprise kernel: [    3.616422] pata_acpi 0000:00:1f.1: setting latency timer to 64
Feb 15 13:45:11 Enterprise kernel: [    3.616438] pata_acpi 0000:00:1f.1: PCI INT A disabled
Feb 15 13:45:11 Enterprise kernel: [    3.616750] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 11
Feb 15 13:45:11 Enterprise kernel: [    3.616754] e100 0000:01:08.0: PCI INT A -> Link[LNKE] -> GSI 11 (level, low) -> IRQ 11
Feb 15 13:45:11 Enterprise kernel: [    3.639833] e100 0000:01:08.0: PME# disabled
Feb 15 13:45:11 Enterprise kernel: [    3.641490] e100: eth0: e100_probe: addr 0xfcffd000, irq 11, MAC addr 00:0f:1f:ce:18:93
Feb 15 13:45:11 Enterprise kernel: [    3.641524] ohci1394 0000:01:01.1: PCI INT B -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11
Feb 15 13:45:11 Enterprise kernel: [    3.691257] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[11]  MMIO=[fcfff800-fcffffff]  Max Packet=[2048]  IR/IT contexts=[4/8]
Feb 15 13:45:11 Enterprise kernel: [    3.700262] ata_piix 0000:00:1f.1: version 2.12
Feb 15 13:45:11 Enterprise kernel: [    3.700278] ata_piix 0000:00:1f.1: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
Feb 15 13:45:11 Enterprise kernel: [    3.700322] ata_piix 0000:00:1f.1: setting latency timer to 64
Feb 15 13:45:11 Enterprise kernel: [    3.700614] scsi0 : ata_piix
Feb 15 13:45:11 Enterprise kernel: [    3.701068] scsi1 : ata_piix
Feb 15 13:45:11 Enterprise kernel: [    3.702156] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xbfa0 irq 14
Feb 15 13:45:11 Enterprise kernel: [    3.702160] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xbfa8 irq 15
Feb 15 13:45:11 Enterprise kernel: [    3.786643] usb 2-2: configuration #1 chosen from 1 choice
Feb 15 13:45:11 Enterprise kernel: [    3.864550] ata1.00: ATA-6: HTS548040M9AT00, MG2OA5EA, max UDMA/100
Feb 15 13:45:11 Enterprise kernel: [    3.864555] ata1.00: 78140160 sectors, multi 8: LBA48 
Feb 15 13:45:11 Enterprise kernel: [    3.880467] ata1.00: configured for UDMA/100
Feb 15 13:45:11 Enterprise kernel: [    4.044285] ata2.00: ATAPI: PHILIPS CD-RW/DVD-ROM CDD5263, UD91, max UDMA/33
Feb 15 13:45:11 Enterprise kernel: [    4.060237] ata2.00: configured for UDMA/33
Feb 15 13:45:11 Enterprise kernel: [    4.060364] scsi 0:0:0:0: Direct-Access     ATA      HTS548040M9AT00  MG2O PQ: 0 ANSI: 5
Feb 15 13:45:11 Enterprise kernel: [    4.060963] scsi 1:0:0:0: CD-ROM            PHILIPS  CDRW/DVD CDD5263 UD91 PQ: 0 ANSI: 5
Feb 15 13:45:11 Enterprise kernel: [    4.073672] scsi 0:0:0:0: Attached scsi generic sg0 type 0
Feb 15 13:45:11 Enterprise kernel: [    4.073722] scsi 1:0:0:0: Attached scsi generic sg1 type 5
Feb 15 13:45:11 Enterprise kernel: [    4.096786] Driver 'sd' needs updating - please use bus_type methods
Feb 15 13:45:11 Enterprise kernel: [    4.099073] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors (40008 MB)
Feb 15 13:45:11 Enterprise kernel: [    4.099092] sd 0:0:0:0: [sda] Write Protect is off
Feb 15 13:45:11 Enterprise kernel: [    4.099096] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Feb 15 13:45:11 Enterprise kernel: [    4.099124] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Feb 15 13:45:11 Enterprise kernel: [    4.099201] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors (40008 MB)
Feb 15 13:45:11 Enterprise kernel: [    4.099218] sd 0:0:0:0: [sda] Write Protect is off
Feb 15 13:45:11 Enterprise kernel: [    4.099221] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Feb 15 13:45:11 Enterprise kernel: [    4.099249] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Feb 15 13:45:11 Enterprise kernel: [    4.099254]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
Feb 15 13:45:11 Enterprise kernel: [    4.122171]  sda1 sda2 sda3 sda4 < sda5 sda6 >
Feb 15 13:45:11 Enterprise kernel: [    4.155351] sd 0:0:0:0: [sda] Attached SCSI disk
Feb 15 13:45:11 Enterprise kernel: [    4.161571] sr0: scsi3-mmc drive: 4x/24x writer cd/rw xa/form2 cdda tray
Feb 15 13:45:11 Enterprise kernel: [    4.161576] Uniform CD-ROM driver Revision: 3.20
Feb 15 13:45:11 Enterprise kernel: [    4.161668] sr 1:0:0:0: Attached scsi CD-ROM sr0
Feb 15 13:45:11 Enterprise kernel: [    4.532528] PM: Starting manual resume from disk
Feb 15 13:45:11 Enterprise kernel: [    4.532533] PM: Resume from partition 8:6
Feb 15 13:45:11 Enterprise kernel: [    4.532535] PM: Checking hibernation image.
Feb 15 13:45:11 Enterprise kernel: [    4.532714] PM: Resume from disk failed.
Feb 15 13:45:11 Enterprise kernel: [    4.583186] kjournald starting.  Commit interval 5 seconds
Feb 15 13:45:11 Enterprise kernel: [    4.583199] EXT3-fs: mounted filesystem with ordered data mode.
Feb 15 13:45:11 Enterprise kernel: [    4.964154] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[424fc00019933030]
Feb 15 13:45:11 Enterprise kernel: [   11.729586] udevd version 124 started
Feb 15 13:45:11 Enterprise kernel: [   12.696179] Linux agpgart interface v0.103
Feb 15 13:45:11 Enterprise kernel: [   12.763639] agpgart-intel 0000:00:00.0: Intel 855GM Chipset
Feb 15 13:45:11 Enterprise kernel: [   12.764164] agpgart-intel 0000:00:00.0: detected 892K stolen memory
Feb 15 13:45:11 Enterprise kernel: [   12.812028] agpgart-intel 0000:00:00.0: AGP aperture is 128M @ 0xf0000000
Feb 15 13:45:11 Enterprise kernel: [   12.832307] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Feb 15 13:45:11 Enterprise kernel: [   12.888584] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Feb 15 13:45:11 Enterprise kernel: [   12.945215] intel_rng: FWH not detected
Feb 15 13:45:11 Enterprise kernel: [   13.108156] iTCO_vendor_support: vendor-support=0
Feb 15 13:45:11 Enterprise kernel: [   13.160157] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.03 (30-Apr-2008)
Feb 15 13:45:11 Enterprise kernel: [   13.160271] iTCO_wdt: Found a ICH4-M TCO device (Version=1, TCOBASE=0x0860)
Feb 15 13:45:11 Enterprise kernel: [   13.160446] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
Feb 15 13:45:11 Enterprise kernel: [   13.365424] ACPI: AC Adapter [AC] (on-line)
Feb 15 13:45:11 Enterprise kernel: [   13.716233] input: PC Speaker as /devices/platform/pcspkr/input/input2
Feb 15 13:45:11 Enterprise kernel: [   13.837037] ACPI: Battery Slot [BAT0] (battery present)
Feb 15 13:45:11 Enterprise kernel: [   13.837109] ACPI: Battery Slot [BAT1] (battery absent)
Feb 15 13:45:11 Enterprise kernel: [   13.837191] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input3
Feb 15 13:45:11 Enterprise kernel: [   13.837607] ACPI: Lid Switch [LID]
Feb 15 13:45:11 Enterprise kernel: [   13.837670] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input4
Feb 15 13:45:11 Enterprise kernel: [   13.848024] ACPI: Power Button (CM) [PBTN]
Feb 15 13:45:11 Enterprise kernel: [   13.848158] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input5
Feb 15 13:45:11 Enterprise kernel: [   13.860037] ACPI: Sleep Button (CM) [SBTN]
Feb 15 13:45:11 Enterprise kernel: [   14.308136] ieee80211_crypt: registered algorithm 'NULL'
Feb 15 13:45:11 Enterprise kernel: [   14.363262] ieee80211: 802.11 data/management/control stack, git-1.1.13
Feb 15 13:45:11 Enterprise kernel: [   14.363267] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
Feb 15 13:45:11 Enterprise kernel: [   14.694684] Yenta: CardBus bridge found at 0000:01:01.0 [1028:0163]
Feb 15 13:45:11 Enterprise kernel: [   14.694704] Yenta: Using CSCINT to route CSC interrupts to PCI
Feb 15 13:45:11 Enterprise kernel: [   14.694706] Yenta: Routing CardBus interrupts to PCI
Feb 15 13:45:11 Enterprise kernel: [   14.694712] Yenta TI: socket 0000:01:01.0, mfunc 0x012c1222, devctl 0x64
Feb 15 13:45:11 Enterprise kernel: [   14.784301] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
Feb 15 13:45:11 Enterprise kernel: [   14.784306] ipw2200: Copyright(c) 2003-2006 Intel Corporation
Feb 15 13:45:11 Enterprise kernel: [   14.924683] Yenta: ISA IRQ mask 0x04d8, PCI irq 11
Feb 15 13:45:11 Enterprise kernel: [   14.924688] Socket status: 30000086
Feb 15 13:45:11 Enterprise kernel: [   14.924692] Yenta: Raising subordinate bus# of parent bus (#01) from #01 to #05
Feb 15 13:45:11 Enterprise kernel: [   14.924700] pcmcia: parent PCI bridge I/O window: 0xe000 - 0xefff
Feb 15 13:45:11 Enterprise kernel: [   14.924704] cs: IO port probe 0xe000-0xefff: clean.
Feb 15 13:45:11 Enterprise kernel: [   14.925344] pcmcia: parent PCI bridge Memory window: 0xfc000000 - 0xfdffffff
Feb 15 13:45:11 Enterprise kernel: [   14.925347] pcmcia: parent PCI bridge Memory window: 0x30000000 - 0x33ffffff
Feb 15 13:45:11 Enterprise kernel: [   14.925859] ipw2200 0000:01:03.0: PCI INT A -> Link[LNKB] -> GSI 5 (level, low) -> IRQ 5
Feb 15 13:45:11 Enterprise kernel: [   14.935101] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
Feb 15 13:45:11 Enterprise kernel: [   14.935154] firmware: requesting ipw2200-bss.fw
Feb 15 13:45:11 Enterprise kernel: [   14.942470] input: PS/2 Mouse as /devices/platform/i8042/serio1/input/input6
Feb 15 13:45:11 Enterprise kernel: [   14.969798] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input7
Feb 15 13:45:11 Enterprise kernel: [   15.408266] parport_pc 00:0c: reported by Plug and Play ACPI
Feb 15 13:45:11 Enterprise kernel: [   15.408312] parport0: PC-style at 0x378 (0x778), irq 7, dma 1 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
Feb 15 13:45:11 Enterprise kernel: [   15.585192] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:1e/input/input8
Feb 15 13:45:11 Enterprise kernel: [   15.596043] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
Feb 15 13:45:11 Enterprise kernel: [   15.596249] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:24/input/input9
Feb 15 13:45:11 Enterprise kernel: [   15.612028] ACPI: Video Device [VID2] (multi-head: yes  rom: no  post: no)
Feb 15 13:45:11 Enterprise kernel: [   15.945178] Bluetooth: Core ver 2.13
Feb 15 13:45:11 Enterprise kernel: [   15.945393] NET: Registered protocol family 31
Feb 15 13:45:11 Enterprise kernel: [   15.945396] Bluetooth: HCI device and connection manager initialized
Feb 15 13:45:11 Enterprise kernel: [   15.945400] Bluetooth: HCI socket layer initialized
Feb 15 13:45:11 Enterprise kernel: [   15.986039] Bluetooth: Generic Bluetooth USB driver ver 0.3
Feb 15 13:45:11 Enterprise kernel: [   15.986154] usbcore: registered new interface driver btusb
Feb 15 13:45:11 Enterprise kernel: [   16.344792] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
Feb 15 13:45:11 Enterprise kernel: [   17.627657] cs: IO port probe 0x100-0x3af: clean.
Feb 15 13:45:11 Enterprise kernel: [   17.628505] cs: IO port probe 0x3e0-0x4ff: clean.
Feb 15 13:45:11 Enterprise kernel: [   17.628861] cs: IO port probe 0x820-0x8ff: clean.
Feb 15 13:45:11 Enterprise kernel: [   17.628915] cs: IO port probe 0xc00-0xcf7: clean.
Feb 15 13:45:11 Enterprise kernel: [   17.629369] cs: IO port probe 0xa00-0xaff: clean.
Feb 15 13:45:11 Enterprise kernel: [   17.746036] ipw2200: Detected geography ZZD (13 802.11bg channels, 0 802.11a channels)
Feb 15 13:45:11 Enterprise kernel: [   17.746124] Intel ICH 0000:00:1f.5: PCI INT B -> Link[LNKB] -> GSI 5 (level, low) -> IRQ 5
Feb 15 13:45:11 Enterprise kernel: [   17.746159] Intel ICH 0000:00:1f.5: setting latency timer to 64
Feb 15 13:45:11 Enterprise kernel: [   18.572034] intel8x0_measure_ac97_clock: measured 55468 usecs
Feb 15 13:45:11 Enterprise kernel: [   18.572039] intel8x0: clocking to 48000
Feb 15 13:45:11 Enterprise kernel: [   19.712659] lp0: using parport0 (interrupt-driven).
Feb 15 13:45:11 Enterprise kernel: [   19.824680] Adding 1228932k swap on /dev/sda6.  Priority:-1 extents:1 across:1228932k
Feb 15 13:45:11 Enterprise kernel: [   20.357810] EXT3 FS on sda5, internal journal
Feb 15 13:45:11 Enterprise kernel: [   22.098922] type=1505 audit(1234701909.493:2): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=3982
Feb 15 13:45:11 Enterprise kernel: [   22.099253] type=1505 audit(1234701909.493:3): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=3982
Feb 15 13:45:11 Enterprise kernel: [   22.234861] ip_tables: (C) 2000-2006 Netfilter Core Team
Feb 15 13:45:11 Enterprise kernel: [   22.497850] NET: Registered protocol family 17
Feb 15 13:45:11 Enterprise kernel: [   22.926771] NET: Registered protocol family 10
Feb 15 13:45:11 Enterprise kernel: [   22.927311] lo: Disabled Privacy Extensions
Feb 15 13:45:11 Enterprise kernel: [   23.385285] ACPI: WMI: Mapper loaded
Feb 15 13:45:11 Enterprise kernel: [   24.232101] ieee80211_crypt: registered algorithm 'CCMP'
Feb 15 13:45:11 Enterprise kernel: [   24.485904] padlock: VIA PadLock not detected.
Feb 15 13:45:12 Enterprise kernel: [   24.611981] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
Feb 15 13:45:12 Enterprise kernel: [   24.679576] apm: BIOS not found.
Feb 15 13:45:12 Enterprise kernel: [   24.860888] ppdev: user-space parallel port driver
Feb 15 13:45:14 Enterprise kernel: [   26.116026] Clocksource tsc unstable (delta = -200177984 ns)
Feb 15 13:45:15 Enterprise kernel: [   27.128327] Bluetooth: L2CAP ver 2.11
Feb 15 13:45:15 Enterprise kernel: [   27.128334] Bluetooth: L2CAP socket layer initialized
Feb 15 13:45:15 Enterprise kernel: [   27.162826] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Feb 15 13:45:15 Enterprise kernel: [   27.162833] Bluetooth: BNEP filters: protocol multicast
Feb 15 13:45:15 Enterprise kernel: [   27.250392] Bridge firewalling registered
Feb 15 13:45:15 Enterprise kernel: [   27.314130] Bluetooth: SCO (Voice Link) ver 0.6
Feb 15 13:45:15 Enterprise kernel: [   27.314136] Bluetooth: SCO socket layer initialized
Feb 15 13:45:15 Enterprise kernel: [   27.330545] Bluetooth: RFCOMM socket layer initialized
Feb 15 13:45:15 Enterprise kernel: [   27.330830] Bluetooth: RFCOMM TTY layer initialized
Feb 15 13:45:15 Enterprise kernel: [   27.330836] Bluetooth: RFCOMM ver 1.10
Feb 15 13:45:17 Enterprise kernel: [   29.797001] [drm] Initialized drm 1.1.0 20060810
Feb 15 13:45:17 Enterprise kernel: [   29.807151] pci 0000:00:02.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
Feb 15 13:45:17 Enterprise kernel: [   29.807164] pci 0000:00:02.0: setting latency timer to 64
Feb 15 13:45:17 Enterprise kernel: [   29.809166] [drm] Initialized i915 1.6.0 20060119 on minor 0
Feb 15 13:45:17 Enterprise kernel: [   29.809183] pci 0000:00:02.1: setting latency timer to 64
Feb 15 13:45:17 Enterprise kernel: [   29.810676] [drm] Initialized i915 1.6.0 20060119 on minor 1
Feb 15 13:45:21 Enterprise kernel: [   32.936037] eth1: no IPv6 routers present
Feb 15 13:47:08 Enterprise kernel: [  139.968201] ppdev0: registered pardevice
Feb 15 13:47:08 Enterprise kernel: [  140.016070] ppdev0: unregistered pardevice
Feb 15 13:47:08 Enterprise kernel: [  140.436474] ppdev0: registered pardevice
Feb 15 13:47:08 Enterprise kernel: [  140.500713] ppdev0: unregistered pardevice
Feb 15 13:47:09 Enterprise kernel: [  141.554060] ppdev0: registered pardevice
Feb 15 13:47:09 Enterprise kernel: [  141.600256] ppdev0: unregistered pardevice
```

---

### Post by Bonsanto on 2009-02-15
sAME PROBLEM HERE BUT cTROL+ALT+F1 OR F2F3F4 OR SPACE DOENS'T WORK ¡_¡:guitar:

---

### Post by stalkingwolf on 2009-02-15
the only time I experienced this kind of problem I finally traced it
back to a new stick of RAM.  The RAM checks out fine.  But when installed
I have these random shut downs, take it out and all works fine.

:-k

---

### Post by fairy._.queen on 2009-02-19
Thanks for replying!
I didn't put in a new stick of ram, though, i'm using the same as ever... and it did work well with both hardy and windows and it does work well now with windows. :-/ [puzzled]

---

