---
title: "Confusion trying to mount USB Stick"
date: 2009-06-12
forum: New to Ubuntu
---

### Post by MaxVK on 2009-06-12
Hi there. I'm running Jaunty.

I have a *working* USB stick (Tested and working on 3 Windows systems) that I want to mount in Ubuntu. When I plug it in the little light on the USB Stick starts to flash, but nothing else happens.

If I scan the results of dmesg (below) I *think* that the stick is being found as sdc/sdd, but there is no sdc/d in /dev/.

Iv read a few articles that suggest using /dev/sda1 to mount the stick, but sda* and sdb* are all used by my hard disks, and since there are no other sd* items in /dev I'm not sure what to mount it as, or indeed, how!

Can anyone help please.

The last half of the results of dmesg is below.

cheers

Max

```
[    2.258606] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.259027] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 22
[    2.259037] ehci_hcd 0000:00:02.2: PCI INT C -> Link[APCL] -> GSI 22 (level, high) -> IRQ 22
[    2.259065] ehci_hcd 0000:00:02.2: setting latency timer to 64
[    2.259069] ehci_hcd 0000:00:02.2: EHCI Host Controller
[    2.259134] ehci_hcd 0000:00:02.2: new USB bus registered, assigned bus number 1
[    2.259172] ehci_hcd 0000:00:02.2: selective suspend/wakeup unavailable
[    2.259180] ehci_hcd 0000:00:02.2: debug port 1
[    2.259185] ehci_hcd 0000:00:02.2: cache line size of 64 is not supported
[    2.259204] ehci_hcd 0000:00:02.2: irq 22, io mem 0xe5006000
[    2.268019] ehci_hcd 0000:00:02.2: USB 2.0 started, EHCI 1.00
[    2.268097] usb usb1: configuration #1 chosen from 1 choice
[    2.268126] hub 1-0:1.0: USB hub found
[    2.268138] hub 1-0:1.0: 6 ports detected
[    2.268245] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.268583] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 21
[    2.268588] ohci_hcd 0000:00:02.0: PCI INT A -> Link[APCF] -> GSI 21 (level, high) -> IRQ 21
[    2.268600] ohci_hcd 0000:00:02.0: setting latency timer to 64
[    2.268603] ohci_hcd 0000:00:02.0: OHCI Host Controller
[    2.268647] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 2
[    2.268670] ohci_hcd 0000:00:02.0: irq 21, io mem 0xe5002000
[    2.326066] usb usb2: configuration #1 chosen from 1 choice
[    2.326091] hub 2-0:1.0: USB hub found
[    2.326102] hub 2-0:1.0: 3 ports detected
[    2.326506] ACPI: PCI Interrupt Link [APCG] enabled at IRQ 20
[    2.326511] ohci_hcd 0000:00:02.1: PCI INT B -> Link[APCG] -> GSI 20 (level, high) -> IRQ 20
[    2.326522] ohci_hcd 0000:00:02.1: setting latency timer to 64
[    2.326525] ohci_hcd 0000:00:02.1: OHCI Host Controller
[    2.326575] ohci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 3
[    2.326597] ohci_hcd 0000:00:02.1: irq 20, io mem 0xe5005000
[    2.382056] usb usb3: configuration #1 chosen from 1 choice
[    2.382081] hub 3-0:1.0: USB hub found
[    2.382091] hub 3-0:1.0: 3 ports detected
[    2.382177] uhci_hcd: USB Universal Host Controller Interface driver
[    2.382264] PNP: PS/2 Controller [PNP0f13:PS2M] at 0x60,0x64 irq 12
[    2.382267] PNP: PS/2 controller doesn't have KBD irq; using default 1
[    2.384658] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.384664] serio: i8042 AUX port at 0x60,0x64 irq 12
[    2.384789] mice: PS/2 mouse device common for all mice
[    2.384937] rtc_cmos 00:06: RTC can wake from S4
[    2.384984] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    2.385010] rtc0: alarms up to one year, y3k, 242 bytes nvram
[    2.385071] device-mapper: uevent: version 1.0.3
[    2.385189] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
[    2.385251] device-mapper: multipath: version 1.0.5 loaded
[    2.385255] device-mapper: multipath round-robin: version 1.0.0 loaded
[    2.385329] EISA: Probing bus 0 at eisa.0
[    2.385351] Cannot allocate resource for EISA slot 4
[    2.385354] Cannot allocate resource for EISA slot 5
[    2.385369] EISA: Detected 0 cards.
[    2.385414] cpuidle: using governor ladder
[    2.385416] cpuidle: using governor menu
[    2.385932] TCP cubic registered
[    2.386021] NET: Registered protocol family 10
[    2.386429] lo: Disabled Privacy Extensions
[    2.386738] NET: Registered protocol family 17
[    2.386760] Bluetooth: L2CAP ver 2.11
[    2.386761] Bluetooth: L2CAP socket layer initialized
[    2.386765] Bluetooth: SCO (Voice Link) ver 0.6
[    2.386766] Bluetooth: SCO socket layer initialized
[    2.386795] Bluetooth: RFCOMM socket layer initialized
[    2.386804] Bluetooth: RFCOMM TTY layer initialized
[    2.386806] Bluetooth: RFCOMM ver 1.10
[    2.386826] powernow-k8: Processor cpuid 6a0 not supported
[    2.386847] Using IPI No-Shortcut mode
[    2.386933] registered taskstats version 1
[    2.387041]   Magic number: 13:623:689
[    2.387150] rtc_cmos 00:06: setting system clock to 2009-06-12 15:40:44 UTC (1244821244)
[    2.387154] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.387156] EDD information not available.
[    2.387742] Freeing unused kernel memory: 532k freed
[    2.387862] Write protecting the kernel text: 4112k
[    2.387900] Write protecting the kernel read-only data: 1524k
[    2.948034] usb 2-1: new low speed USB device using ohci_hcd and address 2
[    2.953874] Floppy drive(s): fd0 is 1.44M
[    2.971952] FDC 0 is a post-1991 82077
[    3.050221] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
[    3.050622] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 22
[    3.050627] forcedeth 0000:00:04.0: PCI INT A -> Link[APCH] -> GSI 22 (level, high) -> IRQ 22
[    3.050633] forcedeth 0000:00:04.0: setting latency timer to 64
[    3.050709] nv_probe: set workaround bit for reversed mac addr
[    3.182647] usb 2-1: configuration #1 chosen from 1 choice
[    3.488059] usb 3-1: new full speed USB device using ohci_hcd and address 2
[    3.498674] usbcore: registered new interface driver hiddev
[    3.498779] usbcore: registered new interface driver usbhid
[    3.498782] usbhid: v2.6:USB HID core driver
[    3.516503] input: Microsoft Natural&#65533; Ergonomic Keyboard 4000 as /devices/pci0000:00/0000:00:02.0/usb2/2-1/2-1:1.0/input/input3
[    3.518922] microsoft 0003:045E:00DB.0001: input,hidraw0: USB HID v1.11 Keyboard [Microsoft Natural&#65533; Ergonomic Keyboard 4000] on usb-0000:00:02.0-1/input0
[    3.534250] input: Microsoft Natural&#65533; Ergonomic Keyboard 4000 as /devices/pci0000:00/0000:00:02.0/usb2/2-1/2-1:1.1/input/input4
[    3.536848] microsoft 0003:045E:00DB.0002: input,hidraw1: USB HID v1.11 Device [Microsoft Natural&#65533; Ergonomic Keyboard 4000] on usb-0000:00:02.0-1/input1
[    3.569701] forcedeth 0000:00:04.0: ifname eth0, PHY OUI 0x732 @ 1, addr 00:50:8d:fd:e9:05
[    3.569706] forcedeth 0000:00:04.0: timirq lnktim desc-v1
[    3.571856] ACPI: PCI Interrupt Link [APCM] enabled at IRQ 21
[    3.571864] ohci1394 0000:00:0d.0: PCI INT A -> Link[APCM] -> GSI 21 (level, high) -> IRQ 21
[    3.571870] ohci1394 0000:00:0d.0: setting latency timer to 64
[    3.623846] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[21]  MMIO=[e5003000-e50037ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    3.725163] usb 3-1: configuration #1 chosen from 1 choice
[    3.762954] PM: Starting manual resume from disk
[    3.762959] PM: Resume from partition 8:6
[    3.762960] PM: Checking hibernation image.
[    3.763144] PM: Resume from disk failed.
[    3.810832] kjournald starting.  Commit interval 5 seconds
[    3.810846] EXT3-fs: mounted filesystem with ordered data mode.
[    4.746409] ohci1394: fw-host0: SelfID received outside of bus reset sequence
[    5.016146] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[000000508dfee905]
[    9.502542] udev: starting version 141
[    9.684272] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x5000
[    9.684352] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x5100
[    9.693401] Linux agpgart interface v0.103
[    9.696316] agpgart: Detected NVIDIA nForce2 chipset
[    9.712167] agpgart-nvidia 0000:00:00.0: AGP aperture is 256M @ 0xc0000000
[    9.752932] parport_pc 00:0c: reported by Plug and Play ACPI
[    9.753057] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[    9.825648] input: Wacom Intuos3 6x8 as /devices/pci0000:00/0000:00:02.1/usb3/3-1/3-1:1.0/input/input5
[    9.864447] usbcore: registered new interface driver wacom
[    9.864492] wacom: v1.49:USB Wacom Graphire and Wacom Intuos tablet driver
[    9.898391] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   10.682519] nvidia: module license 'NVIDIA' taints kernel.
[   10.941949] ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19
[   10.941962] nvidia 0000:02:00.0: PCI INT A -> Link[APC4] -> GSI 19 (level, high) -> IRQ 19
[   10.943722] NVRM: loading NVIDIA UNIX x86 Kernel Module  180.44  Mon Mar 23 14:59:10 PST 2009
[   11.033680] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[   11.116241] input: PC Speaker as /devices/platform/pcspkr/input/input6
[   11.152767] ppdev: user-space parallel port driver
[   11.196332] gameport: EMU10K1 is pci0000:01:09.1/gameport0, io 0xc400, speed 59659kHz
[   11.375322] ACPI: PCI Interrupt Link [APC2] enabled at IRQ 17
[   11.375334] EMU10K1_Audigy 0000:01:09.0: PCI INT A -> Link[APC2] -> GSI 17 (level, high) -> IRQ 17
[   11.392068] Control name 'Sigmatel Surround Phase Inversion Playback Switch' truncated to 'Sigmatel Surround Phase Inversion Playback '
[   11.514675] psmouse serio1: ID: 10 00 64<4>logips2pp: Detected unknown logitech mouse model 109
[   11.611093] lp0: using parport0 (interrupt-driven).
[   11.732563] Adding 971892k swap on /dev/sda6.  Priority:-1 extents:1 across:971892k
[   12.063776] input: ImExPS/2 Logitech Explorer Mouse as /devices/platform/i8042/serio1/input/input7
[   80.027826] EXT3 FS on sda1, internal journal
[   80.742896] kjournald starting.  Commit interval 5 seconds
[   80.743131] EXT3 FS on sda5, internal journal
[   80.743137] EXT3-fs: mounted filesystem with ordered data mode.
[   80.775480] kjournald starting.  Commit interval 5 seconds
[   80.775487] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
[   80.775710] EXT3 FS on sdb1, internal journal
[   80.775714] EXT3-fs: mounted filesystem with ordered data mode.
[   80.813615] kjournald starting.  Commit interval 5 seconds
[   80.813623] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
[   80.813869] EXT3 FS on sdb2, internal journal
[   80.813872] EXT3-fs: mounted filesystem with ordered data mode.
[   80.850663] kjournald starting.  Commit interval 5 seconds
[   80.850670] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
[   80.850947] EXT3 FS on sdb3, internal journal
[   80.850951] EXT3-fs: mounted filesystem with ordered data mode.
[   81.011353] type=1505 audit(1244821323.120:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2691
[   81.069706] type=1505 audit(1244821323.180:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2695
[   81.069933] type=1505 audit(1244821323.180:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2695
[   81.070016] type=1505 audit(1244821323.180:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2695
[   81.070094] type=1505 audit(1244821323.180:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2695
[   81.243280] type=1505 audit(1244821323.352:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2700
[   81.243616] type=1505 audit(1244821323.352:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2700
[   81.277947] type=1505 audit(1244821323.388:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2704
[   85.072026] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   85.072030] Bluetooth: BNEP filters: protocol multicast
[   85.112247] Bridge firewalling registered
[   87.774563] agpgart-nvidia 0000:00:00.0: AGP 3.0 bridge
[   87.774579] agpgart-nvidia 0000:00:00.0: putting AGP V3 device into 8x mode
[   87.774639] nvidia 0000:02:00.0: putting AGP V3 device into 8x mode
[  100.648015] eth0: no IPv6 routers present
[  147.800568] ondemand governor failed, too long transition latency of HW, fallback to performance governor
[ 5029.088043] usb 1-2: new high speed USB device using ehci_hcd and address 4
[ 5029.244055] usb 1-2: configuration #1 chosen from 1 choice
[ 5029.271835] Initializing USB Mass Storage driver...
[ 5029.273581] scsi2 : SCSI emulation for USB Mass Storage devices
[ 5029.273853] usbcore: registered new interface driver usb-storage
[ 5029.273863] USB Mass Storage support registered.
[ 5029.295225] usb-storage: device found at 4
[ 5029.295229] usb-storage: waiting for device to settle before scanning
[ 5034.292156] usb-storage: device scan complete
[ 5034.292632] scsi 2:0:0:0: Direct-Access              USB DISK 2.0     PMAP PQ: 0 ANSI: 0 CCS
[ 5034.292990] scsi 2:0:0:1: Direct-Access              USB DISK 2.0     PMAP PQ: 0 ANSI: 0 CCS
[ 5035.320038] sd 2:0:0:0: [sdc] 2006016 512-byte hardware sectors: (1.02 GB/979 MiB)
[ 5035.320521] sd 2:0:0:0: [sdc] Write Protect is off
[ 5035.320524] sd 2:0:0:0: [sdc] Mode Sense: 23 00 00 00
[ 5035.320526] sd 2:0:0:0: [sdc] Assuming drive cache: write through
[ 5035.323154] sd 2:0:0:0: [sdc] 2006016 512-byte hardware sectors: (1.02 GB/979 MiB)
[ 5035.323647] sd 2:0:0:0: [sdc] Write Protect is off
[ 5035.323649] sd 2:0:0:0: [sdc] Mode Sense: 23 00 00 00
[ 5035.323652] sd 2:0:0:0: [sdc] Assuming drive cache: write through
[ 5035.323658]  sdc:<6>usb 1-2: reset high speed USB device using ehci_hcd and address 4
[ 5069.596045] end_request: I/O error, dev fd0, sector 0
[ 5081.224036] usb 1-2: device descriptor read/64, error -110
[ 5096.440039] usb 1-2: device descriptor read/64, error -110
[ 5096.656039] usb 1-2: reset high speed USB device using ehci_hcd and address 4
[ 5111.768027] usb 1-2: device descriptor read/64, error -110
[ 5126.984028] usb 1-2: device descriptor read/64, error -110
[ 5127.200024] usb 1-2: reset high speed USB device using ehci_hcd and address 4
[ 5137.608024] usb 1-2: device not accepting address 4, error -110
[ 5137.720023] usb 1-2: reset high speed USB device using ehci_hcd and address 4
[ 5148.128047] usb 1-2: device not accepting address 4, error -110
[ 5148.128109] sd 2:0:0:0: Device offlined - not ready after error recovery
[ 5148.128125] sd 2:0:0:0: [sdc] Result: hostbyte=DID_ABORT driverbyte=DRIVER_OK,SUGGEST_OK
[ 5148.128130] end_request: I/O error, dev sdc, sector 0
[ 5148.128136] Buffer I/O error on device sdc, logical block 0
[ 5148.128191] sd 2:0:0:0: rejecting I/O to offline device
[ 5148.128195] Buffer I/O error on device sdc, logical block 0
[ 5148.128214] sd 2:0:0:0: rejecting I/O to offline device
[ 5148.128216] Buffer I/O error on device sdc, logical block 0
[ 5148.128227] sd 2:0:0:0: rejecting I/O to offline device
[ 5148.128230] Buffer I/O error on device sdc, logical block 0
[ 5148.128237] sd 2:0:0:0: rejecting I/O to offline device
[ 5148.128239] Buffer I/O error on device sdc, logical block 0
[ 5148.128245] ldm_validate_partition_table(): Disk read failed.
[ 5148.128250] sd 2:0:0:0: rejecting I/O to offline device
[ 5148.128252] Buffer I/O error on device sdc, logical block 0
[ 5148.128259] sd 2:0:0:0: rejecting I/O to offline device
[ 5148.128261] Buffer I/O error on device sdc, logical block 0
[ 5148.128268] sd 2:0:0:0: rejecting I/O to offline device
[ 5148.128270] Buffer I/O error on device sdc, logical block 0
[ 5148.128277] sd 2:0:0:0: rejecting I/O to offline device
[ 5148.128280] Buffer I/O error on device sdc, logical block 0
[ 5148.128284] Dev sdc: unable to read RDB block 0
[ 5148.128289] sd 2:0:0:0: rejecting I/O to offline device
[ 5148.128292] Buffer I/O error on device sdc, logical block 0
[ 5148.128299] sd 2:0:0:0: rejecting I/O to offline device
[ 5148.128313] sd 2:0:0:0: rejecting I/O to offline device
[ 5148.128320] sd 2:0:0:0: rejecting I/O to offline device
[ 5148.128327] sd 2:0:0:0: rejecting I/O to offline device
[ 5148.128334] sd 2:0:0:0: rejecting I/O to offline device
[ 5148.128338]  unable to read partition table
[ 5148.131131] usb 1-2: USB disconnect, address 4
[ 5148.131374] sd 2:0:0:0: [sdc] Attached SCSI removable disk
[ 5148.131435] sd 2:0:0:0: Attached scsi generic sg4 type 0
[ 5148.131586] sd 2:0:0:1: [sdd] READ CAPACITY failed
[ 5148.131589] sd 2:0:0:1: [sdd] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 5148.131593] sd 2:0:0:1: [sdd] Sense not available.
[ 5148.131609] sd 2:0:0:1: [sdd] Write Protect is off
[ 5148.131611] sd 2:0:0:1: [sdd] Mode Sense: 00 00 00 00
[ 5148.131614] sd 2:0:0:1: [sdd] Assuming drive cache: write through
[ 5148.131700] sd 2:0:0:1: [sdd] Attached SCSI removable disk
[ 5148.131746] sd 2:0:0:1: Attached scsi generic sg5 type 0
[ 5148.248229] usb 1-2: new high speed USB device using ehci_hcd and address 5
[ 5163.360033] usb 1-2: device descriptor read/64, error -110
[ 5178.576035] usb 1-2: device descriptor read/64, error -110
[ 5178.792035] usb 1-2: new high speed USB device using ehci_hcd and address 6
[ 5193.904038] usb 1-2: device descriptor read/64, error -110
[ 5209.120028] usb 1-2: device descriptor read/64, error -110
[ 5209.336027] usb 1-2: new high speed USB device using ehci_hcd and address 7
[ 5219.744028] usb 1-2: device not accepting address 7, error -110
[ 5219.856038] usb 1-2: new high speed USB device using ehci_hcd and address 8
[ 5230.264017] usb 1-2: device not accepting address 8, error -110
[ 5230.264036] hub 1-0:1.0: unable to enumerate USB device on port 2
[ 5230.720064] usb 2-2: new full speed USB device using ohci_hcd and address 3
```

---

### Post by blueridgedog on 2009-06-12
Is the stick plugged in to a hub or your PC?

What is the output of 

```
sudo fdisk -l
```

when the disk is plugged in?

---

### Post by MaxVK on 2009-06-13
Hi blueridgedog, thanks for replying:

Yes, the stick is plugged into the PC, directly into the rear ports, rather than at the front (The front ones are add-ons and are slower I think).

As you can see below, the stick is not even found.

cheers

Max


```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xea31ea31

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3043    24442866   83  Linux
/dev/sda2            3044        9729    53705295    5  Extended
/dev/sda5            3044        9608    52733331   83  Linux
/dev/sda6            9609        9729      971901   82  Linux swap / Solaris

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x16fb214c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        2432    19535008+  83  Linux
/dev/sdb2           13700       24321    85321215   83  Linux
/dev/sdb3            2433       13699    90502177+  83  Linux

Partition table entries are not in disk order
```

[Edit]
BTW: Iv tried plugging it into the front ports too, but with the same lack of success.

---

### Post by blueridgedog on 2009-06-13
Is it formated as NTFS or FAT32?  As a testing step, I suggest you reformat it (using the windows systems you mentioned) to FAT32.

---

### Post by halitech on 2009-06-13
before you format it, check with Gparted (Partition Editor) to see if that sees it. I've had drives before that Fdisk won't see but Gparted does.

---

### Post by MaxVK on 2009-06-13
Thanks, yes, it is FAT32, and to make sure Iv formatted it in Windows twice (This is a step that many articles suggest) and it has formatted correctly and with no errors, both times..

GParted does not see it at all, although the management program in Windows XP/Vista does. As far as I can tell, nothing in Ubuntu sees the stick at all except for dmesg (above)

cheers

Max

---

### Post by PureLoneWolf on 2009-06-13
Can you look under /media to see if it is there - /dev is the device list, not the normal mount point.

It sounds like you don't have volumes visible on your desktop, which can be enabled by running gconf-editor in a terminal, then going to Apps/Nautilus/Desktop and clicking the volumes_visible checkbox.

---

### Post by MaxVK on 2009-06-13
Thanks for your time:

Volumes_Visible is set to true already (I checked anyway).

In /media I have:
cdrom
cdrom0
cdrom1
musb -> This one I added while following an article, but I have no
     -> idea how to actually use it now that its there (The article wasn't
     -> much help since it wanted to mount at sda1, which is taken)
floppy
floppy0
Storage1 -> These three are partitions on another drive
Storage2 -> that I named myself
Storage3 -> They are simply storage space

As you see, the stick doesn't exist in /media as such. The 'musb' folder was added while I followed an article, but the next command line was something along the lines of:

sudo mount /dev/sda1/ ........

I didn't go through with this since sda and sdb are both used by my hard disks (Indeed they are all to be found in /dev/), which leaves me at the point of having a folder in /media for the stick, but not knowing what it is I need to do to mount it there (Assuming thats the right thing to be doing at this point in any case!).

regards

Max

---

### Post by 3rdalbum on 2009-06-13
That's odd - from your dmesg there's some sort of error occurring that is stopping the kernel and the device from negotiating a communications channel.

So, no, I don't believe the flash drive will even have an entry in /dev. If it does, then it should be /dev/sdc or /dev/sdd - try plugging that into your mount command.

Is there anything unusual about this USB stick? It doesn't have one of those annoying locked partitions on it when you plug it into the Windows PC?

And do other USB flash drives work on your Ubuntu machine?

---

### Post by MaxVK on 2009-06-13
In /dev there is no sdc or sdd etc, which is why I'm getting confused trying to mount the thing. If I use /dev/sdc etc all I get is a message saying that its not found (Which makes sense because its not there!).

As far as I know there is nothing weird about the stick - It has worked in multiple machines, but yes, there is a small partition on it, although I don't know if its locked or not (From what you just said Id guess that it is though).

As for other USB sticks, yes, Iv had others working on this machine, including this stick under Windows when I still had a dual boot on here.

I take it that this partition is a problem, but is it one that I can get around?

cheers


Max

---

### Post by MaxVK on 2009-06-16
Just a quick bump:

Is there any way to get this USB stick working on Ubuntu? Iv had a look around at (Windows) methods of removing the partitions and creating a single one, but so far Iv not found anything that would do the job without me being required to pay for it, and if thats the case Ill just buy a new USB stick for much less money!

Any ideas?

cheers

Max

---

### Post by blueridgedog on 2009-06-16
I don't think it is the stick.

Googling your error produced a wealth of information:

[http://www.google.com/search?hl=en&client=firefox-a&rls=com.ubuntu%3Aen-US%3Aunofficial&hs=QNr&q=%22device+not+accepting+address%22+usb&aq=f&oq=&aqi=](http://www.google.com/search?hl=en&client=firefox-a&rls=com.ubuntu%3Aen-US%3Aunofficial&hs=QNr&q=%22device+not+accepting+address%22+usb&aq=f&oq=&aqi=)

This site: [http://www.linux-usb.org/FAQ.html](http://www.linux-usb.org/FAQ.html)

Had the following:

```

Q:  Why doesn't USB work at all? I get "device not accepting address".

A: This can be one of several problems:

    * High speed devices sometimes have problems with cables used to connect them. They're more sensitive to signal quality issues than older usb 1.1 full or low speed devices. If the device works OK at full speed on the same system, after you "rmmod ehci-hcd", this is likely the problem you're seeing. There are a lot of things you can do to change signal quality.
          o Use a different cable. Some are even marketed specifically for use with high speed devices. Most USB 1.1 cables work just fine at high speed, but the one you're using might be an exception (maybe it's been damaged).
          o Switch to a different USB connector on your computer. Back panel connectors are often right on the motherboard, with much care taken to preserve signal quality. A front panel connector probably doesn't use cabling designed with USB in mind; and its cable could be damaged by bending, baking or something else even when it's not routed through the power supply.
          o Use an external high speed hub. Those hubs have signal conditioning circuitry that may cover up certain flaws.
          o Make sure your device is using its own external power supply, or that its battery is fully charged. 
      You might be able to get the same device to work at high speed on a different machine.
    * You may have some problem with your PCI setup that's preventing your USB host controller from getting hardware interrupts. (Current Linux 2.6 kernels will actually tell you when they notice this problem; see the "dmesg" output.) When Linux submits a request, but never hears back from the controller, this is the diagnostic you'll see. To see if this is the problem, look at /proc/interrupts to see if the interrupt count for your host controller driver ever goes up. If it doesn't, this is the problem: either your BIOS isn't telling the truth to Linux (ACPI sometimes confuses these things, or setting the expected OS to windows in your BIOS), or Linux doesn't understand what it's saying.
    * Sometimes a BIOS fix will be available for your motherboard, and in other cases a more recent kernel will have a Linux fix. You may be able to work around this by passing the noapic boot option to your kernel, or (when you're using an add-in PCI card) moving the USB adapter to some other PCI slot. If you're using a current kernel and BIOS, report this problem to the Linux-kernel mailing list, with details about your motherboard and BIOS.
```

On this forum, it was suggested to unload ehci_hcd:
```

sudo rmmod ehci_hcd
```

I would try as a first step.

---

### Post by MaxVK on 2009-06-16
It seems that there is an error with ehci_hcd that was around when Jaunty was still in beta ([ref]("http://ubuntuforums.org/archive/index.php/t-1113343.html")).

I get:
ERROR: Module ehci_hcd does not exist in /proc/modules

Its not looking good for this USB Stick.

cheers

Max

---

### Post by callan79 on 2009-06-16
> **MaxVK said:**
> Is there any way to get this USB stick working on Ubuntu? Iv had a look around at (Windows) methods of removing the partitions and creating a single one, but so far Iv not found anything that would do the job without me being required to pay for it, and if thats the case Ill just buy a new USB stick for much less money!




Hi Max,

Interesting problem. I'm not sure you're going to have a lot of success with that stick, not even messing with partitions, since your system can't actually talk to the stick at all - let along create/delete partitions.

I've had similar issues in the past with 'cheap' USB devices, or high-speed USB devices connected via an extension cable and/or front panel USB ports. These problems were actually in Windows, before I discovered Ubuntu :-)

Is your USB stick a good one? Or a cheapie?

Given they are so cheap these days, I'd dive down your local store and grab one ... let us know how you go!

Cheers
Callan

---

### Post by MaxVK on 2009-06-16
Hi Callan, no its a cheapie, but it (still) works fine in Windows. Apparently its not a U3 stick (I got a Windows tool to remove the whole U3 thing, but it doesn't recognize the stick as U3, although Windows finds and uses the stick just fine).

Iv read someplace that removing the partitions (there are two) and creating a single large one will help, but so far Iv been unable to do even that.

I think you might be right - A new stick might be in order.

cheers

Max

---

### Post by BambooClaw on 2009-07-04
I had trouble with USB flash drive and CF card reader not mounting. The problem was that the module usb_storage was not being loaded by the OS. So run
sudo modprobe -i usb_storage
before plugging in the drives and see if they are now recognised. 

If so then a more permanent solution is to add usb_storage to the end of your /etc/modules file.

For the record, USB flash drive reading was working fine before I upgraded  to Jaunty, during Jaunty I was having problems.

---

### Post by MaxVK on 2009-07-05
> **BambooClaw said:**
> I had trouble with USB flash drive and CF card reader not mounting. The problem was that the module usb_storage was not being loaded by the OS. So run
sudo modprobe -i usb_storage
before plugging in the drives and see if they are now recognised. 

If so then a more permanent solution is to add usb_storage to the end of your /etc/modules file.

For the record, USB flash drive reading was working fine before I upgraded  to Jaunty, during Jaunty I was having problems.

Cheers BambooClaw. I tried that but to no avail, and Iv a feeling that its the USB Pen rather than anything else. To test this point for myself I now have another USB Key, this time a Maxell, and it starts up fine as soon as its plugged in.

I think the old one is just not going to work with Ubuntu.

Cheers

Max

---

### Post by pppoposition on 2009-07-07
> **MaxVK said:**
> 
I think the old one is just not going to work with Ubuntu.


Hello [MaxVK]("http://www.uluga.ubuntuforums.org/member.php?u=465705")!

Don't lose your hope! While it works in Windows and you reported having it worked in Ubuntu before, there should not be any hardware, cable, "cheap one" or other issues. This drive just has to work. Period.

The problem is that the current Ubuntu you are using prevents it from working.

Some people advice that this might be a problem with wrong kernel modules being used for your USB drive. They say that it might be possible that a USB 1.1 kernel module is loaded and used prior to USB 2.0 module. According to them, this results in communication errors, while your USB drive is surely USB 2.0, but the kernel is trying to communicate with it using USB 1.1 kernel module.

If that was the case, it would be possible to address it by unloading the USB 1.1 kernel modules. I don't know exactly which modules are responsible for USB 1.1 communication and might need to be unloaded. But I think that:

ehci_hcd is the kernel module for USB 2.0,
ohci_hcd is the kernel module for USB 1.1 and
usb-storage is the "USB Mass Storage driver for Linux" (according to modinfo)

But this is most probably not your case, as from the dmesg you posted it is clear that it is the ehci_hcd kernel module which is trying to establish communication with your USB drive.
> 
[ 5148.248229] usb 1-2: new high speed USB device using ehci_hcd and address 5
 And this should be okay.

The fact that you reported this error:
> 
Module ehci_hcd does not exist in /proc/modules
just means that your ehci_hcd kernel module is built directly into your kernel, and you don't need to load it, but also are unable to unload it. You can probably disable it by echoing to some /proc file, but I am not sure of that. And also, I don't know if this is what will help.

The dmesg you posted in the beginning suggests that you have both ehci_hcd and ohci_hcd kernel modules loaded and working. Also, there are messages from usb-storage, which means that you also have this kernel module loaded and working.

So, I assume that the problem will be somewhere else. Maybe there are some options which are necessary to be supplied to these kernel modules upon loading to work correctly, but I am not sure.

I would try to look into dmesg you reported and search for references of similar errors. For example, "device not accepting address 7, error -110" might be a good start.

I know I have not helped much, but I hope that I at least brought a few ideas to think of and to try.

Have a nice day!

---

### Post by MaxVK on 2009-07-07
Thanks pppoposition, but for the sake of about £4 I have another pen that works the moment its plugged in. As frustrating as it is to find that something that previously worked no longer does, the fact remains that the old pen still works fine on Windows machines, and has now been allocated to the kids, who play games and do homework on Windows.

It seems an awful lot of work to get a single USB stick working, and since I have a nice shiny new one now I really cant be bothered to spend the time trying to get the old one going again.

Thanks for your efforts though

regards

Max

---

### Post by Justin2 on 2009-07-09
Have you tried the stick in Kubuntu. I've got a problem with one USB stick not mounting in UBUNTU (GNOME). In windows the stick gets recoginised as USB flash drive as well as a cdrom drive. This USB stick doesn't work and refuses to mount in Ubuntu 9.04 and other Ubuntu versions but Sabayon Linux and Kubuntu 9.04 (KDE) are able to mount it. It mounts it as "vfat" drive even though its been formatted as Fat32

---

### Post by AlmaTlust on 2009-07-09
very nice to see that just recently someone else had the very same problem I'm experiencing right now... My stick's not recognised either. Funny thing, it used to be, and 2 other sticks are recognised without problems. It's an 8g stick and I put a lot of files (two versions of MS office directory trees, >1g in total) on it. Still windows recognises it no problem.
dmesg isn't any different from working sticks...

output of dmesg:
[10006.808205] usb 2-2: new high speed USB device using ehci_hcd and address 10
[10006.944327] usb 2-2: configuration #1 chosen from 1 choice
[10006.949144] scsi11 : SCSI emulation for USB Mass Storage devices
[10006.949632] usb-storage: device found at 10
[10006.949637] usb-storage: waiting for device to settle before scanning
[10011.949288] usb-storage: device scan complete
[10011.950010] scsi 11:0:0:0: Direct-Access     JetFlash TS8GJFV35        8.07 PQ: 0 ANSI: 2
[10011.951740] sd 11:0:0:0: [sdb] 15974400 512-byte hardware sectors: (8.17 GB/7.61 GiB)
[10011.952233] sd 11:0:0:0: [sdb] Write Protect is off
[10011.952236] sd 11:0:0:0: [sdb] Mode Sense: 03 00 00 00
[10011.952239] sd 11:0:0:0: [sdb] Assuming drive cache: write through
[10012.006602] sd 11:0:0:0: [sdb] 15974400 512-byte hardware sectors: (8.17 GB/7.61 GiB)
[10012.007096] sd 11:0:0:0: [sdb] Write Protect is off
[10012.007099] sd 11:0:0:0: [sdb] Mode Sense: 03 00 00 00
[10012.007103] sd 11:0:0:0: [sdb] Assuming drive cache: write through
[10012.007109]  sdb: sdb1
[10012.093183] sd 11:0:0:0: [sdb] Attached SCSI removable disk
[10012.093275] sd 11:0:0:0: Attached scsi generic sg2 type 0

output of fdisk -l:
martin@martin-laptop:~$ sudo fdisk -l

Platte /dev/sda: 320.0 GByte, 320072933376 Byte
255 Köpfe, 63 Sektoren/Spuren, 38913 Zylinder
Einheiten = Zylinder von 16065 × 512 = 8225280 Bytes
Disk identifier: 0xd8000000

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System
/dev/sda1   *           1       37782   303483883+  83  Linux
/dev/sda2           37783       38913     9084757+   5  Erweiterte
/dev/sda5           37783       38913     9084726   82  Linux Swap / Solaris

Platte /dev/sdb: 8178 MByte, 8178892800 Byte
252 Köpfe, 62 Sektoren/Spuren, 1022 Zylinder
Einheiten = Zylinder von 15624 × 512 = 7999488 Bytes
Disk identifier: 0xffffffff

Festplatte /dev/sdb enthält keine gültige Partitionstabelle

funny, isn't it? Windows has no problem with the stick

---

### Post by thedirtymexican on 2009-07-29
Hi guys,

I struggled with this problem on my laptop running 9.04. I searched high and low for a solution and managed to find few good explainations. It seems that USB devices have a 2 ways they can get spoken to:

1. old way (usb 1.1 devices): device is queried 8 bytes, then 16 bytes, then 32 bytes and 64 bytes until the device descriptor is discovered.
2. new way (hi-speed devices): qurey 64 bytes.

Unfortunantly some devices only allow old or new (some both). If the device is not queried in the right way, then it results in the error you are seeing.

The solution that worked for me:
```
sudo vi /etc/modprobe.d/options.conf

#add this line
options usbcore use_both_schemes=y
```[FONT=Verdana]

This forces the usb_code module to try both. Once I added this, my HDD was detected normally.
[/FONT]

---

### Post by candtalan on 2009-09-21
having this same trouble with a wubi install of ubuntu 9.04

the usb mouse works great but usb sticks (512mb and 4gb) are just left flashing and do not mount.

Machine is 
ibm thinkpad type 1871 
model 23737 cg

however
 when the machine is run from the same 9.04 cd live cd then the 512mb usb stick was recognised normally once, then after that, neither the 512mb nor the 4gb were recognised, the lights just kept flashing

any ideas please?
tia



afterthought:
I used sudo gedit to do this:

sudo vi /etc/modprobe.d/options.conf
#add this line
options usbcore use_both_schemes=y

the file did not seem to exist so I created it (I think)
and restarted, however the problem remained unchanged

---

