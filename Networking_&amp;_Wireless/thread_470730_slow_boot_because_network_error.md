---
title: "slow boot because network error"
date: 2007-06-11
forum: Networking &amp; Wireless
---

### Post by sandervdv on 2007-06-11
Hi all,

There are a few post about slow boottime, but i couldn't find the solution i was looking for.

My boottime is about 2 minutes, way to long for my specs. it all started when i configured my wifi.

my sysspecs are: 
Dell inspiron 1501
Amd64 x2
1gig ram
Network card configured with Ndiswrapper: bcmwl5 with THIS [http://ubuntu1501.blogspot.com/2007/01/fixing-wifi-on-dell-1501.html](http://ubuntu1501.blogspot.com/2007/01/fixing-wifi-on-dell-1501.html)  guide
i'm using Feisty

my dmesg spits out:
```
[    6.612000] ACPI: PCI Interrupt 0000:00:13.5[D] -> GSI 19 (level, low) -> IRQ 20
[    6.612000] ehci_hcd 0000:00:13.5: EHCI Host Controller
[    6.612000] ehci_hcd 0000:00:13.5: new USB bus registered, assigned bus number 4
[    6.612000] ehci_hcd 0000:00:13.5: debug port 1
[    6.612000] ehci_hcd 0000:00:13.5: irq 20, io mem 0xc0004400
[    6.612000] ehci_hcd 0000:00:13.5: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    6.612000] usb usb4: configuration #1 chosen from 1 choice
[    6.612000] hub 4-0:1.0: USB hub found
[    6.612000] hub 4-0:1.0: 10 ports detected
[    6.616000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[    6.616000] sda: Write Protect is off
[    6.616000] sda: Mode Sense: 00 3a 00 00
[    6.616000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.616000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[    6.616000] sda: Write Protect is off
[    6.616000] sda: Mode Sense: 00 3a 00 00
[    6.616000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.616000]  sda:<6>usb 1-1: USB disconnect, address 2
[    6.716000] b44.c:v1.01 (Jun 16, 2006)
[    6.716000] ACPI: PCI Interrupt 0000:08:00.0[A] -> GSI 21 (level, low) -> IRQ 21
[    6.720000] SB600_PATA: IDE controller at PCI slot 0000:00:14.1
[    6.720000] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 16
[    6.720000] SB600_PATA: chipset revision 0
[    6.720000] SB600_PATA: not 100% native mode: will probe irqs later
[    6.720000]     ide0: BM-DMA at 0x8420-0x8427, BIOS settings: hda:DMA, hdb:pio
[    6.720000] Probing IDE interface ide0...
[    6.720000] eth0: Broadcom 4400 10/100BaseT Ethernet 00:19:b9:62:52:0e
[    7.004000]  sda1 sda2 sda3
[    7.036000] sd 0:0:0:0: Attached scsi disk sda
[    7.036000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    7.252000] Attempting manual resume
[    7.252000] swsusp: Resume From Partition 8:3
[    7.252000] PM: Checking swsusp image.
[    7.252000] PM: Resume from disk failed.
[    7.300000] kjournald starting.  Commit interval 5 seconds
[    7.300000] EXT3-fs: mounted filesystem with ordered data mode.
[    7.348000] usb 1-1: new low speed USB device using ohci_hcd and address 3
[    7.468000] hda: TSSTcorp DVD+/-RW TS-L632D, ATAPI CD/DVD-ROM drive
[    7.572000] usb 1-1: configuration #1 chosen from 1 choice
[    8.160000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[    8.184000] ACPI: PCI Interrupt 0000:00:13.3[B] -> GSI 17 (level, low) -> IRQ 17
[    8.184000] ohci_hcd 0000:00:13.3: OHCI Host Controller
[    8.184000] ohci_hcd 0000:00:13.3: new USB bus registered, assigned bus number 5
[    8.184000] ohci_hcd 0000:00:13.3: irq 17, io mem 0xc0008000
[    8.240000] usb usb5: configuration #1 chosen from 1 choice
[    8.240000] hub 5-0:1.0: USB hub found
[    8.240000] hub 5-0:1.0: 2 ports detected
[    8.344000] ACPI: PCI Interrupt 0000:00:13.4[C] -> GSI 18 (level, low) -> IRQ 18
[    8.344000] ohci_hcd 0000:00:13.4: OHCI Host Controller
[    8.344000] ohci_hcd 0000:00:13.4: new USB bus registered, assigned bus number 6
[    8.344000] ohci_hcd 0000:00:13.4: irq 18, io mem 0xc0009000
[    8.400000] usb usb6: configuration #1 chosen from 1 choice
[    8.400000] hub 6-0:1.0: USB hub found
[    8.400000] hub 6-0:1.0: 2 ports detected
[   12.700000] Linux agpgart interface v0.102 (c) Dave Jones
[   12.732000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   12.788000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   13.096000] sdhci: Secure Digital Host Controller Interface driver
[   13.096000] sdhci: Copyright(c) Pierre Ossman
[   13.096000] sdhci: SDHCI controller found at 0000:08:01.0 [1180:0822] (rev 19)
[   13.096000] ACPI: PCI Interrupt 0000:08:01.0[B] -> GSI 20 (level, low) -> IRQ 22
[   13.096000] mmc0: SDHCI at 0xc0302000 irq 22 DMA
[   13.344000] input: PC Speaker as /class/input/input2
[   13.600000] usbcore: registered new interface driver hiddev
[   13.640000] hda: ATAPI 24X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(33)
[   13.640000] Uniform CD-ROM driver Revision: 3.20
[   13.740000] input: Logitech USB-PS/2 Optical Mouse as /class/input/input3
[   13.740000] input: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:13.0-1
[   13.740000] usbcore: registered new interface driver usbhid
[   13.740000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   13.812000] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x180b1, caps: 0xa04713/0x200000
[   13.852000] input: SynPS/2 Synaptics TouchPad as /class/input/input4
[   13.944000] ACPI: PCI Interrupt 0000:00:14.2[A] -> GSI 16 (level, low) -> IRQ 16
[   14.200000] NET: Registered protocol family 17
[   14.600000] fuse init (API version 7.8)
[   14.704000] lp: driver loaded but no devices found
[   17.180000] Adding 514072k swap on /dev/disk/by-uuid/5e23040a-ca12-43bd-82ac-025083494d06.  Priority:-1 extents:1 across:514072k
[   17.380000] EXT3 FS on sda1, internal journal
[   17.656000] kjournald starting.  Commit interval 5 seconds
[   17.656000] EXT3 FS on sda2, internal journal
[   17.656000] EXT3-fs: mounted filesystem with ordered data mode.
[B][U][   21.612000] ndiswrapper version 1.41 loaded (smp=yes)
[   21.700000] ndiswrapper: driver bcmwl5 (Broadcom,10/12/2006, 4.100.15.5) loaded[/U][/B]
[B][U][   21.700000] ACPI: PCI Interrupt 0000:05:00.0[A] -> GSI 18 (level, low) -> IRQ 18
[   21.700000] PCI: Setting latency timer of device 0000:05:00.0 to 64
[   21.704000] ndiswrapper: using IRQ 18
[   22.348000] wlan0: ethernet device 00:19:7e:53:b2:c4 using NDIS driver: bcmwl5, version: 0x4640f05, NDIS version: 0x501, vendor: '', 14E4:4311.5.conf
[   22.348000] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   22.348000] usbcore: registered new interface driver ndiswrapper
[   56.292000] NET: Registered protocol family 10
[   56.292000] lo: Disabled Privacy Extensions
[   56.292000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   56.292000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   91.444000] ibm_acpi: ec object not found
[   91.476000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   91.520000] ACPI: AC Adapter [ACAD] (on-line)
[   91.580000] Using specific hotkey driver
[   91.668000] ACPI: Battery Slot [BAT1] (battery present)[/U][/B]
[   91.680000] No dock devices found.
[   91.688000] input: Power Button (FF) as /class/input/input5
[   91.688000] ACPI: Power Button (FF) [PWRF]
[   91.692000] input: Power Button (CM) as /class/input/input6
[   91.692000] ACPI: Power Button (CM) [PWRB]
[   91.692000] input: Sleep Button (CM) as /class/input/input7
[   91.692000] ACPI: Sleep Button (CM) [SLPB]
[   91.692000] input: Lid Switch as /class/input/input8
[   91.692000] ACPI: Lid Switch [LID]
[   91.804000] wmi_add device=f6921c00
[   91.804000] calling WQBA
[   91.812000] pcc_acpi: loading...
[   92.180000] powernow-k8: Found 2 AMD Turion(tm) 64 X2 Mobile Technology TL-50 processors (version 2.00.00)
[   92.180000] powernow-k8:    0 : fid 0x8 (1600 MHz), vid 0x12
[   92.180000] powernow-k8:    1 : fid 0x0 (800 MHz), vid 0x1e
[  101.268000] ppdev: user-space parallel port driver
[  101.444000] [fglrx] Maximum main memory to use for locked dma buffers: 802 MBytes.
[  101.444000] [fglrx] module loaded - fglrx 8.34.8 [Feb 20 2007] on minor 0
[  101.476000] ACPI: PCI Interrupt 0000:01:05.0[A] -> GSI 17 (level, low) -> IRQ 17
[  103.324000] [fglrx] total      GART = 130023424
[  103.324000] [fglrx] free       GART = 114032640
[  103.324000] [fglrx] max single GART = 114032640
[  103.324000] [fglrx] total      LFB  = 134217728
[  103.324000] [fglrx] free       LFB  = 119828480
[  103.324000] [fglrx] max single LFB  = 119828480
[  103.324000] [fglrx] total      Inv  = 0
[  103.324000] [fglrx] free       Inv  = 0
[  103.324000] [fglrx] max single Inv  = 0
[  103.324000] [fglrx] total      TIM  = 0
[  111.156000] hda-intel: Invalid position buffer, using LPIB read method instead.
[  120.196000] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  140.560000] wlan0: no IPv6 routers present
```

I Bolted the problem area

In boot it gives the followin message
```
usdevd-event 4367 Rename_netif: Error changing netif name wlan0 to eth1
```

The wlan does work, so that is not the problem

What to do? thanx for the help

---

### Post by sandervdv on 2007-06-11
I actualy found a solution. it's part of bug #108152 :D

Solution:
Edit the /etc/network/interface and delete everything except:
```

auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
```

***_Don't forget to backup your original file_***

---

### Post by Steogede on 2007-06-25
Just a quick note to say thanks.  This problem had been bugging me with my HP Pavilion dv8000, since about Ubuntu 6.04 - I had been bypassing it by pressing Ctrl-Alt-Delete when the booting stalled.

-- edited to add a link to the original bug

[https://bugs.launchpad.net/ubuntu/+bug/108152](https://bugs.launchpad.net/ubuntu/+bug/108152)

---

### Post by danpre on 2007-08-23
I'm using KUBUNTU and knetworkmanager, so I have commented out from

/etc/network/interface and delete everything except:
```

auto lo
iface lo inet loopback

```

If you don't need network before kde starts, you don't need anything except lo in interfaces.

Now it boots up much faster.

DANIeL

---

