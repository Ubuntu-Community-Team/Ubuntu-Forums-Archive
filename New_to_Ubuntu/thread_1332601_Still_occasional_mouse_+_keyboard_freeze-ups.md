---
title: "Still occasional mouse + keyboard freeze-ups"
date: 2009-11-20
forum: New to Ubuntu
---

### Post by al.adab on 2009-11-20
ref: [http://ubuntuforums.org/showthread.php?t=1326115](http://ubuntuforums.org/showthread.php?t=1326115)

I thought it's solved. It's not. I re-installed Ubuntu 9.10, did what I described at the thread above (except for installing Grub), it worked fine for a while and now both mouse and keyboard freeze every three/four re-boots. 

As I plug in an external mouse I'm able to re-start the computer. It then usually works (well, three or four re-boots later it happens again) Is this a general problem or does it have do to with the making of my computer (Dell Vostro)? I tested it on windows and both mouse and keyboard work fine.

I'll probably switch back to 9.04 if there's no solution...

---

### Post by al.adab on 2009-11-22
any idea anyone?

---

### Post by al.adab on 2009-11-25
>bump<

---

### Post by ukripper on 2009-11-25
go to System-->Preferences-->Keyboard and change your keyboard in layouts tab to "Dell" and make sure in your /etc/grub.d/40_custom you have "**i8042.reset i8042.nomux i8042.nopnp i8042.noloop**"

---

### Post by al.adab on 2009-11-25
Thanks for your help ukripper. I've done as you say. This is what the sections (where the *quiet splash* is) look like now: 

[I]
linux	/boot/vmlinuz-2.6.31-15-generic root=UUID=281b3f66-e4af-48b9-b0f5-9ad8251aa999 ro quiet splash i8042.reset i8042.nomux i8042.nopnp i8042.noloop
initrd	/boot/initrd.img-2.6.31-15-generic[/I]

Will be testing it for a few days before editing this thread as SOLVED.

---

### Post by ukripper on 2009-11-25
looks good to me. I hope this fixes your problem. Make sure you run ```
sudo update-grub
``` in terminal so these changes will picked up everytime your kernel is updated.

---

### Post by al.adab on 2009-11-26
Just froze again. This is getting annoying. I've now tried to change keyboard layout to Dell 101-key PC (don't ask me why, just trying). Anything else I could try to do? 

Does random freeze-ups make any sense at all, by the way?

---

### Post by ukripper on 2009-11-26
can you post log messages running below command:
```
tail -n 200 /var/log/messages
```

---

### Post by al.adab on 2009-11-26
here you go :) 

$ tail -n 200 /var/log/messages
Nov 26 14:08:45 adab kernel: [    3.199943] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
Nov 26 14:08:45 adab kernel: [    3.199976] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
Nov 26 14:08:45 adab kernel: [    3.200081] device-mapper: uevent: version 1.0.3
Nov 26 14:08:45 adab kernel: [    3.200164] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
Nov 26 14:08:45 adab kernel: [    3.200915] device-mapper: multipath: version 1.1.0 loaded
Nov 26 14:08:45 adab kernel: [    3.200918] device-mapper: multipath round-robin: version 1.0.0 loaded
Nov 26 14:08:45 adab kernel: [    3.201020] EISA: Probing bus 0 at eisa.0
Nov 26 14:08:45 adab kernel: [    3.201027] Cannot allocate resource for EISA slot 1
Nov 26 14:08:45 adab kernel: [    3.201029] Cannot allocate resource for EISA slot 2
Nov 26 14:08:45 adab kernel: [    3.201031] Cannot allocate resource for EISA slot 3
Nov 26 14:08:45 adab kernel: [    3.201033] Cannot allocate resource for EISA slot 4
Nov 26 14:08:45 adab kernel: [    3.201035] Cannot allocate resource for EISA slot 5
Nov 26 14:08:45 adab kernel: [    3.201049] EISA: Detected 0 cards.
Nov 26 14:08:45 adab kernel: [    3.201116] cpuidle: using governor ladder
Nov 26 14:08:45 adab kernel: [    3.201157] cpuidle: using governor menu
Nov 26 14:08:45 adab kernel: [    3.201562] TCP cubic registered
Nov 26 14:08:45 adab kernel: [    3.201694] NET: Registered protocol family 10
Nov 26 14:08:45 adab kernel: [    3.202043] lo: Disabled Privacy Extensions
Nov 26 14:08:45 adab kernel: [    3.202283] NET: Registered protocol family 17
Nov 26 14:08:45 adab kernel: [    3.202300] Bluetooth: L2CAP ver 2.13
Nov 26 14:08:45 adab kernel: [    3.202302] Bluetooth: L2CAP socket layer initialized
Nov 26 14:08:45 adab kernel: [    3.202307] Bluetooth: SCO (Voice Link) ver 0.6
Nov 26 14:08:45 adab kernel: [    3.202308] Bluetooth: SCO socket layer initialized
Nov 26 14:08:45 adab kernel: [    3.202336] Bluetooth: RFCOMM TTY layer initialized
Nov 26 14:08:45 adab kernel: [    3.202338] Bluetooth: RFCOMM socket layer initialized
Nov 26 14:08:45 adab kernel: [    3.202340] Bluetooth: RFCOMM ver 1.11
Nov 26 14:08:45 adab kernel: [    3.202374] Using IPI No-Shortcut mode
Nov 26 14:08:45 adab kernel: [    3.202443] registered taskstats version 1
Nov 26 14:08:45 adab kernel: [    3.202559]   Magic number: 1:534:132
Nov 26 14:08:45 adab kernel: [    3.202612] acpi device:07: hash matches
Nov 26 14:08:45 adab kernel: [    3.202652] rtc_cmos 00:07: setting system clock to 2009-11-26 14:08:31 UTC (1259244511)
Nov 26 14:08:45 adab kernel: [    3.202655] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Nov 26 14:08:45 adab kernel: [    3.202657] EDD information not available.
Nov 26 14:08:45 adab kernel: [    3.238515] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
Nov 26 14:08:45 adab kernel: [    3.287675] ata4.00: ATAPI: Optiarc DVD+/-RW AD-7640A, JD06, max UDMA/33
Nov 26 14:08:45 adab kernel: [    3.300298] ata4.00: configured for UDMA/33
Nov 26 14:08:45 adab kernel: [    3.428031] ata2: SATA link down (SStatus 0 SControl 300)
Nov 26 14:08:45 adab kernel: [    3.428058] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Nov 26 14:08:45 adab kernel: [    3.436030] ata3: SATA link down (SStatus 0 SControl 300)
Nov 26 14:08:45 adab kernel: [    3.464097] ACPI Warning: \_SB_.PCI0.SATA.PRT0._GTF: Return type mismatch - found Integer, expected Buffer 20090521 nspredef-940
Nov 26 14:08:45 adab kernel: [    3.464104] ata1.00: _GTF unexpected object type 0x1
Nov 26 14:08:45 adab kernel: [    3.510426] ata1.00: ATA-8: WDC WD1600BEVT-75ZCT2, 11.01A11, max UDMA/133
Nov 26 14:08:45 adab kernel: [    3.510429] ata1.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 31/32)
Nov 26 14:08:45 adab kernel: [    3.596093] ata1.00: _GTF unexpected object type 0x1
Nov 26 14:08:45 adab kernel: [    3.596258] ata1.00: configured for UDMA/133
Nov 26 14:08:45 adab kernel: [    3.612132] scsi 0:0:0:0: Direct-Access     ATA      WDC WD1600BEVT-7 11.0 PQ: 0 ANSI: 5
Nov 26 14:08:45 adab kernel: [    3.612250] sd 0:0:0:0: Attached scsi generic sg0 type 0
Nov 26 14:08:45 adab kernel: [    3.612283] sd 0:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
Nov 26 14:08:45 adab kernel: [    3.612324] sd 0:0:0:0: [sda] Write Protect is off
Nov 26 14:08:45 adab kernel: [    3.612348] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov 26 14:08:45 adab kernel: [    3.612458]  sda:
Nov 26 14:08:45 adab kernel: [    3.613490] scsi 3:0:0:0: CD-ROM            Optiarc  DVD+-RW AD-7640A JD06 PQ: 0 ANSI: 5
Nov 26 14:08:45 adab kernel: [    3.618578] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda caddy
Nov 26 14:08:45 adab kernel: [    3.618582] Uniform CD-ROM driver Revision: 3.20
Nov 26 14:08:45 adab kernel: [    3.618702] sr 3:0:0:0: Attached scsi generic sg1 type 5
Nov 26 14:08:45 adab kernel: [    3.618826]  sda1 sda2 < sda5 >
Nov 26 14:08:45 adab kernel: [    3.642514] sd 0:0:0:0: [sda] Attached SCSI disk
Nov 26 14:08:45 adab kernel: [    3.728325] Freeing unused kernel memory: 540k freed
Nov 26 14:08:45 adab kernel: [    3.728595] Write protecting the kernel text: 4568k
Nov 26 14:08:45 adab kernel: [    3.728621] Write protecting the kernel read-only data: 1836k
Nov 26 14:08:45 adab kernel: [    3.888157] Linux agpgart interface v0.103
Nov 26 14:08:45 adab kernel: [    3.890899] agpgart-intel 0000:00:00.0: Intel 965GM Chipset
Nov 26 14:08:45 adab kernel: [    3.891104] agpgart-intel 0000:00:00.0: detected 7676K stolen memory
Nov 26 14:08:45 adab kernel: [    3.940071] usb 1-3: new high speed USB device using ehci_hcd and address 2
Nov 26 14:08:45 adab kernel: [    3.940870] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
Nov 26 14:08:45 adab kernel: [    3.994532] ohci1394 0000:08:05.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Nov 26 14:08:45 adab kernel: [    3.997879] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
Nov 26 14:08:45 adab kernel: [    3.997911] r8169 0000:07:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Nov 26 14:08:45 adab kernel: [    3.998755] eth0: RTL8168c/8111c at 0xf81ba000, 00:21:70:f6:de:59, XID 3c4000c0 IRQ 29
Nov 26 14:08:45 adab kernel: [    4.046700] [drm] Initialized drm 1.1.0 20060810
Nov 26 14:08:45 adab kernel: [    4.053851] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[22]  MMIO=[f8200000-f82007ff]  Max Packet=[2048]  IR/IT contexts=[8/8]
Nov 26 14:08:45 adab kernel: [    4.061829] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Nov 26 14:08:45 adab kernel: [    4.572908] [drm] TV-15: set mode NTSC 480i 0
Nov 26 14:08:45 adab kernel: [    4.699547] [drm] fb0: inteldrmfb frame buffer device
Nov 26 14:08:45 adab kernel: [    4.735155] usb 1-3: configuration #1 chosen from 1 choice
Nov 26 14:08:45 adab kernel: [    4.940101] acpi device:0a: registered as cooling_device1
Nov 26 14:08:45 adab kernel: [    4.940327] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:07/input/input6
Nov 26 14:08:45 adab kernel: [    4.940366] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
Nov 26 14:08:45 adab kernel: [    4.940396] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
Nov 26 14:08:45 adab kernel: [    5.011627] [drm] LVDS-8: set mode 1280x800 c
Nov 26 14:08:45 adab kernel: [    5.050874] Console: switching to colour frame buffer device 160x50
Nov 26 14:08:45 adab kernel: [    5.201407] xor: automatically using best checksumming function: pIII_sse
Nov 26 14:08:45 adab kernel: [    5.220008]    pIII_sse  :  6897.000 MB/sec
Nov 26 14:08:45 adab kernel: [    5.220010] xor: using function: pIII_sse (6897.000 MB/sec)
Nov 26 14:08:45 adab kernel: [    5.222741] device-mapper: dm-raid45: initialized v0.2594b
Nov 26 14:08:45 adab kernel: [    5.412657] PM: Starting manual resume from disk
Nov 26 14:08:45 adab kernel: [    5.439972] EXT4-fs (sda1): barriers enabled
Nov 26 14:08:45 adab kernel: [    5.468940] kjournald2 starting: pid 382, dev sda1:8, commit interval 5 seconds
Nov 26 14:08:45 adab kernel: [    5.468952] EXT4-fs (sda1): delayed allocation enabled
Nov 26 14:08:45 adab kernel: [    5.468955] EXT4-fs: file extents enabled
Nov 26 14:08:45 adab kernel: [    5.479638] EXT4-fs: mballoc enabled
Nov 26 14:08:45 adab kernel: [    5.479652] EXT4-fs (sda1): mounted filesystem with ordered data mode
Nov 26 14:08:45 adab kernel: [    6.187074] type=1505 audit(1259244514.483:2): operation="profile_load" pid=405 name=/usr/share/gdm/guest-session/Xsession
Nov 26 14:08:45 adab kernel: [    6.189811] type=1505 audit(1259244514.485:3): operation="profile_load" pid=406 name=/sbin/dhclient3
Nov 26 14:08:45 adab kernel: [    6.190548] type=1505 audit(1259244514.485:4): operation="profile_load" pid=406 name=/usr/lib/NetworkManager/nm-dhcp-client.action
Nov 26 14:08:45 adab kernel: [    6.190949] type=1505 audit(1259244514.485:5): operation="profile_load" pid=406 name=/usr/lib/connman/scripts/dhclient-script
Nov 26 14:08:45 adab kernel: [    6.246732] type=1505 audit(1259244514.541:6): operation="profile_load" pid=407 name=/usr/bin/evince
Nov 26 14:08:45 adab kernel: [    6.258767] type=1505 audit(1259244514.553:7): operation="profile_load" pid=407 name=/usr/bin/evince-previewer
Nov 26 14:08:45 adab kernel: [    6.265837] type=1505 audit(1259244514.561:8): operation="profile_load" pid=407 name=/usr/bin/evince-thumbnailer
Nov 26 14:08:45 adab kernel: [    6.319570] type=1505 audit(1259244514.613:9): operation="profile_load" pid=409 name=/usr/bin/freshclam
Nov 26 14:08:45 adab kernel: [    6.344941] type=1505 audit(1259244514.641:10): operation="profile_load" pid=410 name=/usr/lib/cups/backend/cups-pdf
Nov 26 14:08:45 adab kernel: [    6.345802] type=1505 audit(1259244514.641:11): operation="profile_load" pid=410 name=/usr/sbin/cupsd
Nov 26 14:08:45 adab kernel: [   16.921522] udev: starting version 147
Nov 26 14:08:45 adab kernel: [   16.935034] lp: driver loaded but no devices found
Nov 26 14:08:45 adab kernel: [   16.959039] Adding 6008268k swap on /dev/sda5.  Priority:-1 extents:1 across:6008268k 
Nov 26 14:08:45 adab kernel: [   17.215836] EXT4-fs (sda1): internal journal on sda1:8
Nov 26 14:08:45 adab kernel: [   17.514652] r8169: eth0: link down
Nov 26 14:08:45 adab kernel: [   17.514866] ADDRCONF(NETDEV_UP): eth0: link is not ready
Nov 26 14:08:45 adab kernel: [   17.663907] __ratelimit: 3 callbacks suppressed
Nov 26 14:08:45 adab kernel: [   17.663911] type=1505 audit(1259244525.957:13): operation="profile_replace" pid=680 name=/usr/share/gdm/guest-session/Xsession
Nov 26 14:08:46 adab kernel: [   17.710147] type=1505 audit(1259244526.005:14): operation="profile_replace" pid=723 name=/sbin/dhclient3
Nov 26 14:08:46 adab kernel: [   17.710884] type=1505 audit(1259244526.005:15): operation="profile_replace" pid=723 name=/usr/lib/NetworkManager/nm-dhcp-client.action
Nov 26 14:08:46 adab kernel: [   17.711283] type=1505 audit(1259244526.005:16): operation="profile_replace" pid=723 name=/usr/lib/connman/scripts/dhclient-script
Nov 26 14:08:46 adab kernel: [   17.715945] type=1505 audit(1259244526.009:17): operation="profile_replace" pid=724 name=/usr/bin/evince
Nov 26 14:08:46 adab kernel: [   17.870293] cfg80211: Calling CRDA to update world regulatory domain
Nov 26 14:08:46 adab kernel: [   17.902563] type=1505 audit(1259244526.197:18): operation="profile_replace" pid=724 name=/usr/bin/evince-previewer
Nov 26 14:08:46 adab kernel: [   17.970419] type=1505 audit(1259244526.265:19): operation="profile_replace" pid=724 name=/usr/bin/evince-thumbnailer
Nov 26 14:08:46 adab kernel: [   18.021487] type=1505 audit(1259244526.317:20): operation="profile_replace" pid=967 name=/usr/bin/freshclam
Nov 26 14:08:46 adab kernel: [   18.023565] type=1505 audit(1259244526.317:21): operation="profile_replace" pid=968 name=/usr/lib/cups/backend/cups-pdf
Nov 26 14:08:46 adab kernel: [   18.024459] type=1505 audit(1259244526.321:22): operation="profile_replace" pid=968 name=/usr/sbin/cupsd
Nov 26 14:08:46 adab kernel: [   18.026410] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks
Nov 26 14:08:46 adab kernel: [   18.026413] iwl3945: Copyright(c) 2003-2009 Intel Corporation
Nov 26 14:08:46 adab kernel: [   18.026547] iwl3945 0000:06:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Nov 26 14:08:46 adab kernel: [   18.042168] sdhci: Secure Digital Host Controller Interface driver
Nov 26 14:08:46 adab kernel: [   18.042171] sdhci: Copyright(c) Pierre Ossman
Nov 26 14:08:46 adab kernel: [   18.043460] sdhci-pci 0000:08:05.2: SDHCI controller found [1217:7120] (rev 2)
Nov 26 14:08:46 adab kernel: [   18.043480] sdhci-pci 0000:08:05.2: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Nov 26 14:08:46 adab kernel: [   18.043549] Registered led device: mmc0::
Nov 26 14:08:46 adab kernel: [   18.043584] mmc0: SDHCI controller on PCI [0000:08:05.2] using DMA
Nov 26 14:08:46 adab kernel: [   18.045106] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
Nov 26 14:08:46 adab kernel: [   18.231566] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Nov 26 14:08:46 adab kernel: [   18.232414] input: Dell WMI hotkeys as /devices/virtual/input/input7
Nov 26 14:08:46 adab kernel: [   18.272113] iwl3945 0000:06:00.0: Tunable channels: 13 802.11bg, 23 802.11a channels
Nov 26 14:08:46 adab kernel: [   18.272118] iwl3945 0000:06:00.0: Detected Intel Wireless WiFi Link 3945ABG
Nov 26 14:08:46 adab kernel: [   18.323264] hda_codec: Unknown model for ALC268, trying auto-probe from BIOS...
Nov 26 14:08:46 adab kernel: [   18.323350] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input8
Nov 26 14:08:46 adab kernel: [   18.487460] Linux video capture interface: v2.00
Nov 26 14:08:46 adab kernel: [   18.519636] uvcvideo: Found UVC 1.00 device Integrated Webcam (0c45:63e0)
Nov 26 14:08:46 adab kernel: [   18.543017] input: Integrated Webcam as /devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3:1.0/input/input9
Nov 26 14:08:46 adab kernel: [   18.543071] usbcore: registered new interface driver uvcvideo
Nov 26 14:08:46 adab kernel: [   18.543074] USB Video Class driver (v0.1.0)
Nov 26 14:08:46 adab kernel: [   18.688444] cfg80211: World regulatory domain updated:
Nov 26 14:08:46 adab kernel: [   18.688447] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Nov 26 14:08:46 adab kernel: [   18.688450] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Nov 26 14:08:46 adab kernel: [   18.688453] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Nov 26 14:08:46 adab kernel: [   18.688455] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Nov 26 14:08:46 adab kernel: [   18.688457] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Nov 26 14:08:46 adab kernel: [   18.688460] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Nov 26 14:08:47 adab kernel: [   18.751107] ip_tables: (C) 2000-2006 Netfilter Core Team
Nov 26 14:08:47 adab kernel: [   18.787441] iwl3945 0000:06:00.0: firmware: requesting iwlwifi-3945-2.ucode
Nov 26 14:08:47 adab kernel: [   18.856725] iwl3945 0000:06:00.0: loaded firmware version 15.32.2.9
Nov 26 14:08:47 adab kernel: [   18.999315] Registered led device: iwl-phy0::radio
Nov 26 14:08:47 adab kernel: [   18.999336] Registered led device: iwl-phy0::assoc
Nov 26 14:08:47 adab kernel: [   18.999397] Registered led device: iwl-phy0::RX
Nov 26 14:08:47 adab kernel: [   18.999413] Registered led device: iwl-phy0::TX
Nov 26 14:08:47 adab kernel: [   19.008209] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Nov 26 14:08:47 adab kernel: [   19.238943] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
Nov 26 14:08:47 adab kernel: [   19.239130] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Please use
Nov 26 14:08:47 adab kernel: [   19.239132] nf_conntrack.acct=1 kernel parameter, acct=1 nf_conntrack module option or
Nov 26 14:08:47 adab kernel: [   19.239134] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
Nov 26 14:08:47 adab kernel: [   19.448667] input: PS/2 Mouse as /devices/platform/i8042/serio1/input/input10
Nov 26 14:08:47 adab kernel: [   19.500153] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input11
Nov 26 14:08:48 adab kernel: [   20.082104] ppdev: user-space parallel port driver
Nov 26 14:08:48 adab kernel: [   20.152635] [drm] TV-15: set mode NTSC 480i 0
Nov 26 14:08:48 adab kernel: [   20.316076] [drm] TV-15: set mode NTSC 480i 0
Nov 26 14:08:48 adab kernel: [   20.588588] [drm] TV-15: set mode NTSC 480i 0
Nov 26 14:08:49 adab kernel: [   20.733366] [drm] TV-15: set mode NTSC 480i 0
Nov 26 14:08:52 adab kernel: [   23.771984] [drm] TV-15: set mode NTSC 480i 0
Nov 26 14:08:52 adab kernel: [   23.917521] [drm] TV-15: set mode NTSC 480i 0
Nov 26 14:08:52 adab kernel: [   24.196603] [drm] TV-15: set mode NTSC 480i 0
Nov 26 14:08:52 adab kernel: [   24.340048] [drm] TV-15: set mode NTSC 480i 0
Nov 26 14:08:52 adab kernel: [   24.628774] [drm] TV-15: set mode NTSC 480i 0
Nov 26 14:08:53 adab kernel: [   24.774925] [drm] TV-15: set mode NTSC 480i 0
Nov 26 14:09:03 adab kernel: [   35.081700] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Nov 26 14:09:09 adab python: hp-systray[1944]: warning: No hp: or hpfax: devices found in any installed CUPS queue. Exiting.
Nov 26 16:42:18 adab kernel: [ 9230.446785] Inbound IN=wlan0 OUT= MAC=00:1b:77:bc:6f:ff:00:18:de:c2:a2:b8:08:00 SRC=192.168.100.29 DST=192.168.100.16 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=3637 PROTO=UDP SPT=137 DPT=137 LEN=58 
Nov 26 16:42:20 adab kernel: [ 9231.755312] Inbound IN=wlan0 OUT= MAC=00:1b:77:bc:6f:ff:00:18:de:c2:a2:b8:08:00 SRC=192.168.100.29 DST=192.168.100.16 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=3712 PROTO=UDP SPT=137 DPT=137 LEN=58 
Nov 26 16:42:21 adab kernel: [ 9233.255576] Inbound IN=wlan0 OUT= MAC=00:1b:77:bc:6f:ff:00:18:de:c2:a2:b8:08:00 SRC=192.168.100.29 DST=192.168.100.16 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=3816 PROTO=UDP SPT=137 DPT=137 LEN=58 
Nov 26 16:42:24 adab kernel: [ 9236.256083] Inbound IN=wlan0 OUT= MAC=00:1b:77:bc:6f:ff:00:18:de:c2:a2:b8:08:00 SRC=192.168.100.29 DST=192.168.100.16 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=4023 PROTO=UDP SPT=137 DPT=137 LEN=58 
Nov 26 16:42:26 adab kernel: [ 9237.755861] Inbound IN=wlan0 OUT= MAC=00:1b:77:bc:6f:ff:00:18:de:c2:a2:b8:08:00 SRC=192.168.100.29 DST=192.168.100.16 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=4129 PROTO=UDP SPT=137 DPT=137 LEN=58 
Nov 26 16:42:27 adab kernel: [ 9239.255498] Inbound IN=wlan0 OUT= MAC=00:1b:77:bc:6f:ff:00:18:de:c2:a2:b8:08:00 SRC=192.168.100.29 DST=192.168.100.16 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=4235 PROTO=UDP SPT=137 DPT=137 LEN=58 
Nov 26 16:42:29 adab kernel: [ 9240.757599] Inbound IN=wlan0 OUT= MAC=00:1b:77:bc:6f:ff:00:18:de:c2:a2:b8:08:00 SRC=192.168.100.29 DST=192.168.100.16 LEN=48 TOS=0x00 PREC=0x00 TTL=128 ID=4338 DF PROTO=TCP SPT=1118 DPT=80 WINDOW=16384 RES=0x00 SYN URGP=0 
Nov 26 16:42:31 adab kernel: [ 9243.657473] Inbound IN=wlan0 OUT= MAC=00:1b:77:bc:6f:ff:00:18:de:c2:a2:b8:08:00 SRC=192.168.100.29 DST=192.168.100.16 LEN=48 TOS=0x00 PREC=0x00 TTL=128 ID=4502 DF PROTO=TCP SPT=1118 DPT=80 WINDOW=16384 RES=0x00 SYN URGP=0 
Nov 26 16:42:37 adab kernel: [ 9249.630707] Inbound IN=wlan0 OUT= MAC=00:1b:77:bc:6f:ff:00:18:de:c2:a2:b8:08:00 SRC=192.168.100.29 DST=192.168.100.16 LEN=48 TOS=0x00 PREC=0x00 TTL=128 ID=4810 DF PROTO=TCP SPT=1118 DPT=80 WINDOW=16384 RES=0x00 SYN URGP=0 
Nov 26 16:42:49 adab kernel: [ 9261.696382] Inbound IN=wlan0 OUT= MAC=00:1b:77:bc:6f:ff:00:18:de:c2:a2:b8:08:00 SRC=192.168.100.29 DST=192.168.100.16 LEN=68 TOS=0x00 PREC=0x00 TTL=128 ID=5618 PROTO=UDP SPT=1116 DPT=161 LEN=48 
Nov 26 16:42:52 adab kernel: [ 9263.946338] Inbound IN=wlan0 OUT= MAC=00:1b:77:bc:6f:ff:00:18:de:c2:a2:b8:08:00 SRC=192.168.100.29 DST=192.168.100.16 LEN=68 TOS=0x00 PREC=0x00 TTL=128 ID=5624 PROTO=UDP SPT=1116 DPT=161 LEN=48 
Nov 26 16:42:54 adab kernel: [ 9265.961728] Inbound IN=wlan0 OUT= MAC=00:1b:77:bc:6f:ff:00:18:de:c2:a2:b8:08:00 SRC=192.168.100.29 DST=192.168.100.16 LEN=40 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=TCP SPT=5000 DPT=80 WINDOW=512 RES=0x00 SYN URGP=0 
Nov 26 16:42:56 adab kernel: [ 9268.228374] Inbound IN=wlan0 OUT= MAC=00:1b:77:bc:6f:ff:00:18:de:c2:a2:b8:08:00 SRC=192.168.100.29 DST=192.168.100.16 LEN=40 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=TCP SPT=5000 DPT=80 WINDOW=512 RES=0x00 SYN URGP=0 
Nov 26 16:42:58 adab kernel: [ 9270.336535] Inbound IN=wlan0 OUT= MAC=00:1b:77:bc:6f:ff:00:1c:f0:e7:5f:e1:08:00 SRC=192.168.100.29 DST=192.168.100.16 LEN=40 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=TCP SPT=5000 DPT=139 WINDOW=512 RES=0x00 SYN URGP=0 
Nov 26 16:43:00 adab kernel: [ 9272.524005] Inbound IN=wlan0 OUT= MAC=00:1b:77:bc:6f:ff:00:18:de:c2:a2:b8:08:00 SRC=192.168.100.29 DST=192.168.100.16 LEN=40 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=TCP SPT=5000 DPT=139 WINDOW=512 RES=0x00 SYN URGP=0 
Nov 26 16:43:03 adab kernel: [ 9274.714120] Inbound IN=wlan0 OUT= MAC=00:1b:77:bc:6f:ff:00:18:de:c2:a2:b8:08:00 SRC=192.168.100.29 DST=192.168.100.16 LEN=40 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=TCP SPT=5000 DPT=445 WINDOW=512 RES=0x00 SYN URGP=0 
Nov 26 16:43:05 adab kernel: [ 9276.898810] Inbound IN=wlan0 OUT= MAC=00:1b:77:bc:6f:ff:00:18:de:c2:a2:b8:08:00 SRC=192.168.100.29 DST=192.168.100.16 LEN=40 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=TCP SPT=5000 DPT=445 WINDOW=512 RES=0x00 SYN URGP=0 
Nov 26 16:43:07 adab kernel: [ 9279.086717] Inbound IN=wlan0 OUT= MAC=00:1b:77:bc:6f:ff:00:18:de:c2:a2:b8:08:00 SRC=192.168.100.29 DST=192.168.100.16 LEN=28 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=5000 DPT=137 LEN=8 
Nov 26 16:43:09 adab kernel: [ 9281.273924] Inbound IN=wlan0 OUT= MAC=00:1b:77:bc:6f:ff:00:18:de:c2:a2:b8:08:00 SRC=192.168.100.29 DST=192.168.100.16 LEN=28 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=5000 DPT=137 LEN=8 
Nov 26 16:43:11 adab kernel: [ 9283.461741] Inbound IN=wlan0 OUT= MAC=00:1b:77:bc:6f:ff:00:18:de:c2:a2:b8:08:00 SRC=192.168.100.29 DST=192.168.100.16 LEN=28 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=5000 DPT=138 LEN=8 
Nov 26 16:43:13 adab kernel: [ 9285.649492] Inbound IN=wlan0 OUT= MAC=00:1b:77:bc:6f:ff:00:18:de:c2:a2:b8:08:00 SRC=192.168.100.29 DST=192.168.100.16 LEN=28 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=5000 DPT=138 LEN=8 
Nov 26 16:43:16 adab kernel: [ 9287.889394] Inbound IN=wlan0 OUT= MAC=00:1b:77:bc:6f:ff:00:18:de:c2:a2:b8:08:00 SRC=192.168.100.29 DST=192.168.100.16 LEN=28 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=5000 DPT=10421 LEN=8 
Nov 26 16:43:18 adab kernel: [ 9290.024576] Inbound IN=wlan0 OUT= MAC=00:1b:77:bc:6f:ff:00:18:de:c2:a2:b8:08:00 SRC=192.168.100.29 DST=192.168.100.16 LEN=28 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=5000 DPT=10421 LEN=8 
Nov 26 16:43:20 adab kernel: [ 9292.212346] Inbound IN=wlan0 OUT= MAC=00:1b:77:bc:6f:ff:00:18:de:c2:a2:b8:08:00 SRC=192.168.100.29 DST=192.168.100.16 LEN=28 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=5000 DPT=10426 LEN=8 
Nov 26 16:43:22 adab kernel: [ 9294.442036] Inbound IN=wlan0 OUT= MAC=00:1b:77:bc:6f:ff:00:18:de:c2:a2:b8:08:00 SRC=192.168.100.29 DST=192.168.100.16 LEN=28 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=5000 DPT=10426 LEN=8

---

### Post by ukripper on 2009-11-26
Have you got compiz enabled? Can you go into System-->preferences-->Appearence-->go to Visual effects tab and select none.

And let us know if it still freezes

---

### Post by al.adab on 2009-11-26
It's not enabled. In fact, I disabled it first things first after re-installing 9.10, to no avail. It does still freeze, despite disabling it.

Is this the only way of disabling Compiz?

---

### Post by ukripper on 2009-11-26
can you post output of lspci:
```
lspci
```

---

### Post by al.adab on 2009-11-26
here it is: 

~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
06:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
08:05.0 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
08:05.2 SD Host controller: O2 Micro, Inc. Integrated MMC/SD Controller (rev 02)
08:05.3 Mass storage controller: O2 Micro, Inc. Integrated MS/xD Controller (rev 01)

---

### Post by ukripper on 2009-11-26
Does freeze up happens when you using any particular app like firefox or watching some video online?

---

### Post by al.adab on 2009-11-26
No, it happens after booting the machine and when the desktop appears. The mouse cursor is stuck right in the middle of the screen, and the only way out is either to press the power button (and the machine will turn itself off after some 20secs or so) or plug in an external mouse and re-boot the machine. Notice that the keyboard also doesn't respond when this happens. Usually everything is back to normality after re-booting it.

---

### Post by ukripper on 2009-11-26
here is the bug reports for your intel 965 chipset - [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/298532](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/298532)
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/345119](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/345119)

---

### Post by al.adab on 2009-11-26
Could you please tell me how to disable this "reflection plugin"? I really appreciate the effort. This is very kind.

---

### Post by al.adab on 2009-11-26
I tried this 

~$ locate reflex
/home/daniele/.cache/compizconfig/reflex.pb
/usr/lib/compiz/libreflex.a
/usr/lib/compiz/libreflex.la
/usr/lib/compiz/libreflex.so
/usr/share/compiz/reflex.xml
/usr/share/gconf/schemas/compiz-reflex.schemas

but don't know how to proceed from here...

---

### Post by al.adab on 2009-11-26
...or where / how to find a Compiz Configuration Settings Manager or something of the sort (if that's the right path to walk down anyway)...

---

### Post by al.adab on 2009-11-26
don't really know what implications this might have, but that's what I've done: 

*sudo apt-get remove compiz*

if compiz is what I think it is - and I don't need it as what I only need is open office to work properly (and maybe watch the occasional film or look at the occasional photo)...

I now need to make sure that by removing compiz I also removed that "reflex" bug described above...?

---

### Post by ukripper on 2009-11-26
remove compiz config settings manager it should remove reflection window too but you told earlier you don't have compiz enabled so it shouldn't effect.

---

### Post by al.adab on 2009-11-26
so what should I do with this bug?

---

### Post by ukripper on 2009-11-27
you can follow the steps in the link and add you output to the bug report there. [https://wiki.ubuntu.com/X/Troubleshooting/Freeze#How%20to%20Get%20a%20Batchbuffer%20Dump%20%28-intel%20only%29](https://wiki.ubuntu.com/X/Troubleshooting/Freeze#How%20to%20Get%20a%20Batchbuffer%20Dump%20%28-intel%20only%29)


For time being I'd suggest best option would be to try different releases like 9.04 or 8.04 lts

---

### Post by al.adab on 2009-11-28
OK. Thanks so much for your help. I've in fact reverted to 9.04.

---

