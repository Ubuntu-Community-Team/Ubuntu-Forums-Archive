---
title: "No Internet/Broadcom 440/Ubuntu 12.04/Dell Vostro 1500"
date: 2013-12-04
forum: Networking &amp; Wireless
---

### Post by fracas on 2013-12-04
Folks:
 
I am a Linux novice, an old geezer, and the owner of a DELL Vostro 1500 laptop.
Like so many others, I have installed Ubuntu 12.04 successfully but I have no wireless or wired internet connectivity.
 
I followed the instructions (at “HowTo Post A Wireless Issue”) for submitting a request to the best of my ability.  The data results are attached.  Please forgive me for sending so much data, but I did not think I could edit it safely, nor do I know how to use “code tags”. 
 
I would be very grateful if someone can help me get on line.


```
DELL Vostro 1500 laptop
[code] $ lspci

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)

00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) (rev 0c)

00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (secondary) (rev 0c)

00:1a.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)

00:1a.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)

00:1a.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)

00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)

00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)

00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)

00:1d.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)

00:1d.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)

00:1d.2 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)

00:1d.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)

00:1f.0 ISA bridge: Intel Corporation 82801HM (ICH8M) LPC Interface Controller (rev 02)

00:1f.1 IDE interface: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)

00:1f.2 IDE interface: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) SATA Controller [IDE mode] (rev 02)

00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)

03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)

03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)

03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)

03:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)

03:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)

0c:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)

$ lsusb

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Bus 005 Device 002: ID 046d:c52f Logitech, Inc. Wireless Mouse M305

$ lspci -nn | grep 'Wireless Brand'

:~$ 
$ ifconfig

lo        Link encap:Local Loopback  

          inet addr:127.0.0.1  Mask:255.0.0.0

          inet6 addr: ::1/128 Scope:Host

          UP LOOPBACK RUNNING  MTU:16436  Metric:1

          RX packets:2672 errors:0 dropped:0 overruns:0 frame:0

          TX packets:2672 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0 

          RX bytes:217408 (217.4 KB)  TX bytes:217408 (217.4 KB)

$ ifconfig

lo        Link encap:Local Loopback  

          inet addr:127.0.0.1  Mask:255.0.0.0

          inet6 addr: ::1/128 Scope:Host

          UP LOOPBACK RUNNING  MTU:16436  Metric:1

          RX packets:2688 errors:0 dropped:0 overruns:0 frame:0

          TX packets:2688 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0 

          RX bytes:218720 (218.7 KB)  TX bytes:218720 (218.7 KB)



$ iwconfig wlan0

wlan0     No such device

$ lsmod

Module                  Size  Used by

nls_iso8859_1          12617  0 

nls_cp437              12751  0 

vfat                   17308  0 

fat                    55605  1 vfat

usb_storage            39646  0 

snd_hda_codec_idt      60251  1 

bnep                   17830  2 

bluetooth             158447  7 bnep

r852                   17901  0 

snd_hda_intel          32719  3 

i915                  428127  3 

snd_hda_codec         109562  2 snd_hda_codec_idt,snd_hda_intel

ssb                    69106  1 

wl                   3032542  1 

sm_common              16772  1 r852

nand                   49667  2 r852,sm_common

nand_ids                8547  1 nand

mtd                    35584  2 sm_common,nand

nand_bch               13003  1 nand

drm_kms_helper         45466  1 i915

snd_hwdep              13276  1 snd_hda_codec

bch                    21784  1 nand_bch

snd_pcm                80916  2 snd_hda_intel,snd_hda_codec

dell_laptop            17767  0 

joydev                 17393  0 

snd_seq_midi           13132  0 

snd_rawmidi            25424  1 snd_seq_midi

snd_seq_midi_event     14475  1 snd_seq_midi

dcdbas                 14098  1 dell_laptop

dell_wmi               12601  0 

drm                   197641  4 i915,drm_kms_helper

parport_pc             32114  0 

r592                   17808  0 

ppdev                  12849  0 

snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event

snd_timer              28931  2 snd_pcm,snd_seq

snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq

sparse_keymap          13658  1 dell_wmi

snd                    62218  15 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device

cfg80211              178877  1 wl

psmouse                86546  0 

nand_ecc               13105  1 nand

memstick               15857  1 r592

serio_raw              13027  0 

mac_hid                13077  0 

i2c_algo_bit           13199  1 i915

soundcore              14635  1 snd

video                  19115  1 i915

lib80211               14040  1 wl

snd_page_alloc         14108  2 snd_hda_intel,snd_pcm

wmi                    18744  1 dell_wmi

lp                     17455  0 

parport                40930  3 parport_pc,ppdev,lp

firewire_ohci          40172  0 

sdhci_pci              18324  0 

sdhci                  28241  1 sdhci_pci

firewire_core          56940  1 firewire_ohci

crc_itu_t              12627  1 firewire_core

usbhid                 41937  0 

hid                    77428  1 usbhid

 
$ lsmod | grep "wlan_module_name"
:~$

 $ dmesg
0000000
[    0.425699] brd: module loaded
[    0.426536] loop: module loaded
[    0.426742] ata_piix 0000:00:1f.1: version 2.13
[    0.426759] ata_piix 0000:00:1f.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.426805] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.436074] scsi0 : ata_piix
[    0.436196] scsi1 : ata_piix
[    0.436589] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x6fa0 irq 14
[    0.436593] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x6fa8 irq 15
[    0.436647] ata_piix 0000:00:1f.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.436655] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    0.436887] ata2: port disabled--ignoring
[    0.436904] ACPI: Battery Slot [BAT0] (battery present)
[    0.592266] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.596085] scsi2 : ata_piix
[    0.596197] scsi3 : ata_piix
[    0.596601] ata3: SATA max UDMA/133 cmd 0x6eb0 ctl 0x6eb8 bmdma 0x6ee0 irq 17
[    0.596610] ata4: SATA max UDMA/133 cmd 0x6ec0 ctl 0x6ec8 bmdma 0x6ee8 irq 17
[    0.597072] Fixed MDIO Bus: probed
[    0.597096] tun: Universal TUN/TAP device driver, 1.6
[    0.597098] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.597199] PPP generic driver version 2.4.2
[    0.597316] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.597341] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    0.597369] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    0.597374] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    0.597421] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    0.597456] ehci_hcd 0000:00:1a.7: debug port 1
[    0.601345] ehci_hcd 0000:00:1a.7: cache line size of 64 is not supported
[    0.601529] ehci_hcd 0000:00:1a.7: irq 22, io mem 0xfed1c400
[    0.616580] ata1.00: ATAPI: TSSTcorpCD-RW/DVD-ROM TSL462D, DE04, max UDMA/33
[    0.624049] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    0.624451] hub 1-0:1.0: USB hub found
[    0.624457] hub 1-0:1.0: 4 ports detected
[    0.624556] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.624587] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.624592] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.624642] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    0.624678] ehci_hcd 0000:00:1d.7: debug port 1
[    0.628565] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
[    0.632480] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xfed1c000
[    0.648617] ata1.00: configured for UDMA/33
[    0.652047] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.652278] hub 2-0:1.0: USB hub found
[    0.652284] hub 2-0:1.0: 6 ports detected
[    0.652387] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.652408] uhci_hcd: USB Universal Host Controller Interface driver
[    0.652444] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.652459] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    0.652464] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    0.652519] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    0.652555] uhci_hcd 0000:00:1a.0: irq 20, io base 0x00006f20
[    0.652705] hub 3-0:1.0: USB hub found
[    0.652710] hub 3-0:1.0: 2 ports detected
[    0.652785] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.652795] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    0.652799] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    0.652846] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    0.652892] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00006f00
[    0.653043] hub 4-0:1.0: USB hub found
[    0.653048] hub 4-0:1.0: 2 ports detected
[    0.653121] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.653132] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.653136] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.653182] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    0.653212] uhci_hcd 0000:00:1d.0: irq 20, io base 0x00006f80
[    0.653361] hub 5-0:1.0: USB hub found
[    0.653365] hub 5-0:1.0: 2 ports detected
[    0.653434] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.653444] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.653448] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.653492] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    0.653523] uhci_hcd 0000:00:1d.1: irq 21, io base 0x00006f60
[    0.653669] hub 6-0:1.0: USB hub found
[    0.653673] hub 6-0:1.0: 2 ports detected
[    0.653747] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    0.653757] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.653761] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.653808] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    0.653840] uhci_hcd 0000:00:1d.2: irq 22, io base 0x00006f40
[    0.653985] hub 7-0:1.0: USB hub found
[    0.653990] hub 7-0:1.0: 2 ports detected
[    0.654127] usbcore: registered new interface driver libusual
[    0.654193] i8042: PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.704149] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.704161] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.704347] mousedev: PS/2 mouse device common for all mice
[    0.704534] rtc_cmos 00:03: RTC can wake from S4
[    0.704671] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    0.704707] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    0.704794] device-mapper: uevent: version 1.0.3
[    0.704876] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[    0.704906] EISA: Probing bus 0 at eisa.0
[    0.704915] Cannot allocate resource for EISA slot 1
[    0.704918] Cannot allocate resource for EISA slot 2
[    0.704920] Cannot allocate resource for EISA slot 3
[    0.704944] EISA: Detected 0 cards.
[    0.704958] cpufreq-nforce2: No nForce2 chipset.
[    0.704998] cpuidle: using governor ladder
[    0.705057] cpuidle: using governor menu
[    0.705059] EFI Variables Facility v0.08 2004-May-17
[    0.705303] TCP cubic registered
[    0.705449] NET: Registered protocol family 10
[    0.707186] NET: Registered protocol family 17
[    0.707200] Registering the dns_resolver key type
[    0.707231] Using IPI No-Shortcut mode
[    0.707345] PM: Hibernation image not present or could not be loaded.
[    0.707357] registered taskstats version 1
[    0.709290] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    0.979913] isapnp: No Plug & Play device found
[    0.981235] scsi 0:0:0:0: CD-ROM            TSSTcorp CDRW/DVD TSL462D DE04 PQ: 0 ANSI: 5
[    0.983340] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    0.983344] cdrom: Uniform CD-ROM driver Revision: 3.20
[    0.983489] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    0.983683] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    1.054016] Freeing initrd memory: 13876k freed
[    1.071508]   Magic number: 9:588:423
[    1.071638] rtc_cmos 00:03: setting system clock to 2013-12-03 09:24:04 UTC (1386062644)
[    1.071660] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.071662] EDD information not available.
[    1.384054] usb 5-2: new full-speed USB device number 2 using uhci_hcd
[    1.484136] ata3.00: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.484155] ata3.01: SATA link down (SStatus 0 SControl 300)
[    1.492474] ata3.00: ATA-8: FUJITSU MHW2080BH, 0085001C, max UDMA/100
[    1.492478] ata3.00: 156301488 sectors, multi 8: LBA48 NCQ (depth 0/32)
[    1.508477] ata3.00: configured for UDMA/100
[    1.508610] scsi 2:0:0:0: Direct-Access     ATA      FUJITSU MHW2080B 0085 PQ: 0 ANSI: 5
[    1.508822] sd 2:0:0:0: [sda] 156301488 512-byte logical blocks: (80.0 GB/74.5 GiB)
[    1.508878] sd 2:0:0:0: [sda] Write Protect is off
[    1.508882] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.508906] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.509240] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    1.594593]  sda: sda1 sda2 < sda5 sda6 >
[    1.594979] sd 2:0:0:0: [sda] Attached SCSI disk
[    2.040053] ata4.01: failed to resume link (SControl 0)
[    2.040106] ata4.00: SATA link down (SStatus 0 SControl 300)
[    2.040130] ata4.01: SATA link down (SStatus 0 SControl 0)
[    2.040211] Freeing unused kernel memory: 744k freed
[    2.040559] Write protecting the kernel text: 5840k
[    2.040573] Write protecting the kernel read-only data: 2388k
[    2.040575] NX-protecting the kernel data: 4400k
[    2.063880] udevd[89]: starting version 175
[    2.302124] sdhci: Secure Digital Host Controller Interface driver
[    2.302128] sdhci: Copyright(c) Pierre Ossman
[    2.302458] sdhci-pci 0000:03:01.1: SDHCI controller found [1180:0822] (rev 22)
[    2.302488] sdhci-pci 0000:03:01.1: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[    2.303540] mmc0: no vmmc regulator found
[    2.312752] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.0/usb5/5-2/5-2:1.0/input/input4
[    2.315847] generic-usb 0003:046D:C52F.0001: input,hidraw0: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:1d.0-2/input0
[    2.321640] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.0/usb5/5-2/5-2:1.1/input/input5
[    2.321798] generic-usb 0003:046D:C52F.0002: input,hiddev0,hidraw1: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1d.0-2/input1
[    2.321819] usbcore: registered new interface driver usbhid
[    2.321822] usbhid: USB HID core driver
[    2.331703] Registered led device: mmc0::
[    2.341101] mmc0: SDHCI controller on PCI [0000:03:01.1] using DMA
[    2.341148] firewire_ohci 0000:03:01.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    2.404088] firewire_ohci: Added fw-ohci device 0000:03:01.0, OHCI v1.10, 4 IR + 4 IT contexts, quirks 0x11
[    2.653861] EXT4-fs (sda5): INFO: recovery required on readonly filesystem
[    2.653866] EXT4-fs (sda5): write access will be enabled during recovery
[    2.904211] firewire_core: created device fw0: GUID 374fc0002a9d3981, S400
[    6.168407] EXT4-fs (sda5): recovery complete
[    6.169385] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
[    8.741859] Adding 4183036k swap on /dev/sda6.  Priority:-1 extents:1 across:4183036k
[    9.227856] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro
[   10.538793] udevd[372]: starting version 175
[   11.536335] lp: driver loaded but no devices found
[   12.755748] wmi: Mapper loaded
[   12.764435] lib80211: common routines for IEEE802.11 drivers
[   12.764439] lib80211_crypt: registered algorithm 'NULL'
[   12.800977] cfg80211: Calling CRDA to update world regulatory domain
[   13.352432] cfg80211: Calling CRDA to update world regulatory domain
[   13.960694] psmouse serio1: synaptics: Touchpad model: 1, fw: 6.3, id: 0x1a0b1, caps: 0xa04793/0x300000/0x0
[   13.960703] psmouse serio1: synaptics: serio: Synaptics pass-through port at isa0060/serio1/input0
[   13.996692] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input6
[   14.007299] ppdev: user-space parallel port driver
[   14.050449] r592 0000:03:01.2: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[   14.051573] r592: driver successfully loaded
[   14.158970] [drm] Initialized drm 1.1.0 20060810
[   14.298888] input: Dell WMI hotkeys as /devices/virtual/input/input7
[   14.310978] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   15.316796] wl: module license 'MIXED/Proprietary' taints kernel.
[   15.316801] Disabling lock debugging due to kernel taint
[   15.344343] wl 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   15.344354] wl 0000:0c:00.0: setting latency timer to 64
[   15.346808] malloc in abgphy done
[   15.347027] wl driver 6.20.155.1 (r326264) failed with code 21
[   15.347055] ------------[ cut here ]------------
[   15.347101] kernel BUG at include/net/cfg80211.h:2209!
[   15.347145] invalid opcode: 0000 [#1] SMP
[   15.347255] Modules linked in: wl(P+) sm_common nand nand_ids mtd nand_bch drm_kms_helper snd_hwdep bch snd_pcm dell_laptop joydev snd_seq_midi snd_rawmidi snd_seq_midi_event dcdbas dell_wmi drm parport_pc r592 ppdev snd_seq snd_timer snd_seq_device sparse_keymap snd cfg80211 psmouse nand_ecc memstick serio_raw mac_hid i2c_algo_bit soundcore video lib80211 snd_page_alloc wmi lp parport firewire_ohci sdhci_pci sdhci firewire_core crc_itu_t usbhid hid [last unloaded: cfg80211]
[   15.348014]
[   15.348014] Pid: 660, comm: modprobe Tainted: P           O 3.2.0-56-generic-pae #86-Ubuntu Dell Inc. Vostro 1500                     /0NX907
[   15.348014] EIP: 0060:[<f8ddd4b8>] EFLAGS: 00010246 CPU: 0
[   15.348014] EIP is at wdev_priv.part.7+0x3/0x5 [wl]
[   15.348014] EAX: 00000000 EBX: f7074c80 ECX: f7074c80 EDX: ef8ebc90
[   15.348014] ESI: ef8ebc90 EDI: ef8ebc0c EBP: ef925cec ESP: ef925cec
[   15.348014]  DS: 007b ES: 007b FS: 00d8 GS: 00e0 SS: 0068
[   15.348014] Process modprobe (pid: 660, ti=ef924000 task=f27ca610 task.ti=ef924000)
[   15.348014] Stack:
[   15.348014]  ef925d00 f8ddc944 f7074c80 ef8ebc90 ef8ebc0c ef925d14 f8dd559f ef8ebc00
[   15.348014]  f756b000 f7074800 ef925dc0 f8dd5f68 00000000 00000000 ffffff06 00000000
[   15.348014]  c1971f93 ef925d7d ef925db0 00000246 ef925d6e c174a4f9 0000000f 00054b93
[   15.348014] Call Trace:
[   15.348014]  [<f8ddc944>] wl_cfg80211_detach+0xc4/0xd0 [wl]
[   15.348014]  [<f8dd559f>] wl_free_if.isra.10+0x1f/0xa0 [wl]
[   15.348014]  [<f8dd5f68>] wl_free+0x58/0x250 [wl]
[   15.348014]  [<f8cf5e92>] ? wlc_attach+0xf6c/0xfda [wl]
[   15.348014]  [<f8ddd42b>] wl_pci_probe+0x51c/0x53c [wl]
[   15.348014]  [<c15ab67d>] ? _raw_spin_lock_irqsave+0x2d/0x40
[   15.348014]  [<c138ffc5>] ? pm_runtime_enable+0x45/0x70
[   15.348014]  [<c12d3b07>] local_pci_probe+0x47/0xb0
[   15.348014]  [<c12d5008>] pci_device_probe+0x68/0x90
[   15.348014]  [<c11a9e77>] ? sysfs_create_link+0x17/0x20
[   15.348014]  [<c1387d6d>] really_probe+0x4d/0x150
[   15.348014]  [<c13913f9>] ? pm_runtime_barrier+0x49/0xb0
[   15.348014]  [<c1387faa>] driver_probe_device+0x3a/0x60
[   15.348014]  [<c1388061>] __driver_attach+0x91/0xa0
[   15.348014]  [<c1387fd0>] ? driver_probe_device+0x60/0x60
[   15.348014]  [<c13870e1>] bus_for_each_dev+0x51/0x80
[   15.348014]  [<c1387ba1>] driver_attach+0x21/0x30
[   15.348014]  [<c1387fd0>] ? driver_probe_device+0x60/0x60
[   15.348014]  [<c138787f>] bus_add_driver+0x17f/0x260
[   15.348014]  [<c12d5030>] ? pci_device_probe+0x90/0x90
[   15.348014]  [<c1388536>] driver_register+0x66/0x110
[   15.348014]  [<c12d4db2>] __pci_register_driver+0x42/0xc0
[   15.348014]  [<f8fae017>] wl_module_init+0x17/0x1000 [wl]
[   15.348014]  [<c1003035>] do_one_initcall+0x35/0x170
[   15.348014]  [<f8fae000>] ? 0xf8fadfff
[   15.348014]  [<c10968ec>] sys_init_module+0xac/0x210
[   15.348014]  [<c15b295f>] sysenter_do_call+0x12/0x28
[   15.348014] Code: d0 e8 fd e0 7c c8 89 f0 e8 76 8a ff ff 89 d8 e8 2f 55 4f c8 31 d2 89 f8 e8 76 a5 5a c8 58 5b 5e 5f 5d c3 55 89 e5 0f 0b 55 89 e5 <0f> 0b 55 89 e5 66 66 66 66 90 0f 0b 55 89 e5 66 66 66 66 90 0f
[   15.348014] EIP: [<f8ddd4b8>] wdev_priv.part.7+0x3/0x5 [wl] SS:ESP 0068:ef925cec
[   15.354744] ---[ end trace ad46c02fbf192219 ]---
[   15.605570] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   15.605637] i915 0000:00:02.0: setting latency timer to 64
[   15.626569] mtrr: type mismatch for e0000000,10000000 old: write-back new: write-combining
[   15.626648] [drm] MTRR allocation failed.  Graphics performance may suffer.
[   15.628215] i915 0000:00:02.0: irq 43 for MSI/MSI-X
[   15.628277] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   15.628334] [drm] Driver supports precise vblank timestamp query.
[   15.628434] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   15.681898] composite sync not supported
[   15.773562] r852 0000:03:01.3: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[   15.773825] r852: driver loaded successfully
[   15.934266] [drm] initialized overlay support
[   15.934376] composite sync not supported
[   16.100368] fbcon: inteldrmfb (fb0) is primary device
[   16.552886] Console: switching to colour frame buffer device 160x50
[   16.557752] fb0: inteldrmfb frame buffer device
[   16.557789] drm: registered panic notifier
[   16.571630] acpi device:34: registered as cooling_device1
[   16.573098] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/LNXVIDEO:01/input/input8
[   16.573381] ACPI: Video Device [VID1] (multi-head: yes  rom: no  post: no)
[   16.573469] [Firmware Bug]: Duplicate ACPI video bus devices for the same VGA controller, please try module parameter "video.allow_duplicates=1"if the current driver doesn't work.
[   16.574556] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   16.574673] snd_hda_intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   16.574829] snd_hda_intel 0000:00:1b.0: irq 44 for MSI/MSI-X
[   16.574914] snd_hda_intel 0000:00:1b.0: setting latency timer to 64
[   16.691582] Bluetooth: Core ver 2.16
[   16.691700] NET: Registered protocol family 31
[   16.691743] Bluetooth: HCI device and connection manager initialized
[   16.691799] Bluetooth: HCI socket layer initialized
[   16.691838] Bluetooth: L2CAP socket layer initialized
[   16.692657] Bluetooth: SCO socket layer initialized
[   16.695616] type=1400 audit(1386080660.116:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=667 comm="apparmor_parser"
[   16.696325] type=1400 audit(1386080660.120:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=667 comm="apparmor_parser"
[   16.696743] type=1400 audit(1386080660.120:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=667 comm="apparmor_parser"
[   16.793552] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   16.793611] Bluetooth: BNEP filters: protocol multicast
[   16.860776] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   16.868073] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   17.369288] type=1400 audit(1386080660.792:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=705 comm="apparmor_parser"
[   17.376518] type=1400 audit(1386080660.800:6): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=705 comm="apparmor_parser"
[   17.537263] cfg80211: World regulatory domain updated:
[   17.540261] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   17.543249] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.546260] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   17.549228] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   17.552161] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.555054] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.566312] cfg80211: World regulatory domain updated:
[   17.569166] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   17.572158] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.574981] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   17.577794] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   17.580560] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.583271] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.605485] composite sync not supported
[   18.485230] init: failsafe main process (758) killed by TERM signal
[   23.698934] type=1400 audit(1386080667.124:7): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=884 comm="apparmor_parser"
[   23.699390] type=1400 audit(1386080667.124:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper//chromium_browser" pid=884 comm="apparmor_parser"
[   23.703196] type=1400 audit(1386080667.124:9): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=885 comm="apparmor_parser"
[   23.704871] type=1400 audit(1386080667.128:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=885 comm="apparmor_parser"
[   23.705176] type=1400 audit(1386080667.128:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=885 comm="apparmor_parser"
[   23.825571] type=1400 audit(1386080667.248:12): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=886 comm="apparmor_parser"
[   23.832957] type=1400 audit(1386080667.256:13): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince//launchpad_integration" pid=886 comm="apparmor_parser"
[   23.834585] type=1400 audit(1386080667.256:14): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince//sanitized_helper" pid=886 comm="apparmor_parser"
[   23.836050] type=1400 audit(1386080667.256:15): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=886 comm="apparmor_parser"
[   23.840552] type=1400 audit(1386080667.264:16): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer//launchpad_integration" pid=886 comm="apparmor_parser"
[   26.391915] composite sync not supported
[   26.724169] composite sync not supported
[   32.653031] composite sync not supported
[   39.683889] composite sync not supported
[   46.249324] composite sync not supported
[   46.873957] composite sync not supported
[   59.136627] composite sync not supported
[ 1413.495331] composite sync not supported
[ 1788.320064] usb 2-1: new high-speed USB device number 3 using ehci_hcd
[ 1788.577095] Initializing USB Mass Storage driver...
[ 1788.577252] scsi4 : usb-storage 2-1:1.0
[ 1788.577361] usbcore: registered new interface driver usb-storage
[ 1788.577364] USB Mass Storage support registered.
[ 1789.641149] scsi 4:0:0:0: Direct-Access     Verbatim STORE N GO       5.00 PQ: 0 ANSI: 6
[ 1789.646686] sd 4:0:0:0: Attached scsi generic sg2 type 0
[ 1790.316030] sd 4:0:0:0: [sdb] 3913728 512-byte logical blocks: (2.00 GB/1.86 GiB)
[ 1790.317128] sd 4:0:0:0: [sdb] Write Protect is off
[ 1790.317131] sd 4:0:0:0: [sdb] Mode Sense: 23 00 00 00
[ 1790.318128] sd 4:0:0:0: [sdb] No Caching mode page present
[ 1790.318132] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 1790.323757] sd 4:0:0:0: [sdb] No Caching mode page present
[ 1790.323763] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 1790.343344]  sdb: sdb1
[ 1790.348145] sd 4:0:0:0: [sdb] No Caching mode page present
[ 1790.348151] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 1790.348155] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[ 1828.087038] usb 2-1: USB disconnect, device number 3
[ 2506.239828] composite sync not supported
[ 4359.212076] usb 2-1: new high-speed USB device number 4 using ehci_hcd
[ 4359.353250] scsi5 : usb-storage 2-1:1.0
[ 4360.416086] scsi 5:0:0:0: Direct-Access     Verbatim STORE N GO       5.00 PQ: 0 ANSI: 6
[ 4360.418895] sd 5:0:0:0: Attached scsi generic sg2 type 0
[ 4361.059438] sd 5:0:0:0: [sdb] 3913728 512-byte logical blocks: (2.00 GB/1.86 GiB)
[ 4361.060559] sd 5:0:0:0: [sdb] Write Protect is off
[ 4361.060563] sd 5:0:0:0: [sdb] Mode Sense: 23 00 00 00
[ 4361.061677] sd 5:0:0:0: [sdb] No Caching mode page present
[ 4361.061681] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 4361.067307] sd 5:0:0:0: [sdb] No Caching mode page present
[ 4361.067312] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 4361.086919]  sdb: sdb1
[ 4361.092440] sd 5:0:0:0: [sdb] No Caching mode page present
[ 4361.092445] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 4361.092449] sd 5:0:0:0: [sdb] Attached SCSI removable disk
[ 4545.998118] usb 2-1: USB disconnect, device number 4
[ 4548.424062] usb 2-1: new high-speed USB device number 5 using ehci_hcd
[ 4548.565160] scsi6 : usb-storage 2-1:1.0
[ 4549.627908] scsi 6:0:0:0: Direct-Access     Verbatim STORE N GO       5.00 PQ: 0 ANSI: 6
[ 4549.634150] sd 6:0:0:0: Attached scsi generic sg2 type 0
[ 4550.280402] sd 6:0:0:0: [sdb] 3913728 512-byte logical blocks: (2.00 GB/1.86 GiB)
[ 4550.281515] sd 6:0:0:0: [sdb] Write Protect is off
[ 4550.281519] sd 6:0:0:0: [sdb] Mode Sense: 23 00 00 00
[ 4550.282641] sd 6:0:0:0: [sdb] No Caching mode page present
[ 4550.282645] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 4550.288271] sd 6:0:0:0: [sdb] No Caching mode page present
[ 4550.288276] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 4550.307974]  sdb: sdb1
[ 4550.312779] sd 6:0:0:0: [sdb] No Caching mode page present
[ 4550.312785] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 4550.312789] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[ 4584.815450] usb 2-1: USB disconnect, device number 5
[ 5187.609806] composite sync not supported

$ sudo lshw -C network
 *-network              
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=wl latency=0
       resources: irq:17 memory:fe8fc000-fe8fffff
  *-network UNCLAIMED
       description: Ethernet controller
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=64
       resources: memory:fe5fe000-fe5fffff

$ iwlist scan
lo        Interface doesn't support scanning.
 

$ sudo iwlist wlan0 scan
wlan0     Interface doesn't support scanning.
-----------------------------------------------
lsb_release -d
Description:                        Ubuntu 12.04.3 LTS

$ uname -mr
3.2.0-56-generic-pae i686

$ sudo service networking restart
stop: Unknown instance:
networking stop/waiting
==============================================
 
$ lsmod | grep "wlan_module_name"
:~$

 $ dmesg
0000000
[    0.425699] brd: module loaded
[    0.426536] loop: module loaded
[    0.426742] ata_piix 0000:00:1f.1: version 2.13
[    0.426759] ata_piix 0000:00:1f.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.426805] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.436074] scsi0 : ata_piix
[    0.436196] scsi1 : ata_piix
[    0.436589] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x6fa0 irq 14
[    0.436593] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x6fa8 irq 15
[    0.436647] ata_piix 0000:00:1f.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.436655] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    0.436887] ata2: port disabled--ignoring
[    0.436904] ACPI: Battery Slot [BAT0] (battery present)
[    0.592266] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.596085] scsi2 : ata_piix
[    0.596197] scsi3 : ata_piix
[    0.596601] ata3: SATA max UDMA/133 cmd 0x6eb0 ctl 0x6eb8 bmdma 0x6ee0 irq 17
[    0.596610] ata4: SATA max UDMA/133 cmd 0x6ec0 ctl 0x6ec8 bmdma 0x6ee8 irq 17
[    0.597072] Fixed MDIO Bus: probed
[    0.597096] tun: Universal TUN/TAP device driver, 1.6
[    0.597098] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.597199] PPP generic driver version 2.4.2
[    0.597316] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.597341] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    0.597369] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    0.597374] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    0.597421] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    0.597456] ehci_hcd 0000:00:1a.7: debug port 1
[    0.601345] ehci_hcd 0000:00:1a.7: cache line size of 64 is not supported
[    0.601529] ehci_hcd 0000:00:1a.7: irq 22, io mem 0xfed1c400
[    0.616580] ata1.00: ATAPI: TSSTcorpCD-RW/DVD-ROM TSL462D, DE04, max UDMA/33
[    0.624049] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    0.624451] hub 1-0:1.0: USB hub found
[    0.624457] hub 1-0:1.0: 4 ports detected
[    0.624556] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.624587] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.624592] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.624642] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    0.624678] ehci_hcd 0000:00:1d.7: debug port 1
[    0.628565] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
[    0.632480] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xfed1c000
[    0.648617] ata1.00: configured for UDMA/33
[    0.652047] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.652278] hub 2-0:1.0: USB hub found
[    0.652284] hub 2-0:1.0: 6 ports detected
[    0.652387] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.652408] uhci_hcd: USB Universal Host Controller Interface driver
[    0.652444] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.652459] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    0.652464] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    0.652519] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    0.652555] uhci_hcd 0000:00:1a.0: irq 20, io base 0x00006f20
[    0.652705] hub 3-0:1.0: USB hub found
[    0.652710] hub 3-0:1.0: 2 ports detected
[    0.652785] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.652795] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    0.652799] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    0.652846] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    0.652892] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00006f00
[    0.653043] hub 4-0:1.0: USB hub found
[    0.653048] hub 4-0:1.0: 2 ports detected
[    0.653121] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.653132] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.653136] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.653182] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    0.653212] uhci_hcd 0000:00:1d.0: irq 20, io base 0x00006f80
[    0.653361] hub 5-0:1.0: USB hub found
[    0.653365] hub 5-0:1.0: 2 ports detected
[    0.653434] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.653444] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.653448] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.653492] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    0.653523] uhci_hcd 0000:00:1d.1: irq 21, io base 0x00006f60
[    0.653669] hub 6-0:1.0: USB hub found
[    0.653673] hub 6-0:1.0: 2 ports detected
[    0.653747] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    0.653757] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.653761] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.653808] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    0.653840] uhci_hcd 0000:00:1d.2: irq 22, io base 0x00006f40
[    0.653985] hub 7-0:1.0: USB hub found
[    0.653990] hub 7-0:1.0: 2 ports detected
[    0.654127] usbcore: registered new interface driver libusual
[    0.654193] i8042: PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.704149] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.704161] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.704347] mousedev: PS/2 mouse device common for all mice
[    0.704534] rtc_cmos 00:03: RTC can wake from S4
[    0.704671] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    0.704707] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    0.704794] device-mapper: uevent: version 1.0.3
[    0.704876] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[    0.704906] EISA: Probing bus 0 at eisa.0
[    0.704915] Cannot allocate resource for EISA slot 1
[    0.704918] Cannot allocate resource for EISA slot 2
[    0.704920] Cannot allocate resource for EISA slot 3
[    0.704944] EISA: Detected 0 cards.
[    0.704958] cpufreq-nforce2: No nForce2 chipset.
[    0.704998] cpuidle: using governor ladder
[    0.705057] cpuidle: using governor menu
[    0.705059] EFI Variables Facility v0.08 2004-May-17
[    0.705303] TCP cubic registered
[    0.705449] NET: Registered protocol family 10
[    0.707186] NET: Registered protocol family 17
[    0.707200] Registering the dns_resolver key type
[    0.707231] Using IPI No-Shortcut mode
[    0.707345] PM: Hibernation image not present or could not be loaded.
[    0.707357] registered taskstats version 1
[    0.709290] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    0.979913] isapnp: No Plug & Play device found
[    0.981235] scsi 0:0:0:0: CD-ROM            TSSTcorp CDRW/DVD TSL462D DE04 PQ: 0 ANSI: 5
[    0.983340] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    0.983344] cdrom: Uniform CD-ROM driver Revision: 3.20
[    0.983489] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    0.983683] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    1.054016] Freeing initrd memory: 13876k freed
[    1.071508]   Magic number: 9:588:423
[    1.071638] rtc_cmos 00:03: setting system clock to 2013-12-03 09:24:04 UTC (1386062644)
[    1.071660] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.071662] EDD information not available.
[    1.384054] usb 5-2: new full-speed USB device number 2 using uhci_hcd
[    1.484136] ata3.00: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.484155] ata3.01: SATA link down (SStatus 0 SControl 300)
[    1.492474] ata3.00: ATA-8: FUJITSU MHW2080BH, 0085001C, max UDMA/100
[    1.492478] ata3.00: 156301488 sectors, multi 8: LBA48 NCQ (depth 0/32)
[    1.508477] ata3.00: configured for UDMA/100
[    1.508610] scsi 2:0:0:0: Direct-Access     ATA      FUJITSU MHW2080B 0085 PQ: 0 ANSI: 5
[    1.508822] sd 2:0:0:0: [sda] 156301488 512-byte logical blocks: (80.0 GB/74.5 GiB)
[    1.508878] sd 2:0:0:0: [sda] Write Protect is off
[    1.508882] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.508906] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.509240] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    1.594593]  sda: sda1 sda2 < sda5 sda6 >
[    1.594979] sd 2:0:0:0: [sda] Attached SCSI disk
[    2.040053] ata4.01: failed to resume link (SControl 0)
[    2.040106] ata4.00: SATA link down (SStatus 0 SControl 300)
[    2.040130] ata4.01: SATA link down (SStatus 0 SControl 0)
[    2.040211] Freeing unused kernel memory: 744k freed
[    2.040559] Write protecting the kernel text: 5840k
[    2.040573] Write protecting the kernel read-only data: 2388k
[    2.040575] NX-protecting the kernel data: 4400k
[    2.063880] udevd[89]: starting version 175
[    2.302124] sdhci: Secure Digital Host Controller Interface driver
[    2.302128] sdhci: Copyright(c) Pierre Ossman
[    2.302458] sdhci-pci 0000:03:01.1: SDHCI controller found [1180:0822] (rev 22)
[    2.302488] sdhci-pci 0000:03:01.1: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[    2.303540] mmc0: no vmmc regulator found
[    2.312752] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.0/usb5/5-2/5-2:1.0/input/input4
[    2.315847] generic-usb 0003:046D:C52F.0001: input,hidraw0: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:1d.0-2/input0
[    2.321640] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.0/usb5/5-2/5-2:1.1/input/input5
[    2.321798] generic-usb 0003:046D:C52F.0002: input,hiddev0,hidraw1: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1d.0-2/input1
[    2.321819] usbcore: registered new interface driver usbhid
[    2.321822] usbhid: USB HID core driver
[    2.331703] Registered led device: mmc0::
[    2.341101] mmc0: SDHCI controller on PCI [0000:03:01.1] using DMA
[    2.341148] firewire_ohci 0000:03:01.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    2.404088] firewire_ohci: Added fw-ohci device 0000:03:01.0, OHCI v1.10, 4 IR + 4 IT contexts, quirks 0x11
[    2.653861] EXT4-fs (sda5): INFO: recovery required on readonly filesystem
[    2.653866] EXT4-fs (sda5): write access will be enabled during recovery
[    2.904211] firewire_core: created device fw0: GUID 374fc0002a9d3981, S400
[    6.168407] EXT4-fs (sda5): recovery complete
[    6.169385] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
[    8.741859] Adding 4183036k swap on /dev/sda6.  Priority:-1 extents:1 across:4183036k
[    9.227856] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro
[   10.538793] udevd[372]: starting version 175
[   11.536335] lp: driver loaded but no devices found
[   12.755748] wmi: Mapper loaded
[   12.764435] lib80211: common routines for IEEE802.11 drivers
[   12.764439] lib80211_crypt: registered algorithm 'NULL'
[   12.800977] cfg80211: Calling CRDA to update world regulatory domain
[   13.352432] cfg80211: Calling CRDA to update world regulatory domain
[   13.960694] psmouse serio1: synaptics: Touchpad model: 1, fw: 6.3, id: 0x1a0b1, caps: 0xa04793/0x300000/0x0
[   13.960703] psmouse serio1: synaptics: serio: Synaptics pass-through port at isa0060/serio1/input0
[   13.996692] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input6
[   14.007299] ppdev: user-space parallel port driver
[   14.050449] r592 0000:03:01.2: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[   14.051573] r592: driver successfully loaded
[   14.158970] [drm] Initialized drm 1.1.0 20060810
[   14.298888] input: Dell WMI hotkeys as /devices/virtual/input/input7
[   14.310978] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   15.316796] wl: module license 'MIXED/Proprietary' taints kernel.
[   15.316801] Disabling lock debugging due to kernel taint
[   15.344343] wl 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   15.344354] wl 0000:0c:00.0: setting latency timer to 64
[   15.346808] malloc in abgphy done
[   15.347027] wl driver 6.20.155.1 (r326264) failed with code 21
[   15.347055] ------------[ cut here ]------------
[   15.347101] kernel BUG at include/net/cfg80211.h:2209!
[   15.347145] invalid opcode: 0000 [#1] SMP
[   15.347255] Modules linked in: wl(P+) sm_common nand nand_ids mtd nand_bch drm_kms_helper snd_hwdep bch snd_pcm dell_laptop joydev snd_seq_midi snd_rawmidi snd_seq_midi_event dcdbas dell_wmi drm parport_pc r592 ppdev snd_seq snd_timer snd_seq_device sparse_keymap snd cfg80211 psmouse nand_ecc memstick serio_raw mac_hid i2c_algo_bit soundcore video lib80211 snd_page_alloc wmi lp parport firewire_ohci sdhci_pci sdhci firewire_core crc_itu_t usbhid hid [last unloaded: cfg80211]
[   15.348014]
[   15.348014] Pid: 660, comm: modprobe Tainted: P           O 3.2.0-56-generic-pae #86-Ubuntu Dell Inc. Vostro 1500                     /0NX907
[   15.348014] EIP: 0060:[<f8ddd4b8>] EFLAGS: 00010246 CPU: 0
[   15.348014] EIP is at wdev_priv.part.7+0x3/0x5 [wl]
[   15.348014] EAX: 00000000 EBX: f7074c80 ECX: f7074c80 EDX: ef8ebc90
[   15.348014] ESI: ef8ebc90 EDI: ef8ebc0c EBP: ef925cec ESP: ef925cec
[   15.348014]  DS: 007b ES: 007b FS: 00d8 GS: 00e0 SS: 0068
[   15.348014] Process modprobe (pid: 660, ti=ef924000 task=f27ca610 task.ti=ef924000)
[   15.348014] Stack:
[   15.348014]  ef925d00 f8ddc944 f7074c80 ef8ebc90 ef8ebc0c ef925d14 f8dd559f ef8ebc00
[   15.348014]  f756b000 f7074800 ef925dc0 f8dd5f68 00000000 00000000 ffffff06 00000000
[   15.348014]  c1971f93 ef925d7d ef925db0 00000246 ef925d6e c174a4f9 0000000f 00054b93
[   15.348014] Call Trace:
[   15.348014]  [<f8ddc944>] wl_cfg80211_detach+0xc4/0xd0 [wl]
[   15.348014]  [<f8dd559f>] wl_free_if.isra.10+0x1f/0xa0 [wl]
[   15.348014]  [<f8dd5f68>] wl_free+0x58/0x250 [wl]
[   15.348014]  [<f8cf5e92>] ? wlc_attach+0xf6c/0xfda [wl]
[   15.348014]  [<f8ddd42b>] wl_pci_probe+0x51c/0x53c [wl]
[   15.348014]  [<c15ab67d>] ? _raw_spin_lock_irqsave+0x2d/0x40
[   15.348014]  [<c138ffc5>] ? pm_runtime_enable+0x45/0x70
[   15.348014]  [<c12d3b07>] local_pci_probe+0x47/0xb0
[   15.348014]  [<c12d5008>] pci_device_probe+0x68/0x90
[   15.348014]  [<c11a9e77>] ? sysfs_create_link+0x17/0x20
[   15.348014]  [<c1387d6d>] really_probe+0x4d/0x150
[   15.348014]  [<c13913f9>] ? pm_runtime_barrier+0x49/0xb0
[   15.348014]  [<c1387faa>] driver_probe_device+0x3a/0x60
[   15.348014]  [<c1388061>] __driver_attach+0x91/0xa0
[   15.348014]  [<c1387fd0>] ? driver_probe_device+0x60/0x60
[   15.348014]  [<c13870e1>] bus_for_each_dev+0x51/0x80
[   15.348014]  [<c1387ba1>] driver_attach+0x21/0x30
[   15.348014]  [<c1387fd0>] ? driver_probe_device+0x60/0x60
[   15.348014]  [<c138787f>] bus_add_driver+0x17f/0x260
[   15.348014]  [<c12d5030>] ? pci_device_probe+0x90/0x90
[   15.348014]  [<c1388536>] driver_register+0x66/0x110
[   15.348014]  [<c12d4db2>] __pci_register_driver+0x42/0xc0
[   15.348014]  [<f8fae017>] wl_module_init+0x17/0x1000 [wl]
[   15.348014]  [<c1003035>] do_one_initcall+0x35/0x170
[   15.348014]  [<f8fae000>] ? 0xf8fadfff
[   15.348014]  [<c10968ec>] sys_init_module+0xac/0x210
[   15.348014]  [<c15b295f>] sysenter_do_call+0x12/0x28
[   15.348014] Code: d0 e8 fd e0 7c c8 89 f0 e8 76 8a ff ff 89 d8 e8 2f 55 4f c8 31 d2 89 f8 e8 76 a5 5a c8 58 5b 5e 5f 5d c3 55 89 e5 0f 0b 55 89 e5 <0f> 0b 55 89 e5 66 66 66 66 90 0f 0b 55 89 e5 66 66 66 66 90 0f
[   15.348014] EIP: [<f8ddd4b8>] wdev_priv.part.7+0x3/0x5 [wl] SS:ESP 0068:ef925cec
[   15.354744] ---[ end trace ad46c02fbf192219 ]---
[   15.605570] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   15.605637] i915 0000:00:02.0: setting latency timer to 64
[   15.626569] mtrr: type mismatch for e0000000,10000000 old: write-back new: write-combining
[   15.626648] [drm] MTRR allocation failed.  Graphics performance may suffer.
[   15.628215] i915 0000:00:02.0: irq 43 for MSI/MSI-X
[   15.628277] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   15.628334] [drm] Driver supports precise vblank timestamp query.
[   15.628434] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   15.681898] composite sync not supported
[   15.773562] r852 0000:03:01.3: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[   15.773825] r852: driver loaded successfully
[   15.934266] [drm] initialized overlay support
[   15.934376] composite sync not supported
[   16.100368] fbcon: inteldrmfb (fb0) is primary device
[   16.552886] Console: switching to colour frame buffer device 160x50
[   16.557752] fb0: inteldrmfb frame buffer device
[   16.557789] drm: registered panic notifier
[   16.571630] acpi device:34: registered as cooling_device1
[   16.573098] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/LNXVIDEO:01/input/input8
[   16.573381] ACPI: Video Device [VID1] (multi-head: yes  rom: no  post: no)
[   16.573469] [Firmware Bug]: Duplicate ACPI video bus devices for the same VGA controller, please try module parameter "video.allow_duplicates=1"if the current driver doesn't work.
[   16.574556] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   16.574673] snd_hda_intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   16.574829] snd_hda_intel 0000:00:1b.0: irq 44 for MSI/MSI-X
[   16.574914] snd_hda_intel 0000:00:1b.0: setting latency timer to 64
[   16.691582] Bluetooth: Core ver 2.16
[   16.691700] NET: Registered protocol family 31
[   16.691743] Bluetooth: HCI device and connection manager initialized
[   16.691799] Bluetooth: HCI socket layer initialized
[   16.691838] Bluetooth: L2CAP socket layer initialized
[   16.692657] Bluetooth: SCO socket layer initialized
[   16.695616] type=1400 audit(1386080660.116:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=667 comm="apparmor_parser"
[   16.696325] type=1400 audit(1386080660.120:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=667 comm="apparmor_parser"
[   16.696743] type=1400 audit(1386080660.120:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=667 comm="apparmor_parser"
[   16.793552] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   16.793611] Bluetooth: BNEP filters: protocol multicast
[   16.860776] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   16.868073] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   17.369288] type=1400 audit(1386080660.792:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=705 comm="apparmor_parser"
[   17.376518] type=1400 audit(1386080660.800:6): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=705 comm="apparmor_parser"
[   17.537263] cfg80211: World regulatory domain updated:
[   17.540261] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   17.543249] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.546260] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   17.549228] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   17.552161] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.555054] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.566312] cfg80211: World regulatory domain updated:
[   17.569166] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   17.572158] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.574981] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   17.577794] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   17.580560] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.583271] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.605485] composite sync not supported
[   18.485230] init: failsafe main process (758) killed by TERM signal
[   23.698934] type=1400 audit(1386080667.124:7): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=884 comm="apparmor_parser"
[   23.699390] type=1400 audit(1386080667.124:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper//chromium_browser" pid=884 comm="apparmor_parser"
[   23.703196] type=1400 audit(1386080667.124:9): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=885 comm="apparmor_parser"
[   23.704871] type=1400 audit(1386080667.128:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=885 comm="apparmor_parser"
[   23.705176] type=1400 audit(1386080667.128:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=885 comm="apparmor_parser"
[   23.825571] type=1400 audit(1386080667.248:12): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=886 comm="apparmor_parser"
[   23.832957] type=1400 audit(1386080667.256:13): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince//launchpad_integration" pid=886 comm="apparmor_parser"
[   23.834585] type=1400 audit(1386080667.256:14): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince//sanitized_helper" pid=886 comm="apparmor_parser"
[   23.836050] type=1400 audit(1386080667.256:15): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=886 comm="apparmor_parser"
[   23.840552] type=1400 audit(1386080667.264:16): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer//launchpad_integration" pid=886 comm="apparmor_parser"
[   26.391915] composite sync not supported
[   26.724169] composite sync not supported
[   32.653031] composite sync not supported
[   39.683889] composite sync not supported
[   46.249324] composite sync not supported
[   46.873957] composite sync not supported
[   59.136627] composite sync not supported
[ 1413.495331] composite sync not supported
[ 1788.320064] usb 2-1: new high-speed USB device number 3 using ehci_hcd
[ 1788.577095] Initializing USB Mass Storage driver...
[ 1788.577252] scsi4 : usb-storage 2-1:1.0
[ 1788.577361] usbcore: registered new interface driver usb-storage
[ 1788.577364] USB Mass Storage support registered.
[ 1789.641149] scsi 4:0:0:0: Direct-Access     Verbatim STORE N GO       5.00 PQ: 0 ANSI: 6
[ 1789.646686] sd 4:0:0:0: Attached scsi generic sg2 type 0
[ 1790.316030] sd 4:0:0:0: [sdb] 3913728 512-byte logical blocks: (2.00 GB/1.86 GiB)
[ 1790.317128] sd 4:0:0:0: [sdb] Write Protect is off
[ 1790.317131] sd 4:0:0:0: [sdb] Mode Sense: 23 00 00 00
[ 1790.318128] sd 4:0:0:0: [sdb] No Caching mode page present
[ 1790.318132] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 1790.323757] sd 4:0:0:0: [sdb] No Caching mode page present
[ 1790.323763] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 1790.343344]  sdb: sdb1
[ 1790.348145] sd 4:0:0:0: [sdb] No Caching mode page present
[ 1790.348151] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 1790.348155] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[ 1828.087038] usb 2-1: USB disconnect, device number 3
[ 2506.239828] composite sync not supported
[ 4359.212076] usb 2-1: new high-speed USB device number 4 using ehci_hcd
[ 4359.353250] scsi5 : usb-storage 2-1:1.0
[ 4360.416086] scsi 5:0:0:0: Direct-Access     Verbatim STORE N GO       5.00 PQ: 0 ANSI: 6
[ 4360.418895] sd 5:0:0:0: Attached scsi generic sg2 type 0
[ 4361.059438] sd 5:0:0:0: [sdb] 3913728 512-byte logical blocks: (2.00 GB/1.86 GiB)
[ 4361.060559] sd 5:0:0:0: [sdb] Write Protect is off
[ 4361.060563] sd 5:0:0:0: [sdb] Mode Sense: 23 00 00 00
[ 4361.061677] sd 5:0:0:0: [sdb] No Caching mode page present
[ 4361.061681] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 4361.067307] sd 5:0:0:0: [sdb] No Caching mode page present
[ 4361.067312] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 4361.086919]  sdb: sdb1
[ 4361.092440] sd 5:0:0:0: [sdb] No Caching mode page present
[ 4361.092445] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 4361.092449] sd 5:0:0:0: [sdb] Attached SCSI removable disk
[ 4545.998118] usb 2-1: USB disconnect, device number 4
[ 4548.424062] usb 2-1: new high-speed USB device number 5 using ehci_hcd
[ 4548.565160] scsi6 : usb-storage 2-1:1.0
[ 4549.627908] scsi 6:0:0:0: Direct-Access     Verbatim STORE N GO       5.00 PQ: 0 ANSI: 6
[ 4549.634150] sd 6:0:0:0: Attached scsi generic sg2 type 0
[ 4550.280402] sd 6:0:0:0: [sdb] 3913728 512-byte logical blocks: (2.00 GB/1.86 GiB)
[ 4550.281515] sd 6:0:0:0: [sdb] Write Protect is off
[ 4550.281519] sd 6:0:0:0: [sdb] Mode Sense: 23 00 00 00
[ 4550.282641] sd 6:0:0:0: [sdb] No Caching mode page present
[ 4550.282645] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 4550.288271] sd 6:0:0:0: [sdb] No Caching mode page present
[ 4550.288276] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 4550.307974]  sdb: sdb1
[ 4550.312779] sd 6:0:0:0: [sdb] No Caching mode page present
[ 4550.312785] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 4550.312789] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[ 4584.815450] usb 2-1: USB disconnect, device number 5
[ 5187.609806] composite sync not supported

$ sudo lshw -C network
 *-network              
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=wl latency=0
       resources: irq:17 memory:fe8fc000-fe8fffff
  *-network UNCLAIMED
       description: Ethernet controller
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=64
       resources: memory:fe5fe000-fe5fffff

$ iwlist scan
lo        Interface doesn't support scanning.
 

$ sudo iwlist wlan0 scan
wlan0     Interface doesn't support scanning.
-----------------------------------------------
lsb_release -d
Description:                        Ubuntu 12.04.3 LTS

$ uname -mr
3.2.0-56-generic-pae i686

$ sudo service networking restart
stop: Unknown instance:
networking stop/waiting
==============================================
```[/CODE]

---

### Post by varunendra on 2013-12-07
Wow !! For a moment I thought I was reading a text book ! :P
> **fracas said:**
> ...nor do I know how to use “code tags”.

Please follow the "**Using Code Tags**" link in my signature to see how.

And to fix your wireless, please do the following :
```
sudo apt-get purge bcmwl-kernel-source
```
This will purge (remove) the proprietary "sta" driver from your system, which is a wrong driver for you wireless card. Don't install it again.

The correct driver "b43" is already present in the kernel, but it needs a proprietary firmware to work. To install this firmware, download the "linux-firmware-nonfree" package from here : [http://packages.ubuntu.com/precise/all/linux-firmware-nonfree/download](http://packages.ubuntu.com/precise/all/linux-firmware-nonfree/download)

Copy the downloaded .deb file to your Ubuntu machine and double-click it to install. Reboot and confirm if everything is working properly (purging the "sta" driver will also make your Ethernet (wired) connection work).

Let me know if any problems remain after following above instructions.

**PS:**
And you should edit your first post to wrap the output part within 'Code' tags now. :)

---

### Post by fracas on 2013-12-07
Varunendra, I am very grateful for your response.  I am afraid I am caught in a Linux “Catch 22”.  I downloaded the “linux-firmware-nonfree” package on a Windows PC and installed it to my Ubuntu laptop via flash drive.  When I double-clicked it, the .deb file took me to the Download Center for an additional download.  Sadly, I need an internet connection to download from the Center – thus the “Catch 22”.
 
I have read the instructions on posting “no internet” problems and using “code tags”.  I will try to revise my post using “code tags” as per your request.
 
I would really appreciate a work-around for the Catch 22 if there is one.  Thanks.

---

### Post by varunendra on 2013-12-09
> **fracas said:**
> When I double-clicked it, the .deb file took me to the Download Center[COLOR="#FF0000"] for an additional download[/COLOR].

Are you sure it asked for some additional download? Ubuntu Software Center is the default installer for .deb files in default Ubuntu, so double-clicking a .deb file will open it no doubt. But the "linux-firmware-nonfree" package has no dependencies and no version boundations, so it should have presented you an active "Install" button straight away, and shouldn't have asked for ANY additional download.

Anyway, try again and just click the "Install" button if it is activated when Software Center opens up. If it seems inactive, close it and do the following (make sure to close Software Center before doing this) -

**1)** Copy/Move the "linux-firmware-nonfree_1.11_all.deb" package on your Desktop.

**2)** Open a terminal and do -
```
sudo dpkg -i Desktop/linux-firmware-nonfree_1.11_all.deb
```
..and report back if it returns any errors. If not, just reboot after the command finishes its job, and see if your wireless works. It should.

As a matter of fact, the firmware deb package is just an archive of some firmware files which need to be copied in the correct directory - /lib/firmware. Of the hundreds of files, we need only 7 files (of which only any one will be used for your device). We can as well just extract and copy it (the "b43" directory within the package) manually, but installing the .deb file is usually much easier. So be assured, there is no catch 22 in our way. :)

---

### Post by fracas on 2013-12-09
Varun:
 
I tried double-clicking the deb file again, and again it took me to the Software Center where a greyed-out &#8220;install&#8221; button did nothing (I was mistaken about &#8220;additional files&#8221;).  So I followed your additional instructions and, lo and behold, I have network connectivity! 
 
I will mark this problem as &#8220;Solved&#8221;.  I am very grateful for your assistance and expertise.  Thanks again!

---

### Post by varunendra on 2013-12-09
Glad I could help. :)

Remember not to install the proprietary "STA" driver again. The BCM4311 card works with the native b43 driver and only the firmware needs to be installed manually which you did above. It is one time task and you won't need to do it again unless you do a reinstall of Ubuntu.

Good luck, and have a great time with Ubuntu and the forums here ! :)

---

