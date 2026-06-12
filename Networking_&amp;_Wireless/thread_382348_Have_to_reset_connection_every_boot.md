---
title: "Have to reset connection every boot"
date: 2007-03-11
forum: Networking &amp; Wireless
---

### Post by hatstand on 2007-03-11
Hi,

I recently changed my IP. I have the same set up as before (Cable >> Router >> Ubuntu and Win XP

The Win XP box works fine, but now I have to go to System >>> Admin >>> networking and reset the connection every time I boot. Very tedious.

Any ideas? Help much appreciated.

---

### Post by Mr. C. on 2007-03-12
What do you mean "reset" ?

If your router is acting as a DHCP server, it is responsible for supplying the IP information.  Ubuntu will run the dhclient app for your interface on startup, which will request DHCP information.

Check /var/log/syslog for dhclient messages, such as

```
Mar 11 15:30:53 gumby dhclient: bound to 192.168.1.102 -- renewal in 1402 seconds.
```

MrC

---

### Post by hatstand on 2007-03-12
I mean I have to click the little tick box, first to remove the tick, then to put it back. I get a message saying "activating network connection", so I guess that I mean I have to deactivate it then reactivate it.

Here is the latest from syslog:


Mar 11 21:40:00 mat-desktop kernel: [17179572.236000] pnp: 00:02: ioport range 0x4000-0x407f could not be reserved
Mar 11 21:40:00 mat-desktop kernel: [17179572.236000] pnp: 00:02: ioport range 0x5000-0x500f has been reserved
Mar 11 21:40:00 mat-desktop kernel: [17179572.236000] PCI: Bridge: 0000:00:01.0
Mar 11 21:40:00 mat-desktop kernel: [17179572.236000]   IO window: disabled.
Mar 11 21:40:00 mat-desktop kernel: [17179572.236000]   MEM window: e8000000-e9ffffff
Mar 11 21:40:00 mat-desktop kernel: [17179572.236000]   PREFETCH window: e4000000-e7ffffff
Mar 11 21:40:00 mat-desktop kernel: [17179572.236000] PCI: Setting latency timer of device 0000:00:01.0 to 64
Mar 11 21:40:00 mat-desktop kernel: [17179572.236000] NET: Registered protocol family 2
Mar 11 21:40:00 mat-desktop kernel: [17179572.276000] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Mar 11 21:40:00 mat-desktop kernel: [17179572.276000] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Mar 11 21:40:00 mat-desktop kernel: [17179572.276000] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Mar 11 21:40:00 mat-desktop kernel: [17179572.280000] TCP: Hash tables configured (established 131072 bind 65536)
Mar 11 21:40:00 mat-desktop kernel: [17179572.280000] TCP reno registered
Mar 11 21:40:00 mat-desktop kernel: [17179572.280000] audit: initializing netlink socket (disabled)
Mar 11 21:40:00 mat-desktop kernel: [17179572.280000] audit(1173649175.280:1): initialized
Mar 11 21:40:00 mat-desktop kernel: [17179572.280000] VFS: Disk quotas dquot_6.5.1
Mar 11 21:40:00 mat-desktop kernel: [17179572.280000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Mar 11 21:40:00 mat-desktop kernel: [17179572.280000] Initializing Cryptographic API
Mar 11 21:40:00 mat-desktop kernel: [17179572.280000] io scheduler noop registered
Mar 11 21:40:00 mat-desktop kernel: [17179572.280000] io scheduler anticipatory registered
Mar 11 21:40:00 mat-desktop kernel: [17179572.280000] io scheduler deadline registered
Mar 11 21:40:00 mat-desktop kernel: [17179572.280000] io scheduler cfq registered (default)
Mar 11 21:40:00 mat-desktop kernel: [17179572.280000] PCI: Bypassing VIA 8237 APIC De-Assert Message
Mar 11 21:40:00 mat-desktop kernel: [17179572.280000] isapnp: Scanning for PnP cards...
Mar 11 21:40:00 mat-desktop kernel: [17179577.436000] hda: 78165360 sectors (40020 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(100)
Mar 11 21:40:00 mat-desktop kernel: [17179577.436000] hda: cache flushes supported
Mar 11 21:40:00 mat-desktop kernel: [17179577.436000]  hda: hda1 hda2 hda3 < hda5 >
Mar 11 21:40:00 mat-desktop kernel: [17179577.520000] hdc: ATAPI 48X CD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
Mar 11 21:40:00 mat-desktop kernel: [17179577.520000] Uniform CD-ROM driver Revision: 3.20
Mar 11 21:40:00 mat-desktop kernel: [17179577.528000] hdd: ATAPI 48X DVD-ROM drive, 254kB Cache, UDMA(33)
Mar 11 21:40:00 mat-desktop kernel: [17179577.820000] ieee1394: Initialized config rom entry `ip1394'
Mar 11 21:40:00 mat-desktop kernel: [17179577.820000] ACPI: PCI Interrupt 0000:00:0b.0[A] -> GSI 19 (level, low) -> IRQ 177
Mar 11 21:40:00 mat-desktop kernel: [17179577.820000] PCI: Via IRQ fixup for 0000:00:0b.0, from 3 to 1
Mar 11 21:40:00 mat-desktop kernel: [17179577.912000] usbcore: registered new driver usbfs
Mar 11 21:40:00 mat-desktop kernel: [17179577.912000] usbcore: registered new driver hub
Mar 11 21:40:00 mat-desktop kernel: [17179577.916000] USB Universal Host Controller Interface driver v3.0
Mar 11 21:40:00 mat-desktop kernel: [17179577.924000] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[177]  MMIO=[eb002000-eb0027ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
Mar 11 21:40:00 mat-desktop kernel: [17179577.928000] ACPI: PCI Interrupt Link [ALKB] BIOS reported IRQ 0, using IRQ 21
Mar 11 21:40:00 mat-desktop kernel: [17179577.928000] ACPI: PCI Interrupt Link [ALKB] enabled at IRQ 21
Mar 11 21:40:00 mat-desktop kernel: [17179577.928000] ACPI: PCI Interrupt 0000:00:10.0[A] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 185
Mar 11 21:40:00 mat-desktop kernel: [17179577.928000] PCI: Via IRQ fixup for 0000:00:10.0, from 255 to 9
Mar 11 21:40:00 mat-desktop kernel: [17179577.928000] uhci_hcd 0000:00:10.0: UHCI Host Controller
Mar 11 21:40:00 mat-desktop kernel: [17179577.928000] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
Mar 11 21:40:00 mat-desktop kernel: [17179577.928000] uhci_hcd 0000:00:10.0: irq 185, io base 0x0000cc00
Mar 11 21:40:00 mat-desktop kernel: [17179577.928000] usb usb1: configuration #1 chosen from 1 choice
Mar 11 21:40:00 mat-desktop kernel: [17179577.928000] hub 1-0:1.0: USB hub found
Mar 11 21:40:00 mat-desktop kernel: [17179577.928000] hub 1-0:1.0: 2 ports detected
Mar 11 21:40:00 mat-desktop kernel: [17179578.036000] ACPI: PCI Interrupt 0000:00:10.1[A] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 185
Mar 11 21:40:00 mat-desktop kernel: [17179578.036000] PCI: Via IRQ fixup for 0000:00:10.1, from 255 to 9
Mar 11 21:40:00 mat-desktop kernel: [17179578.036000] uhci_hcd 0000:00:10.1: UHCI Host Controller
Mar 11 21:40:00 mat-desktop kernel: [17179578.036000] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
Mar 11 21:40:00 mat-desktop kernel: [17179578.036000] uhci_hcd 0000:00:10.1: irq 185, io base 0x0000d000
Mar 11 21:40:00 mat-desktop kernel: [17179578.036000] usb usb2: configuration #1 chosen from 1 choice
Mar 11 21:40:00 mat-desktop kernel: [17179578.036000] hub 2-0:1.0: USB hub found
Mar 11 21:40:00 mat-desktop kernel: [17179578.036000] hub 2-0:1.0: 2 ports detected
Mar 11 21:40:00 mat-desktop kernel: [17179578.144000] ACPI: PCI Interrupt 0000:00:10.2[B] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 185
Mar 11 21:40:00 mat-desktop kernel: [17179578.144000] PCI: Via IRQ fixup for 0000:00:10.2, from 255 to 9
Mar 11 21:40:00 mat-desktop kernel: [17179578.144000] uhci_hcd 0000:00:10.2: UHCI Host Controller
Mar 11 21:40:00 mat-desktop kernel: [17179578.144000] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
Mar 11 21:40:00 mat-desktop kernel: [17179578.144000] uhci_hcd 0000:00:10.2: irq 185, io base 0x0000d400
Mar 11 21:40:00 mat-desktop kernel: [17179578.144000] usb usb3: configuration #1 chosen from 1 choice
Mar 11 21:40:00 mat-desktop kernel: [17179578.144000] hub 3-0:1.0: USB hub found
Mar 11 21:40:00 mat-desktop kernel: [17179578.144000] hub 3-0:1.0: 2 ports detected
Mar 11 21:40:00 mat-desktop kernel: [17179578.252000] ACPI: PCI Interrupt 0000:00:10.3[B] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 185
Mar 11 21:40:00 mat-desktop kernel: [17179578.252000] PCI: Via IRQ fixup for 0000:00:10.3, from 255 to 9
Mar 11 21:40:00 mat-desktop kernel: [17179578.252000] uhci_hcd 0000:00:10.3: UHCI Host Controller
Mar 11 21:40:00 mat-desktop kernel: [17179578.252000] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
Mar 11 21:40:00 mat-desktop kernel: [17179578.252000] uhci_hcd 0000:00:10.3: irq 185, io base 0x0000d800
Mar 11 21:40:00 mat-desktop kernel: [17179578.252000] usb usb4: configuration #1 chosen from 1 choice
Mar 11 21:40:00 mat-desktop kernel: [17179578.252000] hub 4-0:1.0: USB hub found
Mar 11 21:40:00 mat-desktop kernel: [17179578.252000] hub 4-0:1.0: 2 ports detected
Mar 11 21:40:00 mat-desktop kernel: [17179578.276000] usb 1-1: new full speed USB device using uhci_hcd and address 2
Mar 11 21:40:00 mat-desktop kernel: [17179578.364000] ACPI: PCI Interrupt 0000:00:10.4[C] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 185
Mar 11 21:40:00 mat-desktop kernel: [17179578.364000] PCI: Via IRQ fixup for 0000:00:10.4, from 255 to 9
Mar 11 21:40:00 mat-desktop kernel: [17179578.364000] ehci_hcd 0000:00:10.4: EHCI Host Controller
Mar 11 21:40:00 mat-desktop kernel: [17179578.364000] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 5
Mar 11 21:40:00 mat-desktop kernel: [17179578.364000] ehci_hcd 0000:00:10.4: irq 185, io mem 0xeb003000
Mar 11 21:40:00 mat-desktop kernel: [17179578.364000] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Mar 11 21:40:00 mat-desktop kernel: [17179578.364000] usb usb5: configuration #1 chosen from 1 choice
Mar 11 21:40:00 mat-desktop kernel: [17179578.364000] hub 5-0:1.0: USB hub found
Mar 11 21:40:00 mat-desktop kernel: [17179578.364000] hub 5-0:1.0: 8 ports detected
Mar 11 21:40:00 mat-desktop kernel: [17179578.512000] Attempting manual resume
Mar 11 21:40:00 mat-desktop kernel: [17179578.548000] kjournald starting.  Commit interval 5 seconds
Mar 11 21:40:00 mat-desktop kernel: [17179578.548000] EXT3-fs: mounted filesystem with ordered data mode.
Mar 11 21:40:00 mat-desktop kernel: [17179578.808000] usb 1-1: device not accepting address 2, error -71
Mar 11 21:40:00 mat-desktop kernel: [17179579.200000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00e018000083a786]
Mar 11 21:40:00 mat-desktop kernel: [17179579.844000] ACPI: Unable to turn cooling device [dffeddec] 'on'
Mar 11 21:40:00 mat-desktop kernel: [17179580.292000] usb 1-1: new full speed USB device using uhci_hcd and address 4
Mar 11 21:40:00 mat-desktop kernel: [17179580.488000] usb 1-1: configuration #1 chosen from 1 choice
Mar 11 21:40:00 mat-desktop kernel: [17179585.844000] ACPI: Unable to turn cooling device [dffeddec] 'on'
Mar 11 21:40:00 mat-desktop kernel: [17179590.188000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Mar 11 21:40:00 mat-desktop kernel: [17179590.192000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Mar 11 21:40:00 mat-desktop kernel: [17179590.636000] Linux agpgart interface v0.101 (c) Dave Jones
Mar 11 21:40:00 mat-desktop kernel: [17179590.772000] agpgart: Detected VIA KM400/KM400A chipset
Mar 11 21:40:00 mat-desktop kernel: [17179590.780000] agpgart: AGP aperture is 64M @ 0xe0000000
Mar 11 21:40:00 mat-desktop kernel: [17179590.868000] via-rhine.c:v1.10-LK1.2.0-2.6 June-10-2004 Written by Donald Becker
Mar 11 21:40:00 mat-desktop kernel: [17179590.868000] ACPI: PCI Interrupt Link [ALKD] BIOS reported IRQ 0, using IRQ 23
Mar 11 21:40:00 mat-desktop kernel: [17179590.868000] ACPI: PCI Interrupt Link [ALKD] enabled at IRQ 23
Mar 11 21:40:00 mat-desktop kernel: [17179590.868000] ACPI: PCI Interrupt 0000:00:12.0[A] -> Link [ALKD] -> GSI 23 (level, low) -> IRQ 193
Mar 11 21:40:00 mat-desktop kernel: [17179590.868000] PCI: Via IRQ fixup for 0000:00:12.0, from 10 to 1
Mar 11 21:40:00 mat-desktop kernel: [17179590.868000] eth0: VIA Rhine II at 0x1e400, 00:11:2f:2c:2d:51, IRQ 193.
Mar 11 21:40:00 mat-desktop kernel: [17179590.868000] eth0: MII PHY found at address 1, status 0x7849 advertising 05e1 Link 0000.
Mar 11 21:40:00 mat-desktop kernel: [17179591.056000] Linux Tulip driver version 1.1.14 (May 6, 2006)
Mar 11 21:40:00 mat-desktop kernel: [17179591.056000] ACPI: PCI Interrupt 0000:00:08.0[A] -> GSI 16 (level, low) -> IRQ 201
Mar 11 21:40:00 mat-desktop kernel: [17179591.056000] tulip0:  MII transceiver #1 config 3100 status 7869 advertising 05e1.
Mar 11 21:40:00 mat-desktop kernel: [17179591.056000] tulip0:  MII transceiver #2 config 1000 status 7849 advertising 05e1.
Mar 11 21:40:00 mat-desktop kernel: [17179591.056000] tulip0:  MII transceiver #3 config 1000 status 7849 advertising 05e1.
Mar 11 21:40:00 mat-desktop kernel: [17179591.056000] tulip0:  MII transceiver #4 config 1000 status 7849 advertising 05e1.
Mar 11 21:40:00 mat-desktop kernel: [17179591.060000] eth1: ADMtek Comet rev 17 at Port 0xa000, 00:A1:B0:00:48:28, IRQ 201.
Mar 11 21:40:00 mat-desktop kernel: [17179591.432000] parport: PnPBIOS parport detected.
Mar 11 21:40:00 mat-desktop kernel: [17179591.432000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
Mar 11 21:40:00 mat-desktop kernel: [17179591.644000] ACPI: PCI Interrupt Link [ALKC] BIOS reported IRQ 0, using IRQ 22
Mar 11 21:40:00 mat-desktop kernel: [17179591.644000] ACPI: PCI Interrupt Link [ALKC] enabled at IRQ 22
Mar 11 21:40:00 mat-desktop kernel: [17179591.644000] ACPI: PCI Interrupt 0000:00:11.5[C] -> Link [ALKC] -> GSI 22 (level, low) -> IRQ 209
Mar 11 21:40:00 mat-desktop kernel: [17179591.644000] PCI: Via IRQ fixup for 0000:00:11.5, from 5 to 1
Mar 11 21:40:00 mat-desktop kernel: [17179591.644000] PCI: Setting latency timer of device 0000:00:11.5 to 64
Mar 11 21:40:00 mat-desktop kernel: [17179591.688000] input: PC Speaker as /class/input/input1
Mar 11 21:40:00 mat-desktop kernel: [17179591.844000] ACPI: Unable to turn cooling device [dffeddec] 'on'
Mar 11 21:40:00 mat-desktop kernel: [17179591.972000] logips2pp: Detected unknown logitech mouse model 0
Mar 11 21:40:00 mat-desktop kernel: [17179592.008000] Floppy drive(s): fd0 is 1.44M
Mar 11 21:40:00 mat-desktop kernel: [17179592.036000] FDC 0 is a post-1991 82077
Mar 11 21:40:00 mat-desktop kernel: [17179592.036000] Linux video capture interface: v1.00
Mar 11 21:40:00 mat-desktop kernel: [17179592.044000] zc0301: V4L2 driver for ZC0301 Image Processor and Control Chip v1:1.03
Mar 11 21:40:00 mat-desktop kernel: [17179592.044000] usb 1-1: ZC0301 Image Processor and Control Chip detected (vid/pid 0x041E/0x4034)
Mar 11 21:40:00 mat-desktop kernel: [17179592.092000] usb 1-1: No supported image sensor detected
Mar 11 21:40:00 mat-desktop kernel: [17179592.092000] usbcore: registered new driver zc0301
Mar 11 21:40:00 mat-desktop kernel: [17179592.128000] drivers/media/video/spca5xx/spca5xx-main.c: USB SPCA5XX camera found. Type Creative Instant P0620
Mar 11 21:40:00 mat-desktop kernel: [17179592.164000] PCI: Enabling device 0000:00:11.6 (0000 -> 0001)
Mar 11 21:40:00 mat-desktop kernel: [17179592.164000] ACPI: PCI Interrupt 0000:00:11.6[C] -> Link [ALKC] -> GSI 22 (level, low) -> IRQ 209
Mar 11 21:40:00 mat-desktop kernel: [17179592.164000] PCI: Via IRQ fixup for 0000:00:11.6, from 0 to 1
Mar 11 21:40:00 mat-desktop kernel: [17179592.188000] usbcore: registered new driver spca5xx
Mar 11 21:40:00 mat-desktop kernel: [17179592.188000] drivers/media/video/spca5xx/spca5xx-main.c: spca5xx driver 00.57.08 registered
Mar 11 21:40:00 mat-desktop kernel: [17179592.392000] input: ImPS/2 Logitech Wheel Mouse as /class/input/input2
Mar 11 21:40:00 mat-desktop kernel: [17179592.420000] ts: Compaq touchscreen protocol output
Mar 11 21:40:00 mat-desktop kernel: [17179592.916000] PCI: Setting latency timer of device 0000:00:11.6 to 64
Mar 11 21:40:00 mat-desktop kernel: [17179592.956000] NET: Registered protocol family 17
Mar 11 21:40:00 mat-desktop kernel: [17179593.420000] ACPI: PCI interrupt for device 0000:00:11.6 disabled
Mar 11 21:40:00 mat-desktop kernel: [17179593.420000] VIA 82xx Modem: probe of 0000:00:11.6 failed with error -13
Mar 11 21:40:00 mat-desktop kernel: [17179593.656000] lp0: using parport0 (interrupt-driven).
Mar 11 21:40:00 mat-desktop kernel: [17179593.680000] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)
Mar 11 21:40:00 mat-desktop kernel: [17179593.680000] ieee1394: sbp2: Try serialize_io=0 for better performance
Mar 11 21:40:00 mat-desktop kernel: [17179593.716000] Adding 1244996k swap on /dev/disk/by-uuid/fde96a03-6fcd-4e7c-afb7-952e9cabbee4.  Priority:-1 extents:1 across:1244996k
Mar 11 21:40:00 mat-desktop kernel: [17179593.800000] EXT3 FS on hda2, internal journal
Mar 11 21:40:00 mat-desktop kernel: [17179594.900000] 0000:00:08.0: tulip_stop_rxtx() failed (CSR5 0xfc664010 CSR6 0xff972113)
Mar 11 21:40:00 mat-desktop kernel: [17179594.900000] eth0: Setting full-duplex based on MII#1 link partner capability of 45e1.
Mar 11 21:40:00 mat-desktop kernel: [17179597.844000] ACPI: Unable to turn cooling device [dffeddec] 'on'
Mar 11 21:40:00 mat-desktop kernel: [17179598.528000] ACPI: Power Button (FF) [PWRF]
Mar 11 21:40:00 mat-desktop kernel: [17179598.528000] ACPI: Power Button (CM) [PWRB]
Mar 11 21:40:00 mat-desktop kernel: [17179598.644000] ibm_acpi: ec object not found
Mar 11 21:40:00 mat-desktop kernel: [17179598.680000] pcc_acpi: loading...
Mar 11 21:40:02 mat-desktop kernel: [17179601.660000] [drm] Initialized drm 1.0.1 20051102
Mar 11 21:40:02 mat-desktop kernel: [17179601.668000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 201
Mar 11 21:40:02 mat-desktop kernel: [17179601.668000] PCI: Via IRQ fixup for 0000:01:00.0, from 10 to 9
Mar 11 21:40:02 mat-desktop kernel: [17179601.672000] [drm] Initialized via 2.7.4 20051116 on minor 0
Mar 11 21:40:02 mat-desktop kernel: [17179601.716000] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
Mar 11 21:40:02 mat-desktop kernel: [17179601.716000] agpgart: Device is in legacy mode, falling back to 2.x
Mar 11 21:40:02 mat-desktop kernel: [17179601.716000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
Mar 11 21:40:02 mat-desktop kernel: [17179601.716000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
Mar 11 21:40:03 mat-desktop hpiod: 1.6.9 accepting connections at 2208... 
Mar 11 21:40:03 mat-desktop kernel: [17179602.604000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
Mar 11 21:40:03 mat-desktop kernel: [17179602.604000] apm: overridden by ACPI.
Mar 11 21:40:05 mat-desktop kernel: [17179603.844000] ACPI: Unable to turn cooling device [dffeddec] 'on'
Mar 11 21:40:07 mat-desktop gconfd (mat-4265): starting (version 2.16.0), pid 4265 user 'mat'
Mar 11 21:40:07 mat-desktop gconfd (mat-4265): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Mar 11 21:40:07 mat-desktop gconfd (mat-4265): Resolved address "xml:readwrite:/home/mat/.gconf" to a writable configuration source at position 1
Mar 11 21:40:07 mat-desktop gconfd (mat-4265): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Mar 11 21:40:07 mat-desktop gconfd (mat-4265): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Mar 11 21:40:07 mat-desktop gconfd (mat-4265): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Mar 11 21:40:08 mat-desktop hcid[4338]: Bluetooth HCI daemon
Mar 11 21:40:08 mat-desktop kernel: [17179607.604000] Bluetooth: Core ver 2.8
Mar 11 21:40:08 mat-desktop kernel: [17179607.604000] NET: Registered protocol family 31
Mar 11 21:40:08 mat-desktop kernel: [17179607.604000] Bluetooth: HCI device and connection manager initialized
Mar 11 21:40:08 mat-desktop kernel: [17179607.604000] Bluetooth: HCI socket layer initialized
Mar 11 21:40:08 mat-desktop hcid[4338]: Register path:/org/bluez fallback:1
Mar 11 21:40:08 mat-desktop kernel: [17179607.792000] Bluetooth: L2CAP ver 2.8
Mar 11 21:40:08 mat-desktop kernel: [17179607.792000] Bluetooth: L2CAP socket layer initialized
Mar 11 21:40:08 mat-desktop sdpd[4345]: Bluetooth SDP daemon 
Mar 11 21:40:09 mat-desktop kernel: [17179607.904000] Bluetooth: RFCOMM socket layer initialized
Mar 11 21:40:09 mat-desktop kernel: [17179607.904000] Bluetooth: RFCOMM TTY layer initialized
Mar 11 21:40:09 mat-desktop kernel: [17179607.904000] Bluetooth: RFCOMM ver 1.7
Mar 11 21:40:09 mat-desktop anacron[4374]: Anacron 2.3 started on 2007-03-11
Mar 11 21:40:09 mat-desktop anacron[4374]: Normal exit (0 jobs run)
Mar 11 21:40:09 mat-desktop /usr/sbin/cron[4400]: (CRON) INFO (pidfile fd = 3)
Mar 11 21:40:09 mat-desktop /usr/sbin/cron[4401]: (CRON) STARTUP (fork ok)
Mar 11 21:40:09 mat-desktop /usr/sbin/cron[4401]: (CRON) INFO (Running @reboot jobs)
Mar 11 21:40:11 mat-desktop kernel: [17179609.844000] ACPI: Unable to turn cooling device [dffeddec] 'on'
Mar 11 21:40:11 mat-desktop kernel: [17179610.044000] NET: Registered protocol family 10
Mar 11 21:40:11 mat-desktop kernel: [17179610.044000] lo: Disabled Privacy Extensions
Mar 11 21:40:11 mat-desktop kernel: [17179610.044000] IPv6 over IPv4 tunneling driver
Mar 11 21:40:17 mat-desktop kernel: [17179615.844000] ACPI: Unable to turn cooling device [dffeddec] 'on'
Mar 11 21:40:17 mat-desktop gconfd (mat-4265): Resolved address "xml:readwrite:/home/mat/.gconf" to a writable configuration source at position 0
Mar 11 21:40:22 mat-desktop kernel: [17179620.964000] eth0: no IPv6 routers present
Mar 11 21:40:23 mat-desktop kernel: [17179621.844000] ACPI: Unable to turn cooling device [dffeddec] 'on'
Mar 11 21:40:29 mat-desktop kernel: [17179627.844000] ACPI: Unable to turn cooling device [dffeddec] 'on'
Mar 11 21:40:35 mat-desktop kernel: [17179633.844000] ACPI: Unable to turn cooling device [dffeddec] 'on'
Mar 11 21:40:41 mat-desktop kernel: [17179639.848000] ACPI: Unable to turn cooling device [dffeddec] 'on'
Mar 11 21:40:47 mat-desktop kernel: [17179645.852000] ACPI: Unable to turn cooling device [dffeddec] 'on'
Mar 11 21:40:53 mat-desktop kernel: [17179651.852000] ACPI: Unable to turn cooling device [dffeddec] 'on'
Mar 11 21:40:59 mat-desktop kernel: [17179657.852000] ACPI: Unable to turn cooling device [dffeddec] 'on'
Mar 11 21:41:05 mat-desktop kernel: [17179663.852000] ACPI: Unable to turn cooling device [dffeddec] 'on'
Mar 11 21:41:11 mat-desktop kernel: [17179669.852000] ACPI: Unable to turn cooling device [dffeddec] 'on'
Mar 11 21:41:13 mat-desktop gconfd (root-4704): starting (version 2.16.0), pid 4704 user 'root'
Mar 11 21:41:13 mat-desktop gconfd (root-4704): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Mar 11 21:41:13 mat-desktop gconfd (root-4704): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 1
Mar 11 21:41:13 mat-desktop gconfd (root-4704): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Mar 11 21:41:13 mat-desktop gconfd (root-4704): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Mar 11 21:41:13 mat-desktop gconfd (root-4704): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Mar 11 21:41:15 mat-desktop dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 3420
Mar 11 21:41:15 mat-desktop dhclient: killed old client process, removed PID file
Mar 11 21:41:15 mat-desktop dhclient: Internet Systems Consortium DHCP Client V3.0.4
Mar 11 21:41:15 mat-desktop dhclient: Copyright 2004-2006 Internet Systems Consortium.
Mar 11 21:41:15 mat-desktop dhclient: All rights reserved.
Mar 11 21:41:15 mat-desktop dhclient: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Mar 11 21:41:15 mat-desktop dhclient: 
Mar 11 21:41:15 mat-desktop dhclient: Listening on LPF/eth0/00:a1:b0:00:48:28
Mar 11 21:41:15 mat-desktop dhclient: Sending on   LPF/eth0/00:a1:b0:00:48:28
Mar 11 21:41:15 mat-desktop dhclient: Sending on   Socket/fallback
Mar 11 21:41:15 mat-desktop dhclient: DHCPRELEASE on eth0 to 192.168.1.1 port 67
Mar 11 21:41:16 mat-desktop kernel: [17179674.824000] 0000:00:08.0: tulip_stop_rxtx() failed (CSR5 0xfc06c012 CSR6 0xff970111)
Mar 11 21:41:16 mat-desktop dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416
Mar 11 21:41:16 mat-desktop dhclient: Internet Systems Consortium DHCP Client V3.0.4
Mar 11 21:41:16 mat-desktop dhclient: Copyright 2004-2006 Internet Systems Consortium.
Mar 11 21:41:16 mat-desktop dhclient: All rights reserved.
Mar 11 21:41:16 mat-desktop dhclient: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Mar 11 21:41:16 mat-desktop dhclient: 
Mar 11 21:41:17 mat-desktop kernel: [17179675.852000] ACPI: Unable to turn cooling device [dffeddec] 'on'
Mar 11 21:41:17 mat-desktop dhclient: Listening on LPF/eth0/00:a1:b0:00:48:28
Mar 11 21:41:17 mat-desktop dhclient: Sending on   LPF/eth0/00:a1:b0:00:48:28
Mar 11 21:41:17 mat-desktop dhclient: Sending on   Socket/fallback
Mar 11 21:41:18 mat-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Mar 11 21:41:18 mat-desktop dhclient: DHCPOFFER from 192.168.1.254
Mar 11 21:41:18 mat-desktop dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Mar 11 21:41:18 mat-desktop dhclient: DHCPACK from 192.168.1.254
Mar 11 21:41:18 mat-desktop dhclient: bound to 192.168.1.100 -- renewal in 36763 seconds.
Mar 11 21:41:18 mat-desktop ntpdate[4828]: step time server 82.211.81.145 offset -0.479317 sec
Mar 11 21:41:19 mat-desktop kernel: [17179678.292000] 0000:00:08.0: tulip_stop_rxtx() failed (CSR5 0xfc664010 CSR6 0xff972113)
Mar 11 21:41:19 mat-desktop kernel: [17179678.292000] eth0: Setting full-duplex based on MII#1 link partner capability of 45e1.
Mar 11 21:41:22 mat-desktop kernel: [17179681.852000] ACPI: Unable to turn cooling device [dffeddec] 'on'
Mar 11 21:41:26 mat-desktop kernel: [17179685.908000] eth0: no IPv6 routers present
Mar 11 21:41:28 mat-desktop kernel: [17179687.856000] ACPI: Unable to turn cooling device [dffeddec] 'on'
Mar 11 21:41:34 mat-desktop kernel: [17179693.856000] ACPI: Unable to turn cooling device [dffeddec] 'on'
Mar 11 21:41:40 mat-desktop kernel: [17179699.856000] ACPI: Unable to turn cooling device [dffeddec] 'on'
Mar 11 21:41:43 mat-desktop gconfd (root-4704): GConf server is not in use, shutting down.
Mar 11 21:41:43 mat-desktop gconfd (root-4704): Exiting
Mar 11 21:41:46 mat-desktop kernel: [17179705.856000] ACPI: Unable to turn cooling device [dffeddec] 'on'
Mar 11 21:41:52 mat-desktop kernel: [17179711.856000] ACPI: Unable to turn cooling device [dffeddec] 'on'
Mar 11 21:41:58 mat-desktop kernel: [17179717.856000] ACPI: Unable to turn cooling device [dffeddec] 'on'
Mar 11 21:42:04 mat-desktop kernel: [17179723.860000] ACPI: Unable to turn cooling device [dffeddec] 'on'
Mar 11 21:42:10 mat-desktop kernel: [17179729.864000] ACPI: Unable to turn cooling device [dffeddec] 'on'
Mar 11 21:42:16 mat-desktop kernel: [17179735.864000] ACPI: Unable to turn cooling device [dffeddec] 'on'
Mar 11 21:42:22 mat-desktop kernel: [17179741.864000] ACPI: Unable to turn cooling device [dffeddec] 'on'
Mar 11 21:42:28 mat-desktop kernel: [17179747.864000] ACPI: Unable to turn cooling device [dffeddec] 'on'
Mar 11 21:42:34 mat-desktop kernel: [17179753.864000] ACPI: Unable to turn cooling device [dffeddec] 'on'
Mar 11 21:42:40 mat-desktop kernel: [17179759.864000] ACPI: Unable to turn cooling device [dffeddec] 'on'
Mar 11 21:42:46 mat-desktop kernel: [17179765.864000] ACPI: Unable to turn cooling device [dffeddec] 'on'
Mar 11 21:42:52 mat-desktop kernel: [17179771.872000] ACPI: Unable to turn cooling device [dffeddec] 'on'
Mar 11 21:42:58 mat-desktop kernel: [17179777.872000] ACPI: Unable to turn cooling device [dffeddec] 'on'
Mar 11 21:43:04 mat-desktop kernel: [17179783.872000] ACPI: Unable to turn cooling device [dffeddec] 'on'
Mar 11 21:43:10 mat-desktop kernel: [17179789.872000] ACPI: Unable to turn cooling device [dffeddec] 'on'
Mar 11 21:43:16 mat-desktop kernel: [17179795.872000] ACPI: Unable to turn cooling device [dffeddec] 'on'
Mar 11 21:43:22 mat-desktop kernel: [17179801.872000] ACPI: Unable to turn cooling device [dffeddec] 'on'
Mar 11 21:43:28 mat-desktop kernel: [17179807.876000] ACPI: Unable to turn cooling device [dffeddec] 'on'
Mar 11 21:43:34 mat-desktop kernel: [17179813.880000] ACPI: Unable to turn cooling device [dffeddec] 'on'
Mar 11 21:43:40 mat-desktop kernel: [17179819.880000] ACPI: Unable to turn cooling device [dffeddec] 'on'
Mar 11 21:43:46 mat-desktop kernel: [17179825.880000] ACPI: Unable to turn cooling device [dffeddec] 'on'
Mar 11 21:43:52 mat-desktop kernel: [17179831.880000] ACPI: Unable to turn cooling device [dffeddec] 'on'
Mar 11 21:43:58 mat-desktop kernel: [17179837.880000] ACPI: Unable to turn cooling device [dffeddec] 'on'
Mar 11 21:44:04 mat-desktop kernel: [17179843.880000] ACPI: Unable to turn cooling device [dffeddec] 'on'
Mar 11 21:44:10 mat-desktop kernel: [17179849.884000] ACPI: Unable to turn cooling device [dffeddec] 'on'
Mar 11 21:44:16 mat-desktop kernel: [17179855.884000] ACPI: Unable to turn cooling device [dffeddec] 'on'
Mar 11 21:44:22 mat-desktop kernel: [17179861.884000] ACPI: Unable to turn cooling device [dffeddec] 'on'
Mar 11 21:44:23 mat-desktop gconfd (root-4923): starting (version 2.16.0), pid 4923 user 'root'
Mar 11 21:44:23 mat-desktop gconfd (root-4923): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Mar 11 21:44:23 mat-desktop gconfd (root-4923): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 1
Mar 11 21:44:23 mat-desktop gconfd (root-4923): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Mar 11 21:44:23 mat-desktop gconfd (root-4923): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Mar 11 21:44:23 mat-desktop gconfd (root-4923): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Mar 11 21:44:28 mat-desktop kernel: [17179867.884000] ACPI: Unable to turn cooling device [dffeddec] 'on'
Mar 11 21:44:34 mat-desktop kernel: [17179873.884000] ACPI: Unable to turn cooling device [dffeddec] 'on'
Mar 11 21:44:40 mat-desktop kernel: [17179879.888000] ACPI: Unable to turn cooling device [dffeddec] 'on'
Mar 11 21:44:46 mat-desktop kernel: [17179885.892000] ACPI: Unable to turn cooling device [dffeddec] 'on'
Mar 11 21:44:52 mat-desktop kernel: [17179891.892000] ACPI: Unable to turn cooling device [dffeddec] 'on'
Mar 11 21:44:58 mat-desktop kernel: [17179897.892000] ACPI: Unable to turn cooling device [dffeddec] 'on'
Mar 11 21:45:04 mat-desktop kernel: [17179903.892000] ACPI: Unable to turn cooling device [dffeddec] 'on'
Mar 11 21:45:10 mat-desktop kernel: [17179909.892000] ACPI: Unable to turn cooling device [dffeddec] 'on'
Mar 11 21:45:16 mat-desktop kernel: [17179915.896000] ACPI: Unable to turn cooling device [dffeddec] 'on'
Mar 11 21:45:22 mat-desktop kernel: [17179921.900000] ACPI: Unable to turn cooling device [dffeddec] 'on'
Mar 11 21:45:28 mat-desktop kernel: [17179927.900000] ACPI: Unable to turn cooling device [dffeddec] 'on'
Mar 11 21:45:34 mat-desktop kernel: [17179933.900000] ACPI: Unable to turn cooling device [dffeddec] 'on'
Mar 11 21:45:40 mat-desktop kernel: [17179939.900000] ACPI: Unable to turn cooling device [dffeddec] 'on'
Mar 11 21:45:46 mat-desktop kernel: [17179945.900000] ACPI: Unable to turn cooling device [dffeddec] 'on'
Mar 11 21:45:52 mat-desktop kernel: [17179951.904000] ACPI: Unable to turn cooling device [dffeddec] 'on'
Mar 11 21:45:53 mat-desktop gconfd (root-4923): GConf server is not in use, shutting down.
Mar 11 21:45:53 mat-desktop gconfd (root-4923): Exiting
Mar 11 21:45:58 mat-desktop kernel: [17179957.908000] ACPI: Unable to turn cooling device [dffeddec] 'on'
Mar 11 21:46:04 mat-desktop kernel: [17179963.908000] ACPI: Unable to turn cooling device [dffeddec] 'on'
Mar 11 21:46:10 mat-desktop kernel: [17179969.908000] ACPI: Unable to turn cooling device [dffeddec] 'on'
Mar 11 21:46:16 mat-desktop kernel: [17179975.908000] ACPI: Unable to turn cooling device [dffeddec] 'on'
Mar 11 21:46:22 mat-desktop kernel: [17179981.908000] ACPI: Unable to turn cooling device [dffeddec] 'on'
Mar 11 21:46:28 mat-desktop kernel: [17179987.908000] ACPI: Unable to turn cooling device [dffeddec] 'on'
Mar 11 21:46:34 mat-desktop kernel: [17179993.912000] ACPI: Unable to turn cooling device [dffeddec] 'on'
Mar 11 21:46:40 mat-desktop kernel: [17179999.916000] ACPI: Unable to turn cooling device [dffeddec] 'on'
Mar 11 21:46:46 mat-desktop kernel: [17180005.916000] ACPI: Unable to turn cooling device [dffeddec] 'on'
Mar 11 21:46:52 mat-desktop kernel: [17180011.916000] ACPI: Unable to turn cooling device [dffeddec] 'on'
Mar 11 21:46:58 mat-desktop kernel: [17180017.916000] ACPI: Unable to turn cooling device [dffeddec] 'on'
Mar 11 21:47:04 mat-desktop kernel: [17180023.916000] ACPI: Unable to turn cooling device [dffeddec] 'on'
Mar 11 21:47:10 mat-desktop kernel: [17180029.920000] ACPI: Unable to turn cooling device [dffeddec] 'on'
Mar 11 21:47:16 mat-desktop kernel: [17180035.924000] ACPI: Unable to turn cooling device [dffeddec] 'on'
Mar 11 21:47:22 mat-desktop kernel: [17180041.924000] ACPI: Unable to turn cooling device [dffeddec] 'on'
Mar 11 21:47:28 mat-desktop kernel: [17180047.924000] ACPI: Unable to turn cooling device [dffeddec] 'on'
Mar 11 21:47:34 mat-desktop kernel: [17180053.924000] ACPI: Unable to turn cooling device [dffeddec] 'on'
Mar 11 21:47:40 mat-desktop kernel: [17180059.924000] ACPI: Unable to turn cooling device [dffeddec] 'on'
Mar 11 21:47:46 mat-desktop kernel: [17180065.928000] ACPI: Unable to turn cooling device [dffeddec] 'on'
Mar 11 21:47:48 mat-desktop gconfd (root-5020): starting (version 2.16.0), pid 5020 user 'root'
Mar 11 21:47:48 mat-desktop gconfd (root-5020): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Mar 11 21:47:48 mat-desktop gconfd (root-5020): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 1
Mar 11 21:47:48 mat-desktop gconfd (root-5020): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Mar 11 21:47:48 mat-desktop gconfd (root-5020): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Mar 11 21:47:48 mat-desktop gconfd (root-5020): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Mar 11 21:47:52 mat-desktop kernel: [17180071.932000] ACPI: Unable to turn cooling device [dffeddec] 'on'
Mar 11 21:47:58 mat-desktop kernel: [17180077.932000] ACPI: Unable to turn cooling device [dffeddec] 'on'
Mar 11 21:48:04 mat-desktop kernel: [17180083.932000] ACPI: Unable to turn cooling device [dffeddec] 'on'
Mar 11 21:48:10 mat-desktop kernel: [17180089.932000] ACPI: Unable to turn cooling device [dffeddec] 'on'
Mar 11 21:48:16 mat-desktop kernel: [17180095.932000] ACPI: Unable to turn cooling device [dffeddec] 'on'
Mar 11 21:48:18 mat-desktop gconfd (root-5020): GConf server is not in use, shutting down.
Mar 11 21:48:18 mat-desktop gconfd (root-5020): Exiting
Mar 11 21:48:22 mat-desktop kernel: [17180101.932000] ACPI: Unable to turn cooling device [dffeddec] 'on'
Mar 11 21:48:28 mat-desktop kernel: [17180107.936000] ACPI: Unable to turn cooling device [dffeddec] 'on'
Mar 11 21:48:34 mat-desktop kernel: [17180113.936000] ACPI: Unable to turn cooling device [dffeddec] 'on'
Mar 11 21:48:40 mat-desktop kernel: [17180119.936000] ACPI: Unable to turn cooling device [dffeddec] 'on'
Mar 11 21:48:46 mat-desktop kernel: [17180125.936000] ACPI: Unable to turn cooling device [dffeddec] 'on'
Mar 11 21:48:52 mat-desktop kernel: [17180131.936000] ACPI: Unable to turn cooling device [dffeddec] 'on'
Mar 11 21:48:58 mat-desktop kernel: [17180137.936000] ACPI: Unable to turn cooling device [dffeddec] 'on'
Mar 11 21:49:04 mat-desktop kernel: [17180143.940000] ACPI: Unable to turn cooling device [dffeddec] 'on'
Mar 11 21:49:07 mat-desktop gconfd (root-5085): starting (version 2.16.0), pid 5085 user 'root'
Mar 11 21:49:07 mat-desktop gconfd (root-5085): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Mar 11 21:49:07 mat-desktop gconfd (root-5085): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 1
Mar 11 21:49:07 mat-desktop gconfd (root-5085): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Mar 11 21:49:07 mat-desktop gconfd (root-5085): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Mar 11 21:49:07 mat-desktop gconfd (root-5085): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Mar 11 21:49:10 mat-desktop kernel: [17180149.944000] ACPI: Unable to turn cooling device [dffeddec] 'on'
Mar 11 21:49:16 mat-desktop kernel: [17180155.944000] ACPI: Unable to turn cooling device [dffeddec] 'on'
Mar 11 21:49:22 mat-desktop kernel: [17180161.944000] ACPI: Unable to turn cooling device [dffeddec] 'on'
Mar 11 21:49:28 mat-desktop kernel: [17180167.944000] ACPI: Unable to turn cooling device [dffeddec] 'on'
Mar 11 21:49:34 mat-desktop kernel: [17180173.944000] ACPI: Unable to turn cooling device [dffeddec] 'on'
 and so on

---

### Post by hatstand on 2007-03-12
Whoops.

Sorry: didn't know it'd be so BIG!

---

### Post by Mr. C. on 2007-03-12
It appears that the Ethernet driver is having trouble disabling transmission and receive for some reason.  It receives its IP address 192.168.1.100 from your DHCP server, but then has this failure.
```

dhclient: bound to 192.168.1.100 -- renewal in 36763 seconds.
...
tulip_stop_rxtx() failed (CSR5 0xfc664010 CSR6 0xff972113)
```

Problems with the card ?  This driver is present in the 2.6.20 kernel.  You must have updated kernels ?

I'm also concerned about these:

```
ACPI: Unable to turn cooling device [dffeddec] 'on'
```

These may be erroneous, or they may be an indication that one or more of your fans are not being enabled.

MrC

---

### Post by hatstand on 2007-03-12
as I say, all was hunky dory until I changed ISP.

I will check the fan in the morning. Maybe it's a DCHP/DNS thing?

Thanks for the help. Bedtime now. Will check for replies mañana.

Gracias.

---

### Post by Mr. C. on 2007-03-12
That's funny.  Sorry, nope.  DHCP and DNS don't yet know how to control fans! :-)

Its often easy to link to unrelated events like this.   Changing and ISP wouldn't cause any of these problems.  Perhaps different hardware on the other end of the NIC might have something to do with it.

MrC

---

### Post by hatstand on 2007-03-12
Obviously the fan is not controlled by network configuration, but maybe the network problem is a result of the DHCP or DNS settings. It was late and the two unrelated sentences were put in a single paragraph. Sorry about that. Es más facil en Español. 

I have seen other threads on losing DNSs on boot: how do I check if that is the problem?

Thanks again.

---

### Post by Mr. C. on 2007-03-12
I understand.  Me rio a carcajadas.

DNS servers are provided by either you via manual configuration (Networking, or /etc/resolv.conf) or offered by a DHCP server.  If the latter, configure your DHCP server to offer the proper DNS servers.  The system will not just lose or de-configure them.

As to the NIC issue, this would require some diagnosis at the driver level.  That's a pretty old NIC, correct ?  And the system ?

MrC

---

### Post by wasteoftime on 2007-03-18
I think im having the same problem as i have to "ifdown" and the "ifup" in the terminal everytime as when i plug in my modem it just sends and doesnt recieve until i do, very annoying!

My isp uses DHCP. Can anyone help:confused:

---

### Post by Mr. C. on 2007-03-18
> **wasteoftime said:**
> I think im having the same problem as i have to "ifdown" and the "ifup" in the terminal everytime as when i plug in my modem it just sends and doesnt recieve until i do...

Are you saying you power down your modem, and then power it up; and after that, you need to  ifup/ifdown to get connected?

Or do you mean move the Ethernet cable from one machine to another ?

That the modem "just sends and doesnt recieve [sic]" is not likely.  I think you misunderstand the matter at hand.

MrC

---

### Post by wasteoftime on 2007-03-19
Sorry my bad:) , it recieves lots and countinues to do so but sends hardly anything, so when i open firefox it does connect. It happens when i first turn on the comp if i take the cable out, after configuring it, and put it back in its ok. Its not a major thing but slightly annoying.

---

### Post by Mr. C. on 2007-03-19
Try: [https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4)

If that doesn't help, you're going to have to show the same diags requested earlier in this post.

MrC

---

