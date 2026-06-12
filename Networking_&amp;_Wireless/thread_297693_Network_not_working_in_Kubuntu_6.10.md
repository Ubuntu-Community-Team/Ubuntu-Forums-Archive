---
title: "Network not working in Kubuntu 6.10"
date: 2006-11-11
forum: Networking &amp; Wireless
---

### Post by msie02 on 2006-11-11
Hi

I have just left Fedora Core 5 in favour of Kubuntu 6.10, but are unable to connect to the internet through Konqueror. I have tried different DNS/IPv6 solutions described in this forum without any luck.

My connection is wired to an ADSL modem (Zyxel HW660), which I know is working (as my desktop is connected through it). The NIC is also working as I am able to connect to my local FTP-server, however Konqueror is unable to find any webpages. I have disabled the wireless connection in order to simplify the problem. Does anyone have an idea of what is wrong? Below is the end of /var/log/syslog, in case this brings any information. As far as I can see, the router (192.168.1.1) offers IP address on the 255.255.255.255 subnet mask. I find it strange as my desktop claims to be on the 255.255.255.0 subnet mask??

Thank you
Martin

[SIZE="1"]
Nov 11 20:28:37 laptop kernel: [17179577.404000] EXT3-fs: mounted filesystem with ordered data mode.
Nov 11 20:28:37 laptop kernel: [17179577.544000] usb 5-5: new high speed USB device using ehci_hcd and address 2
Nov 11 20:28:37 laptop kernel: [17179577.676000] usb 5-5: configuration #1 chosen from 1 choice
Nov 11 20:28:37 laptop kernel: [17179578.552000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00023f5873401581]
Nov 11 20:28:37 laptop kernel: [17179586.620000] hw_random: cannot enable RNG, aborting
Nov 11 20:28:37 laptop kernel: [17179586.680000] Linux agpgart interface v0.101 (c) Dave Jones
Nov 11 20:28:37 laptop kernel: [17179586.684000] agpgart: Detected an Intel 915GM Chipset.
Nov 11 20:28:37 laptop kernel: [17179586.704000] agpgart: AGP aperture is 256M @ 0x0
Nov 11 20:28:37 laptop kernel: [17179586.768000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Nov 11 20:28:37 laptop kernel: [17179586.772000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Nov 11 20:28:37 laptop kernel: [17179587.068000] input: PS/2 Mouse as /class/input/input1
Nov 11 20:28:37 laptop kernel: [17179587.088000] input: AlpsPS/2 ALPS GlidePoint as /class/input/input2
Nov 11 20:28:37 laptop kernel: [17179587.156000] ACPI: PCI Interrupt 0000:00:1e.2[A] -> GSI 17 (level, low) -> IRQ 225
Nov 11 20:28:37 laptop kernel: [17179587.156000] PCI: Setting latency timer of device 0000:00:1e.2 to 64
Nov 11 20:28:37 laptop kernel: [17179587.428000] ts: Compaq touchscreen protocol output
Nov 11 20:28:37 laptop kernel: [17179587.492000] ieee80211_crypt: registered algorithm 'NULL'
Nov 11 20:28:37 laptop kernel: [17179587.496000] ieee80211: 802.11 data/management/control stack, git-1.1.13
Nov 11 20:28:37 laptop kernel: [17179587.496000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
Nov 11 20:28:37 laptop kernel: [17179587.524000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.1.2kmprq
Nov 11 20:28:37 laptop kernel: [17179587.524000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
Nov 11 20:28:37 laptop kernel: [17179587.524000] Driver 'ipw2200' needs updating - please use bus_type methods
Nov 11 20:28:37 laptop kernel: [17179587.568000] usbcore: registered new driver libusual
Nov 11 20:28:37 laptop kernel: [17179587.612000] SCSI subsystem initialized
Nov 11 20:28:37 laptop kernel: [17179587.616000] Initializing USB Mass Storage driver...
Nov 11 20:28:37 laptop kernel: [17179587.616000] scsi0 : SCSI emulation for USB Mass Storage devices
Nov 11 20:28:37 laptop kernel: [17179587.616000] usbcore: registered new driver usb-storage
Nov 11 20:28:37 laptop kernel: [17179587.616000] USB Mass Storage support registered.
Nov 11 20:28:37 laptop kernel: [17179587.616000] usb-storage: device found at 2
Nov 11 20:28:37 laptop kernel: [17179587.616000] usb-storage: waiting for device to settle before scanning
Nov 11 20:28:37 laptop kernel: [17179587.680000] sdhci: Secure Digital Host Controller Interface driver, 0.12
Nov 11 20:28:37 laptop kernel: [17179587.680000] sdhci: Copyright(c) Pierre Ossman
Nov 11 20:28:37 laptop kernel: [17179587.928000] Linux video capture interface: v1.00
Nov 11 20:28:37 laptop kernel: [17179587.976000] intel8x0_measure_ac97_clock: measured 55472 usecs
Nov 11 20:28:37 laptop kernel: [17179587.976000] intel8x0: clocking to 48000
Nov 11 20:28:37 laptop kernel: [17179587.976000] ACPI: PCI Interrupt 0000:02:02.0[A] -> GSI 22 (level, low) -> IRQ 233
Nov 11 20:28:37 laptop kernel: [17179587.976000] ipw2200: Detected Intel PRO/Wireless 2915ABG Network Connection
Nov 11 20:28:37 laptop kernel: [17179588.172000] ipw2200: Detected geography ZZE (13 802.11bg channels, 19 802.11a channels)
Nov 11 20:28:37 laptop kernel: [17179588.172000] r8169 Gigabit Ethernet driver 2.2LK loaded
Nov 11 20:28:37 laptop kernel: [17179588.172000] ACPI: PCI Interrupt 0000:02:01.0[A] -> GSI 21 (level, low) -> IRQ 50
Nov 11 20:28:37 laptop kernel: [17179588.172000] eth1: Identified chip type is 'RTL8169s/8110s'.
Nov 11 20:28:37 laptop kernel: [17179588.172000] eth1: RTL8169 at 0xe0b5c000, 00:0f:b0:92:57:de, IRQ 50
Nov 11 20:28:37 laptop kernel: [17179588.172000] sdhci: SDHCI controller found at 0000:02:04.2 [1524:0550] (rev 0)
Nov 11 20:28:37 laptop kernel: [17179588.172000] ACPI: PCI Interrupt 0000:02:04.2[B] -> GSI 17 (level, low) -> IRQ 225
Nov 11 20:28:37 laptop kernel: [17179588.172000] mmc0: SDHCI at 0xb0000100 irq 225 DMA
Nov 11 20:28:37 laptop kernel: [17179588.172000] ACPI: PCI Interrupt 0000:02:04.0[A] -> GSI 16 (level, low) -> IRQ 169
Nov 11 20:28:37 laptop kernel: [17179588.172000] Yenta: CardBus bridge found at 0000:02:04.0 [14c0:0012]
Nov 11 20:28:37 laptop kernel: [17179588.172000] Yenta: Using CSCINT to route CSC interrupts to PCI
Nov 11 20:28:37 laptop kernel: [17179588.172000] Yenta: Routing CardBus interrupts to PCI
Nov 11 20:28:37 laptop kernel: [17179588.172000] Yenta TI: socket 0000:02:04.0, mfunc 0x89001202, devctl 0x44
Nov 11 20:28:37 laptop kernel: [17179588.196000] saa7130/34: v4l2 driver version 0.2.14 loaded
Nov 11 20:28:37 laptop kernel: [17179588.404000] Yenta: ISA IRQ mask 0x0cf8, PCI irq 169
Nov 11 20:28:37 laptop kernel: [17179588.404000] Socket status: 30000006
Nov 11 20:28:37 laptop kernel: [17179588.404000] Yenta: Raising subordinate bus# of parent bus (#02) from #02 to #06
Nov 11 20:28:37 laptop kernel: [17179588.404000] pcmcia: parent PCI bridge I/O window: 0xa000 - 0xbfff
Nov 11 20:28:37 laptop kernel: [17179588.404000] cs: IO port probe 0xa000-0xbfff: clean.
Nov 11 20:28:37 laptop kernel: [17179588.404000] pcmcia: parent PCI bridge Memory window: 0xb0000000 - 0xbfffffff
Nov 11 20:28:37 laptop kernel: [17179588.404000] pcmcia: parent PCI bridge Memory window: 0x80000000 - 0x8fffffff
Nov 11 20:28:37 laptop kernel: [17179588.408000] ACPI: PCI Interrupt 0000:02:03.0[A] -> GSI 23 (level, low) -> IRQ 209
Nov 11 20:28:37 laptop kernel: [17179588.408000] saa7133[0]: found at 0000:02:03.0, rev: 240, irq: 209, latency: 128, mmio: 0xb0000800
Nov 11 20:28:37 laptop kernel: [17179588.408000] saa7133[0]: subsystem: 14c0:1212, board: LifeView FlyTV Platinum Mini2 [card=74,autodetected]
Nov 11 20:28:37 laptop kernel: [17179588.408000] saa7133[0]: board init: gpio is 10400
Nov 11 20:28:37 laptop kernel: [17179588.408000] input: saa7134 IR (LifeView FlyTV Plat as /class/input/input3
Nov 11 20:28:37 laptop kernel: [17179588.460000] r8169: eth0: link down
Nov 11 20:28:37 laptop kernel: [17179588.544000] saa7133[0]: i2c eeprom 00: c0 14 12 12 10 28 ff ff ff ff ff ff ff ff ff ff
Nov 11 20:28:37 laptop kernel: [17179588.544000] saa7133[0]: i2c eeprom 10: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
Nov 11 20:28:37 laptop kernel: [17179588.544000] saa7133[0]: i2c eeprom 20: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
Nov 11 20:28:37 laptop kernel: [17179588.544000] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
Nov 11 20:28:37 laptop kernel: [17179588.544000] saa7133[0]: i2c eeprom 40: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
Nov 11 20:28:37 laptop kernel: [17179588.544000] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
Nov 11 20:28:37 laptop kernel: [17179588.544000] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
Nov 11 20:28:37 laptop kernel: [17179588.544000] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
Nov 11 20:28:37 laptop kernel: [17179588.648000] tuner 0-004b: chip found @ 0x96 (saa7133[0])
Nov 11 20:28:37 laptop kernel: [17179588.696000] tuner 0-004b: setting tuner address to 61
Nov 11 20:28:37 laptop kernel: [17179588.732000] cs: IO port probe 0x100-0x3af: excluding 0x170-0x177 0x370-0x377
Nov 11 20:28:37 laptop kernel: [17179588.732000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
Nov 11 20:28:37 laptop kernel: [17179588.732000] cs: IO port probe 0x820-0x8ff: clean.
Nov 11 20:28:37 laptop kernel: [17179588.732000] cs: IO port probe 0xc00-0xcf7:<6>tuner 0-004b: type set to tda8290+75
Nov 11 20:28:37 laptop kernel: [17179588.736000]  clean.
Nov 11 20:28:37 laptop kernel: [17179588.736000] cs: IO port probe 0xa00-0xaff: clean.
Nov 11 20:28:37 laptop kernel: [17179588.800000] saa7133[0]: registered device video0 [v4l2]
Nov 11 20:28:37 laptop kernel: [17179588.800000] saa7133[0]: registered device vbi0
Nov 11 20:28:37 laptop kernel: [17179588.812000] saa7134 ALSA driver for DMA sound loaded
Nov 11 20:28:37 laptop kernel: [17179588.812000] saa7133[0]/alsa: saa7133[0] at 0xb0000800 irq 209 registered as card -1
Nov 11 20:28:37 laptop kernel: [17179589.048000] lp: driver loaded but no devices found
Nov 11 20:28:37 laptop kernel: [17179589.064000] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)
Nov 11 20:28:37 laptop kernel: [17179589.064000] ieee1394: sbp2: Try serialize_io=0 for better performance
Nov 11 20:28:37 laptop kernel: [17179589.080000] Adding 538136k swap on /dev/disk/by-uuid/eb10616a-529d-4524-bd1b-1b280d2695d2.  Priority:-1 extents:1 across:538136k
Nov 11 20:28:37 laptop kernel: [17179589.228000] EXT3 FS on hda5, internal journal
Nov 11 20:28:37 laptop kernel: [17179589.532000] NET: Registered protocol family 17
Nov 11 20:28:37 laptop kernel: [17179589.704000] r8169: eth0: link up
Nov 11 20:28:37 laptop kernel: [17179589.724000] r8169: eth0: link down
Nov 11 20:28:37 laptop kernel: [17179592.060000] r8169: eth0: link up
Nov 11 20:28:37 laptop kernel: [17179592.616000] usb-storage: device scan complete
Nov 11 20:28:37 laptop kernel: [17179592.616000]   Vendor: SMART G2  Model: Dell Memory Key   Rev: 1.04
Nov 11 20:28:37 laptop kernel: [17179592.616000]   Type:   Direct-Access                      ANSI SCSI revision: 01 CCS
Nov 11 20:28:37 laptop kernel: [17179592.656000] SCSI device sda: 251904 512-byte hdwr sectors (129 MB)
Nov 11 20:28:37 laptop kernel: [17179592.656000] sda: Write Protect is off
Nov 11 20:28:37 laptop kernel: [17179592.656000] sda: Mode Sense: 23 00 00 00
Nov 11 20:28:37 laptop kernel: [17179592.656000] sda: assuming drive cache: write through
Nov 11 20:28:37 laptop kernel: [17179592.656000] SCSI device sda: 251904 512-byte hdwr sectors (129 MB)
Nov 11 20:28:37 laptop kernel: [17179592.660000] sda: Write Protect is off
Nov 11 20:28:37 laptop kernel: [17179592.660000] sda: Mode Sense: 23 00 00 00
Nov 11 20:28:37 laptop kernel: [17179592.660000] sda: assuming drive cache: write through
Nov 11 20:28:37 laptop kernel: [17179592.660000]  sda: unknown partition table
Nov 11 20:28:37 laptop kernel: [17179592.660000] sd 0:0:0:0: Attached scsi removable disk sda
Nov 11 20:28:37 laptop kernel: [17179592.764000] sd 0:0:0:0: Attached scsi generic sg0 type 0
Nov 11 20:28:37 laptop kernel: [17179595.992000] NTFS driver 2.1.27 [Flags: R/O MODULE].
Nov 11 20:28:37 laptop kernel: [17179596.044000] NTFS volume version 3.1.
Nov 11 20:28:37 laptop kernel: [17179600.128000] ACPI: AC Adapter [ACAD] (off-line)
Nov 11 20:28:37 laptop kernel: [17179600.268000] ACPI: Battery Slot [BAT1] (battery present)
Nov 11 20:28:37 laptop kernel: [17179600.280000] ACPI: Power Button (FF) [PWRF]
Nov 11 20:28:37 laptop kernel: [17179600.280000] ACPI: Lid Switch [LID0]
Nov 11 20:28:37 laptop kernel: [17179600.280000] ACPI: Power Button (CM) [PWRB]
Nov 11 20:28:37 laptop kernel: [17179600.280000] ACPI: Sleep Button (CM) [SLPB]
Nov 11 20:28:37 laptop kernel: [17179600.416000] ibm_acpi: ec object not found
Nov 11 20:28:37 laptop kernel: [17179600.440000] pcc_acpi: loading...
Nov 11 20:28:37 laptop kernel: [17179600.536000] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
Nov 11 20:28:37 laptop kernel: [17179600.752000] acpi-cpufreq: CPU0 - ACPI performance management activated.
Nov 11 20:28:37 laptop kernel: [17179601.856000] [drm] Initialized drm 1.0.1 20051102
Nov 11 20:28:37 laptop kernel: [17179601.864000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 169
Nov 11 20:28:37 laptop kernel: [17179601.864000] [drm] Initialized radeon 1.25.0 20060524 on minor 0
Nov 11 20:28:37 laptop hpiod: 1.6.9 accepting connections at 2208... 
Nov 11 20:28:38 laptop kernel: [17179602.448000] apm: BIOS not found.
Nov 11 20:28:39 laptop kernel: [17179603.228000] [drm] Setting GART location based on new memory map
Nov 11 20:28:39 laptop kernel: [17179603.228000] [drm] Loading R300 Microcode
Nov 11 20:28:39 laptop kernel: [17179603.228000] [drm] writeback test succeeded in 1 usecs
Nov 11 20:28:43 laptop kdm_greet[4171]: Can't open default user face
Nov 11 20:28:44 laptop hcid[4266]: Bluetooth HCI daemon
Nov 11 20:28:44 laptop kernel: [17179608.148000] Bluetooth: Core ver 2.8
Nov 11 20:28:44 laptop kernel: [17179608.148000] NET: Registered protocol family 31
Nov 11 20:28:44 laptop kernel: [17179608.148000] Bluetooth: HCI device and connection manager initialized
Nov 11 20:28:44 laptop kernel: [17179608.148000] Bluetooth: HCI socket layer initialized
Nov 11 20:28:44 laptop hcid[4266]: Register path:/org/bluez fallback:1
Nov 11 20:28:44 laptop kernel: [17179608.760000] Bluetooth: L2CAP ver 2.8
Nov 11 20:28:44 laptop kernel: [17179608.760000] Bluetooth: L2CAP socket layer initialized
Nov 11 20:28:44 laptop sdpd[4273]: Bluetooth SDP daemon 
Nov 11 20:28:44 laptop kernel: [17179608.868000] Bluetooth: RFCOMM socket layer initialized
Nov 11 20:28:44 laptop kernel: [17179608.868000] Bluetooth: RFCOMM TTY layer initialized
Nov 11 20:28:44 laptop kernel: [17179608.868000] Bluetooth: RFCOMM ver 1.7
Nov 11 20:28:45 laptop /usr/sbin/cron[4320]: (CRON) INFO (pidfile fd = 3)
Nov 11 20:28:45 laptop /usr/sbin/cron[4321]: (CRON) STARTUP (fork ok)
Nov 11 20:28:45 laptop /usr/sbin/cron[4321]: (CRON) INFO (Running @reboot jobs)
Nov 11 20:28:56 laptop kdm_greet[4171]: Internal error: memory corruption detected
Nov 11 20:29:15 laptop hcid[4266]: name_listener_add(:1.3)
Nov 11 20:29:15 laptop hcid[4266]: Default passkey agent (:1.3, /org/bluez/passkey_agent_4548) registered
Nov 11 20:29:15 laptop kernel: [17179639.776000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
Nov 11 20:29:39 laptop kernel: [17179663.828000] psmouse.c: GlidePoint at isa0060/serio4/input0 lost synchronization, throwing 1 bytes away.
Nov 11 20:29:40 laptop kernel: [17179664.332000] psmouse.c: resync failed, issuing reconnect request
Nov 11 20:29:40 laptop kernel: [17179665.052000] input: PS/2 Mouse as /class/input/input4
Nov 11 20:29:40 laptop kernel: [17179665.064000] input: AlpsPS/2 ALPS GlidePoint as /class/input/input5
Nov 11 20:38:18 laptop dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 3463
Nov 11 20:38:18 laptop dhclient: removed stale PID file
Nov 11 20:38:18 laptop dhclient: Internet Systems Consortium DHCP Client V3.0.4
Nov 11 20:38:18 laptop dhclient: Copyright 2004-2006 Internet Systems Consortium.
Nov 11 20:38:18 laptop dhclient: All rights reserved.
Nov 11 20:38:18 laptop dhclient: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Nov 11 20:38:18 laptop dhclient: 
Nov 11 20:38:18 laptop dhclient: Listening on LPF/eth0/00:0f:b0:92:57:de
Nov 11 20:38:18 laptop dhclient: Sending on   LPF/eth0/00:0f:b0:92:57:de
Nov 11 20:38:18 laptop dhclient: Sending on   Socket/fallback
Nov 11 20:38:18 laptop dhclient: DHCPRELEASE on eth0 to 192.168.1.1 port 67
Nov 11 20:38:18 laptop kernel: [17180182.404000] ACPI: PCI interrupt for device 0000:02:01.0 disabled
Nov 11 20:38:18 laptop kernel: [17180182.444000] ACPI: PCI interrupt for device 0000:02:02.0 disabled
Nov 11 20:38:18 laptop kernel: [17180182.448000] ieee80211_crypt: unregistered algorithm 'NULL'
Nov 11 20:43:17 laptop kernel: [17180185.528000] Freezing cpus ...
Nov 11 20:43:17 laptop kernel: [17180185.528000] Stopping tasks: ==================================================================================|
Nov 11 20:43:17 laptop kernel: [17180186.476000] ACPI: PCI interrupt for device 0000:02:04.2 disabled
Nov 11 20:43:17 laptop kernel: [17180186.492000] ACPI: PCI interrupt for device 0000:02:04.0 disabled
Nov 11 20:43:17 laptop kernel: [17180186.492000] ACPI: PCI interrupt for device 0000:00:1e.2 disabled
Nov 11 20:43:17 laptop kernel: [17180186.492000] ACPI: PCI interrupt for device 0000:00:1d.7 disabled
Nov 11 20:43:17 laptop kernel: [17180186.508000] ACPI: PCI interrupt for device 0000:00:1d.3 disabled
Nov 11 20:43:17 laptop kernel: [17180186.508000] ACPI: PCI interrupt for device 0000:00:1d.2 disabled
Nov 11 20:43:17 laptop kernel: [17180186.508000] ACPI: PCI interrupt for device 0000:00:1d.1 disabled
Nov 11 20:43:17 laptop kernel: [17180186.508000] ACPI: PCI interrupt for device 0000:00:1d.0 disabled
Nov 11 20:43:17 laptop kernel: [17180186.508000] cpufreq: suspend failed to assert current frequency is what timing core thinks it is.
Nov 11 20:43:17 laptop kernel: [17180186.508000] Back to C!
Nov 11 20:43:17 laptop kernel: [17180186.508000] cpufreq: resume failed to assert current frequency is what timing core thinks it is.
Nov 11 20:43:17 laptop kernel: [17180479.508000] PM: Writing back config space on device 0000:00:01.0 at offset 7 (was d0c0, writing 2000d0c0)
Nov 11 20:43:17 laptop kernel: [17180479.508000] PM: Writing back config space on device 0000:00:01.0 at offset 1 (was 100000, writing 100407)
Nov 11 20:43:17 laptop kernel: [17180479.508000] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 169
Nov 11 20:43:17 laptop kernel: [17180479.508000] PCI: Setting latency timer of device 0000:00:01.0 to 64
Nov 11 20:43:17 laptop kernel: [17180479.508000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 209
Nov 11 20:43:17 laptop kernel: [17180479.508000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
Nov 11 20:43:17 laptop kernel: [17180479.508000] usb usb1: root hub lost power or was reset
Nov 11 20:43:17 laptop kernel: [17180479.508000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 217
Nov 11 20:43:17 laptop kernel: [17180479.508000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
Nov 11 20:43:17 laptop kernel: [17180479.508000] usb usb2: root hub lost power or was reset
Nov 11 20:43:17 laptop kernel: [17180479.508000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 201
Nov 11 20:43:17 laptop kernel: [17180479.508000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
Nov 11 20:43:17 laptop kernel: [17180479.508000] usb usb3: root hub lost power or was reset
Nov 11 20:43:17 laptop kernel: [17180479.508000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 169
Nov 11 20:43:17 laptop kernel: [17180479.508000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
Nov 11 20:43:17 laptop kernel: [17180479.508000] usb usb4: root hub lost power or was reset
Nov 11 20:43:17 laptop kernel: [17180479.524000] PCI: Enabling device 0000:00:1d.7 (0000 -> 0002)
Nov 11 20:43:17 laptop kernel: [17180479.524000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 209
Nov 11 20:43:17 laptop kernel: [17180479.524000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
Nov 11 20:43:17 laptop kernel: [17180479.524000] PM: Writing back config space on device 0000:00:1d.7 at offset 4 (was 0, writing 30000000)
Nov 11 20:43:17 laptop kernel: [17180479.524000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
Nov 11 20:43:17 laptop kernel: [17180479.524000] ACPI: PCI Interrupt 0000:00:1e.2[A] -> GSI 17 (level, low) -> IRQ 225
Nov 11 20:43:17 laptop kernel: [17180479.524000] PCI: Setting latency timer of device 0000:00:1e.2 to 64
Nov 11 20:43:17 laptop kernel: [17180479.776000] PM: Writing back config space on device 0000:00:1f.1 at offset 1 (was 2800005, writing 2880005)
Nov 11 20:43:17 laptop kernel: [17180479.776000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 201
Nov 11 20:43:17 laptop kernel: [17180479.776000] PM: Writing back config space on device 0000:01:00.0 at offset 6 (was 0, writing c0000000)
Nov 11 20:43:17 laptop kernel: [17180479.776000] PM: Writing back config space on device 0000:01:00.0 at offset 5 (was 1, writing c001)
Nov 11 20:43:17 laptop kernel: [17180479.776000] PM: Writing back config space on device 0000:01:00.0 at offset 4 (was 8, writing 90000008)
Nov 11 20:43:17 laptop kernel: [17180479.776000] PM: Writing back config space on device 0000:01:00.0 at offset 3 (was 0, writing 4)
Nov 11 20:43:17 laptop kernel: [17180479.776000] PM: Writing back config space on device 0000:01:00.0 at offset 1 (was 100000, writing 100007)
Nov 11 20:43:17 laptop kernel: [17180479.776000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 169
Nov 11 20:43:17 laptop kernel: [17180479.776000] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 20 (level, low) -> IRQ 193
Nov 11 20:43:17 laptop kernel: [17180479.776000] PM: Writing back config space on device 0000:02:01.0 at offset 5 (was 0, writing b0002000)
Nov 11 20:43:17 laptop kernel: [17180479.776000] PM: Writing back config space on device 0000:02:01.0 at offset 4 (was 1, writing a001)
Nov 11 20:43:17 laptop kernel: [17180479.776000] PM: Writing back config space on device 0000:02:01.0 at offset 3 (was 0, writing 8008)
Nov 11 20:43:17 laptop kernel: [17180479.776000] PM: Writing back config space on device 0000:02:01.0 at offset 1 (was 2b80000, writing 2b00013)
Nov 11 20:43:17 laptop kernel: [17180479.776000] PM: Writing back config space on device 0000:02:02.0 at offset f (was 18030100, writing 1803010b)
Nov 11 20:43:17 laptop kernel: [17180479.776000] PM: Writing back config space on device 0000:02:02.0 at offset 4 (was 0, writing b0001000)
Nov 11 20:43:17 laptop kernel: [17180479.776000] PM: Writing back config space on device 0000:02:02.0 at offset 3 (was 0, writing 8000)
Nov 11 20:43:17 laptop kernel: [17180479.776000] PM: Writing back config space on device 0000:02:02.0 at offset 1 (was 2900000, writing 2900002)
Nov 11 20:43:17 laptop kernel: [17180479.776000] PM: Writing back config space on device 0000:02:03.0 at offset f (was 28100100, writing 28100107)
Nov 11 20:43:17 laptop kernel: [17180479.776000] PM: Writing back config space on device 0000:02:03.0 at offset 4 (was 0, writing b0000800)
Nov 11 20:43:17 laptop kernel: [17180479.776000] PM: Writing back config space on device 0000:02:03.0 at offset 3 (was 0, writing 8000)
Nov 11 20:43:17 laptop kernel: [17180479.776000] PM: Writing back config space on device 0000:02:03.0 at offset 1 (was 2900000, writing 2900006)
Nov 11 20:43:17 laptop kernel: [17180479.776000] ACPI: PCI Interrupt 0000:02:03.0[A] -> GSI 23 (level, low) -> IRQ 209
Nov 11 20:43:17 laptop kernel: [17180479.776000] PM: Writing back config space on device 0000:02:04.0 at offset b (was 0, writing a400)
Nov 11 20:43:17 laptop kernel: [17180479.776000] PM: Writing back config space on device 0000:02:04.0 at offset 1 (was 2100003, writing 2100007)
Nov 11 20:43:17 laptop kernel: [17180479.776000] ACPI: PCI Interrupt 0000:02:04.0[A] -> GSI 16 (level, low) -> IRQ 169
Nov 11 20:43:17 laptop kernel: [17180479.776000] PM: Writing back config space on device 0000:02:04.1 at offset f (was 40102ff, writing 4010205)
Nov 11 20:43:17 laptop kernel: [17180479.776000] PM: Writing back config space on device 0000:02:04.1 at offset 4 (was 0, writing b0000000)
Nov 11 20:43:17 laptop kernel: [17180479.776000] PM: Writing back config space on device 0000:02:04.1 at offset 3 (was 800000, writing 808004)
Nov 11 20:43:17 laptop kernel: [17180479.776000] PM: Writing back config space on device 0000:02:04.1 at offset 1 (was 2100000, writing 2100006)
Nov 11 20:43:17 laptop kernel: [17180479.792000] PM: Writing back config space on device 0000:02:04.2 at offset f (was 482002ff, writing 48200205)
Nov 11 20:43:17 laptop kernel: [17180479.792000] PM: Writing back config space on device 0000:02:04.2 at offset 4 (was 0, writing b0000100)
Nov 11 20:43:17 laptop kernel: [17180479.792000] PM: Writing back config space on device 0000:02:04.2 at offset 3 (was 800000, writing 808004)
Nov 11 20:43:17 laptop kernel: [17180479.792000] PM: Writing back config space on device 0000:02:04.2 at offset 1 (was 2100000, writing 2100006)
Nov 11 20:43:17 laptop kernel: [17180479.792000] ACPI: PCI Interrupt 0000:02:04.2[B] -> GSI 17 (level, low) -> IRQ 225
Nov 11 20:43:17 laptop kernel: [17180479.832000] pnp: Device 00:07 does not support activation.
Nov 11 20:43:17 laptop kernel: [17180479.832000] pnp: Device 00:08 does not support activation.
Nov 11 20:43:17 laptop kernel: [17180481.928000] Restarting tasks... done
Nov 11 20:43:17 laptop kernel: [17180481.980000] Thawing cpus ...
Nov 11 20:43:18 laptop kernel: [17180482.584000] r8169 Gigabit Ethernet driver 2.2LK loaded
Nov 11 20:43:18 laptop kernel: [17180482.584000] ACPI: PCI Interrupt 0000:02:01.0[A] -> GSI 21 (level, low) -> IRQ 50
Nov 11 20:43:18 laptop kernel: [17180482.604000] eth0: Identified chip type is 'RTL8169s/8110s'.
Nov 11 20:43:18 laptop kernel: [17180482.604000] eth0: RTL8169 at 0xe09fe000, 00:0f:b0:92:57:de, IRQ 50
Nov 11 20:43:18 laptop kernel: [17180482.616000] ieee80211_crypt: registered algorithm 'NULL'
Nov 11 20:43:18 laptop kernel: [17180482.620000] ieee80211: 802.11 data/management/control stack, git-1.1.13
Nov 11 20:43:18 laptop kernel: [17180482.620000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
Nov 11 20:43:18 laptop kernel: [17180482.624000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.1.2kmprq
Nov 11 20:43:18 laptop kernel: [17180482.624000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
Nov 11 20:43:18 laptop kernel: [17180482.624000] Driver 'ipw2200' needs updating - please use bus_type methods
Nov 11 20:43:18 laptop kernel: [17180482.624000] ACPI: PCI Interrupt 0000:02:02.0[A] -> GSI 22 (level, low) -> IRQ 233
Nov 11 20:43:18 laptop kernel: [17180482.624000] ipw2200: Detected Intel PRO/Wireless 2915ABG Network Connection
Nov 11 20:43:18 laptop dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416
Nov 11 20:43:18 laptop dhclient: Internet Systems Consortium DHCP Client V3.0.4
Nov 11 20:43:18 laptop dhclient: Copyright 2004-2006 Internet Systems Consortium.
Nov 11 20:43:18 laptop dhclient: All rights reserved.
Nov 11 20:43:18 laptop dhclient: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Nov 11 20:43:18 laptop dhclient: 
Nov 11 20:43:18 laptop kernel: [17180482.784000] r8169: eth0: link down
Nov 11 20:43:18 laptop kernel: [17180482.784000] ipw2200: Detected geography ZZE (13 802.11bg channels, 19 802.11a channels)
Nov 11 20:43:19 laptop kernel: [17180483.244000] [drm] Loading R300 Microcode
Nov 11 20:43:19 laptop kernel: [17180483.416000] input: PS/2 Mouse as /class/input/input6
Nov 11 20:43:19 laptop kernel: [17180483.436000] input: AlpsPS/2 ALPS GlidePoint as /class/input/input7
Nov 11 20:43:19 laptop dhclient: Listening on LPF/eth0/00:0f:b0:92:57:de
Nov 11 20:43:19 laptop dhclient: Sending on   LPF/eth0/00:0f:b0:92:57:de
Nov 11 20:43:19 laptop dhclient: Sending on   Socket/fallback
Nov 11 20:43:20 laptop kernel: [17180484.004000] ACPI: Power Button (FF) [PWRF]
Nov 11 20:43:20 laptop kernel: [17180484.004000] ACPI: Lid Switch [LID0]
Nov 11 20:43:20 laptop kernel: [17180484.004000] ACPI: Power Button (CM) [PWRB]
Nov 11 20:43:20 laptop kernel: [17180484.004000] ACPI: Sleep Button (CM) [SLPB]
Nov 11 20:43:20 laptop kernel: [17180484.148000] ACPI: AC Adapter [ACAD] (off-line)
Nov 11 20:43:20 laptop kernel: [17180484.156000] r8169: eth0: link up
Nov 11 20:43:20 laptop kernel: [17180484.288000] ACPI: Battery Slot [BAT1] (battery present)
Nov 11 20:43:23 laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Nov 11 20:43:25 laptop kernel: [17180489.776000] psmouse.c: GlidePoint at isa0060/serio4/input0 lost synchronization, throwing 1 bytes away.
Nov 11 20:43:26 laptop kernel: [17180490.280000] psmouse.c: resync failed, issuing reconnect request
Nov 11 20:43:26 laptop kernel: [17180490.968000] input: PS/2 Mouse as /class/input/input8
Nov 11 20:43:26 laptop kernel: [17180490.988000] input: AlpsPS/2 ALPS GlidePoint as /class/input/input9
Nov 11 20:43:31 laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
Nov 11 20:43:31 laptop dhclient: DHCPOFFER from 192.168.1.1
Nov 11 20:43:31 laptop dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Nov 11 20:43:31 laptop dhclient: DHCPACK from 192.168.1.1
Nov 11 20:43:31 laptop dhclient: bound to 192.168.1.103 -- renewal in 127185 seconds.
Nov 11 20:43:31 laptop ntpdate[5262]: can't find host ntp.ubuntu.com 
Nov 11 20:43:31 laptop ntpdate[5262]: no servers can be used, exiting
Nov 11 20:47:29 laptop kernel: [17180733.820000] NET: Registered protocol family 10
Nov 11 20:47:29 laptop kernel: [17180733.820000] lo: Disabled Privacy Extensions
Nov 11 20:47:29 laptop kernel: [17180733.820000] IPv6 over IPv4 tunneling driver
Nov 11 20:47:40 laptop kernel: [17180744.108000] eth0: no IPv6 routers present[/SIZE]

---

### Post by DaveBorealis on 2006-11-11
> Nov 11 20:43:18 laptop dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416
Nov 11 20:43:18 laptop dhclient: Internet Systems Consortium DHCP Client V3.0.4
Nov 11 20:43:18 laptop dhclient: Copyright 2004-2006 Internet Systems Consortium.
Nov 11 20:43:18 laptop dhclient: All rights reserved.
Nov 11 20:43:18 laptop dhclient: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Nov 11 20:43:18 laptop dhclient: 
Nov 11 20:43:18 laptop kernel: [17180482.784000] r8169: eth0: link down

Hello, 
Did you try deleting the pid file listed above, and then restart dhcp?
Dave

---

### Post by msie02 on 2006-11-11
> **DaveBorealis said:**
> Hello, 
Did you try deleting the pid file listed above, and then restart dhcp?
Dave

Thanks for your reply. I tried deleting the file, which results in the generation of a new with reference to the new dhcp-pid. Still not connected to the internet. . 

/Martin

---

### Post by stream303 on 2006-11-11
Right off the bat it looks like it can't find the ntp host url.  How's your dns ie /etc/resolv.conf file?  Can you add your isp's nameservers in the Ubuntu networking tabs and see if that works - at least temporarily?

Or perhaps add your isp's dns servers in your router setup page (if you are using one...)

hope this helps..

---

### Post by msie02 on 2006-11-12
> **stream303 said:**
> Right off the bat it looks like it can't find the ntp host url.  How's your dns ie /etc/resolv.conf file?  Can you add your isp's nameservers in the Ubuntu networking tabs and see if that works - at least temporarily?


As far as I see, the dns seems fine. resolv.conf contains "212.242.40.3" and "212.242.40.51", which should be in accordance with the below output from "ipconfig /all" from my working dektop (WinXP) on the same network:

```
C:\Documents and Settings\Martin>ipconfig /all

Windows IP Configuration

        Host Name . . . . . . . . . . . . : nemesis
        Primary Dns Suffix  . . . . . . . :
        Node Type . . . . . . . . . . . . : Unknown
        IP Routing Enabled. . . . . . . . : No
        WINS Proxy Enabled. . . . . . . . : No

Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . :
        Description . . . . . . . . . . . : 3Com EtherLink XL/100PCI TX NIC(3C905B-TX)
        Physical Address. . . . . . . . . : 00-01-02-0D-5A-2D
        Dhcp Enabled. . . . . . . . . . . : Yes
        Autoconfiguration Enabled . . . . : Yes
        IP Address. . . . . . . . . . . . : 192.168.1.101
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 10.0.0.1
        DHCP Server . . . . . . . . . . . : 192.168.1.1
        DNS Servers . . . . . . . . . . . : 212.242.40.3
                                            212.242.40.51
        Lease Obtained. . . . . . . . . . : 12. november 2006 09:30:31
        Lease Expires . . . . . . . . . . : 15. november 2006 09:30:31
```

I am able to ping the DHCP server (192.168.1.1). Furthermore I just tried disabling the ipv6, through the "blacklist ipv6" - solution described in this forum, which did not help either. 

In an other (similar) thread, the following was requested:
1) ping [www.yahoo.com](www.yahoo.com)
2) ping 209.73.186.238 (the address i get for yahoo.com)

which in my case returns
1) unknown host [www.yahoo.com](www.yahoo.com)
2) Network is unreachable

So I suppose that the problem is deeper than just the DNS? Thanks for your reply

/Martin

---

### Post by stream303 on 2006-11-12
Hmmmm...  I wonder if your default gateway is correct.  Does **route -n** reveal anything?

---

### Post by msie02 on 2006-11-12
This seems to be the issue - I suppose it should have been 10.0.0.1? 

```
martin@laptop:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
```

Where do I correct this?

/Martin

---

### Post by DaveBorealis on 2006-11-12
> **msie02 said:**
> 
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0

The line looks fine, but there's a missing second line that should look like:
```
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
```
Assuming that 192.168.1.1 (your router) is your gateway.

Go to 'System->Administration->Networking' and select 'Ethernet Connection' (or do you use a modem?) and click 'Properties' and type your gateway in along with anyother missing info.  I'd go with a '255.255.255.0' mask.

Dave

---

### Post by FrodoB on 2006-11-12
How about trying:

$ sudo dhclient eth0

then what does netstat -rn reveal?

---

### Post by msie02 on 2006-11-14
> **DaveBorealis said:**
> Go to 'System->Administration->Networking' and select 'Ethernet Connection' (or do you use a modem?) and click 'Properties' and type your gateway in along with anyother missing info.  I'd go with a '255.255.255.0' mask.
Dave

Sorry for my late response -and no, I do not use a modem. The above mentioned attempt yields the same result, the line with the gateway IP does not appear (at "route -n"). I think that we can conclude that the gateway is not set properly -right?

However, I tried connecting to a friends router, which worked straight out of the box. As far as I remember, the gateway and the DHCP server was on the same IP address - does this make sense, or do I remember wrong? In my case they are not on the same IP - can this cause the problems? 

For clarification my setup is as follows
```
   
   -----------------  ----------   --------
--|ADSL modem|--|switch|--|laptop|
   -----------------  ----------   --------
                    |
                    |
                 ---------
                |desktop|
                 ---------

```That is, both of my computers are connected to the ADSL modem through a standard (noname) 100Mbit ethernet switch. The ADSL modem is a Zyxel 660HW.

Googling on this combination doesn't indicate any general/known issues.

Thanks
Martin

---

### Post by DaveBorealis on 2006-11-14
> **msie02 said:**
> As far as I remember, the gateway and the DHCP server was on the same IP address

That would make a difference.  Whichever one got the IP first would have it, and the other would have no network connection.  Assuming that the gateway and DHCP are on separate ethernet cards.  If so, and if your gateway is not showing up, give it a new IP.

And these are all on the same network, right?  In other words, they all start with 192.168.1.X?

Dave

---

### Post by msie02 on 2006-11-15
I am not sure I understand what you are saying. There are two different networks, upon which I will try to clarify in the following:

> Net1 - mine, where the laptop does NOT achieve connection to the internet. It is based on an ADSL modem (Zyxel 660HW), incorporating a WLAN access point (however the laptop is connected through ethernet). This is the unit that ought to connect me to the internet, and includes the following specs (obatined from ipconfig /all from Windows in a dual boot configuration)

Subnet Mask . . . . . . . . . . . : 255.255.255.0
Default Gateway . . . . . . . . . : 10.0.0.1
DHCP Server . . . . . . . . . . . : 192.168.1.1
DNS Servers . . . . . . . . . . . : 212.242.40.3, 212.242.40.51

The result of a route -n on this network returns:
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0

and an attempt to manually add the gateway:
martin@laptop:~$ sudo route add gw 10.0.0.1
gw: Host name lookup failure


> Net2 - friends, where the laptop does achieve the connection to the internet. It is also based on an ADSL modem (Dlink - something), which also incorporates WLAN access point. The "route -n" on this network returns:

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0

Both networks are hence based on all-in-one ADSL gateways incorporating DHCP server, gateway etc. The internet connection is supplied by my company, and unfortunately I can not log into my router for configuration. DaveBorealis, I assume your comment does not really apply in this conofiguration?

So the Million dollar question is: Why doesn't the laptop achieve internet connection in Net1, when it works straight out of the box in Net2?

Thanks for all your comments, they are highly appreciated. . .

---

### Post by DaveBorealis on 2006-11-15
You have a net1 (192.168.1.x) that connects to net2 (192.168.0.x) that connects to either a net3 10.0.0.x network or to the internet.

Your computer (a 192.168.1.x) would have to connect to router1's ethernet card with an IP of 192.168.1.1, and that same router would then have to have a second ethernet card with a valid 192.168.0.x IP.

So you would ' sudo route add gw 192.168.1.1' to connect with router1.  Router1 would then be a client on the 192.168.0.x net2, and connect with router2's ethernet card at 192.168.0.1, and router2's second ethernet card would have the IP 10.0.0.x and connect with router3's 10.0.0.1.  Etc. to the internet.

So to make this long story short, all you have to do is connect with your own gateway/router, the 192.168.1.1, and it and the other gateway/routers will handle it form there.

[edit] In rereading you previous post, I think I still don't understand your set up.  Please disregard this posting as I think it doesn't apply. But I'll leave it as is in case I was getting close!

Sorry,
Dave

---

### Post by msie02 on 2006-11-16
Ok, it seems as I contribute with even more confusion at each attempt of clarification :-). First of all, the two nets are completely independent LANs, which are both connected to the internet through each their own gateway/router. I have no intention of connecting the two nets - only to connect to the internet from net1 (achieve response when for instance pinging google). At net1 (my own), I do not achieve internet connection, whereas at net2 (a friends) I do achieve internet connection. By the sentence, used in a previous post

> "However, I tried connecting to a friends router, which worked straight out of the box"

I do not mean that I connected to net2 from net1. What I meant, was that I went to my friends place, plugged my laptop to his router/gateway, and achieved internet connection. My point in this is that, perhaps some configuration in the router/gateway at net1 results prevents the laptop from achieving internet connection. 

Again, my goal is to achieve internet connection from net1, which works out of the box in Windows, and not in Ubuntu. Perhaps we should forget about net2, and focus on net1 which ought to connect me to the internet through an ADSL modem/router, configured with the following:
```
Subnet Mask . . . . . . . . . . . : 255.255.255.0
Default Gateway . . . . . . . .  : 10.0.0.1
DHCP Server . . . . . . . . . . . : 192.168.1.1
DNS Servers . . . . . . . . . . . : 212.242.40.3, 212.242.40.51
```

The result of a route -n on this network returns:
```
Kernel IP routing table
Destination Gateway Genmask Flags Metric Ref Use Iface
192.168.1.0 0.0.0.0 255.255.255.0 U 0 0 0 eth0
```

Are the setup clear now?

Br,
Martin

---

