---
title: "Where'd my webcam go?"
date: 2011-05-29
forum: New to Ubuntu
---

### Post by port_launay on 2011-05-29
I bought my wife a usb webcam so that she and I can Skype while she's away.
Before I set it up on her Windows laptop I tried it on mine and now I've lost my own built in one.
Nothing seems to be able to acknowledge its existence - Cheese and Skype simply say it aint there.

Can anyone help, I'm a complete newb so any help would be greatly appreciated.

---

### Post by webofunni on 2011-05-29
```
ls -l /dev/video*
```

?

---

### Post by port_launay on 2011-05-29
> **webofunni said:**
> ?

ls: cannot access /dev/video*: No such file or directory

---

### Post by webofunni on 2011-05-29
try

```

udevadm trigger

```

and execute the previous command again

---

### Post by no2498 on 2011-05-29
open a terminal type gstreamer-properties click enter

click video set it to the cam you like to use

---

### Post by port_launay on 2011-05-29
> **webofunni said:**
> try

```

udevadm trigger

```

and execute the previous command again

This has no effect.

> **no2498 said:**
> open a terminal type gstreamer-properties click enter

click video set it to the cam you like to use

When I try to change the default input to anything other than test I get the following message in the terminal;

gstreamer-properties-Message: Error running pipeline 'Video for Linux 2 (v4l2)': Cannot identify device "/dev/video0". [v4l2_calls.c(493): gst_v4l2_open (): /GstPipeline:pipeline2/GstV4l2Src:v4l2src2:
system error: No such file or directory]

---

### Post by webofunni on 2011-05-29
Reboot the system, if you have not done that. Paste the result of 

```

dmesg
lsmod
lsusb

```

if the issue persists.

---

### Post by port_launay on 2011-05-29
> **webofunni said:**
> Reboot the system, if you have not done that. Paste the result of 

```

dmesg

```

if the issue persists.

[ 2939.588073] PM: freeze of devices complete after 278.299 msecs
[ 2939.589020] PM: late freeze of devices complete after 0.942 msecs
[ 2939.589106] ACPI: Preparing to enter system sleep state S4
[ 2939.589218] PM: Saving platform NVS memory
[ 2939.589254] Disabling non-boot CPUs ...
[ 2939.589603] Broke affinity for irq 16
[ 2939.589626] Broke affinity for irq 22
[ 2939.692018] CPU 1 is now offline
[ 2939.692368] Extended CMOS year: 2000
[ 2939.692465] PM: Creating hibernation image:
[ 2939.696009] PM: Need to copy 340560 pages
[ 2939.696009] PM: Normal pages needed: 53664 + 1024, available pages: 174493
[ 2939.696009] PM: Restoring platform NVS memory
[ 2939.696009] Extended CMOS year: 2000
[ 2939.696009] Enabling non-boot CPUs ...
[ 2939.696009] Booting Node 0 Processor 1 APIC 0x1
[ 2939.590642] Initializing CPU#1
[ 2939.590642] Switch to broadcast mode on CPU1
[ 2939.788033] Switched to NOHz mode on CPU #1
[ 2939.788097] CPU1 is up
[ 2939.788269] ACPI: Waking up from system sleep state S4
[ 2939.789327] pata_amd 0000:00:06.0: restoring config space at offset 0x1 (was 0xb00001, writing 0xb00005)
[ 2939.789352] HDA Intel 0000:00:07.0: restoring config space at offset 0x1 (was 0xb00006, writing 0xb00002)
[ 2939.789411] pci 0000:00:00.0: Found enabled HT MSI Mapping
[ 2939.789479] pci 0000:00:00.0: Found enabled HT MSI Mapping
[ 2939.789495] ahci 0000:00:09.0: restoring config space at offset 0x1 (was 0xb00003, writing 0xb00007)
[ 2939.789558] pci 0000:00:00.0: Found enabled HT MSI Mapping
[ 2939.789642] pci 0000:00:00.0: Found enabled HT MSI Mapping
[ 2939.789732] pci 0000:00:00.0: Found enabled HT MSI Mapping
[ 2939.789826] pci 0000:00:00.0: Found enabled HT MSI Mapping
[ 2939.804024] firewire_ohci 0000:02:05.0: BAR 0: set to [mem 0xf6100000-0xf61007ff] (PCI address [0xf6100000-0xf61007ff])
[ 2939.804043] firewire_ohci 0000:02:05.0: restoring config space at offset 0x3 (was 0x800000, writing 0x804010)
[ 2939.804048] firewire_ohci 0000:02:05.0: restoring config space at offset 0x1 (was 0x2100000, writing 0x2100106)
[ 2939.820023] sdhci-pci 0000:02:05.1: BAR 0: set to [mem 0xf6100800-0xf61008ff] (PCI address [0xf6100800-0xf61008ff])
[ 2939.820042] sdhci-pci 0000:02:05.1: restoring config space at offset 0x3 (was 0x800000, writing 0x804010)
[ 2939.820047] sdhci-pci 0000:02:05.1: restoring config space at offset 0x1 (was 0x2100000, writing 0x2100106)
[ 2939.820624] PM: early restore of devices complete after 31.696 msecs
[ 2939.941536] ohci_hcd 0000:00:02.0: setting latency timer to 64
[ 2939.941567] ehci_hcd 0000:00:02.1: setting latency timer to 64
[ 2939.941587] ohci_hcd 0000:00:04.0: setting latency timer to 64
[ 2939.941603] ehci_hcd 0000:00:04.1: setting latency timer to 64
[ 2939.941621] pata_amd 0000:00:06.0: setting latency timer to 64
[ 2939.941699] pci 0000:00:08.0: setting latency timer to 64
[ 2939.941718] HDA Intel 0000:00:07.0: PCI INT A -> Link[LAZA] -> GSI 21 (level, low) -> IRQ 21
[ 2939.941723] HDA Intel 0000:00:07.0: setting latency timer to 64
[ 2939.957694] sdhci-pci 0000:02:05.1: PCI INT B -> Link[LNK2] -> GSI 7 (level, low) -> IRQ 7
[ 2939.957699] sdhci-pci 0000:02:05.1: Will use DMA mode even though HW doesn't fully claim to support it.
[ 2939.998013] usb usb3: root hub lost power or was reset
[ 2940.000022] usb usb4: root hub lost power or was reset
[ 2940.000120] firewire_core: skipped bus generations, destroying all nodes
[ 2940.000137] usb usb2: root hub lost power or was reset
[ 2940.000154] ehci_hcd 0000:00:04.1: cache line size of 64 is not supported
[ 2940.000192] usb usb1: root hub lost power or was reset
[ 2940.000199] ehci_hcd 0000:00:02.1: cache line size of 64 is not supported
[ 2940.024151] ahci 0000:00:09.0: PCI INT A -> Link[LSI0] -> GSI 23 (level, low) -> IRQ 23
[ 2940.024155] ahci 0000:00:09.0: setting latency timer to 64
[ 2940.024255] sd 2:0:0:0: [sda] Starting disk
[ 2940.024631] ata2: port disabled. ignoring.
[ 2940.132029] PM: restore of drv:usb dev:usb2 complete after 189.488 msecs
[ 2940.132040] PM: restore of drv:hub dev:2-0:1.0 complete after 189.482 msecs
[ 2940.132047] PM: restore of drv: dev:ep_00 complete after 189.454 msecs
[ 2940.132053] PM: restore of drv: dev:ep_81 complete after 189.477 msecs
[ 2940.132070] PM: restore of drv:usb dev:usb1 complete after 189.605 msecs
[ 2940.132079] PM: restore of drv:hub dev:1-0:1.0 complete after 189.595 msecs
[ 2940.132087] PM: restore of drv: dev:ep_00 complete after 189.565 msecs
[ 2940.132093] PM: restore of drv: dev:ep_81 complete after 189.590 msecs
[ 2940.196038] PM: restore of drv:usb dev:usb3 complete after 253.427 msecs
[ 2940.196048] PM: restore of drv:hub dev:3-0:1.0 complete after 253.419 msecs
[ 2940.196056] PM: restore of drv: dev:ep_00 complete after 253.390 msecs
[ 2940.196062] PM: restore of drv: dev:ep_81 complete after 253.414 msecs
[ 2940.204293] ata1.00: ACPI cmd ef/03:22:00:00:00:a0 (SET FEATURES) filtered out
[ 2940.204297] ata1.00: ACPI cmd ef/03:0c:00:00:00:a0 (SET FEATURES) filtered out
[ 2940.204308] ata1: nv_mode_filter: 0x39f&0x739f->0x39f, BIOS=0x0 (0xc600) ACPI=0x39f (120:600:0x12)
[ 2940.236231] ata1.00: configured for MWDMA2
[ 2940.288283] PM: restore of drv:battery dev:PNP0C0A:00 complete after 263.494 msecs
[ 2940.289052] i8042 kbd 00:09: wake-up capability disabled by ACPI
[ 2940.300023] PM: restore of drv:usb dev:usb4 complete after 357.339 msecs
[ 2940.300035] PM: restore of drv:hub dev:4-0:1.0 complete after 357.333 msecs
[ 2940.300042] PM: restore of drv: dev:ep_00 complete after 357.305 msecs
[ 2940.300048] PM: restore of drv: dev:ep_81 complete after 357.328 msecs
[ 2940.344024] ata6: SATA link down (SStatus 0 SControl 300)
[ 2940.344039] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[ 2940.344051] ata4: SATA link down (SStatus 0 SControl 300)
[ 2940.344062] ata5: SATA link down (SStatus 0 SControl 300)
[ 2940.349030] ata3.00: configured for UDMA/100
[ 2940.368609] PM: restore of drv:sd dev:2:0:0:0 complete after 425.664 msecs
[ 2940.368630] PM: restore of drv:scsi_device dev:2:0:0:0 complete after 425.668 msecs
[ 2940.464459] PM: restore of drv:forcedeth dev:0000:00:0a.0 complete after 522.719 msecs
[ 2940.464468] PM: restore of drv:net dev:eth0 complete after 166.651 msecs
[ 2940.500042] firewire_core: rediscovered device fw0
[ 2942.821328] PM: restore of drv:nvidia dev:0000:00:12.0 complete after 2879.424 msecs
[ 2942.821358] PM: restore of drv:i2c dev:i2c-2 complete after 2355.168 msecs
[ 2942.821382] PM: restore of devices complete after 2879.922 msecs
[ 2942.821616] PM: Image restored successfully.
[ 2942.821618] Restarting tasks ... done.
[ 2942.835326] PM: Basic memory bitmaps freed
[ 2942.835341] video LNXVIDEO:00: Restoring backlight state
[ 2945.135246] forcedeth 0000:00:0a.0: irq 42 for MSI/MSI-X
[ 2945.135453] forcedeth 0000:00:0a.0: eth0: no link during initialization
[ 2945.136228] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 2945.146102] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2947.409888] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[ 2948.003954] wlan0: authenticate with c0:3f:0e:fb:56:88 (try 1)
[ 2948.008709] wlan0: authenticated
[ 2948.008762] wlan0: associate with c0:3f:0e:fb:56:88 (try 1)
[ 2948.011242] wlan0: RX AssocResp from c0:3f:0e:fb:56:88 (capab=0x411 status=0 aid=2)
[ 2948.011249] wlan0: associated
[ 2948.012203] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 2958.224069] wlan0: no IPv6 routers present
[ 4978.897744] wlan0: deauthenticating from c0:3f:0e:fb:56:88 by local choice (reason=3)
[ 4978.932236] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 4978.932253] cfg80211: Restoring regulatory settings
[ 4978.932279] cfg80211: Calling CRDA to update world regulatory domain
[ 4978.989461] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[ 4978.989481] cfg80211: World regulatory domain updated:
[ 4978.989487] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 4978.989496] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 4978.989505] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 4978.989513] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 4978.989521] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 4978.989529] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 4979.008573] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4979.065501] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4981.356391] wlan0: authenticate with c0:3f:0e:fb:56:88 (try 1)
[ 4981.358772] wlan0: authenticated
[ 4981.358879] wlan0: associate with c0:3f:0e:fb:56:88 (try 1)
[ 4981.361336] wlan0: RX AssocResp from c0:3f:0e:fb:56:88 (capab=0x411 status=0 aid=2)
[ 4981.361348] wlan0: associated
[ 4981.363130] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 4991.664029] wlan0: no IPv6 routers present
[ 6678.743422] wlan0: deauthenticating from c0:3f:0e:fb:56:88 by local choice (reason=3)
[ 6678.780152] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 6678.780160] cfg80211: Restoring regulatory settings
[ 6678.780166] cfg80211: Calling CRDA to update world regulatory domain
[ 6678.789187] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[ 6678.789196] cfg80211: World regulatory domain updated:
[ 6678.789199] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 6678.789204] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 6678.789208] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 6678.789212] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 6678.789216] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 6678.789220] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 6680.795094] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[ 6683.381603] PM: Marking nosave pages: 000000000009e000 - 0000000000100000
[ 6683.381608] PM: Basic memory bitmaps created
[ 6683.381610] PM: Syncing filesystems ... done.
[ 6683.466623] Freezing user space processes ... (elapsed 0.01 seconds) done.
[ 6683.480068] Freezing remaining freezable tasks ... (elapsed 0.01 seconds) done.
[ 6683.496068] PM: Preallocating image memory... done (allocated 568029 pages)
[ 6683.991952] PM: Allocated 2272116 kbytes in 0.49 seconds (4636.97 MB/s)
[ 6683.991955] Suspending console(s) (use no_console_suspend to debug)
[ 6683.992552] sd 2:0:0:0: [sda] Synchronizing SCSI cache
[ 6683.993518] i8042 aux 00:0a: wake-up capability disabled by ACPI
[ 6683.993546] i8042 kbd 00:09: wake-up capability enabled by ACPI
[ 6683.993980] ACPI handle has no context!
[ 6683.994664] ACPI handle has no context!
[ 6683.994676] sdhci-pci 0000:02:05.1: PCI INT B disabled
[ 6683.994680] ACPI handle has no context!
[ 6683.995180] ahci 0000:00:09.0: PCI INT A disabled
[ 6684.008105] ata2: port disabled. ignoring.
[ 6684.174592] PM: freeze of drv:nvidia dev:0000:00:12.0 complete after 180.581 msecs
[ 6684.200037] HDA Intel 0000:00:07.0: PCI INT A disabled
[ 6684.216025] PM: freeze of drv:HDA Intel dev:0000:00:07.0 complete after 207.979 msecs
[ 6684.216056] PM: freeze of drv: dev:pci0000:00 complete after 207.871 msecs
[ 6684.216072] PM: freeze of devices complete after 223.783 msecs
[ 6684.217043] PM: late freeze of devices complete after 0.968 msecs
[ 6684.217129] ACPI: Preparing to enter system sleep state S4
[ 6684.217241] PM: Saving platform NVS memory
[ 6684.217275] Disabling non-boot CPUs ...
[ 6684.217624] Broke affinity for irq 16
[ 6684.320018] CPU 1 is now offline
[ 6684.320369] Extended CMOS year: 2000
[ 6684.320465] PM: Creating hibernation image:
[ 6684.324010] PM: Need to copy 377637 pages
[ 6684.324010] PM: Normal pages needed: 59620 + 1024, available pages: 168537
[ 6684.324010] PM: Restoring platform NVS memory
[ 6684.324010] Extended CMOS year: 2000
[ 6684.324010] Enabling non-boot CPUs ...
[ 6684.324010] Booting Node 0 Processor 1 APIC 0x1
[ 6684.218661] Initializing CPU#1
[ 6684.218661] Switch to broadcast mode on CPU1
[ 6684.416032] Switched to NOHz mode on CPU #1
[ 6684.416095] CPU1 is up
[ 6684.416269] ACPI: Waking up from system sleep state S4
[ 6684.417330] pata_amd 0000:00:06.0: restoring config space at offset 0x1 (was 0xb00001, writing 0xb00005)
[ 6684.417356] HDA Intel 0000:00:07.0: restoring config space at offset 0x1 (was 0xb00006, writing 0xb00002)
[ 6684.417414] pci 0000:00:00.0: Found enabled HT MSI Mapping
[ 6684.417483] pci 0000:00:00.0: Found enabled HT MSI Mapping
[ 6684.417499] ahci 0000:00:09.0: restoring config space at offset 0x1 (was 0xb00003, writing 0xb00007)
[ 6684.417562] pci 0000:00:00.0: Found enabled HT MSI Mapping
[ 6684.417646] pci 0000:00:00.0: Found enabled HT MSI Mapping
[ 6684.417737] pci 0000:00:00.0: Found enabled HT MSI Mapping
[ 6684.417830] pci 0000:00:00.0: Found enabled HT MSI Mapping
[ 6684.432024] firewire_ohci 0000:02:05.0: BAR 0: set to [mem 0xf6100000-0xf61007ff] (PCI address [0xf6100000-0xf61007ff])
[ 6684.432042] firewire_ohci 0000:02:05.0: restoring config space at offset 0x3 (was 0x800000, writing 0x804010)
[ 6684.432048] firewire_ohci 0000:02:05.0: restoring config space at offset 0x1 (was 0x2100000, writing 0x2100106)
[ 6684.448023] sdhci-pci 0000:02:05.1: BAR 0: set to [mem 0xf6100800-0xf61008ff] (PCI address [0xf6100800-0xf61008ff])
[ 6684.448042] sdhci-pci 0000:02:05.1: restoring config space at offset 0x3 (was 0x800000, writing 0x804010)
[ 6684.448048] sdhci-pci 0000:02:05.1: restoring config space at offset 0x1 (was 0x2100000, writing 0x2100106)
[ 6684.448624] PM: early restore of devices complete after 31.694 msecs
[ 6684.578413] ohci_hcd 0000:00:02.0: setting latency timer to 64
[ 6684.578444] ehci_hcd 0000:00:02.1: setting latency timer to 64
[ 6684.578462] ohci_hcd 0000:00:04.0: setting latency timer to 64
[ 6684.578482] ehci_hcd 0000:00:04.1: setting latency timer to 64
[ 6684.578544] pata_amd 0000:00:06.0: setting latency timer to 64
[ 6684.578623] HDA Intel 0000:00:07.0: PCI INT A -> Link[LAZA] -> GSI 21 (level, low) -> IRQ 21
[ 6684.578628] HDA Intel 0000:00:07.0: setting latency timer to 64
[ 6684.578663] pci 0000:00:08.0: setting latency timer to 64
[ 6684.578675] ahci 0000:00:09.0: PCI INT A -> Link[LSI0] -> GSI 23 (level, low) -> IRQ 23
[ 6684.578679] ahci 0000:00:09.0: setting latency timer to 64
[ 6684.579170] ata2: port disabled. ignoring.
[ 6684.579413] sdhci-pci 0000:02:05.1: PCI INT B -> Link[LNK2] -> GSI 7 (level, low) -> IRQ 7
[ 6684.579417] sdhci-pci 0000:02:05.1: Will use DMA mode even though HW doesn't fully claim to support it.
[ 6684.580786] sd 2:0:0:0: [sda] Starting disk
[ 6684.634011] usb usb3: root hub lost power or was reset
[ 6684.636017] usb usb4: root hub lost power or was reset
[ 6684.636098] usb usb1: root hub lost power or was reset
[ 6684.636106] ehci_hcd 0000:00:02.1: cache line size of 64 is not supported
[ 6684.636153] usb usb2: root hub lost power or was reset
[ 6684.636156] firewire_core: skipped bus generations, destroying all nodes
[ 6684.636161] ehci_hcd 0000:00:04.1: cache line size of 64 is not supported
[ 6684.756301] ata1.00: ACPI cmd ef/03:22:00:00:00:a0 (SET FEATURES) filtered out
[ 6684.756305] ata1.00: ACPI cmd ef/03:0c:00:00:00:a0 (SET FEATURES) filtered out
[ 6684.756317] ata1: nv_mode_filter: 0x39f&0x739f->0x39f, BIOS=0x0 (0xc600) ACPI=0x39f (120:600:0x12)
[ 6684.768032] PM: restore of drv:usb dev:usb2 complete after 187.506 msecs
[ 6684.768053] PM: restore of drv:usb dev:usb1 complete after 187.602 msecs
[ 6684.768064] PM: restore of drv:hub dev:2-0:1.0 complete after 187.522 msecs
[ 6684.768071] PM: restore of drv: dev:ep_00 complete after 187.494 msecs
[ 6684.768077] PM: restore of drv:hub dev:1-0:1.0 complete after 187.605 msecs
[ 6684.768084] PM: restore of drv: dev:ep_00 complete after 187.577 msecs
[ 6684.768090] PM: restore of drv: dev:ep_81 complete after 187.530 msecs
[ 6684.768096] PM: restore of drv: dev:ep_81 complete after 187.606 msecs
[ 6684.788236] ata1.00: configured for MWDMA2
[ 6684.832042] PM: restore of drv:usb dev:usb3 complete after 251.446 msecs
[ 6684.832051] PM: restore of drv:hub dev:3-0:1.0 complete after 251.438 msecs
[ 6684.832058] PM: restore of drv: dev:ep_00 complete after 251.410 msecs
[ 6684.832064] PM: restore of drv: dev:ep_81 complete after 251.434 msecs
[ 6684.844268] PM: restore of drv:battery dev:PNP0C0A:00 complete after 263.228 msecs
[ 6684.845033] i8042 kbd 00:09: wake-up capability disabled by ACPI
[ 6684.896028] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[ 6684.896041] ata5: SATA link down (SStatus 0 SControl 300)
[ 6684.896056] ata6: SATA link down (SStatus 0 SControl 300)
[ 6684.896067] ata4: SATA link down (SStatus 0 SControl 300)
[ 6684.901031] ata3.00: configured for UDMA/100
[ 6684.923297] PM: restore of drv:sd dev:2:0:0:0 complete after 342.510 msecs
[ 6684.923310] PM: restore of drv:scsi_device dev:2:0:0:0 complete after 342.480 msecs
[ 6684.936032] PM: restore of drv:usb dev:usb4 complete after 355.366 msecs
[ 6684.936042] PM: restore of drv:hub dev:4-0:1.0 complete after 355.359 msecs
[ 6684.936050] PM: restore of drv: dev:ep_00 complete after 355.332 msecs
[ 6684.936056] PM: restore of drv: dev:ep_81 complete after 355.355 msecs
[ 6685.100484] PM: restore of drv:forcedeth dev:0000:00:0a.0 complete after 521.784 msecs
[ 6685.100493] PM: restore of drv:net dev:eth0 complete after 248.654 msecs
[ 6685.592377] firewire_core: rediscovered device fw0
[ 6687.461899] PM: restore of drv:nvidia dev:0000:00:12.0 complete after 2882.585 msecs
[ 6687.461928] PM: restore of drv:i2c dev:i2c-2 complete after 2359.776 msecs
[ 6687.461952] PM: restore of devices complete after 2883.614 msecs
[ 6687.462184] PM: Image restored successfully.
[ 6687.462186] Restarting tasks ... done.
[ 6687.482407] PM: Basic memory bitmaps freed
[ 6687.482424] video LNXVIDEO:00: Restoring backlight state
[ 6689.510420] forcedeth 0000:00:0a.0: irq 42 for MSI/MSI-X
[ 6689.510627] forcedeth 0000:00:0a.0: eth0: no link during initialization
[ 6689.511312] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 6690.551653] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[ 6725.181649] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 6727.375638] wlan0: authenticate with c0:3f:0e:fb:56:88 (try 1)
[ 6727.377681] wlan0: authenticated
[ 6727.377805] wlan0: associate with c0:3f:0e:fb:56:88 (try 1)
[ 6727.380243] wlan0: RX AssocResp from c0:3f:0e:fb:56:88 (capab=0x411 status=0 aid=3)
[ 6727.380252] wlan0: associated
[ 6727.381975] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 6737.760029] wlan0: no IPv6 routers present
[ 7205.959017] wlan0: deauthenticating from c0:3f:0e:fb:56:88 by local choice (reason=3)
[ 7205.996117] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 7205.996125] cfg80211: Restoring regulatory settings
[ 7205.996133] cfg80211: Calling CRDA to update world regulatory domain
[ 7206.003822] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[ 7206.003832] cfg80211: World regulatory domain updated:
[ 7206.003834] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 7206.003839] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 7206.003843] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 7206.003847] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 7206.003851] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 7206.003855] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 7207.797820] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[ 7210.208254] PM: Marking nosave pages: 000000000009e000 - 0000000000100000
[ 7210.208259] PM: Basic memory bitmaps created
[ 7210.208261] PM: Syncing filesystems ... done.
[ 7210.325147] Freezing user space processes ... (elapsed 0.01 seconds) done.
[ 7210.340077] Freezing remaining freezable tasks ... (elapsed 0.01 seconds) done.
[ 7210.356076] PM: Preallocating image memory... done (allocated 378027 pages)
[ 7210.609353] PM: Allocated 1512108 kbytes in 0.25 seconds (6048.43 MB/s)
[ 7210.609356] Suspending console(s) (use no_console_suspend to debug)
[ 7210.612197] sd 2:0:0:0: [sda] Synchronizing SCSI cache
[ 7210.613058] i8042 aux 00:0a: wake-up capability disabled by ACPI
[ 7210.613089] i8042 kbd 00:09: wake-up capability enabled by ACPI
[ 7210.613526] ACPI handle has no context!
[ 7210.614208] ACPI handle has no context!
[ 7210.614218] sdhci-pci 0000:02:05.1: PCI INT B disabled
[ 7210.614223] ACPI handle has no context!
[ 7210.614725] ahci 0000:00:09.0: PCI INT A disabled
[ 7210.620222] ata2: port disabled. ignoring.
[ 7210.794095] PM: freeze of drv:nvidia dev:0000:00:12.0 complete after 180.494 msecs
[ 7210.812042] HDA Intel 0000:00:07.0: PCI INT A disabled
[ 7210.828027] PM: freeze of drv:HDA Intel dev:0000:00:07.0 complete after 207.959 msecs
[ 7210.828056] PM: freeze of drv: dev:pci0000:00 complete after 207.889 msecs
[ 7210.828071] PM: freeze of devices complete after 218.393 msecs
[ 7210.829043] PM: late freeze of devices complete after 0.968 msecs
[ 7210.829130] ACPI: Preparing to enter system sleep state S4
[ 7210.829243] PM: Saving platform NVS memory
[ 7210.829277] Disabling non-boot CPUs ...
[ 7210.836128] Broke affinity for irq 16
[ 7210.940019] CPU 1 is now offline
[ 7210.940395] Extended CMOS year: 2000
[ 7210.940493] PM: Creating hibernation image:
[ 7210.944009] PM: Need to copy 377783 pages
[ 7210.944009] PM: Normal pages needed: 59923 + 1024, available pages: 168234
[ 7210.944009] PM: Restoring platform NVS memory
[ 7210.944009] Extended CMOS year: 2000
[ 7210.944009] Enabling non-boot CPUs ...
[ 7210.944009] Booting Node 0 Processor 1 APIC 0x1
[ 7210.837162] Initializing CPU#1
[ 7210.837162] Switch to broadcast mode on CPU1
[ 7211.036032] Switched to NOHz mode on CPU #1
[ 7211.036094] CPU1 is up
[ 7211.036263] ACPI: Waking up from system sleep state S4
[ 7211.037329] pata_amd 0000:00:06.0: restoring config space at offset 0x1 (was 0xb00001, writing 0xb00005)
[ 7211.037355] HDA Intel 0000:00:07.0: restoring config space at offset 0x1 (was 0xb00006, writing 0xb00002)
[ 7211.037413] pci 0000:00:00.0: Found enabled HT MSI Mapping
[ 7211.037482] pci 0000:00:00.0: Found enabled HT MSI Mapping
[ 7211.037498] ahci 0000:00:09.0: restoring config space at offset 0x1 (was 0xb00003, writing 0xb00007)
[ 7211.037561] pci 0000:00:00.0: Found enabled HT MSI Mapping
[ 7211.037644] pci 0000:00:00.0: Found enabled HT MSI Mapping
[ 7211.037735] pci 0000:00:00.0: Found enabled HT MSI Mapping
[ 7211.037829] pci 0000:00:00.0: Found enabled HT MSI Mapping
[ 7211.052023] firewire_ohci 0000:02:05.0: BAR 0: set to [mem 0xf6100000-0xf61007ff] (PCI address [0xf6100000-0xf61007ff])
[ 7211.052041] firewire_ohci 0000:02:05.0: restoring config space at offset 0x3 (was 0x800000, writing 0x804010)
[ 7211.052047] firewire_ohci 0000:02:05.0: restoring config space at offset 0x1 (was 0x2100000, writing 0x2100106)
[ 7211.068023] sdhci-pci 0000:02:05.1: BAR 0: set to [mem 0xf6100800-0xf61008ff] (PCI address [0xf6100800-0xf61008ff])
[ 7211.068042] sdhci-pci 0000:02:05.1: restoring config space at offset 0x3 (was 0x800000, writing 0x804010)
[ 7211.068048] sdhci-pci 0000:02:05.1: restoring config space at offset 0x1 (was 0x2100000, writing 0x2100106)
[ 7211.068624] PM: early restore of devices complete after 31.696 msecs
[ 7211.197612] ohci_hcd 0000:00:02.0: setting latency timer to 64
[ 7211.197636] ehci_hcd 0000:00:02.1: setting latency timer to 64
[ 7211.197677] ohci_hcd 0000:00:04.0: setting latency timer to 64
[ 7211.197694] ehci_hcd 0000:00:04.1: setting latency timer to 64
[ 7211.197715] pata_amd 0000:00:06.0: setting latency timer to 64
[ 7211.197741] HDA Intel 0000:00:07.0: PCI INT A -> Link[LAZA] -> GSI 21 (level, low) -> IRQ 21
[ 7211.197746] HDA Intel 0000:00:07.0: setting latency timer to 64
[ 7211.197804] pci 0000:00:08.0: setting latency timer to 64
[ 7211.197817] ahci 0000:00:09.0: PCI INT A -> Link[LSI0] -> GSI 23 (level, low) -> IRQ 23
[ 7211.197823] ahci 0000:00:09.0: setting latency timer to 64
[ 7211.197927] ata2: port disabled. ignoring.
[ 7211.199136] sdhci-pci 0000:02:05.1: PCI INT B -> Link[LNK2] -> GSI 7 (level, low) -> IRQ 7
[ 7211.199140] sdhci-pci 0000:02:05.1: Will use DMA mode even though HW doesn't fully claim to support it.
[ 7211.200866] sd 2:0:0:0: [sda] Starting disk
[ 7211.252104] firewire_core: skipped bus generations, destroying all nodes
[ 7211.258009] usb usb3: root hub lost power or was reset
[ 7211.260019] usb usb4: root hub lost power or was reset
[ 7211.260064] usb usb2: root hub lost power or was reset
[ 7211.260084] ehci_hcd 0000:00:04.1: cache line size of 64 is not supported
[ 7211.260116] usb usb1: root hub lost power or was reset
[ 7211.260123] ehci_hcd 0000:00:02.1: cache line size of 64 is not supported
[ 7211.376293] ata1.00: ACPI cmd ef/03:22:00:00:00:a0 (SET FEATURES) filtered out
[ 7211.376297] ata1.00: ACPI cmd ef/03:0c:00:00:00:a0 (SET FEATURES) filtered out
[ 7211.376308] ata1: nv_mode_filter: 0x39f&0x739f->0x39f, BIOS=0x0 (0xc600) ACPI=0x39f (120:600:0x12)
[ 7211.392029] PM: restore of drv:usb dev:usb2 complete after 191.678 msecs
[ 7211.392038] PM: restore of drv:hub dev:2-0:1.0 complete after 191.662 msecs
[ 7211.392045] PM: restore of drv: dev:ep_00 complete after 191.587 msecs
[ 7211.392051] PM: restore of drv: dev:ep_81 complete after 191.649 msecs
[ 7211.392070] PM: restore of drv:usb dev:usb1 complete after 191.886 msecs
[ 7211.392078] PM: restore of drv:hub dev:1-0:1.0 complete after 191.843 msecs
[ 7211.392085] PM: restore of drv: dev:ep_00 complete after 191.763 msecs
[ 7211.392091] PM: restore of drv: dev:ep_81 complete after 191.828 msecs
[ 7211.408233] ata1.00: configured for MWDMA2
[ 7211.456045] PM: restore of drv:usb dev:usb3 complete after 255.558 msecs
[ 7211.456054] PM: restore of drv:hub dev:3-0:1.0 complete after 255.540 msecs
[ 7211.456061] PM: restore of drv: dev:ep_00 complete after 255.442 msecs
[ 7211.456067] PM: restore of drv: dev:ep_81 complete after 255.525 msecs
[ 7211.464262] PM: restore of drv:battery dev:PNP0C0A:00 complete after 265.921 msecs
[ 7211.465050] i8042 kbd 00:09: wake-up capability disabled by ACPI
[ 7211.516024] ata6: SATA link down (SStatus 0 SControl 300)
[ 7211.516039] ata5: SATA link down (SStatus 0 SControl 300)
[ 7211.516050] ata4: SATA link down (SStatus 0 SControl 300)
[ 7211.516063] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[ 7211.521055] ata3.00: configured for UDMA/100
[ 7211.543212] PM: restore of drv:sd dev:2:0:0:0 complete after 342.346 msecs
[ 7211.543309] PM: restore of drv:scsi_device dev:2:0:0:0 complete after 342.341 msecs
[ 7211.560024] PM: restore of drv:usb dev:usb4 complete after 359.377 msecs
[ 7211.560034] PM: restore of drv:hub dev:4-0:1.0 complete after 359.361 msecs
[ 7211.560041] PM: restore of drv: dev:ep_00 complete after 359.285 msecs
[ 7211.560047] PM: restore of drv: dev:ep_81 complete after 359.317 msecs
[ 7211.720507] PM: restore of drv:forcedeth dev:0000:00:0a.0 complete after 522.664 msecs
[ 7211.720515] PM: restore of drv:net dev:eth0 complete after 247.530 msecs
[ 7212.210728] firewire_core: rediscovered device fw0
[ 7214.086437] PM: restore of drv:nvidia dev:0000:00:12.0 complete after 2887.960 msecs
[ 7214.086503] PM: restore of drv:i2c dev:i2c-2 complete after 2364.272 msecs
[ 7214.086526] PM: restore of devices complete after 2888.991 msecs
[ 7214.086759] PM: Image restored successfully.
[ 7214.086761] Restarting tasks ... done.
[ 7214.099037] PM: Basic memory bitmaps freed
[ 7214.099055] video LNXVIDEO:00: Restoring backlight state
[ 7216.000360] forcedeth 0000:00:0a.0: irq 42 for MSI/MSI-X
[ 7216.000571] forcedeth 0000:00:0a.0: eth0: no link during initialization
[ 7216.001269] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 7216.013423] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 7217.757901] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[ 7218.232189] wlan0: authenticate with c0:3f:0e:fb:56:88 (try 1)
[ 7218.233647] wlan0: authenticated
[ 7218.233683] wlan0: associate with c0:3f:0e:fb:56:88 (try 1)
[ 7218.236238] wlan0: RX AssocResp from c0:3f:0e:fb:56:88 (capab=0x411 status=0 aid=3)
[ 7218.236244] wlan0: associated
[ 7218.237129] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 7229.056054] wlan0: no IPv6 routers present

---

### Post by port_launay on 2011-05-29
> **webofunni said:**
> Reboot the system, if you have not done that. Paste the result of 

```

lsmod

```

if the issue persists.

Module                  Size  Used by
nls_iso8859_1          12617  0 
nls_cp437              12751  0 
vfat                   17335  0 
fat                    55505  1 vfat
usb_storage            43946  0 
uas                    17676  0 
cryptd                 19801  0 
aes_i586               16956  1 
aes_generic            38023  1 aes_i586
binfmt_misc            13213  1 
parport_pc             32111  0 
ppdev                  12849  0 
vesafb                 13449  1 
nvidia               7098106  40 
arc4                   12473  2 
snd_hda_codec_conexant    43782  1 
snd_hda_intel          24140  2 
ath5k                 144412  0 
snd_hda_codec          90901  2 snd_hda_codec_conexant,snd_hda_intel
r852                   17878  0 
sm_common              16737  1 r852
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80244  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
nand                   49822  2 r852,sm_common
ath                    19141  1 ath5k
snd_rawmidi            25269  1 snd_seq_midi
nand_ids                8547  1 nand
snd_seq_midi_event     14475  1 snd_seq_midi
nand_ecc               13070  1 nand
joydev                 17322  0 
mac80211              257001  1 ath5k
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55295  13 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mtd                    26530  2 sm_common,nand
cfg80211              156212  3 ath5k,ath,mac80211
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
psmouse                59039  0 
i2c_nforce2            12906  0 
lp                     13349  0 
video                  18951  0 
parport                36746  3 parport_pc,ppdev,lp
k8temp                 12872  0 
hp_wmi                 13418  0 
serio_raw              12990  0 
sparse_keymap          13666  1 hp_wmi
ahci                   21591  2 
firewire_ohci          31504  0 
sdhci_pci              13623  0 
sdhci                  22720  1 sdhci_pci
firewire_core          56138  1 firewire_ohci
pata_amd               13762  0 
libahci                25548  1 ahci
forcedeth              58190  0 
crc_itu_t              12627  1 firewire_core

---

### Post by port_launay on 2011-05-29
> **webofunni said:**
> Reboot the system, if you have not done that. Paste the result of 

```

lsusb

```

if the issue persists.

Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by webofunni on 2011-05-29
I am not near to my system now. The output that you provided shows that system is not detecting the webcam. Do you have any other OS installed in the laptop. Webcam working in that ? 

I will check the logs once I get my system. In the mean time can you give 

```

lspci
hwinfo

```

also

---

### Post by port_launay on 2011-05-30
> **webofunni said:**
> 
```

lspci

```

00:00.0 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP67 ISA Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP67 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.3 Co-processor: nVidia Corporation MCP67 Co-processor (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:04.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:04.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP67 IDE Controller (rev a1)
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP67 PCI Bridge (rev a2)
00:09.0 IDE interface: nVidia Corporation MCP67 AHCI Controller (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0d.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:12.0 VGA compatible controller: nVidia Corporation C67 [GeForce 7150M / nForce 630M] (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
02:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
02:05.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
02:05.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
02:05.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
03:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)

---

### Post by port_launay on 2011-05-30
> **webofunni said:**
> 
```

hwinfo

```


Device: pci 0x001c "AR242x 802.11abg Wireless PCI Express Adapter"
  SubVendor: pci 0x103c "Hewlett-Packard Company"
  SubDevice: pci 0x137b 
  Revision: 0x01
  Driver: "ath5k"
  Driver Modules: "ath5k"
  Device File: wlan0
  Features: WLAN
  Memory Range: 0xf6000000-0xf600ffff (rw,non-prefetchable)
  IRQ: 19 (598865 events)
  HW Address: 00:1f:e2:ca:20:77
  Link detected: yes
  WLAN channels: 1 2 3 4 5 6 7 8 9 10 11 12 13
  WLAN frequencies: 2.412 2.417 2.422 2.427 2.432 2.437 2.442 2.447 2.452 2.457 2.462 2.467 2.472
  WLAN encryption modes: WEP40 WEP104 TKIP CCMP
  WLAN authentication modes: open sharedkey wpa-psk wpa-eap
  Module Alias: "pci:v0000168Cd0000001Csv0000103Csd0000137Bbc02sc00i00"
  Driver Info #0:
    Driver Status: ath5k is active
    Driver Activation Cmd: "modprobe ath5k"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #26 (PCI bridge)

37: ISA(PnP) 00.0: 0000 Unclassified device
  [Created at isapnp.142]
  UDI: /org/freedesktop/Hal/devices/pnp_PNP0a08
  Unique ID: z9pp.+GmdJItMGB9
  SysFS ID: /devices/pnp0/00:00
  SysFS BusID: 00:00
  Hardware Class: unknown
  Model: "Unclassified device"
  SubVendor: PNP "PnP"
  SubDevice: eisa 0x0a08 
  Config Status: cfg=new, avail=yes, need=no, active=unknown

38: ISA(PnP) 00.0: 0000 Unclassified device
  [Created at isapnp.142]
  UDI: /org/freedesktop/Hal/devices/pnp_PNP0103
  Unique ID: QL3u.fG36JLVNse9
  SysFS ID: /devices/pnp0/00:01
  SysFS BusID: 00:01
  Hardware Class: unknown
  Model: "Unclassified device"
  SubVendor: PNP "PnP"
  SubDevice: eisa 0x0103 
  Config Status: cfg=new, avail=yes, need=no, active=unknown

39: ISA(PnP) 00.0: 0000 Unclassified device
  [Created at isapnp.142]
  UDI: /org/freedesktop/Hal/devices/pnp_PNP0c02
  Unique ID: tWJy.B+yZ9Ve8gC1
  SysFS ID: /devices/pnp0/00:02
  SysFS BusID: 00:02
  Hardware Class: unknown
  Model: "Unclassified device"
  SubVendor: PNP "PnP"
  SubDevice: eisa 0x0c02 
  Config Status: cfg=new, avail=yes, need=no, active=unknown

40: ISA(PnP) 00.0: 0000 Unclassified device
  [Created at isapnp.142]
  UDI: /org/freedesktop/Hal/devices/pnp_PNP0c02_0
  Unique ID: KiZ0.B+yZ9Ve8gC1
  SysFS ID: /devices/pnp0/00:03
  SysFS BusID: 00:03
  Hardware Class: unknown
  Model: "Unclassified device"
  SubVendor: PNP "PnP"
  SubDevice: eisa 0x0c02 
  Config Status: cfg=new, avail=yes, need=no, active=unknown

41: ISA(PnP) 00.0: 0000 Unclassified device
  [Created at isapnp.142]
  UDI: /org/freedesktop/Hal/devices/pnp_PNP0c02_1
  Unique ID: ntp4.B+yZ9Ve8gC1
  SysFS ID: /devices/pnp0/00:04
  SysFS BusID: 00:04
  Hardware Class: unknown
  Model: "Unclassified device"
  SubVendor: PNP "PnP"
  SubDevice: eisa 0x0c02 
  Config Status: cfg=new, avail=yes, need=no, active=unknown

42: ISA(PnP) 00.0: 0000 Unclassified device
  [Created at isapnp.142]
  UDI: /org/freedesktop/Hal/devices/pnp_PNP0200
  Unique ID: E349.ld94kxNGZf5
  SysFS ID: /devices/pnp0/00:05
  SysFS BusID: 00:05
  Hardware Class: unknown
  Model: "Unclassified device"
  SubVendor: PNP "PnP"
  SubDevice: eisa 0x0200 
  Config Status: cfg=new, avail=yes, need=no, active=unknown

43: ISA(PnP) 00.0: 0000 Unclassified device
  [Created at isapnp.142]
  UDI: /org/freedesktop/Hal/devices/pnp_PNP0800
  Unique ID: hEKD.bvKf3UMzZfE
  SysFS ID: /devices/pnp0/00:06
  SysFS BusID: 00:06
  Hardware Class: unknown
  Model: "Unclassified device"
  SubVendor: PNP "PnP"
  SubDevice: eisa 0x0800 
  Config Status: cfg=new, avail=yes, need=no, active=unknown

44: ISA(PnP) 00.0: 0000 Unclassified device
  [Created at isapnp.142]
  UDI: /org/freedesktop/Hal/devices/pnp_PNP0b00
  Unique ID: NhVi.WYwRElrJa93
  SysFS ID: /devices/pnp0/00:07
  SysFS BusID: 00:07
  Hardware Class: unknown
  Model: "Unclassified device"
  SubVendor: PNP "PnP"
  SubDevice: eisa 0x0b00 
  Config Status: cfg=new, avail=yes, need=no, active=unknown

45: ISA(PnP) 00.0: 0000 Unclassified device
  [Created at isapnp.142]
  UDI: /org/freedesktop/Hal/devices/pnp_PNP0c04
  Unique ID: qslm.DE8RM9cWQQ8
  SysFS ID: /devices/pnp0/00:08
  SysFS BusID: 00:08
  Hardware Class: unknown
  Model: "Unclassified device"
  SubVendor: PNP "PnP"
  SubDevice: eisa 0x0c04 
  Config Status: cfg=new, avail=yes, need=no, active=unknown

46: ISA(PnP) 00.0: 0000 Unclassified device
  [Created at isapnp.142]
  UDI: /org/freedesktop/Hal/devices/pnp_PNP0303
  Unique ID: H20r.xhndlW9HXJ7
  SysFS ID: /devices/pnp0/00:09
  SysFS BusID: 00:09
  Hardware Class: unknown
  Model: "Unclassified device"
  SubVendor: PNP "PnP"
  SubDevice: eisa 0x0303 
  Config Status: cfg=new, avail=yes, need=no, active=unknown

47: ISA(PnP) 00.0: 0000 Unclassified device
  [Created at isapnp.142]
  UDI: /org/freedesktop/Hal/devices/pnp_SYN013b
  Unique ID: iT2w.zeph4bkcMgD
  SysFS ID: /devices/pnp0/00:0a
  SysFS BusID: 00:0a
  Hardware Class: unknown
  Model: "Unclassified device"
  SubVendor: SYN 
  SubDevice: eisa 0x013b 
  Config Status: cfg=new, avail=yes, need=no, active=unknown

48: ISA(PnP) 00.0: 0000 Unclassified device
  [Created at isapnp.142]
  UDI: /org/freedesktop/Hal/devices/pnp_PNP0c01
  Unique ID: 9fI_.gNN83gfynbD
  SysFS ID: /devices/pnp0/00:0b
  SysFS BusID: 00:0b
  Hardware Class: unknown
  Model: "Unclassified device"
  SubVendor: PNP "PnP"
  SubDevice: eisa 0x0c01 
  Config Status: cfg=new, avail=yes, need=no, active=unknown

49: SCSI 00.0: 10602 CD-ROM (DVD)
  [Created at block.247]
  UDI: /org/freedesktop/Hal/devices/storage_serial_TSSTcorp_CDDVDW_TS_L632N
  Unique ID: KD9E.efi45GMc8N7
  Parent ID: H0_h.tnXewr65wmE
  SysFS ID: /class/block/sr0
  SysFS BusID: 0:0:0:0
  SysFS Device Link: /devices/pci0000:00/0000:00:06.0/host0/target0:0:0/0:0:0:0
  Hardware Class: cdrom
  Model: "TSSTcorp CDDVDW TS-L632N"
  Vendor: "TSSTcorp"
  Device: "CDDVDW TS-L632N"
  Revision: "0503"
  Driver: "pata_amd", "sr"
  Driver Modules: "pata_amd"
  Device File: /dev/sr0 (/dev/sg0)
  Device Files: /dev/sr0, /dev/scd0, /dev/disk/by-id/ata-TSSTcorp_CDDVDW_TS-L632N, /dev/disk/by-path/pci-0000:00:06.0-scsi-0:0:0:0, /dev/cdrom, /dev/cdrw, /dev/dvd, /dev/dvdrw
  Device Number: block 11:0 (char 21:0)
  Features: CD-R, CD-RW, DVD, DVD-R, DVD-RW, DVD+R, DVD+RW, DVD+DL, DVDRAM
  Drive status: no medium
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #20 (IDE interface)
  Drive Speed: 24

50: IDE 200.0: 10600 Disk
  [Created at block.243]
  UDI: /org/freedesktop/Hal/devices/storage_serial_SAMSUNG_HM160HI_S18PJDNQ506588
  Unique ID: 3OOL.YUsbScIQ6L5
  Parent ID: WL76.32+uULFatWA
  SysFS ID: /class/block/sda
  SysFS BusID: 2:0:0:0
  SysFS Device Link: /devices/pci0000:00/0000:00:09.0/host2/target2:0:0/2:0:0:0
  Hardware Class: disk
  Model: "SAMSUNG HM160HI"
  Vendor: "SAMSUNG"
  Device: "HM160HI"
  Revision: "HH10"
  Driver: "ahci", "sd"
  Driver Modules: "ahci"
  Device File: /dev/sda
  Device Files: /dev/sda, /dev/disk/by-id/ata-SAMSUNG_HM160HI_S18PJDNQ506588, /dev/disk/by-id/scsi-SATA_SAMSUNG_HM160HIS18PJDNQ506588, /dev/disk/by-path/pci-0000:00:09.0-scsi-0:0:0:0, /dev/disk/by-id/wwn-0x50f00000e1506588
  Device Number: block 8:0-8:15
  Drive status: no medium
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #23 (IDE interface)

51: None 00.0: 11300 Partition
  [Created at block.412]
  UDI: /org/freedesktop/Hal/devices/volume_uuid_84e2594c_9753_4f69_8a20_584d6e60a569
  Unique ID: bdUI.SE1wIdpsiiC
  Parent ID: 3OOL.YUsbScIQ6L5
  SysFS ID: /class/block/sda/sda1
  Hardware Class: partition
  Model: "Partition"
  Device File: /dev/sda1
  Device Files: /dev/sda1, /dev/disk/by-id/ata-SAMSUNG_HM160HI_S18PJDNQ506588-part1, /dev/disk/by-id/scsi-SATA_SAMSUNG_HM160HIS18PJDNQ506588-part1, /dev/disk/by-path/pci-0000:00:09.0-scsi-0:0:0:0-part1, /dev/disk/by-uuid/84e2594c-9753-4f69-8a20-584d6e60a569, /dev/disk/by-id/wwn-0x50f00000e1506588-part1, /dev/root
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #50 (Disk)

52: None 00.0: 11300 Partition
  [Created at block.412]
  UDI: /org/freedesktop/Hal/devices/volume_part2_size_1024
  Unique ID: 2pkM.SE1wIdpsiiC
  Parent ID: 3OOL.YUsbScIQ6L5
  SysFS ID: /class/block/sda/sda2
  Hardware Class: partition
  Model: "Partition"
  Device File: /dev/sda2
  Device Files: /dev/sda2, /dev/disk/by-id/ata-SAMSUNG_HM160HI_S18PJDNQ506588-part2, /dev/disk/by-id/scsi-SATA_SAMSUNG_HM160HIS18PJDNQ506588-part2, /dev/disk/by-path/pci-0000:00:09.0-scsi-0:0:0:0-part2, /dev/disk/by-id/wwn-0x50f00000e1506588-part2
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #50 (Disk)

53: None 00.0: 11300 Partition
  [Created at block.412]
  UDI: /org/freedesktop/Hal/devices/volume_uuid_564b5473_3a78_4af3_8bb8_6e96f3420944
  Unique ID: QLVZ.SE1wIdpsiiC
  Parent ID: 3OOL.YUsbScIQ6L5
  SysFS ID: /class/block/sda/sda5
  Hardware Class: partition
  Model: "Partition"
  Device File: /dev/sda5
  Device Files: /dev/sda5, /dev/disk/by-id/ata-SAMSUNG_HM160HI_S18PJDNQ506588-part5, /dev/disk/by-id/scsi-SATA_SAMSUNG_HM160HIS18PJDNQ506588-part5, /dev/disk/by-path/pci-0000:00:09.0-scsi-0:0:0:0-part5, /dev/disk/by-uuid/564b5473-3a78-4af3-8bb8-6e96f3420944, /dev/disk/by-id/wwn-0x50f00000e1506588-part5
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #50 (Disk)

54: None 00.0: 10600 Disk
  [Created at block.243]
  UDI: /org/freedesktop/Hal/devices/storage_serial_0xb1cf91ec
  Unique ID: HAKk.Fxp0d3BezAE
  Parent ID: RxpL.1Jezk9TGFRF
  SysFS ID: /class/block/mmcblk0
  SysFS BusID: mmc0:0002
  SysFS Device Link: /devices/pci0000:00/0000:00:08.0/0000:02:05.1/mmc_host/mmc0/mmc0:0002
  Hardware Class: disk
  Model: "Disk"
  Driver: "sdhci-pci", "mmcblk"
  Driver Modules: "sdhci_pci"
  Device File: /dev/mmcblk0
  Device Files: /dev/mmcblk0, /dev/disk/by-id/mmc-00000_0xb1cf91ec, /dev/disk/by-path/pci-0000:02:05.1
  Device Number: block 179:0-179:7
  Features: Hotpluggable
  Drive status: no medium
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #33 (SD Host controller)

55: None 00.0: 11300 Partition
  [Created at block.412]
  UDI: /org/freedesktop/Hal/devices/volume_uuid_E0FD_1813
  Unique ID: l7UW.SE1wIdpsiiC
  Parent ID: HAKk.Fxp0d3BezAE
  SysFS ID: /class/block/mmcblk0/mmcblk0p1
  Hardware Class: partition
  Model: "Partition"
  Device File: /dev/mmcblk0p1
  Device Files: /dev/mmcblk0p1, /dev/disk/by-id/mmc-00000_0xb1cf91ec-part1, /dev/disk/by-path/pci-0000:02:05.1-part1, /dev/disk/by-uuid/E0FD-1813
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #54 (Disk)

56: USB 00.0: 10a00 Hub
  [Created at usb.122]
  UDI: /org/freedesktop/Hal/devices/usb_device_1d6b_2_0000_00_02_1_if0
  Unique ID: k4bc.OqydEZZ981A
  Parent ID: ruGf.Q2YEkqhxk71
  SysFS ID: /devices/pci0000:00/0000:00:02.1/usb1/1-0:1.0
  SysFS BusID: 1-0:1.0
  Hardware Class: hub
  Model: "Linux 2.6.38-8-generic-pae ehci_hcd EHCI Host Controller"
  Hotplug: USB
  Vendor: usb 0x1d6b "Linux 2.6.38-8-generic-pae ehci_hcd"
  Device: usb 0x0002 "EHCI Host Controller"
  Revision: "2.06"
  Serial ID: "0000:00:02.1"
  Driver: "hub"
  Driver Modules: "usbcore"
  Speed: 480 Mbps
  Module Alias: "usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00"
  Driver Info #0:
    Driver Status: option is not active
    Driver Activation Cmd: "modprobe option"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #17 (USB Controller)

57: USB 00.0: 10a00 Hub
  [Created at usb.122]
  UDI: /org/freedesktop/Hal/devices/usb_device_1d6b_2_0000_00_04_1_if0
  Unique ID: pBe4.QtYiGM_hXFF
  Parent ID: +6Nb.Q2YEkqhxk71
  SysFS ID: /devices/pci0000:00/0000:00:04.1/usb2/2-0:1.0
  SysFS BusID: 2-0:1.0
  Hardware Class: hub
  Model: "Linux 2.6.38-8-generic-pae ehci_hcd EHCI Host Controller"
  Hotplug: USB
  Vendor: usb 0x1d6b "Linux 2.6.38-8-generic-pae ehci_hcd"
  Device: usb 0x0002 "EHCI Host Controller"
  Revision: "2.06"
  Serial ID: "0000:00:04.1"
  Driver: "hub"
  Driver Modules: "usbcore"
  Speed: 480 Mbps
  Module Alias: "usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00"
  Driver Info #0:
    Driver Status: option is not active
    Driver Activation Cmd: "modprobe option"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #19 (USB Controller)

58: USB 00.0: 10a00 Hub
  [Created at usb.122]
  UDI: /org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_02_0_if0
  Unique ID: uIhY.kllrQr_lFX9
  Parent ID: _Znp.fdoO6mi4bbA
  SysFS ID: /devices/pci0000:00/0000:00:02.0/usb3/3-0:1.0
  SysFS BusID: 3-0:1.0
  Hardware Class: hub
  Model: "Linux 2.6.38-8-generic-pae ohci_hcd OHCI Host Controller"
  Hotplug: USB
  Vendor: usb 0x1d6b "Linux 2.6.38-8-generic-pae ohci_hcd"
  Device: usb 0x0001 "OHCI Host Controller"
  Revision: "2.06"
  Serial ID: "0000:00:02.0"
  Driver: "hub"
  Driver Modules: "usbcore"
  Speed: 12 Mbps
  Module Alias: "usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #16 (USB Controller)

59: USB 00.0: 10a00 Hub
  [Created at usb.122]
  UDI: /org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_04_0_if0
  Unique ID: zPk0.moLwSePIflE
  Parent ID: 8otl.fdoO6mi4bbA
  SysFS ID: /devices/pci0000:00/0000:00:04.0/usb4/4-0:1.0
  SysFS BusID: 4-0:1.0
  Hardware Class: hub
  Model: "Linux 2.6.38-8-generic-pae ohci_hcd OHCI Host Controller"
  Hotplug: USB
  Vendor: usb 0x1d6b "Linux 2.6.38-8-generic-pae ohci_hcd"
  Device: usb 0x0001 "OHCI Host Controller"
  Revision: "2.06"
  Serial ID: "0000:00:04.0"
  Driver: "hub"
  Driver Modules: "usbcore"
  Speed: 12 Mbps
  Module Alias: "usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #18 (USB Controller)

60: PS/2 00.0: 10800 Keyboard
  [Created at input.161]
  UDI: /org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port_logicaldev_input
  Unique ID: c3zD.+49ps10DtUF
  Hardware Class: keyboard
  Model: "AT Translated Set 2 keyboard"
  Vendor: 0x0001 
  Device: 0x0001 "AT Translated Set 2 keyboard"
  Compatible to: int 0x0211 0x0001
  Device File: /dev/input/event4
  Device Files: /dev/input/event4, /dev/input/by-path/platform-i8042-serio-0-event-kbd
  Device Number: char 13:68
  Driver Info #0:
    XkbRules: xfree86
    XkbModel: pc104
  Config Status: cfg=new, avail=yes, need=no, active=unknown

61: PS/2 00.0: 10500 PS/2 Mouse
  [Created at input.183]
  UDI: /org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port_logicaldev_input
  Unique ID: AH6Q.ZHI3OT7LsxA
  Hardware Class: mouse
  Model: "SynPS/2 Synaptics TouchPad"
  Vendor: 0x0002 
  Device: 0x0007 "SynPS/2 Synaptics TouchPad"
  Compatible to: int 0x0210 0x0002
  Device File: /dev/input/mice (/dev/input/mouse0)
  Device Files: /dev/input/mice, /dev/input/mouse0, /dev/input/event7, /dev/input/by-path/platform-i8042-serio-1-event-mouse, /dev/input/by-path/platform-i8042-serio-1-mouse
  Device Number: char 13:63 (char 13:32)
  Driver Info #0:
    Buttons: 2
    Wheels: 0
    XFree86 Protocol: explorerps/2
    GPM Protocol: exps2
  Config Status: cfg=new, avail=yes, need=no, active=unknown

62: None 00.0: 10103 CPU
  [Created at cpu.304]
  Unique ID: rdCR.j8NaKXDZtZ6
  Hardware Class: cpu
  Arch: Intel
  Vendor: "AuthenticAMD"
  Model: 15.104.2 "AMD Turion(tm) 64 X2 Mobile Technology TL-60"
  Features: fpu,vme,de,pse,tsc,msr,pae,mce,cx8,apic,sep,mtrr,pge,mca,cmov,pat,pse36,clflush,mmx,fxsr,sse,sse2,ht,syscall,nx,mmxext,fxsr_opt,rdtscp,lm,3dnowext,3dnow,extd_apicid,pni,cx16,lahf_lm,cmp_legacy,svm,extapic,cr8_legacy,3dnowprefetch,lbrv
  Clock: 1600 MHz
  BogoMips: 3200.08
  Cache: 512 kb
  Units/Processor: 2
  Config Status: cfg=new, avail=yes, need=no, active=unknown

63: None 01.0: 10103 CPU
  [Created at cpu.304]
  Unique ID: wkFv.j8NaKXDZtZ6
  Hardware Class: cpu
  Arch: Intel
  Vendor: "AuthenticAMD"
  Model: 15.104.2 "AMD Turion(tm) 64 X2 Mobile Technology TL-60"
  Features: fpu,vme,de,pse,tsc,msr,pae,mce,cx8,apic,sep,mtrr,pge,mca,cmov,pat,pse36,clflush,mmx,fxsr,sse,sse2,ht,syscall,nx,mmxext,fxsr_opt,rdtscp,lm,3dnowext,3dnow,extd_apicid,pni,cx16,lahf_lm,cmp_legacy,svm,extapic,cr8_legacy,3dnowprefetch,lbrv
  Clock: 1600 MHz
  BogoMips: 3200.08
  Cache: 512 kb
  Units/Processor: 2
  Config Status: cfg=new, avail=yes, need=no, active=unknown

64: None 00.0: 10700 Loopback
  [Created at net.124]
  Unique ID: ZsBS.GQNx7L4uPNA
  SysFS ID: /class/net/lo
  Hardware Class: network interface
  Model: "Loopback network interface"
  Device File: lo
  Link detected: yes
  Config Status: cfg=new, avail=yes, need=no, active=unknown

65: None 00.0: 10701 Ethernet
  [Created at net.124]
  Unique ID: usDW.ndpeucax6V1
  Parent ID: rBUF.Qh8YuQ9wg77
  SysFS ID: /class/net/eth0
  SysFS Device Link: /devices/pci0000:00/0000:00:0a.0
  Hardware Class: network interface
  Model: "Ethernet network interface"
  Driver: "forcedeth"
  Driver Modules: "forcedeth"
  Device File: eth0
  HW Address: 00:1e:68:7f:2c:8b
  Link detected: no
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #24 (Ethernet controller)

66: None 00.0: 1070a WLAN
  [Created at net.124]
  Unique ID: AYEt.QXn1l67RSa1
  Parent ID: y9sn.9AnOduZyIOF
  SysFS ID: /class/net/wlan0
  SysFS Device Link: /devices/pci0000:00/0000:00:0d.0/0000:03:00.0
  Hardware Class: network interface
  Model: "WLAN network interface"
  Driver: "ath5k"
  Driver Modules: "ath5k"
  Device File: wlan0
  HW Address: 00:1f:e2:ca:20:77
  Link detected: yes
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #36 (WLAN controller)


I have no other OS. The laptop came with Windows installed of course and for a while I was dual booting into Ubuntu but made the switch permanently some time ago. I'm running 11.04 if that's at all relevant.
I also really appreciate the help, thank you.

---

### Post by webofunni on 2011-05-30
upload the hwinfo also. Also put the data in code tag.

---

### Post by webofunni on 2011-05-30
There should be more. do

```
sudo hwinfo > hwinfo.txt
```

and attach the file.

---

### Post by port_launay on 2011-05-30
> **webofunni said:**
> upload the hwinfo also. Also put the data in code tag.

Changed terminal window to scroll back unlimited lines so this might be what you need;

```
jeff@jeff-HP-Pavilion-dv9700-Notebook-PC:~$ hwinfo
============ start debug info ============                      
libhd version 16.0u (ia32)
using /var/lib/hardware
kernel version is 2.6
----- /proc/cmdline -----
  BOOT_IMAGE=/boot/vmlinuz-2.6.38-8-generic-pae root=UUID=84e2594c-9753-4f69-8a20-584d6e60a569 ro quiet splash vt.handoff=7
----- /proc/cmdline end -----
debug = 0xff7ffff7
probe = 0x00138fc4aa17fcf9fffe (+memory +pci +isapnp +net +floppy +misc +misc.serial +misc.par +misc.floppy +serial +cpu +bios +monitor +mouse +scsi +usb -usb.mods +modem +modem.usb +parallel +parallel.lp +parallel.zip -isa -isa.isdn +isdn +kbd +prom +sbus +int +braille +braille.alva +braille.fhp +braille.ht -ignx11 +sys -bios.vbe -isapnp.old -isapnp.new -isapnp.mod +braille.baum -manual +fb +pppoe -scan +pcmcia -fork -parallel.imm +s390 -cpuemu -sysfs -s390disks +udev +block +block.cdrom +block.part +edd +edd.mod -bios.ddc -bios.fb -bios.mode +input +block.mods +bios.vesa -cpuemu.debug -scsi.noserial +wlan -bios.crc -hal -bios.vram -bios.acpi -bios.ddc.ports -modules.pata -net.eeprom -x86emu -max -lxrc)
shm: attached segment 56164417 at 0xb7454000
>> hal.1: read hal data
  hal: connected to: :1.185
----- hal device list -----
  0: udi = '/org/freedesktop/Hal/devices/volume_uuid_564b5473_3a78_4af3_8bb8_6e96f3420944'
  info.category = 'volume'
  volume.partition.media_size = 160041885696ull (0x25433d6000ull)
  linux.hotplug_type = 3 (0x3)
  volume.fstype = 'swap'
  volume.fsusage = 'other'
  volume.fsversion = '2'
  volume.uuid = '564b5473-3a78-4af3-8bb8-6e96f3420944'
  volume.label = ''
  volume.mount_point = ''
  volume.is_mounted = false
  volume.is_mounted_read_only = false
  volume.linux.is_device_mapper = false
  volume.is_disc = false
  volume.is_partition = true
  volume.partition.number = 5 (0x5)
  volume.block_size = 512 (0x200)
  volume.num_blocks = 12769280ull (0xc2d800ull)
  volume.size = 6537871360ull (0x185b00000ull)
  info.product = 'Volume (swap)'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:09.0/host2/target2:0:0/2:0:0:0/block/sda/sda5'
  info.parent = '/org/freedesktop/Hal/devices/storage_serial_SAMSUNG_HM160HI_S18PJDNQ506588'
  block.minor = 5 (0x5)
  block.is_volume = true
  block.major = 8 (0x8)
  info.capabilities = { 'volume', 'block' }
  block.device = '/dev/sda5'
  volume.partition.start = 153503137792ull (0x23bd800000ull)
  block.storage_device = '/org/freedesktop/Hal/devices/storage_serial_SAMSUNG_HM160HI_S18PJDNQ506588'
  info.udi = '/org/freedesktop/Hal/devices/volume_uuid_564b5473_3a78_4af3_8bb8_6e96f3420944'

  1: udi = '/org/freedesktop/Hal/devices/pci_10de_55c_sound_card_0_logicaldev_input'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'input'
  info.udi = '/org/freedesktop/Hal/devices/pci_10de_55c_sound_card_0_logicaldev_input'
  info.subsystem = 'input'
  info.product = 'HDA NVidia Headphone'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:07.0/sound/card0/input8/event8'
  input.originating_device = '/org/freedesktop/Hal/devices/pci_10de_55c_sound_card_0'
  info.parent = '/org/freedesktop/Hal/devices/pci_10de_55c_sound_card_0'
  info.category = 'input'
  info.capabilities = { 'input', 'input.switch', 'button' }
  input.device = '/dev/input/event8'
  input.product = 'HDA NVidia Headphone'
  button.has_state = true
  button.type = 'headphone_insert'
  button.state.value = false
  linux.device_file = '/dev/input/event8'
  info.addons.singleton = { 'hald-addon-input' }

  2: udi = '/org/freedesktop/Hal/devices/volume_part2_size_1024'
  volume.partition.scheme = 'mbr'
  volume.partition.type = '0x05'
  volume.partition.label = ''
  linux.hotplug_type = 3 (0x3)
  volume.partition.uuid = ''
  volume.partition.flags = {  }
  volume.partition.start = 153503136768ull (0x23bd7ffc00ull)
  info.product = 'Volume'
  info.udi = '/org/freedesktop/Hal/devices/volume_part2_size_1024'
  block.storage_device = '/org/freedesktop/Hal/devices/storage_serial_SAMSUNG_HM160HI_S18PJDNQ506588'
  volume.fstype = ''
  volume.fsusage = 'partitiontable'
  volume.fsversion = ''
  volume.uuid = ''
  volume.label = ''
  volume.mount_point = ''
  volume.is_mounted = false
  volume.is_mounted_read_only = false
  volume.linux.is_device_mapper = false
  volume.is_disc = false
  volume.is_partition = true
  volume.partition.number = 2 (0x2)
  volume.block_size = 512 (0x200)
  volume.num_blocks = 2ull (0x2ull)
  volume.size = 1024ull (0x400ull)
  info.parent = '/org/freedesktop/Hal/devices/storage_serial_SAMSUNG_HM160HI_S18PJDNQ506588'
  volume.partition.media_size = 160041885696ull (0x25433d6000ull)
  info.category = 'volume'
  block.minor = 2 (0x2)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:09.0/host2/target2:0:0/2:0:0:0/block/sda/sda2'
  block.is_volume = true
  block.major = 8 (0x8)
  info.capabilities = { 'volume', 'block' }
  block.device = '/dev/sda2'

  3: udi = '/org/freedesktop/Hal/devices/volume_uuid_84e2594c_9753_4f69_8a20_584d6e60a569'
  volume.unmount.valid_options = { 'lazy' }
  org.freedesktop.Hal.Device.Volume.method_execpaths = { 'hal-storage-mount', 'hal-storage-unmount', 'hal-storage-eject' }
  org.freedesktop.Hal.Device.Volume.method_names = { 'Mount', 'Unmount', 'Eject' }
  org.freedesktop.Hal.Device.Volume.method_signatures = { 'ssas', 'as', 'as' }
  linux.hotplug_type = 3 (0x3)
  volume.mount.valid_options = { 'ro', 'sync', 'dirsync', 'noatime', 'nodiratime', 'relatime', 'noexec', 'quiet', 'remount', 'exec' }
  volume.partition.start = 1048576ull (0x100000ull)
  info.product = 'Volume (ext4)'
  info.udi = '/org/freedesktop/Hal/devices/volume_uuid_84e2594c_9753_4f69_8a20_584d6e60a569'
  block.storage_device = '/org/freedesktop/Hal/devices/storage_serial_SAMSUNG_HM160HI_S18PJDNQ506588'
  info.interfaces = { 'org.freedesktop.Hal.Device.Volume' }
  volume.fstype = 'ext4'
  volume.fsusage = 'filesystem'
  volume.fsversion = '1.0'
  volume.uuid = '84e2594c-9753-4f69-8a20-584d6e60a569'
  volume.label = ''
  volume.mount_point = '/'
  volume.is_mounted = true
  volume.is_mounted_read_only = false
  volume.linux.is_device_mapper = false
  volume.is_disc = false
  volume.is_partition = true
  volume.partition.number = 1 (0x1)
  volume.block_size = 512 (0x200)
  volume.num_blocks = 299806720ull (0x11deb000ull)
  volume.size = 153501040640ull (0x23bd600000ull)
  info.parent = '/org/freedesktop/Hal/devices/storage_serial_SAMSUNG_HM160HI_S18PJDNQ506588'
  volume.partition.media_size = 160041885696ull (0x25433d6000ull)
  info.category = 'volume'
  block.minor = 1 (0x1)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:09.0/host2/target2:0:0/2:0:0:0/block/sda/sda1'
  volume.ignore = false
  block.is_volume = true
  block.major = 8 (0x8)
  org.freedesktop.Hal.Device.Volume.method_argnames = { 'mount_point fstype extra_options', 'extra_options', 'extra_options' }
  info.capabilities = { 'volume', 'block' }
  block.device = '/dev/sda1'

  4: udi = '/org/freedesktop/Hal/devices/computer_logicaldev_input_4'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'input'
  info.subsystem = 'input'
  info.product = 'Lid Switch'
  linux.sysfs_path = '/sys/devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1/event1'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  input.device = '/dev/input/event1'
  info.category = 'input'
  info.capabilities = { 'input', 'input.switch', 'button' }
  button.has_state = true
  input.product = 'Lid Switch'
  linux.device_file = '/dev/input/event1'
  button.type = 'lid'
  button.state.value = false
  info.udi = '/org/freedesktop/Hal/devices/computer_logicaldev_input_4'
  info.addons.singleton = { 'hald-addon-input' }

  5: udi = '/org/freedesktop/Hal/devices/storage_serial_SAMSUNG_HM160HI_S18PJDNQ506588'
  storage.drive_type = 'disk'
  info.vendor = 'ATA'
  storage.vendor = 'ATA'
  storage.serial = 'SAMSUNG_HM160HI_S18PJDNQ506588'
  storage.firmware_version = 'HH100-21'
  linux.hotplug_type = 3 (0x3)
  storage.originating_device = '/org/freedesktop/Hal/devices/computer'
  storage.removable.media_available = true
  storage.lun = 0 (0x0)
  storage.removable = false
  storage.size = 160041885696ull (0x25433d6000ull)
  storage.hotpluggable = false
  storage.requires_eject = false
  storage.model = 'SAMSUNG HM160HI'
  info.product = 'SAMSUNG HM160HI'
  info.udi = '/org/freedesktop/Hal/devices/storage_serial_SAMSUNG_HM160HI_S18PJDNQ506588'
  storage.removable.media_size = 160041885696ull (0x25433d6000ull)
  storage.partitioning_scheme = 'mbr'
  block.storage_device = '/org/freedesktop/Hal/devices/storage_serial_SAMSUNG_HM160HI_S18PJDNQ506588'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:09.0/host2/target2:0:0/2:0:0:0/block/sda'
  info.parent = '/org/freedesktop/Hal/devices/pci_10de_550_scsi_host_scsi_device_lun0'
  block.device = '/dev/sda'
  block.major = 8 (0x8)
  info.category = 'storage'
  info.capabilities = { 'storage', 'block' }
  block.is_volume = false
  block.minor = 0 (0x0)
  storage.media_check_enabled = false
  storage.bus = 'pci'
  storage.no_partitions_hint = false
  storage.automount_enabled_hint = true

  6: udi = '/org/freedesktop/Hal/devices/computer'
  org.freedesktop.Hal.Device.SystemPowerManagement.method_names = { 'Suspend', 'SuspendHybrid', 'Hibernate', 'Shutdown', 'Reboot', 'SetPowerSave' }
  org.freedesktop.Hal.Device.SystemPowerManagement.method_signatures = { 'i', 'i', '', '', '', 'b' }
  org.freedesktop.Hal.Device.SystemPowerManagement.method_argnames = { 'num_seconds_to_sleep', 'num_seconds_to_sleep', '', '', '', 'enable_power_save' }
  org.freedesktop.Hal.Device.SystemPowerManagement.method_execpaths = { 'hal-system-power-suspend', 'hal-system-power-suspend-hybrid', 'hal-system-power-hibernate', 'hal-system-power-shutdown', 'hal-system-power-reboot', 'hal-system-power-set-power-save' }
  power_management.is_powersave_set = false
  info.callouts.add = { 'hal-storage-cleanup-all-mountpoints' }
  info.subsystem = 'unknown'
  info.product = 'Computer'
  info.udi = '/org/freedesktop/Hal/devices/computer'
  org.freedesktop.Hal.version = '0.5.14'
  org.freedesktop.Hal.version.major = 0 (0x0)
  org.freedesktop.Hal.version.minor = 5 (0x5)
  org.freedesktop.Hal.version.micro = 14 (0xe)
  system.kernel.name = 'Linux'
  system.kernel.version = '2.6.38-8-generic-pae'
  system.kernel.version.major = 2 (0x2)
  system.kernel.version.minor = 6 (0x6)
  system.kernel.version.micro = 38 (0x26)
  system.kernel.machine = 'i686'
  power_management.can_suspend = true
  power_management.can_suspend_hybrid = true
  power_management.can_hibernate = true
  system.hardware.primary_video.vendor = 4318 (0x10de)
  system.hardware.primary_video.product = 1329 (0x531)
  system.hardware.serial = 'CNF8244WDL'
  system.hardware.uuid = '434E4638-3234-3457-444C-001E687F2C8B'
  system.board.serial = 'None1'
  system.firmware.vendor = 'Hewlett-Packard'
  system.firmware.version = 'F.30'
  system.firmware.release_date = '04/24/2008'
  system.hardware.vendor = 'Hewlett-Packard'
  system.hardware.product = 'HP Pavilion dv9700 Notebook PC'
  system.hardware.version = 'Rev 1'
  system.chassis.manufacturer = 'Quanta'
  system.board.product = '30D1'
  system.board.version = '85.26'
  system.board.vendor = 'Quanta'
  system.chassis.type = 'Notebook'
  system.formfactor = 'laptop'
  info.addons = { 'hald-addon-cpufreq', 'hald-addon-acpi' }
  power_management.type = 'acpi'
  power_management.acpi.linux.version = '20110112'
  info.capabilities = { 'cpufreq_control' }
  power_management.quirk.none = true
  info.interfaces = { 'org.freedesktop.Hal.Device.SystemPowerManagement', 'org.freedesktop.Hal.Device.CPUFreq' }

  7: udi = '/org/freedesktop/Hal/devices/storage_serial_TSSTcorp_CDDVDW_TS_L632N'
  storage.removable = true
  storage.removable.support_async_notification = false
  storage.hotpluggable = false
  storage.requires_eject = true
  storage.no_partitions_hint = true
  storage.automount_enabled_hint = true
  info.interfaces = { 'org.freedesktop.Hal.Device.Storage', 'org.freedesktop.Hal.Device.Storage', 'org.freedesktop.Hal.Device.Storage.Removable' }
  info.addons = { 'hald-addon-storage' }
  info.category = 'storage'
  info.capabilities = { 'storage', 'block', 'storage.cdrom' }
  storage.cdrom.cdr = true
  storage.cdrom.cdrw = true
  storage.cdrom.dvd = true
  storage.cdrom.dvdr = true
  storage.cdrom.dvdrw = true
  storage.cdrom.dvdrdl = true
  storage.cdrom.dvdram = true
  storage.cdrom.dvdplusr = true
  storage.cdrom.dvdplusrw = true
  storage.cdrom.dvdplusrwdl = false
  storage.cdrom.dvdplusrdl = true
  storage.cdrom.bd = false
  storage.cdrom.bdr = false
  storage.cdrom.bdre = false
  storage.cdrom.hddvd = false
  storage.cdrom.hddvdr = false
  storage.cdrom.hddvdrw = false
  storage.cdrom.mo = false
  storage.cdrom.mrw = true
  storage.cdrom.mrw_w = true
  storage.cdrom.support_media_changed = true
  storage.cdrom.support_multisession = true
  storage.cdrom.read_speed = 4234 (0x108a)
  info.product = 'CDDVDW TS-L632N'
  storage.cdrom.write_speed = 0 (0x0)
  storage.cdrom.write_speeds = {  }
  storage.partitioning_scheme = ''
  info.udi = '/org/freedesktop/Hal/devices/storage_serial_TSSTcorp_CDDVDW_TS_L632N'
  block.storage_device = '/org/freedesktop/Hal/devices/storage_serial_TSSTcorp_CDDVDW_TS_L632N'
  org.freedesktop.Hal.Device.Storage.method_names = { 'Eject', 'CloseTray' }
  org.freedesktop.Hal.Device.Storage.method_argnames = { 'extra_options', 'extra_options' }
  org.freedesktop.Hal.Device.Storage.method_execpaths = { 'hal-storage-eject', 'hal-storage-closetray' }
  org.freedesktop.Hal.Device.Storage.method_signatures = { 'as', 'as' }
  block.device = '/dev/sr0'
  block.major = 11 (0xb)
  block.minor = 0 (0x0)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:06.0/host0/target0:0:0/0:0:0:0/block/sr0'
  info.parent = '/org/freedesktop/Hal/devices/pci_10de_560_scsi_host_scsi_device_lun0'
  storage.bus = 'pci'
  block.is_volume = false
  storage.media_check_enabled = true
  storage.drive_type = 'cdrom'
  storage.model = 'CDDVDW TS-L632N'
  storage.vendor = 'TSSTcorp'
  storage.serial = 'TSSTcorp_CDDVDW_TS-L632N'
  storage.firmware_version = '0503'
  storage.lun = 0 (0x0)
  info.vendor = 'TSSTcorp'
  storage.originating_device = '/org/freedesktop/Hal/devices/computer'
  storage.removable.media_available = false
  linux.hotplug_type = 3 (0x3)
  storage.size = 0ull (0x0ull)

  8: udi = '/org/freedesktop/Hal/devices/computer_alsa_timer'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'sound'
  alsa.device_file = '/dev/snd/timer'
  alsa.type = 'timer'
  info.subsystem = 'sound'
  info.product = 'ALSA Timer Device'
  linux.sysfs_path = '/sys/devices/virtual/sound/timer'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  info.category = 'alsa'
  info.capabilities = { 'alsa' }
  info.udi = '/org/freedesktop/Hal/devices/computer_alsa_timer'
  linux.device_file = '/dev/snd/timer'

  9: udi = '/org/freedesktop/Hal/devices/computer_alsa_sequencer'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'sound'
  alsa.device_file = '/dev/snd/seq'
  alsa.type = 'sequencer'
  info.subsystem = 'sound'
  info.product = 'ALSA Sequencer Device'
  linux.sysfs_path = '/sys/devices/virtual/sound/seq'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  info.category = 'alsa'
  info.capabilities = { 'alsa' }
  info.udi = '/org/freedesktop/Hal/devices/computer_alsa_sequencer'
  linux.device_file = '/dev/snd/seq'

  10: udi = '/org/freedesktop/Hal/devices/net_computer_loopback'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'net'
  info.udi = '/org/freedesktop/Hal/devices/net_computer_loopback'
  info.subsystem = 'net'
  info.product = 'Loopback device Interface'
  linux.sysfs_path = '/sys/devices/virtual/net/lo'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  info.category = 'net.loopback'
  info.capabilities = { 'net', 'net.loopback' }
  net.originating_device = '/org/freedesktop/Hal/devices/computer'
  net.interface = 'lo'
  net.address = '00:00:00:00:00:00'
  net.linux.ifindex = 1 (0x1)
  net.arp_proto_hw_id = 772 (0x304)

  11: udi = '/org/freedesktop/Hal/devices/computer_logicaldev_input_3'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'input'
  info.subsystem = 'input'
  info.product = 'HP WMI hotkeys'
  linux.sysfs_path = '/sys/devices/virtual/input/input5/event5'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  input.device = '/dev/input/event5'
  info.category = 'input'
  info.capabilities = { 'input', 'input.keys', 'input.switch', 'button' }
  input.product = 'HP WMI hotkeys'
  linux.device_file = '/dev/input/event5'
  info.addons.singleton = { 'hald-addon-input' }
  info.udi = '/org/freedesktop/Hal/devices/computer_logicaldev_input_3'

  12: udi = '/org/freedesktop/Hal/devices/computer_backlight'
  info.interfaces = { 'org.freedesktop.Hal.Device.LaptopPanel' }
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'backlight'
  laptop_panel.access_method = 'general'
  info.product = 'Generic Backlight Device'
  linux.sysfs_path = '/sys/devices/virtual/backlight/acpi_video0'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  laptop_panel.brightness_in_hardware = true
  info.category = 'laptop_panel'
  info.capabilities = { 'laptop_panel' }
  laptop_panel.num_levels = 11 (0xb)
  info.addons = { 'hald-addon-generic-backlight' }
  info.subsystem = 'backlight'
  info.udi = '/org/freedesktop/Hal/devices/computer_backlight'

  13: udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port_logicaldev_input'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'input'
  info.subsystem = 'input'
  info.product = 'SynPS/2 Synaptics TouchPad'
  linux.sysfs_path = '/sys/devices/platform/i8042/serio1/input/input7/event7'
  input.originating_device = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port'
  info.parent = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port'
  info.category = 'input'
  info.capabilities = { 'input', 'input.touchpad' }
  input.device = '/dev/input/event7'
  input.product = 'SynPS/2 Synaptics TouchPad'
  linux.device_file = '/dev/input/event7'
  info.udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port_logicaldev_input'

  14: udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port_logicaldev_input'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'input'
  input.keymap.data = { 'e001:fn_esc', 'e009:battery', 'e00a:screenlock', 'e00b:camera', 'e00c:media', 'e00e:dvd', 'e031:help', 'e033:f23', 'e057:wlan', 'e012:brightnessdown', 'e017:brightnessup', 'e06e:switchvideomode', 'e008:media', 'e058:f22', 'e059:f23' }
  info.subsystem = 'input'
  info.product = 'AT Translated Set 2 keyboard'
  linux.sysfs_path = '/sys/devices/platform/i8042/serio0/input/input4/event4'
  input.originating_device = '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port'
  info.parent = '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port'
  info.category = 'input'
  info.capabilities = { 'input', 'input.keyboard', 'input.keypad', 'input.keys', 'input.keymap', 'button' }
  input.device = '/dev/input/event4'
  input.product = 'AT Translated Set 2 keyboard'
  linux.device_file = '/dev/input/event4'
  info.addons.singleton = { 'hald-addon-input' }
  info.udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port_logicaldev_input'

  15: udi = '/org/freedesktop/Hal/devices/platform_hp_wmi_rfkill_hp_wifi_wlan'
  info.interfaces = { 'org.freedesktop.Hal.Device.KillSwitch' }
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'rfkill'
  killswitch.type = 'wlan'
  killswitch.state = 1 (0x1)
  killswitch.access_method = 'rfkill'
  killswitch.name = 'hp-wifi'
  info.subsystem = 'rfkill'
  info.product = 'hp-wifi wlan Killswitch'
  linux.sysfs_path = '/sys/devices/platform/hp-wmi/rfkill/rfkill0'
  info.parent = '/org/freedesktop/Hal/devices/platform_hp_wmi'
  info.category = 'killswitch'
  info.capabilities = { 'killswitch' }
  info.udi = '/org/freedesktop/Hal/devices/platform_hp_wmi_rfkill_hp_wifi_wlan'
  info.addons.singleton = { 'hald-addon-rfkill-killswitch' }

  16: udi = '/org/freedesktop/Hal/devices/net_00_1f_e2_ca_20_77'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'net'
  info.udi = '/org/freedesktop/Hal/devices/net_00_1f_e2_ca_20_77'
  net.80211.mac_address = 136948883575ull (0x1fe2ca2077ull)
  info.subsystem = 'net'
  info.product = 'WLAN Interface'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:0d.0/0000:03:00.0/net/wlan0'
  info.parent = '/org/freedesktop/Hal/devices/pci_168c_1c'
  info.category = 'net.80211'
  info.capabilities = { 'net', 'net.80211' }
  net.originating_device = '/org/freedesktop/Hal/devices/pci_168c_1c'
  net.interface = 'wlan0'
  net.address = '00:1f:e2:ca:20:77'
  net.linux.ifindex = 3 (0x3)
  net.arp_proto_hw_id = 1 (0x1)

  17: udi = '/org/freedesktop/Hal/devices/leds_ath5k_phy0_tx'
  info.interfaces = { 'org.freedesktop.Hal.Device.Leds' }
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'leds'
  leds.function = 'tx'
  keyboard_backlight.num_levels = 256 (0x100)
  info.subsystem = 'leds'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:0d.0/0000:03:00.0/leds/ath5k-phy0::tx'
  info.parent = '/org/freedesktop/Hal/devices/pci_168c_1c'
  info.category = 'leds'
  info.capabilities = { 'leds', 'keyboard_backlight' }
  leds.num_levels = 256 (0x100)
  leds.device_name = 'ath5k-phy0'
  info.addons.singleton = { 'hald-addon-leds' }
  info.udi = '/org/freedesktop/Hal/devices/leds_ath5k_phy0_tx'

  18: udi = '/org/freedesktop/Hal/devices/leds_ath5k_phy0_rx'
  info.interfaces = { 'org.freedesktop.Hal.Device.Leds' }
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'leds'
  leds.function = 'rx'
  keyboard_backlight.num_levels = 256 (0x100)
  info.subsystem = 'leds'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:0d.0/0000:03:00.0/leds/ath5k-phy0::rx'
  info.parent = '/org/freedesktop/Hal/devices/pci_168c_1c'
  info.category = 'leds'
  info.capabilities = { 'leds', 'keyboard_backlight' }
  leds.num_levels = 256 (0x100)
  leds.device_name = 'ath5k-phy0'
  info.addons.singleton = { 'hald-addon-leds' }
  info.udi = '/org/freedesktop/Hal/devices/leds_ath5k_phy0_rx'

  19: udi = '/org/freedesktop/Hal/devices/pci_168c_1c_rfkill_phy0_wlan'
  info.interfaces = { 'org.freedesktop.Hal.Device.KillSwitch' }
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'rfkill'
  killswitch.type = 'wlan'
  killswitch.state = 1 (0x1)
  killswitch.access_method = 'rfkill'
  killswitch.name = 'phy0'
  info.subsystem = 'rfkill'
  info.product = 'phy0 wlan Killswitch'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:0d.0/0000:03:00.0/ieee80211/phy0/rfkill1'
  info.parent = '/org/freedesktop/Hal/devices/pci_168c_1c'
  info.category = 'killswitch'
  info.capabilities = { 'killswitch' }
  info.udi = '/org/freedesktop/Hal/devices/pci_168c_1c_rfkill_phy0_wlan'
  info.addons.singleton = { 'hald-addon-rfkill-killswitch' }
  info.vendor = 'Atheros Communications Inc.'

  20: udi = '/org/freedesktop/Hal/devices/net_00_1e_68_7f_2c_8b'
  info.interfaces = { 'org.freedesktop.Hal.Device.WakeOnLan' }
  org.freedesktop.Hal.Device.WakeOnLan.method_names = { 'GetSupported', 'GetEnabled', 'SetEnabled' }
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'net'
  org.freedesktop.Hal.Device.WakeOnLan.method_argnames = { '', '', 'enable' }
  org.freedesktop.Hal.Device.WakeOnLan.method_signatures = { '', '', 'b' }
  org.freedesktop.Hal.Device.WakeOnLan.method_execpaths = { 'hal-system-wol-supported', 'hal-system-wol-enabled', 'hal-system-wol-enable' }
  info.udi = '/org/freedesktop/Hal/devices/net_00_1e_68_7f_2c_8b'
  info.subsystem = 'net'
  info.product = 'Networking Interface'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:0a.0/net/eth0'
  info.parent = '/org/freedesktop/Hal/devices/pci_10de_54c'
  info.category = 'net.80203'
  info.capabilities = { 'net', 'net.80203', 'wake_on_lan' }
  net.originating_device = '/org/freedesktop/Hal/devices/pci_10de_54c'
  net.interface = 'eth0'
  net.address = '00:1e:68:7f:2c:8b'
  net.linux.ifindex = 2 (0x2)
  net.arp_proto_hw_id = 1 (0x1)
  net.80203.mac_address = 130602183819ull (0x1e687f2c8bull)

  21: udi = '/org/freedesktop/Hal/devices/pci_10de_550_scsi_host_2'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'scsi_host'
  info.subsystem = 'scsi_host'
  info.product = 'SCSI Host Adapter'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:09.0/host5/scsi_host/host5'
  info.parent = '/org/freedesktop/Hal/devices/pci_10de_550'
  scsi_host.host = 5 (0x5)
  info.category = 'scsi_host'
  info.capabilities = { 'scsi_host' }
  info.udi = '/org/freedesktop/Hal/devices/pci_10de_550_scsi_host_2'

  22: udi = '/org/freedesktop/Hal/devices/pci_10de_550_scsi_host_1'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'scsi_host'
  info.subsystem = 'scsi_host'
  info.product = 'SCSI Host Adapter'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:09.0/host4/scsi_host/host4'
  info.parent = '/org/freedesktop/Hal/devices/pci_10de_550'
  scsi_host.host = 4 (0x4)
  info.category = 'scsi_host'
  info.capabilities = { 'scsi_host' }
  info.udi = '/org/freedesktop/Hal/devices/pci_10de_550_scsi_host_1'

  23: udi = '/org/freedesktop/Hal/devices/pci_10de_550_scsi_host_0'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'scsi_host'
  info.subsystem = 'scsi_host'
  info.product = 'SCSI Host Adapter'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:09.0/host3/scsi_host/host3'
  info.parent = '/org/freedesktop/Hal/devices/pci_10de_550'
  scsi_host.host = 3 (0x3)
  info.category = 'scsi_host'
  info.capabilities = { 'scsi_host' }
  info.udi = '/org/freedesktop/Hal/devices/pci_10de_550_scsi_host_0'

  24: udi = '/org/freedesktop/Hal/devices/pci_10de_550_scsi_host_scsi_device_lun0_scsi_generic'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'scsi_generic'
  scsi_generic.device = '/dev/sg1'
  info.subsystem = 'scsi_generic'
  info.product = 'SCSI Generic Interface'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:09.0/host2/target2:0:0/2:0:0:0/scsi_generic/sg1'
  info.parent = '/org/freedesktop/Hal/devices/pci_10de_550_scsi_host_scsi_device_lun0'
  info.category = 'scsi_generic'
  info.capabilities = { 'scsi_generic' }
  info.udi = '/org/freedesktop/Hal/devices/pci_10de_550_scsi_host_scsi_device_lun0_scsi_generic'
  linux.device_file = '/dev/sg1'

  25: udi = '/org/freedesktop/Hal/devices/pci_10de_550_scsi_host_scsi_host'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'scsi_host'
  info.subsystem = 'scsi_host'
  info.product = 'SCSI Host Adapter'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:09.0/host2/scsi_host/host2'
  info.parent = '/org/freedesktop/Hal/devices/pci_10de_550_scsi_host'
  scsi_host.host = 2 (0x2)
  info.category = 'scsi_host'
  info.capabilities = { 'scsi_host' }
  info.udi = '/org/freedesktop/Hal/devices/pci_10de_550_scsi_host_scsi_host'

  26: udi = '/org/freedesktop/Hal/devices/pci_1180_822_mmc_host'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'mmc_host'
  info.subsystem = 'mmc_host'
  info.product = 'MMC/SD Host Adapter'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:08.0/0000:02:05.1/mmc_host/mmc0'
  info.parent = '/org/freedesktop/Hal/devices/pci_1180_822'
  info.category = 'mmc_host'
  info.capabilities = { 'mmc_host' }
  mmc_host.host = 0 (0x0)
  info.udi = '/org/freedesktop/Hal/devices/pci_1180_822_mmc_host'

  27: udi = '/org/freedesktop/Hal/devices/leds_mmc0'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'leds'
  info.subsystem = 'leds'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:08.0/0000:02:05.1/leds/mmc0::'
  info.parent = '/org/freedesktop/Hal/devices/pci_1180_822'
  info.category = 'leds'
  info.capabilities = { 'leds' }
  leds.num_levels = 256 (0x100)
  leds.device_name = 'mmc0'
  info.udi = '/org/freedesktop/Hal/devices/leds_mmc0'

  28: udi = '/org/freedesktop/Hal/devices/pci_10de_55c_sound_card_0_alsa_playback_1'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'sound'
  alsa.device_file = '/dev/snd/pcmC0D1p'
  alsa.originating_device = '/org/freedesktop/Hal/devices/pci_10de_55c_sound_card_0'
  alsa.card = 0 (0x0)
  alsa.type = 'playback'
  alsa.card_id = 'HDA NVidia'
  alsa.device = 1 (0x1)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:07.0/sound/card0/pcmC0D1p'
  info.parent = '/org/freedesktop/Hal/devices/pci_10de_55c_sound_card_0'
  alsa.pcm_class = 'generic'
  info.category = 'alsa'
  info.capabilities = { 'alsa' }
  alsa.device_id = 'Conexant Digital'
  info.udi = '/org/freedesktop/Hal/devices/pci_10de_55c_sound_card_0_alsa_playback_1'
  linux.device_file = '/dev/snd/pcmC0D1p'
  info.subsystem = 'sound'
  info.product = 'Conexant Digital ALSA Playback Device'

  29: udi = '/org/freedesktop/Hal/devices/pci_10de_55c_sound_card_0_alsa_playback_0'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'sound'
  alsa.device_file = '/dev/snd/pcmC0D0p'
  alsa.originating_device = '/org/freedesktop/Hal/devices/pci_10de_55c_sound_card_0'
  alsa.card = 0 (0x0)
  alsa.type = 'playback'
  alsa.card_id = 'HDA NVidia'
  alsa.device = 0 (0x0)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:07.0/sound/card0/pcmC0D0p'
  info.parent = '/org/freedesktop/Hal/devices/pci_10de_55c_sound_card_0'
  alsa.pcm_class = 'generic'
  info.category = 'alsa'
  info.capabilities = { 'alsa' }
  alsa.device_id = 'CONEXANT Analog'
  info.udi = '/org/freedesktop/Hal/devices/pci_10de_55c_sound_card_0_alsa_playback_0'
  linux.device_file = '/dev/snd/pcmC0D0p'
  info.subsystem = 'sound'
  info.product = 'CONEXANT Analog ALSA Playback Device'

  30: udi = '/org/freedesktop/Hal/devices/pci_10de_55c_sound_card_0_alsa_capture_0'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'sound'
  alsa.device_file = '/dev/snd/pcmC0D0c'
  alsa.originating_device = '/org/freedesktop/Hal/devices/pci_10de_55c_sound_card_0'
  alsa.card = 0 (0x0)
  alsa.type = 'capture'
  alsa.card_id = 'HDA NVidia'
  alsa.device = 0 (0x0)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:07.0/sound/card0/pcmC0D0c'
  info.parent = '/org/freedesktop/Hal/devices/pci_10de_55c_sound_card_0'
  alsa.pcm_class = 'generic'
  info.category = 'alsa'
  info.capabilities = { 'alsa' }
  alsa.device_id = 'CONEXANT Analog'
  info.udi = '/org/freedesktop/Hal/devices/pci_10de_55c_sound_card_0_alsa_capture_0'
  linux.device_file = '/dev/snd/pcmC0D0c'
  info.subsystem = 'sound'
  info.product = 'CONEXANT Analog ALSA Capture Device'

  31: udi = '/org/freedesktop/Hal/devices/pci_10de_55c_sound_card_0_alsa_hw_specific_0'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'sound'
  alsa.device_file = '/dev/snd/hwC0D0'
  alsa.originating_device = '/org/freedesktop/Hal/devices/pci_10de_55c_sound_card_0'
  alsa.card = 0 (0x0)
  alsa.type = 'hw_specific'
  alsa.card_id = 'HDA NVidia'
  alsa.device = 0 (0x0)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:07.0/sound/card0/hwC0D0'
  info.parent = '/org/freedesktop/Hal/devices/pci_10de_55c_sound_card_0'
  info.product = 'HDA NVidia ALSA hardware specific Device'
  info.category = 'alsa'
  info.capabilities = { 'alsa' }
  info.udi = '/org/freedesktop/Hal/devices/pci_10de_55c_sound_card_0_alsa_hw_specific_0'
  linux.device_file = '/dev/snd/hwC0D0'
  info.subsystem = 'sound'

  32: udi = '/org/freedesktop/Hal/devices/pci_10de_55c_sound_card_0_alsa_control__1'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'sound'
  alsa.device_file = '/dev/snd/controlC0'
  alsa.originating_device = '/org/freedesktop/Hal/devices/pci_10de_55c_sound_card_0'
  alsa.card = 0 (0x0)
  alsa.type = 'control'
  alsa.card_id = 'HDA NVidia'
  info.product = 'HDA NVidia ALSA Control Device'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:07.0/sound/card0/controlC0'
  info.parent = '/org/freedesktop/Hal/devices/pci_10de_55c_sound_card_0'
  info.category = 'alsa'
  info.capabilities = { 'alsa' }
  info.udi = '/org/freedesktop/Hal/devices/pci_10de_55c_sound_card_0_alsa_control__1'
  linux.device_file = '/dev/snd/controlC0'
  info.subsystem = 'sound'

  33: udi = '/org/freedesktop/Hal/devices/pci_10de_55c_sound_card_0'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'sound'
  sound.originating_device = '/org/freedesktop/Hal/devices/pci_10de_55c'
  sound.card = 0 (0x0)
  sound.card_id = 'HDA NVidia'
  info.subsystem = 'sound'
  info.product = 'HDA NVidia Sound Card'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:07.0/sound/card0'
  info.parent = '/org/freedesktop/Hal/devices/pci_10de_55c'
  info.category = 'sound'
  info.capabilities = { 'sound' }
  info.udi = '/org/freedesktop/Hal/devices/pci_10de_55c_sound_card_0'

  34: udi = '/org/freedesktop/Hal/devices/pci_10de_560_scsi_host_0'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'scsi_host'
  info.subsystem = 'scsi_host'
  info.product = 'SCSI Host Adapter'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:06.0/host1/scsi_host/host1'
  info.parent = '/org/freedesktop/Hal/devices/pci_10de_560'
  scsi_host.host = 1 (0x1)
  info.category = 'scsi_host'
  info.capabilities = { 'scsi_host' }
  info.udi = '/org/freedesktop/Hal/devices/pci_10de_560_scsi_host_0'

  35: udi = '/org/freedesktop/Hal/devices/pci_10de_560_scsi_host_scsi_device_lun0_scsi_generic'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'scsi_generic'
  scsi_generic.device = '/dev/sg0'
  info.subsystem = 'scsi_generic'
  info.product = 'SCSI Generic Interface'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:06.0/host0/target0:0:0/0:0:0:0/scsi_generic/sg0'
  info.parent = '/org/freedesktop/Hal/devices/pci_10de_560_scsi_host_scsi_device_lun0'
  info.category = 'scsi_generic'
  info.capabilities = { 'scsi_generic' }
  info.udi = '/org/freedesktop/Hal/devices/pci_10de_560_scsi_host_scsi_device_lun0_scsi_generic'
  linux.device_file = '/dev/sg0'

  36: udi = '/org/freedesktop/Hal/devices/pci_10de_560_scsi_host_scsi_host'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'scsi_host'
  info.subsystem = 'scsi_host'
  info.product = 'SCSI Host Adapter'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:06.0/host0/scsi_host/host0'
  info.parent = '/org/freedesktop/Hal/devices/pci_10de_560_scsi_host'
  scsi_host.host = 0 (0x0)
  info.category = 'scsi_host'
  info.capabilities = { 'scsi_host' }
  info.udi = '/org/freedesktop/Hal/devices/pci_10de_560_scsi_host_scsi_host'

  37: udi = '/org/freedesktop/Hal/devices/computer_logicaldev_input_2'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'input'
  info.subsystem = 'input'
  info.product = 'Sleep Button'
  linux.sysfs_path = '/sys/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input0/event0'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  input.device = '/dev/input/event0'
  info.category = 'input'
  info.capabilities = { 'input', 'button', 'input.keys' }
  button.has_state = false
  input.product = 'Sleep Button'
  linux.device_file = '/dev/input/event0'
  button.type = 'sleep'
  info.addons.singleton = { 'hald-addon-input' }
  info.udi = '/org/freedesktop/Hal/devices/computer_logicaldev_input_2'

  38: udi = '/org/freedesktop/Hal/devices/computer_logicaldev_input_1'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'input'
  info.subsystem = 'input'
  info.product = 'Power Button'
  linux.sysfs_path = '/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input2/event2'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  input.device = '/dev/input/event2'
  info.category = 'input'
  info.capabilities = { 'input', 'button', 'input.keys' }
  button.has_state = false
  input.product = 'Power Button'
  linux.device_file = '/dev/input/event2'
  button.type = 'power'
  info.addons.singleton = { 'hald-addon-input' }
  info.udi = '/org/freedesktop/Hal/devices/computer_logicaldev_input_1'

  39: udi = '/org/freedesktop/Hal/devices/computer_power_supply_battery_BAT0'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'power_supply'
  info.subsystem = 'power_supply'
  info.product = 'Primary'
  info.udi = '/org/freedesktop/Hal/devices/computer_power_supply_battery_BAT0'
  battery.type = 'primary'
  battery.reporting.technology = 'Li-ion'
  battery.technology = 'lithium-ion'
  battery.model = 'Primary'
  battery.vendor = 'Hewlett-Packard'
  battery.voltage.design = 14800 (0x39d0)
  battery.voltage.unit = 'mV'
  battery.reporting.design = 6000 (0x1770)
  battery.reporting.unit = 'mAh'
  battery.serial = ''
  battery.present = true
  battery.voltage.current = 16572 (0x40bc)
  battery.is_rechargeable = true
  battery.rechargeable.is_charging = false
  battery.rechargeable.is_discharging = false
  battery.reporting.current = 2240 (0x8c0)
  battery.reporting.last_full = 2240 (0x8c0)
  battery.charge_level.current = 33152 (0x8180)
  battery.charge_level.last_full = 33152 (0x8180)
  battery.charge_level.design = 88800 (0x15ae0)
  battery.charge_level.rate = 0 (0x0)
  battery.charge_level.percentage = 100 (0x64)
  linux.sysfs_path = '/sys/devices/LNXSYSTM:00/device:00/PNP0C0A:00/power_supply/BAT0'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  info.category = 'battery'
  info.capabilities = { 'battery' }

  40: udi = '/org/freedesktop/Hal/devices/computer_logicaldev_input_0'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'input'
  info.subsystem = 'input'
  info.product = 'Video Bus'
  linux.sysfs_path = '/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input6/event6'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  input.device = '/dev/input/event6'
  info.category = 'input'
  info.capabilities = { 'input', 'input.keys', 'button' }
  input.product = 'Video Bus'
  linux.device_file = '/dev/input/event6'
  info.addons.singleton = { 'hald-addon-input' }
  info.udi = '/org/freedesktop/Hal/devices/computer_logicaldev_input_0'

  41: udi = '/org/freedesktop/Hal/devices/computer_power_supply_ac_adapter_ACAD'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'power_supply'
  info.subsystem = 'power_supply'
  info.product = 'Generic AC Adapter Device'
  linux.sysfs_path = '/sys/devices/LNXSYSTM:00/device:00/ACPI0003:00/power_supply/ACAD'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  info.category = 'ac_adapter'
  info.capabilities = { 'ac_adapter' }
  info.udi = '/org/freedesktop/Hal/devices/computer_power_supply_ac_adapter_ACAD'
  ac_adapter.present = true

  42: udi = '/org/freedesktop/Hal/devices/computer_logicaldev_input'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'input'
  info.subsystem = 'input'
  info.product = 'Power Button'
  linux.sysfs_path = '/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3/event3'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  input.device = '/dev/input/event3'
  info.category = 'input'
  info.capabilities = { 'input', 'button', 'input.keys' }
  button.has_state = false
  input.product = 'Power Button'
  linux.device_file = '/dev/input/event3'
  button.type = 'power'
  info.addons.singleton = { 'hald-addon-input' }
  info.udi = '/org/freedesktop/Hal/devices/computer_logicaldev_input'

  43: udi = '/org/freedesktop/Hal/devices/pnp_PNP0c01'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'pnp'
  info.linux.driver = 'system'
  info.subsystem = 'pnp'
  info.product = 'System Board'
  linux.sysfs_path = '/sys/devices/pnp0/00:0b'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  pnp.description = 'System Board'
  pnp.id = 'PNP0c01'
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0c01'

  44: udi = '/org/freedesktop/Hal/devices/pnp_SYN013b'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'pnp'
  info.linux.driver = 'i8042 aux'
  info.subsystem = 'pnp'
  info.product = 'PnP Device (SYN013b)'
  linux.sysfs_path = '/sys/devices/pnp0/00:0a'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  pnp.id = 'SYN013b'
  info.udi = '/org/freedesktop/Hal/devices/pnp_SYN013b'

  45: udi = '/org/freedesktop/Hal/devices/pnp_PNP0303'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'pnp'
  info.linux.driver = 'i8042 kbd'
  info.subsystem = 'pnp'
  info.product = 'IBM Enhanced (101/102-key, PS/2 mouse support)'
  linux.sysfs_path = '/sys/devices/pnp0/00:09'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  pnp.description = 'IBM Enhanced (101/102-key, PS/2 mouse support)'
  pnp.id = 'PNP0303'
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0303'

  46: udi = '/org/freedesktop/Hal/devices/pnp_PNP0c04'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'pnp'
  info.subsystem = 'pnp'
  info.product = 'Math Coprocessor'
  linux.sysfs_path = '/sys/devices/pnp0/00:08'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  pnp.description = 'Math Coprocessor'
  pnp.id = 'PNP0c04'
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0c04'

  47: udi = '/org/freedesktop/Hal/devices/pnp_PNP0b00'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'pnp'
  info.linux.driver = 'rtc_cmos'
  info.subsystem = 'pnp'
  info.product = 'AT Real-Time Clock'
  linux.sysfs_path = '/sys/devices/pnp0/00:07'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  pnp.description = 'AT Real-Time Clock'
  pnp.id = 'PNP0b00'
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0b00'

  48: udi = '/org/freedesktop/Hal/devices/pnp_PNP0800'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'pnp'
  info.subsystem = 'pnp'
  info.product = 'AT-style speaker sound'
  linux.sysfs_path = '/sys/devices/pnp0/00:06'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  pnp.description = 'AT-style speaker sound'
  pnp.id = 'PNP0800'
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0800'

  49: udi = '/org/freedesktop/Hal/devices/pnp_PNP0200'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'pnp'
  info.subsystem = 'pnp'
  info.product = 'AT DMA Controller'
  linux.sysfs_path = '/sys/devices/pnp0/00:05'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  pnp.description = 'AT DMA Controller'
  pnp.id = 'PNP0200'
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0200'

  50: udi = '/org/freedesktop/Hal/devices/pnp_PNP0c02_1'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'pnp'
  info.linux.driver = 'system'
  info.subsystem = 'pnp'
  info.product = 'General ID for reserving resources required by PnP motherboard registers. (Not device specific.)'
  linux.sysfs_path = '/sys/devices/pnp0/00:04'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  pnp.description = 'General ID for reserving resources required by PnP motherboard registers. (Not device specific.)'
  pnp.id = 'PNP0c02'
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0c02_1'

  51: udi = '/org/freedesktop/Hal/devices/pnp_PNP0c02_0'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'pnp'
  info.linux.driver = 'system'
  info.subsystem = 'pnp'
  info.product = 'General ID for reserving resources required by PnP motherboard registers. (Not device specific.)'
  linux.sysfs_path = '/sys/devices/pnp0/00:03'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  pnp.description = 'General ID for reserving resources required by PnP motherboard registers. (Not device specific.)'
  pnp.id = 'PNP0c02'
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0c02_0'

  52: udi = '/org/freedesktop/Hal/devices/pnp_PNP0c02'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'pnp'
  info.linux.driver = 'system'
  info.subsystem = 'pnp'
  info.product = 'General ID for reserving resources required by PnP motherboard registers. (Not device specific.)'
  linux.sysfs_path = '/sys/devices/pnp0/00:02'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  pnp.description = 'General ID for reserving resources required by PnP motherboard registers. (Not device specific.)'
  pnp.id = 'PNP0c02'
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0c02'

  53: udi = '/org/freedesktop/Hal/devices/pnp_PNP0103'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'pnp'
  info.subsystem = 'pnp'
  info.product = 'PnP Device (PNP0103)'
  linux.sysfs_path = '/sys/devices/pnp0/00:01'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  pnp.id = 'PNP0103'
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0103'

  54: udi = '/org/freedesktop/Hal/devices/pnp_PNP0a08'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'pnp'
  info.subsystem = 'pnp'
  info.product = 'PnP Device (PNP0a08)'
  linux.sysfs_path = '/sys/devices/pnp0/00:00'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  pnp.id = 'PNP0a08'
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0a08'

  55: udi = '/org/freedesktop/Hal/devices/platform_vesafb_0'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'platform'
  info.linux.driver = 'vesafb'
  platform.id = 'vesafb.0'
  info.subsystem = 'platform'
  info.product = 'Platform Device (vesafb.0)'
  linux.sysfs_path = '/sys/devices/platform/vesafb.0'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  info.udi = '/org/freedesktop/Hal/devices/platform_vesafb_0'

  56: udi = '/org/freedesktop/Hal/devices/platform_serial8250'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'platform'
  info.linux.driver = 'serial8250'
  platform.id = 'serial8250'
  info.subsystem = 'platform'
  info.product = 'Platform Device (serial8250)'
  linux.sysfs_path = '/sys/devices/platform/serial8250'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  info.udi = '/org/freedesktop/Hal/devices/platform_serial8250'

  57: udi = '/org/freedesktop/Hal/devices/platform_regulatory_0'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'platform'
  platform.id = 'regulatory.0'
  info.subsystem = 'platform'
  info.product = 'Platform Device (regulatory.0)'
  linux.sysfs_path = '/sys/devices/platform/regulatory.0'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  info.udi = '/org/freedesktop/Hal/devices/platform_regulatory_0'

  58: udi = '/org/freedesktop/Hal/devices/platform_reg_dummy'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'platform'
  platform.id = 'reg-dummy'
  info.subsystem = 'platform'
  info.product = 'Platform Device (reg-dummy)'
  linux.sysfs_path = '/sys/devices/platform/reg-dummy'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  info.udi = '/org/freedesktop/Hal/devices/platform_reg_dummy'

  59: udi = '/org/freedesktop/Hal/devices/platform_pcspkr'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'platform'
  platform.id = 'pcspkr'
  info.subsystem = 'platform'
  info.product = 'Platform Device (pcspkr)'
  linux.sysfs_path = '/sys/devices/platform/pcspkr'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  info.udi = '/org/freedesktop/Hal/devices/platform_pcspkr'

  60: udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'serio'
  info.linux.driver = 'psmouse'
  serio.id = 'serio1'
  serio.description = 'i8042 AUX port'
  linux.sysfs_path = '/sys/devices/platform/i8042/serio1'
  info.parent = '/org/freedesktop/Hal/devices/platform_i8042'
  info.product = 'i8042 AUX port'
  info.udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port'
  info.subsystem = 'serio'

  61: udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'serio'
  info.linux.driver = 'atkbd'
  serio.id = 'serio0'
  serio.description = 'i8042 KBD port'
  linux.sysfs_path = '/sys/devices/platform/i8042/serio0'
  info.parent = '/org/freedesktop/Hal/devices/platform_i8042'
  info.product = 'i8042 KBD port'
  info.udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port'
  info.subsystem = 'serio'

  62: udi = '/org/freedesktop/Hal/devices/platform_i8042'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'platform'
  info.linux.driver = 'i8042'
  platform.id = 'i8042'
  info.subsystem = 'platform'
  info.product = 'Platform Device (i8042)'
  linux.sysfs_path = '/sys/devices/platform/i8042'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  info.udi = '/org/freedesktop/Hal/devices/platform_i8042'

  63: udi = '/org/freedesktop/Hal/devices/platform_hp_wmi'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'platform'
  info.linux.driver = 'hp-wmi'
  platform.id = 'hp-wmi'
  info.subsystem = 'platform'
  info.product = 'Platform Device (hp-wmi)'
  linux.sysfs_path = '/sys/devices/platform/hp-wmi'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  info.udi = '/org/freedesktop/Hal/devices/platform_hp_wmi'

  64: udi = '/org/freedesktop/Hal/devices/platform_eisa_0'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'platform'
  platform.id = 'eisa.0'
  info.subsystem = 'platform'
  info.product = 'Platform Device (eisa.0)'
  linux.sysfs_path = '/sys/devices/platform/eisa.0'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  info.udi = '/org/freedesktop/Hal/devices/platform_eisa_0'

  65: udi = '/org/freedesktop/Hal/devices/platform_Fixed_MDIO_bus_0'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'platform'
  platform.id = 'Fixed MDIO bus.0'
  info.subsystem = 'platform'
  info.product = 'Platform Device (Fixed MDIO bus.0)'
  linux.sysfs_path = '/sys/devices/platform/Fixed MDIO bus.0'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  info.udi = '/org/freedesktop/Hal/devices/platform_Fixed_MDIO_bus_0'

  66: udi = '/org/freedesktop/Hal/devices/pci_1022_1103'
  pci.product = 'K8 [Athlon64/Opteron] Miscellaneous Control'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'pci'
  info.linux.driver = 'k8temp'
  info.udi = '/org/freedesktop/Hal/devices/pci_1022_1103'
  info.subsystem = 'pci'
  info.product = 'K8 [Athlon64/Opteron] Miscellaneous Control'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:18.3'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:18.3'
  pci.product_id = 4355 (0x1103)
  pci.vendor_id = 4130 (0x1022)
  pci.subsys_product_id = 0 (0x0)
  pci.subsys_vendor_id = 0 (0x0)
  pci.device_class = 6 (0x6)
  pci.device_subclass = 0 (0x0)
  pci.device_protocol = 0 (0x0)
  pci.vendor = 'Advanced Micro Devices [AMD]'
  info.vendor = 'Advanced Micro Devices [AMD]'

  67: udi = '/org/freedesktop/Hal/devices/pci_1022_1102'
  pci.product = 'K8 [Athlon64/Opteron] DRAM Controller'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'pci'
  info.udi = '/org/freedesktop/Hal/devices/pci_1022_1102'
  info.subsystem = 'pci'
  info.product = 'K8 [Athlon64/Opteron] DRAM Controller'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:18.2'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:18.2'
  pci.product_id = 4354 (0x1102)
  pci.vendor_id = 4130 (0x1022)
  pci.subsys_product_id = 0 (0x0)
  pci.subsys_vendor_id = 0 (0x0)
  pci.device_class = 6 (0x6)
  pci.device_subclass = 0 (0x0)
  pci.device_protocol = 0 (0x0)
  pci.vendor = 'Advanced Micro Devices [AMD]'
  info.vendor = 'Advanced Micro Devices [AMD]'

  68: udi = '/org/freedesktop/Hal/devices/pci_1022_1101'
  pci.product = 'K8 [Athlon64/Opteron] Address Map'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'pci'
  info.udi = '/org/freedesktop/Hal/devices/pci_1022_1101'
  info.subsystem = 'pci'
  info.product = 'K8 [Athlon64/Opteron] Address Map'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:18.1'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:18.1'
  pci.product_id = 4353 (0x1101)
  pci.vendor_id = 4130 (0x1022)
  pci.subsys_product_id = 0 (0x0)
  pci.subsys_vendor_id = 0 (0x0)
  pci.device_class = 6 (0x6)
  pci.device_subclass = 0 (0x0)
  pci.device_protocol = 0 (0x0)
  pci.vendor = 'Advanced Micro Devices [AMD]'
  info.vendor = 'Advanced Micro Devices [AMD]'

  69: udi = '/org/freedesktop/Hal/devices/pci_1022_1100'
  pci.product = 'K8 [Athlon64/Opteron] HyperTransport Technology Configuration'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'pci'
  info.udi = '/org/freedesktop/Hal/devices/pci_1022_1100'
  info.subsystem = 'pci'
  info.product = 'K8 [Athlon64/Opteron] HyperTransport Technology Configuration'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:18.0'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:18.0'
  pci.product_id = 4352 (0x1100)
  pci.vendor_id = 4130 (0x1022)
  pci.subsys_product_id = 0 (0x0)
  pci.subsys_vendor_id = 0 (0x0)
  pci.device_class = 6 (0x6)
  pci.device_subclass = 0 (0x0)
  pci.device_protocol = 0 (0x0)
  pci.vendor = 'Advanced Micro Devices [AMD]'
  info.vendor = 'Advanced Micro Devices [AMD]'

  70: udi = '/org/freedesktop/Hal/devices/pci_10de_531'
  pci.product = 'C67 [GeForce 7150M / nForce 630M]'
  pci.subsys_vendor = 'Hewlett-Packard Company'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'pci'
  info.linux.driver = 'nvidia'
  info.udi = '/org/freedesktop/Hal/devices/pci_10de_531'
  info.subsystem = 'pci'
  info.product = 'C67 [GeForce 7150M / nForce 630M]'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:12.0'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:12.0'
  pci.product_id = 1329 (0x531)
  pci.vendor_id = 4318 (0x10de)
  pci.subsys_product_id = 12495 (0x30cf)
  pci.subsys_vendor_id = 4156 (0x103c)
  pci.device_class = 3 (0x3)
  pci.device_subclass = 0 (0x0)
  pci.device_protocol = 0 (0x0)
  pci.vendor = 'nVidia Corporation'
  info.vendor = 'nVidia Corporation'

  71: udi = '/org/freedesktop/Hal/devices/pci_168c_1c'
  pci.product = 'AR5001 Wireless Network Adapter'
  pci.subsys_vendor = 'Hewlett-Packard Company'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'pci'
  info.linux.driver = 'ath5k'
  info.udi = '/org/freedesktop/Hal/devices/pci_168c_1c'
  info.subsystem = 'pci'
  info.product = 'AR5001 Wireless Network Adapter'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:0d.0/0000:03:00.0'
  info.parent = '/org/freedesktop/Hal/devices/pci_10de_563_0'
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:0d.0/0000:03:00.0'
  pci.product_id = 28 (0x1c)
  pci.vendor_id = 5772 (0x168c)
  pci.subsys_product_id = 4987 (0x137b)
  pci.subsys_vendor_id = 4156 (0x103c)
  pci.device_class = 2 (0x2)
  pci.device_subclass = 0 (0x0)
  pci.device_protocol = 0 (0x0)
  pci.vendor = 'Atheros Communications Inc.'
  info.vendor = 'Atheros Communications Inc.'

  72: udi = '/org/freedesktop/Hal/devices/pci_10de_563_0'
  pci.product = 'MCP67 PCI Express Bridge'
  pci.subsys_vendor = 'nVidia Corporation'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'pci'
  info.linux.driver = 'pcieport'
  info.udi = '/org/freedesktop/Hal/devices/pci_10de_563_0'
  info.subsystem = 'pci'
  info.product = 'MCP67 PCI Express Bridge'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:0d.0'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:0d.0'
  pci.product_id = 1379 (0x563)
  pci.vendor_id = 4318 (0x10de)
  pci.subsys_product_id = 0 (0x0)
  pci.subsys_vendor_id = 4318 (0x10de)
  pci.device_class = 6 (0x6)
  pci.device_subclass = 4 (0x4)
  pci.device_protocol = 0 (0x0)
  pci.vendor = 'nVidia Corporation'
  info.vendor = 'nVidia Corporation'

  73: udi = '/org/freedesktop/Hal/devices/pci_10de_563'
  pci.product = 'MCP67 PCI Express Bridge'
  pci.subsys_vendor = 'nVidia Corporation'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'pci'
  info.linux.driver = 'pcieport'
  info.udi = '/org/freedesktop/Hal/devices/pci_10de_563'
  info.subsystem = 'pci'
  info.product = 'MCP67 PCI Express Bridge'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:0c.0'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:0c.0'
  pci.product_id = 1379 (0x563)
  pci.vendor_id = 4318 (0x10de)
  pci.subsys_product_id = 0 (0x0)
  pci.subsys_vendor_id = 4318 (0x10de)
  pci.device_class = 6 (0x6)
  pci.device_subclass = 4 (0x4)
  pci.device_protocol = 0 (0x0)
  pci.vendor = 'nVidia Corporation'
  info.vendor = 'nVidia Corporation'

  74: udi = '/org/freedesktop/Hal/devices/pci_10de_54c'
  pci.product = 'MCP67 Ethernet'
  pci.subsys_vendor = 'Hewlett-Packard Company'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'pci'
  info.linux.driver = 'forcedeth'
  info.udi = '/org/freedesktop/Hal/devices/pci_10de_54c'
  info.subsystem = 'pci'
  info.product = 'MCP67 Ethernet'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:0a.0'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:0a.0'
  pci.product_id = 1356 (0x54c)
  pci.vendor_id = 4318 (0x10de)
  pci.subsys_product_id = 12495 (0x30cf)
  pci.subsys_vendor_id = 4156 (0x103c)
  pci.device_class = 2 (0x2)
  pci.device_subclass = 0 (0x0)
  pci.device_protocol = 0 (0x0)
  pci.vendor = 'nVidia Corporation'
  info.vendor = 'nVidia Corporation'

  75: udi = '/org/freedesktop/Hal/devices/pci_10de_550_scsi_host_scsi_device_lun0'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'scsi'
  info.linux.driver = 'sd'
  info.subsystem = 'scsi'
  info.product = 'SCSI Device'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:09.0/host2/target2:0:0/2:0:0:0'
  info.parent = '/org/freedesktop/Hal/devices/pci_10de_550_scsi_host'
  info.udi = '/org/freedesktop/Hal/devices/pci_10de_550_scsi_host_scsi_device_lun0'
  scsi.host = 2 (0x2)
  scsi.bus = 0 (0x0)
  scsi.target = 0 (0x0)
  scsi.lun = 0 (0x0)
  scsi.model = 'SAMSUNG HM160HI'
  scsi.vendor = 'ATA'
  scsi.type = 'disk'

  76: udi = '/org/freedesktop/Hal/devices/pci_10de_550_scsi_host'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'scsi_host'
  info.subsystem = 'scsi_host'
  info.product = 'SCSI Host Adapter'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:09.0/host2'
  info.parent = '/org/freedesktop/Hal/devices/pci_10de_550'
  scsi_host.host = 2 (0x2)
  info.category = 'scsi_host'
  info.capabilities = { 'scsi_host' }
  info.udi = '/org/freedesktop/Hal/devices/pci_10de_550_scsi_host'

  77: udi = '/org/freedesktop/Hal/devices/pci_10de_550'
  pci.product = 'MCP67 AHCI Controller'
  pci.subsys_vendor = 'Hewlett-Packard Company'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'pci'
  info.linux.driver = 'ahci'
  info.udi = '/org/freedesktop/Hal/devices/pci_10de_550'
  info.subsystem = 'pci'
  info.product = 'MCP67 AHCI Controller'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:09.0'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:09.0'
  pci.product_id = 1360 (0x550)
  pci.vendor_id = 4318 (0x10de)
  pci.subsys_product_id = 12495 (0x30cf)
  pci.subsys_vendor_id = 4156 (0x103c)
  pci.device_class = 1 (0x1)
  pci.device_subclass = 1 (0x1)
  pci.device_protocol = 133 (0x85)
  pci.vendor = 'nVidia Corporation'
  info.vendor = 'nVidia Corporation'

  78: udi = '/org/freedesktop/Hal/devices/pci_1180_852'
  pci.product = 'xD-Picture Card Controller'
  pci.subsys_vendor = 'Hewlett-Packard Company'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'pci'
  info.linux.driver = 'r852'
  info.udi = '/org/freedesktop/Hal/devices/pci_1180_852'
  info.subsystem = 'pci'
  info.product = 'xD-Picture Card Controller'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:08.0/0000:02:05.3'
  info.parent = '/org/freedesktop/Hal/devices/pci_10de_561'
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:08.0/0000:02:05.3'
  pci.product_id = 2130 (0x852)
  pci.vendor_id = 4480 (0x1180)
  pci.subsys_product_id = 12495 (0x30cf)
  pci.subsys_vendor_id = 4156 (0x103c)
  pci.device_class = 8 (0x8)
  pci.device_subclass = 128 (0x80)
  pci.device_protocol = 0 (0x0)
  pci.vendor = 'Ricoh Co Ltd'
  info.vendor = 'Ricoh Co Ltd'

  79: udi = '/org/freedesktop/Hal/devices/pci_1180_592'
  pci.product = 'R5C592 Memory Stick Bus Host Adapter'
  pci.subsys_vendor = 'Hewlett-Packard Company'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'pci'
  info.udi = '/org/freedesktop/Hal/devices/pci_1180_592'
  info.subsystem = 'pci'
  info.product = 'R5C592 Memory Stick Bus Host Adapter'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:08.0/0000:02:05.2'
  info.parent = '/org/freedesktop/Hal/devices/pci_10de_561'
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:08.0/0000:02:05.2'
  pci.product_id = 1426 (0x592)
  pci.vendor_id = 4480 (0x1180)
  pci.subsys_product_id = 12495 (0x30cf)
  pci.subsys_vendor_id = 4156 (0x103c)
  pci.device_class = 8 (0x8)
  pci.device_subclass = 128 (0x80)
  pci.device_protocol = 0 (0x0)
  pci.vendor = 'Ricoh Co Ltd'
  info.vendor = 'Ricoh Co Ltd'

  80: udi = '/org/freedesktop/Hal/devices/pci_1180_822'
  pci.product = 'R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter'
  pci.subsys_vendor = 'Hewlett-Packard Company'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'pci'
  info.linux.driver = 'sdhci-pci'
  info.udi = '/org/freedesktop/Hal/devices/pci_1180_822'
  info.subsystem = 'pci'
  info.product = 'R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:08.0/0000:02:05.1'
  info.parent = '/org/freedesktop/Hal/devices/pci_10de_561'
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:08.0/0000:02:05.1'
  pci.product_id = 2082 (0x822)
  pci.vendor_id = 4480 (0x1180)
  pci.subsys_product_id = 12495 (0x30cf)
  pci.subsys_vendor_id = 4156 (0x103c)
  pci.device_class = 8 (0x8)
  pci.device_subclass = 5 (0x5)
  pci.device_protocol = 0 (0x0)
  pci.vendor = 'Ricoh Co Ltd'
  info.vendor = 'Ricoh Co Ltd'

  81: udi = '/org/freedesktop/Hal/devices/ieee1394_guid241b004c520501'
  ieee1394.device = '/dev/fw0'
  ieee1394.guid = 10162787255977217ull (0x241b004c520501ull)
  ieee1394.vendor_id = 13634846 (0xd00d1e)
  ieee1394.product_id = 1 (0x1)
  ieee1394.vendor = 'Linux Firewire'
  ieee1394.product = 'Juju'
  linux.subsystem = 'firewire'
  linux.hotplug_type = 2 (0x2)
  info.subsystem = 'ieee1394'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:08.0/0000:02:05.0/fw0'
  info.parent = '/org/freedesktop/Hal/devices/pci_1180_832'
  info.udi = '/org/freedesktop/Hal/devices/ieee1394_guid241b004c520501'
  info.capabilities = { 'ieee1394' }
  linux.device_file = '/dev/fw0'

  82: udi = '/org/freedesktop/Hal/devices/pci_1180_832'
  pci.product = 'R5C832 IEEE 1394 Controller'
  pci.subsys_vendor = 'Hewlett-Packard Company'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'pci'
  info.linux.driver = 'firewire_ohci'
  info.udi = '/org/freedesktop/Hal/devices/pci_1180_832'
  info.subsystem = 'pci'
  info.product = 'R5C832 IEEE 1394 Controller'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:08.0/0000:02:05.0'
  info.parent = '/org/freedesktop/Hal/devices/pci_10de_561'
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:08.0/0000:02:05.0'
  pci.product_id = 2098 (0x832)
  pci.vendor_id = 4480 (0x1180)
  pci.subsys_product_id = 12495 (0x30cf)
  pci.subsys_vendor_id = 4156 (0x103c)
  pci.device_class = 12 (0xc)
  pci.device_subclass = 0 (0x0)
  pci.device_protocol = 16 (0x10)
  pci.vendor = 'Ricoh Co Ltd'
  info.vendor = 'Ricoh Co Ltd'

  83: udi = '/org/freedesktop/Hal/devices/pci_10de_561'
  pci.product = 'MCP67 PCI Bridge'
  pci.subsys_vendor = 'nVidia Corporation'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'pci'
  info.udi = '/org/freedesktop/Hal/devices/pci_10de_561'
  info.subsystem = 'pci'
  info.product = 'MCP67 PCI Bridge'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:08.0'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:08.0'
  pci.product_id = 1377 (0x561)
  pci.vendor_id = 4318 (0x10de)
  pci.subsys_product_id = 52100 (0xcb84)
  pci.subsys_vendor_id = 4318 (0x10de)
  pci.device_class = 6 (0x6)
  pci.device_subclass = 4 (0x4)
  pci.device_protocol = 1 (0x1)
  pci.vendor = 'nVidia Corporation'
  info.vendor = 'nVidia Corporation'

  84: udi = '/org/freedesktop/Hal/devices/pci_10de_55c'
  pci.product = 'MCP67 High Definition Audio'
  pci.subsys_vendor = 'Hewlett-Packard Company'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'pci'
  info.linux.driver = 'HDA Intel'
  info.udi = '/org/freedesktop/Hal/devices/pci_10de_55c'
  info.subsystem = 'pci'
  info.product = 'MCP67 High Definition Audio'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:07.0'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:07.0'
  pci.product_id = 1372 (0x55c)
  pci.vendor_id = 4318 (0x10de)
  pci.subsys_product_id = 12495 (0x30cf)
  pci.subsys_vendor_id = 4156 (0x103c)
  pci.device_class = 4 (0x4)
  pci.device_subclass = 3 (0x3)
  pci.device_protocol = 0 (0x0)
  pci.vendor = 'nVidia Corporation'
  info.vendor = 'nVidia Corporation'

  85: udi = '/org/freedesktop/Hal/devices/pci_10de_560_scsi_host_scsi_device_lun0'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'scsi'
  info.linux.driver = 'sr'
  info.subsystem = 'scsi'
  info.product = 'SCSI Device'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:06.0/host0/target0:0:0/0:0:0:0'
  info.parent = '/org/freedesktop/Hal/devices/pci_10de_560_scsi_host'
  info.udi = '/org/freedesktop/Hal/devices/pci_10de_560_scsi_host_scsi_device_lun0'
  scsi.host = 0 (0x0)
  scsi.bus = 0 (0x0)
  scsi.target = 0 (0x0)
  scsi.lun = 0 (0x0)
  scsi.model = 'CDDVDW TS-L632N'
  scsi.vendor = 'TSSTcorp'
  scsi.type = 'cdrom'

  86: udi = '/org/freedesktop/Hal/devices/pci_10de_560_scsi_host'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'scsi_host'
  info.subsystem = 'scsi_host'
  info.product = 'SCSI Host Adapter'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:06.0/host0'
  info.parent = '/org/freedesktop/Hal/devices/pci_10de_560'
  scsi_host.host = 0 (0x0)
  info.category = 'scsi_host'
  info.capabilities = { 'scsi_host' }
  info.udi = '/org/freedesktop/Hal/devices/pci_10de_560_scsi_host'

  87: udi = '/org/freedesktop/Hal/devices/pci_10de_560'
  pci.product = 'MCP67 IDE Controller'
  pci.subsys_vendor = 'Hewlett-Packard Company'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'pci'
  info.linux.driver = 'pata_amd'
  info.udi = '/org/freedesktop/Hal/devices/pci_10de_560'
  info.subsystem = 'pci'
  info.product = 'MCP67 IDE Controller'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:06.0'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:06.0'
  pci.product_id = 1376 (0x560)
  pci.vendor_id = 4318 (0x10de)
  pci.subsys_product_id = 12495 (0x30cf)
  pci.subsys_vendor_id = 4156 (0x103c)
  pci.device_class = 1 (0x1)
  pci.device_subclass = 1 (0x1)
  pci.device_protocol = 138 (0x8a)
  pci.vendor = 'nVidia Corporation'
  info.vendor = 'nVidia Corporation'

  88: udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_2_0000_00_04_1_if0'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'usb'
  info.linux.driver = 'hub'
  info.subsystem = 'usb'
  info.product = 'USB Hub Interface'
  info.udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_2_0000_00_04_1_if0'
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:04.1/usb2/2-0:1.0'
  usb.configuration_value = 1 (0x1)
  usb.num_configurations = 1 (0x1)
  usb.num_interfaces = 1 (0x1)
  usb.device_class = 9 (0x9)
  usb.device_subclass = 0 (0x0)
  usb.device_protocol = 0 (0x0)
  usb.vendor_id = 7531 (0x1d6b)
  usb.product_id = 2 (0x2)
  usb.vendor = 'Linux Foundation'
  usb.product = 'USB Hub Interface'
  usb.device_revision_bcd = 518 (0x206)
  usb.num_ports = 2 (0x2)
  usb.speed = 480.000
  usb.linux.device_number = 1 (0x1)
  usb.max_power = 0 (0x0)
  usb.can_wake_up = true
  usb.version = 2.00000
  usb.bus_number = 2 (0x2)
  usb.is_self_powered = true
  usb.serial = '0000:00:04.1'
  usb.interface.number = 0 (0x0)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:04.1/usb2/2-0:1.0'
  info.parent = '/org/freedesktop/Hal/devices/usb_device_1d6b_2_0000_00_04_1'
  usb.interface.subclass = 0 (0x0)
  usb.interface.class = 9 (0x9)
  usb.interface.protocol = 0 (0x0)

  89: udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_2_0000_00_04_1'
  info.vendor = 'Linux Foundation'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'usb'
  info.linux.driver = 'usb'
  usb_device.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:04.1/usb2'
  usb_device.configuration_value = 1 (0x1)
  usb_device.num_configurations = 1 (0x1)
  usb_device.num_interfaces = 1 (0x1)
  usb_device.device_class = 9 (0x9)
  usb_device.device_subclass = 0 (0x0)
  usb_device.device_protocol = 0 (0x0)
  usb_device.vendor_id = 7531 (0x1d6b)
  usb_device.product_id = 2 (0x2)
  usb_device.vendor = 'Linux Foundation'
  usb_device.product = '2.0 root hub'
  usb_device.device_revision_bcd = 518 (0x206)
  info.subsystem = 'usb_device'
  info.udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_2_0000_00_04_1'
  usb_device.num_ports = 2 (0x2)
  info.product = '2.0 root hub'
  usb_device.speed = 480.000
  usb_device.linux.device_number = 1 (0x1)
  usb_device.max_power = 0 (0x0)
  usb_device.can_wake_up = true
  usb_device.version = 2.00000
  linux.device_file = '/dev/bus/usb/002/001'
  usb_device.bus_number = 2 (0x2)
  usb_device.is_self_powered = true
  usb_device.serial = '0000:00:04.1'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:04.1/usb2'
  info.parent = '/org/freedesktop/Hal/devices/pci_10de_55f_0'

  90: udi = '/org/freedesktop/Hal/devices/pci_10de_55f_0'
  pci.product = 'MCP67 EHCI USB 2.0 Controller'
  pci.subsys_vendor = 'Hewlett-Packard Company'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'pci'
  info.linux.driver = 'ehci_hcd'
  info.udi = '/org/freedesktop/Hal/devices/pci_10de_55f_0'
  info.subsystem = 'pci'
  info.product = 'MCP67 EHCI USB 2.0 Controller'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:04.1'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:04.1'
  pci.product_id = 1375 (0x55f)
  pci.vendor_id = 4318 (0x10de)
  pci.subsys_product_id = 12495 (0x30cf)
  pci.subsys_vendor_id = 4156 (0x103c)
  pci.device_class = 12 (0xc)
  pci.device_subclass = 3 (0x3)
  pci.device_protocol = 32 (0x20)
  pci.vendor = 'nVidia Corporation'
  info.vendor = 'nVidia Corporation'

  91: udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_04_0_if0'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'usb'
  info.linux.driver = 'hub'
  info.subsystem = 'usb'
  info.product = 'USB Hub Interface'
  info.udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_04_0_if0'
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:04.0/usb4/4-0:1.0'
  usb.configuration_value = 1 (0x1)
  usb.num_configurations = 1 (0x1)
  usb.num_interfaces = 1 (0x1)
  usb.device_class = 9 (0x9)
  usb.device_subclass = 0 (0x0)
  usb.device_protocol = 0 (0x0)
  usb.vendor_id = 7531 (0x1d6b)
  usb.product_id = 1 (0x1)
  usb.vendor = 'Linux Foundation'
  usb.product = 'USB Hub Interface'
  usb.device_revision_bcd = 518 (0x206)
  usb.num_ports = 2 (0x2)
  usb.speed = 12.0000
  usb.linux.device_number = 1 (0x1)
  usb.max_power = 0 (0x0)
  usb.can_wake_up = true
  usb.version = 1.10000
  usb.bus_number = 4 (0x4)
  usb.is_self_powered = true
  usb.serial = '0000:00:04.0'
  usb.interface.number = 0 (0x0)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:04.0/usb4/4-0:1.0'
  info.parent = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_04_0'
  usb.interface.subclass = 0 (0x0)
  usb.interface.class = 9 (0x9)
  usb.interface.protocol = 0 (0x0)

  92: udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_04_0'
  info.vendor = 'Linux Foundation'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'usb'
  info.linux.driver = 'usb'
  usb_device.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:04.0/usb4'
  usb_device.configuration_value = 1 (0x1)
  usb_device.num_configurations = 1 (0x1)
  usb_device.num_interfaces = 1 (0x1)
  usb_device.device_class = 9 (0x9)
  usb_device.device_subclass = 0 (0x0)
  usb_device.device_protocol = 0 (0x0)
  usb_device.vendor_id = 7531 (0x1d6b)
  usb_device.product_id = 1 (0x1)
  usb_device.vendor = 'Linux Foundation'
  usb_device.product = '1.1 root hub'
  usb_device.device_revision_bcd = 518 (0x206)
  info.subsystem = 'usb_device'
  info.udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_04_0'
  usb_device.num_ports = 2 (0x2)
  info.product = '1.1 root hub'
  usb_device.speed = 12.0000
  usb_device.linux.device_number = 1 (0x1)
  usb_device.max_power = 0 (0x0)
  usb_device.can_wake_up = true
  usb_device.version = 1.10000
  linux.device_file = '/dev/bus/usb/004/001'
  usb_device.bus_number = 4 (0x4)
  usb_device.is_self_powered = true
  usb_device.serial = '0000:00:04.0'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:04.0/usb4'
  info.parent = '/org/freedesktop/Hal/devices/pci_10de_55e_0'

  93: udi = '/org/freedesktop/Hal/devices/pci_10de_55e_0'
  pci.product = 'MCP67 OHCI USB 1.1 Controller'
  pci.subsys_vendor = 'Hewlett-Packard Company'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'pci'
  info.linux.driver = 'ohci_hcd'
  info.udi = '/org/freedesktop/Hal/devices/pci_10de_55e_0'
  info.subsystem = 'pci'
  info.product = 'MCP67 OHCI USB 1.1 Controller'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:04.0'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:04.0'
  pci.product_id = 1374 (0x55e)
  pci.vendor_id = 4318 (0x10de)
  pci.subsys_product_id = 12495 (0x30cf)
  pci.subsys_vendor_id = 4156 (0x103c)
  pci.device_class = 12 (0xc)
  pci.device_subclass = 3 (0x3)
  pci.device_protocol = 16 (0x10)
  pci.vendor = 'nVidia Corporation'
  info.vendor = 'nVidia Corporation'

  94: udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_2_0000_00_02_1_if0'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'usb'
  info.linux.driver = 'hub'
  info.subsystem = 'usb'
  info.product = 'USB Hub Interface'
  info.udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_2_0000_00_02_1_if0'
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:02.1/usb1/1-0:1.0'
  usb.configuration_value = 1 (0x1)
  usb.num_configurations = 1 (0x1)
  usb.num_interfaces = 1 (0x1)
  usb.device_class = 9 (0x9)
  usb.device_subclass = 0 (0x0)
  usb.device_protocol = 0 (0x0)
  usb.vendor_id = 7531 (0x1d6b)
  usb.product_id = 2 (0x2)
  usb.vendor = 'Linux Foundation'
  usb.product = 'USB Hub Interface'
  usb.device_revision_bcd = 518 (0x206)
  usb.num_ports = 7 (0x7)
  usb.speed = 480.000
  usb.linux.device_number = 1 (0x1)
  usb.max_power = 0 (0x0)
  usb.can_wake_up = true
  usb.version = 2.00000
  usb.bus_number = 1 (0x1)
  usb.is_self_powered = true
  usb.serial = '0000:00:02.1'
  usb.interface.number = 0 (0x0)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:02.1/usb1/1-0:1.0'
  info.parent = '/org/freedesktop/Hal/devices/usb_device_1d6b_2_0000_00_02_1'
  usb.interface.subclass = 0 (0x0)
  usb.interface.class = 9 (0x9)
  usb.interface.protocol = 0 (0x0)

  95: udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_2_0000_00_02_1'
  info.vendor = 'Linux Foundation'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'usb'
  info.linux.driver = 'usb'
  usb_device.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:02.1/usb1'
  usb_device.configuration_value = 1 (0x1)
  usb_device.num_configurations = 1 (0x1)
  usb_device.num_interfaces = 1 (0x1)
  usb_device.device_class = 9 (0x9)
  usb_device.device_subclass = 0 (0x0)
  usb_device.device_protocol = 0 (0x0)
  usb_device.vendor_id = 7531 (0x1d6b)
  usb_device.product_id = 2 (0x2)
  usb_device.vendor = 'Linux Foundation'
  usb_device.product = '2.0 root hub'
  usb_device.device_revision_bcd = 518 (0x206)
  info.subsystem = 'usb_device'
  info.udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_2_0000_00_02_1'
  usb_device.num_ports = 7 (0x7)
  info.product = '2.0 root hub'
  usb_device.speed = 480.000
  usb_device.linux.device_number = 1 (0x1)
  usb_device.max_power = 0 (0x0)
  usb_device.can_wake_up = true
  usb_device.version = 2.00000
  linux.device_file = '/dev/bus/usb/001/001'
  usb_device.bus_number = 1 (0x1)
  usb_device.is_self_powered = true
  usb_device.serial = '0000:00:02.1'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:02.1/usb1'
  info.parent = '/org/freedesktop/Hal/devices/pci_10de_55f'

  96: udi = '/org/freedesktop/Hal/devices/pci_10de_55f'
  pci.product = 'MCP67 EHCI USB 2.0 Controller'
  pci.subsys_vendor = 'Hewlett-Packard Company'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'pci'
  info.linux.driver = 'ehci_hcd'
  info.udi = '/org/freedesktop/Hal/devices/pci_10de_55f'
  info.subsystem = 'pci'
  info.product = 'MCP67 EHCI USB 2.0 Controller'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:02.1'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:02.1'
  pci.product_id = 1375 (0x55f)
  pci.vendor_id = 4318 (0x10de)
  pci.subsys_product_id = 12495 (0x30cf)
  pci.subsys_vendor_id = 4156 (0x103c)
  pci.device_class = 12 (0xc)
  pci.device_subclass = 3 (0x3)
  pci.device_protocol = 32 (0x20)
  pci.vendor = 'nVidia Corporation'
  info.vendor = 'nVidia Corporation'

  97: udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_02_0_if0'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'usb'
  info.linux.driver = 'hub'
  info.subsystem = 'usb'
  info.product = 'USB Hub Interface'
  info.udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_02_0_if0'
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:02.0/usb3/3-0:1.0'
  usb.configuration_value = 1 (0x1)
  usb.num_configurations = 1 (0x1)
  usb.num_interfaces = 1 (0x1)
  usb.device_class = 9 (0x9)
  usb.device_subclass = 0 (0x0)
  usb.device_protocol = 0 (0x0)
  usb.vendor_id = 7531 (0x1d6b)
  usb.product_id = 1 (0x1)
  usb.vendor = 'Linux Foundation'
  usb.product = 'USB Hub Interface'
  usb.device_revision_bcd = 518 (0x206)
  usb.num_ports = 7 (0x7)
  usb.speed = 12.0000
  usb.linux.device_number = 1 (0x1)
  usb.max_power = 0 (0x0)
  usb.can_wake_up = true
  usb.version = 1.10000
  usb.bus_number = 3 (0x3)
  usb.is_self_powered = true
  usb.serial = '0000:00:02.0'
  usb.interface.number = 0 (0x0)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:02.0/usb3/3-0:1.0'
  info.parent = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_02_0'
  usb.interface.subclass = 0 (0x0)
  usb.interface.class = 9 (0x9)
  usb.interface.protocol = 0 (0x0)

  98: udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_02_0'
  info.vendor = 'Linux Foundation'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'usb'
  info.linux.driver = 'usb'
  usb_device.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:02.0/usb3'
  usb_device.configuration_value = 1 (0x1)
  usb_device.num_configurations = 1 (0x1)
  usb_device.num_interfaces = 1 (0x1)
  usb_device.device_class = 9 (0x9)
  usb_device.device_subclass = 0 (0x0)
  usb_device.device_protocol = 0 (0x0)
  usb_device.vendor_id = 7531 (0x1d6b)
  usb_device.product_id = 1 (0x1)
  usb_device.vendor = 'Linux Foundation'
  usb_device.product = '1.1 root hub'
  usb_device.device_revision_bcd = 518 (0x206)
  info.subsystem = 'usb_device'
  info.udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_02_0'
  usb_device.num_ports = 7 (0x7)
  info.product = '1.1 root hub'
  usb_device.speed = 12.0000
  usb_device.linux.device_number = 1 (0x1)
  usb_device.max_power = 0 (0x0)
  usb_device.can_wake_up = true
  usb_device.version = 1.10000
  linux.device_file = '/dev/bus/usb/003/001'
  usb_device.bus_number = 3 (0x3)
  usb_device.is_self_powered = true
  usb_device.serial = '0000:00:02.0'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:02.0/usb3'
  info.parent = '/org/freedesktop/Hal/devices/pci_10de_55e'

  99: udi = '/org/freedesktop/Hal/devices/pci_10de_55e'
  pci.product = 'MCP67 OHCI USB 1.1 Controller'
  pci.subsys_vendor = 'Hewlett-Packard Company'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'pci'
  info.linux.driver = 'ohci_hcd'
  info.udi = '/org/freedesktop/Hal/devices/pci_10de_55e'
  info.subsystem = 'pci'
  info.product = 'MCP67 OHCI USB 1.1 Controller'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:02.0'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:02.0'
  pci.product_id = 1374 (0x55e)
  pci.vendor_id = 4318 (0x10de)
  pci.subsys_product_id = 12495 (0x30cf)
  pci.subsys_vendor_id = 4156 (0x103c)
  pci.device_class = 12 (0xc)
  pci.device_subclass = 3 (0x3)
  pci.device_protocol = 16 (0x10)
  pci.vendor = 'nVidia Corporation'
  info.vendor = 'nVidia Corporation'

  100: udi = '/org/freedesktop/Hal/devices/pci_10de_543'
  pci.product = 'MCP67 Co-processor'
  pci.subsys_vendor = 'Hewlett-Packard Company'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'pci'
  info.udi = '/org/freedesktop/Hal/devices/pci_10de_543'
  info.subsystem = 'pci'
  info.product = 'MCP67 Co-processor'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:01.3'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:01.3'
  pci.product_id = 1347 (0x543)
  pci.vendor_id = 4318 (0x10de)
  pci.subsys_product_id = 12495 (0x30cf)
  pci.subsys_vendor_id = 4156 (0x103c)
  pci.device_class = 11 (0xb)
  pci.device_subclass = 64 (0x40)
  pci.device_protocol = 0 (0x0)
  pci.vendor = 'nVidia Corporation'
  info.vendor = 'nVidia Corporation'

  101: udi = '/org/freedesktop/Hal/devices/pci_10de_541'
  pci.product = 'MCP67 Memory Controller'
  pci.subsys_vendor = 'Hewlett-Packard Company'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'pci'
  info.udi = '/org/freedesktop/Hal/devices/pci_10de_541'
  info.subsystem = 'pci'
  info.product = 'MCP67 Memory Controller'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:01.2'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:01.2'
  pci.product_id = 1345 (0x541)
  pci.vendor_id = 4318 (0x10de)
  pci.subsys_product_id = 12495 (0x30cf)
  pci.subsys_vendor_id = 4156 (0x103c)
  pci.device_class = 5 (0x5)
  pci.device_subclass = 0 (0x0)
  pci.device_protocol = 0 (0x0)
  pci.vendor = 'nVidia Corporation'
  info.vendor = 'nVidia Corporation'

  102: udi = '/org/freedesktop/Hal/devices/pci_10de_542'
  pci.product = 'MCP67 SMBus'
  pci.subsys_vendor = 'Hewlett-Packard Company'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'pci'
  info.linux.driver = 'nForce2_smbus'
  info.udi = '/org/freedesktop/Hal/devices/pci_10de_542'
  info.subsystem = 'pci'
  info.product = 'MCP67 SMBus'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:01.1'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:01.1'
  pci.product_id = 1346 (0x542)
  pci.vendor_id = 4318 (0x10de)
  pci.subsys_product_id = 12495 (0x30cf)
  pci.subsys_vendor_id = 4156 (0x103c)
  pci.device_class = 12 (0xc)
  pci.device_subclass = 5 (0x5)
  pci.device_protocol = 0 (0x0)
  pci.vendor = 'nVidia Corporation'
  info.vendor = 'nVidia Corporation'

  103: udi = '/org/freedesktop/Hal/devices/pci_10de_548'
  pci.product = 'MCP67 ISA Bridge'
  pci.subsys_vendor = 'Hewlett-Packard Company'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'pci'
  info.udi = '/org/freedesktop/Hal/devices/pci_10de_548'
  info.subsystem = 'pci'
  info.product = 'MCP67 ISA Bridge'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:01.0'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:01.0'
  pci.product_id = 1352 (0x548)
  pci.vendor_id = 4318 (0x10de)
  pci.subsys_product_id = 12495 (0x30cf)
  pci.subsys_vendor_id = 4156 (0x103c)
  pci.device_class = 6 (0x6)
  pci.device_subclass = 1 (0x1)
  pci.device_protocol = 0 (0x0)
  pci.vendor = 'nVidia Corporation'
  info.vendor = 'nVidia Corporation'

  104: udi = '/org/freedesktop/Hal/devices/pci_10de_547'
  pci.product = 'MCP67 Memory Controller'
  pci.subsys_vendor = 'Hewlett-Packard Company'
  linux.hotplug_type = 2 (0x2)
  linux.subsystem = 'pci'
  info.udi = '/org/freedesktop/Hal/devices/pci_10de_547'
  info.subsystem = 'pci'
  info.product = 'MCP67 Memory Controller'
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:00.0'
  info.parent = '/org/freedesktop/Hal/devices/computer'
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:00.0'
  pci.product_id = 1351 (0x547)
  pci.vendor_id = 4318 (0x10de)
  pci.subsys_product_id = 12495 (0x30cf)
  pci.subsys_vendor_id = 4156 (0x103c)
  pci.device_class = 5 (0x5)
  pci.device_subclass = 0 (0x0)
  pci.device_protocol = 0 (0x0)
  pci.vendor = 'nVidia Corporation'
  info.vendor = 'nVidia Corporation'
----- hal device list end -----
>> floppy.1: get nvram
>> floppy.2: klog info
>> bios.1: cmdline
>> bios.1.1: apm
>> bios.2: ram
  bios: 0 disks
>> bios.2: rom
>> bios.3: smp
----- BIOS data 0x00400 - 0x004ff -----
  400  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  410  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  420  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  430  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  440  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  450  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  460  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  470  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  480  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  490  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  4a0  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  4b0  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  4c0  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  4d0  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  4e0  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  4f0  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
----- BIOS data end -----
>> bios.4: vbe
VBE: Could not init Int10
>> bios.5: 32
>> bios.6: acpi
>> sys.1: cpu
  vm check: vm_1 = 0, vm_2 = -1
  is_vmware = 0, has_vmware_mouse = 0
>> misc.9: kernel log
----- kernel log -----
  <6>[11496.724009] PM: Need to copy 377523 pages
  <7>[11496.724009] PM: Normal pages needed: 59060 + 1024, available pages: 169097
  <6>[11496.724009] PM: Restoring platform NVS memory
  <6>[11496.724009] Extended CMOS year: 2000
  <4>[11496.724009] Enabling non-boot CPUs ...
  <6>[11496.724009] Booting Node 0 Processor 1 APIC 0x1
  <6>[11496.618673] Initializing CPU#1
  <6>[11496.618673] Switch to broadcast mode on CPU1
  <6>[11496.816032] Switched to NOHz mode on CPU #1
  <4>[11496.816096] CPU1 is up
  <6>[11496.816267] ACPI: Waking up from system sleep state S4
  <7>[11496.817330] pata_amd 0000:00:06.0: restoring config space at offset 0x1 (was 0xb00001, writing 0xb00005)
  <7>[11496.817355] HDA Intel 0000:00:07.0: restoring config space at offset 0x1 (was 0xb00006, writing 0xb00002)
  <6>[11496.817413] pci 0000:00:00.0: Found enabled HT MSI Mapping
  <6>[11496.817482] pci 0000:00:00.0: Found enabled HT MSI Mapping
  <7>[11496.817498] ahci 0000:00:09.0: restoring config space at offset 0x1 (was 0xb00003, writing 0xb00007)
  <6>[11496.817560] pci 0000:00:00.0: Found enabled HT MSI Mapping
  <6>[11496.817644] pci 0000:00:00.0: Found enabled HT MSI Mapping
  <6>[11496.817735] pci 0000:00:00.0: Found enabled HT MSI Mapping
  <6>[11496.817829] pci 0000:00:00.0: Found enabled HT MSI Mapping
  <6>[11496.832024] firewire_ohci 0000:02:05.0: BAR 0: set to [mem 0xf6100000-0xf61007ff] (PCI address [0xf6100000-0xf61007ff])
  <7>[11496.832042] firewire_ohci 0000:02:05.0: restoring config space at offset 0x3 (was 0x800000, writing 0x804010)
  <7>[11496.832048] firewire_ohci 0000:02:05.0: restoring config space at offset 0x1 (was 0x2100000, writing 0x2100106)
  <6>[11496.848023] sdhci-pci 0000:02:05.1: BAR 0: set to [mem 0xf6100800-0xf61008ff] (PCI address [0xf6100800-0xf61008ff])
  <7>[11496.848042] sdhci-pci 0000:02:05.1: restoring config space at offset 0x3 (was 0x800000, writing 0x804010)
  <7>[11496.848048] sdhci-pci 0000:02:05.1: restoring config space at offset 0x1 (was 0x2100000, writing 0x2100106)
  <6>[11496.848624] PM: early restore of devices complete after 31.694 msecs
  <7>[11496.978443] ohci_hcd 0000:00:02.0: setting latency timer to 64
  <7>[11496.978467] ehci_hcd 0000:00:02.1: setting latency timer to 64
  <7>[11496.978495] ohci_hcd 0000:00:04.0: setting latency timer to 64
  <7>[11496.978518] ehci_hcd 0000:00:04.1: setting latency timer to 64
  <7>[11496.978548] pata_amd 0000:00:06.0: setting latency timer to 64
  <6>[11496.978566] HDA Intel 0000:00:07.0: PCI INT A -> Link[LAZA] -> GSI 21 (level, low) -> IRQ 21
  <7>[11496.978572] HDA Intel 0000:00:07.0: setting latency timer to 64
  <7>[11496.978570] pci 0000:00:08.0: setting latency timer to 64
  <6>[11496.978589] ahci 0000:00:09.0: PCI INT A -> Link[LSI0] -> GSI 23 (level, low) -> IRQ 23
  <7>[11496.978594] ahci 0000:00:09.0: setting latency timer to 64
  <6>[11496.979310] sdhci-pci 0000:02:05.1: PCI INT B -> Link[LNK2] -> GSI 7 (level, low) -> IRQ 7
  <4>[11496.979314] sdhci-pci 0000:02:05.1: Will use DMA mode even though HW doesn't fully claim to support it.
  <5>[11496.980686] sd 2:0:0:0: [sda] Starting disk
  <7>[11496.980944] ata2: port disabled. ignoring.
  <4>[11497.034013] usb usb3: root hub lost power or was reset
  <4>[11497.036019] usb usb4: root hub lost power or was reset
  <4>[11497.036101] usb usb1: root hub lost power or was reset
  <7>[11497.036109] ehci_hcd 0000:00:02.1: cache line size of 64 is not supported
  <4>[11497.036150] usb usb2: root hub lost power or was reset
  <7>[11497.036158] ehci_hcd 0000:00:04.1: cache line size of 64 is not supported
  <5>[11497.036161] firewire_core: skipped bus generations, destroying all nodes
  <6>[11497.160301] ata1.00: ACPI cmd ef/03:22:00:00:00:a0 (SET FEATURES) filtered out
  <6>[11497.160305] ata1.00: ACPI cmd ef/03:0c:00:00:00:a0 (SET FEATURES) filtered out
  <7>[11497.160316] ata1: nv_mode_filter: 0x39f&0x739f->0x39f, BIOS=0x0 (0xc600) ACPI=0x39f (120:600:0x12)
  <6>[11497.168033] PM: restore of drv:usb dev:usb2 complete after 187.607 msecs
  <6>[11497.168054] PM: restore of drv:usb dev:usb1 complete after 187.705 msecs
  <6>[11497.168063] PM: restore of drv:hub dev:2-0:1.0 complete after 187.622 msecs
  <6>[11497.168071] PM: restore of drv: dev:ep_00 complete after 187.596 msecs
  <6>[11497.168077] PM: restore of drv:hub dev:1-0:1.0 complete after 187.708 msecs
  <6>[11497.168085] PM: restore of drv: dev:ep_00 complete after 187.678 msecs
  <6>[11497.168090] PM: restore of drv: dev:ep_81 complete after 187.632 msecs
  <6>[11497.168096] PM: restore of drv: dev:ep_81 complete after 187.708 msecs
  <6>[11497.192235] ata1.00: configured for MWDMA2
  <6>[11497.232041] PM: restore of drv:usb dev:usb3 complete after 251.548 msecs
  <6>[11497.232051] PM: restore of drv:hub dev:3-0:1.0 complete after 251.540 msecs
  <6>[11497.232059] PM: restore of drv: dev:ep_00 complete after 251.514 msecs
  <6>[11497.232065] PM: restore of drv: dev:ep_81 complete after 251.538 msecs
  <6>[11497.244272] PM: restore of drv:battery dev:PNP0C0A:00 complete after 262.687 msecs
  <6>[11497.245052] i8042 kbd 00:09: wake-up capability disabled by ACPI
  <6>[11497.300027] ata5: SATA link down (SStatus 0 SControl 300)
  <6>[11497.300043] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
  <6>[11497.300055] ata4: SATA link down (SStatus 0 SControl 300)
  <6>[11497.300066] ata6: SATA link down (SStatus 0 SControl 300)
  <6>[11497.305045] ata3.00: configured for UDMA/100
  <6>[11497.327154] PM: restore of drv:sd dev:2:0:0:0 complete after 346.467 msecs
  <6>[11497.327165] PM: restore of drv:scsi_device dev:2:0:0:0 complete after 346.437 msecs
  <6>[11497.336032] PM: restore of drv:usb dev:usb4 complete after 355.469 msecs
  <6>[11497.336043] PM: restore of drv:hub dev:4-0:1.0 complete after 355.462 msecs
  <6>[11497.336050] PM: restore of drv: dev:ep_00 complete after 355.435 msecs
  <6>[11497.336056] PM: restore of drv: dev:ep_81 complete after 355.458 msecs
  <6>[11497.500482] PM: restore of drv:forcedeth dev:0000:00:0a.0 complete after 521.872 msecs
  <6>[11497.500490] PM: restore of drv:net dev:eth0 complete after 246.812 msecs
  <5>[11497.991868] firewire_core: rediscovered device fw0
  <6>[11499.873919] PM: restore of drv:nvidia dev:0000:00:12.0 complete after 2895.243 msecs
  <6>[11499.873949] PM: restore of drv:i2c dev:i2c-2 complete after 2371.739 msecs
  <6>[11499.873972] PM: restore of devices complete after 2895.602 msecs
  <7>[11499.874204] PM: Image restored successfully.
  <4>[11499.874206] Restarting tasks ... done.
  <7>[11499.888323] PM: Basic memory bitmaps freed
  <6>[11499.888336] video LNXVIDEO:00: Restoring backlight state
  <6>[11501.751214] mmc0: new SD card at address 0002
  <6>[11501.900085] mmcblk0: mmc0:0002 00000 974 MiB 
  <6>[11501.902891]  mmcblk0: p1
  <3>[11509.693731] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
  <3>[11509.693737] ata3.00: irq_stat 0x40000001
  <3>[11509.693741] ata3.00: failed command: READ DMA
  <3>[11509.693749] ata3.00: cmd c8/00:10:08:2f:f6/00:00:00:00:00/e0 tag 0 dma 8192 in
  <3>[11509.693751]          res 51/40:07:14:2f:f6/00:00:00:00:00/e0 Emask 0x9 (media error)
  <3>[11509.693754] ata3.00: status: { DRDY ERR }
  <3>[11509.693757] ata3.00: error: { UNC }
  <6>[11509.699095] ata3.00: configured for UDMA/100
  <6>[11509.699105] ata3: EH complete
  <7>[11510.507977] forcedeth 0000:00:0a.0: irq 42 for MSI/MSI-X
  <6>[11510.508238] forcedeth 0000:00:0a.0: eth0: no link during initialization
  <6>[11510.508921] ADDRCONF(NETDEV_UP): eth0: link is not ready
  <6>[11510.524265] ADDRCONF(NETDEV_UP): wlan0: link is not ready
  <7>[11512.943532] wlan0: authenticate with c0:3f:0e:fb:56:88 (try 1)
  <7>[11512.945148] wlan0: authenticated
  <7>[11512.945205] wlan0: associate with c0:3f:0e:fb:56:88 (try 1)
  <7>[11512.947587] wlan0: RX AssocResp from c0:3f:0e:fb:56:88 (capab=0x411 status=0 aid=4)
  <7>[11512.947593] wlan0: associated
  <6>[11512.948451] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
  <6>[11513.833596] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
  <7>[11523.200058] wlan0: no IPv6 routers present
  <6>[15303.244174] mmc0: card 0002 removed
  <6>[15388.538346] lp: driver loaded but no devices found
  <6>[15388.561336] st: Version 20101219, fixed bufsize 32768, s/g segs 256
  <6>[15537.792357] lp: driver loaded but no devices found
----- kernel log end -----
>> misc.1: misc data
>> misc.1.1: open serial
>> misc.1.2: open parallel
----- exec: "/sbin/rmmod lp" -----
  ERROR: Removing 'lp': Operation not permitted
----- return code: ? -----
----- exec: "/sbin/rmmod parport_pc" -----
  ERROR: Removing 'parport_pc': Operation not permitted
----- return code: ? -----
----- exec: "/sbin/rmmod parport" -----
  ERROR: Module parport is in use by lp,parport_pc,ppdev
----- return code: ? -----
>> misc.2.1: io
>> misc.2.2: dma
>> misc.2.3: irq
----- /proc/ioports -----
  0000-0cf7 : PCI Bus 0000:00
    0000-001f : dma1
    0020-0021 : pic1
    0040-0043 : timer0
    0050-0053 : timer1
    0060-0060 : keyboard
    0062-0062 : EC data
    0064-0064 : keyboard
    0066-0066 : EC cmd
    0070-0071 : rtc0
    0080-008f : dma page reg
    00a0-00a1 : pic2
    00c0-00df : dma2
    00f0-00ff : fpu
    0170-0177 : 0000:00:06.0
      0170-0177 : pata_amd
    01f0-01f7 : 0000:00:06.0
      01f0-01f7 : pata_amd
    0360-0361 : pnp 00:04
    0376-0376 : 0000:00:06.0
      0376-0376 : pata_amd
    03c0-03df : vesafb
    03f6-03f6 : 0000:00:06.0
      03f6-03f6 : pata_amd
    04d0-04d1 : pnp 00:04
  0cf8-0cff : PCI conf1
  0d00-ffff : PCI Bus 0000:00
    1000-107f : pnp 00:03
      1000-1003 : ACPI PM1a_EVT_BLK
      1004-1005 : ACPI PM1a_CNT_BLK
      1008-100b : ACPI PM_TMR
      1010-1015 : ACPI CPU throttle
      1020-1027 : ACPI GPE0_BLK
    1080-10ff : pnp 00:03
    1400-147f : pnp 00:03
    1480-14ff : pnp 00:03
      1484-1484 : ACPI PM2_CNT_BLK
    1800-187f : pnp 00:03
    1880-18ff : pnp 00:03
    3000-303f : 0000:00:01.1
      3000-303f : nForce2_smbus
    3040-307f : 0000:00:01.1
      3040-307f : nForce2_smbus
    3080-30bf : 0000:00:01.1
    30c0-30cf : 0000:00:06.0
      30c0-30cf : pata_amd
    30d0-30df : 0000:00:09.0
      30d0-30df : ahci
    30e0-30e3 : 0000:00:09.0
      30e0-30e3 : ahci
    30e4-30e7 : 0000:00:09.0
      30e4-30e7 : ahci
    30e8-30ef : 0000:00:09.0
      30e8-30ef : ahci
    30f0-30f7 : 0000:00:09.0
      30f0-30f7 : ahci
    30f8-30ff : 0000:00:0a.0
      30f8-30ff : forcedeth
    4000-4fff : PCI Bus 0000:04
----- /proc/ioports end -----
----- /proc/interrupts -----
    0:    5338559    1253144   IO-APIC-edge      timer
    1:      10246       4410   IO-APIC-edge      i8042
    5:        235         20   IO-APIC-fasteoi   firewire_ohci
    7:        238       4294   IO-APIC-fasteoi   r852, mmc0
    8:          0          1   IO-APIC-edge      rtc0
    9:     230698       3032   IO-APIC-fasteoi   acpi
   12:    3537997      10254   IO-APIC-edge      i8042
   14:      11156      76332   IO-APIC-edge      pata_amd
   15:          0          0   IO-APIC-edge      pata_amd
   16:     538214     504285   IO-APIC-fasteoi   nvidia
   18:          8          0   IO-APIC-fasteoi   ohci_hcd:usb3, ohci_hcd:usb4
   19:     894359        777   IO-APIC-fasteoi   ath
   21:       1042        122   IO-APIC-fasteoi   hda_intel
   22:          0      15529   IO-APIC-fasteoi   ehci_hcd:usb1, ehci_hcd:usb2
   23:     144712       3866   IO-APIC-fasteoi   ahci
   42:          0          0   PCI-MSI-edge      eth0
  NMI:          0          0   Non-maskable interrupts
  LOC:    3593343    5519327   Local timer interrupts
  SPU:          0          0   Spurious interrupts
  PMI:          0          0   Performance monitoring interrupts
  IWI:          0          0   IRQ work interrupts
  RES:    1764517    2137589   Rescheduling interrupts
  CAL:     307098     321964   Function call interrupts
  TLB:     103679     119906   TLB shootdowns
  TRM:          0          0   Thermal event interrupts
  THR:          0          0   Threshold APIC interrupts
  MCE:          0          0   Machine check exceptions
  MCP:         57         54   Machine check polls
  ERR:          1
  MIS:          0
----- /proc/interrupts end -----
----- /proc/dma -----
   4: cascade
----- /proc/dma end -----
>> misc.3: FPU
>> misc.3.1: DMA
>> misc.3.2: PIC
>> misc.3.3: timer
>> misc.3.4: RTC
>> cpu.1: cpuinfo
----- /proc/cpuinfo -----
  processor	: 0
  vendor_id	: AuthenticAMD
  cpu family	: 15
  model		: 104
  model name	: AMD Turion(tm) 64 X2 Mobile Technology TL-60
  stepping	: 2
  cpu MHz		: 800.000
  cache size	: 512 KB
  physical id	: 0
  siblings	: 2
  core id		: 0
  cpu cores	: 2
  apicid		: 0
  initial apicid	: 0
  fdiv_bug	: no
  hlt_bug		: no
  f00f_bug	: no
  coma_bug	: no
  fpu		: yes
  fpu_exception	: yes
  cpuid level	: 1
  wp		: yes
  flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow extd_apicid pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch lbrv
  bogomips	: 1600.04
  clflush size	: 64
  cache_alignment	: 64
  address sizes	: 40 bits physical, 48 bits virtual
  power management: ts fid vid ttp tm stc 100mhzsteps
  
  processor	: 1
  vendor_id	: AuthenticAMD
  cpu family	: 15
  model		: 104
  model name	: AMD Turion(tm) 64 X2 Mobile Technology TL-60
  stepping	: 2
  cpu MHz		: 800.000
  cache size	: 512 KB
  physical id	: 0
  siblings	: 2
  core id		: 1
  cpu cores	: 2
  apicid		: 1
  initial apicid	: 1
  fdiv_bug	: no
  hlt_bug		: no
  f00f_bug	: no
  coma_bug	: no
  fpu		: yes
  fpu_exception	: yes
  cpuid level	: 1
  wp		: yes
  flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow extd_apicid pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch lbrv
  bogomips	: 1600.04
  clflush size	: 64
  cache_alignment	: 64
  address sizes	: 40 bits physical, 48 bits virtual
  power management: ts fid vid ttp tm stc 100mhzsteps
  
----- /proc/cpuinfo end -----
>> memory.1: main memory size
  kcore mem:  0x3fbfe000
  klog mem 0: 0x0
  klog mem 1: 0x0
  klog mem:   0x0
  bios mem:   0x0
  meminfo:    0xeb7f4000
>> pci.1: sysfs drivers
----- sysfs driver list (id 0x6b4541a3496a6183) -----
      serial8250: /devices/platform/serial8250
           i8042: /devices/platform/i8042
          hp-wmi: module = hp_wmi
          hp-wmi: /devices/platform/hp-wmi
          vesafb: /devices/platform/vesafb.0
      parport_pc: module = parport_pc
        pcieport: /devices/pci0000:00/0000:00:0c.0
        pcieport: /devices/pci0000:00/0000:00:0d.0
      virtio-pci: module = virtio_pci
       sym53c8xx: module = sym53c8xx
        pdc_adma: module = pdc_adma
        ata_piix: module = ata_piix
        pata_sis: module = pata_sis
       pata_acpi: module = pata_acpi
     ata_generic: module = ata_generic
        ehci_hcd: /devices/pci0000:00/0000:00:02.1
        ehci_hcd: /devices/pci0000:00/0000:00:04.1
        ehci_hcd: module = ehci_hcd
        ohci_hcd: /devices/pci0000:00/0000:00:02.0
        ohci_hcd: /devices/pci0000:00/0000:00:04.0
        uhci_hcd: module = uhci_hcd
       forcedeth: /devices/pci0000:00/0000:00:0a.0
       forcedeth: module = forcedeth
        pata_amd: /devices/pci0000:00/0000:00:06.0
        pata_amd: module = pata_amd
       sdhci-pci: /devices/pci0000:00/0000:00:08.0/0000:02:05.1
       sdhci-pci: module = sdhci_pci
   firewire_ohci: /devices/pci0000:00/0000:00:08.0/0000:02:05.0
   firewire_ohci: module = firewire_ohci
            ahci: /devices/pci0000:00/0000:00:09.0
            ahci: module = ahci
          k8temp: /devices/pci0000:00/0000:00:18.3
          k8temp: module = k8temp
   nForce2_smbus: /devices/pci0000:00/0000:00:01.1
   nForce2_smbus: module = i2c_nforce2
            r852: /devices/pci0000:00/0000:00:08.0/0000:02:05.3
            r852: module = r852
           ath5k: /devices/pci0000:00/0000:00:0d.0/0000:03:00.0
           ath5k: module = ath5k
       HDA Intel: /devices/pci0000:00/0000:00:07.0
       HDA Intel: module = snd_hda_intel
          nvidia: /devices/pci0000:00/0000:00:12.0
          nvidia: module = nvidia
      parport_pc: module = parport_pc
              ec: /devices/LNXSYSTM:00/device:00/PNP0A08:00/PNP0C09:00
        pci_root: /devices/LNXSYSTM:00/device:00/PNP0A08:00
        pci_link: /devices/LNXSYSTM:00/device:00/PNP0A08:00/PNP0C0F:00
        pci_link: /devices/LNXSYSTM:00/device:00/PNP0A08:00/PNP0C0F:01
        pci_link: /devices/LNXSYSTM:00/device:00/PNP0A08:00/PNP0C0F:02
        pci_link: /devices/LNXSYSTM:00/device:00/PNP0A08:00/PNP0C0F:03
        pci_link: /devices/LNXSYSTM:00/device:00/PNP0A08:00/PNP0C0F:04
        pci_link: /devices/LNXSYSTM:00/device:00/PNP0A08:00/PNP0C0F:05
        pci_link: /devices/LNXSYSTM:00/device:00/PNP0A08:00/PNP0C0F:06
        pci_link: /devices/LNXSYSTM:00/device:00/PNP0A08:00/PNP0C0F:07
        pci_link: /devices/LNXSYSTM:00/device:00/PNP0A08:00/PNP0C0F:08
        pci_link: /devices/LNXSYSTM:00/device:00/PNP0A08:00/PNP0C0F:09
        pci_link: /devices/LNXSYSTM:00/device:00/PNP0A08:00/PNP0C0F:0a
        pci_link: /devices/LNXSYSTM:00/device:00/PNP0A08:00/PNP0C0F:0b
        pci_link: /devices/LNXSYSTM:00/device:00/PNP0A08:00/PNP0C0F:0c
        pci_link: /devices/LNXSYSTM:00/device:00/PNP0A08:00/PNP0C0F:0d
        pci_link: /devices/LNXSYSTM:00/device:00/PNP0A08:00/PNP0C0F:0e
        pci_link: /devices/LNXSYSTM:00/device:00/PNP0A08:00/PNP0C0F:0f
        pci_link: /devices/LNXSYSTM:00/device:00/PNP0A08:00/PNP0C0F:10
        pci_link: /devices/LNXSYSTM:00/device:00/PNP0A08:00/PNP0C0F:11
        pci_link: /devices/LNXSYSTM:00/device:00/PNP0A08:00/PNP0C0F:12
             wmi: /devices/LNXSYSTM:00/device:00/PNP0C14:00
              ac: /devices/LNXSYSTM:00/device:00/ACPI0003:00
          button: /devices/LNXSYSTM:00/device:00/PNP0C0E:00
          button: /devices/LNXSYSTM:00/device:00/PNP0C0D:00
          button: /devices/LNXSYSTM:00/device:00/PNP0C0C:00
          button: /devices/LNXSYSTM:00/LNXPWRBN:00
       processor: /devices/LNXSYSTM:00/LNXCPU:00
       processor: /devices/LNXSYSTM:00/LNXCPU:01
         thermal: /devices/LNXSYSTM:00/device:28/LNXTHERM:00
         battery: /devices/LNXSYSTM:00/device:00/PNP0C0A:00
           video: /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00
          system: /devices/pnp0/00:02
          system: /devices/pnp0/00:03
          system: /devices/pnp0/00:04
          system: /devices/pnp0/00:0b
       i8042 kbd: /devices/pnp0/00:09
       i8042 aux: /devices/pnp0/00:0a
        rtc_cmos: /devices/pnp0/00:07
              sd: /devices/pci0000:00/0000:00:09.0/host2/target2:0:0/2:0:0:0
              sr: /devices/pci0000:00/0000:00:06.0/host0/target0:0:0/0:0:0:0
           usbfs: module = usbcore
             hub: module = usbcore
             hub: /devices/pci0000:00/0000:00:02.1/usb1/1-0:1.0
             hub: /devices/pci0000:00/0000:00:04.1/usb2/2-0:1.0
             hub: /devices/pci0000:00/0000:00:02.0/usb3/3-0:1.0
             hub: /devices/pci0000:00/0000:00:04.0/usb4/4-0:1.0
             usb: /devices/pci0000:00/0000:00:02.1/usb1
             usb: /devices/pci0000:00/0000:00:04.1/usb2
             usb: /devices/pci0000:00/0000:00:02.0/usb3
             usb: /devices/pci0000:00/0000:00:04.0/usb4
             uas: module = uas
     usb-storage: module = usb_storage
           atkbd: /devices/platform/i8042/serio0
       serio_raw: module = serio_raw
         psmouse: module = psmouse
         psmouse: /devices/platform/i8042/serio1
----- sysfs driver list end -----
>> pci.2: get sysfs pci data
  pci device: name = 0000:00:00.0
    path = /devices/pci0000:00/0000:00:00.0
    modalias = "pci:v000010DEd00000547sv0000103Csd000030CFbc05sc00i00"
    class = 0x50000
    vendor = 0x10de
    device = 0x547
    subvendor = 0x103c
    subdevice = 0x30cf
    irq = 0
    config[64]
  pci device: name = 0000:00:01.0
    path = /devices/pci0000:00/0000:00:01.0
    modalias = "pci:v000010DEd00000548sv0000103Csd000030CFbc06sc01i00"
    class = 0x60100
    vendor = 0x10de
    device = 0x548
    subvendor = 0x103c
    subdevice = 0x30cf
    irq = 0
    config[64]
  pci device: name = 0000:00:01.1
    path = /devices/pci0000:00/0000:00:01.1
    modalias = "pci:v000010DEd00000542sv0000103Csd000030CFbc0Csc05i00"
    class = 0xc0500
    vendor = 0x10de
    device = 0x542
    subvendor = 0x103c
    subdevice = 0x30cf
    irq = 10
    res[0] = 0x3080 0x30bf 0x40101
    res[4] = 0x3040 0x307f 0x40101
    res[5] = 0x3000 0x303f 0x40101
    config[64]
  pci device: name = 0000:00:01.2
    path = /devices/pci0000:00/0000:00:01.2
    modalias = "pci:v000010DEd00000541sv0000103Csd000030CFbc05sc00i00"
    class = 0x50000
    vendor = 0x10de
    device = 0x541
    subvendor = 0x103c
    subdevice = 0x30cf
    irq = 0
    config[64]
  pci device: name = 0000:00:01.3
    path = /devices/pci0000:00/0000:00:01.3
    modalias = "pci:v000010DEd00000543sv0000103Csd000030CFbc0Bsc40i00"
    class = 0xb4000
    vendor = 0x10de
    device = 0x543
    subvendor = 0x103c
    subdevice = 0x30cf
    irq = 11
    res[0] = 0xf6200000 0xf627ffff 0x40200
    config[64]
  pci device: name = 0000:00:02.0
    path = /devices/pci0000:00/0000:00:02.0
    modalias = "pci:v000010DEd0000055Esv0000103Csd000030CFbc0Csc03i10"
    class = 0xc0310
    vendor = 0x10de
    device = 0x55e
    subvendor = 0x103c
    subdevice = 0x30cf
    irq = 18
    res[0] = 0xf6486000 0xf6486fff 0x40200
    config[64]
  pci device: name = 0000:00:02.1
    path = /devices/pci0000:00/0000:00:02.1
    modalias = "pci:v000010DEd0000055Fsv0000103Csd000030CFbc0Csc03i20"
    class = 0xc0320
    vendor = 0x10de
    device = 0x55f
    subvendor = 0x103c
    subdevice = 0x30cf
    irq = 22
    res[0] = 0xf6489000 0xf64890ff 0x40200
    config[64]
  pci device: name = 0000:00:04.0
    path = /devices/pci0000:00/0000:00:04.0
    modalias = "pci:v000010DEd0000055Esv0000103Csd000030CFbc0Csc03i10"
    class = 0xc0310
    vendor = 0x10de
    device = 0x55e
    subvendor = 0x103c
    subdevice = 0x30cf
    irq = 18
    res[0] = 0xf6487000 0xf6487fff 0x40200
    config[64]
  pci device: name = 0000:00:04.1
    path = /devices/pci0000:00/0000:00:04.1
    modalias = "pci:v000010DEd0000055Fsv0000103Csd000030CFbc0Csc03i20"
    class = 0xc0320
    vendor = 0x10de
    device = 0x55f
    subvendor = 0x103c
    subdevice = 0x30cf
    irq = 22
    res[0] = 0xf6489400 0xf64894ff 0x40200
    config[64]
  pci device: name = 0000:00:06.0
    path = /devices/pci0000:00/0000:00:06.0
    modalias = "pci:v000010DEd00000560sv0000103Csd000030CFbc01sc01i8a"
    class = 0x1018a
    vendor = 0x10de
    device = 0x560
    subvendor = 0x103c
    subdevice = 0x30cf
    irq = 0
    res[0] = 0x1f0 0x1f7 0x110
    res[1] = 0x3f6 0x3f6 0x110
    res[2] = 0x170 0x177 0x110
    res[3] = 0x376 0x376 0x110
    res[4] = 0x30c0 0x30cf 0x40101
    config[64]
  pci device: name = 0000:00:07.0
    path = /devices/pci0000:00/0000:00:07.0
    modalias = "pci:v000010DEd0000055Csv0000103Csd000030CFbc04sc03i00"
    class = 0x40300
    vendor = 0x10de
    device = 0x55c
    subvendor = 0x103c
    subdevice = 0x30cf
    irq = 21
    res[0] = 0xf6480000 0xf6483fff 0x40200
    config[64]
  pci device: name = 0000:00:08.0
    path = /devices/pci0000:00/0000:00:08.0
    modalias = "pci:v000010DEd00000561sv000010DEsd0000CB84bc06sc04i01"
    class = 0x60401
    vendor = 0x10de
    device = 0x561
    subvendor = 0x10de
    subdevice = 0xcb84
    irq = 0
    config[64]
  pci device: name = 0000:00:09.0
    path = /devices/pci0000:00/0000:00:09.0
    modalias = "pci:v000010DEd00000550sv0000103Csd000030CFbc01sc01i85"
    class = 0x10185
    vendor = 0x10de
    device = 0x550
    subvendor = 0x103c
    subdevice = 0x30cf
    irq = 23
    res[0] = 0x30f0 0x30f7 0x40101
    res[1] = 0x30e4 0x30e7 0x40101
    res[2] = 0x30e8 0x30ef 0x40101
    res[3] = 0x30e0 0x30e3 0x40101
    res[4] = 0x30d0 0x30df 0x40101
    res[5] = 0xf6484000 0xf6485fff 0x40200
    config[64]
  pci device: name = 0000:00:0a.0
    path = /devices/pci0000:00/0000:00:0a.0
    modalias = "pci:v000010DEd0000054Csv0000103Csd000030CFbc02sc00i00"
    class = 0x20000
    vendor = 0x10de
    device = 0x54c
    subvendor = 0x103c
    subdevice = 0x30cf
    irq = 42
    res[0] = 0xf6488000 0xf6488fff 0x40200
    res[1] = 0x30f8 0x30ff 0x40101
    res[2] = 0xf6489c00 0xf6489cff 0x40200
    res[3] = 0xf6489800 0xf648980f 0x40200
    config[64]
  pci device: name = 0000:00:0c.0
    path = /devices/pci0000:00/0000:00:0c.0
    modalias = "pci:v000010DEd00000563sv000010DEsd00000000bc06sc04i00"
    class = 0x60400
    vendor = 0x10de
    device = 0x563
    subvendor = 0x10de
    subdevice = 0x0
    irq = 40
    config[64]
  pci device: name = 0000:00:0d.0
    path = /devices/pci0000:00/0000:00:0d.0
    modalias = "pci:v000010DEd00000563sv000010DEsd00000000bc06sc04i00"
    class = 0x60400
    vendor = 0x10de
    device = 0x563
    subvendor = 0x10de
    subdevice = 0x0
    irq = 41
    config[64]
  pci device: name = 0000:00:12.0
    path = /devices/pci0000:00/0000:00:12.0
    modalias = "pci:v000010DEd00000531sv0000103Csd000030CFbc03sc00i00"
    class = 0x30000
    vendor = 0x10de
    device = 0x531
    subvendor = 0x103c
    subdevice = 0x30cf
    irq = 16
    res[0] = 0xf5000000 0xf5ffffff 0x40200
    res[1] = 0xd0000000 0xdfffffff 0x14220c
    res[3] = 0xf4000000 0xf4ffffff 0x140204
    res[6] = 0xf6280000 0xf629ffff 0x4e202
    config[64]
  pci device: name = 0000:00:18.0
    path = /devices/pci0000:00/0000:00:18.0
    modalias = "pci:v00001022d00001100sv00000000sd00000000bc06sc00i00"
    class = 0x60000
    vendor = 0x1022
    device = 0x1100
    subvendor = 0x0
    subdevice = 0x0
    irq = 0
    config[64]
  pci device: name = 0000:00:18.1
    path = /devices/pci0000:00/0000:00:18.1
    modalias = "pci:v00001022d00001101sv00000000sd00000000bc06sc00i00"
    class = 0x60000
    vendor = 0x1022
    device = 0x1101
    subvendor = 0x0
    subdevice = 0x0
    irq = 0
    config[64]
  pci device: name = 0000:00:18.2
    path = /devices/pci0000:00/0000:00:18.2
    modalias = "pci:v00001022d00001102sv00000000sd00000000bc06sc00i00"
    class = 0x60000
    vendor = 0x1022
    device = 0x1102
    subvendor = 0x0
    subdevice = 0x0
    irq = 0
    config[64]
  pci device: name = 0000:00:18.3
    path = /devices/pci0000:00/0000:00:18.3
    modalias = "pci:v00001022d00001103sv00000000sd00000000bc06sc00i00"
    class = 0x60000
    vendor = 0x1022
    device = 0x1103
    subvendor = 0x0
    subdevice = 0x0
    irq = 0
    config[64]
  pci device: name = 0000:02:05.0
    path = /devices/pci0000:00/0000:00:08.0/0000:02:05.0
    modalias = "pci:v00001180d00000832sv0000103Csd000030CFbc0Csc00i10"
    class = 0xc0010
    vendor = 0x1180
    device = 0x832
    subvendor = 0x103c
    subdevice = 0x30cf
    irq = 5
    res[0] = 0xf6100000 0xf61007ff 0x40200
    config[64]
  pci device: name = 0000:02:05.1
    path = /devices/pci0000:00/0000:00:08.0/0000:02:05.1
    modalias = "pci:v00001180d00000822sv0000103Csd000030CFbc08sc05i00"
    class = 0x80500
    vendor = 0x1180
    device = 0x822
    subvendor = 0x103c
    subdevice = 0x30cf
    irq = 7
    res[0] = 0xf6100800 0xf61008ff 0x40200
    config[64]
  pci device: name = 0000:02:05.2
    path = /devices/pci0000:00/0000:00:08.0/0000:02:05.2
    modalias = "pci:v00001180d00000592sv0000103Csd000030CFbc08sc80i00"
    class = 0x88000
    vendor = 0x1180
    device = 0x592
    subvendor = 0x103c
    subdevice = 0x30cf
    irq = 11
    res[0] = 0xf6101000 0xf61010ff 0x40200
    config[64]
  pci device: name = 0000:02:05.3
    path = /devices/pci0000:00/0000:00:08.0/0000:02:05.3
    modalias = "pci:v00001180d00000852sv0000103Csd000030CFbc08sc80i00"
    class = 0x88000
    vendor = 0x1180
    device = 0x852
    subvendor = 0x103c
    subdevice = 0x30cf
    irq = 7
    res[0] = 0xf6101400 0xf61014ff 0x40200
    config[64]
  pci device: name = 0000:03:00.0
    path = /devices/pci0000:00/0000:00:0d.0/0000:03:00.0
    modalias = "pci:v0000168Cd0000001Csv0000103Csd0000137Bbc02sc00i00"
    class = 0x20000
    vendor = 0x168c
    device = 0x1c
    subvendor = 0x103c
    subdevice = 0x137b
    irq = 19
    res[0] = 0xf6000000 0xf600ffff 0x140204
    config[64]
---------- PCI raw data ----------
bus 00, slot 00, func 0, vend:dev:s_vend:s_dev:rev 10de:0547:103c:30cf:a2
class 05, sub_class 00 prog_if 00, hdr 0, flags <>, irq 0
  00: de 10 47 05 06 00 b0 00 a2 00 00 05 00 00 00 00  "..G............."
  10: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  20: 00 00 00 00 00 00 00 00 00 00 00 00 3c 10 cf 30  "............<..0"
  30: 00 00 00 00 44 00 00 00 00 00 00 00 00 00 00 00  "....D..........."

bus 00, slot 01, func 0, vend:dev:s_vend:s_dev:rev 10de:0548:103c:30cf:a2
class 06, sub_class 01 prog_if 00, hdr 0, flags <>, irq 0
  00: de 10 48 05 0f 00 a0 20 a2 00 01 06 00 00 80 00  "..H.... ........"
  10: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  20: 00 00 00 00 00 00 00 00 00 00 00 00 3c 10 cf 30  "............<..0"
  30: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"

bus 00, slot 01, func 1, vend:dev:s_vend:s_dev:rev 10de:0542:103c:30cf:a2
class 0c, sub_class 05 prog_if 00, hdr 0, flags <>, irq 10
  addr0 00003080, size 00000040
  addr4 00003040, size 00000040
  addr5 00003000, size 00000040
  00: de 10 42 05 01 00 b0 00 a2 00 05 0c 00 00 80 00  "..B............."
  10: 81 30 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ".0.............."
  20: 41 30 00 00 01 30 00 00 00 00 00 00 3c 10 cf 30  "A0...0......<..0"
  30: 00 00 00 00 44 00 00 00 00 00 00 00 0a 01 00 00  "....D..........."

bus 00, slot 01, func 2, vend:dev:s_vend:s_dev:rev 10de:0541:103c:30cf:a2
class 05, sub_class 00 prog_if 00, hdr 0, flags <>, irq 0
  00: de 10 41 05 00 04 a0 00 a2 00 00 05 00 00 80 00  "..A............."
  10: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  20: 00 00 00 00 00 00 00 00 00 00 00 00 3c 10 cf 30  "............<..0"
  30: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"

bus 00, slot 01, func 3, vend:dev:s_vend:s_dev:rev 10de:0543:103c:30cf:a2
class 0b, sub_class 40 prog_if 00, hdr 0, flags <>, irq 11
  addr0 f6200000, size 00080000
  00: de 10 43 05 06 00 a0 00 a2 00 40 0b 00 00 80 00  "..C.......@....."
  10: 00 00 20 f6 00 00 00 00 00 00 00 00 00 00 00 00  ".. ............."
  20: 00 00 00 00 00 00 00 00 00 00 00 00 3c 10 cf 30  "............<..0"
  30: 00 00 00 00 00 00 00 00 00 00 00 00 0b 02 03 01  "................"

bus 00, slot 02, func 0, vend:dev:s_vend:s_dev:rev 10de:055e:103c:30cf:a2
class 0c, sub_class 03 prog_if 10, hdr 0, flags <>, irq 18
  addr0 f6486000, size 00001000
  00: de 10 5e 05 07 00 b0 00 a2 10 03 0c 00 00 80 00  "..^............."
  10: 00 60 48 f6 00 00 00 00 00 00 00 00 00 00 00 00  ".`H............."
  20: 00 00 00 00 00 00 00 00 00 00 00 00 3c 10 cf 30  "............<..0"
  30: 00 00 00 00 44 00 00 00 00 00 00 00 0b 01 03 01  "....D..........."

bus 00, slot 02, func 1, vend:dev:s_vend:s_dev:rev 10de:055f:103c:30cf:a2
class 0c, sub_class 03 prog_if 20, hdr 0, flags <>, irq 22
  addr0 f6489000, size 00000100
  00: de 10 5f 05 06 00 b0 00 a2 20 03 0c 00 00 80 00  ".._...... ......"
  10: 00 90 48 f6 00 00 00 00 00 00 00 00 00 00 00 00  "..H............."
  20: 00 00 00 00 00 00 00 00 00 00 00 00 3c 10 cf 30  "............<..0"
  30: 00 00 00 00 44 00 00 00 00 00 00 00 07 02 03 01  "....D..........."

bus 00, slot 04, func 0, vend:dev:s_vend:s_dev:rev 10de:055e:103c:30cf:a2
class 0c, sub_class 03 prog_if 10, hdr 0, flags <>, irq 18
  addr0 f6487000, size 00001000
  00: de 10 5e 05 07 00 b0 00 a2 10 03 0c 00 00 80 00  "..^............."
  10: 00 70 48 f6 00 00 00 00 00 00 00 00 00 00 00 00  ".pH............."
  20: 00 00 00 00 00 00 00 00 00 00 00 00 3c 10 cf 30  "............<..0"
  30: 00 00 00 00 44 00 00 00 00 00 00 00 05 01 03 01  "....D..........."

bus 00, slot 04, func 1, vend:dev:s_vend:s_dev:rev 10de:055f:103c:30cf:a2
class 0c, sub_class 03 prog_if 20, hdr 0, flags <>, irq 22
  addr0 f6489400, size 00000100
  00: de 10 5f 05 06 00 b0 00 a2 20 03 0c 00 00 80 00  ".._...... ......"
  10: 00 94 48 f6 00 00 00 00 00 00 00 00 00 00 00 00  "..H............."
  20: 00 00 00 00 00 00 00 00 00 00 00 00 3c 10 cf 30  "............<..0"
  30: 00 00 00 00 44 00 00 00 00 00 00 00 0a 02 03 01  "....D..........."

bus 00, slot 06, func 0, vend:dev:s_vend:s_dev:rev 10de:0560:103c:30cf:a1
class 01, sub_class 01 prog_if 8a, hdr 0, flags <>, irq 0
  addr0 000001f0, size 00000008
  addr1 000003f6, size 00000001
  addr2 00000170, size 00000008
  addr3 00000376, size 00000001
  addr4 000030c0, size 00000010
  00: de 10 60 05 05 00 b0 00 a1 8a 01 01 00 00 00 00  "..`............."
  10: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  20: c1 30 00 00 00 00 00 00 00 00 00 00 3c 10 cf 30  ".0..........<..0"
  30: 00 00 00 00 44 00 00 00 00 00 00 00 00 00 03 01  "....D..........."

bus 00, slot 07, func 0, vend:dev:s_vend:s_dev:rev 10de:055c:103c:30cf:a1
class 04, sub_class 03 prog_if 00, hdr 0, flags <>, irq 21
  addr0 f6480000, size 00004000
  00: de 10 5c 05 06 00 b0 00 a1 00 03 04 00 00 80 00  "..\............."
  10: 00 00 48 f6 00 00 00 00 00 00 00 00 00 00 00 00  "..H............."
  20: 00 00 00 00 00 00 00 00 00 00 00 00 3c 10 cf 30  "............<..0"
  30: 00 00 00 00 44 00 00 00 00 00 00 00 0a 01 02 05  "....D..........."

bus 00->02, slot 08, func 0, vend:dev:s_vend:s_dev:rev 10de:0561:10de:cb84:a2
class 06, sub_class 04 prog_if 01, hdr 1, flags <>, irq 0
  00: de 10 61 05 07 01 b0 00 a2 01 04 06 00 00 01 00  "..a............."
  10: 00 00 00 00 00 00 00 00 00 02 02 40 f0 00 80 22  "...........@...""
  20: 10 f6 10 f6 f0 ff 00 00 00 00 00 00 00 00 00 00  "................"
  30: 00 00 00 00 b8 00 00 00 00 00 00 00 ff 00 04 02  "................"

bus 00, slot 09, func 0, vend:dev:s_vend:s_dev:rev 10de:0550:103c:30cf:a2
class 01, sub_class 01 prog_if 85, hdr 0, flags <>, irq 23
  addr0 000030f0, size 00000008
  addr1 000030e4, size 00000004
  addr2 000030e8, size 00000008
  addr3 000030e0, size 00000004
  addr4 000030d0, size 00000010
  addr5 f6484000, size 00002000
  00: de 10 50 05 07 00 b0 00 a2 85 01 01 00 00 80 00  "..P............."
  10: f1 30 00 00 e5 30 00 00 e9 30 00 00 e1 30 00 00  ".0...0...0...0.."
  20: d1 30 00 00 00 40 48 f6 00 00 00 00 3c 10 cf 30  ".0...@H.....<..0"
  30: 00 00 00 00 44 00 00 00 00 00 00 00 0b 01 03 01  "....D..........."

bus 00, slot 0a, func 0, vend:dev:s_vend:s_dev:rev 10de:054c:103c:30cf:a2
class 02, sub_class 00 prog_if 00, hdr 0, flags <>, irq 42
  addr0 f6488000, size 00001000
  addr1 000030f8, size 00000008
  addr2 f6489c00, size 00000100
  addr3 f6489800, size 00000010
  00: de 10 4c 05 07 04 b0 00 a2 00 00 02 00 00 00 00  "..L............."
  10: 00 80 48 f6 f9 30 00 00 00 9c 48 f6 00 98 48 f6  "..H..0....H...H."
  20: 00 00 00 00 00 00 00 00 00 00 00 00 3c 10 cf 30  "............<..0"
  30: 00 00 00 00 44 00 00 00 00 00 00 00 0b 01 01 14  "....D..........."

bus 00->04, slot 0c, func 0, vend:dev:s_vend:s_dev:rev 10de:0563:10de:0000:a2
class 06, sub_class 04 prog_if 00, hdr 1, flags <>, irq 40
  00: de 10 63 05 07 05 10 00 a2 00 04 06 10 00 01 00  "..c............."
  10: 00 00 00 00 00 00 00 00 00 04 05 00 41 41 00 00  "............AA.."
  20: 00 f2 f0 f3 01 f0 f1 f1 00 00 00 00 00 00 00 00  "................"
  30: 00 00 00 00 40 00 00 00 00 00 00 00 ff 00 04 00  "....@..........."

bus 00->03, slot 0d, func 0, vend:dev:s_vend:s_dev:rev 10de:0563:10de:0000:a2
class 06, sub_class 04 prog_if 00, hdr 1, flags <>, irq 41
  00: de 10 63 05 07 05 10 00 a2 00 04 06 10 00 01 00  "..c............."
  10: 00 00 00 00 00 00 00 00 00 03 03 00 f1 01 00 20  "............... "
  20: 00 f6 00 f6 f1 ff 01 00 00 00 00 00 00 00 00 00  "................"
  30: 00 00 00 00 40 00 00 00 00 00 00 00 ff 00 04 00  "....@..........."

bus 00, slot 12, func 0, vend:dev:s_vend:s_dev:rev 10de:0531:103c:30cf:a2
class 03, sub_class 00 prog_if 00, hdr 0, flags <>, irq 16
  addr0 f5000000, size 01000000
  addr1 d0000000, size 10000000
  addr3 f4000000, size 01000000
  00: de 10 31 05 07 00 b0 00 a2 00 00 03 00 00 00 00  "..1............."
  10: 00 00 00 f5 0c 00 00 d0 00 00 00 00 04 00 00 f4  "................"
  20: 00 00 00 00 00 00 00 00 00 00 00 00 3c 10 cf 30  "............<..0"
  30: 00 00 00 00 48 00 00 00 00 00 00 00 0a 01 00 00  "....H..........."

bus 00, slot 18, func 0, vend:dev:s_vend:s_dev:rev 1022:1100:0000:0000:00
class 06, sub_class 00 prog_if 00, hdr 0, flags <>, irq 0
  00: 22 10 00 11 00 00 10 00 00 00 00 06 00 00 80 00  ""..............."
  10: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  20: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  30: 00 00 00 00 80 00 00 00 00 00 00 00 00 00 00 00  "................"

bus 00, slot 18, func 1, vend:dev:s_vend:s_dev:rev 1022:1101:0000:0000:00
class 06, sub_class 00 prog_if 00, hdr 0, flags <>, irq 0
  00: 22 10 01 11 00 00 00 00 00 00 00 06 00 00 80 00  ""..............."
  10: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  20: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  30: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"

bus 00, slot 18, func 2, vend:dev:s_vend:s_dev:rev 1022:1102:0000:0000:00
class 06, sub_class 00 prog_if 00, hdr 0, flags <>, irq 0
  00: 22 10 02 11 00 00 00 00 00 00 00 06 00 00 80 00  ""..............."
  10: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  20: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  30: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"

bus 00, slot 18, func 3, vend:dev:s_vend:s_dev:rev 1022:1103:0000:0000:00
class 06, sub_class 00 prog_if 00, hdr 0, flags <>, irq 0
  00: 22 10 03 11 00 00 10 00 00 00 00 06 00 00 80 00  ""..............."
  10: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  20: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  30: 00 00 00 00 f0 00 00 00 00 00 00 00 00 00 00 00  "................"

bus 02, slot 05, func 0, vend:dev:s_vend:s_dev:rev 1180:0832:103c:30cf:05
class 0c, sub_class 00 prog_if 10, hdr 0, flags <>, irq 5
  addr0 f6100000, size 00000800
  00: 80 11 32 08 06 01 10 02 05 10 00 0c 10 40 80 00  "..2..........@.."
  10: 00 00 10 f6 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  20: 00 00 00 00 00 00 00 00 00 00 00 00 3c 10 cf 30  "............<..0"
  30: 00 00 00 00 dc 00 00 00 00 00 00 00 0a 01 02 04  "................"

bus 02, slot 05, func 1, vend:dev:s_vend:s_dev:rev 1180:0822:103c:30cf:22
class 08, sub_class 05 prog_if 00, hdr 0, flags <>, irq 7
  addr0 f6100800, size 00000100
  00: 80 11 22 08 06 01 10 02 22 00 05 08 10 40 80 00  ".."....."....@.."
  10: 00 08 10 f6 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  20: 00 00 00 00 00 00 00 00 00 00 00 00 3c 10 cf 30  "............<..0"
  30: 00 00 00 00 80 00 00 00 00 00 00 00 0b 02 00 00  "................"

bus 02, slot 05, func 2, vend:dev:s_vend:s_dev:rev 1180:0592:103c:30cf:12
class 08, sub_class 80 prog_if 00, hdr 0, flags <>, irq 11
  addr0 f6101000, size 00000100
  00: 80 11 92 05 06 01 10 02 12 00 80 08 10 40 80 00  ".............@.."
  10: 00 10 10 f6 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  20: 00 00 00 00 00 00 00 00 00 00 00 00 3c 10 cf 30  "............<..0"
  30: 00 00 00 00 80 00 00 00 00 00 00 00 0b 02 00 00  "................"

bus 02, slot 05, func 3, vend:dev:s_vend:s_dev:rev 1180:0852:103c:30cf:12
class 08, sub_class 80 prog_if 00, hdr 0, flags <>, irq 7
  addr0 f6101400, size 00000100
  00: 80 11 52 08 06 01 10 02 12 00 80 08 10 40 80 00  "..R..........@.."
  10: 00 14 10 f6 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  20: 00 00 00 00 00 00 00 00 00 00 00 00 3c 10 cf 30  "............<..0"
  30: 00 00 00 00 80 00 00 00 00 00 00 00 0b 02 00 00  "................"

bus 03, slot 00, func 0, vend:dev:s_vend:s_dev:rev 168c:001c:103c:137b:01
class 02, sub_class 00 prog_if 00, hdr 0, flags <>, irq 19
  addr0 f6000000, size 00010000
  00: 8c 16 1c 00 07 01 10 00 01 00 00 02 10 00 00 00  "................"
  10: 04 00 00 f6 00 00 00 00 00 00 00 00 00 00 00 00  "................"
  20: 00 00 00 00 00 00 00 00 01 50 00 00 3c 10 7b 13  ".........P..<.{."
  30: 00 00 00 00 40 00 00 00 00 00 00 00 0a 01 00 00  "....@..........."
---------- PCI raw data end ----------
>> pci.4: build list
>> pci.3: macio
sysfs: no such bus: macio
>> pci.4: vio
sysfs: no such bus: vio
>> pci.5: xen
sysfs: no such bus: xen
>> pci.6: ps3
sysfs: no such bus: ps3_system_bus
>> pci.7: platform
  platform device: name = reg-dummy
    path = /devices/platform/reg-dummy
    type = "platform:reg-dummy"
  platform device: sf_eth_net = (null) sf_eth_dev = (nil)
  platform device: name = pcspkr
    path = /devices/platform/pcspkr
    type = "platform:pcspkr"
  platform device: sf_eth_net = (null) sf_eth_dev = (nil)
  platform device: name = serial8250
    path = /devices/platform/serial8250
    type = "platform:serial8250"
  platform device: sf_eth_net = (null) sf_eth_dev = (nil)
  platform device: name = Fixed MDIO bus.0
    path = /devices/platform/Fixed MDIO bus.0
    type = "platform:Fixed MDIO bus"
  platform device: sf_eth_net = (null) sf_eth_dev = (nil)
  platform device: name = i8042
    path = /devices/platform/i8042
    type = "platform:i8042"
  platform device: sf_eth_net = (null) sf_eth_dev = (nil)
  platform device: name = eisa.0
    path = /devices/platform/eisa.0
    type = "platform:eisa"
  platform device: sf_eth_net = (null) sf_eth_dev = (nil)
  platform device: name = hp-wmi
    path = /devices/platform/hp-wmi
    type = "platform:hp-wmi"
  platform device: sf_eth_net = (null) sf_eth_dev = (nil)
  platform device: name = regulatory.0
    path = /devices/platform/regulatory.0
    type = "platform:regulatory"
  platform device: sf_eth_net = (null) sf_eth_dev = (nil)
  platform device: name = vesafb.0
    path = /devices/platform/vesafb.0
    type = "platform:vesafb"
  platform device: sf_eth_net = (null) sf_eth_dev = (nil)
>> pci.8: of_platform
sysfs: no such bus: of_platform
>> pci.9: vm
sysfs: no such bus: vm
>> pci.10: virtio
sysfs: no such bus: virtio
>> pci.11: ibmebus
sysfs: no such bus: ibmebus
>> monitor.1: ddc
>> monitor.2: bios
>> monitor.3: pci
>> monitor.4: internal db
>> monitor.5: prom
>> isapnp.1: pnp devices
  pnp device: name = 00:00
    path = /devices/pnp0/00:00
    id = PNP 0a08
  pnp device: name = 00:01
    path = /devices/pnp0/00:01
    id = PNP 0103
  pnp device: name = 00:02
    path = /devices/pnp0/00:02
    id = PNP 0c02
  pnp device: name = 00:03
    path = /devices/pnp0/00:03
    id = PNP 0c02
  pnp device: name = 00:04
    path = /devices/pnp0/00:04
    id = PNP 0c02
  pnp device: name = 00:05
    path = /devices/pnp0/00:05
    id = PNP 0200
  pnp device: name = 00:06
    path = /devices/pnp0/00:06
    id = PNP 0800
  pnp device: name = 00:07
    path = /devices/pnp0/00:07
    id = PNP 0b00
  pnp device: name = 00:08
    path = /devices/pnp0/00:08
    id = PNP 0c04
  pnp device: name = 00:09
    path = /devices/pnp0/00:09
    id = PNP 0303
  pnp device: name = 00:0a
    path = /devices/pnp0/00:0a
    id = SYN 013b
  pnp device: name = 00:0b
    path = /devices/pnp0/00:0b
    id = PNP 0c01
>> pcmcia.1: sysfs drivers
>> pcmcia.2: pcmcia
sysfs: no such bus: pcmcia
>> pcmcia.3: pcmcia ctrl
sysfs: no such class: pcmcia_socket
>> serial.1: read info
----- serial info -----
----- serial info end -----
>> serial.2: build list
>> misc.5: misc data
----- misc resources -----
i/o:0 0x0000 - 0x0cf7 (0xcf8) "PCI Bus 0000:00"
i/o:1 0x0000 - 0x001f (0x20) "dma1"
i/o:1 0x0020 - 0x0021 (0x02) "pic1"
i/o:0 0x0040 - 0x0043 (0x04) "timer0"
i/o:0 0x0050 - 0x0053 (0x04) "timer1"
i/o:1 0x0060 - 0x0060 (0x01) "keyboard"
i/o:0 0x0062 - 0x0062 (0x01) "EC data"
i/o:1 0x0064 - 0x0064 (0x01) "keyboard"
i/o:0 0x0066 - 0x0066 (0x01) "EC cmd"
i/o:0 0x0070 - 0x0071 (0x02) "rtc0"
i/o:1 0x0080 - 0x008f (0x10) "dma page reg"
i/o:1 0x00a0 - 0x00a1 (0x02) "pic2"
i/o:1 0x00c0 - 0x00df (0x20) "dma2"
i/o:1 0x00f0 - 0x00ff (0x10) "fpu"
i/o:0 0x0170 - 0x0177 (0x08) "0000:00:06.0"
i/o:0 0x0170 - 0x0177 (0x08) "pata_amd"
i/o:0 0x01f0 - 0x01f7 (0x08) "0000:00:06.0"
i/o:0 0x01f0 - 0x01f7 (0x08) "pata_amd"
i/o:0 0x0360 - 0x0361 (0x02) "pnp 00:04"
i/o:0 0x0376 - 0x0376 (0x01) "0000:00:06.0"
i/o:0 0x0376 - 0x0376 (0x01) "pata_amd"
i/o:1 0x03c0 - 0x03df (0x20) "vesafb"
i/o:0 0x03f6 - 0x03f6 (0x01) "0000:00:06.0"
i/o:0 0x03f6 - 0x03f6 (0x01) "pata_amd"
i/o:0 0x04d0 - 0x04d1 (0x02) "pnp 00:04"
i/o:0 0x0cf8 - 0x0cff (0x08) "PCI conf1"
i/o:0 0x0d00 - 0xffff (0xf300) "PCI Bus 0000:00"
i/o:0 0x1000 - 0x107f (0x80) "pnp 00:03"
i/o:0 0x1000 - 0x1003 (0x04) "ACPI PM1a_EVT_BLK"
i/o:0 0x1004 - 0x1005 (0x02) "ACPI PM1a_CNT_BLK"
i/o:0 0x1008 - 0x100b (0x04) "ACPI PM_TMR"
i/o:0 0x1010 - 0x1015 (0x06) "ACPI CPU throttle"
i/o:0 0x1020 - 0x1027 (0x08) "ACPI GPE0_BLK"
i/o:0 0x1080 - 0x10ff (0x80) "pnp 00:03"
i/o:0 0x1400 - 0x147f (0x80) "pnp 00:03"
i/o:0 0x1480 - 0x14ff (0x80) "pnp 00:03"
i/o:0 0x1484 - 0x1484 (0x01) "ACPI PM2_CNT_BLK"
i/o:0 0x1800 - 0x187f (0x80) "pnp 00:03"
i/o:0 0x1880 - 0x18ff (0x80) "pnp 00:03"
i/o:0 0x3000 - 0x303f (0x40) "0000:00:01.1"
i/o:0 0x3000 - 0x303f (0x40) "nForce2_smbus"
i/o:0 0x3040 - 0x307f (0x40) "0000:00:01.1"
i/o:0 0x3040 - 0x307f (0x40) "nForce2_smbus"
i/o:0 0x3080 - 0x30bf (0x40) "0000:00:01.1"
i/o:0 0x30c0 - 0x30cf (0x10) "0000:00:06.0"
i/o:0 0x30c0 - 0x30cf (0x10) "pata_amd"
i/o:0 0x30d0 - 0x30df (0x10) "0000:00:09.0"
i/o:0 0x30d0 - 0x30df (0x10) "ahci"
i/o:0 0x30e0 - 0x30e3 (0x04) "0000:00:09.0"
i/o:0 0x30e0 - 0x30e3 (0x04) "ahci"
i/o:0 0x30e4 - 0x30e7 (0x04) "0000:00:09.0"
i/o:0 0x30e4 - 0x30e7 (0x04) "ahci"
i/o:0 0x30e8 - 0x30ef (0x08) "0000:00:09.0"
i/o:0 0x30e8 - 0x30ef (0x08) "ahci"
i/o:0 0x30f0 - 0x30f7 (0x08) "0000:00:09.0"
i/o:0 0x30f0 - 0x30f7 (0x08) "ahci"
i/o:0 0x30f8 - 0x30ff (0x08) "0000:00:0a.0"
i/o:0 0x30f8 - 0x30ff (0x08) "forcedeth"
i/o:0 0x4000 - 0x4fff (0x1000) "PCI Bus 0000:04"
irq:1  0 (  6591703) "timer"
irq:0  1 (    14656) "i8042"
irq:0  5 (      255) "firewire_ohci"
irq:0  7 (     4532) "r852" "mmc0"
irq:0  8 (        1) "rtc0"
irq:0  9 (   233730) "acpi"
irq:0 12 (  3548251) "i8042"
irq:0 14 (    87488) "pata_amd"
irq:0 15 (        0) "pata_amd"
irq:0 16 (  1042499) "nvidia"
irq:0 18 (        8) "ohci_hcd:usb3" "ohci_hcd:usb4"
irq:0 19 (   895136) "ath"
irq:0 21 (     1164) "hda_intel"
irq:0 22 (    15529) "ehci_hcd:usb1" "ehci_hcd:usb2"
irq:0 23 (   148578) "ahci"
irq:0 42 (        0) "eth0"
dma:1 4 "cascade"
----- misc resources end -----
>> parallel.1: pp mod
----- exec: "/sbin/rmmod lp" -----
  ERROR: Removing 'lp': Operation not permitted
----- return code: ? -----
----- exec: "/sbin/rmmod parport_pc" -----
  ERROR: Removing 'parport_pc': Operation not permitted
----- return code: ? -----
>> parallel.2.1: lp read info
>> parallel.2.2: lp read info
>> parallel.2.3: lp read info
----- parallel info -----
----- parallel info end -----
>> block.1: block modules
----- exec: "/sbin/modprobe ide-cd_mod " -----
  FATAL: Module ide_cd_mod not found.
----- return code: ? -----
----- exec: "/sbin/modprobe ide-disk " -----
  FATAL: Module ide_disk not found.
----- return code: ? -----
----- exec: "/sbin/modprobe sr_mod " -----
----- return code: ? -----
----- exec: "/sbin/modprobe sd_mod " -----
----- return code: ? -----
>> block.2: sysfs drivers
>> block.3: cdrom
----- /proc/sys/dev/cdrom/info -----
drive name:		sr0
drive speed:		24
drive # of slots:	1
Can close tray:		1
Can open tray:		1
Can lock tray:		1
Can change speed:	1
Can select disk:	0
Can read multisession:	1
Can read MCN:		1
Reports media changed:	1
Can play audio:		1
Can write CD-R:		1
Can write CD-RW:	1
Can read DVD:		1
Can write DVD-R:	1
Can write DVD-RAM:	1
Can read MRW:		1
Can write MRW:		1
Can write RAM:		1
----- /proc/sys/dev/cdrom/info end -----
>> block.4: partition
----- /proc/partitions -----
     8        0  156290904 sda
     8        1  149903360 sda1
     8        2          1 sda2
     8        5    6384640 sda5
----- /proc/partitions end -----
disks:
  sda
partitions:
  sda1
  sda2
  sda5
>> block.5: get sysfs block dev data
-----  lsscsi -----
-----  lsscsi end -----
  block: name = ram0, path = /class/block/ram0
    dev = 1:0
    range = 1
  block: name = ram1, path = /class/block/ram1
    dev = 1:1
    range = 1
  block: name = ram2, path = /class/block/ram2
    dev = 1:2
    range = 1
  block: name = ram3, path = /class/block/ram3
    dev = 1:3
    range = 1
  block: name = ram4, path = /class/block/ram4
    dev = 1:4
    range = 1
  block: name = ram5, path = /class/block/ram5
    dev = 1:5
    range = 1
  block: name = ram6, path = /class/block/ram6
    dev = 1:6
    range = 1
  block: name = ram7, path = /class/block/ram7
    dev = 1:7
    range = 1
  block: name = ram8, path = /class/block/ram8
    dev = 1:8
    range = 1
  block: name = ram9, path = /class/block/ram9
    dev = 1:9
    range = 1
  block: name = ram10, path = /class/block/ram10
    dev = 1:10
    range = 1
  block: name = ram11, path = /class/block/ram11
    dev = 1:11
    range = 1
  block: name = ram12, path = /class/block/ram12
    dev = 1:12
    range = 1
  block: name = ram13, path = /class/block/ram13
    dev = 1:13
    range = 1
  block: name = ram14, path = /class/block/ram14
    dev = 1:14
    range = 1
  block: name = ram15, path = /class/block/ram15
    dev = 1:15
    range = 1
  block: name = loop0, path = /class/block/loop0
    dev = 7:0
    range = 1
  block: name = loop1, path = /class/block/loop1
    dev = 7:1
    range = 1
  block: name = loop2, path = /class/block/loop2
    dev = 7:2
    range = 1
  block: name = loop3, path = /class/block/loop3
    dev = 7:3
    range = 1
  block: name = loop4, path = /class/block/loop4
    dev = 7:4
    range = 1
  block: name = loop5, path = /class/block/loop5
    dev = 7:5
    range = 1
  block: name = loop6, path = /class/block/loop6
    dev = 7:6
    range = 1
  block: name = loop7, path = /class/block/loop7
    dev = 7:7
    range = 1
  block: name = sr0, path = /class/block/sr0
    dev = 11:0
    range = 1
    block device: bus = scsi, bus_id = 0:0:0:0 driver = sr
      path = /devices/pci0000:00/0000:00:06.0/host0/target0:0:0/0:0:0:0
    vendor = TSSTcorp
    model = CDDVDW TS-L632N
    rev = 0503
    type = 5
>> block.5: /dev/sr0
>> block.5.1: /dev/sr0 cache
  scsi cache: 0x00
  block: name = sda, path = /class/block/sda
    dev = 8:0
    range = 16
    block device: bus = scsi, bus_id = 2:0:0:0 driver = sd
      path = /devices/pci0000:00/0000:00:09.0/host2/target2:0:0/2:0:0:0
    vendor = ATA
    model = SAMSUNG HM160HI
    rev = HH10
    type = 0
>> block.5: /dev/sda
  block: name = sda1, path = /class/block/sda1
    dev = 8:1
  block: name = sda2, path = /class/block/sda2
    dev = 8:2
  block: name = sda5, path = /class/block/sda5
    dev = 8:5
>> scsi.1: scsi modules
----- exec: "/sbin/modprobe sg " -----
----- return code: ? -----
>> scsi.2: scsi tape
sysfs: no such class: scsi_tape
>> scsi.3: scsi generic
  scsi: name = sg0, path = /class/scsi_generic/sg0
    dev = 21:0
    scsi device: bus_id = 0:0:0:0 driver = sr
      path = /devices/pci0000:00/0000:00:06.0/host0/target0:0:0/0:0:0:0
  scsi: name = sg1, path = /class/scsi_generic/sg1
    dev = 21:1
    scsi device: bus_id = 2:0:0:0 driver = sd
      path = /devices/pci0000:00/0000:00:09.0/host2/target2:0:0/2:0:0:0
>> usb.1: sysfs drivers
>> usb.2: usb
  usb dev: /devices/pci0000:00/0000:00:02.1/usb1
  usb dev: /devices/pci0000:00/0000:00:04.1/usb2
  usb dev: /devices/pci0000:00/0000:00:02.0/usb3
  usb dev: /devices/pci0000:00/0000:00:04.0/usb4
  usb device: name = usb1
    path = /devices/pci0000:00/0000:00:02.1/usb1
  usb device: name = 1-0:1.0
    path = /devices/pci0000:00/0000:00:02.1/usb1/1-0:1.0
    modalias = "usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00"
    bInterfaceNumber = 0
    bInterfaceClass = 9
    bInterfaceSubClass = 0
    bInterfaceProtocol = 0
    if: 1-0:1.0 @ /devices/pci0000:00/0000:00:02.1/usb1
    bDeviceClass = 9
    bDeviceSubClass = 0
    bDeviceProtocol = 0
    idVendor = 0x1d6b
    idProduct = 0x0002
    manufacturer = "Linux 2.6.38-8-generic-pae ehci_hcd"
    product = "EHCI Host Controller"
    serial = "0000:00:02.1"
    bcdDevice = 0206
    speed = "480"
  usb device: name = usb2
    path = /devices/pci0000:00/0000:00:04.1/usb2
  usb device: name = 2-0:1.0
    path = /devices/pci0000:00/0000:00:04.1/usb2/2-0:1.0
    modalias = "usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00"
    bInterfaceNumber = 0
    bInterfaceClass = 9
    bInterfaceSubClass = 0
    bInterfaceProtocol = 0
    if: 2-0:1.0 @ /devices/pci0000:00/0000:00:04.1/usb2
    bDeviceClass = 9
    bDeviceSubClass = 0
    bDeviceProtocol = 0
    idVendor = 0x1d6b
    idProduct = 0x0002
    manufacturer = "Linux 2.6.38-8-generic-pae ehci_hcd"
    product = "EHCI Host Controller"
    serial = "0000:00:04.1"
    bcdDevice = 0206
    speed = "480"
  usb device: name = usb3
    path = /devices/pci0000:00/0000:00:02.0/usb3
  usb device: name = 3-0:1.0
    path = /devices/pci0000:00/0000:00:02.0/usb3/3-0:1.0
    modalias = "usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00"
    bInterfaceNumber = 0
    bInterfaceClass = 9
    bInterfaceSubClass = 0
    bInterfaceProtocol = 0
    if: 3-0:1.0 @ /devices/pci0000:00/0000:00:02.0/usb3
    bDeviceClass = 9
    bDeviceSubClass = 0
    bDeviceProtocol = 0
    idVendor = 0x1d6b
    idProduct = 0x0001
    manufacturer = "Linux 2.6.38-8-generic-pae ohci_hcd"
    product = "OHCI Host Controller"
    serial = "0000:00:02.0"
    bcdDevice = 0206
    speed = "12"
  usb device: name = usb4
    path = /devices/pci0000:00/0000:00:04.0/usb4
  usb device: name = 4-0:1.0
    path = /devices/pci0000:00/0000:00:04.0/usb4/4-0:1.0
    modalias = "usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00"
    bInterfaceNumber = 0
    bInterfaceClass = 9
    bInterfaceSubClass = 0
    bInterfaceProtocol = 0
    if: 4-0:1.0 @ /devices/pci0000:00/0000:00:04.0/usb4
    bDeviceClass = 9
    bDeviceSubClass = 0
    bDeviceProtocol = 0
    idVendor = 0x1d6b
    idProduct = 0x0001
    manufacturer = "Linux 2.6.38-8-generic-pae ohci_hcd"
    product = "OHCI Host Controller"
    serial = "0000:00:04.0"
    bcdDevice = 0206
    speed = "12"
>> usb.3.1: joydev mod
>> usb.3.2: evdev mod
----- exec: "/sbin/modprobe evdev " -----
----- return code: ? -----
>> usb.3.3: input
  input: name = input0, path = /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input0
    no dev - ignored
  input: name = input1, path = /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
    no dev - ignored
  input: name = input2, path = /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input2
    no dev - ignored
  input: name = input3, path = /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
    no dev - ignored
  input: name = mice, path = /devices/virtual/input/mice
    dev = 13:63
  input: name = event0, path = /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input0/event0
    dev = 13:64
    input device: bus = acpi, bus_id = PNP0C0E:00 driver = button
      path = /devices/LNXSYSTM:00/device:00/PNP0C0E:00
  input: name = event1, path = /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1/event1
    dev = 13:65
    input device: bus = acpi, bus_id = PNP0C0D:00 driver = button
      path = /devices/LNXSYSTM:00/device:00/PNP0C0D:00
  input: name = event2, path = /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input2/event2
    dev = 13:66
    input device: bus = acpi, bus_id = PNP0C0C:00 driver = button
      path = /devices/LNXSYSTM:00/device:00/PNP0C0C:00
  input: name = event3, path = /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3/event3
    dev = 13:67
    input device: bus = acpi, bus_id = LNXPWRBN:00 driver = button
      path = /devices/LNXSYSTM:00/LNXPWRBN:00
  input: name = input4, path = /devices/platform/i8042/serio0/input/input4
    no dev - ignored
  input: name = event4, path = /devices/platform/i8042/serio0/input/input4/event4
    dev = 13:68
    input device: bus = serio, bus_id = serio0 driver = atkbd
      path = /devices/platform/i8042/serio0
  input: name = input5, path = /devices/virtual/input/input5
    no dev - ignored
  input: name = event5, path = /devices/virtual/input/input5/event5
    dev = 13:69
    input device: bus = input, bus_id = input5 driver = (null)
      path = /devices/virtual/input/input5
  input: name = input6, path = /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input6
    no dev - ignored
  input: name = event6, path = /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input6/event6
    dev = 13:70
    input device: bus = acpi, bus_id = LNXVIDEO:00 driver = video
      path = /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00
  input: name = input7, path = /devices/platform/i8042/serio1/input/input7
    no dev - ignored
  input: name = mouse0, path = /devices/platform/i8042/serio1/input/input7/mouse0
    dev = 13:32
    input device: bus = serio, bus_id = serio1 driver = psmouse
      path = /devices/platform/i8042/serio1
  input: name = event7, path = /devices/platform/i8042/serio1/input/input7/event7
    dev = 13:71
    input device: bus = serio, bus_id = serio1 driver = psmouse
      path = /devices/platform/i8042/serio1
  input: name = input8, path = /devices/pci0000:00/0000:00:07.0/sound/card0/input8
    no dev - ignored
  input: name = event8, path = /devices/pci0000:00/0000:00:07.0/sound/card0/input8/event8
    dev = 13:72
    input device: bus = sound, bus_id = card0 driver = (null)
      path = /devices/pci0000:00/0000:00:07.0/sound/card0
>> usb.3.4: lp
sysfs: no such class: usb
>> usb.3.5: serial
>> edd.1: edd mod
----- exec: "/sbin/modprobe edd " -----
----- return code: ? -----
>> edd.2: edd info
>> modem.1: serial
******  started child process 10211 (15s/120s)  ******
******  stopped child process 10211 (120s)  ******
>> mouse.2: serial
******  started child process 10212 (20s/20s)  ******
******  stopped child process 10212 (20s)  ******
>> input.1: joydev mod
>> input.1.1: evdev mod
----- exec: "/sbin/modprobe evdev " -----
----- return code: ? -----
>> input.2: input
----- /proc/bus/input/devices -----
  I: Bus=0019 Vendor=0000 Product=0003 Version=0000
  N: Name="Sleep Button"
  P: Phys=PNP0C0E/button/input0
  S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input0
  U: Uniq=
  H: Handlers=kbd event0 
  B: PROP=0
  B: EV=3
  B: KEY=4000 0 0 0 0
  
  I: Bus=0019 Vendor=0000 Product=0005 Version=0000
  N: Name="Lid Switch"
  P: Phys=PNP0C0D/button/input0
  S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
  U: Uniq=
  H: Handlers=event1 
  B: PROP=0
  B: EV=21
  B: SW=1
  
  I: Bus=0019 Vendor=0000 Product=0001 Version=0000
  N: Name="Power Button"
  P: Phys=PNP0C0C/button/input0
  S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input2
  U: Uniq=
  H: Handlers=kbd event2 
  B: PROP=0
  B: EV=3
  B: KEY=100000 0 0 0
  
  I: Bus=0019 Vendor=0000 Product=0001 Version=0000
  N: Name="Power Button"
  P: Phys=LNXPWRBN/button/input0
  S: Sysfs=/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
  U: Uniq=
  H: Handlers=kbd event3 
  B: PROP=0
  B: EV=3
  B: KEY=100000 0 0 0
  
  I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
  N: Name="AT Translated Set 2 keyboard"
  P: Phys=isa0060/serio0/input0
  S: Sysfs=/devices/platform/i8042/serio0/input/input4
  U: Uniq=
  H: Handlers=sysrq kbd event4 
  B: PROP=0
  B: EV=120013
  B: KEY=20000 0 20 0 0 0 0 500f 2100003 3803078 f900d401 feffffdf ffefffff ffffffff fffffffe
  B: MSC=10
  B: LED=7
  
  I: Bus=0019 Vendor=0000 Product=0000 Version=0000
  N: Name="HP WMI hotkeys"
  P: Phys=wmi/input0
  S: Sysfs=/devices/virtual/input/input5
  U: Uniq=
  H: Handlers=kbd event5 
  B: PROP=0
  B: EV=33
  B: KEY=40 0 0 0 10007 0 0 2100400 0 0 0 0
  B: MSC=10
  B: SW=22
  
  I: Bus=0019 Vendor=0000 Product=0006 Version=0000
  N: Name="Video Bus"
  P: Phys=LNXVIDEO/video/input0
  S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input6
  U: Uniq=
  H: Handlers=kbd event6 
  B: PROP=0
  B: EV=3
  B: KEY=3e000b 0 0 0 0 0 0 0
  
  I: Bus=0011 Vendor=0002 Product=0007 Version=01b1
  N: Name="SynPS/2 Synaptics TouchPad"
  P: Phys=isa0060/serio1/input0
  S: Sysfs=/devices/platform/i8042/serio1/input/input7
  U: Uniq=
  H: Handlers=mouse0 event7 
  B: PROP=1
  B: EV=b
  B: KEY=420 0 30000 0 0 0 0 0 0 0 0
  B: ABS=11000003
  
  I: Bus=0000 Vendor=0000 Product=0000 Version=0000
  N: Name="HDA NVidia Headphone"
  P: Phys=ALSA
  S: Sysfs=/devices/pci0000:00/0000:00:07.0/sound/card0/input8
  U: Uniq=
  H: Handlers=event8 
  B: PROP=0
  B: EV=21
  B: SW=4
  
----- /proc/bus/input/devices end -----
bus = 25, name = Sleep Button
  handlers = kbd event0
  key = 0000400000000000000000000000000000000000
  mouse buttons = 0
  mouse wheels = 0
bus = 25, name = Lid Switch
  handlers = event1
  mouse buttons = 0
  mouse wheels = 0
bus = 25, name = Power Button
  handlers = kbd event2
  key = 00100000000000000000000000000000
  mouse buttons = 0
  mouse wheels = 0
bus = 25, name = Power Button
  handlers = kbd event3
  key = 00100000000000000000000000000000
  mouse buttons = 0
  mouse wheels = 0
bus = 17, name = AT Translated Set 2 keyboard
  handlers = sysrq kbd event4
  key = 000200000000000000000020000000000000000000000000000000000000500f0210000303803078f900d401feffffdfffeffffffffffffffffffffe
  mouse buttons = 0
  mouse wheels = 0
bus = 25, name = HP WMI hotkeys
  handlers = kbd event5
  key = 000000400000000000000000000000000001000700000000000000000210040000000000000000000000000000000000
  mouse buttons = 0
  mouse wheels = 0
bus = 25, name = Video Bus
  handlers = kbd event6
  key = 003e000b00000000000000000000000000000000000000000000000000000000
  mouse buttons = 0
  mouse wheels = 0
bus = 17, name = SynPS/2 Synaptics TouchPad
  handlers = mouse0 event7
  key = 0000042000000000000300000000000000000000000000000000000000000000000000000000000000000000
  abs = 11000003
  mouse buttons = 2
  mouse wheels = 0
bus = 0, name = HDA NVidia Headphone
  handlers = event8
  mouse buttons = 0
  mouse wheels = 0
>> kbd.2: uml
>> cpu.1: cpuinfo
----- /proc/cpuinfo -----
  processor	: 0
  vendor_id	: AuthenticAMD
  cpu family	: 15
  model		: 104
  model name	: AMD Turion(tm) 64 X2 Mobile Technology TL-60
  stepping	: 2
  cpu MHz		: 2000.000
  cache size	: 512 KB
  physical id	: 0
  siblings	: 2
  core id		: 0
  cpu cores	: 2
  apicid		: 0
  initial apicid	: 0
  fdiv_bug	: no
  hlt_bug		: no
  f00f_bug	: no
  coma_bug	: no
  fpu		: yes
  fpu_exception	: yes
  cpuid level	: 1
  wp		: yes
  flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow extd_apicid pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch lbrv
  bogomips	: 4000.10
  clflush size	: 64
  cache_alignment	: 64
  address sizes	: 40 bits physical, 48 bits virtual
  power management: ts fid vid ttp tm stc 100mhzsteps
  
  processor	: 1
  vendor_id	: AuthenticAMD
  cpu family	: 15
  model		: 104
  model name	: AMD Turion(tm) 64 X2 Mobile Technology TL-60
  stepping	: 2
  cpu MHz		: 2000.000
  cache size	: 512 KB
  physical id	: 0
  siblings	: 2
  core id		: 1
  cpu cores	: 2
  apicid		: 1
  initial apicid	: 1
  fdiv_bug	: no
  hlt_bug		: no
  f00f_bug	: no
  coma_bug	: no
  fpu		: yes
  fpu_exception	: yes
  cpuid level	: 1
  wp		: yes
  flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow extd_apicid pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch lbrv
  bogomips	: 4000.10
  clflush size	: 64
  cache_alignment	: 64
  address sizes	: 40 bits physical, 48 bits virtual
  power management: ts fid vid ttp tm stc 100mhzsteps
  
----- /proc/cpuinfo end -----
>> kbd.3: serial console
>> fb.1: read info
>> net.1: get network data
  net interface: name = lo, path = /class/net/lo
    type = 772
    carrier = 1
    hw_addr = 00:00:00:00:00:00
    GDRVINFO ethtool error: Operation not supported
  net interface: name = eth0, path = /class/net/eth0
    type = 1
    carrier = 0
    hw_addr = 00:1e:68:7f:2c:8b
    net device: path = /devices/pci0000:00/0000:00:0a.0
    net driver: name = forcedeth, path = /bus/pci/drivers/forcedeth
  net interface: name = wlan0, path = /class/net/wlan0
    type = 1
    carrier = 1
    hw_addr = 00:1f:e2:ca:20:77
    net device: path = /devices/pci0000:00/0000:00:0d.0/0000:03:00.0
    net driver: name = ath5k, path = /bus/pci/drivers/ath5k
>> net.2: eeprom dump
>> net.2: eeprom dump
>> net.2: eeprom dump
>> pppoe.1: looking for pppoe
>> pppoe.2: discovery
eth0: socket failed: Operation not permitted
>> wlan.1: detecting wlan features
*** device wlan0 is wireless ***
>> wlan.2: assign udi
>> isdn.1: list
>> dsl.1: list
>> int.2: cdrom
>> int.3: media
>> int.4.1: /dev/sda
  read_block0: open(/dev/sda) failed
>> int.4: floppy
>> int.5: edd
>> int.5.1: bios
  bios ctrl 0: 23
>> int.6: mouse
>> int.15: system info
  system type:
  acpi: 1
>> int.7: hdb
>> int.7.1: modules
>> int.8: usbscsi
>> int.9: hotplug
>> int.10: modem
>> int.11: wlan
>> int.12: udev
-----  udevinfo -----
  P: /devices/LNXSYSTM:00
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00
  E: MODALIAS=acpi:LNXSYSTM:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/LNXCPU:00
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXCPU:00
  E: DRIVER=processor
  E: MODALIAS=acpi:LNXCPU:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/LNXCPU:01
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXCPU:01
  E: DRIVER=processor
  E: MODALIAS=acpi:LNXCPU:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/LNXPWRBN:00
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXPWRBN:00
  E: DRIVER=button
  E: MODALIAS=acpi:LNXPWRBN:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
  E: PRODUCT=19/0/1/0
  E: NAME="Power Button"
  E: PHYS="LNXPWRBN/button/input0"
  E: PROP=0
  E: EV=3
  E: KEY=100000 0 0 0
  E: MODALIAS=input:b0019v0000p0001e0000-e0,1,k74,ramlsfw
  E: SUBSYSTEM=input
  
  P: /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3/event3
  N: input/event3
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3/event3
  E: MAJOR=13
  E: MINOR=67
  E: DEVNAME=/dev/input/event3
  E: SUBSYSTEM=input
  E: ID_INPUT=1
  E: ID_INPUT_KEY=1
  E: XKBMODEL=pc105
  E: XKBLAYOUT=gb
  E: DMI_VENDOR=Hewlett-Packard
  
  P: /devices/LNXSYSTM:00/device:00
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/ACPI0003:00
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/ACPI0003:00
  E: DRIVER=ac
  E: MODALIAS=acpi:ACPI0003:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/ACPI0003:00/power_supply/ACAD
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/ACPI0003:00/power_supply/ACAD
  E: POWER_SUPPLY_NAME=ACAD
  E: POWER_SUPPLY_ONLINE=1
  E: SUBSYSTEM=power_supply
  
  P: /devices/LNXSYSTM:00/device:00/HPQ0007:00
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/HPQ0007:00
  E: MODALIAS=acpi:HPQ0007:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A08:00
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00
  E: DRIVER=pci_root
  E: MODALIAS=acpi:PNP0A08:PNP0A03:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00
  E: DRIVER=video
  E: MODALIAS=acpi:LNXVIDEO:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/device:23
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/device:23
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/device:24
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/device:24
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/device:25
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/device:25
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/device:26
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/device:26
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input6
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input6
  E: PRODUCT=19/0/6/0
  E: NAME="Video Bus"
  E: PHYS="LNXVIDEO/video/input0"
  E: PROP=0
  E: EV=3
  E: KEY=3e000b 0 0 0 0 0 0 0
  E: MODALIAS=input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F1,F2,F3,F4,F5,ramlsfw
  E: SUBSYSTEM=input
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input6/event6
  N: input/event6
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input6/event6
  E: MAJOR=13
  E: MINOR=70
  E: DEVNAME=/dev/input/event6
  E: SUBSYSTEM=input
  E: ID_INPUT=1
  E: ID_INPUT_KEY=1
  E: XKBMODEL=pc105
  E: XKBLAYOUT=gb
  E: DMI_VENDOR=Hewlett-Packard
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/PNP0000:00
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/PNP0000:00
  E: MODALIAS=acpi:PNP0000:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/PNP0100:00
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/PNP0100:00
  E: MODALIAS=acpi:PNP0100:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/PNP0103:00
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/PNP0103:00
  E: MODALIAS=acpi:PNP0103:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/PNP0200:00
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/PNP0200:00
  E: MODALIAS=acpi:PNP0200:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/PNP0303:00
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/PNP0303:00
  E: MODALIAS=acpi:PNP0303:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/PNP0800:00
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/PNP0800:00
  E: MODALIAS=acpi:PNP0800:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/PNP0B00:00
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/PNP0B00:00
  E: MODALIAS=acpi:PNP0B00:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/PNP0C02:02
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/PNP0C02:02
  E: MODALIAS=acpi:PNP0C02:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/PNP0C04:00
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/PNP0C04:00
  E: MODALIAS=acpi:PNP0C04:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/PNP0C09:00
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/PNP0C09:00
  E: DRIVER=ec
  E: MODALIAS=acpi:PNP0C09:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/PNP0C0F:00
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/PNP0C0F:00
  E: DRIVER=pci_link
  E: MODALIAS=acpi:PNP0C0F:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/PNP0C0F:01
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/PNP0C0F:01
  E: DRIVER=pci_link
  E: MODALIAS=acpi:PNP0C0F:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/PNP0C0F:02
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/PNP0C0F:02
  E: DRIVER=pci_link
  E: MODALIAS=acpi:PNP0C0F:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/PNP0C0F:03
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/PNP0C0F:03
  E: DRIVER=pci_link
  E: MODALIAS=acpi:PNP0C0F:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/PNP0C0F:04
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/PNP0C0F:04
  E: DRIVER=pci_link
  E: MODALIAS=acpi:PNP0C0F:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/PNP0C0F:05
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/PNP0C0F:05
  E: DRIVER=pci_link
  E: MODALIAS=acpi:PNP0C0F:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/PNP0C0F:06
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/PNP0C0F:06
  E: DRIVER=pci_link
  E: MODALIAS=acpi:PNP0C0F:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/PNP0C0F:07
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/PNP0C0F:07
  E: DRIVER=pci_link
  E: MODALIAS=acpi:PNP0C0F:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/PNP0C0F:08
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/PNP0C0F:08
  E: DRIVER=pci_link
  E: MODALIAS=acpi:PNP0C0F:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/PNP0C0F:09
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/PNP0C0F:09
  E: DRIVER=pci_link
  E: MODALIAS=acpi:PNP0C0F:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/PNP0C0F:0a
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/PNP0C0F:0a
  E: DRIVER=pci_link
  E: MODALIAS=acpi:PNP0C0F:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/PNP0C0F:0b
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/PNP0C0F:0b
  E: DRIVER=pci_link
  E: MODALIAS=acpi:PNP0C0F:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/PNP0C0F:0c
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/PNP0C0F:0c
  E: DRIVER=pci_link
  E: MODALIAS=acpi:PNP0C0F:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/PNP0C0F:0d
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/PNP0C0F:0d
  E: DRIVER=pci_link
  E: MODALIAS=acpi:PNP0C0F:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/PNP0C0F:0e
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/PNP0C0F:0e
  E: DRIVER=pci_link
  E: MODALIAS=acpi:PNP0C0F:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/PNP0C0F:0f
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/PNP0C0F:0f
  E: DRIVER=pci_link
  E: MODALIAS=acpi:PNP0C0F:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/PNP0C0F:10
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/PNP0C0F:10
  E: DRIVER=pci_link
  E: MODALIAS=acpi:PNP0C0F:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/PNP0C0F:11
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/PNP0C0F:11
  E: DRIVER=pci_link
  E: MODALIAS=acpi:PNP0C0F:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/PNP0C0F:12
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/PNP0C0F:12
  E: DRIVER=pci_link
  E: MODALIAS=acpi:PNP0C0F:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/SYN013B:00
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/SYN013B:00
  E: MODALIAS=acpi:SYN013B:SYN0100:SYN0002:PNP0F13:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:02
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:02
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:03
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:03
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:04
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:04
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:05
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:05
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:06
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:06
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:07
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:07
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:08
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:08
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:09
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:09
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:09/device:0a
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:09/device:0a
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:0b
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:0b
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:0b/device:0c
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:0b/device:0c
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:0d
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:0d
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:0d/device:0e
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:0d/device:0e
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:0f
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:0f
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:0f/device:10
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:0f/device:10
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:11
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:11
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:11/device:12
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:11/device:12
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:13
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:13
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:13/device:14
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:13/device:14
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:15
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:15
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:15/device:16
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:15/device:16
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:17
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:17
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:17/device:18
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:17/device:18
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:17/device:18/device:19
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:17/device:18/device:19
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:17/device:18/device:1a
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:17/device:18/device:1a
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:1b
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:1b
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:1b/device:1c
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:1b/device:1c
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:1b/device:1c/device:1d
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:1b/device:1c/device:1d
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:1b/device:1c/device:1e
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:1b/device:1c/device:1e
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:1b/device:1f
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:1b/device:1f
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:1b/device:1f/device:20
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:1b/device:1f/device:20
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:1b/device:1f/device:21
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:1b/device:1f/device:21
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:22
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:22
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:22/PNP0C02:00
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:22/PNP0C02:00
  E: MODALIAS=acpi:PNP0C02:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:22/PNP0C02:01
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:22/PNP0C02:01
  E: MODALIAS=acpi:PNP0C02:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:27
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:27
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0C01:00
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0C01:00
  E: MODALIAS=acpi:PNP0C01:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0C0A:00
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0C0A:00
  E: DRIVER=battery
  E: MODALIAS=acpi:PNP0C0A:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0C0A:00/power_supply/BAT0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0C0A:00/power_supply/BAT0
  E: POWER_SUPPLY_NAME=BAT0
  E: POWER_SUPPLY_STATUS=Full
  E: POWER_SUPPLY_PRESENT=1
  E: POWER_SUPPLY_TECHNOLOGY=Li-ion
  E: POWER_SUPPLY_CYCLE_COUNT=0
  E: POWER_SUPPLY_VOLTAGE_MIN_DESIGN=14800000
  E: POWER_SUPPLY_VOLTAGE_NOW=16571000
  E: POWER_SUPPLY_CHARGE_FULL_DESIGN=6000000
  E: POWER_SUPPLY_CHARGE_FULL=2240000
  E: POWER_SUPPLY_CHARGE_NOW=2240000
  E: POWER_SUPPLY_MODEL_NAME=Primary
  E: POWER_SUPPLY_MANUFACTURER=Hewlett-Packard
  E: POWER_SUPPLY_SERIAL_NUMBER= 
  E: SUBSYSTEM=power_supply
  
  P: /devices/LNXSYSTM:00/device:00/PNP0C0C:00
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0C0C:00
  E: DRIVER=button
  E: MODALIAS=acpi:PNP0C0C:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input2
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input2
  E: PRODUCT=19/0/1/0
  E: NAME="Power Button"
  E: PHYS="PNP0C0C/button/input0"
  E: PROP=0
  E: EV=3
  E: KEY=100000 0 0 0
  E: MODALIAS=input:b0019v0000p0001e0000-e0,1,k74,ramlsfw
  E: SUBSYSTEM=input
  
  P: /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input2/event2
  N: input/event2
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input2/event2
  E: MAJOR=13
  E: MINOR=66
  E: DEVNAME=/dev/input/event2
  E: SUBSYSTEM=input
  E: ID_INPUT=1
  E: ID_INPUT_KEY=1
  E: XKBMODEL=pc105
  E: XKBLAYOUT=gb
  E: DMI_VENDOR=Hewlett-Packard
  
  P: /devices/LNXSYSTM:00/device:00/PNP0C0D:00
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0C0D:00
  E: DRIVER=button
  E: MODALIAS=acpi:PNP0C0D:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
  E: PRODUCT=19/0/5/0
  E: NAME="Lid Switch"
  E: PHYS="PNP0C0D/button/input0"
  E: PROP=0
  E: EV=21
  E: SW=1
  E: MODALIAS=input:b0019v0000p0005e0000-e0,5,kramlsfw0,
  E: SUBSYSTEM=input
  
  P: /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1/event1
  N: input/event1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1/event1
  E: MAJOR=13
  E: MINOR=65
  E: DEVNAME=/dev/input/event1
  E: SUBSYSTEM=input
  E: ID_INPUT=1
  E: DMI_VENDOR=Hewlett-Packard
  
  P: /devices/LNXSYSTM:00/device:00/PNP0C0E:00
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0C0E:00
  E: DRIVER=button
  E: MODALIAS=acpi:PNP0C0E:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input0
  E: PRODUCT=19/0/3/0
  E: NAME="Sleep Button"
  E: PHYS="PNP0C0E/button/input0"
  E: PROP=0
  E: EV=3
  E: KEY=4000 0 0 0 0
  E: MODALIAS=input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw
  E: SUBSYSTEM=input
  
  P: /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input0/event0
  N: input/event0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input0/event0
  E: MAJOR=13
  E: MINOR=64
  E: DEVNAME=/dev/input/event0
  E: SUBSYSTEM=input
  E: ID_INPUT=1
  E: ID_INPUT_KEY=1
  E: XKBMODEL=pc105
  E: XKBLAYOUT=gb
  E: DMI_VENDOR=Hewlett-Packard
  
  P: /devices/LNXSYSTM:00/device:00/PNP0C14:00
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0C14:00
  E: DRIVER=wmi
  E: MODALIAS=acpi:PNP0C14:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0C32:00
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0C32:00
  E: MODALIAS=acpi:PNP0C32:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0C32:01
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0C32:01
  E: MODALIAS=acpi:PNP0C32:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0C32:02
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0C32:02
  E: MODALIAS=acpi:PNP0C32:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0C32:03
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0C32:03
  E: MODALIAS=acpi:PNP0C32:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0C32:04
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0C32:04
  E: MODALIAS=acpi:PNP0C32:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0C32:05
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0C32:05
  E: MODALIAS=acpi:PNP0C32:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:00/PNP0C32:06
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0C32:06
  E: MODALIAS=acpi:PNP0C32:
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:28
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:28
  E: SUBSYSTEM=acpi
  
  P: /devices/LNXSYSTM:00/device:28/LNXTHERM:00
  E: UDEV_LOG=3
  E: DEVPATH=/devices/LNXSYSTM:00/device:28/LNXTHERM:00
  E: DRIVER=thermal
  E: MODALIAS=acpi:LNXTHERM:
  E: SUBSYSTEM=acpi
  
  P: /devices/breakpoint
  E: UDEV_LOG=3
  E: DEVPATH=/devices/breakpoint
  E: SUBSYSTEM=event_source
  
  P: /devices/cpu
  E: UDEV_LOG=3
  E: DEVPATH=/devices/cpu
  E: SUBSYSTEM=event_source
  
  P: /devices/pci0000:00/0000:00:00.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:00.0
  E: PCI_CLASS=50000
  E: PCI_ID=10DE:0547
  E: PCI_SUBSYS_ID=103C:30CF
  E: PCI_SLOT_NAME=0000:00:00.0
  E: MODALIAS=pci:v000010DEd00000547sv0000103Csd000030CFbc05sc00i00
  E: SUBSYSTEM=pci
  
  P: /devices/pci0000:00/0000:00:01.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:01.0
  E: PCI_CLASS=60100
  E: PCI_ID=10DE:0548
  E: PCI_SUBSYS_ID=103C:30CF
  E: PCI_SLOT_NAME=0000:00:01.0
  E: MODALIAS=pci:v000010DEd00000548sv0000103Csd000030CFbc06sc01i00
  E: SUBSYSTEM=pci
  
  P: /devices/pci0000:00/0000:00:01.1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:01.1
  E: DRIVER=nForce2_smbus
  E: PCI_CLASS=C0500
  E: PCI_ID=10DE:0542
  E: PCI_SUBSYS_ID=103C:30CF
  E: PCI_SLOT_NAME=0000:00:01.1
  E: MODALIAS=pci:v000010DEd00000542sv0000103Csd000030CFbc0Csc05i00
  E: SUBSYSTEM=pci
  
  P: /devices/pci0000:00/0000:00:01.1/i2c-0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:01.1/i2c-0
  E: SUBSYSTEM=i2c
  
  P: /devices/pci0000:00/0000:00:01.1/i2c-1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:01.1/i2c-1
  E: SUBSYSTEM=i2c
  
  P: /devices/pci0000:00/0000:00:01.2
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:01.2
  E: PCI_CLASS=50000
  E: PCI_ID=10DE:0541
  E: PCI_SUBSYS_ID=103C:30CF
  E: PCI_SLOT_NAME=0000:00:01.2
  E: MODALIAS=pci:v000010DEd00000541sv0000103Csd000030CFbc05sc00i00
  E: SUBSYSTEM=pci
  
  P: /devices/pci0000:00/0000:00:01.3
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:01.3
  E: PCI_CLASS=B4000
  E: PCI_ID=10DE:0543
  E: PCI_SUBSYS_ID=103C:30CF
  E: PCI_SLOT_NAME=0000:00:01.3
  E: MODALIAS=pci:v000010DEd00000543sv0000103Csd000030CFbc0Bsc40i00
  E: SUBSYSTEM=pci
  
  P: /devices/pci0000:00/0000:00:02.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:02.0
  E: DRIVER=ohci_hcd
  E: PCI_CLASS=C0310
  E: PCI_ID=10DE:055E
  E: PCI_SUBSYS_ID=103C:30CF
  E: PCI_SLOT_NAME=0000:00:02.0
  E: MODALIAS=pci:v000010DEd0000055Esv0000103Csd000030CFbc0Csc03i10
  E: SUBSYSTEM=pci
  
  P: /devices/pci0000:00/0000:00:02.0/usb3
  N: bus/usb/003/001
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:02.0/usb3
  E: MAJOR=189
  E: MINOR=256
  E: DEVNAME=/dev/bus/usb/003/001
  E: DEVTYPE=usb_device
  E: DRIVER=usb
  E: PRODUCT=1d6b/1/206
  E: TYPE=9/0/0
  E: BUSNUM=003
  E: DEVNUM=001
  E: SUBSYSTEM=usb
  E: ID_VENDOR=Linux_2.6.38-8-generic-pae_ohci_hcd
  E: ID_VENDOR_ENC=Linux\x202.6.38-8-generic-pae\x20ohci_hcd
  E: ID_VENDOR_ID=1d6b
  E: ID_MODEL=OHCI_Host_Controller
  E: ID_MODEL_ENC=OHCI\x20Host\x20Controller
  E: ID_MODEL_ID=0001
  E: ID_REVISION=0206
  E: ID_SERIAL=Linux_2.6.38-8-generic-pae_ohci_hcd_OHCI_Host_Controller_0000:00:02.0
  E: ID_SERIAL_SHORT=0000:00:02.0
  E: ID_BUS=usb
  E: ID_USB_INTERFACES=:090000:
  
  P: /devices/pci0000:00/0000:00:02.0/usb3/3-0:1.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:02.0/usb3/3-0:1.0
  E: DEVTYPE=usb_interface
  E: DRIVER=hub
  E: PRODUCT=1d6b/1/206
  E: TYPE=9/0/0
  E: INTERFACE=9/0/0
  E: MODALIAS=usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00
  E: SUBSYSTEM=usb
  
  P: /devices/pci0000:00/0000:00:02.0/usbmon/usbmon3
  N: usbmon3
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:02.0/usbmon/usbmon3
  E: MAJOR=252
  E: MINOR=3
  E: DEVNAME=/dev/usbmon3
  E: SUBSYSTEM=usbmon
  
  P: /devices/pci0000:00/0000:00:02.1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:02.1
  E: DRIVER=ehci_hcd
  E: PCI_CLASS=C0320
  E: PCI_ID=10DE:055F
  E: PCI_SUBSYS_ID=103C:30CF
  E: PCI_SLOT_NAME=0000:00:02.1
  E: MODALIAS=pci:v000010DEd0000055Fsv0000103Csd000030CFbc0Csc03i20
  E: SUBSYSTEM=pci
  
  P: /devices/pci0000:00/0000:00:02.1/usb1
  N: bus/usb/001/001
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:02.1/usb1
  E: MAJOR=189
  E: MINOR=0
  E: DEVNAME=/dev/bus/usb/001/001
  E: DEVTYPE=usb_device
  E: DRIVER=usb
  E: PRODUCT=1d6b/2/206
  E: TYPE=9/0/0
  E: BUSNUM=001
  E: DEVNUM=001
  E: SUBSYSTEM=usb
  E: ID_VENDOR=Linux_2.6.38-8-generic-pae_ehci_hcd
  E: ID_VENDOR_ENC=Linux\x202.6.38-8-generic-pae\x20ehci_hcd
  E: ID_VENDOR_ID=1d6b
  E: ID_MODEL=EHCI_Host_Controller
  E: ID_MODEL_ENC=EHCI\x20Host\x20Controller
  E: ID_MODEL_ID=0002
  E: ID_REVISION=0206
  E: ID_SERIAL=Linux_2.6.38-8-generic-pae_ehci_hcd_EHCI_Host_Controller_0000:00:02.1
  E: ID_SERIAL_SHORT=0000:00:02.1
  E: ID_BUS=usb
  E: ID_USB_INTERFACES=:090000:
  
  P: /devices/pci0000:00/0000:00:02.1/usb1/1-0:1.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:02.1/usb1/1-0:1.0
  E: DEVTYPE=usb_interface
  E: DRIVER=hub
  E: PRODUCT=1d6b/2/206
  E: TYPE=9/0/0
  E: INTERFACE=9/0/0
  E: MODALIAS=usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00
  E: SUBSYSTEM=usb
  
  P: /devices/pci0000:00/0000:00:02.1/usbmon/usbmon1
  N: usbmon1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:02.1/usbmon/usbmon1
  E: MAJOR=252
  E: MINOR=1
  E: DEVNAME=/dev/usbmon1
  E: SUBSYSTEM=usbmon
  
  P: /devices/pci0000:00/0000:00:04.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:04.0
  E: DRIVER=ohci_hcd
  E: PCI_CLASS=C0310
  E: PCI_ID=10DE:055E
  E: PCI_SUBSYS_ID=103C:30CF
  E: PCI_SLOT_NAME=0000:00:04.0
  E: MODALIAS=pci:v000010DEd0000055Esv0000103Csd000030CFbc0Csc03i10
  E: SUBSYSTEM=pci
  
  P: /devices/pci0000:00/0000:00:04.0/usb4
  N: bus/usb/004/001
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:04.0/usb4
  E: MAJOR=189
  E: MINOR=384
  E: DEVNAME=/dev/bus/usb/004/001
  E: DEVTYPE=usb_device
  E: DRIVER=usb
  E: PRODUCT=1d6b/1/206
  E: TYPE=9/0/0
  E: BUSNUM=004
  E: DEVNUM=001
  E: SUBSYSTEM=usb
  E: ID_VENDOR=Linux_2.6.38-8-generic-pae_ohci_hcd
  E: ID_VENDOR_ENC=Linux\x202.6.38-8-generic-pae\x20ohci_hcd
  E: ID_VENDOR_ID=1d6b
  E: ID_MODEL=OHCI_Host_Controller
  E: ID_MODEL_ENC=OHCI\x20Host\x20Controller
  E: ID_MODEL_ID=0001
  E: ID_REVISION=0206
  E: ID_SERIAL=Linux_2.6.38-8-generic-pae_ohci_hcd_OHCI_Host_Controller_0000:00:04.0
  E: ID_SERIAL_SHORT=0000:00:04.0
  E: ID_BUS=usb
  E: ID_USB_INTERFACES=:090000:
  
  P: /devices/pci0000:00/0000:00:04.0/usb4/4-0:1.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:04.0/usb4/4-0:1.0
  E: DEVTYPE=usb_interface
  E: DRIVER=hub
  E: PRODUCT=1d6b/1/206
  E: TYPE=9/0/0
  E: INTERFACE=9/0/0
  E: MODALIAS=usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00
  E: SUBSYSTEM=usb
  
  P: /devices/pci0000:00/0000:00:04.0/usbmon/usbmon4
  N: usbmon4
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:04.0/usbmon/usbmon4
  E: MAJOR=252
  E: MINOR=4
  E: DEVNAME=/dev/usbmon4
  E: SUBSYSTEM=usbmon
  
  P: /devices/pci0000:00/0000:00:04.1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:04.1
  E: DRIVER=ehci_hcd
  E: PCI_CLASS=C0320
  E: PCI_ID=10DE:055F
  E: PCI_SUBSYS_ID=103C:30CF
  E: PCI_SLOT_NAME=0000:00:04.1
  E: MODALIAS=pci:v000010DEd0000055Fsv0000103Csd000030CFbc0Csc03i20
  E: SUBSYSTEM=pci
  
  P: /devices/pci0000:00/0000:00:04.1/usb2
  N: bus/usb/002/001
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:04.1/usb2
  E: MAJOR=189
  E: MINOR=128
  E: DEVNAME=/dev/bus/usb/002/001
  E: DEVTYPE=usb_device
  E: DRIVER=usb
  E: PRODUCT=1d6b/2/206
  E: TYPE=9/0/0
  E: BUSNUM=002
  E: DEVNUM=001
  E: SUBSYSTEM=usb
  E: ID_VENDOR=Linux_2.6.38-8-generic-pae_ehci_hcd
  E: ID_VENDOR_ENC=Linux\x202.6.38-8-generic-pae\x20ehci_hcd
  E: ID_VENDOR_ID=1d6b
  E: ID_MODEL=EHCI_Host_Controller
  E: ID_MODEL_ENC=EHCI\x20Host\x20Controller
  E: ID_MODEL_ID=0002
  E: ID_REVISION=0206
  E: ID_SERIAL=Linux_2.6.38-8-generic-pae_ehci_hcd_EHCI_Host_Controller_0000:00:04.1
  E: ID_SERIAL_SHORT=0000:00:04.1
  E: ID_BUS=usb
  E: ID_USB_INTERFACES=:090000:
  
  P: /devices/pci0000:00/0000:00:04.1/usb2/2-0:1.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:04.1/usb2/2-0:1.0
  E: DEVTYPE=usb_interface
  E: DRIVER=hub
  E: PRODUCT=1d6b/2/206
  E: TYPE=9/0/0
  E: INTERFACE=9/0/0
  E: MODALIAS=usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00
  E: SUBSYSTEM=usb
  
  P: /devices/pci0000:00/0000:00:04.1/usbmon/usbmon2
  N: usbmon2
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:04.1/usbmon/usbmon2
  E: MAJOR=252
  E: MINOR=2
  E: DEVNAME=/dev/usbmon2
  E: SUBSYSTEM=usbmon
  
  P: /devices/pci0000:00/0000:00:06.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:06.0
  E: DRIVER=pata_amd
  E: PCI_CLASS=1018A
  E: PCI_ID=10DE:0560
  E: PCI_SUBSYS_ID=103C:30CF
  E: PCI_SLOT_NAME=0000:00:06.0
  E: MODALIAS=pci:v000010DEd00000560sv0000103Csd000030CFbc01sc01i8a
  E: SUBSYSTEM=pci
  E: ID_VENDOR_FROM_DATABASE=nVidia Corporation
  E: ID_MODEL_FROM_DATABASE=MCP67 IDE Controller
  
  P: /devices/pci0000:00/0000:00:06.0/ata1/ata_port/ata1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:06.0/ata1/ata_port/ata1
  E: SUBSYSTEM=ata_port
  
  P: /devices/pci0000:00/0000:00:06.0/ata1/link1/ata_link/link1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:06.0/ata1/link1/ata_link/link1
  E: SUBSYSTEM=ata_link
  
  P: /devices/pci0000:00/0000:00:06.0/ata1/link1/dev1.0/ata_device/dev1.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:06.0/ata1/link1/dev1.0/ata_device/dev1.0
  E: SUBSYSTEM=ata_device
  
  P: /devices/pci0000:00/0000:00:06.0/ata1/link1/dev1.1/ata_device/dev1.1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:06.0/ata1/link1/dev1.1/ata_device/dev1.1
  E: SUBSYSTEM=ata_device
  
  P: /devices/pci0000:00/0000:00:06.0/ata2/ata_port/ata2
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:06.0/ata2/ata_port/ata2
  E: SUBSYSTEM=ata_port
  
  P: /devices/pci0000:00/0000:00:06.0/ata2/link2/ata_link/link2
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:06.0/ata2/link2/ata_link/link2
  E: SUBSYSTEM=ata_link
  
  P: /devices/pci0000:00/0000:00:06.0/ata2/link2/dev2.0/ata_device/dev2.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:06.0/ata2/link2/dev2.0/ata_device/dev2.0
  E: SUBSYSTEM=ata_device
  
  P: /devices/pci0000:00/0000:00:06.0/ata2/link2/dev2.1/ata_device/dev2.1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:06.0/ata2/link2/dev2.1/ata_device/dev2.1
  E: SUBSYSTEM=ata_device
  
  P: /devices/pci0000:00/0000:00:06.0/host0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:06.0/host0
  E: DEVTYPE=scsi_host
  E: SUBSYSTEM=scsi
  
  P: /devices/pci0000:00/0000:00:06.0/host0/scsi_host/host0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:06.0/host0/scsi_host/host0
  E: SUBSYSTEM=scsi_host
  
  P: /devices/pci0000:00/0000:00:06.0/host0/target0:0:0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:06.0/host0/target0:0:0
  E: DEVTYPE=scsi_target
  E: SUBSYSTEM=scsi
  
  P: /devices/pci0000:00/0000:00:06.0/host0/target0:0:0/0:0:0:0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:06.0/host0/target0:0:0/0:0:0:0
  E: DEVTYPE=scsi_device
  E: DRIVER=sr
  E: MODALIAS=scsi:t-0x05
  E: SUBSYSTEM=scsi
  
  P: /devices/pci0000:00/0000:00:06.0/host0/target0:0:0/0:0:0:0/block/sr0
  N: sr0
  S: scd0
  S: disk/by-id/ata-TSSTcorp_CDDVDW_TS-L632N
  S: disk/by-path/pci-0000:00:06.0-scsi-0:0:0:0
  S: cdrom
  S: cdrw
  S: dvd
  S: dvdrw
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:06.0/host0/target0:0:0/0:0:0:0/block/sr0
  E: MAJOR=11
  E: MINOR=0
  E: DEVNAME=/dev/sr0
  E: DEVTYPE=disk
  E: SUBSYSTEM=block
  E: ID_CDROM=1
  E: ID_CDROM_CD=1
  E: ID_CDROM_CD_R=1
  E: ID_CDROM_CD_RW=1
  E: ID_CDROM_DVD=1
  E: ID_CDROM_DVD_R=1
  E: ID_CDROM_DVD_RW=1
  E: ID_CDROM_DVD_RAM=1
  E: ID_CDROM_DVD_PLUS_R=1
  E: ID_CDROM_DVD_PLUS_RW=1
  E: ID_CDROM_DVD_PLUS_R_DL=1
  E: ID_CDROM_MRW=1
  E: ID_CDROM_MRW_W=1
  E: ID_ATA=1
  E: ID_TYPE=cd
  E: ID_BUS=ata
  E: ID_MODEL=TSSTcorp_CDDVDW_TS-L632N
  E: ID_MODEL_ENC=TSSTcorp\x20CDDVDW\x20TS-L632N\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20
  E: ID_REVISION=0503
  E: ID_SERIAL=TSSTcorp_CDDVDW_TS-L632N
  E: ID_ATA_FEATURE_SET_PM=1
  E: ID_ATA_FEATURE_SET_PM_ENABLED=1
  E: ID_PATH=pci-0000:00:06.0-scsi-0:0:0:0
  E: GENERATED=1
  E: UDISKS_PRESENTATION_NOPOLICY=0
  E: DEVLINKS=/dev/scd0 /dev/disk/by-id/ata-TSSTcorp_CDDVDW_TS-L632N /dev/disk/by-path/pci-0000:00:06.0-scsi-0:0:0:0 /dev/cdrom /dev/cdrw /dev/dvd /dev/dvdrw
  E: TAGS=:udev-acl:
  
  P: /devices/pci0000:00/0000:00:06.0/host0/target0:0:0/0:0:0:0/bsg/0:0:0:0
  N: bsg/0:0:0:0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:06.0/host0/target0:0:0/0:0:0:0/bsg/0:0:0:0
  E: MAJOR=253
  E: MINOR=0
  E: DEVNAME=/dev/bsg/0:0:0:0
  E: SUBSYSTEM=bsg
  
  P: /devices/pci0000:00/0000:00:06.0/host0/target0:0:0/0:0:0:0/scsi_device/0:0:0:0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:06.0/host0/target0:0:0/0:0:0:0/scsi_device/0:0:0:0
  E: SUBSYSTEM=scsi_device
  
  P: /devices/pci0000:00/0000:00:06.0/host0/target0:0:0/0:0:0:0/scsi_generic/sg0
  N: sg0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:06.0/host0/target0:0:0/0:0:0:0/scsi_generic/sg0
  E: MAJOR=21
  E: MINOR=0
  E: DEVNAME=/dev/sg0
  E: SUBSYSTEM=scsi_generic
  E: TAGS=:udev-acl:
  
  P: /devices/pci0000:00/0000:00:06.0/host1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:06.0/host1
  E: DEVTYPE=scsi_host
  E: SUBSYSTEM=scsi
  
  P: /devices/pci0000:00/0000:00:06.0/host1/scsi_host/host1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:06.0/host1/scsi_host/host1
  E: SUBSYSTEM=scsi_host
  
  P: /devices/pci0000:00/0000:00:07.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:07.0
  E: DRIVER=HDA Intel
  E: PCI_CLASS=40300
  E: PCI_ID=10DE:055C
  E: PCI_SUBSYS_ID=103C:30CF
  E: PCI_SLOT_NAME=0000:00:07.0
  E: MODALIAS=pci:v000010DEd0000055Csv0000103Csd000030CFbc04sc03i00
  E: SUBSYSTEM=pci
  
  P: /devices/pci0000:00/0000:00:07.0/sound/card0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:07.0/sound/card0
  E: SUBSYSTEM=sound
  E: SOUND_INITIALIZED=1
  E: ID_VENDOR_FROM_DATABASE=nVidia Corporation
  E: ID_MODEL_FROM_DATABASE=MCP67 High Definition Audio
  E: ID_BUS=pci
  E: ID_VENDOR_ID=0x10de
  E: ID_MODEL_ID=0x055c
  E: ID_PATH=pci-0000:00:07.0
  E: SOUND_FORM_FACTOR=internal
  E: PULSE_PROFILE_SET=nvidia.conf
  
  P: /devices/pci0000:00/0000:00:07.0/sound/card0/hwC0D0
  N: snd/hwC0D0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:07.0/sound/card0/hwC0D0
  E: MAJOR=116
  E: MINOR=5
  E: DEVNAME=/dev/snd/hwC0D0
  E: SUBSYSTEM=sound
  E: TAGS=:udev-acl:
  
  P: /devices/pci0000:00/0000:00:07.0/sound/card0/input8
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:07.0/sound/card0/input8
  E: PRODUCT=0/0/0/0
  E: NAME="HDA NVidia Headphone"
  E: PHYS="ALSA"
  E: PROP=0
  E: EV=21
  E: SW=4
  E: MODALIAS=input:b0000v0000p0000e0000-e0,5,kramlsfw2,
  E: SUBSYSTEM=input
  
  P: /devices/pci0000:00/0000:00:07.0/sound/card0/input8/event8
  N: input/event8
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:07.0/sound/card0/input8/event8
  E: MAJOR=13
  E: MINOR=72
  E: DEVNAME=/dev/input/event8
  E: SUBSYSTEM=input
  E: ID_INPUT=1
  E: ID_PATH=pci-0000:00:07.0
  E: DMI_VENDOR=Hewlett-Packard
  
  P: /devices/pci0000:00/0000:00:07.0/sound/card0/pcmC0D0c
  N: snd/pcmC0D0c
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:07.0/sound/card0/pcmC0D0c
  E: MAJOR=116
  E: MINOR=4
  E: DEVNAME=/dev/snd/pcmC0D0c
  E: SUBSYSTEM=sound
  E: TAGS=:udev-acl:
  
  P: /devices/pci0000:00/0000:00:07.0/sound/card0/pcmC0D0p
  N: snd/pcmC0D0p
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:07.0/sound/card0/pcmC0D0p
  E: MAJOR=116
  E: MINOR=3
  E: DEVNAME=/dev/snd/pcmC0D0p
  E: SUBSYSTEM=sound
  E: TAGS=:udev-acl:
  
  P: /devices/pci0000:00/0000:00:07.0/sound/card0/pcmC0D1p
  N: snd/pcmC0D1p
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:07.0/sound/card0/pcmC0D1p
  E: MAJOR=116
  E: MINOR=2
  E: DEVNAME=/dev/snd/pcmC0D1p
  E: SUBSYSTEM=sound
  E: TAGS=:udev-acl:
  
  P: /devices/pci0000:00/0000:00:07.0/sound/card0/controlC0
  N: snd/controlC0
  S: snd/by-path/pci-0000:00:07.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:07.0/sound/card0/controlC0
  E: MAJOR=116
  E: MINOR=6
  E: DEVNAME=/dev/snd/controlC0
  E: SUBSYSTEM=sound
  E: ID_PATH=pci-0000:00:07.0
  E: DEVLINKS=/dev/snd/by-path/pci-0000:00:07.0
  E: TAGS=:udev-acl:
  
  P: /devices/pci0000:00/0000:00:08.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:08.0
  E: PCI_CLASS=60401
  E: PCI_ID=10DE:0561
  E: PCI_SUBSYS_ID=10DE:CB84
  E: PCI_SLOT_NAME=0000:00:08.0
  E: MODALIAS=pci:v000010DEd00000561sv000010DEsd0000CB84bc06sc04i01
  E: SUBSYSTEM=pci
  
  P: /devices/pci0000:00/0000:00:08.0/0000:02:05.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:08.0/0000:02:05.0
  E: DRIVER=firewire_ohci
  E: PCI_CLASS=C0010
  E: PCI_ID=1180:0832
  E: PCI_SUBSYS_ID=103C:30CF
  E: PCI_SLOT_NAME=0000:02:05.0
  E: MODALIAS=pci:v00001180d00000832sv0000103Csd000030CFbc0Csc00i10
  E: SUBSYSTEM=pci
  
  P: /devices/pci0000:00/0000:00:08.0/0000:02:05.0/fw0
  N: fw0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:08.0/0000:02:05.0/fw0
  E: MAJOR=251
  E: MINOR=0
  E: DEVNAME=/dev/fw0
  E: SUBSYSTEM=firewire
  
  P: /devices/pci0000:00/0000:00:08.0/0000:02:05.1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:08.0/0000:02:05.1
  E: DRIVER=sdhci-pci
  E: PCI_CLASS=80500
  E: PCI_ID=1180:0822
  E: PCI_SUBSYS_ID=103C:30CF
  E: PCI_SLOT_NAME=0000:02:05.1
  E: MODALIAS=pci:v00001180d00000822sv0000103Csd000030CFbc08sc05i00
  E: SUBSYSTEM=pci
  
  P: /devices/pci0000:00/0000:00:08.0/0000:02:05.1/leds/mmc0::
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:08.0/0000:02:05.1/leds/mmc0::
  E: SUBSYSTEM=leds
  
  P: /devices/pci0000:00/0000:00:08.0/0000:02:05.1/mmc_host/mmc0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:08.0/0000:02:05.1/mmc_host/mmc0
  E: SUBSYSTEM=mmc_host
  
  P: /devices/pci0000:00/0000:00:08.0/0000:02:05.2
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:08.0/0000:02:05.2
  E: PCI_CLASS=88000
  E: PCI_ID=1180:0592
  E: PCI_SUBSYS_ID=103C:30CF
  E: PCI_SLOT_NAME=0000:02:05.2
  E: MODALIAS=pci:v00001180d00000592sv0000103Csd000030CFbc08sc80i00
  E: SUBSYSTEM=pci
  
  P: /devices/pci0000:00/0000:00:08.0/0000:02:05.3
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:08.0/0000:02:05.3
  E: DRIVER=r852
  E: PCI_CLASS=88000
  E: PCI_ID=1180:0852
  E: PCI_SUBSYS_ID=103C:30CF
  E: PCI_SLOT_NAME=0000:02:05.3
  E: MODALIAS=pci:v00001180d00000852sv0000103Csd000030CFbc08sc80i00
  E: SUBSYSTEM=pci
  
  P: /devices/pci0000:00/0000:00:08.0/pci_bus/0000:02
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:08.0/pci_bus/0000:02
  E: SUBSYSTEM=pci_bus
  
  P: /devices/pci0000:00/0000:00:09.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:09.0
  E: DRIVER=ahci
  E: PCI_CLASS=10185
  E: PCI_ID=10DE:0550
  E: PCI_SUBSYS_ID=103C:30CF
  E: PCI_SLOT_NAME=0000:00:09.0
  E: MODALIAS=pci:v000010DEd00000550sv0000103Csd000030CFbc01sc01i85
  E: SUBSYSTEM=pci
  E: ID_VENDOR_FROM_DATABASE=nVidia Corporation
  E: ID_MODEL_FROM_DATABASE=MCP67 AHCI Controller
  
  P: /devices/pci0000:00/0000:00:09.0/ata3/ata_port/ata3
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:09.0/ata3/ata_port/ata3
  E: SUBSYSTEM=ata_port
  
  P: /devices/pci0000:00/0000:00:09.0/ata3/link3/ata_link/link3
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:09.0/ata3/link3/ata_link/link3
  E: SUBSYSTEM=ata_link
  
  P: /devices/pci0000:00/0000:00:09.0/ata3/link3/dev3.0/ata_device/dev3.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:09.0/ata3/link3/dev3.0/ata_device/dev3.0
  E: SUBSYSTEM=ata_device
  
  P: /devices/pci0000:00/0000:00:09.0/ata4/ata_port/ata4
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:09.0/ata4/ata_port/ata4
  E: SUBSYSTEM=ata_port
  
  P: /devices/pci0000:00/0000:00:09.0/ata4/link4/ata_link/link4
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:09.0/ata4/link4/ata_link/link4
  E: SUBSYSTEM=ata_link
  
  P: /devices/pci0000:00/0000:00:09.0/ata4/link4/dev4.0/ata_device/dev4.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:09.0/ata4/link4/dev4.0/ata_device/dev4.0
  E: SUBSYSTEM=ata_device
  
  P: /devices/pci0000:00/0000:00:09.0/ata5/ata_port/ata5
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:09.0/ata5/ata_port/ata5
  E: SUBSYSTEM=ata_port
  
  P: /devices/pci0000:00/0000:00:09.0/ata5/link5/ata_link/link5
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:09.0/ata5/link5/ata_link/link5
  E: SUBSYSTEM=ata_link
  
  P: /devices/pci0000:00/0000:00:09.0/ata5/link5/dev5.0/ata_device/dev5.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:09.0/ata5/link5/dev5.0/ata_device/dev5.0
  E: SUBSYSTEM=ata_device
  
  P: /devices/pci0000:00/0000:00:09.0/ata6/ata_port/ata6
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:09.0/ata6/ata_port/ata6
  E: SUBSYSTEM=ata_port
  
  P: /devices/pci0000:00/0000:00:09.0/ata6/link6/ata_link/link6
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:09.0/ata6/link6/ata_link/link6
  E: SUBSYSTEM=ata_link
  
  P: /devices/pci0000:00/0000:00:09.0/ata6/link6/dev6.0/ata_device/dev6.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:09.0/ata6/link6/dev6.0/ata_device/dev6.0
  E: SUBSYSTEM=ata_device
  
  P: /devices/pci0000:00/0000:00:09.0/host2
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:09.0/host2
  E: DEVTYPE=scsi_host
  E: SUBSYSTEM=scsi
  
  P: /devices/pci0000:00/0000:00:09.0/host2/scsi_host/host2
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:09.0/host2/scsi_host/host2
  E: SUBSYSTEM=scsi_host
  
  P: /devices/pci0000:00/0000:00:09.0/host2/target2:0:0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:09.0/host2/target2:0:0
  E: DEVTYPE=scsi_target
  E: SUBSYSTEM=scsi
  
  P: /devices/pci0000:00/0000:00:09.0/host2/target2:0:0/2:0:0:0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:09.0/host2/target2:0:0/2:0:0:0
  E: DEVTYPE=scsi_device
  E: DRIVER=sd
  E: MODALIAS=scsi:t-0x00
  E: SUBSYSTEM=scsi
  
  P: /devices/pci0000:00/0000:00:09.0/host2/target2:0:0/2:0:0:0/block/sda
  N: sda
  S: disk/by-id/ata-SAMSUNG_HM160HI_S18PJDNQ506588
  S: disk/by-id/scsi-SATA_SAMSUNG_HM160HIS18PJDNQ506588
  S: disk/by-path/pci-0000:00:09.0-scsi-0:0:0:0
  S: disk/by-id/wwn-0x50f00000e1506588
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:09.0/host2/target2:0:0/2:0:0:0/block/sda
  E: MAJOR=8
  E: MINOR=0
  E: DEVNAME=/dev/sda
  E: DEVTYPE=disk
  E: SUBSYSTEM=block
  E: ID_ATA=1
  E: ID_TYPE=disk
  E: ID_BUS=ata
  E: ID_MODEL=SAMSUNG_HM160HI
  E: ID_MODEL_ENC=SAMSUNG\x20HM160HI\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20
  E: ID_REVISION=HH100-21
  E: ID_SERIAL=SAMSUNG_HM160HI_S18PJDNQ506588
  E: ID_SERIAL_SHORT=S18PJDNQ506588
  E: ID_ATA_WRITE_CACHE=1
  E: ID_ATA_WRITE_CACHE_ENABLED=1
  E: ID_ATA_FEATURE_SET_PM=1
  E: ID_ATA_FEATURE_SET_PM_ENABLED=1
  E: ID_ATA_FEATURE_SET_SECURITY=1
  E: ID_ATA_FEATURE_SET_SECURITY_ENABLED=0
  E: ID_ATA_FEATURE_SET_SECURITY_ERASE_UNIT_MIN=60
  E: ID_ATA_FEATURE_SET_SECURITY_ENHANCED_ERASE_UNIT_MIN=60
  E: ID_ATA_FEATURE_SET_SECURITY_FROZEN=1
  E: ID_ATA_FEATURE_SET_SMART=1
  E: ID_ATA_FEATURE_SET_SMART_ENABLED=1
  E: ID_ATA_FEATURE_SET_APM=1
  E: ID_ATA_FEATURE_SET_APM_ENABLED=1
  E: ID_ATA_FEATURE_SET_APM_CURRENT_VALUE=254
  E: ID_ATA_DOWNLOAD_MICROCODE=1
  E: ID_ATA_SATA=1
  E: ID_ATA_SATA_SIGNAL_RATE_GEN1=1
  E: ID_WWN=0x50f00000e1506588
  E: ID_WWN_WITH_EXTENSION=0x50f00000e1506588
  E: ID_SCSI_COMPAT=SATA_SAMSUNG_HM160HIS18PJDNQ506588
  E: ID_PATH=pci-0000:00:09.0-scsi-0:0:0:0
  E: ID_PART_TABLE_TYPE=dos
  E: UDISKS_PRESENTATION_NOPOLICY=0
  E: UDISKS_PARTITION_TABLE=1
  E: UDISKS_PARTITION_TABLE_SCHEME=mbr
  E: UDISKS_PARTITION_TABLE_COUNT=3
  E: UDISKS_ATA_SMART_IS_AVAILABLE=1
  E: DEVLINKS=/dev/disk/by-id/ata-SAMSUNG_HM160HI_S18PJDNQ506588 /dev/disk/by-id/scsi-SATA_SAMSUNG_HM160HIS18PJDNQ506588 /dev/disk/by-path/pci-0000:00:09.0-scsi-0:0:0:0 /dev/disk/by-id/wwn-0x50f00000e1506588
  
  P: /devices/pci0000:00/0000:00:09.0/host2/target2:0:0/2:0:0:0/block/sda/sda1
  N: sda1
  S: disk/by-id/ata-SAMSUNG_HM160HI_S18PJDNQ506588-part1
  S: disk/by-id/scsi-SATA_SAMSUNG_HM160HIS18PJDNQ506588-part1
  S: disk/by-path/pci-0000:00:09.0-scsi-0:0:0:0-part1
  S: disk/by-uuid/84e2594c-9753-4f69-8a20-584d6e60a569
  S: disk/by-id/wwn-0x50f00000e1506588-part1
  S: root
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:09.0/host2/target2:0:0/2:0:0:0/block/sda/sda1
  E: MAJOR=8
  E: MINOR=1
  E: DEVNAME=/dev/sda1
  E: DEVTYPE=partition
  E: SUBSYSTEM=block
  E: ID_ATA=1
  E: ID_TYPE=disk
  E: ID_BUS=ata
  E: ID_MODEL=SAMSUNG_HM160HI
  E: ID_MODEL_ENC=SAMSUNG\x20HM160HI\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20
  E: ID_REVISION=HH100-21
  E: ID_SERIAL=SAMSUNG_HM160HI_S18PJDNQ506588
  E: ID_SERIAL_SHORT=S18PJDNQ506588
  E: ID_ATA_WRITE_CACHE=1
  E: ID_ATA_WRITE_CACHE_ENABLED=1
  E: ID_ATA_FEATURE_SET_PM=1
  E: ID_ATA_FEATURE_SET_PM_ENABLED=1
  E: ID_ATA_FEATURE_SET_SECURITY=1
  E: ID_ATA_FEATURE_SET_SECURITY_ENABLED=0
  E: ID_ATA_FEATURE_SET_SECURITY_ERASE_UNIT_MIN=60
  E: ID_ATA_FEATURE_SET_SECURITY_ENHANCED_ERASE_UNIT_MIN=60
  E: ID_ATA_FEATURE_SET_SECURITY_FROZEN=1
  E: ID_ATA_FEATURE_SET_SMART=1
  E: ID_ATA_FEATURE_SET_SMART_ENABLED=1
  E: ID_ATA_FEATURE_SET_APM=1
  E: ID_ATA_FEATURE_SET_APM_ENABLED=1
  E: ID_ATA_FEATURE_SET_APM_CURRENT_VALUE=254
  E: ID_ATA_DOWNLOAD_MICROCODE=1
  E: ID_ATA_SATA=1
  E: ID_ATA_SATA_SIGNAL_RATE_GEN1=1
  E: ID_WWN=0x50f00000e1506588
  E: ID_WWN_WITH_EXTENSION=0x50f00000e1506588
  E: ID_SCSI_COMPAT=SATA_SAMSUNG_HM160HIS18PJDNQ506588
  E: ID_PATH=pci-0000:00:09.0-scsi-0:0:0:0
  E: ID_PART_TABLE_TYPE=dos
  E: ID_FS_UUID=84e2594c-9753-4f69-8a20-584d6e60a569
  E: ID_FS_UUID_ENC=84e2594c-9753-4f69-8a20-584d6e60a569
  E: ID_FS_VERSION=1.0
  E: ID_FS_TYPE=ext4
  E: ID_FS_USAGE=filesystem
  E: UDISKS_PRESENTATION_NOPOLICY=0
  E: UDISKS_PARTITION=1
  E: UDISKS_PARTITION_SCHEME=mbr
  E: UDISKS_PARTITION_NUMBER=1
  E: UDISKS_PARTITION_TYPE=0x83
  E: UDISKS_PARTITION_SIZE=153501040640
  E: UDISKS_PARTITION_FLAGS=boot
  E: UDISKS_PARTITION_SLAVE=/sys/devices/pci0000:00/0000:00:09.0/host2/target2:0:0/2:0:0:0/block/sda
  E: UDISKS_PARTITION_OFFSET=1048576
  E: UDISKS_PARTITION_ALIGNMENT_OFFSET=0
  E: DEVLINKS=/dev/disk/by-id/ata-SAMSUNG_HM160HI_S18PJDNQ506588-part1 /dev/disk/by-id/scsi-SATA_SAMSUNG_HM160HIS18PJDNQ506588-part1 /dev/disk/by-path/pci-0000:00:09.0-scsi-0:0:0:0-part1 /dev/disk/by-uuid/84e2594c-9753-4f69-8a20-584d6e60a569 /dev/disk/by-id/wwn-0x50f00000e1506588-part1 /dev/root
  
  P: /devices/pci0000:00/0000:00:09.0/host2/target2:0:0/2:0:0:0/block/sda/sda2
  N: sda2
  S: disk/by-id/ata-SAMSUNG_HM160HI_S18PJDNQ506588-part2
  S: disk/by-id/scsi-SATA_SAMSUNG_HM160HIS18PJDNQ506588-part2
  S: disk/by-path/pci-0000:00:09.0-scsi-0:0:0:0-part2
  S: disk/by-id/wwn-0x50f00000e1506588-part2
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:09.0/host2/target2:0:0/2:0:0:0/block/sda/sda2
  E: MAJOR=8
  E: MINOR=2
  E: DEVNAME=/dev/sda2
  E: DEVTYPE=partition
  E: SUBSYSTEM=block
  E: ID_ATA=1
  E: ID_TYPE=disk
  E: ID_BUS=ata
  E: ID_MODEL=SAMSUNG_HM160HI
  E: ID_MODEL_ENC=SAMSUNG\x20HM160HI\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20
  E: ID_REVISION=HH100-21
  E: ID_SERIAL=SAMSUNG_HM160HI_S18PJDNQ506588
  E: ID_SERIAL_SHORT=S18PJDNQ506588
  E: ID_ATA_WRITE_CACHE=1
  E: ID_ATA_WRITE_CACHE_ENABLED=1
  E: ID_ATA_FEATURE_SET_PM=1
  E: ID_ATA_FEATURE_SET_PM_ENABLED=1
  E: ID_ATA_FEATURE_SET_SECURITY=1
  E: ID_ATA_FEATURE_SET_SECURITY_ENABLED=0
  E: ID_ATA_FEATURE_SET_SECURITY_ERASE_UNIT_MIN=60
  E: ID_ATA_FEATURE_SET_SECURITY_ENHANCED_ERASE_UNIT_MIN=60
  E: ID_ATA_FEATURE_SET_SECURITY_FROZEN=1
  E: ID_ATA_FEATURE_SET_SMART=1
  E: ID_ATA_FEATURE_SET_SMART_ENABLED=1
  E: ID_ATA_FEATURE_SET_APM=1
  E: ID_ATA_FEATURE_SET_APM_ENABLED=1
  E: ID_ATA_FEATURE_SET_APM_CURRENT_VALUE=254
  E: ID_ATA_DOWNLOAD_MICROCODE=1
  E: ID_ATA_SATA=1
  E: ID_ATA_SATA_SIGNAL_RATE_GEN1=1
  E: ID_WWN=0x50f00000e1506588
  E: ID_WWN_WITH_EXTENSION=0x50f00000e1506588
  E: ID_SCSI_COMPAT=SATA_SAMSUNG_HM160HIS18PJDNQ506588
  E: ID_PATH=pci-0000:00:09.0-scsi-0:0:0:0
  E: ID_PART_TABLE_TYPE=dos
  E: UDISKS_PRESENTATION_NOPOLICY=0
  E: UDISKS_PARTITION=1
  E: UDISKS_PARTITION_SCHEME=mbr
  E: UDISKS_PARTITION_NUMBER=2
  E: UDISKS_PARTITION_TYPE=0x05
  E: UDISKS_PARTITION_SIZE=6537872384
  E: UDISKS_PARTITION_SLAVE=/sys/devices/pci0000:00/0000:00:09.0/host2/target2:0:0/2:0:0:0/block/sda
  E: UDISKS_PARTITION_OFFSET=153503136768
  E: UDISKS_PARTITION_ALIGNMENT_OFFSET=0
  E: DEVLINKS=/dev/disk/by-id/ata-SAMSUNG_HM160HI_S18PJDNQ506588-part2 /dev/disk/by-id/scsi-SATA_SAMSUNG_HM160HIS18PJDNQ506588-part2 /dev/disk/by-path/pci-0000:00:09.0-scsi-0:0:0:0-part2 /dev/disk/by-id/wwn-0x50f00000e1506588-part2
  
  P: /devices/pci0000:00/0000:00:09.0/host2/target2:0:0/2:0:0:0/block/sda/sda5
  N: sda5
  S: disk/by-id/ata-SAMSUNG_HM160HI_S18PJDNQ506588-part5
  S: disk/by-id/scsi-SATA_SAMSUNG_HM160HIS18PJDNQ506588-part5
  S: disk/by-path/pci-0000:00:09.0-scsi-0:0:0:0-part5
  S: disk/by-uuid/564b5473-3a78-4af3-8bb8-6e96f3420944
  S: disk/by-id/wwn-0x50f00000e1506588-part5
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:09.0/host2/target2:0:0/2:0:0:0/block/sda/sda5
  E: MAJOR=8
  E: MINOR=5
  E: DEVNAME=/dev/sda5
  E: DEVTYPE=partition
  E: SUBSYSTEM=block
  E: ID_ATA=1
  E: ID_TYPE=disk
  E: ID_BUS=ata
  E: ID_MODEL=SAMSUNG_HM160HI
  E: ID_MODEL_ENC=SAMSUNG\x20HM160HI\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20\x20
  E: ID_REVISION=HH100-21
  E: ID_SERIAL=SAMSUNG_HM160HI_S18PJDNQ506588
  E: ID_SERIAL_SHORT=S18PJDNQ506588
  E: ID_ATA_WRITE_CACHE=1
  E: ID_ATA_WRITE_CACHE_ENABLED=1
  E: ID_ATA_FEATURE_SET_PM=1
  E: ID_ATA_FEATURE_SET_PM_ENABLED=1
  E: ID_ATA_FEATURE_SET_SECURITY=1
  E: ID_ATA_FEATURE_SET_SECURITY_ENABLED=0
  E: ID_ATA_FEATURE_SET_SECURITY_ERASE_UNIT_MIN=60
  E: ID_ATA_FEATURE_SET_SECURITY_ENHANCED_ERASE_UNIT_MIN=60
  E: ID_ATA_FEATURE_SET_SECURITY_FROZEN=1
  E: ID_ATA_FEATURE_SET_SMART=1
  E: ID_ATA_FEATURE_SET_SMART_ENABLED=1
  E: ID_ATA_FEATURE_SET_APM=1
  E: ID_ATA_FEATURE_SET_APM_ENABLED=1
  E: ID_ATA_FEATURE_SET_APM_CURRENT_VALUE=254
  E: ID_ATA_DOWNLOAD_MICROCODE=1
  E: ID_ATA_SATA=1
  E: ID_ATA_SATA_SIGNAL_RATE_GEN1=1
  E: ID_WWN=0x50f00000e1506588
  E: ID_WWN_WITH_EXTENSION=0x50f00000e1506588
  E: ID_SCSI_COMPAT=SATA_SAMSUNG_HM160HIS18PJDNQ506588
  E: ID_PATH=pci-0000:00:09.0-scsi-0:0:0:0
  E: ID_PART_TABLE_TYPE=dos
  E: ID_FS_UUID=564b5473-3a78-4af3-8bb8-6e96f3420944
  E: ID_FS_UUID_ENC=564b5473-3a78-4af3-8bb8-6e96f3420944
  E: ID_FS_VERSION=2
  E: ID_FS_TYPE=swap
  E: ID_FS_USAGE=other
  E: UDISKS_PRESENTATION_NOPOLICY=0
  E: UDISKS_PARTITION=1
  E: UDISKS_PARTITION_SCHEME=mbr
  E: UDISKS_PARTITION_NUMBER=5
  E: UDISKS_PARTITION_TYPE=0x82
  E: UDISKS_PARTITION_SIZE=6537871360
  E: UDISKS_PARTITION_SLAVE=/sys/devices/pci0000:00/0000:00:09.0/host2/target2:0:0/2:0:0:0/block/sda
  E: UDISKS_PARTITION_OFFSET=153503137792
  E: UDISKS_PARTITION_ALIGNMENT_OFFSET=0
  E: DEVLINKS=/dev/disk/by-id/ata-SAMSUNG_HM160HI_S18PJDNQ506588-part5 /dev/disk/by-id/scsi-SATA_SAMSUNG_HM160HIS18PJDNQ506588-part5 /dev/disk/by-path/pci-0000:00:09.0-scsi-0:0:0:0-part5 /dev/disk/by-uuid/564b5473-3a78-4af3-8bb8-6e96f3420944 /dev/disk/by-id/wwn-0x50f00000e1506588-part5
  
  P: /devices/pci0000:00/0000:00:09.0/host2/target2:0:0/2:0:0:0/bsg/2:0:0:0
  N: bsg/2:0:0:0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:09.0/host2/target2:0:0/2:0:0:0/bsg/2:0:0:0
  E: MAJOR=253
  E: MINOR=1
  E: DEVNAME=/dev/bsg/2:0:0:0
  E: SUBSYSTEM=bsg
  
  P: /devices/pci0000:00/0000:00:09.0/host2/target2:0:0/2:0:0:0/scsi_device/2:0:0:0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:09.0/host2/target2:0:0/2:0:0:0/scsi_device/2:0:0:0
  E: SUBSYSTEM=scsi_device
  
  P: /devices/pci0000:00/0000:00:09.0/host2/target2:0:0/2:0:0:0/scsi_disk/2:0:0:0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:09.0/host2/target2:0:0/2:0:0:0/scsi_disk/2:0:0:0
  E: SUBSYSTEM=scsi_disk
  
  P: /devices/pci0000:00/0000:00:09.0/host2/target2:0:0/2:0:0:0/scsi_generic/sg1
  N: sg1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:09.0/host2/target2:0:0/2:0:0:0/scsi_generic/sg1
  E: MAJOR=21
  E: MINOR=1
  E: DEVNAME=/dev/sg1
  E: SUBSYSTEM=scsi_generic
  
  P: /devices/pci0000:00/0000:00:09.0/host3
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:09.0/host3
  E: DEVTYPE=scsi_host
  E: SUBSYSTEM=scsi
  
  P: /devices/pci0000:00/0000:00:09.0/host3/scsi_host/host3
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:09.0/host3/scsi_host/host3
  E: SUBSYSTEM=scsi_host
  
  P: /devices/pci0000:00/0000:00:09.0/host4
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:09.0/host4
  E: DEVTYPE=scsi_host
  E: SUBSYSTEM=scsi
  
  P: /devices/pci0000:00/0000:00:09.0/host4/scsi_host/host4
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:09.0/host4/scsi_host/host4
  E: SUBSYSTEM=scsi_host
  
  P: /devices/pci0000:00/0000:00:09.0/host5
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:09.0/host5
  E: DEVTYPE=scsi_host
  E: SUBSYSTEM=scsi
  
  P: /devices/pci0000:00/0000:00:09.0/host5/scsi_host/host5
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:09.0/host5/scsi_host/host5
  E: SUBSYSTEM=scsi_host
  
  P: /devices/pci0000:00/0000:00:0a.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:0a.0
  E: DRIVER=forcedeth
  E: PCI_CLASS=20000
  E: PCI_ID=10DE:054C
  E: PCI_SUBSYS_ID=103C:30CF
  E: PCI_SLOT_NAME=0000:00:0a.0
  E: MODALIAS=pci:v000010DEd0000054Csv0000103Csd000030CFbc02sc00i00
  E: SUBSYSTEM=pci
  
  P: /devices/pci0000:00/0000:00:0a.0/net/eth0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:0a.0/net/eth0
  E: INTERFACE=eth0
  E: IFINDEX=2
  E: SUBSYSTEM=net
  E: ID_VENDOR_FROM_DATABASE=nVidia Corporation
  E: ID_MODEL_FROM_DATABASE=MCP67 Ethernet
  E: ID_BUS=pci
  E: ID_VENDOR_ID=0x10de
  E: ID_MODEL_ID=0x054c
  E: ID_MM_CANDIDATE=1
  
  P: /devices/pci0000:00/0000:00:0c.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:0c.0
  E: DRIVER=pcieport
  E: PCI_CLASS=60400
  E: PCI_ID=10DE:0563
  E: PCI_SUBSYS_ID=10DE:0000
  E: PCI_SLOT_NAME=0000:00:0c.0
  E: MODALIAS=pci:v000010DEd00000563sv000010DEsd00000000bc06sc04i00
  E: SUBSYSTEM=pci
  
  P: /devices/pci0000:00/0000:00:0c.0/0000:00:0c.0:pcie08
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:0c.0/0000:00:0c.0:pcie08
  E: SUBSYSTEM=pci_express
  
  P: /devices/pci0000:00/0000:00:0c.0/pci_bus/0000:04
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:0c.0/pci_bus/0000:04
  E: SUBSYSTEM=pci_bus
  
  P: /devices/pci0000:00/0000:00:0d.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:0d.0
  E: DRIVER=pcieport
  E: PCI_CLASS=60400
  E: PCI_ID=10DE:0563
  E: PCI_SUBSYS_ID=10DE:0000
  E: PCI_SLOT_NAME=0000:00:0d.0
  E: MODALIAS=pci:v000010DEd00000563sv000010DEsd00000000bc06sc04i00
  E: SUBSYSTEM=pci
  
  P: /devices/pci0000:00/0000:00:0d.0/0000:00:0d.0:pcie08
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:0d.0/0000:00:0d.0:pcie08
  E: SUBSYSTEM=pci_express
  
  P: /devices/pci0000:00/0000:00:0d.0/0000:03:00.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:0d.0/0000:03:00.0
  E: DRIVER=ath5k
  E: PCI_CLASS=20000
  E: PCI_ID=168C:001C
  E: PCI_SUBSYS_ID=103C:137B
  E: PCI_SLOT_NAME=0000:03:00.0
  E: MODALIAS=pci:v0000168Cd0000001Csv0000103Csd0000137Bbc02sc00i00
  E: SUBSYSTEM=pci
  
  P: /devices/pci0000:00/0000:00:0d.0/0000:03:00.0/ieee80211/phy0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:0d.0/0000:03:00.0/ieee80211/phy0
  E: SUBSYSTEM=ieee80211
  
  P: /devices/pci0000:00/0000:00:0d.0/0000:03:00.0/ieee80211/phy0/rfkill1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:0d.0/0000:03:00.0/ieee80211/phy0/rfkill1
  E: RFKILL_NAME=phy0
  E: RFKILL_TYPE=wlan
  E: RFKILL_STATE=1
  E: SUBSYSTEM=rfkill
  
  P: /devices/pci0000:00/0000:00:0d.0/0000:03:00.0/leds/ath5k-phy0::rx
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:0d.0/0000:03:00.0/leds/ath5k-phy0::rx
  E: SUBSYSTEM=leds
  
  P: /devices/pci0000:00/0000:00:0d.0/0000:03:00.0/leds/ath5k-phy0::tx
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:0d.0/0000:03:00.0/leds/ath5k-phy0::tx
  E: SUBSYSTEM=leds
  
  P: /devices/pci0000:00/0000:00:0d.0/0000:03:00.0/net/wlan0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:0d.0/0000:03:00.0/net/wlan0
  E: DEVTYPE=wlan
  E: INTERFACE=wlan0
  E: IFINDEX=3
  E: SUBSYSTEM=net
  E: ID_VENDOR_FROM_DATABASE=Atheros Communications Inc.
  E: ID_MODEL_FROM_DATABASE=AR5001 Wireless Network Adapter
  E: ID_BUS=pci
  E: ID_VENDOR_ID=0x168c
  E: ID_MODEL_ID=0x001c
  E: ID_MM_CANDIDATE=1
  
  P: /devices/pci0000:00/0000:00:0d.0/pci_bus/0000:03
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:0d.0/pci_bus/0000:03
  E: SUBSYSTEM=pci_bus
  
  P: /devices/pci0000:00/0000:00:12.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:12.0
  E: DRIVER=nvidia
  E: PCI_CLASS=30000
  E: PCI_ID=10DE:0531
  E: PCI_SUBSYS_ID=103C:30CF
  E: PCI_SLOT_NAME=0000:00:12.0
  E: MODALIAS=pci:v000010DEd00000531sv0000103Csd000030CFbc03sc00i00
  E: SUBSYSTEM=pci
  
  P: /devices/pci0000:00/0000:00:12.0/i2c-2
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:12.0/i2c-2
  E: SUBSYSTEM=i2c
  
  P: /devices/pci0000:00/0000:00:12.0/i2c-3
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:12.0/i2c-3
  E: SUBSYSTEM=i2c
  
  P: /devices/pci0000:00/0000:00:12.0/i2c-4
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:12.0/i2c-4
  E: SUBSYSTEM=i2c
  
  P: /devices/pci0000:00/0000:00:12.0/i2c-5
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:12.0/i2c-5
  E: SUBSYSTEM=i2c
  
  P: /devices/pci0000:00/0000:00:18.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:18.0
  E: PCI_CLASS=60000
  E: PCI_ID=1022:1100
  E: PCI_SUBSYS_ID=0000:0000
  E: PCI_SLOT_NAME=0000:00:18.0
  E: MODALIAS=pci:v00001022d00001100sv00000000sd00000000bc06sc00i00
  E: SUBSYSTEM=pci
  
  P: /devices/pci0000:00/0000:00:18.1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:18.1
  E: PCI_CLASS=60000
  E: PCI_ID=1022:1101
  E: PCI_SUBSYS_ID=0000:0000
  E: PCI_SLOT_NAME=0000:00:18.1
  E: MODALIAS=pci:v00001022d00001101sv00000000sd00000000bc06sc00i00
  E: SUBSYSTEM=pci
  
  P: /devices/pci0000:00/0000:00:18.2
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:18.2
  E: PCI_CLASS=60000
  E: PCI_ID=1022:1102
  E: PCI_SUBSYS_ID=0000:0000
  E: PCI_SLOT_NAME=0000:00:18.2
  E: MODALIAS=pci:v00001022d00001102sv00000000sd00000000bc06sc00i00
  E: SUBSYSTEM=pci
  
  P: /devices/pci0000:00/0000:00:18.3
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:18.3
  E: DRIVER=k8temp
  E: PCI_CLASS=60000
  E: PCI_ID=1022:1103
  E: PCI_SUBSYS_ID=0000:0000
  E: PCI_SLOT_NAME=0000:00:18.3
  E: MODALIAS=pci:v00001022d00001103sv00000000sd00000000bc06sc00i00
  E: SUBSYSTEM=pci
  
  P: /devices/pci0000:00/0000:00:18.3/hwmon/hwmon1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/0000:00:18.3/hwmon/hwmon1
  E: SUBSYSTEM=hwmon
  
  P: /devices/pci0000:00/pci_bus/0000:00
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pci0000:00/pci_bus/0000:00
  E: SUBSYSTEM=pci_bus
  
  P: /devices/platform/Fixed MDIO bus.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/Fixed MDIO bus.0
  E: MODALIAS=platform:Fixed MDIO bus
  E: SUBSYSTEM=platform
  
  P: /devices/platform/Fixed MDIO bus.0/mdio_bus/0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/Fixed MDIO bus.0/mdio_bus/0
  E: SUBSYSTEM=mdio_bus
  
  P: /devices/platform/eisa.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/eisa.0
  E: MODALIAS=platform:eisa
  E: SUBSYSTEM=platform
  
  P: /devices/platform/hp-wmi
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/hp-wmi
  E: DRIVER=hp-wmi
  E: MODALIAS=platform:hp-wmi
  E: SUBSYSTEM=platform
  
  P: /devices/platform/hp-wmi/rfkill/rfkill0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/hp-wmi/rfkill/rfkill0
  E: RFKILL_NAME=hp-wifi
  E: RFKILL_TYPE=wlan
  E: RFKILL_STATE=1
  E: SUBSYSTEM=rfkill
  
  P: /devices/platform/i8042
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/i8042
  E: DRIVER=i8042
  E: MODALIAS=platform:i8042
  E: SUBSYSTEM=platform
  
  P: /devices/platform/i8042/serio0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/i8042/serio0
  E: DRIVER=atkbd
  E: SERIO_TYPE=06
  E: SERIO_PROTO=00
  E: SERIO_ID=00
  E: SERIO_EXTRA=00
  E: MODALIAS=serio:ty06pr00id00ex00
  E: SUBSYSTEM=serio
  E: DMI_VENDOR=Hewlett-Packard
  
  P: /devices/platform/i8042/serio0/input/input4
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/i8042/serio0/input/input4
  E: PRODUCT=11/1/1/ab41
  E: NAME="AT Translated Set 2 keyboard"
  E: PHYS="isa0060/serio0/input0"
  E: PROP=0
  E: EV=120013
  E: KEY=20000 0 20 0 0 0 0 500f 2100003 3803078 f900d401 feffffdf ffefffff ffffffff fffffffe
  E: MSC=10
  E: LED=7
  E: MODALIAS=input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8A,8C,8E,8F,98,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,C0,C1,D4,D9,E0,E1,E2,E3,EC,EE,185,1D1,ram4,l0,1,2,sfw
  E: SUBSYSTEM=input
  
  P: /devices/platform/i8042/serio0/input/input4/event4
  N: input/event4
  S: input/by-path/platform-i8042-serio-0-event-kbd
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/i8042/serio0/input/input4/event4
  E: MAJOR=13
  E: MINOR=68
  E: DEVNAME=/dev/input/event4
  E: SUBSYSTEM=input
  E: ID_INPUT=1
  E: ID_INPUT_KEY=1
  E: ID_INPUT_KEYBOARD=1
  E: ID_SERIAL=noserial
  E: ID_PATH=platform-i8042-serio-0
  E: XKBMODEL=pc105
  E: XKBLAYOUT=gb
  E: DEVLINKS=/dev/input/by-path/platform-i8042-serio-0-event-kbd
  E: DMI_VENDOR=Hewlett-Packard
  
  P: /devices/platform/i8042/serio1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/i8042/serio1
  E: DRIVER=psmouse
  E: SERIO_TYPE=01
  E: SERIO_PROTO=00
  E: SERIO_ID=00
  E: SERIO_EXTRA=00
  E: MODALIAS=serio:ty01pr00id00ex00
  E: SUBSYSTEM=serio
  
  P: /devices/platform/i8042/serio1/input/input7
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/i8042/serio1/input/input7
  E: PRODUCT=11/2/7/1b1
  E: NAME="SynPS/2 Synaptics TouchPad"
  E: PHYS="isa0060/serio1/input0"
  E: PROP=1
  E: EV=b
  E: KEY=420 0 30000 0 0 0 0 0 0 0 0
  E: ABS=11000003
  E: MODALIAS=input:b0011v0002p0007e01B1-e0,1,3,k110,111,145,14A,ra0,1,18,1C,mlsfw
  E: SUBSYSTEM=input
  
  P: /devices/platform/i8042/serio1/input/input7/event7
  N: input/event7
  S: input/by-path/platform-i8042-serio-1-event-mouse
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/i8042/serio1/input/input7/event7
  E: MAJOR=13
  E: MINOR=71
  E: DEVNAME=/dev/input/event7
  E: SUBSYSTEM=input
  E: ID_INPUT=1
  E: ID_INPUT_TOUCHPAD=1
  E: ID_SERIAL=noserial
  E: ID_PATH=platform-i8042-serio-1
  E: DMI_VENDOR=Hewlett-Packard
  E: DEVLINKS=/dev/input/by-path/platform-i8042-serio-1-event-mouse
  
  P: /devices/platform/i8042/serio1/input/input7/mouse0
  N: input/mouse0
  S: input/by-path/platform-i8042-serio-1-mouse
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/i8042/serio1/input/input7/mouse0
  E: MAJOR=13
  E: MINOR=32
  E: DEVNAME=/dev/input/mouse0
  E: SUBSYSTEM=input
  E: ID_INPUT=1
  E: ID_INPUT_TOUCHPAD=1
  E: ID_SERIAL=noserial
  E: ID_PATH=platform-i8042-serio-1
  E: DEVLINKS=/dev/input/by-path/platform-i8042-serio-1-mouse
  
  P: /devices/platform/pcspkr
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/pcspkr
  E: MODALIAS=platform:pcspkr
  E: SUBSYSTEM=platform
  
  P: /devices/platform/reg-dummy
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/reg-dummy
  E: MODALIAS=platform:reg-dummy
  E: SUBSYSTEM=platform
  
  P: /devices/platform/regulatory.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/regulatory.0
  E: MODALIAS=platform:regulatory
  E: SUBSYSTEM=platform
  
  P: /devices/platform/serial8250
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/serial8250
  E: DRIVER=serial8250
  E: MODALIAS=platform:serial8250
  E: SUBSYSTEM=platform
  
  P: /devices/platform/serial8250/tty/ttyS0
  N: ttyS0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/serial8250/tty/ttyS0
  E: MAJOR=4
  E: MINOR=64
  E: DEVNAME=/dev/ttyS0
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/platform/serial8250/tty/ttyS1
  N: ttyS1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/serial8250/tty/ttyS1
  E: MAJOR=4
  E: MINOR=65
  E: DEVNAME=/dev/ttyS1
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/platform/serial8250/tty/ttyS10
  N: ttyS10
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/serial8250/tty/ttyS10
  E: MAJOR=4
  E: MINOR=74
  E: DEVNAME=/dev/ttyS10
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/platform/serial8250/tty/ttyS11
  N: ttyS11
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/serial8250/tty/ttyS11
  E: MAJOR=4
  E: MINOR=75
  E: DEVNAME=/dev/ttyS11
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/platform/serial8250/tty/ttyS12
  N: ttyS12
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/serial8250/tty/ttyS12
  E: MAJOR=4
  E: MINOR=76
  E: DEVNAME=/dev/ttyS12
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/platform/serial8250/tty/ttyS13
  N: ttyS13
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/serial8250/tty/ttyS13
  E: MAJOR=4
  E: MINOR=77
  E: DEVNAME=/dev/ttyS13
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/platform/serial8250/tty/ttyS14
  N: ttyS14
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/serial8250/tty/ttyS14
  E: MAJOR=4
  E: MINOR=78
  E: DEVNAME=/dev/ttyS14
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/platform/serial8250/tty/ttyS15
  N: ttyS15
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/serial8250/tty/ttyS15
  E: MAJOR=4
  E: MINOR=79
  E: DEVNAME=/dev/ttyS15
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/platform/serial8250/tty/ttyS16
  N: ttyS16
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/serial8250/tty/ttyS16
  E: MAJOR=4
  E: MINOR=80
  E: DEVNAME=/dev/ttyS16
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/platform/serial8250/tty/ttyS17
  N: ttyS17
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/serial8250/tty/ttyS17
  E: MAJOR=4
  E: MINOR=81
  E: DEVNAME=/dev/ttyS17
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/platform/serial8250/tty/ttyS18
  N: ttyS18
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/serial8250/tty/ttyS18
  E: MAJOR=4
  E: MINOR=82
  E: DEVNAME=/dev/ttyS18
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/platform/serial8250/tty/ttyS19
  N: ttyS19
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/serial8250/tty/ttyS19
  E: MAJOR=4
  E: MINOR=83
  E: DEVNAME=/dev/ttyS19
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/platform/serial8250/tty/ttyS2
  N: ttyS2
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/serial8250/tty/ttyS2
  E: MAJOR=4
  E: MINOR=66
  E: DEVNAME=/dev/ttyS2
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/platform/serial8250/tty/ttyS20
  N: ttyS20
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/serial8250/tty/ttyS20
  E: MAJOR=4
  E: MINOR=84
  E: DEVNAME=/dev/ttyS20
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/platform/serial8250/tty/ttyS21
  N: ttyS21
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/serial8250/tty/ttyS21
  E: MAJOR=4
  E: MINOR=85
  E: DEVNAME=/dev/ttyS21
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/platform/serial8250/tty/ttyS22
  N: ttyS22
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/serial8250/tty/ttyS22
  E: MAJOR=4
  E: MINOR=86
  E: DEVNAME=/dev/ttyS22
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/platform/serial8250/tty/ttyS23
  N: ttyS23
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/serial8250/tty/ttyS23
  E: MAJOR=4
  E: MINOR=87
  E: DEVNAME=/dev/ttyS23
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/platform/serial8250/tty/ttyS24
  N: ttyS24
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/serial8250/tty/ttyS24
  E: MAJOR=4
  E: MINOR=88
  E: DEVNAME=/dev/ttyS24
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/platform/serial8250/tty/ttyS25
  N: ttyS25
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/serial8250/tty/ttyS25
  E: MAJOR=4
  E: MINOR=89
  E: DEVNAME=/dev/ttyS25
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/platform/serial8250/tty/ttyS26
  N: ttyS26
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/serial8250/tty/ttyS26
  E: MAJOR=4
  E: MINOR=90
  E: DEVNAME=/dev/ttyS26
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/platform/serial8250/tty/ttyS27
  N: ttyS27
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/serial8250/tty/ttyS27
  E: MAJOR=4
  E: MINOR=91
  E: DEVNAME=/dev/ttyS27
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/platform/serial8250/tty/ttyS28
  N: ttyS28
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/serial8250/tty/ttyS28
  E: MAJOR=4
  E: MINOR=92
  E: DEVNAME=/dev/ttyS28
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/platform/serial8250/tty/ttyS29
  N: ttyS29
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/serial8250/tty/ttyS29
  E: MAJOR=4
  E: MINOR=93
  E: DEVNAME=/dev/ttyS29
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/platform/serial8250/tty/ttyS3
  N: ttyS3
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/serial8250/tty/ttyS3
  E: MAJOR=4
  E: MINOR=67
  E: DEVNAME=/dev/ttyS3
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/platform/serial8250/tty/ttyS30
  N: ttyS30
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/serial8250/tty/ttyS30
  E: MAJOR=4
  E: MINOR=94
  E: DEVNAME=/dev/ttyS30
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/platform/serial8250/tty/ttyS31
  N: ttyS31
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/serial8250/tty/ttyS31
  E: MAJOR=4
  E: MINOR=95
  E: DEVNAME=/dev/ttyS31
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/platform/serial8250/tty/ttyS4
  N: ttyS4
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/serial8250/tty/ttyS4
  E: MAJOR=4
  E: MINOR=68
  E: DEVNAME=/dev/ttyS4
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/platform/serial8250/tty/ttyS5
  N: ttyS5
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/serial8250/tty/ttyS5
  E: MAJOR=4
  E: MINOR=69
  E: DEVNAME=/dev/ttyS5
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/platform/serial8250/tty/ttyS6
  N: ttyS6
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/serial8250/tty/ttyS6
  E: MAJOR=4
  E: MINOR=70
  E: DEVNAME=/dev/ttyS6
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/platform/serial8250/tty/ttyS7
  N: ttyS7
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/serial8250/tty/ttyS7
  E: MAJOR=4
  E: MINOR=71
  E: DEVNAME=/dev/ttyS7
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/platform/serial8250/tty/ttyS8
  N: ttyS8
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/serial8250/tty/ttyS8
  E: MAJOR=4
  E: MINOR=72
  E: DEVNAME=/dev/ttyS8
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/platform/serial8250/tty/ttyS9
  N: ttyS9
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/serial8250/tty/ttyS9
  E: MAJOR=4
  E: MINOR=73
  E: DEVNAME=/dev/ttyS9
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/platform/vesafb.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/vesafb.0
  E: DRIVER=vesafb
  E: MODALIAS=platform:vesafb
  E: SUBSYSTEM=platform
  
  P: /devices/platform/vesafb.0/graphics/fb0
  N: fb0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/platform/vesafb.0/graphics/fb0
  E: MAJOR=29
  E: MINOR=0
  E: DEVNAME=/dev/fb0
  E: SUBSYSTEM=graphics
  E: PRIMARY_DEVICE_FOR_DISPLAY=1
  
  P: /devices/pnp0/00:00
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pnp0/00:00
  E: SUBSYSTEM=pnp
  
  P: /devices/pnp0/00:01
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pnp0/00:01
  E: SUBSYSTEM=pnp
  
  P: /devices/pnp0/00:02
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pnp0/00:02
  E: DRIVER=system
  E: SUBSYSTEM=pnp
  
  P: /devices/pnp0/00:03
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pnp0/00:03
  E: DRIVER=system
  E: SUBSYSTEM=pnp
  
  P: /devices/pnp0/00:04
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pnp0/00:04
  E: DRIVER=system
  E: SUBSYSTEM=pnp
  
  P: /devices/pnp0/00:05
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pnp0/00:05
  E: SUBSYSTEM=pnp
  
  P: /devices/pnp0/00:06
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pnp0/00:06
  E: SUBSYSTEM=pnp
  
  P: /devices/pnp0/00:07
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pnp0/00:07
  E: DRIVER=rtc_cmos
  E: SUBSYSTEM=pnp
  
  P: /devices/pnp0/00:07/rtc/rtc0
  N: rtc0
  S: rtc
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pnp0/00:07/rtc/rtc0
  E: MAJOR=254
  E: MINOR=0
  E: DEVNAME=/dev/rtc0
  E: SUBSYSTEM=rtc
  E: DEVLINKS=/dev/rtc
  
  P: /devices/pnp0/00:08
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pnp0/00:08
  E: SUBSYSTEM=pnp
  
  P: /devices/pnp0/00:09
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pnp0/00:09
  E: DRIVER=i8042 kbd
  E: SUBSYSTEM=pnp
  
  P: /devices/pnp0/00:0a
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pnp0/00:0a
  E: DRIVER=i8042 aux
  E: SUBSYSTEM=pnp
  
  P: /devices/pnp0/00:0b
  E: UDEV_LOG=3
  E: DEVPATH=/devices/pnp0/00:0b
  E: DRIVER=system
  E: SUBSYSTEM=pnp
  
  P: /devices/software
  E: UDEV_LOG=3
  E: DEVPATH=/devices/software
  E: SUBSYSTEM=event_source
  
  P: /devices/tracepoint
  E: UDEV_LOG=3
  E: DEVPATH=/devices/tracepoint
  E: SUBSYSTEM=event_source
  
  P: /devices/virtual/backlight/acpi_video0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/backlight/acpi_video0
  E: SUBSYSTEM=backlight
  
  P: /devices/virtual/bdi/0:20
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/0:20
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/11:0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/11:0
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/1:0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/1:0
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/1:1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/1:1
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/1:10
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/1:10
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/1:11
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/1:11
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/1:12
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/1:12
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/1:13
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/1:13
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/1:14
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/1:14
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/1:15
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/1:15
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/1:2
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/1:2
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/1:3
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/1:3
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/1:4
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/1:4
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/1:5
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/1:5
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/1:6
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/1:6
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/1:7
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/1:7
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/1:8
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/1:8
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/1:9
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/1:9
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/7:0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/7:0
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/7:1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/7:1
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/7:2
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/7:2
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/7:3
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/7:3
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/7:4
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/7:4
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/7:5
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/7:5
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/7:6
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/7:6
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/7:7
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/7:7
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/8:0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/8:0
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/default
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/default
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/mtd-romap
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/mtd-romap
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/mtd-rwmap
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/mtd-rwmap
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/bdi/mtd-unmap
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/bdi/mtd-unmap
  E: SUBSYSTEM=bdi
  
  P: /devices/virtual/block/loop0
  N: loop0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/block/loop0
  E: MAJOR=7
  E: MINOR=0
  E: DEVNAME=/dev/loop0
  E: DEVTYPE=disk
  E: SUBSYSTEM=block
  E: UDISKS_PRESENTATION_NOPOLICY=1
  
  P: /devices/virtual/block/loop1
  N: loop1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/block/loop1
  E: MAJOR=7
  E: MINOR=1
  E: DEVNAME=/dev/loop1
  E: DEVTYPE=disk
  E: SUBSYSTEM=block
  E: UDISKS_PRESENTATION_NOPOLICY=1
  
  P: /devices/virtual/block/loop2
  N: loop2
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/block/loop2
  E: MAJOR=7
  E: MINOR=2
  E: DEVNAME=/dev/loop2
  E: DEVTYPE=disk
  E: SUBSYSTEM=block
  E: UDISKS_PRESENTATION_NOPOLICY=1
  
  P: /devices/virtual/block/loop3
  N: loop3
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/block/loop3
  E: MAJOR=7
  E: MINOR=3
  E: DEVNAME=/dev/loop3
  E: DEVTYPE=disk
  E: SUBSYSTEM=block
  E: UDISKS_PRESENTATION_NOPOLICY=1
  
  P: /devices/virtual/block/loop4
  N: loop4
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/block/loop4
  E: MAJOR=7
  E: MINOR=4
  E: DEVNAME=/dev/loop4
  E: DEVTYPE=disk
  E: SUBSYSTEM=block
  E: UDISKS_PRESENTATION_NOPOLICY=1
  
  P: /devices/virtual/block/loop5
  N: loop5
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/block/loop5
  E: MAJOR=7
  E: MINOR=5
  E: DEVNAME=/dev/loop5
  E: DEVTYPE=disk
  E: SUBSYSTEM=block
  E: UDISKS_PRESENTATION_NOPOLICY=1
  
  P: /devices/virtual/block/loop6
  N: loop6
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/block/loop6
  E: MAJOR=7
  E: MINOR=6
  E: DEVNAME=/dev/loop6
  E: DEVTYPE=disk
  E: SUBSYSTEM=block
  E: UDISKS_PRESENTATION_NOPOLICY=1
  
  P: /devices/virtual/block/loop7
  N: loop7
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/block/loop7
  E: MAJOR=7
  E: MINOR=7
  E: DEVNAME=/dev/loop7
  E: DEVTYPE=disk
  E: SUBSYSTEM=block
  E: UDISKS_PRESENTATION_NOPOLICY=1
  
  P: /devices/virtual/block/ram0
  N: ram0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/block/ram0
  E: MAJOR=1
  E: MINOR=0
  E: DEVNAME=/dev/ram0
  E: DEVTYPE=disk
  E: SUBSYSTEM=block
  
  P: /devices/virtual/block/ram1
  N: ram1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/block/ram1
  E: MAJOR=1
  E: MINOR=1
  E: DEVNAME=/dev/ram1
  E: DEVTYPE=disk
  E: SUBSYSTEM=block
  
  P: /devices/virtual/block/ram10
  N: ram10
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/block/ram10
  E: MAJOR=1
  E: MINOR=10
  E: DEVNAME=/dev/ram10
  E: DEVTYPE=disk
  E: SUBSYSTEM=block
  
  P: /devices/virtual/block/ram11
  N: ram11
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/block/ram11
  E: MAJOR=1
  E: MINOR=11
  E: DEVNAME=/dev/ram11
  E: DEVTYPE=disk
  E: SUBSYSTEM=block
  
  P: /devices/virtual/block/ram12
  N: ram12
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/block/ram12
  E: MAJOR=1
  E: MINOR=12
  E: DEVNAME=/dev/ram12
  E: DEVTYPE=disk
  E: SUBSYSTEM=block
  
  P: /devices/virtual/block/ram13
  N: ram13
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/block/ram13
  E: MAJOR=1
  E: MINOR=13
  E: DEVNAME=/dev/ram13
  E: DEVTYPE=disk
  E: SUBSYSTEM=block
  
  P: /devices/virtual/block/ram14
  N: ram14
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/block/ram14
  E: MAJOR=1
  E: MINOR=14
  E: DEVNAME=/dev/ram14
  E: DEVTYPE=disk
  E: SUBSYSTEM=block
  
  P: /devices/virtual/block/ram15
  N: ram15
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/block/ram15
  E: MAJOR=1
  E: MINOR=15
  E: DEVNAME=/dev/ram15
  E: DEVTYPE=disk
  E: SUBSYSTEM=block
  
  P: /devices/virtual/block/ram2
  N: ram2
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/block/ram2
  E: MAJOR=1
  E: MINOR=2
  E: DEVNAME=/dev/ram2
  E: DEVTYPE=disk
  E: SUBSYSTEM=block
  
  P: /devices/virtual/block/ram3
  N: ram3
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/block/ram3
  E: MAJOR=1
  E: MINOR=3
  E: DEVNAME=/dev/ram3
  E: DEVTYPE=disk
  E: SUBSYSTEM=block
  
  P: /devices/virtual/block/ram4
  N: ram4
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/block/ram4
  E: MAJOR=1
  E: MINOR=4
  E: DEVNAME=/dev/ram4
  E: DEVTYPE=disk
  E: SUBSYSTEM=block
  
  P: /devices/virtual/block/ram5
  N: ram5
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/block/ram5
  E: MAJOR=1
  E: MINOR=5
  E: DEVNAME=/dev/ram5
  E: DEVTYPE=disk
  E: SUBSYSTEM=block
  
  P: /devices/virtual/block/ram6
  N: ram6
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/block/ram6
  E: MAJOR=1
  E: MINOR=6
  E: DEVNAME=/dev/ram6
  E: DEVTYPE=disk
  E: SUBSYSTEM=block
  
  P: /devices/virtual/block/ram7
  N: ram7
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/block/ram7
  E: MAJOR=1
  E: MINOR=7
  E: DEVNAME=/dev/ram7
  E: DEVTYPE=disk
  E: SUBSYSTEM=block
  
  P: /devices/virtual/block/ram8
  N: ram8
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/block/ram8
  E: MAJOR=1
  E: MINOR=8
  E: DEVNAME=/dev/ram8
  E: DEVTYPE=disk
  E: SUBSYSTEM=block
  
  P: /devices/virtual/block/ram9
  N: ram9
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/block/ram9
  E: MAJOR=1
  E: MINOR=9
  E: DEVNAME=/dev/ram9
  E: DEVTYPE=disk
  E: SUBSYSTEM=block
  
  P: /devices/virtual/dmi/id
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/dmi/id
  E: MODALIAS=dmi:bvnHewlett-Packard:bvrF.30:bd04/24/2008:svnHewlett-Packard:pnHPPaviliondv9700NotebookPC:pvrRev1:rvnQuanta:rn30D1:rvr85.26:cvnQuanta:ct10:cvrN/A:
  E: SUBSYSTEM=dmi
  
  P: /devices/virtual/graphics/fbcon
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/graphics/fbcon
  E: SUBSYSTEM=graphics
  
  P: /devices/virtual/hwmon/hwmon0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/hwmon/hwmon0
  E: SUBSYSTEM=hwmon
  
  P: /devices/virtual/input/input5
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/input/input5
  E: PRODUCT=19/0/0/0
  E: NAME="HP WMI hotkeys"
  E: PHYS="wmi/input0"
  E: PROP=0
  E: EV=33
  E: KEY=40 0 0 0 10007 0 0 2100400 0 0 0 0
  E: MSC=10
  E: SW=22
  E: MODALIAS=input:b0019v0000p0000e0000-e0,1,4,5,k8A,94,99,E0,E1,E2,F0,166,ram4,lsfw1,5,
  E: SUBSYSTEM=input
  
  P: /devices/virtual/input/input5/event5
  N: input/event5
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/input/input5/event5
  E: MAJOR=13
  E: MINOR=69
  E: DEVNAME=/dev/input/event5
  E: SUBSYSTEM=input
  E: ID_INPUT=1
  E: ID_INPUT_KEY=1
  E: XKBMODEL=pc105
  E: XKBLAYOUT=gb
  E: DMI_VENDOR=Hewlett-Packard
  
  P: /devices/virtual/input/mice
  N: input/mice
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/input/mice
  E: MAJOR=13
  E: MINOR=63
  E: DEVNAME=/dev/input/mice
  E: SUBSYSTEM=input
  
  P: /devices/virtual/mem/full
  N: full
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/mem/full
  E: MAJOR=1
  E: MINOR=7
  E: DEVNAME=/dev/full
  E: DEVMODE=0666
  E: SUBSYSTEM=mem
  
  P: /devices/virtual/mem/kmsg
  N: kmsg
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/mem/kmsg
  E: MAJOR=1
  E: MINOR=11
  E: DEVNAME=/dev/kmsg
  E: SUBSYSTEM=mem
  
  P: /devices/virtual/mem/mem
  N: mem
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/mem/mem
  E: MAJOR=1
  E: MINOR=1
  E: DEVNAME=/dev/mem
  E: SUBSYSTEM=mem
  
  P: /devices/virtual/mem/null
  N: null
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/mem/null
  E: MAJOR=1
  E: MINOR=3
  E: DEVNAME=/dev/null
  E: DEVMODE=0666
  E: SUBSYSTEM=mem
  
  P: /devices/virtual/mem/oldmem
  N: oldmem
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/mem/oldmem
  E: MAJOR=1
  E: MINOR=12
  E: DEVNAME=/dev/oldmem
  E: SUBSYSTEM=mem
  
  P: /devices/virtual/mem/port
  N: port
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/mem/port
  E: MAJOR=1
  E: MINOR=4
  E: DEVNAME=/dev/port
  E: SUBSYSTEM=mem
  
  P: /devices/virtual/mem/random
  N: random
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/mem/random
  E: MAJOR=1
  E: MINOR=8
  E: DEVNAME=/dev/random
  E: DEVMODE=0666
  E: SUBSYSTEM=mem
  
  P: /devices/virtual/mem/urandom
  N: urandom
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/mem/urandom
  E: MAJOR=1
  E: MINOR=9
  E: DEVNAME=/dev/urandom
  E: DEVMODE=0666
  E: SUBSYSTEM=mem
  
  P: /devices/virtual/mem/zero
  N: zero
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/mem/zero
  E: MAJOR=1
  E: MINOR=5
  E: DEVNAME=/dev/zero
  E: DEVMODE=0666
  E: SUBSYSTEM=mem
  
  P: /devices/virtual/misc/cpu_dma_latency
  N: cpu_dma_latency
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/misc/cpu_dma_latency
  E: MAJOR=10
  E: MINOR=59
  E: DEVNAME=/dev/cpu_dma_latency
  E: SUBSYSTEM=misc
  
  P: /devices/virtual/misc/device-mapper
  N: mapper/control
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/misc/device-mapper
  E: MAJOR=10
  E: MINOR=236
  E: DEVNAME=/dev/mapper/control
  E: SUBSYSTEM=misc
  
  P: /devices/virtual/misc/ecryptfs
  N: ecryptfs
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/misc/ecryptfs
  E: MAJOR=10
  E: MINOR=61
  E: DEVNAME=/dev/ecryptfs
  E: SUBSYSTEM=misc
  
  P: /devices/virtual/misc/fuse
  N: fuse
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/misc/fuse
  E: MAJOR=10
  E: MINOR=229
  E: DEVNAME=/dev/fuse
  E: SUBSYSTEM=misc
  
  P: /devices/virtual/misc/hpet
  N: hpet
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/misc/hpet
  E: MAJOR=10
  E: MINOR=228
  E: DEVNAME=/dev/hpet
  E: SUBSYSTEM=misc
  
  P: /devices/virtual/misc/mcelog
  N: mcelog
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/misc/mcelog
  E: MAJOR=10
  E: MINOR=227
  E: DEVNAME=/dev/mcelog
  E: SUBSYSTEM=misc
  
  P: /devices/virtual/misc/network_latency
  N: network_latency
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/misc/network_latency
  E: MAJOR=10
  E: MINOR=58
  E: DEVNAME=/dev/network_latency
  E: SUBSYSTEM=misc
  
  P: /devices/virtual/misc/network_throughput
  N: network_throughput
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/misc/network_throughput
  E: MAJOR=10
  E: MINOR=57
  E: DEVNAME=/dev/network_throughput
  E: SUBSYSTEM=misc
  
  P: /devices/virtual/misc/pktcdvd
  N: pktcdvd/control
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/misc/pktcdvd
  E: MAJOR=10
  E: MINOR=60
  E: DEVNAME=/dev/pktcdvd/control
  E: SUBSYSTEM=misc
  
  P: /devices/virtual/misc/psaux
  N: psaux
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/misc/psaux
  E: MAJOR=10
  E: MINOR=1
  E: DEVNAME=/dev/psaux
  E: SUBSYSTEM=misc
  
  P: /devices/virtual/misc/rfkill
  N: rfkill
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/misc/rfkill
  E: MAJOR=10
  E: MINOR=62
  E: DEVNAME=/dev/rfkill
  E: SUBSYSTEM=misc
  E: TAGS=:udev-acl:
  
  P: /devices/virtual/misc/snapshot
  N: snapshot
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/misc/snapshot
  E: MAJOR=10
  E: MINOR=231
  E: DEVNAME=/dev/snapshot
  E: SUBSYSTEM=misc
  
  P: /devices/virtual/misc/tun
  N: net/tun
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/misc/tun
  E: MAJOR=10
  E: MINOR=200
  E: DEVNAME=/dev/net/tun
  E: SUBSYSTEM=misc
  
  P: /devices/virtual/misc/uinput
  N: uinput
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/misc/uinput
  E: MAJOR=10
  E: MINOR=223
  E: DEVNAME=/dev/uinput
  E: SUBSYSTEM=misc
  
  P: /devices/virtual/misc/vga_arbiter
  N: vga_arbiter
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/misc/vga_arbiter
  E: MAJOR=10
  E: MINOR=63
  E: DEVNAME=/dev/vga_arbiter
  E: SUBSYSTEM=misc
  
  P: /devices/virtual/net/lo
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/net/lo
  E: INTERFACE=lo
  E: IFINDEX=1
  E: SUBSYSTEM=net
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/ppp/ppp
  N: ppp
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/ppp/ppp
  E: MAJOR=108
  E: MINOR=0
  E: DEVNAME=/dev/ppp
  E: SUBSYSTEM=ppp
  
  P: /devices/virtual/regulator/regulator.0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/regulator/regulator.0
  E: SUBSYSTEM=regulator
  
  P: /devices/virtual/sound/seq
  N: snd/seq
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/sound/seq
  E: MAJOR=116
  E: MINOR=1
  E: DEVNAME=/dev/snd/seq
  E: SUBSYSTEM=sound
  E: TAGS=:udev-acl:
  
  P: /devices/virtual/sound/timer
  N: snd/timer
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/sound/timer
  E: MAJOR=116
  E: MINOR=33
  E: DEVNAME=/dev/snd/timer
  E: SUBSYSTEM=sound
  E: TAGS=:udev-acl:
  
  P: /devices/virtual/thermal/cooling_device0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/thermal/cooling_device0
  E: SUBSYSTEM=thermal
  
  P: /devices/virtual/thermal/cooling_device1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/thermal/cooling_device1
  E: SUBSYSTEM=thermal
  
  P: /devices/virtual/thermal/cooling_device2
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/thermal/cooling_device2
  E: SUBSYSTEM=thermal
  
  P: /devices/virtual/thermal/thermal_zone0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/thermal/thermal_zone0
  E: SUBSYSTEM=thermal
  
  P: /devices/virtual/tty/console
  N: console
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/console
  E: MAJOR=5
  E: MINOR=1
  E: DEVNAME=/dev/console
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/ptmx
  N: ptmx
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/ptmx
  E: MAJOR=5
  E: MINOR=2
  E: DEVNAME=/dev/ptmx
  E: DEVMODE=0666
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty
  N: tty
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty
  E: MAJOR=5
  E: MINOR=0
  E: DEVNAME=/dev/tty
  E: DEVMODE=0666
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty0
  N: tty0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty0
  E: MAJOR=4
  E: MINOR=0
  E: DEVNAME=/dev/tty0
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty1
  N: tty1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty1
  E: MAJOR=4
  E: MINOR=1
  E: DEVNAME=/dev/tty1
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty10
  N: tty10
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty10
  E: MAJOR=4
  E: MINOR=10
  E: DEVNAME=/dev/tty10
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty11
  N: tty11
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty11
  E: MAJOR=4
  E: MINOR=11
  E: DEVNAME=/dev/tty11
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty12
  N: tty12
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty12
  E: MAJOR=4
  E: MINOR=12
  E: DEVNAME=/dev/tty12
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty13
  N: tty13
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty13
  E: MAJOR=4
  E: MINOR=13
  E: DEVNAME=/dev/tty13
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty14
  N: tty14
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty14
  E: MAJOR=4
  E: MINOR=14
  E: DEVNAME=/dev/tty14
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty15
  N: tty15
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty15
  E: MAJOR=4
  E: MINOR=15
  E: DEVNAME=/dev/tty15
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty16
  N: tty16
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty16
  E: MAJOR=4
  E: MINOR=16
  E: DEVNAME=/dev/tty16
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty17
  N: tty17
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty17
  E: MAJOR=4
  E: MINOR=17
  E: DEVNAME=/dev/tty17
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty18
  N: tty18
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty18
  E: MAJOR=4
  E: MINOR=18
  E: DEVNAME=/dev/tty18
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty19
  N: tty19
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty19
  E: MAJOR=4
  E: MINOR=19
  E: DEVNAME=/dev/tty19
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty2
  N: tty2
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty2
  E: MAJOR=4
  E: MINOR=2
  E: DEVNAME=/dev/tty2
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty20
  N: tty20
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty20
  E: MAJOR=4
  E: MINOR=20
  E: DEVNAME=/dev/tty20
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty21
  N: tty21
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty21
  E: MAJOR=4
  E: MINOR=21
  E: DEVNAME=/dev/tty21
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty22
  N: tty22
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty22
  E: MAJOR=4
  E: MINOR=22
  E: DEVNAME=/dev/tty22
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty23
  N: tty23
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty23
  E: MAJOR=4
  E: MINOR=23
  E: DEVNAME=/dev/tty23
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty24
  N: tty24
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty24
  E: MAJOR=4
  E: MINOR=24
  E: DEVNAME=/dev/tty24
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty25
  N: tty25
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty25
  E: MAJOR=4
  E: MINOR=25
  E: DEVNAME=/dev/tty25
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty26
  N: tty26
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty26
  E: MAJOR=4
  E: MINOR=26
  E: DEVNAME=/dev/tty26
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty27
  N: tty27
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty27
  E: MAJOR=4
  E: MINOR=27
  E: DEVNAME=/dev/tty27
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty28
  N: tty28
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty28
  E: MAJOR=4
  E: MINOR=28
  E: DEVNAME=/dev/tty28
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty29
  N: tty29
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty29
  E: MAJOR=4
  E: MINOR=29
  E: DEVNAME=/dev/tty29
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty3
  N: tty3
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty3
  E: MAJOR=4
  E: MINOR=3
  E: DEVNAME=/dev/tty3
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty30
  N: tty30
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty30
  E: MAJOR=4
  E: MINOR=30
  E: DEVNAME=/dev/tty30
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty31
  N: tty31
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty31
  E: MAJOR=4
  E: MINOR=31
  E: DEVNAME=/dev/tty31
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty32
  N: tty32
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty32
  E: MAJOR=4
  E: MINOR=32
  E: DEVNAME=/dev/tty32
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty33
  N: tty33
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty33
  E: MAJOR=4
  E: MINOR=33
  E: DEVNAME=/dev/tty33
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty34
  N: tty34
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty34
  E: MAJOR=4
  E: MINOR=34
  E: DEVNAME=/dev/tty34
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty35
  N: tty35
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty35
  E: MAJOR=4
  E: MINOR=35
  E: DEVNAME=/dev/tty35
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty36
  N: tty36
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty36
  E: MAJOR=4
  E: MINOR=36
  E: DEVNAME=/dev/tty36
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty37
  N: tty37
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty37
  E: MAJOR=4
  E: MINOR=37
  E: DEVNAME=/dev/tty37
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty38
  N: tty38
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty38
  E: MAJOR=4
  E: MINOR=38
  E: DEVNAME=/dev/tty38
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty39
  N: tty39
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty39
  E: MAJOR=4
  E: MINOR=39
  E: DEVNAME=/dev/tty39
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty4
  N: tty4
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty4
  E: MAJOR=4
  E: MINOR=4
  E: DEVNAME=/dev/tty4
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty40
  N: tty40
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty40
  E: MAJOR=4
  E: MINOR=40
  E: DEVNAME=/dev/tty40
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty41
  N: tty41
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty41
  E: MAJOR=4
  E: MINOR=41
  E: DEVNAME=/dev/tty41
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty42
  N: tty42
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty42
  E: MAJOR=4
  E: MINOR=42
  E: DEVNAME=/dev/tty42
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty43
  N: tty43
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty43
  E: MAJOR=4
  E: MINOR=43
  E: DEVNAME=/dev/tty43
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty44
  N: tty44
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty44
  E: MAJOR=4
  E: MINOR=44
  E: DEVNAME=/dev/tty44
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty45
  N: tty45
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty45
  E: MAJOR=4
  E: MINOR=45
  E: DEVNAME=/dev/tty45
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty46
  N: tty46
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty46
  E: MAJOR=4
  E: MINOR=46
  E: DEVNAME=/dev/tty46
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty47
  N: tty47
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty47
  E: MAJOR=4
  E: MINOR=47
  E: DEVNAME=/dev/tty47
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty48
  N: tty48
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty48
  E: MAJOR=4
  E: MINOR=48
  E: DEVNAME=/dev/tty48
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty49
  N: tty49
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty49
  E: MAJOR=4
  E: MINOR=49
  E: DEVNAME=/dev/tty49
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty5
  N: tty5
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty5
  E: MAJOR=4
  E: MINOR=5
  E: DEVNAME=/dev/tty5
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty50
  N: tty50
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty50
  E: MAJOR=4
  E: MINOR=50
  E: DEVNAME=/dev/tty50
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty51
  N: tty51
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty51
  E: MAJOR=4
  E: MINOR=51
  E: DEVNAME=/dev/tty51
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty52
  N: tty52
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty52
  E: MAJOR=4
  E: MINOR=52
  E: DEVNAME=/dev/tty52
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty53
  N: tty53
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty53
  E: MAJOR=4
  E: MINOR=53
  E: DEVNAME=/dev/tty53
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty54
  N: tty54
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty54
  E: MAJOR=4
  E: MINOR=54
  E: DEVNAME=/dev/tty54
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty55
  N: tty55
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty55
  E: MAJOR=4
  E: MINOR=55
  E: DEVNAME=/dev/tty55
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty56
  N: tty56
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty56
  E: MAJOR=4
  E: MINOR=56
  E: DEVNAME=/dev/tty56
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty57
  N: tty57
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty57
  E: MAJOR=4
  E: MINOR=57
  E: DEVNAME=/dev/tty57
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty58
  N: tty58
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty58
  E: MAJOR=4
  E: MINOR=58
  E: DEVNAME=/dev/tty58
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty59
  N: tty59
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty59
  E: MAJOR=4
  E: MINOR=59
  E: DEVNAME=/dev/tty59
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty6
  N: tty6
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty6
  E: MAJOR=4
  E: MINOR=6
  E: DEVNAME=/dev/tty6
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty60
  N: tty60
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty60
  E: MAJOR=4
  E: MINOR=60
  E: DEVNAME=/dev/tty60
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty61
  N: tty61
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty61
  E: MAJOR=4
  E: MINOR=61
  E: DEVNAME=/dev/tty61
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty62
  N: tty62
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty62
  E: MAJOR=4
  E: MINOR=62
  E: DEVNAME=/dev/tty62
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty63
  N: tty63
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty63
  E: MAJOR=4
  E: MINOR=63
  E: DEVNAME=/dev/tty63
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty7
  N: tty7
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty7
  E: MAJOR=4
  E: MINOR=7
  E: DEVNAME=/dev/tty7
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty8
  N: tty8
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty8
  E: MAJOR=4
  E: MINOR=8
  E: DEVNAME=/dev/tty8
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/tty9
  N: tty9
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/tty9
  E: MAJOR=4
  E: MINOR=9
  E: DEVNAME=/dev/tty9
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/tty/ttyprintk
  N: ttyprintk
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/tty/ttyprintk
  E: MAJOR=5
  E: MINOR=3
  E: DEVNAME=/dev/ttyprintk
  E: SUBSYSTEM=tty
  E: ID_MM_CANDIDATE=1
  
  P: /devices/virtual/usbmon/usbmon0
  N: usbmon0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/usbmon/usbmon0
  E: MAJOR=252
  E: MINOR=0
  E: DEVNAME=/dev/usbmon0
  E: SUBSYSTEM=usbmon
  
  P: /devices/virtual/vc/vcs
  N: vcs
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/vc/vcs
  E: MAJOR=7
  E: MINOR=0
  E: DEVNAME=/dev/vcs
  E: SUBSYSTEM=vc
  
  P: /devices/virtual/vc/vcs1
  N: vcs1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/vc/vcs1
  E: MAJOR=7
  E: MINOR=1
  E: DEVNAME=/dev/vcs1
  E: SUBSYSTEM=vc
  
  P: /devices/virtual/vc/vcs2
  N: vcs2
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/vc/vcs2
  E: MAJOR=7
  E: MINOR=2
  E: DEVNAME=/dev/vcs2
  E: SUBSYSTEM=vc
  
  P: /devices/virtual/vc/vcs3
  N: vcs3
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/vc/vcs3
  E: MAJOR=7
  E: MINOR=3
  E: DEVNAME=/dev/vcs3
  E: SUBSYSTEM=vc
  
  P: /devices/virtual/vc/vcs4
  N: vcs4
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/vc/vcs4
  E: MAJOR=7
  E: MINOR=4
  E: DEVNAME=/dev/vcs4
  E: SUBSYSTEM=vc
  
  P: /devices/virtual/vc/vcs5
  N: vcs5
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/vc/vcs5
  E: MAJOR=7
  E: MINOR=5
  E: DEVNAME=/dev/vcs5
  E: SUBSYSTEM=vc
  
  P: /devices/virtual/vc/vcs6
  N: vcs6
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/vc/vcs6
  E: MAJOR=7
  E: MINOR=6
  E: DEVNAME=/dev/vcs6
  E: SUBSYSTEM=vc
  
  P: /devices/virtual/vc/vcsa
  N: vcsa
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/vc/vcsa
  E: MAJOR=7
  E: MINOR=128
  E: DEVNAME=/dev/vcsa
  E: SUBSYSTEM=vc
  
  P: /devices/virtual/vc/vcsa1
  N: vcsa1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/vc/vcsa1
  E: MAJOR=7
  E: MINOR=129
  E: DEVNAME=/dev/vcsa1
  E: SUBSYSTEM=vc
  
  P: /devices/virtual/vc/vcsa2
  N: vcsa2
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/vc/vcsa2
  E: MAJOR=7
  E: MINOR=130
  E: DEVNAME=/dev/vcsa2
  E: SUBSYSTEM=vc
  
  P: /devices/virtual/vc/vcsa3
  N: vcsa3
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/vc/vcsa3
  E: MAJOR=7
  E: MINOR=131
  E: DEVNAME=/dev/vcsa3
  E: SUBSYSTEM=vc
  
  P: /devices/virtual/vc/vcsa4
  N: vcsa4
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/vc/vcsa4
  E: MAJOR=7
  E: MINOR=132
  E: DEVNAME=/dev/vcsa4
  E: SUBSYSTEM=vc
  
  P: /devices/virtual/vc/vcsa5
  N: vcsa5
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/vc/vcsa5
  E: MAJOR=7
  E: MINOR=133
  E: DEVNAME=/dev/vcsa5
  E: SUBSYSTEM=vc
  
  P: /devices/virtual/vc/vcsa6
  N: vcsa6
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/vc/vcsa6
  E: MAJOR=7
  E: MINOR=134
  E: DEVNAME=/dev/vcsa6
  E: SUBSYSTEM=vc
  
  P: /devices/virtual/vtconsole/vtcon0
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/vtconsole/vtcon0
  E: SUBSYSTEM=vtconsole
  
  P: /devices/virtual/vtconsole/vtcon1
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/vtconsole/vtcon1
  E: SUBSYSTEM=vtconsole
  
  P: /devices/virtual/wmi/05901221-D566-11D1-B2F0-00A0C9062910
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/wmi/05901221-D566-11D1-B2F0-00A0C9062910
  E: MODALIAS=wmi:05901221-D566-11D1-B2F0-00A0C9062910
  E: SUBSYSTEM=wmi
  
  P: /devices/virtual/wmi/5FB7F034-2C63-45E9-BE91-3D44E2C707E4
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/wmi/5FB7F034-2C63-45E9-BE91-3D44E2C707E4
  E: MODALIAS=wmi:5FB7F034-2C63-45E9-BE91-3D44E2C707E4
  E: SUBSYSTEM=wmi
  
  P: /devices/virtual/wmi/95F24279-4D7B-4334-9387-ACCDC67EF61C
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/wmi/95F24279-4D7B-4334-9387-ACCDC67EF61C
  E: MODALIAS=wmi:95F24279-4D7B-4334-9387-ACCDC67EF61C
  E: SUBSYSTEM=wmi
  
  P: /devices/virtual/wmi/D0992BD4-A47C-4EFE-B072-324AEC92296C
  E: UDEV_LOG=3
  E: DEVPATH=/devices/virtual/wmi/D0992BD4-A47C-4EFE-B072-324AEC92296C
  E: MODALIAS=wmi:D0992BD4-A47C-4EFE-B072-324AEC92296C
  E: SUBSYSTEM=wmi
  
-----  udevinfo end -----
/devices/LNXSYSTM:00
/devices/LNXSYSTM:00/LNXCPU:00
/devices/LNXSYSTM:00/LNXCPU:01
/devices/LNXSYSTM:00/LNXPWRBN:00
/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3/event3
  name: /dev/input/event3
/devices/LNXSYSTM:00/device:00
/devices/LNXSYSTM:00/device:00/ACPI0003:00
/devices/LNXSYSTM:00/device:00/ACPI0003:00/power_supply/ACAD
/devices/LNXSYSTM:00/device:00/HPQ0007:00
/devices/LNXSYSTM:00/device:00/PNP0A08:00
/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00
/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/device:23
/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/device:24
/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/device:25
/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/device:26
/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input6
/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input6/event6
  name: /dev/input/event6
/devices/LNXSYSTM:00/device:00/PNP0A08:00/PNP0000:00
/devices/LNXSYSTM:00/device:00/PNP0A08:00/PNP0100:00
/devices/LNXSYSTM:00/device:00/PNP0A08:00/PNP0103:00
/devices/LNXSYSTM:00/device:00/PNP0A08:00/PNP0200:00
/devices/LNXSYSTM:00/device:00/PNP0A08:00/PNP0303:00
/devices/LNXSYSTM:00/device:00/PNP0A08:00/PNP0800:00
/devices/LNXSYSTM:00/device:00/PNP0A08:00/PNP0B00:00
/devices/LNXSYSTM:00/device:00/PNP0A08:00/PNP0C02:02
/devices/LNXSYSTM:00/device:00/PNP0A08:00/PNP0C04:00
/devices/LNXSYSTM:00/device:00/PNP0A08:00/PNP0C09:00
/devices/LNXSYSTM:00/device:00/PNP0A08:00/PNP0C0F:00
/devices/LNXSYSTM:00/device:00/PNP0A08:00/PNP0C0F:01
/devices/LNXSYSTM:00/device:00/PNP0A08:00/PNP0C0F:02
/devices/LNXSYSTM:00/device:00/PNP0A08:00/PNP0C0F:03
/devices/LNXSYSTM:00/device:00/PNP0A08:00/PNP0C0F:04
/devices/LNXSYSTM:00/device:00/PNP0A08:00/PNP0C0F:05
/devices/LNXSYSTM:00/device:00/PNP0A08:00/PNP0C0F:06
/devices/LNXSYSTM:00/device:00/PNP0A08:00/PNP0C0F:07
/devices/LNXSYSTM:00/device:00/PNP0A08:00/PNP0C0F:08
/devices/LNXSYSTM:00/device:00/PNP0A08:00/PNP0C0F:09
/devices/LNXSYSTM:00/device:00/PNP0A08:00/PNP0C0F:0a
/devices/LNXSYSTM:00/device:00/PNP0A08:00/PNP0C0F:0b
/devices/LNXSYSTM:00/device:00/PNP0A08:00/PNP0C0F:0c
/devices/LNXSYSTM:00/device:00/PNP0A08:00/PNP0C0F:0d
/devices/LNXSYSTM:00/device:00/PNP0A08:00/PNP0C0F:0e
/devices/LNXSYSTM:00/device:00/PNP0A08:00/PNP0C0F:0f
/devices/LNXSYSTM:00/device:00/PNP0A08:00/PNP0C0F:10
/devices/LNXSYSTM:00/device:00/PNP0A08:00/PNP0C0F:11
/devices/LNXSYSTM:00/device:00/PNP0A08:00/PNP0C0F:12
/devices/LNXSYSTM:00/device:00/PNP0A08:00/SYN013B:00
/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01
/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:02
/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:03
/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:04
/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:05
/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:06
/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:07
/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:08
/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:09
/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:09/device:0a
/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:0b
/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:0b/device:0c
/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:0d
/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:0d/device:0e
/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:0f
/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:0f/device:10
/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:11
/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:11/device:12
/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:13
/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:13/device:14
/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:15
/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:15/device:16
/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:17
/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:17/device:18
/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:17/device:18/device:19
/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:17/device:18/device:1a
/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:1b
/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:1b/device:1c
/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:1b/device:1c/device:1d
/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:1b/device:1c/device:1e
/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:1b/device:1f
/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:1b/device:1f/device:20
/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:1b/device:1f/device:21
/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:22
/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:22/PNP0C02:00
/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:22/PNP0C02:01
/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:27
/devices/LNXSYSTM:00/device:00/PNP0C01:00
/devices/LNXSYSTM:00/device:00/PNP0C0A:00
/devices/LNXSYSTM:00/device:00/PNP0C0A:00/power_supply/BAT0
/devices/LNXSYSTM:00/device:00/PNP0C0C:00
/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input2
/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input2/event2
  name: /dev/input/event2
/devices/LNXSYSTM:00/device:00/PNP0C0D:00
/devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
/devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1/event1
  name: /dev/input/event1
/devices/LNXSYSTM:00/device:00/PNP0C0E:00
/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input0
/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input0/event0
  name: /dev/input/event0
/devices/LNXSYSTM:00/device:00/PNP0C14:00
/devices/LNXSYSTM:00/device:00/PNP0C32:00
/devices/LNXSYSTM:00/device:00/PNP0C32:01
/devices/LNXSYSTM:00/device:00/PNP0C32:02
/devices/LNXSYSTM:00/device:00/PNP0C32:03
/devices/LNXSYSTM:00/device:00/PNP0C32:04
/devices/LNXSYSTM:00/device:00/PNP0C32:05
/devices/LNXSYSTM:00/device:00/PNP0C32:06
/devices/LNXSYSTM:00/device:28
/devices/LNXSYSTM:00/device:28/LNXTHERM:00
/devices/breakpoint
/devices/cpu
/devices/pci0000:00/0000:00:00.0
/devices/pci0000:00/0000:00:01.0
/devices/pci0000:00/0000:00:01.1
/devices/pci0000:00/0000:00:01.1/i2c-0
/devices/pci0000:00/0000:00:01.1/i2c-1
/devices/pci0000:00/0000:00:01.2
/devices/pci0000:00/0000:00:01.3
/devices/pci0000:00/0000:00:02.0
/devices/pci0000:00/0000:00:02.0/usb3
  name: /dev/bus/usb/003/001
/devices/pci0000:00/0000:00:02.0/usb3/3-0:1.0
/devices/pci0000:00/0000:00:02.0/usbmon/usbmon3
  name: /dev/usbmon3
/devices/pci0000:00/0000:00:02.1
/devices/pci0000:00/0000:00:02.1/usb1
  name: /dev/bus/usb/001/001
/devices/pci0000:00/0000:00:02.1/usb1/1-0:1.0
/devices/pci0000:00/0000:00:02.1/usbmon/usbmon1
  name: /dev/usbmon1
/devices/pci0000:00/0000:00:04.0
/devices/pci0000:00/0000:00:04.0/usb4
  name: /dev/bus/usb/004/001
/devices/pci0000:00/0000:00:04.0/usb4/4-0:1.0
/devices/pci0000:00/0000:00:04.0/usbmon/usbmon4
  name: /dev/usbmon4
/devices/pci0000:00/0000:00:04.1
/devices/pci0000:00/0000:00:04.1/usb2
  name: /dev/bus/usb/002/001
/devices/pci0000:00/0000:00:04.1/usb2/2-0:1.0
/devices/pci0000:00/0000:00:04.1/usbmon/usbmon2
  name: /dev/usbmon2
/devices/pci0000:00/0000:00:06.0
/devices/pci0000:00/0000:00:06.0/ata1/ata_port/ata1
/devices/pci0000:00/0000:00:06.0/ata1/link1/ata_link/link1
/devices/pci0000:00/0000:00:06.0/ata1/link1/dev1.0/ata_device/dev1.0
/devices/pci0000:00/0000:00:06.0/ata1/link1/dev1.1/ata_device/dev1.1
/devices/pci0000:00/0000:00:06.0/ata2/ata_port/ata2
/devices/pci0000:00/0000:00:06.0/ata2/link2/ata_link/link2
/devices/pci0000:00/0000:00:06.0/ata2/link2/dev2.0/ata_device/dev2.0
/devices/pci0000:00/0000:00:06.0/ata2/link2/dev2.1/ata_device/dev2.1
/devices/pci0000:00/0000:00:06.0/host0
/devices/pci0000:00/0000:00:06.0/host0/scsi_host/host0
/devices/pci0000:00/0000:00:06.0/host0/target0:0:0
/devices/pci0000:00/0000:00:06.0/host0/target0:0:0/0:0:0:0
/devices/pci0000:00/0000:00:06.0/host0/target0:0:0/0:0:0:0/block/sr0
  name: /dev/sr0
  links: /dev/scd0, /dev/disk/by-id/ata-TSSTcorp_CDDVDW_TS-L632N, /dev/disk/by-path/pci-0000:00:06.0-scsi-0:0:0:0, /dev/cdrom, /dev/cdrw, /dev/dvd, /dev/dvdrw
/devices/pci0000:00/0000:00:06.0/host0/target0:0:0/0:0:0:0/bsg/0:0:0:0
  name: /dev/bsg/0:0:0:0
/devices/pci0000:00/0000:00:06.0/host0/target0:0:0/0:0:0:0/scsi_device/0:0:0:0
/devices/pci0000:00/0000:00:06.0/host0/target0:0:0/0:0:0:0/scsi_generic/sg0
  name: /dev/sg0
/devices/pci0000:00/0000:00:06.0/host1
/devices/pci0000:00/0000:00:06.0/host1/scsi_host/host1
/devices/pci0000:00/0000:00:07.0
/devices/pci0000:00/0000:00:07.0/sound/card0
/devices/pci0000:00/0000:00:07.0/sound/card0/hwC0D0
  name: /dev/snd/hwC0D0
/devices/pci0000:00/0000:00:07.0/sound/card0/input8
/devices/pci0000:00/0000:00:07.0/sound/card0/input8/event8
  name: /dev/input/event8
/devices/pci0000:00/0000:00:07.0/sound/card0/pcmC0D0c
  name: /dev/snd/pcmC0D0c
/devices/pci0000:00/0000:00:07.0/sound/card0/pcmC0D0p
  name: /dev/snd/pcmC0D0p
/devices/pci0000:00/0000:00:07.0/sound/card0/pcmC0D1p
  name: /dev/snd/pcmC0D1p
/devices/pci0000:00/0000:00:07.0/sound/card0/controlC0
  name: /dev/snd/controlC0
  links: /dev/snd/by-path/pci-0000:00:07.0
/devices/pci0000:00/0000:00:08.0
/devices/pci0000:00/0000:00:08.0/0000:02:05.0
/devices/pci0000:00/0000:00:08.0/0000:02:05.0/fw0
  name: /dev/fw0
/devices/pci0000:00/0000:00:08.0/0000:02:05.1
/devices/pci0000:00/0000:00:08.0/0000:02:05.1/leds/mmc0::
/devices/pci0000:00/0000:00:08.0/0000:02:05.1/mmc_host/mmc0
/devices/pci0000:00/0000:00:08.0/0000:02:05.2
/devices/pci0000:00/0000:00:08.0/0000:02:05.3
/devices/pci0000:00/0000:00:08.0/pci_bus/0000:02
/devices/pci0000:00/0000:00:09.0
/devices/pci0000:00/0000:00:09.0/ata3/ata_port/ata3
/devices/pci0000:00/0000:00:09.0/ata3/link3/ata_link/link3
/devices/pci0000:00/0000:00:09.0/ata3/link3/dev3.0/ata_device/dev3.0
/devices/pci0000:00/0000:00:09.0/ata4/ata_port/ata4
/devices/pci0000:00/0000:00:09.0/ata4/link4/ata_link/link4
/devices/pci0000:00/0000:00:09.0/ata4/link4/dev4.0/ata_device/dev4.0
/devices/pci0000:00/0000:00:09.0/ata5/ata_port/ata5
/devices/pci0000:00/0000:00:09.0/ata5/link5/ata_link/link5
/devices/pci0000:00/0000:00:09.0/ata5/link5/dev5.0/ata_device/dev5.0
/devices/pci0000:00/0000:00:09.0/ata6/ata_port/ata6
/devices/pci0000:00/0000:00:09.0/ata6/link6/ata_link/link6
/devices/pci0000:00/0000:00:09.0/ata6/link6/dev6.0/ata_device/dev6.0
/devices/pci0000:00/0000:00:09.0/host2
/devices/pci0000:00/0000:00:09.0/host2/scsi_host/host2
/devices/pci0000:00/0000:00:09.0/host2/target2:0:0
/devices/pci0000:00/0000:00:09.0/host2/target2:0:0/2:0:0:0
/devices/pci0000:00/0000:00:09.0/host2/target2:0:0/2:0:0:0/block/sda
  name: /dev/sda
  links: /dev/disk/by-id/ata-SAMSUNG_HM160HI_S18PJDNQ506588, /dev/disk/by-id/scsi-SATA_SAMSUNG_HM160HIS18PJDNQ506588, /dev/disk/by-path/pci-0000:00:09.0-scsi-0:0:0:0, /dev/disk/by-id/wwn-0x50f00000e1506588
/devices/pci0000:00/0000:00:09.0/host2/target2:0:0/2:0:0:0/block/sda/sda1
  name: /dev/sda1
  links: /dev/disk/by-id/ata-SAMSUNG_HM160HI_S18PJDNQ506588-part1, /dev/disk/by-id/scsi-SATA_SAMSUNG_HM160HIS18PJDNQ506588-part1, /dev/disk/by-path/pci-0000:00:09.0-scsi-0:0:0:0-part1, /dev/disk/by-uuid/84e2594c-9753-4f69-8a20-584d6e60a569, /dev/disk/by-id/wwn-0x50f00000e1506588-part1, /dev/root
/devices/pci0000:00/0000:00:09.0/host2/target2:0:0/2:0:0:0/block/sda/sda2
  name: /dev/sda2
  links: /dev/disk/by-id/ata-SAMSUNG_HM160HI_S18PJDNQ506588-part2, /dev/disk/by-id/scsi-SATA_SAMSUNG_HM160HIS18PJDNQ506588-part2, /dev/disk/by-path/pci-0000:00:09.0-scsi-0:0:0:0-part2, /dev/disk/by-id/wwn-0x50f00000e1506588-part2
/devices/pci0000:00/0000:00:09.0/host2/target2:0:0/2:0:0:0/block/sda/sda5
  name: /dev/sda5
  links: /dev/disk/by-id/ata-SAMSUNG_HM160HI_S18PJDNQ506588-part5, /dev/disk/by-id/scsi-SATA_SAMSUNG_HM160HIS18PJDNQ506588-part5, /dev/disk/by-path/pci-0000:00:09.0-scsi-0:0:0:0-part5, /dev/disk/by-uuid/564b5473-3a78-4af3-8bb8-6e96f3420944, /dev/disk/by-id/wwn-0x50f00000e1506588-part5
/devices/pci0000:00/0000:00:09.0/host2/target2:0:0/2:0:0:0/bsg/2:0:0:0
  name: /dev/bsg/2:0:0:0
/devices/pci0000:00/0000:00:09.0/host2/target2:0:0/2:0:0:0/scsi_device/2:0:0:0
/devices/pci0000:00/0000:00:09.0/host2/target2:0:0/2:0:0:0/scsi_disk/2:0:0:0
/devices/pci0000:00/0000:00:09.0/host2/target2:0:0/2:0:0:0/scsi_generic/sg1
  name: /dev/sg1
/devices/pci0000:00/0000:00:09.0/host3
/devices/pci0000:00/0000:00:09.0/host3/scsi_host/host3
/devices/pci0000:00/0000:00:09.0/host4
/devices/pci0000:00/0000:00:09.0/host4/scsi_host/host4
/devices/pci0000:00/0000:00:09.0/host5
/devices/pci0000:00/0000:00:09.0/host5/scsi_host/host5
/devices/pci0000:00/0000:00:0a.0
/devices/pci0000:00/0000:00:0a.0/net/eth0
/devices/pci0000:00/0000:00:0c.0
/devices/pci0000:00/0000:00:0c.0/0000:00:0c.0:pcie08
/devices/pci0000:00/0000:00:0c.0/pci_bus/0000:04
/devices/pci0000:00/0000:00:0d.0
/devices/pci0000:00/0000:00:0d.0/0000:00:0d.0:pcie08
/devices/pci0000:00/0000:00:0d.0/0000:03:00.0
/devices/pci0000:00/0000:00:0d.0/0000:03:00.0/ieee80211/phy0
/devices/pci0000:00/0000:00:0d.0/0000:03:00.0/ieee80211/phy0/rfkill1
/devices/pci0000:00/0000:00:0d.0/0000:03:00.0/leds/ath5k-phy0::rx
/devices/pci0000:00/0000:00:0d.0/0000:03:00.0/leds/ath5k-phy0::tx
/devices/pci0000:00/0000:00:0d.0/0000:03:00.0/net/wlan0
/devices/pci0000:00/0000:00:0d.0/pci_bus/0000:03
/devices/pci0000:00/0000:00:12.0
/devices/pci0000:00/0000:00:12.0/i2c-2
/devices/pci0000:00/0000:00:12.0/i2c-3
/devices/pci0000:00/0000:00:12.0/i2c-4
/devices/pci0000:00/0000:00:12.0/i2c-5
/devices/pci0000:00/0000:00:18.0
/devices/pci0000:00/0000:00:18.1
/devices/pci0000:00/0000:00:18.2
/devices/pci0000:00/0000:00:18.3
/devices/pci0000:00/0000:00:18.3/hwmon/hwmon1
/devices/pci0000:00/pci_bus/0000:00
/devices/platform/Fixed
/devices/platform/Fixed
/devices/platform/eisa.0
/devices/platform/hp-wmi
/devices/platform/hp-wmi/rfkill/rfkill0
/devices/platform/i8042
/devices/platform/i8042/serio0
/devices/platform/i8042/serio0/input/input4
/devices/platform/i8042/serio0/input/input4/event4
  name: /dev/input/event4
  links: /dev/input/by-path/platform-i8042-serio-0-event-kbd
/devices/platform/i8042/serio1
/devices/platform/i8042/serio1/input/input7
/devices/platform/i8042/serio1/input/input7/event7
  name: /dev/input/event7
  links: /dev/input/by-path/platform-i8042-serio-1-event-mouse
/devices/platform/i8042/serio1/input/input7/mouse0
  name: /dev/input/mouse0
  links: /dev/input/by-path/platform-i8042-serio-1-mouse
/devices/platform/pcspkr
/devices/platform/reg-dummy
/devices/platform/regulatory.0
/devices/platform/serial8250
/devices/platform/serial8250/tty/ttyS0
  name: /dev/ttyS0
/devices/platform/serial8250/tty/ttyS1
  name: /dev/ttyS1
/devices/platform/serial8250/tty/ttyS10
  name: /dev/ttyS10
/devices/platform/serial8250/tty/ttyS11
  name: /dev/ttyS11
/devices/platform/serial8250/tty/ttyS12
  name: /dev/ttyS12
/devices/platform/serial8250/tty/ttyS13
  name: /dev/ttyS13
/devices/platform/serial8250/tty/ttyS14
  name: /dev/ttyS14
/devices/platform/serial8250/tty/ttyS15
  name: /dev/ttyS15
/devices/platform/serial8250/tty/ttyS16
  name: /dev/ttyS16
/devices/platform/serial8250/tty/ttyS17
  name: /dev/ttyS17
/devices/platform/serial8250/tty/ttyS18
  name: /dev/ttyS18
/devices/platform/serial8250/tty/ttyS19
  name: /dev/ttyS19
/devices/platform/serial8250/tty/ttyS2
  name: /dev/ttyS2
/devices/platform/serial8250/tty/ttyS20
  name: /dev/ttyS20
/devices/platform/serial8250/tty/ttyS21
  name: /dev/ttyS21
/devices/platform/serial8250/tty/ttyS22
  name: /dev/ttyS22
/devices/platform/serial8250/tty/ttyS23
  name: /dev/ttyS23
/devices/platform/serial8250/tty/ttyS24
  name: /dev/ttyS24
/devices/platform/serial8250/tty/ttyS25
  name: /dev/ttyS25
/devices/platform/serial8250/tty/ttyS26
  name: /dev/ttyS26
/devices/platform/serial8250/tty/ttyS27
  name: /dev/ttyS27
/devices/platform/serial8250/tty/ttyS28
  name: /dev/ttyS28
/devices/platform/serial8250/tty/ttyS29
  name: /dev/ttyS29
/devices/platform/serial8250/tty/ttyS3
  name: /dev/ttyS3
/devices/platform/serial8250/tty/ttyS30
  name: /dev/ttyS30
/devices/platform/serial8250/tty/ttyS31
  name: /dev/ttyS31
/devices/platform/serial8250/tty/ttyS4
  name: /dev/ttyS4
/devices/platform/serial8250/tty/ttyS5
  name: /dev/ttyS5
/devices/platform/serial8250/tty/ttyS6
  name: /dev/ttyS6
/devices/platform/serial8250/tty/ttyS7
  name: /dev/ttyS7
/devices/platform/serial8250/tty/ttyS8
  name: /dev/ttyS8
/devices/platform/serial8250/tty/ttyS9
  name: /dev/ttyS9
/devices/platform/vesafb.0
/devices/platform/vesafb.0/graphics/fb0
  name: /dev/fb0
/devices/pnp0/00:00
/devices/pnp0/00:01
/devices/pnp0/00:02
/devices/pnp0/00:03
/devices/pnp0/00:04
/devices/pnp0/00:05
/devices/pnp0/00:06
/devices/pnp0/00:07
/devices/pnp0/00:07/rtc/rtc0
  name: /dev/rtc0
  links: /dev/rtc
/devices/pnp0/00:08
/devices/pnp0/00:09
/devices/pnp0/00:0a
/devices/pnp0/00:0b
/devices/software
/devices/tracepoint
/devices/virtual/backlight/acpi_video0
/devices/virtual/bdi/0:20
/devices/virtual/bdi/11:0
/devices/virtual/bdi/1:0
/devices/virtual/bdi/1:1
/devices/virtual/bdi/1:10
/devices/virtual/bdi/1:11
/devices/virtual/bdi/1:12
/devices/virtual/bdi/1:13
/devices/virtual/bdi/1:14
/devices/virtual/bdi/1:15
/devices/virtual/bdi/1:2
/devices/virtual/bdi/1:3
/devices/virtual/bdi/1:4
/devices/virtual/bdi/1:5
/devices/virtual/bdi/1:6
/devices/virtual/bdi/1:7
/devices/virtual/bdi/1:8
/devices/virtual/bdi/1:9
/devices/virtual/bdi/7:0
/devices/virtual/bdi/7:1
/devices/virtual/bdi/7:2
/devices/virtual/bdi/7:3
/devices/virtual/bdi/7:4
/devices/virtual/bdi/7:5
/devices/virtual/bdi/7:6
/devices/virtual/bdi/7:7
/devices/virtual/bdi/8:0
/devices/virtual/bdi/default
/devices/virtual/bdi/mtd-romap
/devices/virtual/bdi/mtd-rwmap
/devices/virtual/bdi/mtd-unmap
/devices/virtual/block/loop0
  name: /dev/loop0
/devices/virtual/block/loop1
  name: /dev/loop1
/devices/virtual/block/loop2
  name: /dev/loop2
/devices/virtual/block/loop3
  name: /dev/loop3
/devices/virtual/block/loop4
  name: /dev/loop4
/devices/virtual/block/loop5
  name: /dev/loop5
/devices/virtual/block/loop6
  name: /dev/loop6
/devices/virtual/block/loop7
  name: /dev/loop7
/devices/virtual/block/ram0
  name: /dev/ram0
/devices/virtual/block/ram1
  name: /dev/ram1
/devices/virtual/block/ram10
  name: /dev/ram10
/devices/virtual/block/ram11
  name: /dev/ram11
/devices/virtual/block/ram12
  name: /dev/ram12
/devices/virtual/block/ram13
  name: /dev/ram13
/devices/virtual/block/ram14
  name: /dev/ram14
/devices/virtual/block/ram15
  name: /dev/ram15
/devices/virtual/block/ram2
  name: /dev/ram2
/devices/virtual/block/ram3
  name: /dev/ram3
/devices/virtual/block/ram4
  name: /dev/ram4
/devices/virtual/block/ram5
  name: /dev/ram5
/devices/virtual/block/ram6
  name: /dev/ram6
/devices/virtual/block/ram7
  name: /dev/ram7
/devices/virtual/block/ram8
  name: /dev/ram8
/devices/virtual/block/ram9
  name: /dev/ram9
/devices/virtual/dmi/id
/devices/virtual/graphics/fbcon
/devices/virtual/hwmon/hwmon0
/devices/virtual/input/input5
/devices/virtual/input/input5/event5
  name: /dev/input/event5
/devices/virtual/input/mice
  name: /dev/input/mice
/devices/virtual/mem/full
  name: /dev/full
/devices/virtual/mem/kmsg
  name: /dev/kmsg
/devices/virtual/mem/mem
  name: /dev/mem
/devices/virtual/mem/null
  name: /dev/null
/devices/virtual/mem/oldmem
  name: /dev/oldmem
/devices/virtual/mem/port
  name: /dev/port
/devices/virtual/mem/random
  name: /dev/random
/devices/virtual/mem/urandom
  name: /dev/urandom
/devices/virtual/mem/zero
  name: /dev/zero
/devices/virtual/misc/cpu_dma_latency
  name: /dev/cpu_dma_latency
/devices/virtual/misc/device-mapper
  name: /dev/mapper/control
/devices/virtual/misc/ecryptfs
  name: /dev/ecryptfs
/devices/virtual/misc/fuse
  name: /dev/fuse
/devices/virtual/misc/hpet
  name: /dev/hpet
/devices/virtual/misc/mcelog
  name: /dev/mcelog
/devices/virtual/misc/network_latency
  name: /dev/network_latency
/devices/virtual/misc/network_throughput
  name: /dev/network_throughput
/devices/virtual/misc/pktcdvd
  name: /dev/pktcdvd/control
/devices/virtual/misc/psaux
  name: /dev/psaux
/devices/virtual/misc/rfkill
  name: /dev/rfkill
/devices/virtual/misc/snapshot
  name: /dev/snapshot
/devices/virtual/misc/tun
  name: /dev/net/tun
/devices/virtual/misc/uinput
  name: /dev/uinput
/devices/virtual/misc/vga_arbiter
  name: /dev/vga_arbiter
/devices/virtual/net/lo
/devices/virtual/ppp/ppp
  name: /dev/ppp
/devices/virtual/regulator/regulator.0
/devices/virtual/sound/seq
  name: /dev/snd/seq
/devices/virtual/sound/timer
  name: /dev/snd/timer
/devices/virtual/thermal/cooling_device0
/devices/virtual/thermal/cooling_device1
/devices/virtual/thermal/cooling_device2
/devices/virtual/thermal/thermal_zone0
/devices/virtual/tty/console
  name: /dev/console
/devices/virtual/tty/ptmx
  name: /dev/ptmx
/devices/virtual/tty/tty
  name: /dev/tty
/devices/virtual/tty/tty0
  name: /dev/tty0
/devices/virtual/tty/tty1
  name: /dev/tty1
/devices/virtual/tty/tty10
  name: /dev/tty10
/devices/virtual/tty/tty11
  name: /dev/tty11
/devices/virtual/tty/tty12
  name: /dev/tty12
/devices/virtual/tty/tty13
  name: /dev/tty13
/devices/virtual/tty/tty14
  name: /dev/tty14
/devices/virtual/tty/tty15
  name: /dev/tty15
/devices/virtual/tty/tty16
  name: /dev/tty16
/devices/virtual/tty/tty17
  name: /dev/tty17
/devices/virtual/tty/tty18
  name: /dev/tty18
/devices/virtual/tty/tty19
  name: /dev/tty19
/devices/virtual/tty/tty2
  name: /dev/tty2
/devices/virtual/tty/tty20
  name: /dev/tty20
/devices/virtual/tty/tty21
  name: /dev/tty21
/devices/virtual/tty/tty22
  name: /dev/tty22
/devices/virtual/tty/tty23
  name: /dev/tty23
/devices/virtual/tty/tty24
  name: /dev/tty24
/devices/virtual/tty/tty25
  name: /dev/tty25
/devices/virtual/tty/tty26
  name: /dev/tty26
/devices/virtual/tty/tty27
  name: /dev/tty27
/devices/virtual/tty/tty28
  name: /dev/tty28
/devices/virtual/tty/tty29
  name: /dev/tty29
/devices/virtual/tty/tty3
  name: /dev/tty3
/devices/virtual/tty/tty30
  name: /dev/tty30
/devices/virtual/tty/tty31
  name: /dev/tty31
/devices/virtual/tty/tty32
  name: /dev/tty32
/devices/virtual/tty/tty33
  name: /dev/tty33
/devices/virtual/tty/tty34
  name: /dev/tty34
/devices/virtual/tty/tty35
  name: /dev/tty35
/devices/virtual/tty/tty36
  name: /dev/tty36
/devices/virtual/tty/tty37
  name: /dev/tty37
/devices/virtual/tty/tty38
  name: /dev/tty38
/devices/virtual/tty/tty39
  name: /dev/tty39
/devices/virtual/tty/tty4
  name: /dev/tty4
/devices/virtual/tty/tty40
  name: /dev/tty40
/devices/virtual/tty/tty41
  name: /dev/tty41
/devices/virtual/tty/tty42
  name: /dev/tty42
/devices/virtual/tty/tty43
  name: /dev/tty43
/devices/virtual/tty/tty44
  name: /dev/tty44
/devices/virtual/tty/tty45
  name: /dev/tty45
/devices/virtual/tty/tty46
  name: /dev/tty46
/devices/virtual/tty/tty47
  name: /dev/tty47
/devices/virtual/tty/tty48
  name: /dev/tty48
/devices/virtual/tty/tty49
  name: /dev/tty49
/devices/virtual/tty/tty5
  name: /dev/tty5
/devices/virtual/tty/tty50
  name: /dev/tty50
/devices/virtual/tty/tty51
  name: /dev/tty51
/devices/virtual/tty/tty52
  name: /dev/tty52
/devices/virtual/tty/tty53
  name: /dev/tty53
/devices/virtual/tty/tty54
  name: /dev/tty54
/devices/virtual/tty/tty55
  name: /dev/tty55
/devices/virtual/tty/tty56
  name: /dev/tty56
/devices/virtual/tty/tty57
  name: /dev/tty57
/devices/virtual/tty/tty58
  name: /dev/tty58
/devices/virtual/tty/tty59
  name: /dev/tty59
/devices/virtual/tty/tty6
  name: /dev/tty6
/devices/virtual/tty/tty60
  name: /dev/tty60
/devices/virtual/tty/tty61
  name: /dev/tty61
/devices/virtual/tty/tty62
  name: /dev/tty62
/devices/virtual/tty/tty63
  name: /dev/tty63
/devices/virtual/tty/tty7
  name: /dev/tty7
/devices/virtual/tty/tty8
  name: /dev/tty8
/devices/virtual/tty/tty9
  name: /dev/tty9
/devices/virtual/tty/ttyprintk
  name: /dev/ttyprintk
/devices/virtual/usbmon/usbmon0
  name: /dev/usbmon0
/devices/virtual/vc/vcs
  name: /dev/vcs
/devices/virtual/vc/vcs1
  name: /dev/vcs1
/devices/virtual/vc/vcs2
  name: /dev/vcs2
/devices/virtual/vc/vcs3
  name: /dev/vcs3
/devices/virtual/vc/vcs4
  name: /dev/vcs4
/devices/virtual/vc/vcs5
  name: /dev/vcs5
/devices/virtual/vc/vcs6
  name: /dev/vcs6
/devices/virtual/vc/vcsa
  name: /dev/vcsa
/devices/virtual/vc/vcsa1
  name: /dev/vcsa1
/devices/virtual/vc/vcsa2
  name: /dev/vcsa2
/devices/virtual/vc/vcsa3
  name: /dev/vcsa3
/devices/virtual/vc/vcsa4
  name: /dev/vcsa4
/devices/virtual/vc/vcsa5
  name: /dev/vcsa5
/devices/virtual/vc/vcsa6
  name: /dev/vcsa6
/devices/virtual/vtconsole/vtcon0
/devices/virtual/vtconsole/vtcon1
/devices/virtual/wmi/05901221-D566-11D1-B2F0-00A0C9062910
/devices/virtual/wmi/5FB7F034-2C63-45E9-BE91-3D44E2C707E4
/devices/virtual/wmi/95F24279-4D7B-4334-9387-ACCDC67EF61C
/devices/virtual/wmi/D0992BD4-A47C-4EFE-B072-324AEC92296C
>> int.13: device names
>> int.14: soft raid
----- soft raid devices -----
----- soft raid devices end -----
>> int.15: geo
>> int.16: parent
  prop read: rdCR.lZF+r4EgHp4 (failed)
  old prop read: rdCR.lZF+r4EgHp4 (failed)
  prop read: rdCR.n_7QNeEnh23 (failed)
  old prop read: rdCR.n_7QNeEnh23 (failed)
  prop read: rdCR.EMpH5pjcahD (failed)
  old prop read: rdCR.EMpH5pjcahD (failed)
  prop read: rdCR.f5u1ucRm+H9 (failed)
  old prop read: rdCR.f5u1ucRm+H9 (failed)
  prop read: rdCR.8uRK7LxiIA2 (failed)
  old prop read: rdCR.8uRK7LxiIA2 (failed)
  prop read: rdCR.AJKleuxpiP0 (failed)
  old prop read: rdCR.AJKleuxpiP0 (failed)
  prop read: rdCR.9N+EecqykME (failed)
  old prop read: rdCR.9N+EecqykME (failed)
  prop read: rdCR.CxwsZFjVASF (failed)
  old prop read: rdCR.CxwsZFjVASF (failed)
  prop read: /org/freedesktop/Hal/devices/pci_10de_547 (failed)
  prop read: qLht.u35Y1PF8No9 (failed)
  old prop read: qLht.u35Y1PF8No9 (failed)
  prop read: /org/freedesktop/Hal/devices/pci_10de_548 (failed)
  prop read: vSkL.xA1wnWm82VD (failed)
  old prop read: vSkL.xA1wnWm82VD (failed)
  prop read: /org/freedesktop/Hal/devices/pci_10de_542 (failed)
  prop read: mnDB.+RSl1sRdLr0 (failed)
  old prop read: mnDB.+RSl1sRdLr0 (failed)
  prop read: /org/freedesktop/Hal/devices/pci_10de_541 (failed)
  prop read: e6j0.oaQ29_XvCV7 (failed)
  old prop read: e6j0.oaQ29_XvCV7 (failed)
  prop read: /org/freedesktop/Hal/devices/pci_10de_543 (failed)
  prop read: VRCs.wqrTvOknH2C (failed)
  old prop read: VRCs.wqrTvOknH2C (failed)
  prop read: /org/freedesktop/Hal/devices/pci_10de_55e (failed)
  prop read: _Znp.fdoO6mi4bbA (failed)
  old prop read: _Znp.fdoO6mi4bbA (failed)
  prop read: /org/freedesktop/Hal/devices/pci_10de_55f (failed)
  prop read: ruGf.Q2YEkqhxk71 (failed)
  old prop read: ruGf.Q2YEkqhxk71 (failed)
  prop read: /org/freedesktop/Hal/devices/pci_10de_55e_0 (failed)
  prop read: 8otl.fdoO6mi4bbA (failed)
  old prop read: 8otl.fdoO6mi4bbA (failed)
  prop read: /org/freedesktop/Hal/devices/pci_10de_55f_0 (failed)
  prop read: +6Nb.Q2YEkqhxk71 (failed)
  old prop read: +6Nb.Q2YEkqhxk71 (failed)
  prop read: /org/freedesktop/Hal/devices/pci_10de_560 (failed)
  prop read: H0_h.tnXewr65wmE (failed)
  old prop read: H0_h.tnXewr65wmE (failed)
  prop read: /org/freedesktop/Hal/devices/pci_10de_55c (failed)
  prop read: M71A.k5JPLyF5+X5 (failed)
  old prop read: M71A.k5JPLyF5+X5 (failed)
  prop read: /org/freedesktop/Hal/devices/pci_10de_561 (failed)
  prop read: RE4e.YJkdpAs+Bd6 (failed)
  old prop read: RE4e.YJkdpAs+Bd6 (failed)
  prop read: /org/freedesktop/Hal/devices/pci_10de_550 (failed)
  prop read: WL76.32+uULFatWA (failed)
  old prop read: WL76.32+uULFatWA (failed)
  prop read: /org/freedesktop/Hal/devices/pci_10de_54c (failed)
  prop read: rBUF.Qh8YuQ9wg77 (failed)
  old prop read: rBUF.Qh8YuQ9wg77 (failed)
  prop read: /org/freedesktop/Hal/devices/pci_10de_563 (failed)
  prop read: lgGW.SBYAWohmo3A (failed)
  old prop read: lgGW.SBYAWohmo3A (failed)
  prop read: /org/freedesktop/Hal/devices/pci_10de_563_0 (failed)
  prop read: qnJ_.SBYAWohmo3A (failed)
  old prop read: qnJ_.SBYAWohmo3A (failed)
  prop read: /org/freedesktop/Hal/devices/pci_10de_531 (failed)
  prop read: CLZK.W_CERNWvuOA (failed)
  old prop read: CLZK.W_CERNWvuOA (failed)
  prop read: /org/freedesktop/Hal/devices/pci_1022_1100 (failed)
  prop read: fiDB.ptk_g9XAN03 (failed)
  old prop read: fiDB.ptk_g9XAN03 (failed)
  prop read: /org/freedesktop/Hal/devices/pci_1022_1101 (failed)
  prop read: W1j0.KIhk9ketuO3 (failed)
  old prop read: W1j0.KIhk9ketuO3 (failed)
  prop read: /org/freedesktop/Hal/devices/pci_1022_1102 (failed)
  prop read: OMCs.ridUeImaQn3 (failed)
  old prop read: OMCs.ridUeImaQn3 (failed)
  prop read: /org/freedesktop/Hal/devices/pci_1022_1103 (failed)
  prop read: Fhhh.M7aE7ttHy94 (failed)
  old prop read: Fhhh.M7aE7ttHy94 (failed)
  prop read: /org/freedesktop/Hal/devices/pci_1180_832 (failed)
  prop read: ZcKW.31mjw4gc_i5 (failed)
  old prop read: ZcKW.31mjw4gc_i5 (failed)
  prop read: /org/freedesktop/Hal/devices/pci_1180_822 (failed)
  prop read: RxpL.1Jezk9TGFRF (failed)
  old prop read: RxpL.1Jezk9TGFRF (failed)
  prop read: /org/freedesktop/Hal/devices/pci_1180_592 (failed)
  prop read: IGJB.1P05GMbfz2D (failed)
  old prop read: IGJB.1P05GMbfz2D (failed)
  prop read: /org/freedesktop/Hal/devices/pci_1180_852 (failed)
  prop read: Abo0.y1DwemReLyA (failed)
  old prop read: Abo0.y1DwemReLyA (failed)
  prop read: /org/freedesktop/Hal/devices/pci_168c_1c (failed)
  prop read: y9sn.9AnOduZyIOF (failed)
  old prop read: y9sn.9AnOduZyIOF (failed)
  prop read: /org/freedesktop/Hal/devices/pnp_PNP0a08 (failed)
  prop read: z9pp.+GmdJItMGB9 (failed)
  old prop read: z9pp.+GmdJItMGB9 (failed)
  prop read: /org/freedesktop/Hal/devices/pnp_PNP0103 (failed)
  prop read: QL3u.fG36JLVNse9 (failed)
  old prop read: QL3u.fG36JLVNse9 (failed)
  prop read: /org/freedesktop/Hal/devices/pnp_PNP0c02 (failed)
  prop read: tWJy.B+yZ9Ve8gC1 (failed)
  old prop read: tWJy.B+yZ9Ve8gC1 (failed)
  prop read: /org/freedesktop/Hal/devices/pnp_PNP0c02_0 (failed)
  prop read: KiZ0.B+yZ9Ve8gC1 (failed)
  old prop read: KiZ0.B+yZ9Ve8gC1 (failed)
  prop read: /org/freedesktop/Hal/devices/pnp_PNP0c02_1 (failed)
  prop read: ntp4.B+yZ9Ve8gC1 (failed)
  old prop read: ntp4.B+yZ9Ve8gC1 (failed)
  prop read: /org/freedesktop/Hal/devices/pnp_PNP0200 (failed)
  prop read: E349.ld94kxNGZf5 (failed)
  old prop read: E349.ld94kxNGZf5 (failed)
  prop read: /org/freedesktop/Hal/devices/pnp_PNP0800 (failed)
  prop read: hEKD.bvKf3UMzZfE (failed)
  old prop read: hEKD.bvKf3UMzZfE (failed)
  prop read: /org/freedesktop/Hal/devices/pnp_PNP0b00 (failed)
  prop read: NhVi.WYwRElrJa93 (failed)
  old prop read: NhVi.WYwRElrJa93 (failed)
  prop read: /org/freedesktop/Hal/devices/pnp_PNP0c04 (failed)
  prop read: qslm.DE8RM9cWQQ8 (failed)
  old prop read: qslm.DE8RM9cWQQ8 (failed)
  prop read: /org/freedesktop/Hal/devices/pnp_PNP0303 (failed)
  prop read: H20r.xhndlW9HXJ7 (failed)
  old prop read: H20r.xhndlW9HXJ7 (failed)
  prop read: /org/freedesktop/Hal/devices/pnp_SYN013b (failed)
  prop read: iT2w.zeph4bkcMgD (failed)
  old prop read: iT2w.zeph4bkcMgD (failed)
  prop read: /org/freedesktop/Hal/devices/pnp_PNP0c01 (failed)
  prop read: 9fI_.gNN83gfynbD (failed)
  old prop read: 9fI_.gNN83gfynbD (failed)
  prop read: /org/freedesktop/Hal/devices/storage_serial_TSSTcorp_CDDVDW_TS_L632N (failed)
  prop read: KD9E.efi45GMc8N7 (failed)
  old prop read: KD9E.efi45GMc8N7 (failed)
  prop read: /org/freedesktop/Hal/devices/storage_serial_SAMSUNG_HM160HI_S18PJDNQ506588 (failed)
  prop read: 3OOL.YUsbScIQ6L5 (failed)
  old prop read: 3OOL.YUsbScIQ6L5 (failed)
  prop read: /org/freedesktop/Hal/devices/volume_uuid_84e2594c_9753_4f69_8a20_584d6e60a569 (failed)
  prop read: bdUI.SE1wIdpsiiC (failed)
  old prop read: bdUI.SE1wIdpsiiC (failed)
  prop read: /org/freedesktop/Hal/devices/volume_part2_size_1024 (failed)
  prop read: 2pkM.SE1wIdpsiiC (failed)
  old prop read: 2pkM.SE1wIdpsiiC (failed)
  prop read: /org/freedesktop/Hal/devices/volume_uuid_564b5473_3a78_4af3_8bb8_6e96f3420944 (failed)
  prop read: QLVZ.SE1wIdpsiiC (failed)
  old prop read: QLVZ.SE1wIdpsiiC (failed)
  prop read: /org/freedesktop/Hal/devices/usb_device_1d6b_2_0000_00_02_1_if0 (failed)
  prop read: k4bc.OqydEZZ981A (failed)
  old prop read: k4bc.OqydEZZ981A (failed)
  prop read: /org/freedesktop/Hal/devices/usb_device_1d6b_2_0000_00_04_1_if0 (failed)
  prop read: pBe4.QtYiGM_hXFF (failed)
  old prop read: pBe4.QtYiGM_hXFF (failed)
  prop read: /org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_02_0_if0 (failed)
  prop read: uIhY.kllrQr_lFX9 (failed)
  old prop read: uIhY.kllrQr_lFX9 (failed)
  prop read: /org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_04_0_if0 (failed)
  prop read: zPk0.moLwSePIflE (failed)
  old prop read: zPk0.moLwSePIflE (failed)
  prop read: /org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port_logicaldev_input (failed)
  prop read: c3zD.+49ps10DtUF (failed)
  old prop read: c3zD.+49ps10DtUF (failed)
  prop read: /org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port_logicaldev_input (failed)
  prop read: AH6Q.ZHI3OT7LsxA (failed)
  old prop read: AH6Q.ZHI3OT7LsxA (failed)
  prop read: rdCR.j8NaKXDZtZ6 (failed)
  old prop read: rdCR.j8NaKXDZtZ6 (failed)
  prop read: wkFv.j8NaKXDZtZ6 (failed)
  old prop read: wkFv.j8NaKXDZtZ6 (failed)
  prop read: ZsBS.GQNx7L4uPNA (failed)
  old prop read: ZsBS.GQNx7L4uPNA (failed)
  prop read: usDW.ndpeucax6V1 (failed)
  old prop read: usDW.ndpeucax6V1 (failed)
  prop read: AYEt.QXn1l67RSa1 (failed)
  old prop read: AYEt.QXn1l67RSa1 (failed)
----- /proc/modules -----
  lp 13349 0 - Live 0x00000000
  parport_pc 32111 0 - Live 0x00000000
  st 40038 0 - Live 0x00000000
  mmc_block 17704 0 - Live 0x00000000
  nls_iso8859_1 12617 0 - Live 0x00000000
  nls_cp437 12751 0 - Live 0x00000000
  vfat 17335 0 - Live 0x00000000
  fat 55505 1 vfat, Live 0x00000000
  usb_storage 43946 0 - Live 0x00000000
  uas 17676 0 - Live 0x00000000
  cryptd 19801 0 - Live 0x00000000
  aes_i586 16956 1 - Live 0x00000000
  aes_generic 38023 1 aes_i586, Live 0x00000000
  binfmt_misc 13213 1 - Live 0x00000000
  ppdev 12849 0 - Live 0x00000000
  vesafb 13449 1 - Live 0x00000000
  nvidia 7098106 40 - Live 0x00000000 (P)
  arc4 12473 2 - Live 0x00000000
  snd_hda_codec_conexant 43782 1 - Live 0x00000000
  snd_hda_intel 24140 2 - Live 0x00000000
  ath5k 144412 0 - Live 0x00000000
  snd_hda_codec 90901 2 snd_hda_codec_conexant,snd_hda_intel, Live 0x00000000
  r852 17878 0 - Live 0x00000000
  sm_common 16737 1 r852, Live 0x00000000
  snd_hwdep 13274 1 snd_hda_codec, Live 0x00000000
  snd_pcm 80244 2 snd_hda_intel,snd_hda_codec, Live 0x00000000
  snd_seq_midi 13132 0 - Live 0x00000000
  nand 49822 2 r852,sm_common, Live 0x00000000
  ath 19141 1 ath5k, Live 0x00000000
  snd_rawmidi 25269 1 snd_seq_midi, Live 0x00000000
  nand_ids 8547 1 nand, Live 0x00000000
  snd_seq_midi_event 14475 1 snd_seq_midi, Live 0x00000000
  nand_ecc 13070 1 nand, Live 0x00000000
  joydev 17322 0 - Live 0x00000000
  mac80211 257001 1 ath5k, Live 0x00000000
  snd_seq 51291 2 snd_seq_midi,snd_seq_midi_event, Live 0x00000000
  snd_timer 28659 2 snd_pcm,snd_seq, Live 0x00000000
  snd_seq_device 14110 3 snd_seq_midi,snd_rawmidi,snd_seq, Live 0x00000000
  snd 55295 13 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device, Live 0x00000000
  mtd 26530 2 sm_common,nand, Live 0x00000000
  cfg80211 156212 3 ath5k,ath,mac80211, Live 0x00000000
  soundcore 12600 1 snd, Live 0x00000000
  snd_page_alloc 14073 2 snd_hda_intel,snd_pcm, Live 0x00000000
  psmouse 59039 0 - Live 0x00000000
  i2c_nforce2 12906 0 - Live 0x00000000
  video 18951 0 - Live 0x00000000
  parport 36746 3 lp,parport_pc,ppdev, Live 0x00000000
  k8temp 12872 0 - Live 0x00000000
  hp_wmi 13418 0 - Live 0x00000000
  serio_raw 12990 0 - Live 0x00000000
  sparse_keymap 13666 1 hp_wmi, Live 0x00000000
  ahci 21591 2 - Live 0x00000000
  firewire_ohci 31504 0 - Live 0x00000000
  sdhci_pci 13623 0 - Live 0x00000000
  sdhci 22720 1 sdhci_pci, Live 0x00000000
  firewire_core 56138 1 firewire_ohci, Live 0x00000000
  pata_amd 13762 0 - Live 0x00000000
  libahci 25548 1 ahci, Live 0x00000000
  forcedeth 58190 0 - Live 0x00000000
  crc_itu_t 12627 1 firewire_core, Live 0x00000000
----- /proc/modules end -----
  used irqs: 0,1,5,7,8,9,10,11,12,14,15,16,18,19,21,22,23,40,41,42
=========== end debug info ============
01: None 00.0: 10105 BIOS
  [Created at bios.190]
  Unique ID: rdCR.lZF+r4EgHp4
  Hardware Class: bios
  BIOS Keyboard LED Status:
    Scroll Lock: off
    Num Lock: off
    Caps Lock: off
  Config Status: cfg=new, avail=yes, need=no, active=unknown

02: None 00.0: 10107 System
  [Created at sys.63]
  Unique ID: rdCR.n_7QNeEnh23
  Hardware Class: system
  Model: "System"
  Formfactor: "laptop"
  Driver Info #0:
    Driver Status: thermal,fan are not active
    Driver Activation Cmd: "modprobe thermal; modprobe fan"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

03: None 00.0: 10104 FPU
  [Created at misc.192]
  Unique ID: rdCR.EMpH5pjcahD
  Hardware Class: unknown
  Model: "FPU"
  I/O Ports: 0xf0-0xff (rw)
  Config Status: cfg=new, avail=yes, need=no, active=unknown

04: None 00.0: 0801 DMA controller (8237)
  [Created at misc.206]
  Unique ID: rdCR.f5u1ucRm+H9
  Hardware Class: unknown
  Model: "DMA controller"
  I/O Ports: 0x00-0xcf7 (rw)
  I/O Ports: 0xc0-0xdf (rw)
  I/O Ports: 0x80-0x8f (rw)
  DMA: 4
  Config Status: cfg=new, avail=yes, need=no, active=unknown

05: None 00.0: 0800 PIC (8259)
  [Created at misc.219]
  Unique ID: rdCR.8uRK7LxiIA2
  Hardware Class: unknown
  Model: "PIC"
  I/O Ports: 0x20-0x21 (rw)
  I/O Ports: 0xa0-0xa1 (rw)
  Config Status: cfg=new, avail=yes, need=no, active=unknown

06: None 00.0: 0802 Timer (8254)
  [Created at misc.230]
  Unique ID: rdCR.AJKleuxpiP0
  Hardware Class: unknown
  Model: "Timer"
  IRQ: 0 (6591703 events)
  Config Status: cfg=new, avail=yes, need=no, active=unknown

07: None 00.0: 0900 Keyboard controller
  [Created at misc.251]
  Unique ID: rdCR.9N+EecqykME
  Hardware Class: unknown
  Model: "Keyboard controller"
  I/O Port: 0x60 (rw)
  I/O Port: 0x64 (rw)
  Config Status: cfg=new, avail=yes, need=no, active=unknown

10: None 00.0: 10102 Main Memory
  [Created at memory.61]
  Unique ID: rdCR.CxwsZFjVASF
  Hardware Class: memory
  Model: "Main Memory"
  Memory Range: 0x00000000-0xeb7f3fff (rw)
  Memory Size: 3 GB + 768 MB
  Config Status: cfg=new, avail=yes, need=no, active=unknown

11: PCI 00.0: 0500 RAM memory
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_10de_547
  Unique ID: qLht.u35Y1PF8No9
  SysFS ID: /devices/pci0000:00/0000:00:00.0
  SysFS BusID: 0000:00:00.0
  Hardware Class: unknown
  Model: "nVidia MCP67 Memory Controller"
  Vendor: pci 0x10de "nVidia Corporation"
  Device: pci 0x0547 "MCP67 Memory Controller"
  SubVendor: pci 0x103c "Hewlett-Packard Company"
  SubDevice: pci 0x30cf 
  Revision: 0xa2
  Module Alias: "pci:v000010DEd00000547sv0000103Csd000030CFbc05sc00i00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

12: PCI 01.0: 0601 ISA bridge
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_10de_548
  Unique ID: vSkL.xA1wnWm82VD
  SysFS ID: /devices/pci0000:00/0000:00:01.0
  SysFS BusID: 0000:00:01.0
  Hardware Class: bridge
  Model: "nVidia MCP67 ISA Bridge"
  Vendor: pci 0x10de "nVidia Corporation"
  Device: pci 0x0548 "MCP67 ISA Bridge"
  SubVendor: pci 0x103c "Hewlett-Packard Company"
  SubDevice: pci 0x30cf 
  Revision: 0xa2
  Module Alias: "pci:v000010DEd00000548sv0000103Csd000030CFbc06sc01i00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

13: PCI 01.1: 0c05 SMBus
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_10de_542
  Unique ID: mnDB.+RSl1sRdLr0
  SysFS ID: /devices/pci0000:00/0000:00:01.1
  SysFS BusID: 0000:00:01.1
  Hardware Class: unknown
  Model: "nVidia MCP67 SMBus"
  Vendor: pci 0x10de "nVidia Corporation"
  Device: pci 0x0542 "MCP67 SMBus"
  SubVendor: pci 0x103c "Hewlett-Packard Company"
  SubDevice: pci 0x30cf 
  Revision: 0xa2
  Driver: "nForce2_smbus"
  Driver Modules: "i2c_nforce2"
  I/O Ports: 0x3080-0x30bf (rw)
  I/O Ports: 0x3040-0x307f (rw)
  I/O Ports: 0x3000-0x303f (rw)
  IRQ: 10 (no events)
  Module Alias: "pci:v000010DEd00000542sv0000103Csd000030CFbc0Csc05i00"
  Driver Info #0:
    Driver Status: i2c_nforce2 is active
    Driver Activation Cmd: "modprobe i2c_nforce2"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

14: PCI 01.2: 0500 RAM memory
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_10de_541
  Unique ID: e6j0.oaQ29_XvCV7
  SysFS ID: /devices/pci0000:00/0000:00:01.2
  SysFS BusID: 0000:00:01.2
  Hardware Class: unknown
  Model: "nVidia MCP67 Memory Controller"
  Vendor: pci 0x10de "nVidia Corporation"
  Device: pci 0x0541 "MCP67 Memory Controller"
  SubVendor: pci 0x103c "Hewlett-Packard Company"
  SubDevice: pci 0x30cf 
  Revision: 0xa2
  Module Alias: "pci:v000010DEd00000541sv0000103Csd000030CFbc05sc00i00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

15: PCI 01.3: 0b40 Co-processor
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_10de_543
  Unique ID: VRCs.wqrTvOknH2C
  SysFS ID: /devices/pci0000:00/0000:00:01.3
  SysFS BusID: 0000:00:01.3
  Hardware Class: unknown
  Model: "nVidia MCP67 Co-processor"
  Vendor: pci 0x10de "nVidia Corporation"
  Device: pci 0x0543 "MCP67 Co-processor"
  SubVendor: pci 0x103c "Hewlett-Packard Company"
  SubDevice: pci 0x30cf 
  Revision: 0xa2
  Memory Range: 0xf6200000-0xf627ffff (rw,non-prefetchable)
  IRQ: 11 (no events)
  Module Alias: "pci:v000010DEd00000543sv0000103Csd000030CFbc0Bsc40i00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

16: PCI 02.0: 0c03 USB Controller (OHCI)
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_10de_55e
  Unique ID: _Znp.fdoO6mi4bbA
  SysFS ID: /devices/pci0000:00/0000:00:02.0
  SysFS BusID: 0000:00:02.0
  Hardware Class: usb controller
  Model: "nVidia MCP67 OHCI USB 1.1 Controller"
  Vendor: pci 0x10de "nVidia Corporation"
  Device: pci 0x055e "MCP67 OHCI USB 1.1 Controller"
  SubVendor: pci 0x103c "Hewlett-Packard Company"
  SubDevice: pci 0x30cf 
  Revision: 0xa2
  Driver: "ohci_hcd"
  Memory Range: 0xf6486000-0xf6486fff (rw,non-prefetchable)
  IRQ: 18 (8 events)
  Module Alias: "pci:v000010DEd0000055Esv0000103Csd000030CFbc0Csc03i10"
  Driver Info #0:
    Driver Status: ohci-hcd is not active
    Driver Activation Cmd: "modprobe ohci-hcd"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

17: PCI 02.1: 0c03 USB Controller (EHCI)
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_10de_55f
  Unique ID: ruGf.Q2YEkqhxk71
  SysFS ID: /devices/pci0000:00/0000:00:02.1
  SysFS BusID: 0000:00:02.1
  Hardware Class: usb controller
  Model: "nVidia MCP67 EHCI USB 2.0 Controller"
  Vendor: pci 0x10de "nVidia Corporation"
  Device: pci 0x055f "MCP67 EHCI USB 2.0 Controller"
  SubVendor: pci 0x103c "Hewlett-Packard Company"
  SubDevice: pci 0x30cf 
  Revision: 0xa2
  Driver: "ehci_hcd"
  Driver Modules: "ehci_hcd"
  Memory Range: 0xf6489000-0xf64890ff (rw,non-prefetchable)
  IRQ: 22 (15529 events)
  Module Alias: "pci:v000010DEd0000055Fsv0000103Csd000030CFbc0Csc03i20"
  Driver Info #0:
    Driver Status: ehci-hcd is not active
    Driver Activation Cmd: "modprobe ehci-hcd"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

18: PCI 04.0: 0c03 USB Controller (OHCI)
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_10de_55e_0
  Unique ID: 8otl.fdoO6mi4bbA
  SysFS ID: /devices/pci0000:00/0000:00:04.0
  SysFS BusID: 0000:00:04.0
  Hardware Class: usb controller
  Model: "nVidia MCP67 OHCI USB 1.1 Controller"
  Vendor: pci 0x10de "nVidia Corporation"
  Device: pci 0x055e "MCP67 OHCI USB 1.1 Controller"
  SubVendor: pci 0x103c "Hewlett-Packard Company"
  SubDevice: pci 0x30cf 
  Revision: 0xa2
  Driver: "ohci_hcd"
  Memory Range: 0xf6487000-0xf6487fff (rw,non-prefetchable)
  IRQ: 18 (8 events)
  Module Alias: "pci:v000010DEd0000055Esv0000103Csd000030CFbc0Csc03i10"
  Driver Info #0:
    Driver Status: ohci-hcd is not active
    Driver Activation Cmd: "modprobe ohci-hcd"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

19: PCI 04.1: 0c03 USB Controller (EHCI)
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_10de_55f_0
  Unique ID: +6Nb.Q2YEkqhxk71
  SysFS ID: /devices/pci0000:00/0000:00:04.1
  SysFS BusID: 0000:00:04.1
  Hardware Class: usb controller
  Model: "nVidia MCP67 EHCI USB 2.0 Controller"
  Vendor: pci 0x10de "nVidia Corporation"
  Device: pci 0x055f "MCP67 EHCI USB 2.0 Controller"
  SubVendor: pci 0x103c "Hewlett-Packard Company"
  SubDevice: pci 0x30cf 
  Revision: 0xa2
  Driver: "ehci_hcd"
  Driver Modules: "ehci_hcd"
  Memory Range: 0xf6489400-0xf64894ff (rw,non-prefetchable)
  IRQ: 22 (15529 events)
  Module Alias: "pci:v000010DEd0000055Fsv0000103Csd000030CFbc0Csc03i20"
  Driver Info #0:
    Driver Status: ehci-hcd is not active
    Driver Activation Cmd: "modprobe ehci-hcd"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

20: PCI 06.0: 0101 IDE interface
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_10de_560
  Unique ID: H0_h.tnXewr65wmE
  SysFS ID: /devices/pci0000:00/0000:00:06.0
  SysFS BusID: 0000:00:06.0
  Hardware Class: storage
  Model: "nVidia MCP67 IDE Controller"
  Vendor: pci 0x10de "nVidia Corporation"
  Device: pci 0x0560 "MCP67 IDE Controller"
  SubVendor: pci 0x103c "Hewlett-Packard Company"
  SubDevice: pci 0x30cf 
  Revision: 0xa1
  Driver: "pata_amd"
  Driver Modules: "pata_amd"
  I/O Ports: 0x1f0-0x1f7 (rw)
  I/O Port: 0x3f6 (rw)
  I/O Ports: 0x170-0x177 (rw)
  I/O Port: 0x376 (rw)
  I/O Ports: 0x30c0-0x30cf (rw)
  Module Alias: "pci:v000010DEd00000560sv0000103Csd000030CFbc01sc01i8a"
  Driver Info #0:
    Driver Status: pata_amd is active
    Driver Activation Cmd: "modprobe pata_amd"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

21: PCI 07.0: 0403 Audio device
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_10de_55c
  Unique ID: M71A.k5JPLyF5+X5
  SysFS ID: /devices/pci0000:00/0000:00:07.0
  SysFS BusID: 0000:00:07.0
  Hardware Class: sound
  Model: "nVidia MCP67 High Definition Audio"
  Vendor: pci 0x10de "nVidia Corporation"
  Device: pci 0x055c "MCP67 High Definition Audio"
  SubVendor: pci 0x103c "Hewlett-Packard Company"
  SubDevice: pci 0x30cf 
  Revision: 0xa1
  Driver: "HDA Intel"
  Driver Modules: "snd_hda_intel"
  Memory Range: 0xf6480000-0xf6483fff (rw,non-prefetchable)
  IRQ: 21 (1164 events)
  Module Alias: "pci:v000010DEd0000055Csv0000103Csd000030CFbc04sc03i00"
  Driver Info #0:
    Driver Status: snd_hda_intel is active
    Driver Activation Cmd: "modprobe snd_hda_intel"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

22: PCI 08.0: 0604 PCI bridge (Subtractive decode)
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_10de_561
  Unique ID: RE4e.YJkdpAs+Bd6
  SysFS ID: /devices/pci0000:00/0000:00:08.0
  SysFS BusID: 0000:00:08.0
  Hardware Class: bridge
  Model: "nVidia MCP67 PCI Bridge"
  Vendor: pci 0x10de "nVidia Corporation"
  Device: pci 0x0561 "MCP67 PCI Bridge"
  SubVendor: pci 0x10de "nVidia Corporation"
  SubDevice: pci 0xcb84 
  Revision: 0xa2
  Module Alias: "pci:v000010DEd00000561sv000010DEsd0000CB84bc06sc04i01"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

23: PCI 09.0: 0101 IDE interface
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_10de_550
  Unique ID: WL76.32+uULFatWA
  SysFS ID: /devices/pci0000:00/0000:00:09.0
  SysFS BusID: 0000:00:09.0
  Hardware Class: storage
  Model: "nVidia MCP67 AHCI Controller"
  Vendor: pci 0x10de "nVidia Corporation"
  Device: pci 0x0550 "MCP67 AHCI Controller"
  SubVendor: pci 0x103c "Hewlett-Packard Company"
  SubDevice: pci 0x30cf 
  Revision: 0xa2
  Driver: "ahci"
  Driver Modules: "ahci"
  I/O Ports: 0x30f0-0x30f7 (rw)
  I/O Ports: 0x30e4-0x30e7 (rw)
  I/O Ports: 0x30e8-0x30ef (rw)
  I/O Ports: 0x30e0-0x30e3 (rw)
  I/O Ports: 0x30d0-0x30df (rw)
  Memory Range: 0xf6484000-0xf6485fff (rw,non-prefetchable)
  IRQ: 23 (148578 events)
  Module Alias: "pci:v000010DEd00000550sv0000103Csd000030CFbc01sc01i85"
  Driver Info #0:
    Driver Status: ahci is active
    Driver Activation Cmd: "modprobe ahci"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

24: PCI 0a.0: 0200 Ethernet controller
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_10de_54c
  Unique ID: rBUF.Qh8YuQ9wg77
  SysFS ID: /devices/pci0000:00/0000:00:0a.0
  SysFS BusID: 0000:00:0a.0
  Hardware Class: network
  Model: "nVidia MCP67 Ethernet"
  Vendor: pci 0x10de "nVidia Corporation"
  Device: pci 0x054c "MCP67 Ethernet"
  SubVendor: pci 0x103c "Hewlett-Packard Company"
  SubDevice: pci 0x30cf 
  Revision: 0xa2
  Driver: "forcedeth"
  Driver Modules: "forcedeth"
  Device File: eth0
  Memory Range: 0xf6488000-0xf6488fff (rw,non-prefetchable)
  I/O Ports: 0x30f8-0x30ff (rw)
  Memory Range: 0xf6489c00-0xf6489cff (rw,non-prefetchable)
  Memory Range: 0xf6489800-0xf648980f (rw,non-prefetchable)
  IRQ: 42 (no events)
  HW Address: 00:1e:68:7f:2c:8b
  Link detected: no
  Module Alias: "pci:v000010DEd0000054Csv0000103Csd000030CFbc02sc00i00"
  Driver Info #0:
    Driver Status: forcedeth is active
    Driver Activation Cmd: "modprobe forcedeth"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

25: PCI 0c.0: 0604 PCI bridge (Normal decode)
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_10de_563
  Unique ID: lgGW.SBYAWohmo3A
  SysFS ID: /devices/pci0000:00/0000:00:0c.0
  SysFS BusID: 0000:00:0c.0
  Hardware Class: bridge
  Model: "nVidia MCP67 PCI Express Bridge"
  Vendor: pci 0x10de "nVidia Corporation"
  Device: pci 0x0563 "MCP67 PCI Express Bridge"
  SubVendor: pci 0x10de "nVidia Corporation"
  SubDevice: pci 0x0000 
  Revision: 0xa2
  Driver: "pcieport"
  IRQ: 40 (no events)
  Module Alias: "pci:v000010DEd00000563sv000010DEsd00000000bc06sc04i00"
  Driver Info #0:
    Driver Status: shpchp is not active
    Driver Activation Cmd: "modprobe shpchp"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

26: PCI 0d.0: 0604 PCI bridge (Normal decode)
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_10de_563_0
  Unique ID: qnJ_.SBYAWohmo3A
  SysFS ID: /devices/pci0000:00/0000:00:0d.0
  SysFS BusID: 0000:00:0d.0
  Hardware Class: bridge
  Model: "nVidia MCP67 PCI Express Bridge"
  Vendor: pci 0x10de "nVidia Corporation"
  Device: pci 0x0563 "MCP67 PCI Express Bridge"
  SubVendor: pci 0x10de "nVidia Corporation"
  SubDevice: pci 0x0000 
  Revision: 0xa2
  Driver: "pcieport"
  IRQ: 41 (no events)
  Module Alias: "pci:v000010DEd00000563sv000010DEsd00000000bc06sc04i00"
  Driver Info #0:
    Driver Status: shpchp is not active
    Driver Activation Cmd: "modprobe shpchp"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

27: PCI 12.0: 0300 VGA compatible controller (VGA)
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_10de_531
  Unique ID: CLZK.W_CERNWvuOA
  SysFS ID: /devices/pci0000:00/0000:00:12.0
  SysFS BusID: 0000:00:12.0
  Hardware Class: graphics card
  Model: "nVidia GeForce 7150M"
  Vendor: pci 0x10de "nVidia Corporation"
  Device: pci 0x0531 "GeForce 7150M"
  SubVendor: pci 0x103c "Hewlett-Packard Company"
  SubDevice: pci 0x30cf 
  Revision: 0xa2
  Driver: "nvidia"
  Driver Modules: "nvidia"
  Memory Range: 0xf5000000-0xf5ffffff (rw,non-prefetchable)
  Memory Range: 0xd0000000-0xdfffffff (ro,non-prefetchable)
  Memory Range: 0xf4000000-0xf4ffffff (rw,non-prefetchable)
  Memory Range: 0xf6280000-0xf629ffff (ro,non-prefetchable,disabled)
  IRQ: 16 (1042499 events)
  I/O Ports: 0x3c0-0x3df (rw)
  Module Alias: "pci:v000010DEd00000531sv0000103Csd000030CFbc03sc00i00"
  Driver Info #0:
    Driver Status: nvidiafb is not active
    Driver Activation Cmd: "modprobe nvidiafb"
  Driver Info #1:
    Driver Status: nouveau is not active
    Driver Activation Cmd: "modprobe nouveau"
  Driver Info #2:
    Driver Status: nvidia_current is not active
    Driver Activation Cmd: "modprobe nvidia_current"
  Driver Info #3:
    Driver Status: nvidia_173 is not active
    Driver Activation Cmd: "modprobe nvidia_173"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

28: PCI 18.0: 0600 Host bridge
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_1022_1100
  Unique ID: fiDB.ptk_g9XAN03
  SysFS ID: /devices/pci0000:00/0000:00:18.0
  SysFS BusID: 0000:00:18.0
  Hardware Class: bridge
  Model: "AMD K8 [Athlon64/Opteron] HyperTransport Technology Configuration"
  Vendor: pci 0x1022 "AMD"
  Device: pci 0x1100 "K8 [Athlon64/Opteron] HyperTransport Technology Configuration"
  Module Alias: "pci:v00001022d00001100sv00000000sd00000000bc06sc00i00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

29: PCI 18.1: 0600 Host bridge
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_1022_1101
  Unique ID: W1j0.KIhk9ketuO3
  SysFS ID: /devices/pci0000:00/0000:00:18.1
  SysFS BusID: 0000:00:18.1
  Hardware Class: bridge
  Model: "AMD K8 [Athlon64/Opteron] Address Map"
  Vendor: pci 0x1022 "AMD"
  Device: pci 0x1101 "K8 [Athlon64/Opteron] Address Map"
  Module Alias: "pci:v00001022d00001101sv00000000sd00000000bc06sc00i00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

30: PCI 18.2: 0600 Host bridge
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_1022_1102
  Unique ID: OMCs.ridUeImaQn3
  SysFS ID: /devices/pci0000:00/0000:00:18.2
  SysFS BusID: 0000:00:18.2
  Hardware Class: bridge
  Model: "AMD K8 [Athlon64/Opteron] DRAM Controller"
  Vendor: pci 0x1022 "AMD"
  Device: pci 0x1102 "K8 [Athlon64/Opteron] DRAM Controller"
  Module Alias: "pci:v00001022d00001102sv00000000sd00000000bc06sc00i00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

31: PCI 18.3: 0600 Host bridge
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_1022_1103
  Unique ID: Fhhh.M7aE7ttHy94
  SysFS ID: /devices/pci0000:00/0000:00:18.3
  SysFS BusID: 0000:00:18.3
  Hardware Class: bridge
  Model: "AMD K8 [Athlon64/Opteron] Miscellaneous Control"
  Vendor: pci 0x1022 "AMD"
  Device: pci 0x1103 "K8 [Athlon64/Opteron] Miscellaneous Control"
  Driver: "k8temp"
  Driver Modules: "k8temp"
  Module Alias: "pci:v00001022d00001103sv00000000sd00000000bc06sc00i00"
  Driver Info #0:
    Driver Status: k8temp is active
    Driver Activation Cmd: "modprobe k8temp"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

32: PCI 205.0: 0c00 FireWire (IEEE 1394) (OHCI)
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_1180_832
  Unique ID: ZcKW.31mjw4gc_i5
  Parent ID: RE4e.YJkdpAs+Bd6
  SysFS ID: /devices/pci0000:00/0000:00:08.0/0000:02:05.0
  SysFS BusID: 0000:02:05.0
  Hardware Class: firewire controller
  Model: "Ricoh R5C832 IEEE 1394 Controller"
  Vendor: pci 0x1180 "Ricoh Co Ltd"
  Device: pci 0x0832 "R5C832 IEEE 1394 Controller"
  SubVendor: pci 0x103c "Hewlett-Packard Company"
  SubDevice: pci 0x30cf 
  Revision: 0x05
  Driver: "firewire_ohci"
  Driver Modules: "firewire_ohci"
  Memory Range: 0xf6100000-0xf61007ff (rw,non-prefetchable)
  IRQ: 5 (255 events)
  Module Alias: "pci:v00001180d00000832sv0000103Csd000030CFbc0Csc00i10"
  Driver Info #0:
    Driver Status: ohci1394 is not active
    Driver Activation Cmd: "modprobe ohci1394"
  Driver Info #1:
    Driver Status: firewire_ohci is active
    Driver Activation Cmd: "modprobe firewire_ohci"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #22 (PCI bridge)

33: PCI 205.1: 0805 SD Host controller
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_1180_822
  Unique ID: RxpL.1Jezk9TGFRF
  Parent ID: RE4e.YJkdpAs+Bd6
  SysFS ID: /devices/pci0000:00/0000:00:08.0/0000:02:05.1
  SysFS BusID: 0000:02:05.1
  Hardware Class: unknown
  Model: "Ricoh R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter"
  Vendor: pci 0x1180 "Ricoh Co Ltd"
  Device: pci 0x0822 "R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter"
  SubVendor: pci 0x103c "Hewlett-Packard Company"
  SubDevice: pci 0x30cf 
  Revision: 0x22
  Driver: "sdhci-pci"
  Driver Modules: "sdhci_pci"
  Memory Range: 0xf6100800-0xf61008ff (rw,non-prefetchable)
  IRQ: 7 (4532 events)
  Module Alias: "pci:v00001180d00000822sv0000103Csd000030CFbc08sc05i00"
  Driver Info #0:
    Driver Status: sdhci_pci is active
    Driver Activation Cmd: "modprobe sdhci_pci"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #22 (PCI bridge)

34: PCI 205.2: 0880 System peripheral
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_1180_592
  Unique ID: IGJB.1P05GMbfz2D
  Parent ID: RE4e.YJkdpAs+Bd6
  SysFS ID: /devices/pci0000:00/0000:00:08.0/0000:02:05.2
  SysFS BusID: 0000:02:05.2
  Hardware Class: unknown
  Model: "Ricoh R5C592 Memory Stick Bus Host Adapter"
  Vendor: pci 0x1180 "Ricoh Co Ltd"
  Device: pci 0x0592 "R5C592 Memory Stick Bus Host Adapter"
  SubVendor: pci 0x103c "Hewlett-Packard Company"
  SubDevice: pci 0x30cf 
  Revision: 0x12
  Memory Range: 0xf6101000-0xf61010ff (rw,non-prefetchable)
  IRQ: 11 (no events)
  Module Alias: "pci:v00001180d00000592sv0000103Csd000030CFbc08sc80i00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #22 (PCI bridge)

35: PCI 205.3: 0880 System peripheral
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_1180_852
  Unique ID: Abo0.y1DwemReLyA
  Parent ID: RE4e.YJkdpAs+Bd6
  SysFS ID: /devices/pci0000:00/0000:00:08.0/0000:02:05.3
  SysFS BusID: 0000:02:05.3
  Hardware Class: unknown
  Model: "Ricoh xD-Picture Card Controller"
  Vendor: pci 0x1180 "Ricoh Co Ltd"
  Device: pci 0x0852 "xD-Picture Card Controller"
  SubVendor: pci 0x103c "Hewlett-Packard Company"
  SubDevice: pci 0x30cf 
  Revision: 0x12
  Driver: "r852"
  Driver Modules: "r852"
  Memory Range: 0xf6101400-0xf61014ff (rw,non-prefetchable)
  IRQ: 7 (4532 events)
  Module Alias: "pci:v00001180d00000852sv0000103Csd000030CFbc08sc80i00"
  Driver Info #0:
    Driver Status: r852 is active
    Driver Activation Cmd: "modprobe r852"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #22 (PCI bridge)

36: PCI 300.0: 0282 WLAN controller
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_168c_1c
  Unique ID: y9sn.9AnOduZyIOF
  Parent ID: qnJ_.SBYAWohmo3A
  SysFS ID: /devices/pci0000:00/0000:00:0d.0/0000:03:00.0
  SysFS BusID: 0000:03:00.0
  Hardware Class: network
  Model: "Atheros AR242x 802.11abg Wireless PCI Express Adapter"
  Vendor: pci 0x168c "Atheros Communications Inc."
  Device: pci 0x001c "AR242x 802.11abg Wireless PCI Express Adapter"
  SubVendor: pci 0x103c "Hewlett-Packard Company"
  SubDevice: pci 0x137b 
  Revision: 0x01
  Driver: "ath5k"
  Driver Modules: "ath5k"
  Device File: wlan0
  Features: WLAN
  Memory Range: 0xf6000000-0xf600ffff (rw,non-prefetchable)
  IRQ: 19 (895136 events)
  HW Address: 00:1f:e2:ca:20:77
  Link detected: yes
  WLAN channels: 1 2 3 4 5 6 7 8 9 10 11 12 13
  WLAN frequencies: 2.412 2.417 2.422 2.427 2.432 2.437 2.442 2.447 2.452 2.457 2.462 2.467 2.472
  WLAN encryption modes: WEP40 WEP104 TKIP CCMP
  WLAN authentication modes: open sharedkey wpa-psk wpa-eap
  Module Alias: "pci:v0000168Cd0000001Csv0000103Csd0000137Bbc02sc00i00"
  Driver Info #0:
    Driver Status: ath5k is active
    Driver Activation Cmd: "modprobe ath5k"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #26 (PCI bridge)

37: ISA(PnP) 00.0: 0000 Unclassified device
  [Created at isapnp.142]
  UDI: /org/freedesktop/Hal/devices/pnp_PNP0a08
  Unique ID: z9pp.+GmdJItMGB9
  SysFS ID: /devices/pnp0/00:00
  SysFS BusID: 00:00
  Hardware Class: unknown
  Model: "Unclassified device"
  SubVendor: PNP "PnP"
  SubDevice: eisa 0x0a08 
  Config Status: cfg=new, avail=yes, need=no, active=unknown

38: ISA(PnP) 00.0: 0000 Unclassified device
  [Created at isapnp.142]
  UDI: /org/freedesktop/Hal/devices/pnp_PNP0103
  Unique ID: QL3u.fG36JLVNse9
  SysFS ID: /devices/pnp0/00:01
  SysFS BusID: 00:01
  Hardware Class: unknown
  Model: "Unclassified device"
  SubVendor: PNP "PnP"
  SubDevice: eisa 0x0103 
  Config Status: cfg=new, avail=yes, need=no, active=unknown

39: ISA(PnP) 00.0: 0000 Unclassified device
  [Created at isapnp.142]
  UDI: /org/freedesktop/Hal/devices/pnp_PNP0c02
  Unique ID: tWJy.B+yZ9Ve8gC1
  SysFS ID: /devices/pnp0/00:02
  SysFS BusID: 00:02
  Hardware Class: unknown
  Model: "Unclassified device"
  SubVendor: PNP "PnP"
  SubDevice: eisa 0x0c02 
  Config Status: cfg=new, avail=yes, need=no, active=unknown

40: ISA(PnP) 00.0: 0000 Unclassified device
  [Created at isapnp.142]
  UDI: /org/freedesktop/Hal/devices/pnp_PNP0c02_0
  Unique ID: KiZ0.B+yZ9Ve8gC1
  SysFS ID: /devices/pnp0/00:03
  SysFS BusID: 00:03
  Hardware Class: unknown
  Model: "Unclassified device"
  SubVendor: PNP "PnP"
  SubDevice: eisa 0x0c02 
  Config Status: cfg=new, avail=yes, need=no, active=unknown

41: ISA(PnP) 00.0: 0000 Unclassified device
  [Created at isapnp.142]
  UDI: /org/freedesktop/Hal/devices/pnp_PNP0c02_1
  Unique ID: ntp4.B+yZ9Ve8gC1
  SysFS ID: /devices/pnp0/00:04
  SysFS BusID: 00:04
  Hardware Class: unknown
  Model: "Unclassified device"
  SubVendor: PNP "PnP"
  SubDevice: eisa 0x0c02 
  Config Status: cfg=new, avail=yes, need=no, active=unknown

42: ISA(PnP) 00.0: 0000 Unclassified device
  [Created at isapnp.142]
  UDI: /org/freedesktop/Hal/devices/pnp_PNP0200
  Unique ID: E349.ld94kxNGZf5
  SysFS ID: /devices/pnp0/00:05
  SysFS BusID: 00:05
  Hardware Class: unknown
  Model: "Unclassified device"
  SubVendor: PNP "PnP"
  SubDevice: eisa 0x0200 
  Config Status: cfg=new, avail=yes, need=no, active=unknown

43: ISA(PnP) 00.0: 0000 Unclassified device
  [Created at isapnp.142]
  UDI: /org/freedesktop/Hal/devices/pnp_PNP0800
  Unique ID: hEKD.bvKf3UMzZfE
  SysFS ID: /devices/pnp0/00:06
  SysFS BusID: 00:06
  Hardware Class: unknown
  Model: "Unclassified device"
  SubVendor: PNP "PnP"
  SubDevice: eisa 0x0800 
  Config Status: cfg=new, avail=yes, need=no, active=unknown

44: ISA(PnP) 00.0: 0000 Unclassified device
  [Created at isapnp.142]
  UDI: /org/freedesktop/Hal/devices/pnp_PNP0b00
  Unique ID: NhVi.WYwRElrJa93
  SysFS ID: /devices/pnp0/00:07
  SysFS BusID: 00:07
  Hardware Class: unknown
  Model: "Unclassified device"
  SubVendor: PNP "PnP"
  SubDevice: eisa 0x0b00 
  Config Status: cfg=new, avail=yes, need=no, active=unknown

45: ISA(PnP) 00.0: 0000 Unclassified device
  [Created at isapnp.142]
  UDI: /org/freedesktop/Hal/devices/pnp_PNP0c04
  Unique ID: qslm.DE8RM9cWQQ8
  SysFS ID: /devices/pnp0/00:08
  SysFS BusID: 00:08
  Hardware Class: unknown
  Model: "Unclassified device"
  SubVendor: PNP "PnP"
  SubDevice: eisa 0x0c04 
  Config Status: cfg=new, avail=yes, need=no, active=unknown

46: ISA(PnP) 00.0: 0000 Unclassified device
  [Created at isapnp.142]
  UDI: /org/freedesktop/Hal/devices/pnp_PNP0303
  Unique ID: H20r.xhndlW9HXJ7
  SysFS ID: /devices/pnp0/00:09
  SysFS BusID: 00:09
  Hardware Class: unknown
  Model: "Unclassified device"
  SubVendor: PNP "PnP"
  SubDevice: eisa 0x0303 
  Config Status: cfg=new, avail=yes, need=no, active=unknown

47: ISA(PnP) 00.0: 0000 Unclassified device
  [Created at isapnp.142]
  UDI: /org/freedesktop/Hal/devices/pnp_SYN013b
  Unique ID: iT2w.zeph4bkcMgD
  SysFS ID: /devices/pnp0/00:0a
  SysFS BusID: 00:0a
  Hardware Class: unknown
  Model: "Unclassified device"
  SubVendor: SYN 
  SubDevice: eisa 0x013b 
  Config Status: cfg=new, avail=yes, need=no, active=unknown

48: ISA(PnP) 00.0: 0000 Unclassified device
  [Created at isapnp.142]
  UDI: /org/freedesktop/Hal/devices/pnp_PNP0c01
  Unique ID: 9fI_.gNN83gfynbD
  SysFS ID: /devices/pnp0/00:0b
  SysFS BusID: 00:0b
  Hardware Class: unknown
  Model: "Unclassified device"
  SubVendor: PNP "PnP"
  SubDevice: eisa 0x0c01 
  Config Status: cfg=new, avail=yes, need=no, active=unknown

49: SCSI 00.0: 10602 CD-ROM (DVD)
  [Created at block.247]
  UDI: /org/freedesktop/Hal/devices/storage_serial_TSSTcorp_CDDVDW_TS_L632N
  Unique ID: KD9E.efi45GMc8N7
  Parent ID: H0_h.tnXewr65wmE
  SysFS ID: /class/block/sr0
  SysFS BusID: 0:0:0:0
  SysFS Device Link: /devices/pci0000:00/0000:00:06.0/host0/target0:0:0/0:0:0:0
  Hardware Class: cdrom
  Model: "TSSTcorp CDDVDW TS-L632N"
  Vendor: "TSSTcorp"
  Device: "CDDVDW TS-L632N"
  Revision: "0503"
  Driver: "pata_amd", "sr"
  Driver Modules: "pata_amd"
  Device File: /dev/sr0 (/dev/sg0)
  Device Files: /dev/sr0, /dev/scd0, /dev/disk/by-id/ata-TSSTcorp_CDDVDW_TS-L632N, /dev/disk/by-path/pci-0000:00:06.0-scsi-0:0:0:0, /dev/cdrom, /dev/cdrw, /dev/dvd, /dev/dvdrw
  Device Number: block 11:0 (char 21:0)
  Features: CD-R, CD-RW, DVD, DVD-R, DVD-RW, DVD+R, DVD+RW, DVD+DL, DVDRAM
  Drive status: no medium
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #20 (IDE interface)
  Drive Speed: 24

50: IDE 200.0: 10600 Disk
  [Created at block.243]
  UDI: /org/freedesktop/Hal/devices/storage_serial_SAMSUNG_HM160HI_S18PJDNQ506588
  Unique ID: 3OOL.YUsbScIQ6L5
  Parent ID: WL76.32+uULFatWA
  SysFS ID: /class/block/sda
  SysFS BusID: 2:0:0:0
  SysFS Device Link: /devices/pci0000:00/0000:00:09.0/host2/target2:0:0/2:0:0:0
  Hardware Class: disk
  Model: "SAMSUNG HM160HI"
  Vendor: "SAMSUNG"
  Device: "HM160HI"
  Revision: "HH10"
  Driver: "ahci", "sd"
  Driver Modules: "ahci"
  Device File: /dev/sda
  Device Files: /dev/sda, /dev/disk/by-id/ata-SAMSUNG_HM160HI_S18PJDNQ506588, /dev/disk/by-id/scsi-SATA_SAMSUNG_HM160HIS18PJDNQ506588, /dev/disk/by-path/pci-0000:00:09.0-scsi-0:0:0:0, /dev/disk/by-id/wwn-0x50f00000e1506588
  Device Number: block 8:0-8:15
  BIOS id: 0x80
  Drive status: no medium
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #23 (IDE interface)

51: None 00.0: 11300 Partition
  [Created at block.412]
  UDI: /org/freedesktop/Hal/devices/volume_uuid_84e2594c_9753_4f69_8a20_584d6e60a569
  Unique ID: bdUI.SE1wIdpsiiC
  Parent ID: 3OOL.YUsbScIQ6L5
  SysFS ID: /class/block/sda/sda1
  Hardware Class: partition
  Model: "Partition"
  Device File: /dev/sda1
  Device Files: /dev/sda1, /dev/disk/by-id/ata-SAMSUNG_HM160HI_S18PJDNQ506588-part1, /dev/disk/by-id/scsi-SATA_SAMSUNG_HM160HIS18PJDNQ506588-part1, /dev/disk/by-path/pci-0000:00:09.0-scsi-0:0:0:0-part1, /dev/disk/by-uuid/84e2594c-9753-4f69-8a20-584d6e60a569, /dev/disk/by-id/wwn-0x50f00000e1506588-part1, /dev/root
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #50 (Disk)

52: None 00.0: 11300 Partition
  [Created at block.412]
  UDI: /org/freedesktop/Hal/devices/volume_part2_size_1024
  Unique ID: 2pkM.SE1wIdpsiiC
  Parent ID: 3OOL.YUsbScIQ6L5
  SysFS ID: /class/block/sda/sda2
  Hardware Class: partition
  Model: "Partition"
  Device File: /dev/sda2
  Device Files: /dev/sda2, /dev/disk/by-id/ata-SAMSUNG_HM160HI_S18PJDNQ506588-part2, /dev/disk/by-id/scsi-SATA_SAMSUNG_HM160HIS18PJDNQ506588-part2, /dev/disk/by-path/pci-0000:00:09.0-scsi-0:0:0:0-part2, /dev/disk/by-id/wwn-0x50f00000e1506588-part2
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #50 (Disk)

53: None 00.0: 11300 Partition
  [Created at block.412]
  UDI: /org/freedesktop/Hal/devices/volume_uuid_564b5473_3a78_4af3_8bb8_6e96f3420944
  Unique ID: QLVZ.SE1wIdpsiiC
  Parent ID: 3OOL.YUsbScIQ6L5
  SysFS ID: /class/block/sda/sda5
  Hardware Class: partition
  Model: "Partition"
  Device File: /dev/sda5
  Device Files: /dev/sda5, /dev/disk/by-id/ata-SAMSUNG_HM160HI_S18PJDNQ506588-part5, /dev/disk/by-id/scsi-SATA_SAMSUNG_HM160HIS18PJDNQ506588-part5, /dev/disk/by-path/pci-0000:00:09.0-scsi-0:0:0:0-part5, /dev/disk/by-uuid/564b5473-3a78-4af3-8bb8-6e96f3420944, /dev/disk/by-id/wwn-0x50f00000e1506588-part5
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #50 (Disk)

54: USB 00.0: 10a00 Hub
  [Created at usb.122]
  UDI: /org/freedesktop/Hal/devices/usb_device_1d6b_2_0000_00_02_1_if0
  Unique ID: k4bc.OqydEZZ981A
  Parent ID: ruGf.Q2YEkqhxk71
  SysFS ID: /devices/pci0000:00/0000:00:02.1/usb1/1-0:1.0
  SysFS BusID: 1-0:1.0
  Hardware Class: hub
  Model: "Linux 2.6.38-8-generic-pae ehci_hcd EHCI Host Controller"
  Hotplug: USB
  Vendor: usb 0x1d6b "Linux 2.6.38-8-generic-pae ehci_hcd"
  Device: usb 0x0002 "EHCI Host Controller"
  Revision: "2.06"
  Serial ID: "0000:00:02.1"
  Driver: "hub"
  Driver Modules: "usbcore"
  Speed: 480 Mbps
  Module Alias: "usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00"
  Driver Info #0:
    Driver Status: option is not active
    Driver Activation Cmd: "modprobe option"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #17 (USB Controller)

55: USB 00.0: 10a00 Hub
  [Created at usb.122]
  UDI: /org/freedesktop/Hal/devices/usb_device_1d6b_2_0000_00_04_1_if0
  Unique ID: pBe4.QtYiGM_hXFF
  Parent ID: +6Nb.Q2YEkqhxk71
  SysFS ID: /devices/pci0000:00/0000:00:04.1/usb2/2-0:1.0
  SysFS BusID: 2-0:1.0
  Hardware Class: hub
  Model: "Linux 2.6.38-8-generic-pae ehci_hcd EHCI Host Controller"
  Hotplug: USB
  Vendor: usb 0x1d6b "Linux 2.6.38-8-generic-pae ehci_hcd"
  Device: usb 0x0002 "EHCI Host Controller"
  Revision: "2.06"
  Serial ID: "0000:00:04.1"
  Driver: "hub"
  Driver Modules: "usbcore"
  Speed: 480 Mbps
  Module Alias: "usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00"
  Driver Info #0:
    Driver Status: option is not active
    Driver Activation Cmd: "modprobe option"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #19 (USB Controller)

56: USB 00.0: 10a00 Hub
  [Created at usb.122]
  UDI: /org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_02_0_if0
  Unique ID: uIhY.kllrQr_lFX9
  Parent ID: _Znp.fdoO6mi4bbA
  SysFS ID: /devices/pci0000:00/0000:00:02.0/usb3/3-0:1.0
  SysFS BusID: 3-0:1.0
  Hardware Class: hub
  Model: "Linux 2.6.38-8-generic-pae ohci_hcd OHCI Host Controller"
  Hotplug: USB
  Vendor: usb 0x1d6b "Linux 2.6.38-8-generic-pae ohci_hcd"
  Device: usb 0x0001 "OHCI Host Controller"
  Revision: "2.06"
  Serial ID: "0000:00:02.0"
  Driver: "hub"
  Driver Modules: "usbcore"
  Speed: 12 Mbps
  Module Alias: "usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #16 (USB Controller)

57: USB 00.0: 10a00 Hub
  [Created at usb.122]
  UDI: /org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_04_0_if0
  Unique ID: zPk0.moLwSePIflE
  Parent ID: 8otl.fdoO6mi4bbA
  SysFS ID: /devices/pci0000:00/0000:00:04.0/usb4/4-0:1.0
  SysFS BusID: 4-0:1.0
  Hardware Class: hub
  Model: "Linux 2.6.38-8-generic-pae ohci_hcd OHCI Host Controller"
  Hotplug: USB
  Vendor: usb 0x1d6b "Linux 2.6.38-8-generic-pae ohci_hcd"
  Device: usb 0x0001 "OHCI Host Controller"
  Revision: "2.06"
  Serial ID: "0000:00:04.0"
  Driver: "hub"
  Driver Modules: "usbcore"
  Speed: 12 Mbps
  Module Alias: "usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #18 (USB Controller)

58: PS/2 00.0: 10800 Keyboard
  [Created at input.161]
  UDI: /org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port_logicaldev_input
  Unique ID: c3zD.+49ps10DtUF
  Hardware Class: keyboard
  Model: "AT Translated Set 2 keyboard"
  Vendor: 0x0001 
  Device: 0x0001 "AT Translated Set 2 keyboard"
  Compatible to: int 0x0211 0x0001
  Device File: /dev/input/event4
  Device Files: /dev/input/event4, /dev/input/by-path/platform-i8042-serio-0-event-kbd
  Device Number: char 13:68
  Driver Info #0:
    XkbRules: xfree86
    XkbModel: pc104
  Config Status: cfg=new, avail=yes, need=no, active=unknown

59: PS/2 00.0: 10500 PS/2 Mouse
  [Created at input.183]
  UDI: /org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port_logicaldev_input
  Unique ID: AH6Q.ZHI3OT7LsxA
  Hardware Class: mouse
  Model: "SynPS/2 Synaptics TouchPad"
  Vendor: 0x0002 
  Device: 0x0007 "SynPS/2 Synaptics TouchPad"
  Compatible to: int 0x0210 0x0002
  Device File: /dev/input/mice (/dev/input/mouse0)
  Device Files: /dev/input/mice, /dev/input/mouse0, /dev/input/event7, /dev/input/by-path/platform-i8042-serio-1-event-mouse, /dev/input/by-path/platform-i8042-serio-1-mouse
  Device Number: char 13:63 (char 13:32)
  Driver Info #0:
    Buttons: 2
    Wheels: 0
    XFree86 Protocol: explorerps/2
    GPM Protocol: exps2
  Config Status: cfg=new, avail=yes, need=no, active=unknown

60: None 00.0: 10103 CPU
  [Created at cpu.304]
  Unique ID: rdCR.j8NaKXDZtZ6
  Hardware Class: cpu
  Arch: Intel
  Vendor: "AuthenticAMD"
  Model: 15.104.2 "AMD Turion(tm) 64 X2 Mobile Technology TL-60"
  Features: fpu,vme,de,pse,tsc,msr,pae,mce,cx8,apic,sep,mtrr,pge,mca,cmov,pat,pse36,clflush,mmx,fxsr,sse,sse2,ht,syscall,nx,mmxext,fxsr_opt,rdtscp,lm,3dnowext,3dnow,extd_apicid,pni,cx16,lahf_lm,cmp_legacy,svm,extapic,cr8_legacy,3dnowprefetch,lbrv
  Clock: 2000 MHz
  BogoMips: 4000.10
  Cache: 512 kb
  Units/Processor: 2
  Config Status: cfg=new, avail=yes, need=no, active=unknown

61: None 01.0: 10103 CPU
  [Created at cpu.304]
  Unique ID: wkFv.j8NaKXDZtZ6
  Hardware Class: cpu
  Arch: Intel
  Vendor: "AuthenticAMD"
  Model: 15.104.2 "AMD Turion(tm) 64 X2 Mobile Technology TL-60"
  Features: fpu,vme,de,pse,tsc,msr,pae,mce,cx8,apic,sep,mtrr,pge,mca,cmov,pat,pse36,clflush,mmx,fxsr,sse,sse2,ht,syscall,nx,mmxext,fxsr_opt,rdtscp,lm,3dnowext,3dnow,extd_apicid,pni,cx16,lahf_lm,cmp_legacy,svm,extapic,cr8_legacy,3dnowprefetch,lbrv
  Clock: 2000 MHz
  BogoMips: 4000.10
  Cache: 512 kb
  Units/Processor: 2
  Config Status: cfg=new, avail=yes, need=no, active=unknown

62: None 00.0: 10700 Loopback
  [Created at net.124]
  Unique ID: ZsBS.GQNx7L4uPNA
  SysFS ID: /class/net/lo
  Hardware Class: network interface
  Model: "Loopback network interface"
  Device File: lo
  Link detected: yes
  Config Status: cfg=new, avail=yes, need=no, active=unknown

63: None 00.0: 10701 Ethernet
  [Created at net.124]
  Unique ID: usDW.ndpeucax6V1
  Parent ID: rBUF.Qh8YuQ9wg77
  SysFS ID: /class/net/eth0
  SysFS Device Link: /devices/pci0000:00/0000:00:0a.0
  Hardware Class: network interface
  Model: "Ethernet network interface"
  Driver: "forcedeth"
  Driver Modules: "forcedeth"
  Device File: eth0
  HW Address: 00:1e:68:7f:2c:8b
  Link detected: no
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #24 (Ethernet controller)

64: None 00.0: 1070a WLAN
  [Created at net.124]
  Unique ID: AYEt.QXn1l67RSa1
  Parent ID: y9sn.9AnOduZyIOF
  SysFS ID: /class/net/wlan0
  SysFS Device Link: /devices/pci0000:00/0000:00:0d.0/0000:03:00.0
  Hardware Class: network interface
  Model: "WLAN network interface"
  Driver: "ath5k"
  Driver Modules: "ath5k"
  Device File: wlan0
  HW Address: 00:1f:e2:ca:20:77
  Link detected: yes
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #36 (WLAN controller)

```

---

### Post by no2498 on 2011-05-30
if your on a lap top you may need to turn the cam on with like fn+f10 keys

---

### Post by webofunni on 2011-05-30
Yes, something like that should be done. I cant see any details of webcam in the lsusb and hwinfo.

---

### Post by dFlyer on 2011-05-30
Try this, start skype and go to the options, video devices

under Select Webcam: How many devices are listed. When I use my HP webcam on my laptop it changes driver and I have to change it back to my laptop webcam. So if more than one webcam is listed try them.

---

### Post by no2498 on 2011-05-31
if he ever gets it turned on
in a terminal type dmesg click enter
that should install a cam grabber
in the terminal type lsusb click enter

---

### Post by webofunni on 2011-05-31
How dmesg will install something ?

---

### Post by no2498 on 2011-05-31
i do not know how or why but it does

---

