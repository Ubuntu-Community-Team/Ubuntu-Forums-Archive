---
title: "Strange dmesg/syslog output"
date: 2007-04-24
forum: Networking &amp; Wireless
---

### Post by mwells on 2007-04-24
Hi all,

I have successfully managed to setup my netgear wireless card with Fesity using ndiswrapper . .great!

However I notice that dhclient is allways running really high when I run 'top', also when I check dmesg/syslog output I note they are full ofrelated warnings/errors.

Is anyone able to interpret what is going on with all this? or is it all standard network manager output?

**dmesg output**
```

[   29.485658] input: Macintosh mouse button emulation as /class/input/input0
[   29.485697] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   29.485703] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   29.485987] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[   29.485990] PNP: PS/2 controller doesn't have AUX irq; using default 12
[   29.486374] serio: i8042 KBD port at 0x60,0x64 irq 1
[   29.486380] serio: i8042 AUX port at 0x60,0x64 irq 12
[   29.486537] EISA: Probing bus 0 at eisa.0
[   29.486561] Cannot allocate resource for EISA slot 4
[   29.486563] Cannot allocate resource for EISA slot 5
[   29.486576] EISA: Detected 0 cards.
[   29.516803] TCP cubic registered
[   29.516813] NET: Registered protocol family 1
[   29.516846] Using IPI No-Shortcut mode
[   29.516969] ACPI: (supports S0 S1 S3 S4 S5)
[   29.517028]   Magic number: 3:917:641
[   29.517819] Freeing unused kernel memory: 328k freed
[   29.518105] Time: tsc clocksource has been installed.
[   29.536778] input: AT Translated Set 2 keyboard as /class/input/input1
[   30.764220] Capability LSM initialized
[   30.803680] ACPI: Fan [FAN] (on)
[   30.807805] ACPI: CPU0 (power states: C1[C1] C2[C2])
[   30.809516] ACPI: Thermal Zone [THRM] (40 C)
[   31.443171] ieee1394: Initialized config rom entry `ip1394'
[   31.444777] ACPI: PCI Interrupt 0000:00:0a.0[A] -> GSI 18 (level, low) -> IRQ 16
[   31.494771] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[16]  MMIO=[e8025000-e80257ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   31.501530] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[   31.501578] 8139cp 0000:00:0b.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[   31.501580] 8139cp 0000:00:0b.0: Try the "8139too" driver instead.
[   31.503857] 8139too Fast Ethernet driver 0.9.28
[   31.503922] ACPI: PCI Interrupt 0000:00:0b.0[A] -> GSI 18 (level, low) -> IRQ 16
[   31.504244] eth0: RealTek RTL8139 at 0xe088e000, 00:40:ca:4f:0e:31, IRQ 16
[   31.504246] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[   31.517340] usbcore: registered new interface driver usbfs
[   31.517377] usbcore: registered new interface driver hub
[   31.517407] usbcore: registered new device driver usb
[   31.518525] USB Universal Host Controller Interface driver v3.0
[   31.519058] ACPI: PCI Interrupt Link [ALKB] BIOS reported IRQ 0, using IRQ 21
[   31.519061] ACPI: PCI Interrupt Link [ALKB] enabled at IRQ 21
[   31.519074] ACPI: PCI Interrupt 0000:00:10.0[A] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 17
[   31.519089] uhci_hcd 0000:00:10.0: UHCI Host Controller
[   31.519311] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
[   31.519349] uhci_hcd 0000:00:10.0: irq 17, io base 0x0000d400
[   31.519525] usb usb1: configuration #1 chosen from 1 choice
[   31.519555] hub 1-0:1.0: USB hub found
[   31.519568] hub 1-0:1.0: 2 ports detected
[   31.596118] SCSI subsystem initialized
[   31.601797] libata version 2.20 loaded.
[   31.620698] ACPI: PCI Interrupt 0000:00:10.1[B] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 17
[   31.620717] uhci_hcd 0000:00:10.1: UHCI Host Controller
[   31.620747] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
[   31.620776] uhci_hcd 0000:00:10.1: irq 17, io base 0x0000d800
[   31.620900] usb usb2: configuration #1 chosen from 1 choice
[   31.620939] hub 2-0:1.0: USB hub found
[   31.620952] hub 2-0:1.0: 2 ports detected
[   31.693110] Floppy drive(s): fd0 is 1.44M
[   31.724617] ACPI: PCI Interrupt 0000:00:10.2[C] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 17
[   31.724638] uhci_hcd 0000:00:10.2: UHCI Host Controller
[   31.724671] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
[   31.724702] uhci_hcd 0000:00:10.2: irq 17, io base 0x0000dc00
[   31.724848] usb usb3: configuration #1 chosen from 1 choice
[   31.724880] hub 3-0:1.0: USB hub found
[   31.724894] hub 3-0:1.0: 2 ports detected
[   31.726044] FDC 0 is a post-1991 82077
[    3.720000] Time: acpi_pm clocksource has been installed.
[    3.756000] ACPI: PCI Interrupt 0000:00:10.3[D] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 17
[    3.756000] ehci_hcd 0000:00:10.3: EHCI Host Controller
[    3.756000] ehci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
[    3.756000] ehci_hcd 0000:00:10.3: irq 17, io mem 0xe8026000
[    3.756000] ehci_hcd 0000:00:10.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.756000] usb usb4: configuration #1 chosen from 1 choice
[    3.756000] hub 4-0:1.0: USB hub found
[    3.756000] hub 4-0:1.0: 6 ports detected
[    3.864000] VP_IDE: IDE controller at PCI slot 0000:00:11.1
[    3.868000] ACPI: PCI Interrupt Link [ALKA] BIOS reported IRQ 0, using IRQ 20
[    3.868000] ACPI: PCI Interrupt Link [ALKA] enabled at IRQ 20
[    3.868000] ACPI: PCI Interrupt 0000:00:11.1[A] -> Link [ALKA] -> GSI 20 (level, low) -> IRQ 18
[    3.868000] VP_IDE: chipset revision 6
[    3.868000] VP_IDE: not 100% native mode: will probe irqs later
[    3.868000] VP_IDE: VIA vt8235 (rev 00) IDE UDMA133 controller on pci0000:00:11.1
[    3.868000]     ide0: BM-DMA at 0xe000-0xe007, BIOS settings: hda:DMA, hdb:DMA
[    3.868000]     ide1: BM-DMA at 0xe008-0xe00f, BIOS settings: hdc:pio, hdd:DMA
[    3.868000] Probing IDE interface ide0...
[    4.424000] hda: SONY CD-RW CRX320EE, ATAPI CD/DVD-ROM drive
[    4.708000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00309500a0015e3b]
[    4.716000] hdb: ST380022A, ATA DISK drive
[    4.772000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[    4.784000] Probing IDE interface ide1...
[    5.076000] usb 1-2: new low speed USB device using uhci_hcd and address 2
[    5.264000] usb 1-2: configuration #1 chosen from 1 choice
[    5.280000] usbcore: registered new interface driver hiddev
[    5.296000] input: Logitech USB-PS/2 Optical Mouse as /class/input/input2
[    5.296000] input: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:10.0-2
[    5.296000] usbcore: registered new interface driver usbhid
[    5.296000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[    5.460000] hdd: ST380011A, ATA DISK drive
[    5.520000] ide1 at 0x170-0x177,0x376 on irq 15
[    5.552000] hda: ATAPI 8X DVD-ROM CD-R/RW drive, 1536kB Cache, UDMA(33)
[    5.552000] Uniform CD-ROM driver Revision: 3.20
[    5.568000] hdb: max request size: 128KiB
[    5.568000] hdb: 156301488 sectors (80026 MB) w/1024KiB Cache, CHS=65535/16/63, UDMA(33)
[    5.572000] hdb: cache flushes supported
[    5.572000]  hdb: hdb1 hdb2 < hdb5 >
[    5.608000] hdd: max request size: 512KiB
[    5.608000] hdd: 156301488 sectors (80026 MB) w/2048KiB Cache, CHS=16383/255/63, UDMA(100)
[    5.608000] hdd: cache flushes supported
[    5.608000]  hdd: hdd1 hdd2
[    5.944000] Attempting manual resume
[    5.944000] swsusp: Resume From Partition 3:69
[    5.944000] PM: Checking swsusp image.
[    5.964000] PM: Resume from disk failed.
[    6.028000] kjournald starting.  Commit interval 5 seconds
[    6.028000] EXT3-fs: mounted filesystem with ordered data mode.
[   16.648000] eth0: link down
[   18.108000] NET: Registered protocol family 17
[   19.000000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   19.004000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   19.416000] Linux agpgart interface v0.102 (c) Dave Jones
[   19.444000] agpgart: Detected VIA PM266/KM266 chipset
[   19.448000] agpgart: AGP aperture is 64M @ 0xe0000000
[   19.480000] irda_init()
[   19.480000] NET: Registered protocol family 23
[   19.776000] input: PC Speaker as /class/input/input3
[   19.848000] parport: PnPBIOS parport detected.
[   19.848000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   19.940000] nvidia: module license 'NVIDIA' taints kernel.
[   20.324000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 19
[   20.324000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-9631  Thu Nov  9 17:38:10 PST 2006
[   20.472000] ACPI: PCI Interrupt Link [ALKC] BIOS reported IRQ 0, using IRQ 22
[   20.472000] ACPI: PCI Interrupt Link [ALKC] enabled at IRQ 22
[   20.472000] ACPI: PCI Interrupt 0000:00:11.5[C] -> Link [ALKC] -> GSI 22 (level, low) -> IRQ 20
[   20.472000] PCI: Setting latency timer of device 0000:00:11.5 to 64
[   21.220000] fuse init (API version 7.8)
[   21.252000] lp0: using parport0 (interrupt-driven).
[   21.324000] Adding 1510068k swap on /dev/disk/by-uuid/bc418f06-6cd9-4507-8a2d-3f176761db46.  Priority:-1 extents:1 across:1510068k
[   21.480000] EXT3 FS on hdb1, internal journal
[   25.616000] ndiswrapper version 1.42 loaded (smp=yes)
[   25.692000] ndiswrapper: driver wg311v3 (NETGEAR,08/22/2005,3.2.1.3) loaded
[   25.696000] ACPI: PCI Interrupt 0000:00:09.0[A] -> GSI 17 (level, low) -> IRQ 21
[   25.700000] ndiswrapper: using IRQ 21
[   25.976000] wlan0: ethernet device 00:14:6c:c4:ae:c0 using NDIS driver: wg311v3, version: 0x3020002, NDIS version: 0x501, vendor: '', 11AB:1FAA.5.conf
[   25.976000] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   29.668000] usbcore: registered new interface driver ndiswrapper
[   33.788000] NET: Registered protocol family 10
[   33.792000] lo: Disabled Privacy Extensions
[   33.792000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   34.272000] No dock devices found.
[   34.328000] input: Power Button (FF) as /class/input/input4
[   34.336000] ACPI: Power Button (FF) [PWRF]
[   34.372000] input: Power Button (CM) as /class/input/input5
[   34.380000] ACPI: Power Button (CM) [PWRB]
[   34.548000] ibm_acpi: ec object not found
[   34.720000] Using specific hotkey driver
[   34.840000] pcc_acpi: loading...
[   43.788000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[   43.788000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[   43.788000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[   44.116000] **WARNING** I2C adapter driver [NVIDIA i2c adapter 0 at 1:00.0] forgot to specify physical device; fix it!
[   44.116000] **WARNING** I2C adapter driver [NVIDIA i2c adapter 1 at 1:00.0] forgot to specify physical device; fix it!
[   44.116000] **WARNING** I2C adapter driver [NVIDIA i2c adapter 2 at 1:00.0] forgot to specify physical device; fix it!
[   44.284000] wlan0: no IPv6 routers present
[   44.540000] ppdev: user-space parallel port driver
[   48.176000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   48.176000] apm: overridden by ACPI.
[   48.392000] Bluetooth: Core ver 2.11
[   48.392000] NET: Registered protocol family 31
[   48.392000] Bluetooth: HCI device and connection manager initialized
[   48.392000] Bluetooth: HCI socket layer initialized
[   48.432000] Bluetooth: L2CAP ver 2.8
[   48.432000] Bluetooth: L2CAP socket layer initialized
[   48.500000] Bluetooth: RFCOMM socket layer initialized
[   48.500000] Bluetooth: RFCOMM TTY layer initialized
[   48.500000] Bluetooth: RFCOMM ver 1.8
[   66.064000] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   68.084000] ndiswrapper (set_essid:59): setting essid failed (C0000001)
[   68.992000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   70.116000] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   80.972000] wlan0: no IPv6 routers present
[   99.040000] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  116.760000] wlan0: no IPv6 routers present
[  251.728000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  313.756000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  822.336000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[  822.336000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[  822.340000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[ 1012.556000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1082.820000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1187.984000] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1204.864000] wlan0: no IPv6 routers present
[ 1579.020000] ndiswrapper (set_scan:1177): scanning failed (C0000001)
[ 1579.040000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1584.036000] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1597.848000] wlan0: no IPv6 routers present
[ 3266.696000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3266.712000] eth0: link down
[ 3266.712000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 3291.320000] eth0: link down
[ 3291.320000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 3296.416000] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 3311.856000] wlan0: no IPv6 routers present
[ 8104.648000] usb 4-6: new high speed USB device using ehci_hcd and address 3
[ 8104.788000] usb 4-6: configuration #1 chosen from 1 choice
[ 8104.928000] usbcore: registered new interface driver libusual
[ 8104.944000] Initializing USB Mass Storage driver...
[ 8104.944000] scsi0 : SCSI emulation for USB Mass Storage devices
[ 8104.944000] usb-storage: device found at 3
[ 8104.944000] usb-storage: waiting for device to settle before scanning
[ 8104.944000] usbcore: registered new interface driver usb-storage
[ 8104.944000] USB Mass Storage support registered.
[ 8109.944000] usb-storage: device scan complete
[ 8109.944000] scsi 0:0:0:0: Direct-Access     ClvrStuf USB Flash Drive  6.51 PQ: 0 ANSI: 0 CCS
[ 8109.944000] scsi 0:0:0:1: CD-ROM            ClvrStuf USB Flash Drive  6.51 PQ: 0 ANSI: 0
[ 8109.996000] sr0: scsi3-mmc drive: 8x/40x writer xa/form2 cdda tray
[ 8110.000000] sr 0:0:0:1: Attached scsi CD-ROM sr0
[ 8110.028000] SCSI device sda: 1944991 512-byte hdwr sectors (996 MB)
[ 8110.028000] sda: Write Protect is off
[ 8110.028000] sda: Mode Sense: 45 00 00 08
[ 8110.028000] sda: assuming drive cache: write through
[ 8110.032000] SCSI device sda: 1944991 512-byte hdwr sectors (996 MB)
[ 8110.036000] sda: Write Protect is off
[ 8110.036000] sda: Mode Sense: 45 00 00 08
[ 8110.036000] sda: assuming drive cache: write through
[ 8110.036000]  sda:<5>sd 0:0:0:0: Attached scsi generic sg0 type 0
[ 8110.036000]  sda1
[ 8110.036000] sr 0:0:0:1: Attached scsi generic sg1 type 5
[ 8110.060000] sd 0:0:0:0: Attached scsi removable disk sda
[ 9384.196000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 9384.212000] eth0: link down
[ 9384.212000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 9420.304000] eth0: link down
[ 9420.304000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 9424.040000] eth0: link down
[ 9424.040000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 9441.008000] eth0: link down
[ 9441.008000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 9467.304000] eth0: link down
[ 9467.304000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 9558.808000] eth0: link down
[ 9558.808000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 9563.768000] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 9580.492000] wlan0: no IPv6 routers present
[ 9587.244000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 9596.712000] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 9611.072000] wlan0: no IPv6 routers present
[66560.048000] usb 4-6: USB disconnect, address 3
[103988.096000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[103990.716000] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[104007.184000] wlan0: no IPv6 routers present


```

**Syslog output**
```

Apr 24 11:22:53 server1 NetworkManager: <information>^Iwpa_supplicant(1662): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
Apr 24 11:22:53 server1 NetworkManager: <information>^Iwpa_supplicant(1662): Wireless event: cmd=0x8b06 len=8
Apr 24 11:22:53 server1 NetworkManager: <information>^Iwpa_supplicant(1662): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
Apr 24 11:22:53 server1 NetworkManager: <information>^Iwpa_supplicant(1662): Wireless event: cmd=0x8b06 len=8
Apr 24 11:22:53 server1 NetworkManager: <information>^Iwpa_supplicant(1662): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
Apr 24 11:22:53 server1 NetworkManager: <information>^Iwpa_supplicant(1662): Wireless event: cmd=0x8b06 len=8
Apr 24 11:22:53 server1 NetworkManager: <information>^Iwpa_supplicant(1662): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
Apr 24 11:22:53 server1 NetworkManager: <information>^Iwpa_supplicant(1662): Wireless event: cmd=0x8b06 len=8
Apr 24 11:23:45 server1 dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
Apr 24 11:23:49 server1 dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
Apr 24 11:23:59 server1 dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 17
Apr 24 11:24:16 server1 dhclient: No DHCPOFFERS received.
Apr 24 11:24:16 server1 dhclient: No working leases in persistent database - sleeping.
Apr 24 11:26:47 server1 dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
Apr 24 11:26:52 server1 dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
Apr 24 11:27:05 server1 dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
Apr 24 11:27:18 server1 dhclient: No DHCPOFFERS received.
Apr 24 11:27:18 server1 dhclient: No working leases in persistent database - sleeping.
Apr 24 11:29:53 server1 nmbd[18074]: [2007/04/24 11:29:53, 0] nmbd/nmbd_incomingrequests.c:process_name_refresh_request(172)
Apr 24 11:29:53 server1 nmbd[18074]:   process_name_refresh_request: unicast name registration request received for name MASSIVE<20> from IP 192.168.0.3 on subnet UNICAST_SUBNET.
Apr 24 11:29:53 server1 nmbd[18074]: [2007/04/24 11:29:53, 0] nmbd/nmbd_incomingrequests.c:process_name_refresh_request(173)
Apr 24 11:29:53 server1 nmbd[18074]:   Error - should be sent to WINS server
Apr 24 11:29:53 server1 nmbd[18074]: [2007/04/24 11:29:53, 0] nmbd/nmbd_incomingrequests.c:process_name_refresh_request(172)
Apr 24 11:29:53 server1 nmbd[18074]:   process_name_refresh_request: unicast name registration request received for name MASSIVE<00> from IP 192.168.0.3 on subnet UNICAST_SUBNET.
Apr 24 11:29:53 server1 nmbd[18074]: [2007/04/24 11:29:53, 0] nmbd/nmbd_incomingrequests.c:process_name_refresh_request(173)
Apr 24 11:29:53 server1 nmbd[18074]:   Error - should be sent to WINS server
Apr 24 11:29:53 server1 nmbd[18074]: [2007/04/24 11:29:53, 0] nmbd/nmbd_incomingrequests.c:process_name_refresh_request(172)
Apr 24 11:29:53 server1 nmbd[18074]:   process_name_refresh_request: unicast name registration request received for name MSHOME<00> from IP 192.168.0.3 on subnet UNICAST_SUBNET.
Apr 24 11:29:53 server1 nmbd[18074]: [2007/04/24 11:29:53, 0] nmbd/nmbd_incomingrequests.c:process_name_refresh_request(173)
Apr 24 11:29:53 server1 nmbd[18074]:   Error - should be sent to WINS server
Apr 24 11:31:47 server1 dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
Apr 24 11:31:51 server1 dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Apr 24 11:31:58 server1 dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
Apr 24 11:32:08 server1 dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
Apr 24 11:32:18 server1 dhclient: No DHCPOFFERS received.
Apr 24 11:32:18 server1 dhclient: No working leases in persistent database - sleeping.
Apr 24 11:35:59 server1 dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Apr 24 11:36:07 server1 dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 17
Apr 24 11:36:24 server1 dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
Apr 24 11:36:30 server1 dhclient: No DHCPOFFERS received.
Apr 24 11:36:30 server1 dhclient: No working leases in persistent database - sleeping.
Apr 24 11:37:53 server1 nmbd[18074]: [2007/04/24 11:37:53, 0] nmbd/nmbd_incomingrequests.c:process_name_refresh_request(172)
Apr 24 11:37:53 server1 nmbd[18074]:   process_name_refresh_request: unicast name registration request received for name MASSIVE<20> from IP 192.168.0.3 on subnet UNICAST_SUBNET.
Apr 24 11:37:53 server1 nmbd[18074]: [2007/04/24 11:37:53, 0] nmbd/nmbd_incomingrequests.c:process_name_refresh_request(173)
Apr 24 11:37:53 server1 nmbd[18074]:   Error - should be sent to WINS server
Apr 24 11:37:53 server1 nmbd[18074]: [2007/04/24 11:37:53, 0] nmbd/nmbd_incomingrequests.c:process_name_refresh_request(172)
Apr 24 11:37:53 server1 nmbd[18074]:   process_name_refresh_request: unicast name registration request received for name MASSIVE<00> from IP 192.168.0.3 on subnet UNICAST_SUBNET.
Apr 24 11:37:53 server1 nmbd[18074]: [2007/04/24 11:37:53, 0] nmbd/nmbd_incomingrequests.c:process_name_refresh_request(173)
Apr 24 11:37:53 server1 nmbd[18074]:   Error - should be sent to WINS server
Apr 24 11:37:53 server1 nmbd[18074]: [2007/04/24 11:37:53, 0] nmbd/nmbd_incomingrequests.c:process_name_refresh_request(172)
Apr 24 11:37:53 server1 nmbd[18074]:   process_name_refresh_request: unicast name registration request received for name MSHOME<00> from IP 192.168.0.3 on subnet UNICAST_SUBNET.
Apr 24 11:37:53 server1 nmbd[18074]: [2007/04/24 11:37:53, 0] nmbd/nmbd_incomingrequests.c:process_name_refresh_request(173)
Apr 24 11:37:53 server1 nmbd[18074]:   Error - should be sent to WINS server
Apr 24 11:39:46 server1 dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Apr 24 11:39:49 server1 dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
Apr 24 11:39:55 server1 dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Apr 24 11:40:03 server1 dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
Apr 24 11:40:17 server1 dhclient: No DHCPOFFERS received.
Apr 24 11:40:17 server1 dhclient: No working leases in persistent database - sleeping.
Apr 24 11:44:00 server1 NetworkManager: <information>^Iwpa_supplicant(1662): NING][LOWER_UP])
Apr 24 11:44:00 server1 NetworkManager: <information>^Iwpa_supplicant(1662): Wireless event: cmd=0x8b06 len=8
Apr 24 11:44:00 server1 NetworkManager: <information>^Iwpa_supplicant(1662): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
Apr 24 11:44:00 server1 NetworkManager: <information>^Iwpa_supplicant(1662): Wireless event: cmd=0x8b06 len=8
Apr 24 11:44:00 server1 NetworkManager: <information>^Iwpa_supplicant(1662): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
Apr 24 11:44:00 server1 NetworkManager: <information>^Iwpa_supplicant(1662): Wireless event: cmd=0x8b06 len=8
Apr 24 11:44:00 server1 NetworkManager: <information>^Iwpa_supplicant(1662): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
Apr 24 11:44:00 server1 NetworkManager: <information>^Iwpa_supplicant(1662): Wireless event: cmd=0x8b06 len=8
Apr 24 11:44:00 server1 NetworkManager: <information>^Iwpa_supplicant(1662): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
Apr 24 11:44:00 server1 NetworkManager: <information>^Iwpa_supplicant(1662): Wireless event: cmd=0x8b06 len=8
Apr 24 11:44:00 server1 NetworkManager: <information>^Iwpa_supplicant(1662): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
Apr 24 11:44:00 server1 NetworkManager: <information>^Iwpa_supplicant(1662): Wireless event: cmd=0x8b06 len=8
Apr 24 11:44:00 server1 NetworkManager: <information>^Iwpa_supplicant(1662): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
Apr 24 11:44:00 server1 NetworkManager: <information>^Iwpa_supplicant(1662): Wireless event: cmd=0x8b06 len=8
Apr 24 11:44:00 server1 NetworkManager: <information>^Iwpa_supplicant(1662): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
Apr 24 11:44:00 server1 NetworkManager: <information>^Iwpa_supplicant(1662): Wireless event: cmd=0x8b06 len=8
Apr 24 11:44:00 server1 NetworkManager: <information>^Iwpa_supplicant(1662): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
Apr 24 11:44:00 server1 NetworkManager: <information>^Iwpa_supplicant(1662): Wireless event: cmd=0x8b06 len=8
Apr 24 11:44:00 server1 NetworkManager: <information>^Iwpa_supplicant(1662): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
Apr 24 11:44:00 server1 NetworkManager: <information>^Iwpa_supplicant(1662): Wireless event: cmd=0x8b06 len=8
Apr 24 11:44:53 server1 dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
Apr 24 11:44:59 server1 dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Apr 24 11:45:06 server1 dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
Apr 24 11:45:18 server1 dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
Apr 24 11:45:24 server1 dhclient: No DHCPOFFERS received.
Apr 24 11:45:24 server1 dhclient: No working leases in persistent database - sleeping.
Apr 24 11:45:52 server1 nmbd[18074]: [2007/04/24 11:45:52, 0] nmbd/nmbd_incomingrequests.c:process_name_refresh_request(172)
Apr 24 11:45:52 server1 nmbd[18074]:   process_name_refresh_request: unicast name registration request received for name MASSIVE<20> from IP 192.168.0.3 on subnet UNICAST_SUBNET.
Apr 24 11:45:52 server1 nmbd[18074]: [2007/04/24 11:45:52, 0] nmbd/nmbd_incomingrequests.c:process_name_refresh_request(173)
Apr 24 11:45:52 server1 nmbd[18074]:   Error - should be sent to WINS server
Apr 24 11:45:52 server1 nmbd[18074]: [2007/04/24 11:45:52, 0] nmbd/nmbd_incomingrequests.c:process_name_refresh_request(172)
Apr 24 11:45:52 server1 nmbd[18074]:   process_name_refresh_request: unicast name registration request received for name MASSIVE<00> from IP 192.168.0.3 on subnet UNICAST_SUBNET.
Apr 24 11:45:52 server1 nmbd[18074]: [2007/04/24 11:45:52, 0] nmbd/nmbd_incomingrequests.c:process_name_refresh_request(173)
Apr 24 11:45:52 server1 nmbd[18074]:   Error - should be sent to WINS server
Apr 24 11:45:52 server1 nmbd[18074]: [2007/04/24 11:45:52, 0] nmbd/nmbd_incomingrequests.c:process_name_refresh_request(172)
Apr 24 11:45:52 server1 nmbd[18074]:   process_name_refresh_request: unicast name registration request received for name MSHOME<00> from IP 192.168.0.3 on subnet UNICAST_SUBNET.
Apr 24 11:45:52 server1 nmbd[18074]: [2007/04/24 11:45:52, 0] nmbd/nmbd_incomingrequests.c:process_name_refresh_request(173)
Apr 24 11:45:52 server1 nmbd[18074]:   Error - should be sent to WINS server
Apr 24 11:52:20 server1 dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
Apr 24 11:52:26 server1 dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
Apr 24 11:52:35 server1 dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 16
Apr 24 11:52:51 server1 dhclient: No DHCPOFFERS received.
Apr 24 11:52:51 server1 dhclient: No working leases in persistent database - sleeping.
Apr 24 11:53:52 server1 nmbd[18074]: [2007/04/24 11:53:52, 0] nmbd/nmbd_incomingrequests.c:process_name_refresh_request(172)
Apr 24 11:53:52 server1 nmbd[18074]:   process_name_refresh_request: unicast name registration request received for name MASSIVE<20> from IP 192.168.0.3 on subnet UNICAST_SUBNET.
Apr 24 11:53:52 server1 nmbd[18074]: [2007/04/24 11:53:52, 0] nmbd/nmbd_incomingrequests.c:process_name_refresh_request(173)
Apr 24 11:53:52 server1 nmbd[18074]:   Error - should be sent to WINS server
Apr 24 11:53:52 server1 nmbd[18074]: [2007/04/24 11:53:52, 0] nmbd/nmbd_incomingrequests.c:process_name_refresh_request(172)
Apr 24 11:53:52 server1 nmbd[18074]:   process_name_refresh_request: unicast name registration request received for name MASSIVE<00> from IP 192.168.0.3 on subnet UNICAST_SUBNET.
Apr 24 11:53:52 server1 nmbd[18074]: [2007/04/24 11:53:52, 0] nmbd/nmbd_incomingrequests.c:process_name_refresh_request(173)
Apr 24 11:53:52 server1 nmbd[18074]:   Error - should be sent to WINS server
Apr 24 11:53:52 server1 nmbd[18074]: [2007/04/24 11:53:52, 0] nmbd/nmbd_incomingrequests.c:process_name_refresh_request(172)
Apr 24 11:53:52 server1 nmbd[18074]:   process_name_refresh_request: unicast name registration request received for name MSHOME<00> from IP 192.168.0.3 on subnet UNICAST_SUBNET.
Apr 24 11:53:52 server1 nmbd[18074]: [2007/04/24 11:53:52, 0] nmbd/nmbd_incomingrequests.c:process_name_refresh_request(173)
Apr 24 11:53:52 server1 nmbd[18074]:   Error - should be sent to WINS server
Apr 24 11:58:31 server1 dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Apr 24 11:58:39 server1 dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
Apr 24 11:58:51 server1 dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
Apr 24 11:59:02 server1 dhclient: No DHCPOFFERS received.
Apr 24 11:59:02 server1 dhclient: No working leases in persistent database - sleeping.
Apr 24 12:01:52 server1 nmbd[18074]: [2007/04/24 12:01:52, 0] nmbd/nmbd_incomingrequests.c:process_name_refresh_request(172)
Apr 24 12:01:52 server1 nmbd[18074]:   process_name_refresh_request: unicast name registration request received for name MASSIVE<20> from IP 192.168.0.3 on subnet UNICAST_SUBNET.
Apr 24 12:01:52 server1 nmbd[18074]: [2007/04/24 12:01:52, 0] nmbd/nmbd_incomingrequests.c:process_name_refresh_request(173)
Apr 24 12:01:52 server1 nmbd[18074]:   Error - should be sent to WINS server
Apr 24 12:01:52 server1 nmbd[18074]: [2007/04/24 12:01:52, 0] nmbd/nmbd_incomingrequests.c:process_name_refresh_request(172)
Apr 24 12:01:52 server1 nmbd[18074]:   process_name_refresh_request: unicast name registration request received for name MASSIVE<00> from IP 192.168.0.3 on subnet UNICAST_SUBNET.
Apr 24 12:01:52 server1 nmbd[18074]: [2007/04/24 12:01:52, 0] nmbd/nmbd_incomingrequests.c:process_name_refresh_request(173)
Apr 24 12:01:52 server1 nmbd[18074]:   Error - should be sent to WINS server
Apr 24 12:01:52 server1 nmbd[18074]: [2007/04/24 12:01:52, 0] nmbd/nmbd_incomingrequests.c:process_name_refresh_request(172)
Apr 24 12:01:52 server1 nmbd[18074]:   process_name_refresh_request: unicast name registration request received for name MSHOME<00> from IP 192.168.0.3 on subnet UNICAST_SUBNET.
Apr 24 12:01:52 server1 nmbd[18074]: [2007/04/24 12:01:52, 0] nmbd/nmbd_incomingrequests.c:process_name_refresh_request(173)
Apr 24 12:01:52 server1 nmbd[18074]:   Error - should be sent to WINS server
Apr 24 12:02:48 server1 dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Apr 24 12:02:55 server1 dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
Apr 24 12:03:08 server1 dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
Apr 24 12:03:19 server1 dhclient: No DHCPOFFERS received.
Apr 24 12:03:19 server1 dhclient: No working leases in persistent database - sleeping.
Apr 24 12:05:04 server1 NetworkManager: <information>^Iwpa_supplicant(1662): ][LOWER_UP])
Apr 24 12:05:04 server1 NetworkManager: <information>^Iwpa_supplicant(1662): Wireless event: cmd=0x8b06 len=8
Apr 24 12:05:04 server1 NetworkManager: <information>^Iwpa_supplicant(1662): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
Apr 24 12:05:04 server1 NetworkManager: <information>^Iwpa_supplicant(1662): Wireless event: cmd=0x8b06 len=8
Apr 24 12:05:04 server1 NetworkManager: <information>^Iwpa_supplicant(1662): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
Apr 24 12:05:04 server1 NetworkManager: <information>^Iwpa_supplicant(1662): Wireless event: cmd=0x8b06 len=8
Apr 24 12:05:04 server1 NetworkManager: <information>^Iwpa_supplicant(1662): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
Apr 24 12:05:04 server1 NetworkManager: <information>^Iwpa_supplicant(1662): Wireless event: cmd=0x8b06 len=8
Apr 24 12:05:04 server1 NetworkManager: <information>^Iwpa_supplicant(1662): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
Apr 24 12:05:04 server1 NetworkManager: <information>^Iwpa_supplicant(1662): Wireless event: cmd=0x8b06 len=8
Apr 24 12:05:04 server1 NetworkManager: <information>^Iwpa_supplicant(1662): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
Apr 24 12:05:04 server1 NetworkManager: <information>^Iwpa_supplicant(1662): Wireless event: cmd=0x8b06 len=8
Apr 24 12:05:04 server1 NetworkManager: <information>^Iwpa_supplicant(1662): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
Apr 24 12:05:04 server1 NetworkManager: <information>^Iwpa_supplicant(1662): Wireless event: cmd=0x8b06 len=8
Apr 24 12:05:04 server1 NetworkManager: <information>^Iwpa_supplicant(1662): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
Apr 24 12:05:04 server1 NetworkManager: <information>^Iwpa_supplicant(1662): Wireless event: cmd=0x8b06 len=8
Apr 24 12:05:04 server1 NetworkManager: <information>^Iwpa_supplicant(1662): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
Apr 24 12:05:04 server1 NetworkManager: <information>^Iwpa_supplicant(1662): Wireless event: cmd=0x8b06 len=8
Apr 24 12:05:04 server1 NetworkManager: <information>^Iwpa_supplicant(1662): RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
Apr 24 12:05:04 server1 NetworkManager: <information>^Iwpa_supplicant(1662): Wireless event: cmd=0x8b06 len=8
Apr 24 12:05:56 server1 dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Apr 24 12:06:04 server1 dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15

```

Cheers

Matt

---

### Post by mwells on 2007-04-26
*bump* . . .Any thoughts on this at all?

Cheers

/Matt

---

### Post by gypsy_roadhog on 2007-04-30
Not really an answer but I am seeing something very similar. I have upgraded to feisty and my netgear wg311v2 card was running fine with ndiswrapper connecting to my router with wep encryption. 

I'd like to upgrade to wpa and was trying this out on feisty (I need to get it right as other members of the family connect to the router with devices running other OS)

However, when reverting to wep I am unable to connect. I can't seem to setup the card using iwconfig commands and I get the same link not ready message as yourself

I haven't solved this yet.

Neil

---

