---
title: "*-network UNCLAIMED"
date: 2014-06-02
forum: Networking &amp; Wireless
---

### Post by pablo21 on 2014-06-02
Hello, I just installed ubuntu on my desktop pc and the wireless isnt working, heres my info:

lshw -C network

shows:
```

*-network NO RECLAMADO
       descripción: Ethernet controller
       producto: 88w8335 [Libertas] 802.11b/g Wireless
       fabricante: Marvell Technology Group Ltd.
       id físico: 6
       información del bus: pci@0000:04:06.0
       versión: 43
       anchura: 32 bits
       reloj: 66MHz
       capacidades: bus_master cap_list
       configuración: latency=32
       recursos: memoria:fe910000-fe91ffff memoria:fe900000-fe90ffff

```

lspci -nn shows this to be my wireless card
```
04:06.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless [11ab:1faa] (rev 43)

```

sudo lspci -nn | grep 0280

show nothing

and iwconfig shows
```

lo        no wireless extensions.

eth0      no wireless extensions.

```


my wireless card is a NEXXT. serial number NW122NXT12, tried installing the drivers with ndiswrapper but nothing helped.

---

### Post by chili555 on 2014-06-02
I think ndiswrapper is the only possibly working driver. Let's see where you are:```
ndiswrapper -l
dmesg | grep ndis
```Did you use Windows XP files? Hint, hint!!

---

### Post by pablo21 on 2014-06-02
ndiswrapper -l
```

netmw125 : driver installed
    device (11AB:1FAA) present
netmw13b : driver installed
    device (11AB:1FAA) present
```

netmw125 supports xp and when it didn't work I tried with netmw13b, neither of them worked. thenk you very much for helping
[h=2]Inf file Marvell_8335a_3.2.3.3/driver/inf/WinXP_2K/netmw125.inf Supported Drivers[/h]                      
                     
[LIST]
[*] **Provider:**[Marvell]("http://www.driversguru.com/providers-Marvell")                            								        **Model Name :**[ 802.11g/b Wireless LAN Client Adapter]("http://www.driversguru.com/driverdownload/802.11g/b%20Wireless%20LAN%20Client%20Adapter")
[*]** OS:** Windows  7, Vista, Windows 8, XP, XP 64 bit, Windows 2003, Windows 2003 64 bit, Windows  2008
[*] ** Hardware ID:** [PCI\VEN_11AB&DEV_1FAB]("http://www.driversguru.com/hardwareid-PCI---VEN_11AB-_-DEV_1FAB")
[/LIST]

---

### Post by chili555 on 2014-06-02
And what about the dmesg?

---

### Post by pablo21 on 2014-06-02
```
[    0.476936] pcieport 0000:00:1c.0: irq 41 for MSI/MSI-X
[    0.477072] pcieport 0000:00:1c.1: irq 42 for MSI/MSI-X
[    0.477163] pcieport 0000:00:01.0: Signaling PME through PCIe PME interrupt
[    0.477166] pcie_pme 0000:00:01.0:pcie01: service driver pcie_pme loaded
[    0.477183] pcieport 0000:00:1c.0: Signaling PME through PCIe PME interrupt
[    0.477187] pcie_pme 0000:00:1c.0:pcie01: service driver pcie_pme loaded
[    0.477204] pcieport 0000:00:1c.1: Signaling PME through PCIe PME interrupt
[    0.477206] pci 0000:03:00.0: Signaling PME through PCIe PME interrupt
[    0.477209] pcie_pme 0000:00:1c.1:pcie01: service driver pcie_pme loaded
[    0.477224] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.477255] pciehp 0000:00:1c.0:pcie04: HPC vendor_id 8086 device_id 27d0 ss_vid 8086 ss_did 27d0
[    0.477280] pciehp 0000:00:1c.0:pcie04: service driver pciehp loaded
[    0.477290] pciehp 0000:00:1c.1:pcie04: HPC vendor_id 8086 device_id 27d2 ss_vid 8086 ss_did 27d2
[    0.477311] pciehp 0000:00:1c.1:pcie04: service driver pciehp loaded
[    0.477315] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.477357] vesafb: mode is 1024x768x32, linelength=4096, pages=0
[    0.477358] vesafb: scrolling: redraw
[    0.477360] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    0.477560] vesafb: framebuffer at 0xd0000000, mapped to 0xf8480000, using 3072k, total 3072k
[    0.501451] Console: switching to colour frame buffer device 128x48
[    0.525266] fb0: VESA VGA frame buffer device
[    0.525285] intel_idle: does not run on family 6 model 23
[    0.525291] ipmi message handler version 39.2
[    0.525348] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input0
[    0.525354] ACPI: Sleep Button [SLPB]
[    0.525387] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.525389] ACPI: Power Button [PWRB]
[    0.525425] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.525427] ACPI: Power Button [PWRF]
[    0.525562] GHES: HEST is not enabled!
[    0.525591] isapnp: Scanning for PnP cards...
[    0.532040] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.552398] 00:05: ttyS0 at I/O 0x3f8 (irq = 4, base_baud = 115200) is a 16550A
[    0.553518] Linux agpgart interface v0.103
[    0.553592] agpgart-intel 0000:00:00.0: Intel G33 Chipset
[    0.553638] agpgart-intel 0000:00:00.0: detected gtt size: 524288K total, 262144K mappable
[    0.554306] agpgart-intel 0000:00:00.0: detected 8192K stolen memory
[    0.554404] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[    0.555679] brd: module loaded
[    0.556345] loop: module loaded
[    0.556463] ata_piix 0000:00:1f.1: version 2.13
[    0.557443] scsi0 : ata_piix
[    0.557498] scsi1 : ata_piix
[    0.557528] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xe0f0 irq 14
[    0.557530] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xe0f8 irq 15
[    0.557594] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    0.557953] ata2: port disabled--ignoring
[    0.557965] scsi2 : ata_piix
[    0.558012] scsi3 : ata_piix
[    0.558044] ata3: SATA max UDMA/133 cmd 0xe0e0 ctl 0xe0d0 bmdma 0xe0a0 irq 19
[    0.558046] ata4: SATA max UDMA/133 cmd 0xe0c0 ctl 0xe0b0 bmdma 0xe0a8 irq 19
[    0.558330] libphy: Fixed MDIO Bus: probed
[    0.558427] tun: Universal TUN/TAP device driver, 1.6
[    0.558429] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.558470] PPP generic driver version 2.4.2
[    0.558504] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.558508] ehci-pci: EHCI PCI platform driver
[    0.558591] ehci-pci 0000:00:1d.7: EHCI Host Controller
[    0.558596] ehci-pci 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.558608] ehci-pci 0000:00:1d.7: debug port 1
[    0.562497] ehci-pci 0000:00:1d.7: cache line size of 64 is not supported
[    0.562511] ehci-pci 0000:00:1d.7: irq 23, io mem 0xfeb84000
[    0.572015] ehci-pci 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.572080] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    0.572082] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.572084] usb usb1: Product: EHCI Host Controller
[    0.572086] usb usb1: Manufacturer: Linux 3.13.0-24-generic ehci_hcd
[    0.572088] usb usb1: SerialNumber: 0000:00:1d.7
[    0.572172] hub 1-0:1.0: USB hub found
[    0.572181] hub 1-0:1.0: 8 ports detected
[    0.572338] ehci-platform: EHCI generic platform driver
[    0.572347] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.572349] ohci-pci: OHCI PCI platform driver
[    0.572358] ohci-platform: OHCI generic platform driver
[    0.572365] uhci_hcd: USB Universal Host Controller Interface driver
[    0.572432] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.572436] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.572456] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000e080
[    0.572501] usb usb2: New USB device found, idVendor=1d6b, idProduct=0001
[    0.572503] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.572505] usb usb2: Product: UHCI Host Controller
[    0.572507] usb usb2: Manufacturer: Linux 3.13.0-24-generic uhci_hcd
[    0.572509] usb usb2: SerialNumber: 0000:00:1d.0
[    0.572584] hub 2-0:1.0: USB hub found
[    0.572591] hub 2-0:1.0: 2 ports detected
[    0.572723] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.572728] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.572748] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000e060
[    0.572792] usb usb3: New USB device found, idVendor=1d6b, idProduct=0001
[    0.572794] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.572796] usb usb3: Product: UHCI Host Controller
[    0.572798] usb usb3: Manufacturer: Linux 3.13.0-24-generic uhci_hcd
[    0.572799] usb usb3: SerialNumber: 0000:00:1d.1
[    0.572875] hub 3-0:1.0: USB hub found
[    0.572882] hub 3-0:1.0: 2 ports detected
[    0.573011] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.573016] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.573044] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000e040
[    0.573087] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
[    0.573090] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.573092] usb usb4: Product: UHCI Host Controller
[    0.573093] usb usb4: Manufacturer: Linux 3.13.0-24-generic uhci_hcd
[    0.573095] usb usb4: SerialNumber: 0000:00:1d.2
[    0.573171] hub 4-0:1.0: USB hub found
[    0.573178] hub 4-0:1.0: 2 ports detected
[    0.573311] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    0.573315] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    0.573343] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000e020
[    0.573388] usb usb5: New USB device found, idVendor=1d6b, idProduct=0001
[    0.573390] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.573392] usb usb5: Product: UHCI Host Controller
[    0.573394] usb usb5: Manufacturer: Linux 3.13.0-24-generic uhci_hcd
[    0.573396] usb usb5: SerialNumber: 0000:00:1d.3
[    0.573472] hub 5-0:1.0: USB hub found
[    0.573479] hub 5-0:1.0: 2 ports detected
[    0.573609] i8042: PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    0.573611] i8042: PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    0.574209] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.574287] mousedev: PS/2 mouse device common for all mice
[    0.574407] rtc_cmos 00:07: RTC can wake from S4
[    0.574504] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
[    0.574526] rtc_cmos 00:07: alarms up to one year, y3k, 114 bytes nvram, hpet irqs
[    0.574584] device-mapper: uevent: version 1.0.3
[    0.574633] device-mapper: ioctl: 4.27.0-ioctl (2013-10-30) initialised: dm-devel@redhat.com
[    0.574650] platform eisa.0: Probing EISA bus 0
[    0.574652] platform eisa.0: EISA: Cannot allocate resource for mainboard
[    0.574655] platform eisa.0: Cannot allocate resource for EISA slot 1
[    0.574657] platform eisa.0: Cannot allocate resource for EISA slot 2
[    0.574658] platform eisa.0: Cannot allocate resource for EISA slot 3
[    0.574660] platform eisa.0: Cannot allocate resource for EISA slot 4
[    0.574662] platform eisa.0: Cannot allocate resource for EISA slot 5
[    0.574664] platform eisa.0: Cannot allocate resource for EISA slot 6
[    0.574666] platform eisa.0: Cannot allocate resource for EISA slot 7
[    0.574668] platform eisa.0: Cannot allocate resource for EISA slot 8
[    0.574670] platform eisa.0: EISA: Detected 0 cards
[    0.574676] cpufreq-nforce2: No nForce2 chipset.
[    0.574679] ledtrig-cpu: registered to indicate activity on CPUs
[    0.574800] TCP: cubic registered
[    0.574889] NET: Registered protocol family 10
[    0.575068] NET: Registered protocol family 17
[    0.575076] Key type dns_resolver registered
[    0.575216] Using IPI No-Shortcut mode
[    0.575278] Loading compiled-in X.509 certificates
[    0.578356] Loaded X.509 cert 'Magrathea: Glacier signing key: 5682f337b8a0a17eef58c6ac5e9a85712c9208df'
[    0.578368] registered taskstats version 1
[    0.584782] Key type trusted registered
[    0.600793] Key type encrypted registered
[    0.604269] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    0.616773] AppArmor: AppArmor sha1 policy hashing enabled
[    0.616776] IMA: No TPM chip found, activating TPM-bypass!
[    0.616987] regulator-dummy: disabling
[    0.617020]   Magic number: 2:124:139
[    0.617039] block ram4: hash matches
[    0.617067] acpi device:10: hash matches
[    0.617097] rtc_cmos 00:07: setting system clock to 2014-06-02 18:06:12 UTC (1401732372)
[    0.617144] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.617146] EDD information not available.
[    0.617192] PM: Hibernation image not present or could not be loaded.
[    0.716279] ata4.01: NODEV after polling detection
[    0.720277] ata1.00: failed to IDENTIFY (INIT_DEV_PARAMS failed, err_mask=0x80)
[    0.724268] ata3.00: ATA-7: SAMSUNG HD162GJ, 1AC01113, max UDMA7
[    0.724270] ata3.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    0.724328] ata4.00: ATAPI: HL-DT-ST DVDRAM GH22NS40, NL00, max UDMA/100
[    0.732288] ata3.00: configured for UDMA/133
[    0.740111] ata4.00: configured for UDMA/100
[    0.836092] isapnp: No Plug & Play device found
[    0.940034] usb 1-6: new high-speed USB device number 3 using ehci-pci
[    1.206054] usb 1-6: New USB device found, idVendor=0718, idProduct=0700
[    1.206058] usb 1-6: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    1.206062] usb 1-6: Product: Mobile
[    1.206065] usb 1-6: Manufacturer: Imation
[    1.206068] usb 1-6: SerialNumber: 561111300917003
[    1.316030] usb 1-8: new high-speed USB device number 4 using ehci-pci
[    1.452016] tsc: Refined TSC clocksource calibration: 2799.942 MHz
[    2.163930] usb 1-8: New USB device found, idVendor=054c, idProduct=01bd
[    2.163935] usb 1-8: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    2.163938] usb 1-8: Product: USB 2.0 MultiCard R/W
[    2.163941] usb 1-8: Manufacturer: Sony
[    2.163944] usb 1-8: SerialNumber: 120000011197
[    2.404022] usb 2-2: new low-speed USB device number 2 using uhci_hcd
[    2.452061] Switched to clocksource tsc
[    2.577486] usb 2-2: New USB device found, idVendor=0458, idProduct=003a
[    2.577490] usb 2-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    2.577494] usb 2-2: Product: Optical Mouse
[    2.577497] usb 2-2: Manufacturer: Genius
[    5.876287] ata1.00: failed to IDENTIFY (INIT_DEV_PARAMS failed, err_mask=0x80)
[   11.032284] ata1.00: failed to IDENTIFY (INIT_DEV_PARAMS failed, err_mask=0x80)
[   16.180219] scsi 2:0:0:0: Direct-Access     ATA      SAMSUNG HD162GJ  1AC0 PQ: 0 ANSI: 5
[   16.180310] sd 2:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[   16.180329] sd 2:0:0:0: Attached scsi generic sg0 type 0
[   16.180352] sd 2:0:0:0: [sda] Write Protect is off
[   16.180355] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   16.180465] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   16.183740] scsi 3:0:0:0: CD-ROM            HL-DT-ST DVDRAM GH22NS40  NL00 PQ: 0 ANSI: 5
[   16.189577] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[   16.189580] cdrom: Uniform CD-ROM driver Revision: 3.20
[   16.189700] sr 3:0:0:0: Attached scsi CD-ROM sr0
[   16.189773] sr 3:0:0:0: Attached scsi generic sg1 type 5
[   16.209551]  sda: sda1 sda2 < sda5 >
[   16.209853] sd 2:0:0:0: [sda] Attached SCSI disk
[   16.210142] Freeing unused kernel memory: 872K (c19ae000 - c1a88000)
[   16.210172] Write protecting the kernel text: 6512k
[   16.210247] Write protecting the kernel read-only data: 2756k
[   16.210248] NX-protecting the kernel data: 5776k
[   16.219849] systemd-udevd[106]: starting version 204
[   16.245858] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[   16.246078] r8169 0000:03:00.0: irq 43 for MSI/MSI-X
[   16.246239] r8169 0000:03:00.0 eth0: RTL8168b/8111b at 0xf840e000, 00:1c:c0:bb:93:de, XID 98500000 IRQ 43
[   16.246241] r8169 0000:03:00.0 eth0: jumbo features [frames: 4080 bytes, tx checksumming: ko]
[   16.253585] usb-storage 1-6:1.0: USB Mass Storage device detected
[   16.253628] scsi4 : usb-storage 1-6:1.0
[   16.253690] usb-storage 1-8:1.0: USB Mass Storage device detected
[   16.253719] scsi5 : usb-storage 1-8:1.0
[   16.253768] usbcore: registered new interface driver usb-storage
[   16.259337] hidraw: raw HID events driver (C) Jiri Kosina
[   16.274179] FDC 0 is a post-1991 82077
[   16.278922] usbcore: registered new interface driver usbhid
[   16.278925] usbhid: USB HID core driver
[   16.294058] input: Genius Optical Mouse as /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0/input/input4
[   16.294156] hid-generic 0003:0458:003A.0001: input,hidraw0: USB HID v1.10 Mouse [Genius Optical Mouse] on usb-0000:00:1d.0-2/input0
[   16.506487] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[   17.029137] random: init urandom read with 85 bits of entropy available
[   17.324093] scsi 5:0:0:0: Direct-Access     Sony     Card_R/W     -CF 1.10 PQ: 0 ANSI: 0 CCS
[   17.395972] scsi 5:0:0:1: Direct-Access     Sony     Card_R/W     -SD 1.10 PQ: 0 ANSI: 0 CCS
[   17.414588] scsi 4:0:0:0: Direct-Access     Imation  Mobile           1100 PQ: 0 ANSI: 0 CCS
[   17.467843] scsi 5:0:0:2: Direct-Access     Sony     Card_R/W     -MS 1.10 PQ: 0 ANSI: 0 CCS
[   17.468071] sd 5:0:0:0: Attached scsi generic sg2 type 0
[   17.468196] sd 5:0:0:1: Attached scsi generic sg3 type 0
[   17.468318] sd 5:0:0:2: Attached scsi generic sg4 type 0
[   17.468449] sd 4:0:0:0: Attached scsi generic sg5 type 0
[   17.469074] sd 4:0:0:0: [sde] 7829504 512-byte logical blocks: (4.00 GB/3.73 GiB)
[   17.469818] sd 4:0:0:0: [sde] Write Protect is off
[   17.469823] sd 4:0:0:0: [sde] Mode Sense: 43 00 00 00
[   17.470568] sd 4:0:0:0: [sde] No Caching mode page found
[   17.470572] sd 4:0:0:0: [sde] Assuming drive cache: write through
[   17.473318] sd 5:0:0:0: [sdb] Attached SCSI removable disk
[   17.473691] sd 4:0:0:0: [sde] No Caching mode page found
[   17.473696] sd 4:0:0:0: [sde] Assuming drive cache: write through
[   17.474064] sd 5:0:0:1: [sdc] Attached SCSI removable disk
[   17.474720]  sde: sde1
[   17.474827] sd 5:0:0:2: [sdd] Attached SCSI removable disk
[   17.477190] sd 4:0:0:0: [sde] No Caching mode page found
[   17.477194] sd 4:0:0:0: [sde] Assuming drive cache: write through
[   17.477198] sd 4:0:0:0: [sde] Attached SCSI removable disk
[   17.749823] random: nonblocking pool is initialized
[   18.532287] Adding 1035260k swap on /dev/sda5.  Priority:-1 extents:1 across:1035260k FS
[   19.164939] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   19.334530] systemd-udevd[275]: starting version 204
[   20.210855] lp: driver loaded but no devices found
[   20.700417] cfg80211: Calling CRDA to update world regulatory domain
[   21.135390] ppdev: user-space parallel port driver
[   21.734048] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   22.294629] intel_rng: Firmware space is locked read-only. If you can't or
[   22.294629] intel_rng: don't want to disable this in firmware setup, and if
[   22.294629] intel_rng: you are certain that your system has a functional
[   22.294629] intel_rng: RNG, try using the 'no_fwh_detect' option.
[   22.525998] leds_ss4200: no LED devices found
[   22.945422] [drm] Initialized drm 1.1.0 20060810
[   22.946396] Linux video capture interface: v2.00
[   23.311071] gpio_ich: GPIO from 206 to 255 on gpio_ich
[   23.443894] [drm] Memory usable by graphics device = 512M
[   23.443898] checking generic (d0000000 300000) vs hw (d0000000 10000000)
[   23.443900] fb: conflicting fb hw usage inteldrmfb vs VESA VGA - removing generic driver
[   23.443939] Console: switching to colour dummy device 80x25
[   23.468070] i915 0000:00:02.0: irq 44 for MSI/MSI-X
[   23.468084] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[   23.468087] [drm] Driver supports precise vblank timestamp query.
[   23.468151] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   23.469321] [drm] initialized overlay support
[   23.560992] fbcon: inteldrmfb (fb0) is primary device
[   23.628092] Console: switching to colour frame buffer device 128x48
[   23.631457] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[   23.631459] i915 0000:00:02.0: registered panic notifier
[   23.631522] ACPI Exception: AE_NOT_FOUND, Evaluating _DOD (20131115/video-1246)
[   23.631526] ACPI: Video Device [GFX0] (multi-head: no  rom: yes  post: no)
[   23.631577] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input5
[   23.631827] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   23.676291] snd_hda_intel 0000:00:1b.0: irq 45 for MSI/MSI-X
[   23.778967] saa7130/34: v4l2 driver version 0, 2, 17 loaded
[   23.779077] saa7133[0]: found at 0000:04:05.0, rev: 16, irq: 20, latency: 32, mmio: 0xfe920000
[   23.779081] saa7133[0]: subsystem: 1019:4cb5, board: Elitegroup ECS TVP3XP FM1236 Tuner Card (NTSC,FM) [card=31,autodetected]
[   23.779094] saa7133[0]: board init: gpio is 2
[   23.874653] hda_codec: ALC888: SKU not ready 0x411111f0
[   23.874947] autoconfig: line_outs=1 (0x14/0x0/0x0/0x0/0x0) type:line
[   23.874949]    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   23.874950]    hp_outs=1 (0x1b/0x0/0x0/0x0/0x0)
[   23.874951]    mono: mono_out=0x0
[   23.874953]    dig-out=0x1e/0x0
[   23.874954]    inputs:
[   23.874956]      Front Mic=0x19
[   23.874957]      Rear Mic=0x18
[   23.874958]      Line=0x1a
[   23.874960] realtek: No valid SSID, checking pincfg 0x411111f0 for NID 0x1d
[   23.874961] realtek: Enable default setup for auto mode as fallback
[   23.884935] input: HDA Intel Line Out as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   23.885095] input: HDA Intel Line as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   23.885245] input: HDA Intel Rear Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[   24.089203] Registered IR keymap rc-eztv
[   24.089509] input: saa7134 IR (Elitegroup ECS TVP3 as /devices/pci0000:00/0000:00:1e.0/0000:04:05.0/rc/rc0/input6
[   24.091006] rc0: saa7134 IR (Elitegroup ECS TVP3 as /devices/pci0000:00/0000:00:1e.0/0000:04:05.0/rc/rc0
[   24.240130] saa7133[0]: i2c eeprom 00: 19 10 b5 4c ff ff ff ff ff ff ff ff ff ff ff ff
[   24.240141] saa7133[0]: i2c eeprom 10: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   24.240150] saa7133[0]: i2c eeprom 20: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   24.240158] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   24.240166] saa7133[0]: i2c eeprom 40: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   24.240174] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   24.240183] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   24.240191] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   24.240199] saa7133[0]: i2c eeprom 80: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   24.240207] saa7133[0]: i2c eeprom 90: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   24.240216] saa7133[0]: i2c eeprom a0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   24.240224] saa7133[0]: i2c eeprom b0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   24.240232] saa7133[0]: i2c eeprom c0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   24.240240] saa7133[0]: i2c eeprom d0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   24.240249] saa7133[0]: i2c eeprom e0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   24.240257] saa7133[0]: i2c eeprom f0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   24.504025] All bytes are equal. It is not a TEA5767
[   24.504031] tuner 6-0060: Tuner -1 found with type(s) Radio TV.
[   24.760024] tuner-simple 6-0060: creating new instance
[   24.760030] tuner-simple 6-0060: type set to 2 (Philips NTSC (FI1236,FM1236 and compatibles))
[   24.784347] saa7133[0]: registered device video0 [v4l2]
[   24.784405] saa7133[0]: registered device vbi0
[   24.784469] saa7133[0]: registered device radio0
[   24.851335] saa7134 ALSA driver for DMA sound loaded
[   24.851363] saa7133[0]/alsa: saa7133[0] at 0xfe920000 irq 20 registered as card -2
[   24.931550] cfg80211: World regulatory domain updated:
[   24.931554] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   24.931556] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   24.931558] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   24.931559] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   24.931561] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   24.931563] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   25.649505] type=1400 audit(1401732397.530:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=370 comm="apparmor_parser"
[   25.649511] type=1400 audit(1401732397.530:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=370 comm="apparmor_parser"
[   25.649516] type=1400 audit(1401732397.530:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=370 comm="apparmor_parser"
[   25.649526] type=1400 audit(1401732397.530:5): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=371 comm="apparmor_parser"
[   25.649532] type=1400 audit(1401732397.530:6): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=371 comm="apparmor_parser"
[   25.649536] type=1400 audit(1401732397.530:7): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=371 comm="apparmor_parser"
[   25.649947] type=1400 audit(1401732397.530:8): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=370 comm="apparmor_parser"
[   25.649951] type=1400 audit(1401732397.530:9): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=370 comm="apparmor_parser"
[   25.649966] type=1400 audit(1401732397.530:10): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=371 comm="apparmor_parser"
[   25.649971] type=1400 audit(1401732397.530:11): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=371 comm="apparmor_parser"
[   26.789202] init: failsafe main process (553) killed by TERM signal
[   30.232991] Bluetooth: Core ver 2.17
[   30.233010] NET: Registered protocol family 31
[   30.233012] Bluetooth: HCI device and connection manager initialized
[   30.233024] Bluetooth: HCI socket layer initialized
[   30.233027] Bluetooth: L2CAP socket layer initialized
[   30.233032] Bluetooth: SCO socket layer initialized
[   30.414240] Bluetooth: RFCOMM TTY layer initialized
[   30.414251] Bluetooth: RFCOMM socket layer initialized
[   30.414256] Bluetooth: RFCOMM ver 1.11
[   30.508053] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   30.508057] Bluetooth: BNEP filters: protocol multicast
[   30.508066] Bluetooth: BNEP socket layer initialized
[   30.683794] init: cups main process (756) killed by HUP signal
[   30.683810] init: cups main process ended, respawning
[   36.873282] r8169 0000:03:00.0 eth0: link down
[   36.873331] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   36.873603] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   36.873908] r8169 0000:03:00.0 eth0: link down
[   37.198404] audit_printk_skb: 15 callbacks suppressed
[   37.198407] type=1400 audit(1401732409.078:17): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=838 comm="apparmor_parser"
[   37.198414] type=1400 audit(1401732409.078:18): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=838 comm="apparmor_parser"
[   37.198419] type=1400 audit(1401732409.078:19): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=838 comm="apparmor_parser"
[   37.198850] type=1400 audit(1401732409.078:20): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=838 comm="apparmor_parser"
[   37.198854] type=1400 audit(1401732409.078:21): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=838 comm="apparmor_parser"
[   37.199071] type=1400 audit(1401732409.078:22): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=838 comm="apparmor_parser"
[   37.649889] type=1400 audit(1401732409.530:23): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/lightdm/lightdm-guest-session" pid=837 comm="apparmor_parser"
[   37.649897] type=1400 audit(1401732409.530:24): apparmor="STATUS" operation="profile_load" profile="unconfined" name="chromium" pid=837 comm="apparmor_parser"
[   37.650158] type=1400 audit(1401732409.530:25): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="chromium" pid=837 comm="apparmor_parser"
[   37.900217] type=1400 audit(1401732409.782:26): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/telepathy/mission-control-5" pid=842 comm="apparmor_parser"
[   38.280135] init: samba-ad-dc main process (781) terminated with status 1
[   38.483013] r8169 0000:03:00.0 eth0: link up
[   38.483025] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   44.951383] init: plymouth-upstart-bridge main process ended, respawning
[   44.965258] init: plymouth-upstart-bridge main process ended, respawning
[   60.942676] audit_printk_skb: 123 callbacks suppressed
[   60.942680] type=1400 audit(1401732432.822:68): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=1865 comm="apparmor_parser"
[   60.942686] type=1400 audit(1401732432.822:69): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=1865 comm="apparmor_parser"
[   60.943116] type=1400 audit(1401732432.822:70): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=1865 comm="apparmor_parser"
[   62.107968] FAT-fs (sde1): Volume was not properly unmounted. Some data may be corrupt. Please run fsck.
[  826.785464] perf samples too long (2521 > 2500), lowering kernel.perf_event_max_sample_rate to 50000
[ 2458.761054] perf samples too long (5005 > 5000), lowering kernel.perf_event_max_sample_rate to 25000


```

---

### Post by chili555 on 2014-06-02
> [   24.931550] cfg80211: World regulatory domain updated:
[   24.931554] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   24.931556] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   24.931558] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   24.931559] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   24.931561] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   24.931563] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)We see some wireless activity, but none related to ndiswrapper. Weird! Are there any interesting errors or other clues here?```
sudo modprobe ndiswrapper
iwconfig
```We will probably need to remove one set of inf files after we figure out the problem.

---

### Post by pablo21 on 2014-06-02
Hey! as soon as i typed 
sudo modprobe ndiswrapper

it started searching for a wireless conection nad it's connected right now. Thank you very much for your help and time.

anyways; this is the result for iwconfig

```
wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   Sensitivity=-200 dBm  
          RTS thr=2346 B   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

lo        no wireless extensions.

eth0      no wireless extensions.
```

before this it used to show lo and eth0 only. again thank you very much

---

### Post by chili555 on 2014-06-02
Let's get ndiswrapper to load automatically, shall we?```
sudo -i
echo ndiswrapper  >>  /etc/modules
exit
```You should be all set.

---

### Post by pablo21 on 2014-06-02
thanks i also tried adding sudo modprobe ndiswrapper
on the rc.local file

I'll do it your way since it's from someone who knows more than me

---

### Post by alpha-command on 2014-12-09
> **chili555 said:**
> We see some wireless activity, but none related to ndiswrapper. Weird! Are there any interesting errors or other clues here?```
sudo modprobe ndiswrapper
iwconfig
```We will probably need to remove one set of inf files after we figure out the problem.

Hello, I know this thread is old but I am having the same problem with  the same device, I have followed steps to install drivers through ndiswrapper, but unlike Pablo21 using

```
sudo modprobe ndiswrapper
iwconfig
```

did not fix the problem for me...

Can you please have a look at the ouput of my dmesg here;

```
[    2.690815] hub 3-0:1.0: 2 ports detected
[    2.691030] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    2.693249] i8042: Detected active multiplexing controller, rev 1.1
[    2.694394] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.694404] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    2.738064] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    2.738100] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    2.738131] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    2.738293] mousedev: PS/2 mouse device common for all mice
[    2.738499] rtc_cmos 00:03: RTC can wake from S4
[    2.738711] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    2.738753] rtc_cmos 00:03: alarms up to one year, y3k, 242 bytes nvram
[    2.738866] device-mapper: uevent: version 1.0.3
[    2.738962] device-mapper: ioctl: 4.27.0-ioctl (2013-10-30) initialised: dm-devel@redhat.com
[    2.738993] platform eisa.0: Probing EISA bus 0
[    2.739004] platform eisa.0: Cannot allocate resource for EISA slot 1
[    2.739008] platform eisa.0: Cannot allocate resource for EISA slot 2
[    2.739015] platform eisa.0: Cannot allocate resource for EISA slot 4
[    2.739038] platform eisa.0: EISA: Detected 0 cards
[    2.739053] cpufreq-nforce2: No nForce2 chipset.
[    2.739059] ledtrig-cpu: registered to indicate activity on CPUs
[    2.739288] TCP: cubic registered
[    2.739441] NET: Registered protocol family 10
[    2.739755] NET: Registered protocol family 17
[    2.739775] Key type dns_resolver registered
[    2.740029] Using IPI No-Shortcut mode
[    2.740134] Loading compiled-in X.509 certificates
[    2.745759] Loaded X.509 cert 'Magrathea: Glacier signing key: 7231ad671e9d1af57bcbc00021a6ff374a791741'
[    2.745785] registered taskstats version 1
[    2.749001] Key type trusted registered
[    2.751523] Key type encrypted registered
[    2.754139] AppArmor: AppArmor sha1 policy hashing enabled
[    2.754147] IMA: No TPM chip found, activating TPM-bypass!
[    2.754547] regulator-dummy: disabling
[    2.754610]   Magic number: 10:505:512
[    2.754814] rtc_cmos 00:03: setting system clock to 2014-12-09 03:31:50 UTC (1418095910)
[    2.754936] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.754938] EDD information not available.
[    2.754995] PM: Hibernation image not present or could not be loaded.
[    2.929495] isapnp: No Plug & Play device found
[    2.930034] Freeing unused kernel memory: 876K (c19b9000 - c1a94000)
[    2.930101] Write protecting the kernel text: 6544k
[    2.930194] Write protecting the kernel read-only data: 2768k
[    2.930195] NX-protecting the kernel data: 5744k
[    2.950269] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    2.950711] systemd-udevd[91]: starting version 204
[    3.021423] sata_via 0000:00:0f.0: version 2.6
[    3.021576] sata_via 0000:00:0f.0: routed to hard irq line 10
[    3.028993] scsi0 : sata_via
[    3.031654] scsi1 : sata_via
[    3.031741] ata1: SATA max UDMA/133 cmd 0x4c70 ctl 0x4c64 bmdma 0x4c40 irq 21
[    3.031745] ata2: SATA max UDMA/133 cmd 0x4c68 ctl 0x4c60 bmdma 0x4c48 irq 21
[    3.031907] pata_via 0000:00:0f.1: version 0.3.4
[    3.033545] scsi2 : pata_via
[    3.040133] scsi3 : pata_via
[    3.040212] ata3: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x4c50 irq 14
[    3.040216] ata4: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x4c58 irq 15
[    3.097800] via_rhine: v1.10-LK1.5.1 2010-10-09 Written by Donald Becker
[    3.123762] via-rhine 0000:00:12.0 eth0: VIA Rhine II at 0xc9400400, 00:14:0b:36:1d:b2, IRQ 23
[    3.124619] via-rhine 0000:00:12.0 eth0: MII PHY found at address 1, status 0x7849 advertising 05e1 Link 0000
[    3.232169] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    3.396397] ata1.00: ATA-8: FUJITSU MHW2100BH, 00000012, max UDMA/100
[    3.396402] ata1.00: 195371568 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    3.412381] ata1.00: configured for UDMA/100
[    3.412593] scsi 0:0:0:0: Direct-Access     ATA      FUJITSU MHW2100B 0000 PQ: 0 ANSI: 5
[    3.412945] sd 0:0:0:0: [sda] 195371568 512-byte logical blocks: (100 GB/93.1 GiB)
[    3.413020] sd 0:0:0:0: [sda] Write Protect is off
[    3.413024] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.413058] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.413460] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    3.518880]  sda: sda1 sda2 < sda5 >
[    3.519455] sd 0:0:0:0: [sda] Attached SCSI disk
[    3.616028] ata2: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[    3.804382] ata4.00: ATAPI: TSSTcorp CDDVDW SN-S082H, SB00, max UDMA/33
[    3.836229] ata4.00: configured for UDMA/33
[    3.839241] scsi 3:0:0:0: CD-ROM            TSSTcorp CDDVDW SN-S082H  SB00 PQ: 0 ANSI: 5
[    3.845399] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    3.845404] cdrom: Uniform CD-ROM driver Revision: 3.20
[    3.845857] sr 3:0:0:0: Attached scsi CD-ROM sr0
[    3.846085] sr 3:0:0:0: Attached scsi generic sg1 type 5
[    4.120052] input: ALPS PS/2 Device as /devices/platform/i8042/serio4/input/input12
[    4.136487] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio4/input/input11
[    4.260930] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    5.461104] random: nonblocking pool is initialized
[   18.990644] Adding 914428k swap on /dev/sda5.  Priority:-1 extents:1 across:914428k FS
[   19.066434] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   19.262609] systemd-udevd[262]: starting version 204
[   19.605812] lp: driver loaded but no devices found
[   19.649925] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   19.662490] ppdev: user-space parallel port driver
[   19.794712] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   19.794763] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[   19.912252] acpi device:15: registered as cooling_device2
[   19.914323] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:13/LNXVIDEO:00/input/input13
[   20.004285] ndiswrapper: module verification failed: signature and/or  required key missing - tainting kernel
[   20.004325] Disabling lock debugging due to kernel taint
[   20.007079] ndiswrapper version 1.59 loaded (smp=yes, preempt=no)
[   20.023682] type=1400 audit(1418095927.762:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=322 comm="apparmor_parser"
[   20.023825] type=1400 audit(1418095927.762:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=322 comm="apparmor_parser"
[   20.023833] type=1400 audit(1418095927.762:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=322 comm="apparmor_parser"
[   20.029912] type=1400 audit(1418095927.770:5): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=322 comm="apparmor_parser"
[   20.029931] type=1400 audit(1418095927.770:6): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=322 comm="apparmor_parser"
[   20.030321] type=1400 audit(1418095927.770:7): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=322 comm="apparmor_parser"
[   20.465857] ndiswrapper: driver mrv8335x (3Com,05/19/2005,3.1.1.10) loaded
[   20.467017] ndiswrapper: using IRQ 18
[   20.594450] hda-intel 0000:04:01.0: Using VIACOMBO position fix
[   20.594517] snd_hda_intel 0000:04:01.0: PCI: Disallowing DAC for device
[   20.613956] autoconfig: line_outs=1 (0x1f/0x0/0x0/0x0/0x0) type:speaker
[   20.613964]    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   20.613967]    hp_outs=1 (0x20/0x0/0x0/0x0/0x0)
[   20.613970]    mono: mono_out=0x0
[   20.613972]    inputs:
[   20.613974]      Mic=0x1d
[   20.638206] input: HDA VIA VT82xx Speaker as /devices/pci0000:00/0000:00:13.0/0000:04:01.0/sound/card0/input16
[   20.639204] input: HDA VIA VT82xx Front Headphone as /devices/pci0000:00/0000:00:13.0/0000:04:01.0/sound/card0/input15
[   20.640915] input: HDA VIA VT82xx Mic as /devices/pci0000:00/0000:00:13.0/0000:04:01.0/sound/card0/input14
[   20.710508] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   20.827433] ndiswrapper (mp_init:211): couldn't initialize device: C0000001
[   20.827447] ndiswrapper (pnp_start_device:395): Windows driver couldn't initialize the device (C0000001)
[   20.827458] ndiswrapper (mp_halt:254): device f3e01500 is not initialized - not halting
[   20.827462] ndiswrapper: device eth%d removed
[   20.827587] ndiswrapper: probe of 0000:05:01.0 failed with error -22
[   20.830014] usbcore: registered new interface driver ndiswrapper
[   21.977013] Bluetooth: Core ver 2.17
[   21.978639] NET: Registered protocol family 31
[   21.978647] Bluetooth: HCI device and connection manager initialized
[   21.979378] Bluetooth: HCI socket layer initialized
[   21.979387] Bluetooth: L2CAP socket layer initialized
[   21.979399] Bluetooth: SCO socket layer initialized
[   22.013193] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   22.013202] Bluetooth: BNEP filters: protocol multicast
[   22.013221] Bluetooth: BNEP socket layer initialized
[   22.065451] Bluetooth: RFCOMM TTY layer initialized
[   22.065479] Bluetooth: RFCOMM socket layer initialized
[   22.065496] Bluetooth: RFCOMM ver 1.11
[   22.171820] init: failsafe main process (530) killed by TERM signal
[   22.562650] type=1400 audit(1418095930.302:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=661 comm="apparmor_parser"
[   22.562667] type=1400 audit(1418095930.302:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cupsd" pid=661 comm="apparmor_parser"
[   22.563422] type=1400 audit(1418095930.302:10): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=661 comm="apparmor_parser"
[   22.886183] type=1400 audit(1418095930.626:11): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/lightdm/lightdm-guest-session" pid=713 comm="apparmor_parser"
[   23.073273] init: cups main process (662) killed by HUP signal
[   23.073299] init: cups main process ended, respawning
[   24.151752] init: alsa-restore main process (896) terminated with status 99
[   24.154286] zram: module is from the staging directory, the quality is unknown, you have been warned.
[   24.160251] zram: Created 1 device(s) ...
[   24.207659] Adding 447540k swap on /dev/zram0.  Priority:5 extents:1 across:447540k SSFS
[   24.484280] init: Failed to spawn hybrid-gfx main process: unable to execute: No such file or directory
[   25.218896] audit_printk_skb: 147 callbacks suppressed
[   25.218905] type=1400 audit(1418095932.958:61): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cups-browsed" pid=1033 comm="apparmor_parser"
[   25.265314] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   25.266495] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   28.820263] init: plymouth-upstart-bridge main process ended, respawning
[   28.861251] init: plymouth-upstart-bridge main process ended, respawning
[   52.733145] type=1400 audit(1418095960.473:62): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=1876 comm="apparmor_parser"
[   52.733166] type=1400 audit(1418095960.473:63): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=1876 comm="apparmor_parser"
[   52.733937] type=1400 audit(1418095960.473:64): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=1876 comm="apparmor_parser"
[   79.709961] systemd-hostnamed[1998]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
[  116.799793] usbcore: deregistering interface driver ndiswrapper
[  116.822444] ndiswrapper version 1.59 loaded (smp=yes, preempt=no)
[  116.852450] ndiswrapper: driver mrv8335x (3Com,05/19/2005,3.1.1.10) loaded
[  116.853693] ndiswrapper: using IRQ 18
[  117.656301] ndiswrapper (mp_init:211): couldn't initialize device: C0000001
[  117.656317] ndiswrapper (pnp_start_device:395): Windows driver couldn't initialize the device (C0000001)
[  117.656331] ndiswrapper (mp_halt:254): device f3283500 is not initialized - not halting
[  117.656335] ndiswrapper: device eth%d removed
[  117.656487] ndiswrapper: probe of 0000:05:01.0 failed with error -22
[  117.663849] usbcore: registered new interface driver ndiswrapper
[  189.079594] perf samples too long (2503 > 2500), lowering kernel.perf_event_max_sample_rate to 50000
[  348.477048] usbcore: deregistering interface driver ndiswrapper
[  348.512199] ndiswrapper version 1.59 loaded (smp=yes, preempt=no)
[  348.546589] ndiswrapper: driver mrv8335x (3Com,05/19/2005,3.1.1.10) loaded
[  348.547840] ndiswrapper: using IRQ 18
[  349.352330] ndiswrapper (mp_init:211): couldn't initialize device: C0000001
[  349.352346] ndiswrapper (pnp_start_device:395): Windows driver couldn't initialize the device (C0000001)
[  349.352359] ndiswrapper (mp_halt:254): device f3283500 is not initialized - not halting
[  349.352363] ndiswrapper: device eth%d removed
[  349.352507] ndiswrapper: probe of 0000:05:01.0 failed with error -22
[  349.360084] usbcore: registered new interface driver ndiswrapper
[  443.972614] cfg80211: Calling CRDA to update world regulatory domain
[  444.016304] cfg80211: World regulatory domain updated:
[  444.016317] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  444.016321] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  444.016324] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  444.016326] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  444.016329] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  444.016331] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  518.583293] usbcore: deregistering interface driver ndiswrapper
[  518.606052] ndiswrapper version 1.59 loaded (smp=yes, preempt=no)
[  518.636375] ndiswrapper: driver mrv8335x (3Com,05/19/2005,3.1.1.10) loaded
[  518.637650] ndiswrapper: using IRQ 18
[  519.440331] ndiswrapper (mp_init:211): couldn't initialize device: C0000001
[  519.440346] ndiswrapper (pnp_start_device:395): Windows driver couldn't initialize the device (C0000001)
[  519.440358] ndiswrapper (mp_halt:254): device f3283500 is not initialized - not halting
[  519.440362] ndiswrapper: device eth%d removed
[  519.440507] ndiswrapper: probe of 0000:05:01.0 failed with error -22
[  519.447928] usbcore: registered new interface driver ndiswrapper
[  774.373464] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 1115.026289] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 1700.215014] perf samples too long (5016 > 5000), lowering kernel.perf_event_max_sample_rate to 25000
[ 3386.791772] systemd-hostnamed[3895]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
[ 7586.568963] systemd-hostnamed[4214]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
[ 7617.489543] usbcore: deregistering interface driver ndiswrapper
[ 7617.577532] ndiswrapper version 1.59 loaded (smp=yes, preempt=no)
[ 7617.674922] ndiswrapper: driver mrv8335 (3Com,05/19/2005,3.1.1.10) loaded
[ 7617.676474] ndiswrapper: using IRQ 18
[ 7618.480318] ndiswrapper (mp_init:211): couldn't initialize device: C0000001
[ 7618.480331] ndiswrapper (pnp_start_device:395): Windows driver couldn't initialize the device (C0000001)
[ 7618.480342] ndiswrapper (mp_halt:254): device f3286500 is not initialized - not halting
[ 7618.480346] ndiswrapper: device eth%d removed
[ 7618.480481] ndiswrapper: probe of 0000:05:01.0 failed with error -22
[ 7618.480568] usbcore: registered new interface driver ndiswrapper
[ 8064.438742] systemd-hostnamed[4405]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
[ 8375.671907] usbcore: deregistering interface driver ndiswrapper
[ 8375.685309] ndiswrapper version 1.59 loaded (smp=yes, preempt=no)
[ 8375.840165] ndiswrapper: driver netmw125 (Marvell,12/30/2005,3.2.3.2) loaded
[ 8375.841875] ndiswrapper: using IRQ 18
[ 8376.644312] ndiswrapper (mp_init:211): couldn't initialize device: C0000001
[ 8376.644324] ndiswrapper (pnp_start_device:395): Windows driver couldn't initialize the device (C0000001)
[ 8376.644335] ndiswrapper (mp_halt:254): device f5a34500 is not initialized - not halting
[ 8376.644339] ndiswrapper: device eth%d removed
[ 8376.644470] ndiswrapper: probe of 0000:05:01.0 failed with error -22
[ 8376.644556] usbcore: registered new interface driver ndiswrapper
[ 9119.674154] systemd-hostnamed[5302]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
[ 9179.152900] usbcore: deregistering interface driver ndiswrapper
[ 9179.173774] ndiswrapper version 1.59 loaded (smp=yes, preempt=no)
[ 9179.205855] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateMdl'
[ 9179.205878] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMSynchronizeWithInterruptEx'
[ 9179.205887] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisGetSystemUpTimeEx'
[ 9179.205895] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeNetBufferList'
[ 9179.205904] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeNetBufferListPool'
[ 9179.205912] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeMdl'
[ 9179.205921] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferAndNetBufferList'
[ 9179.205930] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMOidRequestComplete'
[ 9179.205938] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMSetMiniportAttributes'
[ 9179.205954] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisOpenConfigurationEx'
[ 9179.205963] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMDeregisterMiniportDriver'
[ 9179.205972] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMRegisterMiniportDriver'
[ 9179.205980] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMPauseComplete'
[ 9179.205989] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMSendNetBufferListsComplete'
[ 9179.206014] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMIndicateReceiveNetBufferLists'
[ 9179.206041] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMDeregisterInterruptEx'
[ 9179.206057] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMGetBusData'
[ 9179.206069] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateMemoryWithTagPriority'
[ 9179.206077] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferListPool'
[ 9179.206086] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMRegisterInterruptEx'
[ 9179.206107] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMDeregisterScatterGatherDma'
[ 9179.206116] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMRegisterScatterGatherDma'
[ 9179.206125] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateIoWorkItem'
[ 9179.206133] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisQueueIoWorkItem'
[ 9179.206142] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeIoWorkItem'
[ 9179.206155] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMIndicateStatusEx'
[ 9179.206166] ndiswrapper (import:232): unknown symbol: WDFLDR.SYS:'WdfVersionBind'
[ 9179.206172] ndiswrapper (import:232): unknown symbol: WDFLDR.SYS:'WdfVersionUnbind'
[ 9179.206176] ndiswrapper (load_sys_files:200): couldn't prepare driver 'netmw13b'
[ 9179.207385] ndiswrapper (load_wrap_driver:103): couldn't load driver netmw13b; check system log for messages from 'loadndisdriver'
[ 9179.207512] usbcore: registered new interface driver ndiswrapper
[ 9776.113298] atkbd serio0: Unknown key pressed (translated set 2, code 0x67 on isa0060/serio0).
[ 9776.113308] atkbd serio0: Use 'setkeycodes 67 <keycode>' to make it known.
[ 9776.353749] atkbd serio0: Unknown key pressed (translated set 2, code 0x67 on isa0060/serio0).
[ 9776.353758] atkbd serio0: Use 'setkeycodes 67 <keycode>' to make it known.
[ 9776.388197] atkbd serio0: Unknown key pressed (translated set 2, code 0x67 on isa0060/serio0).
[ 9776.388204] atkbd serio0: Use 'setkeycodes 67 <keycode>' to make it known.
[ 9776.422476] atkbd serio0: Unknown key pressed (translated set 2, code 0x67 on isa0060/serio0).
[ 9776.422484] atkbd serio0: Use 'setkeycodes 67 <keycode>' to make it known.
[ 9776.456837] atkbd serio0: Unknown key pressed (translated set 2, code 0x67 on isa0060/serio0).
[ 9776.456845] atkbd serio0: Use 'setkeycodes 67 <keycode>' to make it known.
[ 9776.491209] atkbd serio0: Unknown key pressed (translated set 2, code 0x67 on isa0060/serio0).
[ 9776.491217] atkbd serio0: Use 'setkeycodes 67 <keycode>' to make it known.
[ 9776.545167] atkbd serio0: Unknown key released (translated set 2, code 0x67 on isa0060/serio0).
[ 9776.545176] atkbd serio0: Use 'setkeycodes 67 <keycode>' to make it known.
[ 9777.704677] atkbd serio0: Unknown key pressed (translated set 2, code 0x67 on isa0060/serio0).
[ 9777.704687] atkbd serio0: Use 'setkeycodes 67 <keycode>' to make it known.
[ 9777.945479] atkbd serio0: Unknown key pressed (translated set 2, code 0x67 on isa0060/serio0).
[ 9777.945489] atkbd serio0: Use 'setkeycodes 67 <keycode>' to make it known.
[ 9777.979951] atkbd serio0: Unknown key pressed (translated set 2, code 0x67 on isa0060/serio0).
[ 9777.979962] atkbd serio0: Use 'setkeycodes 67 <keycode>' to make it known.
[ 9778.014827] atkbd serio0: Unknown key pressed (translated set 2, code 0x67 on isa0060/serio0).
[ 9778.014838] atkbd serio0: Use 'setkeycodes 67 <keycode>' to make it known.
[ 9778.049217] atkbd serio0: Unknown key pressed (translated set 2, code 0x67 on isa0060/serio0).
[ 9778.049225] atkbd serio0: Use 'setkeycodes 67 <keycode>' to make it known.
[ 9778.083618] atkbd serio0: Unknown key pressed (translated set 2, code 0x67 on isa0060/serio0).
[ 9778.083627] atkbd serio0: Use 'setkeycodes 67 <keycode>' to make it known.
[ 9778.118003] atkbd serio0: Unknown key pressed (translated set 2, code 0x67 on isa0060/serio0).
[ 9778.118013] atkbd serio0: Use 'setkeycodes 67 <keycode>' to make it known.
[ 9778.152356] atkbd serio0: Unknown key pressed (translated set 2, code 0x67 on isa0060/serio0).
[ 9778.152364] atkbd serio0: Use 'setkeycodes 67 <keycode>' to make it known.
[ 9778.187476] atkbd serio0: Unknown key pressed (translated set 2, code 0x67 on isa0060/serio0).
[ 9778.187484] atkbd serio0: Use 'setkeycodes 67 <keycode>' to make it known.
[ 9778.221819] atkbd serio0: Unknown key pressed (translated set 2, code 0x67 on isa0060/serio0).
[ 9778.221827] atkbd serio0: Use 'setkeycodes 67 <keycode>' to make it known.
[ 9778.256182] atkbd serio0: Unknown key pressed (translated set 2, code 0x67 on isa0060/serio0).
[ 9778.256189] atkbd serio0: Use 'setkeycodes 67 <keycode>' to make it known.
[ 9778.290619] atkbd serio0: Unknown key pressed (translated set 2, code 0x67 on isa0060/serio0).
[ 9778.290627] atkbd serio0: Use 'setkeycodes 67 <keycode>' to make it known.
[ 9778.349394] atkbd serio0: Unknown key released (translated set 2, code 0x67 on isa0060/serio0).
[ 9778.349401] atkbd serio0: Use 'setkeycodes 67 <keycode>' to make it known.
[ 9778.638778] atkbd serio0: Unknown key pressed (translated set 2, code 0x67 on isa0060/serio0).
[ 9778.638789] atkbd serio0: Use 'setkeycodes 67 <keycode>' to make it known.
[ 9778.894299] atkbd serio0: Unknown key released (translated set 2, code 0x67 on isa0060/serio0).
[ 9778.894310] atkbd serio0: Use 'setkeycodes 67 <keycode>' to make it known.
[ 9781.787507] atkbd serio0: Unknown key pressed (translated set 2, code 0x67 on isa0060/serio0).
[ 9781.787516] atkbd serio0: Use 'setkeycodes 67 <keycode>' to make it known.
[ 9782.029872] atkbd serio0: Unknown key pressed (translated set 2, code 0x67 on isa0060/serio0).
[ 9782.029882] atkbd serio0: Use 'setkeycodes 67 <keycode>' to make it known.
[ 9782.088731] atkbd serio0: Unknown key released (translated set 2, code 0x67 on isa0060/serio0).
[ 9782.088741] atkbd serio0: Use 'setkeycodes 67 <keycode>' to make it known.
[10146.247705] systemd-hostnamed[5502]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
[13092.637767] systemd-hostnamed[6030]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
[13143.721501] usbcore: deregistering interface driver ndiswrapper
[13143.769656] ndiswrapper version 1.59 loaded (smp=yes, preempt=no)
[13143.909446] ndiswrapper: driver netmw125 (Marvell,12/30/2005,3.2.3.2) loaded
[13143.910955] ndiswrapper: using IRQ 18
[13144.712324] ndiswrapper (mp_init:211): couldn't initialize device: C0000001
[13144.712337] ndiswrapper (pnp_start_device:395): Windows driver couldn't initialize the device (C0000001)
[13144.712349] ndiswrapper (mp_halt:254): device f3e01500 is not initialized - not halting
[13144.712352] ndiswrapper: device eth%d removed
[13144.712477] ndiswrapper: probe of 0000:05:01.0 failed with error -22
[13144.712564] usbcore: registered new interface driver ndiswrapper
[13187.892246] usbcore: deregistering interface driver ndiswrapper
[13187.913526] ndiswrapper version 1.59 loaded (smp=yes, preempt=no)
[13187.944339] ndiswrapper: driver netmw125 (Marvell,12/30/2005,3.2.3.2) loaded
[13187.945844] ndiswrapper: using IRQ 18
[13188.752317] ndiswrapper (mp_init:211): couldn't initialize device: C0000001
[13188.752330] ndiswrapper (pnp_start_device:395): Windows driver couldn't initialize the device (C0000001)
[13188.752341] ndiswrapper (mp_halt:254): device f3e04500 is not initialized - not halting
[13188.752344] ndiswrapper: device eth%d removed
[13188.752469] ndiswrapper: probe of 0000:05:01.0 failed with error -22
[13188.752555] usbcore: registered new interface driver ndiswrapper
[13212.923704] usbcore: deregistering interface driver ndiswrapper
[13212.946905] ndiswrapper version 1.59 loaded (smp=yes, preempt=no)
[13212.977828] ndiswrapper: driver netmw122 (Marvell,12/30/2005,3.2.3.2) loaded
[13212.979532] ndiswrapper: using IRQ 18
[13213.788297] ndiswrapper (mp_init:211): couldn't initialize device: C0000001
[13213.788310] ndiswrapper (pnp_start_device:395): Windows driver couldn't initialize the device (C0000001)
[13213.788321] ndiswrapper (mp_halt:254): device f5a34500 is not initialized - not halting
[13213.788324] ndiswrapper: device eth%d removed
[13213.788460] ndiswrapper: probe of 0000:05:01.0 failed with error -22
[13213.788543] usbcore: registered new interface driver ndiswrapper
[13238.916570] usbcore: deregistering interface driver ndiswrapper
[13238.937652] ndiswrapper version 1.59 loaded (smp=yes, preempt=no)
[13238.969078] ndiswrapper: driver netmw122 (Marvell,12/30/2005,3.2.3.2) loaded
[13238.970647] ndiswrapper: using IRQ 18
[13239.772304] ndiswrapper (mp_init:211): couldn't initialize device: C0000001
[13239.772317] ndiswrapper (pnp_start_device:395): Windows driver couldn't initialize the device (C0000001)
[13239.772327] ndiswrapper (mp_halt:254): device f5a34500 is not initialized - not halting
[13239.772330] ndiswrapper: device eth%d removed
[13239.772465] ndiswrapper: probe of 0000:05:01.0 failed with error -22
[13239.772552] usbcore: registered new interface driver ndiswrapper
[13310.830428] usbcore: deregistering interface driver ndiswrapper
[13310.851608] ndiswrapper version 1.59 loaded (smp=yes, preempt=no)
[13310.884702] ndiswrapper: driver netmw122 (Marvell,12/30/2005,3.2.3.2) loaded
[13310.886235] ndiswrapper: using IRQ 18
[13311.696290] ndiswrapper (mp_init:211): couldn't initialize device: C0000001
[13311.696302] ndiswrapper (pnp_start_device:395): Windows driver couldn't initialize the device (C0000001)
[13311.696313] ndiswrapper (mp_halt:254): device f5a35500 is not initialized - not halting
[13311.696317] ndiswrapper: device eth%d removed
[13311.696451] ndiswrapper: probe of 0000:05:01.0 failed with error -22
[13311.696536] usbcore: registered new interface driver ndiswrapper
[13476.128724] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[13686.040489] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
user@user-VA250D:~/Downloads/wireless driver/Driver/Win2kXP$ 
```

I still get this from iwconfig;

```
user@user-VA250D:~/Downloads/wireless driver/Driver/Win2kXP$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.
```


I have been trying to resolve this for about 12 hours and am going out of my mind trying to fix it becuse I have a buyer for this laptop that is expected tonight...

I really need an urgent responce!

I can give any information you need to try and help me fix the problem... please please please will someone help me!

Thanks in advance

Chris

---

### Post by chili555 on 2014-12-09
> [13310.851608] ndiswrapper version 1.59 loaded (smp=yes, preempt=no)
[13310.884702] ndiswrapper: driver netmw122 (Marvell,12/30/2005,3.2.3.2) loaded
[13310.886235] ndiswrapper: using IRQ 18
[13311.696290] ndiswrapper (mp_init:211): couldn't initialize device: C0000001
[13311.696302] ndiswrapper (pnp_start_device:395): [COLOR="#FF0000"]Windows driver couldn't initialize the device [/COLOR](C0000001)
[13311.696313] ndiswrapper (mp_halt:254): [COLOR="#FF0000"]device f5a35500 is not initialized - not halting[/COLOR]
[13311.696317] ndiswrapper: device eth%d removed
[13311.696451] ndiswrapper: [COLOR="#FF0000"]probe of 0000:05:01.0 failed with error -22[/COLOR]Ouch! That suggests an incorrect .inf and/or .sys file. It looks like you have two, at least, drivers loaded. That may be causing some confusion:> ndiswrapper: driver [COLOR="#FF0000"]mrv8335x[/COLOR] (3Com,05/19/2005,3.1.1.10) loaded
....
ndiswrapper: driver [COLOR="#FF0000"]mrv8335[/COLOR] (3Com,05/19/2005,3.1.1.10) loaded
....
ndiswrapper: driver[COLOR="#FF0000"] netmw122[/COLOR] (Marvell,12/30/2005,3.2.3.2) loadedWithout a lot more diagnostics, I have no idea which is correct. I do know, however, that, unlike Windows, ndiswrapper doesn't automagically overwrite the older driver with the new. I suggest we look at what is in here:```
ls /etc/ndiswrapper
```If you have any insight as to what you've tried and failed, it may help us proceed.

---

