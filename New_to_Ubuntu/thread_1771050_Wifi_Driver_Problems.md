---
title: "Wifi Driver Problems"
date: 2011-05-30
forum: New to Ubuntu
---

### Post by ohgodplshelpme on 2011-05-30
Hello All,

I'm trying to break a 25 yr stint as a slave to Microsoft.  I love the idea of linux.  I am excited to switch to linux.  Only problem is linux seems to be less than thrilled to receive me.

I have (currently & historically) abandoned the switch due to the frustration of not having my wifi card supported by, or unable to find a compatibile driver for, Ubuntu.  I hear it's supposed to be compatible with damn near everything these days, just not me.  

My current attempt has me hunting down a driver for an Intel WiFi Link 5300 AGN.  Does Ubuntu (or any other fairly easy-to-use distro) support this card?  How can I fit the square plug in the round hole?

Any help would be most appreciated.

---

### Post by wildmanne39 on 2011-05-30
> **ohgodplshelpme said:**
> Hello All,

I'm trying to break a 25 yr stint as a slave to Microsoft.  I love the idea of linux.  I am excited to switch to linux.  Only problem is linux seems to be less than thrilled to receive me.

I have (currently & historically) abandoned the switch due to the frustration of not having my wifi card supported by, or unable to find a compatibile driver for, Ubuntu.  I hear it's supposed to be compatible with damn near everything these days, just not me.  

My current attempt has me hunting down a driver for an Intel WiFi Link 5300 AGN.  Does Ubuntu (or any other fairly easy-to-use distro) support this card?  How can I fit the square plug in the round hole?

Any help would be most appreciated.
Hi, I found this post with the same wireless card and he got it working with these instructions so click on this link [http://ubuntuforums.org/showthread.php?t=1756096&highlight=Intel+WiFi+Link+5300+AGN](http://ubuntuforums.org/showthread.php?t=1756096&highlight=Intel+WiFi+Link+5300+AGN) if you have any problem post back here.

---

### Post by ohgodplshelpme on 2011-05-30
Thanks for the reply, but it sounds like we're having different issues.  My fault, I should have been more descriptive in my original post.

I am able to view wireless networks, but not connect, even as far as my router.  No browsing whatsoever.

---

### Post by wolfen69 on 2011-05-30
> **ohgodplshelpme said:**
> Thanks for the reply, but it sounds like we're having different issues.  My fault, I should have been more descriptive in my original post.

I am able to view wireless networks, but not connect, even as far as my router.  No browsing whatsoever.

Try resetting the router to defaults and see if you can connect on an open network. Then we can go from there.

---

### Post by wildmanne39 on 2011-05-30
> **ohgodplshelpme said:**
> Thanks for the reply, but it sounds like we're having different issues.  My fault, I should have been more descriptive in my original post.

I am able to view wireless networks, but not connect, even as far as my router.  No browsing whatsoever.
So it show its connect to the router so your password and all has been entered? Check you web browser and see if it is set to off line mode.Under file work off line in firefox.

---

### Post by ohgodplshelpme on 2011-05-30
> **wolfen69 said:**
> Try resetting the router to defaults and see if you can connect on an open network. Then we can go from there.

I tried that earlier.  I also couldn't connect to a different router, also open, different ISP.

---

### Post by ohgodplshelpme on 2011-05-30
> **wildmanne39 said:**
> So it show its connect to the router so your password and all has been entered? Check you web browser and see if it is set to off line mode.Under file work off line in firefox.

It will not connect.  I get as far as typing in my PW (or not, when I tried to connect to the open router) and it craps out every time.

---

### Post by 3rdalbum on 2011-05-30
After attempting to connect, please post the output of the "dmesg" command so we can see what error messages the kernel/driver is reporting.

---

### Post by ohgodplshelpme on 2011-05-30
[QUOTE][   [    1.437650] registered taskstats version 1
[    1.438249]   Magic number: 11:849:808
[    1.438370] rtc_cmos 00:05: setting system clock to 2011-05-29 23:47:53 UTC (1306712873)
[    1.438373] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.438375] EDD information not available.
[    1.440343] Freeing unused kernel memory: 956k freed
[    1.440651] Write protecting the kernel read-only data: 10240k
[    1.441531] Freeing unused kernel memory: 184k freed
[    1.446950] Freeing unused kernel memory: 1444k freed
[    1.447686] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    1.466680] <30>udev[76]: starting version 167
[    1.710046] usb 1-6: new high speed USB device using ehci_hcd and address 2
[    1.756271] tg3.c:v3.116 (December 3, 2010)
[    1.756442] tg3 0000:08:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.756456] tg3 0000:08:00.0: setting latency timer to 64
[    1.763411] ahci 0000:00:1f.2: version 3.0
[    1.763428] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.763491] ahci 0000:00:1f.2: irq 44 for MSI/MSI-X
[    1.763581] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 4 ports 3 Gbps 0x33 impl SATA mode
[    1.763584] ahci 0000:00:1f.2: flags: 64bit ncq sntf led clo pmp pio slum part ccc sxs 
[    1.763590] ahci 0000:00:1f.2: setting latency timer to 64
[    1.767492] sdhci: Secure Digital Host Controller Interface driver
[    1.767495] sdhci: Copyright(c) Pierre Ossman
[    1.769576] sdhci-pci 0000:09:01.1: SDHCI controller found [1180:0822] (rev 22)
[    1.769593] sdhci-pci 0000:09:01.1: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[    1.771338] scsi0 : ahci
[    1.771459] mmc0: no vmmc regulator found
[    1.772487] Registered led device: mmc0::
[    1.773541] scsi1 : ahci
[    1.773601] mmc0: SDHCI controller on PCI [0000:09:01.1] using DMA
[    1.773851] scsi2 : ahci
[    1.775727] firewire_ohci 0000:09:01.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.775794] scsi3 : ahci
[    1.775902] scsi4 : ahci
[    1.775988] scsi5 : ahci
[    1.776047] ata1: SATA max UDMA/133 abar m2048@0xfc904000 port 0xfc904100 irq 44
[    1.776051] ata2: SATA max UDMA/133 abar m2048@0xfc904000 port 0xfc904180 irq 44
[    1.776053] ata3: DUMMY
[    1.776055] ata4: DUMMY
[    1.776057] ata5: SATA max UDMA/133 abar m2048@0xfc904000 port 0xfc904300 irq 44
[    1.776061] ata6: SATA max UDMA/133 abar m2048@0xfc904000 port 0xfc904380 irq 44
[    1.840162] firewire_ohci: Added fw-ohci device 0000:09:01.0, OHCI v1.10, 4 IR + 4 IT contexts, quirks 0x1
[    1.873342] mmc0: new high speed SDHC card at address 0001
[    1.876649] mmcblk0: mmc0:0001 00000 3.79 GiB 
[    1.877369]  mmcblk0: p1
[    1.887840] tg3 0000:08:00.0: eth0: Tigon3 [partno(BCM95784M) rev 5784100] (PCI Express) MAC address 00:26:b9:01:62:88
[    1.887844] tg3 0000:08:00.0: eth0: attached PHY is 5784 (10/100/1000Base-T Ethernet) (WireSpeed[1])
[    1.887847] tg3 0000:08:00.0: eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[    1.887850] tg3 0000:08:00.0: eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[    2.130105] ata6: SATA link down (SStatus 0 SControl 300)
[    2.130172] ata5: SATA link down (SStatus 0 SControl 300)
[    2.330081] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.330107] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.332105] ata2.00: ATAPI: PLDS DVD+/-RW DL-8ATS, XD13, max UDMA/100
[    2.332658] ata1.00: ATA-8: ST9500420ASG, 0003SDM1, max UDMA/133
[    2.332663] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    2.333261] ata2.00: configured for UDMA/100
[    2.340173] firewire_core: created device fw0: GUID 4a4fc00003862221, S400
[    2.342713] ata1.00: configured for UDMA/133
[    2.342906] scsi 0:0:0:0: Direct-Access     ATA      ST9500420ASG     0003 PQ: 0 ANSI: 5
[    2.343042] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    2.343054] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.343097] sd 0:0:0:0: [sda] Write Protect is off
[    2.343100] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.343134] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.346265] scsi 1:0:0:0: CD-ROM            PLDS     DVD+-RW DL-8ATS  XD13 PQ: 0 ANSI: 5
[    2.350152] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda caddy
[    2.350157] cdrom: Uniform CD-ROM driver Revision: 3.20
[    2.350289] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.350354] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.364462]  sda: sda1 sda2 sda3
[    2.364873] sd 0:0:0:0: [sda] Attached SCSI disk
[    3.301591] EXT4-fs (loop0): mounted filesystem with ordered data mode. Opts: (null)
[    5.245303] <30>udev[353]: starting version 167
[    5.666801] cfg80211: Calling CRDA to update world regulatory domain
[    5.716545] lp: driver loaded but no devices found
[    5.878122] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[    6.143816] [drm] Initialized drm 1.1.0 20060810
[    6.194218] input: Dell WMI hotkeys as /devices/virtual/input/input5
[    6.302833] Linux video capture interface: v2.00
[    6.632301] uvcvideo: Found UVC 1.00 device Laptop_Integrated_Webcam_2M (0c45:63ea)
[    6.637083] input: Laptop_Integrated_Webcam_2M as /devices/pci0000:00/0000:00:1a.7/usb1/1-6/1-6:1.0/input/input6
[    6.637747] usbcore: registered new interface driver uvcvideo
[    6.637750] USB Video Class driver (v1.0.0)
[    6.660365] r852 0000:09:01.3: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[    6.660469] r852: driver loaded succesfully
[    6.723903] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    6.723909] i915 0000:00:02.0: setting latency timer to 64
[    6.803891] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[    6.803895] iwlagn: Copyright(c) 2003-2010 Intel Corporation
[    6.804012] iwlagn 0000:04:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    6.804021] iwlagn 0000:04:00.0: setting latency timer to 64
[    6.804343] iwlagn 0000:04:00.0: Detected Intel(R) Ultimate N WiFi Link 5300 AGN, REV=0x24
[    6.826386] iwlagn 0000:04:00.0: device EEPROM VER=0x120, CALIB=0x4
[    6.826389] iwlagn 0000:04:00.0: Device SKU: 0Xb
[    6.826391] iwlagn 0000:04:00.0: Valid Tx ant: 0X7, Valid Rx ant: 0X7
[    6.827729] iwlagn 0000:04:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[    6.828276] iwlagn 0000:04:00.0: irq 45 for MSI/MSI-X
[    6.829392] i915 0000:00:02.0: irq 46 for MSI/MSI-X
[    6.829399] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    6.829400] [drm] Driver supports precise vblank timestamp query.
[    6.895686] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[    6.896024] fixme: max PWM is zero.
[    6.945219] cfg80211: World regulatory domain updated:
[    6.945223] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[    6.945226] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    6.945229] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    6.945231] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    6.945234] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    6.945237] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    7.047652] iwlagn 0000:04:00.0: loaded firmware version 8.83.5.1 build 33692
[    7.048007] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[    7.127782] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[    7.193985] type=1400 audit(1306738079.244:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=624 comm="apparmor_parser"
[    7.194884] type=1400 audit(1306738079.244:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=624 comm="apparmor_parser"
[    7.195472] type=1400 audit(1306738079.244:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=624 comm="apparmor_parser"
[    7.196337] type=1400 audit(1306738079.244:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=698 comm="apparmor_parser"
[    7.197247] type=1400 audit(1306738079.244:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=698 comm="apparmor_parser"
[    7.197822] type=1400 audit(1306738079.244:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=698 comm="apparmor_parser"
[    7.198677] type=1400 audit(1306738079.244:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=625 comm="apparmor_parser"
[    7.199581] type=1400 audit(1306738079.244:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=625 comm="apparmor_parser"
[    7.200235] type=1400 audit(1306738079.254:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=625 comm="apparmor_parser"
[    7.215435] Synaptics Touchpad, model: 1, fw: 7.2, id: 0x1c0b1, caps: 0xd04733/0xa40000/0xa0000
[    7.259785] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input7
[    7.373025] Console: switching to colour frame buffer device 170x48
[    7.375901] fb0: inteldrmfb frame buffer device
[    7.375903] drm: registered panic notifier
[    7.420542] ACPI Warning: For \_SB_.PCI0.GFX0.DD01._BCL: Return type mismatch - found Integer, expected Package (20110112/nspredef-1053)
[    7.420550] ACPI: Invalid _BCL data
[    7.420776] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input8
[    7.420874] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[    7.421096] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    7.421168] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    7.421242] HDA Intel 0000:00:1b.0: irq 47 for MSI/MSI-X
[    7.421277] HDA Intel 0000:00:1b.0: setting latency timer to 64
[    7.731311] input: HDA Intel Mic at Ext Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[    7.731464] input: HDA Intel HP Out at Ext Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[    7.731545] input: HDA Intel HP Out at Ext Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[    9.818421] Adding 262136k swap on /host/ubuntu/disks/swap.disk.  Priority:-1 extents:1 across:262136k 
[    9.965849] EXT4-fs (loop0): re-mounted. Opts: errors=remount-ro
[   10.464866] type=1400 audit(1306738082.514:11): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=847 comm="apparmor_parser"
[   10.615558] ppdev: user-space parallel port driver
[   12.527817] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   12.529976] tg3 0000:08:00.0: irq 48 for MSI/MSI-X
[   12.632339] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   12.774210] EXT4-fs (loop0): re-mounted. Opts: errors=remount-ro,commit=0
[   14.233394] tg3 0000:08:00.0: eth0: Link is up at 100 Mbps, full duplex
[   14.233398] tg3 0000:08:00.0: eth0: Flow control is on for TX and on for RX
[   14.233839] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   19.147820] EXT4-fs (loop0): re-mounted. Opts: errors=remount-ro,commit=0
[   24.720043] eth0: no IPv6 routers present
[   31.650051] CE: hpet increased min_delta_ns to 20113 nsec
[   81.171581] tg3 0000:08:00.0: eth0: Link is down
[   95.982927] wlan0: authenticate with 94:44:52:10:e4:b3 (try 1)
[   95.985997] wlan0: authenticated
[   95.986037] wlan0: associate with 94:44:52:10:e4:b3 (try 1)
[   95.989748] wlan0: RX AssocResp from 94:44:52:10:e4:b3 (capab=0x411 status=0 aid=1)
[   95.989753] wlan0: associated
[   96.001250] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   96.001325] cfg80211: Calling CRDA for country: US
[   96.005817] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   96.005822] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[   96.005825] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   96.005828] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[   96.005830] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   96.005833] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[   96.005835] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   96.005837] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[   96.005840] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   96.005842] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[   96.005844] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   96.005847] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[   96.005849] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   96.005852] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[   96.005854] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   96.005857] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[   96.005859] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   96.005862] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[   96.005864] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   96.005866] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[   96.005868] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   96.005871] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[   96.005873] cfg80211: Disabling freq 2467 MHz
[   96.005875] cfg80211: Disabling freq 2472 MHz
[   96.005878] cfg80211: Updating information on frequency 5180 MHz for a 20 MHz width channel with regulatory rule:
[   96.005881] cfg80211: 5170000 KHz - 5250000 KHz @  KHz), (300 mBi, 1700 mBm)
[   96.005883] cfg80211: Updating information on frequency 5200 MHz for a 20 MHz width channel with regulatory rule:
[   96.005886] cfg80211: 5170000 KHz - 5250000 KHz @  KHz), (300 mBi, 1700 mBm)
[   96.005888] cfg80211: Updating information on frequency 5220 MHz for a 20 MHz width channel with regulatory rule:
[   96.005890] cfg80211: 5170000 KHz - 5250000 KHz @  KHz), (300 mBi, 1700 mBm)
[   96.005892] cfg80211: Updating information on frequency 5240 MHz for a 20 MHz width channel with regulatory rule:
[   96.005895] cfg80211: 5170000 KHz - 5250000 KHz @  KHz), (300 mBi, 1700 mBm)
[   96.005897] cfg80211: Updating information on frequency 5260 MHz for a 20 MHz width channel with regulatory rule:
[   96.005900] cfg80211: 5250000 KHz - 5330000 KHz @  KHz), (300 mBi, 2000 mBm)
[   96.005902] cfg80211: Updating information on frequency 5280 MHz for a 20 MHz width channel with regulatory rule:
[   96.005905] cfg80211: 5250000 KHz - 5330000 KHz @  KHz), (300 mBi, 2000 mBm)
[   96.005907] cfg80211: Updating information on frequency 5300 MHz for a 20 MHz width channel with regulatory rule:
[   96.005909] cfg80211: 5250000 KHz - 5330000 KHz @  KHz), (300 mBi, 2000 mBm)
[   96.005911] cfg80211: Updating information on frequency 5320 MHz for a 20 MHz width channel with regulatory rule:
[   96.005914] cfg80211: 5250000 KHz - 5330000 KHz @  KHz), (300 mBi, 2000 mBm)
[   96.005916] cfg80211: Updating information on frequency 5500 MHz for a 20 MHz width channel with regulatory rule:
[   96.005919] cfg80211: 5490000 KHz - 5600000 KHz @  KHz), (300 mBi, 2000 mBm)
[   96.005921] cfg80211: Updating information on frequency 5520 MHz for a 20 MHz width channel with regulatory rule:
[   96.005923] cfg80211: 5490000 KHz - 5600000 KHz @  KHz), (300 mBi, 2000 mBm)
[   96.005925] cfg80211: Updating information on frequency 5540 MHz for a 20 MHz width channel with regulatory rule:
[   96.005928] cfg80211: 5490000 KHz - 5600000 KHz @  KHz), (300 mBi, 2000 mBm)
[   96.005930] cfg80211: Updating information on frequency 5560 MHz for a 20 MHz width channel with regulatory rule:
[   96.005933] cfg80211: 5490000 KHz - 5600000 KHz @  KHz), (300 mBi, 2000 mBm)
[   96.005935] cfg80211: Updating information on frequency 5580 MHz for a 20 MHz width channel with regulatory rule:
[   96.005938] cfg80211: 5490000 KHz - 5600000 KHz @  KHz), (300 mBi, 2000 mBm)
[   96.005939] cfg80211: Disabling freq 5600 MHz
[   96.005941] cfg80211: Disabling freq 5620 MHz
[   96.005943] cfg80211: Disabling freq 5640 MHz
[   96.005945] cfg80211: Updating information on frequency 5660 MHz for a 20 MHz width channel with regulatory rule:
[   96.005947] cfg80211: 5650000 KHz - 5710000 KHz @  KHz), (300 mBi, 2000 mBm)
[   96.005950] cfg80211: Updating information on frequency 5680 MHz for a 20 MHz width channel with regulatory rule:
[   96.005952] cfg80211: 5650000 KHz - 5710000 KHz @  KHz), (300 mBi, 2000 mBm)
[   96.005954] cfg80211: Updating information on frequency 5700 MHz for a 20 MHz width channel with regulatory rule:
[   96.005957] cfg80211: 5650000 KHz - 5710000 KHz @  KHz), (300 mBi, 2000 mBm)
[   96.005959] cfg80211: Updating information on frequency 5745 MHz for a 20 MHz width channel with regulatory rule:
[   96.005962] cfg80211: 5735000 KHz - 5835000 KHz @  KHz), (300 mBi, 3000 mBm)
[   96.005964] cfg80211: Updating information on frequency 5765 MHz for a 20 MHz width channel with regulatory rule:
[   96.005966] cfg80211: 5735000 KHz - 5835000 KHz @  KHz), (300 mBi, 3000 mBm)
[   96.005968] cfg80211: Updating information on frequency 5785 MHz for a 20 MHz width channel with regulatory rule:
[   96.005971] cfg80211: 5735000 KHz - 5835000 KHz @  KHz), (300 mBi, 3000 mBm)
[   96.005973] cfg80211: Updating information on frequency 5805 MHz for a 20 MHz width channel with regulatory rule:
[   96.005976] cfg80211: 5735000 KHz - 5835000 KHz @  KHz), (300 mBi, 3000 mBm)
[   96.005978] cfg80211: Updating information on frequency 5825 MHz for a 20 MHz width channel with regulatory rule:
[   96.005980] cfg80211: 5735000 KHz - 5835000 KHz @  KHz), (300 mBi, 3000 mBm)
[   96.005985] cfg80211: Regulatory domain changed to country: US
[   96.005986] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   96.005989] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   96.005992] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[   96.005994] cfg80211:     (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   96.005997] cfg80211:     (5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   96.005999] cfg80211:     (5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   96.006002] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[   96.126612] Intel AES-NI instructions are not detected.
[   96.182471] padlock_aes: VIA PadLock not detected.
[  106.960128] wlan0: no IPv6 routers present
[  142.209865] wlan0: deauthenticating from 94:44:52:10:e4:b3 by local choice (reason=3)
[  142.300208] cfg80211: All devices are disconnected, going to restore regulatory settings
[  142.300222] cfg80211: Restoring regulatory settings
[  142.300238] cfg80211: Calling CRDA to update world regulatory domain
[  142.304878] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[  142.304886] cfg80211: World regulatory domain updated:
[  142.304889] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  142.304893] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  142.304896] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  142.304900] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  142.304903] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  142.304906] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  171.217996] tg3 0000:08:00.0: eth0: Link is up at 100 Mbps, full duplex
[  171.218003] tg3 0000:08:00.0: eth0: Flow control is on for TX and on for RX
[  182.871169] tg3 0000:08:00.0: eth0: Link is down
[  184.486468] tg3 0000:08:00.0: eth0: Link is up at 100 Mbps, full duplex
[  184.486474] tg3 0000:08:00.0: eth0: Flow control is on for TX and on for RX
[  212.963542] tg3 0000:08:00.0: eth0: Link is down
[  253.380906] wlan0: authenticate with 94:44:52:10:e4:b3 (try 1)
[  253.385940] wlan0: authenticated
[  253.385984] wlan0: associate with 94:44:52:10:e4:b3 (try 1)
[  253.389675] wlan0: RX AssocResp from 94:44:52:10:e4:b3 (capab=0x411 status=0 aid=1)
[  253.389680] wlan0: associated
[  253.395960] cfg80211: Calling CRDA for country: US
[  253.400178] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[  253.400182] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[  253.400185] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[  253.400188] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[  253.400190] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[  253.400192] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[  253.400195] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[  253.400197] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[  253.400199] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[  253.400202] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[  253.400204] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[  253.400207] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[  253.400209] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[  253.400211] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[  253.400214] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[  253.400216] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[  253.400218] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[  253.400221] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[  253.400223] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[  253.400226] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[  253.400228] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[  253.400230] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[  253.400232] cfg80211: Disabling freq 2467 MHz
[  253.400234] cfg80211: Disabling freq 2472 MHz
[  253.400236] cfg80211: Updating information on frequency 5180 MHz for a 20 MHz width channel with regulatory rule:
[  253.400239] cfg80211: 5170000 KHz - 5250000 KHz @  KHz), (300 mBi, 1700 mBm)
[  253.400241] cfg80211: Updating information on frequency 5200 MHz for a 20 MHz width channel with regulatory rule:
[  253.400244] cfg80211: 5170000 KHz - 5250000 KHz @  KHz), (300 mBi, 1700 mBm)
[  253.400246] cfg80211: Updating information on frequency 5220 MHz for a 20 MHz width channel with regulatory rule:
[  253.400248] cfg80211: 5170000 KHz - 5250000 KHz @  KHz), (300 mBi, 1700 mBm)
[  253.400251] cfg80211: Updating information on frequency 5240 MHz for a 20 MHz width channel with regulatory rule:
[  253.400253] cfg80211: 5170000 KHz - 5250000 KHz @  KHz), (300 mBi, 1700 mBm)
[  253.400255] cfg80211: Updating information on frequency 5260 MHz for a 20 MHz width channel with regulatory rule:
[  253.400258] cfg80211: 5250000 KHz - 5330000 KHz @  KHz), (300 mBi, 2000 mBm)
[  253.400260] cfg80211: Updating information on frequency 5280 MHz for a 20 MHz width channel with regulatory rule:
[  253.400263] cfg80211: 5250000 KHz - 5330000 KHz @  KHz), (300 mBi, 2000 mBm)
[  253.400265] cfg80211: Updating information on frequency 5300 MHz for a 20 MHz width channel with regulatory rule:
[  253.400268] cfg80211: 5250000 KHz - 5330000 KHz @  KHz), (300 mBi, 2000 mBm)
[  253.400270] cfg80211: Updating information on frequency 5320 MHz for a 20 MHz width channel with regulatory rule:
[  253.400273] cfg80211: 5250000 KHz - 5330000 KHz @  KHz), (300 mBi, 2000 mBm)
[  253.400275] cfg80211: Updating information on frequency 5500 MHz for a 20 MHz width channel with regulatory rule:
[  253.400278] cfg80211: 5490000 KHz - 5600000 KHz @  KHz), (300 mBi, 2000 mBm)
[  253.400280] cfg80211: Updating information on frequency 5520 MHz for a 20 MHz width channel with regulatory rule:
[  253.400283] cfg80211: 5490000 KHz - 5600000 KHz @  KHz), (300 mBi, 2000 mBm)
[  253.400285] cfg80211: Updating information on frequency 5540 MHz for a 20 MHz width channel with regulatory rule:
[  253.400287] cfg80211: 5490000 KHz - 5600000 KHz @  KHz), (300 mBi, 2000 mBm)
[  253.400289] cfg80211: Updating information on frequency 5560 MHz for a 20 MHz width channel with regulatory rule:
[  253.400292] cfg80211: 5490000 KHz - 5600000 KHz @  KHz), (300 mBi, 2000 mBm)
[  253.400294] cfg80211: Updating information on frequency 5580 MHz for a 20 MHz width channel with regulatory rule:
[  253.400297] cfg80211: 5490000 KHz - 5600000 KHz @  KHz), (300 mBi, 2000 mBm)
[  253.400299] cfg80211: Disabling freq 5600 MHz
[  253.400300] cfg80211: Disabling freq 5620 MHz
[  253.400302] cfg80211: Disabling freq 5640 MHz
[  253.400304] cfg80211: Updating information on frequency 5660 MHz for a 20 MHz width channel with regulatory rule:
[  253.400307] cfg80211: 5650000 KHz - 5710000 KHz @  KHz), (300 mBi, 2000 mBm)
[  253.400309] cfg80211: Updating information on frequency 5680 MHz for a 20 MHz width channel with regulatory rule:
[  253.400311] cfg80211: 5650000 KHz - 5710000 KHz @  KHz), (300 mBi, 2000 mBm)
[  253.400313] cfg80211: Updating information on frequency 5700 MHz for a 20 MHz width channel with regulatory rule:
[  253.400316] cfg80211: 5650000 KHz - 5710000 KHz @  KHz), (300 mBi, 2000 mBm)
[  253.400318] cfg80211: Updating information on frequency 5745 MHz for a 20 MHz width channel with regulatory rule:
[  253.400321] cfg80211: 5735000 KHz - 5835000 KHz @  KHz), (300 mBi, 3000 mBm)
[  253.400323] cfg80211: Updating information on frequency 5765 MHz for a 20 MHz width channel with regulatory rule:
[  253.400326] cfg80211: 5735000 KHz - 5835000 KHz @  KHz), (300 mBi, 3000 mBm)
[  253.400328] cfg80211: Updating information on frequency 5785 MHz for a 20 MHz width channel with regulatory rule:
[  253.400330] cfg80211: 5735000 KHz - 5835000 KHz @  KHz), (300 mBi, 3000 mBm)
[  253.400333] cfg80211: Updating information on frequency 5805 MHz for a 20 MHz width channel with regulatory rule:
[  253.400335] cfg80211: 5735000 KHz - 5835000 KHz @  KHz), (300 mBi, 3000 mBm)
[  253.400337] cfg80211: Updating information on frequency 5825 MHz for a 20 MHz width channel with regulatory rule:
[  253.400340] cfg80211: 5735000 KHz - 5835000 KHz @  KHz), (300 mBi, 3000 mBm)
[  253.400344] cfg80211: Regulatory domain changed to country: US
[  253.400346] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  253.400348] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[  253.400351] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[  253.400354] cfg80211:     (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  253.400356] cfg80211:     (5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  253.400359] cfg80211:     (5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  253.400361] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[  299.221596] wlan0: deauthenticating from 94:44:52:10:e4:b3 by local choice (reason=3)
[  299.300357] cfg80211: All devices are disconnected, going to restore regulatory settings
[  299.300367] cfg80211: Restoring regulatory settings
[  299.300384] cfg80211: Calling CRDA to update world regulatory domain
[  299.306600] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[  299.306611] cfg80211: World regulatory domain updated:
[  299.306614] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  299.306619] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  299.306624] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  299.306629] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  299.306634] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  299.306638] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
jonas@ubuntu:~$ 
/QUOTE]

---

### Post by ohgodplshelpme on 2011-05-30
I also notice that after one misconnnect, I can no longer open the networking menu.  I have to log off and then back on.

---

### Post by wildmanne39 on 2011-05-30
> **ohgodplshelpme said:**
> I also notice that after one misconnnect, I can no longer open the networking menu.  I have to log off and then back on.
Bump

---

### Post by ohgodplshelpme on 2011-06-06
Does anyone have any ideas that could help me out?

---

### Post by Immolatus on 2011-06-06
maybe try setting your router to  different channel. It seems from the dump there that certain frequencies are being denied. Is this a US card or Japan?

What are the machine specs???

---

### Post by ohgodplshelpme on 2011-06-06
The card is a Intel WiFi Link 5300 AGN.  Will give a different channel on the router a shot.

what specs do you need?

---

### Post by Immolatus on 2011-06-06
is it a b/g/n card? How old is the machine? What router are you using? Is this a pci card or integrated?
Tell you what, open a terminal and do: lspci

post back the output.:popcorn:

---

### Post by ohgodplshelpme on 2011-06-06
This is just downright bizarre.

After not touching Ubuntu since the lag in this thread (thank god for dual boot), my wifi has come to life!  Maybe the linux gods are finally with me or the channel switch worked and you're a genius- Take your pick!

Thanks for all the help   :)

---

