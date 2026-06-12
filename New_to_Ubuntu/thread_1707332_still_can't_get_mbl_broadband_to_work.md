---
title: "still can't get mbl broadband to work"
date: 2011-03-15
forum: New to Ubuntu
---

### Post by dingo dog on 2011-03-15
Hi there. I have followed your advice on this forum re getting Optus prepaid Mobile Broadband to work & still no go. I use  Ubuntu 10.04 & can't get a network connection although signal strength is strong. Anything I may be overlooking? (it's like the modem is not recognized by the laptop) Thanks in advance. DDog

---

### Post by aussielinuxguy on 2011-03-15
dingo dog,

 I have 3 Pre Paid Mobile Broadband and it works good.

Did you go to the network connection on the task bar to setup your connection ?

Right click on it and click on edit connections, then up top click on mobile broadband then  add  ?

---

### Post by dingo dog on 2011-03-15
Yep, same as other forum users advice. I typed in my username/password for my current ISP. Do I tick the mPPe box anyone?

---

### Post by aussielinuxguy on 2011-03-15
If you are using a optus broadband dongle, your laptop should see it.

Maybe one of the experts might be able to help you out.

---

### Post by Hippytaff on 2011-03-15
I'm not an expert but it sounds like the wireless device is being recognised as a mass storage device. Can you open a terminal (CTRL+ALT+T) and post the output of```
lsusb
``` with the dongle plugged in. Remove the dongle, put it back in and post the results of```
dmesg | tail
```
to varify if this is the case :-)

---

### Post by dingo dog on 2011-03-15
***Plugged In***

Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 03f0:171d Hewlett-Packard Wireless (Bluetooth + WLAN) Interface [Integrated Module]
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 005: ID 12d1:1446 Huawei Technologies Co., Ltd. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

***plugged in/taken out & plugged back in***


[    0.573339] ACPI: Thermal Zone [CPUZ] (55 C)
[    0.577749] thermal LNXTHERM:03: registered as thermal_zone2
[    0.577757] ACPI: Thermal Zone [SKNZ] (45 C)
[    0.591079] thermal LNXTHERM:04: registered as thermal_zone3
[    0.591086] ACPI: Thermal Zone [BATZ] (28 C)
[    0.597459] thermal LNXTHERM:05: registered as thermal_zone4
[    0.597467] ACPI: Thermal Zone [FDTZ] (20 C)
[    0.598995] Linux agpgart interface v0.103
[    0.599032] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.600362] brd: module loaded
[    0.600853] loop: module loaded
[    0.600937] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    0.601397] Fixed MDIO Bus: probed
[    0.601431] PPP generic driver version 2.4.2
[    0.601461] tun: Universal TUN/TAP device driver, 1.6
[    0.601463] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.601540] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.601564]   alloc irq_desc for 19 on node -1
[    0.601566]   alloc kstat_irqs on node -1
[    0.601572] ehci_hcd 0000:00:1a.7: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.601585] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    0.601589] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    0.601622] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    0.601664] ehci_hcd 0000:00:1a.7: debug port 1
[    0.605537] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    0.605552] ehci_hcd 0000:00:1a.7: irq 19, io mem 0x98904c00
[    0.620017] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    0.620109] usb usb1: configuration #1 chosen from 1 choice
[    0.620137] hub 1-0:1.0: USB hub found
[    0.620144] hub 1-0:1.0: 6 ports detected
[    0.620209]   alloc irq_desc for 20 on node -1
[    0.620210]   alloc kstat_irqs on node -1
[    0.620215] ehci_hcd 0000:00:1d.7: PCI INT D -> GSI 20 (level, low) -> IRQ 20
[    0.620226] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.620229] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.620260] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    0.620290] ehci_hcd 0000:00:1d.7: debug port 1
[    0.624182] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.624197] ehci_hcd 0000:00:1d.7: irq 20, io mem 0x98904800
[    0.640021] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.640091] usb usb2: configuration #1 chosen from 1 choice
[    0.640120] hub 2-0:1.0: USB hub found
[    0.640127] hub 2-0:1.0: 6 ports detected
[    0.640184] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.640198] uhci_hcd: USB Universal Host Controller Interface driver
[    0.640221] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.640228] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    0.640232] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    0.640265] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    0.640302] uhci_hcd 0000:00:1a.0: irq 16, io base 0x000070c0
[    0.640391] usb usb3: configuration #1 chosen from 1 choice
[    0.640417] hub 3-0:1.0: USB hub found
[    0.640423] hub 3-0:1.0: 2 ports detected
[    0.640469] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.640475] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    0.640479] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    0.640519] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    0.640558] uhci_hcd 0000:00:1a.1: irq 17, io base 0x000070a0
[    0.640652] usb usb4: configuration #1 chosen from 1 choice
[    0.640717] hub 4-0:1.0: USB hub found
[    0.640724] hub 4-0:1.0: 2 ports detected
[    0.640770] uhci_hcd 0000:00:1a.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.640776] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[    0.640780] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    0.640814] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
[    0.640850] uhci_hcd 0000:00:1a.2: irq 18, io base 0x00007080
[    0.640942] usb usb5: configuration #1 chosen from 1 choice
[    0.640968] hub 5-0:1.0: USB hub found
[    0.640975] hub 5-0:1.0: 2 ports detected
[    0.641024] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.641030] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.641034] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.641063] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
[    0.641093] uhci_hcd 0000:00:1d.0: irq 20, io base 0x00007060
[    0.641181] usb usb6: configuration #1 chosen from 1 choice
[    0.641208] hub 6-0:1.0: USB hub found
[    0.641215] hub 6-0:1.0: 2 ports detected
[    0.641264]   alloc irq_desc for 22 on node -1
[    0.641266]   alloc kstat_irqs on node -1
[    0.641270] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 22 (level, low) -> IRQ 22
[    0.641277] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.641280] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.641310] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
[    0.641346] uhci_hcd 0000:00:1d.1: irq 22, io base 0x00007040
[    0.641436] usb usb7: configuration #1 chosen from 1 choice
[    0.641461] hub 7-0:1.0: USB hub found
[    0.641467] hub 7-0:1.0: 2 ports detected
[    0.641515] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.641522] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.641525] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.641554] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
[    0.641582] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00007020
[    0.641670] usb usb8: configuration #1 chosen from 1 choice
[    0.641695] hub 8-0:1.0: USB hub found
[    0.641701] hub 8-0:1.0: 2 ports detected
[    0.641806] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.643383] i8042.c: Detected active multiplexing controller, rev 1.1.
[    0.644150] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.644156] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    0.644159] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    0.644162] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    0.644165] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    0.644245] mice: PS/2 mouse device common for all mice
[    0.644374] rtc_cmos 00:08: RTC can wake from S4
[    0.644412] rtc_cmos 00:08: rtc core: registered rtc_cmos as rtc0
[    0.644443] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    0.644562] device-mapper: uevent: version 1.0.3
[    0.644683] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
[    0.644774] device-mapper: multipath: version 1.1.0 loaded
[    0.644777] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.645024] cpuidle: using governor ladder
[    0.645160] cpuidle: using governor menu
[    0.645499] TCP cubic registered
[    0.645635] NET: Registered protocol family 10
[    0.646094] lo: Disabled Privacy Extensions
[    0.646353] NET: Registered protocol family 17
[    0.647241] PM: Resume from disk failed.
[    0.647255] registered taskstats version 1
[    0.647970]   Magic number: 3:856:531
[    0.648096] rtc_cmos 00:08: setting system clock to 2011-03-15 12:30:18 UTC (1300192218)
[    0.648099] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.648101] EDD information not available.
[    0.668696] Freeing unused kernel memory: 880k freed
[    0.669045] Write protecting the kernel read-only data: 7700k
[    0.669113] ACPI: Battery Slot [BAT0] (battery present)
[    0.672987] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    0.685070] udev: starting version 151
[    0.776092] ahci 0000:00:1f.2: version 3.0
[    0.776115]   alloc irq_desc for 21 on node -1
[    0.776117]   alloc kstat_irqs on node -1
[    0.776124] ahci 0000:00:1f.2: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    0.776170]   alloc irq_desc for 29 on node -1
[    0.776171]   alloc kstat_irqs on node -1
[    0.776182] ahci 0000:00:1f.2: irq 29 for MSI/MSI-X
[    0.776244] ahci: SSS flag set, parallel bus scan disabled
[    0.776278] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 4 ports 3 Gbps 0x23 impl SATA mode
[    0.776282] ahci 0000:00:1f.2: flags: 64bit ncq sntf stag pm led clo pio slum part ccc ems 
[    0.776288] ahci 0000:00:1f.2: setting latency timer to 64
[    0.806655] sky2 driver version 1.25
[    0.806745] sky2 0000:85:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.806796] sky2 0000:85:00.0: setting latency timer to 64
[    0.806906] sky2 0000:85:00.0: Yukon-2 FE+ chip revision 0
[    0.807451]   alloc irq_desc for 30 on node -1
[    0.807454]   alloc kstat_irqs on node -1
[    0.807533] sky2 0000:85:00.0: irq 30 for MSI/MSI-X
[    0.831695] sky2 eth0: addr 00:24:81:4b:bb:d6
[    0.840241] scsi0 : ahci
[    0.840382] scsi1 : ahci
[    0.840442] scsi2 : ahci
[    0.840503] scsi3 : ahci
[    0.840575] scsi4 : ahci
[    0.840633] scsi5 : ahci
[    0.840885] ata1: SATA max UDMA/133 abar m2048@0x98904000 port 0x98904100 irq 29
[    0.840889] ata2: SATA max UDMA/133 abar m2048@0x98904000 port 0x98904180 irq 29
[    0.840891] ata3: DUMMY
[    0.840892] ata4: DUMMY
[    0.840893] ata5: DUMMY
[    0.840896] ata6: SATA max UDMA/133 abar m2048@0x98904000 port 0x98904380 irq 29
[    1.060215] usb 2-6: new high speed USB device using ehci_hcd and address 2
[    1.190059] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.191080] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[    1.191299] ata1.00: ATA-8: Hitachi HTS543216L9A300, FB2OC40F, max UDMA/100
[    1.191302] ata1.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.192508] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[    1.192749] ata1.00: configured for UDMA/100
[    1.210665] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS54321 FB2O PQ: 0 ANSI: 5
[    1.210862] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.210940] sd 0:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    1.210987] sd 0:0:0:0: [sda] Write Protect is off
[    1.210990] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.211014] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.211144]  sda:
[    1.212513] usb 2-6: configuration #1 chosen from 1 choice
[    1.219265] Initializing USB Mass Storage driver...
[    1.219393] scsi6 : SCSI emulation for USB Mass Storage devices
[    1.219541] usb-storage: device found at 2
[    1.219543] usb-storage: waiting for device to settle before scanning
[    1.219571] scsi7 : SCSI emulation for USB Mass Storage devices
[    1.219647] usbcore: registered new interface driver usb-storage
[    1.219649] USB Mass Storage support registered.
[    1.219655] usb-storage: device found at 2
[    1.219656] usb-storage: waiting for device to settle before scanning
[    1.233605]  sda1 sda2 < sda5 >
[    1.255133] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.491460] usb 3-1: new full speed USB device using uhci_hcd and address 2
[    1.665555] usb 3-1: configuration #1 chosen from 1 choice
[    1.960210] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.973239] ata2.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[    1.973243] ata2.00: ATAPI: Optiarc DVD RW AD-7561S, AH03, max UDMA/100
[    1.987179] ata2.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[    1.987194] ata2.00: configured for UDMA/100
[    2.001272] scsi 1:0:0:0: CD-ROM            Optiarc  DVD RW AD-7561S  AH03 PQ: 0 ANSI: 5
[    2.006994] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.006998] Uniform CD-ROM driver Revision: 3.20
[    2.007173] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.007261] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.351469] ata6: SATA link down (SStatus 0 SControl 300)
[    2.651973] kjournald starting.  Commit interval 5 seconds
[    2.651999] EXT3-fs: mounted filesystem with ordered data mode.
[    6.210688] usb-storage: device scan complete
[    6.210988] usb-storage: device scan complete
[    6.211753] scsi 6:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2
[    6.211964] scsi 7:0:0:0: Direct-Access     HUAWEI   SD Storage       2.31 PQ: 0 ANSI: 2
[    6.215831] sr1: scsi-1 drive
[    6.215941] sr 6:0:0:0: Attached scsi CD-ROM sr1
[    6.215998] sr 6:0:0:0: Attached scsi generic sg2 type 5
[    6.216176] sd 7:0:0:0: Attached scsi generic sg3 type 0
[    6.217827] sd 7:0:0:0: [sdb] Attached SCSI removable disk
[   23.522307] Adding 5743196k swap on /dev/sda5.  Priority:-1 extents:1 across:5743196k 
[   23.527902] udev: starting version 151
[   23.541056] lp: driver loaded but no devices found
[   23.622268] agpgart-intel 0000:00:00.0: Intel Mobile Intel® GM45 Express Chipset
[   23.622863] agpgart-intel 0000:00:00.0: detected 65532K stolen memory
[   23.757552] EXT3 FS on sda1, internal journal
[   23.828932] [drm] Initialized drm 1.1.0 20060810
[   23.847258] lis3lv02d: hardware type NC653x found.
[   23.848058] lis3lv02d: 1-byte sensor found
[   23.853474] Bluetooth: Core ver 2.15
[   23.857575] NET: Registered protocol family 31
[   23.857578] Bluetooth: HCI device and connection manager initialized
[   23.857581] Bluetooth: HCI socket layer initialized
[   23.859328] Bluetooth: Generic Bluetooth USB driver ver 0.6
[   23.859484] usbcore: registered new interface driver btusb
[   23.861056] cfg80211: Calling CRDA to update world regulatory domain
[   23.887572] input: ST LIS3LV02DL Accelerometer as /devices/platform/lis3lv02d/input/input5
[   23.887684] Registered led device: hp::hddprotect
[   23.887712] lis3lv02d driver loaded.
[   23.892420] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0x80000000
[   23.925564] cfg80211: World regulatory domain updated:
[   23.925568]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   23.925571]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   23.925574]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   23.925577]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   23.925579]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   23.925582]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   23.941802] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
[   23.941806] iwlagn: Copyright(c) 2003-2009 Intel Corporation
[   23.941929] iwlagn 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   23.941959] iwlagn 0000:02:00.0: setting latency timer to 64
[   23.942023] iwlagn 0000:02:00.0: Detected Intel Wireless WiFi Link 5100AGN REV=0x54
[   23.949151] type=1505 audit(1300192241.793:2):  operation="profile_load" pid=793 name="/sbin/dhclient3"
[   23.949879] type=1505 audit(1300192241.793:3):  operation="profile_load" pid=793 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   23.950284] type=1505 audit(1300192241.793:4):  operation="profile_load" pid=793 name="/usr/lib/connman/scripts/dhclient-script"
[   23.951774] type=1505 audit(1300192241.803:5):  operation="profile_replace" pid=813 name="/sbin/dhclient3"
[   23.952505] type=1505 audit(1300192241.803:6):  operation="profile_replace" pid=813 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   23.952909] type=1505 audit(1300192241.803:7):  operation="profile_replace" pid=813 name="/usr/lib/connman/scripts/dhclient-script"
[   23.963307] type=1505 audit(1300192241.813:8):  operation="profile_load" pid=823 name="/usr/sbin/ntpd"
[   23.966317] type=1505 audit(1300192241.813:9):  operation="profile_replace" pid=822 name="/usr/sbin/ntpd"
[   23.982361] iwlagn 0000:02:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[   23.982519]   alloc irq_desc for 31 on node -1
[   23.982521]   alloc kstat_irqs on node -1
[   23.982542] iwlagn 0000:02:00.0: irq 31 for MSI/MSI-X
[   23.993377] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   23.993384] i915 0000:00:02.0: setting latency timer to 64
[   24.009334] phy0: Selected rate control algorithm 'iwl-agn-rs'
[   24.021721]   alloc irq_desc for 32 on node -1
[   24.021724]   alloc kstat_irqs on node -1
[   24.021734] i915 0000:00:02.0: irq 32 for MSI/MSI-X
[   24.021742] [drm] set up 63M of stolen space
[   24.521505] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x1a0b1, caps: 0xa04711/0x200000
[   24.561619] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input6
[   24.579287] type=1505 audit(1300192242.423:10):  operation="profile_load" pid=972 name="/usr/share/gdm/guest-session/Xsession"
[   24.579500] type=1505 audit(1300192242.423:11):  operation="profile_replace" pid=973 name="/sbin/dhclient3"
[   24.651516] iwlagn 0000:02:00.0: firmware: requesting iwlwifi-5000-2.ucode
[   24.738329] iwlagn 0000:02:00.0: loaded firmware version 8.24.2.12
[   24.802406] Bluetooth: L2CAP ver 2.14
[   24.802412] Bluetooth: L2CAP socket layer initialized
[   24.808661] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   24.808664] Bluetooth: BNEP filters: protocol multicast
[   24.815114] Bridge firewalling registered
[   24.865735] fb0: inteldrmfb frame buffer device
[   24.865739] registered panic notifier
[   24.872313] acpi device:03: registered as cooling_device7
[   24.873498] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input7
[   24.873635] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   24.873973] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   24.877189] vga16fb: initializing
[   24.877194] vga16fb: mapped to 0xffff8800000a0000
[   24.877197] vga16fb: not registering due to another framebuffer present
[   24.883917] HDA Intel 0000:00:1b.0: power state changed by ACPI to D0
[   24.883979] HDA Intel 0000:00:1b.0: power state changed by ACPI to D0
[   24.883990] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   24.884033] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   24.893861] ppdev: user-space parallel port driver
[   24.897850] Registered led device: iwl-phy0::radio
[   24.898573] Registered led device: iwl-phy0::assoc
[   24.899254] Registered led device: iwl-phy0::RX
[   24.899921] Registered led device: iwl-phy0::TX
[   24.920669] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   24.926380] sky2 eth0: enabling interface
[   24.926696] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   24.968665] Bluetooth: SCO (Voice Link) ver 0.6
[   24.968668] Bluetooth: SCO socket layer initialized
[   25.083607] Bluetooth: RFCOMM TTY layer initialized
[   25.083612] Bluetooth: RFCOMM socket layer initialized
[   25.083614] Bluetooth: RFCOMM ver 1.11
[   25.203127] Console: switching to colour frame buffer device 160x50
[   25.407484] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input8
[   25.478079] CPU0 attaching NULL sched-domain.
[   25.478085] CPU1 attaching NULL sched-domain.
[   25.530251] CPU0 attaching sched-domain:
[   25.530257]  domain 0: span 0-1 level MC
[   25.530260]   groups: 0 1
[   25.530266] CPU1 attaching sched-domain:
[   25.530268]  domain 0: span 0-1 level MC
[   25.530270]   groups: 1 0
[   30.916902] CPU0 attaching NULL sched-domain.
[   30.916908] CPU1 attaching NULL sched-domain.
[   30.971408] CPU0 attaching sched-domain:
[   30.971417]  domain 0: span 0-1 level MC
[   30.971421]   groups: 0 1
[   30.971431] CPU1 attaching sched-domain:
[   30.971434]  domain 0: span 0-1 level MC
[   30.971438]   groups: 1 0
[   57.173216] ISO 9660 Extensions: Microsoft Joliet Level 1
[   57.211098] ISOFS: changing to secondary root
[   58.916070] wlan0: deauthenticating from 94:44:52:aa:28:d8 by local choice (reason=3)
[   58.916162] wlan0: direct probe to AP 94:44:52:aa:28:d8 (try 1)
[   59.111284] wlan0: direct probe to AP 94:44:52:aa:28:d8 (try 2)
[   59.114884] wlan0: direct probe responded
[   59.114891] wlan0: authenticate with AP 94:44:52:aa:28:d8 (try 1)
[   59.123510] wlan0: authenticated
[   59.123558] wlan0: associate with AP 94:44:52:aa:28:d8 (try 1)
[   59.140374] wlan0: RX AssocResp from 94:44:52:aa:28:d8 (capab=0x411 status=0 aid=4)
[   59.140379] wlan0: associated
[   59.142189] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   59.205625] Intel AES-NI instructions are not detected.
[   59.241431] padlock: VIA PadLock not detected.
[   69.260019] wlan0: no IPv6 routers present
[   76.019874] cfg80211: Found new beacon on frequency: 5220 MHz (Ch 44) on phy0
[  386.494382] usb 2-6: USB disconnect, address 2
[  386.548785] scsi 6:0:0:0: rejecting I/O to dead device
[  400.590273] usb 2-6: new high speed USB device using ehci_hcd and address 3
[  400.743855] usb 2-6: configuration #1 chosen from 1 choice
[  400.757602] scsi8 : SCSI emulation for USB Mass Storage devices
[  400.759802] usb-storage: device found at 3
[  400.759806] usb-storage: waiting for device to settle before scanning
[  400.762429] scsi9 : SCSI emulation for USB Mass Storage devices
[  400.764492] usb-storage: device found at 3
[  400.764496] usb-storage: waiting for device to settle before scanning
[  405.751059] usb-storage: device scan complete
[  405.752035] scsi 8:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2
[  405.760449] sr1: scsi-1 drive
[  405.760877] sr 8:0:0:0: Attached scsi CD-ROM sr1
[  405.761079] sr 8:0:0:0: Attached scsi generic sg2 type 5
[  405.761256] usb-storage: device scan complete
[  405.761965] scsi 9:0:0:0: Direct-Access     HUAWEI   SD Storage       2.31 PQ: 0 ANSI: 2
[  405.762899] sd 9:0:0:0: Attached scsi generic sg3 type 0
[  405.772660] sd 9:0:0:0: [sdb] Attached SCSI removable disk
[  418.080898] ISO 9660 Extensions: Microsoft Joliet Level 1
[  418.081783] ISOFS: changing to secondary root
[ 1507.638221] __ratelimit: 30 callbacks suppressed
[ 1507.638229] type=1503 audit(1300193725.683:22):  operation="open" pid=2280 parent=1 profile="/usr/bin/evince" requested_mask="r::" denied_mask="r::" fsuid=1001 ouid=1001 name=2F6D656469612F4F70747573204D6F62696C652F537461727475702E69636F
[ 1507.647462] type=1503 audit(1300193725.693:23):  operation="open" pid=2280 parent=1 profile="/usr/bin/evince" requested_mask="r::" denied_mask="r::" fsuid=1001 ouid=1001 name=2F6D656469612F4F70747573204D6F62696C652F537461727475702E69636F
[ 1507.676610] type=1503 audit(1300193725.723:24):  operation="open" pid=2280 parent=1 profile="/usr/bin/evince" requested_mask="r::" denied_mask="r::" fsuid=1001 ouid=1001 name=2F6D656469612F4F70747573204D6F62696C652F537461727475702E69636F
[ 1507.695369] type=1503 audit(1300193725.743:25):  operation="open" pid=2280 parent=1 profile="/usr/bin/evince" requested_mask="r::" denied_mask="r::" fsuid=1001 ouid=1001 name=2F6D656469612F4F70747573204D6F62696C652F537461727475702E69636F
[ 1507.720777] type=1503 audit(1300193725.773:26):  operation="open" pid=2280 parent=1 profile="/usr/bin/evince" requested_mask="r::" denied_mask="r::" fsuid=1001 ouid=1001 name=2F6D656469612F4F70747573204D6F62696C652F537461727475702E69636F
[ 1765.382324] usb 2-6: USB disconnect, address 3
[ 1775.180142] usb 2-2: new high speed USB device using ehci_hcd and address 4
[ 1775.334189] usb 2-2: configuration #1 chosen from 1 choice
[ 1775.336169] scsi10 : SCSI emulation for USB Mass Storage devices
[ 1775.336689] usb-storage: device found at 4
[ 1775.336694] usb-storage: waiting for device to settle before scanning
[ 1775.336765] scsi11 : SCSI emulation for USB Mass Storage devices
[ 1775.337108] usb-storage: device found at 4
[ 1775.337113] usb-storage: waiting for device to settle before scanning
[ 1780.331345] usb-storage: device scan complete
[ 1780.331512] usb-storage: device scan complete
[ 1780.332659] scsi 10:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2
[ 1780.332872] scsi 11:0:0:0: Direct-Access     HUAWEI   SD Storage       2.31 PQ: 0 ANSI: 2
[ 1780.341114] sr1: scsi-1 drive
[ 1780.343024] sr 10:0:0:0: Attached scsi CD-ROM sr1
[ 1780.344622] sr 10:0:0:0: Attached scsi generic sg2 type 5
[ 1780.345201] sd 11:0:0:0: Attached scsi generic sg3 type 0
[ 1780.354566] sd 11:0:0:0: [sdb] Attached SCSI removable disk
[ 1790.221610] wlan0: deauthenticating from 94:44:52:aa:28:d8 by local choice (reason=3)
[ 1791.092631] ISO 9660 Extensions: Microsoft Joliet Level 1
[ 1791.093498] ISOFS: changing to secondary root
[ 2012.161509] sky2 eth0: disabling interface
[ 2016.227956] Registered led device: iwl-phy0::radio
[ 2016.228003] Registered led device: iwl-phy0::assoc
[ 2016.228061] Registered led device: iwl-phy0::RX
[ 2016.228104] Registered led device: iwl-phy0::TX
[ 2016.263107] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2016.270968] sky2 eth0: enabling interface
[ 2016.271875] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 2019.517797] wlan0: deauthenticating from 94:44:52:aa:28:d8 by local choice (reason=3)
[ 2019.556379] wlan0: direct probe to AP 94:44:52:aa:28:d8 (try 1)
[ 2019.560210] wlan0: direct probe responded
[ 2019.560220] wlan0: authenticate with AP 94:44:52:aa:28:d8 (try 1)
[ 2019.562029] wlan0: authenticated
[ 2019.562107] wlan0: associate with AP 94:44:52:aa:28:d8 (try 1)
[ 2019.565932] wlan0: RX AssocResp from 94:44:52:aa:28:d8 (capab=0x411 status=0 aid=4)
[ 2019.565940] wlan0: associated
[ 2019.571741] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 2030.390185] wlan0: no IPv6 routers present
[ 2094.478130] usb 2-2: USB disconnect, address 4
[ 2094.539452] scsi 10:0:0:0: rejecting I/O to dead device
[ 2108.960241] usb 2-5: new high speed USB device using ehci_hcd and address 5
[ 2109.114819] usb 2-5: configuration #1 chosen from 1 choice
[ 2109.116904] scsi12 : SCSI emulation for USB Mass Storage devices
[ 2109.117438] usb-storage: device found at 5
[ 2109.117443] usb-storage: waiting for device to settle before scanning
[ 2109.117518] scsi13 : SCSI emulation for USB Mass Storage devices
[ 2109.118476] usb-storage: device found at 5
[ 2109.118483] usb-storage: waiting for device to settle before scanning
[ 2114.111131] usb-storage: device scan complete
[ 2114.111473] usb-storage: device scan complete
[ 2114.112428] scsi 12:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2
[ 2114.112786] scsi 13:0:0:0: Direct-Access     HUAWEI   SD Storage       2.31 PQ: 0 ANSI: 2
[ 2114.122116] sr1: scsi-1 drive
[ 2114.122448] sr 12:0:0:0: Attached scsi CD-ROM sr1
[ 2114.123374] sr 12:0:0:0: Attached scsi generic sg2 type 5
[ 2114.125105] sd 13:0:0:0: Attached scsi generic sg3 type 0
[ 2114.131810] sd 13:0:0:0: [sdb] Attached SCSI removable disk
[ 2125.103482] ISO 9660 Extensions: Microsoft Joliet Level 1
[ 2125.104356] ISOFS: changing to secondary root
[ 2437.322162] usb 2-5: USB disconnect, address 5
[ 2437.354417] scsi 12:0:0:0: rejecting I/O to dead device
[ 2556.940224] usb 2-6: new high speed USB device using ehci_hcd and address 6
[ 2557.094593] usb 2-6: configuration #1 chosen from 1 choice
[ 2557.096535] scsi14 : SCSI emulation for USB Mass Storage devices
[ 2557.097047] usb-storage: device found at 6
[ 2557.097052] usb-storage: waiting for device to settle before scanning
[ 2557.097120] scsi15 : SCSI emulation for USB Mass Storage devices
[ 2557.097474] usb-storage: device found at 6
[ 2557.097479] usb-storage: waiting for device to settle before scanning
[ 2562.091168] usb-storage: device scan complete
[ 2562.091445] usb-storage: device scan complete
[ 2562.092867] scsi 14:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2
[ 2562.092936] scsi 15:0:0:0: Direct-Access     HUAWEI   SD Storage       2.31 PQ: 0 ANSI: 2
[ 2562.103122] sr1: scsi-1 drive
[ 2562.103439] sr 14:0:0:0: Attached scsi CD-ROM sr1
[ 2562.107419] sr 14:0:0:0: Attached scsi generic sg2 type 5
[ 2562.119617] sd 15:0:0:0: Attached scsi generic sg3 type 0
[ 2562.124478] sd 15:0:0:0: [sdb] Attached SCSI removable disk
[ 2574.099161] ISO 9660 Extensions: Microsoft Joliet Level 1
[ 2574.100127] ISOFS: changing to secondary root

---

### Post by Hippytaff on 2011-03-15
This is seems to be the same problem we're having [here]("http://ubuntuforums.org/showthread.php?t=1704837&page=2") My last post (18 might be of some use to you too.

---

### Post by dingo dog on 2011-03-15
Many thanks, I'll check it out tomorrow, enough for tonight. Thanks again!

---

### Post by Hippytaff on 2011-03-15
Your welcome...let me know how it goes

---

### Post by dingo dog on 2011-03-16
I downloaded the the libsub & modeswitch tar & data. How do i get it to work. Very new at this! Thanks in advance

---

### Post by Hippytaff on 2011-03-16
I'd install it by opening a terminal and doing ```
sudo apt-get usb-modeswitch
```

It's likely that you might have to compile the contents of the tar you downloaded. Just easier this way...

---

### Post by dingo dog on 2011-03-20
[SIZE=3]E: Invalid operation usb-modeswitch
[/SIZE]
That's what I got in return, am I doing something wrong? ( i copied word-for-word your instruction)
Thanks for your help, appreciate it!

---

### Post by Hippytaff on 2011-03-20
Sorry...I missed a bit of the code
should be```
 sudo apt-get install usb-modeswitch
```

---

### Post by dingo dog on 2011-03-21
Many Thanks, works great! Appreciated your help.

---

### Post by Hippytaff on 2011-03-21
You're welcome

---

