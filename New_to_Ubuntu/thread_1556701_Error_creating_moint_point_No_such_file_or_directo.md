---
title: "Error creating moint point: No such file or directory"
date: 2010-08-19
forum: New to Ubuntu
---

### Post by fremantle on 2010-08-19
no matter which usb drive i plug in i get this 
> error creating moint point: No such file or directory

any ideas?

---

### Post by fremantle on 2010-08-19
[IMG]http://img404.imageshack.us/img404/1143/screenshotfn.png[/IMG]

ya, it says "moint"

---

### Post by AlphaLexman on 2010-08-19
An empty directory must exist before mounting to the directory!
```
mkdir /media/usb_drive
```

---

### Post by jtarin on 2010-08-19
When you encounter problems with USB devices, the first thing to do is to check the latest debug information generated from the kernel just after you plug in your device and/or just after you encounter the problem.
To do that, open a terminal and type :```
dmesg
```

---

### Post by fremantle on 2010-08-19
so what  r u guys suggesting??

---

### Post by skatinjj on 2010-08-19
> **fremantle said:**
> so what  r u guys suggesting??

Plug in your usb drive, open a terminal and run the command:

```
dmesg
```

then copy the output here.

---

### Post by fremantle on 2010-08-19
> Cpu1Cst 00003000 INTL 20050624)
bash: syntax error near unexpected token `('
abir@openforce:~$ [    0.557640] Switching to clocksource hpet
bash: [: missing `]'
abir@openforce:~$ [    0.559376] processor LNXCPU:01: registered as cooling_device1
bash: [: missing `]'
abir@openforce:~$ [    0.590388] Linux agpgart interface v0.103
bash: [: missing `]'
abir@openforce:~$ [    0.590561] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
bash: [: missing `]'
abir@openforce:~$ [    0.594986] brd: module loaded
bash: [: missing `]'
abir@openforce:~$ [    0.596871] loop: module loaded
bash: [: missing `]'
abir@openforce:~$ [    0.597266] input: Macintosh mouse button emulation as /devices/virtual/input/input3
bash: [: missing `]'
abir@openforce:~$ [    0.598793] Fixed MDIO Bus: probed
bash: [: missing `]'
abir@openforce:~$ [    0.599010] PPP generic driver version 2.4.2
bash: [: missing `]'
abir@openforce:~$ [    0.599229] tun: Universal TUN/TAP device driver, 1.6
bash: [: missing `]'
abir@openforce:~$ [    0.599310] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
bash: syntax error near unexpected token `('
abir@openforce:~$ [    0.599679] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
bash: syntax error near unexpected token `('
abir@openforce:~$ [    0.599823]   alloc irq_desc for 23 on node -1
bash: [: missing `]'
abir@openforce:~$ [    0.599831]   alloc kstat_irqs on node -1
bash: [: missing `]'
abir@openforce:~$ [    0.599849] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
bash: syntax error near unexpected token `('
abir@openforce:~$ [    0.599973] ehci_hcd 0000:00:1d.7: setting latency timer to 64
bash: [: missing `]'
abir@openforce:~$ [    0.599983] ehci_hcd 0000:00:1d.7: EHCI Host Controller
bash: [: missing `]'
abir@openforce:~$ [    0.600234] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
bash: [: missing `]'
abir@openforce:~$ [    0.600401] ehci_hcd 0000:00:1d.7: using broken periodic workaround
bash: [: missing `]'
abir@openforce:~$ [    0.600501] ehci_hcd 0000:00:1d.7: debug port 1
bash: [: missing `]'
abir@openforce:~$ [    0.604480] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
bash: [: missing `]'
abir@openforce:~$ [    0.604770] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xf0504000
bash: [: missing `]'
abir@openforce:~$ [    0.622910] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
bash: [: missing `]'
abir@openforce:~$ [    0.623513] usb usb1: configuration #1 chosen from 1 choicebash: [: missing `]'
abir@openforce:~$ [    0.624579] hub 1-0:1.0: USB hub found
bash: [: missing `]'
abir@openforce:~$ [    0.624672] hub 1-0:1.0: 8 ports detected
bash: [: missing `]'
abir@openforce:~$ [    0.624948] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
bash: syntax error near unexpected token `('
abir@openforce:~$ [    0.625074] uhci_hcd: USB Universal Host Controller Interface driver
bash: [: missing `]'
abir@openforce:~$ [    0.625255] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
bash: syntax error near unexpected token `('
abir@openforce:~$ [    0.625356] uhci_hcd 0000:00:1d.0: setting latency timer to 64
bash: [: missing `]'
abir@openforce:~$ [    0.625366] uhci_hcd 0000:00:1d.0: UHCI Host Controller
bash: [: missing `]'
abir@openforce:~$ [    0.625600] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
bash: [: missing `]'
abir@openforce:~$ [    0.625758] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001820
bash: [: missing `]'
abir@openforce:~$ [    0.626163] usb usb2: configuration #1 chosen from 1 choicebash: [: missing `]'
abir@openforce:~$ [    0.626336] hub 2-0:1.0: USB hub found
bash: [: missing `]'
abir@openforce:~$ [    0.626427] hub 2-0:1.0: 2 ports detected
bash: [: missing `]'
abir@openforce:~$ [    0.626643]   alloc irq_desc for 19 on node -1
bash: [: missing `]'
abir@openforce:~$ [    0.626651]   alloc kstat_irqs on node -1
bash: [: missing `]'
abir@openforce:~$ [    0.626668] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
bash: syntax error near unexpected token `('
abir@openforce:~$ [    0.626781] uhci_hcd 0000:00:1d.1: setting latency timer to 64
bash: [: missing `]'
abir@openforce:~$ [    0.626791] uhci_hcd 0000:00:1d.1: UHCI Host Controller
bash: [: missing `]'
abir@openforce:~$ [    0.626996] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
bash: [: missing `]'
abir@openforce:~$ [    0.627181] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001840
bash: [: missing `]'
abir@openforce:~$ [    0.627575] usb usb3: configuration #1 chosen from 1 choicebash: [: missing `]'
abir@openforce:~$ [    0.627766] hub 3-0:1.0: USB hub found
bash: [: missing `]'
abir@openforce:~$ [    0.627858] hub 3-0:1.0: 2 ports detected
bash: [: missing `]'
abir@openforce:~$ [    0.628075]   alloc irq_desc for 18 on node -1
bash: [: missing `]'
abir@openforce:~$ [    0.628083]   alloc kstat_irqs on node -1
bash: [: missing `]'
abir@openforce:~$ [    0.628101] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
bash: syntax error near unexpected token `('
abir@openforce:~$ [    0.628202] uhci_hcd 0000:00:1d.2: setting latency timer to 64
bash: [: missing `]'
abir@openforce:~$ [    0.628213] uhci_hcd 0000:00:1d.2: UHCI Host Controller
bash: [: missing `]'
abir@openforce:~$ [    0.628463] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
bash: [: missing `]'
abir@openforce:~$ [    0.628663] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001860
bash: [: missing `]'
abir@openforce:~$ [    0.629072] usb usb4: configuration #1 chosen from 1 choicebash: [: missing `]'
abir@openforce:~$ [    0.629251] hub 4-0:1.0: USB hub found
bash: [: missing `]'
abir@openforce:~$ [    0.629342] hub 4-0:1.0: 2 ports detected
bash: [: missing `]'
abir@openforce:~$ [    0.629553] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
bash: syntax error near unexpected token `('
abir@openforce:~$ [    0.629668] uhci_hcd 0000:00:1d.3: setting latency timer to 64
bash: [: missing `]'
abir@openforce:~$ [    0.629679] uhci_hcd 0000:00:1d.3: UHCI Host Controller
bash: [: missing `]'
abir@openforce:~$ [    0.629920] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
bash: [: missing `]'
abir@openforce:~$ [    0.630119] uhci_hcd 0000:00:1d.3: irq 16, io base 0x00001880
bash: [: missing `]'
abir@openforce:~$ [    0.630496] usb usb5: configuration #1 chosen from 1 choicebash: [: missing `]'
abir@openforce:~$ [    0.630688] hub 5-0:1.0: USB hub found
bash: [: missing `]'
abir@openforce:~$ [    0.630778] hub 5-0:1.0: 2 ports detected
bash: [: missing `]'
abir@openforce:~$ [    0.631120] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
bash: [: missing `]'
abir@openforce:~$ [    0.644189] serio: i8042 KBD port at 0x60,0x64 irq 1
bash: [: missing `]'
abir@openforce:~$ [    0.644382] serio: i8042 AUX port at 0x60,0x64 irq 12
bash: [: missing `]'
abir@openforce:~$ [    0.645031] mice: PS/2 mouse device common for all mice
bash: [: missing `]'
abir@openforce:~$ [    0.645533] rtc_cmos 00:04: RTC can wake from S4
bash: [: missing `]'
abir@openforce:~$ [    0.645779] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
bash: [: missing `]'
abir@openforce:~$ [    0.645912] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
bash: [: missing `]'
abir@openforce:~$ [    0.646453] device-mapper: uevent: version 1.0.3
bash: [: missing `]'
abir@openforce:~$ [    0.647021] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
bash: syntax error near unexpected token `('
abir@openforce:~$ [    0.647507] device-mapper: multipath: version 1.1.0 loaded
bash: [: missing `]'
abir@openforce:~$ [    0.647595] device-mapper: multipath round-robin: version 1.0.0 loaded
bash: [: missing `]'
abir@openforce:~$ [    0.648456] cpuidle: using governor ladder
bash: [: missing `]'
abir@openforce:~$ [    0.648899] cpuidle: using governor menu
bash: [: missing `]'
abir@openforce:~$ [    0.650184] TCP cubic registered
bash: [: missing `]'
abir@openforce:~$ [    0.650765] NET: Registered protocol family 10
bash: [: missing `]'
abir@openforce:~$ [    0.652335] lo: Disabled Privacy Extensions
bash: [: missing `]'
abir@openforce:~$ [    0.653469] NET: Registered protocol family 17
bash: [: missing `]'
abir@openforce:~$ [    0.655252] PM: Resume from disk failed.
bash: [: missing `]'
abir@openforce:~$ [    0.655292] registered taskstats version 1
bash: [: missing `]'
abir@openforce:~$ [    0.656075]   Magic number: 6:540:557
bash: [: missing `]'
abir@openforce:~$ [    0.656309] rtc_cmos 00:04: setting system clock to 2010-08-20 00:33:07 UTC (1282264387)
bash: syntax error near unexpected token `('
abir@openforce:~$ [    0.656429] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
bash: [: missing `]'
abir@openforce:~$ [    0.656513] EDD information not available.
bash: [: missing `]'
abir@openforce:~$ [    0.661153] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
bash: [: missing `]'
abir@openforce:~$ [    0.765655] Freeing initrd memory: 8150k freed
bash: [: missing `]'
abir@openforce:~$ [    0.771893] Freeing unused kernel memory: 880k freed
bash: [: missing `]'
abir@openforce:~$ [    0.772618] Write protecting the kernel read-only data: 7696k
bash: [: missing `]'
abir@openforce:~$ [    0.812857] udev: starting version 151
bash: [: missing `]'
abir@openforce:~$ [    1.003965] ACPI: Battery Slot [BAT1] (battery present)
bash: syntax error near unexpected token `('
abir@openforce:~$ [    1.027070] ahci 0000:00:1f.2: version 3.0
bash: [: missing `]'
abir@openforce:~$ [    1.027108] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
bash: syntax error near unexpected token `('
abir@openforce:~$ [    1.027271]   alloc irq_desc for 26 on node -1
bash: [: missing `]'
abir@openforce:~$ [    1.027279]   alloc kstat_irqs on node -1
bash: [: missing `]'
abir@openforce:~$ [    1.027302] ahci 0000:00:1f.2: irq 26 for MSI/MSI-X
bash: [: missing `]'
abir@openforce:~$ [    1.027424] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
bash: [: missing `]'
abir@openforce:~$ [    1.027548] ahci 0000:00:1f.2: flags: 64bit ncq pm led clo pio slum part 
bash: [: missing `]'
abir@openforce:~$ [    1.027640] ahci 0000:00:1f.2: setting latency timer to 64
bash: [: missing `]'
abir@openforce:~$ [    1.028193] scsi0 : ahci
bash: [: missing `]'
abir@openforce:~$ [    1.028639] scsi1 : ahci
bash: [: missing `]'
abir@openforce:~$ [    1.028935] scsi2 : ahci
bash: [: missing `]'
abir@openforce:~$ [    1.029215] scsi3 : ahci
bash: [: missing `]'
abir@openforce:~$ [    1.029726] ata1: SATA max UDMA/133 abar m1024@0xf0504400 port 0xf0504500 irq 26
bash: [: missing `]'
abir@openforce:~$ [    1.029844] ata2: SATA max UDMA/133 abar m1024@0xf0504400 port 0xf0504580 irq 26
bash: [: missing `]'
abir@openforce:~$ [    1.029963] ata3: SATA max UDMA/133 abar m1024@0xf0504400 port 0xf0504600 irq 26
bash: [: missing `]'
abir@openforce:~$ [    1.030097] ata4: SATA max UDMA/133 abar m1024@0xf0504400 port 0xf0504680 irq 26
bash: [: missing `]'
abir@openforce:~$ [    1.079506] r8169 Gigabit Ethernet driver 2.3LK-NAPI loadedbash: [: missing `]'
abir@openforce:~$ [    1.079638] r8169 0000:05:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
bash: syntax error near unexpected token `('
abir@openforce:~$ [    1.079807] r8169 0000:05:00.0: setting latency timer to 64bash: [: missing `]'
abir@openforce:~$ [    1.079887]   alloc irq_desc for 27 on node -1
bash: [: missing `]'
abir@openforce:~$ [    1.079895]   alloc kstat_irqs on node -1
bash: [: missing `]'
abir@openforce:~$ [    1.079925] r8169 0000:05:00.0: irq 27 for MSI/MSI-X
bash: [: missing `]'
abir@openforce:~$ [    1.081940] eth0: RTL8102e at 0xffffc900001ee000, 00:26:b9:e1:50:2c, XID 04e00000 IRQ 27
bash: [: missing `]'
abir@openforce:~$ [    1.130150] usb 1-4: new high speed USB device using ehci_hcd and address 3
bash: [: missing `]'
abir@openforce:~$ [    1.312456] usb 1-4: configuration #1 chosen from 1 choice
bash: [: missing `]'
abir@openforce:~$ [    1.372599] ata3: SATA link down (SStatus 0 SControl 300)
bash: syntax error near unexpected token `('
abir@openforce:~$ [    1.372713] ata2: SATA link down (SStatus 0 SControl 300)
bash: syntax error near unexpected token `('
abir@openforce:~$ [    1.372818] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
bash: syntax error near unexpected token `('
abir@openforce:~$ [    1.372929] ata4: SATA link down (SStatus 0 SControl 300)
bash: syntax error near unexpected token `('
abir@openforce:~$ [    1.374622] ata1.00: ATA-8: ST9250315AS, D005DEM1, max UDMA/133
bash: [: missing `]'
abir@openforce:~$ [    1.374702] ata1.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 31/32)
bash: syntax error near unexpected token `('
abir@openforce:~$ [    1.376921] ata1.00: configured for UDMA/133
bash: [: missing `]'
abir@openforce:~$ [    1.400347] scsi 0:0:0:0: Direct-Access     ATA      ST9250315AS      D005 PQ: 0 ANSI: 5
bash: [: missing `]'
abir@openforce:~$ [    1.400821] sd 0:0:0:0: Attached scsi generic sg0 type 0
bash: [: missing `]'
abir@openforce:~$ [    1.401148] sd 0:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
bash: syntax error near unexpected token `('
abir@openforce:~$ [    1.401511] sd 0:0:0:0: [sda] Write Protect is off
bash: [: missing `]'
abir@openforce:~$ [    1.401600] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
bash: [: missing `]'
abir@openforce:~$ [    1.401688] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
> [    1.402230]  sda: sda1 sda2 <
> [    1.430079] usb 1-8: new high speed USB device using ehci_hcd and address 4
> [    1.438402]  sda5 >
> [    1.439868] sd 0:0:0:0: [sda] Attached SCSI disk
> [    1.593956] usb 1-8: configuration #1 chosen from 1 choice
> [    1.615186] Initializing USB Mass Storage driver...
> [    1.615690] scsi4 : SCSI emulation for USB Mass Storage devices
> [    1.616053] usbcore: registered new interface driver usb-storage
> [    1.616156] USB Mass Storage support registered.
> [    1.616534] usb-storage: device found at 4
> [    1.616541] usb-storage: waiting for device to settle before scanning
> [    1.870054] usb 2-2: new full speed USB device using uhci_hcd and address 2
> [    1.883335] EXT4-fs (sda1): mounted filesystem with ordered data mode
> [    2.018993] usb 2-2: not running at top speed; connect to a high speed hub
> [    2.046261] usb 2-2: configuration #1 chosen from 1 choice
> [    2.049352] scsi5 : SCSI emulation for USB Mass Storage devices
> [    2.049838] usb-storage: device found at 2
> [    2.049846] usb-storage: waiting for device to settle before scanning
> [    6.610382] usb-storage: device scan complete
> [    6.612582] scsi 4:0:0:0: Direct-Access     Generic- Multi-Card       1.00 PQ: 0 ANSI: 0 CCS
> [    6.613798] sd 4:0:0:0: Attached scsi generic sg1 type 0
> [    6.618047] sd 4:0:0:0: [sdb] Attached SCSI removable disk
> [    7.041268] usb-storage: device scan complete
> [    7.044219] scsi 5:0:0:0: Direct-Access     MP3      HS USB FlashDisk 2.00 PQ: 0 ANSI: 0 CCS
> [    7.045352] sd 5:0:0:0: Attached scsi generic sg2 type 0
> [    7.050212] sd 5:0:0:0: [sdc] 1971121 512-byte logical blocks: (1.00 GB/962 MiB)
> [    7.053196] sd 5:0:0:0: [sdc] Write Protect is off
> [    7.053277] sd 5:0:0:0: [sdc] Mode Sense: 00 c0 00 00
> [    7.053283] sd 5:0:0:0: [sdc] Assuming drive cache: write through
> [    7.061192] sd 5:0:0:0: [sdc] Assuming drive cache: write through
> [    7.061282]  sdc: sdc1
> [    7.076197] sd 5:0:0:0: [sdc] Assuming drive cache: write through
> [    7.076295] sd 5:0:0:0: [sdc] Attached SCSI disk
> [   12.920366] udev: starting version 151
> [   12.975085] Adding 2966520k swap on /dev/sda5.  Priority:-1 extents:1 across:2966520k 
> [   12.995179] lp: driver loaded but no devices found
> [   13.709514] cfg80211: Calling CRDA to update world regulatory domain
> [   13.721521] agpgart-intel 0000:00:00.0: Intel IGD Chipset
> [   13.721832] agpgart-intel 0000:00:00.0: detected 8188K stolen memory
> [   13.792560] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
> [   13.801934] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
> [   13.847889] type=1505 audit(1282264400.686:2):  operation="profile_load" pid=549 name="/sbin/dhclient3"
> [   13.848624] type=1505 audit(1282264400.686:3):  operation="profile_load" pid=549 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
> [   13.849059] type=1505 audit(1282264400.686:4):  operation="profile_load" pid=549 name="/usr/lib/connman/scripts/dhclient-script"
> [   13.861811] cfg80211: World regulatory domain updated:
> [   13.861821] (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
> [   13.861831] (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
> [   13.861840] (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
> [   13.861848] (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
> [   13.861857] (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
> [   13.861866] (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
> [   13.882982] [drm] Initialized drm 1.1.0 20060810
> [   14.151520] Linux video capture interface: v2.00
> [   14.189797] ip_tables: (C) 2000-2006 Netfilter Core Team
> [   14.191242] dell-wmi: No known WMI GUID found
> [   14.246536] ath9k 0000:07:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
> [   14.246560] ath9k 0000:07:00.0: setting latency timer to 64
> [   14.296544] ath: EEPROM regdomain: 0x60
> [   14.296553] ath: EEPROM indicates we should expect a direct regpair map
> [   14.296564] ath: Country alpha2 being used: 00
> [   14.296570] ath: Regpair used: 0x60
> [   14.304666] uvcvideo: Found UVC 1.00 device Laptop_Integrated_Webcam_1.3M (064e:8101)
> [   14.357497] input: Laptop_Integrated_Webcam_1.3M as /devices/pci0000:00/0000:00:1d.7/usb1/1-4/1-4:1.0/input/input5
> [   14.357720] usbcore: registered new interface driver uvcvideo
> [   14.357733] USB Video Class driver (v0.1.0)
> [   14.468306] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
> [   14.468319] i915 0000:00:02.0: setting latency timer to 64
> [   14.538763] nf_conntrack version 0.5.0 (7917 buckets, 31668 max)
> [   14.543960] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Please use
> [   14.543972] nf_conntrack.acct=1 kernel parameter, acct=1 nf_conntrack module option or
> [   14.543980] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
> [   14.593546]   alloc irq_desc for 28 on node -1
> [   14.593557]   alloc kstat_irqs on node -1
> [   14.593580] i915 0000:00:02.0: irq 28 for MSI/MSI-X
> [   14.593597] [drm] set up 7M of stolen space
> [   14.648816] type=1505 audit(1282264401.486:5):  operation="profile_load" pid=698 name="/usr/share/gdm/guest-session/Xsession"
> [   14.699383] phy0: Selected rate control algorithm 'ath9k_rate_control'
> [   14.701664] Registered led device: ath9k-phy0::radio
> [   14.701725] Registered led device: ath9k-phy0::assoc
> [   14.701789] Registered led device: ath9k-phy0::tx
> [   14.701864] Registered led device: ath9k-phy0::rx
> [   14.701919] phy0: Atheros AR9285 MAC/BB Rev:2 AR5133 RF Rev:e0: mem=0xffffc90010580000, irq=17
> [   14.715057] type=1505 audit(1282264401.556:6):  operation="profile_replace" pid=702 name="/sbin/dhclient3"
> [   14.715795] type=1505 audit(1282264401.556:7):  operation="profile_replace" pid=702 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
> [   14.719079] type=1505 audit(1282264401.556:8):  operation="profile_replace" pid=702 name="/usr/lib/connman/scripts/dhclient-script"
> [   14.723416] [drm] initialized overlay support
> [   14.777788] r8169: eth0: link down
> [   14.778964] ADDRCONF(NETDEV_UP): eth0: link is not ready
> [   14.829048] type=1505 audit(1282264401.666:9):  operation="profile_load" pid=703 name="/usr/bin/evince"
> [   14.889833] type=1505 audit(1282264401.726:10):  operation="profile_load" pid=703 name="/usr/bin/evince-previewer"
> [   14.913821] type=1505 audit(1282264401.756:11):  operation="profile_load" pid=703 name="/usr/bin/evince-thumbnailer"
> [   14.972406] ip6_tables: (C) 2000-2006 Netfilter Core Team
> [   15.003078] Synaptics Touchpad, model: 1, fw: 7.4, id: 0x1e0b1, caps: 0xd04711/0xa40000
> [   15.084505] ADDRCONF(NETDEV_UP): wlan0: link is not ready
> [   15.110527] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input6
> [   15.289596] fb0: inteldrmfb frame buffer device
> [   15.289605] registered panic notifier
> [   15.295862] acpi device:00: registered as cooling_device2
> [   15.299054] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input7
> [   15.299512] ACPI: Video Device [IGD0] (multi-head: yes  rom: no  post: no)
> [   15.301927] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
> [   15.330079] vga16fb: initializing
> [   15.330090] vga16fb: mapped to 0xffff8800000a0000
> [   15.330101] vga16fb: not registering due to another framebuffer present
> [   15.355600]   alloc irq_desc for 22 on node -1
> [   15.355610]   alloc kstat_irqs on node -1
> [   15.355629] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
> [   15.355730] HDA Intel 0000:00:1b.0: setting latency timer to 64
> [   15.386909] [drm] Big FIFO is enabled
> [   15.490273] [drm] Big FIFO is enabled
> [   15.490300] [drm] Big FIFO is enabled
> [   15.490418] [drm] Big FIFO is enabled
> [   15.541931] [drm] Big FIFO is enabled
> [   15.542111] Console: switching to colour frame buffer device 128x37
> [   15.553653] hda_codec: ALC272: BIOS auto-probing.
> [   15.555223] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input8
> [   15.570455] [drm] Big FIFO is enabled
> [   15.794414] [drm] Big FIFO is enabled
> [   43.469060] [drm] Big FIFO is enabled
> [   44.647037] [drm] Big FIFO is enabled
> [   54.979954] [drm] Big FIFO is enabled
> [   56.095063] [drm] Big FIFO is enabled
> [   60.143822] CPU0 attaching NULL sched-domain.
> [   60.143838] CPU1 attaching NULL sched-domain.
> [   60.200221] CPU0 attaching sched-domain:
> [   60.200232]  domain 0: span 0-1 level SIBLING
> [   60.200241]   groups: 0 (cpu_power = 589) 1 (cpu_power = 589)
> [   60.200259]   domain 1: span 0-1 level MC
> [   60.200267]    groups: 0-1 (cpu_power = 1178)
> [   60.200284] CPU1 attaching sched-domain:
> [   60.200291]  domain 0: span 0-1 level SIBLING
> [   60.200299]   groups: 1 (cpu_power = 589) 0 (cpu_power = 589)
> [   60.200316]   domain 1: span 0-1 level MC
> [   60.200324]    groups: 0-1 (cpu_power = 1178)
> [   68.791896] wlan0: direct probe to AP 00:23:97:8d:d5:81 (try 1)
> [   68.791967] wlan0: deauthenticating from 00:23:97:8d:d5:81 by local choice (reason=3)
> [   68.792053] wlan0: direct probe to AP 00:23:97:8d:d5:81 (try 1)
> [   68.795250] wlan0: direct probe responded
> [   68.795264] wlan0: authenticate with AP 00:23:97:8d:d5:81 (try 1)
> [   68.799823] wlan0: authenticated
> [   68.799875] wlan0: associate with AP 00:23:97:8d:d5:81 (try 1)
> [   68.802398] wlan0: RX AssocResp from 00:23:97:8d:d5:81 (capab=0x411 status=0 aid=1)
> [   68.802407] wlan0: associated
> [   68.803223] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
> [   71.297347] [UFW BLOCK] IN=wlan0 OUT= MAC=00:26:4d:1d:72:0f:00:23:97:8d:d5:7b:08:00 SRC=192.168.1.1 DST=192.168.1.33 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=46967 DF PROTO=TCP SPT=1933 DPT=80 WINDOW=5840 RES=0x00 SYN URGP=0 
> [   74.294508] [UFW BLOCK] IN=wlan0 OUT= MAC=00:26:4d:1d:72:0f:00:23:97:8d:d5:7b:08:00 SRC=192.168.1.1 DST=192.168.1.33 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=46968 DF PROTO=TCP SPT=1933 DPT=80 WINDOW=5840 RES=0x00 SYN URGP=0 
> [   75.371787] [UFW BLOCK] IN=wlan0 OUT= MAC=00:26:4d:1d:72:0f:00:23:97:8d:d5:7b:08:00 SRC=174.36.30.73 DST=192.168.1.33 LEN=89 TOS=0x00 PREC=0x00 TTL=47 ID=59398 DF PROTO=TCP SPT=443 DPT=53935 WINDOW=85 RES=0x00 ACK PSH URGP=0 
> [   79.062551] wlan0: no IPv6 routers present
> [   79.837337] [UFW BLOCK] IN=wlan0 OUT= MAC=00:26:4d:1d:72:0f:00:23:97:8d:d5:7b:08:00 SRC=174.36.30.95 DST=192.168.1.33 LEN=250 TOS=0x00 PREC=0x00 TTL=47 ID=45812 DF PROTO=TCP SPT=80 DPT=36426 WINDOW=62 RES=0x00 ACK PSH URGP=0 
> [   80.297339] [UFW BLOCK] IN=wlan0 OUT= MAC=00:26:4d:1d:72:0f:00:23:97:8d:d5:7b:08:00 SRC=192.168.1.1 DST=192.168.1.33 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=46969 DF PROTO=TCP SPT=1933 DPT=80 WINDOW=5840 RES=0x00 SYN URGP=0 
> [   92.303270] [UFW BLOCK] IN=wlan0 OUT= MAC=00:26:4d:1d:72:0f:00:23:97:8d:d5:7b:08:00 SRC=192.168.1.1 DST=192.168.1.33 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=46970 DF PROTO=TCP SPT=1933 DPT=80 WINDOW=5840 RES=0x00 SYN URGP=0 
> [  193.194297] lo: Disabled Privacy Extensions
> 


thats is all

---

### Post by fremantle on 2010-08-19
no worries people, just found this AWESOME tool MountManager 0.2.6 (find it from soft center) Ran usb wizard and selected a folder in my home directory as mountpoint. now i can access the flash drive.


thanks brothas.

---

### Post by skatinjj on 2010-08-19
> **fremantle said:**
> no worries people, just found this AWESOME tool MountManager 0.2.6 (find it from soft center) Ran usb wizard and selected a folder in my home directory as mountpoint. now i can access the flash drive.


thanks brothas.

Was going to direct you on how to mount it from a terminal, but I see you found a solution :p

---

### Post by fremantle on 2010-08-19
but hey, i need to format the drive as ntfs. i installed gparted (64 bit) but when i click on it it doesnt come up!!!

---

### Post by skatinjj on 2010-08-19
> **fremantle said:**
> but hey, i need to format the drive as ntfs. i installed gparted (64 bit) but when i click on it it doesnt come up!!!

Ok, so you installed gparted 64 bit edition and when you select it from the menu it does not come up? Does the mouse pointer change to indicate the CPU is trying to do something?  

Also, how did you install it, apt-get, package manager, off the internet somewhere?  Any errors during or after installation?

---

### Post by fremantle on 2010-08-19
> **skatinjj said:**
> Ok, so you installed gparted 64 bit edition and when you select it from the menu it does not come up? Does the mouse pointer change to indicate the CPU is trying to do something?  

Also, how did you install it, apt-get, package manager, off the internet somewhere?  Any errors during or after installation?

i should provide some more info.
im running lucid lynx 64 bit on my dell mini 1012. so i installed gparted using sudo apt-get install gparted. now its under Applications>System tools. (but, i remember that last time i had it on lucid it was in System>Administration). So when i click on gparted, down below in the gnome panel i see "starting gparted"// The mouse gets the busy shape and stays like that for like 4-5 seconds. then everything is normal but gparted doesnt open up.

---

### Post by fremantle on 2010-08-19
ow, and i faced no errors whatsoever during installation.

---

### Post by skatinjj on 2010-08-19
> **fremantle said:**
> ow, and i faced no errors whatsoever during installation.

I believe gparted is installed out of the box in Lucid under System > Administration > GParted

Have you tried running it from there?

---

### Post by fremantle on 2010-08-19
strange! for me it wasnt there after i installed lucid..and besides, if i already had it, when i did apt-get it woud have told me that gparted is already the newest version, so not installed.

---

### Post by jtarin on 2010-08-19
Start from a terminal for error messages. ```
sudo gparted
```

---

### Post by fremantle on 2010-08-19
> **jtarin said:**
> Start from a terminal for error messages. ```
sudo gparted
```

bingo!
> abir@openforce:~$ sudo gparted
[sudo] password for abir: 
error: libhal_acquire_global_interface_lock: org.freedesktop.Hal.Device.InterfaceAlreadyLocked: The interface org.freedesktop.Hal.Device.Storage is already exclusively locked either by someone else or it's already locked by yourself
abir@openforce:~$ 


---

### Post by fremantle on 2010-08-19
i have no idea what this error is referring to. any explanations???

---

### Post by skatinjj on 2010-08-19
> **fremantle said:**
> bingo!

Have you tried rebooting and run it again from terminal?

---

### Post by jtarin on 2010-08-19
That means its already running somewhere and the process is locked. Do as suggested and either reboot or kill the process and issue the command again.

---

### Post by fremantle on 2010-08-19
> **jtarin said:**
> That means its already running somewhere and the process is locked. Do as suggested and either reboot or kill the process and issue the command again.

ya the command worked after reboot. now do i always have to do this?

---

### Post by jtarin on 2010-08-19
Not if the command worked. Exit the terminal and Gparted should exit. Now you might want to edit your menu to reflect the install.

---

### Post by fremantle on 2010-08-19
hm. right now im trying to mount my 4 gb usb drive (gonna install vista from it) can anyone tell me how to do it thru command line? sumthning is messd up with my lucid, no usb drives are getting mounted. even mountmanager failed.

---

### Post by fremantle on 2010-08-19
i created a usb_drive folder in /media/.

---

### Post by skatinjj on 2010-08-19
> **fremantle said:**
> i created a usb_drive folder in /media/.

To mount via terminal:

```
sudo mount /dev/sdb /media/usb_drive
```

Replace /dev/sdb with whatever your drive is, that just so happens to be my thumb drive in my system.

---

### Post by jtarin on 2010-08-19
> **skatinjj said:**
> To mount via terminal:

```
sudo mount /dev/sdb /media/usb_drive
```

Replace /dev/sdb with whatever your drive is, that just so happens to be my thumb drive in my system.
Post new topic in a new thread and mark this as solved so you can get specific help.

---

### Post by disan on 2010-10-24
Hi, I had the same problem, but my solution was so easy.
I went to the / directory in a terminal:
*cd /*
and there wasn't any media directory, :confused:  so I created it!!
*sudo mkdir media*
that's it, no more.
I hope this can help someone else!

---

### Post by Suhaib58 on 2012-03-14
sudo mkdir /media
sudo chmod a+x /media
sudo mkdir /media/usb_drive

this works.. I had similar problem as I had deleted media folder from the root.

---

### Post by ubudog on 2012-03-14
Back to sleep thread.

---

