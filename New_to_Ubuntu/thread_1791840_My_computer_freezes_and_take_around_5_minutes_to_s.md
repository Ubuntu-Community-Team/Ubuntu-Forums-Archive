---
title: "My computer freezes and take around 5 minutes to start."
date: 2011-06-27
forum: New to Ubuntu
---

### Post by Arazu on 2011-06-27
Running 10.04

The BIOS part seems to go fine but it hangs on the Ubuntu splash screen. It's not stuck because the dots are moving. It just takes forever to load. This started yesterday and today it seems worse.

On top of that it will lock up for no apparent reason. Suddenly it will stop accepting keyboard and mouse clicks but I can still move the cursor. By no apparent reason I mean that it happens at random. Sometimes the system is under load and sometimes it's not. It could lock up right now and all I have open are Pidgin and Firefox. Oddly it's never locked up when I'm playing Minecraft which is really difficult for my computer to handle.

I'm at a loss and honestly too stressed out to think logically. I don't know if I should be looking at hardware or software.

Any help would be greatly appreciated. Thanks.

---

### Post by aeiah on 2011-06-27
if you press F1 during boot (or maybe ctrl+alt+F1) you should be able to see all the messages scroll by as ubuntu loads, rather than the splash screen. things may go by too fast though.

your boot log can be accessed using the dmesg command in a terminal. these messages get appended to /var/log/messages so you could look there too.

so in a terminal do:
```
dmesg
```
and paste the contents here. if you wanted to place it in a text file on your desktop you could do 
```

dmesg > ~/Desktop/boot_messages

```

there's also a program you can install called bootlog, or specifically its daemon, bootlogd. it will monitor your startup and create a bar chart of how long each process takes. this could also be useful for identifying how long things are taking, or where things are hanging. i think the logs get stored in /var/log/bootchart/

---

### Post by Arazu on 2011-06-27
It's a lot but here it is.

```
[    0.429909] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    0.429946] rtc0: alarms up to one year, y3k, 242 bytes nvram, hpet irqs
[    0.430044] device-mapper: uevent: version 1.0.3
[    0.430158] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    0.430227] device-mapper: multipath: version 1.1.0 loaded
[    0.430230] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.430339] EISA: Probing bus 0 at eisa.0
[    0.430345] Cannot allocate resource for EISA slot 1
[    0.430363] EISA: Detected 0 cards.
[    0.430439] cpuidle: using governor ladder
[    0.430442] cpuidle: using governor menu
[    0.430823] TCP cubic registered
[    0.430974] NET: Registered protocol family 10
[    0.431420] lo: Disabled Privacy Extensions
[    0.431741] NET: Registered protocol family 17
[    0.431772] powernow-k8: Found 1 AMD Athlon(tm) 64 X2 Dual Core Processor 4400+ processors (2 cpu cores) (version 2.20.00)
[    0.431825] powernow-k8:    0 : fid 0xf (2300 MHz), vid 0xa
[    0.431827] powernow-k8:    1 : fid 0xe (2200 MHz), vid 0xb
[    0.431829] powernow-k8:    2 : fid 0xc (2000 MHz), vid 0xd
[    0.431831] powernow-k8:    3 : fid 0xa (1800 MHz), vid 0xf
[    0.431833] powernow-k8:    4 : fid 0x2 (1000 MHz), vid 0x12
[    0.431873] Using IPI No-Shortcut mode
[    0.431947] PM: Resume from disk failed.
[    0.431960] registered taskstats version 1
[    0.432205]   Magic number: 15:786:235
[    0.432254] fan PNP0C0B:00: hash matches
[    0.432316] rtc_cmos 00:05: setting system clock to 2011-06-27 15:14:06 UTC (1309187646)
[    0.432319] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.432321] EDD information not available.
[    0.675263] isapnp: No Plug & Play device found
[    0.675284] Freeing unused kernel memory: 668k freed
[    0.675771] Write protecting the kernel text: 4676k
[    0.675805] Write protecting the kernel read-only data: 1844k
[    0.693485] udev: starting version 151
[    0.736434] pata_amd 0000:00:06.0: version 0.4.1
[    0.736481] pata_amd 0000:00:06.0: setting latency timer to 64
[    0.763514] scsi0 : pata_amd
[    0.767804] scsi1 : pata_amd
[    0.768518] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[    0.768522] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[    0.770968] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
[    0.771286] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 23
[    0.771291] forcedeth 0000:00:07.0: PCI INT A -> Link[APCH] -> GSI 23 (level, low) -> IRQ 23
[    0.771296] forcedeth 0000:00:07.0: setting latency timer to 64
[    0.864025] usb 1-5: new high speed USB device using ehci_hcd and address 4
[    0.935011] ata2: port disabled. ignoring.
[    1.054671] usb 1-5: configuration #1 chosen from 1 choice
[    1.062124] Initializing USB Mass Storage driver...
[    1.062278] scsi2 : SCSI emulation for USB Mass Storage devices
[    1.062380] usbcore: registered new interface driver usb-storage
[    1.062383] USB Mass Storage support registered.
[    1.062484] usb-storage: device found at 4
[    1.062486] usb-storage: waiting for device to settle before scanning
[    1.288971] forcedeth 0000:00:07.0: ifname eth0, PHY OUI 0x732 @ 1, addr 00:1a:a0:88:c0:af
[    1.288975] forcedeth 0000:00:07.0: highdma pwrctl mgmt lnktim msi desc-v3
[    1.288998] sata_nv 0000:00:08.0: version 3.5
[    1.289022] sata_nv 0000:00:08.0: PCI INT A -> Link[APSI] -> GSI 20 (level, low) -> IRQ 20
[    1.289070] sata_nv 0000:00:08.0: setting latency timer to 64
[    1.289132] scsi3 : sata_nv
[    1.289246] scsi4 : sata_nv
[    1.289429] ata3: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xd800 irq 20
[    1.289432] ata4: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xd808 irq 20
[    1.356017] usb 2-1: new full speed USB device using ohci_hcd and address 2
[    1.577106] usb 2-1: configuration #1 chosen from 1 choice
[    1.593708] usbcore: registered new interface driver hiddev
[    1.598302] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:02.0/usb2/2-1/2-1:1.0/input/input3
[    1.598388] generic-usb 0003:046D:C529.0001: input,hidraw0: USB HID v1.11 Keyboard [Logitech USB Receiver] on usb-0000:00:02.0-1/input0
[    1.606625] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:02.0/usb2/2-1/2-1:1.1/input/input4
[    1.606738] generic-usb 0003:046D:C529.0002: input,hiddev96,hidraw1: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:02.0-1/input1
[    1.606760] usbcore: registered new interface driver usbhid
[    1.606843] usbhid: v2.6:USB HID core driver
[    1.756035] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.775293] ata3.00: ATA-8: WDC WD3200AAKS-75VYA0, 12.01B02, max UDMA/133
[    1.775296] ata3.00: 625142448 sectors, multi 1: LBA48 NCQ (depth 0/32)
[    1.789016] ata3.00: configured for UDMA/133
[    1.789175] scsi 3:0:0:0: Direct-Access     ATA      WDC WD3200AAKS-7 12.0 PQ: 0 ANSI: 5
[    1.789340] sd 3:0:0:0: Attached scsi generic sg0 type 0
[    1.789387] sd 3:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    1.789454] sd 3:0:0:0: [sda] Write Protect is off
[    1.789457] sd 3:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.789477] sd 3:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.789611]  sda: sda1 sda2 sda3
[    1.806814] sd 3:0:0:0: [sda] Attached SCSI disk
[    1.884015] usb 2-2: new low speed USB device using ohci_hcd and address 3
[    2.100099] usb 2-2: configuration #1 chosen from 1 choice
[    2.113282] input: Microsoft Natural Keyboard Elite as /devices/pci0000:00/0000:00:02.0/usb2/2-2/2-2:1.0/input/input5
[    2.113369] generic-usb 0003:045E:000B.0003: input,hidraw2: USB HID v1.10 Keyboard [Microsoft Natural Keyboard Elite] on usb-0000:00:02.0-2/input0
[    2.256042] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.264135] ata4.00: ATAPI: HL-DT-ST DVD+/-RW GSA-H73N, B103, max UDMA/100
[    2.280140] ata4.00: configured for UDMA/100
[    2.282053] scsi 4:0:0:0: CD-ROM            HL-DT-ST DVD+-RW GSA-H73N B103 PQ: 0 ANSI: 5
[    2.286524] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[    2.286527] Uniform CD-ROM driver Revision: 3.20
[    2.286627] sr 4:0:0:0: Attached scsi CD-ROM sr0
[    2.286686] sr 4:0:0:0: Attached scsi generic sg1 type 5
[    2.567738] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
[    2.567743] EXT4-fs (sda1): write access will be enabled during recovery
[    2.599124] EXT4-fs (sda1): recovery complete
[    2.599450] EXT4-fs (sda1): mounted filesystem with ordered data mode
[    6.066245] usb-storage: device scan complete
[    6.070224] scsi 2:0:0:0: Direct-Access     TEAC     USB   HS-CF Card 4.08 PQ: 0 ANSI: 0
[    6.073963] scsi 2:0:0:1: Direct-Access     TEAC     USB   HS-xD/SM   4.08 PQ: 0 ANSI: 0
[    6.077586] scsi 2:0:0:2: Direct-Access     TEAC     USB   HS-MS Card 4.08 PQ: 0 ANSI: 0
[    6.080711] scsi 2:0:0:3: Direct-Access     TEAC     USB   HS-SD Card 4.08 PQ: 0 ANSI: 0
[    6.081205] sd 2:0:0:0: Attached scsi generic sg2 type 0
[    6.081340] sd 2:0:0:1: Attached scsi generic sg3 type 0
[    6.081475] sd 2:0:0:2: Attached scsi generic sg4 type 0
[    6.081620] sd 2:0:0:3: Attached scsi generic sg5 type 0
[    6.094085] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[    6.097955] sd 2:0:0:1: [sdc] Attached SCSI removable disk
[    6.110576] sd 2:0:0:2: [sdd] Attached SCSI removable disk
[    6.114701] sd 2:0:0:3: [sde] Attached SCSI removable disk
[   12.898444] udev: starting version 151
[   12.959035] lp: driver loaded but no devices found
[   12.981116] k8temp 0000:00:18.3: Temperature readouts might be wrong - check erratum #141
[   12.982042] i2c i2c-0: nForce2 SMBus adapter at 0x1c00
[   12.982062] i2c i2c-1: nForce2 SMBus adapter at 0x1c40
[   12.984926] vga16fb: initializing
[   12.984931] vga16fb: mapped to 0xc00a0000
[   12.984995] fb0: VGA16 VGA frame buffer device
[   13.007927] Adding 7812088k swap on /dev/sda2.  Priority:-1 extents:1 across:7812088k 
[   13.078805] f71882fg: Found f8000 chip at 0x290, revision 41
[   13.078847] ACPI: resource f71882fg [0x290-0x297] conflicts with ACPI region SEN1 [0x295-0x296]
[   13.078849] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   13.078946] Linux agpgart interface v0.103
[   13.136273] type=1505 audit(1309187659.200:2):  operation="profile_load" pid=604 name="/sbin/dhclient3"
[   13.136538] type=1505 audit(1309187659.200:3):  operation="profile_load" pid=604 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   13.136689] type=1505 audit(1309187659.200:4):  operation="profile_load" pid=604 name="/usr/lib/connman/scripts/dhclient-script"
[   13.159335] type=1505 audit(1309187659.224:5):  operation="profile_load" pid=643 name="/usr/sbin/ntpd"
[   13.229419] nvidia: module license 'NVIDIA' taints kernel.
[   13.229423] Disabling lock debugging due to kernel taint
[   14.197088] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   14.197836] dell-wmi: No known WMI GUID found
[   14.207489] ip_tables: (C) 2000-2006 Netfilter Core Team
[   14.301811] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 22
[   14.301818] HDA Intel 0000:00:05.0: PCI INT B -> Link[AAZA] -> GSI 22 (level, low) -> IRQ 22
[   14.301821] hda_intel: Disable MSI for Nvidia chipset
[   14.301845] HDA Intel 0000:00:05.0: setting latency timer to 64
[   14.472615] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[   14.472955] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Please use
[   14.472957] nf_conntrack.acct=1 kernel parameter, acct=1 nf_conntrack module option or
[   14.472959] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
[   14.507925] ip6_tables: (C) 2000-2006 Netfilter Core Team
[   14.541013] Console: switching to colour frame buffer device 80x30
[   15.049017] hda_codec: ALC888: BIOS auto-probing.
[   15.272092] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:05.0/input/input6
[   15.500509] ACPI: PCI Interrupt Link [AIGP] enabled at IRQ 23
[   15.500517] nvidia 0000:00:0d.0: PCI INT A -> Link[AIGP] -> GSI 23 (level, low) -> IRQ 23
[   15.500524] nvidia 0000:00:0d.0: setting latency timer to 64
[   15.500530] vgaarb: device changed decodes: PCI:0000:00:0d.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   15.500802] NVRM: loading NVIDIA UNIX x86 Kernel Module  195.36.24  Thu Apr 22 09:18:20 PDT 2010
[   90.804034] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[   90.804041] ata3.00: failed command: READ DMA EXT
[   90.804047] ata3.00: cmd 25/00:f0:f8:78:17/00:00:16:00:00/e0 tag 0 dma 122880 in
[   90.804049]          res 40/00:ff:00:00:00/00:00:00:00:00/40 Emask 0x4 (timeout)
[   90.804052] ata3.00: status: { DRDY }
[   90.804057] ata3: hard resetting link
[   90.804060] ata3: nv: skipping hardreset on occupied port
[   91.328031] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   91.369072] ata3.00: configured for UDMA/133
[   91.369076] ata3.00: device reported invalid CHS sector 0
[   91.369083] ata3: EH complete
[  121.804024] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[  121.804027] ata3.00: failed command: READ DMA EXT
[  121.804033] ata3.00: cmd 25/00:f0:f8:78:17/00:00:16:00:00/e0 tag 0 dma 122880 in
[  121.804034]          res 40/00:ff:00:00:00/00:00:00:00:00/40 Emask 0x4 (timeout)
[  121.804037] ata3.00: status: { DRDY }
[  121.804041] ata3: hard resetting link
[  121.804043] ata3: nv: skipping hardreset on occupied port
[  122.272039] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[  122.304851] ata3.00: configured for UDMA/133
[  122.304854] ata3.00: device reported invalid CHS sector 0
[  122.304858] ata3: EH complete
[  152.804023] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[  152.804026] ata3.00: failed command: READ DMA EXT
[  152.804032] ata3.00: cmd 25/00:f0:f8:78:17/00:00:16:00:00/e0 tag 0 dma 122880 in
[  152.804033]          res 40/00:ff:00:00:00/00:00:00:00:00/40 Emask 0x4 (timeout)
[  152.804036] ata3.00: status: { DRDY }
[  152.804040] ata3: hard resetting link
[  152.804041] ata3: nv: skipping hardreset on occupied port
[  153.272032] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[  153.300595] ata3.00: configured for UDMA/133
[  153.300598] ata3.00: device reported invalid CHS sector 0
[  153.300602] ata3: EH complete
[  183.804035] ata3: limiting SATA link speed to 1.5 Gbps
[  183.804042] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[  183.804047] ata3.00: failed command: READ DMA EXT
[  183.804054] ata3.00: cmd 25/00:f0:f8:78:17/00:00:16:00:00/e0 tag 0 dma 122880 in
[  183.804055]          res 40/00:ff:00:00:00/00:00:00:00:00/40 Emask 0x4 (timeout)
[  183.804058] ata3.00: status: { DRDY }
[  183.804065] ata3: hard resetting link
[  183.804067] ata3: nv: skipping hardreset on occupied port
[  184.272030] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[  184.300364] ata3.00: configured for UDMA/133
[  184.300367] ata3.00: device reported invalid CHS sector 0
[  184.300372] ata3: EH complete
[  214.804028] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[  214.804031] ata3.00: failed command: READ DMA EXT
[  214.804037] ata3.00: cmd 25/00:f0:f8:78:17/00:00:16:00:00/e0 tag 0 dma 122880 in
[  214.804038]          res 40/00:ff:00:00:00/00:00:00:00:00/40 Emask 0x4 (timeout)
[  214.804041] ata3.00: status: { DRDY }
[  214.804046] ata3: hard resetting link
[  214.804048] ata3: nv: skipping hardreset on occupied port
[  215.272028] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[  215.309178] ata3.00: configured for UDMA/133
[  215.309181] ata3.00: device reported invalid CHS sector 0
[  215.309186] ata3: EH complete
[  240.309015] INFO: task ata_aux:27 blocked for more than 120 seconds.
[  240.309017] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[  240.309020] ata_aux       D 0000010c     0    27      2 0x00000000
[  240.309025]  f719bcbc 00000046 f0f0f0f0 0000010c 00000000 c0849860 f7134f24 c0849860
[  240.309032]  45ab873c 00000015 c0849860 c0849860 f7134f24 c0849860 c0849860 f6b6cc40
[  240.309037]  45aa8fd2 00000015 f7134c80 7fffffff 7fffffff f719bd7c f719bd1c c058a29d
[  240.309044] Call Trace:
[  240.309052]  [<c058a29d>] schedule_timeout+0x1ad/0x280
[  240.309057]  [<c034e76d>] ? kobject_put+0x1d/0x50
[  240.309063]  [<c012a768>] ? default_spin_lock_flags+0x8/0x10
[  240.309066]  [<c058ba98>] ? _spin_lock_irq+0x18/0x20
[  240.309069]  [<c0589f56>] wait_for_common+0xa6/0x130
[  240.309073]  [<c0145830>] ? default_wake_function+0x0/0x20
[  240.309076]  [<c058a097>] wait_for_completion+0x17/0x20
[  240.309080]  [<c0340eea>] blk_execute_rq+0x7a/0xd0
[  240.309083]  [<c0340da0>] ? blk_end_sync_rq+0x0/0x30
[  240.309088]  [<c033d4c2>] ? get_request_wait+0x22/0x170
[  240.309092]  [<c033d673>] ? blk_get_request+0x63/0x80
[  240.309096]  [<c0403f07>] scsi_execute+0xb7/0x140
[  240.309099]  [<c040414a>] scsi_execute_req+0x8a/0x140
[  240.309103]  [<c040d1a5>] sd_spinup_disk+0x85/0x4d0
[  240.309106]  [<c040f10f>] ? sd_revalidate_disk+0x6f/0x310
[  240.309109]  [<c040f13a>] sd_revalidate_disk+0x9a/0x310
[  240.309112]  [<c0148908>] ? dequeue_entity+0x1c8/0x220
[  240.309116]  [<c034e8d2>] ? kobject_get+0x12/0x20
[  240.309121]  [<c03e6118>] ? get_device+0x18/0x20
[  240.309125]  [<c0233f69>] revalidate_disk+0x29/0x80
[  240.309129]  [<c040c2df>] sd_rescan+0x1f/0x30
[  240.309132]  [<c040547f>] scsi_rescan_device+0x6f/0xc0
[  240.309135]  [<c03e6118>] ? get_device+0x18/0x20
[  240.309139]  [<c03fbeb3>] ? scsi_device_get+0x43/0xc0
[  240.309142]  [<c042099c>] ata_scsi_dev_rescan+0x8c/0xe0
[  240.309147]  [<c016438e>] run_workqueue+0x8e/0x150
[  240.309150]  [<c0420910>] ? ata_scsi_dev_rescan+0x0/0xe0
[  240.309154]  [<c01644d4>] worker_thread+0x84/0xe0
[  240.309157]  [<c0168450>] ? autoremove_wake_function+0x0/0x50
[  240.309161]  [<c0164450>] ? worker_thread+0x0/0xe0
[  240.309164]  [<c01681c4>] kthread+0x74/0x80
[  240.309167]  [<c0168150>] ? kthread+0x0/0x80
[  240.309171]  [<c0104087>] kernel_thread_helper+0x7/0x10
[  240.309176] INFO: task jbd2/sda1-8:301 blocked for more than 120 seconds.
[  240.309178] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[  240.309180] jbd2/sda1-8   D 00002537     0   301      2 0x00000000
[  240.309184]  f6b0de2c 00000046 f6b0dde4 00002537 00000000 c0849860 f6a168a4 c0849860
[  240.309190]  0442d27f 0000000e c0849860 c0849860 f6a168a4 c0849860 c0849860 f3781c00
[  240.309196]  0442a41e 0000000e f6a16600 f6a16600 c2e08860 f6b0de78 f6b0de3c c0589db1
[  240.309202] Call Trace:
[  240.309205]  [<c0589db1>] io_schedule+0x61/0xa0
[  240.309208]  [<c022eae8>] sync_buffer+0x38/0x40
[  240.309211]  [<c058a56d>] __wait_on_bit+0x4d/0x70
[  240.309214]  [<c022eab0>] ? sync_buffer+0x0/0x40
[  240.309217]  [<c022eab0>] ? sync_buffer+0x0/0x40
[  240.309220]  [<c058a63b>] out_of_line_wait_on_bit+0xab/0xc0
[  240.309223]  [<c01684a0>] ? wake_bit_function+0x0/0x50
[  240.309226]  [<c022eaae>] __wait_on_buffer+0x2e/0x30
[  240.309232]  [<c02c6a11>] journal_wait_on_commit_record+0x41/0xe0
[  240.309236]  [<c02c7ab5>] jbd2_journal_commit_transaction+0xe85/0x1030
[  240.309239]  [<c0145ee9>] ? load_balance_newidle+0x99/0x340
[  240.309243]  [<c012a768>] ? default_spin_lock_flags+0x8/0x10
[  240.309246]  [<c015c4e8>] ? try_to_del_timer_sync+0x68/0xb0
[  240.309252]  [<c02cd935>] kjournald2+0x95/0x1c0
[  240.309255]  [<c0168450>] ? autoremove_wake_function+0x0/0x50
[  240.309258]  [<c02cd8a0>] ? kjournald2+0x0/0x1c0
[  240.309261]  [<c01681c4>] kthread+0x74/0x80
[  240.309264]  [<c0168150>] ? kthread+0x0/0x80
[  240.309267]  [<c0104087>] kernel_thread_helper+0x7/0x10
[  245.804033] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[  245.804037] ata3.00: failed command: READ DMA EXT
[  245.804043] ata3.00: cmd 25/00:f0:f8:78:17/00:00:16:00:00/e0 tag 0 dma 122880 in
[  245.804044]          res 40/00:ff:00:00:00/00:00:00:00:00/40 Emask 0x4 (timeout)
[  245.804047] ata3.00: status: { DRDY }
[  245.804053] ata3: hard resetting link
[  245.804055] ata3: nv: skipping hardreset on occupied port
[  246.272038] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[  246.296926] ata3.00: configured for UDMA/133
[  246.296930] ata3.00: device reported invalid CHS sector 0
[  246.296942] sd 3:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  246.296945] sd 3:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[  246.296950] Descriptor sense data with sense descriptors (in hex):
[  246.296952]         72 0b 00 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  246.296961]         00 00 00 00 
[  246.296965] sd 3:0:0:0: [sda] Add. Sense: No additional sense information
[  246.296969] sd 3:0:0:0: [sda] CDB: Read(10): 28 00 16 17 78 f8 00 00 f0 00
[  246.296977] end_request: I/O error, dev sda, sector 370637048
[  246.296982] Buffer I/O error on device sda3, logical block 38273055
[  246.296986] Buffer I/O error on device sda3, logical block 38273056
[  246.296989] Buffer I/O error on device sda3, logical block 38273057
[  246.296992] Buffer I/O error on device sda3, logical block 38273058
[  246.296996] Buffer I/O error on device sda3, logical block 38273059
[  246.296999] Buffer I/O error on device sda3, logical block 38273060
[  246.297008] Buffer I/O error on device sda3, logical block 38273061
[  246.297011] Buffer I/O error on device sda3, logical block 38273062
[  246.297014] Buffer I/O error on device sda3, logical block 38273063
[  246.297018] Buffer I/O error on device sda3, logical block 38273064
[  246.297039] ata3: EH complete
[  248.293526] EXT4-fs (sda3): mounted filesystem with ordered data mode
[  252.630523] __ratelimit: 20 callbacks suppressed
[  252.630527] type=1505 audit(1309187898.695:6):  operation="profile_replace" pid=1123 name="/sbin/dhclient3"
[  252.630802] type=1505 audit(1309187898.695:7):  operation="profile_replace" pid=1123 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[  252.632590] type=1505 audit(1309187898.699:8):  operation="profile_replace" pid=1123 name="/usr/lib/connman/scripts/dhclient-script"
[  252.632905] type=1505 audit(1309187898.699:9):  operation="profile_load" pid=1122 name="/usr/share/gdm/guest-session/Xsession"
[  252.639854] type=1505 audit(1309187898.703:10):  operation="profile_load" pid=1126 name="/usr/lib/cups/backend/cups-pdf"
[  252.640191] type=1505 audit(1309187898.707:11):  operation="profile_load" pid=1126 name="/usr/sbin/cupsd"
[  252.641925] type=1505 audit(1309187898.707:12):  operation="profile_load" pid=1124 name="/usr/bin/evince"
[  252.642985] type=1505 audit(1309187898.707:13):  operation="profile_replace" pid=1127 name="/usr/sbin/ntpd"
[  252.645404] type=1505 audit(1309187898.711:14):  operation="profile_load" pid=1124 name="/usr/bin/evince-previewer"
[  252.645518] type=1505 audit(1309187898.711:15):  operation="profile_load" pid=1128 name="/usr/sbin/tcpdump"
[  252.732721]   alloc irq_desc for 26 on node -1
[  252.732725]   alloc kstat_irqs on node -1
[  252.732736] forcedeth 0000:00:07.0: irq 26 for MSI/MSI-X
[  252.911320] vboxdrv: Found 2 processor cores.
[  252.911471] vboxdrv: fAsync=1 offMin=0x7f5bf offMax=0x7f5bf
[  252.911796] vboxdrv: TSC mode is 'asynchronous', kernel timer mode is 'normal'.
[  252.911798] vboxdrv: Successfully loaded version 4.0.4 (interface 0x00160000).
[  254.323252] ppdev: user-space parallel port driver
[  263.596011] eth0: no IPv6 routers present
[  315.005035] Clocksource tsc unstable (delta = -183675123 ns)
[  321.416223] [UFW BLOCK] IN=eth0 OUT= MAC=00:1a:a0:88:c0:af:00:15:f9:2a:93:da:08:00 SRC=98.222.126.31 DST=68.228.32.254 LEN=48 TOS=0x00 PREC=0x00 TTL=51 ID=7095 DF PROTO=TCP SPT=50208 DPT=51413 WINDOW=8192 RES=0x00 SYN URGP=0 
[  413.617887] [UFW BLOCK] IN=eth0 OUT= MAC=00:1a:a0:88:c0:af:00:15:f9:2a:93:da:08:00 SRC=90.215.36.212 DST=68.228.32.254 LEN=95 TOS=0x00 PREC=0x00 TTL=118 ID=239 PROTO=UDP SPT=17857 DPT=51413 LEN=75 
[  416.887824] [UFW BLOCK] IN=eth0 OUT= MAC=00:1a:a0:88:c0:af:00:15:f9:2a:93:da:08:00 SRC=90.215.36.212 DST=68.228.32.254 LEN=58 TOS=0x00 PREC=0x00 TTL=118 ID=303 PROTO=UDP SPT=17857 DPT=51413 LEN=38 
[  424.503196] [UFW BLOCK] IN=eth0 OUT= MAC=00:1a:a0:88:c0:af:00:15:f9:2a:93:da:08:00 SRC=90.215.36.212 DST=68.228.32.254 LEN=58 TOS=0x00 PREC=0x00 TTL=118 ID=355 PROTO=UDP SPT=17857 DPT=51413 LEN=38 
[  437.053398] [UFW BLOCK] IN=eth0 OUT= MAC=00:1a:a0:88:c0:af:00:15:f9:2a:93:da:08:00 SRC=90.215.36.212 DST=68.228.32.254 LEN=48 TOS=0x00 PREC=0x00 TTL=118 ID=468 DF PROTO=TCP SPT=1082 DPT=51413 WINDOW=16384 RES=0x00 SYN URGP=0 
[  440.050724] [UFW BLOCK] IN=eth0 OUT= MAC=00:1a:a0:88:c0:af:00:15:f9:2a:93:da:08:00 SRC=90.215.36.212 DST=68.228.32.254 LEN=48 TOS=0x00 PREC=0x00 TTL=118 ID=478 DF PROTO=TCP SPT=1082 DPT=51413 WINDOW=16384 RES=0x00 SYN URGP=0 
[  445.985278] [UFW BLOCK] IN=eth0 OUT= MAC=00:1a:a0:88:c0:af:00:15:f9:2a:93:da:08:00 SRC=90.215.36.212 DST=68.228.32.254 LEN=48 TOS=0x00 PREC=0x00 TTL=118 ID=544 DF PROTO=TCP SPT=1082 DPT=51413 WINDOW=16384 RES=0x00 SYN URGP=0 
[  473.847248] [UFW BLOCK] IN=eth0 OUT= MAC=00:1a:a0:88:c0:af:00:15:f9:2a:93:da:08:00 SRC=14.199.47.136 DST=68.228.32.254 LEN=90 TOS=0x00 PREC=0x00 TTL=53 ID=50536 PROTO=UDP SPT=40798 DPT=32764 LEN=70 
[  520.167147] [UFW BLOCK] IN=eth0 OUT= MAC=00:1a:a0:88:c0:af:00:15:f9:2a:93:da:08:00 SRC=90.215.36.212 DST=68.228.32.254 LEN=58 TOS=0x00 PREC=0x00 TTL=118 ID=1207 PROTO=UDP SPT=17857 DPT=51413 LEN=38 
[  522.862677] [UFW BLOCK] IN=eth0 OUT= MAC=00:1a:a0:88:c0:af:00:15:f9:2a:93:da:08:00 SRC=90.215.36.212 DST=68.228.32.254 LEN=58 TOS=0x00 PREC=0x00 TTL=118 ID=1224 PROTO=UDP SPT=17857 DPT=51413 LEN=38 
[  547.098060] [UFW BLOCK] IN=eth0 OUT= MAC=00:1a:a0:88:c0:af:00:15:f9:2a:93:da:08:00 SRC=90.215.36.212 DST=68.228.32.254 LEN=48 TOS=0x00 PREC=0x00 TTL=118 ID=1344 DF PROTO=TCP SPT=1164 DPT=51413 WINDOW=16384 RES=0x00 SYN URGP=0 
[  550.097536] [UFW BLOCK] IN=eth0 OUT= MAC=00:1a:a0:88:c0:af:00:15:f9:2a:93:da:08:00 SRC=90.215.36.212 DST=68.228.32.254 LEN=48 TOS=0x00 PREC=0x00 TTL=118 ID=1360 DF PROTO=TCP SPT=1164 DPT=51413 WINDOW=16384 RES=0x00 SYN URGP=0 
[  556.132772] [UFW BLOCK] IN=eth0 OUT= MAC=00:1a:a0:88:c0:af:00:15:f9:2a:93:da:08:00 SRC=90.215.36.212 DST=68.228.32.254 LEN=48 TOS=0x00 PREC=0x00 TTL=118 ID=1373 DF PROTO=TCP SPT=1164 DPT=51413 WINDOW=16384 RES=0x00 SYN URGP=0 
[  571.423441] [UFW BLOCK] IN=eth0 OUT= MAC=00:1a:a0:88:c0:af:00:15:f9:2a:93:da:08:00 SRC=60.173.10.27 DST=68.228.32.254 LEN=40 TOS=0x00 PREC=0x00 TTL=115 ID=256 DF PROTO=TCP SPT=12200 DPT=27977 WINDOW=8192 RES=0x00 SYN URGP=0 
[  577.725904] [UFW BLOCK] IN=eth0 OUT= MAC=00:1a:a0:88:c0:af:00:15:f9:2a:93:da:08:00 SRC=60.173.10.27 DST=68.228.32.254 LEN=40 TOS=0x00 PREC=0x00 TTL=115 ID=256 DF PROTO=TCP SPT=12200 DPT=1080 WINDOW=8192 RES=0x00 SYN URGP=0 
[  622.318002] [UFW BLOCK] IN=eth0 OUT= MAC=00:1a:a0:88:c0:af:00:15:f9:2a:93:da:08:00 SRC=216.245.196.122 DST=68.228.32.254 LEN=40 TOS=0x00 PREC=0x00 TTL=118 ID=256 DF PROTO=TCP SPT=12200 DPT=27977 WINDOW=8192 RES=0x00 SYN URGP=0 
[  656.925460] [UFW BLOCK] IN=eth0 OUT= MAC=00:1a:a0:88:c0:af:00:15:f9:2a:93:da:08:00 SRC=222.1.58.112 DST=68.228.32.254 LEN=90 TOS=0x00 PREC=0x00 TTL=115 ID=3209 PROTO=UDP SPT=13931 DPT=32764 LEN=70 
[  751.935611] [UFW BLOCK] IN=eth0 OUT= MAC=00:1a:a0:88:c0:af:00:15:f9:2a:93:da:08:00 SRC=123.165.159.198 DST=68.228.32.254 LEN=90 TOS=0x00 PREC=0x00 TTL=52 ID=42876 PROTO=UDP SPT=16001 DPT=64294 LEN=70 
[  771.369808] [UFW BLOCK] IN=eth0 OUT= MAC=00:1a:a0:88:c0:af:00:15:f9:2a:93:da:08:00 SRC=60.209.152.54 DST=68.228.32.254 LEN=64 TOS=0x00 PREC=0x00 TTL=49 ID=40521 DF PROTO=TCP SPT=2259 DPT=5900 WINDOW=65535 RES=0x00 SYN URGP=0 
[  774.357480] [UFW BLOCK] IN=eth0 OUT= MAC=00:1a:a0:88:c0:af:00:15:f9:2a:93:da:08:00 SRC=60.209.152.54 DST=68.228.32.254 LEN=64 TOS=0x00 PREC=0x00 TTL=49 ID=40987 DF PROTO=TCP SPT=2259 DPT=5900 WINDOW=65535 RES=0x00 SYN URGP=0 
[  799.942051] [UFW BLOCK] IN=eth0 OUT= MAC=00:1a:a0:88:c0:af:00:15:f9:2a:93:da:08:00 SRC=94.221.222.200 DST=68.228.32.254 LEN=90 TOS=0x00 PREC=0x00 TTL=112 ID=22250 PROTO=UDP SPT=17111 DPT=32764 LEN=70 
[  800.849856] [UFW BLOCK] IN=eth0 OUT= MAC=00:1a:a0:88:c0:af:00:15:f9:2a:93:da:08:00 SRC=90.215.36.212 DST=68.228.32.254 LEN=58 TOS=0x00 PREC=0x00 TTL=118 ID=2088 PROTO=UDP SPT=17857 DPT=51413 LEN=38 
[  803.867061] [UFW BLOCK] IN=eth0 OUT= MAC=00:1a:a0:88:c0:af:00:15:f9:2a:93:da:08:00 SRC=90.215.36.212 DST=68.228.32.254 LEN=58 TOS=0x00 PREC=0x00 TTL=118 ID=2097 PROTO=UDP SPT=17857 DPT=51413 LEN=38 
[  831.190345] [UFW BLOCK] IN=eth0 OUT= MAC=00:1a:a0:88:c0:af:00:15:f9:2a:93:da:08:00 SRC=60.173.10.27 DST=68.228.32.254 LEN=40 TOS=0x00 PREC=0x00 TTL=115 ID=256 DF PROTO=TCP SPT=12200 DPT=27977 WINDOW=8192 RES=0x00 SYN URGP=0 
[  834.395907] [UFW BLOCK] IN=eth0 OUT= MAC=00:1a:a0:88:c0:af:00:15:f9:2a:93:da:08:00 SRC=60.173.10.27 DST=68.228.32.254 LEN=40 TOS=0x00 PREC=0x00 TTL=115 ID=256 DF PROTO=TCP SPT=12200 DPT=1080 WINDOW=8192 RES=0x00 SYN URGP=0 
[  840.840620] [UFW BLOCK] IN=eth0 OUT= MAC=00:1a:a0:88:c0:af:00:15:f9:2a:93:da:08:00 SRC=90.215.36.212 DST=68.228.32.254 LEN=48 TOS=0x00 PREC=0x00 TTL=118 ID=2183 DF PROTO=TCP SPT=1275 DPT=51413 WINDOW=16384 RES=0x00 SYN URGP=0 
[  843.749404] [UFW BLOCK] IN=eth0 OUT= MAC=00:1a:a0:88:c0:af:00:15:f9:2a:93:da:08:00 SRC=90.215.36.212 DST=68.228.32.254 LEN=48 TOS=0x00 PREC=0x00 TTL=118 ID=2190 DF PROTO=TCP SPT=1275 DPT=51413 WINDOW=16384 RES=0x00 SYN URGP=0 
[  849.748887] [UFW BLOCK] IN=eth0 OUT= MAC=00:1a:a0:88:c0:af:00:15:f9:2a:93:da:08:00 SRC=90.215.36.212 DST=68.228.32.254 LEN=48 TOS=0x00 PREC=0x00 TTL=118 ID=2215 DF PROTO=TCP SPT=1275 DPT=51413 WINDOW=16384 RES=0x00 SYN URGP=0 
[  922.574694] [UFW BLOCK] IN=eth0 OUT= MAC=00:1a:a0:88:c0:af:00:15:f9:2a:93:da:08:00 SRC=208.115.219.10 DST=68.228.32.254 LEN=40 TOS=0x00 PREC=0x00 TTL=118 ID=256 DF PROTO=TCP SPT=12200 DPT=27977 WINDOW=8192 RES=0x00 SYN URGP=0 
[ 1679.202916] [UFW BLOCK] IN=eth0 OUT= MAC=00:1a:a0:88:c0:af:00:15:f9:2a:93:da:08:00 SRC=14.199.47.136 DST=68.228.32.254 LEN=90 TOS=0x00 PREC=0x00 TTL=53 ID=16160 PROTO=UDP SPT=41891 DPT=32764 LEN=70 
[ 1772.716676] [UFW BLOCK] IN=eth0 OUT= MAC=00:1a:a0:88:c0:af:00:15:f9:2a:93:da:08:00 SRC=208.115.219.10 DST=68.228.32.254 LEN=40 TOS=0x00 PREC=0x00 TTL=118 ID=256 DF PROTO=TCP SPT=12200 DPT=27977 WINDOW=8192 RES=0x00 SYN URGP=0 
[ 1789.130934] [UFW BLOCK] IN=eth0 OUT= MAC=00:1a:a0:88:c0:af:00:15:f9:2a:93:da:08:00 SRC=222.1.58.112 DST=68.228.32.254 LEN=90 TOS=0x00 PREC=0x00 TTL=115 ID=12813 PROTO=UDP SPT=13931 DPT=32764 LEN=70 
[ 1966.014860] [UFW BLOCK] IN=eth0 OUT= MAC=00:1a:a0:88:c0:af:00:15:f9:2a:93:da:08:00 SRC=119.184.114.211 DST=68.228.32.254 LEN=40 TOS=0x00 PREC=0x00 TTL=112 ID=256 DF PROTO=TCP SPT=12200 DPT=27977 WINDOW=8192 RES=0x00 SYN URGP=0 
[ 1973.483633] [UFW BLOCK] IN=eth0 OUT= MAC=00:1a:a0:88:c0:af:00:15:f9:2a:93:da:08:00 SRC=68.39.57.121 DST=68.228.32.254 LEN=52 TOS=0x00 PREC=0x00 TTL=114 ID=26263 DF PROTO=TCP SPT=1751 DPT=51413 WINDOW=65535 RES=0x00 SYN URGP=0 
[ 1976.548556] [UFW BLOCK] IN=eth0 OUT= MAC=00:1a:a0:88:c0:af:00:15:f9:2a:93:da:08:00 SRC=68.39.57.121 DST=68.228.32.254 LEN=52 TOS=0x00 PREC=0x00 TTL=114 ID=26446 DF PROTO=TCP SPT=1751 DPT=51413 WINDOW=65535 RES=0x00 SYN URGP=0 
[ 1982.563143] [UFW BLOCK] IN=eth0 OUT= MAC=00:1a:a0:88:c0:af:00:15:f9:2a:93:da:08:00 SRC=68.39.57.121 DST=68.228.32.254 LEN=52 TOS=0x00 PREC=0x00 TTL=114 ID=26807 DF PROTO=TCP SPT=1751 DPT=51413 WINDOW=65535 RES=0x00 SYN URGP=0 
[ 2066.351980] [UFW BLOCK] IN=eth0 OUT= MAC=00:1a:a0:88:c0:af:00:15:f9:2a:93:da:08:00 SRC=94.221.222.200 DST=68.228.32.254 LEN=90 TOS=0x00 PREC=0x00 TTL=112 ID=3705 PROTO=UDP SPT=17111 DPT=32764 LEN=70 
[ 2075.041881] [UFW BLOCK] IN=eth0 OUT= MAC=00:1a:a0:88:c0:af:00:15:f9:2a:93:da:08:00 SRC=174.76.227.113 DST=68.228.32.254 LEN=40 TOS=0x00 PREC=0x00 TTL=60 ID=0 DF PROTO=TCP SPT=80 DPT=54553 WINDOW=0 RES=0x00 RST URGP=0 
[ 2075.041934] [UFW BLOCK] IN=eth0 OUT= MAC=00:1a:a0:88:c0:af:00:15:f9:2a:93:da:08:00 SRC=174.76.227.113 DST=68.228.32.254 LEN=40 TOS=0x00 PREC=0x00 TTL=60 ID=0 DF PROTO=TCP SPT=80 DPT=54552 WINDOW=0 RES=0x00 RST URGP=0
```

I'm looking for obvious errors. I'll try F1 during boot to see what's going on. Right now I don't want to restart because I'm afraid I won't be able to get back. =\

---

### Post by Grenage on 2011-06-27
Surely the I/O error on SDA3 is worthy of investigation?  A problem with a drive could certainly slow down the boot.

---

### Post by Arazu on 2011-06-27
> **Grenage said:**
> Surely the I/O error on SDA3 is worthy of investigation?  A problem with a drive could certainly slow down the boot.

SDA3 is /home. How would I check that to see what's wrong?

---

### Post by Grenage on 2011-06-27
If you have any drive testing tools, then it can't hurt to run them.  I also see:

```
240.309015] INFO: task ata_aux:27 blocked for more than 120 seconds.
```

and:

```
121.804024] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
```

So might be some mounting/drive issues, all on ATA3.  Notice the time stamps and the difference between them and the previous output.

---

### Post by Arazu on 2011-06-27
Can you please suggest one?

---

### Post by Grenage on 2011-06-27
I tend to just swap out suspect drives, and I appreciate that it's not always possible to do so.  There is some good information here:

[http://www.cyberciti.biz/tips/linux-find-out-if-harddisk-failing.html](http://www.cyberciti.biz/tips/linux-find-out-if-harddisk-failing.html)

So if your drive and board support SMART (they almost certainly do), it's a good place to start.

---

### Post by Arazu on 2011-06-27
Thank you for the link. I'll look into it.

You're right that it's not always possible and sadly in my case that's true. I also don't have a reliable backup because my external drive has the "click of death". I'm not going to power that up until I'm ready to pull everything off of it.

Thanks again for all of your help.

---

### Post by Arazu on 2011-06-27
Well I tried your link but all I get is "permission denied" when I try to run smartctl. I tried it with the --gui flag but I get "GTK not available".

In any event, thanks again. I know I need to get a solid backup ASAP. I might have a drive that I can back up to but I'm not sure. If not I'm going to be burning a ton of disks. =)

---

### Post by Grenage on 2011-06-27
Hi there :)

You may well need to run the tool with root permissions:

```
sudo smartctl
```

---

### Post by Arazu on 2011-06-27
> **Grenage said:**
> Hi there :)

You may well need to run the tool with root permissions:

```
sudo smartctl
```
I tried that and it didn't work. I tried again after I read your post and it did work. I have no idea why it didn't work before. When it said I didn't have permission sudo was the first thing I tried.

In any event the result is: "SMART overall-health self-assessment test result: PASSED"

And this:

```
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0003   164   159   021    Pre-fail  Always       -       4775
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       932
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000e   200   200   051    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   085   085   000    Old_age   Always       -       11282
 10 Spin_Retry_Count        0x0012   100   100   051    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0012   100   100   051    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       931
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       239
193 Load_Cycle_Count        0x0032   200   200   000    Old_age   Always       -       933
194 Temperature_Celsius     0x0022   102   093   000    Old_age   Always       -       45
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0012   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   200   200   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   200   200   051    Old_age   Offline      -       0

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%         0         -

```

Edit: I have no clue what any of that means. =\

---

### Post by Grenage on 2011-06-28
Well to be honest I can't see anything much wrong there; there are certainly no fails.

I'd personally just copy my data to a spare drive and test with that; do you have a spare available?

---

### Post by Arazu on 2011-06-30
Sorry for the late reply. I've been having trouble booting.

I just moved and can't find my box of computer parts. I found a laptop drive that I'm fairly sure is stable but I can't find my dock to mount it.

A little more info:

I tried booting from the F1 terminal and it seems to hang on "/dev/sda3: recovering journal"

It will retry that 4 times then it reports some bad sectors. 34636908 through 34636917 to be specific. After that it goes back to trying sda3 and hangs in the same place.

Edit: What scares me is this. Shouldn't the drive be ignoring those bad sectors and writing elsewhere? I thought drives ignored bad sectors up until a point. I fear I've reached that point.

---

### Post by Grenage on 2011-06-30
> **Arazu said:**
> Sorry for the late reply. I've been having trouble booting.

I just moved and can't find my box of computer parts. I found a laptop drive that I'm fairly sure is stable but I can't find my dock to mount it.

A little more info:

I tried booting from the F1 terminal and it seems to hang on "/dev/sda3: recovering journal"

It will retry that 4 times then it reports some bad sectors. 34636908 through 34636917 to be specific. After that it goes back to trying sda3 and hangs in the same place.

Edit: What scares me is this. Shouldn't the drive be ignoring those bad sectors and writing elsewhere? I thought drives ignored bad sectors up until a point. I fear I've reached that point.

Indeed, that doesn't sound great.  As you say, a drive can handle so many bad sectors, but there's a limit.  When drives start throwing out more and more, there's usually a physical issue such as head misalignment.  Time to swap out that drive!

---

### Post by Arazu on 2011-06-30
The rub is that I can't afford a new drive. I don't trust any of the ones I have in storage as a primary even if I could figure out which box they are in.

I guess the best thing to do is backup what I can and hope it holds out for a little while.

---

### Post by amjjawad on 2011-06-30
[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=how+to+check+for+bad+sector&as_qdr=all&sa=Google+Search&lang=en#1006](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=how+to+check+for+bad+sector&as_qdr=all&sa=Google+Search&lang=en#1006)

Try to check your HDD for bad sector in case there are any.

If you could find any media to backup your important files, then boot your machine from LiveCD or LiveUSB and backup whatever important.

If the same problem will happen again then I don't think it's your HDD.

What's your hardware specification anyway?

---

### Post by Arazu on 2011-06-30
It's a Dell 530S:


AMD Athlon 4400
3 GB ram
ATA 300 - 320 GB drive. That's all it tells me.

---

### Post by amjjawad on 2011-06-30
> **Arazu said:**
> It's a Dell 530S:


AMD Athlon 4400
3 GB ram
ATA 300 - 320 GB drive. That's all it tells me.

Have you checked your HDD for bad sector? in case there are any!

---

### Post by Arazu on 2011-06-30
> **amjjawad said:**
> Have you checked your HDD for bad sector?

I've run smart and every other utility I could find. Nothing finds a bad sector.

---

### Post by amjjawad on 2011-06-30
> **Arazu said:**
> I've run smart and every other utility I could find. Nothing finds a bad sector.

I'm not on Linux now but there was a command like "fdisk" but forgot the full command.

I posted a link for a search result. Did you have a look?

If you have checked then it's not a bad sector issue, it's something else.

I suggest to backup your files so that your data will be safe then you can try some other approaches to find what's the cause of this issue and how to fix it.

---

### Post by Arazu on 2011-06-30
I think it's fsck but I'm reluctant to try because I don't have a solid backup. I need to find my dock so I can backup to the laptop drive I mentioned earlier. Then I need to find the money for a new drive.

Edit: Thanks for all of your help! It's greatly appreciated.

---

### Post by amjjawad on 2011-06-30
> **Arazu said:**
> I think it's fsck but I'm reluctant to try because I don't have a solid backup. I need to find my dock so I can backup to the laptop drive I mentioned earlier. Then I need to find the money for a new drive.

Edit: Thanks for all of your help! It's greatly appreciated.

Yes, backup first if you do have important files you don't want to lose.

How about borrow one from a friend? I mean just in case you're in hurry and want things to be done quickly - just a suggestion :)

Do you have s spare 4GB USB Drive? if yes, you can install Ubuntu on that USB Drive and use it until you fix the other problem.
Your OS will be running from an USB Drive. If the same issue will happen again, then it's definitely not your HDD. You can also disconnect your HDD if you want.
Just another idea.

Installing Ubuntu on USB Drive and choose to install GRUB in the MBR of the USB Drive will do NOTHING to your HDD. As long as the USB is plugged in, you'll be able to boot from the USB. Once you remove it, everything will be back to normal.

I'm suggesting that in case you need your machine to do something important.

---

### Post by Eiji Takanaka on 2011-06-30
Have you tried putting it in the microwave on the "de-frost" setting for a few minutes?

---

### Post by Arazu on 2011-06-30
> **amjjawad said:**
> Yes, backup first if you do have important files you don't want to lose.

How about borrow one from a friend? I mean just in case you're in hurry and want things to be done quickly - just a suggestion :)

Do you have s spare 4GB USB Drive? if yes, you can install Ubuntu on that USB Drive and use it until you fix the other problem.
Your OS will be running from an USB Drive. If the same issue will happen again, then it's definitely not your HDD. You can also disconnect your HDD if you want.
Just another idea.

Installing Ubuntu on USB Drive and choose to install GRUB in the MBR of the USB Drive will do NOTHING to your HDD. As long as the USB is plugged in, you'll be able to boot from the USB. Once you remove it, everything will be back to normal.

I'm suggesting that in case you need your machine to do something important.

The OS isn't the problem. Sda3 is /home. As you said, I need to backup and get out. I cant get back so this is from my cell.

---

### Post by amjjawad on 2011-06-30
To  make it easier for us to follow up: [http://ubuntuforums.org/showthread.php?t=1794029](http://ubuntuforums.org/showthread.php?t=1794029)

> What I would like to do is move the files from my failing HD to the  laptop, find my backup HD and swap it out as primary in my tower, then  copy the files back over.

Could you please explain that in a better way?

---

### Post by Arazu on 2011-06-30
> **amjjawad said:**
> To  make it easier for us to follow up: [http://ubuntuforums.org/showthread.php?t=1794029](http://ubuntuforums.org/showthread.php?t=1794029)



Could you please explain that in a better way?
I wasn't sure if a cross link was acceptable or not considering the topic changed rather drastically which is why I made a new post. Thanks for linking to the new thread.

What I meant was: I need to move the files from the failing disk to the laptop. That will secure the files and give me a temporary computer. Once I find or buy another drive for my tower I'll move the files back over. I'll probably keep them on the laptop too as a mirror.

One interesting thing is that my last boot went pretty much like what I posted but the bad sectors reported had different numbers. That got me thinking about the "recovering journal" message that persists in every boot attempt. Could it be that the file system is just messed up and there is no physical drive damage?

Thanks again for all the great help.

---

### Post by amjjawad on 2011-07-01
> **Arazu said:**
> I wasn't sure if a cross link was acceptable or not considering the topic changed rather drastically which is why I made a new post. Thanks for linking to the new thread.

For me, it's the same subject so I prefer to write in one thread and talk about the same problem rather than two which might get me lost in the process ;)

> What I meant was: I need to move the files from the failing disk to the laptop. That will secure the files and give me a temporary computer. Once I find or buy another drive for my tower I'll move the files back over. I'll probably keep them on the laptop too as a mirror.
That's good idea but we both know it's a temporary solution.
Have you done that already or not yet?  

> One interesting thing is that my last boot went pretty much like what I posted but the bad sectors reported had different numbers. That got me thinking about the "recovering journal" message that persists in every boot attempt. Could it be that the file system is just messed up and there is no physical drive damage?

I remember that I asked you to check the HDD for bad sector but you told me that there is no bad sectors and the problem with /dev/sda3 only, right?
Well, I would backup my files, format, check the HDD and install again.
If you have some space on your current HDD, say 10GB and it's unused, you could use it as your /home partition instead of the current one but I don't want to go to that approach, formatting the whole HDD is of course easier.

I had a HDD which was making some weird sounds. It was working and booting for some time until the day has come and it stopped booting.

Good luck with the backup and hope you managed to sort it out :)

---

### Post by Arazu on 2011-07-06
A late update but it may be helpful to someone out there so I'm posting it.

First, the laptop was in dire need of help. Not exactly the reliable backup I thought it would be.

Second, what I did:

I had left my machine running because of the startup problems. This morning I woke up to find it had locked up. Several hours of boot attempts failed.

We had already identified sda3 as the problem partition but there was no evidence to suggest a failing disk vs. a failing file system. I keep thinking back to "/dev/sda3: Recovering journal". To me that suggested a flaw in the file system.

I had made a fast backup of everything vital so I figured I had nothing to lose.

I booted from a live CD and ran fsck. It found a ton of bad blocks (I previously called them sectors by mistake). I chose to rewrite them figuring a block is fairly small and they are all in a row so I wouldn't be losing a ton of data.

It worked, sort of. My system now goes to the login screen instantly but, there is always a but isn't there, the GUI take a very long time to load.

I believe I've even found the suspect files that caused this mess. It was something on my desktop that I moved into a junk folder to sort out later. That folder is still acting weird. Weird as in no preview for .jpg files and other odd things.

I don't suggest running fsck without a solid backup but I had no means of getting one. I had to take a chance and, aside from the slow GUI load, it seems to have worked.

---

### Post by amjjawad on 2011-07-06
I did not understand. After all of this, do you have a backup for your important data or you don't?

IF YES, then try to create new partition table and format your HDD all over again. 

Some kind of format could fix the issue but I can't post the command unless we're sure it's going to help.

Some bad sectors/blocks can't be fixed.

At the end of the day, even if you'll manage to get it up and running, keep in mind it may fail very soon so better to get new HDD if you couldn't fix the bad blocks issue.

---

### Post by Arazu on 2011-07-06
> **amjjawad said:**
> I did not understand. After all of this, do you have a backup for your important data or you don't?

IF YES, then try to create new partition table and format your HDD all over again. 

Some kind of format could fix the issue but I can't post the command unless we're sure it's going to help.

Some bad sectors/blocks can't be fixed.

At the end of the day, even if you'll manage to get it up and running, keep in mind it may fail very soon so better to get new HDD if you couldn't fix the bad blocks issue.
No, I don't have a solid backup. That isn't possible at the moment.

I spoke too soon. Now I'm having bad sectors reported in disk utility. I guess I'll try fsck again.

I know I need a new HD but I can't afford one. I'm stuck with what I have.

---

