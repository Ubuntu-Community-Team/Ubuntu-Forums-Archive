---
title: "Ralink Wireless Problems"
date: 2014-04-15
forum: Networking &amp; Wireless
---

### Post by xtjacob on 2014-04-15
Hello all,
I ham having a crazy problem with the wireless NIC in my HP Pvilion dv7. I used to be running a dual boot of Arch and Windows 8.1, but my Windows 8.1 installation croaked, forcing me to reinstall it. Since then I have not been able to remove the hardblock on the wireless card. I've experimented with it in Arch, Debian, and now I'm back to Ubuntu 13.10. The wireless key on my keyboard fails to do anything (hard or soft block), and even if I try plugging in another wireless card NetworkManager still says it's disabled.

Here's lspci:
```

0a:00.0 Network controller: Ralink corp. Device 539a
	Subsystem: Hewlett-Packard Company Device 1839
	Flags: bus master, fast devsel, latency 0, IRQ 19
	Memory at d4500000 (32-bit, non-prefetchable) [size=64K]
	Capabilities: [40] Power Management version 3
	Capabilities: [50] MSI: Enable- Count=1/32 Maskable- 64bit+
	Capabilities: [70] Express Endpoint, MSI 00
	Capabilities: [100] Advanced Error Reporting
	Capabilities: [140] Device Serial Number xx-xx-xx-xx-xx-x-xx-xx
	Kernel driver in use: rt2800pci

0b:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 07)
	Subsystem: Hewlett-Packard Company Device 1818
	Flags: bus master, fast devsel, latency 0, IRQ 44
	I/O ports at 2000 [size=256]
	Memory at d4404000 (64-bit, prefetchable) [size=4K]
	Memory at d4400000 (64-bit, prefetchable) [size=16K]
	Capabilities: [40] Power Management version 3
	Capabilities: [50] MSI: Enable+ Count=1/1 Maskable- 64bit+
	Capabilities: [70] Express Endpoint, MSI 01
	Capabilities: [b0] MSI-X: Enable- Count=4 Masked-
	Capabilities: [d0] Vital Product Data
	Capabilities: [100] Advanced Error Reporting
	Capabilities: [140] Virtual Channel
	Capabilities: [160] Device Serial Number xx-xx-xx-xx-xx-xx-xx-xx
	Kernel driver in use: r8169

```

rfkill list:
```

0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes

```

dmesg:
```

[    1.421924] SCSI subsystem initialized
[    1.421926] ACPI: bus type ATA registered
[    1.421955] libata version 3.00 loaded.
[    1.421966] ACPI: bus type USB registered
[    1.421975] usbcore: registered new interface driver usbfs
[    1.421980] usbcore: registered new interface driver hub
[    1.421992] usbcore: registered new device driver usb
[    1.422065] PCI: Using ACPI for IRQ routing
[    1.428279] PCI: pci_cache_line_size set to 64 bytes
[    1.428401] e820: reserve RAM buffer [mem 0x00091800-0x0009ffff]
[    1.428402] e820: reserve RAM buffer [mem 0x40004000-0x43ffffff]
[    1.428403] e820: reserve RAM buffer [mem 0x9a3bf000-0x9bffffff]
[    1.428404] e820: reserve RAM buffer [mem 0x9b000000-0x9bffffff]
[    1.428405] e820: reserve RAM buffer [mem 0x25f600000-0x25fffffff]
[    1.428461] NetLabel: Initializing
[    1.428462] NetLabel:  domain hash size = 128
[    1.428463] NetLabel:  protocols = UNLABELED CIPSOv4
[    1.428469] NetLabel:  unlabeled traffic allowed by default
[    1.428508] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    1.428512] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    1.430533] Switched to clocksource hpet
[    1.433680] AppArmor: AppArmor Filesystem Enabled
[    1.433697] pnp: PnP ACPI init
[    1.433705] ACPI: bus type PNP registered
[    1.433727] pnp 00:00: [dma 4]
[    1.433741] pnp 00:00: Plug and Play ACPI device, IDs PNP0200 (active)
[    1.433753] pnp 00:01: Plug and Play ACPI device, IDs INT0800 (active)
[    1.433821] pnp 00:02: Plug and Play ACPI device, IDs PNP0103 (active)
[    1.433840] pnp 00:03: Plug and Play ACPI device, IDs PNP0c04 (active)
[    1.433868] system 00:04: [io  0x1100-0x110f] has been reserved
[    1.433869] system 00:04: [io  0xffff] has been reserved
[    1.433870] system 00:04: [io  0xffff] has been reserved
[    1.433872] system 00:04: [io  0x0400-0x0453] could not be reserved
[    1.433873] system 00:04: [io  0x0458-0x047f] has been reserved
[    1.433875] system 00:04: [io  0x0500-0x057f] has been reserved
[    1.433876] system 00:04: [io  0x1200-0x1207] has been reserved
[    1.433878] system 00:04: [mem 0xfe800000-0xfe8001ff] has been reserved
[    1.433880] system 00:04: Plug and Play ACPI device, IDs PNP0c02 (active)
[    1.433895] pnp 00:05: Plug and Play ACPI device, IDs PNP0b00 (active)
[    1.433925] system 00:06: [io  0x0454-0x0457] has been reserved
[    1.433926] system 00:06: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
[    1.433968] pnp 00:07: Plug and Play ACPI device, IDs HPQ8001 PNP0303 (active)
[    1.433986] pnp 00:08: Plug and Play ACPI device, IDs SYN1e5e SYN1e00 SYN0002 PNP0f13 (active)
[    1.434068] system 00:09: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    1.434070] system 00:09: [mem 0xfed10000-0xfed17fff] has been reserved
[    1.434071] system 00:09: [mem 0xfed18000-0xfed18fff] has been reserved
[    1.434072] system 00:09: [mem 0xfed19000-0xfed19fff] has been reserved
[    1.434074] system 00:09: [mem 0xe0000000-0xefffffff] has been reserved
[    1.434075] system 00:09: [mem 0xfed20000-0xfed3ffff] has been reserved
[    1.434076] system 00:09: [mem 0xfed90000-0xfed93fff] has been reserved
[    1.434078] system 00:09: [mem 0xff000000-0xffffffff] could not be reserved
[    1.434079] system 00:09: [mem 0xfee00000-0xfeefffff] could not be reserved
[    1.434081] system 00:09: [mem 0x9fa00000-0x9fa00fff] has been reserved
[    1.434082] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
[    1.434275] system 00:0a: [mem 0x20000000-0x201fffff] has been reserved
[    1.434277] system 00:0a: [mem 0x40004000-0x40004fff] has been reserved
[    1.434278] system 00:0a: Plug and Play ACPI device, IDs PNP0c01 (active)
[    1.434315] pnp 00:0b: Plug and Play ACPI device, IDs HPQ0004 (active)
[    1.434336] pnp: PnP ACPI: found 12 devices
[    1.434336] ACPI: bus type PNP unregistered
[    1.440212] pci 0000:01:00.0: no compatible bridge window for [mem 0xfff80000-0xffffffff pref]
[    1.440262] pci 0000:01:00.0: BAR 6: assigned [mem 0xb2000000-0xb207ffff pref]
[    1.440264] pci 0000:00:01.0: PCI bridge to [bus 01-06]
[    1.440265] pci 0000:00:01.0:   bridge window [io  0x4000-0x4fff]
[    1.440267] pci 0000:00:01.0:   bridge window [mem 0xd2000000-0xd3ffffff]
[    1.440269] pci 0000:00:01.0:   bridge window [mem 0xa0000000-0xbfffffff 64bit pref]
[    1.440272] pci 0000:00:1c.0: PCI bridge to [bus 07]
[    1.440289] pci 0000:00:1c.1: PCI bridge to [bus 08-09]
[    1.440292] pci 0000:00:1c.1:   bridge window [io  0x3000-0x3fff]
[    1.440298] pci 0000:00:1c.1:   bridge window [mem 0xd1000000-0xd1ffffff]
[    1.440302] pci 0000:00:1c.1:   bridge window [mem 0xd0000000-0xd0ffffff 64bit pref]
[    1.440310] pci 0000:00:1c.3: PCI bridge to [bus 0a]
[    1.440316] pci 0000:00:1c.3:   bridge window [mem 0xd4500000-0xd45fffff]
[    1.440328] pci 0000:00:1c.5: PCI bridge to [bus 0b]
[    1.440330] pci 0000:00:1c.5:   bridge window [io  0x2000-0x2fff]
[    1.440335] pci 0000:00:1c.5:   bridge window [mem 0xd4400000-0xd44fffff]
[    1.440595] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    1.440597] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    1.440598] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    1.440599] pci_bus 0000:00: resource 7 [mem 0x9fa00000-0xfeafffff]
[    1.440601] pci_bus 0000:01: resource 0 [io  0x4000-0x4fff]
[    1.440602] pci_bus 0000:01: resource 1 [mem 0xd2000000-0xd3ffffff]
[    1.440603] pci_bus 0000:01: resource 2 [mem 0xa0000000-0xbfffffff 64bit pref]
[    1.440604] pci_bus 0000:08: resource 0 [io  0x3000-0x3fff]
[    1.440606] pci_bus 0000:08: resource 1 [mem 0xd1000000-0xd1ffffff]
[    1.440607] pci_bus 0000:08: resource 2 [mem 0xd0000000-0xd0ffffff 64bit pref]
[    1.440608] pci_bus 0000:0a: resource 1 [mem 0xd4500000-0xd45fffff]
[    1.440609] pci_bus 0000:0b: resource 0 [io  0x2000-0x2fff]
[    1.440611] pci_bus 0000:0b: resource 1 [mem 0xd4400000-0xd44fffff]
[    1.440630] NET: Registered protocol family 2
[    1.440758] TCP established hash table entries: 65536 (order: 8, 1048576 bytes)
[    1.440908] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    1.441019] TCP: Hash tables configured (established 65536 bind 65536)
[    1.441030] TCP: reno registered
[    1.441038] UDP hash table entries: 4096 (order: 5, 131072 bytes)
[    1.441060] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
[    1.441109] NET: Registered protocol family 1
[    1.441116] pci 0000:00:02.0: Boot video device
[    1.474691] PCI: CLS 64 bytes, default 64
[    1.474719] Trying to unpack rootfs image as initramfs...
[    1.677129] Freeing initrd memory: 17020K (ffff880035eb2000 - ffff880036f51000)
[    1.677133] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    1.677135] software IO TLB [mem 0x963bf000-0x9a3bf000] (64MB) mapped at [ffff8800963bf000-ffff88009a3befff]
[    1.677170] Simple Boot Flag at 0x44 set to 0x1
[    1.677384] Scanning for low memory corruption every 60 seconds
[    1.677590] Initialise module verification
[    1.677619] audit: initializing netlink socket (disabled)
[    1.677630] type=2000 audit(1397571963.624:1): initialized
[    1.697419] bounce pool size: 64 pages
[    1.697426] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.698250] zbud: loaded
[    1.698345] VFS: Disk quotas dquot_6.5.2
[    1.698371] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.698701] fuse init (API version 7.22)
[    1.698753] msgmni has been set to 15755
[    1.699158] Key type asymmetric registered
[    1.699159] Asymmetric key parser 'x509' registered
[    1.699179] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    1.699215] io scheduler noop registered
[    1.699216] io scheduler deadline registered (default)
[    1.699233] io scheduler cfq registered
[    1.699292] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
[    1.699543] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.699552] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.699585] intel_idle: MWAIT substates: 0x21120
[    1.699586] intel_idle: v0.4 model 0x3A
[    1.699586] intel_idle: lapic_timer_reliable_states 0xffffffff
[    1.730412] ACPI: AC Adapter [ADP1] (on-line)
[    1.730486] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    1.762396] ACPI: Lid Switch [LID0]
[    1.762428] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    1.762431] ACPI: Power Button [PWRF]
[    1.778417] ACPI: Requesting acpi_cpufreq
[    2.030257] thermal LNXTHERM:00: registered as thermal_zone0
[    2.030259] ACPI: Thermal Zone [TZS0] (57 C)
[    2.046245] [Firmware Bug]: No valid trip found
[    2.262134] thermal LNXTHERM:02: registered as thermal_zone1
[    2.262135] ACPI: Thermal Zone [TZS2] (59 C)
[    2.382072] thermal LNXTHERM:03: registered as thermal_zone2
[    2.382073] ACPI: Thermal Zone [TZS3] (30 C)
[    2.382093] GHES: HEST is not enabled!
[    2.382139] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    2.454051] Linux agpgart interface v0.103
[    2.454845] brd: module loaded
[    2.455249] loop: module loaded
[    2.455450] libphy: Fixed MDIO Bus: probed
[    2.455495] tun: Universal TUN/TAP device driver, 1.6
[    2.455496] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    2.455523] PPP generic driver version 2.4.2
[    2.455548] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.455550] ehci-pci: EHCI PCI platform driver
[    2.455622] ehci-pci 0000:00:1a.0: setting latency timer to 64
[    2.455628] ehci-pci 0000:00:1a.0: EHCI Host Controller
[    2.455632] ehci-pci 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    2.455644] ehci-pci 0000:00:1a.0: debug port 2
[    2.459552] ehci-pci 0000:00:1a.0: cache line size of 64 is not supported
[    2.459566] ehci-pci 0000:00:1a.0: irq 16, io mem 0xd4619000
[    2.470013] ehci-pci 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    2.470025] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    2.470026] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    2.470027] usb usb1: Product: EHCI Host Controller
[    2.470028] usb usb1: Manufacturer: Linux 3.11.0-19-generic ehci_hcd
[    2.470029] usb usb1: SerialNumber: 0000:00:1a.0
[    2.470091] hub 1-0:1.0: USB hub found
[    2.470094] hub 1-0:1.0: 2 ports detected
[    2.470217] ehci-pci 0000:00:1d.0: setting latency timer to 64
[    2.470222] ehci-pci 0000:00:1d.0: EHCI Host Controller
[    2.470225] ehci-pci 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    2.470236] ehci-pci 0000:00:1d.0: debug port 2
[    2.474132] ehci-pci 0000:00:1d.0: cache line size of 64 is not supported
[    2.474143] ehci-pci 0000:00:1d.0: irq 23, io mem 0xd4618000
[    2.486007] ehci-pci 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    2.486015] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    2.486016] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    2.486017] usb usb2: Product: EHCI Host Controller
[    2.486018] usb usb2: Manufacturer: Linux 3.11.0-19-generic ehci_hcd
[    2.486019] usb usb2: SerialNumber: 0000:00:1d.0
[    2.486074] hub 2-0:1.0: USB hub found
[    2.486076] hub 2-0:1.0: 2 ports detected
[    2.486137] ehci-platform: EHCI generic platform driver
[    2.486142] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.486143] ohci-pci: OHCI PCI platform driver
[    2.486149] ohci-platform: OHCI generic platform driver
[    2.486153] uhci_hcd: USB Universal Host Controller Interface driver
[    2.486225] xhci_hcd 0000:00:14.0: setting latency timer to 64
[    2.486228] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    2.486231] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 3
[    2.486317] xhci_hcd 0000:00:14.0: cache line size of 64 is not supported
[    2.486334] xhci_hcd 0000:00:14.0: irq 41 for MSI/MSI-X
[    2.486371] usb usb3: New USB device found, idVendor=1d6b, idProduct=0002
[    2.486372] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    2.486373] usb usb3: Product: xHCI Host Controller
[    2.486375] usb usb3: Manufacturer: Linux 3.11.0-19-generic xhci_hcd
[    2.486376] usb usb3: SerialNumber: 0000:00:14.0
[    2.486417] xHCI xhci_add_endpoint called for root hub
[    2.486418] xHCI xhci_check_bandwidth called for root hub
[    2.486431] hub 3-0:1.0: USB hub found
[    2.486436] hub 3-0:1.0: 4 ports detected
[    2.486640] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    2.486642] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 4
[    2.486658] usb usb4: New USB device found, idVendor=1d6b, idProduct=0003
[    2.486659] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    2.486660] usb usb4: Product: xHCI Host Controller
[    2.486661] usb usb4: Manufacturer: Linux 3.11.0-19-generic xhci_hcd
[    2.486662] usb usb4: SerialNumber: 0000:00:14.0
[    2.486704] xHCI xhci_add_endpoint called for root hub
[    2.486704] xHCI xhci_check_bandwidth called for root hub
[    2.486716] hub 4-0:1.0: USB hub found
[    2.486722] hub 4-0:1.0: 4 ports detected
[    2.502028] i8042: PNP: PS/2 Controller [PNP0303:KBD0,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    2.527298] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.527302] serio: i8042 AUX port at 0x60,0x64 irq 12
[    2.527369] mousedev: PS/2 mouse device common for all mice
[    2.528544] rtc_cmos 00:05: RTC can wake from S4
[    2.528646] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    2.528673] rtc_cmos 00:05: alarms up to one month, 242 bytes nvram, hpet irqs
[    2.528709] device-mapper: uevent: version 1.0.3
[    2.528745] device-mapper: ioctl: 4.25.0-ioctl (2013-06-26) initialised: dm-devel@redhat.com
[    2.528847] cpuidle: using governor ladder
[    2.528988] cpuidle: using governor menu
[    2.528996] ledtrig-cpu: registered to indicate activity on CPUs
[    2.529052] TCP: cubic registered
[    2.529104] NET: Registered protocol family 10
[    2.529222] NET: Registered protocol family 17
[    2.529228] Key type dns_resolver registered
[    2.529414] PM: Hibernation image not present or could not be loaded.
[    2.529417] Loading module verification certificates
[    2.530050] MODSIGN: Loaded cert 'Magrathea: Glacier signing key: 5553b4b7b74ebe0a90f93fbc0d8e2b9c98211b47'
[    2.530056] registered taskstats version 1
[    2.531500] Key type trusted registered
[    2.532707] Key type encrypted registered
[    2.534061] AppArmor: AppArmor sha1 policy hashing enabled
[    2.534547]   Magic number: 10:971:434
[    2.534642] rtc_cmos 00:05: setting system clock to 2014-04-15 14:26:05 UTC (1397571965)
[    2.558484] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
[    2.673984] tsc: Refined TSC clocksource calibration: 2294.787 MHz
[    2.742687] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.742690] EDD information not available.
[    2.781944] usb 1-1: new high-speed USB device number 2 using ehci-pci
[    2.914293] usb 1-1: New USB device found, idVendor=8087, idProduct=0024
[    2.914301] usb 1-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    2.914738] hub 1-1:1.0: USB hub found
[    2.914937] hub 1-1:1.0: 6 ports detected
[    3.025748] usb 2-1: new high-speed USB device number 2 using ehci-pci
[    3.158166] usb 2-1: New USB device found, idVendor=8087, idProduct=0024
[    3.158173] usb 2-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    3.158616] hub 2-1:1.0: USB hub found
[    3.158804] hub 2-1:1.0: 8 ports detected
[    3.229902] usb 1-1.1: new full-speed USB device number 3 using ehci-pci
[    3.323376] usb 1-1.1: New USB device found, idVendor=138a, idProduct=0018
[    3.323383] usb 1-1.1: New USB device strings: Mfr=0, Product=0, SerialNumber=1
[    3.323387] usb 1-1.1: SerialNumber: 97b7066917f4
[    3.393799] usb 1-1.3: new high-speed USB device number 4 using ehci-pci
[    3.543289] usb 1-1.3: New USB device found, idVendor=064e, idProduct=c334
[    3.543297] usb 1-1.3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    3.543300] usb 1-1.3: Product: HP Truevision HD
[    3.543303] usb 1-1.3: Manufacturer: SuYin
[    3.543306] usb 1-1.3: SerialNumber: HF1016-P62A-OV01-VH-R04.00.06
[    3.673727] Switched to clocksource tsc
[    3.897456] ACPI: Battery Slot [BAT0] (battery present)
[    3.898209] Freeing unused kernel memory: 1368K (ffffffff81d10000 - ffffffff81e66000)
[    3.898212] Write protecting the kernel read-only data: 12288k
[    3.900006] Freeing unused kernel memory: 1028K (ffff8800016ff000 - ffff880001800000)
[    3.901249] Freeing unused kernel memory: 784K (ffff880001b3c000 - ffff880001c00000)
[    3.909916] systemd-udevd[148]: starting version 204
[    3.950683] rtsx_pci 0000:08:00.0: irq 42 for MSI/MSI-X
[    3.950714] rtsx_pci 0000:08:00.0: rtsx_pci_acquire_irq: pcr->msi_en = 1, pci->irq = 42
[    3.952018] ahci 0000:00:1f.2: version 3.0
[    3.952124] ahci 0000:00:1f.2: irq 43 for MSI/MSI-X
[    3.954781] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    3.954789] r8169 0000:0b:00.0: can't disable ASPM; OS doesn't have ASPM control
[    3.954995] r8169 0000:0b:00.0: irq 44 for MSI/MSI-X
[    3.955170] r8169 0000:0b:00.0 eth0: RTL8168evl/8111evl at 0xffffc90000c56000, a0:b3:cc:52:01:3e, XID 0c900800 IRQ 44
[    3.955173] r8169 0000:0b:00.0 eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
[    3.965257] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 6 Gbps 0x11 impl RAID mode
[    3.965261] ahci 0000:00:1f.2: flags: 64bit ncq pm led clo pio slum part ems apst 
[    3.965265] ahci 0000:00:1f.2: setting latency timer to 64
[    3.973535] scsi0 : ahci
[    3.973589] scsi1 : ahci
[    3.973623] scsi2 : ahci
[    3.973653] scsi3 : ahci
[    3.973684] scsi4 : ahci
[    3.973714] scsi5 : ahci
[    3.973750] ata1: SATA max UDMA/133 abar m2048@0xd4617000 port 0xd4617100 irq 43
[    3.973751] ata2: DUMMY
[    3.973752] ata3: DUMMY
[    3.973752] ata4: DUMMY
[    3.973755] ata5: SATA max UDMA/133 abar m2048@0xd4617000 port 0xd4617300 irq 43
[    3.973756] ata6: DUMMY
[    4.293162] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    4.295336] ata5.00: ATAPI: hp DVDWBD SN-406AB, HH01, max UDMA/100
[    4.301157] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    4.302196] ata5.00: configured for UDMA/100
[    4.302329] ata1.00: ATA-8: WDC WD10JPVT-60A1YT0, 01.01A01, max UDMA/133
[    4.302336] ata1.00: 1953525168 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
[    4.303863] ata1.00: configured for UDMA/133
[    4.304118] scsi 0:0:0:0: Direct-Access     ATA      WDC WD10JPVT-60A 01.0 PQ: 0 ANSI: 5
[    4.304271] sd 0:0:0:0: [sda] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    4.304274] sd 0:0:0:0: [sda] 4096-byte physical blocks
[    4.304285] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    4.304322] sd 0:0:0:0: [sda] Write Protect is off
[    4.304325] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.304344] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.309220] scsi 4:0:0:0: CD-ROM            hp       DVDWBD SN-406AB  HH01 PQ: 0 ANSI: 5
[    4.316235] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    4.316242] cdrom: Uniform CD-ROM driver Revision: 3.20
[    4.316457] sr 4:0:0:0: Attached scsi CD-ROM sr0
[    4.316598] sr 4:0:0:0: Attached scsi generic sg1 type 5
[    4.352803]  sda: sda1 sda2 sda3 < sda5 sda6 >
[    4.353462] sd 0:0:0:0: [sda] Attached SCSI disk
[    5.737265] EXT4-fs (sda6): INFO: recovery required on readonly filesystem
[    5.737268] EXT4-fs (sda6): write access will be enabled during recovery
[    6.549457] EXT4-fs (sda6): recovery complete
[    6.557682] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
[    8.416218] Adding 6347772k swap on /dev/sda5.  Priority:-1 extents:1 across:6347772k FS
[    9.618808] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    9.907190] systemd-udevd[348]: starting version 204
[   10.407233] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
[   10.783906] lp: driver loaded but no devices found
[   12.249079] microcode: CPU0 sig=0x306a9, pf=0x10, revision=0x15
[   12.509967] wmi: Mapper loaded
[   12.617850] ACPI Warning: 0x0000000000000428-0x000000000000042f SystemIO conflicts with Region \PMIO 1 (20130517/utaddress-251)
[   12.617856] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   12.617859] ACPI Warning: 0x0000000000000530-0x000000000000053f SystemIO conflicts with Region \GPIO 1 (20130517/utaddress-251)
[   12.617861] ACPI Warning: 0x0000000000000530-0x000000000000053f SystemIO conflicts with Region \_SB_.GPIO 2 (20130517/utaddress-251)
[   12.617864] ACPI Warning: 0x0000000000000530-0x000000000000053f SystemIO conflicts with Region \_SB_.PCI0.PEG0.PEGP.GPIO 3 (20130517/utaddress-251)
[   12.617866] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   12.617866] ACPI Warning: 0x0000000000000500-0x000000000000052f SystemIO conflicts with Region \GPIO 1 (20130517/utaddress-251)
[   12.617868] ACPI Warning: 0x0000000000000500-0x000000000000052f SystemIO conflicts with Region \_SB_.GPIO 2 (20130517/utaddress-251)
[   12.617870] ACPI Warning: 0x0000000000000500-0x000000000000052f SystemIO conflicts with Region \_SB_.PCI0.PEG0.PEGP.GPIO 3 (20130517/utaddress-251)
[   12.617872] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   12.617873] lpc_ich: Resource conflict(s) found affecting gpio_ich
[   12.667765] hp_accel: hardware type DV7 found
[   12.696266] [drm] Initialized drm 1.1.0 20060810
[   12.760053] mei_me 0000:00:16.0: setting latency timer to 64
[   12.760087] mei_me 0000:00:16.0: irq 45 for MSI/MSI-X
[   12.880694] lis3lv02d: 8 bits 3DC sensor found
[   13.080603] input: ST LIS3LV02DL Accelerometer as /devices/platform/lis3lv02d/input/input3
[   13.142528] cfg80211: Calling CRDA to update world regulatory domain
[   13.335390] MXM: GUID detected in BIOS
[   13.335416] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Integer], ACPI requires [Package] (20130517/nsarguments-95)
[   13.335459] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20130517/nsarguments-95)
[   13.335509] VGA switcheroo: detected Optimus DSM method \_SB_.PCI0.PEG0.PEGP handle
[   13.335530] nouveau 0000:01:00.0: enabling device (0006 -> 0007)
[   13.335954] nouveau  [  DEVICE][0000:01:00.0] BOOT0  : 0x0c1480a1
[   13.335957] nouveau  [  DEVICE][0000:01:00.0] Chipset: GF108 (NVC1)
[   13.335959] nouveau  [  DEVICE][0000:01:00.0] Family : NVC0
[   13.337724] nouveau  [   VBIOS][0000:01:00.0] checking PRAMIN for image...
[   13.347449] nouveau  [   VBIOS][0000:01:00.0] ... signature not found
[   13.347451] nouveau  [   VBIOS][0000:01:00.0] checking PROM for image...
[   13.347518] nouveau  [   VBIOS][0000:01:00.0] ... signature not found
[   13.347519] nouveau  [   VBIOS][0000:01:00.0] checking ACPI for image...
[   13.584952] Bluetooth: Core ver 2.16
[   13.584965] NET: Registered protocol family 31
[   13.584966] Bluetooth: HCI device and connection manager initialized
[   13.584972] Bluetooth: HCI socket layer initialized
[   13.584974] Bluetooth: L2CAP socket layer initialized
[   13.584977] Bluetooth: SCO socket layer initialized
[   13.653173] init: avahi-cups-reload main process (515) terminated with status 1
[   13.723329] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   13.723331] Bluetooth: BNEP filters: protocol multicast
[   13.723338] Bluetooth: BNEP socket layer initialized
[   13.756056] microcode: CPU1 sig=0x306a9, pf=0x10, revision=0x15
[   13.808569] ppdev: user-space parallel port driver
[   13.824801] psmouse serio1: synaptics: Touchpad model: 1, fw: 8.1, id: 0x1e2b1, caps: 0xd00123/0x840300/0x26c00, board id: 2055, fw id: 1107424
[   13.891001] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input4
[   14.111835] Bluetooth: RFCOMM TTY layer initialized
[   14.111845] Bluetooth: RFCOMM socket layer initialized
[   14.111846] Bluetooth: RFCOMM ver 1.11
[   14.163886] microcode: CPU2 sig=0x306a9, pf=0x10, revision=0x15
[   14.164590] microcode: CPU3 sig=0x306a9, pf=0x10, revision=0x15
[   14.164963] microcode: CPU4 sig=0x306a9, pf=0x10, revision=0x15
[   14.165328] microcode: CPU5 sig=0x306a9, pf=0x10, revision=0x15
[   14.165791] microcode: CPU6 sig=0x306a9, pf=0x10, revision=0x15
[   14.166205] microcode: CPU7 sig=0x306a9, pf=0x10, revision=0x15
[   14.166650] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[   14.172826] Linux video capture interface: v2.00
[   14.328222] ieee80211 phy0: rt2x00_set_rt: Info - RT chipset 5390, rev 1502 detected
[   14.332562] ieee80211 phy0: rt2x00_set_rf: Info - RF chipset 5390 detected
[   14.358675] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   14.434111] uvcvideo: Found UVC 1.00 device HP Truevision HD (064e:c334)
[   14.442565] input: HP Truevision HD as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3:1.0/input/input5
[   14.478239] type=1400 audit(1397589977.443:2): apparmor="STATUS" operation="profile_load" parent=534 profile="unconfined" name="/sbin/dhclient" pid=535 comm="apparmor_parser"
[   14.478244] type=1400 audit(1397589977.443:3): apparmor="STATUS" operation="profile_load" parent=534 profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=535 comm="apparmor_parser"
[   14.478247] type=1400 audit(1397589977.443:4): apparmor="STATUS" operation="profile_load" parent=534 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=535 comm="apparmor_parser"
[   14.478254] type=1400 audit(1397589977.443:5): apparmor="STATUS" operation="profile_replace" parent=492 profile="unconfined" name="/sbin/dhclient" pid=498 comm="apparmor_parser"
[   14.478260] type=1400 audit(1397589977.443:6): apparmor="STATUS" operation="profile_replace" parent=492 profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=498 comm="apparmor_parser"
[   14.478263] type=1400 audit(1397589977.443:7): apparmor="STATUS" operation="profile_replace" parent=492 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=498 comm="apparmor_parser"
[   14.478270] type=1400 audit(1397589977.443:8): apparmor="STATUS" operation="profile_replace" parent=580 profile="unconfined" name="/sbin/dhclient" pid=581 comm="apparmor_parser"
[   14.478275] type=1400 audit(1397589977.443:9): apparmor="STATUS" operation="profile_replace" parent=580 profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=581 comm="apparmor_parser"
[   14.478278] type=1400 audit(1397589977.443:10): apparmor="STATUS" operation="profile_replace" parent=580 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=581 comm="apparmor_parser"
[   14.478632] type=1400 audit(1397589977.443:11): apparmor="STATUS" operation="profile_replace" parent=534 profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=535 comm="apparmor_parser"
[   14.803971] cfg80211: World regulatory domain updated:
[   14.803974] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   14.803975] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.803976] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.803977] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   14.803978] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.803979] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.031954] input: HP WMI hotkeys as /devices/virtual/input/input6
[   15.195651] nouveau  [   VBIOS][0000:01:00.0] ... appears to be valid
[   15.195654] nouveau  [   VBIOS][0000:01:00.0] using image from ACPI
[   15.195736] nouveau  [   VBIOS][0000:01:00.0] BIT signature found
[   15.195739] nouveau  [   VBIOS][0000:01:00.0] version 70.08.cb.00.03
[   15.196004] nouveau  [ DEVINIT][0000:01:00.0] adaptor not initialised
[   15.196007] nouveau  [   VBIOS][0000:01:00.0] running init tables
[   15.302786] nouveau  [     PFB][0000:01:00.0] RAM type: DDR3
[   15.302788] nouveau  [     PFB][0000:01:00.0] RAM size: 512 MiB
[   15.302790] nouveau  [     PFB][0000:01:00.0]    ZCOMP: 0 tags
[   15.326749] nouveau  [  PTHERM][0000:01:00.0] FAN control: none / external
[   15.326754] nouveau  [  PTHERM][0000:01:00.0] fan management: disabled
[   15.326758] nouveau  [  PTHERM][0000:01:00.0] internal sensor: yes
[   15.330051] [TTM] Zone  kernel: Available graphics memory: 4034974 kiB
[   15.330053] [TTM] Zone   dma32: Available graphics memory: 2097152 kiB
[   15.330054] [TTM] Initializing pool allocator
[   15.330057] [TTM] Initializing DMA pool allocator
[   15.330067] nouveau  [     DRM] VRAM: 512 MiB
[   15.330068] nouveau  [     DRM] GART: 1048576 MiB
[   15.330071] nouveau  [     DRM] TMDS table version 2.0
[   15.330072] nouveau  [     DRM] DCB version 4.0
[   15.330074] nouveau  [     DRM] DCB outp 00: 02010300 00000000
[   15.330075] nouveau  [     DRM] DCB conn 00: 00000400
[   15.330670] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   15.330671] [drm] No driver support for vblank timestamp query.
[   15.330761] nouveau  [     DRM] ACPI backlight interface available, not registering our own
[   15.330767] nouveau W[     DRM] voltage table 0x50 unknown
[   15.330922] nouveau  [     DRM] 2 available performance level(s)
[   15.330924] nouveau  [     DRM] 1: core 270MHz shader 540MHz memory 405MHz
[   15.330926] nouveau  [     DRM] 3: core 475MHz shader 950MHz memory 900MHz voltage 10mV
[   15.330928] nouveau  [     DRM] c: core 270MHz shader 540MHz memory 405MHz
[   15.336147] nouveau  [     DRM] MM: using COPY0 for buffer copies
[   15.376855] nouveau  [     DRM] allocated 1024x768 fb: 0x60000, bo ffff88024fbde000
[   15.410728] Console: switching to colour frame buffer device 128x48
[   15.411284] nouveau 0000:01:00.0: fb0: nouveaufb frame buffer device
[   15.411285] nouveau 0000:01:00.0: registered panic notifier
[   15.411288] [drm] Initialized nouveau 1.1.1 20120801 for 0000:01:00.0 on minor 0
[   15.411925] [drm] Memory usable by graphics device = 2048M
[   15.411929] i915 0000:00:02.0: setting latency timer to 64
[   15.432497] i915 0000:00:02.0: irq 46 for MSI/MSI-X
[   15.432505] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   15.432505] [drm] Driver supports precise vblank timestamp query.
[   15.432523] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Integer], ACPI requires [Package] (20130517/nsarguments-95)
[   15.432553] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Integer], ACPI requires [Package] (20130517/nsarguments-95)
[   15.432567] vga_switcheroo: enabled
[   15.432605] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=none
[   15.432607] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   15.477287] fbcon: inteldrmfb (fb1) is primary device
[   15.477288] fbcon: Remapping primary device, fb1, to tty 1-63
[   15.723419] usbcore: registered new interface driver uvcvideo
[   15.723420] USB Video Class driver (1.1.1)
[   16.485308] i915 0000:00:02.0: fb1: inteldrmfb frame buffer device
[   16.518865] init: failsafe main process (594) killed by TERM signal
[   16.738837] [Firmware Bug]: ACPI(PEGP) defines _DOD but not _DOS
[   16.858976] [drm] Enabling RC6 states: RC6 on, RC6p on, RC6pp off
[   17.346573] acpi device:39: registered as cooling_device9
[   17.346694] ACPI: Video Device [PEGP] (multi-head: yes  rom: yes  post: no)
[   17.346749] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:37/LNXVIDEO:00/input/input7
[   17.594412] acpi device:45: registered as cooling_device10
[   17.594566] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   17.594613] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:01/input/input8
[   17.594726] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 1
[   17.594871] snd_hda_intel 0000:00:1b.0: irq 47 for MSI/MSI-X
[   17.634543] mute LED gpio 1 polarity 0
[   17.634728] autoconfig: line_outs=1 (0xd/0x0/0x0/0x0/0x0) type:speaker
[   17.634729]    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   17.634730]    hp_outs=1 (0xb/0x0/0x0/0x0/0x0)
[   17.634731]    mono: mono_out=0x0
[   17.634731]    inputs:
[   17.634732]      Internal Mic=0x11
[   17.634733]      Mic=0xa
[   17.683263] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   17.683316] input: HDA Intel PCH Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   17.683355] input: HDA Intel PCH Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   19.523979] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   19.719245] r8169 0000:0b:00.0 eth0: link down
[   19.719271] r8169 0000:0b:00.0 eth0: link down
[   19.719294] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   19.719555] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   20.243681] audit_printk_skb: 33 callbacks suppressed
[   20.243684] type=1400 audit(1397589983.211:23): apparmor="STATUS" operation="profile_replace" parent=877 profile="unconfined" name="/sbin/dhclient" pid=885 comm="apparmor_parser"
[   20.243689] type=1400 audit(1397589983.211:24): apparmor="STATUS" operation="profile_replace" parent=877 profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=885 comm="apparmor_parser"
[   20.243692] type=1400 audit(1397589983.211:25): apparmor="STATUS" operation="profile_replace" parent=877 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=885 comm="apparmor_parser"
[   20.244076] type=1400 audit(1397589983.211:26): apparmor="STATUS" operation="profile_replace" parent=877 profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=885 comm="apparmor_parser"
[   20.244079] type=1400 audit(1397589983.211:27): apparmor="STATUS" operation="profile_replace" parent=877 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=885 comm="apparmor_parser"
[   20.244264] type=1400 audit(1397589983.211:28): apparmor="STATUS" operation="profile_replace" parent=877 profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=889 comm="apparmor_parser"
[   20.244269] type=1400 audit(1397589983.211:29): apparmor="STATUS" operation="profile_replace" parent=877 profile="unconfined" name="/usr/sbin/cupsd" pid=889 comm="apparmor_parser"
[   20.244290] type=1400 audit(1397589983.211:30): apparmor="STATUS" operation="profile_replace" parent=877 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=885 comm="apparmor_parser"
[   20.244703] type=1400 audit(1397589983.211:31): apparmor="STATUS" operation="profile_replace" parent=877 profile="unconfined" name="/usr/sbin/cupsd" pid=889 comm="apparmor_parser"
[   20.302749] type=1400 audit(1397589983.271:32): apparmor="STATUS" operation="profile_load" parent=877 profile="unconfined" name="/usr/sbin/tcpdump" pid=891 comm="apparmor_parser"
[   22.097948] r8169 0000:0b:00.0 eth0: link up
[   22.097956] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready

```

lsmod:
```

Module                  Size  Used by
snd_hda_codec_hdmi     41154  1 
snd_hda_codec_idt      50341  1 
x86_pkg_temp_thermal    14162  0 
intel_powerclamp       14705  0 
coretemp               13435  0 
kvm_intel             138567  0 
kvm                   431754  1 kvm_intel
crct10dif_pclmul       14289  0 
crc32_pclmul           13113  0 
ghash_clmulni_intel    13259  0 
aesni_intel            55624  0 
aes_x86_64             17131  1 aesni_intel
lrw                    13286  1 aesni_intel
gf128mul               14951  1 lrw
uvcvideo               80885  0 
snd_hda_intel          52267  3 
glue_helper            13990  1 aesni_intel
arc4                   12608  2 
ablk_helper            13597  1 aesni_intel
snd_hda_codec         188738  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
joydev                 17377  0 
cryptd                 20359  3 ghash_clmulni_intel,aesni_intel,ablk_helper
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
rt2800pci              18719  0 
videobuf2_core         40499  1 uvcvideo
rt2800lib              79992  1 rt2800pci
snd_pcm               102033  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
videodev              133509  2 uvcvideo,videobuf2_core
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
hp_wmi                 14062  0 
rfcomm                 69130  0 
sparse_keymap          13948  1 hp_wmi
snd_seq_midi           13324  0 
rt2x00pci              13287  1 rt2800pci
parport_pc             32701  0 
ppdev                  17671  0 
bnep                   19704  2 
rt2x00mmio             13603  1 rt2800pci
i915                  661339  3 
rt2x00lib              55362  4 rt2x00pci,rt2800lib,rt2800pci,rt2x00mmio
bluetooth             372041  10 bnep,rfcomm
mac80211              597268  3 rt2x00lib,rt2x00pci,rt2800lib
nouveau               943749  1 
mxm_wmi                13021  1 nouveau
snd_seq_midi_event     14899  1 snd_seq_midi
video                  19318  2 i915,nouveau
cfg80211              480503  2 mac80211,rt2x00lib
snd_rawmidi            30095  1 snd_seq_midi
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
rtsx_pci_ms            18151  0 
memstick               16760  1 rtsx_pci_ms
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
ttm                    84169  1 nouveau
mei_me                 18421  0 
eeprom_93cx6           13344  1 rt2800pci
snd_timer              29433  2 snd_pcm,snd_seq
mei                    77782  1 mei_me
drm_kms_helper         52710  2 i915,nouveau
snd                    69141  17 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
drm                   297056  7 ttm,i915,drm_kms_helper,nouveau
psmouse                97655  0 
hp_accel               26012  0 
crc_ccitt              12707  1 rt2800lib
i2c_algo_bit           13413  2 i915,nouveau
lis3lv02d              20156  1 hp_accel
lpc_ich                21080  0 
input_polldev          13896  1 lis3lv02d
soundcore              12680  1 snd
wmi                    19070  3 hp_wmi,mxm_wmi,nouveau
mac_hid                13205  0 
serio_raw              13413  0 
microcode              23656  0 
lp                     17759  0 
parport                42299  3 lp,ppdev,parport_pc
rtsx_pci_sdmmc         23527  0 
r8169                  67581  0 
mii                    13934  1 r8169
ahci                   25819  2 
libahci                32009  1 ahci
rtsx_pci               45546  2 rtsx_pci_ms,rtsx_pci_sdmmc

```

I'm pretty much out of ideas, and I would really like to get Linux working again. Any help is much appreciated.

---

### Post by praseodym on 2014-04-15
BIOS-Reset? Or is it an (U)EFI? Any settings there?

---

### Post by xtjacob on 2014-04-15
The computer has a UEFI motherboard, but I am running it in Legacy mode. I don't see any settings relating to wireless in the BIOS settings.

---

### Post by xtjacob on 2014-04-15
So I just tried running showkey -k to see if it's even picking the key up and it appears not. I didn't get a response from showkey when I hit the wireless toggle key, but I got a response from the other keys...

---

### Post by xtjacob on 2014-04-19
Well, I finally managed to get it working. What I had to do was add acpi_osi='Windows 2012' to get it to recognize my keys correctly, then blacklist hp_wmi to get the hardblock removed. However, I have to reenable the wireless card everytime I reboot, and I'm having some pretty bad packet loss...

---

### Post by praseodym on 2014-04-19
The driver should run pretty good since 13.10. Lets check
```

cat /etc/resolv.conf
route -n
iwlist chan
iwconfig
sudo iwlist scan
```

---

### Post by xtjacob on 2014-04-19
cat /etc/resolv.conf:
```

# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1

```

route -n:
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

```

iwlist chan
```

eth0      no frequency information.

lo        no frequency information.

wlan0     14 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 14 : 2.484 GHz
          Current Frequency:2.412 GHz (Channel 1)

```

iwconfig:
```

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"-------"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: xx:xx:xx:xx:xx:xx   
          Bit Rate=15 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=33/70  Signal level=-77 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:97  Invalid misc:108   Missed beacon:0

```

sudo iwlist scan:
```

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: xx:xx:xx:xx:xx:xx
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:on
                    ESSID:"--------"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000003f26d729
                    Extra: Last beacon: 128ms ago
                    IE: Unknown: 0006427974654D65
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AEE181BFFFF000001000000000000000000000000000000000000
                    IE: Unknown: 3D16010D0400000000000000000000000000000000000000
                    IE: Unknown: DD090010180206F0050000
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
          Cell 02 - Address: 00:19:5B:06:12:90
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:off
                    ESSID:"\x00\x00\x00\x00\x00"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000028f70b98181
                    Extra: Last beacon: 2348ms ago
                    IE: Unknown: 00050000000000
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32041224606C
                    IE: Unknown: DD0600032F010001

```

---

### Post by praseodym on 2014-04-20
Check these nameservers:
```

echo -e "nameserver 8.8.8.8\nnameserver 8.8.4.4" | sudo tee /etc/resolv.conf
sudo service network-manager restart
```
Can you change the encryption to WPA2-AES only instead of mixed WPA/WPA2?

---

### Post by xtjacob on 2014-04-20
Well it appears I'm still getting a little packet loss, but the internet is not throttling down everytime it's under a load, and is much faster. Thank you!

---

