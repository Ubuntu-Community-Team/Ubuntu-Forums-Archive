---
title: "webcam settings"
date: 2011-07-01
forum: New to Ubuntu
---

### Post by helphelp on 2011-07-01
Hello
I've got a mikomi web cam. It's  brightness is low,
I would like to change the settings but it does not come with any options for that.
If someone knows how i could  change the brightness i would be grateful.
thank you

---

### Post by androssofer on 2011-07-01
this of any help?

[https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)

---

### Post by helphelp on 2011-07-01
> **androssofer said:**
> this of any help?

[https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)

Hi,
I tried that but now my computer does no detect my cam.

---

### Post by androssofer on 2011-07-01
tried rebooting...?

try typing 

```
dmesg
```

into the terminal, c if it says anything about it....

---

### Post by helphelp on 2011-07-01
> **androssofer said:**
> tried rebooting...?

try typing 

```
dmesg
```into the terminal, c if it says anything about it....

Hi,
Sorry computer does detect web cam ( on cheese  )
It's on quvcview that it says :
  unable to open device    
  please make sure the camera is connected and the correct driver installed


ain, max_eirp)
[   52.404331] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   52.404335] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   52.404338] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   52.404341] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   52.404345] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   53.813198] wlan0: authenticate with 00:17:9a:63:43:5f (try 1)
[   53.815053] wlan0: authenticated
[   53.815281] wlan0: associate with 00:17:9a:63:43:5f (try 1)
[   53.817175] wlan0: RX AssocResp from 00:17:9a:63:43:5f (capab=0x431 status=0 aid=1)
[   53.817180] wlan0: associated
[   58.824026] wlan0: no IPv6 routers present
[  144.132734] process `skype' is using obsolete setsockopt SO_BSDCOMPAT
[  316.641517] b44 ssb1:0: eth0: powering down PHY
[  318.223207] wlan0: deauthenticating from 00:17:9a:63:43:5f by local choice (reason=3)
[  318.223672] cfg80211: All devices are disconnected, going to restore regulatory settings
[  318.223677] cfg80211: Restoring regulatory settings
[  318.223681] cfg80211: Calling CRDA to update world regulatory domain
[  329.932478] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[  329.932484] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  329.932488] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[  329.932491] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  329.932494] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[  329.932498] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  329.932501] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[  329.932504] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  329.932507] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[  329.932511] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  329.932514] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[  329.932517] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  329.932520] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[  329.932524] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  329.932527] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[  329.932530] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  329.932533] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[  329.932536] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  329.932539] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[  329.932543] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  329.932546] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[  329.932549] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[  329.932552] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[  329.932556] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[  329.932559] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[  329.932562] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[  329.932565] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[  329.932569] cfg80211: 2474000 KHz - 2494000 KHz @  KHz), (300 mBi, 2000 mBm)
[  329.932573] cfg80211: World regulatory domain updated:
[  329.932575] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  329.932578] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  329.932582] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  329.932585] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  329.932589] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  329.932592] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  350.055076] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[  370.942583] PM: Marking nosave pages: 000000000009f000 - 0000000000100000
[  370.942589] PM: Basic memory bitmaps created
[  370.942591] PM: Syncing filesystems ... done.
[  372.467220] Freezing user space processes ... (elapsed 0.33 seconds) done.
[  372.800129] Freezing remaining freezable tasks ... (elapsed 0.01 seconds) done.
[  372.816125] PM: Preallocating image memory... done (allocated 78448 pages)
[  382.177402] PM: Allocated 313792 kbytes in 9.36 seconds (33.52 MB/s)
[  382.177406] Suspending console(s) (use no_console_suspend to debug)
[  382.179557] ACPI handle has no context!
[  382.179568] sdhci-pci 0000:06:04.4: PCI INT B disabled
[  382.179575] ACPI handle has no context!
[  382.179673] ACPI handle has no context!
[  382.179678] sdhci-pci 0000:06:04.2: PCI INT B disabled
[  382.179685] ACPI handle has no context!
[  382.179799] b44 0000:06:01.0: PCI INT A disabled
[  382.179915] b43-pci-bridge 0000:05:00.0: PCI INT A disabled
[  382.380020] sd 0:0:0:0: [sda] Synchronizing SCSI cache
[  382.380158] PM: freeze of drv:sd dev:0:0:0:0 complete after 200.937 msecs
[  382.380168] PM: freeze of drv:scsi dev:target0:0:0 complete after 200.921 msecs
[  382.380176] PM: freeze of drv:scsi dev:host0 complete after 200.725 msecs
[  382.380287] ata_piix 0000:00:1f.2: PCI INT B disabled
[  382.380292] PM: freeze of drv:ata_piix dev:0000:00:1f.2 complete after 200.333 msecs
[  382.388094] HDA Intel 0000:00:1b.0: PCI INT A disabled
[  382.404020] PM: freeze of drv:HDA Intel dev:0000:00:1b.0 complete after 223.892 msecs
[  382.404032] PM: freeze of drv: dev:pci0000:00 complete after 223.230 msecs
[  382.404039] PM: freeze of devices complete after 226.320 msecs
[  382.405207] PM: late freeze of devices complete after 1.164 msecs
[  382.405365] ACPI: Preparing to enter system sleep state S4
[  382.407749] PM: Saving platform NVS memory
[  382.409010] Disabling non-boot CPUs ...
[  382.409158] PM: Creating hibernation image:
[  382.412018] PM: Need to copy 48832 pages
[  382.412018] PM: Normal pages needed: 48832 + 1024, available pages: 79683
[  382.412018] PM: Hibernation image created (48832 pages copied)
[  382.412018] ACPI: Waking up from system sleep state S4
[  382.412018] PM: early thaw of devices complete after 1.012 msecs
[  382.416615] pci 0000:00:1e.0: setting latency timer to 64
[  382.416661] ata_piix 0000:00:1f.2: restoring config space at offset 0x1 (was 0x2b80001, writing 0x2b80005)
[  382.416682] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[  382.416688] ata_piix 0000:00:1f.2: setting latency timer to 64
[  382.429434] sd 0:0:0:0: [sda] Starting disk
[  382.432044] HDA Intel 0000:00:1b.0: BAR 0: set to [mem 0xd0340000-0xd0343fff 64bit] (PCI address [0xd0340000-0xd0343fff])
[  382.432067] HDA Intel 0000:00:1b.0: restoring config space at offset 0xf (was 0x100, writing 0x10a)
[  382.432089] HDA Intel 0000:00:1b.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[  382.432097] HDA Intel 0000:00:1b.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100102)
[  382.432122] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[  382.432130] HDA Intel 0000:00:1b.0: setting latency timer to 64
[  382.432183] HDA Intel 0000:00:1b.0: irq 44 for MSI/MSI-X
[  382.432235] b43-pci-bridge 0000:05:00.0: BAR 0: set to [mem 0xd0000000-0xd0003fff] (PCI address [0xd0000000-0xd0003fff])
[  382.432247] b43-pci-bridge 0000:05:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[  382.432304] b43-pci-bridge 0000:05:00.0: restoring config space at offset 0x1 (was 0x100103, writing 0x100107)
[  382.432347] b44 0000:06:01.0: BAR 0: set to [mem 0xd0100000-0xd0101fff] (PCI address [0xd0100000-0xd0101fff])
[  382.432355] b44 0000:06:01.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[  382.432386] b44 0000:06:01.0: restoring config space at offset 0x1 (was 0x100002, writing 0x100006)
[  382.432414] sdhci-pci 0000:06:04.2: BAR 0: set to [mem 0xd0103400-0xd01034ff] (PCI address [0xd0103400-0xd01034ff])
[  382.432466] sdhci-pci 0000:06:04.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[  382.432494] sdhci-pci 0000:06:04.4: BAR 0: set to [mem 0xd0103100-0xd01031ff] (PCI address [0xd0103100-0xd01031ff])
[  382.432546] sdhci-pci 0000:06:04.4: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[  382.477108] sonixj: Sonix chip id: 12
[  382.580346] ata1.00: ACPI cmd ef/03:0c:00:00:00:a0 (SET FEATURES) filtered out
[  382.580350] ata1.00: ACPI cmd ef/03:45:00:00:00:a0 (SET FEATURES) filtered out
[  382.596566] ata2.00: ACPI cmd ef/03:0c:00:00:00:a0 (SET FEATURES) filtered out
[  382.596570] ata2.00: ACPI cmd ef/03:42:00:00:00:a0 (SET FEATURES) filtered out
[  382.596878] ata1.00: configured for UDMA/100
[  382.617914] PM: thaw of drv:sd dev:0:0:0:0 complete after 188.480 msecs
[  382.617925] PM: thaw of drv:scsi_device dev:0:0:0:0 complete after 188.447 msecs
[  382.628290] ata2.00: configured for UDMA/33
[  383.152118] PM: thaw of drv:battery dev:PNP0C0A:00 complete after 733.715 msecs
[  383.360052] PM: thaw of drv:pcmcia_socket dev:pcmcia_socket0 complete after 139.909 msecs
[  383.360228] PM: thaw of devices complete after 949.438 msecs
[  383.360401] PM: writing image.
[  383.360415] PM: Free swap pages: 20446
[  383.360417] PM: Not enough free swap
[  383.376029] Restarting tasks ... done.
[  383.380902] PM: Basic memory bitmaps freed
[  383.380920] video LNXVIDEO:01: Restoring backlight state
[  398.431732] [drm:drm_mode_getfb] *ERROR* invalid framebuffer id
[  401.915145] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  402.076050] b43-phy0: Loading firmware version 351.126 (2006-07-29 05:54:02)
[  402.076055] b43-phy0 warning: You are using an old firmware image. Support for old firmware will be removed soon (official deadline was July 2008).
[  402.076059] b43-phy0 warning: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[  402.168652] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  422.100194] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[  433.345199] wlan0: authenticate with 00:17:9a:63:43:5f (try 1)
[  433.346606] wlan0: authenticated
[  433.347108] wlan0: associate with 00:17:9a:63:43:5f (try 1)
[  433.349002] wlan0: RX AssocResp from 00:17:9a:63:43:5f (capab=0x431 status=0 aid=1)
[  433.349007] wlan0: associated
[  433.349742] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  444.280031] wlan0: no IPv6 routers present
[  982.800996] cfg80211: Found new beacon on frequency: 2472 MHz (Ch 13) on phy0
[ 1986.016069] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[ 1986.016078] sr 1:0:0:0: CDB: Test Unit Ready: 00 00 00 00 00 00
[ 1986.016091] ata2.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
[ 1986.016093]          res 40/00:02:00:08:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
[ 1986.016096] ata2.00: status: { DRDY }
[ 1991.056036] ata2: link is slow to respond, please be patient (ready=0)
[ 1996.040034] ata2: device not ready (errno=-16), forcing hardreset
[ 1996.040047] ata2: soft resetting link
[ 1996.252333] ata2.00: configured for UDMA/33
[ 1996.260453] ata2: EH complete
[ 3092.064075] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[ 3092.064084] sr 1:0:0:0: CDB: Get event status notification: 4a 01 00 00 10 00 00 00 08 00
[ 3092.064100] ata2.00: cmd a0/00:00:00:08:00/00:00:00:00:00/a0 tag 0 pio 16392 in
[ 3092.064102]          res 40/00:03:00:00:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
[ 3092.064106] ata2.00: status: { DRDY }
[ 3097.104048] ata2: link is slow to respond, please be patient (ready=0)
[ 3102.088046] ata2: device not ready (errno=-16), forcing hardreset
[ 3102.088059] ata2: soft resetting link
[ 3102.300388] ata2.00: configured for UDMA/33
[ 3102.308806] ata2: EH complete
[ 3308.064306] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[ 3308.064315] sr 1:0:0:0: CDB: Get event status notification: 4a 01 00 00 10 00 00 00 08 00
[ 3308.064331] ata2.00: cmd a0/00:00:00:08:00/00:00:00:00:00/a0 tag 0 pio 16392 in
[ 3308.064333]          res 40/00:03:00:00:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
[ 3308.064337] ata2.00: status: { DRDY }
[ 3313.104044] ata2: link is slow to respond, please be patient (ready=0)
[ 3318.088045] ata2: device not ready (errno=-16), forcing hardreset
[ 3318.088059] ata2: soft resetting link
[ 3318.300303] ata2.00: configured for UDMA/33
[ 3318.308460] ata2: EH complete
[ 4012.079002] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=600
[ 4042.568283] usb 5-1: USB disconnect, address 2
[ 4054.665041] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[ 4436.064067] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[ 4436.064075] sr 1:0:0:0: CDB: Test Unit Ready: 00 00 00 00 00 00
[ 4436.064088] ata2.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
[ 4436.064090]          res 40/00:02:00:08:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
[ 4436.064093] ata2.00: status: { DRDY }
[ 4441.104064] ata2: link is slow to respond, please be patient (ready=0)
[ 4446.088582] ata2: device not ready (errno=-16), forcing hardreset
[ 4446.088595] ata2: soft resetting link
[ 4446.308299] ata2.00: configured for UDMA/33
[ 4446.308830] ata2: EH complete
[ 6754.016077] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[ 6754.016085] sr 1:0:0:0: CDB: Test Unit Ready: 00 00 00 00 00 00
[ 6754.016099] ata2.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
[ 6754.016100]          res 40/00:02:00:08:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
[ 6754.016104] ata2.00: status: { DRDY }
[ 6759.056027] ata2: link is slow to respond, please be patient (ready=0)
[ 6764.040043] ata2: device not ready (errno=-16), forcing hardreset
[ 6764.040056] ata2: soft resetting link
[ 6764.260307] ata2.00: configured for UDMA/33
[ 6764.268424] ata2: EH complete
[ 9385.021266] gspca: ISOC data error: [15] len=0, status=-84
[ 9385.021272] gspca: ISOC data error: [16] len=0, status=-84
[ 9385.021274] gspca: ISOC data error: [17] len=0, status=-84
[ 9385.021277] gspca: ISOC data error: [18] len=0, status=-84
[ 9385.021279] gspca: ISOC data error: [19] len=0, status=-84
[ 9385.021282] gspca: ISOC data error: [20] len=0, status=-84
[ 9385.021284] gspca: ISOC data error: [21] len=0, status=-84
[ 9385.021287] gspca: ISOC data error: [22] len=0, status=-84
[ 9385.021289] gspca: ISOC data error: [23] len=0, status=-84
[ 9385.045272] gspca: ISOC data error: [0] len=0, status=-84
[ 9385.045276] gspca: ISOC data error: [1] len=0, status=-84
[ 9385.045278] gspca: ISOC data error: [2] len=0, status=-84
[ 9385.045281] gspca: ISOC data error: [3] len=0, status=-84
[ 9385.045283] gspca: ISOC data error: [4] len=0, status=-84
[ 9385.045285] gspca: ISOC data error: [5] len=0, status=-84
[ 9385.045288] gspca: ISOC data error: [6] len=0, status=-84
[ 9385.045290] gspca: ISOC data error: [7] len=0, status=-84
[ 9385.045293] gspca: ISOC data error: [8] len=0, status=-84
[ 9385.045295] gspca: ISOC data error: [9] len=0, status=-84
[ 9385.045297] gspca: ISOC data error: [10] len=0, status=-84
[ 9385.045300] gspca: ISOC data error: [11] len=0, status=-84
[ 9385.045302] gspca: ISOC data error: [12] len=0, status=-84
[ 9385.045305] gspca: ISOC data error: [13] len=0, status=-84
[ 9385.045307] gspca: ISOC data error: [14] len=0, status=-84
[ 9385.045310] gspca: ISOC data error: [15] len=0, status=-84
[ 9385.045312] gspca: ISOC data error: [16] len=0, status=-84
[ 9385.045314] gspca: ISOC data error: [17] len=0, status=-84
[ 9385.045317] gspca: ISOC data error: [18] len=0, status=-84
[ 9385.045319] gspca: ISOC data error: [19] len=0, status=-84
[ 9385.045322] gspca: ISOC data error: [20] len=0, status=-84
[ 9385.045324] gspca: ISOC data error: [21] len=0, status=-84
[ 9385.045327] gspca: ISOC data error: [22] len=0, status=-84
[ 9385.045329] gspca: ISOC data error: [23] len=0, status=-84
[ 9385.069274] gspca: ISOC data error: [0] len=0, status=-84
[ 9385.069278] gspca: ISOC data error: [1] len=0, status=-84
[ 9385.069281] gspca: ISOC data error: [2] len=0, status=-84
[ 9385.069283] gspca: ISOC data error: [3] len=0, status=-84
[ 9385.069286] gspca: ISOC data error: [4] len=0, status=-84
[ 9385.069288] gspca: ISOC data error: [5] len=0, status=-84
[ 9385.069290] gspca: ISOC data error: [6] len=0, status=-84
[ 9385.069293] gspca: ISOC data error: [7] len=0, status=-84
[ 9385.069295] gspca: ISOC data error: [8] len=0, status=-84
[ 9385.069298] gspca: ISOC data error: [9] len=0, status=-84
[ 9385.069300] gspca: ISOC data error: [10] len=0, status=-84
[ 9385.069303] gspca: ISOC data error: [11] len=0, status=-84
[ 9385.069305] gspca: ISOC data error: [12] len=0, status=-84
[ 9385.069307] gspca: ISOC data error: [13] len=0, status=-84
[ 9385.069310] gspca: ISOC data error: [14] len=0, status=-84
[ 9385.069312] gspca: ISOC data error: [15] len=0, status=-84
[ 9385.069315] gspca: ISOC data error: [16] len=0, status=-84
[ 9385.069317] gspca: ISOC data error: [17] len=0, status=-84
[ 9385.069320] gspca: ISOC data error: [18] len=0, status=-84
[ 9385.069322] gspca: ISOC data error: [19] len=0, status=-84
[ 9385.069324] gspca: ISOC data error: [20] len=0, status=-84
[ 9385.069327] gspca: ISOC data error: [21] len=0, status=-84
[ 9385.069329] gspca: ISOC data error: [22] len=0, status=-84
[ 9385.069332] gspca: ISOC data error: [23] len=0, status=-84
[ 9385.093273] gspca: ISOC data error: [0] len=0, status=-84
[ 9385.093277] gspca: ISOC data error: [1] len=0, status=-84
[ 9385.093280] gspca: ISOC data error: [2] len=0, status=-84
[ 9385.093282] gspca: ISOC data error: [3] len=0, status=-84
[ 9385.093285] gspca: ISOC data error: [4] len=0, status=-84
[ 9385.093287] gspca: ISOC data error: [5] len=0, status=-84
[ 9385.093290] gspca: ISOC data error: [6] len=0, status=-84
[ 9385.093292] gspca: ISOC data error: [7] len=0, status=-84
[ 9385.093295] gspca: ISOC data error: [8] len=0, status=-84
[ 9385.093297] gspca: ISOC data error: [9] len=0, status=-84
[ 9385.093300] gspca: ISOC data error: [10] len=0, status=-84
[ 9385.093302] gspca: ISOC data error: [11] len=0, status=-84
[ 9385.093305] gspca: ISOC data error: [12] len=0, status=-84
[ 9385.093307] gspca: ISOC data error: [13] len=0, status=-84
[ 9385.093310] gspca: ISOC data error: [14] len=0, status=-84
[ 9385.093312] gspca: ISOC data error: [15] len=0, status=-84
[ 9385.093314] gspca: ISOC data error: [16] len=0, status=-84
[ 9385.093317] gspca: ISOC data error: [17] len=0, status=-84
[ 9385.093319] gspca: ISOC data error: [18] len=0, status=-84
[ 9385.093322] gspca: ISOC data error: [19] len=0, status=-84
[ 9385.093324] gspca: ISOC data error: [20] len=0, status=-84
[ 9385.093327] gspca: ISOC data error: [21] len=0, status=-84
[ 9385.093329] gspca: ISOC data error: [22] len=0, status=-84
[ 9385.093332] gspca: ISOC data error: [23] len=0, status=-84
[ 9385.117279] gspca: ISOC data error: [0] len=0, status=-84
[ 9385.117285] gspca: ISOC data error: [1] len=0, status=-84
[ 9385.117288] gspca: ISOC data error: [2] len=0, status=-84
[ 9385.117290] gspca: ISOC data error: [3] len=0, status=-84
[ 9385.117293] gspca: ISOC data error: [4] len=0, status=-84
[ 9385.117295] gspca: ISOC data error: [5] len=0, status=-84
[ 9385.117298] gspca: ISOC data error: [6] len=0, status=-84
[ 9385.117300] gspca: ISOC data error: [7] len=0, status=-84
[ 9385.117303] gspca: ISOC data error: [8] len=0, status=-84
[ 9385.117305] gspca: ISOC data error: [9] len=0, status=-84
[ 9385.117307] gspca: ISOC data error: [10] len=0, status=-84
[ 9385.117310] gspca: ISOC data error: [11] len=0, status=-84
[ 9385.117312] gspca: ISOC data error: [12] len=0, status=-84
[ 9385.117315] gspca: ISOC data error: [13] len=0, status=-84
[ 9385.117317] gspca: ISOC data error: [14] len=0, status=-84
[ 9385.117320] gspca: ISOC data error: [15] len=0, status=-84
[ 9385.117322] gspca: ISOC data error: [16] len=0, status=-84
[ 9385.117325] gspca: ISOC data error: [17] len=0, status=-84
[ 9385.117327] gspca: ISOC data error: [18] len=0, status=-84
[ 9385.117329] gspca: ISOC data error: [19] len=0, status=-84
[ 9385.117332] gspca: ISOC data error: [20] len=0, status=-84
[ 9385.117334] gspca: ISOC data error: [21] len=0, status=-84
[ 9385.117337] gspca: ISOC data error: [22] len=0, status=-84
[ 9385.117339] gspca: ISOC data error: [23] len=0, status=-84
[ 9385.141270] gspca: ISOC data error: [0] len=0, status=-84
[ 9385.141274] gspca: ISOC data error: [1] len=0, status=-84
[ 9385.141277] gspca: ISOC data error: [2] len=0, status=-84
[ 9385.141279] gspca: ISOC data error: [3] len=0, status=-84
[ 9385.141281] gspca: ISOC data error: [4] len=0, status=-84
[ 9385.141284] gspca: ISOC data error: [5] len=0, status=-84
[ 9385.141286] gspca: ISOC data error: [6] len=0, status=-84
[ 9385.141289] gspca: ISOC data error: [7] len=0, status=-84
[ 9385.141291] gspca: ISOC data error: [8] len=0, status=-84
[ 9385.141293] gspca: ISOC data error: [9] len=0, status=-84
[ 9385.141296] gspca: ISOC data error: [10] len=0, status=-84
[ 9385.141298] gspca: ISOC data error: [11] len=0, status=-84
[ 9385.141301] gspca: ISOC data error: [12] len=0, status=-84
[ 9385.141303] gspca: ISOC data error: [13] len=0, status=-84
[ 9385.141306] gspca: ISOC data error: [14] len=0, status=-84
[ 9385.141308] gspca: ISOC data error: [15] len=0, status=-84
[ 9385.141311] gspca: ISOC data error: [16] len=0, status=-84
[ 9385.141313] gspca: ISOC data error: [17] len=0, status=-84
[ 9385.141315] gspca: ISOC data error: [18] len=0, status=-84
[ 9385.141318] gspca: ISOC data error: [19] len=0, status=-84
[ 9385.141320] gspca: ISOC data error: [20] len=0, status=-84
[ 9385.141323] gspca: ISOC data error: [21] len=0, status=-84
[ 9385.141325] gspca: ISOC data error: [22] len=0, status=-84
[ 9385.141328] gspca: ISOC data error: [23] len=0, status=-84
[ 9385.165262] gspca: ISOC data error: [0] len=0, status=-84
[ 9385.165266] gspca: ISOC data error: [1] len=0, status=-84
[ 9385.165269] gspca: ISOC data error: [2] len=0, status=-84
[ 9385.165271] gspca: ISOC data error: [3] len=0, status=-84
[ 9385.165274] gspca: ISOC data error: [4] len=0, status=-84
[ 9385.165276] gspca: ISOC data error: [5] len=0, status=-84
[ 9385.165279] gspca: ISOC data error: [6] len=0, status=-84
[ 9385.165281] gspca: ISOC data error: [7] len=0, status=-84
[ 9385.165283] gspca: ISOC data error: [8] len=0, status=-84
[ 9385.165286] gspca: ISOC data error: [9] len=0, status=-84
[ 9385.165288] gspca: ISOC data error: [10] len=0, status=-84
[ 9385.165291] gspca: ISOC data error: [11] len=0, status=-84
[ 9385.165293] gspca: ISOC data error: [12] len=0, status=-84
[ 9385.165296] gspca: ISOC data error: [13] len=0, status=-84
[ 9385.165298] gspca: ISOC data error: [14] len=0, status=-84
[ 9385.165301] gspca: ISOC data error: [15] len=0, status=-84
[ 9385.165303] gspca: ISOC data error: [16] len=0, status=-84
[ 9385.165306] gspca: ISOC data error: [17] len=0, status=-84
[ 9385.165308] gspca: ISOC data error: [18] len=0, status=-84
[ 9385.165310] gspca: ISOC data error: [19] len=0, status=-84
[ 9385.165313] gspca: ISOC data error: [20] len=0, status=-84
[ 9385.165315] gspca: ISOC data error: [21] len=0, status=-84
[ 9385.165318] gspca: ISOC data error: [22] len=0, status=-84
[ 9385.165320] gspca: ISOC data error: [23] len=0, status=-84
[ 9385.165330] gspca: URB error -84, resubmitting
[ 9385.189269] gspca: ISOC data error: [0] len=0, status=-84
[ 9385.189273] gspca: ISOC data error: [1] len=0, status=-84
[ 9385.189276] gspca: ISOC data error: [2] len=0, status=-84
[ 9385.189278] gspca: ISOC data error: [3] len=0, status=-84
[ 9385.189281] gspca: ISOC data error: [4] len=0, status=-84
[ 9385.189283] gspca: ISOC data error: [5] len=0, status=-84
[ 9385.189286] gspca: ISOC data error: [6] len=0, status=-84
[ 9385.189288] gspca: ISOC data error: [7] len=0, status=-84
[ 9385.189290] gspca: ISOC data error: [8] len=0, status=-84
[ 9385.189293] gspca: ISOC data error: [9] len=0, status=-84
[ 9385.189295] gspca: ISOC data error: [10] len=0, status=-84
[ 9385.189298] gspca: ISOC data error: [11] len=0, status=-84
[ 9385.189300] gspca: ISOC data error: [12] len=0, status=-84
[ 9385.189303] gspca: ISOC data error: [13] len=0, status=-84
[ 9385.189305] gspca: ISOC data error: [14] len=0, status=-84
[ 9385.189308] gspca: ISOC data error: [15] len=0, status=-84
[ 9385.189310] gspca: ISOC data error: [16] len=0, status=-84
[ 9385.189313] gspca: ISOC data error: [17] len=0, status=-84
[ 9385.189315] gspca: ISOC data error: [18] len=0, status=-84
[ 9385.189317] gspca: ISOC data error: [19] len=0, status=-84
[ 9385.189320] gspca: ISOC data error: [20] len=0, status=-84
[ 9385.189322] gspca: ISOC data error: [21] len=0, status=-84
[ 9385.189325] gspca: ISOC data error: [22] len=0, status=-84
[ 9385.189327] gspca: ISOC data error: [23] len=0, status=-84
[ 9385.213266] gspca: ISOC data error: [0] len=0, status=-84
[ 9385.213270] gspca: ISOC data error: [1] len=0, status=-84
[ 9385.213272] gspca: ISOC data error: [2] len=0, status=-84
[ 9385.213275] gspca: ISOC data error: [3] len=0, status=-84
[ 9385.213277] gspca: ISOC data error: [4] len=0, status=-84
[ 9385.213280] gspca: ISOC data error: [5] len=0, status=-84
[ 9385.213282] gspca: ISOC data error: [6] len=0, status=-84
[ 9385.213285] gspca: ISOC data error: [7] len=0, status=-84
[ 9385.213287] gspca: ISOC data error: [8] len=0, status=-84
[ 9385.213289] gspca: ISOC data error: [9] len=0, status=-84
[ 9385.213292] gspca: ISOC data error: [10] len=0, status=-84
[ 9385.213294] gspca: ISOC data error: [11] len=0, status=-84
[ 9385.213297] gspca: ISOC data error: [12] len=0, status=-84
[ 9385.213299] gspca: ISOC data error: [13] len=0, status=-84
[ 9385.213302] gspca: ISOC data error: [14] len=0, status=-84
[ 9385.213304] gspca: ISOC data error: [15] len=0, status=-84
[ 9385.213307] gspca: ISOC data error: [16] len=0, status=-84
[ 9385.213309] gspca: ISOC data error: [17] len=0, status=-84
[ 9385.213312] gspca: ISOC data error: [18] len=0, status=-84
[ 9385.213314] gspca: ISOC data error: [19] len=0, status=-84
[ 9385.213316] gspca: ISOC data error: [20] len=0, status=-84
[ 9385.213319] gspca: ISOC data error: [21] len=0, status=-84
[ 9385.213321] gspca: ISOC data error: [22] len=0, status=-84
[ 9385.213324] gspca: ISOC data error: [23] len=0, status=-84
[ 9385.232084] usb 2-1: USB disconnect, address 2
[ 9385.234264] gspca: video0 disconnect
[ 9387.732039] usb 2-1: new full speed USB device using uhci_hcd and address 3
[ 9387.892534] gspca: probing 0c45:612c
[ 9387.897483] sonixj: Sonix chip id: 12
[ 9387.899582] input: sonixj as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/input/input9
[ 9387.899729] gspca: video1 created
[ 9401.110440] gspca: video0 released
[10184.008086] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[10184.008095] sr 1:0:0:0: CDB: Prevent/Allow Medium Removal: 1e 00 00 00 00 00
[10184.008108] ata2.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
[10184.008110]          res 40/00:03:00:00:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
[10184.008113] ata2.00: status: { DRDY }
[10189.048063] ata2: link is slow to respond, please be patient (ready=0)
[10194.032096] ata2: device not ready (errno=-16), forcing hardreset
[10194.032109] ata2: soft resetting link
[10194.244296] ata2.00: configured for UDMA/33
[10194.244865] ata2: EH complete
[10194.244937] sr 1:0:0:0: ioctl_internal_command return code = 8000002
[10194.244940]    : Sense Key : Aborted Command [current] [descriptor]
[10194.244945]    : Add. Sense: No additional sense information
[10547.040066] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[10547.040074] sr 1:0:0:0: CDB: Test Unit Ready: 00 00 00 00 00 00
[10547.040088] ata2.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
[10547.040089]          res 40/00:02:00:08:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
[10547.040093] ata2.00: status: { DRDY }
[10552.080032] ata2: link is slow to respond, please be patient (ready=0)
[10557.064060] ata2: device not ready (errno=-16), forcing hardreset
[10557.064072] ata2: soft resetting link
[10557.292310] ata2.00: configured for UDMA/33
[10557.300482] ata2: EH complete
[10756.009150] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[10756.009156] ata2.00: ST_FIRST: !(DRQ|ERR|DF)
[10756.009160] sr 1:0:0:0: CDB: Test Unit Ready: 00 00 00 00 00 00
[10756.009174] ata2.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
[10756.009175]          res 50/00:00:00:00:00/00:00:00:00:00/a0 Emask 0x2 (HSM violation)
[10756.009179] ata2.00: status: { DRDY }
[10756.009214] ata2: soft resetting link
[10756.228293] ata2.00: configured for UDMA/33
[10756.236440] ata2: EH complete

---

### Post by androssofer on 2011-07-01
nvr used quvcview, i would uninstall it, then re-install it. see if that helps any...

appart from that i dont know.. sorry

---

### Post by helphelp on 2011-07-01
Seems to have done the trick
many thanks

---

