---
title: "Problems with DWA-171 WiFi-adapter"
date: 2015-10-09
forum: Networking &amp; Wireless
---

### Post by paul-summermatter on 2015-10-09
Hi

My USBs don't work anymore. Specially the DWA-171 WiFi-adapter, which used to work perfectly, dos not work anymore.

I'm a total newbie in Ubuntu and it would be great to get this work again....cause I don't wan't to go back to Windows.

Txs, for your help.

Paesu


```
[    0.481741] HugeTLB registered 2 MB page size, pre-allocated 0 pages[    0.482498] zbud: loaded
[    0.482549] VFS: Disk quotas dquot_6.5.2
[    0.482577] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.482834] fuse init (API version 7.22)
[    0.482885] msgmni has been set to 1664
[    0.482919] Key type big_key registered
[    0.483217] Key type asymmetric registered
[    0.483219] Asymmetric key parser 'x509' registered
[    0.483238] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    0.483265] io scheduler noop registered
[    0.483267] io scheduler deadline registered (default)
[    0.483281] io scheduler cfq registered
[    0.483332] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.483341] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.483365] vesafb: mode is 1920x1080x32, linelength=7680, pages=0
[    0.483366] vesafb: scrolling: redraw
[    0.483367] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    0.485271] vesafb: framebuffer at 0xe0000000, mapped to 0xf8480000, using 8128k, total 8128k
[    0.489796] Console: switching to colour frame buffer device 240x67
[    0.494212] fb0: VESA VGA frame buffer device
[    0.494227] intel_idle: MWAIT substates: 0x1120
[    0.494228] intel_idle: v0.4 model 0x3A
[    0.494229] intel_idle: lapic_timer_reliable_states 0xffffffff
[    0.494299] ipmi message handler version 39.2
[    0.494349] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.494353] ACPI: Power Button [PWRB]
[    0.494376] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.494377] ACPI: Power Button [PWRF]
[    0.494429] ACPI: Fan [FAN0] (off)
[    0.494446] ACPI: Fan [FAN1] (off)
[    0.494461] ACPI: Fan [FAN2] (off)
[    0.494475] ACPI: Fan [FAN3] (off)
[    0.494490] ACPI: Fan [FAN4] (off)
[    0.553858] thermal LNXTHERM:00: registered as thermal_zone0
[    0.553860] ACPI: Thermal Zone [TZ00] (28 C)
[    0.553989] thermal LNXTHERM:01: registered as thermal_zone1
[    0.553990] ACPI: Thermal Zone [TZ01] (30 C)
[    0.554007] GHES: HEST is not enabled!
[    0.554074] isapnp: Scanning for PnP cards...
[    0.554076] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.574544] 00:0c: ttyS0 at I/O 0x3f8 (irq = 4, base_baud = 115200) is a 16550A
[    0.595751] 0000:00:16.3: ttyS4 at I/O 0xf0e0 (irq = 19, base_baud = 115200) is a 16550A
[    0.595903] Linux agpgart interface v0.103
[    0.595986] tpm_tis 00:0d: 1.2 TPM (device-id 0xB, rev-id 16)
[    0.845811] tpm_tis 00:0d: TPM is disabled/deactivated (0x7)
[    0.846758] brd: module loaded
[    0.847240] loop: module loaded
[    0.847467] libphy: Fixed MDIO Bus: probed
[    0.847521] tun: Universal TUN/TAP device driver, 1.6
[    0.847522] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.847554] PPP generic driver version 2.4.2
[    0.847587] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.847589] ehci-pci: EHCI PCI platform driver
[    0.847677] ehci-pci 0000:00:1a.0: EHCI Host Controller
[    0.847681] ehci-pci 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    0.847692] ehci-pci 0000:00:1a.0: debug port 2
[    0.851577] ehci-pci 0000:00:1a.0: cache line size of 64 is not supported
[    0.851589] ehci-pci 0000:00:1a.0: irq 16, io mem 0xf7c38000
[    0.861790] ehci-pci 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    0.861822] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    0.861823] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.861824] usb usb1: Product: EHCI Host Controller
[    0.861826] usb usb1: Manufacturer: Linux 3.13.0-63-generic ehci_hcd
[    0.861827] usb usb1: SerialNumber: 0000:00:1a.0
[    0.861902] hub 1-0:1.0: USB hub found
[    0.861906] hub 1-0:1.0: 3 ports detected
[    0.862061] ehci-pci 0000:00:1d.0: EHCI Host Controller
[    0.862065] ehci-pci 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.862077] ehci-pci 0000:00:1d.0: debug port 2
[    0.865988] ehci-pci 0000:00:1d.0: cache line size of 64 is not supported
[    0.865998] ehci-pci 0000:00:1d.0: irq 23, io mem 0xf7c37000
[    0.869362] isapnp: No Plug & Play device found
[    0.877813] ehci-pci 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    0.877867] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    0.877869] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.877870] usb usb2: Product: EHCI Host Controller
[    0.877871] usb usb2: Manufacturer: Linux 3.13.0-63-generic ehci_hcd
[    0.877872] usb usb2: SerialNumber: 0000:00:1d.0
[    0.877996] hub 2-0:1.0: USB hub found
[    0.878002] hub 2-0:1.0: 3 ports detected
[    0.878090] ehci-platform: EHCI generic platform driver
[    0.878096] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.878097] ohci-pci: OHCI PCI platform driver
[    0.878103] ohci-platform: OHCI generic platform driver
[    0.878106] uhci_hcd: USB Universal Host Controller Interface driver
[    0.878194] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    0.878197] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 3
[    0.878285] xhci_hcd 0000:00:14.0: cache line size of 64 is not supported
[    0.878304] xhci_hcd 0000:00:14.0: irq 40 for MSI/MSI-X
[    0.878354] usb usb3: New USB device found, idVendor=1d6b, idProduct=0002
[    0.878355] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.878357] usb usb3: Product: xHCI Host Controller
[    0.878358] usb usb3: Manufacturer: Linux 3.13.0-63-generic xhci_hcd
[    0.878359] usb usb3: SerialNumber: 0000:00:14.0
[    0.878478] hub 3-0:1.0: USB hub found
[    0.878490] hub 3-0:1.0: 4 ports detected
[    0.878729] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    0.878731] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 4
[    0.878759] usb usb4: New USB device found, idVendor=1d6b, idProduct=0003
[    0.878760] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.878761] usb usb4: Product: xHCI Host Controller
[    0.878762] usb usb4: Manufacturer: Linux 3.13.0-63-generic xhci_hcd
[    0.878763] usb usb4: SerialNumber: 0000:00:14.0
[    0.878887] hub 4-0:1.0: USB hub found
[    0.878899] hub 4-0:1.0: 4 ports detected
[    0.937956] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    0.940803] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.940809] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.940987] mousedev: PS/2 mouse device common for all mice
[    0.941277] rtc_cmos 00:05: RTC can wake from S4
[    0.941418] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    0.941444] rtc_cmos 00:05: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    0.941488] device-mapper: uevent: version 1.0.3
[    0.941548] device-mapper: ioctl: 4.27.0-ioctl (2013-10-30) initialised: dm-devel@redhat.com
[    0.941558] platform eisa.0: Probing EISA bus 0
[    0.941559] platform eisa.0: EISA: Cannot allocate resource for mainboard
[    0.941561] platform eisa.0: Cannot allocate resource for EISA slot 1
[    0.941562] platform eisa.0: Cannot allocate resource for EISA slot 2
[    0.941563] platform eisa.0: Cannot allocate resource for EISA slot 3
[    0.941564] platform eisa.0: Cannot allocate resource for EISA slot 4
[    0.941565] platform eisa.0: Cannot allocate resource for EISA slot 5
[    0.941566] platform eisa.0: Cannot allocate resource for EISA slot 6
[    0.941567] platform eisa.0: Cannot allocate resource for EISA slot 7
[    0.941568] platform eisa.0: Cannot allocate resource for EISA slot 8
[    0.941569] platform eisa.0: EISA: Detected 0 cards
[    0.941572] cpufreq-nforce2: No nForce2 chipset.
[    0.941574] ledtrig-cpu: registered to indicate activity on CPUs
[    0.941654] TCP: cubic registered
[    0.941701] NET: Registered protocol family 10
[    0.941823] NET: Registered protocol family 17
[    0.941828] Key type dns_resolver registered
[    0.941975] Using IPI No-Shortcut mode
[    0.942104] Loading compiled-in X.509 certificates
[    0.944291] Loaded X.509 cert 'Magrathea: Glacier signing key: 4c6ca20988788cea7d674a4f55cf4d2766b200d6'
[    0.944299] registered taskstats version 1
[    0.945907] Key type trusted registered
[    0.948456] Key type encrypted registered
[    0.948459] AppArmor: AppArmor sha1 policy hashing enabled
[    0.961460] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
[    0.993905] tpm_tis 00:0d: A TPM error (7) occurred attempting to read a pcr value
[    0.993907] IMA: No TPM chip found, activating TPM-bypass!
[    0.994065] regulator-dummy: disabling
[    0.994215]   Magic number: 3:788:577
[    0.994300] rtc_cmos 00:05: setting system clock to 2015-10-09 10:34:20 UTC (1444386860)
[    0.994746] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.994748] EDD information not available.
[    0.994783] PM: Hibernation image not present or could not be loaded.
[    0.994998] Freeing unused kernel memory: 880K (c19bf000 - c1a9b000)
[    0.995050] Write protecting the kernel text: 6560k
[    0.995113] Write protecting the kernel read-only data: 2776k
[    0.995114] NX-protecting the kernel data: 5728k
[    1.003192] systemd-udevd[107]: starting version 204
[    1.022347] pps_core: LinuxPPS API ver. 1 registered
[    1.022350] pps_core: Software ver. 5.3.6 - Copyright 2005-2007 Rodolfo Giometti <giometti@linux.it>
[    1.024902] PTP clock support registered
[    1.029560] ahci 0000:00:1f.2: version 3.0
[    1.029682] ahci 0000:00:1f.2: irq 41 for MSI/MSI-X
[    1.034817] e1000e: Intel(R) PRO/1000 Network Driver - 2.3.2-k
[    1.034820] e1000e: Copyright(c) 1999 - 2013 Intel Corporation.
[    1.041947] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 6 Gbps 0x5 impl SATA mode
[    1.041952] ahci 0000:00:1f.2: flags: 64bit ncq pm led clo pio slum part ems apst 
[    1.050281] scsi0 : ahci
[    1.050358] scsi1 : ahci
[    1.050443] scsi2 : ahci
[    1.050509] scsi3 : ahci
[    1.050586] scsi4 : ahci
[    1.050656] scsi5 : ahci
[    1.050684] ata1: SATA max UDMA/133 abar m2048@0xf7c36000 port 0xf7c36100 irq 41
[    1.050685] ata2: DUMMY
[    1.050688] ata3: SATA max UDMA/133 abar m2048@0xf7c36000 port 0xf7c36200 irq 41
[    1.050688] ata4: DUMMY
[    1.050689] ata5: DUMMY
[    1.050690] ata6: DUMMY
[    1.050874] e1000e 0000:00:19.0: Interrupt Throttling Rate (ints/sec) set to dynamic conservative mode
[    1.050894] e1000e 0000:00:19.0: irq 42 for MSI/MSI-X
[    1.173954] usb 1-1: new high-speed USB device number 2 using ehci-pci
[    1.258145] e1000e 0000:00:19.0 eth0: registered PHC clock
[    1.258147] e1000e 0000:00:19.0 eth0: (PCI Express:2.5GT/s:Width x1) 9c:8e:99:f3:8c:4a
[    1.258148] e1000e 0000:00:19.0 eth0: Intel(R) PRO/1000 Network Connection
[    1.258195] e1000e 0000:00:19.0 eth0: MAC: 10, PHY: 11, PBA No: 0100FF-0FF
[    1.306382] usb 1-1: New USB device found, idVendor=8087, idProduct=0024
[    1.306386] usb 1-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.306625] hub 1-1:1.0: USB hub found
[    1.306740] hub 1-1:1.0: 6 ports detected
[    1.370042] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.374741] ata3.00: ACPI cmd ef/10:06:00:00:00:00 (SET FEATURES) succeeded
[    1.374747] ata3.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
[    1.374751] ata3.00: ACPI cmd b1/c1:00:00:00:00:00 (DEVICE CONFIGURATION OVERLAY) filtered out
[    1.378052] ata1: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    1.379487] ata1.00: ACPI cmd ef/10:06:00:00:00:00 (SET FEATURES) succeeded
[    1.379493] ata1.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
[    1.379497] ata1.00: ACPI cmd b1/c1:00:00:00:00:00 (DEVICE CONFIGURATION OVERLAY) filtered out
[    1.380527] ata1.00: ATA-8: ST500DM002-1BD142, HP73, max UDMA/100
[    1.380532] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    1.380689] ata3.00: ATAPI: hp       CDDVDW SN-208BB, HD20, max UDMA/100
[    1.382233] ata1.00: ACPI cmd ef/10:06:00:00:00:00 (SET FEATURES) succeeded
[    1.382239] ata1.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
[    1.382243] ata1.00: ACPI cmd b1/c1:00:00:00:00:00 (DEVICE CONFIGURATION OVERLAY) filtered out
[    1.383233] ata1.00: configured for UDMA/100
[    1.383333] scsi 0:0:0:0: Direct-Access     ATA      ST500DM002-1BD14 HP73 PQ: 0 ANSI: 5
[    1.383422] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    1.383425] sd 0:0:0:0: [sda] 4096-byte physical blocks
[    1.383440] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.383487] sd 0:0:0:0: [sda] Write Protect is off
[    1.383490] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.383553] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.387230] ata3.00: ACPI cmd ef/10:06:00:00:00:00 (SET FEATURES) succeeded
[    1.387232] ata3.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
[    1.387234] ata3.00: ACPI cmd b1/c1:00:00:00:00:00 (DEVICE CONFIGURATION OVERLAY) filtered out
[    1.389438] ata3.00: configured for UDMA/100
[    1.394435] scsi 2:0:0:0: CD-ROM            hp       CDDVDW SN-208BB  HD20 PQ: 0 ANSI: 5
[    1.409211] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.409214] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.409323] sr 2:0:0:0: Attached scsi CD-ROM sr0
[    1.409377] sr 2:0:0:0: Attached scsi generic sg1 type 5
[    1.415778] psmouse serio1: alps: Unknown ALPS touchpad: E7=10 00 64, EC=10 00 64
[    1.418066] usb 2-1: new high-speed USB device number 2 using ehci-pci
[    1.421148]  sda: sda1 sda2 < sda5 >
[    1.421609] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.466085] tsc: Refined TSC clocksource calibration: 3392.303 MHz
[    1.550502] usb 2-1: New USB device found, idVendor=8087, idProduct=0024
[    1.550507] usb 2-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.550745] hub 2-1:1.0: USB hub found
[    1.550862] hub 2-1:1.0: 8 ports detected
[    1.622159] usb 1-1.4: new high-speed USB device number 3 using ehci-pci
[    1.731415] usb 1-1.4: New USB device found, idVendor=0603, idProduct=8b03
[    1.731420] usb 1-1.4: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.731423] usb 1-1.4: Manufacturer: DCWGA019I2X9EP
[    2.175259] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input4
[    2.262981] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
[    2.262983] EXT4-fs (sda1): write access will be enabled during recovery
[    2.412844] random: nonblocking pool is initialized
[    2.466614] Switched to clocksource tsc
[    3.034454] EXT4-fs (sda1): orphan cleanup on readonly fs
[    3.405333] EXT4-fs (sda1): 42 orphan inodes deleted
[    3.405335] EXT4-fs (sda1): recovery complete
[    3.528246] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[   11.952003] Adding 4064252k swap on /dev/sda5.  Priority:-1 extents:1 across:4064252k FS
[   12.065943] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   12.121281] systemd-udevd[290]: starting version 204
[   12.153021] lp: driver loaded but no devices found
[   12.158179] ppdev: user-space parallel port driver
[   12.189469] wmi: Mapper loaded
[   12.194447] mei_me 0000:00:16.0: irq 43 for MSI/MSI-X
[   12.204230] [drm] Initialized drm 1.1.0 20060810
[   12.244636] [drm] Memory usable by graphics device = 2048M
[   12.244640] checking generic (e0000000 7f0000) vs hw (e0000000 10000000)
[   12.244641] fb: conflicting fb hw usage inteldrmfb vs VESA VGA - removing generic driver
[   12.244656] Console: switching to colour dummy device 80x25
[   12.270757] i915 0000:00:02.0: irq 44 for MSI/MSI-X
[   12.270767] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[   12.270768] [drm] Driver supports precise vblank timestamp query.
[   12.270877] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   12.306084] kvm: disabled by bios
[   12.313147] type=1400 audit(1444379671.809:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=355 comm="apparmor_parser"
[   12.313154] type=1400 audit(1444379671.809:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=355 comm="apparmor_parser"
[   12.313159] type=1400 audit(1444379671.809:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=355 comm="apparmor_parser"
[   12.313618] type=1400 audit(1444379671.809:5): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=355 comm="apparmor_parser"
[   12.313625] type=1400 audit(1444379671.809:6): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=355 comm="apparmor_parser"
[   12.313858] type=1400 audit(1444379671.809:7): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=355 comm="apparmor_parser"
[   12.351234] fbcon: inteldrmfb (fb0) is primary device
[   12.360566] kvm: disabled by bios
[   12.502183] intel_rapl: domain uncore energy ctr 4319:4319 not working, skip
[   12.649848] Linux video capture interface: v2.00
[   12.661935] uvcvideo: Found UVC 1.00 device <unnamed> (0603:8b03)
[   12.720255] input: UVC Camera (0603:8b03) as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.4/1-1.4:1.0/input/input6
[   12.720340] usbcore: registered new interface driver uvcvideo
[   12.720341] USB Video Class driver (1.1.1)
[   12.735357] input: HP WMI hotkeys as /devices/virtual/input/input5
[   13.820109] [drm] Enabling RC6 states: RC6 on, RC6p on, RC6pp off
[   14.123990] Console: switching to colour frame buffer device 240x67
[   14.130019] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[   14.130020] i915 0000:00:02.0: registered panic notifier
[   14.130100] [Firmware Bug]: Duplicate ACPI video bus devices for the same VGA controller, please try module parameter "video.allow_duplicates=1"if the current driver doesn't work.
[   14.130139] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   14.130273] ACPI Warning: 0x00000428-0x0000042f SystemIO conflicts with Region \PMIO 1 (20131115/utaddress-251)
[   14.130275] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   14.130282] ACPI Warning: 0x00000530-0x0000053f SystemIO conflicts with Region \GPIO 1 (20131115/utaddress-251)
[   14.130282] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   14.130284] ACPI Warning: 0x00000500-0x0000052f SystemIO conflicts with Region \GPIO 1 (20131115/utaddress-251)
[   14.130285] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   14.130285] lpc_ich: Resource conflict(s) found affecting gpio_ich
[   14.130508] snd_hda_intel 0000:00:1b.0: irq 45 for MSI/MSI-X
[   14.145210] autoconfig: line_outs=1 (0xf/0x0/0x0/0x0/0x0) type:line
[   14.145214]    speaker_outs=1 (0xd/0x0/0x0/0x0/0x0)
[   14.145216]    hp_outs=1 (0xb/0x0/0x0/0x0/0x0)
[   14.145217]    mono: mono_out=0x0
[   14.145218]    inputs:
[   14.145220]      Internal Mic=0x11
[   14.145222]      Mic=0xc
[   14.146944] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   14.167516] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   14.167617] input: HDA Intel PCH Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   14.167703] input: HDA Intel PCH Line Out as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   14.167789] input: HDA Intel PCH Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[   14.409138] init: failsafe main process (570) killed by TERM signal
[   14.602426] type=1400 audit(1444379674.097:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=629 comm="apparmor_parser"
[   14.602432] type=1400 audit(1444379674.097:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cupsd" pid=629 comm="apparmor_parser"
[   14.602754] type=1400 audit(1444379674.097:10): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=629 comm="apparmor_parser"
[   14.666669] init: cups main process (630) killed by HUP signal
[   14.666677] init: cups main process ended, respawning
[   14.777098] Bluetooth: Core ver 2.17
[   14.777113] NET: Registered protocol family 31
[   14.777114] Bluetooth: HCI device and connection manager initialized
[   14.777119] Bluetooth: HCI socket layer initialized
[   14.777120] Bluetooth: L2CAP socket layer initialized
[   14.777123] Bluetooth: SCO socket layer initialized
[   14.782032] Bluetooth: RFCOMM TTY layer initialized
[   14.782040] Bluetooth: RFCOMM socket layer initialized
[   14.782043] Bluetooth: RFCOMM ver 1.11
[   14.961131] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   14.961135] Bluetooth: BNEP filters: protocol multicast
[   14.961143] Bluetooth: BNEP socket layer initialized
[   15.678865] e1000e 0000:00:19.0: irq 42 for MSI/MSI-X
[   15.780779] e1000e 0000:00:19.0: irq 42 for MSI/MSI-X
[   15.781002] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   15.781231] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   16.205813] type=1400 audit(1444379675.701:11): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=777 comm="apparmor_parser"
[   19.101254] init: plymouth-upstart-bridge main process ended, respawning
[   19.108518] init: plymouth-upstart-bridge main process ended, respawning
[   29.837767] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: Rx/Tx
[   29.837773] e1000e 0000:00:19.0 eth0: 10/100 speed: disabling TSO
[   29.837807] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   44.688581] audit_printk_skb: 159 callbacks suppressed
[   44.688584] type=1400 audit(1444379663.160:65): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=1869 comm="apparmor_parser"
[   44.688588] type=1400 audit(1444379663.160:66): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=1869 comm="apparmor_parser"
[   44.688914] type=1400 audit(1444379663.160:67): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=1869 comm="apparmor_parser"
[  224.593678] usb 3-3: new high-speed USB device number 2 using xhci_hcd
[  224.610232] usb 3-3: New USB device found, idVendor=2001, idProduct=3314
[  224.610237] usb 3-3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  224.610240] usb 3-3: Product: 802.11n WLAN Adapter
[  224.610243] usb 3-3: Manufacturer: Realtek
[  224.610245] usb 3-3: SerialNumber: 00e04c000001
[  332.846417] systemd-hostnamed[2143]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
[ 1328.614355] sr 2:0:0:0: [sr0]  
[ 1328.614361] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1328.614364] sr 2:0:0:0: [sr0]  
[ 1328.614367] Sense Key : Not Ready [current] 
[ 1328.614378] sr 2:0:0:0: [sr0]  
[ 1328.614382] Add. Sense: Medium not present - tray closed
[ 1328.614385] sr 2:0:0:0: [sr0] CDB: 
[ 1328.614387] Read(10): 28 00 00 00 00 00 00 00 08 00
[ 1328.614397] end_request: I/O error, dev sr0, sector 0
[ 1328.614401] Buffer I/O error on device sr0, logical block 0
[ 1328.614404] Buffer I/O error on device sr0, logical block 1
[ 1328.614406] Buffer I/O error on device sr0, logical block 2
[ 1328.614408] Buffer I/O error on device sr0, logical block 3
[ 1328.614410] Buffer I/O error on device sr0, logical block 4
[ 1328.614412] Buffer I/O error on device sr0, logical block 5
[ 1328.614414] Buffer I/O error on device sr0, logical block 6
[ 1328.614417] Buffer I/O error on device sr0, logical block 7
[ 1328.614422] Buffer I/O error on device sr0, logical block 8
[ 1328.614425] Buffer I/O error on device sr0, logical block 9
[ 1328.614457] sr 2:0:0:0: [sr0] unaligned transfer
[ 1328.614483] sr 2:0:0:0: [sr0] unaligned transfer
[ 1328.614489] sr 2:0:0:0: [sr0] unaligned transfer
[ 1328.614495] sr 2:0:0:0: [sr0] unaligned transfer
[ 1328.614501] sr 2:0:0:0: [sr0] unaligned transfer
[ 1328.614519] sr 2:0:0:0: [sr0] unaligned transfer
[ 1328.614526] sr 2:0:0:0: [sr0] unaligned transfer
[ 1328.614532] sr 2:0:0:0: [sr0] unaligned transfer
[ 1335.611556] systemd-hostnamed[6251]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
[ 1385.304264] init: samba-ad-dc main process (7109) terminated with status 1
[ 1836.505844] audit_printk_skb: 22 callbacks suppressed
[ 1836.505849] type=1400 audit(1444381454.148:68): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=9338 comm="apparmor_parser"
[ 1836.505858] type=1400 audit(1444381454.148:69): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=9338 comm="apparmor_parser"
[ 1836.506312] type=1400 audit(1444381454.148:70): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=9338 comm="apparmor_parser"
[ 1879.133495] sr 2:0:0:0: [sr0]  
[ 1879.133501] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1879.133504] sr 2:0:0:0: [sr0]  
[ 1879.133506] Sense Key : Not Ready [current] 
[ 1879.133510] sr 2:0:0:0: [sr0]  
[ 1879.133514] Add. Sense: Medium not present - tray closed
[ 1879.133517] sr 2:0:0:0: [sr0] CDB: 
[ 1879.133519] Read(10): 28 00 00 00 00 00 00 00 08 00
[ 1879.133528] end_request: I/O error, dev sr0, sector 0
[ 1879.133541] Buffer I/O error on device sr0, logical block 0
[ 1879.133542] Buffer I/O error on device sr0, logical block 1
[ 1879.133543] Buffer I/O error on device sr0, logical block 2
[ 1879.133544] Buffer I/O error on device sr0, logical block 3
[ 1879.133545] Buffer I/O error on device sr0, logical block 4
[ 1879.133546] Buffer I/O error on device sr0, logical block 5
[ 1879.133547] Buffer I/O error on device sr0, logical block 6
[ 1879.133548] Buffer I/O error on device sr0, logical block 7
[ 1879.133551] Buffer I/O error on device sr0, logical block 8
[ 1879.133552] Buffer I/O error on device sr0, logical block 9
[ 1879.133557] sr 2:0:0:0: [sr0] unaligned transfer
[ 1879.133563] sr 2:0:0:0: [sr0] unaligned transfer
[ 1879.133566] sr 2:0:0:0: [sr0] unaligned transfer
[ 1879.133569] sr 2:0:0:0: [sr0] unaligned transfer
[ 1879.133572] sr 2:0:0:0: [sr0] unaligned transfer
[ 1879.133575] sr 2:0:0:0: [sr0] unaligned transfer
[ 1879.133577] sr 2:0:0:0: [sr0] unaligned transfer
[ 1879.133580] sr 2:0:0:0: [sr0] unaligned transfer
[ 3674.698845] ip_tables: (C) 2000-2006 Netfilter Core Team
[ 3685.649895] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[ 3685.746619] ip6_tables: (C) 2000-2006 Netfilter Core Team
[ 3690.858821] [UFW BLOCK] IN=eth0 OUT= MAC= SRC=192.168.0.111 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 3694.236197] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:00:1a:22:00:dd:b2:08:00 SRC=192.168.0.106 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=26766 PROTO=2 
[ 3696.060638] [UFW BLOCK] IN=eth0 OUT= MAC=9c:8e:99:f3:8c:4a:64:66:b3:3a:b7:04:08:00 SRC=157.56.127.11 DST=192.168.0.111 LEN=553 TOS=0x00 PREC=0x00 TTL=115 ID=28108 DF PROTO=TCP SPT=443 DPT=55613 WINDOW=64643 RES=0x00 ACK PSH URGP=0 
[ 3698.455153] [UFW BLOCK] IN=eth0 OUT= MAC=9c:8e:99:f3:8c:4a:6c:ad:f8:4f:f0:d1:08:00 SRC=192.168.0.105 DST=192.168.0.111 LEN=544 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=50273 DPT=54691 LEN=524 
[ 4267.404261] systemd-hostnamed[16739]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
```

---

### Post by gordintoronto on 2015-10-09
I'm not sure what you posted, but it wasn't what I would have expected. How about the output from the command: lsusb

Also, what version of Ubuntu? Does USB work when you plug in a flash drive?

---

### Post by paul-summermatter on 2015-10-12
Txs Gordintoronto

Yes - the usb does workwith a flash stick. Here are the infos of [COLOR=#000000]lsusb
> [/COLOR]Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching HubBus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0603:8b03 Novatek Microelectronics Corp. 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 004: ID 2001:3314 D-Link Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


[COLOR=#000000]
[/COLOR]

---

### Post by Skaperen on 2015-10-12
is your dvd/br drive connected by USB? unplug it (or remove the disk it has) and reboot.

---

### Post by paul-summermatter on 2015-10-12
No it's not. It is an internal drive with no dosk in it.

---

### Post by gordintoronto on 2015-10-12
What version of Ubuntu? (Eg: Ubuntu desktop 14.04 64-bit.) Your DWA-171 is being recognized, what does Network Manager show?

---

### Post by Skaperen on 2015-10-13
did you install ubuntu from a cd/dvd or from a memory stick?  still have it?  can you boot up the live system from that to test USB with to see if there is a software configuration issue?

---

### Post by paul-summermatter on 2015-10-14
Hi

It is 14.04. lts on 32-bit.
[http://pix.toile-libre.org/upload/original/1444806546.png](http://pix.toile-libre.org/upload/original/1444806546.png)

It does not show any error in the network manager

paul

---

### Post by gordintoronto on 2015-10-14
USB is working, it's your WiFi adapter which is not working. Did it work under Linux previously?

---

### Post by paul-summermatter on 2015-10-15
Yes it did worked under linux. I did some workarround from a forum and it worked for months without any problem.

Paul

---

### Post by Bucky Ball on 2015-10-15
*Thread moved to **Networking and Wireless**.*

> **gordintoronto said:**
> USB is working, it's your WiFi adapter which is not working.

... agreed and consequently thread moved to the correct area and renamed. Good luck. 

You might try posting the output of:

```
sudo lshw -C network
```


... between code tags (see last link in my signature). Make sure you have the dongle plugged in when issuing the command.

---

### Post by michi1983 on 2015-10-15
And what exactly does not work with your dw-171?
Does it see wifi-networks?
Is it that you just can't connect to it?

Please also post the output of
```
ifconfig -a
```

---

### Post by Skaperen on 2015-10-16
can you boot up the ubuntu cd and see if your usb wifi-adapter still works there?  this is to see if there is a hardware problem (like a bad connector or bad power supply voltage) or a software problem (missing or bad driver).

---

### Post by chili555 on 2015-10-16
This device uses the driver 8812au. I suspect you had to compile the driver from source code. When a later kernel version, also known as linux-image, is installed, you must re-compile:```
cd ~/Desktop/rtl8812AU_8821AU_linux/
```...or wherever you have the files downloaded.```
make clean
make
sudo make install
```Reboot.

---

### Post by paul-summermatter on 2015-10-25
You are my hero chili555!!! :D

This worked perfectly and I can use my USB-Network-Stick again.
Thank you very much!

Paul

---

