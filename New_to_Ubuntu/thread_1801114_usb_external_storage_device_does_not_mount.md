---
title: "usb external storage device does not mount"
date: 2011-07-09
forum: New to Ubuntu
---

### Post by Ymurti on 2011-07-09
Help! I have an external storage device that I can mount it in Windows but it is not appearing in Ubuntu. 

From another post I got this command dmesg  I tiped it in a terminal and got it:

[   24.705430] [drm] RAM width 64bits DDR
[   24.705581] [TTM] Zone  kernel: Available graphics memory: 430000 kiB.
[   24.705583] [TTM] Zone highmem: Available graphics memory: 1506476 kiB.
[   24.705586] [TTM] Initializing pool allocator.
[   24.705607] [drm] radeon: 512M of VRAM memory ready
[   24.705610] [drm] radeon: 512M of GTT memory ready.
[   24.705633] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   24.705635] [drm] Driver supports precise vblank timestamp query.
[   24.705749] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro
[   24.705844] radeon 0000:01:00.0: irq 43 for MSI/MSI-X
[   24.705870] radeon 0000:01:00.0: radeon: using MSI.
[   24.706010] [drm] radeon: irq initialized.
[   24.706013] [drm] GART: num cpu pages 131072, num gpu pages 131072
[   24.706576] ath: EEPROM regdomain: 0x65
[   24.706578] ath: EEPROM indicates we should expect a direct regpair map
[   24.706581] ath: Country alpha2 being used: 00
[   24.706582] ath: Regpair used: 0x65
[   24.706586] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   24.706588] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   24.706590] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   24.706592] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   24.706593] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   24.706595] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   24.706597] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   24.706599] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   24.706601] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   24.706603] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   24.706604] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   24.706606] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   24.706608] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   24.706610] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   24.706612] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   24.706614] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   24.706615] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   24.706617] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   24.706619] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   24.706621] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   24.706623] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   24.706625] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   24.706626] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   24.706628] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   24.706630] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   24.706632] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   24.706634] cfg80211: Disabling freq 2484 MHz as custom regd has no rule that fits a 20 MHz wide channel
[   24.707085] [drm] Loading CEDAR Microcode
[   24.708137] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[   24.718807] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
[   24.719613] Registered led device: ath9k-phy0::radio
[   24.719642] Registered led device: ath9k-phy0::assoc
[   24.719667] Registered led device: ath9k-phy0::tx
[   24.719695] Registered led device: ath9k-phy0::rx
[   24.719703] ieee80211 phy0: Atheros AR9285 Rev:2 mem=0xf8360000, irq=16
[   24.723289] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   24.723360] HDA Intel 0000:00:1b.0: irq 44 for MSI/MSI-X
[   24.723395] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   24.728685] input: PS/2 Mouse as /devices/platform/i8042/serio1/input/input9
[   24.746665] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input10
[   24.758110] radeon 0000:01:00.0: WB enabled
[   24.774704] [drm] ring test succeeded in 1 usecs
[   24.774909] [drm] radeon: ib pool ready.
[   24.775045] [drm] ib test succeeded in 0 usecs
[   24.776774] [drm] Radeon Display Connectors
[   24.776777] [drm] Connector 0:
[   24.776779] [drm]   LVDS
[   24.776780] [drm]   Encoders:
[   24.776782] [drm]     LCD1: INTERNAL_UNIPHY
[   24.776783] [drm] Connector 1:
[   24.776785] [drm]   HDMI-A
[   24.776786] [drm]   HPD1
[   24.776789] [drm]   DDC: 0x6460 0x6460 0x6464 0x6464 0x6468 0x6468 0x646c 0x646c
[   24.776791] [drm]   Encoders:
[   24.776793] [drm]     DFP1: INTERNAL_UNIPHY1
[   24.776794] [drm] Connector 2:
[   24.776796] [drm]   VGA
[   24.776798] [drm]   DDC: 0x6430 0x6430 0x6434 0x6434 0x6438 0x6438 0x643c 0x643c
[   24.776800] [drm]   Encoders:
[   24.776801] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
[   24.780401] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   24.780548] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[   24.780794] [drm] Internal thermal controller with fan control
[   24.780875] [drm] radeon: power management initialized
[   25.057558] type=1400 audit(1310256686.457:5): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=831 comm="apparmor_parser"
[   25.057921] type=1400 audit(1310256686.457:6): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=832 comm="apparmor_parser"
[   25.058985] type=1400 audit(1310256686.461:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=832 comm="apparmor_parser"
[   25.059446] type=1400 audit(1310256686.461:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=832 comm="apparmor_parser"
[   25.061406] type=1400 audit(1310256686.461:9): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=838 comm="apparmor_parser"
[   25.061573] type=1400 audit(1310256686.461:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=836 comm="apparmor_parser"
[   25.062514] type=1400 audit(1310256686.465:11): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=836 comm="apparmor_parser"
[   25.168393] [drm] fb mappable at 0xE0141000
[   25.168395] [drm] vram apper at 0xE0000000
[   25.168397] [drm] size 4325376
[   25.168398] [drm] fb depth is 24
[   25.168399] [drm]    pitch is 5632
[   25.168585] Console: switching to colour frame buffer device 170x48
[   25.168621] fb0: radeondrmfb frame buffer device
[   25.168623] drm: registered panic notifier
[   25.168630] [drm] Initialized radeon 2.8.0 20080528 for 0000:01:00.0 on minor 0
[   25.168685] HDA Intel 0000:01:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   25.168735] HDA Intel 0000:01:00.1: irq 45 for MSI/MSI-X
[   25.168756] HDA Intel 0000:01:00.1: setting latency timer to 64
[   25.226075] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   25.246259] sky2 0000:04:00.0: eth0: enabling interface
[   25.246488] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   26.012007] ppdev: user-space parallel port driver
[   26.497837] Bluetooth: L2CAP ver 2.15
[   26.497841] Bluetooth: L2CAP socket layer initialized
[   26.504247] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   26.504250] Bluetooth: BNEP filters: protocol multicast
[   26.508472] Bluetooth: SCO (Voice Link) ver 0.6
[   26.508476] Bluetooth: SCO socket layer initialized
[   26.546444] Bluetooth: RFCOMM TTY layer initialized
[   26.546450] Bluetooth: RFCOMM socket layer initialized
[   26.546452] Bluetooth: RFCOMM ver 1.11
[   27.484865] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=0
[   28.056974] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
[   28.829172] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=0
[   43.644557] wlan0: authenticate with 00:1d:6a:be:98:8b (try 1)
[   43.646529] wlan0: authenticated
[   43.646552] wlan0: associate with 00:1d:6a:be:98:8b (try 1)
[   43.648794] wlan0: RX AssocResp from 00:1d:6a:be:98:8b (capab=0x421 status=0 aid=6)
[   43.648798] wlan0: associated
[   43.649064] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   43.649177] cfg80211: Calling CRDA for country: US
[   43.653111] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   43.653115] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[   43.653117] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   43.653120] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[   43.653121] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   43.653123] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[   43.653125] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   43.653127] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[   43.653129] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   43.653131] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[   43.653133] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   43.653135] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[   43.653136] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   43.653138] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[   43.653140] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   43.653142] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[   43.653144] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   43.653146] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[   43.653148] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   43.653150] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[   43.653151] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   43.653153] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[   43.653155] cfg80211: Disabling freq 2467 MHz
[   43.653156] cfg80211: Disabling freq 2472 MHz
[   43.653157] cfg80211: Disabling freq 2484 MHz
[   43.653161] cfg80211: Regulatory domain changed to country: US
[   43.653162] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   43.653164] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   43.653166] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[   43.653168] cfg80211:     (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   43.653170] cfg80211:     (5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   43.653172] cfg80211:     (5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   43.653174] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[   53.673072] wlan0: no IPv6 routers present
[ 1985.148017] wlan0: deauthenticating from 00:1d:6a:be:98:8b by local choice (reason=3)
[ 1985.194564] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 1985.194572] cfg80211: Restoring regulatory settings
[ 1985.194579] cfg80211: Calling CRDA to update world regulatory domain
[ 1985.202163] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[ 1985.202174] cfg80211: World regulatory domain updated:
[ 1985.202178] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 1985.202184] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1985.202190] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1985.202195] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1985.202200] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1985.202205] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1985.338755] sky2 0000:04:00.0: eth0: disabling interface
[ 1987.623431] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=0
[ 1989.274315] PM: Syncing filesystems ... done.
[ 1989.276426] PM: Preparing system for mem sleep
[ 1989.451980] Freezing user space processes ... (elapsed 0.01 seconds) done.
[ 1989.467607] Freezing remaining freezable tasks ... (elapsed 0.01 seconds) done.
[ 1989.483578] PM: Entering mem sleep
[ 1989.483626] Suspending console(s) (use no_console_suspend to debug)
[ 1989.495777] sd 0:0:0:0: [sda] Synchronizing SCSI cache
[ 1989.516156] sdhci-pci 0000:03:00.4: PCI INT C disabled
[ 1989.516169] sdhci-pci 0000:03:00.0: PCI INT A disabled
[ 1989.543395] ehci_hcd 0000:00:1a.0: PCI INT A disabled
[ 1989.543410] ehci_hcd 0000:00:1d.0: PCI INT A disabled
[ 1989.554247] sd 0:0:0:0: [sda] Stopping disk
[ 1989.619461] HDA Intel 0000:01:00.1: PCI INT B disabled
[ 1989.619497] ACPI handle has no context!
[ 1989.619627] HDA Intel 0000:00:1b.0: PCI INT A disabled
[ 1989.635296] PM: suspend of drv:HDA Intel dev:0000:01:00.1 complete after 119.227 msecs
[ 1989.635310] PM: suspend of drv:HDA Intel dev:0000:00:1b.0 complete after 118.742 msecs
[ 1989.942800] PM: suspend of drv:radeon dev:0000:01:00.0 complete after 427.138 msecs
[ 1989.942846] PM: suspend of drv:pcieport dev:0000:00:01.0 complete after 426.654 msecs
[ 1990.183690] PM: suspend of drv:sd dev:0:0:0:0 complete after 689.101 msecs
[ 1990.183765] PM: suspend of drv:scsi dev:target0:0:0 complete after 688.900 msecs
[ 1990.183784] PM: suspend of drv:scsi dev:host0 complete after 688.677 msecs
[ 1990.198380] PM: suspend of drv:ahci dev:0000:00:1f.2 complete after 683.078 msecs
[ 1990.198452] PM: suspend of drv: dev:pci0000:00 complete after 682.678 msecs
[ 1990.198530] PM: suspend of devices complete after 715.910 msecs
[ 1990.198534] PM: suspend devices took 0.716 seconds
[ 1990.354102] PM: late suspend of drv:sky2 dev:0000:04:00.0 complete after 155.636 msecs
[ 1990.402081] PM: late suspend of devices complete after 203.892 msecs
[ 1990.402502] ACPI: Preparing to enter system sleep state S3
[ 1990.403084] PM: Saving platform NVS memory
[ 1990.403868] Disabling non-boot CPUs ...
[ 1990.505851] CPU 1 is now offline
[ 1990.673500] CPU 2 is now offline
[ 1990.809272] CPU 3 is now offline
[ 1990.809618] Extended CMOS year: 2000
[ 1990.809908] Back to C!
[ 1990.809912] PM: Restoring platform NVS memory
[ 1990.810270] CPU0: Thermal monitoring handled by SMI
[ 1990.810328] Extended CMOS year: 2000
[ 1990.810344] Enabling non-boot CPUs ...
[ 1990.810455] Booting Node 0 Processor 1 APIC 0x4
[ 1990.820523] Initializing CPU#1
[ 1990.897774] CPU1: Thermal monitoring handled by SMI
[ 1990.918294] CPU1 is up
[ 1990.918378] Booting Node 0 Processor 2 APIC 0x1
[ 1990.921718] Switched to NOHz mode on CPU #1
[ 1990.928512] Initializing CPU#2
[ 1991.005590] CPU2: Thermal monitoring handled by SMI
[ 1991.026200] CPU2 is up
[ 1991.026288] Booting Node 0 Processor 3 APIC 0x5
[ 1991.029535] Switched to NOHz mode on CPU #2
[ 1991.036422] Initializing CPU#3
[ 1991.113402] CPU3: Thermal monitoring handled by SMI
[ 1991.137473] Switched to NOHz mode on CPU #3
[ 1991.142293] CPU3 is up
[ 1991.144177] ACPI: Waking up from system sleep state S3
[ 1991.369172] power_supply BAT0: parent PNP0C0A:00 should not be sleeping
[ 1991.561271] pcieport 0000:00:01.0: restoring config space at offset 0x1 (was 0x100007, writing 0x100407)
[ 1991.561306] pci 0000:00:16.0: restoring config space at offset 0xf (was 0x100, writing 0x10b)
[ 1991.561325] pci 0000:00:16.0: restoring config space at offset 0x4 (was 0x4, writing 0xf5e0a004)
[ 1991.561332] pci 0000:00:16.0: restoring config space at offset 0x1 (was 0x180000, writing 0x100006)
[ 1991.561361] ehci_hcd 0000:00:1a.0: restoring config space at offset 0xf (was 0x100, writing 0x10b)
[ 1991.561380] ehci_hcd 0000:00:1a.0: restoring config space at offset 0x4 (was 0x0, writing 0xf5e08000)
[ 1991.561388] ehci_hcd 0000:00:1a.0: restoring config space at offset 0x1 (was 0x2900000, writing 0x2900002)
[ 1991.561422] HDA Intel 0000:00:1b.0: restoring config space at offset 0xf (was 0x100, writing 0x103)
[ 1991.561440] HDA Intel 0000:00:1b.0: restoring config space at offset 0x4 (was 0xbc000004, writing 0xf5e00004)
[ 1991.561445] HDA Intel 0000:00:1b.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[ 1991.561451] HDA Intel 0000:00:1b.0: restoring config space at offset 0x1 (was 0x100006, writing 0x100002)
[ 1991.561486] pcieport 0000:00:1c.0: restoring config space at offset 0xf (was 0x100, writing 0x10010b)
[ 1991.561497] pcieport 0000:00:1c.0: restoring config space at offset 0x9 (was 0x1fff1, writing 0xbc21bc11)
[ 1991.561509] pcieport 0000:00:1c.0: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
[ 1991.561515] pcieport 0000:00:1c.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100007)
[ 1991.561555] pcieport 0000:00:1c.1: restoring config space at offset 0xf (was 0x200, writing 0x10020a)
[ 1991.561567] pcieport 0000:00:1c.1: restoring config space at offset 0x9 (was 0x1fff1, writing 0xbc41bc31)
[ 1991.561578] pcieport 0000:00:1c.1: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
[ 1991.561585] pcieport 0000:00:1c.1: restoring config space at offset 0x1 (was 0x100000, writing 0x100007)
[ 1991.561624] pcieport 0000:00:1c.2: restoring config space at offset 0xf (was 0x300, writing 0x100304)
[ 1991.561636] pcieport 0000:00:1c.2: restoring config space at offset 0x9 (was 0x1fff1, writing 0xbc61bc51)
[ 1991.561647] pcieport 0000:00:1c.2: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
[ 1991.561654] pcieport 0000:00:1c.2: restoring config space at offset 0x1 (was 0x100000, writing 0x100007)
[ 1991.561693] pcieport 0000:00:1c.5: restoring config space at offset 0xf (was 0x200, writing 0x10020a)
[ 1991.561704] pcieport 0000:00:1c.5: restoring config space at offset 0x9 (was 0x1fff1, writing 0xbc81bc71)
[ 1991.561716] pcieport 0000:00:1c.5: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
[ 1991.561722] pcieport 0000:00:1c.5: restoring config space at offset 0x1 (was 0x100000, writing 0x100007)
[ 1991.561758] ehci_hcd 0000:00:1d.0: restoring config space at offset 0xf (was 0x100, writing 0x10b)
[ 1991.561776] ehci_hcd 0000:00:1d.0: restoring config space at offset 0x4 (was 0x0, writing 0xf5e07000)
[ 1991.561784] ehci_hcd 0000:00:1d.0: restoring config space at offset 0x1 (was 0x2900000, writing 0x2900002)
[ 1991.561809] pci 0000:00:1e.0: restoring config space at offset 0xf (was 0x0, writing 0x100000)
[ 1991.561907] ahci 0000:00:1f.2: restoring config space at offset 0x1 (was 0x2b00007, writing 0x2b00407)
[ 1991.561961] pci 0000:00:1f.3: restoring config space at offset 0x1 (was 0x2800001, writing 0x2800003)
[ 1991.561994] radeon 0000:01:00.0: restoring config space at offset 0x1 (was 0x100007, writing 0x100407)
[ 1991.562037] HDA Intel 0000:01:00.1: restoring config space at offset 0x4 (was 0x4, writing 0xf0040004)
[ 1991.562043] HDA Intel 0000:01:00.1: restoring config space at offset 0x1 (was 0x100007, writing 0x100003)
[ 1991.562082] ath9k 0000:02:00.0: restoring config space at offset 0xf (was 0x1ff, writing 0x10b)
[ 1991.562104] ath9k 0000:02:00.0: restoring config space at offset 0x4 (was 0x4, writing 0xf4a00004)
[ 1991.562110] ath9k 0000:02:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[ 1991.562116] ath9k 0000:02:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100007)
[ 1991.562193] sdhci-pci 0000:03:00.0: restoring config space at offset 0xf (was 0x100, writing 0x10a)
[ 1991.562221] sdhci-pci 0000:03:00.0: restoring config space at offset 0x4 (was 0x0, writing 0xf3602000)
[ 1991.562227] sdhci-pci 0000:03:00.0: restoring config space at offset 0x3 (was 0x800000, writing 0x800010)
[ 1991.562237] sdhci-pci 0000:03:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100006)
[ 1991.562286] pci 0000:03:00.1: restoring config space at offset 0xf (was 0x200, writing 0x204)
[ 1991.562313] pci 0000:03:00.1: restoring config space at offset 0x4 (was 0x0, writing 0xf3601000)
[ 1991.562320] pci 0000:03:00.1: restoring config space at offset 0x3 (was 0x800000, writing 0x800010)
[ 1991.562328] pci 0000:03:00.1: restoring config space at offset 0x1 (was 0x100000, writing 0x100006)
[ 1991.562377] sdhci-pci 0000:03:00.4: restoring config space at offset 0xf (was 0x300, writing 0x305)
[ 1991.562404] sdhci-pci 0000:03:00.4: restoring config space at offset 0x4 (was 0x0, writing 0xf3600000)
[ 1991.562411] sdhci-pci 0000:03:00.4: restoring config space at offset 0x3 (was 0x800000, writing 0x800010)
[ 1991.562419] sdhci-pci 0000:03:00.4: restoring config space at offset 0x1 (was 0x100000, writing 0x100006)
[ 1991.562557] sky2 0000:04:00.0: restoring config space at offset 0xf (was 0x100, writing 0x104)
[ 1991.562567] sky2 0000:04:00.0: restoring config space at offset 0xc (was 0x0, writing 0xf2200000)
[ 1991.562583] sky2 0000:04:00.0: restoring config space at offset 0x6 (was 0x1, writing 0xa001)
[ 1991.562591] sky2 0000:04:00.0: restoring config space at offset 0x4 (was 0x4, writing 0xf2220004)
[ 1991.562597] sky2 0000:04:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[ 1991.562605] sky2 0000:04:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100407)
[ 1991.562815] PM: early resume of devices complete after 1.651 msecs
[ 1991.562953] ehci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 1991.562962] ehci_hcd 0000:00:1a.0: setting latency timer to 64
[ 1991.563001] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[ 1991.563011] HDA Intel 0000:00:1b.0: setting latency timer to 64
[ 1991.563017] ehci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[ 1991.563021] pci 0000:00:1e.0: setting latency timer to 64
[ 1991.563030] ehci_hcd 0000:00:1d.0: setting latency timer to 64
[ 1991.563045] ahci 0000:00:1f.2: setting latency timer to 64
[ 1991.705355] PM: resume of drv:pci dev:0000:00:1f.3 complete after 142.523 msecs
[ 1991.705392] HDA Intel 0000:01:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[ 1991.705414] HDA Intel 0000:01:00.1: setting latency timer to 64
[ 1991.705438] PM: resume of drv:ahci dev:0000:00:1f.2 complete after 142.652 msecs
[ 1991.705455] HDA Intel 0000:00:1b.0: irq 44 for MSI/MSI-X
[ 1991.705494] HDA Intel 0000:01:00.1: irq 45 for MSI/MSI-X
[ 1991.705518] PM: resume of drv:HDA Intel dev:0000:00:1b.0 complete after 142.769 msecs
[ 1991.705539] sdhci-pci 0000:03:00.4: PCI INT C -> GSI 19 (level, low) -> IRQ 19
[ 1991.705555] sdhci-pci 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 1991.705618] radeon 0000:01:00.0: setting latency timer to 64
[ 1991.705650] sd 0:0:0:0: [sda] Starting disk
[ 1991.716332] PM: resume of drv:Sony Notebook Control Driver dev:SNY5001:00 complete after 153.609 msecs
[ 1991.731528] radeon 0000:01:00.0: WB enabled
[ 1991.747907] [drm] ring test succeeded in 1 usecs
[ 1991.747926] [drm] ib test succeeded in 0 usecs
[ 1991.828816] PM: resume of drv:usb dev:1-1.6 complete after 123.131 msecs
[ 1991.828828] PM: resume of drv:btusb dev:1-1.6:1.0 complete after 123.129 msecs
[ 1991.828836] PM: resume of drv:btusb dev:1-1.6:1.1 complete after 123.067 msecs
[ 1991.828843] PM: resume of drv:usb dev:1-1.6:1.3 complete after 122.965 msecs
[ 1991.828848] PM: resume of drv: dev:ep_82 complete after 123.115 msecs
[ 1991.828853] PM: resume of drv: dev:ep_03 complete after 123.048 msecs
[ 1991.828866] PM: resume of drv:usb dev:2-1.2 complete after 122.951 msecs
[ 1991.828874] PM: resume of drv:usbhid dev:2-1.2:1.0 complete after 122.942 msecs
[ 1991.828883] PM: resume of drv: dev:ep_00 complete after 122.879 msecs
[ 1991.828886] PM: resume of drv:usbhid dev:2-1.2:1.1 complete after 122.916 msecs
[ 1991.828890] PM: resume of drv:usb dev:1-1.6:1.2 complete after 123.066 msecs
[ 1991.828893] PM: resume of drv: dev:ep_81 complete after 122.943 msecs
[ 1991.828896] PM: resume of drv: dev:ep_82 complete after 122.907 msecs
[ 1991.828901] PM: resume of drv: dev:ep_00 complete after 123.000 msecs
[ 1991.828904] PM: resume of drv: dev:ep_84 complete after 123.060 msecs
[ 1991.828907] PM: resume of drv: dev:ep_83 complete after 123.120 msecs
[ 1991.828914] PM: resume of drv: dev:ep_81 complete after 123.191 msecs
[ 1991.828921] PM: resume of drv: dev:ep_04 complete after 123.050 msecs
[ 1991.828927] PM: resume of drv: dev:ep_02 complete after 123.171 msecs
[ 1991.834865] PM: resume of drv:usb dev:1-1.2 complete after 129.292 msecs
[ 1991.834884] PM: resume of drv: dev:ep_00 complete after 129.230 msecs
[ 1991.834911] PM: resume of drv:uvcvideo dev:1-1.2:1.1 complete after 129.274 msecs
[ 1991.834921] PM: resume of drv:uvcvideo dev:1-1.2:1.0 complete after 129.327 msecs
[ 1991.834935] PM: resume of drv: dev:ep_83 complete after 129.319 msecs
[ 1992.023923] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[ 1992.023956] ata6: SATA link down (SStatus 0 SControl 300)
[ 1992.207573] sdhci-pci 0000:03:00.4: Will use DMA mode even though HW doesn't fully claim to support it.
[ 1992.207579] sdhci-pci 0000:03:00.0: Will use DMA mode even though HW doesn't fully claim to support it.
[ 1992.207584] sdhci-pci 0000:03:00.4: setting latency timer to 64
[ 1992.207589] sdhci-pci 0000:03:00.0: setting latency timer to 64
[ 1992.207613] PM: resume of drv:sdhci-pci dev:0000:03:00.4 complete after 502.953 msecs
[ 1992.207617] PM: resume of drv:sdhci-pci dev:0000:03:00.0 complete after 503.040 msecs
[ 1992.207636] PM: resume of drv:leds dev:mmc0:: complete after 392.577 msecs
[ 1992.232553] ata2.00: configured for UDMA/100
[ 1992.359293] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[ 1992.360043] ata1.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
[ 1992.361263] ata1.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
[ 1992.361533] ata1.00: configured for UDMA/100
[ 1992.406327] PM: resume of drv:sd dev:0:0:0:0 complete after 701.883 msecs
[ 1992.406371] PM: resume of drv:scsi_disk dev:0:0:0:0 complete after 199.041 msecs
[ 1992.406381] PM: resume of drv:scsi_device dev:0:0:0:0 complete after 701.921 msecs
[ 1992.958266] PM: resume of drv:radeon dev:0000:01:00.0 complete after 1255.054 msecs
[ 1992.958292] PM: resume of drv:drm dev:controlD64 complete after 550.754 msecs
[ 1992.961753] PM: resume of devices complete after 1401.266 msecs
[ 1992.961885] PM: resume devices took 1.400 seconds
[ 1992.961914] PM: Finishing wakeup.
[ 1992.961915] Restarting tasks ... done.
[ 1992.969579] video LNXVIDEO:01: Restoring backlight state
[ 1993.110240] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1993.113256] sky2 0000:04:00.0: eth0: enabling interface
[ 1993.113542] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 1993.712856] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=0
[ 1995.508127] wlan0: authenticate with 00:1d:6a:be:98:8b (try 1)
[ 1995.510114] wlan0: authenticated
[ 1995.510145] wlan0: associate with 00:1d:6a:be:98:8b (try 1)
[ 1995.512470] wlan0: RX AssocResp from 00:1d:6a:be:98:8b (capab=0x21 status=0 aid=7)
[ 1995.512475] wlan0: associated
[ 1995.512906] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1995.513040] cfg80211: Calling CRDA for country: US
[ 1995.521947] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[ 1995.521952] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[ 1995.521954] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[ 1995.521956] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[ 1995.521958] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[ 1995.521960] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[ 1995.521962] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[ 1995.521964] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[ 1995.521965] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[ 1995.521967] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[ 1995.521969] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[ 1995.521971] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[ 1995.521973] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[ 1995.521975] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[ 1995.521977] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[ 1995.521979] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[ 1995.521980] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[ 1995.521982] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[ 1995.521984] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[ 1995.521986] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[ 1995.521988] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[ 1995.521990] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[ 1995.521991] cfg80211: Disabling freq 2467 MHz
[ 1995.521993] cfg80211: Disabling freq 2472 MHz
[ 1995.521994] cfg80211: Disabling freq 2484 MHz
[ 1995.521997] cfg80211: Regulatory domain changed to country: US
[ 1995.521999] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 1995.522001] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 1995.522003] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[ 1995.522005] cfg80211:     (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1995.522007] cfg80211:     (5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1995.522008] cfg80211:     (5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1995.522010] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[ 2005.660373] wlan0: no IPv6 routers present
[ 2578.472774] usb 2-1.2: USB disconnect, address 3
[ 2579.737295] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 2579.737306] cfg80211: Restoring regulatory settings
[ 2579.737315] cfg80211: Calling CRDA to update world regulatory domain
[ 2579.744800] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[ 2579.744811] cfg80211: World regulatory domain updated:
[ 2579.744814] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 2579.744821] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2579.744826] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 2579.744832] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 2579.744837] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2579.744842] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2592.131387] wlan0: authenticate with 00:1d:6a:be:98:8b (try 1)
[ 2592.133359] wlan0: authenticated
[ 2592.133391] wlan0: associate with 00:1d:6a:be:98:8b (try 1)
[ 2592.138448] wlan0: RX AssocResp from 00:1d:6a:be:98:8b (capab=0x21 status=0 aid=7)
[ 2592.138453] wlan0: associated
[ 2592.138872] cfg80211: Calling CRDA for country: US
[ 2592.143884] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[ 2592.143887] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[ 2592.143889] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[ 2592.143891] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[ 2592.143893] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[ 2592.143895] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[ 2592.143897] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[ 2592.143899] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[ 2592.143901] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[ 2592.143903] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[ 2592.143905] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[ 2592.143907] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[ 2592.143908] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[ 2592.143910] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[ 2592.143912] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[ 2592.143914] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[ 2592.143916] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[ 2592.143918] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[ 2592.143919] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[ 2592.143922] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[ 2592.143923] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[ 2592.143925] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[ 2592.143927] cfg80211: Disabling freq 2467 MHz
[ 2592.143928] cfg80211: Disabling freq 2472 MHz
[ 2592.143929] cfg80211: Disabling freq 2484 MHz
[ 2592.143932] cfg80211: Regulatory domain changed to country: US
[ 2592.143934] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 2592.143936] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 2592.143938] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[ 2592.143940] cfg80211:     (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2592.143941] cfg80211:     (5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2592.143943] cfg80211:     (5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2592.143945] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[ 2625.775397] usb 2-1.2: new full speed USB device using ehci_hcd and address 4
[ 2625.873373] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.0/input/input13
[ 2625.873688] generic-usb 0003:046D:C52F.0003: input,hidraw0: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:1d.0-1.2/input0
[ 2625.876708] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.1/input/input14
[ 2625.877208] generic-usb 0003:046D:C52F.0004: input,hiddev0,hidraw1: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1d.0-1.2/input1
[ 3320.457578] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 3320.457589] cfg80211: Restoring regulatory settings
[ 3320.457598] cfg80211: Calling CRDA to update world regulatory domain
[ 3320.465438] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[ 3320.465448] cfg80211: World regulatory domain updated:
[ 3320.465452] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 3320.465458] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 3320.465464] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 3320.465495] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 3320.465504] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 3320.465512] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 3321.348345] wlan0: authenticate with 00:1d:6a:be:98:8b (try 1)
[ 3321.353364] wlan0: authenticated
[ 3321.353389] wlan0: associate with 00:1d:6a:be:98:8b (try 1)
[ 3321.357108] wlan0: RX AssocResp from 00:1d:6a:be:98:8b (capab=0x21 status=0 aid=7)
[ 3321.357114] wlan0: associated
[ 3321.357821] cfg80211: Calling CRDA for country: US
[ 3321.364886] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[ 3321.364894] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[ 3321.364899] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[ 3321.364905] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[ 3321.364909] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[ 3321.364915] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[ 3321.364919] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[ 3321.364924] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[ 3321.364929] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[ 3321.364934] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[ 3321.364938] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[ 3321.364943] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[ 3321.364948] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[ 3321.364953] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[ 3321.364957] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[ 3321.364963] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[ 3321.364967] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[ 3321.364972] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[ 3321.364977] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[ 3321.364982] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[ 3321.364986] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[ 3321.364992] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[ 3321.364996] cfg80211: Disabling freq 2467 MHz
[ 3321.364999] cfg80211: Disabling freq 2472 MHz
[ 3321.365002] cfg80211: Disabling freq 2484 MHz
[ 3321.365008] cfg80211: Regulatory domain changed to country: US
[ 3321.365012] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 3321.365017] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 3321.365022] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[ 3321.365027] cfg80211:     (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 3321.365032] cfg80211:     (5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 3321.365037] cfg80211:     (5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 3321.365042] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
yajnamurti@yajnamurti-laptop:~$

---

### Post by Ymurti on 2011-07-09
yajnamurti@yajnamurti-laptop:~$ sudo fdisk -l
[sudo] password for yajnamurti: 

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa7e1f5f4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1681    13494272   27  Unknown
/dev/sda2   *        1681        1693      102400    7  HPFS/NTFS
/dev/sda3            1693       19559   143509971+   7  HPFS/NTFS
/dev/sda4           19560       38914   155462657    5  Extended
/dev/sda5           19560       38123   149110784   83  Linux
/dev/sda6           38123       38914     6350848   82  Linux swap / Solaris

---

### Post by wildmanne39 on 2011-07-09
Hi try this in a terminal
```
lsusb
```
and post the outcome  here by clicking on new reply and click # and paste the information between the brackets. Also if you did not properly eject it in windows, you will need to hook it back up to windows and eject it properly before you can use it in ubuntu.

---

### Post by Ymurti on 2011-07-09
# 
"Bus 002 Device 004: ID 046d:c52f Logitech, Inc. Wireless Mouse M305
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 0489:e00f Foxconn / Hon Hai 
Bus 001 Device 003: ID 0c45:6464 Microdia 
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub"
yajnamurti@yajnamurti-laptop:~$ 


I did eject it properly from Windows.

Thank You for your quick reply.

---

### Post by Wim Sturkenboom on 2011-07-10
Immediately after inserting the usb device, run the follwoing command

```

dmesg |tail -n15

```

The output should look like
```

[65253.850029] usb 2-1: new high speed USB device using ehci_hcd and address 2
[65254.002823] usb 2-1: configuration #1 chosen from 1 choice
[65254.043682] Initializing USB Mass Storage driver...
[65254.043867] scsi6 : SCSI emulation for USB Mass Storage devices
[65254.043953] usb-storage: device found at 2
[65254.043955] usb-storage: waiting for device to settle before scanning
[65254.043966] usbcore: registered new interface driver usb-storage
[65254.043969] USB Mass Storage support registered.
[65259.040104] usb-storage: device scan complete
[65259.040459] scsi 6:0:0:0: Direct-Access     CBM      Flash Disk       5.00 PQ: 0 ANSI: 2
[65259.040846] sd 6:0:0:0: Attached scsi generic sg2 type 0
[65259.042337] sd 6:0:0:0: [sdb] 2062336 512-byte logical blocks: (1.05 GB/1007 MiB)
[65259.042819] sd 6:0:0:0: [sdb] Write Protect is off
[65259.042823] sd 6:0:0:0: [sdb] Mode Sense: 0b 00 00 08
[65259.042825] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[65259.044570] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[65259.044573]  sdb: sdb1
[65259.046701] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[65259.046705] sd 6:0:0:0: [sdb] Attached SCSI removable disk

```

Post the result between [noparse]```
 and 
```[/noparse] (that's what the little # (that wildmanne39 was refering to) does when your editing a post in advanced mode).

---

### Post by Ymurti on 2011-07-10
```

[ 8743.758581] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[ 8743.758588] cfg80211: Disabling freq 2467 MHz
[ 8743.758593] cfg80211: Disabling freq 2472 MHz
[ 8743.758597] cfg80211: Disabling freq 2484 MHz
[ 8743.758606] cfg80211: Regulatory domain changed to country: US
[ 8743.758612] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 8743.758620] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 8743.758628] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[ 8743.758635] cfg80211:     (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 8743.758642] cfg80211:     (5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 8743.758650] cfg80211:     (5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 8743.758658] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[ 8833.971420] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=0
[10490.167990] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=600
[10491.789035] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=0

```

---

### Post by wildmanne39 on 2011-07-10
Hi, I am not sure why we are seeing sda5 instead of sdb or sdx for example.
Try this command in a terminal
```
sudo fdisk -l
```
and post the outcome  here by clicking on new reply and click # and paste the information between the brackets. Also have you opened disk utility to see if it is there if so click on it and mount it.

---

### Post by Ymurti on 2011-07-10
> **wildmanne39 said:**
> Hi, I am not sure why we are seeing sda5 instead of sdb or sdx for example.


I think I know why. Some time ago I tried to install Ubuntu in a laptop and this external storage device was mounted so Ubuntu began to be installed in the external storage device and has created some partitions in the external storage device. I think is for this reason that we see sda5. The point is that I have some data on the  external storage device and I do not want to loose it.

---

### Post by Ymurti on 2011-07-10
Here it is the result of the command sudo fdisk -l:



```


yajnamurti@yajnamurti-laptop:~$ sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa7e1f5f4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1681    13494272   27  Unknown
/dev/sda2   *        1681        1693      102400    7  HPFS/NTFS
/dev/sda3            1693       19559   143509971+   7  HPFS/NTFS
/dev/sda4           19560       38914   155462657    5  Extended
/dev/sda5           19560       38123   149110784   83  Linux
/dev/sda6           38123       38914     6350848   82  Linux swap / Solaris


```

---

### Post by wildmanne39 on 2011-07-10
Hi, so far I have seen nothing that looks like it is even seeing it. Did you try to mount it in disk utility?

---

### Post by Ymurti on 2011-07-10
[ATTACH]197102[/ATTACH]

[ATTACH]197103[/ATTACH]

I used disk utility and could see the external storage device.I have mounted all the partitions but still I can not see my data. I have attached some screen shots, I hope yoy can see them.

Thank You very much for your help.

---

### Post by wildmanne39 on 2011-07-10
> **Ymurti said:**
> [ATTACH]197102[/ATTACH]

[ATTACH]197103[/ATTACH]

I used disk utility and could see the external storage device.I have mounted all the partitions but still I can not see my data. I have attached some screen shots, I hope yoy can see them.

Thank You very much for your help.Hi, those partitions are on your internal drive, the one you need to click on is the 147 gigs in that window of your screenshot you should me in disk utility and mount it, then open file manager and click on 147 gigs and you should be able to access your files.

---

### Post by Ymurti on 2011-07-10
Sorry I made a mistake. I said I could see the external storage device but it is not, that is my internal drive. So that means disk utility can not see the external storage device. I am suspicious that I have some problem with my usb in my laptop. I just tried to open the external storage device in another computer with Ubuntu and it has mounted the external storage device without problem. So anyway thank you a lot and I will try to repair my usb port.

---

### Post by wildmanne39 on 2011-07-10
> **Ymurti said:**
> Sorry I made a mistake. I said I could see the external storage device but it is not, that is my internal drive. So that means disk utility can not see the external storage device. I am suspicious that I have some problem with my usb in my laptop. I just tried to open the external storage device in another computer with Ubuntu and it has mounted the external storage device without problem. So anyway thank you a lot and I will try to repair my usb port.
Hi, your welcome, enjoy ubuntu.

---

